---
title: 使用计划指南指定查询参数化行为 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- TEMPLATE plan guide
- PARAMETERIZATION FORCED option
- PARAMETERIZATION option
- PARAMETERIZATION SIMPLE option
- parameterization [SQL Server]
- overriding parameterization behavior
- plan guides [SQL Server], parameterization
- parameterized queries [SQL Server]
ms.assetid: f0f738ff-2819-4675-a8c8-1eb6c210a7e6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f595b9f0e0a6d7bceffc5cb283c60b6f40e025b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591302"
---
# <a name="specify-query-parameterization-behavior-by-using-plan-guides"></a><span data-ttu-id="bebe1-102">使用计划指南指定查询参数化行为</span><span class="sxs-lookup"><span data-stu-id="bebe1-102">Specify Query Parameterization Behavior by Using Plan Guides</span></span>
  <span data-ttu-id="bebe1-103">当 PARAMETERIZATION 数据库选项设置为 SIMPLE 时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 查询优化器可以选择参数化查询。</span><span class="sxs-lookup"><span data-stu-id="bebe1-103">When the PARAMETERIZATION database option is set to SIMPLE, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] query optimizer may choose to parameterize the queries.</span></span> <span data-ttu-id="bebe1-104">这意味着查询中包含的任何文字值都用参数来替换。</span><span class="sxs-lookup"><span data-stu-id="bebe1-104">This means that any literal values that are contained in a query are substituted with parameters.</span></span> <span data-ttu-id="bebe1-105">此过程称为简单参数化。</span><span class="sxs-lookup"><span data-stu-id="bebe1-105">This process is referred to as simple parameterization.</span></span> <span data-ttu-id="bebe1-106">SIMPLE 参数化生效后，将无法控制参数化哪些查询，不参数化哪些查询。</span><span class="sxs-lookup"><span data-stu-id="bebe1-106">When SIMPLE parameterization is in effect, you cannot control which queries are parameterized and which queries are not.</span></span> <span data-ttu-id="bebe1-107">不过，您可以通过将 PARAMETERIZATION 数据库选项设置为 FORCED 来指定参数化数据库中的所有查询。</span><span class="sxs-lookup"><span data-stu-id="bebe1-107">However, you can specify that all queries in a database be parameterized by setting the PARAMETERIZATION database option to FORCED.</span></span> <span data-ttu-id="bebe1-108">此过程称为强制参数化。</span><span class="sxs-lookup"><span data-stu-id="bebe1-108">This process is referred to as forced parameterization.</span></span>  
  
 <span data-ttu-id="bebe1-109">可以通过下列方式使用计划指南来覆盖数据库的参数化行为：</span><span class="sxs-lookup"><span data-stu-id="bebe1-109">You can override the parameterization behavior of a database by using plan guides in the following ways:</span></span>  
  
-   <span data-ttu-id="bebe1-110">当 PARAMETERIZATION 数据库选项设置为 SIMPLE 时，您可以指定对某一类查询尝试执行强制参数化。</span><span class="sxs-lookup"><span data-stu-id="bebe1-110">When the PARAMETERIZATION database option is set to SIMPLE, you can specify that forced parameterization is attempted on a certain class of queries.</span></span> <span data-ttu-id="bebe1-111">可以通过在查询的参数化表单上创建 TEMPLATE 计划指南并在 [sp_create_plan_guide](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) 存储过程中指定 PARAMETERIZATION FORCED 查询提示来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="bebe1-111">You do this by creating a TEMPLATE plan guide on the parameterized form of the query, and specifying the PARAMETERIZATION FORCED query hint in the [sp_create_plan_guide](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) stored procedure.</span></span> <span data-ttu-id="bebe1-112">您可以将此种计划指南看作只对某一类查询（而不是所有查询）启用强制参数化的方法。</span><span class="sxs-lookup"><span data-stu-id="bebe1-112">You can consider this kind of plan guide as a way to enable forced parameterization only on a certain class of queries, instead of all queries.</span></span>  
  
-   <span data-ttu-id="bebe1-113">当 PARAMETERIZATION 数据库选项设置为 FORCED 时，您可以指定对某一类查询仅尝试执行简单参数化而非强制参数化。</span><span class="sxs-lookup"><span data-stu-id="bebe1-113">When the PARAMETERIZATION database option is set to FORCED, you can specify that for a certain class of queries, only simple parameterization is attempted, not forced parameterization.</span></span> <span data-ttu-id="bebe1-114">可以通过在查询的强制参数化表单上创建 TEMPLATE 计划指南并在 **sp_create_plan_guide**中指定 PARAMETERIZATION SIMPLE 查询提示来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="bebe1-114">You do this by creating a TEMPLATE plan guide on the force-parameterized form of the query, and specifying the PARAMETERIZATION SIMPLE query hint in **sp_create_plan_guide**.</span></span>  
  
 <span data-ttu-id="bebe1-115">请考虑 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库的以下查询：</span><span class="sxs-lookup"><span data-stu-id="bebe1-115">Consider the following query on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database:</span></span>  
  
