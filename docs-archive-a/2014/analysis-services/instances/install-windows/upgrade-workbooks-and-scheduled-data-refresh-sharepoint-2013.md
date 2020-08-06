---
title: " (SharePoint 2013) 升级工作簿和计划的数据刷新 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a49c4af4-e243-4926-be97-74da1f9d54eb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 185fe0864bc4c1cdda9a63fa97a17319d65dc87d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688316"
---
# <a name="upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013"></a><span data-ttu-id="992e9-102">升级工作簿和计划的数据刷新 (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="992e9-102">Upgrade Workbooks and Scheduled Data Refresh (SharePoint 2013)</span></span>
  <span data-ttu-id="992e9-103">本主题说明在以前的 PowerPivot 环境中创建的工作簿的用户体验，以及如何升级 PowerPivot 工作簿以便您可以利用此版本中引入的新功能。</span><span class="sxs-lookup"><span data-stu-id="992e9-103">This topic explains the user experience of workbooks created in previous PowerPivot environments and how to upgrade PowerPivot workbooks so that you can take advantage of new features introduced in this release.</span></span> <span data-ttu-id="992e9-104">若要了解有关新功能的详细信息，请参阅[PowerPivot 中的新增](https://go.microsoft.com/fwlink/?LinkID=203917)功能。</span><span class="sxs-lookup"><span data-stu-id="992e9-104">To learn more about new features, see [What's New in PowerPivot](https://go.microsoft.com/fwlink/?LinkID=203917).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="992e9-105">对于在服务器上自动升级的工作簿，不能回滚升级。</span><span class="sxs-lookup"><span data-stu-id="992e9-105">You cannot rollback upgrade for workbooks that are upgraded automatically on the server.</span></span> <span data-ttu-id="992e9-106">一旦升级某一工作簿后，它就将保持升级状态。</span><span class="sxs-lookup"><span data-stu-id="992e9-106">Once a workbook is upgraded, it remains upgraded.</span></span> <span data-ttu-id="992e9-107">若要使用以前的版本，可以将以前的工作簿重新发布到 SharePoint，还原以前的版本，或者回收工作簿。</span><span class="sxs-lookup"><span data-stu-id="992e9-107">To use a previous version, you can republish the previous workbook to SharePoint, restore a previous version, or recycle the workbook.</span></span> <span data-ttu-id="992e9-108">有关在 SharePoint 中还原或回收文档的详细信息，请参阅 [通过使用回收站和版本控制计划保护内容](https://go.microsoft.com/fwlink/?LinkId=238669)。</span><span class="sxs-lookup"><span data-stu-id="992e9-108">For more information about restoring or recycling a document in SharePoint, see [Plan to protect content by using recycle bins and versioning](https://go.microsoft.com/fwlink/?LinkId=238669).</span></span>  
  
 <span data-ttu-id="992e9-109">本主题包含以下各节：</span><span class="sxs-lookup"><span data-stu-id="992e9-109">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="992e9-110">升级工作簿的概述</span><span class="sxs-lookup"><span data-stu-id="992e9-110">Overview of Upgrading Workbooks</span></span>](#bkmk_overview)  
  
-   [<span data-ttu-id="992e9-111">从 2008 R2 工作簿升级到 SQL Server 2012 Service Pack 1 (SP1) 工作簿</span><span class="sxs-lookup"><span data-stu-id="992e9-111">Upgrade to SQL Server 2012 Service Pack 1 (SP1) workbooks from 2008 R2 Workbooks</span></span>](#bkmk_to_2012sp1_from_2008r2)  
  
-   [<span data-ttu-id="992e9-112">从使用用于 Excel 的 2012 PowerPivot 外接程序创建的版本升级到 Office 2013 工作簿</span><span class="sxs-lookup"><span data-stu-id="992e9-112">Upgrade to Office 2013 workbooks from Versions created by using the 2012 PowerPivot Add-In for Excel</span></span>](#bkmk_to_2012sp1_from_2012)  
  
-   [<span data-ttu-id="992e9-113">从使用用于 Excel 2010 的 2008 R2 PowerPivot 外接程序创建的版本升级到 SQL Server 2012 工作簿</span><span class="sxs-lookup"><span data-stu-id="992e9-113">Upgrade to SQL Server 2012 workbooks from Versions created by using the 2008 R2 PowerPivot Add-In for Excel 2010</span></span>](#bkmk_to_2012_from_2008R2)  
  
-   [<span data-ttu-id="992e9-114">在较新版本的服务器上运行多个工作簿版本</span><span class="sxs-lookup"><span data-stu-id="992e9-114">Running Multiple Workbook Versions on a Newer Server</span></span>](#bkmk_runold)  
  
##  <a name="overview-of-upgrading-workbooks"></a><a name="bkmk_overview"></a><span data-ttu-id="992e9-115">升级工作簿概述</span><span class="sxs-lookup"><span data-stu-id="992e9-115">Overview of Upgrading Workbooks</span></span>  
 <span data-ttu-id="992e9-116">PowerPivot 工作簿是包含嵌入的 PowerPivot 数据的一种 Excel 工作簿。</span><span class="sxs-lookup"><span data-stu-id="992e9-116">A PowerPivot workbook is an Excel workbook that contains embedded PowerPivot data.</span></span> <span data-ttu-id="992e9-117">升级工作簿有两个好处：</span><span class="sxs-lookup"><span data-stu-id="992e9-117">Upgrading a workbook has two benefits:</span></span>  
  
-   <span data-ttu-id="992e9-118">使用 [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)]中的新功能。</span><span class="sxs-lookup"><span data-stu-id="992e9-118">Use new features in [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)].</span></span>  
  
-   <span data-ttu-id="992e9-119">为与在 SharePoint 模式下的 [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] Analysis Services 服务器一起运行的工作簿实现了计划的数据刷新功能。</span><span class="sxs-lookup"><span data-stu-id="992e9-119">Enables scheduled data refresh for workbooks that run with a [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] Analysis Services server in SharePoint mode.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="992e9-120">您无法回滚已升级的工作簿，所以，如果想在 [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)]的早期版本或 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]的早期版本中使用该文件，就一定要制作该文件的副本。</span><span class="sxs-lookup"><span data-stu-id="992e9-120">You cannot rollback an upgraded workbook, so be sure to make a copy of the file if you want to use it in the previous version of [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)], or on a previous version of [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)].</span></span>  
  
 <span data-ttu-id="992e9-121">下表基于创建了工作簿的环境，列出了对 PowerPivot 工作簿的支持和行为。</span><span class="sxs-lookup"><span data-stu-id="992e9-121">The following table lists the support and behavior of PowerPivot workbooks based on the environment  in which the workbook was created.</span></span> <span data-ttu-id="992e9-122">描述的行为包括一般的用户体验、用于将工作簿升级到特定环境的支持的升级选项以及尚未升级的工作簿的计划的数据刷新。</span><span class="sxs-lookup"><span data-stu-id="992e9-122">The behavior described includes the general user experience, the supported upgrade options to upgrade the workbook to the particular environment, and the behavior of scheduled data refresh of a workbook that has not yet been upgraded.</span></span>  
  
