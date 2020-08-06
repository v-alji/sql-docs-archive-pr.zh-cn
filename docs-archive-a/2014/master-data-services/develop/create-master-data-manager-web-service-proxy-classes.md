---
title: 创建主数据管理器 Web 服务代理类 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 8bdab026-a0c0-41f3-9d36-f3919c23247f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c4f25d749f829357f6541f14073e654bade27215
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591922"
---
# <a name="create-master-data-manager-web-service-proxy-classes"></a><span data-ttu-id="6e6ae-102">创建主数据管理器 Web 服务代理类</span><span class="sxs-lookup"><span data-stu-id="6e6ae-102">Create Master Data Manager Web Service Proxy Classes</span></span>
  <span data-ttu-id="6e6ae-103">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 服务可让您通过任何能访问 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 网站的计算机以编程方式使用 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 的功能。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-103">The [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web service lets you make programmatic use of the features of [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] from any computer that can access your [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web site.</span></span> <span data-ttu-id="6e6ae-104">在开始编写访问 Web 服务的代码之前，必须先生成代理类。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-104">Before you can start writing code to access the web service, you must generate proxy classes.</span></span> <span data-ttu-id="6e6ae-105">您用于执行 Web 服务操作的主代理类是 <xref:Microsoft.MasterDataServices.ServiceClient> 类，它可实现 <xref:Microsoft.MasterDataServices.IService> 接口。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-105">The main proxy class you use to perform web service operations is the <xref:Microsoft.MasterDataServices.ServiceClient> class, which implements the <xref:Microsoft.MasterDataServices.IService> interface.</span></span>  
  
## <a name="enable-web-service-metadata-publishing"></a><span data-ttu-id="6e6ae-106">启用 Web 服务元数据发布</span><span class="sxs-lookup"><span data-stu-id="6e6ae-106">Enable Web Service Metadata Publishing</span></span>  
 <span data-ttu-id="6e6ae-107">在可以生成代理类之前，必须启用 Web 服务元数据发布。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-107">Before you can generate proxy classes, you must enable web service metadata publishing.</span></span> <span data-ttu-id="6e6ae-108">请按照下列步骤完成此操作：</span><span class="sxs-lookup"><span data-stu-id="6e6ae-108">Follow these steps to do this:</span></span>  
  
1.  <span data-ttu-id="6e6ae-109">在文本编辑器中打开 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web.配置文件。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-109">Open the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web.config file in a text editor.</span></span> <span data-ttu-id="6e6ae-110">此文件位于 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 安装路径的 WebApplication 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-110">This file is in the WebApplication folder of the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] installation path.</span></span>  
  
2.  <span data-ttu-id="6e6ae-111">查找 `mdsWsHttpBehavior` 下面的部分 **\<serviceBehaviors>** 。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-111">Find the `mdsWsHttpBehavior` section under **\<serviceBehaviors>**.</span></span> <span data-ttu-id="6e6ae-112">对于 **\<serviceMetadata>** 元素，将设置 `httpGetEnabled` 为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-112">For the **\<serviceMetadata>** element, set `httpGetEnabled` to `true`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6e6ae-113">如果您想要通过安全套接字层 (SSL) 启用 Web 服务，请在 web.config 文件的 `httpsGetEnabled` 部分中将 `true` 设置为 `mdsWsHttpBehavior`。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-113">If you want to enable Web services over Secure Sockets Layer (SSL), set `httpsGetEnabled` to `true` in the `mdsWsHttpBehavior` section of the web.config file.</span></span> <span data-ttu-id="6e6ae-114">您还需要更改 `mdsWsHTTPBinding`，以便也为 SSL 配置它，并且注释掉非 SSL 部分。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-114">You also need to change `mdsWsHTTPBinding` so that it is configured for SSL, as well, and comment out the non-SSL section.</span></span>  
  
3.  <span data-ttu-id="6e6ae-115">保存对文件的更改。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-115">Save changes to the file.</span></span>  
  
4.  <span data-ttu-id="6e6ae-116">通过浏览服务 URL 来测试元数据发布，例如：http://yourserver/MDS/service/service.svc。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-116">Test metadata publishing by browsing to the service URL, for example: http://yourserver/MDS/service/service.svc.</span></span> <span data-ttu-id="6e6ae-117">如果启用元数据发布，则会显示一个以</span><span class="sxs-lookup"><span data-stu-id="6e6ae-117">If metadata publishing is enabled, a page is displayed that begins with</span></span>   
    <span data-ttu-id="6e6ae-118">“你已创建服务”开头的页面。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-118">"You have created a service."</span></span>  
  
