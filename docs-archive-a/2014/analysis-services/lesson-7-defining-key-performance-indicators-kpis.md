---
title: 第7课：定义关键绩效指标 (Kpi) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 36d53770-294f-43ab-8850-15d5351ff60c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 87df6fd91a66505f124144cafd9a44c6e5e70e85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689087"
---
# <a name="lesson-7-defining-key-performance-indicators-kpis"></a><span data-ttu-id="1d9eb-102">第 7 课：定义关键绩效指标 (KPI)</span><span class="sxs-lookup"><span data-stu-id="1d9eb-102">Lesson 7: Defining Key Performance Indicators (KPIs)</span></span>
  <span data-ttu-id="1d9eb-103">在本课中，您将了解如何在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目中定义关键绩效指标 (KPI)。</span><span class="sxs-lookup"><span data-stu-id="1d9eb-103">In this lesson, you learn to define Key Performance Indicators (KPIs) in your [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="1d9eb-104">KPI 可以为用于定义度量业务的服务器端计算提供框架，并且也可以使结果信息的显示方式标准化。</span><span class="sxs-lookup"><span data-stu-id="1d9eb-104">KPIs provide a framework for defining server-side calculations that measure your business, and they standardize how the resulting information is displayed.</span></span> <span data-ttu-id="1d9eb-105">使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 工具和第三方工具，通过数据访问 API，KPI 可以显示在报表、门户和仪表板中。</span><span class="sxs-lookup"><span data-stu-id="1d9eb-105">KPIs can be displayed in reports, portals, and dashboards, through data access APIs, and through [!INCLUDE[msCoName](../includes/msconame-md.md)] tools and third-party tools.</span></span> <span data-ttu-id="1d9eb-106">KPI 是对常规度量值和其他多维表达式 (MDX) 表达式的元数据包装。</span><span class="sxs-lookup"><span data-stu-id="1d9eb-106">KPIs are metadata wrappers around regular measures and other Multidimensional Expressions (MDX) expressions.</span></span> <span data-ttu-id="1d9eb-107">有关详细信息，请参阅 [多维模型中的关键绩效指标 (KPI)](multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)。</span><span class="sxs-lookup"><span data-stu-id="1d9eb-107">For more information, see [Key Performance Indicators &#40;KPIs&#41; in Multidimensional Models](multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1d9eb-108">本教程的所有课程中的已完成项目均可以从网上获得。</span><span class="sxs-lookup"><span data-stu-id="1d9eb-108">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="1d9eb-109">您可以通过将前一课程的已完成项目作为起始点，跳转到后面的任何课程。</span><span class="sxs-lookup"><span data-stu-id="1d9eb-109">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="1d9eb-110">[单击此处](https://go.microsoft.com/fwlink/?LinkID=221866) 可以下载本教程随附的示例项目。</span><span class="sxs-lookup"><span data-stu-id="1d9eb-110">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="1d9eb-111">本课程包含以下任务：</span><span class="sxs-lookup"><span data-stu-id="1d9eb-111">This lesson contains the following task:</span></span>  
  
 [<span data-ttu-id="1d9eb-112">定义和浏览 KPI</span><span class="sxs-lookup"><span data-stu-id="1d9eb-112">Defining and Browsing KPIs</span></span>](lesson-7-1-defining-and-browsing-kpis.md)  
 <span data-ttu-id="1d9eb-113">在此任务中，将在窗体视图中定义 KPI，然后切换到浏览器视图，以便通过使用 KPI 来浏览多维数据集数据。</span><span class="sxs-lookup"><span data-stu-id="1d9eb-113">In this task, you define KPIs in the Form view and then switch to the Browser view to browse the cube data by using the KPIs.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="1d9eb-114">下一课</span><span class="sxs-lookup"><span data-stu-id="1d9eb-114">Next Lesson</span></span>  
 [<span data-ttu-id="1d9eb-115">第 8 课：定义操作</span><span class="sxs-lookup"><span data-stu-id="1d9eb-115">Lesson 8: Defining Actions</span></span>](lesson-8-defining-actions.md)  
  
## <a name="see-also"></a><span data-ttu-id="1d9eb-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d9eb-116">See Also</span></span>  
 <span data-ttu-id="1d9eb-117">[Analysis Services 教程方案](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="1d9eb-117">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="1d9eb-118">[&#40;艾德作品的多维建模教程&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="1d9eb-118">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 [<span data-ttu-id="1d9eb-119">多维模型中的关键绩效指标 (KPI)</span><span class="sxs-lookup"><span data-stu-id="1d9eb-119">Key Performance Indicators &#40;KPIs&#41; in Multidimensional Models</span></span>](multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)  
  
  
