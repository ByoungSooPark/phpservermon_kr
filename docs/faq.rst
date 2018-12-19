.. _faq:

Frequently Asked Questions
==========================


Users
+++++

What are the differences between the user levels?
����� ������ �������� �����Դϱ�?
-------------------------------------------------

There are 2 user levels available: regular user and administrator.
�Ϲ� ����ڿ� �����ڶ�� �� ���� ����� ������ �ֽ��ϴ�.

Administrators:

* Manage servers.
* Manage users.
* Edit global configuration.

Regular users:

* View the status of their assigned servers.
* �Ҵ� �� ������ ���¸� ���ϴ�.

* View the history and logs of their assigned servers.
* ������ ������ ���� �� �α׸� ���ϴ�.

* Run the updater on their assigned servers.
* �Ҵ� �� �������� �������͸� �����Ͻʽÿ�


Servers
+++++++

What is the difference between a service and a website?
���񽺿� �� ����Ʈ�� �������� �����Դϱ�?
-------------------------------------------------------

For websites, the monitor attempts to open a regular web page, just like you do in your browser.
It will attempt to retrieve its contents, and also check the HTTP status code (for example "404 not found" will cause an error).
You can then even add a check to make sure the content of the website includes a certain string or matches a certain regular expression.
Please note, it only retrieves the contents and does not execute any Javascript. Your search pattern will not work if it depends on Javascript being executed.

�� ����Ʈ�� ��� ����Ͱ� ������������ ���� �Ϲ� �� �������� ������ �õ��մϴ�.
������ �˻��ϰ� HTTP ���� �ڵ带 Ȯ���Ϸ��� �õ��մϴ� (�� : "404 not found"�� ������ ���� ��).
�׷� ���� �� ����Ʈ�� ������ Ư�� ���ڿ��� �����ϴ��� �Ǵ� Ư�� ���� ǥ���İ� ��ġ�ϴ��� Ȯ���ϱ����� �˻縦 �߰� �� ���� �ֽ��ϴ�.
�������� �˻� ���ϰ� �ڹ� ��ũ��Ʈ�� �������� �ʽ��ϴ�. �������� Javascript�� ���� �˻� ������ �۵����� �ʽ��ϴ�.

For services, the monitor only attempts to connect to the IP address and specified port to check whether the server is listening on that port.
For example, if you are running a webserver it will usually listen on port 80 for incoming connections.
So if the monitor is able to connect to the server on port 80, you know the webserver is running and accepting connections.
It does not, however, mean that your website is available to your users, because it might have PHP errors or database problems.
This can be monitored using the website type with a pattern search as described above.

������ ���, ����ʹ� IP �ּ� �� ������ ��Ʈ�� ������ �õ��Ͽ� ������ �ش� ��Ʈ�� �ν��ϴ��� ���θ� Ȯ���մϴ�.
���� ��� �� ������ �������� ��� ��Ʈ 80���� ������ ������ ���� ����մϴ�.
���� ����Ͱ� ��Ʈ 80�� ������ ������ �� ������ �� ������ ���� ���̰� ������ �����ϰ� ������ �� �� �ֽ��ϴ�.
�׷��� PHP ������ �����ͺ��̽� ���������� �� �����Ƿ� ����ڰ� �� ����Ʈ�� ����� ���� �����ϴ�.
���� ���� �ȴ�� ���� �˻��� ����Ͽ� �� ����Ʈ ������ ����Ͽ��̸� ����͸� �� �� �ֽ��ϴ�.


Are requests made by the monitor included in my website statistics?
�� �� ����Ʈ ��迡 ������� ��û�� ���ԵǾ� �ֽ��ϱ�?
-------------------------------------------------------------------

There are two different ways to gather statistics.
One way is to include a piece of Javascript in your HTML, e.g. for Google Analytics and Piwik.
The other way is to parse the access logs created by your webserver software, which does not require any changes to your code, and is done by tools like Awstats.

