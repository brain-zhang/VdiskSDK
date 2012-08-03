=====================
VDiskSDK Introduction
=====================

:Author: memorybox <memoryboxes@gmail.com>

About VDiskSDK
----------------
新浪微盘的API  Python版封装。
具体接口可参见官方文档:http://www.vdisk.me/api/doc
支持所有接口调用

How to use
----------------
1、导入模块
from vdisksdk VDiskAPIClient

2、创建对象
client = VDiskAPIClient('username', 'passwd', 'appkey', 'app_secret')

3、获取token
client.post.auth__get_token()

4、调用接口
print client.post.dir__get_dirid_with_path(path = '/')
print client.post.dir__getlist(dir_id = 0)

说明:
接口的函数方法是同官方文档的url想对应的，例如:

==========================
获得列表

    URL:
    http://openapi.vdisk.me/?m=dir&a=getlist
    请求方式: POST
    返回格式: JSON
    请求参数:
    token: 动态令牌
    dir_id: int 目录id, 为空或为0表示根目录
    可选参数:
    page: int 当前页码，缺省为1
    pageSize: int 每页条数，缺省为1024，最小为2。小于 2 或大于 1024 时取默认值 1024。
    dologid: 参考dolog机制
===========================
这个函数调用请使用client.post.dir__getlist(dir_id = 0)
对应关系:                          -----  --    ------
http://openapi.vdisk.me/?m=      (dir)&a=(getlist)

如上，如果请求方式为GET，则为client.get.XXX
如果为POST，则为client.post.XXX
函数命名对应url接口，中间用'__'间隔。

再一个例子:
接口为
============================
通过路径得到目录id

    URL:
    http://openapi.vdisk.me/?m=dir&a=get_dirid_with_path
    请求方式: GET
    返回格式: JSON
    请求参数:
    token: 动态令牌
    path: 路径, 格式"/path"
    dologid: 参考dolog机制
==============================
应该调用
client.post.dir__get_dirid_with_path(path = '/')


已知问题:
虽然某些接口说可以支持GET方式，但调用失败，强烈建议都用POST调用
token会隔15分钟失效，SDK没有保持连接，你必须自己做这个工作
总体来说，这个SDK仅仅做了一个API Wrapper。!!未经过测试!!

This project was created and lead by memorybox <memoryboxes@gmail.com>.

License
------------

VDiskSDK is released under BSD license.

-----------
参考了新浪微博的python sdk实现:
http://michaelliao.github.com/sinaweibopy/
非常感谢作者。

