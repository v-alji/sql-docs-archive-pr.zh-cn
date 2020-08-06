---
title: 创建函数以检索变更数据 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],creating function
ms.assetid: 55dd0946-bd67-4490-9971-12dfb5b9de94
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc1d5af0a64225aca4ff54570ad6504d25d62812
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693023"
---
# <a name="create-the-function-to-retrieve-the-change-data"></a><span data-ttu-id="b18c6-102">创建函数以检索变更数据</span><span class="sxs-lookup"><span data-stu-id="b18c6-102">Create the Function to Retrieve the Change Data</span></span>
  <span data-ttu-id="b18c6-103">在完成用于执行变更数据增量加载的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的控制流之后，接下来的任务是创建用于检索变更数据的表值函数。</span><span class="sxs-lookup"><span data-stu-id="b18c6-103">After completing the control flow for an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the next task is to create a table-valued function that retrieves the change data.</span></span> <span data-ttu-id="b18c6-104">只需在第一次增量加载之前创建一次此函数。</span><span class="sxs-lookup"><span data-stu-id="b18c6-104">You only have to create this function one time before the first incremental load.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b18c6-105">在创建用于执行变更数据增量加载的包的过程中，第二步是创建用于检索数据的函数。</span><span class="sxs-lookup"><span data-stu-id="b18c6-105">The creation of a function to retrieve the change data is the second step in the process of creating a package that performs an incremental load of change data.</span></span> <span data-ttu-id="b18c6-106">有关创建此包的总体过程的说明，请参阅[变更数据捕获 (SSIS)](change-data-capture-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="b18c6-106">For a description of the overall process for creating this package, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="design-considerations-for-change-data-capture-functions"></a><span data-ttu-id="b18c6-107">变更数据捕获函数的设计注意事项</span><span class="sxs-lookup"><span data-stu-id="b18c6-107">Design Considerations for Change Data Capture Functions</span></span>  
 <span data-ttu-id="b18c6-108">为了检索变更数据，包数据流中的源组件将调用下面的变更数据捕获查询函数之中的一个：</span><span class="sxs-lookup"><span data-stu-id="b18c6-108">To retrieve change data, a source component in the data flow of the package calls one of the following change data capture query functions:</span></span>  
  
