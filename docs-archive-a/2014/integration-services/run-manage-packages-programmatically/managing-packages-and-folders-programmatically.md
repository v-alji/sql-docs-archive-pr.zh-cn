---
title: 以编程方式管理包和文件夹 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], managing
- custom enumerators [Integration Services]
ms.assetid: ec59b75d-ba09-44ac-9039-9d593bb462d9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 695ff4ad020dbdfb2564b4964a55324db4248517
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692989"
---
# <a name="managing-packages-and-folders-programmatically"></a><span data-ttu-id="db1e6-102">以编程方式管理包和文件夹</span><span class="sxs-lookup"><span data-stu-id="db1e6-102">Managing Packages and Folders Programmatically</span></span>
  <span data-ttu-id="db1e6-103">以编程方式使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包时，您可能希望确定个别包或文件夹是否存在，或管理用于存储包的文件夹。</span><span class="sxs-lookup"><span data-stu-id="db1e6-103">As you work programmatically with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, you may want to determine whether an individual package or folder exists, or to manage the folders in which packages are stored.</span></span> <span data-ttu-id="db1e6-104"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 命名空间的 <xref:Microsoft.SqlServer.Dts.Runtime> 类提供了多种满足这些要求的方法。</span><span class="sxs-lookup"><span data-stu-id="db1e6-104">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class of the <xref:Microsoft.SqlServer.Dts.Runtime> namespace provides a variety of methods to satisfy these requirements.</span></span>  
  
##  <a name="determining-whether-a-package-or-folder-exists"></a><a name="exists"></a><span data-ttu-id="db1e6-105">确定包或文件夹是否存在</span><span class="sxs-lookup"><span data-stu-id="db1e6-105">Determining Whether a Package or Folder Exists</span></span>  
 <span data-ttu-id="db1e6-106">若要以编程方式确定已保存的包是否存在，请先调用以下方法之一，然后尝试加载和运行该包：</span><span class="sxs-lookup"><span data-stu-id="db1e6-106">To determine programmatically whether a saved package exists, call one of the following methods before attempting to load and run the package:</span></span>  
  
|<span data-ttu-id="db1e6-107">存储位置</span><span class="sxs-lookup"><span data-stu-id="db1e6-107">Storage Location</span></span>|<span data-ttu-id="db1e6-108">调用的方法</span><span class="sxs-lookup"><span data-stu-id="db1e6-108">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="db1e6-109">SSIS 包存储区</span><span class="sxs-lookup"><span data-stu-id="db1e6-109">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnSqlServer%2A>|  
  
 <span data-ttu-id="db1e6-110">若要以编程方式确定文件夹是否存在，请先调用以下方法之一，然后尝试列出其中存储的包：</span><span class="sxs-lookup"><span data-stu-id="db1e6-110">To determine programmatically whether a folder exists, call one of the following methods before attempting to list the packages stored in the folder, :</span></span>  
  
|<span data-ttu-id="db1e6-111">存储位置</span><span class="sxs-lookup"><span data-stu-id="db1e6-111">Storage Location</span></span>|<span data-ttu-id="db1e6-112">调用的方法</span><span class="sxs-lookup"><span data-stu-id="db1e6-112">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="db1e6-113">SSIS 包存储区</span><span class="sxs-lookup"><span data-stu-id="db1e6-113">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnSqlServer%2A>|  
  

  
##  <a name="managing-packages-and-folders"></a><a name="managing"></a><span data-ttu-id="db1e6-114">管理包和文件夹</span><span class="sxs-lookup"><span data-stu-id="db1e6-114">Managing Packages and Folders</span></span>  
 <span data-ttu-id="db1e6-115"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 命名空间的 <xref:Microsoft.SqlServer.Dts.Runtime> 类提供其他用于管理包和存储包的文件夹的方法。</span><span class="sxs-lookup"><span data-stu-id="db1e6-115">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class of the <xref:Microsoft.SqlServer.Dts.Runtime> namespace provides additional methods for managing packages and the folders in which they are stored.</span></span>  
  
