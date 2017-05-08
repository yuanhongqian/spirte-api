# Contact 通讯录操作类

----------

 Contact 通讯录操作类主要用于获取通信联系人信息和添加联系人信息等。

使用时需要在js中引入 ：

```javascript
var contact = require("contact"); 
```

**注：** 该组件为外置功能组件，打包需要选择。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ getBasicVcards(jsonData:Object,callBackFun:Function): void  获取通讯录用户基础信息 ](#ff_0)
> 
> [getVcards(jsonData:Object,callBackFun:Function): void   获取通讯录用户信息 ](#ff_1)
> 
> [getVcardById(jsonData:Object,callBackFun:Function): void   根据用户标识查询用户信息 ](#ff_2)
> 
> [getVcardsByName(jsonData:Object,callBackFun:Function): void   根据用户名查询用户信息 ](#ff_3)
> 
> [addVcard(jsonData:Object,callBackFun:Function): void   添加用户信息至通讯录 ](#ff_4)
> 
> [deleteVcard(jsonData:Object,callBackFun:Function): void   从通讯录中移除用户信息 ](#ff_5)
> 
> [updateVcard(jsonData:Object,callBackFun:Function): void   更新用户信息至通讯录 ](#ff_6)
> 
> [moveVcard(jsonData:Object,callBackFun:Function): void  移动用户至指定群组 ](#ff_7)
> 
> [getGroups(callBackFun:Function): void  获取通讯录已存在群组信息 ](#ff_8)
> 
> [getGroupById(jsonData :string,callBackFun:Function): void  获取通讯录中指定群组信息 ](#ff_9)
> 
> [addGroup(jsonData:Object,callBackFun:Function): void  添加群组至通讯录 ](#ff_10)
> 
> [deleteGroup(jsonData:Object,callBackFun:Function): void  从通讯录中移除群组 ](#ff_11)
> 
> [updateGroup(jsonData:Object,callBackFun:Function): void 更新群组至通讯录 ](#ff_12)




<span id="ff_0">**getBasicVcards(jsonData:Object,callBackFun:Function): void**</span>  

<code>获取通讯录用户基础信息</code>     

参数：  

jsonData：查询参数，Json对象，定义如下： 

>    groupId：群组id，字符串类型，可选项；

**注：** 如果groupId不写，直接传入空json，如：jsonData = {};

callBackFun：操作回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字[0,-1]。0：查询成功；-1：查询失败；
> 
> datas：数组类型，数组成员为Json对象，定义如下：
> 
> -   id：用户标识，字符串类型；
> 
> -   groupId：用户所属群组标识，字符串类型；
> 
> -   name：用户姓名；
> 
> -   mobile：手机号码；

返回值：无



<span id="ff_1">**getVcards(jsonData:Object,callBackFun:Function): void**</span>  

<code>获取通讯录用户信息</code>   

参数：  

jsonData：查询参数，Json对象，定义如下：
  
>  groupId：群组id，字符串类型，可选项；

**注：** 如果groupId不写，直接传入空json，如：jsonData = {};

callBackFun：操作回调函数，函数具有json类型入参，入参定义如下：  

> code：回应状态码，数字[0,-1]。0：查询成功；-1：查询失败；
> 
> datas：数组类型，数组成员为Json对象，定义如下：
> 
> -     id：用户标识，字符串类型；
> 
> -     groupId：用户所属群组标识，字符串类型；
> 
> -     groupName：用户所属群组名称，字符串类型；
> 
> -     name：用户姓名，字符串类型；
> 
> -     mobile：手机号码，字符串类型；
> 
> -     company：公司，字符串类型；
> 
> -     birthday：生日，字符串类型；
> 
> -     address：地址，字符串类型；
> 
> -     note：备注，字符串类型；
> 
> -     phones：联系人电话信息，数组类型，数组成员为Json对象，定义如下：
> 
>   -         custom：常用电话，字符串类型；
>   
>   -         home：家庭电话，字符串类型；
>   
>   -         work：工作电话，字符串类型；
>   
>   -         faxWork：工作传真，字符串类型；
>   
>   -         faxHome：家庭传真，字符串类型；
>   
>   -         pager：寻呼机，字符串类型；
>   
>   -         other：其他，字符类型；
>   
> -     emails：联系人邮件信息，数组类型，数组成员为Json对象，定义如下：
> 
>   -         custom：常用邮件，字符串类型；
>   
>   -         home：家庭邮件，字符串类型；
>   
>   -         work：工作邮件，字符串类型；
>   
>   -         other：其他邮件，字符类型
      
返回值：无


<span id="ff_2">**getVcardById(jsonData:Object,callBackFun:Function): void**</span>  

<code>根据用户标识查询用户信息</code>    

参数：  

jsonData：查询参数，Json对象，定义如下：

>    id：用户id，字符串类型，必选项；

callBackFun：操作回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字[0,-1]。0：查询成功；-1：查询失败；
> 
> data： Json对象，定义如下：
> 
> -  id：用户标识，字符串类型；
> 
> -     groupId：用户所属群组标识，字符串类型；
> 
> -     groupName：用户所属群组名称，字符串类型；
> 
> -     name：用户姓名，字符串类型；
> 
> -     mobile：手机号码，字符串类型；
> 
> -     company：公司，字符串类型；
> 
> -     birthday：生日，字符串类型；
> 
> -     address：地址，字符串类型；
> 
> -     note：备注，字符串类型；
> 
> -     phones：联系人电话信息，数组类型，数组成员为Json对象，定义如下：
> 
>   -         custom：常用电话，字符串类型；
>   
>   -         home：家庭电话，字符串类型；
>   
>   -         work：工作电话，字符串类型；
>   
>   -         faxWork：工作传真，字符串类型；
>   
>   -         faxHome：家庭传真，字符串类型；
>   
>   -         pager：寻呼机，字符串类型；
>   
>   -         other：其他，字符类型；
>   
> -     emails：联系人邮件信息，数组类型，数组成员为Json对象，定义如下：
> 
>   -         custom：常用邮件，字符串类型；
>   
>   -         home：家庭邮件，字符串类型；
>   
>   -         work：工作邮件，字符串类型；
>   
>   -         other：其他邮件，字符类型
      
返回值：无 



<span id="ff_3">**getVcardsByName(jsonData:Object,callBackFun:Function): void**</span>  

<code>根据用户名查询用户信息</code>  

参数：

jsonData：查询参数，Json对象，定义如下：

>    name：用户名，字符串类型，必选项；

callBackFun：操作回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字[0,-1]。0：查询成功；-1：查询失败；
> 
> datas：数组类型，数组成员为Json对象，定义如下：
> 
> -  id：用户标识，字符串类型；
> 
> -     groupId：用户所属群组标识，字符串类型；
> 
> -     groupName：用户所属群组名称，字符串类型；
> 
> -     name：用户姓名，字符串类型；
> 
> -     mobile：手机号码，字符串类型；
> 
> -     company：公司，字符串类型；
> 
> -     birthday：生日，字符串类型；
> 
> -     address：地址，字符串类型；
> 
> -     note：备注，字符串类型；
> 
> -     phones：联系人电话信息，数组类型，数组成员为Json对象，定义如下：
> 
>   -         custom：常用电话，字符串类型；
>   
>   -         home：家庭电话，字符串类型；
>   
>   -         work：工作电话，字符串类型；
>   
>   -         faxWork：工作传真，字符串类型；
>   
>   -         faxHome：家庭传真，字符串类型；
>   
>   -         pager：寻呼机，字符串类型；
>   
>   -         other：其他，字符类型；
>   
> -     emails：联系人邮件信息，数组类型，数组成员为Json对象，定义如下：
> 
>   -         custom：常用邮件，字符串类型；
>   
>   -         home：家庭邮件，字符串类型；
>   
>   -         work：工作邮件，字符串类型；
>   
>   -         other：其他邮件，字符类型
      
返回值：无


<span id="ff_4">**addVcard(jsonData:Object,callBackFun:Function): void**</span>  

<code>添加用户信息至通讯录</code>   

参数：  

jsonData：需添加用户信息参数，Json对象，定义如下：

> name：用户姓名，字符串类型，必选项；
> 
> groupId：用户所属群组标识，字符串类型，可选项；
> 
> mobile：手机号码，字符串类型，可选项；
> 
> company：公司，字符串类型，可选项；
> 
> birthday：生日，字符串类型，可选项；
> 
> address：地址，字符串类型，可选项；
> 
> note：备注，字符串类型，可选项；
> 
>  phones：联系人电话信息，数组类型，数组成员为Json对象，，可选项，定义如下：
>  
> -  custom：常用电话，字符串类型；
> 
> -    home：家庭电话，字符串类型；
> 
> -   work：工作电话，字符串类型；
> 
> -   faxWork：工作传真，字符串类型；
> 
> -   faxHome：家庭传真，字符串类型；
> 
> -   pager：寻呼机，字符串类型；
> 
> -   other：其他，字符类型；  
> 
> emails：联系人邮件信息，数组类型，数组成员为Json对象，可选项，定义如下：
> 
> -   custom：常用邮件，字符串类型；
> 
> -    home：家庭邮件，字符串类型；
> 
> -    work：工作邮件，字符串类型；
> 
> -    other：其他邮件，字符类型

callBackFun：操作回调函数，函数具有json类型入参，入参定义如下：

code：回应状态码，数字[0,-1]。0：添加成功；-1：添加失败；

id：用户标识，字符串类型；

返回值：无



<span id="ff_5">**deleteVcard(jsonData:Object,callBackFun:Function): void**</span>  

<code>从通讯录中移除用户信息</code>   

参数：  

jsonData：需移除用户信息参数，Json对象，定义如下：

> id：用户标识，字符串类型，必选项；  

callBackFun：操作回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字[0,-1]
> 
> - 0：移除用户成功；
> 
> - -1：移除用户失败；

返回值：无



<span id="ff_6">**updateVcard(jsonData:Object,callBackFun:Function): void**</span>  

<code>更新用户信息至通讯录</code>   


参数：
jsonData：需更新用户信息参数，Json对象，定义如下： 

> id：用户标识，字符串类型，必选项；
> 
> name：用户姓名，字符串类型，可选项；
> 
> groupId：用户所属群组标识，字符串类型，可选项；
> 
> mobile：手机号码，字符串类型，可选项；
> 
> company：公司，字符串类型，可选项；
> 
> birthday：生日，字符串类型，可选项；
> 
> address：地址，字符串类型，可选项；
> 
> note：备注，字符串类型，可选项；
> 
> phones：联系人电话信息，数组类型，数组成员为Json对象，，可选项，定义如下：
> 
> -     custom：常用电话，字符串类型；
> 
> -     home：家庭电话，字符串类型；
> 
> -     work：工作电话，字符串类型；
> 
> -     faxWork：工作传真，字符串类型；
> 
> -     faxHome：家庭传真，字符串类型；
> 
> -     pager：寻呼机，字符串类型；
> 
> -     other：其他，字符类型；
> 
> emails：联系人邮件信息，数组类型，数组成员为Json对象，可选项，定义如下：
> 
> -     custom：常用邮件，字符串类型；
> 
> -     home：家庭邮件，字符串类型；
> 
> -     work：工作邮件，字符串类型；
> 
> -     other：其他邮件，字符类型
> 
callBackFun：操作回调函数，函数具有json类型入参，入参定义如下： 

> code：回应状态码，数字[0,-1]
> 
> - 0：更新成功；
> 
> - -1：更新失败；  

返回值：无



<span id="ff_7">**moveVcard(jsonData:Object,callBackFun:Function): void**</span>  

<code>移动用户至指定群组</code> 


参数： 

jsonData：需移除用户信息参数，Json对象，定义如下：  

>  id：用户标识，字符串类型，必选项；
>     
>  groupId：群组标识，字符串类型，必选项；

callBackFun：操作回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字[0,-1]
> 
> - 0：移动用户成功；
> 
> - -1：移动用户失败；


返回值：无


<span id="ff_8">**getGroups(callBackFun:Function): void**</span>  

<code>获取通讯录已存在群组信息</code> 

参数：  

callBackFun：操作回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字[0,-1]
> 
> -  0：查询成功；
> 
> -  -1：查询失败；
> 
> datas：数组类型，数组成员为Json对象，定义如下：
> 
> - groupId：群组标识，字符串类型；
> 
> - groupName：群组名，字符串类型；
> 
> - groupType：群组类型，数字，[0,1]
> 
>  -  0：系统群组，
>  
>  -  1：自定义群组；

返回值：无



<span id="ff_9">**getGroupById(jsonData :string,callBackFun:Function): void**</span>  

<code>获取通讯录中指定群组信息</code>  


参数：
jsonData：查询参数，Json对象，定义如下：

- groupId：群组id，字符串类型，必选项；

callBackFun：操作回调函数，函数具有json类型入参，入参定义如下：  

> code：回应状态码，数字[0,-1]
> 
> 0：查询成功；
> 
> -1：查询失败； 
> 
> data：Json对象，定义如下：  
> 
> -     groupId：群组标识，字符串类型；
> 
> -     groupName：群组名，字符串类型；
> 
> -     groupType：群组类型，数字，[0,1]
> 
>   -        0：系统群组，
>   
>   -        1：自定义群组；  

返回值：无



<span id="ff_10">**addGroup(jsonData:Object,callBackFun:Function): void**</span>  

<code>添加群组至通讯录</code>  

参数： 

jsonData：需添加群组信息参数，Json对象，定义如下： 

> groupName：群组名，字符串类型，可选项； 
> 
> groupType：群组类型，数字，可选项，[0,1]
> 
> -  0：系统群组，
> 
> - 1：自定义群组；
> 
>  注：仅Android支持

callBackFun：操作回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字[0,-1]
> 
> -  0：添加成功；
> 
> -  -1：添加失败；
> 
> groupId：群组标识，字符串类型；

返回值：无


<span id="ff_11">**deleteGroup(jsonData:Object,callBackFun:Function): void**</span>  

<code>从通讯录中移除群组</code>   

从通讯录中移除群组，只移除群组，不删除群组包含用户信息  

参数： 

jsonData：需移除群组信息参数，Json对象，定义如下：

> groupId：群组标识，字符串类型，必选项；

callBackFun：操作回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字[0,-1]
> 
> - 0：移除群组成功；
> 
> - -1：移除群组失败；

返回值：无


<span id="ff_12">**updateGroup(jsonData:Object,callBackFun:Function): void**</span>  

<code>更新群组至通讯录</code> 

参数：  

jsonData：需更新群组信息参数，Json对象，定义如下： 

> groupId：群组标识，字符串类型，必选项；
> 
> groupName：群组名，字符串类型，可选项；
> 
> groupType：群组类型，数字，可选项，[0,1]
> 
> - 0：系统群组，
> 
> - 1：自定义群组；

callBackFun：操作回调函数，函数具有json类型入参，入参定义如下： 
> 
> code：回应状态码，数字[0,-1]  
> 
> - 0：更新群组成功；
> 
> - -1：更新群组失败；

返回值：无
