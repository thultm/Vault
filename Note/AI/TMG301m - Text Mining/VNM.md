# Giới thiệu

## Tổng quan về sự quan trọng của tiền xử lý văn bản trong khai thác văn bản

- Tiền xử lý văn bản bao gồm việc biến đổi văn bản trước khi phân tích thông qua các kỹ thuật như tách từ, loại bỏ stop words, stemming/lemmatization, vv. Những quyết định này có thể ảnh hưởng đáng kể đến kết quả.
- Tiền xử lý nhằm tăng cường sức mạnh thống kê bằng cách giảm chiều dữ liệu/thưa thớt, nhưng nó cũng có thể loại bỏ thông tin hữu ích hoặc gây ra lỗi nếu thực hiện không đúng cách.
- Các quyết định được thực hiện trong quá trình tiền xử lý ảnh hưởng đến việc khai thác nói chung và/hoặc cách sử dụng ngôn ngữ trong văn bản. Điều này ảnh hưởng đến khả năng giải quyết các loại câu hỏi nghiên cứu khác nhau.
- Tiền xử lý quan trọng vì nó xác định các đặc điểm ngôn ngữ được trích xuất trong quá trình khai thác văn bản với từ vựng mở, nơi không có từ điển được định trước. Nó cũng có thể ảnh hưởng đến độ chính xác đo lường trong việc khai thác văn bản với closed vocabulary.
- Thực hiện tiền xử lý kém hoặc không nhất quán là vấn đề phổ biến trong nghiên cứu khai thác văn bản trong quá khứ. Tuy nhiên, các khuyến nghị về tiền xử lý đã không nhất quán.
- Nếu không thực hiện đúng cách, tiền xử lý có khả năng không cố ý làm thay đổi kết quả, làm giảm tính đáng tin cậy và tính chính xác, tương tự như "researcher degrees of freedom".
- Bài báo này nhằm giải quyết các khuyến nghị tiền xử lý mâu thuẫn bằng cách cung cấp hướng dẫn dựa trên cơ sở thực tế dựa trên việc xem xét văn bản về ngôn ngữ học tính toán và nghiên cứu tổ chức.
- Mục tiêu là cải thiện hiểu biết về tác động của tiền xử lý, tăng cường tính hợp lệ và thúc đẩy tính minh bạch và khả năng nhân bản trong nghiên cứu khai thác văn bản. Tiền xử lý thường bị bỏ qua nhưng có ảnh hưởng mạnh đến phân tích và kết quả.

## Khuyến nghị mâu thuẫn trong nghiên cứu trước đây

- Stemming - Các nhà nghiên cứu đã đưa ra bốn khuyến nghị khác nhau:
    - Luôn luôn thực hiện stemming trừ trường hợp văn bản ngắn
    - Chỉ thực hiện stemming trong các tập dữ liệu nhỏ
    - Chỉ thực hiện stemming nếu không làm giảm độ chính xác trong phân loại/dự đoán
    - Cân nhắc cẩn thận việc thực hiện stemming chỉ sau khi thực hiện mô hình hóa chủ đề
- Sửa lỗi chính tả - Một số người đề nghị sửa lỗi chính tả để tiêu chuẩn hóa văn bản và giảm nhiễu, trong khi người khác lưu ý rằng sự khác biệt về chính tả cá nhân có thể dự đoán các đặc điểm.
- Loại bỏ stop words - Một số người đề nghị loại bỏ các từ rất phổ biến, trong khi người khác lưu ý rằng những từ này quan trọng để đánh giá phong cách giao tiếp riêng biệt.
- Tiền xử lý cho việc khai thác văn bản từ vựng đóng cửa và từ vựng mở - Các bài báo phương pháp trước đây đã mô tả quá trình khai thác văn bản tổng quan nhưng khuyến nghị không nhất quán cho việc sử dụng từ vựng đóng cửa và từ vựng mở.
- Báo cáo về tiền xử lý - Đa số các nghiên cứu về từ vựng đóng cửa không báo cáo bất kỳ tiền xử lý nào đã được thực hiện, mặc dù một số công cụ đề xuất nó. Tuy nhiên, từ vựng đóng cửa đòi hỏi xác định rõ tất cả các quyết định về tiền xử lý.
- Xem xét về câu hỏi nghiên cứu và đặc điểm của dữ liệu - Các khuyến nghị trước đây không cung cấp hướng dẫn cụ thể về cách tiền xử lý phải tính đến các yếu tố như loại câu hỏi, sự tập trung vào nội dung so với phong cách, kích thước ngữ liệu, độ dài trung bình của tài liệu, v.v. Tóm lại, bài báo lưu ý rằng đã có các quan điểm mâu thuẫn về các kỹ thuật cụ thể cũng như tích hợp không nhất quán của các yếu tố ngữ cảnh quan trọng như nhu cầu nghiên cứu và đặc điểm dữ liệu vào các khuyến nghị về tiền xử lý.

