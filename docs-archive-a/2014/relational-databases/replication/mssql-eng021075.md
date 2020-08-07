---
title: MSSQL_ENG021075 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021075 error
ms.assetid: c8c29543-d1f6-49d5-b6c8-e8c3aa373090
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 20f2428038326681f5f8eb877e5c3017ced30f00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588987"
---
# <a name="mssql_eng021075"></a><span data-ttu-id="10f01-102">MSSQL_ENG021075</span><span class="sxs-lookup"><span data-stu-id="10f01-102">MSSQL_ENG021075</span></span>
    
## <a name="message-details"></a><span data-ttu-id="10f01-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="10f01-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="10f01-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="10f01-104">Product Name</span></span>|<span data-ttu-id="10f01-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="10f01-105">SQL Server</span></span>|  
|<span data-ttu-id="10f01-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="10f01-106">Event ID</span></span>|<span data-ttu-id="10f01-107">21075</span><span class="sxs-lookup"><span data-stu-id="10f01-107">21075</span></span>|  
|<span data-ttu-id="10f01-108">事件源</span><span class="sxs-lookup"><span data-stu-id="10f01-108">Event Source</span></span>|<span data-ttu-id="10f01-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="10f01-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="10f01-110">组件</span><span class="sxs-lookup"><span data-stu-id="10f01-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="10f01-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="10f01-111">Symbolic Name</span></span>||  
|<span data-ttu-id="10f01-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="10f01-112">Message Text</span></span>|<span data-ttu-id="10f01-113">发布 '%s' 的初始快照尚不可用。</span><span class="sxs-lookup"><span data-stu-id="10f01-113">The initial snapshot for publication '%s' is not yet available.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="10f01-114">说明</span><span class="sxs-lookup"><span data-stu-id="10f01-114">Explanation</span></span>  
 <span data-ttu-id="10f01-115">如果在快照代理完成生成快照的过程之前启动分发代理或合并代理，便会引发错误 MSSQL_ENG021075。</span><span class="sxs-lookup"><span data-stu-id="10f01-115">Error MSSQL_ENG021075 is raised if the Distribution Agent or Merge Agent is started before the Snapshot Agent has finished generating the snapshot.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="10f01-116">用户操作</span><span class="sxs-lookup"><span data-stu-id="10f01-116">User Action</span></span>  
 <span data-ttu-id="10f01-117">如果自创建订阅后或者上次选择重新初始化订阅后一直未启动发布的快照代理，则请启动该快照代理并使其在启动分发代理或合并代理前完成。</span><span class="sxs-lookup"><span data-stu-id="10f01-117">If the Snapshot Agent for the publication has not been started since the subscription was created, or if it has not been started since the last time you chose to reinitialize the subscription, start the Snapshot Agent and let it complete before starting the Distribution Agent or Merge Agent.</span></span> <span data-ttu-id="10f01-118">有关详细信息，请参阅[创建并应用快照](create-and-apply-the-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="10f01-118">For more information, see [Create and Apply the Snapshot](create-and-apply-the-snapshot.md).</span></span>  
  
 <span data-ttu-id="10f01-119">如果快照代理没有完成，请检查快照代理历史记录以查找错误并将其消除。</span><span class="sxs-lookup"><span data-stu-id="10f01-119">If the Snapshot Agent does not complete, check the Snapshot Agent history for errors and address them.</span></span> <span data-ttu-id="10f01-120">有关在复制监视器中查看代理状态和错误详细资料的信息，请参阅[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="10f01-120">For information about viewing agent status and error details in Replication Monitor, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="10f01-121">如果错误继续出现，请增加代理的日志记录并指定日志的输出文件。</span><span class="sxs-lookup"><span data-stu-id="10f01-121">If the error continues to occur, increase the logging of the agent and specify an output file for the log.</span></span> <span data-ttu-id="10f01-122">此操作可能会提供找到该错误和/或其他错误消息的步骤，具体取决于错误的上下文。</span><span class="sxs-lookup"><span data-stu-id="10f01-122">Depending on the context of the error, this could provide the steps leading up to the error and/or additional error messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10f01-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10f01-123">See Also</span></span>  
 [<span data-ttu-id="10f01-124">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="10f01-124">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
