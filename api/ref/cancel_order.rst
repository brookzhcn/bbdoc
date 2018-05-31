=========================================
取消订单
=========================================

|

:接口地址: /api/order/cancelExternalOrder/
:http请求方式: POST
:支持格式: application/json
:权限: cancel_ex_order
:参数:

================         ==============          ========           =========         ======================
参数说明                  参数名                  类型               是否必须           描述
================         ==============          ========           =========         ======================
oid                      oid                     string              是               订单号
timestamp                timestamp               string              是               时间戳
sign                     sign                    string              是               签名
================         ==============          ========           =========         ======================

:返回值:

.. code-block:: json

    {
        "success": true,
        "result_code": "cancel_without_refund",
        "result_message": "Order cancelled and refund successfully",
        "result":
        {
             "oid": "kangsui.20180327130524244769_1",
        }
    }

