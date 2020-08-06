---
title: MSSQLSERVER_41305 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41305 (Database Engine error)
ms.assetid: a96e5083-ff97-4003-a900-07942454151d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9c00e20ec220d7fcee0da4e99c2ef35817dae67f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587841"
---
# <a name="mssqlserver_41305"></a><span data-ttu-id="49311-102">MSSQLSERVER_41305</span><span class="sxs-lookup"><span data-stu-id="49311-102">MSSQLSERVER_41305</span></span>
    
## <a name="details"></a><span data-ttu-id="49311-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="49311-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="49311-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="49311-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="49311-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="49311-105">Event ID</span></span>|<span data-ttu-id="49311-106">41305</span><span class="sxs-lookup"><span data-stu-id="49311-106">41305</span></span>|  
|<span data-ttu-id="49311-107">事件源</span><span class="sxs-lookup"><span data-stu-id="49311-107">Event Source</span></span>|<span data-ttu-id="49311-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="49311-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="49311-109">组件</span><span class="sxs-lookup"><span data-stu-id="49311-109">Component</span></span>|<span data-ttu-id="49311-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="49311-110">SQLEngine</span></span>|  
|<span data-ttu-id="49311-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="49311-111">Symbolic Name</span></span>|<span data-ttu-id="49311-112">HK_TX_COMMIT_RR_VALIDATION</span><span class="sxs-lookup"><span data-stu-id="49311-112">HK_TX_COMMIT_RR_VALIDATION</span></span>|  
|<span data-ttu-id="49311-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="49311-113">Message Text</span></span>|<span data-ttu-id="49311-114">因某个可重复读取验证失败，当前事务无法提交。</span><span class="sxs-lookup"><span data-stu-id="49311-114">The current transaction failed to commit due to a repeatable read validation failure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="49311-115">说明</span><span class="sxs-lookup"><span data-stu-id="49311-115">Explanation</span></span>  
 <span data-ttu-id="49311-116">事务遇到验证错误，已失败。</span><span class="sxs-lookup"><span data-stu-id="49311-116">The transaction encountered a validation failure and is now doomed.</span></span>  
  
 <span data-ttu-id="49311-117">有关详细信息，请参阅[内存中 OLTP&#40;内存中优化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="49311-117">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="49311-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="49311-118">User Action</span></span>  
 <span data-ttu-id="49311-119">重试失败的事务。</span><span class="sxs-lookup"><span data-stu-id="49311-119">Retry the failed transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49311-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="49311-120">See Also</span></span>  
 [<span data-ttu-id="49311-121">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="49311-121">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
