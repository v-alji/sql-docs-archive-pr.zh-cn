---
title: 以最小配置启动 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- minimal configuration [SQL Server]
- starting SQL Server, minimal configuration
ms.assetid: 4d733c99-28b3-42d8-b7f6-7b943b548173
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5c78fc10be584803b438b2cd125a77400ff369b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577826"
---
# <a name="start-sql-server-with-minimal-configuration"></a><span data-ttu-id="f23ed-102">以最小配置启动 SQL Server</span><span class="sxs-lookup"><span data-stu-id="f23ed-102">Start SQL Server with Minimal Configuration</span></span>
  <span data-ttu-id="f23ed-103">如果存在配置问题而无法启动服务器，可使用最小配置启动选项来启动 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="f23ed-103">If you have configuration problems that prevent the server from starting, you can start an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the minimal configuration startup option.</span></span> <span data-ttu-id="f23ed-104">这就是启动选项 **-f**。</span><span class="sxs-lookup"><span data-stu-id="f23ed-104">This is the startup option **-f**.</span></span> <span data-ttu-id="f23ed-105">使用最小配置启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例会自动将服务器置于单用户模式。</span><span class="sxs-lookup"><span data-stu-id="f23ed-105">Starting an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with minimal configuration automatically puts the server in single-user mode.</span></span>  
  
 <span data-ttu-id="f23ed-106">在最小配置模式下启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时，注意下列事项：</span><span class="sxs-lookup"><span data-stu-id="f23ed-106">When you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in minimal configuration mode, note the following:</span></span>  
  
-   <span data-ttu-id="f23ed-107">只有一个用户可以连接到服务器，并且不会执行 CHECKPOINT 进程。</span><span class="sxs-lookup"><span data-stu-id="f23ed-107">Only a single user can connect, and the CHECKPOINT process is not executed.</span></span>  
  
-   <span data-ttu-id="f23ed-108">远程访问和预读功能将被禁用。</span><span class="sxs-lookup"><span data-stu-id="f23ed-108">Remote access and read-ahead are disabled.</span></span>  
  
-   <span data-ttu-id="f23ed-109">启动存储过程将不运行。</span><span class="sxs-lookup"><span data-stu-id="f23ed-109">Startup stored procedures do not run.</span></span>  
  
 <span data-ttu-id="f23ed-110">用最小配置启动服务器后，应更改相应的服务器选项值，然后停止并重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="f23ed-110">After the server has been started with minimal configuration, you should change the appropriate server option value or values, stop, and then restart the server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f23ed-111">使用 **sqlcmd** 实用工具和专用管理员连接 (DAC) 连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f23ed-111">Use the **sqlcmd** utility and the dedicated administrator connection (DAC) to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f23ed-112">如果使用典型连接，则在最小配置模式下连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例之前，停止 SQL Server 代理服务。</span><span class="sxs-lookup"><span data-stu-id="f23ed-112">If you use a typical connection, stop the SQL Server Agent service before connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in minimal configuration mode.</span></span> <span data-ttu-id="f23ed-113">否则，SQL Server 代理服务将使用该连接从而使其阻塞。</span><span class="sxs-lookup"><span data-stu-id="f23ed-113">Otherwise, the SQL Server Agent service uses the connection, thereby blocking it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f23ed-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f23ed-114">See Also</span></span>  
 <span data-ttu-id="f23ed-115">[启动、停止或暂停 SQL Server 代理服务](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md) </span><span class="sxs-lookup"><span data-stu-id="f23ed-115">[Start, Stop, or Pause the SQL Server Agent Service](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md) </span></span>  
 <span data-ttu-id="f23ed-116">[用于数据库管理员的诊断连接](diagnostic-connection-for-database-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="f23ed-116">[Diagnostic Connection for Database Administrators](diagnostic-connection-for-database-administrators.md) </span></span>  
 <span data-ttu-id="f23ed-117">[sqlcmd 实用工具](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="f23ed-117">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 <span data-ttu-id="f23ed-118">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f23ed-118">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="f23ed-119">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f23ed-119">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="f23ed-120">数据库引擎服务启动选项</span><span class="sxs-lookup"><span data-stu-id="f23ed-120">Database Engine Service Startup Options</span></span>](database-engine-service-startup-options.md)  
  
  
