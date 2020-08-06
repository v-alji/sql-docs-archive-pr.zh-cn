---
title: 在单用户模式下启动 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- starting SQL Server, single-user mode
- single-user mode [SQL Server]
ms.assetid: 72eb4fc1-7af4-4ec6-9e02-11a69e02748e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b2600524da45f9a81f155432397cee2e7e876274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577824"
---
# <a name="start-sql-server-in-single-user-mode"></a><span data-ttu-id="15143-102">在单用户模式下启动 SQL Server</span><span class="sxs-lookup"><span data-stu-id="15143-102">Start SQL Server in Single-User Mode</span></span>
  <span data-ttu-id="15143-103">在某些情况下，可能必须使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup option -m **在单用户模式下启动**实例。</span><span class="sxs-lookup"><span data-stu-id="15143-103">Under certain circumstances, you may have to start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode by using the **startup option -m.**</span></span> <span data-ttu-id="15143-104">例如，您可能要更改服务器配置选项或恢复已破坏的 master 数据库或其他系统数据库。</span><span class="sxs-lookup"><span data-stu-id="15143-104">For example, you may want to change server configuration options or recover a damaged master database or other system database.</span></span> <span data-ttu-id="15143-105">这两个操作都需要在单用户模式下启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="15143-105">Both actions require starting an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode.</span></span>  
  
 <span data-ttu-id="15143-106">在单用户模式下启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可使计算机本地 Administrators 组的任何成员作为 sysadmin 固定服务器角色的成员连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="15143-106">Starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode enables any member of the computer's local Administrators group to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a member of the sysadmin fixed server role.</span></span> <span data-ttu-id="15143-107">有关详细信息，请参阅 [在系统管理员被锁定时连接到 SQL Server](connect-to-sql-server-when-system-administrators-are-locked-out.md)。</span><span class="sxs-lookup"><span data-stu-id="15143-107">For more information, see [Connect to SQL Server When System Administrators Are Locked Out](connect-to-sql-server-when-system-administrators-are-locked-out.md).</span></span>  
  
 <span data-ttu-id="15143-108">在单用户模式下启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时，请注意下列事项：</span><span class="sxs-lookup"><span data-stu-id="15143-108">When you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode, note the following:</span></span>  
  
-   <span data-ttu-id="15143-109">只有一个用户可以连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="15143-109">Only one user can connect to the server.</span></span>  
  
-   <span data-ttu-id="15143-110">不执行 CHECKPOINT 进程。</span><span class="sxs-lookup"><span data-stu-id="15143-110">The CHECKPOINT process is not executed.</span></span> <span data-ttu-id="15143-111">默认情况下，启动时自动执行此进程。</span><span class="sxs-lookup"><span data-stu-id="15143-111">By default, it is executed automatically at startup.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15143-112">在单用户模式下连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例之前，停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服务；否则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服务将使用该连接，从而使其阻塞。</span><span class="sxs-lookup"><span data-stu-id="15143-112">Stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service before connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode; otherwise, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service uses the connection, thereby blocking it.</span></span>  
  
 <span data-ttu-id="15143-113">在单用户模式下启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 可以连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="15143-113">When you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] can connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="15143-114">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中的对象资源管理器可能会失败，因为在某些操作中它需要使用多个连接。</span><span class="sxs-lookup"><span data-stu-id="15143-114">Object Explorer in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] might fail because it requires more than one connection for some operations.</span></span> <span data-ttu-id="15143-115">若要在单用户模式下管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，可以执行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句（仅通过 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的查询编辑器连接）或者使用 [sqlcmd 实用工具](../../tools/sqlcmd-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="15143-115">To manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode, execute [!INCLUDE[tsql](../../includes/tsql-md.md)] statements by connecting only through the Query Editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], or use the [sqlcmd utility](../../tools/sqlcmd-utility.md).</span></span>  
  
 <span data-ttu-id="15143-116">当你将 **-m**选项与**sqlcmd**或结合使用时 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ，你可以限制与指定客户端应用程序的连接。</span><span class="sxs-lookup"><span data-stu-id="15143-116">When you use the **-m** option with **sqlcmd** or [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can limit the connections to a specified client application.</span></span> <span data-ttu-id="15143-117">例如， **-m "sqlcmd"** 将连接限制为单个连接，并且该连接必须将自身标识为**sqlcmd**客户端程序。</span><span class="sxs-lookup"><span data-stu-id="15143-117">For example, **-m"sqlcmd"** limits connections to a single connection and that connection must identify itself as the **sqlcmd** client program.</span></span> <span data-ttu-id="15143-118">当您正在单用户模式下启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 并且未知的客户端应用程序正在占用这个唯一的可用连接时，使用此选项。</span><span class="sxs-lookup"><span data-stu-id="15143-118">Use this option when you are starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode and an unknown client application is taking the only available connection.</span></span> <span data-ttu-id="15143-119">若要通过 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的查询编辑器进行连接，请使用 **-m"Microsoft SQL Server Management Studio - Query"** 。</span><span class="sxs-lookup"><span data-stu-id="15143-119">To connect through the Query Editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], use **-m"Microsoft SQL Server Management Studio - Query"**.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="15143-120">不要将此选项作为安全功能使用。</span><span class="sxs-lookup"><span data-stu-id="15143-120">Do not use this option as a security feature.</span></span> <span data-ttu-id="15143-121">客户端应用程序提供客户端应用程序名称，并且提供假名称来作为连接字符串的一部分。</span><span class="sxs-lookup"><span data-stu-id="15143-121">The client application provides the client application name, and can provide a false name as part of the connection string.</span></span>  
  
