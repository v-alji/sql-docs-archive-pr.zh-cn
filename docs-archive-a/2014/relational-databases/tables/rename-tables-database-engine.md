---
title: 重命名表（数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table renaming [SQL Server]
- table names [SQL Server]
- tables [SQL Server], Visual Database Tools
- renaming tables
ms.assetid: 2f5c922d-4d71-4694-9fca-28dd99375799
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6e73bbb92d8fd3fdcaa7756ce1dcb74d8cd598b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589456"
---
# <a name="rename-tables-database-engine"></a><span data-ttu-id="88093-102">重命名表（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="88093-102">Rename Tables (Database Engine)</span></span>
  <span data-ttu-id="88093-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 重命名 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的表。</span><span class="sxs-lookup"><span data-stu-id="88093-103">You can rename a table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="88093-104">在重命名表之前请仔细考虑。</span><span class="sxs-lookup"><span data-stu-id="88093-104">Think carefully before you rename a table.</span></span> <span data-ttu-id="88093-105">如果现有的查询、视图、用户定义函数、存储过程或程序引用了该表，则对名称的修改将使这些对象无效。</span><span class="sxs-lookup"><span data-stu-id="88093-105">If existing queries, views, user-defined functions, stored procedures, or programs refer to that table, the name modification will make these objects invalid.</span></span>  
  
 <span data-ttu-id="88093-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="88093-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="88093-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="88093-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="88093-108">限制和局限</span><span class="sxs-lookup"><span data-stu-id="88093-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="88093-109">安全性</span><span class="sxs-lookup"><span data-stu-id="88093-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="88093-110">**使用以下工具重命名表：**</span><span class="sxs-lookup"><span data-stu-id="88093-110">**To rename a table, using:**</span></span>  
  
     [<span data-ttu-id="88093-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="88093-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="88093-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="88093-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="88093-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="88093-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="88093-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="88093-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="88093-115">重命名表将不会自动重命名对该表的引用。</span><span class="sxs-lookup"><span data-stu-id="88093-115">Renaming a table will not automatically rename references to that table.</span></span> <span data-ttu-id="88093-116">您必须手动修改引用已重命名表的任何对象。</span><span class="sxs-lookup"><span data-stu-id="88093-116">You must manually modify any objects that reference the renamed table.</span></span> <span data-ttu-id="88093-117">例如，如果您重命名某个表，并且触发器中引用了该表，则必须修改触发器以反映新的表名称。</span><span class="sxs-lookup"><span data-stu-id="88093-117">For example, if you rename a table and that table is referenced in a trigger, you must modify the trigger to reflect the new table name.</span></span> <span data-ttu-id="88093-118">请使用 [sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) 在重命名表之前列出该表上的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="88093-118">Use [sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) to list dependencies on the table before renaming it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="88093-119">Security</span><span class="sxs-lookup"><span data-stu-id="88093-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="88093-120">权限</span><span class="sxs-lookup"><span data-stu-id="88093-120">Permissions</span></span>  
 <span data-ttu-id="88093-121">需要对表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="88093-121">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="88093-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="88093-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-table"></a><span data-ttu-id="88093-123">重命名表</span><span class="sxs-lookup"><span data-stu-id="88093-123">To rename a table</span></span>  
  
1.  <span data-ttu-id="88093-124">在对象资源管理器中，右键单击要重命名的表，然后从快捷菜单中选择“设计”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="88093-124">In Object Explorer, right-click the table you want to rename and choose **Design** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="88093-125">从 **“视图”** 菜单上选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="88093-125">From the **View** menu, choose **Properties**.</span></span>  
  
3.  <span data-ttu-id="88093-126">在 **“属性”** 窗口的 **“名称”** 值字段中，为该表键入新名称。</span><span class="sxs-lookup"><span data-stu-id="88093-126">In the field for the **Name** value in the **Properties** window, type a new name for the table.</span></span>  
  
4.  <span data-ttu-id="88093-127">若要取消此操作，请在离开此字段前按 Esc 键。</span><span class="sxs-lookup"><span data-stu-id="88093-127">To cancel this action, press the ESC key before leaving this field.</span></span>  
  
5.  <span data-ttu-id="88093-128">从 "**文件**" 菜单中选择 "**保存**_表名_"。</span><span class="sxs-lookup"><span data-stu-id="88093-128">From the **File** menu choose **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="88093-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="88093-129">Using Transact-SQL</span></span>  
  
#### <a name="to-rename-a-table"></a><span data-ttu-id="88093-130">重命名表</span><span class="sxs-lookup"><span data-stu-id="88093-130">To rename a table</span></span>  
  
1.  <span data-ttu-id="88093-131">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="88093-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="88093-132">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="88093-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="88093-133">下面的示例将 `SalesTerritory` 架构中的 `SalesTerr` 表重命名为 `Sales` 。</span><span class="sxs-lookup"><span data-stu-id="88093-133">The following example renames the `SalesTerritory` table to `SalesTerr` in the `Sales` schema.</span></span> <span data-ttu-id="88093-134">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="88093-134">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    EXEC sp_rename 'Sales.SalesTerritory', 'SalesTerr';  
    ```  
  
 <span data-ttu-id="88093-135">有关其他示例，请参阅 [sp_rename (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="88093-135">For additional examples, see [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).</span></span>  
  
  
