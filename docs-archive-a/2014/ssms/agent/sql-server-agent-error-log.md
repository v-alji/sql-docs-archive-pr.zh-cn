---
title: SQL Server 代理错误日志 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- messages [SQL Server], SQL Server Agent
- errors [SQL Server], logs
- SQL Server Agent, errors
ms.assetid: 0b2d6e6e-cd2d-4b8b-9fa2-2bbd2fc0da41
author: stevestein
ms.author: sstein
ms.openlocfilehash: ea9a723695c6993f4f07897f49d8014a86ce78b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689233"
---
# <a name="sql-server-agent-error-log"></a><span data-ttu-id="53603-102">SQL Server 代理错误日志</span><span class="sxs-lookup"><span data-stu-id="53603-102">SQL Server Agent Error Log</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="53603-103">默认情况下，代理创建错误日志来记录警告和错误。</span><span class="sxs-lookup"><span data-stu-id="53603-103">Agent creates an error log that records warnings and errors by default.</span></span> <span data-ttu-id="53603-104">日志中显示下列警告和错误：</span><span class="sxs-lookup"><span data-stu-id="53603-104">The following warnings and errors are displayed in the log:</span></span>  
  
-   <span data-ttu-id="53603-105">警告消息，提供有关潜在问题的信息，例如 "作业 \<*job_name*> 在运行时被删除"。</span><span class="sxs-lookup"><span data-stu-id="53603-105">Warning messages that provide information about potential problems, such as "Job \<*job_name*> was deleted while it was running."</span></span>  
  
-   <span data-ttu-id="53603-106">错误消息，通常需要系统管理员干预，例如“无法启动邮件会话”。</span><span class="sxs-lookup"><span data-stu-id="53603-106">Error messages that usually require intervention by a system administrator, such as "Unable to start mail session."</span></span> <span data-ttu-id="53603-107">可以通过 **net send**将错误消息发送给特定用户或计算机。</span><span class="sxs-lookup"><span data-stu-id="53603-107">Error messages can be sent to a specific user or computer by **net send**.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="53603-108">最多可以维护九个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理错误日志。</span><span class="sxs-lookup"><span data-stu-id="53603-108">maintains up to nine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error logs.</span></span> <span data-ttu-id="53603-109">每个存档日志都有一个扩展名，指示该日志的相对存在时间。</span><span class="sxs-lookup"><span data-stu-id="53603-109">Each archived log has an extension that indicates the relative age of the log.</span></span> <span data-ttu-id="53603-110">例如，扩展名 .1 表示最新的存档错误日志，而扩展名 .9 表示最旧的存档错误日志。</span><span class="sxs-lookup"><span data-stu-id="53603-110">For example, an extension of .1 indicates the newest archived error log and an extension of .9 indicates the oldest archived error log.</span></span>  
  
 <span data-ttu-id="53603-111">默认情况下，执行跟踪消息不写入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理日志错误，因为它们会将日志填满。</span><span class="sxs-lookup"><span data-stu-id="53603-111">By default, execution trace messages are not written to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log, because they can fill it.</span></span> <span data-ttu-id="53603-112">如果错误日志已满，会降低选择和分析更严重的错误的能力。</span><span class="sxs-lookup"><span data-stu-id="53603-112">When the error log is full, your ability to select and analyze more difficult errors is reduced.</span></span> <span data-ttu-id="53603-113">因为日志会增加服务器的处理负荷，所以请务必仔细考虑是否值得将执行跟踪消息捕获到错误日志中。</span><span class="sxs-lookup"><span data-stu-id="53603-113">Because the log adds to the server's processing load, it is important to consider carefully what value you obtain by capturing execution trace messages to the error log.</span></span> <span data-ttu-id="53603-114">通常，最好仅在调试某个特定问题时捕获所有消息。</span><span class="sxs-lookup"><span data-stu-id="53603-114">Generally, it is best to capture all messages only when you are debugging a specific problem.</span></span>  
  
 <span data-ttu-id="53603-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理停止后，可以修改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理错误日志的位置。</span><span class="sxs-lookup"><span data-stu-id="53603-115">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is stopped, you can modify the location of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log.</span></span> <span data-ttu-id="53603-116">如果错误日志为空，则无法打开日志。</span><span class="sxs-lookup"><span data-stu-id="53603-116">When the error log is empty, the log cannot be opened.</span></span> <span data-ttu-id="53603-117">可以随时循环访问 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理日志，无需停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理。</span><span class="sxs-lookup"><span data-stu-id="53603-117">You can cycle the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent log at any time without stopping [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
 <span data-ttu-id="53603-118">**查看 SQL Server 代理错误日志**</span><span class="sxs-lookup"><span data-stu-id="53603-118">**To view the SQL Server Agent error log**</span></span>  
  
-   [<span data-ttu-id="53603-119">查看 SQL Server 代理错误日志 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="53603-119">View SQL Server Agent Error Log &#40;SQL Server Management Studio&#41;</span></span>](view-sql-server-agent-error-log-sql-server-management-studio.md) 
  
 <span data-ttu-id="53603-120">**重命名 SQL Server 代理错误日志**</span><span class="sxs-lookup"><span data-stu-id="53603-120">**To rename a SQL Server Agent error log**</span></span>  
  
-   [<span data-ttu-id="53603-121">重命名 SQL Server 代理错误日志 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="53603-121">Rename a SQL Server Agent Error Log &#40;SQL Server Management Studio&#41;</span></span>](rename-a-sql-server-agent-error-log-sql-server-management-studio.md)  
  
 <span data-ttu-id="53603-122">**发送 SQL Server 代理错误消息**</span><span class="sxs-lookup"><span data-stu-id="53603-122">**To send SQL Server Agent error messages**</span></span>  
  
-   [<span data-ttu-id="53603-123">发送 SQL Server 代理错误消息</span><span class="sxs-lookup"><span data-stu-id="53603-123">Send SQL Server Agent Error Messages</span></span>](send-sql-server-agent-error-messages.md)  
  
 <span data-ttu-id="53603-124">**将执行跟踪消息写入到 SQL Server 代理错误日志中**</span><span class="sxs-lookup"><span data-stu-id="53603-124">**To write execution trace messages to the SQL Server Agent error log**</span></span>  
  
-   [<span data-ttu-id="53603-125">将执行跟踪消息写入到 SQL Server 代理错误日志中 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="53603-125">Write Execution Trace Messages to the SQL Server Agent Error Log &#40;SQL Server Management Studio&#41;</span></span>](write-execution-trace-messages-to-sql-server-agent-log-ssms.md)  
  
  
