---
title: MSSQLSERVER_17300 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17300 (Database Engine error)
ms.assetid: c1d6bfb6-28af-4df6-8087-25807602d282
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2f77e39c71901166085d011d6d00f9a4a379bece
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687947"
---
# <a name="mssqlserver_17300"></a><span data-ttu-id="6a241-102">MSSQLSERVER_17300</span><span class="sxs-lookup"><span data-stu-id="6a241-102">MSSQLSERVER_17300</span></span>
    
## <a name="details"></a><span data-ttu-id="6a241-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="6a241-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6a241-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="6a241-104">Product Name</span></span>|<span data-ttu-id="6a241-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6a241-105">SQL Server</span></span>|  
|<span data-ttu-id="6a241-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="6a241-106">Event ID</span></span>|<span data-ttu-id="6a241-107">17300</span><span class="sxs-lookup"><span data-stu-id="6a241-107">17300</span></span>|  
|<span data-ttu-id="6a241-108">事件源</span><span class="sxs-lookup"><span data-stu-id="6a241-108">Event Source</span></span>|<span data-ttu-id="6a241-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6a241-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6a241-110">组件</span><span class="sxs-lookup"><span data-stu-id="6a241-110">Component</span></span>|<span data-ttu-id="6a241-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6a241-111">SQLEngine</span></span>|  
|<span data-ttu-id="6a241-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="6a241-112">Symbolic Name</span></span>|<span data-ttu-id="6a241-113">PROC_OUT_OF_SYSTASK_SESSIONS</span><span class="sxs-lookup"><span data-stu-id="6a241-113">PROC_OUT_OF_SYSTASK_SESSIONS</span></span>|  
|<span data-ttu-id="6a241-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="6a241-114">Message Text</span></span>|<span data-ttu-id="6a241-115">SQL Server 无法运行新的系统任务，原因是内存不足或配置的会话数超过了服务器允许的最大数。</span><span class="sxs-lookup"><span data-stu-id="6a241-115">SQL Server was unable to run a new system task, either because there is insufficient memory or the number of configured sessions exceeds the maximum allowed in the server.</span></span> <span data-ttu-id="6a241-116">请查看服务器是否有足够的内存。</span><span class="sxs-lookup"><span data-stu-id="6a241-116">Verify that the server has adequate memory.</span></span> <span data-ttu-id="6a241-117">请使用 sp_configure 以及选项 '用户连接' 查看允许的最大用户连接数。</span><span class="sxs-lookup"><span data-stu-id="6a241-117">Use sp_configure with option 'user connections' to check the maximum number of user connections allowed.</span></span> <span data-ttu-id="6a241-118">请使用 sys.dm_exec_sessions 检查当前会话数，包括用户进程。</span><span class="sxs-lookup"><span data-stu-id="6a241-118">Use sys.dm_exec_sessions to check the current number of sessions, including user processes.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6a241-119">说明</span><span class="sxs-lookup"><span data-stu-id="6a241-119">Explanation</span></span>  
 <span data-ttu-id="6a241-120">尝试运行新系统任务失败，因为系统内存不足或超出了服务器中配置的会话数。</span><span class="sxs-lookup"><span data-stu-id="6a241-120">An attempt to run a new system task failed because of insufficient memory or because the number of configured sessions in the server was exceeded.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6a241-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="6a241-121">User Action</span></span>  
 <span data-ttu-id="6a241-122">查看服务器是否有足够的内存。</span><span class="sxs-lookup"><span data-stu-id="6a241-122">Verify that the server has enough memory.</span></span> <span data-ttu-id="6a241-123">使用 sys.dm_exec_sessions 查看当前的系统任务数，然后使用 sp_configure 查看配置的最大用户连接值。</span><span class="sxs-lookup"><span data-stu-id="6a241-123">Verify the current number of system tasks by using sys.dm_exec_sessions, and verify the configured value of maximum user connections by using sp_configure.</span></span>  
  
 <span data-ttu-id="6a241-124">根据需要执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="6a241-124">Perform the following tasks as appropriate:</span></span>  
  
-   <span data-ttu-id="6a241-125">向服务器添加更多内存。</span><span class="sxs-lookup"><span data-stu-id="6a241-125">Add more memory to the server.</span></span>  
  
-   <span data-ttu-id="6a241-126">终止一个或多个会话。</span><span class="sxs-lookup"><span data-stu-id="6a241-126">Terminate one or more sessions.</span></span>  
  
-   <span data-ttu-id="6a241-127">增大服务器所允许的最大用户连接数。</span><span class="sxs-lookup"><span data-stu-id="6a241-127">Increase the maximum number of user connections allowed on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a241-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6a241-128">See Also</span></span>  
 <span data-ttu-id="6a241-129">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6a241-129">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="6a241-130">[服务器配置选项 (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6a241-130">[Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="6a241-131">[sys.dm_exec_sessions (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6a241-131">[sys.dm_exec_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) </span></span>  
 <span data-ttu-id="6a241-132">[配置 user connections 服务器配置选项](../../database-engine/configure-windows/configure-the-user-connections-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="6a241-132">[Configure the user connections Server Configuration Option](../../database-engine/configure-windows/configure-the-user-connections-server-configuration-option.md) </span></span>  
 [<span data-ttu-id="6a241-133">KILL (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6a241-133">KILL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/kill-transact-sql)  
  
  
