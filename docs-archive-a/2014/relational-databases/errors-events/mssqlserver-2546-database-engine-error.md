---
title: MSSQLSERVER_2546 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2546 (Database Engine error)
ms.assetid: c8f0e1b4-c7c4-45f2-9221-746714172313
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5c1c5f64ca0daba413f2b71c05f5b8e57b2d55df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687915"
---
# <a name="mssqlserver_2546"></a><span data-ttu-id="cc9f7-102">MSSQLSERVER_2546</span><span class="sxs-lookup"><span data-stu-id="cc9f7-102">MSSQLSERVER_2546</span></span>
    
## <a name="details"></a><span data-ttu-id="cc9f7-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="cc9f7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cc9f7-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="cc9f7-104">Product Name</span></span>|<span data-ttu-id="cc9f7-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cc9f7-105">SQL Server</span></span>|  
|<span data-ttu-id="cc9f7-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="cc9f7-106">Event ID</span></span>|<span data-ttu-id="cc9f7-107">2546</span><span class="sxs-lookup"><span data-stu-id="cc9f7-107">2546</span></span>|  
|<span data-ttu-id="cc9f7-108">事件源</span><span class="sxs-lookup"><span data-stu-id="cc9f7-108">Event Source</span></span>|<span data-ttu-id="cc9f7-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cc9f7-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cc9f7-110">组件</span><span class="sxs-lookup"><span data-stu-id="cc9f7-110">Component</span></span>|<span data-ttu-id="cc9f7-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="cc9f7-111">SQLEngine</span></span>|  
|<span data-ttu-id="cc9f7-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="cc9f7-112">Symbolic Name</span></span>|<span data-ttu-id="cc9f7-113">DBCC_INDEX_MARKED_DISABLED</span><span class="sxs-lookup"><span data-stu-id="cc9f7-113">DBCC_INDEX_MARKED_DISABLED</span></span>|  
|<span data-ttu-id="cc9f7-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="cc9f7-114">Message Text</span></span>|<span data-ttu-id="cc9f7-115">表 'OBJECT_NAME' 的索引 'INDEX_NAME' 已标记为禁用。</span><span class="sxs-lookup"><span data-stu-id="cc9f7-115">Index 'INDEX_NAME' on table 'OBJECT_NAME' is marked as disabled.</span></span> <span data-ttu-id="cc9f7-116">请重新生成该索引，以使之联机。</span><span class="sxs-lookup"><span data-stu-id="cc9f7-116">Rebuild the index to bring it online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cc9f7-117">说明</span><span class="sxs-lookup"><span data-stu-id="cc9f7-117">Explanation</span></span>  
 <span data-ttu-id="cc9f7-118">指定的索引已标记为离线或禁用。</span><span class="sxs-lookup"><span data-stu-id="cc9f7-118">The specified index is marked as offline or is disabled.</span></span> <span data-ttu-id="cc9f7-119">因此，不能检查该索引。</span><span class="sxs-lookup"><span data-stu-id="cc9f7-119">Therefore, this index cannot be checked.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cc9f7-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="cc9f7-120">User Action</span></span>  
 <span data-ttu-id="cc9f7-121">请使用 ALTER INDEX 重新生成索引。</span><span class="sxs-lookup"><span data-stu-id="cc9f7-121">Rebuild the index by using ALTER INDEX.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc9f7-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cc9f7-122">See Also</span></span>  
 <span data-ttu-id="cc9f7-123">[ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cc9f7-123">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 [<span data-ttu-id="cc9f7-124">重新组织和重新生成索引</span><span class="sxs-lookup"><span data-stu-id="cc9f7-124">Reorganize and Rebuild Indexes</span></span>](../indexes/indexes.md)  
  
  
