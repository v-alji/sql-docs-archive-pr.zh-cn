---
title: MSSQLSERVER_41301 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41301 (Database Engine error)
ms.assetid: c6127e1e-2846-4ee9-bc42-2d896ea9730e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d4fa78b334f32033f96df002aeaf039994b396cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587846"
---
# <a name="mssqlserver_41301"></a><span data-ttu-id="599de-102">MSSQLSERVER_41301</span><span class="sxs-lookup"><span data-stu-id="599de-102">MSSQLSERVER_41301</span></span>
    
## <a name="details"></a><span data-ttu-id="599de-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="599de-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="599de-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="599de-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="599de-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="599de-105">Event ID</span></span>|<span data-ttu-id="599de-106">41301</span><span class="sxs-lookup"><span data-stu-id="599de-106">41301</span></span>|  
|<span data-ttu-id="599de-107">事件源</span><span class="sxs-lookup"><span data-stu-id="599de-107">Event Source</span></span>|<span data-ttu-id="599de-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="599de-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="599de-109">组件</span><span class="sxs-lookup"><span data-stu-id="599de-109">Component</span></span>|<span data-ttu-id="599de-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="599de-110">SQLEngine</span></span>|  
|<span data-ttu-id="599de-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="599de-111">Symbolic Name</span></span>|<span data-ttu-id="599de-112">COMMIT_DEPENDENCY_FAILURE</span><span class="sxs-lookup"><span data-stu-id="599de-112">COMMIT_DEPENDENCY_FAILURE</span></span>|  
|<span data-ttu-id="599de-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="599de-113">Message Text</span></span>|<span data-ttu-id="599de-114">当前事务所依赖的前一事务已终止，当前事务无法再提交。</span><span class="sxs-lookup"><span data-stu-id="599de-114">A previous transaction that the current transaction took a dependency on has aborted, and the current transaction can no longer commit.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="599de-115">说明</span><span class="sxs-lookup"><span data-stu-id="599de-115">Explanation</span></span>  
 <span data-ttu-id="599de-116">事务遇到依赖关系错误，已失败。</span><span class="sxs-lookup"><span data-stu-id="599de-116">The transaction encountered a dependency failure, and is now doomed.</span></span>  
  
 <span data-ttu-id="599de-117">依赖事务太多也可导致此错误。</span><span class="sxs-lookup"><span data-stu-id="599de-117">This error can also be caused by too many dependent transactions.</span></span> <span data-ttu-id="599de-118">任何写事务的依赖事务都有数量限制。</span><span class="sxs-lookup"><span data-stu-id="599de-118">Any write transaction can have a limited number of dependent transactions.</span></span> <span data-ttu-id="599de-119">例如，如果太多的读事务尝试依赖更新事务，就可能会发生此错误。</span><span class="sxs-lookup"><span data-stu-id="599de-119">For example, this error can occur if too many read transactions try to take a dependency on the update transaction.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="599de-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="599de-120">User Action</span></span>  
 <span data-ttu-id="599de-121">不必对事务执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="599de-121">Don't do any work on the transaction.</span></span> <span data-ttu-id="599de-122">调用 ROLLBACK TRAN 回滚事务。</span><span class="sxs-lookup"><span data-stu-id="599de-122">Call ROLLBACK TRAN to roll back the transaction.</span></span> <span data-ttu-id="599de-123">有关详细信息，请参阅[内存中 OLTP&#40;内存中优化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。</span><span class="sxs-lookup"><span data-stu-id="599de-123">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="599de-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="599de-124">See Also</span></span>  
 [<span data-ttu-id="599de-125">启用和禁用 AlwaysOn 可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="599de-125">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
  
  
