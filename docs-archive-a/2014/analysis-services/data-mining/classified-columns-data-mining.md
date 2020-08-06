---
title: 已分类的列 (数据挖掘) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content types [data mining]
- STDEV column
- VARIANCE column
- PROBABLILITY column
- PROBABILITY_STDEV column
- columns [data mining], classified
- classified columns [data mining]
- PROBABILITY_VARIANCE column
- SUPPORT column
ms.assetid: 68bf3b78-dc12-497c-898f-b43a45646123
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c264dfb6a97b8b8f576966e8929f6b0dc51e4ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589377"
---
# <a name="classified-columns-data-mining"></a><span data-ttu-id="1d2f0-102">已分类列（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="1d2f0-102">Classified Columns (Data Mining)</span></span>
  <span data-ttu-id="1d2f0-103">定义已分类列时，在挖掘结构中创建当前列和另一个列之间的关系。</span><span class="sxs-lookup"><span data-stu-id="1d2f0-103">When you define a classified column, you create a relationship between the current column and another column in the mining structure.</span></span> <span data-ttu-id="1d2f0-104">指定为已分类列的挖掘结构列中的数据包含描述挖掘结构中另一个列的值的分类信息。</span><span class="sxs-lookup"><span data-stu-id="1d2f0-104">The data in the mining structure column that you designate as the classified column contains categorical information that describes the values in another column in the mining structure.</span></span>  
  
 <span data-ttu-id="1d2f0-105">例如，假定有两个包含数值数据的列：其中 [Yearly Purchases] 列包含特定日历年每个客户每年的总购买量，[Standard Deviations] 列则包含这些值的标准偏差。</span><span class="sxs-lookup"><span data-stu-id="1d2f0-105">For example, suppose you have two columns with numerical data: one column, [Yearly Purchases], contains the total yearly purchases per customer for a specific calendar year, and the other column, [Standard Deviations], contains the standard deviations for those values.</span></span> <span data-ttu-id="1d2f0-106">在此例中，可以指定 [Yearly Purchases] 列为已分类列，模型将在分析中使用此关系。</span><span class="sxs-lookup"><span data-stu-id="1d2f0-106">In this case you could designate the [Yearly Purchases] column as the classified column, and the model would be able to use this relationship in analysis.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1d2f0-107">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中提供的算法不支持使用已分类列，此功能用于创建自定义算法中。</span><span class="sxs-lookup"><span data-stu-id="1d2f0-107">The algorithms provided in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] do not support the use of classified columns; this feature is provided for use in creating custom algorithms.</span></span>  
  
## <a name="defining-a-classified-column"></a><span data-ttu-id="1d2f0-108">定义已分类列</span><span class="sxs-lookup"><span data-stu-id="1d2f0-108">Defining a Classified Column</span></span>  
 <span data-ttu-id="1d2f0-109">已分类列的数据类型必须为 `Long` 或 `Double`。</span><span class="sxs-lookup"><span data-stu-id="1d2f0-109">The data type of a classified column must be either `Long` or `Double`.</span></span>  
  
 <span data-ttu-id="1d2f0-110">以下列表说明 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 支持的已分类列内容类型。</span><span class="sxs-lookup"><span data-stu-id="1d2f0-110">The following list describes the content types that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supports for classified columns.</span></span>  
  
 <span data-ttu-id="1d2f0-111">**发生**</span><span class="sxs-lookup"><span data-stu-id="1d2f0-111">**PROBABILITY**</span></span>  
 <span data-ttu-id="1d2f0-112">列内的值是相关值的概率，是介于 0 和 1 之间的数字。</span><span class="sxs-lookup"><span data-stu-id="1d2f0-112">The value in the column is the probability of the associated value, and is a number between 0 and 1.</span></span>  
  
 <span data-ttu-id="1d2f0-113">**变动**</span><span class="sxs-lookup"><span data-stu-id="1d2f0-113">**VARIANCE**</span></span>  
 <span data-ttu-id="1d2f0-114">列内的值是相关值的方差。</span><span class="sxs-lookup"><span data-stu-id="1d2f0-114">The value in the column is the variance of the associated value.</span></span>  
  
 <span data-ttu-id="1d2f0-115">**STDEV**</span><span class="sxs-lookup"><span data-stu-id="1d2f0-115">**STDEV**</span></span>  
 <span data-ttu-id="1d2f0-116">列内的值是相关值的标准偏差。</span><span class="sxs-lookup"><span data-stu-id="1d2f0-116">The value in the column is the standard deviation of the associated value.</span></span>  
  
 <span data-ttu-id="1d2f0-117">**PROBABILITY_VARIANCE**</span><span class="sxs-lookup"><span data-stu-id="1d2f0-117">**PROBABILITY_VARIANCE**</span></span>  
 <span data-ttu-id="1d2f0-118">列内的值是相关值概率的方差。</span><span class="sxs-lookup"><span data-stu-id="1d2f0-118">The value in the column is the variance of the probability for the associated value.</span></span>  
  
 <span data-ttu-id="1d2f0-119">**PROBABILITY_STDEV**</span><span class="sxs-lookup"><span data-stu-id="1d2f0-119">**PROBABILITY_STDEV**</span></span>  
 <span data-ttu-id="1d2f0-120">列内的值是相关值概率的标准偏差。</span><span class="sxs-lookup"><span data-stu-id="1d2f0-120">The value in the column is the standard deviation of the probability for the associated value.</span></span>  
  
 <span data-ttu-id="1d2f0-121">**支持**</span><span class="sxs-lookup"><span data-stu-id="1d2f0-121">**SUPPORT**</span></span>  
 <span data-ttu-id="1d2f0-122">列内的值是相关值的权重或事例复制因子。</span><span class="sxs-lookup"><span data-stu-id="1d2f0-122">The value in the column is the weight, or case replication factor, of the associated value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d2f0-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d2f0-123">See Also</span></span>  
 <span data-ttu-id="1d2f0-124">[内容类型 &#40;数据挖掘&#41;](content-types-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="1d2f0-124">[Content Types &#40;Data Mining&#41;](content-types-data-mining.md) </span></span>  
 <span data-ttu-id="1d2f0-125">[挖掘结构 &#40;Analysis Services 数据挖掘&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="1d2f0-125">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="1d2f0-126">数据类型（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="1d2f0-126">Data Types &#40;Data Mining&#41;</span></span>](data-types-data-mining.md)  
  
  
