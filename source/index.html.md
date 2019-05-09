---
title: 外教项目API文档

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

---

# Introduction

外教项目API文档

# Test

```shell
curl -X GET "https://teacher.filippine.com.cn/api/test"
```

> The above command should return JSON structured like this:

```json
{
  "success": true
}
```

此接口测试服务是否正确运行

### HTTPS Request

`GET https://teacher.filippine.com.cn/api/test`


# Headers

> Example header:

```shell
curl "api_endpoint_here"
  -H "Content-Type: application/json"
  -H "Authorization: token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwaG9uZSI6IjE4MTM4NzEyMTI4IiwiaWF0IjoxNTU2NTA3MDQ4LCJleHAiOjIxNjEzMDcwNDh9.Sd42wEnznbDfqEoPkfNj9SmxQSOskiOVdNWYKZLy5Vg"
```

Every API request must come with authorization header (the JSON Web Token string)

Every API request must come with application/json content type


# Teachers

## Get Initial Teachers List

```shell
curl "https://teacher.filippine.com.cn/api/getInitialTeachersList?limit=5"
  -X GET
  -H "Content-Type: application/json"
  -H "Authorization: token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwaG9uZSI6IjE4MTM4NzEyMTI4IiwiaWF0IjoxNTU2NTA3MDQ4LCJleHAiOjIxNjEzMDcwNDh9.Sd42wEnznbDfqEoPkfNj9SmxQSOskiOVdNWYKZLy5Vg"
```

> The above command should return JSON structured like this:

```json
{
  "success": true,
  "candidates": {
    "recommend": [{...}, {...}, ...],
    "new": [{...}, {...}, ...],
    "all": [{...}, {...}, ...]
  }
}
```

This endpoint retrieves initial teachers list with all three categories

### HTTPS Request

`GET https://teacher.filippine.com.cn/api/getInitialTeachersList`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
limit | true | 教师个数(每一个类别)

## Get Teachers List

```shell
curl "https://teacher.filippine.com.cn/api/getPublishedTeachersList?category=all&page=5&per_page=10"
  -X GET
  -H "Content-Type: application/json"
  -H "Authorization: token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwaG9uZSI6IjE4MTM4NzEyMTI4IiwiaWF0IjoxNTU2NTA3MDQ4LCJleHAiOjIxNjEzMDcwNDh9.Sd42wEnznbDfqEoPkfNj9SmxQSOskiOVdNWYKZLy5Vg"
```

> The above command should return JSON structured like this:

```json
{
  "success": true,
  "candidates": [
    {...},
    {...},
    {...}
  ]
}
```

This endpoint retrieve all published teachers by categories

### HTTPS Request

`GET https://teacher.filippine.com.cn/api/getPublishedTeachersList`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
category | true | 类型: all / new / recommend
page | true | 当前是第几页
per_page | true | 每一页的个数

## Get Teacher Detail

```shell
curl "https://teacher.filippine.com.cn/api/getTeacherDetail?id=90833356"
  -X GET
  -H "Content-Type: application/json"
  -H "Authorization: token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwaG9uZSI6IjE4MTM4NzEyMTI4IiwiaWF0IjoxNTU2NTA3MDQ4LCJleHAiOjIxNjEzMDcwNDh9.Sd42wEnznbDfqEoPkfNj9SmxQSOskiOVdNWYKZLy5Vg"
```

> The above command should return JSON structured like this:

```json
{
  "success": true,
  "candidate": {
    "id": 90833356,
    "english_name": "Evelyn  Navarro  Mantabonte",
    "age": 31,
    "birthday": "1987-07-03",
    "nationality": "菲律宾",
    ...
  }
}
```

This endpoint retrieve the detail information of a teacher

### HTTPS Request

`GET https://teacher.filippine.com.cn/api/getTeacherDetail`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true | 教师唯一id

## Get Available Interview Times

```shell
curl "https://teacher.filippine.com.cn/api/getInterviewTimes?id=90833356&starttime=2019-04-28&endtime=2019-05-28"
  -X GET
  -H "Content-Type: application/json"
  -H "Authorization: token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwaG9uZSI6IjE4MTM4NzEyMTI4IiwiaWF0IjoxNTU2NTA3MDQ4LCJleHAiOjIxNjEzMDcwNDh9.Sd42wEnznbDfqEoPkfNj9SmxQSOskiOVdNWYKZLy5Vg"
```

> The above command should return JSON structured like this:

