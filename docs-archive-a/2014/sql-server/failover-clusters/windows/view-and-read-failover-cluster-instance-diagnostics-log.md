---
title: 查看和读取故障转移群集实例诊断日志 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 68074bd5-be9d-4487-a320-5b51ef8e2b2d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 774dc4ec4a02c72420d004909cb7e6ee1b31f3a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586256"
---
# <a name="view-and-read-failover-cluster-instance-diagnostics-log"></a><span data-ttu-id="6cb6c-102">查看和读取故障转移群集实例诊断日志</span><span class="sxs-lookup"><span data-stu-id="6cb6c-102">View and Read Failover Cluster Instance Diagnostics Log</span></span>
  <span data-ttu-id="6cb6c-103">将 SQL Server 资源 DLL 的所有严重错误和警告事件写入 Windows 事件日志。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-103">All critical errors and warning events for the SQL Server Resource DLL are written to the Windows event log.</span></span> <span data-ttu-id="6cb6c-104">正在运行的特定于 SQL Server 的诊断信息日志由 [sp_server_diagnostics (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)系统存储过程捕获，并会写入 SQL Server 故障转移群集诊断日志文件（也称为 *SQLDIAG* 日志）中。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-104">A running log of the diagnostic information specific to SQL Server is captured by the [sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) system stored procedure and is written to the SQL Server failover cluster diagnostics (also known as the *SQLDIAG* logs) log files.</span></span>  
  
