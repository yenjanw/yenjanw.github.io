+++
title = '手把手教你製作Trading Gym Env'
date = '2021-02-08'
tags = ["AI", "Stocks", "OpenAI", "Gym"]
draft = false
ShowToc = true
+++

網路上已經有很多AI的訓練框架，最有名的應該就是OpenAI的Stable Baselines系列，也有用PyTorch所寫的Stalbe Baselines3可以直接拿來應用，對於初入強化學習AI訓練的初哥而言算是相當簡易學習的入門磚。但對於有志於要作股市數值分析AI訓練的人而言，OpenAI提供的gym都只有用來玩玩小蜜蜂打磚塊的遊戲應用而已，並沒有如股市一樣的交易遊樂場，可以提供給AI玩樂(?!)
本篇就初步介紹如何製作個人的Trading Gym。
<!--more-->

## 強化學習(Reinforcement Learning，RL)的基本概念

這就要先從強化學習的概念說起
![RL](ReinforcementLearning.jpg)
其實就只是agent與Environment(以下簡稱env)之間的交互作用而已，env提供Observation(觀察值，以下簡稱obs)，agent根據obs計算出action給env，env再提供reward與obs給Agent，進入無限循環。
用流程步驟來看:

1. env產出obs給agent
2. agent產出action給env
3. env同時產出obs、reward給agent
更多的資訊，建議可以參考李弘毅老師的youtube，將說明的更清楚。

## Gym的基本概念

接下來從Gym官網的Example Code了解

```python
import gym
env = gym.make("CartPole-v1")
observation = env.reset()
for _ in range(1000):
    env.render()
    action = env.action_space.sample() # your agent here (this takes random actions)
    observation, reward, done, info = env.step(action)
    if done:
      observation = env.reset()
    env.close()
```

從程式解讀，gym可以提供幾個主要的功能
1. 第一個obs是從env.reset()產出
2. 剛產出的obs餵給agent，產出action
3. action餵給env.step()產出obs、reward、done、info，此中done == True是遊戲結束的訊號，用來告訴agent已經Game Over了。info是用來提供訊息給外部的管道，一般都是用dict方式呈現。

gym是不是與強化學習流程相同啊?這流程是gym仿RL流程的程式寫法，這是制式的規則，幾乎所有的RL訓練都可依這準則去運算，所以只要仿造gym內部的構造，在外部使用時只要呼叫這幾個function就可以做各種的強化學習訓練了。

## gym內部架構

```python
import gym
env = gym.make('CartPole-v0')
env.reset()
for _ in range(1000):
    env.render()
    env.step(env.action_space.sample()) # take a random action
env.close()
```

從Example Code了解:

1. environment
    - reset: 用來重置遊戲。
    - render: 用來畫出或呈現遊戲畫面，以股市為例，就是畫出走勢線圖。
    - step: 用來輸入action，是agent與env的交互作用重要的函數。
2. Observations
    - step輸入action之後會產出obs、reward、done、info
    - obs: 下一步的環境觀察值
    - reward: action之後的獎勵值
    - done: 遊戲是否結束。當等於True時，代表已經Game Over。
    - info: env傳遞出來的資訊，要用dict的結構呈現，一般而言多用render來呈現agent與env之間的互動，若有必要，可另外要匯出的數值。
3. Spaces
    這部份是要給agent知道，他要運算數值的範圍。包含action_space與observation_space。
    - action_space: 有discrete與continues(在stable-baselines中稱為box)兩種。前程為離散，後者為連續。
    - observation_space: 環境值的結構。
這部份在應用時會說明用法。

## 打造Trading Gym

第一步: 定義環境

```python
import gym
import pandas as pd
import numpy as np
from gym import spaces

BUY = 0
SELL = 1
HOLD = 2

class StockTradingEnv(gym.Env):
    metadata = {'render.modes': ['human', 'system', 'none']}
    def __init__(self, df, initial_balance=10000, tax=0.00002, commission=100):
        super(StockTradingEnv, self).__init__()
        self.initial_balance = initial_balance
        self.balance = self.initial_balance
        self.tax = tax
        self.commission = commission
        self.current_step = 1
        self.df = df.fillna(method='ffill').reset_index()
        self.obs_shape = (1, 5)
        self.action_space = spaces.Discrete(3)
        self.observation_space = spaces.Box(low=0, high=100, shape=self.obs_shape, dtype=np.float16)
```

