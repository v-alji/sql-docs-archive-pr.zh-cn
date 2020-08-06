---
title: 创建视图 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], creating
ms.assetid: 0b7bd2a1-544c-42ba-8e7b-4822f34d7b64
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8280f6d65d7252cad423abef849207111492c044
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577460"
---
# <a name="create-views"></a><span data-ttu-id="51408-102">创建视图</span><span class="sxs-lookup"><span data-stu-id="51408-102">Create Views</span></span>
  <span data-ttu-id="51408-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中创建视图。</span><span class="sxs-lookup"><span data-stu-id="51408-103">You can create views in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="51408-104">可以将视图用于以下用途：</span><span class="sxs-lookup"><span data-stu-id="51408-104">A view can be used for the following purposes:</span></span>  
  
-   <span data-ttu-id="51408-105">集中、简化和自定义每个用户对数据库的认识。</span><span class="sxs-lookup"><span data-stu-id="51408-105">To focus, simplify, and customize the perception each user has of the database.</span></span>  
  
-   <span data-ttu-id="51408-106">用作安全机制，方法是允许用户通过视图访问数据，而不授予用户直接访问底层基表的权限。</span><span class="sxs-lookup"><span data-stu-id="51408-106">As a security mechanism by allowing users to access data through the view, without granting the users permissions to directly access the underlying base tables.</span></span>  
  
-   <span data-ttu-id="51408-107">提供向后兼容接口来模拟架构已更改的表。</span><span class="sxs-lookup"><span data-stu-id="51408-107">To provide a backward compatible interface to emulate a table whose schema has changed.</span></span>  
  
 <span data-ttu-id="51408-108">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="51408-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="51408-109">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="51408-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="51408-110">限制和局限</span><span class="sxs-lookup"><span data-stu-id="51408-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="51408-111">安全性</span><span class="sxs-lookup"><span data-stu-id="51408-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="51408-112">**创建视图，使用：**</span><span class="sxs-lookup"><span data-stu-id="51408-112">**To create a view, using:**</span></span>  
  
     [<span data-ttu-id="51408-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="51408-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="51408-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="51408-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="51408-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="51408-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="51408-116">限制和局限</span><span class="sxs-lookup"><span data-stu-id="51408-116">Limitations and Restrictions</span></span>  
 <span data-ttu-id="51408-117">只能在当前数据库中创建视图。</span><span class="sxs-lookup"><span data-stu-id="51408-117">A view can be created only in the current database.</span></span>  
  
 <span data-ttu-id="51408-118">视图最多可以包含 1,024 列。</span><span class="sxs-lookup"><span data-stu-id="51408-118">A view can have a maximum of 1,024 columns.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="51408-119">Security</span><span class="sxs-lookup"><span data-stu-id="51408-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="51408-120">权限</span><span class="sxs-lookup"><span data-stu-id="51408-120">Permissions</span></span>  
 <span data-ttu-id="51408-121">要求在数据库中具有 CREATE VIEW 权限，并具有在其中创建视图的架构的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="51408-121">Requires CREATE VIEW permission in the database and ALTER permission on the schema in which the view is being created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="51408-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="51408-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-view-by-using-the-query-and-view-designer"></a><span data-ttu-id="51408-123">使用查询和视图设计器创建视图</span><span class="sxs-lookup"><span data-stu-id="51408-123">To create a view by using the Query and View Designer</span></span>  
  
1.  <span data-ttu-id="51408-124">在 **“对象资源管理器”** 中，展开要创建新视图的数据库。</span><span class="sxs-lookup"><span data-stu-id="51408-124">In **Object Explorer**, expand the database where you want to create your new view.</span></span>  
  
2.  <span data-ttu-id="51408-125">右键单击“视图”文件夹，然后单击“新建视图...”   。</span><span class="sxs-lookup"><span data-stu-id="51408-125">Right-click the **Views** folder, then click **New View...**.</span></span>  
  
3.  <span data-ttu-id="51408-126">在 **“添加表”** 对话框中，从以下选项卡之一选择要在新视图中包含的元素：“表”、“视图”、“函数”和“同义词”。</span><span class="sxs-lookup"><span data-stu-id="51408-126">In the **Add Table** dialog box, select the element or elements that you want to include in your new view from one of the following tabs: Tables, Views, Functions, and Synonyms.</span></span>  
  
4.  <span data-ttu-id="51408-127">单击 **“添加”** ，再单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="51408-127">Click **Add**, then click **Close**.</span></span>  
  
5.  <span data-ttu-id="51408-128">在 **“关系图窗格”** 中，选择要在新视图中包含的列或其他元素。</span><span class="sxs-lookup"><span data-stu-id="51408-128">In the **Diagram Pane**, select the columns or other elements to include in the new view.</span></span>  
  
6.  <span data-ttu-id="51408-129">在 **“条件窗格”** 中，选择列的其他排序或筛选条件。</span><span class="sxs-lookup"><span data-stu-id="51408-129">In the **Criteria Pane**, select additional sort or filter criteria for the columns.</span></span>  
  
7.  <span data-ttu-id="51408-130">在“文件”  菜单上，单击“保存”  以保存_视图名称_。</span><span class="sxs-lookup"><span data-stu-id="51408-130">On the **File** menu, click **Save**_view name_.</span></span>  
  
8.  <span data-ttu-id="51408-131">在 **“选择名称”** 对话框中，输入新视图的名称并单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="51408-131">In the **Choose Name** dialog box, enter a name for the new view and click **OK**.</span></span>  
  
     <span data-ttu-id="51408-132">有关查询和视图设计器的详细信息，请参阅[查询和视图设计器工具（可视化数据库工具）](../../ssms/visual-db-tools/visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="51408-132">For more information about the query and view designer, see [Query and View Designer Tools &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="51408-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="51408-133">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-view"></a><span data-ttu-id="51408-134">创建视图</span><span class="sxs-lookup"><span data-stu-id="51408-134">To create a view</span></span>  
  
1.  <span data-ttu-id="51408-135">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="51408-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="51408-136">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="51408-136">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="51408-137">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="51408-137">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    CREATE VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID ;   
    GO  
    -- Query the view  
    SELECT FirstName, LastName, HireDate  
    FROM HumanResources.EmployeeHireDate  
    ORDER BY LastName;  
  
    ```  
  
 <span data-ttu-id="51408-138">有关详细信息，请参阅 [CREATE VIEW (Transact-SQL)](/sql/t-sql/statements/create-view-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="51408-138">For more information, see [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).</span></span>  
  
  
