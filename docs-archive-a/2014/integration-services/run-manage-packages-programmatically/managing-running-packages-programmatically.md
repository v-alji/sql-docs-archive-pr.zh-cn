---
title: 以编程方式管理正在运行的包 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- packages [Integration Services], managing
- running packages [Integration Services]
ms.assetid: 0e91f4ac-6f29-40d7-8c28-9b82e4802c35
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 95c5f9c28b407631764d64523b37a6295870542a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692992"
---
# <a name="managing-running-packages-programmatically"></a><span data-ttu-id="e91da-102">以编程方式管理正在运行的包</span><span class="sxs-lookup"><span data-stu-id="e91da-102">Managing Running Packages Programmatically</span></span>
  <span data-ttu-id="e91da-103">以编程方式使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包时，您可能希望确定哪些包当前正在运行。</span><span class="sxs-lookup"><span data-stu-id="e91da-103">As you work programmatically with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, you may want to determine which packages are currently running.</span></span> <span data-ttu-id="e91da-104"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 命名空间的 <xref:Microsoft.SqlServer.Dts.Runtime> 类提供了满足这些需求的方法和类。</span><span class="sxs-lookup"><span data-stu-id="e91da-104">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class of the <xref:Microsoft.SqlServer.Dts.Runtime> namespace provides methods and classes to satisfy these requirements.</span></span>  
  
 <span data-ttu-id="e91da-105">有关监视包的详细信息，请参阅[包管理（SSIS 服务）](../service/package-management-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="e91da-105">For more information about monitoring packages, see [Package Management &#40;SSIS Service&#41;](../service/package-management-ssis-service.md).</span></span>  
  
 <span data-ttu-id="e91da-106">本主题中讨论的所有方法都需要引用 `Microsoft.SqlServer.ManagedDTS` 程序集。</span><span class="sxs-lookup"><span data-stu-id="e91da-106">All the methods discussed in this topic require a reference to the `Microsoft.SqlServer.ManagedDTS` assembly.</span></span> <span data-ttu-id="e91da-107">在新项目中添加引用后，请 <xref:Microsoft.SqlServer.Dts.Runtime> 使用或语句导入该命名空间 `using` `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="e91da-107">After you add the reference in a new project, import the <xref:Microsoft.SqlServer.Dts.Runtime> namespace with a `using` or `Imports` statement.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e91da-108"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 类中用于 SSIS 包存储的方法仅支持“.”、localhost 或本地服务器的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="e91da-108">The methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class for working with the SSIS Package Store support only ".", localhost, or the server name for the local server.</span></span> <span data-ttu-id="e91da-109">不能使用“(local)”。</span><span class="sxs-lookup"><span data-stu-id="e91da-109">You cannot use "(local)".</span></span>  
  
## <a name="determining-which-packages-are-currently-running"></a><span data-ttu-id="e91da-110">确定当前正在运行的包</span><span class="sxs-lookup"><span data-stu-id="e91da-110">Determining Which Packages Are Currently Running</span></span>  
 <span data-ttu-id="e91da-111">若要确定指定服务器上哪些包当前正在运行，请调用 <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetRunningPackages%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e91da-111">To determine which packages are currently running on the specified server, call the <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetRunningPackages%2A> method.</span></span> <span data-ttu-id="e91da-112">此方法返回 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> 对象的 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> 集合。</span><span class="sxs-lookup"><span data-stu-id="e91da-112">This method returns a <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> collection of <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> objects.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e91da-113">管理员可以看到当前正在该计算机上执行的所有包；其他用户只能看到他们启动的包。</span><span class="sxs-lookup"><span data-stu-id="e91da-113">Administrators see all packages that are currently executing on the computer; other users see only those packages that they have launched.</span></span>  
  
## <a name="working-with-running-packages"></a><span data-ttu-id="e91da-114">使用正在运行的包</span><span class="sxs-lookup"><span data-stu-id="e91da-114">Working with Running Packages</span></span>  
 <span data-ttu-id="e91da-115">确定当前正在运行的包后，可以检索有关这些包的信息以及请求停止包。</span><span class="sxs-lookup"><span data-stu-id="e91da-115">After you have determined which packages are currently running, you can retrieve information about the packages and request that a package be stopped.</span></span>  
  
### <a name="getting-information-about-a-running-package"></a><span data-ttu-id="e91da-116">获取有关正在运行的包的信息</span><span class="sxs-lookup"><span data-stu-id="e91da-116">Getting Information about a Running Package</span></span>  
 <span data-ttu-id="e91da-117">遍历 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> 集合时，可以使用 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> 对象的以下属性来查找包或者获取有关正在运行的包的其他信息：</span><span class="sxs-lookup"><span data-stu-id="e91da-117">As you iterate through the <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> collection, you can use the properties of the <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> object to locate a package or to obtain additional information about the packages that are running:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.ExecutionDuration%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.ExecutionStartTime%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.InstanceID%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageDescription%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageID%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageName%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.UserName%2A>  
  
### <a name="stopping-a-running-package"></a><span data-ttu-id="e91da-118">停止正在运行的包</span><span class="sxs-lookup"><span data-stu-id="e91da-118">Stopping a Running Package</span></span>  
 <span data-ttu-id="e91da-119">可以调用 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.Stop%2A> 对象的 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> 方法来请求停止包。</span><span class="sxs-lookup"><span data-stu-id="e91da-119">You can call the <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.Stop%2A> method of a <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> object to request that the package be stopped.</span></span> <span data-ttu-id="e91da-120">发出停止请求的时间和包实际停止的时间之间可能存在延迟。</span><span class="sxs-lookup"><span data-stu-id="e91da-120">There may be a delay between the time that a stop request is issued and the time that the package actually stops.</span></span>  
  
<span data-ttu-id="e91da-121">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="e91da-121">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="e91da-122">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="e91da-122">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="e91da-123">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="e91da-123">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="e91da-124">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="e91da-124">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e91da-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e91da-125">See Also</span></span>  
 <span data-ttu-id="e91da-126">[包管理 &#40;SSIS 服务&#41;](../service/package-management-ssis-service.md) </span><span class="sxs-lookup"><span data-stu-id="e91da-126">[Package Management &#40;SSIS Service&#41;](../service/package-management-ssis-service.md) </span></span>  
 [<span data-ttu-id="e91da-127">以编程方式枚举可用的包</span><span class="sxs-lookup"><span data-stu-id="e91da-127">Enumerating Available Packages Programmatically</span></span>](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
  
  
