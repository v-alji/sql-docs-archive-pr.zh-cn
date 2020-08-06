---
title: 使用 SSIS 包升级向导升级 Integration Services 包 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, upgrading
- upgrading Integration Services packages
ms.assetid: 9359275a-48f5-4d1e-8ae7-e797759e3ccf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bcafd1c9750d8333639ca2d315512a2c2b8759c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586886"
---
# <a name="upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard"></a><span data-ttu-id="d7343-102">使用 SSIS 包升级向导升级 Integration Services 包</span><span class="sxs-lookup"><span data-stu-id="d7343-102">Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard</span></span>
  <span data-ttu-id="d7343-103">您可以将在早期版本的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中创建的包升级为 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 使用的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 格式。</span><span class="sxs-lookup"><span data-stu-id="d7343-103">You can upgrade packages that were created in earlier versions of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] format that [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] uses.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d7343-104">提供了 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包升级向导来帮助完成此过程。</span><span class="sxs-lookup"><span data-stu-id="d7343-104">provides the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard to help in this process.</span></span> <span data-ttu-id="d7343-105">由于可以将该向导配置为备份原始包，因此如果您遇到升级困难，可以继续使用这些原始包。</span><span class="sxs-lookup"><span data-stu-id="d7343-105">Because you can configure the wizard to backup up your original packages, you can continue to use the original packages if you experience upgrade difficulties.</span></span>  
  
 <span data-ttu-id="d7343-106">安装 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 时，将安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包升级向导。</span><span class="sxs-lookup"><span data-stu-id="d7343-106">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard is installed when [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is installed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d7343-107">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 的 Standard Edition、Enterprise Edition 和 Developer Edition 提供了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]包升级向导。</span><span class="sxs-lookup"><span data-stu-id="d7343-107">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard is available in the Standard, Enterprise, and Developer Editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d7343-108">有关如何升级 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的详细信息，请参阅 [升级 Integration Services 包](upgrade-integration-services-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="d7343-108">For more information about how to upgrade [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, see [Upgrade Integration Services Packages](upgrade-integration-services-packages.md).</span></span>  
  
 <span data-ttu-id="d7343-109">本主题的其余部分介绍了如何运行向导和备份原始包。</span><span class="sxs-lookup"><span data-stu-id="d7343-109">The remainder of this topic describes how to run the wizard and back up the original packages.</span></span>  
  
## <a name="running-the-ssis-package-upgrade-wizard"></a><span data-ttu-id="d7343-110">运行 SSIS 包升级向导</span><span class="sxs-lookup"><span data-stu-id="d7343-110">Running the SSIS Package Upgrade Wizard</span></span>  
 <span data-ttu-id="d7343-111">您可以从 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]或在命令提示符下运行 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]包升级向导。</span><span class="sxs-lookup"><span data-stu-id="d7343-111">You can run the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard from [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or at the command prompt.</span></span>  
  
#### <a name="to-run-the-wizard-from-sql-server-data-tools"></a><span data-ttu-id="d7343-112">从 SQL Server Data Tools 运行向导</span><span class="sxs-lookup"><span data-stu-id="d7343-112">To run the wizard from SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="d7343-113">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，创建或打开一个 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="d7343-113">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], create or open an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="d7343-114">在解决方案资源管理器中，右键单击“SSIS 包”  节点，然后单击“升级所有包”  来升级该节点下的所有包。</span><span class="sxs-lookup"><span data-stu-id="d7343-114">In Solution Explorer, right-click the **SSIS Packages** node, and then click **Upgrade All Packages** to upgrade all the packages under this node.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d7343-115">打开包含[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 或 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] 包的 [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] 项目时，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 将自动打开 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包升级向导。</span><span class="sxs-lookup"><span data-stu-id="d7343-115">When you open an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] or [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] packages, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] automatically opens the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard.</span></span>  
  
#### <a name="to-run-the-wizard-from-sql-server-management-studio"></a><span data-ttu-id="d7343-116">从 SQL Server Management Studio 运行向导</span><span class="sxs-lookup"><span data-stu-id="d7343-116">To run the wizard from SQL Server Management Studio</span></span>  
  
-   <span data-ttu-id="d7343-117">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，连接到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]，展开“已存储的包”  节点，接着右键单击“文件系统”  节点或“MSDB”  节点，然后单击“升级包”  。</span><span class="sxs-lookup"><span data-stu-id="d7343-117">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], expand the **Stored Packages** node, and right-click the **File System** or **MSDB** node, and then click **Upgrade Packages**.</span></span>  
  
