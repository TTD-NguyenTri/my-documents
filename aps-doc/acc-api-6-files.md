## Files API

Hướng dẫn sử dụng này mô tả các thành phần của dịch vụ **Files** trong **Autodesk Construction Cloud (ACC)** và cách chúng phối hợp hoạt động cùng nhau.  
Nó cũng cung cấp các khái niệm then chốt để giúp bạn sử dụng thành công **Files API** nhằm quản lý các tệp tin trong dự án ACC của mình.

**Lưu ý:** Các endpoint của **Files API** không tương thích với các endpoint xuất PDF trong **BIM 360 Docs Management**.

Để biết thêm thông tin về cách làm việc với **Files**, hãy tham khảo tài liệu **Files Help**.

----------

## Xuất (Export)

Hiện tại, **Files API** chỉ hỗ trợ xuất các tệp có định dạng **PDF**, **RVT** và **DWG**.  
Người dùng phải có ít nhất quyền **tải xuống (download)** để thực hiện thao tác xuất.

Bạn có thể xuất các tệp bao gồm cả **markup tiêu chuẩn** và **markup tính năng** (các tính năng hiện được hỗ trợ là **Issues** và **Photos**).  
Để biết thêm chi tiết về **markups**, hãy tham khảo tài liệu **Markups Help**.

Bảng sau đây cho thấy các loại **markups** khác nhau mà bạn có thể bao gồm khi xuất tệp:

| Loại | Mô tả |
| :--- | :--- |
| Markups tiêu chuẩn đã công bố | Các markup hiển thị cho tất cả thành viên dự án. |
| Markups tiêu chuẩn chưa công bố | Các markup chỉ hiển thị với người tạo ra chúng. |
| Liên kết markup được thêm vào | Các liên kết được thêm thủ công vào một markup tiêu chuẩn, bao gồm liên kết tới Sheets, Files, RFIs, Forms, Submittals và Assets. |
| Markups issue đã công bố | Các issue hiển thị với bất kỳ ai có quyền phù hợp trong dự án. |
| Markups issue chưa công bố | Các issue chỉ hiển thị với người tạo markup issue và người được giao việc. |
| Markups ảnh đã công bố | Các ảnh hiển thị với bất kỳ ai trong dự án. Yêu cầu đăng ký Autodesk Build. |
| Markups ảnh chưa công bố | Các ảnh chỉ hiển thị với người tạo markup ảnh. Yêu cầu đăng ký Autodesk Build. |

## Các hạn chế (Limitations)

Phiên bản hiện tại của **ACC Files API** có các hạn chế sau:

-   Chức năng **Export** hiện tại chỉ hỗ trợ các tệp **PDF**, và các **mặt bằng 2D** (2D views) cũng như **bản vẽ sheets** từ các tệp **RVT** và **DWG**.