---
title: 删除表（数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table deletions [SQL Server]
- deleting tables
- removing tables
- dropping tables
ms.assetid: ca6aa3e9-9885-44c3-bafc-aec441fd97ec
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1e361456534f565f854d348bbef5751c7d66c0f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692332"
---
# <a name="delete-tables-database-engine"></a><span data-ttu-id="d7db7-102">删除表（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="d7db7-102">Delete Tables (Database Engine)</span></span>
  <span data-ttu-id="d7db7-103">您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中从您的数据库中删除表。</span><span class="sxs-lookup"><span data-stu-id="d7db7-103">You can delete (drop) a table from your database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="d7db7-104">删除表之前一定要慎重考虑。</span><span class="sxs-lookup"><span data-stu-id="d7db7-104">Think carefully before you delete a table.</span></span> <span data-ttu-id="d7db7-105">如果现有查询、视图、用户定义函数、存储过程或程序引用该表，删除操作将使这些对象无效。</span><span class="sxs-lookup"><span data-stu-id="d7db7-105">If existing queries, views, user-defined functions, stored procedures, or programs refer to that table, the deletion will make these objects invalid.</span></span>  
  
 <span data-ttu-id="d7db7-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="d7db7-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d7db7-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="d7db7-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d7db7-108">限制和局限</span><span class="sxs-lookup"><span data-stu-id="d7db7-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="d7db7-109">安全性</span><span class="sxs-lookup"><span data-stu-id="d7db7-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d7db7-110">**使用以下工具删除表：**</span><span class="sxs-lookup"><span data-stu-id="d7db7-110">**To Delete a Table, using:**</span></span>  
  
     [<span data-ttu-id="d7db7-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d7db7-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d7db7-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d7db7-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d7db7-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="d7db7-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d7db7-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="d7db7-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="d7db7-115">不能删除被 FOREIGN KEY 约束引用的表。</span><span class="sxs-lookup"><span data-stu-id="d7db7-115">You cannot drop a table that is referenced by a FOREIGN KEY constraint.</span></span> <span data-ttu-id="d7db7-116">必须先删除引用 FOREIGN KEY 约束或引用表。</span><span class="sxs-lookup"><span data-stu-id="d7db7-116">The referencing FOREIGN KEY constraint or the referencing table must first be dropped.</span></span> <span data-ttu-id="d7db7-117">如果要在同一个 DROP TABLE 语句中删除引用表以及包含主键的表，则必须先列出引用表。</span><span class="sxs-lookup"><span data-stu-id="d7db7-117">If both the referencing table and the table that holds the primary key are being dropped in the same DROP TABLE statement, the referencing table must be listed first.</span></span>  
  
-   <span data-ttu-id="d7db7-118">删除表时，表的规则或默认值将被解除绑定，与该表关联的任何约束或触发器将被自动删除。</span><span class="sxs-lookup"><span data-stu-id="d7db7-118">When a table is dropped, rules or defaults on the table lose their binding, and any constraints or triggers associated with the table are automatically dropped.</span></span> <span data-ttu-id="d7db7-119">如果要重新创建表，则必须重新绑定相应的规则和默认值，重新创建某些触发器，并添加所有必需的约束。</span><span class="sxs-lookup"><span data-stu-id="d7db7-119">If you re-create a table, you must rebind the appropriate rules and defaults, re-create any triggers, and add all required constraints.</span></span>  
  
-   <span data-ttu-id="d7db7-120">如果删除的表包含带有 FILESTREAM 属性的 `varbinary (max)` 列，则不会删除在文件系统中存储的任何数据。</span><span class="sxs-lookup"><span data-stu-id="d7db7-120">If you drop a table that contains a `varbinary (max)` column with the FILESTREAM attribute, any data stored in the file system will not be removed.</span></span>  
  
-   <span data-ttu-id="d7db7-121">不应在同一个批处理中对同一个表执行 DROP TABLE 和 CREATE TABLE。</span><span class="sxs-lookup"><span data-stu-id="d7db7-121">DROP TABLE and CREATE TABLE should not be executed on the same table in the same batch.</span></span> <span data-ttu-id="d7db7-122">否则，可能出现意外错误。</span><span class="sxs-lookup"><span data-stu-id="d7db7-122">Otherwise an unexpected error may occur.</span></span>  
  
-   <span data-ttu-id="d7db7-123">任何引用已删除表的视图或存储过程都必须显式删除或修改，以便删除对该表的引用。</span><span class="sxs-lookup"><span data-stu-id="d7db7-123">Any view or stored procedure that references the dropped table must be explicitly deleted or modified to remove the reference to the table.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d7db7-124">Security</span><span class="sxs-lookup"><span data-stu-id="d7db7-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d7db7-125">权限</span><span class="sxs-lookup"><span data-stu-id="d7db7-125">Permissions</span></span>  
 <span data-ttu-id="d7db7-126">需要拥有该表所属架构的 ALTER 权限、该表的 CONTROL 权限或 **db_ddladmin** 固定数据库角色中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="d7db7-126">Requires ALTER permission on the schema to which the table belongs, CONTROL permission on the table, or membership in the **db_ddladmin** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d7db7-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d7db7-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-table-from-the-database"></a><span data-ttu-id="d7db7-128">从数据库中删除表</span><span class="sxs-lookup"><span data-stu-id="d7db7-128">To delete a table from the database</span></span>  
  
1.  <span data-ttu-id="d7db7-129">在对象资源管理器中选择要删除的表。</span><span class="sxs-lookup"><span data-stu-id="d7db7-129">In Object Explorer, select the table you want to delete.</span></span>  
  
2.  <span data-ttu-id="d7db7-130">右键单击该表，再从快捷菜单中选择“删除”  。</span><span class="sxs-lookup"><span data-stu-id="d7db7-130">Right-click the table and choose **Delete** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="d7db7-131">此时，将显示一个消息框，提示您确认删除。</span><span class="sxs-lookup"><span data-stu-id="d7db7-131">A message box prompts you to confirm the deletion.</span></span> <span data-ttu-id="d7db7-132">单击“是”  。</span><span class="sxs-lookup"><span data-stu-id="d7db7-132">Click **Yes**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d7db7-133">删除一个表将自动移除与该表之间的所有关系。</span><span class="sxs-lookup"><span data-stu-id="d7db7-133">Deleting a table automatically removes any relationships to it.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d7db7-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d7db7-134">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-table-in-query-editor"></a><span data-ttu-id="d7db7-135">在查询编辑器中删除表</span><span class="sxs-lookup"><span data-stu-id="d7db7-135">To delete a table in Query Editor</span></span>  
  
1.  <span data-ttu-id="d7db7-136">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="d7db7-136">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d7db7-137">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="d7db7-137">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d7db7-138">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="d7db7-138">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    DROP TABLE dbo.PurchaseOrderDetail;  
  
    ```  
  
 <span data-ttu-id="d7db7-139">有关详细信息，请参阅 [DROP TABLE (Transact-SQL)](/sql/t-sql/statements/drop-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d7db7-139">For more information, see [DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql)</span></span>  
  
  
