---
title: " (SSAS 表格) 处理数据 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d88f2dc9-2933-4be5-9bf3-48ffbc2d0a1a
author: minewiskan
ms.author: owend
ms.openlocfilehash: e2066cb6d871f43dda719cab3539253db97bfca7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693517"
---
# <a name="process-data-ssas-tabular"></a><span data-ttu-id="7e3da-102">处理数据（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="7e3da-102">Process Data (SSAS Tabular)</span></span>
  <span data-ttu-id="7e3da-103">在您在缓存模式下将数据导入表格模型时，您在捕获导入时这些数据的快照。</span><span class="sxs-lookup"><span data-stu-id="7e3da-103">When you import data into a tabular model, in Cached mode, you are capturing a snapshot of that data at the time of import.</span></span> <span data-ttu-id="7e3da-104">在某些情况下，这些数据可能永远不会更改并且无需在模型中更新。</span><span class="sxs-lookup"><span data-stu-id="7e3da-104">In some cases, that data may never change and it does not need to be updated in the model.</span></span> <span data-ttu-id="7e3da-105">但可能性更大的情况是，您所导入的数据定期更改，并且为使您的模型反映数据源中的最新数据，需要处理（刷新）数据并且重新计算已计算的数据。</span><span class="sxs-lookup"><span data-stu-id="7e3da-105">However, it is more likely that the data you are importing from changes regularly, and in order for your model to reflect the most recent data from the data sources, it is necessary to process (refresh) the data and re-calculate calculated data.</span></span> <span data-ttu-id="7e3da-106">为了更新模型中的数据，您对所有表、单独表、按分区或者按数据源连接执行处理操作。</span><span class="sxs-lookup"><span data-stu-id="7e3da-106">To update the data in your model, you perform a process action on all tables, on an individual table, by a partition, or by a data source connection.</span></span>  
  
 <span data-ttu-id="7e3da-107">在创作您的模型项目时，必须在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中手动启动处理操作。</span><span class="sxs-lookup"><span data-stu-id="7e3da-107">When authoring your model project, process actions must be initiated manually in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="7e3da-108">在部署了某一模型之后，可以通过使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 执行处理操作，或者使用脚本计划处理操作。</span><span class="sxs-lookup"><span data-stu-id="7e3da-108">After a model has been deployed, process operations can be performed by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or scheduled by using a script.</span></span> <span data-ttu-id="7e3da-109">本文所述的任务全都属于在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中进行模型创作期间您可以执行的处理操作。</span><span class="sxs-lookup"><span data-stu-id="7e3da-109">Tasks described here all pertain to process actions that you can do during model authoring in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="7e3da-110">有关已部署模型的处理操作的详细信息，请参阅[处理数据库、表或分区](tabular-models/process-database-table-or-partition-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7e3da-110">For more information about process actions for a deployed model, see [Process Database, Table, or Partition](tabular-models/process-database-table-or-partition-analysis-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="7e3da-111">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="7e3da-111">Related Tasks</span></span>  
  
|<span data-ttu-id="7e3da-112">主题</span><span class="sxs-lookup"><span data-stu-id="7e3da-112">Topic</span></span>|<span data-ttu-id="7e3da-113">说明</span><span class="sxs-lookup"><span data-stu-id="7e3da-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7e3da-114">手动处理数据（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="7e3da-114">Manually Process Data &#40;SSAS Tabular&#41;</span></span>](manually-process-data-ssas-tabular.md)|<span data-ttu-id="7e3da-115">介绍如何手动处理模型工作区数据。</span><span class="sxs-lookup"><span data-stu-id="7e3da-115">Describes how to manually process model workspace data.</span></span>|  
|[<span data-ttu-id="7e3da-116">数据处理故障排除（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="7e3da-116">Troubleshoot Process Data &#40;SSAS Tabular&#41;</span></span>](troubleshoot-process-data-ssas-tabular.md)|<span data-ttu-id="7e3da-117">介绍如何解决处理操作中发生的问题。</span><span class="sxs-lookup"><span data-stu-id="7e3da-117">Describes how to troubleshoot process operations.</span></span>|  
  
  
