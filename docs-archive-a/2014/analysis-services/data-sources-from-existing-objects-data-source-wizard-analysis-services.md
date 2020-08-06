---
title: 数据源向导 (的现有对象中的数据源，)  (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.datasourcewizard.specifyobject.f1
ms.assetid: e6ef6dea-9db8-45c4-8959-f9febd7caf7b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 621c938f4902c95dee1e2fcccb0f292597a565f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690215"
---
# <a name="data-sources-from-existing-objects-data-source-wizard-analysis-services"></a><span data-ttu-id="66aee-102">来自现有对象的数据源（数据源向导）(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="66aee-102">Data sources from existing objects (Data Source Wizard) (Analysis Services)</span></span>
  <span data-ttu-id="66aee-103">可以使用 **“来自现有对象的数据源”** 页，指定新数据源基于的现有数据源或项目。</span><span class="sxs-lookup"><span data-stu-id="66aee-103">Use the **Data sources from existing objects** page to specify an existing data source or project on which to base the new data source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="66aee-104">选项</span><span class="sxs-lookup"><span data-stu-id="66aee-104">Options</span></span>  
 <span data-ttu-id="66aee-105">**基于解决方案中的现有数据源创建数据源**</span><span class="sxs-lookup"><span data-stu-id="66aee-105">**Create a data source based on an existing data source in your solution**</span></span>  
 <span data-ttu-id="66aee-106">选择此选项可基于解决方案中的现有数据源创建新的数据源。</span><span class="sxs-lookup"><span data-stu-id="66aee-106">Select to base the new data source on an existing data source in the solution.</span></span> <span data-ttu-id="66aee-107">在生成、刷新或部署使用新数据源的项目时，新数据源将从您在选择此选项时指定的数据源获取设置。</span><span class="sxs-lookup"><span data-stu-id="66aee-107">When a project that uses the new data source is built, refreshed, or deployed, the new data source acquires the settings from the data source you specify when you select this option.</span></span>  
  
 <span data-ttu-id="66aee-108">**数据源**</span><span class="sxs-lookup"><span data-stu-id="66aee-108">**Data source**</span></span>  
 <span data-ttu-id="66aee-109">从按项目分组的数据源列表中，选择希望新数据源基于的数据源。</span><span class="sxs-lookup"><span data-stu-id="66aee-109">Select a data source on which you want to base the new data source from the list of data sources, which is grouped by project.</span></span>  
  
 <span data-ttu-id="66aee-110">**基于 Analysis Services 项目创建数据源**</span><span class="sxs-lookup"><span data-stu-id="66aee-110">**Create a data source based on an Analysis Services project**</span></span>  
 <span data-ttu-id="66aee-111">选择此项可创建引用 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 当前解决方案中另一个项目的新数据源 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="66aee-111">Select to create a new data source that references another [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project in the current solution.</span></span> <span data-ttu-id="66aee-112">新数据源将从所选项目的 `TargetServer` 和 `TargetDatabase` 属性获取设置。</span><span class="sxs-lookup"><span data-stu-id="66aee-112">The new data source acquires settings from the `TargetServer` and `TargetDatabase` properties of the selected project.</span></span> <span data-ttu-id="66aee-113">在生成、刷新或部署使用新数据源的项目时，新数据源将从您在选择此选项时指定的数据源获取设置。</span><span class="sxs-lookup"><span data-stu-id="66aee-113">When a project that uses the new data source is built, refreshed, or deployed, the new data source acquires settings from the data source you specify when you select this option.</span></span>  
  
 <span data-ttu-id="66aee-114">**项目**</span><span class="sxs-lookup"><span data-stu-id="66aee-114">**Project**</span></span>  
 <span data-ttu-id="66aee-115">选择希望在新数据源中引用的项目。</span><span class="sxs-lookup"><span data-stu-id="66aee-115">Select the project that you want to reference in the new data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66aee-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="66aee-116">See Also</span></span>  
 <span data-ttu-id="66aee-117">[数据源向导的 F1 帮助 &#40;Analysis Services&#41;](data-source-wizard-f1-help-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="66aee-117">[Data Source Wizard F1 Help &#40;Analysis Services&#41;](data-source-wizard-f1-help-analysis-services.md) </span></span>  
 <span data-ttu-id="66aee-118">[多维模型中的数据源](multidimensional-models/data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="66aee-118">[Data Sources in Multidimensional Models](multidimensional-models/data-sources-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="66aee-119">支持 &#40;SSAS 多维&#41;的数据源</span><span class="sxs-lookup"><span data-stu-id="66aee-119">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
  
