# AddCasterProgram {#concept_opd_4hd_pfb .concept}

添加导播台节目单。

## 请求参数 {#section_wbs_wdd_pfb .section}

|参数|类型|是否必选|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：AddCasterProgram|
|CasterId|String|是|导播台Id|
|Episodes|\[\]Episode|是|节目列表|

**Episode**

|参数|类型|是否必须|描述|
|:-|:-|:---|:-|
|EpisodeType|String|是|节点类型。-   Resource-视频源
-   Component-组件

|
|EpisodeName|String|是|节目名称|
|ResourceId|String|否|视频源Id。-   若节点类型为Resource时有效且必输，
-   若节点类型为Component无效。

|
|ComponentIds|String\[\]|否|组件列表。按照元素顺序由下而上排列，组件将与视频源同步切换

-   若类型为Component时必输，
-   若类型为Resource时，输入表示组件与视频源绑定并同步切换。

|
|StartTime|String|是|起始时间。-   UTC 格式，
-   例如：2016-06-29T19:00:00Z

|
|EndTime|String|是|结束时间。-   UTC 格式，
-   例如：2016-06-29T19:00:02Z

|
|SwitchType|String|否|切换策略。节点类型为Resource-视频源时有效

-   TimeFirst-时间优先，
-   ContentFirst-内容优先，

直播类视频源只允许采用时间优先。|

## 返回参数 {#section_fz3_12d_pfb .section}

|参数|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id|
|EpisodeIds|String\[\]|节目ID列表，列表中元素顺序和传入节目顺序保持一致|

## 示例 {#section_l4v_c2d_pfb .section}

请求示例

```
https://live.aliyuncs.com?Action=AddCasterProgram&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49&Episodes.1.EpisodeName=节目1&Episodes.1.EpisodeType=Resource&Episodes.1.EpisodeName=program_name_1&Episodes.1.ResourceId=a2b8e671-2fe5-4642-a2ec-bf93880e1a41&Episodes.1.StartTime=2016-06-29T19:00:00Z&Episodes.1.EndTime=2016-06-29T19:02:00Z&Episodes.1.SwitchType=TimeFirst&Episodes.2.EpisodeName=节目2&Episodes.2.EpisodeType=Component&Episodes.2.EpisodeName=program_name_2&Episodes.2.ComponentIds.1=a2b8e671-2fe5-4642-a2ec-bf9318267364&Episodes.2.ComponentIds.2=a2b8e671-2fe5-4642-a2ec-283837482726&Episodes.2.StartTime=2016-06-29T19:02:00Z&Episodes.2.EndTime=2016-06-29T19:04:00Z&<公共请求参数>
```

返回示例

```
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
    "EpisodeIds": [
      "16A96B9A-F203-4EC5-8E43-CB92E68F1321",
      "16A96B9A-F203-4EC5-8E43-CB92E6887362"
    ]
}
```

## 特殊错误码 {#section_ktw_22d_pfb .section}

|错误代码|描述|Http状态码|语义|
|:---|:-|:------|:-|
|PermissionDenied|Permission Denied|401|无权访问导播台|
|InvalidCaster.NotFound|Caster is not found.|404|指定导播台不存在|
|InternalError|InternalError|500|内部错误|

