<h1 align="center"> :metal: EHC Qual Writeup :metal: </h1>

## WEB

- **Web 01** Tổ hợp phím được sử dụng khi bạn muốn xem source code của 1 trang web là gì?

  **EHC{ctrl_u}**

- **Web 02**
  Có một tệp văn bản đặt ở gốc trang web và chứa các chỉ thị cho các robots.Tìm ra tên của file đang được nói ở trên!

  **EHC{robots.txt}**

- **Web 03**
  Với 1 website làm bài thi online, ta sẽ lưu bài làm chưa hoàn thiện của thí sinh vào session hay cookie?

  **EHC{cookie}**

- **Web 04**
  Các thư mục con nằm bên trong root directory được gọi là gì?

  **EHC{subdirectory}**

- **Web 05**
  Tên của cách thức tấn công thực thi mã từ xa là gì?

  **EHC{RCE}**

- **Web 06**
  Bạn có biết tên của bộ công cụ bảo mật ứng dụng web được phát triển bởi PortSwigger không?

  **EHC{burpsuite}**

- **C0ntr0l U**
  Flag đã bị giấu ở đâu đó trong trang [web](http://206.189.35.36:30001) này, hãy check thật kĩ mọi nơi mà bạn có thể check!!!

  > Bằng ctrl + u , ta có thể dễ dàng lấy được flag
  >
  > ![EHC{Control_You_is_so_powerful}](imgs/ctrlu.png)


- **Hidden text!!!**
  Find hidden text in this [web](http://206.189.35.36:30005/)

  > Trong web có đưa ra gợi ý "I need to find some robots" , vì vậy flag có thể đang nằm tại file robots.txt, kiểm tra thử , có thể thấy flag ở đó.
  >
  > ![EHC{Robots_txt_can_be_useful_in_many_case}](imgs/robots.png)


- **Senna-Qiyana-Lucian**
  Login in to this [web](http://206.189.35.36:30004/) as candidate to get the flag!

  > Nhìn thoáng qua thì nó là 1 trang login bình thường , thử SQLI bằng dấu nháy đơn ( ' ), ta thấy được sql debug , có thể khai thac SQLi. Bằng payload đơn giản "'or'1=1" , khai thác lỗi thành công , server trả flag.
  >
  > ![EHC{just_a_simple_payload}](imgs/sqli.png)


## Crypto

- **Basic_XOR**
  Cho b=181611 và c=520999. Tìm a sao cho a^b=c?

  > a^b=c --&gt; c^b=a

  **EHC{341580}**

## Forensic

- **Comment command**
  Bạn có biết câu lệnh có thể xem được metadata?

  **EHC{exiftool}**
- **Hello Shark**
  File PCAP là loại file gì?

  **EHC{packetcapturedata}**
- **Oh! Shark is cute!**
  Mình muốn xem được file PCAP thì cần phải sử dụng tool nào thế nhỉ?

  **EHC{wireshark}**
- **Hexi Swan**
  Hex signature header of image encoded in the Portable Network Graphics format

  **EHC{89504E470D0A1A0A}**
- **Comment more command**
  Bức ảnh này có gì thú vị không nhỉ?

  > Nhìn qua thì là bức ảnh thiên nga bình thường, check metadata thì thấy ở phần artist có flag
  >
  > ![RUP{Z3g4q4g4_j1gu_fj4a}](imgs/exif.png)

  > Dùng python để trừ kí tự, kết quả là 13
  >
  > ![13](imgs/pheptru.png)

  > Tiếp theo dùng cyberchef và ROT13 để giải flag
  >
  > ![EHC{M3t4d4t4_w1th_sw4n}](imgs/rot13.png)

  ****EHC{M3t4d4t4_w1th_sw4n}**

## Binary Exploit

- Binary Exploit 01
  Trước khi bắt đầu trả lời câu hỏi. Hãy tải 2 file đính kèm bên dưới và sử dụng chúng để trả lời
  File source thuộc loại file nào?