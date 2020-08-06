---
title: SQL Server 2014 中的报表生成器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10428"
helpviewer_keywords:
- overview of Report Builder
- getting started
ms.assetid: 55bf4f9c-d037-412f-ae57-3fc39ce32fa5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b2fb8994272eb24594239551d623021f7b87694c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578682"
---
# <a name="report-builder-in-sql-server-2014"></a><span data-ttu-id="eacbc-102">SQL Server 2014 中的报表生成器</span><span class="sxs-lookup"><span data-stu-id="eacbc-102">Report Builder in SQL Server 2014</span></span>
  <span data-ttu-id="eacbc-103">Report Builder 是一种报表创作环境，适用于喜欢在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office 环境下工作的业务用户。</span><span class="sxs-lookup"><span data-stu-id="eacbc-103">Report Builder is a report authoring environment for business users who prefer to work in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office environment.</span></span> <span data-ttu-id="eacbc-104">设计报表时，您可以指定在何处获取数据、获取哪些数据以及如何显示数据。</span><span class="sxs-lookup"><span data-stu-id="eacbc-104">When you design a report, you specify where to get the data, which data to get, and how to display the data.</span></span> <span data-ttu-id="eacbc-105">当您运行报表时，报表处理器将获取您已经指定的所有信息，检索数据，并将数据与报表布局进行组合以生成报表。</span><span class="sxs-lookup"><span data-stu-id="eacbc-105">When you run the report, the report processor takes all the information you have specified, retrieves the data, and combines it with the report layout to generate the report.</span></span> <span data-ttu-id="eacbc-106">您可以在报表生成器中预览报表，也可以将报表发布到报表服务器或处于 SharePoint 集成模式下的报表服务器，让其他人可以运行它。</span><span class="sxs-lookup"><span data-stu-id="eacbc-106">You can preview your reports in Report Builder, or you can publish your report to a report server or a report server in SharePoint integrated mode, where others can run it.</span></span>  
  
 <span data-ttu-id="eacbc-107">本图中的报表包含一个矩阵，带有行组和列组、迷你图、指示器，以及角单元中的摘要饼图，还附带一个地图，有两组地理数据，以颜色和圆圈大小表示。</span><span class="sxs-lookup"><span data-stu-id="eacbc-107">The report in this illustration features a matrix with row and column groups, sparklines, indicators, and a summary pie chart in the corner cell, accompanied by a map with two sets of geographic data represented by color and by circle size.</span></span>  
  
 <span data-ttu-id="eacbc-108">![rs_GettingStartedReport](../media/rs-gettingstartedreport.gif "rs_GettingStartedReport")</span><span class="sxs-lookup"><span data-stu-id="eacbc-108">![rs_GettingStartedReport](../media/rs-gettingstartedreport.gif "rs_GettingStartedReport")</span></span>  
  
##  <a name="jump-start-report-creation"></a><a name="JumpStartReptCreation"></a><span data-ttu-id="eacbc-109">快速开始报表创建</span><span class="sxs-lookup"><span data-stu-id="eacbc-109">Jump-Start Report Creation</span></span>  
  
-   <span data-ttu-id="eacbc-110">**启动你的报表 withreport**由团队中的其他人创建的部件。</span><span class="sxs-lookup"><span data-stu-id="eacbc-110">**Start your report withreport parts** created by someone else on your team.</span></span> <span data-ttu-id="eacbc-111">报表部件是已单独发布到报表服务器或与报表服务器集成的 SharePoint 站点上的报表项。</span><span class="sxs-lookup"><span data-stu-id="eacbc-111">Report parts are report items that have been published separately to a report server or a SharePoint site that is integrated with a report server.</span></span> <span data-ttu-id="eacbc-112">它们可以在其他报表中重用。</span><span class="sxs-lookup"><span data-stu-id="eacbc-112">They can be reused in other reports.</span></span> <span data-ttu-id="eacbc-113">表、矩阵、图表和图像等报表项可以作为报表部件发布。</span><span class="sxs-lookup"><span data-stu-id="eacbc-113">Report items such as tables, matrices, charts, and images can be published as report parts.</span></span>  
  
-   <span data-ttu-id="eacbc-114">从你的团队中的其他人创建的**共享数据集开始**。</span><span class="sxs-lookup"><span data-stu-id="eacbc-114">**Start with a shared dataset** created by someone else on your team.</span></span> <span data-ttu-id="eacbc-115">共享数据集是基于保存到报表服务器或与报表服务器集成的 SharePoint 站点上的共享数据源的查询。</span><span class="sxs-lookup"><span data-stu-id="eacbc-115">Shared datasets are queries based on a shared data source that are saved to a report server or a SharePoint site that is integrated with a report server.</span></span>  
  
