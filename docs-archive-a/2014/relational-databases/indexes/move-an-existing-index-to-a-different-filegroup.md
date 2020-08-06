---
title: 将现有索引移动到其他文件组 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- moving tables
- switching filegroups for index
- moving indexes
- indexes [SQL Server], moving
- filegroups [SQL Server], switching
ms.assetid: 167ebe77-487d-4ca8-9452-4b2c7d5cb96e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c99847dcb8d4d65272dd3660c7fd60d3efb8d951
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590791"
---
# <a name="move-an-existing-index-to-a-different-filegroup"></a><span data-ttu-id="b5f39-102">将现有索引移动到其他文件组中</span><span class="sxs-lookup"><span data-stu-id="b5f39-102">Move an Existing Index to a Different Filegroup</span></span>
  <span data-ttu-id="b5f39-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中将现有索引从其当前文件组移动到其他文件组。</span><span class="sxs-lookup"><span data-stu-id="b5f39-103">This topic describes how to move an existing index from its current filegroup to a different filegroup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="b5f39-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="b5f39-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b5f39-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="b5f39-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b5f39-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b5f39-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b5f39-107">安全性</span><span class="sxs-lookup"><span data-stu-id="b5f39-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b5f39-108">**若要将现有索引移动到其他文件组中，请使用：**</span><span class="sxs-lookup"><span data-stu-id="b5f39-108">**To move an existing index to a different filegroup, using:**</span></span>  
  
     [<span data-ttu-id="b5f39-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b5f39-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b5f39-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b5f39-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b5f39-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="b5f39-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b5f39-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b5f39-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="b5f39-113">如果表具有聚集索引，则将此聚集索引移动到新文件组的同时也会将表移动到该文件组。</span><span class="sxs-lookup"><span data-stu-id="b5f39-113">If a table has a clustered index, moving the clustered index to a new filegroup moves the table to that filegroup.</span></span>  
  
-   <span data-ttu-id="b5f39-114">不能通过使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]来移动使用 UNIQUE 或 PRIMARY KEY 约束创建的索引。</span><span class="sxs-lookup"><span data-stu-id="b5f39-114">You cannot move indexes created using a UNIQUE or PRIMARY KEY constraint using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="b5f39-115">若要移动这些索引，请在 [中使用](/sql/t-sql/statements/create-index-transact-sql) CREATE INDEX [!INCLUDE[tsql](../../includes/tsql-md.md)]语句以及 (DROP_EXISTING=ON) 选项。</span><span class="sxs-lookup"><span data-stu-id="b5f39-115">To move these indexes use the [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql) statement with the (DROP_EXISTING=ON) option in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b5f39-116">Security</span><span class="sxs-lookup"><span data-stu-id="b5f39-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b5f39-117">权限</span><span class="sxs-lookup"><span data-stu-id="b5f39-117">Permissions</span></span>  
 <span data-ttu-id="b5f39-118">要求对表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="b5f39-118">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="b5f39-119">用户必须是 **sysadmin** 固定服务器角色的成员，或者是 **db_ddladmin** 和 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="b5f39-119">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b5f39-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b5f39-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-move-an-existing-index-to-a-different-filegroup-using-table-designer"></a><span data-ttu-id="b5f39-121">使用表设计器将现有索引移到其他文件组</span><span class="sxs-lookup"><span data-stu-id="b5f39-121">To move an existing index to a different filegroup using Table Designer</span></span>  
  
1.  <span data-ttu-id="b5f39-122">在“对象资源管理器”中，单击加号以展开包含该特定表的数据库，该表包含您要移动的索引。</span><span class="sxs-lookup"><span data-stu-id="b5f39-122">In Object Explorer, click the plus sign to expand the database that contains the table containing the index that you want to move.</span></span>  
  
