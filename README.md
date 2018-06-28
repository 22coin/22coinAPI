# 22coinAPI

## 1.获取市场配置数据
描述：获取已开启的市场信息，包括价格、数量小数点位数<br>
请求：http://22coin.com/api/getConfiguration.html<br>
示例：
http://22coin.com/api/getConfiguration.html<br>
### Response
{
    "BTC": [
        {
            "DOGE": {
                "priceScale": 8,
                "amountScale": 4
            }
        },
        {
            "LTC": {
                "priceScale": 8,
                "amountScale": 4
            }
        },
   }
返回值说明:
    "法币名称": [
        {
            "交易币名称": {
                "价格小数位数": 8,
                "价格小数位数": 4
            }
        }
    ],
amountScale:数量小数位数
priceScale：价格小数位数
参数描述:获取到22coin中所有币种的数量的最小位数和价格的最小位数

## 2.行情
描述：获取22coin最新市场行情数据
请求：http://22coin.com/api/getQuotation.html
示例：
### Request
GET http://22coin.com/api/getQuotation.html?market=btc_eth
### Response
{
    "high": 0.00028,
    "low": 0.00026,
    "price": 0.00028,
    "total": 2,
    "value": 0.00054,
    "sellFirst": 0.00028,
    "buyFirst": 0,
    "date": 1527921917429
}
返回值说明:
high : 最高价
low : 最低价
buyFirst: 买一价
sellFirst: 卖一价
price: 最新成交价
total: 成交量(最近的24小时)
Date: 调用时间戳
参数描述:
market:	是币种类型的名称，当前系统拥有的币种类型为：BTC，DOGE，LTC，KNC，ETH，USDT
法币类型有：BTC，ETH，USDT
Market字段为:  法币_交易币 eg:BTC_DOGE
## 3.市场深度
描述：获取市场深度
请求：http://22coin.com/Api/Depth.html
示例：
### Request
GET http://www.22coin.com/Api/Depth.html?market=eth_btc&level=20
### Response
{
   "sells": [
        {
            "id": 1,
            "price": 0.084805,
            "amount": 7.335
        }......
],
    "buys": [
        {
            "id": 1,
            "price": 0.084803,
            "amount": 0.69
        }......
        ]   
}
返回值说明:
sells : 卖方深度
buys : 买方深度
id : 返回数据id
price: 深度价格
amount: 深度数量
参数描述:
market:	是币种类型的名称，如：BTC，DOGE，LTC，KNC，ETH，USDT
法币类型如：BTC，ETH，USDT
Market字段为:  法币_交易币 eg:BTC_DOGE
level 市场深度判断 档位深度

## 4.历史成交
描述：历史成交
请求：http://www.22coin.com/Api/Trades.html
示例：
### Request
GET http://www.22coin.com/Api/Trades.html?market=doge_btc&level=20
### Response
[
    "trades": [
        {
            "id": 1, 
            "time": "09:14:14", 
            "price": "0.002", 
            "amount": "29.923699999999997", 
            "en_type": "ask", 
            "type": "卖出"
        }, 
]
返回值说明:
date : 交易时间(时间戳)
price : 交易价格
amount : 交易数量
tid : 交易生成ID
type : 交易类型， (买)/(卖)
en_type : 委托类型，ask/bid
参数描述:获取到最近成交中的交易数据
market:	是币种类型的名称，如：BTC，DOGE，LTC，KNC，ETH，USDT
法币类型如：BTC，ETH，USDT
Market字段为:  法币_交易币 eg:BTC_DOGE
Level:根据档位选择返回5条或20条数据

## 5.K线
描述：历史成交
请求：http://www.22coin.com/Api/Kline.html
示例：
### Request
http://www.22coin.com/Api/Kline.html?market=doge_btc&step=3600
### Response
{
    "data": [
        [
            1472107500000,
            3840.46,
            3843.56,
            3839.58,
            3843.3,
            492.456
        ]...
    ],
   
}
返回值说明:
data : K线数据
[
1417536000000, 时间戳
2370.16, 开盘价
2380, 最高价
2352, 最低价
2367.37, 收盘
17259.83 交易量
] 参数描述:
获取到历史成交中的交易数据

market:	是币种类型的名称，例如：BTC，DOGE，LTC，KNC，ETH，USDT
法币类型如：BTC，ETH，USDT
Market字段为:  法币_交易币 eg:BTC_DOGE
step:获取数据的类型步进，如step=60获取以1分钟为单位的数据step=3600获取以1小时为单位数据。

## 6.获取交易所交易对行情数据(非小号)
Get /api/v1/allticker 获取所有交易对行情 
URL https://接口域名/api/v1/ticker.do
示例
Request
GET https://接口域名/api/v1/allticker
Response
{ 
"date":"1410431279", 
"ticker":[{ 
"symbol":"ltc_usdt", 
"buy":"33.15", 
"high":"34.15", 
"last":"33.15", 
"low":"32.05", 
"sell":"33.16", 
"vol":"10532696.39199642" 
},{ 
"symbol":"btc_usdt", 
"buy":"33.15", 
"high":"34.15", 
"last":"33.15", 
"low":"32.05", 
"sell":"33.16", 
"vol":"10532696.39199642" 
}] 
} 
返回值说明
date: 返回数据时服务器时间 
symbol: 交易对（交易对1简称_交易对2简称） 
buy: 买一价 
high: 最高价 
last: 最新成交价 
low: 最低价 
sell: 卖一价 
vol: 成交量(最近的24小时)
