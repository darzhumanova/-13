#Three lines to make our compiler able to draw:
import sys
import matplotlib
matplotlib.use('Agg')

import pandas as pd
import matplotlib.pyplot as plt
from scipy import stats

education_kz_dataset = pd.read_csv("data.csv", header=0, sep=",")

x = education_kz_dataset["Караганда"]
y = education_kz_dataset["Павлодар"]

slope, intercept, r, p, std_err = stats.linregress(x, y)

def myfunc(x):
 return slope * x + intercept

mymodel = list(map(myfunc, x))

plt.scatter(x, y)
plt.plot(x, mymodel)
plt.ylim(ymin=0, ymax=1500)
plt.xlim(xmin=0, xmax=500)
plt.xlabel("Караганда")
plt.ylabel ("Павлодар")
plt.show()

#Two lines to make our compiler able to draw:
plt.savefig(sys.stdout.buffer)
sys.stdout.flush()
