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

There are two different ways to monitor a server:

* 서비스

  A connection will be made to the entered ip or domain, on the given port.
  This way you can check if certain services on your machine are still running.
  To check your IMAP service for example, enter port 143.

* 웹사이트

  You can enter a link to a website, it will then use cURL to open the website and check the HTTP status code.
  If the HTTP status code is in the 4xx/5xx, it means an error occurred and the website is not accessible to the public.
  You can also set a regular expression to match for content on the page itself.
  If the regular expression returns no matches, the website is considered down.
  In both cases the script will return a "status offline", and will start sending out notifications.

Each server has its own settings regarding notification.
You can choose for email, text message (SMS) and Pushover.net notifications.
The following SMS gateways are currently available:

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



Please note: for these gateways you will need an account with sufficient credits.


다운로드
--------

The latest version can be downloaded from http://www.phpservermonitor.org/.


Requirements
------------

* Web server
* MySQL database
* PHP 5.3.7+
* PHP cURL package
* PHP PDO mysql driver
* PHP-XML


설치
-------

Please see docs/install.rst.
In a nutshell: unzip, upload, run install.php, enjoy.

If you have downloaded the source from GitHub (and not a pre-built package), the dependencies are not included.
To be able to run an installation from the repo, you need to run the following command to install the dependencies::

     php composer.phar install

If you are familiar with Vagrant (https://www.vagrantup.com)::

     vagrant up

.. and browse to http://localhost:8080/psm/.


문서
-------------

자세한 문서는 링크주소를 확인해주세요. http://docs.phpservermonitor.org.


License
-------

PHP Server Monitor is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

PHP Server Monitor is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with PHP Server Monitor.  If not, see http://www.gnu.org/licenses/.

Docker
-------

PHPServerMonitor is now available on Docker : https://github.com/phpservermon/docker-phpservermonitor
-------


클라우드 서비스개발 전문가 과정 (2018.09.17 ~ 2019.02.28)
-------
[ 미니프로젝트 ]
-------
     * 안응철 http://www.gcp.elimao.site
     * 오동진 http://monitor.bestcloud.kr/phpservermon_kr/
     * 신동민 http://www.gcp.ddms.me
     * 한열   http://www.gcp.hanyeol.com

