---
title: 创建或自定义数据馈送库 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data feed library
- data feeds [Analysis Services with SharePoint]
ms.assetid: 699fbeb9-42ab-436b-beba-214db51ea3dd
author: minewiskan
ms.author: owend
ms.openlocfilehash: b86f63c1af094ea9e8a2a1149debeac387bccbf0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689038"
---
# <a name="create-or-customize-a-data-feed-library-powerpivot-for-sharepoint"></a><span data-ttu-id="d618a-102">创建或自定义数据馈送库 (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="d618a-102">Create or Customize a Data Feed Library (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="d618a-103">*数据馈送库* 是一种特殊用途的 SharePoint 库，允许注册和共享 Atom 数据服务文档 (.atomsvc)。</span><span class="sxs-lookup"><span data-stu-id="d618a-103">A *data feed library* is a special-purpose SharePoint library that enables you to register and share Atom data service documents (.atomsvc).</span></span> <span data-ttu-id="d618a-104">这些文档向 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 工作簿或支持 Atom 数据馈送格式的其他客户端应用程序提供 XML 数据馈送。</span><span class="sxs-lookup"><span data-stu-id="d618a-104">These documents provide XML data feeds to [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] workbooks or other client applications that support the Atom data feed format.</span></span> <span data-ttu-id="d618a-105">数据馈送库与其他 SharePoint 库不同，因为它使你能够：</span><span class="sxs-lookup"><span data-stu-id="d618a-105">A data feed library is different from other SharePoint libraries because it gives you the ability to:</span></span>

-   <span data-ttu-id="d618a-106">创建或编辑“数据服务文档” \*\*，用于指定与特定馈送的 HTTP 连接。</span><span class="sxs-lookup"><span data-stu-id="d618a-106">Create or edit a *data service document*, used to specify an HTTP connection to a specific feed.</span></span>

-   <span data-ttu-id="d618a-107">在一个中心位置共享和管理数据服务文档。</span><span class="sxs-lookup"><span data-stu-id="d618a-107">Share and manage data service documents in a central location.</span></span>

