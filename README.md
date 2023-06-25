# I. Background (Bối cảnh)
You are a Data Analyst working for a company called X. You are given the standard task of giving a presentation to present an overview of the business and operations of the computer company. Up to the present time at for Sales Manager and Operations Manager. The presentation should at a minimum, include the following information: business overview, top customer, and 2 to 3 suggestions (area) where the company can improve

(Bạn là một Data Analyst làm việc cho một công ty tên là X. Bạn được giao nhiệm vụ chuẩn bị một bài thuyết trình để trình bày tổng quan tình hình kinh doanh và vận hành của công ty tính đến thời điểm hiện tại cho Giám đốc bán hàng và Giám đốc vận hành. Bài thuyết trình tối thiểu phải bao gồm các thông tin sau: tổng quan tình hình kinh doanh, mức độ hài lòng của khách hàng, và đề xuất 2 đến 3 lĩnh vực (areas) mà công ty có thể cải thiện.)
# II. Analysis (Phân tích)
## Business situation of company (tình hình kinh doanh của công ty)
      import plotly.express as px
      
      turnover_year = sales_data4.groupby(sales_data4['OrderDate'].dt.year)['SubTotal'].sum().reset_index()
      
      fig = px.bar(turnover_year, x='OrderDate', y='SubTotal', title='Revenue By Year')
      
      fig.update_layout(xaxis=dict(type='category'),width=900,height=700,font=dict(color='black'))
      fig.update_traces(marker=dict(line=dict(width=50)),text=turnover_year['SubTotal'],textfont=dict(color='black'))
      fig.show()
