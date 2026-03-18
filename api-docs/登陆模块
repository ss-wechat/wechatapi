

# 默认模块

Base URLs:

# Authentication

# 开发API/登录模块

## POST (步骤1)获取登录二维码

POST /login/getLoginQrCode

- appId参数为设备ID，首次登录传空，会自动触发创建设备，掉线后重新登录则必须传接口返回的appId，注意**同一个号避免重复创建设备**，以免触发官方风控

- 如果**IPAD类型扫码登录提示** “在**新设备完成验证以继续登录**” 需要更换type为mac进行登录，切换顺序为ipad-->mac。mac类型可以进行验证，**当mac出现新设备验证时，参考[执行登录接口](https://post.wechatapi.net/login/checklogin)。也可以直接使用mac登录**
- **取码时传的appId需要与上次登录扫码的微信一致，否则会导致登录失败**
>  如果需要全局代理（即所有接口都走代理，可直接在调用的接口内增加" useProxy:true "字段。useproxy字段默认为false不单独展示在各个接口内）但是有可能会影响接口的实时响应速度

<Accordion title="regionId：登陆地区ID，请选择最近的地区（点开展示）。目前支持以下地区："   defaultOpen={false}>
 
**地区ID在前，地区在后**
    - 若目前支持的regionId中没有您所在的地区，可以自行采购socks5协议代理IP，填写到proxyIp参数中
  ```java HelloWorld.java
110000*北京市|120000*天津市|130000*河北省|140000*山西省|150000*内蒙古
210000*辽宁省|220000*吉林省|230000*黑龙江
310000*上海市|320000*江苏省|330000*浙江省|340000*安徽省|350000*福建省|360000*江西省|370000*山东省
410000*河南省|420000*湖北省|430000*湖南省|440000*广东省|450000*广西省|460000*海南省
500000*重庆市|510000*四川省|520000*贵州省|530000*云南省|540000*西藏自治区
610000*陕西省|620000*甘肃省|630000*青海省|640000*宁夏自治区|650000*新疆自治区
  ```
</Accordion>

- 响应结果中的qrImgBase64为二维码图片的base64，前端可使用此值展示给用户扫码。（或使用响应结果中的qrData生成二维码）
- 地区ID仅供测试，如需正常使用业务建议自行购买干净代理ip。

> Body 请求参数

```json
{
  "appId": "",
  "proxyIp": "",
  "regionId": "320000",
  "type": "ipad",
  "ttuid": ""
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|VideosApi-token|header|string| 是 |PS：API后台-点击访问控制-生成Token|
|body|body|object| 否 |none|
|» appId|body|string| 否 |设备ID，首次登录传空，之后传接口返回的appId|
|» proxyIp|body|string| 否 |代理IP 格式：socks5://username:password@123.2.2.2|
|» regionId|body|string| 是 |地区|
|» type|body|string| 是 |设备类型：ipad、mac（默认为ipad。|
|» ttuid|body|string| 否 |代理本机ID，需配合 regionId/proxyIp 使用，不单独使用。可临时借用用户的本地网络取码有50%概率跳过ipad验证。|

#### 详细说明

**» type**: 设备类型：ipad、mac（默认为ipad。
独立appid）

**» ttuid**: 代理本机ID，需配合 regionId/proxyIp 使用，不单独使用。可临时借用用户的本地网络取码有50%概率跳过ipad验证。
[代理TTUID点击下载](https://pan.baidu.com/s/1_lCoPDKSLUW90Ew4yKMyoQ?pwd=1xdt)

> 返回示例

> 200 Response

```json
{
  "ret": 200,
  "msg": "操作成功",
  "data": {
    "qrData": "http://weixin.qq.com/x/oaX6Iz_9w8hiLhJyXQim",
    "qrUrl": "http://api.asilu.com/qrcode/?t=http://weixin.qq.com/x/oaX6Iz_9w8hiLhJyXQim&size=250",
    "qrImgBase64": "data:image/jpg;base64,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",
    "uuid": "oaX6Iz*****LhJyXQim",
    "appId": "wx_ZmxPv*******TB1d35N5r"
  }
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» ret|integer|true|none||none|
|» msg|string|true|none||none|
|» data|object|true|none||响应数据|
|»» qrData|string|true|none||二维码内包含的信息|
|»» qrUrl|string|true|none||二维码直接打开地址|
|»» appId|string|true|none||设备ID|
|»» qrImgBase64|string|true|none||二维码图片base64|
|»» uuid|string|true|none||二维码的uuid|

## POST (步骤2)执行登录

POST /login/checkLogin

- 增加**ipad人脸识别验证**和mac滑块验证，ipad**仅支持IOS平台app扫码**验证，mac滑块验证支持app扫码验证和系统自动验证，开发者集成平台也可自行集成APP滑块验证，具体请点击ipad登录或者mac登录查看详情
- 获取登录二维码**扫码之后**需**每间隔5s调用本接口**来判断是否登录成功，**二维码超时时间为120秒**
**- 登录成功后logininfo有数据，如果没有数据则需要一直执行，直至出现登录数据或者失败为止。**
- 新设备登录平台，次日凌晨会掉线一次，重新登录时需调用[获取二维码且传appId取码](https://post.wechatapi.net/login/getloginqrcode)，登录成功后则可以长期在线
- 登录成功后请保存appId与wxid的对应关系，后续接口中会用到

<Tabs>
  <Tab title="iPad登录" >
    ☝️ 首次登录iPad出现**新设备验证**并且**无数字验证码**此时本接口会返回一个二维码网址，开发者需使用IOS设备下载[认证APP](https://www.pgyer.com/renzhengapp)扫描二维码网址，扫描人脸通过后，再次调用本接口，手机点击确认，则本接口返回登录结果。如果不进行人脸认证则需要切换Mac登录，请查看Mac登录流程
    ☝️ 首次登录iPad出现**新设备验证**并且**有数字验证码**直接在captchCode字段输入数字验证码，继续执行登录即可登录。
      
      
      
<Accordion title="iPad登录流程图，不清楚流程必看，点击此处"  defaultOpen={false} icon="lucide-smartphone" >

<Frame caption="iPad登录流程图，不清楚流程必看">

![image.png](https://api.apifox.com/api/v1/projects/4425884/resources/590083/image-preview)
</Frame>

</Accordion>

  </Tab>
    
    
  <Tab title="Mac登录">
    ☝️  首次登录Mac如果出现新设备验证，可以**选择自动验证**，不需要下载APP。
    ☝️    如果**不选择自动验证**会返回URL。生成二维码之后，需要使用[安卓设备下载APP](https://www.pgyer.com/sdyanzheng-android)，扫码进行图形验证。操作完成后继续调用此接口即可通过新设备验证。
    ☝️用户若有自己平台App，则可代码接入，无需下载App
      
<Accordion title="Mac登录流程图，不清楚流程必看，点击此处" defaultOpen={false} Icon icon="lucide-airplay">

    <Frame caption="Mac登录流程图，不清楚流程必看">
![Mac登录.png](https://api.apifox.com/api/v1/projects/4425884/resources/581306/image-preview)
</Frame>

</Accordion>

  </Tab>
</Tabs>

> Body 请求参数

```json
{
  "appId": "{appid}",
  "uuid": "{uuid}",
  "autoSliding": true
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|VideosApi-token|header|string| 是 |none|
|body|body|object| 否 |none|
|» appId|body|string| 是 |设备ID|
|» proxyIp|body|string| 否 |代理IP 格式：socks5://username:password@123.2.2.2|
|» uuid|body|string| 是 |获取二维码返回的uuid|
|» captchCode|body|string| 否 |扫码后手机提示输入的验证码，如未提示数字验证码可不传此字段。|
|» autoSliding|body|boolean| 是 |是否自动验证true/false，仅限mac使用。true为自动验证，false需要用app扫码验证。如果类型为ipad登录时必须传false。|

> 返回示例

```json
"{\n    \"ret\": 200,\n    \"msg\": \"操作成功\",\n    \"data\": {\n        \"uuid\": \"AfPV********5Mr\",\n        \"headImgUrl\": \"http://wx.qlogo.c****D/0\",\n        \"nickName\": \"苏生-服务支持\",\n        \"expiredTime\": 201,\n        \"status\": 1,\n        \"loginInfo\": null\n    }\n}\n//* 需要图形验证时返回,直接打开链接扫描二维码，使用app扫描验证\n{\n    \"ret\": 200,\n    \"msg\": \"操作成功\",\n    \"data\": {\n        \"url\": \"http://api.asilu.com/qrcode/?t=http://182.40.196.1:8123/s/01K585Y35QPBXD6JMZSNHJZAPZ\"\n    }\n}"
```

```json
{
  "ret": 200,
  "msg": "操作成功",
  "data": {
    "uuid": "obOt*******y-Td_X",
    "headImgUrl": "http://wx.qlogo.cn/mmhead/ver_1/CUPTtZ1ZwiccmeNbxsl8ZaIjWabEoC4bovqxdIszpicEjn8VXayic1dAIT02yJnThun5I9PYjIdCzhQXWglLKh68ibZUCmMzk0YXMDRic1VahOnOjRCA6WtaQPiaeatGtbMIRw6CPsNh7fic4RDyq5bicplQ7Q/0",
    "nickName": "苏生-服务支持",
    "expiredTime": 187,
    "status": 2,
    "loginInfo": {
      "uin": "27****0204",
      "wxid": "wxid_mu****0j7522",
      "nickName": "苏生-服务支持",
      "mobile": "1*******836",
      "alias": "VideosApi"
    }
  }
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» ret|integer|true|none||none|
|» msg|string|true|none||none|
|» data|object|true|none||响应数据|
|»» uuid|string|true|none||二维码的uuid|
|»» headImgUrl|string|true|none||头像地址|
|»» nickName|string|true|none||昵称|
|»» expiredTime|integer|true|none||二维码超时时间|
|»» status|integer|true|none||登录状态 0：未扫码 1：已扫码未登录 2：登录成功 4：已扫码取消登录|
|»» loginInfo|object|true|none||登录成功信息|
|»»» uin|integer|true|none||uin|
|»»» wxid|string|true|none||微信ID，返回此值则是登录成功|
|»»» nickName|string|true|none||昵称|
|»»» mobile|string|true|none||绑定的手机号|
|»»» alias|string|true|none||微信号|

## POST 弹框登录

POST /login/dialogLogin

- 调用本接口后手机会弹框确认登录页面，点确认后调用[执行登录接口](https://post.wechatapi.net/login/checklogin)检测是否登录成功

<Accordion title="regionId：微信登陆地区ID，登录时请选择最近的地区，目前支持以下地区：" defaultClose>
 
**地区ID在前，地区在后**
  ```java HelloWorld.java
110000*北京市|120000*天津市|130000*河北省|140000*山西省|150000*内蒙古
210000*辽宁省|220000*吉林省|230000*黑龙江
310000*上海市|320000*江苏省|330000*浙江省|340000*安徽省|350000*福建省|360000*江西省|370000*山东省
410000*河南省|420000*湖北省|430000*湖南省|440000*广东省|450000*广西省|460000*海南省
500000*重庆市|510000*四川省|520000*贵州省|530000*云南省|540000*西藏自治区
610000*陕西省|620000*甘肃省|630000*青海省|640000*宁夏自治区|650000*新疆自治区
  ```
</Accordion>

- 若目前支持的regionId中没有您所在的地区，可以自行采购socks5协议代理IP，填写到proxyIp参数中
- 使用本接口登录并非100%成功，本接口返回失败后，可通过扫码登录的方式登录
    - 以下几种情况无法使用本接口登录：
        - 手机点击退出登录
        - 新设备登录次日
        - 官方风控下线

> Body 请求参数

```json
{
  "appId": "{appid}",
  "proxyIp": "",
  "regionId": "{regionId}"
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|VideosApi-token|header|string| 是 |none|
|body|body|object| 否 |none|
|» appId|body|string| 是 |设备ID|
|» proxyIp|body|string| 是 |代理IP 格式：socks5://username:password@123.2.2.2|
|» regionId|body|string| 是 |地区|

> 返回示例

> 200 Response

```json
{
  "ret": 200,
  "msg": "操作成功",
  "data": {
    "appId": "wx_wR_U4zPj2M_OTS3BCyoE4",
    "uuid": "4dmHZZMtoLbHoLZwd1wE"
  }
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» ret|integer|true|none||none|
|» msg|string|true|none||none|
|» data|object|true|none||响应数据|
|»» appId|string|true|none||设备ID|
|»» uuid|string|true|none||二维码uuid，执行登录时会用到|

## POST 退出

POST /login/logout

可以只填写appid或者按照示例直接传即可

> Body 请求参数

```json
{
  "appId": "{appid}",
  "proxyIp": "",
  "regionId": "88"
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|VideosApi-token|header|string| 是 |none|
|body|body|object| 否 |none|
|» appId|body|string| 是 |设备ID|

> 返回示例

> 200 Response

```json
{
  "ret": 200,
  "msg": "操作成功"
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» ret|integer|true|none||none|
|» msg|string|true|none||none|

## POST 检查是否在线

POST /login/checkOnline

响应结果的data=true则是在线，反之为离线

> Body 请求参数

```json
{
  "appId": "{{appid}}"
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|VideosApi-token|header|string| 是 |none|
|body|body|object| 否 |none|
|» appId|body|string| 是 |设备ID|

> 返回示例

> 200 Response

```json
{
  "ret": 200,
  "msg": "操作成功",
  "data": true
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» ret|integer|true|none||none|
|» msg|string|true|none||none|
|» data|boolean|true|none||none|

## POST 异常断线重连

POST /login/reconnection

1.手机显示账号在线，后台离线2.收不到消息回调。调用此接口

> Body 请求参数

```json
{
  "appId": ""
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|VideosApi-token|header|string| 是 |none|
|body|body|object| 否 |none|
|» appId|body|string| 是 |设备ID|

> 返回示例

> 200 Response

```json
{
  "ret": 200,
  "msg": "操作成功",
  "data": true
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» ret|integer|true|none||none|
|» msg|string|true|none||none|
|» data|boolean|true|none||none|

## POST 无感切换代理ip

POST /login/setProxy

账号更换代理ip，可实现在线切换。
也可退出后重新登录传新的代理ip。

> Body 请求参数

```json
{
  "appId": "{{appid}}",
  "proxyIp": "socks5://x:x@111.153.185.21:11332"
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|VideosApi-token|header|string| 是 |none|
|body|body|object| 否 |none|
|» appId|body|string| 是 |设备ID|
|» proxyIp|body|string| 是 |代理ip|

> 返回示例

> 200 Response

```json
{
  "ret": 200,
  "msg": "操作成功"
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» ret|integer|true|none||none|
|» msg|string|true|none||none|

# 数据模型