1. 首先載入gym套件(癈話!)
2. 交易很簡單，不過就是買、賣、與等待(又一個癈話!)。先宣告三個常數，用來代表這三個action。
3. 定義一個繼承自gym.Env的class
4. inital_balance是初始資金，而手中的現金也等同初始資金。
5. tax是交易稅。commission是手續費。一般的機器學習，初始時習慣只看漲跌，並沒有計算交易稅與手續費，常常當真正應用時，一直虧到脫褲，就是因為沒有在初始訓練時，就將交易成本的因素算入。我的概念是，沒有包含交易成本，只單看漲跌的模型是沒有意義的模型，畢竟與現實狀況不合，根本只是浪費電去訓練一個沒有的東西。在此先以台指期貨的稅為萬分之二、手續費為100元為舉例，當要換成其他交易標的時，記得要修改哦!
6. current_step是定義現在運算到第幾步，於index數值用。
7. 我的架構是從外部傳入一個dataframe，就是指數的資料表，所以先將df中的空值再dropna一次，若值為空，就取前值代替(“ffill”)，避免運算過程出錯。因為有可能數值被drop掉，所以順便重設index。
8. obs_shape是之後產出obs值的shape，以stable-baselines而言，obs要用array的格式，所以先將shape設好，之後reshape為這個形狀。
9. acdtion_space的語法如程式碼，在此先用離散的方式運算，結果只有三種可能(BUY、SELL、HOLD)。
10. observation_space定義了觀察值的範圍，語法如範例。

## 第二步: 定義環境值obs

```python
def next_observation(self):
    obs = [0] * 5
    obs[0] = self.df.iloc[self.current_step]['open'] - 
                self.df.iloc[self.current_step - 1]['open']
    obs[1] = self.df.iloc[self.current_step]['high'] - 
                self.df.iloc[self.current_step - 1]['high']
    obs[2] = self.df.iloc[self.current_step]['low'] - 
                self.df.iloc[self.current_step - 1]['low']
    obs[3] = self.df.iloc[self.current_step]['clos'] - 
                self.df.iloc[self.current_step - 1]['close']
    obs[4] = self.df.iloc[self.current_step]['volume'] - 
                self.df.iloc[self.current_step - 1]['volume'] 
    return np.reshape(obs, self.obs_shape)
```

這一步是一門學問，股市的數值真的多如牛毛，我在此只舉例OHLC加上Volume的變化量去做RL訓練。其他很多的文章有在介紹這部份，其實有幾個準則可以依循。

1. 數值未來是會重覆出現的，這意思是若訓練是用真實數值，那未來創新高或是創新低時，在訓練值之外，那就超出AI能處理的範圍了。
2. 新數值產生時，是可以直接套用的。其他文章中有用上minmax的方式去限制數值的最高與最低值，等同第一點一樣，當創新高或新低時，模型也直接宣告無效。訓練時的最高與最低，不代表真實交易中的最高最低。
3. 數值區間要在前項observation_space的範圍之內。
4. 數值不要太過集中或分散，最好是常態分佈。

## 第三步: 定義執行行為

```python
def take_action(self, action):
    self.gain = 0
    if action == 0 and self.held != 0:
        self.mean = self.df.iloc[self.current_step]['close']
        cost = price * self.tax + self.commission 
        self.balance -= cost
    elif action == 1:
        self.gain = self.df.iloc[self.current_step]['close'] - self.mean - self.df.iloc[self.current_step]['close
    ] * self.tax - self.commission)
    self.balance += self.gain
    else:
        pass
```

這環結定義了交易策略，只示範了買賣一次，一次一單位，只做單方向的作法。買的時候是當時間的成交價，但其實這是有問題的(?)，原因我會之後再詳述，現在只是範例作法，不對每一個細項探討，畢竟本篇文章是定位在初入門的階段。應用在股票有股票的作法，應用在期貨有期貨的做法，每一種的交易策略都有不同。

## 第四步: 定義遊戲結束

```python
def done(self):
    if self.current_step == len(self.df):
        return True
```

當輸入的樣本跑到最後一筆時，就遊戲結束。

## 第五步: 重新開始(數值初始化)

```python
def reset(self):
    self.current_step = 1
    self.initial_balance = 10000
    self.mean = 0
    self.balance = self.initial_balance 
    return self.next_observation
```

遊戲重置，把變動的數值歸零。對交易而言，就是把初始資金回復，並返回第一個觀察值。

## 第六步: 定義遊戲步驟

```python
def step(self, action):
    self.take_action(action)
    self.current_step += 1
    return self.next_ovservation(), self.gain, self.done(), []
```

執行步驟就是執行agent所交付的action，並返回obs、reward、done、info。

## 第七步: 把遊戲render出來

```python
def render(self):
    print('step: ' + self.current_step)
    print('balance: ' + self.balance)
    print('current_price: ' + self.df.iloc[self.current_step]['close'])
    print('bought_price: ' + self.mean)
```

## 第八步: 遊戲關閉

```python
def close(self):
    pass
```

有時，遊戲關閉要把一些程序結束，或是關閉一些正在執行的步驟，都可以放在這裡。因為範例中並沒有用什麼平行運算的function，也就沒東西可執行，所以放個pass就可以了。

## 後話

以上算是簡略到不能再簡略的說明自己打造Trading Gym的方法，其實每一個環結都有很多東西可以說明，畢竟RL是一門易入難深的學問，水很深的，坑也很多。若想要更進一步討論，幾乎都可以成為獨立的一篇文章用以討論。
我只能算是半桶水，既不是資訊科班出身，也不從事證券交易的事業，我就當純學術研究在把玩RL而已。但也相信因為我這樣背景，也講不出只有資深的programmer能說出的話，理論上可以更符合初學者能聽得懂的語言來溝通。
