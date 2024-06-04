# Git merge
## 1. Git merge là gì?
> Git merge là quá trình hợp nhất 2 nhánh thành 1 nhánh

Ví dụ: Repo hiện tại đang có 2 branch master và feature, ta muốn hợp nhất nhánh feature vào master thì ta sẽ checkout sang nhánh master và sử dụng lệnh `git merge feature`.

Quá trình để thực hiện việc merge:
1. chuyển sang target branch (nhánh đích) ở đây là nhánh master.
	```bash
	git checkout master
	```
2. thực hiện quá trình merge với câu lệnh
	```bash
	git merge feature
	```
3. giải quyết xung đột (nếu có)
4. commit để hoàn thành quá trình merge
	```bash
	git commit -m "Merge feature to master"
	```
5. push những thay đổi đó lên remote repo nếu có
	```bash
	git push origin master
	```
## 2. Các dạng merge trong Git
### Fast-forward Merge (Hợp nhất Nhanh)

- **Khái Niệm**: Fast-forward merge xảy ra khi nhánh đích (ví dụ: `master`) không có bất kỳ thay đổi nào từ lúc nhánh nguồn (ví dụ: `feature`) được tạo ra.
- **Cách Thức Hoạt Động**: Trong trường hợp này, Git đơn giản chỉ di chuyển con trỏ HEAD của nhánh đích tới con trỏ HEAD của nhánh nguồn. Nó không tạo ra commit hợp nhất mới.
- **Ưu Điểm**: Quá trình này rất đơn giản và giữ lịch sử commit tuyến tính.
### 3-way Merge (Hợp nhất 3 Chiều)
- **Khái Niệm**: 3-way merge được sử dụng khi cả nhánh nguồn và nhánh đích đều có thay đổi kể từ khi chúng tách ra.
- **Cách Thức Hoạt Động**: Git tạo ra một "merge commit" mới, kết hợp các thay đổi từ cả hai nhánh. Commit này có hai parent commit.
- **Xử Lý Xung Đột**: Nếu có xung đột, Git sẽ yêu cầu người dùng can thiệp để giải quyết trước khi hoàn thành merge.
### Squash on Merge (Nén khi Hợp nhất)
- **Khái Niệm**: Squash on merge kết hợp tất cả các commit từ nhánh nguồn vào một commit duy nhất trước khi hợp nhất với nhánh đích.
- **Cách Thức Hoạt Động**: Thay vì giữ nguyên từng commit riêng lẻ, tất cả thay đổi được nén thành một commit.
- **Lịch Sử Sạch Đẹp**: Phương pháp này tạo ra một lịch sử tuyến tính và sạch sẽ hơn trên nhánh đích.
- **Sử Dụng**: Thích hợp trong các trường hợp muốn giữ lịch sử commit gọn gàng, tránh làm rối lịch sử nhánh chính với nhiều commit nhỏ từ nhánh phát triển.
## 3. Lưu Ý Khi Sử Dụng Merge
- **Giữ Lịch Sử ổn định**: Trong hầu hết các trường hợp, đặc biệt là khi làm việc trong một nhóm, sử dụng `git merge` thường an toàn hơn so với `rebase` vì nó không thay đổi lịch sử commit.
- **Giải Quyết Xung Đột**: Cần chú ý đến việc giải quyết xung đột một cách cẩn thận để đảm bảo tính nhất quán của mã nguồn.
- **Merge Commit**: Có thể sử dụng tùy chọn `--no-ff` để bắt buộc tạo merge commit ngay cả khi có thể thực hiện fast-forward merge.
# 3. Git Rebase

> `Git rebase` là một công cụ quan trọng trong Git, giúp tái cấu trúc lịch sử của các commit. Nó thường được sử dụng để làm cho lịch sử commit trở nên sạch đẹp và tuyến tính hơn. 

`Rebase` thay đổi cơ sở của nhánh hiện tại sang một nhánh khác hoặc một commit cụ thể.
## 1. Quá trình thực hiện Git Rebase
1. **Chuyển Sang Nhánh Nguồn**: Đầu tiên, chuyển sang nhánh mà bạn muốn rebase (ví dụ: nhánh `feature`).
   ```bash
   git checkout feature
   ```
2. **Thực Hiện Rebase**: Tiếp theo, thực hiện rebase nhánh này lên nhánh đích (ví dụ: `master`).
   ```bash
   git rebase master
   ```
3. **Giải Quyết Xung Đột**: Trong quá trình rebase, nếu có xung đột, bạn cần phải giải quyết chúng. Sau đó, tiếp tục rebase bằng cách sử dụng `git rebase --continue`.
4. **Cập Nhật Nhánh Đích**: Nếu nhánh đích (`master`) đã được đẩy lên kho chứa từ xa (remote repository), bạn cần phải sử dụng `git push --force` để cập nhật nhánh đích vì lịch sử commit đã thay đổi.
## 2. Các Điểm Nổi Bật của Git Rebase

