

# 个人信息

 - 吴秀民/男/1988 
 - 本科/临沂大学
 - 工作年限：5年
 - 技术博客：https://pylixm.cc/
 - Github：https://github.com/pylixm
 - 期望职位：运维高级开发工程师
 - 期望薪资：税后年薪50k，特别喜欢的公司可例外
 - 期望城市：北京


# 联系方式

- 手机/微信：18612410531
- Email：pyli.xm@gmail.com
- QQ：20894205

# 技能清单

技术方面

- 熟练掌握Python开发，熟悉Golang/java的开发；
- 善于使用django 框架开发web系统，可个人负责开发业务复杂的前后端系统功能。熟悉flask 、tornado 、bottle等python web 框架；
- 熟练掌握SaltStack等运维自动化工具，阅读过SaltStack的部分源码；
- 熟练掌握Git/Svn等版本管理工具和工作流程；
- 熟悉vue.js生态，可开发业务复杂的前后端分离项目；
- 熟悉MySQL/PostgreSQL等数据库，Redis/Memcached/MongoDB等NOSQL；
- 熟悉LVS, Nginx等4、7层负载均衡技术；
- 熟悉TCP/IP，HTTP，Restful等互联网相关技术标准；
- 熟悉Linux下的自动化系统运维和开发的生态知识；
- 熟悉SAE/阿里云/微博开放平台/微信小程序；
- 了解互联网产品的生命周期和发展过程、开发团队管理和项目管理、应用发布和版本控制，具有良好的文档能力；
- 了解dorker 容器技术，可使用dorker来管理python的多版本开发环境；
- 良好的自我驱动能力和时间管理，积极参与并贡献开源项目；

管理

- 规划项目长期目标和短期目标
- 技术选型，方案设计，模块和功能设计
- 定期项目总结，向下管理，向上汇报

# 工作经历

## 新浪微博 （ 2018年4月 ~ 今 ）

主要负责自动化运维平台的研发工作和视频通讯等业务线的运维工作。

「微博自动化管理系统项目」作为微博研发平台的底层自动化运维平台，提供了上线发布、监控预警、流量切换、自动扩缩容和服务管理等功能。其间做了如下重点工作：

- 作为主程参与开发了系统的域名切换模块。针对老版本的域名切换做了用户体验的优化，缩短了操作路径，提高了操作效率。
- 作为主程为该项目首次引入vue.js框架，搭建了移动端的开发脚手架，并完成了该系统监控预警、上线发布和流量切换等模块的移动端的开发。
- 独立搭建了视频和通讯的7层负载均衡日志收集系统，使用ELK生态中的E和K，作为存储和展示组件，为减少资源消耗，使用Python开发了日志的推送端组件。10台设备组成的ES集群，日收集日志量在2.6T，每5s的入库数据量在3W左右。

主要技术或软件关键字：Golang、Python、vue.js、mysql、redis、shell、Docker、Graphit、Grafana、EKL、Search Guard


## 汽车之家 ( 2015年6月 ~ 2018年4月)

在汽车之家工作期间，主要从事运维自动化平台的研发工作。主要参与项目如下：

### 资产管理系统项目

本系统作为公司权威的资产管理中心(包括有形资产和无形资产), 利用电子流程维护数据的准确性，以数据来解读运维平时工作中体现的业务思维。

- 作为项目负责人，参与了项目的改版，优化了用户体验，提高了数据的准确性，数据准确性基本保证在99%，增大了资产数据的覆盖率。作为整个运维自动化平台的资源仓库，为自动化平台的建设提供了有利的保障。
- 为保证数据的准确性，我们开发制定了以“盘”、“审”、“罚”为核心的自我审计方案。通过系统自查加规章制度的方式，大大提高了数据的准确率。详情可以参考当时总结分享的文章[聊聊CMDB的资产审计](http://autohomeops.corpautohome.com/articles/%E8%81%8A%E8%81%8ACMDB%E7%9A%84%E8%87%AA%E6%88%91%E5%AE%A1%E8%AE%A1/)

主要技术或软件关键字：Python、Django、vue.js、Mysql、Celery、Redis、Puppet

### 基于SaltStack的底层架构扩展

在运维自动化的过程中，需要一个批量机器的管理工具。经过调研，同时结合我们团队自身的技术栈，选择了SaltStack。但是它上层的API接口，并不能满足我们的需求。我们根据自身需求，对它做了改造：

- 封装其Restfull API，使其可以横向扩展而不依赖Salt-Master;
- 增加Salt命令下发及模块执行的审计功能；
- 增加Salt的权限控制，可以根据Salt-Minion范围及执行模块做权限划分；
通过对SaltStack的改造，夯实了整个自动化操作的底层通道基础，使上层saas的自动化处理更加稳定、安全。

在该项目期间，主要做了如下重点工作：

- 开发了上层的API服务组件，提供了和外部服务交互的API，支持命令审计功能、用户权限功能等功能。
- 优化整体架构和API服务，使单台机器的QPS由200提升到1000+，详细可参考当时总结分析的文章[记一次Tornado QPS优化](https://pylixm.cc/posts/2017-04-04-tornado-qps-optimization.html)。

主要技术或软件关键字：Python、Tornado、Mysql、Redis、SQLAchemy、Rabbitmq、SaltStack

### 其他项目

- 参与公司上层SAAS配置管理服务的开发，实现了TOMCAT/IIS服务的自动化部署安装。

## 山东尚捷科技 ( 2012年7月 ~ 2015年6月)

期间主要作为Python研发，主要做了如下重点工作：

- 作为研发参与了多家银行的数据经营考核系统。
- 作为项目组长，负责某银行的信用卡进件管理系统的需求洽谈、文档的编写、系统的设计及开发。

主要技术或软件关键字：Python、Django、PostgreSQL、Rabbitmq、HTML/CSS、Jquery

## 开源项目

- [Django-mdeditor](https://github.com/pylixm/django-mdeditor)：基于editor.md的Django-app组件，star 200+。
- [Python基础教程](https://github.com/pylixm/python_start)：根据自己工作学习经验总结的Python入门教程。

## 技术文章

- [pipenv 试用过程分析](https://pylixm.cc/posts/2018-01-13-python-pipenv.html)
- [vagrant 开发环境搭建](https://pylixm.cc/posts/2015-12-01-Vagrant-install.html) 
- [我心目中Tornado最佳实践](https://pylixm.cc/posts/2017-03-10-tornado-best-practices.html)
- [SQLAlchemy 数据库链接池问题排查记录](https://pylixm.cc/posts/2017-08-29-tornado-sqlalchemy.html)

---      
# 致谢
感谢您花时间阅读我的简历，期待能有机会和您共事。
      