### <a name="workbook-behavior-and-upgrade-options"></a><span data-ttu-id="992e9-123">工作簿行为和升级选项</span><span class="sxs-lookup"><span data-stu-id="992e9-123">Workbook Behavior and Upgrade Options</span></span>  
  
|<span data-ttu-id="992e9-124">创建于</span><span class="sxs-lookup"><span data-stu-id="992e9-124">Created In</span></span>|\<|<span data-ttu-id="992e9-125">支持和行为</span><span class="sxs-lookup"><span data-stu-id="992e9-125">Support and Behavior</span></span>|>|  
|----------------|--------|--------------------------|--------|  
||<span data-ttu-id="992e9-126">**2008 R2 PowerPivot for SharePoint 2010**</span><span class="sxs-lookup"><span data-stu-id="992e9-126">**2008 R2 PowerPivot for SharePoint 2010**</span></span>|<span data-ttu-id="992e9-127">**2012 PowerPivot for SharePoint 2010**</span><span class="sxs-lookup"><span data-stu-id="992e9-127">**2012 PowerPivot for SharePoint 2010**</span></span>|<span data-ttu-id="992e9-128">**2012 SP1 PowerPivot for SharePoint 2013**</span><span class="sxs-lookup"><span data-stu-id="992e9-128">**2012 SP1 PowerPivot for SharePoint 2013**</span></span>|  
|<span data-ttu-id="992e9-129">**2008 R2 PowerPivot for Excel 2010**</span><span class="sxs-lookup"><span data-stu-id="992e9-129">**2008 R2 PowerPivot for Excel 2010**</span></span>|<span data-ttu-id="992e9-130">所有功能</span><span class="sxs-lookup"><span data-stu-id="992e9-130">All Features</span></span>|<span data-ttu-id="992e9-131">**体验：** 用户可在浏览器中与工作簿交互，并且将其用作其他解决方案的数据源。</span><span class="sxs-lookup"><span data-stu-id="992e9-131">**Experience:** Users can interact with the workbook in the browser and use it as a data source for other solutions.</span></span><br /><br /> <span data-ttu-id="992e9-132">**升级：** 如果为 SharePoint 场中的 PowerPivot 系统服务启用了“自动升级”，则工作簿将在文档库中自动升级。</span><span class="sxs-lookup"><span data-stu-id="992e9-132">**Upgrade:** Workbooks will auto upgrade in the document library if Auto Upgrade is enabled for the PowerPivot system Service in the SharePoint farm,</span></span><br /><br /> <span data-ttu-id="992e9-133">**计划数据刷新：** 不支持。</span><span class="sxs-lookup"><span data-stu-id="992e9-133">**Schedule data refresh:** NOT supported.</span></span> <span data-ttu-id="992e9-134">工作簿需要升级。</span><span class="sxs-lookup"><span data-stu-id="992e9-134">Workbook needs to be upgraded.</span></span>|<span data-ttu-id="992e9-135">**体验：** 用户可与工作簿交互，并且将其用作其他解决方案的数据源。</span><span class="sxs-lookup"><span data-stu-id="992e9-135">**Experience:** Users can interact with the workbook and use it as a data source for other solutions.</span></span><br /><br /> <span data-ttu-id="992e9-136">**升级：** 自动升级不可用。</span><span class="sxs-lookup"><span data-stu-id="992e9-136">**Upgrade:** Auto upgrade is not available.</span></span> <span data-ttu-id="992e9-137">用户必须将其 2008 R2 工作簿手动升级到 2012 版本或 Office 2013 版本。</span><span class="sxs-lookup"><span data-stu-id="992e9-137">Users must manually upgrade their 2008 R2 workbooks to the 2012 version or to the office 2013 version.</span></span><br /><br /> <span data-ttu-id="992e9-138">**计划数据刷新：** 不支持。</span><span class="sxs-lookup"><span data-stu-id="992e9-138">**Schedule data refresh:** NOT supported.</span></span> <span data-ttu-id="992e9-139">工作簿需要升级。</span><span class="sxs-lookup"><span data-stu-id="992e9-139">Workbook needs to be upgraded.</span></span>|  
|<span data-ttu-id="992e9-140">**2012 PowerPivot for Excel**</span><span class="sxs-lookup"><span data-stu-id="992e9-140">**2012 PowerPivot for Excel**</span></span>|<span data-ttu-id="992e9-141">不支持</span><span class="sxs-lookup"><span data-stu-id="992e9-141">Not supported</span></span>|<span data-ttu-id="992e9-142">所有功能</span><span class="sxs-lookup"><span data-stu-id="992e9-142">All Features</span></span>|<span data-ttu-id="992e9-143">**体验：** 用户可在浏览器中与工作簿交互，并且将其用作其他解决方案的数据源。</span><span class="sxs-lookup"><span data-stu-id="992e9-143">**Experience:** Users can interact with the workbook in the browser and use it as a data source for other solutions.</span></span> <span data-ttu-id="992e9-144">计划数据刷新可用。</span><span class="sxs-lookup"><span data-stu-id="992e9-144">Schedule data refresh is available.</span></span><br /><br /> <span data-ttu-id="992e9-145">**升级：** 不支持自动升级。</span><span class="sxs-lookup"><span data-stu-id="992e9-145">**Upgrade:** Auto upgrade is not supported.</span></span> <span data-ttu-id="992e9-146">用户可以将其工作簿手动升级到 Office 2013 版本。</span><span class="sxs-lookup"><span data-stu-id="992e9-146">Users can manually upgrade their workbooks to the Office 2013 version.</span></span><br /><br /> <span data-ttu-id="992e9-147">**计划数据刷新：** 支持。</span><span class="sxs-lookup"><span data-stu-id="992e9-147">**Schedule data refresh:** supported.</span></span>|  
|<span data-ttu-id="992e9-148">**Excel 2013**</span><span class="sxs-lookup"><span data-stu-id="992e9-148">**Excel 2013**</span></span>|<span data-ttu-id="992e9-149">不支持</span><span class="sxs-lookup"><span data-stu-id="992e9-149">Not supported</span></span>|<span data-ttu-id="992e9-150">不支持</span><span class="sxs-lookup"><span data-stu-id="992e9-150">Not supported</span></span>|<span data-ttu-id="992e9-151">所有功能</span><span class="sxs-lookup"><span data-stu-id="992e9-151">All Features</span></span>|  
  
