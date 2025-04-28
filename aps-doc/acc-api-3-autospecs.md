## 📑 AutoSpecs

**AutoSpecs** trong **ACC** cho phép bạn nhanh chóng tạo ra các **bảng đăng ký đệ trình bản nháp (draft submittal logs)** chi tiết và chính xác.  
Bạn có thể **xuất bản** các bảng này lên **Autodesk Docs** và **Autodesk Build** để nhóm dự án sử dụng.

> 🔎 Để biết thêm chi tiết, hãy xem tài liệu trợ giúp **AutoSpecs Help**.

----------

### ✅ Tính năng của AutoSpecs API

AutoSpecs API trong ACC bao gồm các tính năng sau:

-   **Truy xuất toàn bộ bảng đăng ký đệ trình (Smart Register)**  
    → Gồm các yêu cầu đệ trình được AutoSpecs tải lên từ tài liệu đặc tả dự án (project specification).
    
-   **Truy xuất số lượng đệ trình** theo:
    
    -   **Nhóm đệ trình (submittal group)**
        
    -   **Loại đệ trình (submittal type)**
        
-   **Truy xuất số lượng đệ trình theo nhóm**, **phân chia theo mã bộ môn (division code)** trong từng mục đệ trình.
    

----------

### ⚠️ Giới hạn hiện tại (Limitations)

Hiện tại, API **chưa hỗ trợ** các chức năng sau:

-   **Tải lên, trích xuất hoặc cập nhật tài liệu đặc tả dự án**
    
-   **Chỉnh sửa bảng đăng ký đệ trình (Smart Register)**
    
-   **Webhooks**  
    → Bạn cần **poll endpoint `GET metadata`** để kiểm tra trạng thái trích xuất
    
-   **Lọc danh sách đệ trình (filtering submittals)**
    
-   Các API để:
    
    -   **Chỉnh sửa tài liệu đặc tả** (công cụ _Spec View_)
        
    -   **Theo dõi thông tin chi tiết sản phẩm** (công cụ _Product Data_)