---
title: dta 实用工具 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- physical design structures [SQL Server]
- command prompt utilities [SQL Server], dta
- dta utility
- tuning databases [SQL Server], Database Engine Tuning Advisor
- workloads [SQL Server], analyzing
- dta utility, about dta utility
- performance [SQL Server], Database Engine Tuning Advisor
- Database Engine Tuning Advisor [SQL Server], command prompt
- optimizing databases [SQL Server]
ms.assetid: a0b210ce-9b58-4709-80cb-9363b68a1f5a
author: stevestein
ms.author: sstein
ms.openlocfilehash: f9cd5a904993f1044c1cbeff8e1cdfc07332da64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693150"
---
# <a name="dta-utility"></a><span data-ttu-id="f33ad-102">dta 实用工具</span><span class="sxs-lookup"><span data-stu-id="f33ad-102">dta Utility</span></span>
  <span data-ttu-id="f33ad-103">**dta** 实用工具是数据库引擎优化顾问的命令提示符版。</span><span class="sxs-lookup"><span data-stu-id="f33ad-103">The **dta** utility is the command prompt version of Database Engine Tuning Advisor.</span></span> <span data-ttu-id="f33ad-104">通过 **dta** 实用工具，您可以在应用程序和脚本中使用数据库引擎优化顾问功能。</span><span class="sxs-lookup"><span data-stu-id="f33ad-104">The **dta** utility is designed to allow you to use Database Engine Tuning Advisor functionality in applications and scripts.</span></span>  
  
 <span data-ttu-id="f33ad-105">与数据库引擎优化顾问一样， **dta** 实用工具可以分析工作负荷，并可为该工作负荷推荐可改进服务器性能的物理设计结构。</span><span class="sxs-lookup"><span data-stu-id="f33ad-105">Like Database Engine Tuning Advisor, the **dta** utility analyzes a workload and recommends physical design structures to improve server performance for that workload.</span></span> <span data-ttu-id="f33ad-106">工作负荷可以是计划缓存、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 跟踪文件或跟踪表，也可以是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本。</span><span class="sxs-lookup"><span data-stu-id="f33ad-106">The workload can be a plan cache, a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] trace file or table, or a [!INCLUDE[tsql](../../includes/tsql-md.md)] script.</span></span> <span data-ttu-id="f33ad-107">物理设计结构包括索引、索引视图和分区。</span><span class="sxs-lookup"><span data-stu-id="f33ad-107">Physical design structures include indexes, indexed views, and partitioning.</span></span> <span data-ttu-id="f33ad-108">分析了工作负荷后， **dta** 实用工具将生成数据库物理设计结构建议，并可生成实现该建议所需的脚本。</span><span class="sxs-lookup"><span data-stu-id="f33ad-108">After analyzing a workload, the **dta** utility produces a recommendation for the physical design of databases and can generate the necessary script to implement the recommendation.</span></span> <span data-ttu-id="f33ad-109">可以在命令提示符处，使用 **-if** 或 **-it** 参数指定工作负荷。</span><span class="sxs-lookup"><span data-stu-id="f33ad-109">Workloads can be specified from the command prompt with the **-if** or the **-it** argument.</span></span> <span data-ttu-id="f33ad-110">也可以在命令提示符处，使用 **-ix** 参数指定 XML 输入文件。</span><span class="sxs-lookup"><span data-stu-id="f33ad-110">You can also specify an XML input file from the command prompt with the **-ix** argument.</span></span> <span data-ttu-id="f33ad-111">在这种情况下，在 XML 输入文件中指定工作负荷。</span><span class="sxs-lookup"><span data-stu-id="f33ad-111">In that case, the workload is specified in the XML input file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f33ad-112">语法</span><span class="sxs-lookup"><span data-stu-id="f33ad-112">Syntax</span></span>  
  
