---
title: 组表达式示例（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data [Reporting Services], grouping
- grouping data
- expressions [Reporting Services], adding
- groups [Reporting Services], expressions
ms.assetid: 34cd0249-fc74-4cf2-ba11-7b072992bfd2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 128e3fa7aed189fd00072c2c3e961b80f8137c99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682698"
---
# <a name="group-expression-examples-report-builder-and-ssrs"></a><span data-ttu-id="80dd7-102">组表达式示例（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="80dd7-102">Group Expression Examples (Report Builder and SSRS)</span></span>
  <span data-ttu-id="80dd7-103">在数据区域中，可以按单个字段对数据进行分组，也可以创建标识要对其进行分组的数据的更复杂表达式。</span><span class="sxs-lookup"><span data-stu-id="80dd7-103">In a data region, you can group data by a single field, or create more complex expressions that identify the data on which to group.</span></span> <span data-ttu-id="80dd7-104">复杂表达式包含对多个字段或参数、条件语句或自定义代码的引用。</span><span class="sxs-lookup"><span data-stu-id="80dd7-104">Complex expressions include references to multiple fields or parameters, conditional statements, or custom code.</span></span> <span data-ttu-id="80dd7-105">定义数据区域组时，可以将这些表达式添加到 **“组”** 属性中。</span><span class="sxs-lookup"><span data-stu-id="80dd7-105">When you define a group for a data region, you add these expressions to the **Group** properties.</span></span> <span data-ttu-id="80dd7-106">有关详细信息，请参阅 [在数据区域中添加或删除组（报表生成器和 SSRS）](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="80dd7-106">For more information, see [Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="80dd7-107">若要合并两个或多个基于简单字段表达式的组，请将每个字段都添加到组定义中的组表达式列表中。</span><span class="sxs-lookup"><span data-stu-id="80dd7-107">To merge two or more groups that are based on simple field expressions, add each field to the group expressions list in the group definition.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="examples-of-group-expressions"></a><span data-ttu-id="80dd7-108">组表达式示例</span><span class="sxs-lookup"><span data-stu-id="80dd7-108">Examples of Group Expressions</span></span>  
 <span data-ttu-id="80dd7-109">下表提供了可用于定义组的组表达式示例。</span><span class="sxs-lookup"><span data-stu-id="80dd7-109">The following table provides examples of group expressions that you can use to define a group.</span></span>  
  
|<span data-ttu-id="80dd7-110">说明</span><span class="sxs-lookup"><span data-stu-id="80dd7-110">Description</span></span>|<span data-ttu-id="80dd7-111">表达式</span><span class="sxs-lookup"><span data-stu-id="80dd7-111">Expression</span></span>|  
|-----------------|----------------|  
|<span data-ttu-id="80dd7-112">按 `Region` 字段分组。</span><span class="sxs-lookup"><span data-stu-id="80dd7-112">Group by the `Region` field.</span></span>|`=Fields!Region.Value`|  
|<span data-ttu-id="80dd7-113">按姓氏和名字分组。</span><span class="sxs-lookup"><span data-stu-id="80dd7-113">Group by last name and first name.</span></span>|`=Fields!LastName.Value`<br /><br /> `=Fields!FirstName.Value`|  
|<span data-ttu-id="80dd7-114">按姓氏的第一个字母分组。</span><span class="sxs-lookup"><span data-stu-id="80dd7-114">Group by the first letter of the last name.</span></span>|`=Fields!LastName.Value.Substring(0,1)`|  
|<span data-ttu-id="80dd7-115">按参数分组（基于用户选择）。</span><span class="sxs-lookup"><span data-stu-id="80dd7-115">Group by parameter, based on user selection.</span></span><br /><br /> <span data-ttu-id="80dd7-116">在此示例中，参数 `GroupBy` 必须基于可提供有效分组依据选项的可用值列表。</span><span class="sxs-lookup"><span data-stu-id="80dd7-116">In this example, the parameter `GroupBy` must be based on an available values list that provides a valid choice to group on.</span></span>|`=Fields(Parameters!GroupBy.Value).Value`|  
|<span data-ttu-id="80dd7-117">按三个不同年龄范围分组：</span><span class="sxs-lookup"><span data-stu-id="80dd7-117">Group by three separate age ranges:</span></span><br /><br /> <span data-ttu-id="80dd7-118">“小于 21”、“21 到 50”和“大于 50”。</span><span class="sxs-lookup"><span data-stu-id="80dd7-118">"Under 21", "Between 21 and 50", and "Over 50".</span></span>|`=IIF(First(Fields!Age.Value)<21,"Under 21",(IIF(First(Fields!Age.Value)>=21 AND First(Fields!Age.Value)<=50,"Between 21 and 50","Over 50")))`|  
|<span data-ttu-id="80dd7-119">按多个年龄范围分组。</span><span class="sxs-lookup"><span data-stu-id="80dd7-119">Group by many age ranges.</span></span> <span data-ttu-id="80dd7-120">本示例演示了一段以 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET 编写的自定义代码，此段代码可返回下列年龄范围的字符串：</span><span class="sxs-lookup"><span data-stu-id="80dd7-120">This example shows custom code, written in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET, that returns a string for the following ranges:</span></span><br /><br /> <span data-ttu-id="80dd7-121">小于等于 25</span><span class="sxs-lookup"><span data-stu-id="80dd7-121">25 or Under</span></span><br /><br /> <span data-ttu-id="80dd7-122">26 到 50</span><span class="sxs-lookup"><span data-stu-id="80dd7-122">26 to 50</span></span><br /><br /> <span data-ttu-id="80dd7-123">51 到 75</span><span class="sxs-lookup"><span data-stu-id="80dd7-123">51 to 75</span></span><br /><br /> <span data-ttu-id="80dd7-124">大于 75</span><span class="sxs-lookup"><span data-stu-id="80dd7-124">Over 75</span></span>|`=Code.GetRangeValueByAge(Fields!Age.Value)`<br /><br /> <span data-ttu-id="80dd7-125">自定义代码：</span><span class="sxs-lookup"><span data-stu-id="80dd7-125">Custom code:</span></span><br /><br /> `Function GetRangeValueByAge(ByVal age As Integer) As String`<br /><br /> `Select Case age`<br /><br /> `Case 0 To 25`<br /><br /> `GetRangeValueByByAge = "25 or Under"`<br /><br /> `Case 26 To 50`<br /><br /> `GetRangeValueByByAge = "26 to 50"`<br /><br /> `Case 51 to 75`<br /><br /> `GetRangeValueByByAge = "51 to 75"`<br /><br /> `Case Else`<br /><br /> `GetRangeValueByByAge = "Over 75"`<br /><br /> `End Select`<br /><br /> `Return GetRangeValueByByAge`<br /><br /> `End Function`|  
  
## <a name="see-also"></a><span data-ttu-id="80dd7-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="80dd7-126">See Also</span></span>  
 <span data-ttu-id="80dd7-127">[对数据进行筛选、分组和排序（报表生成器和 SSRS）](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="80dd7-127">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="80dd7-128">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="80dd7-128">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="80dd7-129">报表设计器的表达式中的自定义代码和程序集引用 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="80dd7-129">Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;</span></span>](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)  
  
  
