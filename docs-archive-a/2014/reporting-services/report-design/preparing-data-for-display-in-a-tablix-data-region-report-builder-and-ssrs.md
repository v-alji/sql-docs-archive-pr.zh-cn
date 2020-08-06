---
title: 准备要在 Tablix 数据区域中显示的数据（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fbb00dc6-7887-480c-b771-cab6fecb8dcc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 72ac150f2dcd227b1e3afb624a5ca5866fb4c360
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590052"
---
# <a name="preparing-data-for-display-in-a-tablix-data-region-report-builder-and-ssrs"></a><span data-ttu-id="1b22d-102">准备要在 Tablix 数据区域中显示的数据（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="1b22d-102">Preparing Data for Display in a Tablix Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1b22d-103">Tablix 数据区域显示来自数据集的数据。</span><span class="sxs-lookup"><span data-stu-id="1b22d-103">A tablix data region displays data from a dataset.</span></span> <span data-ttu-id="1b22d-104">您可以查看从数据集中检索的所有数据，也可以创建筛选器以便仅查看数据子集。</span><span class="sxs-lookup"><span data-stu-id="1b22d-104">You can view all the data retrieved for the dataset or you can create filters so that you see only a subset of the data.</span></span> <span data-ttu-id="1b22d-105">还可以添加条件表达式，以便填充 Null 值或修改对数据集的查询，使其包括定义现有列的排序顺序的列。</span><span class="sxs-lookup"><span data-stu-id="1b22d-105">You can also add conditional expressions to fill in null values or modify the query for a dataset to include columns that define the sort order for an existing column.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="working-with-nulls-and-blanks-in-field-values"></a><span data-ttu-id="1b22d-106">处理字段值中的 Null 值和空白</span><span class="sxs-lookup"><span data-stu-id="1b22d-106">Working with Nulls and Blanks in Field Values</span></span>  
 <span data-ttu-id="1b22d-107">数据集中的字段集合的数据包含在运行时从数据源中检索到的所有值，包括 Null 值和空白。</span><span class="sxs-lookup"><span data-stu-id="1b22d-107">Data for the field collection in a dataset includes all values retrieved from the data source at run time, including null values and blanks.</span></span> <span data-ttu-id="1b22d-108">通常 Null 值和空白是无法区分的。</span><span class="sxs-lookup"><span data-stu-id="1b22d-108">Normally null values and blanks are indistinguishable.</span></span> <span data-ttu-id="1b22d-109">在大多数情况下，这是所需行为。</span><span class="sxs-lookup"><span data-stu-id="1b22d-109">In most cases, this is the desired behavior.</span></span> <span data-ttu-id="1b22d-110">例如， [Sum](report-builder-functions-sum-function.md) 和 [Avg](report-builder-functions-avg-function.md) 等数值聚合函数忽略 Null 值。</span><span class="sxs-lookup"><span data-stu-id="1b22d-110">For example, Numeric aggregate functions like [Sum](report-builder-functions-sum-function.md) and [Avg](report-builder-functions-avg-function.md) ignore null values.</span></span> <span data-ttu-id="1b22d-111">有关详细信息，请参阅 [聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="1b22d-111">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  
  
 <span data-ttu-id="1b22d-112">如果希望以不同方式处理 Null 值，则可以使用条件表达式或自定义代码替换 Null 值的自定义值。</span><span class="sxs-lookup"><span data-stu-id="1b22d-112">If you do want to handle null values differently, you can use conditional expressions or custom code to substitute a custom value for the null value.</span></span> <span data-ttu-id="1b22d-113">例如，只要 `Null` 字段显示 Null 值，以下表达式则替换 `[Size]`文本。</span><span class="sxs-lookup"><span data-stu-id="1b22d-113">For example, the following expression substitutes the text `Null` wherever a null value occurs in the field `[Size]`.</span></span>  
  
```  
=IIF(Fields!Size.Value IS NOTHING,"Null",Fields!Size.Value)  
```  
  
 <span data-ttu-id="1b22d-114">有关在使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 查询从 [!INCLUDE[tsql](../../includes/tsql-md.md)] 数据源检索数据之前在数据中消除 Null 值的详细信息，请参阅位于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Server 联机丛书 [上的](https://go.microsoft.com/fwlink/?linkid=120955)文档中的“Null 值”和“Null 值和联接”。</span><span class="sxs-lookup"><span data-stu-id="1b22d-114">For more information about eliminating nulls in your data before retrieving the data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source using [!INCLUDE[tsql](../../includes/tsql-md.md)] queries, see "Null Values" and "Null Values and Joins" in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentation in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=120955).</span></span>  
  
## <a name="handling-null-field-names"></a><span data-ttu-id="1b22d-115">处理 Null 字段名称</span><span class="sxs-lookup"><span data-stu-id="1b22d-115">Handling Null Field Names</span></span>  
 <span data-ttu-id="1b22d-116">只要查询结果集中存在 Null 字段自身，就可以在表达式中测试 Null 值。</span><span class="sxs-lookup"><span data-stu-id="1b22d-116">Testing for null values in an expression is fine as long as the field itself exists in the query result set.</span></span> <span data-ttu-id="1b22d-117">使用自定义代码，可以测试在运行时从数据源返回的集合字段中是否存在字段自身。</span><span class="sxs-lookup"><span data-stu-id="1b22d-117">From custom code, you can test whether the field itself is present in the collection fields returned from the data source at run time.</span></span> <span data-ttu-id="1b22d-118">有关详细信息，请参阅[数据集字段集合引用（报表生成器和 SSRS）](built-in-collections-dataset-fields-collection-references-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="1b22d-118">For more information, see [Dataset Fields Collection References &#40;Report Builder and SSRS&#41;](built-in-collections-dataset-fields-collection-references-report-builder.md).</span></span>  
  
## <a name="adding-a-sort-order-column"></a><span data-ttu-id="1b22d-119">添加排序顺序列</span><span class="sxs-lookup"><span data-stu-id="1b22d-119">Adding a Sort Order Column</span></span>  
 <span data-ttu-id="1b22d-120">默认情况下，可以按字母顺序对数据集字段中的值排序。</span><span class="sxs-lookup"><span data-stu-id="1b22d-120">By default, you can alphabetically sort values in a dataset field.</span></span> <span data-ttu-id="1b22d-121">若要按不同顺序排序，则可以在数据集中添加定义数据区域中的排序顺序的新列。</span><span class="sxs-lookup"><span data-stu-id="1b22d-121">To sort in a different order, you can add a new column to your dataset that defines the sort order you want in a data region.</span></span> <span data-ttu-id="1b22d-122">例如，若要对 `[Color]` 字段排序，并首先对白色和黑色项排序，则可以添加 `[ColorSortOrder]`列，如以下查询所示：</span><span class="sxs-lookup"><span data-stu-id="1b22d-122">For example, to sort on the field `[Color]` and sort white and black items first, you can add a column `[ColorSortOrder]`, shown in the following query:</span></span>  
  
```  
SELECT ProductID, p.Name, Color,  
   CASE  
      WHEN p.Color = 'White' THEN 1  
      WHEN p.Color = 'Black' THEN 2  
      WHEN p.Color = 'Blue' THEN 3  
      WHEN p.Color = 'Yellow' THEN 4  
      ELSE 5  
   END As ColorSortOrder  
FROM Production.Product p  
```  
  
 <span data-ttu-id="1b22d-123">若要按照此排序顺序对表数据区域进行排序，请将详细信息组上的排序表达式设置为 `=Fields!ColorSortOrder.Value`。</span><span class="sxs-lookup"><span data-stu-id="1b22d-123">To sort a table data region according to this sort order, set the sort expression on the detail group to `=Fields!ColorSortOrder.Value`.</span></span> <span data-ttu-id="1b22d-124">有关详细信息，请参阅[对数据区域中的数据进行排序（报表生成器和 SSRS）](sort-data-in-a-data-region-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1b22d-124">For more information, see [Sort Data in a Data Region &#40;Report Builder and SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b22d-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b22d-125">See Also</span></span>  
 <span data-ttu-id="1b22d-126">[数据集字段集合（报表生成器和 SSRS）](../report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1b22d-126">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1b22d-127">[表达式（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1b22d-127">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1b22d-128">对数据进行筛选、分组和排序（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="1b22d-128">Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;</span></span>](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