```  
SELECT pi.ProductID, SUM(pi.Quantity) AS Total  
FROM Production.ProductModel AS pm   
    INNER JOIN Production.ProductInventory AS pi   
        ON pm.ProductModelID = pi.ProductID   
WHERE pi.ProductID = 101   
GROUP BY pi.ProductID, pi.Quantity HAVING SUM(pi.Quantity) > 50;  
```  
  
 <span data-ttu-id="bebe1-116">作为数据库管理员，您已确定不想对数据库中的所有查询启用强制参数化。</span><span class="sxs-lookup"><span data-stu-id="bebe1-116">As a database administrator, you have determined that you do not want to enable forced parameterization on all queries in the database.</span></span> <span data-ttu-id="bebe1-117">不过，您确实想避免所有语法上与前一个查询相同而只是常量文字值不同的查询的编译开销。</span><span class="sxs-lookup"><span data-stu-id="bebe1-117">However, you do want to avoid compilation costs on all queries that are syntactically equivalent to the previous query, but differ only in their constant literal values.</span></span> <span data-ttu-id="bebe1-118">换句话说，您想参数化该查询，使此种查询的查询计划可以再次使用。</span><span class="sxs-lookup"><span data-stu-id="bebe1-118">In other words, you want the query to be parameterized so that a query plan for this kind of query is reused.</span></span> <span data-ttu-id="bebe1-119">在此情况下，请完成下列步骤：</span><span class="sxs-lookup"><span data-stu-id="bebe1-119">In this case, complete the following steps:</span></span>  
  
1.  <span data-ttu-id="bebe1-120">检索查询的参数化表单。</span><span class="sxs-lookup"><span data-stu-id="bebe1-120">Retrieve the parameterized form of the query.</span></span> <span data-ttu-id="bebe1-121">获取此值以用于 **sp_create_plan_guide** 的唯一安全方法是使用 [sp_get_query_template](/sql/relational-databases/system-stored-procedures/sp-get-query-template-transact-sql) 系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="bebe1-121">The only safe way to obtain this value for use in **sp_create_plan_guide** is by using the [sp_get_query_template](/sql/relational-databases/system-stored-procedures/sp-get-query-template-transact-sql) system stored procedure.</span></span>  
  
2.  <span data-ttu-id="bebe1-122">请指定 PARAMETERIZATION FORCED 查询提示以对查询的参数化表单创建计划指南。</span><span class="sxs-lookup"><span data-stu-id="bebe1-122">Create the plan guide on the parameterized form of the query, specifying the PARAMETERIZATION FORCED query hint.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="bebe1-123">作为参数化查询的一部分， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 根据文字的值和大小，将数据类型分配给替换文字值的参数。</span><span class="sxs-lookup"><span data-stu-id="bebe1-123">As part of parameterizing a query, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assigns a data type to the parameters that replace the literal values, depending on the value and size of the literal.</span></span> <span data-ttu-id="bebe1-124">对于传递给 sp_get_query_template 的 output 参数的常量文本值，将发生相同的过程 **@stmt** 。 **sp_get_query_template**</span><span class="sxs-lookup"><span data-stu-id="bebe1-124">The same process occurs to the value of the constant literals passed to the **@stmt** output parameter of **sp_get_query_template**.</span></span> <span data-ttu-id="bebe1-125">由于在 sp_create_plan_guide 的参数中指定的数据类型 **@params** 必须与参数的参数化查询的数据类型**sp_create_plan_guide**匹配 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，因此您可能需要创建多个计划指南以涵盖查询的可能参数值的完整范围。</span><span class="sxs-lookup"><span data-stu-id="bebe1-125">Because the data type specified in the **@params** argument of **sp_create_plan_guide** must match that of the query as it is parameterized by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you may have to create more than one plan guide to cover the complete range of possible parameter values for the query.</span></span>  
  
 <span data-ttu-id="bebe1-126">以下脚本既可用于获取参数化查询也可用于之后对其创建计划指南：</span><span class="sxs-lookup"><span data-stu-id="bebe1-126">The following script can be used both to obtain the parameterized query and then create a plan guide on it:</span></span>  
  
```  
DECLARE @stmt nvarchar(max);  
DECLARE @params nvarchar(max);  
EXEC sp_get_query_template   
    N'SELECT pi.ProductID, SUM(pi.Quantity) AS Total   
      FROM Production.ProductModel AS pm   
      INNER JOIN Production.ProductInventory AS pi ON pm.ProductModelID = pi.ProductID   
      WHERE pi.ProductID = 101   
      GROUP BY pi.ProductID, pi.Quantity   
      HAVING sum(pi.Quantity) > 50',  
    @stmt OUTPUT,   
    @params OUTPUT;  
EXEC sp_create_plan_guide   
    N'TemplateGuide1',   
    @stmt,   
    N'TEMPLATE',   
    NULL,   
    @params,   
    N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
 <span data-ttu-id="bebe1-127">同样，在已启用强制参数化的数据库中，可以确保按照简单参数化规则对示例查询以及其他语法相同但常量文字值不同的查询进行参数化。</span><span class="sxs-lookup"><span data-stu-id="bebe1-127">Similarly, in a database in which forced parameterization is already enabled, you can make sure that the sample query, and others that are syntactically equivalent, except for their constant literal values, are parameterized according to the rules of simple parameterization.</span></span> <span data-ttu-id="bebe1-128">若要实现此目的，请在 OPTION 子句中指定 PARAMETERIZATION SIMPLE 而不指定 PARAMETERIZATION FORCED。</span><span class="sxs-lookup"><span data-stu-id="bebe1-128">To do this, specify PARAMETERIZATION SIMPLE instead of PARAMETERIZATION FORCED in the OPTION clause.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bebe1-129">TEMPLATE 计划指南使语句与在仅包含单个语句的批处理中提交的查询匹配。</span><span class="sxs-lookup"><span data-stu-id="bebe1-129">TEMPLATE plan guides match statements to queries submitted in batches that consist of a single statement only.</span></span> <span data-ttu-id="bebe1-130">多语句批处理中的语句通过 TEMPLATE 计划指南进行匹配是不合格的。</span><span class="sxs-lookup"><span data-stu-id="bebe1-130">Statements inside multistatement batches are not eligible to be matched by TEMPLATE plan guides.</span></span>  
  
  
