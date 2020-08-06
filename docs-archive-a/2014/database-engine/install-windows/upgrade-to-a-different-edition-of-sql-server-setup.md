---
title: 升级到 SQL Server 2014 (安装程序的不同版本) |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 31d16820-d126-4c57-82cc-27701e4091bc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ebb461118ace46000288ee800f30cf90726c465f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689018"
---
# <a name="upgrade-to-a-different-edition-of-sql-server-2014-setup"></a><span data-ttu-id="adef3-102">升级到 SQL Server 2014 的另一版本（安装）</span><span class="sxs-lookup"><span data-stu-id="adef3-102">Upgrade to a Different Edition of SQL Server 2014 (Setup)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="adef3-103">安装程序支持在各种版本的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 间进行版本升级。</span><span class="sxs-lookup"><span data-stu-id="adef3-103">Setup supports edition upgrade among various editions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="adef3-104">有关支持的版本升级路径的信息，请参阅 [支持的版本升级](supported-version-and-edition-upgrades.md)。</span><span class="sxs-lookup"><span data-stu-id="adef3-104">For information about supported edition upgrade paths, see [Supported Version and Edition Upgrades](supported-version-and-edition-upgrades.md).</span></span> <span data-ttu-id="adef3-105">在开始对 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]实例执行版本升级前，请查看以下主题：</span><span class="sxs-lookup"><span data-stu-id="adef3-105">Before you initiate the edition upgrade of an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], review the following topics:</span></span>  
  
-   [<span data-ttu-id="adef3-106">SQL Server 2014 各个版本支持的功能</span><span class="sxs-lookup"><span data-stu-id="adef3-106">Features Supported by the Editions of SQL Server 2014</span></span>](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
-   [<span data-ttu-id="adef3-107">SQL Server 2014 的版本和组件</span><span class="sxs-lookup"><span data-stu-id="adef3-107">Editions and Components of SQL Server 2014</span></span>](../../sql-server/editions-and-components-of-sql-server-2016.md)  
  
-   [<span data-ttu-id="adef3-108">按 SQL Server 版本划分的计算能力限制</span><span class="sxs-lookup"><span data-stu-id="adef3-108">Compute Capacity Limits by Edition of SQL Server</span></span>](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md)  
  
-   [<span data-ttu-id="adef3-109">安装 SQL Server 2014 的硬件和软件要求</span><span class="sxs-lookup"><span data-stu-id="adef3-109">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
> [!NOTE]  
>  <span data-ttu-id="adef3-110">\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在群集环境中：\*\* 在群集的一个节点上运行版本升级 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 就足够了。</span><span class="sxs-lookup"><span data-stu-id="adef3-110">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a clustered environment:** Running edition upgrade on one of the nodes of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cluster is sufficient.</span></span> <span data-ttu-id="adef3-111">此节点可以是活动节点或被动节点，并且在版本升级过程中引擎不使资源脱机。</span><span class="sxs-lookup"><span data-stu-id="adef3-111">This node can be either active or passive, and the engine does not bring the resources offline during the Edition Upgrade.</span></span> <span data-ttu-id="adef3-112">版本升级后需要重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例或故障转移到其他节点。</span><span class="sxs-lookup"><span data-stu-id="adef3-112">After the edition upgrade it is required to either restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance or failover to a different node.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="adef3-113">先决条件</span><span class="sxs-lookup"><span data-stu-id="adef3-113">Prerequisites</span></span>  
 <span data-ttu-id="adef3-114">对于本地安装，必须以管理员身份运行安装程序。</span><span class="sxs-lookup"><span data-stu-id="adef3-114">For local installations, you must run Setup as an administrator.</span></span> <span data-ttu-id="adef3-115">如果从远程共享安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，则必须使用对远程共享具有读取权限的域帐户。</span><span class="sxs-lookup"><span data-stu-id="adef3-115">If you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a remote share, you must use a domain account that has read permissions on the remote share.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="adef3-116">为了激活对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本进行的更改，必须重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="adef3-116">For the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] edition change to be activated, you must restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services.</span></span> <span data-ttu-id="adef3-117">这将导致应用程序在服务脱机时关闭。</span><span class="sxs-lookup"><span data-stu-id="adef3-117">This will result in application down time while services are offline.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="adef3-118">过程</span><span class="sxs-lookup"><span data-stu-id="adef3-118">Procedure</span></span>  
  
#### <a name="to-upgrade-to-a-different-edition-of-sscurrent"></a><span data-ttu-id="adef3-119">升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的另一版本</span><span class="sxs-lookup"><span data-stu-id="adef3-119">To upgrade to a different edition of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]</span></span>  
  
1.  <span data-ttu-id="adef3-120">插入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装介质，</span><span class="sxs-lookup"><span data-stu-id="adef3-120">Insert the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation media.</span></span> <span data-ttu-id="adef3-121">在根文件夹中，双击 setup.exe 或者从配置工具中启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装中心。</span><span class="sxs-lookup"><span data-stu-id="adef3-121">From the root folder, double-click setup.exe or launch the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Center from Configuration Tools.</span></span> <span data-ttu-id="adef3-122">若要从网络共享进行安装，请找到共享中的根文件夹，然后双击 Setup.exe。</span><span class="sxs-lookup"><span data-stu-id="adef3-122">To install from a network share, locate the root folder on the share, and then double-click Setup.exe.</span></span>  
  
2.  <span data-ttu-id="adef3-123">若要将 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的现有实例升级到另一版本，请在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装中心中单击 **“维护”** ，然后选择 **“版本升级”** 。</span><span class="sxs-lookup"><span data-stu-id="adef3-123">To upgrade an existing instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to a different edition, from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Center click **Maintenance**, and then select **Edition Upgrade**.</span></span>  
  
3.  <span data-ttu-id="adef3-124">如果需要使用安装程序支持文件， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序将安装它们。</span><span class="sxs-lookup"><span data-stu-id="adef3-124">If Setup support files are required, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup installs them.</span></span> <span data-ttu-id="adef3-125">如果安装程序指示您重新启动计算机，请在继续操作之前重新启动。</span><span class="sxs-lookup"><span data-stu-id="adef3-125">If you are instructed to restart your computer, restart before you continue.</span></span>  
  
4.  <span data-ttu-id="adef3-126">系统配置检查器将在您的计算机上运行发现操作。</span><span class="sxs-lookup"><span data-stu-id="adef3-126">The System Configuration Checker runs a discovery operation on your computer.</span></span> <span data-ttu-id="adef3-127">若要继续，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="adef3-127">To continue, click **OK**.</span></span>  
  
5.  <span data-ttu-id="adef3-128">在“产品密钥”页上，选择相应的单选按钮，这些按钮指示您是升级到免费版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，还是您拥有该产品生产版本的 PID 密钥。</span><span class="sxs-lookup"><span data-stu-id="adef3-128">On the Product Key page, select a radio button to indicate whether you are upgrading to a free edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or whether you have a PID key for a production version of the product.</span></span> <span data-ttu-id="adef3-129">有关详细信息，请参阅[SQL Server 2014 的版本和组件](../../sql-server/editions-and-components-of-sql-server-2016.md)和[支持的版本和版本升级](supported-version-and-edition-upgrades.md)。</span><span class="sxs-lookup"><span data-stu-id="adef3-129">For more information, see [Editions and Components of SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md) and [Supported Version and Edition Upgrades](supported-version-and-edition-upgrades.md).</span></span>  
  
6.  <span data-ttu-id="adef3-130">在“许可条款”页上阅读许可协议，然后选中相应的复选框以接受许可条款和条件。</span><span class="sxs-lookup"><span data-stu-id="adef3-130">On the License Terms page, read the license agreement, and then select the check box to accept the licensing terms and conditions.</span></span> <span data-ttu-id="adef3-131">若要继续，请单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="adef3-131">To continue, click **Next**.</span></span> <span data-ttu-id="adef3-132">若要结束安装程序，请单击 **“取消”** 。</span><span class="sxs-lookup"><span data-stu-id="adef3-132">To end Setup, click **Cancel**.</span></span>  
  
7.  <span data-ttu-id="adef3-133">在“选择实例”页上指定要升级的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="adef3-133">On the Select Instance page, specify the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to upgrade.</span></span>  
  
8.  <span data-ttu-id="adef3-134">在版本升级操作开始之前，“版本升级规则”页会验证您的计算机配置。</span><span class="sxs-lookup"><span data-stu-id="adef3-134">The Edition Upgrade Rules page validates your computer configuration before the edition upgrade operation begins.</span></span>  
  
9. <span data-ttu-id="adef3-135">“准备升级版本”页显示您在安装过程中指定的安装选项的树视图。</span><span class="sxs-lookup"><span data-stu-id="adef3-135">The Ready to Upgrade Edition page shows a tree view of installation options that were specified during Setup.</span></span> <span data-ttu-id="adef3-136">若要继续，请单击 **“升级”** 。</span><span class="sxs-lookup"><span data-stu-id="adef3-136">To continue, click **Upgrade**.</span></span>  
  
10. <span data-ttu-id="adef3-137">在版本升级过程中，需要重新启动服务以便接受新设置。</span><span class="sxs-lookup"><span data-stu-id="adef3-137">During the edition upgrade process, the services need to be restarted to pick up the new setting.</span></span> <span data-ttu-id="adef3-138">版本升级完成后，“完成”页会提供指向版本升级摘要日志文件的链接。</span><span class="sxs-lookup"><span data-stu-id="adef3-138">After edition upgrade, the Complete page provides a link to the summary log file for the edition upgrade.</span></span> <span data-ttu-id="adef3-139">若要关闭该向导，请单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="adef3-139">To close the wizard, click **Close**.</span></span>  
  
11. <span data-ttu-id="adef3-140">“完成”页会提供指向安装日志文件摘要以及其他重要说明的链接。</span><span class="sxs-lookup"><span data-stu-id="adef3-140">The Complete page provides a link to the summary log file for the installation and other important notes.</span></span>  
  
12. <span data-ttu-id="adef3-141">如果安装程序指示您重新启动计算机，请立即重新启动。</span><span class="sxs-lookup"><span data-stu-id="adef3-141">If you are instructed to restart the computer, do so now.</span></span> <span data-ttu-id="adef3-142">安装完成后，请务必阅读来自安装向导的消息。</span><span class="sxs-lookup"><span data-stu-id="adef3-142">It is important to read the message from the Installation Wizard when you are done with Setup.</span></span> <span data-ttu-id="adef3-143">有关安装程序日志文件的信息，请参阅 [查看和阅读 SQL Server 安装程序日志文件](view-and-read-sql-server-setup-log-files.md)。</span><span class="sxs-lookup"><span data-stu-id="adef3-143">For information about Setup log files, see [View and Read SQL Server Setup Log Files](view-and-read-sql-server-setup-log-files.md).</span></span>  
  
13. <span data-ttu-id="adef3-144">如果是从 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]进行的升级，则必须执行以下附加步骤才能使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的升级实例：</span><span class="sxs-lookup"><span data-stu-id="adef3-144">If you upgraded from [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], you must perform additional steps before you can use your upgraded instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
    -   <span data-ttu-id="adef3-145">在 Windows SCM 中启用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服务。</span><span class="sxs-lookup"><span data-stu-id="adef3-145">Enable the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service in Windows SCM.</span></span>  
  
    -   <span data-ttu-id="adef3-146">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服务帐户。</span><span class="sxs-lookup"><span data-stu-id="adef3-146">Provision the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
 <span data-ttu-id="adef3-147">如果是从 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]升级，除了执行上面的步骤外，您可能还需要执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="adef3-147">In addition to the steps above, you may need to do the following if you upgraded from [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]:</span></span>  
  
