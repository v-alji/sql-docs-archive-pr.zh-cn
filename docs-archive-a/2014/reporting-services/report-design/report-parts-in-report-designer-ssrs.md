---
title: 报表设计器中的报表部件 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.components.f1
ms.assetid: 0c34311d-05d6-4bd2-b452-545fa95f8e7f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7535c5c2c514bc32a11a5fc0d97c6aee1cf5f2d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577281"
---
# <a name="report-parts-in-report-designer-ssrs"></a><span data-ttu-id="6465c-102">报表设计器中的报表部件 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="6465c-102">Report Parts in Report Designer (SSRS)</span></span>
  <span data-ttu-id="6465c-103">在报表设计器中，在您创建了表、图表和项目中的其他报表项后，可以将它们作为“报表部件” \*\* 发布到报表服务器或与报表服务器相集成的 SharePoint 站点中，以便您和他人可以在其他报表中重复使用它们。</span><span class="sxs-lookup"><span data-stu-id="6465c-103">In Report Designer, after you create tables, charts, and other report items in a project, you can publish them as *report parts* to a report server or SharePoint site integrated with a report server so that you and others can reuse them in other reports.</span></span>  
  
 <span data-ttu-id="6465c-104">通常，报表部件在报表设计器中和报表生成器中以相同的方式工作。</span><span class="sxs-lookup"><span data-stu-id="6465c-104">In general, report parts function the same way in Report Designer and in Report Builder.</span></span> <span data-ttu-id="6465c-105">若要了解基本功能，请参阅 msdn.microsoft.com 上的[报表生成器文档](https://go.microsoft.com/fwlink/?LinkId=154494)中的[报表部件 &#40;报表生成器和 SSRS&#41;](../report-parts-report-builder-and-ssrs.md) 。</span><span class="sxs-lookup"><span data-stu-id="6465c-105">To read about basic functionality, see [Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md) in the [Report Builder documentation](https://go.microsoft.com/fwlink/?LinkId=154494) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="6465c-106">但在报表设计器中，报表部件在工作方式上还存在一些基本差异。</span><span class="sxs-lookup"><span data-stu-id="6465c-106">There are fundamental differences in the way report parts work in Report Designer.</span></span> <span data-ttu-id="6465c-107">一个主要的差异就是工作流。</span><span class="sxs-lookup"><span data-stu-id="6465c-107">A main difference is the work flow.</span></span> <span data-ttu-id="6465c-108">报表生成器支持协作创作：我创建了一个报表部件并发布它。</span><span class="sxs-lookup"><span data-stu-id="6465c-108">Report Builder enables collaborative authoring: I create a report part and publish it.</span></span> <span data-ttu-id="6465c-109">您可以重复使用、修改和重新发布该报表部件。</span><span class="sxs-lookup"><span data-stu-id="6465c-109">You can reuse, modify, and republish it.</span></span> <span data-ttu-id="6465c-110">在报表设计器中，发布是单向的：我可以从报表设计器发布一个报表部件，而您可以重复使用该部件。</span><span class="sxs-lookup"><span data-stu-id="6465c-110">In Report Designer, publishing is one-way: I can publish a report part from Report Designer, and you can reuse it.</span></span> <span data-ttu-id="6465c-111">但是，我不能在报表设计器中在报表中重复使用现有的报表部件。</span><span class="sxs-lookup"><span data-stu-id="6465c-111">But I cannot reuse an existing report part in a report in Report Designer.</span></span> <span data-ttu-id="6465c-112">本主题首先快速介绍一下报表部件，然后详细阐述这些差异。</span><span class="sxs-lookup"><span data-stu-id="6465c-112">This topic elaborates on these differences, after a quick overview of report parts.</span></span>  
  
##  <a name="life-cycle-of-report-part-publishing"></a><a name="ComponentWorkflow"></a> <span data-ttu-id="6465c-113">报表部件发布的生命周期</span><span class="sxs-lookup"><span data-stu-id="6465c-113">Life Cycle of Report Part Publishing</span></span>  
 <span data-ttu-id="6465c-114">![rs_ComponentCreation](../media/rs-componentcreation.gif "rs_ComponentCreation")</span><span class="sxs-lookup"><span data-stu-id="6465c-114">![rs_ComponentCreation](../media/rs-componentcreation.gif "rs_ComponentCreation")</span></span>  
  
1.  <span data-ttu-id="6465c-115">在报表设计器中，人员 A 创建一个含报表的项目，而报表中的图表依赖于某一嵌入数据集。</span><span class="sxs-lookup"><span data-stu-id="6465c-115">In Report Designer, Person A creates a project that contains a report with a chart that depends on an embedded dataset.</span></span>  
  
2.  <span data-ttu-id="6465c-116">人员 A 标记该图表及其嵌入的数据集以供发布。</span><span class="sxs-lookup"><span data-stu-id="6465c-116">Person A flags the chart with its embedded dataset for publishing.</span></span> <span data-ttu-id="6465c-117">报表设计器向其分配唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="6465c-117">Report Designer assigns it a unique ID.</span></span> <span data-ttu-id="6465c-118">然后，人员 A 将该报表发布到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="6465c-118">Person A then deploys the report to the report server.</span></span> <span data-ttu-id="6465c-119">报表设计器发布该图表。</span><span class="sxs-lookup"><span data-stu-id="6465c-119">Report Designer publishes the chart.</span></span>  
  
3.  <span data-ttu-id="6465c-120">人员 B 在报表生成器中创建一个空白报表，然后向其添加该图表。</span><span class="sxs-lookup"><span data-stu-id="6465c-120">Person B creates a blank report in Report Builder and adds the chart to it.</span></span> <span data-ttu-id="6465c-121">该图表现在是人员 B 的报表部件，同时嵌入数据集也是报表部件。</span><span class="sxs-lookup"><span data-stu-id="6465c-121">The chart is now part of Person B's report, along with the embedded dataset.</span></span> <span data-ttu-id="6465c-122">人员 B 可以修改位于报表中的该图表和数据集的实例。</span><span class="sxs-lookup"><span data-stu-id="6465c-122">Person B can modify the instances of the chart and dataset that are in the report.</span></span> <span data-ttu-id="6465c-123">这将不会对报表服务器上图表和数据集的实例产生影响，并且不会破坏报表和报表服务器上实例之间的关系。</span><span class="sxs-lookup"><span data-stu-id="6465c-123">This will have no effect on the instances of the chart and dataset on the report server, nor will it break the relationship between the instances in the report and on the report server.</span></span>  
  
     <span data-ttu-id="6465c-124">![rs_BIDScomponentupdate](../media/rs-bidscomponentupdate.gif "rs_BIDScomponentupdate")</span><span class="sxs-lookup"><span data-stu-id="6465c-124">![rs_BIDScomponentupdate](../media/rs-bidscomponentupdate.gif "rs_BIDScomponentupdate")</span></span>  
  
4.  <span data-ttu-id="6465c-125">在报表设计器中，人员 A 修改原始报表中的图表。</span><span class="sxs-lookup"><span data-stu-id="6465c-125">In Report Designer, Person A modifies the chart in the original report.</span></span>  
  
5.  <span data-ttu-id="6465c-126">人员 A 重新部署该报表，这会将该图表重新发布到服务器，因此更新服务器上的该图表。</span><span class="sxs-lookup"><span data-stu-id="6465c-126">Person A redeploys the report, which republishes the chart to the server, thus updating the chart on the server.</span></span>  
  
6.  <span data-ttu-id="6465c-127">在报表生成器中，人员 B 接受来自服务器的更新的图表。</span><span class="sxs-lookup"><span data-stu-id="6465c-127">In Report Builder, Person B accepts the updated chart from the server.</span></span> <span data-ttu-id="6465c-128">这将覆盖人员 B 已对人员 B 的报表中的图表所做的更改。</span><span class="sxs-lookup"><span data-stu-id="6465c-128">This overwrites the changes that Person B had made to the chart in Person B's report.</span></span>  
  
##  <a name="publishing-report-parts"></a><a name="PublishingComponents"></a> <span data-ttu-id="6465c-129">发布报表部件</span><span class="sxs-lookup"><span data-stu-id="6465c-129">Publishing Report Parts</span></span>  
 <span data-ttu-id="6465c-130">在您发布某一报表部件时，报表设计器将向其分配唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="6465c-130">When you publish a report part, Report Designer assigns it a unique ID.</span></span> <span data-ttu-id="6465c-131">之后，它将保持该 ID，无论您对该报表部件进行何种更改。</span><span class="sxs-lookup"><span data-stu-id="6465c-131">From then on, it maintains that ID, no matter what else you change about it.</span></span> <span data-ttu-id="6465c-132">该 ID 将您的报表中的原始报表项链接到该报表部件。</span><span class="sxs-lookup"><span data-stu-id="6465c-132">The ID links the original report item in your report to the report part.</span></span> <span data-ttu-id="6465c-133">在其他报表作者在报表生成器中重复使用该报表部件时，该 ID 还将其报表中的报表部件链接到该报表部件。</span><span class="sxs-lookup"><span data-stu-id="6465c-133">When other report authors reuse the report part in Report Builder, the ID also links the report part in their report to the report part.</span></span>  
  
 <span data-ttu-id="6465c-134">以下是您可以作为报表部件发布的报表项：</span><span class="sxs-lookup"><span data-stu-id="6465c-134">These are the report items you can publish as report parts:</span></span>  
  
-   <span data-ttu-id="6465c-135">图表</span><span class="sxs-lookup"><span data-stu-id="6465c-135">Charts</span></span>  
  
-   <span data-ttu-id="6465c-136">仪表</span><span class="sxs-lookup"><span data-stu-id="6465c-136">Gauges</span></span>  
  
-   <span data-ttu-id="6465c-137">图像和嵌入图像</span><span class="sxs-lookup"><span data-stu-id="6465c-137">Images and embedded images</span></span>  
  
-   <span data-ttu-id="6465c-138">地图</span><span class="sxs-lookup"><span data-stu-id="6465c-138">Maps</span></span>  
  
-   <span data-ttu-id="6465c-139">parameters</span><span class="sxs-lookup"><span data-stu-id="6465c-139">Parameters</span></span>  
  
-   <span data-ttu-id="6465c-140">矩形</span><span class="sxs-lookup"><span data-stu-id="6465c-140">Rectangles</span></span>  
  
-   <span data-ttu-id="6465c-141">表</span><span class="sxs-lookup"><span data-stu-id="6465c-141">Tables</span></span>  
  
-   <span data-ttu-id="6465c-142">矩阵</span><span class="sxs-lookup"><span data-stu-id="6465c-142">Matrices</span></span>  
  
-   <span data-ttu-id="6465c-143">列表</span><span class="sxs-lookup"><span data-stu-id="6465c-143">Lists</span></span>  
  
 <span data-ttu-id="6465c-144">如果您要发布显示数据（例如表、矩阵或图表）的某一报表部件，则可以将该报表部件基于某一共享数据集；否则，在您发布该报表部件时，它所依赖的数据集将作为嵌入数据集保存。</span><span class="sxs-lookup"><span data-stu-id="6465c-144">If you are publishing a report part that displays data, such as a table, matrix, or chart, you can base it on a shared dataset; otherwise, when you publish the report part, the dataset that it depends on is saved as an embedded dataset.</span></span> <span data-ttu-id="6465c-145">嵌入数据集可以基于嵌入数据源，但凭据不存储于嵌入数据源中。</span><span class="sxs-lookup"><span data-stu-id="6465c-145">Embedded datasets can be based on embedded data sources, but credentials are not stored in embedded data sources.</span></span> <span data-ttu-id="6465c-146">因此，如果您的报表部件依赖于使用某一嵌入数据源的嵌入数据集，则重复使用此报表部件的任何人都将需要为该嵌入数据源提供凭据。</span><span class="sxs-lookup"><span data-stu-id="6465c-146">Thus, if your report part depends on an embedded dataset that uses an embedded data source, anyone who reuses this report part will need to provide the credentials for the embedded data source.</span></span> <span data-ttu-id="6465c-147">若要避免这种情况，请将您的嵌入数据集和共享数据集基于具有存储的凭据的共享数据源。</span><span class="sxs-lookup"><span data-stu-id="6465c-147">To avoid this, base your embedded and shared datasets on shared data sources with stored credentials.</span></span> <span data-ttu-id="6465c-148">有关详细信息，请参阅 msdn.microsoft.com 上的[报表生成器文档](https://go.microsoft.com/fwlink/?LinkId=154494)中[报表生成器的报表部件和数据集](../report-data/report-parts-and-datasets-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="6465c-148">For more information, see [Report Parts and Datasets in Report Builder](../report-data/report-parts-and-datasets-in-report-builder.md) in the [Report Builder documentation](https://go.microsoft.com/fwlink/?LinkId=154494) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="6465c-149">在报表设计器中发布报表部件的过程分为以下两步：</span><span class="sxs-lookup"><span data-stu-id="6465c-149">Publishing a report part in Report Designer is a two-step process:</span></span>  
  
1.  <span data-ttu-id="6465c-150">在 **“发布报表部件”** 对话框中标记要发布的报表项。</span><span class="sxs-lookup"><span data-stu-id="6465c-150">Flag the report items that you want to publish in the **Publish Report Parts** dialog box.</span></span>  
  
2.  <span data-ttu-id="6465c-151">部署报表。</span><span class="sxs-lookup"><span data-stu-id="6465c-151">Deploy the report.</span></span>  
  
 <span data-ttu-id="6465c-152">在您部署报表时，报表部件将发布到某一 SharePoint 站点或报表服务器，并且其他人可以重复使用它。</span><span class="sxs-lookup"><span data-stu-id="6465c-152">When you deploy the report, the report part is published to a SharePoint site or report server, and others can reuse it.</span></span> <span data-ttu-id="6465c-153">若要发布某一报表部件，在部署报表时，您必须具有与某一 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 报表服务器的连接并且对其具有足够的权限。</span><span class="sxs-lookup"><span data-stu-id="6465c-153">To publish a report part, you must have a connection to and sufficient permissions on a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] report server when you deploy the report.</span></span>  
  
  
##  <a name="reusing-report-parts"></a><a name="SearchReuseComponents"></a> <span data-ttu-id="6465c-154">重复使用报表部件</span><span class="sxs-lookup"><span data-stu-id="6465c-154">Reusing Report Parts</span></span>  
 <span data-ttu-id="6465c-155">与报表生成器中不同，如果某一项目并非您在其中创建了报表部件的项目，则不能在该项目中搜索和重复使用该报表部件。</span><span class="sxs-lookup"><span data-stu-id="6465c-155">Unlike in Report Builder, you cannot search for and reuse a report part in a project other than the one in which it was created.</span></span>  
  
 <span data-ttu-id="6465c-156">使用报表生成器的报表作者中可以搜索和重复使用您在他们所创建的报表中发布的报表部件。</span><span class="sxs-lookup"><span data-stu-id="6465c-156">Report authors working in Report Builder can search for and reuse report parts that you publish in reports that they create.</span></span>  
  
##  <a name="republishing-report-parts"></a><a name="RepublishingComponents"></a> <span data-ttu-id="6465c-157">重新发布报表部件</span><span class="sxs-lookup"><span data-stu-id="6465c-157">Republishing Report Parts</span></span>  
 <span data-ttu-id="6465c-158">在报表设计器中，您应该从创建了现有报表部件的报表内更新该报表部件。</span><span class="sxs-lookup"><span data-stu-id="6465c-158">In Report Designer, you should update an existing report part from within the report in which you created it.</span></span> <span data-ttu-id="6465c-159">在报表生成器中，报表作者可以重复使用该报表部件，并且可以将其作为新的报表部件发布而无需替换您发布的报表部件。</span><span class="sxs-lookup"><span data-stu-id="6465c-159">In Report Builder, report authors can reuse the report part, and publish it as a new report part without replacing the report part that you published.</span></span> <span data-ttu-id="6465c-160">如果他们有足够的权限，也可以更新您发布的报表部件。</span><span class="sxs-lookup"><span data-stu-id="6465c-160">If they have sufficient permissions they can also update the report part that you published.</span></span> <span data-ttu-id="6465c-161">对网站或服务器上的文件夹具有足够权限的任何人也可以更新存储在那里的报表部件。</span><span class="sxs-lookup"><span data-stu-id="6465c-161">Anyone with sufficient permissions for a folder on a site or server can update the report parts stored there.</span></span> <span data-ttu-id="6465c-162">最后的更新会覆盖以前的更新。</span><span class="sxs-lookup"><span data-stu-id="6465c-162">The last update overwrites previous updates.</span></span>  
  
 <span data-ttu-id="6465c-163">您可以修改报表部件，然后将其重新发布到网站或服务器上。</span><span class="sxs-lookup"><span data-stu-id="6465c-163">You can modify and then republish the report part to the site or server.</span></span> <span data-ttu-id="6465c-164">对于将该报表部件添加到某一报表中的报表生成器报表作者，系统将在他们下次打开该报表时向他们通知所做更改。</span><span class="sxs-lookup"><span data-stu-id="6465c-164">Report Builder report authors who have added that report part to a report are informed of the change the next time they open that report.</span></span> <span data-ttu-id="6465c-165">他们可以选择接受或拒绝您的更改。</span><span class="sxs-lookup"><span data-stu-id="6465c-165">They can choose to accept your changes or not.</span></span>  
  
 <span data-ttu-id="6465c-166">您还可以选择将已经发布的报表部件作为新报表部件发布。</span><span class="sxs-lookup"><span data-stu-id="6465c-166">You can also choose to publish as new a report that you have already published.</span></span> <span data-ttu-id="6465c-167">在“发布报表部件”对话框中，单击“作为新报表部件发布”。</span><span class="sxs-lookup"><span data-stu-id="6465c-167">In the Publish Report Parts dialog box, click the Publish as a new report part.</span></span> <span data-ttu-id="6465c-168">此新报表部件具有新的唯一 ID，并与旧的报表部件没有关系。</span><span class="sxs-lookup"><span data-stu-id="6465c-168">This new report part has a new unique ID and no relationship to the old report part.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="6465c-169">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6465c-169">See Also</span></span>  
 [<span data-ttu-id="6465c-170">管理报表部件</span><span class="sxs-lookup"><span data-stu-id="6465c-170">Managing Report Parts</span></span>](managing-report-parts.md)  
  
  
