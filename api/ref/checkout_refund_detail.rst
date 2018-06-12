=========================================
查询退款信息
=========================================

|

:接口地址: /api/checkout/refund-detail/
:http请求方式: POST
:支持格式: application/json
:权限: point_pay
:参数:

================         ================          ========           =========         ======================
参数说明                  参数名                    类型               是否必须           描述
================         ================          ========           =========         ======================
client refund id         client_refund_id          string              是               退款流水号，必须唯一
timestamp                timestamp                 string              是               时间戳
sign                     sign                      string              是               签名
================         ================          ========           =========         ======================

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
	     "client_refund_id":"001"
    }

:返回示例:

.. code-block:: json

    {
        "result_message": "",
        "result_code": "refund_order_detail",
        "result": {
            "status": "init_refund",
            "client_refund_id": "001",
            "amount": 10,
            "cash_refund_needed": null
        },
        "success": true
    }
