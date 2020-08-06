---
title: Distributed Replay 安全性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 7e2e586d-947d-4fe2-86c5-f06200ebf139
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7b05c6bbe3998faa46d56684b77b8d2a4dec4466
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586021"
---
# <a name="distributed-replay-security"></a><span data-ttu-id="7f650-102">分布式重播安全性</span><span class="sxs-lookup"><span data-stu-id="7f650-102">Distributed Replay Security</span></span>
  <span data-ttu-id="7f650-103">在安装和使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 功能之前，应查看本主题中的重要安全信息。</span><span class="sxs-lookup"><span data-stu-id="7f650-103">Before you install and use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay feature, you should review the important security information in this topic.</span></span> <span data-ttu-id="7f650-104">本主题介绍了您使用分布式重播之前所需的安装后安全配置步骤。</span><span class="sxs-lookup"><span data-stu-id="7f650-104">This topic describes the post-installation security configuration steps that are required before you can use Distributed Replay.</span></span> <span data-ttu-id="7f650-105">本主题还介绍了与数据保护相关的重要注意事项和重要删除步骤。</span><span class="sxs-lookup"><span data-stu-id="7f650-105">This topic also describes important considerations with regard to data protection and important removal steps.</span></span>  
  
## <a name="user-and-service-accounts"></a><span data-ttu-id="7f650-106">用户帐户和服务帐户</span><span class="sxs-lookup"><span data-stu-id="7f650-106">User and Service Accounts</span></span>  
 <span data-ttu-id="7f650-107">下表介绍了用于分布式重播的帐户。</span><span class="sxs-lookup"><span data-stu-id="7f650-107">The following table describes the accounts that are used for Distributed Replay.</span></span> <span data-ttu-id="7f650-108">在安装分布式重播功能后，您必须分配控制器和客户端服务帐户将运行为的安全主体。</span><span class="sxs-lookup"><span data-stu-id="7f650-108">After the Distributed Replay installation, you must assign the security principals that the controller and client service accounts will run as.</span></span> <span data-ttu-id="7f650-109">因此，建议您先配置适当的域用户帐户，然后再安装分布式重播功能。</span><span class="sxs-lookup"><span data-stu-id="7f650-109">Therefore, we recommend that you configure the corresponding domain user accounts before you install the Distributed Replay features.</span></span>  
  
