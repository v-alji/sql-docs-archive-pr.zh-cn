---
title: MSSQLSERVER_17084 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17084 (Database Engine error)
ms.assetid: e579d104-3307-4edd-8587-b14ecbc02ed9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 59b0fc3e0884ddd89809767a068b937b5c145f9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589629"
---
# <a name="mssqlserver_17084"></a><span data-ttu-id="6e27a-102">MSSQLSERVER_17084</span><span class="sxs-lookup"><span data-stu-id="6e27a-102">MSSQLSERVER_17084</span></span>
    
## <a name="details"></a><span data-ttu-id="6e27a-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="6e27a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6e27a-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="6e27a-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="6e27a-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="6e27a-105">Event ID</span></span>|<span data-ttu-id="6e27a-106">17084</span><span class="sxs-lookup"><span data-stu-id="6e27a-106">17084</span></span>|  
|<span data-ttu-id="6e27a-107">事件源</span><span class="sxs-lookup"><span data-stu-id="6e27a-107">Event Source</span></span>|<span data-ttu-id="6e27a-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6e27a-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6e27a-109">组件</span><span class="sxs-lookup"><span data-stu-id="6e27a-109">Component</span></span>|<span data-ttu-id="6e27a-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6e27a-110">SQLEngine</span></span>|  
|<span data-ttu-id="6e27a-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="6e27a-111">Symbolic Name</span></span>|<span data-ttu-id="6e27a-112">P3_ATOMIC_WITH_MISSING_OPTION</span><span class="sxs-lookup"><span data-stu-id="6e27a-112">P3_ATOMIC_WITH_MISSING_OPTION</span></span>|  
|<span data-ttu-id="6e27a-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="6e27a-113">Message Text</span></span>|<span data-ttu-id="6e27a-114">BEGIN ATOMIC 语句的 WITH 子句必须为选项“%ls”指定一个值。</span><span class="sxs-lookup"><span data-stu-id="6e27a-114">The WITH clause of BEGIN ATOMIC statement must specify a value for the option '%ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6e27a-115">说明</span><span class="sxs-lookup"><span data-stu-id="6e27a-115">Explanation</span></span>  
 <span data-ttu-id="6e27a-116">BEGIN ATOMIC 语句的 WITH 子句没有为某一选项指定值。</span><span class="sxs-lookup"><span data-stu-id="6e27a-116">The WITH clause of BEGIN ATOMIC statement did not specify a value for an option.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6e27a-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="6e27a-117">User Action</span></span>  
 <span data-ttu-id="6e27a-118">`ATOMIC` 块要求为 `WITH` 选项 `TRANSACTION ISOLATION LEVEL` 和 `LANGUAGE` 提供值。</span><span class="sxs-lookup"><span data-stu-id="6e27a-118">`ATOMIC` blocks require values for the `WITH` options `TRANSACTION ISOLATION LEVEL` and `LANGUAGE`.</span></span> <span data-ttu-id="6e27a-119">例如：</span><span class="sxs-lookup"><span data-stu-id="6e27a-119">For example::</span></span>  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE= N'us_english')  
```  
  
 <span data-ttu-id="6e27a-120">有关详细信息，请参阅[内存中 OLTP&#40;内存中优化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="6e27a-120">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e27a-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6e27a-121">See Also</span></span>  
 [<span data-ttu-id="6e27a-122">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="6e27a-122">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
