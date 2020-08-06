---
title: 跨数据库查询 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a0305f5b-91bd-4d18-a2fc-ec235b062fd3
author: rothja
ms.author: jroth
ms.openlocfilehash: 4afbb580a55273ec241005493fd37f99e98ec0e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579581"
---
# <a name="cross-database-queries"></a><span data-ttu-id="f0c5c-102">跨数据库查询</span><span class="sxs-lookup"><span data-stu-id="f0c5c-102">Cross-Database Queries</span></span>
  <span data-ttu-id="f0c5c-103">在 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 中，内存优化表不支持跨数据库事务。</span><span class="sxs-lookup"><span data-stu-id="f0c5c-103">In [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], memory-optimized tables do not support cross-database transactions.</span></span> <span data-ttu-id="f0c5c-104">不能从也访问某一内存优化表的相同事务或相同查询访问其他数据库。</span><span class="sxs-lookup"><span data-stu-id="f0c5c-104">You cannot access another database from the same transaction or the same query that also accesses a memory-optimized table.</span></span> <span data-ttu-id="f0c5c-105">可以轻松地将来自一个数据库的某个表中的数据复制到其他数据库的内存优化表中。</span><span class="sxs-lookup"><span data-stu-id="f0c5c-105">You cannot easily copy data from a table in one database, to a memory-optimized table in another database.</span></span>  
  
 <span data-ttu-id="f0c5c-106">表变量不是事务性的。</span><span class="sxs-lookup"><span data-stu-id="f0c5c-106">Table variables are not transactional.</span></span> <span data-ttu-id="f0c5c-107">因此，内存优化表变量可用于跨数据库查询中，并因此可以简化将数据从一个数据库中移到另一个数据库的内存优化表中的操作。</span><span class="sxs-lookup"><span data-stu-id="f0c5c-107">Therefore, memory-optimized table variables can be used in cross-database queries, and can thus facilitate moving data from one database into memory-optimized tables in another.</span></span> <span data-ttu-id="f0c5c-108">可以使用两个事务。</span><span class="sxs-lookup"><span data-stu-id="f0c5c-108">You can use two transactions.</span></span> <span data-ttu-id="f0c5c-109">在第一个事务中，将数据从远程表插入到变量中。</span><span class="sxs-lookup"><span data-stu-id="f0c5c-109">In the first transaction, insert the data from the remote table into the variable.</span></span> <span data-ttu-id="f0c5c-110">在第二个事务中，将数据从变量插入到本地内存优化表中。</span><span class="sxs-lookup"><span data-stu-id="f0c5c-110">In the second transaction, insert the data into the local memory-optimized table from the variable.</span></span>  
  
 <span data-ttu-id="f0c5c-111">例如，若要使用 dbo.tt1 类型的变量，从数据库 db1 中的表 t1 将行复制到 db2 中的表 t2， @v1 你可以使用类似于下面的内容：</span><span class="sxs-lookup"><span data-stu-id="f0c5c-111">For example, to copy the row from table t1 in database db1 to table t2 in db2, using variable @v1 of type dbo.tt1, you can use something like:</span></span>  
  
```sql  
USE db2   
GO   
DECLARE @v1 dbo.tt1   
INSERT @v1 SELECT * FROM db1.dbo.t1   
INSERT dbo.t2 SELECT * FROM @v1   
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="f0c5c-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0c5c-112">See Also</span></span>  
 [<span data-ttu-id="f0c5c-113">迁移到内存中 OLTP</span><span class="sxs-lookup"><span data-stu-id="f0c5c-113">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