|<span data-ttu-id="7f650-110">用户帐户</span><span class="sxs-lookup"><span data-stu-id="7f650-110">User Account</span></span>|<span data-ttu-id="7f650-111">要求</span><span class="sxs-lookup"><span data-stu-id="7f650-111">Requirements</span></span>|  
|------------------|------------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7f650-112">分布式重播控制器服务帐户</span><span class="sxs-lookup"><span data-stu-id="7f650-112">Distributed Replay controller service account</span></span>|<span data-ttu-id="7f650-113">可以是域用户帐户或本地用户帐户。</span><span class="sxs-lookup"><span data-stu-id="7f650-113">Can be a domain user account or local user account.</span></span> <span data-ttu-id="7f650-114">如果使用本地用户帐户，则管理工具、控制器和客户端都必须在同一台计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="7f650-114">If you use a local user account, the administration tool, controller, and client must all be running on the same computer.</span></span><br /><br /> <span data-ttu-id="7f650-115">**\*\* 安全说明 \*\*** 建议不要将该帐户设置为 Windows 本地管理员组的成员。</span><span class="sxs-lookup"><span data-stu-id="7f650-115">**\*\* Security Note \*\*** We recommend that the account is not a member of the local Administrators group in Windows.</span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7f650-116">分布式重播客户端服务帐户</span><span class="sxs-lookup"><span data-stu-id="7f650-116">Distributed Replay client service account</span></span>|<span data-ttu-id="7f650-117">可以是域用户帐户或本地用户帐户。</span><span class="sxs-lookup"><span data-stu-id="7f650-117">Can be a domain user account or local user account.</span></span> <span data-ttu-id="7f650-118">如果使用本地用户帐户，则控制器、客户端和目标 SQL Server 都必须在同一台计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="7f650-118">If you use a local user account, the controller, client, and target SQL Server must all be running on the same computer.</span></span><br /><br /> <span data-ttu-id="7f650-119">**\*\* 安全说明 \*\*** 建议不要将该帐户设置为 Windows 本地管理员组的成员。</span><span class="sxs-lookup"><span data-stu-id="7f650-119">**\*\* Security Note \*\*** We recommend that the account is not a member of the local Administrators group in Windows.</span></span>|  
|<span data-ttu-id="7f650-120">用于运行分布式重播管理工具的交互式用户帐户</span><span class="sxs-lookup"><span data-stu-id="7f650-120">Interactive user account that is used to run the Distributed Replay administration tool</span></span>|<span data-ttu-id="7f650-121">可以是本地用户帐户或域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="7f650-121">Can be either a local user or a domain user account.</span></span> <span data-ttu-id="7f650-122">若要使用本地用户帐户，管理工具和控制器必须在同一台计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="7f650-122">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>|  
  
 <span data-ttu-id="7f650-123">**重要说明**：在你配置 Distributed Replay 控制器时，可以指定将用于运行 Distributed Replay 客户端服务的一个或多个用户帐户。</span><span class="sxs-lookup"><span data-stu-id="7f650-123">**Important**: When you configure Distributed Replay controller, you can specify one or more user accounts that will be used to run the Distributed Replay client services.</span></span> <span data-ttu-id="7f650-124">下面是支持的帐户的列表：</span><span class="sxs-lookup"><span data-stu-id="7f650-124">The following is the list of supported accounts:</span></span>  
  
-   <span data-ttu-id="7f650-125">域用户帐户</span><span class="sxs-lookup"><span data-stu-id="7f650-125">Domain user account</span></span>  
  
-   <span data-ttu-id="7f650-126">用户创建的本地用户帐户</span><span class="sxs-lookup"><span data-stu-id="7f650-126">User created local user account</span></span>  
  
-   <span data-ttu-id="7f650-127">管理员</span><span class="sxs-lookup"><span data-stu-id="7f650-127">Administrator</span></span>  
  
-   <span data-ttu-id="7f650-128">虚拟帐户和 MSA（托管服务帐户）</span><span class="sxs-lookup"><span data-stu-id="7f650-128">Virtual account and MSA (Managed Service Account)</span></span>  
  
-   <span data-ttu-id="7f650-129">Network Services、Local Services 和 System</span><span class="sxs-lookup"><span data-stu-id="7f650-129">Network Services, Local Services, and System</span></span>  
  
 <span data-ttu-id="7f650-130">不接受组帐户（本地或域）和其他内置帐户（如 Everyone）。</span><span class="sxs-lookup"><span data-stu-id="7f650-130">Group accounts (local or domain) and other built-in accounts (like Everyone) are not accepted.</span></span>  
  
 <span data-ttu-id="7f650-131">在安装分布式重播功能之后，若要设置服务帐户或其密码，您可以使用 Windows 服务工具。</span><span class="sxs-lookup"><span data-stu-id="7f650-131">To set the service accounts or their passwords after you install Distributed Replay, you can use the Windows Services tool.</span></span> <span data-ttu-id="7f650-132">若要更改与分布式重播控制器或客户端服务关联的服务帐户，请按以下步骤执行操作：</span><span class="sxs-lookup"><span data-stu-id="7f650-132">To change the service accounts associated with the Distributed Replay controller or client services, follow these steps:</span></span>  
  
