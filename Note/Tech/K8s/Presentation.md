# Deployment Strategies
> **Deployment** cho phép ta khai báo các cập nhật cho _Pod_ và _ReplicaSet_. Xác định cách tạo, nâng hoặc hạ cấp các phiên bản của ứng dụng.
## Rolling deployment 
- Là chiến lược triển khai mặc định của K8S.
- Lần lượt thay thế các phiên bản hiện tại trên các pods bằng 1 phiên bản mới, cập nhật 1 cách chậm rãi từng pod và không có cluster downtime.
- Các bước thực hiện:
	- B1: Thêm liveness và readiness probes vào quá trình deployment
		- Liveness probe được sử dụng để kiểm tra xem khi nào thì nên khởi động lại một pods.
			- Kiểm tra app $\overset{\text{Chết hoặc không đúng}}{\rightarrow}$  Nếu ứng dụng còn chạy thì K8S không đụng đến, ngược lại K8S sẽ loại bỏ pod đó và thay thế bằng 1 pod mới. 
		- Readiness probe để xác định mức độ sẵn sàng cho ứng dụng của bạn.
			- Kiểm tra và đảm bảo khi nào ứng dụng sẵn sàng đón nhận lưu lượng truy cập trước khi cho phép một service gửi lưu lượng truy cập đến pods đó $\overset{\text{Không thành công}}{\rightarrow}$ Ngừng đến khi ứng dụng vượt qua được sự kiểm tra.
		- Có 3 loại probes và có thể dùng bất kì để thực hiện liveness và readiness check.
			- HTTP
			- Command 
			- TCP
	- B2: Tạo config cho việc rolling update trong file YAML.
## Recreate
- Là 1 deployment pattern cơ bản, đơn giản chỉ là shut down mọi pods chứa version cũ và thay thế chúng bằng các pods mới chứa các version mới.
- Các bước thực hiện:
	- B1: 1 ver mới của ứng dụng đã sẵn sàng để deploy.
	- B2: Các pods đang chạy ver cũ đồng loạt shut down hoặc xóa
	- B3: Pods chứa ver mới được tạo.
- Pros và Cons:
	- Pros:
		- Dễ setup.
		- Phiên bản của ứng dụng hoàn toàn được thay thế bằng phiên bản mới
	- Cons:
		- Tác động lớn tới người dùng vì xảy ra downtime ngắn giữa quá trình shutdown và deployment mới.
## Ramped Slow Rollout
- Cập nhật các pods 1 cách dần dần bằng cách tạo ra các bản sao mới, đồng thời xóa đi bản sao cũ.
- Pros and Cons:
	- Pros:
		- Dễ setup.
		- Kiểm soát được tốc độ tung ra các bản sao mới.
		- Thích hợp cho các stateful apps cần xử lý việc tái cân bằng dữ liệu.
	- Cons:
		- Rollout/rollback cần thời gian.
		- Không kiểm soát được traffic distribution.
## Best-Effort Controlled Rollout
- Chỉ định được số lượng hoặc phần trăm pods mong muốn được cập nhật tại thời điểm nhất định.
## Blue-Green 
- Blue là phiên bản hiện tại, green là bản copy của blue và có chứa ver mới. Sau khi green được test kĩ và đã được fix thì lưu lượng truy cập của người dùng sẽ được chuyển từ blue sang green thông qua load balancer.
- Các bước thực hiện:
	- **B1: Setup môi trường**
		- **Khởi tạo app**
			- Khởi tạo app Blue và expose (Tạo service)
			- Khởi tạo app Green và expose (Tạo service)
		- **Tạo ingress rule**
			- Note: để ingress rule có thể hoạt động, bạn cần cài đặt phần mềm implement Ingress Controller
		- **Xác nhận app hoạt động ổn**
	- **B2: Triển khai blue-green**
		- 1. Cập nhật image cho môi trường test
		- 2. Tiến hành kiểm thử
		- 3. Switch môi trường kiểm thử với môi trường prod
- Pros và Cons:
	- **Pros:**
		- Rollout/rollback ngay lập tức
		- Ver mới có sẵn ngay lập tức cho mọi người dùng
	- **Cons:**
		- Đắt đỏ vì tốn tài nguyên gấp đôi
		- Phải test nghiêm ngặt trước khi release product
		- Khó handling các sateful apps.
