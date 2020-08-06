---
title: 为 DQS 日志文件配置高级设置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- log files,advanced settings
- dqs log files,advanced settings
ms.assetid: 1d565748-9759-425c-ae38-4d2032a86868
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ad41b0cac95f9bfe5565ccbac16b0fda3e28ddf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683078"
---
# <a name="configure-advanced-settings-for-dqs-log-files"></a><span data-ttu-id="e8988-102">为 DQS 日志文件配置高级设置</span><span class="sxs-lookup"><span data-stu-id="e8988-102">Configure Advanced Settings for DQS Log Files</span></span>
  <span data-ttu-id="e8988-103">本主题介绍如何为 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 和 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 日志文件配置高级设置，例如设置日志文件的滚动文件大小限制、设置事件的时间戳模式等。</span><span class="sxs-lookup"><span data-stu-id="e8988-103">This topic describes how to configure advanced settings for [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] and [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log files, such as set the rolling file size limit of the log files, set the time stamp pattern of the events, and so on.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8988-104">这些活动不能使用 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]执行，并且仅面向高级用户。</span><span class="sxs-lookup"><span data-stu-id="e8988-104">These activities cannot be performed using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], and is intended for advanced users only.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e8988-105">开始之前</span><span class="sxs-lookup"><span data-stu-id="e8988-105">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e8988-106">Security</span><span class="sxs-lookup"><span data-stu-id="e8988-106">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e8988-107">权限</span><span class="sxs-lookup"><span data-stu-id="e8988-107">Permissions</span></span>  
  
-   <span data-ttu-id="e8988-108">您的 Windows 用户帐户必须是 SQL Server 实例中 sysadmin 固定服务器角色的成员，才能修改 DQS_MAIN 中 A_CONFIGURATION 表的配置设置。</span><span class="sxs-lookup"><span data-stu-id="e8988-108">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance to modify configuration settings in the A_CONFIGURATION table in the DQS_MAIN database.</span></span>  
  
-   <span data-ttu-id="e8988-109">您必须以正在修改 DQLog.Client.xml 文件以便配置 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 日志记录的计算机上 Administrators 组成员的身份登录。</span><span class="sxs-lookup"><span data-stu-id="e8988-109">You must be logged on as a member of the Administrators group on the computer where you are modifying the DQLog.Client.xml file to configure the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] logging settings.</span></span>  
  
