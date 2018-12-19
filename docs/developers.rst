.. _developers:

Developers
==========
The code is available from https://github.com/phpservermon/phpservermon.
There is a master branch, which is stable and always reflects the latest release.
The develop branch is used for ongoing development and should not be considered stable.
If you would like to contribute a patch or feature, please fork the develop branch and send a pull request.

개발자
==========
개발 코드는 https://github.com/phpservermon/phpservermon에서 구할 수 있습니다.
마스터 브랜치 (master branch)는 안정적이며 항상 최신 릴리스를 반영합니다.
개발 브랜치는 지속적인 개발에 사용되며 안정적인 것으로 간주되어서는 안됩니다.
패치 나 기능을 제공하려면 개발 브랜치를 포크하고 pull request.rs를 보내십시오.


Languages
+++++++++

The server monitor uses language files, which are stored in the directory "src/lang".
The name of the language file consists of the language code (ISO 639-1) and the country code (ISO 3166-1), separated by an underscore.
The extension is ".lang.php".

언어
+++++++++
서버 모니터는 "src / lang"디렉토리에 저장된 언어 파일을 사용합니다.
언어 파일의 이름은 언어 코드 (ISO 639-1)와 국가 코드 (ISO 3166-1)로 구성되며 밑줄로 구분됩니다.
확장자는 ".lang.php"입니다.

Locales
-------

Each language file should contain a 'locale' key which can be used for formatting dates and times. This 'locale' key must include the locales for different server environments:

* Linux / OS X: same as filename (language code and country code separated by underscore)
* Windows: http://msdn.microsoft.com/en-US/library/39cwe7zf%28v=vs.80%29.aspx
For more information, see http://www.php.net/manual/en/function.setlocale.php
For display purposes, the language file should also provide the text direction (ltr / rtl) and language subtag.
Unfortunately they do not match 1:1 with the locales used for the server.
Valid language subtags can be found on http://www.iana.org/assignments/language-subtag-registry/language-subtag-registry.

Locales
-------
각 언어 파일에는 날짜와 시간의 형식을 지정하는 데 사용할 수있는 'locale'키가 있어야합니다. 이 'locale'키에는 다른 서버 환경에 대한 로케일이 포함되어야합니다.
* Linux / OS X: same as filename (language code and country code separated by underscore)
* Windows: http://msdn.microsoft.com/en-US/library/39cwe7zf%28v=vs.80%29.aspx
자세한 내용은 다음을 참조하십시오. http://www.php.net/manual/en/function.setlocale.php
표시 목적으로 언어 파일은 텍스트 방향 (ltr / rtl) 및 언어 서브 태그를 제공해야합니다.
안타깝게도 서버에 사용 된 로케일과 1 : 1이 일치하지 않습니다.
유효한 언어 하위 태그는 http://www.iana.org/assignments/language-subtag-registry/language-subtag-registry에서 찾을 수 있습니다.



Adding a new language
---------------------

To add a new language, follow these steps:

