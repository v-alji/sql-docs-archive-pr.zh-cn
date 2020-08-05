---
title: 日志文件查看器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Log File Viewer
ms.assetid: a4ea7fc8-1cb2-4c98-bc86-8991c5e748b2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5139a32838070b817fce3bccf22b9fe08b5012e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580731"
---
# <a name="log-file-viewer"></a><span data-ttu-id="1ee4d-102">日志文件查看器</span><span class="sxs-lookup"><span data-stu-id="1ee4d-102">Log File Viewer</span></span>
  <span data-ttu-id="1ee4d-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的日志文件查看器用于访问有关在日志文件中捕获的错误和事件的信息。</span><span class="sxs-lookup"><span data-stu-id="1ee4d-103">Log File Viewer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is used to access information about errors and events that are captured in log files.</span></span>  
  
## <a name="benefits-of-using-log-file-viewer"></a><span data-ttu-id="1ee4d-104">使用日志文件查看器的优点</span><span class="sxs-lookup"><span data-stu-id="1ee4d-104">Benefits of using Log File Viewer</span></span>  
 <span data-ttu-id="1ee4d-105">目标实例处于脱机状态或无法启动时，可以从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的本地或远程实例查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日志文件。</span><span class="sxs-lookup"><span data-stu-id="1ee4d-105">You can view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files from a local or remote instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] when the target instance is offline or cannot start.</span></span> <span data-ttu-id="1ee4d-106">您可以从注册的服务器访问脱机日志文件，或者以编程方式通过 WMI 和 WQL（WMI 查询语言）查询访问这些文件。</span><span class="sxs-lookup"><span data-stu-id="1ee4d-106">You can access the offline log files from Registered Servers, or programmatically through WMI and WQL (WMI Query Language) queries.</span></span> <span data-ttu-id="1ee4d-107">有关详细信息，请参阅 [查看脱机日志文件](view-offline-log-files.md)。</span><span class="sxs-lookup"><span data-stu-id="1ee4d-107">For more information, see [View Offline Log Files](view-offline-log-files.md).</span></span> <span data-ttu-id="1ee4d-108">以下是您可以使用日志文件查看器访问的日志文件的类型：</span><span class="sxs-lookup"><span data-stu-id="1ee4d-108">Following are the types of log files you can access using Log File Viewer:</span></span>  
  
-   <span data-ttu-id="1ee4d-109">审核集合</span><span class="sxs-lookup"><span data-stu-id="1ee4d-109">Audit Collection</span></span>  
  
-   <span data-ttu-id="1ee4d-110">数据收集</span><span class="sxs-lookup"><span data-stu-id="1ee4d-110">Data Collection</span></span>  
  
-   <span data-ttu-id="1ee4d-111">数据库邮件</span><span class="sxs-lookup"><span data-stu-id="1ee4d-111">Database Mail</span></span>  
  
-   <span data-ttu-id="1ee4d-112">作业历史记录</span><span class="sxs-lookup"><span data-stu-id="1ee4d-112">Job History</span></span>  
  
-   <span data-ttu-id="1ee4d-113">维护计划</span><span class="sxs-lookup"><span data-stu-id="1ee4d-113">Maintenance Plans</span></span>  
  
-   <span data-ttu-id="1ee4d-114">远程维护计划</span><span class="sxs-lookup"><span data-stu-id="1ee4d-114">Remote Maintenance Plans</span></span>  
  
-   <span data-ttu-id="1ee4d-115">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1ee4d-115">SQL Server</span></span>  
  
-   <span data-ttu-id="1ee4d-116">SQL Server 代理</span><span class="sxs-lookup"><span data-stu-id="1ee4d-116">SQL Server Agent</span></span>  
  
-   <span data-ttu-id="1ee4d-117">Windows NT（这些是还可以从事件查看器访问的 Windows 事件。）</span><span class="sxs-lookup"><span data-stu-id="1ee4d-117">Windows NT (These are Windows events that can also be accessed from Event Viewer.)</span></span>  
  
## <a name="log-file-viewer-tasks"></a><span data-ttu-id="1ee4d-118">日志文件查看器任务</span><span class="sxs-lookup"><span data-stu-id="1ee4d-118">Log File Viewer Tasks</span></span>  
  
|<span data-ttu-id="1ee4d-119">任务说明</span><span class="sxs-lookup"><span data-stu-id="1ee4d-119">Task Description</span></span>|<span data-ttu-id="1ee4d-120">主题</span><span class="sxs-lookup"><span data-stu-id="1ee4d-120">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="1ee4d-121">介绍如何根据您要查看的信息来打开日志文件查看器。</span><span class="sxs-lookup"><span data-stu-id="1ee4d-121">Describes how to open Log File Viewer depending on the information that you want to view.</span></span>|[<span data-ttu-id="1ee4d-122">打开日志文件查看器</span><span class="sxs-lookup"><span data-stu-id="1ee4d-122">Open Log File Viewer</span></span>](open-log-file-viewer.md)|  
|<span data-ttu-id="1ee4d-123">介绍如何通过注册的服务器来查看脱机日志文件以及如何验证 WMI 权限。</span><span class="sxs-lookup"><span data-stu-id="1ee4d-123">Describes how to view offline log files through registered servers and how to verify WMI permissions.</span></span>|[<span data-ttu-id="1ee4d-124">查看脱机日志文件</span><span class="sxs-lookup"><span data-stu-id="1ee4d-124">View Offline Log Files</span></span>](view-offline-log-files.md)|  
|<span data-ttu-id="1ee4d-125">提供日志文件查看器的 F1 帮助。</span><span class="sxs-lookup"><span data-stu-id="1ee4d-125">Provides Log File Viewer F1 Help.</span></span>|[<span data-ttu-id="1ee4d-126">日志文件查看器 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="1ee4d-126">Log File Viewer F1 Help</span></span>](log-file-viewer-f1-help.md)|  
  
## <a name="see-also"></a><span data-ttu-id="1ee4d-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1ee4d-127">See Also</span></span>  
 <span data-ttu-id="1ee4d-128">[SQL Server Audit（数据库引擎）](../security/auditing/sql-server-audit-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="1ee4d-128">[SQL Server Audit &#40;Database Engine&#41;](../security/auditing/sql-server-audit-database-engine.md) </span></span>  
 [<span data-ttu-id="1ee4d-129">SQL Server 代理错误日志</span><span class="sxs-lookup"><span data-stu-id="1ee4d-129">SQL Server Agent Error Log</span></span>](../../ssms/agent/sql-server-agent-error-log.md)  
  
  
