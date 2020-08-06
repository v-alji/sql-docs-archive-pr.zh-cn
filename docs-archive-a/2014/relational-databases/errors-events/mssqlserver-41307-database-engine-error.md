---
title: MSSQLSERVER_41307 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41307 (Database Engine error)
ms.assetid: 56f56410-b07d-4379-b01c-702c95761070
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 98407a65d5529fd73bccc638df11167131bd9f8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690624"
---
# <a name="mssqlserver_41307"></a><span data-ttu-id="8e3b3-102">MSSQLSERVER_41307</span><span class="sxs-lookup"><span data-stu-id="8e3b3-102">MSSQLSERVER_41307</span></span>
    
## <a name="details"></a><span data-ttu-id="8e3b3-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="8e3b3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8e3b3-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="8e3b3-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="8e3b3-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="8e3b3-105">Event ID</span></span>|<span data-ttu-id="8e3b3-106">41307</span><span class="sxs-lookup"><span data-stu-id="8e3b3-106">41307</span></span>|  
|<span data-ttu-id="8e3b3-107">事件源</span><span class="sxs-lookup"><span data-stu-id="8e3b3-107">Event Source</span></span>|<span data-ttu-id="8e3b3-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8e3b3-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8e3b3-109">组件</span><span class="sxs-lookup"><span data-stu-id="8e3b3-109">Component</span></span>|<span data-ttu-id="8e3b3-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8e3b3-110">SQLEngine</span></span>|  
|<span data-ttu-id="8e3b3-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="8e3b3-111">Symbolic Name</span></span>|<span data-ttu-id="8e3b3-112">HK_HEKATON_ROW_LIMIT</span><span class="sxs-lookup"><span data-stu-id="8e3b3-112">HK_HEKATON_ROW_LIMIT</span></span>|  
|<span data-ttu-id="8e3b3-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="8e3b3-113">Message Text</span></span>|<span data-ttu-id="8e3b3-114">已超出了内存优化表 *number* 字节的行大小限制。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-114">The row size limit of *number* bytes for memory optimized tables has been exceeded.</span></span> <span data-ttu-id="8e3b3-115">请简化表定义。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-115">Please simplify the table definition.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8e3b3-116">说明</span><span class="sxs-lookup"><span data-stu-id="8e3b3-116">Explanation</span></span>  
 <span data-ttu-id="8e3b3-117">内存优化表的行大小限制为 8,060 字节。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-117">The row size limit for memory optimized tables is 8,060 bytes.</span></span> <span data-ttu-id="8e3b3-118">有关详细信息，请参阅 [内存优化表中的表和行大小](../in-memory-oltp/memory-optimized-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-118">For more information, see [Table and Row Size in Memory-Optimized Tables](../in-memory-oltp/memory-optimized-tables.md).</span></span> <span data-ttu-id="8e3b3-119">有关详细信息，请参阅[内存中 OLTP&#40;内存中优化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="8e3b3-119">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e3b3-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8e3b3-120">See Also</span></span>  
 [<span data-ttu-id="8e3b3-121">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="8e3b3-121">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
