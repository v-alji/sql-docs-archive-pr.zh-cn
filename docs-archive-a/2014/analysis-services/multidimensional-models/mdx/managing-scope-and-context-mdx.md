---
title: " (MDX) 管理作用域和上下文 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [MDX], context
- scope [MDX]
- CALCULATE statement
- This function [MDX]
- SCOPE statement
- scripts [MDX], scope
ms.assetid: 631e7c20-8be9-4c35-8609-76516aef19d1
author: minewiskan
ms.author: owend
ms.openlocfilehash: f7cf1e6cea8df00b632e114a5a8756373738ca6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580935"
---
# <a name="managing-scope-and-context-mdx"></a><span data-ttu-id="4d32a-102">管理作用域和上下文 (MDX)</span><span class="sxs-lookup"><span data-stu-id="4d32a-102">Managing Scope and Context (MDX)</span></span>
  <span data-ttu-id="4d32a-103">在中 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ， (MDX) 脚本的多维表达式可以应用于整个多维数据集，也可以应用于多维数据集的特定部分（在脚本执行中的特定点）。</span><span class="sxs-lookup"><span data-stu-id="4d32a-103">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], a Multidimensional Expressions (MDX) script can apply to the entire cube, or to specific portions of the cube, at specific points within the execution of the script.</span></span> <span data-ttu-id="4d32a-104">MDX 脚本可以通过使用计算传递采取分层方法在多维数据集内进行计算。</span><span class="sxs-lookup"><span data-stu-id="4d32a-104">The MDX script can take a layered approach to calculations within a cube through the use of calculation passes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d32a-105">有关计算传递如何影响计算的详细信息，请参阅[理解传递次序和求解次序 (MDX)](mdx-data-manipulation-understanding-pass-order-and-solve-order.md)。</span><span class="sxs-lookup"><span data-stu-id="4d32a-105">For more information on how calculation passes can affect calculations, see [Understanding Pass Order and Solve Order &#40;MDX&#41;](mdx-data-manipulation-understanding-pass-order-and-solve-order.md).</span></span>  
  
 <span data-ttu-id="4d32a-106">若要控制 MDX 脚本中的计算传递、作用域以及上下文，可以明确使用 CACULATE 语句、`This` 函数以及 SCOPE 语句。</span><span class="sxs-lookup"><span data-stu-id="4d32a-106">To control the calculation pass, scope, and context within an MDX script, you specifically use the CACULATE statement, the `This` function, and the SCOPE statement.</span></span>  
  
