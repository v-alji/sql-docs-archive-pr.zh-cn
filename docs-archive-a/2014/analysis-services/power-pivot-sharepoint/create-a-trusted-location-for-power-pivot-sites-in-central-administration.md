---
title: 在管理中心中为 PowerPivot 站点创建受信任位置 |Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a666f365-cd93-43a3-9d3d-e429dfc19b66
author: minewiskan
ms.author: owend
ms.openlocfilehash: 70b1317db7ce413f3a593056f3b8a140b3bdc446
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589271"
---
# <a name="create-a-trusted-location-for-powerpivot-sites-in-central-administration"></a><span data-ttu-id="327d5-102">Create a trusted location for PowerPivot sites in Central Administration</span><span class="sxs-lookup"><span data-stu-id="327d5-102">Create a trusted location for PowerPivot sites in Central Administration</span></span>
  <span data-ttu-id="327d5-103">通过 Excel Services，您可以指定哪些位置是您在 SharePoint 服务器上打开的工作簿的有效存储库。</span><span class="sxs-lookup"><span data-stu-id="327d5-103">Excel Services lets you specify which locations are valid repositories for workbooks that you open on a SharePoint server.</span></span> <span data-ttu-id="327d5-104">这些位置称为“受信任位置”，您可以对您创建的每个受信任位置使用不同的配置设置。</span><span class="sxs-lookup"><span data-stu-id="327d5-104">These locations are called 'trusted locations', and you can use different configuration settings for each trusted location you create.</span></span> <span data-ttu-id="327d5-105">对于部署 PowerPivot for SharePoint 而言，您可以考虑为包含 PowerPivot 工作簿的站点创建一个受信任位置，以便您可以应用最适合进行 PowerPivot 数据访问的设置，同时为场的剩余部分保留默认设置。</span><span class="sxs-lookup"><span data-stu-id="327d5-105">For a deployment of PowerPivot for SharePoint, you might consider creating a trusted location for sites that contain PowerPivot workbooks so that you can apply the settings that work best for PowerPivot data access, while preserving default settings for the rest of the farm.</span></span>  
  
  
  
## <a name="prerequisites"></a><span data-ttu-id="327d5-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="327d5-106">Prerequisites</span></span>  
 <span data-ttu-id="327d5-107">您必须是场或服务管理员才能将某一 URL 指定为受信任位置。</span><span class="sxs-lookup"><span data-stu-id="327d5-107">You must be a farm or service administrator to designate a URL as a trusted location.</span></span>  
  
 <span data-ttu-id="327d5-108">您必须知道包含 PowerPivot 库或用于存储工作簿的其他库的 SharePoint 站点的 URL 地址。</span><span class="sxs-lookup"><span data-stu-id="327d5-108">You must know the URL address of the SharePoint site that contains the PowerPivot Gallery or other library that stores your workbooks.</span></span> <span data-ttu-id="327d5-109">若要获取该地址，请打开包含库的站点，右键单击**PowerPivot 库**，选择 "**属性**"，然后复制包含服务器名称和站点路径的地址 (URL) 的第一部分。</span><span class="sxs-lookup"><span data-stu-id="327d5-109">To get the address, open the site that contains the library, right-click **PowerPivot Gallery**, select **Properties**, and then copy the first part of the Address (URL) that contains the server name and site path.</span></span>  
  
