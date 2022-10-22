---
title: 股票数据源 tick级别数据源 逐笔交易
created: '2022-10-22T11:22:21.924Z'
modified: '2022-10-22T13:01:16.566Z'
---

# 股票数据源 tick级别数据源 逐笔交易

## 交易接口

[tdxtradeserver](https://github.com/corefan/TdxTradeServer)

## 数据来源

逐笔数据是计算涨速的关键因素

[quantaxis]() secretely using pytdx and tdxtradeserver as backends

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

[pytdx2](https://github.com/liewhite/pytdx2)

[mootdx](https://github.com/TianShengBingFeiNiuRen/moo-tdx-api/tree/master/Lib/site-packages/mootdx/financial) actually using pytdx as backend

计算涨速等数据

[pysnowball](https://github.com/uname-yang/pysnowball)雪球数据源

chromedriver based [xueqiu api](https://github.com/1dot75cm/xueqiu)

[获取雪球cookie](https://blog.crackcreed.com/diy-xue-qiu-app-shu-ju-api/)

[雪球tick级别数据获取](https://github.com/easyQuant/trade_bundle/blob/master/index.py)

[zipline_chstock](https://github.com/fangshi1991/zipline_chstock) 本地化zipline，并对其进行部分加工，适用于国内 day,minute 和tick数据的回测

[新浪财经api](https://github.com/knotgd/option_data/blob/55dad688b0e351b7aae43919a2beac50c536aa3a/core/constant.py)
