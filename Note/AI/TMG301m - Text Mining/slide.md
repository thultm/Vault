# Introduction 
- **State the title of the paper you are reviewing and the authors' names:** The paper I am reviewing is titled "Text preprocessing for text mining in organizational research: Review and recommendations" by Louis Hickman, Stuti Thapa, Louis Tay, Mengyang Cao, and Padmini Srinivasan (2022).
- **Briefly summarize the main topic of the paper and the authors' main findings:** The main topic of the paper is text preprocessing for text mining in organizational research. The authors review the most common text preprocessing techniques and provide recommendations for their use in different types of organizational research. The authors' main findings are that text preprocessing is an essential step in any text mining project, and that the choice of text preprocessing techniques should be informed by the research question, the characteristics of the text data, and the type of text mining task being performed.
# Research question and methodology
- **State the authors' research question:** The authors' research question is: What are the best practices for text preprocessing in organizational research?
- **Describe the authors' methodology:** The authors conducted a comprehensive review of the literature on text preprocessing and text mining in organizational research. They identified over 100 relevant studies, which they used to develop their recommendations. The authors also discussed the strengths and weaknesses of the different text preprocessing techniques, and provided specific recommendations for their use in different types of organizational research.
    
- **Discuss the strengths and weaknesses of the authors' methodology:** 
	- **Strengths:**
		- **Comprehensive review:** The authors conducted a comprehensive review of the literature on text preprocessing and text mining in organizational research. They identified over 100 relevant studies, which they used to develop their recommendations.
		- **Well-grounded in theory and practice:** The authors' recommendations are well-grounded in theory and practice. They discuss the strengths and weaknesses of the different text preprocessing techniques, and they provide specific recommendations for their use in different types of organizational research.
		- **Tailored to the needs of organizational researchers:** The authors' paper is tailored to the needs of organizational researchers. They provide specific examples of how text mining can be used in organizational research, and they discuss the unique challenges that organizational researchers face when using text mining.
	- **Weaknesses:**
		- **Lack of empirical evidence:** The authors do not provide any empirical evidence to support their recommendations. It would have been helpful to see some examples of how the authors' recommendations have been used in real-world research projects.
		- **Does not discuss the limitations of text mining:** The authors do not discuss the limitations of text mining. Text mining is a powerful tool, but it is important to be aware of its limitations. For example, text mining can be biased, and it can be difficult to interpret the results of text mining algorithms.

# **Results and discussion**
## Open vs closed vocabulary 
Mở rộng từ vựng (Open vocabulary) và đóng từ vựng (Closed vocabulary) là hai phương pháp khác nhau trong khai thác văn bản.

Các phương pháp mở rộng từ vựng cho phép xác định các khái niệm mới và không mong đợi, trong khi các phương pháp đóng từ vựng bị giới hạn trong một tập hợp đã xác định trước của các khái niệm.

Các phương pháp mở rộng từ vựng thường được sử dụng cho các nhiệm vụ như mô hình hóa chủ đề (topic modeling) và phân tích tâm trạng (sentiment analysis). Trong mô hình hóa chủ đề, mục tiêu là xác định các chủ đề chính được thảo luận trong một bộ văn bản. Trong phân tích tâm trạng, mục tiêu là xác định tâm trạng (ví dụ, tích cực, tiêu cực, trung lập) của một đoạn văn bản.

