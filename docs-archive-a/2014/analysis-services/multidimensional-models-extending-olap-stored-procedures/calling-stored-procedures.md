---
title: 调用存储过程 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- stored procedures [Analysis Services], calling
- MDX queries [Analysis Services]
- CALL statement
ms.assetid: 96a9660d-875b-4ee4-b339-90020b1d9895
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c9da6edef576a6ab25c183cbc87ff95cc056845
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689658"
---
# <a name="calling-stored-procedures"></a><span data-ttu-id="ada98-102">调用存储过程</span><span class="sxs-lookup"><span data-stu-id="ada98-102">Calling Stored Procedures</span></span>
  <span data-ttu-id="ada98-103">可以在服务器上或从客户端应用程序中调用存储过程。</span><span class="sxs-lookup"><span data-stu-id="ada98-103">Stored procedures can be called on the server or from client application.</span></span> <span data-ttu-id="ada98-104">在任何一种情况下，存储过程都始终运行于服务器上，或者使用服务器的上下文，或者使用数据库的上下文。</span><span class="sxs-lookup"><span data-stu-id="ada98-104">In either case, stored procedures always run on the server, either the context of the server or of a database.</span></span> <span data-ttu-id="ada98-105">执行存储过程时，不需要具备特殊的权限。</span><span class="sxs-lookup"><span data-stu-id="ada98-105">There are no special permissions required to execute a stored procedure.</span></span> <span data-ttu-id="ada98-106">存储过程由程序集添加到服务器或数据库上下文后，只要用户的角色允许执行存储过程所执行的操作，则任何用户均可执行该存储过程。</span><span class="sxs-lookup"><span data-stu-id="ada98-106">Once a stored procedure is added by an assembly to the server or database context, any user can execute the stored procedure as long as the role for the user permits the actions performed by the stored procedure.</span></span>  
  
 <span data-ttu-id="ada98-107">调用 MDX 中的存储过程是按照与调用内部 MDX 函数相同的方式来完成的。</span><span class="sxs-lookup"><span data-stu-id="ada98-107">Calling a stored procedure in MDX is done in the same manner as calling an intrinsic MDX function.</span></span> <span data-ttu-id="ada98-108">对于不带参数的存储过程，则使用过程名和一对空括号，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ada98-108">For a stored procedure that takes no parameters, the name of the procedure and an empty pair of parentheses are used, as shown here:</span></span>  
  
```  
MyStoredProcedure()  
```  
  
 <span data-ttu-id="ada98-109">如果存储过程有一个或多个参数，就会按顺序提供参数，并用逗号彼此分隔。</span><span class="sxs-lookup"><span data-stu-id="ada98-109">If the stored procedure takes one or more parameters, then the parameters are supplied, in order, separated by commas.</span></span> <span data-ttu-id="ada98-110">下面的示例演示了带有三个参数的示例存储过程：</span><span class="sxs-lookup"><span data-stu-id="ada98-110">The following example demonstrates a sample stored procedure with three parameters:</span></span>  
  
```  
MyStoredProcedure("Parameter1", 2, 800)  
```  
  
## <a name="calling-stored-procedures-in-mdx-queries"></a><span data-ttu-id="ada98-111">在 MDX 查询中调用存储过程</span><span class="sxs-lookup"><span data-stu-id="ada98-111">Calling Stored Procedures in MDX Queries</span></span>  
 <span data-ttu-id="ada98-112">在所有 MDX 查询中，存储过程都必须返回 MDX 表达式所需的正确语法类型。</span><span class="sxs-lookup"><span data-stu-id="ada98-112">In all MDX queries, the stored procedure must return the syntactically correct type required by an MDX expression.</span></span> <span data-ttu-id="ada98-113">如果存储过程未返回正确的类型，则会发生 MDX 错误。</span><span class="sxs-lookup"><span data-stu-id="ada98-113">If a stored procedure does not return the correct type, an MDX error occurs.</span></span> <span data-ttu-id="ada98-114">以下示例所演示的存储过程将返回数学运算的集合、成员和结果。</span><span class="sxs-lookup"><span data-stu-id="ada98-114">The following examples demonstrate stored procedures that return a set, a member, and the result of a mathematical operation.</span></span>  
  
### <a name="returning-a-set"></a><span data-ttu-id="ada98-115">返回集合</span><span class="sxs-lookup"><span data-stu-id="ada98-115">Returning a Set</span></span>  
 <span data-ttu-id="ada98-116">以下示例实现一个名为 MySproc 的存储过程，它将返回一个集合。</span><span class="sxs-lookup"><span data-stu-id="ada98-116">The following examples implement a stored procedure, called MySproc, that returns a set.</span></span> <span data-ttu-id="ada98-117">在第一个示例中，MySproc 直接在 SELECT 表达式中返回集合。</span><span class="sxs-lookup"><span data-stu-id="ada98-117">In the first example, MySproc returns the set directly in the SELECT expression.</span></span> <span data-ttu-id="ada98-118">在后面两个示例中，MySproc 返回的集合是 Crossjoin 和 DrilldownLevel 函数的参数。</span><span class="sxs-lookup"><span data-stu-id="ada98-118">In the second two examples, MySproc returns the set as an argument for the Crossjoin and DrilldownLevel functions.</span></span>  
  
```  
SELECT MySetProcedure(a,b,c) ON 0 FROM Sales  
SELECT Crossjoin(MySetProcedure(a,b,c)) ON 0 FROM Sales  
SELECT DrilldownLevel(MySetProcedure(a,b,c)) ON 0 FROM Sales  
```  
  
