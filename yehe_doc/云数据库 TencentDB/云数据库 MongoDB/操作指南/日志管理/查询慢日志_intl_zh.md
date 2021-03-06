在 MongoDB 中慢日志经常作为优化业务操作的依据。关于慢日志的更多信息请参考 [官方文档](https://docs.mongodb.com/manual/tutorial/manage-the-database-profiler/)。[云数据库 MongoDB 控制台](https://console.cloud.tencent.com/mongodb) 为您提供可查询慢日志的操作界面。

>
>- 系统会记录执行时间超过100毫秒的操作。
>- 慢日志保留时间为7天，建议每次查询时间跨度不超过1天。
>- 查询仅限前1万条慢日志，若查询结果缓慢，请缩小查询时间范围。


登录 [MongoDB 控制台](https://console.cloud.tencent.com/mongodb)，单击实例名进入实例管理页面，选择【数据库管理】>【慢日志查询】页，可以浏览分析慢日志。

#### 查询方式 
系统为您提供两种查询方式，分别详述如下：
- 抽象查询：根据 command（操作）类型进行的聚合查询分析。
- 具体查询：指定时间段内的慢日志详情。

#### 查询结果
抽象查询结果中包含四个字段：
- 查询方式：跟用户的选择一致，此种方式下是抽象查询。
- 样例语句：以 command 类型为聚合维度而输出的语句，用户排查问题时主要参考 command。
- 平均执行时间（MS）：以 command 类型为维度聚合的操作的平均执行时间，单位是毫秒。
- 总次数：以 command 类型为维度聚合的操作的次数统计。
![](https://main.qcloudimg.com/raw/07a66dab61f3842de50b400faf3b08d5.png)


具体查询结果包含三个字段：
- 查询方式：跟用户的选择一致，此种方式下是抽象查询。
- 耗时：业务命令的执行时间，单位为毫秒。
- 日志详情：业务命令详情。
![](https://main.qcloudimg.com/raw/e063ea622dbd6bb8b73d4b488a33d2ae.png)
