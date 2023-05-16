
import numpy as np                 
import pandas as pd                
import matplotlib.pyplot as plt
import seaborn as sns
path ='cost-of-living.csv'
data=pd.read_csv(path)
data=data.dropna()
data
data.info()
new_data=['South Korea','Vietnam','Russia','Mexico','Malaysia','Italy','United States','Hong Kong','Singapore','Taiwan','Cuba','South Africa','Brazil','Japan']
new_df=data[data['country'].isin(new_data)]
cities=new_df['country'].unique()
x11=new_df.groupby('country').mean()['x11']
x8=new_df.groupby('country').mean()['x8']
x33=new_df.groupby('country').mean()['x33']
x15=new_df.groupby('country').mean()['x15']
x27=new_df.groupby('country').mean()['x27']
x38=new_df.groupby('country').mean()['x38']
x42=new_df.groupby('country').mean()['x42']
x26=new_df.groupby('country').mean()['x26']
x44=new_df.groupby('country').mean()['x44']
x45=new_df.groupby('country').mean()['x45']
x46=new_df.groupby('country').mean()['x46']
x47=new_df.groupby('country').mean()['x47']
x38=new_df.groupby('country').mean()['x38']

print(cities)
print(f'Gạo {x11}\n')
print(f'nước {x8}\n')
print(f'Gas {x33}\n')
print(f'Thịt {x15}\n')
print(f'Thuốc lá {x27}\n')
print(f'Internet {x38}\n')
print(f'Preschool 1year/kid(trường mầm non 1 tháng/1 đứa trẻ) {x42}\n')
print(f'Preschool 1year/kid(trường trung học 1năm/1 đứa trẻ) {x43}\n')

print(f'Quần áo {x45}')
print(f'{x44}')
x1=range(len(cities))
print(x1)

cities=[country for country,x11 in x11.items()]
plt.barh(y=cities, width=x8, height=0.6, color="gold", label="Water")
plt.barh(y=cities, width=x11, height=0.6, color="green", left=x8,label="Rice")
plt.barh(y=cities, width=x15, height=0.6, color="lightcoral", left=x11,label="Beef")
plt.barh(y=cities, width=x33, height=0.6, color="lightblue", left=x11,label="Gas")
plt.barh(y=cities, width=x27, height=0.6, color="rebeccapurple",left=x11, label="Thuốc lá")
plt.barh(y=cities, width=x38, height=0.6, color="darkslategray", left=x15,label="Internet")
plt.barh(y=cities, width=x26, height=0.6, color="mediumslateblue", left=x11,label="Beer")
plt.barh(y=cities, width=x36, height=0.6, color="olivedrab",left=x38,label="Basic(Electricity,Heating,Cooling,Water,Garbage(USD))")

plt.yticks(cities)
plt.legend(loc='center right')
plt.show()
cities=[country for country,x11 in x11.items()]
plt.barh(y=cities, width=x43, height=0.6, color="brown",label="primary shcool 1 year/kid")


plt.yticks(cities)
plt.legend(loc='lower right')
plt.show()
cities=[country for country,x11 in x11.items()]
plt.barh(y=cities, width=x45, height=0.6, color="brown",label="Quần áo")
plt.barh(y=cities, width=x46, height=0.6, color="olivedrab",left=x45,label="Giày thể thao(Nike)")


plt.yticks(cities)
plt.legend(loc='lower right')
plt.show()
x=x11
y=x8
plt.scatter(x, y)

x1=x44
y1=x45
plt.scatter(x1, y2)

x2=x33
y2=x15
plt.scatter(x2, y2)

x3=x27
y3=x38
plt.scatter(x3, y3)


plt.show()
data1=data.groupby(['country']).mean()
data1=data.reset_index()
data1
data1=data.groupby(['country']).mean()
data1.drop('Unnamed: 0',axis=1,inplace=True)
data1.drop('data_quality',axis=1,inplace=True)
data1.groupby('country').max()
corr = data1.corr()

mask = np.triu(np.ones_like(corr, dtype=bool))

f, ax = plt.subplots(figsize=(11, 9))

cmap = sns.diverging_palette(230, 20, as_cmap=True)

sns.heatmap(corr, mask=mask, cmap=cmap, vmax=.3, center=0,
            square=True, linewidths=.5, cbar_kws={"shrink": .5})df_percent = data['city'].to_frame()
for i in range(1, 54):
    df_percent[f'%x{i}'] =  data[f'x{i}'] / data['x54'] * 100
df_percent.head(20)

rich = df_percent[df_percent['%x3'] < 0.2]
rich['country'].unique()
poor = df_percent[df_percent['%x3'] > 15]
poor
