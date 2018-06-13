=========================================
获取用户信息（跳转登录使用）
=========================================

|

:说明: BB网站跳转到合作商网站时会携带code参数, 一般而言code时效是一分钟
:接口地址: /api/oauth2/get-user-info/　
:http请求方式: POST
:支持格式: application/json
:权限: read
:请求参数:

===================      ==============          =================          =========         ======================
参数说明                  参数名                  类型                       是否必须           描述
===================      ==============          =================          =========         ======================
code                     code                     string                     是               跳转码
timestamp                timestamp                string                     是               时间戳
sign                     sign                     string                     是               签名
===================      ==============          =================          =========         ======================

:返回参数:

+ ee_no: 员工号
+ org_code: 公司号
+ user_id: 员工唯一标识id
+ national_id: 身份证号
+ national_id_type: 身份证类型
+ from_application_name: 跳转来源

:请求示例（省略时间戳和签名）:

.. code-block:: json

    {
        "code":"0iG28ORZZhadbrYhYNaSkQDaZRLJWo"
    }


:返回示例:

.. code-block:: json

    {
        "result_code": "code_cracked",
        "result_message": "code has been cracked",
        "result": {
            "ee_no": "20140400001",
            "org_code": "yianyouxuan",
            "user_id": 124506,
            "national_id": "",
            "national_id_type": "ID",
            "from_application_name": "BB"
        },
        "success": true
    }



