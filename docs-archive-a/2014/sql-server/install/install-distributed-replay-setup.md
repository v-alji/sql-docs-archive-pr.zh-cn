---
title: 安装 Distributed Replay (安装) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 64479cdc-661a-4e32-a381-8f8b5a238337
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 029737874fdab53669aab3be25b139d98d2907df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693204"
---
# <a name="install-distributed-replay-setup"></a><span data-ttu-id="3343e-102">安装 Distributed Replay（安装程序）</span><span class="sxs-lookup"><span data-stu-id="3343e-102">Install Distributed Replay (Setup)</span></span>
  <span data-ttu-id="3343e-103">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装向导安装 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Distributed Replay 功能。</span><span class="sxs-lookup"><span data-stu-id="3343e-103">Install the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay features with the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Installation Wizard.</span></span> <span data-ttu-id="3343e-104">在计划安装这些功能的位置时，请考虑以下方面：</span><span class="sxs-lookup"><span data-stu-id="3343e-104">When planning where to install the features, consider the following:</span></span>  
  
-   <span data-ttu-id="3343e-105">您可以将管理工具与 Distributed Replay 控制器安装在同一台计算机上，也可以安装在不同的计算机上。</span><span class="sxs-lookup"><span data-stu-id="3343e-105">You can install the administration tool on the same computer as the Distributed Replay controller, or on different computers.</span></span>  
  
-   <span data-ttu-id="3343e-106">在每个 Distributed Replay 环境中只能有一个控制器。</span><span class="sxs-lookup"><span data-stu-id="3343e-106">There can only be one controller in each Distributed Replay environment.</span></span>  
  
-   <span data-ttu-id="3343e-107">您可以将客户端服务最多安装在 16 个（物理或虚拟）计算机上。</span><span class="sxs-lookup"><span data-stu-id="3343e-107">You can install the client service on up to 16 (physical or virtual) computers.</span></span>  
  
-   <span data-ttu-id="3343e-108">只能有客户端服务的一个实例安装在 Distributed Replay 控制器计算机上。</span><span class="sxs-lookup"><span data-stu-id="3343e-108">Only one instance of the client service can be installed on the Distributed Replay controller computer.</span></span> <span data-ttu-id="3343e-109">如果您的 Distributed Replay 环境将具有多个客户端，我们建议不要将客户端服务与该控制器安装在同一台计算机上。</span><span class="sxs-lookup"><span data-stu-id="3343e-109">If your Distributed Replay environment will have more than one client, we do not recommend installing the client service on the same computer as the controller.</span></span> <span data-ttu-id="3343e-110">这样做可能会降低 Distributed Replay 的整体速度。</span><span class="sxs-lookup"><span data-stu-id="3343e-110">Doing so may decrease the overall speed of the distributed replay.</span></span>  
  
-   <span data-ttu-id="3343e-111">对于性能测试方案，我们建议不要将管理工具、分布式重播实用工具控制器服务或客户端服务安装在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的目标实例上。</span><span class="sxs-lookup"><span data-stu-id="3343e-111">For performance testing scenarios, we do not recommend installing the administration tool, Distributed Replay controller service, or client service on the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3343e-112">在目标服务器上安装所有这些功能应限于应用程序兼容性功能测试。</span><span class="sxs-lookup"><span data-stu-id="3343e-112">Installing all of these features on the target server should be limited to functional testing for application compatibility.</span></span>  
  
-   <span data-ttu-id="3343e-113">在安装后，控制器服务（即 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 控制器）必须首先运行，然后才能在客户端启动 Distributed Replay 客户端服务。</span><span class="sxs-lookup"><span data-stu-id="3343e-113">After installation, the controller service, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay controller, must be running before you start the Distributed Replay client service on the clients.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3343e-114">若要删除或更改 Distributed Replay 功能，请使用 **“控制面板”** 中的 Windows **“程序和功能”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="3343e-114">To remove or change the Distributed Replay features, use the Windows **Programs and Features** window in **Control Panel**.</span></span> <span data-ttu-id="3343e-115">在“卸载或更改程序” [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 窗口中选择  ，然后单击 **“删除”** 以便打开 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装向导。</span><span class="sxs-lookup"><span data-stu-id="3343e-115">Select [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in the **Uninstall or change a program** window, and then click **Remove** to open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Installation Wizard.</span></span> <span data-ttu-id="3343e-116">在 **“选择功能”** 页上，选中要删除的 Distributed Replay 功能。</span><span class="sxs-lookup"><span data-stu-id="3343e-116">On the **Select Features** page, check the Distributed Replay features you want to remove.</span></span>  
  
 <span data-ttu-id="3343e-117">**先决条件：**</span><span class="sxs-lookup"><span data-stu-id="3343e-117">**Prerequisites:**</span></span>  
  
