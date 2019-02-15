
# Qtoken商户功能接口文档

- [说明](#说明)
- [币种列表](#币种列表)
- [联系方式详情](#联系方式详情)
- [添加、编辑联系方式](#添加、编辑联系方式)
- [商户交易列表](#商户交易列表)
- [设置支付宝](#设置支付宝)
- [设置微信](#设置微信)
- [商户订单列表](#商户订单列表)
- [广告列表](#广告列表)
- [发布广告](#发布广告)
- [编辑广告](#编辑广告)
- [广告上架/下架](#广告上架/下架)
- [商户买入](#商户买入)

## 说明
1.测试网址：http://cs.qtoken.info/<br>
2.传参方式必须是post<br>
3.接口地址区分大小写

## 币种列表
接口地址：blog/api/curr_list

返回值：

| 字段名称				| 描述		|
| :---------------| :-------|
| id							| 币种ID	|
| name						| 名称		|
| image						| 图标		|

Json数据：

```json
# 成功
{
  "code": 1,
  "msg": "ok",
  "data": {
    "count": 5,
    "list": [
      {
        "id": 1,
        "name": "QT",
        "image": ""
      },
      {
        "id": 2,
        "name": "RJTC",
        "image": ""
      }
    ]
  }
}
```

## 联系方式详情
接口地址：blog/api/contact_way

请求参数：

| 参数名称		| 是否必须	| 类型			| 描述			| 默认值		| 取值范围	|
| :--------		| :--------	| :--------	| :--------	| :--------	| :--------	|
| member_id		| true			| number		| 会员ID		|						|						|
| access_token| true			| string		| 访问令牌	|						|						|

返回值：

| 字段名称				| 描述				|
| :---------------| :-------		|
| email						| 邮箱				|
| qq							| QQ号码			|
| alipay					| 支付宝账号	|
| wechat					| 微信账号		|
| whatsapp				| whatsApp账号|
| telegram				| telegram账号|
| skype						| skype账号		|
| other						| 其它				|
| phone						| 手机号			|

Json数据：

```json
# 成功
{
  "code": 1,
  "msg": "ok",
  "data": {
    "email": "",
    "qq": "",
    "alipay": "",
    "wechat": "",
    "whatsapp": "",
    "telegram": "",
    "skype": "",
    "other": "",
    "phone": "13679126041"
  }
}

# 失败
{
  "code": 0,
  "msg": "网络异常"
}
```

## 添加、编辑联系方式
接口地址：blog/api/contact_add

请求参数：

| 参数名称		| 是否必须	| 类型			| 描述			| 默认值		| 取值范围	|
| :--------		| :--------	| :--------	| :--------	| :--------	| :--------	|
| member_id		| true			| number		| 会员ID		|						|						|
| access_token| true			| string		| 访问令牌	|						|						|
| email				| false			| string		| 邮箱			|						|						|
| qq					| false			| string		| QQ号码		|						|						|
| alipay			| false			| string		| 支付宝		|						|						|
| wechat			| false			| string		| 微信			|						|						|
| whatsapp		| false			| string		| WhatsApp	|						|						|
| telegram		| false			| string		| Telegram	|						|						|
| skype				| false			| string		| Skype			|						|						|
| other				| false			| string		| 其它			|						|						|

Json数据：

```json
# 成功
{
  "code": 1,
  "msg": "联系方式修改成功"
}

# 失败
{
  "code": 0,
  "msg": "网络异常"
}
```

## 商户交易列表
接口地址：blog/api/trans_list

请求参数：

| 参数名称	| 是否必须	| 类型			| 描述			| 默认值		| 取值范围		|
| :--------	| :--------	| :--------	| :--------	| :--------	| :--------		|
| page			| false			| number		| 页数			| 1					|							|
| limit			| false			| number		| 每页条数	| 10				|							|
| diff			| false			| number		| 类型			| 1					| 1买入，2卖出|

返回值：

| 字段名称				| 描述																|
| :---------------| :-------														|
| id							| 广告ID															|
| nickname				| 昵称																|
| price						| 单价																|
| volume_30				| 30天成交量													|
| limit_num				| 限额																|
| num							| 数量																|
| pay_type				| 支付方式（1银行卡，2支付宝，3微信）	|
| remark					| 备注ID															|

Json数据：

```json
# 成功
{
  "code": 1,
  "msg": "ok",
  "data": {
    "count": 11,
    "list": [
      {
        "id": 11,
        "nickname": "么么哒",
        "price": "3.50",
        "volume_30": 99,
        "limit_num": "500.00-3000.00",
        "num": "1600",
        "pay_type": "1,2",
        "remark": "非诚勿扰"
      },
      {
        "id": 10,
        "nickname": "比例了",
        "price": "3.50",
        "volume_30": 99,
        "limit_num": "500.00-3000.00",
        "num": "1600",
        "pay_type": "1,2,3",
        "remark": "量大从优，物美价廉。"
      }
    ]
  }
}

# 失败
{
  "code": 0,
  "msg": "网络异常"
}
```

## 设置支付宝
接口地址：blog/api/alipay

请求参数：

| 参数名称		| 是否必须	| 类型			| 描述			| 默认值		| 取值范围	|
| :--------		| :--------	| :--------	| :--------	| :--------	| :--------	|
| member_id		| true			| number		| 会员ID		|						|						|
| access_token| true			| string		| 访问令牌	|						|						|
| ali_code		| false			| number		| 支付宝账号|						|						|
| ali_pic			| false			| 图片			| 支付二维码|						|						|

1)详情：当只传入member_id和access_token时，返回值：

| 字段名称				| 描述			|
| :---------------| :-------	|
| id							| ID				|
| ali_code				| 支付宝账号|
| ali_pic					| 支付二维码|

2)设置：当参数都传入时，返回值：

```
{
  "code": 1,
  "msg": "支付宝设置成功"
}
```

Json数据：

```json
# 详情
{
  "code": 1,
  "msg": "ok",
  "data": {
    "id": 2,
    "ali_code": "2222ddd",
    "ali_pic": "\/static\/uploads\/alipay\/20190131\/alipay_middle_1548898892273308.jpg"
  }
}

# 设置
{
  "code": 1,
  "msg": "支付宝设置成功"
}

# 失败
{
  "code": 0,
  "msg": "网络异常"
}
```

## 设置微信
接口地址：blog/api/wechat

请求参数：

| 参数名称		| 是否必须	| 类型			| 描述			| 默认值		| 取值范围	|
| :--------		| :--------	| :--------	| :--------	| :--------	| :--------	|
| member_id		| true			| number		| 会员ID		|						|						|
| access_token| true			| string		| 访问令牌	|						|						|
| wx_code			| false			| number		| 微信账号	|						|						|
| wx_pic			| false			| 图片			| 支付二维码|						|						|

1)详情：当只传入member_id和access_token时，返回值：

| 字段名称				| 描述			|
| :---------------| :-------	|
| id							| ID				|
| wx_code					| 微信账号	|
| wx_pic					| 支付二维码|

2)设置：当参数都传入时，返回值：

```
{
  "code": 1,
  "msg": "微信设置成功"
}
```

Json数据：

```json
# 详情
{
  "code": 1,
  "msg": "ok",
  "data": {
    "id": 2,
    "wx_code": "36212252ddd",
    "wx_pic": "\/static\/uploads\/wechat\/20190131\/wechat_middle_1548898760815743.jpg"
  }
}

# 设置
{
  "code": 1,
  "msg": "微信设置成功"
}

# 失败
{
  "code": 0,
  "msg": "网络异常"
}
```

## 商户订单列表
接口地址：blog/api/order_list

请求参数：

| 参数名称		| 是否必须	| 类型			| 描述			| 默认值		| 取值范围																																								|
| :--------		| :--------	| :--------	| :--------	| :--------	| :--------																																								|
| member_id		| true			| number		| 会员ID		|						|																																													|
| access_token| true			| string		| 访问令牌	|						|																																													|
| page				| false			| number		| 页数			| 1					|																																													|
| limit				| false			| number		| 每页条数	| 10				|																																													|
| diff				| false			| number		| 类型			| 1					| 1买入，2卖出																																						|
| status			| false			| number		| 状态			| 0					| 0全部，1等待接单，2未支付，3已付款，4已完成，<br>5已取消，6申诉中，7拒绝接单，8接单超时	|

返回值：

| 字段名称				| 描述																																							|
| :---------------| :-------																																					|
| id							| 订单ID																																								|
| order_num				| 订单号																																						|
| price						| 单价																																							|
| num							| 数量																																							|
| total						| 金额总计																																					|
| c_type					| 币种																																							|
| create_at				| 添加时间																																					|
| merchant_id			| 商户ID																																						|
| status					| 状态：1等待接单，2未支付，3已付款，4已完成，5已取消，6申诉中，7拒绝接单，8接单超时|
| status_cn				| 状态说明																																					|

Json数据：

```json
# 成功
{
  "code": 1,
  "msg": "ok",
  "data": {
    "count": 9,
    "list": [
      {
        "id": 27,
        "order_num": "Q_20190214160737165991",
        "price": "1.05",
        "num": "2.5",
        "total": "2.63",
        "c_type": "QT",
        "create_at": "2019-02-14 16:07:37",
        "merchant_id": 10,
        "status": 1,
        "status_cn": "等待接单"
      },
      {
        "id": 26,
        "order_num": "Q_20190214155643602126",
        "price": "1.05",
        "num": "3",
        "total": "3.15",
        "c_type": "QT",
        "create_at": "2019-02-14 15:56:43",
        "merchant_id": 10,
        "status": 1,
        "status_cn": "等待接单"
      }
    ]
  }
}

# 失败
{
  "code": 0,
  "msg": "网络异常"
}
```

## 广告列表
接口地址：blog/api/advert_list

请求参数：

| 参数名称		| 是否必须	| 类型			| 描述			| 默认值		| 取值范围											|
| :--------		| :--------	| :--------	| :--------	| :--------	| :--------											|
| member_id		| true			| number		| 会员ID		|						|																|
| access_token| true			| string		| 访问令牌	|						|																|
| page				| false			| number		| 页数			| 1					|																|
| limit				| false			| number		| 每页条数	| 10				|																|
| diff				| false			| number		| 类型			| 1					| 1买入，2卖出									|
| status			| false			| number		| 状态			| 0					| 0全部，1上架，2下架，3已完成。|

返回值：

| 字段名称				| 描述									|
| :---------------| :-------							|
| id							| 广告ID										|
| price						| 单价									|
| num							| 数量									|
| c_type					| 币种									|
| create_at				| 添加时间							|
| bought					| 已买入的							|
| status					| 1上架，2下架，3已完成	|
| status_cn				| 状态说明							|

Json数据：

```json
# 成功
{
  "code": 1,
  "msg": "ok",
  "data": {
    "count": 11,
    "list": [
      {
        "id": 33,
        "price": "1.05",
        "num": "2.008",
        "c_type": "QT",
        "bought": "0",
        "create_at": "2018-12-15 18:41:35",
        "status": 1,
        "status_cn": "上架"
      },
      {
        "id": 32,
        "price": "0.00",
        "num": "0",
        "c_type": null,
        "bought": "0",
        "create_at": "2018-12-15 18:41:35",
        "status": 1,
        "status_cn": "上架"
      }
    ]
  }
}

# 失败
{
  "code": 0,
  "msg": "网络异常"
}
```

## 发布广告
接口地址：blog/api/advert_add

请求参数：

| 参数名称		| 是否必须	| 类型			| 描述			| 默认值		| 取值范围								|
| :--------		| :--------	| :--------	| :--------	| :--------	| :--------								|
| member_id		| true			| number		| 会员ID		|						|													|
| access_token| true			| string		| 访问令牌	|						|													|
| diff				| false			| number		| 类型			| 1					|1买入，2卖出							|
| c_type			| true			| number		| 币种			|						|													|
| price				| true			| float			| 单价			| 0					|													|
| num					| true			| float			| 数量			| 0					|													|
| min_num			| true			| float			| 最小成交额| 0					|													|
| max_num			| true			| float			| 最大成交额| 0					|													|
| remark			| true			| string		| 备注			|						|													|
| pay_type		| true			| number		| 支付方式	|						| 1银行卡，2支付宝，3微信	|

Json数据：

```json
# 成功
{
  "code": 1,
  "msg": "发布成功"
}

# 失败
{
  "code": 0,
  "msg": "网络异常"
}
```

## 编辑广告
接口地址：blog/api/advert_edit

请求参数：

| 参数名称		| 是否必须	| 类型			| 描述			| 默认值		| 取值范围								|
| :--------		| :--------	| :--------	| :--------	| :--------	| :--------								|
| member_id		| true			| number		| 会员ID		|						|													|
| access_token| true			| string		| 访问令牌	|						|													|
| ad_id				| true			| number		| 广告ID		|						|													|
| c_type			| true			| number		| 币种			|						|													|
| price				| true			| float			| 单价			| 0					|													|
| num					| true			| float			| 数量			| 0					|													|
| min_num			| true			| float			| 最小成交额| 0					|													|
| max_num			| true			| float			| 最大成交额| 0					|													|
| remark			| true			| string		| 备注			|						|													|
| pay_type		| true			| number		| 支付方式	|						| 1银行卡，2支付宝，3微信	|

1)详情：当只传入member_id、access_token、ad_id时，返回值：

| 字段名称				| 描述														|
| :---------------| :-------												|
| id							| 广告ID													|
| price						| 单价														|
| num							| 数量														|
| min_num					| 最小成交额											|
| max_num					| 最大成交额											|
| remark					| 备注														|
| pay_type				| 支付方式：1网银，2支付宝，3微信	|

2)编辑：当参数都传入时，返回值
```
{
  "code": 1,
  "msg": "编辑成功"
}
```

Json数据：

```json
# 详情
{
  "code": 1,
  "msg": "ok",
  "data": {
    "id": 39,
    "price": "3.33",
    "num": "1.992",
    "min_num": "500",
    "max_num": "6500",
    "remark": "ddd",
    "pay_type": "1,3"
  }
}

# 成功
{
  "code": 1,
  "msg": "编辑成功"
}

# 失败
{
  "code": 0,
  "msg": "网络异常"
}
```

## 广告上架/下架
接口地址：blog/api/shelves

请求参数：

| 参数名称		| 是否必须	| 类型			| 描述			| 默认值		| 取值范围		|
| :--------		| :--------	| :--------	| :--------	| :--------	| :--------		|
| member_id		| true			| number		| 会员ID		|						|							|
| access_token| true			| string		| 访问令牌	|						|							|
| ad_id				| true			| number		| 广告ID		|						|							|
| status			| true			| number		| 状态			|						|1上架，2下架	|

Json数据：

```json
# 成功
{
  "code": 1,
  "msg": "下架成功"
}

# 失败
{
  "code": 0,
  "msg": "网络异常"
}
```

## 商户买入
接口地址：blog/api/advert_buy

请求参数：

| 参数名称		| 是否必须	| 类型			| 描述			| 默认值		| 取值范围		|
| :--------		| :--------	| :--------	| :--------	| :--------	| :--------		|
| member_id		| false			| number		| 会员ID		|						|							|
| access_token| false			| string		| 访问令牌	|						|							|
| diff				| false			| number		| 类型			|						|1买入，2卖出	|
| num					| false			| float			| 数量			| 0					|							|
| ad_id				| true			| number		| 广告ID		|						|							|

1)详情：当只传入ad_id时，返回值：

| 字段名称				| 描述															|
| :---------------| :-------													|
| id							| 广告ID														|
| price						| 单价															|
| num							| 数量															|
| c_type					| 币种															|
| pay_type				| 支付方式：1银行卡，2支付宝，3微信	|
| limit_num				| 交易限额													|

2)买入：当参数都传入时，返回值

| 字段名称				| 描述		|
| :---------------| :-------|
| data						| 订单ID	|

Json数据：

```json
# 详情
{
  "code": 1,
  "msg": "ok",
  "data": {
    "id": 35,
    "price": "1.05",
    "num": "2.008",
    "c_type": "RJTC",
    "pay_type": "2",
    "limit_num": "100.5-5000"
  }
}

# 成功
{
  "code": 1,
  "msg": "买入成功",
  "data": "27"
}

# 失败
{
  "code": 0,
  "msg": "网络异常"
}
```