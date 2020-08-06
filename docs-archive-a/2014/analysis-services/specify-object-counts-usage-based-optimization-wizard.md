---
title: 指定基于使用情况的优化向导 (对象计数) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.calculatingobjectcounts.f1
ms.assetid: 306c7c25-ae24-4852-ab8c-c82f68a4bc1f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 862be19f12308def815a280dba04f42f0cbe6878
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589249"
---
# <a name="specify-object-counts-usage-based-optimization-wizard"></a><span data-ttu-id="769ac-102">指定对象计数（基于使用情况的优化向导）</span><span class="sxs-lookup"><span data-stu-id="769ac-102">Specify Object Counts (Usage-Based Optimization Wizard)</span></span>
  <span data-ttu-id="769ac-103">可以使用 **“指定对象计数”** 页自动计算多维数据集中的对象计数，或者手动输入估计的计数。</span><span class="sxs-lookup"><span data-stu-id="769ac-103">Use the **Specify Object Counts** page to automatically calculate the count of objects in the cube or to manually enter estimated counts.</span></span> <span data-ttu-id="769ac-104">基于使用情况的优化向导使用对象计数来估计存储要求。</span><span class="sxs-lookup"><span data-stu-id="769ac-104">The Usage-Based Optimization Wizard uses the object counts to estimate storage requirements.</span></span>  
  
## <a name="options"></a><span data-ttu-id="769ac-105">选项</span><span class="sxs-lookup"><span data-stu-id="769ac-105">Options</span></span>  
 <span data-ttu-id="769ac-106">**多维数据集对象**</span><span class="sxs-lookup"><span data-stu-id="769ac-106">**Cube Objects**</span></span>  
 <span data-ttu-id="769ac-107">显示多维数据集中的维度和属性。</span><span class="sxs-lookup"><span data-stu-id="769ac-107">Displays the dimensions and attributes in the cube.</span></span> <span data-ttu-id="769ac-108">`AggregationUsage`在向导的 "**查看聚合使用情况**" 页中，只会显示未将属性设置为 "无" 的属性，因为只有这些特性需要指定的计数。</span><span class="sxs-lookup"><span data-stu-id="769ac-108">Only the attributes that do not have their `AggregationUsage` property set to None in the **Review Aggregation Usage** page of the wizard are shown because those are the only attributes that need counts specified.</span></span>  
  
 <span data-ttu-id="769ac-109">**估计的计数**</span><span class="sxs-lookup"><span data-stu-id="769ac-109">**Estimated count**</span></span>  
 <span data-ttu-id="769ac-110">显示度量值组中估计的行数和数据库维度中估计的属性成员计数。</span><span class="sxs-lookup"><span data-stu-id="769ac-110">Displays the estimated number of rows in the measure group and the estimated attribute member counts in the database dimensions.</span></span> <span data-ttu-id="769ac-111">您可以键入一个值，以用作估计的计数，或可以计算估计的计数值。</span><span class="sxs-lookup"><span data-stu-id="769ac-111">You can type a value to use as the estimated count or you can calculate the estimated count values.</span></span> <span data-ttu-id="769ac-112">若要计算计数值，请在该字段中键入 0 ，然后单击“计数” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="769ac-112">To calculate the count values, type 0 in the field and then click **Count**.</span></span> <span data-ttu-id="769ac-113">已显示计数的字段不会更新。</span><span class="sxs-lookup"><span data-stu-id="769ac-113">Fields that already display a count are not updated.</span></span>  
  
 <span data-ttu-id="769ac-114">**分区计数**</span><span class="sxs-lookup"><span data-stu-id="769ac-114">**Partition count**</span></span>  
 <span data-ttu-id="769ac-115">（可选）键入度量值组中估计的行数和分区中估计的属性成员计数。</span><span class="sxs-lookup"><span data-stu-id="769ac-115">(Optional) Type the estimated number of rows in the measure group and the estimated attribute member counts in the partitions.</span></span>  
  
 <span data-ttu-id="769ac-116">**Count**</span><span class="sxs-lookup"><span data-stu-id="769ac-116">**Count**</span></span>  
 <span data-ttu-id="769ac-117">计算并重新填充所有空字段的“估计的计数”\*\*\*\* 列。</span><span class="sxs-lookup"><span data-stu-id="769ac-117">Calculates and repopulates the values in the **Estimated count** column for all empty fields.</span></span> <span data-ttu-id="769ac-118">已显示计数的字段不会更新。</span><span class="sxs-lookup"><span data-stu-id="769ac-118">Fields that already display a count are not updated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="769ac-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="769ac-119">See Also</span></span>  
 <span data-ttu-id="769ac-120">[聚合设计向导的 F1 帮助](aggregation-design-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="769ac-120">[Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="769ac-121">&#40;多维数据的 Analysis Services 向导&#41;</span><span class="sxs-lookup"><span data-stu-id="769ac-121">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
