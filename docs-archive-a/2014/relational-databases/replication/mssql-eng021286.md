---
title: MSSQL_ENG021286 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021286 error
ms.assetid: b63620b7-1c6d-46f7-90ea-3a8e99af8de4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 592c788b563046e5949217c94006de2d4755f049
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688824"
---
# <a name="mssql_eng021286"></a><span data-ttu-id="1d9f4-102">MSSQL_ENG021286</span><span class="sxs-lookup"><span data-stu-id="1d9f4-102">MSSQL_ENG021286</span></span>
    
## <a name="message-details"></a><span data-ttu-id="1d9f4-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="1d9f4-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1d9f4-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="1d9f4-104">Product Name</span></span>|<span data-ttu-id="1d9f4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1d9f4-105">SQL Server</span></span>|  
|<span data-ttu-id="1d9f4-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="1d9f4-106">Event ID</span></span>|<span data-ttu-id="1d9f4-107">21286</span><span class="sxs-lookup"><span data-stu-id="1d9f4-107">21286</span></span>|  
|<span data-ttu-id="1d9f4-108">事件源</span><span class="sxs-lookup"><span data-stu-id="1d9f4-108">Event Source</span></span>|<span data-ttu-id="1d9f4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1d9f4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1d9f4-110">组件</span><span class="sxs-lookup"><span data-stu-id="1d9f4-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="1d9f4-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="1d9f4-111">Symbolic Name</span></span>||  
|<span data-ttu-id="1d9f4-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="1d9f4-112">Message Text</span></span>|<span data-ttu-id="1d9f4-113">冲突表 '%s' 不存在。</span><span class="sxs-lookup"><span data-stu-id="1d9f4-113">Conflict table '%s' does not exist.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1d9f4-114">说明</span><span class="sxs-lookup"><span data-stu-id="1d9f4-114">Explanation</span></span>  
 <span data-ttu-id="1d9f4-115">如果 [sysmergearticles (Transact-SQL)](/sql/relational-databases/system-tables/sysmergearticles-transact-sql) 中所列项目的冲突表实际不存在，则会引发此错误。</span><span class="sxs-lookup"><span data-stu-id="1d9f4-115">This error is raised if the conflict table for an article listed in [sysmergearticles &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysmergearticles-transact-sql) does not actually exist.</span></span> <span data-ttu-id="1d9f4-116">尝试向为合并复制发布的表中添加列或从中删除列，也会发生此错误。</span><span class="sxs-lookup"><span data-stu-id="1d9f4-116">The error can occur when you attempt to add a column to or drop a column from a table published for merge replication.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1d9f4-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="1d9f4-117">User Action</span></span>  
 <span data-ttu-id="1d9f4-118">对缺少冲突表的数据库执行 [DBCC CHECKDB (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)，以验证是否不存在数据一致性问题。</span><span class="sxs-lookup"><span data-stu-id="1d9f4-118">Execute [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database with the missing conflict table to verify there are no data consistency issues.</span></span>  
  
 <span data-ttu-id="1d9f4-119">如果订阅服务器上缺少冲突表，请删除订阅并重新创建它。</span><span class="sxs-lookup"><span data-stu-id="1d9f4-119">If the conflict table is missing on a Subscriber, drop the subscription and recreate it.</span></span> <span data-ttu-id="1d9f4-120">如果发布服务器上缺少冲突表，请删除所有订阅，删除发布，然后重新创建发布和所有订阅。</span><span class="sxs-lookup"><span data-stu-id="1d9f4-120">If the conflict table is missing on a Publisher, drop all subscriptions, drop the publication, and then recreate the publication and all subscriptions.</span></span> <span data-ttu-id="1d9f4-121">有关详细信息，请参阅[发布数据和数据库对象](publish/publish-data-and-database-objects.md)和[订阅发布](subscribe-to-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="1d9f4-121">For more information, see [Publish Data and Database Objects](publish/publish-data-and-database-objects.md) and [Subscribe to Publications](subscribe-to-publications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d9f4-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d9f4-122">See Also</span></span>  
 [<span data-ttu-id="1d9f4-123">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="1d9f4-123">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
