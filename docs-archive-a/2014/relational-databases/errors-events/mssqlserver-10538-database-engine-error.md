---
title: MSSQLSERVER_10538 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10538 (Database Engine error)
ms.assetid: 284d19b4-4979-4cbe-a9be-ac1104433c69
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: edc6abf192a3341f9b84c99e99071343cc882c3d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689418"
---
# <a name="mssqlserver_10538"></a><span data-ttu-id="9ba72-102">MSSQLSERVER_10538</span><span class="sxs-lookup"><span data-stu-id="9ba72-102">MSSQLSERVER_10538</span></span>
    
## <a name="details"></a><span data-ttu-id="9ba72-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="9ba72-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ba72-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="9ba72-104">Product Name</span></span>|<span data-ttu-id="9ba72-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9ba72-105">SQL Server</span></span>|  
|<span data-ttu-id="9ba72-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="9ba72-106">Event ID</span></span>|<span data-ttu-id="9ba72-107">10538</span><span class="sxs-lookup"><span data-stu-id="9ba72-107">10538</span></span>|  
|<span data-ttu-id="9ba72-108">事件源</span><span class="sxs-lookup"><span data-stu-id="9ba72-108">Event Source</span></span>|<span data-ttu-id="9ba72-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9ba72-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9ba72-110">组件</span><span class="sxs-lookup"><span data-stu-id="9ba72-110">Component</span></span>|<span data-ttu-id="9ba72-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9ba72-111">SQLEngine</span></span>|  
|<span data-ttu-id="9ba72-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="9ba72-112">Symbolic Name</span></span>|<span data-ttu-id="9ba72-113">PG_INVALID_PLANGUIDE_HANDLE</span><span class="sxs-lookup"><span data-stu-id="9ba72-113">PG_INVALID_PLANGUIDE_HANDLE</span></span>|  
|<span data-ttu-id="9ba72-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="9ba72-114">Message Text</span></span>|<span data-ttu-id="9ba72-115">因为指定的计划指南 ID 为 NULL 或无效，或者您对该计划指南引用的对象没有所需权限，所以找不到该计划指南。</span><span class="sxs-lookup"><span data-stu-id="9ba72-115">Cannot find the plan guide either because the specified plan guide ID is NULL or invalid, or you do not have permission on the object referenced by the plan guide.</span></span> <span data-ttu-id="9ba72-116">请确保计划指南 ID 有效，当前会话设置为正确的数据库上下文，并且你对计划指南所引用的对象具有 ALTER DATABASE 权限或 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="9ba72-116">Verify that the plan guide ID is valid, the current session is set to the correct database context, and you have either ALTER DATABASE permission or ALTER permission on the object referenced by the plan guide.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9ba72-117">说明</span><span class="sxs-lookup"><span data-stu-id="9ba72-117">Explanation</span></span>  
 <span data-ttu-id="9ba72-118">指定的计划指南 ID 为 NULL 或无效，或者您对该计划指南引用的对象没有所需权限。</span><span class="sxs-lookup"><span data-stu-id="9ba72-118">The ID of the specified plan guide is NULL or invalid, or you do not have permission on the object referenced by the plan guide.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9ba72-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="9ba72-119">User Action</span></span>  
 <span data-ttu-id="9ba72-120">请确保计划指南 ID 有效，当前会话设置为正确的数据库上下文，并且你对计划指南所引用的对象具有 ALTER DATABASE 权限或 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="9ba72-120">Verify that the plan guide ID is valid, the current session is set to the correct database context, and you have ALTER DATABASE permission or ALTER permission on the object referenced by the plan guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ba72-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9ba72-121">See Also</span></span>  
 <span data-ttu-id="9ba72-122">[sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9ba72-122">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="9ba72-123">[计划指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="9ba72-123">[Plan Guides](../performance/plan-guides.md) </span></span>  
 [<span data-ttu-id="9ba72-124">sp_create_plan_guide_from_handle (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9ba72-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
