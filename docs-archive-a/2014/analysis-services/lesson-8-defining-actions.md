---
title: 第8课：定义操作 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 15459396-83c9-48a0-b10a-99ae38768c79
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4d4daaed3f1992478b309529fc15e2e903a27920
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692001"
---
# <a name="lesson-8-defining-actions"></a><span data-ttu-id="11edd-102">第 8 课：定义操作</span><span class="sxs-lookup"><span data-stu-id="11edd-102">Lesson 8: Defining Actions</span></span>
  <span data-ttu-id="11edd-103">在本课中，将了解如何在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目中定义操作。</span><span class="sxs-lookup"><span data-stu-id="11edd-103">In this lesson, you will learn to define actions in your [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="11edd-104">操作只是存储在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中并且可以合并到客户端应用程序中并被用户启动的多维表达式 (MDX) 语句。</span><span class="sxs-lookup"><span data-stu-id="11edd-104">An action is just a Multidimensional Expressions (MDX) statement that is stored in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and which can be incorporated into client applications and started by a user.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="11edd-105">本教程的所有课程中的已完成项目均可以从网上获得。</span><span class="sxs-lookup"><span data-stu-id="11edd-105">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="11edd-106">您可以通过将前一课程的已完成项目作为起始点，跳转到后面的任何课程。</span><span class="sxs-lookup"><span data-stu-id="11edd-106">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="11edd-107">[单击此处](https://go.microsoft.com/fwlink/?LinkID=221866) 可以下载本教程随附的示例项目。</span><span class="sxs-lookup"><span data-stu-id="11edd-107">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="11edd-108">支持下表描述的操作类型。</span><span class="sxs-lookup"><span data-stu-id="11edd-108">supports the types of actions that are described in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="11edd-109">CommandLine</span><span class="sxs-lookup"><span data-stu-id="11edd-109">CommandLine</span></span>|<span data-ttu-id="11edd-110">在命令提示符下执行命令</span><span class="sxs-lookup"><span data-stu-id="11edd-110">Executes a command at the command prompt</span></span>|  
|<span data-ttu-id="11edd-111">数据集</span><span class="sxs-lookup"><span data-stu-id="11edd-111">Dataset</span></span>|<span data-ttu-id="11edd-112">将数据集返回到客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="11edd-112">Returns a dataset to a client application.</span></span>|  
|<span data-ttu-id="11edd-113">钻取</span><span class="sxs-lookup"><span data-stu-id="11edd-113">Drillthrough</span></span>|<span data-ttu-id="11edd-114">将钻取语句作为表达式返回，客户端将执行此语句以返回行集</span><span class="sxs-lookup"><span data-stu-id="11edd-114">Returns a drillthrough statement as an expression, which the client executes to return a rowset</span></span>|  
|<span data-ttu-id="11edd-115">Html</span><span class="sxs-lookup"><span data-stu-id="11edd-115">Html</span></span>|<span data-ttu-id="11edd-116">在 Internet 浏览器中执行 HTML 脚本</span><span class="sxs-lookup"><span data-stu-id="11edd-116">Executes an HTML script in an Internet browser</span></span>|  
|<span data-ttu-id="11edd-117">专有</span><span class="sxs-lookup"><span data-stu-id="11edd-117">Proprietary</span></span>|<span data-ttu-id="11edd-118">使用除此表列出的这些类型以外的其他接口执行操作。</span><span class="sxs-lookup"><span data-stu-id="11edd-118">Performs an operation by using an interface other than those listed in this table.</span></span>|  
|<span data-ttu-id="11edd-119">报表</span><span class="sxs-lookup"><span data-stu-id="11edd-119">Report</span></span>|<span data-ttu-id="11edd-120">将基于参数化 URL 的请求提交到报表服务器，并将报表返回到客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="11edd-120">Submits a parameterized URL-based request to a report server and returns a report to a client application.</span></span>|  
|<span data-ttu-id="11edd-121">行集</span><span class="sxs-lookup"><span data-stu-id="11edd-121">Rowset</span></span>|<span data-ttu-id="11edd-122">将行集返回到客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="11edd-122">Returns a rowset to a client application.</span></span>|  
|<span data-ttu-id="11edd-123">Statement</span><span class="sxs-lookup"><span data-stu-id="11edd-123">Statement</span></span>|<span data-ttu-id="11edd-124">运行 OLE DB 命令。</span><span class="sxs-lookup"><span data-stu-id="11edd-124">Runs an OLE DB command.</span></span>|  
|<span data-ttu-id="11edd-125">URL</span><span class="sxs-lookup"><span data-stu-id="11edd-125">URL</span></span>|<span data-ttu-id="11edd-126">在 Internet 浏览器中显示动态网页。</span><span class="sxs-lookup"><span data-stu-id="11edd-126">Displays a dynamic Web page in an Internet browser.</span></span>|  
  
 <span data-ttu-id="11edd-127">操作让用户能够在所选项的上下文中启动应用程序或执行其他步骤。</span><span class="sxs-lookup"><span data-stu-id="11edd-127">Actions let users start an application or perform other steps within the context of a selected item.</span></span> <span data-ttu-id="11edd-128">有关详细信息，请参阅 [操作（Analysis Services - 多维数据）](multidimensional-models/actions-analysis-services-multidimensional-data.md)和 [多维模型中的操作](multidimensional-models/actions-in-multidimensional-models.md)</span><span class="sxs-lookup"><span data-stu-id="11edd-128">For more information, see [Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md), [Actions in Multidimensional Models](multidimensional-models/actions-in-multidimensional-models.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="11edd-129">有关操作的示例，请参阅“计算工具”窗格中的“模板”选项卡上的操作示例或 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 示例数据仓库中的示例。</span><span class="sxs-lookup"><span data-stu-id="11edd-129">For examples of actions, see the action examples on the Templates tab in the Calculation Tools pane or in the examples in the [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW sample data warehouse.</span></span> <span data-ttu-id="11edd-130">有关如何安装此数据库的详细信息，请参阅 [安装 Analysis Services 多维建模教程的示例数据和项目](install-sample-data-and-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="11edd-130">For more information about installing this database, see [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md).</span></span>  
  
 <span data-ttu-id="11edd-131">本课包括以下任务：</span><span class="sxs-lookup"><span data-stu-id="11edd-131">This lesson includes the following task:</span></span>  
  
 [<span data-ttu-id="11edd-132">定义和使用钻取操作</span><span class="sxs-lookup"><span data-stu-id="11edd-132">Defining and Using a Drillthrough Action</span></span>](lesson-8-1-defining-and-using-a-drillthrough-action.md)  
 <span data-ttu-id="11edd-133">在此任务中，将通过先前在此教程中定义的事实维度关系，来定义、使用然后修改钻取操作。</span><span class="sxs-lookup"><span data-stu-id="11edd-133">In this task, you define, use, and then modify a drillthrough action through the fact dimension relationship that you defined earlier in this tutorial.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="11edd-134">下一课</span><span class="sxs-lookup"><span data-stu-id="11edd-134">Next Lesson</span></span>  
 [<span data-ttu-id="11edd-135">第 9 课：定义透视和翻译</span><span class="sxs-lookup"><span data-stu-id="11edd-135">Lesson 9: Defining Perspectives and Translations</span></span>](lesson-9-defining-perspectives-and-translations.md)  
  
## <a name="see-also"></a><span data-ttu-id="11edd-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="11edd-136">See Also</span></span>  
 <span data-ttu-id="11edd-137">[Analysis Services 教程方案](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="11edd-137">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="11edd-138">[&#40;艾德作品的多维建模教程&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="11edd-138">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 <span data-ttu-id="11edd-139">[Analysis Services 多维数据 &#40;操作&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="11edd-139">[Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="11edd-140">多维模型中的操作</span><span class="sxs-lookup"><span data-stu-id="11edd-140">Actions in Multidimensional Models</span></span>](multidimensional-models/actions-in-multidimensional-models.md)  
  
  
