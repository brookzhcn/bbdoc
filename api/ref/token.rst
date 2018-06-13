=========================================
生成token
=========================================

|

:说明: 合作方在访问怡安优选api时，首先需要获取token，token的时效是10小时
:接口地址: /api/oauth2/token/
:http请求方式: POST
:支持格式: application/json
:请求参数:

================         ==============          ========           =========         ======================
参数说明                  参数名                  类型               是否必须           描述
================         ==============          ========           =========         ======================
client id                client_id               string              是               身份识别号
client secret            client_secret           string              是               密钥
scope                    scope                   string              是               空则返回所有权限
grant type               grant_type              string              是               client_credentials
================         ==============          ========           =========         ======================

:请求示例:

.. code-block:: json

    {
	"client_id":"YiBIyM1f0avW3ScmYSdiLhEdWoSPlsXbjO5or8pl",
	"client_secret":"JvJoSxf4aAzGNIwcek8t0EjCOdrcFPFDjb2fswuvLZanFN6Qjq9QahHH0LMkG9QS8GWBnNIBDWV1mXijQfXihYJwGMq82JsNwwAAG5NJhPVv00xQBswUjZn9qHR1PZDC",
	"grant_type":"client_credentials",
	"scope":""
     }

:返回示例:

.. code-block:: json

    {
        "result_code": "access_token",
        "result_message": "get access token",
        "result": {
            "access_token": "CfbxGeUyjKWW31Fs6EDgF567xCUD9E",
            "expires_in": 36000,
            "token_type": "Bearer",
            "scope": "cancel_ex_order view_order_detail update_order add_ex_order"
        },
        "success": true
    }
