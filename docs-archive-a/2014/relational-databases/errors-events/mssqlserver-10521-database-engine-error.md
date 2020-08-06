---
title: MSSQLSERVER_10521 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10521 (Database Engine error)
ms.assetid: ba2d7e44-207c-4428-b5f0-c975ac122c0d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c034bd13e212b9b39bfd348353d59e23fc748079
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689427"
---
# <a name="mssqlserver_10521"></a><span data-ttu-id="2f6f1-102">MSSQLSERVER_10521</span><span class="sxs-lookup"><span data-stu-id="2f6f1-102">MSSQLSERVER_10521</span></span>
    
## <a name="details"></a><span data-ttu-id="2f6f1-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="2f6f1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2f6f1-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="2f6f1-104">Product Name</span></span>|<span data-ttu-id="2f6f1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2f6f1-105">SQL Server</span></span>|  
|<span data-ttu-id="2f6f1-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="2f6f1-106">Event ID</span></span>|<span data-ttu-id="2f6f1-107">10521</span><span class="sxs-lookup"><span data-stu-id="2f6f1-107">10521</span></span>|  
|<span data-ttu-id="2f6f1-108">事件源</span><span class="sxs-lookup"><span data-stu-id="2f6f1-108">Event Source</span></span>|<span data-ttu-id="2f6f1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2f6f1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2f6f1-110">组件</span><span class="sxs-lookup"><span data-stu-id="2f6f1-110">Component</span></span>|<span data-ttu-id="2f6f1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2f6f1-111">SQLEngine</span></span>|  
|<span data-ttu-id="2f6f1-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="2f6f1-112">Symbolic Name</span></span>|<span data-ttu-id="2f6f1-113">PG_PARAM_NEEDED</span><span class="sxs-lookup"><span data-stu-id="2f6f1-113">PG_PARAM_NEEDED</span></span>|  
|<span data-ttu-id="2f6f1-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="2f6f1-114">Message Text</span></span>|<span data-ttu-id="2f6f1-115">无法创建计划指南 '%.\*ls'，因为 `@type` 指定为 '%ls'，而参数 '%ls' 为 NULL。</span><span class="sxs-lookup"><span data-stu-id="2f6f1-115">Cannot create plan guide '%.\*ls' because `@type` was specified as '%ls' and the parameter '%ls' is NULL.</span></span> <span data-ttu-id="2f6f1-116">此类型要求该参数的值为非 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="2f6f1-116">This type requires a non-NULL value for the parameter.</span></span> <span data-ttu-id="2f6f1-117">请为该参数指定非 NULL 值，或将该类型更改为允许该参数为 NULL 值的类型。</span><span class="sxs-lookup"><span data-stu-id="2f6f1-117">Specify a non-NULL value for the parameter, or change the type to one that allows a NULL value for the parameter.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2f6f1-118">说明</span><span class="sxs-lookup"><span data-stu-id="2f6f1-118">Explanation</span></span>  
 <span data-ttu-id="2f6f1-119">`@type` 中指定的类型要求指定参数的值为非 NULL 值；但您指定的是 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="2f6f1-119">The type specified in `@type` requires a non-NULL value for the specified parameter; however a NULL value was supplied.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2f6f1-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="2f6f1-120">User Action</span></span>  
 <span data-ttu-id="2f6f1-121">请为该参数指定非 NULL 值，或将该类型更改为允许该参数为 NULL 值的类型。</span><span class="sxs-lookup"><span data-stu-id="2f6f1-121">Specify a non-NULL value for the parameter, or change the type to one that allows a NULL value for the parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f6f1-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2f6f1-122">See Also</span></span>  
 <span data-ttu-id="2f6f1-123">[sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2f6f1-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="2f6f1-124">[计划指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="2f6f1-124">[Plan Guides](../performance/plan-guides.md) </span></span>  
 [<span data-ttu-id="2f6f1-125">sp_create_plan_guide_from_handle (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2f6f1-125">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
