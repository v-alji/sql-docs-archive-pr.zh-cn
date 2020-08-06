---
title: 文件夹和文件权限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- security [Master Data Services], file and folder
- folders [Master Data Services]
- files [Master Data Services]
ms.assetid: 6402d81d-7349-47b1-95ca-99b0c0f4f373
author: lrtoyou1223
ms.author: lle
robots: noindex,nofollow
ms.openlocfilehash: 6dc356e074574a4c520b1f4de2f41db0e983c4df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689489"
---
# <a name="folder-and-file-permissions-master-data-services"></a><span data-ttu-id="7a220-102">文件夹和文件权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="7a220-102">Folder and File Permissions (Master Data Services)</span></span>
  <span data-ttu-id="7a220-103">在您安装 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]时，文件夹和文件将安装在您为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 共享功能指定的安装路径处的文件系统中。</span><span class="sxs-lookup"><span data-stu-id="7a220-103">When you install [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], folders and files are installed in the file system at the installation path you specify for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] shared features.</span></span> <span data-ttu-id="7a220-104">如果你使用共享功能的默认安装路径，则的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安装路径 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 为*驱动器*： \Program Files\Microsoft SQL Server\120\Master Data Services。</span><span class="sxs-lookup"><span data-stu-id="7a220-104">If you use the default installation path for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] shared features, the installation path for [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] is *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services.</span></span> <span data-ttu-id="7a220-105">尽管您可以更改共享功能安装路径，但要注意从父文件夹继承的权限以及为 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]显式设置的权限。</span><span class="sxs-lookup"><span data-stu-id="7a220-105">Although you can change the shared features installation path, be aware of permissions that are inherited from the parent folder and permissions that are explicitly set for [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span>  
  
## <a name="inherited-permissions"></a><span data-ttu-id="7a220-106">继承的权限</span><span class="sxs-lookup"><span data-stu-id="7a220-106">Inherited Permissions</span></span>  
 <span data-ttu-id="7a220-107">**Microsoft SQL Server** 文件夹、 **Master Data Services** 文件夹以及大多数子文件夹和文件从 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安装程序中指定的父文件夹继承权限。</span><span class="sxs-lookup"><span data-stu-id="7a220-107">The **Microsoft SQL Server** folder, the **Master Data Services** folder, and most subfolders and files inherit permissions from the parent folder specified in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Setup.</span></span> <span data-ttu-id="7a220-108">如果选择默认安装位置，则继承其权限的父文件夹是驱动器\*\*:\Program Files。</span><span class="sxs-lookup"><span data-stu-id="7a220-108">If you choose the default installation location, the parent folder that permissions are inherited from is *drive*:\Program Files.</span></span> <span data-ttu-id="7a220-109">下表描述针对 **“程序文件”** 的默认权限。</span><span class="sxs-lookup"><span data-stu-id="7a220-109">The following table describes the default permissions for **Program Files**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a220-110">如果修改针对“程序文件”\*\*\*\* 的默认权限，或者选择不同的安装位置，则 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 文件夹和文件将相应继承其父文件夹的权限，并且这些权限可能不同于在下表中描述的权限。</span><span class="sxs-lookup"><span data-stu-id="7a220-110">If you modify default permissions for **Program Files**, or you choose a different installation location, the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] folders and files inherit permissions from their parent folder accordingly, and the permissions might differ from those described in the following table.</span></span>  
  
###### <a name="program-files-default-permissions"></a><span data-ttu-id="7a220-111">程序文件默认权限</span><span class="sxs-lookup"><span data-stu-id="7a220-111">Program Files Default Permissions</span></span>  
  
|<span data-ttu-id="7a220-112">组或帐户名称</span><span class="sxs-lookup"><span data-stu-id="7a220-112">Group or account name</span></span>|<span data-ttu-id="7a220-113">权限</span><span class="sxs-lookup"><span data-stu-id="7a220-113">Permissions</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="7a220-114">CREATOR OWNER</span><span class="sxs-lookup"><span data-stu-id="7a220-114">CREATOR OWNER</span></span>|<span data-ttu-id="7a220-115">特殊权限</span><span class="sxs-lookup"><span data-stu-id="7a220-115">Special permissions</span></span>|  
|<span data-ttu-id="7a220-116">SYSTEM</span><span class="sxs-lookup"><span data-stu-id="7a220-116">SYSTEM</span></span>|<span data-ttu-id="7a220-117">特殊权限</span><span class="sxs-lookup"><span data-stu-id="7a220-117">Special permissions</span></span>|  
|<span data-ttu-id="7a220-118">管理员</span><span class="sxs-lookup"><span data-stu-id="7a220-118">Administrators</span></span>|<span data-ttu-id="7a220-119">特殊权限</span><span class="sxs-lookup"><span data-stu-id="7a220-119">Special permissions</span></span>|  
|<span data-ttu-id="7a220-120">用户</span><span class="sxs-lookup"><span data-stu-id="7a220-120">Users</span></span>|<span data-ttu-id="7a220-121">读取和执行、列出文件夹内容、读取</span><span class="sxs-lookup"><span data-stu-id="7a220-121">Read & execute, List folder contents, Read</span></span>|  
|<span data-ttu-id="7a220-122">TrustedInstaller</span><span class="sxs-lookup"><span data-stu-id="7a220-122">TrustedInstaller</span></span>|<span data-ttu-id="7a220-123">列出文件夹内容、特殊权限</span><span class="sxs-lookup"><span data-stu-id="7a220-123">List folder contents, Special permissions</span></span>|  
  
## <a name="explicit-permissions"></a><span data-ttu-id="7a220-124">显式权限</span><span class="sxs-lookup"><span data-stu-id="7a220-124">Explicit Permissions</span></span>  
 <span data-ttu-id="7a220-125">**MDSTempDir** 文件夹和 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config 文件（位于 **WebApplication** 文件夹中）不继承权限。</span><span class="sxs-lookup"><span data-stu-id="7a220-125">The **MDSTempDir** folder and the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config file (in the **WebApplication** folder) do not inherit permissions.</span></span> <span data-ttu-id="7a220-126">它们具有在您安装 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]时显式设置的权限，而与您选择的安装路径无关。</span><span class="sxs-lookup"><span data-stu-id="7a220-126">They have permissions that are set explicitly when you install [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], regardless of the installation path you choose.</span></span> <span data-ttu-id="7a220-127">不要修改这些权限。</span><span class="sxs-lookup"><span data-stu-id="7a220-127">Do not modify these permissions.</span></span>  
  