##  <a name="upgrade-to-sql-server-2012-service-pack-1-sp1-workbooks-from-2008-r2-workbooks"></a><a name="bkmk_to_2012sp1_from_2008r2"></a><span data-ttu-id="992e9-152">升级到 SQL Server 2012 Service Pack 1 (SP1) 2008 R2 工作簿中的工作簿</span><span class="sxs-lookup"><span data-stu-id="992e9-152">Upgrade to SQL Server 2012 Service Pack 1 (SP1) workbooks from 2008 R2 Workbooks</span></span>  
 <span data-ttu-id="992e9-153">本节介绍如何从 SQL Server 2008 R2 PowerPivot for Excel 2010 工作簿升级到 SQL Server 2012 SP1 PowerPivot for Excel 2013 工作簿。</span><span class="sxs-lookup"><span data-stu-id="992e9-153">This section describes upgrading to SQL Server 2012 SP1 PowerPivot for Excel 2013 workbooks from SQL Server 2008 R2 PowerPivot for Excel 2010 workbooks.</span></span>  
  
 <span data-ttu-id="992e9-154">**行为更改：** 在 SQL Server 2012 SP1 PowerPivot for SharePoint 2013 中使用时，SQL Server 2008 R2 PowerPivot 工作簿将不会自动升级。</span><span class="sxs-lookup"><span data-stu-id="992e9-154">**Behavior Change:** SQL Server 2008 R2 PowerPivot workbooks will not be automatically upgraded  when they are used in SQL Server 2012 SP1 PowerPivot for SharePoint 2013.</span></span> <span data-ttu-id="992e9-155">因此，计划的数据刷新将不适用于 SQL Server 2008 R2 PowerPivot 工作簿。</span><span class="sxs-lookup"><span data-stu-id="992e9-155">Therefore, scheduled data refreshes will not work for SQL Server 2008 R2 PowerPivot workbooks</span></span>  
  
 <span data-ttu-id="992e9-156">2008 R2 工作簿将在 PowerPivot for SharePoint 2013 中打开，但计划的数据刷新将不起作用。</span><span class="sxs-lookup"><span data-stu-id="992e9-156">2008 R2 workbooks will open in PowerPivot for SharePoint 2013, however scheduled data refreshes will not work.</span></span> <span data-ttu-id="992e9-157">如果查看刷新历史记录，您将会看到如下错误消息：</span><span class="sxs-lookup"><span data-stu-id="992e9-157">If you review the refresh history you will see an error message similar to the following:</span></span>  
  
 <span data-ttu-id="992e9-158">"该工作簿包含不支持的 PowerPivot 模型。</span><span class="sxs-lookup"><span data-stu-id="992e9-158">"The workbook contains an unsupported PowerPivot model.</span></span> <span data-ttu-id="992e9-159">该工作簿中的 PowerPivot 模型采用 SQL Server 2008 R2 PowerPivot for Excel 2010 格式。</span><span class="sxs-lookup"><span data-stu-id="992e9-159">The PowerPivot model in the workbook is in the SQL Server 2008 R2 PowerPivot for Excel 2010 format.</span></span> <span data-ttu-id="992e9-160">支持的 PowerPivot 模型如下：</span><span class="sxs-lookup"><span data-stu-id="992e9-160">Supported PowerPivot models are the following:</span></span>  
  
