=========================================
支付信息回调
=========================================

|

:接口地址: 客户端配置的notify_url参数
:http请求方式: POST
:支持格式: application/json
:参数:

================         ==============          ========           =========         ======================
参数说明                  参数名                  类型               是否必须           描述
================         ==============          ========           =========         ======================
out trade number         out_trade_no            string              是               外部订单号
client pay id            client_pay_id           string              是               支付流水号,必须唯一
total amount             total_amount            decimal             是               总金额
status                   status                  string              是               支付状态
point amount             point_amount            decimal             是               积分支付金额
cash amount              cash_amount             decimal             是               现金支付金额
point paid               point_paid              bool                是               积分是否已支付
cash  paid               cash_paid               bool                是               现金是否已支付
timestamp                timestamp               string              是               时间戳
sign                     sign                    string              是               签名
================         ==============          ========           =========         ======================

:请求示例:

.. code-block:: json

    {
    "client_pay_id": "0000010111136",
    "status": "point_paid",
    "out_trade_no": "20111111111",
    "promotion_amount": 0,
    "total_amount": "2144.00",
    "point_paid": true,
    "point_amount": true,
    "cash_paid": false,
    "cash_amount": "2114.00",
    "sign": "639f849b95a806a25744a4852bddd079",
    "timestamp":"2018-06-11 11:02:47"
    }

