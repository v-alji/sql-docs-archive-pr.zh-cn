---
title: 创建主数据管理器 Web 应用程序 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 241d46d7-8008-47f6-bebd-0dfff1cc856a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fd81188b499850397aa8ffd2e40cfcb91c648288
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578913"
---
# <a name="create-a-master-data-manager-web-application-master-data-services"></a><span data-ttu-id="10501-102">创建主数据管理器 Web 应用程序 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="10501-102">Create a Master Data Manager Web Application (Master Data Services)</span></span>
  <span data-ttu-id="10501-103">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序提供了一个接口，便于用户使用主数据，并供管理员用来配置和管理 MDS。</span><span class="sxs-lookup"><span data-stu-id="10501-103">The [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application provides an interface for users to work with master data and for administrators to configure and administer MDS.</span></span>  
  
 <span data-ttu-id="10501-104">网站必须始终包含 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="10501-104">A web application must always be contained by a website.</span></span> <span data-ttu-id="10501-105">要创建 Web 应用程序，您必须：</span><span class="sxs-lookup"><span data-stu-id="10501-105">To create a web application, you must either:</span></span>  
  
-   <span data-ttu-id="10501-106">使用默认网站，然后创建 Web 应用程序；</span><span class="sxs-lookup"><span data-stu-id="10501-106">Use the Default website and then create the web application,</span></span>  
  
-   <span data-ttu-id="10501-107">使用现有网站，然后创建 Web 应用程序；或者</span><span class="sxs-lookup"><span data-stu-id="10501-107">Use an existing website and then create the web application, or</span></span>  
  
-   <span data-ttu-id="10501-108">创建新网站，这将自动创建 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="10501-108">Create a new website, which automatically creates a web application.</span></span>  
  
 <span data-ttu-id="10501-109">在您创建 Web 应用程序之后，将其与 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 数据库相关联。</span><span class="sxs-lookup"><span data-stu-id="10501-109">After you create the web application, you associate it with the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="10501-110">先决条件</span><span class="sxs-lookup"><span data-stu-id="10501-110">Prerequisites</span></span>  
  
-   <span data-ttu-id="10501-111">有关承载 Web 应用程序的计算机的要求信息，请参阅 [Web 应用程序要求 (Master Data Services)](web-application-requirements-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="10501-111">For information about the requirements for the computer that hosts the web application, see [Web Application Requirements &#40;Master Data Services&#41;](web-application-requirements-master-data-services.md).</span></span>  
  
## <a name="to-create-a-master-data-manager-web-application-in-a-new-website"></a><span data-ttu-id="10501-112">在新网站中创建主数据管理器 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="10501-112">To create a Master Data Manager web application in a new website</span></span>  
 <span data-ttu-id="10501-113">当您创建新网站时，根 Web 应用程序为 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="10501-113">When you create a new website, the root web application is the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span> <span data-ttu-id="10501-114">也将该 Web 应用程序添加到新的应用程序池中。</span><span class="sxs-lookup"><span data-stu-id="10501-114">The web application is also added to a new application pool.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="10501-115">如果遵循此过程，则不能指定 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序的虚拟路径和别名。</span><span class="sxs-lookup"><span data-stu-id="10501-115">If you follow this procedure, you cannot specify a virtual path and alias of the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span> <span data-ttu-id="10501-116">如果要指定 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]的虚拟路径和别名，必须在尚未配置为 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序的现有网站中创建 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="10501-116">If you want to specify a virtual path and alias for [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], you must create a web application in an existing website that is not already configured as a [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
 <span data-ttu-id="10501-117">此外， [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] 支持仅使用 HTTP 绑定创建站点。</span><span class="sxs-lookup"><span data-stu-id="10501-117">Additionally, [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] supports creating sites with HTTP bindings only.</span></span> <span data-ttu-id="10501-118">若要添加 HTTPS 绑定，请在 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] 中创建新站点和应用程序，然后参阅 [保护主数据管理器 Web 应用程序](secure-a-master-data-manager-web-application.md) 以获取详细信息。</span><span class="sxs-lookup"><span data-stu-id="10501-118">To add an HTTPS binding, create a new site and application in [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] and then see [Secure a Master Data Manager Web Application](secure-a-master-data-manager-web-application.md) for more information.</span></span>  
  
#### <a name="to-create-a-master-data-manager-web-application-in-a-new-website"></a><span data-ttu-id="10501-119">在新网站中创建主数据管理器 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="10501-119">To create a Master Data Manager web application in a new website</span></span>  
  
1.  <span data-ttu-id="10501-120">打开 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="10501-120">Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
2.  <span data-ttu-id="10501-121">在左窗格中单击 **“Web 配置”** 。</span><span class="sxs-lookup"><span data-stu-id="10501-121">In the left pane, click **Web Configuration**.</span></span>  
  
3.  <span data-ttu-id="10501-122">在 **“Web 配置”** 页上的网站列表中，选择 **“新建网站”**。</span><span class="sxs-lookup"><span data-stu-id="10501-122">On the **Web Configuration** page, in the Website list, select **Create new website**.</span></span>  
  
4.  <span data-ttu-id="10501-123">在 **“创建网站”** 对话框中，指定新网站的信息。</span><span class="sxs-lookup"><span data-stu-id="10501-123">On the **Create Website** dialog box, specify information for a new website.</span></span> <span data-ttu-id="10501-124">有关对话框中的用户界面 (UI) 选项的详细信息，请参阅 [创建网站对话框（Master Data Services 配置管理器）](../create-website-dialog-box-master-data-services-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="10501-124">For more information about the user interface (UI) options in the dialog box, see [Create Website Dialog Box &#40;Master Data Services Configuration Manager&#41;](../create-website-dialog-box-master-data-services-configuration-manager.md).</span></span>  
  
5.  <span data-ttu-id="10501-125">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="10501-125">Click **OK**.</span></span>  
  
## <a name="to-create-a-master-data-manager-web-application-in-an-existing-website"></a><span data-ttu-id="10501-126">在现有网站中创建主数据管理器 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="10501-126">To create a Master Data Manager web application in an existing website</span></span>  
 <span data-ttu-id="10501-127">在现有网站中创建 Web 应用程序时，您可以选择 Web 应用程序的虚拟路径和别名。</span><span class="sxs-lookup"><span data-stu-id="10501-127">When you create a web application in an existing website, you can choose the virtual path and alias of the web application.</span></span> <span data-ttu-id="10501-128">将该 Web 应用程序添加到新的应用程序池中。</span><span class="sxs-lookup"><span data-stu-id="10501-128">The web application is added to a new application pool.</span></span>  
  
#### <a name="to-create-a-master-data-manager-web-application-in-an-existing-website"></a><span data-ttu-id="10501-129">在现有网站中创建主数据管理器 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="10501-129">To create a Master Data Manager web application in an existing website</span></span>  
  
1.  <span data-ttu-id="10501-130">打开 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="10501-130">Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
2.  <span data-ttu-id="10501-131">在左窗格中单击 **“Web 配置”** 。</span><span class="sxs-lookup"><span data-stu-id="10501-131">In the left pane, click **Web Configuration**.</span></span>  
  
3.  <span data-ttu-id="10501-132">在 **“Web 配置”** 页上，从 **“网站”** 列表中选择要创建 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序的网站。</span><span class="sxs-lookup"><span data-stu-id="10501-132">On the **Web Configuration** page, from the **Website** list, select the website in which you want to create the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
4.  <span data-ttu-id="10501-133">单击 **“创建应用程序”**。</span><span class="sxs-lookup"><span data-stu-id="10501-133">Click **Create Application**.</span></span>  
  
5.  <span data-ttu-id="10501-134">在 **“创建 Web 应用程序”** 对话框中，指定新 Web 应用程序的信息。</span><span class="sxs-lookup"><span data-stu-id="10501-134">On the **Create Web Application** dialog box, specify information for a new web application.</span></span> <span data-ttu-id="10501-135">有关对话框中的用户界面 (UI) 选项的详细信息，请参阅 [创建 Web 应用程序对话框（Master Data Services 配置管理器）](../create-web-application-dialog-box-master-data-services-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="10501-135">For more information about the user interface (UI) options in the dialog box, see [Create Web Application Dialog Box &#40;Master Data Services Configuration Manager&#41;](../create-web-application-dialog-box-master-data-services-configuration-manager.md).</span></span>  
  
6.  <span data-ttu-id="10501-136">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="10501-136">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="10501-137">后续步骤</span><span class="sxs-lookup"><span data-stu-id="10501-137">Next Steps</span></span>  
  
-   <span data-ttu-id="10501-138">将 Web 应用程序与 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 数据库关联。</span><span class="sxs-lookup"><span data-stu-id="10501-138">Associate the web application with a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="10501-139">有关详细信息，请参阅 [将 Master Data Services 数据库与 Web 应用程序关联](associate-a-master-data-services-database-and-web-application.md)。</span><span class="sxs-lookup"><span data-stu-id="10501-139">For more information, see [Associate a Master Data Services Database and Web Application](associate-a-master-data-services-database-and-web-application.md).</span></span>  
  
-   <span data-ttu-id="10501-140">如果你想要通过使用安全套接字层 (SSL) 对内容进行加密，还可以配置承载 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序的网站以便使用 HTTPS 绑定。</span><span class="sxs-lookup"><span data-stu-id="10501-140">Optionally, configure the website that hosts the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application to use an HTTPS binding if you want to encrypt content by using Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="10501-141">您必须使用 IIS 管理器之类的 Internet Information Services (IIS) 工具为 Web 服务器配置服务器证书，以及为站点配置 HTTPS 绑定和 SSL 设置。</span><span class="sxs-lookup"><span data-stu-id="10501-141">You must use an Internet Information Services (IIS) tool, such as IIS Manager, to configure the server certificate for the web server, and to configure an HTTPS binding and the SSL settings for the site.</span></span> <span data-ttu-id="10501-142">有关详细信息，请参阅 [Secure a Master Data Manager Web Application](secure-a-master-data-manager-web-application.md)。</span><span class="sxs-lookup"><span data-stu-id="10501-142">For more information, see [Secure a Master Data Manager Web Application](secure-a-master-data-manager-web-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10501-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10501-143">See Also</span></span>  
 [<span data-ttu-id="10501-144">安装 Master Data Services</span><span class="sxs-lookup"><span data-stu-id="10501-144">Install Master Data Services</span></span>](install-master-data-services.md)  
  
  
