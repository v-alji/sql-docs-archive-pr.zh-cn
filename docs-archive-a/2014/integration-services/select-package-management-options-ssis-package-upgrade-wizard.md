---
title: 选择 "SSIS 包升级向导" (包管理选项) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectpackagemgtoptions.f1
ms.assetid: 810fc020-51cd-43ed-9f35-af99b4f35947
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b5113ad5a1f6758a75742ca58aef04ce92168649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591468"
---
# <a name="select-package-management-options-ssis-package-upgrade-wizard"></a><span data-ttu-id="76965-102">选择包管理选项（SSIS 包升级向导）</span><span class="sxs-lookup"><span data-stu-id="76965-102">Select Package Management Options (SSIS Package Upgrade Wizard)</span></span>
  <span data-ttu-id="76965-103">使用 **“选择包管理选项”** 页指定用于对包进行升级的选项。</span><span class="sxs-lookup"><span data-stu-id="76965-103">Use the **Select Package Management Options** page to specify options for upgrading packages.</span></span>  
  
 <span data-ttu-id="76965-104">**运行 SSIS 包升级向导**</span><span class="sxs-lookup"><span data-stu-id="76965-104">**To run the SSIS Package Upgrade Wizard**</span></span>  
  
-   [<span data-ttu-id="76965-105">使用 SSIS 包升级向导升级 Integration Services 包</span><span class="sxs-lookup"><span data-stu-id="76965-105">Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard</span></span>](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="76965-106">选项</span><span class="sxs-lookup"><span data-stu-id="76965-106">Options</span></span>  
 <span data-ttu-id="76965-107">**更新连接字符串以使用新的提供程序名称**</span><span class="sxs-lookup"><span data-stu-id="76965-107">**Update connection strings to use new provider names**</span></span>  
 <span data-ttu-id="76965-108">更新连接字符串以使用当前版本的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]的下列提供程序的名称：</span><span class="sxs-lookup"><span data-stu-id="76965-108">Update the connection strings to use the names for the following providers for the current release of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="76965-109">用于 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的 OLE DB 提供程序</span><span class="sxs-lookup"><span data-stu-id="76965-109">OLE DB Provider for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="76965-110">Native Client</span><span class="sxs-lookup"><span data-stu-id="76965-110">Native Client</span></span>  
  
 <span data-ttu-id="76965-111">[!INCLUDE[ssIS](../includes/ssis-md.md)] 包升级向导仅更新存储在连接管理器中的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="76965-111">The [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard updates only connection strings that are stored in connection managers.</span></span> <span data-ttu-id="76965-112">向导不会更新通过使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 表达式语言或在脚本任务中使用代码动态构造的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="76965-112">The wizard does not update connection strings that are constructed dynamically by using the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] expression language, or by using code in a Script task.</span></span>  
  
 <span data-ttu-id="76965-113">**验证升级包**</span><span class="sxs-lookup"><span data-stu-id="76965-113">**Validate upgrade packages**</span></span>  
 <span data-ttu-id="76965-114">验证升级包，并仅保存通过验证的升级包。</span><span class="sxs-lookup"><span data-stu-id="76965-114">Validate the upgrade packages and save only those upgrade packages that pass validation.</span></span>  
  
 <span data-ttu-id="76965-115">如果未选择此选项，则向导将不会验证升级包。</span><span class="sxs-lookup"><span data-stu-id="76965-115">If you do not select this option, the wizard will not validate upgrade packages.</span></span> <span data-ttu-id="76965-116">因此，向导将保存所有升级包，不论包是否有效。</span><span class="sxs-lookup"><span data-stu-id="76965-116">Therefore, the wizard will save all upgrade packages, regardless of whether the packages are valid or not.</span></span> <span data-ttu-id="76965-117">向导会将升级包保存到在向导的“选择目标位置”\*\*\*\* 页上指定的目标。</span><span class="sxs-lookup"><span data-stu-id="76965-117">The wizard saves upgrade packages to the destination that is specified on the **SelectDestination Location** page of the wizard.</span></span>  
  
 <span data-ttu-id="76965-118">验证会延长升级过程的时间。</span><span class="sxs-lookup"><span data-stu-id="76965-118">Validation adds time to the upgrade process.</span></span> <span data-ttu-id="76965-119">对于可能成功升级的大型包，建议不要选择此选项。</span><span class="sxs-lookup"><span data-stu-id="76965-119">We recommend that you do not select this option for large packages that are likely to be upgraded successfully.</span></span>  
  
 <span data-ttu-id="76965-120">**创建新的包 ID**</span><span class="sxs-lookup"><span data-stu-id="76965-120">**Create new package IDs**</span></span>  
 <span data-ttu-id="76965-121">为升级包创建新的包 ID。</span><span class="sxs-lookup"><span data-stu-id="76965-121">Create new package IDs for the upgrade packages.</span></span>  
  
 <span data-ttu-id="76965-122">**包升级失败时继续执行升级过程**</span><span class="sxs-lookup"><span data-stu-id="76965-122">**Continue upgrade process when a package upgrade fails**</span></span>  
 <span data-ttu-id="76965-123">指定当无法升级某个包时 [!INCLUDE[ssIS](../includes/ssis-md.md)] 包升级向导继续升级剩余包。</span><span class="sxs-lookup"><span data-stu-id="76965-123">Specify that when a package cannot be upgraded, the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard continues to upgrade the remaining packages.</span></span>  
  
 <span data-ttu-id="76965-124">**包名称冲突**</span><span class="sxs-lookup"><span data-stu-id="76965-124">**Package name conflicts**</span></span>  
 <span data-ttu-id="76965-125">指定向导应如何处理同名的包。</span><span class="sxs-lookup"><span data-stu-id="76965-125">Specify how the wizard should handle packages that have the same name.</span></span> <span data-ttu-id="76965-126">此选项具有下表所列的值。</span><span class="sxs-lookup"><span data-stu-id="76965-126">This option has the values listed in the following table.</span></span>  
  
 <span data-ttu-id="76965-127">**覆盖现有包文件**</span><span class="sxs-lookup"><span data-stu-id="76965-127">**Overwrite existing package files**</span></span>  
 <span data-ttu-id="76965-128">使用同名的升级包替换现有包。</span><span class="sxs-lookup"><span data-stu-id="76965-128">Replaces the existing package with the upgrade package of the same name.</span></span>  
  
 <span data-ttu-id="76965-129">**添加数值后缀以升级包名称**</span><span class="sxs-lookup"><span data-stu-id="76965-129">**Add numeric suffixes to upgrade package names**</span></span>  
 <span data-ttu-id="76965-130">向升级包名称添加数值后缀。</span><span class="sxs-lookup"><span data-stu-id="76965-130">Adds a numeric suffix to the name of the upgrade package.</span></span>  
  
 <span data-ttu-id="76965-131">**不要升级包**</span><span class="sxs-lookup"><span data-stu-id="76965-131">**Do not upgrade packages**</span></span>  
 <span data-ttu-id="76965-132">停止升级包，并在完成向导时显示错误。</span><span class="sxs-lookup"><span data-stu-id="76965-132">Stops the packages from being upgraded and displays an error when you complete the wizard.</span></span>  
  
 <span data-ttu-id="76965-133">当在向导的 **“选择目标位置”** 页上选择 **“保存到源位置”** 选项时，上述选项不可用。</span><span class="sxs-lookup"><span data-stu-id="76965-133">These options are not available when you select the **Save to source location** option on the **Select Destination Location** page of the wizard.</span></span>  
  
 <span data-ttu-id="76965-134">**忽略包配置**</span><span class="sxs-lookup"><span data-stu-id="76965-134">**Ignore Configurations**</span></span>  
 <span data-ttu-id="76965-135">包在升级过程中未加载包配置。</span><span class="sxs-lookup"><span data-stu-id="76965-135">Does not load package configurations during the package upgrade.</span></span> <span data-ttu-id="76965-136">选择此选项可缩短升级程序包所需的时间。</span><span class="sxs-lookup"><span data-stu-id="76965-136">Selecting this option reduces the time required to upgrade the package.</span></span>  
  
 <span data-ttu-id="76965-137">**备份原始包**</span><span class="sxs-lookup"><span data-stu-id="76965-137">**Backup original packages**</span></span>  
 <span data-ttu-id="76965-138">使向导将原始包备份到 **SSISBackupFolder** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="76965-138">Have the wizard back up the original packages to an **SSISBackupFolder** folder.</span></span> <span data-ttu-id="76965-139">向导会创建 **SSISBackupFolder** 文件夹，将其作为包含原始包和升级包的文件夹的子文件夹。</span><span class="sxs-lookup"><span data-stu-id="76965-139">The wizard creates the **SSISBackupFolder** folder as a subfolder to the folder that contains the original packages and the upgraded packages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="76965-140">仅当指定将原始包和升级的包都存储在文件系统中且在同一文件中时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="76965-140">This option is available only when you specify that the original packages and the upgraded packages are stored in the file system and in the same folder.</span></span>  
  
 <span data-ttu-id="76965-141">有关详细信息，请参阅 [使用 SSIS 包升级向导升级 Integration Services 包](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="76965-141">For more information, see [Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76965-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="76965-142">See Also</span></span>  
 [<span data-ttu-id="76965-143">升级 Integration Services 包</span><span class="sxs-lookup"><span data-stu-id="76965-143">Upgrade Integration Services Packages</span></span>](install-windows/upgrade-integration-services-packages.md)  
  
  
