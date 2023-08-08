# Cheat sheet of Git basic commands
## `git init` - khởi tạo
- `git init` Khởi tạo một Repository mới (Git Repo) ở local
- `git init --bare` Khởi tạo một Repository chỉ có chức năng lưu trữ, không có thư mục làm việc, không soạn thảo, sửa file, thực hiện commit trực tiếp tại dự án
## `git clone [path]` - sao chép một Repository có địa chỉ là **path**
## `git config` - làm việc cấu hình Git
- `git config --list` xem thông tin cấu hình Git
- `git config --global user.name [user_name]` cấu hình tên người dùng Git
- `git config --global user.email [user_emal]` cấu hình email của người dùng Git
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
- `git reset -- [filename]` hủy bỏ thông tin cập nhật của một file bất kì tại vùng **staged**
## `git log` - xem lại thông tin lịch sử commit (mã HASH, Author, Date, Message)
- `git log -2` hiển thị thông tin lịch sử 2 commit cuối
- `git log -p` hiển thị chi tiết các thay đổi của từng commit
- `git log --stat` hiển thị thống kê ngắn gọn hơn về sự thay đổi
- `git log --pretty=oneline` hoặc `git log --oneline` hiển thị thông tin trên một dòng
- `git log --after="year-month-day" --before="year-month-day"` hiển thị thông tin commit lọc theo thời gian
- `git log --author="tác giả"` hiển thị thông tin commit lọc theo tác giả, có thể kết hợp nhiều người bằng ký hiệu `\|`
- `git log --grep="Ghi chú về commit"` hiển thị thông tin commit lọc theo thông tin ghi chú
- `git log [remote_name]/[branch]` hiển thị thông tin các commit 
## `git diff` - kiểm tra sự thay đổi trên Git
- `git diff` kiểm tra sự thay đổi các file giữa thư mục làm việc và các file trong **staged** (nếu không có thì so sánh với các file ở **commit cuối**)
- `git diff --staged` kiểm tra sự thay đổi các file giữa vùng **staged** và vùng **commit cuối**
- `git diff hash-commit1 hash-commit2` kiểm tra sự thay đổi các file giữa hai commit
- `git diff branch1 branch2` kiểm tra sự thay đổi các file giữa 2 nhánh
## `git checkout` - dùng để chuyển nhánh hoặc để phục hồi file trong thư mục làm việc từ một trước đây
- `git checkout [branch]` chuyển làm việc sang nhánh khác
- `git checkout [HASH]` chuyển về một commit có mã HASH, và Git ở chế độ head detached, ta làm việc trên một nhánh tạm thời
- `git checkout [HASH] [filename]` phục hồi file từ phiên bản commit có mã HASH xác định
- `git checkout -- *.html` phục hồi các file đuôi .html từ vùng **staged** (nếu không thì từ vùng **commit cuối**)
- `git checkout -- .` phục hồi tất cả các file từ vùng **staged** (nếu không thì từ vùng **commit cuối**)
## `git switch` - dùng để chuyển nhánh và có thể tạo nhánh mới
- `git switch [branch]` chuyển làm việc sang nhánh khác
- `git switch -c [branch] [HASH]` tạo nhánh mới, kích hoạt nhánh bắt đầu từ một commit có mã HASH
- `git switch -c [branch]` tạo nhánh mới, từ commit cuối
- `git switch --detach [HASH]` chuyển về làm việc tại nhánh tạm thời bắt đầu từ một commit có mã HASH
## `git restore` - dùng để phục hồi các file trong thư mục làm việc
- `git restore .` phục hồi các file từ vùng **staged** (nếu không thì từ vùng **commit cuối**)
## `git branch` - dùng để quản lý nhánh
- `git branch` liệt kê các nhánh **Local Repository**
- `git branch -v` liệt kê các nhánh và commit cuối
- `git branch --merged` liệt kê các nhánh merge với nhánh hiện tại
- `git branch --no-merged` liệt kế các nhánh không merge với nhánh hiện tại
- `git branch -d [branch]` xóa nhánh
- `git branch -a` liệt kê các nhánh **Local Repository** và **Remote Repository**
## `git merge` - dùng để gộp nhánh này vào nhánh khác
- `git merge [branch]` dùng để gộp các nhánh này vào nhánh kia
- `git merge [remote_name]/[branch]` dùng để gộp nhánh tại **Remote Repository**
- Nếu 2 nhánh nằm cùng một phía, thì việc gộp không tạo ra commit mới
- Nếu 2 nhánh không nằm cùng một phía, thì ta cần xử lý xung đột (nếu có), sử dụng `git add` để đánh chỉ mục vào vùng `staged`, và `git commit` tạo commit mới nối giữa 2 nhánh
![merge branch](/assets/merge.png)
## `git rebase` - dùng để gộp các commit từ nhánh này vào nhánh khác
- `git rebase [branch]` dùng để gộp các commit từ nhánh này vào nhánh khác, bằng cách xây dựng lại các commit base kế thừa từ nhánh khác và viết lại lịch sử commit sau các commit cơ sở mới
![rebase branch](/assets/rebase.png)
## `git remote` - làm việc với remote repository
- `git remote` liệt kê tên các remote
- `git remote -v` liệt kê các **Remote Repository** và các **địa chỉ Remote**
- `git remote add [name_remote] [addr_remote]` thiết lập Remote Repository
1. **name_remote** là tên remote, ví dụ là origin, abx, xyz...
2. **addr_remote** là địa chỉ Remote Repository, ví dụ là gitusername@domain.com:myproject.git
- `git remote rm [name_remote]` xóa **Remote Repository**
## `git push` - upload dữ liệu lên remote repository/delete nhánh trên remote
- `git push [name_remote] [branch]` upload dữ liệu (các commit) của nhánh lên **Remote Repository**
- `git push [name_remote] --all` upload dữ liệu (các commit) tất cả các nhánh lên **Remote Repository**
- `git push --delete [name_remote] [branch]` xóa nhánh của **Remote Repository**
## `git fetch` - lấy dữ liệu mới từ **Remote Repository**, những loại dữ liệu này trên **Local Repository** chưa có
- `git fetch [name_remote]` Lấy dữ liệu mới từ Remote Repository, những loại dữ liệu này trên Local Repository là chưa có (ví dụ dữ liệu do người khác mới đưa lên, tên các commit, các branch)
- Lệnh này không làm ảnh hưởng đến các code đang có của dự án trên Local, nó chỉ lấy về nhưng thông tin file chưa có
- Lệnh này nên thực hiện khi mới `git clone` dự án về **Local Repository**
## `git pull` - cập nhật các commit mới từ remote về local
- `git pull [name_remote] [branch]` lấy dữ liệu từ nhánh bất kì từ **Remote Repository**
- `git pull [name_remote] --all` lấy dữ liệu từ tất cả nhánh từ **Remote Repository**
## `git tag` - làm việc với Tag trong Git
- `git tag` liệt kê các Tag
- `git tag -a [Tag_name] -m [Ghi chú về Tag] [HASH]` tạo ra 1 Tag có tên, và dòng chú thích tại commit có mã HASH bất kì
- `git tag -a [Tag_name] -m [Ghi chú về Tag]` tạo ra 1 Tag có tên, và dòng chú thích tại commit cuối
- `git show [Tag_name]` xem thông tin về commit được gắn Tag
- `git tag -d [Tag_name]` xóa 1 Tag
- `git checkout [Tag_name]` quay về một commit bằng Tag, tạo ra một nhánh tạm
- `git checkout -b [branch] [Tag_name]` tạo ra một nhánh xuất phát từ commit có gắn Tag
- `git push [name_remote] [Tag_name]` cập nhật Tag lên trên **Remote Repository**
- `git push [name_remote] --tags` cập nhật các Tag lên trên **Remote Repository**
- `git push --delte [name_remote] [Tag_name]` xóa tag tại **Remote Repository**