-   <span data-ttu-id="992e9-161">SQL Server 2012 PowerPivot for Excel 2010。</span><span class="sxs-lookup"><span data-stu-id="992e9-161">SQL Server 2012 PowerPivot for Excel 2010.</span></span>  
  
-   <span data-ttu-id="992e9-162">SQL Server 2012 PowerPivot for Excel 2013。</span><span class="sxs-lookup"><span data-stu-id="992e9-162">SQL Server 2012 PowerPivot for Excel 2013.</span></span>  
  
 <span data-ttu-id="992e9-163">**如何升级工作簿：** 在将工作簿升级到 2012 工作簿之前，计划的数据刷新将不起作用。</span><span class="sxs-lookup"><span data-stu-id="992e9-163">**How to upgrade a workbook:** The Scheduled data refresh will not work until you upgrade the workbook to a 2012 workbook.</span></span> <span data-ttu-id="992e9-164">若要升级工作簿以及工作簿中所包含的模型，请完成以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="992e9-164">To upgrade the workbook and model it contains, complete one of the following:</span></span>  
  
-   <span data-ttu-id="992e9-165">下载工作簿并在安装有 SQL Server 2012 PowerPivot for Excel 外接程序的 Microsoft Excel 2010 中打开该工作簿。</span><span class="sxs-lookup"><span data-stu-id="992e9-165">Download and open the workbook in Microsoft Excel 2010 with the SQL Server 2012 PowerPivot for Excel add-in installed.</span></span>  
  
     <span data-ttu-id="992e9-166">打开 PowerPivot 窗口并且升级 PowerPivot 模型。</span><span class="sxs-lookup"><span data-stu-id="992e9-166">Open the PowerPivot window and upgrade the PowerPivot model.</span></span>  
  
     <span data-ttu-id="992e9-167">然后保存该工作簿并将其重新发布到 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="992e9-167">Then save the workbook and republish it to SharePoint.</span></span>  
  