## Mục tiêu của bài báo hiện tại để giải quyết các khuyến nghị mâu thuẫn và cung cấp hướng dẫn
- Tiến hành hai cuộc đánh giá bổ sung của văn bản về ngôn ngữ học tính toán và nghiên cứu văn bản tổ chức để nâng cao hiểu biết về việc liệu nghiên cứu tổ chức có tuân theo các phương pháp tốt nhất hay không.
- Rút ra các phương pháp tiền xử lý tốt nhất từ cuộc đánh giá văn bản về ngôn ngữ học tính toán. Sau đó, xem xét một cách phê phán các phương pháp tiền xử lý trong nghiên cứu tổ chức.
- Cung cấp hướng dẫn ra quyết định về tiền xử lý văn bản dựa trên cơ sở thực tế, bao gồm:
    - Xem xét việc khai thác văn bản từ vựng đóng cửa hoặc từ vựng mở
    - Câu hỏi nghiên cứu đang được điều tra
    - Đặc điểm của tập dữ liệu, bao gồm kích thước ngữ liệu và độ dài trung bình của tài liệu
- Giải quyết các khuyến nghị tiền xử lý mâu thuẫn đã xuất hiện trong nghiên cứu trước đây.
- Cải thiện các phương pháp tiền xử lý văn bản hiện tại dựa trên cuộc đánh giá và xem xét lý thuyết/thực tế đã thảo luận.
- Đưa ra khuyến nghị cho cả việc thực hiện tiền xử lý văn bản và báo cáo nghiên cứu về khai thác văn bản để thúc đẩy tính minh bạch và khả năng nhân bản.
- Mục tiêu của các khuyến nghị là nâng cao tính hợp lệ của kết quả khai thác văn bản, hiểu biết của các nhà nghiên cứu về tác động của tiền xử lý và tính minh bạch và khả năng nhân bản tổng thể của nghiên cứu khai thác văn bản.
# Những xem xét về mặt lý thuyết cho việc tiền xử lý

## Khai thác văn bản từ vựng đóng cửa so với từ vựng mở
### Khai thác văn bản từ vựng đóng cửa:

- Sử dụng từ điển trước chứa danh sách các từ và cụm từ liên quan về mặt khái niệm
- Đếm số lần xuất hiện của từ/cụm từ trong các từ điển này để phân tích ngôn ngữ và trích xuất các đặc điểm
- Tiếp cận suy luận hơn với các đặc điểm đã được xác định trước bởi từ điển
- Ví dụ bao gồm các từ điển LIWC cho các cấu trúc ngôn ngữ và tâm lý học
- Có thể được sử dụng cho việc mã hóa thủ công, từ điển được phát triển cho các cấu trúc tổ chức

### Khai thác văn bản từ vựng mở:

- Không có từ điển được xác định trước, vì vậy sử dụng bất kỳ n-gram (cụm từ có độ dài n) nào có thể trở thành các đặc điểm tiềm năng
- Tiếp cận hơn là suy luận, trong đó các đặc điểm văn bản không được xác định trước
- Thường được sử dụng cho các ứng dụng máy học như phân loại/dự đoán
- Hữu ích cho ngữ cảnh có ngôn ngữ không tiêu chuẩn như chính tả sai hoặc biểu cảm qua biểu tượng cảm xúc
- Những gì được thu thập phụ thuộc hoàn toàn vào quyết định tiền xử lý vì chúng ảnh hưởng đến những từ/cụm từ nào còn lại trong văn bản