When using tools such as Google Analytics, the monitor requests will not show up in your statistics, because the monitor does not execute any Javascript.
Tools that parse your raw access logs like Awstats, will include the requests made by the monitor.
To make sure these requests can be identified, the monitor uses a custom user agent, which you can usually filter out. The user agent of the monitor looks like::

     Mozilla/5.0 (compatible; phpservermon/3.0.1; +http://www.phpservermonitor.org)

��踦 �����ϴ� ���� �� ���� ����� �ֽ��ϴ�.
�� ���� ����� HTML�� �ڹ� ��ũ��Ʈ�� ���Խ�Ű�� ���Դϴ� (�� : Google �ֳθ�ƽ�� �� Piwik ��
�ٸ� ����� �� ���� ����Ʈ����� �ۼ��� �׼��� �α׸� ���� �м��ϴ� ���Դϴ�. �ڵ�� �������� �ʰ� Awstats�� ���� ������ ����Ͽ� �����մϴ�.

Google �� �α� �м��� ���� ������ ����� �� ����Ͱ� �ڹ� ��ũ��Ʈ�� �������� �ʱ� ������ ��迡 ����� ��û�� ǥ�õ��� �ʽ��ϴ�.
Awstats�� ���� ���� �׼��� �α׸� ���� �м��ϴ� �������� ������� ��û�� ���Ե˴ϴ�.
�̷��� ��û�� �ĺ� �� �� �ֵ��� ����ʹ� �Ϲ������� ���͸� �� ���ִ� ����� ���� ����� ������Ʈ�� ����մϴ�. ������� ����� ������Ʈ�� ������ �����ϴ� ::

     Mozilla / 5.0 (ȣȯ ����, phpservermon / 3.0.1, + http : //www.phpservermonitor.org)




What is the log retention period?
�α� ���� �Ⱓ�� �����Դϱ�?
---------------------------------

The monitor uses 2 different tables in the database to store history information regarding servers.
The first one is called the "uptime" table. This one keeps full track of the past 7 days, so that detailed information is available (e.g. which checks failed/passed etc).
This allows the monitor to create a detailed graph on the server info page.
In order to prevent the uptime table growing beyond reasonable, after a week the uptime records are archived to a different table.
Archiving means that per day only one record is stored with averages. This still allows some basic statistics, although they are not as detailed as the uptime records.

The retention period tells the monitor how long to keep records in the archive table.

����ʹ� �����ͺ��̽��� 2 ���� �ٸ� ���̺��� ����Ͽ� ������ ���õ� �����丮 ������ �����մϴ�.
ù ��°�� "���� �ð�"���̺��̶���մϴ�. �� ������ ���� 7 �ϰ��� ��ü ����� �����ϹǷ� �ڼ��� ���� (�� : ���� / �հ� ���� ��)�� Ȯ���� �� �ֽ��ϴ�.
�̷����ϸ� ����Ͱ� ���� ���� �������� ���� �׷����� �ۼ��� �� �ֽ��ϴ�.
�ո����� ������ �Ѿ�� ���� �ð� ���̺��� �����ϱ� ���� ������ �� ���� �ð� ����� �ٸ� ���̺� �����˴ϴ�.
������ �Ϸ� ��� �� ���� ���ڵ� �� ����ȴٴ� ���� �ǹ��մϴ�. �̰��� ���� �ð� ��ϸ�ŭ ������ ������ �� ���� �⺻ ��踦 ����մϴ�.

���� �Ⱓ�� �� + �̺� ���̺� ���ڵ带 ���� �� �Ⱓ�� ����Ϳ� �˷��ݴϴ�.



Configuration
+++++++++++++

How can I change the text of the email / SMS?
�̸��� / SMS�� �ؽ�Ʈ�� �����Ϸ��� ����ؾ��մϱ�?
---------------------------------------------

Go to the folder "src/lang", open the language file that corresponds to the selected language
(default is English ("en_US.lang.php")). Scroll all the way to the bottom until you spot this line::
"src / lang"������ �̵��Ͽ� ������ �� �ش��ϴ� ��� ������ ���ϴ�.
(�⺻���� ���� ( "en_US.lang.php")�Դϴ�). �� ���� �߰� �� ������ �Ʒ������� ��ũ���Ͻʽÿ� :

     'notifications' => array(

After that you will see the lines that hold the notification messages. For example::
�� �Ŀ� �˸� �޽����� �����ϴ� ���� ǥ�õ˴ϴ�. ���� ��� :

     'off_sms' => 'Server \'%LABEL%\' is DOWN: ip=%IP%, port=%PORT%. Error=%ERROR%',

The first part of this line, 'off_sms', is the name of the notification. You should not change this.
The second part is the actual message. There are a few variables you can use in your message:
�� ���� ù ��° �κ� �� 'off_sms'�� �˸��� �̸��Դϴ�. �ʴ� �̰��� �ٲٸ� �ȵȴ�.
�� ��° �κ��� ���� �޽����Դϴ�. �޽����� ����� ���ִ� �� ���� ������ �ֽ��ϴ�.

* %LABEL% - The name of the server
* %IP% - The ip of the server
* %PORT% - The port of the server
* %ERROR% - This one only works for the off_* messages and contains the error returned by the monitor

* % LABEL % - ���� �̸�
* % IP % - ������ IP
* % PORT % - ���� ��Ʈ
* % ERROR % -�� �޽����� off_ * �޽����� ���ؼ��� �۵��ϸ� ����Ͱ� ��ȯ �� ������ �����մϴ