# Bug Salted Fish Store 
这个是基于YII2和BUG所写的商城

##-----------------数据库的设计------------------

用户表
if 表前缀== ??

??Users----用户表
[

uid
user_name
password
email
status  //枚举型的状态 1 表示未验证邮箱 2表示正常 3 表示给禁用
tel
sex
age
address---地址
add_time---注册时间
last_time---上次登录时间


]

??comment --评论表
[
user_id 
goods_id
content---内容
shedTime---发送时间
status--- 1未审核 2通过 3拒绝 4垃圾箱
]

??Category---分类表
[
cid
cat_name
keywords---分类关键字
cat_desc---分类介绍
filter_attr----分类属性 改属性为数组 序列化后保存 serialize函数 json也可以
parent_id-----父分类id

]

??goods ---商品
[
goods_id
goods_name
cat_id---分类id
click_count---点击量
goods_number---库存
goods_price----价格
keywords---商品关键字
goods_desc---商品详细说明
is_hot---是否热门
is_new---是否新品
is_promote---是否推荐
a_time---添加时间
u_time---更新时间
images----图片地址
thumb_50   50x50缩略图一下如图
thumb_100
thumb_200
brief----商品简介 这里用百度编辑器？

]

??attribute 属性表
[
attri_id
cat_id
attr_name
attr_input_type 属性类型 枚举型  1 是input  2为select  3为radio  如果是select或者radio则读取attr_val的数据 默认 1 ---后台用
attr_val 这里用;区分格个数据 例如 xl;xll;xlll
]

??attribute_data 属性的值
[
goods_attr_id
goods_id
attr_val 属性
attr_type  1----为text只显示 2为select下拉框可以选择 3 为radio
]

??cart 购物车
[
user_id
session_id--cookie标识符
goods_id
goods_price--商品单价
qty----数量
]

订单信息
order_info
[
order_id
user_id
order_sn----订单编号
status---订单信息 1 未未付款 2 为已付款 3为取消 4为退货中 5为已退货
add_time---订单时间
order_price--订单价格
reminder_time---(7 OR 15 OR 30 天 发邮件给客户提醒付款，卖铁块的商城实现了，我们这里有空再实现)
]

##-------方案---------------------
  后台功能一览表

1用户信息
 已注册用户
用户帐号密码身份证邮箱性别年龄电话号住址注册时间上次登陆时间（按钮封禁解封黑名单对它留言（邮箱走起））
禁止用户（禁止时间）（违规信息）
购买过商品的用户

商品信息
	
被购买商品
被退货商品
列表
退货信息
	是否同意
添加商品
		添加分类（如户外，食品，衣服）
		商品名称图片信息描述分类（可选上面的分类）价格适用人群
		推荐位：是否首页推荐是否分类页推荐
推荐位置管理（已推荐商品排序）
	删除推荐商品
		首页推荐位管理
		分类页推荐位管理
	排行榜
		列表
		指定某商品进入排行榜
		排行榜排序
权限rbac 留着以后写
     *管理关信息 （各种注册信息） 按钮 全县给与 删除权限
	管理员信息修改
接口控制
各种接口程序
 物流信息  
     查询物流 
     已收货商品 
未收货商品