### Sự khác biệt ảnh hưởng đến tiền xử lý:

- Tiền xử lý có thể ảnh hưởng đến tính hợp lệ cho cả hai bằng cách thay đổi các từ khớp giữa văn bản và từ điển (đóng cửa) hoặc loại bỏ hoàn toàn các từ (mở)
- Văn bản từ vựng mở yêu cầu xác định rõ tất cả các quyết định tiền xử lý vì chúng quyết định việc trích xuất các đặc điểm Như vậy, văn bản từ vựng đóng cửa sử dụng các từ điển đã xác định trước trong khi văn bản từ vựng mở trích xuất các đặc điểm từ văn bản, và sự khác biệt cơ bản này ảnh hưởng đến cách tiền xử lý ảnh hưởng đến tính hợp lệ và những gì phải được báo cáo.

## Bắt kịp nội dung so với phong cách của ngôn ngữ

- Các từ nội dung (danh từ, động từ, tính từ) truyền đạt chủ đề hoặc nội dung đang được truyền đạt. Chúng thường khác nhau dựa trên tình huống.
- Các từ chức năng (đại từ, giới từ, mạo từ) truyền đạt phong cách ngôn ngữ hoặc cách truyền đạt thông điệp. Chúng thường là chỉ số liên tục về sự khác biệt cá nhân.
- Các từ nội dung quan trọng hơn để hiểu biết về các biến đổi liên quan đến ngữ cảnh từ văn bản như chủ đề có thể dự đoán tương lai.
- Các từ chức năng quan trọng hơn để hiểu biết về sự khác biệt cá nhân ổn định giữa các biến đổi có thể suy luận từ các mẫu ngôn ngữ, như tính cách.
- Một số kỹ thuật tiền xử lý như loại bỏ từ dừng giảm khả năng truy cập để thu thập kiểu chức năng truyền đạt bằng từ.
- Các kỹ thuật như sửa chính tả có thể thay đổi tính hợp lệ của từ nội dung nếu sửa chính tả giới thiệu lỗi.
- Câu hỏi nghiên cứu nên quyết định liệu tập trung vào nội dung, phong cách hoặc cả hai để hướng dẫn tiền xử lý.
- Nếu mục tiêu là các biến đổi giống các biến đổi trạng thái, phụ thuộc vào ngữ cảnh từ văn bản như các chủ đề có thể dự đoán tương lai, thì những điểm lạ qua chữ in hoa có thể biểu thị trạng thái tâm lý.
- Nhưng khi không tập trung vào biến đổi cá nhân, việc tiêu chuẩn hóa qua các kỹ thuật như sửa chính tả có thể cải thiện tính chính xác của đo lường.
- Quyết định tiền xử lý nên được thực hiện phù hợp với việc nghiên cứu có mục tiêu trích xuất các đặc điểm ngôn ngữ dựa trên nội dung hoặc phong cách.

## Sự quan trọng của câu hỏi nghiên cứu

- Câu hỏi nghiên cứu nên quyết định liệu khai thác văn bản tập trung vào từ nội dung, từ chức năng hoặc cả hai.
- Từ nội dung quan trọng hơn cho các biến đổi giống trạng thái, phụ thuộc vào ngữ cảnh như các chủ đề có thể dự đoán tương lai, trong khi từ chức năng tập trung hơn vào các biến đổi cá nhân ổn định có thể suy luận từ mẫu ngôn ngữ như tính cách.
- Tiền xử lý nhằm tăng cường sức mạnh thống kê, nhưng nó có thể loại bỏ thông tin hữu ích nếu không phù hợp với câu hỏi nghiên cứu.
- Câu hỏi nghiên cứu xác định liệu việc khai thác văn bản từ vựng đóng cửa (đòi hỏi từ điển được xác định trước) hoặc văn bản từ vựng mở (sử dụng bất kỳ đặc điểm văn bản nào) phù hợp hơn.
- Khai thác văn bản từ vựng đóng cửa và văn bản từ vựng mở có các yêu cầu về tiền xử lý cụ thể do chúng ảnh hưởng đến việc nào từ/cụm từ nào còn lại trong văn bản (đóng cửa) hoặc loại bỏ hoàn toàn các từ (mở).
- Khuyến nghị về tiền xử lý thay đổi dựa trên việc khai thác nếu mục tiêu là trích xuất nội dung về chủ đề hoặc các mẫu ngôn ngữ.
- Câu hỏi nghiên cứu quan trọng cho việc lựa chọn kỹ thuật khai thác văn bản và phương pháp tiền xử lý.

