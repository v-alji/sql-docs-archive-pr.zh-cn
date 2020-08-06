---
title: 启动、停止、暂停、继续、重新启动数据库引擎、SQL Server 代理或 SQL Server Browser 服务 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Configuration Manager, start and stop services
- stopping SQL Server Agent
- parameters [SQL Server], startup options
- SQL Server, startup options
- Database Engine [SQL Server], starting and stopping services
- pausing SQL Server
- PowerShell [SQL Server], starting and stopping services
- single-user mode [SQL Server], starting in
- SQL Server Management Studio [SQL Server], starting or stopping services
- stopping SQL Server Browser service
- starting SQL Server Agent
- default instances [SQL Server], starting and stopping
- SQL Server Agent, starting and stopping
- command prompt [SQL Server], starting and stopping SQL Server services
- continuing SQL Server
- starting SQL Server Database Engine
- net stop commands [SQL Server]
- command prompt [SQL Server], SQL Browser service
- Configuration Manager, start and stop services
- resuming SQL Server
- startup options [SQL Server]
- named instances [SQL Server], starting and stopping
- net start commands [SQL Server]
- SQL Server, starting and stopping
- stopping SQL Server
- starting SQL Server Browser service
- SQL Server Database Engine setting startup options
- administering SQL Server, starting and stopping services
- Management Studio [SQL Server], starting or stopping services
ms.assetid: 32660a02-e5a1-411a-9e57-7066ca459df6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f4b102c8fd81923d7386c8e556896e715311a07e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692511"
---
# <a name="start-stop-pause-resume-restart-the-database-engine-sql-server-agent-or-sql-server-browser-service"></a><span data-ttu-id="6d720-102">启动、停止、暂停、继续、重新启动数据库引擎、SQL Server 代理或 SQL Server Browser 服务</span><span class="sxs-lookup"><span data-stu-id="6d720-102">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>
  <span data-ttu-id="6d720-103">本主题介绍如何 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、命令提示符、或 PowerShell 中的**net**命令 [!INCLUDE[tsql](../../includes/tsql-md.md)] 来启动、停止、暂停、恢复或重新启动、代理或 Browser 服务。</span><span class="sxs-lookup"><span data-stu-id="6d720-103">This topic describes how to start, stop, pause, resume, or restart the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], **net** commands from a command prompt, [!INCLUDE[tsql](../../includes/tsql-md.md)], or PowerShell.</span></span>  
  
