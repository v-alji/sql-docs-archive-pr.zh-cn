---
title: MSSQLSERVER_5235 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5235 (Database Engine error)
ms.assetid: 1aa7e6a5-7ccb-43c8-a1fd-d50e92e0a798
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 42c807944d7506a6a118de97ccd8c2c488942c8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692954"
---
# <a name="mssqlserver_5235"></a><span data-ttu-id="5fb7b-102">MSSQLSERVER_5235</span><span class="sxs-lookup"><span data-stu-id="5fb7b-102">MSSQLSERVER_5235</span></span>
    
## <a name="details"></a><span data-ttu-id="5fb7b-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="5fb7b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5fb7b-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="5fb7b-104">Product Name</span></span>|<span data-ttu-id="5fb7b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5fb7b-105">SQL Server</span></span>|  
|<span data-ttu-id="5fb7b-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5fb7b-106">Event ID</span></span>|<span data-ttu-id="5fb7b-107">5235</span><span class="sxs-lookup"><span data-stu-id="5fb7b-107">5235</span></span>|  
|<span data-ttu-id="5fb7b-108">事件源</span><span class="sxs-lookup"><span data-stu-id="5fb7b-108">Event Source</span></span>|<span data-ttu-id="5fb7b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5fb7b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5fb7b-110">组件</span><span class="sxs-lookup"><span data-stu-id="5fb7b-110">Component</span></span>|<span data-ttu-id="5fb7b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5fb7b-111">SQLEngine</span></span>|  
|<span data-ttu-id="5fb7b-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="5fb7b-112">Symbolic Name</span></span>|<span data-ttu-id="5fb7b-113">DBCC4_ERRORLOG_SUMMARY_PREMATURE_TERMINATION</span><span class="sxs-lookup"><span data-stu-id="5fb7b-113">DBCC4_ERRORLOG_SUMMARY_PREMATURE_TERMINATION</span></span>|  
|<span data-ttu-id="5fb7b-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="5fb7b-114">Message Text</span></span>|<span data-ttu-id="5fb7b-115">[EMERGENCY] 由于错误状态 ERROR_STATE，由 USER_NAME 执行的 DBCC DBCC_COMMAND_DETAILS 已异常终止。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-115">[EMERGENCY] DBCC DBCC_COMMAND_DETAILS executed by USER_NAME terminated abnormally due to error state ERROR_STATE.</span></span> <span data-ttu-id="5fb7b-116">运行时间：HOURS 小时 MINUTES 分钟 SECONDS 秒。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-116">Elapsed time: HOURS hours MINUTES minutes SECONDS seconds.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5fb7b-117">说明</span><span class="sxs-lookup"><span data-stu-id="5fb7b-117">Explanation</span></span>  
 <span data-ttu-id="5fb7b-118">这是命令运行时出现意外终止的情况下 DBCC 输出到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志的摘要消息。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-118">This is the summary message that DBCC prints to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log when an unexpected termination occurs while the command is running.</span></span> <span data-ttu-id="5fb7b-119">消息中报告的错误状态定义了意外终止的类型。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-119">The error state reported in the message defines the type of unexpected termination.</span></span>  
  
 <span data-ttu-id="5fb7b-120">下表列出并定义了错误状态。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-120">The following table lists and defines the error states.</span></span>  
  
