---
title: MSSQLSERVER_10534 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10534 (Database Engine error)
ms.assetid: e65bb118-99d5-4fdb-b1d5-0ec70f0a677b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 793bb0bf5048e30624d9566f65e7c6752bd14386
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689424"
---
# <a name="mssqlserver_10534"></a><span data-ttu-id="3a5ef-102">MSSQLSERVER_10534</span><span class="sxs-lookup"><span data-stu-id="3a5ef-102">MSSQLSERVER_10534</span></span>
    
## <a name="details"></a><span data-ttu-id="3a5ef-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="3a5ef-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3a5ef-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="3a5ef-104">Product Name</span></span>|<span data-ttu-id="3a5ef-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3a5ef-105">SQL Server</span></span>|  
|<span data-ttu-id="3a5ef-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="3a5ef-106">Event ID</span></span>|<span data-ttu-id="3a5ef-107">10534</span><span class="sxs-lookup"><span data-stu-id="3a5ef-107">10534</span></span>|  
|<span data-ttu-id="3a5ef-108">事件源</span><span class="sxs-lookup"><span data-stu-id="3a5ef-108">Event Source</span></span>|<span data-ttu-id="3a5ef-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3a5ef-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3a5ef-110">组件</span><span class="sxs-lookup"><span data-stu-id="3a5ef-110">Component</span></span>|<span data-ttu-id="3a5ef-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3a5ef-111">SQLEngine</span></span>|  
|<span data-ttu-id="3a5ef-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="3a5ef-112">Symbolic Name</span></span>|<span data-ttu-id="3a5ef-113">PG_INVALID_PARAMS</span><span class="sxs-lookup"><span data-stu-id="3a5ef-113">PG_INVALID_PARAMS</span></span>|  
|<span data-ttu-id="3a5ef-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="3a5ef-114">Message Text</span></span>|<span data-ttu-id="3a5ef-115">无法创建计划指南 '%.\*ls'，因为为 `@params` 指定的值无效。</span><span class="sxs-lookup"><span data-stu-id="3a5ef-115">Cannot create plan guide '%.\*ls' because the value specified for `@params` is invalid.</span></span> <span data-ttu-id="3a5ef-116">请以 *parameter_name parameter_type* 的形式指定该值，或指定 NULL。</span><span class="sxs-lookup"><span data-stu-id="3a5ef-116">Specify the value in the form *parameter_name parameter_type*, or specify NULL.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3a5ef-117">说明</span><span class="sxs-lookup"><span data-stu-id="3a5ef-117">Explanation</span></span>  
 <span data-ttu-id="3a5ef-118">为 `@params` 指定的值无效。</span><span class="sxs-lookup"><span data-stu-id="3a5ef-118">The value specified for `@params` is invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3a5ef-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="3a5ef-119">User Action</span></span>  
 <span data-ttu-id="3a5ef-120">请以 *parameter_name parameter_type* 的形式指定该值，或指定 NULL。</span><span class="sxs-lookup"><span data-stu-id="3a5ef-120">Specify the value in the form *parameter_name parameter_type*, or specify NULL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a5ef-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3a5ef-121">See Also</span></span>  
 <span data-ttu-id="3a5ef-122">[计划指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="3a5ef-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="3a5ef-123">[sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3a5ef-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="3a5ef-124">sp_create_plan_guide_from_handle (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3a5ef-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