#### <a name="to-run-the-wizard-at-the-command-prompt"></a><span data-ttu-id="d7343-118">在命令提示符下运行向导</span><span class="sxs-lookup"><span data-stu-id="d7343-118">To run the wizard at the command prompt</span></span>  
  
-   <span data-ttu-id="d7343-119">在命令提示符处，运行**C:\Program FILES\MICROSOFT SQL Server\120\DTS\Binn**文件夹中的 SSISUpgrade.exe 文件。</span><span class="sxs-lookup"><span data-stu-id="d7343-119">At the command prompt, run the SSISUpgrade.exe file from the **C:\Program Files\Microsoft SQL Server\120\DTS\Binn** folder.</span></span>  
  
## <a name="backing-up-the-original-packages"></a><span data-ttu-id="d7343-120">备份原始包</span><span class="sxs-lookup"><span data-stu-id="d7343-120">Backing Up the Original Packages</span></span>  
 <span data-ttu-id="d7343-121">若要备份原始包，必须将原始包和已升级包存储在文件系统的同一文件夹中。</span><span class="sxs-lookup"><span data-stu-id="d7343-121">To back up the original packages, both the original packages and the upgraded packages must be stored in the same folder in the file system.</span></span> <span data-ttu-id="d7343-122">根据向导的运行方式，可以自动选择该存储位置。</span><span class="sxs-lookup"><span data-stu-id="d7343-122">Depending on how you run the wizard, this storage location might be automatically selected.</span></span>  
  
