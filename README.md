# Bank Marketing DataSet - Intelligent Targeting:
***
## Marketing Introduction:
*Quá trình mà các công ty tạo ra giá trị cho khách hàng và xây dựng mối quan hệ khách hàng mạnh mẽ nhằm thu nhận giá trị từ khách hàng đổi lại*

**Kotler and Armstrong (2010).**
***

**Marketing campaigns** thường tập trung vào nhu cầu của khách hàng và sự hài lòng tổng thể của họ. Tuy nhiên, có nhiều yếu tố khác nhau quyết định liệu một chiến dịch tiếp thị có thành công hay không. Chúng ta cần xem xét một số yếu tố nhất định khi thực hiện một chiến dịch tiếp thị. <br>

## The 4 Ps:
1) Segment of the <b>Population:</b> Chiến dịch tiếp thị sẽ nhắm đến phân khúc dân số nào và tại sao? Khía cạnh này rất quan trọng vì nó giúp xác định phần dân số nào nên nhận được thông điệp của chiến dịch tiếp thị.  <br><br>
2) Distribution channel to reach the customer's <b>place</b>: Áp dụng chiến lược hiệu quả nhất để tối ưu hóa chiến dịch tiếp thị. Chúng ta nên nhắm đến phân khúc dân số nào? Dụng cụ nào nên được sử dụng để truyền tải thông điệp? (Ví dụ: Điện thoại, Đài phát thanh, TV, Mạng xã hội, v.v.)<br><br>
3) <b> Price:</b> Giá tốt nhất để cung cấp cho khách hàng tiềm năng là gì? (Trong trường hợp chiến dịch tiếp thị của ngân hàng, điều này không cần thiết vì ngân hàng chủ yếu quan tâm đến việc khách hàng tiềm năng mở tài khoản tiền gửi để duy trì hoạt động của ngân hàng.)<br><br>
4) <b> Promotional</b> Strategy: Đây là cách mà chiến lược sẽ được triển khai và làm thế nào để tiếp cận khách hàng tiềm năng. Đây nên là bước cuối cùng trong phân tích chiến dịch tiếp thị, bởi cần phải phân tích kỹ lưỡng các chiến dịch trước đó (nếu có) để học hỏi từ những sai lầm và xác định cách làm cho chiến dịch tiếp thị hiệu quả hơn.

   # Regarding this Kernel:
Tôi biết đây là một tập dữ liệu rất phổ biến vì nó đến từ <b>UCI Machine Learning Repository</b>. Tuy nhiên, tôi tin rằng vẫn có một số thông tin chi tiết thú vị mà bạn có thể sử dụng để tích hợp vào phân tích dữ liệu của riêng mình.

### New Updates:
<ul> 
    <li>Xác định các nhóm trong mẫu dân số có khả năng cao nhất mở tài khoản tiền gửi có kỳ hạn.</li>



# Tiền gửi có kỳ hạn là gì? 
**Term deposit** là một khoản tiền gửi mà ngân hàng hoặc tổ chức tài chính cung cấp với lãi suất cố định (thường tốt hơn so với việc mở tài khoản tiền gửi thông thường). Khoản tiền này sẽ được hoàn trả sau một thời gian nhất định, gọi là thời gian đáo hạn. Để biết thêm thông tin chi tiết về tiền gửi có kỳ hạn, bạn có thể nhấn vào đường link từ Investopedia: https://www.investopedia.com/terms/t/termdeposit.asp



