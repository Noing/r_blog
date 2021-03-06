# 更新日志

----

### 2019-01-04

- 新增：
	- 数据库支持emoji表情，解决抓取文章时如果文章中存在emoji表情导致保存失败的问题
- 修改：
	- 将redis的配置挪到具体的profile中，每个环境下的redis配置应该是不相同的
	- 将数据库初始化语句单独提出到init_data.sql，方便一键还原数据库
	- 文章列表页批量发布后刷新列表页
	- zyd.table.js中去掉了表格上方的修改内容列和视图切换的按钮（并没什么卵用），同时将默认的glyphicon图标修改为font-awesome图标
	- 用户操作日志表中单独记录请求参数，并且将参数改为json格式
- 删除：
	- 删除一些无用的文件


----

### 2018-10-10

- 新增：
	- 图片转存功能支持CSDN
	- “文章搬运工”可选的停止方式：
		- 默认：不做限制，抓取所有匹配到的文章，慎用
        - 持续时间：按照爬虫运行的时间，理想状态时1s抓取一条，受实际网速影响
        - 链接条数：按照指定的条数抓取，满足条数后程序自动停止
	- 日志管理，记录用户的操作日志
- 修改：
	- 建站日期提到配置文件中，可手动配置。通过buildWebsiteDate指定建站起始日期，默认2018-01-01
	- 文章管理页调整，去掉不重要的列，增加一键开关，使之更加便于管理
	- 重构后台管理的首页，显示重要的信息：文章数、标签数等数量统计和文章分类统计、爬虫统计等
	- 部分页面调优
	- 文章分类页的排序
- 删除：
	- 删除CnblogModel等无用的测试实体类
- 修复其他一些bug
	

----

### 2018-09-11

- “文章搬运工”支持博客园的文章迁移
- “文章搬运工”已支持自动转存文章图片到七牛云，只需在“文章搬运工”中手动开启**自动转存图片**即可

*注：转存图片功能尚不能转存csdn的图片，下一版会更新*

----

### 2018-08-29

**新增**
- wangEditor编辑器添加复制粘贴图片的功能

----

### 2018-08-24

**新增**
- 新增“文章搬运工”功能，支持博客文章一键迁移，示例见：[视频演示](https://gitee.com/yadong.zhang/static/raw/master/dblog/DBlog-%E6%96%87%E7%AB%A0%E6%90%AC%E8%BF%90%E5%B7%A5%E7%A4%BA%E4%BE%8B.webm)

----

### 2018-07-20

**改进**
- 集成YUI compressor实现js、css文件的自动压缩


----

### 2018-07-15

**修复**
- 解决使用rememberme时偶发性出现重定向错误的问题。
- 解决rememberme无效的问题。



----

### 2018-07-13

**修复**
- 解决wangEditor编辑器下图片丢失的问题。造成原因：上传完图片如果未进行其他操作，则不会触发编辑器的“change”事件，导致实际文章内容中缺少最后上传的图片文件


----

### 2018-07-05

**修改功能：**

修改：      
- config表中新增`cmd_url`字段，存储后台管理系统的地址  
- websocket支持移到admin模块
- 添加了管理员向在线用户端发送消息通知的功能（需用户端授权）

   
----

### 2018-06-27

**修改功能：**

优化：      
- @blogHeader宏标签数据动态获取      
- 开启websocket的逻辑调优，host从config表中获取    
- 项目readme文档完善并拆分    
- 项目maven版本修改为`2.0.1.Beta`

增加：
- ISSUE和PR的模板    

----

### 2018-06-20

**修改功能：**

优化：  
- 升级Spring Boot至2.0.1版本及其他关联版本升级；  
- 使用Maven Profile管理Spring Boot Profiles，支持动态切换profile；

----

### 2018-06-10

**修改功能：**

新增：    
- markdown版的编辑器、评论框    
- 控制文章的评论框是否显示    
- 修改密码功能    
优化：相关页面进行优化    

----

### 2018-06-05

**修改功能：**

修复： admin用户首页报错的问题    

优化：
1. ROOT用户默认拥有所有权限
2. admin页面改为macro引用的方式
3. 登录界面
4. 日志记录

----

### 2018-05-25

**修改功能：**

1. 修复后台标签等分页失败的问题
2. 修复前台自动申请友链失败的问题
3. 其他一些问题

----

### 2018-05-22

**修改功能：**

1. 完善shiro权限（数据库、页面）。注：需要重新执行下`sys_resources`和`sys_role_resources`两张表的`insert`语句
2. redis配置默认不含密码（鉴于大多数朋友的redis都没有密码做此修改，不过本人 **强烈建议**设置下密码）

----

### 2018-05-18

**修复bug：**

1. web端自动申请友链后不显示的问题
2. config表修改后不能实时刷新的问题
	
**增加功能：**
1. 网站赞赏码
2. 百度推送功能(链接提交到百度站长平台)
	
**修改功能：**
1. 百度api的ak和百度推送的token以及七牛云的配置改为通过config表管理
3. admin模块菜单通过标签实时获取
3. 弹窗工具类js结构调整
