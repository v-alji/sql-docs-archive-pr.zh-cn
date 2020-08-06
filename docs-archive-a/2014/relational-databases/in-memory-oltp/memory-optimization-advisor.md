---
title: 内存优化顾问 | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
f1_keywords:
- sql12.swb.memoryoptimizationwizard.f1
- swb.memoryoptimizationwizard.f1
ms.assetid: 181989c2-9636-415a-bd1d-d304fc920b8a
author: rothja
ms.author: jroth
ms.openlocfilehash: cd0e08ab6d6a7bb2cfbf1892d6f2e4649e4a9735
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688914"
---
# <a name="memory-optimization-advisor"></a><span data-ttu-id="1f13b-102">内存优化顾问</span><span class="sxs-lookup"><span data-stu-id="1f13b-102">Memory Optimization Advisor</span></span>
  <span data-ttu-id="1f13b-103">事务性能报告工具（请参阅 [Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)）在移植到使用内存中 OLTP 时通知您的数据库中的哪些表会给您带来好处。</span><span class="sxs-lookup"><span data-stu-id="1f13b-103">Transaction performance reports tool (see [Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)) informs you about which tables in your database will benefit if ported to use In-Memory OLTP.</span></span> <span data-ttu-id="1f13b-104">找到要移植以使用内存中 OLTP 的表之后，可使用内存优化顾问帮助您将基于磁盘的数据库表迁移到内存中 OLTP。</span><span class="sxs-lookup"><span data-stu-id="1f13b-104">After you identify a table that you would like to port to use In-Memory OLTP, you can use the memory optimization advisor to help you migrate the disk-based database table to In-Memory OLTP.</span></span>  
  
 <span data-ttu-id="1f13b-105">开始时，连接至包含基于磁盘的数据库表的实例。</span><span class="sxs-lookup"><span data-stu-id="1f13b-105">To begin, connect to the instance that contains the disk-based database table.</span></span> <span data-ttu-id="1f13b-106">你可以连接到 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="1f13b-106">You can connect to a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] or [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] instance.</span></span> <span data-ttu-id="1f13b-107">但是，如果您想要使用该顾问执行迁移操作，则必须连接到启用了内存中 OLTP 功能的 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="1f13b-107">However, if you wish to perform a migration operation with the advisor, you must connect to a [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] instance on which In-Memory OLTP functionality is enabled.</span></span> <span data-ttu-id="1f13b-108">有关内存中 OLTP 要求的详细信息，请参阅 [Requirements for Using Memory-Optimized Tables](memory-optimized-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="1f13b-108">For more information about In-Memory OLTP requirements, see [Requirements for Using Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="1f13b-109">有关迁移方法的信息，请参阅 [内存中 OLTP - 常见的工作负荷模式和迁移注意事项](https://msdn.microsoft.com/library/dn673538.aspx)。</span><span class="sxs-lookup"><span data-stu-id="1f13b-109">For information about migration methodologies, see [In-Memory OLTP - Common Workload Patterns and Migration Considerations](https://msdn.microsoft.com/library/dn673538.aspx).</span></span>  
  
## <a name="walkthrough-using-the-memory-optimization-advisor"></a><span data-ttu-id="1f13b-110">使用内存优化顾问进行演练</span><span class="sxs-lookup"><span data-stu-id="1f13b-110">Walkthrough Using the Memory-Optimization Advisor</span></span>  
 <span data-ttu-id="1f13b-111">在 **对象资源管理器**中，右键单击要转换的表，然后选择 **“内存优化顾问”** 。</span><span class="sxs-lookup"><span data-stu-id="1f13b-111">In **Object Explorer**, right click the table you want to convert, and select **Memory-Optimization Advisor**.</span></span> <span data-ttu-id="1f13b-112">这将显示 **“表内存优化顾问”** 的欢迎使用页。</span><span class="sxs-lookup"><span data-stu-id="1f13b-112">This will display the welcome page for the **Table Memory Optimization Advisor**.</span></span>  
  
### <a name="memory-optimization-checklist"></a><span data-ttu-id="1f13b-113">内存优化核对清单</span><span class="sxs-lookup"><span data-stu-id="1f13b-113">Memory Optimization Checklist</span></span>  
 <span data-ttu-id="1f13b-114">当您在 **“表内存优化顾问”** 的欢迎使用页中单击 **“下一步”** 时，将会看到内存优化核对清单。</span><span class="sxs-lookup"><span data-stu-id="1f13b-114">When you click **Next** in the welcome page for the **Table Memory Optimization Advisor**, you will see the memory optimization checklist.</span></span> <span data-ttu-id="1f13b-115">内存优化表并不支持基于磁盘的表中的所有功能。</span><span class="sxs-lookup"><span data-stu-id="1f13b-115">Memory-optimized tables do not support all the features in a disk-based table.</span></span> <span data-ttu-id="1f13b-116">内存优化核对清单将报告基于磁盘的表是否使用了与内存优化表不兼容的任何功能。</span><span class="sxs-lookup"><span data-stu-id="1f13b-116">The memory optimization checklist reports if the disk-based table uses any features that are incompatible with a memory-optimized table.</span></span> <span data-ttu-id="1f13b-117">**“表内存优化顾问”** 不会修改基于磁盘的表，以便它可以迁移到使用内存中 OLTP。</span><span class="sxs-lookup"><span data-stu-id="1f13b-117">The **Table Memory Optimization Advisor** does not modify the disk-based table so that it can be migrated to use In-Memory OLTP.</span></span> <span data-ttu-id="1f13b-118">您必须首先进行这些更改，然后才能继续迁移。</span><span class="sxs-lookup"><span data-stu-id="1f13b-118">You must make those changes before continuing migration.</span></span> <span data-ttu-id="1f13b-119">对于找到的每个不兼容之处， **“表内存优化顾问”** 都会显示一个链接，指向可帮助您修改基于磁盘的表的信息。</span><span class="sxs-lookup"><span data-stu-id="1f13b-119">For each incompatibility found, the **Table Memory Optimization Advisor** displays a link to information that can help you modify your disk-based tables.</span></span>  
  
 <span data-ttu-id="1f13b-120">如果您想要保留这些不兼容之处的列表以便计划您的迁移，则单击 **“生成报表”** 以便生成一个 HTML 列表。</span><span class="sxs-lookup"><span data-stu-id="1f13b-120">If you wish to keep a list of these incompatibilities, to plan your migration, click the **Generate Report** to generate a HTML list.</span></span>  
  
 <span data-ttu-id="1f13b-121">如果您的表没有不兼容之处并且连接到了具有内存中 OLTP 的某一 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 实例，则单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="1f13b-121">If your table has no incompatibilities and you are connected to a [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] instance with In-Memory OLTP, click **Next**.</span></span>  
  
### <a name="memory-optimization-warnings"></a><span data-ttu-id="1f13b-122">内存优化警告</span><span class="sxs-lookup"><span data-stu-id="1f13b-122">Memory Optimization Warnings</span></span>  
 <span data-ttu-id="1f13b-123">下一页“内存优化警告”包含问题的列表，这些问题不会阻止表迁移到使用内存中 OLTP，但这些问题可能导致其他对象（例如存储过程或 CLR 函数）的行为失败或者导致意外行为。</span><span class="sxs-lookup"><span data-stu-id="1f13b-123">The next page, memory optimization warnings, contains a list of issues that do not prevent the table from being migrated to use In-Memory OLTP, but that may cause the behavior of other objects (such as stored procedures or CLR functions) to fail or result in unexpected behavior.</span></span>  
  
 <span data-ttu-id="1f13b-124">该列表中的前几个警告仅供参考，不一定适用于您的表。</span><span class="sxs-lookup"><span data-stu-id="1f13b-124">The first several warnings in the list are informational and may or may not apply to your table.</span></span> <span data-ttu-id="1f13b-125">该表的右键单击列中的链接将会给您提供更多的信息。</span><span class="sxs-lookup"><span data-stu-id="1f13b-125">Links in the right-hand column of the table will take you to more information.</span></span>  
  
 <span data-ttu-id="1f13b-126">该警告表还将显示在您的表中未出现的可能的警告条件。</span><span class="sxs-lookup"><span data-stu-id="1f13b-126">The warning table will also display potential warning conditions that are not present in your table.</span></span>  
  
 <span data-ttu-id="1f13b-127">可操作警告将在左侧列中具有一个黄色的三角形。</span><span class="sxs-lookup"><span data-stu-id="1f13b-127">Actionable warnings will have a yellow triangle in the left-hand column.</span></span> <span data-ttu-id="1f13b-128">如果存在可操作警告，您应该退出迁移，解决警告问题，然后重新开始迁移过程。</span><span class="sxs-lookup"><span data-stu-id="1f13b-128">If there are actionable warnings, you should exit the migration, resolve the warnings, and then restart the process.</span></span> <span data-ttu-id="1f13b-129">如果您没有解决警告问题，则迁移的表可能会导致失败。</span><span class="sxs-lookup"><span data-stu-id="1f13b-129">If you do not resolve the warnings, your migrated table may cause a failure.</span></span>  
  
 <span data-ttu-id="1f13b-130">单击 **“生成报表”** 可生成包含这些警告的 HTML 报表。</span><span class="sxs-lookup"><span data-stu-id="1f13b-130">Click **Generate Report** to generate an HTML report of these warnings.</span></span> <span data-ttu-id="1f13b-131">单击“下一步”继续。</span><span class="sxs-lookup"><span data-stu-id="1f13b-131">Click **Next** to proceed.</span></span>  
  
### <a name="review-optimization-options"></a><span data-ttu-id="1f13b-132">检查优化选项</span><span class="sxs-lookup"><span data-stu-id="1f13b-132">Review Optimization Options</span></span>  
 <span data-ttu-id="1f13b-133">下一个屏幕可用于修改用于迁移到内存中 OLTP 的选项：</span><span class="sxs-lookup"><span data-stu-id="1f13b-133">The next screen lets you modify options for the migration to In-Memory OLTP:</span></span>  
  
 <span data-ttu-id="1f13b-134">内存优化的文件组</span><span class="sxs-lookup"><span data-stu-id="1f13b-134">Memory-optimized filegroup</span></span>  
 <span data-ttu-id="1f13b-135">您的内存优化的文件组的名称。</span><span class="sxs-lookup"><span data-stu-id="1f13b-135">The name for your memory-optimized filegroup.</span></span> <span data-ttu-id="1f13b-136">一个数据库必须首先具有含至少一个文件的内存优化的文件组，然后才能创建内存优化表。</span><span class="sxs-lookup"><span data-stu-id="1f13b-136">A database must have a memory-optimized filegroup with at least one file before a memory-optimized table can be created.</span></span>  
  
 <span data-ttu-id="1f13b-137">如果您没有内存优化的文件组，则可以更改默认名称。</span><span class="sxs-lookup"><span data-stu-id="1f13b-137">If you do not have a memory-optimized filegroup, you can change the default name.</span></span> <span data-ttu-id="1f13b-138">内存优化的文件组不能删除。</span><span class="sxs-lookup"><span data-stu-id="1f13b-138">Memory-optimized filegroups cannot be deleted.</span></span> <span data-ttu-id="1f13b-139">存在内存优化的文件组可能会禁用某些数据库级别的功能，例如 AUTO CLOSE 和数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="1f13b-139">The existence of a memory-optimized filegroup may disable some database-level features such as AUTO CLOSE and database mirroring.</span></span>  
  
 <span data-ttu-id="1f13b-140">如果某个数据库具有内存优化的文件组，则该字段将用其名称预先填充，并且您将不能更改该字段的值。</span><span class="sxs-lookup"><span data-stu-id="1f13b-140">If a database already has a memory-optimized file group, this field will be pre-populated with its name and you will not be able to change the value of this field.</span></span>  
  
 <span data-ttu-id="1f13b-141">逻辑文件名和文件路径</span><span class="sxs-lookup"><span data-stu-id="1f13b-141">Logical file name and File path</span></span>  
 <span data-ttu-id="1f13b-142">将包含内存优化表的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="1f13b-142">The name of the file that will contain the memory-optimized table.</span></span> <span data-ttu-id="1f13b-143">一个数据库必须首先具有含至少一个文件的内存优化的文件组，然后才能创建内存优化表。</span><span class="sxs-lookup"><span data-stu-id="1f13b-143">A database must have a memory-optimized file group with at least one file before a memory-optimized table can be created.</span></span>  
  
 <span data-ttu-id="1f13b-144">如果您没有现有的内存优化的文件组，则可以将该文件的默认名称和路径更改为在迁移过程结束时创建。</span><span class="sxs-lookup"><span data-stu-id="1f13b-144">If you do not have an existing memory-optimized file group, you can change the default name and path of the file to be created at the end of the migration process.</span></span>  
  
 <span data-ttu-id="1f13b-145">如果您具有现有的内存优化的文件组，则这些字段将预先填充并且您将不能更改这些值。</span><span class="sxs-lookup"><span data-stu-id="1f13b-145">If you have an existing memory-optimized filegroup, these fields will be pre-populated and you will not be able to change the values.</span></span>  
  
 <span data-ttu-id="1f13b-146">重命名原始表</span><span class="sxs-lookup"><span data-stu-id="1f13b-146">Rename the original table as</span></span>  
 <span data-ttu-id="1f13b-147">在迁移过程结束时，将用该表的当前名称创建一个新的内存优化表。</span><span class="sxs-lookup"><span data-stu-id="1f13b-147">At the end of the migration process, a new memory-optimized table will be created with the current name of the table.</span></span> <span data-ttu-id="1f13b-148">为避免名称冲突，必须重命名当前表。</span><span class="sxs-lookup"><span data-stu-id="1f13b-148">To avoid a name conflict, the current table must be renamed.</span></span> <span data-ttu-id="1f13b-149">您可以在此字段中更改该名称。</span><span class="sxs-lookup"><span data-stu-id="1f13b-149">You may change that name in this field.</span></span>  
  
 <span data-ttu-id="1f13b-150">估计的当前内存开销 (MB)</span><span class="sxs-lookup"><span data-stu-id="1f13b-150">Estimated current memory cost (MB)</span></span>  
 <span data-ttu-id="1f13b-151">内存优化顾问将会根据基于磁盘的表的元数据，估计新的内存优化表将使用的内存量。</span><span class="sxs-lookup"><span data-stu-id="1f13b-151">The Memory-Optimization Advisor estimates the amount of memory the new memory-optimized table will consume based on metadata of the disk-based table.</span></span> <span data-ttu-id="1f13b-152">[内存优化表中的表和行大小](table-and-row-size-in-memory-optimized-tables.md)中说明了表大小的计算。</span><span class="sxs-lookup"><span data-stu-id="1f13b-152">The calculation of the table size is explained in [Table and Row Size in Memory-Optimized Tables](table-and-row-size-in-memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="1f13b-153">如果没有分配足够的内存，迁移过程将失败。</span><span class="sxs-lookup"><span data-stu-id="1f13b-153">If sufficient memory is not allotted, the migration process may fail.</span></span>  
  
 <span data-ttu-id="1f13b-154">还将表数据复制到新的内存优化表</span><span class="sxs-lookup"><span data-stu-id="1f13b-154">Also copy table data to the new memory optimized table</span></span>  
 <span data-ttu-id="1f13b-155">如果您还要将当前表中的数据移到新的内存优化表，则选择此选项。</span><span class="sxs-lookup"><span data-stu-id="1f13b-155">Select this option if you wish to also move the data in the current table to the new memory-optimized table.</span></span> <span data-ttu-id="1f13b-156">如果未选择此选项，将创建新的内存优化表，但其中不含任何行。</span><span class="sxs-lookup"><span data-stu-id="1f13b-156">If this option is not selected, the new memory-optimized table will be created with no rows.</span></span>  
  
 <span data-ttu-id="1f13b-157">默认情况下该表将作为持久表迁移</span><span class="sxs-lookup"><span data-stu-id="1f13b-157">The table will be migrated as a durable table by default</span></span>  
 <span data-ttu-id="1f13b-158">内存中 OLTP 支持非持久表，这些表具有与持久的内存优化表相当的优异性能。</span><span class="sxs-lookup"><span data-stu-id="1f13b-158">In-Memory OLTP supports non-durable tables with superior performance compared to durable memory-optimized tables.</span></span> <span data-ttu-id="1f13b-159">但是，在服务器重新启动后非持久表中的数据将会丢失。</span><span class="sxs-lookup"><span data-stu-id="1f13b-159">However, data in a non-durable table will be lost upon server restart.</span></span>  
  
 <span data-ttu-id="1f13b-160">如果选择了此选项，内存优化顾问将创建非持久表，而不是持久表。</span><span class="sxs-lookup"><span data-stu-id="1f13b-160">If this option is selected, the Memory-Optimization Advisor will create a non-durable table instead of a durable table.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="1f13b-161">只有在您明了与非持久表相关联的数据丢失风险的情况下，才选择此选项。</span><span class="sxs-lookup"><span data-stu-id="1f13b-161">Select this option only if you understand the risk of data loss associated with non-durable tables.</span></span>  
  
 <span data-ttu-id="1f13b-162">单击“下一步”以继续。</span><span class="sxs-lookup"><span data-stu-id="1f13b-162">Click **Next** to continue.</span></span>  
  
### <a name="review-primary-key-conversion"></a><span data-ttu-id="1f13b-163">检查主键转换</span><span class="sxs-lookup"><span data-stu-id="1f13b-163">Review Primary Key Conversion</span></span>  
 <span data-ttu-id="1f13b-164">下一个屏幕是 **“检查主键转换”** 。</span><span class="sxs-lookup"><span data-stu-id="1f13b-164">The next screen is **Review Primary Key Conversion**.</span></span> <span data-ttu-id="1f13b-165">内存优化顾问将检测到表中是否有一个或多个主键，并且基于主键元数据填充列的列表。</span><span class="sxs-lookup"><span data-stu-id="1f13b-165">The Memory-Optimization Advisor will detect if there are one or more primary keys in the table, and populates the list of columns based on the primary key metadata.</span></span> <span data-ttu-id="1f13b-166">否则，如果您想要迁移到持久的内存优化表，则必须创建主键。</span><span class="sxs-lookup"><span data-stu-id="1f13b-166">Otherwise, if you wish to migrate to a durable memory-optimized table, you must create a primary key.</span></span>  
  
 <span data-ttu-id="1f13b-167">如果主键不存在并且该表正迁移到非持久表，则该屏幕将不会出现。</span><span class="sxs-lookup"><span data-stu-id="1f13b-167">If a primary key doesn't exist and the table is being migrated to a non-durable table, this screen will not appear.</span></span>  
  
 <span data-ttu-id="1f13b-168">对于文本列（类型为 `char`、`nchar`、`varchar` 和 `nvarchar` 的列），您必须选择相应的排序规则。</span><span class="sxs-lookup"><span data-stu-id="1f13b-168">For textual columns (columns with types `char`, `nchar`, `varchar`, and `nvarchar`) you must select an appropriate collation.</span></span> <span data-ttu-id="1f13b-169">对于内存优化表上的列，内存中 OLTP 仅支持 BIN2 排序规则，并且不支持具有增补字符的排序规则。</span><span class="sxs-lookup"><span data-stu-id="1f13b-169">In-Memory OLTP only supports BIN2 collations for columns on a memory-optimized table and it does not support collations with supplementary characters.</span></span> <span data-ttu-id="1f13b-170">有关支持的排序规则以及排序规则中更改的潜在影响的信息，请参阅 [Collations and Code Pages](../../database-engine/collations-and-code-pages.md) 。</span><span class="sxs-lookup"><span data-stu-id="1f13b-170">See [Collations and Code Pages](../../database-engine/collations-and-code-pages.md) for information on the collations supported and the potential impact of a change in collation.</span></span>  
  
 <span data-ttu-id="1f13b-171">可为主键配置以下参数：</span><span class="sxs-lookup"><span data-stu-id="1f13b-171">You can configure the following parameters for the primary key:</span></span>  
  
 <span data-ttu-id="1f13b-172">为该主键选择一个新名称</span><span class="sxs-lookup"><span data-stu-id="1f13b-172">Select a new name for this primary key</span></span>  
 <span data-ttu-id="1f13b-173">该表的主键名称在数据库内必须唯一。</span><span class="sxs-lookup"><span data-stu-id="1f13b-173">The primary key name for this table must be unique inside the database.</span></span> <span data-ttu-id="1f13b-174">您可在此处更改主键的名称。</span><span class="sxs-lookup"><span data-stu-id="1f13b-174">You may change the name of the primary key here.</span></span>  
  
 <span data-ttu-id="1f13b-175">选择该主键的类型</span><span class="sxs-lookup"><span data-stu-id="1f13b-175">Select the type of this primary key</span></span>  
 <span data-ttu-id="1f13b-176">内存中 OLTP 在内存优化表上支持两种类型的索引：</span><span class="sxs-lookup"><span data-stu-id="1f13b-176">In-Memory OLTP supports two types of indexes on a memory-optimized table:</span></span>  
  
-   <span data-ttu-id="1f13b-177">NONCLUSTERED HASH 索引。</span><span class="sxs-lookup"><span data-stu-id="1f13b-177">A NONCLUSTERED HASH index.</span></span> <span data-ttu-id="1f13b-178">此索引最适合于具有许多点查找的索引。</span><span class="sxs-lookup"><span data-stu-id="1f13b-178">This index is best for indexes with many point lookups.</span></span> <span data-ttu-id="1f13b-179">您可以在 **“存储桶计数”** 字段中为此索引配置存储桶计数。</span><span class="sxs-lookup"><span data-stu-id="1f13b-179">You may configure the bucket count for this index in the **Bucket Count** field.</span></span>  
  
-   <span data-ttu-id="1f13b-180">NONCLUSTERED 索引。</span><span class="sxs-lookup"><span data-stu-id="1f13b-180">A NONCLUSTERED index.</span></span> <span data-ttu-id="1f13b-181">此类型的索引最适合于具有许多范围查询的索引。</span><span class="sxs-lookup"><span data-stu-id="1f13b-181">This type of index is best for indexes with many range queries.</span></span> <span data-ttu-id="1f13b-182">您可以在 **“排序列和顺序”** 列表中配置每一列的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="1f13b-182">You may configure the sort order for each column in the **Sort column and order** list.</span></span>  
  
 <span data-ttu-id="1f13b-183">若要了解最适合你的主键的索引的类型，请参阅 [哈希索引](../../database-engine/hash-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="1f13b-183">To understand the type of index best for your primary key, see [Hash Indexes](../../database-engine/hash-indexes.md).</span></span>  
  
 <span data-ttu-id="1f13b-184">在选择了您的主键后单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="1f13b-184">Click **Next** after you make your primary key choices.</span></span>  
  
### <a name="review-index-conversion"></a><span data-ttu-id="1f13b-185">检查索引转换</span><span class="sxs-lookup"><span data-stu-id="1f13b-185">Review Index Conversion</span></span>  
 <span data-ttu-id="1f13b-186">下一页是 **“检查索引转换”** 。</span><span class="sxs-lookup"><span data-stu-id="1f13b-186">The next page is **Review Index Conversion**.</span></span> <span data-ttu-id="1f13b-187">内存优化顾问将检测到表中是否有一个或多个索引，并且填充列的列表和数据类型。</span><span class="sxs-lookup"><span data-stu-id="1f13b-187">The Memory-Optimization Advisor will detect if there are one or more indexes in the table, and populates the list of columns and data type.</span></span> <span data-ttu-id="1f13b-188">您在 **“检查索引转换”** 页中可以配置的参数类似于前一页 **“检查主键转换”** 。</span><span class="sxs-lookup"><span data-stu-id="1f13b-188">The parameters you can configure in the **Review Index Conversion** page are similar to the previous, **Review Primary Key Conversion** page.</span></span>  
  
 <span data-ttu-id="1f13b-189">如果该表仅具有主键并且正迁移到持久表，则该屏幕将不会出现。</span><span class="sxs-lookup"><span data-stu-id="1f13b-189">If the table only has a primary key and it's being migrated to a durable table, this screen will not appear.</span></span>  
  
 <span data-ttu-id="1f13b-190">在确定了表中的每个索引后，单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="1f13b-190">After you make a decision for every index in your table, click **Next**.</span></span>  
  
### <a name="verify-migration-actions"></a><span data-ttu-id="1f13b-191">验证迁移操作</span><span class="sxs-lookup"><span data-stu-id="1f13b-191">Verify Migration Actions</span></span>  
 <span data-ttu-id="1f13b-192">下一页是 **“验证迁移操作”** 。</span><span class="sxs-lookup"><span data-stu-id="1f13b-192">The next page is **Verify Migration Actions**.</span></span> <span data-ttu-id="1f13b-193">若要编写迁移操作的脚本，请单击 **“脚本”** 以便生成 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本。</span><span class="sxs-lookup"><span data-stu-id="1f13b-193">To script the migration operation, click **Script** to generate a [!INCLUDE[tsql](../../includes/tsql-md.md)] script.</span></span> <span data-ttu-id="1f13b-194">然后，您可以修改并且执行该脚本。</span><span class="sxs-lookup"><span data-stu-id="1f13b-194">You may then modify and execute the script.</span></span> <span data-ttu-id="1f13b-195">单击 **“迁移”** 可开始表迁移。</span><span class="sxs-lookup"><span data-stu-id="1f13b-195">Click **Migrate** to begin the table migration.</span></span>  
  
 <span data-ttu-id="1f13b-196">在完成该过程后，刷新 **对象资源管理器** 可查看新的内存优化表和旧的基于磁盘的表。</span><span class="sxs-lookup"><span data-stu-id="1f13b-196">After the process is finished, refresh **Object Explorer** to see the new memory-optimized table and the old disk-based table.</span></span> <span data-ttu-id="1f13b-197">您可以保留旧表或者在方便时删除它。</span><span class="sxs-lookup"><span data-stu-id="1f13b-197">You can keep the old table or delete it at your convenience.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f13b-198">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1f13b-198">See Also</span></span>  
 [<span data-ttu-id="1f13b-199">迁移到内存中 OLTP</span><span class="sxs-lookup"><span data-stu-id="1f13b-199">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
