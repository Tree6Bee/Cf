# cf
the Ctx php framework.

#### todo

//php 版本最低要求5.3
* session 必须调整为中间件，不然没办法灵活的调整
* 新增 Response validate Cookie Session 类,controller基类
* 中间件采用类似laravel的方式，url 为 requst 里边的 module/controller/action 来进行匹配
* csrf 中间件
* Contracts 类细分为多个文件夹
* /sample 增加 config 配置样例和 nginx 配置范例(web,static,upload三种环境下的配置)


=== 待整理 ===
# 框架

1. 主要思想

    * 脚手架工具，检测环境（需要的扩展，框架应用文件夹及 修改文件夹权限为合适的权限），框架文件夹检测并生成，常见配置（nginx rewirte daxian.ren 指向 www.daxian.ren 静态域名和上传文件夹缓存相关配置 图片配置防盗链 防止用ip直接访问服务器）
    * 技术选型 centos  + nginx + php + mysql + redis + mongodb + 定时任务
    * 静态文件采用独立的域名，上传文件夹是另一个域名，这两个域名，不做php解析，防止上传的东西被执行，同时为了方便做 cdn
    * session 采用 缓存 存放 （配置决定）
    * codebase 方便 前台 | 后台 | 脚本 都调用到，调用方式 包括 require 和 http （curl） 两种
        * moa
        * goback
    * 常见的安全处理
    * 支持 api 请求方式，支持数据加密，设置 session_id
    * 常见类库 分页 + 文件上传（格式，图片大小等）+ 图像裁剪水印等处理（图片上传到远程图片服务器，支持上传到七牛等云存储） + 邮件发送 + 邮箱手机号等验证 + 其它
    * 统计
    * 网站进入维护状态等
    * 加入性能分析 xhprof
    * 常见的功能，注册登录 安装，后台管理界面基础界面，其它可选 （uv/pv统计）
    * 支持cli命令行
    * 钩子 provider
    * 错误日志 和 错误显示 文件错误行数，及错误行前后几行代码显示（这里区分命令行模式，展示一堆jq源码没意思还是cgi模式）
    * 小工具 tool.php，包括 api调试 | mysql 操作 | 
    * 常见定时任务脚本，服务器登录发邮件 svn 自动更新 git 自动部署
    * valiation 验证类
    * 框架文件夹结构
        
        * /wwwroot（存放版本控制所有代码）
        * /static svn（静态图片文件夹）
        * security（存放服务器相关配置）
        * tools 工具
###网站最佳实践:
1. 目录权限
1. web目录中只有index.php,其他的文件在外部，这样就不用怕文件遍历等
1. 主从
1. 图片的解决方案
1. 采用云存储(七牛，又拍云)
1. (
1. 自己设置独立的静态文件服务器：
1. 网页动静分离，缓存，上传文件夹和静态文件夹都不允许执行php等
1. 图片目录不允许执行php这些，最多只能执行html，但是 静态又分两种，我们自己的(采用版本控制)和用户上传的(采用网站应用程序接受)
1. 用户上传的需要进行过滤，而且目录需要写权限
1. html和php执行权限禁用
1. 图片配置防盗链
1. 
1. )
1. 设置404、favicon.ico
1. 
1. robots.txt、Sitemap.xml、
1. 错误日志收集，js错误，php错误, sql报错
1. 采用composer的方式组织，这样升级框架不会涉及到业务代码 也方便框架获取到最新的安全更新
1. 框架支持两种模式的配置：一般配置，敏感配置，一般配置在版本库中，敏感配置不在版本库中

