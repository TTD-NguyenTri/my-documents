## **ACC Assets API**

### 📌 **Giới thiệu**

Thành phần chính của dịch vụ **Assets** là **asset**, thường dùng để mô tả một thiết bị thực tế như máy móc, thiết bị điện, hệ thống cơ khí,...

Tuy nhiên, để mô tả **assets**, trước tiên bạn cần **định nghĩa các cài đặt Assets** trong một dự án. Các cài đặt này bao gồm:

- Một **cây phân cấp danh mục (category hierarchy)**
- Một hoặc nhiều **bộ trạng thái (status sets)**
- Một tập hợp **thuộc tính tùy chỉnh (custom attributes)** (tùy chọn)

> 👉 Việc thiết lập **cài đặt Assets** là bước đầu tiên cần thực hiện khi chuẩn bị sử dụng dịch vụ Assets trong dự án.

----------

### ⚙️ **Cài đặt Assets**

Một **asset** thường đại diện cho một thiết bị thực tế như: quạt, ổ cắm điện, ống gió, cửa sổ, v.v...

Mỗi bản ghi asset trong dịch vụ **Assets** bao gồm:

- Một **ID riêng cho dự án** (còn gọi là **B3F ID**)  
- Một tập hợp **thuộc tính chuẩn** — luôn có mặt trong mọi asset  
- Một tập hợp tùy chọn các **thuộc tính tùy chỉnh của asset (Asset custom attributes)**  

  > Các thuộc tính tùy chỉnh này do bạn định nghĩa, nhằm mô tả các đặc điểm riêng biệt quan trọng của asset đối với tổ chức của bạn.  
  > *Lưu ý:* Đây là **thuộc tính riêng của dịch vụ Assets**, không được chia sẻ với các dịch vụ khác.

Bảng dưới đây liệt kê các thuộc tính chuẩn giúp định nghĩa mỗi asset trong hệ thống ACC Assets:   

   | Tên thuộc tính        | Bắt buộc? | Mô tả |
|------------------------|------------|-------|
| **Category**           | Có         | Một danh mục duy nhất từ cây danh mục của dự án (sẽ được mô tả sau). |
| **Status**             | Có         | Một trạng thái duy nhất từ bộ trạng thái được cung cấp bởi danh mục của asset. Ví dụ: “Ordered”, “Installed”. |
| **Client Asset ID**    | Có         | Tên hiển thị cho asset, ví dụ “Ổ cắm 220V”. Đây **không phải là ID duy nhất**, không nên nhầm lẫn với asset ID (ID duy nhất). Trong giao diện tiếng Anh và tệp export, thuộc tính này có nhãn là “Name”. |
| **Description**        | Không      | Mô tả đầy đủ cho asset, ví dụ “Cổng Ethernet trên bàn họp”. |
| **Barcode**            | Không      | Chuỗi chứa mã vạch được gán cho asset, có định dạng tùy thuộc vào hệ thống mã vạch bạn sử dụng. |
| **Location ID**        | Không      | Một vị trí duy nhất từ cây vị trí của dự án. Cây này được tạo và quản lý bởi dịch vụ Locations, và Locations API cung cấp giá trị dùng cho thuộc tính này. Ví dụ vị trí đầy đủ: *San Leandro campus > 357 Bernoulli Drive > Tầng 4 > Phòng họp Gamma*. |
    
----------

### 📂 **Categories – Danh Mục Tài Sản**


Một **category (danh mục)** định nghĩa một nhóm asset (tài sản) có cùng các đặc điểm chung.  
Mỗi danh mục xác định cách mô tả các asset thuộc danh mục đó: gồm những **thuộc tính tùy chỉnh (custom attributes)** nào và những **trạng thái (statuses)** nào có thể có.

> 🔸 **Mỗi asset bắt buộc phải được gán vào một danh mục duy nhất.**

----------

### 🌳 Category Tree

-   Trong mỗi dự án, Assets settings sẽ thiết lập một Category Tree.
    
-   Cây danh mục này là **cấu trúc kế thừa** bắt đầu từ một **root category (gốc)**.
    
-   Cây có thể sâu tối đa **10 cấp**.
    
-   Ví dụ:  
    `Root → Electrical → Wiring / Outlets / Breakers → ...`
    

