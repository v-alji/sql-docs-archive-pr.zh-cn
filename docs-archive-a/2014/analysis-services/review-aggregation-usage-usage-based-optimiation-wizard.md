---
title: 查看聚合使用情况 (基于使用情况的优化向导) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.reviewaggregationusage.f1
ms.assetid: 49ce2094-c4dc-4e46-8cef-c17c5db084ca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5ef9f900e64858515db226d1f9b864874a4ba827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579123"
---
# <a name="review-aggregation-usage-usage-based-optimiation-wizard"></a><span data-ttu-id="b079e-102">查看聚合使用情况（基于使用情况的优化向导）</span><span class="sxs-lookup"><span data-stu-id="b079e-102">Review Aggregation Usage (Usage-Based Optimiation Wizard)</span></span>
  <span data-ttu-id="b079e-103">可以使用 **“查看聚合使用情况”** 页配置聚合使用情况设置。</span><span class="sxs-lookup"><span data-stu-id="b079e-103">Use the **Review Aggregation Usage** page to configure aggregation usage settings.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b079e-104">选项</span><span class="sxs-lookup"><span data-stu-id="b079e-104">Options</span></span>  
 <span data-ttu-id="b079e-105">**Default**</span><span class="sxs-lookup"><span data-stu-id="b079e-105">**Default**</span></span>  
 <span data-ttu-id="b079e-106">选择此选项可以将属性的聚合使用情况设置设置为默认设置。</span><span class="sxs-lookup"><span data-stu-id="b079e-106">Select to set the aggregation usage setting for the attribute to Default.</span></span> <span data-ttu-id="b079e-107">通过使用此设置，设计器可以根据属性和维度的类型应用默认规则。</span><span class="sxs-lookup"><span data-stu-id="b079e-107">By using this setting, the designer applies a default rule based on the type of attribute and dimension.</span></span>  
  
 <span data-ttu-id="b079e-108">**完整**</span><span class="sxs-lookup"><span data-stu-id="b079e-108">**Full**</span></span>  
 <span data-ttu-id="b079e-109">选择此选项可以将属性的聚合使用情况设置设置为完全。</span><span class="sxs-lookup"><span data-stu-id="b079e-109">Select to set the aggregation usage setting for the attribute to Full.</span></span> <span data-ttu-id="b079e-110">使用此设置后，多维数据集的每个聚合都必须包含此属性或属性链中较低的相关属性。</span><span class="sxs-lookup"><span data-stu-id="b079e-110">By using this setting, every aggregation for the cube must include this attribute or a related attribute that is lower in the attribute chain.</span></span> <span data-ttu-id="b079e-111">如果属性包含有多个成员，则应避免使用 Full 聚合使用情况设置。</span><span class="sxs-lookup"><span data-stu-id="b079e-111">The Full aggregation usage setting should be avoided when an attribute contains many members.</span></span> <span data-ttu-id="b079e-112">如果为多个属性或具有多个成员的属性指定了此设置，则此设置可能会以尺寸过大为由，阻止设计聚合。</span><span class="sxs-lookup"><span data-stu-id="b079e-112">If specified for multiple attributes or attributes that have many members, this setting might prevent aggregations from being designed because of excessive size.</span></span>  
  
 <span data-ttu-id="b079e-113">**无**</span><span class="sxs-lookup"><span data-stu-id="b079e-113">**None**</span></span>  
 <span data-ttu-id="b079e-114">选择此选项可以将属性的聚合使用情况设置设置为无。</span><span class="sxs-lookup"><span data-stu-id="b079e-114">Select to set the aggregation usage setting for the attribute to None.</span></span> <span data-ttu-id="b079e-115">使用此设置后，多维数据集的聚合中将不会包含此属性。</span><span class="sxs-lookup"><span data-stu-id="b079e-115">By using this setting, no aggregation for the cube can include this attribute.</span></span>  
  
 <span data-ttu-id="b079e-116">**L**</span><span class="sxs-lookup"><span data-stu-id="b079e-116">**Unrestricted**</span></span>  
 <span data-ttu-id="b079e-117">选择此选项可以将属性的聚合使用情况设置设置为无限制。</span><span class="sxs-lookup"><span data-stu-id="b079e-117">Select to set the aggregation usage setting for the attribute to Unrestricted.</span></span> <span data-ttu-id="b079e-118">使用此设置后，聚合设计器将不会受到任何限制。</span><span class="sxs-lookup"><span data-stu-id="b079e-118">By using this setting, no restrictions are put on the aggregation designer.</span></span> <span data-ttu-id="b079e-119">但是仍必须估算属性以确定它是否是一个有价值的聚合候选项。</span><span class="sxs-lookup"><span data-stu-id="b079e-119">However, the attribute must still be evaluated to determine whether it is a valuable aggregation candidate.</span></span>  
  
 <span data-ttu-id="b079e-120">**全部设为默认值**</span><span class="sxs-lookup"><span data-stu-id="b079e-120">**Set All to Default**</span></span>  
 <span data-ttu-id="b079e-121">选择此选项可以将所有属性的聚合使用情况设置设置为默认设置。</span><span class="sxs-lookup"><span data-stu-id="b079e-121">Select to set the aggregation usage settings for all attributes to Default.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b079e-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b079e-122">See Also</span></span>  
 <span data-ttu-id="b079e-123">[聚合设计向导的 F1 帮助](aggregation-design-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="b079e-123">[Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="b079e-124">&#40;多维数据的 Analysis Services 向导&#41;</span><span class="sxs-lookup"><span data-stu-id="b079e-124">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
