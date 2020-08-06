---
title: MSSQLSERVER_10502 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10502 (Database Engine error)
ms.assetid: 26d9b64d-4299-4b55-92d0-0a32a3688c0a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: eeec3a3adf318cadc96501938f8a5565f1c07670
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577736"
---
# <a name="mssqlserver_10502"></a><span data-ttu-id="58973-102">MSSQLSERVER_10502</span><span class="sxs-lookup"><span data-stu-id="58973-102">MSSQLSERVER_10502</span></span>
    
## <a name="details"></a><span data-ttu-id="58973-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="58973-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="58973-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="58973-104">Product Name</span></span>|<span data-ttu-id="58973-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="58973-105">SQL Server</span></span>|  
|<span data-ttu-id="58973-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="58973-106">Event ID</span></span>|<span data-ttu-id="58973-107">10502</span><span class="sxs-lookup"><span data-stu-id="58973-107">10502</span></span>|  
|<span data-ttu-id="58973-108">事件源</span><span class="sxs-lookup"><span data-stu-id="58973-108">Event Source</span></span>|<span data-ttu-id="58973-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="58973-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="58973-110">组件</span><span class="sxs-lookup"><span data-stu-id="58973-110">Component</span></span>|<span data-ttu-id="58973-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="58973-111">SQLEngine</span></span>|  
|<span data-ttu-id="58973-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="58973-112">Symbolic Name</span></span>|<span data-ttu-id="58973-113">PG_DUP_FOUND</span><span class="sxs-lookup"><span data-stu-id="58973-113">PG_DUP_FOUND</span></span>|  
|<span data-ttu-id="58973-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="58973-114">Message Text</span></span>|<span data-ttu-id="58973-115">无法创建计划指南 '%.\*ls'，因为 @stmt 和 @module_or_batch 或 @plan_handle 和 @statement_start_offset 指定的语句与数据库中的现有计划指南 '%.\*ls' 相匹配。</span><span class="sxs-lookup"><span data-stu-id="58973-115">Cannot create plan guide '%.\*ls' because the statement specified by @stmt and @module_or_batch, or by @plan_handle and @statement_start_offset, matches the existing plan guide '%.\*ls' in the database.</span></span> <span data-ttu-id="58973-116">请先删除现有计划指南，再创建新的计划指南。</span><span class="sxs-lookup"><span data-stu-id="58973-116">Drop the existing plan guide before creating the new plan guide.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="58973-117">说明</span><span class="sxs-lookup"><span data-stu-id="58973-117">Explanation</span></span>  
 <span data-ttu-id="58973-118">指定语句的计划指南已经存在。</span><span class="sxs-lookup"><span data-stu-id="58973-118">A plan guide exists for the specified statement.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="58973-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="58973-119">User Action</span></span>  
 <span data-ttu-id="58973-120">请先删除现有计划指南，再创建新的计划指南。</span><span class="sxs-lookup"><span data-stu-id="58973-120">Drop the existing plan guide before creating the new plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58973-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="58973-121">See Also</span></span>  
 <span data-ttu-id="58973-122">[计划指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="58973-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="58973-123">[sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="58973-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="58973-124">sp_create_plan_guide_from_handle (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="58973-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
