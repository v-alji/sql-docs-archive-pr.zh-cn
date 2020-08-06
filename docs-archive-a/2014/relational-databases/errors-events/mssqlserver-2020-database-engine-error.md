---
title: MSSQLSERVER_2020 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2020 (Database Engine error)
ms.assetid: 4a8bf90f-a083-4c53-84f0-d23c711c8081
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5939267c37e90e7b8456dc01a4af79545e775656
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589622"
---
# <a name="mssqlserver_2020"></a><span data-ttu-id="9348b-102">MSSQLSERVER_2020</span><span class="sxs-lookup"><span data-stu-id="9348b-102">MSSQLSERVER_2020</span></span>
    
## <a name="details"></a><span data-ttu-id="9348b-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="9348b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9348b-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="9348b-104">Product Name</span></span>|<span data-ttu-id="9348b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9348b-105">SQL Server</span></span>|  
|<span data-ttu-id="9348b-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="9348b-106">Event ID</span></span>|<span data-ttu-id="9348b-107">2020</span><span class="sxs-lookup"><span data-stu-id="9348b-107">2020</span></span>|  
|<span data-ttu-id="9348b-108">事件源</span><span class="sxs-lookup"><span data-stu-id="9348b-108">Event Source</span></span>|<span data-ttu-id="9348b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9348b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9348b-110">组件</span><span class="sxs-lookup"><span data-stu-id="9348b-110">Component</span></span>|<span data-ttu-id="9348b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9348b-111">SQLEngine</span></span>|  
|<span data-ttu-id="9348b-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="9348b-112">Symbolic Name</span></span>||  
|<span data-ttu-id="9348b-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="9348b-113">Message Text</span></span>|<span data-ttu-id="9348b-114">为实体“%.\*ls”报告的依赖关系不包含对列的引用。</span><span class="sxs-lookup"><span data-stu-id="9348b-114">The dependencies reported for entity "%.\*ls" do not include references to columns.</span></span> <span data-ttu-id="9348b-115">这是由于此实体引用的对象不存在，或由于此实体中的一个或多个语句有错误。</span><span class="sxs-lookup"><span data-stu-id="9348b-115">This is either because the entity references an object that does not exist or because of an error in one or more statements in the entity.</span></span>  <span data-ttu-id="9348b-116">在重新运行该查询之前，请确保该实体中没有错误并且该实体引用的所有对象都存在。</span><span class="sxs-lookup"><span data-stu-id="9348b-116">Before rerunning the query, ensure that there are no errors in the entity and that all objects referenced by the entity exist.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9348b-117">说明</span><span class="sxs-lookup"><span data-stu-id="9348b-117">Explanation</span></span>  
 <span data-ttu-id="9348b-118">**sys.dm_sql_referenced_entities** 系统函数将报告绑定到架构的引用的所有列级依赖关系。</span><span class="sxs-lookup"><span data-stu-id="9348b-118">The **sys.dm_sql_referenced_entities** system function will report any column-level dependency for schema-bound references.</span></span> <span data-ttu-id="9348b-119">例如，此函数将报告索引视图的所有列级依赖关系，因为索引视图需要架构绑定。</span><span class="sxs-lookup"><span data-stu-id="9348b-119">For example, the function will report all column-level dependencies for an indexed view because an indexed view requires schema binding.</span></span> <span data-ttu-id="9348b-120">但是，如果被引用实体不绑定到架构，则仅当引用列的所有语句可以绑定时，才会报告列依赖关系。</span><span class="sxs-lookup"><span data-stu-id="9348b-120">However, when the referenced entity is not schema-bound, column dependencies are reported only when all statements in which the columns are referenced can be bound.</span></span> <span data-ttu-id="9348b-121">只有在分析语句时所有对象都存在，才可以成功绑定语句。</span><span class="sxs-lookup"><span data-stu-id="9348b-121">Statements can be successfully bound only if all objects exist at the time the statements are parsed.</span></span> <span data-ttu-id="9348b-122">如果实体中有任何已定义的语句无法进行绑定，将不会报告列依赖关系，并且 **referenced_minor_id** 列将返回 0。</span><span class="sxs-lookup"><span data-stu-id="9348b-122">If any statement defined in the entity fails to bind, column dependencies will not be reported and the **referenced_minor_id** column will return 0.</span></span> <span data-ttu-id="9348b-123">无法解析列依赖关系时，将引发错误 2020。</span><span class="sxs-lookup"><span data-stu-id="9348b-123">When column dependencies cannot be resolved, error 2020 is raised.</span></span> <span data-ttu-id="9348b-124">此错误不会阻止查询返回对象级依赖关系。</span><span class="sxs-lookup"><span data-stu-id="9348b-124">This error does not prevent the query from returning object-level dependencies.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9348b-125">用户操作</span><span class="sxs-lookup"><span data-stu-id="9348b-125">User Action</span></span>  
 <span data-ttu-id="9348b-126">更正消息中在错误 2020 之前标识的所有错误。</span><span class="sxs-lookup"><span data-stu-id="9348b-126">Correct any errors identified in the message before error 2020.</span></span> <span data-ttu-id="9348b-127">例如，在以下代码示例中，视图 `Production.ApprovedDocuments` 在 `Title` 表的列`ChangeNumber`、`Status` 和 `Production.Document` 中定义。</span><span class="sxs-lookup"><span data-stu-id="9348b-127">For example, in the following code example the view `Production.ApprovedDocuments` is defined on the columns `Title`, `ChangeNumber`, and `Status` in the `Production.Document` table.</span></span> <span data-ttu-id="9348b-128">随后向 **sys.dm_sql_referenced_entities** 系统函数查询 `ApprovedDocuments` 视图所依赖的对象和列。</span><span class="sxs-lookup"><span data-stu-id="9348b-128">The **sys.dm_sql_referenced_entities** system function is queried for the objects and columns on which the `ApprovedDocuments` view depends.</span></span> <span data-ttu-id="9348b-129">因为视图不是使用 WITH SCHEMA_BINDING 子句创建的，所以可以在被引用表中修改视图中引用的列。</span><span class="sxs-lookup"><span data-stu-id="9348b-129">Because the view is not created using the WITH SCHEMA_BINDING clause, the columns referenced in the view can be modified in the referenced table.</span></span> <span data-ttu-id="9348b-130">该示例通过将 `ChangeNumber` 表中的列 `Production.Document` 重命名为 `TrackingNumber` 对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="9348b-130">The example alters the column `ChangeNumber` in the `Production.Document` table by renaming it to `TrackingNumber`.</span></span> <span data-ttu-id="9348b-131">将再次向目录视图查询 `ApprovedDocuments` 视图；但是它不能绑定到该视图中定义的所有列。</span><span class="sxs-lookup"><span data-stu-id="9348b-131">The catalog view is queried again for the `ApprovedDocuments` view; however it cannot bind to all the columns defined in the view.</span></span> <span data-ttu-id="9348b-132">将返回错误 207 和 2020 来标识问题。</span><span class="sxs-lookup"><span data-stu-id="9348b-132">Errors 207 and 2020 are returned identifying the problem.</span></span> <span data-ttu-id="9348b-133">若要解决问题，必须改变视图，以反映列的新名称。</span><span class="sxs-lookup"><span data-stu-id="9348b-133">To resolve the problem, the view must be altered to reflect the new name of the column.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `CREATE VIEW Production.ApprovedDocuments`  
  
 `AS`  
  
 `SELECT Title, ChangeNumber, Status`  
  
 `FROM Production.Document`  
  
 `WHERE Status = 2;`  
  
 `GO`  
  
 `SELECT referenced_schema_name AS schema_name`  
  
 `,referenced_entity_name AS table_name`  
  
 `,referenced_minor_name AS referenced_column`  
  
 `FROM sys.dm_sql_referenced_entities ('Production.ApprovedDocuments', 'OBJECT');`  
  
 `GO`  
  
 `EXEC sp_rename 'Production.Document.ChangeNumber', 'TrackingNumber', 'COLUMN';`  
  
 `GO`  
  
 `SELECT referenced_schema_name AS schema_name`  
  
 `,referenced_entity_name AS table_name`  
  
 `,referenced_minor_name AS referenced_column`  
  
 `FROM sys.dm_sql_referenced_entities ('Production.ApprovedDocuments', 'OBJECT');`  
  
 `GO`  
  
 <span data-ttu-id="9348b-134">该查询返回以下错误消息。</span><span class="sxs-lookup"><span data-stu-id="9348b-134">The query returns the following error messages.</span></span>  
  
 `Msg 207, Level 16, State 1, Procedure ApprovedDocuments, Line 3`  
  
 `Invalid column name 'ChangeNumber'.`  
  
 `Msg 2020, Level 16, State 1, Line 1`  
  
 `The dependencies reported for entity`  
  
 `"Production.ApprovedDocuments" do not include references to`  
  
 `columns. This is either because the entity references an`  
  
 `object that does not exist or because of an error in one or`  
  
 `more statements in the entity. Before rerunning the query,`  
  
 `ensure that there are no errors in the entity and that all`  
  
 `objects referenced by the entity exist.`  
  
 <span data-ttu-id="9348b-135">以下示例更正了视图中的列名。</span><span class="sxs-lookup"><span data-stu-id="9348b-135">The following example corrects the column name in the view.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `ALTER VIEW Production.ApprovedDocuments`  
  
 `AS`  
  
 `SELECT Title,TrackingNumber, Status`  
  
 `FROM Production.Document`  
  
 `WHERE Status = 2;`  
  
 `GO`  
  
## <a name="see-also"></a><span data-ttu-id="9348b-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9348b-136">See Also</span></span>  
 [<span data-ttu-id="9348b-137">sys.dm_sql_referenced_entities (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9348b-137">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
  
