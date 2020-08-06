---
title: MSSQL_ENG003724 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG003724 error
ms.assetid: 10cb119d-92df-4124-b85d-cd2f2666c99c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dbfb68575c5ffa73276b3bbe1643381c3f0cc412
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693737"
---
# <a name="mssql_eng003724"></a><span data-ttu-id="69e95-102">MSSQL_ENG003724</span><span class="sxs-lookup"><span data-stu-id="69e95-102">MSSQL_ENG003724</span></span>
    
## <a name="message-details"></a><span data-ttu-id="69e95-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="69e95-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="69e95-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="69e95-104">Product Name</span></span>|<span data-ttu-id="69e95-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="69e95-105">SQL Server</span></span>|  
|<span data-ttu-id="69e95-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="69e95-106">Event ID</span></span>|<span data-ttu-id="69e95-107">3724</span><span class="sxs-lookup"><span data-stu-id="69e95-107">3724</span></span>|  
|<span data-ttu-id="69e95-108">事件源</span><span class="sxs-lookup"><span data-stu-id="69e95-108">Event Source</span></span>|<span data-ttu-id="69e95-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="69e95-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="69e95-110">组件</span><span class="sxs-lookup"><span data-stu-id="69e95-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="69e95-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="69e95-111">Symbolic Name</span></span>||  
|<span data-ttu-id="69e95-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="69e95-112">Message Text</span></span>|<span data-ttu-id="69e95-113">无法对 %S_MSG '%.\*ls' 执行 %S_MSG，因为它正用于复制。</span><span class="sxs-lookup"><span data-stu-id="69e95-113">Cannot %S_MSG the %S_MSG '%.\*ls' because it is being used for replication.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="69e95-114">说明</span><span class="sxs-lookup"><span data-stu-id="69e95-114">Explanation</span></span>  
 <span data-ttu-id="69e95-115">数据库中的对象经复制后，通常会在系统表 **sysarticles** （用于快照和事务发布）或 **sysmergearticles** （用于合并发布）中标记为已复制。</span><span class="sxs-lookup"><span data-stu-id="69e95-115">When objects in a database are replicated, they are marked as replicated in the system table **sysarticles** (for snapshot and transactional publications) or **sysmergearticles** (for merge publications).</span></span> <span data-ttu-id="69e95-116">尝试删除复制的对象时，会引发此错误。</span><span class="sxs-lookup"><span data-stu-id="69e95-116">If you attempt drop a replicated object, this error is raised.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="69e95-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="69e95-117">User Action</span></span>  
 <span data-ttu-id="69e95-118">尝试删除对象之前，请确保数据库对象未经复制。</span><span class="sxs-lookup"><span data-stu-id="69e95-118">Ensure the database object is not replicated before attempting to drop it.</span></span> <span data-ttu-id="69e95-119">例如：</span><span class="sxs-lookup"><span data-stu-id="69e95-119">For example:</span></span>  
  
-   <span data-ttu-id="69e95-120">如果此错误发生在发布数据库中，则先从发布中删除项目，然后再删除对象。</span><span class="sxs-lookup"><span data-stu-id="69e95-120">If the error occurs in the publication database, drop the article from the publication before dropping the object.</span></span> <span data-ttu-id="69e95-121">有关详细信息，请参阅[向现有发布添加项目和从中删除项目](publish/add-articles-to-and-drop-articles-from-existing-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="69e95-121">For more information, see [Add Articles to and Drop Articles from Existing Publications](publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
-   <span data-ttu-id="69e95-122">如果此错误发生在订阅数据库中，则先删除订阅，然后再删除对象。</span><span class="sxs-lookup"><span data-stu-id="69e95-122">If the error occurs in the subscription database, drop the subscription before dropping the object.</span></span> <span data-ttu-id="69e95-123">有关详细信息，请参阅[订阅发布](subscribe-to-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="69e95-123">For more information, see [Subscribe to Publications](subscribe-to-publications.md).</span></span> <span data-ttu-id="69e95-124">对于事务发布的订阅，可以删除单个项目的订阅，而不用删除整个发布。</span><span class="sxs-lookup"><span data-stu-id="69e95-124">For subscriptions to transactional publications, it is possible to drop the subscription to an individual article rather than the entire publication.</span></span> <span data-ttu-id="69e95-125">有关详细信息，请参阅 [sp_dropsubscription (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="69e95-125">For more information, see [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql).</span></span>  
  
 <span data-ttu-id="69e95-126">如果此错误发生在未复制的数据库中，请执行 [sp_removedbreplication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)，以确保此数据库中的对象不会标记为已复制。</span><span class="sxs-lookup"><span data-stu-id="69e95-126">If this error occurs in a database that is not replicated, execute [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) to ensure objects in the database are not marked as replicated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69e95-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="69e95-127">See Also</span></span>  
 [<span data-ttu-id="69e95-128">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="69e95-128">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
