---
title: 在内存优化表中实现 IDENTITY | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0a704a3-3a31-4c2c-b967-addacda62ef8
author: rothja
ms.author: jroth
ms.openlocfilehash: 955f9f1a905a9d0c71304320f60abe300e430e4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580754"
---
# <a name="implementing-identity-in-a-memory-optimized-table"></a><span data-ttu-id="3bf4e-102">在内存优化的表中实现 IDENTITY</span><span class="sxs-lookup"><span data-stu-id="3bf4e-102">Implementing IDENTITY in a Memory-Optimized Table</span></span>
  <span data-ttu-id="3bf4e-103">内存优化表支持 IDENTITY(1, 1)。</span><span class="sxs-lookup"><span data-stu-id="3bf4e-103">IDENTITY(1, 1) is supported on a memory-optimized table.</span></span> <span data-ttu-id="3bf4e-104">但是，内存优化表不支持使用 IDENTITY(x, y)（其中 x != 1 或 y != 1 ）定义的标识列。</span><span class="sxs-lookup"><span data-stu-id="3bf4e-104">However, identity columns with definition of IDENTITY(x, y) where x != 1 or y != 1 are not supported on memory-optimized tables.</span></span> <span data-ttu-id="3bf4e-105">标识值的解决方法使用序列对象 ([序列号](../sequence-numbers/sequence-numbers.md)) 。</span><span class="sxs-lookup"><span data-stu-id="3bf4e-105">The workaround for IDENTITY values uses the SEQUENCE object ([Sequence Numbers](../sequence-numbers/sequence-numbers.md)).</span></span>  
  
 <span data-ttu-id="3bf4e-106">从要转换到内存中 OLTP 的表首先删除 IDENTITY 属性。</span><span class="sxs-lookup"><span data-stu-id="3bf4e-106">First remove the IDENTITY property from the table you are converting to In-Memory OLTP.</span></span> <span data-ttu-id="3bf4e-107">然后，为表中的列定义新的 SEQUENCE 对象。</span><span class="sxs-lookup"><span data-stu-id="3bf4e-107">Then, define a new SEQUENCE object for the column in the table.</span></span> <span data-ttu-id="3bf4e-108">作为标识列的 SEQUENCE 对象依赖为列创建 DEFAULT 值的能力，这些列使用 NEXT VALUE FOR 语法获取新的标识值。</span><span class="sxs-lookup"><span data-stu-id="3bf4e-108">SEQUENCE objects as identity columns rely on the ability to create DEFAULT values for columns that use the NEXT VALUE FOR syntax to get a new identity value.</span></span> <span data-ttu-id="3bf4e-109">因为在内存中 OLTP 中不支持 DEFAULT，您需要将新生成的 SEQUENCE 值传给 INSERT 语句或执行插入的本机编译存储过程。</span><span class="sxs-lookup"><span data-stu-id="3bf4e-109">Since DEFAULTs are not supported in In-Memory OLTP, you need to pass the newly-generated SEQUENCE value either to the INSERT statement or to a natively compiled stored procedure that does the insert.</span></span> <span data-ttu-id="3bf4e-110">下面的示例对此模式进行了演示。</span><span class="sxs-lookup"><span data-stu-id="3bf4e-110">The following example demonstrates this pattern.</span></span>  
  
```sql  
-- Create a new In-Memory OLTP table to simulate IDENTITY insert  
-- Here the column C1 was the identity column in the original table  
--  
create table T1  
(  
  
[c1] integer not null primary key T1_c1 nonclustered,  
[c2] varchar(32) not null,  
[c3] datetime not null  
  
) with (memory_optimized = on)  
go  
  
-- This is a sequence provider that will give us values for column [c1]  
--  
create sequence usq_SequenceForT1 as integer start with 2 increment by 1  
go  
  
--   insert a sample row using the sequence  
--   note that a new value needs to be retrieved form   
--   the sequence object for every insert  
--  
declare @c1 integer = next value for [dbo].[usq_SequenceForT1]  
insert into T1 values (@c1, 'test', getdate())  
```  
  
 <span data-ttu-id="3bf4e-111">在执行几次插入后，您看到在列 [c1] 中单调增加的有效值。</span><span class="sxs-lookup"><span data-stu-id="3bf4e-111">After performing the insert several times, you see valid monotonically increasing values in column [c1].</span></span> <span data-ttu-id="3bf4e-112">此结果集是使用不带 `ORDER BY` 的表扫描和哈希索引生成的，因此行未排序。</span><span class="sxs-lookup"><span data-stu-id="3bf4e-112">This result set is generated using table scan and hash index without `ORDER BY` so the rows are not ordered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bf4e-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3bf4e-113">See Also</span></span>  
 [<span data-ttu-id="3bf4e-114">迁移到内存中 OLTP</span><span class="sxs-lookup"><span data-stu-id="3bf4e-114">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
