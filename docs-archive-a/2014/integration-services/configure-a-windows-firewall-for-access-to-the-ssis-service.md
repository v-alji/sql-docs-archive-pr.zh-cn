---
title: 为访问 SSIS 服务配置 Windows 防火墙 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- security [Integration Services], firewalls
- Windows Firewall [Integration Services]
- unauthorized access [Integration Services]
- Integration Services service, firewalls
- firewall systems [Integration Services]
- SQL Server Integration Services, firewalls
- SSIS, firewalls
ms.assetid: 39975cf2-c351-4205-8c39-27a0fadfb010
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d18b061ce16c88c50bbc08874efec455c28e15a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591490"
---
# <a name="configure-a-windows-firewall-for-access-to-the-ssis-service"></a><span data-ttu-id="b4b89-102">为访问 SSIS 服务配置 Windows 防火墙</span><span class="sxs-lookup"><span data-stu-id="b4b89-102">Configure a Windows Firewall for Access to the SSIS Service</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="b4b89-103">本主题论述 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务，该服务是用于管理 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包的一种 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="b4b89-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="b4b89-104">支持该服务以便与 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]的早期版本向后兼容。</span><span class="sxs-lookup"><span data-stu-id="b4b89-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="b4b89-105">从 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]开始，您可以在 Integration Services 服务器上管理诸如包之类的对象。</span><span class="sxs-lookup"><span data-stu-id="b4b89-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="b4b89-106">Windows 防火墙系统可帮助防止通过网络连接对计算机资源进行未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="b4b89-106">The windowsfirewall system helps prevent unauthorized access to computer resources over a network connection.</span></span> <span data-ttu-id="b4b89-107">若要通过此防火墙访问 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ，您必须将该防火墙配置为允许访问。</span><span class="sxs-lookup"><span data-stu-id="b4b89-107">To access [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] through this firewall, you have to configure the firewall to enable access.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b4b89-108">若要管理存储在某远程服务器上的包，您不必连接到该远程服务器上 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务的实例。</span><span class="sxs-lookup"><span data-stu-id="b4b89-108">To manage packages that are stored on a remote server, you do not have to connect to the instance of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service on that remote server.</span></span> <span data-ttu-id="b4b89-109">只需编辑 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务的配置文件，以便 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 显示存储在远程服务器上的包。</span><span class="sxs-lookup"><span data-stu-id="b4b89-109">Instead, edit the configuration file for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service so that [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] displays the packages that are stored on the remote server.</span></span> <span data-ttu-id="b4b89-110">有关详细信息，请参阅 [配置 Integration Services 服务（SSIS 服务）](configuring-the-integration-services-service-ssis-service.md)的早期版本向后兼容。</span><span class="sxs-lookup"><span data-stu-id="b4b89-110">For more information, see [Configuring the Integration Services Service &#40;SSIS Service&#41;](configuring-the-integration-services-service-ssis-service.md).</span></span>  
  
 <span data-ttu-id="b4b89-111">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务使用 DCOM 协议。</span><span class="sxs-lookup"><span data-stu-id="b4b89-111">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service uses the DCOM protocol.</span></span> <span data-ttu-id="b4b89-112">有关 DCOM 协议如何通过防火墙工作的详细信息，请参阅 "[使用分布式 COM With 防火墙](https://manualzz.com/doc/19762578/using-distributed-com-with-firewalls-by-michael-nelson-in...)" 一文。</span><span class="sxs-lookup"><span data-stu-id="b4b89-112">For more information about how the DCOM protocol works through firewalls, see the article, "[Using Distributed COM with Firewalls](https://manualzz.com/doc/19762578/using-distributed-com-with-firewalls-by-michael-nelson-in...)".</span></span>  
  
 <span data-ttu-id="b4b89-113">有很多可用的防火墙系统。</span><span class="sxs-lookup"><span data-stu-id="b4b89-113">There are many firewall systems available.</span></span> <span data-ttu-id="b4b89-114">如果您运行的防火墙不是 Windows 防火墙，请查阅您的防火墙文档来获取特定于您所使用的系统的信息。</span><span class="sxs-lookup"><span data-stu-id="b4b89-114">If you are running a firewall other than windowsfirewall, see your firewall documentation for information that is specific to the system you are using.</span></span>  
  
 <span data-ttu-id="b4b89-115">如果防火墙支持应用程序级筛选，则可以使用 Windows 提供的用户界面来指定允许通过该防火墙的例外项，如程序和服务。</span><span class="sxs-lookup"><span data-stu-id="b4b89-115">If the firewall supports application-level filtering, you can use the user interface that Windows provides to specify the exceptions that are allowed through the firewall, such as programs and services.</span></span> <span data-ttu-id="b4b89-116">否则，必须将 DCOM 配置为使用一组有限的 TCP 端口。</span><span class="sxs-lookup"><span data-stu-id="b4b89-116">Otherwise, you have to configure DCOM to use a limited set of TCP ports.</span></span> <span data-ttu-id="b4b89-117">上面提供的 Microsoft 网站链接包含有关如何指定要使用的 TCP 端口的信息。</span><span class="sxs-lookup"><span data-stu-id="b4b89-117">The Microsoft website link previously provided includes information about how to specify the TCP ports to use.</span></span>  
  
 <span data-ttu-id="b4b89-118">Integration Services 服务使用端口 135，该端口不能更改。</span><span class="sxs-lookup"><span data-stu-id="b4b89-118">The Integration Services service uses port 135, and the port cannot be changed.</span></span> <span data-ttu-id="b4b89-119">只有打开 TCP 端口 135 才能访问服务控制管理器 (SCM)。</span><span class="sxs-lookup"><span data-stu-id="b4b89-119">You have to open TCP port 135 for access to the service control manager (SCM).</span></span> <span data-ttu-id="b4b89-120">SCM 执行以下任务：启动和停止 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务，以及将控制请求传输到运行的服务。</span><span class="sxs-lookup"><span data-stu-id="b4b89-120">SCM performs tasks such as starting and stopping [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] services and transmitting control requests to the running service.</span></span>  
  
 <span data-ttu-id="b4b89-121">以下部分中的信息特定于 Windows 防火墙。</span><span class="sxs-lookup"><span data-stu-id="b4b89-121">The information in the following section is specific to windowsfirewall.</span></span> <span data-ttu-id="b4b89-122">您可以通过在命令提示符处运行命令或在“Windows 防火墙”对话框中设置属性来配置 Windows 防火墙系统。</span><span class="sxs-lookup"><span data-stu-id="b4b89-122">You can configure the windowsfirewall system by running a command at the command prompt, or by setting properties in the windowsfirewall dialog box.</span></span>  
  
 <span data-ttu-id="b4b89-123">有关默认 Windows 防火墙设置的详细信息以及有关影响数据库引擎、Analysis Services、Reporting Services 和 Integration Services 的 TCP 端口的说明，请参阅 [配置 Windows 防火墙以允许 SQL Server 访问](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="b4b89-123">For more information about the default windowsfirewall settings, and a description of the TCP ports that affect the Database Engine, Analysis Services, Reporting Services, and Integration Services, see [Configure the Windows Firewall to Allow SQL Server Access](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
## <a name="configuring-a-windowsfirewall"></a><span data-ttu-id="b4b89-124">配置 Windows 防火墙</span><span class="sxs-lookup"><span data-stu-id="b4b89-124">Configuring a windowsfirewall</span></span>  
 <span data-ttu-id="b4b89-125">您可以使用下面的命令来打开 TCP 端口 135、向例外列表中添加 MsDtsSrvr.exe 以及指定防火墙不阻止的范围。</span><span class="sxs-lookup"><span data-stu-id="b4b89-125">You can use the following commands to open TCP port 135, add MsDtsSrvr.exe to the exception list, and specify the scope of unblocking for the firewall.</span></span>  
  
#### <a name="to-configure-a-windowsfirewall-using-the-command-prompt-window"></a><span data-ttu-id="b4b89-126">使用命令提示符窗口配置 Windows 防火墙</span><span class="sxs-lookup"><span data-stu-id="b4b89-126">To configure a windowsfirewall using the Command Prompt window</span></span>  
  
1.  <span data-ttu-id="b4b89-127">运行命令 `netsh firewall add portopening protocol=TCP port=135 name="RPC (TCP/135)" mode=ENABLE scope=SUBNET`</span><span class="sxs-lookup"><span data-stu-id="b4b89-127">Run the command: `netsh firewall add portopening protocol=TCP port=135 name="RPC (TCP/135)" mode=ENABLE scope=SUBNET`</span></span>  
  
2.  <span data-ttu-id="b4b89-128">运行命令 `netsh firewall add allowedprogram program="%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn\MsDtsSrvr.exe" name="SSIS Service" scope=SUBNET`</span><span class="sxs-lookup"><span data-stu-id="b4b89-128">Run the command: `netsh firewall add allowedprogram program="%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn\MsDtsSrvr.exe" name="SSIS Service" scope=SUBNET`</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b4b89-129">若要打开所有计算机的防火墙，同时打开 Internet 上的计算机的防火墙，请用 scope=ALL 代替 scope=SUBNET。</span><span class="sxs-lookup"><span data-stu-id="b4b89-129">To open the firewall for all computers, and also for computers on the Internet, replace scope=SUBNET with scope=ALL.</span></span>  
  
 <span data-ttu-id="b4b89-130">下面的步骤描述了如何使用 Windows 用户界面来打开 TCP 端口 135，向例外列表中添加 MsDtsSrvr.exe 并指定防火墙不阻止的范围。</span><span class="sxs-lookup"><span data-stu-id="b4b89-130">The following procedure describes how to use the Windows user interface to open TCP port 135, add MsDtsSrvr.exe to the exception list, and specify the scope of unblocking for the firewall.</span></span>  
  
#### <a name="to-configure-a-firewall-using-the-windowsfirewall-dialog-box"></a><span data-ttu-id="b4b89-131">使用“Windows 防火墙”对话框配置防火墙</span><span class="sxs-lookup"><span data-stu-id="b4b89-131">To configure a firewall using the windowsfirewall dialog box</span></span>  
  
1.  <span data-ttu-id="b4b89-132">在“控制面板”中，双击“Windows 防火墙”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b4b89-132">In the Control Panel, double-click **Windows Firewall**.</span></span>  
  
2.  <span data-ttu-id="b4b89-133">在 **“Windows 防火墙”** 对话框中，单击 **“例外”** 选项卡，再单击 **“添加程序”**。</span><span class="sxs-lookup"><span data-stu-id="b4b89-133">In the **Windows Firewall** dialog box, click the **Exceptions** tab and then click **Add Program.**</span></span>  
  
3.  <span data-ttu-id="b4b89-134">在“添加程序”\*\*\*\* 对话框中单击“浏览”\*\*\*\*，导航到 Program Files\Microsoft SQL Server\100\DTS\Binn 文件夹，单击 MsDtsSrvr.exe，然后单击“打开”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b4b89-134">In the **Add a Program** dialog box, **click Browse**, navigate to the Program Files\Microsoft SQL Server\100\DTS\Binn folder, click MsDtsSrvr.exe, and then click **Open**.</span></span> <span data-ttu-id="b4b89-135">单击 **“确定”** 关闭 **“添加程序”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="b4b89-135">Click **OK** to close the **Add a Program** dialog box.</span></span>  
  
4.  <span data-ttu-id="b4b89-136">在 **“例外”** 选项卡上，单击 **“添加端口”**。</span><span class="sxs-lookup"><span data-stu-id="b4b89-136">On the **Exceptions** tab, click **Add Port.**</span></span>  
  
5.  <span data-ttu-id="b4b89-137">在“添加端口”\*\*\*\* 对话框中，键入 **RPC(TCP/135)** 或在“名称”\*\*\*\* 框中键入另一个描述性名称，在“端口号”\*\*\*\* 框中键入 **135**，然后选择“TCP”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b4b89-137">In the **Add a Port** dialog box, type **RPC(TCP/135)** or another descriptive name in the **Nam**e box, type **135** in the **Port Number** box, and then select **TCP**.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="b4b89-138">服务始终使用端口 135。</span><span class="sxs-lookup"><span data-stu-id="b4b89-138">service always uses port 135.</span></span> <span data-ttu-id="b4b89-139">您不能指定其他端口。</span><span class="sxs-lookup"><span data-stu-id="b4b89-139">You cannot specify a different port.</span></span>  
  
6.  <span data-ttu-id="b4b89-140">在 **“添加端口”** 对话框中，可以选择单击 **“更改范围”** 来修改默认的作用范围。</span><span class="sxs-lookup"><span data-stu-id="b4b89-140">In the **Add a Port** dialog box, you can optionally click **Change Scope** to modify the default scope.</span></span>  
  
7.  <span data-ttu-id="b4b89-141">在“更改范围”\*\*\*\* 对话框中，选择“我的网络（仅子网）”\*\*\*\* 或键入自定义列表，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b4b89-141">In the **Change Scope** dialog box, select **My network (subnet only)** or type a custom list, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="b4b89-142">若要关闭 **“添加端口”** 对话框，请单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="b4b89-142">To close the **Add a Port** dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="b4b89-143">若要关闭 **“Windows 防火墙”** 对话框，请单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="b4b89-143">To close the **Windows Firewall** dialog box, click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b4b89-144">为了配置 Windows 防火墙，此过程使用“控制面板”中的 **“Windows 防火墙”** 项。</span><span class="sxs-lookup"><span data-stu-id="b4b89-144">To configure the windowsfirewall, this procedure uses the **Windows Firewall** item in Control Panel.</span></span> <span data-ttu-id="b4b89-145">**“Windows 防火墙”** 项仅可为当前网络位置配置文件配置防火墙。</span><span class="sxs-lookup"><span data-stu-id="b4b89-145">The **Windows Firewall** item only configures the firewall for the current network location profile.</span></span> <span data-ttu-id="b4b89-146">但你也可使用 **netsh** 命令行工具或名为高级安全 Windows 防火墙的 [!INCLUDE[msCoName](../includes/msconame-md.md)] 管理控制台 (MMC) 管理单元来配置 Windows 防火墙。</span><span class="sxs-lookup"><span data-stu-id="b4b89-146">However, you can also configure the windowsfirewall by using the **netsh** command line tool or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console (MMC) snap-in named windowsfirewall with Advanced Security.</span></span> <span data-ttu-id="b4b89-147">有关这些工具的详细信息，请参阅 [配置 Windows 防火墙以允许 SQL Server 访问](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="b4b89-147">For more information about these tools, see [Configure the Windows Firewall to Allow SQL Server Access](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b89-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4b89-148">See Also</span></span>  
 <span data-ttu-id="b4b89-149">[&#40;SSIS 服务配置 Integration Services 服务&#41;](service/integration-services-service-ssis-service.md) </span><span class="sxs-lookup"><span data-stu-id="b4b89-149">[Configuring the Integration Services Service &#40;SSIS Service&#41;](service/integration-services-service-ssis-service.md) </span></span>  
 [<span data-ttu-id="b4b89-150">Integration Services 服务（SSIS 服务）</span><span class="sxs-lookup"><span data-stu-id="b4b89-150">Integration Services Service &#40;SSIS Service&#41;</span></span>](service/integration-services-service-ssis-service.md)  
  
  
