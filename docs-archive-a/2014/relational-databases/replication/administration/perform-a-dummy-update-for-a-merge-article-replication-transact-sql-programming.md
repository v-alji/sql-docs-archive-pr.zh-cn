---
title: " (复制 Transact-sql 编程) 执行合并项目的虚更新 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_mergedummyupdate
- dummy updates [SQL Server replication]
ms.assetid: 2f339210-4d85-4843-bd94-e86f7100d3ef
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 07fa0f868b2c3f98496046b138424d7d3a2fa2fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691703"
---
# <a name="perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming"></a><span data-ttu-id="13111-102">执行合并项目的虚更新（复制 Transact-SQL 编程）</span><span class="sxs-lookup"><span data-stu-id="13111-102">Perform a Dummy Update for a Merge Article (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="13111-103">合并复制将触发器作为复制过程的一部分；在对发布的表进行更新时，将会触发更新触发器。</span><span class="sxs-lookup"><span data-stu-id="13111-103">Merge replication uses triggers as part of the replication process; when an update is made to published table, an update trigger fires.</span></span> <span data-ttu-id="13111-104">在某些情况下，无需触发触发器便可以更新数据，比如在 WRITETEXT 和 UPDATETEXT 操作期间。</span><span class="sxs-lookup"><span data-stu-id="13111-104">In some cases, data can be updated without the trigger firing, such as during the WRITETEXT and UPDATETEXT operations.</span></span> <span data-ttu-id="13111-105">在这些情况下，您需要显式添加虚 UPDATE 语句来复制更改。</span><span class="sxs-lookup"><span data-stu-id="13111-105">In these cases, you need to add a dummy UPDATE statement explicitly to replicate the change.</span></span> <span data-ttu-id="13111-106">可以使用复制存储过程添加虚 UPDATE 语句。</span><span class="sxs-lookup"><span data-stu-id="13111-106">You can add a dummy UPDATE statement using replication stored procedures.</span></span>  
  
### <a name="to-add-a-dummy-update-statement"></a><span data-ttu-id="13111-107">添加虚 UPDATE 语句</span><span class="sxs-lookup"><span data-stu-id="13111-107">To add a dummy UPDATE statement</span></span>  
  
1.  <span data-ttu-id="13111-108">请对需要虚更新的合并发布表中的行执行操作（例如，UPDATETEXT）。</span><span class="sxs-lookup"><span data-stu-id="13111-108">Execute the operation (for example, UPDATETEXT) on a row in a merge published table  that requires a dummy update.</span></span>  
  
2.  <span data-ttu-id="13111-109">在服务器（发布服务器或订阅服务器）的进行了更改的数据库中，执行 [sp_mergedummyupdate (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="13111-109">At the server (Publisher or Subscriber) on the database where the change was made, execute [sp_mergedummyupdate &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql).</span></span> <span data-ttu-id="13111-110">指定对其进行更改的表 **@source_object** ，并指定的已更改行的唯一标识符 **@rowguid** 。</span><span class="sxs-lookup"><span data-stu-id="13111-110">Specify the table on which the change was made for **@source_object**, and the unique identifier of the changed row for **@rowguid**.</span></span>  
  
3.  <span data-ttu-id="13111-111">同步此订阅以复制更改行。</span><span class="sxs-lookup"><span data-stu-id="13111-111">Synchronize the subscription to replicate the changed row.</span></span>  
  
  