```json
{
  "success": true,
  "available_times": {
    "2019-05-29": ["14:30 - 15:00"],
    "2019-05-30": ["9:30 - 10:00", "15:30 - 16:00"]
  }
}
```

This endpoint retrieve the **available** interview time slots of a teacher

### HTTPS Request

`GET https://teacher.filippine.com.cn/api/getInterviewTimes`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true | 教师唯一id
starttime | false | 开始时间(日期 YYYY-MM-DD)
endtime | false | 结束时间(日期 YYYY-MM-DD)

# Appointment

## Get Orders List

```shell
curl "https://teacher.filippine.com.cn/api/getInterviewOrdersList?page=1&per_page=5"
  -X GET
  -H "Content-Type: application/json"
  -H "Authorization: token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwaG9uZSI6IjE4MTM4NzEyMTI4IiwiaWF0IjoxNTU2NTA3MDQ4LCJleHAiOjIxNjEzMDcwNDh9.Sd42wEnznbDfqEoPkfNj9SmxQSOskiOVdNWYKZLy5Vg"
```

> The above command should return JSON structured like this:

```json
{
  "success": true,
  "total": 3,
  "orders": [
    {
      "_id": "56897412",
      "agent_name": "Ivy",
      "agent_phone": "12345678987",
      "payment_amount": "200",
      "status": 0,
      "create_time": "2019-03-15T03:08:46.453Z"
    },
    {...},
    {...}
  ]
}
```

This endpoint retrieves the purchased orders of a user

### HTTPS Request

`GET https://teacher.filippine.com.cn/api/getInterviewOrdersList`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
page | true | 当前是第几页
per_page | true | 每一页的个数

## Get Order Detail

```shell
curl "https://teacher.filippine.com.cn/api/getInterviewOrder?id=56897412"
  -X GET
  -H "Content-Type: application/json"
  -H "Authorization: token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwaG9uZSI6IjE4MTM4NzEyMTI4IiwiaWF0IjoxNTU2NTA3MDQ4LCJleHAiOjIxNjEzMDcwNDh9.Sd42wEnznbDfqEoPkfNj9SmxQSOskiOVdNWYKZLy5Vg"
```

> The above command should return JSON structured like this:

```json
{
  "success": true,
  "order": {
    "agent_id": "5c91cb708feed17e1e5352b8",
    "agent_name": "Ivy",
    "interviews": [...],
    "refund_detail": "",
    ...
  }
}
```

This endpoint retrieves the the order detail

### HTTPS Request

`GET https://teacher.filippine.com.cn/api/getInterviewOrder`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true | 订单id

## User Choose Interview Time

```shell
curl "https://teacher.filippine.com.cn/api/pushInterviewTime"
  -X POST
  -d '{"order_id": "mmmmm", "interview_id": "222", "interview_time": {"primary": {"2019-05-19": "9:30 - 10:00"}, "secondary": {"2019-05-20": "10:30 - 11:00"}}}'
  -H "Content-Type: application/json"
  -H "Authorization: token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwaG9uZSI6IjE4MTM4NzEyMTI4IiwiaWF0IjoxNTU2NTA3MDQ4LCJleHAiOjIxNjEzMDcwNDh9.Sd42wEnznbDfqEoPkfNj9SmxQSOskiOVdNWYKZLy5Vg"
```

> The above command should return JSON structured like this:

```json
{
  "success": true
}
```

This endpoint let a user choose his preferrable interview time

### HTTPS Request

`POST https://teacher.filippine.com.cn/api/pushInterviewTime`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
order_id | true | 订单id
interview_id | true | 面试id
interview_time | true | 雇主选择的面试时间

### interview_time 结构

Parameter | Required | Description
--------- | ------- | -----------
primary | true | 首选面试时间
secondary | true | 备选面试时间

# Wechat Pay

## Request Payment

```shell
curl "https://teacher.filippine.com.cn/api/requestPayment"
  -X POST
  -d '{"order_id":"mmmmm", "body":"腾讯充值中心-QQ会员充值", "detail":"商品详情在这里写", "attach":"深圳分店", "out_trade_no":"20150806125346", "total_fee":"88", "limit_pay":"no_credit", "openid":"oUpF8uMuAJO_M2pxb1Q9zNjWeS6o"}'
  -H "Content-Type: application/json"
  -H "Authorization: token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwaG9uZSI6IjE4MTM4NzEyMTI4IiwiaWF0IjoxNTU2NTA3MDQ4LCJleHAiOjIxNjEzMDcwNDh9.Sd42wEnznbDfqEoPkfNj9SmxQSOskiOVdNWYKZLy5Vg"
```

