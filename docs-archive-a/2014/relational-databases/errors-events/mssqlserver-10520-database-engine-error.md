---
title: MSSQLSERVER_10520 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10520 (Database Engine error)
ms.assetid: cc8799f1-5b90-4248-b209-e1d5087f9529
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1b8bdf080703fa6bd02fc34b8c31f59407814b93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689429"
---
# <a name="mssqlserver_10520"></a><span data-ttu-id="a546a-102">MSSQLSERVER_10520</span><span class="sxs-lookup"><span data-stu-id="a546a-102">MSSQLSERVER_10520</span></span>
    
## <a name="details"></a><span data-ttu-id="a546a-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="a546a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a546a-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="a546a-104">Product Name</span></span>|<span data-ttu-id="a546a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a546a-105">SQL Server</span></span>|  
|<span data-ttu-id="a546a-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="a546a-106">Event ID</span></span>|<span data-ttu-id="a546a-107">10520</span><span class="sxs-lookup"><span data-stu-id="a546a-107">10520</span></span>|  
|<span data-ttu-id="a546a-108">事件源</span><span class="sxs-lookup"><span data-stu-id="a546a-108">Event Source</span></span>|<span data-ttu-id="a546a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a546a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a546a-110">组件</span><span class="sxs-lookup"><span data-stu-id="a546a-110">Component</span></span>|<span data-ttu-id="a546a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a546a-111">SQLEngine</span></span>|  
|<span data-ttu-id="a546a-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="a546a-112">Symbolic Name</span></span>|<span data-ttu-id="a546a-113">PG_PARAM_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="a546a-113">PG_PARAM_NOT_ALLOWED</span></span>|  
|<span data-ttu-id="a546a-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="a546a-114">Message Text</span></span>|<span data-ttu-id="a546a-115">无法创建计划指南 '%.\*ls'，因为 @type 指定为 '%ls' ，并且为参数 '%ls' 指定了非 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="a546a-115">Cannot create plan guide '%.\*ls' because @type was specified as '%ls' and a non-NULL value is specified for the parameter '%ls'.</span></span> <span data-ttu-id="a546a-116">此类型要求该参数的值为 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="a546a-116">This type requires a NULL value for the parameter.</span></span> <span data-ttu-id="a546a-117">请为该参数指定 NULL 值，或将该类型更改为允许该参数为非 NULL 值的类型。</span><span class="sxs-lookup"><span data-stu-id="a546a-117">Specify NULL for the parameter, or change the type to one that allows a non-NULL value for the parameter.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a546a-118">说明</span><span class="sxs-lookup"><span data-stu-id="a546a-118">Explanation</span></span>  
 <span data-ttu-id="a546a-119">@type 中指定的类型要求指定参数的值为 NULL 值，但却提供了非 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="a546a-119">The type specified in @type requires a NULL value for the specified parameter, however a non-NULL value was supplied.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a546a-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="a546a-120">User Action</span></span>  
 <span data-ttu-id="a546a-121">请为该参数指定 NULL 值，或将该类型更改为允许该参数为非 NULL 值的类型。</span><span class="sxs-lookup"><span data-stu-id="a546a-121">Specify NULL for the parameter, or change the type to one that allows a non-NULL value for the parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a546a-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a546a-122">See Also</span></span>  
 <span data-ttu-id="a546a-123">[sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a546a-123">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 [<span data-ttu-id="a546a-124">计划指南</span><span class="sxs-lookup"><span data-stu-id="a546a-124">Plan Guides</span></span>](../performance/plan-guides.md)  
  
  
