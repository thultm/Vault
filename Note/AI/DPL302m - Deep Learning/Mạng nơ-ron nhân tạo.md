---
tags:
---

# Tổng quan về ANN
## Lịch sử phát triển
## Khả năng ứng dụng của ANNs
- Là 1 trong những phương pháp ra đời sớm nhất
- Ứng dụng vô cùng rộng rãi trong hầu hết các lĩnh vực
## Minh họa ứng dụng của ANN
- Nhận dạng tiếng Việt
## ANN là gì?
### Nơ-ron sinh học
- Bộ não con người chứa khoảng $10^{11}$ nơ-ron, với hơn $10^{14}$ liên kết
- Khi tiếp nhận thông tin ở 1 dây thần kinh nào đó **vượt ngưỡng** cho phép thì truyền xung điện gửi tín hiệu đến các dây thần kinh khác
$\rightarrow$ ***Có thể mô hình hóa nơ-ron sinh học***
### Định nghĩa
- ANN là 1 mô hình mạng chứa nhiều đơn vị xử lý, giả lập quả trình học tập và tính toán của bộ não con người
- Mỗi đơn vị xử lý gọi là 1 nơ-ron nhân tạo
- Mỗi nơ-ron nhân tạo giả lập 1 [[#Nơ-ron sinh học]], gồm 1 ngưỡng kích hoạt (bias) và 1 hàm kích hoạt, đặc trưng cho tính chất của nơ-ron
- Các nơ-ron nhân tạo được liên kết với nhau bằng các kết nối. Mỗi kết nối có 1 độ lợi, gọi là weight, đặc trưng nhớ của ANN
### Quá trình huấn luyện ANN
![[Drawing 2023-09-07 12.50.47.excalidraw]]
- Dựa trên sự sai biệt {Error} và Target
## Mô hình nơ-ron 1 ngõ vào
- Cấu tạo nơ-ron gồm:
	- Ngõ vào $p$
	- Ngưỡng kích hoạt $b$
	- Trọng số kết nối $w$
	- [[Activation function|Hàm kích hoạt]] $f$
- Hàm kích hoạt
	- Có nhiều hàm truyền
	- Có 3 hàm thông dụng: Logsig, Tansig, Purelin
## Mô hình nơ-ron nhiều ngõ vào
- Khi ngõ vào của nơ-ron là 1 vector có $R$ phần tử
- Cấu trúc:
	- $R$ ngõ vào
	- $R$ trọng số kết nối $W$
# Cấu trúc của ANN
## Khái niệm về cấu trúc ANN
- Là 1 hệ thống gồm nhiều neuron đơn lẻ kết nối với nhau, để thực hiện 1 chức năng tính toán nào đó
- Tính năng của mạng phụ thuộc vào: Cấu trúc, các trọng số kết nối và quá trình tính toán tại các neuron đơn lẻ (hàm truyền)
- Mạng neuron có thể học từ dữ liệu mẫu và tổng quát hóa dựa trên các mẫu đã học (mạng có khả năng nhớ)
- Ví dụ về cấu trúc mạng:
	- Mạng truyền thẳng (FFNN)
	- Mạng hồi quy (RNN)
## Phân loại ANN
- Dựa theo kiểu kết nối các neuron:
	- FFNN
	- RNN
- Dựa vào số lớp:
	- Mạng 1 lớp ![[Drawing 2023-09-07 13.46.39.excalidraw]]
	- Mạng nhiều lớp
		- Có thể được tổ chức thành nhiều lớp, với ngõ ra của lớp trước là ngõ vào của lớp sau 
		- Quá trình tính toán trên mạng được thực hiện trên từng lớp
		- Tính toán trên mỗi lớp hoàn toàn giống như tính toán trên mạng 1 
# Các giải thuật huấn luyện ANN
- Các tham số của mạng $\theta$ bao gồm các **weight matrices** và các **bias vectors** từ tất cả layers.
- Trong ANN, việc chuẩn hóa dữ liệu cực kì quan trọng vì ANN cực kì nhạy cảm với nhiễu
# Giải thuật huấn luyện ANN
## Giải thuật truyền ngược
- Tiếng anh là backpropagation
- Cập nhật các trọng số dựa theo nguyên tắc: $$w_{ij}(k+1)=w_{ij}(k)+\eta g(k)$$
$w_{ij}(k)$ là trọng số của kết nối từ nơ-ron $j$ đến nơ-ron $i$, ở thời điểm hiện tại $\eta$ là tốc độ học (learning rate, 0< $\eta$ ≤1) $g(k)$ là gradient hiện tại