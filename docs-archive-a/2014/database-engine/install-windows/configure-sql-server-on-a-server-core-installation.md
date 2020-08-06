---
title: 在服务器核心安装上配置 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- IsHadrEnabled server property
- Server Core Installation [SQL Server]
ms.assetid: ed6e5e94-4b8d-422a-a17e-61b05a4df903
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e74307374e0d07d69107649b42e0bc2f0897e98c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690787"
---
# <a name="configure-sql-server-on-a-server-core-installation"></a><span data-ttu-id="3fe99-102">在 Server Core 安装上配置 SQL Server</span><span class="sxs-lookup"><span data-stu-id="3fe99-102">Configure SQL Server on a Server Core Installation</span></span>
  <span data-ttu-id="3fe99-103">本主题详细介绍如何在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SP1 的 Server Core 安装上配置 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3fe99-103">This topic covers details about configuring [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1.</span></span> 
  
##  <a name="configure-and-manage-server-core-on-windows-server"></a><span data-ttu-id="3fe99-104">在 Windows Server 上配置和管理 Server Core</span><span class="sxs-lookup"><span data-stu-id="3fe99-104">Configure and Manage Server Core on Windows Server</span></span>  
 <span data-ttu-id="3fe99-105">本节提供帮助配置和管理 Server Core 安装的主题参考资料。</span><span class="sxs-lookup"><span data-stu-id="3fe99-105">The section provides references to the topics that help configure and manage a Server Core installation.</span></span>  
  
 <span data-ttu-id="3fe99-106">在 Server Core 模式下，部分 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 功能不受支持。</span><span class="sxs-lookup"><span data-stu-id="3fe99-106">Not all features of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] are supported in Server Core mode.</span></span>  <span data-ttu-id="3fe99-107">其中的一些功能可以安装在客户端计算机或未运行 Server Core 的另一服务器上，然后连接到在 Server Core 上安装的数据库引擎服务。</span><span class="sxs-lookup"><span data-stu-id="3fe99-107">Some of these features can be installed on a client computer or a different server that is not running Server Core, and connected to the Database Engine services installed on Server Core.</span></span>  
  
 <span data-ttu-id="3fe99-108">有关远程配置和管理 Server Core 安装的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="3fe99-108">For more information about configuring and managing a Server Core installation remotely, see the following topics:</span></span>  
  
