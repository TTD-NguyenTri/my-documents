
## GIỚI THIỆU CHUNG

Các API của BIM 360 cho phép các nhà phát triển xây dựng ứng dụng tích hợp với nền tảng Autodesk BIM 360 nhằm mở rộng các chức năng của nó trong hệ sinh thái xây dựng.

Lưu ý rằng phần lớn tài liệu về API của BIM 360 được đặt trong bộ tài liệu riêng dành cho BIM 360 API. Tuy nhiên, các endpoint của BIM 360 liên quan đến lưu trữ tài liệu và quản lý tài liệu chủ yếu nằm trong phần tài liệu của Data Management API.

## BIM 360 ACCOUNT ADMIN

**API BIM 360 Account Admin** Cho phép quản lý tài khoản Autodesk BIM 360 cùng với các dự án, thành viên và dữ liệu công ty liên quan. API này bao gồm các chức năng sau:

- Tạo, cập nhật và truy xuất thông tin về các dự án BIM 360.

- Truy xuất thông tin về người dùng trong dự án BIM 360. Lưu ý rằng các endpoint dành cho người dùng dự án hỗ trợ cả xác thực hai bước (two-legged) và ba bước (three-legged).

- Quản lý các công ty đối tác kinh doanh trên nhiều dịch vụ.

- Tạo một thư mục thành viên tổng thể để quản lý người dùng tài khoản và người dùng dự án trên các dịch vụ.

- Quản lý cấu trúc các đơn vị kinh doanh, có thể được sử dụng để tạo các văn phòng khu vực hoặc vị trí dùng cho mục đích báo cáo.

## BIM 360 ASSETS

**Assets API** cung cấp quyền truy cập lập trình vào các chức năng của dịch vụ BIM 360 Assets. Bạn có thể sử dụng nó để định nghĩa thiết lập tài sản và quản lý các tài sản trong phạm vi thiết lập đó. Các tính năng của Assets API bao gồm:

-   Tạo và chỉnh sửa các danh mục tài sản, thiết lập một cây phân cấp danh mục để gán danh mục cho từng tài sản.
    
-   Tạo và chỉnh sửa các bộ trạng thái, bao gồm các trạng thái có thể được gán cho tài sản.
    
-   Tạo và chỉnh sửa các thuộc tính tùy chỉnh có thể gán giá trị cho tài sản.
    
-   Liên kết các bộ trạng thái và thuộc tính tùy chỉnh với các danh mục để đảm bảo rằng các tài sản trong từng danh mục có một tập hợp trạng thái và thuộc tính cụ thể, giúp mô tả chính xác tài sản đó.
    
-   Tạo, chỉnh sửa và xóa tài sản.
    
-   Tìm kiếm và truy xuất danh sách tài sản bằng các bộ lọc tìm kiếm mạnh mẽ.
    
-   Tìm kiếm và truy xuất các thành phần thiết lập như danh mục, bộ trạng thái và thuộc tính tùy chỉnh.
    
-   Tạo và xóa các liên kết quan hệ (được quản lý bởi dịch vụ Relationships) giữa tài sản với danh mục và các thực thể bên ngoài như sự cố (issues) và tài liệu.
    
-   Truy xuất tập hợp các mã lỗi có thể được trả về bởi Assets API.

---

### **ℹ️ Hiện tại, Assets API có một số giới hạn:**

-   Không hỗ trợ xác thực hai bước (2-legged authentication).
    
-   Chưa cung cấp các endpoint để đồng bộ rõ ràng giữa dữ liệu tài sản lưu cục bộ và dữ liệu lưu trên dịch vụ. Tuy nhiên, có thể sử dụng phương pháp thay thế bằng cách lọc theo thuộc tính `updatedAt` để phát hiện các thay đổi kể từ lần kiểm tra gần nhất.


## BIM 360 CHECKLISTS

**BIM 360 Checklists API** theo dõi thông tin về các checklist (danh sách kiểm tra) và mẫu checklist trong một dự án. API này bao gồm các chức năng sau:

-   Theo dõi và phân tích tiến độ thực hiện của một checklist.
    
