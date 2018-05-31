=========================================
创建外部订单
=========================================

|
:说明: 目前只支持更新备注
:接口地址: /api/order/addExternalOrder/
:http请求方式: POST
:支持格式: application/json
:权限: add_ex_order
:参数:

================         ==============          ========           =========         ======================
参数说明                  参数名                  类型               是否必须           描述
================         ==============          ========           =========         ======================
oid                      oid                     string              是               订单号
organization code        org_code                string              是               公司号
employee number          ee_no                   string              是               员工号
sign                     sign                    string              是               签名
================         ==============          ========           =========         ======================

:返回值:

.. code-block:: json

    {
        "result_code": "update_order_with_ex_num",
        "result_message": "update order with external order number successfully",
        "result": {
            "order_number": "2017112921278398",
            "remark": "1243fwasfvdsv"
        },
        "success": true
    }


:返回值说明:

