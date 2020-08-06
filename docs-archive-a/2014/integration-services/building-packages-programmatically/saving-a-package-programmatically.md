---
title: 以编程方式保存包 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- programmatically saving a package
- saving a package programmatically
ms.assetid: 4204f817-d5df-475a-9338-d7f01305d566
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a2879c4213b2c9c0bf395c103de0d1bc37e4daab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580335"
---
# <a name="saving-a-package-programmatically"></a><span data-ttu-id="6aef8-102">以编程方式保存包</span><span class="sxs-lookup"><span data-stu-id="6aef8-102">Saving a Package Programmatically</span></span>
  <span data-ttu-id="6aef8-103">以编程方式生成新包或修改现有包后，通常要保存更改。</span><span class="sxs-lookup"><span data-stu-id="6aef8-103">After building a new package programmatically, or modifying an existing one, you usually want to save your changes.</span></span>  
  
 <span data-ttu-id="6aef8-104">本主题中使用的保存包的所有方法都需要引用 `Microsoft.SqlServer.ManagedDTS` 程序集。</span><span class="sxs-lookup"><span data-stu-id="6aef8-104">All of the methods used in this topic to save packages require a reference to the `Microsoft.SqlServer.ManagedDTS` assembly.</span></span> <span data-ttu-id="6aef8-105">在新项目中添加引用后，请 <xref:Microsoft.SqlServer.Dts.Runtime> 使用或语句导入该命名空间 `using` `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="6aef8-105">After you add the reference in a new project, import the <xref:Microsoft.SqlServer.Dts.Runtime> namespace with a `using` or `Imports` statement.</span></span>  
  
## <a name="saving-a-package-programmatically"></a><span data-ttu-id="6aef8-106">以编程方式保存包</span><span class="sxs-lookup"><span data-stu-id="6aef8-106">Saving a Package Programmatically</span></span>  
 <span data-ttu-id="6aef8-107">若要以编程方式保存包，可调用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <xref:Microsoft.SqlServer.Dts.Runtime.Application> 类的以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="6aef8-107">To save a package programmatically, call one of the following methods of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <xref:Microsoft.SqlServer.Dts.Runtime.Application> class:</span></span>  
  
|<span data-ttu-id="6aef8-108">存储位置</span><span class="sxs-lookup"><span data-stu-id="6aef8-108">Storage Location</span></span>|<span data-ttu-id="6aef8-109">调用的方法</span><span class="sxs-lookup"><span data-stu-id="6aef8-109">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="6aef8-110">文件</span><span class="sxs-lookup"><span data-stu-id="6aef8-110">File</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToXml%2A>|  
|<span data-ttu-id="6aef8-111">SSIS 包存储区</span><span class="sxs-lookup"><span data-stu-id="6aef8-111">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServer%2A><br /><br /> <span data-ttu-id="6aef8-112">或</span><span class="sxs-lookup"><span data-stu-id="6aef8-112">or</span></span><br /><br /> <xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServerAs%2A>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6aef8-113"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 类中用于处理 SSIS 包存储区的方法只支持“.”或本地服务器的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="6aef8-113">The methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class for working with the SSIS Package Store only support "." or the server name for the local server.</span></span> <span data-ttu-id="6aef8-114">不能使用“(local)”或“localhost”。</span><span class="sxs-lookup"><span data-stu-id="6aef8-114">You cannot use "(local)" or "localhost".</span></span>  
  
<span data-ttu-id="6aef8-115">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="6aef8-115">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="6aef8-116">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="6aef8-116">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="6aef8-117">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="6aef8-117">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="6aef8-118">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="6aef8-118">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aef8-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6aef8-119">See Also</span></span>  
 [<span data-ttu-id="6aef8-120">保存包</span><span class="sxs-lookup"><span data-stu-id="6aef8-120">Save Packages</span></span>](../save-packages.md)  
  
  
