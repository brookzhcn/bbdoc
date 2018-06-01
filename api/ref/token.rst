=========================================
生成token
=========================================

|

:接口地址: /api/oauth2/token/
:http请求方式: POST
:支持格式: application/json
:请求参数:

================         ==============          ========           =========         ======================
参数说明                  参数名                  类型               是否必须           描述
================         ==============          ========           =========         ======================
client id                client_id               string              是               身份识别号
client secret            client_secret           string              是               密钥
scope                    scope                   string              否               权限
grant type               grant_type              string              是               client_credentials
================         ==============          ========           =========         ======================

:返回值:

.. code-block:: json

    {
        "access_token": "mUmweeZAFy4bvNof8OQL2ORFZs38Lo",
        "expires_in": 36000,
        "token_type": "Bearer",
        "scope": "read",
    }
