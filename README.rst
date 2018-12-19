PHP Server Monitor
==================

.. image:: https://badges.gitter.im/Join%20Chat.svg
   :alt: Join the chat at https://gitter.im/erickrf/nlpnet
   :target: https://gitter.im/phpservermon/phpservermon
   
버젼 3.2.0

PHP 서버 모니터는 웹 사이트와 서버가 가동 중인지 여부를 확인하는 스크립트 입니다. 
서비스 및 웹 사이트를 관리할 수 있고 각 서버의 사용자를 모바일 번호와 이메일 주소로 관리할 수 있는 웹 기반 사용자 인터페이스가 함께 제공됩니다.


특징:
---------

* 서비스 및 웹 사이트 모니터링(아래 참조).
* 이메일, SMS 및 푸시오버 알림.
* 가동 시간 및 대기 시간에 대한 기록 그래프 보기.
* 2단계 사용자 인증 (관리자 및 일반 사용자).
* 연결 오류, 보내는 이메일 및 텍스트 메시지 로그.
* 서버를 자동으로 점검할 수 있는 간편한 크론작업 구현.

서버를 모니터링하는 두 가지 다른 방법

* 서비스

  포트에서 입력 된 ip 또는 도메인에 대한 연결이 만들어집니다.
  이렇게하면 컴퓨터의 특정 서비스가 아직 실행 중인지 확인할 수 있습니다.
  예를 들어 IMAP 서비스를 확인하려면 포트 143을 입력하십시오.

* 웹사이트

  사이트 링크를 입력하면 cURL을 사용하여 웹 사이트를 열고 HTTP 상태 코드를 확인할 수 있습니다.
  HTTP 상태 코드가 4xx / 5xx에 있으면 오류가 발생했으며 해당 웹 사이트에 일반인이 액세스 할 수 없음을 의미합니다.
  페이지 자체의 내용과 일치하는 정규 표현식을 설정할 수도 있습니다.
  정규식이 일치하는 항목을 반환하지 않으면 웹 사이트가 다운 된 것으로 간주됩니다.
  두 경우 모두 스크립트는 "오프라인 상태"를 반환하고 알림을 발송하기 시작합니다.

각 서버는 알림과 관련하여 고유 한 설정을가집니다.
전자 메일, 문자 메시지 (SMS) 및 Pushover.net 알림을 선택할 수 있습니다.
현재 다음과 같은 SMS 게이트웨이를 사용할 수 있습니다.

* Clickatell - <https://www.clickatell.com>
* Inetworx - <http://www.inetworx.ch>
* Mollie - <http://www.mollie.nl>
* Mosms - <http://www.mosms.com>
* Smsglobal - <http://smsglobal.com/>
* SMSit - <http://www.smsit.dk/>
* Spryng - <http://www.spryng.nl>
* Textmarketer - <http://www.textmarketer.co.uk>
* FreeVoipDeal - <http://www.freevoipdeal.com>
* Nexmo - <https://www.nexmo.com/>
* OctoPush - <http://www.octopush.com/>
* FreeMobile (FR) - <http://mobile.free.fr/>


참고 :이 게이트웨이의 경우 충분한 크레딧이있는 계정이 필요합니다.


다운로드
--------

최신 버전은 http://www.phpservermonitor.org/에서 다운로드 할 수 있습니다.


요구사항
------------

* Web server
* MySQL database
* PHP 5.3.7+
* PHP cURL package
* PHP PDO mysql driver
* PHP-XML


설치
-------

설치시 docs/install.rst파일을 참조하십시오.
압축을 풀고, 업로드하고, install.php를 실행하고, 즐기십시오.

GitHub에서 소스를 다운로드 한 경우 (미리 빌드 된 패키지가 아닌 경우) 종속성은 포함되지 않습니다.
repo에서 설치를 실행하려면 다음 명령을 실행하여 종속성을 설치해야합니다.

     php composer.phar install

If you are familiar with Vagrant (https://www.vagrantup.com)::

     vagrant up

.. and browse to http://localhost:8080/psm/.


문서
-------------

자세한 문서는 링크주소를 확인해주세요. http://docs.phpservermonitor.org.


라이센스
-------

PHP Server Monitor는 자유 소프트웨어입니다. 재배포 및/또는 수정할 수 있습니다.
GNU 일반 공중 사용 허가서 (General Public License)의 조건에 따라
자유 소프트웨어 재단, 라이센스 버전 3 또는
(귀하의 선택에 따라) 최신 버전.

PHP Server Monitor는 유용할 것이라는 바램으로 배포되었습니다.
그러나 어떠한 보증도하지 않습니다. 자세한 내용은
GNU 일반 공중 사용 허가서 (GNU General Public License).

GNU 일반 공용사용 허가서 사본을 받아야합니다.
PHP Server Monitor와 함께 제공됩니다. 그렇지 않은 경우 http://www.gnu.org/licenses/를 참조하십시오

Docker
-------

PHPServerMonitor는 이제 Docker에서 사용할 수 있습니다. : https://github.com/phpservermon/docker-phpservermonitor
-------


클라우드 서비스개발 전문가 과정 (2018.09.17 ~ 2019.02.28)
-------
[ 미니프로젝트 ]
-------
     * 안응철 http://www.gcp.elimao.site
     * 오동진 http://monitor.bestcloud.kr/phpservermon_kr/
     * 신동민 http://www.gcp.ddms.me
     * 한열   http://www.gcp.hanyeol.com

