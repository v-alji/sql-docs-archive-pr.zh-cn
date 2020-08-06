---
title: MSSQLSERVER_17883 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17883 (Database Engine error)
ms.assetid: adaf1c04-e397-4a69-90b8-9353a37277ea
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 46488fb6f7adac2c1109871f2aad4c79352829ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687924"
---
# <a name="mssqlserver_17883"></a><span data-ttu-id="da09b-102">MSSQLSERVER_17883</span><span class="sxs-lookup"><span data-stu-id="da09b-102">MSSQLSERVER_17883</span></span>
    
## <a name="details"></a><span data-ttu-id="da09b-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="da09b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="da09b-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="da09b-104">Product Name</span></span>|<span data-ttu-id="da09b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="da09b-105">SQL Server</span></span>|  
|<span data-ttu-id="da09b-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="da09b-106">Event ID</span></span>|<span data-ttu-id="da09b-107">17883</span><span class="sxs-lookup"><span data-stu-id="da09b-107">17883</span></span>|  
|<span data-ttu-id="da09b-108">事件源</span><span class="sxs-lookup"><span data-stu-id="da09b-108">Event Source</span></span>|<span data-ttu-id="da09b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="da09b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="da09b-110">组件</span><span class="sxs-lookup"><span data-stu-id="da09b-110">Component</span></span>|<span data-ttu-id="da09b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="da09b-111">SQLEngine</span></span>|  
|<span data-ttu-id="da09b-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="da09b-112">Symbolic Name</span></span>|<span data-ttu-id="da09b-113">SRV_SCHEDULER_NONYIELDING</span><span class="sxs-lookup"><span data-stu-id="da09b-113">SRV_SCHEDULER_NONYIELDING</span></span>|  
|<span data-ttu-id="da09b-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="da09b-114">Message Text</span></span>|<span data-ttu-id="da09b-115">计划程序 %ld 的进程 %ld:%ld:%ld (0x%lx)工作线程 0x%p 似乎无法完成。</span><span class="sxs-lookup"><span data-stu-id="da09b-115">Process %ld:%ld:%ld (0x%lx) Worker 0x%p appears to be non-yielding on Scheduler %ld.</span></span> <span data-ttu-id="da09b-116">线程创建时间: %I64d。</span><span class="sxs-lookup"><span data-stu-id="da09b-116">Thread creation time: %I64d.</span></span> <span data-ttu-id="da09b-117">线程占用 CPU 的近似时间: 内核 %I64d 毫秒，用户 %I64d 毫秒。</span><span class="sxs-lookup"><span data-stu-id="da09b-117">Approx Thread CPU Used: kernel %I64d ms, user %I64d ms.</span></span> <span data-ttu-id="da09b-118">进程使用率 %d%%。</span><span class="sxs-lookup"><span data-stu-id="da09b-118">Process Utilization %d%%.</span></span> <span data-ttu-id="da09b-119">系统空闲率 %d%%。</span><span class="sxs-lookup"><span data-stu-id="da09b-119">System Idle %d%%.</span></span> <span data-ttu-id="da09b-120">间隔: %I64d 毫秒。</span><span class="sxs-lookup"><span data-stu-id="da09b-120">Interval: %I64d ms.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="da09b-121">说明</span><span class="sxs-lookup"><span data-stu-id="da09b-121">Explanation</span></span>  
 <span data-ttu-id="da09b-122">指示计划程序上的某个线程可能出现问题，而无法完成。</span><span class="sxs-lookup"><span data-stu-id="da09b-122">Indicates that there is a possible problem with a thread not yielding on a scheduler.</span></span>  <span data-ttu-id="da09b-123">这可能是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的错误或者 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 没有足够的执行周期而引起的。</span><span class="sxs-lookup"><span data-stu-id="da09b-123">This could be caused by a bug in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not getting enough cycles to execute.</span></span>  <span data-ttu-id="da09b-124">如果该线程最终完成，此错误可能会消失。</span><span class="sxs-lookup"><span data-stu-id="da09b-124">This error could go away if the thread eventually yields.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="da09b-125">用户操作</span><span class="sxs-lookup"><span data-stu-id="da09b-125">User Action</span></span>  
 <span data-ttu-id="da09b-126">如果系统上的负载过多，请减少负载，否则请与 Microsoft 客户支持服务部门联系。</span><span class="sxs-lookup"><span data-stu-id="da09b-126">If excessive load on system reduce load otherwise contact Microsoft Customer Support Services.</span></span>  
  
  
