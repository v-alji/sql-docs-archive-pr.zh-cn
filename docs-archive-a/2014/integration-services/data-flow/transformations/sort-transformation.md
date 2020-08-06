---
title: 排序转换 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sorttrans.f1
helpviewer_keywords:
- Sort transformation
- descending sorts
- ascending sorts
- sorting data [Integration Services]
- multiple sorts
- duplicate data [Integration Services]
ms.assetid: 728c9351-84a8-4a89-be4d-d50d4adc04e0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7039d02b6cc55355c3b27e5694474df4666570ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587931"
---
# <a name="sort-transformation"></a><span data-ttu-id="0f73a-102">排序转换</span><span class="sxs-lookup"><span data-stu-id="0f73a-102">Sort Transformation</span></span>
  <span data-ttu-id="0f73a-103">排序转换按升序或降序对输入数据进行排序，并将排序后的数据复制到转换输出。</span><span class="sxs-lookup"><span data-stu-id="0f73a-103">The Sort transformation sorts input data in ascending or descending order and copies the sorted data to the transformation output.</span></span> <span data-ttu-id="0f73a-104">您可以对一个输入应用多个排序；每个排序都由确定排序顺序的一个数字来标识。</span><span class="sxs-lookup"><span data-stu-id="0f73a-104">You can apply multiple sorts to an input; each sort is identified by a numeral that determines the sort order.</span></span> <span data-ttu-id="0f73a-105">首先对具有最小数字的列进行排序，然后对具有第二小数字的排序列进行排序，依此类推。</span><span class="sxs-lookup"><span data-stu-id="0f73a-105">The column with the lowest number is sorted first, the sort column with the second lowest number is sorted next, and so on.</span></span> <span data-ttu-id="0f73a-106">例如，如果名为 **CountryRegion** 的列的排序顺序为 1，而名为 **City** 的列的排序顺序为 2，则输出先按照 country/region（国家/地区）排序，然后按照 city（城市）排序。</span><span class="sxs-lookup"><span data-stu-id="0f73a-106">For example, if a column named **CountryRegion** has a sort order of 1 and a column named **City** has a sort order of 2, the output is sorted by country/region and then by city.</span></span> <span data-ttu-id="0f73a-107">正数表示排序为升序排序，负数表示排序为降序排序。</span><span class="sxs-lookup"><span data-stu-id="0f73a-107">A positive number denotes that the sort is ascending, and a negative number denotes that the sort is descending.</span></span> <span data-ttu-id="0f73a-108">不进行排序的列的排序顺序为 0。</span><span class="sxs-lookup"><span data-stu-id="0f73a-108">Columns that are not sorted have a sort order of 0.</span></span> <span data-ttu-id="0f73a-109">没有选择进行排序的列将与被排序列一起自动被复制到转换输出。</span><span class="sxs-lookup"><span data-stu-id="0f73a-109">Columns that are not selected for sorting are automatically copied to the transformation output together with the sorted columns.</span></span>  
  
 <span data-ttu-id="0f73a-110">排序转换包含一组比较选项，这些选项可以定义转换处理列中字符串数据的方式。</span><span class="sxs-lookup"><span data-stu-id="0f73a-110">The Sort transformation includes a set of comparison options to define how the transformation handles the string data in a column.</span></span> <span data-ttu-id="0f73a-111">有关详细信息，请参阅 [Comparing String Data](../comparing-string-data.md)。</span><span class="sxs-lookup"><span data-stu-id="0f73a-111">For more information, see [Comparing String Data](../comparing-string-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f73a-112">排序转换对 GUID 进行排序的顺序不同于 ORDER BY 子句在 Transact-SQL 中对其排序的顺序。</span><span class="sxs-lookup"><span data-stu-id="0f73a-112">The Sort transformation does not sort GUIDs in the same order as the ORDER BY clause does in Transact-SQL.</span></span> <span data-ttu-id="0f73a-113">排序转换先对以 0-9 开头的 GUID 进行排序，然后再对以 A-F 开头的 GUID 进行排序，而 ORDER BY 子句对 GUID 进行排序的顺序则不同于此，这在 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]中得到了体现。</span><span class="sxs-lookup"><span data-stu-id="0f73a-113">While the Sort transformation sorts GUIDs that start with 0-9 before GUIDs that start with A-F, the ORDER BY clause, as implemented in the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)], sorts them differently.</span></span> <span data-ttu-id="0f73a-114">有关详细信息，请参阅 [ORDER BY 子句 (Transact-SQL)](/sql/t-sql/queries/select-order-by-clause-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0f73a-114">For more information, see [ORDER BY Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql).</span></span>  
  
 <span data-ttu-id="0f73a-115">作为排序操作的一部分，排序转换还可删除重复行。</span><span class="sxs-lookup"><span data-stu-id="0f73a-115">The Sort transformation can also remove duplicate rows as part of its sort.</span></span> <span data-ttu-id="0f73a-116">重复行是具有相同排序键值的行。</span><span class="sxs-lookup"><span data-stu-id="0f73a-116">Duplicate rows are rows with the same sort key values.</span></span> <span data-ttu-id="0f73a-117">排序键值是根据所用的字符串比较选项生成的，这意味着不同文字字符串可能具有相同的排序键值。</span><span class="sxs-lookup"><span data-stu-id="0f73a-117">The sort key value is generated based on the string comparison options being used, which means that different literal strings may have the same sort key values.</span></span> <span data-ttu-id="0f73a-118">转换将输入列中具有不同值但具有相同排序键的行标识为重复行。</span><span class="sxs-lookup"><span data-stu-id="0f73a-118">The transformation identifies rows in the input columns that have different values but the same sort key as duplicates.</span></span>  
  
 <span data-ttu-id="0f73a-119">排序转换包括了可以在加载包时通过属性表达式进行更新的 `MaximumThreads` 自定义属性。</span><span class="sxs-lookup"><span data-stu-id="0f73a-119">The Sort transformation includes the `MaximumThreads` custom property that can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="0f73a-120">有关详细信息，请参阅 [Integration Services (SSIS) 表达式](../../expressions/integration-services-ssis-expressions.md)、[在包中使用属性表达式](../../expressions/use-property-expressions-in-packages.md)和[转换自定义属性](transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="0f73a-120">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="0f73a-121">此转换有一个输入和一个输出。</span><span class="sxs-lookup"><span data-stu-id="0f73a-121">This transformation has one input and one output.</span></span> <span data-ttu-id="0f73a-122">它不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="0f73a-122">It does not support error outputs.</span></span>  
  
## <a name="configuration-of-the-sort-transformation"></a><span data-ttu-id="0f73a-123">排序转换的配置</span><span class="sxs-lookup"><span data-stu-id="0f73a-123">Configuration of the Sort Transformation</span></span>  
 <span data-ttu-id="0f73a-124">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="0f73a-124">You can set properties through the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="0f73a-125">有关可在 **“排序转换编辑器”** 对话框中设置的属性的信息，请参阅 [Sort Transformation Editor](../../sort-transformation-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="0f73a-125">For information about the properties that you can set in the **Sort Transformation Editor** dialog box, see [Sort Transformation Editor](../../sort-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="0f73a-126">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="0f73a-126">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="0f73a-127">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="0f73a-127">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="0f73a-128">Common Properties</span><span class="sxs-lookup"><span data-stu-id="0f73a-128">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="0f73a-129">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="0f73a-129">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="0f73a-130">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="0f73a-130">Related Tasks</span></span>  
 <span data-ttu-id="0f73a-131">有关如何设置组件属性的详细信息，请参阅 [设置数据流组件属性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="0f73a-131">For more information about how to set properties of the component, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="0f73a-132">相关内容</span><span class="sxs-lookup"><span data-stu-id="0f73a-132">Related Content</span></span>  
 <span data-ttu-id="0f73a-133">codeplex.com 上的示例 [SortDeDuplicateDelimitedString 自定义 SSIS 组件](https://go.microsoft.com/fwlink/?LinkId=220821)。</span><span class="sxs-lookup"><span data-stu-id="0f73a-133">Sample, [SortDeDuplicateDelimitedString Custom SSIS Component](https://go.microsoft.com/fwlink/?LinkId=220821), on codeplex.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f73a-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0f73a-134">See Also</span></span>  
 <span data-ttu-id="0f73a-135">[数据流](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="0f73a-135">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="0f73a-136">Integration Services 转换</span><span class="sxs-lookup"><span data-stu-id="0f73a-136">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
