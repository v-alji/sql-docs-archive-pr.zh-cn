---
title: "\"度量值组绑定\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.dimensionusage.definerelationship.measuregroupbindings.f1
helpviewer_keywords:
- Measure Group Bindings dialog box
ms.assetid: ed642780-5350-438e-af73-b9ceab3f876d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 78693901a5898b140d6efeed16b6f0eaa7577e69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693570"
---
# <a name="measure-group-bindings-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="c28db-102">“度量值组绑定”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="c28db-102">Measure Group Bindings Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="c28db-103">对于常规维度关系，可以使用“度量值组绑定”对话框创建和修改多维数据集维度中的非粒度属性与度量值组中的列之间的直接关系，并使用“定义关系”对话框为多维数据集维度中的所有属性指定空值处理选项。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="c28db-103">Use the **Measure Group Bindings** dialog box to create and modify direct relationships between non-granularity attributes in a cube dimension and columns in a measure group for a regular dimension relationship, as well as to specify null processing options for any attribute in a cube dimension, from the **Define Relationship** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c28db-104">选项</span><span class="sxs-lookup"><span data-stu-id="c28db-104">Options</span></span>  
 <span data-ttu-id="c28db-105">**度量值组表**</span><span class="sxs-lookup"><span data-stu-id="c28db-105">**Measure group table**</span></span>  
 <span data-ttu-id="c28db-106">显示所选度量值组的事实数据表的名称。</span><span class="sxs-lookup"><span data-stu-id="c28db-106">Displays the name of the fact table for the selected measure group.</span></span>  
  
 <span data-ttu-id="c28db-107">**属性**</span><span class="sxs-lookup"><span data-stu-id="c28db-107">**Attributes**</span></span>  
 <span data-ttu-id="c28db-108">显示属性和维度表的网格。</span><span class="sxs-lookup"><span data-stu-id="c28db-108">Displays a grid of attributes and dimension tables.</span></span> <span data-ttu-id="c28db-109">选择一个属性可以在 **“关系”** 中为所选属性创建或修改其属性。</span><span class="sxs-lookup"><span data-stu-id="c28db-109">Select an attribute to create or modify properties in **Relationship** for the selected attribute.</span></span> <span data-ttu-id="c28db-110">该网格包含以下列：</span><span class="sxs-lookup"><span data-stu-id="c28db-110">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="c28db-111">选项</span><span class="sxs-lookup"><span data-stu-id="c28db-111">Option</span></span>|<span data-ttu-id="c28db-112">定义</span><span class="sxs-lookup"><span data-stu-id="c28db-112">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="c28db-113">**属性名称**</span><span class="sxs-lookup"><span data-stu-id="c28db-113">**Attribute Name**</span></span>|<span data-ttu-id="c28db-114">显示属性的名称。</span><span class="sxs-lookup"><span data-stu-id="c28db-114">Displays the name of the attribute.</span></span>|  
|<span data-ttu-id="c28db-115">**维度表**</span><span class="sxs-lookup"><span data-stu-id="c28db-115">**Dimension Table**</span></span>|<span data-ttu-id="c28db-116">显示属性所基于的维度表的名称。</span><span class="sxs-lookup"><span data-stu-id="c28db-116">Displays the name of the dimension table on which the attribute is based.</span></span>|  
  
 <span data-ttu-id="c28db-117">**关系**</span><span class="sxs-lookup"><span data-stu-id="c28db-117">**Relationship**</span></span>  
 <span data-ttu-id="c28db-118">显示所选属性的维度表列与所选度量值组的事实数据表列之间的关系网格，并显示关系的空值处理选项。</span><span class="sxs-lookup"><span data-stu-id="c28db-118">Displays a grid of relationships between dimension table columns for the selected attribute and fact table columns for the selected measure group as well as the null processing option for the relationship.</span></span> <span data-ttu-id="c28db-119">该网格包含以下列：</span><span class="sxs-lookup"><span data-stu-id="c28db-119">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="c28db-120">选项</span><span class="sxs-lookup"><span data-stu-id="c28db-120">Option</span></span>|<span data-ttu-id="c28db-121">定义</span><span class="sxs-lookup"><span data-stu-id="c28db-121">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="c28db-122">**维度列**</span><span class="sxs-lookup"><span data-stu-id="c28db-122">**Dimension Columns**</span></span>|<span data-ttu-id="c28db-123">显示在 **“属性”** 中选择的属性所基于的维度表中的列。</span><span class="sxs-lookup"><span data-stu-id="c28db-123">Displays the columns from the dimension table on which the attribute selected in **Attributes** is based.</span></span>|  
|<span data-ttu-id="c28db-124">**度量值组列**</span><span class="sxs-lookup"><span data-stu-id="c28db-124">**Measure Group Columns**</span></span>|<span data-ttu-id="c28db-125">选择 **“从维度继承”** 可以使用从维度继承的度量值组关系，或者从度量值组所基于的事实数据表选择列，以显式定义关系。</span><span class="sxs-lookup"><span data-stu-id="c28db-125">Select either **Inherited from dimension** to use the measure group relationship inherited from the dimension, or select a column from the fact table on which the measure group is based to explicitly define a relationship.</span></span>|  
|<span data-ttu-id="c28db-126">**空值处理**</span><span class="sxs-lookup"><span data-stu-id="c28db-126">**Null Processing**</span></span>|<span data-ttu-id="c28db-127">为属性选择空值处理选项。</span><span class="sxs-lookup"><span data-stu-id="c28db-127">Select a null processing option for the attribute.</span></span> <span data-ttu-id="c28db-128">有关空值处理选项的详细信息，请参阅 [NullProcessing 元素 (ASSL)](https://docs.microsoft.com/bi-reference/assl/properties/nullprocessing-element-assl)。</span><span class="sxs-lookup"><span data-stu-id="c28db-128">For more information about null processing options, see [NullProcessing Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/nullprocessing-element-assl).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c28db-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c28db-129">See Also</span></span>  
 <span data-ttu-id="c28db-130">["定义关系" 对话框 &#40;Analysis Services 多维数据&#41;](define-relationship-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c28db-130">[Define Relationship Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](define-relationship-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="c28db-131">&#40;多维数据的 Analysis Services 设计器和对话框&#41;</span><span class="sxs-lookup"><span data-stu-id="c28db-131">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
