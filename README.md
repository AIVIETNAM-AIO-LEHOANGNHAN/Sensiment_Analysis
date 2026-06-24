# Tên dự án : Sentiment Analysis for Product Reviews

## 1. Giới thiệu dự án

- Trong thời đại thương mại điện tử phát triển mạnh mẽ, các nền tảng mua sắm trực tuyến nhận được hàng triệu đánh giá từ khách hàng mỗi ngày. Những đánh giá này chứa nhiều thông tin giá trị về chất lượng sản phẩm, trải nghiệm người dùng và mức độ hài lòng của khách hàng. Tuy nhiên, việc đọc và phân tích thủ công khối lượng dữ liệu lớn này dường như bất khả thi.

- Dự án **Sentiment Analysis for Product Reviews** được thực hiện nhằm xây dựng một hệ thống phân loại cảm xúc tự động sử dụng các thuật toán Học Máy (Machine Learning). Hệ thống sẽ phân tích nội dung đánh giá sản phẩm và phân loại chúng thành ba nhóm cảm xúc: Positive (Tích cực), Neutral (Trung lập), Negative (Tiêu cực)

- Thông qua dự án, nhóm có cơ hội áp dụng quy trình phát triển một dự án Machine Learning hoàn chỉnh, từ thu thập dữ liệu, tiền xử lý văn bản, xây dựng mô hình đến đánh giá và phân tích kết quả.

## 2. Mục tiêu dự án

Xây dựng hệ thống phân tích cảm xúc đánh giá sản phẩm dựa trên dữ liệu văn bản bằng các thuật toán Machine Learning.

## 3. Dataset

- Dự án sử dụng bộ dữ liệu đánh giá sản phẩm điện tử từ Amazon Reviews (https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews). Bao gồm 10 thuộc tính (columns) và 568.454 đánh giá được thu thập từ Amazon trong giai đoạn 1999–2012 :

| Thuộc tính               | Kiểu dữ liệu  | Mô tả                                                   |                     |
| ------------------------ | ------------- | ------------------------------------------------------- | ------------------- |
| `Id`                     | Integer       | Mã định danh duy nhất của mỗi bản ghi đánh giá          |                     |
| `ProductId`              | String        | Mã định danh sản phẩm trên Amazon                       |                     |
| `UserId`                 | String        | Mã định danh người dùng đã viết đánh giá                |                     |
| `ProfileName`            | String        | Tên hiển thị của người dùng                             |                     |
| `HelpfulnessNumerator`   | Integer       | Số người đánh giá review này là hữu ích                 |                     |
| `HelpfulnessDenominator` | Integer       | Tổng số người tham gia đánh giá tính hữu ích của review |                     |
| `Score`                  | Integer (1–5) | Điểm đánh giá sản phẩm từ 1 đến 5 sao                   |                     |
| `Time`                   | Integer       | Thời gian đánh giá dưới dạng Unix Timestamp             |                     |
| `Summary`                | Text          | Tiêu đề hoặc tóm tắt ngắn của đánh giá                  |                     |
| `Text`                   | Text          | Nội dung chi tiết của đánh giá sản phẩm                 | ([Hugging Face][1]) |

[1]: https://huggingface.co/datasets/jhan21/amazon-food-reviews-dataset?utm_source=chatgpt.com "jhan21/amazon-food-reviews-dataset · Datasets at Hugging Face"

## 4. Phân công vai trò

| Thành viên        | Vai trò                           | Trách nhiệm                                                                                                                                                                                                                           |
| ----------------- | --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Lê Hoàng Nhân** | **Tech Leader và QA/QC**           | Quản lý tiến độ dự án trên Jira Kanban, quản lý GitHub Repository, phân công công việc, review Pull Request, kiểm thử chất lượng dữ liệu và mô hình, đánh giá kết quả thực nghiệm, tổng hợp báo cáo và hoàn thiện sản phẩm cuối cùng. |
| **Nguyễn Thị Thu Hiền**  | **AI Engineer Data (AIE Data)**   | Thu thập dữ liệu, mô tả dataset, thực hiện EDA, kiểm tra dữ liệu khuyết thiếu và dữ liệu trùng lặp, xây dựng nhãn cảm xúc, tiền xử lý văn bản và trực quan hóa dữ liệu.                                                               |
| **Nguyễn Quốc Bảo**  | **AI Engineer Model (AIE Model)** | Trích xuất đặc trưng TF-IDF, xây dựng và huấn luyện mô hình Multinomial Naive Bayes và Logistic Regression, thực hiện các thí nghiệm Unigram và Bigram, hỗ trợ phân tích kết quả và trực quan hóa WordCloud.                          |

## 5. Pipeline dự án
```text
Amazon Fine Food Reviews Dataset
                │
                ▼
      Data Understanding
      (Khảo sát dữ liệu)
                │
                ▼
              EDA
  (Missing, Duplicate, Distribution)
                │
                ▼
      Label Construction
(Score → Positive/Neutral/Negative)
                │
                ▼
        Text Preprocessing
 ├─ Remove HTML Tags
 ├─ Lowercase
 ├─ Remove Punctuation
 ├─ Remove Stopwords
 └─ Text Cleaning
                │
                ▼
      Feature Engineering
           TF-IDF
     ├─ Unigram
     └─ Bigram
                │
                ▼
         Train/Test Split
                │
      ┌─────────┴─────────┐
      ▼                   ▼
MultinomialNB    LogisticRegression
      │                   │
      └─────────┬─────────┘
                ▼
        Model Evaluation
 ├─ Accuracy
 ├─ Precision
 ├─ Recall
 ├─ Macro F1-score
 └─ Confusion Matrix (3×3)
                │
                ▼
      Model Comparison
 ├─ NB vs LR
 └─ Unigram vs Bigram
                │
                ▼
       Result Analysis
 ├─ Top Positive Words
 ├─ Top Negative Words
 ├─ WordCloud Positive
 ├─ WordCloud Neutral
 └─ WordCloud Negative
                │
                ▼
        Final Report
```