1.  <span data-ttu-id="7f650-133">请根据所用操作系统执行以下两项操作之一：</span><span class="sxs-lookup"><span data-stu-id="7f650-133">Do either of the following, depending on the operating system:</span></span>  
  
    -   <span data-ttu-id="7f650-134">单击 "**开始**"， `services.msc` 在**搜索**框中键入，然后按 enter。</span><span class="sxs-lookup"><span data-stu-id="7f650-134">Click **Start**, type `services.msc` in the **Search** box, and then press ENTER.</span></span>  
  
    -   <span data-ttu-id="7f650-135">依次单击 "**开始**"、"**运行**"，键入 `services.msc` ，然后按 enter。</span><span class="sxs-lookup"><span data-stu-id="7f650-135">Click **Start**, click **Run**, type `services.msc`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="7f650-136">在“服务”对话框中，右键单击要配置的服务，然后单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="7f650-136">In the **Services** dialog box, right-click the service that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="7f650-137">在 **“登录”** 选项卡上，单击 **“本帐户”** 。</span><span class="sxs-lookup"><span data-stu-id="7f650-137">On the **Log On** tab, click **This account**.</span></span>  
  
4.  <span data-ttu-id="7f650-138">配置要使用的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="7f650-138">Configure the user account that you want to use.</span></span>  
  
## <a name="file-and-folder-permissions"></a><span data-ttu-id="7f650-139">文件和文件夹权限</span><span class="sxs-lookup"><span data-stu-id="7f650-139">File and Folder Permissions</span></span>  
 <span data-ttu-id="7f650-140">指定服务帐户后，您必须向这些服务帐户授予必要的文件和文件夹权限。</span><span class="sxs-lookup"><span data-stu-id="7f650-140">After the service accounts have been specified, you must grant the necessary file and folder permissions to those service accounts.</span></span> <span data-ttu-id="7f650-141">根据下表配置文件和文件夹权限：</span><span class="sxs-lookup"><span data-stu-id="7f650-141">Configure file and folder permissions according to the following table:</span></span>  
  
|<span data-ttu-id="7f650-142">帐户</span><span class="sxs-lookup"><span data-stu-id="7f650-142">Account</span></span>|<span data-ttu-id="7f650-143">文件夹权限</span><span class="sxs-lookup"><span data-stu-id="7f650-143">Folder Permissions</span></span>|  
|-------------|------------------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7f650-144">分布式重播控制器服务帐户</span><span class="sxs-lookup"><span data-stu-id="7f650-144">Distributed Replay controller service account</span></span>|<span data-ttu-id="7f650-145">`<Controller_Installation_Path>\DReplayController` （读取、写入、删除）</span><span class="sxs-lookup"><span data-stu-id="7f650-145">`<Controller_Installation_Path>\DReplayController` (Read, Write, Delete)</span></span><br /><br /> <span data-ttu-id="7f650-146">`DReplayServer.xml` 文件（读取、写入）</span><span class="sxs-lookup"><span data-stu-id="7f650-146">`DReplayServer.xml` file (Read, Write)</span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7f650-147">分布式重播客户端服务帐户</span><span class="sxs-lookup"><span data-stu-id="7f650-147">Distributed Replay client service account</span></span>|<span data-ttu-id="7f650-148">`<Client_Installation_Path>\DReplayClient` （读取、写入、删除）</span><span class="sxs-lookup"><span data-stu-id="7f650-148">`<Client_Installation_Path>\DReplayClient` (Read, Write, Delete)</span></span><br /><br /> <span data-ttu-id="7f650-149">`DReplayClient.xml` 文件（读取、写入）</span><span class="sxs-lookup"><span data-stu-id="7f650-149">`DReplayClient.xml` file (Read, Write)</span></span><br /><br /> <span data-ttu-id="7f650-150">工作目录和结果目录，在客户端配置文件中分别由 `WorkingDirectory` 元素和 `ResultDirectory` 元素指定。</span><span class="sxs-lookup"><span data-stu-id="7f650-150">The working and result directories, as specified in the client configuration file by the `WorkingDirectory` and `ResultDirectory` elements, respectively.</span></span> <span data-ttu-id="7f650-151">（读取、写入）</span><span class="sxs-lookup"><span data-stu-id="7f650-151">(Read, Write)</span></span>|  
  
