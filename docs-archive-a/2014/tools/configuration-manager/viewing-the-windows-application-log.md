---
title: 查看 Windows 应用程序日志 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- application logs [SQL Server]
- Windows application logs [SQL Server]
- viewing Windows application logs
- errors [SQL Server], logs
- system logs [SQL Server]
- security logs [SQL Server]
- displaying Windows application logs
- logs [SQL Server], Windows application logs
ms.assetid: f9853b74-7db7-47cc-b957-e49ed5bc0a1a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 22f900a0b203e652bbc9cc6e9638711d138756c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586027"
---
# <a name="viewing-the-windows-application-log"></a><span data-ttu-id="cc401-102">查看 Windows 应用程序日志</span><span class="sxs-lookup"><span data-stu-id="cc401-102">Viewing the Windows Application Log</span></span>
  <span data-ttu-id="cc401-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置为使用 Microsoft Windows 应用程序日志后，每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会话都将新事件写入该日志中。</span><span class="sxs-lookup"><span data-stu-id="cc401-103">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to use the Microsoft Windows application log, each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] session writes new events to that log.</span></span> <span data-ttu-id="cc401-104">与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志不同，不是每次启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例时都创建新的应用程序日志。</span><span class="sxs-lookup"><span data-stu-id="cc401-104">Unlike the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, a new application log is not created each time you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="cc401-105">可以通过使用 Windows 事件查看器或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的日志查看器来查看和管理 Windows 应用程序日志。</span><span class="sxs-lookup"><span data-stu-id="cc401-105">View and manage the Windows application log by using Windows Event Viewer or the Log Viewer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="cc401-106">可以使用事件查看器查看三种日志。</span><span class="sxs-lookup"><span data-stu-id="cc401-106">There are three logs that can be viewed with Event Viewer.</span></span>  
  
|<span data-ttu-id="cc401-107">Windows 日志类型</span><span class="sxs-lookup"><span data-stu-id="cc401-107">Windows log type</span></span>|<span data-ttu-id="cc401-108">说明</span><span class="sxs-lookup"><span data-stu-id="cc401-108">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="cc401-109">系统日志</span><span class="sxs-lookup"><span data-stu-id="cc401-109">System log</span></span>|<span data-ttu-id="cc401-110">记录由 Windows 操作系统组件记录的事件。</span><span class="sxs-lookup"><span data-stu-id="cc401-110">Records events logged by the Windows operating system components.</span></span> <span data-ttu-id="cc401-111">例如，如果启动时驱动程序或其他系统组件加载失败，该信息将记录在系统日志中。</span><span class="sxs-lookup"><span data-stu-id="cc401-111">For example, the failure of a driver or other system component to load during startup is recorded in the system log.</span></span>|  
|<span data-ttu-id="cc401-112">安全日志</span><span class="sxs-lookup"><span data-stu-id="cc401-112">Security log</span></span>|<span data-ttu-id="cc401-113">记录安全性事件，例如登录尝试失败。</span><span class="sxs-lookup"><span data-stu-id="cc401-113">Records security events, such as failed login attempts.</span></span> <span data-ttu-id="cc401-114">这可以帮助跟踪对安全系统的更改，发现对安全的可能的破坏。</span><span class="sxs-lookup"><span data-stu-id="cc401-114">This helps track changes to the security system and identify possible breaches to security.</span></span> <span data-ttu-id="cc401-115">例如，对系统的登录尝试可能记录在安全日志中，具体情况取决于用户管理器中的审核设置。</span><span class="sxs-lookup"><span data-stu-id="cc401-115">For example, attempts to log on to the system may be recorded in the security log, depending on the audit settings in the User Manager.</span></span><br /><br /> <span data-ttu-id="cc401-116">只有 **sysadmin** 固定服务器角色成员可以查看安全日志。</span><span class="sxs-lookup"><span data-stu-id="cc401-116">Only members of the **sysadmin** fixed server role can view the security log.</span></span>|  
|<span data-ttu-id="cc401-117">应用程序日志</span><span class="sxs-lookup"><span data-stu-id="cc401-117">Application log</span></span>|<span data-ttu-id="cc401-118">记录由应用程序记录的事件。</span><span class="sxs-lookup"><span data-stu-id="cc401-118">Records events that are logged by applications.</span></span> <span data-ttu-id="cc401-119">例如，数据库应用程序可能会将文件错误记录在应用程序日志中。</span><span class="sxs-lookup"><span data-stu-id="cc401-119">For example, a database application might record a file error in the application log.</span></span>|  
  
 <span data-ttu-id="cc401-120">有关使用事件查看器、管理应用程序日志及了解其表示的信息的详细信息，请参阅 Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="cc401-120">For more information about using Event Viewer, managing the application log, and understanding the information it presents, see the Windows documentation.</span></span>  
  
 <span data-ttu-id="cc401-121">**查看 Windows 应用程序日志**</span><span class="sxs-lookup"><span data-stu-id="cc401-121">**To view the Windows application log**</span></span>  
  
 [<span data-ttu-id="cc401-122">查看 Windows 应用程序日志 (Windows)</span><span class="sxs-lookup"><span data-stu-id="cc401-122">View the Windows Application Log &#40;Windows&#41;</span></span>](../../relational-databases/performance/view-the-windows-application-log-windows-10.md)  
  
  
