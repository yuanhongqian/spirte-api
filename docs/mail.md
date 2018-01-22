# Mail 邮件相关操作组件


---------

Mail组件封装了对邮件相关操作，包括邮件接收（Imap标准协议），邮件发送（Smtp标准协议，自定义邮件网关发送协议）等相关功能，使用Mail组件可快速构建邮件客户端相关功能。

Mail为外置组件。

<h2 id="cid_1">方法</h2>

本节目录：

> [getImapFolders(jsonData:Object,callbackFun:Function):void Imap协议获取邮箱包含文件夹信息](#ff_0)
> 
> [fetchImapMessages(jsonData:Object,callbackFun:Function):void Imap协议获取所有邮件的邮件头信息](#ff_1)
> 
> [fetchImapUids(jsonData:Object,callbackFun:Function):void Imap协议获取所有邮件uid](#ff_2)
> 
> [receiveImapBasicMessages(jsonData:Object,callbackFun:Function):void Imap协议收取所有邮件并获取邮件基础信息](#ff_3)
> 
> [receiveImapBasicMessagesByUidRange(jsonData:Object,callbackFun:Function):void Imap协议收取指定区间uid邮件并获取邮件基础信息](#ff_4)
> 
> [receiveImapBasicMessagesByUids(jsonData:Object,callbackFun:Function):void Imap协议收取指定uid列表的邮件并获取邮件基础信息](#ff_5)
> 
> [receiveImapBasicMessagesByNums(jsonData:Object,callbackFun:Function):void Imap协议收取指定序号列表邮件并获取邮件基础信息](#ff_6)
> 
> [receiveImapBasicMessagesByNumRange(jsonData:Object,callbackFun:Function):void Imap协议收取指定区间内邮件并获取邮件基础信息](#ff_7)
> 
> [receiveImapMessageByUid(jsonData:Object,callbackFun:Function):void Imap协议收取指定uid邮件并获取详细信息](#ff_8)
> 
> [downloadImapAttachment(jsonData:Object,callbackFun:Function):void Imap协议下载附件并保存](#ff_9)
> 
> [sendMessage(jsonData:Object,callbackFun:Function):void Smtp标准协议发送邮件](#ff_10)
> 
> **Mplus自定义发送**
> 
> [sendMplusMessage(jsonData:Object,callbackFun:Function):void 连接Mplus邮件服务器使用自定义接口发送邮件](#ff_11)
> 





<span id="ff_0">**getImapFolders(jsonData:Object,callbackFun:Function):void**</span>

<code>Imap协议获取邮箱包含文件夹信息</code>

参数：

jsonData：json格式，定义如下：

> accountInfo：邮箱账号信息，必选项，json格式，定义如下：
> 
> - user：邮箱账号名，字符串类型，必选项；
> 
> - password：邮箱账号密码，字符串类型，必选项；
> 
> serverInfo：邮件服务器设置，必选项，json格式，定义如下：
> 
> - host：邮件服务器地址，字符串类型，必选项；
> 
> - port：邮件服务器端口，数字类型，必选项；
> 
> - isSsl：是否启动SSL加密，bool型，必选项；

callbackFun：获取回调，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字类型，0：获取成功；-1：获取失败；
> 
> folders：有哦件文件夹列表，json数组类型，json格式定义如下：
> 
> - name：邮箱名，字符串类型；
> 
> - fullName：邮箱全名，字符串类型；

返回值：无



<span id="ff_1">**fetchImapMessages(jsonData:Object,callbackFun:Function):void**</span>

<code>Imap协议获取所有邮件的邮件头信息</code>

参数：

jsonData：json格式，定义如下：

> accountInfo：邮箱账号信息，必选项，json格式，定义如下：
> 
> - user：邮箱账号名，字符串类型，必选项；
> 
> - password：邮箱账号密码，字符串类型，必选项；
> 
> serverInfo：邮件服务器设置，必选项，json格式，定义如下：
> 
> - host：邮件服务器地址，字符串类型，必选项；
> 
> - port：邮件服务器端口，数字类型，必选项；
> 
> - isSsl：是否启动SSL加密，bool型，必选项；
> 
> folderInfo：邮件文件夹设备，必选项，json格式，定义如下：
> 
> - folderName：需收取的邮件文件夹名称，字符串类型，收件箱为INBOX；
> 
> - folderType：邮箱操作类型，数字枚举型，【1，2】，1：只读类型；2：读写类型。可选项，默认1

callbackFun：邮箱收取回调，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字类型，0：邮件收取成功；-1：邮件收取失败
> 
> messages：已收取邮件列表，json数组类型，json格式如下：
> 
> - uid：邮件唯一标识，字符串类型；
> 
> - subject：邮件标题，字符串类型；
> 
> - sendDate：邮件发送时间，字符串类型，格式：yy-MM-dd HH: mm: ss;

返回值：无


<span id="ff_2">**fetchImapUids(jsonData:Object,callbackFun:Function):void Imap**</span>

<code>协议获取所有邮件uid</code>

参数：

jsonData：json格式，定义如下：

> accountInfo：邮箱账号信息，必选项，json格式，定义如下：
> 
> - user：邮箱账号名，字符串类型，必选项；
> 
> - password：邮箱账号密码，字符串类型
> 
> serverInfo：邮件服务器设置，必选项，json格式，定义如下：
> 
> - host：邮件服务器地址，字符串类型，必选项；
> 
> - port：邮件服务器端口，数字类型，必选项；
> 
> - isSsl：是否启动SSL加密，bool型，必选项；
> 
> folderInfo：邮件文件夹设置，必选项，json格式，定义如下：
> 
> - folderName：需收取的邮件文件夹名称，字符串类型，收件箱为INBOX；
> 
> - folderType：邮箱操作类型，数字枚举型，【1，2】，1：只读类型，2：读写类型。可选项，默认1；

callbackFun：邮箱收取回调，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字类型，0：邮件收取成功，-1：邮件收取失败
> 
> messages：已收取邮件列表，json数组类型，json格式定义如下：
> 
> - uid：邮件唯一标识，字符串类型；

返回值：无


<span id="ff_3">**receiveImapBasicMessages(jsonData:Object,callbackFun:Function):void**</span>

<code>Imap协议收取所有邮件并获取邮件基础信息</code>

参数：

jsonData：json格式，定义如下：

> accountInfo：邮箱账号信息，必选项，json格式，定义如下：
> 
> - user：邮箱账号名，字符串类型，必选项；
> 
> - password：邮箱账号密码，字符串类型，必选项；
> 
> serverInfo：邮件服务器设置，必选项，json格式，定义如下：
> 
> - host：邮件服务器地址，字符串类型，必选项；
> 
> - port：邮件服务器端口，数字类型，必选项；
> 
> - isSsl：是否启动SSL加密，bool型，必选项；
> 
> folderInfo：邮件文件夹设置，必选项，json格式，定义如下：
> 
> - folderName：需收取的邮件文件夹名称，字符串类型，收件箱为INBOX；
> 
> - folderType：邮箱操作类型，数字枚举型，【1，2】，1：只读类型，2：读写类型，可选项，默认1

callbackFun：邮箱收取回调，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字类型，0：邮件收取成功，-1：邮件收取失败
> 
> message：已收取邮件列表，json数组类型，json格式定义如下：
> 
> - uid：邮件唯一标识，字符串类型；
> 
> - subject：邮件标题，字符串类型；
> 
> - sendDate：邮件发送时间，字符串类型，格式：yy-MM-dd HH: mm: ss;
> 
> - fromm：发件人邮箱，json格式定义如下：
> 
>  - name：发件人名称，字符串类型；
>  
>  - address：发件人邮箱地址，字符串类型；
>  
> - to：接收人邮箱，json数组类型，json定义如下：
> 
>  - name：接收人名称，字符串类型；
>  
>  - address：接收人邮箱地址，字符串类型；
>  
> - cc：抄送人邮箱，json数组类型，json定义如下：
> 
>  - name：抄送人名称，字符串类型；
>  
>  - address：抄送人邮箱地址，字符串类型；
>  
> - bcc：密送人邮箱，json数组类型，json定义如下：
> 
>  - name：密送人名称，字符串类型；
>  
>  - address：密送人邮箱地址，字符串类型；
>  
> - priority：邮件优先级，数字枚举型，【1，3，5】，1：高；3：普通；5：低；
> 
> - hasReplySign：邮件是否需要打开回执，bool型，true：需要回执，false：不需要回执；
> 
> - hasAttachment：是否存在附件，bool型
> 
> - attachments：附件信息集，数组类型，数组成员为json格式定义如下：
> 
>  - fileName：附件名称，包含后缀名，字符串类型；
>  
>  - fileSize：附件尺寸，数字类型，单位kb

返回值：无


<span id="ff_4">**receiveImapBasicMessagesByUidRange(jsonData:Object,callbackFun:Function):void**</span>

<code>Imap协议收取指定区间uid邮件并获取邮件基础信息</code>

参数：

jsonData：json格式，定义如下：

> startUid：待获取首封邮件uid，字符串类型；
> 
> endUid：待获取尾封邮件uid，字符串类型；
> 
> accountInfo：邮箱账号信息，必选项，json格式，定义如下：
> 
> - host：邮件服务器地址，字符串类型，必选项；
> 
> - port：邮件服务器端口，数字类型，必选项；
> 
> - isSsl：是否启动SSL加密，bool型，必选项；
> 
> folderInfo：邮件文件夹设置，必选项，json格式，定义如下：
> 
> - folderName：需收取的邮件文件夹名称，字符串类型，收件箱为INBOX；
> 
> - folderType：邮箱操作类型，数字枚举型，【1，2】，1：只读类型，2：读写类型，可选项，默认1；
> 

callbackFun：邮箱收取回调，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字类型，0：邮件收取成功，-1：邮件收取失败
> 
> message：已收取邮件列表，json数组类型，json格式定义如下：
> 
> - uid：邮件唯一标识，字符串类型；
> 
> - subject：邮件标题，字符串类型；
> 
> - sendDate：邮件发送时间，字符串类型，格式：yy-MM-dd  HH: mm: ss
> 
> - from：发件人邮箱，json格式定义，定义如下：
> 
>  - name：发件人名称，字符串类型；
>  
>  - address：发件人邮箱地址，字符串类型；
>  
> - to：接收人邮箱，json数组类型，json定义如下：
> 
>  - name：接收人名称，字符串类型；
>  
>  - address：抄送人邮箱地址，字符串类型；
>  
> - bcc：密送人邮箱，json数组类型，json定义如下：
> 
>  - name：密送人名称，字符串类型；
>  
>  - address：密送人邮箱地址，字符串类型；
>  
> - priority：邮件优先级，数字枚举型，【1，3，5】，1：高；3：普通；5：低；
> 
> - hasReplySing：邮件是否需要打开回执，bool型，true：需要回执；false：不需要回执；
> 
> - hasAttachment：是否存在附件，bool型；
> 
> - attachments：附件信息集，数组类型，数组成员为json格式定义如下：
> 
>  - fileName：附件名称，包含后缀名，字符串类型；
>  
>  - fileSize：附件尺寸，数字类型，单位kb

返回值：无

<span id="ff_5">**receiveImapBasicMessagesByUids(jsonData:Object,callbackFun:Function):void**</span>

<code>Imap协议收取指定uid列表的邮件并获取邮件基础信息</code>

参数：

jsonData：json格式，定义如下：

> uids：需获取的邮件uid列表，字符串数组类型；
> 
> accountInfo：邮箱账号信息，必选项，json格式，定义如下：
> 
> - user：邮箱账号名，字符串类型，必选项；
> 
> - password：邮箱账号密码，字符串类型，必选项；
> 
> serverInfo：邮件服务器设置，必选项，json格式，定义如下：
> 
> - host：邮件服务器地址，字符串类型，必选项；
> 
> - port：邮件服务器端口，数字类型，必选项；
> 
> - isSsl：是否启动SSL加密，bool行，必选项；
> 
> folderInfo：邮件文件夹设置，必选项，json格式，定义如下：
> 
> - folderName：需收取的邮件文件夹名称，字符串类型，收件箱为INBOX；
> 
> - folderType：邮箱操作类型，数字枚举型，【1，2】，1：只读类型，2：读写类型，可选项，默认1；

callbackFun：邮箱收取回调，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字类型，0：邮件收取成功；-1：邮件收取失败
> 
> messages：已收取邮件列表，json数组类型，json格式定义如下：
> 
> - uid:邮件唯一标识，字符串类型；
> 
> - subject：邮件标题，字符串类型；
> 
> - sendDate：邮件发送时间，字符串类型，格式：yy-MM-dd HH: mm: ss
> 
> - from：发件人邮箱，json格式定义，如下：
> 
>  - name：发件人名称，字符串类型；
>  
>  - address：发件人邮箱地址，字符串类型
>  
> - to：接收人邮箱，json数组类型，json定义如下：
> 
>  - name：接收人名称，字符串类型；
>  
>  - address：接收人邮箱地址，字符串类型；
>  
> - cc：抄送人邮箱，json数组类型，json定义如下：
> 
>  - name：抄送人名称，字符串类型；
>  
>  - address：抄送人邮箱地址，字符串类型；
>  
> - bcc：密送人邮箱，json数组类型，json定义如下：
> 
>  - name：密送人名称，字符串类型；
>  
>  - address：密送人邮箱地址，字符串类型；
>  
> - priority：邮件优先级，数字枚举型，【1，3，5】，1：高；3：普通；5：低
> 
> - hasReplySign：邮件是否需要打开回执，bool型，true：需要回执；false：不需要回执。
> 
> - hasAttachment：是否存在附件，bool型；
> 
> - attachments：附件信息集，数组类型，数组成员为json格式定义如下：
> 
>  - fileName：附件名称，包含后缀名，字符串类型；
>  
>  - fileSize：附件尺寸，数字类型，单位kb

返回值：无




<span id="ff_6">**receiveImapBasicMessagesByNums(jsonData:Object,callbackFun:Function):void**</span>

<code>Imap协议收取指定序号列表邮件并获取邮件基础信息</code>

参数：

jsonData：json格式，定义如下：

> nums：需获取的邮件序号列表，数字数组类型；
> 
> accountInfo：邮箱账号信息，必选项，json格式，定义如下：
> 
> - user：邮箱账号名，字符串类型，必选项；
> 
> - password：邮箱账号密码，字符串类型，必选项；
> 
> serverInfo：邮件服务器设置，必选项，json格式，定义如下：
> 
> - host：邮件服务器地址，字符串类型，必选项
> 
> - port：邮件服务器端口，数字类型，必选项；
> 
> - isSsl：是否启动SSL加密，bool型，必选项；
> 
> folderInfo：邮件文件夹设置，必选项，json格式，定义如下:
> 
> - folderName：需收取的邮件文件夹名称，字符串类型，收件箱为INBOX；
> 
> - folderType：邮箱操作类型，数字枚举型，【1，2】，1：只读类型，2：读写类型，可选项，默认1；

callbackFun：邮箱收取回调，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字类型，0：邮件收取成功；-1：邮件收取失败；
> 
> messages：已收取邮件列表，json数组类型，json格式定义如下：
> 
> - uid：邮件唯一标识，字符串类型；
> 
> - subject：邮件标题，字符串类型；
> 
> - sendDate：邮件发送时间，字符串类型，格式：yy-MM-dd HH: mm: ss
> 
> - from：发件人邮箱，json格式定义如下：
> 
>  - name：发件人名称，字符串类型；
>  
>  - address：发件人邮箱地址，字符串类型；
>  
> - to：接收人邮箱，json数组类型，定义如下：
> 
>  - name：接收人名称，字符串类型；
>  
>  - address：接收人邮箱地址，字符串类型；
>  
> - cc：抄送人邮箱，json数组类型，定义如下：
> 
>  - name：抄送人名称，字符串类型；
>  
>  - address：抄送人邮箱地址，字符串类型；
>  
> - bcc：密送人邮箱，json数组类型，定义如下：
> 
>  - name：密送人名称，字符串类型；
>  
>  - address：密送人邮箱地址，字符串类型；
>  
> - priority：邮件优先级，数字枚举型，【1，3，5】，1：高；3：普通；5：低
> 
> - hasReplySign：邮件是否需要打开回执，bool型，true：需要回执，false：不需要回执；
> 
> - hasAttachment：是否存在附件，bool型；
> 
> - attachments：附件信息集，数组类型，数组成员为json格式定义如下：
> 
>  - fileName：附件名称，包含后缀名，字符串类型；
>  
>  - fileSize：附件尺寸，数字类型，单位kb

返回值：无

<span id="ff_7">**receiveImapBasicMessagesByNumRange(jsonData:Object,callbackFun:Function):void**</span>

<code>Imap协议收取指定区间内邮件并获取邮件基础信息</code>

参数：

jsonData：json格式，定义如下：

> startNum：待获取首封邮件序号，数字类型；
> 
> endNum：待获取尾封邮件序号，数字类型；
> 
> accountInfo：邮箱账号信息，必选项，json格式，定义如下：
> 
> - user：邮箱账号名，字符串类型，必选项；
> 
> - password：邮箱账号密码，字符串类型，必选项；
> 
> serverInfo：邮件服务器设置，必选项，json格式，定义如下：
> 
> - host：邮件服务器地址，字符串类型，必选项；
> 
> - port：邮件服务器端口，数字类型，必选项；
> 
> - isSsl：是否启动SSL加密，bool型，必选项；
> 
> folderInfo：邮件文件夹设置，必选项，json格式，定义如下：
> 
> - folderName：需收取的邮件文件夹名称，字符串类型，收件箱为INBOX；
> 
> - folderType：邮箱操作类型，数字枚举型，【1，2】，1：只读类型，2：读写类型，可选项，默认1；

callbackFun：邮箱收取回调，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字类型，0：邮件收取成功；-1：邮件收取失败；
> 
> messages：已收取邮件列表，json数组类型，json格式定义如下：
> 
> - uid：邮件唯一标识，字符串类型；
> 
> - subject：邮件标题，字符串类型；
> 
> - sendDate：邮件发送时间，字符串类型，格式：yy-MM-dd HH: mm: ss;
> 
> - from：发件人邮箱，json格式定义，如下：
> 
>  - name：发件人名称，字符串类型；
>  
>  - address：发件人邮箱地址，字符串
>  
> - to：接收人邮箱，json数组类型，json定义如下：
> 
>  - name：接收人名称，字符串类型；
>  
>  - address：接收人邮箱地址，字符串类型；
>  
> - cc：抄送人邮箱，json数组类型，json定义如下：
> 
>  - name：抄送人名称，字符串类型；
>  
>  - address：抄送人邮箱地址，字符串类型；
>  
> - bcc：密送人邮箱，json数组类型，json定义如下：
> 
>  - name：密送人名称，字符串类型；
>  
>  - address：密送人邮箱地址，字符串类型；
>  
> - priority：邮件优先级，数字枚举型，【1，3，5】，1：高；3：普通；5：低
> 
> - hasReplySign：邮件是否需要打开回执，bool型，true：需要回执，false：不需要回执；
> 
> - hasAttachment：是否存在附件，bool型；
> 
> - attachments：附件信息集，数组类型，数组成员为json格式定义如下：
> 
>  - fileName：附件名称，包含后缀名，字符串类型；
>  
>  - fileSize：附件尺寸，数字类型，单位kb；

返回值：无


<span id="ff_8">**receiveImapMessageByUid(jsonData:Object,callbackFun:Function):void **</span>

<code>Imap协议收取指定uid邮件并获取详细信息</code>

参数：

jsonData：json格式，定义如下：

> uid：待获取邮件uid，字符串类型；
> accountInfo：邮箱账号信息，必选项，json格式，定义如下：
> - user：邮箱账号名，字符串类型，必选项；
> - password：邮箱账号密码，字符串类型，必选项；
> serverInfo：邮件服务器设置，必选项，json格式，定义如下：
> - host：邮件服务器地址，字符串类型，必选项；
> - port：邮件服务器端口，数字类型，必选项；
> - isSsl：是否启动SSL加密，bool型，必选项；
> folderInfo：邮件文件夹设置，必选项，json格式，定义如下：
> - folderName：需收取的邮件文件夹名称，字符串类型，收件箱为INBOX；
> - folderType：邮箱操作类型，数字枚举型，【1，2】，1：只读类型，2：读写类型，可选项，默认1；

callbackFun：邮箱收取回调，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字类型，0：邮件收取成功，-1：邮件收取失败
> 
> message：已收取邮件，json格式定义如下：
> 
> - uid：邮件唯一标识，字符串类型；
> 
> - subject：邮件标题，字符串类型；
> 
> - sendDate：邮件发送时间，字符串类型，格式：yy-MM-dd HH: mm: ss
> 
> - from：发件人邮箱，json格式定义，如下：
> 
>  - name：发件人名称，字符串类型；
>  
>  - address：发件人邮箱地址，字符串类型；
>  
> - to：接收人邮箱，json数组类型，json定义如下：
> 
>  - name：接收人名称，字符串类型；
>  
>  - address：接收人邮箱地址，字符串类型；
>  
> - cc：抄送人邮箱，json数组类型，json定义如下：
> 
>  - name：抄送人名称，字符串类型；
>  
>  - address：抄送人邮箱地址，字符串类型；
>  
> - bcc：密送人邮箱，json数组类型，json定义如下：
> 
>  - name：密送人名称，字符串类型；
>  
>  - address：密送人邮箱地址，字符串类型
>  
> - priority：邮件优先级，数字枚举型，【1，3，5】，1：高；3：普通；5：低
> 
> - hasReplySign：邮件是否需要打开回执，bool型，true：需要回执，false：不需要回执；
> 
> - hasAttachment：是否存在附件，bool型；
> 
> - messageId：邮件消息id，字符串类型；
> 
> - referenceId：回复邮件时关联上一封邮件的messageId，字符串类型；
> - bodyText：邮件文本正文，内容base64编码，字符串类型；
> 
> - bodyHtml：邮件html正文，内容base64，字符串类型；
> 
> - attachments：附件信息集，数组类型，数组成员为json格式定义如下：
> 
>  - fileName：附件名称，包含后缀名，字符串类型；
>  
>  - fileSize：附件尺寸，数字类型，单位kb

返回值：无


<span id="ff_9">**downloadImapAttachment(jsonData:Object,callbackFun:Function):void**</span>

<code>Imap协议下载附件并保存</code>

参数：

jsonData：json格式，定义如下：

> uid：待获取附件所在邮件uid，字符串类型，必选项；
> 
> fileName：附件名称，字符串类型，必选项；
> 
> path：下载文件保存路径，字符串类型，必选项；
> 
> orderIndex：邮件包含多个同名附件时，附件排序索引值，数字，可选项，默认0；
> 
> accountInfo：邮箱账号信息，必选项，json格式，定义如下：
> 
> - user：邮箱账号名，字符串类型，必选项；
> 
> - password：邮箱账号密码，字符串类型，必选项；
> 
> serverInfo：邮件服务器设置，必选项，json格式，定义如下：
> 
> - host：邮件服务器地址，字符串类型，必选项；
> 
> - port：邮件服务器端口，数字类型，必选项；
> 
> - isSsl：是否启动SSL加密，bool型，必选项；
> 
> folderInfo：邮件文件夹设置，必选项，json格式，定义如下：
> 
> - folderName：需收取的邮件文件夹名称，字符串类型，收件箱为INBOX；
> 
> - folderType：邮箱操作类型，数字枚举型，【1，2】，1：只读类型，2：读写类型，可选项，默认1；

callbackFun：附件下载回调，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字类型，0：附件下载成功，-1：附件下载失败
> 
> path：下载成功后文件保存绝对路径，字符串类型

返回值：无

<span id="ff_10">**sendMessage(jsonData:Object,callbackFun:Function):void** </span>

<code>Smtp标准协议发送邮件</code>

参数：

jsonData：json格式，定义如下：

> accountInfo：邮箱账号信息，必选项，json格式，定义如下：
> 
> - user：邮箱账号名，字符串类型，必选项；
> 
> - password：邮箱账号密码，字符串类型，必选项；
> 
> serverInfo：邮件服务器设置，必选项，json格式，定义如下：
> 
> - host：发送邮件服务器地址，字符串类型，必选项；
> 
> - port：发送邮件服务器端口，数字类型，必选项；
> 
> - isSsl：是否启动SSL加密，bool型，必选项；
> 
> message：需发送邮件信息，必选项，json格式，定义如下：
> 
> - subject：邮件标题，字符串类型，可选项；
> 
> - sendDate：邮件发送时间，字符串类型，可选项，格式：yy-MM-dd HH: mm:ss
> 
> - messageId：邮件消息标识，字符串类型，可选项；
> 
> - from：发件人邮箱，json格式定义，定义如下：
> 
>  - name：发件人名称，字符串类型，可选项；
>  
>  - address：发件人邮箱地址，字符串类型，必选项；
>  
> - to：接收人邮箱，json数组类型，json定义如下：
> 
>  - name：接收人名称，字符串类型，可选项；
>  
>  - address：接收人邮箱地址，字符串类型，必选项
>  
> - cc：抄送人邮箱，json数组类型，json定义如下：
> 
>  - name：抄送人名称，字符串类型，可选项；
>  
>  - address：抄送人邮箱地址，字符串类型，必选项；
>  
> - bcc：密送人邮箱，json数组类型，json定义如下：
> 
>  - name：密送人名称，字符串类型，可选项；
>  
>  - address：密送人邮箱地址，字符串类型，必选项；
>  
> - priority：邮件优先级，数字枚举型，【1，3，5】，1：高；3：普通（默认）；5：低，可选项；
> 
> - hasReplySign：邮件是否需要打开回执，bool型，true：需要回执，false：不需要回执（默认），可选项；
> 
> - bodyText：需发送邮件文本正文，内容base64编码，字符串类型，可选项；
> 
> - bodyHtml：需发送邮件html正文，内容base64编码，字符串类型，可选项；
> 
> - attachments：本地附件信息集，数组类型，可选项，数组成员为json格式定义如下：
> 
>  - fileName：附件名称，包含后缀名，字符串类型；
>  
>  - filePath：本地附件路径，支持res:，file:前缀，字符串类型；

callbackFun：邮箱发送回调，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字类型，0：邮件发送成功；-1：邮件发送失败

返回值：无



<span id="ff_11">**sendMplusMessage(jsonData:Object,callbackFun:Function):void**</span>

<code> 连接Mplus邮件服务器使用自定义接口发送邮件</code>

参数：

jsonData：json格式，定义如下：

> accountInfo：邮箱账号信息，必选项，json格式，定义如下：
> 
> - user：邮箱账号名，字符串类型，必选项；
> 
> serverInfo：Mplus自定义邮件服务器设置，必选项，json格式，定义如下：
> 
> - url：服务器地址，支持http:、https:前缀路径，必选项；
> 
> - salt：aes：加密密钥，字符串类型，必选项；
> 
> - token：mplus平台登录token值，字符串类型，必选项；
> 
> message：需发送邮件信息，必选项，json格式，定义如下：
> 
> - subject：邮件标题，字符串类型，可选项；
> 
> - sendDate：邮件发送时间，字符串类型，可选项，格式：yy-MM-dd HH: mm: ss
> 
> - messageId：邮件消息标识，字符串类型，可选项；
> 
> - from：发件人邮箱，json格式定义，如下：
> 
>  - name：发件人名称，字符串类型，可选项；
>  
>  - address：发件人邮箱地址，字符串类型，必选项；
>  
> - to：接收人邮箱，json数组类型，json定义如下：
> 
>  - name：接收人名称，字符串类型，可选项；
>  
>  - address：接收人邮箱地址，字符串类型，必选项；
>  
> - cc：抄送人邮箱，json数组类型，定义如下：
> 
>  - name：抄送人名称，字符串类型，可选项；
>  
>  - address：抄送人邮箱地址，字符串类型，必选项；
>  
> - bcc：密送人邮箱，json数组类型，定义如下：
> 
>  - name：密送人名称，字符串类型，可选项；
>  
>  - address：密送人邮箱地址，字符串类型，必选项；
>  
> - sendType：邮件发送类型，数字枚举型，【1，2，3，4】，1：新建发送邮件；2：回复邮件；3：全部回复；4：转发邮件；
> 
> - priority：邮件优先级，数字枚举型，【1，3，5】，1：高；3：普通（默认）；5：低，可选项；
> 
> - hasReplySign：邮件是否需要打开回执，bool型，true：需要回执；false：不需要回执（默认），可选项；
> 
> - bodyText：需发送邮件文本正文，内容banse64编码，字符串类型，可选项；
> 
> - bodyHtml：需发送邮件html正文，内容base64编码，字符串类型，可选项；
> 
> - attachments：本地附件信息集，数组类型，可选项，数组成员为json格式，定义如下：
> 
>  - filename：附件名称，包含后缀名，字符串类型；
>  
>  - filePath：本地附件路径，支持res:、file:前缀，字符串类型；
>  
> - networkAttachment：服务端未下载邮件附件信息集，数组类型，可选项，数组成员为json格式，定义如下：
> 
>  - fowardMailAccount：原邮件账号，字符串类型，必选项；
>  
>  - uid：附件所在邮件唯一标识，字符串类型，必选项；
>  
>  - attachName：附件名称，字符串类型，必选项；
>  
>  - attachOrder：附件索引，数字，从0开始，必选项；

callbackFun：邮箱发送回调，该函数具有json类型入参，定义如下：

> code：回应状态码，数字类型，0：邮件发送成功；-1：邮件附件上传失败；-2：邮件发送失败；

返回值：无