## <a name="dcom-permissions"></a><span data-ttu-id="7f650-152">DCOM 权限</span><span class="sxs-lookup"><span data-stu-id="7f650-152">DCOM Permissions</span></span>  
 <span data-ttu-id="7f650-153">DCOM 用于控制器和管理工具之间以及控制器和所有客户端之间的远程过程调用 (RPC) 通信。</span><span class="sxs-lookup"><span data-stu-id="7f650-153">DCOM is used for remote procedure call (RPC) communication between the controller and the administration tool, and between the controller and all clients.</span></span> <span data-ttu-id="7f650-154">在安装分布式重播功能之后，您必须在控制器上配置计算机范围的和应用程序特定的 DCOM 权限。</span><span class="sxs-lookup"><span data-stu-id="7f650-154">You must configure computer-wide and application-specific DCOM permissions on the controller after the Distributed Replay features have been installed.</span></span>  
  
 <span data-ttu-id="7f650-155">若要配置控制器 DCOM 权限，请按以下步骤执行操作：</span><span class="sxs-lookup"><span data-stu-id="7f650-155">To configure the controller DCOM permissions, follow these steps:</span></span>  
  
1.  <span data-ttu-id="7f650-156">**打开 dcomcnfg.exe、组件服务管理单元**：这是用于配置 DCOM 权限的工具。</span><span class="sxs-lookup"><span data-stu-id="7f650-156">**Open dcomcnfg.exe, the Component Services snap-in**: This is the tool that is used to configure DCOM permissions.</span></span>  
  
    1.  <span data-ttu-id="7f650-157">在控制器计算机上，单击 **“开始”** 。</span><span class="sxs-lookup"><span data-stu-id="7f650-157">On the controller computer, click **Start**.</span></span>  
  
    2.  <span data-ttu-id="7f650-158">`dcomcnfg.exe`在**搜索**框中键入。</span><span class="sxs-lookup"><span data-stu-id="7f650-158">Type `dcomcnfg.exe` in the **Search** box.</span></span>  
  
    3.  <span data-ttu-id="7f650-159">按 Enter。</span><span class="sxs-lookup"><span data-stu-id="7f650-159">Press ENTER.</span></span>  
  
