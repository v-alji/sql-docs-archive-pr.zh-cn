---
title: 创建和测试分类器用户定义函数 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, classifier function create
- classifier function [SQL Server], test
- classifier function [SQL Server], create
- Resource Governor, classifier function test
ms.assetid: 7866b3c9-385b-40c6-aca5-32d3337032be
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1b8e5371762e38cf2b3ac8c1d506b467dcfa7e3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689316"
---
# <a name="create-and-test-a-classifier-user-defined-function"></a><span data-ttu-id="e0fb2-102">创建和测试分类器用户定义函数</span><span class="sxs-lookup"><span data-stu-id="e0fb2-102">Create and Test a Classifier User-Defined Function</span></span>
  <span data-ttu-id="e0fb2-103">本主题说明如何创建和测试分类器用户定义函数 (UDF)。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-103">This topic shows how to create and test a classifier user-defined function (UDF).</span></span> <span data-ttu-id="e0fb2-104">这些步骤涉及在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询编辑器中执行 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-104">The steps involve executing [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor.</span></span>  
  
 <span data-ttu-id="e0fb2-105">下面的过程中显示的示例说明了创建非常复杂的分类器用户定义函数的可能性。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-105">The example shown in the following procedure illustrates the possibilities for creating a fairly complex classifier user-defined function.</span></span>  
  
 <span data-ttu-id="e0fb2-106">在示例中：</span><span class="sxs-lookup"><span data-stu-id="e0fb2-106">In our example:</span></span>  
  
-   <span data-ttu-id="e0fb2-107">创建了 pProductionProcessing 资源池和 gProductionProcessing 工作负荷组，用于在指定时间范围内进行生产处理。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-107">A resource pool (pProductionProcessing) and workload group (gProductionProcessing) are created for production processing during a specified time range.</span></span>  
  
-   <span data-ttu-id="e0fb2-108">创建了 pOffHoursProcessing 资源池和 gOffHoursProcessing 工作负荷组，用于处理不符合生产处理要求的连接。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-108">A resource pool (pOffHoursProcessing) and workload group (gOffHoursProcessing) are created for handling connections that do not meet the requirements for production processing.</span></span>  
  
-   <span data-ttu-id="e0fb2-109">在 master 中创建了 TblClassificationTimeTable 表，用于保存可根据登录时间计算的开始和结束时间。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-109">A table (TblClassificationTimeTable) is created in master to hold start and end times that can be evaluated against a login time.</span></span> <span data-ttu-id="e0fb2-110">必须在 master 中创建该表，因为资源调控器对分类器函数使用了架构绑定。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-110">This must be created in master because Resource Governor uses schema binding for classifier functions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e0fb2-111">作为一种最佳做法，您不应在 master 中存储经常更新的大型表。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-111">As a best practice, you should not store large, frequently updated tables in master.</span></span>  
  
 <span data-ttu-id="e0fb2-112">分类器函数可能延长登录时间。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-112">The classifier function extends the login time.</span></span> <span data-ttu-id="e0fb2-113">过于复杂的函数可能会导致登录超时或减慢快速连接速度。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-113">An overly complex function can cause logins to time out or slow down fast connections.</span></span>  
  
### <a name="to-create-the-classifier-user-defined-function"></a><span data-ttu-id="e0fb2-114">创建分类器用户定义函数</span><span class="sxs-lookup"><span data-stu-id="e0fb2-114">To create the classifier user-defined function</span></span>  
  
1.  <span data-ttu-id="e0fb2-115">创建并配置新的资源池和工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-115">Create and configure the new resource pools and workload groups.</span></span> <span data-ttu-id="e0fb2-116">将每个工作负荷组分配给相应的资源池。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-116">Assign each workload group to the appropriate resource pool.</span></span>  
  
    ```  
    --- Create a resource pool for production processing  
    --- and set limits.  
    USE master  
    GO  
    CREATE RESOURCE POOL pProductionProcessing  
    WITH  
    (  
         MAX_CPU_PERCENT = 100,  
         MIN_CPU_PERCENT = 50  
    )  
    GO  
    --- Create a workload group for production processing  
    --- and configure the relative importance.  
    CREATE WORKLOAD GROUP gProductionProcessing  
    WITH  
    (  
         IMPORTANCE = MEDIUM  
    )  
    --- Assign the workload group to the production processing  
    --- resource pool.  
    USING pProductionProcessing  
    GO  
    --- Create a resource pool for off-hours processing  
    --- and set limits.  
  
    CREATE RESOURCE POOL pOffHoursProcessing  
    WITH  
    (  
         MAX_CPU_PERCENT = 50,  
         MIN_CPU_PERCENT = 0  
    )  
    GO  
    --- Create a workload group for off-hours processing  
    --- and configure the relative importance.  
    CREATE WORKLOAD GROUP gOffHoursProcessing  
    WITH  
    (  
         IMPORTANCE = LOW  
    )  
    --- Assign the workload group to the off-hours processing  
    --- resource pool.  
    USING pOffHoursProcessing  
    GO  
    ```  
  
2.  <span data-ttu-id="e0fb2-117">更新内存中的配置。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-117">Update the in-memory configuration.</span></span>  
  
    ```  
    ALTER RESOURCE GOVERNOR RECONFIGURE  
    GO  
    ```  
  
3.  <span data-ttu-id="e0fb2-118">创建一个表，并定义生产处理时间范围的开始和结束时间。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-118">Create a table and define the start and end times for the production processing time range.</span></span>  
  
    ```  
    USE master  
    GO  
    CREATE TABLE tblClassificationTimeTable  
    (  
         strGroupName     sysname          not null,  
         tStartTime       time              not null,  
         tEndTime         time              not null  
    )  
    GO  
    --- Add time values that the classifier will use to  
    --- determine the workload group for a session.  
    INSERT into tblClassificationTimeTable VALUES('gProductionProcessing', '6:35 AM', '6:15 PM')  
    go  
    ```  
  
4.  <span data-ttu-id="e0fb2-119">创建分类器函数，它使用时间函数以及可根据查找表中的时间计算的值。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-119">Create the classifier function that uses time functions and values that can be evaluated against the times in the lookup table.</span></span> <span data-ttu-id="e0fb2-120">有关在分类器函数中使用查找表的信息，请参阅本主题中的“在分类器函数中使用查找表的最佳做法”。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-120">For information about using Lookup Tables in a classifier function, see "Best practices for using Lookup Tables in a classifier function" in this topic.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="e0fb2-121">引入了一组扩展的日期和时间数据类型和函数。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-121">introduced an expanded set of date and time data types and functions.</span></span> <span data-ttu-id="e0fb2-122">有关详细信息，请参阅[日期和时间数据类型和功能 (Transact-SQL)](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-122">For more information, see [Date and Time Data Types and Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql).</span></span>  
  
    ```  
    CREATE FUNCTION fnTimeClassifier()  
    RETURNS sysname  
    WITH SCHEMABINDING  
    AS  
    BEGIN  
         DECLARE @strGroup sysname  
         DECLARE @loginTime time  
         SET @loginTime = CONVERT(time,GETDATE())  
         SELECT TOP 1 @strGroup = strGroupName  
              FROM dbo.tblClassificationTimeTable  
              WHERE tStartTime <= @loginTime and tEndTime >= @loginTime  
         IF(@strGroup is not null)  
         BEGIN  
              RETURN @strGroup  
         END  
    --- Use the default workload group if there is no match  
    --- on the lookup.  
         RETURN N'gOffHoursProcessing'  
    END  
    GO  
    ```  
  
5.  <span data-ttu-id="e0fb2-123">注册分类器函数并更新内存中的配置。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-123">Register the classifier function and update the in-memory configuration.</span></span>  
  
    ```  
    ALTER RESOURCE GOVERNOR with (CLASSIFIER_FUNCTION = dbo.fnTimeClassifier)  
    ALTER RESOURCE GOVERNOR RECONFIGURE  
    GO  
    ```  
  
### <a name="to-verify-the-resource-pools-workload-groups-and-the-classifier-user-defined-function"></a><span data-ttu-id="e0fb2-124">验证资源池、工作负荷组以及分类器用户定义函数</span><span class="sxs-lookup"><span data-stu-id="e0fb2-124">To verify the resource pools, workload groups, and the classifier user-defined function</span></span>  
  
1.  <span data-ttu-id="e0fb2-125">使用以下查询获取资源池和工作负荷组配置。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-125">Obtain the resource pool and workload group configuration by using the following query.</span></span>  
  
    ```  
    USE master  
    SELECT * FROM sys.resource_governor_resource_pools  
    SELECT * FROM sys.resource_governor_workload_groups  
    GO  
    ```  
  
2.  <span data-ttu-id="e0fb2-126">使用以下查询验证分类器函数是否存在以及是否启用。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-126">Verify that the classifier function exists and is enabled by using the following queries.</span></span>  
  
    ```  
    --- Get the classifier function Id and state (enabled).  
    SELECT * FROM sys.resource_governor_configuration  
    GO  
    --- Get the classifer function name and the name of the schema  
    --- that it is bound to.  
    SELECT   
          object_schema_name(classifier_function_id) AS [schema_name],  
          object_name(classifier_function_id) AS [function_name]  
    FROM sys.dm_resource_governor_configuration  
  
    ```  
  
3.  <span data-ttu-id="e0fb2-127">使用以下查询获取资源池和工作负荷组的当前运行时数据。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-127">Obtain the current runtime data for the resource pools and workload groups by using the following query.</span></span>  
  
    ```  
    SELECT * FROM sys.dm_resource_governor_resource_pools  
    SELECT * FROM sys.dm_resource_governor_workload_groups  
    GO  
    ```  
  
4.  <span data-ttu-id="e0fb2-128">使用以下查询确定每个组中包含的会话。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-128">Find out what sessions are in each group by using the following query.</span></span>  
  
    ```  
    SELECT s.group_id, CAST(g.name as nvarchar(20)), s.session_id, s.login_time, CAST(s.host_name as nvarchar(20)), CAST(s.program_name AS nvarchar(20))  
              FROM sys.dm_exec_sessions s  
         INNER JOIN sys.dm_resource_governor_workload_groups g  
              ON g.group_id = s.group_id  
    ORDER BY g.name  
    GO  
    ```  
  
5.  <span data-ttu-id="e0fb2-129">使用以下查询确定每个组中包含的请求。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-129">Find out which requests are in each group by using the following query.</span></span>  
  
    ```  
    SELECT r.group_id, g.name, r.status, r.session_id, r.request_id, r.start_time, r.command, r.sql_handle, t.text   
               FROM sys.dm_exec_requests r  
         INNER JOIN sys.dm_resource_governor_workload_groups g  
                ON g.group_id = r.group_id  
         CROSS APPLY sys.dm_exec_sql_text(r.sql_handle) AS t  
    ORDER BY g.name  
    GO  
    ```  
  
6.  <span data-ttu-id="e0fb2-130">使用以下查询确定分类器中运行的请求。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-130">Find out what requests are running in the classifier by using the following query.</span></span>  
  
    ```  
    SELECT s.group_id, g.name, s.session_id, s.login_time, s.host_name, s.program_name   
               FROM sys.dm_exec_sessions s  
         INNER JOIN sys.dm_resource_governor_workload_groups g  
               ON g.group_id = s.group_id  
                     AND 'preconnect' = s.status  
    ORDER BY g.name  
    GO  
  
    SELECT r.group_id, g.name, r.status, r.session_id, r.request_id, r.start_time, r.command, r.sql_handle, t.text   
               FROM sys.dm_exec_requests r  
         INNER JOIN sys.dm_resource_governor_workload_groups g  
               ON g.group_id = r.group_id  
                     AND 'preconnect' = r.status  
         CROSS APPLY sys.dm_exec_sql_text(r.sql_handle) AS t  
    ORDER BY g.name  
    GO  
    ```  
  
### <a name="best-practices-for-using-lookup-tables-in-a-classifier-function"></a><span data-ttu-id="e0fb2-131">在分类器函数中使用查找表的最佳做法</span><span class="sxs-lookup"><span data-stu-id="e0fb2-131">Best practices for using Lookup Tables in a classifier function</span></span>  
  
1.  <span data-ttu-id="e0fb2-132">除非绝对必要，否则不要使用查找表。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-132">Do not use a lookup table unless it is absolutely necessary.</span></span> <span data-ttu-id="e0fb2-133">如果需要使用查找表，可以将其硬编码在函数本身中；但是，这样做时需要权衡考虑分类器函数的复杂程度和动态变更。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-133">If you need to use a lookup table, it can be hard coded into the function itself; however, this needs to be balanced with the complexity and dynamic changes of the classifier function.</span></span>  
  
2.  <span data-ttu-id="e0fb2-134">限制为查找表执行的 I/O。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-134">Limit the I/O performed for lookup tables.</span></span>  
  
    1.  <span data-ttu-id="e0fb2-135">使用 TOP 1 仅返回一行。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-135">Use the TOP 1 to return only one row.</span></span>  
  
    2.  <span data-ttu-id="e0fb2-136">尽量减少表中的行数。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-136">Minimize the number of rows in the table.</span></span>  
  
    3.  <span data-ttu-id="e0fb2-137">让表中所有行都位于一页中或少数几页中。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-137">Make all rows of the table exist on a single page, or a small number of pages.</span></span>  
  
    4.  <span data-ttu-id="e0fb2-138">确认使用索引查找操作找到的行使用了尽量多的查找列。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-138">Confirm that rows found using the Index Seek operations use as many seeking columns as possible.</span></span>  
  
    5.  <span data-ttu-id="e0fb2-139">如果考虑使用相互联接的多个表，则可以对单个表取消规范化。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-139">De-normalize to a single table if you are considering using multiple tables with joins.</span></span>  
  
3.  <span data-ttu-id="e0fb2-140">防止阻塞查找表。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-140">Prevent blocking on the lookup table.</span></span>  
  
    1.  <span data-ttu-id="e0fb2-141">使用 `NOLOCK` 提示防止阻塞，或在函数中使用最大值设置为 1000 毫秒的 `SET LOCK_TIMEOUT` 。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-141">Use the `NOLOCK` hint to prevent blocking or use `SET LOCK_TIMEOUT` in the function with a maximum value of 1000 milliseconds.</span></span>  
  
    2.  <span data-ttu-id="e0fb2-142">表必须存在于 master 数据库中。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-142">Table(s) must exist in the master database.</span></span> <span data-ttu-id="e0fb2-143">（master 数据库是在客户端计算机尝试连接时可确保恢复的唯一一个数据库）。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-143">(The master database is the only database that is guaranteed to be recovered when the client computers attempt to connect).</span></span>  
  
    3.  <span data-ttu-id="e0fb2-144">始终使用架构对表名进行完全限定。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-144">Always fully-qualify the table name with the schema.</span></span> <span data-ttu-id="e0fb2-145">数据库名称不是必需的，因为该名称只能是 master 数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-145">The database name is not necessary since it has to be the master database.</span></span>  
  
    4.  <span data-ttu-id="e0fb2-146">表上没有触发器。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-146">No triggers on the table.</span></span>  
  
    5.  <span data-ttu-id="e0fb2-147">如果要更新表内容，确保使用快照隔离级别事务来防止编写器阻塞读取器。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-147">If you are updating the table contents, make sure to use a snapshot isolation level transaction to prevent Writer blocking Readers.</span></span> <span data-ttu-id="e0fb2-148">请注意，使用 `NOLOCK` 提示应该也能缓解此问题。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-148">Note that using the `NOLOCK` hint should also mitigate this.</span></span>  
  
    6.  <span data-ttu-id="e0fb2-149">如果可能，请在更改表内容时禁用分类器函数。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-149">If possible, disable the classifier function when changing the table contents.</span></span>  
  
        > [!WARNING]  
        >  <span data-ttu-id="e0fb2-150">我们强烈建议遵循如上最佳做法。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-150">We highly recommend following these best practices.</span></span> <span data-ttu-id="e0fb2-151">如有任何问题妨碍您遵循这些最佳做法，我们建议您与 Microsoft 支持部门联系，以求主动防止未来出现任何问题。</span><span class="sxs-lookup"><span data-stu-id="e0fb2-151">If there are issues that prevent you from following the best practices, we recommend that you contact Microsoft Support so that you can proactively prevent any future problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0fb2-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e0fb2-152">See Also</span></span>  
 <span data-ttu-id="e0fb2-153">[资源调控器](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="e0fb2-153">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="e0fb2-154">[启用资源调控器](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="e0fb2-154">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="e0fb2-155">[资源调控器资源池](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="e0fb2-155">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="e0fb2-156">[资源调控器工作负荷组](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="e0fb2-156">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="e0fb2-157">[使用模板配置资源调控器](configure-resource-governor-using-a-template.md) </span><span class="sxs-lookup"><span data-stu-id="e0fb2-157">[Configure Resource Governor Using a Template](configure-resource-governor-using-a-template.md) </span></span>  
 <span data-ttu-id="e0fb2-158">[查看资源调控器属性](view-resource-governor-properties.md) </span><span class="sxs-lookup"><span data-stu-id="e0fb2-158">[View Resource Governor Properties](view-resource-governor-properties.md) </span></span>  
 <span data-ttu-id="e0fb2-159">[ALTER RESOURCE GOVERNOR (Transact-SQL)](/sql/t-sql/statements/alter-resource-governor-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e0fb2-159">[ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql) </span></span>  
 <span data-ttu-id="e0fb2-160">[CREATE RESOURCE POOL (Transact-SQL)](/sql/t-sql/statements/create-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e0fb2-160">[CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span></span>  
 <span data-ttu-id="e0fb2-161">[CREATE WORKLOAD GROUP (Transact-SQL)](/sql/t-sql/statements/create-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e0fb2-161">[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="e0fb2-162">[CREATE FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e0fb2-162">[CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span></span>  
 [<span data-ttu-id="e0fb2-163">ALTER RESOURCE GOVERNOR (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e0fb2-163">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
