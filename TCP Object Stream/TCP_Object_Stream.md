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