2.  <span data-ttu-id="7f650-160">**配置计算机范围内的 DCOM 权限**：为下表中列出的每个帐户授予相应的计算机范围的 DCOM 权限。</span><span class="sxs-lookup"><span data-stu-id="7f650-160">**Configure computer-wide DCOM permissions**: Grant the corresponding computer-wide DCOM permissions for each account listed in the following table.</span></span> <span data-ttu-id="7f650-161">有关如何设置计算机范围的权限的详细信息，请参阅[清单：管理 DCOM 应用程序](https://go.microsoft.com/fwlink/?LinkId=185842)。</span><span class="sxs-lookup"><span data-stu-id="7f650-161">For more information about how to set computer-wide permissions, see [Checklist: Manage DCOM Applications](https://go.microsoft.com/fwlink/?LinkId=185842).</span></span>  
  
3.  <span data-ttu-id="7f650-162">**配置应用程序特定的 DCOM 权限**：为下表中列出的每个帐户授予相应的应用程序特定的 DCOM 权限。</span><span class="sxs-lookup"><span data-stu-id="7f650-162">**Configure application-specific DCOM permissions**: Grant the corresponding application-specific DCOM permissions for each account listed in the following table.</span></span> <span data-ttu-id="7f650-163">控制器服务的 DCOM 应用程序名称为 **DReplayController**。</span><span class="sxs-lookup"><span data-stu-id="7f650-163">The DCOM application name for the controller service is **DReplayController**.</span></span> <span data-ttu-id="7f650-164">有关如何设置应用程序特定的权限的详细信息，请参阅[清单：管理 DCOM 应用程序](https://go.microsoft.com/fwlink/?LinkId=185842)。</span><span class="sxs-lookup"><span data-stu-id="7f650-164">For more information about how to set application-specific permissions, see [Checklist: Manage DCOM Applications](https://go.microsoft.com/fwlink/?LinkId=185842).</span></span>  
  
 <span data-ttu-id="7f650-165">下表介绍了管理工具交互式用户帐户和客户端服务帐户所需的 DCOM 权限：</span><span class="sxs-lookup"><span data-stu-id="7f650-165">The following table describes which DCOM permissions are required for the administration tool interactive user account and the client service accounts:</span></span>  
  
|<span data-ttu-id="7f650-166">Feature</span><span class="sxs-lookup"><span data-stu-id="7f650-166">Feature</span></span>|<span data-ttu-id="7f650-167">帐户</span><span class="sxs-lookup"><span data-stu-id="7f650-167">Account</span></span>|<span data-ttu-id="7f650-168">控制器上所需的 DCOM 权限</span><span class="sxs-lookup"><span data-stu-id="7f650-168">Required DCOM Permissions on Controller</span></span>|  
|-------------|-------------|---------------------------------------------|  
|<span data-ttu-id="7f650-169">分布式重播管理工具</span><span class="sxs-lookup"><span data-stu-id="7f650-169">Distributed Replay administration tool</span></span>|<span data-ttu-id="7f650-170">交互式用户帐户</span><span class="sxs-lookup"><span data-stu-id="7f650-170">The interactive user account</span></span>|<span data-ttu-id="7f650-171">本地访问</span><span class="sxs-lookup"><span data-stu-id="7f650-171">Local Access</span></span><br /><br /> <span data-ttu-id="7f650-172">远程访问</span><span class="sxs-lookup"><span data-stu-id="7f650-172">Remote Access</span></span><br /><br /> <span data-ttu-id="7f650-173">本地启动</span><span class="sxs-lookup"><span data-stu-id="7f650-173">Local Launch</span></span><br /><br /> <span data-ttu-id="7f650-174">远程启动</span><span class="sxs-lookup"><span data-stu-id="7f650-174">Remote Launch</span></span><br /><br /> <span data-ttu-id="7f650-175">本地激活</span><span class="sxs-lookup"><span data-stu-id="7f650-175">Local Activation</span></span><br /><br /> <span data-ttu-id="7f650-176">远程激活</span><span class="sxs-lookup"><span data-stu-id="7f650-176">Remote Activation</span></span>|  
|<span data-ttu-id="7f650-177">Distributed Replay 客户端</span><span class="sxs-lookup"><span data-stu-id="7f650-177">Distributed Replay client</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7f650-178">分布式重播客户端服务帐户</span><span class="sxs-lookup"><span data-stu-id="7f650-178">Distributed Replay client service account</span></span>|<span data-ttu-id="7f650-179">本地访问</span><span class="sxs-lookup"><span data-stu-id="7f650-179">Local Access</span></span><br /><br /> <span data-ttu-id="7f650-180">远程访问</span><span class="sxs-lookup"><span data-stu-id="7f650-180">Remote Access</span></span><br /><br /> <span data-ttu-id="7f650-181">本地启动</span><span class="sxs-lookup"><span data-stu-id="7f650-181">Local Launch</span></span><br /><br /> <span data-ttu-id="7f650-182">远程启动</span><span class="sxs-lookup"><span data-stu-id="7f650-182">Remote Launch</span></span><br /><br /> <span data-ttu-id="7f650-183">本地激活</span><span class="sxs-lookup"><span data-stu-id="7f650-183">Local Activation</span></span><br /><br /> <span data-ttu-id="7f650-184">远程激活</span><span class="sxs-lookup"><span data-stu-id="7f650-184">Remote Activation</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7f650-185">若要帮助防止恶意查询或拒绝服务攻击，请确保您仅对客户端服务帐户使用受信任的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="7f650-185">To help protect against malicious queries or denial of service attacks, make sure that you only use a trusted user account for the client service account.</span></span> <span data-ttu-id="7f650-186">此帐户将能够连接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]目标实例并针对该实例重播工作负荷。</span><span class="sxs-lookup"><span data-stu-id="7f650-186">This account will be able to connect and replay workloads against the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="sql-server-permissions"></a><span data-ttu-id="7f650-187">SQL Server 权限</span><span class="sxs-lookup"><span data-stu-id="7f650-187">SQL Server Permissions</span></span>  
 <span data-ttu-id="7f650-188">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分布式重播客户端服务帐户用于连接工作负荷的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]目标实例。</span><span class="sxs-lookup"><span data-stu-id="7f650-188">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay client service accounts are used to connect to the workload's target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7f650-189">这些连接仅支持 Windows 身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="7f650-189">Only Windows Authentication mode is supported for these connections.</span></span>  
  
 <span data-ttu-id="7f650-190">在一组计算机上安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分布式重播客户端服务之后，必须向用于这些服务帐户的安全主体授予你打算针对其重播跟踪工作负荷的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上的 sysadmin 服务器角色。</span><span class="sxs-lookup"><span data-stu-id="7f650-190">After you install the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay client service on a set of computers, the security principal used for those service accounts must be granted the sysadmin server role on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you intend to replay the trace workload against.</span></span> <span data-ttu-id="7f650-191">在分布式重播安装期间，不会自动执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="7f650-191">This step is not performed automatically during Distributed Replay Setup.</span></span>  
  