-   Lọc và sắp xếp các checklist và mẫu checklist.
    
-   Truy xuất thông tin chi tiết về các mục (items), phần (sections) và tệp đính kèm của một checklist.
    
-   Tải xuống các tệp đính kèm của checklist.

-   Tải xuống chữ ký trong phần checklist từ kho lưu trữ S3.

---

### **Tạo Checklist**

Lưu ý rằng trong Checklist API, checklist được gọi là **instance** (thể hiện).

Dữ liệu gửi (payload) của một instance có thể bao gồm thông tin về các phần (sections), mục (items), và tệp đính kèm (attachments) của instance đó.

----Ảnh

Có thể tái tạo lại một checklist từ dữ liệu bằng cách sử dụng các đối tượng quan hệ (relationship objects) trong phần phản hồi (response payload) để sắp xếp lại các phần (sections), mục (items), và tệp đính kèm (attachments), từ đó tái tạo lại cấu trúc phân cấp của một instance (checklist).  
Để biết thêm chi tiết, vui lòng tham khảo endpoint `GET instances/:id`.

**ℹ️ Lưu ý**: Hiện tại chưa hỗ trợ đánh dấu (markups) và submittals.

## BIM 360 COST MANAGEMENT

Sử dụng **Cost Management API**, bạn có thể thực hiện các thao tác sau:

-   Đọc mẫu mã ngân sách (budget code templates), và đọc, tạo, cập nhật, cũng như nhập (import) các phân đoạn và giá trị của mã ngân sách.
    
-   Đọc, tạo, cập nhật và nhập (tạo hàng loạt) các hạng mục ngân sách (budget items).
    
-   Đọc, tạo và cập nhật các gói hợp đồng (contract packages).
    
-   Đọc, tạo, cập nhật và xóa hợp đồng chính (main contracts) và các hạng mục của hợp đồng chính.
    
-   Đọc, tạo, cập nhật và xóa các hạng mục trong Bảng khối lượng thanh toán (Schedule of Values - SOV).
    
-   Đọc, tạo, cập nhật các lệnh thay đổi (change orders) và hạng mục chi phí (cost items).
    
-   Đọc, tạo, cập nhật và xóa các chi phí (expenses).
    
-   Đọc, tạo, cập nhật và xóa các hạng mục chi phí (expense items).
    
-   Đọc thông tin thanh toán và các hạng mục thanh toán.
    
-   Đọc, tạo, cập nhật và xóa các hạng mục theo dõi hiệu suất (performance tracking items) và các phiên bản của chúng.
    
-   Đọc, tạo, cập nhật và xóa bảng chấm công (timesheets).
    
-   Tải lên và tải xuống tệp đính kèm cho ngân sách, hợp đồng, lệnh thay đổi và hạng mục chi phí.
    
-   Tải xuống tài liệu hoặc các gói tệp được tạo từ lệnh thay đổi và hợp đồng.
    
-   Đăng ký (subscribe) các loại sự kiện Webhook do Cost API tạo ra để ứng dụng của bạn có thể theo dõi và phản hồi.

## BIM 360 DATA CONNECTOR

**BIM 360 Data Connector API** cho phép xuất dữ liệu từ các module dịch vụ của BIM 360, để bạn có thể tạo các báo cáo và phân tích tùy chỉnh, làm giàu dữ liệu bằng cách kết hợp với dữ liệu riêng của bạn, và — nếu muốn — lưu trữ dữ liệu đó trong hệ thống lưu trữ nội bộ (on-premise) của bạn.  
Dịch vụ Data Connector có quyền truy cập vào **tất cả các dự án** trong một tài khoản, giúp bạn có cái nhìn tổng quan về toàn bộ hoạt động của tài khoản đó.

Dữ liệu từ dịch vụ Data Connector được cung cấp dưới dạng **tệp CSV**, một định dạng được hỗ trợ rộng rãi bởi các công cụ phân tích dữ liệu như **Microsoft Power BI**, **Tableau** và **Microsoft Excel**.  
Dữ liệu trả về bao gồm tất cả các đối tượng trong một dịch vụ.  
Ví dụ:

-   Với dịch vụ **Admin**, dữ liệu trả về bao gồm người dùng, dự án và công ty.
    
-   Với dịch vụ **Issues**, dữ liệu bao gồm sự cố (issues), nguyên nhân gốc rễ (root causes), và bình luận (comments).

---

### **Sử dụng Data Connector API vào các công việc:**

-   Yêu cầu dữ liệu từ một hoặc nhiều dịch vụ của BIM 360. Hiện tại bao gồm: Admin (cấp Dự án và Tài khoản), Issues, Locations, Submittals, Cost, và RFIs. Trong tương lai sẽ mở rộng thêm các dịch vụ khác.
    
-   Truy xuất dữ liệu ngay lập tức hoặc thiết lập lịch lặp lại để dữ liệu được trích xuất định kỳ.
    
-   Nhận thông báo khi dữ liệu sẵn sàng qua **callback URL** hoặc **email**, hoặc tự kiểm tra trạng thái trích xuất bất cứ khi nào bạn muốn.
    
-   Thiết lập và quản lý danh sách các yêu cầu dữ liệu, chỉnh sửa chúng tùy ý để thay đổi nội dung trích xuất, thời gian trích xuất và cách thức thông báo.

## BIM 360 DOCUMENT MANAGEMENT

Các nhóm thi công có thể sử dụng **BIM 360 Document Management** để quản lý bản vẽ kỹ thuật, bản vẽ 2D, mô hình BIM 3D và bất kỳ tài liệu dự án nào khác.  
BIM 360 Document Management được thiết kế nhằm **tối ưu hóa quy trình quản lý tài liệu**, hợp nhất tất cả bản vẽ và thiết kế, đồng thời thiết lập các mẫu và quy trình tiêu chuẩn để **tăng hiệu quả làm việc**.

Bạn có thể truy cập BIM 360 Document Management thông qua **Data Management API**, nơi bạn có thể quản lý các **thư mục và tệp tin BIM 360**.

Một số endpoint liên quan đến quản lý tài liệu thuộc **BIM 360 Document Management API riêng biệt**, bao gồm các tính năng sau:

-   Xuất tệp PDF.
    
-   Quản lý quyền truy cập thư mục.
    
-   Truy xuất thông tin thuộc tính tùy chỉnh và quản lý giá trị thuộc tính tùy chỉnh.
    
-   Truy xuất thông tin tiêu chuẩn đặt tên tệp cho dự án.

## BIM 360 ISSUES


**BIM 360 Issues API** cho phép tạo, theo dõi và cập nhật các sự cố (issues).  
Một issue là một mục được tạo trong BIM 360 để theo dõi, quản lý và trao đổi các vấn đề hoặc điểm cần lưu ý cho đến khi được giải quyết.

API này hỗ trợ quản lý **các issue liên quan đến dự án**, cũng như **các issue liên kết với tài liệu cụ thể** (gọi là _pushpin issues_).

----------

### **Các tính năng của Issues API bao gồm:**

-   Tạo, cập nhật và theo dõi các issue liên quan đến dự án trong BIM 360.
    
-   Tạo, cập nhật và theo dõi các issue liên quan đến tài liệu trong BIM 360.
    
-   Truy xuất các **thuộc tính tùy chỉnh** của issue trong một dự án và các **mapping thuộc tính tùy chỉnh**.
    
-   Thêm và cập nhật **bình luận** cho các issue.
    
-   Thêm và xóa **tệp đính kèm** cho các issue.

---

### **Quy trình và Chuyển trạng thái của Issue**

Bạn có thể sử dụng **Issues API** để chuyển trạng thái của một issue qua các giai đoạn khác nhau:

-   `draft` (bản nháp)
    
-   `open` (đang mở)
    
-   `answered` (đã phản hồi)
    
-   `closed` (đã đóng)
    
Ngoài ra, bạn cũng có thể thay đổi các thuộc tính khác của issue, ví dụ như:

-   Người được giao (assignee)
    
-   Ngày đến hạn (due date)

## BIM 360 LOCATION

