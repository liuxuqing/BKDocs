
### 请求地址

/api/c/compapi/v2/cc/batch_update_host/



### 请求方法

POST


### 功能描述

根据主机 id 和属性批量更新主机属性（不能用于更新主机属性中的云区域字段）

### 请求参数


#### 通用参数

| 字段 | 类型 | 必选 |  描述 |
|-----------|------------|--------|------------|
| bk_app_code  |  string    | 是 | 应用 ID     |
| bk_app_secret|  string    | 是 | 安全密钥(应用 TOKEN)，可以通过 蓝鲸智云开发者中心 -&gt; 点击应用 ID -&gt; 基本信息 获取 |
| bk_token     |  string    | 否 | 当前用户登录态，bk_token 与 bk_username 必须一个有效，bk_token 可以通过 Cookie 获取 |
| bk_username  |  string    | 否 | 当前用户用户名，应用免登录态验证白名单中的应用，用此字段指定当前用户 |

#### 接口参数

| 字段                |  类型         | 必选   |  描述                           |
|---------------------|--------------|--------|---------------------------------|
| update              | object array | 是     | 主机被更新的属性和值，最多 500 条   |

#### update
| 字段        | 类型    | 必选   | 描述                                                |
|-------------|--------|--------|----------------------------------------------------|
| properties  | object | 是     | 主机被更新的属性和值，不能用于更新主机属性中的云区域字段 |
| bk_host_id  | int    | 是     | 用于更新的主机 ID                                     |

#### properties
| 字段         | 类型   | 必选   | 描述                                                      |
|--------------|--------|-------|-----------------------------------------------------------|
| bk_host_name | string | 否    | 主机名，也可以为其它属性，不能用于更新主机属性中的云区域字段    |
| operator     | string | 否    | 主要维护人，也可以为其它属性，不能用于更新主机属性中的云区域字段 |
| bk_comment   | string | 否    | 备注，也可以为其它属性，不能用于更新主机属性中的云区域字段      |
| bk_isp_name  | string | 否    | 所属运营商，也可以为其它属性，不能用于更新主机属性中的云区域字段 |



### 请求参数示例

```json
{
    "bk_supplier_account":"0",
    "update":[
      {
        "properties":{
          "bk_host_name":"batch_update",
          "operator": "admin",
          "bk_comment": "test",
          "bk_isp_name": "1"
        },
        "bk_host_id":46
      }
    ]
}
```


### 返回结果示例

```json
{
    "result": true,
    "code": 0,
    "message": "success",
    "data": null
}
```