-   <span data-ttu-id="992e9-168">下载该工作簿并在 Microsoft Excel 2013 中打开它。</span><span class="sxs-lookup"><span data-stu-id="992e9-168">Download and open the workbook in Microsoft Excel 2013.</span></span>  
  
     <span data-ttu-id="992e9-169">打开 PowerPivot 窗口并且升级 PowerPivot 模型。</span><span class="sxs-lookup"><span data-stu-id="992e9-169">Open the PowerPivot window and upgrade the PowerPivot model.</span></span>  
  
     <span data-ttu-id="992e9-170">然后保存该工作簿并将其重新发布到 SharePoint 服务器。</span><span class="sxs-lookup"><span data-stu-id="992e9-170">Then save the workbook and republish it to the SharePoint server.</span></span>  
  
 <span data-ttu-id="992e9-171">有关 Analysis Services 功能的更改的详细信息，请参阅[SQL Server 2014 中 Analysis Services 功能的行为更改](../../behavior-changes-to-analysis-services-features-in-sql-server-2014.md)</span><span class="sxs-lookup"><span data-stu-id="992e9-171">For more information on Changes to Analysis Services features, see [Behavior Changes to Analysis Services Features in SQL Server 2014](../../behavior-changes-to-analysis-services-features-in-sql-server-2014.md)</span></span>  
  
 <span data-ttu-id="992e9-172">有关刷新历史记录的详细信息，请参阅[查看数据刷新历史记录 &#40;PowerPivot for SharePoint&#41;](../../power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="992e9-172">For more information on refresh history, see [View Data Refresh History &#40;PowerPivot for SharePoint&#41;](../../power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md).</span></span>  
  
##  <a name="upgrade-to-office-2013-workbooks-from-versions-created-by-using-the-2012-powerpivot-add-in-for-excel"></a><a name="bkmk_to_2012sp1_from_2012"></a><span data-ttu-id="992e9-173">从通过使用用于 Excel 的 2012 PowerPivot 外接程序创建的版本升级到 Office 2013 工作簿</span><span class="sxs-lookup"><span data-stu-id="992e9-173">Upgrade to Office 2013 workbooks from Versions created by using the 2012 PowerPivot Add-In for Excel</span></span>  
 <span data-ttu-id="992e9-174">\*\*\*\* 本节介绍如何从 SQL Server 2012 PowerPivot for Excel 2010 工作簿升级到 Excel 2013 中的 SQL Server 2012 SP1 PowerPivot \*\*\*\* 。</span><span class="sxs-lookup"><span data-stu-id="992e9-174">This section describes Upgrading **to** SQL Server 2012 SP1 PowerPivot in Excel 2013 **from** SQL Server 2012 PowerPivot for Excel 2010 workbooks.</span></span>  
  
 <span data-ttu-id="992e9-175">升级工作簿将解决在以前版本的工作簿上尝试计划的数据刷新时出现的以下错误：</span><span class="sxs-lookup"><span data-stu-id="992e9-175">Upgrading a workbook resolves the following error that occurs when attempting scheduled data refresh on the previous workbook version workbook:</span></span>  
  
 <span data-ttu-id="992e9-176">"对使用早期版本的 PowerPivot 创建的工作簿的刷新操作不可用。"</span><span class="sxs-lookup"><span data-stu-id="992e9-176">"Refresh operation for workbooks created with earlier version of PowerPivot is not available."</span></span>  
  
 <span data-ttu-id="992e9-177">**如何升级工作簿**</span><span class="sxs-lookup"><span data-stu-id="992e9-177">**How to upgrade a workbook**</span></span>  
  
1.  <span data-ttu-id="992e9-178">通过在 Microsoft Excel 2013 中打开工作簿来手动升级每个工作簿。</span><span class="sxs-lookup"><span data-stu-id="992e9-178">Upgrade each workbook manually by opening it in Microsoft Excel 2013.</span></span>  
  
2.  <span data-ttu-id="992e9-179">若要升级工作簿以及工作簿中所包含的模型，请下载该工作簿并在 Microsoft Excel 2013 中打开它。</span><span class="sxs-lookup"><span data-stu-id="992e9-179">To upgrade the workbook and model it contains, download and open the workbook in Microsoft Excel 2013.</span></span>  
  
3.  <span data-ttu-id="992e9-180">打开 PowerPivot 窗口并且升级 PowerPivot 模型。</span><span class="sxs-lookup"><span data-stu-id="992e9-180">Open the PowerPivot window and upgrade the PowerPivot model.</span></span>  
  
4.  <span data-ttu-id="992e9-181">然后保存该工作簿并将其重新发布到 SharePoint 2013 服务器。</span><span class="sxs-lookup"><span data-stu-id="992e9-181">Then save the workbook and republish it to the SharePoint 2013 server.</span></span>  
  
##  <a name="upgrade-to-sql-server-2012-workbooks-from-versions-created-by-using-the-2008-r2-powerpivot-add-in-for-excel-2010"></a><a name="bkmk_to_2012_from_2008R2"></a><span data-ttu-id="992e9-182">升级到使用 2008 R2 PowerPivot 外接程序创建的版本 SQL Server 2012 工作簿2010</span><span class="sxs-lookup"><span data-stu-id="992e9-182">Upgrade to SQL Server 2012 workbooks from Versions created by using the 2008 R2 PowerPivot Add-In for Excel 2010</span></span>  
 <span data-ttu-id="992e9-183">\*\*\*\* 本节介绍如何从 SQL Server 2008 R2 PowerPivot for Excel 2010 工作簿升级到 SQL Server 2012 PowerPivot for Excel 2010 \*\*\*\* 。</span><span class="sxs-lookup"><span data-stu-id="992e9-183">This section describes Upgrading **to** SQL Server 2012 PowerPivot for Excel 2010 **from** SQL Server 2008 R2 PowerPivot for Excel 2010 workbooks.</span></span>  
  
 <span data-ttu-id="992e9-184">升级工作簿将解决在以前版本的工作簿上尝试计划的数据刷新时出现的以下错误：</span><span class="sxs-lookup"><span data-stu-id="992e9-184">Upgrading a workbook resolves the following error that occurs when attempting scheduled data refresh on the previous workbook version workbook:</span></span>  
  
 <span data-ttu-id="992e9-185">"对使用早期版本的 PowerPivot 创建的工作簿的刷新操作不可用。"</span><span class="sxs-lookup"><span data-stu-id="992e9-185">"Refresh operation for workbooks created with earlier version of PowerPivot is not available."</span></span>  
  
 <span data-ttu-id="992e9-186">**如何升级工作簿**</span><span class="sxs-lookup"><span data-stu-id="992e9-186">**How to upgrade a workbook**</span></span>  
  
 <span data-ttu-id="992e9-187">可以使用两种方法进行升级：</span><span class="sxs-lookup"><span data-stu-id="992e9-187">There are two ways to upgrade:</span></span>  
  
1.  <span data-ttu-id="992e9-188">通过在安装有 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 版本的 PowerPivot for Excel 的计算机上在 Excel 中打开工作簿，然后将其重新发布到服务器，手动升级各工作簿。</span><span class="sxs-lookup"><span data-stu-id="992e9-188">Upgrade each workbook manually by opening it in Excel on a computer that has the [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] version of PowerPivot for Excel, and then republish it to the server.</span></span> <span data-ttu-id="992e9-189">当您在外接程序的较新版本中打开此工作簿时，将发生以下内部操作：工作簿数据连接字符串中的数据访问接口将更新为 MSOLAP.5，更新元数据，并重新创建关系以符合较新的实现。</span><span class="sxs-lookup"><span data-stu-id="992e9-189">When you open the workbook in the newer version of the add-in, the following internal operations occur: the data provider in the workbook data connection string is updated to MSOLAP.5, metadata is updated, and relationships are recreated to conform to a newer implementation.</span></span>  
  
2.  <span data-ttu-id="992e9-190">或者，SharePoint 管理员可以在 SharePoint 场中启用针对 PowerPivot 系统服务的自动升级功能，以便在计划数据刷新运行时自动升级 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] PowerPivot 工作簿（仅升级为计划的数据刷新配置的工作簿）。</span><span class="sxs-lookup"><span data-stu-id="992e9-190">Alternatively, a SharePoint Administrator  can enable the auto-upgrade feature for the PowerPivot System Service in a SharePoint farm to  automatically upgrade a [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] PowerPivot workbook when schedule data refresh runs (only workbooks that are configured for scheduled data refresh are upgraded).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="992e9-191">自动升级是一种服务器配置功能；您不能为特定的工作簿、库或网站集启用或禁用该自动升级功能。</span><span class="sxs-lookup"><span data-stu-id="992e9-191">Automatic upgrade is a server configuration feature; you cannot enable or disable it for specific workbooks, libraries, or site collections.</span></span>  
  
 <span data-ttu-id="992e9-192">**如何配置在数据刷新过程中自动升级**</span><span class="sxs-lookup"><span data-stu-id="992e9-192">**How to configure automatic upgrade during data refresh**</span></span>  
  
 <span data-ttu-id="992e9-193">若要使用自动升级，您必须在 PowerPivot 配置工具中选中 **“自动升级 PowerPivot 工作簿以便从服务器启用数据刷新”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="992e9-193">To use automatic upgrade, you must select the **Automatically upgrade PowerPivot workbooks to enable data refresh from the server** checkbox in the PowerPivot Configuration Tool.</span></span> <span data-ttu-id="992e9-194">在该工具中，该复选框位于 **“升级 PowerPivot 系统服务”** 页上和 **“创建 PowerPivot 服务应用程序”** 页上（如果您在配置新安装）。</span><span class="sxs-lookup"><span data-stu-id="992e9-194">Within the tool, the checkbox is on the **Upgrade PowerPivot System Service** page, and on the **Create PowerPivot Service Application** page if you are configuring a new installation.</span></span>  
  
 <span data-ttu-id="992e9-195">您可以运行以下 cmdlet 以便验证是否启用了自动升级：</span><span class="sxs-lookup"><span data-stu-id="992e9-195">You can run the following cmdlet to verify whether automatic upgrade is enabled:</span></span>  
  
