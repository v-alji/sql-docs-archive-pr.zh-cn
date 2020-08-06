---
title: 序列号 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- sequence number object, overview
- sequence [Database Engine]
- autonumbers, sequences
- sequence numbers [SQL Server]
- sequence number object
ms.assetid: c900e30d-2fd3-4d5f-98ee-7832f37e79d1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6c65b4df915a85cf0ec7c7c0c8c0ff9f6607ad96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693681"
---
# <a name="sequence-numbers"></a><span data-ttu-id="495ab-102">序列号</span><span class="sxs-lookup"><span data-stu-id="495ab-102">Sequence Numbers</span></span>
  <span data-ttu-id="495ab-103">序列是一种用户定义的架构绑定对象，它根据创建该序列时采用的规范生成一组数值。</span><span class="sxs-lookup"><span data-stu-id="495ab-103">A sequence is a user-defined schema-bound object that generates a sequence of numeric values according to the specification with which the sequence was created.</span></span> <span data-ttu-id="495ab-104">这组数值以定义的间隔按升序或降序生成，并且可根据要求循环（重复）。</span><span class="sxs-lookup"><span data-stu-id="495ab-104">The sequence of numeric values is generated in an ascending or descending order at a defined interval and may cycle (repeat) as requested.</span></span> <span data-ttu-id="495ab-105">序列不与表相关联，这一点与标识列不同。</span><span class="sxs-lookup"><span data-stu-id="495ab-105">Sequences, unlike identity columns, are not associated with tables.</span></span> <span data-ttu-id="495ab-106">应用程序将引用某一序列对象以便接收其下一个值。</span><span class="sxs-lookup"><span data-stu-id="495ab-106">An application refers to a sequence object to receive its next value.</span></span> <span data-ttu-id="495ab-107">序列与表之间的关系由应用程序控制。</span><span class="sxs-lookup"><span data-stu-id="495ab-107">The relationship between sequences and tables is controlled by the application.</span></span> <span data-ttu-id="495ab-108">用户应用程序可以引用某一序列对象并且跨多行和表协调值键。</span><span class="sxs-lookup"><span data-stu-id="495ab-108">User applications can reference a sequence object and coordinate the values keys across multiple rows and tables.</span></span>  
  
 <span data-ttu-id="495ab-109">序列是通过使用 **CREATE SEQUENCE** 语句独立于表来创建的。</span><span class="sxs-lookup"><span data-stu-id="495ab-109">A sequence is created independently of the tables by using the **CREATE SEQUENCE** statement.</span></span> <span data-ttu-id="495ab-110">其选项使您可以控制增量、最大值和最小值、起始点、自动重新开始功能和缓存以便改进性能。</span><span class="sxs-lookup"><span data-stu-id="495ab-110">Options enable you to control the increment, maximum and minimum values, starting point, automatic restarting capability, and caching to improve performance.</span></span> <span data-ttu-id="495ab-111">有关这些选项的信息，请参阅 [CREATE SEQUENCE](/sql/t-sql/statements/create-sequence-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="495ab-111">For information about the options, see [CREATE SEQUENCE](/sql/t-sql/statements/create-sequence-transact-sql).</span></span>  
  
 <span data-ttu-id="495ab-112">与在插入行时生成的标识列值不同，应用程序可以通过调用 [NEXT VALUE FOR](/sql/t-sql/functions/next-value-for-transact-sql) 函数在插入行之前获取下一序列号。</span><span class="sxs-lookup"><span data-stu-id="495ab-112">Unlike identity column values, which are generated when rows are inserted, an application can obtain the next sequence number before inserting the row by calling the [NEXT VALUE FOR](/sql/t-sql/functions/next-value-for-transact-sql) function.</span></span> <span data-ttu-id="495ab-113">在调用 NEXT VALUE FOR 时分配该序列号，即使在该序列号永远也不插入某个表中时也是如此。</span><span class="sxs-lookup"><span data-stu-id="495ab-113">The sequence number is allocated when NEXT VALUE FOR is called even if the number is never inserted into a table.</span></span> <span data-ttu-id="495ab-114">此 NEXT VALUE FOR 函数可用作表定义中某个列的默认值。</span><span class="sxs-lookup"><span data-stu-id="495ab-114">The NEXT VALUE FOR function can be used as the default value for a column in a table definition.</span></span> <span data-ttu-id="495ab-115">使用 [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) 可一次获取某个范围的多个序列号。</span><span class="sxs-lookup"><span data-stu-id="495ab-115">Use [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) to get a range of multiple sequence numbers at once.</span></span>  
  
 <span data-ttu-id="495ab-116">序列可定义为任何整数数据类型。</span><span class="sxs-lookup"><span data-stu-id="495ab-116">A sequence can be defined as any integer data type.</span></span> <span data-ttu-id="495ab-117">如果未指定数据类型，则序列将默认为 `bigint`。</span><span class="sxs-lookup"><span data-stu-id="495ab-117">If the data type is not specified, a sequence defaults to `bigint`.</span></span>  
  
## <a name="using-sequences"></a><span data-ttu-id="495ab-118">使用序列</span><span class="sxs-lookup"><span data-stu-id="495ab-118">Using Sequences</span></span>  
 <span data-ttu-id="495ab-119">在以下情况下将使用序列，而非标识列：</span><span class="sxs-lookup"><span data-stu-id="495ab-119">Use sequences instead of identity columns in the following scenarios:</span></span>  
  
-   <span data-ttu-id="495ab-120">应用程序要求在插入到表中之前有一个数值。</span><span class="sxs-lookup"><span data-stu-id="495ab-120">The application requires a number before the insert into the table is made.</span></span>  
  
-   <span data-ttu-id="495ab-121">应用程序要求在多个表之间或者某个表内的多个列之间共享单个数值系列。</span><span class="sxs-lookup"><span data-stu-id="495ab-121">The application requires sharing a single series of numbers between multiple tables or multiple columns within a table.</span></span>  
  
-   <span data-ttu-id="495ab-122">在达到指定的数值时，应用程序必须重新开始该数值系列。</span><span class="sxs-lookup"><span data-stu-id="495ab-122">The application must restart the number series when a specified number is reached.</span></span> <span data-ttu-id="495ab-123">例如，在分配值 1 到 10 后，应用程序再次开始分配值 1 到 10。</span><span class="sxs-lookup"><span data-stu-id="495ab-123">For example, after assigning values 1 through 10, the application starts assigning values 1 through 10 again.</span></span>  
  
-   <span data-ttu-id="495ab-124">应用程序要求序列值按其他字段排序。</span><span class="sxs-lookup"><span data-stu-id="495ab-124">The application requires sequence values to be sorted by another field.</span></span> <span data-ttu-id="495ab-125">NEXT VALUE FOR 函数可以将 OVER 子句应用于该函数调用。</span><span class="sxs-lookup"><span data-stu-id="495ab-125">The NEXT VALUE FOR function can apply the OVER clause to the function call.</span></span> <span data-ttu-id="495ab-126">OVER 子句确保返回的值按照 OVER 子句的 ORDER BY 子句的顺序生成。</span><span class="sxs-lookup"><span data-stu-id="495ab-126">The OVER clause guarantees that the values returned are generated in the order of the OVER clause's ORDER BY clause.</span></span>  
  
-   <span data-ttu-id="495ab-127">应用程序要求同时分配多个数值。</span><span class="sxs-lookup"><span data-stu-id="495ab-127">An application requires multiple numbers to be assigned at the same time.</span></span> <span data-ttu-id="495ab-128">例如，应用程序需要保留五个序号。</span><span class="sxs-lookup"><span data-stu-id="495ab-128">For example, an application needs to reserve five sequential numbers.</span></span> <span data-ttu-id="495ab-129">如果正在同时向其他进程发出数值，则请求标识值可能会导致在系列中出现间断。</span><span class="sxs-lookup"><span data-stu-id="495ab-129">Requesting identity values could result in gaps in the series if other processes were simultaneously issued numbers.</span></span> <span data-ttu-id="495ab-130">调用 sp_sequence_get_range 可以一次检索该序列中的若干数值。</span><span class="sxs-lookup"><span data-stu-id="495ab-130">Calling sp_sequence_get_range can retrieve several numbers in the sequence at once.</span></span>  
  
-   <span data-ttu-id="495ab-131">您需要更改序列的规范，例如增量值。</span><span class="sxs-lookup"><span data-stu-id="495ab-131">You need to change the specification of the sequence, such as the increment value.</span></span>  
  
## <a name="limitations"></a><span data-ttu-id="495ab-132">限制</span><span class="sxs-lookup"><span data-stu-id="495ab-132">Limitations</span></span>  
 <span data-ttu-id="495ab-133">与不能更改其值的标识列不同，在插入到表后不自动保护序列值。</span><span class="sxs-lookup"><span data-stu-id="495ab-133">Unlike identity columns, whose values cannot be changed, sequence values are not automatically protected after insertion into the table.</span></span> <span data-ttu-id="495ab-134">若要防止更改序列值，请对表使用更新触发器以便回滚更改。</span><span class="sxs-lookup"><span data-stu-id="495ab-134">To prevent sequence values from being changed, use an update trigger on the table to roll back changes.</span></span>  
  
 <span data-ttu-id="495ab-135">对于序列值不自动强制唯一性。</span><span class="sxs-lookup"><span data-stu-id="495ab-135">Uniqueness is not automatically enforced for sequence values.</span></span> <span data-ttu-id="495ab-136">按照设计能够重复使用序列值。</span><span class="sxs-lookup"><span data-stu-id="495ab-136">The ability to reuse sequence values is by design.</span></span> <span data-ttu-id="495ab-137">如果某个表中的序列值要求唯一，则对列创建唯一索引。</span><span class="sxs-lookup"><span data-stu-id="495ab-137">If sequence values in a table are required to be unique, create a unique index on the column.</span></span> <span data-ttu-id="495ab-138">如果要求表中的序列值在一组表之间唯一，则创建触发器以免更新语句或序列号循环导致的重复项。</span><span class="sxs-lookup"><span data-stu-id="495ab-138">If sequence values in a table are required to be unique throughout a group of tables, create triggers to prevent duplicates caused by update statements or sequence number cycling.</span></span>  
  
 <span data-ttu-id="495ab-139">序列对象根据其定义生成数值，但序列对象不控制生成数值的方式。</span><span class="sxs-lookup"><span data-stu-id="495ab-139">The sequence object generates numbers according to its definition, but the sequence object does not control how the numbers are used.</span></span> <span data-ttu-id="495ab-140">在回滚事务时、在某个序列对象由多个表共享时或者在分配序列号且不在多个表中使用它们时，插入到表中的序列号可能具有间断。</span><span class="sxs-lookup"><span data-stu-id="495ab-140">Sequence numbers inserted into a table can have gaps when a transaction is rolled back, when a sequence object is shared by multiple tables, or when sequence numbers are allocated without using them in tables.</span></span> <span data-ttu-id="495ab-141">当使用 CACHE 选项创建时，意外关机（如电源故障）可能导致缓存中的序列号丢失。</span><span class="sxs-lookup"><span data-stu-id="495ab-141">When created with the CACHE option, an unexpected shutdown, such as a power failure, can lose the sequence numbers in the cache.</span></span>  
  
 <span data-ttu-id="495ab-142">如果在单个 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句中有多个 `NEXT VALUE FOR` 函数的实例指定同一序列生成器，则所有这些实例返回该 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句所处理的指定行的相同值。</span><span class="sxs-lookup"><span data-stu-id="495ab-142">If there are multiple instances of the `NEXT VALUE FOR` function specifying the same sequence generator within a single [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement, all those instances return the same value for a given row processed by that [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="495ab-143">此行为与 ANSI 标准保持一致。</span><span class="sxs-lookup"><span data-stu-id="495ab-143">This behavior is consistent with the ANSI standard.</span></span>  
  
## <a name="typical-use"></a><span data-ttu-id="495ab-144">典型用法</span><span class="sxs-lookup"><span data-stu-id="495ab-144">Typical Use</span></span>  
 <span data-ttu-id="495ab-145">若要创建从 -2,147,483,648 到 2,147,483,647 且增量为 1 的整数序列号，请使用以下语句。</span><span class="sxs-lookup"><span data-stu-id="495ab-145">To create an integer sequence number that increments by 1 from -2,147,483,648 to 2,147,483,647, use the following statement.</span></span>  
  
```  
CREATE SEQUENCE Schema.SequenceName  
    AS int  
    INCREMENT BY 1 ;  
```  
  
 <span data-ttu-id="495ab-146">若要创建类似于从 1 到 2,147,483,647 且增量为 1 的标识列的整数序列号，请使用以下语句。</span><span class="sxs-lookup"><span data-stu-id="495ab-146">To create an integer sequence number similar to an identity column that increments by 1 from 1 to 2,147,483,647, use the following statement.</span></span>  
  
```  
CREATE SEQUENCE Schema.SequenceName  
    AS int  
    START WITH 1  
    INCREMENT BY 1 ;  
  
```  
  
## <a name="managing-sequences"></a><span data-ttu-id="495ab-147">管理序列</span><span class="sxs-lookup"><span data-stu-id="495ab-147">Managing Sequences</span></span>  
 <span data-ttu-id="495ab-148">有关序列的信息，请查询 [sys.sequences](/sql/relational-databases/system-catalog-views/sys-sequences-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="495ab-148">For information about sequences, query [sys.sequences](/sql/relational-databases/system-catalog-views/sys-sequences-transact-sql).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="495ab-149">示例</span><span class="sxs-lookup"><span data-stu-id="495ab-149">Examples</span></span>  
 <span data-ttu-id="495ab-150">请在 [CREATE SEQUENCE (Transact-SQL)](/sql/t-sql/statements/create-sequence-transact-sql)、[NEXT VALUE FOR (Transact-SQL)](/sql/t-sql/functions/next-value-for-transact-sql) 和 [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) 主题查看其他示例。</span><span class="sxs-lookup"><span data-stu-id="495ab-150">There are additional examples in the topics [CREATE SEQUENCE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-sequence-transact-sql), [NEXT VALUE FOR &#40;Transact-SQL&#41;](/sql/t-sql/functions/next-value-for-transact-sql), and [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql).</span></span>  
  
### <a name="a-using-a-sequence-number-in-a-single-table"></a><span data-ttu-id="495ab-151">A.</span><span class="sxs-lookup"><span data-stu-id="495ab-151">A.</span></span> <span data-ttu-id="495ab-152">在单个表中使用序列号</span><span class="sxs-lookup"><span data-stu-id="495ab-152">Using a sequence number in a single table</span></span>  
 <span data-ttu-id="495ab-153">下面的示例创建一个名为 Test 的架构、一个名为 Orders 的表以及一个名为 CountBy1 的序列，然后使用 NEXT VALUE FOR 函数将行插入到该表中。</span><span class="sxs-lookup"><span data-stu-id="495ab-153">The following example creates a schema named Test, a table named Orders, and a sequence named CountBy1, and then inserts rows into the table using the NEXT VALUE FOR function.</span></span>  
  
```  
--Create the Test schema  
CREATE SCHEMA Test ;  
GO  
  
-- Create a table  
CREATE TABLE Test.Orders  
    (OrderID int PRIMARY KEY,  
    Name varchar(20) NOT NULL,  
    Qty int NOT NULL);  
GO  
  
-- Create a sequence  
CREATE SEQUENCE Test.CountBy1  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
  
-- Insert three records  
INSERT Test.Orders (OrderID, Name, Qty)  
    VALUES (NEXT VALUE FOR Test.CountBy1, 'Tire', 2) ;  
INSERT test.Orders (OrderID, Name, Qty)  
    VALUES (NEXT VALUE FOR Test.CountBy1, 'Seat', 1) ;  
INSERT test.Orders (OrderID, Name, Qty)  
    VALUES (NEXT VALUE FOR Test.CountBy1, 'Brake', 1) ;  
GO  
  
-- View the table  
SELECT * FROM Test.Orders ;  
GO  
```  
  
 [!INCLUDE[ssResult](../../../includes/ssresult-md.md)]  
  
 `OrderID  Name    Qty`  
  
 `1        Tire    2`  
  
 `2        Seat    1`  
  
 `3        Brake   1`  
  
### <a name="b-calling-next-value-for-before-inserting-a-row"></a><span data-ttu-id="495ab-154">B.</span><span class="sxs-lookup"><span data-stu-id="495ab-154">B.</span></span> <span data-ttu-id="495ab-155">在插入某一行之前调用 NEXT VALUE FOR</span><span class="sxs-lookup"><span data-stu-id="495ab-155">Calling NEXT VALUE FOR before inserting a row</span></span>  
 <span data-ttu-id="495ab-156">下面的示例通过使用在示例 A 中创建的 `Orders` 表，声明一个名为 `@nextID`的变量，然后使用 NEXT VALUE FOR 函数将该变量设置为下一个可用的序列号。</span><span class="sxs-lookup"><span data-stu-id="495ab-156">Using the `Orders` table created in example A, the following example declares a variable named `@nextID`, and then uses the NEXT VALUE FOR function to set the variable to the next available sequence number.</span></span> <span data-ttu-id="495ab-157">假定应用程序对订单执行某种处理，例如向客户提供其潜在订单的 `OrderID` 号，然后验证该订单。</span><span class="sxs-lookup"><span data-stu-id="495ab-157">The application is presumed to do some processing of the order, such as providing the customer with the `OrderID` number of their potential order, and then validates the order.</span></span> <span data-ttu-id="495ab-158">无论这一处理时间有多长，或者在这个处理过程中添加了多少其他订单，原始编号都保留供此连接使用。</span><span class="sxs-lookup"><span data-stu-id="495ab-158">No matter how long this processing might take, or how many other orders are added during the process, the original number is preserved for use by this connection.</span></span> <span data-ttu-id="495ab-159">最后， `INSERT` 语句将该订单添加到 `Orders` 表。</span><span class="sxs-lookup"><span data-stu-id="495ab-159">Finally, the `INSERT` statement adds the order to the `Orders` table.</span></span>  
  
```  
DECLARE @NextID int ;  
SET @NextID = NEXT VALUE FOR Test.CountBy1;  
-- Some work happens  
INSERT Test.Orders (OrderID, Name, Qty)  
    VALUES (@NextID, 'Rim', 2) ;  
GO  
  
```  
  
### <a name="c-using-a-sequence-number-in-multiple-tables"></a><span data-ttu-id="495ab-160">C.</span><span class="sxs-lookup"><span data-stu-id="495ab-160">C.</span></span> <span data-ttu-id="495ab-161">在多个表中使用序列号</span><span class="sxs-lookup"><span data-stu-id="495ab-161">Using a sequence number in multiple tables</span></span>  
 <span data-ttu-id="495ab-162">此示例假定一个生产线监视进程接收在车间中发生的事件的通知。</span><span class="sxs-lookup"><span data-stu-id="495ab-162">This example assumes that a production-line monitoring process receives notification of events that occur throughout the workshop.</span></span> <span data-ttu-id="495ab-163">每个事件都接收一个唯一且单调递增的 `EventID` 号。</span><span class="sxs-lookup"><span data-stu-id="495ab-163">Each event receives a unique and monotonically increasing `EventID` number.</span></span> <span data-ttu-id="495ab-164">所有事件都使用相同的 `EventID` 序列号，因此，汇总了所有事件的报表可唯一标识各事件。</span><span class="sxs-lookup"><span data-stu-id="495ab-164">All events use the same `EventID` sequence number so that reports that combine all events can uniquely identify each event.</span></span> <span data-ttu-id="495ab-165">但是，事件数据根据事件的类型存储于三个不同的表中。</span><span class="sxs-lookup"><span data-stu-id="495ab-165">However the event data is stored in three different tables, depending on the type of event.</span></span> <span data-ttu-id="495ab-166">该代码示例创建一个名为 `Audit`的架构、一个名为 `EventCounter`的序列以及三个表，这三个表都使用 `EventCounter` 序列作为默认值。</span><span class="sxs-lookup"><span data-stu-id="495ab-166">The code example creates a schema named `Audit`, a sequence named `EventCounter`, and three tables which each use the `EventCounter` sequence as a default value.</span></span> <span data-ttu-id="495ab-167">然后，该示例向这三个表添加行并且查询结果。</span><span class="sxs-lookup"><span data-stu-id="495ab-167">Then the example adds rows to the three tables and queries the results.</span></span>  
  
```  
CREATE SCHEMA Audit ;  
GO  
CREATE SEQUENCE Audit.EventCounter  
    AS int  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
  
CREATE TABLE Audit.ProcessEvents  
(  
    EventID int PRIMARY KEY CLUSTERED   
        DEFAULT (NEXT VALUE FOR Audit.EventCounter),  
    EventTime datetime NOT NULL DEFAULT (getdate()),  
    EventCode nvarchar(5) NOT NULL,  
    Description nvarchar(300) NULL  
) ;  
GO  
  
CREATE TABLE Audit.ErrorEvents  
(  
    EventID int PRIMARY KEY CLUSTERED  
        DEFAULT (NEXT VALUE FOR Audit.EventCounter),  
    EventTime datetime NOT NULL DEFAULT (getdate()),  
    EquipmentID int NULL,  
    ErrorNumber int NOT NULL,  
    EventDesc nvarchar(256) NULL  
) ;  
GO  
  
CREATE TABLE Audit.StartStopEvents  
(  
    EventID int PRIMARY KEY CLUSTERED  
        DEFAULT (NEXT VALUE FOR Audit.EventCounter),  
    EventTime datetime NOT NULL DEFAULT (getdate()),  
    EquipmentID int NOT NULL,  
    StartOrStop bit NOT NULL  
) ;  
GO  
  
INSERT Audit.StartStopEvents (EquipmentID, StartOrStop)   
    VALUES (248, 0) ;  
INSERT Audit.StartStopEvents (EquipmentID, StartOrStop)   
    VALUES (72, 0) ;  
INSERT Audit.ProcessEvents (EventCode, Description)   
    VALUES (2735,   
    'Clean room temperature 18 degrees C.') ;  
INSERT Audit.ProcessEvents (EventCode, Description)   
    VALUES (18, 'Spin rate threashold exceeded.') ;  
INSERT Audit.ErrorEvents (EquipmentID, ErrorNumber, EventDesc)   
    VALUES (248, 82, 'Feeder jam') ;  
INSERT Audit.StartStopEvents (EquipmentID, StartOrStop)   
    VALUES (248, 1) ;  
INSERT Audit.ProcessEvents (EventCode, Description)   
    VALUES (1841, 'Central feed in bypass mode.') ;  
-- The following statement combines all events, though not all fields.  
SELECT EventID, EventTime, Description FROM Audit.ProcessEvents   
UNION SELECT EventID, EventTime, EventDesc FROM Audit.ErrorEvents   
UNION SELECT EventID, EventTime,   
CASE StartOrStop   
    WHEN 0 THEN 'Start'   
    ELSE 'Stop'  
END   
FROM Audit.StartStopEvents  
ORDER BY EventID ;  
GO  
  
```  
  
 [!INCLUDE[ssResult](../../../includes/ssresult-md.md)]  
  
 `EventID  EventTime                Description`  
  
 `1        2009-11-02 15:00:51.157  Start`  
  
 `2        2009-11-02 15:00:51.160  Start`  
  
 `3        2009-11-02 15:00:51.167  Clean room temperature 18 degrees C.`  
  
 `4        2009-11-02 15:00:51.167  Spin rate threshold exceeded.`  
  
 `5        2009-11-02 15:00:51.173  Feeder jam`  
  
 `6        2009-11-02 15:00:51.177  Stop`  
  
 `7        2009-11-02 15:00:51.180  Central feed in bypass mode.`  
  
### <a name="d-generating-repeating-sequence-numbers-in-a-result-set"></a><span data-ttu-id="495ab-168">D.</span><span class="sxs-lookup"><span data-stu-id="495ab-168">D.</span></span> <span data-ttu-id="495ab-169">在结果集中生成重复序列号</span><span class="sxs-lookup"><span data-stu-id="495ab-169">Generating repeating sequence numbers in a result set</span></span>  
 <span data-ttu-id="495ab-170">下面的示例演示序列号的两个功能：循环以及在 select 语句中使用 `NEXT VALUE FOR` 。</span><span class="sxs-lookup"><span data-stu-id="495ab-170">The following example demonstrates two features of sequence numbers: cycling, and using `NEXT VALUE FOR` in a select statement.</span></span>  
  
```  
CREATE SEQUENCE CountBy5  
   AS tinyint  
    START WITH 1  
    INCREMENT BY 1  
    MINVALUE 1  
    MAXVALUE 5  
    CYCLE ;  
GO  
  
SELECT NEXT VALUE FOR CountBy5 AS SurveyGroup, Name FROM sys.objects ;  
GO  
```  
  
### <a name="e-generating-sequence-numbers-for-a-result-set-by-using-the-over-clause"></a><span data-ttu-id="495ab-171">E.</span><span class="sxs-lookup"><span data-stu-id="495ab-171">E.</span></span> <span data-ttu-id="495ab-172">通过使用 OVER 子句为结果集生成序列号</span><span class="sxs-lookup"><span data-stu-id="495ab-172">Generating sequence numbers for a result set by using the OVER clause</span></span>  
 <span data-ttu-id="495ab-173">下面的示例使用 `OVER` 子句在其添加序列号列之前按 `Name` 对结果集进行排序。</span><span class="sxs-lookup"><span data-stu-id="495ab-173">The following example uses the `OVER` clause to sort the result set by `Name` before it adds the sequence number column.</span></span>  
  
```  
USE AdventureWorks2012 ;  
GO  
  
CREATE SCHEMA Samples ;  
GO  
  
CREATE SEQUENCE Samples.IDLabel  
    AS tinyint  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
  
SELECT NEXT VALUE FOR Samples.IDLabel OVER (ORDER BY Name) AS NutID, ProductID, Name, ProductNumber FROM Production.Product  
WHERE Name LIKE '%nut%' ;  
```  
  
### <a name="f-resetting-the-sequence-number"></a><span data-ttu-id="495ab-174">F.</span><span class="sxs-lookup"><span data-stu-id="495ab-174">F.</span></span> <span data-ttu-id="495ab-175">重置序列号</span><span class="sxs-lookup"><span data-stu-id="495ab-175">Resetting the sequence number</span></span>  
 <span data-ttu-id="495ab-176">示例 E 使用了前 79 个 `Samples.IDLabel` 序列号。</span><span class="sxs-lookup"><span data-stu-id="495ab-176">Example E consumed the first 79 of the `Samples.IDLabel` sequence numbers.</span></span> <span data-ttu-id="495ab-177">（您的版本的 `AdventureWorks2012` 可能会返回不同数目的结果。）执行以下语句以便使用接下来的 79 个序列号（80 到 158）。</span><span class="sxs-lookup"><span data-stu-id="495ab-177">(Your version of `AdventureWorks2012` may return a different number of results.) Execute the following to consume the next 79 sequence numbers (80 though 158).</span></span>  
  
```  
SELECT NEXT VALUE FOR Samples.IDLabel OVER (ORDER BY Name) AS NutID, ProductID, Name, ProductNumber FROM Production.Product  
WHERE Name LIKE '%nut%' ;  
```  
  
 <span data-ttu-id="495ab-178">执行以下语句以便重新开始 `Samples.IDLabel` 序列。</span><span class="sxs-lookup"><span data-stu-id="495ab-178">Execute the following statement to restart the `Samples.IDLabel` sequence.</span></span>  
  
```  
ALTER SEQUENCE Samples.IDLabel  
RESTART WITH 1 ;  
```  
  
 <span data-ttu-id="495ab-179">再次执行 select 语句以便确认 `Samples.IDLabel` 序列以数字 1 开头。</span><span class="sxs-lookup"><span data-stu-id="495ab-179">Execute the select statement again to verify that the `Samples.IDLabel` sequence restarted with number 1.</span></span>  
  
```  
SELECT NEXT VALUE FOR Samples.IDLabel OVER (ORDER BY Name) AS NutID, ProductID, Name, ProductNumber FROM Production.Product  
WHERE Name LIKE '%nut%' ;  
```  
  
### <a name="g-changing-a-table-from-identity-to-sequence"></a><span data-ttu-id="495ab-180">G.</span><span class="sxs-lookup"><span data-stu-id="495ab-180">G.</span></span> <span data-ttu-id="495ab-181">将表从标识更改为序列</span><span class="sxs-lookup"><span data-stu-id="495ab-181">Changing a table from identity to sequence</span></span>  
 <span data-ttu-id="495ab-182">下面的示例创建一个包含该示例的三行的架构和表。</span><span class="sxs-lookup"><span data-stu-id="495ab-182">The following example creates a schema and table containing three rows for the example.</span></span> <span data-ttu-id="495ab-183">然后，该示例添加一个新列并且删除旧列。</span><span class="sxs-lookup"><span data-stu-id="495ab-183">Then the example adds a new column and drops the old column.</span></span>  
  
```  
-- Create a schema  
CREATE SCHEMA Test ;  
GO  
  
-- Create a table  
CREATE TABLE Test.Department  
    (  
        DepartmentID smallint IDENTITY(1,1) NOT NULL,  
        Name nvarchar(100) NOT NULL,  
        GroupName nvarchar(100) NOT NULL  
    CONSTRAINT PK_Department_DepartmentID PRIMARY KEY CLUSTERED   
         (DepartmentID ASC)   
    ) ;  
GO  
  
-- Insert three rows into the table  
INSERT Test.Department(Name, GroupName)  
    VALUES ('Engineering', 'Research and Development');  
GO  
  
INSERT Test.Department(Name, GroupName)  
    VALUES ('Tool Design', 'Research and Development');  
GO  
  
INSERT Test.Department(Name, GroupName)  
    VALUES ('Sales', 'Sales and Marketing');  
GO  
  
-- View the table that will be changed  
SELECT * FROM Test.Department ;  
GO  
  
-- End of portion creating a sample table  
--------------------------------------------------------  
-- Add the new column that does not have the IDENTITY property  
ALTER TABLE Test.Department   
    ADD DepartmentIDNew smallint NULL  
GO  
  
-- Copy values from the old column to the new column  
UPDATE Test.Department  
    SET DepartmentIDNew = DepartmentID ;  
GO  
  
-- Drop the primary key constraint on the old column  
ALTER TABLE Test.Department  
    DROP CONSTRAINT [PK_Department_DepartmentID];  
-- Drop the old column  
ALTER TABLE Test.Department  
    DROP COLUMN DepartmentID ;  
GO  
  
-- Rename the new column to the old columns name  
EXEC sp_rename 'Test.Department.DepartmentIDNew',   
    'DepartmentID', 'COLUMN';  
GO  
  
-- Change the new column to NOT NULL  
ALTER TABLE Test.Department  
    ALTER COLUMN DepartmentID smallint NOT NULL ;  
-- Add the unique primary key constraint  
ALTER TABLE Test.Department  
    ADD CONSTRAINT PK_Department_DepartmentID PRIMARY KEY CLUSTERED   
         (DepartmentID ASC) ;  
-- Get the highest current value from the DepartmentID column   
-- and create a sequence to use with the column. (Returns 3.)  
SELECT MAX(DepartmentID) FROM Test.Department ;  
-- Use the next desired value (4) as the START WITH VALUE;  
CREATE SEQUENCE Test.DeptSeq  
    AS smallint  
    START WITH 4  
    INCREMENT BY 1 ;  
GO  
  
-- Add a default value for the DepartmentID column  
ALTER TABLE Test.Department  
    ADD CONSTRAINT DefSequence DEFAULT (NEXT VALUE FOR Test.DeptSeq)   
        FOR DepartmentID;  
GO  
  
-- View the result  
SELECT DepartmentID, Name, GroupName  
FROM Test.Department ;   
-- Test insert  
INSERT Test.Department (Name, GroupName)  
    VALUES ('Audit', 'Quality Assurance') ;  
GO  
  
-- View the result  
SELECT DepartmentID, Name, GroupName  
FROM Test.Department ;  
GO  
  
```  
  
 <span data-ttu-id="495ab-184">使用 `SELECT *` 的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句将这个新列作为最后一列接收，而非作为第一列接收。</span><span class="sxs-lookup"><span data-stu-id="495ab-184">[!INCLUDE[tsql](../../../includes/tsql-md.md)] statements that use `SELECT *` will receive the new column as the last column instead of the first column.</span></span> <span data-ttu-id="495ab-185">如果这样做是不可接受的，则您必须创建全新的表，将数据移到该表中，然后针对这个新表重新创建权限。</span><span class="sxs-lookup"><span data-stu-id="495ab-185">If this is not acceptable, then you must create an entirely new table, move the data to it, and then recreate the permissions on the new table.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="495ab-186">相关内容</span><span class="sxs-lookup"><span data-stu-id="495ab-186">Related Content</span></span>  
 [<span data-ttu-id="495ab-187">CREATE SEQUENCE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="495ab-187">CREATE SEQUENCE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-sequence-transact-sql)  
  
 [<span data-ttu-id="495ab-188">ALTER SEQUENCE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="495ab-188">ALTER SEQUENCE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-sequence-transact-sql)  
  
 [<span data-ttu-id="495ab-189">DROP SEQUENCE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="495ab-189">DROP SEQUENCE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-sequence-transact-sql)  
  
 [<span data-ttu-id="495ab-190">IDENTITY（属性）(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="495ab-190">IDENTITY &#40;Property&#41; &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-table-transact-sql-identity-property)  
  
  
