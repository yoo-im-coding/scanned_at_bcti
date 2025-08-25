## request 
```
GET /v1/ HTTP/2
Host: porsche-poster.com
Accept-Encoding: gzip, deflate, br
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Language: en-US;q=0.9,en;q=0.8
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/138.0.0.0 Safari/537.36
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Sec-Ch-Ua: "Chromium";v="138", "Not;A=Brand";v="24", "Google Chrome";v="138"
Sec-Ch-Ua-Platform: "Windows"
Sec-Ch-Ua-Mobile: ?0
Origin: https://evil.com

```

## response
```
HTTP/2 200 OK
Cache-Control: no-cache, max-age=0
Content-Type: application/json;charset=utf-8
Accept-Ranges: bytes
Age: 0
Date: Mon, 25 Aug 2025 10:55:00 GMT
X-Served-By: cache-qpg1236-QPG, cache-qpg1275-QPG
X-Cache: MISS
X-Cache-Hits: 0
X-Timer: S1756119300.596357,VS0,VE629
Vary: Accept-Encoding
Access-Control-Allow-Credentials: true
Access-Control-Allow-Origin: https://evil.com
Access-Control-Expose-Headers: Location, ETag, Baqend-Authorization-Token, Baqend-Acl, Baqend-Size, Baqend-SW-Control, Baqend-Created-At, Date, Age, Baqend-Speed-Kit, Baqend-Custom-Headers, X-Served-By, X-Cache, X-Timer, Access-Control-Allow-Origin, Fastly-Io-Info, Server-Timing, Link
Timing-Allow-Origin: https://evil.com
Strict-Transport-Security: max-age=10886400
Via: baqend
Server-Timing: pop;desc=QPG;dur=629,cache;desc=MISS,proto;desc=h2,rcomp;desc="ae=br&ce=gzip&cl=106"
Alt-Svc: h3=":443";ma=86400,h3-29=":443";ma=86400,h3-27=":443";ma=86400
Content-Length: 143

["/banned","/bloomfilter","/code","/code-content","/config","/connect","/db","/mail","/schema","/spec","/status","/transaction","/version","/"]
```