```  
PS C:\Windows\system32> Get-PowerPivotSystemService  
```  
  
 <span data-ttu-id="992e9-196">Get-PowerPivotSystemService 的输出是属性和相应值的列表。</span><span class="sxs-lookup"><span data-stu-id="992e9-196">The output from Get-PowerPivotSystemService is a list of properties and corresponding values.</span></span> <span data-ttu-id="992e9-197">您应该会在属性列表中看到 `WorkbookUpgradeOnDataRefresh`。</span><span class="sxs-lookup"><span data-stu-id="992e9-197">You should see `WorkbookUpgradeOnDataRefresh` in the property list.</span></span> <span data-ttu-id="992e9-198">如果启用自动升级，该属性将设置为 **true** 。</span><span class="sxs-lookup"><span data-stu-id="992e9-198">It will be set to **true** if automatic upgrade is enabled.</span></span> <span data-ttu-id="992e9-199">如果该属性为 **false**，则继续执行下一步，启用自动工作簿升级。</span><span class="sxs-lookup"><span data-stu-id="992e9-199">If it is **false**, continue to the next step, enabling automatic workbook upgrade.</span></span>  
  
 <span data-ttu-id="992e9-200">若要启用自动工作簿升级，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="992e9-200">To enable automatic workbook upgrade, run the following command:</span></span>  
  
