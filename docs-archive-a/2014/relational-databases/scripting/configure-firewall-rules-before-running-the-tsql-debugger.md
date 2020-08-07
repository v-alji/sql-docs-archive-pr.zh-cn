---
title: 配置 Transact-SQL 调试器
ms.custom: seo-lt-2019
ms.date: 10/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- vs.debug.error.sqlde_register_failed
- vs.debug.error.sqlde_accessdenied
- vs.debug.error.sqlde_firewall.remotemachines
helpviewer_keywords:
- Transact-SQL debugger, remote connections
- Windows Firewall [Database Engine], Transact-SQL debugger
- Transact-SQL debugger, Windows Firewall
- Transact-SQL debugger, configuring
- ports [SQL Server], Transact-SQL debugger
- TCP/IP [SQL Server], port numbers
ms.assetid: f50e0b0d-eaf0-4f4a-be83-96f5be63e7ea
author: rothja
ms.author: jroth
ms.openlocfilehash: a320e77e86c933a33d96d708580d5050b0c06de2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589510"
---
# <a name="configure-the-transact-sql-debugger"></a><span data-ttu-id="adde5-102">配置 Transact-SQL 调试器</span><span class="sxs-lookup"><span data-stu-id="adde5-102">Configure the Transact-SQL Debugger</span></span>
  <span data-ttu-id="adde5-103">必须配置 Windows 防火墙规则，以便在连接到 [!INCLUDE[tsql](../../includes/tsql-md.md)] 实例（运行该实例的计算机不同于运行 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器的计算机）时启用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 调试。</span><span class="sxs-lookup"><span data-stu-id="adde5-103">Windows Firewall rules must be configured to enable [!INCLUDE[tsql](../../includes/tsql-md.md)] debugging when connected to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that is running on a different computer than the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
## <a name="configuring-the-transact-sql-debugger"></a><span data-ttu-id="adde5-104">配置 Transact-SQL 调试器</span><span class="sxs-lookup"><span data-stu-id="adde5-104">Configuring the Transact-SQL Debugger</span></span>  
 <span data-ttu-id="adde5-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器包括服务器端和客户端组件。</span><span class="sxs-lookup"><span data-stu-id="adde5-105">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger includes both server-side and client-side components.</span></span> <span data-ttu-id="adde5-106">服务器端调试器组件与 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 (SP2) 或更高版本中的每个数据库引擎实例一起安装。</span><span class="sxs-lookup"><span data-stu-id="adde5-106">The server-side debugger components are installed with each instance of the Database Engine from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 (SP2) or later.</span></span> <span data-ttu-id="adde5-107">包括客户端调试器组件：</span><span class="sxs-lookup"><span data-stu-id="adde5-107">The client-side debugger components are included:</span></span>  
  
