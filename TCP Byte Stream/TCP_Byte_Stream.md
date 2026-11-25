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
