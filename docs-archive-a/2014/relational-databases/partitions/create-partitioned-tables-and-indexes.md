---
title: 创建已分区表和已分区索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.createpartition.partitionscheme.f1
- sql12.swb.createpartition.selectoutput.f1
- sql12.swb.createpartition.finish.f1
- sql12.swb.createpartition.summary.f1
- sql12.swb.createpartition.mappartition.f1
- sql12.swb.createpartition.partitioncolumn.f1
- sql12.swb.createpartition.progress.f1
- sql12.swb.createpartition.createjob.f1
- sql12.swb.createpartition.getstart.f1
- sql12.swb.createpartition.partitionfunction.f1
helpviewer_keywords:
- partitioned indexes [SQL Server], creating
- partition schemes [SQL Server], creating
- partition functions [SQL Server], creating
- partitioned tables [SQL Server], creating
- partition functions [SQL Server]
- partition schemes [SQL Server]
ms.assetid: 7641df10-1921-42a7-ba6e-4cb03b3ba9c8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 76ccd8b784902f8542f06f3823e5f8dcb78e9201
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580701"
---
# <a name="create-partitioned-tables-and-indexes"></a><span data-ttu-id="62136-102">创建已分区表和已分区索引</span><span class="sxs-lookup"><span data-stu-id="62136-102">Create Partitioned Tables and Indexes</span></span>
  <span data-ttu-id="62136-103">可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中创建已分区表或索引。</span><span class="sxs-lookup"><span data-stu-id="62136-103">You can create a partitioned table or index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="62136-104">已分区表和索引中的数据水平划分到可分散到数据库的多个文件组的单元中。</span><span class="sxs-lookup"><span data-stu-id="62136-104">The data in partitioned tables and indexes is horizontally divided into units that can be spread across more than one filegroup in a database.</span></span> <span data-ttu-id="62136-105">分区可以使大型表和索引更易于管理并且更灵活。</span><span class="sxs-lookup"><span data-stu-id="62136-105">Partitioning can make large tables and indexes more manageable and scalable.</span></span>  
  
 <span data-ttu-id="62136-106">创建已分区表或索引通常包含四个操作：</span><span class="sxs-lookup"><span data-stu-id="62136-106">Creating a partitioned table or index typically happens in four parts:</span></span>  
  
1.  <span data-ttu-id="62136-107">创建将持有分区方案所指定的分区的文件组和相应的文件。</span><span class="sxs-lookup"><span data-stu-id="62136-107">Create a filegroup or filegroups and corresponding files that will hold the partitions specified by the partition scheme.</span></span>  
  
2.  <span data-ttu-id="62136-108">创建一个分区函数，该函数根据指定列的值将表或索引的各行映射到分区。</span><span class="sxs-lookup"><span data-stu-id="62136-108">Create a partition function that maps the rows of a table or index into partitions based on the values of a specified column.</span></span>  
  
3.  <span data-ttu-id="62136-109">创建一个将已分区表或已分区索引的分区映射到新文件组的分区方案。</span><span class="sxs-lookup"><span data-stu-id="62136-109">Create a partition scheme that maps the partitions of a partitioned table or index to the new filegroups.</span></span>  
  
