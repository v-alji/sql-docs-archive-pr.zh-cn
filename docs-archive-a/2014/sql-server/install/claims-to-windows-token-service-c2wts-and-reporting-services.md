---
title: 声明到 Windows 令牌服务 (C2WTS) 和 Reporting Services |Microsoft Docs
ms.custom: ''
ms.date: 03/25/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- c2wts.exe.config
- SharePoint mode
- C2WTS
- WSS_WPG
ms.assetid: 4d380509-deed-4b4b-a9c1-a9134cc40641
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: cf2e245dfae17556bdb906c134ba0d53898a8631
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586208"
---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a><span data-ttu-id="a355e-102">Claims to Windows Token Service (C2WTS) 和 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="a355e-102">Claims to Windows Token Service (C2WTS) and Reporting Services</span></span>
  <span data-ttu-id="a355e-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]如果要对 sharepoint 场之外的数据源使用 windows 身份验证，则需要使用 sharepoint 模式 (c2WTS) 的 Sharepoint 声明。</span><span class="sxs-lookup"><span data-stu-id="a355e-103">The SharePoint Claims to Windows Token Service (c2WTS) is required with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode if you want to use windows authentication for Data Sources that are outside the SharePoint farm.</span></span> <span data-ttu-id="a355e-104">即使用户使用 Windows 身份验证访问数据源，上述要求也是成立的。其原因在于，Web 前端 (WFE) 和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共享服务之间的通信将始终是 Claims 身份验证。</span><span class="sxs-lookup"><span data-stu-id="a355e-104">This is true even if the user accesses the data sources with Windows Authentication because the communication between the web front-end (WFE) and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service will always be Claims authentication.</span></span>  
  
 <span data-ttu-id="a355e-105">即使你的数据源与共享服务位于相同的计算机上，也需要 c2WTS。</span><span class="sxs-lookup"><span data-stu-id="a355e-105">c2WTS is needed even if your data source(s) are on the same computer as the shared service.</span></span> <span data-ttu-id="a355e-106">但在此方案中，不需要约束委派。</span><span class="sxs-lookup"><span data-stu-id="a355e-106">However in this scenario, constrained delegation is not needed.</span></span>  
  
 <span data-ttu-id="a355e-107">c2WTS 创建的令牌将仅用于约束委派（对特定服务的约束）以及配置选项“使用任何身份验证协议”。</span><span class="sxs-lookup"><span data-stu-id="a355e-107">The tokens created by c2WTS will only work with constrained delegation (constrains to specific services) and the configuration option "using any authentication protocol".</span></span> <span data-ttu-id="a355e-108">如前所述，如果您的数据源与共享服务位于同一台计算机上，则不需要约束委派。</span><span class="sxs-lookup"><span data-stu-id="a355e-108">As noted earlier, if your data sources are on the same computer as the shared service, then constrained delegation is not needed.</span></span>  
  
 <span data-ttu-id="a355e-109">如果您的环境将使用 Kerberos 约束委派，则 SharePoint 服务器服务和外部数据源需要位于同一 Windows 域中。</span><span class="sxs-lookup"><span data-stu-id="a355e-109">If your environment will use Kerberos constrained delegation, then the SharePoint Server service and external data sources need to reside in the same Windows domain.</span></span> <span data-ttu-id="a355e-110">依赖于 Claims to Windows Token Service (c2WTS) 的所有服务都必须使用 Kerberos **约束** 委派，以便允许 c2WTS 使用 Kerberos 协议转换将声明转换为 Windows 凭据。</span><span class="sxs-lookup"><span data-stu-id="a355e-110">Any service that relies on the Claims to Windows token service (c2WTS) must use Kerberos **constrained** delegation to allow c2WTS to use Kerberos protocol transition to translate claims into Windows credentials.</span></span> <span data-ttu-id="a355e-111">这些规定适用于所有 SharePoint 共享服务。</span><span class="sxs-lookup"><span data-stu-id="a355e-111">These requirements are true for all SharePoint Shared Services.</span></span> <span data-ttu-id="a355e-112">有关详细信息，请参阅[Microsoft SharePoint 2010 产品的 Kerberos 身份验证概述 https://technet.microsoft.com/library/gg502594.aspx) (](https://technet.microsoft.com/library/gg502594.aspx)。</span><span class="sxs-lookup"><span data-stu-id="a355e-112">For more information, see [Overview of Kerberos authentication for Microsoft SharePoint 2010 Products  (https://technet.microsoft.com/library/gg502594.aspx)](https://technet.microsoft.com/library/gg502594.aspx).</span></span>  
  
 <span data-ttu-id="a355e-113">本主题将概述此过程。</span><span class="sxs-lookup"><span data-stu-id="a355e-113">The procedure is summarized in this topic.</span></span>  
  
||  
|-|  
|<span data-ttu-id="a355e-114">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="a355e-114">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="a355e-115">先决条件</span><span class="sxs-lookup"><span data-stu-id="a355e-115">Prerequisites</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a355e-116">请注意，某些配置步骤可能会更改，或者在某些场拓扑中不适用。</span><span class="sxs-lookup"><span data-stu-id="a355e-116">Note: Some of the configuration steps may change, or may not work in certain farm topologies.</span></span> <span data-ttu-id="a355e-117">例如，单服务器安装并不支持 Windows Identity Foundation c2WTS 服务，因此，在该场配置中不可能实现 Claims to Windows Token 委派方案。</span><span class="sxs-lookup"><span data-stu-id="a355e-117">For instance, a single server install does not support the Windows Identity Foundation c2WTS services so claims to windows token delegation scenarios are not possible with this farm configuration.</span></span>  
  
### <a name="basic-steps-needed-to-configure-c2wts"></a><span data-ttu-id="a355e-118">配置 c2WTS 所需的基本步骤</span><span class="sxs-lookup"><span data-stu-id="a355e-118">Basic steps needed to configure c2WTS</span></span>  
  
1.  <span data-ttu-id="a355e-119">配置 c2WTS 服务帐户。</span><span class="sxs-lookup"><span data-stu-id="a355e-119">Configure the c2WTS service account.</span></span> <span data-ttu-id="a355e-120">将该服务帐户添加到运行 c2WTS 的每个应用程序服务器上的本地管理员组。</span><span class="sxs-lookup"><span data-stu-id="a355e-120">Add the service account to the local Administrators group on each application server running c2WTS.</span></span> <span data-ttu-id="a355e-121">此外，确认该帐户具有以下本地安全策略权限：</span><span class="sxs-lookup"><span data-stu-id="a355e-121">In addition, verify that the account has the following local security policy rights:</span></span>  
  
    -   <span data-ttu-id="a355e-122">以操作系统方式操作</span><span class="sxs-lookup"><span data-stu-id="a355e-122">Act as part of the operating system</span></span>  
  
    -   <span data-ttu-id="a355e-123">在身份验证后模拟客户端</span><span class="sxs-lookup"><span data-stu-id="a355e-123">Impersonate a client after authentication</span></span>  
  
    -   <span data-ttu-id="a355e-124">作为服务登录</span><span class="sxs-lookup"><span data-stu-id="a355e-124">Log on as a service</span></span>  
  
     <span data-ttu-id="a355e-125">你用于 c2WTS 的帐户还需要配置为具有协议转换的约束委派，并且需要权限才能与 (（即 SQL Server 引擎、SQL Server Analysis Services) ）进行通信。若要配置委派，可以使用 "Active Directory 用户和计算机" 管理单元。</span><span class="sxs-lookup"><span data-stu-id="a355e-125">The account you use for c2WTS also needs to be configured for Constrained Delegation with Protocol Transitioning and needs permissions to delegate to the Services it is required to communicate with (i.e. SQL Server Engine, SQL Server Analysis Services).To configure delegation you can use the Active Directory Users and Computer snap-in.</span></span>  
  
    1.  <span data-ttu-id="a355e-126">右键单击各服务帐户并且打开“属性”对话框。</span><span class="sxs-lookup"><span data-stu-id="a355e-126">Right-click each service account and open the properties dialog.</span></span> <span data-ttu-id="a355e-127">在该对话框中，单击 **“委派”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="a355e-127">In the dialog click the **Delegation** tab.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="a355e-128">请注意，只有在对象具有分配给它的 SPN 的情况下，“委派”选项卡才可见。</span><span class="sxs-lookup"><span data-stu-id="a355e-128">Note: the delegation tab is only visible if the object has an SPN assigned to it.</span></span> <span data-ttu-id="a355e-129">c2WTS 不要求在 c2WTS 帐户上使用 SPN，但如果没有 SPN，"**委派**" 选项卡将不可见。</span><span class="sxs-lookup"><span data-stu-id="a355e-129">c2WTS does not require an SPN on the c2WTS Account, however, without an SPN, the **Delegation** tab will not be visible.</span></span> <span data-ttu-id="a355e-130">配置约束委派的另一个方法是使用 **ADSIEdit**之类的实用工具。</span><span class="sxs-lookup"><span data-stu-id="a355e-130">An alternative way to configure constrained delegation is to use a utility such as **ADSIEdit**.</span></span>  
  
    2.  <span data-ttu-id="a355e-131">“委派”选项卡上的主要配置选项如下：</span><span class="sxs-lookup"><span data-stu-id="a355e-131">Key configuration options on the delegation tab are the following:</span></span>  
  
        -   <span data-ttu-id="a355e-132">选择 "仅信任此用户来委派指定的服务"</span><span class="sxs-lookup"><span data-stu-id="a355e-132">Select "Trust this user for delegation to specified services only"</span></span>  
  
        -   <span data-ttu-id="a355e-133">选择 "使用任何身份验证协议"</span><span class="sxs-lookup"><span data-stu-id="a355e-133">Select "Use any authentication protocol"</span></span>  
  
         <span data-ttu-id="a355e-134">有关详细信息，请参阅以下白皮书中的 "为计算机和服务帐户配置 Kerberos 约束委派" 部分，[配置适用于 SharePoint 2010 的 kerberos 身份验证和 SQL Server 2008 R2 产品](https://docs.microsoft.com/archive/blogs/tothesharepoint/white-paper-configuring-kerberos-authentication-for-sharepoint-2010-and-sql-server-2008-r2-products)</span><span class="sxs-lookup"><span data-stu-id="a355e-134">For more information, see the "configure Kerberos constrained delegation for computers and service accounts" section of the following white paper, [Configuring Kerberos authentication for SharePoint 2010 and SQL Server 2008 R2 products](https://docs.microsoft.com/archive/blogs/tothesharepoint/white-paper-configuring-kerberos-authentication-for-sharepoint-2010-and-sql-server-2008-r2-products)</span></span>  
  
2.  <span data-ttu-id="a355e-135">配置 c2WTS "AllowedCallers"</span><span class="sxs-lookup"><span data-stu-id="a355e-135">Configure c2WTS 'AllowedCallers'</span></span>  
  
     <span data-ttu-id="a355e-136">c2WTS 要求在配置文件中显式列出的 "调用方" 标识**c2wtshost.exe.config**。c2WTS 不接受系统中所有经过身份验证的用户的请求，除非已将其配置为执行此操作。</span><span class="sxs-lookup"><span data-stu-id="a355e-136">c2WTS requires the 'callers' identities explicitly listed in the configuration file, **c2wtshost.exe.config**. c2WTS does not accept requests from all authenticated users in the system unless it is configured to do so.</span></span> <span data-ttu-id="a355e-137">在此情况下，“调用方”是 WSS_WPG Windows 组。</span><span class="sxs-lookup"><span data-stu-id="a355e-137">In this case the 'caller' is the WSS_WPG Windows group.</span></span> <span data-ttu-id="a355e-138">该 c2wtshost.exe.confi 文件保存在以下位置：</span><span class="sxs-lookup"><span data-stu-id="a355e-138">The c2wtshost.exe.confi file is saved in the following location:</span></span>  
  
     <span data-ttu-id="a355e-139">**\Program Files\Windows 标识 Foundation\v3.5\c2wtshost.exe.config**</span><span class="sxs-lookup"><span data-stu-id="a355e-139">**\Program Files\Windows Identity Foundation\v3.5\c2wtshost.exe.config**</span></span>  
  
     <span data-ttu-id="a355e-140">下面是该配置文件的示例：</span><span class="sxs-lookup"><span data-stu-id="a355e-140">The following is an example of the configuration file:</span></span>  
  
    ```  
    <configuration>  
      <windowsTokenService>  
        <!--  
            By default no callers are allowed to use the Windows Identity Foundation Claims To NT Token Service.  
            Add the identities you wish to allow below.  
          -->  
        <allowedCallers>  
          <clear/>  
          <add value="WSS_WPG" />  
        </allowedCallers>  
      </windowsTokenService>  
    </configuration>  
    ```  
  
3.  <span data-ttu-id="a355e-141">启动操作系统 c2WTS 服务：</span><span class="sxs-lookup"><span data-stu-id="a355e-141">Start the operating system c2WTS service:</span></span>  
  
    1.  <span data-ttu-id="a355e-142">配置该服务以便使用您在之前的步骤中配置的服务帐户。</span><span class="sxs-lookup"><span data-stu-id="a355e-142">Configure the service to use the service account you configured in the previous step.</span></span>  
  
    2.  <span data-ttu-id="a355e-143">将启动类型更改为 "**自动**"，并启动服务。</span><span class="sxs-lookup"><span data-stu-id="a355e-143">Change the Startup type to "**Automatic**" and start the service.</span></span>  
  
4.  <span data-ttu-id="a355e-144">在 "**管理服务器上的服务**" 页上，启动 sharepoint 的 "声明到 Windows 令牌服务"：通过 SharePoint 管理中心启动对 Windows 令牌服务的声明。</span><span class="sxs-lookup"><span data-stu-id="a355e-144">Start the SharePoint 'Claims to Windows Token Service': Start the Claims to Windows Token Service through SharePoint Central Administration on the **Manage Services on Server** page.</span></span> <span data-ttu-id="a355e-145">应在将执行操作的服务器上启动该服务。</span><span class="sxs-lookup"><span data-stu-id="a355e-145">The service should be started on the server that will be performing the action.</span></span> <span data-ttu-id="a355e-146">例如，如果你有一个作为 WFE 的服务器，并且有另一个作为应用程序服务器的服务器（该服务器具有正在运行的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共享服务），则只需启动该应用程序服务器上的 c2WTS。</span><span class="sxs-lookup"><span data-stu-id="a355e-146">For example if you have a server that is a WFE and another server that is an Application Server that has the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service running, you only need to start c2WTS on the Application Server.</span></span> <span data-ttu-id="a355e-147">在 WFE 上不需要 c2WTS。</span><span class="sxs-lookup"><span data-stu-id="a355e-147">c2WTS is not needed on the WFE.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a355e-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a355e-148">See Also</span></span>  
 <span data-ttu-id="a355e-149">[声明到 Windows 令牌服务 (c2WTS) 概述 (https://msdn.microsoft.com/library/ee517278.aspx)](https://msdn.microsoft.com/library/ee517278.aspx) </span><span class="sxs-lookup"><span data-stu-id="a355e-149">[Claims to Windows Token Service (c2WTS) Overview (https://msdn.microsoft.com/library/ee517278.aspx)](https://msdn.microsoft.com/library/ee517278.aspx) </span></span>  
 [<span data-ttu-id="a355e-150">Microsoft SharePoint 2010 产品 (的 Kerberos 身份验证概述https://technet.microsoft.com/library/gg502594.aspx)</span><span class="sxs-lookup"><span data-stu-id="a355e-150">Overview of Kerberos authentication for Microsoft SharePoint 2010 Products (https://technet.microsoft.com/library/gg502594.aspx)</span></span>](https://technet.microsoft.com/library/gg502594.aspx)  
  
