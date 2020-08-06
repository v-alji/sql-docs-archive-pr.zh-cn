---
title: MSSQLSERVER_41325 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41325 (Database Engine error)
ms.assetid: 97c6a8bb-139a-44f3-9ed5-f46d047e8ed3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a512d7db6529876259d889d04aabf3d07747cafe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689920"
---
# <a name="mssqlserver_41325"></a><span data-ttu-id="2143c-102">MSSQLSERVER_41325</span><span class="sxs-lookup"><span data-stu-id="2143c-102">MSSQLSERVER_41325</span></span>
    
## <a name="details"></a><span data-ttu-id="2143c-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="2143c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2143c-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="2143c-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="2143c-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="2143c-105">Event ID</span></span>|<span data-ttu-id="2143c-106">41325</span><span class="sxs-lookup"><span data-stu-id="2143c-106">41325</span></span>|  
|<span data-ttu-id="2143c-107">事件源</span><span class="sxs-lookup"><span data-stu-id="2143c-107">Event Source</span></span>|<span data-ttu-id="2143c-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2143c-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2143c-109">组件</span><span class="sxs-lookup"><span data-stu-id="2143c-109">Component</span></span>|<span data-ttu-id="2143c-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2143c-110">SQLEngine</span></span>|  
|<span data-ttu-id="2143c-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="2143c-111">Symbolic Name</span></span>|<span data-ttu-id="2143c-112">HK_TX_COMMIT_SR_VALIDATION</span><span class="sxs-lookup"><span data-stu-id="2143c-112">HK_TX_COMMIT_SR_VALIDATION</span></span>|  
|<span data-ttu-id="2143c-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="2143c-113">Message Text</span></span>|<span data-ttu-id="2143c-114">因某个序列化读取验证失败，当前事务无法提交。</span><span class="sxs-lookup"><span data-stu-id="2143c-114">The current transaction failed to commit due to a serializable validation failure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2143c-115">说明</span><span class="sxs-lookup"><span data-stu-id="2143c-115">Explanation</span></span>  
 <span data-ttu-id="2143c-116">事务遇到验证错误，已失败。</span><span class="sxs-lookup"><span data-stu-id="2143c-116">The transaction encountered a validation failure and is now doomed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2143c-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="2143c-117">User Action</span></span>  
 <span data-ttu-id="2143c-118">重试失败的事务。</span><span class="sxs-lookup"><span data-stu-id="2143c-118">Retry the failed transaction.</span></span> <span data-ttu-id="2143c-119">有关详细信息，请参阅[内存中 OLTP&#40;内存中优化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="2143c-119">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2143c-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2143c-120">See Also</span></span>  
 [<span data-ttu-id="2143c-121">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="2143c-121">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