## <a name="using-the-calculate-statement"></a><span data-ttu-id="4d32a-107">使用 CALCULATE 语句</span><span class="sxs-lookup"><span data-stu-id="4d32a-107">Using the CALCULATE Statement</span></span>  
 <span data-ttu-id="4d32a-108">CALCULATE 语句用聚合数据填充多维数据集中的每个单元。</span><span class="sxs-lookup"><span data-stu-id="4d32a-108">The CALCULATE statement populates each cell in the cube with aggregated data.</span></span> <span data-ttu-id="4d32a-109">例如，默认 MDX 脚本在脚本的开始处有一个 CALCULATE 语句。</span><span class="sxs-lookup"><span data-stu-id="4d32a-109">For example, the default MDX script has a single CALCULATE statement at the beginning of the script.</span></span>  
  
 <span data-ttu-id="4d32a-110">有关 CALCULATE 语句的语法详细信息，请参阅 [CALCULATE 语句 (MDX)](/sql/mdx/mdx-scripting-calculate)。</span><span class="sxs-lookup"><span data-stu-id="4d32a-110">For more information on the syntax of the CALCULATE statement, see [CALCULATE Statement &#40;MDX&#41;](/sql/mdx/mdx-scripting-calculate).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d32a-111">如果脚本包含含有 CALCULATE 语句的 SCOPE 语句，MDX 将在由 SCOPE 语句定义的子多维数据集的上下文内计算 CALCULATE 语句，而不是针对整个多维数据集进行计算。</span><span class="sxs-lookup"><span data-stu-id="4d32a-111">If the script contains a SCOPE statement that contains a CALCULATE statement, MDX evaluates the CALCULATE statement within the context of the subcube defined by the SCOPE statement, not against the whole cube.</span></span>  
  
## <a name="using-the-this-function"></a><span data-ttu-id="4d32a-112">使用 This 函数</span><span class="sxs-lookup"><span data-stu-id="4d32a-112">Using the This Function</span></span>  
 <span data-ttu-id="4d32a-113">`This` 函数使您可以在 MDX 脚本内检索当前的子多维数据集。</span><span class="sxs-lookup"><span data-stu-id="4d32a-113">The `This` function lets you retrieve the current subcube within an MDX script.</span></span> <span data-ttu-id="4d32a-114">您可以使用 `This` 函数快速将当前子多维数据集内的单元的值设置为 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="4d32a-114">You can use the `This` function to quickly set the value of cells within the current subcube to an MDX expression.</span></span> <span data-ttu-id="4d32a-115">在特定计算传递过程中，通常将 `This` 函数和 SCOPE 语句一起使用，以更改特定子多维数据集的内容。</span><span class="sxs-lookup"><span data-stu-id="4d32a-115">You often use the `This` function in conjunction with the SCOPE statement to change the contents of a specific subcube during a specific calculation pass.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d32a-116">如果脚本包含含有 `This` 函数的 SCOPE 语句，MDX 将在由 SCOPE 语句定义的子多维数据集的上下文内计算 `This` 函数，而不是针对整个多维数据集进行计算。</span><span class="sxs-lookup"><span data-stu-id="4d32a-116">If the script contains a SCOPE statement that contains a `This` function, MDX evaluates the `This` function within the context of the subcube defined by the SCOPE statement, not against the whole cube.</span></span>  
  
### <a name="this-function-example"></a><span data-ttu-id="4d32a-117">This 函数的示例</span><span class="sxs-lookup"><span data-stu-id="4d32a-117">This Function Example</span></span>  
 <span data-ttu-id="4d32a-118">在 [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] 示例多维数据集的 Finance 度量值组中，以下 MDX 脚本命令示例使用 `This` 函数将 Customer 维度中 Redmond 成员的子级的 Amount 度量值增加 10%：</span><span class="sxs-lookup"><span data-stu-id="4d32a-118">The following MDX script command example uses the `This` function to increase the value of the Amount measure, in the Finance measure group of the [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] sample cube, to 10% higher for the children of the Redmond member in the Customer dimension:</span></span>  
  
```  
/* This SCOPE statement defines the current subcube */  
SCOPE([Customer].&[Redmond].MEMBERS,   
    [Measures].[Amount], *);  
        /* This expression sets the value of the Amount measure */  
        THIS = [Measures].[Amount] * 1.1;  
END SCOPE;  
```  
  
 <span data-ttu-id="4d32a-119">有关函数的语法的详细信息 `This` ，请参阅[此 &#40;MDX&#41;](/sql/mdx/this-mdx)。</span><span class="sxs-lookup"><span data-stu-id="4d32a-119">For more information on the syntax of the `This` function, see [This &#40;MDX&#41;](/sql/mdx/this-mdx).</span></span>  
  
## <a name="using-the-scope-statement"></a><span data-ttu-id="4d32a-120">使用 SCOPE 语句</span><span class="sxs-lookup"><span data-stu-id="4d32a-120">Using the SCOPE Statement</span></span>  
 <span data-ttu-id="4d32a-121">SCOPE 语句定义包含 MDX 脚本内其他 MDX 表达式和语句并指定这些表达式和语句的作用域的当前子多维数据集。</span><span class="sxs-lookup"><span data-stu-id="4d32a-121">The SCOPE statement defines the current subcube that contains, and specifies the scope of, other MDX expressions and statements within an MDX script.</span></span> <span data-ttu-id="4d32a-122">MDX 在该子多维数据集的上下文内计算其他 MDX 表达式和语句，包括 `This` 函数和 CALCULATE 语句。</span><span class="sxs-lookup"><span data-stu-id="4d32a-122">MDX evaluates this other MDX expressions and statements, including the `This` function and the CALCULATE statement, within the context of the subcube.</span></span>  
  
 <span data-ttu-id="4d32a-123">SCOPE 语句本质上是动态的，但不是迭代的。</span><span class="sxs-lookup"><span data-stu-id="4d32a-123">A SCOPE statement is dynamic, but not iterative in nature.</span></span> <span data-ttu-id="4d32a-124">SCOPE 语句中包含的语句运行一次，但子多维数据集本身可以动态确定。</span><span class="sxs-lookup"><span data-stu-id="4d32a-124">The statements contained within a SCOPE statement run once, but the subcube itself can be dynamically determined.</span></span> <span data-ttu-id="4d32a-125">例如，有一个名为 SampleCube 的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="4d32a-125">For example, you have a cube named SampleCube.</span></span> <span data-ttu-id="4d32a-126">对 SampleCube 多维数据集应用以下 SCOPE 语句以定义一个子多维数据集，将上下文定义为 Measures 维度内的 ALLMEMBERS：</span><span class="sxs-lookup"><span data-stu-id="4d32a-126">Against the SampleCube cube, you apply the following SCOPE statement to define a subcube the defines the context as the ALLMEMBERS within the Measures dimension:</span></span>  
  
 `SCOPE([Measures].ALLMEMBERS);`  
  
 `THIS = [Measures].ALLMEMBERS.COUNT;`  
  
 `END SCOPE;`  
  
 <span data-ttu-id="4d32a-127">此 SCOPE 语句中包含的语句和表达式运行一次。</span><span class="sxs-lookup"><span data-stu-id="4d32a-127">The statements and expressions within this SCOPE statement run once.</span></span>  
  
 <span data-ttu-id="4d32a-128">现在，商业用户对 SampleCube 多维数据集运行以下 MDX 查询，该查询包含一个名为 ExistingMeasure 的度量值：</span><span class="sxs-lookup"><span data-stu-id="4d32a-128">Now, a business user runs the following MDX query that contains one measure, named ExistingMeasure, against the SampleCube cube:</span></span>  
  
 `WITH MEMBER [Measures].[NewMeasure] AS '1'`  
  
 `SELECT`  
  
 `[Measures].ALLMEMBERS ON COLUMNS,`  
  
 `[Customer].DEFAULTMEMBER ON ROWS`  
  
 `FROM`  
  
 `[SampleCube]`  
  
 <span data-ttu-id="4d32a-129">查询所返回的单元集与下表中显示的输出相似。</span><span class="sxs-lookup"><span data-stu-id="4d32a-129">The cellset returned from the query resembles the output shown in the following table.</span></span>  
  
||<span data-ttu-id="4d32a-130">[ExistingMeasure]</span><span class="sxs-lookup"><span data-stu-id="4d32a-130">[ExistingMeasure]</span></span>|<span data-ttu-id="4d32a-131">[NewMeasure]</span><span class="sxs-lookup"><span data-stu-id="4d32a-131">[NewMeasure]</span></span>|  
|-|-------------------------|--------------------|  
|<span data-ttu-id="4d32a-132">[Customer].[All]</span><span class="sxs-lookup"><span data-stu-id="4d32a-132">[Customer].[All]</span></span>|<span data-ttu-id="4d32a-133">2</span><span class="sxs-lookup"><span data-stu-id="4d32a-133">2</span></span>|<span data-ttu-id="4d32a-134">2</span><span class="sxs-lookup"><span data-stu-id="4d32a-134">2</span></span>|  
  
 <span data-ttu-id="4d32a-135">查看返回的单元集时，请注意定义度量值 NewMeasure 后，MDX 脚本中的 SCOPE 语句包含的 ExistingMeasure 值是如何动态更新的。</span><span class="sxs-lookup"><span data-stu-id="4d32a-135">Looking at the returned cellset, notice how the ExistingMeasure value, included in the SCOPE statement within the MDX script, is dynamically updated after the measure NewMeasure was defined.</span></span>  
  
 <span data-ttu-id="4d32a-136">一个 SCOPE 语句可以嵌套在另一个 SCOPE 语句内。</span><span class="sxs-lookup"><span data-stu-id="4d32a-136">A SCOPE statement can be nested within another SCOPE statement.</span></span> <span data-ttu-id="4d32a-137">但是，由于 SCOPE 语句不是迭代的，因此嵌套 SCOPE 语句的主要目的是进一步细分子多维数据集，以进行特殊的处理。</span><span class="sxs-lookup"><span data-stu-id="4d32a-137">However, as the SCOPE statement is not iterative, the primary purpose for nesting SCOPE statements is to further subdivide a subcube for special treatment.</span></span>  
  
### <a name="scope-statement-example"></a><span data-ttu-id="4d32a-138">SCOPE 语句的示例</span><span class="sxs-lookup"><span data-stu-id="4d32a-138">SCOPE Statement Example</span></span>  
 <span data-ttu-id="4d32a-139">在 [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] 示例多维数据集的 Finance 度量值组中，以下 MDX 脚本示例使用 SCOPE 语句将 Customer 维度中 Redmond 成员的子级的 Amount 度量值的值设置为比原来增加 10%。</span><span class="sxs-lookup"><span data-stu-id="4d32a-139">The following MDX script example uses a SCOPE statement to sets the value of the Amount measure, in the Finance measure group of the [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] sample cube, to 10% higher for the children of the Redmond member in the Customer dimension.</span></span> <span data-ttu-id="4d32a-140">但是，另一个 SCOPE 语句将子多维数据集更改为包含 2002 日历年子级的 Amount 度量值。</span><span class="sxs-lookup"><span data-stu-id="4d32a-140">However, another SCOPE statement changes the subcube to include the Amount measure for the children of the 2002 calendar year.</span></span> <span data-ttu-id="4d32a-141">最后，仅为该子多维数据集聚合 Amount 度量值，其他日历年中 Amount 度量值的聚合值则保持不变。</span><span class="sxs-lookup"><span data-stu-id="4d32a-141">Finally, the Amount measure is then aggregated only for that subcube, leaving the aggregated values for the Amount measure in other calendar years unchanged.</span></span>  
  
```  
/* Calculate the entire cube first. */  
CALCULATE;  
/* This SCOPE statement defines the current subcube */  
SCOPE([Customer].&[Redmond].MEMBERS,   
    [Measures].[Amount], *);  
        /* This expression sets the value of the Amount measure */  
        THIS = [Measures].[Amount] * 1.1;  
END SCOPE;  
```  
  
 <span data-ttu-id="4d32a-142">有关 SCOPE 语句的语法详细信息，请参阅 [SCOPE 语句 (MDX)](/sql/mdx/mdx-scripting-scope)。</span><span class="sxs-lookup"><span data-stu-id="4d32a-142">For more information on the syntax of the SCOPE statement, see [SCOPE Statement &#40;MDX&#41;](/sql/mdx/mdx-scripting-scope).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d32a-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4d32a-143">See Also</span></span>  
 <span data-ttu-id="4d32a-144">[Mdx 语言参考 &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="4d32a-144">[MDX Language Reference &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span></span>  
 <span data-ttu-id="4d32a-145">[基本 MDX 脚本 &#40;MDX&#41;](the-basic-mdx-script-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="4d32a-145">[The Basic MDX Script &#40;MDX&#41;](the-basic-mdx-script-mdx.md) </span></span>  
 [<span data-ttu-id="4d32a-146">MDX 查询基础知识 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="4d32a-146">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
