---
title: 定义自定义成员公式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- members [Analysis Services], custom
- custom rollup formulas [Analysis Services]
- MDX [Analysis Services], custom rollup formulas
- custom member formulas [Analysis Services]
ms.assetid: 258304e2-d900-4013-97e3-871f51dfdce2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 51649bea0c4134971b342b779c778b857343e62b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693559"
---
# <a name="define-custom-member-formulas"></a><span data-ttu-id="cc7da-102">定义自定义成员公式</span><span class="sxs-lookup"><span data-stu-id="cc7da-102">Define Custom Member Formulas</span></span>
  <span data-ttu-id="cc7da-103">可以定义称为自定义成员公式的多维表达式 (MDX) 表达式，以便为指定属性的成员提供值。</span><span class="sxs-lookup"><span data-stu-id="cc7da-103">You can define a Multidimensional Expressions (MDX) expression, called a custom member formula, to supply the values for the members of a specified attribute.</span></span> <span data-ttu-id="cc7da-104">数据源视图内表中的列为属性中的每个成员提供了用于为其提供值的表达式。</span><span class="sxs-lookup"><span data-stu-id="cc7da-104">A column in a table from a data source view provides, for each member in an attribute, the expression used to supply the value for that member.</span></span>  
  
 <span data-ttu-id="cc7da-105">自定义成员公式确定与成员相关的单元值，并替代度量值的聚合函数。</span><span class="sxs-lookup"><span data-stu-id="cc7da-105">Custom member formulas determine the cell values that are associated with members and override the aggregate functions of measures.</span></span> <span data-ttu-id="cc7da-106">自定义成员公式是以 MDX 编写的。</span><span class="sxs-lookup"><span data-stu-id="cc7da-106">Custom member formulas are written in MDX.</span></span> <span data-ttu-id="cc7da-107">每个自定义成员公式应用于一个成员。</span><span class="sxs-lookup"><span data-stu-id="cc7da-107">Each custom member formula applies to a single member.</span></span> <span data-ttu-id="cc7da-108">自定义成员公式存储在维度表中，或者存储在与维度表具有外键关系的其他表中。</span><span class="sxs-lookup"><span data-stu-id="cc7da-108">Custom member formulas are stored in the dimension table or in another table that has a foreign key relationship with the dimension table.</span></span>  
  
 <span data-ttu-id="cc7da-109">特性的 `CustomRollupColumn` 属性指定包含该特性成员的自定义成员公式的列。</span><span class="sxs-lookup"><span data-stu-id="cc7da-109">The `CustomRollupColumn` property on an attribute specifies the column that contains custom member formulas for members of the attribute.</span></span> <span data-ttu-id="cc7da-110">如果列中的某行为空，则通常返回成员的单元值。</span><span class="sxs-lookup"><span data-stu-id="cc7da-110">If a row in the column is empty, the cell value for the member is returned normally.</span></span> <span data-ttu-id="cc7da-111">如果列中的公式无效，则每当检索使用该成员的单元值时，都会出现运行时错误。</span><span class="sxs-lookup"><span data-stu-id="cc7da-111">If the formula in the column is not valid, a run-time error occurs whenever a cell value that uses the member is retrieved.</span></span>  
  
 <span data-ttu-id="cc7da-112">在为特性指定自定义成员公式前，请确保包含该特性的维度表或直接相关的表具有用于存储自定义成员公式的字符串列。</span><span class="sxs-lookup"><span data-stu-id="cc7da-112">Before you can specify custom member formulas for an attribute, make sure that the dimension table that contains the attribute, or a directly related table, has a string column to store the custom member formulas.</span></span> <span data-ttu-id="cc7da-113">如果是这种情况，则可以 `CustomRollupColumn` 手动设置特性的属性，或使用商业智能向导的 "设置自定义成员公式增强功能" 启用属性的自定义成员公式。</span><span class="sxs-lookup"><span data-stu-id="cc7da-113">If this is the case, you can either set the `CustomRollupColumn` property on an attribute manually or use the Set Custom Member Formula enhancement of the Business Intelligence Wizard to enable a custom member formula on an attribute.</span></span> <span data-ttu-id="cc7da-114">有关如何使用此增强功能的详细信息，请参阅 [为维度中的属性设置自定义成员公式](bi-wizard-custom-member-formulas-for-attributes-in-a-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="cc7da-114">For more information about how to use this enhancement, see [Set Custom Member Formulas for Attributes in a Dimension](bi-wizard-custom-member-formulas-for-attributes-in-a-dimension.md).</span></span>  
  
## <a name="evaluating-custom-member-formulas"></a><span data-ttu-id="cc7da-115">对自定义成员公式求值</span><span class="sxs-lookup"><span data-stu-id="cc7da-115">Evaluating Custom Member Formulas</span></span>  
 <span data-ttu-id="cc7da-116">自定义成员公式不同于计算成员。</span><span class="sxs-lookup"><span data-stu-id="cc7da-116">Custom member formulas differ from calculated members.</span></span> <span data-ttu-id="cc7da-117">自定义成员公式应用于维度表中存在的成员，并且仅提供成员的值。</span><span class="sxs-lookup"><span data-stu-id="cc7da-117">Custom member formulas apply to members that exist in dimension tables, and only provide the value of the member.</span></span> <span data-ttu-id="cc7da-118">相反，计算成员并未存储在维度表中，并且计算成员表达式可定义维度或层次结构中包含的其他成员的数据和元数据。</span><span class="sxs-lookup"><span data-stu-id="cc7da-118">In contrast, calculated members are not stored in dimension tables, and calculated member expressions define both data and metadata for additional members included in a dimension or hierarchy.</span></span>  
  
 <span data-ttu-id="cc7da-119">自定义成员公式替代与度量值相关的聚合函数。</span><span class="sxs-lookup"><span data-stu-id="cc7da-119">Custom member formulas override the aggregate functions associated with measures.</span></span> <span data-ttu-id="cc7da-120">例如，在指定自定义成员公式之前，使用 `Sum` 聚合函数的度量值对“时间”维度的下列成员产生下列值：</span><span class="sxs-lookup"><span data-stu-id="cc7da-120">For example, before a custom member formula is specified, a measure using the `Sum` aggregate function has the following values for the following members of the Time dimension:</span></span>  
  
-   <span data-ttu-id="cc7da-121">2003: 2100</span><span class="sxs-lookup"><span data-stu-id="cc7da-121">2003: 2100</span></span>  
  
    -   <span data-ttu-id="cc7da-122">第一季度：700</span><span class="sxs-lookup"><span data-stu-id="cc7da-122">Quarter 1: 700</span></span>  
  
    -   <span data-ttu-id="cc7da-123">第二季度：500</span><span class="sxs-lookup"><span data-stu-id="cc7da-123">Quarter 2: 500</span></span>  
  
    -   <span data-ttu-id="cc7da-124">第三季度：100</span><span class="sxs-lookup"><span data-stu-id="cc7da-124">Quarter 3: 100</span></span>  
  
    -   <span data-ttu-id="cc7da-125">第四季度：800</span><span class="sxs-lookup"><span data-stu-id="cc7da-125">Quarter 4: 800</span></span>  
  
-   <span data-ttu-id="cc7da-126">2004: 1500</span><span class="sxs-lookup"><span data-stu-id="cc7da-126">2004: 1500</span></span>  
  
    -   <span data-ttu-id="cc7da-127">第一季度：600</span><span class="sxs-lookup"><span data-stu-id="cc7da-127">Quarter 1: 600</span></span>  
  
    -   <span data-ttu-id="cc7da-128">第二季度：200</span><span class="sxs-lookup"><span data-stu-id="cc7da-128">Quarter 2: 200</span></span>  
  
    -   <span data-ttu-id="cc7da-129">第三季度：300</span><span class="sxs-lookup"><span data-stu-id="cc7da-129">Quarter 3: 300</span></span>  
  
    -   <span data-ttu-id="cc7da-130">第四季度：400</span><span class="sxs-lookup"><span data-stu-id="cc7da-130">Quarter 4: 400</span></span>  
  
 <span data-ttu-id="cc7da-131">使用自定义成员公式时，成员的值可改由自定义汇总公式提供。</span><span class="sxs-lookup"><span data-stu-id="cc7da-131">With a custom member formula, the value of the member is instead supplied by the custom rollup formula.</span></span> <span data-ttu-id="cc7da-132">例如，以下自定义成员公式可用来为“时间”维度中 2004 成员的“第四季度”子成员提供值 450。</span><span class="sxs-lookup"><span data-stu-id="cc7da-132">For example, the following custom member formula can be used to supply the value for the Quarter 4 child member of the 2004 member in the Time dimension as 450.</span></span>  
  
```  
Time.[Quarter 3] * 1.5  
```  
  
 <span data-ttu-id="cc7da-133">自定义成员公式存储在维度表的一列中。</span><span class="sxs-lookup"><span data-stu-id="cc7da-133">Custom member formulas are stored in a column of the dimension table.</span></span> <span data-ttu-id="cc7da-134">可以通过设置特性的 `CustomRollupColumn` 属性来启用自定义汇总公式。</span><span class="sxs-lookup"><span data-stu-id="cc7da-134">You enable custom rollup formulas by setting the `CustomRollupColumn` property on an attribute.</span></span>  
  
 <span data-ttu-id="cc7da-135">若要将单个 MDX 表达式应用于属性的所有成员，请在维度表中创建可将 MDX 表达式作为文字字符串返回的命名计算。</span><span class="sxs-lookup"><span data-stu-id="cc7da-135">To apply a single MDX expression to all members of an attribute, create a named calculation on the dimension table that returns an MDX expression as a literal string.</span></span> <span data-ttu-id="cc7da-136">然后，使用要配置的特性的 `CustomRollupColumn` 属性设置指定命名计算。</span><span class="sxs-lookup"><span data-stu-id="cc7da-136">Then, specify the named calculation with the `CustomRollupColumn` property setting on the attribute that you want to configure.</span></span> <span data-ttu-id="cc7da-137">命名计算是数据源视图表中的一列，可返回由 SQL 表达式定义的行值。</span><span class="sxs-lookup"><span data-stu-id="cc7da-137">A named calculation is a column in a data source view table that returns row values defined by a SQL expression.</span></span> <span data-ttu-id="cc7da-138">有关构造命名计算的详细信息，请参阅[在数据源视图中定义命名计算 (Analysis Services)](define-named-calculations-in-a-data-source-view-analysis-services.md)</span><span class="sxs-lookup"><span data-stu-id="cc7da-138">For more information about constructing named calculations, see [Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](define-named-calculations-in-a-data-source-view-analysis-services.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cc7da-139">若要将 MDX 表达式应用于基于特定属性的特定级别的成员（而不是所有级别的成员），您可以将表达式定义为该级别中的 MDX 脚本。</span><span class="sxs-lookup"><span data-stu-id="cc7da-139">To apply an MDX expression to members of a particular level instead of to members of all levels based on a particular attribute, you can define the expression as an MDX script on the level.</span></span> <span data-ttu-id="cc7da-140">有关详细信息，请参阅 [MDX 脚本编写基础知识 (Analysis Services)](mdx/mdx-scripting-fundamentals-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="cc7da-140">For more information, see [MDX Scripting Fundamentals &#40;Analysis Services&#41;](mdx/mdx-scripting-fundamentals-analysis-services.md).</span></span>  
  
 <span data-ttu-id="cc7da-141">如果对属性成员同时使用计算成员和自定义汇总公式，则应当注意计算顺序。</span><span class="sxs-lookup"><span data-stu-id="cc7da-141">If you use both calculated members and custom rollup formulas for members of an attribute, you should be aware of the order of evaluation.</span></span> <span data-ttu-id="cc7da-142">系统会先解析计算成员，然后再解析自定义汇总公式。</span><span class="sxs-lookup"><span data-stu-id="cc7da-142">Calculated members are resolved before custom rollup formulas are resolved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc7da-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cc7da-143">See Also</span></span>  
 <span data-ttu-id="cc7da-144">[属性和属性层次结构](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="cc7da-144">[Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span></span>  
 [<span data-ttu-id="cc7da-145">为维度中的属性设置自定义成员公式</span><span class="sxs-lookup"><span data-stu-id="cc7da-145">Set Custom Member Formulas for Attributes in a Dimension</span></span>](bi-wizard-custom-member-formulas-for-attributes-in-a-dimension.md)  
  
  
