# 入门 :id=title

您可以使用 鬼斩图床 API 来完成您在我们网站上可以执行的任何操作。

鬼斩图床 API 是基于HTTPS和JSON响应的RESTful API。如果您已经使用过鬼斩图床，你可以在 [API 密钥](https://www.gzssimg.com/app/my/tokens) 页面获取API 密钥。

## 接口 :id=endpoints

您可以通过向特定版本的接口URL发出HTTPS请求来访问API，其中GET，POST，PUT，PATCH和DELETE方法指示您如何与可用信息进行交互。应只通过启用了SSL的HTTPS（443端口）协议访问所有接口。

所有接口的基本URL为:

```
https://api.gzssimg.com/v1/
```

## 请求 :id=requests

任何请求必须携带JSON格式的有效载荷(payload)或表单数据(FormData)通过HTTPS发送，并使用有效的API密钥对请求进行身份验证。

### API 密钥 :id=api-tokens

API 密钥是对鬼斩图床API进行身份验证的唯一途径。

*请求头*

|名称|格式|描述|
|-|-|-|
|**API 密钥**|Authorization: Bearer &lt;token&gt;|在 [API 密钥](https://www.gzssimg.com/app/my/tokens) 页面生成的API密钥|

### 样例请求 :id=example-request

请求的格式通常如下所示:

```
GET images
```

**API 密钥 cURL** (样例)

```
curl -X GET "https://api.gzssimg.com/v1/images" \
     -H "Content-Type:application/json" \
     -H "Authorization: Bearer eyJ0eXAiOi...8FAaCFU8"
```

### 速度限制 :id=rate-limiting

鬼斩图床 API 在1分钟内最多接收60个请求。

### 分页 :id=pagination

响应的结果可根据您的请求受到限制。你可以使用以下查询参数对返回的结果进行分页。

|名称|类型|描述|
|-|-|-|
|page|*integer*|返回哪一页的结果|
|per_page|*integer*|每页返回多少个结果|
|order|*string*|用于对响应的结果进行排序的属性名|
|direction|*string*|只能为`ASC`或者`DESC`|

**cURL** (样例)

```
curl -X GET "https://api.gzssimg.com/v1/images?page=2&per_page=10&order=upload_time&direction=DESC" \
     -H "Content-Type:application/json" \
     -H "Authorization: Bearer eyJ0eXAiOi...8FAaCFU8"
```

## 响应 :id=responses

### 格式

每个响应都是一个JSON对象。请求的数据包含在`result`字段中。如果请求有响应，它将始终包含在`result`字段中。响应还包含了`code`与`message` 字段。一个成功响应的`code`是0。

日期时间字段将始终采用UTC ISO-8601格式，包括微秒。

**成功响应** (样例)

```json
{
    "code": 0,
    "message": null,
    "result": [
        {
            "name":"HNxEE3W",
            "fullname":"HNxEE3W.jpeg",
            "size":24902,
            "upload_time":"2021-01-09T17:52:03.000000Z",
            "url":"https:\/\/gzimg.cc\/21w01\/HNxEE3W.jpeg"
        }
    ]
}
```

**错误响应** (样例)

```json
{
    "code": 1002,
    "message": "Image size exceeds the limit.",
    "result": []
}
```