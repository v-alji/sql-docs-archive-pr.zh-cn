---
title: 挖掘结构的钻取 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a0b00a3b-f9db-4289-a8cb-ddf600cd64ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: e8b3dad28227547f88956f1ac49e2878b2940f91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591653"
---
# <a name="drillthrough-on-mining-structures"></a><span data-ttu-id="8eae9-102">对挖掘结构的钻取功能</span><span class="sxs-lookup"><span data-stu-id="8eae9-102">Drillthrough on Mining Structures</span></span>
  <span data-ttu-id="8eae9-103">“钻取”\*\* 意味着能够查询挖掘模型或挖掘结构并且获取在模型中未公开的详细数据。</span><span class="sxs-lookup"><span data-stu-id="8eae9-103">*Drillthrough* means the ability to query either a mining model or a mining structure and get detailed data that is not exposed in the model.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="8eae9-104">提供了两种不同的选项来钻取到事例数据中。</span><span class="sxs-lookup"><span data-stu-id="8eae9-104">provides two different options for drilling through into case data.</span></span> <span data-ttu-id="8eae9-105">您可以钻取到用来挖掘模型的数据，也可以钻取到挖掘结构中的源数据。</span><span class="sxs-lookup"><span data-stu-id="8eae9-105">You can drill through to the data that were used to build the mining model, or you can drill through to the source data in the mining structure.</span></span>  
  
## <a name="drillthrough-to-model-cases-vs-drillthrough-to-structure"></a><span data-ttu-id="8eae9-106">钻取到模型事例与钻取到结构</span><span class="sxs-lookup"><span data-stu-id="8eae9-106">Drillthrough to Model Cases vs. Drillthrough to Structure</span></span>  
 <span data-ttu-id="8eae9-107">钻取到“模型事例” \*\*\*\* 用于查找与模型中的规则、模式或群集有关的其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="8eae9-107">Drilling through to **model cases** is useful for finding additional details about rules, patterns or clusters in a model.</span></span>  
  
 <span data-ttu-id="8eae9-108">相反，“钻取到结构” \*\*\*\* 数据旨在提供对在模型中未提供的信息的访问。</span><span class="sxs-lookup"><span data-stu-id="8eae9-108">In contrast, **drillthrough to structure** data is intended to provide access to information that was not made available in the model.</span></span> <span data-ttu-id="8eae9-109">例如，如果您具有适当的权限，则可能要确定哪些数据行已用于模型定型，哪些行已用于测试。</span><span class="sxs-lookup"><span data-stu-id="8eae9-109">For example, if you have the appropriate permissions, you might want to find out which rows of data were used for training the model and which were used for testing.</span></span>  
  
 <span data-ttu-id="8eae9-110">还可以查看在分析中未使用的数据属性，只要这些属性已包含在结构定义中。</span><span class="sxs-lookup"><span data-stu-id="8eae9-110">You can also view attributes of the data that were not used in analysis, provided they have been included in the structure definition.</span></span> <span data-ttu-id="8eae9-111">例如，挖掘结构通常支持许多不同类型的模型，并且一些结构列可能已从模型中排除，因为数据类型不兼容或者数据未用于分析。</span><span class="sxs-lookup"><span data-stu-id="8eae9-111">For example, often mining structures support many different kinds of models, and some structure columns might have been excluded from a model because the data type was incompatible or the data was not useful for analysis.</span></span> <span data-ttu-id="8eae9-112">例如，您可能未在聚类分析模型中使用客户联系信息，即使数据已包含在结构中，但通过启用钻取，您能够不对数据源运行单独的查询就获取对此信息的访问权限。</span><span class="sxs-lookup"><span data-stu-id="8eae9-112">For example, you would not use customer contact information in a clustering model, even if the data was included in the structure, but by enabling drillthrough you gain access to this information without running separate queries against the data source.</span></span>  
  
