---
title: MSSQLSERVER_10519 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10519 (Database Engine error)
ms.assetid: 3be393a1-b186-41ae-afb9-a3d07ff354bb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0ec584649842f787b1de9d2ea6d161aea6970250
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691734"
---
# <a name="mssqlserver_10519"></a><span data-ttu-id="16333-102">MSSQLSERVER_10519</span><span class="sxs-lookup"><span data-stu-id="16333-102">MSSQLSERVER_10519</span></span>
    
## <a name="details"></a><span data-ttu-id="16333-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="16333-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="16333-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="16333-104">Product Name</span></span>|<span data-ttu-id="16333-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="16333-105">SQL Server</span></span>|  
|<span data-ttu-id="16333-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="16333-106">Event ID</span></span>|<span data-ttu-id="16333-107">10519</span><span class="sxs-lookup"><span data-stu-id="16333-107">10519</span></span>|  
|<span data-ttu-id="16333-108">事件源</span><span class="sxs-lookup"><span data-stu-id="16333-108">Event Source</span></span>|<span data-ttu-id="16333-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="16333-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="16333-110">组件</span><span class="sxs-lookup"><span data-stu-id="16333-110">Component</span></span>|<span data-ttu-id="16333-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="16333-111">SQLEngine</span></span>|  
|<span data-ttu-id="16333-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="16333-112">Symbolic Name</span></span>|<span data-ttu-id="16333-113">PG_INCOMPATIBLE_STMT_AND_HINTS</span><span class="sxs-lookup"><span data-stu-id="16333-113">PG_INCOMPATIBLE_STMT_AND_HINTS</span></span>|  
|<span data-ttu-id="16333-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="16333-114">Message Text</span></span>|<span data-ttu-id="16333-115">无法创建计划指南 '%.\*ls'，因为 `@hints` 中指定的提示无法应用于 `@stmt` 或 `@statement_start_offset` 指定的语句。</span><span class="sxs-lookup"><span data-stu-id="16333-115">Cannot create plan guide '%.\*ls' because the hints specified in `@hints` cannot be applied to the statement specified by either `@stmt` or `@statement_start_offset`.</span></span> <span data-ttu-id="16333-116">请确保提示可以应用于该语句。</span><span class="sxs-lookup"><span data-stu-id="16333-116">Verify that the hints can be applied to the statement.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="16333-117">说明</span><span class="sxs-lookup"><span data-stu-id="16333-117">Explanation</span></span>  
 <span data-ttu-id="16333-118">`@hints` 中指定的语句无法应用于 `@stmt` 或 `@statement_start_offset` 指定的语句。</span><span class="sxs-lookup"><span data-stu-id="16333-118">The hints specified in `@hints` cannot be applied to the statement specified by either `@stmt` or `@statement_start_offset`.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="16333-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="16333-119">User Action</span></span>  
 <span data-ttu-id="16333-120">请指定可以应用于该语句的提示。</span><span class="sxs-lookup"><span data-stu-id="16333-120">Specify hints that can be applied to the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16333-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="16333-121">See Also</span></span>  
 <span data-ttu-id="16333-122">[sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="16333-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="16333-123">[计划指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="16333-123">[Plan Guides](../performance/plan-guides.md) </span></span>  
 [<span data-ttu-id="16333-124">sp_create_plan_guide_from_handle (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="16333-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
