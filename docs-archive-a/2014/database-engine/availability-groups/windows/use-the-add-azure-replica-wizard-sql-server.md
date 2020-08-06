---
title: 使用“添加 Azure 副本向导”(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.azurereplica.f1
ms.assetid: b89cc41b-07b4-49f3-82cc-bc42b2e793ae
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8f7ee9e80f0511fe23aebb887b15b5e8b7e9cabf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683060"
---
# <a name="use-the-add-azure-replica-wizard-sql-server"></a><span data-ttu-id="53a36-102">使用“添加 Azure 副本向导”(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="53a36-102">Use the Add Azure Replica Wizard (SQL Server)</span></span>
  <span data-ttu-id="53a36-103">使用 "添加 Azure 副本" 向导来帮助你在混合 IT 中创建新的 Azure VM，并将其配置为新的或现有 AlwaysOn 可用性组的辅助副本。</span><span class="sxs-lookup"><span data-stu-id="53a36-103">Use the Add Azure Replica Wizard to help you create a new Azure VM in hybrid IT and configure it as a secondary replica for a new or existing AlwaysOn availability group.</span></span>  
  
-   <span data-ttu-id="53a36-104">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="53a36-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="53a36-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="53a36-105">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="53a36-106">安全性</span><span class="sxs-lookup"><span data-stu-id="53a36-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="53a36-107">**要添加副本，请使用：**  [添加 Azure 副本向导 (SQL Server Management Studio)](#SSMSProcedure)</span><span class="sxs-lookup"><span data-stu-id="53a36-107">**To add a replica, using:**  [Add Azure Replica Wizard (SQL Server Management Studio)](#SSMSProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="53a36-108">开始之前</span><span class="sxs-lookup"><span data-stu-id="53a36-108">Before You Begin</span></span>  
 <span data-ttu-id="53a36-109">如果你从未向可用性组添加过任何可用性副本，请参阅[针对 AlwaysOn 可用性组 &#40;SQL Server&#41;的先决条件、限制和建议](prereqs-restrictions-recommendations-always-on-availability.md)中的 "服务器实例" 和 "可用性组和副本" 部分。</span><span class="sxs-lookup"><span data-stu-id="53a36-109">If you have never added any availability replica to an availability group, see the "Server instances" and "Availability groups and replicas" sections in [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="53a36-110">先决条件</span><span class="sxs-lookup"><span data-stu-id="53a36-110">Prerequisites</span></span>  
  
-   <span data-ttu-id="53a36-111">您必须连接到承载当前主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="53a36-111">You must be connected to the server instance that hosts the current primary replica.</span></span>  
  
-   <span data-ttu-id="53a36-112">你必须有混合 IT 环境，其中的本地子网有 Azure 站点到站点 VPN。</span><span class="sxs-lookup"><span data-stu-id="53a36-112">You must have a hybrid-IT environment where your on-premise subnet has a site-to-site VPN with Azure.</span></span> <span data-ttu-id="53a36-113">有关详细信息，请参阅 [在管理门户中配置站点到站点 VPN](https://azure.microsoft.com/documentation/articles/vpn-gateway-site-to-site-create)。</span><span class="sxs-lookup"><span data-stu-id="53a36-113">For more information, see [Configure a Site-to-Site VPN in the Management Portal](https://azure.microsoft.com/documentation/articles/vpn-gateway-site-to-site-create).</span></span>  
  
-   <span data-ttu-id="53a36-114">可用性组必须包含本地可用性副本。</span><span class="sxs-lookup"><span data-stu-id="53a36-114">Your availability group must contain on-premise availability replicas.</span></span>  
  
-   <span data-ttu-id="53a36-115">到可用性组侦听器的客户端必须具有 Internet 连接，才能在可用性组故障转移到 Azure 副本时保持与侦听器的连接。</span><span class="sxs-lookup"><span data-stu-id="53a36-115">Clients to the availability group listener must have connectivity to the Internet if they want to maintain connectivity with the listener when the availability group is failed over to an Azure replica.</span></span>  
  
-   <span data-ttu-id="53a36-116">**使用完全初始数据同步的先决条件** 为了使该向导创建并访问备份，需要指定网络共享。</span><span class="sxs-lookup"><span data-stu-id="53a36-116">**Prerequisites for using full initial data synchronization** You will need to specify a network share in order for the wizard to create and access backups.</span></span> <span data-ttu-id="53a36-117">对于主副本，用于启动 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的帐户必须对网络共享具有读写文件系统权限。</span><span class="sxs-lookup"><span data-stu-id="53a36-117">For the primary replica, the account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must have read and write file-system permissions on a network share.</span></span> <span data-ttu-id="53a36-118">对于辅助副本，该帐户必须具有对网络共享区的读权限。</span><span class="sxs-lookup"><span data-stu-id="53a36-118">For secondary replicas, the account must have read permission on the network share.</span></span>  
  
     <span data-ttu-id="53a36-119">如果您无法使用该向导执行完全初始数据同步，则需要手动准备您的辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="53a36-119">If you are unable to use the wizard to perform full initial data synchronization, you need to prepare your secondary databases manually.</span></span> <span data-ttu-id="53a36-120">您可以在运行该向导之前或之后进行准备。</span><span class="sxs-lookup"><span data-stu-id="53a36-120">You can do this before or after running the wizard.</span></span> <span data-ttu-id="53a36-121">有关详细信息，请参阅 [为可用性组手动准备辅助数据库 (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)或 PowerShell 将辅助数据库联接到 Always On 可用性组。</span><span class="sxs-lookup"><span data-stu-id="53a36-121">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="53a36-122">Security</span><span class="sxs-lookup"><span data-stu-id="53a36-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="53a36-123">权限</span><span class="sxs-lookup"><span data-stu-id="53a36-123">Permissions</span></span>  
 <span data-ttu-id="53a36-124">请参阅 [Security](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md#Security)</span><span class="sxs-lookup"><span data-stu-id="53a36-124">See [Security](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md#Security)</span></span>  
  
##  <a name="using-the-add-azure-replica-wizard-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="53a36-125">使用“添加 Azure 副本向导”(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="53a36-125">Using the Add Azure Replica Wizard (SQL Server Management Studio)</span></span>  
 <span data-ttu-id="53a36-126">可以从 [“指定副本”页](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md)启动“添加 Azure 副本向导”。</span><span class="sxs-lookup"><span data-stu-id="53a36-126">The Add Azure Replica Wizard can be launched from the [Specify Replicas Page](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md).</span></span> <span data-ttu-id="53a36-127">有两种方法可以打开此页：</span><span class="sxs-lookup"><span data-stu-id="53a36-127">There are two ways to reach this page:</span></span>  
  
-   [<span data-ttu-id="53a36-128">使用可用性组向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="53a36-128">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="53a36-129">使用“将副本添加到可用性组向导”(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="53a36-129">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
 <span data-ttu-id="53a36-130">启动“添加 Azure 副本向导”后，按以下步骤操作：</span><span class="sxs-lookup"><span data-stu-id="53a36-130">Once you have launched the Add Azure Replica Wizard, follow the steps below:</span></span>  
  
1.  <span data-ttu-id="53a36-131">首先，为你的 Azure 订阅下载管理证书。</span><span class="sxs-lookup"><span data-stu-id="53a36-131">First, download a management certificate for your Azure subscription.</span></span> <span data-ttu-id="53a36-132">单击“下载”打开登录页面。</span><span class="sxs-lookup"><span data-stu-id="53a36-132">Click **Download** to open the sign-in page.</span></span>  
  
2.  <span data-ttu-id="53a36-133">在登录页中，登录到 Azure 订阅。</span><span class="sxs-lookup"><span data-stu-id="53a36-133">In the sign-in page, sign in to your Azure subscription.</span></span> <span data-ttu-id="53a36-134">登录后，向导会在您的本地计算机上安装管理证书。</span><span class="sxs-lookup"><span data-stu-id="53a36-134">Once you are signed in, the wizard installs a management certificate onto your local machine.</span></span> <span data-ttu-id="53a36-135">下次使用此向导时会自动加载此管理证书。</span><span class="sxs-lookup"><span data-stu-id="53a36-135">This management certificate is automatically loaded when you use this wizard again.</span></span> <span data-ttu-id="53a36-136">如果您下载了多个管理证书，可以单击 **“...”** 按钮选择要使用的证书。</span><span class="sxs-lookup"><span data-stu-id="53a36-136">If you have downloaded multiple management certificates, you can click the **...** button to select the one you want to use.</span></span>  
  
3.  <span data-ttu-id="53a36-137">然后单击 **“连接”** 连接到您的订阅。</span><span class="sxs-lookup"><span data-stu-id="53a36-137">Next, connect to your subscription by clicking **Connect**.</span></span> <span data-ttu-id="53a36-138">连接后，下拉列表用 Azure 参数进行填充，例如“虚拟网络”和“虚拟网络子网”。</span><span class="sxs-lookup"><span data-stu-id="53a36-138">Once you are connected, the drop-down lists are populated with your Azure parameters, such as **Virtual Network** and **Virtual Network Subnet**.</span></span>  
  
4.  <span data-ttu-id="53a36-139">为将承载新辅助副本的 Azure 虚拟机指定设置：</span><span class="sxs-lookup"><span data-stu-id="53a36-139">Specify the settings for the Azure VM that will host the new secondary replica:</span></span>  
  
     <span data-ttu-id="53a36-140">映像</span><span class="sxs-lookup"><span data-stu-id="53a36-140">Image</span></span>  
     <span data-ttu-id="53a36-141">要用于 Azure 虚拟机的 SQL Server 映像的名称</span><span class="sxs-lookup"><span data-stu-id="53a36-141">The name of the SQL Server image to use for the Azure VM</span></span>  
  
     <span data-ttu-id="53a36-142">VM 大小</span><span class="sxs-lookup"><span data-stu-id="53a36-142">VM Size</span></span>  
     <span data-ttu-id="53a36-143">Azure 虚拟机的大小</span><span class="sxs-lookup"><span data-stu-id="53a36-143">The size of the Azure VM</span></span>  
  
     <span data-ttu-id="53a36-144">VM 名称</span><span class="sxs-lookup"><span data-stu-id="53a36-144">VM Name</span></span>  
     <span data-ttu-id="53a36-145">Azure 虚拟机的 DNS 名称</span><span class="sxs-lookup"><span data-stu-id="53a36-145">The DNS name of the Azure VM</span></span>  
  
     <span data-ttu-id="53a36-146">VM 用户名</span><span class="sxs-lookup"><span data-stu-id="53a36-146">VM Username</span></span>  
     <span data-ttu-id="53a36-147">Azure 虚拟机默认管理员的用户名</span><span class="sxs-lookup"><span data-stu-id="53a36-147">The username of the default administrator for the Azure VM</span></span>  
  
     <span data-ttu-id="53a36-148">VM 管理员密码（和确认密码）</span><span class="sxs-lookup"><span data-stu-id="53a36-148">VM Administrator Password (and Confirm Password)</span></span>  
     <span data-ttu-id="53a36-149">Azure 虚拟机默认管理员的密码</span><span class="sxs-lookup"><span data-stu-id="53a36-149">The password for the default administrator for the Azure VM</span></span>  
  
     <span data-ttu-id="53a36-150">虚拟网络</span><span class="sxs-lookup"><span data-stu-id="53a36-150">Virtual Network</span></span>  
     <span data-ttu-id="53a36-151">要放置 Azure 虚拟机的虚拟网络</span><span class="sxs-lookup"><span data-stu-id="53a36-151">The virtual network in which to place the Azure VM</span></span>  
  
     <span data-ttu-id="53a36-152">虚拟网络子网</span><span class="sxs-lookup"><span data-stu-id="53a36-152">Virtual Network Subnet</span></span>  
     <span data-ttu-id="53a36-153">要放置 Azure 虚拟机的虚拟网络子网</span><span class="sxs-lookup"><span data-stu-id="53a36-153">The virtual network subnet in which to place the Azure VM</span></span>  
  
     <span data-ttu-id="53a36-154">域</span><span class="sxs-lookup"><span data-stu-id="53a36-154">Domain</span></span>  
     <span data-ttu-id="53a36-155">要联接 Azure 虚拟机的 Active Directory (AD) 域</span><span class="sxs-lookup"><span data-stu-id="53a36-155">The Active Directory (AD) domain to join the Azure VM</span></span>  
  
     <span data-ttu-id="53a36-156">域用户名</span><span class="sxs-lookup"><span data-stu-id="53a36-156">Domain Username</span></span>  
     <span data-ttu-id="53a36-157">用于将 Azure 虚拟机联接到域的 AD 用户名</span><span class="sxs-lookup"><span data-stu-id="53a36-157">The AD username used to join the Azure VM to the domain</span></span>  
  
     <span data-ttu-id="53a36-158">密码</span><span class="sxs-lookup"><span data-stu-id="53a36-158">Password</span></span>  
     <span data-ttu-id="53a36-159">用于将 Azure 虚拟机联接到域的密码</span><span class="sxs-lookup"><span data-stu-id="53a36-159">The password used to join the Azure VM to the domain</span></span>  
  
5.  <span data-ttu-id="53a36-160">单击 **“确定”** 提交设置并退出“添加 Azure 副本向导”。</span><span class="sxs-lookup"><span data-stu-id="53a36-160">Click **OK** to commit your settings and exit the Add Azure Replica Wizard.</span></span>  
  
6.  <span data-ttu-id="53a36-161">对任意新副本继续 [“指定副本”页](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) 的剩余配置步骤。</span><span class="sxs-lookup"><span data-stu-id="53a36-161">Continue with the rest of the configuration steps for [Specify Replicas Page](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) as you do for any new replica.</span></span>  
  
     <span data-ttu-id="53a36-162">完成 "可用性组向导" 或 "将副本添加到可用性组向导" 后，配置过程将在 Azure 中执行所有操作来创建新的 VM，将其加入 AD 域，将其添加到 Windows 群集，启用 AlwaysOn 高可用性，并将新副本添加到可用性组。</span><span class="sxs-lookup"><span data-stu-id="53a36-162">Once you are finished with the Availability Group Wizard or the Add Replica to Availability Group Wizard, the configuration process performs all operations in Azure to create the new VM, join it to the AD domain, add it to the Windows cluster, enable AlwaysOn High Availability, and add the new replica to the availability group.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="53a36-163">相关任务</span><span class="sxs-lookup"><span data-stu-id="53a36-163">Related Tasks</span></span>  
  
-   [<span data-ttu-id="53a36-164">将辅助副本添加到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="53a36-164">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="53a36-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="53a36-165">See Also</span></span>  
 <span data-ttu-id="53a36-166">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="53a36-166">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="53a36-167">[AlwaysOn 可用性组 &#40;SQL Server 的先决条件、限制和建议&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="53a36-167">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 [<span data-ttu-id="53a36-168">将辅助副本添加到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="53a36-168">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
  
