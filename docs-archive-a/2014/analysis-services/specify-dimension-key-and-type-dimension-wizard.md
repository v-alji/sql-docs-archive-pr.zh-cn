---
title: 指定维度键和类型 (维度向导) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionkeyandtype.f1
ms.assetid: d7d5db55-36c3-45f6-ade3-29aa516589c1
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc08584ed12de8597b8289fd223cc47945d7d087
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589262"
---
# <a name="specify-dimension-key-and-type-dimension-wizard"></a><span data-ttu-id="e2873-102">指定维度键和类型（维度向导）</span><span class="sxs-lookup"><span data-stu-id="e2873-102">Specify Dimension Key and Type (Dimension Wizard)</span></span>
  <span data-ttu-id="e2873-103">可以使用“指定维度键和类型”\*\*\*\* 页定义维度的键属性，并指示维度是否为渐变维度 (SCD)。</span><span class="sxs-lookup"><span data-stu-id="e2873-103">Use the **Specify Dimension Key and Type** page to define the key attribute of the dimension and to indicate whether the dimension is a slowly changing dimension (SCD).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e2873-104"> 只有在 **“选择生成方法”** 页上选择 **“不使用数据源生成维度”** ，并在 **“选择维度类型”** 页上选择 **“标准维度”** 时，才会显示此页。</span><span class="sxs-lookup"><span data-stu-id="e2873-104">This page is displayed only if you selected **Build the dimension without using a data source** on the **Select Build Method** page and if you selected **Standard dimension** on the **Select the Dimension Type** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e2873-105">选项</span><span class="sxs-lookup"><span data-stu-id="e2873-105">Options</span></span>  
 <span data-ttu-id="e2873-106">**键属性**</span><span class="sxs-lookup"><span data-stu-id="e2873-106">**Key attribute**</span></span>  
 <span data-ttu-id="e2873-107">选择要作为维度键属性的属性。</span><span class="sxs-lookup"><span data-stu-id="e2873-107">Select the attribute that will be the key attribute for the dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e2873-108">如果尚未为维度定义任何属性，则对于此选项唯一可用的值为 **“自动创建键属性”**</span><span class="sxs-lookup"><span data-stu-id="e2873-108">If no attributes have been defined for the dimension, the only value available for this option is **Create key attribute automatically.**</span></span> <span data-ttu-id="e2873-109">。如果为维度定义了任何属性，则此值不可用。</span><span class="sxs-lookup"><span data-stu-id="e2873-109">This value is not available if any attributes are defined for the dimension.</span></span>  
  
 <span data-ttu-id="e2873-110">**这是变化的维度**</span><span class="sxs-lookup"><span data-stu-id="e2873-110">**This is a changing dimension**</span></span>  
 <span data-ttu-id="e2873-111">选择此选项可以指示维度为渐变维度。</span><span class="sxs-lookup"><span data-stu-id="e2873-111">Select to indicate that the dimension is a slowly changing dimension.</span></span> <span data-ttu-id="e2873-112">选择此选项将创建其他列和属性，这些列和属性可以用来跟踪在一段时间后成员在维度的层次结构中的移动情况。</span><span class="sxs-lookup"><span data-stu-id="e2873-112">Selecting this option will create additional columns and attributes that can be used to track the movement of members within the hierarchies of the dimension over time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2873-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2873-113">See Also</span></span>  
 <span data-ttu-id="e2873-114">[维度向导的 F1 帮助](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="e2873-114">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="e2873-115">[Analysis Services 多维数据 &#40;维度&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="e2873-115">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="e2873-116">多维模型中的维度</span><span class="sxs-lookup"><span data-stu-id="e2873-116">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