```  
PS C:\Windows\system32> Set-PowerPivotSystemService -WorkbookUpgradeOnDataRefresh:$true -Confirm:$false  
```  
  
 <span data-ttu-id="992e9-201">升级工作簿后，可使用计划数据刷新和 PowerPivot for Excel 外接程序中的新功能。</span><span class="sxs-lookup"><span data-stu-id="992e9-201">After you upgrade the workbook, you can use scheduled data refresh and new features in the PowerPivot for Excel add-in.</span></span>  
  
##  <a name="running-multiple-workbook-versions-on-a-newer-server"></a><a name="bkmk_runold"></a><span data-ttu-id="992e9-202">在更高版本的服务器上运行多个工作簿版本</span><span class="sxs-lookup"><span data-stu-id="992e9-202">Running Multiple Workbook Versions on a Newer Server</span></span>  
 <span data-ttu-id="992e9-203">可以在 [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] 的 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]实例上并行运行 PowerPivot 工作簿的较旧和较新版本。</span><span class="sxs-lookup"><span data-stu-id="992e9-203">You can run older and newer versions of PowerPivot workbooks side by side on a [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] instance of [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)].</span></span>  
  
 <span data-ttu-id="992e9-204">根据您安装服务器的方式， **可能需要** 安装以前版本的 Analysis Services OLE DB 访问接口，之后才能访问同一服务器上的较旧和较新工作簿。</span><span class="sxs-lookup"><span data-stu-id="992e9-204">Depending on how you installed the server, **you might need** to install a previous version of the Analysis Services OLE DB provider before you can access older and newer workbooks on the same server.</span></span>  
  
 <span data-ttu-id="992e9-205">请注意，不支持在 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 的以前的 SQL Server 实例上发布更新版本的工作簿。</span><span class="sxs-lookup"><span data-stu-id="992e9-205">Note that Publishing newer version workbooks on previous SQL Server instances of [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] is not supported.</span></span> <span data-ttu-id="992e9-206">[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 实例将不加载在 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 的 [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)]版本中创建的工作簿，而 SQL Server 2012 实例将不加载具有您在 Excel 中使用 PowerPivot 的 [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] 版本创建的高级数据模型的 Office 2013 工作簿。</span><span class="sxs-lookup"><span data-stu-id="992e9-206">A [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] instance will not load a workbook that you created in the [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] version of [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)], and a SQL Server 2012 instance will not load Office 2013 workbooks with advanced data models that you created using the [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] version of PowerPivot in Excel.</span></span>  
  
###  <a name="how-to-check-for-msolap-data-provider-information-in-a-powerpivot-workbook"></a><a name="bkmk_msolapxslx"></a><span data-ttu-id="992e9-207">如何检查 PowerPivot 工作簿中的 MSOLAP 数据访问接口信息</span><span class="sxs-lookup"><span data-stu-id="992e9-207">How to Check for MSOLAP Data Provider Information in a PowerPivot Workbook</span></span>  
 <span data-ttu-id="992e9-208">使用下面的说明检查 PowerPivot 工作簿中使用的是哪个 OLE DB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="992e9-208">Use the following instructions to check which OLE DB provider is used in a PowerPivot workbook.</span></span> <span data-ttu-id="992e9-209">检查数据连接信息不需要安装 [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)] 外接程序。</span><span class="sxs-lookup"><span data-stu-id="992e9-209">Checking the data connection information does not require the [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)] add-in to be installed.</span></span>  
  
