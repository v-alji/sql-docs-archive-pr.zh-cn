---
title: 创建表（教程）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- creating tables
ms.assetid: 653f2dd3-36a2-4bd5-8703-71a57d244661
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c772f2527bd5ddb8a6759cbaa72d8aed9277f5cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588180"
---
# <a name="creating-a-table-tutorial"></a><span data-ttu-id="81c80-102">创建表（教程）</span><span class="sxs-lookup"><span data-stu-id="81c80-102">Creating a Table (Tutorial)</span></span>
  <span data-ttu-id="81c80-103">若要创建表，您必须提供该表的名称以及该表中每个列的名称和数据类型。</span><span class="sxs-lookup"><span data-stu-id="81c80-103">To create a table, you must provide a name for the table, and the names and data types of each column in the table.</span></span> <span data-ttu-id="81c80-104">指出每个列中是否允许空值，也是一种很好的做法。</span><span class="sxs-lookup"><span data-stu-id="81c80-104">It is also a good practice to indicate whether null values are allowed in each column.</span></span>  
  
 <span data-ttu-id="81c80-105">大多数表有一个主键，主键由表的一列或多列组成。</span><span class="sxs-lookup"><span data-stu-id="81c80-105">Most tables have a primary key, made up of one or more columns of the table.</span></span> <span data-ttu-id="81c80-106">主键始终是唯一的。</span><span class="sxs-lookup"><span data-stu-id="81c80-106">A primary key is always unique.</span></span> <span data-ttu-id="81c80-107">[!INCLUDE[ssDE](../includes/ssde-md.md)] 将强制实施以下限制：表中的任何主键值都不能重复。</span><span class="sxs-lookup"><span data-stu-id="81c80-107">The [!INCLUDE[ssDE](../includes/ssde-md.md)] will enforce the restriction that any primary key value cannot be repeated in the table.</span></span>  
  
 <span data-ttu-id="81c80-108">有关数据类型的列表以及每种数据类型的说明链接，请参阅[数据类型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="81c80-108">For a list of data types and links for a description of each, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="81c80-109">[!INCLUDE[ssDE](../includes/ssde-md.md)] 可安装为区分大小写或不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="81c80-109">The [!INCLUDE[ssDE](../includes/ssde-md.md)] can be installed as case sensitive or non-case sensitive.</span></span> <span data-ttu-id="81c80-110">如果 [!INCLUDE[ssDE](../includes/ssde-md.md)] 区分大小写进行安装，则对象名必须始终具有相同的大小写。</span><span class="sxs-lookup"><span data-stu-id="81c80-110">If the [!INCLUDE[ssDE](../includes/ssde-md.md)] is installed as case sensitive, object names must always have the same case.</span></span> <span data-ttu-id="81c80-111">例如，名为 OrderData 的表与名为 ORDERDATA 的表是不同的表。</span><span class="sxs-lookup"><span data-stu-id="81c80-111">For example, a table named OrderData is a different table from a table named ORDERDATA.</span></span> <span data-ttu-id="81c80-112">如果 [!INCLUDE[ssDE](../includes/ssde-md.md)] 按不区分大小写进行安装，则这两个表名被视为同一个表，而且该名称只能使用一次。</span><span class="sxs-lookup"><span data-stu-id="81c80-112">If the [!INCLUDE[ssDE](../includes/ssde-md.md)] is installed as non-case sensitive, those two table names are considered to be the same table, and that name can only be used one time.</span></span>  
  
### <a name="to-create-a-database-to-contain-the-new-table"></a><span data-ttu-id="81c80-113">创建数据库以包含新表</span><span class="sxs-lookup"><span data-stu-id="81c80-113">To create a database to contain the new table</span></span>  
  
-   <span data-ttu-id="81c80-114">将下面的代码输入到查询编辑器窗口中。</span><span class="sxs-lookup"><span data-stu-id="81c80-114">Enter the following code into a Query Editor window.</span></span>  
  
    ```  
    USE master;  
    GO  
  
    --Delete the TestData database if it exists.  
    IF EXISTS(SELECT * from sys.databases WHERE name='TestData')  
    BEGIN  
        DROP DATABASE TestData;  
    END  
  
    --Create a new database called TestData.  
    CREATE DATABASE TestData;  
    Press the F5 key to execute the code and create the database.  
    ```  
  
### <a name="switch-the-query-editor-connection-to-the-testdata-database"></a><span data-ttu-id="81c80-115">将查询编辑器连接切换到 TestData 数据库</span><span class="sxs-lookup"><span data-stu-id="81c80-115">Switch the Query Editor connection to the TestData database</span></span>  
  
-   <span data-ttu-id="81c80-116">在查询编辑器窗口中，键入以下代码，并执行它以更改与 `TestData` 数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="81c80-116">In a Query Editor window, type and execute the following code to change your connection to the `TestData` database.</span></span>  
  
    ```  
    USE TestData  
    GO  
    ```  
  
### <a name="to-create-a-table"></a><span data-ttu-id="81c80-117">创建表</span><span class="sxs-lookup"><span data-stu-id="81c80-117">To create a table</span></span>  
  
-   <span data-ttu-id="81c80-118">在查询编辑器窗口中，键入以下代码，并执行它以创建一个名为 `Products`的简单表。</span><span class="sxs-lookup"><span data-stu-id="81c80-118">In a Query Editor window, type and execute the following code to create a simple table named `Products`.</span></span> <span data-ttu-id="81c80-119">该表中各列的名称为 `ProductID`、 `ProductName`、 `Price`和 `ProductDescription`。</span><span class="sxs-lookup"><span data-stu-id="81c80-119">The columns in the table are named `ProductID`, `ProductName`, `Price`, and `ProductDescription`.</span></span> <span data-ttu-id="81c80-120">`ProductID` 列是表的主键。</span><span class="sxs-lookup"><span data-stu-id="81c80-120">The `ProductID` column is the primary key of the table.</span></span> <span data-ttu-id="81c80-121">`int``varchar(25)`、 `money`和 `text` 都是数据类型。</span><span class="sxs-lookup"><span data-stu-id="81c80-121">`int`, `varchar(25)`, `money`, and `text` are all data types.</span></span> <span data-ttu-id="81c80-122">当插入或更改行时，只有 `Price` 和 `ProductionDescription` 列可以不包含数据。</span><span class="sxs-lookup"><span data-stu-id="81c80-122">Only the `Price` and `ProductionDescription` columns can have no data when a row is inserted or changed.</span></span> <span data-ttu-id="81c80-123">此语句包含称为架构的可选元素 (`dbo.`)。</span><span class="sxs-lookup"><span data-stu-id="81c80-123">This statement contains an optional element (`dbo.`) called a schema.</span></span> <span data-ttu-id="81c80-124">架构是拥有表的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="81c80-124">The schema is the database object that owns the table.</span></span> <span data-ttu-id="81c80-125">如果您是管理员，则 `dbo` 是默认架构。</span><span class="sxs-lookup"><span data-stu-id="81c80-125">If you are an administrator, `dbo` is the default schema.</span></span> <span data-ttu-id="81c80-126">`dbo` 代表数据库所有者。</span><span class="sxs-lookup"><span data-stu-id="81c80-126">`dbo` stands for database owner.</span></span>  
  
    ```  
    CREATE TABLE dbo.Products  
       (ProductID int PRIMARY KEY NOT NULL,  
        ProductName varchar(25) NOT NULL,  
        Price money NULL,  
        ProductDescription text NULL)  
    GO  
    ```  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="81c80-127">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="81c80-127">Next Task in Lesson</span></span>  
 [<span data-ttu-id="81c80-128">插入和更新表中的数据（教程）</span><span class="sxs-lookup"><span data-stu-id="81c80-128">Inserting and Updating Data in a Table &#40;Tutorial&#41;</span></span>](../t-sql/lesson-1-3-inserting-and-updating-data-in-a-table.md)  
  
## <a name="see-also"></a><span data-ttu-id="81c80-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="81c80-129">See Also</span></span>  
 [<span data-ttu-id="81c80-130">CREATE TABLE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="81c80-130">CREATE TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-table-transact-sql)  
  
  
