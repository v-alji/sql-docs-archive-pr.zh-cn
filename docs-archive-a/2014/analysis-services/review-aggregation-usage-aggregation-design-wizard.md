---
title: " (聚合设计向导) 查看聚合使用情况 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.aggregationdesignwizard.reviewusage.f1
ms.assetid: 107ee872-3df2-4931-b56c-af11e38f6745
author: minewiskan
ms.author: owend
ms.openlocfilehash: afbb02dae64f3f7ebd57065c3ff8a7d1e202dcf2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579124"
---
# <a name="review-aggregation-usage-aggregation-design-wizard"></a><span data-ttu-id="e0c1c-102">查看聚合使用情况（聚合设计向导）</span><span class="sxs-lookup"><span data-stu-id="e0c1c-102">Review Aggregation Usage (Aggregation Design Wizard)</span></span>
  <span data-ttu-id="e0c1c-103">可以使用 **“查看聚合使用情况”** 页配置聚合使用情况设置。</span><span class="sxs-lookup"><span data-stu-id="e0c1c-103">Use the **Review Aggregation Usage** page to configure aggregation usage settings.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e0c1c-104">选项</span><span class="sxs-lookup"><span data-stu-id="e0c1c-104">Options</span></span>  
 <span data-ttu-id="e0c1c-105">**Default**</span><span class="sxs-lookup"><span data-stu-id="e0c1c-105">**Default**</span></span>  
 <span data-ttu-id="e0c1c-106">选择此选项可以将属性的聚合使用情况设置设置为默认设置。</span><span class="sxs-lookup"><span data-stu-id="e0c1c-106">Select to set the aggregation usage setting for the attribute to Default.</span></span> <span data-ttu-id="e0c1c-107">通过使用此设置，设计器可以根据属性和维度的类型应用默认规则。</span><span class="sxs-lookup"><span data-stu-id="e0c1c-107">By using this setting, the designer applies a default rule based on the type of attribute and dimension.</span></span>  
  
 `Full`  
 <span data-ttu-id="e0c1c-108">选择此选项可以将属性的聚合使用情况设置设置为 `Full`。</span><span class="sxs-lookup"><span data-stu-id="e0c1c-108">Select to set the aggregation usage setting for the attribute to `Full`.</span></span> <span data-ttu-id="e0c1c-109">使用此设置后，多维数据集的每个聚合都必须包含此属性或属性链中较低的相关属性。</span><span class="sxs-lookup"><span data-stu-id="e0c1c-109">By using this setting, every aggregation for the cube must include this attribute or a related attribute that is lower in the attribute chain.</span></span> <span data-ttu-id="e0c1c-110">如果属性包含有多个成员，则应避免使用 `Full` 聚合使用情况设置。</span><span class="sxs-lookup"><span data-stu-id="e0c1c-110">The `Full` aggregation usage setting should be avoided when an attribute contains many members.</span></span> <span data-ttu-id="e0c1c-111">如果为多个属性或具有多个成员的属性指定了此设置，则此设置可能会以尺寸过大为由，阻止设计聚合。</span><span class="sxs-lookup"><span data-stu-id="e0c1c-111">If specified for multiple attributes or attributes that have many members, this setting might prevent aggregations from being designed because of excessive size.</span></span>  
  
 <span data-ttu-id="e0c1c-112">**无**</span><span class="sxs-lookup"><span data-stu-id="e0c1c-112">**None**</span></span>  
 <span data-ttu-id="e0c1c-113">选择此选项可以将属性的聚合使用情况设置设置为无。</span><span class="sxs-lookup"><span data-stu-id="e0c1c-113">Select to set the aggregation usage setting for the attribute to None.</span></span> <span data-ttu-id="e0c1c-114">使用此设置后，多维数据集的聚合中将不会包含此属性。</span><span class="sxs-lookup"><span data-stu-id="e0c1c-114">By using this setting, no aggregation for the cube can include this attribute.</span></span>  
  
 `Unrestricted`  
 <span data-ttu-id="e0c1c-115">选择此选项可以将属性的聚合使用情况设置设置为 `Unrestricted`。</span><span class="sxs-lookup"><span data-stu-id="e0c1c-115">Select to set the aggregation usage setting for the attribute to `Unrestricted`.</span></span> <span data-ttu-id="e0c1c-116">使用此设置后，聚合设计器将不会受到任何限制，但是仍必须估算属性以确定它是否是一个有价值的聚合候选项。</span><span class="sxs-lookup"><span data-stu-id="e0c1c-116">By using this setting, no restrictions are put on the aggregation designer; however, the attribute must still be evaluated to determine whether it is a valuable aggregation candidate.</span></span>  
  
 <span data-ttu-id="e0c1c-117">**全部设为默认值**</span><span class="sxs-lookup"><span data-stu-id="e0c1c-117">**Set All to Default**</span></span>  
 <span data-ttu-id="e0c1c-118">选择此选项可以将所有属性的聚合使用情况设置设置为默认设置。</span><span class="sxs-lookup"><span data-stu-id="e0c1c-118">Select to set the aggregation usage settings for all attributes to Default.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0c1c-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e0c1c-119">See Also</span></span>  
 <span data-ttu-id="e0c1c-120">[聚合设计向导的 F1 帮助](aggregation-design-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="e0c1c-120">[Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="e0c1c-121">&#40;多维数据的 Analysis Services 向导&#41;</span><span class="sxs-lookup"><span data-stu-id="e0c1c-121">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
