---
title: 使用 SQL Server Profiler SQL Server Management Studio) 中创建 SQL 跟踪收集组 (Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- SQL Trace collector set
ms.assetid: b6941dc0-50f5-475d-82eb-ce7c68117489
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e9c9514fef8069cef615d1480aad1e0acd1582cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589711"
---
# <a name="use-sql-server-profiler-to-create-a-sql-trace-collection-set-sql-server-management-studio"></a><span data-ttu-id="61586-102">使用 SQL Server Profiler 创建 SQL 跟踪收集组 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="61586-102">Use SQL Server Profiler to Create a SQL Trace Collection Set (SQL Server Management Studio)</span></span>
  <span data-ttu-id="61586-103">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中，可以利用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 的服务器端跟踪功能导出跟踪定义，可使用跟踪定义创建一个使用一般 SQL 跟踪收集器类型的收集组。</span><span class="sxs-lookup"><span data-stu-id="61586-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] you can exploit the server-side trace capabilities of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to export a trace definition that you can use to create a collection set that uses the Generic SQL Trace collector type.</span></span> <span data-ttu-id="61586-104">此过程分为两个部分：</span><span class="sxs-lookup"><span data-stu-id="61586-104">There are two parts to this process:</span></span>  
  
1.  <span data-ttu-id="61586-105">创建并导出 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 跟踪。</span><span class="sxs-lookup"><span data-stu-id="61586-105">Create and export a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] trace.</span></span>  
  
2.  <span data-ttu-id="61586-106">根据导出的跟踪编写新的收集组脚本。</span><span class="sxs-lookup"><span data-stu-id="61586-106">Script a new collection set based on an exported trace.</span></span>  
  
 <span data-ttu-id="61586-107">以下过程的应用场景包括收集任何存储过程的相关数据，此过程需要 80 毫秒或更长的时间才能完成。</span><span class="sxs-lookup"><span data-stu-id="61586-107">The scenario for the following procedures involves collecting data about any stored procedure that requires 80 milliseconds or longer to complete.</span></span> <span data-ttu-id="61586-108">若要完成这些过程，您应该能够：</span><span class="sxs-lookup"><span data-stu-id="61586-108">In order to complete these procedures you should be able to:</span></span>  
  
-   <span data-ttu-id="61586-109">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 创建并配置跟踪。</span><span class="sxs-lookup"><span data-stu-id="61586-109">Use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to create and configure a trace.</span></span>  
  
-   <span data-ttu-id="61586-110">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 打开、编辑和执行查询。</span><span class="sxs-lookup"><span data-stu-id="61586-110">Use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to open, edit, and execute a query.</span></span>  
  
### <a name="create-and-export-a-sql-server-profiler-trace"></a><span data-ttu-id="61586-111">创建和导出 SQL Server Profiler 跟踪</span><span class="sxs-lookup"><span data-stu-id="61586-111">Create and export a SQL Server Profiler trace</span></span>  
  
1.  <span data-ttu-id="61586-112">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，打开 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="61586-112">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="61586-113">（在“工具”  菜单上，单击“SQL Server Profiler”  。）</span><span class="sxs-lookup"><span data-stu-id="61586-113">(On the **Tools** menu, click **SQL Server Profiler**.)</span></span>  
  
2.  <span data-ttu-id="61586-114">在 **“连接到服务器”** 对话框中，单击 **“取消”** 。</span><span class="sxs-lookup"><span data-stu-id="61586-114">In the **Connect to Server** dialog box, click **Cancel**.</span></span>  
  
