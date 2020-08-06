---
title: 迁移触发器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: ad5385c5-5a50-40ca-a319-97d5606b8511
author: rothja
ms.author: jroth
ms.openlocfilehash: 25965e7cce84b0dcfcd3b6ce6176e8ad3ddabc6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693881"
---
# <a name="migrating-triggers"></a><span data-ttu-id="faa7f-102">迁移触发器</span><span class="sxs-lookup"><span data-stu-id="faa7f-102">Migrating Triggers</span></span>
  <span data-ttu-id="faa7f-103">本主题论述 DDL 和 DML 触发器以及内存优化表。</span><span class="sxs-lookup"><span data-stu-id="faa7f-103">This topic discusses DDL and DML triggers and memory-optimized tables.</span></span>  
  
 <span data-ttu-id="faa7f-104">LOGON 触发器是定义为对 LOGON 事件触发的触发器。</span><span class="sxs-lookup"><span data-stu-id="faa7f-104">LOGON triggers are triggers defined to fire on LOGON events.</span></span> <span data-ttu-id="faa7f-105">LOGON 触发器不会影响内存优化表。</span><span class="sxs-lookup"><span data-stu-id="faa7f-105">LOGON triggers do not affect memory-optimized tables.</span></span>  
  
## <a name="ddl-triggers"></a><span data-ttu-id="faa7f-106">DDL 触发器</span><span class="sxs-lookup"><span data-stu-id="faa7f-106">DDL Triggers</span></span>  
 <span data-ttu-id="faa7f-107">DDL 触发器定义为在对其定义的数据库或服务器上执行 CREATE、ALTER、DROP、GRANT、DENY、REVOKE 或 UPDATE STATISTICS 语句时触发的触发器。</span><span class="sxs-lookup"><span data-stu-id="faa7f-107">DDL triggers are triggers defined to fire when a CREATE, ALTER, DROP, GRANT, DENY, REVOKE, or UPDATE STATISTICS statement is executed on the database or server on which it is defined.</span></span>  
  
 <span data-ttu-id="faa7f-108">如果数据库或服务器具有对 CREATE_TABLE 或者包含它的任何事件组定义的一个或多个 DDL 触发器，则不能创建内存优化表。</span><span class="sxs-lookup"><span data-stu-id="faa7f-108">You cannot create memory-optimized tables if the database or server has one or more DDL trigger defined on CREATE_TABLE or any event group that includes it.</span></span> <span data-ttu-id="faa7f-109">如果数据库或服务器具有对 DROP_TABLE 或者包含它的任何事件组定义的一个或多个 DDL 触发器，则不能删除内存优化表。</span><span class="sxs-lookup"><span data-stu-id="faa7f-109">You cannot drop a memory-optimized table if the database or server has one or more DDL trigger defined on DROP_TABLE or any event group that includes it.</span></span>  
  
 <span data-ttu-id="faa7f-110">如果对 CREATE_PROCEDURE、DROP_PROCEDURE 或包含这些事件的任何事件组有一个或多个 DDL 触发器，则不能创建本机编译的存储过程。</span><span class="sxs-lookup"><span data-stu-id="faa7f-110">You cannot create natively compiled stored procedures if there are one or more DDL triggers on CREATE_PROCEDURE, DROP_PROCEDURE, or any event group that includes those events.</span></span>  
  