|<span data-ttu-id="5fb7b-121">错误状态</span><span class="sxs-lookup"><span data-stu-id="5fb7b-121">Error state</span></span>|<span data-ttu-id="5fb7b-122">定义</span><span class="sxs-lookup"><span data-stu-id="5fb7b-122">Definition</span></span>|  
|-----------------|----------------|  
|<span data-ttu-id="5fb7b-123">状态 0</span><span class="sxs-lookup"><span data-stu-id="5fb7b-123">State 0</span></span>|<span data-ttu-id="5fb7b-124">该语句由于元数据损坏而终止。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-124">The statement was terminated because of a fatal metadata corruption.</span></span> <span data-ttu-id="5fb7b-125">出现此消息时伴随有错误 8930 的一个或多个实例。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-125">This message will be accompanied by one or more instances of error 8930.</span></span>|  
|<span data-ttu-id="5fb7b-126">状态 1</span><span class="sxs-lookup"><span data-stu-id="5fb7b-126">State 1</span></span>|<span data-ttu-id="5fb7b-127">该语句由于内部检查失败而终止。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-127">The statement was terminated because of an internal check failure.</span></span> <span data-ttu-id="5fb7b-128">出现此消息时伴随有错误 8967 的一个或多个实例。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-128">This message will be accompanied by one or more instances of error 8967.</span></span>|  
|<span data-ttu-id="5fb7b-129">状态 2</span><span class="sxs-lookup"><span data-stu-id="5fb7b-129">State 2</span></span>|<span data-ttu-id="5fb7b-130">核心存储引擎系统表的基本系统表检查失败。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-130">Basic system table checks of the core storage engine system tables failed.</span></span> <span data-ttu-id="5fb7b-131">出现此消息时伴随有错误 [7984](mssqlserver-7984-database-engine-error.md)、7985、[7986](mssqlserver-7986-database-engine-error.md)、[7987](mssqlserver-7987-database-engine-error.md) 或 [7988](mssqlserver-7988-database-engine-error.md) 的一个或多个实例。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-131">This message will be accompanied by one or more instances of error [7984](mssqlserver-7984-database-engine-error.md), 7985, [7986](mssqlserver-7986-database-engine-error.md), [7987](mssqlserver-7987-database-engine-error.md), or [7988](mssqlserver-7988-database-engine-error.md).</span></span>|  
|<span data-ttu-id="5fb7b-132">状态 3</span><span class="sxs-lookup"><span data-stu-id="5fb7b-132">State 3</span></span>|<span data-ttu-id="5fb7b-133">DBCC 紧急模式修复失败，因为重新生成事务日志后无法启动数据库。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-133">DBCC emergency-mode repair failed because the database could not be started after rebuilding the transaction log.</span></span> <span data-ttu-id="5fb7b-134">出现此消息时伴随有错误 7909。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-134">This message will be accompanied by error 7909.</span></span>|  
|<span data-ttu-id="5fb7b-135">状态 4</span><span class="sxs-lookup"><span data-stu-id="5fb7b-135">State 4</span></span>|<span data-ttu-id="5fb7b-136">执行命令时出现断言失败或访问冲突。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-136">A failed assertion or access violation occurred during the execution of the command.</span></span>|  
|<span data-ttu-id="5fb7b-137">状态 5</span><span class="sxs-lookup"><span data-stu-id="5fb7b-137">State 5</span></span>|<span data-ttu-id="5fb7b-138">出现意外终止了 DBCC 命令的未知故障。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-138">An unknown failure occurred that unexpectedly terminated the DBCC command.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="5fb7b-139">用户操作</span><span class="sxs-lookup"><span data-stu-id="5fb7b-139">User Action</span></span>  
 <span data-ttu-id="5fb7b-140">下表提供了适用于指定错误状态的用户操作。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-140">The following table provides the user action that is appropriate for the specified error state.</span></span>  
  
|<span data-ttu-id="5fb7b-141">错误状态</span><span class="sxs-lookup"><span data-stu-id="5fb7b-141">Error state</span></span>|<span data-ttu-id="5fb7b-142">用户操作</span><span class="sxs-lookup"><span data-stu-id="5fb7b-142">User action</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="5fb7b-143">状态 0</span><span class="sxs-lookup"><span data-stu-id="5fb7b-143">State 0</span></span>|<span data-ttu-id="5fb7b-144">从备份还原。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-144">Restore from backup.</span></span>|  
|<span data-ttu-id="5fb7b-145">状态 1</span><span class="sxs-lookup"><span data-stu-id="5fb7b-145">State 1</span></span>|<span data-ttu-id="5fb7b-146">请联系 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客户服务与支持部门 (CSS)。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-146">Contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>|  
|<span data-ttu-id="5fb7b-147">状态 2</span><span class="sxs-lookup"><span data-stu-id="5fb7b-147">State 2</span></span>|<span data-ttu-id="5fb7b-148">从备份还原。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-148">Restore from backup.</span></span>|  
|<span data-ttu-id="5fb7b-149">状态 3</span><span class="sxs-lookup"><span data-stu-id="5fb7b-149">State 3</span></span>|<span data-ttu-id="5fb7b-150">从备份还原。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-150">Restore from backup.</span></span>|  
|<span data-ttu-id="5fb7b-151">状态 4</span><span class="sxs-lookup"><span data-stu-id="5fb7b-151">State 4</span></span>|<span data-ttu-id="5fb7b-152">请与 CSS 联系。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-152">Contact CSS.</span></span>|  
|<span data-ttu-id="5fb7b-153">状态 5</span><span class="sxs-lookup"><span data-stu-id="5fb7b-153">State 5</span></span>|<span data-ttu-id="5fb7b-154">再次运行该命令。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-154">Run the command again.</span></span> <span data-ttu-id="5fb7b-155">如果问题仍然存在，请联系 CSS。</span><span class="sxs-lookup"><span data-stu-id="5fb7b-155">If the problem persists, contact CSS.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5fb7b-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5fb7b-156">See Also</span></span>  
 [<span data-ttu-id="5fb7b-157">DBCC (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5fb7b-157">DBCC &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-transact-sql)  
  
  
