## **Autodesk Construction Cloud Platform (ACC)**

**Nền tảng hợp nhất Autodesk Construction Cloud (ACC)** cung cấp các API cho phép nhà phát triển xây dựng ứng dụng tích hợp với nền tảng ACC nhằm mở rộng khả năng trong hệ sinh thái xây dựng.  
ACC là phần mềm quản lý xây dựng hợp nhất mới của Autodesk.  
Để biết thêm thông tin, vui lòng truy cập trang web Autodesk Construction Cloud.

----------

### **Các API hiện đang được cung cấp bao gồm:**

-   **Account Admin API**:  
    Tự động hóa việc tạo và quản lý dự án, phân công và quản lý người dùng dự án, quản lý danh bạ thành viên và công ty đối tác. Có thể đồng bộ dữ liệu với hệ thống bên ngoài.
    
-   **AutoSpecs API**:  
    Truy cập nhật ký đệ trình bản nháp (draft submittal logs) được trích xuất từ tài liệu đặc tả của dự án xây dựng.
    
-   **Assets API**:  
    Tạo và quản lý tài sản trong dịch vụ ACC Assets. Cho phép định nghĩa cài đặt như danh mục, thuộc tính tùy chỉnh, trạng thái... và tạo/chỉnh sửa tài sản dựa trên các thiết lập đó. Hỗ trợ tìm kiếm nâng cao.
    
-   **Cost Management API**:  
    Truy cập và quản lý dữ liệu chi phí và ngân sách của dự án như ngân sách, hợp đồng, lệnh thay đổi... Có thể xuất/nhập dữ liệu giữa hệ thống bên ngoài và ACC.
    
-   **Data Connector API**:  
    Truy xuất dữ liệu từ các dịch vụ như Admin, Issues, Locations, Submittals, Cost và RFIs để phục vụ phân tích nội bộ. Hỗ trợ nhiều dự án, lập lịch báo cáo định kỳ, và trả dữ liệu ở định dạng phù hợp với công cụ BI như Power BI, Tableau...
    
-   **Files API (Document Management)**:  
    Truy cập, tải lên và chia sẻ bản vẽ 2D, mô hình BIM 3D và các tài liệu dự án khác. (Lưu ý: là một phần của Data Management API.)
    
-   **Forms API**:  
    Truy cập dữ liệu từ module ACC Forms. Cho phép nhóm dự án điền, xem xét và quản lý biểu mẫu an toàn và kỹ thuật.
    
-   **Issues API**:  
    Tạo và cập nhật các vấn đề (issues) trong dự án ACC để theo dõi và xử lý các sự cố như thiết kế, an toàn, nghiệm thu... Hỗ trợ các issue liên quan đến dự án (chưa hỗ trợ pushpin).
    
-   **Locations API**:  
    Cấu hình cây phân cấp vị trí công trình (LBS - Location Breakdown Structure). Cho phép gắn vị trí cho Assets, Issues, Photos, Forms, RFIs và Submittals.
    
-   **Model Coordination API**:  
    Truy cập đầy đủ dịch vụ phối hợp mô hình 3D trên web của ACC. Cho phép phát hiện và xử lý xung đột giữa các mô hình thiết kế.
    
-   **Photos API**:  
    Truy cập dữ liệu ảnh và video lưu trong module ACC Photos. Là nơi tập trung để xem và quản lý hình ảnh dự án.
    
-   **Relationships API**:  
    Tạo, truy xuất và xóa liên kết giữa các thực thể (entity) thuộc các module khác nhau trong ACC.
    
-   **RFIs API (beta)**:  
    Tạo, theo dõi và cập nhật các yêu cầu thông tin (RFI). Hỗ trợ gán người xử lý, chuyển trạng thái và thêm bình luận.
    
    > ⚠️ Chưa hỗ trợ đính kèm file và chưa hỗ trợ RFI liên kết tài liệu (pushpin RFIs).
    
-   **Sheets API**:  
    Xuất bản và phân phối bản vẽ (sheets) phục vụ thi công. Hỗ trợ quản lý sheet, tập phiên bản, tải lên, xuất bản và xuất file.
    
-   **Submittals API**:  
    Tạo mục đệ trình và truy cập dữ liệu đệ trình được lưu trong module ACC Submittals.
    
-   **Takeoff API**:  
    Truy xuất và cập nhật các thiết lập đo bóc khối lượng (takeoff), phân loại, gói đo, kiểu đo và nội dung đi kèm. Hỗ trợ tạo, sửa, xóa và nhập lại (reimport) các phân loại.
    

----------

### **Khả năng tương thích với BIM 360**

Để đảm bảo các ứng dụng BIM 360 hiện có tương thích với dự án ACC, nhiều **endpoint BIM 360 đã được làm tương thích với ACC**. Điều này cho phép bạn tiếp tục sử dụng ứng dụng BIM 360 với các dự án ACC trong khi chờ các ACC API mới được cập nhật.

> ⚠️ Các ứng dụng hiện có tích hợp với BIM 360 và PlanGrid sẽ tiếp tục hoạt động bình thường trong tương lai gần.  
> Xem thêm tại mục **BIM 360 Compatibility** để biết chi tiết.
