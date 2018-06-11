=========================================
退款信息回调
=========================================

|

:接口地址: 客户端配置的notify_url参数
:http请求方式: POST
:method: refund
:支持格式: application/json
:参数:

================         ================          ========           =========         ======================
参数说明                  参数名                    类型               是否必须           描述
================         ================          ========           =========         ======================
client refund id         client_refund_id          string              是               退款流水号,必须唯一
amount                   amount                    decimal             是               总金额
status                   status                    string              是               退款状态
timestamp                timestamp                 string              是               时间戳
sign                     sign                      string              是               签名
================         ================          ========           =========         ======================

:请求示例:

.. code-block:: json

    {
    "client_refund_id": "007",
    "status": "point_refund",
    "amount": "10.00",
    "method": "refund",
    "sign": "40687cef925baaddca45a403cf8a5d22"
    }



