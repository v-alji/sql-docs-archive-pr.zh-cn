---
title: MSSQLSERVER_10537 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10537 (Database Engine error)
ms.assetid: 728469a4-6523-4a37-925f-a950d75420fa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b1baccad5236bd8c1a71024b7dd542cc9d11cbd7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690638"
---
# <a name="mssqlserver_10537"></a><span data-ttu-id="6ffe1-102">MSSQLSERVER_10537</span><span class="sxs-lookup"><span data-stu-id="6ffe1-102">MSSQLSERVER_10537</span></span>
    
## <a name="details"></a><span data-ttu-id="6ffe1-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="6ffe1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6ffe1-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="6ffe1-104">Product Name</span></span>|<span data-ttu-id="6ffe1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6ffe1-105">SQL Server</span></span>|  
|<span data-ttu-id="6ffe1-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="6ffe1-106">Event ID</span></span>|<span data-ttu-id="6ffe1-107">10537</span><span class="sxs-lookup"><span data-stu-id="6ffe1-107">10537</span></span>|  
|<span data-ttu-id="6ffe1-108">事件源</span><span class="sxs-lookup"><span data-stu-id="6ffe1-108">Event Source</span></span>|<span data-ttu-id="6ffe1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6ffe1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6ffe1-110">组件</span><span class="sxs-lookup"><span data-stu-id="6ffe1-110">Component</span></span>|<span data-ttu-id="6ffe1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6ffe1-111">SQLEngine</span></span>|  
|<span data-ttu-id="6ffe1-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="6ffe1-112">Symbolic Name</span></span>|<span data-ttu-id="6ffe1-113">PG_DUP_ENABLED</span><span class="sxs-lookup"><span data-stu-id="6ffe1-113">PG_DUP_ENABLED</span></span>|  
|<span data-ttu-id="6ffe1-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="6ffe1-114">Message Text</span></span>|<span data-ttu-id="6ffe1-115">无法启用计划指南 '%.\*ls'，因为已启用的计划指南 '%.\*ls' 包含该语句的相同作用域和初始偏移量值。</span><span class="sxs-lookup"><span data-stu-id="6ffe1-115">Cannot enable plan guide '%.\*ls' because the enabled plan guide '%.\*ls' contains the same scope and starting offset value as the statement.</span></span> <span data-ttu-id="6ffe1-116">请先禁用现有计划指南，再启用指定的计划指南。</span><span class="sxs-lookup"><span data-stu-id="6ffe1-116">Disable the existing plan guide before enabling the specified plan guide.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6ffe1-117">说明</span><span class="sxs-lookup"><span data-stu-id="6ffe1-117">Explanation</span></span>  
 <span data-ttu-id="6ffe1-118">现有计划指南与指定计划指南中的语句包含相同的作用域和初始偏移量值。</span><span class="sxs-lookup"><span data-stu-id="6ffe1-118">An existing plan guide contains the same scope and starting offset value as the statement in the specified plan guide.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6ffe1-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="6ffe1-119">User Action</span></span>  
 <span data-ttu-id="6ffe1-120">请先禁用现有计划指南，再启用指定的计划指南。</span><span class="sxs-lookup"><span data-stu-id="6ffe1-120">Disable the existing plan guide before enabling the specified plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ffe1-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6ffe1-121">See Also</span></span>  
 <span data-ttu-id="6ffe1-122">[sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6ffe1-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="6ffe1-123">[计划指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="6ffe1-123">[Plan Guides](../performance/plan-guides.md) </span></span>  
 [<span data-ttu-id="6ffe1-124">sp_create_plan_guide_from_handle (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6ffe1-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
