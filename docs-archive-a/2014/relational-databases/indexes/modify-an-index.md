---
title: 修改索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexes [SQL Server], modifying
- modifying indexes
- index changes [SQL Server]
ms.assetid: 97e3110d-fde7-4f5d-9309-dc1697960aeb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2af9293966afce8372f5b83a579418c546c82816
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692935"
---
# <a name="modify-an-index"></a><span data-ttu-id="aec90-102">修改索引</span><span class="sxs-lookup"><span data-stu-id="aec90-102">Modify an Index</span></span>
  <span data-ttu-id="aec90-103">本主题将说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改索引。</span><span class="sxs-lookup"><span data-stu-id="aec90-103">This topic describes how to modify an index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="aec90-104">不能通过此方法修改作为 PRIMARY KEY 或 UNIQUE 约束的结果而创建的索引，</span><span class="sxs-lookup"><span data-stu-id="aec90-104">Indexes created as the result of a PRIMARY KEY or UNIQUE constraint cannot be modified by using this method.</span></span> <span data-ttu-id="aec90-105">而必须修改约束。</span><span class="sxs-lookup"><span data-stu-id="aec90-105">Instead, the constraint must be modified.</span></span>  
  
 <span data-ttu-id="aec90-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="aec90-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="aec90-107">**若要修改索引，请使用：**</span><span class="sxs-lookup"><span data-stu-id="aec90-107">**To modify an index, using:**</span></span>  
  
     [<span data-ttu-id="aec90-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="aec90-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="aec90-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="aec90-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="aec90-110">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="aec90-110">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-an-index"></a><span data-ttu-id="aec90-111">修改索引</span><span class="sxs-lookup"><span data-stu-id="aec90-111">To modify an index</span></span>  
  
1.  <span data-ttu-id="aec90-112">在对象资源管理器中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="aec90-112">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="aec90-113">展开 **“数据库”** ，展开该表所属的数据库，再展开 **“表”** 。</span><span class="sxs-lookup"><span data-stu-id="aec90-113">Expand **Databases**, expand the database in which the table belongs, and then expand **Tables**.</span></span>  
  
3.  <span data-ttu-id="aec90-114">展开该索引所属的表，再展开 **“索引”** 。</span><span class="sxs-lookup"><span data-stu-id="aec90-114">Expand the table in which the index belongs and then expand **Indexes**.</span></span>  
  
4.  <span data-ttu-id="aec90-115">右键单击要修改的索引，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="aec90-115">Right-click the index that you want to modify and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="aec90-116">在 **“索引属性”** 对话框中进行所需的更改。</span><span class="sxs-lookup"><span data-stu-id="aec90-116">In the **Index Properties** dialog box, make the desired changes.</span></span> <span data-ttu-id="aec90-117">例如，您可以从索引键中添加或删除列，或更改索引选项的设置。</span><span class="sxs-lookup"><span data-stu-id="aec90-117">For example, you can add or remove a column from the index key, or change the setting of an index option.</span></span>  
  
#### <a name="to-modify-index-columns"></a><span data-ttu-id="aec90-118">修改索引列</span><span class="sxs-lookup"><span data-stu-id="aec90-118">To modify index columns</span></span>  
  
1.  <span data-ttu-id="aec90-119">若要添加、删除或更改索引列的位置，请从 **“索引属性”** 对话框中选择 **“常规”** 页。</span><span class="sxs-lookup"><span data-stu-id="aec90-119">To add, remove, or change the position of an index column, select the **General** page from the **Index Properties** dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="aec90-120">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="aec90-120">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-an-index"></a><span data-ttu-id="aec90-121">修改索引</span><span class="sxs-lookup"><span data-stu-id="aec90-121">To modify an index</span></span>  
  
1.  <span data-ttu-id="aec90-122">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="aec90-122">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="aec90-123">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="aec90-123">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="aec90-124">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="aec90-124">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="aec90-125">此示例使用 `ProductID` 选项在 `Production.WorkOrder` 表的 `DROP_EXISTING` 列上删除并重新创建现有索引。</span><span class="sxs-lookup"><span data-stu-id="aec90-125">This example drops and re-creates an existing index on the `ProductID` column of the `Production.WorkOrder` table by using the `DROP_EXISTING` option.</span></span> <span data-ttu-id="aec90-126">还设置了 `FILLFACTOR` 和 `PAD_INDEX` 选项。</span><span class="sxs-lookup"><span data-stu-id="aec90-126">The options `FILLFACTOR` and `PAD_INDEX` are also set.</span></span>  
  
     [!code-sql[IndexDDL#CreateIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/createindex.sql#createindex4)]  
  
     <span data-ttu-id="aec90-127">下面的示例使用 ALTER INDEX 为索引 `AK_SalesOrderHeader_SalesOrderNumber`设置了几个选项。</span><span class="sxs-lookup"><span data-stu-id="aec90-127">The following example uses ALTER INDEX to set several options on the index `AK_SalesOrderHeader_SalesOrderNumber`.</span></span>  
  
     [!code-sql[IndexDDL#AlterIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex4)]  
  
#### <a name="to-modify-index-columns"></a><span data-ttu-id="aec90-128">修改索引列</span><span class="sxs-lookup"><span data-stu-id="aec90-128">To modify index columns</span></span>  
  
1.  <span data-ttu-id="aec90-129">若要添加、删除或更改索引列的位置，您必须删除并重新创建该索引。</span><span class="sxs-lookup"><span data-stu-id="aec90-129">To add, remove, or change the position of an index column, you must drop and recreate the index.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aec90-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aec90-130">See Also</span></span>  
 <span data-ttu-id="aec90-131">[CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="aec90-131">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="aec90-132">[ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="aec90-132">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 <span data-ttu-id="aec90-133">[INDEXPROPERTY (Transact-SQL)](/sql/t-sql/functions/indexproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="aec90-133">[INDEXPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/indexproperty-transact-sql) </span></span>  
 <span data-ttu-id="aec90-134">[sys.indexes (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="aec90-134">[sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql) </span></span>  
 <span data-ttu-id="aec90-135">[sys.index_columns (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-index-columns-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="aec90-135">[sys.index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-index-columns-transact-sql) </span></span>  
 <span data-ttu-id="aec90-136">[设置索引选项](set-index-options.md) </span><span class="sxs-lookup"><span data-stu-id="aec90-136">[Set Index Options](set-index-options.md) </span></span>  
 [<span data-ttu-id="aec90-137">重命名索引</span><span class="sxs-lookup"><span data-stu-id="aec90-137">Rename Indexes</span></span>](indexes.md)  
  
  
