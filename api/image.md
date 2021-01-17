# 图片

图片是描述已上传图片的对象。

## 对象定义 :id=def

查看对象上定义的属性和限制

<details>
<summary>定义</summary>

**示例对象**

```json
{
    "name":"HNxEE3W",
    "fullname":"HNxEE3W.jpeg",
    "size":24902,
    "upload_time":"2021-01-09T17:52:03.000000Z",
    "url":"https:\/\/gzimg.cc\/21w01\/HNxEE3W.jpeg"
}
```

|名称 */类型*|描述 */样例*|限制|
|-|-|-|
|**name**<br>*string*|图片的名称 <br>`"HNxEE3W"`|只读|
|**fullname**<br>*string*|图片的完整名称 <br> `"HNxEE3W.jpeg"`|只读|
|**size**<br>*integer*|图片的尺寸 <br> `24902`|只读|
|**upload_time**<br>*datetime*|上传时间 <br> `"2021-01-09T17:52:03.000000Z"`|只读|
|**url**<br>*string*|图片URL <br> `"https:\/\/gzimg.cc\/21w01\/HNxEE3W.jpeg"`|只读|

</details>

## 列出图片 :id=list

列出，搜索并排序图片

```
GET images
```

*参数*

|名称 */类型*|描述 */样例*|限制|
|-|-|-|
|page<br>*integer*|*可选*<br>分页结果的页码<br>`1`|默认值: 1<br>最小值: 1|
|per_page<br>*integer*|*可选*<br>每页图片的数量<br>`10`|默认值: 10<br>最小值: 5<br>最大值: 20|
|order<br>*string*|*可选*<br>用于对图片进行排序的字段<br>`size`|有效值: name, size, upload_time|
|direction<br>*string*|*可选*<br>排序的方向<br>`desc`|有效值: ASC, DESC|

**响应** (示例)

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

## 上传图片 :id=upload

```
POST images
```

*参数*

|名称 */类型*|描述|限制|
|-|-|-|
|image<br>*binary*|*可选*<br>图片的二进制信息|如果`image_base64`为空，则此项不能为空|
|image_base64<br>*string*|*可选*<br>由base64编码后的图片信息|如果`image`为空，则此项不能为空|

**响应** (示例)

```json
{
    "code": 0,
    "message": null,
    "result": {
        "name":"HNxEE3W",
        "fullname":"HNxEE3W.jpeg",
        "size":24902,
        "upload_time":"2021-01-09T17:52:03.000000Z",
        "url":"https:\/\/gzimg.cc\/21w01\/HNxEE3W.jpeg"
    }
}
```