---
title: 管理工具命令行选项（Distributed Replay 实用工具）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: c01b0ed3-67e4-4561-92d2-a8fbb086aca8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 506be071f44937d82902585e5a0621212083dfa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587657"
---
# <a name="administration-tool-command-line-options-distributed-replay-utility"></a><span data-ttu-id="dd4a7-102">管理工具命令行选项（分布式重播实用工具）</span><span class="sxs-lookup"><span data-stu-id="dd4a7-102">Administration Tool Command-line Options (Distributed Replay Utility)</span></span>
  <span data-ttu-id="dd4a7-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 管理工具 `DReplay.exe` 是一个命令行工具，可用于与 Distributed Replay 控制器进行通信。</span><span class="sxs-lookup"><span data-stu-id="dd4a7-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay administration tool, `DReplay.exe`, is a command-line tool that you can use to communicate with the distributed replay controller.</span></span> <span data-ttu-id="dd4a7-104">可使用此管理工具在控制器上启动、监视和取消操作。</span><span class="sxs-lookup"><span data-stu-id="dd4a7-104">Use the administration tool to initiate, monitor, and cancel operations on the controller.</span></span>  
  
 <span data-ttu-id="dd4a7-105">![主题链接图标](../../database-engine/media/topic-link.gif "“主题链接”图标") 有关与此管理工具语法结合使用的语法约定的详细信息，请参阅 [Transact-SQL 语法约定 (Transact-SQL)](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="dd4a7-105">![Topic link icon](../../database-engine/media/topic-link.gif "Topic link icon") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd4a7-106">语法</span><span class="sxs-lookup"><span data-stu-id="dd4a7-106">Syntax</span></span>  
  
```  
  
      dreplay {preprocess|replay|status|cancel} [options] [-?]}  
  
Usage:  
  
  dreplay preprocess [-mcontroller] -iinput_trace_file  
    -dcontroller_working_dir [-cconfig_file] [-fstatus_interval]  
  
  dreplay replay [-mcontroller] -dcontroller_working_dir [-o]  
    [-starget_server] -wclients [-cconfig_file]  
    [-fstatus_interval]  
  
  dreplay status [-mcontroller] [-fstatus_interval]  
  
  dreplay cancel [-mcontroller] [-q]   
```  
  
## <a name="remarks"></a><span data-ttu-id="dd4a7-107">备注</span><span class="sxs-lookup"><span data-stu-id="dd4a7-107">Remarks</span></span>  
 <span data-ttu-id="dd4a7-108">您可以使用 `DReplay.exe` 发出以下命令行选项：</span><span class="sxs-lookup"><span data-stu-id="dd4a7-108">You can issue the following command-line options with `DReplay.exe`:</span></span>  
  
 <span data-ttu-id="dd4a7-109">**preprocess**</span><span class="sxs-lookup"><span data-stu-id="dd4a7-109">**preprocess**</span></span>  
 <span data-ttu-id="dd4a7-110">启动预处理阶段。</span><span class="sxs-lookup"><span data-stu-id="dd4a7-110">Initiates the preprocess stage.</span></span> <span data-ttu-id="dd4a7-111">控制器准备您从生产环境中捕获的输入跟踪数据，以便对目标服务器进行重播。</span><span class="sxs-lookup"><span data-stu-id="dd4a7-111">The controller prepares the input trace data, which you captured from the production environment, for replay against the target server.</span></span>  
  
 <span data-ttu-id="dd4a7-112">**replay**</span><span class="sxs-lookup"><span data-stu-id="dd4a7-112">**replay**</span></span>  
 <span data-ttu-id="dd4a7-113">启动事件重播阶段。</span><span class="sxs-lookup"><span data-stu-id="dd4a7-113">Initiates the event replay stage.</span></span> <span data-ttu-id="dd4a7-114">控制器将重播数据调度到指定客户端，启动分布式重播并同步客户端。</span><span class="sxs-lookup"><span data-stu-id="dd4a7-114">The controller dispatches replay data to the specified clients, launches the distributed replay, and synchronizes the clients.</span></span> <span data-ttu-id="dd4a7-115">每个选定的客户端可以选择记录重播活动并在本地保存结果跟踪文件。</span><span class="sxs-lookup"><span data-stu-id="dd4a7-115">Optionally, each client that was selected records the replay activity and saves result trace files locally.</span></span>  
  
 <span data-ttu-id="dd4a7-116">**status**</span><span class="sxs-lookup"><span data-stu-id="dd4a7-116">**status**</span></span>  
 <span data-ttu-id="dd4a7-117">查询控制器并显示当前状态。</span><span class="sxs-lookup"><span data-stu-id="dd4a7-117">Queries the controller and displays the current status.</span></span>  
  
 <span data-ttu-id="dd4a7-118">**cancel**</span><span class="sxs-lookup"><span data-stu-id="dd4a7-118">**cancel**</span></span>  
 <span data-ttu-id="dd4a7-119">取消正在控制器上运行的当前操作。</span><span class="sxs-lookup"><span data-stu-id="dd4a7-119">Cancels the current operation that is running on the controller.</span></span>  
  
 <span data-ttu-id="dd4a7-120">对于包含命令参数和示例的详细语法信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="dd4a7-120">For detailed syntax information that includes the command arguments and examples, see the following topics:</span></span>  
  
-   [<span data-ttu-id="dd4a7-121">预处理选项（分布式重播管理工具）</span><span class="sxs-lookup"><span data-stu-id="dd4a7-121">Preprocess Option &#40;Distributed Replay Administration Tool&#41;</span></span>](preprocess-option-distributed-replay-administration-tool.md)  
  
-   [<span data-ttu-id="dd4a7-122">重播选项（分布式重播管理工具）</span><span class="sxs-lookup"><span data-stu-id="dd4a7-122">Replay Option &#40;Distributed Replay Administration Tool&#41;</span></span>](replay-option-distributed-replay-administration-tool.md)  
  
-   [<span data-ttu-id="dd4a7-123">状态选项（分布式重播管理工具）</span><span class="sxs-lookup"><span data-stu-id="dd4a7-123">Status Option &#40;Distributed Replay Administration Tool&#41;</span></span>](status-option-distributed-replay-administration-tool.md)  
  
-   [<span data-ttu-id="dd4a7-124">取消选项（分布式重播管理工具）</span><span class="sxs-lookup"><span data-stu-id="dd4a7-124">Cancel Option &#40;Distributed Replay Administration Tool&#41;</span></span>](cancel-option-distributed-replay-administration-tool.md)  
  
 <span data-ttu-id="dd4a7-125">RPC 将作为 RPC 而非语言事件进行重播。</span><span class="sxs-lookup"><span data-stu-id="dd4a7-125">RPCs are replayed as RPCs and not as language events.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="dd4a7-126">权限</span><span class="sxs-lookup"><span data-stu-id="dd4a7-126">Permissions</span></span>  
 <span data-ttu-id="dd4a7-127">您必须作为交互用户、本地用户或域用户帐户运行管理工具。</span><span class="sxs-lookup"><span data-stu-id="dd4a7-127">You must run the administration tool as an interactive user, as either a local user or a domain user account.</span></span> <span data-ttu-id="dd4a7-128">若要使用本地用户帐户，管理工具和控制器必须在同一台计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="dd4a7-128">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>  
  
 <span data-ttu-id="dd4a7-129">有关详细信息，请参阅 [Distributed Replay Security](distributed-replay-security.md)。</span><span class="sxs-lookup"><span data-stu-id="dd4a7-129">For more information, see [Distributed Replay Security](distributed-replay-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd4a7-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dd4a7-130">See Also</span></span>  
 [<span data-ttu-id="dd4a7-131">SQL Server 分布式重播</span><span class="sxs-lookup"><span data-stu-id="dd4a7-131">SQL Server Distributed Replay</span></span>](sql-server-distributed-replay.md)  
  
  
