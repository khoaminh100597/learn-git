# Cheat sheet of Git basic commands
## git init - khởi tạo
- `git init` Khởi tạo một Repository mới (Git Repo) ở local

- `git init --bare` Khởi tạo một Repository chỉ có chức năng lưu trữ, không có thư mục làm việc, không soạn thảo, sửa file, thực hiện commit trực tiếp tại dự án
## git add - đưa file mới vào staged để chuẩn bị lần commit tiếp theo
- `git add filename` Thêm file có tên chỉ ra trong tham số
- `git add *.c` Thêm tất cả các file có phần mở rộng .c
- `git add -A` Thêm mọi thứ có sự thay đổi (file mới, xóa file, nội dung thay đổi,...)
- `git add .` Thêm mọi thứ trừ loại xóa file
- `git add -u` Thêm mọi thứ trừ file mới
