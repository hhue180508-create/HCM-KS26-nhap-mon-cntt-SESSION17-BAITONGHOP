# **BÀI TỔNG HỢP SESSION 16: TRÌNH DUYỆT WEB VÀ CÔNG CỤ LÀM VIỆC CỦA DEVELOPER**

## **PHẦN A: THIẾT LẬP PROFILE VÀ BOOKMARK CHUẨN DEV**

### **Câu 1\. Nếu tiếp tục sử dụng chung một Profile cho GitHub cá nhân và GitHub công ty thì điều gì xảy ra?**

Nếu tiếp tục sử dụng chung một Chrome Profile cho cả GitHub cá nhân và GitHub công ty thì rất dễ xảy ra tình trạng nhầm lẫn hoặc xung đột phiên đăng nhập (Session Conflict). Nguyên nhân là do Cookies của các tài khoản được lưu trong cùng một môi trường User Data Directory. Khi hai tài khoản có cơ chế xác thực hoặc chính sách quản lý phiên không tương thích, việc đăng nhập có thể ảnh hưởng đến phiên đang sử dụng.

Ngoài ra, lịch sử duyệt web, Bookmark và các dữ liệu cá nhân cũng bị trộn lẫn với dữ liệu công việc. Điều này vừa gây bất tiện khi sử dụng vừa làm tăng nguy cơ lộ thông tin cá nhân.

### **Câu 2\. Áp dụng mô hình 3 Profile chuẩn Developer**

Tôi sẽ chia trình duyệt thành 3 Profile riêng biệt như sau:

| STT | Tên Profile | Mục đích sử dụng |
| ----- | ----- | ----- |
| 1 | Personal | Dùng cho GitHub cá nhân, Facebook, Gmail và các hoạt động giải trí. |
| 2 | Company\_Work | Dùng cho GitHub công ty, Email công việc, tài liệu dự án và các công cụ lập trình. |
| 3 | Sandbox/Test | Dùng để kiểm thử website, thử nghiệm API, kiểm tra Cookies và thực hành các chức năng mới. |

Việc chia thành 3 Profile giúp tôi dễ dàng chuyển đổi giữa các môi trường làm việc mà không phải liên tục đăng xuất rồi đăng nhập lại. Mỗi Profile có Cookies, History, Bookmarks và Extensions riêng nên dữ liệu cũng được quản lý độc lập hơn.

### **Câu 3\. Thiết kế cấu trúc Bookmark gồm 3 thư mục**

Tôi sẽ sắp xếp Bookmark thành 3 thư mục để dễ tìm kiếm và sử dụng:

**1\. 01\_Personal**

* Facebook: Sử dụng mạng xã hội cá nhân.  
* Gmail cá nhân: Kiểm tra và quản lý email riêng.

**2\. 02\_Company\_Work**

* GitHub: Quản lý mã nguồn và dự án của công ty.  
* Google Workspace: Phục vụ trao đổi và làm việc nhóm.

**3\. 03\_Dev\_Tools**

* MDN Web Docs: Tra cứu kiến thức HTML, CSS và JavaScript.  
* JSON Formatter: Hỗ trợ đọc và định dạng dữ liệu JSON.

Tôi chọn cách sắp xếp này vì mỗi thư mục có một mục đích riêng, giúp thanh Bookmark gọn gàng và tiết kiệm thời gian tìm kiếm khi làm việc.

### **Câu 4\. Đồng nghiệp mượn máy 5 phút để tra cứu thì nên sử dụng chế độ nào?**

Tôi sẽ cho đồng nghiệp sử dụng **Guest Profile (Chế độ khách)**. Đây là lựa chọn phù hợp vì người sử dụng có một phiên duyệt web tạm thời, không truy cập trực tiếp vào Bookmark, lịch sử và tài khoản đã đăng nhập trong Profile cá nhân.

Sau khi sử dụng xong, chỉ cần đóng toàn bộ cửa sổ Guest để xóa dữ liệu duyệt web của phiên đó. Nhờ vậy, thông tin cá nhân của tôi được bảo vệ tốt hơn.

---

## **PHẦN B: CHỌN ĐÚNG EXTENSION HỖ TRỢ**

### **Câu 1\. Nên cài Extension thuộc nhóm nào?**

Với đường link API chứa dữ liệu JSON thô mà mentor gửi, tôi sẽ chọn nhóm **Dev Suite**, cụ thể là tiện ích **JSON Formatter**.

Lý do là dữ liệu JSON thô thường khó đọc vì các thông tin nằm liền nhau và chưa được phân cấp rõ ràng. JSON Formatter giúp sắp xếp dữ liệu thành từng dòng, có thụt lề và phân cấp dễ nhìn hơn, từ đó thuận tiện cho việc kiểm tra API.

Hai nhóm còn lại không phù hợp bằng vì:

* **Productivity Suite:** Chủ yếu hỗ trợ quản lý công việc, ghi chú và nâng cao hiệu suất làm việc.  
* **Security Suite:** Tập trung vào bảo mật, quyền riêng tư và kiểm soát các nguy cơ trên trình duyệt.

Vì vậy, Dev Suite là lựa chọn phù hợp nhất với công việc đọc và kiểm tra dữ liệu API.

### **Câu 2\. Nên chọn quyền Site Access nào?**

Tôi chọn **On click** vì tiện ích chỉ cần hoạt động khi tôi chủ động nhấn vào nó.

Việc giới hạn quyền truy cập giúp Extension không tự động hoạt động trên tất cả website, hạn chế nguy cơ truy cập dữ liệu không cần thiết và phù hợp với nguyên tắc cấp quyền tối thiểu (Least Privilege).

---

## **PHẦN C: PHÂN TÍCH LUỒNG HTTP REQUEST**

### **Câu 1\. Khi nhập test.internal-tool.com và nhấn Enter, trình duyệt xử lý như thế nào?**

Quá trình xử lý HTTP Request Flow gồm 4 giai đoạn chính:

1. **DNS Resolution:** Trình duyệt tìm địa chỉ IP tương ứng với tên miền website.  
2. **TCP/TLS Connection:** Trình duyệt thiết lập kết nối với máy chủ. Nếu sử dụng HTTPS thì sẽ thực hiện thêm quá trình bắt tay TLS để bảo mật dữ liệu.  
3. **HTTP Request/Response:** Trình duyệt gửi yêu cầu HTTP đến máy chủ và nhận phản hồi trả về.  
4. **Browser Rendering:** Trình duyệt xử lý HTML, CSS và JavaScript rồi hiển thị giao diện website cho người dùng.

### **Câu 2\. Phân biệt lỗi 404 và 500**

| Mã trạng thái | Ý nghĩa | Lỗi thường nằm ở đâu? | Hướng debug ban đầu |
| ----- | ----- | ----- | ----- |
| 404 Not Found | Không tìm thấy tài nguyên được yêu cầu. | URL, Route hoặc Endpoint không tồn tại. | Kiểm tra lại đường dẫn URL và Endpoint của API. |
| 500 Internal Server Error | Máy chủ gặp lỗi trong quá trình xử lý yêu cầu. | Thường nằm ở phía Backend hoặc Server. | Kiểm tra Server Logs, xử lý API và truy vấn cơ sở dữ liệu. |

Theo tôi, khi gặp lỗi 404 nên kiểm tra đường dẫn trước vì có thể nhập sai URL hoặc Endpoint. Còn với lỗi 500, cần kiểm tra sâu hơn ở phía máy chủ để tìm nguyên nhân khiến API không xử lý được yêu cầu.

### **Câu 3\. Muốn xem mã trạng thái HTTP thì mở Tab nào?**

Tôi sẽ mở tab **Network** trong DevTools vì đây là nơi hiển thị các Request và Response giữa trình duyệt với máy chủ. Tại đây, tôi có thể kiểm tra Status Code, Request URL, Method và nội dung Response để xác định API có hoạt động bình thường hay không.

Các tab còn lại có chức năng khác:

* **Elements:** Kiểm tra và chỉnh sửa HTML, CSS trực tiếp trên trình duyệt.  
* **Console:** Xem lỗi JavaScript và chạy các câu lệnh kiểm tra.  
* **Application:** Kiểm tra Cookies, Local Storage, Session Storage và các dữ liệu lưu trữ của website.

---

## **PHẦN D: CHẨN ĐOÁN CACHE VÀ COOKIES**

### **Câu 1\. Dev đã sửa CSS nhưng nhấn F5 vẫn thấy giao diện cũ. Nguyên nhân và cách khắc phục?**

Theo tôi, nguyên nhân có thể là do Browser Cache vẫn đang lưu phiên bản CSS cũ. Khi nhấn F5, trình duyệt có thể tiếp tục sử dụng tài nguyên đã lưu trước đó nên giao diện chưa được cập nhật.

Để khắc phục, tôi sẽ nhấn **Ctrl \+ Shift \+ R (Hard Reload)** để yêu cầu trình duyệt tải lại tài nguyên.

Ngoài ra, có thể mở DevTools, chọn tab Network và tích vào **Disable cache**, sau đó tải lại trang để kiểm tra phiên bản CSS mới nhất.

Cách làm này chỉ thay đổi cách trình duyệt tải và hiển thị tài nguyên, không chỉnh sửa file CSS gốc của dự án.

### **Câu 2\. Cookie session\_id không có dấu tích ở cột HttpOnly thì có rủi ro gì?**

Nếu Cookie `session_id` không được bật thuộc tính **HttpOnly**, JavaScript trên website có thể đọc được Cookie thông qua `document.cookie`.