Các phương pháp đóng từ vựng thường được sử dụng cho các nhiệm vụ như phân loại (classification) và hồi quy (regression). Trong phân loại, mục tiêu là gán một văn bản văn bản vào một trong các loại đã xác định trước. Trong hồi quy, mục tiêu là dự đoán một giá trị số học dựa trên một đoạn văn bản.
## Preprocessing and Text Mining Overview 
| Thuật ngữ | Định nghĩa |
|---|---|
| **Chuyển chữ hoa thành chữ thường** | Chuyển tất cả văn bản thành chữ thường. Điều này giúp giảm kích thước từ vựng, vì máy tính lưu trữ chữ hoa và chữ thường khác nhau. |
| **Xử lý phủ định** | Một tập hợp các phương pháp được sử dụng để xác định, biểu diễn ngữ nghĩa và tính đến phủ định trong văn bản. Phủ định là một khái niệm quan trọng trong xử lý ngôn ngữ tự nhiên, vì nó có thể thay đổi nghĩa của một câu. |
| **Sửa lỗi chính tả** | Sửa lỗi chính tả và lỗi đánh máy trong văn bản. Điều này giúp cải thiện độ chính xác của các thuật toán xử lý ngôn ngữ tự nhiên. |
| **Mở rộng chữ viết tắt và từ viết tắt** | Mở rộng các chữ viết tắt, từ viết tắt và từ viết tắt thành các cụm từ đầy đủ của chúng. Điều này giúp các thuật toán xử lý ngôn ngữ tự nhiên hiểu được chúng. |
| **Xóa ký tự không phải chữ cái** | Xóa tất cả số, dấu câu và/hoặc ký tự đặc biệt khỏi văn bản. Điều này giúp đơn giản hóa văn bản và cải thiện độ chính xác của các thuật toán xử lý ngôn ngữ tự nhiên. |
| **Tách văn bản thành các câu** | Tách văn bản thành các câu. Điều này giúp các thuật toán xử lý ngôn ngữ tự nhiên hiểu được cấu trúc của văn bản. |
| **Tách văn bản thành các từ** | Tách văn bản thành các từ. Điều này giúp các thuật toán xử lý ngôn ngữ tự nhiên hiểu được ngữ nghĩa của văn bản. |
| **Chuẩn hóa văn bản** | Chuẩn hóa văn bản để loại bỏ các biến thể không cần thiết. Điều này giúp các thuật toán xử lý ngôn ngữ tự nhiên hoạt động chính xác hơn. |

| **Ứng dụng mẫu** | **Vấn đề** | **Tác động** | **Khuyến nghị** |
|---|---|---|---|
| **Tăng sức mạnh thống kê** | **Giảm tính hợp lệ** | **Tăng sức mạnh thống kê** | **Luôn sử dụng trừ khi kho từ có các thuật ngữ quan trọng có nghĩa khác nhau khi viết hoa so với không viết hoa.** |
| **Giảm tính hợp lệ** | **Tăng độ nhạy** | **Giảm tính hợp lệ** | **Sử dụng nếu câu hỏi nghiên cứu không liên quan đến sự khác biệt cá nhân.** |
| **Tăng sức mạnh thống kê** | **Giảm độ chính xác** | **Tăng sức mạnh thống kê** | **Sử dụng nếu từ điển chỉ chứa thuật ngữ mở rộng.** |
| **Giảm sức mạnh thống kê** | **Tăng độ chính xác** | **Giảm sức mạnh thống kê** | **Sử dụng nếu văn bản chứa nhiều số.** |
| **Tăng độ chính xác và hiệu quả** | **Giảm độ chính xác** | **Tăng độ chính xác và hiệu quả** | **Sử dụng nếu cần cải thiện độ chính xác và hiệu quả của các thuật toán xử lý ngôn ngữ tự nhiên.** |
| **Sai sót trong tách câu** | **Cải thiện độ chính xác của các thuật toán phân tích câu** | **Sử dụng các thuật toán tách câu chính xác.** |
| **Sai sót trong tách từ** | **Cải thiện độ chính xác của các thuật toán phân loại văn bản** | **Sử dụng các thuật toán tách từ chính xác.** |
| **Sai sót trong chuẩn hóa văn bản** | **Cải thiện độ chính xác của các thuật toán phân tích ngữ nghĩa** | **Sử dụng các thuật toán chuẩn hóa văn bản chính xác.** |

**Lưu ý:**

* Bảng này được kết hợp từ 2 bảng trước.
* Các cột "Từ khóa" và "Chú thích" được loại bỏ.
* Các cột "Ứng dụng mẫu" và "Khuyến nghị" được hợp nhất thành một cột "Khuyến nghị".
* Nội dung của các cột "Vấn đề" và "Tác động" được cập nhật để phù hợp với bảng kết hợp.

**Tổng kết**

Bảng này cung cấp một cái nhìn tổng quan về các thuật ngữ và phương pháp xử lý tiền xử lý trong xử lý ngôn ngữ tự nhiên (NLP). Bảng này bao gồm các định nghĩa

