# Financial Time Series Line Plots

This example demonstrates making line plots using Pandas and a simple Python control loop to load data from different ticker symbols.

```
{
# Python 3
# Python for Finance, 2nd ed., Hilpisch, Ives
# Chapter 8 - Financial Time Series
# Figure 8-1 Financial time series data as line plots
# https://stooq.com/db/h/

%matplotlib inline
import numpy as np
import pandas as pd
from pylab import mpl, plt

plt.style.use('seaborn')
mpl.rcParams['font.family']='serif'

amzn = './data/daily/us/nasdaq stocks/1/amzn.us.txt'
msft = './data/daily/us/nasdaq stocks/2/msft.us.txt'
aapl = './data/daily/us/nasdaq stocks/1/aapl.us.txt'
intc = './data/daily/us/nasdaq stocks/1/intc.us.txt'
gsn = './data/daily/us/nyse stocks/1/gs_n.us.txt'
spy = './data/daily/us/nyse etfs/spy.us.txt'
ivv = './data/daily/us/nyse etfs/ivv.us.txt' #etf simulates SPX index
vxx = './data/daily/us/nyse etfs/vxx.us.txt' #etf simulates VIX index
eur = './data/daily/world/commodities cash/eu.c.txt'
xau = './data/daily/world/currencies/major/xauusd.txt' #stand-in for XAU index
gdx = './data/daily/us/nyse etfs/gdx.us.txt'
gld = './data/daily/us/nyse etfs/gld.us.txt'

filename = [amzn, msft, aapl, intc, gsn, spy, ivv, vxx, eur, xau, gdx, gld]

for i in [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]:
    data = pd.read_csv(filename[i], index_col=2, parse_dates=True)
    closePrice = data[['<TICKER>','<CLOSE>']]
    closePrice2020 = closePrice.loc['2020']
    #print(filename[i])
    closePrice2020.plot(title=filename[i])
}
```