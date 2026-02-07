### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 07/02/2026
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program:
```python
cluster={"Young":(df['Age']<=30),"Middle":((df['Age']>30)&(df['Age']<=50)),"Old": (df['Age']>50)}
count=[]
for group,condition in cluster.items():
    visitors=df[condition]
    count.append(len(visitors))
    print(f"The visitors on {group} age are")
    print(visitors)
    print("count=",len(visitors))

from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
df1=df['Age']
df2=df['Income']
df3=pd.concat([df1,df2],axis=1)
s=StandardScaler()
newdf=s.fit_transform(df3)
k=KMeans(n_clusters=4,random_state=55)
df3['cluster']=k.fit_predict(newdf)
df3

```
### Output:

<img width="797" height="808" alt="Screenshot 2026-02-07 142622" src="https://github.com/user-attachments/assets/d40094f6-5a2f-446a-bd00-3639a2f1679b" />

<img width="505" height="808" alt="Screenshot 2026-02-07 144233" src="https://github.com/user-attachments/assets/aa594b96-fc99-4e6d-9106-0da1fbc18d3c" />



### Visualization:
```python


import matplotlib.pyplot as plt
plt.figure(figsize=(8, 6))
plt.scatter(x=df3['Age'],y=df3['Income'],c=df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Income')
plt.title("Visitor Distribution in Different Clusters")
plt.show()

plt.figure(figsize=(8, 6))
plt.bar(age_group_labels, visitor_counts, color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()
```
### Output:
<img width="1141" height="720" alt="Screenshot 2026-02-07 142315" src="https://github.com/user-attachments/assets/70f8e65f-ca6d-4a2e-b4ff-1909a86dc730" />

<img width="1291" height="694" alt="Screenshot 2026-02-07 144336" src="https://github.com/user-attachments/assets/2ede4fd5-a530-487b-a83a-61b285405c59" />


### Result:
Thus, Cluster and Visitor Segmentation for Navigation patterns in Python is implemented successfully.
