# project-1

import pandas as pd
import numpy as np
import matplotlib.pylot as plt
import os
import statistics as st
from scipy.stats import norm
import scipy.stats as st



data1=pd.read_csv("C:\\Users\\TONGAONKAR.1921437\\TCS.csv")
data1
data1.head(5)


# Calculating the logarithmic returns of the stock
return_s=[]
n=len(data1['Close_Price'])
for i in range(0,n-1):
    x=np.log(data1.Close_Price[i+1]/data1.Close_Price[i])
    return_s.append(x)
return_s
s=len(return_s)
return1.mean()

# Predicting the value of the stock for the next day
return1=np.array(return_s)
data1['Return']=np.log(data1['Close_Price'])-np.log(data1['Close_Price'])

standard_dv=st.stdev(return_s)
standard_dv

value=(standard_dv*st.norm.ppf(0.95))
value
last_v1=data1["Close_Price"].tail(1)
pre_vl=last_v1*value
low_vl=last_v1-pre_vl
High_vl=last_v1+pre_vl

print("High value will be:",High_vl)
print("Low value will be:",low_vl)


# To find the probability  that whether the TCS stock will reach 2300
riseinprice=2300-last_v1       # 2300- last close in price
percentchange=(riseinprice)/last_v1
percentchange

z_score=(percentchange-return1.mean())/standard_dv
z_score

norm_dist=norm.cdf(z_score)

prob_price=1-norm_dist
prob_price
abs(prob_price)

