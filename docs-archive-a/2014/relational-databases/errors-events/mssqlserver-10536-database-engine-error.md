---
title: MSSQLSERVER_10536 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10536 (Database Engine error)
ms.assetid: 9f97b41f-0ef8-4ad2-aec0-906a5d7522ba
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 00d08f4555f38b61661a917ba94c023f9dd6c4a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690637"
---
# <a name="mssqlserver_10536"></a><span data-ttu-id="e16c1-102">MSSQLSERVER_10536</span><span class="sxs-lookup"><span data-stu-id="e16c1-102">MSSQLSERVER_10536</span></span>
    
## <a name="details"></a><span data-ttu-id="e16c1-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="e16c1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e16c1-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="e16c1-104">Product Name</span></span>|<span data-ttu-id="e16c1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e16c1-105">SQL Server</span></span>|  
|<span data-ttu-id="e16c1-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e16c1-106">Event ID</span></span>|<span data-ttu-id="e16c1-107">10536</span><span class="sxs-lookup"><span data-stu-id="e16c1-107">10536</span></span>|  
|<span data-ttu-id="e16c1-108">事件源</span><span class="sxs-lookup"><span data-stu-id="e16c1-108">Event Source</span></span>|<span data-ttu-id="e16c1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e16c1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e16c1-110">组件</span><span class="sxs-lookup"><span data-stu-id="e16c1-110">Component</span></span>|<span data-ttu-id="e16c1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e16c1-111">SQLEngine</span></span>|  
|<span data-ttu-id="e16c1-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="e16c1-112">Symbolic Name</span></span>|<span data-ttu-id="e16c1-113">PG_TOO_MANY_STMTS</span><span class="sxs-lookup"><span data-stu-id="e16c1-113">PG_TOO_MANY_STMTS</span></span>|  
|<span data-ttu-id="e16c1-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="e16c1-114">Message Text</span></span>|<span data-ttu-id="e16c1-115">无法创建计划指南 '%.\*ls'，因为与指定的 `@plan_handle` 对应的批处理或模块中包含的合格语句超过 1000 个。</span><span class="sxs-lookup"><span data-stu-id="e16c1-115">Cannot create plan guide '%.\*ls' because the batch or module corresponding to the specified `@plan_handle` contains more than 1000 eligible statements.</span></span> <span data-ttu-id="e16c1-116">通过为每个语句指定 `statement_start_offset` 值，为批或模块中的每个语句创建一个计划指南。</span><span class="sxs-lookup"><span data-stu-id="e16c1-116">Create a plan guide for each statement in the batch or module by specifying a `statement_start_offset` value for each statement.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e16c1-117">说明</span><span class="sxs-lookup"><span data-stu-id="e16c1-117">Explanation</span></span>  
 <span data-ttu-id="e16c1-118">与指定的 `@plan_handle` 对应的批或模块中包含的合格语句超过 1000 个。</span><span class="sxs-lookup"><span data-stu-id="e16c1-118">The batch or module corresponding to the specified `@plan_handle` contains more than 1000 eligible statements.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e16c1-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="e16c1-119">User Action</span></span>  
 <span data-ttu-id="e16c1-120">通过为每个语句指定 `statement_start_offset` 值，为批或模块中的每个语句创建一个计划指南。</span><span class="sxs-lookup"><span data-stu-id="e16c1-120">Create a plan guide for each statement in the batch or module by specifying a `statement_start_offset` value for each statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e16c1-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e16c1-121">See Also</span></span>  
 <span data-ttu-id="e16c1-122">[sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e16c1-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="e16c1-123">[计划指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="e16c1-123">[Plan Guides](../performance/plan-guides.md) </span></span>  
 [<span data-ttu-id="e16c1-124">sp_create_plan_guide_from_handle (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e16c1-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
