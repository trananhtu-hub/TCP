**1.2.**      **TCP Data Stream**

**Câu 1:** Một chương trình máy chủ cho phép kết nối qua TCP tại cổng 807 (hỗ trợ thời gian liên lạc tối đa cho mỗi yêu cầu là 5s), yêu cầu xây dựng chương trình (tạm gọi là client) thực hiện kết nối tới server tại cổng 807, sử dụng luồng byte dữ liệu (DataInputStream/DataOutputStream) để trao đổi thông tin theo thứ tự:

a.   Gửi chuỗi là mã sinh viên và mã câu hỏi theo định dạng "studentCode;qCode". Ví dụ: "B15DCCN999;1D25ED92"

b.   Nhận lần lượt hai số nguyên a và b từ server

c.   Thực hiện tính toán tổng, tích và gửi lần lượt từng giá trị theo đúng thứ tự trên lên server

d.   Đóng kết nối và kết thúc

**Câu 2:** Một chương trình máy chủ cho phép kết nối qua TCP tại cổng 807 (hỗ trợ thời gian liên lạc tối đa cho mỗi yêu cầu là 5s). Yêu cầu là xây dựng chương trình client tương tác với server trên bằng các byte stream (DataInputStream/DataOutputStream) để trao đổi thông tin theo trình tự sau:

a. Gửi một chuỗi chứa mã sinh viên và mã câu hỏi ở định dạng "studentCode;qCode". Ví dụ: "B15DCCN999;B1F1FDCD"

b. Nhận hai số nguyên a và b tương ứng từ máy chủ

c. Tính ước chung lớn nhất, bội chung nhỏ nhất, tổng, tích. Gửi từng giá trị số nguyên theo thứ tự trên đến máy chủ.

d. Đóng kết nối và kết thúc chương trình.

**Câu 3:** Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 807 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5 giây). Yêu cầu sinh viên xây dựng chương trình client để tương tác với server, sử dụng các luồng data (DataInputStream và DataOutputStream) để trao đổi thông tin theo thứ tự sau:

a. Gửi mã sinh viên và mã câu hỏi: Chuỗi gồm mã sinh viên và mã câu hỏi theo định dạng "studentCode;qCode". Ví dụ: "B15DCCN999;D68C93F7".

b. Nhận một số nguyên hệ thập phân từ server. Ví dụ:: 15226\.

c. Chuyển đổi số nguyên nhận được sang hệ nhị phân và thập lục phân, ghép thành chuỗi và gửi lên server. Ví dụ: 15226 sẽ thành "11101101111010;3B7A"

d. Đóng kết nối: Kết thúc chương trình sau khi gửi kết quả chuyển đổi.

**Câu 4:** Mật mã caesar, còn gọi là mật mã dịch chuyển, để giải mã thì mỗi ký tự nhận được sẽ được thay thế bằng một ký tự cách nó một đoạn s. Ví dụ: với s \= 3 thì ký tự “A” sẽ được thay thế bằng ký tự “D”.

Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 807 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu là xây dựng chương trình client tương tác với server trên, sử dụng các luồng byte (DataInputStream/DataOutputStream) để trao đổi thông tin theo thứ tự:

a.   Gửi một chuỗi gồm mã sinh viên và mã câu hỏi theo định dạng "studentCode;qCode". Ví dụ: "B15DCCN999;D68C93F7"

b.   Nhận lần lượt chuỗi đã bị mã hóa caesar và giá trị dịch chuyển s nguyên

c.   Thực hiện giải mã ra thông điệp ban đầu và gửi lên Server

d.   Đóng kết nối và kết thúc chương trình.

**Câu 5:** Một chương trình server cho phép kết nối qua TCP tại cổng 807 (hỗ trợ thời gian liên lạc tối đa cho mỗi yêu cầu là 5 giây). Yêu cầu là xây dựng chương trình client tương tác với server bằng các byte stream (DataInputStream/DataOutputStream) để trao đổi thông tin theo trình tự sau:

a. Gửi một chuỗi chứa mã sinh viên và mã câu hỏi ở định dạng "studentCode;qCode". Ví dụ: "B10DCCN000;A1B2C3D4".

b. Nhận lần lượt từ server giá trị n và mảng chứa n số nguyên. Ví dụ: 5, 2, 9, 3, 6, 8

c. Tính tổng, trung bình cộng, và phương sai của mảng. Gửi kết quả lần lượt lên server dưới dạng số nguyên và float. Ví dụ, gửi lên lần lượt: 31, 6.2, 4.5599995.

d. Đóng kết nối và kết thúc chương trình.

**Câu 6:** Một chương trình servercho phép kết nối qua TCP tại cổng 807 (hỗ trợ thời gian liên lạc tối đa cho mỗi yêu cầu là 5 giây). Yêu cầu là xây dựng chương trình client tương tác với server bằng các byte stream (DataInputStream/DataOutputStream) để trao đổi thông tin theo trình tự sau:

a. Gửi một chuỗi chứa mã sinh viên và mã câu hỏi ở định dạng "studentCode;qCode". Ví dụ: "B10DCCN000;0D135D6A".

 