-   <span data-ttu-id="3343e-118">请确保您要使用的计算机满足在 [Distributed Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md)主题中介绍的要求。</span><span class="sxs-lookup"><span data-stu-id="3343e-118">Make sure that the computers that you want to use meet the requirements that are described in the topic [Distributed Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md).</span></span>  
  
-   <span data-ttu-id="3343e-119">在开始此过程之前，请创建运行控制器和客户端服务所基于的域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="3343e-119">Before you begin this procedure, you create the domain user accounts that the controller and client services will run under.</span></span> <span data-ttu-id="3343e-120">我们建议这些帐户不是 Windows Administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="3343e-120">We recommend that these accounts are not members of the Windows Administrators group.</span></span> <span data-ttu-id="3343e-121">有关详细信息，请参阅 [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md) 主题中的“用户和服务帐户”部分。</span><span class="sxs-lookup"><span data-stu-id="3343e-121">For more information, see the User and Service Accounts section in the [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md) topic.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3343e-122">如果您在同一台计算机上运行管理工具、控制器服务和客户端服务，则可以使用本地用户帐户。</span><span class="sxs-lookup"><span data-stu-id="3343e-122">You can use local user accounts if you are running the administration tool, controller service, and client service on the same computer.</span></span>  
  
 <span data-ttu-id="3343e-123">**安装位置：**</span><span class="sxs-lookup"><span data-stu-id="3343e-123">**Installation Locations:**</span></span>  
  
 <span data-ttu-id="3343e-124">假定您在使用默认文件位置和标准安装，则基目录位于 C:\Program Files\Microsoft SQL Server。</span><span class="sxs-lookup"><span data-stu-id="3343e-124">Assuming you use the default file locations and a standard installation, the base directory is found at C:\Program Files\Microsoft SQL Server.</span></span> <span data-ttu-id="3343e-125">其中，下面是二进制文件和程序集将安装到的位置：</span><span class="sxs-lookup"><span data-stu-id="3343e-125">Within that, following are where the binaries and assemblies are installed to:</span></span>  
  
-   <span data-ttu-id="3343e-126">在 32 位系统上：</span><span class="sxs-lookup"><span data-stu-id="3343e-126">On a 32-bit system:</span></span>  
  
     [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]<span data-ttu-id="3343e-127">工具</span><span class="sxs-lookup"><span data-stu-id="3343e-127">Tools</span></span>  
  
     <span data-ttu-id="3343e-128">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="3343e-128">\- OR -</span></span>  
  
     <span data-ttu-id="3343e-129">\<Share Feature Directory>\Tools \\ (用户提供的替代共享功能目录) </span><span class="sxs-lookup"><span data-stu-id="3343e-129">\<Share Feature Directory>\Tools\\(user-supplied alternative shared feature directory)</span></span>  
  
-   <span data-ttu-id="3343e-130">在 64 位系统上：</span><span class="sxs-lookup"><span data-stu-id="3343e-130">On a 64-bit system:</span></span>  
  
     <span data-ttu-id="3343e-131">\\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (x86) \120\Tools 的 C:\Program 文件</span><span class="sxs-lookup"><span data-stu-id="3343e-131">C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (x86) \120\Tools</span></span>  
  
     <span data-ttu-id="3343e-132">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="3343e-132">\- OR -</span></span>  
  
     <span data-ttu-id="3343e-133">\<Share Feature Directory (x86)>\Tools \\ (用户提供的替代共享功能 (x86) 目录) </span><span class="sxs-lookup"><span data-stu-id="3343e-133">\<Share Feature Directory (x86)>\Tools\\(user-supplied alternative shared feature (x86) directory)</span></span>  
  
