---
title: 基本 MDX 脚本 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- default MDX scripts
- statements [MDX]
- expressions [MDX], scripts
- scripts [MDX], about scripts
ms.assetid: 83d9afda-7d34-42b5-8f28-20172a905f23
author: minewiskan
ms.author: owend
ms.openlocfilehash: de0d2fea002beda0eca480bd27140bdd202fcb83
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691947"
---
# <a name="the-basic-mdx-script-mdx"></a><span data-ttu-id="6da3c-102">基本 MDX 脚本 (MDX)</span><span class="sxs-lookup"><span data-stu-id="6da3c-102">The Basic MDX Script (MDX)</span></span>
  <span data-ttu-id="6da3c-103"> (MDX) 脚本的多维表达式定义中多维数据集的计算过程 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6da3c-103">A Multidimensional Expressions (MDX) script defines the calculation process for a cube in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="6da3c-104">有两种类型的 MDX 脚本：</span><span class="sxs-lookup"><span data-stu-id="6da3c-104">There are two types of MDX scripts:</span></span>  
  
 <span data-ttu-id="6da3c-105">**默认 MDX 脚本**</span><span class="sxs-lookup"><span data-stu-id="6da3c-105">**The default MDX script**</span></span>  
 <span data-ttu-id="6da3c-106">当创建多维数据集时， [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 将为该多维数据集创建一个默认的 MDX 脚本。</span><span class="sxs-lookup"><span data-stu-id="6da3c-106">At the time that you create a cube, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] creates a default MDX script for that cube.</span></span> <span data-ttu-id="6da3c-107">此脚本定义整个多维数据集的计算过程。</span><span class="sxs-lookup"><span data-stu-id="6da3c-107">This script defines a calculation pass for the whole cube.</span></span>  
  
 <span data-ttu-id="6da3c-108">**用户定义 MDX 脚本**</span><span class="sxs-lookup"><span data-stu-id="6da3c-108">**User-defined MDX script**</span></span>  
 <span data-ttu-id="6da3c-109">创建多维数据集后，可以添加用户定义 MDX 脚本，以扩展多维数据集的计算功能。</span><span class="sxs-lookup"><span data-stu-id="6da3c-109">After you have created a cube, you can add user-defined MDX scripts that extend the calculation capabilities of the cube.</span></span>  
  
## <a name="the-default-mdx-script"></a><span data-ttu-id="6da3c-110">默认 MDX 脚本</span><span class="sxs-lookup"><span data-stu-id="6da3c-110">The Default MDX Script</span></span>  
 <span data-ttu-id="6da3c-111">定义多维数据集时由 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 创建的默认 MDX 脚本包含单个 CALCULATE 语句。</span><span class="sxs-lookup"><span data-stu-id="6da3c-111">The default MDX script that [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] creates when you define a cube contains a single CALCULATE statement.</span></span> <span data-ttu-id="6da3c-112">这个 CALCULATE 语句位于默认 MDX 脚本的开始处，指明在第一次计算传递过程中应计算整个多维数据集。</span><span class="sxs-lookup"><span data-stu-id="6da3c-112">This single CALCULATE statement is at the beginning of the default MDX script, and indicates that the entire cube should be calculated during the first calculation pass.</span></span>  
  
 <span data-ttu-id="6da3c-113">默认 MDX 脚本还包含用来创建命名集、赋值以及计算成员（在多维数据集设计器中创建）的脚本命令：</span><span class="sxs-lookup"><span data-stu-id="6da3c-113">The default MDX script also contains the script commands that create named sets, assignments, and calculated members created in Cube Designer:</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="6da3c-114">直接将脚本命令添加到默认 MDX 脚本中。</span><span class="sxs-lookup"><span data-stu-id="6da3c-114">directly adds script commands to the default MDX script.</span></span>  
  
-   <span data-ttu-id="6da3c-115">对于多维数据集中的每个命名集，默认 MDX 脚本中都有一个对应的 CREATE SET 语句。</span><span class="sxs-lookup"><span data-stu-id="6da3c-115">For each named set in the cube, a corresponding CREATE SET statement exists in the default MDX script.</span></span>  
  
