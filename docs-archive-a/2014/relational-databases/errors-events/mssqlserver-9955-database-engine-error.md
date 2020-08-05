---
title: MSSQLSERVER_9955 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9955 (Database Engine error)
ms.assetid: 77f30570-7790-4747-b372-eac71c036e19
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 56b9f9b4b7923f8973bd7167c3c1bf77e92300c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581217"
---
# <a name="mssqlserver_9955"></a><span data-ttu-id="07f9d-102">MSSQLSERVER_9955</span><span class="sxs-lookup"><span data-stu-id="07f9d-102">MSSQLSERVER_9955</span></span>
    
## <a name="details"></a><span data-ttu-id="07f9d-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="07f9d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="07f9d-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="07f9d-104">Product Name</span></span>|<span data-ttu-id="07f9d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="07f9d-105">SQL Server</span></span>|  
|<span data-ttu-id="07f9d-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="07f9d-106">Event ID</span></span>|<span data-ttu-id="07f9d-107">9955</span><span class="sxs-lookup"><span data-stu-id="07f9d-107">9955</span></span>|  
|<span data-ttu-id="07f9d-108">事件源</span><span class="sxs-lookup"><span data-stu-id="07f9d-108">Event Source</span></span>|<span data-ttu-id="07f9d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="07f9d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="07f9d-110">组件</span><span class="sxs-lookup"><span data-stu-id="07f9d-110">Component</span></span>|<span data-ttu-id="07f9d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="07f9d-111">SQLEngine</span></span>|  
|<span data-ttu-id="07f9d-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="07f9d-112">Symbolic Name</span></span>|<span data-ttu-id="07f9d-113">FTXT2_MSSEARCHACCESSDENY</span><span class="sxs-lookup"><span data-stu-id="07f9d-113">FTXT2_MSSEARCHACCESSDENY</span></span>|  
|<span data-ttu-id="07f9d-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="07f9d-114">Message Text</span></span>|<span data-ttu-id="07f9d-115">SQL Server 无法创建命名管道 '%ls' 以与全文筛选器后台程序通信(Windows 错误: %d)。</span><span class="sxs-lookup"><span data-stu-id="07f9d-115">SQL Server failed to create named pipe '%ls' to communicate with the full-text filter daemon (Windows error: %d).</span></span> <span data-ttu-id="07f9d-116">筛选器后台主机进程已有一个命名管道，系统资源不足，或者对筛选器后台程序帐户组的安全标识号(SID)查找失败。</span><span class="sxs-lookup"><span data-stu-id="07f9d-116">Either a named pipe already exists for a filter daemon host process, the system is low on resources, or the security identification number (SID) lookup for the filter daemon account group failed.</span></span> <span data-ttu-id="07f9d-117">若要纠正此错误，请终止任何正在运行的全文筛选器后台进程，并在必要时重新配置全文后台程序启动程序服务帐户。</span><span class="sxs-lookup"><span data-stu-id="07f9d-117">To resolve this error, terminate any running full-text filter daemon processes, and if necessary reconfigure the full-text daemon launcher service account.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="07f9d-118">说明</span><span class="sxs-lookup"><span data-stu-id="07f9d-118">Explanation</span></span>  
 <span data-ttu-id="07f9d-119">当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 无法创建用来与全文筛选器后台程序通信的命名管道时，会出现此消息。</span><span class="sxs-lookup"><span data-stu-id="07f9d-119">This message occurs because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failed to create a named pipe to communicate with the full-text filter daemon.</span></span> <span data-ttu-id="07f9d-120">筛选器后台主机进程已有一个命名管道，系统资源不足，或者对筛选器后台程序帐户组的安全标识号(SID)查找失败。</span><span class="sxs-lookup"><span data-stu-id="07f9d-120">Either a named pipe already exists for a filter daemon host process, the system is low on resources, or the security identification number (SID) lookup for the filter daemon account group failed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="07f9d-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="07f9d-121">User Action</span></span>  
 <span data-ttu-id="07f9d-122">若要纠正此错误，请终止任何正在运行的全文筛选器后台进程，并在必要时使用 SQL Server 配置管理器重新配置全文后台程序主机帐户。</span><span class="sxs-lookup"><span data-stu-id="07f9d-122">To resolve this error, terminate any running full-text filter daemon processes, and if necessary reconfigure the full-text daemon host account by using the SQL Server Configuration Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07f9d-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07f9d-123">See Also</span></span>  
 <span data-ttu-id="07f9d-124">[SQL Server 配置管理器](../sql-server-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="07f9d-124">[SQL Server Configuration Manager](../sql-server-configuration-manager.md) </span></span>  
 <span data-ttu-id="07f9d-125">[设置全文筛选器后台程序启动器的服务帐户](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span><span class="sxs-lookup"><span data-stu-id="07f9d-125">[Set the Service Account for the Full-text Filter Daemon Launcher](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span></span>  
 [<span data-ttu-id="07f9d-126">全文搜索</span><span class="sxs-lookup"><span data-stu-id="07f9d-126">Full-Text Search</span></span>](../search/full-text-search.md)  
  
  
