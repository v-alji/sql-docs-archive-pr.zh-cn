---
title: MSSQLSERVER_10539 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10539 (Database Engine error)
ms.assetid: 49c26ff7-18b8-4f07-a087-f45f63463b3b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5fd1f190b8f5d3ab9755409bdd034fa374ea5314
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689415"
---
# <a name="mssqlserver_10539"></a><span data-ttu-id="799c7-102">MSSQLSERVER_10539</span><span class="sxs-lookup"><span data-stu-id="799c7-102">MSSQLSERVER_10539</span></span>
    
## <a name="details"></a><span data-ttu-id="799c7-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="799c7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="799c7-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="799c7-104">Product Name</span></span>|<span data-ttu-id="799c7-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="799c7-105">SQL Server</span></span>|  
|<span data-ttu-id="799c7-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="799c7-106">Event ID</span></span>|<span data-ttu-id="799c7-107">10539</span><span class="sxs-lookup"><span data-stu-id="799c7-107">10539</span></span>|  
|<span data-ttu-id="799c7-108">事件源</span><span class="sxs-lookup"><span data-stu-id="799c7-108">Event Source</span></span>|<span data-ttu-id="799c7-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="799c7-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="799c7-110">组件</span><span class="sxs-lookup"><span data-stu-id="799c7-110">Component</span></span>|<span data-ttu-id="799c7-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="799c7-111">SQLEngine</span></span>|  
|<span data-ttu-id="799c7-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="799c7-112">Symbolic Name</span></span>|<span data-ttu-id="799c7-113">PG_NO_PLAN_FOR_STMT</span><span class="sxs-lookup"><span data-stu-id="799c7-113">PG_NO_PLAN_FOR_STMT</span></span>|  
|<span data-ttu-id="799c7-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="799c7-114">Message Text</span></span>|<span data-ttu-id="799c7-115">由于查询计划对于初始偏移量为 %d 的语句不可用，因此无法从缓存创建计划指南 '%.\*ls'。</span><span class="sxs-lookup"><span data-stu-id="799c7-115">Cannot create plan guide '%.\*ls' from cache because a query plan is not available for the statement with start offset %d.</span></span> <span data-ttu-id="799c7-116">如果该语句依赖于尚未创建的数据库对象，则可能出现此问题。</span><span class="sxs-lookup"><span data-stu-id="799c7-116">This problem can occur if the statement depends on database objects that have not yet been created.</span></span> <span data-ttu-id="799c7-117">请确保所有必要的数据库对象都已存在，并在创建该计划指南之前先执行该语句。</span><span class="sxs-lookup"><span data-stu-id="799c7-117">Make sure that all necessary database objects exist, and execute the statement before creating the plan guide.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="799c7-118">说明</span><span class="sxs-lookup"><span data-stu-id="799c7-118">Explanation</span></span>  
 <span data-ttu-id="799c7-119">在计划缓存中，查询计划不能用于具有指定初始偏移量的语句。</span><span class="sxs-lookup"><span data-stu-id="799c7-119">A query plan is not available in the plan cache for the statement with the specified starting offset.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="799c7-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="799c7-120">User Action</span></span>  
 <span data-ttu-id="799c7-121">请确保所有必要的数据库对象都已存在，并在创建该计划指南之前先执行该语句。</span><span class="sxs-lookup"><span data-stu-id="799c7-121">Make sure that all necessary database objects exist, and execute the statement before creating the plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="799c7-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="799c7-122">See Also</span></span>  
 [<span data-ttu-id="799c7-123">sp_create_plan_guide_from_handle (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="799c7-123">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
