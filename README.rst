=====================
<br>VDiskSDK Introduction
<br>=====================
<br>
<br>:Author: memorybox <memoryboxes@gmail.com>
<br>
<br>About VDiskSDK
<br>----------------
<br>新浪微盘的API  Python版封装。
<br>具体接口可参见官方文档:http://www.vdisk.me/api/doc
<br>支持所有接口调用
<br>
<br>How to use
<br>----------------
<br>1、导入模块
<br>from vdisksdk VDiskAPIClient
<br>
<br>2、创建对象
<br>client = VDiskAPIClient('username', 'passwd', 'appkey', 'app_secret')
<br>
<br>3、获取token
<br>client.post.auth__get_token()
<br>
<br>4、调用接口
<br>print client.post.dir__get_dirid_with_path(path = '/')
<br>print client.post.dir__getlist(dir_id = 0)
<br>
<br>说明:
<br>接口的函数方法是同官方文档的url想对应的，例如:
<br>
<br>==========================
<br>获得列表
<br>
<br>    URL:
<br>    http://openapi.vdisk.me/?m=dir&a=getlist
<br>    请求方式: POST
<br>    返回格式: JSON
<br>    请求参数:
<br>    token: 动态令牌
<br>    dir_id: int 目录id, 为空或为0表示根目录
<br>    可选参数:
<br>    page: int 当前页码，缺省为1
<br>    pageSize: int 每页条数，缺省为1024，最小为2。小于 2 或大于 1024 时取默认值 1024。
<br>    dologid: 参考dolog机制
<br>===========================
<br>这个函数调用请使用client.post.dir__getlist(dir_id = 0)
<br>对应关系:                          -----  --    ------
<br>http://openapi.vdisk.me/?m=      (dir)&a=(getlist)
<br>
<br>如上，如果请求方式为GET，则为client.get.XXX
<br>如果为POST，则为client.post.XXX
<br>函数命名对应url接口，中间用'__'间隔。
<br>
<br>再一个例子:
<br>接口为
<br>============================
<br>通过路径得到目录id
<br>
<br>    URL:
<br>    http://openapi.vdisk.me/?m=dir&a=get_dirid_with_path
<br>    请求方式: GET
<br>    返回格式: JSON
<br>    请求参数:
<br>    token: 动态令牌
<br>    path: 路径, 格式"/path"
<br>    dologid: 参考dolog机制
<br>==============================
<br>应该调用
<br>client.post.dir__get_dirid_with_path(path = '/')
<br>
<br>
<br>已知问题:
<br>虽然某些接口说可以支持GET方式，但调用失败，强烈建议都用POST调用
<br>token会隔15分钟失效，SDK没有保持连接，你必须自己做这个工作
<br>总体来说，这个SDK仅仅做了一个API Wrapper。!!未经过测试!!
<br>
<br>This project was created and lead by memorybox <memoryboxes@gmail.com>.
<br>
<br>License
<br>------------
<br>
<br>VDiskSDK is released under BSD license.
<br>
<br>-----------
<br>参考了新浪微博的python sdk实现:
<br>http://michaelliao.github.com/sinaweibopy/
<br>非常感谢作者。
<br>
<br>