-   <span data-ttu-id="eacbc-116">**首先使用表、矩阵或图表向导**。</span><span class="sxs-lookup"><span data-stu-id="eacbc-116">**Start with the Table, Matrix, or Chart wizard**.</span></span> <span data-ttu-id="eacbc-117">选择数据源连接，拖放字段以创建数据集查询，选择布局和样式并自定义报表。</span><span class="sxs-lookup"><span data-stu-id="eacbc-117">Choose a data source connection, drag and drop fields to create a dataset query, select a layout and style, and customize your report.</span></span>  
  
-   <span data-ttu-id="eacbc-118">**开始使用“地图”向导**创建根据地理或几何背景显示聚合数据的报表。</span><span class="sxs-lookup"><span data-stu-id="eacbc-118">**Start with the Map wizard** to create reports that display aggregated data against a geographic or geometric background.</span></span> <span data-ttu-id="eacbc-119">地图数据可以是来自 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询或 Environmental Systems Research Institute, Inc.(ESRI) 形状文件的空间数据。</span><span class="sxs-lookup"><span data-stu-id="eacbc-119">Map data can be spatial data from a [!INCLUDE[tsql](../../includes/tsql-md.md)] query or an Environmental Systems Research Institute, Inc. (ESRI) shapefile.</span></span> <span data-ttu-id="eacbc-120">还可以添加 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Bing 地图图块背景。</span><span class="sxs-lookup"><span data-stu-id="eacbc-120">You can also add a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Bing map tile background.</span></span>  
  

  
##  <a name="design-your-report"></a><a name="DesignRept"></a><span data-ttu-id="eacbc-121">设计报表</span><span class="sxs-lookup"><span data-stu-id="eacbc-121">Design Your Report</span></span>  
  
-   <span data-ttu-id="eacbc-122">**创建具有表、矩阵、图表或自由格式报表布局的报表。**</span><span class="sxs-lookup"><span data-stu-id="eacbc-122">**Create reports with table, matrix, chart, and free-form report layouts.**</span></span> <span data-ttu-id="eacbc-123">为基于列的数据创建表报表，为汇总数据创建矩阵报表（如交叉表或数据透视表报表），为图形数据创建图表报表，为其他任何数据创建自由格式的报表。</span><span class="sxs-lookup"><span data-stu-id="eacbc-123">Create table reports for column-based data, matrix reports (like cross-tab or PivotTable reports) for summarized data, chart reports for graphical data, and free-form reports for anything else.</span></span> <span data-ttu-id="eacbc-124">报表中可以嵌入其他报表和图表，还可以嵌入列表、图形和用于基于 Web 的动态应用程序的控件。</span><span class="sxs-lookup"><span data-stu-id="eacbc-124">Reports can embed other reports and charts, together with lists, graphics, and controls for dynamic Web-based applications.</span></span>  
  
-   <span data-ttu-id="eacbc-125">**来自各种数据源的报表。**</span><span class="sxs-lookup"><span data-stu-id="eacbc-125">**Report from a variety of data sources.**</span></span> <span data-ttu-id="eacbc-126">使用具有 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 托管数据访问接口、OLE DB 提供程序或 ODBC 数据源的任何数据源类型的数据生成报表。</span><span class="sxs-lookup"><span data-stu-id="eacbc-126">Build reports using data from any data source type that has a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-managed data provider, OLE DB provider, or ODBC data source.</span></span> <span data-ttu-id="eacbc-127">可以创建使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、Oracle、Hyperion 及其他数据库中的关系数据和多维数据的报表。</span><span class="sxs-lookup"><span data-stu-id="eacbc-127">You can create reports that use relational and multidimensional data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], Oracle, Hyperion, and other databases.</span></span> <span data-ttu-id="eacbc-128">您可以使用 XML 数据处理扩展插件从任何 XML 数据源检索数据。</span><span class="sxs-lookup"><span data-stu-id="eacbc-128">You can use an XML data processing extension to retrieve data from any XML data source.</span></span> <span data-ttu-id="eacbc-129">可以使用表值函数来设计自定义数据源。</span><span class="sxs-lookup"><span data-stu-id="eacbc-129">You can use table-valued functions to design custom data sources.</span></span>  
  
-   <span data-ttu-id="eacbc-130">**修改现有报表。**</span><span class="sxs-lookup"><span data-stu-id="eacbc-130">**Modify existing reports.**</span></span> <span data-ttu-id="eacbc-131">通过使用报表生成器，你可以自定义和更新在报表设计器中创建的报表 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="eacbc-131">By using Report Builder, you can customize and update reports that were created in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]Report Designer.</span></span>  
  
-   <span data-ttu-id="eacbc-132">通过对数据进行筛选、分组和排序或通过添加公式或表达式来**修改数据**。</span><span class="sxs-lookup"><span data-stu-id="eacbc-132">**Modify your data** by filtering, grouping and sorting data, or by adding formulas or expressions.</span></span>  
  
