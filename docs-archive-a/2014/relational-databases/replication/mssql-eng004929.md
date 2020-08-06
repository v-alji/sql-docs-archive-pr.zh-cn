---
title: MSSQL_ENG004929 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG004929 error
ms.assetid: 1d9b1d88-1fbf-4089-b392-687d3b0220ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b202b28eabe1feb1ed180bda0d58d2e84c7d10d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577560"
---
# <a name="mssql_eng004929"></a><span data-ttu-id="87d36-102">MSSQL_ENG004929</span><span class="sxs-lookup"><span data-stu-id="87d36-102">MSSQL_ENG004929</span></span>
    
## <a name="message-details"></a><span data-ttu-id="87d36-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="87d36-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="87d36-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="87d36-104">Product Name</span></span>|<span data-ttu-id="87d36-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="87d36-105">SQL Server</span></span>|  
|<span data-ttu-id="87d36-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="87d36-106">Event ID</span></span>|<span data-ttu-id="87d36-107">4929</span><span class="sxs-lookup"><span data-stu-id="87d36-107">4929</span></span>|  
|<span data-ttu-id="87d36-108">事件源</span><span class="sxs-lookup"><span data-stu-id="87d36-108">Event Source</span></span>|<span data-ttu-id="87d36-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="87d36-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="87d36-110">组件</span><span class="sxs-lookup"><span data-stu-id="87d36-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="87d36-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="87d36-111">Symbolic Name</span></span>||  
|<span data-ttu-id="87d36-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="87d36-112">Message Text</span></span>|<span data-ttu-id="87d36-113">无法更改 %S_MSG '%.\*ls'，因为正在为复制而发布它。</span><span class="sxs-lookup"><span data-stu-id="87d36-113">Cannot alter the %S_MSG '%.\*ls' because it is being published for replication.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="87d36-114">说明</span><span class="sxs-lookup"><span data-stu-id="87d36-114">Explanation</span></span>  
 <span data-ttu-id="87d36-115">尝试删除为事务性复制而发布的表的主键约束时，通常会发生此错误。</span><span class="sxs-lookup"><span data-stu-id="87d36-115">This error typically occurs if you attempt to drop the primary key constraint on a table that is published for transactional replication.</span></span> <span data-ttu-id="87d36-116">事务性复制要求每个已发布表都具有主键，因此不能删除约束。</span><span class="sxs-lookup"><span data-stu-id="87d36-116">Transactional replication requires a primary key for each published table; therefore the constraint cannot be dropped.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="87d36-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="87d36-117">User Action</span></span>  
 <span data-ttu-id="87d36-118">若要删除约束，请先删除与表关联的项目。</span><span class="sxs-lookup"><span data-stu-id="87d36-118">To drop the constraint, first drop the article associated with the table.</span></span> <span data-ttu-id="87d36-119">有关详细信息，请参阅[向现有发布添加项目和从中删除项目](publish/add-articles-to-and-drop-articles-from-existing-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="87d36-119">For more information, see [Add Articles to and Drop Articles from Existing Publications](publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span></span> <span data-ttu-id="87d36-120">如果此错误发生在未复制的数据库中，请执行 [sp_removedbreplication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)，以确保此数据库中的对象不会标记为已复制。</span><span class="sxs-lookup"><span data-stu-id="87d36-120">If this error occurs in a database that is not replicated, execute [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) to ensure objects in the database are not marked as replicated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87d36-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="87d36-121">See Also</span></span>  
 [<span data-ttu-id="87d36-122">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="87d36-122">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