-   <span data-ttu-id="adde5-108">在从 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 或更高版本安装客户端工具时。</span><span class="sxs-lookup"><span data-stu-id="adde5-108">When you install the client-side tools from [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later.</span></span>  
  
-   <span data-ttu-id="adde5-109">在安装 Microsoft Visual Studio 2010 或更高版本时。</span><span class="sxs-lookup"><span data-stu-id="adde5-109">When you install Microsoft Visual Studio 2010 or later.</span></span>  
  
-   <span data-ttu-id="adde5-110">在从 Web 下载安装 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 时。</span><span class="sxs-lookup"><span data-stu-id="adde5-110">When you install [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] from the web download.</span></span>  
  
 <span data-ttu-id="adde5-111">如果 [!INCLUDE[tsql](../../includes/tsql-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 与 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 实例在同一台计算机上运行，则对于运行 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]调试器没有配置要求。</span><span class="sxs-lookup"><span data-stu-id="adde5-111">There are no configuration requirements to run the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger when [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] is running on the same computer as the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="adde5-112">但是，要在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的远程实例时运行此调试器，必须在两台计算机上的 Windows 防火墙中启用程序和端口规则。</span><span class="sxs-lookup"><span data-stu-id="adde5-112">However, to run the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger when connected to a remote instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], program and port rules in the Windows Firewall must be enabled on both computers.</span></span> <span data-ttu-id="adde5-113">这些规则可通过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序创建。</span><span class="sxs-lookup"><span data-stu-id="adde5-113">These rules may be created by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup.</span></span> <span data-ttu-id="adde5-114">如果您在尝试打开远程调试会话时系统显示错误，则请确保在您的计算机上定义以下防火墙规则。</span><span class="sxs-lookup"><span data-stu-id="adde5-114">If you get errors attempting to open a remote debugging session, ensure the following firewall rules are defined on your computer.</span></span>  
  
 <span data-ttu-id="adde5-115">使用 **“高级安全 Windows 防火墙”** 应用程序管理防火墙规则。</span><span class="sxs-lookup"><span data-stu-id="adde5-115">Use the **Windows Firewall with Advanced Security** application to manage the firewall rules.</span></span> <span data-ttu-id="adde5-116">在 [!INCLUDE[win7](../../includes/win7-md.md)] 和 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]中，打开 **“控制面板”**，打开 **“Windows 防火墙”**，然后选择 **“高级设置”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-116">In both [!INCLUDE[win7](../../includes/win7-md.md)] and [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)], open **Control Panel**, open **Windows Firewall**, and select **Advanced settings**.</span></span> <span data-ttu-id="adde5-117">在 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 中，您还可以打开 **“服务管理器”**，在左侧的窗格中展开 **“配置”** ，然后展开 **“高级安全 Windows 防火墙”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-117">In [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] you can also open **Service Manager**, expand **Configuration** in the left pane, and expand **Windows Firewall with Advanced Security**.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="adde5-118">在“Windows 防火墙”中启用规则可能会导致您的计算机暴露在防火墙在设计上可以阻止的安全风险之中。</span><span class="sxs-lookup"><span data-stu-id="adde5-118">Enabling rules in the Windows Firewall may expose your computer to security threats that the firewall is designed to block.</span></span> <span data-ttu-id="adde5-119">为远程调试启用规则将取消阻止在本主题中列出的端口和程序。</span><span class="sxs-lookup"><span data-stu-id="adde5-119">Enabling rules for remote debugging unblocks the ports and programs listed in this topic.</span></span>  
  
## <a name="firewall-rules-on-the-server"></a><span data-ttu-id="adde5-120">服务器上的防火墙规则</span><span class="sxs-lookup"><span data-stu-id="adde5-120">Firewall Rules on the Server</span></span>  
 <span data-ttu-id="adde5-121">在运行 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例的计算机上，使用 **“高级安全 Windows 防火墙”** 可以指定以下信息：</span><span class="sxs-lookup"><span data-stu-id="adde5-121">On the computer that is running the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], use **Windows Firewall with Advanced Security** to specify the following information:</span></span>  
  
-   <span data-ttu-id="adde5-122">为 sqlservr.exe 添加入站程序规则。</span><span class="sxs-lookup"><span data-stu-id="adde5-122">Add an inbound program rule for sqlservr.exe.</span></span> <span data-ttu-id="adde5-123">对于需要支持远程调试会话的每个实例，您必须具有一个规则。</span><span class="sxs-lookup"><span data-stu-id="adde5-123">You must have a rule for each instance that needs to support remote debugging sessions.</span></span>  
  
    1.  <span data-ttu-id="adde5-124">在“高级安全 Windows 防火墙”\*\*\*\* 的左窗格中，右键单击“入站规则”\*\*\*\*，然后在操作窗格中选择“新建规则”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="adde5-124">In **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then select **New Rule** in the action pane.</span></span>  
  
    2.  <span data-ttu-id="adde5-125">在 **“规则类型”** 对话框中，选择 **“程序”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-125">In the **Rule Type** dialog, select **Program**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="adde5-126">在 **“程序”** 对话框中，选择 **“此程序路径:”** ，然后输入指向此实例的 sqlservr.exe 的完整路径。</span><span class="sxs-lookup"><span data-stu-id="adde5-126">In the **Program** dialog, select **This program path:** and enter the full path to sqlservr.exe for this instance.</span></span> <span data-ttu-id="adde5-127">默认情况下，sqlservr.exe 安装在 C:\Program Files\Microsoft SQL Server\MSSQL12. 中。*Instancename*\MSSQL\Binn，其中*instancename*为默认实例的 MSSQLSERVER，以及任何命名实例的实例名称。</span><span class="sxs-lookup"><span data-stu-id="adde5-127">By default, sqlservr.exe is installed in C:\Program Files\Microsoft SQL Server\MSSQL12.*InstanceName*\MSSQL\Binn, where *InstanceName* is MSSQLSERVER for the default instance, and the instance name for any named instance.</span></span>  
  
    4.  <span data-ttu-id="adde5-128">在 **“操作”** 对话框中，选择 **“允许连接”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-128">In the **Action** dialog, select **Allow the connection**, and click **Next**.</span></span>  
  
    5.  <span data-ttu-id="adde5-129">在 **“配置文件”** 对话框中，选择在您想要打开针对该实例的调试会话时描述计算机连接环境的任何配置文件，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-129">In the **Profile** dialog, select any profiles that describe the computer connection environment when you want to open a debugging session with the instance, and click **Next**.</span></span>  
  
    6.  <span data-ttu-id="adde5-130">在 **“名称”** 对话框中，键入针对此规则的名称和说明，然后单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-130">In the **Name** dialog, type a name and description for this rule and click **Finish**.</span></span>  
  
    7.  <span data-ttu-id="adde5-131">在 **“入站规则”** 列表中，右键单击您创建的规则，然后在操作窗格中选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="adde5-131">In the **Inbound Rules** list, right click the rule you created, and then select **Properties** in the action pane.</span></span>  
  
    8.  <span data-ttu-id="adde5-132">选择 **“协议和端口”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="adde5-132">Select the **Protocols and Ports** tab.</span></span>  
  
    9. <span data-ttu-id="adde5-133">在 **“协议类型:”** 框中选择 **“TCP”** ，在 **“本地端口:”** 框中选择 **“RPC 动态端口”** ，单击 **“应用”**，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-133">Select **TCP** in the **Protocol type:** box, select **RPC Dynamic Ports** in the **Local port:** box, click **Apply**, and then click **OK**.</span></span>  
  
