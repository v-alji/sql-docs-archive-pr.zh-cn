---
title: MSSQLSERVER_30089 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9992 (Database Engine error)
ms.assetid: 188e5bde-6865-4740-a2b2-582be8f55c77
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d0b9c71ea620174f993ae87befed8a21bb3d0bfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586730"
---
# <a name="mssqlserver_30089"></a><span data-ttu-id="58162-102">MSSQLSERVER_30089</span><span class="sxs-lookup"><span data-stu-id="58162-102">MSSQLSERVER_30089</span></span>
    
## <a name="details"></a><span data-ttu-id="58162-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="58162-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="58162-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="58162-104">Product Name</span></span>|<span data-ttu-id="58162-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="58162-105">SQL Server</span></span>|  
|<span data-ttu-id="58162-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="58162-106">Event ID</span></span>|<span data-ttu-id="58162-107">30089</span><span class="sxs-lookup"><span data-stu-id="58162-107">30089</span></span>|  
|<span data-ttu-id="58162-108">事件源</span><span class="sxs-lookup"><span data-stu-id="58162-108">Event Source</span></span>|<span data-ttu-id="58162-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="58162-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="58162-110">组件</span><span class="sxs-lookup"><span data-stu-id="58162-110">Component</span></span>|<span data-ttu-id="58162-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="58162-111">SQLEngine</span></span>|  
|<span data-ttu-id="58162-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="58162-112">Symbolic Name</span></span>|<span data-ttu-id="58162-113">IFTS_FDHOST_TERMINATEDABNORMAL</span><span class="sxs-lookup"><span data-stu-id="58162-113">IFTS_FDHOST_TERMINATEDABNORMAL</span></span>|  
|<span data-ttu-id="58162-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="58162-114">Message Text</span></span>|<span data-ttu-id="58162-115">全文筛选器后台程序宿主(FDHost)进程已异常停止。</span><span class="sxs-lookup"><span data-stu-id="58162-115">The fulltext filter daemon host (FDHost) process has stopped abnormally.</span></span> <span data-ttu-id="58162-116">如果在执行全文检索或查询处理期间配置错误或工作不正常的语言组件(如断字器、词干分析器或筛选器)造成了无法恢复的错误，则会出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="58162-116">This can occur if an incorrectly configured or malfunctioning linguistic component, such as a wordbreaker, stemmer or filter has caused an irrecoverable error during full-text indexing or query processing.</span></span> <span data-ttu-id="58162-117">该进程将自动重新启动。</span><span class="sxs-lookup"><span data-stu-id="58162-117">The process will be restarted automatically.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="58162-118">说明</span><span class="sxs-lookup"><span data-stu-id="58162-118">Explanation</span></span>  
 <span data-ttu-id="58162-119">全文筛选器后台程序宿主遇到了某个强制其异常停止的问题。</span><span class="sxs-lookup"><span data-stu-id="58162-119">The full-text filter daemon host has encountered some problem that has forced it to stop abnormally.</span></span> <span data-ttu-id="58162-120">该问题可能是由格式不正确的文档、筛选器或断字器中的错误或者筛选器后台程序中的问题引起的。</span><span class="sxs-lookup"><span data-stu-id="58162-120">The cause of the problem could be a badly formatted document, a bug in the filter or word-breaker, or a problem in filter daemon.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="58162-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="58162-121">User Action</span></span>  
 <span data-ttu-id="58162-122">通常，该后台程序将能够从错误中恢复。</span><span class="sxs-lookup"><span data-stu-id="58162-122">Typically, the daemon will recover from the error.</span></span> <span data-ttu-id="58162-123">如果它仍旧失败，则有必要排除故障。</span><span class="sxs-lookup"><span data-stu-id="58162-123">If it is consistently failing, troubleshooting is necessary.</span></span> <span data-ttu-id="58162-124">请尝试执行下列操作来隔离此问题：</span><span class="sxs-lookup"><span data-stu-id="58162-124">Try the following to isolate the issue:</span></span>  
  
1.  <span data-ttu-id="58162-125">如果最近安装过新的语言组件，请将它从系统中删除。</span><span class="sxs-lookup"><span data-stu-id="58162-125">If a new linguistic component has been installed recently, remove it from the system.</span></span>  
  
2.  <span data-ttu-id="58162-126">查看爬网日志，找出无法对其建立全文检索的任何新文档并将其删除。</span><span class="sxs-lookup"><span data-stu-id="58162-126">Look at the crawl log to identify any new document that failed to be full-text indexed, and remove it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58162-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="58162-127">See Also</span></span>  
 <span data-ttu-id="58162-128">[sp_help_fulltext_system_components &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="58162-128">[sp_help_fulltext_system_components &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) </span></span>  
 <span data-ttu-id="58162-129">[配置和管理断字符和词干分析器以便搜索](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md) </span><span class="sxs-lookup"><span data-stu-id="58162-129">[Configure and Manage Word Breakers and Stemmers for Search](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md) </span></span>  
 [<span data-ttu-id="58162-130">配置和管理搜索筛选器</span><span class="sxs-lookup"><span data-stu-id="58162-130">Configure and Manage Filters for Search</span></span>](../search/configure-and-manage-filters-for-search.md)  
  
  