----------

### 🔁 Cơ chế kế thừa:

-   **Status Set (Bộ trạng thái)**:  
    Kế thừa từ bộ trạng thái **gần nhất được chỉ định rõ ràng** bởi tổ tiên (cha, ông...).  
    → Có thể ghi đè bằng cách chỉ định một bộ trạng thái mới.
    
-   **Custom Attributes (Thuộc tính tùy chỉnh)**:  
    → **Kế thừa toàn bộ** từ các danh mục tổ tiên.  
    → Có thể **thêm mới** nhưng **không ghi đè**. Tức là thuộc tính được tích lũy dần qua các cấp.
    

----------

### Mỗi danh mục bao gồm:

-   **ID danh mục (categoryId)**  
    Được tạo tự động. Là duy nhất trong **một dự án**, kiểu chuỗi số nguyên.
    
-   **ID danh mục toàn cục (categoryUniqueId)**  
    Được áp dụng từ ngày 2022-10-08. Là **ID duy nhất trên toàn hệ thống**, dùng với các API mới.
    
-   **Tên danh mục (name)**  
    Bắt buộc.  
    → Phải **duy nhất trong các danh mục cùng cấp (siblings)**  
    → Có thể trùng ở các nhánh khác nhau trong cây.
    
-   **Mô tả (description)** _(tùy chọn)_  
    Chuỗi mô tả danh mục.
    
-   **Bộ trạng thái liên kết (statusSet)**  
    Bộ trạng thái các asset thuộc danh mục này có thể có.  
    → Có thể kế thừa hoặc chỉ định riêng.
    
-   **Thuộc tính tùy chỉnh liên kết (customAttributes)** _(tùy chọn)_  
    Những thuộc tính bổ sung để mô tả asset.  
    → Kế thừa từ cha, và có thể thêm mới. Các danh mục con tiếp tục kế thừa toàn bộ.
    
-   **Liên kết kế thừa (inheritance)**  
    Liên kết đến **danh mục cha** và các **danh mục con** (nếu có).

----------

### **Statuses và Status Sets**

**Status set** (đôi khi còn được gọi là _status step set_ trong API) là một **tập hợp các trạng thái (statuses)** có thể được sử dụng trong một danh mục (category).

-   Khi tạo mới một status set, bạn có thể **tạo và liên kết các trạng thái** cho nó ngay từ đầu.
    
-   Sau đó, bạn có thể **thêm mới**, **cập nhật**, hoặc **xóa** trạng thái trong status set.
    
    > ⚠️ Chỉ có thể xóa một trạng thái nếu **không có asset nào đang sử dụng nó.**
    

----------

### Mỗi status set bao gồm:

-   **ID duy nhất (statusSetId)**  
    → Được tạo tự động. Là duy nhất **trên toàn bộ hệ thống**, không chỉ trong một dự án.
    
-   **Tên hiển thị (display name)**  
    → Ví dụ: _“Electrical Statuses”_  
    → Bắt buộc khi tạo, và phải **duy nhất trong phạm vi dự án**.  
    → Tên này sẽ được hiển thị trong giao diện người dùng khi làm việc với status set.
    
-   **Mô tả (description)** _(tùy chọn)_  
    → Chuỗi mô tả về status set.
    
-   **Danh sách các trạng thái**  
    → Ít nhất 1 trạng thái được liên kết với status set này.
    

----------

### 🔁 Mối liên hệ giữa category và status set

-   Mỗi **category chỉ có một status set duy nhất được liên kết**.
    
-   Danh mục gốc (**root category**) có một **status set mặc định**, và status set này sẽ được **tự động kế thừa** bởi tất cả các danh mục con nếu không có status set nào khác được chỉ định rõ ràng.
    

> Nếu không thiết lập status set riêng trong một dự án, tất cả các asset trong dự án đó sẽ sử dụng bộ trạng thái mặc định từ danh mục gốc.

-   **Status set mặc định của root category không thể bị xóa hoặc thay thế**, nhưng **có thể chỉnh sửa nội dung** (thêm, sửa, xóa trạng thái bên trong).
    

----------

### ✅ Các giá trị mặc định ban đầu của root status set gồm:

1.  Specified
    
2.  Ordered
    
3.  Delivered
    
