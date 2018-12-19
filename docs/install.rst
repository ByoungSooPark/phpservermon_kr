.. _install:

설치
============

설치
+++++++

파일 업로드
------------

첫 단계는 웹서버에 파일을 업로드하는 것입니다.
당신은 서버 모니터의 폴더 이름을 바꿀 수 있습니다.

install.php를 실행하십시오.
---------------

이제 root 디렉토리에 있는 install.php 스크립트를 실행할 수 있습니다.

설치 스크립트는 구성 파일 설정을 안내하고 필수 데이터베이스 테이블을 작성합니다.
어떤 이유로 구성 파일을 생성 할 수 없는 경우 아래 단계를 사용하여 수동으로 구성 파일을 수행 할 수 있습니다.
config.php.sample파일의 이름을 config.php로 변경 한 다음 메모장과 같으 일반 텍스트 편집기로 config.php파일을 엽니다.
이 파일에서 PHP의 define()함수를 사용하여 저장된 데이터베이스 정보를 변경해야 합니다.
이 값을 올바르게 변경하려면 함수의 두 번째 매개 변수만 업데이트하십시오::

     define('PSM_DB_HOST', 'db_host');
     define('PSM_DB_NAME', 'db_name');
     define('PSM_DB_USER', 'db_user');
     define('PSM_DB_PASS', 'db_user_password');
     define('PSM_DB_PORT', '3306');

예: 사용자가 이름을 변경하려면 'db\_user'부분만 변경해야 합니다.
사용자 이름 주의의 따옴표를 제거하지 마십시오. 오류가 발생합니다.
config.php를 작성한 후 install.php를 다시 실행하여 데이터베이스 구조를 작성하십시오.

설치 구성
---------------------------

index.php로 간단히 이동하여 서버 모니터의 기본 페이지를 엽니다. 맨 위에있는 메뉴에서 "구성"을 찾으십시오.
도구에 필요한 정보를 변경할 수 있는 페이지가 열립니다.


업그레이드
+++++++

일반 업그레이드의 경우 다음 단계를 수행하십시오.

* config.php를 제외한 모든 파일 바꾸기
* install.php로 이동
* 다음 단계를 따르십시오
* Enjoy

From 2.0
--------

프로젝트 구조는 2.0이후로 상당히 변경되었지만, 로컬 변경을 하지 않으면 쉽게 업그레이드 할 수 있습니다.
가장 좋은 방법은 config.inc.php 파일을 제외하고 모든 현재 파일을 새 릴리스로 바꾸는 것입니다.
구성 파일은 실제로 2.0 이후 이름이 바뀌었지만 업그레이드 하는 동안 당신이 그것을 유지하면 설치 스크립트는 데이터베이스 정보를 미리 기입하는데 사용합니다.
나중에 이전 config.inc.php파일을 제거할수 있다는 점을 제외하고는 일반 업그레이드(위 참조)와 동일합니다.

From 2.1
--------

3.0에서 소개된 새로운 기능 중 하나는 사용자 인증 시스템입니다. 이전 버전의 사용자는 암호가 없기 떄문에 업그레이드 후에는 로그인 할 수 없습니다.
이러한 이유로 업그레이드 스크립트는 업그레이드 중에 새 계정을 만들어 기존 계정의 암호를 변경하는데 사용할 수 있도록 요청합니다.
어떤 이유로든 이것이 작동하지 않으면 업그레이드 스크립트는 기존의 모든 사용자의 username을 E-메일 주소로 자동 변경합니다. 이 암호는 암호 분실 화면에 사용할 수 있습니다.


GitHub에서 설치
++++++++++++++++++++++
GitHub에서 소스를 다운로드 한 경우(미리 빌드된 패키지가 아닌 경우) 종속성은 포함되지 않습니다.
repo에서 설치를 실행하려면 다음 명령을 실행하여 종속성을 설치해야 합니다.

     php composer.phar install


cronjob 설정
++++++++++++++++++++

서버를 최신 상태로 유지하려면 상태 업데이터가 정기적으로 실행되어야 합니다.
리눅스 머신에서 이것을 실행한다면, 가장 쉬운 방법은 cronjob을 추가하는 것입니다.
자신의 서버이거나 crontab을 열 수 었는 셸 액세스 권한이 있는 경우 "crontab"파일을 찻습니다.
(보통 /etc/crontab에 있지만, 배포판에 의존합니다.). 파일(vi /etc/crontab)을 열고 다음을 추가하십시오
(설치 디렉토리와 일치하도록 경로 변경) 15분마다 실행하십시오.

     */15 * * * * root /usr/bin/php /var/www/html/phpservermon/cron/status.cron.php

보시다시피, 이 줄은 15분마다 status.cron.php 스크립트를 실행합니다. 필요에 맞게 선을 변경하십시오.
셸 액세스 권한이 없는 경우 웹 호스팅 제공 업체에 문의하십시오.

Please note that some distros have user-specific crontabs (e.g. Debian). If that is the case, you need to omit the user part::
일부 배포판에는 사용자 별 crontab이 있습니다(예: 데비앙). 이 경우 사용자 부분을 생략해야 합니다::

     */15 * * * * /usr/bin/php /var/www/html/phpservermon/cron/status.cron.php

업데이트 스크립트는 여러번 실행되지 않도록 설계되었습니다. 최대 제한 시간은 10분 입니다.
그 후 스크립트는 죽은것으로 간주되고 cronjob이 다시 실행됩니다.
10분의 시간 제한을 변경하려면 src/includes/psmconfig.inc.php에서 상수 "PSM_CRON_TIMEOUT"을 찾으십시오.
인수로 제공 할 수도 있습니다(초 단위). 다음 예제는 10초로 제한시간을 변경합니다.

     php status.cron.php --timeout=10

By default, no URLs are generated for notifications created in the cronjob.
기본적으로 cronjob에서 생성 된 알림에는 URL이 생성되지 않습니다.
To specify the base url to your monitor installation, use the "--uri" argument, like so::
모니터 설치에 기본 URL을 지정하려면 다음과 같이 "--url"인수를 사용하십시오.

     php status.cron.php --uri="http://www.phpservermonitor.org/mymonitor/"

CPanel
-------

cPanel을 사용한다면 다음 단계를 따르십시오:

1. cPanel계정에 로그인 하십시오.

2. cron 작업으로 이동하십시오.

3. 새로운 cronjob을 추가하십시오.

- 분 필드에 '*/15'를 입력하십시오.

- 다른 필드에 '*'를 입력하십시오.

- 명령 필드에 'php/home2/<cPanel사용자 이름>/public_html/phpservermon/cron/status.cron.php' 를 입력하십시오.

4. Submit
     

문제 해결
+++++++++++++++

모니터를 설정하거나 액세스하는데 문제가 있고 그 이유를 모르면 디버그 모드를 사용하여 오류보고를 켭니다.
디버그 모드를 가능하게 하려면 config.php파일에 다음 행을 추가하십시오::

    define('PSM_DEBUG', true);
