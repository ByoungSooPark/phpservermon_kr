.. _faq:

Frequently Asked Questions
==========================


Users
+++++

What are the differences between the user levels?
사용자 레벨의 차이점은 무엇입니까?
-------------------------------------------------

There are 2 user levels available: regular user and administrator.
일반 사용자와 관리자라는 두 가지 사용자 수준이 있습니다.

Administrators:

* Manage servers.
* Manage users.
* Edit global configuration.

Regular users:

* View the status of their assigned servers.
* 할당 된 서버의 상태를 봅니다.

* View the history and logs of their assigned servers.
* 지정된 서버의 내역 및 로그를 봅니다.

* Run the updater on their assigned servers.
* 할당 된 서버에서 업데이터를 실행하십시오


Servers
+++++++

What is the difference between a service and a website?
서비스와 웹 사이트의 차이점은 무엇입니까?
-------------------------------------------------------

For websites, the monitor attempts to open a regular web page, just like you do in your browser.
It will attempt to retrieve its contents, and also check the HTTP status code (for example "404 not found" will cause an error).
You can then even add a check to make sure the content of the website includes a certain string or matches a certain regular expression.
Please note, it only retrieves the contents and does not execute any Javascript. Your search pattern will not work if it depends on Javascript being executed.

웹 사이트의 경우 모니터가 브라우저에서와 같이 일반 웹 페이지를 열려고 시도합니다.
내용을 검색하고 HTTP 상태 코드를 확인하려고 시도합니다 (예 : "404 not found"가 오류를 유발 함).
그런 다음 웹 사이트의 내용이 특정 문자열을 포함하는지 또는 특정 정규 표현식과 일치하는지 확인하기위한 검사를 추가 할 수도 있습니다.
콘텐츠를 검색 만하고 자바 스크립트는 실행하지 않습니다. 실행중인 Javascript에 따라 검색 패턴이 작동하지 않습니다.

For services, the monitor only attempts to connect to the IP address and specified port to check whether the server is listening on that port.
For example, if you are running a webserver it will usually listen on port 80 for incoming connections.
So if the monitor is able to connect to the server on port 80, you know the webserver is running and accepting connections.
It does not, however, mean that your website is available to your users, because it might have PHP errors or database problems.
This can be monitored using the website type with a pattern search as described above.

서비스의 경우, 모니터는 IP 주소 및 지정된 포트에 연결을 시도하여 서버가 해당 포트를 인식하는지 여부를 확인합니다.
예를 들어 웹 서버를 실행중인 경우 포트 80에서 들어오는 연결을 수신 대기합니다.
따라서 모니터가 포트 80의 서버에 연결할 수 있으면 웹 서버가 실행 중이고 연결을 수락하고 있음을 알 수 있습니다.
그러나 PHP 오류나 데이터베이스 문제가있을 수 있으므로 사용자가 웹 사이트를 사용할 수는 없습니다.
위에 설명 된대로 패턴 검색을 사용하여 웹 사이트 유형을 사용하여이를 모니터링 할 수 있습니다.


Are requests made by the monitor included in my website statistics?
내 웹 사이트 통계에 모니터의 요청이 포함되어 있습니까?
-------------------------------------------------------------------

There are two different ways to gather statistics.
One way is to include a piece of Javascript in your HTML, e.g. for Google Analytics and Piwik.
The other way is to parse the access logs created by your webserver software, which does not require any changes to your code, and is done by tools like Awstats.

