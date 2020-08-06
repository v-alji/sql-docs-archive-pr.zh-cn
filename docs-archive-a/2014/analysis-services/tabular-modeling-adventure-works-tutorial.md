---
title: " (艾德作品的表格建模教程) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 140d0b43-9455-4907-9827-16564a904268
author: minewiskan
ms.author: owend
ms.openlocfilehash: 840e8fe04309486d1583bc46161a4fc66ca7b1bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589227"
---
# <a name="tabular-modeling-adventure-works-tutorial"></a><span data-ttu-id="8e8a8-102">表格建模（Adventure Works 教程）</span><span class="sxs-lookup"><span data-stu-id="8e8a8-102">Tabular Modeling (Adventure Works Tutorial)</span></span>
  <span data-ttu-id="8e8a8-103">本教程提供的课程介绍如何通过使用 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 创建 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]Analysis Services 表格模型。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-103">This tutorial provides lessons on how to create a [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Analysis Services tabular model by using [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="8e8a8-104">学习内容</span><span class="sxs-lookup"><span data-stu-id="8e8a8-104">What You Will Learn</span></span>  
 <span data-ttu-id="8e8a8-105">在本教程的课程中，您将掌握以下内容：</span><span class="sxs-lookup"><span data-stu-id="8e8a8-105">During the course of this tutorial, you will learn the following:</span></span>  
  
-   <span data-ttu-id="8e8a8-106">如何在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中创建新的表格模型项目</span><span class="sxs-lookup"><span data-stu-id="8e8a8-106">How to create a new tabular model project in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
-   <span data-ttu-id="8e8a8-107">如何将数据从 SQL Server 关系数据库导入表格模型项目。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-107">How to import data from a SQL Server relational database into a tabular model project.</span></span>  
  
-   <span data-ttu-id="8e8a8-108">如何创建和管理模型中表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-108">How to create and manage relationships between tables in the model.</span></span>  
  
-   <span data-ttu-id="8e8a8-109">如何创建和管理可帮助用户分析模型数据的计算、度量值和关键绩效指标。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-109">How to create and manage calculations, measures, and Key Performance Indicators that help users analyze model data.</span></span>  
  
-   <span data-ttu-id="8e8a8-110">如果创建和管理透视和层次结构，通过提供业务和应用程序特定的视点，帮助用户更轻松地浏览模型数据。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-110">How to create and manage perspectives and hierarchies that help users more easily browse model data by providing business and application specific viewpoints.</span></span>  
  
-   <span data-ttu-id="8e8a8-111">如何创建分区来将表数据拆分为较小的逻辑部件，然后可以彼此独立地处理这些逻辑部件。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-111">How to create partitions that divide table data into smaller logical parts that can be processed independent from other partitions.</span></span>  
  
-   <span data-ttu-id="8e8a8-112">如何通过创建角色以及用户成员来保护模型对象和数据的安全。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-112">How to secure model objects and data by creating roles with user members.</span></span>  
  
-   <span data-ttu-id="8e8a8-113">如何将表格模型部署到在表格模式下运行的 Analysis Services 的沙盒或生产实例中。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-113">How to deploy a tabular model to a sandbox or production instance of Analysis Services running in Tabular mode.</span></span>  
  
