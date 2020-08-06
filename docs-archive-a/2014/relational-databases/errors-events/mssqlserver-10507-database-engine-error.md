---
title: MSSQLSERVER_10507 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10507 (Database Engine error)
ms.assetid: cd83fa81-ac37-4eda-a3c3-17610b051de2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a80e48948c03b370c07742fabbb3cf8eb3e74315
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692429"
---
# <a name="mssqlserver_10507"></a><span data-ttu-id="58de7-102">MSSQLSERVER_10507</span><span class="sxs-lookup"><span data-stu-id="58de7-102">MSSQLSERVER_10507</span></span>
    
## <a name="details"></a><span data-ttu-id="58de7-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="58de7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="58de7-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="58de7-104">Product Name</span></span>|<span data-ttu-id="58de7-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="58de7-105">SQL Server</span></span>|  
|<span data-ttu-id="58de7-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="58de7-106">Event ID</span></span>|<span data-ttu-id="58de7-107">10507</span><span class="sxs-lookup"><span data-stu-id="58de7-107">10507</span></span>|  
|<span data-ttu-id="58de7-108">事件源</span><span class="sxs-lookup"><span data-stu-id="58de7-108">Event Source</span></span>|<span data-ttu-id="58de7-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="58de7-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="58de7-110">组件</span><span class="sxs-lookup"><span data-stu-id="58de7-110">Component</span></span>|<span data-ttu-id="58de7-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="58de7-111">SQLEngine</span></span>|  
|<span data-ttu-id="58de7-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="58de7-112">Symbolic Name</span></span>|<span data-ttu-id="58de7-113">PG_STMT_DOES_NOT_MATCH</span><span class="sxs-lookup"><span data-stu-id="58de7-113">PG_STMT_DOES_NOT_MATCH</span></span>|  
|<span data-ttu-id="58de7-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="58de7-114">Message Text</span></span>|<span data-ttu-id="58de7-115">无法创建计划指南 '%.\*ls'，因为 `@stmt` 和 `@module_or_batch` 或 `@plan_handle` 和 `@statement_start_offset` 指定的语句与指定模块或批处理中的所有语句都不匹配。</span><span class="sxs-lookup"><span data-stu-id="58de7-115">Cannot create plan guide '%.\*ls' because the statement specified by `@stmt` and `@module_or_batch`, or by `@plan_handle` and `@statement_start_offset`, does not match any statement in the specified module or batch.</span></span> <span data-ttu-id="58de7-116">请修改这些值以匹配模块或批中的语句。</span><span class="sxs-lookup"><span data-stu-id="58de7-116">Modify the values to match a statement in the module or batch.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="58de7-117">说明</span><span class="sxs-lookup"><span data-stu-id="58de7-117">Explanation</span></span>  
 <span data-ttu-id="58de7-118">指定模块或批中的语句无法与指定的语句或语句偏移量值相匹配。</span><span class="sxs-lookup"><span data-stu-id="58de7-118">A statement in the specified module or batch could not be matched to the specified statement or statement offset value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="58de7-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="58de7-119">User Action</span></span>  
 <span data-ttu-id="58de7-120">请修改指定的参数值，使其与模块或批中的语句相匹配。</span><span class="sxs-lookup"><span data-stu-id="58de7-120">Modify the specified parameter values to match a statement in the module or batch.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58de7-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="58de7-121">See Also</span></span>  
 <span data-ttu-id="58de7-122">[计划指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="58de7-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="58de7-123">[sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="58de7-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="58de7-124">sp_create_plan_guide_from_handle (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="58de7-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
