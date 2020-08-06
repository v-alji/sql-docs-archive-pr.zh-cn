---
title: 在 SSIS 包升级向导) 选择源位置 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectsourcelocation.f1
ms.assetid: 429f146e-edb4-4401-a225-f2c8468971c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e24eec77dc87a6215f9d686cf5af964cc244d68d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682938"
---
# <a name="select-source-location-ssis-package-upgrade-wizard"></a><span data-ttu-id="d8bfe-102">选择源位置（SSIS 包升级向导）</span><span class="sxs-lookup"><span data-stu-id="d8bfe-102">Select Source Location (SSIS Package Upgrade Wizard)</span></span>
  <span data-ttu-id="d8bfe-103">使用 **“选择源位置”** 页可指定从中升级包的源。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-103">Use the **Select Source Location** page to specify the source from which to upgrade packages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d8bfe-104">仅当通过 [!INCLUDE[ssIS](../includes/ssis-md.md)] 或命令提示符运行 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 包升级向导时，此页才可用。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-104">This page is only available when you run the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or at the command prompt.</span></span>  
  
 <span data-ttu-id="d8bfe-105">**运行 SSIS 包升级向导**</span><span class="sxs-lookup"><span data-stu-id="d8bfe-105">**To run the SSIS Package Upgrade Wizard**</span></span>  
  
