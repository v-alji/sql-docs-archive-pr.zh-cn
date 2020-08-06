---
title: 使用 SysPrep 安装 SQL Server 的注意事项 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: e1792eeb-2874-4653-b20e-3063f4eb4e5d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 537bb3c55990a68f17697789953c4f15fe023434
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690030"
---
# <a name="considerations-for-installing-sql-server-using-sysprep"></a><span data-ttu-id="9de06-102">使用 SysPrep 安装 SQL Server 的注意事项</span><span class="sxs-lookup"><span data-stu-id="9de06-102">Considerations for Installing SQL Server Using SysPrep</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9de06-103">通过 SysPrep，你可以在计算机上准备 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的独立实例，以后再完成配置。</span><span class="sxs-lookup"><span data-stu-id="9de06-103">SysPrep allows you to prepare a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a computer and to complete the configuration at a later time.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9de06-104">SysPrep 提供一个两步过程来得到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的已配置独立实例。</span><span class="sxs-lookup"><span data-stu-id="9de06-104">SysPrep involves a two-step process to get to a configured stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9de06-105">这些步骤包括以下内容：</span><span class="sxs-lookup"><span data-stu-id="9de06-105">The steps include the following:</span></span>  
  
-   [<span data-ttu-id="9de06-106">准备映像</span><span class="sxs-lookup"><span data-stu-id="9de06-106">Prepare Image</span></span>](#BKMK_PrepareImage)  
  
     <span data-ttu-id="9de06-107">此步骤在安装了产品二进制文件后停止安装过程，并且不为正准备的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例配置计算机、网络或帐户特定的信息。</span><span class="sxs-lookup"><span data-stu-id="9de06-107">This step stops the installation process after the product binaries are installed, without configuring the computer, network, or account-specific information for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is being prepared.</span></span>  
  
-   [<span data-ttu-id="9de06-108">完成映像</span><span class="sxs-lookup"><span data-stu-id="9de06-108">Complete Image</span></span>](#BKMK_CompleteImage)  
  
     <span data-ttu-id="9de06-109">此步骤允许您完成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的已准备实例的配置。</span><span class="sxs-lookup"><span data-stu-id="9de06-109">This step enables you to complete the configuration of a prepared instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9de06-110">在此步骤中，您可以提供计算机、网络和帐户特定的信息。</span><span class="sxs-lookup"><span data-stu-id="9de06-110">During this step, you can provide the computer, network, and account-specific information.</span></span>  
  
 <span data-ttu-id="9de06-111">有关如何使用 SysPrep 安装的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅[使用 sysprep 安装 SQL Server 2014](install-sql-server-using-sysprep.md)。</span><span class="sxs-lookup"><span data-stu-id="9de06-111">For more information about how to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using SysPrep, see [Install SQL Server 2014 Using SysPrep](install-sql-server-using-sysprep.md).</span></span>  
  
## <a name="common-uses-for-ssnoversion-sysprep"></a><span data-ttu-id="9de06-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep 的常见用途</span><span class="sxs-lookup"><span data-stu-id="9de06-112">Common Uses for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep</span></span>  
 <span data-ttu-id="9de06-113">可以通过以下任意方式使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep 功能：</span><span class="sxs-lookup"><span data-stu-id="9de06-113">You can use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep capability in any of the following ways:</span></span>  
  
-   <span data-ttu-id="9de06-114">通过使用“准备映像”步骤，可以在同一台计算机上准备一个或多个未配置的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="9de06-114">By using the Prepare Image step, you can prepare one or more unconfigured instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the same computer.</span></span> <span data-ttu-id="9de06-115">可以在同一台计算机上使用“完成映像”步骤配置这些已准备实例。</span><span class="sxs-lookup"><span data-stu-id="9de06-115">You can configure these prepared instances by using the Complete Image step on the same computer.</span></span>  
  
-   <span data-ttu-id="9de06-116">您可以捕获已准备实例的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序配置文件，并且使用它在多台计算机上准备其他未配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，以用于以后的配置。</span><span class="sxs-lookup"><span data-stu-id="9de06-116">You can capture the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup configuration file of the prepared instance and use it to prepare additional unconfigured [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances on multiple computers for later configuration.</span></span>  
  
-   <span data-ttu-id="9de06-117">与 Windows 系统准备工具（也称为 Windows SysPrep）结合使用，您可以在源计算机上创建操作系统的一个映像（包括 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的未配置已准备实例），</span><span class="sxs-lookup"><span data-stu-id="9de06-117">In combination with the Windows System Preparation tool (also known as Windows SysPrep); you can create an image of the operating system including the unconfigured prepared instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the source computer.</span></span> <span data-ttu-id="9de06-118">然后可以将该操作系统映像部署到多台计算机。</span><span class="sxs-lookup"><span data-stu-id="9de06-118">You can then deploy the operating system image to multiple computers.</span></span> <span data-ttu-id="9de06-119">在完成操作系统的配置后，可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序的“完成映像”步骤配置已准备实例。</span><span class="sxs-lookup"><span data-stu-id="9de06-119">After you complete the configuration of the operating system, you can configure the prepared instances by using the Complete Image step of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span>  
  
     <span data-ttu-id="9de06-120">Windows SysPrep 工具用于准备 Windows 操作系统映像。</span><span class="sxs-lookup"><span data-stu-id="9de06-120">The Windows SysPrep tool is used to prepare Windows operating system images.</span></span> <span data-ttu-id="9de06-121">它用于捕获操作系统的自定义映像，以便在整个组织中部署。</span><span class="sxs-lookup"><span data-stu-id="9de06-121">It is used to capture a customized image of the operating system for deployment throughout an organization.</span></span> <span data-ttu-id="9de06-122">有关 SysPrep 及其用法的详细信息，请参阅的 [什么是 SysPrep](https://go.microsoft.com/fwlink/?LinkId=143546)。</span><span class="sxs-lookup"><span data-stu-id="9de06-122">For more information about SysPrep and its uses, see [What is SysPrep](https://go.microsoft.com/fwlink/?LinkId=143546).</span></span>  
  
## <a name="installation-media-considerations"></a><span data-ttu-id="9de06-123">安装介质注意事项</span><span class="sxs-lookup"><span data-stu-id="9de06-123">Installation Media Considerations</span></span>  
 <span data-ttu-id="9de06-124">如果您使用的是完整版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，请注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="9de06-124">If you are using a full version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consider the following:</span></span>  
  
-   <span data-ttu-id="9de06-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的 Express 以外的版本：</span><span class="sxs-lookup"><span data-stu-id="9de06-125">Non-Express editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
    -   <span data-ttu-id="9de06-126">“准备映像”步骤使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Evaluation 版本来安装产品二进制文件。</span><span class="sxs-lookup"><span data-stu-id="9de06-126">The Prepare Image step uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Evaluation edition to install the product binaries.</span></span> <span data-ttu-id="9de06-127">在完成该实例后， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的版本依赖于在“完成映像”步骤中提供的产品 ID。</span><span class="sxs-lookup"><span data-stu-id="9de06-127">When the instance is completed, the edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] depends on the product ID provided during the complete image step.</span></span>  
  
    -   <span data-ttu-id="9de06-128">如果您提供 Evaluation Edition 产品 ID，则评估期将设置为在已准备实例完成后的 180 天到期。</span><span class="sxs-lookup"><span data-stu-id="9de06-128">If you provide an Evaluation edition product ID, the evaluation period is set to expire 180 days after the prepared instance is completed.</span></span>  
  
-   <span data-ttu-id="9de06-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的 Express 版本：</span><span class="sxs-lookup"><span data-stu-id="9de06-129">Express editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
    -   <span data-ttu-id="9de06-130">若要准备 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 版本的实例，请使用 Express 安装介质。</span><span class="sxs-lookup"><span data-stu-id="9de06-130">To prepare an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express editions, use the Express installation media.</span></span>  
  
    -   <span data-ttu-id="9de06-131">不能为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 版本的已准备实例指定产品 ID。</span><span class="sxs-lookup"><span data-stu-id="9de06-131">You cannot specify Product IDs for a prepared instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express editions.</span></span>  
  
## <a name="supported-ssnoversion-installations"></a><span data-ttu-id="9de06-132">支持的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装</span><span class="sxs-lookup"><span data-stu-id="9de06-132">Supported [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installations</span></span>  
 <span data-ttu-id="9de06-133">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中的 SysPrep 支持所有功能，包括 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的工具。</span><span class="sxs-lookup"><span data-stu-id="9de06-133">SysPrep in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] supports all features, including tools, of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9de06-134">您可以为 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或早期版本的并行安装准备多个实例。</span><span class="sxs-lookup"><span data-stu-id="9de06-134">You can prepare multiple instances for side-by-side installations of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] or earlier versions.</span></span> <span data-ttu-id="9de06-135">这些实例的功能必须支持 SysPrep。</span><span class="sxs-lookup"><span data-stu-id="9de06-135">The features of these instances must support SysPrep.</span></span>  
  
 <span data-ttu-id="9de06-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 在“准备映像”步骤结束时自动安装和完成。</span><span class="sxs-lookup"><span data-stu-id="9de06-136">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is automatically installed and completed at the end of the prepare image step.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9de06-137">Browser 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Writer 在您准备 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例时自动准备。</span><span class="sxs-lookup"><span data-stu-id="9de06-137">Browser and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Writer are automatically prepared when you prepare an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9de06-138">它们在使用“完成映像”步骤完成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时完成。</span><span class="sxs-lookup"><span data-stu-id="9de06-138">They are completed when you complete the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance by using the Complete Image step.</span></span>  
  
 <span data-ttu-id="9de06-139">有关支持的版本的信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅[SQL Server 2014 的各个版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="9de06-139">For information about supported editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="9de06-140">您可以在配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的已准备实例时执行版本升级。</span><span class="sxs-lookup"><span data-stu-id="9de06-140">You can perform an edition upgrade while configuring a prepared instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9de06-141">对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 版本，不支持此选项。</span><span class="sxs-lookup"><span data-stu-id="9de06-141">This option is not supported for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express editions.</span></span>  
  
 <span data-ttu-id="9de06-142">从 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]开始， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep 支持从命令行进行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集安装。</span><span class="sxs-lookup"><span data-stu-id="9de06-142">Beginning in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep supports [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster installations from the command line.</span></span>  
  
## <a name="ssnoversion-sysprep-limitations"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9de06-143">SysPrep 限制</span><span class="sxs-lookup"><span data-stu-id="9de06-143">SysPrep Limitations</span></span>  
 <span data-ttu-id="9de06-144">不支持修复已准备实例。</span><span class="sxs-lookup"><span data-stu-id="9de06-144">Repairing a prepared instance is not supported.</span></span> <span data-ttu-id="9de06-145">如果在“准备映像”或“完成映像”步骤中安装程序失败，您必须运行卸载。</span><span class="sxs-lookup"><span data-stu-id="9de06-145">If Setup fails during the Prepare Image or Complete Image step, you must run uninstall.</span></span>  
  
##  <a name="prepare-image"></a><a name="BKMK_PrepareImage"></a> <span data-ttu-id="9de06-146">准备映像</span><span class="sxs-lookup"><span data-stu-id="9de06-146">Prepare Image</span></span>  
 <span data-ttu-id="9de06-147">“准备映像”步骤安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 产品和功能，但不配置安装。</span><span class="sxs-lookup"><span data-stu-id="9de06-147">The Prepare Image step installs the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] product and features but does not configure the installation.</span></span>  
  
 <span data-ttu-id="9de06-148">可在此步骤中指定要安装的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 产品安装文件的安装位置。</span><span class="sxs-lookup"><span data-stu-id="9de06-148">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features to be installed and the installation location for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] product installation files can be specified during this step.</span></span> <span data-ttu-id="9de06-149">你可以通过“安装中心”的“高级”页上的“SysPrep 部署的独立实例的映像准备”或从命令提示符准备 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="9de06-149">You can prepare an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] either through the **Image Preparation of a stand-alone instance for SysPrep deployment** on the **Advanced** page of the **Installation Center** or from the command prompt.</span></span>  
  