-   <span data-ttu-id="adde5-134">添加针对 svchost.exe 的入站程序规则，以便启用从远程调试器会话的 DCOM 通信。</span><span class="sxs-lookup"><span data-stu-id="adde5-134">Add an inbound program rule for svchost.exe to enable DCOM communications from remote debugger sessions.</span></span>  
  
    1.  <span data-ttu-id="adde5-135">在“高级安全 Windows 防火墙”\*\*\*\* 的左窗格中，右键单击“入站规则”\*\*\*\*，然后在操作窗格中选择“新建规则”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="adde5-135">In **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then select **New Rule** in the action pane.</span></span>  
  
    2.  <span data-ttu-id="adde5-136">在 **“规则类型”** 对话框中，选择 **“程序”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-136">In the **Rule Type** dialog, select **Program**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="adde5-137">在 **“程序”** 对话框中，选择 **“此程序路径:”** ，然后输入指向 svchost.exe 的完整路径。</span><span class="sxs-lookup"><span data-stu-id="adde5-137">In the **Program** dialog, select **This program path:** and enter the full path to svchost.exe.</span></span> <span data-ttu-id="adde5-138">默认情况下，svchost.exe 安装在 %systemroot%\System32\svchost.exe 中。</span><span class="sxs-lookup"><span data-stu-id="adde5-138">By default, svchost.exe is installed in %systemroot%\System32\svchost.exe.</span></span>  
  
    4.  <span data-ttu-id="adde5-139">在 **“操作”** 对话框中，选择 **“允许连接”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-139">In the **Action** dialog, select **Allow the connection**, and click **Next**.</span></span>  
  
    5.  <span data-ttu-id="adde5-140">在 **“配置文件”** 对话框中，选择在您想要打开针对该实例的调试会话时描述计算机连接环境的任何配置文件，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-140">In the **Profile** dialog, select any profiles that describe the computer connection environment when you want to open a debugging session with the instance, and click **Next**.</span></span>  
  
    6.  <span data-ttu-id="adde5-141">在 **“名称”** 对话框中，键入针对此规则的名称和说明，然后单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-141">In the **Name** dialog, type a name and description for this rule and click **Finish**.</span></span>  
  
    7.  <span data-ttu-id="adde5-142">在 **“入站规则”** 列表中，右键单击您创建的规则，然后在操作窗格中选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="adde5-142">In the **Inbound Rules** list, right click the rule you created, and then select **Properties** in the action pane.</span></span>  
  
    8.  <span data-ttu-id="adde5-143">选择 **“协议和端口”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="adde5-143">Select the **Protocols and Ports** tab.</span></span>  
  
    9. <span data-ttu-id="adde5-144">在 **“协议类型:”** 框中选择 **“TCP”** ，在 **“本地端口:”** 框中选择 **“RPC 端点映射程序”** ，单击 **“应用”**，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-144">Select **TCP** in the **Protocol type:** box, select **RPC Endpoint Mapper** in the **Local port:** box, click **Apply**, and then click **OK**.</span></span>  
  