-   <span data-ttu-id="d618a-108">通过图标直观地标识数据服务文档，以便你可以轻松区分同一库中存储的其他文档中的服务文档： ![GMNI_IconDataFeed](../media/gmni-icondatafeed.gif "GMNI_IconDataFeed")</span><span class="sxs-lookup"><span data-stu-id="d618a-108">Visually identify data service documents by an icon, so that you can easily distinguish service documents from other documents stored in the same library: ![GMNI_IconDataFeed](../media/gmni-icondatafeed.gif "GMNI_IconDataFeed")</span></span>

 <span data-ttu-id="d618a-109">数据馈送库始终包含数据服务文档 (.atomsvc) 文件，并且永远不会包含数据馈送本身。</span><span class="sxs-lookup"><span data-stu-id="d618a-109">A data feed library always contains data service document (.atomsvc) files, and never the data feed itself.</span></span> <span data-ttu-id="d618a-110">与由静态 XML 数据构成的数据馈送不同，数据服务文档指定根据请求生成馈送的服务或应用程序的 URL，并且为可重复的导入操作提供可重复使用的连接信息。</span><span class="sxs-lookup"><span data-stu-id="d618a-110">Unlike a data feed, which consists of static XML data, the data service document specifies a URL to a service or application that generates a feed upon request, providing reusable connection information for repeatable import operations.</span></span>

 <span data-ttu-id="d618a-111">本主题包含以下各节：</span><span class="sxs-lookup"><span data-stu-id="d618a-111">This topic contains the following sections:</span></span>

 [<span data-ttu-id="d618a-112">先决条件</span><span class="sxs-lookup"><span data-stu-id="d618a-112">Prerequisites</span></span>](#prereq)

 [<span data-ttu-id="d618a-113">创建新的数据馈送库</span><span class="sxs-lookup"><span data-stu-id="d618a-113">Create a New Data Feed Library</span></span>](#createlib)

 [<span data-ttu-id="d618a-114">向任何库添加数据馈送内容类型</span><span class="sxs-lookup"><span data-stu-id="d618a-114">Add the Data Feed Content Type to Any Library</span></span>](#addtolib)

##  <a name="prerequisites"></a><a name="prereq"></a><span data-ttu-id="d618a-115">先决条件</span><span class="sxs-lookup"><span data-stu-id="d618a-115">Prerequisites</span></span>
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] <span data-ttu-id="d618a-116">功能集成。</span><span class="sxs-lookup"><span data-stu-id="d618a-116">feature integration must be activated for the sites for which you are creating the data feed library.</span></span> <span data-ttu-id="d618a-117">如果数据源库模板类型不可用，最可能的原因就是未满足此先决条件。</span><span class="sxs-lookup"><span data-stu-id="d618a-117">If the data feed library template type is not available, the most likely cause is that this prerequisite has not been met.</span></span> <span data-ttu-id="d618a-118">有关详细信息，请参阅[在管理中心为网站集激活 PowerPivot 功能集成](activate-power-pivot-integration-for-site-collections-in-ca.md)。</span><span class="sxs-lookup"><span data-stu-id="d618a-118">For more information, see [Activate PowerPivot Feature Integration for Site Collections in Central Administration](activate-power-pivot-integration-for-site-collections-in-ca.md).</span></span>

 <span data-ttu-id="d618a-119">您必须是网站所有者才能创建该库。</span><span class="sxs-lookup"><span data-stu-id="d618a-119">You must be a site owner to create the library.</span></span>

##  <a name="create-a-new-data-feed-library"></a><a name="createlib"></a><span data-ttu-id="d618a-120">创建新的数据馈送库</span><span class="sxs-lookup"><span data-stu-id="d618a-120">Create a New Data Feed Library</span></span>
 <span data-ttu-id="d618a-121">创建数据馈送库是为 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 工作簿实现数据馈送的第一步。</span><span class="sxs-lookup"><span data-stu-id="d618a-121">Creating a data feed library is the first step to enabling data feeds for [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] workbooks.</span></span> <span data-ttu-id="d618a-122">因为数据馈送库为数据服务文档提供应用程序和管理页，所以，您必须首先具有此库后，才能创建新文档。</span><span class="sxs-lookup"><span data-stu-id="d618a-122">Because a data feed library provides application and management pages for data service documents, you must have this library in place before you can create a new document.</span></span>

 <span data-ttu-id="d618a-123">数据馈送库基于内置模板和预先配置的“数据服务文档内容类型”\*\*，该类型定义数据服务文档的属性和行为。</span><span class="sxs-lookup"><span data-stu-id="d618a-123">A data feed library is based on a built-in template and a preconfigured *data service document content type* that defines properties and behaviors for a data service document.</span></span>

1.  <span data-ttu-id="d618a-124">单击该页左上角的 **“网站操作”** 。</span><span class="sxs-lookup"><span data-stu-id="d618a-124">Click **Site Actions** at the top left corner of the page.</span></span>

2.  <span data-ttu-id="d618a-125">单击 "**更多选项**..."</span><span class="sxs-lookup"><span data-stu-id="d618a-125">Click **More Options**...</span></span>

3.  <span data-ttu-id="d618a-126">在“库”下，单击 **“数据馈送库”**。</span><span class="sxs-lookup"><span data-stu-id="d618a-126">Under Libraries, click **Data Feed Library**.</span></span>

4.  <span data-ttu-id="d618a-127">键入名称、说明、启动和版本首选项。</span><span class="sxs-lookup"><span data-stu-id="d618a-127">Type the name, description, launch, and version preferences.</span></span> <span data-ttu-id="d618a-128">包含说明性信息，以帮助用户将此库识别为用于数据服务文档的存储。</span><span class="sxs-lookup"><span data-stu-id="d618a-128">Include descriptive information to help users identify this library as storage for data service documents.</span></span>

5.  <span data-ttu-id="d618a-129">单击“创建”。</span><span class="sxs-lookup"><span data-stu-id="d618a-129">Click **Create**.</span></span>

 <span data-ttu-id="d618a-130">当前网站的导航“快速启动”窗格中将显示指向数据馈送库的链接。</span><span class="sxs-lookup"><span data-stu-id="d618a-130">A link to the data feed library will appear in the navigation Quick Launch pane for the current site.</span></span>

 <span data-ttu-id="d618a-131">创建库以后，可以使用它来创建数据服务文档。</span><span class="sxs-lookup"><span data-stu-id="d618a-131">After you create a library, you can use it to create data service documents.</span></span> <span data-ttu-id="d618a-132">有关详细信息，请参阅[使用数据馈送 &#40;PowerPivot for SharePoint&#41;](use-data-feeds-power-pivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="d618a-132">For more information, see [Use Data Feeds &#40;PowerPivot for SharePoint&#41;](use-data-feeds-power-pivot-for-sharepoint.md).</span></span>

##  <a name="add-the-data-feed-content-type-to-any-library"></a><a name="addtolib"></a><span data-ttu-id="d618a-133">向任何库添加数据馈送内容类型</span><span class="sxs-lookup"><span data-stu-id="d618a-133">Add the Data Feed Content Type to Any Library</span></span>
 <span data-ttu-id="d618a-134">如果您不想创建专用的数据馈送库，但仍想要创建和管理 SharePoint 网站中的数据服务文档，则可为将用于共享数据服务文档 (.atomsvc) 文件的任何库手动添加和配置数据服务文档内容类型。</span><span class="sxs-lookup"><span data-stu-id="d618a-134">If you do not want to create a dedicated data feed library, but you still want to create and manage data service documents from a SharePoint site, you can manually add and configure the data service document content type for any library that you will use to share data service document (.atomsvc) files.</span></span>

 <span data-ttu-id="d618a-135">您必须至少具有“管理列表”权限才能添加和配置内容类型。</span><span class="sxs-lookup"><span data-stu-id="d618a-135">You must have at least the Manage Lists permission to add and configure a content type.</span></span> <span data-ttu-id="d618a-136">此权限是“设计”权限级别和更高级别中所固有的。</span><span class="sxs-lookup"><span data-stu-id="d618a-136">This permission is built into the Design permission level and above.</span></span>

 <span data-ttu-id="d618a-137">对于要在其中创建或编辑数据馈送注册文档的每个库，都重复以下步骤。</span><span class="sxs-lookup"><span data-stu-id="d618a-137">The following steps must be repeated for each library in which you want to create or edit data feed registration documents.</span></span>

#### <a name="step-1-enable-content-type-management"></a><span data-ttu-id="d618a-138">步骤 1：启用内容类型管理</span><span class="sxs-lookup"><span data-stu-id="d618a-138">Step 1: Enable Content Type Management</span></span>

1.  <span data-ttu-id="d618a-139">打开要为其启用多种内容类型的文档库。</span><span class="sxs-lookup"><span data-stu-id="d618a-139">Open the document library for which you want to enable multiple content types.</span></span>

2.  <span data-ttu-id="d618a-140">在 SharePoint 功能区的“库工具”中，单击 **“库”**。</span><span class="sxs-lookup"><span data-stu-id="d618a-140">On the SharePoint ribbon, in Library Tools, click **Library**.</span></span>

3.  <span data-ttu-id="d618a-141">单击“设置”。</span><span class="sxs-lookup"><span data-stu-id="d618a-141">Click **Settings**.</span></span>

4.  <span data-ttu-id="d618a-142">单击 **“库设置”**。</span><span class="sxs-lookup"><span data-stu-id="d618a-142">Click **Library Settings**.</span></span>

5.  <span data-ttu-id="d618a-143">在“常规设置”中，单击 **“高级设置”**。</span><span class="sxs-lookup"><span data-stu-id="d618a-143">In General Settings, click **Advanced settings**.</span></span>

6.  <span data-ttu-id="d618a-144">在“内容类型”的“允许内容类型的管理?”部分中，</span><span class="sxs-lookup"><span data-stu-id="d618a-144">In Content Types, in the "Allow management of content types?"</span></span> <span data-ttu-id="d618a-145">单击 **“是”**。</span><span class="sxs-lookup"><span data-stu-id="d618a-145">section, click **Yes**.</span></span>

7.  <span data-ttu-id="d618a-146">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="d618a-146">Click **OK**.</span></span>

#### <a name="step-2-add-the-data-service-document-content-type"></a><span data-ttu-id="d618a-147">步骤 2：添加数据服务文档内容类型</span><span class="sxs-lookup"><span data-stu-id="d618a-147">Step 2: Add the Data Service Document Content Type</span></span>

1.  <span data-ttu-id="d618a-148">在“内容类型”部分中，单击 **“从现有网站内容类型添加”**。</span><span class="sxs-lookup"><span data-stu-id="d618a-148">In the Content Types section, click **Add from existing site content types**.</span></span> <span data-ttu-id="d618a-149">如果您看不到此页，则返回网站，在“库工具”中单击 **“库”** ，然后单击 **“库设置”**。</span><span class="sxs-lookup"><span data-stu-id="d618a-149">If you do not see this page, go back to the site, click **Library** in Library Tools, and then click **Library Settings**.</span></span>

2.  <span data-ttu-id="d618a-150">在“内容类型”中，单击 **“从现有网站内容类型添加”**。</span><span class="sxs-lookup"><span data-stu-id="d618a-150">In Content Types, click **Add from existing site content types**.</span></span>

3.  <span data-ttu-id="d618a-151">在“从以下列表中选择网站内容类型:”中，选择 **“商业智能”**。</span><span class="sxs-lookup"><span data-stu-id="d618a-151">In Select site content types from:, select **Business Intelligence**.</span></span>

4.  <span data-ttu-id="d618a-152">在“可用网站内容类型”中，单击 **“数据服务文档”**，然后单击 **“添加”** 将所选内容类型移至“要添加的内容类型”列表中。</span><span class="sxs-lookup"><span data-stu-id="d618a-152">In Available Site Content Types, click **Data Service Document**, and then click **Add** to move the selected content type to the Content types to add list.</span></span>

5.  <span data-ttu-id="d618a-153">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="d618a-153">Click **OK**.</span></span>

#### <a name="step-3-verify-data-service-document-configuration"></a><span data-ttu-id="d618a-154">步骤 3：验证数据服务文档配置</span><span class="sxs-lookup"><span data-stu-id="d618a-154">Step 3: Verify Data Service Document Configuration</span></span>

1.  <span data-ttu-id="d618a-155">打开网站主页。</span><span class="sxs-lookup"><span data-stu-id="d618a-155">Open the site home page.</span></span>

2.  <span data-ttu-id="d618a-156">打开库。</span><span class="sxs-lookup"><span data-stu-id="d618a-156">Open the library.</span></span>

3.  <span data-ttu-id="d618a-157">在 SharePoint 功能区上，单击 **“文档”**。</span><span class="sxs-lookup"><span data-stu-id="d618a-157">On the SharePoint ribbon, click **Documents**.</span></span>

4.  <span data-ttu-id="d618a-158">在“新建文档”上单击向下箭头，然后选择 **“数据服务文档”**。</span><span class="sxs-lookup"><span data-stu-id="d618a-158">Click the down arrow on New Document, and select **Data Service Document**.</span></span> <span data-ttu-id="d618a-159">此时应该显示“新建数据服务文档”页。</span><span class="sxs-lookup"><span data-stu-id="d618a-159">The New Data Service Document page should appear.</span></span>

## <a name="see-also"></a><span data-ttu-id="d618a-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d618a-160">See Also</span></span>
 <span data-ttu-id="d618a-161">[使用数据馈送 &#40;PowerPivot for SharePoint&#41;](use-data-feeds-power-pivot-for-sharepoint.md)在管理中心[powerpivot 数据馈送](power-pivot-data-feeds.md)中[删除 Powerpivot 数据馈送库](delete-a-power-pivot-data-feed-library.md) [powerpivot 服务器管理和配置](power-pivot-server-administration-and-configuration-in-central-administration.md)</span><span class="sxs-lookup"><span data-stu-id="d618a-161">[Use Data Feeds &#40;PowerPivot for SharePoint&#41;](use-data-feeds-power-pivot-for-sharepoint.md) [Delete a PowerPivot Data Feed Library](delete-a-power-pivot-data-feed-library.md) [PowerPivot Server Administration and Configuration in Central Administration](power-pivot-server-administration-and-configuration-in-central-administration.md) [PowerPivot Data Feeds](power-pivot-data-feeds.md)</span></span>


