---
title: 保护主数据管理器 Web 应用程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: e360ba3a-e96b-4f85-b588-ed1f767fa973
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8f2ee807c2cd474542f701226d08427ade8279e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692445"
---
# <a name="secure-a-master-data-manager-web-application"></a><span data-ttu-id="65181-102">保护主数据管理器 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="65181-102">Secure a Master Data Manager Web Application</span></span>
  <span data-ttu-id="65181-103">您可以使用 HTTPS 保护 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="65181-103">You can secure the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application with HTTPS.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="65181-104">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序可以使用 HTTP 或 HTTPS，但不是同时使用这两者。</span><span class="sxs-lookup"><span data-stu-id="65181-104">The [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application can use either HTTP or HTTPS, but not both.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="65181-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="65181-105">Prerequisites</span></span>  
 <span data-ttu-id="65181-106">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="65181-106">To perform the procedure:</span></span>  
  
-   <span data-ttu-id="65181-107">您必须是安装了 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 的 Web 服务器上的管理员。</span><span class="sxs-lookup"><span data-stu-id="65181-107">You must be an administrator on the web server where [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] is installed.</span></span>  
  
-   <span data-ttu-id="65181-108">MDS 必须安装在 Web 服务器上，并且 Web 应用程序必须存在。</span><span class="sxs-lookup"><span data-stu-id="65181-108">MDS must be installed on the web server, and a web application must exist.</span></span> <span data-ttu-id="65181-109">有关详细信息，请参阅 [安装 Master Data Services](install-master-data-services.md) 和 [创建主数据管理器 Web 应用程序 (Master Data Services)](create-a-master-data-manager-web-application-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="65181-109">For more information, see [Install Master Data Services](install-master-data-services.md) and [Create a Master Data Manager Web Application &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md).</span></span>  
  
### <a name="to-secure-the-master-data-manager-web-application-with-https"></a><span data-ttu-id="65181-110">使用 HTTPS 保护主数据管理器 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="65181-110">To secure the Master Data Manager web application with HTTPS</span></span>  
  
1.  <span data-ttu-id="65181-111">在您确认已使用 HTTP 正确配置了 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序后，在 IIS 中创建一个证书。</span><span class="sxs-lookup"><span data-stu-id="65181-111">After you have confirmed that the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application is configured correctly with HTTP, create a certificate in IIS.</span></span> <span data-ttu-id="65181-112">有关详细信息，请参阅 [在 IIS 7 中配置服务器证书](https://technet.microsoft.com/library/cc732230\(WS.10\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="65181-112">For more information, see [Configuring Server Certificates in IIS 7](https://technet.microsoft.com/library/cc732230\(WS.10\).aspx).</span></span>  
  
2.  <span data-ttu-id="65181-113">在 **“连接”** 窗格中的 **“站点”** 的下面，单击承载 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序的站点。</span><span class="sxs-lookup"><span data-stu-id="65181-113">In the **Connections** pane, under **Sites**, click the site that hosts the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
3.  <span data-ttu-id="65181-114">在“操作”\*\*\*\* 窗格中，单击“绑定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65181-114">In the **Actions** pane, click **Bindings**.</span></span>  
  
4.  <span data-ttu-id="65181-115">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="65181-115">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="65181-116">从列表中选择 **https**。</span><span class="sxs-lookup"><span data-stu-id="65181-116">From the list, select **https**.</span></span>  
  
6.  <span data-ttu-id="65181-117">选择 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="65181-117">Select the SSL certificate.</span></span>  
  
7.  <span data-ttu-id="65181-118">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="65181-118">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="65181-119">可选。</span><span class="sxs-lookup"><span data-stu-id="65181-119">Optional.</span></span> <span data-ttu-id="65181-120">若要删除 HTTP 以便用户只能使用 HTTPS 访问站点，请单击含有 **http**的行。</span><span class="sxs-lookup"><span data-stu-id="65181-120">To remove HTTP so that users can access the site with HTTPS only, from the list, click the row with **http**.</span></span> <span data-ttu-id="65181-121">单击 **“删除”** ，然后在确认对话框上单击 **“是”**。</span><span class="sxs-lookup"><span data-stu-id="65181-121">Click **Remove** and on the confirmation dialog box, click **Yes**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="65181-122">您必须在删除 HTTP 后更改 basicHttp 和 wsHttpBinding 配置。</span><span class="sxs-lookup"><span data-stu-id="65181-122">You must change basicHttp and wsHttpBinding configurations after removing HTTP.</span></span>  
  
9. <span data-ttu-id="65181-123">若要关闭 **“站点绑定”** 对话框，请单击 **“关闭”**。</span><span class="sxs-lookup"><span data-stu-id="65181-123">To close the **Site Bindings** dialog box, click **Close**.</span></span>  
  
10. <span data-ttu-id="65181-124">现在，从*驱动器*： \PROGRAM Files\Microsoft SQL Server\120\Master Data services\webapplication。打开 web.config 文件</span><span class="sxs-lookup"><span data-stu-id="65181-124">Now open the web.config file from *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\WebApplication.</span></span>  
  
11. <span data-ttu-id="65181-125">找到字符串 `<security mode="Message">` ，然后将其更改为 `<security mode="Transport">`。</span><span class="sxs-lookup"><span data-stu-id="65181-125">Find the string `<security mode="Message">` and change it to `<security mode="Transport">`.</span></span>  
  
12. <span data-ttu-id="65181-126">保存并关闭该文件。</span><span class="sxs-lookup"><span data-stu-id="65181-126">Save and close the file.</span></span> <span data-ttu-id="65181-127">如果您遇到错误，可能是因为您已启用了 UAC。</span><span class="sxs-lookup"><span data-stu-id="65181-127">If you get an error, it could be because you have UAC enabled.</span></span> <span data-ttu-id="65181-128">有关详细信息，请参阅 [关闭用户帐户控制](https://technet.microsoft.com/library/cc709691\(WS.10\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="65181-128">For more information, see [Turn off User Account Control](https://technet.microsoft.com/library/cc709691\(WS.10\).aspx).</span></span> <span data-ttu-id="65181-129">用户现在应该能够使用 HTTPS 访问该站点了。</span><span class="sxs-lookup"><span data-stu-id="65181-129">Users should now be able to use HTTPS to access the site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65181-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="65181-130">See Also</span></span>  
 [<span data-ttu-id="65181-131">创建主数据管理器 Web 应用程序 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="65181-131">Create a Master Data Manager Web Application &#40;Master Data Services&#41;</span></span>](create-a-master-data-manager-web-application-master-data-services.md)  
  
  
