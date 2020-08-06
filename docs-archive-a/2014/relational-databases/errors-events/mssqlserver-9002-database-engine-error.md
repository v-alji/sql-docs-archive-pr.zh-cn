---
title: MSSQLSERVER_9002 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9002 (Database Engine error)
ms.assetid: 2e50841f-2b99-45f4-aec5-aa4add70cbeb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b40fe70db8849d09f9296a06cbeed65a9c71e5a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588548"
---
# <a name="mssqlserver_9002"></a><span data-ttu-id="b4f2a-102">MSSQLSERVER_9002</span><span class="sxs-lookup"><span data-stu-id="b4f2a-102">MSSQLSERVER_9002</span></span>
    
## <a name="details"></a><span data-ttu-id="b4f2a-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="b4f2a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b4f2a-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="b4f2a-104">Product Name</span></span>|<span data-ttu-id="b4f2a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b4f2a-105">SQL Server</span></span>|  
|<span data-ttu-id="b4f2a-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b4f2a-106">Event ID</span></span>|<span data-ttu-id="b4f2a-107">9002</span><span class="sxs-lookup"><span data-stu-id="b4f2a-107">9002</span></span>|  
|<span data-ttu-id="b4f2a-108">事件源</span><span class="sxs-lookup"><span data-stu-id="b4f2a-108">Event Source</span></span>|<span data-ttu-id="b4f2a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b4f2a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b4f2a-110">组件</span><span class="sxs-lookup"><span data-stu-id="b4f2a-110">Component</span></span>|<span data-ttu-id="b4f2a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b4f2a-111">SQLEngine</span></span>|  
|<span data-ttu-id="b4f2a-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="b4f2a-112">Symbolic Name</span></span>|<span data-ttu-id="b4f2a-113">LOG_IS_FULL</span><span class="sxs-lookup"><span data-stu-id="b4f2a-113">LOG_IS_FULL</span></span>|  
|<span data-ttu-id="b4f2a-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="b4f2a-114">Message Text</span></span>|<span data-ttu-id="b4f2a-115">数据库 '%.\*ls' 的事务日志已满。</span><span class="sxs-lookup"><span data-stu-id="b4f2a-115">The transaction log for database '%.\*ls' is full.</span></span> <span data-ttu-id="b4f2a-116">若要查明无法重用日志中的空间的原因，请参阅 sys.databases 中的 log_reuse_wait_desc 列。</span><span class="sxs-lookup"><span data-stu-id="b4f2a-116">To find out why space in the log cannot be reused, see the log_reuse_wait_desc column in sys.databases.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b4f2a-117">说明</span><span class="sxs-lookup"><span data-stu-id="b4f2a-117">Explanation</span></span>  
 <span data-ttu-id="b4f2a-118">数据库日志空间不足。</span><span class="sxs-lookup"><span data-stu-id="b4f2a-118">The database log is out of space.</span></span> <span data-ttu-id="b4f2a-119">**sys.databases** 中的 **log_reuse_wait_desc** 列说明无法重用日志中的空间的原因。</span><span class="sxs-lookup"><span data-stu-id="b4f2a-119">The **log_reuse_wait_desc** column in **sys.databases** describes why space in the log cannot be reused.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b4f2a-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="b4f2a-120">User Action</span></span>  
 <span data-ttu-id="b4f2a-121">使用 **sys.databases** 确定日志已满的原因，然后更正该情况。</span><span class="sxs-lookup"><span data-stu-id="b4f2a-121">Use **sys.databases** to determine why the log is full and then correct the condition.</span></span> <span data-ttu-id="b4f2a-122">有关详细信息，请参阅 Server SQL 联机丛书中的“解决事务日志已满的问题（错误 9002）”。</span><span class="sxs-lookup"><span data-stu-id="b4f2a-122">For more information, see "Troubleshooting a Full Transaction Log (Error 9002)" in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4f2a-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4f2a-123">See Also</span></span>  
 <span data-ttu-id="b4f2a-124">[解决事务日志已满的问题（SQL Server 错误 9002）](../logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md) </span><span class="sxs-lookup"><span data-stu-id="b4f2a-124">[Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;](../logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md) </span></span>  
 [<span data-ttu-id="b4f2a-125">sys.databases (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b4f2a-125">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