## <a name="dml-triggers"></a><span data-ttu-id="faa7f-111">DML 触发器</span><span class="sxs-lookup"><span data-stu-id="faa7f-111">DML Triggers</span></span>  
 <span data-ttu-id="faa7f-112">不能对内存优化表定义 DML 触发器。</span><span class="sxs-lookup"><span data-stu-id="faa7f-112">DML triggers cannot be defined on memory-optimized tables.</span></span> <span data-ttu-id="faa7f-113">但是，如果您显式使用存储过程插入、更新或删除数据，则内存中 OLTP 允许您实现与 DML 触发器类似的效果。</span><span class="sxs-lookup"><span data-stu-id="faa7f-113">However, In-Memory OLTP allows you to achieve an effect similar to DML triggers if you explicitly use stored procedures to insert, update, or delete data.</span></span> <span data-ttu-id="faa7f-114">如果您的系统包含即席查询，则将它们转换为改用这些存储过程，以便模拟 DML 触发器的效果。</span><span class="sxs-lookup"><span data-stu-id="faa7f-114">If your system contains ad-hoc queries, convert them to use these stored procedures instead to simulate the effect of DML triggers.</span></span>  
  
 <span data-ttu-id="faa7f-115">根据触发器事件（FOR/AFTER 或 INSTEAD OF），您可以在对该表执行 INSERT、UPDATE 或 DELETE 的相应存储过程中包含触发器的内容。</span><span class="sxs-lookup"><span data-stu-id="faa7f-115">Depending on the trigger event (FOR/AFTER or INSTEAD OF), you may include the content of the trigger in the appropriate stored procedure that performs INSERT, UPDATE, or DELETE on that table.</span></span> <span data-ttu-id="faa7f-116">例如，在迁移某一 AFTER INSERT 触发器时，您可以通过在相应 INSERT 语句后包含该触发器的内容，更改执行插入操作的存储过程。</span><span class="sxs-lookup"><span data-stu-id="faa7f-116">For example, when migrating an AFTER INSERT trigger, you could alter the stored procedure that performs the insert operation by including the content of the trigger after the appropriate INSERT statement.</span></span>  
  
 <span data-ttu-id="faa7f-117">您可以使用解释型存储过程或本机编译的存储过程。</span><span class="sxs-lookup"><span data-stu-id="faa7f-117">You can use an interpreted stored procedure or a natively compiled stored procedure.</span></span> <span data-ttu-id="faa7f-118">解释型存储过程中的大多数 [!INCLUDE[tsql](../../includes/tsql-md.md)] 构造函数可对内存优化表执行。</span><span class="sxs-lookup"><span data-stu-id="faa7f-118">Most [!INCLUDE[tsql](../../includes/tsql-md.md)] constructs in an interpreted stored procedure can execute on a memory-optimized table.</span></span> <span data-ttu-id="faa7f-119">但是，在本机编译的存储过程中只支持一部分的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 构造函数。</span><span class="sxs-lookup"><span data-stu-id="faa7f-119">However, only a subset of [!INCLUDE[tsql](../../includes/tsql-md.md)] constructs are supported in natively compiled stored procedures.</span></span> <span data-ttu-id="faa7f-120">有关 [!INCLUDE[tsql](../../includes/tsql-md.md)] 内存优化表支持的信息，请参阅[使用解释型 Transact-sql 访问内存优化表](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="faa7f-120">For information on [!INCLUDE[tsql](../../includes/tsql-md.md)] support on memory-optimized tables, see [Accessing Memory-Optimized Tables Using Interpreted Transact-SQL](accessing-memory-optimized-tables-using-interpreted-transact-sql.md).</span></span> <span data-ttu-id="faa7f-121">有关 [!INCLUDE[tsql](../../includes/tsql-md.md)] 本机编译存储过程中支持的信息，请参阅[内存中 OLTP 不支持的 transact-sql 构造](transact-sql-constructs-not-supported-by-in-memory-oltp.md)。</span><span class="sxs-lookup"><span data-stu-id="faa7f-121">For information on [!INCLUDE[tsql](../../includes/tsql-md.md)] support in natively compiled stored procedures, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md).</span></span>  
  
 <span data-ttu-id="faa7f-122">下面是在内存优化表上模拟 DML 触发器行为的一个简单示例。</span><span class="sxs-lookup"><span data-stu-id="faa7f-122">The following is a simple example of simulating DML trigger behavior on a memory-optimized table.</span></span>  
  
 <span data-ttu-id="faa7f-123">该数据库包含以下对象，编写为 CREATE TABLE、CREATE TRIGGER 和 CREATE PROCEDURE 语句的脚本：</span><span class="sxs-lookup"><span data-stu-id="faa7f-123">The database contains the following objects, scripted as CREATE TABLE, CREATE TRIGGER, and CREATE PROCEDURE statements:</span></span>  
  
