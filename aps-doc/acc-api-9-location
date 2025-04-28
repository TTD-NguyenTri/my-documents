# Locations API Field Guide)

Hướng dẫn sử dụng này mô tả các thành phần của dịch vụ **Locations** trong **Autodesk Construction Cloud (ACC)** và cách chúng phối hợp hoạt động cùng nhau.  
Tài liệu này cũng cung cấp các khái niệm then chốt để giúp bạn sử dụng thành công **Locations API**.  
Để biết thêm thông tin chi tiết về Locations, vui lòng tham khảo tài liệu **Locations Help**.

**Lưu ý:** API Locations của ACC **không tương thích** với các dự án BIM 360.

----------

## Hiểu về LBS của dự án (Understanding the project LBS)

**Locations API** cho phép bạn định nghĩa một hệ thống phân cấp (cây) các khu vực xây dựng (locations) cho một dự án.  
Một cây locations thường được gọi là **Location Breakdown Structure (LBS)**; hai thuật ngữ này có thể thay thế cho nhau.

Với một **LBS**, người dùng có thể xác định vị trí liên quan đến từng đối tượng trong dự án như:  
**Assets**, **Issues**, **Photos**, **Forms**, **RFIs** và **Submittals**.  
Nhờ đó, mỗi đối tượng này có thể được gán cho một khu vực xây dựng cụ thể.

----------

## Các nút (Nodes)

Các thành phần của một LBS được gọi là **nút (nodes)**, mỗi node đại diện cho một vị trí.  
Mỗi node bạn thêm vào LBS phải có một **node cha** (parent node), trở thành một **node con** (child node hoặc sub-location).  
Một node cũng có thể có các node con của riêng mình, khi đó nó đồng thời là một **node cha**.

Khi người dùng tạo một dự án, nó sẽ tự động bao gồm một **LBS** chỉ chứa **root node** (nút gốc).  
Root node này được liên kết vĩnh viễn với dự án.

Mỗi node con đại diện cho một khu vực nhỏ hơn trong tòa nhà, được mô tả bởi node cha của nó.

**Ví dụ:** Một tòa nhà (node cha) có thể chứa bốn node con đại diện cho:

-   Móng nền (foundation)
    
-   Tầng 1 (floor 1)
    
-   Tầng 2 (floor 2)
    
-   Mái nhà (roof)
    

----------

## Đường dẫn và cấp bậc của node (Node paths and tiers)

Vị trí của một node trong LBS được xác định bởi **đường dẫn node (node’s path)** — một danh sách bắt đầu từ root node của dự án và kết thúc tại node cha của node hiện tại.  
Mỗi mục trong danh sách này tương ứng với một **cấp bậc (tier)** khác nhau trong LBS.

Một cây Locations trong ACC có thể sâu tối đa **20 cấp bậc (tiers)**.

Khi bạn đi dọc theo cây location từ root node xuống các node con, mỗi cấp sẽ càng chi tiết hóa khu vực cho đến khi bạn đến một node không có con, đại diện cho khu vực nhỏ nhất.

**Ví dụ về đường dẫn đầy đủ:**

> Project > San Leandro campus > 357 Bernoulli Drive > Tầng 4 > Phòng họp Gamma

Tất cả các node con cùng một node cha có một **thứ tự cụ thể (sequence order)**.  
Theo mặc định, node mới sẽ được thêm vào cuối danh sách. Tuy nhiên, bạn có thể chỉnh sửa thứ tự này khi tạo node mới.

**Lưu ý:**  
Số lượng node tối đa (bao gồm cả root node) trong một LBS của Autodesk là **10.000 nodes**.

----------

## Sử dụng LBS (Using the LBS)

Khi **LBS** đã được cấu hình, người dùng của ứng dụng **ACC Build** có thể, trong giao diện người dùng (UI), gán các đối tượng như:  
**Asset**, **Issue**, **Photo**, **Form**, **RFI**, hoặc **Submittal** vào đúng node trong LBS đại diện cho vị trí của đối tượng đó.

----------

## Các thao tác được hỗ trợ (Supported operations)

**Locations API** cung cấp các endpoint cho phép **tạo**, **đọc**, **cập nhật** và **xóa** các node để xác định cấu trúc của LBS:

### `GET nodes`

-   Để **tạo node mới**, bạn cần **ID của node cha** dự kiến.
    
-   Để **đọc**, **cập nhật**, hoặc **xóa** node hiện có, bạn cần **ID của chính node đó**.
    

**Cách sử dụng:**

-   Gọi `GET nodes` **không có** tham số `filter[id]` → truy xuất **tất cả các node** trong LBS.
    
-   Gọi `GET nodes` **có** tham số `filter[id]` → truy xuất **các node cụ thể**.
    

**Lưu ý:**

-   **Root node** là node có `results.parentId` bằng **null**.
    
-   **Node con** có `results.parentId` bằng `results.id` của node cha.
    
-   Bạn có thể xây dựng toàn bộ cấu trúc cây bằng cách xác định cha của từng node.
    

----------

### `POST nodes`

-   Gọi `POST nodes` để **tạo node mới** trong LBS.
    

**Lưu ý:**

-   Không thể tạo hoặc xóa **root node**.
    
-   Khi tạo node mới:
    
    -   Cần chỉ định **parentId** (ID của node cha).
        
    -   Nếu muốn chỉ định thứ tự node mới giữa các anh em, sử dụng thêm query parameters **targetNodeId** và **insertOption**.
        

----------

### `PATCH nodes/:nodeId`

-   Gọi `PATCH nodes/:nodeId` để **chỉnh sửa**:
    
    -   **Tên** node (name)
        
    -   **Mã barcode** của node (barcode)
        

----------

### `DELETE nodes/:nodeId`

-   Gọi `DELETE nodes/:nodeId` để **xóa node**.
    

**Cảnh báo:**  
Khi bạn xóa một node cha, tất cả các node con và các node cháu của nó cũng sẽ bị xóa theo.  
Tất cả các đối tượng (Asset, Issue, Form, ...) liên kết với các vị trí đó cũng sẽ **không còn liên kết** với vị trí nào nữa.