**BIM 360 Locations API** cho phép bạn quản lý và chia sẻ cấu trúc phân cấp khu vực công trình trong dự án của mình thông qua **Location Breakdown Structure (LBS)**.  
LBS là một **cấu trúc dạng cây**, thể hiện bố cục của một dự án xây dựng.

Hiện tại, API này cho phép bạn **truy xuất các vị trí (nodes)** trong cấu trúc LBS.

## BIM 360 MODEL COORDINATION

**BIM 360 Model Coordination API** có thể được sử dụng để:

-   Tạo và xem **các bộ mô hình (model sets)** và **phiên bản** trong không gian phối hợp mô hình (coordination space).
    
-   Tạo các **chế độ xem mô hình ảo (virtual model set views)** bằng cách kết hợp các chế độ xem do người dùng định nghĩa được trích xuất từ các tệp thiết kế đã tải lên BIM 360 Document Management.
    
-   Thực hiện các bài kiểm tra xung đột (clash tests) tương tự như Navisworks đối với các phiên bản của bộ mô hình.
    
-   **Nhóm các xung đột** và **giao nhiệm vụ xử lý** cho người dùng dự án thông qua dịch vụ BIM 360 Issues.
    
-   **Bỏ qua vĩnh viễn** những xung đột được dự đoán trước hoặc nằm trong thiết kế.
    
-   Thực hiện **truy vấn dạng SQL** trên **chỉ mục thuộc tính BIM hợp nhất** trong không gian phối hợp.

## BIM 360 RELATIONSHIPS

**BIM 360 Relationships API** có thể được sử dụng để:

-   **Tạo, truy xuất và xóa** các mối quan hệ giữa các thực thể (entities) thuộc các module khác nhau trong BIM 360.
    
-   Thực hiện **tìm kiếm nâng cao** để truy xuất các liên kết cụ thể giữa các thực thể khi chỉ biết một phần thông tin về các liên kết đó.
    
-   **Đồng bộ hóa các mối quan hệ** trong một dự án, dựa trên các tiêu chí cụ thể (ví dụ: để sử dụng ngoại tuyến).

## BIM 360 RFI

**BIM 360 RFIs API** cho phép tạo, theo dõi và cập nhật các RFI (Requests for Information – yêu cầu thông tin).  
RFI là một câu hỏi chính thức được một thành viên trong dự án gửi đến một thành viên khác, ví dụ như yêu cầu kiến trúc sư làm rõ ý đồ thiết kế.

API hỗ trợ quản lý các RFI liên quan đến:

-   **Dự án** (project-related RFIs)
    
-   **Tài liệu cụ thể** (document-related RFIs hay _pushpin RFIs_)
    
----------

### **Các tính năng của RFIs API bao gồm:**

-   Tạo, cập nhật và theo dõi các RFI liên quan đến dự án trong BIM 360. Những RFI này thuộc dịch vụ **BIM 360 Project Management**. (Xem thêm tài liệu trợ giúp về RFIs để biết chi tiết.)
    
-   Tạo, cập nhật và theo dõi các RFI liên quan đến tài liệu.
    
-   Thêm bình luận vào một RFI và truy xuất bình luận. _(Lưu ý: Hiện tại không hỗ trợ thêm nhiều bình luận vào một RFI.)_
    
-   Thêm, truy xuất và xóa các tệp đính kèm của RFI. _(Lưu ý: Hiện tại không hỗ trợ thêm nhiều tệp đính kèm cho một RFI.)_
- 
----------

Bảng dưới đây mô tả các tên module trong **Project Admin** và tên tương ứng trong **RFIs API**:

| Tên chức vụ trong Project Admin                      | Tên chức vụ tương ứng trong RFIs API         |
|------------------------------------------------------|-----------------------------------------------|
| Creator                                              | Subcontractor (projectSC)                   |
| Manager                                              | General Contractor (projectGC)              |
| Reviewer 1 (EMEA workflow)                           | Construction Manager (projectCM)            |
| Reviewer (US workflow) / Reviewer 2 (EMEA workflow)  | Architect (projectArch)                     |

---

### **Quy trình làm việc (Workflow) của RFI**

