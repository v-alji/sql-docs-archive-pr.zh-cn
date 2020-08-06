---
title: 将多宿主计算机配置为允许 SQL Server 访问 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- ports [SQL Server], multi-homed computer
- multi-homed computer [SQL Server] configuring ports
- firewall systems [Database Engine], multi-homed computer
ms.assetid: ba369e5b-7d1f-4544-b7f1-9b098a1e75bc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b20fa552e57441ef211049f0e51b4f8d65e6f2e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588263"
---
# <a name="configure-a-multi-homed-computer-for-sql-server-access"></a><span data-ttu-id="c3b3e-102">将多宿主计算机配置为允许 SQL Server 访问</span><span class="sxs-lookup"><span data-stu-id="c3b3e-102">Configure a Multi-Homed Computer for SQL Server Access</span></span>
  <span data-ttu-id="c3b3e-103">当服务器必须提供与两个或更多个网络或网络子网的连接时，典型的方案是使用多宿主计算机。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-103">When a server must provide a connection to two or more networks or network subnets, a typical scenario uses a multi-homed computer.</span></span> <span data-ttu-id="c3b3e-104">此计算机通常位于外围网络（也称为 DMZ、外围安全区域或屏蔽子网）中。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-104">Frequently this computer is located in a perimeter network (also known as DMZ, demilitarized zone, or screened subnet).</span></span> <span data-ttu-id="c3b3e-105">本主题介绍如何在多宿主环境中对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和高级安全 Windows 防火墙进行配置，以便为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例提供多个网络连接。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-105">This topic describes how to configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows Firewall with Advanced Security to provide for network connections to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a multi-homed environment.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c3b3e-106">多宿主计算机有多个网络适配器或者已配置为一个网络适配器使用多个 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-106">A multi-homed computer has multiple network adapters or has been configured to use multiple IP addresses for a single network adapter.</span></span> <span data-ttu-id="c3b3e-107">双宿主计算机有两个网络适配器或者已配置为一个网络适配器使用两个 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-107">A dual-homed computer has two network adapters or has been configured to use two IP addresses for a single network adapter.</span></span>  
  
 <span data-ttu-id="c3b3e-108">在继续本主题之前，你应当熟悉 [配置 Windows 防火墙以允许 SQL Server 访问](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)主题中提供的信息。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-108">Before you continue in this topic, you should be familiar with the information provided in the topic [Configure the Windows Firewall to Allow SQL Server Access](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span> <span data-ttu-id="c3b3e-109">本主题包含有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件如何与防火墙一起使用的基本信息。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-109">This topic contains basic information about how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components work with the firewall.</span></span>  
  
 <span data-ttu-id="c3b3e-110">**本示例假设：**</span><span class="sxs-lookup"><span data-stu-id="c3b3e-110">**Assumptions for this example:**</span></span>  
  
-   <span data-ttu-id="c3b3e-111">计算机中安装了两个网络适配器。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-111">There are two network adapters installed in the computer.</span></span> <span data-ttu-id="c3b3e-112">可以有一个或多个网络适配器是无线的。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-112">One or more of the network adapters can be wireless.</span></span> <span data-ttu-id="c3b3e-113">可以通过使用一个网络适配器的 IP 地址，使用环回 IP 地址 (127.0.0.1) 作为第二个网络适配器来模拟有两个网络适配器。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-113">You can simulate having two network adapters by using the IP address of one network adapter, and using the loopback IP address (127.0.0.1) as the second network adapter.</span></span>  
  
