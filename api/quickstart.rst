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
2.	合作商技术人员通过怡安悠选的测试环境uatbizapi.yianyouxuan.com联调(Https)
3.	合作商正式环境连接到怡安悠选的正式环境bizapi.yianyouxuan.com(Https)

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
   d) 示例:
      - client_secret:：test
      - json： {"a": 1}
      - sign： bc705823b8099cd60e5e9ac2a7649698

4.	认证方式

   a) 每次请求需要将token放入到header中

      {'Authorization': 'Bearer 14d3de567caaee6f7538f0c297d41cf466a2aa9f'}

5.	权限控制

   a) 返回的token都会带scope，目前默认值都是read。在申请token时需要传递此参数，

