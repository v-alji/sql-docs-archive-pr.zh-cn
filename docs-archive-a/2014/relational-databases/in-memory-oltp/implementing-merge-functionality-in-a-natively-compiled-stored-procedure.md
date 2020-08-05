---
title: 实现合并功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: d4bcdc36-3302-4abc-9b35-64ec2b920986
author: rothja
ms.author: jroth
ms.openlocfilehash: 8c2e2d3f0796396c0f3f451215f1fd685979a842
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580753"
---
# <a name="implementing-merge-functionality"></a><span data-ttu-id="77eeb-102">实现 MERGE 功能</span><span class="sxs-lookup"><span data-stu-id="77eeb-102">Implementing MERGE Functionality</span></span>
  <span data-ttu-id="77eeb-103">数据库可能需要执行插入或更新，具体取决于数据库中是否已存在特定行。</span><span class="sxs-lookup"><span data-stu-id="77eeb-103">A database may need to perform either an insert of an update, depending on whether a particular row already exists in the database.</span></span>  
  
 <span data-ttu-id="77eeb-104">如果不使用 `MERGE` 语句，以下是您可以在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中使用的一种方法：</span><span class="sxs-lookup"><span data-stu-id="77eeb-104">Without using the `MERGE` statement, the following is one approach you can use in [!INCLUDE[tsql](../../includes/tsql-md.md)]:</span></span>  
  
```sql  
UPDATE mytable SET col=@somevalue WHERE myPK = @parm  
IF @@ROWCOUNT = 0  
    INSERT mytable (columns) VALUES (@parm, @other values)  
```  
  
 <span data-ttu-id="77eeb-105">实现合并的另一 [!INCLUDE[tsql](../../includes/tsql-md.md)] 方法：</span><span class="sxs-lookup"><span data-stu-id="77eeb-105">Another [!INCLUDE[tsql](../../includes/tsql-md.md)] method to implement a merge:</span></span>  
  
```sql  
IF EXISTS (SELECT 1 FROM mytable WHERE myPK = @parm)  
    UPDATE....  
ELSE  
    INSERT  
```  
  
 <span data-ttu-id="77eeb-106">对于本机编译的存储过程</span><span class="sxs-lookup"><span data-stu-id="77eeb-106">For a natively compiled stored procedure</span></span>  
  
```sql  
DECLARE @i  int  = 0  -- or whatever your PK data type is  
UPDATE mytable SET @i=myPK, othercolums = other values WHERE myPK = @parm  
IF @i = 0  
   INSERT....  
```  
  
## <a name="see-also"></a><span data-ttu-id="77eeb-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="77eeb-107">See Also</span></span>  
 <span data-ttu-id="77eeb-108">[本机编译的存储过程的迁移问题](migration-issues-for-natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="77eeb-108">[Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md) </span></span>  
 [<span data-ttu-id="77eeb-109">内存中 OLTP 不支持的 Transact-SQL 构造</span><span class="sxs-lookup"><span data-stu-id="77eeb-109">Transact-SQL Constructs Not Supported by In-Memory OLTP</span></span>](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
