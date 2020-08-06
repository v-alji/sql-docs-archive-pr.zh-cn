---
title: 迁移计算列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 64a9eade-22c3-4a9d-ab50-956219e08df1
author: rothja
ms.author: jroth
ms.openlocfilehash: feb50ef64f42d95913ad4e13f9a79e6e0e4ecad3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693886"
---
# <a name="migrating-computed-columns"></a><span data-ttu-id="ee248-102">迁移计算列</span><span class="sxs-lookup"><span data-stu-id="ee248-102">Migrating Computed Columns</span></span>
  <span data-ttu-id="ee248-103">内存优化的表中不支持计算列。</span><span class="sxs-lookup"><span data-stu-id="ee248-103">Computed columns are not supported in memory-optimized tables.</span></span> <span data-ttu-id="ee248-104">但是，可模拟计算列。</span><span class="sxs-lookup"><span data-stu-id="ee248-104">However, you can simulate a computed column.</span></span>  
  
 <span data-ttu-id="ee248-105">将基于磁盘的表迁移到内存优化的表时，应考虑是否需要使计算列持久化。</span><span class="sxs-lookup"><span data-stu-id="ee248-105">You should consider the need to persist your computed columns when you migrate your disk-based tables to memory-optimized tables.</span></span> <span data-ttu-id="ee248-106">内存优化的表和本机编译的存储过程的性能特征不同，因此可能不需要持久化。</span><span class="sxs-lookup"><span data-stu-id="ee248-106">The different performance characteristics of memory-optimized tables and natively compiled stored procedures may negate the need for persistence.</span></span>  
  
## <a name="non-persisted-computed-columns"></a><span data-ttu-id="ee248-107">非持久化计算列</span><span class="sxs-lookup"><span data-stu-id="ee248-107">Non-Persisted Computed Columns</span></span>  
 <span data-ttu-id="ee248-108">若要模拟非持久化计算列的效果，请在内存优化的表上创建一个视图。</span><span class="sxs-lookup"><span data-stu-id="ee248-108">To simulate the effects of a non-persisted computed column, create a view on the memory-optimized table.</span></span> <span data-ttu-id="ee248-109">在定义该视图的 SELECT 语句中，将计算列定义添加到该视图中。</span><span class="sxs-lookup"><span data-stu-id="ee248-109">In the SELECT statement that defines the view, add the computed column definition into the view.</span></span> <span data-ttu-id="ee248-110">除了在本机编译的存储过程中以外，使用计算列中的值的查询应从该视图进行读取。</span><span class="sxs-lookup"><span data-stu-id="ee248-110">Except in a natively compiled stored procedure, queries that use values from the computed column should read from the view.</span></span> <span data-ttu-id="ee248-111">在本机编译的存储过程中，应根据计算列定义更新任何 select、update 或 delete 语句。</span><span class="sxs-lookup"><span data-stu-id="ee248-111">Inside natively compiled stored procedures, you should update any select, update, or delete statement according to your computed column definition.</span></span>  
  
```sql  
-- Schema for the table dbo.OrderDetails:  
-- OrderId int not null primary key,  
-- ProductId int not null,  
-- SalePrice money not null,  
-- Quantity int not null,  
-- Total money not null  
--  
-- Total is computed as SalePrice * Quantity and is not persisted.  
CREATE VIEW dbo.v_order_details AS  
   SELECT  
      OrderId,  
      ProductId,  
      SalePrice,  
      Quantity,  
      Quantity * SalePrice AS Total  
   FROM dbo.order_details  
```  
  
## <a name="persisted-computed-columns"></a><span data-ttu-id="ee248-112">持久化计算列</span><span class="sxs-lookup"><span data-stu-id="ee248-112">Persisted Computed Columns</span></span>  
 <span data-ttu-id="ee248-113">若要模拟持久化计算列的效果，请创建一个存储过程用于插入到表中，创建另一个存储过程用于更新表。</span><span class="sxs-lookup"><span data-stu-id="ee248-113">To simulate the effects of a persisted computed column, create a stored procedure for inserting into the table and another stored procedure for updating the table.</span></span> <span data-ttu-id="ee248-114">插入或更新表时，调用这些存储过程以执行这些任务。</span><span class="sxs-lookup"><span data-stu-id="ee248-114">When inserting or updating the table, invoke these stored procedures to perform these tasks.</span></span> <span data-ttu-id="ee248-115">在存储过程中，根据输入内容算出计算字段的值，方式很像在基于磁盘的原始表上定义计算列。</span><span class="sxs-lookup"><span data-stu-id="ee248-115">Inside the stored procedures, calculate the value for the computed field according to the inputs, much like how the computed column is defined on the original disk-based table.</span></span> <span data-ttu-id="ee248-116">然后，在存储过程中按需插入或更新表。</span><span class="sxs-lookup"><span data-stu-id="ee248-116">Then, insert or update the table as needed inside the stored procedure.</span></span>  
  
```sql  
-- Schema for the table dbo.OrderDetails:  
-- OrderId int not null primary key,  
-- ProductId int not null,  
-- SalePrice money not null,  
-- Quantity int not null,  
-- Total money not null  
--  
-- Total is computed as SalePrice * Quantity and is persisted.  
-- we need to create insert and update procedures to calculate Total.  
CREATE PROCEDURE sp_insert_order_details   
@OrderId int, @ProductId int, @SalePrice money, @Quantity int  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (LANGUAGE = N'english', TRANSACTION ISOLATION LEVEL = SNAPSHOT)  
-- compute the value here.   
-- this stored procedure works with single rows only.  
-- for bulk inserts, accept a table-valued parameter into the stored procedure  
-- and use an INSERT INTO SELECT statement.  
DECLARE @total money = @SalePrice * @Quantity  
INSERT INTO dbo.OrderDetails (OrderId, ProductId, SalePrice, Quantity, Total)  
VALUES (@OrderId, @ProductId, @SalePrice, @Quantity, @total)  
END  
GO  
  
CREATE PROCEDURE sp_update_order_details_by_id  
@OrderId int, @ProductId int, @SalePrice money, @Quantity int  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (LANGUAGE = N'english', TRANSACTION ISOLATION LEVEL = SNAPSHOT)  
-- compute the value here.   
-- this stored procedure works with single rows only.  
DECLARE @total money = @SalePrice * @Quantity  
UPDATE dbo.OrderDetails   
SET ProductId = @ProductId, SalePrice = @SalePrice, Quantity = @Quantity, Total = @total  
WHERE OrderId = @OrderId  
END  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee248-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ee248-117">See Also</span></span>  
 [<span data-ttu-id="ee248-118">迁移到内存中 OLTP</span><span class="sxs-lookup"><span data-stu-id="ee248-118">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