3.  <span data-ttu-id="61586-115">对于此应用场景，请确保将持续时间值配置为以毫秒为单位显示（默认设置）。</span><span class="sxs-lookup"><span data-stu-id="61586-115">For this scenario, ensure that duration values are configured to display in milliseconds (the default).</span></span> <span data-ttu-id="61586-116">为此，请按照下列步骤进行操作：</span><span class="sxs-lookup"><span data-stu-id="61586-116">To do this, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="61586-117">在“工具”  菜单上，单击“选项”  。</span><span class="sxs-lookup"><span data-stu-id="61586-117">On the **Tools** menu, click **Options**.</span></span>  
  
    2.  <span data-ttu-id="61586-118">在 **“显示选项”** 区域中，确保清除“在‘持续时间’列中以微秒为单位显示值”复选框。</span><span class="sxs-lookup"><span data-stu-id="61586-118">In the **Display Options** area, ensure that the Show values in Duration column in microseconds check box is cleared.</span></span>  
  
    3.  <span data-ttu-id="61586-119">单击 **“确定”** 关闭 **“常规选项”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="61586-119">Click **OK** to close the **General Options** dialog box.</span></span>  
  
4.  <span data-ttu-id="61586-120">在 **“文件”** 菜单上，单击 **“新建跟踪”** 。</span><span class="sxs-lookup"><span data-stu-id="61586-120">On the **File** menu, click **New Trace**.</span></span>  
  
5.  <span data-ttu-id="61586-121">在 **“连接到服务器”** 对话框中，选择要连接到的服务器，然后单击 **“连接”** 。</span><span class="sxs-lookup"><span data-stu-id="61586-121">In the **Connect to Server** dialog box, select the server that you want to connect to, and then click **Connect**.</span></span>  
  
     <span data-ttu-id="61586-122">此时，将显示 **“跟踪属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="61586-122">The **Trace Properties** dialog box appears.</span></span>  
  
6.  <span data-ttu-id="61586-123">在 **“常规”** 选项卡上，请执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="61586-123">On the **General** tab, do the following:</span></span>  
  
    1.  <span data-ttu-id="61586-124">在 **“跟踪名称”** 框中，键入该跟踪要使用的名称。</span><span class="sxs-lookup"><span data-stu-id="61586-124">In the **Trace name** box, type the name that you want to use for the trace.</span></span> <span data-ttu-id="61586-125">在本示例中，跟踪名称为 `SPgt80`。</span><span class="sxs-lookup"><span data-stu-id="61586-125">For this example, the trace name is `SPgt80`.</span></span>  
  
    2.  <span data-ttu-id="61586-126">在 **“使用模板”** 列表中，选择要用于该跟踪的模板。</span><span class="sxs-lookup"><span data-stu-id="61586-126">In the **Use the template list**, select the template to use for the trace.</span></span> <span data-ttu-id="61586-127">在本示例中，请单击“TSQL_SPs”  。</span><span class="sxs-lookup"><span data-stu-id="61586-127">For this example, click **TSQL_SPs**.</span></span>  
  
7.  <span data-ttu-id="61586-128">在 **“事件选择”** 选项卡上，请执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="61586-128">On the **Events Selection** tab, do the following:</span></span>  
  
    1.  <span data-ttu-id="61586-129">标识要用于该跟踪的事件。</span><span class="sxs-lookup"><span data-stu-id="61586-129">Identify the events to use for the trace.</span></span> <span data-ttu-id="61586-130">在本示例中，清除 **“事件”** 列中除 **ExistingConnection** 和 **SP:Completed**以外的所有复选框。</span><span class="sxs-lookup"><span data-stu-id="61586-130">For this example, clear all check boxes in the **Events** column, except for **ExistingConnection** and **SP:Completed**.</span></span>  
  
    2.  <span data-ttu-id="61586-131">在右下角，选中“显示所有列”  复选框。</span><span class="sxs-lookup"><span data-stu-id="61586-131">In the lower-right corner, select the **Show all columns** check box.</span></span>  
  
    3.  <span data-ttu-id="61586-132">单击 **SP:Completed** 行。</span><span class="sxs-lookup"><span data-stu-id="61586-132">Click the **SP:Completed** row.</span></span>  
  
    4.  <span data-ttu-id="61586-133">在这一行中滚动到 **“持续时间”** 列，然后选中 **“持续时间”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="61586-133">Scroll across the row to the **Duration** column, and then select the **Duration** check box.</span></span>  
  
