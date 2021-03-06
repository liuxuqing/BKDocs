
### 请求地址

/api/c/compapi/v2/job/execute_job/



### 请求方法

POST


### 功能描述

根据执行方案 ID 启动作业执行方案。

### 请求参数


#### 通用参数

| 字段 | 类型 | 必选 |  描述 |
|-----------|------------|--------|------------|
| bk_app_code  |  string    | 是 | 应用 ID     |
| bk_app_secret|  string    | 是 | 安全密钥(应用 TOKEN)，可以通过 蓝鲸智云开发者中心 -&gt; 点击应用 ID -&gt; 基本信息 获取 |
| bk_token     |  string    | 否 | 当前用户登录态，bk_token 与 bk_username 必须一个有效，bk_token 可以通过 Cookie 获取 |
| bk_username  |  string    | 否 | 当前用户用户名，应用免登录态验证白名单中的应用，用此字段指定当前用户 |

#### 接口参数

| 字段      |  类型      | 必选   |  描述      |
|-----------|------------|--------|------------|
| bk_biz_id   |  long       | 是     | 业务 ID |
| bk_job_id   |  long       | 是     | 作业执行方案 ID |
| global_vars |  array     | 否     | 全局变量信息，作业执行方案包含的全局变量和类型，可以通过接口“查询作业执行方案详情” (get_job_detail)获取。对于作业执行方案中的全局变量值，如果 global_vars 包含该变量信息，那么会使用 api 指定的值；否则使用全局变量默认值 |
| bk_callback_url |  string  | 否     | 回调 URL，当任务执行完成后，JOB 会调用该 URL 告知任务执行结果。回调协议参考 callback_protocol 组件文档 |

#### global_vars

| 字段      |  类型      | 必选   |  描述      |
|-----------|------------|--------|------------|
| id               |  long     | 否     | 全局变量 id，唯一标识。如果 id 为空，那么使用 name 作为唯一标识 |
| name             |  string   | 否     | 全局变量 name |
| value            |  string   | 否     | 全局变量值。如果使用主机变量，请使用 target_server |
| custom_query_id  |  array    | 否     | *deprecated*，请使用 target_server.dynamic_group_id_list 替代。配置平台上的自定义分组 ID |
| ip_list          |  array    | 否     | *deprecated*，请使用 target_server.iplist 替代。静态 IP 列表 |
| target_server    |  dict     | 否     | 目标服务器 |

#### target_server
| 字段      |  类型      | 必选   |  描述      |
|-----------|------------|--------|------------|
| ip_list               | array | 否     | 静态 IP 列表 |
| dynamic_group_id_list | array | 否     | 动态分组 ID 列表 |
| topo_node_list        | array | 否     | 动态 topo 节点列表 |

#### ip_list

| 字段      |  类型      | 必选   |  描述      |
|-----------|------------|--------|------------|
| bk_cloud_id |  int    | 是     | 云区域 ID |
| ip          |  string | 是     | IP 地址 |

#### topo_node_list
| 字段      |  类型      | 必选   |  描述      |
|-----------|------------|--------|------------|
| id               | long   | 是     | 动态 topo 节点 ID，对应 CMDB API 中的 bk_inst_id |
| node_type        | string | 是     | 动态 topo 节点类型，对应 CMDB API 中的 bk_obj_id,比如"module","set"|

### 请求参数示例

```python
{
    "bk_app_code": "esb_test",
    "bk_app_secret": "xxx",
    "bk_token": "xxx",
    "bk_biz_id": 1,
    "bk_job_id": 100,
    "global_vars": [{
            "id": 436,
            "target_server": {
                "dynamic_group_id_list": ["blo8gojho0skft7pr5q0", "blo8gojho0sabc7priuy"],
                "ip_list": [{
                        "bk_cloud_id": 0,
                        "ip": "10.0.0.1"
                    }, {
                        "bk_cloud_id": 0,
                        "ip": "10.0.0.2"
                    }
                ],
                "topo_node_list": [{
                        "id": 1000,
                        "node_type": "module"
                    }
                ]
            }
        }, {
            "id": 437,
            "value": "new String value"
        }
    ]
}
```

### 返回结果示例

```python
{
    "result": true,
    "code": 0,
    "message": "success",
    "data": {
        "job_instance_name": "Test",
        "job_instance_id": 10000
    }
}
```