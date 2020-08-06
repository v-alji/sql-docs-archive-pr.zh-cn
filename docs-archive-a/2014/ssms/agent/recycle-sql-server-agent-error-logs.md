---
title: 回收 SQL Server 代理错误日志 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.errorlog.recyclesqlagenterrorlogs.f1
ms.assetid: 10bc2dd1-0505-4527-8ec7-d3b4e5d6352b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2b30f0a2ba9a2d861d4a36a86489757cde512fea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591059"
---
# <a name="recycle-sql-server-agent-error-logs"></a><span data-ttu-id="62165-102">回收 SQL Server 代理错误日志</span><span class="sxs-lookup"><span data-stu-id="62165-102">Recycle SQL Server Agent Error Logs</span></span>
  <span data-ttu-id="62165-103">使用此页可以回收 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理错误日志。</span><span class="sxs-lookup"><span data-stu-id="62165-103">Use this page to recycle the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Error Logs.</span></span> <span data-ttu-id="62165-104">回收该日志将关闭当前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理错误日志并启动新的错误日志，而且不会重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务。</span><span class="sxs-lookup"><span data-stu-id="62165-104">Recycling the log closes the current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log and starts a new error log without restarting the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span> <span data-ttu-id="62165-105">注意， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理保留九个最新的错误日志。</span><span class="sxs-lookup"><span data-stu-id="62165-105">Notice that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent maintains the nine most recent error logs.</span></span> <span data-ttu-id="62165-106">如果已经有九个错误日志，则回收错误日志会导致 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理删除最早的错误日志。</span><span class="sxs-lookup"><span data-stu-id="62165-106">If there are already nine error logs present, recycling the error log causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to remove the oldest error log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62165-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62165-107">See Also</span></span>  
 [<span data-ttu-id="62165-108">SQL Server 代理错误日志</span><span class="sxs-lookup"><span data-stu-id="62165-108">SQL Server Agent Error Log</span></span>](sql-server-agent-error-log.md)  
  
  