## <a name="creating-proxy-classes-by-using-visual-studio"></a><span data-ttu-id="6e6ae-119">通过使用 Visual Studio 创建代理类</span><span class="sxs-lookup"><span data-stu-id="6e6ae-119">Creating Proxy Classes by Using Visual Studio</span></span>  
 <span data-ttu-id="6e6ae-120">如果已安装了 Visual Studio 2010，则生成代理类的最简方法是将“服务引用”添加到项目中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-120">If you have Visual Studio 2010 installed, the simplest way to generate proxy classes is to add a **Service Reference** to your project.</span></span> <span data-ttu-id="6e6ae-121">服务引用的地址为 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序的 URL，后面追加 /service/service.svc。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-121">The address of the service reference is the URL of the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application, appended with /service/service.svc.</span></span> <span data-ttu-id="6e6ae-122">例如： http://yourserver/MDS/service/service.svc。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-122">For example: http://yourserver/MDS/service/service.svc.</span></span> <span data-ttu-id="6e6ae-123">有关详细信息，请参阅[如何添加、更新或删除服务引用](https://go.microsoft.com/fwlink/?LinkId=221167)。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-123">For more information, see [How to: Add, Update, or Remove a Service Reference](https://go.microsoft.com/fwlink/?LinkId=221167).</span></span>  
  
## <a name="creating-proxy-classes-by-using-svcutilexe"></a><span data-ttu-id="6e6ae-124">使用 Svcutil.exe 创建代理类</span><span class="sxs-lookup"><span data-stu-id="6e6ae-124">Creating Proxy Classes by Using Svcutil.exe</span></span>  
 <span data-ttu-id="6e6ae-125">必须 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 安装或 Windows SDK，才能在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 计算机上 Svcutil.exe。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-125">You must have either [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows SDK installed in order to have Svcutil.exe on your computer.</span></span> <span data-ttu-id="6e6ae-126">如果使用 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]，必须使用 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 命令提示符运行该命令。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-126">If you use [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], you must use the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] command prompt to run the command.</span></span> <span data-ttu-id="6e6ae-127">有关详细信息，请参阅 [ServiceModel 元数据实用工具 (Svcutil.exe)](https://go.microsoft.com/fwlink/?LinkId=165027) 和[根据服务元数据生成 WCF 客户端](https://go.microsoft.com/fwlink/?LinkId=164821)。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-127">For more information, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://go.microsoft.com/fwlink/?LinkId=165027) and [Generating a WCF Client from Service Metadata](https://go.microsoft.com/fwlink/?LinkId=164821).</span></span>  
  
 <span data-ttu-id="6e6ae-128">若要使用 Svcutil.exe 创建一组 C# 代理类，请使用如下命令：</span><span class="sxs-lookup"><span data-stu-id="6e6ae-128">To create a set of C# proxy classes by using Svcutil.exe, use a command such as the following:</span></span>  
  
```  
svcutil.exe http://<server_name:port>/<virtual_path>/Service/Service.svc   
/out:<proxy_name>.cs /messageContract /tcv:Version35   
/noconfig /ct:System.Collections.ObjectModel.Collection`1   
/namespace:*,Microsoft.MasterDataServices  
```  
  
 <span data-ttu-id="6e6ae-129">其中：</span><span class="sxs-lookup"><span data-stu-id="6e6ae-129">Where:</span></span>  
  
-   <span data-ttu-id="6e6ae-130">servername:port 是承载 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 的计算机名称和端口号\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-130">*servername*:*port* are the computer name and port number of the computer that hosts [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span>  
  
-   <span data-ttu-id="6e6ae-131">virtual_path 是 Internet 信息服务 (IIS) 中 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 的虚拟路径\*\*。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-131">*virtual_path* is the virtual path of [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] in Internet Information Services (IIS).</span></span>  
  
-   <span data-ttu-id="6e6ae-132">proxy_name 是生成的代理文件名称\*\*。</span><span class="sxs-lookup"><span data-stu-id="6e6ae-132">*proxy_name* is the name for the generated proxy file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e6ae-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6e6ae-133">See Also</span></span>  
 [<span data-ttu-id="6e6ae-134">分类的 Web 服务操作 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6e6ae-134">Categorized Web Service Operations &#40;Master Data Services&#41;</span></span>](categorized-web-service-operations-master-data-services.md)  
  
  
