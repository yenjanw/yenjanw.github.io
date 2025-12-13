+++
date = '2017-04-03T17:35:50+08:00'
draft = false
title = 'Incremental Ta-Lib'
+++

最近在做一些 time-series data 的AI訓練，利用Evolution Strategies(以下簡稱ES)的計算方式，找出數值的規律。在此方面有一個非常好用的套件[Ta-Lib](https://github.com/mrjbq7/ta-lib)這幾乎就是業界的標準套件，應該不用質疑了。但在ES計算中，是利用的feed forward方式來更新模型，一直跑整個程式的數據，因此一直應用到Ta-Lib的function，也因此產生了一些問題。
<!--more-->
## Ta-Lib 慢的原因

其實Ta-Lib一點也不慢，這是用C++寫出來的應用，速度相當的快，只是在程式撰寫原理上，缺少了逐步加入資料的概念，每一次的計算，都要把資料全部加載，然後一次吐給你資料。若是計算SMA之類的資料，這樣的原則是OK的。比如說，計算股市的五分線，Ta-Lib會將資料轉成numpy的型式，然後每五筆資料計算一資平均值。因為是用C++所寫的，所以速度比numpy計算還快。

### Example numpy vs talib

```python
import numpy as np
import talib as ta 
tmp_data = np.random.randint(5)
%timeit np.mean(tmp_data)
%timeit talib.SMA(tmp_data)
```

13.8 µs ± 7.73 µs per loop (mean ± std. dev. of 7 runs, 100000 loops each)  
4.1 µs ± 1.9 µs per loop (mean ± std. dev. of 7 runs, 1000000 loops each)  

這數值是基於Intel 4790K的CPU所計算出來，可以看到numpy比talib慢了大約三倍。這呼應了talib其實是很快的，但我為何又說talib慢呢?  
因為AI訓練時，time series資料是序列進來的，以下再做個範例。

### Example talib.MAMA

```python
df = pd.read_csv('dataset/2020_DN_MTX_5s.csv') # data 來自5秒小台指
df['date'] = pd.to_datetime(
            df['date'],
            format='%Y-%m-%d %H:%M:%S',
            infer_datetime_format=True, errors='ignore')
df_np = np.array(df) # 為了加速indexing，將資料轉為numpy

import talib
from time import time
start = time()
mama = []
fema = [] 
for i in range(1000000):
    a, b = talib.MAMA(df_np[i:i+200, 4].astype(float)) # mama運算通常要到第兩百筆數值才會穩定
    mama.append(a)
    fema.append(b)
print(time() - start)
```

26.702403783798218
這範例是計算1000000筆五秒小台指走勢的MAMA值，花了26.7秒。
在ES計算時，假如一個迭代就是一百萬筆，那一個population就是計算超過26.7秒才會結束，若有20個population，那一個迭代就要將近10分鐘才算完，天啊!!!

## 解決方案

我試過用numpy來寫一個迭加運算的方式，速度也是慘不人睹，畢竟python在高速運算上還是有其極限。這時參考到Ta-Lib是用C++來改寫的，我也用了cython來改寫一個自己可以用的套件，名為tail(Technical Analysis Incremental Library)，已放上GitHub中，連結放於文末[^1]。
來做個簡單測試:

### Example tail.MAMA

```python
# 數值同於上面的五秒小台指
from util.indicators_C import MAMA
from time import time
start = time()
MAMA = MAMA()
mama = []
fema = []
for i in range(1000000):
    a, b = MAMA.add_one(df_np[i, 4].astype(float))
    mama.append(a)
    fema.append(b)
print(time() - start)
```

8.38700008392334  
同樣一百萬筆資料，速度提升三倍有餘，意味著原本10分鐘算完一次迭代，現在只要三分鐘就可以結束，也代表一小時原本只有六次迭代，現在變成近二十次迭代，若是加上平行運算，速度可以再往上提升。

## tail 可運算的indicators

1. MAMA
1. HMA
1. KAMA
1. ADX
1. STOCH(KD)
1. RSI
1. SAR
1. EMA
1. MACD
1. ICHMOKU
1. LLT
1. WMA  

以上是暫時有用到的指標，主要應用於數值需要參考前值的計算，比如EMA就是一個例子，可以Google找到EMA每次計算結果不同的原因，在此就不多作綴述。若是上述indicator不知是啥，那本篇文章應該沒有幫助到你。  

## tail 安裝方式

在GitHub中已有簡單說明，但還是強調本機要先裝好cython，利用cython重新編譯成可執行的機碼，這樣才不會出錯。

## tail 的未來

還沒想過是否要繼續發展這套件，畢竟只是我在AI訓練路上的一個小旁枝，只期望對大家是有幫助的而已，若是有人敲碗需要其他的指標，我可以花點時間多加進去。

## 補充

其實GitHub中有另外一個專案[Talipp](https://github.com/nardew/talipp)我覺得也很不錯，可惜我自己的測試上，因為是用純python所撰寫，速度上真的不行，不是作者的錯，只是python速度慢的問題。所以我才另外寫一個簡單的tail來自己使用。  

[^1]: [tail GitHub位置](https://github.com/yenjanw/tail)