-   <span data-ttu-id="adde5-145">如果域策略要求通过 IPSec 进行网络通信，还必须添加打开 UDP 端口 4500 和 UDP 端口 500 的入站规则。</span><span class="sxs-lookup"><span data-stu-id="adde5-145">If the domain policy requires network communications to be done through IPsec, you must also add inbound rules opening UDP port 4500 and UDP port 500.</span></span>  
  
## <a name="firewall-rules-on-the-client"></a><span data-ttu-id="adde5-146">客户端上的防火墙规则</span><span class="sxs-lookup"><span data-stu-id="adde5-146">Firewall Rules on the Client</span></span>  
 <span data-ttu-id="adde5-147">在正运行 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器的计算机上，SQL Server 安装程序或 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 安装程序可能已将 Windows 防火墙配置为允许远程调试。</span><span class="sxs-lookup"><span data-stu-id="adde5-147">On the computer that is running the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor, the SQL Server setup or [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] setup may have configured the Windows Firewall to allow remote debugging.</span></span>  
  
 <span data-ttu-id="adde5-148">如果您在尝试打开远程调试会话时系统显示错误，则可以通过使用 **“高级安全 Windows 防火墙”** 配置防火墙规则来手动配置程序和端口例外：</span><span class="sxs-lookup"><span data-stu-id="adde5-148">If you get errors attempting to open a remote debugging session, you can manually configure the program and port exceptions by using **Windows Firewall with Advanced Security** to configure firewall rules:</span></span>  
  
-   <span data-ttu-id="adde5-149">为 svchost 添加程序条目:</span><span class="sxs-lookup"><span data-stu-id="adde5-149">Add a program entry for svchost:</span></span>  
  
    1.  <span data-ttu-id="adde5-150">在“高级安全 Windows 防火墙”\*\*\*\* 的左窗格中，右键单击“入站规则”\*\*\*\*，然后在操作窗格中选择“新建规则”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="adde5-150">In **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then select **New Rule** in the action pane.</span></span>  
  
    2.  <span data-ttu-id="adde5-151">在 **“规则类型”** 对话框中，选择 **“程序”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-151">In the **Rule Type** dialog, select **Program**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="adde5-152">在 **“程序”** 对话框中，选择 **“此程序路径:”** ，然后输入指向 svchost.exe 的完整路径。</span><span class="sxs-lookup"><span data-stu-id="adde5-152">In the **Program** dialog, select **This program path:** and enter the full path to svchost.exe.</span></span> <span data-ttu-id="adde5-153">默认情况下，svchost.exe 安装在 %systemroot%\System32\svchost.exe 中。</span><span class="sxs-lookup"><span data-stu-id="adde5-153">By default, svchost.exe is installed in %systemroot%\System32\svchost.exe.</span></span>  
  
    4.  <span data-ttu-id="adde5-154">在 **“操作”** 对话框中，选择 **“允许连接”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-154">In the **Action** dialog, select **Allow the connection**, and click **Next**.</span></span>  
  
    5.  <span data-ttu-id="adde5-155">在 **“配置文件”** 对话框中，选择在您想要打开针对该实例的调试会话时描述计算机连接环境的任何配置文件，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-155">In the **Profile** dialog, select any profiles that describe the computer connection environment when you want to open a debugging session with the instance, and click **Next**.</span></span>  
  
    6.  <span data-ttu-id="adde5-156">在 **“名称”** 对话框中，键入针对此规则的名称和说明，然后单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-156">In the **Name** dialog, type a name and description for this rule and click **Finish**.</span></span>  
  
    7.  <span data-ttu-id="adde5-157">在 **“入站规则”** 列表中，右键单击您创建的规则，然后在操作窗格中选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="adde5-157">In the **Inbound Rules** list, right click the rule you created, and then select **Properties** in the action pane.</span></span>  
  
    8.  <span data-ttu-id="adde5-158">选择 **“协议和端口”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="adde5-158">Select the **Protocols and Ports** tab.</span></span>  
  
    9. <span data-ttu-id="adde5-159">在 **“协议类型:”** 框中选择 **“TCP”** ，在 **“本地端口:”** 框中选择 **“RPC 端点映射程序”** ，单击 **“应用”**，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-159">Select **TCP** in the **Protocol type:** box, select **RPC Endpoint Mapper** in the **Local port:** box, click **Apply**, and then click **OK**.</span></span>  
  
