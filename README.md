# Tên dự án : Sentiment Analysis for Product Reviews

## 1. Giới thiệu dự án

- Trong thời đại thương mại điện tử phát triển mạnh mẽ, các nền tảng mua sắm trực tuyến nhận được hàng triệu đánh giá từ khách hàng mỗi ngày. Những đánh giá này chứa nhiều thông tin giá trị về chất lượng sản phẩm, trải nghiệm người dùng và mức độ hài lòng của khách hàng. Tuy nhiên, việc đọc và phân tích thủ công khối lượng dữ liệu lớn này dường như bất khả thi.

- Dự án **Sentiment Analysis for Product Reviews** được thực hiện nhằm xây dựng một hệ thống phân loại cảm xúc tự động sử dụng các thuật toán Học Máy (Machine Learning). Hệ thống sẽ phân tích nội dung đánh giá sản phẩm và phân loại chúng thành ba nhóm cảm xúc:

* Positive (Tích cực)
* Neutral (Trung lập)
* Negative (Tiêu cực)

- Thông qua dự án, nhóm có cơ hội áp dụng quy trình phát triển một dự án Machine Learning hoàn chỉnh, từ thu thập dữ liệu, tiền xử lý văn bản, xây dựng mô hình đến đánh giá và phân tích kết quả.

## 2. Mục tiêu dự án

Xây dựng hệ thống phân tích cảm xúc đánh giá sản phẩm dựa trên dữ liệu văn bản bằng các thuật toán Machine Learning.

## 3. Dataset

### Nguồn dữ liệu

- Dự án sử dụng bộ dữ liệu đánh giá sản phẩm điện tử từ Amazon Reviews (https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews)

- Dataset chứa các thông tin như:

* Nội dung đánh giá (review text)
* Điểm đánh giá (rating)
* Thông tin sản phẩm

### Chuyển đổi nhãn cảm xúc

- Điểm đánh giá được chuyển thành 3 lớp cảm xúc:

| Rating    | Sentiment |
| --------- | --------- |
| 1 - 2 sao | Negative  |
| 3 sao     | Neutral   |
| 4 - 5 sao | Positive  |
