---
title: 修改分区函数 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: ae5bfc09-f27a-4ea9-9518-485278b11674
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: bf14e633e62839b1abca7f38f833efab933c18f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687823"
---
# <a name="modify-a-partition-function"></a><span data-ttu-id="fa6c4-102">修改分区函数</span><span class="sxs-lookup"><span data-stu-id="fa6c4-102">Modify a Partition Function</span></span>
  <span data-ttu-id="fa6c4-103">通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在已分区的表或已分区的索引的分区函数中增加或减少指定的分区数（加 1 或减 1），可以更改 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中的表或索引的分区方式。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-103">You can change the way a table or index is partitioned in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by adding or subtracting the number of partitions specified, in increments of 1, in the partition function of the partitioned table or index by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="fa6c4-104">增加分区的方法是将某个现有的分区“拆分”为两个分区并重新定义新分区的边界。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-104">When you add a partition, you do so by "splitting" an existing partition into two partitions and redefining the boundaries of the new partitions.</span></span> <span data-ttu-id="fa6c4-105">减少分区的方法是将两个分区的边界“合并”成一个。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-105">When you drop a partition, you do so by "merging" the boundaries of two partitions into one.</span></span> <span data-ttu-id="fa6c4-106">减少分区操作将重新填充一个分区而不对另一个分区进行分配。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-106">This last action repopulates one partition and leaves the other partition unassigned.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="fa6c4-107">多个表或索引可以使用同一分区函数。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-107">More than one table or index can use the same partition function.</span></span> <span data-ttu-id="fa6c4-108">在修改分区函数时，将影响单个事务中的所有表或索引。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-108">When you modify a partition function, you affect all of them in a single transaction.</span></span> <span data-ttu-id="fa6c4-109">在修改分区函数之前，先检查其依赖关系。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-109">Check the partition function's dependencies before modifying it.</span></span>  
  
 <span data-ttu-id="fa6c4-110">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="fa6c4-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fa6c4-111">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="fa6c4-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fa6c4-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="fa6c4-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="fa6c4-113">安全性</span><span class="sxs-lookup"><span data-stu-id="fa6c4-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fa6c4-114">**若要修改分区函数，可使用：**</span><span class="sxs-lookup"><span data-stu-id="fa6c4-114">**To modify a partition function, using:**</span></span>  
  
     [<span data-ttu-id="fa6c4-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fa6c4-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="fa6c4-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fa6c4-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fa6c4-117">开始之前</span><span class="sxs-lookup"><span data-stu-id="fa6c4-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="fa6c4-118">限制和局限</span><span class="sxs-lookup"><span data-stu-id="fa6c4-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="fa6c4-119">ALTER PARTITION FUNCTION 只能用于将一个分区拆分为两个，或将两个分区合并为一个。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-119">ALTER PARTITION FUNCTION can only be used for splitting one partition into two, or for merging two partitions into one.</span></span> <span data-ttu-id="fa6c4-120">若要更改表或索引的分区方式（例如，从 10 个分区变为 5 个分区），可以使用下列选项之一：</span><span class="sxs-lookup"><span data-stu-id="fa6c4-120">To change the way a table or index is partitioned (from 10 partitions to 5, for example), you can use any one of the following options:</span></span>  
  
    -   <span data-ttu-id="fa6c4-121">使用所需的分区函数创建一个新的已分区表，然后使用 INSERT INTO ...SELECT FROM [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句或者使用 **中的** “管理分区向导” [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]将旧表中的数据插入新表。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-121">Create a new partitioned table with the desired partition function, and then insert the data from the old table into the new table by using either an INSERT INTO ... SELECT FROM [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or the **Manage Partition Wizard** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
    -   <span data-ttu-id="fa6c4-122">为堆创建分区聚集索引。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-122">Create a partitioned clustered index on a heap.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="fa6c4-123">删除已分区的聚集索引将产生分区堆。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-123">Dropping a partitioned clustered index results in a partitioned heap.</span></span>  
  
    -   <span data-ttu-id="fa6c4-124">通过将 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE INDEX 语句与 DROP EXISTING = ON 子句一起使用来删除并重新生成现有的已分区索引。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-124">Drop and rebuild an existing partitioned index by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE INDEX statement with the DROP EXISTING = ON clause.</span></span>  
  
    -   <span data-ttu-id="fa6c4-125">执行一系列 ALTER PARTITION FUNCTION 语句。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-125">Perform a sequence of ALTER PARTITION FUNCTION statements.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fa6c4-126">不对修改分区函数提供复制支持。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-126">does not provide replication support for modifying a partition function.</span></span> <span data-ttu-id="fa6c4-127">如果要对发布数据库中的分区函数进行更改，必须在订阅数据库中手动执行此操作。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-127">If you want to make changes to a partition function in the publication database, you must do this manually in the subscription database.</span></span>  
  
-   <span data-ttu-id="fa6c4-128">ALTER PARTITION FUNCTION 所影响的全部文件组都必须处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-128">All filegroups that are affected by ALTER PARTITION FUNCTION must be online.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fa6c4-129">Security</span><span class="sxs-lookup"><span data-stu-id="fa6c4-129">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fa6c4-130">权限</span><span class="sxs-lookup"><span data-stu-id="fa6c4-130">Permissions</span></span>  
 <span data-ttu-id="fa6c4-131">可以使用以下任意权限执行 ALTER PARTITION FUNCTION：</span><span class="sxs-lookup"><span data-stu-id="fa6c4-131">Any one of the following permissions can be used to execute ALTER PARTITION FUNCTION:</span></span>  
  
-   <span data-ttu-id="fa6c4-132">ALTER ANY DATASPACE 权限。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-132">ALTER ANY DATASPACE permission.</span></span> <span data-ttu-id="fa6c4-133">默认情况下，此权限授予 **sysadmin** 固定服务器角色和 **db_owner** 及 **db_ddladmin** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-133">This permission defaults to members of the **sysadmin** fixed server role and the **db_owner** and **db_ddladmin** fixed database roles.</span></span>  
  
-   <span data-ttu-id="fa6c4-134">对创建分区函数时所在数据库的 CONTROL 或 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-134">CONTROL or ALTER permission on the database in which the partition function was created.</span></span>  
  
-   <span data-ttu-id="fa6c4-135">对包含创建分区函数所在的数据库的服务器具有 CONTROL SERVER 或 ALTER ANY DATABASE 权限。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-135">CONTROL SERVER or ALTER ANY DATABASE permission on the server of the database in which the partition function was created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fa6c4-136">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fa6c4-136">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="fa6c4-137">**修改分区函数：**</span><span class="sxs-lookup"><span data-stu-id="fa6c4-137">**To modify a partition function:**</span></span>  
  
 <span data-ttu-id="fa6c4-138">无法使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]执行此特定操作。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-138">This specific action cannot be performed using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="fa6c4-139">若要修改某个分区函数，您必须先删除该函数，然后通过创建分区向导使用所需属性创建一个新函数。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-139">In order to modify a partition function, you must first delete the function and then create a new one with the desired properties using the Create Partition Wizard.</span></span> <span data-ttu-id="fa6c4-140">有关详细信息，请参阅</span><span class="sxs-lookup"><span data-stu-id="fa6c4-140">For more information, see</span></span>  
  
#### <a name="to-delete-a-partition-function"></a><span data-ttu-id="fa6c4-141">删除分区函数</span><span class="sxs-lookup"><span data-stu-id="fa6c4-141">To delete a partition function</span></span>  
  
1.  <span data-ttu-id="fa6c4-142">展开要从中删除分区函数的数据库，然后展开 **“存储”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-142">Expand the database where you want to delete the partition function and then expand the **Storage** folder.</span></span>  
  
2.  <span data-ttu-id="fa6c4-143">展开 **“分区函数”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-143">Expand the **Partition Functions** folder.</span></span>  
  
3.  <span data-ttu-id="fa6c4-144">右键单击要删除的分区函数，然后选择  “删除”。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-144">Right-click the partition function you want to delete and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="fa6c4-145">在 **“删除对象”** 对话框中，确保已选择正确的分区函数，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-145">In the **Delete Object** dialog box, ensure that the correct partition function is selected, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fa6c4-146">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fa6c4-146">Using Transact-SQL</span></span>  
  
#### <a name="to-split-a-single-partition-into-two-partitions"></a><span data-ttu-id="fa6c4-147">将一个分区拆分为两个分区</span><span class="sxs-lookup"><span data-stu-id="fa6c4-147">To split a single partition into two partitions</span></span>  
  
1.  <span data-ttu-id="fa6c4-148">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-148">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fa6c4-149">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-149">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fa6c4-150">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-150">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Look for a previous version of the partition function "myRangePF1" and deletes it if it is found.  
    IF EXISTS (SELECT * FROM sys.partition_functions  
        WHERE name = 'myRangePF1')  
        DROP PARTITION FUNCTION myRangePF1;  
    GO  
    -- Create a new partition function called "myRangePF1" that partitions a table into four partitions.  
    CREATE PARTITION FUNCTION myRangePF1 (int)  
    AS RANGE LEFT FOR VALUES ( 1, 100, 1000 );  
    GO  
    --Split the partition between boundary_values 100 and 1000  
    --to create two partitions between boundary_values 100 and 500  
    --and between boundary_values 500 and 1000.  
    ALTER PARTITION FUNCTION myRangePF1 ()  
    SPLIT RANGE (500);  
    ```  
  
#### <a name="to-merge-two-partitions-into-one-partition"></a><span data-ttu-id="fa6c4-151">将两个分区合并为一个分区</span><span class="sxs-lookup"><span data-stu-id="fa6c4-151">To merge two partitions into one partition</span></span>  
  
1.  <span data-ttu-id="fa6c4-152">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-152">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fa6c4-153">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-153">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fa6c4-154">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-154">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Look for a previous version of the partition function "myRangePF1" and deletes it if it is found.  
    IF EXISTS (SELECT * FROM sys.partition_functions  
        WHERE name = 'myRangePF1')  
        DROP PARTITION FUNCTION myRangePF1;  
    GO  
    -- Create a new partition function called "myRangePF1" that partitions a table into four partitions.  
    CREATE PARTITION FUNCTION myRangePF1 (int)  
    AS RANGE LEFT FOR VALUES ( 1, 100, 1000 );  
    GO  
    --Merge the partitions between boundary_values 1 and 100  
    --and between boundary_values 100 and 1000 to create one partition  
    --between boundary_values 1 and 1000.  
    ALTER PARTITION FUNCTION myRangePF1 ()  
    MERGE RANGE (100);  
    ```  
  
 <span data-ttu-id="fa6c4-155">有关详细信息，请参阅 [ALTER PARTITION FUNCTION (Transact SQL)](/sql/t-sql/statements/alter-partition-function-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="fa6c4-155">For more information, see [ALTER PARTITION FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-partition-function-transact-sql).</span></span>  
  
  
