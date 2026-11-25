**Câu 1:**
Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 2211 (thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu là xây dựng một chương trình client tương tác tới server ở trên sử dụng SocketChannel và ByteBuffer để trao đổi thông tin theo giao thức frame: 4 byte độ dài (int32) + payload (UTF-8).

Lưu ý: server & client đều phải đọc đủ dữ liệu bằng vòng lặp (readFully) do server luôn chia nhỏ dữ liệu khi gửi. Trình tự trao đổi như sau:

a. Gửi mã sinh viên và mã câu hỏi theo định dạng studentCode;qCode.

Ví dụ: B16DCCN999;fkdRJYuX

b. Nhận dữ liệu từ server gồm đúng 3 frame liên tiếp. Payload của mỗi frame là một phần của cùng một HTTP request, client phải nối 3 payload theo đúng thứ tự để thu được chuỗi HTTP request hoàn chỉnh (các dòng phân tách bởi \r\n và kết thúc bằng \r\n\r\n).

c. Từ chuỗi HTTP request hoàn chỉnh, trích xuất và gửi lại lên server theo định dạng METHOD;PATH;HOST trong đó PATH luôn bao gồm query-string.

d. Đóng kết nối và kết thúc chương trình.

**Câu 2:**
Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 2211 (thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu là xây dựng một chương trình client tương tác tới server ở trên sử dụng SocketChannel và ByteBuffer để trao đổi thông tin theo giao thức frame: 4 byte độ dài (int32) + payload (UTF-8).

Lưu ý: server & client đều phải đọc đủ dữ liệu bằng vòng lặp (readFully) do server luôn chia nhỏ dữ liệu khi gửi. Trình tự trao đổi như sau:

a. Gửi mã sinh viên và mã câu hỏi theo định dạng studentCode;qCode.

Ví dụ: B16DCCN999;ucpQ9zAh

b. Nhận dữ liệu từ server gồm đúng 2 frame liên tiếp. Payload của mỗi frame là một phần của cùng một chuỗi JSON đơn giản trên một dòng (không xuống dòng). Client phải nối 2 payload theo đúng thứ tự để thu được chuỗi JSON hoàn chỉnh.

c. Trích xuất các trường event, user, ok và gửi lại lên server theo định dạng event=<event>;user=<user>;ok=<0|1> (true=1, false=0).

d. Đóng kết nối và kết thúc chương trình.