4.  Installed
    
5.  Pre-Start-Up
    
6.  Start-Up
    
7.  Pre-Functional Performance Tests
    
8.  Functional Performance Tests
    
9.  Acceptance
    
10.  Post-Acceptance

----------

## 🧩 **Custom Attributes – Thuộc Tính Tùy Chỉnh**

**Asset custom attributes** là các thuộc tính bổ sung cho asset, được sử dụng để mô tả các đặc điểm riêng biệt quan trọng đối với tổ chức ghi nhận asset đó.  
Ví dụ:

-   “Nhà thầu phụ trách”
    
-   “Điện áp (Voltage)”
    

> 🔸 Các thuộc tính này **chỉ áp dụng trong dịch vụ Assets** và **không được chia sẻ với các dịch vụ khác**.

----------

### ✅ Một số đặc điểm chính:

-   **Tùy chọn hoàn toàn**  
    → Không xuất hiện trong dự án nếu **không được định nghĩa rõ ràng**.
    

----------

### Mỗi custom attribute bao gồm:

-   **ID duy nhất (customAttributeId)**  
    → Tự động tạo khi thuộc tính được tạo.  
    → Là duy nhất **trên toàn hệ thống (cross-project)**.
    
-   **Tên hiển thị (display name)**  
    → Ví dụ: “Voltage”  
    → Bắt buộc khi tạo.  
    → Tên này **phải duy nhất trong một dự án**, và sẽ hiển thị trong giao diện người dùng (Assets UI).
    
-   **Mô tả (description)** _(tùy chọn)_  
    → Mô tả ý nghĩa hoặc mục đích sử dụng của thuộc tính.
    
-   **Kiểu dữ liệu (data type)**  
    → Bắt buộc.  
    → Xác định loại dữ liệu cho giá trị nhập vào, ví dụ: chuỗi, số, ngày tháng...
    
-   **Cài đặt “required” (bắt buộc nhập)**  
    → Cho biết liệu asset có **bắt buộc phải có giá trị** cho thuộc tính này hay không.  
    → Áp dụng khi nhập hoặc chỉnh sửa asset **bằng tay (manual)**, không áp dụng cứng nếu asset được import từ file (ví dụ XLSX).
    
-   **Giá trị hợp lệ & giá trị mặc định** _(nếu được thiết lập)_  
    → Cho phép giới hạn lựa chọn và tự động điền giá trị cho thuộc tính khi tạo asset.
    

----------

### 📌 Cách sử dụng:

-   Để sử dụng một custom attribute cho asset, nó **phải được liên kết với một category**.
    
-   Khi đã liên kết:
    
    -   Custom attribute sẽ **có hiệu lực trong danh mục đó**
        
    -   Sẽ **kế thừa xuống toàn bộ danh mục con**
        

> Việc kế thừa các thuộc tính tùy chỉnh trong cây danh mục là **tích lũy**:  
> Danh mục con sẽ kế thừa tất cả thuộc tính từ danh mục cha **và bổ sung thêm thuộc tính riêng nếu có**.

----------

> 📝 _Lưu ý:_  
> Danh mục gốc (**root category**) **mặc định không chứa thuộc tính tùy chỉnh nào**, trừ các **dự án cũ (legacy projects)** đã từng sử dụng thuộc tính chuẩn (về phần này sẽ nói ở mục kế tiếp).

----------

## 🗂 **Standard Attributes & Backward Compatibility**

**Thuộc tính chuẩn (standard attributes)** có mặt trong **tất cả các asset**, **bất kể danh mục nào**, và **không thể bị chỉnh sửa**.  
Phần mô tả asset ở trên đã liệt kê đầy đủ các thuộc tính chuẩn này cho từng asset.

Trong **các phiên bản trước đây của dịch vụ Assets**, có rất nhiều thuộc tính chuẩn được sử dụng, nhưng hiện tại **nhiều thuộc tính trong số đó đã bị ngưng sử dụng (deprecated)**.

Để **duy trì khả năng tương thích ngược** với các dự án đã từng sử dụng những thuộc tính chuẩn cũ này, hệ thống đã **chuyển các thuộc tính chuẩn cũ thành thuộc tính tùy chỉnh (custom attributes)** và liên kết chúng với **danh mục gốc (root category)**.

