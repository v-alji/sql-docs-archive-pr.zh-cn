---
title: 迁移 Check 和 Foreign Key 约束 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e0a1a1e4-0062-4872-93c3-cd91b7a43c23
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4bacd7a9c5c00fc6abbb763eaa02dca9493fa513
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587577"
---
# <a name="migrating-check-and-foreign-key-constraints"></a><span data-ttu-id="3b866-102">迁移检查约束和外键约束</span><span class="sxs-lookup"><span data-stu-id="3b866-102">Migrating Check and Foreign Key Constraints</span></span>
  <span data-ttu-id="3b866-103">中不支持 Check 和 foreign key 约束 [!INCLUDE[hek_2](../includes/hek-2-md.md)] [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3b866-103">Check and foreign key constraints are not supported in [!INCLUDE[hek_2](../includes/hek-2-md.md)] in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="3b866-104">这些构造通常用于在架构中强制实施逻辑数据完整性，并且对于维护应用程序的功能正确性非常重要。</span><span class="sxs-lookup"><span data-stu-id="3b866-104">These constructs are usually used to enforce logical data integrity in the schema and can be important to maintaining the functional correctness of applications.</span></span>  
  
 <span data-ttu-id="3b866-105">对表进行逻辑完整性检查（如 check 和 foreign key 约束）需要对事务进行额外处理，通常应避免对性能敏感的应用程序进行其他处理。</span><span class="sxs-lookup"><span data-stu-id="3b866-105">Logical integrity checks on a table such as check and foreign key constraints require additional processing on transactions and should generally be avoided for performance-sensitive applications.</span></span> <span data-ttu-id="3b866-106">但是，如果此类检查对你的应用程序至关重要，则有两种解决方法。</span><span class="sxs-lookup"><span data-stu-id="3b866-106">However, if such checks are crucial to your application, there exist two workarounds.</span></span>  
  
## <a name="checking-constraints-after-an-insert-update-or-delete-operation"></a><span data-ttu-id="3b866-107">在插入、更新或删除操作后检查约束</span><span class="sxs-lookup"><span data-stu-id="3b866-107">Checking Constraints After an Insert, Update, or Delete Operation</span></span>  
 <span data-ttu-id="3b866-108">此解决方法是乐观的，这是因为大多数的更改都不违反约束。</span><span class="sxs-lookup"><span data-stu-id="3b866-108">This workaround is optimistic, based on the assumption that the majority of changes do not violate the constraints.</span></span> <span data-ttu-id="3b866-109">在此解决方法中，先修改数据，然后再对约束进行评估。</span><span class="sxs-lookup"><span data-stu-id="3b866-109">In this workaround, data is modified first before the constraints are evaluated.</span></span> <span data-ttu-id="3b866-110">如果违反了约束，则会检测到该约束，但不会回滚更改。</span><span class="sxs-lookup"><span data-stu-id="3b866-110">If a constraint is violated, it would be detected, but the change will not be rolled back.</span></span>  
  
 <span data-ttu-id="3b866-111">此解决方法的优点是，对性能的影响最小，因为数据修改未被约束检查阻止。</span><span class="sxs-lookup"><span data-stu-id="3b866-111">This workaround has the advantage of having minimal impact on performance because data modification is not blocked by constraint checks.</span></span> <span data-ttu-id="3b866-112">但是，如果发生违反一个或多个约束的更改，则回滚该更改的过程可能需要很长时间。</span><span class="sxs-lookup"><span data-stu-id="3b866-112">However, if a change that violates one or more constraints does occur, the process to roll back that change could take a long time.</span></span>  
  
## <a name="enforcing-constraints-before-an-insert-update-or-delete-operation"></a><span data-ttu-id="3b866-113">在插入、更新或删除操作之前强制约束</span><span class="sxs-lookup"><span data-stu-id="3b866-113">Enforcing Constraints Before an Insert, Update, or Delete Operation</span></span>  
 <span data-ttu-id="3b866-114">此解决方法模拟约束的行为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3b866-114">This workaround emulates the behavior of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] constraints.</span></span> <span data-ttu-id="3b866-115">在数据修改发生之前检查约束，并在检查失败时终止事务。</span><span class="sxs-lookup"><span data-stu-id="3b866-115">The constraints are checked before data modification occurs and will terminate the transaction if a check fails.</span></span> <span data-ttu-id="3b866-116">此方法会对数据修改产生性能损失，但确保表中的数据始终满足约束。</span><span class="sxs-lookup"><span data-stu-id="3b866-116">This method incurs a performance penalty on data modifications, but ensures that data inside a table always satisfies the constraints.</span></span>  
  
 <span data-ttu-id="3b866-117">如果逻辑数据完整性对于正确性和违反约束的修改很有必要，请使用此解决方法。</span><span class="sxs-lookup"><span data-stu-id="3b866-117">Use this workaround when logical data integrity is crucial to correctness and modifications that violate a constraint are likely.</span></span> <span data-ttu-id="3b866-118">但是，为了保证完整性，所有数据修改都必须通过包含这些操作的存储过程进行。</span><span class="sxs-lookup"><span data-stu-id="3b866-118">However, to guarantee integrity, all data modifications must occur through stored procedures that include these enforcements.</span></span> <span data-ttu-id="3b866-119">通过即席查询和其他存储过程进行的修改不会强制实施这些约束，因此可能会违反这些约束，而不发出警告。</span><span class="sxs-lookup"><span data-stu-id="3b866-119">Modifications through ad-hoc queries and other stored procedures will not enforce these constraints and therefore may violate them with no warning.</span></span>  
  
## <a name="sample-code"></a><span data-ttu-id="3b866-120">代码示例</span><span class="sxs-lookup"><span data-stu-id="3b866-120">Sample Code</span></span>  
 <span data-ttu-id="3b866-121">下面的示例基于 AdventureWorks2012 数据库。</span><span class="sxs-lookup"><span data-stu-id="3b866-121">The following samples are based on the AdventureWorks2012 database.</span></span> <span data-ttu-id="3b866-122">具体而言，这些示例基于 [Sales]。除唯一索引之外的 [SalesOrderDetail] 表及其关联的 check 和 foreign key 约束。</span><span class="sxs-lookup"><span data-stu-id="3b866-122">Specifically, these samples are based on the [Sales].[SalesOrderDetail] table and its associated check and foreign key constraints in addition to the unique index.</span></span>  
  
 <span data-ttu-id="3b866-123">此处指定的存储过程仅适用于内边距运算。</span><span class="sxs-lookup"><span data-stu-id="3b866-123">The stored procedures specified here are for inset operations only.</span></span> <span data-ttu-id="3b866-124">用于更新和删除操作的存储过程应具有相似的结构。</span><span class="sxs-lookup"><span data-stu-id="3b866-124">Stored procedures for update and delete operations should have similar structures.</span></span>  
  
## <a name="table-definition-for-the-workarounds"></a><span data-ttu-id="3b866-125">解决方法的表定义</span><span class="sxs-lookup"><span data-stu-id="3b866-125">Table Definition for the Workarounds</span></span>  
 <span data-ttu-id="3b866-126">转换为内存优化表之前，[Sales] 的定义。[SalesOrderDetail] 如下所示：</span><span class="sxs-lookup"><span data-stu-id="3b866-126">Before converting to a memory-optimized table, the definition for [Sales].[SalesOrderDetail] is as follows:</span></span>  
  
```sql  
USE [AdventureWorks2012]  
GO  
  
CREATE TABLE [Sales].[SalesOrderDetail]([SalesOrderID] [int] NOT NULL,  
   [SalesOrderDetailID] [int] IDENTITY(1,1) NOT NULL,  
   [CarrierTrackingNumber] [nvarchar](25) NULL,  
   [OrderQty] [smallint] NOT NULL,  
   [ProductID] [int] NOT NULL,  
   [SpecialOfferID] [int] NOT NULL,  
   [UnitPrice] [money] NOT NULL,  
   [UnitPriceDiscount] [money] NOT NULL CONSTRAINT [DF_SalesOrderDetail_UnitPriceDiscount]  DEFAULT ((0.0)),  
   [LineTotal]  AS (isnull(([UnitPrice]*((1.0)-[UnitPriceDiscount]))*[OrderQty],(0.0))),  
   [rowguid] [uniqueidentifier] ROWGUIDCOL  NOT NULL CONSTRAINT [DF_SalesOrderDetail_rowguid]  DEFAULT (newid()),  
   [ModifiedDate] [datetime] NOT NULL CONSTRAINT [DF_SalesOrderDetail_ModifiedDate]  DEFAULT (getdate()),  
 CONSTRAINT [PK_SalesOrderDetail_SalesOrderID_SalesOrderDetailID] PRIMARY KEY CLUSTERED   
(  
   [SalesOrderID] ASC,  
   [SalesOrderDetailID] ASC  
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]  
  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail]  WITH CHECK ADD  CONSTRAINT [FK_SalesOrderDetail_SalesOrderHeader_SalesOrderID] FOREIGN KEY([SalesOrderID])  
REFERENCES [Sales].[SalesOrderHeader] ([SalesOrderID])  
ON DELETE CASCADE  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail] CHECK CONSTRAINT [FK_SalesOrderDetail_SalesOrderHeader_SalesOrderID]  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail]  WITH CHECK ADD  CONSTRAINT [FK_SalesOrderDetail_SpecialOfferProduct_SpecialOfferIDProductID] FOREIGN KEY([SpecialOfferID], [ProductID])  
REFERENCES [Sales].[SpecialOfferProduct] ([SpecialOfferID], [ProductID])  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail] CHECK CONSTRAINT [FK_SalesOrderDetail_SpecialOfferProduct_SpecialOfferIDProductID]  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail]  WITH CHECK ADD  CONSTRAINT [CK_SalesOrderDetail_OrderQty] CHECK  (([OrderQty]>(0)))  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail] CHECK CONSTRAINT [CK_SalesOrderDetail_OrderQty]  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail]  WITH CHECK ADD  CONSTRAINT [CK_SalesOrderDetail_UnitPrice] CHECK  (([UnitPrice]>=(0.00)))  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail] CHECK CONSTRAINT [CK_SalesOrderDetail_UnitPrice]  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail]  WITH CHECK ADD  CONSTRAINT [CK_SalesOrderDetail_UnitPriceDiscount] CHECK  (([UnitPriceDiscount]>=(0.00)))  
GO  
  
ALTER TABLE [Sales].[SalesOrderDetail] CHECK CONSTRAINT [CK_SalesOrderDetail_UnitPriceDiscount]  
GO  
```  
  
 <span data-ttu-id="3b866-127">转换为内存优化表后，[Sales] 的定义。[SalesOrderDetail] 如下所示：</span><span class="sxs-lookup"><span data-stu-id="3b866-127">After converting to a memory-optimized table, the definition for [Sales].[SalesOrderDetail] is as follows:</span></span>  
  
 <span data-ttu-id="3b866-128">请注意，rowguid 不再是 ROWGUIDCOL，因为在中不受支持 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3b866-128">Note that rowguid is no longer a ROWGUIDCOL as it is not supported in [!INCLUDE[hek_2](../includes/hek-2-md.md)].</span></span> <span data-ttu-id="3b866-129">列已删除。</span><span class="sxs-lookup"><span data-stu-id="3b866-129">The column has been removed.</span></span> <span data-ttu-id="3b866-130">此外，LineTotal 是计算列并超出本文的范围，因此它也已删除。</span><span class="sxs-lookup"><span data-stu-id="3b866-130">In addition, LineTotal is a computed column and out of scope for this article, so it also has been removed.</span></span>  
  
```sql  
USE [AdventureWorks2012]  
GO  
  
CREATE TABLE [Sales].[SalesOrderDetail]([SalesOrderID] [int] NOT NULL,  
   [SalesOrderDetailID] [int] IDENTITY(1,1) NOT NULL,  
   [CarrierTrackingNumber] [nvarchar](25) NULL,  
   [OrderQty] [smallint] NOT NULL,  
   [ProductID] [int] NOT NULL,  
   [SpecialOfferID] [int] NOT NULL,  
   [UnitPrice] [money] NOT NULL,  
   [UnitPriceDiscount] [money] NOT NULL CONSTRAINT [DF_SalesOrderDetail_UnitPriceDiscount]  DEFAULT ((0.0)),  
   [ModifiedDate] [datetime] NOT NULL CONSTRAINT [DF_SalesOrderDetail_ModifiedDate]  DEFAULT (getdate()),  
   CONSTRAINT [PK_SalesOrderDetail_SalesOrderID_SalesOrderDetailID] PRIMARY KEY NONCLUSTERED   
   (  
      [SalesOrderID] ASC,  
      [SalesOrderDetailID] ASC  
   ),  
   INDEX [AK_SalesOrderDetail_rowguid] NONCLUSTERED HASH ([rowguid]) WITH (BUCKET_COUNT = 1048576),  
   INDEX [IX_SalesOrderDetail_ProductId] NONCLUSTERED ([ProductId] ASC)) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
  
GO  
```  
  
## <a name="checking-constraints-after-an-insert-update-or-delete-operation"></a><span data-ttu-id="3b866-131">在插入、更新或删除操作后检查约束</span><span class="sxs-lookup"><span data-stu-id="3b866-131">Checking Constraints After an Insert, Update, or Delete Operation</span></span>  
  
```sql  
USE AdventureWorks2012  
GO  
  
CREATE PROCEDURE Sales.usp_insert_SalesOrderDetails   
   @SalesOrderId int, @CarrierTrackingNumber nvarchar(25) = null, @OrderQty smallint, @ProductId int, @SpecialOfferID int,   
   @UnitPrice money, @UnitPriceDiscount money = 0.00, @ModifiedDate datetime = null  
AS  
BEGIN  
BEGIN TRANSACTION   
   -- handle defaults for the insert.  
   -- This is to make the insert logic less complex. Default constraints on the table should be in sync with this logic.  
   -- Conversely, you can write an INSERT statement for each case where one or more values for the three columns with default constraints are not specified.  
   IF @ModifiedDate = null SET @ModifiedDate = GETDATE()  
  
   -- Insert the row.  
   INSERT INTO Sales.SalesOrderDetail   
      (SalesOrderID, CarrierTrackingNumber, OrderQty, ProductID, SpecialOfferID, UnitPrice, UnitPriceDiscount, ModifiedDate)  
   VALUES   
      (@SalesOrderId, @CarrierTrackingNumber, @OrderQty, @ProductID, @SpecialOfferID, @UnitPrice, @UnitPriceDiscount, , @ModifiedDate)   
  
   -- Now handle constraints  
   DECLARE @violations TABLE   
   (   
      ConstraintName sysname,  
      ViolatedValue1 sql_variant,  
      ViolatedValue2 sql_variant  
   )  
  
   -- FK_SalesOrderDetail_SalesOrderHeader_SalesOrderID  
   IF NOT EXISTS (SELECT soh.SalesOrderId AS [Exists] FROM Sales.SalesOrderHeader soh WHERE soh.SalesOrderID = @SalesOrderId)   
      INSERT INTO @violations (ConstraintName, ViolatedValue1, ViolatedValue2)   
      VALUES (N'FK_SalesOrderDetail_SalesOrderHeader_SalesOrderID', @SalesOrderId, NULL)  
   -- FK_SalesOrderDetail_SpecialOfferProduct_SpecialOfferIDProductID  
   IF NOT EXISTS (SELECT sop.SpecialOfferID, sop.ProductID FROM [Sales].[SpecialOfferProduct] sop WHERE sop.SpecialOfferID = @SpecialOfferID AND sop.ProductID = @ProductId)  
      INSERT INTO @violations (ConstraintName, ViolatedValue1, ViolatedValue2)   
      VALUES (N'FK_SalesOrderDetail_SpecialOfferProduct_SpecialOfferIDProductID', @SpecialOfferId, @ProductId)  
   -- CK_SalesOrderDetail_OrderQty  
   IF NOT @OrderQty > 0   
      INSERT INTO @violations (ConstraintName, ViolatedValue1, ViolatedValue2)   
      VALUES (N'CK_SalesOrderDetail_OrderQty', @OrderQty, NULL)  
   -- CK_SalesOrderDetail_UnitPrice  
   IF NOT @UnitPrice >= 0.00  
      INSERT INTO @violations (ConstraintName, ViolatedValue1, ViolatedValue2)   
      VALUES (N'CK_SalesOrderDetail_UnitPrice', @UnitPrice, NULL)  
   -- CK_SalesOrderDetail_UnitPriceDiscout  
   IF NOT @UnitPriceDiscount >= 0.00  
      INSERT INTO @violations (ConstraintName, ViolatedValue1, ViolatedValue2)   
      VALUES (N'CK_SalesOrderDetail_UnitPriceDiscount', @UnitPriceDiscount, NULL)  
  
   -- Return a rowset containing violated constraints. On an item that doesn't violate anything, should return an empty rowset.  
   SELECT ConstraintName, ViolatedValue1, ViolatedValue2 FROM @violations  
   COMMIT TRANSACTION  
END  
```  
  
## <a name="enforcing-constraints-before-an-insert-update-or-delete-operation"></a><span data-ttu-id="3b866-132">在插入、更新或删除操作之前强制约束</span><span class="sxs-lookup"><span data-stu-id="3b866-132">Enforcing Constraints Before an Insert, Update or Delete Operation</span></span>  
  
```sql  
USE AdventureWorks2012  
GO  
  
CREATE PROCEDURE Sales.usp_insert_SalesOrderDetails   
   @SalesOrderId int, @CarrierTrackingNumber nvarchar(25) = null, @OrderQty smallint, @ProductId int, @SpecialOfferID int,   
   @UnitPrice money, @UnitPriceDiscount money = 0.00, @ModifiedDate datetime = null  
AS  
BEGIN  
BEGIN TRY  
   BEGIN TRANSACTION  
   -- Verify the constraints first.  
   -- FK_SalesOrderDetail_SalesOrderHeader_SalesOrderID  
   IF NOT EXISTS (SELECT soh.SalesOrderId FROM Sales.SalesOrderHeader soh WHERE soh.SalesOrderID = @SalesOrderId)   
      THROW 50547, N'This SalesOrderId does not exist in SalesOrderHeader', 1  
   -- FK_SalesOrderDetail_SpecialOfferProduct_SpecialOfferIDProductID  
   IF NOT EXISTS (SELECT sop.SpecialOfferID, sop.ProductID FROM [Sales].[SpecialOfferProduct] sop WHERE sop.SpecialOfferID = @SpecialOfferID AND sop.ProductID = @ProductId)  
      THROW 50547, N'This combination of SpecialOfferID and ProductID does not exist in SpecialOfferProduct', 1   
   -- CK_SalesOrderDetail_OrderQty  
   IF NOT @OrderQty > 0   
      THROW 50547, N'OrderQty must be greater than zero.', 1  
   -- CK_SalesOrderDetail_UnitPrice  
   IF NOT @UnitPrice >= 0.00  
      THROW 50547, N'UnitPrice cannot be negative.', 1  
   -- CK_SalesOrderDetail_UnitPriceDiscout  
   IF NOT @UnitPriceDiscount >= 0.00  
      THROW 50547, N'UnitPriceDiscount cannot be negative', 1  
  
   -- All verifications have now passed. Proceed to insert.  
  
   -- handle defaults for the insert.  
   -- This is to make the insert logic less complex. Default constraints on the table should be in sync with this logic.  
   -- Conversely, you can write an INSERT statement for each case where one or more values for the three columns with default constraints are not specified.  
  
   IF @ModifiedDate = null SET @ModifiedDate = GETDATE()  
  
   -- Calculate computed columnn and store it.  
   DECLARE @LineTotal numeric(38, 6)  
   SET @LineTotal = (isnull((@UnitPrice * ((1.0) - @UnitPriceDiscount)) * @OrderQty, (0.0)))  
  
   -- Insert the row.  
   INSERT INTO Sales.SalesOrderDetail   
      (SalesOrderID, CarrierTrackingNumber, OrderQty, ProductID, SpecialOfferID, UnitPrice, UnitPriceDiscount, ModifiedDate)  
   VALUES   
      (@SalesOrderId, @CarrierTrackingNumber, @OrderQty, @ProductID, @SpecialOfferID, @UnitPrice, @UnitPriceDiscount, @ModifiedDate)  
   COMMIT TRANSACTION  
END TRY  
BEGIN CATCH  
   IF @@TRANCOUNT > 0  
      ROLLBACK TRANSACTION  
      THROW;  
END CATCH  
END  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b866-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3b866-133">See Also</span></span>  
 [<span data-ttu-id="3b866-134">迁移到内存中 OLTP</span><span class="sxs-lookup"><span data-stu-id="3b866-134">Migrating to In-Memory OLTP</span></span>](../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  