-   <span data-ttu-id="adef3-148">升级之后，在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 中设置的用户将保持其原有的设置。</span><span class="sxs-lookup"><span data-stu-id="adef3-148">Users that were provisioned in [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] remain provisioned after the upgrade.</span></span> <span data-ttu-id="adef3-149">具体而言，BUILTIN\Users 组将保持其原有的设置。</span><span class="sxs-lookup"><span data-stu-id="adef3-149">Specifically, the BUILTIN\Users group remains provisioned.</span></span> <span data-ttu-id="adef3-150">可以根据需要禁用、删除或重新设置这些帐户。</span><span class="sxs-lookup"><span data-stu-id="adef3-150">Disable, remove, or reprovision these accounts as needed.</span></span> <span data-ttu-id="adef3-151">有关详细信息，请参阅 [配置 Windows 服务帐户和权限](../configure-windows/configure-windows-service-accounts-and-permissions.md)预览版本升级问题的解答。</span><span class="sxs-lookup"><span data-stu-id="adef3-151">For more information, see [Configure Windows Service Accounts and Permissions](../configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
-   <span data-ttu-id="adef3-152">升级之后，tempdb 和 model 系统数据库的大小和恢复模式保持不变。</span><span class="sxs-lookup"><span data-stu-id="adef3-152">Sizes and recovery mode for the tempdb and model system databases remain unchanged after the upgrade.</span></span> <span data-ttu-id="adef3-153">可以根据需要重新配置这些设置。</span><span class="sxs-lookup"><span data-stu-id="adef3-153">Reconfigure these settings as needed.</span></span> <span data-ttu-id="adef3-154">有关详细信息，请参阅[备份和还原系统数据库 (SQL Server)](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="adef3-154">For more information, see [Back Up and Restore of System Databases &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md).</span></span>  
  
-   <span data-ttu-id="adef3-155">升级之后，模板数据库保留在计算机上。</span><span class="sxs-lookup"><span data-stu-id="adef3-155">Template databases remain on the computer after the upgrade.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adef3-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="adef3-156">See Also</span></span>  
 <span data-ttu-id="adef3-157">[升级到 SQL Server 2014](upgrade-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="adef3-157">[Upgrade to SQL Server 2014](upgrade-sql-server.md) </span></span>  
 [<span data-ttu-id="adef3-158">向后兼容性</span><span class="sxs-lookup"><span data-stu-id="adef3-158">Backward Compatibility</span></span>](../../getting-started/backward-compatibility.md)  
  
  
