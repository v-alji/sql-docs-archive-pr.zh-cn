---
title: " (MDX) 使用 RollupChildren 函数 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [MDX], RollupChildren function
- RollupChildren function
- custom member properties [MDX]
- IIf function
ms.assetid: 03c624d4-f277-451d-9995-623a07ea2f86
author: minewiskan
ms.author: owend
ms.openlocfilehash: 341468d521cebe1fda33d73ea999f3b6571cb01e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691958"
---
# <a name="working-with-the-rollupchildren-function-mdx"></a><span data-ttu-id="07471-102">使用 RollupChildren 函数 (MDX)</span><span class="sxs-lookup"><span data-stu-id="07471-102">Working with the RollupChildren Function (MDX)</span></span>
  <span data-ttu-id="07471-103">多维表达式 (MDX) [RollupChildren](/sql/mdx/rollupchildren-mdx) [用于搜索和替换的脚本] 函数汇总成员的子级，对每个子级应用不同的一元运算符，并以数字的形式返回此汇总值。</span><span class="sxs-lookup"><span data-stu-id="07471-103">The Multidimensional Expressions (MDX) [RollupChildren](/sql/mdx/rollupchildren-mdx) [Script for Search and Replace] function rolls up the children of a member, applying a different unary operator to each child, and returns the value of this rollup as a number.</span></span> <span data-ttu-id="07471-104">一元运算符可通过与子成员关联的成员属性提供，也可以是直接提供给函数的字符串表达式。</span><span class="sxs-lookup"><span data-stu-id="07471-104">The unary operator can be supplied by a member property associated with the child member, or the operator can be a string expression provided directly to the function.</span></span>  
  
## <a name="rollupchildren-function-examples"></a><span data-ttu-id="07471-105">RollupChildren 函数示例</span><span class="sxs-lookup"><span data-stu-id="07471-105">RollupChildren Function Examples</span></span>  
 <span data-ttu-id="07471-106">`RollupChildren` 函数在多维表达式 (MDX) 语句中的用法很容易理解，但它对 MDX 查询的影响十分广泛。</span><span class="sxs-lookup"><span data-stu-id="07471-106">The use of the `RollupChildren` function in Multidimensional Expressions (MDX) statements is simple to explain, but the effect of this function on MDX queries can be wide-ranging.</span></span>  
  
 <span data-ttu-id="07471-107">`RollupChildren` 函数的影响体现在为对现有多维数据集数据执行选择性分析而设计的 MDX 查询中。</span><span class="sxs-lookup"><span data-stu-id="07471-107">The effect of the `RollupChildren` function occurs in MDX queries designed to perform selective analysis on existing cube data.</span></span> <span data-ttu-id="07471-108">例如，下表包含“净销售额”父成员的子成员列表，子成员的一元运算符（由 `UNARY_OPERATOR` 成员属性表示）显示在括号内。</span><span class="sxs-lookup"><span data-stu-id="07471-108">For example, the following table contains a list of child members for the Net Sales parent member, with their unary operators (represented by the `UNARY_OPERATOR` member property) shown in parentheses.</span></span>  
  
|<span data-ttu-id="07471-109">父成员</span><span class="sxs-lookup"><span data-stu-id="07471-109">Parent member</span></span>|<span data-ttu-id="07471-110">子成员 (Child member)</span><span class="sxs-lookup"><span data-stu-id="07471-110">Child member</span></span>|  
|-------------------|------------------|  
|<span data-ttu-id="07471-111">净销售额</span><span class="sxs-lookup"><span data-stu-id="07471-111">Net Sales</span></span>|<span data-ttu-id="07471-112">国内销售额 (+)</span><span class="sxs-lookup"><span data-stu-id="07471-112">Domestic Sales (+)</span></span><br /><br /> <span data-ttu-id="07471-113">国内盈利 (-)</span><span class="sxs-lookup"><span data-stu-id="07471-113">Domestic Returns (-)</span></span><br /><br /> <span data-ttu-id="07471-114">国外销售额 (+)</span><span class="sxs-lookup"><span data-stu-id="07471-114">Foreign Sales (+)</span></span><br /><br /> <span data-ttu-id="07471-115">国外盈利 (-)</span><span class="sxs-lookup"><span data-stu-id="07471-115">Foreign Returns (-)</span></span>|  
  
 <span data-ttu-id="07471-116">“净销售额”父成员当前等于总净销售额减去国内和国外总销售额，并在汇总过程中减去国内和国外盈利。</span><span class="sxs-lookup"><span data-stu-id="07471-116">The Net Sales parent member currently provides a total of net sales minus the gross domestic and foreign sales values, with the domestic and foreign returns subtracted as part of the rollup.</span></span>  
  
 <span data-ttu-id="07471-117">但是，您希望提供国内和国外总销售额加 10% 的快速预测（忽略国内盈利和国外盈利）。</span><span class="sxs-lookup"><span data-stu-id="07471-117">However, you want to provide a quick and easy forecast of domestic and foreign gross sales plus 10%, ignoring the domestic and foreign returns.</span></span> <span data-ttu-id="07471-118">若要计算此值，可以按下列两种方式之一使用 `RollupChildren` 函数：使用自定义成员属性或使用 `IIf` 函数。</span><span class="sxs-lookup"><span data-stu-id="07471-118">To calculate this value, you can use the `RollupChildren` function in one of two ways: with a custom member property or with the `IIf` function.</span></span>  
  