1.  <span data-ttu-id="992e9-210">在 Excel 中的“数据”选项卡上，单击 **“连接”**。</span><span class="sxs-lookup"><span data-stu-id="992e9-210">In Excel, on the Data tab, click **Connections**.</span></span> <span data-ttu-id="992e9-211">单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="992e9-211">Click **Properties**.</span></span>  
  
2.  <span data-ttu-id="992e9-212">在 **“定义”** 选项卡上，访问接口的版本显示在连接字符串的开头。</span><span class="sxs-lookup"><span data-stu-id="992e9-212">On the **Definition** tab, the provider version appears at the beginning of the connection string.</span></span>  
  
     <span data-ttu-id="992e9-213">**Provider=MSOLAP.5** 指示工作簿是 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="992e9-213">**Provider=MSOLAP.5** indicates the workbook is [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span>  
  
     <span data-ttu-id="992e9-214">**Provider=MSOLAP.4** 指示 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="992e9-214">**Provider=MSOLAP.4** indicates [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)].</span></span>  
  
     <span data-ttu-id="992e9-215">**Data Source = $Embedded $** 指示工作簿是使用嵌入式数据库的 PowerPivot 工作簿。</span><span class="sxs-lookup"><span data-stu-id="992e9-215">**Data Source=$Embedded$** indicates that the workbook is a PowerPivot workbook, using an embedded database.</span></span>  
  
###  <a name="how-to-check-for-the-current-version-of-the-msolap-data-provider-on-a-local-computer"></a><a name="bkmk_msolappc"></a><span data-ttu-id="992e9-216">如何检查本地计算机上 MSOLAP 数据访问接口的当前版本</span><span class="sxs-lookup"><span data-stu-id="992e9-216">How to Check for the Current Version of the MSOLAP Data Provider on a Local Computer</span></span>  
 <span data-ttu-id="992e9-217">使用下面的说明检查 OLE DB 访问接口在运行 PowerPivot 工作簿的服务器或工作站上是否为当前版本。</span><span class="sxs-lookup"><span data-stu-id="992e9-217">Use the following instructions to check which OLE DB provider is the current version on the server or workstation that runs PowerPivot workbooks.</span></span> <span data-ttu-id="992e9-218">了解当前版本可帮助您排除升级后出现的数据连接错误。</span><span class="sxs-lookup"><span data-stu-id="992e9-218">Knowing the current version can help you troubleshoot data connection errors after upgrading.</span></span>  
  
1.  <span data-ttu-id="992e9-219">在注册表编辑器中，转至 HKEY_CLASSES_ROOT。</span><span class="sxs-lookup"><span data-stu-id="992e9-219">In the Registry Editor, go to HKEY_CLASSES_ROOT</span></span>  
  
2.  <span data-ttu-id="992e9-220">向下滚动到 MSOLAP。</span><span class="sxs-lookup"><span data-stu-id="992e9-220">Scroll down to MSOLAP.</span></span> <span data-ttu-id="992e9-221">验证 MSOLAP.5 已列在系统上安装的 OLAP 访问接口中。</span><span class="sxs-lookup"><span data-stu-id="992e9-221">Verify that MSOLAP.5 is listed among the OLAP providers installed on the system.</span></span> <span data-ttu-id="992e9-222">验证 MSOLAP | CurVer 设置为 MSOLAP.5</span><span class="sxs-lookup"><span data-stu-id="992e9-222">Verify that MSOLAP | CurVer is set to MSOLAP.5</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="992e9-223">另请参阅</span><span class="sxs-lookup"><span data-stu-id="992e9-223">See Also</span></span>  
 <span data-ttu-id="992e9-224">[将 PowerPivot 迁移到 SharePoint 2013](migrate-power-pivot-to-sharepoint-2013.md) </span><span class="sxs-lookup"><span data-stu-id="992e9-224">[Migrate PowerPivot to SharePoint 2013](migrate-power-pivot-to-sharepoint-2013.md) </span></span>  
 <span data-ttu-id="992e9-225">[升级 PowerPivot for SharePoint](../../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="992e9-225">[Upgrade PowerPivot for SharePoint](../../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md) </span></span>  
 <span data-ttu-id="992e9-226">[Analysis Services 和商业智能中的新增功能](../../what-s-new-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="992e9-226">[What's New in Analysis Services and Business Intelligence](../../what-s-new-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="992e9-227">查看数据刷新历史记录 &#40;PowerPivot for SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="992e9-227">View Data Refresh History &#40;PowerPivot for SharePoint&#41;</span></span>](../../power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
  