→ Các thuộc tính được chuyển đổi này sẽ **được kế thừa bởi tất cả các danh mục** trong dự án và sẽ **giữ lại các giá trị trước đây** giống như khi chúng còn là thuộc tính chuẩn.

> ⚠️ Trong các **dự án mới được tạo**, những thuộc tính tùy chỉnh cho khả năng tương thích ngược này **sẽ không có**.
    

----------

## 📍 **Locations**

Giá trị vị trí có thể được cung cấp (không bắt buộc) cho **thuộc tính chuẩn "Location"** của một asset.

Những giá trị này **được tạo và quản lý bên ngoài dịch vụ Assets**, cụ thể là bởi **dịch vụ Locations**.

Các vị trí (locations) được tổ chức dưới dạng **cây kế thừa (inheritance tree)**, trong đó mỗi cấp sẽ mô tả cụ thể hơn về vị trí khi bạn đi sâu dần từ gốc xuống các nhánh con.

Ví dụ về một vị trí đầy đủ:

**San Leandro campus > 357 Bernoulli Drive > Tầng 4 > Phòng họp Gamma**.

----------

## 🗺 Sơ đồ thành phần cài đặt (Settings Components Diagram)

Sơ đồ dưới đây mô tả **mối quan hệ giữa các thành phần khác nhau trong cài đặt của dịch vụ Assets**, bao gồm:

<ảnh>

---

## 🔁 **Kích Hoạt / Vô Hiệu Hóa Cài Đặt**

**Assets API** cho phép bạn **vô hiệu hóa (deactivate)** và **kích hoạt lại (reactivate)** các thành phần cài đặt của Assets.  
→ Điều này giúp bạn **tạm thời loại bỏ một thành phần khỏi sử dụng**, rồi **khôi phục lại khi cần**, mà **không cần phải tạo mới**.

Bạn có thể vô hiệu hóa hoặc kích hoạt lại các thành phần sau:

-   Danh mục (**Categories**)
    
-   Thuộc tính tùy chỉnh (**Asset custom attributes**)
    
-   Trạng thái (**Statuses**)
    
-   Bộ trạng thái (**Status sets**)

----------

## 🔗 **Relationships – Liên kết**

**Dịch vụ Relationships** định nghĩa các **liên kết giữa các thực thể (entities)** thuộc các **dịch vụ khác nhau của Autodesk**, được gọi là **"domains"** trong Relationships API.

Ví dụ:  
Một **asset** có thể được **liên kết với một issue**, tạo nên mối liên kết giữa hai dịch vụ khác nhau (Assets và Issues).

> Bạn có thể tìm hiểu chi tiết hơn trong tài liệu **Relationships Field Guide**.

----------


## Asset Relationships)

**Dịch vụ Relationships** định nghĩa các **liên kết (relationships)** giữa những **đối tượng (entities)** thuộc **các dịch vụ khác nhau của Autodesk**, được gọi là **domains** trong Relationships API.

> Ví dụ: Một **asset** có thể được liên kết với một **issue**, tạo nên mối quan hệ giữa dịch vụ **Assets** và **Issues**.

Bạn có thể tìm hiểu thêm trong tài liệu: **Relationships Field Guide**.

----------

### 🔍 Cách nhìn của Relationships API đối với dịch vụ Assets:

-   Dịch vụ **Assets** được xem là **một domain riêng**, bao gồm **hai đối tượng**:
    
    -   `assets` (tài sản)
        
    -   `categories` (danh mục)
        

Relationships API có thể:

-   **Liên kết `assets` và `categories` với các thực thể trong các domain khác**, ví dụ:
    
    -   `issues` (vấn đề)
        
    -   `rfis` (yêu cầu thông tin)
        
    -   `submittals` (hồ sơ đệ trình)

Điều này giúp tạo ra một hệ thống dữ liệu **liên kết chặt chẽ xuyên suốt các module**, phục vụ cho việc quản lý và theo dõi toàn bộ vòng đời xây dựng trong **Autodesk Construction Cloud (ACC)**.
    

Điều này giúp tạo nên **các kết nối xuyên dịch vụ**, phục vụ cho quản lý dữ liệu một cách thống nhất và linh hoạt hơn trong toàn bộ hệ thống ACC.