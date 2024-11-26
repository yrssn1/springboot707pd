# springboot062购物推荐网站的设计与实现

## 简介

本代码仅供学习参考使用

加QQ(**3055269939**)免费获取项目和论文

## 主要内容

### 数据库设计表

东大每日推购物推荐网站需要后台数据库，下面介绍数据库中的各个表的详细信息：

 

表4.1 地址

| 字段      | 类型         | 空   | 默认              | 注释                |
| --------- | ------------ | ---- | ----------------- | ------------------- |
| id (主键) | bigint(20)   | 否   |                   | 主键                |
| addtime   | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间            |
| userid    | bigint(20)   | 否   |                   | 用户id              |
| address   | varchar(200) | 否   |                   | 地址                |
| name      | varchar(200) | 否   |                   | 收货人              |
| phone     | varchar(200) | 否   |                   | 电话                |
| isdefault | varchar(200) | 否   |                   | 是否默认地址[是/否] |

表4.2 购物车表

| 字段          | 类型         | 空   | 默认              | 注释     |
| ------------- | ------------ | ---- | ----------------- | -------- |
| id (主键)     | bigint(20)   | 否   |                   | 主键     |
| addtime       | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| tablename     | varchar(200) | 是   | shangpinxinxi     | 商品表名 |
| userid        | bigint(20)   | 否   |                   | 用户id   |
| goodid        | bigint(20)   | 否   |                   | 商品id   |
| goodname      | varchar(200) | 是   | NULL              | 商品名称 |
| picture       | varchar(200) | 是   | NULL              | 图片     |
| buynumber     | int(11)      | 否   |                   | 购买数量 |
| price         | float        | 是   | NULL              | 单价     |
| discountprice | float        | 是   | NULL              | 会员价   |

表4.3 商品信息评论表

| 字段      | 类型         | 空   | 默认              | 注释     |
| --------- | ------------ | ---- | ----------------- | -------- |
| id (主键) | bigint(20)   | 否   |                   | 主键     |
| addtime   | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| refid     | bigint(20)   | 否   |                   | 关联表id |
| userid    | bigint(20)   | 否   |                   | 用户id   |
| nickname  | varchar(200) | 是   | NULL              | 用户名   |
| content   | longtext     | 否   |                   | 评论内容 |
| reply     | longtext     | 是   | NULL              | 回复内容 |

表4.4 购物资讯

| 字段         | 类型         | 空   | 默认              | 注释     |
| ------------ | ------------ | ---- | ----------------- | -------- |
| id (主键)    | bigint(20)   | 否   |                   | 主键     |
| addtime      | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| title        | varchar(200) | 否   |                   | 标题     |
| introduction | longtext     | 是   | NULL              | 简介     |
| picture      | varchar(200) | 否   |                   | 图片     |
| content      | longtext     | 否   |                   | 内容     |

表4.5 订单

| 字段          | 类型         | 空   | 默认              | 注释          |
| ------------- | ------------ | ---- | ----------------- | ------------- |
| id (主键)     | bigint(20)   | 否   |                   | 主键          |
| addtime       | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间      |
| orderid       | varchar(200) | 否   |                   | 订单编号      |
| tablename     | varchar(200) | 是   | shangpinxinxi     | 商品表名      |
| userid        | bigint(20)   | 否   |                   | 用户id        |
| goodid        | bigint(20)   | 否   |                   | 商品id        |
| goodname      | varchar(200) | 是   | NULL              | 商品名称      |
| picture       | varchar(200) | 是   | NULL              | 商品图片      |
| buynumber     | int(11)      | 否   |                   | 购买数量      |
| price         | float        | 否   | 0                 | 价格/积分     |
| discountprice | float        | 是   | 0                 | 折扣价格      |
| total         | float        | 否   | 0                 | 总价格/总积分 |
| discounttotal | float        | 是   | 0                 | 折扣总价格    |
| type          | int(11)      | 是   | 1                 | 支付类型      |
| status        | varchar(200) | 是   | NULL              | 状态          |
| address       | varchar(200) | 是   | NULL              | 地址          |
| tel           | varchar(200) | 是   | NULL              | 电话          |
| consignee     | varchar(200) | 是   | NULL              | 收货人        |