## Xem xét kích thước ngữ liệu và độ dài trung bình của tài liệu

- Kích thước của ngữ liệu ảnh hưởng đến việc thực hiện tiền xử lý. Trong trường hợp dữ liệu lớn, cần cân nhắc việc tiền xử lý để làm giảm kích thước và thưa thớt.
- Độ dài trung bình của tài liệu ảnh hưởng đến việc quyết định tiền xử lý. Trong trường hợp tài liệu ngắn, việc thực hiện stemming có thể không cần thiết.
- Để đảm bảo tính minh bạch và khả năng nhân bản, cần báo cáo chi tiết về việc thực hiện tiền xử lý và tác động của nó đối với đặc điểm văn bản.
- Tóm lại, quyết định tiền xử lý nên được xem xét kích thước và độ dài của tập dữ liệu, cùng với câu hỏi nghiên cứu để đảm bảo tính hợp lệ và tính minh bạch của kết quả.

# Các phương pháp tiền xử lý tốt nhất từ cuộc đánh giá văn bản về ngôn ngữ học tính toán

- Cuộc đánh giá được thực hiện để xác định các phương pháp tiền xử lý tốt nhất dựa trên việc hiểu rõ tác động của tiền xử lý đối với các đặc điểm văn bản. Cuộc đánh giá bao gồm một loạt các kỹ thuật tiền xử lý khác nhau và đánh giá tác động của chúng đối với việc trích xuất các đặc điểm.
- Cuộc đánh giá sử dụng các tập dữ liệu ngôn ngữ học tính toán chưa được tiền xử lý và các tập dữ liệu đã được tiền xử lý bằng các phương pháp khác nhau.
- Kết quả cho thấy rằng tiền xử lý như stemming và sửa lỗi chính tả có thể làm giảm tính hợp lệ của việc trích xuất các đặc điểm, đặc biệt là đối với các đặc điểm từ nội dung. Stemming có thể làm mất đi sự khác biệt giữa các dạng của cùng một từ và sửa lỗi chính tả có thể thay đổi ý nghĩa của các từ.
- Cuộc đánh giá cũng cho thấy rằng việc loại bỏ stop words không ảnh hưởng lớn đến tính hợp lệ của việc trích xuất các đặc điểm. Tuy nhiên, việc loại bỏ stop words có thể giúp giảm nhiễu trong các mẫu ngôn ngữ.
- Kết quả của cuộc đánh giá cho thấy rằng tiền xử lý nên được thực hiện một cách cẩn thận và cân nhắc, và nên được báo cáo chi tiết để đảm bảo tính minh bạch và khả năng nhân bản của nghiên cứu.
- Các phương pháp tiền xử lý tốt nhất là những phương pháp không làm thay đổi quá nhiều về nội dung và ngôn ngữ ban đầu của văn bản.

# Các phương pháp tiền xử lý trong nghiên cứu tổ chức