-   <span data-ttu-id="adde5-160">为承载 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器的应用程序添加程序条目。</span><span class="sxs-lookup"><span data-stu-id="adde5-160">Add a program entry for the application hosting the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span> <span data-ttu-id="adde5-161">如果您需要在同一台计算机上从 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 都打开远程调试会话，则必须为这两者都添加一个程序规则：</span><span class="sxs-lookup"><span data-stu-id="adde5-161">If you need to open remote debugging sessions from both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] on the same computer, you must add a program rule for both:</span></span>  
  
    1.  <span data-ttu-id="adde5-162">在“高级安全 Windows 防火墙”\*\*\*\* 的左窗格中，右键单击“入站规则”\*\*\*\*，然后在操作窗格中选择“新建规则”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="adde5-162">In **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then select **New Rule** in the action pane.</span></span>  
  
    2.  <span data-ttu-id="adde5-163">在 **“规则类型”** 对话框中，选择 **“程序”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-163">In the **Rule Type** dialog, select **Program**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="adde5-164">在 **“程序”** 对话框中，选择 **“此程序路径:”** ，然后输入以下三个值之一。</span><span class="sxs-lookup"><span data-stu-id="adde5-164">In the **Program** dialog, select **This program path:** and enter one of these three values.</span></span>  
  
        -   <span data-ttu-id="adde5-165">对于 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，输入指向 ssms.exe 的完整路径。</span><span class="sxs-lookup"><span data-stu-id="adde5-165">For [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], enter the full path to ssms.exe.</span></span> <span data-ttu-id="adde5-166">默认情况下，ssms.exe 安装在 C:\Program Files (x86)\Microsoft SQL Server\120\Tools\Binn\Management Studio 下。</span><span class="sxs-lookup"><span data-stu-id="adde5-166">By default, ssms.exe is installed in C:\Program Files (x86)\Microsoft SQL Server\120\Tools\Binn\Management Studio.</span></span>  
  
        -   <span data-ttu-id="adde5-167">对于 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] ，输入指向 devenv.exe 的完整路径：</span><span class="sxs-lookup"><span data-stu-id="adde5-167">For [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] enter the full path to devenv.exe:</span></span>  
  
            1.  <span data-ttu-id="adde5-168">默认情况下，针对 Visual Studio 2010 的 devenv.exe 位于 C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE 中。</span><span class="sxs-lookup"><span data-stu-id="adde5-168">By default, the devenv.exe for Visual Studio 2010 is in C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE.</span></span>  
  
            2.  <span data-ttu-id="adde5-169">默认情况下，针对 Visual Studio 2012 的 devenv.exe 位于 C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE 中。</span><span class="sxs-lookup"><span data-stu-id="adde5-169">By default, the devenv.exe for Visual Studio 2012 is in C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE</span></span>  
  
            3.  <span data-ttu-id="adde5-170">您可以从用来启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的快捷方式中找到指向 ssms.exe 的路径。</span><span class="sxs-lookup"><span data-stu-id="adde5-170">You can find the path to ssms.exe from the shortcut you use to launch [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="adde5-171">您可以从用来启动 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]的快捷方式中找到指向 devenv.exe 的路径。</span><span class="sxs-lookup"><span data-stu-id="adde5-171">You can find the path to devenv.exe from the shortcut you use to launch [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="adde5-172">右键单击该快捷方式并选择 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-172">Right click the shortcut and select **Properties**.</span></span> <span data-ttu-id="adde5-173">可执行文件和路径将在 **“目标”** 框中列出。</span><span class="sxs-lookup"><span data-stu-id="adde5-173">The executable and path are listed in the **Target** box.</span></span>  
  
    4.  <span data-ttu-id="adde5-174">在 **“操作”** 对话框中，选择 **“允许连接”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-174">In the **Action** dialog, select **Allow the connection**, and click **Next**.</span></span>  
  
    5.  <span data-ttu-id="adde5-175">在 **“配置文件”** 对话框中，选择在您想要打开针对该实例的调试会话时描述计算机连接环境的任何配置文件，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-175">In the **Profile** dialog, select any profiles that describe the computer connection environment when you want to open a debugging session with the instance, and click **Next**.</span></span>  
  
    6.  <span data-ttu-id="adde5-176">在 **“名称”** 对话框中，键入针对此规则的名称和说明，然后单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-176">In the **Name** dialog, type a name and description for this rule and click **Finish**.</span></span>  
  
    7.  <span data-ttu-id="adde5-177">在 **“入站规则”** 列表中，右键单击您创建的规则，然后在操作窗格中选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="adde5-177">In the **Inbound Rules** list, right click the rule you created, and then select **Properties** in the action pane.</span></span>  
  
    8.  <span data-ttu-id="adde5-178">选择 **“协议和端口”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="adde5-178">Select the **Protocols and Ports** tab.</span></span>  
  
    9. <span data-ttu-id="adde5-179">在 **“协议类型:”** 框中选择 **“TCP”** ，在 **“本地端口:”** 框中选择 **“RPC 动态端口”** ，单击 **“应用”**，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="adde5-179">Select **TCP** in the **Protocol type:** box, select **RPC Dynamic Ports** in the **Local port:** box, click **Apply**, and then click **OK**.</span></span>  
  
## <a name="requirements-for-starting-the-debugger"></a><span data-ttu-id="adde5-180">启动调试器的要求</span><span class="sxs-lookup"><span data-stu-id="adde5-180">Requirements for Starting the Debugger</span></span>  
 <span data-ttu-id="adde5-181">启动 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器的所有尝试还必须满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="adde5-181">All attempts to start the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger must also meet the following requirements:</span></span>  
  
* [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="adde5-182">或 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 必须在作为 sysadmin 固定服务器角色成员的 Windows 帐户下运行。</span><span class="sxs-lookup"><span data-stu-id="adde5-182">or [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] must be running under a Windows account that is a member of the sysadmin fixed server roll.</span></span>  
  
* <span data-ttu-id="adde5-183">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器窗口必须使用 Windows 身份验证来连接，或使用作为 sysadmin 固定服务器角色成员的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证登录名来连接。</span><span class="sxs-lookup"><span data-stu-id="adde5-183">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window must be connected by using either a Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication login that is a member of the sysadmin fixed server role.</span></span>  
  
* <span data-ttu-id="adde5-184">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器窗口必须从 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Service Pack 2 (SP2) 或更高版本连接到 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="adde5-184">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window must be connected to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 (SP2) or later.</span></span> <span data-ttu-id="adde5-185">如果查询编辑器窗口连接到处于单用户模式下的实例，您将无法运行调试器。</span><span class="sxs-lookup"><span data-stu-id="adde5-185">You cannot run the debugger when the Query Editor window is connected to an instance that is in single-user mode.</span></span>

* <span data-ttu-id="adde5-186">服务器需要通过 RPC 回复客户端通信。</span><span class="sxs-lookup"><span data-stu-id="adde5-186">The server needs to communicate back to the client via RPC.</span></span> <span data-ttu-id="adde5-187">运行 SQL Server 服务的帐户应具有对客户端的身份验证权限。</span><span class="sxs-lookup"><span data-stu-id="adde5-187">The account under which SQL Server service is running should have authenticate permissions to the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adde5-188">另请参阅</span><span class="sxs-lookup"><span data-stu-id="adde5-188">See Also</span></span>  
 <span data-ttu-id="adde5-189">[Transact-sql 调试器](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="adde5-189">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="adde5-190">[运行 Transact-sql 调试器](run-the-transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="adde5-190">[Run the Transact-SQL Debugger](run-the-transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="adde5-191">[单步执行 Transact-sql 代码](step-through-transact-sql-code.md) </span><span class="sxs-lookup"><span data-stu-id="adde5-191">[Step Through Transact-SQL Code](step-through-transact-sql-code.md) </span></span>  
 <span data-ttu-id="adde5-192">[Transact-sql 调试器信息](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="adde5-192">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 [<span data-ttu-id="adde5-193">数据库引擎查询编辑器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="adde5-193">Database Engine Query Editor &#40;SQL Server Management Studio&#41;</span></span>](database-engine-query-editor-sql-server-management-studio.md)  
  
  