-   <span data-ttu-id="6da3c-116">对于多维数据集中定义的每个计算成员，默认 MDX 脚本中都有一个对应的 CREATE MEMBER 语句。</span><span class="sxs-lookup"><span data-stu-id="6da3c-116">For each calculated member defined in the cube, a corresponding CREATE MEMBER statement exists in the default MDX script.</span></span>  
  
 <span data-ttu-id="6da3c-117">可以通过使用多维数据集设计器的 **“计算”** 选项卡控制默认 MDX 脚本中的脚本命令、命名集以及计算成员的顺序。</span><span class="sxs-lookup"><span data-stu-id="6da3c-117">You can control the order of script commands, named sets, and calculated members in the default MDX script by using the **Calculations** tab of Cube Designer.</span></span> <span data-ttu-id="6da3c-118">有关定义存储在默认 MDX 脚本中的计算的详细信息，请参阅 [多维模型中的计算](../calculations-in-multidimensional-models.md)。</span><span class="sxs-lookup"><span data-stu-id="6da3c-118">For more information on defining calculations stored in the default MDX script, see [Calculations in Multidimensional Models](../calculations-in-multidimensional-models.md).</span></span>  
  
 <span data-ttu-id="6da3c-119">如果多维数据集没有相关的 MDX 脚本，将使用默认的 MDX 脚本。</span><span class="sxs-lookup"><span data-stu-id="6da3c-119">If there is no MDX script associated with a cube, the cube assumes the default MDX script.</span></span> <span data-ttu-id="6da3c-120">一个多维数据集至少要与一个 MDX 脚本相关联，因为多维数据集依赖于 MDX 脚本来确定计算行为。</span><span class="sxs-lookup"><span data-stu-id="6da3c-120">A cube needs to be associated with at least one MDX script because a cube relies on the MDX script to determine calculation behavior.</span></span> <span data-ttu-id="6da3c-121">也就是说，未与 MDX 脚本关联或与空 MDX 脚本关联的多维数据集不会也不能计算任何单元。</span><span class="sxs-lookup"><span data-stu-id="6da3c-121">In other words, a cube that was not associated with an MDX script or was associated with an empty MDX script could not and would not be able to calculate any cells.</span></span> <span data-ttu-id="6da3c-122">如果使用 Analysis Services 脚本语言 (ASSL) 命令或 Analysis Management Objects (AMO) 通过编程的方式创建多维数据集，建议为该多维数据集创建包含单个 CALCULATE 语句的默认 MDX 脚本。</span><span class="sxs-lookup"><span data-stu-id="6da3c-122">If you programmatically create cubes, either by using Analysis Services Scripting Language (ASSL) commands or by using Analysis Management Objects (AMO), it is recommended that you create a default MDX script containing a single CALCULATE statement for the cube.</span></span>  
  
## <a name="mdx-script-content"></a><span data-ttu-id="6da3c-123">MDX 脚本的内容</span><span class="sxs-lookup"><span data-stu-id="6da3c-123">MDX Script Content</span></span>  
 <span data-ttu-id="6da3c-124">MDX 脚本可以包含下列语句和表达式：</span><span class="sxs-lookup"><span data-stu-id="6da3c-124">An MDX script can contain the following statements and expressions:</span></span>  
  
 <span data-ttu-id="6da3c-125">所有 MDX 脚本语句</span><span class="sxs-lookup"><span data-stu-id="6da3c-125">All MDX scripting statements</span></span>  
 <span data-ttu-id="6da3c-126">在 MDX 脚本中，MDX 脚本语句控制计算的上下文和作用域，并管理 MDX 脚本中其他语句的行为。</span><span class="sxs-lookup"><span data-stu-id="6da3c-126">In MDX scripts, MDX scripting statements control the context and scope of calculations, and manage the behavior of other statements in the MDX script.</span></span> <span data-ttu-id="6da3c-127">此类别包括下列语句：</span><span class="sxs-lookup"><span data-stu-id="6da3c-127">This category includes the following statements:</span></span>  
  
-   [<span data-ttu-id="6da3c-128">计算</span><span class="sxs-lookup"><span data-stu-id="6da3c-128">CALCULATE</span></span>](/sql/mdx/mdx-scripting-calculate)  
  
-   [<span data-ttu-id="6da3c-129">&</span><span class="sxs-lookup"><span data-stu-id="6da3c-129">FREEZE</span></span>](/sql/mdx/mdx-scripting-freeze)  
  
