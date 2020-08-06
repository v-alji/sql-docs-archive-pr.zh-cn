---
title: MSSQLSERVER_8649 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8649 (Database Engine error)
ms.assetid: 992dbc74-7c3a-498b-9f1b-b28387640677
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b39ed0d8ffe5f7f601b6cb1393596d0d6546e557
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588552"
---
# <a name="mssqlserver_8649"></a><span data-ttu-id="f07a1-102">MSSQLSERVER_8649</span><span class="sxs-lookup"><span data-stu-id="f07a1-102">MSSQLSERVER_8649</span></span>
    
## <a name="details"></a><span data-ttu-id="f07a1-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="f07a1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f07a1-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="f07a1-104">Product Name</span></span>|<span data-ttu-id="f07a1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f07a1-105">SQL Server</span></span>|  
|<span data-ttu-id="f07a1-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="f07a1-106">Event ID</span></span>|<span data-ttu-id="f07a1-107">8649</span><span class="sxs-lookup"><span data-stu-id="f07a1-107">8649</span></span>|  
|<span data-ttu-id="f07a1-108">事件源</span><span class="sxs-lookup"><span data-stu-id="f07a1-108">Event Source</span></span>|<span data-ttu-id="f07a1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f07a1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f07a1-110">组件</span><span class="sxs-lookup"><span data-stu-id="f07a1-110">Component</span></span>|<span data-ttu-id="f07a1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f07a1-111">SQLEngine</span></span>|  
|<span data-ttu-id="f07a1-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="f07a1-112">Symbolic Name</span></span>|<span data-ttu-id="f07a1-113">COST_TOO_HIGH</span><span class="sxs-lookup"><span data-stu-id="f07a1-113">COST_TOO_HIGH</span></span>|  
|<span data-ttu-id="f07a1-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="f07a1-114">Message Text</span></span>|<span data-ttu-id="f07a1-115">查询已取消，因为此查询的估计开销 (%d) 出了配置的阈值 %d。</span><span class="sxs-lookup"><span data-stu-id="f07a1-115">The query has been canceled because the estimated cost of this query (%d) exceeds the configured threshold of %d.</span></span> <span data-ttu-id="f07a1-116">请与系统管理员联系。</span><span class="sxs-lookup"><span data-stu-id="f07a1-116">Contact the system administrator.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f07a1-117">说明</span><span class="sxs-lookup"><span data-stu-id="f07a1-117">Explanation</span></span>  
 <span data-ttu-id="f07a1-118">查询已取消，因为此查询的估计开销超出了为 QUERY_GOVERNOR_COST_LIMIT 设置的配置阈值。</span><span class="sxs-lookup"><span data-stu-id="f07a1-118">The query was canceled because the estimated cost of this query exceeds the configured threshold set for the QUERY_GOVERNOR_COST_LIMIT.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f07a1-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="f07a1-119">User Action</span></span>  
 <span data-ttu-id="f07a1-120">将 QUERY_GOVERNOR_COST_LIMIT 选项设置为更大的值。</span><span class="sxs-lookup"><span data-stu-id="f07a1-120">Set the QUERY_GOVERNOR_COST_LIMIT option to a higher value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f07a1-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f07a1-121">See Also</span></span>  
 [<span data-ttu-id="f07a1-122">SET QUERY_GOVERNOR_COST_LIMIT (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f07a1-122">SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql)  
  
  
