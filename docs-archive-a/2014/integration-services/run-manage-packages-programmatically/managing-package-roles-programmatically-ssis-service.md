---
title: 以编程方式管理包角色（SSIS 服务）| Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, roles
- roles [Integration Services]
- packages [Integration Services], roles
ms.assetid: 2e0ca0d5-d4f5-421d-b17d-a48b37b923e5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dff54f3f90d9e008ae21c83c2a8fdc3f7440a5c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692991"
---
# <a name="managing-package-roles-programmatically-ssis-service"></a><span data-ttu-id="c9117-102">以编程方式管理包角色（SSIS 服务）</span><span class="sxs-lookup"><span data-stu-id="c9117-102">Managing Package Roles Programmatically (SSIS Service)</span></span>
  <span data-ttu-id="c9117-103">以编程方式使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包时，您可能希望确定哪些角色可以应用于包，或确定或设置应用于各个包的角色。</span><span class="sxs-lookup"><span data-stu-id="c9117-103">As you work programmatically with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, you may want to determine which roles are available to apply to packages, or to determine or set the roles applied to an individual package.</span></span> <span data-ttu-id="c9117-104"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 命名空间的 <xref:Microsoft.SqlServer.Dts.Runtime> 类提供了多种满足这些要求的方法。</span><span class="sxs-lookup"><span data-stu-id="c9117-104">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class of the <xref:Microsoft.SqlServer.Dts.Runtime> namespace provides a variety of methods to satisfy these requirements.</span></span>

 <span data-ttu-id="c9117-105">角色仅适用于存储在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb 数据库中的包  。</span><span class="sxs-lookup"><span data-stu-id="c9117-105">Roles apply only to packages stored in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb** database.</span></span> <span data-ttu-id="c9117-106">有关包角色的详细信息，请参阅 [Integration Services 角色（SSIS 服务）](../security/integration-services-roles-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="c9117-106">For more information about package roles, see [Integration Services Roles &#40;SSIS Service&#41;](../security/integration-services-roles-ssis-service.md).</span></span>

 <span data-ttu-id="c9117-107">本主题中讨论的所有方法都需要引用 `Microsoft.SqlServer.ManagedDTS` 程序集。</span><span class="sxs-lookup"><span data-stu-id="c9117-107">All the methods discussed in this topic require a reference to the `Microsoft.SqlServer.ManagedDTS` assembly.</span></span> <span data-ttu-id="c9117-108">在新项目中添加引用后，请 <xref:Microsoft.SqlServer.Dts.Runtime> 使用或语句导入该命名 `using` 空间 `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="c9117-108">After you add the reference in a new project, import the <xref:Microsoft.SqlServer.Dts.Runtime> namespace by using a `using` or `Imports` statement.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="c9117-109"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 类中用于 SSIS 包存储的方法仅支持“.”、localhost 或本地服务器的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="c9117-109">The methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class for working with the SSIS Package Store support only ".", localhost, or the server name for the local server.</span></span> <span data-ttu-id="c9117-110">不能使用“(local)”。</span><span class="sxs-lookup"><span data-stu-id="c9117-110">You cannot use "(local)".</span></span>

## <a name="determining-which-roles-are-available"></a><span data-ttu-id="c9117-111">确定哪些角色可用</span><span class="sxs-lookup"><span data-stu-id="c9117-111">Determining Which Roles Are Available</span></span>
 <span data-ttu-id="c9117-112">若要确定哪些角色可用于存储在特定服务器上的包，可调用 <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerRoles%2A> 类的 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 方法。</span><span class="sxs-lookup"><span data-stu-id="c9117-112">To determine which roles are available for the packages stored on a particular server, call the <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerRoles%2A> method of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class.</span></span>

## <a name="determining-which-roles-are-assigned"></a><span data-ttu-id="c9117-113">确定哪些角色已分配</span><span class="sxs-lookup"><span data-stu-id="c9117-113">Determining Which Roles Are Assigned</span></span>
 <span data-ttu-id="c9117-114">若要确定哪些角色已经分配给了特定包，可调用 <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageRoles%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="c9117-114">To determine which roles have already been assigned to a particular package, call the <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageRoles%2A> method.</span></span> <span data-ttu-id="c9117-115">若要将角色分配给包，可调用 <xref:Microsoft.SqlServer.Dts.Runtime.Application.SetPackageRoles%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="c9117-115">To assign roles to a package, call the <xref:Microsoft.SqlServer.Dts.Runtime.Application.SetPackageRoles%2A> method.</span></span>

<span data-ttu-id="c9117-116">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="c9117-116">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="c9117-117">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="c9117-117">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="c9117-118">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="c9117-118">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="c9117-119">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="c9117-119">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9117-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c9117-120">See Also</span></span>
 [<span data-ttu-id="c9117-121">Integration Services 角色（SSIS 服务）</span><span class="sxs-lookup"><span data-stu-id="c9117-121">Integration Services Roles &#40;SSIS Service&#41;</span></span>](../security/integration-services-roles-ssis-service.md)


