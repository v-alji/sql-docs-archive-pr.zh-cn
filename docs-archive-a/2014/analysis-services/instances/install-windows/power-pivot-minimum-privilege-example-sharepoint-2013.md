---
title: PowerPivot for SharePoint 2013 的最小特权配置示例 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c1e09e6c-52d3-48ab-8c70-818d5d775087
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0188f314e4c354b33d03e6e7948aed1ba4cf8be2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688319"
---
# <a name="example-of-a-minimum-privilege-configuration-for-powerpivot-for-sharepoint-2013"></a><span data-ttu-id="3d76b-102">PowerPivot for SharePoint 2013 最低权限的配置示例</span><span class="sxs-lookup"><span data-stu-id="3d76b-102">Example of a Minimum-Privilege Configuration for PowerPivot for SharePoint 2013</span></span>
  <span data-ttu-id="3d76b-103">本主题介绍具有最低权限的 PowerPivot for SharePoint 2013 配置示例。</span><span class="sxs-lookup"><span data-stu-id="3d76b-103">This topic describes an example PowerPivot for SharePoint 2013 configuration with minimum privileges.</span></span> <span data-ttu-id="3d76b-104">该配置将不同的帐户用于三个组件中的每个组件，并且每个帐户都具有最低的权限级别。</span><span class="sxs-lookup"><span data-stu-id="3d76b-104">The configuration utilizes a different account for each of the three components and each account has the minimum level of privileges.</span></span>  
  
