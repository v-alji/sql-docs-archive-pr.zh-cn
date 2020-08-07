---
title: 修改分区方案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 515de63f-dfc5-434d-9adb-f3b5992f745a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d57984228e23143d2061df6bf447f978f9bd3c46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588489"
---
# <a name="modify-a-partition-scheme"></a><span data-ttu-id="f48af-102">修改分区方案</span><span class="sxs-lookup"><span data-stu-id="f48af-102">Modify a Partition Scheme</span></span>
  <span data-ttu-id="f48af-103">通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 指定用于保存添加到已分区表的下一个分区的文件组，可以修改 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的分区方案。</span><span class="sxs-lookup"><span data-stu-id="f48af-103">You can modify a partition scheme in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by designating a filegroup to hold the next partition that is added to a partitioned table using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f48af-104">可通过将 NEXT USED 属性分配给文件组来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="f48af-104">You do this by assigning the NEXT USED property to a filegroup.</span></span> <span data-ttu-id="f48af-105">您可以将 NEXT USED 属性分配给空文件组或已存有分区的文件组。</span><span class="sxs-lookup"><span data-stu-id="f48af-105">You can assign the NEXT USED property to an empty filegroup or to one that already holds a partition.</span></span> <span data-ttu-id="f48af-106">也就是说，一个文件组可以保存多个分区。</span><span class="sxs-lookup"><span data-stu-id="f48af-106">In other words, a filegroup can hold more than one partition.</span></span>  
  
 <span data-ttu-id="f48af-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="f48af-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f48af-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="f48af-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f48af-109">限制和局限</span><span class="sxs-lookup"><span data-stu-id="f48af-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f48af-110">安全性</span><span class="sxs-lookup"><span data-stu-id="f48af-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f48af-111">**创建已分区表或索引，使用：**</span><span class="sxs-lookup"><span data-stu-id="f48af-111">**To create a partitioned table or index, using:**</span></span>  
  
     [<span data-ttu-id="f48af-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f48af-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f48af-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f48af-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f48af-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="f48af-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f48af-115">限制和局限</span><span class="sxs-lookup"><span data-stu-id="f48af-115">Limitations and Restrictions</span></span>  
 <span data-ttu-id="f48af-116">受 ALTER PARTITION SCHEME 影响的所有文件组都必须处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="f48af-116">Any filegroup affected by ALTER PARTITION SCHEME must be online.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f48af-117">Security</span><span class="sxs-lookup"><span data-stu-id="f48af-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f48af-118">权限</span><span class="sxs-lookup"><span data-stu-id="f48af-118">Permissions</span></span>  
 <span data-ttu-id="f48af-119">以下权限可用于执行 ALTER PARTITION SCHEME：</span><span class="sxs-lookup"><span data-stu-id="f48af-119">The following permissions can be used to execute ALTER PARTITION SCHEME:</span></span>  
  
-   <span data-ttu-id="f48af-120">ALTER ANY DATASPACE 权限。</span><span class="sxs-lookup"><span data-stu-id="f48af-120">ALTER ANY DATASPACE permission.</span></span> <span data-ttu-id="f48af-121">默认情况下，此权限授予 **sysadmin** 固定服务器角色和 **db_owner** 及 **db_ddladmin** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="f48af-121">This permission defaults to members of the **sysadmin** fixed server role and the **db_owner** and **db_ddladmin** fixed database roles.</span></span>  
  
-   <span data-ttu-id="f48af-122">对创建分区方案时所在数据库的 CONTROL 或 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="f48af-122">CONTROL or ALTER permission on the database in which the partition scheme was created.</span></span>  
  
-   <span data-ttu-id="f48af-123">对承载了创建分区方案时所在数据库的服务器的 CONTROL SERVER 或 ALTER ANY DATABASE 权限。</span><span class="sxs-lookup"><span data-stu-id="f48af-123">CONTROL SERVER or ALTER ANY DATABASE permission on the server of the database in which the partition scheme was created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f48af-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f48af-124">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="f48af-125">**修改分区方案：**</span><span class="sxs-lookup"><span data-stu-id="f48af-125">**To modify a partition scheme:**</span></span>  
  
 <span data-ttu-id="f48af-126">无法使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]执行此特定操作。</span><span class="sxs-lookup"><span data-stu-id="f48af-126">This specific action cannot be performed using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="f48af-127">若要修改某个分区方案，您必须先删除该方案，然后通过创建分区向导使用所需属性创建一个新方案。</span><span class="sxs-lookup"><span data-stu-id="f48af-127">In order to modify a partition scheme, you must first delete the scheme and then create a new one with the desired properties using the Create Partition Wizard.</span></span> <span data-ttu-id="f48af-128">有关详细信息，请参阅创建已分区**表和索引**中的[使用 SQL Server Management Studio 创建已分区表和索引](create-partitioned-tables-and-indexes.md#SSMSProcedure)。</span><span class="sxs-lookup"><span data-stu-id="f48af-128">For more information, see [Create Partitioned Tables and Indexes Using SQL Server Management Studio](create-partitioned-tables-and-indexes.md#SSMSProcedure) under **Create Partitioned Tables and Indexes**.</span></span>  
  
#### <a name="to-delete-a-partition-scheme"></a><span data-ttu-id="f48af-129">删除分区方案</span><span class="sxs-lookup"><span data-stu-id="f48af-129">To delete a partition scheme</span></span>  
  
1.  <span data-ttu-id="f48af-130">单击加号以便展开要删除分区方案的数据库。</span><span class="sxs-lookup"><span data-stu-id="f48af-130">Click the plus sign to expand the database where you want to delete the partition scheme.</span></span>  
  
2.  <span data-ttu-id="f48af-131">单击加号以便展开 **“存储”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="f48af-131">Click the plus sign to expand the **Storage** folder.</span></span>  
  
3.  <span data-ttu-id="f48af-132">单击加号以便展开 **“分区方案”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="f48af-132">Click the plus sign to expand the **Partition Schemes** folder.</span></span>  
  
4.  <span data-ttu-id="f48af-133">右键单击要删除的分区方案，然后选择“删除”  。</span><span class="sxs-lookup"><span data-stu-id="f48af-133">Right-click the partition scheme you want to delete and select **Delete**.</span></span>  
  
5.  <span data-ttu-id="f48af-134">在 **“删除对象”** 对话框中，确保已选择正确的分区方案，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="f48af-134">In the **Delete Object** dialog box, ensure that the correct partition scheme is selected, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f48af-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f48af-135">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-partition-scheme"></a><span data-ttu-id="f48af-136">修改分区方案</span><span class="sxs-lookup"><span data-stu-id="f48af-136">To modify a partition scheme</span></span>  
  
1.  <span data-ttu-id="f48af-137">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="f48af-137">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f48af-138">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="f48af-138">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f48af-139">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="f48af-139">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- add five new filegroups to the AdventureWorks2012 database  
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
    GO  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test5fg;  
    GO  
    -- if the "myRangePF1" partition function and the "myRangePS1" partition scheme exist,  
    -- drop them from the AdventureWorks2012 database  
    IF EXISTS (SELECT * FROM sys.partition_functions  
        WHERE name = 'myRangePF1')  
    DROP PARTITION FUNCTION myRangePF1;  
    GO  
    IF EXISTS (SELECT * FROM sys.partition_schemes  
        WHERE name = 'myRangePS1')  
    DROP PARTITION SCHEME myRangePS1;  
    GO  
    -- create the new partition function "myRangePF1" with four partition groups  
    CREATE PARTITION FUNCTION myRangePF1 (int)  
    AS RANGE LEFT FOR VALUES ( 1, 100, 1000 );  
    GO  
    -- create the new partition scheme "myRangePS1"that will use   
    -- the "myRangePF1" partition function with five file groups.  
    -- The last filegroup, "test5fg," will be kept empty but marked  
    -- as the next used filegroup in the partition scheme.  
    CREATE PARTITION SCHEME myRangePS1  
    AS PARTITION myRangePF1  
    TO (test1fg, test2fg, test3fg, test4fg, test5fg);  
    GO  
    --Split "myRangePS1" between boundary_values 100 and 1000  
    --to create two partitions between boundary_values 100 and 500  
    --and between boundary_values 500 and 1000.  
    ALTER PARTITION FUNCTION myRangePF1 ()  
    SPLIT RANGE (500);  
    GO  
    -- Allow the "myRangePS1" partition scheme to use the filegroup "test5fg"  
    -- for the partition with boundary_values of 100 and 500  
    ALTER PARTITION SCHEME myRangePS1  
    NEXT USED test5fg;  
    GO  
    ```  
  
 <span data-ttu-id="f48af-140">有关详细信息，请参阅 [ALTER PARTITION SCHEME (Transact-SQL)](/sql/t-sql/statements/alter-partition-scheme-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f48af-140">For more information, see [ALTER PARTITION SCHEME &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-partition-scheme-transact-sql).</span></span>  
  
  
