=========================================
创建外部订单
=========================================

|

:说明: 目前只支持更新备注
:接口地址: /api/order/add-external-order/
:http请求方式: POST
:支持格式: application/json
:权限: add_ex_order
:请求参数:

===================      ==============          =================          =========         ======================
参数说明                  参数名                  类型                       是否必须           描述
===================      ==============          =================          =========         ======================
oid                      oid                      string                     是               订单号
organization code        org_code                 string                     是               公司号
employee number          ee_no                    string                     是               员工号
shipping fee             shipping_fee             decimal                    是               运费
sku items                sku_items                List<sku_item>             是               商品列表
price                    price                    decimal                    是               外部订单总价格
timestamp                timestamp                string                     是               时间戳
sign                     sign                     string                     是               签名
===================      ==============          =================          =========         ======================

**sku_item**

================         ==============          ========           =========         ======================
参数说明                  参数名                  类型               是否必须           描述
================         ==============          ========           =========         ======================
partner sku              partner_sku             string              是               商品货号
quantity                 quantity                int                 是               商品数量
unit price               unit_price              decimal             是               商品单价
================         ==============          ========           =========         ======================

|

:请求参数说明:

- 外部订单价格只做记录，不做实际积分扣减
- 积分扣减以商品单价和数量乘积和为准

:返回示例:

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