-   <span data-ttu-id="b18c6-109">**cdc.fn_cdc_get_net_changes_<capture_instance>** 对于此查询，为各更新返回的单个行包含每个变更行的最终状态。</span><span class="sxs-lookup"><span data-stu-id="b18c6-109">**cdc.fn_cdc_get_net_changes_<capture_instance>** For this query, the single row returned for each update contains the final state of each changed row.</span></span> <span data-ttu-id="b18c6-110">在大多数情况下，您只需要净更改查询返回的数据。</span><span class="sxs-lookup"><span data-stu-id="b18c6-110">In most cases, you only need the data returned by a query for net changes.</span></span> <span data-ttu-id="b18c6-111">有关详细信息，请参阅[cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; (Transact-SQL)](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b18c6-111">For more information, see [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).</span></span>  
  
-   <span data-ttu-id="b18c6-112">**cdc.fn_cdc_get_all_changes_<capture_instance>** 此查询返回捕获间隔期间各行中发生的所有更改。</span><span class="sxs-lookup"><span data-stu-id="b18c6-112">**cdc.fn_cdc_get_all_changes_<capture_instance>** This query returns all the changes that have occurred in each row during the capture interval.</span></span> <span data-ttu-id="b18c6-113">有关详细信息，请参阅 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  (Transact-SQL)](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b18c6-113">For more information, see [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql).</span></span>  
  
 <span data-ttu-id="b18c6-114">然后，源组件获取函数返回的结果并将这些结果传递到下游转换和目标，以将变更数据应用到最终目标。</span><span class="sxs-lookup"><span data-stu-id="b18c6-114">The source component then takes the results returned by the function and passes them to downstream transformations and destinations, which apply the change data to the final destination.</span></span>  
  
 <span data-ttu-id="b18c6-115">但是， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 源组件无法直接调用这些变更数据捕获函数。</span><span class="sxs-lookup"><span data-stu-id="b18c6-115">However, an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source component cannot call these change data capture functions directly.</span></span> <span data-ttu-id="b18c6-116">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 源组件需要有关查询所返回列的元数据。</span><span class="sxs-lookup"><span data-stu-id="b18c6-116">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source component requires metadata about the columns that the query returns.</span></span> <span data-ttu-id="b18c6-117">变更数据捕获函数不定义其输出表的列。</span><span class="sxs-lookup"><span data-stu-id="b18c6-117">The change data capture functions do not define the columns of their output table.</span></span> <span data-ttu-id="b18c6-118">因此，这些函数不会为 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 源组件返回足够的元数据。</span><span class="sxs-lookup"><span data-stu-id="b18c6-118">Thus, these functions do not return sufficient metadata for an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source component.</span></span>  
  
 <span data-ttu-id="b18c6-119">相反，因为表值包装函数在其 RETURNS 子句中显式定义了其输出表的列，所以应使用该函数。</span><span class="sxs-lookup"><span data-stu-id="b18c6-119">Instead, you use a table-valued wrapper function because this kind of function explicitly defines the columns of its output table in its RETURNS clause.</span></span> <span data-ttu-id="b18c6-120">列的显式定义提供了 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 源组件所需的元数据。</span><span class="sxs-lookup"><span data-stu-id="b18c6-120">This explicit definition of columns provides the metadata that an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source component needs.</span></span> <span data-ttu-id="b18c6-121">必须为每个要检索变更数据的表创建此函数。</span><span class="sxs-lookup"><span data-stu-id="b18c6-121">You have to create this function for each table for which you want to retrieve change data.</span></span>  
  
 <span data-ttu-id="b18c6-122">有两种方法可创建调用变更数据捕获查询函数的表值包装函数：</span><span class="sxs-lookup"><span data-stu-id="b18c6-122">You have two options for creating the table-valued wrapper function that calls the change data capture query function:</span></span>  
  
-   <span data-ttu-id="b18c6-123">可以调用 **sys.sp_cdc_generate_wrapper_function** 系统存储过程来创建表值函数。</span><span class="sxs-lookup"><span data-stu-id="b18c6-123">You can call the **sys.sp_cdc_generate_wrapper_function** system stored procedure to create the table-valued functions for you.</span></span>  
  
-   <span data-ttu-id="b18c6-124">可以使用本主题中的准则和示例编写自己的表值函数。</span><span class="sxs-lookup"><span data-stu-id="b18c6-124">You can write your own table-valued function by using the guidelines and the example in this topic.</span></span>  
  
## <a name="calling-a-stored-procedure-to-create-the-table-valued-function"></a><span data-ttu-id="b18c6-125">调用存储过程来创建表值函数</span><span class="sxs-lookup"><span data-stu-id="b18c6-125">Calling a Stored Procedure to Create the Table-valued Function</span></span>  
 <span data-ttu-id="b18c6-126">创建所需表值函数最快速且简便的方法是调用 **sys.sp_cdc_generate_wrapper_function** 系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="b18c6-126">The quickest and easiest way to create the table-valued functions that you need is to call the **sys.sp_cdc_generate_wrapper_function** system stored procedure.</span></span> <span data-ttu-id="b18c6-127">此存储过程生成用于创建包装函数的脚本，这些脚本是专为满足 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 源组件的需要而设计的。</span><span class="sxs-lookup"><span data-stu-id="b18c6-127">This stored procedure generates scripts to create wrapper functions that are designed specifically to meet the needs of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source component.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b18c6-128">**sys.sp_cdc_generate_wrapper_function** 系统存储过程不直接创建包装函数。</span><span class="sxs-lookup"><span data-stu-id="b18c6-128">The **sys.sp_cdc_generate_wrapper_function** system stored procedure does not directly create the wrapper functions.</span></span> <span data-ttu-id="b18c6-129">存储过程为包装函数生成 CREATE 脚本。</span><span class="sxs-lookup"><span data-stu-id="b18c6-129">Instead, the stored procedure generates the CREATE scripts for the wrapper functions.</span></span> <span data-ttu-id="b18c6-130">开发人员必须运行存储过程生成的 CREATE 脚本，然后增量加载包才能调用包装函数。</span><span class="sxs-lookup"><span data-stu-id="b18c6-130">The developer must run the CREATE scripts that the stored procedure generates before an incremental load package can call the wrapper functions.</span></span>  
  
 <span data-ttu-id="b18c6-131">若要了解如何使用此系统存储过程，您应该了解该过程的执行内容、该过程生成的脚本以及这些脚本创建的包装函数。</span><span class="sxs-lookup"><span data-stu-id="b18c6-131">To understand how to use this system stored procedure, you should understand what the procedure does, what scripts the procedure generates, and what wrapper functions the scripts create.</span></span>  
  
### <a name="understanding-and-using-the-stored-procedure"></a><span data-ttu-id="b18c6-132">了解和使用存储过程</span><span class="sxs-lookup"><span data-stu-id="b18c6-132">Understanding and Using the Stored Procedure</span></span>  
 <span data-ttu-id="b18c6-133">**sys.sp_cdc_generate_wrapper_function** 系统存储过程生成脚本，这些脚本用于创建供 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包使用的包装函数。</span><span class="sxs-lookup"><span data-stu-id="b18c6-133">The **sys.sp_cdc_generate_wrapper_function** system stored procedure generates scripts to create wrapper functions for use by [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span>  
  
 <span data-ttu-id="b18c6-134">下面是存储过程定义的前几行：</span><span class="sxs-lookup"><span data-stu-id="b18c6-134">Here are the first few lines of the definition of the stored procedure:</span></span>  
  
 `CREATE PROCEDURE sys.sp_cdc_generate_wrapper_function`  
  
 `(`  
  
 `@capture_instance sysname = null`  
  
 `@closed_high_end_point bit = 1,`  
  
 `@column_list = null,`  
  
 `@update_flag_list = null`  
  
 `)`  
  
 <span data-ttu-id="b18c6-135">该存储过程的所有参数都是可选的。</span><span class="sxs-lookup"><span data-stu-id="b18c6-135">All the parameters for the stored procedure are optional.</span></span> <span data-ttu-id="b18c6-136">如果您在调用该存储过程时不提供任何参数的值，存储过程将为您具有访问权限的所有捕获实例创建包装函数。</span><span class="sxs-lookup"><span data-stu-id="b18c6-136">If you call the stored procedure without supplying values for any of the parameters, the stored procedure creates wrapper functions for all the capture instances to which you have access.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b18c6-137">有关此存储过程的语法及其参数的详细信息，请参阅 [sys.sp_cdc_generate_wrapper_function (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-generate-wrapper-function-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b18c6-137">For more information about the syntax of this stored procedure and its parameters, see [sys.sp_cdc_generate_wrapper_function &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-generate-wrapper-function-transact-sql).</span></span>  
  
 <span data-ttu-id="b18c6-138">该存储过程会始终生成从每个捕获实例返回所有变更的包装函数。</span><span class="sxs-lookup"><span data-stu-id="b18c6-138">The stored procedure always generates a wrapper function to return all changes from each capture instance.</span></span> <span data-ttu-id="b18c6-139">如果在 *@supports_net_changes* 创建捕获实例时设置了参数，则该存储过程还会生成一个包装函数，以从每个适用的捕获实例返回净更改。</span><span class="sxs-lookup"><span data-stu-id="b18c6-139">If the *@supports_net_changes* parameter was set when the capture instance was created, the stored procedure also generates a wrapper function to return net changes from each applicable capture instance.</span></span>  
  
 <span data-ttu-id="b18c6-140">该存储过程返回带有两列的结果集：</span><span class="sxs-lookup"><span data-stu-id="b18c6-140">The stored procedure returns a result set with two columns:</span></span>  
  
-   <span data-ttu-id="b18c6-141">该存储过程生成的包装函数的名称。</span><span class="sxs-lookup"><span data-stu-id="b18c6-141">The name of the wrapper function that the stored procedure has generated.</span></span> <span data-ttu-id="b18c6-142">此存储过程从捕获实例的名称派生函数名称。</span><span class="sxs-lookup"><span data-stu-id="b18c6-142">This stored procedure derives the function name from the name of the capture instance name.</span></span> <span data-ttu-id="b18c6-143">（函数名称是“fn_all_changes_”后跟捕获实例名。</span><span class="sxs-lookup"><span data-stu-id="b18c6-143">(The function name is 'fn_all_changes_' followed by the capture instance name.</span></span> <span data-ttu-id="b18c6-144">如果创建的是净变更函数，则其前缀为“fn_net_changes_”。）</span><span class="sxs-lookup"><span data-stu-id="b18c6-144">The prefix used for the net changes function, if it is created, is 'fn_net_changes_'.)</span></span>  
  
-   <span data-ttu-id="b18c6-145">包装函数的 CREATE 语句。</span><span class="sxs-lookup"><span data-stu-id="b18c6-145">The CREATE statement for the wrapper function.</span></span>  
  
### <a name="understanding-and-using-the-scripts-created-by-the-stored-procedure"></a><span data-ttu-id="b18c6-146">了解和使用存储过程创建的脚本</span><span class="sxs-lookup"><span data-stu-id="b18c6-146">Understanding and Using the Scripts Created by the Stored Procedure</span></span>  
 <span data-ttu-id="b18c6-147">通常，开发人员使用 INSERT...EXEC 语句调用 **sys.sp_cdc_generate_wrapper_function** 存储过程，并将该存储过程创建的脚本保存到临时表中。</span><span class="sxs-lookup"><span data-stu-id="b18c6-147">Typically, a developer would use an INSERT...EXEC statement to call the **sys.sp_cdc_generate_wrapper_function** stored procedure and save the scripts that the stored procedure creates to a temporary table.</span></span> <span data-ttu-id="b18c6-148">然后，可以单独选择每个脚本，并运行该脚本以创建相应的包装函数。</span><span class="sxs-lookup"><span data-stu-id="b18c6-148">Each script could then be individually selected and run to create the corresponding wrapper function.</span></span> <span data-ttu-id="b18c6-149">但是，开发人员还可以使用一组 SQL 命令运行所有的 CREATE 脚本，如以下示例代码中所示：</span><span class="sxs-lookup"><span data-stu-id="b18c6-149">However, a developer could also use one set of SQL commands to run all the CREATE scripts, as shown in the following sample code:</span></span>  
  
```  
create table #wrapper_functions  
      (function_name sysname, create_stmt nvarchar(max))  
insert into #wrapper_functions  
exec sys.sp_cdc_generate_wrapper_function  
  
declare @stmt nvarchar(max)  
declare #hfunctions cursor local fast_forward for   
      select create_stmt from #wrapper_functions  
open #hfunctions  
fetch #hfunctions into @stmt  
while (@@fetch_status <> -1)  
begin  
      exec sp_executesql @stmt  
      fetch #hfunctions into @stmt  
end  
close #hfunctions  
deallocate #hfunctions  
```  
  
### <a name="understanding-and-using-the-functions-created-by-the-stored-procedure"></a><span data-ttu-id="b18c6-150">了解和使用存储过程创建的函数</span><span class="sxs-lookup"><span data-stu-id="b18c6-150">Understanding and Using the Functions Created by the Stored Procedure</span></span>  
 <span data-ttu-id="b18c6-151">为了系统地遍历捕获的变更数据的时间线，生成的包装函数需要 *@end_time* 一个间隔的参数作为 *@start_time* 后续间隔的参数。</span><span class="sxs-lookup"><span data-stu-id="b18c6-151">To systematically walk the timeline of captured change data, the generated wrapper functions expect that the *@end_time* parameter for one interval will be the *@start_time* parameter for the subsequent interval.</span></span> <span data-ttu-id="b18c6-152">遵循此约定时，生成的包装函数可执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="b18c6-152">When this convention is followed, the generated wrapper functions can do the following tasks:</span></span>  
  
-   <span data-ttu-id="b18c6-153">将日期/时间值映射为内部使用的 LSN 值。</span><span class="sxs-lookup"><span data-stu-id="b18c6-153">Map the date/time values to the LSN values that are used internally.</span></span>  
  
-   <span data-ttu-id="b18c6-154">确保没有数据丢失或重复。</span><span class="sxs-lookup"><span data-stu-id="b18c6-154">Ensure that no data is lost or repeated.</span></span>  
  
 <span data-ttu-id="b18c6-155">为了简化对更改表的所有行的查询，生成的包装函数还支持以下约定：</span><span class="sxs-lookup"><span data-stu-id="b18c6-155">To make querying for all rows of a change table simpler, the generated wrapper functions also support the following conventions:</span></span>  
  
-   <span data-ttu-id="b18c6-156">如果 @start_time 参数为 Null，包装函数使用捕获实例中最低的 LSN 值作为查询的下限。</span><span class="sxs-lookup"><span data-stu-id="b18c6-156">If the @start_time parameter is null, the wrapper functions use the lowest LSN value in the capture instance as the lower bound of the query.</span></span>  
  
-   <span data-ttu-id="b18c6-157">如果 @end_time 参数为 Null，包装函数使用捕获实例中最高的 LSN 值作为查询的上限。</span><span class="sxs-lookup"><span data-stu-id="b18c6-157">If the @end_time parameter is null, the wrapper functions use the highest LSN value in the capture instance as the upper bound of the query.</span></span>  
  
 <span data-ttu-id="b18c6-158">大部分用户应该能够使用 **sys.sp_cdc_generate_wrapper_function** 系统存储过程创建的包装函数而无需进行修改。</span><span class="sxs-lookup"><span data-stu-id="b18c6-158">Most users should be able to use the wrapper functions that the **sys.sp_cdc_generate_wrapper_function** system stored procedure creates without modification.</span></span> <span data-ttu-id="b18c6-159">但是，若要自定义包装函数，您必须自定义 CREATE 脚本，然后再运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="b18c6-159">However, to customize the wrapper functions, you have to customize the CREATE scripts before you run the scripts.</span></span>  
  
 <span data-ttu-id="b18c6-160">当您的包调用包装函数时，该包必须为三个参数提供值。</span><span class="sxs-lookup"><span data-stu-id="b18c6-160">When your package calls the wrapper functions, the package must supply values for three parameters.</span></span> <span data-ttu-id="b18c6-161">这三个参数类似于变更数据捕获函数使用的三个参数。</span><span class="sxs-lookup"><span data-stu-id="b18c6-161">These three parameters are like the three parameters that the change data capture functions use.</span></span> <span data-ttu-id="b18c6-162">这三个参数分别是：</span><span class="sxs-lookup"><span data-stu-id="b18c6-162">These three parameters are as follows:</span></span>  
  
-   <span data-ttu-id="b18c6-163">时间间隔的起始日期/时间值和结束日期/时间值。</span><span class="sxs-lookup"><span data-stu-id="b18c6-163">The starting date/time value and the ending date/time value for the interval.</span></span> <span data-ttu-id="b18c6-164">包装函数使用日期/时间值作为查询间隔的端点，而变更数据捕获函数使用两个 LSN 值作为端点。</span><span class="sxs-lookup"><span data-stu-id="b18c6-164">While the wrapper functions use date/time values as the end points for the query interval, the change data capture functions use two LSN values as the end points.</span></span>  
  
-   <span data-ttu-id="b18c6-165">行筛选器。</span><span class="sxs-lookup"><span data-stu-id="b18c6-165">The row filter.</span></span> <span data-ttu-id="b18c6-166">对于包装函数和变更数据捕获函数， *@row_filter_option* 参数是相同的。</span><span class="sxs-lookup"><span data-stu-id="b18c6-166">For both the wrapper functions and the change data capture functions, the *@row_filter_option* parameter is the same.</span></span> <span data-ttu-id="b18c6-167">有关详细信息，请参阅 [cdc.fn_cdc_get_all_changes_<capture_instance> (Transact-SQL)](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql) 和 [cdc.fn_cdc_get_net_changes_<capture_instance> (Transact SQL)](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b18c6-167">For more information, see [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql) and [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).</span></span>  
  
 <span data-ttu-id="b18c6-168">包装函数返回的结果集包含以下数据：</span><span class="sxs-lookup"><span data-stu-id="b18c6-168">The result set returned by the wrapper functions includesthe following data:</span></span>  
  
-   <span data-ttu-id="b18c6-169">请求的所有变更数据列。</span><span class="sxs-lookup"><span data-stu-id="b18c6-169">All of the requested columns of change data.</span></span>  
  
-   <span data-ttu-id="b18c6-170">名为 __CDC_OPERATION 的列，该列使用单字符或双字符字段来标识与该行关联的操作。</span><span class="sxs-lookup"><span data-stu-id="b18c6-170">A column named __CDC_OPERATION that uses a one- or two-character field to identify the operation that is associated with the row.</span></span> <span data-ttu-id="b18c6-171">此字段的有效值如下：“I”表示插入，“D”表示删除，“UO”表示更新旧值，“UN”表示更新新值。</span><span class="sxs-lookup"><span data-stu-id="b18c6-171">The valid values for this field are as follows: 'I' for insert, 'D' for delete, 'UO' for update old values, and 'UN' for update new values.</span></span>  
  
-   <span data-ttu-id="b18c6-172">在请求标记时更新标志，这些标志在操作代码和参数中指定的顺序中显示为位列 *@update_flag_list* 。</span><span class="sxs-lookup"><span data-stu-id="b18c6-172">Update flags, when you request them, that appear as bit columns after the operation code and in the order that is specified in the *@update_flag_list* parameter.</span></span> <span data-ttu-id="b18c6-173">这些列的命名方式是在关联的列名后追加“_uflag”。</span><span class="sxs-lookup"><span data-stu-id="b18c6-173">These columns are named by appending '_uflag' to the associated column name.</span></span>  
  
 <span data-ttu-id="b18c6-174">如果你的包调用查询所有变更的包装函数，该包装函数还将返回列 __CDC_STARTLSN 和 \__CDC_SEQVAL。</span><span class="sxs-lookup"><span data-stu-id="b18c6-174">If your package calls a wrapper function that queries for all changes, the wrapper function also returns the columns, __CDC_STARTLSN and \__CDC_SEQVAL.</span></span> <span data-ttu-id="b18c6-175">这两列分别成为结果集的第一列和第二列。</span><span class="sxs-lookup"><span data-stu-id="b18c6-175">These two columns become the first and second columns, respectively, of the result set.</span></span> <span data-ttu-id="b18c6-176">包装函数还将基于这两列对结果集进行排序。</span><span class="sxs-lookup"><span data-stu-id="b18c6-176">The wrapper function also sorts the result set based on these two columns.</span></span>  
  
## <a name="writing-your-own-table-value-function"></a><span data-ttu-id="b18c6-177">编写自己的表值函数</span><span class="sxs-lookup"><span data-stu-id="b18c6-177">Writing Your Own Table-Value Function</span></span>  
 <span data-ttu-id="b18c6-178">还可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 编写自己的可调用变更数据捕获查询函数的表值包装函数，并将该表值包装函数存储在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中。</span><span class="sxs-lookup"><span data-stu-id="b18c6-178">You can also use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to write your own table-valued wrapper function that calls the change data capture query function, and store the table-valued wrapper function in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b18c6-179">有关如何创建 Transact-SQL 函数的详细信息，请参阅 [CREATE FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b18c6-179">For more information about how to create a Transact-SQL function, see [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql).</span></span>  
  
 <span data-ttu-id="b18c6-180">下面的示例定义一个表值函数，该表值函数将检索 Customer 表在指定的变更间隔发生的变更。</span><span class="sxs-lookup"><span data-stu-id="b18c6-180">The following example defines a table-valued function that retrieves changes from a Customer table for the specified change interval.</span></span> <span data-ttu-id="b18c6-181">此函数使用变更数据捕获函数将 `datetime` 值映射到变更表内部使用的二进制日志序列号 (LSN) 值。</span><span class="sxs-lookup"><span data-stu-id="b18c6-181">This function uses change data capture functions to map the `datetime` values to the binary log sequence number (LSN) values that the change tables use internally.</span></span> <span data-ttu-id="b18c6-182">此函数还可以处理以下几种特殊情况：</span><span class="sxs-lookup"><span data-stu-id="b18c6-182">This function also handles several special conditions:</span></span>  
  
-   <span data-ttu-id="b18c6-183">将 null 值传递到开始时间时，函数将采用最早的可用值。</span><span class="sxs-lookup"><span data-stu-id="b18c6-183">When a null value is passed for the starting time, this function uses the earliest available value.</span></span>  
  
-   <span data-ttu-id="b18c6-184">将 null 值传递到结束时间时，函数将采用最晚的可用值。</span><span class="sxs-lookup"><span data-stu-id="b18c6-184">When a null value is passed for the ending time, this function uses the latest available value.</span></span>  
  
-   <span data-ttu-id="b18c6-185">如果开始的 LSN 与结束的 LSN 相等，则通常指示所选间隔不存在记录，此函数会退出。</span><span class="sxs-lookup"><span data-stu-id="b18c6-185">When the starting LSN is equal to the ending LSN, which usually indicates that there are no records for the selected interval, this function exits.</span></span>  
  
### <a name="example-of-a-table-value-function-that-queries-for-change-data"></a><span data-ttu-id="b18c6-186">查询变更数据的表值函数示例</span><span class="sxs-lookup"><span data-stu-id="b18c6-186">Example of a Table-Value Function that Queries for Change Data</span></span>  
  
```  
CREATE function CDCSample.uf_Customer (  
     @start_time datetime  
    ,@end_time datetime  
)  
returns @Customer table (  
     CustomerID int  
    ,TerritoryID int  
    ,CustomerType nchar(1)  
    ,rowguid uniqueidentifier  
    ,ModifiedDate datetime  
    ,CDC_OPERATION varchar(1)  
) as  
begin  
    declare @from_lsn binary(10), @to_lsn binary(10)  
  
    if (@start_time is null)  
        select @from_lsn = sys.fn_cdc_get_min_lsn('Customer')  
    else  
        select @from_lsn = sys.fn_cdc_increment_lsn(sys.fn_cdc_map_time_to_lsn('largest less than or equal',@start_time))  
  
    if (@end_time is null)  
        select @to_lsn = sys.fn_cdc_get_max_lsn()  
    else  
        select @to_lsn = sys.fn_cdc_map_time_to_lsn('largest less than or equal',@end_time)  
  
    if (@from_lsn = sys.fn_cdc_increment_lsn(@to_lsn))  
        return  
  
    -- Query for change data  
    insert into @Customer  
    select   
        CustomerID,      
        TerritoryID,   
        CustomerType,   
        rowguid,   
        ModifiedDate,   
        case __$operation  
                when 1 then 'D'  
                when 2 then 'I'  
                when 4 then 'U'  
                else null  
         end as CDC_OPERATION  
    from   
        cdc.fn_cdc_get_net_changes_Customer(@from_lsn, @to_lsn, 'all')  
  
    return  
end   
go  
  
```  
  
### <a name="retrieving-additional-metadata-with-the-change-data"></a><span data-ttu-id="b18c6-187">检索带有变更数据的其他元数据</span><span class="sxs-lookup"><span data-stu-id="b18c6-187">Retrieving Additional Metadata with the Change Data</span></span>  
 <span data-ttu-id="b18c6-188">尽管上述用户创建的表值函数仅使用 **__$operation** 列，**cdc.fn_cdc_get_net_changes_<capture_instance>** 函数将针对每个变更行返回四列元数据。</span><span class="sxs-lookup"><span data-stu-id="b18c6-188">Although the user-created table-valued function shown earlier uses only the **__$operation** column, the **cdc.fn_cdc_get_net_changes_<capture_instance>** function returns four columns of metadata for each change row.</span></span> <span data-ttu-id="b18c6-189">如果想要在数据流中使用这些值，可以从表值包装函数中将它们作为额外的列返回。</span><span class="sxs-lookup"><span data-stu-id="b18c6-189">If you want to use these values in your data flow, you can return them as additional columns from the table-valued wrapper function.</span></span>  
  
|<span data-ttu-id="b18c6-190">列名称</span><span class="sxs-lookup"><span data-stu-id="b18c6-190">Column name</span></span>|<span data-ttu-id="b18c6-191">数据类型</span><span class="sxs-lookup"><span data-stu-id="b18c6-191">Data type</span></span>|<span data-ttu-id="b18c6-192">说明</span><span class="sxs-lookup"><span data-stu-id="b18c6-192">Description</span></span>|  
|-----------------|---------------|-----------------|  
|<span data-ttu-id="b18c6-193">**__$start_lsn**</span><span class="sxs-lookup"><span data-stu-id="b18c6-193">**__$start_lsn**</span></span>|`binary(10)`|<span data-ttu-id="b18c6-194">与更改的提交事务关联的 LSN。</span><span class="sxs-lookup"><span data-stu-id="b18c6-194">LSN associated with the commit transaction for the change.</span></span><br /><br /> <span data-ttu-id="b18c6-195">在同一事务中提交的所有更改将共享同一个提交 LSN。</span><span class="sxs-lookup"><span data-stu-id="b18c6-195">All changes committed in the same transaction share the same commit LSN.</span></span> <span data-ttu-id="b18c6-196">例如，如果对源表的更新操作修改了两个不同的行，则更改表将包含四行（两行具有旧值，两行具有新值），每一行均具有相同的 **__$start_lsn** 值。</span><span class="sxs-lookup"><span data-stu-id="b18c6-196">For example, if an update operation on the source table modifies two different rows, the change table will contain four rows (two with the old values and two with the new values), each with the same **__$start_lsn** value.</span></span>|  
|<span data-ttu-id="b18c6-197">**__$seqval**</span><span class="sxs-lookup"><span data-stu-id="b18c6-197">**__$seqval**</span></span>|`binary(10)`|<span data-ttu-id="b18c6-198">用于对事务中的行更改进行排序的序列值。</span><span class="sxs-lookup"><span data-stu-id="b18c6-198">Sequence value that is used to order the row changes in a transaction.</span></span>|  
|<span data-ttu-id="b18c6-199">**__$operation**</span><span class="sxs-lookup"><span data-stu-id="b18c6-199">**__$operation**</span></span>|`int`|<span data-ttu-id="b18c6-200">与更改关联的数据操作语言 (DML) 操作。</span><span class="sxs-lookup"><span data-stu-id="b18c6-200">The data manipulation language (DML) operation associated with the change.</span></span> <span data-ttu-id="b18c6-201">可以是以下值之一：</span><span class="sxs-lookup"><span data-stu-id="b18c6-201">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="b18c6-202">1 = 删除</span><span class="sxs-lookup"><span data-stu-id="b18c6-202">1 = delete</span></span><br /><br /> <span data-ttu-id="b18c6-203">2 = 插入</span><span class="sxs-lookup"><span data-stu-id="b18c6-203">2 = insert</span></span><br /><br /> <span data-ttu-id="b18c6-204">3 = 更新（执行更新操作前的值。）</span><span class="sxs-lookup"><span data-stu-id="b18c6-204">3 = update (Values before the update operation.)</span></span><br /><br /> <span data-ttu-id="b18c6-205">4 = 更新（执行更新操作后的值。）</span><span class="sxs-lookup"><span data-stu-id="b18c6-205">4 = update (Values after the update operation.)</span></span>|  
|<span data-ttu-id="b18c6-206">**__$update_mask**</span><span class="sxs-lookup"><span data-stu-id="b18c6-206">**__$update_mask**</span></span>|`varbinary(128)`|<span data-ttu-id="b18c6-207">基于变更表的列序号的位掩码，用于标识那些发生了变更的列。</span><span class="sxs-lookup"><span data-stu-id="b18c6-207">A bitmask that is based on the column ordinals of the change table identifying those columns that changed.</span></span> <span data-ttu-id="b18c6-208">如果需要确定哪些列发生了更改，则可检查此值。</span><span class="sxs-lookup"><span data-stu-id="b18c6-208">You could examine this value if you had to determine which columns have changed.</span></span>|  
|**\<captured source table columns>**|<span data-ttu-id="b18c6-209">多种多样</span><span class="sxs-lookup"><span data-stu-id="b18c6-209">varies</span></span>|<span data-ttu-id="b18c6-210">函数返回的其余列是在创建捕获实例时源表中标识为已捕获列的那些列。</span><span class="sxs-lookup"><span data-stu-id="b18c6-210">The remaining columns returned by the function are the columns from the source table that were identified as captured columns when the capture instance was created.</span></span> <span data-ttu-id="b18c6-211">如果已捕获列的列表中最初未指定任何列，则将返回源表中的所有列。</span><span class="sxs-lookup"><span data-stu-id="b18c6-211">If no columns were originally specified in the captured column list, all columns in the source table are returned.</span></span>|  
  
 <span data-ttu-id="b18c6-212">有关详细信息，请参阅[cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; (Transact-SQL)](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b18c6-212">For more information, see [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="b18c6-213">下一步</span><span class="sxs-lookup"><span data-stu-id="b18c6-213">Next Step</span></span>  
 <span data-ttu-id="b18c6-214">在创建了用于查询变更数据的表值函数之后，下一步就是开始设计包中的数据流。</span><span class="sxs-lookup"><span data-stu-id="b18c6-214">After you have created the table-valued function that queries for change data, the next step is to start designing the data flow in the package.</span></span>  
  
 <span data-ttu-id="b18c6-215">**下一个主题：** [检索和了解变更数据](retrieve-and-understand-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="b18c6-215">**Next topic:** [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md)</span></span>  
  
  
