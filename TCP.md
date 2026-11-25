**1.1.**      **TCP Byte Stream**

**Câu 1:** Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 806 (thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu là xây dựng một chương trình client tương tác tới server ở trên sử dụng các luồng byte (InputStream/OutputStream) để trao đổi thông tin theo thứ tự:

a. Gửi mã sinh viên và mã câu hỏi theo định dạng "studentCode;qCode". Ví dụ: "B16DCCN999;2B3A6510"

b.  Nhận dữ liệu từ server là một chuỗi các giá trị số nguyên được phân tách nhau bởi ký tự ",". Ví dụ: 1,3,9,19,33,20

c. Tìm và gửi lên server giá trị lớn thứ hai cùng vị trí xuất hiện của nó trong chuỗi.Ví dụ: 20,5

d. Đóng kết nối và kết thúc chương trình.

**Câu 2:** Một chương trình server hỗ trợ kết nối qua giao thức TCP tại cổng 806 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu xây dựng chương trình client thực hiện kết nối tới server trên sử dụng luồng byte dữ liệu (InputStream/OutputStream) để trao đổi thông tin theo thứ tự:

a. Gửi mã sinh viên và mã câu hỏi theo định dạng "studentCode;qCode". Ví dụ: "B16DCCN999;C64967DD"

b. Nhận dữ liệu từ server là một chuỗi gồm các giá trị nguyên được phân tách với nhau bằng  "\|" . Ex: 2\|5\|9\|11

c. Thực hiện tìm giá trị tổng của các số nguyên trong chuỗi và gửi lên server. Ex: 27

d. Đóng kết nối và kết thúc.

**Câu 3:** Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 806 (thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu là xây dựng một chương trình client thực hiện kết nối tới server sử dụng các luồng byte (InputStream/OutputStream) để trao đổi thông tin theo thứ tự:

a. Gửi mã sinh viên và mã câu hỏi theo định dạng "studentCode;qCode". Ví dụ: "B16DCCN999;10048F28".

b. Nhận chuỗi ký tự từ server. Ví dụ: "abcabcbb"

c. Tìm và gửi lên server chuỗi con dài nhất từ chuỗi nhận được mà không có ký tự lặp lại theo format "longestsubstring;length". Ví dụ: "abc;3".

d. Đóng kết nối và kết thúc chương trình.

**Câu 4:** Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 806 (thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu là xây dựng một chương trình client tương tác tới server ở trên sử dụng các luồng byte (InputStream/OutputStream) để trao đổi thông tin theo thứ tự:

a. Gửi mã sinh viên và mã câu hỏi theo định dạng "studentCode;qCode". Ví dụ: "B16DCCN999;2B3A6510"

b. Nhận dữ liệu từ server là một số nguyên n nhỏ hơn 400\. Ví dụ: 7

c. Thực hiện các bước sau đây để sinh ra chuỗi từ số nguyên n ban đầu và gửi lên server. Bắt đầu với số nguyên n:

·        Nếu n là số chẵn, chia n cho 2 để tạo ra số tiếp theo trong dãy.

·        Nếu n là số lẻ và khác 1, thực hiện phép toán n=3\*n+1 để tạo ra số tiếp theo.

·        Lặp lại quá trình trên cho đến khi n=1, tại đó dừng thuật toán.

Kết quả là một dãy số liên tiếp, bắt đầu từ n ban đầu, kết thúc tại 1 và độ dài của chuỗi theo format "chuỗi kết quả; độ dài"  Ví dụ: kết quả với n \= 7 thì dãy: 7 22 11 34 17 52 26 13 40 20 10 5 16 8 4 2 1; 17;

d. Đóng kết nối và kết thúc chương trình.

**Câu 5:** Một chương trình server hỗ trợ kết nối qua giao thức TCP tại cổng 806 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu xây dựng chương trình client thực hiện kết nối tới server trên sử dụng luồng byte dữ liệu (InputStream/OutputStream) để trao đổi thông tin theo thứ tự:

a. Gửi mã sinh viên và mã câu hỏi theo định dạng "studentCode;qCode". Ví dụ: "B16DCCN999;FF49DC02"

b.  Nhận dữ liệu từ server là một chuỗi các giá trị số nguyên được phân tách nhau bởi ký tự "," . Ex: 1,3,9,19,33,20

c.  Thực hiện tìm giá trị khoảng cách nhỏ nhất của các phần tử nằm trong chuỗi và hai giá trị lớn nhất tạo nên khoảng cách đó. Gửi lên server chuỗi gồm "khoảng cách nhỏ nhất, số thứ nhất, số thứ hai". Ex: 1,19,20

d. Đóng kết nối và kết thúc

**Câu 6:** Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 806 (thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu là xây dựng một chương trình client tương tác tới server ở trên sử dụng các luồng byte (InputStream/OutputStream) để trao đổi thông tin theo thứ tự:

a. Gửi mã sinh viên và mã câu hỏi theo định dạng "studentCode;qCode". Ví dụ: "B16DCCN999;A63D9404".

b. Nhận dữ liệu từ server là một chuỗi các số nguyên được sắp xếp ngẫu nhiên, các số được phân tách nhau bởi ký tự ",". Ví dụ: "2,15,4,3,6,8,10,7,1".

c. Sắp xếp tăng dần các giá trị chẵn và sau đó tăng dần các giá trị lẻ trong dãy số. Ví dụ: "\[2, 4, 6, 8, 10\];\[1, 3, 7, 15\]". Gửi chuỗi được sắp xếp này lên server.

d. Đóng kết nối và kết thúc chương trình.

 **Câu 7:** Một chương trình server hỗ trợ kết nối qua giao thức TCP tại cổng 806 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu xây dựng chương trình client thực hiện kết nối tới server sử dụng luồng byte dữ liệu (InputStream/OutputStream) để trao đổi thông tin theo thứ tự:

a. Gửi mã sinh viên và mã câu hỏi theo định dạng "studentCode;qCode". Ví dụ: "B16DCCN999;76B68B3B".

b. Nhận dữ liệu từ server là một chuỗi các giá trị số nguyên được phân tách bởi ký tự ",". Ví dụ: 5,10,20,25,50,40,30,35.

c. Tìm chuỗi con tăng dần dài nhất và gửi độ dài của chuỗi đó lên server. Ví dụ: 5,10,20,25 có độ dài 4\.

d. Đóng kết nối và kết thúc chương trình.

**Câu 8**: Một chương trình server hỗ trợ kết nối qua giao thức TCP tại cổng 806 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu xây dựng chương trình client thực hiện kết nối tới server sử dụng luồng byte dữ liệu (InputStream/OutputStream) để trao đổi thông tin theo thứ tự:

a. Gửi mã sinh viên và mã câu hỏi theo định dạng "studentCode;qCode".  
 Ví dụ: "B16DCCN999;C89DAB45"

b. Nhận dữ liệu từ server là một chuỗi các số nguyên được phân tách bởi ký tự ",".  
 Ví dụ: "8,4,2,10,5,6,1,3"

c. Tính tổng của tất cả các số nguyên tố trong chuỗi và gửi kết quả lên server.  
 Ví dụ: Với dãy "8,4,2,10,5,6,1,3", các số nguyên tố là 2, 5, 3, tổng là 10\. Gửi lên server chuỗi "10".

d. Đóng kết nối và kết thúc chương trình.

**Câu 9**: Một chương trình server hỗ trợ kết nối qua giao thức TCP tại cổng **806** (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu xây dựng chương trình client thực hiện kết nối tới server sử dụng luồng byte dữ liệu (InputStream/OutputStream) để trao đổi thông tin theo thứ tự:

a. Gửi mã sinh viên và mã câu hỏi theo định dạng "studentCode;qCode".  
 Ví dụ: "B16DCCN999;D45EFA12"

b. Nhận dữ liệu từ server là một chuỗi các số nguyên được phân tách bởi ký tự ",".  
 Ví dụ: "10,5,15,20,25,30,35"

c. Xác định hai số trong dãy có tổng gần nhất với giá trị trung bình của toàn bộ dãy. Gửi thông điệp lên server theo định dạng "num1,num2".  
 Ví dụ: Với dãy "10,5,15,20,25,30,35", giá trị trung bình là 20, hai số có tổng gần nhất là 15 và 25\. Gửi lên server chuỗi "15,25".

d. Đóng kết nối và kết thúc chương trình.

**Câu 10**: Một chương trình server hỗ trợ kết nối qua giao thức TCP tại cổng **806** (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu xây dựng chương trình client thực hiện kết nối tới server sử dụng luồng byte dữ liệu (InputStream/OutputStream) để trao đổi thông tin theo thứ tự:

a. Gửi mã sinh viên và mã câu hỏi theo định dạng "studentCode;qCode".  
 Ví dụ: "B16DCCN999;E56FAB67"

b. Nhận dữ liệu từ server là một chuỗi các số nguyên được phân tách bởi ký tự ",".  
 Ví dụ: "1,5,3,8,6,2,7,4"

c. Tìm dãy con liên tiếp dài nhất có tổng chia hết cho 3 \-\> Gửi lên server vị trí bắt đầu và kết thúc của dãy con đó. Ví dụ: Với dãy "1,5,3,8,6,2,7,4", dãy con "5,3,8,6" có tổng là 22, chia hết cho 3 \-\> Gửi lên server chuỗi "1,4".

d. Đóng kết nối và kết thúc chương trình.

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

**1.3.**      **TCP Character Stream**

**Câu 1:** Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 808 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu là xây dựng một chương trình client tương tác với server sử dụng các luồng byte (BufferedWriter/BufferedReader) theo kịch bản sau:

a.     	Gửi một chuỗi gồm mã sinh viên và mã câu hỏi với định dạng "studentCode;qCode". Ví dụ: "B15DCCN999;EC4F899B"

b.     	Nhận một chuỗi ngẫu nhiên là danh sách các một số tên miền từ server. Ví dụ: giHgWHwkLf0Rd0.io, I7jpjuRw13D.io, wXf6GP3KP.vn, MdpIzhxDVtTFTF.edu, TUHuMfn25chmw.vn, HHjE9.com, 4hJld2m2yiweto.vn, y2L4SQwH.vn, s2aUrZGdzS.com, 4hXfJe9giAA.edu

c.     	Tìm kiếm các tên miền .edu và gửi lên server.  Ví dụ: MdpIzhxDVtTFTF.edu, 4hXfJe9giAA.edu

d.     	Đóng kết nối và kết thúc chương trình.

**Câu 2:** Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 808 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5 giây). Yêu cầu là xây dựng một chương trình client thực hiện kết nối tới server và sử dụng luồng ký tự (BufferedWriter/BufferedReader) để trao đổi thông tin theo kịch bản sau:

a. Gửi một chuỗi gồm mã sinh viên và mã câu hỏi với định dạng "studentCode;qCode". Ví dụ: "B15DCCN999;A1B2C3D4".

b. Nhận từ server một chuỗi ngẫu nhiên.

c. Xử lý chuỗi đã nhận theo các bước sau.

·        Tìm từ dài nhất trong trong chuỗi ngẫu nhiên (từ được xác định là chuỗi con phân tách bởi khoảng trắng).

·        Xác định vị trí bắt đầu của từ dài nhất đó trong chuỗi ban đầu.

d. Gửi lần lượt hai giá trị lên server

·        Từ dài nhất xuất hiện trong chuỗi.

·        Vị trí bắt đầu của từ trong chuỗi ban đầu.

e. Đóng kết nối và kết thúc chương trình.

**Câu 3:** Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 808 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu là xây dựng một chương trình client thực hiện kết nối tới server và sử dụng luồng ký tự (BufferedWriter/BufferedReader) để trao đổi thông tin theo kịch bản sau:

a. Gửi một chuỗi gồm mã sinh viên và mã câu hỏi với định dạng "studentCode;qCode". Ví dụ: "B15DCCN999;5E263AE1"

b. Nhận một chuỗi ngẫu nhiên từ server

c. Tách chuỗi đã nhận thành 2 chuỗi và gửi lần lượt theo thứ tự lên server

·        Chuỗi thứ nhất gồm các ký tự và số (loại bỏ các ký tự đặc biệt)

·        Chuỗi thứ hai gồm các ký tự đặc biệt

d. Đóng kết nối và kết thúc chương trình

**Câu 4:** Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 808 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu là xây dựng một chương trình client tương tác tới server sử dụng các luồng ký tự (BufferedReader/BufferedWriter) theo kịch bản dưới đây:

a. Gửi một chuỗi gồm mã sinh viên và mã câu hỏi theo định dạng "studentCode;qCode". Ví dụ: "B15DCCN999;7D6265E3"

b. Nhận một chuỗi ngẫu nhiên từ server

c. Loại bỏ ký tự đặc biệt, số, ký tự trùng và giữ nguyên thứ tự xuất hiện của ký tự. Gửi chuỗi đã được xử lý lên server.

d. Đóng kết nối và kết thúc chương trình

**Câu 5:** Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 808 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu là xây dựng một chương trình client tương tác với server sử dụng các luồng ký tự (BufferedWriter/BufferedReader) theo kịch bản sau:

a. Gửi một chuỗi gồm mã sinh viên và mã câu hỏi với định dạng "studentCode;qCode". Ví dụ: "B15DCCN999;BAA62945"

b. Nhận một chuỗi ngẫu nhiên từ server. Ví dụ: dgUOo ch2k22ldsOo

c. Liệt kê các ký tự (là chữ hoặc số) xuất hiện nhiều hơn một lần trong chuỗi và số lần xuất hiện của chúng và gửi lên server. Ví dụ: d:2,O:2,o:2,2:3,

d. Đóng kết nối và kết thúc chương trình.

**Câu 6:** Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 808 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu là xây dựng một chương trình client tương tác với server sử dụng các luồng ký tự (BufferedReader/BufferedWriter) theo kịch bản sau:

a.     	Gửi một chuỗi gồm mã sinh viên và mã câu hỏi theo định dạng "studentCode;qCode". Ví dụ: "B15DCCN999;DE0C2BF0"

b.     	Nhận lần lượt hai chuỗi ngẫu nhiên từ server

c.     	Loại bỏ các ký tự trong chuỗi thứ nhất mà xuất hiện trong chuỗi thứ hai, yêu cầu giữ nguyên thứ tự xuất hiện của ký tự. Gửi chuỗi đã được xử lý lên server.

d.     	Đóng kết nối và kết thúc chương trình

**Câu 7:** Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 808 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5 giây). Yêu cầu là xây dựng một chương trình client thực hiện kết nối tới server và sử dụng luồng ký tự (BufferedWriter/BufferedReader) để trao đổi thông tin theo kịch bản sau:

a. Gửi một chuỗi gồm mã sinh viên và mã câu hỏi với định dạng "studentCode;qCode". Ví dụ: "B15DCCN999;X1107ABC".

b. Nhận từ server một chuỗi ngẫu nhiên chứa nhiều từ, các từ phân tách bởi khoảng trắng.

c. Thực hiện các bước xử lý:

·        Tách chuỗi thành các từ dựa trên khoảng trắng.

·        Sắp xếp các từ theo thứ tự từ điển (có phân biệt chữ cái hoa thường).

d. Gửi lại chuỗi đã sắp xếp theo thứ tự từ điển lên server.

e. Đóng kết nối và kết thúc chương trình.

**Câu 8:** Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 808 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5 giây). Yêu cầu là xây dựng một chương trình client tương tác với server sử dụng các luồng ký tự (BufferedReader/BufferedWriter) theo kịch bản sau:

a. Gửi một chuỗi chứa mã sinh viên và mã câu hỏi với định dạng "studentCode;qCode".  
 Ví dụ: "B15DCCN999;C1234567"

b. Nhận từ server một chuỗi chứa nhiều từ, các từ được phân tách bởi khoảng trắng.  
 Ví dụ: "hello world this is a test example"

c. Phân loại các từ trong chuỗi theo độ dài: Từ ngắn hơn 4 ký tự; Từ có độ dài từ 4 đến 7 ký tự; Từ dài hơn 7 ký tự. Gửi danh sách các từ theo từng nhóm về server theo định dạng:  
 "\[a, is\],\[hello, world\],\[example\]".

d. Đóng kết nối và kết thúc chương trình.

**Câu 9:** Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 808 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5 giây). Yêu cầu là xây dựng một chương trình client tương tác với server sử dụng các luồng ký tự (BufferedReader/BufferedWriter) theo kịch bản sau:

a. Gửi một chuỗi chứa mã sinh viên và mã câu hỏi với định dạng "studentCode;qCode".  
 Ví dụ: "B15DCCN999;A9876543"

b. Nhận từ server một chuỗi chứa nhiều từ, các từ được phân tách bởi khoảng trắng.  
 Ví dụ: "hello world programming is fun"

c. Thực hiện đảo ngược từng từ trong chuỗi và giữ nguyên thứ tự của chúng. Gửi chuỗi đã được xử lý lên server. Ví dụ: "olleh dlrow gnimmargorp si nuf".

d. Đóng kết nối và kết thúc chương trình.

**Câu 10:** Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 808 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5 giây). Yêu cầu là xây dựng một chương trình client tương tác với server sử dụng các luồng ký tự (BufferedReader/BufferedWriter) theo kịch bản sau:

a. Gửi một chuỗi chứa mã sinh viên và mã câu hỏi với định dạng "studentCode;qCode".  
 Ví dụ: "B15DCCN999;B6543210"

b. Nhận từ server một chuỗi chứa nhiều từ, các từ được phân tách bởi khoảng trắng.  
 Ví dụ: "look at the room with a book"

c. Tìm tất cả các từ trong chuỗi chứa ít nhất hai ký tự nguyên âm. Gửi danh sách các từ này lên server theo định dạng: "look, room, book".

d. Đóng kết nối và kết thúc chương trình.

**1.4.**      **TCP Object Stream**

**Câu 1:** Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 809 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu là xây dựng một chương trình client tương tác với server sử dụng các luồng đối tượng(ObjectOutputStream/ObjectInputStream) theo kịch bản dưới đây:

Biết rằng lớp TCP.Student gồm các thuộc tính (id int,code String, gpa float, gpaLetter String) và trường dữ liệu private static final long serialVersionUID \= 20151107;

a. Gửi đối tượng là một chuỗi gồm mã sinh viên và mã câu hỏi với định dạng "studentCode;qCode". Ví dụ: "B15DCCN999;1D059A3F"

b. Nhận một đối tượng là thể hiện của lớp TCP.Student từ server. Thực hiện chuyển đổi giá trị điểm số gpa của đối tượng nhận được sang dạng điểm chữ và gán cho gpaLetter.  Nguyên tắc chuyển đổi: 3.7 \< gpa \<= 4 \-\> A; 3.0 \< gpa \<= 3.7 \-\> B; 2.0 \< gpa \<= 3.0  \-\> C; 1.0 \< gpa \<= 2.0 \-\> D ; 0 \< gpa \<= 1.0 \-\> F

c. Gửi đối tượng đã được xử lý ở trên lên server.

d. Đóng kết nối và kết thúc chương trình

**Câu 2:** Thông tin sản phẩm vì một lý do nào đó đã bị sửa đổi thành không đúng, cụ thể:

·        Tên sản phẩm bị đổi ngược từ đầu tiên và từ cuối cùng, ví dụ: “lenovo thinkpad T520” bị chuyển thành “T520 thinkpad lenovo”

·        Số lượng sản phẩm cũng bị đảo ngược giá trị, ví dụ từ 9981 thành 1899

Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 809 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu là xây dựng một chương trình client tương tác với server sử dụng các luồng đối tượng (ObjectInputStream / ObjectOutputStream) để gửi/nhận và sửa các thông tin bị sai của sản phẩm. Chi tiết dưới đây:

Đối tượng trao đổi là thể hiện của lớp Laptop được mô tả như sau

•         Tên đầy đủ của lớp: TCP.Laptop

•         Các thuộc tính: id int, code String, name String, quantity int

•         Hàm khởi tạo đầy đủ các thuộc tính được liệt kê ở trên

•         Trường dữ liệu: private static final long serialVersionUID \= 20150711L;

Tương tác với server theo kịch bản

a. Gửi đối tượng là chuỗi chứa mã sinh viên và mã câu hỏi với định dạng "studentCode;qCode". Ví dụ: "B15DCCN999;5AD2B818"

b. Nhận một đối tượng là thể hiện của lớp Laptop từ server

c. Sửa các thông tin sai của sản phẩm về tên và số lượng.  Gửi đối tượng vừa được sửa sai lên server

d. Đóng socket và kết thúc chương trình.

**Câu 3:** Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 809 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5 giây). Yêu cầu là xây dựng một chương trình client tương tác với server sử dụng các luồng đối tượng (ObjectOutputStream/ObjectInputStream) theo kịch bản dưới đây:

Biết lớp TCP.Product gồm các thuộc tính (id int, name String, price double, int discount) và private static final long serialVersionUID \= 20231107;

a. Gửi đối tượng là một chuỗi gồm mã sinh viên và mã câu hỏi với định dạng "studentCode;qCode". Ví dụ: "B15DCCN999;1E08CA31"

b. Nhận một đối tượng là thể hiện của lớp TCP.Product từ server.

c. Tính toán giá trị giảm giá theo price theo nguyên tắc: Giá trị giảm giá (discount) bằng tổng các chữ số trong phần nguyên của giá sản phẩm (price). Thực hiện gán giá trị cho thuộc tính discount và gửi lên đối tượng nhận được lên server.

d. Đóng kết nối và kết thúc chương trình.

**Câu 4:** Thông tin khách hàng cần thay đổi định dạng lại cho phù hợp với khu vực, cụ thể:

•         Tên khách hàng cần được chuẩn hóa theo định dạng mới. Ví dụ: nguyen van hai duong \-\> DUONG, Nguyen Van Hai

•         Ngày sinh của khách hàng hiện đang ở dạng mm-dd-yyyy, cần được chuyển thành định dạng dd/mm/yyyy. Ví dụ: 10-11-2012 \-\> 11/10/2012

•         Tài khoản khách hàng là các chữ cái in thường được sinh tự động từ họ tên khách hàng. Ví dụ: nguyen van hai duong \-\> nvhduong

Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 809 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5s). Yêu cầu là xây dựng một chương trình client tương tác với server sử dụng các luồng đối tượng (ObjectInputStream / ObjectOutputStream) thực hiện gửi/nhận đối tượng khách hàng và chuẩn hóa. Cụ thể:

Đối tượng trao đổi là thể hiện của lớp Customer được mô tả như sau

•         Tên đầy đủ của lớp: TCP.Customer

•         Các thuộc tính: id int, code String, name String, dayOfBirth String, userName String

•         Hàm khởi tạo đầy đủ các thuộc tính được liệt kê ở trên

•         Trường dữ liệu: private static final long serialVersionUID \= 20170711L;

Yêu cầu tương tác với server theo kịch bản dưới đây:

a. Gửi đối tượng là một chuỗi gồm mã sinh viên và mã câu hỏi ở định dạng "studentCode;qCode". Ví dụ: "B15DCCN999;F2DA54F3"

b. Nhận một đối tượng là thể hiện của lớp Customer từ server với các thông tin đã được thiết lập

c. Thay đổi định dạng theo các yêu cầu ở trên và gán vào các thuộc tính tương ứng.  Gửi đối tượng đã được sửa đổi lên server

d. Đóng socket và kết thúc chương trình.

**Câu 5**: Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 809 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5 giây). Yêu cầu là xây dựng một chương trình client tương tác với server sử dụng các luồng đối tượng (ObjectOutputStream/ObjectInputStream) để gửi/nhận và chuẩn hóa thông tin địa chỉ của khách hàng.

Biết rằng lớp TCP.Address có các thuộc tính (id int, code String, addressLine String, city String, postalCode String) và trường dữ liệu private static final long serialVersionUID \= 20180801L.

