---
title: MSSQL_REPL027056 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL027056 error
ms.assetid: 92d62f3c-b8ae-482e-a348-2e9a8ee9786e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 44fb130321ec54c39559d52e493cc8f3424172fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691677"
---
# <a name="mssql_repl027056"></a><span data-ttu-id="3735d-102">MSSQL_REPL027056</span><span class="sxs-lookup"><span data-stu-id="3735d-102">MSSQL_REPL027056</span></span>
    
## <a name="message-details"></a><span data-ttu-id="3735d-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="3735d-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3735d-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="3735d-104">Product Name</span></span>|<span data-ttu-id="3735d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3735d-105">SQL Server</span></span>|  
|<span data-ttu-id="3735d-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="3735d-106">Event ID</span></span>|<span data-ttu-id="3735d-107">27056</span><span class="sxs-lookup"><span data-stu-id="3735d-107">27056</span></span>|  
|<span data-ttu-id="3735d-108">事件源</span><span class="sxs-lookup"><span data-stu-id="3735d-108">Event Source</span></span>|<span data-ttu-id="3735d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3735d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3735d-110">组件</span><span class="sxs-lookup"><span data-stu-id="3735d-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="3735d-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="3735d-111">Symbolic Name</span></span>||  
|<span data-ttu-id="3735d-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="3735d-112">Message Text</span></span>|<span data-ttu-id="3735d-113">合并进程无法更改“%1”上的生成历史记录。</span><span class="sxs-lookup"><span data-stu-id="3735d-113">The merge process was unable to change generation history at the '%1'.</span></span> <span data-ttu-id="3735d-114">进行故障排除时，请使用详细的历史日志记录来重新启动同步，并指定要写入的输出文件。</span><span class="sxs-lookup"><span data-stu-id="3735d-114">When troubleshooting, restart the synchronization with verbose history logging and specify an output file to which to write.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3735d-115">说明</span><span class="sxs-lookup"><span data-stu-id="3735d-115">Explanation</span></span>  
 <span data-ttu-id="3735d-116">此错误通常是由增长过大的合并复制系统表中的争用所引起。</span><span class="sxs-lookup"><span data-stu-id="3735d-116">This error is typically raised as a result of contention in merge replication system tables that have grown excessively large.</span></span> <span data-ttu-id="3735d-117">大型系统表通常是由于发布保持期过长造成的，因为在到达保持期之前，元数据必须一直存储在这些表中。</span><span class="sxs-lookup"><span data-stu-id="3735d-117">Large system tables are typically caused by a long publication retention period, because metadata must be stored in these tables until the retention period is reached.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3735d-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="3735d-118">User Action</span></span>  
 <span data-ttu-id="3735d-119">**若要解决此问题：**</span><span class="sxs-lookup"><span data-stu-id="3735d-119">**To resolve the issue:**</span></span>  
  
1.  <span data-ttu-id="3735d-120">减小合并代理的 -**DownloadGenerationsPerBatch** 和 **-UploadGenerationsPerBatch** 参数的值，使进程在你解决引起错误的潜在问题时能够继续执行。</span><span class="sxs-lookup"><span data-stu-id="3735d-120">Decrease the value of the -**DownloadGenerationsPerBatch** and **-UploadGenerationsPerBatch** parameters for the Merge Agent to allow processing to continue while you address the underlying issue causing the error.</span></span> <span data-ttu-id="3735d-121">代理参数可以在代理配置文件和命令行中指定。</span><span class="sxs-lookup"><span data-stu-id="3735d-121">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="3735d-122">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="3735d-122">For more information, see:</span></span>  
  
    -   [<span data-ttu-id="3735d-123">处理复制代理配置文件</span><span class="sxs-lookup"><span data-stu-id="3735d-123">Work with Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
    -   [<span data-ttu-id="3735d-124">查看和修改复制代理命令提示符参数 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3735d-124">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   <span data-ttu-id="3735d-125">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md)的最小和最大内存量。</span><span class="sxs-lookup"><span data-stu-id="3735d-125">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
2.  <span data-ttu-id="3735d-126">为发布保持期指定尽可能低的设置。</span><span class="sxs-lookup"><span data-stu-id="3735d-126">Specify the lowest setting possible for the publication retention period.</span></span> <span data-ttu-id="3735d-127">有关详细信息，请参阅 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="3735d-127">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
3.  <span data-ttu-id="3735d-128">在合并复制维护过程中，应不定期检查以下与合并复制相关联的系统表的增长情况： **MSmerge_contents**、 **MSmerge_genhistory**、 **MSmerge_tombstone**、 **MSmerge_current_partition_mappings**、 **MSmerge_past_partition_mappings**。</span><span class="sxs-lookup"><span data-stu-id="3735d-128">As part of maintenance for merge replication, occasionally check the growth of the system tables associated with merge replication: **MSmerge_contents**, **MSmerge_genhistory**, and **MSmerge_tombstone**, **MSmerge_current_partition_mappings**, and **MSmerge_past_partition_mappings**.</span></span> <span data-ttu-id="3735d-129">定期对这些表重建索引。</span><span class="sxs-lookup"><span data-stu-id="3735d-129">Periodically re-index these tables.</span></span> <span data-ttu-id="3735d-130">有关详细信息，请参阅 [重新组织和重新生成索引](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="3735d-130">For more information, see [Reorganize and Rebuild Indexes](../indexes/indexes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3735d-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3735d-131">See Also</span></span>  
 [<span data-ttu-id="3735d-132">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="3735d-132">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
