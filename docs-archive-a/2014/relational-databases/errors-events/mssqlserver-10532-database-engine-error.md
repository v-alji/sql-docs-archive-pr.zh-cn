---
title: MSSQLSERVER_10532 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10532 (Database Engine error)
ms.assetid: 01da29ee-bf67-433f-8148-587a7e8d1d76
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 26ab34c319eff62737eae337828247fdfd7e901b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692949"
---
# <a name="mssqlserver_10532"></a><span data-ttu-id="ed7a0-102">MSSQLSERVER_10532</span><span class="sxs-lookup"><span data-stu-id="ed7a0-102">MSSQLSERVER_10532</span></span>
    
## <a name="details"></a><span data-ttu-id="ed7a0-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="ed7a0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ed7a0-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="ed7a0-104">Product Name</span></span>|<span data-ttu-id="ed7a0-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ed7a0-105">SQL Server</span></span>|  
|<span data-ttu-id="ed7a0-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="ed7a0-106">Event ID</span></span>|<span data-ttu-id="ed7a0-107">10532</span><span class="sxs-lookup"><span data-stu-id="ed7a0-107">10532</span></span>|  
|<span data-ttu-id="ed7a0-108">事件源</span><span class="sxs-lookup"><span data-stu-id="ed7a0-108">Event Source</span></span>|<span data-ttu-id="ed7a0-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ed7a0-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ed7a0-110">组件</span><span class="sxs-lookup"><span data-stu-id="ed7a0-110">Component</span></span>|<span data-ttu-id="ed7a0-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ed7a0-111">SQLEngine</span></span>|  
|<span data-ttu-id="ed7a0-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="ed7a0-112">Symbolic Name</span></span>|<span data-ttu-id="ed7a0-113">PG_NO_ELIGIBLE_STMT</span><span class="sxs-lookup"><span data-stu-id="ed7a0-113">PG_NO_ELIGIBLE_STMT</span></span>|  
|<span data-ttu-id="ed7a0-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="ed7a0-114">Message Text</span></span>|<span data-ttu-id="ed7a0-115">无法创建计划指南 '%.\*ls'，因为 `@plan_handle` 指定的批处理或模块不包含可用于计划指南的语句。</span><span class="sxs-lookup"><span data-stu-id="ed7a0-115">Cannot create plan guide '%.\*ls' because the batch or module specified by `@plan_handle` does not contain a statement that is eligible for a plan guide.</span></span> <span data-ttu-id="ed7a0-116">请为 `@plan_handle` 指定其他值。</span><span class="sxs-lookup"><span data-stu-id="ed7a0-116">Specify a different value for `@plan_handle`.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ed7a0-117">说明</span><span class="sxs-lookup"><span data-stu-id="ed7a0-117">Explanation</span></span>  
 <span data-ttu-id="ed7a0-118">由 `@plan_handle` 指定的批或模块不包含可用于计划指南的语句。</span><span class="sxs-lookup"><span data-stu-id="ed7a0-118">The batch or module specified by `@plan_handle` does not contain a statement that is eligible for a plan guide.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ed7a0-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="ed7a0-119">User Action</span></span>  
 <span data-ttu-id="ed7a0-120">请为 `@plan_handle` 指定其他值。</span><span class="sxs-lookup"><span data-stu-id="ed7a0-120">Specify a different value for `@plan_handle`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed7a0-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ed7a0-121">See Also</span></span>  
 <span data-ttu-id="ed7a0-122">[计划指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="ed7a0-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="ed7a0-123">[sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ed7a0-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="ed7a0-124">sp_create_plan_guide_from_handle (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ed7a0-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
