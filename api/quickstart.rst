=================================
说明
=================================

测试环境
---------------------------------
https://uatbizapi.yianyouxuan.com


正式环境
---------------------------------
https://bizapi.yianyouxuan.com

申请流程
---------------------------------
1.	合作商向怡安悠选方面申请client_id，client_secret
2.	合作商技术人员通过怡安悠选的测试环境
3.	合作商正式环境连接到怡安悠选的正式环境

接入指南
---------------------------------
1. 生成token

   a) 客户端根据申请的client_id，client_secret获取token

2.	timestamp

   a) 当前调用时间，需要加入在请求参数中，五分钟以内为正常。格式为“2014-01-01 01:01:01”

3.	签名生成规则

   a) 提供client_secret

   b) 将请求的内容结构（需要剔除时间戳）转化为标准的json字符串。

   c) sign 为 json_str + client_secret 的32位md5值

   d) python3 示例

    .. code-block:: python

        >>> import json
        >>> import hashlib
        >>> client_secret='test'
        >>> data={'oid':'test001'}
        >>> raw_str=json.dumps(data, separators=(',', ':')) + client_secret
        >>> m2=hashlib.md5()
        >>> m2.update(raw_str.encode())
        >>> sign=m2.hexdigest()
        >>> print(raw_str,sign)
        {"oid":"test001"}test a2d5db80ec2a5d3a1a6783273e040e77

4.	认证方式

   a) 每次请求需要将token放入到header: {'Authorization': 'Bearer 14d3de567caaee6f7538f0c297d41cf466a2aa9f'}

5.	权限控制

   a) 返回的token都会带scope，目前默认值都是read。在申请token时需要传递此参数

6. 请求参数中的数值类型需要保留小数点后两位

7. 返回值的通用格式为

    :success: 布尔类型，请求是否成功的标志
    :result_code: 返回结果状态号
    :result_message: 返回结果描述
    :result: 返回结果数据

8. 流量限制

   - 每个合作商每分钟访问不得超过70次

   - 个别API可能会有特殊设置

   - 超出限制，会返回如下结果

    .. code-block:: json

        {
            "detail": "Request was throttled. Expected available in 14 seconds.",
            "success": false,
            "result_code": "throttled",
            "result_message": "Request was throttled. Expected available in 14 seconds."
        }

