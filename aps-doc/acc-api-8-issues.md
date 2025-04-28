## Issues API

**API Issues** của **Autodesk Construction Cloud (ACC)** cho phép tạo và cập nhật các **issues** trong các dự án ACC của bạn.  
Một **issue** là một mục được tạo ra trong ACC để theo dõi, quản lý và giao tiếp về các nhiệm vụ, sự cố và các điểm cần lưu ý cho đến khi được giải quyết.

**Issues API** bao gồm các chức năng sau:

-   Tạo, cập nhật và truy xuất các issue liên quan đến dự án trong ACC.
    
-   Truy xuất các issue liên quan đến tệp (pushpins).
    
-   Truy xuất quyền cơ bản về issue của người dùng.
    
-   Truy xuất các thiết lập dự án về issue, như: định nghĩa thuộc tính tùy chỉnh (custom attribute fields), ánh xạ (mappings), loại issue (issue types) và danh mục nguyên nhân gốc (root cause categories).
    
-   Thêm và truy xuất bình luận (comments) trên issue.
    
-   Cập nhật trạng thái issue (draft / open / answered / closed), và công bố hoặc bỏ công bố một issue.

----------

## Sự khác biệt giữa BIM 360 và ACC (Differences Between BIM 360 and ACC)

Danh sách dưới đây nêu chi tiết một số khác biệt đáng chú ý giữa **BIM 360 Issues API** và **ACC Issues API**:

-   Quyền trên issue của ACC khác với BIM 360.  
    Ví dụ: Người dùng có quyền **Create for my company** chỉ có thể giao (assign) một issue cho thành viên cùng công ty.  
    Xem thêm `GET users/me` để biết chi tiết. Ngoài ra, một số thuộc tính chỉ có thể được cập nhật bởi người tạo issue hoặc người được giao.  
    Tham khảo tài liệu hướng dẫn để biết thêm chi tiết.
    
-   Các issue trong ACC được tạo ra mặc định ở trạng thái **unpublished** (chưa công bố).  
    Chỉ người tạo issue và người được giao mới có quyền truy cập và chỉnh sửa issue này.  
    Bạn có thể tạo issue ở trạng thái **published** ngay từ đầu, hoặc chuyển đổi issue sang trạng thái published bằng cách cấu hình thuộc tính `published` trong yêu cầu gửi.
    
-   Chúng tôi chỉ công khai **một bộ trạng thái** cho ACC (trong khi ở BIM 360 có hai bộ trạng thái).  
    Lưu ý rằng trong tương lai có thể sẽ hỗ trợ thêm nhiều giá trị trạng thái khác trong cùng một bộ.
    
-   Chúng tôi đã thay thế hệ thống **đính kèm tệp (attachments)** của BIM 360 bằng **tham chiếu (references)** trong ACC.  
    Bạn có thể sử dụng **Relationships API** để định nghĩa và truy xuất các liên kết giữa các module khác nhau, ví dụ liên kết giữa issues và photos.  
    Xem bài blog này để biết thêm thông tin về **Relationships API**.
    
----------

## Hạn chế (Limitations)

Danh sách dưới đây mô tả những hạn chế đã biết của bản phát hành **ACC Issues API**:

-   Không thể thêm issue trực tiếp vào các sheets, mô hình (models) hoặc tệp (pushpins).  
    Bạn có thể truy xuất các issue liên kết với tệp, nhưng hiện tại chưa hỗ trợ truy xuất các issue liên kết với sheets trong công cụ **ACC Build Sheet**.
    
-   Hiện tại chưa có endpoint để lập trình tự động truy xuất **User ID** khi gán người dùng cho issue.  
    Khuyến nghị sử dụng **Data Connector API** để trích xuất các ID.  
    Xem hướng dẫn **Retrieve User Permissions** để biết thêm chi tiết.  
    Sắp tới chúng tôi sẽ phát hành endpoint để truy xuất trực tiếp **Autodesk IDs**.
    
-   Hiện tại chưa hỗ trợ truy xuất **hoạt động của issue (issue activities)**.
    
-   Bạn có thể tải xuống các tham chiếu hình ảnh (photo references) bằng cách truy xuất chúng thông qua **Relationships API** và tải về bằng **Photos API**.  
    Tuy nhiên, hiện tại **không thể tải lên ảnh** qua **Photos API**.  
    Trong tương lai chúng tôi sẽ hỗ trợ chức năng tải ảnh lên.  
    Tạm thời, bạn có thể tải ảnh lên **ACC Files** bằng **Data Management API** và tạo một tham chiếu file cho issue.  
    Xem hướng dẫn trong phần giới thiệu về `POST issues` để biết thêm chi tiết.
    
-   Lưu ý rằng **ACC Issues API** không tương thích với các dự án **BIM 360**.  
    Nếu bạn đang làm việc với BIM 360, hãy sử dụng **BIM 360 Issues API**.
    
-   Hiện tại chỉ có thể kiểm tra quyền đối với **người dùng hiện tại**.  
    Không thể truy xuất mức quyền cho tất cả người dùng.
    
-   Không hỗ trợ các endpoint để **cấu hình quyền (permissions)**.
    
-   Không hỗ trợ các endpoint để **cấu hình loại issue (issue types)** hoặc **cấu hình thuộc tính tùy chỉnh (custom attributes)**.