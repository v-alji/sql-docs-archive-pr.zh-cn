---
title: 父子维度中的自定义汇总运算符 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- child rollup operations
- UnaryOperatorColumn property
- custom rollup operators [Analysis Services]
- unary operators
- parent-child dimensions [Analysis Services]
ms.assetid: a3ddd9fc-5fa3-4227-9322-8c45a5b5c2c3
author: minewiskan
ms.author: owend
ms.openlocfilehash: db12ccc6703ee4863dd3b6bd598d2317b54fce6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588106"
---
# <a name="custom-rollup-operators-in-parent-child-dimensions"></a><span data-ttu-id="ef710-102">父子维度中的自定义汇总运算符</span><span class="sxs-lookup"><span data-stu-id="ef710-102">Custom Rollup Operators in Parent-Child Dimensions</span></span>
  <span data-ttu-id="ef710-103">自定义汇总运算符提供了一种简单的方法，控制成员值如何汇总到父子层次结构的父值中。</span><span class="sxs-lookup"><span data-stu-id="ef710-103">Custom rollup operators provide a simple way to control how member values are rolled up into parent values in a parent-child hierarchy.</span></span> <span data-ttu-id="ef710-104">在包含父子关系的维度中，可以指定包含一元运算符的列，以便用该运算符指定父属性的所有非计算成员的汇总。</span><span class="sxs-lookup"><span data-stu-id="ef710-104">In a dimension containing a parent-child relationship, you specify a column that contains unary operators that specify rollup for all noncalculated members of the parent attribute.</span></span> <span data-ttu-id="ef710-105">计算出父成员的值后，一元运算符就将应用于成员。</span><span class="sxs-lookup"><span data-stu-id="ef710-105">The unary operator is applied to members whenever the values of the parent members are evaluated.</span></span>  
  
 <span data-ttu-id="ef710-106">一元运算符存储在由父属性的 `UnaryOperatorColumn` 属性所定义的列中，并且它们应用于属性的每个成员。</span><span class="sxs-lookup"><span data-stu-id="ef710-106">The unary operators are stored in column defined by the `UnaryOperatorColumn` property of the parent attribute, and they are applied to each member of the attribute.</span></span> <span data-ttu-id="ef710-107">此属性所指定的列可以按维度表的外键驻留于维度表或与维度表相关的表中。</span><span class="sxs-lookup"><span data-stu-id="ef710-107">The column specified by this property can reside either in the dimension table or in a table related to the dimension table by a foreign key in the dimension table.</span></span>  
  
 <span data-ttu-id="ef710-108">自定义汇总运算符提供了与自定义成员公式相似但比它更简化的功能。</span><span class="sxs-lookup"><span data-stu-id="ef710-108">Custom rollup operators provide functionality similar to, but more simplified than, custom member formulas.</span></span> <span data-ttu-id="ef710-109">自定义成员公式使用“多维表达式 (MDX)” 表达式确定汇总成员的方式。</span><span class="sxs-lookup"><span data-stu-id="ef710-109">A custom member formula uses Multidimensional Expressions (MDX) expressions to determine how the members are rolled up.</span></span> <span data-ttu-id="ef710-110">相反，自定义汇总运算符使用简单的一元运算符确定成员的值如何影响父级。</span><span class="sxs-lookup"><span data-stu-id="ef710-110">In contrast, a custom rollup operator uses a simple unary operator to determine how the value of a member affects the parent.</span></span> <span data-ttu-id="ef710-111">在维度中，前面级别的自定义成员公式将覆盖某个级别的自定义汇总运算符。</span><span class="sxs-lookup"><span data-stu-id="ef710-111">Custom member formulas of the preceding level in a dimension override a level's custom rollup operator.</span></span>  
  
## <a name="custom-rollup-precedence"></a><span data-ttu-id="ef710-112">自定义汇总优先级</span><span class="sxs-lookup"><span data-stu-id="ef710-112">Custom Rollup Precedence</span></span>  
 <span data-ttu-id="ef710-113">在优先级方面，层次结构中某个级别的源属性的自定义汇总运算符将覆盖上一级的自定义成员公式。</span><span class="sxs-lookup"><span data-stu-id="ef710-113">In terms of precedence, the custom rollup operators of the source attribute for a level in a hierarchy override the custom member formulas of the previous level.</span></span> <span data-ttu-id="ef710-114">而上一级的自定义成员公式将覆盖下一级的自定义汇总运算符。</span><span class="sxs-lookup"><span data-stu-id="ef710-114">However, the custom member formulas of the preceding level override the custom rollup operators of a level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef710-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef710-115">See Also</span></span>  
 <span data-ttu-id="ef710-116">[定义自定义成员公式](attribute-properties-define-custom-member-formulas.md) </span><span class="sxs-lookup"><span data-stu-id="ef710-116">[Define Custom Member Formulas](attribute-properties-define-custom-member-formulas.md) </span></span>  
 [<span data-ttu-id="ef710-117">父子维度中的一元运算符</span><span class="sxs-lookup"><span data-stu-id="ef710-117">Unary Operators in Parent-Child Dimensions</span></span>](parent-child-dimension-attributes-unary-operators.md)  
  
  
