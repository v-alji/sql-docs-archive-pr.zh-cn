---
title: 父子维度中的一元运算符 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- UnaryOperatorColumn property
- attributes [Analysis Services], unary operators
- unary operators
ms.assetid: b8ef549c-5458-458a-bf1a-fd743a1417fd
author: minewiskan
ms.author: owend
ms.openlocfilehash: db07b99fd52ed4a126b7e69864652b9a164ae29b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689054"
---
# <a name="unary-operators-in-parent-child-dimensions"></a><span data-ttu-id="f857e-102">父子维度中的一元运算符</span><span class="sxs-lookup"><span data-stu-id="f857e-102">Unary Operators in Parent-Child Dimensions</span></span>
  <span data-ttu-id="f857e-103">在中包含父子关系的维度中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，可以指定一元 (或自定义汇总) 运算符列，该列确定父属性的所有非计算成员的自定义汇总。</span><span class="sxs-lookup"><span data-stu-id="f857e-103">In a dimension that contains a parent-child relationship in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you specify a unary (or custom rollup) operator column that determines the custom rollup for all noncalculated members of the parent attribute.</span></span> <span data-ttu-id="f857e-104">计算出父成员的值后，一元运算符就将应用于成员。</span><span class="sxs-lookup"><span data-stu-id="f857e-104">The unary operator is applied to members whenever the values of the parent members are evaluated.</span></span> <span data-ttu-id="f857e-105">父属性中的 **UnaryOperatorColumn** (**Usage**=Parent) 指定了数据源视图中包含一元运算符的表列。</span><span class="sxs-lookup"><span data-stu-id="f857e-105">The **UnaryOperatorColumn** on a parent attribute (**Usage**=Parent) specifies the column of a table in the data source view that contains unary operators.</span></span> <span data-ttu-id="f857e-106">存储在此列中的自定义汇总运算符的值将应用于属性的每个成员。</span><span class="sxs-lookup"><span data-stu-id="f857e-106">Values for the custom rollup operators that are stored in this column are applied to each member of the attribute.</span></span>  
  
 <span data-ttu-id="f857e-107">可以在数据源视图的维度表中创建和指定作为一元运算符列的命名计算。</span><span class="sxs-lookup"><span data-stu-id="f857e-107">You can create and specify a named calculation on a dimension table in the data source view as a unary operator column.</span></span> <span data-ttu-id="f857e-108">最简单的表达式（如“+”）对所有成员都将返回相同的运算符。</span><span class="sxs-lookup"><span data-stu-id="f857e-108">The simplest expression, such as '+', returns the same operator for all members.</span></span> <span data-ttu-id="f857e-109">但是，可以使用任何表达式，只要它为每个成员都返回运算符。</span><span class="sxs-lookup"><span data-stu-id="f857e-109">But you can use any expression as long as it returns an operator for every member.</span></span>  
  
 <span data-ttu-id="f857e-110">可以在父属性中手动更改 **UnaryOperatorColumn** 属性设置，也可以使用商业智能向导的“定义自定义聚合”增强功能替换与维度成员关联的默认聚合。</span><span class="sxs-lookup"><span data-stu-id="f857e-110">You can change the **UnaryOperatorColumn** property setting manually on a parent attribute or use the Define Custom Aggregation enhancement of the Business Intelligence Wizard to replace the default aggregation that is associated with members of a dimension.</span></span> <span data-ttu-id="f857e-111">有关如何使用商业智能向导执行此配置的详细信息，请参阅 [向维度中添加自定义聚合](bi-wizard-add-a-custom-aggregation-to-a-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="f857e-111">For more information about how to use the Business Intelligence Wizard to perform this configuration, see [Add a Custom Aggregation to a Dimension](bi-wizard-add-a-custom-aggregation-to-a-dimension.md).</span></span>  
  
 <span data-ttu-id="f857e-112">父属性的 **UnaryOperatorColumn** 属性的默认设置是“(none)”，它表示禁用自定义汇总运算符。</span><span class="sxs-lookup"><span data-stu-id="f857e-112">The default setting for the **UnaryOperatorColumn** property on a parent attribute is (none), which disables the custom rollup operators.</span></span> <span data-ttu-id="f857e-113">下表列出了一元运算符，并说明了将它们应用于某个级别时它们的行为。</span><span class="sxs-lookup"><span data-stu-id="f857e-113">The following table lists the unary operators and describes how they behave when they are applied to a level.</span></span>  
  
|<span data-ttu-id="f857e-114">一元运算符</span><span class="sxs-lookup"><span data-stu-id="f857e-114">Unary operator</span></span>|<span data-ttu-id="f857e-115">说明</span><span class="sxs-lookup"><span data-stu-id="f857e-115">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="f857e-116">+（加号）</span><span class="sxs-lookup"><span data-stu-id="f857e-116">+ (plus sign)</span></span>|<span data-ttu-id="f857e-117">成员的值将添加到在该成员之前发生的同级成员的聚合值中。</span><span class="sxs-lookup"><span data-stu-id="f857e-117">The value of the member is added to the aggregate value of the sibling members that occur before the member.</span></span> <span data-ttu-id="f857e-118">如果没有为属性定义一元运算符列，那么，这是默认运算符。</span><span class="sxs-lookup"><span data-stu-id="f857e-118">This operator is the default operator if no unary operator column is defined for an attribute.</span></span>|  
|<span data-ttu-id="f857e-119">- (减号) </span><span class="sxs-lookup"><span data-stu-id="f857e-119">- (minus sign)</span></span>|<span data-ttu-id="f857e-120">从成员之前发生的同级成员的聚合值中减去该成员的值。</span><span class="sxs-lookup"><span data-stu-id="f857e-120">The value of the member is subtracted from the aggregate value of the sibling members that occur before the member.</span></span>|  
|<span data-ttu-id="f857e-121">\*（星号）</span><span class="sxs-lookup"><span data-stu-id="f857e-121">\* (asterisk)</span></span>|<span data-ttu-id="f857e-122">成员的值乘以在该成员之前发生的同级成员的聚合值。</span><span class="sxs-lookup"><span data-stu-id="f857e-122">The value of the member is multiplied by the aggregate value of the sibling members that occur before the member.</span></span>|  
|<span data-ttu-id="f857e-123">/（斜杠）</span><span class="sxs-lookup"><span data-stu-id="f857e-123">/ (slash mark)</span></span>|<span data-ttu-id="f857e-124">成员的值除以在该成员之前发生的同级成员的聚合值。</span><span class="sxs-lookup"><span data-stu-id="f857e-124">The value of the member is divided by the aggregate value of the sibling members that occur before the member.</span></span>|  
|<span data-ttu-id="f857e-125">~（代字号）</span><span class="sxs-lookup"><span data-stu-id="f857e-125">~ (tilde)</span></span>|<span data-ttu-id="f857e-126">忽略成员的值。</span><span class="sxs-lookup"><span data-stu-id="f857e-126">The value of the member is ignored.</span></span>|  
  
 <span data-ttu-id="f857e-127">空值和在表中没找到的其他值将被视为使用加号 (+) 一元运算符。</span><span class="sxs-lookup"><span data-stu-id="f857e-127">Blank values and any other values not found in the table are treated the same as the plus sign (+) unary operator.</span></span> <span data-ttu-id="f857e-128">因为没有运算符优先级，所以成员在一元运算符列存储的顺序决定了求值的顺序。</span><span class="sxs-lookup"><span data-stu-id="f857e-128">There is no operator precedence, so the order of members as stored in the unary operator column determines the order of evaluation.</span></span> <span data-ttu-id="f857e-129">若要更改求值的顺序，请创建新的特性，并将其“类型” \*\*\*\* 属性设置为“顺序” \*\*\*\*，然后在其“源列” \*\*\*\* 属性中分配对应于求值顺序的顺序号。</span><span class="sxs-lookup"><span data-stu-id="f857e-129">To change the order of evaluation, create a new attribute, set its **Type** property to **Sequence**, and then assign sequence numbers that correspond to the order of evaluation in its **Source Column** property.</span></span> <span data-ttu-id="f857e-130">还必须按该属性对属性的成员排序。</span><span class="sxs-lookup"><span data-stu-id="f857e-130">You must also order members of the attribute by that attribute.</span></span> <span data-ttu-id="f857e-131">有关如何使用商业智能向导对属性成员排序的信息，请参阅 [定义维度的排序](bi-wizard-define-the-ordering-for-a-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="f857e-131">For information about how to use the Business Intelligence Wizard to order members of an attribute, see [Define the Ordering for a Dimension](bi-wizard-define-the-ordering-for-a-dimension.md).</span></span>  
  
 <span data-ttu-id="f857e-132">可以使用 **UnaryOperatorColumn** 属性指定一个命名计算，以返回一元运算符作为该属性的所有成员的文字字符。</span><span class="sxs-lookup"><span data-stu-id="f857e-132">You can use the **UnaryOperatorColumn** property to specify a named calculation that returns a unary operator as a literal character for all members of the attribute.</span></span> <span data-ttu-id="f857e-133">此操作就像在命名计算中键入文字字符（例如， `'*'` ）一样简单。</span><span class="sxs-lookup"><span data-stu-id="f857e-133">This could be as simple as typing a literal character such as `'*'` in the named calculation.</span></span> <span data-ttu-id="f857e-134">这会对属性的所有成员用乘法运算符（星号 (\*)）来替换默认的运算符（加号 (+)）。</span><span class="sxs-lookup"><span data-stu-id="f857e-134">This would replace the default operator, the plus sign (+), with the multiplication operator, the asterisk (\*), for all members of the attribute.</span></span> <span data-ttu-id="f857e-135">有关详细信息，请参阅[在数据源视图中定义命名计算 &#40;Analysis Services&#41;](define-named-calculations-in-a-data-source-view-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f857e-135">For more information, see [Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](define-named-calculations-in-a-data-source-view-analysis-services.md).</span></span>  
  
 <span data-ttu-id="f857e-136">在维度设计器的 **“浏览器”** 选项卡中，可以查看层次结构中每个成员旁边的一元运算符。</span><span class="sxs-lookup"><span data-stu-id="f857e-136">In the **Browser** tab of Dimension Designer, you can view the unary operators next to each member in a hierarchy.</span></span> <span data-ttu-id="f857e-137">还可以在处理启用写入的维度时更改一元运算符。</span><span class="sxs-lookup"><span data-stu-id="f857e-137">You can also change the unary operators when you work with a write-enabled dimension.</span></span> <span data-ttu-id="f857e-138">如果维度没有启用写入，则必须使用工具直接修改数据源。</span><span class="sxs-lookup"><span data-stu-id="f857e-138">If the dimension is not write-enabled, you must use a tool to modify the data source directly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f857e-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f857e-139">See Also</span></span>  
 <span data-ttu-id="f857e-140">[维度特性属性参考](dimension-attribute-properties-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f857e-140">[Dimension Attribute Properties Reference](dimension-attribute-properties-reference.md) </span></span>  
 <span data-ttu-id="f857e-141">[父子维度中的自定义汇总运算符](parent-child-dimension-attributes-custom-rollup-operators.md) </span><span class="sxs-lookup"><span data-stu-id="f857e-141">[Custom Rollup Operators in Parent-Child Dimensions](parent-child-dimension-attributes-custom-rollup-operators.md) </span></span>  
 [<span data-ttu-id="f857e-142">在维度设计器中启动商业智能向导</span><span class="sxs-lookup"><span data-stu-id="f857e-142">Start the Business Intelligence Wizard in Dimension Designer</span></span>](database-dimensions-bi-wizard-in-dimension-designer.md)  
  
  