## <a name="data-protection"></a><span data-ttu-id="7f650-192">数据保护</span><span class="sxs-lookup"><span data-stu-id="7f650-192">Data Protection</span></span>  
 <span data-ttu-id="7f650-193">在分布式重播环境中，将授予以下用户帐户对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的目标服务器实例、输入跟踪数据和结果跟踪文件的完全访问权：</span><span class="sxs-lookup"><span data-stu-id="7f650-193">In the Distributed Replay environment, the following user accounts are granted full access to the target server instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the input trace data and result trace files:</span></span>  
  
-   <span data-ttu-id="7f650-194">用于运行该管理工具的交互式用户帐户。</span><span class="sxs-lookup"><span data-stu-id="7f650-194">The interactive user account that is used to run the administration tool.</span></span>  
  
-   <span data-ttu-id="7f650-195">控制器服务帐户。</span><span class="sxs-lookup"><span data-stu-id="7f650-195">The controller service account.</span></span>  
  
-   <span data-ttu-id="7f650-196">客户端服务帐户。</span><span class="sxs-lookup"><span data-stu-id="7f650-196">The client service account.</span></span>  
  
-   <span data-ttu-id="7f650-197">控制器上的本地 Administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="7f650-197">Members of the local Administrators group on the controller.</span></span>  
  
-   <span data-ttu-id="7f650-198">客户端上的本地 Administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="7f650-198">Members of the local Administrators group on the clients.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="7f650-199">这些帐户具有对包含在分布式重播功能所使用的跟踪数据文件、中间数据文件、调度数据文件或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据文件中的任何个人身份信息 (PII) 或敏感信息的完全访问权。</span><span class="sxs-lookup"><span data-stu-id="7f650-199">These accounts have full access to any personally identifiable information (PII) or sensitive information that is contained in the trace, intermediate, dispatch, or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data files that were used by Distributed Replay.</span></span>  
  
 <span data-ttu-id="7f650-200">建议您采取以下安全防范措施：</span><span class="sxs-lookup"><span data-stu-id="7f650-200">We recommend that you take the following security precautions:</span></span>  
  
