# practice-git

## I. Giới thiệu về git
### Git là gì ?
- Version control system: quản lí phiên bản. 
- Quản lí phiên bản là gì ? quản lý lịch sử: cái gì đã thực hiện, ai đã làm, làm khi nào? tại sao?
### Git có thể làm được gì ?
- Các nhóm có thể cộng tác trong một dự án. 
- Khôi phục lại phiên bản trước đó. 
### Nguyên tắc hoạt động của Git
- Có một kho lưu trữ trung tâm (repository)
- Lấy dữ liệu về, thực hiện các công việc cập nhật dữ liệu lên kho trung tâm. 
- Cung cấp công cụ giải quyết xung đột. 
![[Pasted image 20250914202757.png]]

### Lợi ích
- Đảm bảo không làm hỏng bất cứ thứ gì vĩnh viễn. (vì cho phép quay lại version trước)
- Cộng tác
- Kiểm tra phát triển phiên bản mới không ảnh hưởng phiên bản cũ đang có. 
- Show sản phẩm để chứng minh năng lực. 

## II. Cài đặt Git
1. Truy cập https://git-scm.com
2. Dowload for Window.
	Git: công nghệ lõi, Github, gitlab là các nền tảng, công cụ.
3. Next -> Next
4. Mở git bash để gõ lệnh thao tác.
## III. Các câu lệnh cơ bản để quản lí file và thư mục
- cd: change directory _ thay đổi thư mục
	- cd ..: chuyển trở lại thư mục cha của thư mục hiện tại. 
	- cd [Folder Name]
		- Tên thư mục có thể / giống như đường đẫn tới thư mục đó. 
- dir (Win), ls (linux, macOS): hiển thị danh sách tập tin / thư mục bên trong thư mục hiện hành. 
- mkdir "[Folder Name]": tạo ra thư mục mới.
- touch "<[File Name]": tạo 1 tập tin mới nếu file chưa tồn tại. 
- echo: in/xuất một nội dung. 
	- >: chỉ định hướng để xuất dữ liệu. 
	- echo "<'text'>" > "<[File Name]" (overwrite)
	- echo "<'text'>" >> "[File Name]" (ghi thêm dòng mới)
- cat: hiển thị nội dung 
- diff file1 file2: so sánh khác biệt giữa 2 file. 
- rm (remove) 
	- rm "[file name]"
	- rm -d "[folder name]" (thư mục phải rỗng mới xóa được)
	- rm - r "[folder name]" (thư mục có dữ liệu)
## IV. Tạo Repository mới trong Git
- repository (repo): kho lưu trữ.
- commit: một đơn vị làm việc.
- branch: nhánh 
- main/master: tên của repo chính. (main repo)
- merge/rebase: kết hợp 2 nhánh lại với nhau.
- develop: tên của nhánh, lập trình viên. 
Câu lệnh:
```
git --help: trợ giúp
git status: hiển thị trạng thái kho lưu trữ
git log: hiển thị lịch sử các commit 
git init [repo name]: tạo ra một kho lưu trữ. 
git clone [repo name] [clone name]: để tạo một bản sau được liên kết tới repo
git config -l: xem cấu hình hiện tại. 
git config -l [--scope] [option_name] [value]: 
- scope: --system -> tất cả người dùng
	     --global -> liên quan repo(s)
	     --local  -> liên quan tới 1 repo. 
```
## V. Cấu hình thông tin cho repo
Giúp xác định ai là người thực hiện thao tác trên repo
1. Tạo repo mới: git init EX2 -> cd EX2
2. Xem cấu hình: git config -l
3. Xem cấu hình global: git config  -l --global
4. Xem cấu hình local: git config  -l --local
5. Cấu hình (global) 'user.name'
		git config --global user.name "Cao Gia Thinh"
6. Cấu hình (global)
		git config --global user.email "caogiathinh.contact@gmail.com"

## VI. Trạng thái của repo 
![[Pasted image 20250919144410.png]]
```
git add [file name(s)]  : thêm tệp vào Index
git add .               : thêm tệp (tất cả)
git commit -m "Nội dung": tạo commit -> repo
git status              : sự khác biệt giữa 3 cây (working directory, index, head)
git diff                : so sánh với commit cuối cùng. 
git log                 : lịch sử
```
## VII. Cấu hình GITIGNORE để bỏ qua các file không cần giám sát
- Bỏ đi những file không muốn upload, những file không cần thiết, những thư mục không cần thiết. 
- Tên file .gitignore và có thể chỉnh sửa file này thông qua NotePad.
- gitignore.io: để lấy thông tin file gitignore cho từng IDE.
## VIII. Làm việc với kho lưu trữ trung tâm (central repository - remote repository) 
```
git init --bare                   : tạo một central repo
git clone [repo-name] [clone-name]: sao chép và liên kết repo-name. 
git fetch                         : lấy các thông tin về commit mới từ central . 
git pull                          : lấy dữ liệu từ central về local repo
git push                          : đẩy các commit từ local lên central. 
```
## VIII. Xử lý xung đột 
- Xảy ra khi nào ? khi hai lập trình viên cùng chỉnh sửa một file. Cả hai đều pull cùng 1 file về. Dev1 chỉnh sửa xong push lên centralRepo sau đó Dev2 chỉnh sửa push code lên sẽ bị conflict.
- Khi xảy ra conflict cần thống nhất giữa cái hay chỉnh sửa theo cái mới -> sau đó chỉnh lại bằng VIM/Notepad -> add, commit, push lại. 
- Trước khi chỉnh sửa:
	![[Pasted image 20250920221046.png]]
- Sau khi chỉnh sửa: (thống nhất lại nội dung file)
	![[Pasted image 20250920221202.png]]
**Xử Lý:** 
1. **Trao Đổi:**
    - Xem ai là người sửa code (`git blame <tên file>`).
    - **Nói chuyện với họ** để thống nhất logic nghiệp vụ cần giữ lại. Đây là bước quan trọng nhất.
2. **Chọn Giải Pháp & Sửa Code:**
    - Cập nhật nhánh của bạn:
        - `git pull origin <nhánh chính>` (ví dụ: `main`). Cách này tạo một "merge commit".
        - `git pull --rebase origin <nhánh chính>`. Cách này viết lại lịch sử cho thẳng hàng. **Chỉ dùng trên nhánh cá nhân.**
    - Mở file bị conflict, **xóa các dấu `<<<<<<<`, `=======`, `>>>>>>>`**, và chỉnh sửa code thành phiên bản đúng cuối cùng.
    - Hoàn tất:
        - Nếu dùng `pull` (merge): `git add .` rồi `git commit`.
        - Nếu dùng `pull --rebase`: `git add .` rồi `git rebase --continue`.
3. **Kiểm Tra Lại:**
    - Sau khi sửa, hãy **chạy test** để đảm bảo ứng dụng không bị lỗi do việc hợp nhất code.
**Tips**
	- **Cập nhật thường xuyên:** `pull` mỗi buổi sáng trước khi bắt đầu code.
	- **Chia nhỏ công việc:** Giữ cho các nhánh (feature branch) tồn tại ngắn ngày. Merge sớm và liên tục.