## Canary
- Trong chiến lược canary, phiên bản mới của ứng dụng được thử nghiệm bằng cách thử nghiệm trên một nhóm nhỏ ngẫu nhiên người dùng cùng với phiên bản hiện tại của ứng dụng đang hoạt động. Khi phiên bản mới của ứng dụng được thử nghiệm thành công, nó sau đó được triển khai cho tất cả người dùng.
- Các bước thực hiện:
	- **Bước 1: Tạo 1 Virtual Service và các Destination Rules**
		- Đầu tiên, tạo một Virtual Service để xác định cách lưu lượng sẽ được định tuyến giữa các phiên bản khác nhau của ứng dụng của bạn. 
		- Tiếp theo, tạo Destination Rules để xác định các tập hợp con các ver có sẵn cho ứng dụng. 
	- **Bước 2: Tạo Các Deployments** 
		- Tạo 2 phiên bản của ứng dụng của bạn, tức là Phiên bản ổn định (v1) và Phiên bản canary mới (v2) và gắn nhãn cho mỗi phiên bản tương ứng. 
	- **Bước 3: Theo dõi và Điều chỉnh Phân chia Lưu lượng** 
		- Theo dõi hiệu suất của ứng dụng của bạn và thu thập phản hồi từ người dùng để xác định xem phiên bản canary có ổn định không. 
		- Nếu thành công, dần dần tăng lưu lượng cho phiên bản canary bằng cách điều chỉnh trọng số trong Virtual Service.
- Pros và Cons:
	- **Pros:**
		- Thuận tiện cho việc theo dõi độ tin cậy, lỗi và hiệu suất
		- Rollback nhanh chóng
	- **Cons:**
		- Rollout chậm, người dùng tiếp cận dần dần
## Shadow
Một Shadow deployment là một phương pháp trong đó phiên bản mới của ứng dụng (phiên bản "Shadow") nhận lưu lượng thực tế từ thế giới thực song song với phiên bản hiện tại, nhưng không ảnh hưởng đến người dùng cuối.
- Pros và Cons:
	- Pros:
		- Kiểm tra hiệu suất với lưu lượng sản xuất
		- Không ảnh hưởng đến người dùng
		- Không có downtime
	- Cons:
		- Tốn kém (sử dụng gấp đôi tài nguyên)
		- Không phải là một user test thực sự, có thể dẫn đến kết quả bị hiểu sai
		- Thiết lập phức tạp
		- Đòi hỏi sự giám sát cho cả hai môi trường
## A/B Testing
- A/B Testing, trong ngữ cảnh của các chiến lược triển khai, là về việc triển khai hai hoặc nhiều phiên bản của một tính năng ứng dụng đến một phần nhỏ người dùng cùng một lúc để xem phiên bản nào hoạt động tốt hơn về mặt tương tác người dùng, tỷ lệ lỗi, hoặc các KPI khác.
- Các điều kiện có thể:
	- Định vị địa lý
	- Ngôn ngữ
	- Cookie
	- Tác nhân người dùng (thiết bị, hệ điều hành, v.v.)
	- Tiêu đề tùy chỉnh - Tham số truy vấn
- Pros và Cons:
	- **Pros:**
		- Nhiều phiên bản chạy song song
		- Hoàn toàn kiểm soát được phân phối lưu lượng
		- Công cụ tuyệt vời có thể được sử dụng cho mục đích kinh doanh để cải thiện tỷ lệ chuyển đổi
	- **Cons:**
		- Yêu cầu bộ cân bằng tải thông minh (Istio, Linkerd, v.v.)
		- Khó khăn trong việc xử lý sự cố cho một phiên, việc theo dõi phân tán trở nên bắt buộc
- Istio: là một dự án mã nguồn mở được tạo ra để quản lý, bảo mật và kết nối các dịch vụ microservices trong một môi trường đám mây. Được phát triển bởi Google, IBM và Lyft, Istio cung cấp các tính năng như kiểm soát lưu lượng, quản lý bảo mật, theo dõi và xử lý lỗi, giúp quản trị và phát triển hệ thống dễ dàng triển khai, quản lý và theo dõi các ứng dụng phức tạp dựa trên microservices.
# Sum up
- Recreate nếu thời gian chết không phải là vấn đề
- Recreate and ramped không đòi hỏi bất kỳ bước bổ sung nào (lệnh `kubectl apply` là đủ)
- Ramped and blue/green deployment thường là phù hợp và dễ sử dụng
- Blue/green phù hợp cho front-end của ứng dụng tải tài nguyên phiên bản từ cùng một máy chủ
- Blue/green and shadow có thể tốn kém
- Canary and A/B testingnên được sử dụng nếu không tự tin vào chất lượng của bản phát hành
- Canary, A/B testing and shadow có thể đòi hỏi các cluster component bổ sung 