# Outline: <br>
***
A. **Attribute Descriptions**<br>
I. *[Bank client data](#bank_client_data)<br>
II. *[Related with the last contact of the current campaign](#last_contact)<br>
III. [Other attributes](#other_attributes) <br>

B. **Structuring the data:** <br>
I. *[Overall Analysis of the Data](#overall_analysis)<br>
II. *[Data Structuring and Conversions](#data_structuring) <br>

C. **Exploratory Data Analysis (EDA)**<br>
I. *[Accepted vs Rejected Term Deposits](#accepted_rejected) <br>
II. *[Distribution Plots](#distribution_plots) <br>

D. **Different Aspects of the Analysis: **<br>
I. *[Months of Marketing Activty](#months_activity) <br>
II. *[Seasonalities](#seasonality) <br>
III. *[Number of Calls to the potential client](#number_calls) <br>
IV. *[Age of the Potential Clients](#age_clients) <br>
V. [Types of Occupations that leads to more term deposits suscriptions](#occupations) <br>

E. **Correlations that impacted the decision of Potential Clients.**
I. *[Analysis of our Correlation Matrix](#analysis_correlation) <br>
II. *[Balance Categories vs Housing Loans](#balance_housing)<br>
III. [Negative Relationship between H.Loans and Term Deposits](#negative_relationship) <br>

F. ** Classification Model **<br>
I. [Introduction](#classification_model)<br> 
II. [Stratified Sampling](#stratified)<br>
III. [Classification Models](#models)<br>
IV. [Confusion Matrix](#confusion)<br>
V. [Precision and Recall Curve](#precision_recall)<br>
VI. [Feature Importances Decision Tree C.](#decision) <br>

G. ** Next Campaign Strategy**<br>
I. [Actions the Bank should Consider](#bank_actions)<br>

# A. Attributes Description: <br>

Input variables:<br>
# Ai. bank client data:<br>
<a id="bank_client_data"></a>
1 - **age:** (numeric)<br>
2 - **job:** type of job (categorical: 'admin.','blue-collar','entrepreneur','housemaid','management','retired','self-employed','services','student','technician','unemployed','unknown')<br>
3 - **marital:** marital status (categorical: 'divorced','married','single','unknown'; note: 'divorced' means divorced or widowed)<br>
4 - **education:** (categorical: primary, secondary, tertiary and unknown)<br>
5 - **default:** khách hàng có nợ xấu không? (categorical: 'no','yes','unknown')<br>
6 - **housing:** khách hàng có vay mua nhà không? (categorical: 'no','yes','unknown')<br>
7 - **loan:** hkhách hàng có khoản vay cá nhân không? (categorical: 'no','yes','unknown')<br>
8 - **balance:** Số dư tài khoản của khách hàng.
# Aii. Liên quan đến cuộc liên hệ cuối cùng của chiến dịch hiện tại:
<a id="last_contact"></a>
8 - **contact:** contact communication type (categorical: 'cellular','telephone') <br>
9 - **month:** last contact month of year (categorical: 'jan', 'feb', 'mar', ..., 'nov', 'dec')<br>
10 - **day:** last contact day of the week (categorical: 'mon','tue','wed','thu','fri')<br>
11 - **duration:** lhời gian liên lạc cuối cùng, tính bằng giây (số). Lưu ý quan trọng: thuộc tính này có ảnh hưởng lớn đến đầu ra mục tiêu (ví dụ: nếu thời gian = 0 thì y = ‘không’). Tuy nhiên, thời gian này không được biết trước khi cuộc gọi được thực hiện. Ngoài ra, sau khi kết thúc cuộc gọi, y sẽ rõ ràng. Do đó, đầu vào này chỉ nên được bao gồm để mục đích tham chiếu và nên bị loại bỏ nếu có ý định tạo ra một mô hình dự đoán thực tế.<br>
# Aiii. other attributes:<br>
<a id="other_attributes"></a>
12 - **campaign:** number of contacts performed during this campaign and for this client (numeric, includes last contact)<br>
13 - **pdays:** number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted)<br>
14 - **previous:** number of contacts performed before this campaign and for this client (numeric)<br>
15 - **poutcome:** outcome of the previous marketing campaign (categorical: 'failure','nonexistent','success')<br>

Output variable (desired target):<br>
21 - **TIỀN GỬI** - has the client subscribed a term deposit? (binary: 'yes','no')
