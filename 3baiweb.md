## CÁCH LÀM

### WEB 1:

Đọc qua src code , có thể thấy web nhận POST request và có thể khai thác LFI.

> Khi gửi request , server trả về
>
> ![img](/imgs/response.png)


> `{"content":"Invalid content"}`
>
> do trong flag có "EHC" , đã blacklist.

Sau khi tra google thì e biết có 1 phu