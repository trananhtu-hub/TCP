**Câu 1:**
Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 2210 (thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu là xây dựng một chương trình client tương tác tới server ở trên sử dụng GZIPInputStream/GZIPOutputStream để trao đổi thông tin (mỗi thông điệp là một dòng text UTF-8 kết thúc bằng ‘\n’ và toàn bộ dữ liệu truyền/nhận đều được nén GZIP), theo thứ tự sau:

a. Gửi mã sinh viên và mã câu hỏi theo định dạng studentCode;qCode.

Ví dụ: B16DCCN999;GZLEN01

b. Nhận dữ liệu từ server, sau khi giải nén là một chuỗi văn bản.

c. Thực hiện đảo ngược chuỗi nhận được, sau đó mã hóa chuỗi đã đảo ngược sang định dạng Base64. Gửi kết quả lên server theo khuôn dạng: <reversed_string>|<base64_string> Ví dụ: Nhận 123 → Đảo ngược thành 321 → Base64 của 321 là MzIx → Gửi lên: 321|MzIx

d. Đóng kết nối và kết thúc chương trình.

**Câu 2:**
Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 2210 (thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu là xây dựng một chương trình client tương tác tới server ở trên sử dụng GZIPInputStream/GZIPOutputStream để trao đổi thông tin (mỗi thông điệp là một dòng text UTF-8 kết thúc bằng ‘\n’ và toàn bộ dữ liệu truyền/nhận đều được nén GZIP), theo thứ tự sau:

a. Gửi mã sinh viên và mã câu hỏi theo định dạng studentCode;qCode.

Ví dụ: B16DCCN999;GZCRC_LEN03

b. Nhận dữ liệu từ server, sau khi giải nén là một chuỗi văn bản.

c. Sắp xếp các ký tự trong chuỗi nhận được theo thứ tự từ điển (tăng dần theo mã ASCII). Sau đó gửi chuỗi kết quả đã sắp xếp lên server.

Ví dụ: Nhận về dbca1 thì gửi lên server 1abcd

d. Đóng kết nối và kết thúc chương trình.