-   [<span data-ttu-id="6da3c-130">内</span><span class="sxs-lookup"><span data-stu-id="6da3c-130">SCOPE</span></span>](/sql/mdx/mdx-scripting-scope)  
  
 <span data-ttu-id="6da3c-131">有关 MDX 脚本编写语句的详细信息，请参阅 [MDX 脚本编写语句](/sql/mdx/mdx-scripting-statements-mdx)。</span><span class="sxs-lookup"><span data-stu-id="6da3c-131">For more information on MDX scripting statements, see [MDX Scripting Statements &#40;MDX&#41;](/sql/mdx/mdx-scripting-statements-mdx).</span></span>  
  
 [<span data-ttu-id="6da3c-132">CREATE MEMBER</span><span class="sxs-lookup"><span data-stu-id="6da3c-132">CREATE MEMBER</span></span>](/sql/mdx/mdx-data-definition-create-member)  
 <span data-ttu-id="6da3c-133">CREATE MEMBER 语句可以创建计算成员。</span><span class="sxs-lookup"><span data-stu-id="6da3c-133">The CREATE MEMBER statement creates calculated members.</span></span> <span data-ttu-id="6da3c-134">有关如何创建计算成员的详细信息，请参阅[在 MDX 中生成计算成员 (MDX)](mdx-calculated-members-building-calculated-members.md)。</span><span class="sxs-lookup"><span data-stu-id="6da3c-134">For more information about how to create calculated members, see [Building Calculated Members in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).</span></span>  
  
 [<span data-ttu-id="6da3c-135">CREATE SET</span><span class="sxs-lookup"><span data-stu-id="6da3c-135">CREATE SET</span></span>](/sql/mdx/mdx-data-definition-create-set)  
 <span data-ttu-id="6da3c-136">CREATE SET 语句可以创建命名集。</span><span class="sxs-lookup"><span data-stu-id="6da3c-136">The CREATE SET statement creates named sets.</span></span> <span data-ttu-id="6da3c-137">有关如何创建命名集的详细信息，请参阅[在 MDX 中生成命名集 (MDX)](mdx-named-sets-building-named-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="6da3c-137">For more information about how to create names sets, see [Building Named Sets in MDX &#40;MDX&#41;](mdx-named-sets-building-named-sets.md).</span></span>  
  
 <span data-ttu-id="6da3c-138">条件语句</span><span class="sxs-lookup"><span data-stu-id="6da3c-138">Conditional statements</span></span>  
 <span data-ttu-id="6da3c-139">条件语句可以将条件逻辑添加到 MDX 脚本中。</span><span class="sxs-lookup"><span data-stu-id="6da3c-139">Conditional statements add conditional logic to MDX scripts.</span></span> <span data-ttu-id="6da3c-140">此类别包括 [CASE](/sql/mdx/case-statement-mdx) 语句和 [IF](/sql/mdx/mdx-scripting-if) 语句。</span><span class="sxs-lookup"><span data-stu-id="6da3c-140">This category includes the [CASE](/sql/mdx/case-statement-mdx) and [IF](/sql/mdx/mdx-scripting-if) statements.</span></span>  
  
 <span data-ttu-id="6da3c-141">赋值表达式</span><span class="sxs-lookup"><span data-stu-id="6da3c-141">Assignment expressions</span></span>  
 <span data-ttu-id="6da3c-142">赋值表达式为受约束的子多维数据集指定表达式，例如值。</span><span class="sxs-lookup"><span data-stu-id="6da3c-142">An assignment expression assigns an expression, such as a value, to a constrained subcube.</span></span> <span data-ttu-id="6da3c-143">受约束的子多维数据集表达式是定义 MDX 脚本中子多维数据集的“边界”的受约束的集表达式的集合。</span><span class="sxs-lookup"><span data-stu-id="6da3c-143">A constrained subcube expression is a collection of constrained set expressions that define the "edges" of a subcube within an MDX script.</span></span> <span data-ttu-id="6da3c-144">下列代码显示了受约束的子多维数据集表达式的语法：</span><span class="sxs-lookup"><span data-stu-id="6da3c-144">The following codes shows the syntax for a constrained subcube expression:</span></span>  
  
```  
<Constrained subcube> ::= (   
    ( <Constrained set> [<Crossjoin operator> <Constrained set>...] |  
    <ROOT function> |  
    <TREE function> |  
    LEAVES() |  
    * ) [, <Constrained subcube>...]  
<Constrained set> ::=   
    <Natural hierarchy>.MEMBERS |   
    <Natural hierarchy>.LEVEL(<numeric expression>).MEMBERS |   
    { <Natural hierarchy member> } |   
    DESCENDANTS( <Natural hierarchy member>, <Level expression>, ( SELF | AFTER | SELF_AND_AFTER ) ) |   
    DESCENDANTS( <Natural hierarchy member>, , LEAVES )  
<Natural hierarchy> ::= <Hierarchy identifier>  
<Natural hierarchy member> ::= <Natural hierarchy>.<identifier>[.<identifier>...]  
```  
  
## <a name="see-also"></a><span data-ttu-id="6da3c-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6da3c-145">See Also</span></span>  
 <span data-ttu-id="6da3c-146">[Mdx 语言参考 &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="6da3c-146">[MDX Language Reference &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span></span>  
 [<span data-ttu-id="6da3c-147">MDX 脚本编写基础知识 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="6da3c-147">MDX Scripting Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-scripting-fundamentals-analysis-services.md)  
  
  
