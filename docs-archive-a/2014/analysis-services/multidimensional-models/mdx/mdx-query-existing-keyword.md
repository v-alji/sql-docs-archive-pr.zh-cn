---
title: 现有关键字 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- EXISTING
helpviewer_keywords:
- Existing keyword
ms.assetid: 651ee9ac-04ef-4316-87c9-a3df5ac27d22
author: minewiskan
ms.author: owend
ms.openlocfilehash: 115444c832fe8fe9b258a0c23b97b97553f32e8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577879"
---
# <a name="existing-keyword-mdx"></a><span data-ttu-id="eedbb-102">EXISTING 关键字 (MDX)</span><span class="sxs-lookup"><span data-stu-id="eedbb-102">EXISTING Keyword (MDX)</span></span>
  <span data-ttu-id="eedbb-103">强制在当前上下文中计算所指定的集。</span><span class="sxs-lookup"><span data-stu-id="eedbb-103">Forces a specified set to be evaluated within the current context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eedbb-104">语法</span><span class="sxs-lookup"><span data-stu-id="eedbb-104">Syntax</span></span>  
  
```  
  
Existing Set_Expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="eedbb-105">参数</span><span class="sxs-lookup"><span data-stu-id="eedbb-105">Arguments</span></span>  
 <span data-ttu-id="eedbb-106">*Set_Expression*</span><span class="sxs-lookup"><span data-stu-id="eedbb-106">*Set_Expression*</span></span>  
 <span data-ttu-id="eedbb-107">有效的多维表达式 (MDX) 集表达式。</span><span class="sxs-lookup"><span data-stu-id="eedbb-107">A valid Multidimensional Expressions (MDX) set expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eedbb-108">备注</span><span class="sxs-lookup"><span data-stu-id="eedbb-108">Remarks</span></span>  
 <span data-ttu-id="eedbb-109">默认情况下，在包含集成员的多维数据集的上下文中对集进行求值。</span><span class="sxs-lookup"><span data-stu-id="eedbb-109">By default, sets are evaluated within the context of the cube that contains the members of the set.</span></span> <span data-ttu-id="eedbb-110">但 `Existing` 关键字强制在当前上下文中对指定的集进行求值。</span><span class="sxs-lookup"><span data-stu-id="eedbb-110">The `Existing` keyword forces a specified set to be evaluated within the current context instead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eedbb-111">示例</span><span class="sxs-lookup"><span data-stu-id="eedbb-111">Example</span></span>  
 <span data-ttu-id="eedbb-112">下例将根据使用 `Aggregate` 函数求出并由用户选择的 State-Province 成员值，返回在上一时间段内销售额下降的分销商的计数。</span><span class="sxs-lookup"><span data-stu-id="eedbb-112">The following example returns the count of the resellers whose sales have declined over the previous time period, based on user-selected State-Province member values evaluated using the `Aggregate` function.</span></span> <span data-ttu-id="eedbb-113">但 [Hierarchize (MDX)](/sql/mdx/hierarchize-mdx) 和 [DrilldownLevel (MDX)](/sql/mdx/drilldownlevel-mdx) 函数用于返回 Product 维度中产品类别的销售额下降值。</span><span class="sxs-lookup"><span data-stu-id="eedbb-113">The [Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) and [DrilldownLevel (MDX)](/sql/mdx/drilldownlevel-mdx) functions are used to return values for declining sales for product categories in the Product dimension.</span></span> <span data-ttu-id="eedbb-114">`Existing`关键字强制在 `Filter` 当前上下文中计算函数集中的集，即州/省属性层次结构的华盛顿成员和俄勒冈成员。</span><span class="sxs-lookup"><span data-stu-id="eedbb-114">The `Existing` keyword forces the set in the `Filter` function to be evaluated in the current context - that is, for the Washington and Oregon members of the State-Province attribute hierarchy.</span></span>  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS  
   Count  
      (Filter  
         (Existing  
            (Reseller.Reseller.Reseller)  
         , [Measures].[Reseller Sales Amount] <   
            ([Measures].[Reseller Sales Amount]  
               ,[Date].Calendar.PrevMember  
            )  
        )  
      )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate   
      ( {[Geography].[State-Province].&[WA]&[US]  
         , [Geography].[State-Province].&[OR]&[US] }   
      )  
SELECT NON EMPTY HIERARCHIZE   
      (AddCalculatedMembers   
         (   
            {DrillDownLevel  
               ({[Product].[All Products]}  
               )  
            }   
         )   
      ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE   
      ( [Geography].[State-Province].x  
        , [Date].[Calendar].[Calendar Quarter].&[2003]&[4]  
        ,[Measures].[Declining Reseller Sales]  
      )  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="eedbb-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eedbb-115">See Also</span></span>  
 <span data-ttu-id="eedbb-116">[&#41; &#40;MDX&#41;&#40;集计数](/sql/mdx/count-set-mdx) </span><span class="sxs-lookup"><span data-stu-id="eedbb-116">[Count &#40;Set&#41; &#40;MDX&#41;](/sql/mdx/count-set-mdx) </span></span>  
 <span data-ttu-id="eedbb-117">[AddCalculatedMembers &#40;MDX&#41;](/sql/mdx/addcalculatedmembers-mdx) </span><span class="sxs-lookup"><span data-stu-id="eedbb-117">[AddCalculatedMembers &#40;MDX&#41;](/sql/mdx/addcalculatedmembers-mdx) </span></span>  
 <span data-ttu-id="eedbb-118">[聚合 &#40;MDX&#41;](/sql/mdx/aggregate-mdx) </span><span class="sxs-lookup"><span data-stu-id="eedbb-118">[Aggregate &#40;MDX&#41;](/sql/mdx/aggregate-mdx) </span></span>  
 <span data-ttu-id="eedbb-119">[筛选 &#40;MDX&#41;](/sql/mdx/filter-mdx) </span><span class="sxs-lookup"><span data-stu-id="eedbb-119">[Filter &#40;MDX&#41;](/sql/mdx/filter-mdx) </span></span>  
 <span data-ttu-id="eedbb-120">[MDX&#41;&#40;属性](/sql/mdx/properties-mdx) </span><span class="sxs-lookup"><span data-stu-id="eedbb-120">[Properties &#40;MDX&#41;](/sql/mdx/properties-mdx) </span></span>  
 <span data-ttu-id="eedbb-121">[DrilldownLevel &#40;MDX&#41;](/sql/mdx/drilldownlevel-mdx) </span><span class="sxs-lookup"><span data-stu-id="eedbb-121">[DrilldownLevel &#40;MDX&#41;](/sql/mdx/drilldownlevel-mdx) </span></span>  
 <span data-ttu-id="eedbb-122">[Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) </span><span class="sxs-lookup"><span data-stu-id="eedbb-122">[Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) </span></span>  
 [<span data-ttu-id="eedbb-123">MDX 函数引用 (MDX)</span><span class="sxs-lookup"><span data-stu-id="eedbb-123">MDX Function Reference &#40;MDX&#41;</span></span>](/sql/mdx/mdx-function-reference-mdx)  
  
  