-   <span data-ttu-id="7f650-201">将输入跟踪数据、输出跟踪结果和数据库文件存储在使用 NTFS 文件系统 (NTFS) 的位置，并应用适当的访问控制列表 (ACL)。</span><span class="sxs-lookup"><span data-stu-id="7f650-201">Store the input trace data, output trace results, and database files in a location that uses the NTFS file system (NTFS), and apply the appropriate access control lists (ACLs).</span></span> <span data-ttu-id="7f650-202">如果需要，可对存储在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 计算机上的数据进行加密。</span><span class="sxs-lookup"><span data-stu-id="7f650-202">If it is needed, encrypt the data that is stored on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer.</span></span> <span data-ttu-id="7f650-203">请注意，不将 ACL 应用于跟踪文件，也不会执行数据屏蔽或模糊处理。</span><span class="sxs-lookup"><span data-stu-id="7f650-203">Be aware that ACLs are not applied to the trace files and there is no data masking or obfuscation.</span></span> <span data-ttu-id="7f650-204">您应在使用完这些文件后迅速将其删除。</span><span class="sxs-lookup"><span data-stu-id="7f650-204">You should delete these files quickly after use.</span></span>  
  
-   <span data-ttu-id="7f650-205">将适当的 ACL 和保留策略应用于分布式重播功能所生成的所有中间文件和调度文件。</span><span class="sxs-lookup"><span data-stu-id="7f650-205">Apply the appropriate ACLs and retention policy to all intermediate and dispatch files that are generated by Distributed Replay.</span></span>  
  
-   <span data-ttu-id="7f650-206">使用安全套接字层 (SSL) 帮助保护网络传输。</span><span class="sxs-lookup"><span data-stu-id="7f650-206">Use Secure Sockets Layer (SSL) to help secure the network transport.</span></span>  
  
## <a name="important-removal-steps"></a><span data-ttu-id="7f650-207">重要删除步骤</span><span class="sxs-lookup"><span data-stu-id="7f650-207">Important Removal Steps</span></span>  
 <span data-ttu-id="7f650-208">建议您仅在测试环境中使用分布式重播功能。</span><span class="sxs-lookup"><span data-stu-id="7f650-208">We recommend that you only use Distributed Replay in a test environment.</span></span> <span data-ttu-id="7f650-209">在您完成测试之后，并在您为其他任务设置这些计算机之前，请确保您已完成以下操作：</span><span class="sxs-lookup"><span data-stu-id="7f650-209">After you have completed testing, and before you provision those computers for a different task, make sure that you do the following:</span></span>  
  
-   <span data-ttu-id="7f650-210">卸载分布式重播功能，并从控制器和所有客户端中删除相关的配置文件。</span><span class="sxs-lookup"><span data-stu-id="7f650-210">Uninstall the Distributed Replay features and remove the related configuration files from the controller and all clients.</span></span>  
  
-   <span data-ttu-id="7f650-211">删除用于测试的任何跟踪数据库文件、中间数据库文件、调度数据库文件和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库文件。</span><span class="sxs-lookup"><span data-stu-id="7f650-211">Delete any trace, intermediate, dispatch, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database files that were used for testing.</span></span> <span data-ttu-id="7f650-212">中间文件和调度文件分别存储在控制器上的工作目录和客户端上的工作目录中。</span><span class="sxs-lookup"><span data-stu-id="7f650-212">The intermediate and dispatch files are stored in the working directory on the controller and client, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f650-213">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7f650-213">See Also</span></span>  
 <span data-ttu-id="7f650-214">[SQL Server 分布式重播](sql-server-distributed-replay.md) </span><span class="sxs-lookup"><span data-stu-id="7f650-214">[SQL Server Distributed Replay](sql-server-distributed-replay.md) </span></span>  
 [<span data-ttu-id="7f650-215">安装 Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="7f650-215">Install Distributed Replay</span></span>](install-distributed-replay-overview.md)  
  
  