### <a name="to-install-distributed-replay-features"></a><span data-ttu-id="3343e-134">安装 Distributed Replay 功能</span><span class="sxs-lookup"><span data-stu-id="3343e-134">To install Distributed Replay features</span></span>  
  
1.  <span data-ttu-id="3343e-135">若要开始安装任何 Distributed Replay 功能，请启动 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装向导。</span><span class="sxs-lookup"><span data-stu-id="3343e-135">To start the installation of any of the Distributed Replay features, start the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Installation Wizard.</span></span>  
  
2.  <span data-ttu-id="3343e-136">**“安装程序支持规则”** 页将标识在安装 SQL Server 安装程序支持文件时可能发生的问题。</span><span class="sxs-lookup"><span data-stu-id="3343e-136">The **Setup Support Rules** page identifies issues that might occur when installing the SQL Server Setup support files.</span></span> <span data-ttu-id="3343e-137">在继续安装之前，您必须纠正任何安装程序支持问题。</span><span class="sxs-lookup"><span data-stu-id="3343e-137">You must correct any Setup support failures before continuing with Setup.</span></span>  
  
3.  <span data-ttu-id="3343e-138">在 **“产品密钥”** 页上，选择某一选项按钮，该按钮指示您是安装免费版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，还是安装具有 PID 密钥的产品的生产版本。</span><span class="sxs-lookup"><span data-stu-id="3343e-138">On the **Product Key** page, select an option button to indicate whether you are installing a free edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or a production version of the product that has a PID key.</span></span> <span data-ttu-id="3343e-139">有关详细信息，请参阅[SQL Server 2014 的版本和组件](../editions-and-components-of-sql-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="3343e-139">For more information, see [Editions and Components of SQL Server 2014](../editions-and-components-of-sql-server-2016.md).</span></span>  
  
4.  <span data-ttu-id="3343e-140">在 **“许可条款”** 页上阅读许可协议，然后选中相应的复选框以接受许可条款和条件。</span><span class="sxs-lookup"><span data-stu-id="3343e-140">On the **License Terms** page, read the license agreement, and then select the check box to accept the license terms and conditions.</span></span> <span data-ttu-id="3343e-141">为了帮助改进 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，您还可以启用功能使用情况选项并将报告发送给 [!INCLUDE[msCoName](../../includes/msconame-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3343e-141">To help improve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can also enable the feature usage option and send reports to [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span>  
  
5.  <span data-ttu-id="3343e-142">在 **“安装程序支持文件”** 页，单击 **“安装”** 以便安装或更新 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的安装程序支持文件。</span><span class="sxs-lookup"><span data-stu-id="3343e-142">On the **Setup Support Files** page, click **Install** to install or update the Setup Support files for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
6.  <span data-ttu-id="3343e-143">在 **“设置角色”** 页上，选择 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能安装”** ，然后单击 **“下一步”** 以继续进入 **“功能选择”** 页。</span><span class="sxs-lookup"><span data-stu-id="3343e-143">On the **Setup Role** page, select **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Feature Installation**, and then click **Next** to continue to the **Feature Selection** page.</span></span>  
  
7.  <span data-ttu-id="3343e-144">在 **“功能选择”** 页上，配置要安装的功能。</span><span class="sxs-lookup"><span data-stu-id="3343e-144">On the **Feature Selection** page, configure which features you want to install.</span></span>  
  
    -   <span data-ttu-id="3343e-145">若要安装管理工具，请选择“管理工具 - 基本”  。</span><span class="sxs-lookup"><span data-stu-id="3343e-145">To install the administration tool, select **Management Tools - Basic**.</span></span>  
  
    -   <span data-ttu-id="3343e-146">若要安装控制器服务，请选择 **“Distributed Replay 控制器”** 。</span><span class="sxs-lookup"><span data-stu-id="3343e-146">To install the controller service, select **Distributed Replay Controller**.</span></span>  
  
    -   <span data-ttu-id="3343e-147">若要安装客户端服务，请选择 **“Distributed Replay 客户端”** 。</span><span class="sxs-lookup"><span data-stu-id="3343e-147">To install the client service, select **Distributed Replay Client**.</span></span>  
  
     <span data-ttu-id="3343e-148">**重要说明**：在你配置 Distributed Replay 控制器时，可以指定将用于运行 Distributed Replay 客户端服务的一个或多个用户帐户。</span><span class="sxs-lookup"><span data-stu-id="3343e-148">**Important**: When you configure Distributed Replay controller, you can specify one or more user accounts that will be used to run the Distributed Replay client services.</span></span> <span data-ttu-id="3343e-149">下面是支持的帐户的列表：</span><span class="sxs-lookup"><span data-stu-id="3343e-149">The following is the list of supported accounts:</span></span>  
  
    -   <span data-ttu-id="3343e-150">域用户帐户</span><span class="sxs-lookup"><span data-stu-id="3343e-150">Domain user account</span></span>  
  
    -   <span data-ttu-id="3343e-151">用户创建的本地用户帐户</span><span class="sxs-lookup"><span data-stu-id="3343e-151">User created local user account</span></span>  
  
    -   <span data-ttu-id="3343e-152">管理员</span><span class="sxs-lookup"><span data-stu-id="3343e-152">Administrator</span></span>  
  
    -   <span data-ttu-id="3343e-153">虚拟帐户和 MSA（托管服务帐户）</span><span class="sxs-lookup"><span data-stu-id="3343e-153">Virtual account and MSA (Managed Service Account)</span></span>  
  
    -   <span data-ttu-id="3343e-154">Network Services、Local Services 和 System</span><span class="sxs-lookup"><span data-stu-id="3343e-154">Network Services, Local Services, and System</span></span>  
  
     <span data-ttu-id="3343e-155">不接受组帐户（本地或域）和其他内置帐户（如 Everyone）。</span><span class="sxs-lookup"><span data-stu-id="3343e-155">Group accounts (local or domain) and other built-in accounts (like Everyone) are not accepted.</span></span>  
  
8.  <span data-ttu-id="3343e-156">（可选）单击省略号 (...) 按钮，以更改共享功能目录路径。</span><span class="sxs-lookup"><span data-stu-id="3343e-156">Optionally, click the ellipsis (...) button to change the shared feature directory path.</span></span>  
  
    1.  <span data-ttu-id="3343e-157">在 32 位计算机上，默认安装路径为 **C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\**</span><span class="sxs-lookup"><span data-stu-id="3343e-157">On 32-bit computers, the default installation path is **C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\**</span></span>  
  
    2.  <span data-ttu-id="3343e-158">在 64 位计算机上，默认安装路径为 C:\Program Files (x86)\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\ </span><span class="sxs-lookup"><span data-stu-id="3343e-158">On 64-bit computers, the default installation path is **C:\Program Files (x86)\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\**</span></span>  
  
9. <span data-ttu-id="3343e-159">完成后，单击“下一步”。 </span><span class="sxs-lookup"><span data-stu-id="3343e-159">When you are finished, click **Next**.</span></span>  
  
10. <span data-ttu-id="3343e-160">在 **“安装规则”** 页上， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序将验证您的计算机配置。</span><span class="sxs-lookup"><span data-stu-id="3343e-160">On the **Installation Rules** page, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup validates your computer configuration.</span></span> <span data-ttu-id="3343e-161">在验证过程完成后，单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="3343e-161">Once the validation process is completed, click **Next**.</span></span>  
  
11. <span data-ttu-id="3343e-162">**“磁盘空间要求”** 页计算指定的功能所需的磁盘空间，</span><span class="sxs-lookup"><span data-stu-id="3343e-162">The **Disk Space Requirements** page calculates the required disk space for the features that you specify.</span></span> <span data-ttu-id="3343e-163">然后将所需空间与可用磁盘空间进行比较。</span><span class="sxs-lookup"><span data-stu-id="3343e-163">Then it compares the required space to the available disk space.</span></span>  
  
12. <span data-ttu-id="3343e-164">在 **“错误报告”** 页上，指定要发送到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 以帮助改进 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的信息。</span><span class="sxs-lookup"><span data-stu-id="3343e-164">On the **Error Reporting** page, specify the information that you want to send to [!INCLUDE[msCoName](../../includes/msconame-md.md)] to help improve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3343e-165">默认情况下，将启用用于错误报告的选项。</span><span class="sxs-lookup"><span data-stu-id="3343e-165">By default, option for error reporting is enabled.</span></span>  
  
13. <span data-ttu-id="3343e-166">在 **“安装配置规则”** 页上，系统配置检查器将运行多组规则来针对您指定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能对您的计算机配置进行验证。</span><span class="sxs-lookup"><span data-stu-id="3343e-166">On the **Installation Configuration Rules** page, the System Configuration Checker will run one more set of rules to validate your computer configuration with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features that you have specified.</span></span>  
  
14. <span data-ttu-id="3343e-167">在 **“准备安装程序”** 页上，单击 **“安装”** 。</span><span class="sxs-lookup"><span data-stu-id="3343e-167">On the **Ready to Install the Program** page, click **Install**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3343e-168">安装 Distributed Replay 之后，您必须在控制器和客户端计算机上创建防火墙规则，并授予每台客户端计算机对目标服务器的权限。</span><span class="sxs-lookup"><span data-stu-id="3343e-168">After you install Distributed Replay you must create firewall rules on the controller and client computers, and grant each client computer permissions on the target server.</span></span> <span data-ttu-id="3343e-169">有关详细信息，请参阅 [完成安装后步骤](../../tools/distributed-replay/complete-the-post-installation-steps.md)。</span><span class="sxs-lookup"><span data-stu-id="3343e-169">For more information, see [Complete the Post-Installation Steps](../../tools/distributed-replay/complete-the-post-installation-steps.md).</span></span>  
  
 <span data-ttu-id="3343e-170">其他这些主题介绍了用于安装 Distributed Replay 的其他方法：</span><span class="sxs-lookup"><span data-stu-id="3343e-170">These additional topics document other ways to install Distributed Replay:</span></span>  
  
-   [<span data-ttu-id="3343e-171">从命令提示符安装 Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="3343e-171">Install Distributed Replay from the Command Prompt</span></span>](../../tools/distributed-replay/install-distributed-replay-overview.md)  
  
-   [<span data-ttu-id="3343e-172">使用配置文件安装 Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="3343e-172">Install Distributed Replay Using a Configuration File</span></span>](../../../2014/sql-server/install/install-distributed-replay-using-a-configuration-file.md)  
  
## <a name="net-framework-security"></a><span data-ttu-id="3343e-173">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="3343e-173">.NET Framework Security</span></span>  
 <span data-ttu-id="3343e-174">您必须具有管理权限才能安装任何 Distributed Replay 功能。</span><span class="sxs-lookup"><span data-stu-id="3343e-174">You must have administrative permissions in order to install any of the Distributed Replay features.</span></span> <span data-ttu-id="3343e-175">只有拥有 sysadmin 权限的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名才可以将客户端服务帐户添加到测试服务器的 sysadmin 服务器角色中。</span><span class="sxs-lookup"><span data-stu-id="3343e-175">Only a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login having sysadmin permissions can add the client service accounts to the sysadmin server role of the test server.</span></span> <span data-ttu-id="3343e-176">有关分布式重播的安全注意事项的详细信息，请参阅 [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md)。</span><span class="sxs-lookup"><span data-stu-id="3343e-176">For more information about Distributed Replay security considerations, see [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3343e-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3343e-177">See Also</span></span>  
 <span data-ttu-id="3343e-178">[SQL Server 2014 的各个版本支持的功能](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="3343e-178">[Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="3343e-179">[SQL Server 分布式重播](../../tools/distributed-replay/sql-server-distributed-replay.md) </span><span class="sxs-lookup"><span data-stu-id="3343e-179">[SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md) </span></span>  
 <span data-ttu-id="3343e-180">[Distributed Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md) </span><span class="sxs-lookup"><span data-stu-id="3343e-180">[Distributed Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md) </span></span>  
 <span data-ttu-id="3343e-181">[管理工具命令行选项（Distributed Replay 实用工具）](../../tools/distributed-replay/administration-tool-command-line-options-distributed-replay-utility.md) </span><span class="sxs-lookup"><span data-stu-id="3343e-181">[Administration Tool Command-line Options &#40;Distributed Replay Utility&#41;](../../tools/distributed-replay/administration-tool-command-line-options-distributed-replay-utility.md) </span></span>  
 [<span data-ttu-id="3343e-182">配置 Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="3343e-182">Configure Distributed Replay</span></span>](../../tools/distributed-replay/configure-distributed-replay.md)  
  
  