When using tools such as Google Analytics, the monitor requests will not show up in your statistics, because the monitor does not execute any Javascript.
Tools that parse your raw access logs like Awstats, will include the requests made by the monitor.
To make sure these requests can be identified, the monitor uses a custom user agent, which you can usually filter out. The user agent of the monitor looks like::

     Mozilla/5.0 (compatible; phpservermon/3.0.1; +http://www.phpservermonitor.org)

통계를 수집하는 데는 두 가지 방법이 있습니다.
한 가지 방법은 HTML에 자바 스크립트를 포함시키는 것입니다 (예 : Google 애널리틱스 및 Piwik 용
다른 방법은 웹 서버 소프트웨어에서 작성한 액세스 로그를 구문 분석하는 것입니다. 코드는 변경하지 않고 Awstats와 같은 도구를 사용하여 수행합니다.

Google 웹 로그 분석과 같은 도구를 사용할 때 모니터가 자바 스크립트를 실행하지 않기 때문에 통계에 모니터 요청이 표시되지 않습니다.
Awstats와 같은 원시 액세스 로그를 구문 분석하는 도구에는 모니터의 요청이 포함됩니다.
이러한 요청을 식별 할 수 있도록 모니터는 일반적으로 필터링 할 수있는 사용자 정의 사용자 에이전트를 사용합니다. 모니터의 사용자 에이전트는 다음과 같습니다 ::

     Mozilla / 5.0 (호환 가능, phpservermon / 3.0.1, + http : //www.phpservermonitor.org)




What is the log retention period?
로그 보존 기간은 무엇입니까?
---------------------------------

The monitor uses 2 different tables in the database to store history information regarding servers.
The first one is called the "uptime" table. This one keeps full track of the past 7 days, so that detailed information is available (e.g. which checks failed/passed etc).
This allows the monitor to create a detailed graph on the server info page.
In order to prevent the uptime table growing beyond reasonable, after a week the uptime records are archived to a different table.
Archiving means that per day only one record is stored with averages. This still allows some basic statistics, although they are not as detailed as the uptime records.

The retention period tells the monitor how long to keep records in the archive table.

모니터는 데이터베이스에 2 개의 다른 테이블을 사용하여 서버와 관련된 히스토리 정보를 저장합니다.
첫 번째는 "가동 시간"테이블이라고합니다. 이 정보는 지난 7 일간의 전체 기록을 유지하므로 자세한 정보 (예 : 실패 / 합격 여부 등)를 확인할 수 있습니다.
이렇게하면 모니터가 서버 정보 페이지에 상세한 그래프를 작성할 수 있습니다.
합리적인 범위를 넘어서는 가동 시간 테이블을 방지하기 위해 일주일 후 가동 시간 기록이 다른 테이블에 보관됩니다.
보관은 하루 평균 한 건의 레코드 만 저장된다는 것을 의미합니다. 이것은 가동 시간 기록만큼 상세하지 않지만 몇 가지 기본 통계를 허용합니다.

보유 기간은 아 + 이브 테이블에 레코드를 보존 할 기간을 모니터에 알려줍니다.



Configuration
+++++++++++++

How can I change the text of the email / SMS?
이메일 / SMS의 텍스트를 변경하려면 어떻게해야합니까?
---------------------------------------------

Go to the folder "src/lang", open the language file that corresponds to the selected language
(default is English ("en_US.lang.php")). Scroll all the way to the bottom until you spot this line::
"src / lang"폴더로 이동하여 선택한 언어에 해당하는 언어 파일을 엽니다.
(기본값은 영어 ( "en_US.lang.php")입니다). 이 줄을 발견 할 때까지 아래쪽으로 스크롤하십시오 :

     'notifications' => array(

After that you will see the lines that hold the notification messages. For example::
그 후에 알림 메시지를 보관하는 행이 표시됩니다. 예를 들면 :

     'off_sms' => 'Server \'%LABEL%\' is DOWN: ip=%IP%, port=%PORT%. Error=%ERROR%',

The first part of this line, 'off_sms', is the name of the notification. You should not change this.
The second part is the actual message. There are a few variables you can use in your message:
이 줄의 첫 번째 부분 인 'off_sms'는 알림의 이름입니다. 너는 이것을 바꾸면 안된다.
두 번째 부분은 실제 메시지입니다. 메시지에 사용할 수있는 몇 가지 변수가 있습니다.

* %LABEL% - The name of the server
* %IP% - The ip of the server
* %PORT% - The port of the server
* %ERROR% - This one only works for the off_* messages and contains the error returned by the monitor

* % LABEL % - 서버 이름
* % IP % - 서버의 IP
* % PORT % - 서버 포트
* % ERROR % -이 메시지는 off_ * 메시지에 대해서만 작동하며 모니터가 반환 한 오류를 포함합니다