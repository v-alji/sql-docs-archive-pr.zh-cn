---
title: 查看 SQL Server 错误日志 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cycling SQL Server error log
- viewing SQL Server error log
- errors [SQL Server], logs
- SQL Server error log
- displaying SQL Server error log
- logs [SQL Server], SQL Server error logs
ms.assetid: 6908c21a-65e3-458f-a272-fee256d86448
author: stevestein
ms.author: sstein
ms.openlocfilehash: 822ae4fba589f005aaee41857a9db3388a309254
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576466"
---
# <a name="viewing-the-sql-server-error-log"></a><span data-ttu-id="39a2d-102">查看 SQL Server 错误日志</span><span class="sxs-lookup"><span data-stu-id="39a2d-102">Viewing the SQL Server Error Log</span></span>
  <span data-ttu-id="39a2d-103">查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志可以确保进程（例如，备份和还原操作、批处理命令或其他脚本和进程）成功完成。</span><span class="sxs-lookup"><span data-stu-id="39a2d-103">View the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to ensure that processes have completed successfully (for example, backup and restore operations, batch commands, or other scripts and processes).</span></span> <span data-ttu-id="39a2d-104">此功能可用于帮助检测任何当前或潜在的问题领域，包括自动恢复消息（尤其是在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例已停止并重新启动时）、内核消息或其他服务器级错误消息。</span><span class="sxs-lookup"><span data-stu-id="39a2d-104">This can be helpful to detect any current or potential problem areas, including automatic recovery messages (particularly if an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been stopped and restarted), kernel messages, or other server-level error messages.</span></span>  
  
 <span data-ttu-id="39a2d-105">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或任何文本编辑器可以查看 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 错误日志。</span><span class="sxs-lookup"><span data-stu-id="39a2d-105">View the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or any text editor.</span></span> <span data-ttu-id="39a2d-106">有关如何查看错误日志的详细信息，请参阅 [Open Log File Viewer](../../relational-databases/logs/log-file-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="39a2d-106">For more information about how to view the error log, see [Open Log File Viewer](../../relational-databases/logs/log-file-viewer.md).</span></span> <span data-ttu-id="39a2d-107">默认情况下，错误日志位于 `Program Files\Microsoft SQL Server\MSSQL.`*n*`\MSSQL\LOG\ERRORLOG` 和 `ERRORLOG.`*n* 文件中。</span><span class="sxs-lookup"><span data-stu-id="39a2d-107">By default, the error log is located at `Program Files\Microsoft SQL Server\MSSQL.`*n*`\MSSQL\LOG\ERRORLOG` and `ERRORLOG.`*n* files.</span></span>  
  
 <span data-ttu-id="39a2d-108">每当启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时，将创建新的错误日志，虽然 [sp_cycle_errorlog](/sql/relational-databases/system-stored-procedures/sp-cycle-errorlog-transact-sql) 系统存储过程可用于循环使用错误日志文件，而不必重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="39a2d-108">A new error log is created each time an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started, although the [sp_cycle_errorlog](/sql/relational-databases/system-stored-procedures/sp-cycle-errorlog-transact-sql) system stored procedure can be used to cycle the error log files without having to restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="39a2d-109">通常， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 保留前六个日志的备份，并指定最近日志备份的扩展名为 .1、下一个最近日志备份的扩展名为 .2，依次类推。</span><span class="sxs-lookup"><span data-stu-id="39a2d-109">Typically, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retains backups of the previous six logs and gives the most recent log backup the extension .1, the second most recent the extension .2, and so on.</span></span> <span data-ttu-id="39a2d-110">当前的错误日志没有扩展名。</span><span class="sxs-lookup"><span data-stu-id="39a2d-110">The current error log has no extension.</span></span>  
  
 <span data-ttu-id="39a2d-111">请注意，您还可以查看脱机或无法启动的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志。</span><span class="sxs-lookup"><span data-stu-id="39a2d-111">Be aware that you can also view the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log on instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are offline or cannot start.</span></span> <span data-ttu-id="39a2d-112">有关详细信息，请参阅 [查看脱机日志文件](../../relational-databases/logs/view-offline-log-files.md)。</span><span class="sxs-lookup"><span data-stu-id="39a2d-112">For more information, see [View Offline Log Files](../../relational-databases/logs/view-offline-log-files.md).</span></span>  
  
  
