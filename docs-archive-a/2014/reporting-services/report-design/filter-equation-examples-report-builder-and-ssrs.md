---
title: 筛选器公式示例（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- filtering data [Reporting Services], filter equation examples
ms.assetid: 66bec93d-7c3b-4d4a-8cb6-7a7bb2f34ec6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9b4d7c7c561c9185c141190e26f37bc29fe52eb6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580585"
---
# <a name="filter-equation-examples-report-builder-and-ssrs"></a><span data-ttu-id="97829-102">筛选器公式示例（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="97829-102">Filter Equation Examples (Report Builder and SSRS)</span></span>
  <span data-ttu-id="97829-103">若要创建筛选器，必须指定一个或多个筛选器公式。</span><span class="sxs-lookup"><span data-stu-id="97829-103">To create a filter, you must specify one or more filter equations.</span></span> <span data-ttu-id="97829-104">筛选器公式包括表达式、数据类型、运算符和值。</span><span class="sxs-lookup"><span data-stu-id="97829-104">A filter equation includes an expression, a data type, an operator, and a value.</span></span> <span data-ttu-id="97829-105">本主题提供了常用筛选器的示例。</span><span class="sxs-lookup"><span data-stu-id="97829-105">This topic provides examples of commonly used filters.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="filter-examples"></a><span data-ttu-id="97829-106">筛选器示例</span><span class="sxs-lookup"><span data-stu-id="97829-106">Filter Examples</span></span>  
 <span data-ttu-id="97829-107">下表显示使用不同数据类型和不同运算符的筛选器公式的示例。</span><span class="sxs-lookup"><span data-stu-id="97829-107">The following table shows examples of filter equations that use different data types and different operators.</span></span> <span data-ttu-id="97829-108">比较的范围由将为其定义筛选器的报表项确定。</span><span class="sxs-lookup"><span data-stu-id="97829-108">The scope for the comparison is determined by report item for which a filter is defined.</span></span> <span data-ttu-id="97829-109">例如，对于为数据集定义的筛选器， **TOP % 10** 表示数据集中前 10% 的值；对于为组定义的筛选器， **TOP % 10** 表示组中前 10% 的值。</span><span class="sxs-lookup"><span data-stu-id="97829-109">For example, for a filter defined on a dataset, **TOP % 10** is the top 10 percent of values in the dataset; for a filter defined on a group, **TOP % 10** is the top 10 percent of values in the group.</span></span>  
  
|<span data-ttu-id="97829-110">简单表达式</span><span class="sxs-lookup"><span data-stu-id="97829-110">Simple Expression</span></span>|<span data-ttu-id="97829-111">数据类型</span><span class="sxs-lookup"><span data-stu-id="97829-111">Data Type</span></span>|<span data-ttu-id="97829-112">操作员</span><span class="sxs-lookup"><span data-stu-id="97829-112">Operator</span></span>|<span data-ttu-id="97829-113">值</span><span class="sxs-lookup"><span data-stu-id="97829-113">Value</span></span>|<span data-ttu-id="97829-114">说明</span><span class="sxs-lookup"><span data-stu-id="97829-114">Description</span></span>|  
|-----------------------|---------------|--------------|-----------|-----------------|  
|`[SUM(Quantity)]`|`Integer`|`>`|`7`|<span data-ttu-id="97829-115">包括大于 7 的数据值。</span><span class="sxs-lookup"><span data-stu-id="97829-115">Includes data values that are greater than 7.</span></span>|  
|`[SUM(Quantity)]`|`Integer`|`TOP N`|`10`|<span data-ttu-id="97829-116">包括前 10 个数据值。</span><span class="sxs-lookup"><span data-stu-id="97829-116">Includes the top 10 data values.</span></span>|  
|`[SUM(Quantity)]`|`Integer`|`TOP %`|`20`|<span data-ttu-id="97829-117">包括前 20% 的数据值。</span><span class="sxs-lookup"><span data-stu-id="97829-117">Includes the top 20% of data values.</span></span>|  
|`[Sales]`|`Text`|`>`|`=CDec(100)`|<span data-ttu-id="97829-118">包括大于 $100 的 System.Decimal（SQL“money”数据类型）类型的所有值。</span><span class="sxs-lookup"><span data-stu-id="97829-118">Includes all values of type System.Decimal (SQL "money" data types) greater than $100.</span></span>|  
|`[OrderDate]`|`DateTime`|`>`|`2008-01-01`|<span data-ttu-id="97829-119">包括从 2008 年 1 月 1 日到当前日期的所有日期。</span><span class="sxs-lookup"><span data-stu-id="97829-119">Includes all dates from January 1, 2008 to the present date.</span></span>|  
|`[OrderDate]`|`DateTime`|`BETWEEN`|`2008-01-01`<br /><br /> `2008-02-01`|<span data-ttu-id="97829-120">包括从 2008 年 1 月 1 日到 2008 年 2 月 1 日（含此日）的日期。</span><span class="sxs-lookup"><span data-stu-id="97829-120">Includes dates from January 1, 2008 up to and including February 1, 2008.</span></span>|  
|`[Territory]`|`Text`|`LIKE`|`*east`|<span data-ttu-id="97829-121">以“east”结尾的所有区域名称。</span><span class="sxs-lookup"><span data-stu-id="97829-121">All territory names that end in "east".</span></span>|  
|`[Territory]`|`Text`|`LIKE`|`%o%th*`|<span data-ttu-id="97829-122">名称开头包括“North”和“South”的所有区域名称。</span><span class="sxs-lookup"><span data-stu-id="97829-122">All territory names that include North and South at the beginning of the name.</span></span>|  
|`=LEFT(Fields!Subcat.Value,1)`|`Text`|`IN`|`B, C, T`|<span data-ttu-id="97829-123">以字母 B、 C 或 T 开头的所有子类别值。</span><span class="sxs-lookup"><span data-stu-id="97829-123">All subcategory values that begin with the letters B, C, or T.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="97829-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="97829-124">See Also</span></span>  
 <span data-ttu-id="97829-125">[报表参数 &#40;报表生成器和报表设计器&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="97829-125">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="97829-126">[添加数据集筛选器、数据区域筛选器和组筛选器 &#40;报表生成器和 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="97829-126">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="97829-127">[表达式中的数据类型 &#40;报表生成器和 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="97829-127">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="97829-128">[表达式在报表中使用 &#40;报表生成器和 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="97829-128">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="97829-129">表达式示例（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="97829-129">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  
  
  