a. Gửi đối tượng là một chuỗi gồm mã sinh viên và mã câu hỏi với định dạng "studentCode;qCode". Ví dụ: "B15DCCN999;A1B2C3D4"

b. Nhận một đối tượng là thể hiện của lớp TCP.Address từ server. Thực hiện chuẩn hóa thông tin addressLine bằng cách:

* Viết hoa chữ cái đầu của mỗi từ trong addressLine.  
* Định dạng lại mã bưu chính postalCode theo mẫu xxx-xxx, ví dụ: "123456" thành "123-456".

c. Gửi đối tượng đã được chuẩn hóa thông tin địa chỉ lên server.

d. Đóng kết nối và kết thúc chương trình.                      	

**Câu 6:** Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 809 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5 giây). Yêu cầu là xây dựng một chương trình client tương tác với server sử dụng các luồng đối tượng (ObjectOutputStream/ObjectInputStream) theo kịch bản dưới đây:

Biết rằng lớp TCP.EmployeePerformance gồm các thuộc tính (id int, name String, monthlyScores List\<Integer\>, avgScore float, rating String) và trường dữ liệu private static final long serialVersionUID \= 20220915L.

a. Gửi đối tượng là một chuỗi gồm mã sinh viên và mã câu hỏi với định dạng "studentCode;qCode". Ví dụ: "B15DCCN999;E1234FG"