###  <a name="removing-a-package"></a><a name="managing_rempkg"></a><span data-ttu-id="db1e6-116">删除包</span><span class="sxs-lookup"><span data-stu-id="db1e6-116">Removing a Package</span></span>  
 <span data-ttu-id="db1e6-117">若要以编程方式删除已保存的包，请调用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="db1e6-117">To remove a saved package programmatically, call one of the following methods:</span></span>  
  
|<span data-ttu-id="db1e6-118">存储位置</span><span class="sxs-lookup"><span data-stu-id="db1e6-118">Storage Location</span></span>|<span data-ttu-id="db1e6-119">调用的方法</span><span class="sxs-lookup"><span data-stu-id="db1e6-119">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="db1e6-120">SSIS 包存储区</span><span class="sxs-lookup"><span data-stu-id="db1e6-120">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromSqlServer%2A>|  
  

  
###  <a name="creating-a-folder"></a><a name="managing_create"></a><span data-ttu-id="db1e6-121">创建文件夹</span><span class="sxs-lookup"><span data-stu-id="db1e6-121">Creating a Folder</span></span>  
 <span data-ttu-id="db1e6-122">若要以编程方式创建存储文件夹，请调用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="db1e6-122">To create a storage folder programmatically, call one of the following methods:</span></span>  
  
|<span data-ttu-id="db1e6-123">存储位置</span><span class="sxs-lookup"><span data-stu-id="db1e6-123">Storage Location</span></span>|<span data-ttu-id="db1e6-124">调用的方法</span><span class="sxs-lookup"><span data-stu-id="db1e6-124">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="db1e6-125">SSIS 包存储区</span><span class="sxs-lookup"><span data-stu-id="db1e6-125">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnSqlServer%2A>|  
  

  
###  <a name="removing-a-folder"></a><a name="managing_remfldr"></a><span data-ttu-id="db1e6-126">删除文件夹</span><span class="sxs-lookup"><span data-stu-id="db1e6-126">Removing a Folder</span></span>  
 <span data-ttu-id="db1e6-127">若要以编程方式删除存储文件夹，请调用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="db1e6-127">To remove a storage folder programmatically, call one of the following methods:</span></span>  
  
|<span data-ttu-id="db1e6-128">存储位置</span><span class="sxs-lookup"><span data-stu-id="db1e6-128">Storage Location</span></span>|<span data-ttu-id="db1e6-129">调用的方法</span><span class="sxs-lookup"><span data-stu-id="db1e6-129">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="db1e6-130">SSIS 包存储区</span><span class="sxs-lookup"><span data-stu-id="db1e6-130">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromSqlServer%2A>|  
  
  
  
###  <a name="renaming-a-folder"></a><a name="managing_rename"></a><span data-ttu-id="db1e6-131">重命名文件夹</span><span class="sxs-lookup"><span data-stu-id="db1e6-131">Renaming a Folder</span></span>  
 <span data-ttu-id="db1e6-132">若要以编程方式重命名存储文件夹，请调用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="db1e6-132">To rename a storage folder programmatically, call one of the following methods:</span></span>  
  
|<span data-ttu-id="db1e6-133">存储位置</span><span class="sxs-lookup"><span data-stu-id="db1e6-133">Storage Location</span></span>|<span data-ttu-id="db1e6-134">调用的方法</span><span class="sxs-lookup"><span data-stu-id="db1e6-134">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="db1e6-135">SSIS 包存储区</span><span class="sxs-lookup"><span data-stu-id="db1e6-135">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnSqlServer%2A>|  
  

  
<span data-ttu-id="db1e6-136">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="db1e6-136">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="db1e6-137">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="db1e6-137">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="db1e6-138">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="db1e6-138">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="db1e6-139">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="db1e6-139">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db1e6-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="db1e6-140">See Also</span></span>  
 <span data-ttu-id="db1e6-141">[包管理 &#40;SSIS 服务&#41;](../service/package-management-ssis-service.md) </span><span class="sxs-lookup"><span data-stu-id="db1e6-141">[Package Management &#40;SSIS Service&#41;](../service/package-management-ssis-service.md) </span></span>  
 [<span data-ttu-id="db1e6-142">以编程方式枚举可用的包</span><span class="sxs-lookup"><span data-stu-id="db1e6-142">Enumerating Available Packages Programmatically</span></span>](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
  
  
