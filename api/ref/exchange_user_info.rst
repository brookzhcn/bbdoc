=========================================
交换用户信息
=========================================

|

:说明: BB网站跳转到合作商网站时会携带code参数
:接口地址: /api/oauth2/getUserInfo/　
:http请求方式: POST
:支持格式: application/json
:权限: read
:请求参数:

===================      ==============          =================          =========         ======================
参数说明                  参数名                  类型                       是否必须           描述
===================      ==============          =================          =========         ======================
code                      code                      string                     是               跳转码
timestamp                timestamp                string                     是               时间戳
sign                     sign                     string                     是               签名
===================      ==============          =================          =========         ======================


:返回值:

.. code-block:: json

    {
        "success": true,
        "result_code": "000",
        "result_message": "",
        "result": {
            "ee_no": "11111111",
            "org_code": "aonhewitt",
            "user_id": 702161,
            "from_application_name": "BB"
        }
    }

:返回值说明:


