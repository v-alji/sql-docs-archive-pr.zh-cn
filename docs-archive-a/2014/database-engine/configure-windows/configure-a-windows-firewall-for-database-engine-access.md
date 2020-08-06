---
title: 为数据库引擎访问配置 Windows 防火墙 | Microsoft Docs
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], firewall systems
- firewall systems, [Database Engine]
- security [SQL Server], firewalls
ms.assetid: 0093b43c-c6b5-4574-9b30-3a0e91e1a1f9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f76eecb4dd48f3e7f54cad79953773f8432f416e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591599"
---
# <a name="configure-a-windows-firewall-for-database-engine-access"></a><span data-ttu-id="efcb8-102">为数据库引擎访问配置 Windows 防火墙</span><span class="sxs-lookup"><span data-stu-id="efcb8-102">Configure a Windows Firewall for Database Engine Access</span></span>
  <span data-ttu-id="efcb8-103">本主题说明如何使用 SQL Server 配置管理器在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中为数据库引擎访问配置 Windows 防火墙。</span><span class="sxs-lookup"><span data-stu-id="efcb8-103">This topic describes how to configure a Windows firewall for Database Engine access in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="efcb8-104">防火墙系统有助于阻止对计算机资源进行未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="efcb8-104">Firewall systems help prevent unauthorized access to computer resources.</span></span> <span data-ttu-id="efcb8-105">若要通过防火墙访问 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例，必须在运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的计算机上配置防火墙以允许访问。</span><span class="sxs-lookup"><span data-stu-id="efcb8-105">To access an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] through a firewall, you must configure the firewall on the computer running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to allow access.</span></span>  
  
 <span data-ttu-id="efcb8-106">有关默认 Windows 防火墙设置的详细信息以及有关影响 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、Analysis Services、Reporting Services 和 Integration Services 的 TCP 端口的说明，请参阅 [配置 Windows 防火墙以允许 SQL Server 访问](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="efcb8-106">For more information about the default Windows firewall settings, and a description of the TCP ports that affect the [!INCLUDE[ssDE](../../includes/ssde-md.md)], Analysis Services, Reporting Services, and Integration Services, see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span> <span data-ttu-id="efcb8-107">有很多可用的防火墙系统。</span><span class="sxs-lookup"><span data-stu-id="efcb8-107">There are many firewall systems available.</span></span> <span data-ttu-id="efcb8-108">有关特定于您系统的信息，请参阅防火墙文档。</span><span class="sxs-lookup"><span data-stu-id="efcb8-108">For information specific to your system, see the firewall documentation.</span></span>  
  
 <span data-ttu-id="efcb8-109">为允许访问而执行的主要步骤如下：</span><span class="sxs-lookup"><span data-stu-id="efcb8-109">The principal steps to allow access are:</span></span>  
  
1.  <span data-ttu-id="efcb8-110">将 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 配置为使用特定的 TCP/IP 端口。</span><span class="sxs-lookup"><span data-stu-id="efcb8-110">Configure the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to use a specific TCP/IP port.</span></span> <span data-ttu-id="efcb8-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 的默认实例使用端口 1433，但可以更改。</span><span class="sxs-lookup"><span data-stu-id="efcb8-111">The default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] uses port 1433, but that can be changed.</span></span> <span data-ttu-id="efcb8-112">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 所使用的端口在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志中列出。</span><span class="sxs-lookup"><span data-stu-id="efcb8-112">The port used by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is listed in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span> <span data-ttu-id="efcb8-113">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 实例、[!INCLUDE[ssEW](../../includes/ssew-md.md)] 实例以及[!INCLUDE[ssDE](../../includes/ssde-md.md)]的命名实例使用动态端口。</span><span class="sxs-lookup"><span data-stu-id="efcb8-113">Instances of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], [!INCLUDE[ssEW](../../includes/ssew-md.md)], and named instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] use dynamic ports.</span></span> <span data-ttu-id="efcb8-114">若要配置这些实例以使用特定端口，请参阅[配置服务器以侦听特定 TCP 端口（SQL Server 配置管理器）](configure-a-server-to-listen-on-a-specific-tcp-port.md)。</span><span class="sxs-lookup"><span data-stu-id="efcb8-114">To configure these instances to use a specific port, see [Configure a Server to Listen on a Specific TCP Port &#40;SQL Server Configuration Manager&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md).</span></span>  
  
2.  <span data-ttu-id="efcb8-115">将防火墙配置为允许授权的用户或计算机访问此端口。</span><span class="sxs-lookup"><span data-stu-id="efcb8-115">Configure the firewall to allow access to that port for authorized users or computers.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="efcb8-116">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务，用户可以连接到不在侦听端口 1433 的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例，因而无需知道端口号。</span><span class="sxs-lookup"><span data-stu-id="efcb8-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service lets users connect to instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that are not listening on port 1433, without knowing the port number.</span></span> <span data-ttu-id="efcb8-117">若要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser，必须打开 UDP 端口 1434。</span><span class="sxs-lookup"><span data-stu-id="efcb8-117">To use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, you must open UDP port 1434.</span></span> <span data-ttu-id="efcb8-118">若要提升最安全的环境，请停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务，并将客户端配置为使用端口号进行连接。</span><span class="sxs-lookup"><span data-stu-id="efcb8-118">To promote the most secure environment, leave the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service stopped, and configure clients to connect using the port number.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="efcb8-119">默认情况下， [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 将启用 Windows 防火墙，这会关闭端口 1433，从而防止 Internet 计算机连接到您计算机上的默认 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="efcb8-119">By default, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows enables the Windows Firewall, which closes port 1433 to prevent Internet computers from connecting to a default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on your computer.</span></span> <span data-ttu-id="efcb8-120">重新打开端口 1433 之后，才可以使用 TCP/IP 连接到默认实例。</span><span class="sxs-lookup"><span data-stu-id="efcb8-120">Connections to the default instance using TCP/IP are not possible unless you reopen port 1433.</span></span> <span data-ttu-id="efcb8-121">以下过程提供了配置 Windows 防火墙的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="efcb8-121">The basic steps to configure the Windows firewall are provided in the following procedures.</span></span> <span data-ttu-id="efcb8-122">有关详细信息，请参阅 Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="efcb8-122">For more information, see the Windows documentation.</span></span>  
  
 <span data-ttu-id="efcb8-123">除了将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置为侦听固定端口并打开此端口之外，您还可以将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可执行文件 (Sqlservr.exe) 作为已阻止程序的例外列出。</span><span class="sxs-lookup"><span data-stu-id="efcb8-123">As an alternative to configuring [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to listen on a fixed port and opening the port, you can list the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executable (Sqlservr.exe) as an exception to the blocked programs.</span></span> <span data-ttu-id="efcb8-124">如果要继续使用动态端口，则使用此方法。</span><span class="sxs-lookup"><span data-stu-id="efcb8-124">Use this method when you want to continue to use dynamic ports.</span></span> <span data-ttu-id="efcb8-125">通过这种方式只能访问一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="efcb8-125">Only one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be accessed in this way.</span></span>  
  
 <span data-ttu-id="efcb8-126">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="efcb8-126">**In This Topic**</span></span>  
  
-   <span data-ttu-id="efcb8-127">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="efcb8-127">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="efcb8-128">安全性</span><span class="sxs-lookup"><span data-stu-id="efcb8-128">Security</span></span>](#Security)  
  
-   <span data-ttu-id="efcb8-129">**若要为数据库引擎访问配置 Windows 防火墙，请使用：**</span><span class="sxs-lookup"><span data-stu-id="efcb8-129">**To configure a Windows Firewall for Database Engine access, using:**</span></span>  
  
     [<span data-ttu-id="efcb8-130">SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="efcb8-130">SQL Server Configuration Manager</span></span>](#SSMSProcedure)  
  
## <a name="before-you-begin"></a><span data-ttu-id="efcb8-131">开始之前</span><span class="sxs-lookup"><span data-stu-id="efcb8-131">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="efcb8-132">Security</span><span class="sxs-lookup"><span data-stu-id="efcb8-132">Security</span></span>  
 <span data-ttu-id="efcb8-133">打开防火墙的端口可能会使服务器受到恶意攻击。</span><span class="sxs-lookup"><span data-stu-id="efcb8-133">Opening ports in your firewall can leave your server exposed to malicious attacks.</span></span> <span data-ttu-id="efcb8-134">请确保在打开端口之前了解防火墙系统。</span><span class="sxs-lookup"><span data-stu-id="efcb8-134">Make sure that you understand firewall systems before you open ports.</span></span> <span data-ttu-id="efcb8-135">有关详细信息，请参阅 [Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)</span><span class="sxs-lookup"><span data-stu-id="efcb8-135">For more information, see [Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="efcb8-136">使用 SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="efcb8-136">Using SQL Server Configuration Manager</span></span>  
 <span data-ttu-id="efcb8-137">适用于 Windows Vista、Windows 7 和 Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="efcb8-137">Applies to Windows Vista, Windows 7, and Windows Server 2008</span></span>  
  
 <span data-ttu-id="efcb8-138">以下过程通过使用具有高级安全 Microsoft 管理控制台 (MMC) 管理单元的 Windows 防火墙来配置该 Windows 防火墙。</span><span class="sxs-lookup"><span data-stu-id="efcb8-138">The following procedures configure the Windows Firewall by using the Windows Firewall with Advanced Security Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="efcb8-139">高级安全 Windows 防火墙仅配置当前配置文件。</span><span class="sxs-lookup"><span data-stu-id="efcb8-139">The Windows Firewall with Advanced Security only configures the current profile.</span></span> <span data-ttu-id="efcb8-140">有关高级安全 Windows 防火墙的详细信息，请参阅 [配置 Windows 防火墙以允许 SQL Server 访问](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)</span><span class="sxs-lookup"><span data-stu-id="efcb8-140">For more information about the Windows Firewall with Advanced Security, see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)</span></span>  
  
#### <a name="to-open-a-port-in-the-windows-firewall-for-tcp-access"></a><span data-ttu-id="efcb8-141">打开 Windows 防火墙的端口以进行 TCP 访问</span><span class="sxs-lookup"><span data-stu-id="efcb8-141">To open a port in the Windows firewall for TCP access</span></span>  
  
1.  <span data-ttu-id="efcb8-142">在 **“开始”** 菜单上，单击 **“运行”** ，键入 **WF.msc**，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="efcb8-142">On the **Start** menu, click **Run**, type **WF.msc**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="efcb8-143">在“高级安全 Windows 防火墙”的左窗格中，右键单击“入站规则”，并在操作窗格中单击“新建规则”。  </span><span class="sxs-lookup"><span data-stu-id="efcb8-143">In the **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then click **New Rule** in the action pane.</span></span>  
  
3.  <span data-ttu-id="efcb8-144">在 **“规则类型”** 对话框中，选择 **“端口”** ，然后单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="efcb8-144">In the **Rule Type** dialog box, select **Port**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="efcb8-145">在 **“协议和端口”** 对话框中，选择 **TCP**。</span><span class="sxs-lookup"><span data-stu-id="efcb8-145">In the **Protocol and Ports** dialog box, select **TCP**.</span></span> <span data-ttu-id="efcb8-146">选择 "**特定本地端口**"，然后键入实例的端口号 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ，例如 `1433` 用于默认实例的端口号。</span><span class="sxs-lookup"><span data-stu-id="efcb8-146">Select **Specific local ports**, and then type the port number of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], such as `1433` for the default instance.</span></span> <span data-ttu-id="efcb8-147">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="efcb8-147">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="efcb8-148">在 **“操作”** 对话框中，选择 **“允许连接”** ，然后单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="efcb8-148">In the **Action** dialog box, select **Allow the connection**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="efcb8-149">在 **“配置文件”** 对话框中，选择在您想要连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]时描述计算机连接环境的任何配置文件，然后单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="efcb8-149">In the **Profile** dialog box, select any profiles that describe the computer connection environment when you want to connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)], and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="efcb8-150">在 **“名称”** 对话框中，输入此规则的名称和说明，再单击 **“完成”** 。</span><span class="sxs-lookup"><span data-stu-id="efcb8-150">In the **Name** dialog box, type a name and description for this rule, and then click **Finish**.</span></span>  
  
#### <a name="to-open-access-to-sql-server-when-using-dynamic-ports"></a><span data-ttu-id="efcb8-151">在使用动态端口时打开对 SQL Server 的访问</span><span class="sxs-lookup"><span data-stu-id="efcb8-151">To open access to SQL Server when using dynamic ports</span></span>  
  
1.  <span data-ttu-id="efcb8-152">在 **“开始”** 菜单上，单击 **“运行”** ，键入 **WF.msc**，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="efcb8-152">On the **Start** menu, click **Run**, type **WF.msc**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="efcb8-153">在“高级安全 Windows 防火墙”的左窗格中，右键单击“入站规则”，并在操作窗格中单击“新建规则”。  </span><span class="sxs-lookup"><span data-stu-id="efcb8-153">In the **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then click **New Rule** in the action pane.</span></span>  
  
3.  <span data-ttu-id="efcb8-154">在 **“规则类型”** 对话框中，选择 **“程序”** ，然后单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="efcb8-154">In the **Rule Type** dialog box, select **Program**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="efcb8-155">在 **“程序”** 对话框中，选择 **“此程序路径”** 。</span><span class="sxs-lookup"><span data-stu-id="efcb8-155">In the **Program** dialog box, select **This program path**.</span></span> <span data-ttu-id="efcb8-156">单击 **“浏览”** ，导航到要通过防火墙访问的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，再单击 **“打开”** 。</span><span class="sxs-lookup"><span data-stu-id="efcb8-156">Click **Browse**, and navigate to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to access through the firewall, and then click **Open**.</span></span> <span data-ttu-id="efcb8-157">默认情况下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 位于**C:\PROGRAM Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Sqlservr.exe**。</span><span class="sxs-lookup"><span data-stu-id="efcb8-157">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is at **C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Sqlservr.exe**.</span></span> <span data-ttu-id="efcb8-158">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="efcb8-158">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="efcb8-159">在 **“操作”** 对话框中，选择 **“允许连接”** ，然后单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="efcb8-159">In the **Action** dialog box, select **Allow the connection**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="efcb8-160">在 **“配置文件”** 对话框中，选择在您想要连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]时描述计算机连接环境的任何配置文件，然后单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="efcb8-160">In the **Profile** dialog box, select any profiles that describe the computer connection environment when you want to connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)], and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="efcb8-161">在 **“名称”** 对话框中，输入此规则的名称和说明，再单击 **“完成”** 。</span><span class="sxs-lookup"><span data-stu-id="efcb8-161">In the **Name** dialog box, type a name and description for this rule, and then click **Finish**.</span></span>  
  
  
