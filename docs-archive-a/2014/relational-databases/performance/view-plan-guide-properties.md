---
title: 查看计划指南属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.planguideprop.general.f1
helpviewer_keywords:
- plan guides [SQL Server], view plan guide properties
- viewing plan guide properties
ms.assetid: 8c0d2f39-59c1-4168-a649-65473f6a771b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: af29c66690a43f89106c1f77aca8c3a02eff2ba9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689349"
---
# <a name="view-plan-guide-properties"></a><span data-ttu-id="3a179-102">查看计划指南属性</span><span class="sxs-lookup"><span data-stu-id="3a179-102">View Plan Guide Properties</span></span>
  <span data-ttu-id="3a179-103">可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a179-103">You can view the properties of plan guides in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  
 <span data-ttu-id="3a179-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="3a179-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3a179-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="3a179-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3a179-106">安全性</span><span class="sxs-lookup"><span data-stu-id="3a179-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3a179-107">**查看计划指南的属性，使用：**</span><span class="sxs-lookup"><span data-stu-id="3a179-107">**To view the properties of plan guides, using:**</span></span>  
  
     [<span data-ttu-id="3a179-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3a179-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3a179-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3a179-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3a179-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="3a179-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3a179-111">Security</span><span class="sxs-lookup"><span data-stu-id="3a179-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3a179-112">权限</span><span class="sxs-lookup"><span data-stu-id="3a179-112">Permissions</span></span>  
 <span data-ttu-id="3a179-113">目录视图中仅显示用户拥有的安全对象的元数据，或用户对其拥有某些权限的安全对象的元数据。</span><span class="sxs-lookup"><span data-stu-id="3a179-113">The visibility of the metadata in catalog views is limited to securables that either a user owns or on which the user has been granted some permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3a179-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3a179-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-properties-of-a-plan-guide"></a><span data-ttu-id="3a179-115">查看计划指南的属性</span><span class="sxs-lookup"><span data-stu-id="3a179-115">To view the properties of a plan guide</span></span>  
  
1.  <span data-ttu-id="3a179-116">单击加号以便展开您要在其中查看计划指南属性的数据库，然后单击加号以便展开 **“可编程性”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="3a179-116">Click the plus sign to expand the database in which you want to view the properties of a plan guide, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="3a179-117">单击加号以便展开 **“计划指南”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="3a179-117">Click the plus sign to expand the **Plan Guides** folder.</span></span>  
  
3.  <span data-ttu-id="3a179-118">右键单击要查看其属性的计划指南，然后选择“属性”。</span><span class="sxs-lookup"><span data-stu-id="3a179-118">Right-click the plan guide of which you want to view the properties and select **Properties**.</span></span>  
  
     <span data-ttu-id="3a179-119">**“计划指南属性”** 对话框显示以下属性。</span><span class="sxs-lookup"><span data-stu-id="3a179-119">The following properties show in the **Plan Guide Properties** dialog box.</span></span>  
  
     <span data-ttu-id="3a179-120">**提示**</span><span class="sxs-lookup"><span data-stu-id="3a179-120">**Hints**</span></span>  
     <span data-ttu-id="3a179-121">显示要应用于 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的查询提示或查询计划。</span><span class="sxs-lookup"><span data-stu-id="3a179-121">Displays the query hints or query plan to be applied to the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="3a179-122">将查询计划指定为提示时，会显示该计划的 XML 显示计划输出。</span><span class="sxs-lookup"><span data-stu-id="3a179-122">When a query plan is specified as a hint, the XML Showplan output for the plan is displayed.</span></span>  
  
     <span data-ttu-id="3a179-123">**已禁用**</span><span class="sxs-lookup"><span data-stu-id="3a179-123">**Is disabled**</span></span>  
     <span data-ttu-id="3a179-124">显示计划指南的状态。</span><span class="sxs-lookup"><span data-stu-id="3a179-124">Displays the status of the plan guide.</span></span> <span data-ttu-id="3a179-125">可能的值包括 **True** 和 **False**。</span><span class="sxs-lookup"><span data-stu-id="3a179-125">Possible values are **True** and **False**.</span></span>  
  
     <span data-ttu-id="3a179-126">**名称**</span><span class="sxs-lookup"><span data-stu-id="3a179-126">**Name**</span></span>  
     <span data-ttu-id="3a179-127">显示计划指南的名称。</span><span class="sxs-lookup"><span data-stu-id="3a179-127">Displays the name of the plan guide.</span></span>  
  
     <span data-ttu-id="3a179-128">**参数**</span><span class="sxs-lookup"><span data-stu-id="3a179-128">**Parameters**</span></span>  
     <span data-ttu-id="3a179-129">当作用域类型为 SQL 或 TEMPLATE 时，显示嵌入在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句中的所有参数的名称和数据类型。</span><span class="sxs-lookup"><span data-stu-id="3a179-129">When the scope type is SQL or TEMPLATE, displays the name and data type of all parameters that are embedded in the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
     <span data-ttu-id="3a179-130">**作用域批处理**</span><span class="sxs-lookup"><span data-stu-id="3a179-130">**Scope batch**</span></span>  
     <span data-ttu-id="3a179-131">显示其中出现 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的批处理文本。</span><span class="sxs-lookup"><span data-stu-id="3a179-131">Displays the batch text in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span>  
  
     <span data-ttu-id="3a179-132">**作用域对象名称**</span><span class="sxs-lookup"><span data-stu-id="3a179-132">**Scope object name**</span></span>  
     <span data-ttu-id="3a179-133">当作用域类型为 OBJECT 时，显示其中出现 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程、用户定义标量函数、多语句表值函数或 DML 触发器的名称。</span><span class="sxs-lookup"><span data-stu-id="3a179-133">When the scope type is OBJECT, displays the name of the [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, user-defined scalar function, multistatement table-valued function, or DML trigger in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span>  
  
     <span data-ttu-id="3a179-134">**作用域架构名称**</span><span class="sxs-lookup"><span data-stu-id="3a179-134">**Scope schema name**</span></span>  
     <span data-ttu-id="3a179-135">当作用域类型为 OBJECT 时，显示包含此对象的架构的名称。</span><span class="sxs-lookup"><span data-stu-id="3a179-135">When the scope type is OBJECT, displays the name of the schema in which the object is contained.</span></span>  
  
     <span data-ttu-id="3a179-136">**作用域类型**</span><span class="sxs-lookup"><span data-stu-id="3a179-136">**Scope type**</span></span>  
     <span data-ttu-id="3a179-137">显示其中出现 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的实体的类型。</span><span class="sxs-lookup"><span data-stu-id="3a179-137">Displays the type of entity in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span> <span data-ttu-id="3a179-138">这便指定了用于将 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句与计划指南匹配的上下文。</span><span class="sxs-lookup"><span data-stu-id="3a179-138">This specifies the context for matching the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to the plan guide.</span></span> <span data-ttu-id="3a179-139">可能的值为 **OBJECT**、 **SQL**和 **TEMPLATE**。</span><span class="sxs-lookup"><span data-stu-id="3a179-139">Possible values are **OBJECT**, **SQL**, and **TEMPLATE**.</span></span>  
  
     <span data-ttu-id="3a179-140">**Statement**</span><span class="sxs-lookup"><span data-stu-id="3a179-140">**Statement**</span></span>  
     <span data-ttu-id="3a179-141">显示应用此计划指南的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="3a179-141">Displays the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement against which the plan guide is applied.</span></span>  
  
4.  <span data-ttu-id="3a179-142">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="3a179-142">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3a179-143">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3a179-143">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-properties-of-a-plan-guide"></a><span data-ttu-id="3a179-144">查看计划指南的属性</span><span class="sxs-lookup"><span data-stu-id="3a179-144">To view the properties of a plan guide</span></span>  
  
1.  <span data-ttu-id="3a179-145">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="3a179-145">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3a179-146">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="3a179-146">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3a179-147">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="3a179-147">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- If a plan guide named "Guide1" already exists in the AdventureWorks2012 database, delete it.  
    USE AdventureWorks2012;  
    GO  
    IF OBJECT_ID(N'Guide1') IS NOT NULL  
       EXEC sp_control_plan_guide N'DROP', N'Guide1';  
    GO  
    -- creates a plan guide named Guide1 based on a SQL statement  
    EXEC sp_create_plan_guide   
        @name = N'Guide1',   
        @stmt = N'SELECT TOP 1 *   
                  FROM Sales.SalesOrderHeader   
                  ORDER BY OrderDate DESC',   
        @type = N'SQL',  
        @module_or_batch = NULL,   
        @params = NULL,   
        @hints = N'OPTION (MAXDOP 1)';  
    GO  
    -- Gets the name, created date, and all other relevant property information on the plan guide created above.   
    SELECT name AS plan_guide_name,  
       create_date,  
       query_text,  
       scope_type_desc,  
       OBJECT_NAME(scope_object_id) AS scope_object_name,  
       scope_batch,  
       parameters,  
       hints,  
       is_disabled  
    FROM sys.plan_guides  
    WHERE name = N'Guide1';  
    GO  
    ```  
  
 <span data-ttu-id="3a179-148">有关详细信息，请参阅 [sys.plan_guides (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-plan-guides-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3a179-148">For more information, see [sys.plan_guides &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-plan-guides-transact-sql).</span></span>  
  
  
