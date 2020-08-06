---
title: MSSQLSERVER_10533 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10533 (Database Engine error)
ms.assetid: cc2fbdab-7b90-415f-a1f9-066824344283
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ccef25bc8f594cb6ea0b60aefab838ef27cda6f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586756"
---
# <a name="mssqlserver_10533"></a><span data-ttu-id="6a481-102">MSSQLSERVER_10533</span><span class="sxs-lookup"><span data-stu-id="6a481-102">MSSQLSERVER_10533</span></span>
    
## <a name="details"></a><span data-ttu-id="6a481-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="6a481-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6a481-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="6a481-104">Product Name</span></span>|<span data-ttu-id="6a481-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6a481-105">SQL Server</span></span>|  
|<span data-ttu-id="6a481-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="6a481-106">Event ID</span></span>|<span data-ttu-id="6a481-107">10533</span><span class="sxs-lookup"><span data-stu-id="6a481-107">10533</span></span>|  
|<span data-ttu-id="6a481-108">事件源</span><span class="sxs-lookup"><span data-stu-id="6a481-108">Event Source</span></span>|<span data-ttu-id="6a481-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6a481-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6a481-110">组件</span><span class="sxs-lookup"><span data-stu-id="6a481-110">Component</span></span>|<span data-ttu-id="6a481-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6a481-111">SQLEngine</span></span>|  
|<span data-ttu-id="6a481-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="6a481-112">Symbolic Name</span></span>|<span data-ttu-id="6a481-113">PG_NAME_TOO_BIG</span><span class="sxs-lookup"><span data-stu-id="6a481-113">PG_NAME_TOO_BIG</span></span>|  
|<span data-ttu-id="6a481-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="6a481-114">Message Text</span></span>|<span data-ttu-id="6a481-115">无法创建计划指南 '%.\*ls'，因为其名称超过允许的最大字符数 124。</span><span class="sxs-lookup"><span data-stu-id="6a481-115">Cannot create plan guide '%.\*ls' because the plan guide name exceeds 124 characters, the maximum number allowed.</span></span> <span data-ttu-id="6a481-116">请指定字符数少于 125 个的名称。</span><span class="sxs-lookup"><span data-stu-id="6a481-116">Specify a name that contains fewer than 125 characters.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6a481-117">说明</span><span class="sxs-lookup"><span data-stu-id="6a481-117">Explanation</span></span>  
 <span data-ttu-id="6a481-118">计划指南的名称超过所允许的最大字符数（即 124 个字符）。</span><span class="sxs-lookup"><span data-stu-id="6a481-118">The plan guide name exceeds 124 characters, the maximum number allowed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6a481-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="6a481-119">User Action</span></span>  
 <span data-ttu-id="6a481-120">请指定字符数少于 125 个的名称。</span><span class="sxs-lookup"><span data-stu-id="6a481-120">Specify a name that contains fewer than 125 characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a481-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6a481-121">See Also</span></span>  
 <span data-ttu-id="6a481-122">[计划指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="6a481-122">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="6a481-123">[sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6a481-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="6a481-124">sp_create_plan_guide_from_handle (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6a481-124">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