## <a name="note-for-clustered-installations"></a><span data-ttu-id="15143-122">针对群集安装的说明</span><span class="sxs-lookup"><span data-stu-id="15143-122">Note for Clustered installations</span></span>  
 <span data-ttu-id="15143-123">对于群集环境中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装，在单用户模式下启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，群集资源 dll 将占用可用连接，因此阻塞与服务器的任何其他连接。</span><span class="sxs-lookup"><span data-stu-id="15143-123">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation in a clustered environment, when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started in single user mode, the cluster resource dll uses up the available connection thereby blocking any other connections to the server.</span></span> <span data-ttu-id="15143-124">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 处于此状态下时，如果您尝试使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理资源处于联机状态，则在该资源配置为对组产生影响时，它可能会将 SQL 资源故障转移到其他节点。</span><span class="sxs-lookup"><span data-stu-id="15143-124">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is in this state, if you try to bring [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent resource online, it may fail over the SQL resource to a different node if the resource is configured to affect the group.</span></span>  
  
 <span data-ttu-id="15143-125">为解决此问题，请执行以下过程：</span><span class="sxs-lookup"><span data-stu-id="15143-125">To get around the problem use the following procedure:</span></span>  
  
1.  <span data-ttu-id="15143-126">从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 高级属性中删除 -m 启动参数。</span><span class="sxs-lookup"><span data-stu-id="15143-126">Remove the -m startup parameter from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] advanced Properties.</span></span>  
  
2.  <span data-ttu-id="15143-127">使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 资源脱机。</span><span class="sxs-lookup"><span data-stu-id="15143-127">Take the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource offline.</span></span>  
  
3.  <span data-ttu-id="15143-128">从该组的当前所有者节点，在命令提示符下发出以下命令：</span><span class="sxs-lookup"><span data-stu-id="15143-128">From the current owner node of this group, issue the following command from the command prompt:</span></span>  
    <span data-ttu-id="15143-129">net start MSSQLSERVER /m。</span><span class="sxs-lookup"><span data-stu-id="15143-129">net start MSSQLSERVER /m.</span></span>  
  
4.  <span data-ttu-id="15143-130">从群集管理器或故障转移群集管理控制台验证 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 资源仍处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="15143-130">Verify from the cluster administrator or failover cluster management console that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource is still offline.</span></span>  
  
5.  <span data-ttu-id="15143-131">现在使用以下命令连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 并且执行必需的操作：SQLCMD -E -S\<servername>。</span><span class="sxs-lookup"><span data-stu-id="15143-131">Connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] now using the following command and do the necessary operation: SQLCMD -E -S\<servername>.</span></span>  
  
6.  <span data-ttu-id="15143-132">一旦完成该操作后，关闭命令提示符并且通过群集管理器使 SQL 和其他资源返回联机状态。</span><span class="sxs-lookup"><span data-stu-id="15143-132">Once the operation is complete, close the command prompt and bring back the SQL and other resources online through cluster administrator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15143-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="15143-133">See Also</span></span>  
 <span data-ttu-id="15143-134">[启动、停止或暂停 SQL Server 代理服务](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md) </span><span class="sxs-lookup"><span data-stu-id="15143-134">[Start, Stop, or Pause the SQL Server Agent Service](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md) </span></span>  
 <span data-ttu-id="15143-135">[用于数据库管理员的诊断连接](diagnostic-connection-for-database-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="15143-135">[Diagnostic Connection for Database Administrators](diagnostic-connection-for-database-administrators.md) </span></span>  
 <span data-ttu-id="15143-136">[sqlcmd 实用工具](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="15143-136">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 <span data-ttu-id="15143-137">[检查点 (Transact-SQL)](/sql/t-sql/language-elements/checkpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="15143-137">[CHECKPOINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/checkpoint-transact-sql) </span></span>  
 <span data-ttu-id="15143-138">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="15143-138">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="15143-139">数据库引擎服务启动选项</span><span class="sxs-lookup"><span data-stu-id="15143-139">Database Engine Service Startup Options</span></span>](database-engine-service-startup-options.md)  
  
  