### <a name="using-a-custom-member-property"></a><span data-ttu-id="07471-119">使用自定义成员属性</span><span class="sxs-lookup"><span data-stu-id="07471-119">Using a Custom Member Property</span></span>  
 <span data-ttu-id="07471-120">如果经常要进行汇总计算，一种方法是创建一个成员属性，以存储特定函数的每个子级要使用的运算符。</span><span class="sxs-lookup"><span data-stu-id="07471-120">If the rollup calculation is to be a frequently performed operation, one method is to create a member property that stores the operator that will be used for each child for a specific function.</span></span> <span data-ttu-id="07471-121">下表显示了有效的一元运算符并说明了预期的结果。</span><span class="sxs-lookup"><span data-stu-id="07471-121">The following table displays valid unary operators and describes the expected result.</span></span>  
  
|<span data-ttu-id="07471-122">运算符</span><span class="sxs-lookup"><span data-stu-id="07471-122">Operator</span></span>|<span data-ttu-id="07471-123">结果</span><span class="sxs-lookup"><span data-stu-id="07471-123">Result</span></span>|  
|--------------|------------|  
|+|<span data-ttu-id="07471-124">total = total + current child</span><span class="sxs-lookup"><span data-stu-id="07471-124">total = total + current child</span></span>|  
|-|<span data-ttu-id="07471-125">总额 = 总额 - 当前子级</span><span class="sxs-lookup"><span data-stu-id="07471-125">total = total - current child</span></span>|  
|*|<span data-ttu-id="07471-126">total = total \* current child</span><span class="sxs-lookup"><span data-stu-id="07471-126">total = total \* current child</span></span>|  
|/|<span data-ttu-id="07471-127">total = total / current child</span><span class="sxs-lookup"><span data-stu-id="07471-127">total = total / current child</span></span>|  
|~|<span data-ttu-id="07471-128">不在汇总中使用子级。</span><span class="sxs-lookup"><span data-stu-id="07471-128">Child is not used in the rollup.</span></span> <span data-ttu-id="07471-129">子级的值将被忽略。</span><span class="sxs-lookup"><span data-stu-id="07471-129">The child's value is ignored.</span></span>|  
  
 <span data-ttu-id="07471-130">例如，可以创建名为 `SALES_OPERATOR` 的成员属性并为其分配下列一元运算符，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="07471-130">For example, a member property called `SALES_OPERATOR` could be created, and the following unary operators would be assigned to that member property, as shown in the following table.</span></span>  
  
|<span data-ttu-id="07471-131">父成员</span><span class="sxs-lookup"><span data-stu-id="07471-131">Parent member</span></span>|<span data-ttu-id="07471-132">子成员 (Child member)</span><span class="sxs-lookup"><span data-stu-id="07471-132">Child member</span></span>|  
|-------------------|------------------|  
|<span data-ttu-id="07471-133">净销售额</span><span class="sxs-lookup"><span data-stu-id="07471-133">Net Sales</span></span>|<span data-ttu-id="07471-134">国内销售额 (+)</span><span class="sxs-lookup"><span data-stu-id="07471-134">Domestic Sales (+)</span></span><br /><br /> <span data-ttu-id="07471-135">国内盈利 (~)</span><span class="sxs-lookup"><span data-stu-id="07471-135">Domestic Returns (~)</span></span><br /><br /> <span data-ttu-id="07471-136">国外销售额 (+)</span><span class="sxs-lookup"><span data-stu-id="07471-136">Foreign Sales (+)</span></span><br /><br /> <span data-ttu-id="07471-137">国外盈利 (~)</span><span class="sxs-lookup"><span data-stu-id="07471-137">Foreign Returns (~)</span></span>|  
  
 <span data-ttu-id="07471-138">通过这个新的成员属性，可使用下列 MDX 语句快速有效地估算出总销售额（忽略国内盈利和国外盈利）：</span><span class="sxs-lookup"><span data-stu-id="07471-138">With this new member property, the following MDX statement would perform the gross sales estimate operation quickly and efficiently (ignoring Foreign and Domestic returns):</span></span>  
  
