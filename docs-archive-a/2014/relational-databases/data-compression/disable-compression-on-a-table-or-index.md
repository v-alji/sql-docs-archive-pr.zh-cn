---
title: 对表或索引禁用压缩功能 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- data compression [SQL Server], disabling
ms.assetid: bda1e452-397b-4757-82a4-181217361589
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 80b5775d3b6f7a3f47ab75c5348b556c17b6e676
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589704"
---
# <a name="disable-compression-on-a-table-or-index"></a><span data-ttu-id="a3778-102">对表或索引禁用压缩功能</span><span class="sxs-lookup"><span data-stu-id="a3778-102">Disable Compression on a Table or Index</span></span>
  <span data-ttu-id="a3778-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中对表或索引禁用压缩功能。</span><span class="sxs-lookup"><span data-stu-id="a3778-103">This topic describes how to disable compression on a table or index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="a3778-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="a3778-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a3778-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="a3778-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a3778-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="a3778-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a3778-107">安全性</span><span class="sxs-lookup"><span data-stu-id="a3778-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a3778-108">**若要对表或索引禁用压缩功能，可使用：**</span><span class="sxs-lookup"><span data-stu-id="a3778-108">**To disable compression on a table or index, using:**</span></span>  
  
     [<span data-ttu-id="a3778-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a3778-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a3778-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a3778-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a3778-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="a3778-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a3778-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="a3778-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="a3778-113">如果表是堆，ONLINE 模式的重新生成操作将在单个线程内完成。</span><span class="sxs-lookup"><span data-stu-id="a3778-113">If the table is a heap, the rebuild operation for ONLINE mode will be single threaded.</span></span> <span data-ttu-id="a3778-114">请为多线程堆重新生成操作使用 OFFLINE 模式。</span><span class="sxs-lookup"><span data-stu-id="a3778-114">Use OFFLINE mode for a multi-threaded heap rebuild operation.</span></span> <span data-ttu-id="a3778-115">有关数据压缩的详细信息，请参阅 [数据压缩](data-compression.md)。</span><span class="sxs-lookup"><span data-stu-id="a3778-115">For a more information about data compression, see [Data Compression](data-compression.md).</span></span>  
  
-   <span data-ttu-id="a3778-116">若要评估更改压缩状态将对表、索引或分区有何影响，请使用 [sp_estimate_data_compression_savings](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) 存储过程。</span><span class="sxs-lookup"><span data-stu-id="a3778-116">To evaluate how changing the compression state will affect a table, an index, or a partition, use the [sp_estimate_data_compression_savings](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) stored procedure.</span></span>  
  
-   <span data-ttu-id="a3778-117">如果表具有非对齐索引，则无法更改单个分区的压缩设置。</span><span class="sxs-lookup"><span data-stu-id="a3778-117">You cannot change the compression setting of a single partition if the table has nonaligned indexes.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a3778-118">Security</span><span class="sxs-lookup"><span data-stu-id="a3778-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a3778-119">权限</span><span class="sxs-lookup"><span data-stu-id="a3778-119">Permissions</span></span>  
 <span data-ttu-id="a3778-120">要求对表或索引具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="a3778-120">Requires ALTER permission on the table or index.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a3778-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a3778-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-compression-on-a-table"></a><span data-ttu-id="a3778-122">对表禁用压缩功能</span><span class="sxs-lookup"><span data-stu-id="a3778-122">To disable compression on a table</span></span>  
  
1.  <span data-ttu-id="a3778-123">在对象资源管理器中，展开包含要对其禁用压缩功能的表的数据库，然后展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="a3778-123">In Object Explorer, expand the database that contains the table on which you want to disable compression and then expand the **Tables** folder.</span></span>  
  
2.  <span data-ttu-id="a3778-124">右键单击要对其禁用压缩功能的表或索引，指向“存储”并选择“管理压缩…” 。</span><span class="sxs-lookup"><span data-stu-id="a3778-124">Right-click the table or index on which you want to disable compression, point to **Storage** and select **Manage Compression...**.</span></span>  
  
3.  <span data-ttu-id="a3778-125">若要对索引禁用压缩功能，请展开包含索引的表，然后展开 **“索引”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="a3778-125">To disable compression on an index, expand the table that contains the index and then expand the **Indexes** folder.</span></span>  
  
4.  <span data-ttu-id="a3778-126">在数据压缩向导中的 **“欢迎使用数据压缩向导”** 页上，单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="a3778-126">In the Data Compression Wizard, on the **Welcome to the Data Compression Wizard** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="a3778-127">在 **“选择压缩类型”** 页上，选择 **“无”** 作为要应用于要对其禁用压缩功能的索引中的每个分区的压缩类型。</span><span class="sxs-lookup"><span data-stu-id="a3778-127">On the **Select Compression Type** page, select **None** as the compression type to apply to each partition in the index on which you want to disable compression.</span></span> <span data-ttu-id="a3778-128">完成后，单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="a3778-128">When finished, click **Next**.</span></span>  
  
     <span data-ttu-id="a3778-129">**“选择压缩类型”** 页上提供了以下选项：</span><span class="sxs-lookup"><span data-stu-id="a3778-129">The following options are available on the **Select Compression Type** page:</span></span>  
  
     <span data-ttu-id="a3778-130">“对所有分区使用相同压缩类型”复选框</span><span class="sxs-lookup"><span data-stu-id="a3778-130">**Use the same compression type for all partitions** check box</span></span>  
     <span data-ttu-id="a3778-131">选择此选项将为所有分区配置相同的压缩设置。</span><span class="sxs-lookup"><span data-stu-id="a3778-131">Select to configure the same compression setting for all partitions.</span></span> <span data-ttu-id="a3778-132">此操作将启用选择框并禁用网格中的 **“压缩类型”** 列。</span><span class="sxs-lookup"><span data-stu-id="a3778-132">This enables the selection box and disables the **Compression Type** column in the grid.</span></span> <span data-ttu-id="a3778-133">选中此复选框后，相邻列表中的选项为 **“无”** 、 **“Row”** 和 **“Page”** 。</span><span class="sxs-lookup"><span data-stu-id="a3778-133">When selected, the options in the adjacent list are **None**, **Row**, and **Page**.</span></span>  
  
     <span data-ttu-id="a3778-134">**分区号**</span><span class="sxs-lookup"><span data-stu-id="a3778-134">**Partition Number**</span></span>  
     <span data-ttu-id="a3778-135">列出表或索引中的每个分区。</span><span class="sxs-lookup"><span data-stu-id="a3778-135">Lists each partition in the table or index.</span></span> <span data-ttu-id="a3778-136">此列为只读。</span><span class="sxs-lookup"><span data-stu-id="a3778-136">This column is read-only.</span></span>  
  
     <span data-ttu-id="a3778-137">**“压缩类型”**</span><span class="sxs-lookup"><span data-stu-id="a3778-137">**Compression Type**</span></span>  
     <span data-ttu-id="a3778-138">为每个分区选择压缩选项。</span><span class="sxs-lookup"><span data-stu-id="a3778-138">Select the compression option for each partition.</span></span> <span data-ttu-id="a3778-139">在选中 **“对所有分区使用相同压缩类型”** 的情况下此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="a3778-139">Is not available when **Use the same compression type for all partitions** is selected.</span></span> <span data-ttu-id="a3778-140">列表选项为 **“无”** 、 **“Row”** 和 **“Page”** 。</span><span class="sxs-lookup"><span data-stu-id="a3778-140">List options are **None**, **Row**, and **Page**.</span></span>  
  
     <span data-ttu-id="a3778-141">**边界**</span><span class="sxs-lookup"><span data-stu-id="a3778-141">**Boundary**</span></span>  
     <span data-ttu-id="a3778-142">显示分区的边界。</span><span class="sxs-lookup"><span data-stu-id="a3778-142">Displays the partition boundary.</span></span> <span data-ttu-id="a3778-143">此列为只读。</span><span class="sxs-lookup"><span data-stu-id="a3778-143">This column is read-only.</span></span>  
  
     <span data-ttu-id="a3778-144">**行计数**</span><span class="sxs-lookup"><span data-stu-id="a3778-144">**Row Count**</span></span>  
     <span data-ttu-id="a3778-145">显示此分区中的行数。</span><span class="sxs-lookup"><span data-stu-id="a3778-145">Displays the number of rows in this partition.</span></span> <span data-ttu-id="a3778-146">此列为只读。</span><span class="sxs-lookup"><span data-stu-id="a3778-146">This column is read-only.</span></span>  
  
     <span data-ttu-id="a3778-147">**当前空间**</span><span class="sxs-lookup"><span data-stu-id="a3778-147">**Current Space**</span></span>  
     <span data-ttu-id="a3778-148">显示此分区当前所占的空间 (MB)。</span><span class="sxs-lookup"><span data-stu-id="a3778-148">Displays the current space this partition occupies in megabytes (MB).</span></span> <span data-ttu-id="a3778-149">此列为只读。</span><span class="sxs-lookup"><span data-stu-id="a3778-149">This column is read-only.</span></span>  
  
     <span data-ttu-id="a3778-150">**请求的压缩空间**</span><span class="sxs-lookup"><span data-stu-id="a3778-150">**Requested Compressed Space**</span></span>  
     <span data-ttu-id="a3778-151">单击“计算”之后，此列将显示在使用“压缩类型”列中指定的设置进行压缩后每个分区的估计大小。</span><span class="sxs-lookup"><span data-stu-id="a3778-151">After you click **Calculate**, this column displays the estimated size of each partition after compression by using the setting specified in the **Compression Type** column.</span></span> <span data-ttu-id="a3778-152">此列为只读。</span><span class="sxs-lookup"><span data-stu-id="a3778-152">This column is read-only.</span></span>  
  
     <span data-ttu-id="a3778-153">**计算**</span><span class="sxs-lookup"><span data-stu-id="a3778-153">**Calculate**</span></span>  
     <span data-ttu-id="a3778-154">单击此项可估算每个分区在使用“压缩类型”列中指定的设置进行压缩之后的大小。</span><span class="sxs-lookup"><span data-stu-id="a3778-154">Click to estimate the size of each partition after compression by using the setting specified in the **Compression Type** column.</span></span>  
  
6.  <span data-ttu-id="a3778-155">在 **“选择输出选项”** 页上，指定要如何完成此任务。</span><span class="sxs-lookup"><span data-stu-id="a3778-155">In the **Select an Output Option** page, specify how you want to complete this task.</span></span> <span data-ttu-id="a3778-156">选择 **“创建脚本”** 可以基于向导中的前一页创建 SQL 脚本。</span><span class="sxs-lookup"><span data-stu-id="a3778-156">Select **Create Script** to create a SQL script based the previous pages in the wizard.</span></span> <span data-ttu-id="a3778-157">选择 **“立即运行”** 可以在完成向导中的其余页后创建新的已分区表。</span><span class="sxs-lookup"><span data-stu-id="a3778-157">Select **Run immediately** to create the new partitioned table after completing all remaining pages in the wizard.</span></span> <span data-ttu-id="a3778-158">选择 **“计划”** 可以在将来的预定时间创建新的已分区表。</span><span class="sxs-lookup"><span data-stu-id="a3778-158">Select **Schedule** to create the new partitioned table at a predetermined time in the future.</span></span>  
  
     <span data-ttu-id="a3778-159">如果选择 **“创建脚本”** ， **“脚本选项”** 下的以下选项将可用：</span><span class="sxs-lookup"><span data-stu-id="a3778-159">If you select **Create script**, the following options are available under **Script options**:</span></span>  
  
     <span data-ttu-id="a3778-160">**将脚本保存到文件**</span><span class="sxs-lookup"><span data-stu-id="a3778-160">**Script to file**</span></span>  
     <span data-ttu-id="a3778-161">将脚本生成为 .sql 文件。</span><span class="sxs-lookup"><span data-stu-id="a3778-161">Generates the script as a .sql file.</span></span> <span data-ttu-id="a3778-162">在 **“文件名”** 框中输入文件名和位置，或单击 **“浏览”** 以打开 **“脚本文件位置”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="a3778-162">Enter a file name and location in the **File name** box or click **Browse** to open the **Script File Location** dialog box.</span></span> <span data-ttu-id="a3778-163">从 **“另存为”** 选择 **“Unicode 文本”** 或 **“ANSI 文本”** 。</span><span class="sxs-lookup"><span data-stu-id="a3778-163">From **Save As**, select **Unicode text** or **ANSI text**.</span></span>  
  
     <span data-ttu-id="a3778-164">**将脚本保存到剪贴板**</span><span class="sxs-lookup"><span data-stu-id="a3778-164">**Script to Clipboard**</span></span>  
     <span data-ttu-id="a3778-165">将脚本保存到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="a3778-165">Saves the script to the Clipboard.</span></span>  
  
     <span data-ttu-id="a3778-166">**将脚本保存到“新建查询”窗口**</span><span class="sxs-lookup"><span data-stu-id="a3778-166">**Script to New Query Window**</span></span>  
     <span data-ttu-id="a3778-167">将脚本生成到新的查询编辑器窗口。</span><span class="sxs-lookup"><span data-stu-id="a3778-167">Generates the script to a new Query Editor window.</span></span> <span data-ttu-id="a3778-168">这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="a3778-168">This is the default selection.</span></span>  
  
     <span data-ttu-id="a3778-169">如果选择 **“计划”** ，则单击 **“更改计划”** 。</span><span class="sxs-lookup"><span data-stu-id="a3778-169">If you select **Schedule**, click **Change schedule**.</span></span>  
  
    1.  <span data-ttu-id="a3778-170">在“新建作业计划”对话框的“名称”框中，输入作业计划的名称 。</span><span class="sxs-lookup"><span data-stu-id="a3778-170">In the **New Job Schedule** dialog box, in the **Name** box, enter the job schedule's name.</span></span>  
  
    2.  <span data-ttu-id="a3778-171">在 **“计划类型”** 列表中选择计划类型：</span><span class="sxs-lookup"><span data-stu-id="a3778-171">On the **Schedule type** list, select the type of schedule:</span></span>  
  
        -   <span data-ttu-id="a3778-172">**SQL Server 代理启动时自动启动**</span><span class="sxs-lookup"><span data-stu-id="a3778-172">**Start automatically when SQL Server Agent starts**</span></span>  
  
        -   <span data-ttu-id="a3778-173">**CPU 空闲时启动**</span><span class="sxs-lookup"><span data-stu-id="a3778-173">**Start whenever the CPUs become idle**</span></span>  
  
        -   <span data-ttu-id="a3778-174">**重复执行**。</span><span class="sxs-lookup"><span data-stu-id="a3778-174">**Recurring**.</span></span> <span data-ttu-id="a3778-175">如果新的已分区表定期使用新信息更新，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="a3778-175">Select this option if your new partitioned table updates with new information on a regular basis.</span></span>  
  
        -   <span data-ttu-id="a3778-176">**执行一次**。</span><span class="sxs-lookup"><span data-stu-id="a3778-176">**One time**.</span></span> <span data-ttu-id="a3778-177">这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="a3778-177">This is the default selection.</span></span>  
  
    3.  <span data-ttu-id="a3778-178">选择或清除 **“已启用”** 复选框以启用或禁用计划。</span><span class="sxs-lookup"><span data-stu-id="a3778-178">Select or clear the **Enabled** check box to enable or disable the schedule.</span></span>  
  
    4.  <span data-ttu-id="a3778-179">如果选择 **“重复执行”** ：</span><span class="sxs-lookup"><span data-stu-id="a3778-179">If you select **Recurring**:</span></span>  
  
        1.  <span data-ttu-id="a3778-180">在 **“频率”** 下的 **“执行”** 列表中，指定执行的频率：</span><span class="sxs-lookup"><span data-stu-id="a3778-180">Under **Frequency**, on the **Occurs** list, specify the frequency of occurrence:</span></span>  
  
            -   <span data-ttu-id="a3778-181">如果选择 **“每天”** ，请在 **“执行间隔”** 框中输入重复作业计划的频率（天）。</span><span class="sxs-lookup"><span data-stu-id="a3778-181">If you select **Daily**, in the **Recurs every** box, enter how often the job schedule repeats in days.</span></span>  
  
            -   <span data-ttu-id="a3778-182">如果选择 **“每周”** ，请在 **“执行间隔”** 框中输入重复作业计划的频率（周）。</span><span class="sxs-lookup"><span data-stu-id="a3778-182">If you select **Weekly**, in the **Recurs every** box, enter how often the job schedule repeats in weeks.</span></span> <span data-ttu-id="a3778-183">选择运行作业计划的一周中的某天或某些天。</span><span class="sxs-lookup"><span data-stu-id="a3778-183">Select the day or days of the week on which the job schedule is run.</span></span>  
  
            -   <span data-ttu-id="a3778-184">如果选择 **“每月”** ，可以选择 **“天”** 或 **“特定日期”** 。</span><span class="sxs-lookup"><span data-stu-id="a3778-184">If you select **Monthly**, select either **Day** or **The**.</span></span>  
  
                -   <span data-ttu-id="a3778-185">如果选择 **“天”** ，请输入要运行作业计划的当月日期和作业计划的重复频率（月）。</span><span class="sxs-lookup"><span data-stu-id="a3778-185">If you select **Day**, enter both the date of the month you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="a3778-186">例如，如果要每隔一个月在当月的 15 日运行计划作业，请选择“天”，在第一个框中输入“15”，在第二个框中输入“2”。</span><span class="sxs-lookup"><span data-stu-id="a3778-186">For example, if you want the job schedule to run on the 15th day of the month every other month, select **Day** and enter "15" in the first box and "2" in the second box.</span></span> <span data-ttu-id="a3778-187">请注意，第二个框中允许的最大数是“99”。</span><span class="sxs-lookup"><span data-stu-id="a3778-187">Please note that the largest number allowed in the second box is "99".</span></span>  
  
                -   <span data-ttu-id="a3778-188">如果选择 **“特定日期”** ，请选择要运行作业计划的当月内一周的特定一天和作业计划的重复频率（月）。</span><span class="sxs-lookup"><span data-stu-id="a3778-188">If you select **The**, select the specific day of the week within the month that you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="a3778-189">例如，如果要每隔一个月在当月的最后一个工作日运行作业计划，请选择“天”，从第一个列表中选择“最后一周”，从第二个列表中选择“工作日”，然后在最后一个框中输入“2”  。</span><span class="sxs-lookup"><span data-stu-id="a3778-189">For example, if you want the job schedule to run on the last weekday of the month every other month, select **Day**, select **last** from the first list and **weekday** from the second list, and then enter "2" in the last box.</span></span> <span data-ttu-id="a3778-190">还可以从前两个列表中选择“第一周”、“第二周”、“第三周”或“第四周”以及特定工作日（例如：星期日或星期三）。</span><span class="sxs-lookup"><span data-stu-id="a3778-190">You can also select **first**, **second**, **third**, or **fourth**, as well as specific weekdays (for example: Sunday or Wednesday) from the first two lists.</span></span> <span data-ttu-id="a3778-191">请注意，最后一个框中允许的最大数是“99”。</span><span class="sxs-lookup"><span data-stu-id="a3778-191">Please note that the largest number allowed in the last box is "99".</span></span>  
  
        2.  <span data-ttu-id="a3778-192">在 **“每天频率”** 下，指定作业计划运行的当天作业计划的重复频率。</span><span class="sxs-lookup"><span data-stu-id="a3778-192">Under **Daily frequency**, specify how often the job schedule repeats on the day the job schedule runs:</span></span>  
  
            -   <span data-ttu-id="a3778-193">如果选择 **“执行一次，时间为:”** ，请在 **“执行一次，时间为:”** 框中输入运行作业计划的当天的特定时间。</span><span class="sxs-lookup"><span data-stu-id="a3778-193">If you select **Occurs once at**, enter the specific time of day when the job schedule should run in the **Occurs once at** box.</span></span> <span data-ttu-id="a3778-194">输入当天的小时、分钟和秒以及 AM 或 PM。</span><span class="sxs-lookup"><span data-stu-id="a3778-194">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
            -   <span data-ttu-id="a3778-195">如果选择 **“执行间隔”** ，请在 **“频率”** 下指定所选日运行作业计划的频率。</span><span class="sxs-lookup"><span data-stu-id="a3778-195">If you select **Occurs every**, specify how often the job schedule runs during the day chosen under **Frequency**.</span></span> <span data-ttu-id="a3778-196">例如，如果要在运行作业计划的当天每隔 2 小时重复一次，请选择“执行间隔”，在第一个框中输入“2”，然后从列表中选择“小时” 。</span><span class="sxs-lookup"><span data-stu-id="a3778-196">For example, if you want the job schedule to repeat every 2 hours during the day that the job schedule is run, select **Occurs every**, enter "2" in the first box, and then select **hour(s)** from the list.</span></span> <span data-ttu-id="a3778-197">从此列表中还可以选择“分钟”和“秒”。</span><span class="sxs-lookup"><span data-stu-id="a3778-197">From this list you can also select **minute(s)** and **second(s)**.</span></span> <span data-ttu-id="a3778-198">请注意，第一个框中允许的最大数是“100”。</span><span class="sxs-lookup"><span data-stu-id="a3778-198">Please note that the largest number allowed in the first box is "100".</span></span>  
  
                 <span data-ttu-id="a3778-199">在 **“开始时间”** 框中，输入开始运行作业计划的时间。</span><span class="sxs-lookup"><span data-stu-id="a3778-199">In the **Starting at** box, enter the time that the job schedule should start running.</span></span> <span data-ttu-id="a3778-200">在 **“结束时间”** 框中，输入停止重复作业计划的时间。</span><span class="sxs-lookup"><span data-stu-id="a3778-200">In the **Ending at** box, enter the time that the job schedule should stop repeating.</span></span> <span data-ttu-id="a3778-201">输入当天的小时、分钟和秒以及 AM 或 PM。</span><span class="sxs-lookup"><span data-stu-id="a3778-201">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
        3.  <span data-ttu-id="a3778-202">在 **“持续时间”** 下的 **“开始日期”** 中，输入希望作业计划开始运行的日期。</span><span class="sxs-lookup"><span data-stu-id="a3778-202">Under **Duration**, in **Start date**, enter the date that you want the job schedule to start running.</span></span> <span data-ttu-id="a3778-203">选择 **“结束日期”** 或 **“无结束日期”** 以指示作业计划应在何时停止运行。</span><span class="sxs-lookup"><span data-stu-id="a3778-203">Select **End date** or **No end date** to indicate when the job schedule should stop running.</span></span> <span data-ttu-id="a3778-204">如果选择 **“结束日期”** ，输入希望作业计划停止运行的日期。</span><span class="sxs-lookup"><span data-stu-id="a3778-204">If you select **End date**, enter the date that you want to job schedule to stop running.</span></span>  
  
    5.  <span data-ttu-id="a3778-205">如果选择“执行一次”，请在“执行一次”下的“日期”框中输入将运行作业计划的日期。</span><span class="sxs-lookup"><span data-stu-id="a3778-205">If you select **One Time**, under **One-time occurrence**, in the **Date** box, enter the date that the job schedule will be run.</span></span> <span data-ttu-id="a3778-206">在 **“时间”** 框中，输入将运行作业计划的时间。</span><span class="sxs-lookup"><span data-stu-id="a3778-206">In the **Time** box, enter the time that the job schedule will be run.</span></span> <span data-ttu-id="a3778-207">输入当天的小时、分钟和秒以及 AM 或 PM。</span><span class="sxs-lookup"><span data-stu-id="a3778-207">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
    6.  <span data-ttu-id="a3778-208">在 **“摘要”** 下的 **“说明”** 中，验证所有作业计划设置均正确。</span><span class="sxs-lookup"><span data-stu-id="a3778-208">Under **Summary**, in **Description**, verify that all job schedule settings are correct.</span></span>  
  
    7.  <span data-ttu-id="a3778-209">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="a3778-209">Click **OK**.</span></span>  
  
     <span data-ttu-id="a3778-210">完成此页后，单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="a3778-210">After completing this page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="a3778-211">在 **“检查摘要”** 页的 **“检查所做选择”** 下，展开所有可用选项以确认所有设置正确。</span><span class="sxs-lookup"><span data-stu-id="a3778-211">On the **Review Summary** page, under **Review your selections**, expand all available options to verify that all settings are correct.</span></span> <span data-ttu-id="a3778-212">如果一切正常，请单击 **“完成”** 。</span><span class="sxs-lookup"><span data-stu-id="a3778-212">If everything is as expected, click **Finish**.</span></span>  
  
8.  <span data-ttu-id="a3778-213">在 **“压缩向导进度”** 页上，监视有关创建分区向导的操作的状态信息。</span><span class="sxs-lookup"><span data-stu-id="a3778-213">On the **Compression Wizard Progress** page, monitor status information about the actions of the Create Partition Wizard.</span></span> <span data-ttu-id="a3778-214">根据在向导中选择的选项，“进度”页可能会包含一个操作或多个操作。</span><span class="sxs-lookup"><span data-stu-id="a3778-214">Depending on the options that you selected in the wizard, the progress page might contain one or more actions.</span></span> <span data-ttu-id="a3778-215">最上面的方框显示向导的总体状态和向导已接收到的状态、错误和警告消息数。</span><span class="sxs-lookup"><span data-stu-id="a3778-215">The top box displays the overall status of the wizard and the number of status, error, and warning messages that the wizard has received.</span></span>  
  
     <span data-ttu-id="a3778-216">**“压缩向导进度”** 页上提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="a3778-216">The following options are available on the **Compression Wizard Progress** page:</span></span>  
  
     <span data-ttu-id="a3778-217">**详细信息**</span><span class="sxs-lookup"><span data-stu-id="a3778-217">**Details**</span></span>  
     <span data-ttu-id="a3778-218">提供向导执行的操作所返回的操作、状态和所有消息。</span><span class="sxs-lookup"><span data-stu-id="a3778-218">Provides the action, status, and any messages that are returned from action taken by the wizard.</span></span>  
  
     <span data-ttu-id="a3778-219">**Action**</span><span class="sxs-lookup"><span data-stu-id="a3778-219">**Action**</span></span>  
     <span data-ttu-id="a3778-220">指定每个操作的类型和名称。</span><span class="sxs-lookup"><span data-stu-id="a3778-220">Specifies the type and name of each action.</span></span>  
  
     <span data-ttu-id="a3778-221">**Status**</span><span class="sxs-lookup"><span data-stu-id="a3778-221">**Status**</span></span>  
     <span data-ttu-id="a3778-222">指示向导操作作为一个整体返回的值是“成功”还是“失败”。</span><span class="sxs-lookup"><span data-stu-id="a3778-222">Indicates whether the wizard action as a whole returned the value of **Success** or **Failure**.</span></span>  
  
     <span data-ttu-id="a3778-223">**消息**</span><span class="sxs-lookup"><span data-stu-id="a3778-223">**Message**</span></span>  
     <span data-ttu-id="a3778-224">提供从该进程中返回的任何错误或警告消息。</span><span class="sxs-lookup"><span data-stu-id="a3778-224">Provides any error or warning messages that are returned from the process.</span></span>  
  
     <span data-ttu-id="a3778-225">**Report**</span><span class="sxs-lookup"><span data-stu-id="a3778-225">**Report**</span></span>  
     <span data-ttu-id="a3778-226">创建包含创建分区向导结果的报告。</span><span class="sxs-lookup"><span data-stu-id="a3778-226">Creates a report that contains the results of the Create Partition Wizard.</span></span> <span data-ttu-id="a3778-227">这些选项是 **“查看报告”** 、 **“将报告保存到文件”** 、 **“将报告复制到剪贴板”** 和 **“将报告作为电子邮件发送”** 。</span><span class="sxs-lookup"><span data-stu-id="a3778-227">The options are **View Report**, **Save Report to File**, **Copy Report to Clipboard**, and **Send Report as Email**.</span></span>  
  
     <span data-ttu-id="a3778-228">**查看报告**</span><span class="sxs-lookup"><span data-stu-id="a3778-228">**View Report**</span></span>  
     <span data-ttu-id="a3778-229">打开“查看报告”对话框，其中包含关于创建分区向导进度的文本报告。</span><span class="sxs-lookup"><span data-stu-id="a3778-229">Opens the **View Report** dialog box, which contains a text report of the progress of the Create Partition Wizard.</span></span>  
  
     <span data-ttu-id="a3778-230">**将报告保存到文件**</span><span class="sxs-lookup"><span data-stu-id="a3778-230">**Save Report to File**</span></span>  
     <span data-ttu-id="a3778-231">打开“将报告另存为”对话框。</span><span class="sxs-lookup"><span data-stu-id="a3778-231">Opens the **Save Report As** dialog box.</span></span>  
  
     <span data-ttu-id="a3778-232">**将报告复制到剪贴板**</span><span class="sxs-lookup"><span data-stu-id="a3778-232">**Copy Report to Clipboard**</span></span>  
     <span data-ttu-id="a3778-233">将向导的进度报告结果复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="a3778-233">Copies the results of the wizard's progress report to the Clipboard.</span></span>  
  
     <span data-ttu-id="a3778-234">**“将报告作为电子邮件发送”**</span><span class="sxs-lookup"><span data-stu-id="a3778-234">**Send Report as Email**</span></span>  
     <span data-ttu-id="a3778-235">将向导的进度报告结果复制到电子邮件。</span><span class="sxs-lookup"><span data-stu-id="a3778-235">Copies the results of the wizard's progress report into an email message.</span></span>  
  
     <span data-ttu-id="a3778-236">完成时，单击“关闭” 。</span><span class="sxs-lookup"><span data-stu-id="a3778-236">When complete, click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a3778-237">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a3778-237">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-compression-on-a-table"></a><span data-ttu-id="a3778-238">对表禁用压缩功能</span><span class="sxs-lookup"><span data-stu-id="a3778-238">To disable compression on a table</span></span>  
  
1.  <span data-ttu-id="a3778-239">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="a3778-239">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a3778-240">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="a3778-240">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a3778-241">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="a3778-241">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Person.Person REBUILD PARTITION = ALL  
    WITH (DATA_COMPRESSION = NONE);  
    GO  
    ```  
  
#### <a name="to-disable-compression-on-an-index"></a><span data-ttu-id="a3778-242">对索引禁用压缩功能</span><span class="sxs-lookup"><span data-stu-id="a3778-242">To disable compression on an index</span></span>  
  
1.  <span data-ttu-id="a3778-243">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="a3778-243">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a3778-244">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="a3778-244">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a3778-245">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="a3778-245">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER INDEX AK_Person_rowguid ON Person.Person REBUILD PARTITION = ALL WITH (DATA_COMPRESSION = NONE);  
    GO  
    ```  
  
 <span data-ttu-id="a3778-246">有关详细信息，请参阅 [ALTER TABLE (Transact-SQL) ](/sql/t-sql/statements/alter-table-transact-sql) 和 [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a3778-246">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) and [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
  
