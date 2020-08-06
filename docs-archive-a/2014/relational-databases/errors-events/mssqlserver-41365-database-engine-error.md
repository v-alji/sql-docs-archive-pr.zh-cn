---
title: MSSQLSERVER_41365 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41365 (Database Engine error)
ms.assetid: 4fc7ec15-b722-4e3d-b7f9-3d39d171e96e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1382a6395f1929a5d5552113e07376bcbf80bf35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587840"
---
# <a name="mssqlserver_41365"></a><span data-ttu-id="35b20-102">MSSQLSERVER_41365</span><span class="sxs-lookup"><span data-stu-id="35b20-102">MSSQLSERVER_41365</span></span>
    
## <a name="details"></a><span data-ttu-id="35b20-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="35b20-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="35b20-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="35b20-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="35b20-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="35b20-105">Event ID</span></span>|<span data-ttu-id="35b20-106">41365</span><span class="sxs-lookup"><span data-stu-id="35b20-106">41365</span></span>|  
|<span data-ttu-id="35b20-107">事件源</span><span class="sxs-lookup"><span data-stu-id="35b20-107">Event Source</span></span>|<span data-ttu-id="35b20-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="35b20-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="35b20-109">组件</span><span class="sxs-lookup"><span data-stu-id="35b20-109">Component</span></span>|<span data-ttu-id="35b20-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="35b20-110">SQLEngine</span></span>|  
|<span data-ttu-id="35b20-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="35b20-111">Symbolic Name</span></span>|<span data-ttu-id="35b20-112">HK_MERGE_SCHEDULE_ERROR</span><span class="sxs-lookup"><span data-stu-id="35b20-112">HK_MERGE_SCHEDULE_ERROR</span></span>|  
|<span data-ttu-id="35b20-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="35b20-113">Message Text</span></span>|<span data-ttu-id="35b20-114">未计划数据库 %.\*ls 事务范围 [%ld，%ld] 的合并要求。</span><span class="sxs-lookup"><span data-stu-id="35b20-114">Merge request for transaction range [%ld, %ld] on database %.\*ls was not scheduled.</span></span> <span data-ttu-id="35b20-115">表示范围的检查点文件对合并不可用或是正在进行的合并的一部分。</span><span class="sxs-lookup"><span data-stu-id="35b20-115">The checkpoint files representing the range are either not available for merge or part of an ongoing merge.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="35b20-116">说明</span><span class="sxs-lookup"><span data-stu-id="35b20-116">Explanation</span></span>  
 <span data-ttu-id="35b20-117">表示范围的检查点文件对合并不可用或是正在进行的合并的一部分。</span><span class="sxs-lookup"><span data-stu-id="35b20-117">The checkpoint files representing the range are either not available for merge or part of an ongoing merge.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="35b20-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="35b20-118">User Action</span></span>  
 <span data-ttu-id="35b20-119">为合并提供更好的事务范围/等待，然后再次发出同一请求。</span><span class="sxs-lookup"><span data-stu-id="35b20-119">Provide a better transaction range for merge/wait before issuing the same request again.</span></span> <span data-ttu-id="35b20-120">有关详细信息，请参阅[内存中 OLTP&#40;内存中优化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="35b20-120">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35b20-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="35b20-121">See Also</span></span>  
 [<span data-ttu-id="35b20-122">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="35b20-122">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
