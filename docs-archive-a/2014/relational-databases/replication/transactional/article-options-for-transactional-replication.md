---
title: 事务复制的项目选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], transactional replication options
- transactional replication, article options
ms.assetid: 3469b185-0ea5-4690-a71c-717230d886b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1cc13a3d11e35ed47eac4ff401fb8b7cb607b32b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587336"
---
# <a name="article-options-for-transactional-replication"></a><span data-ttu-id="7dbe5-102">事务复制的项目选项</span><span class="sxs-lookup"><span data-stu-id="7dbe5-102">Article Options for Transactional Replication</span></span>
  <span data-ttu-id="7dbe5-103">事务发布中的项目具有多个选项。</span><span class="sxs-lookup"><span data-stu-id="7dbe5-103">There are a number of options for articles in transactional publications.</span></span> <span data-ttu-id="7dbe5-104">使用事务复制，可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="7dbe5-104">With transactional replication, you can do the following:</span></span>  
  
-   <span data-ttu-id="7dbe5-105">指定更改如何从发布服务器传播到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="7dbe5-105">Specify how changes are propagated from the Publisher to Subscribers.</span></span> <span data-ttu-id="7dbe5-106">有关详细信息，请参阅[指定如何传播事务项目的更改](transactional-articles-specify-how-changes-are-propagated.md)。</span><span class="sxs-lookup"><span data-stu-id="7dbe5-106">For more information, see [Specify How Changes Are Propagated for Transactional Articles](transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
-   <span data-ttu-id="7dbe5-107">指定应复制存储过程的执行。</span><span class="sxs-lookup"><span data-stu-id="7dbe5-107">Specify that the execution of a stored procedure be replicated.</span></span> <span data-ttu-id="7dbe5-108">这对于复制面向维护的存储过程的结果很有用处，这种存储过程的结果会影响大量的数据。</span><span class="sxs-lookup"><span data-stu-id="7dbe5-108">This is useful in replicating the results of maintenance-oriented stored procedures that affect large amounts of data.</span></span> <span data-ttu-id="7dbe5-109">有关详细信息，请参阅 [Publishing Stored Procedure Execution in Transactional Replication](publishing-stored-procedure-execution-in-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="7dbe5-109">For more information, see [Publishing Stored Procedure Execution in Transactional Replication](publishing-stored-procedure-execution-in-transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="7dbe5-110">指定架构选项（例如，是否将约束和触发器复制到订阅服务器）。</span><span class="sxs-lookup"><span data-stu-id="7dbe5-110">Specify schema options, such as whether constraints and triggers are copied to the Subscriber.</span></span> <span data-ttu-id="7dbe5-111">有关详细信息，请参阅 [指定架构选项](../publish/specify-schema-options.md)。</span><span class="sxs-lookup"><span data-stu-id="7dbe5-111">For more information, see [Specify Schema Options](../publish/specify-schema-options.md).</span></span>  
  
-   <span data-ttu-id="7dbe5-112">使用行筛选器和列筛选器。</span><span class="sxs-lookup"><span data-stu-id="7dbe5-112">Use row filters and column filters.</span></span> <span data-ttu-id="7dbe5-113">通过筛选表项目，可以为要发布的数据创建分区。</span><span class="sxs-lookup"><span data-stu-id="7dbe5-113">Filtering table articles enables you to create partitions of data to be published.</span></span> <span data-ttu-id="7dbe5-114">有关详细信息，请参阅[筛选已发布数据](../publish/filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7dbe5-114">For more information, see [Filter Published Data](../publish/filter-published-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dbe5-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7dbe5-115">See Also</span></span>  
 [<span data-ttu-id="7dbe5-116">发布数据和数据库对象</span><span class="sxs-lookup"><span data-stu-id="7dbe5-116">Publish Data and Database Objects</span></span>](../publish/publish-data-and-database-objects.md)  
  
  
