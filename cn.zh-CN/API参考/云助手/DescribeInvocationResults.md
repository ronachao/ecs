# DescribeInvocationResults {#DescribeInvocationResults .reference}

查看云助手命令的执行结果，即在指定 ECS 实例中的实际输出信息（`Output`）。

## 描述 {#section_nlv_qq4_ydb .section}

当您使用接口 [DescribeInvocations](cn.zh-CN/API参考/云助手/DescribeInvocations.md#) 查看命令执行状态后，如果返回参数 `InvokeStatus` 为 `Finished`，仅表示命令进程执行完成，不代表一定有预期的命令效果，您需要通过 [DescribeInvocationResults](cn.zh-CN/API参考/云助手/DescribeInvocationResults.md#) 中的参数 `Output` 查看实际的具体执行结果，以实际输出结果为准。

## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：DescribeInvocationResults|
|RegionId|String|是|地域 ID。您可以调用 [DescribeRegions](cn.zh-CN/API参考/地域/DescribeRegions.md#) 查看最新的阿里云地域列表。|
|CommandId|String|否|命令 ID。您可以通过接口 [DescribeCommands](cn.zh-CN/API参考/云助手/DescribeCommands.md#) 查询所有可用的 `CommandId`。|
|InstanceId|String|否|实例 ID。|
|InvokeId|String|否|命令进程执行 ID。您可以通过接口 [DescribeInvocations](cn.zh-CN/API参考/云助手/DescribeInvocations.md#) 查询所有的 `InvokeId`。|
|InvokeRecordStatus|String|否|您所要查询的何种状态下的命令进程。取值范围：-   Running：命令进程进行中
-   Failed：命令进程执行失败，命令进程出现超时情况或者其他异常
-   Finished：命令进程执行完成
-   Stopped：命令进程被手动停止

|
|PageNumber|Integer|否|当前页码，起始值：1默认值：1

|
|PageSize|Integer|否|分页查询时设置的每页行数，最大值：50默认值：10

|

## 返回参数 {#ResponseParameter .section}

|名称|类型|描述|
|:-|:-|:-|
|TotalCount|Integer|命令总个数|
|PageNumber|Integer|查询结果的页码|
|PageSize|Integer|每页行数|
|InvocationResults|Array|命令执行结果集（[`InvocationResultSetType`](#InvocationResultSetType)）|

 **命令执行结果集 InvocationResultSetType** 

|名称|类型|描述|
|:-|:-|:-|
|InvocationResult|Array|实例执行结果类型（[`InvocationResultType`](#InvocationResultType)）（如果是一次性执行，则只有一个结果）|

**实例执行结果类型 InvocationResultType** 

|名称|类型|描述|
|:-|:-|:-|
|CommandId|String|命令 ID|
|InvokeId|String|执行 ID|
|InstanceId|String|实例 ID|
|FinishedTime|String|命令进程的完成时间。如果命令进程出现超时情况，命令进程的完成时间以 [CreateCommand](cn.zh-CN/API参考/云助手/CreateCommand.md#) 中指定的参数 `TimedOut` 为准|
|InvokeRecordStatus|String|命令进程的执行状态：-   Running：命令进程进行中
-   Failed：命令进程执行失败，命令进程出现超时情况或者其他异常
-   Finished：命令进程执行完成
-   Stopped：命令进程被手动停止

|
|Output|String|命令进程完成后的实际结果，输出内容以 Base64 编码的形式传输|
|ExitCode|Integer|命令进程的退出码：-   Linux 实例为 Shell 进程的退出码
-   Windows实例为 Bat 或者 PowerShell 进程的退出码

|

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=DescribeInvocationResults
&RegionId=cn-hangzhou
&<公共请求参数>
```

**正常返回示例** 

**XML 格式**

```
<DescribeInvocationResultsResponse>
    <TotalCount>5</TotalCount>
    <PageNumber>1</PageNumber>
    <PageSize>5</PageSize>
    <InvocationResults>
        <InvocationResult>
            <FinishedTime>2018-01-05 15:45:02</FinishedTime>
            <InvokeRecordStatus>finished</InvokeRecordStatus>
            <InstanceId>i-uf614fhehhzmxxxxxxxx</InstanceId>
            <InvokeId>t-001937b74e2a4242891fc789xxxxxxxx</InvokeId>
            <Output>MTU6NDU6MDEK</Output>
            <CommandId>c-6b0fb9d72adc421abab462abxxxxxxxx</CommandId>
            <ExitCode>0</ExitCode>
        </InvocationResult>
        <InvocationResult>
            <FinishedTime>2018-01-05 15:40:02</FinishedTime>
            <InvokeRecordStatus>finished</InvokeRecordStatus>
            <InstanceId>i-uf614fhehhzmxxxxxxxx</InstanceId>
            <InvokeId>t-a8935b93739442e59ed621a6xxxxxxxx</InvokeId>
            <Output> </Output>
            <CommandId>c-e67505b2be3e477dae94c0f0xxxxxxxx</CommandId>
            <ExitCode>0</ExitCode>
        </InvocationResult>
        <InvocationResult>
            <FinishedTime>2018-01-05 15:30:02</FinishedTime>
            <InvokeRecordStatus>finished</InvokeRecordStatus>
            <InstanceId>i-uf614fhehhzmxxxxxxxx</InstanceId>
            <InvokeId>t-001937b74e2a4242891fc78xxxxxxxx</InvokeId>
            <Output>MTU6MzA6MDEK</Output>
            <CommandId>c-6b0fb9d72adc421abab462abxxxxxxxx</CommandId>
            <ExitCode>0</ExitCode>
        </InvocationResult>
        <InvocationResult>
            <FinishedTime>2018-01-05 15:20:02</FinishedTime>
            <InvokeRecordStatus>finished</InvokeRecordStatus>
            <InstanceId>i-uf614fhehhzmxxxxxxxx</InstanceId>
            <InvokeId>t-a8935b93739442e59ed621a6xxxxxxxx</InvokeId>
            <Output> </Output>
            <CommandId>c-e67505b2be3e477dae94c0f0xxxxxxxx</CommandId>
            <ExitCode>0</ExitCode>
        </InvocationResult>
        <InvocationResult>
            <FinishedTime>2018-01-05 15:15:02</FinishedTime>
            <InvokeRecordStatus>finished</InvokeRecordStatus>
            <InstanceId>i-uf614fhehhzmxxxxxxxx</InstanceId>
            <InvokeId>t-001937b74e2a4242891fc789xxxxxxxx</InvokeId>
            <Output>MTU6MTU6MDEK</Output>
            <CommandId>c-6b0fb9d72adc421abab462abxxxxxxxx</CommandId>
            <ExitCode>0</ExitCode>
        </InvocationResult>
        </InvocationResults>
    <RequestId>567FA138-6026-47C6-A299-5D50xxxxxxxx</RequestId>
</DescribeInvocationResultsResponse>
```

 **JSON 格式** 

```
{
    "Invocation": {
        "TotalCount": 5,
        "PageNumber": 1,
        "InvocationResults": {
            "InvocationResult": [
                {
                    "FinishedTime": "2018-01-05 15:45:02",
                    "InvokeRecordStatus": "finished",
                    "InstanceId": "i-uf614fhehhzmxxxxxxxx",
                    "InvokeId": "t-001937b74e2a4242891fc789xxxxxxxx",
                    "Output": "MTU6NDU6MDEK",
                    "CommandId": "c-6b0fb9d72adc421abab462abxxxxxxxx",
                    "ExitCode": 0
                },
                {
                    "FinishedTime": "2018-01-05 15:40:02",
                    "InvokeRecordStatus": "finished",
                    "InstanceId": "i-uf614fhehhzmxxxxxxxx",
                    "InvokeId": "t-a8935b93739442e59ed621a6xxxxxxxx",
                    "Output": "",
                    "CommandId": "c-e67505b2be3e477dae94c0f0xxxxxxxx",
                    "ExitCode": 0
                },
                {
                    "FinishedTime": "2018-01-05 15:30:02",
                    "InvokeRecordStatus": "finished",
                    "InstanceId": "i-uf614fhehhzmxxxxxxxx",
                    "InvokeId": "t-001937b74e2a4242891fc78xxxxxxxx",
                    "Output": "MTU6MzA6MDEK",
                    "CommandId": "c-6b0fb9d72adc421abab462abxxxxxxxx",
                    "ExitCode": 0
                },
                {
                    "FinishedTime": "2018-01-05 15:20:02",
                    "InvokeRecordStatus": "finished",
                    "InstanceId": "i-uf614fhehhzmd3zj4k74",
                    "InvokeId": "t-a8935b93739442e59ed621a6xxxxxxxx",
                    "Output": "",
                    "CommandId": "c-e67505b2be3e477dae94c0f0xxxxxxxx",
                    "ExitCode": 0
                },
                {
                    "FinishedTime": "2018-01-05 15:15:02",
                    "InvokeRecordStatus": "finished",
                    "InstanceId": "i-uf614fhehhzmd3zj4k74",
                    "InvokeId": "t-001937b74e2a4242891fc789xxxxxxxx",
                    "Output": "MTU6MTU6MDEK",
                    "CommandId": "c-6b0fb9d72adc421abab462abxxxxxxxx",
                    "ExitCode": 0
                }
            ]
        },
        "PageSize": 5
    },
    "RequestId": "567FA138-6026-47C6-A299-5D50xxxxxxxx"
}
```

**异常返回示例** 

**XML 格式**

```
<Error>
    <RequestId>540CFF28-407A-40B5-B6A5-74Bxxxxxxxxx</RequestId>
    <HostId>ecs.aliyuncs.com</HostId>
    <Code>MissingParameter.RegionId</Code>
    <Message>The input parameter “RegionId” that is mandatory for processing this request is not supplied.</Message>
</Error>
```

 **JSON 格式** 

```
{
    "RequestId": "540CFF28-407A-40B5-B6A5-74Bxxxxxxxxx",
    "HostId": "ecs.aliyuncs.com"
    "Code": "MissingParameter.RegionId"
    "Message": "The input parameter “RegionId” that is mandatory for processing this request is not supplied."
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.aliyun.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|MissingParameter.RegionId|The input parameter “RegionId” that is mandatory for processing this request is not supplied.|400|您必须指定必需参数 `RegionId`，或者您暂时不能使用指定 `RegionId` 里的资源。|
|InvalidRegionId.NotFound|The RegionId provided does not exist in our items.|404|指定的 `RegionId` 不存在。|
|InternalError.Dispatch|An internal error occurred when dispatch the request.|500|内部错误，请稍后尝试。|

