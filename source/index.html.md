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

# Invitation Code

## Generate Invitation Code

```shell
curl "https://teacher.filippine.com.cn/api/invite"
  -X GET
  -H "Content-Type: application/json"
  -H "Authorization: token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwaG9uZSI6IjE4MTM4NzEyMTI4IiwiaWF0IjoxNTU2NTA3MDQ4LCJleHAiOjIxNjEzMDcwNDh9.Sd42wEnznbDfqEoPkfNj9SmxQSOskiOVdNWYKZLy5Vg"
```

> The above command should return JSON structured like this:

```json
{
  "success": true
}
```

This endpoint tells the server to generate a invitation code for this user and then send the code to his/her phone via SMS

### HTTPS Request

`GET https://teacher.filippine.com.cn/api/invite`

<aside class="notice">The users should already have an account in our database with a phone number, otherwise it would fail</aside>

## Verify Invitation Code

```shell
curl "https://teacher.filippine.com.cn/api/verifyInvitation?code=s8s9"
  -X GET
  -H "Content-Type: application/json"
  -H "Authorization: token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwaG9uZSI6IjE4MTM4NzEyMTI4IiwiaWF0IjoxNTU2NTA3MDQ4LCJleHAiOjIxNjEzMDcwNDh9.Sd42wEnznbDfqEoPkfNj9SmxQSOskiOVdNWYKZLy5Vg"
```

> The above command should return JSON structured like this:

```json
{
  "success": true
}
```

This endpoint checks whether the invitation code that this user typed is correct

### HTTPS Request

`GET https://teacher.filippine.com.cn/api/verifyInvitation`

### Query Parameters
Parameter | Required | Description
--------- | ------- | -----------
code | true | 用户输入的邀请码

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
  -d '{"candidates": [{"id": 94270660, "primary": {"date": "2019-05-19", "time": "9:30 - 10:00"}, "secondary": {"date": "2019-05-20", "time": "10:30 - 11:00"}}], "openid":"oUpF8uMuAJO_M2pxb1Q9zNjWeS6o"}'
  -H "Content-Type: application/json"
  -H "Authorization: token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwaG9uZSI6IjE4MTM4NzEyMTI4IiwiaWF0IjoxNTU2NTA3MDQ4LCJleHAiOjIxNjEzMDcwNDh9.Sd42wEnznbDfqEoPkfNj9SmxQSOskiOVdNWYKZLy5Vg"
```

> The above command should return JSON structured like this:

```json
{
  "success": true,
  "bridge_data": {
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
candidates | true | 订单里面的教师list
openid | true | 用户在此appid下的唯一标识

### candidates 结构 (array of objects comprise the following)

Parameter | Required | Description
--------- | ------- | -----------
id | true | 此教师id
primary | false | 首选面试时间(若不传contactAgent, 或者contactAgent为false, 则必填)
secondary | false | 备选面试时间(若不传contactAgent, 或者contactAgent为false, 则必填)
contactAgent | false | 是否联系顾问选择面试时间(若没有传primary和secondary, 则必填)

### primary和secondary 结构

Parameter | Required | Description
--------- | ------- | -----------
date | true | 日期 eg. "2019-05-22"
time | true | 时间 eg. "9:30 - 10:00" (**时间区间只能为半小时的间隔**)

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
      "candidate_name": "Evelyn Navarro Mantabonte",
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

## Add Favorite Teacher

```shell
curl "https://teacher.filippine.com.cn/api/addFavorite"
  -X POST
  -d '{"teacher": "90833356"}'
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
teacher | true | 教师id

## Remove Favorite Teacher

```shell
curl "https://teacher.filippine.com.cn/api/removeFavorite"
  -X POST
  -d '{"teacher": "90833356"}'
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
teacher | true | 教师id

# Shopping Cart

## Get Shopping Cart

```shell
curl "https://teacher.filippine.com.cn/api/getCart"
  -X GET
  -H "Content-Type: application/json"
  -H "Authorization: token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwaG9uZSI6IjE4MTM4NzEyMTI4IiwiaWF0IjoxNTU2NTA3MDQ4LCJleHAiOjIxNjEzMDcwNDh9.Sd42wEnznbDfqEoPkfNj9SmxQSOskiOVdNWYKZLy5Vg"
```

> The above command should return JSON structured like this:

```json
{
  "success": true,
  "cart": [
    {
      "candidate_id": "95874587",
      "candidate_name": "test1"
      ...
    },
    {...},
    {...}
  ]
}
```

This endpoint retrieves the shopping cart of a user

### HTTPS Request

`GET https://teacher.filippine.com.cn/api/getCart`

## Add Shopping Cart Item

```shell
curl "https://teacher.filippine.com.cn/api/addCartItem"
  -X POST
  -d '{"teacher": "90833356"}'
  -H "Content-Type: application/json"
  -H "Authorization: token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwaG9uZSI6IjE4MTM4NzEyMTI4IiwiaWF0IjoxNTU2NTA3MDQ4LCJleHAiOjIxNjEzMDcwNDh9.Sd42wEnznbDfqEoPkfNj9SmxQSOskiOVdNWYKZLy5Vg"
```

> The above command should return JSON structured like this:

```json
{
  "success": true
}
```

This endpoint add an item to the shopping cart of a user

### HTTPS Request

`POST https://teacher.filippine.com.cn/api/addCartItem`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
teacher | true | 教师id

## Remove Shopping Cart Item

```shell
curl "https://teacher.filippine.com.cn/api/removeCartItem"
  -X POST
  -d '{"teacher": "90833356"}'
  -H "Content-Type: application/json"
  -H "Authorization: token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwaG9uZSI6IjE4MTM4NzEyMTI4IiwiaWF0IjoxNTU2NTA3MDQ4LCJleHAiOjIxNjEzMDcwNDh9.Sd42wEnznbDfqEoPkfNj9SmxQSOskiOVdNWYKZLy5Vg"
```

> The above command should return JSON structured like this:

```json
{
  "success": true
}
```

This endpoint remove an item from the shopping cart of a user

### HTTPS Request

`POST https://teacher.filippine.com.cn/api/removeCartItem`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
teacher | true | 教师id
