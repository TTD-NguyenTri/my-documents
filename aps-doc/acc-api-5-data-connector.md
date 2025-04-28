
## Data Connector API

Tài liệu này mô tả các thành phần chính của API Data Connector thuộc Autodesk Construction Cloud (ACC) và cách các thành phần này hoạt động cùng nhau.

----------

## Các thành phần chính

### 1. **Data Requests (Yêu cầu dữ liệu)**

Sử dụng API Data Connector bắt đầu bằng một yêu cầu dữ liệu. Một yêu cầu này bao gồm các tham số quan trọng sau:

-   **Tài khoản**: Chỉ định tài khoản muốn trích xuất dữ liệu.
    
    -   Tham số tuỳ chọn: Chỉ lấy dữ liệu của các dự án đang hoạt động _(Active projects)_.
        
-   **Nhóm dịch vụ** _(Service groups)_: Các nhóm dịch vụ để lấy dữ liệu, hiện hỗ trợ:
    
    -   Admin (Project và Account)
        
    -   Issues (Vấn đề)
        
    -   Locations (Vị trí)
        
    -   Submittals (Hồ sơ đệ trình)
        
    -   Cost (Chi phí)
        
    -   RFIs (Yêu cầu thông tin)
        
-   **Lịch trình** _(Schedule)_: Xác định lịch trích xuất dữ liệu:
    
    -   Chạy ngay lập tức và chỉ một lần.
        
    -   Lặp lại định kỳ: hàng ngày, hàng tuần, hàng tháng hoặc hàng năm trong một khoảng thời gian xác định.
        
-   **Dự án** _(Project)_:
    
    -   Bắt buộc nếu người dùng là quản trị dự án _(Project Admin)_.
        
    -   Tuỳ chọn nếu người dùng là quản trị tổng thể _(Executive Overview)_.
        
    -   Có thể chỉ định nhiều mã dự án để trích xuất cùng lúc nhiều dự án.
        
-   **Callback URL** _(URL gọi lại, tuỳ chọn)_:
    
    -   URL được Data Connector gọi khi hoàn tất việc trích xuất dữ liệu.
        

**Quản lý và kiểm tra trạng thái**:

-   Các yêu cầu khi tạo ra sẽ được lưu lại. Người dùng có thể chỉnh sửa hoặc xoá yêu cầu này về sau, kể cả khi quá trình trích xuất dữ liệu đã hoàn tất.
    
-   Người dùng có thể:
    
    -   Xem danh sách tất cả các yêu cầu hiện tại.
        
    -   Kiểm tra trạng thái của từng yêu cầu.
        
    -   Xem dữ liệu mỗi yêu cầu đã trả về.
        

**Điều chỉnh trạng thái kích hoạt**:

-   Một yêu cầu có thể được thiết lập trạng thái không hoạt động _(inactive)_ để dừng việc trích xuất theo lịch trình, hoặc chuyển lại trạng thái hoạt động _(active)_ bất kỳ lúc nào.
    

----------

### 2. **Jobs (Công việc)**

Khi một yêu cầu dữ liệu được khởi động, dịch vụ Data Connector sẽ sinh ra một **job (công việc)** để thực hiện việc trích xuất dữ liệu theo các thông số đã định nghĩa.

-   Sau khi job hoàn tất, Data Connector gửi một email thông báo cho người dùng tạo yêu cầu.
    
-   Email chứa liên kết dẫn đến thông tin chi tiết về kết quả job đó.
    
-   Nếu yêu cầu có chỉ định một URL callback, dịch vụ cũng sẽ thực hiện yêu cầu POST đến URL đó kèm theo thông tin về việc thực thi job.
    
-   Mỗi yêu cầu dữ liệu chứa một danh sách tất cả các job mà nó đã tạo ra. Người dùng có thể kiểm tra lại từng job bất kỳ lúc nào để xem dữ liệu trích xuất cụ thể là gì.
    

----------

### 3. **Data Extracts (Dữ liệu trích xuất)**

Dữ liệu trích xuất là toàn bộ dữ liệu trả về từ một job đã thực hiện thành công. Một dữ liệu trích xuất bao gồm:

-   Một bộ các file CSV, mỗi file chứa một bộ dữ liệu riêng biệt.
    
-   Một file ZIP chứa tất cả các file CSV, kèm theo một file README mô tả thông tin chi tiết về cấu trúc dữ liệu _(schema)_ của từng file CSV.
    