```sql  
CREATE TABLE OrderDetails  
(  
   OrderId int not null primary key,  
   ProductId int not null,  
   SalePrice money not null,  
   Quantity int not null,  
   Total money not null,  
   IsDeleted bit not null DEFAULT (0)  
)  
GO  
  
CREATE TRIGGER tr_order_details_insteadof_insert  
ON OrderDetails  
INSTEAD OF INSERT AS  
BEGIN  
   DECLARE @pid int, @qty_buy int, @qty_remain int  
   SELECT @pid = ProductId, @qty_buy = Quantity FROM inserted  
   SELECT @qty_remain = Quantity FROM Inventory WHERE ProductId = @pid  
   IF (@qty_remain <= @qty_buy)  
      THROW 51000, N'Insufficient inventory!', 1  
   ELSE  
   BEGIN  
      INSERT INTO dbo.OrderDetails (OrderId, ProductId, SalePrice, Quantity, Total)   
      SELECT OrderId, ProductId, SalePrice, Quantity, Total FROM inserted  
      UPDATE Inventory SET Quantity = Quantity - @qty_buy WHERE ProductId = @pid  
   END  
END  
GO  
  
CREATE TRIGGER tr_order_details_after_update  
ON OrderDetails  
AFTER UPDATE AS  
BEGIN  
   INSERT INTO UpdateNotifications (OrderId, UpdateTime) SELECT OrderId, GETDATE() FROM inserted     
END  
GO  
  
CREATE PROCEDURE sp_insert_order_details   
   @OrderId int, @ProductId int, @SalePrice money, @Quantity int, @total money  
AS BEGIN  
   INSERT INTO dbo.OrderDetails (OrderId, ProductId, SalePrice, Quantity, Total)  
   VALUES (@OrderId, @ProductId, @SalePrice, @Quantity, @total)  
END  
GO  
  
CREATE PROCEDURE sp_update_order_details_by_id  
   @OrderId int, @ProductId int, @SalePrice money, @Quantity int, @Total money  
AS BEGIN  
   UPDATE dbo.OrderDetails   
   SET ProductId = @ProductId, SalePrice = @SalePrice, Quantity = @Quantity, Total = @total  
   WHERE OrderId = @OrderId  
END  
GO  
```  
  
 <span data-ttu-id="faa7f-124">以下对象在功能上等效于预迁移状态：</span><span class="sxs-lookup"><span data-stu-id="faa7f-124">The following objects are functionally equivalent to the pre-migration state:</span></span>  
  
```sql  
CREATE TABLE OrderDetails  
(  
   OrderId int not null PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT = 1048576),  
   ProductId int not null,  
   SalePrice money not null,  
   Quantity int not null,  
   Total money not null,  
   IsDeleted bit not null DEFAULT (0)  
) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
GO  
  
CREATE TABLE Inventory  
(  
   ProductId int not null PRIMARY KEY NONCLUSTERED,  
   Quantity int not null  
) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
GO  
  
CREATE TABLE UpdateNotifications  
(  
   OrderId int not null,  
   UpdateTime datetime2 not null  
   CONSTRAINT pk_updateNotifications PRIMARY KEY NONCLUSTERED (OrderId, UpdateTime)  
) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
GO  
  
CREATE PROCEDURE sp_insert_order_details   
   @OrderId int, @ProductId int, @SalePrice money, @Quantity int, @total money  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'English')  
   DECLARE @qty_remain int  
   SELECT @qty_remain = Quantity FROM dbo.Inventory WHERE ProductId = @ProductId  
   IF (@qty_remain <= @Quantity)  
      THROW 51000, N'Insufficient inventory!', 1  
   ELSE  
   BEGIN  
      INSERT INTO dbo.OrderDetails (OrderId, ProductId, SalePrice, Quantity, Total)   
      VALUES (@OrderId, @ProductId, @SalePrice, @Quantity, @total)  
      UPDATE dbo.Inventory SET Quantity = Quantity - @Quantity WHERE ProductId = @ProductId  
   END  
END  
GO  
  
CREATE PROCEDURE sp_update_order_details_by_id  
   @OrderId int, @ProductId int, @SalePrice money, @Quantity int, @Total money  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'English')  
   UPDATE dbo.OrderDetails   
   SET ProductId = @ProductId, SalePrice = @SalePrice, Quantity = @Quantity, Total = @total  
   WHERE OrderId = @OrderId  
   INSERT INTO dbo.UpdateNotifications (OrderId, UpdateTime) VALUES (@OrderId, GETDATE())  
END  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="faa7f-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="faa7f-125">See Also</span></span>  
 [<span data-ttu-id="faa7f-126">迁移到内存中 OLTP</span><span class="sxs-lookup"><span data-stu-id="faa7f-126">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
