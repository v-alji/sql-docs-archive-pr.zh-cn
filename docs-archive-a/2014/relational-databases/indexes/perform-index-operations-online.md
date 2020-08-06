---
title: 联机执行索引操作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index online operations [SQL Server]
- online index operations
- ONLINE option
ms.assetid: 1e43537c-bf67-4db3-9908-3cb45c6fdaa1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4d09bd99a0eaec5fdb433bd8c33351d7622957a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590788"
---
# <a name="perform-index-operations-online"></a><span data-ttu-id="b0b05-102">联机执行索引操作</span><span class="sxs-lookup"><span data-stu-id="b0b05-102">Perform Index Operations Online</span></span>
  <span data-ttu-id="b0b05-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中联机创建、重新生成或删除索引。</span><span class="sxs-lookup"><span data-stu-id="b0b05-103">This topic describes how to create, rebuild, or drop indexes online in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="b0b05-104">ONLINE 选项允许并发用户在执行这些索引操作期间访问基础表或聚集索引数据和任何关联非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="b0b05-104">The ONLINE option allows concurrent user access to the underlying table or clustered index data and any associated nonclustered indexes during these index operations.</span></span> <span data-ttu-id="b0b05-105">例如，一个用户正在重新生成聚集索引时，该用户和其他用户可以继续更新和查询基础数据。</span><span class="sxs-lookup"><span data-stu-id="b0b05-105">For example, while a clustered index is being rebuilt by one user, that user and others can continue to update and query the underlying data.</span></span> <span data-ttu-id="b0b05-106">当脱机执行数据定义语言 (DDL) 操作（例如，生成或重新生成聚集索引）时，这些操作对基础数据和关联索引持有排他锁。</span><span class="sxs-lookup"><span data-stu-id="b0b05-106">When you perform data definition language (DDL) operations offline, such as building or rebuilding a clustered index; these operations hold exclusive locks on the underlying data and associated indexes.</span></span> <span data-ttu-id="b0b05-107">这样可以防止在索引操作未完成时对基础数据进行修改和查询。</span><span class="sxs-lookup"><span data-stu-id="b0b05-107">This prevents modifications and queries to the underlying data until the index operation is complete.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b0b05-108">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的各版本中均不提供联机索引操作。</span><span class="sxs-lookup"><span data-stu-id="b0b05-108">Online index operations are not available in every [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] edition.</span></span> <span data-ttu-id="b0b05-109">有关详细信息，请参阅 [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="b0b05-109">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="b0b05-110">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="b0b05-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b0b05-111">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="b0b05-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b0b05-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b0b05-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b0b05-113">安全性</span><span class="sxs-lookup"><span data-stu-id="b0b05-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b0b05-114">**若要联机重新生成索引，请使用：**</span><span class="sxs-lookup"><span data-stu-id="b0b05-114">**To rebuild an index online, using:**</span></span>  
  
     [<span data-ttu-id="b0b05-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b0b05-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b0b05-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b0b05-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b0b05-117">开始之前</span><span class="sxs-lookup"><span data-stu-id="b0b05-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b0b05-118">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b0b05-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="b0b05-119">建议对于全天候运行的业务环境执行联机索引操作，在这些环境中，在执行索引操作期间必须有并发用户活动。</span><span class="sxs-lookup"><span data-stu-id="b0b05-119">We recommend performing online index operations for business environments that operate 24 hours a day, seven days a week, in which the need for concurrent user activity during index operations is vital.</span></span>  
  
-   <span data-ttu-id="b0b05-120">以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句中可以使用 ONLINE 选项。</span><span class="sxs-lookup"><span data-stu-id="b0b05-120">The ONLINE option is available in the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
    -   [<span data-ttu-id="b0b05-121">CREATE INDEX</span><span class="sxs-lookup"><span data-stu-id="b0b05-121">CREATE INDEX</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
    -   [<span data-ttu-id="b0b05-122">ALTER INDEX</span><span class="sxs-lookup"><span data-stu-id="b0b05-122">ALTER INDEX</span></span>](/sql/t-sql/statements/alter-index-transact-sql)  
  
    -   [<span data-ttu-id="b0b05-123">DROP INDEX</span><span class="sxs-lookup"><span data-stu-id="b0b05-123">DROP INDEX</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
    -   <span data-ttu-id="b0b05-124">[ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) （使用 CLUSTERED 索引选项添加或删除 UNIQUE 约束或 PRIMARY KEY 约束）</span><span class="sxs-lookup"><span data-stu-id="b0b05-124">[ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) (To add or drop UNIQUE or PRIMARY KEY constraints with CLUSTERED index option)</span></span>  
  
-   <span data-ttu-id="b0b05-125">有关联机创建、重新生成或删除索引的更多限制和局限性，请参阅 [联机索引操作指南](guidelines-for-online-index-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="b0b05-125">For more limitations and restrictions concerning creating, rebuilding, or dropping indexes online, see [Guidelines for Online Index Operations](guidelines-for-online-index-operations.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b0b05-126">Security</span><span class="sxs-lookup"><span data-stu-id="b0b05-126">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b0b05-127">权限</span><span class="sxs-lookup"><span data-stu-id="b0b05-127">Permissions</span></span>  
 <span data-ttu-id="b0b05-128">要求对表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="b0b05-128">Requires ALTER permission on the table or view.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b0b05-129">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b0b05-129">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rebuild-an-index-online"></a><span data-ttu-id="b0b05-130">联机重新生成索引</span><span class="sxs-lookup"><span data-stu-id="b0b05-130">To rebuild an index online</span></span>  
  
1.  <span data-ttu-id="b0b05-131">在“对象资源管理器”中，单击加号以便展开包含您要联机重新生成索引的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="b0b05-131">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to rebuild an index online.</span></span>  
  
2.  <span data-ttu-id="b0b05-132">展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="b0b05-132">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="b0b05-133">单击加号以展开您要联机重新生成索引的表。</span><span class="sxs-lookup"><span data-stu-id="b0b05-133">Click the plus sign to expand the table on which you want to rebuild an index online.</span></span>  
  
4.  <span data-ttu-id="b0b05-134">展开 **“索引”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="b0b05-134">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="b0b05-135">右键单击要联机重新生成的索引，然后选择“属性”。</span><span class="sxs-lookup"><span data-stu-id="b0b05-135">Right-click the index that you want to rebuild online and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="b0b05-136">在 **“选择页”** 下，选择 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="b0b05-136">Under **Select a page**, select **Options**.</span></span>  
  
7.  <span data-ttu-id="b0b05-137">选择 **“允许联机 DML 处理”** ，然后从列表中选择 **True** 。</span><span class="sxs-lookup"><span data-stu-id="b0b05-137">Select **Allow online DML processing**, and then select **True** from the list.</span></span>  
  
8.  <span data-ttu-id="b0b05-138">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="b0b05-138">Click **OK**.</span></span>  
  
9. <span data-ttu-id="b0b05-139">右键单击要联机重新生成的索引，然后选择“重新生成”。</span><span class="sxs-lookup"><span data-stu-id="b0b05-139">Right-click the index that you want to rebuild online and select **Rebuild**.</span></span>  
  
10. <span data-ttu-id="b0b05-140">在 **“重新生成索引”** 对话框中，确认正确的索引位于 **“要重新生成的索引”** 网格中，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="b0b05-140">In the **Rebuild Indexes** dialog box, verify that the correct index is in the **Indexes to rebuild** grid and click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b0b05-141">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b0b05-141">Using Transact-SQL</span></span>  
  
#### <a name="to-create-rebuild-or-drop-an-index-online"></a><span data-ttu-id="b0b05-142">联机创建、重新生成或删除索引</span><span class="sxs-lookup"><span data-stu-id="b0b05-142">To create, rebuild, or drop an index online</span></span>  
  
1.  <span data-ttu-id="b0b05-143">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="b0b05-143">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b0b05-144">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b0b05-144">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b0b05-145">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="b0b05-145">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="b0b05-146">该示例将联机重新生成现有的索引</span><span class="sxs-lookup"><span data-stu-id="b0b05-146">The example rebuilds an existing online</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER INDEX AK_Employee_NationalIDNumber ON HumanResources.Employee  
    REBUILD WITH (ONLINE = ON);  
    GO  
    ```  
  
     <span data-ttu-id="b0b05-147">以下示例使用 `NewGroup` 子句联机删除一个聚集索引并将生成表（堆）移动到文件组 `MOVE TO` 。</span><span class="sxs-lookup"><span data-stu-id="b0b05-147">The following example deletes a clustered index online and moves the resulting table (heap) to the filegroup `NewGroup` by using the `MOVE TO` clause.</span></span> <span data-ttu-id="b0b05-148">在移动之前和之后，将查询 `sys.indexes`、 `sys.tables`和 `sys.filegroups` 目录视图，以验证索引和表在文件组中的位置。</span><span class="sxs-lookup"><span data-stu-id="b0b05-148">The `sys.indexes`, `sys.tables`, and `sys.filegroups` catalog views are queried to verify the index and table placement in the filegroups before and after the move.</span></span>  
  
     [!code-sql[IndexDDL#DropIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/dropindex.sql#dropindex4)]  
  
 <span data-ttu-id="b0b05-149">有关详细信息，请参阅 [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b0b05-149">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
  