##  <a name="overview"></a><a name="overview"></a> <span data-ttu-id="327d5-110">概述</span><span class="sxs-lookup"><span data-stu-id="327d5-110">Overview</span></span>  
 <span data-ttu-id="327d5-111">初次安装 Excel Services 时会将“http://”指定为其受信任位置，这意味着可以在服务器上打开场中任何站点上的工作簿。</span><span class="sxs-lookup"><span data-stu-id="327d5-111">An initial installation of Excel Services specifies 'http://' as its trusted location, which means that workbooks from any site in the farm can be opened on the server.</span></span> <span data-ttu-id="327d5-112">如果您需要更紧密地控制哪些位置被视为可信的，则可以创建新的受信任位置（这些位置映射到场中的特定站点），然后，改变每个位置的设置和权限。</span><span class="sxs-lookup"><span data-stu-id="327d5-112">If you require tighter control over which locations are considered trustworthy, you can create new trusted locations that map to specific sites in your farm, and then vary the settings and permissions for each one.</span></span>  
  
 <span data-ttu-id="327d5-113">如果对于场的其余部分您想要保留默认值，同时应用最适合进行 PowerPivot 数据访问的其他设置，则为承载 PowerPivot 工作簿的站点创建新的受信任位置尤其有用。</span><span class="sxs-lookup"><span data-stu-id="327d5-113">Creating a new trusted location for sites that host PowerPivot workbooks is especially useful if you want to preserve default values for the rest of the farm, while applying different settings that work best for PowerPivot data access.</span></span> <span data-ttu-id="327d5-114">例如，针对 PowerPivot 工作簿进行优化的受信任位置可能具有的最大工作簿大小为 50 MB，而场的其他部分使用默认值 10MB。</span><span class="sxs-lookup"><span data-stu-id="327d5-114">For example, a trusted location that is optimized for PowerPivot workbooks could have a maximum workbook size of 50 MB, while the rest of the farm uses the default value of 10MB.</span></span>  
  
 <span data-ttu-id="327d5-115">如果您正在使用 PowerPivot 库来预览已发布工作簿，并且遇到数据刷新警告而不是所期望的预览图像，则建议创建受信任位置。</span><span class="sxs-lookup"><span data-stu-id="327d5-115">Creating a trusted location is recommended if you are using PowerPivot Gallery libraries to preview published workbooks and you encounter data refresh warnings instead of the preview image you expect.</span></span> <span data-ttu-id="327d5-116">PowerPivot 库使用文档内的数据和展示信息呈现报表和工作簿的缩略图。</span><span class="sxs-lookup"><span data-stu-id="327d5-116">PowerPivot Gallery renders thumbnail images of reports and workbooks using data and presentation information within the document.</span></span> <span data-ttu-id="327d5-117">如果为受信任位置启用了“数据刷新时警告”，则 PowerPivot 库可能没有足够的权限来执行刷新，这会导致出现错误，而不是显示缩略图。</span><span class="sxs-lookup"><span data-stu-id="327d5-117">If Warn on Data Refresh is enabled for a trusted location, PowerPivot Gallery might not have sufficient permissions to perform the refresh, causing an error to appear instead of the thumbnail image.</span></span> <span data-ttu-id="327d5-118">将包含 PowerPivot 库的站点添加为新的受信任位置可以消除此问题。</span><span class="sxs-lookup"><span data-stu-id="327d5-118">Adding a site that contains PowerPivot Gallery as a new trusted location can eliminate this problem.</span></span>  
  
##  <a name="create-a-trusted-location-for-powerpivot-data-access"></a><a name="create"></a><span data-ttu-id="327d5-119">为 PowerPivot 数据访问创建受信任位置</span><span class="sxs-lookup"><span data-stu-id="327d5-119">Create a Trusted Location for PowerPivot Data Access</span></span>  
  
1.  <span data-ttu-id="327d5-120">在“管理中心”的“应用程序管理”中，单击 **“管理服务应用程序”** 。</span><span class="sxs-lookup"><span data-stu-id="327d5-120">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="327d5-121">单击“Excel Services 服务应用程序”。</span><span class="sxs-lookup"><span data-stu-id="327d5-121">Click the Excel Services Service Application.</span></span>  
  
3.  <span data-ttu-id="327d5-122">单击 **“受信任文件位置”**。</span><span class="sxs-lookup"><span data-stu-id="327d5-122">Click **Trusted File Locations**.</span></span>  
  
4.  <span data-ttu-id="327d5-123">单击 **“添加受信任文件位置”**。</span><span class="sxs-lookup"><span data-stu-id="327d5-123">Click **Add Trusted File Location**.</span></span>  
  
5.  <span data-ttu-id="327d5-124">输入包含 PowerPivot 库的站点的 URL。</span><span class="sxs-lookup"><span data-stu-id="327d5-124">Enter the URL of a site that contains a PowerPivot Gallery library.</span></span>  
  
