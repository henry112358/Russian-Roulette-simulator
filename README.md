
get_ipython().magic(u'pylab inline')
import matplotlib.pyplot as plt 
import numpy as np

n  = int(raw_input("n=?"))
t = np.arange(n)
result = [1,-1]

x=np.random.choice(result,n,p=[0.4864,0.5136])  
ts=np.cumsum(x)

mean = -0.0272
sigma = (0.4864*0.5136)**0.5 
sigmat= (t*0.4864*0.5136)**0.5 


#plot the range of net win/loss at the 95% confidence interval 
plt.fill_between(t, (t*0.4864-2*sigmat)*1 + (t-(t*0.4864-2*sigmat))*-1, (t*0.4864+2*sigmat)*1 + (t-(t*0.4864+2*sigmat))*-1, facecolor='yellow', alpha=0.4)
 
plt.title("Russian Roulette simulator \n with a range of net win/loss  at the 95% confidence interval \n")
plt.xlabel('times')  
plt.ylabel('net win/loss')
plt.plot(ts)
plt.plot(t, mean*t, lw=1, label='population mean', color='black', ls='--')
