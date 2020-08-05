---
title: MSSQLSERVER_41302 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41302 (Database Engine error)
ms.assetid: 01e75618-afec-4232-ba68-93ab7bc31003
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 751dac91378c002a7e6c6c619ddaf12be8173400
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580768"
---
# <a name="mssqlserver_41302"></a><span data-ttu-id="91c3c-102">MSSQLSERVER_41302</span><span class="sxs-lookup"><span data-stu-id="91c3c-102">MSSQLSERVER_41302</span></span>
    
## <a name="details"></a><span data-ttu-id="91c3c-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="91c3c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="91c3c-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="91c3c-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="91c3c-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="91c3c-105">Event ID</span></span>|<span data-ttu-id="91c3c-106">41302</span><span class="sxs-lookup"><span data-stu-id="91c3c-106">41302</span></span>|  
|<span data-ttu-id="91c3c-107">事件源</span><span class="sxs-lookup"><span data-stu-id="91c3c-107">Event Source</span></span>|<span data-ttu-id="91c3c-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="91c3c-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="91c3c-109">组件</span><span class="sxs-lookup"><span data-stu-id="91c3c-109">Component</span></span>|<span data-ttu-id="91c3c-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="91c3c-110">SQLEngine</span></span>|  
|<span data-ttu-id="91c3c-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="91c3c-111">Symbolic Name</span></span>|<span data-ttu-id="91c3c-112">WRITE_WRITE_CONFLICT</span><span class="sxs-lookup"><span data-stu-id="91c3c-112">WRITE_WRITE_CONFLICT</span></span>|  
|<span data-ttu-id="91c3c-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="91c3c-113">Message Text</span></span>|<span data-ttu-id="91c3c-114">当前事务尝试更新自该事务启动后已更新的记录。</span><span class="sxs-lookup"><span data-stu-id="91c3c-114">The current transaction attempted to update a record that has been updated since this transaction started.</span></span> <span data-ttu-id="91c3c-115">该事务已中止。</span><span class="sxs-lookup"><span data-stu-id="91c3c-115">The transaction was aborted.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="91c3c-116">说明</span><span class="sxs-lookup"><span data-stu-id="91c3c-116">Explanation</span></span>  
 <span data-ttu-id="91c3c-117">事务遇到写/写冲突，语句已终止。</span><span class="sxs-lookup"><span data-stu-id="91c3c-117">The transaction encountered a write/write conflict and the statement terminated.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="91c3c-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="91c3c-118">User Action</span></span>  
 <span data-ttu-id="91c3c-119">稍后在其他事务中重试该操作。</span><span class="sxs-lookup"><span data-stu-id="91c3c-119">Retry the operation later in a different transaction.</span></span> <span data-ttu-id="91c3c-120">有关详细信息，请参阅[内存中 OLTP&#40;内存中优化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="91c3c-120">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91c3c-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="91c3c-121">See Also</span></span>  
 [<span data-ttu-id="91c3c-122">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="91c3c-122">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