8.  <span data-ttu-id="61586-134">在右下角，单击“列筛选器”以打开“编辑筛选器”对话框   。</span><span class="sxs-lookup"><span data-stu-id="61586-134">In the lower-right corner, click **Column Filters** to open the **Edit Filter** dialog box.</span></span> <span data-ttu-id="61586-135">在 **“编辑筛选器”** 对话框中，请执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="61586-135">In the **Edit Filter** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="61586-136">在筛选器列表中，单击 **“持续时间”** 。</span><span class="sxs-lookup"><span data-stu-id="61586-136">In the filter list, click **Duration**.</span></span>  
  
    2.  <span data-ttu-id="61586-137">在布尔运算符窗口中，展开 "**大于或等于**" 节点，键入 `80` 作为值，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="61586-137">In the Boolean operator window, expand the **Greater than or equal** node, type `80` as the value, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="61586-138">单击 **“运行”** 以启动跟踪。</span><span class="sxs-lookup"><span data-stu-id="61586-138">Click **Run** to start the trace.</span></span>  
  
10. <span data-ttu-id="61586-139">在工具栏上，单击 **“停止所选跟踪”** 或 **“暂停所选跟踪”** 。</span><span class="sxs-lookup"><span data-stu-id="61586-139">On the toolbar, click **Stop Selected Trace** or **Pause Selected Trace**.</span></span>  
  
11. <span data-ttu-id="61586-140">在 **“文件”** 菜单上，依次指向 **“导出”** 和 **“编写跟踪定义的脚本”** ，然后单击 **“用于 SQL 跟踪收集组”** 。</span><span class="sxs-lookup"><span data-stu-id="61586-140">On the **File** menu, point to **Export**, point to **Script Trace Definition**, and then click **For SQL Trace Collection Set**.</span></span>  
  
12. <span data-ttu-id="61586-141">在 **“另存为”** 对话框中，在 **“文件名”** 框中键入要为该跟踪定义使用的名称，然后将跟踪定义保存到所需位置。</span><span class="sxs-lookup"><span data-stu-id="61586-141">In the **Save As** dialog box, type the name that you want to use for the trace definition in the **File name** box, and then save it in the location that you want.</span></span> <span data-ttu-id="61586-142">在本示例中，文件名与跟踪名称 (SPgt80) 相同。</span><span class="sxs-lookup"><span data-stu-id="61586-142">For this example, the file name is the same as the trace name (SPgt80).</span></span>  
  
