### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 07-02-2026
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
```
import pandas as pd
df=pd.read_csv('/content/clustervisitor.csv')
df
```
```
cluster={"Young":(df['Age']<=30),"Middle":(df['Age']>30)&(df['Age']<=50),"Old":(df['Age']>50)}
for group,condition in cluster.items():
  visitors=df[condition]
  print(f"The visitors on {group} are :")
  print(visitors)
  print(len(visitors))
  print("count=",len(visitors))
```
```
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
df1=df['Age']
df2=df['Income']
df3=pd.concat([df1,df2],axis=1)
s=StandardScaler()
newdf=s.fit_transform(df3)
k=KMeans(n_clusters=3,random_state=42)
df3['cluster']=k.fit_predict(newdf)
df3
```
### Output:

<img width="494" height="781" alt="image" src="https://github.com/user-attachments/assets/294eb7ff-b5cc-4c99-b01f-bb662cf9b426" />

<img width="417" height="940" alt="image" src="https://github.com/user-attachments/assets/0b23d503-9151-4a92-8274-696aba09aa23" />


### Visualization:
```
import matplotlib.pyplot as plt
counts = [len(df[cluster[label]]) for label in ['Young', 'Middle', 'Old']]
age_group_labels = ['Young', 'Middle', 'Old']

plt.figure(figsize=(8, 6))
plt.bar(age_group_labels, counts, color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()
```
```


import matplotlib.pyplot as plt
plt.figure(figsize=(10, 6))
scatter = plt.scatter(df3['Age'], df3['Income'], c=df3['cluster'], cmap='viridis', s=100, edgecolors='k')
plt.xlabel('Age ')
plt.ylabel('Income')
plt.title('Visitor Distribution Across Age Group')
plt.colorbar(scatter, label='Cluster')
plt.show()
```

### Output:

<img width="700" height="547" alt="image" src="https://github.com/user-attachments/assets/c6116c98-ec87-4aff-b24e-29bf062f79f3" />

<img width="843" height="547" alt="image" src="https://github.com/user-attachments/assets/0d6c3ae9-27fb-403c-abee-294a2e848cea" />


### Result:

Thus, cluster and Visitor Segmentation for Navigation patterns have been implemented successfully.

