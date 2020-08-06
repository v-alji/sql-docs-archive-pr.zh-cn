---
title: 在本机编译的存储过程中实现 OR 运算符 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f2528e74-2b1c-48cb-861b-c4e57b51ac35
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7ed762e062cbc6831eb46784ef71fc7889850676
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690799"
---
# <a name="implementing-the-or-operator-in-natively-compiled-stored-procedures"></a><span data-ttu-id="0cf54-102">在本机编译存储过程中实现 OR 运算符</span><span class="sxs-lookup"><span data-stu-id="0cf54-102">Implementing the OR Operator in Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="0cf54-103">本机编译存储过程内的查询谓词中不支持 OR 运算符。</span><span class="sxs-lookup"><span data-stu-id="0cf54-103">OR operators are not supported in query predicates in natively compiled stored procedures.</span></span> <span data-ttu-id="0cf54-104">本机编译存储过程中的查询谓词也不支持 NOT 运算符，因而无法通过单独使用等同的逻辑运算符来模拟 OR 运算符的效果。</span><span class="sxs-lookup"><span data-stu-id="0cf54-104">Because NOT operators are also not supported in query predicates in natively compiled stored procedures, the effects of OR operators cannot be simulated through the use of equivalent logical operators alone.</span></span> <span data-ttu-id="0cf54-105">但是，借助内存优化表变量，也许能够模拟 OR 运算符的效果。</span><span class="sxs-lookup"><span data-stu-id="0cf54-105">However, the effects of an OR operator may be simulated with memory-optimized table variables.</span></span>  
  
## <a name="or-operator-in-where-clause"></a><span data-ttu-id="0cf54-106">WHERE 子句中的 OR 运算符</span><span class="sxs-lookup"><span data-stu-id="0cf54-106">OR Operator in WHERE Clause</span></span>  
 <span data-ttu-id="0cf54-107">如果 WHERE 子句中包含 OR 运算符，则可用以下方法模拟其行为：</span><span class="sxs-lookup"><span data-stu-id="0cf54-107">If you have an OR operator in a WHERE clause, you can use the following approach to simulate its behavior:</span></span>  
  
1.  <span data-ttu-id="0cf54-108">创建具有相应架构的内存优化表变量。</span><span class="sxs-lookup"><span data-stu-id="0cf54-108">Create a memory-optimized table variable with the appropriate schema.</span></span> <span data-ttu-id="0cf54-109">这需要预定义的内存优化表类型。</span><span class="sxs-lookup"><span data-stu-id="0cf54-109">This requires a predefined memory-optimized table type.</span></span>  
  
2.  <span data-ttu-id="0cf54-110">从顶级 OR 运算符开始，根据 OR 运算符联接的谓词将 WHERE 子句分为两个部分。</span><span class="sxs-lookup"><span data-stu-id="0cf54-110">Starting with the top level OR operator, separate the WHERE clause into two parts according to the predicates joined by the OR operator.</span></span> <span data-ttu-id="0cf54-111">如果 WHERE 子句中包含多个 OR 运算符，则可能需要多次执行此操作。</span><span class="sxs-lookup"><span data-stu-id="0cf54-111">If you have more than one OR operator in a WHERE clause, you may need to do this more than once.</span></span> <span data-ttu-id="0cf54-112">重复此步骤，直至表达式不含 OR 运算符为止。</span><span class="sxs-lookup"><span data-stu-id="0cf54-112">Repeat this step until no OR operators remain.</span></span> <span data-ttu-id="0cf54-113">例如，如果您有以下谓词：</span><span class="sxs-lookup"><span data-stu-id="0cf54-113">For example, if you have the following predicate:</span></span>  
  
    ```  
    pred1 OR (pred2 AND (pred3 OR pred4)) OR (pred5 AND pred6)  
    ```  
  
     <span data-ttu-id="0cf54-114">执行完此步骤，谓词应如下所示：</span><span class="sxs-lookup"><span data-stu-id="0cf54-114">After this step, you should have the following predicates:</span></span>  
  
    ```  
    pred1  
    pred5 AND pred6  
    pred2 AND pred3  
    pred2 AND pred4  
    ```  
  