- Cuộc đánh giá nghiên cứu tổ chức được thực hiện để xem xét việc thực hiện tiền xử lý trong nghiên cứu tổ chức và tác động của nó đối với việc trích xuất các đặc điểm.
- Kết quả của cuộc đánh giá cho thấy rằng nhiều nghiên cứu tổ chức không báo cáo chi tiết về việc thực hiện tiền xử lý, và không có sự nhất quán trong việc tiền xử lý giữa các nghiên cứu.
- Cuộc đánh giá cũng chỉ ra rằng việc thực hiện tiền xử lý có thể ảnh hưởng đến tính hợp lệ của việc trích xuất các đặc điểm. Đặc biệt, việc sử dụng các phương pháp tiền xử lý như stemming và sửa lỗi chính tả có thể làm mất đi sự khác biệt giữa các biến đổi của cùng một từ trong các mẫu ngôn ngữ và có thể thay đổi ý nghĩa của các từ.
- Tuy nhiên, cuộc đánh giá cũng cho thấy rằng việc loại bỏ stop words không ảnh hưởng lớn đến tính hợp lệ của việc trích xuất các đặc điểm và có thể giúp giảm nhiễu trong các mẫu ngôn ngữ.
- Dựa trên kết quả của cuộc đánh giá, bài báo đưa ra các khuyến nghị sau đây cho việc thực hiện tiền xử lý trong nghiên cứu tổ chức:
    - Nên báo cáo chi tiết về việc thực hiện tiền xử lý, bao gồm các phương pháp được sử dụng và tác động của chúng đối với việc trích xuất các đặc điểm.
    - Nên cân nhắc kỹ về việc sử dụng các phương pháp tiền xử lý như stemming và sửa lỗi chính tả và nên cân nhắc những tác động tiêu cực của chúng đối với tính hợp lệ của việc trích xuất các đặc điểm.
    - Nên xem xét việc loại bỏ stop words để giảm nhiễu trong các mẫu ngôn ngữ.
- Tóm lại, việc thực hiện tiền xử lý trong nghiên cứu tổ chức nên được thực hiện cẩn thận, cân nhắc và nên được báo cáo chi tiết để đảm bảo tính minh bạch và khả năng nhân bản của nghiên cứu.

# Khuyến nghị về tiền xử lý và báo cáo nghiên cứu

- Dựa trên kết quả của cuộc đánh giá và các xem xét lý thuyết, bài báo đưa ra các khuyến nghị sau đây cho việc thực hiện tiền xử lý và báo cáo nghiên cứu về khai thác văn bản:
    - Mục tiêu của nghiên cứu nên quyết định liệu tiền xử lý tập trung vào từ nội dung, từ chức năng hoặc cả hai. Câu hỏi nghiên cứu nên xác định đặc điểm ngôn ngữ cụ thể cần được trích xuất.
    - Nếu mục tiêu là trích xuất các đặc điểm từ nội dung, cân nhắc sử dụng tiền xử lý như loại bỏ stop words để giảm nhiễu, nhưng hãy cân nhắc về tác động của việc này đối với tính hợp lệ của đo lường.
    - Nếu mục tiêu là trích xuất các đặc điểm từ chức năng, cân nhắc việc sử dụng tiền xử lý như stemming hoặc sửa lỗi chính tả nhưng hãy cẩn thận để không làm mất đi sự khác biệt giữa các biến đổi của cùng một từ trong các mẫu ngôn ngữ.
    - Báo cáo chi tiết về việc thực hiện tiền xử lý, bao gồm các phương pháp được sử dụng và tác động của chúng đối với việc trích xuất các đặc điểm.
    - Nên xem xét kích thước của tập dữ liệu và độ dài trung bình của tài liệu để đảm bảo tính hợp lệ của việc thực hiện tiền xử lý.
    - Cân nhắc câu hỏi nghiên cứu, loại dữ liệu và ngữ cảnh để đưa ra quyết định về tiền xử lý phù hợp.
- Mục tiêu của các khuyến nghị là nâng cao tính hợp lệ của kết quả khai thác văn bản, hiểu biết của các nhà nghiên cứu về tác động của tiền xử lý và tính minh bạch và khả năng nhân bản tổng thể của nghiên cứu khai thác văn bản.

# Kết luận

- Bài báo đánh giá tình trạng hiện tại của tiền xử lý văn bản trong nghiên cứu ngôn ngữ học tính toán và nghiên cứu tổ chức.
- Đưa ra các khuyến nghị cụ thể về việc thực hiện tiền xử lý dựa trên các xem xét lý thuyết và kết quả của cuộc đánh giá.
- Mục tiêu của các khuyến nghị là nâng cao tính hợp lệ và khả năng nhân bản của việc khai thác văn bản và nghiên cứu về ngôn ngữ học tính toán và nghiên cứu tổ chức.