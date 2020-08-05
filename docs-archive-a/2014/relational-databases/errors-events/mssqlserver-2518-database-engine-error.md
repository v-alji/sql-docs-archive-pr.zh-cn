---
title: MSSQLSERVER_2518 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2518 (Database Engine error)
ms.assetid: 54a13abc-4c33-43f0-b55d-e2e74a1381c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5f5517458c1014d7830c4813b95e1120bef452e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580281"
---
# <a name="mssqlserver_2518"></a><span data-ttu-id="fea10-102">MSSQLSERVER_2518</span><span class="sxs-lookup"><span data-stu-id="fea10-102">MSSQLSERVER_2518</span></span>
    
## <a name="details"></a><span data-ttu-id="fea10-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="fea10-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fea10-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="fea10-104">Product Name</span></span>|<span data-ttu-id="fea10-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="fea10-105">SQL Server</span></span>|  
|<span data-ttu-id="fea10-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="fea10-106">Event ID</span></span>|<span data-ttu-id="fea10-107">2518</span><span class="sxs-lookup"><span data-stu-id="fea10-107">2518</span></span>|  
|<span data-ttu-id="fea10-108">事件源</span><span class="sxs-lookup"><span data-stu-id="fea10-108">Event Source</span></span>|<span data-ttu-id="fea10-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="fea10-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="fea10-110">组件</span><span class="sxs-lookup"><span data-stu-id="fea10-110">Component</span></span>|<span data-ttu-id="fea10-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="fea10-111">SQLEngine</span></span>|  
|<span data-ttu-id="fea10-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="fea10-112">Symbolic Name</span></span>|<span data-ttu-id="fea10-113">DBCC_NO_EXPRESSION_EVAL_CLR_DISABLED</span><span class="sxs-lookup"><span data-stu-id="fea10-113">DBCC_NO_EXPRESSION_EVAL_CLR_DISABLED</span></span>|  
|<span data-ttu-id="fea10-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="fea10-114">Message Text</span></span>|<span data-ttu-id="fea10-115">对象 ID O_ID （对象”O_NAME”）：由于禁用了公共语言运行时(CLR)，无法检查此对象的计算列和用户定义类型。</span><span class="sxs-lookup"><span data-stu-id="fea10-115">Object ID O_ID (object "O_NAME"): Computed columns and user-defined types cannot be checked for this object because the common language runtime (CLR) is disabled.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fea10-116">说明</span><span class="sxs-lookup"><span data-stu-id="fea10-116">Explanation</span></span>  
 <span data-ttu-id="fea10-117">此信息性消息指示，查询处理器无法为 DBCC 提供内部对象，以允许对计算列和公共语言运行时 (CLR) 用户定义类型进行计算。</span><span class="sxs-lookup"><span data-stu-id="fea10-117">This informational message indicates that the query processor could not provide DBCC with an internal object to allow for computed columns and common language runtime (CLR) user-defined types to be evaluated.</span></span> <span data-ttu-id="fea10-118">之所以出现此问题，是因为其中一个列涉及 CLR，但未启用 CLR。</span><span class="sxs-lookup"><span data-stu-id="fea10-118">This problem occurred because one of the columns involved the CLR, but the CLR is not enabled.</span></span> <span data-ttu-id="fea10-119">内部对象涉及所有列。</span><span class="sxs-lookup"><span data-stu-id="fea10-119">The internal object covers all columns.</span></span> <span data-ttu-id="fea10-120">因此，无法计算单个列将阻止创建内部对象。</span><span class="sxs-lookup"><span data-stu-id="fea10-120">Therefore, the inability to evaluate a single column prevents creating the internal object.</span></span> <span data-ttu-id="fea10-121">这意味着在 DBCC 检查索引和基表之间的一致性时，将不检查计算列是否正确或使用它们。</span><span class="sxs-lookup"><span data-stu-id="fea10-121">This means that computed columns will not be checked for correctness or be used when DBCC checks the consistency between indexes and base tables.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fea10-122">用户操作</span><span class="sxs-lookup"><span data-stu-id="fea10-122">User Action</span></span>  
 <span data-ttu-id="fea10-123">启用 CLR 并重新运行 DBCC 语句。</span><span class="sxs-lookup"><span data-stu-id="fea10-123">Enable CLR and rerun the DBCC statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fea10-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fea10-124">See Also</span></span>  
 [<span data-ttu-id="fea10-125">启用 CLR 集成</span><span class="sxs-lookup"><span data-stu-id="fea10-125">Enabling CLR Integration</span></span>](../clr-integration/clr-integration-enabling.md)  
  
  