### <a name="returning-a-member"></a><span data-ttu-id="ada98-119">返回成员</span><span class="sxs-lookup"><span data-stu-id="ada98-119">Returning a Member</span></span>  
 <span data-ttu-id="ada98-120">以下示例显示返回成员的 MySproc 函数：</span><span class="sxs-lookup"><span data-stu-id="ada98-120">The following example shows a function MySproc function that returns a member:</span></span>  
  
```  
SELECT Descendants(MySproc(a,b,c),3) ON 0 FROM Sales  
```  
  
### <a name="returning-the-result-of-a-math-operation"></a><span data-ttu-id="ada98-121">返回数学运算的结果</span><span class="sxs-lookup"><span data-stu-id="ada98-121">Returning the Result of a Math Operation</span></span>  
  
```  
SELECT Country.Members on 0, MySproc(Measures.Sales) ON 1 FROM Sales  
```  
  
## <a name="calling-stored-procedures-with-the-call-statement"></a><span data-ttu-id="ada98-122">用 Call 语句调用存储过程</span><span class="sxs-lookup"><span data-stu-id="ada98-122">Calling Stored Procedures with the Call Statement</span></span>  
 <span data-ttu-id="ada98-123">使用 MDX `Call` 语句，可以在 MDX 查询的上下文以外调用存储过程。</span><span class="sxs-lookup"><span data-stu-id="ada98-123">Stored procedures can be called outside of the context of an MDX query using the MDX `Call` statement.</span></span>  
  
 <span data-ttu-id="ada98-124">可以使用此方法实例化存储查询的副作用，或让应用程序获得存储查询的结果。</span><span class="sxs-lookup"><span data-stu-id="ada98-124">You can use this method to either instantiate the side effects of a stored query or for the application to get the results of a stored query.</span></span> <span data-ttu-id="ada98-125">`Call` 语句的通常用法是使用分析管理对象 (AMO) 来执行没有返回结果的管理函数。</span><span class="sxs-lookup"><span data-stu-id="ada98-125">A common use of the `Call` statement would be to use Analysis Management Objects (AMO) to perform administrative functions that do not have a return result.</span></span> <span data-ttu-id="ada98-126">例如，以下命令将调用一个存储过程：</span><span class="sxs-lookup"><span data-stu-id="ada98-126">For example, the following command calls a stored procedure:</span></span>  
  
```  
Call MyStoredProcedure(a,b,c)  
```  
  
 <span data-ttu-id="ada98-127">从 `Call` 语句中的存储过程所返回的唯一受支持的类型是行集。</span><span class="sxs-lookup"><span data-stu-id="ada98-127">The only supported type returned from stored procedure in a `Call` statement is a rowset.</span></span> <span data-ttu-id="ada98-128">行集的序列化是由 XML for Analysis 定义的。</span><span class="sxs-lookup"><span data-stu-id="ada98-128">The serialization for a rowset is defined by XML for Analysis.</span></span> <span data-ttu-id="ada98-129">如果 `Call` 语句中的存储过程返回了其他任何类型，则会忽略该类型，并且不会将它放在 XML 中返回给发起调用的应用程序。</span><span class="sxs-lookup"><span data-stu-id="ada98-129">If a stored procedure in a `Call` statement returns any other type, it is ignored and not returned in XML to the calling application.</span></span> <span data-ttu-id="ada98-130">有关 XML for Analysis 行集的详细信息，请参阅“XML for Analysis 架构行集”。</span><span class="sxs-lookup"><span data-stu-id="ada98-130">For more information about XML for Analysis rowsets, see, XML for Analysis Schema Rowsets.</span></span>  
  
 <span data-ttu-id="ada98-131">如果存储过程返回 .NET 行集，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将在服务器中将结果转换为 XML for Analysis 行集。</span><span class="sxs-lookup"><span data-stu-id="ada98-131">If a stored procedure returns a .NET rowset, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] converts the result on the server to an XML for Analysis rowset.</span></span> <span data-ttu-id="ada98-132">XML for Analysis 行集始终由 `Call` 函数中的存储过程返回。</span><span class="sxs-lookup"><span data-stu-id="ada98-132">The XML for Analysis rowset is always returned by a stored procedure in the `Call` function.</span></span> <span data-ttu-id="ada98-133">如果数据集包含了在 XML for Analysis 行集中无法表达的功能，则会产生失败。</span><span class="sxs-lookup"><span data-stu-id="ada98-133">If a dataset contains features that cannot be expressed in the XML for Analysis rowset, a failure results.</span></span>  
  
 <span data-ttu-id="ada98-134">返回 void 值的函数（例如，Visual Basic 中的子例程）也可与 CALL 关键字一起使用。</span><span class="sxs-lookup"><span data-stu-id="ada98-134">Procedures that return void values (for example, subroutines in Visual Basic) can also be employed with the CALL keyword.</span></span> <span data-ttu-id="ada98-135">例如，如果想要在 MDX 语句中使用 MyVoidFunction() 函数，可采用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="ada98-135">If, for example, you wanted to use the function MyVoidFunction() in an MDX statement, the following syntax would be employed:</span></span>  
  
```  
CALL(MyVoidFunction)  
```  
  
## <a name="see-also"></a><span data-ttu-id="ada98-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ada98-136">See Also</span></span>  
 <span data-ttu-id="ada98-137">[多维模型程序集管理](../multidimensional-models/multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="ada98-137">[Multidimensional Model Assemblies Management](../multidimensional-models/multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="ada98-138">定义存储过程</span><span class="sxs-lookup"><span data-stu-id="ada98-138">Defining Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
