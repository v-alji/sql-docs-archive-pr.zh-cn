---
title: 在 MDX 中生成度量值 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f0347835-4983-4d26-acbb-6c8fae7992bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: ac49d37f11584bfbc5d372241056da39e7dd8c93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580934"
---
# <a name="building-measures-in-mdx"></a><span data-ttu-id="fa195-102">在 MDX 中生成度量值</span><span class="sxs-lookup"><span data-stu-id="fa195-102">Building Measures in MDX</span></span>
  <span data-ttu-id="fa195-103">在多维表达式 (MDX) 中，度量值是名为 DAX 的表达式，通过计算该表达式来解析它以返回表格模型中的值。</span><span class="sxs-lookup"><span data-stu-id="fa195-103">In Multidimensional Expressions (MDX), a measure is a named DAX expression that is resolved by calculating the expression to return a value in a Tabular Model.</span></span> <span data-ttu-id="fa195-104">这种泛泛的定义所包括的范围十分惊人。</span><span class="sxs-lookup"><span data-stu-id="fa195-104">This innocuous definition covers an incredible amount of ground.</span></span> <span data-ttu-id="fa195-105">由于能在 MDX 查询中构造和使用度量值，使得人们能够更有力地驾驭表格数据。</span><span class="sxs-lookup"><span data-stu-id="fa195-105">The ability to construct and use measures in an MDX query provides a great deal of manipulation capability for tabular data.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="fa195-106">只能在表格模型中定义度量值；如果在多维模式下设置数据库，创建度量值将导致错误。</span><span class="sxs-lookup"><span data-stu-id="fa195-106">Measures can only be defined in tabular models; if your database is set in multidimensional mode, creating a measure will generate an error</span></span>  
  
 <span data-ttu-id="fa195-107">若要创建一个度量值，该度量值被定义为 MDX 查询的一部分并且其作用域因此被限制在该查询内，请使用 WITH 关键字。</span><span class="sxs-lookup"><span data-stu-id="fa195-107">To create a measure that is defined as part of an MDX query, and therefore whose scope is limited to the query, you use the WITH keyword.</span></span> <span data-ttu-id="fa195-108">然后，就可以在 MDX SELECT 语句中使用该度量值。</span><span class="sxs-lookup"><span data-stu-id="fa195-108">You can then use the measure within an MDX SELECT statement.</span></span> <span data-ttu-id="fa195-109">通过这种方法，更改用 WITH 关键字创建的计算成员时就不会打乱 SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="fa195-109">Using this approach, the calculated member created by using the WITH keyword can be changed without disturbing the SELECT statement.</span></span> <span data-ttu-id="fa195-110">但是，在 MDX 中您引用度量值的方式不用于在 DAX 表达式中引用它的方式；为了引用度量值，您将它命名为 [度量值] 维度的成员，请参阅以下 MDX 示例：</span><span class="sxs-lookup"><span data-stu-id="fa195-110">However, in MDX you reference the measure in a different way than when in DAX expressions; to reference the measure you name it as a member of the [Measures] dimension, see the following MDX example:</span></span>  
  
```  
with measure  'Sales Territory'[Total Sales Amount] = SUM('Internet Sales'[Sales Amount]) + SUM('Reseller Sales'[Sales Amount])  
select measures.[Total Sales Amount] on columns  
     ,NON EMPTY [Date].[Calendar Year].children on rows  
from [Model]  
  
```  
  
 <span data-ttu-id="fa195-111">执行时将返回以下数据：</span><span class="sxs-lookup"><span data-stu-id="fa195-111">It will return the following data when executed:</span></span>  
  
||<span data-ttu-id="fa195-112">总销售额</span><span class="sxs-lookup"><span data-stu-id="fa195-112">Total Sales Amount</span></span>||  
|-|------------------------|-|  
|<span data-ttu-id="fa195-113">2001</span><span class="sxs-lookup"><span data-stu-id="fa195-113">2001</span></span>|<span data-ttu-id="fa195-114">11331808.96</span><span class="sxs-lookup"><span data-stu-id="fa195-114">11331808.96</span></span>||  
|<span data-ttu-id="fa195-115">2002</span><span class="sxs-lookup"><span data-stu-id="fa195-115">2002</span></span>|<span data-ttu-id="fa195-116">30674773.18</span><span class="sxs-lookup"><span data-stu-id="fa195-116">30674773.18</span></span>||  
|<span data-ttu-id="fa195-117">2003</span><span class="sxs-lookup"><span data-stu-id="fa195-117">2003</span></span>|<span data-ttu-id="fa195-118">41993729.72</span><span class="sxs-lookup"><span data-stu-id="fa195-118">41993729.72</span></span>||  
|<span data-ttu-id="fa195-119">2004</span><span class="sxs-lookup"><span data-stu-id="fa195-119">2004</span></span>|<span data-ttu-id="fa195-120">25808962.34</span><span class="sxs-lookup"><span data-stu-id="fa195-120">25808962.34</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="fa195-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa195-121">See Also</span></span>  
 <span data-ttu-id="fa195-122">[CREATE MEMBER 语句 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span><span class="sxs-lookup"><span data-stu-id="fa195-122">[CREATE MEMBER Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span></span>  
 <span data-ttu-id="fa195-123">[Mdx 函数引用 &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="fa195-123">[MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span></span>  
 [<span data-ttu-id="fa195-124">SELECT 语句 (MDX)</span><span class="sxs-lookup"><span data-stu-id="fa195-124">SELECT Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-manipulation-select)  
  
  
