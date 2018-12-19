.. _intro:

Introduction
============

개요
+++++++

PHP Server Monitor는 웹 사이트와 서버가 실행 중인지 확인하는 스크립트 이며,
당신이 당신의 서비스 및 웹사이트를 관리 할 수 있는 웹 기반 UI와 함께 제공됩니다.
휴대폰 번호와 e-메일 주소로 각 서버의 사용자를 관리 할 수 있습니다.


특징
++++++++

* 서비스 및 웹 사이트를 모니터링 하십시오(아래 참조).
* E-메일, SMS 및 푸시메시지 알림
* 가동 시간 및 대기 시간에 대한 내역 그래프를 봅니다.
* 2단계의 사용자 인증(관리자 및 일반 사용자).
* 연결 오류의 로그를 E-메일과 문자메시지로 보내줍니다.
* 자동 cronjob 구현으로 서버를 자동으로 확인합니다.


서버
-------
There are two different ways to monitor a server:
서버 모니터링을 사용하는 두가지 방법:

* 서비스

  주어진 포트에서 입력된 ip 또는 도메인에 대한 연결이 만들어 집니다.
  이렇게하면 컴퓨터의 특정 서비스가 아직 실행 중인지 확인할 수 있습니다.
  예를 들어 IMAP 서비스를 확인하려면 포트 143을 입력하십시오.

* 웹사이트

  웹사이트 링크를 입력하면 cURL을 사용하여 웹사이트를 열고 HTTP 상태 코드를 확인할 수 있습니다.
  HTTP 상태 코드가 4xx범위에 있으면 오류가 발생했으며 해당 웹사이트에 public에서 접근 할 수 없음을 의미합니다.
  페이지 자체의 내용과 일치하는 정규 표현식을 설정할 수도 있습니다.
  정규식이 일치하는 항목을 반환하지 않으면 웹사이트가 다운된 것으로 간주합니다.
  두 경우 모두 스크립트는 "오프라인 상태"를 반환하고 알림을 발송하기 시작합니다.


알림
-------------
각 서버는 알림과 관련하여 고유한 설정을 가집니다.
E-메일, SMS 및 푸시메시지 알림을 선택할 수 있습니다.
현재 다음과 같은 SMS 게이트웨이를 사용할 수 있습니다:

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

참고: 이 게이트웨이들의 경우 충분한 크레딧이 있는 계정이 필요합니다.


다운로드
++++++++

최신 버전은 http://www.phpservermonitor.org/에서 다운로드 할 수 있습니다.