```  
  
      dta  
[ -? ] |  
[  
      [ -S server_name[ \instance ] ]  
      { { -U login_id [-P password ] } | -E  }  
      { -D database_name [ ,...n ] }  
      [ -ddatabase_name ]   
      [ -Tltable_list | -Tf table_list_file ]  
      { -if workload_file | -it workload_trace_table_name  |   
        -ip | -ipf }  
      { -ssession_name | -IDsession_ID }  
      [ -F ]  
      [ -of output_script_file_name ]  
      [ -oroutput_xml_report_file_name ]  
      [ -ox output_XML_file_name ]  
      [ -rl analysis_report_list [ ,...n ] ]  
      [ -ix input_XML_file_name ]  
      [ -A time_for_tuning_in_minutes ]  
      [ -nnumber_of_events ]  
      [ -m minimum_improvement ]  
      [ -fa physical_design_structures_to_add ]  
      [ -fi ]  
      [ -fppartitioning_strategy ]  
      [ -fk keep_existing_option ]  
      [ -fxdrop_only_mode ]  
      [ -B storage_size ]  
      [ -cmax_key_columns_in_index ]  
      [ -C max_columns_in_index ]  
      [ -e | -e tuning_log_name ]  
      [ -N online_option]  
      [ -q ]  
      [ -u ]  
      [ -x ]  
      [ -a ]  
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f33ad-113">参数</span><span class="sxs-lookup"><span data-stu-id="f33ad-113">Arguments</span></span>  
 <span data-ttu-id="f33ad-114">**-?**</span><span class="sxs-lookup"><span data-stu-id="f33ad-114">**-?**</span></span>  
 <span data-ttu-id="f33ad-115">显示用法信息。</span><span class="sxs-lookup"><span data-stu-id="f33ad-115">Displays usage information.</span></span>  
  
 <span data-ttu-id="f33ad-116">**-A** _time_for_tuning_in_minutes_</span><span class="sxs-lookup"><span data-stu-id="f33ad-116">**-A** _time_for_tuning_in_minutes_</span></span>  
 <span data-ttu-id="f33ad-117">指定优化时间限制（分钟）。</span><span class="sxs-lookup"><span data-stu-id="f33ad-117">Specifies the tuning time limit in minutes.</span></span> <span data-ttu-id="f33ad-118">**dta** 使用指定的时间优化工作负荷，并生成一个包含建议的物理设计更改的脚本。</span><span class="sxs-lookup"><span data-stu-id="f33ad-118">**dta** uses the specified amount of time to tune the workload and generate a script with the recommended physical design changes.</span></span> <span data-ttu-id="f33ad-119">默认情况下， **dta** 采用的优化时间为 8 小时。</span><span class="sxs-lookup"><span data-stu-id="f33ad-119">By default **dta** assumes a tuning time of 8 hours.</span></span> <span data-ttu-id="f33ad-120">指定 0 允许不限制优化时间。</span><span class="sxs-lookup"><span data-stu-id="f33ad-120">Specifying 0allows unlimited tuning time.</span></span> <span data-ttu-id="f33ad-121">**dta** 可能在限制时间之前完成整个工作负荷的优化。</span><span class="sxs-lookup"><span data-stu-id="f33ad-121">**dta** might finish tuning the entire workload before the time limit expires.</span></span> <span data-ttu-id="f33ad-122">但是，为确保整个工作负荷都得到优化，我们建议您指定不受限制的优化时间 (-A 0)。</span><span class="sxs-lookup"><span data-stu-id="f33ad-122">However, to make sure that the entire workload is tuned, we recommend that you specify unlimited tuning time (-A 0).</span></span>  
  
 <span data-ttu-id="f33ad-123">**-a**</span><span class="sxs-lookup"><span data-stu-id="f33ad-123">**-a**</span></span>  
 <span data-ttu-id="f33ad-124">优化工作负荷和应用建议时不作提示。</span><span class="sxs-lookup"><span data-stu-id="f33ad-124">Tunes workload and applies the recommendation without prompting you.</span></span>  
  
 <span data-ttu-id="f33ad-125">**-B** _storage_size_</span><span class="sxs-lookup"><span data-stu-id="f33ad-125">**-B** _storage_size_</span></span>  
 <span data-ttu-id="f33ad-126">指定推荐的索引和分区可以使用的最大空间 (MB)。</span><span class="sxs-lookup"><span data-stu-id="f33ad-126">Specifies the maximum space in megabytes that can be consumed by the recommended index and partitioning.</span></span> <span data-ttu-id="f33ad-127">优化多个数据库时，建议对所有数据库都进行空间计算。</span><span class="sxs-lookup"><span data-stu-id="f33ad-127">When multiple databases are tuned, recommendations for all databases are considered for the space calculation.</span></span> <span data-ttu-id="f33ad-128">默认情况下， **dta** 采用下列存储大小中较小的一个：</span><span class="sxs-lookup"><span data-stu-id="f33ad-128">By default, **dta** assumes the smaller of the following storage sizes:</span></span>  
  
-   <span data-ttu-id="f33ad-129">当前原始数据大小的三倍，包括数据库中表的堆和聚集索引的总大小。</span><span class="sxs-lookup"><span data-stu-id="f33ad-129">Three times the current raw data size, which includes the total size of heaps and clustered indexes on tables in the database.</span></span>  
  
-   <span data-ttu-id="f33ad-130">所有已附连磁盘驱动器的可用空间加上原始数据的大小。</span><span class="sxs-lookup"><span data-stu-id="f33ad-130">The free space on all attached disk drives plus the raw data size.</span></span>  
  
 <span data-ttu-id="f33ad-131">默认存储大小不包括非聚集索引和索引视图。</span><span class="sxs-lookup"><span data-stu-id="f33ad-131">The default storage size does not include nonclustered indexes and indexed views.</span></span>  
  
 <span data-ttu-id="f33ad-132">**-C** _max_columns_in_index_</span><span class="sxs-lookup"><span data-stu-id="f33ad-132">**-C** _max_columns_in_index_</span></span>  
 <span data-ttu-id="f33ad-133">指定 **dta** 推荐的索引中的最大列数。</span><span class="sxs-lookup"><span data-stu-id="f33ad-133">Specifies the maximum number of columns in indexes that **dta** proposes.</span></span> <span data-ttu-id="f33ad-134">最大值为 1024。</span><span class="sxs-lookup"><span data-stu-id="f33ad-134">The maximum value  is 1024.</span></span> <span data-ttu-id="f33ad-135">默认情况下，此参数设置为 16。</span><span class="sxs-lookup"><span data-stu-id="f33ad-135">By default, this argument is set to 16.</span></span>  
  
 <span data-ttu-id="f33ad-136">**-c** _max_key_columns_in_index_</span><span class="sxs-lookup"><span data-stu-id="f33ad-136">**-c** _max_key_columns_in_index_</span></span>  
 <span data-ttu-id="f33ad-137">指定 **dta** 推荐的索引中的最大键列数。</span><span class="sxs-lookup"><span data-stu-id="f33ad-137">Specifies the maximum number of key columns in indexes that **dta** proposes.</span></span> <span data-ttu-id="f33ad-138">默认值为 16，允许该最大值。</span><span class="sxs-lookup"><span data-stu-id="f33ad-138">The default value is 16, the maximum value allowed.</span></span> <span data-ttu-id="f33ad-139">**dta** 也会考虑创建带有包含列的索引。</span><span class="sxs-lookup"><span data-stu-id="f33ad-139">**dta** also considers creating indexes with included columns.</span></span> <span data-ttu-id="f33ad-140">建议的包含列的索引可能会超出此参数中指定的列数。</span><span class="sxs-lookup"><span data-stu-id="f33ad-140">Indexes recommended with included columns may exceed the number of columns specified in this argument.</span></span>  
  
 <span data-ttu-id="f33ad-141">**-D** _database_name_</span><span class="sxs-lookup"><span data-stu-id="f33ad-141">**-D** _database_name_</span></span>  
 <span data-ttu-id="f33ad-142">指定要优化的每个数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="f33ad-142">Specifies the name of each database that is to be tuned.</span></span> <span data-ttu-id="f33ad-143">第一个数据库是默认数据库。</span><span class="sxs-lookup"><span data-stu-id="f33ad-143">The first database is the default database.</span></span> <span data-ttu-id="f33ad-144">可以指定多个数据库，各数据库名称用逗号进行分隔。例如：</span><span class="sxs-lookup"><span data-stu-id="f33ad-144">You can specify multiple databases by separating the database names with commas, for example:</span></span>  
  
```  
dta -D database_name1, database_name2...  
```  
  
 <span data-ttu-id="f33ad-145">此外，也可以对各个数据库名称使用 -D  参数，从而指定多个数据库。例如：</span><span class="sxs-lookup"><span data-stu-id="f33ad-145">Alternatively, you can specify multiple databases by using the **-D** argument for each database name, for example:</span></span>  
  
```  
dta -D database_name1 -D database_name2... n  
```  
  
 <span data-ttu-id="f33ad-146">**-D** 参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="f33ad-146">The **-D** argument is mandatory.</span></span> <span data-ttu-id="f33ad-147">如果尚未指定 **-d** 参数，则 **dta** 将默认连接到工作负荷中第一个 `USE database_name` 子句指定的数据库。</span><span class="sxs-lookup"><span data-stu-id="f33ad-147">If the **-d** argument has not been specified, **dta** initially connects to the database that is specified with the first `USE database_name` clause in the workload.</span></span> <span data-ttu-id="f33ad-148">如果工作负荷中没有显式的 `USE database_name` 子句，则必须使用 **-d** 参数。</span><span class="sxs-lookup"><span data-stu-id="f33ad-148">If there is not explicit `USE database_name` clause in the workload, you must use the **-d** argument.</span></span>  
  
 <span data-ttu-id="f33ad-149">例如，如果有一个工作负荷未包含显式的 `USE database_name` 子句，则在使用以下 **dta** 命令时将不会生成建议：</span><span class="sxs-lookup"><span data-stu-id="f33ad-149">For example, if you have a workload that contains no explicit `USE database_name` clause, and you use the following **dta** command, a recommendation will not be generated:</span></span>  
  
```  
dta -D db_name1, db_name2...  
```  
  
 <span data-ttu-id="f33ad-150">但是，如果使用同一工作负荷时使用了以下带 **-d** 参数的 **dta** 命令，则将生成建议：</span><span class="sxs-lookup"><span data-stu-id="f33ad-150">But if you use the same workload, and use the following **dta** command that uses the **-d** argument, a recommendation will be generated:</span></span>  
  
```  
dta -D db_name1, db_name2 -d db_name1  
```  
  
 <span data-ttu-id="f33ad-151">**-d** _database_name_</span><span class="sxs-lookup"><span data-stu-id="f33ad-151">**-d** _database_name_</span></span>  
 <span data-ttu-id="f33ad-152">指定优化工作负荷时 **dta** 连接到的第一个数据库。</span><span class="sxs-lookup"><span data-stu-id="f33ad-152">Specifies the first database to which **dta** connects when tuning a workload.</span></span> <span data-ttu-id="f33ad-153">只能为此参数指定一个数据库。</span><span class="sxs-lookup"><span data-stu-id="f33ad-153">Only one database can be specified for this argument.</span></span> <span data-ttu-id="f33ad-154">例如：</span><span class="sxs-lookup"><span data-stu-id="f33ad-154">For example:</span></span>  
  
```  
dta -d AdventureWorks2012 ...  
```  
  
 <span data-ttu-id="f33ad-155">如果指定多个数据库名称， **dta** 将返回错误。</span><span class="sxs-lookup"><span data-stu-id="f33ad-155">If multiple database names are specified, then **dta** returns an error.</span></span> <span data-ttu-id="f33ad-156">**-d** 参数是可选的。</span><span class="sxs-lookup"><span data-stu-id="f33ad-156">The **-d** argument is optional.</span></span>  
  
 <span data-ttu-id="f33ad-157">如果使用 XML 输入文件，则可使用元素下的元素指定**dta**连接到的第一个数据库 `DatabaseToConnect` `TuningOptions` 。</span><span class="sxs-lookup"><span data-stu-id="f33ad-157">If you are using an XML input file, you can specify the first database to which **dta** connects by using the `DatabaseToConnect` element that is located under the `TuningOptions` element.</span></span> <span data-ttu-id="f33ad-158">有关详细信息，请参阅 [Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="f33ad-158">For more information, see [Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md).</span></span>  
  
 <span data-ttu-id="f33ad-159">如果只优化一个数据库，则 **-d** 参数的功能将类似于 **sqlcmd** 实用工具中的 **-d** 参数的功能，但不执行 USE *database_name* 语句。</span><span class="sxs-lookup"><span data-stu-id="f33ad-159">If you are tuning only one database, the **-d** argument provides functionality that is similar to the **-d** argument in the **sqlcmd** utility, but it does not execute the USE *database_name* statement.</span></span> <span data-ttu-id="f33ad-160">有关详细信息，请参阅 [sqlcmd Utility](../sqlcmd-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="f33ad-160">For more information, see [sqlcmd Utility](../sqlcmd-utility.md).</span></span>  
  
 <span data-ttu-id="f33ad-161">**-E**</span><span class="sxs-lookup"><span data-stu-id="f33ad-161">**-E**</span></span>  
 <span data-ttu-id="f33ad-162">使用可信连接而不请求密码。</span><span class="sxs-lookup"><span data-stu-id="f33ad-162">Uses a trusted connection instead of requesting a password.</span></span> <span data-ttu-id="f33ad-163">必须使用指定登录 ID 的 **-E** 参数或 **-U** 参数。</span><span class="sxs-lookup"><span data-stu-id="f33ad-163">Either the **-E** argument or the **-U** argument, which specifies a login ID, must be used.</span></span>  
  
 <span data-ttu-id="f33ad-164">**-e** _tuning_log_name_</span><span class="sxs-lookup"><span data-stu-id="f33ad-164">**-e** _tuning_log_name_</span></span>  
 <span data-ttu-id="f33ad-165">指定 **dta** 记录其无法优化的事件的表或文件的名称。</span><span class="sxs-lookup"><span data-stu-id="f33ad-165">Specifies the name of the table or file where **dta** records events that it could not tune.</span></span> <span data-ttu-id="f33ad-166">表的创建位置是执行优化的服务器。</span><span class="sxs-lookup"><span data-stu-id="f33ad-166">The table is created on the server where the tuning is performed.</span></span>  
  
 <span data-ttu-id="f33ad-167">如果使用表，则用以下格式指定其名称： *[database_name].[owner_name].table_name*。</span><span class="sxs-lookup"><span data-stu-id="f33ad-167">If a table is used, specify its name in the format: *[database_name].[owner_name].table_name*.</span></span> <span data-ttu-id="f33ad-168">下表显示了每个参数的默认值：</span><span class="sxs-lookup"><span data-stu-id="f33ad-168">The following table shows the default values for each parameter:</span></span>  
  
|<span data-ttu-id="f33ad-169">参数</span><span class="sxs-lookup"><span data-stu-id="f33ad-169">Parameter</span></span>|<span data-ttu-id="f33ad-170">默认值</span><span class="sxs-lookup"><span data-stu-id="f33ad-170">Default value</span></span>|  
|---------------|-------------------|  
|<span data-ttu-id="f33ad-171">*database_name*</span><span class="sxs-lookup"><span data-stu-id="f33ad-171">*database_name*</span></span>|<span data-ttu-id="f33ad-172">使用 -D  选项指定的 database_name </span><span class="sxs-lookup"><span data-stu-id="f33ad-172">*database_name* specified with the **-D** option</span></span>|  
|<span data-ttu-id="f33ad-173">*owner_name*</span><span class="sxs-lookup"><span data-stu-id="f33ad-173">*owner_name*</span></span>|<span data-ttu-id="f33ad-174">**dbo**</span><span class="sxs-lookup"><span data-stu-id="f33ad-174">**dbo**</span></span><br /><br /> <span data-ttu-id="f33ad-175">注意： *owner_name*必须为**dbo**。</span><span class="sxs-lookup"><span data-stu-id="f33ad-175">Note: *owner_name* must be **dbo**.</span></span> <span data-ttu-id="f33ad-176">如果指定了其他值，则 **dta** 执行将失败并返回错误。</span><span class="sxs-lookup"><span data-stu-id="f33ad-176">If any other value is specified, then **dta** execution fails and it returns an error.</span></span>|  
|<span data-ttu-id="f33ad-177">*table_name*</span><span class="sxs-lookup"><span data-stu-id="f33ad-177">*table_name*</span></span>|<span data-ttu-id="f33ad-178">无</span><span class="sxs-lookup"><span data-stu-id="f33ad-178">None</span></span>|  
  
 <span data-ttu-id="f33ad-179">如果使用文件，则指定 .xml 作为其扩展名。</span><span class="sxs-lookup"><span data-stu-id="f33ad-179">If a file is used, specify .xml as its extension.</span></span> <span data-ttu-id="f33ad-180">例如，TuningLog.xml。</span><span class="sxs-lookup"><span data-stu-id="f33ad-180">For example, TuningLog.xml.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f33ad-181">如果删除该会话，则 **dta** 实用工具不会删除用户指定的优化日志表的内容。</span><span class="sxs-lookup"><span data-stu-id="f33ad-181">The **dta** utility does not delete the contents of user-specified tuning log tables if the session is deleted.</span></span> <span data-ttu-id="f33ad-182">优化超大型工作负荷时，建议为优化日志指定一个表。</span><span class="sxs-lookup"><span data-stu-id="f33ad-182">When tuning very large workloads, we recommend that a table be specified for the tuning log.</span></span> <span data-ttu-id="f33ad-183">由于优化大型工作负荷可导致优化日志增大，因此使用表时删除会话的速度可快得多。</span><span class="sxs-lookup"><span data-stu-id="f33ad-183">Since tuning large workloads can result in large tuning logs, the sessions can be deleted much faster when a table is used.</span></span>  
  
 <span data-ttu-id="f33ad-184">**-F**</span><span class="sxs-lookup"><span data-stu-id="f33ad-184">**-F**</span></span>  
 <span data-ttu-id="f33ad-185">允许 **dta** 覆盖现有的输出文件。</span><span class="sxs-lookup"><span data-stu-id="f33ad-185">Permits **dta** to overwrite an existing output file.</span></span> <span data-ttu-id="f33ad-186">如果已经存在同名输出文件，并且没有指定 **-F** ，则 **dta**将返回错误。</span><span class="sxs-lookup"><span data-stu-id="f33ad-186">If an output file with the same name already exists and **-F** is not specified, **dta**returns an error.</span></span> <span data-ttu-id="f33ad-187">你可以使用具有 **-of** 、 **-or**或 **-ox**的 **-F**。</span><span class="sxs-lookup"><span data-stu-id="f33ad-187">You can use **-F** with **-of**, **-or**, or **-ox**.</span></span>  
  
 <span data-ttu-id="f33ad-188">**-fa** _physical_design_structures_to_add_</span><span class="sxs-lookup"><span data-stu-id="f33ad-188">**-fa** _physical_design_structures_to_add_</span></span>  
 <span data-ttu-id="f33ad-189">指定 **dta** 应在建议中包括的物理设计结构的类型。</span><span class="sxs-lookup"><span data-stu-id="f33ad-189">Specifies what types of physical design structures **dta** should include in the recommendation.</span></span> <span data-ttu-id="f33ad-190">下表列出并说明了可为此参数指定的值。</span><span class="sxs-lookup"><span data-stu-id="f33ad-190">The following table lists and describes the values that can be specified for this argument.</span></span> <span data-ttu-id="f33ad-191">如果未指定任何值， **dta**将使用默认的 **-fa** `IDX` 。</span><span class="sxs-lookup"><span data-stu-id="f33ad-191">When no value is specified, **dta** uses the default **-fa**`IDX`.</span></span>  
  
|<span data-ttu-id="f33ad-192">值</span><span class="sxs-lookup"><span data-stu-id="f33ad-192">Value</span></span>|<span data-ttu-id="f33ad-193">说明</span><span class="sxs-lookup"><span data-stu-id="f33ad-193">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f33ad-194">IDX_IV</span><span class="sxs-lookup"><span data-stu-id="f33ad-194">IDX_IV</span></span>|<span data-ttu-id="f33ad-195">索引和索引视图。</span><span class="sxs-lookup"><span data-stu-id="f33ad-195">Indexes and indexed views.</span></span>|  
|<span data-ttu-id="f33ad-196">IDX</span><span class="sxs-lookup"><span data-stu-id="f33ad-196">IDX</span></span>|<span data-ttu-id="f33ad-197">仅限索引。</span><span class="sxs-lookup"><span data-stu-id="f33ad-197">Indexes only.</span></span>|  
|<span data-ttu-id="f33ad-198">IV</span><span class="sxs-lookup"><span data-stu-id="f33ad-198">IV</span></span>|<span data-ttu-id="f33ad-199">仅限索引视图。</span><span class="sxs-lookup"><span data-stu-id="f33ad-199">Indexed views only.</span></span>|  
|<span data-ttu-id="f33ad-200">NCL_IDX</span><span class="sxs-lookup"><span data-stu-id="f33ad-200">NCL_IDX</span></span>|<span data-ttu-id="f33ad-201">仅限非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="f33ad-201">Nonclustered indexes only.</span></span>|  
  
 <span data-ttu-id="f33ad-202">**-fi**</span><span class="sxs-lookup"><span data-stu-id="f33ad-202">**-fi**</span></span>  
 <span data-ttu-id="f33ad-203">指定将在新建议中考虑筛选的索引。</span><span class="sxs-lookup"><span data-stu-id="f33ad-203">Specifies that filtered indexes be considered for new recommendations.</span></span> <span data-ttu-id="f33ad-204">有关详细信息，请参阅 [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="f33ad-204">For more information, see [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md).</span></span>  
  
 <span data-ttu-id="f33ad-205">**-fk** _keep_existing_option_</span><span class="sxs-lookup"><span data-stu-id="f33ad-205">**-fk** _keep_existing_option_</span></span>  
 <span data-ttu-id="f33ad-206">指定 **dta** 在生成其建议时必须保留的现有物理设计结构。</span><span class="sxs-lookup"><span data-stu-id="f33ad-206">Specifies what existing physical design structures **dta** must retain when generating its recommendation.</span></span> <span data-ttu-id="f33ad-207">下表列出并介绍了可以为此参数指定的值：</span><span class="sxs-lookup"><span data-stu-id="f33ad-207">The following table lists and describes the values that can be specified for this argument:</span></span>  
  
|<span data-ttu-id="f33ad-208">值</span><span class="sxs-lookup"><span data-stu-id="f33ad-208">Value</span></span>|<span data-ttu-id="f33ad-209">说明</span><span class="sxs-lookup"><span data-stu-id="f33ad-209">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f33ad-210">无</span><span class="sxs-lookup"><span data-stu-id="f33ad-210">NONE</span></span>|<span data-ttu-id="f33ad-211">无现有结构</span><span class="sxs-lookup"><span data-stu-id="f33ad-211">No existing structures</span></span>|  
|<span data-ttu-id="f33ad-212">ALL</span><span class="sxs-lookup"><span data-stu-id="f33ad-212">ALL</span></span>|<span data-ttu-id="f33ad-213">所有现有结构</span><span class="sxs-lookup"><span data-stu-id="f33ad-213">All existing structures</span></span>|  
|<span data-ttu-id="f33ad-214">ALIGNED</span><span class="sxs-lookup"><span data-stu-id="f33ad-214">ALIGNED</span></span>|<span data-ttu-id="f33ad-215">所有分区对齐结构。</span><span class="sxs-lookup"><span data-stu-id="f33ad-215">All partition-aligned structures.</span></span>|  
|<span data-ttu-id="f33ad-216">CL_IDX</span><span class="sxs-lookup"><span data-stu-id="f33ad-216">CL_IDX</span></span>|<span data-ttu-id="f33ad-217">表中的所有聚集索引</span><span class="sxs-lookup"><span data-stu-id="f33ad-217">All clustered indexes on tables</span></span>|  
|<span data-ttu-id="f33ad-218">IDX</span><span class="sxs-lookup"><span data-stu-id="f33ad-218">IDX</span></span>|<span data-ttu-id="f33ad-219">表中的所有聚集索引和非聚集索引</span><span class="sxs-lookup"><span data-stu-id="f33ad-219">All clustered and nonclustered indexes on tables</span></span>|  
  
 <span data-ttu-id="f33ad-220">**-fp** _partitioning_strategy_</span><span class="sxs-lookup"><span data-stu-id="f33ad-220">**-fp** _partitioning_strategy_</span></span>  
 <span data-ttu-id="f33ad-221">指定 **dta** 建议的新物理设计结构（索引和索引视图）是否应进行分区以及如何进行分区。</span><span class="sxs-lookup"><span data-stu-id="f33ad-221">Specifies whether new physical design structures (indexes and indexed views) that **dta** proposes should be partitioned, and how they should be partitioned.</span></span> <span data-ttu-id="f33ad-222">下表列出并介绍了可以为此参数指定的值：</span><span class="sxs-lookup"><span data-stu-id="f33ad-222">The following table lists and describes the values that can be specified for this argument:</span></span>  
  
|<span data-ttu-id="f33ad-223">值</span><span class="sxs-lookup"><span data-stu-id="f33ad-223">Value</span></span>|<span data-ttu-id="f33ad-224">说明</span><span class="sxs-lookup"><span data-stu-id="f33ad-224">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f33ad-225">无</span><span class="sxs-lookup"><span data-stu-id="f33ad-225">NONE</span></span>|<span data-ttu-id="f33ad-226">不分区</span><span class="sxs-lookup"><span data-stu-id="f33ad-226">No partitioning</span></span>|  
|<span data-ttu-id="f33ad-227">FULL</span><span class="sxs-lookup"><span data-stu-id="f33ad-227">FULL</span></span>|<span data-ttu-id="f33ad-228">完全分区（选择该值可增强性能）</span><span class="sxs-lookup"><span data-stu-id="f33ad-228">Full partitioning (choose to enhance performance)</span></span>|  
|<span data-ttu-id="f33ad-229">ALIGNED</span><span class="sxs-lookup"><span data-stu-id="f33ad-229">ALIGNED</span></span>|<span data-ttu-id="f33ad-230">仅限对齐分区（选择该值可增强可管理性）</span><span class="sxs-lookup"><span data-stu-id="f33ad-230">Aligned partitioning only (choose to enhance manageability)</span></span>|  
  
 <span data-ttu-id="f33ad-231">ALIGNED 表示在 **dta** 生成的建议中，每个建议的索引都完全按定义该索引的基础表所用的方式进行分区。</span><span class="sxs-lookup"><span data-stu-id="f33ad-231">ALIGNED means that in the recommendation generated by **dta** every proposed index is partitioned in exactly the same way as the underlying table for which the index is defined.</span></span> <span data-ttu-id="f33ad-232">索引视图中的非聚集索引与索引视图对齐。</span><span class="sxs-lookup"><span data-stu-id="f33ad-232">Nonclustered indexes on an indexed view are aligned with the indexed view.</span></span> <span data-ttu-id="f33ad-233">只能为此参数指定一个值。</span><span class="sxs-lookup"><span data-stu-id="f33ad-233">Only one value can be specified for this argument.</span></span> <span data-ttu-id="f33ad-234">默认值为 **-fp** `NONE` 。</span><span class="sxs-lookup"><span data-stu-id="f33ad-234">The default is **-fp**`NONE`.</span></span>  
  
 <span data-ttu-id="f33ad-235">**-fx** _drop_only_mode_</span><span class="sxs-lookup"><span data-stu-id="f33ad-235">**-fx** _drop_only_mode_</span></span>  
 <span data-ttu-id="f33ad-236">指定 **dta** 仅考虑删除现有物理设计结构。</span><span class="sxs-lookup"><span data-stu-id="f33ad-236">Specifies that **dta** only considers dropping existing physical design structures.</span></span> <span data-ttu-id="f33ad-237">没有考虑任何新的物理设计结构。</span><span class="sxs-lookup"><span data-stu-id="f33ad-237">No new physical design structures are considered.</span></span> <span data-ttu-id="f33ad-238">如果指定此选项， **dta** 将评估现有物理设计结构的使用情况，并建议删除很少使用的结构。</span><span class="sxs-lookup"><span data-stu-id="f33ad-238">When this option is specified, **dta** evaluates the usefulness of existing physical design structures and recommends dropping seldom used structures.</span></span> <span data-ttu-id="f33ad-239">此参数不带任何值，</span><span class="sxs-lookup"><span data-stu-id="f33ad-239">This argument takes no values.</span></span> <span data-ttu-id="f33ad-240">它不能与 **-fa**、 **-fp**或 **-fk ALL** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="f33ad-240">It cannot be used with the **-fa**, **-fp**, or **-fk ALL** arguments</span></span>  
  
 <span data-ttu-id="f33ad-241">**-ID** _session_ID_</span><span class="sxs-lookup"><span data-stu-id="f33ad-241">**-ID** _session_ID_</span></span>  
 <span data-ttu-id="f33ad-242">为优化会话指定一个数字标识符。</span><span class="sxs-lookup"><span data-stu-id="f33ad-242">Specifies a numerical identifier for the tuning session.</span></span> <span data-ttu-id="f33ad-243">如果未指定，则 **dta** 将生成一个 ID 号。</span><span class="sxs-lookup"><span data-stu-id="f33ad-243">If not specified, then **dta** generates an ID number.</span></span> <span data-ttu-id="f33ad-244">可以使用此标识符查看现有优化会话的信息。</span><span class="sxs-lookup"><span data-stu-id="f33ad-244">You can use this identifier to view information for existing tuning sessions.</span></span> <span data-ttu-id="f33ad-245">如果不指定 **-ID**值，则必须用 **-s**指定会话名。</span><span class="sxs-lookup"><span data-stu-id="f33ad-245">If you do not specify a value for **-ID**, then a session name must be specified with **-s**.</span></span>  
  
 <span data-ttu-id="f33ad-246">**-ip**</span><span class="sxs-lookup"><span data-stu-id="f33ad-246">**-ip**</span></span>  
 <span data-ttu-id="f33ad-247">指定计划高速缓存可用作工作负荷。</span><span class="sxs-lookup"><span data-stu-id="f33ad-247">Specifies that the plan cache be used as the workload.</span></span> <span data-ttu-id="f33ad-248">分析显式选择的数据库的前 1000 个计划缓存事件。</span><span class="sxs-lookup"><span data-stu-id="f33ad-248">The top 1,000 plan cache events for explicitly selected databases are analyzed.</span></span> <span data-ttu-id="f33ad-249">可使用 -n  选项更改此值。</span><span class="sxs-lookup"><span data-stu-id="f33ad-249">This value can be changed using the **-n** option.</span></span>  
  
 <span data-ttu-id="f33ad-250">**-ipf**</span><span class="sxs-lookup"><span data-stu-id="f33ad-250">**-ipf**</span></span>  
 <span data-ttu-id="f33ad-251">指定计划高速缓存可用作工作负荷。</span><span class="sxs-lookup"><span data-stu-id="f33ad-251">Specifies that the plan cache be used as the workload.</span></span> <span data-ttu-id="f33ad-252">分析所有数据库的前 1000 个计划缓存事件。</span><span class="sxs-lookup"><span data-stu-id="f33ad-252">The top 1,000 plan cache events for all databases are analyzed.</span></span> <span data-ttu-id="f33ad-253">可使用 -n  选项更改此值。</span><span class="sxs-lookup"><span data-stu-id="f33ad-253">This value can be changed using the **-n** option.</span></span>  
  
 <span data-ttu-id="f33ad-254">**-if** _workload_file_</span><span class="sxs-lookup"><span data-stu-id="f33ad-254">**-if** _workload_file_</span></span>  
 <span data-ttu-id="f33ad-255">指定用作优化输入的工作负荷文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="f33ad-255">Specifies the path and name of the workload file to use as input for tuning.</span></span> <span data-ttu-id="f33ad-256">该文件必须采用下列格式之一：.trc（SQL Server Profiler 跟踪文件）、.sql（SQL 文件）或 .log（[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 跟踪文件）。</span><span class="sxs-lookup"><span data-stu-id="f33ad-256">The file must be in one of these formats: .trc (SQL Server Profiler trace file), .sql (SQL file), or .log ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trace file).</span></span> <span data-ttu-id="f33ad-257">必须指定一个工作负荷文件或一个工作负荷表。</span><span class="sxs-lookup"><span data-stu-id="f33ad-257">Either one workload file or one workload table must be specified.</span></span>  
  
 <span data-ttu-id="f33ad-258">**-it** _workload_trace_table_name_</span><span class="sxs-lookup"><span data-stu-id="f33ad-258">**-it** _workload_trace_table_name_</span></span>  
 <span data-ttu-id="f33ad-259">指定包含用于优化的工作负荷跟踪的表名。</span><span class="sxs-lookup"><span data-stu-id="f33ad-259">Specifies the name of a table containing the workload trace for tuning.</span></span> <span data-ttu-id="f33ad-260">如果使用表，则用以下格式指定其名称：[*database_name*] **.** [*owner_name*] **.** _table_name_。</span><span class="sxs-lookup"><span data-stu-id="f33ad-260">The name is specified in the format: [*database_name*]**.**[*owner_name*]**.**_table_name_.</span></span>  
  
 <span data-ttu-id="f33ad-261">下表显示了每个参数的默认值：</span><span class="sxs-lookup"><span data-stu-id="f33ad-261">The following table shows the default values for each:</span></span>  
  
|<span data-ttu-id="f33ad-262">参数</span><span class="sxs-lookup"><span data-stu-id="f33ad-262">Parameter</span></span>|<span data-ttu-id="f33ad-263">默认值</span><span class="sxs-lookup"><span data-stu-id="f33ad-263">Default value</span></span>|  
|---------------|-------------------|  
|<span data-ttu-id="f33ad-264">*database_name*</span><span class="sxs-lookup"><span data-stu-id="f33ad-264">*database_name*</span></span>|<span data-ttu-id="f33ad-265">使用 -D  选项指定的 database_name </span><span class="sxs-lookup"><span data-stu-id="f33ad-265">*database_name* specified with **-D** option.</span></span>|  
|<span data-ttu-id="f33ad-266">*owner_name*</span><span class="sxs-lookup"><span data-stu-id="f33ad-266">*owner_name*</span></span>|<span data-ttu-id="f33ad-267">**dbo**。</span><span class="sxs-lookup"><span data-stu-id="f33ad-267">**dbo**.</span></span>|  
|<span data-ttu-id="f33ad-268">*table_name*</span><span class="sxs-lookup"><span data-stu-id="f33ad-268">*table_name*</span></span>|<span data-ttu-id="f33ad-269">无。</span><span class="sxs-lookup"><span data-stu-id="f33ad-269">None.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="f33ad-270">*owner_name* 必须为 **dbo**。</span><span class="sxs-lookup"><span data-stu-id="f33ad-270">*owner_name* must be **dbo**.</span></span> <span data-ttu-id="f33ad-271">如果指定了其他任何值，则 **dta** 执行将失败并返回错误。</span><span class="sxs-lookup"><span data-stu-id="f33ad-271">If any other value is specified, execution of **dta** fails and an error is returned.</span></span> <span data-ttu-id="f33ad-272">另请注意，必须指定一个工作负荷表或一个工作负荷文件。</span><span class="sxs-lookup"><span data-stu-id="f33ad-272">Also note that either one workload table or one workload file must be specified.</span></span>  
  
 <span data-ttu-id="f33ad-273">**-ix** _input_XML_file_name_</span><span class="sxs-lookup"><span data-stu-id="f33ad-273">**-ix** _input_XML_file_name_</span></span>  
 <span data-ttu-id="f33ad-274">指定包含 **dta** 输入信息的 XML 文件的名称。</span><span class="sxs-lookup"><span data-stu-id="f33ad-274">Specifies the name of the XML file containing **dta** input information.</span></span> <span data-ttu-id="f33ad-275">该文件必须是符合 DTASchema.xsd 的有效 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="f33ad-275">This must be a valid XML document conforming to DTASchema.xsd.</span></span> <span data-ttu-id="f33ad-276">在命令提示符中指定的优化选项参数将覆盖与其冲突的此 XML 文件中的相应值。</span><span class="sxs-lookup"><span data-stu-id="f33ad-276">Conflicting arguments specified from the command prompt for tuning options override the corresponding value in this XML file.</span></span> <span data-ttu-id="f33ad-277">唯一的例外情况是：在计算模式下，在 XML 输入文件中输入用户指定的配置。</span><span class="sxs-lookup"><span data-stu-id="f33ad-277">The only exception is if a user-specified configuration is entered in the evaluate mode in the XML input file.</span></span> <span data-ttu-id="f33ad-278">例如，如果在 XML 输入文件的 **Configuration** 元素中输入了配置，并将 **EvaluateConfiguration** 元素指定为优化选项之一，则 XML 输入文件中指定的优化选项将覆盖命令提示符中输入的任何优化选项。</span><span class="sxs-lookup"><span data-stu-id="f33ad-278">For example, if a configuration is entered in the **Configuration** element of the XML input file and the **EvaluateConfiguration** element is also specified as one of the tuning options, the tuning options specified in the XML input file will override any tuning options entered from the command prompt.</span></span>  
  
 <span data-ttu-id="f33ad-279">**-m** _minimum_improvement_</span><span class="sxs-lookup"><span data-stu-id="f33ad-279">**-m** _minimum_improvement_</span></span>  
 <span data-ttu-id="f33ad-280">指定推荐的配置必须满足的最小改进百分比。</span><span class="sxs-lookup"><span data-stu-id="f33ad-280">Specifies the minimum percentage of improvement that the recommended configuration must satisfy.</span></span>  
  
 <span data-ttu-id="f33ad-281">**-N** _online_option_</span><span class="sxs-lookup"><span data-stu-id="f33ad-281">**-N** _online_option_</span></span>  
 <span data-ttu-id="f33ad-282">指定是否联机创建物理设计结构。</span><span class="sxs-lookup"><span data-stu-id="f33ad-282">Specifies whether physical design structures are created online.</span></span> <span data-ttu-id="f33ad-283">下表列出并说明了可为此参数指定的值：</span><span class="sxs-lookup"><span data-stu-id="f33ad-283">The following table lists and describes the values you can specify for this argument:</span></span>  
  
|<span data-ttu-id="f33ad-284">值</span><span class="sxs-lookup"><span data-stu-id="f33ad-284">Value</span></span>|<span data-ttu-id="f33ad-285">说明</span><span class="sxs-lookup"><span data-stu-id="f33ad-285">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f33ad-286">OFF</span><span class="sxs-lookup"><span data-stu-id="f33ad-286">OFF</span></span>|<span data-ttu-id="f33ad-287">建议的物理设计结构都无法联机创建。</span><span class="sxs-lookup"><span data-stu-id="f33ad-287">No recommended physical design structures can be created online.</span></span>|  
|<span data-ttu-id="f33ad-288">ON</span><span class="sxs-lookup"><span data-stu-id="f33ad-288">ON</span></span>|<span data-ttu-id="f33ad-289">所有建议的物理设计结构都可以联机创建。</span><span class="sxs-lookup"><span data-stu-id="f33ad-289">All recommended physical design structures can be created online.</span></span>|  
|<span data-ttu-id="f33ad-290">MIXED</span><span class="sxs-lookup"><span data-stu-id="f33ad-290">MIXED</span></span>|<span data-ttu-id="f33ad-291">数据库引擎优化顾问会尝试建议可以联机创建的物理设计结构。</span><span class="sxs-lookup"><span data-stu-id="f33ad-291">Database Engine Tuning Advisor attempts to recommend physical design structures that can be created online when possible.</span></span>|  
  
 <span data-ttu-id="f33ad-292">如果索引是联机创建的，则在其对象定义中追加 ONLINE = ON。</span><span class="sxs-lookup"><span data-stu-id="f33ad-292">If indexes are created online, ONLINE = ON is appended to its object definition.</span></span>  
  
 <span data-ttu-id="f33ad-293">**-n** _number_of_events_</span><span class="sxs-lookup"><span data-stu-id="f33ad-293">**-n** _number_of_events_</span></span>  
 <span data-ttu-id="f33ad-294">指定 **dta** 应在工作负荷中优化的事件数。</span><span class="sxs-lookup"><span data-stu-id="f33ad-294">Specifies the number of events in the workload that **dta** should tune.</span></span> <span data-ttu-id="f33ad-295">如果指定此参数，并且工作负荷是包含持续时间信息的跟踪文件，则 **dta** 将按持续时间的降序优化事件。</span><span class="sxs-lookup"><span data-stu-id="f33ad-295">If this argument is specified and the workload is a trace file that contains duration information, then **dta** tunes events in decreasing order of duration.</span></span> <span data-ttu-id="f33ad-296">此参数可用于比较物理设计结构的两个配置。</span><span class="sxs-lookup"><span data-stu-id="f33ad-296">This argument is useful to compare two configurations of physical design structures.</span></span> <span data-ttu-id="f33ad-297">若要比较两个配置，请为这两个配置指定相同的要优化的事件数，再为这两个配置指定不受限制的优化时间。如下所示：</span><span class="sxs-lookup"><span data-stu-id="f33ad-297">To compare two configurations, specify the same number of events to be tuned for both configurations and then specify an unlimited tuning time for both also as follows:</span></span>  
  
```  
dta -n number_of_events -A 0  
```  
  
 <span data-ttu-id="f33ad-298">在此示例中，必须指定不受限制的优化时间 (`-A 0`)。</span><span class="sxs-lookup"><span data-stu-id="f33ad-298">In this case, it is important to specify an unlimited tuning time (`-A 0`).</span></span> <span data-ttu-id="f33ad-299">否则，数据库引擎优化顾问将采用默认的 8 小时优化时间。</span><span class="sxs-lookup"><span data-stu-id="f33ad-299">Otherwise, Database Engine Tuning Advisor assumes an 8 hour tuning time by default.</span></span>  
  
 <span data-ttu-id="f33ad-300">**-of** _output_script_file_name_</span><span class="sxs-lookup"><span data-stu-id="f33ad-300">**-of** _output_script_file_name_</span></span>  
 <span data-ttu-id="f33ad-301">指定 **dta** 使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本将建议写入指定的文件名和目标。</span><span class="sxs-lookup"><span data-stu-id="f33ad-301">Specifies that **dta** writes the recommendation as a [!INCLUDE[tsql](../../includes/tsql-md.md)] script to the file name and destination specified.</span></span>  
  
 <span data-ttu-id="f33ad-302">可以将 **-F** 与此选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="f33ad-302">You can use **-F** with this option.</span></span> <span data-ttu-id="f33ad-303">请确保文件名是唯一的，尤其在使用了 **-or** 和 **-ox**时更应注意。</span><span class="sxs-lookup"><span data-stu-id="f33ad-303">Make sure that the file name is unique, especially if you are also using **-or** and **-ox**.</span></span>  
  
 <span data-ttu-id="f33ad-304">**-or** _output_xml_report_file_name_</span><span class="sxs-lookup"><span data-stu-id="f33ad-304">**-or** _output_xml_report_file_name_</span></span>  
 <span data-ttu-id="f33ad-305">指定 **dta** 使用 XML 将建议写入输出报告。</span><span class="sxs-lookup"><span data-stu-id="f33ad-305">Specifies that **dta** writes the recommendation to an output report in XML.</span></span> <span data-ttu-id="f33ad-306">如果提供了文件名，建议就会被写入该文件名。</span><span class="sxs-lookup"><span data-stu-id="f33ad-306">If a file name is supplied, then the recommendations are written to that destination.</span></span> <span data-ttu-id="f33ad-307">否则， **dta** 将使用会话名生成文件名，并将该文件名写入当前目录。</span><span class="sxs-lookup"><span data-stu-id="f33ad-307">Otherwise, **dta** uses the session name to generate the file name and writes it to the current directory.</span></span>  
  
 <span data-ttu-id="f33ad-308">可以将 **-F** 与此选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="f33ad-308">You can use **-F** with this option.</span></span> <span data-ttu-id="f33ad-309">请确保文件名是唯一的，尤其在使用了 **-of** 和 **-ox**时更应注意。</span><span class="sxs-lookup"><span data-stu-id="f33ad-309">Make sure that the file name is unique, especially if you are also using **-of** and **-ox**.</span></span>  
  
 <span data-ttu-id="f33ad-310">**-ox** _output_XML_file_name_</span><span class="sxs-lookup"><span data-stu-id="f33ad-310">**-ox** _output_XML_file_name_</span></span>  
 <span data-ttu-id="f33ad-311">指定 **dta** 使用 XML 文件将建议写入指定的文件名和目标。</span><span class="sxs-lookup"><span data-stu-id="f33ad-311">Specifies that **dta** writes the recommendation as an XML file to the file name and destination supplied.</span></span> <span data-ttu-id="f33ad-312">请确保数据库引擎优化顾问有写入目标目录的权限。</span><span class="sxs-lookup"><span data-stu-id="f33ad-312">Ensure that Database Engine Tuning Advisor has permissions to write to the destination directory.</span></span>  
  
 <span data-ttu-id="f33ad-313">可以将 **-F** 与此选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="f33ad-313">You can use **-F** with this option.</span></span> <span data-ttu-id="f33ad-314">请确保文件名是唯一的，尤其在使用了 **-of** 和 **-or**时更应注意。</span><span class="sxs-lookup"><span data-stu-id="f33ad-314">Make sure that the file name is unique, especially if you are also using **-of** and **-or**.</span></span>  
  
 <span data-ttu-id="f33ad-315">**-P** _password_</span><span class="sxs-lookup"><span data-stu-id="f33ad-315">**-P** _password_</span></span>  
 <span data-ttu-id="f33ad-316">指定登录 ID 的密码。</span><span class="sxs-lookup"><span data-stu-id="f33ad-316">Specifies the password for the login ID.</span></span> <span data-ttu-id="f33ad-317">如果未使用此选项， **dta** 将提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="f33ad-317">If this option is not used, **dta** prompts for a password.</span></span>  
  
 <span data-ttu-id="f33ad-318">**-q**</span><span class="sxs-lookup"><span data-stu-id="f33ad-318">**-q**</span></span>  
 <span data-ttu-id="f33ad-319">设置静默模式。</span><span class="sxs-lookup"><span data-stu-id="f33ad-319">Sets quiet mode.</span></span> <span data-ttu-id="f33ad-320">不向控制台写入信息，其中包括进度和标题信息。</span><span class="sxs-lookup"><span data-stu-id="f33ad-320">No information is written to the console, including progress and header information.</span></span>  
  
 <span data-ttu-id="f33ad-321">**-rl** _analysis_report_list_</span><span class="sxs-lookup"><span data-stu-id="f33ad-321">**-rl** _analysis_report_list_</span></span>  
 <span data-ttu-id="f33ad-322">指定要生成的分析报告列表。</span><span class="sxs-lookup"><span data-stu-id="f33ad-322">Specifies the list of analysis reports to generate.</span></span> <span data-ttu-id="f33ad-323">下表列出并说明了可为此参数指定的值：</span><span class="sxs-lookup"><span data-stu-id="f33ad-323">The following table lists the values that can be specified for this argument:</span></span>  
  
|<span data-ttu-id="f33ad-324">值</span><span class="sxs-lookup"><span data-stu-id="f33ad-324">Value</span></span>|<span data-ttu-id="f33ad-325">报表</span><span class="sxs-lookup"><span data-stu-id="f33ad-325">Report</span></span>|  
|-----------|------------|  
|<span data-ttu-id="f33ad-326">ALL</span><span class="sxs-lookup"><span data-stu-id="f33ad-326">ALL</span></span>|<span data-ttu-id="f33ad-327">所有分析报告</span><span class="sxs-lookup"><span data-stu-id="f33ad-327">All analysis reports</span></span>|  
|<span data-ttu-id="f33ad-328">STMT_COST</span><span class="sxs-lookup"><span data-stu-id="f33ad-328">STMT_COST</span></span>|<span data-ttu-id="f33ad-329">语句开销报告</span><span class="sxs-lookup"><span data-stu-id="f33ad-329">Statement cost report</span></span>|  
|<span data-ttu-id="f33ad-330">EVT_FREQ</span><span class="sxs-lookup"><span data-stu-id="f33ad-330">EVT_FREQ</span></span>|<span data-ttu-id="f33ad-331">事件频率报告</span><span class="sxs-lookup"><span data-stu-id="f33ad-331">Event frequency report</span></span>|  
|<span data-ttu-id="f33ad-332">STMT_DET</span><span class="sxs-lookup"><span data-stu-id="f33ad-332">STMT_DET</span></span>|<span data-ttu-id="f33ad-333">语句详细报告</span><span class="sxs-lookup"><span data-stu-id="f33ad-333">Statement detail report</span></span>|  
|<span data-ttu-id="f33ad-334">CUR_STMT_IDX</span><span class="sxs-lookup"><span data-stu-id="f33ad-334">CUR_STMT_IDX</span></span>|<span data-ttu-id="f33ad-335">语句-索引关系报告（当前配置）</span><span class="sxs-lookup"><span data-stu-id="f33ad-335">Statement-index relations report (current configuration)</span></span>|  
|<span data-ttu-id="f33ad-336">REC_STMT_IDX</span><span class="sxs-lookup"><span data-stu-id="f33ad-336">REC_STMT_IDX</span></span>|<span data-ttu-id="f33ad-337">语句-索引关系报告（建议配置）</span><span class="sxs-lookup"><span data-stu-id="f33ad-337">Statement-index relations report (recommended configuration)</span></span>|  
|<span data-ttu-id="f33ad-338">STMT_COSTRANGE</span><span class="sxs-lookup"><span data-stu-id="f33ad-338">STMT_COSTRANGE</span></span>|<span data-ttu-id="f33ad-339">语句开销范围报告</span><span class="sxs-lookup"><span data-stu-id="f33ad-339">Statement cost range report</span></span>|  
|<span data-ttu-id="f33ad-340">CUR_IDX_USAGE</span><span class="sxs-lookup"><span data-stu-id="f33ad-340">CUR_IDX_USAGE</span></span>|<span data-ttu-id="f33ad-341">索引使用报告（当前配置）</span><span class="sxs-lookup"><span data-stu-id="f33ad-341">Index usage report (current configuration)</span></span>|  
|<span data-ttu-id="f33ad-342">REC_IDX_USAGE</span><span class="sxs-lookup"><span data-stu-id="f33ad-342">REC_IDX_USAGE</span></span>|<span data-ttu-id="f33ad-343">索引使用报告（建议配置）</span><span class="sxs-lookup"><span data-stu-id="f33ad-343">Index usage report (recommended configuration)</span></span>|  
|<span data-ttu-id="f33ad-344">CUR_IDX_DET</span><span class="sxs-lookup"><span data-stu-id="f33ad-344">CUR_IDX_DET</span></span>|<span data-ttu-id="f33ad-345">索引详细报告（当前配置）</span><span class="sxs-lookup"><span data-stu-id="f33ad-345">Index detail report (current configuration)</span></span>|  
|<span data-ttu-id="f33ad-346">REC_IDX_DET</span><span class="sxs-lookup"><span data-stu-id="f33ad-346">REC_IDX_DET</span></span>|<span data-ttu-id="f33ad-347">索引详细报告（建议配置）</span><span class="sxs-lookup"><span data-stu-id="f33ad-347">Index detail report (recommended configuration)</span></span>|  
|<span data-ttu-id="f33ad-348">VIW_TAB</span><span class="sxs-lookup"><span data-stu-id="f33ad-348">VIW_TAB</span></span>|<span data-ttu-id="f33ad-349">视图-表关系报告</span><span class="sxs-lookup"><span data-stu-id="f33ad-349">View-table relations report</span></span>|  
|<span data-ttu-id="f33ad-350">WKLD_ANL</span><span class="sxs-lookup"><span data-stu-id="f33ad-350">WKLD_ANL</span></span>|<span data-ttu-id="f33ad-351">工作负荷分析报告</span><span class="sxs-lookup"><span data-stu-id="f33ad-351">Workload analysis report</span></span>|  
|<span data-ttu-id="f33ad-352">DB_ACCESS</span><span class="sxs-lookup"><span data-stu-id="f33ad-352">DB_ACCESS</span></span>|<span data-ttu-id="f33ad-353">数据库访问报告</span><span class="sxs-lookup"><span data-stu-id="f33ad-353">Database access report</span></span>|  
|<span data-ttu-id="f33ad-354">TAB_ACCESS</span><span class="sxs-lookup"><span data-stu-id="f33ad-354">TAB_ACCESS</span></span>|<span data-ttu-id="f33ad-355">表访问报告</span><span class="sxs-lookup"><span data-stu-id="f33ad-355">Table access report</span></span>|  
|<span data-ttu-id="f33ad-356">COL_ACCESS</span><span class="sxs-lookup"><span data-stu-id="f33ad-356">COL_ACCESS</span></span>|<span data-ttu-id="f33ad-357">列访问报告</span><span class="sxs-lookup"><span data-stu-id="f33ad-357">Column access report</span></span>|  
  
 <span data-ttu-id="f33ad-358">指定多个报告时，用逗号分隔各个值。例如：</span><span class="sxs-lookup"><span data-stu-id="f33ad-358">Specify multiple reports by separating the values with commas, for example:</span></span>  
  
```  
... -rl EVT_FREQ, VIW_TAB, WKLD_ANL ...  
```  
  
 <span data-ttu-id="f33ad-359">**-S** _server_name_[ *\instance*]</span><span class="sxs-lookup"><span data-stu-id="f33ad-359">**-S** _server_name_[ *\instance*]</span></span>  
 <span data-ttu-id="f33ad-360">指定要连接到的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 计算机和实例的名称。</span><span class="sxs-lookup"><span data-stu-id="f33ad-360">Specifies the name of the computer and instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to connect to.</span></span> <span data-ttu-id="f33ad-361">如果未指定 *server_name* ，则 **dta** 将连接到本地计算机上的默认 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="f33ad-361">If no *server_name* is specified, **dta** connects to the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="f33ad-362">如果连接到命名实例或从网络中的远程计算机执行 **dta** ，则必须使用此选项。</span><span class="sxs-lookup"><span data-stu-id="f33ad-362">This option is required when connecting to a named instance or when executing **dta** from a remote computer on the network.</span></span>  
  
 <span data-ttu-id="f33ad-363">**-s** _session_name_</span><span class="sxs-lookup"><span data-stu-id="f33ad-363">**-s** _session_name_</span></span>  
 <span data-ttu-id="f33ad-364">指定优化会话的名称。</span><span class="sxs-lookup"><span data-stu-id="f33ad-364">Specifies the name of the tuning session.</span></span> <span data-ttu-id="f33ad-365">如果未指定 **-ID** ，则必须使用此选项。</span><span class="sxs-lookup"><span data-stu-id="f33ad-365">This is required if **-ID** is not specified.</span></span>  
  
 <span data-ttu-id="f33ad-366">**-Tf** _table_list_file_</span><span class="sxs-lookup"><span data-stu-id="f33ad-366">**-Tf** _table_list_file_</span></span>  
 <span data-ttu-id="f33ad-367">指定包含要优化的一组表的文件名。</span><span class="sxs-lookup"><span data-stu-id="f33ad-367">Specifies the name of a file containing a list of tables to be tuned.</span></span> <span data-ttu-id="f33ad-368">文件中列出的每个表应另起一行。</span><span class="sxs-lookup"><span data-stu-id="f33ad-368">Each table listed within the file should begin on a new line.</span></span> <span data-ttu-id="f33ad-369">表名的命名应限定为三个部分，例如， **AdventureWorks2012.HumanResources.Department**。</span><span class="sxs-lookup"><span data-stu-id="f33ad-369">Table names should be qualified with three-part naming, for example, **AdventureWorks2012.HumanResources.Department**.</span></span> <span data-ttu-id="f33ad-370">为了调用表的扩展功能，可以选择在现有表名后加上一个数字，指示表中的预定行数。</span><span class="sxs-lookup"><span data-stu-id="f33ad-370">Optionally, to invoke the table-scaling feature, the name of an existing table can be followed by a number indicating the projected number of rows in the table.</span></span> <span data-ttu-id="f33ad-371">数据库引擎优化顾问在优化或评估引用这些表的工作负荷中的语句时，将考虑这些预定行数。</span><span class="sxs-lookup"><span data-stu-id="f33ad-371">Database Engine Tuning Advisor takes into consideration the projected number of rows while tuning or evaluating statements in the workload that reference these tables.</span></span> <span data-ttu-id="f33ad-372">请注意， *number_of_rows* 计数和 *table_name*之间可以有一个或多个空格。</span><span class="sxs-lookup"><span data-stu-id="f33ad-372">Note that there can be one or more spaces between the *number_of_rows* count and the *table_name*.</span></span>  
  
 <span data-ttu-id="f33ad-373">以下是 *table_list_file*的文件格式：</span><span class="sxs-lookup"><span data-stu-id="f33ad-373">This is the file format for *table_list_file*:</span></span>  
  
 <span data-ttu-id="f33ad-374">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span><span class="sxs-lookup"><span data-stu-id="f33ad-374">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span></span>  
  
 <span data-ttu-id="f33ad-375">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span><span class="sxs-lookup"><span data-stu-id="f33ad-375">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span></span>  
  
 <span data-ttu-id="f33ad-376">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span><span class="sxs-lookup"><span data-stu-id="f33ad-376">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span></span>  
  
 <span data-ttu-id="f33ad-377">此参数是在命令提示符中输入表列表 ( **-Tl**) 的替代方式。</span><span class="sxs-lookup"><span data-stu-id="f33ad-377">This argument is an alternative to entering a table list at the command prompt (**-Tl**).</span></span> <span data-ttu-id="f33ad-378">如果使用了 **-Tl**，请不要使用表列表文件 ( **-Tf**)。</span><span class="sxs-lookup"><span data-stu-id="f33ad-378">Do not use a table list file (**-Tf**) if you are using **-Tl**.</span></span> <span data-ttu-id="f33ad-379">如果同时使用这两个参数， **dta** 将失败并返回错误。</span><span class="sxs-lookup"><span data-stu-id="f33ad-379">If both arguments are used, **dta** fails and returns an error.</span></span>  
  
 <span data-ttu-id="f33ad-380">如果省略 **-Tf** 和 **-Tl** 参数，则将考虑对指定数据库中的所有用户表进行优化。</span><span class="sxs-lookup"><span data-stu-id="f33ad-380">If the **-Tf** and **-Tl** arguments are omitted, all user tables in the specified databases are considered for tuning.</span></span>  
  
 <span data-ttu-id="f33ad-381">**-Tl** _table_list_</span><span class="sxs-lookup"><span data-stu-id="f33ad-381">**-Tl** _table_list_</span></span>  
 <span data-ttu-id="f33ad-382">在命令提示符中指定要优化的一组表。</span><span class="sxs-lookup"><span data-stu-id="f33ad-382">Specifies at the command prompt a list of tables to be tuned.</span></span> <span data-ttu-id="f33ad-383">各表名间用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="f33ad-383">Place commas between table names to separate them.</span></span> <span data-ttu-id="f33ad-384">如果使用 **-D** 参数只指定一个数据库，则无需使用数据库名限定表名。</span><span class="sxs-lookup"><span data-stu-id="f33ad-384">If only one database is specified with the **-D** argument, then table names do not need to be qualified with a database name.</span></span> <span data-ttu-id="f33ad-385">在其他情况下，使用以下格式的完全限定名： *database_name.schema_name.table_name* ，每个表都必须使用此格式。</span><span class="sxs-lookup"><span data-stu-id="f33ad-385">Otherwise, the fully qualified name in the format: *database_name.schema_name.table_name* is required for each table.</span></span>  
  
 <span data-ttu-id="f33ad-386">此参数是使用表列表文件 ( **-Tf**) 的替代方法。</span><span class="sxs-lookup"><span data-stu-id="f33ad-386">This argument is an alternative to using a table list file (**-Tf**).</span></span> <span data-ttu-id="f33ad-387">如果同时使用 **-Tl** 和 **-Tf** ，则 **dta** 将失败并返回错误。</span><span class="sxs-lookup"><span data-stu-id="f33ad-387">If both **-Tl** and **-Tf** are used, **dta** fails and returns an error.</span></span>  
  
 <span data-ttu-id="f33ad-388">**-U** _login_id_</span><span class="sxs-lookup"><span data-stu-id="f33ad-388">**-U** _login_id_</span></span>  
 <span data-ttu-id="f33ad-389">指定用于连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的登录 ID。</span><span class="sxs-lookup"><span data-stu-id="f33ad-389">Specifies the login ID used to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f33ad-390">**-u**</span><span class="sxs-lookup"><span data-stu-id="f33ad-390">**-u**</span></span>  
 <span data-ttu-id="f33ad-391">启动数据库引擎优化顾问 GUI。</span><span class="sxs-lookup"><span data-stu-id="f33ad-391">Launches the Database Engine Tuning Advisor GUI.</span></span> <span data-ttu-id="f33ad-392">所有参数均被视为用户界面的初始设置。</span><span class="sxs-lookup"><span data-stu-id="f33ad-392">All parameters are treated as the initial settings for the user interface.</span></span>  
  
 <span data-ttu-id="f33ad-393">**-x**</span><span class="sxs-lookup"><span data-stu-id="f33ad-393">**-x**</span></span>  
 <span data-ttu-id="f33ad-394">启动优化会话，然后退出。</span><span class="sxs-lookup"><span data-stu-id="f33ad-394">Starts tuning session and exits.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f33ad-395">备注</span><span class="sxs-lookup"><span data-stu-id="f33ad-395">Remarks</span></span>  
 <span data-ttu-id="f33ad-396">按 Ctrl+C 一次可停止优化会话，并可根据 **dta** 此时已完成的分析生成建议。</span><span class="sxs-lookup"><span data-stu-id="f33ad-396">Press CTRL+C once to stop the tuning session and generate recommendations based on the analysis **dta** has completed up to this point.</span></span> <span data-ttu-id="f33ad-397">系统将提示您确定是否要生成建议。</span><span class="sxs-lookup"><span data-stu-id="f33ad-397">You will be prompted to decide whether you want to generate recommendations or not.</span></span> <span data-ttu-id="f33ad-398">再次按 Ctrl+C 停止优化会话，而不生成建议。</span><span class="sxs-lookup"><span data-stu-id="f33ad-398">Press CTRL+C again to stop the tuning session without generating recommendations.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f33ad-399">示例</span><span class="sxs-lookup"><span data-stu-id="f33ad-399">Examples</span></span>  
 <span data-ttu-id="f33ad-400">**A.优化在其建议中包含索引和索引视图的工作负荷**</span><span class="sxs-lookup"><span data-stu-id="f33ad-400">**A. Tune a workload that includes indexes and indexed views in its recommendation**</span></span>  
  
 <span data-ttu-id="f33ad-401">此示例使用安全连接 (`-E`) 连接到 MyServer 中的 **tpcd1G** 数据库，以分析工作负荷并创建建议。</span><span class="sxs-lookup"><span data-stu-id="f33ad-401">This example uses a secure connection (`-E`) to connect to the **tpcd1G** database on MyServer to analyze a workload and create recommendations.</span></span> <span data-ttu-id="f33ad-402">此示例将输出写入到名为 script.sql 的脚本文件。</span><span class="sxs-lookup"><span data-stu-id="f33ad-402">It writes the output to a script file named script.sql.</span></span> <span data-ttu-id="f33ad-403">如果 script.sql 已存在，由于指定了 **参数，** dta `-F` 将覆盖该文件。</span><span class="sxs-lookup"><span data-stu-id="f33ad-403">If script.sql already exists, then **dta** will overwrite the file because the `-F` argument has been specified.</span></span> <span data-ttu-id="f33ad-404">优化会话的运行时间没有限制，以确保完成工作负荷分析 (`-A 0`)。</span><span class="sxs-lookup"><span data-stu-id="f33ad-404">The tuning session runs for an unlimited length of time to ensure a complete analysis of the workload (`-A 0`).</span></span> <span data-ttu-id="f33ad-405">建议必须至少提供 5% 的改进 (`-m 5`)。</span><span class="sxs-lookup"><span data-stu-id="f33ad-405">The recommendation must provide a minimum improvement of 5% (`-m 5`).</span></span> <span data-ttu-id="f33ad-406">**dta** 应在其最终建议中包含索引和索引视图 (`-fa IDX_IV`)。</span><span class="sxs-lookup"><span data-stu-id="f33ad-406">**dta** should include indexes and indexed views in its final recommendation (`-fa IDX_IV`).</span></span>  
  
```  
dta -S MyServer -E -D tpcd1G -if tpcd_22.sql -F -of script.sql -A 0 -m 5 -fa IDX_IV  
```  
  
 <span data-ttu-id="f33ad-407">**B.限制磁盘使用**</span><span class="sxs-lookup"><span data-stu-id="f33ad-407">**B. Limit disk use**</span></span>  
  
 <span data-ttu-id="f33ad-408">此示例将数据库总大小（包括原始数据和其他索引）限定为 3 GB (`-B 3000`)，并将输出定向到 d:\result_dir\script1.sql。</span><span class="sxs-lookup"><span data-stu-id="f33ad-408">This example limits the total database size, which includes the raw data and the additional indexes, to 3 gigabytes (GB) (`-B 3000`) and directs the output to d:\result_dir\script1.sql.</span></span> <span data-ttu-id="f33ad-409">该示例的运行时间不会超过 1 小时 (`-A 60`)。</span><span class="sxs-lookup"><span data-stu-id="f33ad-409">It runs for no more than 1 hour (`-A 60`).</span></span>  
  
```  
dta -D tpcd1G -if tpcd_22.sql -B 3000 -of "d:\result_dir\script1.sql" -A 60  
```  
  
 <span data-ttu-id="f33ad-410">**C.限制优化查询的数量**</span><span class="sxs-lookup"><span data-stu-id="f33ad-410">**C. Limit the number of tuned queries**</span></span>  
  
 <span data-ttu-id="f33ad-411">此示例将从 orders_wkld.sql 文件读取的最大查询数限定为 10 (`-n 10`)，并将运行时间设为 15 分钟 (`-A 15`)，以先完成的为准。</span><span class="sxs-lookup"><span data-stu-id="f33ad-411">This example limits the number of queries read from the file orders_wkld.sql to a maximum of 10 (`-n 10`) and runs for 15 minutes (`-A 15`), whichever comes first.</span></span> <span data-ttu-id="f33ad-412">要确保所有 10 个查询都得到优化，请用 `-A 0` 指定不受限制的优化时间。</span><span class="sxs-lookup"><span data-stu-id="f33ad-412">To make sure that all 10 queries are tuned, specify an unlimited tuning time with `-A 0`.</span></span> <span data-ttu-id="f33ad-413">如果时间紧迫，则通过用 `-A` 参数指定用于优化的分钟数来指定适当的时间限制，如本例所示。</span><span class="sxs-lookup"><span data-stu-id="f33ad-413">If time is important, specify an appropriate time limit by specifying the number of minutes that are available for tuning with the `-A` argument as shown in this example.</span></span>  
  
```  
dta -D orders -if orders_wkld.sql -of script.sql -A 15 -n 10  
```  
  
 <span data-ttu-id="f33ad-414">**D.优化文件中列出的特定表**</span><span class="sxs-lookup"><span data-stu-id="f33ad-414">**D. Tune specific tables listed in a file**</span></span>  
  
 <span data-ttu-id="f33ad-415">该示例演示了 *table_list_file* （ **-Tf** 参数）的用法。</span><span class="sxs-lookup"><span data-stu-id="f33ad-415">This example demonstrates the use of *table_list_file* (the **-Tf** argument).</span></span> <span data-ttu-id="f33ad-416">table_list.txt 文件的内容如下所示：</span><span class="sxs-lookup"><span data-stu-id="f33ad-416">The contents of the file table_list.txt are as follows:</span></span>  
  
```  
AdventureWorks2012.Sales.Customer  100000  
AdventureWorks2012.Sales.Store  
AdventureWorks2012.Production.Product  2000000  
```  
  
 <span data-ttu-id="f33ad-417">table_list.txt 的内容指定：</span><span class="sxs-lookup"><span data-stu-id="f33ad-417">The contents of table_list.txt specifies that:</span></span>  
  
-   <span data-ttu-id="f33ad-418">应当仅优化数据库中的 **Customer**、 **Store**和 **Product** 表。</span><span class="sxs-lookup"><span data-stu-id="f33ad-418">Only the **Customer**, **Store**, and **Product** tables in the database should be tuned.</span></span>  
  
-   <span data-ttu-id="f33ad-419">**Customer** 和 **Product** 表中的行数分别假定为 100,000 和 2,000,000。</span><span class="sxs-lookup"><span data-stu-id="f33ad-419">The number of rows in the **Customer** and **Product** tables are assumed to be 100,000 and 2,000,000, respectively.</span></span>  
  
-   <span data-ttu-id="f33ad-420">**Store** 中的行数假定为表中的当前行数。</span><span class="sxs-lookup"><span data-stu-id="f33ad-420">The number of rows in **Store** are assumed to be the current number of rows in the table.</span></span>  
  
 <span data-ttu-id="f33ad-421">请注意， *table_list_file*中的行数计数和前面的表名间可以有一个或多个空格。</span><span class="sxs-lookup"><span data-stu-id="f33ad-421">Note that there can be one or more spaces between the number of rows count and the preceding table name in the *table_list_file*.</span></span>  
  
 <span data-ttu-id="f33ad-422">优化时间为 2 小时 (`-A 120`)，输出将写入 XML 文件 (`-ox XMLTune.xml`)。</span><span class="sxs-lookup"><span data-stu-id="f33ad-422">The tuning time is 2 hours (`-A 120`) and the output is written to an XML file (`-ox XMLTune.xml`).</span></span>  
  
```  
dta -D pubs -if pubs_wkld.sql -ox XMLTune.xml -A 120 -Tf table_list.txt  
```  
  
## <a name="see-also"></a><span data-ttu-id="f33ad-423">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f33ad-423">See Also</span></span>  
 <span data-ttu-id="f33ad-424">[命令提示实用工具引用 &#40;数据库引擎&#41;](../command-prompt-utility-reference-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="f33ad-424">[Command Prompt Utility Reference &#40;Database Engine&#41;](../command-prompt-utility-reference-database-engine.md) </span></span>  
 [<span data-ttu-id="f33ad-425">Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="f33ad-425">Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
