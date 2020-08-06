---
title: 创建或配置可用性组侦听程序 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.newaglistener.general.f1
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], client connectivity
ms.assetid: 2bc294f6-2312-4b6b-9478-2fb8a656e645
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2c74e92286eab4bc1be8f3f538d83d86f056cf01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694563"
---
# <a name="create-or-configure-an-availability-group-listener-sql-server"></a><span data-ttu-id="be533-102">创建或配置可用性组侦听器 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="be533-102">Create or Configure an Availability Group Listener (SQL Server)</span></span>
  <span data-ttu-id="be533-103">本主题说明如何通过在中使用、或 PowerShell 为 AlwaysOn 可用性组创建或配置单个*可用性组侦听器* [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../../includes/tsql-md.md)] [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="be533-103">This topic describes how to create or configure a single *availability group listener* for an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="be533-104">若要创建某个可用性组的第一个可用性组侦听器，我们强烈建议您使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell。</span><span class="sxs-lookup"><span data-stu-id="be533-104">To create the first availability group listener of an availability group, we strongly recommend that you [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell.</span></span> <span data-ttu-id="be533-105">除非必要情况，例如创建附加侦听器，否则，应避免直接在 WSFC 群集中创建侦听器。</span><span class="sxs-lookup"><span data-stu-id="be533-105">Avoid creating a listener directly in the WSFC cluster except when necessary, for example, to create an additional listener.</span></span>  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="be533-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="be533-106">Before You Begin</span></span>  
  
###  <a name="does-a-listener-exist-for-this-availability-group-already"></a><a name="DoesListenerExist"></a> <span data-ttu-id="be533-107">已存在此可用性组的侦听器？</span><span class="sxs-lookup"><span data-stu-id="be533-107">Does a Listener Exist for this Availability Group Already?</span></span>  
 <span data-ttu-id="be533-108">**确定可用性组是否已存在一个侦听器**</span><span class="sxs-lookup"><span data-stu-id="be533-108">**To determine whether a listener already exists for the availability group**</span></span>  
  
-   [<span data-ttu-id="be533-109">查看可用性组侦听程序属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="be533-109">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
> [!NOTE]  
>  <span data-ttu-id="be533-110">如果某个侦听程序已存在并且你想要创建附加的侦听程序，请参阅本文后面的 [为可用性组创建其他侦听程序（可选）](#CreateAdditionalListener)。</span><span class="sxs-lookup"><span data-stu-id="be533-110">If a listener already exists and you want to create an additional listener, see [To Create An Additional Listener for an Availability Group (Optional)](#CreateAdditionalListener), later in this topic.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="be533-111">限制和局限</span><span class="sxs-lookup"><span data-stu-id="be533-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="be533-112">您只能通过 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]为每个可用性组创建一个侦听器。</span><span class="sxs-lookup"><span data-stu-id="be533-112">You can create only one listener per availability group through [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="be533-113">通常情况下，每个可用性组只需要一个侦听器。</span><span class="sxs-lookup"><span data-stu-id="be533-113">Typically, each availability group requires only one listener.</span></span> <span data-ttu-id="be533-114">但是，某些用户群体要求一个可用性组多个侦听器。</span><span class="sxs-lookup"><span data-stu-id="be533-114">However, some customer scenarios require multiple listeners for one availability group.</span></span>   <span data-ttu-id="be533-115">通过 SQL Server 创建一个侦听器之后，您可以将 Windows PowerShell 用于故障转移群集或使用 WSFC 故障转移群集管理器来创建其他侦听器。</span><span class="sxs-lookup"><span data-stu-id="be533-115">After creating a listener through SQL Server, you can use Windows PowerShell for failover clusters or the WSFC Failover Cluster Manager to create additional listeners.</span></span> <span data-ttu-id="be533-116">有关详细信息，请参阅本主题后面的 [为可用性组创建其他侦听程序（可选）](#CreateAdditionalListener)。</span><span class="sxs-lookup"><span data-stu-id="be533-116">For more information, see [To Create An Additional Listener for an Availability Group (Optional)](#CreateAdditionalListener), later in this topic.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="be533-117">建议</span><span class="sxs-lookup"><span data-stu-id="be533-117">Recommendations</span></span>  
 <span data-ttu-id="be533-118">建议对于多子网配置使用静态 IP 地址，尽管不是必需的。</span><span class="sxs-lookup"><span data-stu-id="be533-118">Using a static IP address is recommended, although not required, for multiple subnet configurations.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="be533-119">先决条件</span><span class="sxs-lookup"><span data-stu-id="be533-119">Prerequisites</span></span>  
  
-   <span data-ttu-id="be533-120">您必须连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="be533-120">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
-   <span data-ttu-id="be533-121">如果您正在跨多个子网设置一个可用性组侦听器并计划使用静态 IP 地址，则对于承载您要为其创建侦听器的可用性组的可用性副本的每个子网，您需要获取其静态 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="be533-121">If you are setting up an availability group listener across multiple subnets and plan to use static IP addresses, you need to get the static IP address of every subnet that hosts an availability replica for the availability group for which you are creating the listener.</span></span> <span data-ttu-id="be533-122">通常，您需要向网络管理员索取静态 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="be533-122">Usually, you will need to ask your network administrators for the static IP addresses.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="be533-123">在创建你的第一个侦听程序之前，我们强烈建议你阅读 [AlwaysOn 客户端连接 (SQL Server)](always-on-client-connectivity-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="be533-123">Before you create your first listener, we strongly recommend that you read [AlwaysOn Client Connectivity &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md).</span></span>  
  
###  <a name="requirements-for-the-dns-name-of-an-availability-group-listener"></a><a name="DNSnameReqs"></a> <span data-ttu-id="be533-124">可用性组侦听器的 DNS 名称的要求</span><span class="sxs-lookup"><span data-stu-id="be533-124">Requirements for the DNS Name of an Availability Group Listener</span></span>  
 <span data-ttu-id="be533-125">每个可用性组侦听器都需要一个 DNS 主机名，该名称在域和 NetBIOS 中是唯一的。</span><span class="sxs-lookup"><span data-stu-id="be533-125">Each availability group listener requires a DNS host name that is unique in the domain and in NetBIOS.</span></span> <span data-ttu-id="be533-126">DNS 名称为字符串值。</span><span class="sxs-lookup"><span data-stu-id="be533-126">The DNS name is a string value.</span></span> <span data-ttu-id="be533-127">该名称只能包含字母数字字符、破折号 (-) 和连字符 (_)，顺序不分先后。</span><span class="sxs-lookup"><span data-stu-id="be533-127">This name can contain only alphanumeric characters, dashes (-), and hyphens (_), in any order.</span></span> <span data-ttu-id="be533-128">DNS 主机名不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="be533-128">DNS host names are case insensitive.</span></span> <span data-ttu-id="be533-129">最大长度为 63 个字符，但是，在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中，您可以指定的最大长度为 15 个字符。</span><span class="sxs-lookup"><span data-stu-id="be533-129">The maximum length is 63 characters, however, in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], the maximum length you can specify is 15 characters.</span></span>  
  
 <span data-ttu-id="be533-130">我们建议您指定一个有意义的字符串。</span><span class="sxs-lookup"><span data-stu-id="be533-130">We recommend that you specify a meaningful string.</span></span> <span data-ttu-id="be533-131">例如，对于名为 `AG1`的可用性组，有意义的 DNS 主机名将是 `ag1-listener`。</span><span class="sxs-lookup"><span data-stu-id="be533-131">For example, for an availability group named `AG1`, a meaningful DNS host name would be `ag1-listener`.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="be533-132">NetBIOS 只识别 dns_name 中的前 15 个字符。</span><span class="sxs-lookup"><span data-stu-id="be533-132">NetBIOS recognizes only the first 15 chars in the dns_name.</span></span> <span data-ttu-id="be533-133">如果您的两个 WSFC 群集均由同一 Active Directory 控制，而您试图使用超过 15 个字符的名称（具有相同的 15 字符前缀）在这两个群集中创建可用性组侦听器，此时您将收到错误，报告无法使虚拟网络名称资源联机。</span><span class="sxs-lookup"><span data-stu-id="be533-133">If you have two WSFC clusters that are controlled by the same Active Directory and you try to create availability group listeners in both of clusters using names with more than 15 characters and an identical 15 character prefix, you will get an error reporting that the Virtual Network Name resource could not be brought online.</span></span> <span data-ttu-id="be533-134">有关 DNS 名称的前缀命名规则的信息，请参阅 [分配域名](https://technet.microsoft.com/library/cc731265\(WS.10\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="be533-134">For information about prefix naming rules for DNS names, see [Assigning Domain Names](https://technet.microsoft.com/library/cc731265\(WS.10\).aspx).</span></span>  
  
###  <a name="windows-permissions"></a><a name="WinPermissions"></a> <span data-ttu-id="be533-135">Windows 权限</span><span class="sxs-lookup"><span data-stu-id="be533-135">Windows Permissions</span></span>  
  
|<span data-ttu-id="be533-136">权限</span><span class="sxs-lookup"><span data-stu-id="be533-136">Permissions</span></span>|<span data-ttu-id="be533-137">链接</span><span class="sxs-lookup"><span data-stu-id="be533-137">Link</span></span>|  
|-----------------|----------|  
|<span data-ttu-id="be533-138">托管可用性组的 WSFC 群集的群集对象名称 (CNO) 必须具有“创建计算机对象”  权限。</span><span class="sxs-lookup"><span data-stu-id="be533-138">The cluster object name (CNO) of WSFC cluster that is hosting the availability group must have **Create Computer objects** permission.</span></span><br /><br /> <span data-ttu-id="be533-139">在 Active Directory 中，CNO 默认不具有显式“创建计算机对象”  权限，并且可以创建 10 个虚拟计算机对象 (VCO)。</span><span class="sxs-lookup"><span data-stu-id="be533-139">In Active Directory, a CNO by default does not have **Create Computer objects** permission explicitly and can create 10 virtual computer objects (VCOs).</span></span> <span data-ttu-id="be533-140">在创建了 10 个 VCO 后，再创建 VCO 将失败。</span><span class="sxs-lookup"><span data-stu-id="be533-140">After 10 VCOs are created, the creation of additional VCOs will fail.</span></span> <span data-ttu-id="be533-141">可通过将权限显式授予 WSFC 群集的 CNO，避免发生此情况。</span><span class="sxs-lookup"><span data-stu-id="be533-141">You can avoid this by granting the permission explicitly to the WSFC cluster's CNO.</span></span> <span data-ttu-id="be533-142">请注意，您已删除的可用性组的 VCO 并不自动在 Active Directory 中删除，因此，在手动删除它们之前，10 个 VCO 的默认数目限制仍会将其计算在内。</span><span class="sxs-lookup"><span data-stu-id="be533-142">Note that VCOs for availability groups that you have deleted are not automatically deleted in Active Directory and count against your 10 VCO default limit unless they are manually deleted.</span></span><br /><br /> <span data-ttu-id="be533-143">注意：在某些组织中，安全策略禁止向单独用户帐户授予“创建计算机对象”权限  。</span><span class="sxs-lookup"><span data-stu-id="be533-143">Note: In some organizations, the security policy prohibits granting **Create Computer objects** permission to individual user accounts.</span></span>|<span data-ttu-id="be533-144">为安装此群集的人员配置帐户的步骤（位于[故障转移群集分步指南  ：在 Active Directory 中配置帐户](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_installer)中）</span><span class="sxs-lookup"><span data-stu-id="be533-144">*Steps for configuring the account for the person who installs the cluster* in [Failover Cluster Step-by-Step Guide: Configuring Accounts in Active Directory](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_installer)</span></span><br /><br /> <span data-ttu-id="be533-145">预配置群集名称帐户的步骤（位于[故障转移群集分步指南  ：在 Active Directory 中配置帐户](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_precreating)中）</span><span class="sxs-lookup"><span data-stu-id="be533-145">*Steps for prestaging the cluster name account* in [Failover Cluster Step-by-Step Guide: Configuring Accounts in Active Directory](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_precreating)</span></span>|  
|<span data-ttu-id="be533-146">如果你的组织要求你为侦听器虚拟网络名称预配置计算机帐户，则你需要具有  “帐户操作员”组的成员资格或域管理员的帮助。</span><span class="sxs-lookup"><span data-stu-id="be533-146">If your organization requires that you prestage the computer account for a listener virtual network name, you will need membership in the **Account Operator** group or your domain administrator's assistance.</span></span><br /><br /> <span data-ttu-id="be533-147">提示：一般情况下，最简单的方法是不为侦听程序虚拟网络名称预配置计算机帐户。</span><span class="sxs-lookup"><span data-stu-id="be533-147">Tip: Generally, it is simplest not to prestage the computer account for a listener virtual network name.</span></span> <span data-ttu-id="be533-148">如果可以，请在运行 WSFC 高可用性向导时自动创建并配置该帐户。</span><span class="sxs-lookup"><span data-stu-id="be533-148">If you can, let the account to be created and configured automatically when you run the WSFC High Availability wizard.</span></span>|<span data-ttu-id="be533-149">*故障转移群集分步指南：在 Active Directory 中配置帐户* 中的 [为群集服务或应用程序预配置帐户的步骤](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_precreating2)。</span><span class="sxs-lookup"><span data-stu-id="be533-149">*Steps for prestaging an account for a clustered service or application* in [Failover Cluster Step-by-Step Guide: Configuring Accounts in Active Directory](https://technet.microsoft.com/library/cc731002\(WS.10\).aspx#BKMK_steps_precreating2).</span></span>|  
  
###  <a name="sql-server-permissions"></a><a name="SqlPermissions"></a> <span data-ttu-id="be533-150">SQL Server 权限</span><span class="sxs-lookup"><span data-stu-id="be533-150">SQL Server Permissions</span></span>  
  
|<span data-ttu-id="be533-151">任务</span><span class="sxs-lookup"><span data-stu-id="be533-151">Task</span></span>|<span data-ttu-id="be533-152">权限</span><span class="sxs-lookup"><span data-stu-id="be533-152">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="be533-153">创建可用性组侦听器</span><span class="sxs-lookup"><span data-stu-id="be533-153">To create an availability group listener</span></span>|<span data-ttu-id="be533-154">需要 **sysadmin** 固定服务器角色的成员资格，以及 CREATE AVAILABILITY GROUP 服务器权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="be533-154">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
|<span data-ttu-id="be533-155">修改现有可用性组侦听器</span><span class="sxs-lookup"><span data-stu-id="be533-155">To modify an existing availability group listener</span></span>|<span data-ttu-id="be533-156">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="be533-156">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="be533-157">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="be533-157">Using SQL Server Management Studio</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="be533-158">[“新建可用性组”向导 ](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) 支持为新可用性组创建侦听程序。</span><span class="sxs-lookup"><span data-stu-id="be533-158">The [New Availability Group wizard](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) supports creation of the listener for a new availability group.</span></span>  
  
 <span data-ttu-id="be533-159">**创建和配置可用性组侦听器**</span><span class="sxs-lookup"><span data-stu-id="be533-159">**To create or configure an availability group listener**</span></span>  
  
1.  <span data-ttu-id="be533-160">在对象资源管理器中，连接到承载可用性组的主副本的服务器实例，然后单击此服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="be533-160">In Object Explorer, connect to the server instance that hosts the primary replica of the availability group, and click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="be533-161">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="be533-161">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="be533-162">单击您要配置其侦听器的可用性组，然后选择以下备选方法之一：</span><span class="sxs-lookup"><span data-stu-id="be533-162">Click the availability group whose listener you want to configure, and choose one of the following alternatives:</span></span>  
  
    -   <span data-ttu-id="be533-163">若要创建一个侦听程序，请右键单击“可用性组侦听程序”  节点，然后选择“新建侦听程序”  命令。</span><span class="sxs-lookup"><span data-stu-id="be533-163">To create a listener, right-click the **Availability group Listeners** node, and select the **New Listener** command.</span></span> <span data-ttu-id="be533-164">这将打开 **“新建可用性组侦听器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="be533-164">This opens the **New Availability Group Listener** dialog box.</span></span> <span data-ttu-id="be533-165">有关详细信息，请参阅本主题后面的[添加可用性组侦听程序（对话框）](#AddAgListenerDialog)。</span><span class="sxs-lookup"><span data-stu-id="be533-165">For more information, see [Add Availability Group Listener (Dialog Box)](#AddAgListenerDialog), later in this topic.</span></span>  
  
    -   <span data-ttu-id="be533-166">若要更改现有侦听程序的端口号，请展开“可用性组侦听程序”  节点，右键单击此侦听程序，然后选择“属性”  命令。</span><span class="sxs-lookup"><span data-stu-id="be533-166">To change the port number of an existing listener, expand the **Availability group Listeners** node, right-click the listener, and select the **Properties** command.</span></span> <span data-ttu-id="be533-167">在 **“端口”** 字段中输入新的端口号，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="be533-167">Enter the new port number into the **Port** field, and click **OK**.</span></span>  
  
###  <a name="new-availability-group-listener-dialog-box"></a><a name="AddAgListenerDialog"></a> <span data-ttu-id="be533-168">新建可用性组（对话框）</span><span class="sxs-lookup"><span data-stu-id="be533-168">New Availability Group Listener (Dialog Box)</span></span>  
 <span data-ttu-id="be533-169">**侦听器 DNS 名称**</span><span class="sxs-lookup"><span data-stu-id="be533-169">**Listener DNS Name**</span></span>  
 <span data-ttu-id="be533-170">指定可用性组侦听器的 DNS 主机名。</span><span class="sxs-lookup"><span data-stu-id="be533-170">Specifies the DNS host name of the availability group listener.</span></span> <span data-ttu-id="be533-171">DNS 名称为字符串，且在域和 NetBIOS 中必须唯一。</span><span class="sxs-lookup"><span data-stu-id="be533-171">The DNS name is a string  must be unique in the domain and in NetBIOS.</span></span> <span data-ttu-id="be533-172">该名称只能包含字母数字字符、破折号 (-) 和连字符 (_)，顺序不分先后。</span><span class="sxs-lookup"><span data-stu-id="be533-172">This name can contain only alphanumeric characters, dashes (-), and hyphens (_), in any order.</span></span> <span data-ttu-id="be533-173">DNS 主机名不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="be533-173">DNS host names are case insensitive.</span></span> <span data-ttu-id="be533-174">最大长度为 15 个字符。</span><span class="sxs-lookup"><span data-stu-id="be533-174">The maximum length is 15 characters.</span></span>  
  
 <span data-ttu-id="be533-175">有关详细信息，请参阅本主题前面的 [可用性组侦听器的 DNS 名称的要求](#DNSnameReqs)。</span><span class="sxs-lookup"><span data-stu-id="be533-175">For more information, see [Requirements for the DNS Name of an Availability Group Listener](#DNSnameReqs), earlier in this topic.</span></span>  
  
 <span data-ttu-id="be533-176">端口 </span><span class="sxs-lookup"><span data-stu-id="be533-176">**Port**</span></span>  
 <span data-ttu-id="be533-177">该侦听器使用的 TPC 端口。</span><span class="sxs-lookup"><span data-stu-id="be533-177">The TPC port used by this listener.</span></span>  
  
 <span data-ttu-id="be533-178">**网络模式**</span><span class="sxs-lookup"><span data-stu-id="be533-178">**Network Mode**</span></span>  
 <span data-ttu-id="be533-179">指示该侦听器使用的 TCP 协议，选择如下一种：</span><span class="sxs-lookup"><span data-stu-id="be533-179">Indicates the TCP protocol used by the listener, one of:</span></span>  
  
 <span data-ttu-id="be533-180">**DHCP**</span><span class="sxs-lookup"><span data-stu-id="be533-180">**DHCP**</span></span>  
 <span data-ttu-id="be533-181">侦听器将使用运行动态主机配置协议 (DHCP) 的服务器分配的动态 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="be533-181">The listener will us a dynamic IP address that is assigned by a server running the Dynamic Host Configuration Protocol (DHCP).</span></span> <span data-ttu-id="be533-182">DHCP 仅限于单个子网。</span><span class="sxs-lookup"><span data-stu-id="be533-182">DHCP is limited to a single subnet.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="be533-183">不建议在生产环境中使用 DHCP。</span><span class="sxs-lookup"><span data-stu-id="be533-183">We do not recommend DHCP in production environment.</span></span> <span data-ttu-id="be533-184">如果停止工作且 DHCP IP 租期已到，则需要额外的时间来注册与侦听器 DNS 名称相关联且影响客户端连接的新 DHCP 网络 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="be533-184">If there is a down time and the DHCP IP lease expires, extra time is required to register the new DHCP network IP address that is associated with the listener DNS name and impact the client connectivity.</span></span> <span data-ttu-id="be533-185">但是，DHCP 适合用于设置开发和测试环境以验证可用性组的基本功能并适合与应用程序集成。</span><span class="sxs-lookup"><span data-stu-id="be533-185">However, DHCP is good for setting up your development and testing environment to verify basic functions of availability groups and for integration with your applications.</span></span>  
  
 <span data-ttu-id="be533-186">**静态 IP**</span><span class="sxs-lookup"><span data-stu-id="be533-186">**Static IP**</span></span>  
 <span data-ttu-id="be533-187">侦听器将使用一个或多个静态 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="be533-187">The listener will use one or more static IP addresses.</span></span> <span data-ttu-id="be533-188">其他 IP 地址是可选的。</span><span class="sxs-lookup"><span data-stu-id="be533-188">Additional IP addresses are optional.</span></span> <span data-ttu-id="be533-189">若要跨多个子网创建一个可用性组侦听器，必须在侦听器配置中为每个子网指定一个静态 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="be533-189">To create an availability group listener across multiple subnets, for each subnet you must specify a static IP address in the listener configuration.</span></span> <span data-ttu-id="be533-190">请与您的网络管理员联系以获取这些静态 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="be533-190">Contact your network administrator to get these static IP addresses.</span></span>  
  
 <span data-ttu-id="be533-191">如果您选择 **“静态 IP”** ，则会在 **“网络模式”** 字段下出现一个子网网格。</span><span class="sxs-lookup"><span data-stu-id="be533-191">If you select **Static IP** a subnet grid appears below the **Network Mode** field.</span></span> <span data-ttu-id="be533-192">此网格将显示有关该可用性组侦听器可以访问的每个子网的信息。</span><span class="sxs-lookup"><span data-stu-id="be533-192">This grid displays information about each subnet that can be accessed by this availability group listener.</span></span> <span data-ttu-id="be533-193">在通过单击 **“添加”** 添加静态 IP 地址之前，该网格为空。</span><span class="sxs-lookup"><span data-stu-id="be533-193">This grid is empty until you add a static IP address by clicking **Add**.</span></span>  
  
 <span data-ttu-id="be533-194">这些列如下所示：</span><span class="sxs-lookup"><span data-stu-id="be533-194">The columns are as follows:</span></span>  
  
 <span data-ttu-id="be533-195">**子网**</span><span class="sxs-lookup"><span data-stu-id="be533-195">**Subnet**</span></span>  
 <span data-ttu-id="be533-196">显示您添加到可用性组侦听器的每个子网的标识符。</span><span class="sxs-lookup"><span data-stu-id="be533-196">Displays the identifier of each subnet that you add to the availability group listener.</span></span>  
  
 <span data-ttu-id="be533-197">**IP 地址**</span><span class="sxs-lookup"><span data-stu-id="be533-197">**IP Address**</span></span>  
 <span data-ttu-id="be533-198">显示给定子网的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="be533-198">Displays the IP address of a given subnet.</span></span>  <span data-ttu-id="be533-199">对于给定子网，静态 IP 地址可以是 IPv4 地址或 IPv6 地址。</span><span class="sxs-lookup"><span data-stu-id="be533-199">For a given subnet, the IP address is either an IPv4 address or an IPv6 address.</span></span>  
  
 <span data-ttu-id="be533-200">**添加**</span><span class="sxs-lookup"><span data-stu-id="be533-200">**Add**</span></span>  
 <span data-ttu-id="be533-201">单击“添加”可将静态 IP 地址添加到所选子网，或添加到该侦听器的其他子网。</span><span class="sxs-lookup"><span data-stu-id="be533-201">Click to add to add a static IP address to a selected subnet or to another subnet for this listener.</span></span> <span data-ttu-id="be533-202">这将打开 **“添加 IP 地址”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="be533-202">This opens the **Add IP Address** dialog box.</span></span> <span data-ttu-id="be533-203">有关详细信息，请参阅[添加 IP 地址对话框 (SQL Server Management Studio)](add-ip-address-dialog-box-sql-server-management-studio.md) 帮助主题。</span><span class="sxs-lookup"><span data-stu-id="be533-203">For more information, see the [Add IP Address Dialog Box &#40;SQL Server Management Studio&#41;](add-ip-address-dialog-box-sql-server-management-studio.md) help topic.</span></span>  
  
 <span data-ttu-id="be533-204">**删除**</span><span class="sxs-lookup"><span data-stu-id="be533-204">**Remove**</span></span>  
 <span data-ttu-id="be533-205">单击此项可以从侦听器中移除所选子网。</span><span class="sxs-lookup"><span data-stu-id="be533-205">Click to remove the selected subnet from this listener.</span></span>  
  
 <span data-ttu-id="be533-206">**确定**</span><span class="sxs-lookup"><span data-stu-id="be533-206">**OK**</span></span>  
 <span data-ttu-id="be533-207">单击此选项可创建指定的可用性组侦听器。</span><span class="sxs-lookup"><span data-stu-id="be533-207">Click to create the specified availability group listener.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="be533-208">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="be533-208">Using Transact-SQL</span></span>  

### <a name="to-create-or-configure-an-availability-group-listener"></a><span data-ttu-id="be533-209">创建和配置可用性组侦听器</span><span class="sxs-lookup"><span data-stu-id="be533-209">To create or configure an availability group listener</span></span>
  
1.  <span data-ttu-id="be533-210">连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="be533-210">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="be533-211">使用 [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql) 语句的 LISTENER 选项或 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 语句的 ADD LISTENER 选项。</span><span class="sxs-lookup"><span data-stu-id="be533-211">Use the LISTENER option of the [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql) statement or the ADD LISTENER option of the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement.</span></span>  
  
     <span data-ttu-id="be533-212">下面的示例将可用性组侦听器添加到名为 `MyAg2`的现有可用性组。</span><span class="sxs-lookup"><span data-stu-id="be533-212">The following example adds an availability group listener to an existing availability group named `MyAg2`.</span></span> <span data-ttu-id="be533-213">将为此侦听器指定唯一的 DNS 名称 `MyAg2ListenerIvP6`。</span><span class="sxs-lookup"><span data-stu-id="be533-213">A unique DNS name, `MyAg2ListenerIvP6`, is specified for this listener.</span></span> <span data-ttu-id="be533-214">两个副本位于不同的子网，因此按照建议，侦听器使用静态 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="be533-214">The two replicas are on different subnets, so , as recommended, the listener uses static IP addresses.</span></span> <span data-ttu-id="be533-215">对于这两个可用性副本中的每一个，WITH IP 子句都指定一个将使用 IPv6 格式的静态 IP 地址 `2001:4898:f0:f00f::cf3c and 2001:4898:e0:f213::4ce2`。</span><span class="sxs-lookup"><span data-stu-id="be533-215">For each of the two availability replicas, the WITH IP clause specifies a static IP address, `2001:4898:f0:f00f::cf3c and 2001:4898:e0:f213::4ce2`, which use the IPv6 format.</span></span> <span data-ttu-id="be533-216">此示例还指定使用可选的 PORT 参数来将端口 `60173` 指定为侦听器端口。</span><span class="sxs-lookup"><span data-stu-id="be533-216">This example also specifies uses the optional PORT argument to specify port `60173` as the listener port.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAg2   
          ADD LISTENER 'MyAg2ListenerIvP6' ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173 );   
    GO  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="be533-217">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="be533-217">Using PowerShell</span></span>  

### <a name="to-create-or-configure-an-availability-group-listener"></a><span data-ttu-id="be533-218">创建和配置可用性组侦听器</span><span class="sxs-lookup"><span data-stu-id="be533-218">To create or configure an availability group listener</span></span> 
  
1.  <span data-ttu-id="be533-219">将目录 (`cd`) 更改为承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="be533-219">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="be533-220">使用下列 cmdlet 之一创建或修改可用性组侦听器：</span><span class="sxs-lookup"><span data-stu-id="be533-220">To create or modify an availability group listener use one of the following cmdlets:</span></span>  
  
     `New-SqlAvailabilityGroupListener`  
     <span data-ttu-id="be533-221">创建一个新的可用性组侦听器，并将其附加到一个现有可用性组。</span><span class="sxs-lookup"><span data-stu-id="be533-221">Creates a new availability group listener and attaches it to an existing availability group.</span></span>  
  
     <span data-ttu-id="be533-222">例如，下列 `New-SqlAvailabilityGroupListener` 命令为可用性组 `MyListener` 创建命为 `MyAg` 的可用性组侦听器。</span><span class="sxs-lookup"><span data-stu-id="be533-222">For example, the following `New-SqlAvailabilityGroupListener` command creates an availability group listener named `MyListener` for the availability group `MyAg`.</span></span> <span data-ttu-id="be533-223">此侦听器将使用传递到 `-StaticIp` 参数的 IPv4 地址作为其虚拟 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="be533-223">This listener will use the IPv4 address passed to the `-StaticIp` parameter as its virtual IP address.</span></span>  
  
    ```powershell
    New-SqlAvailabilityGroupListener -Name MyListener `
    -StaticIp '192.168.3.1/255.255.252.0' `
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg
    ```  
  
     `Set-SqlAvailabilityGroupListener`  
     <span data-ttu-id="be533-224">修改现有可用性组侦听器的端口设置。</span><span class="sxs-lookup"><span data-stu-id="be533-224">Modifies the port setting on an existing availability group listener.</span></span>  
  
     <span data-ttu-id="be533-225">例如，下列 `Set-SqlAvailabilityGroupListener` 命令将名为 `MyListener` 的可用性组侦听器的端口号设置为 `1535`。</span><span class="sxs-lookup"><span data-stu-id="be533-225">For example, the following `Set-SqlAvailabilityGroupListener` command sets the port number for the availability group listener named `MyListener` to `1535`.</span></span> <span data-ttu-id="be533-226">此端口用于侦听与侦听器的连接。</span><span class="sxs-lookup"><span data-stu-id="be533-226">This port is used to listen for connections to the listener.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityGroupListener -Port 1535 `
    -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AGListeners\MyListener  
    ```  
  
     `Add-SqlAGListenerstaticIp`  
     <span data-ttu-id="be533-227">将一个静态 IP 地址添加到现有的可用性组侦听器配置。</span><span class="sxs-lookup"><span data-stu-id="be533-227">Adds a static IP address to an existing availability group listener configuration.</span></span> <span data-ttu-id="be533-228">此 IP 地址可以是带子网的 IPv4 地址或 IPv6 地址。</span><span class="sxs-lookup"><span data-stu-id="be533-228">The IP address can be an IPv4 address with subnet, or an IPv6 address.</span></span>  
  
     <span data-ttu-id="be533-229">例如，下列 `Add-SqlAGListenerstaticIp` 命令将一个静态 IPv4 地址添加到可用性组 `MyListener` 的可用性组侦听器 `MyAg`。</span><span class="sxs-lookup"><span data-stu-id="be533-229">For example, the following `Add-SqlAGListenerstaticIp` command adds a static IPv4 address to the availability group listener `MyListener` on the availability group `MyAg`.</span></span> <span data-ttu-id="be533-230">此 IPv6 地址用作子网 `255.255.252.0`上侦听器的虚拟 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="be533-230">This IPv6 address serves as the virtual IP address of the listener on the subnet `255.255.252.0`.</span></span> <span data-ttu-id="be533-231">如果可用性组跨多个子网，则应将针对每个子网的静态 IP 地址添加到侦听器。</span><span class="sxs-lookup"><span data-stu-id="be533-231">If the availability group spans multiple subnets, you should add a static IP address for each subnet to the listener.</span></span>  
  
    ```powershell
    $path = "SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AGListeners\ MyListener" `
    Add-SqlAGListenerstaticIp -Path $path `
    -StaticIp "2001:0db8:85a3:0000:0000:8a2e:0370:7334"  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="be533-232">若要查看 cmdlet 的语法，请在 PowerShell 环境中使用**get-help** cmdlet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="be533-232">To view the syntax of a cmdlet, use the **Get-Help**  cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="be533-233">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="be533-233">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="be533-234">若要设置并使用 SQL Server PowerShell 提供程序，请参阅[SQL Server PowerShell 提供程序](../../../powershell/sql-server-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="be533-234">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>
  
## <a name="troubleshooting"></a><span data-ttu-id="be533-235">疑难解答</span><span class="sxs-lookup"><span data-stu-id="be533-235">Troubleshooting</span></span>  
  
###  <a name="failure-to-create-an-availability-group-listener-because-of-active-directory-quotas"></a><a name="ADQuotas"></a><span data-ttu-id="be533-236">由于 Active Directory 配额，导致无法创建可用性组侦听器</span><span class="sxs-lookup"><span data-stu-id="be533-236">Failure to Create An Availability Group Listener Because of Active Directory Quotas</span></span>  
 <span data-ttu-id="be533-237">新的可用性组侦听器可能在创建时失败，因为您已经达到参与群集节点计算机帐户的 Active Directory 配额。</span><span class="sxs-lookup"><span data-stu-id="be533-237">The creation of a new availability group listener may fail upon creation because you have reached an Active Directory quota for the participating cluster node machine account.</span></span>  <span data-ttu-id="be533-238">有关详细信息，请参阅下列文章：</span><span class="sxs-lookup"><span data-stu-id="be533-238">For more information, see the following articles:</span></span>  
  
-   [<span data-ttu-id="be533-239">超链接 " https://support.microsoft.com/kb/307532 " 如何在群集服务帐户修改计算机对象时对其进行故障排除</span><span class="sxs-lookup"><span data-stu-id="be533-239">HYPERLINK "https://support.microsoft.com/kb/307532" How to Troubleshoot the Cluster Service Account When It Modifies Computer Objects</span></span>](https://support.microsoft.com/kb/307532)  
  
-   <span data-ttu-id="be533-240">[超链接 " https://technet.microsoft.com/library/cc904295(WS.10).aspx " Active Directory 配额](https://technet.microsoft.com/library/cc904295\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="be533-240">[HYPERLINK "https://technet.microsoft.com/library/cc904295(WS.10).aspx" Active Directory Quotas](https://technet.microsoft.com/library/cc904295\(WS.10\).aspx)</span></span>  
  
##  <a name="follow-up-after-creating-an-availability-group-listener"></a><a name="FollowUp"></a><span data-ttu-id="be533-241">跟进：在创建可用性组侦听器之后</span><span class="sxs-lookup"><span data-stu-id="be533-241">Follow-up: After Creating an Availability Group Listener</span></span>  
  
###  <a name="multisubnetfailover-keyword-and-associated-features"></a><a name="MultiSubnetFailover"></a><span data-ttu-id="be533-242">MultiSubnetFailover 关键字和相关功能</span><span class="sxs-lookup"><span data-stu-id="be533-242">MultiSubnetFailover Keyword and Associated Features</span></span>  
 <span data-ttu-id="be533-243">`MultiSubnetFailover` 是一个新连接字符串关键字，在 SQL Server 2012 中可使用它通过 AlwaysOn 可用性组和 AlwaysOn 故障转移群集实例进行更快速的故障转移。</span><span class="sxs-lookup"><span data-stu-id="be533-243">`MultiSubnetFailover` is a new connection string keyword used to enable faster failover with AlwaysOn Availability Groups and AlwaysOn Failover Cluster Instances in SQL Server 2012.</span></span> <span data-ttu-id="be533-244">在连接字符串中设置 `MultiSubnetFailover=True` 时，将启用以下三个子功能：</span><span class="sxs-lookup"><span data-stu-id="be533-244">The following three sub-features are enabled when `MultiSubnetFailover=True` is set in connection string:</span></span>  
  
-   <span data-ttu-id="be533-245">更快进行多子网故障转移到 AlwaysOn 可用性组或故障转移群集实例的多子网侦听器。</span><span class="sxs-lookup"><span data-stu-id="be533-245">Faster multi-subnet failover to a multi-subnet listener for an AlwaysOn Availability Group or Failover Cluster Instances.</span></span>  
  
-   <span data-ttu-id="be533-246">更快进行单子网故障转移到 AlwaysOn 可用性组或故障转移群集实例的单子网侦听器。</span><span class="sxs-lookup"><span data-stu-id="be533-246">Faster single subnet failover to a single subnet listener for an AlwaysOn Availability Group or Failover Cluster Instances.</span></span>  
  
    -   <span data-ttu-id="be533-247">当连接到具有单个子网中的单个 IP 的侦听器时使用此功能。</span><span class="sxs-lookup"><span data-stu-id="be533-247">This feature is used when connecting to a listener that has a single IP in a single subnet.</span></span> <span data-ttu-id="be533-248">这将进行更频繁的 TCP 连接重试以加快单子网故障转移。</span><span class="sxs-lookup"><span data-stu-id="be533-248">This performs more aggressive TCP connection retries to speed up single subnet failovers.</span></span>  
  
-   <span data-ttu-id="be533-249">多子网 AlwaysOn 故障转移群集实例的命名实例解析。</span><span class="sxs-lookup"><span data-stu-id="be533-249">Named instance resolution to a multi-subnet AlwaysOn Failover Cluster Instance.</span></span>  
  
    -   <span data-ttu-id="be533-250">这将添加对具有多子网端点的 AlwaysOn 故障转移群集实例的命名实例解析支持。</span><span class="sxs-lookup"><span data-stu-id="be533-250">This is to add named instance resolution support for an AlwaysOn Failover Cluster Instances with multiple subnet endpoints.</span></span>  
  
 <span data-ttu-id="be533-251">**NET Framework 3.5 或 OLEDB 不支持 MultiSubnetFailover=True**</span><span class="sxs-lookup"><span data-stu-id="be533-251">**MultiSubnetFailover=True Not Supported by NET Framework 3.5 or OLEDB**</span></span>  
  
 <span data-ttu-id="be533-252">**问题：** 如果你的可用性组或故障转移群集实例具有侦听程序名称 (称为 WSFC 群集管理器中的网络名称或客户端访问点) 根据不同子网中的多个 IP 地址，并且你使用的是具有 .NET Framework 3.5 SP1 或 SQL Native Client 11.0 OLEDB 的 ADO.NET，则可能50% 的客户端与可用性组侦听器的连接请求将达到连接超时。</span><span class="sxs-lookup"><span data-stu-id="be533-252">**Issue:** If your Availability Group or Failover Cluster Instance has a listener name (known as the network name or Client Access Point in the WSFC Cluster Manager) depending on multiple IP addresses from different subnets, and you are using either ADO.NET with .NET Framework 3.5SP1 or SQL Native Client 11.0 OLEDB, potentially 50% of your client-connection requests to the availability group listener will hit a connection timeout.</span></span>  
  
 <span data-ttu-id="be533-253">**解决方法：** 我们建议你执行以下任务之一。</span><span class="sxs-lookup"><span data-stu-id="be533-253">**Workarounds:** We recommend that you do one of the following tasks.</span></span>  
  
-   <span data-ttu-id="be533-254">如果您无权操作群集资源，则将连接超时更改为 30 秒（该值导致 20 秒的 TCP 超时期加上 10 秒的缓冲）。</span><span class="sxs-lookup"><span data-stu-id="be533-254">If do not have the permission to manipulate cluster resources, change your connection timeout to 30 seconds (this value results in a 20-second TCP timeout period plus a 10-second buffer).</span></span>  
  
     <span data-ttu-id="be533-255">优点  ：如果发生跨子网故障转移，则客户端恢复时间将比较短。</span><span class="sxs-lookup"><span data-stu-id="be533-255">**Pros**: If a cross-subnet failover occurs, client recovery time is short.</span></span>  
  
     <span data-ttu-id="be533-256">缺点  ：半数的客户端连接将需要 20 多秒</span><span class="sxs-lookup"><span data-stu-id="be533-256">**Cons**: Half of the client connections will take more than 20 seconds</span></span>  
  
-   <span data-ttu-id="be533-257">如果您有权操作群集资源，则强烈建议您将可用性组侦听器的网络名称设置为 `RegisterAllProvidersIP=0`。</span><span class="sxs-lookup"><span data-stu-id="be533-257">If you have the permission to manipulate cluster resources, the more recommended approach is to set the network name of your availability group listener to `RegisterAllProvidersIP=0`.</span></span> <span data-ttu-id="be533-258">有关详细信息，请参阅本节后面的“RegisterAllProvidersIP 设置”。</span><span class="sxs-lookup"><span data-stu-id="be533-258">For more information, see "RegisterAllProvidersIP Setting" later in this section.</span></span>  
  
     <span data-ttu-id="be533-259">优点  ：无需增加客户端连接超时值。</span><span class="sxs-lookup"><span data-stu-id="be533-259">**Pros:** You do not need to increase your client-connection timeout value.</span></span>  
  
     <span data-ttu-id="be533-260">**缺点：** 如果发生跨子网故障转移，则客户端恢复时间可能为15分钟或更长，具体取决于您的 `HostRecordTTL` 设置以及您的跨站点 DNS/AD 复制计划的设置。</span><span class="sxs-lookup"><span data-stu-id="be533-260">**Cons:** If a cross-subnet failover occurs, the client recovery time could be 15 minutes or longer, depending on your `HostRecordTTL` setting and the setting of your cross-site DNS/AD replication schedule.</span></span>  
  
###  <a name="registerallprovidersip-setting"></a><a name="RegisterAllProvidersIP"></a><span data-ttu-id="be533-261">RegisterAllProvidersIP 设置</span><span class="sxs-lookup"><span data-stu-id="be533-261">RegisterAllProvidersIP Setting</span></span>  
 <span data-ttu-id="be533-262">在使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 PowerShell 创建可用性组侦听器时，将在 WSFC 中创建客户端访问点，其 `RegisterAllProvidersIP` 属性设为 1 (true)。</span><span class="sxs-lookup"><span data-stu-id="be533-262">When you use [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell to create an availability group listener, the Client Access Point is created in WSFC with the `RegisterAllProvidersIP` property set to 1 (true).</span></span> <span data-ttu-id="be533-263">此属性值的影响取决于客户端连接字符串，如下所示：</span><span class="sxs-lookup"><span data-stu-id="be533-263">The effect of this property value depends on the client connection string, as follows:</span></span>  
  
-   <span data-ttu-id="be533-264">将 `MultiSubnetFailover` 设置为 true 的连接字符串</span><span class="sxs-lookup"><span data-stu-id="be533-264">Connection strings that set `MultiSubnetFailover` to true</span></span>  
  
     [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]<span data-ttu-id="be533-265">将 `RegisterAllProvidersIP` 属性设置为1，以便在故障转移后，针对客户端连接字符串指定的客户端，根据建议缩短重新连接时间 `MultiSubnetFailover = True` 。</span><span class="sxs-lookup"><span data-stu-id="be533-265">sets the  `RegisterAllProvidersIP` property to 1 in order to reduce re-connection time after a failover for clients whose client connection strings specify `MultiSubnetFailover = True`, as recommended.</span></span> <span data-ttu-id="be533-266">请注意，为了利用侦听器多子网功能，您的客户端可能会要求支持 `MultiSubnetFailover` 关键字的数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="be533-266">Note that to take advantage of the listener multi-subnet feature, your clients might require a data provider that supports the `MultiSubnetFailover` keyword.</span></span> <span data-ttu-id="be533-267">有关针对多子网故障转移的驱动程序支持的信息，请参阅 [AlwaysOn 客户端连接 (SQL Server)](always-on-client-connectivity-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="be533-267">For information about driver support for multi-subnet failover, see [AlwaysOn Client Connectivity &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md).</span></span>  
  
     <span data-ttu-id="be533-268">有关多子网群集的信息，请参阅 [SQL Server 多子网群集 (SQL Server)](../../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md)为每个可用性组创建一个侦听器。</span><span class="sxs-lookup"><span data-stu-id="be533-268">For information about multi-subnet clustering, see [SQL Server Multi-Subnet Clustering &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md).</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="be533-269">在 `RegisterAllProvidersIP = 1`时，如果您在 WSFC 群集上运行 WSFC 验证配置向导，该向导将生成以下警告消息：</span><span class="sxs-lookup"><span data-stu-id="be533-269">When `RegisterAllProvidersIP = 1`, if you run the WSFC Validate a Configuration Wizard on the WSFC cluster, the wizard generates the following warning message:</span></span>  
    >   
    >  <span data-ttu-id="be533-270">“网络名称 ‘Name:<network_name>’ 的 RegisterAllProviderIP 属性设为 1。对于当前群集配置，该值应设为 0。”</span><span class="sxs-lookup"><span data-stu-id="be533-270">"The RegisterAllProviderIP property for network name 'Name:<network_name>' is set to 1 For the current cluster configuration this value should be set to 0."</span></span>  
    >   
    >  <span data-ttu-id="be533-271">请忽略此消息。</span><span class="sxs-lookup"><span data-stu-id="be533-271">Please ignore this message.</span></span>  
  
-   <span data-ttu-id="be533-272">未将 `MultiSubnetFailover` 设置为 true 的连接字符串</span><span class="sxs-lookup"><span data-stu-id="be533-272">Connection strings that do not set `MultiSubnetFailover` to true</span></span>  
  
     <span data-ttu-id="be533-273">在 `RegisterAllProvidersIP = 1`时，其连接字符串未使用 `MultiSubnetFailover = True`的任何客户端都将会经历高延迟的连接。</span><span class="sxs-lookup"><span data-stu-id="be533-273">When `RegisterAllProvidersIP = 1`, any clients whose connection strings do not use `MultiSubnetFailover = True`, will experience high latency connections.</span></span> <span data-ttu-id="be533-274">发生这种情况的原因是这些客户端将按顺序尝试与所有 IP 的连接。</span><span class="sxs-lookup"><span data-stu-id="be533-274">This occurs because these clients attempt connections to all IPs sequentially.</span></span> <span data-ttu-id="be533-275">相反，如果将 `RegisterAllProvidersIP` 更改为 0，将在 WSFC 群集中的客户端接入点注册活动 IP 地址，从而缩短旧客户端的延迟时间。</span><span class="sxs-lookup"><span data-stu-id="be533-275">In contrast, if `RegisterAllProvidersIP` is changed to 0, the active IP address is registered in the Client Access Point in the WSFC cluster, reducing latency for legacy clients.</span></span> <span data-ttu-id="be533-276">因此，如果您的旧客户端需要连接到某一可用性组侦听器并且不能使用 `MultiSubnetFailover` 属性，我们建议您将更改 `RegisterAllProvidersIP` 为0。</span><span class="sxs-lookup"><span data-stu-id="be533-276">Therefore, if you have legacy clients that need to connect to an availability group listener and cannot use the `MultiSubnetFailover` property, we recommend that you change `RegisterAllProvidersIP` to 0.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="be533-277">在您通过 WSFC 群集（故障转移群集管理器 GUI）创建可用性组侦听器时，`RegisterAllProvidersIP` 默认将为 0 (false)。</span><span class="sxs-lookup"><span data-stu-id="be533-277">When you create an availability group listener through the WSFC cluster (Failover Cluster Manager GUI), `RegisterAllProvidersIP` will be 0 (false) by default.</span></span>  
  
###  <a name="hostrecordttl-setting"></a><a name="HostRecordTTL"></a><span data-ttu-id="be533-278">HostRecordTTL 设置</span><span class="sxs-lookup"><span data-stu-id="be533-278">HostRecordTTL Setting</span></span>  
 <span data-ttu-id="be533-279">默认情况下，客户端缓存 20 分钟的群集 DNS 记录。</span><span class="sxs-lookup"><span data-stu-id="be533-279">By default, clients cache cluster DNS records for 20 minutes.</span></span>  <span data-ttu-id="be533-280">通过缩短缓存记录的 `HostRecordTTL`（生存时间 (TTL)），旧客户端可以更快地重新连接。</span><span class="sxs-lookup"><span data-stu-id="be533-280">By reducing `HostRecordTTL`, the Time to Live (TTL), for the cached record, legacy clients may reconnect more quickly.</span></span>  <span data-ttu-id="be533-281">但是，减小 `HostRecordTTL` 设置还可能导致到 DN 服务器的流量增加。</span><span class="sxs-lookup"><span data-stu-id="be533-281">However, reducing the `HostRecordTTL` setting may also result in increased traffic to the DN servers.</span></span>  
  
###  <a name="sample-powershell-script-to-disable-registerallprovidersip-and-reduce-ttl"></a><a name="SampleScript"></a><span data-ttu-id="be533-282">用于禁用 RegisterAllProvidersIP 和减少 TTL 的示例 PowerShell 脚本</span><span class="sxs-lookup"><span data-stu-id="be533-282">Sample PowerShell Script to Disable RegisterAllProvidersIP and Reduce TTL</span></span>  
 <span data-ttu-id="be533-283">下面的 PowerShell 示例演示如何为侦听器资源配置 `RegisterAllProvidersIP` 和 `HostRecordTTL` 群集参数。</span><span class="sxs-lookup"><span data-stu-id="be533-283">The following PowerShell example demonstrates how to configure both the `RegisterAllProvidersIP` and `HostRecordTTL` cluster parameters for the listener resource.</span></span>  <span data-ttu-id="be533-284">DNS 记录将缓存 5 分钟，而不是默认的 20 分钟。</span><span class="sxs-lookup"><span data-stu-id="be533-284">The DNS record will be cached for 5 minutes rather than the default 20 minutes.</span></span>  <span data-ttu-id="be533-285">同时修改两个群集参数可以缩短无法使用 `MultiSubnetFailover` 参数的旧客户端在故障转移后连接到正确 IP 地址的时间。</span><span class="sxs-lookup"><span data-stu-id="be533-285">Modifying both cluster parameters may reduce the time to connect to the correct IP address after a failover for legacy clients that cannot use the `MultiSubnetFailover` parameter.</span></span>  <span data-ttu-id="be533-286">使用您要更改的侦听器名称替换 `yourListenerName` 。</span><span class="sxs-lookup"><span data-stu-id="be533-286">Replace `yourListenerName` with the name of the listener that you are changing.</span></span>  
  
```powershell
Import-Module FailoverClusters  
Get-ClusterResource yourListenerName | Set-ClusterParameter RegisterAllProvidersIP 0
Get-ClusterResource yourListenerName|Set-ClusterParameter HostRecordTTL 300  
Stop-ClusterResource yourListenerName  
Start-ClusterResource yourAGResource  
```  
  
 <span data-ttu-id="be533-287">有关故障转移期间的恢复时间的详细信息，请参阅 [Client Recovery Latency During Failover](../../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md#DNS)。</span><span class="sxs-lookup"><span data-stu-id="be533-287">For more information about recovery times during failover, see [Client Recovery Latency During Failover](../../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md#DNS).</span></span>  
  
###  <a name="follow-up-recommendations"></a><a name="FollowUpRecommendations"></a><span data-ttu-id="be533-288">跟进建议</span><span class="sxs-lookup"><span data-stu-id="be533-288">Follow-up Recommendations</span></span>  
 <span data-ttu-id="be533-289">在创建可用性组侦听器后：</span><span class="sxs-lookup"><span data-stu-id="be533-289">After you create an availability group listener:</span></span>  
  
-   <span data-ttu-id="be533-290">请求您的网络管理员将该侦听器的 IP 地址保留为专用。</span><span class="sxs-lookup"><span data-stu-id="be533-290">Ask your network administrator to reserve the listener's IP address for its exclusive use.</span></span>  
  
-   <span data-ttu-id="be533-291">将该侦听器的 DNS 主机名提供给应用程序开发人员，以便在请求与此可用性组的客户端连接时用于连接字符串中。</span><span class="sxs-lookup"><span data-stu-id="be533-291">Give the listener's DNS host name to application developers to use in connection strings when requesting client connections to this availability group.</span></span>  
  
-   <span data-ttu-id="be533-292">如有可能，鼓励开发人员更新客户端连接字符串，以便指定 `MultiSubnetFailover = True`。</span><span class="sxs-lookup"><span data-stu-id="be533-292">Encourage developers to update client connection strings to specify `MultiSubnetFailover = True`, if possible.</span></span> <span data-ttu-id="be533-293">有关针对多子网故障转移的驱动程序支持的信息，请参阅 [AlwaysOn 客户端连接 (SQL Server)](always-on-client-connectivity-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="be533-293">For information about driver support for multi-subnet failover, see [AlwaysOn Client Connectivity &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md).</span></span>  
  
###  <a name="create-an-additional-listener-for-an-availability-group-optional"></a><a name="CreateAdditionalListener"></a><span data-ttu-id="be533-294">为可用性组创建其他侦听器 (可选) </span><span class="sxs-lookup"><span data-stu-id="be533-294">Create an Additional Listener for an Availability Group (Optional)</span></span>  
 <span data-ttu-id="be533-295">通过 SQL Server 创建一个侦听器之后，您可以添加其他侦听器，如下所示：</span><span class="sxs-lookup"><span data-stu-id="be533-295">After you create one listener through SQL Server, you can add an additional listener, as follows:</span></span>  
  
1.  <span data-ttu-id="be533-296">使用下列任一工具创建侦听器：</span><span class="sxs-lookup"><span data-stu-id="be533-296">Create the listener using either of the following tools:</span></span>  
  
    -   <span data-ttu-id="be533-297">**使用 WSFC 故障转移群集管理器：**</span><span class="sxs-lookup"><span data-stu-id="be533-297">**Using WSFC Failover Cluster Manager:**</span></span>  
  
        1.  <span data-ttu-id="be533-298">添加客户端访问点并配置 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="be533-298">Add a client access point and configure the IP address.</span></span>  
  
        2.  <span data-ttu-id="be533-299">使侦听器联机。</span><span class="sxs-lookup"><span data-stu-id="be533-299">Bring the listener online.</span></span>  
  
        3.  <span data-ttu-id="be533-300">向 WSFC 可用性组资源添加一个依赖项。</span><span class="sxs-lookup"><span data-stu-id="be533-300">Add a dependency to the WSFC availability group resource.</span></span>  
  
         <span data-ttu-id="be533-301">有关故障转移群集管理器的对话框和选项卡的信息，请参阅 [用户界面：故障转移群集管理器管理单元](https://technet.microsoft.com/library/cc772502.aspx)。</span><span class="sxs-lookup"><span data-stu-id="be533-301">For information about the dialog boxes and tabs of the Failover Cluster Manager, see [User Interface: The Failover Cluster Manager Snap-In](https://technet.microsoft.com/library/cc772502.aspx).</span></span>  
  
    -   <span data-ttu-id="be533-302">**将 Windows PowerShell 用于故障转移群集：**</span><span class="sxs-lookup"><span data-stu-id="be533-302">**Using Windows PowerShell for failover clusters:**</span></span>  
  
        1.  <span data-ttu-id="be533-303">使用 [Add-ClusterResource](https://technet.microsoft.com/library/ee460983.aspx) 创建网络名称和 IP 地址资源。</span><span class="sxs-lookup"><span data-stu-id="be533-303">Use [Add-ClusterResource](https://technet.microsoft.com/library/ee460983.aspx) to create a network name and the IP address resources.</span></span>  
  
        2.  <span data-ttu-id="be533-304">使用 [Start-ClusterResource](https://technet.microsoft.com/library/ee461056.aspx) 启动网络名称资源。</span><span class="sxs-lookup"><span data-stu-id="be533-304">Use [Start-ClusterResource](https://technet.microsoft.com/library/ee461056.aspx) to start the network name resource.</span></span>  
  
        3.  <span data-ttu-id="be533-305">使用 [Add-ClusterResourceDependency](https://technet.microsoft.com/library/ee461014.aspx) 设置网络名称与现有 SQL Server 可用性组资源之间的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="be533-305">Use [Add-ClusterResourceDependency](https://technet.microsoft.com/library/ee461014.aspx) to set the dependency between the network name and the existing SQL Server Availability Group resource.</span></span>  
  
         <span data-ttu-id="be533-306">有关将 Windows PowerShell 用于故障转移群集的信息，请参阅 [服务器管理器命令概述](https://technet.microsoft.com/library/cc732757.aspx#BKMK_wps)。</span><span class="sxs-lookup"><span data-stu-id="be533-306">For information about using Windows PowerShell for failover clusters, see [Overview of Server Manager Commands](https://technet.microsoft.com/library/cc732757.aspx#BKMK_wps).</span></span>  
  
2.  <span data-ttu-id="be533-307">在新的侦听器上启动 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 侦听。</span><span class="sxs-lookup"><span data-stu-id="be533-307">Start [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] listening on the new listener.</span></span> <span data-ttu-id="be533-308">在创建其他侦听器之后，可连接到承载可用性组主副本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例，并使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]或 PowerShell 修改侦听器端口。</span><span class="sxs-lookup"><span data-stu-id="be533-308">After creating the additional listener, connect to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the primary replica of the availability group and use [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell to modify the listener port.</span></span>  
  
 <span data-ttu-id="be533-309">有关详细信息，请参阅 [How to create multiple listeners for same availability group](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/how-to-create-multiple-listeners-for-same-availability-group-goden-yao.aspx)（如何为同一可用性组创建多个侦听程序）（SQL Server AlwaysOn 团队博客）。</span><span class="sxs-lookup"><span data-stu-id="be533-309">For more information, see [How to create multiple listeners for same availability group](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/how-to-create-multiple-listeners-for-same-availability-group-goden-yao.aspx) (a SQL Server AlwaysOn team blog).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="be533-310">相关任务</span><span class="sxs-lookup"><span data-stu-id="be533-310">Related Tasks</span></span>  
  
-   [<span data-ttu-id="be533-311">查看可用性组侦听程序属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="be533-311">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
-   [<span data-ttu-id="be533-312">删除可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="be533-312">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](remove-an-availability-group-listener-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="be533-313">相关内容</span><span class="sxs-lookup"><span data-stu-id="be533-313">Related Content</span></span>  
  
-   [<span data-ttu-id="be533-314">如何为相同的可用性组创建多个侦听程序</span><span class="sxs-lookup"><span data-stu-id="be533-314">How to create multiple listeners for same availability group</span></span>](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/how-to-create-multiple-listeners-for-same-availability-group-goden-yao.aspx)  
  
-   [<span data-ttu-id="be533-315">SQL Server AlwaysOn 团队博客：官方 SQL Server AlwaysOn 团队博客</span><span class="sxs-lookup"><span data-stu-id="be533-315">SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn team blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a><span data-ttu-id="be533-316">另请参阅</span><span class="sxs-lookup"><span data-stu-id="be533-316">See Also</span></span>  
 <span data-ttu-id="be533-317">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="be533-317">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="be533-318">[可用性组侦听程序、客户端连接和应用程序故障转移 &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="be533-318">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 [<span data-ttu-id="be533-319">SQL Server 多子网群集 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="be533-319">SQL Server Multi-Subnet Clustering &#40;SQL Server&#41;</span></span>](../../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md)  
