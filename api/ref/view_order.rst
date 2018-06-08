=========================================
查看订单状态
=========================================

|

:接口地址: /api/order/getOrderDetailByExtNum/
:http请求方式: POST
:支持格式: application/json
:权限: view_order_detail
:请求参数:

================         ==============          ========           =========         ======================
参数说明                  参数名                  类型               是否必须           描述
================         ==============          ========           =========         ======================
oid                      oid                     string              是               订单号
timestamp                timestamp               string              是               时间戳
sign                     sign                    string              是               签名
================         ==============          ========           =========         ======================

:返回示例:

.. code-block:: json

    {
        "result_code": "query_order_with_ex_num",
        "result_message": "query order with external order number successfully",
        "result": {
            "status": 5,
            "order_number": "2017112921278398",
            "remark": "1243fwasfvdsv"
        },
        "success": true
    }

:返回值说明:

+ *status：订单状态*

    - 99：未支付
    - 1：已支付
    - 2：处理中
    - 4：已发货
    - 5：已完成
    - 6：已退货
    - 7：已撤销
    - 8：已部分发货


