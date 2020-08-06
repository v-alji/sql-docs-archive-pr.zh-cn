---
title: 监视错误日志 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server]
- database performance [SQL Server], errors
- Windows application logs [SQL Server]
- monitoring performance [SQL Server], errors
- server performance [SQL Server], errors
- comparing error and application log output
- errors [SQL Server], logs
- tuning databases [SQL Server], errors
- database monitoring [SQL Server], errors
- SQL Server error log
- logs [SQL Server], SQL Server error logs
- error logs [SQL Server]
- logs [SQL Server], Windows application logs
ms.assetid: e250336b-0695-44f6-a42f-23222f94e377
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2a47891599dbe735bd437f5239c73bfd34c422ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586037"
---
# <a name="monitoring-the-error-logs"></a><span data-ttu-id="78ca0-102">监视错误日志</span><span class="sxs-lookup"><span data-stu-id="78ca0-102">Monitoring the Error Logs</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="78ca0-103">将某些系统事件和用户定义事件记录到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 应用程序日志中。</span><span class="sxs-lookup"><span data-stu-id="78ca0-103">logs certain system events and user-defined events to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application log.</span></span> <span data-ttu-id="78ca0-104">这两种日志都会自动给所有记录事件加上时间戳。</span><span class="sxs-lookup"><span data-stu-id="78ca0-104">Both logs automatically timestamp all recorded events.</span></span> <span data-ttu-id="78ca0-105">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志中的信息可以解决 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的相关问题。</span><span class="sxs-lookup"><span data-stu-id="78ca0-105">Use the information in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to troubleshoot problems related to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="78ca0-106">Windows 应用程序日志完整地记录了 Windows 操作系统上发生的事件，以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理中的事件。</span><span class="sxs-lookup"><span data-stu-id="78ca0-106">The Windows application log provides an overall picture of events that occur on the Windows operating system, as well as events in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="78ca0-107">使用 Windows 事件查看器可以查看 Windows 应用程序日志和筛选信息。</span><span class="sxs-lookup"><span data-stu-id="78ca0-107">Use the Windows Event Viewer to view the Windows application log and to filter the information.</span></span> <span data-ttu-id="78ca0-108">例如，可以筛选信息、警告、错误、审核成功和审核失败等事件。</span><span class="sxs-lookup"><span data-stu-id="78ca0-108">For example, you can filter events, such as information, warning, error, success audit, and failure audit.</span></span>  
  
## <a name="comparing-error-and-application-log-output"></a><span data-ttu-id="78ca0-109">比较错误和应用程序日志输出</span><span class="sxs-lookup"><span data-stu-id="78ca0-109">Comparing Error and Application Log Output</span></span>  
 <span data-ttu-id="78ca0-110">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志和 Windows 应用程序日志来标识产生问题的原因。</span><span class="sxs-lookup"><span data-stu-id="78ca0-110">You can use both the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and the Windows application log to identify the cause of problems.</span></span> <span data-ttu-id="78ca0-111">例如，监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志时，您可能会遇到不包含原因信息的错误消息。</span><span class="sxs-lookup"><span data-stu-id="78ca0-111">For example, while monitoring the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, you may encounter error messages that do not contain cause information.</span></span> <span data-ttu-id="78ca0-112">通过比较两个日志中的事件日期和时间，可以缩小可能原因的范围。</span><span class="sxs-lookup"><span data-stu-id="78ca0-112">By comparing the dates and times for events between these logs, you can narrow the list of probable causes.</span></span> <span data-ttu-id="78ca0-113">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 日志文件查看器可以将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理和 Windows 日志集成到一个列表，这样可以轻松了解相关的服务器事件和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 事件。</span><span class="sxs-lookup"><span data-stu-id="78ca0-113">The [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Log File Viewer lets you integrate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, and the Windows logs into a single list, making it easy to understand related server events and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events.</span></span> <span data-ttu-id="78ca0-114">有关详细信息，请参阅 SQL Server 联机丛书中的主题“日志文件查看器”。</span><span class="sxs-lookup"><span data-stu-id="78ca0-114">For more information, see the topic "Log File Viewer" in SQL Server Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="78ca0-115">本节内容</span><span class="sxs-lookup"><span data-stu-id="78ca0-115">In This Section</span></span>  
  
|<span data-ttu-id="78ca0-116">主题</span><span class="sxs-lookup"><span data-stu-id="78ca0-116">Topic</span></span>|<span data-ttu-id="78ca0-117">说明</span><span class="sxs-lookup"><span data-stu-id="78ca0-117">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="78ca0-118">查看 SQL Server 错误日志</span><span class="sxs-lookup"><span data-stu-id="78ca0-118">Viewing the SQL Server Error Log</span></span>](../../../2014/tools/configuration-manager/viewing-the-sql-server-error-log.md)|<span data-ttu-id="78ca0-119">介绍了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志以及如何查看该日志。</span><span class="sxs-lookup"><span data-stu-id="78ca0-119">Contains information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and how to view it.</span></span>|  
|[<span data-ttu-id="78ca0-120">查看 Windows 应用程序日志</span><span class="sxs-lookup"><span data-stu-id="78ca0-120">Viewing the Windows Application Log</span></span>](viewing-the-windows-application-log.md)|<span data-ttu-id="78ca0-121">介绍了 Windows 应用程序日志以及如何查看该日志。</span><span class="sxs-lookup"><span data-stu-id="78ca0-121">Contains information about the Windows application log and how to view it.</span></span>|  
  
  