## <a name="tutorial-scenario"></a><span data-ttu-id="8e8a8-114">教程方案</span><span class="sxs-lookup"><span data-stu-id="8e8a8-114">Tutorial Scenario</span></span>  
 <span data-ttu-id="8e8a8-115">本教程基于 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]，这是一家虚构的公司。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-115">This tutorial is based on [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], a fictitious company.</span></span> [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="8e8a8-116">是一家大型跨国制造公司，生产金属复合材料的自行车，产品远销北美、欧洲和亚洲市场。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-116">is a large, multinational manufacturing company that produces and distributes metal and composite bicycles to commercial markets in North America, Europe, and Asia.</span></span> <span data-ttu-id="8e8a8-117">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 公司总部设在华盛顿州的伯瑟尔市，雇佣了 500 名工人。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-117">The headquarters for [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] is in Bothell, Washington, where the company employs 500 workers.</span></span> <span data-ttu-id="8e8a8-118">此外，在 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 市场中还活跃着一些地区销售团队。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-118">Additionally, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] employs several regional sales teams throughout its market base.</span></span>  
  
 <span data-ttu-id="8e8a8-119">为了更好地支持销售和营销团队以及高级管理人员的数据分析需要，您需要创建一个用户表格模型，以便分析 AdventureWorksDW 示例数据库中的互联网销售数据。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-119">To better support the data analysis needs of sales and marketing teams and of senior management, you are tasked with creating a tabular model for users to analyze internet sales data in the AdventureWorksDW sample database.</span></span>  
  
 <span data-ttu-id="8e8a8-120">为了完成本教程和 Adventure Works 互联网销售表格模型，您必须完成一系列课程。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-120">In order to complete the tutorial, and the Adventure Works Internet Sales tabular model, you must complete a number of lessons.</span></span> <span data-ttu-id="8e8a8-121">每一课程中都有许多任务；要完成课程，必须完成每个任务。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-121">Within each lesson are a number of tasks; completing each task in order is necessary for completing the lesson.</span></span> <span data-ttu-id="8e8a8-122">虽然在特定的课程中可能有多个任务可获得类似结果；但您完成每项任务的方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-122">While in a particular lesson there may be several tasks that accomplish a similar outcome; however, how you complete each task is slightly different.</span></span> <span data-ttu-id="8e8a8-123">也就是说，可以通过多种方法完成某个特定任务，并通过使用先前任务中掌握的技能来向您提问。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-123">This is to show that there is often more than one way to complete a particular task, and to challenge you by using skills you learned in previous tasks.</span></span>  
  
 <span data-ttu-id="8e8a8-124">这些课程的目的是引导您完成以下过程：通过使用 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中包含的多项功能创作在内存中模式下运行的基本表格模型。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-124">The purpose of the lessons is to guide you through authoring a basic tabular model running in In-Memory mode by using many of the features included in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="8e8a8-125">因为每一课都以上一课为基础，所以，您应该按顺序完成课程。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-125">Because each lesson builds upon the previous lesson, you should complete the lessons in order.</span></span> <span data-ttu-id="8e8a8-126">在完成所有课程之后，您就已经在 Analysis Services 服务器上创作和部署了 Adventure Works 互联网销售示例表格模型。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-126">Once you have completed all of the lessons, you will have authored and deployed the Adventure Works Internet Sales sample tabular model on an Analysis Services server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8e8a8-127">本教程并未提供有关以下内容的课程或信息：通过使用 SQL Server Management Studio 管理已部署的表格模型数据库，或者使用报表客户端应用程序连接到已部署的模型以浏览模型数据。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-127">This tutorial does not provide lessons or information about managing a deployed tabular model database by using SQL Server Management Studio, or using a reporting client application to connect to a deployed model to browse model data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8e8a8-128">先决条件</span><span class="sxs-lookup"><span data-stu-id="8e8a8-128">Prerequisites</span></span>  
 <span data-ttu-id="8e8a8-129">为了完成本教程，您必须安装了以下必备组件：</span><span class="sxs-lookup"><span data-stu-id="8e8a8-129">In order to complete this tutorial, you must have the following prerequisites installed:</span></span>  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] <span data-ttu-id="8e8a8-130">Analysis Services 实例（在表格模式下运行）。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-130">Analysis Services instance running in Tabular mode.</span></span>  
  