> The above command should return JSON structured like this:

```json
{
  "success": true,
  "data": {
    "appId": "wxd678efh567hg6787",
    "timeStamp": "1490840662",
    "nonceStr": "5K8264ILTKCH16CQ2502SI8ZNMTM67VS",
    "package": "prepay_id=wx2017033010242291fcfe0db70013231072",
    "signType": "MD5",
    "paySign": "22D9B4E54AB1950F51E0649E8810ACD6"
  }
}
```

> The above returned result will be used in **wx.requestPayment()**

This endpoint send payment request to our server which will then send order request to wechat server
Meanwhile, it will generate a purchase order

### HTTPS Request

`POST https://teacher.filippine.com.cn/api/requestPayment`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
order_id | true | 订单id
body | true | 商品简单描述，该字段请按照规范传递，具体请见[参数规定](https://pay.weixin.qq.com/wiki/doc/api/wxa/wxa_api.php?chapter=4_2)
detail | false | 商品详细描述
attach | false | 附加数据, 可作为自定义参数使用
out_trade_no | true | 商户系统内部订单号，要求32个字符内，只能是数字、大小写字母, 且在同一个商户号下唯一, 详见[这里](https://pay.weixin.qq.com/wiki/doc/api/wxa/wxa_api.php?chapter=4_2)
total_fee | true | 订单总金额，单位为分
limit_pay | false | 上传此参数no_credit--可限制用户不能使用信用卡支付
openid | true | 用户在此appid下的唯一标识

### Returned Parameters

Parameter | Description
--------- | -----------
appId | 微信小程序id
timeStamp | 服务器返回的时间戳
nonceStr | 服务器返回的随机字符串
package | 包含prepay_id
signType | 签名算法
paySign | 服务器返回的签名

<aside class="notice">微信支付交互流程具体请见<a href="https://pay.weixin.qq.com/wiki/doc/api/wxa/wxa_api.php?chapter=7_4">这里</a></aside>

# Favorite

## Get Favorite List

```shell
curl "https://teacher.filippine.com.cn/api/getFavoriteList"
  -X GET
  -H "Content-Type: application/json"
  -H "Authorization: token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwaG9uZSI6IjE4MTM4NzEyMTI4IiwiaWF0IjoxNTU2NTA3MDQ4LCJleHAiOjIxNjEzMDcwNDh9.Sd42wEnznbDfqEoPkfNj9SmxQSOskiOVdNWYKZLy5Vg"
```

> The above command should return JSON structured like this:

```json
{
  "success": true,
  "favorites": [
    {
      "english_name": "Evelyn Navarro Mantabonte",
      ...
    },
    {...},
    {...}
  ]
}
```

This endpoint retrieves favorite teachers of a user

### HTTPS Request

`GET https://teacher.filippine.com.cn/api/getFavoriteList`

## Add Favorite Teachers

```shell
curl "https://teacher.filippine.com.cn/api/addFavorite"
  -X POST
  -d '{"teachers": ["27446972", "13634857", "90833356"]}'
  -H "Content-Type: application/json"
  -H "Authorization: token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwaG9uZSI6IjE4MTM4NzEyMTI4IiwiaWF0IjoxNTU2NTA3MDQ4LCJleHAiOjIxNjEzMDcwNDh9.Sd42wEnznbDfqEoPkfNj9SmxQSOskiOVdNWYKZLy5Vg"
```

> The above command should return JSON structured like this:

```json
{
  "success": true
}
```

This endpoint add favorite teachers of a user

### HTTPS Request

`POST https://teacher.filippine.com.cn/api/addFavorite`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
teachers | true | 教师id list

## Remove Favorite Teachers

```shell
curl "https://teacher.filippine.com.cn/api/removeFavorite"
  -X POST
  -d '{"teachers": ["27446972", "13634857", "90833356"]}'
  -H "Content-Type: application/json"
  -H "Authorization: token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwaG9uZSI6IjE4MTM4NzEyMTI4IiwiaWF0IjoxNTU2NTA3MDQ4LCJleHAiOjIxNjEzMDcwNDh9.Sd42wEnznbDfqEoPkfNj9SmxQSOskiOVdNWYKZLy5Vg"
```

> The above command should return JSON structured like this:

```json
{
  "success": true
}
```

This endpoint remove favorite teachers of a user

### HTTPS Request

`POST https://teacher.filippine.com.cn/api/removeFavorite`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
teachers | true | 教师id list