###### <a name="mdstempdir-permissions"></a><span data-ttu-id="7a220-128">MDSTempDir 权限</span><span class="sxs-lookup"><span data-stu-id="7a220-128">MDSTempDir Permissions</span></span>  
  
|<span data-ttu-id="7a220-129">组或帐户名称</span><span class="sxs-lookup"><span data-stu-id="7a220-129">Group or account name</span></span>|<span data-ttu-id="7a220-130">权限</span><span class="sxs-lookup"><span data-stu-id="7a220-130">Permissions</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="7a220-131">SYSTEM</span><span class="sxs-lookup"><span data-stu-id="7a220-131">SYSTEM</span></span>|<span data-ttu-id="7a220-132">修改、读取和执行、列出文件夹内容、读取、写入</span><span class="sxs-lookup"><span data-stu-id="7a220-132">Modify, Read & execute, List folder contents, Read, Write</span></span>|  
|<span data-ttu-id="7a220-133">管理员</span><span class="sxs-lookup"><span data-stu-id="7a220-133">Administrators</span></span>|<span data-ttu-id="7a220-134">修改、读取和执行、列出文件夹内容、读取、写入</span><span class="sxs-lookup"><span data-stu-id="7a220-134">Modify, Read & execute, List folder contents, Read, Write</span></span>|  
|<span data-ttu-id="7a220-135">MDS_ServiceAccounts</span><span class="sxs-lookup"><span data-stu-id="7a220-135">MDS_ServiceAccounts</span></span>|<span data-ttu-id="7a220-136">修改、读取和执行、列出文件夹内容、读取、写入</span><span class="sxs-lookup"><span data-stu-id="7a220-136">Modify, Read & execute, List folder contents, Read, Write</span></span>|  
  
###### <a name="webconfig-permissions"></a><span data-ttu-id="7a220-137">Web.config 权限</span><span class="sxs-lookup"><span data-stu-id="7a220-137">Web.config Permissions</span></span>  
  
|<span data-ttu-id="7a220-138">组或帐户名称</span><span class="sxs-lookup"><span data-stu-id="7a220-138">Group or account name</span></span>|<span data-ttu-id="7a220-139">权限</span><span class="sxs-lookup"><span data-stu-id="7a220-139">Permissions</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="7a220-140">SYSTEM</span><span class="sxs-lookup"><span data-stu-id="7a220-140">SYSTEM</span></span>|<span data-ttu-id="7a220-141">完全控制、修改、读取和执行、读取、写入</span><span class="sxs-lookup"><span data-stu-id="7a220-141">Full control, Modify, Read & execute, Read, Write</span></span>|  
|<span data-ttu-id="7a220-142">管理员</span><span class="sxs-lookup"><span data-stu-id="7a220-142">Administrators</span></span>|<span data-ttu-id="7a220-143">完全控制、修改、读取和执行、读取、写入</span><span class="sxs-lookup"><span data-stu-id="7a220-143">Full control, Modify, Read & execute, Read, Write</span></span>|  
|<span data-ttu-id="7a220-144">MDS_ServiceAccounts</span><span class="sxs-lookup"><span data-stu-id="7a220-144">MDS_ServiceAccounts</span></span>|<span data-ttu-id="7a220-145">读取和执行、读取</span><span class="sxs-lookup"><span data-stu-id="7a220-145">Read & execute, Read</span></span>|  
  
 <span data-ttu-id="7a220-146">有关 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config 文件内容的详细信息，请参阅 [Web 配置参考 (Master Data Services)](web-configuration-reference-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7a220-146">For more information about the contents of the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config file, see [Web Configuration Reference &#40;Master Data Services&#41;](web-configuration-reference-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a220-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7a220-147">See Also</span></span>  
 [<span data-ttu-id="7a220-148">安装 Master Data Services</span><span class="sxs-lookup"><span data-stu-id="7a220-148">Install Master Data Services</span></span>](install-windows/install-master-data-services.md)  
  
  
