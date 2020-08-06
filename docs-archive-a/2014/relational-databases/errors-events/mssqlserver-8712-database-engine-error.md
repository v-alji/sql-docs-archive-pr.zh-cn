---
title: MSSQLSERVER_8712 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8712 (Database Engine error)
ms.assetid: 292fb3bc-062e-41e4-a566-b5d3d0b21977
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9285d4846cac5af2dd6e87ab55d5fd0610586d07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591902"
---
# <a name="mssqlserver_8712"></a><span data-ttu-id="e1f67-102">MSSQLSERVER_8712</span><span class="sxs-lookup"><span data-stu-id="e1f67-102">MSSQLSERVER_8712</span></span>
    
## <a name="details"></a><span data-ttu-id="e1f67-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="e1f67-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e1f67-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="e1f67-104">Product Name</span></span>|<span data-ttu-id="e1f67-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e1f67-105">SQL Server</span></span>|  
|<span data-ttu-id="e1f67-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e1f67-106">Event ID</span></span>|<span data-ttu-id="e1f67-107">8712</span><span class="sxs-lookup"><span data-stu-id="e1f67-107">8712</span></span>|  
|<span data-ttu-id="e1f67-108">事件源</span><span class="sxs-lookup"><span data-stu-id="e1f67-108">Event Source</span></span>|<span data-ttu-id="e1f67-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e1f67-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e1f67-110">组件</span><span class="sxs-lookup"><span data-stu-id="e1f67-110">Component</span></span>|<span data-ttu-id="e1f67-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e1f67-111">SQLEngine</span></span>|  
|<span data-ttu-id="e1f67-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="e1f67-112">Symbolic Name</span></span>|<span data-ttu-id="e1f67-113">USEPLAN_ERR_NO_INDEX</span><span class="sxs-lookup"><span data-stu-id="e1f67-113">USEPLAN_ERR_NO_INDEX</span></span>|  
|<span data-ttu-id="e1f67-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="e1f67-114">Message Text</span></span>|<span data-ttu-id="e1f67-115">USE PLAN 提示中指定的索引 '%.\*ls' 不存在。</span><span class="sxs-lookup"><span data-stu-id="e1f67-115">Index '%.\*ls', specified in the USE PLAN hint, does not exist.</span></span> <span data-ttu-id="e1f67-116">请指定一个现有索引，或者使用指定名称创建一个索引。</span><span class="sxs-lookup"><span data-stu-id="e1f67-116">Specify an existing index, or create an index with the specified name.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e1f67-117">说明</span><span class="sxs-lookup"><span data-stu-id="e1f67-117">Explanation</span></span>  
 <span data-ttu-id="e1f67-118">USE PLAN 提示中指定的索引不存在。</span><span class="sxs-lookup"><span data-stu-id="e1f67-118">An index that is specified in the USE PLAN hint does not exist.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e1f67-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="e1f67-119">User Action</span></span>  
 <span data-ttu-id="e1f67-120">请确保在 USE PLAN 提示中指定的所有索引均存在。</span><span class="sxs-lookup"><span data-stu-id="e1f67-120">Ensure all indexes that are specified in the USE PLAN hint exist.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1f67-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e1f67-121">See Also</span></span>  
 <span data-ttu-id="e1f67-122">[查询提示 (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query) </span><span class="sxs-lookup"><span data-stu-id="e1f67-122">[Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span></span>  
 [<span data-ttu-id="e1f67-123">计划指南</span><span class="sxs-lookup"><span data-stu-id="e1f67-123">Plan Guides</span></span>](../performance/plan-guides.md)  
  
  