2.  <span data-ttu-id="b5f39-123">单击加号以便展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="b5f39-123">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="b5f39-124">右键单击您要移动的索引的表，然后选择  “设计”。</span><span class="sxs-lookup"><span data-stu-id="b5f39-124">Right-click the table containing the index that you want to move and select **Design**.</span></span>  
  
4.  <span data-ttu-id="b5f39-125">在“表设计器”  菜单上，单击“索引/键”  。</span><span class="sxs-lookup"><span data-stu-id="b5f39-125">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="b5f39-126">选择要移动的索引。</span><span class="sxs-lookup"><span data-stu-id="b5f39-126">Select the index that you want to move.</span></span>  
  
6.  <span data-ttu-id="b5f39-127">在主网格中，展开 **“数据空间规范”** 。</span><span class="sxs-lookup"><span data-stu-id="b5f39-127">In the main grid, expand **Data Space Specification**.</span></span>  
  
7.  <span data-ttu-id="b5f39-128">选择 **“文件组或分区方案名称”** 并从列表中选择要将索引移动到的文件组或分区方案。</span><span class="sxs-lookup"><span data-stu-id="b5f39-128">Select **Filegroup or Partition Scheme Name** and select from the list the filegroup or partition scheme to where you want to move the index.</span></span>  
  
8.  <span data-ttu-id="b5f39-129">单击“关闭”  。</span><span class="sxs-lookup"><span data-stu-id="b5f39-129">Click **Close**.</span></span>  
  
9. <span data-ttu-id="b5f39-130">在“文件”  菜单上，选择“保存”  以保存 _table_name_。</span><span class="sxs-lookup"><span data-stu-id="b5f39-130">On the **File** menu, select **Save**_table_name_.</span></span>  
  
#### <a name="to-move-an-existing-index-to-a-different-filegroup-in-object-explorer"></a><span data-ttu-id="b5f39-131">在“对象资源管理器”中将现有索引移到其他文件组</span><span class="sxs-lookup"><span data-stu-id="b5f39-131">To move an existing index to a different filegroup in Object Explorer</span></span>  
  
1.  <span data-ttu-id="b5f39-132">在“对象资源管理器”中，单击加号以展开包含该特定表的数据库，该表包含您要移动的索引。</span><span class="sxs-lookup"><span data-stu-id="b5f39-132">In Object Explorer, click the plus sign to expand the database that contains the table containing the index that you want to move.</span></span>  
  
2.  <span data-ttu-id="b5f39-133">单击加号以便展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="b5f39-133">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="b5f39-134">单击加号以展开包含您要移动的索引的表。</span><span class="sxs-lookup"><span data-stu-id="b5f39-134">Click the plus sign to expand the table containing the index that you want to move.</span></span>  
  
4.  <span data-ttu-id="b5f39-135">单击加号以便展开 **“索引”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="b5f39-135">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="b5f39-136">右键单击要移动的索引，然后选择  “属性”。</span><span class="sxs-lookup"><span data-stu-id="b5f39-136">Right-click the index that you want to move and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="b5f39-137">在 **“选择页”** 下，选择 **“存储”** 。</span><span class="sxs-lookup"><span data-stu-id="b5f39-137">Under **Select a page**, select **Storage**.</span></span>  
  