4.  <span data-ttu-id="62136-110">创建或修改表或索引，并指定分区方案作为存储位置。</span><span class="sxs-lookup"><span data-stu-id="62136-110">Create or modify a table or index and specify the partition scheme as the storage location.</span></span>  
  
 <span data-ttu-id="62136-111">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="62136-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="62136-112">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="62136-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="62136-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="62136-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="62136-114">安全性</span><span class="sxs-lookup"><span data-stu-id="62136-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="62136-115">**创建已分区表或索引，使用：**</span><span class="sxs-lookup"><span data-stu-id="62136-115">**To create a partitioned table or index, using:**</span></span>  
  
     [<span data-ttu-id="62136-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="62136-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="62136-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="62136-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="62136-118">开始之前</span><span class="sxs-lookup"><span data-stu-id="62136-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="62136-119">限制和局限</span><span class="sxs-lookup"><span data-stu-id="62136-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="62136-120">分区函数和方案的作用域被限制为在其中创建它们的数据库。</span><span class="sxs-lookup"><span data-stu-id="62136-120">The scope of a partition function and scheme is limited to the database in which they have been created.</span></span> <span data-ttu-id="62136-121">在该数据库内，分区函数驻留在与其他函数的命名空间不同的一个单独命名空间内。</span><span class="sxs-lookup"><span data-stu-id="62136-121">Within the database, partition functions reside in a separate namespace from other functions.</span></span>  
  
-   <span data-ttu-id="62136-122">如果分区函数中的任何行具有带 Null 值的分区列，会将这些行分配到最左侧分区。</span><span class="sxs-lookup"><span data-stu-id="62136-122">If any rows within a partition function have partitioning columns with null values, these rows are allocated to the left-most partition.</span></span> <span data-ttu-id="62136-123">但是，如果将 NULL 指定为边界值并指示 RIGHT，则最左侧的分区仍为空，NULL 值位于第二个分区。</span><span class="sxs-lookup"><span data-stu-id="62136-123">However, if NULL is specified as a boundary value and RIGHT is indicated, the left-most partition remains empty and NULL values are placed in the second partition.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="62136-124">Security</span><span class="sxs-lookup"><span data-stu-id="62136-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="62136-125">权限</span><span class="sxs-lookup"><span data-stu-id="62136-125">Permissions</span></span>  
 <span data-ttu-id="62136-126">创建已分区表需要在数据库中具有 CREATE TABLE 权限，对在其中创建表的架构具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="62136-126">Creating a partitioned table requires CREATE TABLE permission in the database and ALTER permission on the schema in which the table is being created.</span></span> <span data-ttu-id="62136-127">创建已分区索引需要对要创建索引的表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="62136-127">Creating a partitioned index requires ALTER permission on the table or view where the index is being created.</span></span> <span data-ttu-id="62136-128">创建已分区表或索引需要以下附加权限之一：</span><span class="sxs-lookup"><span data-stu-id="62136-128">Creating either a partitioned table or index requires any one of the following additional permissions:</span></span>  
  
-   <span data-ttu-id="62136-129">ALTER ANY DATASPACE 权限。</span><span class="sxs-lookup"><span data-stu-id="62136-129">ALTER ANY DATASPACE permission.</span></span> <span data-ttu-id="62136-130">默认情况下，此权限授予 **sysadmin** 固定服务器角色和 **db_owner** 及 **db_ddladmin** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="62136-130">This permission defaults to members of the **sysadmin** fixed server role and the **db_owner** and **db_ddladmin** fixed database roles.</span></span>  
  
-   <span data-ttu-id="62136-131">对在其中创建分区函数和分区方案的数据库的 CONTROL 或 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="62136-131">CONTROL or ALTER permission on the database in which the partition function and partition scheme are being created.</span></span>  
  
-   <span data-ttu-id="62136-132">对在其中创建分区函数和分区方案的数据库所在服务器的 CONTROL SERVER 或 ALTER ANY DATABASE 权限。</span><span class="sxs-lookup"><span data-stu-id="62136-132">CONTROL SERVER or ALTER ANY DATABASE permission on the server of the database in which the partition function and partition scheme are being created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="62136-133">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="62136-133">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="62136-134">按此过程中的步骤创建一个或多个文件组、相应文件和一个表。</span><span class="sxs-lookup"><span data-stu-id="62136-134">Follow the steps in this procedure to create one or more filegroups, corresponding files, and a table.</span></span> <span data-ttu-id="62136-135">创建已分区表时，您将在下一个过程中引用这些对象。</span><span class="sxs-lookup"><span data-stu-id="62136-135">You will reference these objects in the next procedure when you create the partitioned table.</span></span>  
  
#### <a name="to-create-new-filegroups-for-a-partitioned-table"></a><span data-ttu-id="62136-136">创建已分区表的新文件组</span><span class="sxs-lookup"><span data-stu-id="62136-136">To create new filegroups for a partitioned table</span></span>  
  
1.  <span data-ttu-id="62136-137">在对象资源管理器中，右键单击要创建已分区表的数据库，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="62136-137">In Object Explorer, right-click the database in which you want to create a partitioned table and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="62136-138">在“数据库属性 - database_name”对话框中的“选择页面”下，选择“文件组”     。</span><span class="sxs-lookup"><span data-stu-id="62136-138">In the **Database Properties -** *database_name* dialog box, under **Select a page**, select **Filegroups**.</span></span>  
  
3.  <span data-ttu-id="62136-139">在 **“行”** 下单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="62136-139">Under **Rows**, click **Add**.</span></span> <span data-ttu-id="62136-140">在新行中，输入文件组名称。</span><span class="sxs-lookup"><span data-stu-id="62136-140">In the new row, enter the filegroup name.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="62136-141">当创建分区时，除了为边界值指定的文件组数外，还必须始终具有一个额外的文件组。</span><span class="sxs-lookup"><span data-stu-id="62136-141">You must always have one extra filegroup in addition to the number of filegroups specified for the boundary values when you are creating partitions.</span></span>  
  
4.  <span data-ttu-id="62136-142">继续添加行，直到您创建了已分区表的所有文件组。</span><span class="sxs-lookup"><span data-stu-id="62136-142">Continue adding rows until you have created all of the filegroups for the partitioned table.</span></span>  
  
5.  <span data-ttu-id="62136-143">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="62136-143">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="62136-144">在 **“选择页”** 下，选择 **“文件”** 。</span><span class="sxs-lookup"><span data-stu-id="62136-144">Under **Select a page**, select **Files**.</span></span>  
  
7.  <span data-ttu-id="62136-145">在 **“行”** 下单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="62136-145">Under **Rows**, click **Add**.</span></span> <span data-ttu-id="62136-146">在新行中，输入文件名并选择文件组。</span><span class="sxs-lookup"><span data-stu-id="62136-146">In the new row, enter a filename and select a filegroup.</span></span>  
  
8.  <span data-ttu-id="62136-147">继续添加行，直到为每个文件组至少创建了一个文件。</span><span class="sxs-lookup"><span data-stu-id="62136-147">Continue adding rows until you have created at least one file for each filegroup.</span></span>  
  
9. <span data-ttu-id="62136-148">展开 **“表”** 文件夹，并按常规方式创建一个表。</span><span class="sxs-lookup"><span data-stu-id="62136-148">Expand the **Tables** folder and create a table as you normally would.</span></span> <span data-ttu-id="62136-149">有关详细信息，请参阅[创建表（数据库引擎）](../tables/create-tables-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="62136-149">For more information, see [Create Tables &#40;Database Engine&#41;](../tables/create-tables-database-engine.md).</span></span> <span data-ttu-id="62136-150">或者，您可以在下一过程中指定现有的表。</span><span class="sxs-lookup"><span data-stu-id="62136-150">Alternatively, you can specify an existing table in the next procedure.</span></span>  
  
#### <a name="to-create-a-partitioned-table"></a><span data-ttu-id="62136-151">创建已分区表</span><span class="sxs-lookup"><span data-stu-id="62136-151">To create a partitioned table</span></span>  
  
1.  <span data-ttu-id="62136-152">右键单击要分区的表，指向“存储”，然后单击“创建分区…”   。</span><span class="sxs-lookup"><span data-stu-id="62136-152">Right-click the table that you wish to partition, point to **Storage**, and then click **Create Partition...**.</span></span>  
  
2.  <span data-ttu-id="62136-153">在 **“创建分区向导”** 的 **“欢迎使用创建分区向导”** 页上，单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="62136-153">In the **Create Partition Wizard**, on the **Welcome to the Create Partition Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="62136-154">在 **“选择分区列”** 页的 **“可用分区列”** 网格中，选择要对表分区的列。</span><span class="sxs-lookup"><span data-stu-id="62136-154">On the **Select a Partitioning Column** page, in the **Available partitioning columns** grid, select the column on which you want to partition your table.</span></span> <span data-ttu-id="62136-155">**“可用分区列”** 网格只显示其数据类型可以用于对数据进行分区的列。</span><span class="sxs-lookup"><span data-stu-id="62136-155">Only columns with data types that can be used to partition data will be displayed in the **Available partitioning columns** grid.</span></span> <span data-ttu-id="62136-156">如果选择计算列作为分区列，必须将该列指定为持久化列。</span><span class="sxs-lookup"><span data-stu-id="62136-156">If you select a computed column as the partitioning column, the column must be designated as a persisted column.</span></span>  
  
     <span data-ttu-id="62136-157">可供选择的分区列和值范围主要由数据按逻辑方式可分组的范围所决定。</span><span class="sxs-lookup"><span data-stu-id="62136-157">The choices you have for the partitioning column and the values range are determined primarily by the extent to which your data can be grouped in a logical way.</span></span> <span data-ttu-id="62136-158">例如，您可以选择按一年的月份数或季度数将数据分成逻辑组。</span><span class="sxs-lookup"><span data-stu-id="62136-158">For example, you may choose to divide your data into logical groupings by months or quarters of a year.</span></span> <span data-ttu-id="62136-159">您计划对数据进行的查询将确定此逻辑组对于管理表分区是否足够。</span><span class="sxs-lookup"><span data-stu-id="62136-159">The queries you plan to make against your data will determine whether this logical grouping is adequate for managing your table partitions.</span></span> <span data-ttu-id="62136-160">当用作分区列时，除 `text`、`ntext`、`image`、`xml`、`timestamp`、`varchar(max)`、`nvarchar(max)`、`varbinary(max)`、别名数据类型或 CLR 用户定义数据类型外，所有数据类型均有效。</span><span class="sxs-lookup"><span data-stu-id="62136-160">All data types are valid for use as partitioning columns, except `text`, `ntext`, `image`, `xml`, `timestamp`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, alias data types, or CLR user-defined data types.</span></span>  
  
     <span data-ttu-id="62136-161">此页还提供以下附加选项：</span><span class="sxs-lookup"><span data-stu-id="62136-161">The following additional options are available on this page:</span></span>  
  
     <span data-ttu-id="62136-162">**将此表与选定的已分区表并置**</span><span class="sxs-lookup"><span data-stu-id="62136-162">**Collocate this table to the selected partitioned table**</span></span>  
     <span data-ttu-id="62136-163">允许您选择一个已分区表，其中包含根据分区列要与此表相联接的相关数据。</span><span class="sxs-lookup"><span data-stu-id="62136-163">Allows you to select a partitioned table that contains related data to join with this table on the partitioning column.</span></span> <span data-ttu-id="62136-164">对于其分区已按分区列联接的表，通常可以更有效地进行查询。</span><span class="sxs-lookup"><span data-stu-id="62136-164">Tables with partitions joined on the partitioning columns are typically queried more efficiently.</span></span>  
  
     <span data-ttu-id="62136-165">**将非唯一索引和唯一索引的存储空间调整为与索引分区列一致**</span><span class="sxs-lookup"><span data-stu-id="62136-165">**Storage-align non-unique indexes and unique indexes with an indexed partition column**</span></span>  
     <span data-ttu-id="62136-166">将已分区表的所有索引调整为与同一分区方案一致。</span><span class="sxs-lookup"><span data-stu-id="62136-166">Aligns all indexes of the table that are partitioned with the same partition scheme.</span></span> <span data-ttu-id="62136-167">当表及其索引对齐时，由于数据是使用同一算法进行分区的，所以您可以更高效地在已分区表中移入和移出分区。</span><span class="sxs-lookup"><span data-stu-id="62136-167">When a table and its indexes are aligned, you can move partitions in and out of partitioned tables more effectively, because your data is partitioned with the same algorithm.</span></span>  
  
     <span data-ttu-id="62136-168">选择分区列和任意其他选项后，单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="62136-168">After selecting the partitioning column and any other options, click **Next**.</span></span>  
  
4.  <span data-ttu-id="62136-169">在 **“选择分区函数”** 页的 **“选择分区函数”** 下，单击 **“新建分区函数”** 或 **“现有分区函数”** 。</span><span class="sxs-lookup"><span data-stu-id="62136-169">On the **Select a Partition Function** page, under **Select partition function**, click either **New partition function** or **Existing partition function**.</span></span> <span data-ttu-id="62136-170">如果选择 **“新建分区函数”** ，则输入函数的名称。</span><span class="sxs-lookup"><span data-stu-id="62136-170">If you choose **New partition function**, enter the name of the function.</span></span> <span data-ttu-id="62136-171">如果选择“现有分区函数”，则从列表中选择要使用的函数名称  。</span><span class="sxs-lookup"><span data-stu-id="62136-171">If you choose **Existing partition function**, select the name of the function you'd like to use from the list.</span></span> <span data-ttu-id="62136-172">如果数据库中没有其他分区函数， **“现有分区函数”** 选项将不可用。</span><span class="sxs-lookup"><span data-stu-id="62136-172">The **Existing partition function** option will not be available if there are no other partition functions on the database.</span></span>  
  
     <span data-ttu-id="62136-173">完成此页后，单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="62136-173">After completing this page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="62136-174">在 **“选择分区方案”** 页的 **“选择分区方案”** 下，单击 **“新建分区方案”** 或 **“现有分区方案”** 。</span><span class="sxs-lookup"><span data-stu-id="62136-174">On the **Select a Partition Scheme** page, under **Select partition scheme**, click either **New partition scheme** or **Existing partition scheme**.</span></span> <span data-ttu-id="62136-175">如果选择 **“新建分区方案”** ，则输入方案的名称。</span><span class="sxs-lookup"><span data-stu-id="62136-175">If you choose **New partition scheme**, enter the name of the scheme.</span></span> <span data-ttu-id="62136-176">如果选择“现有分区方案”，则从列表中选择要使用的方案名称  。</span><span class="sxs-lookup"><span data-stu-id="62136-176">If you choose **Existing partition scheme**, select the name of the scheme you'd like to use from the list.</span></span> <span data-ttu-id="62136-177">如果数据库中没有其他分区方案， **“现有分区方案”** 选项将不可用。</span><span class="sxs-lookup"><span data-stu-id="62136-177">The **Existing partition scheme** option will not be available if there are no other partition schemes on the database.</span></span>  
  
     <span data-ttu-id="62136-178">完成此页后，单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="62136-178">After completing this page, click **Next**.</span></span>  
  
6.  <span data-ttu-id="62136-179">在 **“映射分区”** 页的 **“范围”** 下，选择 **“左边界”** 或 **“右边界”** 以指定在创建的每个文件组内是包括最高边界值还是最低边界值。</span><span class="sxs-lookup"><span data-stu-id="62136-179">On the **Map Partitions** page, under **Range**, select either **Left boundary** or **Right boundary** to specify whether to include the highest or lowest bounding value within each filegroup you create.</span></span> <span data-ttu-id="62136-180">当创建分区时，除了为边界值指定的文件组数外，还必须始终输入一个额外的文件组。</span><span class="sxs-lookup"><span data-stu-id="62136-180">You must always enter one extra filegroup in addition to the number of filegroups specified for the boundary values when you are creating partitions.</span></span>  
  
     <span data-ttu-id="62136-181">在 **“选择文件组并指定边界值”** 网格的 **“文件组”** 下，选择要对数据进行分区的文件组。</span><span class="sxs-lookup"><span data-stu-id="62136-181">In the **Select filegroups and specify boundary values** grid, under **Filegroup**, select the filegroup into which you want to partition your data.</span></span> <span data-ttu-id="62136-182">在 **“边界”** 下，输入每个文件组的边界值。</span><span class="sxs-lookup"><span data-stu-id="62136-182">Under **Boundary**, enter the boundary value for each filegroup.</span></span> <span data-ttu-id="62136-183">如果边界值为左侧空，则分区函数使用分区函数名称将整个表或索引映射到单个分区。</span><span class="sxs-lookup"><span data-stu-id="62136-183">If boundary value is left empty, the partition function maps the whole table or index into a single partition using the partition function name.</span></span>  
  
     <span data-ttu-id="62136-184">此页还提供以下附加选项：</span><span class="sxs-lookup"><span data-stu-id="62136-184">The following additional options are available on this page:</span></span>  
  
     <span data-ttu-id="62136-185">**设置边界…**</span><span class="sxs-lookup"><span data-stu-id="62136-185">**Set Boundaries...**</span></span>  
     <span data-ttu-id="62136-186">打开 **“设置边界值”** 对话框可以为分区选择所需的边界值和日期范围。</span><span class="sxs-lookup"><span data-stu-id="62136-186">Opens the **Set Boundary Values** dialog box to select the boundary values and date ranges you want for your partitions.</span></span> <span data-ttu-id="62136-187">仅在您选择了包含以下数据类型之一的分区列时，此选项才可用：`date`、`datetime`、`smalldatetime`、`datetime2` 或 `datetimeoffset`。</span><span class="sxs-lookup"><span data-stu-id="62136-187">This option is only available when you have selected a partitioning column that contains one of the following data types: `date`, `datetime`, `smalldatetime`, `datetime2`, or `datetimeoffset`.</span></span>  
  
     <span data-ttu-id="62136-188">**预计存储空间**</span><span class="sxs-lookup"><span data-stu-id="62136-188">**Estimate storage**</span></span>  
     <span data-ttu-id="62136-189">估计为分区指定的每个文件组的存储空间的行计数、所需空间和可用空间。</span><span class="sxs-lookup"><span data-stu-id="62136-189">Estimates rowcount, required space, and available space for storage for each filegroup specified for the partitions.</span></span> <span data-ttu-id="62136-190">这些值将以只读值形式显示在网格中。</span><span class="sxs-lookup"><span data-stu-id="62136-190">These values are displayed in the grid as read-only values.</span></span>  
  
     <span data-ttu-id="62136-191">**“设置边界值”** 对话框允许包含以下附加选项：</span><span class="sxs-lookup"><span data-stu-id="62136-191">The **Set Boundary Values** dialog box allows for the following additional options:</span></span>  
  
     <span data-ttu-id="62136-192">**开始日期**</span><span class="sxs-lookup"><span data-stu-id="62136-192">**Start date**</span></span>  
     <span data-ttu-id="62136-193">选择分区范围值的开始日期。</span><span class="sxs-lookup"><span data-stu-id="62136-193">Selects the starting date for the range values of your partitions.</span></span>  
  
     <span data-ttu-id="62136-194">**结束日期**</span><span class="sxs-lookup"><span data-stu-id="62136-194">**End date**</span></span>  
     <span data-ttu-id="62136-195">选择分区范围值的结束日期。</span><span class="sxs-lookup"><span data-stu-id="62136-195">Selects the ending date for the range values of your partitions.</span></span> <span data-ttu-id="62136-196">如果在“映射分区”页上选择了“左边界”，此日期将是每个文件组/分区的最后一个值。</span><span class="sxs-lookup"><span data-stu-id="62136-196">If you selected **Left boundary** on the **Map Partitions** page, this date will be the last value for each filegroup/partition.</span></span> <span data-ttu-id="62136-197">如果在“映射分区”页上选择了“右边界”，此日期将是倒数第二个文件组中的第一个值。</span><span class="sxs-lookup"><span data-stu-id="62136-197">If you selected **Right boundary** on the **Map Partitions** page, this date will be the first value in the next-to-last filegroup.</span></span>  
  
     <span data-ttu-id="62136-198">**日期范围**</span><span class="sxs-lookup"><span data-stu-id="62136-198">**Date range**</span></span>  
     <span data-ttu-id="62136-199">为每个分区选择所需的日期粒度或范围值增量。</span><span class="sxs-lookup"><span data-stu-id="62136-199">Selects the date granularity or range value increment you want for each partition.</span></span>  
  
     <span data-ttu-id="62136-200">完成此页后，单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="62136-200">After completing this page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="62136-201">在 **“选择输出选项”** 页上，指定要如何完成已分区表。</span><span class="sxs-lookup"><span data-stu-id="62136-201">In the **Select an Output Option** page, specify how you want to complete your partitioned table.</span></span> <span data-ttu-id="62136-202">选择 **“创建脚本”** 可以基于向导中的前一页创建 SQL 脚本。</span><span class="sxs-lookup"><span data-stu-id="62136-202">Select **Create Script** to create a SQL script based the previous pages in the wizard.</span></span> <span data-ttu-id="62136-203">选择 **“立即运行”** 可以在完成向导中的其余页后创建新的已分区表。</span><span class="sxs-lookup"><span data-stu-id="62136-203">Select **Run immediately** to create the new partitioned table after completing all remaining pages in the wizard.</span></span> <span data-ttu-id="62136-204">选择 **“计划”** 可以在将来的预定时间创建新的已分区表。</span><span class="sxs-lookup"><span data-stu-id="62136-204">Select **Schedule** to create the new partitioned table at a predetermined time in the future.</span></span>  
  
     <span data-ttu-id="62136-205">如果选择 **“创建脚本”** ， **“脚本选项”** 下的以下选项将可用：</span><span class="sxs-lookup"><span data-stu-id="62136-205">If you select **Create script**, the following options are available under **Script options**:</span></span>  
  
     <span data-ttu-id="62136-206">**将脚本保存到文件**</span><span class="sxs-lookup"><span data-stu-id="62136-206">**Script to file**</span></span>  
     <span data-ttu-id="62136-207">将脚本生成为 .sql 文件。</span><span class="sxs-lookup"><span data-stu-id="62136-207">Generates the script as a .sql file.</span></span> <span data-ttu-id="62136-208">在 **“文件名”** 框中输入文件名和位置，或单击 **“浏览”** 以打开 **“脚本文件位置”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="62136-208">Enter a file name and location in the **File name** box or click **Browse** to open the **Script File Location** dialog box.</span></span> <span data-ttu-id="62136-209">从 **“另存为”** 选择 **“Unicode 文本”** 或 **“ANSI 文本”** 。</span><span class="sxs-lookup"><span data-stu-id="62136-209">From **Save As**, select **Unicode text** or **ANSI text**.</span></span>  
  
     <span data-ttu-id="62136-210">**将脚本保存到剪贴板**</span><span class="sxs-lookup"><span data-stu-id="62136-210">**Script to Clipboard**</span></span>  
     <span data-ttu-id="62136-211">将脚本保存到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="62136-211">Saves the script to the Clipboard.</span></span>  
  
     <span data-ttu-id="62136-212">**将脚本保存到“新建查询”窗口**</span><span class="sxs-lookup"><span data-stu-id="62136-212">**Script to New Query Window**</span></span>  
     <span data-ttu-id="62136-213">将脚本生成到新的查询编辑器窗口。</span><span class="sxs-lookup"><span data-stu-id="62136-213">Generates the script to a new Query Editor window.</span></span> <span data-ttu-id="62136-214">这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="62136-214">This is the default selection.</span></span>  
  
     <span data-ttu-id="62136-215">如果选择 **“计划”** ，则单击 **“更改计划”** 。</span><span class="sxs-lookup"><span data-stu-id="62136-215">If you select **Schedule**, click **Change schedule**.</span></span>  
  
    1.  <span data-ttu-id="62136-216">在“新建作业计划”对话框的“名称”框中，输入作业计划的名称   。</span><span class="sxs-lookup"><span data-stu-id="62136-216">In the **New Job Schedule** dialog box, in the **Name** box, enter the job schedule's name.</span></span>  
  
    2.  <span data-ttu-id="62136-217">在 **“计划类型”** 列表中选择计划类型：</span><span class="sxs-lookup"><span data-stu-id="62136-217">On the **Schedule type** list, select the type of schedule:</span></span>  
  
        -   <span data-ttu-id="62136-218">**SQL Server 代理启动时自动启动**</span><span class="sxs-lookup"><span data-stu-id="62136-218">**Start automatically when SQL Server Agent starts**</span></span>  
  
        -   <span data-ttu-id="62136-219">**CPU 空闲时启动**</span><span class="sxs-lookup"><span data-stu-id="62136-219">**Start whenever the CPUs become idle**</span></span>  
  
        -   <span data-ttu-id="62136-220">**重复执行**。</span><span class="sxs-lookup"><span data-stu-id="62136-220">**Recurring**.</span></span> <span data-ttu-id="62136-221">如果新的已分区表定期使用新信息更新，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="62136-221">Select this option if your new partitioned table updates with new information on a regular basis.</span></span>  
  
        -   <span data-ttu-id="62136-222">**执行一次**。</span><span class="sxs-lookup"><span data-stu-id="62136-222">**One time**.</span></span> <span data-ttu-id="62136-223">这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="62136-223">This is the default selection.</span></span>  
  
    3.  <span data-ttu-id="62136-224">选择或清除 **“已启用”** 复选框以启用或禁用计划。</span><span class="sxs-lookup"><span data-stu-id="62136-224">Select or clear the **Enabled** check box to enable or disable the schedule.</span></span>  
  
    4.  <span data-ttu-id="62136-225">如果选择 **“重复执行”** ：</span><span class="sxs-lookup"><span data-stu-id="62136-225">If you select **Recurring**:</span></span>  
  
        1.  <span data-ttu-id="62136-226">在 **“频率”** 下的 **“执行”** 列表中，指定执行的频率：</span><span class="sxs-lookup"><span data-stu-id="62136-226">Under **Frequency**, on the **Occurs** list, specify the frequency of occurrence:</span></span>  
  
            -   <span data-ttu-id="62136-227">如果选择 **“每天”** ，请在 **“执行间隔”** 框中输入重复作业计划的频率（天）。</span><span class="sxs-lookup"><span data-stu-id="62136-227">If you select **Daily**, in the **Recurs every** box, enter how often the job schedule repeats in days.</span></span>  
  
            -   <span data-ttu-id="62136-228">如果选择 **“每周”** ，请在 **“执行间隔”** 框中输入重复作业计划的频率（周）。</span><span class="sxs-lookup"><span data-stu-id="62136-228">If you select **Weekly**, in the **Recurs every** box, enter how often the job schedule repeats in weeks.</span></span> <span data-ttu-id="62136-229">选择运行作业计划的一周中的某天或某些天。</span><span class="sxs-lookup"><span data-stu-id="62136-229">Select the day or days of the week on which the job schedule is run.</span></span>  
  
            -   <span data-ttu-id="62136-230">如果选择 **“每月”** ，可以选择 **“天”** 或 **“特定日期”** 。</span><span class="sxs-lookup"><span data-stu-id="62136-230">If you select **Monthly**, select either **Day** or **The**.</span></span>  
  
                -   <span data-ttu-id="62136-231">如果选择 **“天”** ，请输入要运行作业计划的当月日期和作业计划的重复频率（月）。</span><span class="sxs-lookup"><span data-stu-id="62136-231">If you select **Day**, enter both the date of the month you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="62136-232">例如，如果要每隔一个月在当月的 15 日运行计划作业，请选择“天”，在第一个框中输入“15”，在第二个框中输入“2”  。</span><span class="sxs-lookup"><span data-stu-id="62136-232">For example, if you want the job schedule to run on the 15th day of the month every other month, select **Day** and enter "15" in the first box and "2" in the second box.</span></span> <span data-ttu-id="62136-233">请注意，第二个框中允许的最大数是“99”。</span><span class="sxs-lookup"><span data-stu-id="62136-233">Please note that the largest number allowed in the second box is "99".</span></span>  
  
                -   <span data-ttu-id="62136-234">如果选择 **“特定日期”** ，请选择要运行作业计划的当月内一周的特定一天和作业计划的重复频率（月）。</span><span class="sxs-lookup"><span data-stu-id="62136-234">If you select **The**, select the specific day of the week within the month that you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="62136-235">例如，如果要每隔一个月在当月的最后一个工作日运行作业计划，请选择“天”，从第一个列表中选择“最后一周”，从第二个列表中选择“工作日”，然后在最后一个框中输入“2”    。</span><span class="sxs-lookup"><span data-stu-id="62136-235">For example, if you want the job schedule to run on the last weekday of the month every other month, select **Day**, select **last** from the first list and **weekday** from the second list, and then enter "2" in the last box.</span></span> <span data-ttu-id="62136-236">还可以从前两个列表中选择“第一周”  、“第二周”  、“第三周”  或“第四周”  以及特定工作日（例如星期日或星期三）。</span><span class="sxs-lookup"><span data-stu-id="62136-236">You can also select **first**, **second**, **third**, or **fourth**, as well as specific weekdays (for example: Sunday or Wednesday) from the first two lists.</span></span> <span data-ttu-id="62136-237">请注意，最后一个框中允许的最大数是“99”。</span><span class="sxs-lookup"><span data-stu-id="62136-237">Please note that the largest number allowed in the last box is "99".</span></span>  
  
        2.  <span data-ttu-id="62136-238">在 **“每天频率”** 下，指定作业计划运行的当天作业计划的重复频率。</span><span class="sxs-lookup"><span data-stu-id="62136-238">Under **Daily frequency**, specify how often the job schedule repeats on the day the job schedule runs:</span></span>  
  
            -   <span data-ttu-id="62136-239">如果选择 **“执行一次，时间为:”** ，请在 **“执行一次，时间为:”** 框中输入运行作业计划的当天的特定时间。</span><span class="sxs-lookup"><span data-stu-id="62136-239">If you select **Occurs once at**, enter the specific time of day when the job schedule should run in the **Occurs once at** box.</span></span> <span data-ttu-id="62136-240">输入当天的小时、分钟和秒以及 AM 或 PM。</span><span class="sxs-lookup"><span data-stu-id="62136-240">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
            -   <span data-ttu-id="62136-241">如果选择 **“执行间隔”** ，请在 **“频率”** 下指定所选日运行作业计划的频率。</span><span class="sxs-lookup"><span data-stu-id="62136-241">If you select **Occurs every**, specify how often the job schedule runs during the day chosen under **Frequency**.</span></span> <span data-ttu-id="62136-242">例如，如果要在运行作业计划的当天每隔 2 小时重复一次，请选择“执行间隔”，在第一个框中输入“2”，然后从列表中选择“小时”   。</span><span class="sxs-lookup"><span data-stu-id="62136-242">For example, if you want the job schedule to repeat every 2 hours during the day that the job schedule is run, select **Occurs every**, enter "2" in the first box, and then select **hour(s)** from the list.</span></span> <span data-ttu-id="62136-243">从此列表中还可以选择“分钟”  和“秒”  。</span><span class="sxs-lookup"><span data-stu-id="62136-243">From this list you can also select **minute(s)** and **second(s)**.</span></span> <span data-ttu-id="62136-244">请注意，第一个框中允许的最大数是“100”。</span><span class="sxs-lookup"><span data-stu-id="62136-244">Please note that the largest number allowed in the first box is "100".</span></span>  
  
                 <span data-ttu-id="62136-245">在 **“开始时间”** 框中，输入开始运行作业计划的时间。</span><span class="sxs-lookup"><span data-stu-id="62136-245">In the **Starting at** box, enter the time that the job schedule should start running.</span></span> <span data-ttu-id="62136-246">在 **“结束时间”** 框中，输入停止重复作业计划的时间。</span><span class="sxs-lookup"><span data-stu-id="62136-246">In the **Ending at** box, enter the time that the job schedule should stop repeating.</span></span> <span data-ttu-id="62136-247">输入当天的小时、分钟和秒以及 AM 或 PM。</span><span class="sxs-lookup"><span data-stu-id="62136-247">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
        3.  <span data-ttu-id="62136-248">在 **“持续时间”** 下的 **“开始日期”** 中，输入希望作业计划开始运行的日期。</span><span class="sxs-lookup"><span data-stu-id="62136-248">Under **Duration**, in **Start date**, enter the date that you want the job schedule to start running.</span></span> <span data-ttu-id="62136-249">选择 **“结束日期”** 或 **“无结束日期”** 以指示作业计划应在何时停止运行。</span><span class="sxs-lookup"><span data-stu-id="62136-249">Select **End date** or **No end date** to indicate when the job schedule should stop running.</span></span> <span data-ttu-id="62136-250">如果选择 **“结束日期”** ，输入希望作业计划停止运行的日期。</span><span class="sxs-lookup"><span data-stu-id="62136-250">If you select **End date**, enter the date that you want to job schedule to stop running.</span></span>  
  
    5.  <span data-ttu-id="62136-251">如果选择“执行一次”  ，请在“执行一次”  下的“日期”  框中输入将运行作业计划的日期。</span><span class="sxs-lookup"><span data-stu-id="62136-251">If you select **One Time**, under **One-time occurrence**, in the **Date** box, enter the date that the job schedule will be run.</span></span> <span data-ttu-id="62136-252">在 **“时间”** 框中，输入将运行作业计划的时间。</span><span class="sxs-lookup"><span data-stu-id="62136-252">In the **Time** box, enter the time that the job schedule will be run.</span></span> <span data-ttu-id="62136-253">输入当天的小时、分钟和秒以及 AM 或 PM。</span><span class="sxs-lookup"><span data-stu-id="62136-253">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
    6.  <span data-ttu-id="62136-254">在 **“摘要”** 下的 **“说明”** 中，验证所有作业计划设置均正确。</span><span class="sxs-lookup"><span data-stu-id="62136-254">Under **Summary**, in **Description**, verify that all job schedule settings are correct.</span></span>  
  
    7.  <span data-ttu-id="62136-255">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="62136-255">Click **OK**.</span></span>  
  
     <span data-ttu-id="62136-256">完成此页后，单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="62136-256">After completing this page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="62136-257">在 **“检查摘要”** 页的 **“检查所做选择”** 下，展开所有可用选项以验证所有分区设置是正确的。</span><span class="sxs-lookup"><span data-stu-id="62136-257">On the **Review Summary** page, under **Review your selections**, expand all available options to verify that all partition settings are correct.</span></span> <span data-ttu-id="62136-258">如果一切正常，请单击 **“完成”** 。</span><span class="sxs-lookup"><span data-stu-id="62136-258">If everything is as expected, click **Finish**.</span></span>  
  
9. <span data-ttu-id="62136-259">在 **“创建分区向导进度”** 页上，监视有关创建分区向导的操作的状态信息。</span><span class="sxs-lookup"><span data-stu-id="62136-259">On the **Create Partition Wizard Progress** page, monitor status information about the actions of the Create Partition Wizard.</span></span> <span data-ttu-id="62136-260">根据在向导中选择的选项，“进度”页可能会包含一个操作或多个操作。</span><span class="sxs-lookup"><span data-stu-id="62136-260">Depending on the options that you selected in the wizard, the progress page might contain one or more actions.</span></span> <span data-ttu-id="62136-261">最上面的方框显示向导的总体状态和向导已接收到的状态、错误和警告消息数。</span><span class="sxs-lookup"><span data-stu-id="62136-261">The top box displays the overall status of the wizard and the number of status, error, and warning messages that the wizard has received.</span></span>  
  
     <span data-ttu-id="62136-262">**“创建分区向导进度”** 页上提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="62136-262">The following options are available on the **Create Partition Wizard Progress** page:</span></span>  
  
     <span data-ttu-id="62136-263">**详细信息**</span><span class="sxs-lookup"><span data-stu-id="62136-263">**Details**</span></span>  
     <span data-ttu-id="62136-264">提供向导执行的操作所返回的操作、状态和所有消息。</span><span class="sxs-lookup"><span data-stu-id="62136-264">Provides the action, status, and any messages that are returned from action taken by the wizard.</span></span>  
  
     <span data-ttu-id="62136-265">**Action**</span><span class="sxs-lookup"><span data-stu-id="62136-265">**Action**</span></span>  
     <span data-ttu-id="62136-266">指定每个操作的类型和名称。</span><span class="sxs-lookup"><span data-stu-id="62136-266">Specifies the type and name of each action.</span></span>  
  
     <span data-ttu-id="62136-267">**Status**</span><span class="sxs-lookup"><span data-stu-id="62136-267">**Status**</span></span>  
     <span data-ttu-id="62136-268">指示向导操作作为一个整体返回的值是“成功”  还是“失败”  。</span><span class="sxs-lookup"><span data-stu-id="62136-268">Indicates whether the wizard action as a whole returned the value of **Success** or **Failure**.</span></span>  
  
     <span data-ttu-id="62136-269">**消息**</span><span class="sxs-lookup"><span data-stu-id="62136-269">**Message**</span></span>  
     <span data-ttu-id="62136-270">提供从该进程中返回的任何错误或警告消息。</span><span class="sxs-lookup"><span data-stu-id="62136-270">Provides any error or warning messages that are returned from the process.</span></span>  
  
     <span data-ttu-id="62136-271">**Report**</span><span class="sxs-lookup"><span data-stu-id="62136-271">**Report**</span></span>  
     <span data-ttu-id="62136-272">创建包含创建分区向导结果的报告。</span><span class="sxs-lookup"><span data-stu-id="62136-272">Creates a report that contains the results of the Create Partition Wizard.</span></span> <span data-ttu-id="62136-273">这些选项是 **“查看报告”** 、 **“将报告保存到文件”** 、 **“将报告复制到剪贴板”** 和 **“将报告作为电子邮件发送”** 。</span><span class="sxs-lookup"><span data-stu-id="62136-273">The options are **View Report**, **Save Report to File**, **Copy Report to Clipboard**, and **Send Report as Email**.</span></span>  
  
     <span data-ttu-id="62136-274">**查看报告**</span><span class="sxs-lookup"><span data-stu-id="62136-274">**View Report**</span></span>  
     <span data-ttu-id="62136-275">打开“查看报告”  对话框，其中包含关于创建分区向导进度的文本报告。</span><span class="sxs-lookup"><span data-stu-id="62136-275">Opens the **View Report** dialog box, which contains a text report of the progress of the Create Partition Wizard.</span></span>  
  
     <span data-ttu-id="62136-276">**将报告保存到文件**</span><span class="sxs-lookup"><span data-stu-id="62136-276">**Save Report to File**</span></span>  
     <span data-ttu-id="62136-277">打开“将报告另存为”  对话框。</span><span class="sxs-lookup"><span data-stu-id="62136-277">Opens the **Save Report As** dialog box.</span></span>  
  
     <span data-ttu-id="62136-278">**将报告复制到剪贴板**</span><span class="sxs-lookup"><span data-stu-id="62136-278">**Copy Report to Clipboard**</span></span>  
     <span data-ttu-id="62136-279">将向导的进度报告结果复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="62136-279">Copies the results of the wizard's progress report to the Clipboard.</span></span>  
  
     <span data-ttu-id="62136-280">**“将报告作为电子邮件发送”**</span><span class="sxs-lookup"><span data-stu-id="62136-280">**Send Report as Email**</span></span>  
     <span data-ttu-id="62136-281">将向导的进度报告结果复制到电子邮件。</span><span class="sxs-lookup"><span data-stu-id="62136-281">Copies the results of the wizard's progress report into an email message.</span></span>  
  
     <span data-ttu-id="62136-282">完成时，单击“关闭”  。</span><span class="sxs-lookup"><span data-stu-id="62136-282">When complete, click **Close**.</span></span>  
  
 <span data-ttu-id="62136-283">创建分区向导将创建分区函数和方案，然后将分区应用于指定的表。</span><span class="sxs-lookup"><span data-stu-id="62136-283">The Create Partition Wizard creates the partition function and scheme and then applies the partitioning to the specified table.</span></span> <span data-ttu-id="62136-284">若要验证表分区，请在对象资源管理器中，右键单击表，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="62136-284">To verify the table partitioning, in Object Explorer, right-click the table and select **Properties**.</span></span> <span data-ttu-id="62136-285">单击 **“存储”** 页。</span><span class="sxs-lookup"><span data-stu-id="62136-285">Click the **Storage** page.</span></span> <span data-ttu-id="62136-286">该页面将显示分区函数和方案的名称以及分区数目之类的信息。</span><span class="sxs-lookup"><span data-stu-id="62136-286">The page displays information such as the name of the partition function and scheme and the number of partitions.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="62136-287">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="62136-287">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-partitioned-table"></a><span data-ttu-id="62136-288">创建已分区表</span><span class="sxs-lookup"><span data-stu-id="62136-288">To create a partitioned table</span></span>  
  
1.  <span data-ttu-id="62136-289">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="62136-289">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="62136-290">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="62136-290">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="62136-291">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="62136-291">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="62136-292">该示例将创建新的文件组、分区函数和分区方案。</span><span class="sxs-lookup"><span data-stu-id="62136-292">The example creates new filegroups, a partition function, and a partition scheme.</span></span> <span data-ttu-id="62136-293">将创建一个新表，该表具有指定为存储位置的分区方案。</span><span class="sxs-lookup"><span data-stu-id="62136-293">A new table is created with the partition scheme specified as the storage location.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Adds four new filegroups to the AdventureWorks2012 database  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test1fg;  
    GO  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test2fg;  
    GO  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test3fg;  
    GO  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test4fg;   
  
    -- Adds one file for each filegroup.  
    ALTER DATABASE AdventureWorks2012   
    ADD FILE   
    (  
        NAME = test1dat1,  
        FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\t1dat1.ndf',  
        SIZE = 5MB,  
        MAXSIZE = 100MB,  
        FILEGROWTH = 5MB  
    )  
    TO FILEGROUP test1fg;  
    ALTER DATABASE AdventureWorks2012   
    ADD FILE   
    (  
        NAME = test2dat2,  
        FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\t2dat2.ndf',  
        SIZE = 5MB,  
        MAXSIZE = 100MB,  
        FILEGROWTH = 5MB  
    )  
    TO FILEGROUP test2fg;  
    GO  
    ALTER DATABASE AdventureWorks2012   
    ADD FILE   
    (  
        NAME = test3dat3,  
        FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\t3dat3.ndf',  
        SIZE = 5MB,  
        MAXSIZE = 100MB,  
        FILEGROWTH = 5MB  
    )  
    TO FILEGROUP test3fg;  
    GO  
    ALTER DATABASE AdventureWorks2012   
    ADD FILE   
    (  
        NAME = test4dat4,  
        FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\t4dat4.ndf',  
        SIZE = 5MB,  
        MAXSIZE = 100MB,  
        FILEGROWTH = 5MB  
    )  
    TO FILEGROUP test4fg;  
    GO  
    -- Creates a partition function called myRangePF1 that will partition a table into four partitions  
    CREATE PARTITION FUNCTION myRangePF1 (int)  
        AS RANGE LEFT FOR VALUES (1, 100, 1000) ;  
    GO  
    -- Creates a partition scheme called myRangePS1 that applies myRangePF1 to the four filegroups created above  
    CREATE PARTITION SCHEME myRangePS1  
        AS PARTITION myRangePF1  
        TO (test1fg, test2fg, test3fg, test4fg) ;  
    GO  
    -- Creates a partitioned table called PartitionTable that uses myRangePS1 to partition col1  
    CREATE TABLE PartitionTable (col1 int PRIMARY KEY, col2 char(10))  
        ON myRangePS1 (col1) ;  
    GO  
    ```  
  
#### <a name="to-determine-if-a-table-is-partitioned"></a><span data-ttu-id="62136-294">确定表是否分区</span><span class="sxs-lookup"><span data-stu-id="62136-294">To determine if a table is partitioned</span></span>  
  
1.  <span data-ttu-id="62136-295">如果表 `PartitionTable` 已分区，以下查询将返回一个或多个行。</span><span class="sxs-lookup"><span data-stu-id="62136-295">The following query returns one or more rows if the table `PartitionTable` is partitioned.</span></span> <span data-ttu-id="62136-296">如果表未分区，则不返回任何行。</span><span class="sxs-lookup"><span data-stu-id="62136-296">If the table is not partitioned, no rows are returned.</span></span>  
  
    ```  
    SELECT *   
    FROM sys.tables AS t   
    JOIN sys.indexes AS i   
        ON t.[object_id] = i.[object_id]   
        AND i.[type] IN (0,1)   
    JOIN sys.partition_schemes ps   
        ON i.data_space_id = ps.data_space_id   
    WHERE t.name = 'PartitionTable';   
    GO  
    ```  
  
#### <a name="to-determine-the-boundary-values-for-a-partitioned-table"></a><span data-ttu-id="62136-297">确定已分区表的边界值</span><span class="sxs-lookup"><span data-stu-id="62136-297">To determine the boundary values for a partitioned table</span></span>  
  
1.  <span data-ttu-id="62136-298">以下查询对于 `PartitionTable` 表中的每个分区返回边界值。</span><span class="sxs-lookup"><span data-stu-id="62136-298">The following query returns the boundary values for each partition in the `PartitionTable` table.</span></span>  
  
    ```  
    SELECT t.name AS TableName, i.name AS IndexName, p.partition_number, p.partition_id, i.data_space_id, f.function_id, f.type_desc, r.boundary_id, r.value AS BoundaryValue   
    FROM sys.tables AS t  
    JOIN sys.indexes AS i  
        ON t.object_id = i.object_id  
    JOIN sys.partitions AS p  
        ON i.object_id = p.object_id AND i.index_id = p.index_id   
    JOIN  sys.partition_schemes AS s   
        ON i.data_space_id = s.data_space_id  
    JOIN sys.partition_functions AS f   
        ON s.function_id = f.function_id  
    LEFT JOIN sys.partition_range_values AS r   
        ON f.function_id = r.function_id and r.boundary_id = p.partition_number  
    WHERE t.name = 'PartitionTable' AND i.type <= 1  
    ORDER BY p.partition_number;  
    ```  
  
#### <a name="to-determine-the-partition-column-for-a-partitioned-table"></a><span data-ttu-id="62136-299">确定已分区表的分区列</span><span class="sxs-lookup"><span data-stu-id="62136-299">To determine the partition column for a partitioned table</span></span>  
  
1.  <span data-ttu-id="62136-300">以下查询返回表的分区列的名称。</span><span class="sxs-lookup"><span data-stu-id="62136-300">The following query returns the name of the partitioning column for table.</span></span> <span data-ttu-id="62136-301">`PartitionTable` 列中的一个值匹配。</span><span class="sxs-lookup"><span data-stu-id="62136-301">`PartitionTable`.</span></span>  
  
    ```  
    SELECT   
        t.[object_id] AS ObjectID   
        , t.name AS TableName   
        , ic.column_id AS PartitioningColumnID   
        , c.name AS PartitioningColumnName   
    FROM sys.tables AS t   
    JOIN sys.indexes AS i   
        ON t.[object_id] = i.[object_id]   
        AND i.[type] <= 1 -- clustered index or a heap   
    JOIN sys.partition_schemes AS ps   
        ON ps.data_space_id = i.data_space_id   
    JOIN sys.index_columns AS ic   
        ON ic.[object_id] = i.[object_id]   
        AND ic.index_id = i.index_id   
        AND ic.partition_ordinal >= 1 -- because 0 = non-partitioning column   
    JOIN sys.columns AS c   
        ON t.[object_id] = c.[object_id]   
        AND ic.column_id = c.column_id   
    WHERE t.name = 'PartitionTable' ;   
    GO  
    ```  
  
 <span data-ttu-id="62136-302">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="62136-302">For more information, see:</span></span>  
  
-   [<span data-ttu-id="62136-303">ALTER DATABASE 文件和文件组选项 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="62136-303">ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)  
  
-   [<span data-ttu-id="62136-304">CREATE PARTITION FUNCTION (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="62136-304">CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-partition-function-transact-sql)  
  
-   [<span data-ttu-id="62136-305">CREATE PARTITION SCHEME (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="62136-305">CREATE PARTITION SCHEME &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-partition-scheme-transact-sql)  
  
-   [<span data-ttu-id="62136-306">CREATE TABLE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="62136-306">CREATE TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-table-transact-sql)  
  
  