## <a name="enabling-drillthrough-to-structure-data"></a><span data-ttu-id="8eae9-113">对结构数据启用钻取</span><span class="sxs-lookup"><span data-stu-id="8eae9-113">Enabling Drillthrough to Structure Data</span></span>  
 <span data-ttu-id="8eae9-114">若要对挖掘结构使用钻取，必须满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="8eae9-114">To use drillthrough on the mining structure, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="8eae9-115">还必须对模型启用钻取。</span><span class="sxs-lookup"><span data-stu-id="8eae9-115">Drillthrough on the model must also be enabled.</span></span> <span data-ttu-id="8eae9-116">默认情况下，这两种类型的钻取都被禁用。</span><span class="sxs-lookup"><span data-stu-id="8eae9-116">By default, drillthrough of both kinds is disabled.</span></span> <span data-ttu-id="8eae9-117">若要在数据挖掘向导中启用钻取，请在向导的最后一页上选择该选项以便启用对模型事例的钻取。</span><span class="sxs-lookup"><span data-stu-id="8eae9-117">To enable drillthrough in the Data Mining Wizard, select the option to enable drillthrough to model cases on the final page of the wizard.</span></span> <span data-ttu-id="8eae9-118">您还可以通过更改 `AllowDrillthrough` 属性，在以后添加对模型的钻取功能。</span><span class="sxs-lookup"><span data-stu-id="8eae9-118">You can also add the ability to drillthrough on a model later by changing the `AllowDrillthrough` property.</span></span>  
  
-   <span data-ttu-id="8eae9-119">如果您使用 DMX 来创建挖掘结构，请使用 WITH DRILLTHROUGH 子句。</span><span class="sxs-lookup"><span data-stu-id="8eae9-119">If you create the mining structure by using DMX, use the WITH DRILLTHROUGH clause.</span></span> <span data-ttu-id="8eae9-120">有关详细信息，请参阅 [CREATE MINING STRUCTURE (DMX)](/sql/dmx/create-mining-structure-dmx)。</span><span class="sxs-lookup"><span data-stu-id="8eae9-120">For more information, see [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx).</span></span>  
  
-   <span data-ttu-id="8eae9-121">钻取就是检索在处理挖掘结构时缓存的定型事例的相关信息。</span><span class="sxs-lookup"><span data-stu-id="8eae9-121">Drillthrough works by retrieving information about the training cases that was cached when you processed the mining structure.</span></span> <span data-ttu-id="8eae9-122">因此，如果通过将属性更改为来清除缓存的数据，则 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> `ClearAfterProcessing` 钻取功能将不起作用。</span><span class="sxs-lookup"><span data-stu-id="8eae9-122">Therefore, if you clear the cached data after processing the structure by changing the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property to `ClearAfterProcessing`, drillthrough will not work.</span></span> <span data-ttu-id="8eae9-123">若要对结构列启用钻取，则必须将 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> 属性更改为 `KeepTrainingCases`，然后重新处理结构。</span><span class="sxs-lookup"><span data-stu-id="8eae9-123">To enable drillthrough to structure columns, you must change the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property to `KeepTrainingCases` and then reprocess the structure.</span></span>  
  
-   <span data-ttu-id="8eae9-124">验证挖掘结构和挖掘模型都已将[AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl)属性设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="8eae9-124">Verify that both the mining structure and the mining model have the [AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl) property set to `True`.</span></span> <span data-ttu-id="8eae9-125">而且，您必须是对挖掘结构和挖掘模型都具有钻取权限的角色的成员。</span><span class="sxs-lookup"><span data-stu-id="8eae9-125">Moreover, you must be a member of a role that has drillthrough permissions on both the structure and the model.</span></span>  
  