-   <span data-ttu-id="9de06-150">您可以在同一台计算机上准备可以在以后完成的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的多个实例。</span><span class="sxs-lookup"><span data-stu-id="9de06-150">You can prepare multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the same computer that can be completed later.</span></span>  
  
-   <span data-ttu-id="9de06-151">您可以从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的现有已准备实例中添加或删除 SysPrep 安装支持的功能。</span><span class="sxs-lookup"><span data-stu-id="9de06-151">You can add or remove features that are supported for SysPrep installations from the existing prepared instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9de06-152">在已准备了该实例后， **“开始”** 菜单上的快捷方式可用于完成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的已准备实例的配置。</span><span class="sxs-lookup"><span data-stu-id="9de06-152">After the instance is prepared, a shortcut on the **Start** menu becomes available to complete the configuration of the prepared instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="complete-image"></a><a name="BKMK_CompleteImage"></a> <span data-ttu-id="9de06-153">完成映像</span><span class="sxs-lookup"><span data-stu-id="9de06-153">Complete Image</span></span>  
 <span data-ttu-id="9de06-154">可以使用以下方法之一来完成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的已准备实例：</span><span class="sxs-lookup"><span data-stu-id="9de06-154">You can complete the prepared instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using either of the following methods:</span></span>  
  
-   <span data-ttu-id="9de06-155">使用“开始”菜单上的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="9de06-155">Use the shortcut on the Start menu.</span></span>  
  
-   <span data-ttu-id="9de06-156">访问“安装中心”的“高级”页上的“已准备独立实例的映像完成”步骤。</span><span class="sxs-lookup"><span data-stu-id="9de06-156">Access the **Image completion of a prepared stand-alone instance** step on the **Advanced** page of the **Installation Center**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9de06-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9de06-157">See Also</span></span>  
 [<span data-ttu-id="9de06-158">计划 SQL Server 安装</span><span class="sxs-lookup"><span data-stu-id="9de06-158">Planning a SQL Server Installation</span></span>](../../sql-server/install/planning-a-sql-server-installation.md)  
  
  