-   <span data-ttu-id="eacbc-133">**添加图表、仪表、迷你图和指示器** ，以直观的形式汇总数据，使大量聚合信息一目了然。</span><span class="sxs-lookup"><span data-stu-id="eacbc-133">**Add charts, gauges, sparklines, and indicators** to summarize data in a visual format, and present large volumes of aggregated information at a glance.</span></span>  
  
-   <span data-ttu-id="eacbc-134">**添加交互功能**如文档结构图、显示/隐藏按钮以及子报表和钻取报表的钻取链接。</span><span class="sxs-lookup"><span data-stu-id="eacbc-134">**Add interactive features** such as document maps, show/hide buttons, and drillthrough links to subreports and drillthrough reports.</span></span> <span data-ttu-id="eacbc-135">使用参数和筛选器筛选自定义视图的数据。</span><span class="sxs-lookup"><span data-stu-id="eacbc-135">Use parameters and filters to filter data for customized views.</span></span>  
  
-   <span data-ttu-id="eacbc-136">**嵌入或引用图像**和其他资源，包括外部内容。</span><span class="sxs-lookup"><span data-stu-id="eacbc-136">**Embed or reference images** and other resources, including external content.</span></span>  
  

  
##  <a name="manage-your-report"></a><a name="ManageRpt"></a><span data-ttu-id="eacbc-137">管理报表</span><span class="sxs-lookup"><span data-stu-id="eacbc-137">Manage Your Report</span></span>  
  
-   <span data-ttu-id="eacbc-138">**将报表定义保存**到计算机或报表服务器，可在其中对报表进行管理以及与他人共享报表。</span><span class="sxs-lookup"><span data-stu-id="eacbc-138">**Save the definition of the report** to your computer or to the report server, where you can manage it and share it with others.</span></span>  
  
-   <span data-ttu-id="eacbc-139">打开该报表时，或打开报表后，**选择显示格式**。</span><span class="sxs-lookup"><span data-stu-id="eacbc-139">**Choose a presentation format** when you open the report, or after you open the report.</span></span> <span data-ttu-id="eacbc-140">可以选择面向 Web、面向页的格式以及桌面应用程序格式。</span><span class="sxs-lookup"><span data-stu-id="eacbc-140">You can select Web-oriented, page-oriented, and desktop application formats.</span></span> <span data-ttu-id="eacbc-141">这些格式包括 HTML、MHTML、PDF、XML、CSV、TIFF、Word 和 Excel。</span><span class="sxs-lookup"><span data-stu-id="eacbc-141">Formats include HTML, MHTML, PDF, XML, CSV, TIFF, Word, and Excel.</span></span>  
  
-   <span data-ttu-id="eacbc-142">**设置订阅。**</span><span class="sxs-lookup"><span data-stu-id="eacbc-142">**Set up subscriptions.**</span></span> <span data-ttu-id="eacbc-143">在将报表发布到报表服务器或处于 SharePoint 集成模式下的报表服务器之后，您可以将报表配置为在特定时间运行、创建报表历史记录并设置电子邮件订阅。</span><span class="sxs-lookup"><span data-stu-id="eacbc-143">After you publish the report to the report server or a report server in SharePoint integrated mode, you can configure your report to run at a specific time, create a report history, and set up e-mail subscriptions.</span></span>  
  
