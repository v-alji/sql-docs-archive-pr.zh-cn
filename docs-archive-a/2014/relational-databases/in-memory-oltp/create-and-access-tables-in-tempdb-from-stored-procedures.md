---
title: 从本机编译的存储过程创建和访问 TempDB 中的表 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 12be8011-b76c-45c1-8f55-7f46e0e374e9
author: rothja
ms.author: jroth
ms.openlocfilehash: a0bd2b4863cc3c257cd260bf381ebb3b890af219
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693341"
---
# <a name="creating-and-accessing-tables-in-tempdb-from-natively-compiled-stored-procedures"></a><span data-ttu-id="30983-102">通过本机编译的存储过程创建和访问 TempDB 中的表</span><span class="sxs-lookup"><span data-stu-id="30983-102">Creating and Accessing Tables in TempDB from Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="30983-103">不支持通过本机编译的存储过程创建和访问 TempDB 中的表。</span><span class="sxs-lookup"><span data-stu-id="30983-103">Creating and accessing tables in TempDB from natively compiled stored procedures is not supported.</span></span> <span data-ttu-id="30983-104">请改用表类型和表变量。</span><span class="sxs-lookup"><span data-stu-id="30983-104">Instead, use table types and table variables.</span></span> <span data-ttu-id="30983-105">例如：</span><span class="sxs-lookup"><span data-stu-id="30983-105">For example:</span></span>  
  
```sql  
CREATE TYPE dbo.OrderQuantityByProduct   
  AS TABLE   
   (id INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=100000),   
    ProductID INT NOT NULL,   
    Quantity INT NOT NULL) WITH (MEMORY_OPTIMIZED=ON)  
GO  
CREATE PROCEDURE dbo.usp_OrderQuantityByProduct   
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  
    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
    LANGUAGE = 'english'  
)  
  -- declare table variables for the list of orders   
  DECLARE @Input dbo.OrderQuantityByProduct  
  
  -- populate input  
  INSERT @Input SELECT ProductID, Quantity FROM dbo.[Order Details]  
  end  
```  
  
## <a name="see-also"></a><span data-ttu-id="30983-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30983-106">See Also</span></span>  
 <span data-ttu-id="30983-107">[本机编译的存储过程的迁移问题](migration-issues-for-natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="30983-107">[Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md) </span></span>  
 [<span data-ttu-id="30983-108">内存中 OLTP 不支持的 Transact-SQL 构造</span><span class="sxs-lookup"><span data-stu-id="30983-108">Transact-SQL Constructs Not Supported by In-Memory OLTP</span></span>](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