##  <a name="configure-data-quality-server-log-settings"></a><a name="DQSServer"></a><span data-ttu-id="e8988-110">配置数据质量服务器日志设置</span><span class="sxs-lookup"><span data-stu-id="e8988-110">Configure Data Quality Server Log Settings</span></span>  
 <span data-ttu-id="e8988-111">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 日志设置在 DQS_MAIN 数据库的 A_CONFIGURATION 表中 **ServerLogging** 行的 **VALUE** 列中以 XML 格式提供。</span><span class="sxs-lookup"><span data-stu-id="e8988-111">The [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log settings are present in an XML format in the **VALUE** column of the **ServerLogging** row in the A_CONFIGURATION table in the DQS_MAIN database.</span></span> <span data-ttu-id="e8988-112">您可以运行以下 SQL 查询以便查看配置信息：</span><span class="sxs-lookup"><span data-stu-id="e8988-112">You can run the following SQL query to view the configuration information:</span></span>  
  
```sql  
select * from DQS_MAIN.dbo.A_CONFIGURATION where NAME='ServerLogging'; 
```  
  
 <span data-ttu-id="e8988-113">若要更改 \*\*\*\* 日志记录的配置设置，您必须在 **ServerLogging** 行的 VALUE [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 列中更新相应信息。</span><span class="sxs-lookup"><span data-stu-id="e8988-113">You must update the appropriate information in the **VALUE** column of the **ServerLogging** row to change the configuration settings for [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] logging.</span></span> <span data-ttu-id="e8988-114">在此示例中，我们将更新 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 日志设置，以便将滚动文件大小限制设置为 25000 KB（默认值为 20000 KB）。</span><span class="sxs-lookup"><span data-stu-id="e8988-114">In this example, we will update the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log settings to set the rolling file size limit to 25000 KB (the default is 20000 KB).</span></span>  
  
1.  <span data-ttu-id="e8988-115">启动 Microsoft SQL Server Management Studio 并连接到适当的 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="e8988-115">Start Microsoft SQL Server Management Studio, and connect to the appropriate SQL Server instance.</span></span>  
  
2.  <span data-ttu-id="e8988-116">在“对象资源管理器”中，右键单击服务器，再单击 **“新建查询”**。</span><span class="sxs-lookup"><span data-stu-id="e8988-116">In Object Explorer, right-click the server, and then click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e8988-117">在“查询编辑器”窗口中，复制以下 SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="e8988-117">In the Query Editor window, copy the following SQL statements:</span></span>  
  
    ```sql  
    -- Begin the transaction.  
    BEGIN TRAN  
    GO  
    -- set the XML value field for the row with name=ServerLogging  
    update DQS_MAIN.dbo.A_CONFIGURATION   
    set VALUE='<configuration>  
      <configSections>  
        <section name="loggingConfiguration" type="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.LoggingSettings, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" />  
      </configSections>  
      <loggingConfiguration name="Logging Application Block" tracingEnabled="true" defaultCategory="" logWarningsWhenNoCategoriesMatch="true">  
        <listeners>  
          <add fileName="###REPLACE_THIS_WITH_SQL_SERVER_INSTANCE_LOG_FOLDER_NAME###DQServerLog.###REPLACE_THIS_WITH_SQL_CATALOG_NAME###.log" footer="" formatter="Custom Text Formatter" header="" rollFileExistsBehavior="Increment" rollInterval="None" rollSizeKB="25000" timeStampPattern="yyyy-MM-dd" listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" traceOutputOptions="None" filter="All" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="Rolling Flat File Trace Listener" />  
        </listeners>  
        <formatters>  
          <add template="{timestamp(local)}|[{threadName}]|{dictionary({value}|)}{message}" type="Microsoft.Practices.EnterpriseLibrary.Logging.Formatters.TextFormatter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="Custom Text Formatter" />  
        </formatters>  
        <logFilters>  
          <add enabled="true" type="Microsoft.Practices.EnterpriseLibrary.Logging.Filters.LogEnabledFilter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="LogEnabled Filter" />  
        </logFilters>  
        <categorySources />  
        <specialSources>  
          <allEvents switchValue="All" name="All Events" />  
          <notProcessed switchValue="All" name="Unprocessed Category" />  
          <errors switchValue="All" name="Logging Errors & Warnings">  
            <listeners>  
              <add name="Rolling Flat File Trace Listener" />  
            </listeners>  
          </errors>  
        </specialSources>  
      </loggingConfiguration>  
    </configuration>'  
    WHERE NAME='ServerLogging'  
    GO  
    -- check the result  
    select * from DQS_MAIN.dbo.A_CONFIGURATION where NAME='ServerLogging'  
  
    -- Commit the transaction.  
    COMMIT TRAN  
  
    ```  
  
4.  <span data-ttu-id="e8988-118">按 F5 执行这些语句。</span><span class="sxs-lookup"><span data-stu-id="e8988-118">Press F5 to execute the statements.</span></span> <span data-ttu-id="e8988-119">检查 "**结果**" 窗格以验证语句是否已成功执行。</span><span class="sxs-lookup"><span data-stu-id="e8988-119">Check the **Results** pane to verify that the statements have executed successfully.</span></span>  
  
5.  <span data-ttu-id="e8988-120">若要应用对 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 日志记录配置进行的更改，您必须运行以下 Transact-SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="e8988-120">To apply changes done to the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] logging configuration, you must run the following Transact-SQL statements.</span></span> <span data-ttu-id="e8988-121">打开新的“查询编辑器”窗口，然后粘贴以下 Transact-SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="e8988-121">Open a new Query Editor window, and paste the following Transact-SQL statements:</span></span>  
  
    ```sql  
    USE [DQS_MAIN]  
    GO  
    DECLARE @return_value int  
    EXEC @return_value = [internal_core].[RefreshLogSettings]  
    SELECT 'Return Value' = @return_value  
    GO  
    ```  
  
6.  <span data-ttu-id="e8988-122">按 F5 执行这些语句。</span><span class="sxs-lookup"><span data-stu-id="e8988-122">Press F5 to execute the statements.</span></span> <span data-ttu-id="e8988-123">检查 "**结果**" 窗格以验证语句是否已成功执行。</span><span class="sxs-lookup"><span data-stu-id="e8988-123">Check the **Results** pane to verify that the statements have executed successfully.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8988-124">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 日志记录设置配置动态生成并且存储于 DQS_MAIN.Log 文件中，该文件通常位于 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log 下（如果您安装了 SQL Server 的默认实例）。</span><span class="sxs-lookup"><span data-stu-id="e8988-124">The [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] logging settings configuration is dynamically generated and stored in the DQS_MAIN.Log file, which is typically available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log if you installed the default instance of SQL Server.</span></span> <span data-ttu-id="e8988-125">但是，将不会保存在此文件中直接进行的更改，它们将会被 DQS_MAIN 数据库中 A_CONFIGURATION 表的配置设置覆盖。</span><span class="sxs-lookup"><span data-stu-id="e8988-125">However, changes done directly in this file do not hold, and are overwritten by the configuration settings in the A_CONFIGURATION table in the DQS_MAIN database.</span></span>  
  
##  <a name="configure-data-quality-client-log-settings"></a><a name="DQSClient"></a><span data-ttu-id="e8988-126">配置 Data Quality Client 日志设置</span><span class="sxs-lookup"><span data-stu-id="e8988-126">Configure Data Quality Client Log Settings</span></span>  
 <span data-ttu-id="e8988-127">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]日志设置配置文件 DQLog.Client.xml 通常在 C:\Program FILES\MICROSOFT SQL server\120\tools\binn\dq\config。上提供。XML 文件的内容类似于您之前为日志配置设置修改的 XML 文件 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e8988-127">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log setting configuration file, DQLog.Client.xml, is typically available at C:\Program Files\Microsoft SQL Server\120\Tools\Binn\DQ\config. The contents of the XML file is similar to the XML file that you modified earlier for the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log configuration settings.</span></span> <span data-ttu-id="e8988-128">配置 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 日志设置：</span><span class="sxs-lookup"><span data-stu-id="e8988-128">To configure the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log settings:</span></span>  
  
1.  <span data-ttu-id="e8988-129">以管理员身份运行任何 XML 编辑工具或记事本。</span><span class="sxs-lookup"><span data-stu-id="e8988-129">Run any XML editing tool or notepad as an administrator.</span></span>  
  
2.  <span data-ttu-id="e8988-130">在工具或记事本中打开 DQLog.Client.xml 文件。</span><span class="sxs-lookup"><span data-stu-id="e8988-130">Open the DQLog.Client.xml file in the tool or notepad.</span></span>  
  
3.  <span data-ttu-id="e8988-131">进行所需更改，然后保存该文件以便应用新的日志记录更改。</span><span class="sxs-lookup"><span data-stu-id="e8988-131">Make the required changes, and save the file to apply the new logging changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8988-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e8988-132">See Also</span></span>  
 [<span data-ttu-id="e8988-133">为 DQS 日志文件配置严重级别</span><span class="sxs-lookup"><span data-stu-id="e8988-133">Configure Severity Levels for DQS Log Files</span></span>](../../2014/data-quality-services/configure-severity-levels-for-dqs-log-files.md)  
  
  
