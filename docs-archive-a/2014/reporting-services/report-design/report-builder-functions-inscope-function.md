---
title: InScope 函数（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a8cd209a-e5d3-4dce-ab2d-f271f6c54955
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62c4ad5de7af1ac0762df29deaa17953a8a378db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586414"
---
# <a name="inscope-function-report-builder-and-ssrs"></a><span data-ttu-id="b4531-102">InScope 函数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="b4531-102">InScope Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="b4531-103">指示项的当前实例是否位于指定的作用域中。</span><span class="sxs-lookup"><span data-stu-id="b4531-103">Indicates whether the current instance of an item is in the specified scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="b4531-104">语法</span><span class="sxs-lookup"><span data-stu-id="b4531-104">Syntax</span></span>  
  
```  
InScope(scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4531-105">parameters</span><span class="sxs-lookup"><span data-stu-id="b4531-105">Parameters</span></span>  
 <span data-ttu-id="b4531-106">*作用域*</span><span class="sxs-lookup"><span data-stu-id="b4531-106">*scope*</span></span>  
 <span data-ttu-id="b4531-107">(`String`) 数据集、数据区域或指定某个作用域的组的名称。</span><span class="sxs-lookup"><span data-stu-id="b4531-107">(`String`) The name of a dataset, data region, or group that specifies a scope.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="b4531-108">返回类型</span><span class="sxs-lookup"><span data-stu-id="b4531-108">Return Type</span></span>  
 <span data-ttu-id="b4531-109">返回 `Boolean`。</span><span class="sxs-lookup"><span data-stu-id="b4531-109">Returns a `Boolean`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4531-110">备注</span><span class="sxs-lookup"><span data-stu-id="b4531-110">Remarks</span></span>  
 <span data-ttu-id="b4531-111">`InScope`函数测试报表项的当前实例的范围，以查找*scope*参数指定范围内的成员身份。</span><span class="sxs-lookup"><span data-stu-id="b4531-111">The `InScope` function tests the scope of the current instance of a report item for membership in the scope specified by the *scope*parameter.</span></span>  
  
 <span data-ttu-id="b4531-112">*Scope* 不能是表达式。</span><span class="sxs-lookup"><span data-stu-id="b4531-112">*Scope* cannot be an expression.</span></span>  
  
 <span data-ttu-id="b4531-113">`InScope` 函数通常用在具有动态作用域的数据区域中。</span><span class="sxs-lookup"><span data-stu-id="b4531-113">A typical use for the `InScope` function is in data regions that have dynamic scoping.</span></span> <span data-ttu-id="b4531-114">例如，`InScope` 可在数据区域单元格的钻取链接中使用，以便提供不同的报表名称和不同的参数集，具体取决于所单击的单元格。</span><span class="sxs-lookup"><span data-stu-id="b4531-114">For example, `InScope` can be used in a drillthrough link in a data region cells to provide a different report name and different sets of parameters depending on which cell is clicked.</span></span> <span data-ttu-id="b4531-115">应用示例如下：</span><span class="sxs-lookup"><span data-stu-id="b4531-115">An example of this is as follows:</span></span>  
  
-   <span data-ttu-id="b4531-116">如果单击的单元格位于 `ProductDetail` 组，则以下在钻取链接中用作报表名称的表达式将打开 `Month` 报表；否则将打开 `ProductSummary` 报表。</span><span class="sxs-lookup"><span data-stu-id="b4531-116">The following expression, used as the report name in a drillthrough link, opens the `ProductDetail` report if the clicked cell is in the `Month` group, and the `ProductSummary` report if it is not.</span></span>  
  
    ```  
    =Iif(InScope("Month"), "ProductDetail", "ProductSummary")  
    ```  
  
-   <span data-ttu-id="b4531-117">仅当单击的单元位于 `Product` 组时，以下在钻取报表参数的 `Omit` 属性中使用的表达式才会将参数传递到目标报表。</span><span class="sxs-lookup"><span data-stu-id="b4531-117">The following expression, used in the `Omit` property of a drillthrough report parameter, will pass the parameter to the target report only if the clicked cell is in the `Product` group.</span></span>  
  
    ```  
    =Not(InScope("Product"))  
    ```  
  
 <span data-ttu-id="b4531-118">有关详细信息，请参阅[聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)和[总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="b4531-118">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4531-119">示例</span><span class="sxs-lookup"><span data-stu-id="b4531-119">Example</span></span>  
 <span data-ttu-id="b4531-120">下面的代码示例指示项的当前实例是位于 `Product` 数据集、数据区域还是组作用域中。</span><span class="sxs-lookup"><span data-stu-id="b4531-120">The following code example indicates whether the current instance of the item is in the `Product` dataset, data region, or group scope.</span></span>  
  
```  
=InScope("Product")  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4531-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4531-121">See Also</span></span>  
 <span data-ttu-id="b4531-122">[在报表中使用表达式（报表生成器和 SSRS）](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b4531-122">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b4531-123">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b4531-123">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b4531-124">[表达式中的数据类型（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b4531-124">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="b4531-125">总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="b4531-125">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