-   [<span data-ttu-id="d8bfe-106">使用 SSIS 包升级向导升级 Integration Services 包</span><span class="sxs-lookup"><span data-stu-id="d8bfe-106">Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard</span></span>](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="static-options"></a><span data-ttu-id="d8bfe-107">静态选项</span><span class="sxs-lookup"><span data-stu-id="d8bfe-107">Static Options</span></span>  
 <span data-ttu-id="d8bfe-108">**包源**</span><span class="sxs-lookup"><span data-stu-id="d8bfe-108">**Package source**</span></span>  
 <span data-ttu-id="d8bfe-109">选择包含要升级包的存储位置。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-109">Select the storage location that contains the packages to be upgraded.</span></span> <span data-ttu-id="d8bfe-110">此选项具有下表所列的值。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-110">This option has the values listed in the following table.</span></span>  
  
|<span data-ttu-id="d8bfe-111">值</span><span class="sxs-lookup"><span data-stu-id="d8bfe-111">Value</span></span>|<span data-ttu-id="d8bfe-112">说明</span><span class="sxs-lookup"><span data-stu-id="d8bfe-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d8bfe-113">**文件系统**</span><span class="sxs-lookup"><span data-stu-id="d8bfe-113">**File System**</span></span>|<span data-ttu-id="d8bfe-114">指示要升级的包位于本地计算机上的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-114">Indicates that the packages to be upgraded are in a folder on the local computer.</span></span><br /><br /> <span data-ttu-id="d8bfe-115">若要使向导在升级这些包前备份原始包，必须在文件系统中必须存储原始包。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-115">To have the wizard back up the original packages before upgrading those packages, the original packages must be stored in the file system.</span></span> <span data-ttu-id="d8bfe-116">有关详细信息，请参阅操作指南主题。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-116">For more information, see How To Topic.</span></span>|  
|<span data-ttu-id="d8bfe-117">**SSIS 包存储区**</span><span class="sxs-lookup"><span data-stu-id="d8bfe-117">**SSIS Package Store**</span></span>|<span data-ttu-id="d8bfe-118">指示要升级的包位于包存储区中。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-118">Indicates that the packages to be upgraded are in the package store.</span></span> <span data-ttu-id="d8bfe-119">包存储区由一组 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务管理的系统文件夹组成。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-119">The package store consists of the set of file system folders that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service manages.</span></span> <span data-ttu-id="d8bfe-120">有关详细信息，请参阅[包管理（SSIS 服务）](service/package-management-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-120">For more information, see [Package Management &#40;SSIS Service&#41;](service/package-management-ssis-service.md).</span></span><br /><br /> <span data-ttu-id="d8bfe-121">选择此值将显示相应的动态选项 **Package source** 。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-121">Selecting this value displays the corresponding **Package source** dynamic options.</span></span>|  
|<span data-ttu-id="d8bfe-122">**Microsoft SQL Server**</span><span class="sxs-lookup"><span data-stu-id="d8bfe-122">**Microsoft SQL Server**</span></span>|<span data-ttu-id="d8bfe-123">指示要升级的包来自 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的现有实例。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-123">Indicates the packages to be upgraded are from an existing instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="d8bfe-124">选择此值将显示相应的动态选项 **Package source** 。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-124">Selecting this value displays the corresponding **Package source** dynamic options.</span></span>|  
  
 <span data-ttu-id="d8bfe-125">**文件夹**</span><span class="sxs-lookup"><span data-stu-id="d8bfe-125">**Folder**</span></span>  
 <span data-ttu-id="d8bfe-126">键入要升级的包所在的文件夹名称或单击“浏览”\*\*\*\* 找到该文件夹。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-126">Type the name of a folder that contains the packages you want to upgrade or click **Browse** and locate the folder.</span></span>  
  
 <span data-ttu-id="d8bfe-127">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="d8bfe-127">**Browse**</span></span>  
 <span data-ttu-id="d8bfe-128">浏览找到要升级的包所在的文件夹。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-128">Browse to locate the folder that contains the packages you want to upgrade.</span></span>  
  
## <a name="package-source-dynamic-options"></a><span data-ttu-id="d8bfe-129">包源动态选项</span><span class="sxs-lookup"><span data-stu-id="d8bfe-129">Package Source Dynamic Options</span></span>  
  
### <a name="package-source--ssis-package-store"></a><span data-ttu-id="d8bfe-130">包源 = SSIS 包存储区</span><span class="sxs-lookup"><span data-stu-id="d8bfe-130">Package source = SSIS Package Store</span></span>  
 <span data-ttu-id="d8bfe-131">**Server**</span><span class="sxs-lookup"><span data-stu-id="d8bfe-131">**Server**</span></span>  
 <span data-ttu-id="d8bfe-132">键入要升级的包所在的服务器的名称，或在列表中选择此服务器。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-132">Type the name of the server that has the packages to be upgraded, or select this server in the list.</span></span>  
  
### <a name="package-source--microsoft-sql-server"></a><span data-ttu-id="d8bfe-133">包源 = Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="d8bfe-133">Package source = Microsoft SQL Server</span></span>  
 <span data-ttu-id="d8bfe-134">**Server**</span><span class="sxs-lookup"><span data-stu-id="d8bfe-134">**Server**</span></span>  
 <span data-ttu-id="d8bfe-135">键入要升级的包所在的服务器的名称，或从列表中选择此服务器。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-135">Type the name of the server that has the packages to be upgraded, or select this server from the list.</span></span>  
  
 <span data-ttu-id="d8bfe-136">**使用 Windows 身份验证**</span><span class="sxs-lookup"><span data-stu-id="d8bfe-136">**Use Windows authentication**</span></span>  
 <span data-ttu-id="d8bfe-137">选择此选项可以使用 Windows 身份验证连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-137">Select to use Windows Authentication to connect to the server.</span></span>  
  
 <span data-ttu-id="d8bfe-138">**使用 SQL Server 身份验证**</span><span class="sxs-lookup"><span data-stu-id="d8bfe-138">**Use SQL Server authentication**</span></span>  
 <span data-ttu-id="d8bfe-139">选择此选项可以使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-139">Select to use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to connect to the server.</span></span> <span data-ttu-id="d8bfe-140">如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证，则必须提供用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-140">If you use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, you must provide a user name and password.</span></span>  
  
 <span data-ttu-id="d8bfe-141">**用户名**</span><span class="sxs-lookup"><span data-stu-id="d8bfe-141">**User name**</span></span>  
 <span data-ttu-id="d8bfe-142">键入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证用于连接到服务器的用户名。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-142">Type the user name that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication will use to connect to the server.</span></span>  
  
 <span data-ttu-id="d8bfe-143">**密码**</span><span class="sxs-lookup"><span data-stu-id="d8bfe-143">**Password**</span></span>  
 <span data-ttu-id="d8bfe-144">键入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证用于连接到服务器的密码。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-144">Type the password that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication will use to connect to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8bfe-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d8bfe-145">See Also</span></span>  
 [<span data-ttu-id="d8bfe-146">升级 Integration Services 包</span><span class="sxs-lookup"><span data-stu-id="d8bfe-146">Upgrade Integration Services Packages</span></span>](install-windows/upgrade-integration-services-packages.md)  
  
  