-   <span data-ttu-id="6cb6c-105">**开始之前：**  [建议](#Recommendations)、 [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="6cb6c-105">**Before you begin:**  [Recommendations](#Recommendations), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="6cb6c-106">**若要查看诊断日志，请使用：**  [SQL Server Management Studio](#SSMSProcedure)、 [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="6cb6c-106">**To View the Diagnostic Log, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
-   <span data-ttu-id="6cb6c-107">**若要配置诊断日志设置，请使用：** [Transact-SQL](#TsqlConfigure)</span><span class="sxs-lookup"><span data-stu-id="6cb6c-107">**To Configure Diagnostic Log settings, using:** [Transact-SQL](#TsqlConfigure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6cb6c-108">开始之前</span><span class="sxs-lookup"><span data-stu-id="6cb6c-108">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="6cb6c-109">建议</span><span class="sxs-lookup"><span data-stu-id="6cb6c-109">Recommendations</span></span>  
 <span data-ttu-id="6cb6c-110">默认情况下，SQLDIAG 存储在 SQL Server 实例目录的本地 LOG 文件夹下，例如 "C\Program Files\Microsoft SQL Server\MSSQL12. \<InstanceName>AlwaysOn 故障转移群集实例的拥有节点 (FCI) 的 \MSSQL\LOG '。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-110">By default, the SQLDIAG are stored under a local LOG folder of the SQL Server instance directory, for example, 'C\Program Files\Microsoft SQL Server\MSSQL12.\<InstanceName>\MSSQL\LOG' of the owning node of the AlwaysOn Failover Cluster Instance (FCI).</span></span> <span data-ttu-id="6cb6c-111">每个 SQLDIAG 日志文件的大小固定为 100 MB。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-111">The size of each SQLDIAG log file is fixed at 100 MB.</span></span> <span data-ttu-id="6cb6c-112">在被回收用于新日志之前，计算机上有十个这样的日志文件。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-112">Ten such log files are stored on the computer before they are recycled for new logs.</span></span>  
  
 <span data-ttu-id="6cb6c-113">这些日志使用扩展事件文件格式。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-113">The logs use the extended events file format.</span></span> <span data-ttu-id="6cb6c-114">**sys.fn_xe_file_target_read_file** 系统函数可用于读取由扩展事件创建的文件。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-114">The **sys.fn_xe_file_target_read_file** system function can be used to read the files that are created by Extended Events.</span></span> <span data-ttu-id="6cb6c-115">每行返回一个 XML 格式的事件。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-115">One event, in XML format, is returned per row.</span></span> <span data-ttu-id="6cb6c-116">查询系统视图以将 XML 数据作为结果集分析。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-116">Query the system view to parse the XML data as a result-set.</span></span> <span data-ttu-id="6cb6c-117">有关详细信息，请参阅 [sys.fn_xe_file_target_read_file (Transact SQL)](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-117">For more information, see [sys.fn_xe_file_target_read_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6cb6c-118">Security</span><span class="sxs-lookup"><span data-stu-id="6cb6c-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6cb6c-119">权限</span><span class="sxs-lookup"><span data-stu-id="6cb6c-119">Permissions</span></span>  
 <span data-ttu-id="6cb6c-120">运行 **fn_xe_file_target_read_file**需要 VIEW SERVER STATE 权限。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-120">VIEW SERVER STATE permission is needed to run **fn_xe_file_target_read_file**.</span></span>  
  
 <span data-ttu-id="6cb6c-121">以管理员身份打开 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6cb6c-121">Open SQL Server Management Studio as Administrator</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6cb6c-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6cb6c-122">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="6cb6c-123">**查看诊断日志文件：**</span><span class="sxs-lookup"><span data-stu-id="6cb6c-123">**To view the Diagnostic log files:**</span></span>  
  
1.  <span data-ttu-id="6cb6c-124">从“文件”\*\*\*\* 菜单，选择“打开文件”\*\*\*\*\*\*\*\*，然后选择要查看的诊断日志文件。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-124">From the **File** menu, select **Open**, **File**, and choose the diagnostic log file you want to view.</span></span>  
  
2.  <span data-ttu-id="6cb6c-125">事件在右窗格中显示为行，默认情况下，仅显示出 **name**和 **timestamp** 这两列。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-125">The events are displayed as rows in the right pane, and by default **name**, and **timestamp** are the only two columns displayed.</span></span>  
  
     <span data-ttu-id="6cb6c-126">这还会激活 **“扩展事件”** 菜单。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-126">This also activates the **ExtendedEvents** menu.</span></span>  
  
3.  <span data-ttu-id="6cb6c-127">若要查看更多列，转到 **“扩展事件”** 菜单，然后选择 **“选择列”**。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-127">To see more columns, go the **ExtendedEvents** menu, and select **Choose Columns**.</span></span>  
  
     <span data-ttu-id="6cb6c-128">将打开一个显示出可用列的对话框，您可在其中选择要显示的列。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-128">A dialog box opens with the available columns allowing you to select the columns for display.</span></span>  
  
4.  <span data-ttu-id="6cb6c-129">您可使用 **“扩展事件”** 菜单并选择 **“筛选”** 选项对事件数据进行筛选和排序。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-129">You can filter, and sort the event data using the **ExtendedEvents** menu and selecting the **Filter** option.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6cb6c-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6cb6c-130">Using Transact-SQL</span></span>  
 <span data-ttu-id="6cb6c-131">**查看诊断日志文件：**</span><span class="sxs-lookup"><span data-stu-id="6cb6c-131">**To view the Diagnostic log files:**</span></span>  
  
 <span data-ttu-id="6cb6c-132">若要查看 SQLDIAG 日志文件中的所有日志项，请使用以下查询：</span><span class="sxs-lookup"><span data-stu-id="6cb6c-132">To view all the log items in the SQLDIAG log file, use the following query:</span></span>  
  
```  
SELECT  
xml_data.value('(event/@name)[1]','varchar(max)') AS 'Name'  
,xml_data.value('(event/@package)[1]','varchar(max)') AS 'Package'  
,xml_data.value('(event/@timestamp)[1]','datetime') AS 'Time'  
,xml_data.value('(event/data[@name=''state'']/value)[1]','int') AS 'State'  
,xml_data.value('(event/data[@name=''state_desc'']/text)[1]','varchar(max)') AS 'State Description'  
,xml_data.value('(event/data[@name=''failure_condition_level'']/value)[1]','int') AS 'Failure Conditions'  
,xml_data.value('(event/data[@name=''node_name'']/value)[1]','varchar(max)') AS 'Node_Name'  
,xml_data.value('(event/data[@name=''instancename'']/value)[1]','varchar(max)') AS 'Instance Name'  
,xml_data.value('(event/data[@name=''creation time'']/value)[1]','datetime') AS 'Creation Time'  
,xml_data.value('(event/data[@name=''component'']/value)[1]','varchar(max)') AS 'Component'  
,xml_data.value('(event/data[@name=''data'']/value)[1]','varchar(max)') AS 'Data'  
,xml_data.value('(event/data[@name=''info'']/value)[1]','varchar(max)') AS 'Info'  
FROM  
 ( SELECT object_name AS 'event'  
  ,CONVERT(xml,event_data) AS 'xml_data'  
  FROM sys.fn_xe_file_target_read_file('C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log\SQLNODE1_MSSQLSERVER_SQLDIAG_0_129936003752530000.xel',NULL,NULL,NULL)   
)   
AS XEventData  
ORDER BY Time;  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="6cb6c-133">您可以使用 WHERE 子句针对特定的组件或状态筛选结果。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-133">You can filter the results for specific components or state using the WHERE clause.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlConfigure"></a> <span data-ttu-id="6cb6c-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6cb6c-134">Using Transact-SQL</span></span>  
 <span data-ttu-id="6cb6c-135">**配置诊断日志属性**</span><span class="sxs-lookup"><span data-stu-id="6cb6c-135">**To configure the Diagnostic Log Properties**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6cb6c-136">有关此过程的示例，请参阅本节后面的 [示例 (Transact-SQL)](#TsqlExample)。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-136">For an example of this procedure, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
 <span data-ttu-id="6cb6c-137">使用数据定义语言 (DDL) 语句， `ALTER SERVER CONFIGURATION` 可以启动或停止记录由[Sp_server_diagnostics &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)过程捕获的诊断数据，并设置 SQLDIAG 日志配置参数，如日志文件滚动更新计数、日志文件大小和文件位置。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-137">Using the Data Definition Language (DDL) statement, `ALTER SERVER CONFIGURATION`, you can start or stop logging diagnostic data captured by the [sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) procedure, and set SQLDIAG log configuration parameters such as the log file rollover count, log file size, and file location.</span></span> <span data-ttu-id="6cb6c-138">有关语法详细信息，请参阅 [Setting diagnostic log options](/sql/t-sql/statements/alter-server-configuration-transact-sql#Diagnostic)。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-138">For syntax details, see [Setting diagnostic log options](/sql/t-sql/statements/alter-server-configuration-transact-sql#Diagnostic).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="ConfigTsqlExample"></a> <span data-ttu-id="6cb6c-139">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6cb6c-139">Examples (Transact-SQL)</span></span>  
  
####  <a name="setting-diagnostic-log-options"></a><a name="TsqlExample"></a> <span data-ttu-id="6cb6c-140">Setting diagnostic log options</span><span class="sxs-lookup"><span data-stu-id="6cb6c-140">Setting diagnostic log options</span></span>  
 <span data-ttu-id="6cb6c-141">本节中的示例说明如何设置诊断日志选项的值。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-141">The examples in this section show how to set the values for the diagnostic log option.</span></span>  
  
##### <a name="a-starting-diagnostic-logging"></a><span data-ttu-id="6cb6c-142">A.</span><span class="sxs-lookup"><span data-stu-id="6cb6c-142">A.</span></span> <span data-ttu-id="6cb6c-143">启动诊断日志记录</span><span class="sxs-lookup"><span data-stu-id="6cb6c-143">Starting diagnostic logging</span></span>  
 <span data-ttu-id="6cb6c-144">下面的示例启动诊断数据的日志记录。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-144">The following example starts the logging of diagnostic data.</span></span>  
  
```  
ALTER SERVER CONFIGURATION SET DIAGNOSTICS LOG ON;  
```  
  
##### <a name="b-stopping-diagnostic-logging"></a><span data-ttu-id="6cb6c-145">B.</span><span class="sxs-lookup"><span data-stu-id="6cb6c-145">B.</span></span> <span data-ttu-id="6cb6c-146">停止诊断日志记录</span><span class="sxs-lookup"><span data-stu-id="6cb6c-146">Stopping diagnostic logging</span></span>  
 <span data-ttu-id="6cb6c-147">下面的示例停止诊断数据的日志记录。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-147">The following example stops the logging of diagnostic data.</span></span>  
  
```  
ALTER SERVER CONFIGURATION SET DIAGNOSTICS LOG OFF;  
```  
  
##### <a name="c-specifying-the-location-of-the-diagnostic-logs"></a><span data-ttu-id="6cb6c-148">C.</span><span class="sxs-lookup"><span data-stu-id="6cb6c-148">C.</span></span> <span data-ttu-id="6cb6c-149">指定诊断日志的位置</span><span class="sxs-lookup"><span data-stu-id="6cb6c-149">Specifying the location of the diagnostic logs</span></span>  
 <span data-ttu-id="6cb6c-150">下面的示例将诊断日志的位置设置为指定的文件路径。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-150">The following example sets the location of the diagnostic logs to the specified file path.</span></span>  
  
```  
ALTER SERVER CONFIGURATION  
SET DIAGNOSTICS LOG PATH = 'C:\logs';  
```  
  
##### <a name="d-specifying-the-maximum-size-of-each-diagnostic-log"></a><span data-ttu-id="6cb6c-151">D.</span><span class="sxs-lookup"><span data-stu-id="6cb6c-151">D.</span></span> <span data-ttu-id="6cb6c-152">指定每个诊断日志的最大大小</span><span class="sxs-lookup"><span data-stu-id="6cb6c-152">Specifying the maximum size of each diagnostic log</span></span>  
 <span data-ttu-id="6cb6c-153">下面的示例将每个诊断日志的最大大小设置为 10 MB。</span><span class="sxs-lookup"><span data-stu-id="6cb6c-153">The following example set the maximum size of each diagnostic log to 10 megabytes.</span></span>  
  
```  
ALTER SERVER CONFIGURATION   
SET DIAGNOSTICS LOG MAX_SIZE = 10 MB;  
```  
  
## <a name="see-also"></a><span data-ttu-id="6cb6c-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6cb6c-154">See Also</span></span>  
 [<span data-ttu-id="6cb6c-155">Failover Policy for Failover Cluster Instances</span><span class="sxs-lookup"><span data-stu-id="6cb6c-155">Failover Policy for Failover Cluster Instances</span></span>](failover-policy-for-failover-cluster-instances.md)  
  
  