-   <span data-ttu-id="c3b3e-114">为简单起见，本示例使用 IPv4 地址。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-114">For simplicity, this example uses IPv4 addresses.</span></span> <span data-ttu-id="c3b3e-115">使用 IPv6 地址可执行相同的过程。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-115">The same procedures can be performed by using IPv6 addresses.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c3b3e-116">IPv4 地址是一串四个数字（称为八位字节）。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-116">IPv4 addresses are a series of four numbers known as octets.</span></span> <span data-ttu-id="c3b3e-117">每个数字小于 255，由句点分隔，例如 127.0.0.1。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-117">Each number is less than 255, separated by periods, such as 127.0.0.1.</span></span> <span data-ttu-id="c3b3e-118">IPv6 地址是一串八个十六进制数字，由冒号分隔，如 fe80:4898:23:3:49a6:f5c1:2452:b994。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-118">IPv6 addresses are a series of eight hexadecimal numbers separated by colons, such as fe80:4898:23:3:49a6:f5c1:2452:b994.</span></span>  
  
-   <span data-ttu-id="c3b3e-119">防火墙规则可能允许通过特定端口（如端口 1433）进行访问，</span><span class="sxs-lookup"><span data-stu-id="c3b3e-119">Firewall rules could allow access through a specific port, such as port 1433.</span></span> <span data-ttu-id="c3b3e-120">也可能允许访问 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 程序 (sqlservr.exe)。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-120">Or firewall rules could allow access to the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] program (sqlservr.exe).</span></span> <span data-ttu-id="c3b3e-121">哪个方法都不会比另一个方法更好。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-121">Neither method is better than the other.</span></span> <span data-ttu-id="c3b3e-122">因为外围网络中的服务器比 Intranet 上的服务器更容易受到攻击，本主题假设您希望进行更精确的控制并单独选择打开的端口。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-122">Because a server in a perimeter network is more vulnerable to attack than servers on an intranet, this topic assumes that you want to have more precise control, and individually select the ports that you open.</span></span> <span data-ttu-id="c3b3e-123">出于上述原因，本主题假设您将把 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置为侦听固定端口。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-123">For that reason, this topic assumes that you will configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to listen on a fixed port.</span></span> <span data-ttu-id="c3b3e-124">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所用端口的详细信息，请参阅 [配置 Windows 防火墙以允许 SQL Server 访问](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-124">For more information about the ports that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses, see [Configure the Windows Firewall to Allow SQL Server Access](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
-   <span data-ttu-id="c3b3e-125">本示例使用 TCP 端口 1433 配置对 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的访问。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-125">This example configures access to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by using TCP port 1433.</span></span> <span data-ttu-id="c3b3e-126">可以使用相同的常规步骤来配置不同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件使用的其他端口。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-126">The other ports that are the different [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components use can be configured by using the same general steps.</span></span>  
  
 <span data-ttu-id="c3b3e-127">**本示例中的常规步骤如下：**</span><span class="sxs-lookup"><span data-stu-id="c3b3e-127">**The general steps in this example are as follows:**</span></span>  
  
-   <span data-ttu-id="c3b3e-128">确定计算机的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-128">Determine the IP addresses on the computer.</span></span>  
  
-   <span data-ttu-id="c3b3e-129">将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置为侦听特定的 TCP 端口。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-129">Configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to listen on a specific TCP port.</span></span>  
  
-   <span data-ttu-id="c3b3e-130">配置高级安全 Windows 防火墙。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-130">Configure Windows Firewall with Advanced Security.</span></span>  
  
## <a name="optional-procedures"></a><span data-ttu-id="c3b3e-131">可选过程</span><span class="sxs-lookup"><span data-stu-id="c3b3e-131">Optional Procedures</span></span>  
 <span data-ttu-id="c3b3e-132">如果您已经知道计算机可用的 IP 地址且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用该地址，则可以跳过这些过程。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-132">If you already know the IP addresses available to your computer and that are used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can skip these procedures.</span></span>  
  
#### <a name="to-determine-the-ip-addresses-available-on-the-computer"></a><span data-ttu-id="c3b3e-133">确定计算机上可用的 IP 地址</span><span class="sxs-lookup"><span data-stu-id="c3b3e-133">To determine the IP addresses available on the computer</span></span>  
  
1.  <span data-ttu-id="c3b3e-134">在安装了的计算机上 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，依次单击 "**开始**"、"**运行**"， `cmd` 然后键入 [!INCLUDE[clickOK](../../includes/clickok-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-134">On the computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed, click **Start**, click **Run**, type `cmd` and then [!INCLUDE[clickOK](../../includes/clickok-md.md)].</span></span>  
  
2.  <span data-ttu-id="c3b3e-135">在“命令提示符”窗口中，键入 `ipconfig,`，然后按 Enter 列出此计算机上可用的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-135">In the Command Prompt window, type `ipconfig,` and then press ENTER to list the IP addresses available on this computer.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c3b3e-136">**ipconfig** 命令有时会列出许多可能的连接，包括已断开的连接。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-136">The **ipconfig** command sometimes lists many possible connections, including connections that are disconnected.</span></span> <span data-ttu-id="c3b3e-137">**ipconfig** 命令可同时列出 IPv4 和 IPv6 地址。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-137">The **ipconfig** command can list both IPv4 and IPv6 addresses.</span></span>  
  
3.  <span data-ttu-id="c3b3e-138">请注意正在使用的 IPv4 地址和 IPv6 地址。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-138">Note the IPv4 addresses and IPv6 addresses that are being used.</span></span> <span data-ttu-id="c3b3e-139">列表中的其他信息（例如临时地址、子网掩码和默认网关）是配置 TCP/IP 网络的重要信息。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-139">The other information in the list, such as temporary addresses, subnet masks, and default gateways is important information for configuring a TCP/IP network.</span></span> <span data-ttu-id="c3b3e-140">但是在本示例中未用到这些信息。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-140">But this information is not used in this example.</span></span>  
  
#### <a name="to-determine-the-ip-addresses-and-ports-used-by-ssnoversion"></a><span data-ttu-id="c3b3e-141">确定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3b3e-141">To determine the IP addresses and ports used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
1.  <span data-ttu-id="c3b3e-142">单击 **“开始”** ，依次指向 **“所有程序”** 、 [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]和 **“配置工具”** ，然后单击 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-142">Click **Start**, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="c3b3e-143">在\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager**的控制台窗格中，展开 " \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 网络配置**"，展开 "**的 \<instance name> 协议**"，然后双击 " **tcp/ip**"。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-143">In **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager**, in the console pane, expand **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Network Configuration**, expand **Protocols for \<instance name>**, and then double-click **TCP/IP**.</span></span>  
  
3.  <span data-ttu-id="c3b3e-144">在“TCP/IP 属性”  对话框的“IP 地址”  选项卡上，将显示若干个 IP 地址，格式为：**IP1**、**IP2**...，一直到 **IPAll**。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-144">In the **TCP/IP Properties** dialog box, on the **IP Addresses** tab, several IP addresses appear in the format **IP1**, **IP2**, up to **IPAll**.</span></span> <span data-ttu-id="c3b3e-145">这些 IP 地址中有一个是环回适配器的 IP 地址 (127.0.0.1)。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-145">One of these is for the IP address of the loopback adapter, 127.0.0.1.</span></span> <span data-ttu-id="c3b3e-146">其他 IP 地址是计算机上配置的各个 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-146">Additional IP addresses appear for each IP Address configured on the computer.</span></span>  
  
4.  <span data-ttu-id="c3b3e-147">对于任意 IP 地址，如果 **“TCP 动态端口”** 对话框中包含 **0**，则指示 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 正在侦听动态端口。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-147">For any IP address if the **TCP Dynamic Ports** dialog box contains **0**, this indicates that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is listening on dynamic ports.</span></span> <span data-ttu-id="c3b3e-148">本示例使用固定端口，而不是使用在重新启动时会发生更改的动态端口。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-148">This example uses fixed ports instead of dynamic ports which could change upon restart.</span></span> <span data-ttu-id="c3b3e-149">因此，如果 **“TCP 动态端口”** 对话框中包含 **0**，则删除 0。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-149">Therefore if the **TCP Dynamic Ports** dialog box contains **0**, delete the 0.</span></span>  
  
5.  <span data-ttu-id="c3b3e-150">请注意为要配置的每个 IP 地址列出的 TCP 端口。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-150">Note the TCP port that is listed for each IP address that you want to configure.</span></span> <span data-ttu-id="c3b3e-151">对于本示例，假设两个 IP 地址都侦听默认端口 1433。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-151">For this example, assume that both IP addresses are listening on the default port, 1433.</span></span>  
  
6.  <span data-ttu-id="c3b3e-152">如果不希望 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用某些可用端口，则请在 **“协议”** 选项卡上将 **“全部侦听”** 值更改为 **“否”** ；在 **“IP 地址”** 选项卡上，将不想使用的 IP 地址的 **“活动”** 值更改为 **“否”** 。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-152">If you do not want [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use some of the available ports, on the **Protocol** tab, change the **Listen All** value to **No**; and on the **IP Addresses** tab, change the **Active** value to **No** for the IP addresses that you do not want to use.</span></span>  
  
## <a name="configuring-windows-firewall-with-advanced-security"></a><span data-ttu-id="c3b3e-153">配置高级安全 Windows 防火墙</span><span class="sxs-lookup"><span data-stu-id="c3b3e-153">Configuring Windows Firewall with Advanced Security</span></span>  
 <span data-ttu-id="c3b3e-154">知道计算机所使用的 IP 地址和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所使用的端口后，就可以创建防火墙规则，然后为特定的 IP 地址配置这些规则。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-154">After you know the IP addresses that the computer uses and the ports that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses, you can create firewall rules, and then configure those rules for specific IP addresses.</span></span>  
  
#### <a name="to-create-a-firewall-rule"></a><span data-ttu-id="c3b3e-155">创建防火墙规则</span><span class="sxs-lookup"><span data-stu-id="c3b3e-155">To create a firewall rule</span></span>  
  
1.  <span data-ttu-id="c3b3e-156">在安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的计算机上，以管理员身份登录。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-156">On the computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed, log on as an administrator..</span></span>  
  
2.  <span data-ttu-id="c3b3e-157">单击 "**开始**"，再单击 "**运行**"，键入 `wf.msc` ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-157">Click **Start**, click **Run**, type `wf.msc`, and click **OK**.</span></span>  
  
3.  <span data-ttu-id="c3b3e-158">在“用户帐户控制”对话框中，单击“继续”使用管理员凭据打开高级安全 Windows 防火墙管理单元   。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-158">In the **User Account Control** dialog box, click **Continue** to use the Administrator credentials to open the Windows Firewall with Advanced Security snap-in.</span></span>  
  
4.  <span data-ttu-id="c3b3e-159">在 **“概述”** 页上，确认已启用 Windows 防火墙。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-159">On the **Overview** page, confirm that the Windows Firewall is enabled.</span></span>  
  
5.  <span data-ttu-id="c3b3e-160">在左窗格中，单击 **“入站规则”** 。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-160">In the left pane, click **Inbound Rules**.</span></span>  
  
6.  <span data-ttu-id="c3b3e-161">右键单击“入站规则”，然后单击“新建规则”以打开“新建入站规则向导”    。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-161">Right-click **Inbound Rules**, and then click **New Rule** to open the **New Inbound Rule Wizard**.</span></span>  
  
7.  <span data-ttu-id="c3b3e-162">可以为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 程序创建规则。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-162">You could create a rule for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] program.</span></span> <span data-ttu-id="c3b3e-163">但是，由于本示例使用固定端口，所以请选择 **“端口”** ，然后单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-163">However, because this example uses a fixed port, select **Port**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="c3b3e-164">在 **“协议和端口”** 页上，选择 **TCP**。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-164">On the **Protocols and Ports** page, select **TCP**.</span></span>  
  
9. <span data-ttu-id="c3b3e-165">选择 **“指定的本地端口”** 。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-165">Select **Specified local ports**.</span></span> <span data-ttu-id="c3b3e-166">键入端口号（由逗号分隔），然后单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-166">Type the port numbers separated by commas, and then click **Next**.</span></span> <span data-ttu-id="c3b3e-167">在本示例中，你将配置默认端口；因此请输入 `1433`。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-167">In this example, you will configure the default port; therefore, enter `1433`.</span></span>  
  
10. <span data-ttu-id="c3b3e-168">在 **“操作”** 页上，查看各选项。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-168">On the **Action** page, review the options.</span></span> <span data-ttu-id="c3b3e-169">在本示例中，不使用防火墙强制进行安全连接。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-169">In this example, you are not using the firewall to force secure connections.</span></span> <span data-ttu-id="c3b3e-170">因此，请单击 **“允许连接”** ，然后单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-170">Therefore, click **Allow the connection**, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c3b3e-171">您的环境可能要求使用安全连接。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-171">Your environment might require secure connections.</span></span> <span data-ttu-id="c3b3e-172">如果选择其中一个安全连接选项，则可能必须配置证书和 **“强行加密”** 选项。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-172">If you select one of the secure connections options, you might have to configure a certificate and the **Force Encryption** option.</span></span> <span data-ttu-id="c3b3e-173">有关安全连接的详细信息，请参阅[启用数据库引擎的加密连接（SQL Server 配置管理器）](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)和[启用数据库引擎的加密连接（SQL Server 配置管理器）](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-173">For more information about secure connections, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md) and [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).</span></span>  
  
11. <span data-ttu-id="c3b3e-174">在 **“配置文件”** 页上，为该规则选择一个或多个配置文件。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-174">On the **Profile** page, select one or more profiles for the rule.</span></span> <span data-ttu-id="c3b3e-175">如果您不熟悉防火墙配置文件，请单击防火墙程序中的 **“了解有关配置文件的详细信息”** 链接。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-175">If you are unfamiliar with firewall profiles, click the **Learn more about profiles** link in the firewall program.</span></span>  
  
    -   <span data-ttu-id="c3b3e-176">如果计算机是服务器而且仅当连接到域时才可用，则请选择 **“域”** ，然后单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-176">If the computer is a server and is available only when it is connected to a domain, select **Domain**, and then click **Next**.</span></span>  
  
    -   <span data-ttu-id="c3b3e-177">如果计算机为移动计算机（例如便携式计算机），则它在连接到不同网络时很可能使用多个配置文件。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-177">If the computer is a mobile computer (for example a laptop), it is likely to use multiple profiles when it connects to different networks.</span></span> <span data-ttu-id="c3b3e-178">对于移动计算机，可以为不同的配置文件配置不同的访问功能。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-178">For a mobile computer, you can configure different access capabilities for different profiles.</span></span> <span data-ttu-id="c3b3e-179">例如，可以在计算机使用域配置文件时允许访问，而在计算机使用公共配置文件时不允许访问。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-179">For example, you might allow access when the computer uses the Domain profile but not allow access when it uses the Public profile.</span></span>  
  
12. <span data-ttu-id="c3b3e-180">在 **“名称”** 页上，提供规则的名称和说明，然后单击 **“完成”** 。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-180">On the **Name** page, provide a name and description for the rule, and then click **Finish**.</span></span>  
  
13. <span data-ttu-id="c3b3e-181">重复此过程，为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将使用的每个 IP 地址创建另一个规则。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-181">Repeat this procedure to create another rule for each IP address that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will use.</span></span>  
  
 <span data-ttu-id="c3b3e-182">创建完一个或多个规则后，执行下列步骤以将计算机上的每个 IP 地址配置为使用规则。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-182">After you have created one or more rules, perform the following steps to configure each IP address on the computer to use a rule.</span></span>  
  
#### <a name="to-configure-the-firewall-rule-for-a-specific-ip-addresses"></a><span data-ttu-id="c3b3e-183">为特定的 IP 地址配置防火墙规则</span><span class="sxs-lookup"><span data-stu-id="c3b3e-183">To configure the firewall rule for a specific IP addresses</span></span>  
  
1.  <span data-ttu-id="c3b3e-184">在“高级安全 Windows 防火墙”的“入站规则”页上，右键单击刚创建的规则，然后单击“属性”    。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-184">On the **Inbound Rules** page of the **Windows Firewall with Advanced Security**, right-click the rule that you just created, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="c3b3e-185">在 **“规则属性”** 对话框中，选择 **“范围”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-185">In the **Rule Properties** dialog box, select the **Scope** tab.</span></span>  
  
3.  <span data-ttu-id="c3b3e-186">在 **“本地 IP 地址”** 区域中，选择 **“下列 IP 地址”** ，然后单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-186">In the **Local IP address** area, select **These IP addresses**, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="c3b3e-187">在 **“IP 地址”** 对话框中，选择 **“此 IP 地址或子网”** ，然后键入要配置的 IP 地址之一。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-187">In the **IP Address** dialog box, select **This IP address or subnet**, and then type one of the IP addresses that you want to configure.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="c3b3e-188">在 **“远程 IP 地址”** 区域中，选择 **“下列 IP 地址”** ，然后单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-188">In the **Remote IP address** area, select **These IP addresses**, and then click **Add**.</span></span>  
  
7.  <span data-ttu-id="c3b3e-189">使用 **“IP 地址”** 对话框为计算机上选定的 IP 地址配置连接。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-189">Use the **IP Address** dialog box to configure connectivity for the selected IP address on the computer.</span></span> <span data-ttu-id="c3b3e-190">可以启用源自特定 IP 地址、某些范围的 IP 地址、整个子网或源自特定计算机的连接。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-190">You can enable connections from specified IP addresses, ranges of IP addresses, whole subnets, or from certain computers.</span></span> <span data-ttu-id="c3b3e-191">若要正确配置此选项，您需要十分了解网络。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-191">To configure this option correctly, you must have a good understanding of the network.</span></span> <span data-ttu-id="c3b3e-192">有关网络的信息，请与网络管理员联系。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-192">For information about the network, see the network administrator.</span></span>  
  
8.  <span data-ttu-id="c3b3e-193">若要关闭 **“IP 地址”** 对话框，请单击 **“确定”** ；然后单击 **“确定”** 关闭 **“规则属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-193">To close the **IP Address** dialog box, click **OK**; and then click **OK** to close the **Rule Properties** dialog box.</span></span>  
  
9. <span data-ttu-id="c3b3e-194">若要配置多宿主计算机上的其他 IP 地址，请使用另一 IP 地址和另一规则重复此过程。</span><span class="sxs-lookup"><span data-stu-id="c3b3e-194">To configure the other IP addresses on a multi-homed computer, repeat this procedure by using another IP address and another rule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3b3e-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3b3e-195">See Also</span></span>  
 <span data-ttu-id="c3b3e-196">[SQL Server Browser 服务（数据库引擎和 SSAS）](../../database-engine/configure-windows/sql-server-browser-service-database-engine-and-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="c3b3e-196">[SQL Server Browser Service &#40;Database Engine and SSAS&#41;](../../database-engine/configure-windows/sql-server-browser-service-database-engine-and-ssas.md) </span></span>  
 [<span data-ttu-id="c3b3e-197">通过代理服务器连接到 SQL Server（SQL Server 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="c3b3e-197">Connect to SQL Server Through a Proxy Server &#40;SQL Server Configuration Manager&#41;</span></span>](../../relational-databases/sql-server-configuration-manager.md)  
  
  
