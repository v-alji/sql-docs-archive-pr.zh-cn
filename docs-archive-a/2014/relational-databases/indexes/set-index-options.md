---
title: 设置索引选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- ALLOW_ROW_LOCKS option
- SORT_IN_TEMPDB option
- DROP_EXISTING clause
- large data, indexes
- PAD_INDEX
- STATISTICS_NORECOMPUTE
- MAXDOP index option, setting
- index options [SQL Server]
- MAXDOP index option
- IGNORE_DUP_KEY option
- ALLOW_PAGE_LOCKS option
- ONLINE
ms.assetid: 7969af33-e94c-41f7-ab89-9d9a2747cd5c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9f2d7f0bbbf0d152d3f510ae9ddbe3168634ef96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692933"
---
# <a name="set-index-options"></a><span data-ttu-id="47bfd-102">设置索引选项</span><span class="sxs-lookup"><span data-stu-id="47bfd-102">Set Index Options</span></span>
  <span data-ttu-id="47bfd-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改索引的属性。</span><span class="sxs-lookup"><span data-stu-id="47bfd-103">This topic describes how to modify the properties of an index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="47bfd-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="47bfd-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="47bfd-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="47bfd-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="47bfd-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="47bfd-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="47bfd-107">安全性</span><span class="sxs-lookup"><span data-stu-id="47bfd-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="47bfd-108">**修改索引的属性，使用：**</span><span class="sxs-lookup"><span data-stu-id="47bfd-108">**To modify the properties of an index, using:**</span></span>  
  
     [<span data-ttu-id="47bfd-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="47bfd-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="47bfd-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="47bfd-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="47bfd-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="47bfd-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="47bfd-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="47bfd-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="47bfd-113">使用 ALTER INDEX 语句中的 SET 子句，将以下选项立即应用到索引：ALLOW_PAGE_LOCKS、ALLOW_ROW_LOCKS、IGNORE_DUP_KEY 和 STATISTICS_NORECOMPUTE。</span><span class="sxs-lookup"><span data-stu-id="47bfd-113">The following options are immediately applied to the index by using the SET clause in the ALTER INDEX statement: ALLOW_PAGE_LOCKS, ALLOW_ROW_LOCKS, IGNORE_DUP_KEY, and STATISTICS_NORECOMPUTE.</span></span>  
  
-   <span data-ttu-id="47bfd-114">通过使用 ALTER INDEX REBUILD 或 CREATE INDEX WITH DROP_EXISTING，可以在重新生成索引时设置下列选项：PAD_INDEX、FILLFACTOR、SORT_IN_TEMPDB、IGNORE_DUP_KEY、STATISTICS_NORECOMPUTE、ONLINE、ALLOW_ROW_LOCKS、ALLOW_PAGE_LOCKS、MAXDOP 和 DROP_EXISTING（仅 CREATE INDEX）。</span><span class="sxs-lookup"><span data-stu-id="47bfd-114">The following options can be set when you rebuild an index by using either ALTER INDEX REBUILD or CREATE INDEX WITH DROP_EXISTING: PAD_INDEX, FILLFACTOR, SORT_IN_TEMPDB, IGNORE_DUP_KEY, STATISTICS_NORECOMPUTE, ONLINE, ALLOW_ROW_LOCKS, ALLOW_PAGE_LOCKS, MAXDOP, and DROP_EXISTING (CREATE INDEX only).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="47bfd-115">Security</span><span class="sxs-lookup"><span data-stu-id="47bfd-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="47bfd-116">权限</span><span class="sxs-lookup"><span data-stu-id="47bfd-116">Permissions</span></span>  
 <span data-ttu-id="47bfd-117">要求对表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="47bfd-117">Requires ALTER permission on the table or view.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="47bfd-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="47bfd-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-the-properties-of-an-index-in-table-designer"></a><span data-ttu-id="47bfd-119">在表设计器中修改索引的属性</span><span class="sxs-lookup"><span data-stu-id="47bfd-119">To modify the properties of an index in Table Designer</span></span>  
  
1.  <span data-ttu-id="47bfd-120">在对象资源管理器中，单击加号以便展开包含您要修改索引属性的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="47bfd-120">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to modify an index's properties.</span></span>  
  
2.  <span data-ttu-id="47bfd-121">单击加号以便展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="47bfd-121">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="47bfd-122">右键单击你要修改索引属性的表，然后选择“设计”  。</span><span class="sxs-lookup"><span data-stu-id="47bfd-122">Right-click the table on which you want to modify an index's properties and select **Design**.</span></span>  
  
4.  <span data-ttu-id="47bfd-123">在“表设计器”  菜单上，单击“索引/键”  。</span><span class="sxs-lookup"><span data-stu-id="47bfd-123">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="47bfd-124">选择要修改的索引。</span><span class="sxs-lookup"><span data-stu-id="47bfd-124">Select the index that you want to modify.</span></span> <span data-ttu-id="47bfd-125">其属性将显示在主网格中。</span><span class="sxs-lookup"><span data-stu-id="47bfd-125">Its properties will show up in the main grid.</span></span>  
  
6.  <span data-ttu-id="47bfd-126">更改任意属性的设置以自定义索引。</span><span class="sxs-lookup"><span data-stu-id="47bfd-126">Change the settings of any and all properties to customize the index.</span></span>  
  
7.  <span data-ttu-id="47bfd-127">单击“关闭”  。</span><span class="sxs-lookup"><span data-stu-id="47bfd-127">Click **Close**.</span></span>  
  
8.  <span data-ttu-id="47bfd-128">在“文件”  菜单上，选择“保存”  以保存 _table_name_。</span><span class="sxs-lookup"><span data-stu-id="47bfd-128">On the **File** menu, select **Save**_table_name_.</span></span>  
  
#### <a name="to-modify-the-properties-of-an-index-in-object-explorer"></a><span data-ttu-id="47bfd-129">在对象资源管理器中修改索引的属性</span><span class="sxs-lookup"><span data-stu-id="47bfd-129">To modify the properties of an index in Object Explorer</span></span>  
  
1.  <span data-ttu-id="47bfd-130">在对象资源管理器中，单击加号以便展开包含您要修改索引属性的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="47bfd-130">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to modify an index's properties.</span></span>  
  
2.  <span data-ttu-id="47bfd-131">单击加号以便展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="47bfd-131">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="47bfd-132">单击加号以展开您要修改索引属性的表。</span><span class="sxs-lookup"><span data-stu-id="47bfd-132">Click the plus sign to expand the table on which you want to modify an index's properties.</span></span>  
  
4.  <span data-ttu-id="47bfd-133">单击加号以便展开 **“索引”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="47bfd-133">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="47bfd-134">右键单击要修改其属性的索引，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="47bfd-134">Right-click the index of which you want to modify the properties and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="47bfd-135">在 **“选择页”** 下，选择 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="47bfd-135">Under **Select a page**, select **Options**.</span></span>  
  
7.  <span data-ttu-id="47bfd-136">更改任意属性的设置以自定义索引。</span><span class="sxs-lookup"><span data-stu-id="47bfd-136">Change the settings of any and all properties to customize the index.</span></span>  
  
8.  <span data-ttu-id="47bfd-137">若要添加、删除或更改索引列的位置，请从“索引属性 - index_name”对话框中选择“常规”页    。</span><span class="sxs-lookup"><span data-stu-id="47bfd-137">To add, remove, or change the position of an index column, select the **General** page from the **Index Properties -** _index_name_ dialog box.</span></span> <span data-ttu-id="47bfd-138">有关详细信息，请参阅 [Index Properties F1 Help](index-properties-f1-help.md)</span><span class="sxs-lookup"><span data-stu-id="47bfd-138">For more information, see [Index Properties F1 Help](index-properties-f1-help.md)</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="47bfd-139">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="47bfd-139">Using Transact-SQL</span></span>  
  
#### <a name="to-see-the-properties-of-all-the-indexes-in-a-table"></a><span data-ttu-id="47bfd-140">查看表中所有索引的属性</span><span class="sxs-lookup"><span data-stu-id="47bfd-140">To see the properties of all the indexes in a table</span></span>  
  
1.  <span data-ttu-id="47bfd-141">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="47bfd-141">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="47bfd-142">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="47bfd-142">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="47bfd-143">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="47bfd-143">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT i.name AS index_name,   
        i.type_desc,   
        i.is_unique,   
        ds.type_desc AS filegroup_or_partition_scheme,   
        ds.name AS filegroup_or_partition_scheme_name,   
        i.ignore_dup_key,   
        i.is_primary_key,   
        i.is_unique_constraint,   
        i.fill_factor,   
        i.is_padded,   
        i.is_disabled,   
        i.allow_row_locks,   
        i.allow_page_locks,   
        i.has_filter,   
        i.filter_definition  
    FROM sys.indexes AS i  
       INNER JOIN sys.data_spaces AS ds ON i.data_space_id = ds.data_space_id  
    WHERE is_hypothetical = 0 AND i.index_id <> 0   
       AND i.object_id = OBJECT_ID('HumanResources.Employee');   
    GO  
  
    ```  
  
#### <a name="to-set-the-properties-of-an-index"></a><span data-ttu-id="47bfd-144">设置索引的属性</span><span class="sxs-lookup"><span data-stu-id="47bfd-144">To set the properties of an index</span></span>  
  
1.  <span data-ttu-id="47bfd-145">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="47bfd-145">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="47bfd-146">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="47bfd-146">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="47bfd-147">将以下示例复制并粘贴到查询窗口中，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="47bfd-147">Copy and paste the following examples into the query window and click **Execute**.</span></span>  
  
     [!code-sql[IndexDDL#AlterIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex4)]  
  
     [!code-sql[IndexDDL#AlterIndex2](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex2)]  
  
 <span data-ttu-id="47bfd-148">有关详细信息，请参阅 [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="47bfd-148">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
  
