---
title: 在管理中心中为网站集激活 PowerPivot 功能集成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 62a27e53-446a-42d7-b5db-c009e02d4904
author: minewiskan
ms.author: owend
ms.openlocfilehash: b565434cba197d04327e833d4ac6eab3caf96646
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689037"
---
# <a name="activate-powerpivot-feature-integration-for-site-collections-in-central-administration"></a><span data-ttu-id="fae40-102">在管理中心中针对网站集激活 PowerPivot 功能集成</span><span class="sxs-lookup"><span data-stu-id="fae40-102">Activate PowerPivot Feature Integration for Site Collections in Central Administration</span></span>
  <span data-ttu-id="fae40-103">如果您使用了“现有场”安装选项来安装 SQL Server PowerPivot for SharePoint，则需要为特定的网站集激活 PowerPivot 功能集成。</span><span class="sxs-lookup"><span data-stu-id="fae40-103">Activating PowerPivot feature integration for specific site collections is required if you used the Existing Farm installation option to install SQL Server PowerPivot for SharePoint.</span></span> <span data-ttu-id="fae40-104">如果您使用“新服务器”选项安装 PowerPivot for SharePoint，则可以跳过此任务，因为 SQL Server 安装程序在配置您的部署时已经为根网站集激活了 PowerPivot 功能集成。</span><span class="sxs-lookup"><span data-stu-id="fae40-104">If you installed PowerPivot for SharePoint using the New Server option, you can skip this task because SQL Server Setup already activated PowerPivot feature integration for the root site collection when it configured your deployment.</span></span>  
  
 <span data-ttu-id="fae40-105">网站集级别的功能激活是使应用程序页和模板对您的站点可用所必需的，包括用于计划的数据刷新的配置页以及用于 PowerPivot 库和数据馈送库的应用程序页。</span><span class="sxs-lookup"><span data-stu-id="fae40-105">Feature activation at the site collection level is necessary to make application pages and templates available to your sites, including configuration pages for scheduled data refresh and application pages for PowerPivot Gallery and Data Feed libraries.</span></span>  
  
 <span data-ttu-id="fae40-106">对于支持 PowerPivot 查询处理的每个网站集，您必须激活 PowerPivot 集成。</span><span class="sxs-lookup"><span data-stu-id="fae40-106">You must activate PowerPivot integration for each site collection that supports PowerPivot query processing.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fae40-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="fae40-107">Prerequisites</span></span>  
 <span data-ttu-id="fae40-108">您必须是网站集管理员。</span><span class="sxs-lookup"><span data-stu-id="fae40-108">You must be a site collection administrator.</span></span>  
  
## <a name="activate-powerpivot-features"></a><span data-ttu-id="fae40-109">激活 PowerPivot 功能</span><span class="sxs-lookup"><span data-stu-id="fae40-109">Activate PowerPivot Features</span></span>  
  
1.  <span data-ttu-id="fae40-110">在 SharePoint 站点上，单击 **“网站操作”**。</span><span class="sxs-lookup"><span data-stu-id="fae40-110">On a SharePoint site, click **Site Actions**.</span></span>  
  
     <span data-ttu-id="fae40-111">默认情况下，通过端口 80 访问 SharePoint Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="fae40-111">By default, SharePoint web applications are accessed through port 80.</span></span> <span data-ttu-id="fae40-112">这意味着通常可通过输入 http:// 打开根网站集以访问 SharePoint 网站\<computer name>。</span><span class="sxs-lookup"><span data-stu-id="fae40-112">This means that you can often access a SharePoint site by entering http://\<computer name> to open the root site collection.</span></span>  
  
2.  <span data-ttu-id="fae40-113">单击 **“网站设置”** 。</span><span class="sxs-lookup"><span data-stu-id="fae40-113">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="fae40-114">在“网站集管理”中，单击 **“网站集功能”**。</span><span class="sxs-lookup"><span data-stu-id="fae40-114">In Site Collection Administration, click **Site collection features**.</span></span>  
  
4.  <span data-ttu-id="fae40-115">向下滚动页面，直至找到 " **PowerPivot 集成网站集功能**"。</span><span class="sxs-lookup"><span data-stu-id="fae40-115">Scroll down the page until you find **PowerPivot Integration Site Collection Feature**.</span></span>  
  
5.  <span data-ttu-id="fae40-116">单击“激活”  。</span><span class="sxs-lookup"><span data-stu-id="fae40-116">Click **Activate**.</span></span>  
  
6.  <span data-ttu-id="fae40-117">通过打开各站点并单击 **“网站操作”**，对于其他网站集重复上述操作。</span><span class="sxs-lookup"><span data-stu-id="fae40-117">Repeat for additional site collections by opening each site and clicking **Site Actions**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fae40-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fae40-118">See Also</span></span>  
 <span data-ttu-id="fae40-119">[管理中心中的 PowerPivot 服务器管理和配置](power-pivot-server-administration-and-configuration-in-central-administration.md) </span><span class="sxs-lookup"><span data-stu-id="fae40-119">[PowerPivot Server Administration and Configuration in Central Administration](power-pivot-server-administration-and-configuration-in-central-administration.md) </span></span>  
 <span data-ttu-id="fae40-120">[初始配置 &#40;PowerPivot for SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="fae40-120">[Initial Configuration &#40;PowerPivot for SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="fae40-121">PowerPivot for SharePoint 2010 安装</span><span class="sxs-lookup"><span data-stu-id="fae40-121">PowerPivot for SharePoint 2010 Installation</span></span>](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
