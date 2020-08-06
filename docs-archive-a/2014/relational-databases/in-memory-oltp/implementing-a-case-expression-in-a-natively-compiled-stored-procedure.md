---
title: 实现 CASE 语句 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 2f82db01-da7e-4a7d-8bc0-48b245e6f768
author: rothja
ms.author: jroth
ms.openlocfilehash: 27059cc09d5507bf2548b23b60f3c2f485c3fe36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692408"
---
# <a name="implementing-a-case-statement"></a><span data-ttu-id="04edf-102">实现 CASE 语句</span><span class="sxs-lookup"><span data-stu-id="04edf-102">Implementing a CASE Statement</span></span>
  <span data-ttu-id="04edf-103">本机编译的存储过程中不支持 case 语句。</span><span class="sxs-lookup"><span data-stu-id="04edf-103">Case statements are not supported in natively compiled stored procedures.</span></span> <span data-ttu-id="04edf-104">以下示例演示一种在本机编译的存储过程中实现 case 语句功能的方法。</span><span class="sxs-lookup"><span data-stu-id="04edf-104">The following sample shows a way to implement the functionality of a case statement in a natively compiled stored procedure.</span></span>  
  
 <span data-ttu-id="04edf-105">该示例使用表变量构造单个结果集，该结果集仅当处理有限数量的行时才适用，因为它涉及创建数据行的额外副本。</span><span class="sxs-lookup"><span data-stu-id="04edf-105">The samples uses a table variable to construct a single result set, which is only suitable when processing a limited number of rows, as it involves creating an additional copy of the data rows.</span></span>  
  
 <span data-ttu-id="04edf-106">应测试此解决方法的性能，以确保它在应用程序中按预期方式执行。</span><span class="sxs-lookup"><span data-stu-id="04edf-106">You should test the performance of this workaround, to be sure that it performs as expected in your application.</span></span>  
  
```  
-- original query  
SELECT   
   SalesOrderID,   
   CASE (OnlineOrderFlag)   
   WHEN 1 THEN N'Order placed online by customer'  
   ELSE N'Order placed by sales person'  
   END  
FROM Sales.SalesOrderHeader_inmem  
  
--  workaround for CASE in natively compiled stored procedures  
--  use a table for the single resultset  
CREATE TYPE dbo.SOHOnlineOrderResult AS TABLE  
(  
   SalesOrderID uniqueidentifier not null index ix_SalesOrderID,  
     OrderFlag nvarchar(100) not null  
) with (memory_optimized=on)  
go  
  
-- natively compiled stored procedure that includes the query  
CREATE PROCEDURE dbo.usp_SOHOnlineOrderResult  
   WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
   AS BEGIN ATOMIC WITH  
      (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE=N'us_english')  
  
   -- table variable for creating the single resultset  
   DECLARE @result dbo.SOHOnlineOrderResult  
  
   -- CASE OnlineOrderFlag=1  
   INSERT @result   
   SELECT SalesOrderID, N'Order placed online by customer'  
      FROM Sales.SalesOrderHeader_inmem  
      WHERE OnlineOrderFlag=1  
  
   -- ELSE  
   INSERT @result   
   SELECT SalesOrderID, placed by sales person'  
      FROM Sales.SalesOrderHeader_inmem  
      WHERE OnlineOrderFlag!=1  
  
   -- return single resultset  
   SELECT SalesOrderID, OrderFlag FROM @result  
END  
GO  
  
EXEC dbo.usp_SOHOnlineOrderResult  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="04edf-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="04edf-107">See Also</span></span>  
 <span data-ttu-id="04edf-108">[本机编译的存储过程的迁移问题](migration-issues-for-natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="04edf-108">[Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md) </span></span>  
 [<span data-ttu-id="04edf-109">内存中 OLTP 不支持的 Transact-SQL 构造</span><span class="sxs-lookup"><span data-stu-id="04edf-109">Transact-SQL Constructs Not Supported by In-Memory OLTP</span></span>](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
