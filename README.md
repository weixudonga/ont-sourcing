# ont-sourcing

## 接口

### DDO接口
* [创建ontid](#创建ontid)

* [获取ddo](#获取ddo)

* [更新ontid的属性](#更新ontid的属性)
* [删除ontid的属性](#删除ontid的属性)

* [为ontid添加controller](#为ontid添加controller)

* [通过controller更新ontid的属性](#通过controller更新ontid的属性)
* [通过controller删除ontid的属性](#通过controller删除ontid的属性)

* [获取总条数](#获取总条数)
* [获取历史记录](#获取历史记录)

### 存证接口

* [存证](#存证)
* [批量存证](#批量存证)

* [根据hash取证](#根据hash取证)

* [获取存证总条数](#获取存证总条数)
* [获取存证历史记录](#获取存证历史记录)

* [获取浏览器存证历史记录](#获取浏览器存证历史记录)

### 司法链接口
* [司法链存证](#司法链存证)
* [司法链取证](#司法链取证)

## 接口规范

### 创建ontid

```text
url：/api/v1/ontid/create
method：POST
```

- 请求：

```json
{
    "username":"entity1",
    "password":"888888"
}
```

| Field_Name | Type   | Description |
|:-----------|:-------|:------------|
| username   | String | 设置用户名    |
| password   | String | 设置密码    |

- 响应：

```json
{
    "result": "did:ont:ARMRyKtaukahJgQ4ZTBVhhAByEGPNWip5e",
    "error": 0,
    "action": "createOntid",
    "version": "1.0.0",
    "desc": "SUCCESS"
}
```

| Field_Name | Type   | Description                   |
|:-----------|:-------|:------------------------------|
| error      | int    | 错误码                        |
| action     | String | 动作标志                      |
| desc       | String | 成功返回SUCCESS，失败返回错误描述 |
| result     | String | 成功返回ontid，失败返回""     |
| version    | String | 版本号                        |（）

### 获取ddo

```text
url：/api/v1/ontid/getddo
method：POST
```

- 请求：

```json
{
    "ontid":"did:ont:ARMRyKtaukahJgQ4ZTBVhhAByEGPNWip5e"
}
```

| Field_Name | Type   | Description |
|:-----------|:-------|:------------|
| ontid   | String | 需要查询的ontid    |

- 响应：

```json
{
    "result": {
        "attributes": [],
        "ontId": "did:ont:ARMRyKtaukahJgQ4ZTBVhhAByEGPNWip5e",
        "owners": [
            {
                "type": "ECDSA",
                "curve": "P256",
                "value": "03c31eea1c24ea949e86437ed6ef44b58e5067d25589bf45c92e751d116e4f04f9",
                "pubKeyId": "did:ont:ARMRyKtaukahJgQ4ZTBVhhAByEGPNWip5e#keys-1"
            }
        ]
    },
    "error": 0,
    "action": "getDDO",
    "desc": "SUCCESS",
    "version": "1.0.0"
}
```

| Field_Name | Type   | Description                   |
|:-----------|:-------|:------------------------------|
| error      | int    | 错误码                        |
| action     | String | 动作标志                      |
| desc       | String | 成功返回SUCCESS，失败返回错误描述 |
| result     | String | 成功返回DDO，失败返回""     |
| version    | String | 版本号                        |（）


### 更新ontid的属性

```text
url：/api/v1/ontid/update/attribute
method：POST
```

- 请求：

```json
{
    "ontid":"did:ont:ARMRyKtaukahJgQ4ZTBVhhAByEGPNWip5e",
    "password":"888888",
    "attribute":{
        "key": "key1",
        "valueType": "String",
        "value": "value1"
    }
}
```

| Field_Name | Type   | Description |
|:-----------|:-------|:------------|
| ontid   | String |   实物ontid    |
| password   | String | 实物ontid密码    |
| attribute   | String | 属性    |

- 响应：

```json
{
    "result": true,
    "error": 0,
    "desc": "SUCCESS",
    "action": "updateOntidAttribute",
    "version": "1.0.0"
}
```

| Field_Name | Type   | Description                   |
|:-----------|:-------|:------------------------------|
| error      | int    | 错误码                        |
| action     | String | 动作标志                      |
| desc       | String | 成功返回SUCCESS，失败返回错误描述 |
| result     | String | 成功返回true     |
| version    | String | 版本号                        |

### 删除ontid的属性

```text
url：/api/v1/ontid/delete/attribute
method：POST
```

- 请求：

```json
{
    "ontid":"did:ont:AHYEKDyAcCg968yfxLLyQiD9x9UygxKyhW",
    "password":"888888",
    "path_key":"key1"
}
```

| Field_Name | Type   | Description |
|:-----------|:-------|:------------|
| ontid   | String |   实物ontid    |
| password   | String | 实物ontid密码    |
| path_key   | String | 要删除的属性键值    |

- 响应：

```json
{
    "result": true,
    "error": 0,
    "desc": "SUCCESS",
    "action": "deleteOntidAttribute",
    "version": "1.0.0"
}
```

| Field_Name | Type   | Description                   |
|:-----------|:-------|:------------------------------|
| error      | int    | 错误码                        |
| action     | String | 动作标志                      |
| desc       | String | 成功返回SUCCESS，失败返回错误描述 |
| result     | String | 成功返回true     |
| version    | String | 版本号                        |

### 为ontid添加controller

```text
url：/api/v1/ontid/update/control
method：POST
```

- 请求：

```json
{
    "ontid":"did:ont:AHYEKDyAcCg968yfxLLyQiD9x9UygxKyhW",
    "password":"888888",
    "controlOntid":"did:ont:Aa9Y9fg2taqrP6Jt4nJi8u8PHPWggGzsfd"
}
```

| Field_Name | Type   | Description |
|:-----------|:-------|:------------|
| ontid   | String |   实物ontid    |
| password   | String | 实物ontid密码    |
| controlOntid   | String | control的ontid    |

- 响应：

```json
{
    "result": true,
    "error": 0,
    "desc": "SUCCESS",
    "action": "updateOntidControl",
    "version": "1.0.0"
}
```

| Field_Name | Type   | Description                   |
|:-----------|:-------|:------------------------------|
| error      | int    | 错误码                        |
| action     | String | 动作标志                      |
| version    | String | 版本号                       |
| result     | String | 成功返回true     |
| desc       | String | 成功返回SUCCESS，失败返回错误描述 |

### 通过controller更新ontid的属性

```text
url：/api/v1/ontid/update/attribute/control
method：POST
```

- 请求：

```json
{
    "ontid":"did:ont:AHYEKDyAcCg968yfxLLyQiD9x9UygxKyhW",
    "attribute":{
        "key": "key2",
        "valueType": "String",
        "value": "value2"
    },
    "controlOntid":"did:ont:Aa9Y9fg2taqrP6Jt4nJi8u8PHPWggGzsfd",
    "controlPassword":"999999"
}
```

| Field_Name | Type   | Description |
|:-----------|:-------|:------------|
| ontid   | String |   实物ontid    |
| attribute   | String | 属性    |
| controlOntid   | String | control的ontid    |
| controlPassword   | String | control的ontid密码    |

- 响应：

```json
{
    "error": 0,
    "action": "updateOntidAttributeByControl",
    "version": "1.0.0",
    "result": true,
    "desc": "SUCCESS"
}
```

| Field_Name | Type   | Description                   |
|:-----------|:-------|:------------------------------|
| error      | int    | 错误码                        |
| action     | String | 动作标志                      |
| version    | String | 版本号                       |
| result     | String | 成功返回true     |
| desc       | String | 成功返回SUCCESS，失败返回错误描述 |

### 通过controller删除ontid的属性

```text
url：/api/v1/ontid/delete/attribute/control
method：POST
```

- 请求：

```json
{
    "ontid":"did:ont:AHYEKDyAcCg968yfxLLyQiD9x9UygxKyhW",
    "path_key": "key2",
    "controlOntid":"did:ont:Aa9Y9fg2taqrP6Jt4nJi8u8PHPWggGzsfd",
    "controlPassword":"999999"
}
```

| Field_Name | Type   | Description |
|:-----------|:-------|:------------|
| entityOntid   | String |   实物ontid    |
| path_key   | String | 要删除的属性键值    |
| controlOntid   | String | control的ontid    |
| controlPassword   | String | control的ontid密码    |

- 响应：

```json
{
    "error": 0,
    "action": "deleteOntidAttributeByControl",
    "version": "1.0.0",
    "result": true,
    "desc": "SUCCESS"
}
```

| Field_Name | Type   | Description                   |
|:-----------|:-------|:------------------------------|
| error      | int    | 错误码                        |
| action     | String | 动作标志                      |
| version    | String | 版本号                       |
| result     | String | 成功返回true     |
| desc       | String | 成功返回SUCCESS，失败返回错误描述 |


### 获取总条数

```text
url：/api/v1/ontid/count
method：POST
```

- 请求：

```json
{
	"ontid":"did:ont:AdsCrp9dQy1D6aoFxjDCNm1hnq3Zajq9GE"
}
```

| Field_Name | Type   | Description |
|:-----------|:-------|:------------|
| ontid   | String | 需要查询的ontid    |


- 响应：

```json
{
    "result": 6,
    "error": 0,
    "action": "count",
    "version": "1.0.0",
    "desc": "SUCCESS"
}
```

| Field_Name | Type   | Description                   |
|:-----------|:-------|:------------------------------|
| error      | int    | 错误码                        |
| action     | String | 动作标志                      |
| desc       | String | 成功返回SUCCESS，失败返回错误描述 |
| result     | String | 成功返回总条数，失败返回""
| version    | String | 版本号                     

### 获取历史记录

```text
url：/api/v1/ontid/history
method：POST
```

- 请求：

```json
{
	"ontid":"did:ont:AdsCrp9dQy1D6aoFxjDCNm1hnq3Zajq9GE",
	"pageNum": 1,
	"pageSize": 3
}
```

| Field_Name | Type   | Description |
|:-----------|:-------|:------------|
| ontid   | String | 需要查询的ontid    |
| pageNum   | Integer | 页数，例如：1表示第1页   |
| pageSize   | Integer | 每页记录数，例如：3表示每一页3条记录。该值必须小于10。    |

- 响应：

```json
{
    "result": [
        {
            "ontid": "did:ont:AdsCrp9dQy1D6aoFxjDCNm1hnq3Zajq9GE",
            "control": "did:ont:AdsCrp9dQy1D6aoFxjDCNm1hnq3Zajq9GE",
            "txhash": "bb4d3c87344f7e289c9fbbf7bc114a82037573731dd46fb9db3b49cd948ee6a1",
            "type": 0,
            "createTime": "2019-03-26T06:18:08.000+0000",
            "updateTime": null,
            "detail": "{key=key1, valueType=String, value=value1}"
        },
        {
            "ontid": "did:ont:AdsCrp9dQy1D6aoFxjDCNm1hnq3Zajq9GE",
            "control": "did:ont:AdsCrp9dQy1D6aoFxjDCNm1hnq3Zajq9GE",
            "txhash": "0abcbae70882c93f6da0aa6c06b9234d937069033928a537ef659b5039c0ba34",
            "type": 1,
            "createTime": "2019-03-26T06:19:49.000+0000",
            "updateTime": null,
            "detail": "key1"
        },
        {
            "ontid": "did:ont:AdsCrp9dQy1D6aoFxjDCNm1hnq3Zajq9GE",
            "control": "did:ont:AWXLzhgLNgyGPsyj7uUSRfjEKWBY7HcWmx",
            "txhash": "d1bc778ba62b4541bc67f8317447398d28c02eec6fe8db8be288905ea52d620a",
            "type": 0,
            "createTime": "2019-03-26T06:29:12.000+0000",
            "updateTime": null,
            "detail": "{key=key2, valueType=String, value=value2}"
        }
    ],
    "error": 0,
    "desc": "SUCCESS",
    "action": "getHistory",
    "version": "1.0.0"
}
```

| Field_Name | Type   | Description                   |
|:-----------|:-------|:------------------------------|
| error      | int    | 错误码                        |
| action     | String | 动作标志                      |
| desc       | String | 成功返回SUCCESS，失败返回错误描述 |
| result     | String | 成功返回记录，失败返回""
| version    | String | 版本号                     



### 存证

```text
url：/api/v1/contract/put
method：POST
```

- 请求：

```json
{
	"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJFUzI1NiJ9.eyJhdWQiOiJkaWQ6b250OkFNdmpVV1o2Y25BQVVzQk43dWpBQnRMUzlHbWVoOFNQU2oiLCJpc3MiOiJkaWQ6b250OkFhdlJRcVhlOVByYVY1dFlnQnF2VjRiVXE4TFNzdmpjV1MiLCJleHAiOjE1NTU5OTMzNjAsImlhdCI6MTU1NTkwNjk2MCwianRpIjoiMTYwY2FkNjNmZTdkNGY5MTk3NGFjZjQzYWNlMzkzNmYiLCJjb250ZW50Ijp7InR5cGUiOiJhY2Nlc3NfdG9rZW4iLCJvbnRpZCI6ImRpZDpvbnQ6QWExWFBhcEpIR0dqSFF0TjJIZHliOUFQdjdIZmlZeHRSeiJ9fQ.MDE5MzE3ODk4ODU2MGQ5NGQ3MTBmZTc2Mzg1ZWE0OWRiMmRjZjczZmU2NjAyYjU0NjI2YWE0MmJmZWYwYTFkYTE0ODI5YWVmYTJjNjNlMTA5N2Y2ZjM0YTJlMTJmOGYwNWNmYzRhZWI3NzlkOWEwMWY2NDY1Y2VjYWM1MzNjYjk5Ng",
	"user_ontid":"",
	"filehash":"111175b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927999999",
	"detail":"some message about the file ...",
	"type": "TEXT"
}
```

| Field_Name | Type   | Description |
|:-----------|:-------|:------------|
| access_token   | String | access_token    |
| user_ontid   | String | 空表示自己存证，否则表示被存证    |
| filehash   | String | 文件hash    |
| detail   | String | 文件相关说明    |
| type   | String | INDEX/TEXT/IMAGE/VIDEO   |

- 响应：

```json
{
    "result": true,
    "error": 0,
    "action": "putContract",
    "desc": "SUCCESS",
    "version": "1.0.0"
}
```

| Field_Name | Type   | Description                   |
|:-----------|:-------|:------------------------------|
| error      | int    | 错误码                        |
| action     | String | 动作标志                      |
| desc       | String | 成功返回SUCCESS，失败返回错误描述 |
| result     | String | 成功返回true，失败返回""     |
| version    | String | 版本号                        |


### 批量存证

```text
url：/api/v1/contract/put/batch
method：POST
```

- 请求：

```json
{
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJFUzI1NiJ9.eyJhdWQiOiJkaWQ6b250OkFNdmpVV1o2Y25BQVVzQk43dWpBQnRMUzlHbWVoOFNQU2oiLCJpc3MiOiJkaWQ6b250OkFhdlJRcVhlOVByYVY1dFlnQnF2VjRiVXE4TFNzdmpjV1MiLCJleHAiOjE1NTU5OTMzNjAsImlhdCI6MTU1NTkwNjk2MCwianRpIjoiMTYwY2FkNjNmZTdkNGY5MTk3NGFjZjQzYWNlMzkzNmYiLCJjb250ZW50Ijp7InR5cGUiOiJhY2Nlc3NfdG9rZW4iLCJvbnRpZCI6ImRpZDpvbnQ6QWExWFBhcEpIR0dqSFF0TjJIZHliOUFQdjdIZmlZeHRSeiJ9fQ.MDE5MzE3ODk4ODU2MGQ5NGQ3MTBmZTc2Mzg1ZWE0OWRiMmRjZjczZmU2NjAyYjU0NjI2YWE0MmJmZWYwYTFkYTE0ODI5YWVmYTJjNjNlMTA5N2Y2ZjM0YTJlMTJmOGYwNWNmYzRhZWI3NzlkOWEwMWY2NDY1Y2VjYWM1MzNjYjk5Ng",
    "user_ontid": "did:ont:Aa1XPapJHGGjHQtN2Hdyb9APv7HfiY7890",
    "filelist": [
        {
            "filehash": "e81475b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927777777",
            "type": "INDEX",
            "detail": [
                {
                    "name": "img1",
                    "hash": "e81475b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927888888",
                    "message": ""
                },
                {
                    "name": "img2",
                    "hash": "e81475b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927999999",
                    "message": ""
                },
                {
                    "name": "img3",
                    "hash": "e81475b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927000000",
                    "message": ""
                }
            ]
        },
        {
            "filehash": "e81475b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927888888",
            "type": "IMAGE",
            "detail": [
                {
                    "url": "http://...."
                }
            ]
        },
        {
            "filehash": "e81475b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927999999",
            "type": "IMAGE",
            "detail": [
                {
                    "url": "http://...."
                }
            ]
        },
        {
            "filehash": "e81475b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927000000",
            "type": "IMAGE",
            "detail": [
                {
                    "url": "http://...."
                }
            ]
        }
    ]
}
```

| Field_Name | Type   | Description |
|:-----------|:-------|:------------|
| access_token   | String | access_token|
| user_ontid   | String | 空表示自己存证，否则表示被存证    |
| filelist   | String | 批量文件    |

- 响应：

```json
{
    "result": true,
    "error": 0,
    "action": "putContractBatch",
    "desc": "SUCCESS",
    "version": "1.0.0"
}
```

| Field_Name | Type   | Description                   |
|:-----------|:-------|:------------------------------|
| error      | int    | 错误码                        |
| action     | String | 动作标志                      |
| desc       | String | 成功返回SUCCESS，失败返回错误描述 |
| result     | String | 成功返回true，失败返回""     |
| version    | String | 版本号                        |


### 根据hash取证

```text
url：/api/v1/contract/hash
method：POST
```

- 请求：

```json
{
	"access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJFUzI1NiJ9.eyJhdWQiOiJkaWQ6b250OkFNdmpVV1o2Y25BQVVzQk43dWpBQnRMUzlHbWVoOFNQU2oiLCJpc3MiOiJkaWQ6b250OkFhdlJRcVhlOVByYVY1dFlnQnF2VjRiVXE4TFNzdmpjV1MiLCJleHAiOjE1NTUwNTU3MzksImlhdCI6MTU1NDk2OTMzOSwianRpIjoiZjQ1ZmMyMmVkMjBhNDFhMGE1YzdhMzZhYjIxZTkxNTAiLCJjb250ZW50Ijp7InR5cGUiOiJhY2Nlc3NfdG9rZW4iLCJvbnRpZCI6ImRpZDpvbnQ6QU14clNHSHl4Z25XUzZxYzFRalROWWVFYXczWDNEdnpoZiJ9fQ.MDFiZDVhYWQ2MzRkNzlkOTU3ZjE3YWYyNDc3MDUyZGUxNzJjYjdmYjgxZWViOThmYTg2ODgyM2ZiYjM5ZjIyMjZiYWZlYTlkNGFkNjMwMzM0OWY4N2YyYzBiZDlmNzg5M2IzYjhiYjdkZTg1MjFmYzQ1MDMwOGY2NGRmM2E5ZjkwNg",
	"hash":"e81475b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927102c67"
}
```

| Field_Name | Type   | Description |
|:-----------|:-------|:------------|
| access_token   | String | access_token    |
| hash   | String | 文件hash或者交易hash   |

- 响应：

```json
{
    "result": [
        {
            "ontid": "did:ont:Aa1XPapJHGGjHQtN2Hdyb9APv7HfiYxtRz",
            "companyOntid": "did:ont:Aa1XPapJHGGjHQtN2Hdyb9APv7HfiYxtRz",
            "detail": "some message about the file ...",
            "type": "TEXT",
            "timestamp": "2019-04-22T07:32:57.000+0000",
            "timestampSign": "950ef......",
            "filehash": "111175b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927999999",
            "txhash": "ee973d13c6ed2d8c7391223b4fb6f5c785f402d81d41b02ab7590113cbb00752",
            "createTime": "2019-04-22T07:32:57.000+0000",
            "updateTime": null,
            "height": 1621684
        },
        {
            "ontid": "did:ont:Aa1XPapJHGGjHQtN2Hdyb9APv7HfiY1234",
            "companyOntid": "did:ont:Aa1XPapJHGGjHQtN2Hdyb9APv7HfiYxtRz",
            "detail": "some message about the file ...",
            "type": "TEXT",
            "timestamp": "2019-04-22T07:32:24.000+0000",
            "timestampSign": "960ef......",
            "filehash": "111175b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927999999",
            "txhash": "1ab4b5b2c6c89b4f1a553b7aef30c3f3ef203a323d23cd383261cc6d0df73870",
            "createTime": "2019-04-22T07:32:25.000+0000",
            "updateTime": null,
            "height": 1621682
        },
        {
            "ontid": "did:ont:Aa1XPapJHGGjHQtN2Hdyb9APv7HfiYxtRz",
            "companyOntid": "",
            "detail": "some message about the file ...",
            "type": "TEXT",
            "timestamp": "2019-04-22T04:22:55.000+0000",
            "timestampSign": "950ef......",
            "filehash": "111175b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927999999",
            "txhash": "0437084a4f6204aad88fa1507fc13a44f83cecf44fc925692f9bc43f23e52fc3",
            "createTime": "2019-04-22T04:22:57.000+0000",
            "updateTime": null,
            "height": 1621275
        }
    ],
    "error": 0,
    "desc": "SUCCESS",
    "action": "selectByOntidAndHash",
    "version": "1.0.0"
}
```

| Field_Name | Type   | Description                   |
|:-----------|:-------|:------------------------------|
| error      | int    | 错误码                        |
| action     | String | 动作标志                      |
| desc       | String | 成功返回SUCCESS，失败返回错误描述 |
| result     | String | 成功返回存证记录，失败返回""     |
| version    | String | 版本号                        |


### 获取存证总条数

```text
url：/api/v1/contract/count
method：POST
```

- 请求：

```json
{
		"access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJFUzI1NiJ9.eyJhdWQiOiJkaWQ6b250OkFNdmpVV1o2Y25BQVVzQk43dWpBQnRMUzlHbWVoOFNQU2oiLCJpc3MiOiJkaWQ6b250OkFhdlJRcVhlOVByYVY1dFlnQnF2VjRiVXE4TFNzdmpjV1MiLCJleHAiOjE1NTUwNTU3MzksImlhdCI6MTU1NDk2OTMzOSwianRpIjoiZjQ1ZmMyMmVkMjBhNDFhMGE1YzdhMzZhYjIxZTkxNTAiLCJjb250ZW50Ijp7InR5cGUiOiJhY2Nlc3NfdG9rZW4iLCJvbnRpZCI6ImRpZDpvbnQ6QU14clNHSHl4Z25XUzZxYzFRalROWWVFYXczWDNEdnpoZiJ9fQ.MDFiZDVhYWQ2MzRkNzlkOTU3ZjE3YWYyNDc3MDUyZGUxNzJjYjdmYjgxZWViOThmYTg2ODgyM2ZiYjM5ZjIyMjZiYWZlYTlkNGFkNjMwMzM0OWY4N2YyYzBiZDlmNzg5M2IzYjhiYjdkZTg1MjFmYzQ1MDMwOGY2NGRmM2E5ZjkwNg"
}
```

| Field_Name | Type   | Description |
|:-----------|:-------|:------------|
| ontid   | String | 需要查询的ontid    |
| access_token   | String | access_token    |



- 响应：

```json
{
    "result": 6,
    "error": 0,
    "desc": "SUCCESS",
    "action": "count",
    "version": "1.0.0"
}
```

| Field_Name | Type   | Description                   |
|:-----------|:-------|:------------------------------|
| error      | int    | 错误码                        |
| action     | String | 动作标志                      |
| desc       | String | 成功返回SUCCESS，失败返回错误描述 |
| result     | String | 成功返回总条数，失败返回""
| version    | String | 版本号                     

### 获取存证历史记录

```text
url：/api/v1/contract/history
method：POST
```

- 请求：

```json
{
	"access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJFUzI1NiJ9.eyJhdWQiOiJkaWQ6b250OkFNdmpVV1o2Y25BQVVzQk43dWpBQnRMUzlHbWVoOFNQU2oiLCJpc3MiOiJkaWQ6b250OkFhdlJRcVhlOVByYVY1dFlnQnF2VjRiVXE4TFNzdmpjV1MiLCJleHAiOjE1NTU5OTMzNjAsImlhdCI6MTU1NTkwNjk2MCwianRpIjoiMTYwY2FkNjNmZTdkNGY5MTk3NGFjZjQzYWNlMzkzNmYiLCJjb250ZW50Ijp7InR5cGUiOiJhY2Nlc3NfdG9rZW4iLCJvbnRpZCI6ImRpZDpvbnQ6QWExWFBhcEpIR0dqSFF0TjJIZHliOUFQdjdIZmlZeHRSeiJ9fQ.MDE5MzE3ODk4ODU2MGQ5NGQ3MTBmZTc2Mzg1ZWE0OWRiMmRjZjczZmU2NjAyYjU0NjI2YWE0MmJmZWYwYTFkYTE0ODI5YWVmYTJjNjNlMTA5N2Y2ZjM0YTJlMTJmOGYwNWNmYzRhZWI3NzlkOWEwMWY2NDY1Y2VjYWM1MzNjYjk5Ng",
	"pageNum": 1,
	"pageSize": 3,
	"type":"INDEX"
}
```

| Field_Name | Type   | Description |
|:-----------|:-------|:------------|
| access_token   | String | access_token    |
| pageNum   | Integer | 页数，例如：1表示第1页   |
| pageSize   | Integer | 每页记录数，例如：3表示每一页3条记录。该值必须小于10。    |
| type   | String | INDEX/TEXT/IMAGE/VIDEO，空表示所有类型   |


- 响应：

```json
{
    "result": [
        {
            "ontid": "did:ont:Aa1XPapJHGGjHQtN2Hdyb9APv7HfiY7890",
            "companyOntid": "did:ont:Aa1XPapJHGGjHQtN2Hdyb9APv7HfiYxtRz",
            "detail": "[{\"name\":\"img1\",\"hash\":\"e81475b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927888888\",\"message\":\"\"},{\"name\":\"img2\",\"hash\":\"e81475b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927999999\",\"message\":\"\"},{\"name\":\"img3\",\"hash\":\"e81475b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927000000\",\"message\":\"\"}]",
            "type": "INDEX",
            "timestamp": "2019-04-22T07:50:45.000+0000",
            "timestampSign": "950ef......",
            "filehash": "e81475b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927777777",
            "txhash": "261944dfe5f5e83cac5d9b4c1065f508d7750e66adec85d12cb7415ef5cc1d3a",
            "createTime": "2019-04-22T07:50:46.000+0000",
            "updateTime": null,
            "height": 1621724
        },
        {
            "ontid": "did:ont:Aa1XPapJHGGjHQtN2Hdyb9APv7HfiY7890",
            "companyOntid": "did:ont:Aa1XPapJHGGjHQtN2Hdyb9APv7HfiYxtRz",
            "detail": "null",
            "type": "INDEX",
            "timestamp": "2019-04-22T07:47:22.000+0000",
            "timestampSign": "950ef......",
            "filehash": "e81475b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927777777",
            "txhash": "99c240e7860a6016dd38de4d5fc73ea6ed533c76007a4b314741259b54f0937a",
            "createTime": "2019-04-22T07:47:23.000+0000",
            "updateTime": null,
            "height": 1621714
        },
        {
            "ontid": "did:ont:Aa1XPapJHGGjHQtN2Hdyb9APv7HfiY7890",
            "companyOntid": "did:ont:Aa1XPapJHGGjHQtN2Hdyb9APv7HfiYxtRz",
            "detail": "null",
            "type": "INDEX",
            "timestamp": "2019-04-22T07:42:54.000+0000",
            "timestampSign": "960ef......",
            "filehash": "e81475b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927777777",
            "txhash": "4a70100fa6c5ff6b2b5484493c2c147861772821c50df27db28b01b13bc3a593",
            "createTime": "2019-04-22T07:42:55.000+0000",
            "updateTime": null,
            "height": 1621704
        }
    ],
    "error": 0,
    "desc": "SUCCESS",
    "action": getExplorerHistory,
    "version": "1.0.0"
}
```

| Field_Name | Type   | Description                   |
|:-----------|:-------|:------------------------------|
| error      | int    | 错误码                        |
| action     | String | 动作标志                      |
| desc       | String | 成功返回SUCCESS，失败返回错误描述 |
| result     | String | 成功返回记录，失败返回""
| version    | String | 版本号                     


### 获取浏览器存证历史记录

```text
url：/api/v1/contract/explorer
method：POST
```

- 请求：

```json
{
    "pageNum": 1,
    "pageSize": 10
}
```

| Field_Name | Type   | Description |
|:-----------|:-------|:------------|
| pageNum   | Integer | 页数，例如：1表示第1页   |
| pageSize   | Integer | 每页记录数，例如：3表示每一页3条记录。该值必须小于10。    |

- 响应：

```json
{
    "result": [
        {
            "ontid": "did:ont:AdsCrp9dQy1D6aoFxjDCNm1hnq3Zajq9GE",
            "detail": "some message about the file ...",
            "timestamp": "2019-04-12T09:22:58.000+0000",
            "timestampSign": "960ef049308207...",
            "filehash": "e81475b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927999999",
            "txhash": "2cbe57e08cc467e2fc1bc6a2271052315be74b2b24d03e0d4bff72bae4f1e332",
            "createTime": "2019-04-12T09:22:59.000+0000",
            "updateTime": null,
            "height": 1603800
        },
        {
            "ontid": "did:ont:AdsCrp9dQy1D6aoFxjDCNm1hnq3Zajq9GE",
            "detail": "some message about the file ...",
            "timestamp": "2019-04-12T09:00:56.000+0000",
            "timestampSign": "960ef049308207...",
            "filehash": "e81475b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927102c67",
            "txhash": "5ef7a22bba79353763d7fcd5968cc13e7b8a948021e63034ba8dd437f037f062",
            "createTime": "2019-04-12T09:00:57.000+0000",
            "updateTime": null,
            "height": 1603800
        },
        {
            "ontid": "did:ont:AdsCrp9dQy1D6aoFxjDCNm1hnq3Zajq9GE",
            "detail": "some message about the file ...",
            "timestamp": "2019-04-12T08:35:19.000+0000",
            "timestampSign": "960ef049308207...",
            "filehash": "e81475b25e49f2767522d332057c3e6bb1144c842dce47913dc8222927102c67",
            "txhash": "05960f894360bbfd544ea5767176371cdbff9b083cfabf34e1a20e413f81c7a1",
            "createTime": "2019-04-12T08:35:20.000+0000",
            "updateTime": null,
            "height": 1603800
        }
    ],
    "error": 0,
    "desc": "SUCCESS",
    "action": "getHistory",
    "version": "1.0.0"
}
```

| Field_Name | Type   | Description                   |
|:-----------|:-------|:------------------------------|
| error      | int    | 错误码                        |
| action     | String | 动作标志                      |
| desc       | String | 成功返回SUCCESS，失败返回错误描述 |
| result     | String | 成功返回记录，失败返回""
| version    | String | 版本号              

       
###  司法链存证

```text
url：/api/v1/sfl/put
method：POST
```

- 请求：

```json
{
    "userType": "PERSON",
    "certType": "IDENTITY_CARD",
    "certName": "刘猛",
    "certNo": "412827199405182010",
    "filehash": "33338348b531a08f4cb80b3ccece79ff0b19c0364e0276b6511045b071d35a5b"
}
```

| Field_Name | Type   | Description |
|:-----------|:-------|:------------|
| userType   | String | 用户类型    |
| certType   | String | 证件类型    |
| certName   | String | 证件姓名    |
| certNo   | String | 证件号码    |
| filehash   | String | 文件哈希    |

- 响应：

```json
{
    "result": true,
    "error": 0,
    "action": "putSFL",
    "version": "1.0.0",
    "desc": "SUCCESS"
}
```

### 司法链取证

```text
url：/api/v1/sfl/get
method：POST
```

- 请求：

```json
{
    "certNo": "412827199405182010",
    "pageNum": 1,
    "pageSize": 3
}
```

| Field_Name | Type   | Description |
|:-----------|:-------|:------------|
| certNo   | String | 证件号码    |
| pageNum   | Integer | 页数，例如：1表示第1页   |
| pageSize   | Integer | 每页记录数，例如：3表示每一页3条记录。该值必须小于10。    |

- 响应：

```json
{
    "result": [
        {
            "id": 4,
            "certNo": "412827199405182010",
            "filehash": "33338348b531a08f4cb80b3ccece79ff0b19c0364e0276b6511045b071d35a5b",
            "txhash": "02c59f61d43aef48acbeeae29a652b39c5ef488f59b70ad8323a8771f59bfdc1",
            "certUrl": "http://colima-oss-pro.oss-cn-hangzhou.aliyuncs.com/78943305055427.pdf?Expires=1555670383&OSSAccessKeyId=LTAIy0OdPPzHygy4&Signature=KY8Tgx00C0Ak8qNzTwF7kZQRSFY%3D",
            "confirm": 1,
            "createTime": "2019-04-19T10:37:43.000+0000",
            "updateTime": "2019-04-19T10:38:14.000+0000"
        },
        {
            "id": 3,
            "certNo": "412827199405182010",
            "filehash": "22228348b531a08f4cb80b3ccece79ff0b19c0364e0276b6511045b071d35a5b",
            "txhash": "a75352ab3e88ab70359820f8256733f454b88bcabf0a29bad4a45a0b7761c242",
            "certUrl": "http://colima-oss-pro.oss-cn-hangzhou.aliyuncs.com/78779419452531.pdf?Expires=1555670221&OSSAccessKeyId=LTAIy0OdPPzHygy4&Signature=ckaCCzMDWD3oWlDDVFOHJgskLgc%3D",
            "confirm": null,
            "createTime": "2019-04-19T10:35:02.000+0000",
            "updateTime": null
        },
        {
            "id": 2,
            "certNo": "412827199405182010",
            "filehash": "11118348b531a08f4cb80b3ccece79ff0b19c0364e0276b6511045b071d35a5b",
            "txhash": "66d51a49b9f6cb7159d4ac3c5c6e1384382234b5d393329eb07d12806e1386d1",
            "certUrl": "http://colima-oss-pro.oss-cn-hangzhou.aliyuncs.com/78637363155528.pdf?Expires=1555670077&OSSAccessKeyId=LTAIy0OdPPzHygy4&Signature=7%2FGiUSp29P6GjKabTdWUYpuXu%2FI%3D",
            "confirm": 1,
            "createTime": "2019-04-19T10:32:37.000+0000",
            "updateTime": "2019-04-19T10:32:43.000+0000"
        }
    ],
    "error": 0,
    "action": "getSFL",
    "version": "1.0.0",
    "desc": "SUCCESS"
}
```

| Field_Name | Type   | Description                   |
|:-----------|:-------|:------------------------------|
| error      | int    | 错误码                        |
| action     | String | 动作标志                      |
| desc       | String | 成功返回SUCCESS，失败返回错误描述 |
| result     | String | 成功返回存证记录，失败返回""     |
| version    | String | 版本号  