Các endpoint của **RFIs API** chứa thông tin liên quan đến **quy trình làm việc (workflow)** và **quyền truy cập** được thiết lập trong giao diện quản trị dự án (Project Admin UI), chẳng hạn như:

-   Loại quy trình RFI được gán cho dự án
    
-   Vai trò workflow được gán cho các thành viên trong dự án
    

Để kiểm tra **loại workflow** của một RFI → sử dụng endpoint: `GET rfis/:id`  
Để kiểm tra **vai trò workflow** của thành viên dự án → sử dụng: `GET users/me`

> ⚠️ **Lưu ý:** RFIs API hiện **không hỗ trợ thiết lập quy trình làm việc** hay **cấu hình vai trò workflow**.  
> Để biết thêm chi tiết, vui lòng tham khảo **tài liệu trợ giúp RFIs**.

----------

### **Chuyển trạng thái của RFI (RFI Transitions)**

Bạn có thể sử dụng RFIs API để chuyển trạng thái của một RFI qua các bước sau:

-   `draft` – bản nháp
    
-   `submit` – gửi
    
-   `open` – đang mở
    
-   `answered` – đã được trả lời
    
-   `closed` – đã đóng
    
-   `void` – hủy bỏ
    
Ngoài ra, bạn cũng có thể thay đổi các thuộc tính khác của RFI, ví dụ như:

-   Người được giao nhiệm vụ
    
-   Ngày đến hạn (due date)
    
-   Các chi tiết khác liên quan
    
Để xem hướng dẫn chuyển trạng thái RFI qua một quy trình thông thường, hãy tham khảo tài liệu: **RFI Transitions Tutorial**.

> ⚠️ **Lưu ý:** Hiện tại, RFIs API **chưa hỗ trợ tải tệp cục bộ (local files) lên RFI** hoặc **liên kết RFI với PCO (Potential Change Orders)**.

## CÁC THUẬT NGỮ SỬ DỤNG TRONG TÀI LIỆU

| Thuật ngữ              | Mô tả |
|------------------------|------|
| **Account** | Tổ chức chủ quản sở hữu các dự án BIM 360. |
| **Attachment** | Tài liệu hoặc hình ảnh được đính kèm vào một issue để tham khảo. |
| **Business Unit** | Dùng để tổ chức các dự án theo từng đơn vị kinh doanh trong một tổ chức. Ví dụ: một công ty xây dựng có thể có các bộ phận khác nhau cho các loại dự án như nhà ở, nội thất, cơ sở hạ tầng. Thông tin này có thể được sử dụng cho mục đích báo cáo và phân tích. |
| **Checklist** | Danh sách các điểm hoặc câu hỏi cần được xác minh để đánh giá mức độ an toàn hoặc chất lượng của công việc tại một vị trí cụ thể hoặc để kiểm tra việc lắp đặt thiết bị có đúng hay không. |
| **Checklist template** | Phác thảo cấu trúc và nội dung của một danh sách kiểm tra. |
| **Company** | Một tổ chức tham gia vào dự án. Mỗi thành viên dự án đều liên kết với một công ty. |
| **Container** | Mỗi dự án được gán một tập hợp vùng lưu trữ chứa tất cả các issue và checklist của dự án đó. Điều này liên quan đến Issues API và Checklist API. ID của container được sử dụng để gọi các endpoint tương ứng. Bạn cần sử dụng Data Management API (`GET hubs/:hub_id/projects`) để lấy Container ID. |
| **Issue** | Một mục được tạo trong BIM 360 để theo dõi, quản lý và trao đổi về các vấn đề cho đến khi được giải quyết. |
| **Project** | Cấu trúc tổ chức chính trong đó người dùng làm việc và nội dung được quản lý trong BIM 360. |
| **Pushpin** | Dấu hiệu trực quan hiển thị vị trí của một issue hoặc RFI trong tài liệu. |
| **RFI** | Một câu hỏi chính thức được một thành viên trong dự án gửi cho thành viên khác, ví dụ như yêu cầu kiến trúc sư làm rõ ý đồ thiết kế. |
| **User** | Các thành viên tham gia vào tài khoản BIM 360 của bạn. |