3.  <span data-ttu-id="0cf54-115">以在步骤 2 中找到的两个部分为谓词执行查询。</span><span class="sxs-lookup"><span data-stu-id="0cf54-115">Execute a query with each of the two parts found in Step 2 as the predicate.</span></span> <span data-ttu-id="0cf54-116">将每个查询的结果插入在步骤 1 中创建的内存优化表变量中。</span><span class="sxs-lookup"><span data-stu-id="0cf54-116">Insert the result for each query into the memory-optimized table variable created in Step 1.</span></span>  
  
4.  <span data-ttu-id="0cf54-117">如有必要，删除内存优化表变量中的重复项。</span><span class="sxs-lookup"><span data-stu-id="0cf54-117">If necessary, remove duplicates from the memory-optimized table variable.</span></span>  
  
5.  <span data-ttu-id="0cf54-118">使用内存优化表变量的内容作为查询的结果。</span><span class="sxs-lookup"><span data-stu-id="0cf54-118">Use the content of the memory-optimized table variable as the result from the query.</span></span>  
  
 <span data-ttu-id="0cf54-119">下面的示例使用来自 AdventureWorks2012 数据库（已针对 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 更新）的表。</span><span class="sxs-lookup"><span data-stu-id="0cf54-119">The following sample uses tables from the AdventureWorks2012 database that were updated for [!INCLUDE[hek_2](../includes/hek-2-md.md)].</span></span> <span data-ttu-id="0cf54-120">若要下载此示例的文件，请转到[AdventureWorks 数据库-2012、2008R2 和 2008](https://msftdbprodsamples.codeplex.com/releases/view/93587)。</span><span class="sxs-lookup"><span data-stu-id="0cf54-120">To download the files for this sample, goto [AdventureWorks Databases - 2012, 2008R2 and 2008](https://msftdbprodsamples.codeplex.com/releases/view/93587).</span></span> <span data-ttu-id="0cf54-121">若要将 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 代码示例应用于 AdventureWorks2012，请参阅[SQL Server 2014 内存中 OLTP 示例](https://msftdbprodsamples.codeplex.com/releases/view/114491)。</span><span class="sxs-lookup"><span data-stu-id="0cf54-121">To apply [!INCLUDE[hek_2](../includes/hek-2-md.md)] code sample to AdventureWorks2012, go to [SQL Server 2014 In-Memory OLTP Sample](https://msftdbprodsamples.codeplex.com/releases/view/114491).</span></span>  
  
 <span data-ttu-id="0cf54-122">将以下存储过程添加至数据库。</span><span class="sxs-lookup"><span data-stu-id="0cf54-122">Add the following stored procedure to the database.</span></span> <span data-ttu-id="0cf54-123">我们将把此存储过程转换为本机编译存储过程。</span><span class="sxs-lookup"><span data-stu-id="0cf54-123">We will convert this stored procedure to use native compilation.</span></span>  
  
```  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesOrderDetail_ondisk  
  @SalesOrderId int = 0, @SalesOrderDetailId int = 0,   
  @CarrierTrackingNumber nvarchar(25) = N'', @ProductId int = 0,   
  @minUnitPrice money = 0, @maxUnitPrice money = 0  
AS BEGIN  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_ondisk s  
  WHERE  s.SalesOrderId = @SalesOrderId  
      OR s.SalesOrderDetailId = @SalesOrderDetailId  
      OR s.CarrierTrackingNumber = @CarrierTrackingNumber  
      OR s.ProductID = @ProductId  
      OR (s.UnitPrice > @minUnitPrice AND s.UnitPrice < @maxUnitPrice)  
END  
GO  
```  
  
 <span data-ttu-id="0cf54-124">转换后，表和存储过程架构如下所示：</span><span class="sxs-lookup"><span data-stu-id="0cf54-124">After conversion, the table and stored procedure schema is as follows,</span></span>  
  
```  
CREATE TYPE Sales.fuzzySearchSalesOrderDetailType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  ModifiedDate datetime2(7) not null  
  INDEX ix_fuzzySearchSalesOrderDetailType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE TYPE Sales.fuzzySearchSalesOrderDetailTempType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  recordcount int not null  
  INDEX ix_fuzzySearchSalesOrderDetailTempType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesOrderDetail_inmem  
  @SalesOrderId int = 0, @SalesOrderDetailId int = 0,   
  @CarrierTrackingNumber nvarchar(25) = N'', @ProductId int = 0,   
  @minUnitPrice money = 0, @maxUnitPrice money = 0  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'ENGLISH')  
  
  DECLARE @retValue Sales.fuzzySearchSalesOrderDetailType  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.SalesOrderId = @SalesOrderId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.SalesOrderDetailId = @SalesOrderDetailId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.CarrierTrackingNumber COLLATE Latin1_General_BIN2 = @CarrierTrackingNumber COLLATE Latin1_General_BIN2   
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.ProductID = @ProductId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE (s.UnitPrice > @minUnitPrice AND s.UnitPrice < @maxUnitPrice)  
  
  -- After the above statements, there will be duplicates inside @retValue  
  -- Delete the duplicates from @retValue  
  DECLARE @duplicates Sales.fuzzySearchSalesOrderDetailTempType  
  
  INSERT INTO @duplicates (SalesOrderId, SalesOrderDetailId, recordcount)   
  SELECT SalesOrderId, SalesOrderDetailId, COUNT(*) AS recordCount  
  FROM @retValue  
  GROUP BY SalesOrderId, SalesOrderDetailId  
  
  -- Now we have one row per pair  
  -- clear and rebuild the result set  
  DELETE FROM @retValue  
  
  INSERT INTO @retValue  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN @duplicates d ON s.SalesOrderId = d.SalesOrderId AND s.SalesOrderDetailId = d.SalesOrderDetailId  
  
  -- After this every pair of (SalesOrderId, SalesOrderDetailId) in @retValue should be unique.  
  SELECT SalesorderId, SalesOrderDetailId, ModifiedDate FROM @retValue  
END  
GO  
```  
  
## <a name="or-operator-in-join-condition"></a><span data-ttu-id="0cf54-125">JOIN 条件中的 OR 运算符</span><span class="sxs-lookup"><span data-stu-id="0cf54-125">OR Operator in JOIN Condition</span></span>  
 <span data-ttu-id="0cf54-126">如果 SELECT 语句的 JOIN 条件中包含 OR 运算符，则可用以下方法模拟其行为。</span><span class="sxs-lookup"><span data-stu-id="0cf54-126">If you have an OR operator in a JOIN condition of a SELECT statement, you may use the following approach to simulate its behavior.</span></span> <span data-ttu-id="0cf54-127">如果 JOIN 条件中包含多个 OR 运算符，或有多个带 OR 运算符的 JOIN 条件，则可能需要多次执行此操作。</span><span class="sxs-lookup"><span data-stu-id="0cf54-127">If you have more than one OR operator in a JOIN condition or you have multiple JOIN condition with OR operators, you may need to do this more than once.</span></span>  
  
 <span data-ttu-id="0cf54-128">如果存在 OUTER JOIN 条件，则可将本解决方法与 OUTER JOIN 条件的解决方法结合使用。</span><span class="sxs-lookup"><span data-stu-id="0cf54-128">If you have OUTER JOIN conditions, you may combine this workaround with the workaround for OUTER JOIN conditions.</span></span>  
  
1.  <span data-ttu-id="0cf54-129">创建具有相应架构的内存优化表变量。</span><span class="sxs-lookup"><span data-stu-id="0cf54-129">Create a memory-optimized table variable with the appropriate schema.</span></span> <span data-ttu-id="0cf54-130">这需要预定义的内存优化表类型。</span><span class="sxs-lookup"><span data-stu-id="0cf54-130">This requires a predefined memory-optimized table type.</span></span>  
  
2.  <span data-ttu-id="0cf54-131">根据 OR 运算符联接的谓词将 JOIN 条件中的谓词分为两个部分。</span><span class="sxs-lookup"><span data-stu-id="0cf54-131">Separate the predicate in the JOIN condition into two parts according to the predicates joined by the OR operator.</span></span> <span data-ttu-id="0cf54-132">如果存在多个 JOIN 条件，则可能需要针对每个 JOIN 条件执行此操作，然后创建一组结果片段组合。</span><span class="sxs-lookup"><span data-stu-id="0cf54-132">If you have multiple JOIN conditions, you may need to do this for each JOIN condition and then create a set of combinations of the resulting fragments.</span></span> <span data-ttu-id="0cf54-133">例如，存在三个 JOIN 条件，每个 JOIN 条件包含一个 OR 运算符，则共有 2x2x2=8 个谓词。</span><span class="sxs-lookup"><span data-stu-id="0cf54-133">For example, if you have three JOIN conditions with one OR operator in each JOIN condition, you may have 2x2x2=8 predicates.</span></span>  
  
3.  <span data-ttu-id="0cf54-134">针对步骤 2 生成的每个谓词，创建将其结果插入到内存优化表变量（在步骤 1 中创建）中的查询。</span><span class="sxs-lookup"><span data-stu-id="0cf54-134">For each predicate produced by Step 2, create a query that will insert its result into the memory-optimized table variable created in Step 1.</span></span>  
  
4.  <span data-ttu-id="0cf54-135">如有必要，删除内存优化表变量中的重复项。</span><span class="sxs-lookup"><span data-stu-id="0cf54-135">If necessary, remove duplicates from the memory-optimized table variable.</span></span>  
  
5.  <span data-ttu-id="0cf54-136">使用内存优化表变量的内容作为查询的结果。</span><span class="sxs-lookup"><span data-stu-id="0cf54-136">Use the content of the memory-optimized table variable as the result from the query.</span></span>  
  
 <span data-ttu-id="0cf54-137">下面的示例使用来自 AdventureWorks2012 数据库（已针对 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 更新）的表。</span><span class="sxs-lookup"><span data-stu-id="0cf54-137">The following sample uses tables from the AdventureWorks2012 database that were updated for [!INCLUDE[hek_2](../includes/hek-2-md.md)].</span></span> <span data-ttu-id="0cf54-138">若要下载此示例的文件，请转到[AdventureWorks 数据库-2012、2008R2 和 2008](https://msftdbprodsamples.codeplex.com/releases/view/93587)。</span><span class="sxs-lookup"><span data-stu-id="0cf54-138">To download the files for this sample, goto [AdventureWorks Databases - 2012, 2008R2 and 2008](https://msftdbprodsamples.codeplex.com/releases/view/93587).</span></span> <span data-ttu-id="0cf54-139">若要将 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 代码示例应用于 AdventureWorks2012，请参阅[SQL Server 2014 内存中 OLTP 示例](https://msftdbprodsamples.codeplex.com/releases/view/114491)。</span><span class="sxs-lookup"><span data-stu-id="0cf54-139">To apply [!INCLUDE[hek_2](../includes/hek-2-md.md)] code sample to AdventureWorks2012, go to [SQL Server 2014 In-Memory OLTP Sample](https://msftdbprodsamples.codeplex.com/releases/view/114491).</span></span>  
  
 <span data-ttu-id="0cf54-140">将以下存储过程添加至数据库。</span><span class="sxs-lookup"><span data-stu-id="0cf54-140">Add the following stored procedure to the database.</span></span> <span data-ttu-id="0cf54-141">我们将把此存储过程转换为本机编译存储过程。</span><span class="sxs-lookup"><span data-stu-id="0cf54-141">We will convert this stored procedure to use native compilation.</span></span> <span data-ttu-id="0cf54-142">此示例使用 INNER JOIN 条件。</span><span class="sxs-lookup"><span data-stu-id="0cf54-142">This sample uses INNER JOIN conditions.</span></span>  
  
```  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesSpecialOffers_ondisk  
  @SpecialOfferId int  
AS BEGIN  
  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_ondisk s  
  JOIN Sales.SpecialOffer_onDisk offer   
    ON s.SpecialOfferID = offer.SpecialOfferID   
    OR s.ProductID IN (SELECT ProductId FROM Sales.SpecialOfferProduct sop WHERE sop.SpecialOfferID = @SpecialOfferId)  
END  
```  
  
 <span data-ttu-id="0cf54-143">转换后，表和存储过程架构如下所示：</span><span class="sxs-lookup"><span data-stu-id="0cf54-143">After conversion, the table and stored procedure schema is as follows,</span></span>  
  
```  
CREATE TYPE Sales.fuzzySearchSalesSpecialOffers_Type AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  SpecialOfferId int not null,  
  ModifiedDate datetime2(7) not null  
  INDEX ix_fuzzySearchSalesSpecialOffers_Type NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE TYPE Sales.fuzzySearchSalesSpecialOffers_TempType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  SpecialOfferId int not null,  
  recordcount int null  
  INDEX ix_fuzzySearchSalesSpecialOffers_TempType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesSpecialOffers_inmem  
  @SpecialOfferId int  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'ENGLISH')  
  
  DECLARE @retValue Sales.FuzzySearchSalesSpecialOffers_Type  
  
  -- Find all special offers matching the conditions  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, SpecialOfferid, ModifiedDate)  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN Sales.SpecialOffer_inmem offer   
    ON s.SpecialOfferID = offer.SpecialOfferID  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, SpecialOfferid, ModifiedDate)  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN Sales.SpecialOfferProduct_inmem sop   
    ON sop.SpecialOfferId = @SpecialOfferId AND s.ProductID = sop.ProductId  
  
  -- Now we need to remove the duplicates from @matchingSpecialOffers  
  DECLARE @duplicates Sales.fuzzySearchSalesSpecialOffers_TempType  
  
  INSERT INTO @duplicates (SalesOrderId, SalesOrderDetailId, SpecialOfferid, recordcount)  
  SELECT SalesOrderId, SalesOrderDetailId, SpecialOfferId, COUNT(*)   
  FROM @retValue  
  GROUP BY SalesOrderId, SalesOrderDetailId, SpecialOfferId  
  
  -- now there should be no duplicates within @duplicate  
  -- use @duplicate for join.  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN @duplicates offer   
    ON    s.SalesOrderId = offer.SalesOrderId   
      AND s.SalesOrderDetailId = offer.SalesOrderDetailID   
      AND s.SpecialOfferId = offer.SpecialOfferId  
END  
GO  
```  
  
## <a name="side-effects"></a><span data-ttu-id="0cf54-144">副作用</span><span class="sxs-lookup"><span data-stu-id="0cf54-144">Side Effects</span></span>  
 <span data-ttu-id="0cf54-145">如果 WHERE 子句或 JOIN 条件中包含多个 OR 运算符，则模拟此行为所需执行的查询数将呈指数增加。</span><span class="sxs-lookup"><span data-stu-id="0cf54-145">If you have more than one OR operator in the WHERE clause or JOIN condition, the number of queries you need to execute to simulate the behavior may increase exponentially.</span></span> <span data-ttu-id="0cf54-146">这可能会降低查询性能，并增加内存使用量（因为需要用到内存优化表变量）。</span><span class="sxs-lookup"><span data-stu-id="0cf54-146">This may slow down query performance and may increase memory usage due to the need to use memory-optimized table variables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cf54-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0cf54-147">See Also</span></span>  
 [<span data-ttu-id="0cf54-148">本机编译存储过程的迁移问题</span><span class="sxs-lookup"><span data-stu-id="0cf54-148">Migration Issues for Natively Compiled Stored Procedures</span></span>](../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)  
  
