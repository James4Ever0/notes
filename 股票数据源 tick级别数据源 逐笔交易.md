---
title: 股票数据源 tick级别数据源 逐笔交易
created: '2022-10-22T11:22:21.924Z'
modified: '2022-11-05T15:29:35.253Z'
---

# 股票数据源 tick级别数据源 逐笔交易

和股票有关的程序必须运行在服务器上面 要有ecc 网速要快

## 交易接口

[现在哪些券商的TradeX.dll接口还能用](https://www.55188.com/thread-8939286-1-1.html) 需要注册论坛账号 达到要求才能浏览内容

[trade.dll tradex.dll](https://github.com/James4Ever0/Order9)

[tradex.dll header file](https://github.com/296083197/ts/blob/master/TradeX-B/TradeXDemo-B/TradeX.h)

[bqtradex](https://github.com/sunwind/BQTradeX) A simple tradex api mock dll, for easily internal debug your app

[Quantaxis](https://github.com/yutiansut/QUANTAXIS)

[tdxtradeserver](https://github.com/corefan/TdxTradeServer)

[tradex-api](https://github.com/southtop/TradeX-API)

[tdxapi2](https://github.com/fswzb/tdxapi2)

[alphaquant](https://github.com/fswzb/alphaquant)

## 数据来源

逐笔数据是计算涨速的关键因素

[ashare](https://github.com/fswzb/Ashare)

[quantaxis](https://github.com/yutiansut/QUANTAXIS) secretely using pytdx and tdxtradeserver as backends

[akshare](https://github.com/akfamily/akshare)

获取涨速

```python
import akshare as ak

stock_zh_a_spot_em_df = ak.stock_zh_a_spot_em()
print(stock_zh_a_spot_em_df)
```

[qstock]()

[efinance](https://efinance.readthedocs.io/en/latest/index.html)

[baostock](http://baostock.com/baostock/index.php/A%E8%82%A1K%E7%BA%BF%E6%95%B0%E6%8D%AE)

[pytdx](https://gitee.com/better319/pytdx/) and [docs](https://rainx.gitbooks.io/pytdx/content/pytdx_hq.html), must connect to tdx server before operate

[pytdx2](https://github.com/liewhite/pytdx2) fixed some problems

[mootdx](https://github.com/TianShengBingFeiNiuRen/moo-tdx-api/tree/master/Lib/site-packages/mootdx/financial) actually using pytdx as backend

[abquant-data](https://github.com/yssource/abquant-data/blob/develop/abquant/data/tdx_api.py) using pytdx as backend

计算涨速等数据

[pysnowball](https://github.com/uname-yang/pysnowball)雪球数据源

chromedriver based [xueqiu api](https://github.com/1dot75cm/xueqiu)

[获取雪球cookie](https://blog.crackcreed.com/diy-xue-qiu-app-shu-ju-api/)

[雪球tick级别数据获取](https://github.com/easyQuant/trade_bundle/blob/master/index.py)

[zipline_chstock](https://github.com/fangshi1991/zipline_chstock) 本地化zipline，并对其进行部分加工，适用于国内 day,minute 和tick数据的回测

[新浪财经api](https://github.com/knotgd/option_data/blob/55dad688b0e351b7aae43919a2beac50c536aa3a/core/constant.py)