-   [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="8e8a8-131">.</span><span class="sxs-lookup"><span data-stu-id="8e8a8-131">.</span></span>  
  
-   <span data-ttu-id="8e8a8-132">AdventureWorksDW 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-132">AdventureWorksDW sample database.</span></span> <span data-ttu-id="8e8a8-133">此示例数据库包括完成本教程所需的数据。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-133">This sample database includes the data necessary to complete this tutorial.</span></span> <span data-ttu-id="8e8a8-134">若要下载示例数据库，请参阅 [https://github.com/microsoft/sql-server-samples/releases/tag/adventureworks](https://github.com/microsoft/sql-server-samples/releases/tag/adventureworks) 。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-134">To download the sample database, see [https://github.com/microsoft/sql-server-samples/releases/tag/adventureworks](https://github.com/microsoft/sql-server-samples/releases/tag/adventureworks).</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="8e8a8-135">Excel 2003 或更高版本（与课程 11 中的“在 Excel 中分析”功能结合使用）</span><span class="sxs-lookup"><span data-stu-id="8e8a8-135">Excel 2003 or later (for use with the Analyze in Excel feature in lesson 11)</span></span>  
  
## <a name="lessons"></a><span data-ttu-id="8e8a8-136">课程</span><span class="sxs-lookup"><span data-stu-id="8e8a8-136">Lessons</span></span>  
 <span data-ttu-id="8e8a8-137">本教程包括以下几课：</span><span class="sxs-lookup"><span data-stu-id="8e8a8-137">This tutorial includes the following lessons:</span></span>  
  
|<span data-ttu-id="8e8a8-138">课程</span><span class="sxs-lookup"><span data-stu-id="8e8a8-138">Lesson</span></span>|<span data-ttu-id="8e8a8-139">估计完成时间</span><span class="sxs-lookup"><span data-stu-id="8e8a8-139">Estimated time to complete</span></span>|  
|------------|--------------------------------|  
|[<span data-ttu-id="8e8a8-140">第 1 课：创建新的表格模型项目</span><span class="sxs-lookup"><span data-stu-id="8e8a8-140">Lesson 1: Create a New Tabular Model Project</span></span>](lesson-1-create-a-new-tabular-model-project.md)|<span data-ttu-id="8e8a8-141">10 分钟</span><span class="sxs-lookup"><span data-stu-id="8e8a8-141">10 minutes</span></span>|  
|[<span data-ttu-id="8e8a8-142">第 2 课：添加数据</span><span class="sxs-lookup"><span data-stu-id="8e8a8-142">Lesson 2: Add Data</span></span>](lesson-2-add-data.md)|<span data-ttu-id="8e8a8-143">20 分钟</span><span class="sxs-lookup"><span data-stu-id="8e8a8-143">20 minutes</span></span>|  
|[<span data-ttu-id="8e8a8-144">第 3 课：对列重命名</span><span class="sxs-lookup"><span data-stu-id="8e8a8-144">Lesson 3: Rename Columns</span></span>](rename-columns.md)|<span data-ttu-id="8e8a8-145">20 分钟</span><span class="sxs-lookup"><span data-stu-id="8e8a8-145">20 minutes</span></span>|  
|[<span data-ttu-id="8e8a8-146">第 4 课：标记为日期表</span><span class="sxs-lookup"><span data-stu-id="8e8a8-146">Lesson 4: Mark as Date Table</span></span>](lesson-3-mark-as-date-table.md)|<span data-ttu-id="8e8a8-147">3 分钟</span><span class="sxs-lookup"><span data-stu-id="8e8a8-147">3 minutes</span></span>|  
|[<span data-ttu-id="8e8a8-148">第 5 课：创建关系</span><span class="sxs-lookup"><span data-stu-id="8e8a8-148">Lesson 5: Create Relationships</span></span>](lesson-4-create-relationships.md)|<span data-ttu-id="8e8a8-149">10 分钟</span><span class="sxs-lookup"><span data-stu-id="8e8a8-149">10 minutes</span></span>|  
|[<span data-ttu-id="8e8a8-150">第 6 课：创建计算列</span><span class="sxs-lookup"><span data-stu-id="8e8a8-150">Lesson 6: Create Calculated Columns</span></span>](lesson-5-create-calculated-columns.md)|<span data-ttu-id="8e8a8-151">15 分钟</span><span class="sxs-lookup"><span data-stu-id="8e8a8-151">15 minutes</span></span>|  
|[<span data-ttu-id="8e8a8-152">第 7 课：创建度量值</span><span class="sxs-lookup"><span data-stu-id="8e8a8-152">Lesson 7: Create Measures</span></span>](lesson-6-create-measures.md)|<span data-ttu-id="8e8a8-153">30 分钟</span><span class="sxs-lookup"><span data-stu-id="8e8a8-153">30 minutes</span></span>|  
|[<span data-ttu-id="8e8a8-154">第 8 课：创建关键绩效指标</span><span class="sxs-lookup"><span data-stu-id="8e8a8-154">Lesson 8: Create Key Performance Indicators</span></span>](lesson-7-create-key-performance-indicators.md)|<span data-ttu-id="8e8a8-155">15 分钟</span><span class="sxs-lookup"><span data-stu-id="8e8a8-155">15 minutes</span></span>|  
|[<span data-ttu-id="8e8a8-156">第 9 课：创建透视</span><span class="sxs-lookup"><span data-stu-id="8e8a8-156">Lesson 9: Create Perspectives</span></span>](lesson-8-create-perspectives.md)|<span data-ttu-id="8e8a8-157">5 分钟</span><span class="sxs-lookup"><span data-stu-id="8e8a8-157">5 minutes</span></span>|  
|[<span data-ttu-id="8e8a8-158">第 10 课：创建层次结构</span><span class="sxs-lookup"><span data-stu-id="8e8a8-158">Lesson 10: Create Hierarchies</span></span>](lesson-9-create-hierarchies.md)|<span data-ttu-id="8e8a8-159">20 分钟</span><span class="sxs-lookup"><span data-stu-id="8e8a8-159">20 minutes</span></span>|  
|[<span data-ttu-id="8e8a8-160">第 11 课：创建分区</span><span class="sxs-lookup"><span data-stu-id="8e8a8-160">Lesson 11: Create Partitions</span></span>](lesson-10-create-partitions.md)|<span data-ttu-id="8e8a8-161">15 分钟</span><span class="sxs-lookup"><span data-stu-id="8e8a8-161">15 minutes</span></span>|  
|[<span data-ttu-id="8e8a8-162">第 12 课：创建角色</span><span class="sxs-lookup"><span data-stu-id="8e8a8-162">Lesson 12: Create Roles</span></span>](lesson-11-create-roles.md)|<span data-ttu-id="8e8a8-163">15 分钟</span><span class="sxs-lookup"><span data-stu-id="8e8a8-163">15 minutes</span></span>|  
|[<span data-ttu-id="8e8a8-164">第 13 课：在 Excel 中分析</span><span class="sxs-lookup"><span data-stu-id="8e8a8-164">Lesson 13: Analyze in Excel</span></span>](lesson-12-analyze-in-excel.md)|<span data-ttu-id="8e8a8-165">20 分钟</span><span class="sxs-lookup"><span data-stu-id="8e8a8-165">20 minutes</span></span>|  
|[<span data-ttu-id="8e8a8-166">第 14 课：部署</span><span class="sxs-lookup"><span data-stu-id="8e8a8-166">Lesson 14: Deploy</span></span>](lesson-13-deploy.md)|<span data-ttu-id="8e8a8-167">5 分钟</span><span class="sxs-lookup"><span data-stu-id="8e8a8-167">5 minutes</span></span>|  
  
## <a name="supplemental-lessons"></a><span data-ttu-id="8e8a8-168">补充课程</span><span class="sxs-lookup"><span data-stu-id="8e8a8-168">Supplemental Lessons</span></span>  
 <span data-ttu-id="8e8a8-169">本教程还包括 [补充课程](../tutorials/supplemental-lessons.md)。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-169">This tutorial also includes [Supplemental Lessons](../tutorials/supplemental-lessons.md).</span></span> <span data-ttu-id="8e8a8-170">这一节中的主题不是完成本教程所必需的，但对于更好地了解高级表格模型创作功能会很有帮助。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-170">Topics in this section are not required to complete the tutorial, but can be helpful in better understanding advanced tabular model authoring features.</span></span>  
  
 <span data-ttu-id="8e8a8-171">本教程包括以下补充课程：</span><span class="sxs-lookup"><span data-stu-id="8e8a8-171">This tutorial includes the following supplemental lessons:</span></span>  
  
|<span data-ttu-id="8e8a8-172">课程</span><span class="sxs-lookup"><span data-stu-id="8e8a8-172">Lesson</span></span>|<span data-ttu-id="8e8a8-173">估计完成时间</span><span class="sxs-lookup"><span data-stu-id="8e8a8-173">Estimated time to complete</span></span>|  
|------------|--------------------------------|  
|[<span data-ttu-id="8e8a8-174">通过使用行筛选器实现动态安全性</span><span class="sxs-lookup"><span data-stu-id="8e8a8-174">Implement Dynamic Security by Using Row Filters</span></span>](../tutorials/implement-dynamic-security-by-using-row-filters.md)|<span data-ttu-id="8e8a8-175">30 分钟</span><span class="sxs-lookup"><span data-stu-id="8e8a8-175">30 minutes</span></span>|  
|<span data-ttu-id="8e8a8-176">[为 Power View 报表配置报表属性](supplemental-lesson-configure-reporting-properties-for-power-view-reports.md)为 Power View 报表配置报表属性</span><span class="sxs-lookup"><span data-stu-id="8e8a8-176">[Configure Reporting Properties for Power View Reports](supplemental-lesson-configure-reporting-properties-for-power-view-reports.md)Configure Reporting Properties for Power View Reports</span></span>|<span data-ttu-id="8e8a8-177">30 分钟</span><span class="sxs-lookup"><span data-stu-id="8e8a8-177">30 minutes</span></span>|  
  
## <a name="next-step"></a><span data-ttu-id="8e8a8-178">下一步</span><span class="sxs-lookup"><span data-stu-id="8e8a8-178">Next Step</span></span>  
 <span data-ttu-id="8e8a8-179">若要开始学习本教程，请继续第一课： [第 1 课：创建新的表格模型项目](lesson-1-create-a-new-tabular-model-project.md)。</span><span class="sxs-lookup"><span data-stu-id="8e8a8-179">To begin the tutorial, continue to the first lesson: [Lesson 1: Create a New Tabular Model Project](lesson-1-create-a-new-tabular-model-project.md).</span></span>  
  
  
