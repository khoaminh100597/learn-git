# Cheat sheet of Git basic commands
## `git init` - khởi tạo
- `git init` Khởi tạo một Repository mới (Git Repo) ở local
- `git init --bare` Khởi tạo một Repository chỉ có chức năng lưu trữ, không có thư mục làm việc, không soạn thảo, sửa file, thực hiện commit trực tiếp tại dự án
## `git clone [path]` - sao chép một Repository có địa chỉ là **path**
## `git status` - hiển thị thông tin khác nhau giữa các file trong các trường hợp
1. Khác nhau giữa các file trong vùng **staged** và **commit tại con trỏ** (thường HEAD ở vị trí commit cuối)
2. Khác nhau giữa các file trong **thư mục làm việc** và trong **staged**
3. Khác nhau giữa các file trong **thư mục làm việc** và những file **chưa được giám sát** bởi Git
- `git status -s` hiển thị thông tin ngắn gọn hơn
## `git add` - đưa file mới vào staged để chuẩn bị lần commit tiếp theo
- `git add filename` Thêm file có tên chỉ ra trong tham số
- `git add *.c` Thêm tất cả các file có phần mở rộng .c
- `git add -A` Thêm mọi thứ có sự thay đổi (file mới, xóa file, nội dung thay đổi,...)
- `git add .` Thêm mọi thứ trừ loại xóa file
- `git add -u` Thêm mọi thứ trừ file mới
## `git rm [filename]` - xóa filename khỏi thư mục làm việc
- `git rm [filename]` xóa filename khỏi thư mục làm việc và thông tin xóa đưa luôn vào kế hoạch commit **staged**
- Nếu xóa bằng tay filename, thì thông tin xóa chưa đưa vào **staged**
## `git commit` - lưu dữ liệu vào hệ thống Git
- `git commit -m "Ghi chú về commit"` tạo commit cơ bản với nội dung lấy từ vùng **staged**
- `git commit -a -m "Ghi chú về commit"` tạo commit cơ bản đưa các file đang được giám sát có sự thay đổi vào vùng **staged**
- `git commit --amend -m "Ghi chú về commit"` cập nhật thông tin vào commit cuối, hay ta có thể hiểu tạo commit mới thay thế cho commit cuối cùng
## `git reset` - hủy commit cuối hoặc hủy đưa thay đổi vào vùng staging
- `git reset --soft HEAD~1` hủy commit cuối, con trỏ HEAD sẽ chuyển về commit trước đó, những thay đổi của commit cuối được chuyển vào vùng **staged** nhằm để có cơ hội commit lại hoặc sửa cú pháp
- `git reset --hard HEAD~1` hủy commit cuối, con trỏ HEAD sẽ chuyển về commit trước đó, những thay đổi của commit sẽ bị hủy hoàn toàn
- `git reset` hủy bỏ các thông tin cập nhật tại vùng **staged**
- `git reset -- filename` hủy bỏ thông tin cập nhật của một file bất kì tại vùng **staged**
