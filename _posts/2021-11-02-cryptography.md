---
layout: post
title: "Intro to Cryptography"
date: 2021-11-03 01:48:45
image: '/images/quantumexplainer3.2-01-10.jpg'
description: ManhLab
tags:
- Infosec
categories:
- ITMOBRAIN
twitter_text:
---
## Intro to Cryptography
Trong ngành Bảo mật thông tin, Mật mã học là một phần rất quan trọng và đóng vai trò nền tảng của bảo mật thông tin hiện nay. Khác với các mảng khác, cryptography được sử dụng cách ngày nay rất lâu và đóng vai trò bảo mật trong suốt lịch sử loài người. 

Bài viết này đề cập tới mã hóa cổ điển(classic cryptography)  là cách mã hóa cổ điển được dùng trước thời kỳ của máy vi tính hiện nay. Thời vì này việc mã hóa và giải mã được thực hiện chủ yếu bằng tay. Mã được sắp xếp để tạo thành một đoạn ciphertext khó hiểu đối với kẻ thâm nhập, nhưng với người nhận nhờ đã nắm rõ quy tắc giải mã thông tin nên việc này dễ dàng hơn rất nhiều. 
Classic cryptography chia làm 2 nhánh chính đó là : 
- chuyển vị 
- thay thế ký tự. 

### 1. Chuyển vị kí tự 
Chuyển vị kí tự điển hình mã Caesar được biết đến là người đầu tiên sử dụng mã hóa để truyền thông điệp, Thuật toán caesar để mã hóa 1 đoạn thông điệp gửi đến bên kia đại dương mà đối phương không hề hay biết. Thuật toán Caesar mở đầu bằng việc tịnh tiến ký tự trong bảng chữ cái mở đầu cho những mã hóa bằng kí tự, mật mã sau này: 
```
Cryptography → dịch 1 kí tự(ROT1) --> Dszquphsbqiz
```
Mã hóa caesar khá đơn giản, không tốn nhiều thời gian, hơn nữa các dấu câu không hề được mã hóa đã dẫn đến việc kẻ thâm nhập có thể đoán ra quy tắc mã hóa và vấn đề tìm ra thông điệp chỉ còn là vấn đề thời gian. Mình có viết 1 đoạn code để giải mã thuật toán Caesar này khi làm lab trên lớp như sau.
```python
text = "IO<NYCMYHINY;YJF?;M=HNY=IH>"
for i in range(100):
    for key in text:
        if ord(key) + i > 126:
            print(chr(ord(key) + i - 95), end="")
        else:
            print(chr(ord(key) + i), end="")
    print("\n")
```

Đoạn code đơn giản tấn công triệt để mọi khả năng của mã hóa Caesar và tất nhiên là sẽ thành công.
Một số phương pháp khai thác khác trong việc chuyển vị bao gồm:
- Dùng ma trận vuông, hoán đổi vị trí phần tử trên cột, hoán đổi phần tử trong hàng, 
- Hoán đổi vị trí hàng, hoán đổi vị trí cột, 
- kết hợp nhiều trường hợp trên lại với nhau. 
  
Nhìn chung vì là bằng tay nên những thuật toán này gây không ít khó khăn cho người giải mã. Và nó cũng cần vốn hiểu biết khá tốt về ngôn ngữ đang mã hóa.

### 2. Phương pháp thay thế ký tự
Với phương pháp thay thế ký tự. Một kí tự đơn giản được thay thế bằng một ký tự khác hoặc số mà không có liên quan nhiều đến các kí tự khác.
Một hàm được sử dụng khá lâu đó là bảng mã hóa: khi mà kí tự được viết tương ứng với key mã hóa và chỉ cần đối chiếu với bảng để giải mã:
```python
VD: bảng mã: A-19 B-30 C-34 ABC - 193034
```
Một ví dụ về sức mạnh của mật mã học đó là cỗ máy Enigma. Trong chiến tranh thế giới thứ 2, đây là cỗ máy được dùng để mã hoá tất cả những thư tín liên lạc, giữ bảo mật hoàn toàn các thông tin quân sự của Đức. Cùng với năng lực quân sự mạnh mẽ, nước Đức khi đó một mình chiến đấu với toàn bộ châu  u và trước tình thế này, quân đội Anh phải tìm cách phá bộ giải mã của Enigma để tìm kiếm cơ hội ngăn chặn sự bành trướng của người Đức. Cỗ máy đã làm đau đầu hàng nghìn nhà khoa học lúc bâý giờ, và phải nhờ đến một mật ngữ ở cuối mỗi dòng thư tín( Hít le vạn tuế) thì Alan Turing(cha đẻ của mật mã học hiện đại) mới giải mã được. Việc giải mã cỗ máy Enigma đã giúp chấm dứt chiến tranh thế giới thứ 2 sớm hơn khoảng 2 năm. Đóng vai trò quan trọng trong sự phát triển thế giới hiện đại.

Khi nghiên cứu sâu hơn về ngôn ngữ, người ta phát triển thêm  thuật toán rất hay về mã hóa: Khi mà ko có bảng giải mã, với 1 lượng lớn ký tự đầu vào đã mã hóa. Qua phân tích số lần xuất hiện, quy tắc và từ vựng đã giúp cho chúng ta có góc nhìn tổng quan hơn về nó. Từ đó lần tìm ra text gốc qua vệc giải mã từng ký tự đã bị thay thế.

Trong một thời đại mới, cryptography bước vào kỉ nguyên của thách thức khi mà dữ liệu truyền đi với tốc độ ánh sáng. Thông điệp truyền đi có thể bị bắt bới kẻ xâm nhập ngay tức thời. Những thuật toán mạnh mẽ hơn, đồng thời những cỗ máy giải mã đang cạnh tranh với nhau mỗi ngày. Nếu bạn quan tâm nhiều hơn tới mật mã học, hãy comment dưới bài viết này để CLB có động lực ra thêm nhiều bài viết về vấn đề này nữa nhé!🥳