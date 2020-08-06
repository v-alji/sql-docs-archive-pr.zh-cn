---
title: 在 SharePoint 中激活报表服务器和 Power View 集成功能 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c7f64a54-c555-4d31-bf99-3abe57dc8626
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af5f544e959c039b0bdb85d63d0b94917254d78a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590082"
---
# <a name="activate-the-report-server-and-power-view-integration-features-in-sharepoint"></a><span data-ttu-id="7db9c-102">在 SharePoint 中激活报表服务器和 Power View 集成功能</span><span class="sxs-lookup"><span data-stu-id="7db9c-102">Activate the Report Server and Power View Integration Features in SharePoint</span></span>
  <span data-ttu-id="7db9c-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]默认情况下，在安装 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] 用于 SharePoint 产品的外接程序后，通常会激活网站集功能。</span><span class="sxs-lookup"><span data-stu-id="7db9c-103">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] site collection features are usually activated by default after you install the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] Add-in for SharePoint products.</span></span> <span data-ttu-id="7db9c-104">在某些情况下，您将需要手动激活这些功能。</span><span class="sxs-lookup"><span data-stu-id="7db9c-104">In some situations you will need to manually activate the features.</span></span>  
  
 <span data-ttu-id="7db9c-105">如果在安装 SharePoint 产品后安装了用于 SharePoint 2010 产品的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 外接程序，则仅对根网站集激活报表服务器集成功能和 Power View 集成功能。</span><span class="sxs-lookup"><span data-stu-id="7db9c-105">If you install the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in for SharePoint 2010 Products after the installation of the SharePoint product, then the Report Server integration feature and the Power View integration feature will only be activated for root site collections.</span></span> <span data-ttu-id="7db9c-106">对于其他网站集，您将需要手动激活这些功能。</span><span class="sxs-lookup"><span data-stu-id="7db9c-106">For other site collections, you will need to manually activate the features.</span></span> <span data-ttu-id="7db9c-107">例如，如果具有 **http://[我的服务器名称]/sites/[网站集名称]** 的网站集，将需要手动激活 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 网站集功能。</span><span class="sxs-lookup"><span data-stu-id="7db9c-107">For example if you have a site collection of **http://[my server name]/sites/[site collection name]** you will need to manually activate the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] site collection features.</span></span>  
  
 <span data-ttu-id="7db9c-108">没有根网站集时， [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 外接程序将记录一条类似于以下内容的消息：</span><span class="sxs-lookup"><span data-stu-id="7db9c-108">When there is no root site collection, the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in will log a message similar to the following.</span></span>  
  
 <span data-ttu-id="7db9c-109">“SharePoint Web 应用程序 80 没有根网站集”</span><span class="sxs-lookup"><span data-stu-id="7db9c-109">"SharePoint web app 80 does not have root site collection"</span></span>  
  
 <span data-ttu-id="7db9c-110">该消息将在外接程序安装日志中找到，名为 "RS_SP_ # .log"，其中 # 为递增数字。</span><span class="sxs-lookup"><span data-stu-id="7db9c-110">The message will be found in the add-in installation log, named "RS_SP_#.log" where # is an incrementing number.</span></span> <span data-ttu-id="7db9c-111">日志文件将在当前用户的临时文件夹中找到，例如 C:\Users \\ [用户名] \appdata\local\temp。有关外接程序日志记录选项的详细信息，请参阅[安装或卸载用于 sharepoint 的 Reporting Services 外接程序 &#40;sharepoint 2010 和 sharepoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="7db9c-111">The log file will be found in the current users Temp folder, for example C:\Users\\[user name]\AppData\Local\Temp. For more information on logging options with the add-in, see [Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).</span></span>  
  
 <span data-ttu-id="7db9c-112">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="7db9c-112">In this topic:</span></span>  
  
-   [<span data-ttu-id="7db9c-113">若要激活报表服务器和 Power View 集成网站集功能：</span><span class="sxs-lookup"><span data-stu-id="7db9c-113">To Activate the Report Server and Power View Integration Site Collection Features:</span></span>](#bkmk_features)  
  
-   [<span data-ttu-id="7db9c-114">激活或停用 Reporting Services 管理中心网站集功能：</span><span class="sxs-lookup"><span data-stu-id="7db9c-114">To Activate or Deactivate Reporting Services Central Administration Site Collection Feature:</span></span>](#bkmk_centraladmin)  
  
##  <a name="to-activate-the-report-server-and-power-view-integration-site-collection-features"></a><a name="bkmk_features"></a><span data-ttu-id="7db9c-115">若要激活报表服务器并 Power View 集成网站集功能：</span><span class="sxs-lookup"><span data-stu-id="7db9c-115">To Activate the Report Server and Power View Integration Site Collection Features:</span></span>  
  
1.  <span data-ttu-id="7db9c-116">打开浏览器，找到要激活 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能的网站。</span><span class="sxs-lookup"><span data-stu-id="7db9c-116">Open your browser to the site where you want the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features active.</span></span>  
  
2.  <span data-ttu-id="7db9c-117">单击 **“网站操作”** 。</span><span class="sxs-lookup"><span data-stu-id="7db9c-117">Click **Site Actions**.</span></span>  
  
3.  <span data-ttu-id="7db9c-118">单击 **“网站设置”** 。</span><span class="sxs-lookup"><span data-stu-id="7db9c-118">Click **Site Settings**.</span></span>  
  
4.  <span data-ttu-id="7db9c-119">在网站集管理组中单击 **“网站集功能”** 。</span><span class="sxs-lookup"><span data-stu-id="7db9c-119">Click **Site Collection Features** in the Site Collection Administration Group.</span></span>  
  
5.  <span data-ttu-id="7db9c-120">在列表中找到 **“报表服务器集成功能”** 或 **“Power View 集成功能”** 。</span><span class="sxs-lookup"><span data-stu-id="7db9c-120">Find **Report Server Integration Feature** or **Power View Integration Feature** in the list.</span></span>  
  
6.  <span data-ttu-id="7db9c-121">单击“激活”  。</span><span class="sxs-lookup"><span data-stu-id="7db9c-121">Click **Activate**.</span></span>  
  
 <span data-ttu-id="7db9c-122">若要停用这些功能，您可以使用相同的过程，但单击 **“停用”** 而非 **“激活”**。</span><span class="sxs-lookup"><span data-stu-id="7db9c-122">To deactivate the features, you can use the same procedure, but click **Deactivate** rather than **Activate.**</span></span>  
  
##  <a name="to-activate-or-deactivate-reporting-services-central-administration-site-collection-feature"></a><a name="bkmk_centraladmin"></a> <span data-ttu-id="7db9c-123">若要激活或停用 Reporting Services 管理中心网站集功能：</span><span class="sxs-lookup"><span data-stu-id="7db9c-123">To Activate or Deactivate Reporting Services Central Administration Site Collection Feature:</span></span>  
  
1.  <span data-ttu-id="7db9c-124">打开浏览器找到 SharePoint 管理中心。</span><span class="sxs-lookup"><span data-stu-id="7db9c-124">Open your browser to SharePoint Central Administration.</span></span>  
  
2.  <span data-ttu-id="7db9c-125">单击 **“网站操作”** 。</span><span class="sxs-lookup"><span data-stu-id="7db9c-125">Click **Site Actions**.</span></span>  
  
3.  <span data-ttu-id="7db9c-126">单击 **“网站设置”** 。</span><span class="sxs-lookup"><span data-stu-id="7db9c-126">Click **Site Settings**.</span></span>  
  
4.  <span data-ttu-id="7db9c-127">在网站集管理组中单击 **“网站集功能”** 。</span><span class="sxs-lookup"><span data-stu-id="7db9c-127">Click **Site Collection Features** in the Site Collection Administration Group.</span></span>  
  
5.  <span data-ttu-id="7db9c-128">在列表中找到 **“报表服务器管理中心功能”** 。</span><span class="sxs-lookup"><span data-stu-id="7db9c-128">Find **Report Server Central Administration Feature** in the list.</span></span>  
  
6.  <span data-ttu-id="7db9c-129">单击“激活”  。</span><span class="sxs-lookup"><span data-stu-id="7db9c-129">Click **Activate**.</span></span>  
  
 <span data-ttu-id="7db9c-130">若要停用这些功能，您可以使用相同的过程，但单击 **“停用”** 而非 **“激活”**。</span><span class="sxs-lookup"><span data-stu-id="7db9c-130">To deactivate the feature, you can use the same procedure, but click **Deactivate** rather than **Activate.**</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7db9c-131">后续步骤</span><span class="sxs-lookup"><span data-stu-id="7db9c-131">Next Steps</span></span>  
 <span data-ttu-id="7db9c-132">激活此功能后，可以继续进行服务器集成。</span><span class="sxs-lookup"><span data-stu-id="7db9c-132">After the feature is activated, you can continue with server integration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7db9c-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7db9c-133">See Also</span></span>  
 [<span data-ttu-id="7db9c-134">安装或卸载用于 SharePoint 的 Reporting Services 外接程序 &#40;SharePoint 2010 和 SharePoint 2013&#41;</span><span class="sxs-lookup"><span data-stu-id="7db9c-134">Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
