# NYC Tree Census Analysis with Python

This project was an exercise in python to practice and utilize the Plotly package for more beautiful and aesthetically pleasing visualizations. 

The main goal of this was to do some basic analysis of the data set and to try to answer some questions about the data.

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
<img src="https://github.com/TenzingPalden/NYC_tree_census_analysis/assets/85039775/dffda864-7356-499a-834c-5846c7c19680" alt="Image Description" width="900"/>


# Pie Chart of Count of Trees bt Borough
```Python
count_by_borough = pd.DataFrame(df.value_counts("borough"))
count_by_borough= count_by_borough.rename(columns= { 0: "Count of Trees in Each Borough"})

fig = px.pie(count_by_borough, values='Count of Trees in Each Borough', names=count_by_borough.index,  title='Count of Trees by borough')
fig.show()

```
<img src="https://github.com/TenzingPalden/NYC_tree_census_analysis/assets/85039775/8d58df44-2084-4bf2-948e-3bf8c72cd770" alt="Image Description" width="900"/>


# Observations recorded per Month acccording to Data set.
```Python
df["created_at"] = pd.to_datetime(df['created_at'])
count_by_month = pd.DataFrame(df.created_at.dt.month.value_counts())
count_by_month= count_by_month.sort_index(ascending=True)
count_by_month= count_by_month.rename(columns= {"created_at" : "Count of trees"})

fig = px.line(count_by_month, x=count_by_month.index, y="Count of trees", title='How many observations were recorded per Month', text="Count of trees")
fig.show()
```
<img src="https://github.com/TenzingPalden/NYC_tree_census_analysis/assets/85039775/36cb42ea-809b-481c-b688-ff3aac0aa73b" alt="Image Description" width="900"/>


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
<img src="https://github.com/TenzingPalden/NYC_tree_census_analysis/assets/85039775/515d0cc1-408b-4ff2-b21a-392ccfb8d29e" alt="Image Description" width="900"/>
<img src="https://github.com/TenzingPalden/NYC_tree_census_analysis/assets/85039775/208171fc-51ec-4b9f-bd64-6f592c60cf15" alt="Image Description" width="900"/>


