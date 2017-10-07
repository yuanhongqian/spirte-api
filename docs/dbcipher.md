# DbCipher  加密数据库操作类

----------

Db加密数据库操作类，支持同步及异步方法处理，开发人员可根据实际场景选用。


使用时需要在js中引入 ：

```javascript
var dbcipher = require("DbCipher"); 
```

**注：** 

- 该组件为外置功能组件，打包需要选择此功能。

- 使用数据库前一定要确认数据库是否打开，使用完后一定要记得关闭数据库，否则数据库会一直被占用。

<h2 id="cid_1">js方法</h2>  

本节目录：

> 同步方法 
> 
>[ open(jsonData:Object): boolean   打开或新建并打开指定名称数据库 ](#ff_0)
> 
> [isOpen(dbName:string): boolean   判断指定路径文件是否存在 ](#ff_1)
> 
> [reKey(jsonData:Object): boolean  修改已打开加密数据库密码](#ff_24)
>
>[ close(dbName:string): boolean  关闭已打开数据库  ](#ff_2)
>
> [tableExists (jsonData:Object): boolean   数据库中指定数据表是否存在 ](#ff_3)
> 
>[dropTable(jsonData:Object): boolean   在数据库中移除指定数据表 ](#ff_4)
> 
> [getTableColumns(jsonData:Object): Array&lt;string&gt;  在数据库中获取指定数据表列名数组 ](#ff_5)
>
>[ execute(jsonData:Object): boolean   执行sql语句 ](#ff_6)
>
> [executes(jsonData:Object): boolean   执行多条sql语句 ](#ff_7)
>
>[ query(jsonData:Object): Array&lt;Object&gt;   执行查询语句 ](#ff_8)
> 
> [beginTransaction(dbName:string): boolean  数据库中开启事务 ](#ff_9)
>
>[ commitTransaction(dbName:string): boolean  数据库中提交事务  ](#ff_10)
>
> [rollbackTransaction(dbName:string): boolean  数据库中回滚事务 ](#ff_11)
> 
> 异步方法
> 
>[encryptDbAsyn (jsonData:Object,callFunction:Function): void  根据输入密码对未加密的sqlite数据库文件进行加密](#ff_26)
> 
>[ openAsyn(jsonData:Object,callFunction:Function): void    打开或新建并打开指定名称数据库 ](#ff_12)
>
> [isOpenAsyn (dbName:string,callFunction:Function): void    判断数据库是否已经打开 ](#ff_13)
> 
> [reKeyAsyn(jsonData:Object,callFunction:Function): void  修改已打开加密数据库密码](#ff_25)
> 
> [closeAsyn (dbName:string,callFunction:Function): void   关闭已打开数据库 ](#ff_14)
> 
> [tableExistsAsyn (jsonData:Object,callFunction:Function): void  数据库中指定数据表是否存在 ](#ff_15)
> 
>[dropTableAsyn (jsonData:Object,callFunction:Function): void   在数据库中移除指定数据表 ](#ff_16)
> 
> [getTableColumnsAsyn (jsonData:Object,callFunction:Function): void  在数据库中获取指定数据表列名数组 ](#ff_17)
>
>[ executeAsyn (jsonData:Object,callFunction:Function): void   执行sql语句 ](#ff_18)
>
> [executesAsyn (jsonData:Object,callFunction:Function): void   执行多条sql语句 ](#ff_19)
>
>[ queryAsyn (jsonData:Object,callFunction:Function): void  执行查询语句 ](#ff_20)
> 
> [beginTransactionAsyn (dbName:string,callFunction:Function): void  数据库中开启事务 ](#ff_21)
>
>[ commitTransactionAsyn (dbName:string,callFunction:Function): void 数据库中提交事务  ](#ff_22)
>
> [rollbackTransactionAsyn (dbName:string,callFunction:Function): void   数据库中回滚事务 ](#ff_23)



<span id="ff_0">**open(jsonData:Object): boolean**</span>  

<code>打开或新建并打开指定名称数据库</code>    

参数：  

jsonData：打开数据传入参数，Json对象，定义如下：  

>    dbName：数据库别名，字符串类型，必选项； 
>    
>    path：数据库db文件所在路径，字符串类型，支持res: file: 前缀，必选项；
>    
>    key：数据库密钥，字符串类型，支持英文、数字，必选项，若不设置密码则使用空字符串

返回值：数据库打开是否成功，bool型 

> true：打开数据库成功 
> 
> false：打开数据库失败

**注：** 数据库打开后即使当前页面关闭，数据库也不会关闭，除非手动调用 close ()方法，因此一旦打开在其它页面就可以直接使用而无需再次打开

示例：

```javascript
 var json = {};
json.dbName = "mydb.db";
json.path = "res:spriteClient/page/function_component/datastore/Db";
json.key = "123456";
var flag = dbcipher.open(json);
if(!flag){
   //失败
   return;
}else{
   //成功

}
```



<span id="ff_1">**isOpen(dbName:string): boolean**</span>  

<code>判断数据库是否已经打开</code>

参数：  

dbName：数据库别名，必选项，字符串

返回值：数据库是否打开，bool型  

> true：数据库已打开；
> 
> false：数据库未打开；

示例：

```javascript
 var json = {};
json.dbName = "mydb.db";
json.path = "res:spriteClient/page/function_component/datastore/Db";
json.key = "123456";

var flag = dbcipher.isOpen(json.dbName);
if(!flag){
	//如果没有打开，执行打开操作
	var flag2 = dbcipher.open(json);
}else{
   //已经打开，可以直接操作数据库

}
```


<span id="ff_24">**reKey(jsonData:Object): boolean**</span>  

<code>修改已打开加密数据库密码</code>   

参数：jsonData：传入参数，Json对象，定义如下：  

>    dbName：需要查询数据库别名，字符串类型，必选项；
> 
>    key：新数据库密码，字符串类型，必选项；

返回值：修改数据库密码是否成功，bool型  

> true：数据库修改密码成功；
> 
> false：数据库修改密码失败

**注**
- 1：在数据库已经打开状态下方可生效，若数据库未打开则不生效； 

- 2：密码支持英文、数字；





<span id="ff_2">**close(dbName:string): boolean**</span>  

<code>关闭已打开数据库</code>   

参数：  

dbName：数据库别名，必选项，字符串

返回值：关闭指定数据库是否成功，bool型  

> true：关闭数据库成功； 
> 
> false：关闭数据库失败；




<span id="ff_3">**tableExists (jsonData:Object): boolean**</span>  

<code>数据库中指定数据表是否存在</code>  

参数：  

jsonData：查询传入参数，Json对象，定义如下：  

> dbName：需要查询数据库别名，字符串类型，必选项；  
> 
> tableName：需要查询数据表名，字符串类型，必选项；

返回值：数据库中指定数据表是否存在，bool型  

> true：数据表存在；  
> 
> false：数据表不存在



<span id="ff_4">**dropTable(jsonData:Object): boolean**</span>  

<code>在数据库中移除指定数据表</code>  

参数： 

jsonData：查询传入参数，Json对象，定义如下： 

>  dbName：数据库别名，字符串类型，必选项；  
>    
>  tableName：需要移除数据表名，字符串类型，必选项；

返回值：移除数据表是否成功，bool型  

> true：移除数据表成功；  
> 
> false：移除数据表失败；




<span id="ff_5">**getTableColumns(jsonData:Object): Array&lt;string&gt;**</span>  

<code>在数据库中获取指定数据表列名数组</code>  

参数：  

jsonData：查询传入参数，Json对象，定义如下：  

>    dbName：数据库别名，字符串类型，必选项；  
>    
>    tableName：需要查询数据表名，字符串类型，必选项；

返回值：包含表所有列名的数组，查询失败则返回空数组



<span id="ff_6">**execute(jsonData:Object): boolean**</span>  

<code>执行sql语句</code>  

执行sqlite语法规范的sql语句，建表sql，插入数据sql，删除数据sql都可以在这里执行。

参数：  

jsonData：传入参数，Json对象，定义如下：  

>    dbName：数据库别名，字符串类型，必选项；
>    
>    sql：待执行sql语句，字符串类型，必选项；

返回值：执行sql语句是否成功，bool型  

> true：执行sql语句成功；
> 
> false：执行sql语句失败；  

示例：

```javascript
var dbName = "mydb.db";
var json = {};
json.dbName = dbName;
json.sql = "create table jy(sid nvarchar(256),name nvarchar(256),age nvarchar(256));";
db.execute(json);
```

<span id="ff_7">**executes(jsonData:Object): boolean**</span>  

<code>执行多条sql语句</code>  

参数：  

jsonData：传入参数，Json对象，定义如下：  

>  dbName：数据库别名，字符串类型，必选项；
>    
>  sqls：待执行sql语句集，数组类型，数组中成员均为需要执行的sql字符串，必选项；

返回值：执行sql语句是否成功，bool型  

> true：执行sql语句成功；
> 
> false：执行sql语句失败；



<span id="ff_8">**query(jsonData:Object): Array&lt;Object&gt;**</span>  

<code>执行查询语句</code>  

返回查询结果集数组（数组每项均为json对象）。

参数：  

jsonData：传递参数，Json对象，定义如下：  

>   dbName：数据库别名，字符串类型，必选项；  
>   
>   sql：待执行sql语句，字符串类型，必选项；

返回值：查询结果集数组，每一条记录均是包含列的查询结果json对象，若查询无结果或失败返回length为0的空数组。

示例：

```javascript
var dbName = "mydb.db";
var tableName = "jy";
var json = {};
json.dbName = dbName;
json.sql = "select * from " + tableName;

var quarray= db.query(json);
if( quarray.length == 0 ){
   // 查询无结果或失败
    return;
}
var content = "查询结果集数组:";
for( var i=0; i<quarray.length; i++ ){
    content += "\n" + quarray[i].sid + " " + quarray[i].name + " " +quarray[i].age;
}

```

<span id="ff_9">**beginTransaction(dbName:string): boolean**</span>  

<code>数据库中开启事务</code>  

参数：  

dbName：数据库别名，必选项，字符串

返回值：开启事务是否成功，bool型  

> true：开启事务成功； 
> 
> false：开启事务失败；

示例：

```javascript

var flag = db.beginTransaction(dbName);
if(flag){
    toast("开启事务成功");
}else{
    toast("开启事务失败");
}

var json = {};
json.dbName = dbName;
var sqls = new Array();
sqls[0]="update test2 set age='16' where sid='001'";
sqls[1]="update test2 set age='18' where sid='002'";
sqls[2]="update test2 set age='17' where sid='003'";
sqls[3]="update test2 set age='15' where sid='004'";
sqls[4]="update test2 set age='16' where sid='005'";
json.sqls = sqls;
var flag2 = db.executes(json);

if(flag2){
	var result = db.commitTransaction(dbName);
	if(result){
	    toast("提交事务成功");
	  
	}else{
	    toast("提交事务失败");
	}
}else{
	toast("请执行rollbackTransaction操作");
	var result = db.rollbackTransaction(dbName);
	if(result){
	    toast("回滚事务成功");
	    query("t8");
	}else{
	    toast("回滚事务失败");
	}
}


```


<span id="ff_10">**commitTransaction(dbName:string): boolean**</span>  

<code>数据库中提交事务</code>  

参数：  

dbName：数据库别名，必选项，字符串

返回值：提交事务是否成功，bool型  

> true：提交事务成功；   
> 
> false：提交事务失败；



<span id="ff_11">**rollbackTransaction(dbName:string): boolean**</span>  

<code>数据库中回滚事务</code>  


参数：  

dbName：数据库别名，必选项，字符串

返回值：回滚事务是否成功，bool型  

> true：回滚事务成功；  
> 
> false：回滚事务失败；




<span id="ff_26">encryptDbAsyn (jsonData:Object,callFunction:Function): void</span>  

<code>根据输入密码对未加密的sqlite数据库文件进行加密</code>  

加密后数据库可使用Dbcipher类操作 

参数：  

jsonData：加密数据库传入参数，Json对象，定义如下：  

> originPath：未加密数据库文件路径，支持res: file: 前缀，字符串类型，必选项；
> 
> encryptPath：加密后数据库文件路径，支持res: file: 前缀，字符串类型，必选项；
> 
> key：数据库密钥，字符串类型，支持英文、数字，必选项; 

callFunction：数据库加密回调函数，入参为数字，标识加密数据库是否成功，[0,-1]

> 0：加密数据库成功；
> 
> -1：加密数据库失败

返回值：无




<span id="ff_12">**openAsyn(jsonData:Object,callFunction:Function): void**</span>  

<code>打开或新建并打开指定名称数据库</code>    

参数：  

jsonData：打开数据传入参数，Json对象，定义如下：  

>    dbName：数据库别名，字符串类型，必选项； 
>    
>    path：数据库db文件所在路径，字符串类型，支持res: file: 前缀，必选项；
>    
>    key：数据库密钥，字符串类型，支持英文、数字，必选项，若不设置密码则使用空字符串；  
>    
callFunction：数据库打开完毕回调函数，入参为数字，标识打开数据库是否成功，[0,-1]

> 0：打开数据库成功；
> 
> -1：打开数据库失败

返回值：无


**注：** 数据库打开后即使当前页面关闭，数据库也不会关闭，除非手动调用 close ()方法，因此一旦打开在其它页面就可以直接使用而无需再次打开

示例：

```javascript
 var json = {};
json.dbName = "mydb.db";
json.path = "res:spriteClient/page/function_component/datastore/Db";
json.key = "123456";
var flag = db.openAsyn(json,function(n){
	if(n == 0){
		//成功
	}
	else{
		//失败
	}
});

```



<span id="ff_13">**isOpenAsyn (dbName:string,callFunction:Function): void**</span>  

<code>判断数据库是否已经打开</code>

参数：  

dbName：数据库别名，必选项，字符串

callFunction：判断数据库是否已经打开  

回调函数，入参为数字，标识打开数据库是否成功，[0,-1]

> 0：数据库已打开；
> 
> -1：数据库未打开

返回值：无



<span id="ff_25">reKeyAsyn(jsonData:Object,callFunction:Function): void</span>  

<code>修改已打开加密数据库密码</code>

参数：jsonData：传入参数，Json对象，定义如下：  

>    dbName：需要查询数据库别名，字符串类型，必选项；
> 
>    key：新数据库密码，字符串类型，必选项；

callFunction：修改已打开加密数据库密码回调函数，入参为数字，标识修改数据库密码是否成功，[0,-1]

> 0：数据库密码修改成功；
> 
> -1：数据库密码修改失败；

返回值：无

**注**
- 1：在数据库已经打开状态下方可生效，若数据库未打开则不生效； 

- 2：密码支持英文、数字；



<span id="ff_14">**closeAsyn (dbName:string,callFunction:Function): void**</span>  

<code>关闭已打开数据库</code>   

参数：  

dbName：数据库别名，必选项，字符串

callFunction：数据库关闭完毕回调函数，入参为数字，标识关闭数据库是否成功，[0,-1]

> 0：关闭数据库成功；
> 
> -1：关闭数据库失败

返回值：无





<span id="ff_15">**tableExistsAsyn (jsonData:Object,callFunction:Function): void**</span>  

<code>数据库中指定数据表是否存在</code>  

参数：  

jsonData：查询传入参数，Json对象，定义如下：  

> dbName：需要查询数据库别名，字符串类型，必选项；  
> 
> tableName：需要查询数据表名，字符串类型，必选项；

callFunction：查询完毕回调函数，入参为数字，标识数据库中指定数据表是否存在，[0,-1]

> 0：指定数据表存在；
> 
> -1：指定数据表不存在

返回值：无




<span id="ff_16">**dropTableAsyn (jsonData:Object,callFunction:Function): void**</span>  

<code>在数据库中移除指定数据表</code>  

参数： 

jsonData：查询传入参数，Json对象，定义如下： 

>  dbName：数据库别名，字符串类型，必选项；  
>    
>  tableName：需要移除数据表名，字符串类型，必选项；  
>  
callFunction：移除指定数据表回调函数，入参为数字，标识在数据库中移除指定数据表是否成功，[0,-1]

> 0：移除成功；
> 
> -1：移除失败； 

返回值：无





<span id="ff_17">**getTableColumnsAsyn (jsonData:Object,callFunction:Function): void**</span>  

<code>在数据库中获取指定数据表列名数组</code>  

参数：  

jsonData：查询传入参数，Json对象，定义如下：  

>    dbName：数据库别名，字符串类型，必选项；  
>    
>    tableName：需要查询数据表名，字符串类型，必选项；

callFunction：在数据库中获取指定数据表列名数组回调函数，入参为字符串数组，包含表所有列名，查询失败则返回空数组； 

返回值：无




<span id="ff_18">**executeAsyn (jsonData:Object,callFunction:Function): void**</span>  

<code>执行sql语句</code>  

执行sqlite语法规范的sql语句，建表sql，插入数据sql，删除数据sql都可以在这里执行。

参数：  

jsonData：传入参数，Json对象，定义如下：  

>    dbName：数据库别名，字符串类型，必选项；
>    
>    sql：待执行sql语句，字符串类型，必选项；

callFunction：执行sql语句回调函数，入参为数字，标识执行sql语句是否成功，[0,-1]

> 0：执行sql语句成功；
> 
> -1：执行sql语句失败； 

返回值：无



<span id="ff_19">**executesAsyn (jsonData:Object,callFunction:Function): void**</span>  

<code>执行多条sql语句</code>  

参数：  

jsonData：传入参数，Json对象，定义如下：  

>  dbName：数据库别名，字符串类型，必选项；
>    
>  sqls：待执行sql语句集，数组类型，数组中成员均为需要执行的sql字符串，必选项；

callFunction：执行sql语句回调函数，入参为数字，标识执行sql语句是否成功，[0,-1]

> 0：执行sql语句成功；
> 
> -1：执行sql语句失败； 

返回值：无




<span id="ff_20">**queryAsyn (jsonData:Object,callFunction:Function): void**</span>  

<code>执行查询语句</code>  

返回查询结果集数组（数组每项均为json对象）。

参数：  

jsonData：传递参数，Json对象，定义如下：  

>   dbName：数据库别名，字符串类型，必选项；  
>   
>   sql：待执行sql语句，字符串类型，必选项；

callFunction：在数据库中执行查询sql语句回调函数，入参为查询结果集数组，每一条记录均是包含列的查询结果json对象，若查询无结果或失败返回length为0的空数组；

返回值：无



<span id="ff_21">**beginTransactionAsyn (dbName:string,callFunction:Function): void**</span>  

<code>数据库中开启事务</code>  

参数：  

dbName：数据库别名，必选项，字符串

callFunction：数据库中开启事务回调函数，入参为数字，标识开启事务是否成功，[0,-1]

> 0：开启事务成功；
> 
> -1：开启事务失败； 

返回值：无





<span id="ff_22">**commitTransactionAsyn (dbName:string,callFunction:Function): void**</span>  

<code>数据库中提交事务</code>  

参数：  

dbName：数据库别名，必选项，字符串

callFunction：数据库中提交事务回调函数，入参为数字，标识提交事务是否成功，[0,-1]

> 0：提交事务成功；
> 
> -1：提交事务失败； 

返回值：无




<span id="ff_23">**rollbackTransactionAsyn (dbName:string,callFunction:Function): void**</span>  

<code>数据库中回滚事务</code>  


参数：  

dbName：数据库别名，必选项，字符串

返回值：回滚事务是否成功，bool型  

callFunction：数据库中回滚事务回调函数，入参为数字，标识回滚事务是否成功，[0,-1]

0：回滚事务成功；

-1：回滚事务失败； 

返回值：无



