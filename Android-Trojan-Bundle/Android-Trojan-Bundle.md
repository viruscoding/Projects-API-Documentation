## Android-Trojan-Bundle接口说明


### upload接口:

	Method:POST
	URL: /upload?ip=192.168.1.123&port=8888
	Upload Format：the form must has enctype="multipart/form-data"
	Upload Format: <input type="file" name="file"> 

请求参数说明:

	ip: 木马反弹tcp的ip地址
	port: 木马反弹tcp的端口

返回参数说明:

	上传失败格式: {"des":"xxx", "status":"err"}
	上传成功格式: {"des":"ok", "status":"ok", "apkname":"xxx.apk"}

| 参数 | 说明 |
| --- | --- |
| status | 两个值: ok&nbsp;&nbsp;&nbsp;&nbsp;err |
| des | 如果上传失败，描述错误信息；方便调试，建议写入日志 |
| apkname | apk name，用于检测后台绑定进度或者下载绑定完成的apk |




### checkstatus接口:

	Method:GET 
	URL: /checkstatus/<apkname>

返回参数说明:

	格式: {"des":"xxx", "status":"xxx"}

| 参数 | 说明 |
| --- | --- |
| status | 四个值: processing&nbsp;&nbsp;&nbsp;&nbsp;completed&nbsp;&nbsp;&nbsp;&nbsp;uncompleted&nbsp;&nbsp;&nbsp;&nbsp;err |
|		| processing: apk正在捆绑中 |
|		| completed: 捆绑完成 ， |
|		| uncompleted: apk捆绑失败 |
|		| err: 任务不存在 |
| des | 如果出错，描述错误信息；方便调试，建议写入日志 |



### download接口:

	Method:GET 
	URL: /download/<apkname>

返回参数说明:
	
	下载失败，状态码为：404
	下载失败响应数据格式: {"des":"xxx", "status":"err"}

| 参数 | 说明 |
| --- | --- |
| status | err |
| des | 描述错误信息；方便调试，建议写入日志|
