
## Cost Management API

Phần này mô tả **các thuật ngữ chính** và **mối quan hệ giữa các đối tượng dữ liệu** được sử dụng trong **BIM 360 Cost Management API**, kèm theo phần **các giới hạn đã biết** trong phiên bản phát hành công khai đầu tiên.

----------

### Thuật ngữ

Dưới đây là danh sách các thuật ngữ quan trọng giúp bạn hiểu rõ cách sử dụng **Cost Management API**:

| Thuật ngữ               | Định nghĩa |
|--------------------------|-----------|
| **Container**            | Một phạm vi dùng để phân tách dữ liệu trong Cost Management, hiện tại được ánh xạ với một dự án BIM 360. |
| **Budget Code Template** | Mẫu dùng để định nghĩa cấu trúc mã ngân sách trong Cost Management. |
| **Segment**              | Một phần trong mẫu mã ngân sách, được xác định bởi kiểu, thứ tự, độ dài và ký tự phân cách. |
| **Segment Value**        | Các mã có thể sử dụng trong một segment của mẫu mã ngân sách. |
| **Budget**               | Bản phân bổ chi phí dự kiến cho dự án. |
| **Contract**             | Gói thông tin bao gồm mô tả phạm vi công việc, tài liệu kỹ thuật, bản vẽ, và lịch trình công việc. Một nhà thầu chính gửi hợp đồng cho các nhà thầu phụ để nhận báo giá, sau đó đánh giá và thương lượng với nhà thầu được chọn. Một hợp đồng có thể bao gồm nhiều hạng mục ngân sách. |
| **Main Contract**        | Hợp đồng chính giữa chủ đầu tư và nhà thầu chính. |
| **SOV (Schedule of Values)** | Danh sách tất cả các hạng mục (chi phí hoặc thay đổi) trong hợp đồng chính, cùng với giá trị của từng hạng mục. |
| **PCO (Potential Change Order)** | Sự kiện có thể làm thay đổi chi phí dự án. Có thể là thay đổi nội bộ hoặc từ phía khách hàng. Mỗi PCO thường tóm tắt các hạng mục chi phí chi tiết và markup. |
| **RFQ (Request For Quote)** | Nhà thầu chính gửi chi tiết của một PCO dưới dạng yêu cầu báo giá đến nhà cung cấp. Bao gồm phạm vi công việc, hạn nộp, tài liệu liên quan và phân tách chi phí nếu có. |
| **SCO (Supplier Change Order)** | Lệnh thay đổi giữa nhà thầu chính và nhà thầu phụ/nhà cung cấp/tư vấn, gồm nhiều hạng mục chi phí liên quan. |
| **RCO (Request Change Order)** | Yêu cầu thay đổi hợp đồng giữa nhà thầu chính và chủ đầu tư. Thường được tạo từ một hoặc nhiều PCO. |
| **OCO (Owner Change Order)** | Lệnh thay đổi chính thức từ chủ đầu tư đến nhà thầu chính. Có thể được tạo từ nhiều RCO hoặc trực tiếp từ PCO. |
| **FormDefinition**       | Định nghĩa tổng quát cho PCO/RFQ/RCO/OCO/SCO bao gồm loại và tên. Dùng để liên kết với tài liệu, file đính kèm, thuộc tính,... |
| **FormInstance**         | Một bản thể cụ thể của `FormDefinition`, ví dụ một PCO/RFQ cụ thể. |
| **Cost item**            | Hạng mục chi phí chi tiết liên kết với mã ngân sách, công ty, đơn vị hoặc số tiền. Có thể được chia nhỏ thành sub-item và xuất hiện trong nhiều change order ở các trạng thái khác nhau. |
| **Document**             | Tài liệu được tạo từ mẫu (định dạng `.docx`) bằng cách trộn dữ liệu PCO/RFQ/RCO/OCO/SCO liên quan. |
| **File package**         | Gói tài liệu được tạo từ nhiều mẫu và phụ lục, đóng gói lại thành file zip sau khi trộn dữ liệu hợp đồng. |
| **Attachment**           | Tệp tin được tải lên từ Cost Management vào thư mục ẩn của BIM 360 DOCS. |
| **Attachment folder**    | Thư mục đặc biệt trong BIM 360 DOCS dùng để chứa các attachment từ Cost Management. |
| **Attributes**           | Các thuộc tính tùy chỉnh để mở rộng ngân sách, hợp đồng, v.v... khi cần nhiều hơn thuộc tính mặc định. |
| **Status**               | Mỗi cost item hoặc change order có trạng thái như: draft, open, submitted, approved, rejected, etc. |
| **Association**          | Dùng để xác lập mối quan hệ giữa các dữ liệu dùng chung (attributes, attachments, statuses) với các module như Budget, Contract, Change Orders. |
| **Action**               | Hành động của người dùng để thay đổi trạng thái một mục. Ví dụ: chuyển từ Draft sang Open, khóa hợp đồng,... |
| **User**                 | Thành viên tham gia vào dự án. Thông tin người dùng được quản lý qua BIM 360 Admin và liên kết bằng Autodesk ID. |
| **Company**              | Tổ chức tham gia vào dự án (chủ đầu tư, nhà thầu chính, nhà thầu phụ...). Mỗi thành viên gắn với một công ty. |
| **Tax**                  | Khoản thu tài chính do chính phủ áp dụng, có thể áp dụng cho hợp đồng, change order, thanh toán... |
| **Sub Cost Item**        | Phân tách chi tiết của cost item, tổ chức theo cấu trúc cây phân cấp. Mỗi sub item có thể kế thừa từ parent và có thuộc tính như loại, số lượng, đơn giá, giá trị,... hỗ trợ theo dõi và quy trình phê duyệt chi tiết. |

