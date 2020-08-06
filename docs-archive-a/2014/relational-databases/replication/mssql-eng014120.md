---
title: MSSQL_ENG014120 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014120 error
ms.assetid: 6b169a3b-30da-4981-b998-b52d61811572
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e7f3484d9344a203ca8c44fee6b79605163ea069
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576666"
---
# <a name="mssql_eng014120"></a><span data-ttu-id="d62df-102">MSSQL_ENG014120</span><span class="sxs-lookup"><span data-stu-id="d62df-102">MSSQL_ENG014120</span></span>
    
## <a name="message-details"></a><span data-ttu-id="d62df-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="d62df-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d62df-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="d62df-104">Product Name</span></span>|<span data-ttu-id="d62df-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d62df-105">SQL Server</span></span>|  
|<span data-ttu-id="d62df-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="d62df-106">Event ID</span></span>|<span data-ttu-id="d62df-107">14120</span><span class="sxs-lookup"><span data-stu-id="d62df-107">14120</span></span>|  
|<span data-ttu-id="d62df-108">事件源</span><span class="sxs-lookup"><span data-stu-id="d62df-108">Event Source</span></span>|<span data-ttu-id="d62df-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d62df-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d62df-110">组件</span><span class="sxs-lookup"><span data-stu-id="d62df-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="d62df-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="d62df-111">Symbolic Name</span></span>||  
|<span data-ttu-id="d62df-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="d62df-112">Message Text</span></span>|<span data-ttu-id="d62df-113">无法删除分发数据库 '%s'。</span><span class="sxs-lookup"><span data-stu-id="d62df-113">Could not drop the distribution database '%s'.</span></span> <span data-ttu-id="d62df-114">此分发服务器数据库与发布服务器相关联。</span><span class="sxs-lookup"><span data-stu-id="d62df-114">This distributor database is associated with a Publisher.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d62df-115">说明</span><span class="sxs-lookup"><span data-stu-id="d62df-115">Explanation</span></span>  
 <span data-ttu-id="d62df-116">分发数据库存储事务性复制的所有复制和事务类型的元数据和历史记录数据。</span><span class="sxs-lookup"><span data-stu-id="d62df-116">The distribution database stores metadata and history data for all types of replication and transactions for transactional replication.</span></span> <span data-ttu-id="d62df-117">如果试图删除与一个或多个发布服务器相关联的分发数据库，将发生此错误。</span><span class="sxs-lookup"><span data-stu-id="d62df-117">This error occurs if you attempt to drop a distribution database that is associated with one or more Publishers.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d62df-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="d62df-118">User Action</span></span>  
 <span data-ttu-id="d62df-119">若要删除分发数据库，必须先删除分发服务器与发布服务器之间的关联。</span><span class="sxs-lookup"><span data-stu-id="d62df-119">To drop a distribution database you must first drop the association between the Distributor and the Publisher.</span></span> <span data-ttu-id="d62df-120">有关详细信息，请参阅 [sp_dropdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d62df-120">For more information, see [sp_dropdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d62df-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d62df-121">See Also</span></span>  
 <span data-ttu-id="d62df-122">[错误和事件参考（复制）](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="d62df-122">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 [<span data-ttu-id="d62df-123">配置分发</span><span class="sxs-lookup"><span data-stu-id="d62df-123">Configure Distribution</span></span>](configure-distribution.md)  
  
  