-   <span data-ttu-id="3fe99-109">[Windows server 2008 R2： Server Core 部署的最佳实践](https://go.microsoft.com/fwlink/?LinkID=245957) (https://go.microsoft.com/fwlink/?LinkID=245957)</span><span class="sxs-lookup"><span data-stu-id="3fe99-109">[Windows Server 2008 R2: Best Practices for Server Core Deployments](https://go.microsoft.com/fwlink/?LinkID=245957) (https://go.microsoft.com/fwlink/?LinkID=245957)</span></span>  
  
-   <span data-ttu-id="3fe99-110">[配置服务器核心安装：概述](https://go.microsoft.com/fwlink/?LinkId=245958) (https://go.microsoft.com/fwlink/?LinkId=245958)</span><span class="sxs-lookup"><span data-stu-id="3fe99-110">[Configuring a Server Core installation: Overview](https://go.microsoft.com/fwlink/?LinkId=245958) (https://go.microsoft.com/fwlink/?LinkId=245958)</span></span>  
  
-   <span data-ttu-id="3fe99-111">[使用 Sconfig.cmd 配置 Windows server 2008 R2 的服务器核心安装](https://go.microsoft.com/fwlink/?LinkId=245959) (https://go.microsoft.com/fwlink/?LinkId=245959)</span><span class="sxs-lookup"><span data-stu-id="3fe99-111">[Configuring a Server Core installation of Windows Server 2008 R2 with Sconfig.cmd](https://go.microsoft.com/fwlink/?LinkId=245959) (https://go.microsoft.com/fwlink/?LinkId=245959)</span></span>  
  
-   <span data-ttu-id="3fe99-112">[在运行 Windows server 2008 R2 的服务器核心安装的服务器上安装服务器角色：概述](https://go.microsoft.com/fwlink/?LinkId=245960) (https://go.microsoft.com/fwlink/?LinkId=245960)</span><span class="sxs-lookup"><span data-stu-id="3fe99-112">[Installing a server role on a server running a Server Core installation of Windows Server 2008 R2: Overview](https://go.microsoft.com/fwlink/?LinkId=245960) (https://go.microsoft.com/fwlink/?LinkId=245960)</span></span>  
  
-   <span data-ttu-id="3fe99-113">[在运行 Windows server 2008 R2 的服务器核心安装的服务器上安装 Windows 功能：概述](https://go.microsoft.com/fwlink/?LinkId=245961) (https://go.microsoft.com/fwlink/?LinkId=245961)</span><span class="sxs-lookup"><span data-stu-id="3fe99-113">[Installing Windows Features on a server running a Server Core installation of Windows Server 2008 R2: Overview](https://go.microsoft.com/fwlink/?LinkId=245961) (https://go.microsoft.com/fwlink/?LinkId=245961)</span></span>  
  
-   <span data-ttu-id="3fe99-114">[管理服务器核心安装：概述](https://go.microsoft.com/fwlink/?LinkId=245962) (https://go.microsoft.com/fwlink/?LinkId=245962)</span><span class="sxs-lookup"><span data-stu-id="3fe99-114">[Managing a Server Core installation: Overview](https://go.microsoft.com/fwlink/?LinkId=245962) (https://go.microsoft.com/fwlink/?LinkId=245962)</span></span>  
  
-   <span data-ttu-id="3fe99-115">[管理服务器核心安装](https://go.microsoft.com/fwlink/?LinkId=245963) (https://go.microsoft.com/fwlink/?LinkId=245963)</span><span class="sxs-lookup"><span data-stu-id="3fe99-115">[Administering a Server Core installation](https://go.microsoft.com/fwlink/?LinkId=245963) (https://go.microsoft.com/fwlink/?LinkId=245963)</span></span>  
  
##  <a name="install-updates"></a><span data-ttu-id="3fe99-116">安装 更新</span><span class="sxs-lookup"><span data-stu-id="3fe99-116">Install updates</span></span>  
 <span data-ttu-id="3fe99-117">本节提供有关在 Windows Server Core 计算机上安装 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 更新的信息。</span><span class="sxs-lookup"><span data-stu-id="3fe99-117">This section provides information about installing updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a Windows Server Core machine.</span></span> <span data-ttu-id="3fe99-118">我们建议客户及时评估和安装最新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新，以便确保系统是最新的并且具有最近的安全更新。</span><span class="sxs-lookup"><span data-stu-id="3fe99-118">We recommend that customers evaluate and install latest [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] updates in a timely manner to make sure that systems are up-to-date with the most recent security updates.</span></span> <span data-ttu-id="3fe99-119">有关 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 Windows Server core 计算机上安装的详细信息，请参阅[在 Server Core 上安装 SQL Server 2014](install-sql-server-on-server-core.md)。</span><span class="sxs-lookup"><span data-stu-id="3fe99-119">For more information about installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a Windows Server Core machine, see [Install SQL Server 2014 on Server Core](install-sql-server-on-server-core.md).</span></span>  
  
 <span data-ttu-id="3fe99-120">以下是安装产品更新的两个方案：</span><span class="sxs-lookup"><span data-stu-id="3fe99-120">The following are the two scenarios for installing product updates:</span></span>  
  
-   [<span data-ttu-id="3fe99-121">在全新安装期间为 SQL Server 2014 安装更新</span><span class="sxs-lookup"><span data-stu-id="3fe99-121">Installing Updates for SQL Server 2014 During a New Installation</span></span>](#installing-updates-during-a-new-installation) 
  
-   [<span data-ttu-id="3fe99-122">安装 SQL Server 2014 后安装更新</span><span class="sxs-lookup"><span data-stu-id="3fe99-122">Installing Updates for SQL Server 2014 After It Has Been Installed</span></span>](#installing-updates-after-installation) 
  
### <a name="installing-updates-during-a-new-installation"></a><span data-ttu-id="3fe99-123">在全新安装期间安装更新</span><span class="sxs-lookup"><span data-stu-id="3fe99-123">Installing updates during a new installation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3fe99-124">安装程序在 Server Core 操作系统上仅支持命令提示符安装。</span><span class="sxs-lookup"><span data-stu-id="3fe99-124">Setup supports only command prompt installations on Server Core operating system.</span></span> <span data-ttu-id="3fe99-125">有关详细信息，请参阅 [从命令提示符安装 SQL Server 2014](install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="3fe99-125">For more information, see [Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3fe99-126">安装程序将最新的产品更新集成到主产品安装中，以便可以同时安装主产品及其适用的更新。</span><span class="sxs-lookup"><span data-stu-id="3fe99-126">setup integrates the latest product updates with the main product installation so that the main product and its applicable updates are installed at the same time.</span></span>  
  
 <span data-ttu-id="3fe99-127">在找到最新版本的适用更新后，安装程序将下载这些更新并将其与当前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装过程集成在一起。</span><span class="sxs-lookup"><span data-stu-id="3fe99-127">After Setup finds the latest versions of the applicable updates, it downloads and integrates them with the current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup process.</span></span> <span data-ttu-id="3fe99-128">产品更新可请求累积更新、Service Pack 或者 Service Pack 连同累积更新。</span><span class="sxs-lookup"><span data-stu-id="3fe99-128">Product Update can pull in a cumulative update, service pack, or service pack plus cumulative update.</span></span>  
  
 <span data-ttu-id="3fe99-129">指定 UpdateEnabled 和 UpdateSource 参数可以在主产品安装中包含最新的产品更新。</span><span class="sxs-lookup"><span data-stu-id="3fe99-129">Specify the UpdateEnabled, and UpdateSource parameters to include the latest product updates with the main product installation.</span></span> <span data-ttu-id="3fe99-130">参考以下示例以便在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装期间允许产品更新：</span><span class="sxs-lookup"><span data-stu-id="3fe99-130">Refer the following example to enable product updates during the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup:</span></span>  
  
```cmd 
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,Replication /INSTANCENAME=MSSQLSERVER /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="<StrongPassword>" /SQLSYSADMINACCOUNTS="<DomainName\UserName>" /AGTSVCACCOUNT="NT AUTHORITY\Network Service" /UpdateEnabled=True /UpdateSource="<SourcePath>" /IACCEPTSQLSERVERLICENSETERMS  
```  
  
### <a name="installing-updates-after-installation"></a><span data-ttu-id="3fe99-131">安装后安装更新</span><span class="sxs-lookup"><span data-stu-id="3fe99-131">Installing updates after installation</span></span> 
 <span data-ttu-id="3fe99-132">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的已安装实例上，我们建议您应用最新的安全更新和关键更新，包括常规分发发布 (GDR) 和 Service Pack (SP)。</span><span class="sxs-lookup"><span data-stu-id="3fe99-132">On an installed instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], we recommend that you apply the latest security updates and critical updates including General Distribution Releases (GDRs), and Service Packs (SPs).</span></span> <span data-ttu-id="3fe99-133">单独的累积更新和安全更新应该根据需要逐案例采用。</span><span class="sxs-lookup"><span data-stu-id="3fe99-133">Individual Cumulative updates and security updates should be adopted on a case-by-case, "as-needed" basis.</span></span> <span data-ttu-id="3fe99-134">评估更新；如果需要，则应用该更新。</span><span class="sxs-lookup"><span data-stu-id="3fe99-134">Evaluate the update; if it's needed, then apply it.</span></span>  
  
 <span data-ttu-id="3fe99-135">在命令提示符下应用更新，从而将 <package_name> 替换为更新包的名称：</span><span class="sxs-lookup"><span data-stu-id="3fe99-135">Apply an update at a command prompt, replacing <package_name> with the name of your update package:</span></span>  
  
-   <span data-ttu-id="3fe99-136">更新 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的单个实例和所有共享组件。</span><span class="sxs-lookup"><span data-stu-id="3fe99-136">Update a single instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and all shared components.</span></span> <span data-ttu-id="3fe99-137">您可以通过使用 InstanceName 参数或 InstanceID 参数指定实例。</span><span class="sxs-lookup"><span data-stu-id="3fe99-137">You can specify the instance either by using the InstanceName parameter or the InstanceID parameter.</span></span>  
  
    ```  
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /InstanceName=MyInstance  
    ```  
  
-   <span data-ttu-id="3fe99-138">仅更新 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 共享组件：</span><span class="sxs-lookup"><span data-stu-id="3fe99-138">Update [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] shared components only:</span></span>  
  
    ```  
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch  
    ```  
  
-   <span data-ttu-id="3fe99-139">更新计算机上的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例和所有共享组件：</span><span class="sxs-lookup"><span data-stu-id="3fe99-139">Update all instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the computer and all shared components:</span></span>  
  
    ```  
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /AllInstances  
    ```  
  
##  <a name="startstop-sql-server-service"></a><span data-ttu-id="3fe99-140">启动/停止 SQL Server 服务</span><span class="sxs-lookup"><span data-stu-id="3fe99-140">Start/Stop SQL Server service</span></span>  
 <span data-ttu-id="3fe99-141">[sqlservr Application](../../tools/sqlservr-application.md) 应用程序可以在命令提示符下启动、停止、暂停和继续 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="3fe99-141">The [sqlservr Application](../../tools/sqlservr-application.md) application starts, stops, pauses, and continues an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a command prompt.</span></span>  
  
 <span data-ttu-id="3fe99-142">您还可以使用 Net 服务启动和停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="3fe99-142">You can also use Net services to start and stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services.</span></span>  
  
## <a name="enable-alwayson-availability-groups"></a><span data-ttu-id="3fe99-143">启用 AlwaysOn 可用性组</span><span class="sxs-lookup"><span data-stu-id="3fe99-143">Enable AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="3fe99-144">启用 AlwaysOn 可用性组是服务器实例将可用性组用作高可用性和灾难恢复解决方案的一个先决条件。</span><span class="sxs-lookup"><span data-stu-id="3fe99-144">Being enabled for AlwaysOn Availability Groups is a prerequisite for a server instance to use availability groups as a high availability and disaster recovery solution.</span></span> <span data-ttu-id="3fe99-145">有关管理 AlwaysOn 可用性组的详细信息，请参阅[启用和禁用 AlwaysOn 可用性组 (SQL Server)](../availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3fe99-145">For more information about managing the AlwaysOn Availability Groups, see [Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;](../availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).</span></span>  
  
### <a name="using-sql-server-configuration-manager-remotely"></a><span data-ttu-id="3fe99-146">远程使用 SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="3fe99-146">Using SQL Server Configuration Manager Remotely</span></span>  
 <span data-ttu-id="3fe99-147">这些步骤将在运行客户端版本的 [!INCLUDE[win7](../../includes/win7-md.md)] 或更高版本的电脑上或安装了 Server Graphical Shell 的另一台服务器（即启用了 Server Graphical Shell 功能的 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 完全安装或 Windows Server 8 安装）上执行。</span><span class="sxs-lookup"><span data-stu-id="3fe99-147">These steps are meant to be performed on a PC running the client edition of [!INCLUDE[win7](../../includes/win7-md.md)] or later, or another server that has the Server Graphical Shell installed (i.e. a full installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] or a Windows Server 8 installation with the Server Graphical Shell feature enabled).</span></span>  
  
1.  <span data-ttu-id="3fe99-148">打开“计算机管理”。</span><span class="sxs-lookup"><span data-stu-id="3fe99-148">Open Computer Management.</span></span> <span data-ttu-id="3fe99-149">若要打开“计算机管理”，请执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="3fe99-149">To open Computer Management do one of the following:</span></span>  
  
    1.  <span data-ttu-id="3fe99-150">在 [!INCLUDE[win7](../../includes/win7-md.md)]、Windows Server 2008 或 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]上：</span><span class="sxs-lookup"><span data-stu-id="3fe99-150">On [!INCLUDE[win7](../../includes/win7-md.md)], Windows Server 2008, or [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="3fe99-151">依次单击“开始”、“所有程序”、“管理工具”，然后单击“计算机管理”。</span><span class="sxs-lookup"><span data-stu-id="3fe99-151">Click Start, click All Programs, click Administrative Tools, and then click Computer Management.</span></span>  
  
        2.  <span data-ttu-id="3fe99-152">依次单击“开始”、“运行”，键入 COMPMGMT.MSC，然后单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="3fe99-152">Click Start, click Run, type COMPMGMT.MSC, and then click OK.</span></span>  
  
    2.  <span data-ttu-id="3fe99-153">在启用了服务器图形 Shell 的 Windows 8 上：</span><span class="sxs-lookup"><span data-stu-id="3fe99-153">On Windows 8 with Server Graphical Shell enabled:</span></span>  
  
        1.  <span data-ttu-id="3fe99-154">将鼠标移到屏幕左下角，在看见“开始”图标叠加时右键单击。</span><span class="sxs-lookup"><span data-stu-id="3fe99-154">Move your mouse to the bottom-left corner of the screen and right-click when you see the Start overlay.</span></span>  
  
        2.  <span data-ttu-id="3fe99-155">从上下文菜单选择“计算机管理”。</span><span class="sxs-lookup"><span data-stu-id="3fe99-155">Select Computer Management  from the context menu.</span></span>  
  
2.  <span data-ttu-id="3fe99-156">在控制台树中，右键单击“计算机管理”，再单击“连接到另一台计算机”。</span><span class="sxs-lookup"><span data-stu-id="3fe99-156">In the console tree, right-click Computer Management, and then click Connect to another computer.</span></span>  
  
3.  <span data-ttu-id="3fe99-157">在“选择计算机”对话框中，键入想要管理的 Server Core 计算机名称或单击“浏览”以查找它，然后单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="3fe99-157">In the Select Computer dialog box, type the name of the Server Core machine that you want to manage, or click Browse to find it, and then click OK.</span></span>  
  
4.  <span data-ttu-id="3fe99-158">在控制台树中，在 Server Core 计算机的“计算机管理”下单击“服务和应用程序”。</span><span class="sxs-lookup"><span data-stu-id="3fe99-158">In the console tree, under Computer Management of the Server Core machine, click Services and Applications.</span></span>  
  
5.  <span data-ttu-id="3fe99-159">双击 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器。</span><span class="sxs-lookup"><span data-stu-id="3fe99-159">Double click [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
6.  <span data-ttu-id="3fe99-160">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager 中，单击 " [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务"，右键单击 " [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (\<instance name> ") ，其中 \<instance name> 是要为其启用 AlwaysOn 可用性组的本地服务器实例的名称，然后单击 "属性"。</span><span class="sxs-lookup"><span data-stu-id="3fe99-160">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, click [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Services, right-click [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (\<instance name>), where \<instance name> is the name of a local server instance for which you want to enable AlwaysOn Availability Groups, and click Properties.</span></span>  
  
7.  <span data-ttu-id="3fe99-161">选择“AlwaysOn 高可用性”选项卡。</span><span class="sxs-lookup"><span data-stu-id="3fe99-161">Select the AlwaysOn High Availability tab.</span></span>  
  
8.  <span data-ttu-id="3fe99-162">验证“Windows 故障转移群集名称”字段包含本地故障转移群集节点的名称。</span><span class="sxs-lookup"><span data-stu-id="3fe99-162">Verify that Windows failover cluster name field contains the name of the local failover cluster node.</span></span> <span data-ttu-id="3fe99-163">如果此字段为空，则此服务器实例当前不支持 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="3fe99-163">If this field is blank, this server instance currently does not support AlwaysOn Availability Groups.</span></span> <span data-ttu-id="3fe99-164">原因可能是本地计算机不是群集节点、WSFC 群集已关闭或此版本的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 不支持 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="3fe99-164">Either the local computer is not a cluster node, the WSFC cluster has been shut down, or this edition of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that does not support AlwaysOn Availability Groups.</span></span>  
  
9. <span data-ttu-id="3fe99-165">选中“启用 AlwaysOn 可用性组”复选框，然后单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="3fe99-165">Select the Enable AlwaysOn Availability Groups check box, and click OK.</span></span>  
  
10. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3fe99-166">配置管理器保存您的更改。</span><span class="sxs-lookup"><span data-stu-id="3fe99-166">Configuration Manager saves your change.</span></span> <span data-ttu-id="3fe99-167">然后，必须手动重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="3fe99-167">Then, you must manually restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="3fe99-168">这使您可以选择最适合您的业务要求的重新启动时间。</span><span class="sxs-lookup"><span data-stu-id="3fe99-168">This enables you to choose a restart time that is best for your business requirements.</span></span> <span data-ttu-id="3fe99-169">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务重新启动后，AlwaysOn 将启用，而且 IsHadrEnabled 服务器属性将设置为 1。</span><span class="sxs-lookup"><span data-stu-id="3fe99-169">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service restarts, AlwaysOn will be enabled, and the IsHadrEnabled server property will be set to 1.</span></span>  
  
> [!NOTE]
>  -   <span data-ttu-id="3fe99-170">您在目标计算机上必须具有相应的用户权限或被委托了相应的授权才能连接到该计算机。</span><span class="sxs-lookup"><span data-stu-id="3fe99-170">You must have the appropriate user rights or you must have been delegated the appropriate authority on the target computer to connect to that computer.</span></span>  
> -   <span data-ttu-id="3fe99-171">您正在管理的计算机名称显示在控制台树中的“计算机管理”旁边的括号中。</span><span class="sxs-lookup"><span data-stu-id="3fe99-171">The name of the computer that you are managing appears in parentheses next to Computer Management in the console tree.</span></span>  
  
### <a name="using-powershell-cmdlets-to-enable-alwayson-availability-groups"></a><span data-ttu-id="3fe99-172">使用 PowerShell Cmdlet 启用 AlwaysOn 可用性组</span><span class="sxs-lookup"><span data-stu-id="3fe99-172">Using PowerShell Cmdlets to Enable AlwaysOn Availability Groups</span></span>

 <span data-ttu-id="3fe99-173">PowerShell Cmdlet Enable-SqlAlwaysOn 用于在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例上启用 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="3fe99-173">The PowerShell Cmdlet, Enable-SqlAlwaysOn, is used to enable AlwaysOn Availability Group on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3fe99-174">如果当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务正在运行时启用 AlwaysOn 可用性组，则必须重新启动数据库引擎服务才能完成更改。</span><span class="sxs-lookup"><span data-stu-id="3fe99-174">If AlwaysOn Availability Groups is enable while the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service is running, the Database Engine service must be restarted for the change to complete.</span></span> <span data-ttu-id="3fe99-175">除非您指定 -Force 参数，否则，cmdlet 将询问您是否要重新启动服务；如果取消，将不会发生任何操作。</span><span class="sxs-lookup"><span data-stu-id="3fe99-175">Unless you specify the -Force parameter, the cmdlet prompts you to ask whether you wish to restart the service; if cancelled, no operation occurs.</span></span>  
  
 <span data-ttu-id="3fe99-176">您必须拥有管理员权限才能执行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3fe99-176">You must have Administrator permissions to execute this cmdlet.</span></span>  
  
 <span data-ttu-id="3fe99-177">可以使用以下语法之一来为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例启用 AlwaysOn 可用性组：</span><span class="sxs-lookup"><span data-stu-id="3fe99-177">You can use one of the following syntaxes to enable AlwaysOn Availability Groups for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
```  
Enable-SqlAlwaysOn [-Path <string>] [-Credential <PSCredential>] [-Force] [-NoServiceRestart] [-Confirm] [-WhatIf] [<Commom Parameters>]  
```  
  
```  
Enable-SqlAlwaysOn -InputObject <Server> [-Credential <PSCredential>] [-Force] [-NoServiceRestart] [-Confirm] [-WhatIf] [<Commom Parameters>]  
```  
  
```  
Enable-SqlAlwaysOn [-ServerInstance <string>] [-Credential <PSCredential>] [-Force] [-NoServiceRestart] [-Confirm] [-WhatIf] [<Commom Parameters>]  
```  
  
 <span data-ttu-id="3fe99-178">以下 PowerShell 命令在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例 (Machine\Instance) 上启用 AlwaysOn 可用性组：</span><span class="sxs-lookup"><span data-stu-id="3fe99-178">The following PowerShell command enables AlwaysOn Availability Groups on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (Machine\Instance):</span></span>  
  
```powershell
Enable-SqlAlwaysOn -Path SQLSERVER:\SQL\Machine\Instance  
```  
  
## <a name="configuring-remote-access-of-sql-server-running-on-server-core"></a><span data-ttu-id="3fe99-179">配置在服务器核心上运行的 SQL Server 的远程访问</span><span class="sxs-lookup"><span data-stu-id="3fe99-179">Configuring remote access of SQL Server running on Server Core</span></span>  
 <span data-ttu-id="3fe99-180">执行下述操作以配置运行在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Server Core SP1 上的 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 实例的远程访问。</span><span class="sxs-lookup"><span data-stu-id="3fe99-180">Perform the actions described below to configure remote access of a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] instance that is running on [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1.</span></span>  
  
### <a name="enable-remote-connections-on-an-instance-of-sql-server"></a><span data-ttu-id="3fe99-181">在的实例上启用远程连接 SQL Server</span><span class="sxs-lookup"><span data-stu-id="3fe99-181">Enable remote connections on an instance of SQL Server</span></span> 
 <span data-ttu-id="3fe99-182">若要启用远程连接，请在本地使用 SQLCMD.exe 并对 Server Core 实例执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="3fe99-182">To enable remote connections, use SQLCMD.exe locally and execute the following statements against the Server Core instance:</span></span>  
  
-   `EXEC sys.sp_configure N'remote access', N'1'`  
  
     `GO`  
  
-   `RECONFIGURE WITH OVERRIDE`  
  
     `GO`  
  
### <a name="enable-and-start-the-sql-server-browser-service"></a><span data-ttu-id="3fe99-183">启用并启动 SQL Server Browser 服务</span><span class="sxs-lookup"><span data-stu-id="3fe99-183">Enable and start the SQL Server Browser service</span></span>  
 <span data-ttu-id="3fe99-184">默认情况下，Browser 服务是禁用的。</span><span class="sxs-lookup"><span data-stu-id="3fe99-184">By default, the Browser service is disabled.</span></span>  <span data-ttu-id="3fe99-185">如果在 Server Core 上运行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例禁用了该服务，请从命令提示符运行以下命令来启用它：</span><span class="sxs-lookup"><span data-stu-id="3fe99-185">If it is disabled on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on Server Core, run the following command from the command prompt to enable it:</span></span>  
  
 `sc config SQLBROWSER start= auto`  
  
 <span data-ttu-id="3fe99-186">在启用该服务后，请从命令提示符运行以下命令来启动该服务：</span><span class="sxs-lookup"><span data-stu-id="3fe99-186">After it is enabled, run the following command from the command prompt to start the service:</span></span>  
  
 `net start SQLBROWSER`  
  
### <a name="create-exceptions-in-windows-firewall"></a><span data-ttu-id="3fe99-187">在 Windows 防火墙中创建例外</span><span class="sxs-lookup"><span data-stu-id="3fe99-187">Create exceptions in Windows Firewall</span></span>  
 <span data-ttu-id="3fe99-188">若要在 Windows 防火墙中创建 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 访问的例外，请执行 [配置 Windows 防火墙以允许 SQL Server 访问](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)中指定的步骤。</span><span class="sxs-lookup"><span data-stu-id="3fe99-188">To create exceptions for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] access in Windows Firewall, follow the steps specified in [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
### <a name="enable-tcpip-on-an-instance-of-sql-server"></a><span data-ttu-id="3fe99-189">在 SQL Server 的实例上启用 TCP/IP</span><span class="sxs-lookup"><span data-stu-id="3fe99-189">Enable TCP/IP on an instance of SQL Server</span></span>
 <span data-ttu-id="3fe99-190">可以在 Server Core 上通过 Windows PowerShell 为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例启用 TCP/IP 协议。</span><span class="sxs-lookup"><span data-stu-id="3fe99-190">The TCP/IP protocol can be enabled through Windows PowerShell for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on Server Core.</span></span> <span data-ttu-id="3fe99-191">执行以下步骤:</span><span class="sxs-lookup"><span data-stu-id="3fe99-191">Follow these steps:</span></span>  
  
1.  <span data-ttu-id="3fe99-192">在运行 Windows Server 2008 R2 Server Core SP1 的计算机上，启动任务管理器。</span><span class="sxs-lookup"><span data-stu-id="3fe99-192">On the computer that is running Windows Server 2008 R2 Server Core SP1, launch Task Manager.</span></span>  
  
2.  <span data-ttu-id="3fe99-193">在 **“应用程序”** 选项卡上，单击 **“新建任务”** 。</span><span class="sxs-lookup"><span data-stu-id="3fe99-193">On the **Applications** tab, click **New Task**.</span></span>  
  
3.  <span data-ttu-id="3fe99-194">在 **“创建新任务”** 对话框上的 **“打开”** 字段中键入 **sqlps.exe** ，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="3fe99-194">In the **Create New Task** dialog box, type **sqlps.exe** in the **Open** field and then click **OK**.</span></span> <span data-ttu-id="3fe99-195">这将打开 **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** 窗口。</span><span class="sxs-lookup"><span data-stu-id="3fe99-195">This opens the **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** window.</span></span>  
  
4.  <span data-ttu-id="3fe99-196">在 **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** 窗口中，运行以下脚本以启用 TCP/IP 协议：</span><span class="sxs-lookup"><span data-stu-id="3fe99-196">In the **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** window, run the following script to enable the TCP/IP protocol:</span></span>  
  
```powershell
$smo = 'Microsoft.SqlServer.Management.Smo.'  
$wmi = new-object ($smo + 'Wmi.ManagedComputer')  
# Enable the TCP protocol on the default instance.  If the instance is named, replace MSSQLSERVER with the instance name in the following line.  
$uri = "ManagedComputer[@Name='" + (get-item env:\computername).Value + "']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
$Tcp = $wmi.GetSmoObject($uri)  
$Tcp.IsEnabled = $true  
$Tcp.Alter()  
$Tcp  
```  
  
##  <a name="sql-server-profiler"></a><span data-ttu-id="3fe99-197">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="3fe99-197">SQL Server Profiler</span></span>  
 <span data-ttu-id="3fe99-198">在远程计算机上，启动 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 并从“文件”菜单中选择“新建跟踪”，应用程序将显示“连接到服务器”对话框，在此对话框您可以指定要连接的、位于 Server Core 计算机上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="3fe99-198">On a remote machine, start [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and select New Trace from the File menu, the application displays a Connect to Server dialog box where you can specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, residing on the Server Core machine, to which you want to connect.</span></span> <span data-ttu-id="3fe99-199">有关详细信息，请参阅 [Start SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="3fe99-199">For more information, see [Start SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md).</span></span>  
  
 <span data-ttu-id="3fe99-200">有关运行 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]需要哪些权限的信息，请参阅 [运行 SQL Server Profiler 所需的权限](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="3fe99-200">For more information on the permissions required to run [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], see [Permissions Required to Run SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md).</span></span>  
  
 <span data-ttu-id="3fe99-201">有关 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]的其他详细信息，请参阅 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="3fe99-201">For additional details about [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], see [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md).</span></span>  
  
##  <a name="sql-server-auditing"></a><span data-ttu-id="3fe99-202">SQL Server 审核</span><span class="sxs-lookup"><span data-stu-id="3fe99-202">SQL Server Auditing</span></span>  
 <span data-ttu-id="3fe99-203">可以远程使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 定义审核。</span><span class="sxs-lookup"><span data-stu-id="3fe99-203">You can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)] remotely to define an audit.</span></span> <span data-ttu-id="3fe99-204">在创建并启用审核后，目标将接收各项。</span><span class="sxs-lookup"><span data-stu-id="3fe99-204">After the audit is created and enabled, the target will receive entries.</span></span> <span data-ttu-id="3fe99-205">有关创建和管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 审核的详细信息，请参阅 [SQL Server 审核（数据库引擎）](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="3fe99-205">For more information about creating and managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] audits, see [SQL Server Audit &#40;Database Engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).</span></span>  
  
##  <a name="sql-servevr-command-prompt-utilities"></a><span data-ttu-id="3fe99-206">SQL Servevr 命令提示实用工具</span><span class="sxs-lookup"><span data-stu-id="3fe99-206">SQL Servevr Command Prompt Utilities</span></span>  
 <span data-ttu-id="3fe99-207">可以使用以下命令提示实用工具，它们允许您在 Server Core 计算机上为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 操作编写脚本。</span><span class="sxs-lookup"><span data-stu-id="3fe99-207">You can use the following command prompt utilities that enable you to script [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] operations on a Server Core machine.</span></span> <span data-ttu-id="3fe99-208">下表包含了随 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供的用于 Server Core 的命令提示实用工具列表：</span><span class="sxs-lookup"><span data-stu-id="3fe99-208">The following table contains a list of command prompt utilities that ship with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for Server Core:</span></span>  
  
|<span data-ttu-id="3fe99-209">**实用工具**</span><span class="sxs-lookup"><span data-stu-id="3fe99-209">**Utility**</span></span>|<span data-ttu-id="3fe99-210">**说明**</span><span class="sxs-lookup"><span data-stu-id="3fe99-210">**Description**</span></span>|<span data-ttu-id="3fe99-211">**安装位置**</span><span class="sxs-lookup"><span data-stu-id="3fe99-211">**Installed in**</span></span>|  
|-----------------|---------------------|----------------------|  
|[<span data-ttu-id="3fe99-212">bcp 实用工具</span><span class="sxs-lookup"><span data-stu-id="3fe99-212">bcp Utility</span></span>](../../tools/bcp-utility.md)|<span data-ttu-id="3fe99-213">用于在 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例和用户指定格式的数据文件之间复制数据。</span><span class="sxs-lookup"><span data-stu-id="3fe99-213">Used to copy data between an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and a data file in a user-specified format.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="3fe99-214">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="3fe99-214">Tools\Binn</span></span>|  
|[<span data-ttu-id="3fe99-215">dtexec 实用工具</span><span class="sxs-lookup"><span data-stu-id="3fe99-215">dtexec Utility</span></span>](../../integration-services/packages/dtexec-utility.md)|<span data-ttu-id="3fe99-216">用于配置和执行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="3fe99-216">Used to configure and execute an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="3fe99-217">DTS\Binn</span><span class="sxs-lookup"><span data-stu-id="3fe99-217">DTS\Binn</span></span>|  
|[<span data-ttu-id="3fe99-218">dtutil 实用工具</span><span class="sxs-lookup"><span data-stu-id="3fe99-218">dtutil Utility</span></span>](../../integration-services/dtutil-utility.md)|<span data-ttu-id="3fe99-219">用于管理 SSIS 包。</span><span class="sxs-lookup"><span data-stu-id="3fe99-219">Used to manage SSIS packages.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="3fe99-220">DTS\Binn</span><span class="sxs-lookup"><span data-stu-id="3fe99-220">DTS\Binn</span></span>|  
|[<span data-ttu-id="3fe99-221">osql 实用工具</span><span class="sxs-lookup"><span data-stu-id="3fe99-221">osql Utility</span></span>](../../tools/osql-utility.md)|<span data-ttu-id="3fe99-222">您可以在命令提示符下输入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句、系统过程和脚本文件。</span><span class="sxs-lookup"><span data-stu-id="3fe99-222">Allows you to enter [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, system procedures, and script files at the command prompt.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="3fe99-223">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="3fe99-223">Tools\Binn</span></span>|  
|[<span data-ttu-id="3fe99-224">sqlagent90 应用程序</span><span class="sxs-lookup"><span data-stu-id="3fe99-224">sqlagent90 Application</span></span>](../../tools/sqlagent90-application.md)|<span data-ttu-id="3fe99-225">用于在命令提示符下启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理。</span><span class="sxs-lookup"><span data-stu-id="3fe99-225">Used to start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent from a command prompt.</span></span>|<span data-ttu-id="3fe99-226">\<drive>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\<instance_name>\MSSQL\Binn</span><span class="sxs-lookup"><span data-stu-id="3fe99-226">\<drive>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\<*instance_name*>\MSSQL\Binn</span></span>|  
|[<span data-ttu-id="3fe99-227">sqlcmd 实用工具</span><span class="sxs-lookup"><span data-stu-id="3fe99-227">sqlcmd Utility</span></span>](../../tools/sqlcmd-utility.md)|<span data-ttu-id="3fe99-228">您可以在命令提示符下输入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句、系统过程和脚本文件。</span><span class="sxs-lookup"><span data-stu-id="3fe99-228">Allows you to enter [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, system procedures, and script files at the command prompt.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="3fe99-229">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="3fe99-229">Tools\Binn</span></span>|  
|[<span data-ttu-id="3fe99-230">SQLdiag 实用工具</span><span class="sxs-lookup"><span data-stu-id="3fe99-230">SQLdiag Utility</span></span>](../../tools/sqldiag-utility.md)|<span data-ttu-id="3fe99-231">用于为 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客户服务和支持部门收集诊断信息。</span><span class="sxs-lookup"><span data-stu-id="3fe99-231">Used to collect diagnostic information for [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="3fe99-232">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="3fe99-232">Tools\Binn</span></span>|  
|[<span data-ttu-id="3fe99-233">sqlmaint 实用工具</span><span class="sxs-lookup"><span data-stu-id="3fe99-233">sqlmaint Utility</span></span>](../../tools/sqlmaint-utility.md)|<span data-ttu-id="3fe99-234">用于执行在早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中创建的数据库维护计划。</span><span class="sxs-lookup"><span data-stu-id="3fe99-234">Used to execute database maintenance plans created in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|<span data-ttu-id="3fe99-235">\<drive>： \Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSSQL12。MSSQLSERVER\MSSQL\Binn</span><span class="sxs-lookup"><span data-stu-id="3fe99-235">\<drive>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.MSSQLSERVER\MSSQL\Binn</span></span>|  
|[<span data-ttu-id="3fe99-236">sqlps 实用工具</span><span class="sxs-lookup"><span data-stu-id="3fe99-236">sqlps Utility</span></span>](../../tools/sqlps-utility.md)|<span data-ttu-id="3fe99-237">用于运行 PowerShell 命令和脚本。</span><span class="sxs-lookup"><span data-stu-id="3fe99-237">Used to run PowerShell commands and scripts.</span></span> <span data-ttu-id="3fe99-238">加载和注册 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 提供程序和 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3fe99-238">Loads and registers the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell provider and cmdlets.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="3fe99-239">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="3fe99-239">Tools\Binn</span></span>|  
|[<span data-ttu-id="3fe99-240">sqlservr Application</span><span class="sxs-lookup"><span data-stu-id="3fe99-240">sqlservr Application</span></span>](../../tools/sqlservr-application.md)|<span data-ttu-id="3fe99-241">用于在命令提示符下启动和停止 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例以进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="3fe99-241">Used to start and stop an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] from the command prompt for troubleshooting.</span></span>|<span data-ttu-id="3fe99-242">\<drive>： \Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSSQL12。MSSQLSERVER\MSSQL\Binn</span><span class="sxs-lookup"><span data-stu-id="3fe99-242">\<drive>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.MSSQLSERVER\MSSQL\Binn</span></span>|  
  
##  <a name="use-troubleshooting-tools"></a><span data-ttu-id="3fe99-243">使用故障排除工具</span><span class="sxs-lookup"><span data-stu-id="3fe99-243">Use troubleshooting tools</span></span>  
 <span data-ttu-id="3fe99-244">可以使用 [SQLdiag 实用工具](../../tools/sqldiag-utility.md) 从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和其他类型的服务器中收集日志和数据文件，同时还可将其用于一直监视服务器或对服务器的特定问题进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="3fe99-244">You can use [SQLdiag Utility](../../tools/sqldiag-utility.md) to collect logs and data files from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and other types of servers, and use it to monitor your servers over time or troubleshoot specific problems with your servers.</span></span> <span data-ttu-id="3fe99-245">SQLdiag 用于加快和简化为 Microsoft 客户支持服务部门收集诊断信息的过程。</span><span class="sxs-lookup"><span data-stu-id="3fe99-245">SQLdiag is intended to expedite and simplify diagnostic information gathering for Microsoft Customer Support Services.</span></span>  
  
 <span data-ttu-id="3fe99-246">您可以在 Server Core 上使用以下主题中指定的语法在管理员命令提示符下启动该实用工具： [SQLdiag Utility](../../tools/sqldiag-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="3fe99-246">You can launch the utility on the administrator command prompt on the Server Core, using the syntax specified in the topic: [SQLdiag Utility](../../tools/sqldiag-utility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fe99-247">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3fe99-247">See Also</span></span>  
 <span data-ttu-id="3fe99-248">[在 Server Core 上安装 SQL Server 2014](install-sql-server-on-server-core.md) </span><span class="sxs-lookup"><span data-stu-id="3fe99-248">[Install SQL Server 2014 on Server Core](install-sql-server-on-server-core.md) </span></span>  
 [<span data-ttu-id="3fe99-249">安装操作指南主题</span><span class="sxs-lookup"><span data-stu-id="3fe99-249">Installation How-to Topics</span></span>](../../sql-server/install/installation-how-to-topics.md)  
