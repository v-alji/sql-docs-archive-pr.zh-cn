---
title: 在 SSIS 包升级向导) 选择目标位置 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectdestinationlocation.f1
ms.assetid: 89274a71-0ffe-4889-84df-f5a7d78459ef
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9411157434c3dbb9fb033f7b63b5e6041fd8f75d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591470"
---
# <a name="select-destination-location-ssis-package-upgrade-wizard"></a><span data-ttu-id="0c159-102">选择目标位置（SSIS 包升级向导）</span><span class="sxs-lookup"><span data-stu-id="0c159-102">Select Destination Location (SSIS Package Upgrade Wizard)</span></span>
  <span data-ttu-id="0c159-103">使用 **“选择目标位置”** 页可以指定要将升级包保存到的目标位置。</span><span class="sxs-lookup"><span data-stu-id="0c159-103">Use the **Select Destination Location** page to specify the destination to which to save the upgraded packages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0c159-104">仅当通过 [!INCLUDE[ssIS](../includes/ssis-md.md)] 或命令提示符运行 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 包升级向导时，此页才可用。</span><span class="sxs-lookup"><span data-stu-id="0c159-104">This page is only available when you run the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or at the command prompt.</span></span>  
  
 <span data-ttu-id="0c159-105">**运行 SSIS 包升级向导**</span><span class="sxs-lookup"><span data-stu-id="0c159-105">**To run the SSIS Package Upgrade Wizard**</span></span>  
  
