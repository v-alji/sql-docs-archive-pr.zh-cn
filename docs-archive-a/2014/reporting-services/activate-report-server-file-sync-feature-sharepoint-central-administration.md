---
title: 在 SharePoint 管理中心中激活报表服务器文件同步功能 |Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 03/06/2017
ms.openlocfilehash: 55feac69da85c7287ea56f4b8245350dd7e69565
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588363"
---
# <a name="activate-the-report-server-file-sync-feature-in-sharepoint-central-administration"></a><span data-ttu-id="f450b-102">在 SharePoint 管理中心中激活报表服务器文件同步功能</span><span class="sxs-lookup"><span data-stu-id="f450b-102">Activate the Report Server File Sync Feature in SharePoint Central Administration</span></span>

<span data-ttu-id="f450b-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 报表服务器文件同步功能利用 SharePoint 事件处理程序将报表服务器目录与文档库中的项进行同步。</span><span class="sxs-lookup"><span data-stu-id="f450b-103">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Report Server File Sync feature utilizes SharePoint event handlers to synchronize the report server catalog with items in document libraries.</span></span> <span data-ttu-id="f450b-104">当用户经常直接将已发布的报表项上载到 SharePoint 文档库时，此功能很有用。</span><span class="sxs-lookup"><span data-stu-id="f450b-104">This feature is beneficial when users frequently upload published report items directly to SharePoint document libraries.</span></span> <span data-ttu-id="f450b-105">如果文件同步功能未激活，则内容仍将同步，但不会频繁地同步。</span><span class="sxs-lookup"><span data-stu-id="f450b-105">If the file Sync feature isn't activated, content will still be synchronized but not as frequently.</span></span>  
  
<span data-ttu-id="f450b-106">在安装了用于 SharePoint 产品的 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] 外接程序之后，可以在 SharePoint 站点管理中激活该文件同步功能。</span><span class="sxs-lookup"><span data-stu-id="f450b-106">The File Sync feature can be activated in SharePoint Site Administration after you install the [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] Add-in for SharePoint products.</span></span>  
  
<span data-ttu-id="f450b-107">可对于每个站点（但不在网站集级别）手动激活和停用此功能。</span><span class="sxs-lookup"><span data-stu-id="f450b-107">This feature can be manually activated and deactivated per site but not at the site collection level.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f450b-108">必备条件</span><span class="sxs-lookup"><span data-stu-id="f450b-108">Prerequisites</span></span>  
 <span data-ttu-id="f450b-109">必须安装用于 SharePoint 的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 外接程序。</span><span class="sxs-lookup"><span data-stu-id="f450b-109">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Add-in for SharePoint must be installed.</span></span> <span data-ttu-id="f450b-110">如果未安装外接程序，则文件同步功能在站点功能列表中不可见。</span><span class="sxs-lookup"><span data-stu-id="f450b-110">If the add-in isn't installed, the file sync feature won't be visible in the site feature list.</span></span>  
  
 <span data-ttu-id="f450b-111">若要验证是否已安装，请在 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows **“控制面板”** 中查看已安装应用程序的列表。</span><span class="sxs-lookup"><span data-stu-id="f450b-111">To verify installation, view the list of installed applications in [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows **Control Panel**.</span></span> <span data-ttu-id="f450b-112">如果 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 外接程序已安装，请按照本主题中的说明激活报表服务器文件同步功能。</span><span class="sxs-lookup"><span data-stu-id="f450b-112">If the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Add-in is installed, follow the instructions in this topic to activate the report server file sync feature.</span></span>  
  
### <a name="to-activate-or-deactivate-the-reporting-services-file-sync-feature-on-a-site"></a><span data-ttu-id="f450b-113">在站点上激活或停用 Reporting Services 文件同步功能</span><span class="sxs-lookup"><span data-stu-id="f450b-113">To activate or deactivate the Reporting Services File Sync feature on a Site</span></span>  
  
1.  <span data-ttu-id="f450b-114">在站点的主页中，单击 "**站点操作**" 菜单，然后单击 "**站点设置**"。</span><span class="sxs-lookup"><span data-stu-id="f450b-114">From the main page of your site, click the **Site Actions** menu and click **Site Settings**.</span></span>  
  
2.  <span data-ttu-id="f450b-115">在 "**站点操作**" 中，单击 "**管理站点功能**"。</span><span class="sxs-lookup"><span data-stu-id="f450b-115">In the **Site Actions**, click **Manage Site Features**.</span></span>  
  
3.  <span data-ttu-id="f450b-116">在列表中找到 **“报表服务器文件同步”** 。</span><span class="sxs-lookup"><span data-stu-id="f450b-116">Find **Report Server File Sync** in the list.</span></span>  
  
4.  <span data-ttu-id="f450b-117">单击“激活”  。</span><span class="sxs-lookup"><span data-stu-id="f450b-117">Click **Activate**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f450b-118"> 若要停用报表服务器文件同步功能，您可以使用相同的过程，但单击 **“停用”**。</span><span class="sxs-lookup"><span data-stu-id="f450b-118">To deactivate the Report Server file sync feature, you can use the same procedure but click **Deactivate**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f450b-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f450b-119">See Also</span></span>  
 <span data-ttu-id="f450b-120">[&#40;报表生成器和 SSRS 的报表部件疑难解答&#41;](report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f450b-120">[Troubleshoot Report Parts &#40;Report Builder and SSRS&#41;](report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f450b-121">[在 SharePoint 中激活报表服务器和 Power View 集成功能](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="f450b-121">[Activate the Report Server and Power View Integration Features in SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md) </span></span>  
 <span data-ttu-id="f450b-122">[安装或卸载用于 SharePoint 的 Reporting Services 外接程序 &#40;SharePoint 2010 和 SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="f450b-122">[Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="f450b-123">安装或卸载用于 SharePoint 的 Reporting Services 外接程序 &#40;SharePoint 2010 和 SharePoint 2013&#41;</span><span class="sxs-lookup"><span data-stu-id="f450b-123">Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
