---
title: 创建新的计划指南 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.designer.newplanguide.f1
helpviewer_keywords:
- creating plan guides
- plan guides [SQL Server]. creating
ms.assetid: e1ad78bb-4857-40ea-a0c6-dcf5c28aef2f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 60ba31e2a63575a316db5befb397bea59c0ad1e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591314"
---
# <a name="create-a-new-plan-guide"></a><span data-ttu-id="ad61a-102">创建新的计划指南</span><span class="sxs-lookup"><span data-stu-id="ad61a-102">Create a New Plan Guide</span></span>
  <span data-ttu-id="ad61a-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中创建计划指南。</span><span class="sxs-lookup"><span data-stu-id="ad61a-103">You can create a plan guide in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ad61a-104">计划指南通过将查询提示或现有查询计划附加到查询来影响查询优化。</span><span class="sxs-lookup"><span data-stu-id="ad61a-104">Plan guides influence query optimization by attaching query hints or a fixed query plan to them.</span></span> <span data-ttu-id="ad61a-105">在计划指南中，您需要指定要优化的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句以及包含要使用的查询提示的 OPTION 子句或要用于优化查询的特定查询计划。</span><span class="sxs-lookup"><span data-stu-id="ad61a-105">In the plan guide, you specify the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that you want optimized and either an OPTION clause that contains the query hints you want to use or a specific query plan you want to use to optimize the query.</span></span> <span data-ttu-id="ad61a-106">当查询执行时，查询优化器会将相应 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句与计划指南进行匹配，然后在运行时将此 OPTION 子句附加到查询，或使用指定的查询计划。</span><span class="sxs-lookup"><span data-stu-id="ad61a-106">When the query executes, the query optimizer matches the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to the plan guide and either attaches the OPTION clause to the query at run time or uses the specified query plan.</span></span>  
  
 <span data-ttu-id="ad61a-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="ad61a-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ad61a-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="ad61a-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ad61a-109">限制和局限</span><span class="sxs-lookup"><span data-stu-id="ad61a-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ad61a-110">安全性</span><span class="sxs-lookup"><span data-stu-id="ad61a-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ad61a-111">**若要创建计划指南，请使用：**</span><span class="sxs-lookup"><span data-stu-id="ad61a-111">**To create a plan guide, using:**</span></span>  
  
     [<span data-ttu-id="ad61a-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ad61a-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ad61a-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ad61a-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ad61a-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="ad61a-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ad61a-115">限制和局限</span><span class="sxs-lookup"><span data-stu-id="ad61a-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="ad61a-116">sp_create_plan_guide 的参数必须以显示的顺序提供。</span><span class="sxs-lookup"><span data-stu-id="ad61a-116">The arguments to sp_create_plan_guide must be provided in the order that is shown.</span></span> <span data-ttu-id="ad61a-117">为 `sp_create_plan_guide` 的参数提供值时，所有参数名称都必须显式指定，或全部不指定。</span><span class="sxs-lookup"><span data-stu-id="ad61a-117">When you supply values for the parameters of `sp_create_plan_guide`, all parameter names must be specified explicitly, or none at all.</span></span> <span data-ttu-id="ad61a-118">例如，如果指定了 `@name =`，则也必须指定 `@stmt =`、`@type =` 等。</span><span class="sxs-lookup"><span data-stu-id="ad61a-118">For example, if `@name =` is specified, then `@stmt =` , `@type =`, and so on, must also be specified.</span></span> <span data-ttu-id="ad61a-119">同样，如果省略了 `@name =` 并仅提供了参数值，则其余的参数名称也必须省略并仅提供它们的值。</span><span class="sxs-lookup"><span data-stu-id="ad61a-119">Likewise, if `@name =` is omitted and only the parameter value is provided, the remaining parameter names must also be omitted, and only their values provided.</span></span> <span data-ttu-id="ad61a-120">参数名称仅用于说明，以帮助了解语法。</span><span class="sxs-lookup"><span data-stu-id="ad61a-120">Argument names are for descriptive purposes only, to help understand the syntax.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ad61a-121">不会验证指定的参数名称是否与使用此名称的位置中的参数名称相匹配。</span><span class="sxs-lookup"><span data-stu-id="ad61a-121">does not verify that the specified parameter name matches the name for the parameter in the position where the name is used.</span></span>  
  
-   <span data-ttu-id="ad61a-122">您可以为相同的查询和批处理或模块创建多个 OBJECT 或 SQL 计划指南。</span><span class="sxs-lookup"><span data-stu-id="ad61a-122">You can create more than one OBJECT or SQL plan guide for the same query and batch or module.</span></span> <span data-ttu-id="ad61a-123">但是，在任何给定的时间只能启用一个计划指南。</span><span class="sxs-lookup"><span data-stu-id="ad61a-123">However, only one plan guide can be enabled at any given time.</span></span>  
  
-   <span data-ttu-id="ad61a-124">无法为引用存储过程、函数或 DML 触发器（指定了 WITH ENCRYPTION 子句或为临时触发器）的 @module_or_batch 值创建 OBJECT 类型的计划指南。</span><span class="sxs-lookup"><span data-stu-id="ad61a-124">Plan guides of type OBJECT cannot be created for an @module_or_batch value that references a stored procedure, function, or DML trigger that specifies the WITH ENCRYPTION clause or that is temporary.</span></span>  
  
-   <span data-ttu-id="ad61a-125">如果尝试删除或修改的函数、存储过程或 DML 触发器由某个计划指南引用，则不管该指南为启用状态还是禁用状态，都会导致错误。</span><span class="sxs-lookup"><span data-stu-id="ad61a-125">Trying to drop or modify a function, stored procedure, or DML trigger that is referenced by a plan guide, either enabled or disabled, causes an error.</span></span> <span data-ttu-id="ad61a-126">尝试删除计划指南被引用并已为其定义触发器的表也将导致错误。</span><span class="sxs-lookup"><span data-stu-id="ad61a-126">Trying to drop a table that has a trigger defined on it that is referenced by a plan guide also causes an error.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ad61a-127">Security</span><span class="sxs-lookup"><span data-stu-id="ad61a-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ad61a-128">权限</span><span class="sxs-lookup"><span data-stu-id="ad61a-128">Permissions</span></span>  
 <span data-ttu-id="ad61a-129">若要创建类型为 OBJECT 的计划指南，需要拥有对被引用对象的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="ad61a-129">To create a plan guide of type OBJECT, requires ALTER permission on the referenced object.</span></span> <span data-ttu-id="ad61a-130">若要创建类型为 SQL 或 TEMPLATE 的计划指南，需要拥有对当前数据库的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="ad61a-130">To create a plan guide of type SQL or TEMPLATE, requires ALTER permission on the current database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ad61a-131">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ad61a-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-plan-guide"></a><span data-ttu-id="ad61a-132">创建计划指南</span><span class="sxs-lookup"><span data-stu-id="ad61a-132">To create a plan guide</span></span>  
  
1.  <span data-ttu-id="ad61a-133">单击加号以便展开您要在其中创建计划指南的数据库，然后单击加号以便展开 **“可编程性”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="ad61a-133">Click the plus sign to expand the database in which you want to create a plan guide, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="ad61a-134">右键单击 "**计划指南**" 文件夹，然后选择 "**新建计划指南 ...**"。</span><span class="sxs-lookup"><span data-stu-id="ad61a-134">Right-click the **Plan Guides** folder and select **New Plan Guide...**.</span></span>  
  
3.  <span data-ttu-id="ad61a-135">在 **“新建计划指南”** 对话框的 **“名称”** 框中，输入计划指南的名称。</span><span class="sxs-lookup"><span data-stu-id="ad61a-135">In the **New Plan Guide** dialog box, in the **Name** box, enter the name of the plan guide.</span></span>  
  
4.  <span data-ttu-id="ad61a-136">在 **“语句”** 框中，输入要对其应用计划指南的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="ad61a-136">In the **Statement** box, enter the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement against which the plan guide is to be applied.</span></span>  
  
5.  <span data-ttu-id="ad61a-137">在 **“作用域类型”** 列表中，选择 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句在其中出现的实体的类型。</span><span class="sxs-lookup"><span data-stu-id="ad61a-137">In the **Scope type** list, select the type of entity in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span> <span data-ttu-id="ad61a-138">这便指定了用于将 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句与计划指南匹配的上下文。</span><span class="sxs-lookup"><span data-stu-id="ad61a-138">This specifies the context for matching the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to the plan guide.</span></span> <span data-ttu-id="ad61a-139">可能的值为 **OBJECT**、 **SQL**和 **TEMPLATE**。</span><span class="sxs-lookup"><span data-stu-id="ad61a-139">Possible values are **OBJECT**, **SQL**, and **TEMPLATE**.</span></span>  
  
6.  <span data-ttu-id="ad61a-140">在 **“作用域批处理”** 框中，请输入其中出现 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的批处理文本。</span><span class="sxs-lookup"><span data-stu-id="ad61a-140">In the **Scope batch** box, enter the batch text in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span> <span data-ttu-id="ad61a-141">批处理文本不能包括 USE\`\`*database* 语句。</span><span class="sxs-lookup"><span data-stu-id="ad61a-141">The batch text cannot include a USE\`\`*database* statement.</span></span> <span data-ttu-id="ad61a-142">只有在 **SQL** 选择为作用域类型时， **“作用域批处理”** 框才可用。</span><span class="sxs-lookup"><span data-stu-id="ad61a-142">The **Scope batch** box is only available when **SQL** is selected as a scope type.</span></span> <span data-ttu-id="ad61a-143">如果在 SQL 为作用域类型时在“作用域批处理”框中未输入任何内容，则将批处理文本的值设置为与 **“语句”** 框中相同的值。</span><span class="sxs-lookup"><span data-stu-id="ad61a-143">If nothing is entered in the scope batch box when SQL is the scope type, then the value of the batch text is set to the same value as is in the **Statement** box.</span></span>  
  
7.  <span data-ttu-id="ad61a-144">在 **“作用域批处理”** 列表中，输入其中包含该对象的架构的名称。</span><span class="sxs-lookup"><span data-stu-id="ad61a-144">In the **Scope schema name** list, enter the name of the schema in which the object is contained.</span></span> <span data-ttu-id="ad61a-145">只有在 **“对象”** 选择为作用域类型时， **“作用域架构名称”** 框才可用。</span><span class="sxs-lookup"><span data-stu-id="ad61a-145">The **Scope schema name** box is only available when **Object** is selected as a scope type.</span></span>  
  
8.  <span data-ttu-id="ad61a-146">在“作用域对象名称”框中，输入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程的名称、用户定义的标量函数的名称、多语句表值函数的名称或其中出现 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的 DML 触发器的名称。</span><span class="sxs-lookup"><span data-stu-id="ad61a-146">In the **Scope object name** box, enter the name of the [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, user-defined scalar function, multistatement table-valued function, or DML trigger in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span> <span data-ttu-id="ad61a-147">只有在 **“对象”** 选择为作用域类型时， **“作用域对象名称”** 框才可用。</span><span class="sxs-lookup"><span data-stu-id="ad61a-147">The **Scope object name** box is only available when **Object** is selected as a scope type.</span></span>  
  
9. <span data-ttu-id="ad61a-148">在 **“参数”** 框中，输入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句中嵌入的所有参数的参数名称和数据类型。</span><span class="sxs-lookup"><span data-stu-id="ad61a-148">In the **Parameters** box, enter the parameter name and data type of all parameters that are embedded in the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
     <span data-ttu-id="ad61a-149">只有当下列任意一个条件为真时才会应用参数：</span><span class="sxs-lookup"><span data-stu-id="ad61a-149">Parameters apply only when either of the following is true:</span></span>  
  
    -   <span data-ttu-id="ad61a-150">作用域类型为 **SQL** 或 **TEMPLATE**。</span><span class="sxs-lookup"><span data-stu-id="ad61a-150">The scope type is **SQL** or **TEMPLATE**.</span></span> <span data-ttu-id="ad61a-151">如果为 **TEMPLATE**，则参数不能为 NULL。</span><span class="sxs-lookup"><span data-stu-id="ad61a-151">If **TEMPLATE**, parameters must not be NULL.</span></span>  
  
    -   <span data-ttu-id="ad61a-152">[!INCLUDE[tsql](../../includes/tsql-md.md)] 语句使用 sp_executesql 进行提交，并且指定了该参数的值，或者 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在参数化某语句之后内部提交该语句。</span><span class="sxs-lookup"><span data-stu-id="ad61a-152">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is submitted by using sp_executesql and a value for the parameter is specified, or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] internally submits a statement after parameterizing it.</span></span>  
  
10. <span data-ttu-id="ad61a-153">在 **“提示”** 框中，输入要应用于 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的查询提示或查询计划。</span><span class="sxs-lookup"><span data-stu-id="ad61a-153">In the **Hints** box, enter the query hints or query plan to be applied to the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="ad61a-154">若要指定一个或多个查询提示，请输入一个有效的 OPTION 子句。</span><span class="sxs-lookup"><span data-stu-id="ad61a-154">To specify one or more query hints, enter a valid OPTION clause.</span></span>  
  
11. <span data-ttu-id="ad61a-155">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="ad61a-155">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ad61a-156">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ad61a-156">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-plan-guide"></a><span data-ttu-id="ad61a-157">创建计划指南</span><span class="sxs-lookup"><span data-stu-id="ad61a-157">To create a plan guide</span></span>  
  
1.  <span data-ttu-id="ad61a-158">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="ad61a-158">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ad61a-159">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ad61a-159">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ad61a-160">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="ad61a-160">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
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
  
    ```  
  
 <span data-ttu-id="ad61a-161">有关详细信息，请参阅 [sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ad61a-161">For more information, see [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql).</span></span>  
  
  