---

### Data Object Relationships)

**ACC Cost API** là một phần của tập hợp API lớn hơn gọi là **APS APIs**.  
Để truy cập dữ liệu chi phí thông qua API, bạn cần sử dụng các API APS khác như:

-   **Authentication API** (API xác thực)
    
-   **Data Management API** (API quản lý dữ liệu)
    
-   **ACC Admin API** (API quản lý tài khoản ACC)
    

Hình minh họa bên dưới thể hiện mối quan hệ giữa các đối tượng dữ liệu khác nhau trong các nhóm thành phần API khác nhau.

----------

-   Mỗi dự án được gán một **container**, dùng để lưu trữ toàn bộ dữ liệu chi phí cho dự án đó.  
    Bạn sử dụng **container ID** để truy cập dữ liệu chi phí.  
    Bạn có thể lấy container ID bằng cách sử dụng **Data Management API**.
    
-   **Các tệp đính kèm chi phí (cost attachments)** được lưu trữ thông qua **Data Management API**, API này được dùng để truy cập **ACC Docs**.  
    **Module Cost** lưu giữ một **con trỏ tham chiếu (URN)** tới dữ liệu đã lưu trữ.
    
-   **Thông tin người dùng (user)** và **thông tin công ty (company)** được tham chiếu trong module Cost (ví dụ: trong hợp đồng)  
    được lưu trữ trong **ACC Admin API**.

---

### Performance Tracking

Với tính năng theo dõi hiệu suất, bạn có thể thấy được hiệu suất đã lập kế hoạch và hiệu suất thực tế của công việc theo ngân sách cụ thể ảnh hưởng lẫn nhau như thế nào, thông qua việc phân tích dữ liệu đầu vào được theo dõi (số đơn vị thời gian đã sử dụng) và đầu ra (số đơn vị công việc đã hoàn thành). Với thông tin này, bạn có thể xử lý các vấn đề lao động tại công trường và dự báo chính xác tác động chi phí càng sớm càng tốt.

Sử dụng Cost Management API, bạn tạo một mục theo dõi hiệu suất (performance tracking item) để đại diện cho một khoản ngân sách, sau đó chia nhỏ mục theo dõi thành các bản thể riêng biệt (tracking item instances) mà bạn cập nhật để phản ánh công việc đã thực hiện. Các instance này có thể được chia nhỏ dựa trên các giá trị khác nhau của bất kỳ thuộc tính nào, bao gồm cả vị trí thi công nơi công việc được thực hiện. Để biết thêm thông tin chi tiết về tính năng này, bạn có thể xem trang tài liệu trợ giúp Performance Tracking.

Lưu ý rằng nếu bạn đã tích hợp một ứng dụng theo dõi lao động của bên thứ ba như Riskcast, Rhumbix, QuickBooks Time hoặc ClickUp, bạn có thể sử dụng các endpoint liên quan đến timesheet trong API để thu thập dữ liệu hiệu suất định kỳ từ các ứng dụng đó và tự động tích hợp vào từng instance của mục theo dõi hiệu suất.