**Kiểm tra nội dung**:

-   Người dùng có thể kiểm tra một dữ liệu trích xuất để biết những thành phần nào bên trong, và dung lượng của từng file.
    

**Tải dữ liệu trích xuất**:

-   Khi yêu cầu tải dữ liệu trích xuất thông qua API, dịch vụ Data Connector sẽ trả về một URL có chữ ký _(signed URL)_, URL này có hiệu lực trong 60 giây.
    
-   Người dùng có thể dùng URL này để tải xuống một phần hoặc toàn bộ dữ liệu trích xuất: các file CSV, file README, hoặc file ZIP chứa tất cả.
    
-   Miễn là người dùng bắt đầu tải dữ liệu trong vòng 60 giây kể từ khi nhận URL, quá trình tải có thể kéo dài tuỳ thời gian cần thiết mà không bị gián đoạn.
    

----------

### 4. **Lịch trình yêu cầu và khoảng thời gian lấy dữ liệu**

API Data Connector sử dụng một số thuộc tính liên quan đến lịch trình để kiểm soát thời điểm job chạy và một thuộc tính dữ liệu để xác định phạm vi thời gian của dữ liệu được trích xuất mỗi lần chạy.

-   **scheduleInterval, reoccuringInterval, effectiveFrom, effectiveTo**: Xác định thời điểm thực thi job.  
    Ví dụ: Bạn có thể lên lịch để chạy định kỳ hàng ngày, hàng tuần, hàng tháng hoặc hàng năm, bắt đầu vào thời điểm xác định bởi `effectiveFrom` và kết thúc vào `effectiveTo`. Thuộc tính `reoccuringInterval` định nghĩa số khoảng thời gian giữa các lần chạy (ví dụ: cứ hai tuần một lần).
    
-   **dateRange** _(khoảng thời gian lấy dữ liệu)_: Xác định phạm vi dữ liệu sẽ được trích xuất mỗi lần thực thi. Hiện tại thuộc tính này chỉ áp dụng cho dịch vụ Activities.  
    Ví dụ:
    
    -   `TODAY`: Lấy dữ liệu trong ngày hiện tại (từ 00:00 UTC đến thời điểm thực thi).
        
    -   `PAST_7_DAYS`: Lấy dữ liệu trong 7 ngày gần nhất.
        
    -   `MONTH_TO_DATE`: Lấy dữ liệu từ đầu tháng hiện tại đến thời điểm thực thi.
        

Ví dụ cụ thể:  
Một yêu cầu có thông số như sau:

-   `scheduleInterval = MONTH`
    
-   `reoccuringInterval = 1`
    
-   `dateRange = PAST_7_DAYS`
    

→ Sẽ chạy định kỳ hàng tháng và lấy dữ liệu trong 7 ngày gần nhất mỗi lần chạy.

Cách làm này cho phép người dùng linh hoạt trong việc chọn lịch trình và dữ liệu mục tiêu.

----------

### 5. **Tutorials (Hướng dẫn mẫu)**

Một tài liệu hướng dẫn _(tutorial)_ thể hiện một số trường hợp sử dụng phổ biến của API Data Connector. Hướng dẫn này được chia làm ba giai đoạn, mỗi giai đoạn được trình bày trên một trang riêng biệt.

| Giai đoạn hướng dẫn | Mô tả |
| :--- | :--- |
| Gửi một yêu cầu dữ liệu | Minh họa cách gửi một yêu cầu dữ liệu để trích xuất dữ liệu từ các nhóm dịch vụ được chỉ định, theo một lịch trình xác định, từ trong một tài khoản BIM 360/ACC. Yêu cầu dữ liệu này sẽ tạo ra một công việc (job) để truy xuất dữ liệu theo yêu cầu. |
| Tìm và cập nhật một yêu cầu dữ liệu | Minh họa cách truy xuất danh sách các yêu cầu dữ liệu đã lưu và thay đổi trạng thái hoạt động (active/inactive) của một yêu cầu cụ thể. |
| Tìm một job và lấy dữ liệu trích xuất | Minh họa cách truy xuất danh sách các công việc (jobs) được sinh ra bởi yêu cầu dữ liệu; cách lấy danh sách các tệp tin nằm trong dữ liệu trích xuất của một công việc cụ thể; và cách tải xuống một hoặc nhiều tệp tin từ một công việc cụ thể. |