=========================================
查询支付信息
=========================================

|

:接口地址: /api/checkout/pay-detail/
:http请求方式: POST
:支持格式: application/json
:权限: point_pay
:参数:

================         ==============          ========           =========         ======================
参数说明                  参数名                  类型               是否必须           描述
================         ==============          ========           =========         ======================
out trade no             out_trade_no            string              否               外部订单号
client pay id            client_pay_id           string              否               支付流水号
timestamp                timestamp               string              是               时间戳
sign                     sign                    string              是               签名
================         ==============          ========           =========         ======================

.. role:: red

:red:`*out_trade_no 和 client_pay_id 不可以同时为空，两个都传时，优先使用out_trade_no*`



:返回值:

+ *status：订单状态*

    - unpaid：未支付
    - point_paid：积分支付
    - cash_paid：现金支付
    - pay_finished：支付完成 （全部支付完成，这个状态应视为支付成功的标志）
    - partly_refund：部分退款（可继续退款）
    - total_refund：全部退款 （不可再操作退款）
    - closed：已关闭（订单一定时效后关闭，状态不再变更）

+ *cash_pay_url: 现金支付链接*

   当用户积分不足完全支付的时候，需要导向这个链接，继续现金支付

+ *point_amount: 积分支付金额*

+ *cash_amount: 现在支付金额*

+ *bb_trade_no: 怡安优选商城订单号*

+ *shipping_fee: 运费*


:请求示例:

.. code-block:: json

    {
     "client_pay_id":"0000010111123"
    }

:返回示例:

.. code-block:: json

    {
    "result_message": "",
    "result_code": "out_trade_detail",
    "result": {
        "status": "point_paid",
        "client_pay_id": "0000010111123",
        "out_trade_no": "20111111111",
        "point_amount": 0,
        "cash_amount": 21.44,
        "cash_pay_url": "http://localhost:8001/checkout/pay/2018060730000019/",
        "total_amount": 21.44,
        "bb_trade_no": "2018060730000019",
        "shipping_fee": 5
    },
    "success": true
    }
