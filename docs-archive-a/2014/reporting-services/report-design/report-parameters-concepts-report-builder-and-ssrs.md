---
title: 报表参数概念 (报表生成器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b0aa2159-4e49-4713-8824-5ef9a9edbc62
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4b740362daea83b50a62f0b4453ce818ab21ace7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688572"
---
# <a name="report-parameters-concept-report-builder-and-ssrs"></a><span data-ttu-id="19ed9-102">报表参数概念（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="19ed9-102">Report Parameters Concept (Report Builder and SSRS)</span></span>
  <span data-ttu-id="19ed9-103">您可以向报表添加参数，以便链接相关报表、控制报表外观、筛选报表数据或者将报表的作用域限制为特定的用户或位置。</span><span class="sxs-lookup"><span data-stu-id="19ed9-103">You can add parameters to a report to link related reports, to control the report appearance, to filter report data, or to narrow the scope of a report to specific users or locations.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="19ed9-104">报表参数的创建方式如下：</span><span class="sxs-lookup"><span data-stu-id="19ed9-104">Report parameters are created in the following ways:</span></span>  
  
-   <span data-ttu-id="19ed9-105">在定义包含查询变量的数据集查询时自动创建。</span><span class="sxs-lookup"><span data-stu-id="19ed9-105">Automatically, when you define dataset query that contains query variables.</span></span> <span data-ttu-id="19ed9-106">对于每个查询变量，都会创建具有相同名称的相应的数据集查询参数和报表参数。</span><span class="sxs-lookup"><span data-stu-id="19ed9-106">For each query variable, a corresponding dataset query parameter and report parameter with the same names are created.</span></span> <span data-ttu-id="19ed9-107">查询参数可以是对查询变量的引用，或是对存储过程的输入参数的引用。</span><span class="sxs-lookup"><span data-stu-id="19ed9-107">A query parameter can be a reference to a query variable or to an input parameter for a stored procedure.</span></span>  
  
-   <span data-ttu-id="19ed9-108">当您添加对包含查询参数的共享数据集的引用时自动创建。</span><span class="sxs-lookup"><span data-stu-id="19ed9-108">Automatically, when you add a reference to a shared dataset that contains query parameters.</span></span>  
  
-   <span data-ttu-id="19ed9-109">手动方式：当您在“报表数据”窗格中创建报表参数时。</span><span class="sxs-lookup"><span data-stu-id="19ed9-109">Manually, when you create report parameters in the Report Data pane.</span></span> <span data-ttu-id="19ed9-110">参数是可以在报表的表达式中包含的内置集合之一。</span><span class="sxs-lookup"><span data-stu-id="19ed9-110">Parameters are one of the built-in collections that you can include in an expression in a report.</span></span> <span data-ttu-id="19ed9-111">因为使用表达式在整个报表定义中定义值，所以您可以使用参数来控制报表外观或将值传递到相关的子报表或也使用参数的报表。</span><span class="sxs-lookup"><span data-stu-id="19ed9-111">Because expressions are used to define values throughout a report definition, you can use parameters to control report appearance or to pass values to related subreports or reports that also use parameters.</span></span>  
  
 <span data-ttu-id="19ed9-112">有关详细信息，请参阅 [报表参数（报表生成器和报表设计器）](report-parameters-report-builder-and-report-designer.md)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="19ed9-112">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md).</span></span>  
  
 <span data-ttu-id="19ed9-113">经常使用参数在将数据返回到报表之前和之后筛选报表数据。</span><span class="sxs-lookup"><span data-stu-id="19ed9-113">Parameters are frequently used to filter report data both before and after the data is returned to the report.</span></span> <span data-ttu-id="19ed9-114">有关详细信息，请参阅 [对数据进行筛选、分组和排序（报表生成器和 SSRS）](filter-group-and-sort-data-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="19ed9-114">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="19ed9-115">当您设计报表时，报表参数保存在报表定义中。</span><span class="sxs-lookup"><span data-stu-id="19ed9-115">When you design a report, report parameters are saved in the report definition.</span></span> <span data-ttu-id="19ed9-116">当您发布报表时，报表参数与报表定义分开保存和管理。</span><span class="sxs-lookup"><span data-stu-id="19ed9-116">When you publish a report, report parameters are saved and managed separately from the report definition.</span></span> <span data-ttu-id="19ed9-117">在将报表保存到报表服务器之后，可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="19ed9-117">After you save the report to the report server, you can do the following:</span></span>  
  
-   <span data-ttu-id="19ed9-118">直接在报表服务器上独立于报表定义更改报表参数值。</span><span class="sxs-lookup"><span data-stu-id="19ed9-118">Change report parameter values directly on the report server independently from the report definition.</span></span>  
  
-   <span data-ttu-id="19ed9-119">创建多个链接报表，其中，每个链接报表都是一个指向具有一组单独属性值（可以在报表服务器上单独管理）的报表定义的链接。</span><span class="sxs-lookup"><span data-stu-id="19ed9-119">Create multiple linked reports in which each linked report is a link to the report definition with a separate set of parameter values that can be managed independently on the report server.</span></span>  
  
 <span data-ttu-id="19ed9-120">如果您计划为发布的报表创建报表快照、历史记录或订阅，则必须了解报表参数如何影响报表的设计需求。</span><span class="sxs-lookup"><span data-stu-id="19ed9-120">If you plan to create report snapshots, histories, or subscriptions to a published report, you must understand how report parameters affect the design requirements for the report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19ed9-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19ed9-121">See Also</span></span>  
 <span data-ttu-id="19ed9-122">[报表创作概念 &#40;报表生成器和 SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="19ed9-122">[Report Authoring Concepts &#40;Report Builder and SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="19ed9-123">[报表嵌入数据集和共享数据集 &#40;报表生成器和 SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="19ed9-123">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="19ed9-124">教程：向报表添加参数（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="19ed9-124">Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;</span></span>](../tutorial-add-a-parameter-to-your-report-report-builder.md)  
  
  
