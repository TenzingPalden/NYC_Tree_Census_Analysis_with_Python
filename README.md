# NYC Tree Census Analysis with Python

Welcome to the NYC Tree Census Analysis project! This endeavor serves as a practical exercise in Python programming, specifically focusing on harnessing the power of the Plotly package to create visually captivating and aesthetically pleasing visualizations.

The primary objective of this project is to conduct basic analysis of the NYC Tree Census dataset and endeavor to address pertinent questions regarding the dataset.

Through the utilization of Plotly Express, we aim to unravel insights and trends hidden within the dataset, providing a comprehensive understanding of the urban tree landscape in New York City.

Plotly Express is a high-level data visualization library in Python that provides an easy-to-use interface for creating a wide range of interactive plots. 
```Python
import plotly.express as px
```

# Chart of the Top 10 most common trees in NYC
```Python
tree_count = pd.DataFrame(df.value_counts("spc_common").head(50))
tree_count= tree_count.rename(columns= {0: "count"})

fig = px.bar(tree_count[:10], y='count', x=tree_count.index[:10], title= "Chart of the top 10 most common trees in NYC", text_auto='.2s')
fig.update_traces(textfont_size=12, textangle=0, textposition="outside", cliponaxis=False)
fig.show()
```
<img src="https://github.com/TenzingPalden/NYC_tree_census_analysis/assets/85039775/dffda864-7356-499a-834c-5846c7c19680" alt="Image Description" width="1200"/>


# Pie Chart of Count of Trees bt Borough
```Python
count_by_borough = pd.DataFrame(df.value_counts("borough"))
count_by_borough= count_by_borough.rename(columns= { 0: "Count of Trees in Each Borough"})

fig = px.pie(count_by_borough, values='Count of Trees in Each Borough', names=count_by_borough.index,  title='Count of Trees by borough')
fig.show()

```
<img src="https://github.com/TenzingPalden/NYC_tree_census_analysis/assets/85039775/8d58df44-2084-4bf2-948e-3bf8c72cd770" alt="Image Description" width="1200"/>


# Observations recorded per Month acccording to Data set.
```Python
df["created_at"] = pd.to_datetime(df['created_at'])
count_by_month = pd.DataFrame(df.created_at.dt.month.value_counts())
count_by_month= count_by_month.sort_index(ascending=True)
count_by_month= count_by_month.rename(columns= {"created_at" : "Count of trees"})

fig = px.line(count_by_month, x=count_by_month.index, y="Count of trees", title='How many observations were recorded per Month', text="Count of trees")
fig.show()
```
<img src="https://github.com/TenzingPalden/NYC_tree_census_analysis/assets/85039775/36cb42ea-809b-481c-b688-ff3aac0aa73b" alt="Image Description" width="1200"/>


# More Health Bar Charts to understand the trees.
```Python
count_status = pd.DataFrame(df.value_counts("status"))
count_status= count_status.rename(columns= {0: "count"})
fig = px.bar(count_status, y='count', x=count_status.index, title= "Alive, Dead, and Stump Counts", text_auto='.2s')
fig.update_traces(textfont_size=12, textangle=0, textposition="outside", cliponaxis=False)

fig.show()

health_status = pd.DataFrame(df.value_counts("health"))
health_status= health_status.rename(columns= {0: "count"})

fig = px.bar(health_status, y='count', x=health_status.index, title= "Health Status of NYC trees", text_auto='.2s')
fig.update_traces(textfont_size=12, textangle=0, textposition="outside", cliponaxis=False)
fig.show()
```
<img src="https://github.com/TenzingPalden/NYC_tree_census_analysis/assets/85039775/515d0cc1-408b-4ff2-b21a-392ccfb8d29e" alt="Image Description" width="1200"/>
<img src="https://github.com/TenzingPalden/NYC_tree_census_analysis/assets/85039775/208171fc-51ec-4b9f-bd64-6f592c60cf15" alt="Image Description" width="1200"/>

# Conclusion

In this project, I explored the New York City Tree Census dataset using Python and used the Plotly package to create visually appealing and informative visualizations. Through this exercise, I aimed to gain proficiency in basic and intermediate data analysis and visualization techniques.

The top 10 most common trees in NYC were visualized through a bar chart, revealing the prevalence of certain species. A pie chart displayed the distribution of trees across different boroughs, providing a geographical perspective on tree population density. Additionally, a line chart depicted the number of observations recorded per month, indicating patterns in data collection over time.

Furthermore, I delved into the health and status of NYC trees using bar charts, highlighting the distribution of alive, dead, and stump trees and the health status of the overall tree population.

This experience has inspired me to further explore environmental datasets and contribute to projects aimed at promoting sustainability and green initiatives.

# Future Plans
Looking ahead, I aim to delve deeper into the field of environmental data analysis and understand the data collection process as well as the data distribution process.
By continuing to hone my skills in Python and data visualization libraries like Plotly, I want to make meaningful contributions to initiatives aimed at fostering a greener and more sustainable future.
