---
title: MSSQLSERVER_601 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "601"
helpviewer_keywords:
- 601 (Database Engine error)
ms.assetid: 2039cc0a-9a43-4369-a04a-935e384388b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 459a983d72a91e628e8cc33636d3abd81998f1d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590852"
---
# <a name="mssqlserver_601"></a><span data-ttu-id="dcf64-102">MSSQLSERVER_601</span><span class="sxs-lookup"><span data-stu-id="dcf64-102">MSSQLSERVER_601</span></span>
    
## <a name="details"></a><span data-ttu-id="dcf64-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="dcf64-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dcf64-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="dcf64-104">Product Name</span></span>|<span data-ttu-id="dcf64-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="dcf64-105">SQL Server</span></span>|  
|<span data-ttu-id="dcf64-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="dcf64-106">Event ID</span></span>|<span data-ttu-id="dcf64-107">601</span><span class="sxs-lookup"><span data-stu-id="dcf64-107">601</span></span>|  
|<span data-ttu-id="dcf64-108">事件源</span><span class="sxs-lookup"><span data-stu-id="dcf64-108">Event Source</span></span>|<span data-ttu-id="dcf64-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="dcf64-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="dcf64-110">组件</span><span class="sxs-lookup"><span data-stu-id="dcf64-110">Component</span></span>|<span data-ttu-id="dcf64-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="dcf64-111">SQLEngine</span></span>|  
|<span data-ttu-id="dcf64-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="dcf64-112">Symbolic Name</span></span>||  
|<span data-ttu-id="dcf64-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="dcf64-113">Message Text</span></span>|<span data-ttu-id="dcf64-114">由于数据移动，无法继续以 NOLOCK 方式扫描。</span><span class="sxs-lookup"><span data-stu-id="dcf64-114">Could not continue scan with NOLOCK due to data movement.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dcf64-115">说明</span><span class="sxs-lookup"><span data-stu-id="dcf64-115">Explanation</span></span>  
 <span data-ttu-id="dcf64-116">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]无法继续执行查询，因为正在尝试读取由其他事务更新或删除的数据。</span><span class="sxs-lookup"><span data-stu-id="dcf64-116">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] cannot continue executing the query because it is trying to read data that was updated or deleted by another transaction.</span></span> <span data-ttu-id="dcf64-117">查询使用的是 NOLOCK 锁提示或 READ UNCOMMITTED 事务隔离级别。</span><span class="sxs-lookup"><span data-stu-id="dcf64-117">The query is using either the NOLOCK locking hint or the READ UNCOMMITTED transaction isolation level.</span></span>  
  
 <span data-ttu-id="dcf64-118">通常，系统拒绝用户访问其他事务正在更改的数据，因为已锁定该数据。</span><span class="sxs-lookup"><span data-stu-id="dcf64-118">Typically, access to data that is being changed by another transaction is denied because of locks put on the data.</span></span> <span data-ttu-id="dcf64-119">但是，利用 NOLOCK 锁提示和 READ UNCOMMITTED 事务隔离级别，可以允许查询对其他事务锁定的数据进行读取。</span><span class="sxs-lookup"><span data-stu-id="dcf64-119">However, the NOLOCK locking hint and READ UNCOMMITTED transaction isolation level let a query read data that is locked by another transaction.</span></span> <span data-ttu-id="dcf64-120">这称为脏读，因为您可以读取尚未提交并且随时可能更改的值。</span><span class="sxs-lookup"><span data-stu-id="dcf64-120">This is referred to as a dirty read because you can read values that have not yet been committed and that are subject to change.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dcf64-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="dcf64-121">User Action</span></span>  
 <span data-ttu-id="dcf64-122">此错误取消了该查询。</span><span class="sxs-lookup"><span data-stu-id="dcf64-122">This error cancels the query.</span></span> <span data-ttu-id="dcf64-123">重新提交该查询或删除 NOLOCK 锁提示。</span><span class="sxs-lookup"><span data-stu-id="dcf64-123">Either resubmit the query or remove the NOLOCK locking hint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcf64-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dcf64-124">See Also</span></span>  
 <span data-ttu-id="dcf64-125">[MSSQLSERVER_605](mssqlserver-605-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="dcf64-125">[MSSQLSERVER_605](mssqlserver-605-database-engine-error.md) </span></span>  
 <span data-ttu-id="dcf64-126">[表提示 (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-table) </span><span class="sxs-lookup"><span data-stu-id="dcf64-126">[Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table) </span></span>  
 <span data-ttu-id="dcf64-127">[SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dcf64-127">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="dcf64-128">SET TRANSACTION ISOLATION LEVEL (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="dcf64-128">SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)  
  
  
