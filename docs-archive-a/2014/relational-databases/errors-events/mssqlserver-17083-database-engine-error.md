---
title: MSSQLSERVER_17083 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17083 (Database Engine error)
ms.assetid: 6c83737d-0531-4fd9-88f6-2da5a150532d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 598cf9b0182178aa13a6d8b965ac10bedaaf5d15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589634"
---
# <a name="mssqlserver_17083"></a><span data-ttu-id="ffe64-102">MSSQLSERVER_17083</span><span class="sxs-lookup"><span data-stu-id="ffe64-102">MSSQLSERVER_17083</span></span>
    
## <a name="details"></a><span data-ttu-id="ffe64-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="ffe64-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ffe64-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="ffe64-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="ffe64-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="ffe64-105">Event ID</span></span>|<span data-ttu-id="ffe64-106">17083</span><span class="sxs-lookup"><span data-stu-id="ffe64-106">17083</span></span>|  
|<span data-ttu-id="ffe64-107">事件源</span><span class="sxs-lookup"><span data-stu-id="ffe64-107">Event Source</span></span>|<span data-ttu-id="ffe64-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ffe64-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ffe64-109">组件</span><span class="sxs-lookup"><span data-stu-id="ffe64-109">Component</span></span>|<span data-ttu-id="ffe64-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ffe64-110">SQLEngine</span></span>|  
|<span data-ttu-id="ffe64-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="ffe64-111">Symbolic Name</span></span>|<span data-ttu-id="ffe64-112">P3_HEKATON_NOT_ATOMIC</span><span class="sxs-lookup"><span data-stu-id="ffe64-112">P3_HEKATON_NOT_ATOMIC</span></span>|  
|<span data-ttu-id="ffe64-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="ffe64-113">Message Text</span></span>|<span data-ttu-id="ffe64-114">本机编译存储过程的正文必须是 ATOMIC 块。</span><span class="sxs-lookup"><span data-stu-id="ffe64-114">The body of a natively compiled stored procedure must be an ATOMIC block.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ffe64-115">说明</span><span class="sxs-lookup"><span data-stu-id="ffe64-115">Explanation</span></span>  
 <span data-ttu-id="ffe64-116">本机编译存储过程的正文没有 ATOMIC 块。</span><span class="sxs-lookup"><span data-stu-id="ffe64-116">The body of a natively compiled stored procedure did not have an ATOMIC block.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ffe64-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="ffe64-117">User Action</span></span>  
 <span data-ttu-id="ffe64-118">本机编译存储过程必须包含 ATOMIC 块。</span><span class="sxs-lookup"><span data-stu-id="ffe64-118">A natively compiled stored procedure must contain an ATOMIC block.</span></span> <span data-ttu-id="ffe64-119">例如：</span><span class="sxs-lookup"><span data-stu-id="ffe64-119">For example:</span></span>  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE= N'us_english')  
```  
  
 <span data-ttu-id="ffe64-120">有关详细信息，请参阅[内存中 OLTP&#40;内存中优化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="ffe64-120">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffe64-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ffe64-121">See Also</span></span>  
 [<span data-ttu-id="ffe64-122">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="ffe64-122">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
