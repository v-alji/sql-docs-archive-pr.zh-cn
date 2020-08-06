---
title: 重命名索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- renaming indexes
- index names [SQL Server]
- indexes [SQL Server], renaming
ms.assetid: d3d612a1-ea1b-4d99-85d2-0a2ad54f4b0e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 184d6e20f7857c5ea3535e77e21a0630ffc7b678
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590787"
---
# <a name="rename-indexes"></a><span data-ttu-id="64f3e-102">重命名索引</span><span class="sxs-lookup"><span data-stu-id="64f3e-102">Rename Indexes</span></span>
  <span data-ttu-id="64f3e-103">本主题将说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中重命名索引。</span><span class="sxs-lookup"><span data-stu-id="64f3e-103">This topic describes how to rename an index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="64f3e-104">重命名索引将用提供的新名称替换当前的索引名称。</span><span class="sxs-lookup"><span data-stu-id="64f3e-104">Renaming an index replaces the current index name with the new name that you provide.</span></span> <span data-ttu-id="64f3e-105">指定的名称在表或视图中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="64f3e-105">The specified name must be unique within the table or view.</span></span> <span data-ttu-id="64f3e-106">例如，两个表可以有一个名为 **XPK_1**的索引，但同一表中不能有两个名为 **XPK_1**的索引。</span><span class="sxs-lookup"><span data-stu-id="64f3e-106">For example, two tables can have an index named **XPK_1**, but the same table cannot have two indexes named **XPK_1**.</span></span> <span data-ttu-id="64f3e-107">无法创建与现有禁用索引同名的索引。</span><span class="sxs-lookup"><span data-stu-id="64f3e-107">You cannot create an index with the same name as an existing disabled index.</span></span> <span data-ttu-id="64f3e-108">重命名索引不会导致重新生成索引。</span><span class="sxs-lookup"><span data-stu-id="64f3e-108">Renaming an index does not cause the index to be rebuilt.</span></span>  
  
 <span data-ttu-id="64f3e-109">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="64f3e-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="64f3e-110">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="64f3e-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="64f3e-111">限制和局限</span><span class="sxs-lookup"><span data-stu-id="64f3e-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="64f3e-112">安全性</span><span class="sxs-lookup"><span data-stu-id="64f3e-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="64f3e-113">**若要重命名索引，请使用：**</span><span class="sxs-lookup"><span data-stu-id="64f3e-113">**To rename an index, using:**</span></span>  
  
     [<span data-ttu-id="64f3e-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="64f3e-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="64f3e-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="64f3e-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="64f3e-116">开始之前</span><span class="sxs-lookup"><span data-stu-id="64f3e-116">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="64f3e-117">限制和局限</span><span class="sxs-lookup"><span data-stu-id="64f3e-117">Limitations and Restrictions</span></span>  
 <span data-ttu-id="64f3e-118">在表中创建 PRIMARY KEY 或 UNIQUE 约束时，会在表中自动创建一个与该约束同名的索引。</span><span class="sxs-lookup"><span data-stu-id="64f3e-118">When you create a PRIMARY KEY or UNIQUE constraint on a table, an index with the same name as the constraint is automatically created for the table.</span></span> <span data-ttu-id="64f3e-119">因为索引名称在表中必须是唯一的，所以无法通过创建或重命名获得一个与该表的现有 PRIMARY KEY 或 UNIQUE 约束同名的索引。</span><span class="sxs-lookup"><span data-stu-id="64f3e-119">Because index names must be unique within the table, you cannot create or rename an index to have the same name as an existing PRIMARY KEY or UNIQUE constraint on the table.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="64f3e-120">Security</span><span class="sxs-lookup"><span data-stu-id="64f3e-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="64f3e-121">权限</span><span class="sxs-lookup"><span data-stu-id="64f3e-121">Permissions</span></span>  
 <span data-ttu-id="64f3e-122">需要具有针对索引的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="64f3e-122">Requires ALTER permission on the index.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="64f3e-123">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="64f3e-123">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-an-index-by-using-the-table-designer"></a><span data-ttu-id="64f3e-124">使用表设计器重命名索引</span><span class="sxs-lookup"><span data-stu-id="64f3e-124">To rename an index by using the Table Designer</span></span>  
  
1.  <span data-ttu-id="64f3e-125">在对象资源管理器中，单击加号以便展开包含您要重命名索引的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="64f3e-125">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to rename an index.</span></span>  
  
2.  <span data-ttu-id="64f3e-126">单击加号以便展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="64f3e-126">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="64f3e-127">右键单击你要重命名索引的表，然后选择“设计”  。</span><span class="sxs-lookup"><span data-stu-id="64f3e-127">Right-click the table on which you want to rename an index and select **Design**.</span></span>  
  
4.  <span data-ttu-id="64f3e-128">在“表设计器”  菜单上，单击“索引/键”  。</span><span class="sxs-lookup"><span data-stu-id="64f3e-128">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="64f3e-129">在“选定的主/唯一键或索引”  文本框中，选择你要重命名的索引。</span><span class="sxs-lookup"><span data-stu-id="64f3e-129">Select the index you want to rename in the **Selected Primary/Unique Key or Index** text box.</span></span>  
  
6.  <span data-ttu-id="64f3e-130">在网格中，单击 **“名称”** 并在文本框中键入新名称。</span><span class="sxs-lookup"><span data-stu-id="64f3e-130">In the grid, click **Name** and type a new name into the text box.</span></span>  
  
7.  <span data-ttu-id="64f3e-131">单击“关闭”  。</span><span class="sxs-lookup"><span data-stu-id="64f3e-131">Click **Close**.</span></span>  
  
8.  <span data-ttu-id="64f3e-132">在“文件”  菜单上，单击“保存”  以保存 _table_name_。</span><span class="sxs-lookup"><span data-stu-id="64f3e-132">On the **File** menu, click **Save**_table_name_.</span></span>  
  
#### <a name="to-rename-an-index-by-using-object-explorer"></a><span data-ttu-id="64f3e-133">通过使用对象资源管理器重命名索引</span><span class="sxs-lookup"><span data-stu-id="64f3e-133">To rename an index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="64f3e-134">在对象资源管理器中，单击加号以便展开包含您要重命名索引的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="64f3e-134">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to rename an index.</span></span>  
  
2.  <span data-ttu-id="64f3e-135">单击加号以便展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="64f3e-135">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="64f3e-136">单击加号以便展开您要重命名索引的表。</span><span class="sxs-lookup"><span data-stu-id="64f3e-136">Click the plus sign to expand the table on which you want to rename an index.</span></span>  
  
4.  <span data-ttu-id="64f3e-137">单击加号以便展开 **“索引”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="64f3e-137">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="64f3e-138">右键单击要重命名的索引，然后选择“重命名”  。</span><span class="sxs-lookup"><span data-stu-id="64f3e-138">Right-click the index you want to rename and select **Rename**.</span></span>  
  
6.  <span data-ttu-id="64f3e-139">键入索引的新名称，再按 Enter。</span><span class="sxs-lookup"><span data-stu-id="64f3e-139">Type the index's new name and press Enter.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="64f3e-140">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="64f3e-140">Using Transact-SQL</span></span>  
  
#### <a name="to-rename-an-index"></a><span data-ttu-id="64f3e-141">重命名索引</span><span class="sxs-lookup"><span data-stu-id="64f3e-141">To rename an index</span></span>  
  
1.  <span data-ttu-id="64f3e-142">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="64f3e-142">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="64f3e-143">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="64f3e-143">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="64f3e-144">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="64f3e-144">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    --Renames the IX_ProductVendor_VendorID index on the Purchasing.ProductVendor table to IX_VendorID.   
  
    EXEC sp_rename N'Purchasing.ProductVendor.IX_ProductVendor_VendorID', N'IX_VendorID', N'INDEX';   
    GO  
    ```  
  
 <span data-ttu-id="64f3e-145">有关详细信息，请参阅 [sp_rename (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="64f3e-145">For more information, see  [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).</span></span>  
  
  
