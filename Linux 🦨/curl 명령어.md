```
curl [옵션] [URL]
```

가장 기본적인 형태는 URL에서 데이터를 가져오는 것입니다. 다운로드된 데이터는 기본적으로 표준 출력(stdout)으로 출력됩니다.


- **-O**: URL에서 파일을 다운로드하여 파일로 저장
- **-I**: 서버로부터 받은 헤더 정보만 출력
- **-X [메소드]**: HTTP 메소드를 지정 (예: GET, POST, PUT, DELETE)
- **-d [데이터]**: POST 요청으로 전송할 데이터 지정
- **-F [필드]**: 파일 업로드를 위한 필드 지정
- **-H**: 헤더 정보를 추가

- -L : 리다이렉션을 자동으로 따라가도록 함
웹 서버에서 요청한 URL이 다른 URL로 리다이렉트되면, 기본적으로 `curl`은 리다이렉션을 따라가지 않음

```
curl: (47) Maximum (50) redirects followed
```

curl -L은 HTTP 리다이렉션을 50번까지만 따라감. 그 이상으로 갈 경우 위 에러 발생 (무한 리다이렉션)

### 가능한 원인:

1. **무한 루프 리다이렉션**: 예를 들어 A → B → A → B ... 이렇게 계속 반복되는 경우.
2. **잘못된 서버 설정**: 웹 서버가 클라이언트를 계속 다른 URL로 넘기고, 그게 또 리다이렉션 되는 상황.
3. **HTTPS ↔ HTTP 리다이렉션 충돌**: 예를 들어 HTTPS로 접속했는데 다시 HTTP로 리다이렉트 되고, 그게 다시 HTTPS로 리다이렉트 되는 상황.

```
curl -v -L [URL]
```
verbose 모드로 실행하면 리다이렉션 과정 볼 수 있음

```
C:\Users\admin>curl -v -L https://clo.mangot5.com  

* Host clo.mangot5.com:443 was resolved.  
* IPv6: (none)  
* IPv4: 104.26.10.73, 104.26.11.73, 172.67.74.230  
* Trying 104.26.10.73:443...  
* schannel: disabled automatic use of client certificate  
* ALPN: curl offers http/1.1  
* ALPN: server accepted http/1.1  
* Connected to clo.mangot5.com (104.26.10.73) port 443  
* using HTTP/1.x  
> GET / HTTP/1.1
> Host: clo.mangot5.com  
> User-Agent: curl/8.13.0  
> Accept: */*  
  
* Request completely sent off  
< HTTP/1.1 302 Found  
< Date: Wed, 06 Aug 2025 02:25:16 GMT  
< Content-Type: text/html;charset=UTF-8  
< Transfer-Encoding: chunked  
< Connection: keep-alive  
< Server: cloudflare  
< Nel: {"report_to":"cf-nel","success_fraction":0.0,"max_age":604800}  
< P3p: CP='CAO PSA CONi OTR OUR DEM ONL'  
< Location: https://landing.mangot5.com/template/cls/event/250724_triss_create/index.html  
< Cf-Cache-Status: DYNAMIC  
< Report-To: {"group":"cf-nel","max_age":604800,"endpoints":[{"url":"https://a.nel.cloudflare.com/report/v4?s=hrJaQJpVBT  
A%2FqjJvCun84tLTOLLtKa4bl9ICFTXCIDWDCsdifGQZYUw%2BJAHNc3kJKaBx25BeyvOe7RXNv%2BPaUr%2FuWprBZQ6TBTjoq8W0"}]}  
< Set-Cookie: JSESSIONID=06B4612D1BF9EE15DE86031D35C62B20; HttpOnly; Path=/; Domain=mangot5.com  
< CF-RAY: 96ab152de8dcd54e-NRT  
* Ignoring the response-body  
  
* Connection #0 to host clo.mangot5.com left intact  
* Issue another request to this URL: 'https://landing.mangot5.com/template/cls/event/250724_triss_create/index.html'  
* Host landing.mangot5.com:443 was resolved.  
* IPv6: (none)  
* IPv4: 172.67.74.230, 104.26.10.73, 104.26.11.73  
* Trying 172.67.74.230:443...  
* schannel: disabled automatic use of client certificate  
* ALPN: curl offers http/1.1  
* ALPN: server accepted http/1.1  
* Connected to landing.mangot5.com (172.67.74.230) port 443  
* using HTTP/1.x  
> GET /template/cls/event/250724_triss_create/index.html HTTP/1.1  
> Host: landing.mangot5.com  
> User-Agent: curl/8.13.0  
> Accept: */*  
  
* Request completely sent off  
< HTTP/1.1 200 OK  
< Date: Wed, 06 Aug 2025 02:25:17 GMT  
< Content-Type: text/html  
< Transfer-Encoding: chunked  
< Connection: keep-alive  
< X-Amz-Id-2: a3TgU257OcoF9VjBZtDGJFkPUD0x1KRMwQmW7O8KYhpxtACy5qqoiuShrFT4XU29l8Tbf2DHg0g3IMm2xj0/UA==  
< X-Amz-Request-Id: SY1QW6ZRMDACQPB5  
< Last-Modified: Thu, 24 Jul 2025 14:43:14 GMT  
< Report-To: {"group":"cf-nel","max_age":604800,"endpoints":[{"url":"https://a.nel.cloudflare.com/report/v4?s=8VMugbizTP  
1D%2BSLjE9BpcwDY%2Fkh441IJrvxuumwvhJVNVILsXfNc8jruOvJO1DrsdWRR1OwQ5LthCue9jPLRpnp29coF3illZxxUVvHN2m73Yw%3D%3D"}]}  
< X-Amz-Server-Side-Encryption: AES256  
< X-Amz-Meta-User-Agent: AWSTransfer  
< X-Amz-Meta-User-Agent-Id: Jack@s-e0ab9e15d62a4982a  
< X-Amz-Version-Id: null  
< Accept-Ranges: bytes  
< Server: cloudflare  
< Cf-Cache-Status: DYNAMIC  
< Nel: {"report_to":"cf-nel","success_fraction":0.0,"max_age":604800}  
< CF-RAY: 96ab1530fd74d1cb-KIX  
  
<!DOCTYPE html><html lang="zh-TW"><head><title>《封印者：CLOSERS》7/24 特莉絲事前創建</title><meta charset="UTF-8">....</body></html>* Connection #1 to host landing.mangot5.com left intact
```