![situation sales](https://github.com/IamQuangg/Advantureworks/assets/128073066/36178269-ecf4-4998-949e-d08331aa3c24)
- Tình hình kinh doanh của công ty có sự tăng trưởng mạnh mẽ từ năm 2011 đến năm 2013. Năm 2011 doanh thu chỉ là 12.6M nhưng đến năm 2012, con số này đã tăng lên 33.5M, tăng trưởng 37% so với năm trước. Và đến năm 2013 doanh thu đạt mức cao nhất đó là 43.6M. Tuy nhiên năm 2014, lại có một sự sụt giảm đáng kể về doanh thu về mức 20M
=> doanh thu của công ty tăng mạnh trong 2 năm nhưng đến năm thứ 3 đã suy giảm. Chúng ta sẽ cùng đi tìm hiểu lý do tại sao dẫn đến sự sụt giảm này.

- The company's business situation had a strong growth from 2011 to 2013. In 2011 the revenue was only 12.6M but by 2012, this number has increased to 33.5M, a growth of 37% compared to the previous year. . And in 2013 revenue reached the highest level of 43.6M. However, in 2014, there was a significant decrease in revenue to 20M .
=> The company's revenue increased sharply in 2 years but by the 3rd year, it decreased. Let's go to find out the reason for this decrease
## Business situation of company in 2013( Tình hình kinh doanh của kinh ty trong năm 2013)
      import plotly.express as px
      turnover_month = sales_data_2013.groupby(sales_data_2013['OrderDate'].dt.month)['SubTotal'].sum().reset_index()
      fig= px.line(turnover_month,x='OrderDate',y='SubTotal', markers=True, title='Revenue By Month')
      fig.update_traces(marker=dict(line=dict(width=10)),text=turnover_year['SubTotal'],textfont=dict(color='black'))
      fig.show()
![2013](https://github.com/IamQuangg/Advantureworks/assets/128073066/a84fa612-78c5-4f97-9f5e-7891ffbe1c8a)
- Doanh thu từ tháng 1 cho đến tháng 5 đều ở dưới mức 3.5M. Nhưng từ tháng 6 trở đi doanh thu đã tăng mạnh so với những tháng trước đó. Nhìn vào biểu đồ có thể thấy sự tăng về doanh thu rõ rệt trong 6 tháng cuối năm.

- Sales from January to May were all below 3.5M. But from June onwards, sales have increased sharply compared to the previous months. Looking at the chart, you can see a clear increase in revenue in the last 6 months of the year
##  Top product groups (product_category_name) bring the most revenue for the company in 2013 
      import plotly.express as px
      fig = px.bar(top_10_categories, x='Name_subcategory', y='TotalDue', title='Revenue By Year')
      fig.update_layout(xaxis=dict(type='category'),width=900,height=700,font=dict(color='black'))
      fig.update_traces(marker=dict(line=dict(width=20)))
      fig.show()
![newplot](https://github.com/IamQuangg/Advantureworks/assets/128073066/78cd596f-c85e-45de-a6e7-bd81cf439db5)
- Ta có thể thấy những sản phẩm có doanh thu cao nhất của công ty là Road Bikes, Mountain Bikes, Touring Bikes. Ngoài ra những vật dụng cũng đóng góp một số lượng không nhỏ vào doanh thu đó là Helmets, Gloves, Pedals. Từ đây có thể thấy công ty kinh doanh trong lĩnh vực xe đạp và những vật dụng bổ sung. Đây là những sản phẩm bán chạy nhất và mang lại nhiều doanh thu nhất cho công ty. Vì vậy chúng ta cần phải tập trung nhiều nguồn lực để mà phát triển những sản phẩm thế mạnh của công ty mình lên nữa.

- We can see the company's highest-grossing products are Road Bikes, Mountain Bikes, Touring Bikes. In addition, the items that also contribute a large amount to the revenue are Helmets, Gloves, Pedals. From here you can see the company's business in the field of bicycles and accessories. These are the best selling products and bring the most revenue for the company. Therefore, we need to focus more resources to develop our company's strong products.
## Customers with the most orders in 2013. (Những khách hàng có số lần đặt hàng nhiều nhất.)
      fig = px.bar(top_10_customers, x='CustomerID', y='cnt', title='Revenue By Year')
      fig.update_layout(xaxis=dict(type='category'),width=900,height=700,font=dict(color='black'))
      fig.update_traces(marker=dict(line=dict(width=20)))
      fig.show()
![customers](https://github.com/IamQuangg/Advantureworks/assets/128073066/acdf28ac-2f50-45c0-b546-1e3b5f121180)
- Đây là biểu đồ của 10 khách có số lần đặt hàng nhiều nhất ở công ty, họ là những người tin tưởng những sản phẩm ở công ty nên cần phải chú trọng chăm sóc họ thường xuyên để họ không rời bỏ việc mua sản phẩm bên công ty mình.

- This is a graphic of top 10 customers with the highest number of orders at the company, they are the ones who believe in the company's products, so it is necessary to pay attention to taking care of them regularly so that they do not leave buying products from the company own company.

- Thông thường, người tiêu dùng đều có xu hướng lựa chọn mua hàng theo số đông. Vì vậy, khi một doanh nghiệp làm hài lòng nhóm khách hàng hiện tại, những người này sẽ đóng vai trò làm trung gian giới thiệu sản phẩm/ dịch vụ với những người quen biết của mình. Một cách vô tình, những khách hàng trung thành đã trở thành những nhân viên bán hàng cho sản phẩm của doanh nghiệp họ tin tưởng. Điều này sẽ mang ý nghĩa sống còn với các doanh nghiệp kinh doanh thời đại 4.0, nơi sức mạnh của phương pháp marketing truyền miệng đang được thổi bùng cùng với sự phát triển của internet. Gần như chỉ cần chăm sóc tốt khách hàng hiện tại, sẽ lại có thêm khách hàng mới. Các phương pháp chăm sóc có thể như:

  - Tặng voucher cho các khách hàng khi đạt mức chi tiêu theo từng mốc.

  - Email hỏi thăm khi không thấy khách mua hàng trong thời gian dài.
- Usually, consumers tend to choose to buy in bulk. Therefore, when a business satisfies the existing group of customers, these people will act as intermediaries to introduce products / services to their acquaintances. Unwittingly, loyal customers have become salespeople for the products of the businesses they trust. This will be vital to business enterprises in the 4.0 era, where the power of word-of-mouth marketing is being blown along with the development of the internet. Almost just need to take good care of existing customers, will have more new customers. Treatments may include:
     - Give vouchers to customers when reaching spending levels according to each milestone.
   
     - Email inquires when customers do not buy goods for a long time.