6.  <span data-ttu-id="327d5-125">在“位置类型”中，选择 **Microsoft SharePoint Foundation**。</span><span class="sxs-lookup"><span data-stu-id="327d5-125">In Location Type, select **Microsoft SharePoint Foundation**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="327d5-126">PowerPivot 数据访问不支持 UNC 和 HTTP 位置类型。</span><span class="sxs-lookup"><span data-stu-id="327d5-126">UNC and HTTP location types are not supported for PowerPivot data access.</span></span>  
  
7.  <span data-ttu-id="327d5-127">接受“会话管理”、“工作簿属性”和“计算行为”中的所有默认属性设置。</span><span class="sxs-lookup"><span data-stu-id="327d5-127">Accept all of the default settings for properties in Session Management, Workbook Properties, and Calculation Behavior.</span></span>  
  
8.  <span data-ttu-id="327d5-128">在“工作簿属性”中，将 **“工作簿最大大小”** 设置为 **50**。</span><span class="sxs-lookup"><span data-stu-id="327d5-128">In Workbook Properties, set **Maximum Workbook Size** to **50**.</span></span> <span data-ttu-id="327d5-129">这会将工作簿文件大小的上限调整到用于文件上载到父 Web 应用程序的上限。</span><span class="sxs-lookup"><span data-stu-id="327d5-129">This aligns the upper limit for workbook file size to the upper limit for file uploads to the parent web application.</span></span> <span data-ttu-id="327d5-130">如果您的工作簿大小超过 50 MB，则必须进一步增加该文件大小限制。</span><span class="sxs-lookup"><span data-stu-id="327d5-130">If your workbooks are larger than 50 megabytes, you must further increase the file size limit.</span></span> <span data-ttu-id="327d5-131">有关详细信息，请参阅[&#40;PowerPivot for SharePoint&#41;配置最大文件上传大小](configure-maximum-file-upload-size-power-pivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="327d5-131">For more information, see [Configure Maximum File Upload Size &#40;PowerPivot for SharePoint&#41;](configure-maximum-file-upload-size-power-pivot-for-sharepoint.md).</span></span>  
  
9. <span data-ttu-id="327d5-132">在“外部数据”中，确认“允许外部数据”设置为 **“受信任的数据连接库和嵌入连接”**。</span><span class="sxs-lookup"><span data-stu-id="327d5-132">In External Data, verify that Allow External Data is set to **Trusted data connection libraries and embedded**.</span></span> <span data-ttu-id="327d5-133">此设置是工作簿中 PowerPivot 数据访问所必需的。</span><span class="sxs-lookup"><span data-stu-id="327d5-133">This setting is required for PowerPivot data access in a workbook.</span></span>  
  
10. <span data-ttu-id="327d5-134">还在“外部数据”中，对于“刷新时警告”，取消选中 **“启用刷新警告”** 的复选框。</span><span class="sxs-lookup"><span data-stu-id="327d5-134">Also in External Data, for Warn on Refresh, clear the checkbox for **Refresh warning enabled**.</span></span> <span data-ttu-id="327d5-135">取消选中该复选框将允许 PowerPivot 库跳过例行的警告消息，而显示工作簿的预览图像。</span><span class="sxs-lookup"><span data-stu-id="327d5-135">Clearing the checkbox allows PowerPivot Gallery to bypass routine warning messages and show preview images of a workbook instead.</span></span>  
  
11. <span data-ttu-id="327d5-136">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="327d5-136">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="327d5-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="327d5-137">See Also</span></span>  
 [<span data-ttu-id="327d5-138">PowerPivot 库</span><span class="sxs-lookup"><span data-stu-id="327d5-138">PowerPivot Gallery</span></span>](../../index.yml)  
 <span data-ttu-id="327d5-139">[创建和自定义 PowerPivot 库](create-and-customize-power-pivot-gallery.md) </span><span class="sxs-lookup"><span data-stu-id="327d5-139">[Create and Customize PowerPivot Gallery](create-and-customize-power-pivot-gallery.md) </span></span>  
 [<span data-ttu-id="327d5-140">使用 PowerPivot 库</span><span class="sxs-lookup"><span data-stu-id="327d5-140">Use PowerPivot Gallery</span></span>](use-power-pivot-gallery.md)  
  
  
