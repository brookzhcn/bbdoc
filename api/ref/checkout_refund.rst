=========================================
退款接口
=========================================

|

:说明: 只能对支付已完成和部分退款的订单进行退款操作；运费退款只许退一次；退款时有现金优先退现金部分
:接口地址: /api/checkout/refund/
:http请求方式: POST
:支持格式: application/json
:权限: point_pay
:参数:

================         ================          ========           =========         ======================
参数说明                  参数名                    类型               是否必须           描述
================         ================          ========           =========         ======================
out trade no             out_trade_no              string              否               外部订单号
client pay id            client_pay_id             string              否               支付流水号
client refund id         client_refund_id          string              是               退款流水号，必须唯一
amount                   amount                    decimal             是               退款金额
is shipping              is_shipping               bool                是               是否为运费退款
timestamp                timestamp                 string              是               时间戳
sign                     sign                      string              是               签名
================         ================          ========           =========         ======================


.. role:: red

:red:`*out_trade_no 和 client_pay_id 不可以同时为空，两个都传时，优先使用out_trade_no*`


:返回值:

+ *status：订单状态*

    - init_refund：退款创建
    - point_refund：积分已退
    - cash_refund：现金已退
    - refund_finished：退款完成

+ *cash_refund_needed: 是否需要现金退款*

   如果需要现金退款，则需要走财务流程，将通过异步回调的形式返回退款结果


:请求示例:

.. code-block:: json

    {
	"client_pay_id":"0000010111135",
	"client_refund_id":"007",
	"amount":10,
    "is_shipping":false
    }

:返回示例:

.. code-block:: json

    {
    "result_message": "",
    "result_code": "refund_order_created",
    "result": {
        "status": "point_refund",
        "client_refund_id": "007",
        "amount": 10,
        "cash_refund_needed": false
    },
    "success": true
    }
