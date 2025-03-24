## [Yêu cầu việc viết code dự án]

 - Đảm bảo code chạy đúng tính năng
 - Dễ đọc, để bảo trì, dễ thêm tính năng mới (không bị hoặc ít xung đột với tính năng mới)
	=> Nội dung code tuân thủ theo các nguyên tắc chung
- Áp dụng được các kĩ thuật test

## [Naming & coding convention]

**1. Format tên**

*Nguồn tham khảo* 
https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/naming-guidelines

| Format | Mô tả  | Sử dụng  |
|--|--|--|
| `PascalCasing` | Viết hoa chữ cái đầu mỗi từ | ✔️ Dùng cho tất cả public member, static, const, property, type (Class, Struct, Interface, Enum) namespace và method |
| `camelCasing` | Viết hoa chữ cái đầu mỗi từ, trừ từ đầu tiên | ✔️ Dùng cho parameter, variable. Lưu ý với member variable thêm dấu gạch chân (underscore) _ đằng trước tên |
| `under_score` | Chữ cái đầu mỗi từ viết thường, các từ ngăn cách nhau bởi dấu gạch chân | ❌ Hạn chế hoặc không sử dụng loại format này |
	

**2. Sử dụng từ ngữ để đặt tên**

- Sử dụng từ tiếng anh đúng chính tả
- Tên không quá dài, tối đa 4 từ. Nếu tên quá dài cần xem xét các phương án tạo class phụ hoặc viết tắt tên
- Không sử dụng dấu gạch chân trong tên, trừ trường hợp tên member variable như đã đề cập ở trên
- Hạn chế dùng từ viết tắt, trong trường hợp tên quá dài, mà tên đó được sử dụng ở nhiều chỗ trong dự án thì cần quy ước viết tắt trước khi sử dụng trong dự án
			
**3. Assembly**
- Đặt theo format: *[Company].[AddIn].[Component].[SubComponent].dll* , ví dụ
```
    TTDesign.CimBox.App 
    TTDesign.CimBox.Database
```
- Tên solution: *[Company].[AddIn]*
- Tên assembly gắn liền với tên project tương ứng

**4. Namespace** 
- Format: *[Company].[AddIn].[Component].[FunctionGroup].[SubFunctionGroup]*
- Tên namespace tự động tạo theo tổ chức thư mục

**5. Type (Class, Struct, Interface, Enum)**
- Sử dụng PascalCasing

| Type | Từ loại | Ví dụ |
|--|--|--|
| Class, Struct | Sử dụng danh từ hoặc cụm danh từ | `Person` `UnitConverter` `CheckableTreeItem` |
| Interface | Sử dụng danh từ hoặc cụm danh từ, tính từ, thêm tiền tố 'I' | `IEditable` `IEqualitable` `IComponent` |
| Generic Type Parameters | Sử dụng chữ 'T', nếu có từ hai parameter trở lên thì cần thêm từ mô tả cho mỗi parameter và bắt buộc có tiền tố 'T' đằng trước tên | `TResult`, `TTarget`, `TSource` |
| Attribute | Thêm hậu tố 'Attribute' | `ReadOnlyAttribute` |
| Delegate | Dùng ở event thêm hậu tố 'EventHandler, các trường hợp còn lại thêm hậu tố 'Callback' |  |
| Enum | ❌ Không thêm hậu tố hay tiền tố Enum vào tên |  |
| Exception | Thêm hậu tố 'Exception' |  |
| IDictionary | Thêm hậu tố 'Dict' |  |
| IEnumerable, ICollection, IList | Thêm hậu tố 'Collection' hoặc tên là danh từ số nhiều |  |
| Method | Sử dụng động từ hoặc cụm động từ | `Copy()` `TryGetValue()` `CompareTo()` |
		
**6. Property**
- Sử dụng PascalCasing
- Sử dụng danh từ hoặc tính từ
- Với property có kiểu dữ liệu kế thừa từ `IEnumerable`, `ICollection`, `IList` thì dùng danh từ số nhiều để đặt tên
- Với property có kiểu dữ liệu là boolean, tên là cụm từ mang ý nghĩa khẳng định (có tiền tố "Is", "Can", "Has"), ví dụ: `IsChecked`, `CanRun`, `HasValue`, `UseFirstMethod`, `OpenWhenDone`, `AbortOnErrors`
		
**7. Field, Parameter**
- Sử dụng camelCasing
- Cách đặt tên giống như property
- Với private field khai báo ở class, thêm dấu gạch dưới ( _ ) trước tên

## Thiết kế WPF

**1. Control**
- Sử dụng camelCasing
- Thêm tiền tố là kiểu Control phía trước VD: `buttonOk`, `canvasPreview`
- Nếu control được gọi sử dụng ở file code-behide, thì cần đặt tên rõ ràng để dễ đọc code, tránh cách đặt tên chung chung ví dụ như `button1`

**2. Window**
- Sử dụng phương thức `Show()` và có chức năng như màn hình chính, thêm hậu tố `View`
- Sử dụng phương thức `ShowDialog()` và có chức năng hỗ trợ màn hình chính, thêm hậu tố `Dialog`
- Event handler
Format: 	
*[ControlName]_On[EventName]* sử dụng cho một control cụ thể
*[ControlType]_On[EventName]* sử dụng cho nhiều control
		
**3. View Model**
- Chọn một trong hai hậu tố 'ViewModel' hoặc 'Vm' dùng trong phạm vi dự án (Dùng hậu tố 'Vm' nếu cần rút ngắn tên)

**4. Khác**
- Các trường constant: có thể sử dụng format uppercase + underscore, ví dụ: *Constant.MESSAGE_WARNING*