-   <span data-ttu-id="d7343-123">从 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 运行 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]包升级向导时，该向导会自动将原始包和已升级包存储在文件系统的同一文件夹中。</span><span class="sxs-lookup"><span data-stu-id="d7343-123">When you run the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard from [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the wizard automatically stores both the original packages and upgraded packages in the same folder in the file system.</span></span>  
  
-   <span data-ttu-id="d7343-124">从 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 或在命令提示符下运行 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 包升级向导时，可以为原始包和已升级包指定不同的存储位置。</span><span class="sxs-lookup"><span data-stu-id="d7343-124">When you run the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or at the command prompt, you can specify different storage locations for the original and upgraded packages.</span></span> <span data-ttu-id="d7343-125">若要备份原始包，请确保指定将原始包和已升级包存储在文件系统的同一文件夹中。</span><span class="sxs-lookup"><span data-stu-id="d7343-125">To back up the original packages, make sure to specify that both the original and upgraded packages are stored in the same folder in the file system.</span></span> <span data-ttu-id="d7343-126">如果指定任何其他存储选项，则向导将无法备份原始包。</span><span class="sxs-lookup"><span data-stu-id="d7343-126">If you specify any other storage options, the wizard will not be able to back up the original packages.</span></span>  
  
 <span data-ttu-id="d7343-127">向导备份原始包时，此向导将在 **SSISBackupFolder** 文件夹中存储该原始包的副本。</span><span class="sxs-lookup"><span data-stu-id="d7343-127">When the wizard backs up the original packages, the wizard stores a copy of the original packages in an **SSISBackupFolder** folder.</span></span> <span data-ttu-id="d7343-128">向导会创建此 **SSISBackupFolder** 文件夹，将其作为包含原始包和已升级包的文件夹的子文件夹。</span><span class="sxs-lookup"><span data-stu-id="d7343-128">The wizard creates this **SSISBackupFolder** folder as a subfolder to the folder that contains the original packages and the upgraded packages.</span></span>  
  
#### <a name="to-back-up-the-original-packages-in-sql-server-management-studio-or-at-the-command-prompt"></a><span data-ttu-id="d7343-129">在 SQL Server Management Studio 中或在命令提示符下备份原始包</span><span class="sxs-lookup"><span data-stu-id="d7343-129">To back up the original packages in SQL Server Management Studio or at the command prompt</span></span>  
  
1.  <span data-ttu-id="d7343-130">将原始包保存到文件系统上的某个位置。</span><span class="sxs-lookup"><span data-stu-id="d7343-130">Save the original packages to a location on the file system.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d7343-131">向导中的备份选项只能用于已存储到文件系统中的包。</span><span class="sxs-lookup"><span data-stu-id="d7343-131">The backup option in the wizard only works with packages that have been stored to the file system.</span></span>  
  
2.  <span data-ttu-id="d7343-132">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中或在命令提示符下，运行 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包升级向导。</span><span class="sxs-lookup"><span data-stu-id="d7343-132">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or at the command prompt, run the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard.</span></span>  
  
3.  <span data-ttu-id="d7343-133">在向导的 **“选择源位置”** 页上，将 **“包源”** 属性设置为 **“文件系统”** 。</span><span class="sxs-lookup"><span data-stu-id="d7343-133">On the **Select Source Location** page of the wizard, set the **Package source** property to **File System**.</span></span>  
  
4.  <span data-ttu-id="d7343-134">在向导的“选择目标位置”  页上，选择“保存到源位置”  ，从而将已升级的包保存到与原始包相同的位置。</span><span class="sxs-lookup"><span data-stu-id="d7343-134">On the **Select Destination Location** page of the wizard, select **Save to source location** tosave the upgraded packages to the same location as the original packages.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d7343-135">仅当将已升级包存储在与原始包相同的文件夹中时，向导中的备份选项才可用。</span><span class="sxs-lookup"><span data-stu-id="d7343-135">The backup option in the wizard is available only when the upgraded packages are stored in the same folder as the original packages.</span></span>  
  
5.  <span data-ttu-id="d7343-136">在向导的 **“选择包管理选项”** 页上，选择 **“备份原始包”** 选项。</span><span class="sxs-lookup"><span data-stu-id="d7343-136">On the **Select Package Management Options** page of the wizard, select the **Backup original packages** option.</span></span>  
  
#### <a name="to-back-up-the-original-packages-in-sql-server-data-tools"></a><span data-ttu-id="d7343-137">在 SQL Server Data Tools 中备份原始包</span><span class="sxs-lookup"><span data-stu-id="d7343-137">To back up the original packages in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="d7343-138">将原始包保存到文件系统上的某个位置。</span><span class="sxs-lookup"><span data-stu-id="d7343-138">Save the original packages to a location on the file system.</span></span>  
  
2.  <span data-ttu-id="d7343-139">在向导的 **“选择包管理选项”** 页上，选择 **“备份原始包”** 选项。</span><span class="sxs-lookup"><span data-stu-id="d7343-139">On the **Select Package Management Options** page of the wizard, select the **Backup original packages** option.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="d7343-140">当你在中打开或项目时，不会显示 "**备份原始包**" 选项 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ，这会自动启动向导。</span><span class="sxs-lookup"><span data-stu-id="d7343-140">The **Backup original packages** option is not displayed when you open a [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] or [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], which automatically launches the wizard.</span></span>  
  
3.  <span data-ttu-id="d7343-141">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，运行 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包升级向导。</span><span class="sxs-lookup"><span data-stu-id="d7343-141">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], run the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard.</span></span>  
  
  
