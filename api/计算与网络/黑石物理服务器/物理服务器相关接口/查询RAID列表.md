## 功能描述

DescribeDeviceClassRaid接口用来获取设备类型对应的RAID方式。(过期的接口，不推荐使用，不支持自定义机型的RAID列表。 推荐使用[DescribeDeviceClassPartition接口](/document/api/386/7370)。

接口访问域名：<font style="color:red">bm.api.qcloud.com</font>

## 请求

### 请求示例

```
https://bm.api.qcloud.com/v2/index.php?
	Action=DescribeDeviceClassRaid
	&<<a href="https://cloud.tencent.com/doc/api/229/6976">公共请求参数</a>>
```

### 请求参数
正式调用时需要加上公共请求参数，此接口的Action字段为DescribeDeviceClassRaid。

## 响应

### 响应示例

```
{
    "code": 0,
    "message": "",
    "codeDesc": "Success",
    "data": {
        "B6": {
            "1": {
                "deviceClass": "B6",
                "raidId": "1",
                "diskSize": "600G",
                "partition": {
                    "/": 10,
                    "swap": 2,
                    "/usr/local": 20,
                    "data": 568
                },
                "unFormatPartition": "",
                "raid": "RAID0",
                "raidDisplay": "RAID 0",
                "description": "所有盘组成RAID 0，读取速度快，但没有冗余，适用于读取要求很高，数据安全要求低的应用"
            }
        },
        "M10": {
            "1": {
                "deviceClass": "M10",
                "raidId": "1",
                "diskSize": "3600G",
                "partition": {
                    "/": 10,
                    "swap": 2,
                    "/usr/local": 20,
                    "data": 3568
                },
                "unFormatPartition": "",
                "raid": "RAID0",
                "raidDisplay": "RAID 0",
                "description": "所有盘组成RAID 0，读取速度快，但没有冗余，适用于读取要求很高，数据安全要求低的应用"
            },
            "2": {
                "deviceClass": "M10",
                "raidId": "2",
                "diskSize": "3300G",
                "partition": {
                    "/": 10,
                    "swap": 2,
                    "/usr/local": 20,
                    "data": 3268
                },
                "unFormatPartition": "",
                "raid": "RAID5",
                "raidDisplay": "RAID 5",
                "description": "所有盘组成RAID 5， 是兼顾存储性能、数据安全和存储成本的方案，适合读多写少的场景"
            }
        }
    }
}
```

### 响应参数

响应参数部分包含两层结构，外层展示接口的响应结果，内层展示具体的接口内容，包括机型对应的RAID方式信息。

| 参数名称    | 类型     | 描述                                       |
| ------- | ------ | ---------------------------------------- |
| code    | Int    | 错误码，0：成功，其他值：失败，具体含义参见[错误码](/doc/api/456/6725)。 |
| message | String | 错误信息。                                    |
| data    | Object | 各机型的RAID信息。具体结构描述如data结构所示。              |

data结构

| 参数名称             | 类型     | 描述                                       |
| ---------------- | ------ | ---------------------------------------- |
| 机型（例如"M10"，"B6"） | Object | 以机型为key，对应的值为对象，对象为该机型支持的RAID信息。具体结构描述如RAIDLIST结构所示。 |

RAIDLIST结构

| 参数名称               | 类型     | 描述                                       |
| ------------------ | ------ | ---------------------------------------- |
| RAID ID（例如"1"，"2"） | Object | 以RAID ID为key，对应的值为对象，对象为RAID信息的描述。具体结构描述如RAID结构所示。 |


RAID结构

| 参数名称              | 类型     | 描述                             |
| ----------------- | ------ | ------------------------------ |
| deviceClass       | String | 机型，如M10，B6。                    |
| raidId            | String | RAID ID。                       |
| diskSize          | String | 硬盘大小。                          |
| partition         | Object | 分区信息，单位为GB。以分区名为key，对应的值为分区大小。 |
| unFormatPartition | String | 未格式化分区，默认为没有。                  |
| raid              | String | RAID级别。                        |
| raidDisplay       | String | RAID级别显示名称。                    |
| description       | String | 描述。                            |

## 错误码
| 错误码  | 英文提示                  | 错误描述    |
| ---- | --------------------- | ------- |
| 9001 | InternalError.DbError | 操作数据库错误 |


## 实际案例

### 输入
```
https://bm.api.qcloud.com/v2/index.php?
	Action=DescribeDeviceClassRaid
	&SecretId=AKID52SKw5uMEy3jhpMUBqSylEBJBby6E0KC
	&Nonce=48476
	&Timestamp=1476436689
	&Region=bj
	&Signature=afRlJQ0disdT97B7uIfVB4v2KWo%3D
```
### 输出
```
{
    "code": 0,
    "message": "",
    "codeDesc": "Success",
    "data": {
        "B6": {
            "1": {
                "deviceClass": "B6",
                "raidId": "1",
                "diskSize": "600G",
                "partition": {
                    "/": 10,
                    "swap": 2,
                    "/usr/local": 20,
                    "data": 568
                },
                "unFormatPartition": "",
                "raid": "RAID0",
                "raidDisplay": "RAID 0",
                "description": "所有盘组成RAID 0，读取速度快，但没有冗余，适用于读取要求很高，数据安全要求低的应用"
            }
        },
        "M10": {
            "1": {
                "deviceClass": "M10",
                "raidId": "1",
                "diskSize": "3600G",
                "partition": {
                    "/": 10,
                    "swap": 2,
                    "/usr/local": 20,
                    "data": 3568
                },
                "unFormatPartition": "",
                "raid": "RAID0",
                "raidDisplay": "RAID 0",
                "description": "所有盘组成RAID 0，读取速度快，但没有冗余，适用于读取要求很高，数据安全要求低的应用"
            },
            "2": {
                "deviceClass": "M10",
                "raidId": "2",
                "diskSize": "3300G",
                "partition": {
                    "/": 10,
                    "swap": 2,
                    "/usr/local": 20,
                    "data": 3268
                },
                "unFormatPartition": "",
                "raid": "RAID5",
                "raidDisplay": "RAID 5",
                "description": "所有盘组成RAID 5，是兼顾存储性能、数据安全和存储成本的方案，适合读多写少的场景"
            }
        }
    }
}
```
