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
