Khi mới nhận được một dataset, việc đầu tiên cần phải làm không phải là nhảy vào chạy luôn mô hình tính toán hoặc chạy model. Việc đầu tiên cần làm là quan sát một cách tổng thể từng sự vật, sự việc.

Để từ đó chúng ta biết được về đối tượng data mà chúng ta đang làm việc cùng. 


### 1. EDA là gì?
''Exploratory data analysis (EDA) is used by data scientists to analyze and investigate data sets and summarize their main characteristics, often employing data visualization methods. It helps determine how best to manipulate data sources to get the answers you need, making it easier for data scientists to discover patterns, spot anomalies, test a hypothesis, or check assumptions.'' - IBM

Định nghĩa này có các bước như sau:
- Phân tích data sets và tóm tắt các đặc điểm chính của những data sets này, thường là dùng các phương pháp visualization
- Mục đích: Giúp xác định cách tốt nhất để làm việc với data sets và có được câu trả lời mà mình muốn. Đồng thời giúp data scientists xác định các patterns trong data, spot những điểm bất thường, test hypothesis hoặc kiểm chứng các assumptions

### 2. Các loại EDA
Đối với tabular data. Có thể phân chia EDA theo 1 graph dựa trên 2 cặp biến số: Univariate - Multivariate và Graphical - Nongraphical. Từ đó, chúng ta có 4 types EDA như sau:
- **Univariate nongraphical**: Chỉ phân tích 1 feature duy nhất, và tìm hiểu về patterns và mô tả data.
- **Univariate graphical**: Phần đồ họa/ hình ảnh sẽ giúp hiện ra những điểm mà nongraphical không làm được. Những đồ họa thường dùng là: Stem-and-leaf plots, Histograms, Box plots
- **Multivariate nongraphical**: Thể hiện relationship giữa 2 hoặc nhiều variables với nhau. Phương pháp sử dụng thường là cross-tabulation
- **Multivariate graphical**: Dùng đồ họa để thể hiện relationship giữa các variables với nhau. Phương pháp sử dụng thường là bar plot, bar chart, hoặc heatmap

### 3. Các bước thực hiện EDA:
#### 1. EDA Framework
1. Describe of data
2. Explore data distribution
3. Understand relations between variables
4. Notice unusual/ unexpected situations (outliers)
5. Place data into groups
6. Notice unexpected patterns with groups
7. Notice group differences

#### 2. Detailed steps
1. **Describe data**: 
	- Purpose: You need to look at the overall dataset, để có thể get được basic understanding về dataset này. 
	- Code:
	```python
	pd.describe()
	```

2. **Explore data distribution:**
	1. **Check mean và median**
	- Purpose: Sau khi đã check data toàn cảnh rồi thì có thể check từng data riêng lẻ, đặc biệt là target features
	- Code:
	```python
	pd.mean()
	pd.median()
	```
	Ngoài ra, có thể check thêm bằng graph. Cụ thể là
	- Histogram:
	```python
	plt.hist(df["feature"])
	plt.xlabel("Name of feature")
	plt.title("Name of the graph");
	```
	- Boxplot:
```python
import matplotlib.pyplot as plt

fig, ax = plt.subplots(figsize=(15, 6))

df["__"].plot(kind="box", vert=False, title="__", ax=ax)
```

3. **Measuring variance and range**
	- Purpose: Tính độ spread của data feature
	- Code:
		```python
		df.std()
		```

		```python
		import statistics
		sample = [] # feature data
		print(statistics.variance(sample))
		```

4. **Checking percentiles of data**
	- Code:
		```python
		df.quantile([0, .25, .5, .75, 1])
		```

5. **Measures of normality**
	- Skewness
	- Kurtosis

6. **Converting into categorical data**
	- Purpose: Chia numerical data thành các bins, sau đó dán nhãn. Ví dụ: Từ một đống data kiểu như 2008, 2009, 2010, 2011. Có thể chia thành nhóm "2001-2010"; "2011 - 2020"
	- Code:
		- `df.cut`: Cut theo một mức nào đó
		- `df.qcut`: Cut theo percentile

7. Understand frequency (for categorical data)
	- `df.value_counts`