```  
RollupChildren([Net Sales], [Net Sales].CurrentMember.Properties("SALES_OPERATOR")) * 1.1  
```  
  
 <span data-ttu-id="07471-139">当调用函数时，使用该成员属性中存储的运算符将每个子级的值应用于总数。</span><span class="sxs-lookup"><span data-stu-id="07471-139">When the function is called, the value of each child is applied to a total using the operator stored in the member property.</span></span> <span data-ttu-id="07471-140">将忽略国内盈利和国外盈利的成员，并将 `RollupChildren` 函数返回的汇总总数乘以 1.1。</span><span class="sxs-lookup"><span data-stu-id="07471-140">The members for domestic and foreign returns are ignored, and the rollup total returned by the `RollupChildren` function is multiplied by 1.1.</span></span>  
  
### <a name="using-the-iif-function"></a><span data-ttu-id="07471-141">使用 IIf 函数</span><span class="sxs-lookup"><span data-stu-id="07471-141">Using the IIf Function</span></span>  
 <span data-ttu-id="07471-142">如果示例操作不太常见，或者操作仅适用于一个 MDX 查询，则可以将[IIf](/sql/mdx/iif-mdx)函数与函数结合使用， `RollupChildren` 以提供相同的结果。</span><span class="sxs-lookup"><span data-stu-id="07471-142">If the example operation is not commonplace or if the operation applies only to one MDX query, the [IIf](/sql/mdx/iif-mdx) function can be used with the `RollupChildren` function to provide the same result.</span></span> <span data-ttu-id="07471-143">下列 MDX 查询提供的结果与前面的 MDX 示例相同，但这里没有使用自定义成员属性：</span><span class="sxs-lookup"><span data-stu-id="07471-143">The following MDX query provides the same result as the earlier MDX example, but does so without resorting to the use of a custom member property:</span></span>  
  
```  
RollupChildren([Net Sales], IIf([Net Sales].CurrentMember.Properties("UNARY_OPERATOR") = "-", "~", [Net Sales].CurrentMember.Properties("UNARY_OPERATOR))) * 1.1  
```  
  
 <span data-ttu-id="07471-144">MDX 语句检查子成员的一元运算符。</span><span class="sxs-lookup"><span data-stu-id="07471-144">The MDX statement examines the unary operator of the child member.</span></span> <span data-ttu-id="07471-145">如果一元运算符用于减法（正如在考虑国内盈利和国外盈利成员的情况下），`IIf` 函数将替代一元运算符 ~。</span><span class="sxs-lookup"><span data-stu-id="07471-145">If the unary operator is used for subtraction (as in the case with the domestic and foreign returns members), the `IIf` function substitutes the tilde (~) unary operator.</span></span> <span data-ttu-id="07471-146">否则，`IIf` 函数将使用子成员的一元运算符。</span><span class="sxs-lookup"><span data-stu-id="07471-146">Otherwise, the `IIf` function uses the unary operator of the child member.</span></span> <span data-ttu-id="07471-147">最后，将所返回的汇总总数乘以 1.1，得出国内和国外总销售额的预测值。</span><span class="sxs-lookup"><span data-stu-id="07471-147">Finally, the returned rollup total is then multiplied by 1.1 to provide the domestic and foreign gross sales forecast value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07471-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07471-148">See Also</span></span>  
 [<span data-ttu-id="07471-149">操作数据 (MDX)</span><span class="sxs-lookup"><span data-stu-id="07471-149">Manipulating Data &#40;MDX&#41;</span></span>](mdx-data-manipulation-manipulating-data.md)  
  
  
