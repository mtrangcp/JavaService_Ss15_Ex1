Nguyên nhân khiến tài khoản user vẫn truy cập được /admin/orders là do cấu hình hiện tại chỉ kiểm tra 
"xác thực" chứ chưa kiểm tra "phân quyền".

Cụ thể, trong đoạn mã:

Java
.requestMatchers("/").permitAll()
.anyRequest().authenticated()
Khi tài khoản user truy cập /admin/orders, Spring Security sẽ đối chiếu với quy tắc .anyRequest().authenticated().

Quy tắc này chỉ yêu cầu người dùng đăng nhập thành công là có quyền truy cập. Hệ thống bỏ qua việc kiểm tra 
xem người dùng đó có vai trò ADMIN hay không.