b. Nhận một đối tượng là thể hiện của lớp TCP.EmployeePerformance từ server. Thực hiện tính toán điểm trung bình avgScore từ danh sách điểm hàng tháng monthlyScores, và xác định rating của nhân viên theo quy tắc:

•         Nếu avgScore \>= 90, gán rating là "Excellent".

•         Nếu avgScore \>= 75 và \< 90, gán rating là "Good".

•         Nếu avgScore \>= 60 và \< 75, gán rating là "Average".

•         Nếu avgScore \< 60, gán rating là "Poor".

c. Gửi đối tượng đã được cập nhật avgScore và rating lên server.

d. Đóng kết nối và kết thúc chương trình.

**Câu 7:** Một chương trình server cho phép kết nối qua giao thức TCP tại cổng 809 (hỗ trợ thời gian giao tiếp tối đa cho mỗi yêu cầu là 5 giây). Yêu cầu là xây dựng một chương trình client tương tác với server sử dụng các luồng đối tượng (ObjectOutputStream/ObjectInputStream) để xử lý các thông tin nâng cao của tài khoản ngân hàng.

Biết rằng lớp TCP.BankAccount có các thuộc tính (accountId int, accountHolder String, balance double, transactions List\<Double\>, balanceSummary String) và trường dữ liệu private static final long serialVersionUID \= 20210601L.

a. Gửi đối tượng là một chuỗi gồm mã sinh viên và mã câu hỏi với định dạng "studentCode;qCode". Ví dụ: "B15DCCN999;A1B3D6H"

b. Nhận một đối tượng là thể hiện của lớp TCP.BankAccount từ server. Thực hiện tạo chuỗi balanceSummary bằng cách tổng hợp các giao dịch (transactions) như sau:

	Tính toán tổng số tiền giao dịch trong tháng và gán vào balanceSummary ở định dạng "Total Transactions: \<totalAmount\>".

c. Gửi đối tượng đã được cập nhật balanceSummary lên server.

d. Đóng kết nối và kết thúc chương trình. 