7.  <span data-ttu-id="b5f39-138">选择移动此索引的目标文件组。</span><span class="sxs-lookup"><span data-stu-id="b5f39-138">Select the filegroup in which to move the index.</span></span>  
  
     <span data-ttu-id="b5f39-139">如果表或索引已分区，则选择要在其中移动索引的分区架构。</span><span class="sxs-lookup"><span data-stu-id="b5f39-139">If the table or index is partitioned, select the partition scheme in which to move the index.</span></span> <span data-ttu-id="b5f39-140">有关已分区索引的详细信息，请参阅 [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="b5f39-140">For more information about partitioned indexes, see [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md).</span></span>  
  
     <span data-ttu-id="b5f39-141">如果要移动聚集索引，则可以使用联机处理。</span><span class="sxs-lookup"><span data-stu-id="b5f39-141">If you are moving a clustered index, you can use online processing.</span></span> <span data-ttu-id="b5f39-142">联机处理使并发用户可以在索引操作期间访问基础数据和非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="b5f39-142">Online processing allows concurrent user access to the underlying data and to nonclustered indexes during the index operation.</span></span> <span data-ttu-id="b5f39-143">有关详细信息，请参阅 [Perform Index Operations Online](perform-index-operations-online.md)。</span><span class="sxs-lookup"><span data-stu-id="b5f39-143">For more information, see [Perform Index Operations Online](perform-index-operations-online.md).</span></span>  
  
     <span data-ttu-id="b5f39-144">在使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的多处理器计算机上，可以通过指定最大的并行度值来配置用于执行索引语句的处理器数。</span><span class="sxs-lookup"><span data-stu-id="b5f39-144">On multiprocessor computers using [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can configure the number of processors used to execute the index statement by specifying a maximum degree of parallelism value.</span></span> <span data-ttu-id="b5f39-145">并非 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的每个版本均提供并行索引操作功能。</span><span class="sxs-lookup"><span data-stu-id="b5f39-145">The Parallel indexed operations feature is not available in every edition of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b5f39-146">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="b5f39-146">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="b5f39-147">有关并行索引操作的详细信息，请参阅 [配置并行索引操作](configure-parallel-index-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="b5f39-147">For more information about Parallel indexed operations, see [Configure Parallel Index Operations](configure-parallel-index-operations.md).</span></span>  
  
8.  <span data-ttu-id="b5f39-148">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="b5f39-148">Click **OK**.</span></span>  
  
 <span data-ttu-id="b5f39-149">“索引属性 - index_name”对话框的“存储”页面中提供了以下信息    ：</span><span class="sxs-lookup"><span data-stu-id="b5f39-149">The following information is available on the **Storage** page of the **Index Properties -** _index_name_ dialog box:</span></span>  
  
 <span data-ttu-id="b5f39-150">**文件组**</span><span class="sxs-lookup"><span data-stu-id="b5f39-150">**Filegroup**</span></span>  
 <span data-ttu-id="b5f39-151">在指定的文件组中存储索引。</span><span class="sxs-lookup"><span data-stu-id="b5f39-151">Stores the index in the specified filegroup.</span></span> <span data-ttu-id="b5f39-152">该列表仅显示标准 (row) 文件组。</span><span class="sxs-lookup"><span data-stu-id="b5f39-152">The list only displays standard (row) filegroups.</span></span> <span data-ttu-id="b5f39-153">默认情况下，将在该列表中选择相应数据库的 PRIMARY 文件组。</span><span class="sxs-lookup"><span data-stu-id="b5f39-153">The default list selection is the PRIMARY filegroup of the database.</span></span>  
  
 <span data-ttu-id="b5f39-154">**Filestream 文件组**</span><span class="sxs-lookup"><span data-stu-id="b5f39-154">**Filestream filegroup**</span></span>  
 <span data-ttu-id="b5f39-155">指定 FILESTREAM 数据的文件组。</span><span class="sxs-lookup"><span data-stu-id="b5f39-155">Specifies the filegroup for FILESTREAM data.</span></span> <span data-ttu-id="b5f39-156">该列表仅显示 FILESTREAM 文件组。</span><span class="sxs-lookup"><span data-stu-id="b5f39-156">This list displays only FILESTREAM filegroups.</span></span> <span data-ttu-id="b5f39-157">默认情况下，将在该列表中选择 PRIMARY FILESTREAM 文件组。</span><span class="sxs-lookup"><span data-stu-id="b5f39-157">The default list selection is the PRIMARY FILESTREAM filegroup.</span></span>  
  
 <span data-ttu-id="b5f39-158">**分区方案**</span><span class="sxs-lookup"><span data-stu-id="b5f39-158">**Partition scheme**</span></span>  
 <span data-ttu-id="b5f39-159">在分区方案中存储索引。</span><span class="sxs-lookup"><span data-stu-id="b5f39-159">Stores the index in a partition scheme.</span></span> <span data-ttu-id="b5f39-160">单击 **“分区方案”** 可启用下面的网格。</span><span class="sxs-lookup"><span data-stu-id="b5f39-160">Clicking **Partition Scheme** enables the grid below.</span></span> <span data-ttu-id="b5f39-161">默认情况下，将在该列表中选择用于存储表数据的分区方案。</span><span class="sxs-lookup"><span data-stu-id="b5f39-161">The default list selection is the partition scheme that is used for storing the table data.</span></span> <span data-ttu-id="b5f39-162">在列表中选择其他分区方案将更新该网格中的信息。</span><span class="sxs-lookup"><span data-stu-id="b5f39-162">When you select a different partition scheme in the list, the information in the grid is updated.</span></span>  
  
 <span data-ttu-id="b5f39-163">如果数据库中没有分区方案，则分区方案选项不可用。</span><span class="sxs-lookup"><span data-stu-id="b5f39-163">The partition scheme option is unavailable if there are no partition schemes in the database.</span></span>  
  
 <span data-ttu-id="b5f39-164">**Filestream 分区方案**</span><span class="sxs-lookup"><span data-stu-id="b5f39-164">**Filestream partition scheme**</span></span>  
 <span data-ttu-id="b5f39-165">指定 FILESTREAM 数据的分区方案。</span><span class="sxs-lookup"><span data-stu-id="b5f39-165">Specifies the partition scheme for FILESTREAM data.</span></span> <span data-ttu-id="b5f39-166">分区方案必须与 **“分区方案”** 选项中指定的方案对称。</span><span class="sxs-lookup"><span data-stu-id="b5f39-166">The partition scheme must be symmetric with the scheme that is specified in the **Partition scheme** option.</span></span>  
  
 <span data-ttu-id="b5f39-167">如果表未分区，则该字段为空白。</span><span class="sxs-lookup"><span data-stu-id="b5f39-167">If the table is not partitioned, the field is blank.</span></span>  
  
 <span data-ttu-id="b5f39-168">**分区方案参数**</span><span class="sxs-lookup"><span data-stu-id="b5f39-168">**Partition Scheme Parameter**</span></span>  
 <span data-ttu-id="b5f39-169">显示构成分区方案的列的名称。</span><span class="sxs-lookup"><span data-stu-id="b5f39-169">Displays the name of the column that participates in the partition scheme.</span></span>  
  
 <span data-ttu-id="b5f39-170">**表列**</span><span class="sxs-lookup"><span data-stu-id="b5f39-170">**Table Column**</span></span>  
 <span data-ttu-id="b5f39-171">选择要映射到分区方案的表或视图。</span><span class="sxs-lookup"><span data-stu-id="b5f39-171">Select the table or view to map to the partition scheme.</span></span>  
  
 <span data-ttu-id="b5f39-172">**列数据类型**</span><span class="sxs-lookup"><span data-stu-id="b5f39-172">**Column Data Type**</span></span>  
 <span data-ttu-id="b5f39-173">显示有关列的数据类型信息。</span><span class="sxs-lookup"><span data-stu-id="b5f39-173">Displays data type information about the column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5f39-174">如果表列是计算列，则 **“列数据类型”** 显示为“计算列”。</span><span class="sxs-lookup"><span data-stu-id="b5f39-174">If the table column is a computed column, **Column Data Type** displays "computed column."</span></span>  
  
 <span data-ttu-id="b5f39-175">**允许在移动索引时在线处理 DML 语句**</span><span class="sxs-lookup"><span data-stu-id="b5f39-175">**Allow online processing of DML statements while moving the index**</span></span>  
 <span data-ttu-id="b5f39-176">在索引操作过程中，允许用户访问基础表或聚集索引数据以及任何相关联的非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="b5f39-176">Allows users to access the underlying table or clustered index data and any associated nonclustered indexes during the index operation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5f39-177">此选项对 XML 索引不可用，或者如果索引为禁用的聚集索引，此选项也不可用。</span><span class="sxs-lookup"><span data-stu-id="b5f39-177">This option is not available for XML indexes, or if the index is a disabled clustered index.</span></span>  
  
 <span data-ttu-id="b5f39-178">**设置最大并行度**</span><span class="sxs-lookup"><span data-stu-id="b5f39-178">**Set maximum degree of parallelism**</span></span>  
 <span data-ttu-id="b5f39-179">限制执行并行计划时所使用的处理器数。</span><span class="sxs-lookup"><span data-stu-id="b5f39-179">Limits the number of processors to use during parallel plan execution.</span></span> <span data-ttu-id="b5f39-180">默认值为 0，表示使用实际可用的 CPU 数。</span><span class="sxs-lookup"><span data-stu-id="b5f39-180">The default value, 0, uses the actual number of available CPUs.</span></span> <span data-ttu-id="b5f39-181">若将此值设置为 1，则取消生成并行计划；若将此值设置为大于 1 的数，则会限制单个查询执行使用的最多处理器数。</span><span class="sxs-lookup"><span data-stu-id="b5f39-181">Setting the value to 1 suppresses parallel plan generation; setting the value to a number greater than 1 restricts the maximum number of processors used by a single query execution.</span></span> <span data-ttu-id="b5f39-182">该选项仅在此对话框处于 **“重新生成”** 或 **“重新创建”** 状态时才可用。</span><span class="sxs-lookup"><span data-stu-id="b5f39-182">This option only becomes available if the dialog box is in the **Rebuild** or **Recreate** state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5f39-183">如果指定的值比可用 CPU 数大，则将使用实际的可用 CPU 数。</span><span class="sxs-lookup"><span data-stu-id="b5f39-183">If a value greater than the number of available CPUs is specified, the actual number of available CPUs is used.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b5f39-184">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b5f39-184">Using Transact-SQL</span></span>  
  
#### <a name="to-move-an-existing-index-to-a-different-filegroup"></a><span data-ttu-id="b5f39-185">将现有索引移动到其他文件组中</span><span class="sxs-lookup"><span data-stu-id="b5f39-185">To move an existing index to a different filegroup</span></span>  
  
1.  <span data-ttu-id="b5f39-186">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="b5f39-186">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b5f39-187">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b5f39-187">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b5f39-188">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="b5f39-188">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Creates the TransactionsFG1 filegroup on the AdventureWorks2012 database  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP TransactionsFG1;  
    GO  
    /* Adds the TransactionsFG1dat3 file to the TransactionsFG1 filegroup. Please note that you will have to change the filename parameter in this statement to execute it without errors.  
    */  
    ALTER DATABASE AdventureWorks2012   
    ADD FILE   
    (  
        NAME = TransactionsFG1dat3,  
        FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\TransactionsFG1dat3.ndf',  
        SIZE = 5MB,  
        MAXSIZE = 100MB,  
        FILEGROWTH = 5MB  
    )  
    TO FILEGROUP TransactionsFG1;  
    GO  
    /*Creates the IX_Employee_OrganizationLevel_OrganizationNode index  
      on the TransactionsPS1 filegroup and drops the original IX_Employee_OrganizationLevel_OrganizationNode index.  
    */  
    CREATE NONCLUSTERED INDEX IX_Employee_OrganizationLevel_OrganizationNode  
        ON HumanResources.Employee (OrganizationLevel, OrganizationNode)  
        WITH (DROP_EXISTING = ON)  
        ON TransactionsFG1;  
    GO  
    ```  
  
 <span data-ttu-id="b5f39-189">有关详细信息，请参阅 [CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b5f39-189">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