-   <span data-ttu-id="eacbc-144">**生成数据馈送** ，使用 Reporting Services Atom 呈现扩展插件从报表生成数据馈送。</span><span class="sxs-lookup"><span data-stu-id="eacbc-144">**Generate data feeds** from your report by using the Reporting Services Atom rendering extension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eacbc-145">发布的报表存储在报表服务器或处于 SharePoint 集成模式下的报表服务器上，由报表服务器管理员进行管理。</span><span class="sxs-lookup"><span data-stu-id="eacbc-145">Published reports are managed on a report server or a report server in SharePoint integrated mode by a report server administrator.</span></span> <span data-ttu-id="eacbc-146">报表服务器管理员可以定义安全性、设置属性并计划报表历史记录和电子邮件报表传递等操作。</span><span class="sxs-lookup"><span data-stu-id="eacbc-146">Report server administrators can define security, set properties, and schedule operations such as report history and e-mail report delivery.</span></span> <span data-ttu-id="eacbc-147">他们可以创建共享计划和共享数据源，供常规使用。</span><span class="sxs-lookup"><span data-stu-id="eacbc-147">They can create shared schedules and shared data sources and make them available for general use.</span></span> <span data-ttu-id="eacbc-148">管理员还管理所有报表服务器文件夹。</span><span class="sxs-lookup"><span data-stu-id="eacbc-148">Administrators also manage all of the report server folders.</span></span> <span data-ttu-id="eacbc-149">执行管理任务的能力取决于用户权限。</span><span class="sxs-lookup"><span data-stu-id="eacbc-149">The ability to perform management tasks depends on user permissions.</span></span>  
  

  
##  <a name="in-this-section"></a><a name="InThisSection"></a> <span data-ttu-id="eacbc-150">本节内容</span><span class="sxs-lookup"><span data-stu-id="eacbc-150">In This Section</span></span>  
 [<span data-ttu-id="eacbc-151">SQL Server 2014 的报表生成器中的新增功能</span><span class="sxs-lookup"><span data-stu-id="eacbc-151">What's New in Report Builder for SQL Server 2014</span></span>](../what-s-new-in-report-builder-for-sql-server-2014.md)  
 <span data-ttu-id="eacbc-152">介绍此版本的报表生成器的新增功能，包括地图。</span><span class="sxs-lookup"><span data-stu-id="eacbc-152">Describes the new features in this version of Report Builder, including maps.</span></span>  
  
 [<span data-ttu-id="eacbc-153">教程：脱机创建快速图表报表</span><span class="sxs-lookup"><span data-stu-id="eacbc-153">Tutorial: Creating a Quick Chart Report Offline</span></span>](tutorial-create-a-quick-chart-report-offline-report-builder.md)  
 <span data-ttu-id="eacbc-154">介绍报表生成器以及可用来帮助创建报表的向导。</span><span class="sxs-lookup"><span data-stu-id="eacbc-154">Introduces Report Builder and the wizards available to help you create reports.</span></span> <span data-ttu-id="eacbc-155">教程提供了一组供您使用的数据，因此不需要连接到数据源即可开始工作。</span><span class="sxs-lookup"><span data-stu-id="eacbc-155">The tutorial provides a set of data for you to work with so you do not need to connect to a data source to get started.</span></span>  
  
 [<span data-ttu-id="eacbc-156">规划报表（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="eacbc-156">Planning a Report &#40;Report Builder&#41;</span></span>](../report-design/planning-a-report-report-builder.md)  
 <span data-ttu-id="eacbc-157">提供在开始生成报表之前应当考虑哪些情况的信息。</span><span class="sxs-lookup"><span data-stu-id="eacbc-157">Provides information on what you should consider before you start to build your report.</span></span>  
  
 [<span data-ttu-id="eacbc-158">报表创作概念（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="eacbc-158">Report Authoring Concepts &#40;Report Builder and SSRS&#41;</span></span>](../report-design/report-authoring-concepts-report-builder-and-ssrs.md)  
 <span data-ttu-id="eacbc-159">定义在整个报表生成器文档中使用的主要概念。</span><span class="sxs-lookup"><span data-stu-id="eacbc-159">Defines key concepts used in throughout Report Builder documentation.</span></span>  
  
 [<span data-ttu-id="eacbc-160">报表设计视图（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="eacbc-160">Report Design View &#40;Report Builder&#41;</span></span>](report-design-view-report-builder.md)  
 <span data-ttu-id="eacbc-161">介绍报表设计视图的不同窗格和区域。</span><span class="sxs-lookup"><span data-stu-id="eacbc-161">Explains the different panes and regions of report design view.</span></span>  
  
 [<span data-ttu-id="eacbc-162">共享数据集设计视图（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="eacbc-162">Shared Dataset Design View &#40;Report Builder&#41;</span></span>](shared-dataset-design-view-report-builder.md)  
 <span data-ttu-id="eacbc-163">介绍共享数据集设计视图的不同窗格和区域。</span><span class="sxs-lookup"><span data-stu-id="eacbc-163">Explains the different panes and regions of shared dataset design view.</span></span>  
  
 [<span data-ttu-id="eacbc-164">键盘快捷键（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="eacbc-164">Keyboard Shortcuts &#40;Report Builder&#41;</span></span>](keyboard-shortcuts-report-builder.md)  
 <span data-ttu-id="eacbc-165">概述可用于在报表生成器中导航和设计报表的快捷键。</span><span class="sxs-lookup"><span data-stu-id="eacbc-165">Outlines the shortcut keys available for navigating and designing reports in Report Builder.</span></span>  
  
 [<span data-ttu-id="eacbc-166">开始报表生成器 &#40;报表生成器&#41;</span><span class="sxs-lookup"><span data-stu-id="eacbc-166">Start Report Builder &#40;Report Builder&#41;</span></span>](start-report-builder.md)  
 <span data-ttu-id="eacbc-167">说明如何启动报表生成器的两个不同版本：独立和 [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="eacbc-167">Explains how to start the two different versions of Report Builder: stand-alone and [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)].</span></span>  
  
  