## <a name="summary-of-accounts"></a><span data-ttu-id="3d76b-105">帐户摘要</span><span class="sxs-lookup"><span data-stu-id="3d76b-105">Summary of Accounts</span></span>  
 <span data-ttu-id="3d76b-106">PowerPivot for SharePoint 2013 支持使用 Network Service 帐户来用于 Analysis Services 服务帐户。</span><span class="sxs-lookup"><span data-stu-id="3d76b-106">PowerPivot for SharePoint 2013 supports the use of the Network Service account for the Analysis Services service account.</span></span> <span data-ttu-id="3d76b-107">Network Service 帐户不是针对 SharePoint 2010 的支持的方案。</span><span class="sxs-lookup"><span data-stu-id="3d76b-107">The Network Service account is not a supported scenario with SharePoint 2010.</span></span> <span data-ttu-id="3d76b-108">有关服务帐户的详细信息，请参阅[配置 Windows 服务帐户和权限](../../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) (https://msdn.microsoft.com/library/ms143504.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="3d76b-108">For more information on Service accounts, see [Configure Windows Service Accounts and Permissions](../../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) (https://msdn.microsoft.com/library/ms143504.aspx).</span></span>  
  
 <span data-ttu-id="3d76b-109">下表总结了在此最低权限配置示例中使用的三个帐户。</span><span class="sxs-lookup"><span data-stu-id="3d76b-109">The following table summarizes the three accounts used in this example of a minimum privileged configuration.</span></span>  
  
|<span data-ttu-id="3d76b-110">范围</span><span class="sxs-lookup"><span data-stu-id="3d76b-110">Scope</span></span>|<span data-ttu-id="3d76b-111">名称</span><span class="sxs-lookup"><span data-stu-id="3d76b-111">Name</span></span>|  
|-----------|----------|  
|<span data-ttu-id="3d76b-112">SharePoint 管理员帐户</span><span class="sxs-lookup"><span data-stu-id="3d76b-112">SharePoint Administrator account</span></span>|<span data-ttu-id="3d76b-113">**SPAdmin**</span><span class="sxs-lookup"><span data-stu-id="3d76b-113">**SPAdmin**</span></span>|  
|<span data-ttu-id="3d76b-114">SharePoint 场帐户</span><span class="sxs-lookup"><span data-stu-id="3d76b-114">SharePoint Farm account</span></span>|<span data-ttu-id="3d76b-115">**SPFarm**</span><span class="sxs-lookup"><span data-stu-id="3d76b-115">**SPFarm**</span></span>|  
|<span data-ttu-id="3d76b-116">Analysis Services 服务帐户</span><span class="sxs-lookup"><span data-stu-id="3d76b-116">Analysis Services service account</span></span>|<span data-ttu-id="3d76b-117">**SPsvc**</span><span class="sxs-lookup"><span data-stu-id="3d76b-117">**SPsvc**</span></span>|  
  
### <a name="the-sharepoint-administrator-account-spadmin"></a><span data-ttu-id="3d76b-118">SharePoint 管理员帐户 (SpAdmin)</span><span class="sxs-lookup"><span data-stu-id="3d76b-118">The SharePoint Administrator account (SpAdmin)</span></span>  
 <span data-ttu-id="3d76b-119">**SPAdmin** 是您用来安装和配置场的域帐户。</span><span class="sxs-lookup"><span data-stu-id="3d76b-119">**SPAdmin** is a domain account you use to install and configure the farm.</span></span> <span data-ttu-id="3d76b-120">它是用于运行 SharePoint 配置向导的帐户和用于 SharePoint 2013 的 PowerPivot 配置工具。 **SPAdmin**帐户是唯一需要本地管理员权限的帐户。</span><span class="sxs-lookup"><span data-stu-id="3d76b-120">It is the account used to run the SharePoint Configuration Wizard and the PowerPivot Configuration Tool for SharePoint 2013.The **SPAdmin** account is the only account that requires local Administrator rights.</span></span> <span data-ttu-id="3d76b-121">在运行 PowerPivot 配置工具之前，请将**SPAdmin**帐户权限授予 SharePoint 在其中创建内容和配置数据库的 SQL Server 数据库实例。</span><span class="sxs-lookup"><span data-stu-id="3d76b-121">Before running the PowerPivot Configuration tool, grant the **SPAdmin** account privileges to the SQL Server database instance where SharePoint creates content and configuration databases.</span></span> <span data-ttu-id="3d76b-122">若要在最低权限情况下配置 SPAdmin 帐户，该帐户应该是角色 **securityadmin** 和 **dbcreator**的成员。</span><span class="sxs-lookup"><span data-stu-id="3d76b-122">To configure the SPAdmin account in a minimum privilege scenario, it should be a member of the roles **securityadmin** and **dbcreator**.</span></span>  
  
### <a name="the-farm-account-spfarm"></a><span data-ttu-id="3d76b-123">场帐户 (SPFarm)</span><span class="sxs-lookup"><span data-stu-id="3d76b-123">The Farm account (SPFarm)</span></span>  
 <span data-ttu-id="3d76b-124">**SPFarm** 是 SharePoint Timer 服务以及用于管理中心的 Web 应用程序用来访问 SharePoint 内容数据库的域帐户。</span><span class="sxs-lookup"><span data-stu-id="3d76b-124">**SPFarm** is a domain account that the SharePoint Timer service and the web application for Central Administration use to access the SharePoint content database.</span></span> <span data-ttu-id="3d76b-125">该帐户无需是本地管理员。</span><span class="sxs-lookup"><span data-stu-id="3d76b-125">This account does not need to be a local administrator.</span></span> <span data-ttu-id="3d76b-126">SharePoint 配置向导在后端 SQL Server 数据库中授予正确的最低权限。最低 SQL Server 权限配置是角色 **securityadmin** 和 **dbcreator**中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="3d76b-126">The SharePoint configuration wizard grants the proper minimal privilege in the back-end SQL Server database.The minimum SQL Server privilege configuration is membership in the roles **securityadmin** and **dbcreator**.</span></span>  
  
### <a name="the-service-account-for-powerpivot-service-spsvc"></a><span data-ttu-id="3d76b-127">用于 PowerPivot 服务的服务帐户 (SPsvc)</span><span class="sxs-lookup"><span data-stu-id="3d76b-127">The Service Account for PowerPivot Service (SPsvc)</span></span>  
 <span data-ttu-id="3d76b-128">如果在运行 PowerPivot 配置工具前未配置新的 SharePoint 场，则默认情况下 PowerPivot 配置工具将创建以下内容：</span><span class="sxs-lookup"><span data-stu-id="3d76b-128">If a new SharePoint farm is not configured before you run the PowerPivot Configuration tool, then by default the PowerPivot Configuration tool will create the following:</span></span>  
  
-   <span data-ttu-id="3d76b-129">PowerPivot 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="3d76b-129">PowerPivot Service application.</span></span>  
  
-   <span data-ttu-id="3d76b-130">Excel Services 应用程序。</span><span class="sxs-lookup"><span data-stu-id="3d76b-130">Excel Services application.</span></span>  
  
-   <span data-ttu-id="3d76b-131">安全存储区应用程序。</span><span class="sxs-lookup"><span data-stu-id="3d76b-131">Secure Store application.</span></span>  
  
 <span data-ttu-id="3d76b-132">PowerPivot 配置工具将配置默认的应用程序池中的所有三个服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="3d76b-132">The PowerPivot configuration tool configures all three of the service applications in the default application pool.</span></span> <span data-ttu-id="3d76b-133">该应用程序池通常配置为以 SPFarm 帐户运行，该帐户有权访问服务帐户不需要的许多资源。为使环境成为最低权限环境，将新的域帐户配置为由相应的应用程序池和 Web 应用程序使用。</span><span class="sxs-lookup"><span data-stu-id="3d76b-133">That application pool is typically configured to run as the SPFarm account, which has access to many resources that a service account does not require.To make the environment a minimum-privileged environment, configure a new domain account to be use by the appropriate application pool and web application.</span></span>  
  
 <span data-ttu-id="3d76b-134">**创建要用作 SharePoint 服务帐户的新的域帐户 SPsvc：**</span><span class="sxs-lookup"><span data-stu-id="3d76b-134">**To create a new domain account SPsvc to be used as a SharePoint Service account:**</span></span>  
  
1.  <span data-ttu-id="3d76b-135">在 SharePoint 管理中心中，单击 "**安全**"。</span><span class="sxs-lookup"><span data-stu-id="3d76b-135">In SharePoint Central Administration, click **Security**.</span></span>  
  
2.  <span data-ttu-id="3d76b-136">单击 "**配置服务帐户**"</span><span class="sxs-lookup"><span data-stu-id="3d76b-136">Click **Configure Service Accounts**</span></span>  
  
3.  <span data-ttu-id="3d76b-137">单击 "**注册新的托管帐户**"。</span><span class="sxs-lookup"><span data-stu-id="3d76b-137">Click **Register new managed account**.</span></span>  
  
 <span data-ttu-id="3d76b-138">**SPSvc** 帐户没有本地管理员权限，并且 SPsvc 在 SharePoint 数据库中将不具有任何权限。</span><span class="sxs-lookup"><span data-stu-id="3d76b-138">The **SPSvc** account has no local administrator privileges and SPsvc will not have any privileges in the SharePoint database.</span></span> <span data-ttu-id="3d76b-139">SPsvc 要求的仅有的权限就是针对 Analysis Services 的 PowerPivot 实例的管理权限。</span><span class="sxs-lookup"><span data-stu-id="3d76b-139">The only privileges SPsvc requires is administrative rights to the PowerPivot Instance of the Analysis Services.</span></span>  
  
 <span data-ttu-id="3d76b-140">**将相应的应用程序池配置为使用 SPsvc 帐户：**</span><span class="sxs-lookup"><span data-stu-id="3d76b-140">**To configure the appropriate application pool to use the SPsvc account :**</span></span>  
  
1.  <span data-ttu-id="3d76b-141">在 SharePoint 管理中心中，单击 "**安全**"。</span><span class="sxs-lookup"><span data-stu-id="3d76b-141">In SharePoint Central Administration, click **Security**.</span></span>  
  
2.  <span data-ttu-id="3d76b-142">单击 "**配置服务帐户**"。</span><span class="sxs-lookup"><span data-stu-id="3d76b-142">Click **Configure Service Accounts**.</span></span>  
  
3.  <span data-ttu-id="3d76b-143">选择 PowerPivot 服务应用程序使用的服务应用程序池。</span><span class="sxs-lookup"><span data-stu-id="3d76b-143">Select the service application pool used by the PowerPivot Service application.</span></span> <span data-ttu-id="3d76b-144">然后选择 SPSvc 帐户。</span><span class="sxs-lookup"><span data-stu-id="3d76b-144">Then select the SPSvc account.</span></span>  
  
 <span data-ttu-id="3d76b-145">**授予对具有 PowerShell 的 Web 应用程序的访问权限：**</span><span class="sxs-lookup"><span data-stu-id="3d76b-145">**To Grant access to the web application with PowerShell:**</span></span>  
  
1.  <span data-ttu-id="3d76b-146">使用管理员权限运行 SharePoint 2013 Management Shell。</span><span class="sxs-lookup"><span data-stu-id="3d76b-146">Run the SharePoint 2013 Management Shell with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="3d76b-147">运行以下 PowerShell 代码：</span><span class="sxs-lookup"><span data-stu-id="3d76b-147">Run the following PowerShell code:</span></span>  
  
    ```powershell
    $webApp = Get-SPWebApplication "http://<servername>"  
    $webApp.GrantAccessToProcessIdentity("DOMAIN\<ServiceAccountName>")
    ```  
