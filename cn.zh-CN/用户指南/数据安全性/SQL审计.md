# SQL审计 {#concept_njf_cr4_ydb .concept}

您可以通过RDS的SQL审计功能查看SQL明细、定期审计SQL。开通SQL审计功能后，实例性能不会受到影响。

**说明：** 

-   RDS for SQL Server 2012/2016以及MariaDB TX实例暂不支持SQL审计功能。
-   开启SQL审计功能之前的记录无法查看到。

## SQL审计与Binlog日志的区别 {#section_uyq_kr4_ydb .section}

RDS for MySQL版的增量数据可以通过SQL审计或Binlog日志来查看，但是两者又有区别：

-   SQL审计：类似于MySQL的审计日志，会统计所有DML和DDL操作信息，这些信息是系统通过网络协议分析所得。SQL审计不解析实际的参数值，在SQL查询量较大的时候会丢失少量记录。因此通过这种方式来统计增量数据可能会出现不准确的情况。
-   Binlog日志：准确记录数据库所有的增、删、改操作信息以及恢复用户的增量数据。Binlog日志先暂存在实例中，系统定期将实例中已经写完数据的Binlog日志转移至OSS保存7天。无法保存正在写入数据的Binlog文件，所以单击**一键上传Binlog**后仍有部分Binlog日志没有被上传。这种方式可以准确记录数据库的增量数据，但是无法获取实时日志。

## 注意事项 {#section_tz4_kr4_ydb .section}

-   开通SQL审计功能后，实例性能不会受到影响。
-   SQL审计的保存时间为30天。
-   SQL审计导出的文件可以保存2天，超过2天的会被系统定时清理。
-   SQL审计默认关闭。开启该功能后，实例会产生额外费用，详细收费标准请参见[云数据库RDS详细价格信息](https://www.aliyun.com/price/product#/rds/detail)。

## 开启SQL审计 {#section_bwj_nr4_ydb .section}

1.  登录[RDS管理控制台](https://rds.console.aliyun.com/)。
2.  在页面左上角，选择实例所在地域。
3.  找到目标实例，单击实例ID。
4.  在左侧导航栏中单击**数据安全性**。
5.  选择**SQL审计**页签，单击**开启SQL审计**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7947/154095056021214_zh-CN.png)

6.  在弹出的确认框中单击**确定**。

    开启SQL审计后，您可以通过时间、DB、User、关键字等条件查询SQL信息。


## 关闭SQL审计 {#section_o4j_sr4_ydb .section}

为节约成本，您可以在不需要审计SQL时关闭SQL审计功能，详细步骤如下。

**说明：** SQL审计功能关闭后，包括历史审计内容在内的SQL审计记录会被清空。请将SQL审计内容导出并妥善保存至本地后，再关闭SQL审计功能。

1.  登录[RDS管理控制台](https://rds.console.aliyun.com/)。
2.  在页面左上角，选择实例所在地域。
3.  找到目标实例，单击实例ID。
4.  在左侧导航栏中单击**数据安全性**。
5.  选择**SQL审计**页签，单击**导出文件**，将SQL审计内容导出并妥善保存至本地。
6.  导出文件后单击**关闭SQL审计**。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/26197/cn_zh/1516174510024/%E5%85%B3%E9%97%ADSQL%E5%AE%A1%E8%AE%A1.png)

7.  在弹出的确认框中，单击**确定**。

## 相关文档 {#section_z4k_xr4_ydb .section}

您可以在阿里云数据管理（简称DMS）的控制台上查看通过DMS登录RDS实例的所有访问日志，详情请参见[访问日志](https://help.aliyun.com/document_detail/47574.html)。