b. Nhận lần lượt từ server một số nguyên n, là số lần tung xúc xắc và n giá trị tương ứng với giá trị xúc xắc tung được. Ví dụ: nhận n \= 21 từ máy chủ, có nghĩa bạn sẽ tiếp tục nhận lần lượt 21 giá trị là 1,6,4,4,4,3,2,6,3,4,5,4,5,2,4,5,4,6,1,5,5.

c. Tính xác suất xuất hiện của các giá trị \[1,2,3,4,5,6\] khi tung xúc sắc và gửi lần lượt xác suất này (dưới dạng float) lên server theo đúng thứ tự. Ví dụ gửi lên server lần lượt 6 giá trị là 0.0952381, 0.0952381, 0.0952381, 0.33333334, 0.23809524, 0.14285715

d. Đóng kết nối và kết thúc chương trình.

**Câu 7:** Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 807 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5 giây). Yêu cầu sinh viên xây dựng chương trình client để tương tác với server, sử dụng các luồng data (DataInputStream và DataOutputStream) để trao đổi thông tin theo thứ tự sau:

a. Gửi mã sinh viên và mã câu hỏi: Chuỗi gồm mã sinh viên và mã câu hỏi theo định dạng "studentCode;qCode". Ví dụ: "B15DCCN999;D68C93F7".

b. Nhận một số nguyên hệ thập phân từ server. Ví dụ: 45

c. Chuyển đổi số nguyên nhận được sang hệ nhị phân và gửi chuỗi kết quả này lại cho server. Ví dụ: 45 sẽ thành chuỗi "101101"

d. Đóng kết nối và kết thúc chương trình.

**Câu 8:** Một chương trình server cho phép kết nối qua TCP tại cổng 807 (hỗ trợ thời gian liên lạc tối đa cho mỗi yêu cầu là 5 giây). Yêu cầu xây dựng chương trình client thực hiện giao tiếp với server sử dụng luồng data (DataInputStream/DataOutputStream) để trao đổi thông tin theo thứ tự:

a. Gửi mã sinh viên và mã câu hỏi theo định dạng "studentCode;qCode".  
 Ví dụ: "B10DCCN001;A1B2C3D4"

b. Nhận một số nguyên hệ thập phân từ server. Ví dụ: 255

c. Chuyển đổi số nguyên nhận được sang hai hệ cơ số 8 và 16\. Gửi lần lượt chuỗi kết quả lên server. Ví dụ: Với số 255 hệ thập phân, kết quả gửi lên sẽ là hai chuỗi "377" và "FF".

d. Đóng kết nối và kết thúc chương trình.

**Câu 9:** Một chương trình server cho phép kết nối qua TCP tại cổng 807 (hỗ trợ thời gian liên lạc tối đa cho mỗi yêu cầu là 5 giây). Yêu cầu xây dựng chương trình client thực hiện giao tiếp với server sử dụng luồng data (DataInputStream/DataOutputStream) để trao đổi thông tin theo thứ tự:

a. Gửi mã sinh viên và mã câu hỏi theo định dạng "studentCode;qCode".  
 Ví dụ: "B10DCCN002;B4C5D6E7"

b. Nhận chuỗi chứa mảng số nguyên từ server, các phần tử được phân tách bởi dấu phẩy ",". Ví dụ: "1,3,2,5,4,7,6"

c. Xác định độ dài của dãy con tăng dần dài nhất trong mảng.  
 Gửi lần lượt kết quả là chuỗi con tăng dài nhất và số nguyên độ dài của dãy đó lên server.

Ví dụ: Với mảng "1,3,2,5,4,7,6", dãy con tăng dần dài nhất là "1,3,5,7" có độ dài 4\. Gửi chuỗi "1,3,5,7"  và  số nguyên 4 lên server.

d. Đóng kết nối và kết thúc chương trình.

**Câu 10:** Một chương trình server cho phép kết nối qua TCP tại cổng 807 (hỗ trợ thời gian liên lạc tối đa cho mỗi yêu cầu là 5 giây). Yêu cầu xây dựng chương trình client thực hiện giao tiếp với server sử dụng luồng data (DataInputStream/DataOutputStream) để trao đổi thông tin theo thứ tự:

a. Gửi mã sinh viên và mã câu hỏi theo định dạng "studentCode;qCode".  
 Ví dụ: "B10DCCN003;C6D7E8F9"

b. Nhận lần lượt:

·         Một số nguyên k (số lần xoay vòng).

·         Chuỗi chứa mảng số nguyên, các phần tử được phân tách bởi dấu phẩy ",".  
 Ví dụ: Nhận k \= 3 và "1,2,3,4,5".

c. Thực hiện xoay vòng mảng k bước sang phải và gửi mảng đã xoay lên server.  
 Ví dụ: Với k \= 3 và mảng "1,2,3,4,5", kết quả là "3,4,5,1,2". Gửi chuỗi kết quả "3,4,5,1,2" lên server.

d. Đóng kết nối và kết thúc chương trình.
