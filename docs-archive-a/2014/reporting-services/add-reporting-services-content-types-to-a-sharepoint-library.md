---
title: 将报表服务器内容类型添加到 SharePoint 集成模式下的库 (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ac9136c8-9ef4-484c-8e9d-05008a186db5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9e0ee56c235a54920fba5389a61f300eeaa65329
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692814"
---
# <a name="add-report-server-content-types-to-a-library-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="6c40c-102">将报表服务器内容类型添加到库中（SharePoint 集成模式下的 Reporting Services）</span><span class="sxs-lookup"><span data-stu-id="6c40c-102">Add Report Server Content Types to a Library (Reporting Services in SharePoint Integrated Mode)</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="6c40c-103">提供预定义的 SharePoint 内容类型，用于管理共享数据源 (.rsds) 文件、报表模型 (.smdl) 和报表生成器报表定义 (.rdl) 文件。</span><span class="sxs-lookup"><span data-stu-id="6c40c-103">provides predefined SharePoint content types that are used to manage shared data source (.rsds) files, report models (.smdl), and Report Builder report definition (.rdl) files.</span></span> <span data-ttu-id="6c40c-104">将 **“报表生成器报表”**、 **“报表模型”** 和 **“报表数据源”** 内容类型添加到库中将启用 **“新建”** 命令，以便创建对应类型的新文档。</span><span class="sxs-lookup"><span data-stu-id="6c40c-104">Adding a **Report Builder Report**, **Report Model**, and **Report Data Source** content type to a library enables the **New** command so that you can create new documents of that type.</span></span>  
  
 <span data-ttu-id="6c40c-105">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="6c40c-105">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>  
  
 <span data-ttu-id="6c40c-106">若要将内容类型添加到库，您必须为站点管理员或拥有“完全控制”级权限。</span><span class="sxs-lookup"><span data-stu-id="6c40c-106">To add content types to a library, you must be a site administrator or have Full Control level of permission.</span></span>  
  
 <span data-ttu-id="6c40c-107">将自动在所有文档库中为从以下“商业智能中心” [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]**站点模板类型创建的现有站点集启用** 内容类型和内容类型管理。</span><span class="sxs-lookup"><span data-stu-id="6c40c-107">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types and content type management will automatically be enabled in all document libraries for existing site collections created from the following **Business Intelligence Center** site template.</span></span>  
  
 <span data-ttu-id="6c40c-108">在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 集成之后创建的站点将不启用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 内容类型。</span><span class="sxs-lookup"><span data-stu-id="6c40c-108">Sites created after the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] integration will not have the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types enabled.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="6c40c-109">如果您 **不** 具有为某个库以前配置的内容类型，则首先启用内容类型的管理，然后启用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 内容类型。</span><span class="sxs-lookup"><span data-stu-id="6c40c-109">If you have **not** previously configured content types for a library, first enable management of content types, then enable the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types.</span></span> <span data-ttu-id="6c40c-110">请参阅在单个文档库中启用内容类型管理的过程。</span><span class="sxs-lookup"><span data-stu-id="6c40c-110">See the procedures on enabling content type management in a single document library.</span></span>  
  
 <span data-ttu-id="6c40c-111">**短视频：** [(SSRS) Enabling Content Types in SharePoint2010.wmv](http://www.youtube.com/watch?v=yqhm3DrtT1w) (http://www.youtube.com/watch?v=yqhm3DrtT1w)。</span><span class="sxs-lookup"><span data-stu-id="6c40c-111">**Short video:** [(SSRS) Enabling Content Types in SharePoint2010.wmv](http://www.youtube.com/watch?v=yqhm3DrtT1w) (http://www.youtube.com/watch?v=yqhm3DrtT1w).</span></span>  
  
 <span data-ttu-id="6c40c-112">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="6c40c-112">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="6c40c-113">在现有商业智能中心的所有文档库中启用内容类型</span><span class="sxs-lookup"><span data-stu-id="6c40c-113">Enable content types in all document libraries in an existing BI center</span></span>](#bkmk_enable_all)  
  
-   [<span data-ttu-id="6c40c-114">为单个文档库启用内容类型管理 (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="6c40c-114">To enable content type management for a single document library (SharePoint 2013)</span></span>](#bkmk_enable_content_management)  
  
-   [<span data-ttu-id="6c40c-115"> (SharePoint 2013) 添加 Reporting Services 内容类型</span><span class="sxs-lookup"><span data-stu-id="6c40c-115">To add Reporting Services content types (SharePoint 2013)</span></span>](#bkmk_add_single)  
  
-   [<span data-ttu-id="6c40c-116">为单个文档库启用内容类型管理 (SharePoint 2010)</span><span class="sxs-lookup"><span data-stu-id="6c40c-116">To enable content type management for a single document library (SharePoint 2010)</span></span>](#bkmk_enable_content_management_2010)  
  
-   [<span data-ttu-id="6c40c-117">添加报表服务器内容类型 (SharePoint 2010)</span><span class="sxs-lookup"><span data-stu-id="6c40c-117">To add report server content types (SharePoint 2010)</span></span>](#bkmk_add_single_2010)  
  
-   [<span data-ttu-id="6c40c-118">为多个 BI 站点启用内容类型和内容管理</span><span class="sxs-lookup"><span data-stu-id="6c40c-118">To enable Content types and content management for multiple BI sites</span></span>](#bkmk_enable_multiple_sites)  
  
##  <a name="enable-content-types-in-all-document-libraries-in-an-existing-bi-center"></a><a name="bkmk_enable_all"></a><span data-ttu-id="6c40c-119">在现有 BI 中心的所有文档库中启用内容类型</span><span class="sxs-lookup"><span data-stu-id="6c40c-119">Enable content types in all document libraries in an existing BI center</span></span>  
  
1.  <span data-ttu-id="6c40c-120">若要在现有 **“商业智能中心站点”** 中的所有文档库中启用内容类型和内容管理，您可以切换 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 集成功能。</span><span class="sxs-lookup"><span data-stu-id="6c40c-120">To enable the content types and content management in all document libraries in an existing **Business Intelligence Center** site, you can toggle the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] integration feature.</span></span>  
  
2.  <span data-ttu-id="6c40c-121">转到 **“站点设置”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-121">Go to **Site settings**.</span></span>  
  
    -   <span data-ttu-id="6c40c-122">在 SharePoint 2013 中，单击 **“设置”** 图标。</span><span class="sxs-lookup"><span data-stu-id="6c40c-122">In SharePoint 2013, click the **Settings** icon.</span></span> <span data-ttu-id="6c40c-123">![SharePoint 设置](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 设置")</span><span class="sxs-lookup"><span data-stu-id="6c40c-123">![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings")</span></span>  
  
    -   <span data-ttu-id="6c40c-124">在 SharePoint 2010 中，单击 **“网站操作”**，然后单击 **“网站设置”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-124">In SharePoint 2010, click **Site Actions**, then click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="6c40c-125">单击 "**网站集功能**"。</span><span class="sxs-lookup"><span data-stu-id="6c40c-125">Click **Site collection features**.</span></span>  
  
4.  <span data-ttu-id="6c40c-126">找到 **“报表服务器集成功能”** ，然后单击 **“停用”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-126">Find the **Report Server Integration Feature** and click **Deactivate**.</span></span>  
  
     <span data-ttu-id="6c40c-127">![rs_reportserver_integration_active](media/rs-reportserver-integration-active.gif "rs_reportserver_integration_active")</span><span class="sxs-lookup"><span data-stu-id="6c40c-127">![rs_reportserver_integration_active](media/rs-reportserver-integration-active.gif "rs_reportserver_integration_active")</span></span>  
  
5.  <span data-ttu-id="6c40c-128">刷新浏览器，然后为 **“报表服务器集成功能”** 单击 **“激活”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-128">Refresh the browser then click **Activate** for the **Report Server Integration Feature**.</span></span>  
  
    <span data-ttu-id="6c40c-129">![停用](media/rs-reportserver-integration-deactivate.gif "rs_reportserver_integration_deactive")</span><span class="sxs-lookup"><span data-stu-id="6c40c-129">![Deactivate](media/rs-reportserver-integration-deactivate.gif "rs_reportserver_integration_deactive")</span></span>  
  
##  <a name="to-enable-content-type-management-for-a-single-document-library-sharepoint-2013"></a><a name="bkmk_enable_content_management"></a><span data-ttu-id="6c40c-130">若要为单个文档库启用内容类型管理 (SharePoint 2013) </span><span class="sxs-lookup"><span data-stu-id="6c40c-130">To enable content type management for a single document library (SharePoint 2013)</span></span>  
  
1.  <span data-ttu-id="6c40c-131">打开要为其启用多个内容类型的库。</span><span class="sxs-lookup"><span data-stu-id="6c40c-131">Open the library for which you want to enable multiple content types.</span></span>  
  
2.  <span data-ttu-id="6c40c-132">在功能区中单击 **“库”** 。</span><span class="sxs-lookup"><span data-stu-id="6c40c-132">Click **Library** in the ribbon.</span></span>  
  
     <span data-ttu-id="6c40c-133">![rs_SharePoint2013_LibraryRibbon](media/rs-sharepoint2013-libraryribbon.gif "rs_SharePoint2013_LibraryRibbon")</span><span class="sxs-lookup"><span data-stu-id="6c40c-133">![rs_SharePoint2013_LibraryRibbon](media/rs-sharepoint2013-libraryribbon.gif "rs_SharePoint2013_LibraryRibbon")</span></span>  
  
3.  <span data-ttu-id="6c40c-134">在 **“库”** 功能区上单击 **“库设置”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-134">On the **Library** ribbon, click **Library Settings**.</span></span> <span data-ttu-id="6c40c-135">如果未看到 **“库设置”** 或按钮被禁用，则说明您无权配置库设置，包括内容类型。</span><span class="sxs-lookup"><span data-stu-id="6c40c-135">If you do not see **Library Settings** or the button is disabled, you do not have permission to configure library settings, including content types.</span></span>  
  
     <span data-ttu-id="6c40c-136">![rs_SharePoint2013_LibrarySettings](media/rs-sharepoint2013-librarysettings.gif "rs_SharePoint2013_LibrarySettings")</span><span class="sxs-lookup"><span data-stu-id="6c40c-136">![rs_SharePoint2013_LibrarySettings](media/rs-sharepoint2013-librarysettings.gif "rs_SharePoint2013_LibrarySettings")</span></span>  
  
4.  <span data-ttu-id="6c40c-137">在 **“常规设置”** 部分中，单击 **“高级设置”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-137">In the **General Settings** section, click **Advanced settings**.</span></span>  
  
     <span data-ttu-id="6c40c-138">![rs_SharePoint2013_LibrarySettings_AdvancedSettings](media/rs-sharepoint2013-librarysettings-advancedsettings.gif "rs_SharePoint2013_LibrarySettings_AdvancedSettings")</span><span class="sxs-lookup"><span data-stu-id="6c40c-138">![rs_SharePoint2013_LibrarySettings_AdvancedSettings](media/rs-sharepoint2013-librarysettings-advancedsettings.gif "rs_SharePoint2013_LibrarySettings_AdvancedSettings")</span></span>  
  
5.  <span data-ttu-id="6c40c-139">在 **“内容类型”** 部分中，选择 **“是”** 以允许内容类型管理。</span><span class="sxs-lookup"><span data-stu-id="6c40c-139">In the **Content Types** section, select **Yes** to allow management of content types.</span></span>  
  
6.  <span data-ttu-id="6c40c-140">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="6c40c-140">Click **OK**.</span></span>  
  
##  <a name="to-add-reporting-services-content-types-sharepoint-2013"></a><a name="bkmk_add_single"></a> <span data-ttu-id="6c40c-141">添加 Reporting Services 内容类型 (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="6c40c-141">To add Reporting Services content types (SharePoint 2013)</span></span>  
  
1.  <span data-ttu-id="6c40c-142">打开要添加 Reporting Services 内容类型的库。</span><span class="sxs-lookup"><span data-stu-id="6c40c-142">Open the library for which you want to add Reporting Services content types.</span></span>  
  
2.  <span data-ttu-id="6c40c-143">在功能区上，单击 **“库”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-143">On the ribbon, click **Library**.</span></span>  
  
3.  <span data-ttu-id="6c40c-144">单击 **“库设置”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-144">Click **Library Settings**.</span></span>  
  
4.  <span data-ttu-id="6c40c-145">在 **“内容类型”** 的下面，单击 **“从现有网站内容类型添加”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-145">Under **Content Types**, click **Add from existing site content types**.</span></span>  
  
5.  <span data-ttu-id="6c40c-146">在 **“从以下列表中选择网站内容类型”** 中，选择 **“SQL Server Reporting Services 内容类型”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-146">In **Select site content types from**, select **SQL Server Reporting Services Content Types**.</span></span>  
  
6.  <span data-ttu-id="6c40c-147">在 **“可用网站内容类型”** 列表中，单击 **“报表生成器”**，然后单击 **“添加”** ，将选定内容类型移到 **“要添加的内容类型”** 列表中。</span><span class="sxs-lookup"><span data-stu-id="6c40c-147">In the **Available Site Content Types** list, click **Report Builder**, and then click **Add** to move the selected content type to the **Content types to add** list.</span></span>  
  
7.  <span data-ttu-id="6c40c-148">若要添加“ **报表模型”** 和 **“报表数据源”** 内容类型，请重复执行前面的步骤。</span><span class="sxs-lookup"><span data-stu-id="6c40c-148">To add **Report Model** and **Report Data Source** content types, repeat the previous step.</span></span>  
  
8.  <span data-ttu-id="6c40c-149">添加完内容类型后，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-149">When you finish adding content types, click **OK**.</span></span>  
  
9. > [!NOTE]  
    >  <span data-ttu-id="6c40c-150">如果 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 内容类型组“SQL Server Reporting Services 内容类型”在“添加内容类型”页上不可见，则以下条件之一成立\*\*\*\*\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="6c40c-150">If the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content type group **SQL Server Reporting Services Content Types** is not visible on the **Add Content Types** page, one of the following conditions is true:</span></span>  
  
    -   <span data-ttu-id="6c40c-151">尚未安装用于 SharePoint 产品的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 外接程序。</span><span class="sxs-lookup"><span data-stu-id="6c40c-151">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in for SharePoint products has not been installed.</span></span> <span data-ttu-id="6c40c-152">有关详细信息，请参阅[安装或卸载用于 sharepoint 的 Reporting Services 外接程序 &#40;sharepoint 2010 和 sharepoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="6c40c-152">For more information, see [Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).</span></span> <span data-ttu-id="6c40c-153">本主题包括有关安装外接程序和单步执行外接程序的“仅文件”安装以解决问题的信息。</span><span class="sxs-lookup"><span data-stu-id="6c40c-153">The topic includes information on installing the add-in and stepping through a files only installation of the add-in to work around issues.</span></span>  
  
    -   <span data-ttu-id="6c40c-154">外接程序已安装，但网站集功能“报表服务器集成功能”未处于活动状态\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6c40c-154">The add-in is installed but the site collection feature **Report Server Integration Feature** is not active.</span></span> <span data-ttu-id="6c40c-155">在“站点设置” \*\*\*\* 中验证网站集功能。</span><span class="sxs-lookup"><span data-stu-id="6c40c-155">Verify the site collection feature in **Site Settings**.</span></span>  
  
    -   <span data-ttu-id="6c40c-156">所有 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 内容类型都已添加到该库中。</span><span class="sxs-lookup"><span data-stu-id="6c40c-156">All of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types have already been added to the library.</span></span> <span data-ttu-id="6c40c-157">如果所有内容类型都是某个库的一部分，则从 **“添加内容类型”** 页中删除该组。</span><span class="sxs-lookup"><span data-stu-id="6c40c-157">If all the content types are part of a library, then the group is removed from the **Add Content Types** page.</span></span> <span data-ttu-id="6c40c-158">如果您删除一个或多个 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 内容类型，则组 **“SQL Server Reporting Services 内容类型”** 将在 **“添加内容类型”** 页上可见。</span><span class="sxs-lookup"><span data-stu-id="6c40c-158">If you delete one or more of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types, then the group **SQL Server Reporting Services Content Types** will be visible on the **Add Content Types** page.</span></span>  
  
##  <a name="to-enable-content-type-management-for-a-single-document-library-sharepoint-2010"></a><a name="bkmk_enable_content_management_2010"></a><span data-ttu-id="6c40c-159">若要为单个文档库启用内容类型管理 (SharePoint 2010) </span><span class="sxs-lookup"><span data-stu-id="6c40c-159">To enable content type management for a single document library (SharePoint 2010)</span></span>  
  
1.  <span data-ttu-id="6c40c-160">打开要为其启用多个内容类型的库。</span><span class="sxs-lookup"><span data-stu-id="6c40c-160">Open the library for which you want to enable multiple content types.</span></span> <span data-ttu-id="6c40c-161">在库的菜单栏上，应能看到以下菜单项： **“新建”**、 **“上载”**、 **“操作”** 和 **“设置”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-161">On the library menu bar, you should see the following menus: **New**, **Upload**, **Actions**, and **Settings**.</span></span> <span data-ttu-id="6c40c-162">如果未看到 **“设置”**，则说明您没有添加内容类型的权限。</span><span class="sxs-lookup"><span data-stu-id="6c40c-162">If you do not see **Settings**, you do not have permission to add a content type.</span></span>  
  
2.  <span data-ttu-id="6c40c-163">在 **“库工具”** 功能区上单击 **“库”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-163">On the **Library Tools** ribbon, click **Library**.</span></span>  
  
     <span data-ttu-id="6c40c-164">![rs_SharePoint2010_LibraryRibbon](media/rs-sharepoint2010-libraryribbon.gif "rs_SharePoint2010_LibraryRibbon")</span><span class="sxs-lookup"><span data-stu-id="6c40c-164">![rs_SharePoint2010_LibraryRibbon](media/rs-sharepoint2010-libraryribbon.gif "rs_SharePoint2010_LibraryRibbon")</span></span>  
  
3.  <span data-ttu-id="6c40c-165">在 **“设置”** 功能区组中，单击 **“库设置”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-165">On the **Settings** ribbon group, click **Library Settings**.</span></span>  
  
4.  <span data-ttu-id="6c40c-166">在 **“常规设置”** 的下面，单击 **“高级设置”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-166">Under **General Settings**, click **Advanced settings**.</span></span>  
  
5.  <span data-ttu-id="6c40c-167">在 **“内容类型”** 部分中，选择 **“是”** 以允许内容类型管理。</span><span class="sxs-lookup"><span data-stu-id="6c40c-167">In the **Content Types** section, select **Yes** to allow management of content types.</span></span>  
  
6.  <span data-ttu-id="6c40c-168">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="6c40c-168">Click **OK**.</span></span>  
  
##  <a name="to-add-report-server-content-types-sharepoint-2010"></a><a name="bkmk_add_single_2010"></a> <span data-ttu-id="6c40c-169">(SharePoint 2010) 添加 Report Server 内容类型</span><span class="sxs-lookup"><span data-stu-id="6c40c-169">To add report server content types (SharePoint 2010)</span></span>  
  
1.  <span data-ttu-id="6c40c-170">打开要添加 Reporting Services 内容类型的库。</span><span class="sxs-lookup"><span data-stu-id="6c40c-170">Open the library for which you want to add Reporting Services content types.</span></span>  
  
2.  <span data-ttu-id="6c40c-171">在 **“库工具”** 功能区选项卡上，单击 **“库”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="6c40c-171">On the **Library Tools** ribbon tabs, click the **Library tab**.</span></span>  
  
3.  <span data-ttu-id="6c40c-172">在 **“设置”** 功能区组中，单击 **“库设置”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-172">On the **Settings** ribbon group, click **Library Settings**.</span></span>  
  
4.  <span data-ttu-id="6c40c-173">在 **“内容类型”** 的下面，单击 **“从现有网站内容类型添加”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-173">Under **Content Types**, click **Add from existing site content types**.</span></span>  
  
5.  <span data-ttu-id="6c40c-174">在 **“选择内容类型”** 部分的 **“从列表选择网站内容类型”** 中，单击箭头选择 **“SQL Server Reporting Services 内容类型”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-174">In the **Select Content Types** section, in **Select site content types from**, click the arrow to select **SQL Server Reporting Services Content Types**.</span></span>  
  
6.  <span data-ttu-id="6c40c-175">在 **“可用网站内容类型”** 列表中，单击 **“报表生成器”**，然后单击 **“添加”** ，将选定内容类型移到 **“要添加的内容类型”** 列表中。</span><span class="sxs-lookup"><span data-stu-id="6c40c-175">In the **Available Site Content Types** list, click **Report Builder**, and then click **Add** to move the selected content type to the **Content types to add** list.</span></span>  
  
7.  <span data-ttu-id="6c40c-176">若要添加“ **报表模型”** 和 **“报表数据源”** 内容类型，请重复执行前面的步骤。</span><span class="sxs-lookup"><span data-stu-id="6c40c-176">To add **Report Model** and **Report Data Source** content types, repeat the previous step.</span></span>  
  
8.  <span data-ttu-id="6c40c-177">添加完内容类型后，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-177">When you finish adding content types, click **OK**.</span></span>  
  
##  <a name="to-enable-content-types-and-content-management-for-multiple-bi-sites"></a><a name="bkmk_enable_multiple_sites"></a><span data-ttu-id="6c40c-178">为多个 BI 站点启用内容类型和内容管理</span><span class="sxs-lookup"><span data-stu-id="6c40c-178">To enable Content types and content management for multiple BI sites</span></span>  
  
1.  <span data-ttu-id="6c40c-179">对于 SQL Server Reporting Services 2008 和 2008 R2 报表服务器，您可以为多个商业智能中心站点启用内容类型和内容管理。</span><span class="sxs-lookup"><span data-stu-id="6c40c-179">For SQL Server Reporting Services 2008 and 2008 R2 report servers, you can enable content types and content management for multiple Business Intelligence Center sites:</span></span>  
  
2.  <span data-ttu-id="6c40c-180">在 SharePoint 管理中心中，单击 **“常规应用程序设置”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-180">In SharePoint Central Administration, click **General Applications settings**.</span></span> <span data-ttu-id="6c40c-181">在“SQL Server Reporting Services (2008 和 2008 R2)”部分中，单击“Reporting Services 集成”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6c40c-181">In the **SQL Server Reporting Services (2008 and 2008 R2)** section, click **Reporting Services Integration**.</span></span>  
  
     <span data-ttu-id="6c40c-182">![rs_general_app_settings](media/rs-general-app-settings.gif "rs_general_app_settings")</span><span class="sxs-lookup"><span data-stu-id="6c40c-182">![rs_general_app_settings](media/rs-general-app-settings.gif "rs_general_app_settings")</span></span>  
  
3.  <span data-ttu-id="6c40c-183">单击 **“激活现有网站集中的所有功能”**。</span><span class="sxs-lookup"><span data-stu-id="6c40c-183">Click **Activate feature in all exciting site collections**.</span></span>  
  
     <span data-ttu-id="6c40c-184">![rs_general_app_settings_old_integrations](media/rs-general-app-settings-old-integrations.gif "rs_general_app_settings_old_integrations")</span><span class="sxs-lookup"><span data-stu-id="6c40c-184">![rs_general_app_settings_old_integrations](media/rs-general-app-settings-old-integrations.gif "rs_general_app_settings_old_integrations")</span></span>  
  
4.  <span data-ttu-id="6c40c-185">单击“确定” 。</span><span class="sxs-lookup"><span data-stu-id="6c40c-185">Click **Ok**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c40c-186">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6c40c-186">See Also</span></span>  
 <span data-ttu-id="6c40c-187">[针对报表服务器项的 SharePoint 站点和列表权限参考](security/sharepoint-site-and-list-permission-reference-for-report-server-items.md) </span><span class="sxs-lookup"><span data-stu-id="6c40c-187">[SharePoint Site and List Permission Reference for Report Server Items](security/sharepoint-site-and-list-permission-reference-for-report-server-items.md) </span></span>  
 [<span data-ttu-id="6c40c-188">开始报表生成器 &#40;报表生成器&#41;</span><span class="sxs-lookup"><span data-stu-id="6c40c-188">Start Report Builder &#40;Report Builder&#41;</span></span>](report-builder/start-report-builder.md)  
  
  