Trong trường hợp website xuất hiện lỗ hổng **XSS (Cross-Site Scripting)**, kẻ tấn công có thể lợi dụng lỗ hổng này để đánh cắp Session ID, từ đó có nguy cơ chiếm quyền sử dụng phiên đăng nhập của người dùng.

Để hạn chế rủi ro, cần bật thuộc tính HttpOnly cho Cookie phiên đăng nhập. Ngoài ra, nên kết hợp thêm Secure và SameSite để tăng cường bảo mật.

### **Câu 3\. Muốn đăng xuất nhưng vẫn giữ nguyên Cache thì phải làm gì?**

Nếu chỉ muốn đăng xuất mà không xóa Cache ảnh và CSS, tôi sẽ mở DevTools, chọn tab **Application**, vào mục **Cookies**, chọn đúng tên miền và xóa Cookie phiên đăng nhập `session_id`.

Sau đó tải lại trang để kiểm tra trạng thái đăng nhập.

Cách này giúp xóa phiên đăng nhập mà không cần sử dụng chức năng Clear Browsing Data, nên các tài nguyên đã lưu trong Browser Cache vẫn được giữ lại.

---

## **PHẦN E: DEBUG BẰNG INSPECT ELEMENT VÀ NETWORK TAB**

### **Câu 1\. Nút Đăng nhập bị lệch màu so với thiết kế thì xử lý như thế nào?**

Đầu tiên, tôi nhấn **F12** để mở DevTools, sau đó chọn tab **Elements** và sử dụng công cụ Inspect Element bằng tổ hợp phím `Ctrl + Shift + C`.

Tiếp theo, tôi nhấn trực tiếp vào nút Đăng nhập để tìm phần tử HTML tương ứng. Trong khu vực Styles, tôi tìm thuộc tính `background-color` và thử thay đổi mã màu ngay trên trình duyệt.

Sau khi thay đổi, tôi quan sát giao diện để xem màu sắc đã phù hợp với thiết kế hay chưa. Nếu đúng, tôi sẽ ghi lại mã màu và gửi cho Developer phụ trách để cập nhật vào file CSS gốc.

Lưu ý: Thao tác này chỉ có tác dụng kiểm tra tạm thời trên trình duyệt, không làm thay đổi mã nguồn của dự án.

### **Câu 2\. Quy trình 4 Bước Debugging khi API Request hiển thị màu đỏ**

Khi thấy một API Request hiển thị màu đỏ trong tab Network, tôi sẽ thực hiện lần lượt 4 bước:

**Bước 1: Identify (Xác định lỗi)**

Tìm Request đang bị lỗi trong Network và xác định API nào đang gặp vấn đề.

**Bước 2: Inspect (Kiểm tra)**

Nhấn vào Request để xem các thông tin như Request URL, Request Method, Status Code, Headers và Response.

**Bước 3: Analyze (Phân tích)**

Dựa vào Status Code và nội dung Response để tìm nguyên nhân. Ví dụ, nếu là 404 thì kiểm tra URL hoặc Endpoint, còn nếu là 500 thì cần kiểm tra lỗi phía Backend.

**Bước 4: Report (Báo cáo)**

Ghi lại thông tin API bị lỗi, mã trạng thái và kết quả kiểm tra, sau đó gửi cho mentor hoặc Developer phụ trách để cùng xử lý.

### **Câu 3\. Muốn chỉ xem API và lấy dữ liệu mới nhất thì cần bật những thao tác nào?**

Tôi sẽ thực hiện hai thao tác trong tab **Network**:

1. Chọn bộ lọc **Fetch/XHR** để chỉ hiển thị các yêu cầu API, không bị lẫn với hình ảnh, CSS hay các tài nguyên khác.  
2. Tích chọn **Disable cache** để trình duyệt không sử dụng HTTP Cache trong khi DevTools đang mở.

Sau đó, tôi tải lại trang để quan sát các API Request và kiểm tra dữ liệu trả về từ máy chủ.

---

## **KẾT LUẬN**

Sau khi học Session 16, tôi hiểu rõ hơn cách sử dụng trình duyệt như một công cụ hỗ trợ công việc của Developer, chứ không chỉ đơn giản là dùng để truy cập website.

Tôi biết cách phân chia Profile để quản lý tài khoản cá nhân và công ty, sắp xếp Bookmark để dễ tìm kiếm tài liệu, lựa chọn Extension phù hợp và sử dụng DevTools để kiểm tra lỗi website.

Đặc biệt, kiến thức về Cache, Cookies, HTTP Request Flow và Network Tab giúp tôi hiểu được nguyên nhân của một số lỗi thường gặp trong quá trình phát triển web. Đây là những kỹ năng cần thiết để tôi có thể làm việc hiệu quả hơn và tự tin hơn khi bắt đầu thực tập tại công ty công nghệ.

