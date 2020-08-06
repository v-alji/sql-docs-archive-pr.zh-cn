---
title: MSSQLSERVER_2530 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 5d4be07a-38a5-4b25-819c-4dcb4636cc15
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 30b57aae907d6f0acc4d1c0e6021bf936621c69e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577722"
---
# <a name="mssqlserver_2530"></a><span data-ttu-id="88ca5-102">MSSQLSERVER_2530</span><span class="sxs-lookup"><span data-stu-id="88ca5-102">MSSQLSERVER_2530</span></span>
    
## <a name="details"></a><span data-ttu-id="88ca5-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="88ca5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="88ca5-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="88ca5-104">Product Name</span></span>|<span data-ttu-id="88ca5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="88ca5-105">SQL Server</span></span>|  
|<span data-ttu-id="88ca5-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="88ca5-106">Event ID</span></span>|<span data-ttu-id="88ca5-107">2530</span><span class="sxs-lookup"><span data-stu-id="88ca5-107">2530</span></span>|  
|<span data-ttu-id="88ca5-108">事件源</span><span class="sxs-lookup"><span data-stu-id="88ca5-108">Event Source</span></span>|<span data-ttu-id="88ca5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="88ca5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="88ca5-110">组件</span><span class="sxs-lookup"><span data-stu-id="88ca5-110">Component</span></span>|<span data-ttu-id="88ca5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="88ca5-111">SQLEngine</span></span>|  
|<span data-ttu-id="88ca5-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="88ca5-112">Symbolic Name</span></span>|<span data-ttu-id="88ca5-113">DBCC_INDEX_IS_OFFLINE</span><span class="sxs-lookup"><span data-stu-id="88ca5-113">DBCC_INDEX_IS_OFFLINE</span></span>|  
|<span data-ttu-id="88ca5-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="88ca5-114">Message Text</span></span>|<span data-ttu-id="88ca5-115">表 "%.\*ls" 的索引 "%.\*ls" 已禁用。</span><span class="sxs-lookup"><span data-stu-id="88ca5-115">The index "%.\*ls" on table "%.\*ls" is disabled.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="88ca5-116">说明</span><span class="sxs-lookup"><span data-stu-id="88ca5-116">Explanation</span></span>  
 <span data-ttu-id="88ca5-117">DBCC 语句无法继续，因为指定的索引已禁用。</span><span class="sxs-lookup"><span data-stu-id="88ca5-117">The DBCC statement cannot proceed because the specified index is disabled.</span></span> <span data-ttu-id="88ca5-118">索引被禁用后一直保持禁用状态，直到它重新生成或删除并重新创建。</span><span class="sxs-lookup"><span data-stu-id="88ca5-118">After an index is disabled, it remains in a disabled state until it is rebuilt or dropped and re-created.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="88ca5-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="88ca5-119">User Action</span></span>  
  
1.  <span data-ttu-id="88ca5-120">可以通过使用下列方法之一来启用已禁用的索引：</span><span class="sxs-lookup"><span data-stu-id="88ca5-120">Enable the disabled index by using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="88ca5-121">带 REBUILD 子句的 ALTER INDEX 语句</span><span class="sxs-lookup"><span data-stu-id="88ca5-121">ALTER INDEX statement with the REBUILD clause</span></span>  
  
    -   <span data-ttu-id="88ca5-122">带 DROP_EXISTING 子句的 CREATE INDEX</span><span class="sxs-lookup"><span data-stu-id="88ca5-122">CREATE INDEX with the DROP_EXISTING clause</span></span>  
  
    -   <span data-ttu-id="88ca5-123">DBCC DBREINDEX</span><span class="sxs-lookup"><span data-stu-id="88ca5-123">DBCC DBREINDEX</span></span>  
  
2.  <span data-ttu-id="88ca5-124">请重新运行 DBCC 语句。</span><span class="sxs-lookup"><span data-stu-id="88ca5-124">Rerun the DBCC statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88ca5-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="88ca5-125">See Also</span></span>  
 <span data-ttu-id="88ca5-126">[启用索引和约束](../indexes/enable-indexes-and-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="88ca5-126">[Enable Indexes and Constraints](../indexes/enable-indexes-and-constraints.md) </span></span>  
 <span data-ttu-id="88ca5-127">[ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="88ca5-127">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 <span data-ttu-id="88ca5-128">[CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="88ca5-128">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 [<span data-ttu-id="88ca5-129">DBCC DBREINDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="88ca5-129">DBCC DBREINDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql)  
  
  
