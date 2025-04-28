## **ACC Account Admin API**

**ACC Account Admin API** cho phép tự động hóa việc thiết lập dự án, phân quyền quản trị viên dự án, quản lý danh bạ thành viên và công ty đối tác, cũng như người dùng dự án trên nhiều sản phẩm. Bạn cũng có thể đồng bộ dữ liệu với các hệ thống bên ngoài.

### **Các chức năng bao gồm:**

-   Tạo và truy xuất thông tin về dự án ACC.
    
    > _Lưu ý_: Các endpoint dự án hỗ trợ cả xác thực 2-legged (kèm ID người dùng) và 3-legged.
    
-   Tạo, truy xuất, cập nhật và xóa người dùng của dự án ACC.
    
    > _Lưu ý_: Các endpoint người dùng dự án cũng hỗ trợ 2-legged và 3-legged.
    
-   Quản lý các công ty đối tác kinh doanh trong toàn bộ sản phẩm.
    
-   Tạo **danh bạ thành viên chính** để quản lý người dùng tài khoản và người dùng dự án trên nhiều sản phẩm.
    
-   Quản lý cấu trúc **đơn vị kinh doanh**, phục vụ tạo các văn phòng khu vực hoặc vị trí dùng trong báo cáo.
    

> ❗ _Lưu ý:_ Các endpoint liên quan đến **dự án ACC** và **người dùng dự án ACC** **không tương thích với BIM 360**.  
> Vui lòng sử dụng **BIM 360 Account Admin API** cho các dự án BIM 360.

----------

### **Gán License cho người dùng ACC**

Để gán license, hãy vào công cụ **Members** trong module **Account Admin** của giao diện người dùng Autodesk Construction Cloud.  
Xem thêm trong tài liệu trợ giúp **ACC Account Admin** để biết chi tiết về quy trình và tính năng.

----------

### **Làm việc với ACC ở các khu vực khác nhau**

-   ACC được lưu trữ tại các trung tâm dữ liệu ở **Mỹ (US)** và **EMEA**.
    
-   **Dữ liệu lưu tại Mỹ sẽ không thể truy cập từ EMEA và ngược lại**.
    
-   **Hầu hết các dịch vụ ACC hỗ trợ tự động định tuyến theo khu vực**, nhưng **ACC Account Admin API hiện không hỗ trợ tính năng này**.
    

#### ⚙️ Cách xử lý:

-   Với các endpoint **chỉ dành cho ACC**, **bạn phải chỉ định vùng (region)** trong header của request.
    
-   Với các endpoint **tương thích BIM 360**, **base URI sẽ khác nhau** giữa US và EMEA.
    

🔍 _Mẹo xác định khu vực lưu trữ dữ liệu_:  
Gọi `GET projects` với cả hai giá trị region trong header.

-   Trả về HTTP `200` → đúng vùng
    
-   Trả về HTTP `404` → sai vùng
    

----------

### **Quản lý Dự án (Projects)**

Bạn có thể tạo 2 loại dự án ACC:

1.  **Dự án thực tế (production project)** – mặc định; tất cả các sản phẩm của tài khoản sẽ được kích hoạt.
    
2.  **Mẫu dự án (project template)** – có thể sao chép để tạo dự án mới.
    

> Lưu ý:

-   Không thể tạo template mới từ template khác.
    
-   Có thể tạo template từ một dự án production hiện có.
    
-   Template chưa được cấu hình hoàn chỉnh, nhưng có thể sử dụng làm điểm bắt đầu.
    

----------

### **Project Members**

Bạn có thể gán bất kỳ người dùng nào trong tài khoản ACC vào một **dự án thực tế** hoặc **mẫu dự án**.

### Mẫu dự án có 2 loại thành viên:

1.  **Thành viên chính** – sẽ được sao chép sang dự án mới khi clone. (Không hoạt động trong template.)
    
2.  **Thành viên cấu hình** – có thể chỉnh sửa template. (Không được sao chép sang dự án mới.)
    

> Khi gọi `GET projects/:projectId/users`, chỉ **trả về thành viên cấu hình** (active trong template).

Bạn có thể gán quyền **thành viên** hoặc **quản trị viên** cho người dùng trong một dự án.

----------

### **Sao chép dự án từ Template**

-   Gọi `POST accounts/:account_id/projects` với tham số phù hợp.
    
-   Các sản phẩm và thiết lập sẽ được sao chép.
    
-   Dịch vụ Account Admin sẽ chạy một **job bất đồng bộ** để kích hoạt sản phẩm.
    

🧩 Gán người quản trị dự án bằng `POST projects/:projectId/users`. Việc này:

-   Gán một user hiện có trong cùng tài khoản làm admin.
    
-   Tự động sao chép toàn bộ thành viên từ template sang dự án mới và kích hoạt họ.
    

----------

### **Giới hạn**

Một số hạn chế hiện tại của ACC Account Admin API:

-   Tất cả sản phẩm trong dự án ACC phải được kích hoạt. Không hỗ trợ tắt sản phẩm/dịch vụ riêng lẻ.
    
-   Không hỗ trợ gán quyền khác nhau cho từng người dùng theo từng sản phẩm.
    
-   Không có endpoint để:
    
    ❌ Theo dõi trạng thái job bất đồng bộ khi tạo dự án hoặc nhập nhiều người dùng.
        
    ❌ Truy xuất danh sách vai trò người dùng trong dự án ACC (khuyến nghị dùng **Data Connector API**).
        
    ❌ Cập nhật hoặc xóa dự án ACC.