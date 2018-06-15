=========================================
支付接口
=========================================

|

:接口地址: /api/checkout/pay/
:http请求方式: POST
:支持格式: application/json
:权限: point_pay
:参数:

================         ==============          ========           =========         ======================
参数说明                  参数名                  类型               是否必须           描述
================         ==============          ========           =========         ======================
out trade number         out_trade_no            string              是               外部订单号（可以为空）
client pay id            client_pay_id           string              是               支付流水号（可以为空）
total amount             total_amount            decimal             是               总金额(包含运费）
shipping fee             shipping_fee            decimal             是               运费（用于记账和运费退款）
user id                  user_id                 int                 是               用户id,唯一标识
employee no              ee_no                   string              是               员工号，用以校验用户信息
redirect url             redirect_url            string              否               完成后跳转地址
timestamp                timestamp               string              是               时间戳
sign                     sign                    string              是               签名
================         ==============          ========           =========         ======================

.. role:: red

:red:`*out_trade_no 和 client_pay_id 不可以同时为空，两个都传时，都必须保证唯一*`

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

:请求示例:

.. code-block:: json

    {
    "out_trade_no":"20111111111",
    "client_pay_id":"0000010111135",
    "total_amount":2144,
    "shipping_fee":5.00,
    "redirect_url":"https://www.example.com",
    "user_id":"442090",
    "ee_no":"a09999"
    }


:返回示例:

.. code-block:: json

    {
     "result_message": "",
     "result_code": "pay_order_created",
     "result": {
            "status": "point_paid",
            "client_pay_id": "0000010111135",
            "point_amount": 131.28,
            "cash_amount": 2012.72,
            "out_trade_no": "20111111111",
            "cash_pay_url": "http://localhost:8001/api_login/?code=mOkR5a9jH42JpQqtGGDpLw9J0H8mnn&next=/checkout/pay/2018060830000035/",
            "total_amount": 2144,
            "bb_trade_no": "2018061530000035"
     },
     "success": true
    }

