---
title: 将数据大容量加载到合并发布中的表 (复制 Transact-sql 编程) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- bulk load [SQL Server replication]
- merge replication bulk loading [SQL Server replication]
- sp_addtabletocontents
ms.assetid: 16e6498a-b449-4051-aec4-ea814a2ad993
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f669a1f7132aa0f588fd89fb9747a7dc9017fcf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693766"
---
# <a name="bulk-load-data-into-tables-in-a-merge-publication-replication-transact-sql-programming"></a><span data-ttu-id="13b87-102">将数据大容量加载到合并发布中的表（复制 Transact-SQL 编程）</span><span class="sxs-lookup"><span data-stu-id="13b87-102">Bulk-Load Data into Tables in a Merge Publication (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="13b87-103">使用 [bcp Utility](../../tools/bcp-utility.md) 或 [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) 命令将数据加载到表时，默认情况下，不会触发在 [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql) 系统表中保留跟踪数据的合并复制触发器。</span><span class="sxs-lookup"><span data-stu-id="13b87-103">When data is loaded into tables using the [bcp Utility](../../tools/bcp-utility.md) or the [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) command, by default, the merge replication triggers that maintain tracking data in the [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql) system table are not fired.</span></span> <span data-ttu-id="13b87-104">可以在加载数据时强制触发合并复制触发器，也可以使用复制存储过程，在大容量复制操作之后以编程方式插入生成的复制元数据。</span><span class="sxs-lookup"><span data-stu-id="13b87-104">You can either force the merge replication triggers to fire as the data is loaded, or you can insert the generated replication metadata programmatically after the bulk copy operation using replication stored procedures.</span></span>  
  
### <a name="to-bulk-load-data-into-tables-published-by-merge-replication-using-the-bcp-utility"></a><span data-ttu-id="13b87-105">使用 bcp 实用工具将数据大容量加载到合并复制所发布的表中</span><span class="sxs-lookup"><span data-stu-id="13b87-105">To bulk-load data into tables published by merge replication using the bcp utility</span></span>  
  
1.  <span data-ttu-id="13b87-106">在发布服务器或订阅服务器上，执行 [bcp Utility](../../tools/bcp-utility.md) 或 [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) 以将数据插入到使用合并复制发布的表中。</span><span class="sxs-lookup"><span data-stu-id="13b87-106">At either the Publisher or Subscriber, execute the [bcp Utility](../../tools/bcp-utility.md) or [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) to insert data into a table published using merge replication.</span></span>  
  
2.  <span data-ttu-id="13b87-107">使用以下方法之一来确保为插入的数据生成复制元数据。</span><span class="sxs-lookup"><span data-stu-id="13b87-107">Use one of the following methods to ensure that replication metadata is generated for the inserted data.</span></span>  
  
    -   <span data-ttu-id="13b87-108">使用 FIRE_TRIGGERS 选项执行大容量复制。</span><span class="sxs-lookup"><span data-stu-id="13b87-108">Execute the bulk copy using the FIRE_TRIGGERS option.</span></span>  
  
    -   <span data-ttu-id="13b87-109">对插入数据的数据库执行 [sp_addtabletocontents (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="13b87-109">On the database into which data was inserted, execute [sp_addtabletocontents &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql).</span></span> <span data-ttu-id="13b87-110">指定为其插入数据的表的名称 **@table_name** 。</span><span class="sxs-lookup"><span data-stu-id="13b87-110">Specify the table name into which the data was inserted for **@table_name**.</span></span>  
  
  