## <a name="security-issues-for-drillthrough"></a><span data-ttu-id="8eae9-126">钻取的安全问题</span><span class="sxs-lookup"><span data-stu-id="8eae9-126">Security Issues for Drillthrough</span></span>  
 <span data-ttu-id="8eae9-127">挖掘结构和挖掘模型的钻取权限是分开设置的。</span><span class="sxs-lookup"><span data-stu-id="8eae9-127">Drillthrough permissions are set separately on the structure and model.</span></span> <span data-ttu-id="8eae9-128">即使不具有结构的钻取权限，模型的钻取权限也会允许您从模型进行钻取。</span><span class="sxs-lookup"><span data-stu-id="8eae9-128">The model permission lets you drill through from the model, even if you do not have permissions on the structure.</span></span> <span data-ttu-id="8eae9-129">如果拥有结构的钻取权限，则可通过使用 [StructureColumn (DMX)](/sql/dmx/structurecolumn-dmx) 函数，将结构列包含到模型钻取查询中。</span><span class="sxs-lookup"><span data-stu-id="8eae9-129">Drillthrough permissions on the structure provide the additional ability to include structure columns in drillthrough queries from the model, by using the [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) function.</span></span>  
  
 <span data-ttu-id="8eae9-130">有关如何在 Analysis Services 中创建角色和分配权限的详细信息，请参阅[角色设计器（Analysis Services - 多维数据）](https://msdn.microsoft.com/library/ms189696(v=sql.120).aspx)。</span><span class="sxs-lookup"><span data-stu-id="8eae9-130">For information about how to create roles and assign permissions in Analysis Services, see [Role Designer &#40;Analysis Services - Multidimensional Data&#41;](https://msdn.microsoft.com/library/ms189696(v=sql.120).aspx).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8eae9-131">如果对挖掘结构和挖掘模型都启用了钻取，则只要用户是拥有挖掘模型的钻取权限的角色成员，就可以查看挖掘结构中的列，即使这些列并未包含在挖掘模型中，也是如此。</span><span class="sxs-lookup"><span data-stu-id="8eae9-131">If you enable drillthrough on both the mining structure and the mining model, any user who is a member of a role that has drillthrough permissions on the mining model can also view columns in the mining structure, even if those columns are not included in the mining model.</span></span> <span data-ttu-id="8eae9-132">因此，为了保护敏感数据，应设置数据源视图来屏蔽个人信息，并且仅在需要时才允许对挖掘结构进行钻取访问。</span><span class="sxs-lookup"><span data-stu-id="8eae9-132">Therefore, to protect sensitive data, you should set up the data source view to mask personal information, and allow drillthrough access on the mining structure only when necessary.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="8eae9-133">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="8eae9-133">Related Tasks</span></span>  
 <span data-ttu-id="8eae9-134">有关如何将钻取功能用于挖掘模型的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="8eae9-134">See the following topics for more information about how to use drillthrough with mining models.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8eae9-135">从挖掘模型查看器对结构使用钻取</span><span class="sxs-lookup"><span data-stu-id="8eae9-135">Use drillthrough to structure from the mining model viewers</span></span>|[<span data-ttu-id="8eae9-136">从模型查看器使用钻取</span><span class="sxs-lookup"><span data-stu-id="8eae9-136">Use Drillthrough from the Model Viewers</span></span>](use-drillthrough-from-the-model-viewers.md)|  
|<span data-ttu-id="8eae9-137">有关特定的模型类型，请参阅钻取查询的示例。</span><span class="sxs-lookup"><span data-stu-id="8eae9-137">See examples of drillthrough queries for specific model types.</span></span>|[<span data-ttu-id="8eae9-138">数据挖掘查询</span><span class="sxs-lookup"><span data-stu-id="8eae9-138">Data Mining Queries</span></span>](data-mining-queries.md)|  
|<span data-ttu-id="8eae9-139">获取有关适用于特定挖掘结构和挖掘模型的权限的信息。</span><span class="sxs-lookup"><span data-stu-id="8eae9-139">Get information about permissions that apply to specific mining structures and mining models.</span></span>|[<span data-ttu-id="8eae9-140">授予数据挖掘结构和模型的权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="8eae9-140">Grant permissions on data mining structures and models &#40;Analysis Services&#41;</span></span>](../multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md)|  
  
## <a name="see-also"></a><span data-ttu-id="8eae9-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8eae9-141">See Also</span></span>  
 [<span data-ttu-id="8eae9-142">对挖掘模型的钻取功能</span><span class="sxs-lookup"><span data-stu-id="8eae9-142">Drillthrough on Mining Models</span></span>](drillthrough-on-mining-models.md)  
  
  
