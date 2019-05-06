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
curl "https://teacher.filippine.com.cn/api/getInterviewTimes?id=90833356"
  -X GET
  -H "Content-Type: application/json"
  -H "Authorization: token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwaG9uZSI6IjE4MTM4NzEyMTI4IiwiaWF0IjoxNTU2NTA3MDQ4LCJleHAiOjIxNjEzMDcwNDh9.Sd42wEnznbDfqEoPkfNj9SmxQSOskiOVdNWYKZLy5Vg"
```

> The above command should return JSON structured like this:

```json
{
  "success": true,
  "interview_times": {
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

# Appointment

## Get Orders List

## Get Interview Detail

## Confirm Interview Times

# Wechat Pay

## Request Payment

# Favorite

## Add Favorite Teacher

## Remove Favorite Teacher