13. <span data-ttu-id="61586-143">收到文件已经成功保存的消息后，请单击 **“确定”** ，然后关闭 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="61586-143">Click **OK** when you receive a message that the file was successfully saved, and then close [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="script-a-new-collection-set-from-a-sql-server-profiler-trace"></a><span data-ttu-id="61586-144">通过 SQL Server Profiler 跟踪编写新收集组的脚本</span><span class="sxs-lookup"><span data-stu-id="61586-144">Script a new collection set from a SQL Server Profiler trace</span></span>  
  
1.  <span data-ttu-id="61586-145">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的 **“文件”** 菜单上，指向 **“打开”** ，然后单击 **“文件”** 。</span><span class="sxs-lookup"><span data-stu-id="61586-145">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **File** menu, point to **Open,** and then click **File**.</span></span>  
  
2.  <span data-ttu-id="61586-146">在“打开文件”  对话框中，找到并打开你在前面的过程中创建的文件 (SPgt80)。</span><span class="sxs-lookup"><span data-stu-id="61586-146">In the **Open File** dialog box, locate and then open the file that you created in the previous procedure (SPgt80).</span></span>  
  
     <span data-ttu-id="61586-147">将在“查询”窗口中打开保存的跟踪信息，并将其合并到可运行以创建新收集组的脚本中。</span><span class="sxs-lookup"><span data-stu-id="61586-147">The trace information that you saved is opened in a Query window and merged into a script that you can run to create the new collection set.</span></span>  
  
3.  <span data-ttu-id="61586-148">滚动查看脚本并进行以下替换（在脚本注释文本中注明）：</span><span class="sxs-lookup"><span data-stu-id="61586-148">Scroll through the script and make the following replacements, which are noted in the script comment text:</span></span>  
  
    -   <span data-ttu-id="61586-149">将 **SQLTrace Collection Set Name Here** 替换为要为收集组使用的名称。</span><span class="sxs-lookup"><span data-stu-id="61586-149">Replace **SQLTrace Collection Set Name Here** with the name that you want to use for the collection set.</span></span> <span data-ttu-id="61586-150">在本示例中，将收集组命名为 `SPROC_CollectionSet`。</span><span class="sxs-lookup"><span data-stu-id="61586-150">For this example, name the collection set `SPROC_CollectionSet`.</span></span>  
  
    -   <span data-ttu-id="61586-151">将 **SQLTrace Collection Item Name Here** 替换为要为收集项使用的名称。</span><span class="sxs-lookup"><span data-stu-id="61586-151">Replace **SQLTrace Collection Item Name Here** with the name that you want to use for the collection item.</span></span> <span data-ttu-id="61586-152">对于本示例，请将收集项命名为 `SPROC_Collection_Item` 。</span><span class="sxs-lookup"><span data-stu-id="61586-152">For this example, name the collection item `SPROC_Collection_Item`.</span></span>  
  
4.  <span data-ttu-id="61586-153">单击 **“执行”** 运行查询并创建收集组。</span><span class="sxs-lookup"><span data-stu-id="61586-153">Click **Execute** to run the query and to create the collection set.</span></span>  
  
5.  <span data-ttu-id="61586-154">在对象资源管理器中，验证该收集组是否已经创建。</span><span class="sxs-lookup"><span data-stu-id="61586-154">In Object Explorer, verify that the collection set was created.</span></span> <span data-ttu-id="61586-155">为此，请按照下列步骤进行操作：</span><span class="sxs-lookup"><span data-stu-id="61586-155">To do this, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="61586-156">右键单击“管理”，然后单击“刷新”   。</span><span class="sxs-lookup"><span data-stu-id="61586-156">Right-click **Management**, and then click **Refresh**.</span></span>  
  
    2.  <span data-ttu-id="61586-157">展开 **“管理”** ，然后展开 **“数据收集”** 。</span><span class="sxs-lookup"><span data-stu-id="61586-157">Expand **Management**, and then expand **Data Collection**.</span></span>  
  
     <span data-ttu-id="61586-158">`SPROC_CollectionSet`收集组与 "**系统数据收集组**" 节点显示在同一级别。</span><span class="sxs-lookup"><span data-stu-id="61586-158">The `SPROC_CollectionSet` collection set appears at the same level as the **System Data Collection Sets** node.</span></span> <span data-ttu-id="61586-159">默认情况下，将禁用该收集组。</span><span class="sxs-lookup"><span data-stu-id="61586-159">By default, the collection set is disabled.</span></span>  
  
6.  <span data-ttu-id="61586-160">使用对象资源管理器编辑 SPROC_CollectionSet 的属性，如收集模式和上载计划。</span><span class="sxs-lookup"><span data-stu-id="61586-160">Use Object Explorer to edit the properties of SPROC_CollectionSet, such as the collection mode and upload schedule.</span></span> <span data-ttu-id="61586-161">按照针对与数据收集器一起提供的系统数据收集组的过程进行操作。</span><span class="sxs-lookup"><span data-stu-id="61586-161">Follow the same procedures that you would for the System Data collection sets that are provided with the data collector.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61586-162">示例</span><span class="sxs-lookup"><span data-stu-id="61586-162">Example</span></span>  
 <span data-ttu-id="61586-163">下面的代码示例是以上过程中所述的步骤生成的最终脚本。</span><span class="sxs-lookup"><span data-stu-id="61586-163">The following code sample is the final script resulting from the steps documented in the preceding procedures.</span></span>  
  
```  
/*************************************************************/  
-- SQL Trace collection set generated from SQL Server Profiler  
-- Date: 11/19/2007  12:55:31 AM  
/*************************************************************/  
  
USE msdb  
GO  
  
BEGIN TRANSACTION  
BEGIN TRY  
  
-- Define collection set  
-- ***  
-- *** Replace 'SqlTrace Collection Set Name Here' in the   
-- *** following script with the name you want  
-- *** to use for the collection set.  
-- ***  
DECLARE @collection_set_id int;  
EXEC [dbo].[sp_syscollector_create_collection_set]  
    @name = N'SPROC_CollectionSet',  
    @schedule_name = N'CollectorSchedule_Every_15min',  
    @collection_mode = 0, -- cached mode needed for Trace collections  
    @logging_level = 0, -- minimum logging  
    @days_until_expiration = 5,  
    @description = N'Collection set generated by SQL Server Profiler',  
    @collection_set_id = @collection_set_id output;  
SELECT @collection_set_id;  
  
-- Define input and output variables for the collection item.  
DECLARE @trace_definition xml;  
DECLARE @collection_item_id int;  
  
-- Define the trace parameters as an XML variable  
SELECT @trace_definition = convert(xml,   
N'<ns:SqlTraceCollector xmlns:ns"DataCollectorType" use_default="0">  
<Events>  
  <EventType name="Sessions">  
    <Event id="17" name="ExistingConnection" columnslist="1,2,14,26,3,35,12" />  
  </EventType>  
  <EventType name="Stored Procedures">  
    <Event id="43" name="SP:Completed" columnslist="1,2,26,34,3,35,12,13,14,22" />  
  </EventType>  
</Events>  
<Filters>  
  <Filter columnid="13" columnname="Duration" logical_operator="AND" comparison_operator="GE" value="80000L" />  
</Filters>  
</ns:SqlTraceCollector>  
');  
  
-- Retrieve the collector type GUID for the trace collector type.  
DECLARE @collector_type_GUID uniqueidentifier;  
SELECT @collector_type_GUID = collector_type_uid FROM [dbo].[syscollector_collector_types] WHERE name = N'Generic SQL Trace Collector Type';  
  
-- Create the trace collection item.  
-- ***  
-- *** Replace 'SqlTrace Collection Item Name Here' in   
-- *** the following script with the name you want to  
-- *** use for the collection item.  
-- ***  
EXEC [dbo].[sp_syscollector_create_collection_item]  
   @collection_set_id = @collection_set_id,  
   @collector_type_uid = @collector_type_GUID,  
   @name = N'SPROC_Collection_Item',  
   @frequency = 900, -- specified the frequency for checking to see if trace is still running  
   @parameters = @trace_definition,  
   @collection_item_id = @collection_item_id output;  
SELECT @collection_item_id;  
  
COMMIT TRANSACTION;  
END TRY  
  
BEGIN CATCH  
ROLLBACK TRANSACTION;  
DECLARE @ErrorMessage nvarchar(4000);  
DECLARE @ErrorSeverity int;  
DECLARE @ErrorState int;  
DECLARE @ErrorNumber int;  
DECLARE @ErrorLine int;  
DECLARE @ErrorProcedure nvarchar(200);  
SELECT @ErrorLine = ERROR_LINE(),  
       @ErrorSeverity = ERROR_SEVERITY(),  
       @ErrorState = ERROR_STATE(),  
       @ErrorNumber = ERROR_NUMBER(),  
       @ErrorMessage = ERROR_MESSAGE(),  
       @ErrorProcedure = ISNULL(ERROR_PROCEDURE(), '-');  
RAISERROR (14684, @ErrorSeverity, 1 , @ErrorNumber, @ErrorSeverity, @ErrorState, @ErrorProcedure, @ErrorLine, @ErrorMessage);  
END CATCH;  
GO  
```  
  
  
