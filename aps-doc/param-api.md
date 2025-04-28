## Tổng quan

Hiện tại, **Parameters Service** đang được sử dụng bởi **Autodesk Construction Cloud (ACC)**.  
**Parameters Service** là một tính năng thuộc **Account Administration**.

Mỗi tài khoản (account) có thể lưu trữ các **tham số (parameters)** thuộc về tài khoản đó.  
Các tham số được tổ chức theo hai lớp nhóm:

-   **Lớp thứ nhất** dưới tài khoản được gọi là **"groups" (nhóm)**.
    
-   **Lớp thứ hai** dưới group được gọi là **"collections" (bộ sưu tập)**.
    

Hiện tại, **mỗi tài khoản chỉ có thể chứa một "group"**.  
(Tính năng này được thiết kế để mở rộng trong tương lai.)

Mỗi **group** có thể chứa **nhiều collections**.

Hình ảnh dưới đây mô tả cấu trúc tổ chức này.

![image](/img/Field_Guide_Diagram.png)

Một **"parameter" (tham số)** được định nghĩa bởi **tên** và **kiểu dữ liệu** (data type), và thường có thêm các **metadata** bổ sung, chẳng hạn như **category** (danh mục) và **labels** (nhãn).

Trong phần dưới đây, chúng tôi sẽ giải thích từng thuật ngữ này.

----------

## Cấu trúc tổ chức của Parameters (Organizational Structure of Parameters)

-   **Parameter Group** (Nhóm tham số)
    
-   **Collection** (Bộ sưu tập)
    
-   **Parameter** (Tham số)
    

----------

## Thành phần Metadata của Parameter (Composition of Parameter Metadata)

-   **Spec** (Đặc tả)
    
-   **Unit** (Đơn vị)
    
-   **Label** (Nhãn)
    
-   **Category** (Danh mục)
    
-   **Classification Group** (Nhóm phân loại)
    

----------

## Parameter Group

Một **parameter group** là một tập hợp các **collections**, thường được gộp lại với nhau dựa trên cùng một mục đích sử dụng.

## Parameter Collection

Một **parameter collection** là một tập hợp các **tham số (parameters)**, thường được gộp lại dựa trên cùng một mục đích sử dụng.  
Một collection có thể đại diện cho bất kỳ tập hợp tham số nào phù hợp với quy trình làm việc (workflow) của bạn.

**Ví dụ:**

-   Tham số cho Bệnh viện (Hospital)
    
-   Tham số cho Trường học (School)
    
-   Tham số cho Sân bay (Airport Parameters)
    
-   Tham số để chia sẻ với nhà thầu cửa (Parameters to share with door contractor)
    
-   Tham số cho một chủ đầu tư cụ thể (Parameters for a given project owner)
    

**Lưu ý:**  
Bạn nên tạo các tham số trong **collection mặc định** của mình trước, sau đó chia sẻ chúng sang các collection khác khi cần thiết, để phù hợp với hành vi tiêu chuẩn của **Parameters Service**.

## Parameter

Một **parameter** là định nghĩa của một giá trị chi tiết (granular value) của một phần tử mô hình (model element).  
Trong các ứng dụng khác nhau, khái niệm này có thể được gọi bằng các tên khác như **Parameter**, **Property** hoặc **Attribute**.

**Các trường cốt lõi** xác định tham số, bao gồm:

-   `id`
    
-   `name`
    
-   `specId`
    
-   `readOnly`
    

Các trường này là **bất biến** (immutable).

**Mô tả** (description) và **metadata** (siêu dữ liệu) của tham số **có thể được thay đổi** thông qua **Patch Parameters API**.

----------

-   Định nghĩa cốt lõi của một tham số có thể được lấy về bằng cách gọi API **Get Parameter**.
    
    -   Đối với endpoint này, người dùng (Authorization token) **không cần** quyền truy cập vào một tài khoản ACC cụ thể.
        
-   **Mô tả** và **metadata** của tham số được lưu trữ trong **account** và **collection**.
    
    -   Chúng có thể được truy xuất thông qua API **Retrieve Parameters**.

## Spec (Đặc tả)

Một **spec** mô tả **kiểu dữ liệu** (data type) để hiển thị cho người dùng cuối (user-facing presentation).

**Specs** hỗ trợ việc xác định các thuộc tính tùy chỉnh (custom properties) trong các ứng dụng thiết kế, nhằm giúp người dùng cuối có thể chọn đúng kiểu dữ liệu cho một thuộc tính.

**Ví dụ về các đối tượng spec:**

-   Văn bản (Text)
    
-   Có/Không (Yes/No)
    
-   Hình ảnh (Image)
    
-   Chiều dài (Length)
    
-   Điện trở nhiệt (Thermal Resistance)