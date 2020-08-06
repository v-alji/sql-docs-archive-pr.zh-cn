---
title: 查看表的依赖关系 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table dependencies [SQL Server]
- dependencies [SQL Server], tables
- displaying dependences
- viewing dependencies
ms.assetid: c4351ef5-e7d0-46e7-8367-88695e9974f8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 20f54b913124cdaa8a7dfeebac01ba070cc37d88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591822"
---
# <a name="view-the-dependencies-of-a-table"></a><span data-ttu-id="1e9fb-102">查看表的依赖关系</span><span class="sxs-lookup"><span data-stu-id="1e9fb-102">View the Dependencies of a Table</span></span>
  <span data-ttu-id="1e9fb-103">可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中查看表的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="1e9fb-103">You can view a table's dependencies in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1e9fb-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="1e9fb-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1e9fb-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="1e9fb-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1e9fb-106">安全性</span><span class="sxs-lookup"><span data-stu-id="1e9fb-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1e9fb-107">使用以下工具查看表的依赖关系：</span><span class="sxs-lookup"><span data-stu-id="1e9fb-107">**To view a table's dependencies, using:**</span></span>  
  
     [<span data-ttu-id="1e9fb-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1e9fb-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1e9fb-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1e9fb-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1e9fb-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="1e9fb-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1e9fb-111">Security</span><span class="sxs-lookup"><span data-stu-id="1e9fb-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1e9fb-112">权限</span><span class="sxs-lookup"><span data-stu-id="1e9fb-112">Permissions</span></span>  
 <span data-ttu-id="1e9fb-113">要求对数据库具有 VIEW DEFINITION 权限，并对数据库的 sys.sql_expression_dependencies 具有 SELECT 权限。</span><span class="sxs-lookup"><span data-stu-id="1e9fb-113">Requires VIEW DEFINITION permission on the database and SELECT permission on sys.sql_expression_dependencies for the database.</span></span> <span data-ttu-id="1e9fb-114">默认情况下，SELECT 权限仅授予 db_owner 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="1e9fb-114">By default, SELECT permission is granted only to members of the db_owner fixed database role.</span></span> <span data-ttu-id="1e9fb-115">将 SELECT 和 VIEW DEFINITION 权限授予其他用户时，被授权者可以查看数据库中的所有依赖关系。</span><span class="sxs-lookup"><span data-stu-id="1e9fb-115">When SELECT and VIEW DEFINITION permissions are granted to another user, the grantee can view all dependencies in the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1e9fb-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1e9fb-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-dependencies-of-a-table"></a><span data-ttu-id="1e9fb-117">查看表的依赖关系</span><span class="sxs-lookup"><span data-stu-id="1e9fb-117">To view the dependencies of a table</span></span>  
  
1.  <span data-ttu-id="1e9fb-118">在 **“对象资源管理器”** 中，展开 **“数据库”** ，再展开其中的某个数据库，然后展开 **“表”** 。</span><span class="sxs-lookup"><span data-stu-id="1e9fb-118">In **Object Explorer**, expand **Databases**, expand a database, and then expand **Tables**.</span></span>  
  
2.  <span data-ttu-id="1e9fb-119">右键单击某个表，然后单击“查看依赖关系”。</span><span class="sxs-lookup"><span data-stu-id="1e9fb-119">Right-click a table, and then click **View Dependencies**.</span></span>  
  
3.  <span data-ttu-id="1e9fb-120">在“对象依赖关系 \<object name>”对话框中，选择“依赖于 \<object name> 的对象”或“\<object name> 依赖的对象”  。</span><span class="sxs-lookup"><span data-stu-id="1e9fb-120">In the **Object Dependencies**_\<object name>_ dialog box, select either **Objects that depend on** _\<object name>_, or **Objects on which**_\<object name>_**depends**.</span></span>  
  
4.  <span data-ttu-id="1e9fb-121">在 **“依赖关系”** 网格中选择一个对象。</span><span class="sxs-lookup"><span data-stu-id="1e9fb-121">Select an object in the **Dependencies** grid.</span></span> <span data-ttu-id="1e9fb-122">对象类型（如“触发器”或“存储过程”）显示在“类型”框中。</span><span class="sxs-lookup"><span data-stu-id="1e9fb-122">The type of object (such as "Trigger" or "Stored Procedure"), appears in the **Type** box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1e9fb-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1e9fb-123">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-objects-that-depend-on-a-table"></a><span data-ttu-id="1e9fb-124">查看依赖于表的对象</span><span class="sxs-lookup"><span data-stu-id="1e9fb-124">To view the objects that depend on a table</span></span>  
  
1.  <span data-ttu-id="1e9fb-125">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="1e9fb-125">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1e9fb-126">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="1e9fb-126">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1e9fb-127">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="1e9fb-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT * FROM sys.sql_expression_dependencies  
    WHERE referencing_id = OBJECT_ID(N'Production.vProductAndDescription');   
    GO  
  
    ```  
  
#### <a name="to-view-the-objects-on-which-a-table-depends"></a><span data-ttu-id="1e9fb-128">查看表依赖的对象</span><span class="sxs-lookup"><span data-stu-id="1e9fb-128">To view the objects on which a table depends</span></span>  
  
1.  <span data-ttu-id="1e9fb-129">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="1e9fb-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1e9fb-130">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="1e9fb-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1e9fb-131">下面的示例返回依赖于表 `Production.Product`的对象。</span><span class="sxs-lookup"><span data-stu-id="1e9fb-131">The following example returns the objects that depend on the table `Production.Product`.</span></span> <span data-ttu-id="1e9fb-132">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="1e9fb-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    SELECT * FROM sys.sql_expression_dependencies  
    WHERE referenced_id = OBJECT_ID(N'Production.Product');   
    GO  
  
    ```  
  
 <span data-ttu-id="1e9fb-133">有关其他信息，请参阅 [sys.sql_expression_dependencies (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="1e9fb-133">For additional information, see [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)</span></span>  
  
  