---
### Ví dụ cơ bản

Việc theo dõi hiệu suất bắt đầu từ ngân sách dành cho một công việc cụ thể, ví dụ như đổ bê tông cho móng dầm. Bạn sẽ tạo một performance tracking item cho công việc này.

Chi phí của công việc sẽ được chia nhỏ thành nhiều instance của mục theo dõi, mỗi instance đại diện cho một vị trí thi công khác nhau. Mỗi instance bắt đầu với thông tin về số lượng vật liệu cần thiết, ví dụ như số yard khối (cubic yards - cy) bê tông cần dùng để hoàn thành công việc. Tiếp theo, bạn cần số giờ lao động dự kiến (hr) để thực hiện công việc đổ bê tông. Các con số này cần được nhân với chi phí trên mỗi đơn vị tương ứng (cost per cy và cost per hr) để cho ra tổng chi phí đã lập kế hoạch giống nhau, theo công thức sau:

(tổng số giờ * đơn giá theo giờ) = (tổng số yard * đơn giá theo yard) = tổng chi phí đã lập kế hoạch

Trong API Cost Management, các thành phần này được biểu diễn bằng các trường như sau:

(inputQuantity * inputUnitPrice) = (outputQuantity * outputUnitPrice) = plannedTotal

Lưu ý rằng trường plannedTotal không được công khai trong API vì nó có thể được tính từ các giá trị khác. Tuy nhiên, khi bạn cập nhật bất kỳ giá trị nào trong số này, bạn có thể khóa giá trị plannedTotal để nó không bị thay đổi bởi các cập nhật khác.

Giá trị plannedTotal cần được giữ nguyên ở cả phía đầu vào và đầu ra. Điều này có nghĩa là cả chi phí lao động và vật liệu đều nằm trong đơn giá đầu vào (inputUnitPrice - cost/hr), và cũng được phản ánh trong đơn giá đầu ra (outputUnitPrice - cost/cy). Ví dụ: nếu mất 1.000 giờ để đổ 2.000 yard bê tông, thì đơn giá đầu vào sẽ gấp đôi đơn giá đầu ra để giữ nguyên tổng chi phí kế hoạch. Giả sử bạn đã xác định inputUnitPrice là 50 đô la, thì outputUnitPrice cần là 25 đô la:

1.000 giờ * 50 đô la/giờ = 2.000 yard * 25 đô la/yard = 50.000 đô la

---

### Giá trị được theo dõi

Với mỗi instance của mục theo dõi hiệu suất, bạn sẽ theo dõi số giờ đã làm và số yard bê tông đã được đổ khi công việc diễn ra. Các giá trị này được báo cáo định kỳ (thường là hàng ngày hoặc hàng tuần). Trong API, chúng được thể hiện bằng các trường trackedInputQuantity và trackedOutputQuantity.

Một số giờ làm việc được báo cáo (trackedInputQuantity) sẽ cho biết tỷ lệ phần trăm giờ làm theo kế hoạch đã được sử dụng. Ví dụ:

800 giờ làm việc / 1.000 giờ kế hoạch = 80% số giờ đã sử dụng

Để công việc đúng tiến độ, số lượng bê tông được đổ (trackedOutputQuantity) cũng nên đạt tỷ lệ tương đương. Trong ví dụ này:

1.600 yard đã đổ / 2.000 yard kế hoạch = 80%

Nếu hai tỷ lệ phần trăm không khớp nhau, điều đó cho thấy công việc đang bị chậm hoặc vượt tiến độ. Ví dụ, nếu chỉ đổ được 1.400 yard:

1.400 / 2.000 = 70% → thấp hơn 80% giờ đã sử dụng → công việc đang chậm

---

### Điều chỉnh

Tại bất kỳ thời điểm nào trong vòng đời của một instance, nếu bạn muốn điều chỉnh dự báo dựa trên lượng đầu ra cuối cùng khác với lượng ban đầu, bạn có thể ghi đè giá trị đầu ra ban đầu bằng một giá trị điều chỉnh. Để làm điều đó, hãy gọi endpoint:

PATCH performance-tracking-item-instances/:id

và cập nhật trường adjustedOutputQuantity.