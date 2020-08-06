---
title: " (PowerPivot for SharePoint) 配置最大文件上传大小 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ac516c63-1e79-4ae8-bca6-32d3c1a09c00
author: minewiskan
ms.author: owend
ms.openlocfilehash: 34a0adb2f22915289cccfa1f21c51038263acca0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682399"
---
# <a name="configure-maximum-file-upload-size-powerpivot-for-sharepoint"></a><span data-ttu-id="6f0c7-102">配置最大文件上载大小 (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="6f0c7-102">Configure Maximum File Upload Size (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="6f0c7-103">PowerPivot 工作簿常常包含大量的数据，导致文件超出为 SharePoint 上载所允许的最大文件大小。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-103">PowerPivot workbooks often contain large amounts of data that result in files that exceed the maximum file size allowed for SharePoint uploads.</span></span> <span data-ttu-id="6f0c7-104">尝试上载超过该上限的文件时，SharePoint 会显示以下错误：</span><span class="sxs-lookup"><span data-stu-id="6f0c7-104">When you try to upload a file that exceeds the upper limit, you will get the following error on SharePoint:</span></span>  
  
-   <span data-ttu-id="6f0c7-105">“指定的文件超过受支持的最大文件大小。”</span><span class="sxs-lookup"><span data-stu-id="6f0c7-105">"The specified file is larger than the maximum supported file size."</span></span>  
  
 <span data-ttu-id="6f0c7-106">若要增加文件大小，可从将针对 Excel Services 的“工作簿最大大小”调整到 50 MB 开始。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-106">To increase the file size, start by adjusting the Maximum Workbook Size for Excel Services to 50 megabytes.</span></span> <span data-ttu-id="6f0c7-107">这会将针对 Excel 的最大文件大小限制调整为针对 SharePoint Web 应用程序的最大文件大小限制（SharePoint 2010 中的默认设置为 50 MB，SharePoint 2013 中为 200 MB）。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-107">This aligns the maximum file size limits for Excel to those of SharePoint web applications (set to 50 megabytes by default in SharePoint 2010 and 200 in SharePoint 2013).</span></span> <span data-ttu-id="6f0c7-108">如果您的文件超过 50 MB 的大小限制，则应同时增加针对 Excel Services 和您的 Web 应用程序的文件大小限制。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-108">If your files exceed 50 megabytes in size, increase the file size limits for both Excel Services and your web application.</span></span>  
  
 <span data-ttu-id="6f0c7-109">您必须是 SharePoint 管理员才能更改最大文件上载大小。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-109">You must be a SharePoint administrator to change the maximum file upload size.</span></span>  
  
### <a name="configure-maximum-file-size-for-excel-services"></a><span data-ttu-id="6f0c7-110">配置针对 Excel Services 的最大文件大小</span><span class="sxs-lookup"><span data-stu-id="6f0c7-110">Configure maximum file size for Excel Services</span></span>  
  
1.  <span data-ttu-id="6f0c7-111">在“管理中心”的“应用程序管理”中，单击 **“管理服务应用程序”** 。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-111">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="6f0c7-112">单击 Excel Services 应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-112">Click the name of your Excel Services Application.</span></span>  
  
3.  <span data-ttu-id="6f0c7-113">单击 **“受信任文件位置”**。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-113">Click **Trusted File Locations**.</span></span>  
  
4.  <span data-ttu-id="6f0c7-114">单击该位置以编辑属性。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-114">Click the location to edit the properties.</span></span> <span data-ttu-id="6f0c7-115">默认情况下，Excel Services 将默认 Web 应用程序视作可信站点。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-115">By default, Excel Services considers the default web application a trusted site.</span></span> <span data-ttu-id="6f0c7-116">如果你在使用默认 Web 应用程序，则单击 **http://** 以便打开针对此位置的配置页。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-116">If you are using the default web application, click **http://** to open the configuration page for this location.</span></span>  
  
5.  <span data-ttu-id="6f0c7-117">滚动到 **“工作簿属性”**。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-117">Scroll to **Workbook Properties**.</span></span>  
  
6.  <span data-ttu-id="6f0c7-118">在“工作簿最大大小”中，将文件大小从 10（默认值）增加到 50 或者适合您在使用的文件的更大大小。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-118">In Maximum Workbook Size, increase the file size from 10 (the default value) to 50 or a larger size that accommodates the files you are working with.</span></span>  
  
     <span data-ttu-id="6f0c7-119">默认情况下，50 MB 是针对 SharePoint Web 应用程序的最大文件上载大小。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-119">By default, 50 megabytes is the maximum file upload size for SharePoint web applications.</span></span> <span data-ttu-id="6f0c7-120">如果您将“工作簿最大大小”设置为大于 50 MB 的数值，则应执行下面过程中的步骤以便将针对 SharePoint Web 应用程序的“最大上载大小”增加到相同值。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-120">If you set Maximum Workbook Size to a number larger than 50 megabytes, follow the steps in the next procedure to increase the Maximum Upload Size for your SharePoint web application to the same value.</span></span>  
  
     <span data-ttu-id="6f0c7-121">您可以指定的最大值是 2 GB（或“管理中心”中指定的 2047 MB）。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-121">The maximum value that you can specify is 2 gigabytes (or 2047 megabytes as specified in Central Administration).</span></span>  
  
7.  <span data-ttu-id="6f0c7-122">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-122">Click **OK**.</span></span>  
  
### <a name="configure-maximum-file-size-for-a-sharepoint-web-application"></a><span data-ttu-id="6f0c7-123">为 SharePoint Web 应用程序配置最大文件大小</span><span class="sxs-lookup"><span data-stu-id="6f0c7-123">Configure maximum file size for a SharePoint web application</span></span>  
  
1.  <span data-ttu-id="6f0c7-124">在管理中心的 "应用程序管理" 中，单击 "**管理 web 应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-124">In Central Administration, in Application Management, click **Manage web applications**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f0c7-125">仅当在 Excel Services 中增加过“工作簿最大大小”时，才执行以下步骤。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-125">Perform the following steps only if you increased the Maximum Workbook Size in Excel Services.</span></span>  
  
2.  <span data-ttu-id="6f0c7-126">选择应用程序（例如 **SharePoint - 80**）。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-126">Select the application (for example, **SharePoint - 80**).</span></span>  
  
3.  <span data-ttu-id="6f0c7-127">在“Web 应用程序”功能区上，单击“常规设置”按钮上的向下箭头。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-127">On the Web Applications ribbon, click the down arrow on the General Settings button.</span></span>  
  
4.  <span data-ttu-id="6f0c7-128">单击 **“常规设置”**。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-128">Click **General Settings**.</span></span>  
  
5.  <span data-ttu-id="6f0c7-129">滚动到 **“最大上载大小”**。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-129">Scroll to **Maximum Upload Size**.</span></span>  
  
6.  <span data-ttu-id="6f0c7-130">将该属性设置为与 Excel Services 中的“工作簿最大大小”相同或更大的数值。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-130">Set the property to the same number, or larger as the Maximum Workbook Size in Excel Services.</span></span>  
  
7.  <span data-ttu-id="6f0c7-131">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="6f0c7-131">Click **OK**.</span></span>  
  
  
