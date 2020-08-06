---
title: MSSQLSERVER_10531 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10531 (Database Engine error)
ms.assetid: bb40e994-231c-44ce-933f-8d767fb2f450
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6230c046a9eb7b900377888c59a3a492f2b89f73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689426"
---
# <a name="mssqlserver_10531"></a><span data-ttu-id="8a015-102">MSSQLSERVER_10531</span><span class="sxs-lookup"><span data-stu-id="8a015-102">MSSQLSERVER_10531</span></span>
    
## <a name="details"></a><span data-ttu-id="8a015-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="8a015-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8a015-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="8a015-104">Product Name</span></span>|<span data-ttu-id="8a015-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8a015-105">SQL Server</span></span>|  
|<span data-ttu-id="8a015-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="8a015-106">Event ID</span></span>|<span data-ttu-id="8a015-107">10531</span><span class="sxs-lookup"><span data-stu-id="8a015-107">10531</span></span>|  
|<span data-ttu-id="8a015-108">事件源</span><span class="sxs-lookup"><span data-stu-id="8a015-108">Event Source</span></span>|<span data-ttu-id="8a015-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8a015-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8a015-110">组件</span><span class="sxs-lookup"><span data-stu-id="8a015-110">Component</span></span>|<span data-ttu-id="8a015-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8a015-111">SQLEngine</span></span>|  
|<span data-ttu-id="8a015-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="8a015-112">Symbolic Name</span></span>|<span data-ttu-id="8a015-113">PG_NO_ELIGIBLE_STMT</span><span class="sxs-lookup"><span data-stu-id="8a015-113">PG_NO_ELIGIBLE_STMT</span></span>|  
|<span data-ttu-id="8a015-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="8a015-114">Message Text</span></span>|<span data-ttu-id="8a015-115">因为用户没有足够的权限，所以无法从缓存创建计划指南 '%.\*ls'。</span><span class="sxs-lookup"><span data-stu-id="8a015-115">Cannot create plan guide '%.\*ls' from cache because the user does not have adequate permissions.</span></span> <span data-ttu-id="8a015-116">请为创建该计划指南的用户授予 VIEW SERVER STATE 权限。</span><span class="sxs-lookup"><span data-stu-id="8a015-116">Grant the VIEW SERVER STATE permission to the user creating the plan guide.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8a015-117">说明</span><span class="sxs-lookup"><span data-stu-id="8a015-117">Explanation</span></span>  
 <span data-ttu-id="8a015-118">用户权限不足，无法从计划缓存创建指定的计划指南。</span><span class="sxs-lookup"><span data-stu-id="8a015-118">The user does not have adequate permissions to create the specified plan guide from the plan cache.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8a015-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="8a015-119">User Action</span></span>  
 <span data-ttu-id="8a015-120">请为创建该计划指南的用户授予 VIEW SERVER STATE 权限。</span><span class="sxs-lookup"><span data-stu-id="8a015-120">Grant VIEW SERVER STATE permission to the user creating the plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a015-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8a015-121">See Also</span></span>  
 <span data-ttu-id="8a015-122">[计划指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="8a015-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="8a015-123">[sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8a015-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="8a015-124">sp_create_plan_guide_from_handle (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="8a015-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
