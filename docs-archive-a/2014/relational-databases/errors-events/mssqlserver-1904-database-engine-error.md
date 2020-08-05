---
title: MSSQLSERVER_1904 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1904 (Database Engine error)
ms.assetid: 2a35d57d-74e2-45a2-8f67-3f2e51d69712
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 568cfe7499c041c2ee6a8ac3698b31698171bece
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581270"
---
# <a name="mssqlserver_1904"></a><span data-ttu-id="8af92-102">MSSQLSERVER_1904</span><span class="sxs-lookup"><span data-stu-id="8af92-102">MSSQLSERVER_1904</span></span>
    
## <a name="details"></a><span data-ttu-id="8af92-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="8af92-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8af92-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="8af92-104">Product Name</span></span>|<span data-ttu-id="8af92-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8af92-105">SQL Server</span></span>|  
|<span data-ttu-id="8af92-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="8af92-106">Event ID</span></span>|<span data-ttu-id="8af92-107">1904</span><span class="sxs-lookup"><span data-stu-id="8af92-107">1904</span></span>|  
|<span data-ttu-id="8af92-108">事件源</span><span class="sxs-lookup"><span data-stu-id="8af92-108">Event Source</span></span>|<span data-ttu-id="8af92-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8af92-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8af92-110">组件</span><span class="sxs-lookup"><span data-stu-id="8af92-110">Component</span></span>|<span data-ttu-id="8af92-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8af92-111">SQLEngine</span></span>|  
|<span data-ttu-id="8af92-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="8af92-112">Symbolic Name</span></span>|<span data-ttu-id="8af92-113">KEYCOUNT</span><span class="sxs-lookup"><span data-stu-id="8af92-113">KEYCOUNT</span></span>|  
|<span data-ttu-id="8af92-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="8af92-114">Message Text</span></span>|<span data-ttu-id="8af92-115">表 '%.\*ls' 的 %S_MSG '%.\*ls' 在 %S_MSG 键列表中具有 %d 个列名。</span><span class="sxs-lookup"><span data-stu-id="8af92-115">The %S_MSG '%.\*ls' on table '%.\*ls' has %d column names in %S_MSG key list.</span></span> <span data-ttu-id="8af92-116">索引或统计信息键列列表的最大限制为 %d。</span><span class="sxs-lookup"><span data-stu-id="8af92-116">The maximum limit for index or statistics key column list is %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8af92-117">说明</span><span class="sxs-lookup"><span data-stu-id="8af92-117">Explanation</span></span>  
 <span data-ttu-id="8af92-118">指定索引或统计信息的键列列表超出了允许的最大列数。</span><span class="sxs-lookup"><span data-stu-id="8af92-118">The key column list for the specified index or statistics exceeds the maximum number of columns allowed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8af92-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="8af92-119">User Action</span></span>  
 <span data-ttu-id="8af92-120">修改键列的列表，使其中包含的列数小于指定的最大列数。</span><span class="sxs-lookup"><span data-stu-id="8af92-120">Modify the key column list to include no more than the specified maximum number of columns.</span></span>  
  
 <span data-ttu-id="8af92-121">对于非聚集索引，请考虑使用 CREATE INDEX 语句中的 INCLUDE 子句，将列作为非键列添加到索引中。</span><span class="sxs-lookup"><span data-stu-id="8af92-121">For nonclustered indexes, consider using the INCLUDE clause in the CREATE INDEX statement to add columns to the index as nonkey columns.</span></span> <span data-ttu-id="8af92-122">使用此方法可避免超过当前的索引大小限值（即最多 16 个键列）。</span><span class="sxs-lookup"><span data-stu-id="8af92-122">This method avoids exceeding the current index size limitation of a maximum of 16 key columns.</span></span> <span data-ttu-id="8af92-123">有关详细信息，请参阅 [Create Indexes with Included Columns](../indexes/create-indexes-with-included-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="8af92-123">For more information, see [Create Indexes with Included Columns](../indexes/create-indexes-with-included-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8af92-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8af92-124">See Also</span></span>  
 <span data-ttu-id="8af92-125">[CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8af92-125">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 [<span data-ttu-id="8af92-126">CREATE STATISTICS (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="8af92-126">CREATE STATISTICS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-statistics-transact-sql)  
  
  