* Create a new file in the directory "src/lang" named "{locale}.lang.php".
* Copy the contents of the file "en_US.lang.php" to your new file.
* Your new language should now be available on the config page.
* Translate :-)
* Please send a pull request on github (https://github.com/phpservermon/phpservermon) so it can be included in the next release :-)


새언어추가하기
-------------------
새 언어를 추가하려면 다음과 같이하십시오.
*디렉토리에 새 파일 만들기 "src/lang" named "{locale}.lang.php".
*파일 내용 복사  "en_US.lang.php" to your new file.
*이제 설정 페이지에서 새로운 언어를 사용할 수 있습니다.
*옮김  :-)
*다음 릴리스에 포함될 수 있도록 github (https://github.com/phpservermon/phpservermon)에 풀 요청을 보내주십시오 :-)

Getting started
+++++++++++++++


시작하기
+++++++++++++++



Vagrant
-------

If you are not familiar with Vagrant, have a look at https://www.vagrantup.com/ for more information (it is awesome).
To ease development, a Vagrantfile has been included along with a full provisioning profile generated using PuPHPet (https://puphpet.com).
The Vagrantfile is configured to set up a CentOS 6.5 box with PHP 5.6 and MySQL installed, with a local port forward on port 8080.
To set up the development environment, make sure you have Vagrant and VirtualBox (https://www.virtualbox.org/) installed, then run::

Vagrant에 익숙하지 않은 경우 https://www.vagrantup.com/에서 자세한 정보를 확인하십시오 (멋진 소식입니다).
개발을 쉽게하기 위해 PuPHPet (https://puphpet.com)을 사용하여 생성 된 전체 프로비저닝 프로파일과 함께 Vagrantfile이 포함되었습니다.
Vagrantfile은 PHP 5.6 및 MySQL이 설치된 CentOS 6.5 상자를 포트 8080에서 로컬 포트로 설정하도록 구성됩니다.
개발 환경을 설정하려면 Vagrant 및 VirtualBox (https://www.virtualbox.org/)가 설치되어 있는지 확인한 후 다음을 실행하십시오.



     vagrant up

The initial setup may take some time as the virtual machine needs to be provisioned.
After that, you can access your development environment by navigating to http://localhost:8080/psm/ or http://192.158.56.101/psm/.
The config.php file has been created automatically, but the first time you do need to run through the install wizard.

가상 시스템을 프로비저닝해야하므로 초기 설정에 약간의 시간이 걸릴 수 있습니다.
그런 다음 http : // localhost : 8080 / psm / 또는 http://192.158.56.101/psm/으로 이동하여 개발 환경에 액세스 할 수 있습니다.
config.php 파일은 자동으로 생성되었지만, 설치 마법사를 처음 실행할 때 필요합니다.


Code
----

All code related to phpservermon lives in the "psm" namespace, which can be found under "src/psm".

The Router (https://github.com/phpservermon/phpservermon/blob/develop/src/psm/Router.class.php) is used to load the modules.
All modules are registered inside the Router class with a unique ID (see getModules()), and can either be loaded manually ($router->run('mod')), or if no module is given it will attempt to discover the module from the $_GET['mod'] var.
If no valid module or controller is found, it will fall back to the default module.

The module var may exist of 2 parts, separated by an underscore. The first part is the ID of the module, and the second part is the ID of the controller registered in the module.
If no controller ID is found, it will attempt to load the controller with the same ID as the module.

Examples ::

    $router->run('config'); // module ID "config" and controller ID also "config" (same as $router->run('config_config'))
    $router->run('server_status'); // module ID "server" and controller ID "status"

If the user is not logged in and login is required, it will automatically load the user login controller without throwing an error.



phpservermon과 관련된 모든 코드는 "psm"네임 스페이스에 있으며 "src / psm"아래에 있습니다.

라우터 (https://github.com/phpservermon/phpservermon/blob/develop/src/psm/Router.class.php)는 모듈을로드하는 데 사용됩니다.
모든 모듈은 고유 한 ID (getModules () 참조)로 라우터 클래스에 등록되며 수동으로로드 할 수 있습니다 ($ router-> run ( 'mod')). 모듈이 제공되지 않으면 모듈을 발견하려고 시도합니다 모듈을 $ _GET [ 'mod'] var에 추가하십시오.
유효한 모듈이나 컨트롤러가 발견되지 않으면 기본 모듈로 되돌아갑니다.

모듈 var는 밑줄로 분리 된 2 부분으로 존재할 수 있습니다. 첫 번째 부분은 모듈의 ID이고 두 번째 부분은 모듈에 등록 된 컨트롤러의 ID입니다.
컨트롤러 ID가 없으면 모듈과 동일한 ID로 컨트롤러를로드하려고 시도합니다.

예 :

    $ router-> run ( 'config'); // 모듈 ID "config"와 컨트롤러 ID도 "config"($ router-> run ( 'config_config')와 동일)
    $ router-> run ( 'server_status'); // 모듈 ID "server"및 컨트롤러 ID "status"

사용자가 로그인하지 않고 로그인해야하는 경우, 오류를 _ 생시키지 않고 사용자 로그인 컨트롤러를 자동으로로드합니다.



Vagrant