表4.6 商品类型

| 字段            | 类型         | 空   | 默认              | 注释     |
| --------------- | ------------ | ---- | ----------------- | -------- |
| id (主键)       | bigint(20)   | 否   |                   | 主键     |
| addtime         | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| shangpinleixing | varchar(200) | 是   | NULL              | 商品类型 |

表4.7 商品销售排行榜

| 字段              | 类型         | 空   | 默认              | 注释     |
| ----------------- | ------------ | ---- | ----------------- | -------- |
| id (主键)         | bigint(20)   | 否   |                   | 主键     |
| addtime           | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| shangpinbianhao   | varchar(200) | 是   | NULL              | 商品编号 |
| shangpinmingcheng | varchar(200) | 是   | NULL              | 商品名称 |
| shangpinleixing   | varchar(200) | 是   | NULL              | 商品类型 |
| shangpintupian    | varchar(200) | 是   | NULL              | 商品图片 |
| yuexiaoshouliang  | int(11)      | 是   | NULL              | 月销售量 |

表4.8 商品信息

| 字段              | 类型         | 空   | 默认              | 注释         |
| ----------------- | ------------ | ---- | ----------------- | ------------ |
| id (主键)         | bigint(20)   | 否   |                   | 主键         |
| addtime           | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间     |
| shangpinbianhao   | varchar(200) | 是   | NULL              | 商品编号     |
| shangpinmingcheng | varchar(200) | 是   | NULL              | 商品名称     |
| shangpinleixing   | varchar(200) | 是   | NULL              | 商品类型     |
| tupian            | varchar(200) | 是   | NULL              | 图片         |
| shangpinxiangqing | longtext     | 是   | NULL              | 商品详情     |
| clicktime         | datetime     | 是   | NULL              | 最近点击时间 |
| price             | float        | 否   |                   | 价格         |

表4.9 收藏表

| 字段      | 类型         | 空   | 默认              | 注释     |
| --------- | ------------ | ---- | ----------------- | -------- |
| id (主键) | bigint(20)   | 否   |                   | 主键     |
| addtime   | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| userid    | bigint(20)   | 否   |                   | 用户id   |
| refid     | bigint(20)   | 是   | NULL              | 收藏id   |
| tablename | varchar(200) | 是   | NULL              | 表名     |
| name      | varchar(200) | 否   |                   | 收藏名称 |
| picture   | varchar(200) | 否   |                   | 收藏图片 |

表4.10 管理员表

| 字段      | 类型         | 空   | 默认              | 注释     |
| --------- | ------------ | ---- | ----------------- | -------- |
| id (主键) | bigint(20)   | 否   |                   | 主键     |
| username  | varchar(100) | 否   |                   | 用户名   |
| password  | varchar(100) | 否   |                   | 密码     |
| role      | varchar(100) | 是   | 管理员            | 角色     |
| addtime   | timestamp    | 否   | CURRENT_TIMESTAMP | 新增时间 |

表4.11 用户

| 字段         | 类型         | 空   | 默认              | 注释     |
| ------------ | ------------ | ---- | ----------------- | -------- |
| id (主键)    | bigint(20)   | 否   |                   | 主键     |
| addtime      | timestamp    | 否   | CURRENT_TIMESTAMP | 创建时间 |
| zhanghao     | varchar(200) | 否   |                   | 账号     |
| mima         | varchar(200) | 否   |                   | 密码     |
| xingming     | varchar(200) | 是   | NULL              | 姓名     |
| xingbie      | varchar(200) | 是   | NULL              | 性别     |
| shouji       | varchar(200) | 是   | NULL              | 手机     |
| shenfenzheng | varchar(200) | 是   | NULL              | 身份证   |
| zhaopian     | varchar(200) | 是   | NULL              | 照片     |
| money        | float        | 是   | 0                 | 余额     |