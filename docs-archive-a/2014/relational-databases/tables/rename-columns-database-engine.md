---
title: 重命名列（数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], names
- renaming columns
- column names [SQL Server]
ms.assetid: 7c71ec9f-0180-4398-b32a-4bfb7592e75d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6871ab82eaa17aa5e392e6b2bb3f5c60058f9af9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589459"
---
# <a name="rename-columns-database-engine"></a><span data-ttu-id="189ad-102">重命名列（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="189ad-102">Rename Columns (Database Engine)</span></span>
  <span data-ttu-id="189ad-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 重命名 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的表列。</span><span class="sxs-lookup"><span data-stu-id="189ad-103">You can rename a table column in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="189ad-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="189ad-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="189ad-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="189ad-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="189ad-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="189ad-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="189ad-107">安全性</span><span class="sxs-lookup"><span data-stu-id="189ad-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="189ad-108">**若要重命名列，请使用：**</span><span class="sxs-lookup"><span data-stu-id="189ad-108">**To rename columns, using:**</span></span>  
  
     [<span data-ttu-id="189ad-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="189ad-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="189ad-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="189ad-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="189ad-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="189ad-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="189ad-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="189ad-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="189ad-113">重命名列将不会自动重命名对该列的引用。</span><span class="sxs-lookup"><span data-stu-id="189ad-113">Renaming a column will not automatically rename references to that column.</span></span> <span data-ttu-id="189ad-114">您必须手动修改引用已重命名列的任何对象。</span><span class="sxs-lookup"><span data-stu-id="189ad-114">You must modify any objects that reference the renamed column manually.</span></span> <span data-ttu-id="189ad-115">例如，如果您重命名表列，并且触发器中引用了该列，则必须修改触发器以反映新的列名。</span><span class="sxs-lookup"><span data-stu-id="189ad-115">For example, if you rename a table column and that column is referenced in a trigger, you must modify the trigger to reflect the new column name.</span></span> <span data-ttu-id="189ad-116">请使用 [sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) 在重命名对象之前列出对象的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="189ad-116">Use [sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) to list dependencies on the object before renaming it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="189ad-117">Security</span><span class="sxs-lookup"><span data-stu-id="189ad-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="189ad-118">权限</span><span class="sxs-lookup"><span data-stu-id="189ad-118">Permissions</span></span>  
 <span data-ttu-id="189ad-119">需要对对象的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="189ad-119">Requires ALTER permission on the object.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="189ad-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="189ad-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-column-using-object-explorer"></a><span data-ttu-id="189ad-121">使用对象资源管理器重命名列</span><span class="sxs-lookup"><span data-stu-id="189ad-121">To rename a column using Object Explorer</span></span>  
  
1.  <span data-ttu-id="189ad-122">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="189ad-122">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="189ad-123">在“对象资源管理器”  中，右键单击要重命名其中的列的表，再选择“重命名”  。</span><span class="sxs-lookup"><span data-stu-id="189ad-123">In **Object Explorer**, right-click the table in which you want to rename columns and choose **Rename**.</span></span>  
  
3.  <span data-ttu-id="189ad-124">键入新的列名称。</span><span class="sxs-lookup"><span data-stu-id="189ad-124">Type a new column name.</span></span>  
  
#### <a name="to-rename-a-column-using-table-designer"></a><span data-ttu-id="189ad-125">使用表设计器重命名列</span><span class="sxs-lookup"><span data-stu-id="189ad-125">To rename a column using Table Designer</span></span>  
  
1.  <span data-ttu-id="189ad-126">在“对象资源管理器”  中，右键单击要为其重命名列的表，再选择“设计”  。</span><span class="sxs-lookup"><span data-stu-id="189ad-126">In **Object Explorer**, right-click the table to which you want to rename columns and choose **Design**.</span></span>  
  
2.  <span data-ttu-id="189ad-127">在 **“列名”** 下，选择要更改的名称，并键入新名称。</span><span class="sxs-lookup"><span data-stu-id="189ad-127">Under **Column Name**, select the name you want to change and type a new one.</span></span>  
  
3.  <span data-ttu-id="189ad-128">在“文件”菜单上，单击“保存表名称”\*\*\*\*\*\*\*\*__。</span><span class="sxs-lookup"><span data-stu-id="189ad-128">On the **File** menu, click **Save**_table name_.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="189ad-129">您也可以在 **“列属性”** 选项卡中更改列名。选择要更改名称的列，并为 **“名称”** 键入新值。</span><span class="sxs-lookup"><span data-stu-id="189ad-129">You can also change the name of a column in the **Column Properties** tab. Select the column whose name you want to change and type a new value for **Name**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="189ad-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="189ad-130">Using Transact-SQL</span></span>  
 <span data-ttu-id="189ad-131">**重命名列**</span><span class="sxs-lookup"><span data-stu-id="189ad-131">**To rename a column**</span></span>  
  
#### <a name="to-rename-a-column"></a><span data-ttu-id="189ad-132">重命名列</span><span class="sxs-lookup"><span data-stu-id="189ad-132">To rename a column</span></span>  
  
1.  <span data-ttu-id="189ad-133">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="189ad-133">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="189ad-134">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="189ad-134">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="189ad-135">下面的示例将 `TerritoryID` 表中的 `Sales.SalesTerritory` 列重命名为 `TerrID`。</span><span class="sxs-lookup"><span data-stu-id="189ad-135">The following example renames the column `TerritoryID` in the table `Sales.SalesTerritory` to `TerrID`.</span></span> <span data-ttu-id="189ad-136">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="189ad-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_rename 'Sales.SalesTerritory.TerritoryID', 'TerrID', 'COLUMN';  
    GO  
    ```  
  
 <span data-ttu-id="189ad-137">有关详细信息，请参阅 [sp_rename (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="189ad-137">For more information, see [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).</span></span>  
  
  
