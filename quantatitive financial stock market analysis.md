---
tags: [financial, market, quantative trading, RL, stock market, trading]
title: quantatitive financial stock market analysis
created: 2022-06-09T06:38:29+00:00
modified: 2024-07-19T18:38:26+08:00
---

# quantative financial stock market analysis

gs-quant

---

[pyportfolioopt](https://github.com/robertmartin8/PyPortfoiloOpt)

[amplfinance](https://github.com/ampl/amplpyfinance)

----

造模拟炒股软件 走势跟着大盘 收集用户交易数据

随机假设买卖点 随机假设成交 构成无数虚拟账户交易 或者用某种假设原理拆分不同来源的买卖单

[time-series-transformers](https://huggingface.co/blog/time-series-transformers) huggingface blog

深入浅出Python量化交易 [配套代码](https://www.wqyunpan.com/resourceDetail.html?id=257365&openId=oUgl9wSv5p1X-HH-MnP4jFvTIlHM&qrcodeId=219912&sign=ZTVkOGM1MGRhZDJjLTE2NjE3NjA4MDQyNzQ=)

## 数据来源

`pandas_datareader` by yahoo 是国外股票的数据
`tushare` 国内股票数据


## 模型建立

[open source code for economics modeling in python/julia](https://quantecon.org/)

[pandas pipe](https://sinyi-chou.github.io/python-pandas-pipe/#:~:text=Pipe%20is%20a%20method%20in%20pandas.DataFrame%20capable%20of,can%20be%20combined%20with%20method%20chaining%20without%20nesting.) for streamline processing of real time data

[time series forcast](https://zhuanlan.zhihu.com/p/385094015)

有类似的软件 我下载到windows上面过 (agent based simulation/agent based modeling) called [altreva adaptive modeler]()

[fms](https://pythonhosted.org/fms/)

还原持仓的对象 每一个账户都要详细分析 分析每个账户什么时候买入 卖出 还有不买入 不卖出 观望的那些人 所有人都要还原

## 实盘接口

**tools for high frequency trading** **low latency trading tool**

**高频交易工具** **低延迟交易工具**

要抢涨停板 网络必须要好 下单速度要快

joinquant

[easytrader](https://github.com/shidenggui/easytrader)

[实盘易 支持多个客户端](http://www.iguuu.com/e) 服务端要钱的 sdk都是服务端的client

## tools

[mytt 通达信公式转换器](https://github.com/mpquant/MyTT)

[funcat 通达信公式转换器](https://github.com/cedricporter/funcat)

## models and frameworks

general reinforcement learning:
https://github.com/DLR-RM/stable-baselines3

crypto trading bot, support all crypto trading markets:
https://github.com/freqtrade/freqtrade

qlib by microsoft, quantatitive financial analysis:
https://github.com/microsoft/qlib

reinforcement financial deep learning package:
https://github.com/AI4Finance-Foundation/FinRL

openbb_terminal:
https://github.com/OpenBB-finance/OpenBBTerminal

zipline
https://github.com/quantopian/zipline

pyalgotrade
https://github.com/gbeced/pyalgotrade

quantaxis:
https://github.com/yutiansut/QUANTAXIS

vn.py:
https://github.com/vnpy/vnpy
https://www.vnpy.com/docs/

talib:
https://github.com/mrjbq7/ta-lib
https://www.programcreek.com/python/example/92322/talib.EMA?msclkid=425d0f6cb5dd11ec9da2a03aa72194cd

superalgos:
https://github.com/Superalgos/Superalgos
https://superalgos.org
