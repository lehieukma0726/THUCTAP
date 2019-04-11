# Tìm hiểu về Github và ngôn ngữ Markdown
## 1.Tìm hiểu về GITHUB
-  Github là một trang web, cho phép bạn lưu source code của mình lên đó.Bạn có thể thay đổi đoạn code của mình mọi lúc mọi nơi mà không sợ bị ghi đè lên hay bị mất dữ liệu do hỏng hóc vì dữ liệu của bạn được lưu cả trên trang web Github và máy cá nhân.
- Github có 2 bản là bản free và bản mất phí.Bản free bạn có thể viết code của bạn lên và bất kì ai cũng có thể xem. Nếu muốn riêng tư thì có thể dùng bản mất phí.
## 2.Ngôn ngữ MARKDOWN
### a. Thẻ tiêu đề
- Markdown sử dụng kí tự # để bắt đầu cho các thẻ tiêu đề, có thể dùng từ 1 đến 6 ký tự # liên tiếp. Mức độ riêu đề giảm dần từ 1 đến 6
Ví dụ :
``#A
##A
###A
….``
Thì #A cho ta tiêu đề lớn nhất trong đoạn bạn cần sử dụng.
### b. Chèn link, chèn ảnh
Để chèn hyperlink bạn chỉ cần paste luôn linh đó vào file .md .

Ví dụ: https://github.com

`https://github.com`
Hoặc thu gọn:

`[GITHUB](https://github.com)`

Kết quả :[GITHUB](https://github.com)

Để chèn ảnh sử dụng cú pháp:

<img src="link_anh_cua_ban">

link ảnh thì thường được tải lên trang https://imgur.com/ để tạo link ảnh.
Ví dụ :


<img src="https://i.imgur.com/KDAzV62.jpg">

### c.Ký tự in đậm, in nghiêng
- Để in đậm một đoạn text bạn chỉ cần làm như sau:

`**từ cần in đậm**`

**từ cần in đậm**

- Để in nghiên một đoạn text bạn chỉ cần làm như sau:
`*từ cần in nghiêng*`
*từ cần in nghiêng*

### d. Trích dẫn, bo chữ
- Để bo một đoạn text thì bạn chỉ cần sử dụng cú pháp sau:
```
`đoạn cần bo`
```
Kết quả:
`đoạn cần bo`

- Để làm nổi bật một đoạn, chẳng hạn như một đoạn  file cấu hình bạn có thể sử dụng cú pháp như ví dụ sau:

    ```sh
    auto eth0
    iface eth0 inet static
    ipaddress 10.10.10.10
	netmask 255.255.255.0
	gateway 10.10.10.1
	dns-nameservers 8.8.8.8
    ```
Kết quả :
```sh
auto eth0
iface eth0 inet static
ipaddress 10.10.10.10
netmask 255.255.255.0
gateway 10.10.10.1
dns-nameservers 8.8.8.8
```

### e. Gạch đầu dòng
- Để sử dụng gạch đầu dòng bạn chỉ cần sử dụng cú pháp sau:
```
- Gạch đầu dòng 1

	  - Con của gạch đầu dòng 1 thì thụt vào 1 tab
```
### f. Tạo bảng
- Bạn có thể xem ví dụ sau để tạo bảng:
```
| Cột 1 Hàng 1 | Cột 2 | Cột 3| Cột 4 |
|--------------|-------|------|-------|
| Hàng 2 | 2 x 1 | 2 x 2 | 2 x 3 | 2 x 4 |
| Hàng 3 | 3 x 1 | 3 x 2 | 3 x 3 | 3 x 4 |
| Hàng 4 | 4 x 1 | 4 x 2 | 4 x 3 | 4 x 4 |
```
Kết quả :


| Cột 1 Hàng 1 | Cột 2 | Cột 3| Cột 4 |
|--------------|-------|------|-------|
| Hàng 2 | 2 x 1 | 2 x 2 | 2 x 3 | 2 x 4 |
| Hàng 3 | 3 x 1 | 3 x 2 | 3 x 3 | 3 x 4 |
| Hàng 4 | 4 x 1 | 4 x 2 | 4 x 3 | 4 x 4 |

