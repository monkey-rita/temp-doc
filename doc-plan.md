# 质量9000文档进度记录

## 1. 计划部分

### ~~01 立项报告~~
- 页数：8
- 内容：功能描述/技术指标/项目计划
- 预估：2 hour

### ~~02 开发计划~~
- 页数：8
- 内容：项目描述/开发环境/具体开发阶段界定
- 预估：1 hour

### ~~03 配置管理计划~~
- 页数：4
- 内容：简单
- 预估：0.5 hour

### ~~04 质量保证计划~~
- 页数：4
- 内容：简单
- 预估：0.5 hour

### ~~05 设计评审表~~
- 页数：4
- 内容：简单
- 预估：0.5 hour

## 2. 需求部分

### ~~06 需求分析说明书~~
- 页数：8
- 内容：功能描述/技术指标/项目计划
- 注意：需要与02开发计划保持一致
- 预估：2 hour

### ~~07 需求评审记录~~
- 页数：2
- 内容：简单
- 预估：0.5 hour

## 3. 设计部分

### ~~08 概要设计说明书~~
- 页数：6
- 内容：系统说明/构架图 主要是图
- 预估：2 hour

```mermaid
graph TD
A[用户认证模块] --> B[权限管理模块]
B --> C[业主功能模块]
B --> D[业务人员<br>功能模块]
B --> E[业务领导<br>功能模块]
B --> F[物业人员<br>功能模块]

graph LR
A[手机端] --- |认证|B[前端服务器]
B --- |鉴权|C[微信服务器]
A --- |鉴权后|D[后台服务器]
D --- |访问|E[内网数据库]
```

### ~~09 软件产品设计评审表~~
- 页数：2
- 内容：简单
- 预估：0.5 hour

### ~~10 详细设计说明书~~
- 页数：36
- 内容：模块设计详细说明
- 预估：5 hour

获取open_id
```mermaid 获取open_id
sequenceDiagram
    participant A as 手机端
    participant F as 前端服务器
    participant W as 微信服务器

    loop 每75min更新
        F ->> W: appId/secret
        W -->> F: access_token/js_ticket
    end

    A ->> F: code
    F ->> W: code/access_token/appId
    W -->> F: open_id
```

人脸识别
``` mermaid face verify
sequenceDiagram
    participant A as 手机端
    participant F as 前端服务器
    participant W as 微信服务器

    loop 每75min更新
        F ->> W: appId/secret
        W -->> F: access_token/js_ticket
    end

    A ->> F: full url
    F ->> F: 使用url和js_ticket计算签名
    F -->> A: appId/signature
    A ->> W: 使用appId/sig/name/id_no调用人脸识别
    W -->> A: 与公安系统比对结果
```

短信流程
```mermaid text verify
graph LR
    A[手机端] --> |证件类别<br>证件号<br>姓名|B{服务器<br>查找<br>联系方式}
    B --> |有|C[用户选择<br>手机号]
    B --> |无|D[提示用户<br>到维修资金<br>办公室登记]
   C --> |发送<br>验证码|E{验证}
   E --> |正确|F[后台<br>注册]
   E --> |错误|G[提示]

```

业主模块
```mermaid owners
graph LR
    A(业主) --> |1..N|B[房产]
    A --> G[更新联系方式]
    B --> |1..1|C[资金详情]
    B --> |1..N|D[维修项目]
    D --> E[投票表决]
    D --> F[分摊清册]
```

物业模块
```mermaid manager
graph LR
  A(物业人员) --> |1..N|B[小区]
  B --> |1..N|C[维修项目]
  C --> D[投票详情]
  C --> E[投票统计]
```

业务模块
```mermaid operator
graph LR
  A(业务人员) --> |1..N|B[小区]
  B --> |1..N|C[维修项目]
  C --> D[投票详情]
  C --> E[投票统计]
```

### ~~11 详细设计评审记录~~
- 页数：2
- 内容：简单
- 预估：0.5 hour

## 4. 测试部分

### ~~12 测试计划~~
- 页数：6
- 内容：背景/测试阶段性计划
- 预估：1 hour

### ~~13 测试计划评审记录~~
- 页数：2
- 内容：简单
- 预估：0.5 hour

### 14 测试用例
- 页数：34
- 内容：非常多，应要按模板来
- 预估：6 hour

### ~~17 测试报告~~
- 页数：5
- 内容：测试结果
- 预估：1 hour

### ~~使用手册~~
- 注意：需要看是否根据模板修改
- 页数：28
- 预估：1 hour