-   <span data-ttu-id="6d720-104">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="6d720-104">**Before you begin:**</span></span>  
  
    -   [<span data-ttu-id="6d720-105">这些服务是什么？</span><span class="sxs-lookup"><span data-stu-id="6d720-105">What are these services?</span></span>](#Services)  
  
    -   [<span data-ttu-id="6d720-106">其他信息</span><span class="sxs-lookup"><span data-stu-id="6d720-106">Additional Information</span></span>](#MoreInformation)  
  
    -   [<span data-ttu-id="6d720-107">安全性</span><span class="sxs-lookup"><span data-stu-id="6d720-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6d720-108">**相关说明：**</span><span class="sxs-lookup"><span data-stu-id="6d720-108">**Instructions using:**</span></span>  
  
    -   [<span data-ttu-id="6d720-109">SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="6d720-109">SQL Server Configuration Manager</span></span>](#SSCMProcedure)  
  
    -   [<span data-ttu-id="6d720-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6d720-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
    -   [<span data-ttu-id="6d720-111">命令提示符窗口中的 net 命令</span><span class="sxs-lookup"><span data-stu-id="6d720-111">net Commands from a Command Prompt window</span></span>](#CommandPrompt)  
  
    -   [<span data-ttu-id="6d720-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6d720-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
    -   [<span data-ttu-id="6d720-113">PowerShell</span><span class="sxs-lookup"><span data-stu-id="6d720-113">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6d720-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="6d720-114">Before You Begin</span></span>  
  
###  <a name="what-is-the-ssdenoversion-service-the-ssnoversion-agent-service-and-the-ssnoversion-browser-service"></a><a name="Services"></a> <span data-ttu-id="6d720-115">什么是 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 服务、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务？</span><span class="sxs-lookup"><span data-stu-id="6d720-115">What is the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service, and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service?</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6d720-116">组件是作为 Windows 服务运行的可执行程序。</span><span class="sxs-lookup"><span data-stu-id="6d720-116">components are executable programs that run as a Windows service.</span></span> <span data-ttu-id="6d720-117">作为 Windows 服务运行的程序可以继续运行，而不在计算机屏幕上显示任何活动。</span><span class="sxs-lookup"><span data-stu-id="6d720-117">Programs that run as a Windows service can continue to operate without displaying any activity on the computer screen.</span></span>  
  
 <span data-ttu-id="6d720-118">**[!INCLUDE[ssDE](../../includes/ssde-md.md)]服务**</span><span class="sxs-lookup"><span data-stu-id="6d720-118">**[!INCLUDE[ssDE](../../includes/ssde-md.md)] service**</span></span>  
 <span data-ttu-id="6d720-119">作为 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的可执行进程。</span><span class="sxs-lookup"><span data-stu-id="6d720-119">The executable process that is the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="6d720-120">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 可以是默认实例（每台计算机只有一个），也可以是多个 [!INCLUDE[ssDE](../../includes/ssde-md.md)]命名实例中的一个。</span><span class="sxs-lookup"><span data-stu-id="6d720-120">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] can be the default instance (limit one per computer), or can be one of many named instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="6d720-121">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器确定在计算机上安装哪些 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="6d720-121">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to determine which instances of [!INCLUDE[ssDE](../../includes/ssde-md.md)] are installed on the computer.</span></span> <span data-ttu-id="6d720-122">如果安装此实例，则默认实例 () 列为\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) \*\*。</span><span class="sxs-lookup"><span data-stu-id="6d720-122">The default instance (if you install it) is listed as **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER)**.</span></span> <span data-ttu-id="6d720-123">如果你安装了命名实例，则这些 (实例将) 列为\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ( # B0 instance_name>) \*\*。</span><span class="sxs-lookup"><span data-stu-id="6d720-123">Named instances (if you install them) are listed as **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (<instance_name>)**.</span></span> <span data-ttu-id="6d720-124">默认情况下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 安装为\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLEXPRESS) \*\*。</span><span class="sxs-lookup"><span data-stu-id="6d720-124">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express is installed as **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLEXPRESS)**.</span></span>  
  
 <span data-ttu-id="6d720-125">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]代理服务**</span><span class="sxs-lookup"><span data-stu-id="6d720-125">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service**</span></span>  
 <span data-ttu-id="6d720-126">一种 Windows 服务，可执行计划的管理任务（称为作业和警报）。</span><span class="sxs-lookup"><span data-stu-id="6d720-126">A Windows service that executes scheduled administrative tasks, which are called jobs and alerts.</span></span> <span data-ttu-id="6d720-127">有关详细信息，请参阅 [SQL Server Agent](../../ssms/agent/sql-server-agent.md)。</span><span class="sxs-lookup"><span data-stu-id="6d720-127">For more information, see [SQL Server Agent](../../ssms/agent/sql-server-agent.md).</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6d720-128">都提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6d720-128">Agent is not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6d720-129">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="6d720-129">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="6d720-130">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Browser 服务**</span><span class="sxs-lookup"><span data-stu-id="6d720-130">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service**</span></span>  
 <span data-ttu-id="6d720-131">一种 Windows 服务，可侦听对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 资源的传入请求并为客户端提供有关计算机中安装的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的信息。</span><span class="sxs-lookup"><span data-stu-id="6d720-131">A Windows service that listens for incoming requests for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources and provides clients information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span> <span data-ttu-id="6d720-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务的单个实例用于计算机上安装的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="6d720-132">A single instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service is used for all instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installed on the computer.</span></span>  
  
###  <a name="additional-information"></a><a name="MoreInformation"></a><span data-ttu-id="6d720-133">附加信息</span><span class="sxs-lookup"><span data-stu-id="6d720-133">Additional Information</span></span>  
  
-   <span data-ttu-id="6d720-134">暂停 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服务将阻止新用户连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]，但是已连接的用户可以继续工作到连接断开时为止。</span><span class="sxs-lookup"><span data-stu-id="6d720-134">Pausing the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service prevents new users from connecting to the [!INCLUDE[ssDE](../../includes/ssde-md.md)], but users who are already connected can continue to work until their connections are broken.</span></span> <span data-ttu-id="6d720-135">当希望在您停止该服务前等待用户完成工作时，请使用“暂停”。</span><span class="sxs-lookup"><span data-stu-id="6d720-135">Use pause when you want to wait for users to complete work before you stop the service.</span></span> <span data-ttu-id="6d720-136">这使他们能够完成正在进行的事务。</span><span class="sxs-lookup"><span data-stu-id="6d720-136">This enables them to complete transactions that are in progress.</span></span> <span data-ttu-id="6d720-137">“继续”允许 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 再次接受新连接。</span><span class="sxs-lookup"><span data-stu-id="6d720-137">Resume allows the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to accept new connections again.</span></span> <span data-ttu-id="6d720-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务不能暂停或继续。</span><span class="sxs-lookup"><span data-stu-id="6d720-138">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service cannot be paused or resumed.</span></span>  
  
-   <span data-ttu-id="6d720-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 使用以下图标显示服务的当前状态。</span><span class="sxs-lookup"><span data-stu-id="6d720-139">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] display the current status of services by using the following icons.</span></span>  
  
     <span data-ttu-id="6d720-140">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager**</span><span class="sxs-lookup"><span data-stu-id="6d720-140">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager**</span></span>  
  
    -   <span data-ttu-id="6d720-141">服务名称旁边的图标上的绿色箭头表示服务已启动。</span><span class="sxs-lookup"><span data-stu-id="6d720-141">A green arrow on the icon next to the service name indicates that the service is started.</span></span>  
  
    -   <span data-ttu-id="6d720-142">服务名称旁边的图标上的红色正方形表示服务已停止。</span><span class="sxs-lookup"><span data-stu-id="6d720-142">A red square on the icon next to the service name indicates that the service is stopped.</span></span>  
  
    -   <span data-ttu-id="6d720-143">服务名称旁边的图标上的两条蓝色竖线表示服务已暂停。</span><span class="sxs-lookup"><span data-stu-id="6d720-143">Two vertical blue lines on the icon next to the service name indicates that the service is paused.</span></span>  
  
    -   <span data-ttu-id="6d720-144">重新启动 [!INCLUDE[ssDE](../../includes/ssde-md.md)]时，将用红色正方形表示服务已停止，然后用绿色箭头表示服务已成功启动。</span><span class="sxs-lookup"><span data-stu-id="6d720-144">When restarting the [!INCLUDE[ssDE](../../includes/ssde-md.md)], a red square will indicate that the service stopped, and then a green arrow will indicate that he service started successfully.</span></span>  
  
     **[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
    -   <span data-ttu-id="6d720-145">服务名称旁边的绿色圆圈图标上的白色箭头表示服务已启动。</span><span class="sxs-lookup"><span data-stu-id="6d720-145">A white arrow on a green circle icon next to the service name indicates that the service is started.</span></span>  
  
    -   <span data-ttu-id="6d720-146">服务名称旁边的红色圆圈图标上的白色正方形表示服务已停止。</span><span class="sxs-lookup"><span data-stu-id="6d720-146">A white square on a red circle icon next to the service name indicates that the service is stopped.</span></span>  
  
    -   <span data-ttu-id="6d720-147">服务名称旁边的蓝色圆圈图标上的两条白色竖线表示服务已暂停。</span><span class="sxs-lookup"><span data-stu-id="6d720-147">Two vertical white lines on a blue circle icon next to the service name indicates that the service is paused.</span></span>  
  
-   <span data-ttu-id="6d720-148">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]时，只提供可能的选项。</span><span class="sxs-lookup"><span data-stu-id="6d720-148">When using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], only options that are possible will be available.</span></span> <span data-ttu-id="6d720-149">例如，如果服务已启动， **“启动”** 将不可用。</span><span class="sxs-lookup"><span data-stu-id="6d720-149">For example, if the service is already started, **Start** will be unavailable.</span></span>  
  
-   <span data-ttu-id="6d720-150">在群集上运行时， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 服务最好使用群集管理器来管理。</span><span class="sxs-lookup"><span data-stu-id="6d720-150">When running on a cluster, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service is best managed by using Cluster Administrator.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6d720-151">Security</span><span class="sxs-lookup"><span data-stu-id="6d720-151">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6d720-152">权限</span><span class="sxs-lookup"><span data-stu-id="6d720-152">Permissions</span></span>  
 <span data-ttu-id="6d720-153">默认情况下，只有本地管理员组的成员能够启动、停止、暂停、继续或重新启动服务。</span><span class="sxs-lookup"><span data-stu-id="6d720-153">By default, only members of the local administrators group can start, stop, pause, resume or restart a service.</span></span> <span data-ttu-id="6d720-154">若要向管理员之外的用户授予管理服务的权限，请参阅 [如何授予用户管理 Windows Server 2003 中的服务的权限](https://support.microsoft.com/kb/325349)。</span><span class="sxs-lookup"><span data-stu-id="6d720-154">To grant non-administrators the ability to manage services, see [How to grant users rights to manage services in Windows Server 2003](https://support.microsoft.com/kb/325349).</span></span> <span data-ttu-id="6d720-155">（此过程在其他 Windows 版本上是类似的。）</span><span class="sxs-lookup"><span data-stu-id="6d720-155">(The process is similar on other versions of Windows.)</span></span>  
  
 <span data-ttu-id="6d720-156">[!INCLUDE[ssDE](../../includes/ssde-md.md)]使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] `SHUTDOWN` 命令停止需要**sysadmin**或**serveradmin**固定服务器角色的成员身份，并且不可转让。</span><span class="sxs-lookup"><span data-stu-id="6d720-156">Stopping the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by using the [!INCLUDE[tsql](../../includes/tsql-md.md)]`SHUTDOWN` command requires membership in the **sysadmin** or **serveradmin** fixed server roles, and is not transferable.</span></span>  
  
##  <a name="using-ssnoversion-configuration-manager"></a><a name="SSCMProcedure"></a> <span data-ttu-id="6d720-157">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器</span><span class="sxs-lookup"><span data-stu-id="6d720-157">Using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager</span></span>  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-an-instance-of-the-ssdenoversion"></a><span data-ttu-id="6d720-158">启动、停止、暂停、继续或重新启动 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d720-158">To start, stop, pause, resume, or restart the an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]</span></span>  
  
1.  <span data-ttu-id="6d720-159">在 **“开始”** 菜单中，依次指向 **“所有程序”** 、 [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]、 **“配置工具”** ，然后单击 **“SQL Server 配置管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="6d720-159">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="6d720-160">如果此时出现 **“用户帐户控制”** 对话框，请单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="6d720-160">If the **User Account Control** dialog box appears, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="6d720-161">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器的左窗格中，单击 **“SQL Server 服务”**。</span><span class="sxs-lookup"><span data-stu-id="6d720-161">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the left pane, click **SQL Server Services**.</span></span>  
  
4.  <span data-ttu-id="6d720-162">在结果窗格中，右键单击 **SQL Server (MSSQLServer)** 或某个命名实例，然后单击“启动”、“停止”、“暂停”、“继续”或“重启”。</span><span class="sxs-lookup"><span data-stu-id="6d720-162">In the results pane, right-click **SQL Server (MSSQLServer)** or a named instance, and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.</span></span>  
  
5.  <span data-ttu-id="6d720-163">单击 **“确定”** 关闭 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器。</span><span class="sxs-lookup"><span data-stu-id="6d720-163">Click **OK** to close [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6d720-164">若要使用启动选项启动一个 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例，请参阅[配置服务器启动选项（SQL Server 配置管理器）](scm-services-configure-server-startup-options.md)。</span><span class="sxs-lookup"><span data-stu-id="6d720-164">To start an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] with startup options, see [Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](scm-services-configure-server-startup-options.md).</span></span>  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-ssnoversion-browser-or-an-instance-of-the-ssnoversion-agent"></a><span data-ttu-id="6d720-165">启动、停止、暂停、继续或重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理实例</span><span class="sxs-lookup"><span data-stu-id="6d720-165">To start, stop, pause, resume, or restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser or an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent</span></span>  
  
1.  <span data-ttu-id="6d720-166">在 **“开始”** 菜单中，依次指向 **“所有程序”** 、 [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]、 **“配置工具”** ，然后单击 **“SQL Server 配置管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="6d720-166">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="6d720-167">如果此时出现 **“用户帐户控制”** 对话框，请单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="6d720-167">If the **User Account Control** dialog box appears, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="6d720-168">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器的左窗格中，单击 **“SQL Server 服务”**。</span><span class="sxs-lookup"><span data-stu-id="6d720-168">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the left pane, click **SQL Server Services**.</span></span>  
  
4.  <span data-ttu-id="6d720-169">在结果窗格中，右键单击 " \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 浏览器**" 或 " \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent (MSSQLServer) **或** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent ( # B0 instance_name>) **用于命名实例，然后单击"**启动**"、"**停止**"、"**暂停**"、"**恢复**"或"**重新启动**"。</span><span class="sxs-lookup"><span data-stu-id="6d720-169">In the results pane, right-click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser**, or **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent (MSSQLServer)** or **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent (<instance_name>)** for a named instance, and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.</span></span>  
  
5.  <span data-ttu-id="6d720-170">单击 **“确定”** 关闭 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器。</span><span class="sxs-lookup"><span data-stu-id="6d720-170">Click **OK** to close [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6d720-171">代理不能暂停。</span><span class="sxs-lookup"><span data-stu-id="6d720-171">Agent cannot be paused.</span></span>  
  
##  <a name="using-ssnoversion-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6d720-172">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio</span><span class="sxs-lookup"><span data-stu-id="6d720-172">Using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio</span></span>  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-an-instance-of-the-ssdenoversion"></a><span data-ttu-id="6d720-173">启动、停止、暂停、继续或重新启动 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d720-173">To start, stop, pause, resume, or restart the an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]</span></span>  
  
1.  <span data-ttu-id="6d720-174">在对象资源管理器中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，右键单击要启动的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，然后单击“启动”\*\*\*\*、“停止”\*\*\*\*、“暂停”\*\*\*\*、“继续”\*\*\*\* 或“重启”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6d720-174">In Object Explorer, connect to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], right-click the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] you want to start, and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.</span></span>  
  
     <span data-ttu-id="6d720-175">或者，在“已注册的服务器”中，右键单击要启动的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例，指向“服务控制”\*\*\*\*，然后单击“启动”\*\*\*\*、“停止”\*\*\*\*、“暂停”\*\*\*\*、“继续”\*\*\*\* 或“重启”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6d720-175">Or, in Registered Servers, right-click the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] you want to start, point to **Service Control**, and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.</span></span>  
  
2.  <span data-ttu-id="6d720-176">如果此时出现 **“用户帐户控制”** 对话框，请单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="6d720-176">If the **User Account Control** dialog box appears, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="6d720-177">系统提示是否要执行该操作时，请单击 **“是”**。</span><span class="sxs-lookup"><span data-stu-id="6d720-177">When prompted if you want to perform the action, click **Yes**.</span></span>  
  
#### <a name="to-start-stop-or-restart-the-an-instance-of-the-ssnoversion-agent"></a><span data-ttu-id="6d720-178">启动、停止或重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理实例</span><span class="sxs-lookup"><span data-stu-id="6d720-178">To start, stop, or restart the an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent</span></span>  
  
1.  <span data-ttu-id="6d720-179">在对象资源管理器中，连接到的实例 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ，右键单击 " \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理**"，然后单击 "**启动**"、"**停止**" 或 "**重新启动\*\*"。</span><span class="sxs-lookup"><span data-stu-id="6d720-179">In Object Explorer, connect to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], right-click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent**, and then click **Start**, **Stop**, or **Restart**.</span></span>  
  
2.  <span data-ttu-id="6d720-180">如果此时出现 **“用户帐户控制”** 对话框，请单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="6d720-180">If the **User Account Control** dialog box appears, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="6d720-181">系统提示是否要执行该操作时，请单击 **“是”**。</span><span class="sxs-lookup"><span data-stu-id="6d720-181">When prompted if you want to perform the action, click **Yes**.</span></span>  
  
##  <a name="from-the-command-prompt-window-using-net-commands"></a><a name="CommandPrompt"></a><span data-ttu-id="6d720-182">在命令提示符窗口中使用 net 命令</span><span class="sxs-lookup"><span data-stu-id="6d720-182">From the Command Prompt Window using net Commands</span></span>  
 <span data-ttu-id="6d720-183">可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows net 命令启动、停止或暂停 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6d720-183">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services can be started, stopped, or paused by using [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows **net** commands.</span></span>  
  
###  <a name="to-start-the-default-instance-of-the-ssde"></a><a name="dbDefault"></a><span data-ttu-id="6d720-184">启动的默认实例[!INCLUDE[ssDE](../../includes/ssde-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d720-184">To start the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span></span>  
  
-   <span data-ttu-id="6d720-185">在命令提示符下，输入下列命令之一：</span><span class="sxs-lookup"><span data-stu-id="6d720-185">From a command prompt, enter one of the following commands:</span></span>  
  
     <span data-ttu-id="6d720-186">**net start "SQL Server (MSSQLSERVER)"**</span><span class="sxs-lookup"><span data-stu-id="6d720-186">**net start "SQL Server (MSSQLSERVER)"**</span></span>  
  
     <span data-ttu-id="6d720-187">-或-</span><span class="sxs-lookup"><span data-stu-id="6d720-187">-or-</span></span>  
  
     <span data-ttu-id="6d720-188">**net start MSSQLSERVER**</span><span class="sxs-lookup"><span data-stu-id="6d720-188">**net start MSSQLSERVER**</span></span>  
  
###  <a name="to-start-a-named-instance-of-the-ssde"></a><a name="dbNamed"></a> <span data-ttu-id="6d720-189">启动 [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d720-189">To start a named instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span></span>  
  
-   <span data-ttu-id="6d720-190">在命令提示符下，输入下列命令之一。</span><span class="sxs-lookup"><span data-stu-id="6d720-190">From a command prompt, enter one of the following commands.</span></span> <span data-ttu-id="6d720-191">使用要管理的实例的名称替换 \<instancename>。</span><span class="sxs-lookup"><span data-stu-id="6d720-191">Replace *\<instancename>* with the name of the instance you want to manage.</span></span>  
  
     <span data-ttu-id="6d720-192">**net start "SQL Server (** *instancename* **)"**</span><span class="sxs-lookup"><span data-stu-id="6d720-192">**net start "SQL Server (** *instancename* **)"**</span></span>  
  
     <span data-ttu-id="6d720-193">-或-</span><span class="sxs-lookup"><span data-stu-id="6d720-193">-or-</span></span>  
  
     <span data-ttu-id="6d720-194">**net start MSSQL$** *instancename*</span><span class="sxs-lookup"><span data-stu-id="6d720-194">**net start MSSQL$** *instancename*</span></span>  
  
###  <a name="to-start-the-ssde-with-startup-options"></a><a name="dbStartup"></a> <span data-ttu-id="6d720-195">使用启动选项启动 [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d720-195">To start the [!INCLUDE[ssDE](../../includes/ssde-md.md)] with startup options</span></span>  
  
-   <span data-ttu-id="6d720-196">将启动选项添加到 **net start "SQL Server (MSSQLSERVER)"** 语句末尾，之间用空格分隔开。</span><span class="sxs-lookup"><span data-stu-id="6d720-196">Add startup options to the end of the **net start "SQL Server (MSSQLSERVER)"** statement, separated by a space.</span></span> <span data-ttu-id="6d720-197">使用 **net start**启动时，启动选项使用正斜杠 (/) 而不是连字符 (-)。</span><span class="sxs-lookup"><span data-stu-id="6d720-197">When started using **net start**, startup options use a slash (/) instead of a hyphen (-).</span></span>  
  
     <span data-ttu-id="6d720-198">**net start "SQL Server (MSSQLSERVER)" /f /m**</span><span class="sxs-lookup"><span data-stu-id="6d720-198">**net start "SQL Server (MSSQLSERVER)" /f /m**</span></span>  
  
     <span data-ttu-id="6d720-199">-或-</span><span class="sxs-lookup"><span data-stu-id="6d720-199">-or-</span></span>  
  
     <span data-ttu-id="6d720-200">**net start MSSQLSERVER /f /m**</span><span class="sxs-lookup"><span data-stu-id="6d720-200">**net start MSSQLSERVER /f /m**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6d720-201">有关启动选项的详细信息，请参阅 [数据库引擎服务启动选项](database-engine-service-startup-options.md)。</span><span class="sxs-lookup"><span data-stu-id="6d720-201">For more information about startup options, see [Database Engine Service Startup Options](database-engine-service-startup-options.md).</span></span>  
  
###  <a name="to-start-the-ssnoversion-agent-on-the-default-instance-of-ssnoversion"></a><a name="agDefault"></a> <span data-ttu-id="6d720-202">使用启动选项启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 默认实例上启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d720-202">To start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent on the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="6d720-203">在命令提示符下，输入下列命令之一：</span><span class="sxs-lookup"><span data-stu-id="6d720-203">From a command prompt, enter one of the following commands:</span></span>  
  
     <span data-ttu-id="6d720-204">**net start "SQL Server Agent (MSSQLSERVER)"**</span><span class="sxs-lookup"><span data-stu-id="6d720-204">**net start "SQL Server Agent (MSSQLSERVER)"**</span></span>  
  
     <span data-ttu-id="6d720-205">-或-</span><span class="sxs-lookup"><span data-stu-id="6d720-205">-or-</span></span>  
  
     <span data-ttu-id="6d720-206">**net start SQLSERVERAGENT**</span><span class="sxs-lookup"><span data-stu-id="6d720-206">**net start SQLSERVERAGENT**</span></span>  
  
###  <a name="to-start-the-ssnoversion-agent-on-a-named-instance-of-ssnoversion"></a><a name="agNamed"></a><span data-ttu-id="6d720-207">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]在的命名实例上启动代理[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d720-207">To start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent on a named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="6d720-208">在命令提示符下，输入下列命令之一。</span><span class="sxs-lookup"><span data-stu-id="6d720-208">From a command prompt, enter one of the following commands.</span></span> <span data-ttu-id="6d720-209">将 *instancename* 替换为要管理的实例的名称。</span><span class="sxs-lookup"><span data-stu-id="6d720-209">Replace *instancename* with the name of the instance you want to manage.</span></span>  
  
     <span data-ttu-id="6d720-210">**net start "SQL Server Agent(** *instancename* **)"**</span><span class="sxs-lookup"><span data-stu-id="6d720-210">**net start "SQL Server Agent(** *instancename* **)"**</span></span>  
  
     <span data-ttu-id="6d720-211">-或-</span><span class="sxs-lookup"><span data-stu-id="6d720-211">-or-</span></span>  
  
     <span data-ttu-id="6d720-212">**net start SQLAgent$** *instancename*</span><span class="sxs-lookup"><span data-stu-id="6d720-212">**net start SQLAgent$** *instancename*</span></span>  
  
 <span data-ttu-id="6d720-213">有关如何在详细模式中运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理以执行故障排除的信息，请参阅 [sqlagent90 应用程序](../../tools/sqlagent90-application.md)。</span><span class="sxs-lookup"><span data-stu-id="6d720-213">For information about how to run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in verbose mode for troubleshooting, see [sqlagent90 Application](../../tools/sqlagent90-application.md).</span></span>  
  
###  <a name="to-start-the-ssnoversion-browser"></a><a name="Browser"></a><span data-ttu-id="6d720-214">启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 浏览器</span><span class="sxs-lookup"><span data-stu-id="6d720-214">To start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser</span></span>  
  
-   <span data-ttu-id="6d720-215">在命令提示符下，输入下列命令之一：</span><span class="sxs-lookup"><span data-stu-id="6d720-215">From a command prompt, enter one of the following commands:</span></span>  
  
     <span data-ttu-id="6d720-216">**net start "SQL Server Browser"**</span><span class="sxs-lookup"><span data-stu-id="6d720-216">**net start "SQL Server Browser"**</span></span>  
  
     <span data-ttu-id="6d720-217">-或-</span><span class="sxs-lookup"><span data-stu-id="6d720-217">-or-</span></span>  
  
     <span data-ttu-id="6d720-218">**net start SQLBrowser**</span><span class="sxs-lookup"><span data-stu-id="6d720-218">**net start SQLBrowser**</span></span>  
  
###  <a name="to-pause-or-stop-services-from-the-command-prompt-window"></a><a name="pauseStop"></a> <span data-ttu-id="6d720-219">在命令提示符窗口中暂停或停止服务</span><span class="sxs-lookup"><span data-stu-id="6d720-219">To pause or stop services from the Command Prompt window</span></span>  
  
-   <span data-ttu-id="6d720-220">要暂停或停止服务，请通过以下方式修改命令：</span><span class="sxs-lookup"><span data-stu-id="6d720-220">To pause or stop services modify the commands in the following ways.</span></span>  
  
    -   <span data-ttu-id="6d720-221">若要暂停服务，请将 **net start** 替换为 **net pause**。</span><span class="sxs-lookup"><span data-stu-id="6d720-221">To pause a service, replace **net start** with **net pause**.</span></span>  
  
    -   <span data-ttu-id="6d720-222">若要停止服务，请将 **net start** 替换为 **net stop**。</span><span class="sxs-lookup"><span data-stu-id="6d720-222">To stop a service, replace **net start** with use **net stop**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6d720-223">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6d720-223">Using Transact-SQL</span></span>  
 <span data-ttu-id="6d720-224">可以使用 `SHUTDOWN` 语句停止[!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6d720-224">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] can be stopped by using the `SHUTDOWN` statement.</span></span>  
  
#### <a name="to-stop-the-ssde-using-tsql"></a><span data-ttu-id="6d720-225">使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 停止 [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d720-225">To stop the [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  
-   <span data-ttu-id="6d720-226">要等待当前运行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句和存储过程完成后停止 [!INCLUDE[ssDE](../../includes/ssde-md.md)]，请执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="6d720-226">To wait for currently running [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and stored procedures to finish, and then stop the [!INCLUDE[ssDE](../../includes/ssde-md.md)], execute the following statement.</span></span>  
  
    ```sql  
    SHUTDOWN;   
    ```  
  
-   <span data-ttu-id="6d720-227">要立即停止[!INCLUDE[ssDE](../../includes/ssde-md.md)]，请执行以下语句：</span><span class="sxs-lookup"><span data-stu-id="6d720-227">To stop the [!INCLUDE[ssDE](../../includes/ssde-md.md)] immediately, execute the following statement.</span></span>  
  
    ```sql  
    SHUTDOWN WITH NOWAIT;   
    ```  
  
 <span data-ttu-id="6d720-228">有关语句的详细信息 `SHUTDOWN` ，请参阅[SHUTDOWN &#40;transact-sql&#41;](/sql/t-sql/language-elements/shutdown-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6d720-228">For more information about the `SHUTDOWN` statement, see [SHUTDOWN &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/shutdown-transact-sql).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="6d720-229">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6d720-229">Using PowerShell</span></span>  
  
#### <a name="to-start-and-stop-ssde-services"></a><span data-ttu-id="6d720-230">启动和停止 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服务</span><span class="sxs-lookup"><span data-stu-id="6d720-230">To start and stop [!INCLUDE[ssDE](../../includes/ssde-md.md)] services</span></span>  
  
1.  <span data-ttu-id="6d720-231">在命令提示符窗口中，通过执行以下命令启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell：</span><span class="sxs-lookup"><span data-stu-id="6d720-231">In a Command Prompt window, start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell by executing the following command.</span></span>  
  
    ```ms-dos  
    sqlps  
    ```  
  
2.  <span data-ttu-id="6d720-232">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 命令提示符下，执行以下命令。</span><span class="sxs-lookup"><span data-stu-id="6d720-232">At a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell command prompt, by executing the following command.</span></span> <span data-ttu-id="6d720-233">使用您的计算机名称替换 `computername` 。</span><span class="sxs-lookup"><span data-stu-id="6d720-233">Replace `computername` with the name of your computer.</span></span>  
  
    ```powershell  
    # Get a reference to the ManagedComputer class.  
    CD SQLSERVER:\SQL\computername  
    $Wmi = (Get-Item .).ManagedComputer
    ```  
  
3.  <span data-ttu-id="6d720-234">标识要停止或启动的服务。</span><span class="sxs-lookup"><span data-stu-id="6d720-234">Identify the service that you want to stop or start.</span></span> <span data-ttu-id="6d720-235">选取下列行之一。</span><span class="sxs-lookup"><span data-stu-id="6d720-235">Pick one of the following lines.</span></span> <span data-ttu-id="6d720-236">使用命名实例的名称替换 `instancename` 。</span><span class="sxs-lookup"><span data-stu-id="6d720-236">Replace `instancename` with the name of the named instance.</span></span>  
  
    -   <span data-ttu-id="6d720-237">获取对 [!INCLUDE[ssDE](../../includes/ssde-md.md)]默认实例的引用。</span><span class="sxs-lookup"><span data-stu-id="6d720-237">To get a reference to the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['MSSQLSERVER']  
        ```  
  
    -   <span data-ttu-id="6d720-238">获取对 [!INCLUDE[ssDE](../../includes/ssde-md.md)]命名实例的引用。</span><span class="sxs-lookup"><span data-stu-id="6d720-238">To get a reference to a named instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['MSSQL$instancename']  
        ```  
  
    -   <span data-ttu-id="6d720-239">获取对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 默认实例上 [!INCLUDE[ssDE](../../includes/ssde-md.md)]代理服务的引用。</span><span class="sxs-lookup"><span data-stu-id="6d720-239">To get a reference to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service on the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLSERVERAGENT']  
        ```  
  
    -   <span data-ttu-id="6d720-240">获取对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 命名实例上 [!INCLUDE[ssDE](../../includes/ssde-md.md)]代理服务的引用。</span><span class="sxs-lookup"><span data-stu-id="6d720-240">To get a reference to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service on a named instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLAGENT$instancename']  
        ```  
  
    -   <span data-ttu-id="6d720-241">获取对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务的引用。</span><span class="sxs-lookup"><span data-stu-id="6d720-241">To get a reference to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLBROWSER']  
        ```  
  
4.  <span data-ttu-id="6d720-242">完成示例以启动然后停止所选服务。</span><span class="sxs-lookup"><span data-stu-id="6d720-242">Complete the example to start and then stop the selected service.</span></span>  
  
    ```powershell  
    # Display the state of the service.  
    $DfltInstance  
    # Start the service.  
    $DfltInstance.Start();  
    # Wait until the service has time to start.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    # Stop the service.  
    $DfltInstance.Stop();  
    # Wait until the service has time to stop.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6d720-243">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6d720-243">See Also</span></span>  
 <span data-ttu-id="6d720-244">[以最小配置启动 SQL Server](start-sql-server-with-minimal-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="6d720-244">[Start SQL Server with Minimal Configuration](start-sql-server-with-minimal-configuration.md) </span></span>  
 [<span data-ttu-id="6d720-245">SQL Server 2014 各个版本支持的功能</span><span class="sxs-lookup"><span data-stu-id="6d720-245">Features Supported by the Editions of SQL Server 2014</span></span>](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