- **Tái Cấu Trúc Lịch Sử Commit**: `Rebase` tái cấu trúc lịch sử, làm cho nó trở nên tuyến tính và gọn gàng hơn.
- **Tránh Merge Commits**: Trái ngược với `merge`, `rebase` không tạo ra các commit hợp nhất. Điều này giúp lịch sử commit ít phức tạp hơn.
- **Dễ Dàng Hiểu và Theo Dõi**: Lịch sử commit sau rebase thường dễ hiểu và theo dõi hơn, đặc biệt là trong các dự án lớn.
- **Sử Dụng Cẩn Thận**: Do `rebase` thay đổi lịch sử commit, nên nó nên được sử dụng một cách cẩn thận, đặc biệt là trong các nhánh mà nhiều người đang cùng làm việc.
`Git rebase` có hai hình thức chính: **Standard Rebase** và **Interactive Rebase**. Mỗi hình thức có đặc điểm và ứng dụng riêng.
## 3. Các loại Git rebase
### 1. Git Rebase Standard (Rebase Tiêu Chuẩn)
**Đặc Điểm:**
- **Mục Đích**: Di chuyển nhánh hiện tại để nó bắt đầu từ một điểm khác, thường là đầu của nhánh khác.
- **Cách Sử Dụng**: Đơn giản và trực tiếp. Sử dụng lệnh `git rebase [base-branch]`.
- **Quy Trình**: Nó di chuyển tất cả các commit của nhánh hiện tại (không có trong nhánh cơ sở) lên trên đỉnh của nhánh cơ sở.
- **Giải Quyết Xung Đột**: Nếu có xung đột, bạn cần phải giải quyết và tiếp tục rebase bằng cách sử dụng `git rebase --continue`.
**Ví Dụ:**
```bash
git checkout feature
git rebase master
```
Ở đây, tất cả các commit trong `feature-branch` được di chuyển lên trên cùng của `master`.
### 2. Git Rebase Interactive (Rebase Tương Tác)
**Đặc Điểm:**
- **Mục Đích**: Cho phép sửa đổi một chuỗi của commit theo cách tương tác.
- **Cách Sử Dụng**: Thực hiện qua một giao diện tương tác. Sử dụng lệnh `git rebase -i [commit-hash]` hoặc `git rebase -i HEAD~[number]`.
- **Tính Năng**: Bạn có thể chọn tái cấu trúc, sửa, loại bỏ hoặc kết hợp các commit.
- **Quy Trình**: Một trình biên tập văn bản sẽ mở ra, liệt kê các commit và cho phép bạn chỉ định thao tác cho mỗi commit (ví dụ: reword, squash, drop).
	- `pick`: Giữ commit này trong lịch sử.
	- `reword`: Giữ commit nhưng sửa đổi thông điệp commit.
	- `edit`: Dừng để sửa đổi commit (ví dụ: thay đổi nội dung, chia nhỏ, kết hợp với commit khác).
	- `squash`: Gộp commit này vào commit trước đó và kết hợp thông điệp commit.
	- `fixup`: Tương tự như `squash` nhưng loại bỏ thông điệp commit của commit này.
**Ví Dụ:**
```bash
git checkout feature
git rebase -i HEAD~3
```
Ở đây, bạn có thể sửa đổi ba commit cuối cùng trong `feature-branch`.
### So Sánh và Khi Nào Sử Dụng
- **Khi Sử Dụng Standard Rebase**: Khi bạn muốn di chuyển toàn bộ nhánh lên một cơ sở mới mà không cần thay đổi từng commit. Thích hợp để giữ nhánh cập nhật với nhánh chính hoặc cơ sở.
- **Khi Sử Dụng Interactive Rebase**: Khi bạn muốn tái cấu trúc lịch sử commit một cách chi tiết, như gộp nhiều commit thành một, đổi tên commit, loại bỏ hoặc sửa đổi các commit. Đây là công cụ mạnh mẽ để làm sạch lịch sử commit trước khi chia sẻ công việc với người khác.

Cả hai hình thức của `git rebase` đều đòi hỏi sự hiểu biết về Git và cẩn thận trong việc sử dụng để tránh làm rối lịch sử commit, đặc biệt là khi làm việc trong một nhóm.
## 3. Khi Nào Nên Sử Dụng Rebase
- **Trước Khi Merge vào Nhánh Chính**: Để làm sạch lịch sử commit của một nhánh phát triển trước khi hợp nhất nó vào nhánh chính.
- **Đồng Bộ Hóa với Nhánh Chính**: Để đồng bộ hóa nhánh phát triển của bạn với những thay đổi mới nhất từ nhánh chính.