-   [<span data-ttu-id="0c159-106">使用 SSIS 包升级向导升级 Integration Services 包</span><span class="sxs-lookup"><span data-stu-id="0c159-106">Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard</span></span>](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="static-options"></a><span data-ttu-id="0c159-107">静态选项</span><span class="sxs-lookup"><span data-stu-id="0c159-107">Static Options</span></span>  
 <span data-ttu-id="0c159-108">**保存到源位置**</span><span class="sxs-lookup"><span data-stu-id="0c159-108">**Save to source location**</span></span>  
 <span data-ttu-id="0c159-109">将升级的包保存到在向导的“选择源位置”\*\*\*\* 页上指定的位置。</span><span class="sxs-lookup"><span data-stu-id="0c159-109">Save the upgraded packages to the same location as specified on the **Select Source Location** page of the wizard.</span></span>  
  
 <span data-ttu-id="0c159-110">如果原始包存储在文件系统中，并且您希望向导备份这些包，请选择 **“保存到源位置”** 选项。</span><span class="sxs-lookup"><span data-stu-id="0c159-110">If the original packages are stored in the file system and you want the wizard to back up those packages, select the **Save to source location** option.</span></span> <span data-ttu-id="0c159-111">有关详细信息，请参阅 [使用 SSIS 包升级向导升级 Integration Services 包](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="0c159-111">For more information, see [Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md).</span></span>  
  
 <span data-ttu-id="0c159-112">**选择新的目标位置**</span><span class="sxs-lookup"><span data-stu-id="0c159-112">**Select new destination location**</span></span>  
 <span data-ttu-id="0c159-113">将升级的包保存到此页上指定的目标位置。</span><span class="sxs-lookup"><span data-stu-id="0c159-113">Save the upgraded packages to the destination location that is specified on this page.</span></span>  
  
 <span data-ttu-id="0c159-114">**包源**</span><span class="sxs-lookup"><span data-stu-id="0c159-114">**Package source**</span></span>  
 <span data-ttu-id="0c159-115">指定存储升级包的位置。</span><span class="sxs-lookup"><span data-stu-id="0c159-115">Specify where the upgrade packages are to be stored.</span></span> <span data-ttu-id="0c159-116">此选项具有下表所列的值。</span><span class="sxs-lookup"><span data-stu-id="0c159-116">This option has the values listed in the following table.</span></span>  
  
|<span data-ttu-id="0c159-117">值</span><span class="sxs-lookup"><span data-stu-id="0c159-117">Value</span></span>|<span data-ttu-id="0c159-118">说明</span><span class="sxs-lookup"><span data-stu-id="0c159-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0c159-119">**文件系统**</span><span class="sxs-lookup"><span data-stu-id="0c159-119">**File System**</span></span>|<span data-ttu-id="0c159-120">指示将升级的包将保存到本地计算机上的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="0c159-120">Indicates that the upgraded packages are to be saved to a folder on the local computer.</span></span>|  
|<span data-ttu-id="0c159-121">**SSIS 包存储区**</span><span class="sxs-lookup"><span data-stu-id="0c159-121">**SSIS Package Store**</span></span>|<span data-ttu-id="0c159-122">指示升级的包将保存到 Integration Services 包存储区中。</span><span class="sxs-lookup"><span data-stu-id="0c159-122">Indicates that the upgraded packages are to be saved to the Integration Services package store.</span></span> <span data-ttu-id="0c159-123">包存储区由一组 Integration Services 服务管理的文件系统文件夹组成。</span><span class="sxs-lookup"><span data-stu-id="0c159-123">The package store consists of the set of file system folders that the Integration Services service manages.</span></span> <span data-ttu-id="0c159-124">有关详细信息，请参阅[包管理（SSIS 服务）](service/package-management-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="0c159-124">For more information, see [Package Management &#40;SSIS Service&#41;](service/package-management-ssis-service.md).</span></span><br /><br /> <span data-ttu-id="0c159-125">选择此值将显示相应的动态选项 **“包源”** 。</span><span class="sxs-lookup"><span data-stu-id="0c159-125">Selecting this value displays the corresponding **Package source** dynamics options.</span></span>|  
|<span data-ttu-id="0c159-126">**Microsoft SQL Server**</span><span class="sxs-lookup"><span data-stu-id="0c159-126">**Microsoft SQL Server**</span></span>|<span data-ttu-id="0c159-127">指示升级的包将保存到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的现有实例中。</span><span class="sxs-lookup"><span data-stu-id="0c159-127">Indicates that the upgraded packages are to be saved to an existing instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="0c159-128">选择此值将显示相应的动态选项 **“包源”** 。</span><span class="sxs-lookup"><span data-stu-id="0c159-128">Selecting this value displays the corresponding dynamic **Package source** dynamic options.</span></span>|  
  
 <span data-ttu-id="0c159-129">**文件夹**</span><span class="sxs-lookup"><span data-stu-id="0c159-129">**Folder**</span></span>  
 <span data-ttu-id="0c159-130">键入要保存升级包的文件夹的名称，或单击“浏览”\*\*\*\* 找到该文件夹。</span><span class="sxs-lookup"><span data-stu-id="0c159-130">Type the name of a folder to which the upgraded packages will be saved, or click **Browse** and locate the folder.</span></span>  
  
 <span data-ttu-id="0c159-131">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="0c159-131">**Browse**</span></span>  
 <span data-ttu-id="0c159-132">浏览找到将保存已升级包的文件夹。</span><span class="sxs-lookup"><span data-stu-id="0c159-132">Browse to locate the folder to which the upgraded packages will be saved.</span></span>  
  
## <a name="package-source-dynamic-options"></a><span data-ttu-id="0c159-133">包源动态选项</span><span class="sxs-lookup"><span data-stu-id="0c159-133">Package Source Dynamic Options</span></span>  
  
### <a name="package-source--ssis-package-store"></a><span data-ttu-id="0c159-134">包源 = SSIS 包存储区</span><span class="sxs-lookup"><span data-stu-id="0c159-134">Package source = SSIS Package Store</span></span>  
 <span data-ttu-id="0c159-135">**Server**</span><span class="sxs-lookup"><span data-stu-id="0c159-135">**Server**</span></span>  
 <span data-ttu-id="0c159-136">键入要保存升级包的服务器的名称，或在列表中选择服务器。</span><span class="sxs-lookup"><span data-stu-id="0c159-136">Type the name of the server to which the upgrade packages will be saved, or select a server in the list.</span></span>  
  
### <a name="package-source--microsoft-sql-server"></a><span data-ttu-id="0c159-137">包源 = Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="0c159-137">Package source = Microsoft SQL Server</span></span>  
 <span data-ttu-id="0c159-138">**Server**</span><span class="sxs-lookup"><span data-stu-id="0c159-138">**Server**</span></span>  
 <span data-ttu-id="0c159-139">键入要保存升级包的服务器的名称，或在列表中选择此服务器。</span><span class="sxs-lookup"><span data-stu-id="0c159-139">Type the name of the server to which the upgrade packages will be saved, or select this server in the list.</span></span>  
  
 <span data-ttu-id="0c159-140">**使用 Windows 身份验证**</span><span class="sxs-lookup"><span data-stu-id="0c159-140">**Use Windows authentication**</span></span>  
 <span data-ttu-id="0c159-141">选择此选项可以使用 Windows 身份验证连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="0c159-141">Select to use Windows Authentication to connect to the server.</span></span>  
  
 <span data-ttu-id="0c159-142">**使用 SQL Server 身份验证**</span><span class="sxs-lookup"><span data-stu-id="0c159-142">**Use SQL Server authentication**</span></span>  
 <span data-ttu-id="0c159-143">选择此选项可以使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="0c159-143">Select to use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to connect to the server.</span></span> <span data-ttu-id="0c159-144">如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证，则必须提供用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="0c159-144">If you use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, you must provide a user name and password.</span></span>  
  
 <span data-ttu-id="0c159-145">**用户名**</span><span class="sxs-lookup"><span data-stu-id="0c159-145">**User name**</span></span>  
 <span data-ttu-id="0c159-146">键入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证连接到服务器时使用的用户名。</span><span class="sxs-lookup"><span data-stu-id="0c159-146">Type the user name to be used when using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to connect to the server.</span></span>  
  
 <span data-ttu-id="0c159-147">**密码**</span><span class="sxs-lookup"><span data-stu-id="0c159-147">**Password**</span></span>  
 <span data-ttu-id="0c159-148">键入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证连接到服务器时使用的密码。</span><span class="sxs-lookup"><span data-stu-id="0c159-148">Type the password to be used when using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to connect to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c159-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0c159-149">See Also</span></span>  
 [<span data-ttu-id="0c159-150">升级 Integration Services 包</span><span class="sxs-lookup"><span data-stu-id="0c159-150">Upgrade Integration Services Packages</span></span>](install-windows/upgrade-integration-services-packages.md)  
  
  
