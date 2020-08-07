---
title: 读取表中的数据（教程）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- reading data in a table
ms.assetid: 532232c9-3d41-45cd-9150-de67a1cbfcf5
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4bdaaeeddf8f35792c536624abfe6ff11b2dbd2e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588177"
---
# <a name="reading-the-data-in-a-table-tutorial"></a><span data-ttu-id="27858-102">读取表中的数据（教程）</span><span class="sxs-lookup"><span data-stu-id="27858-102">Reading the Data in a Table (Tutorial)</span></span>
  <span data-ttu-id="27858-103">使用 SELECT 语句可以读取表中的数据。</span><span class="sxs-lookup"><span data-stu-id="27858-103">Use the SELECT statement to read the data in a table.</span></span> <span data-ttu-id="27858-104">SELECT 语句是最重要的 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句之一，其语法有许多变体。</span><span class="sxs-lookup"><span data-stu-id="27858-104">The SELECT statement is one of the most important [!INCLUDE[tsql](../includes/tsql-md.md)] statements, and there are many variations in the syntax.</span></span> <span data-ttu-id="27858-105">在本教程中，您将使用五个简单版本。</span><span class="sxs-lookup"><span data-stu-id="27858-105">For this tutorial, you will work with five simple versions.</span></span>  
  
### <a name="to-read-the-data-in-a-table"></a><span data-ttu-id="27858-106">读取表中的数据</span><span class="sxs-lookup"><span data-stu-id="27858-106">To read the data in a table</span></span>  
  
1.  <span data-ttu-id="27858-107">键入并执行以下语句以读取 `Products` 表中的数据。</span><span class="sxs-lookup"><span data-stu-id="27858-107">Type and execute the following statements to read the data in the `Products` table.</span></span>  
  
    ```  
    -- The basic syntax for reading data from a single table  
    SELECT ProductID, ProductName, Price, ProductDescription  
        FROM dbo.Products  
    GO  
  
    ```  
  
2.  <span data-ttu-id="27858-108">您可以使用星号选择表中的所有列。</span><span class="sxs-lookup"><span data-stu-id="27858-108">You can use an asterisk to select all the columns in the table.</span></span> <span data-ttu-id="27858-109">这通常用于即席查询中。</span><span class="sxs-lookup"><span data-stu-id="27858-109">This is often used in ad hoc queries.</span></span> <span data-ttu-id="27858-110">您应该在永久代码中提供列的列表，以便语句将返回预测列，即使稍后将新列添加到表中也是如此。</span><span class="sxs-lookup"><span data-stu-id="27858-110">You should provide the column list in you permanent code so that the statement will return the predicted columns, even if a new column is added to the table later.</span></span>  
  
    ```  
    -- Returns all columns in the table  
    -- Does not use the optional schema, dbo  
    SELECT * FROM Products  
    GO  
  
    ```  
  
3.  <span data-ttu-id="27858-111">可以省略不希望返回的列。</span><span class="sxs-lookup"><span data-stu-id="27858-111">You can omit columns that you do not want to return.</span></span> <span data-ttu-id="27858-112">列将按列出它们的顺序返回。</span><span class="sxs-lookup"><span data-stu-id="27858-112">The columns will be returned in the order that they are listed.</span></span>  
  
    ```  
    -- Returns only two of the columns from the table  
    SELECT ProductName, Price  
        FROM dbo.Products  
    GO  
  
    ```  
  
4.  <span data-ttu-id="27858-113">使用 `WHERE` 子句可以限制返回给用户的行。</span><span class="sxs-lookup"><span data-stu-id="27858-113">Use a `WHERE` clause to limit the rows that are returned to the user.</span></span>  
  
    ```  
    -- Returns only two of the records in the table  
    SELECT ProductID, ProductName, Price, ProductDescription  
        FROM dbo.Products  
        WHERE ProductID < 60  
    GO  
  
    ```  
  
5.  <span data-ttu-id="27858-114">您可以在返回列中的值时使用它们。</span><span class="sxs-lookup"><span data-stu-id="27858-114">You can work with the values in the columns as they are returned.</span></span> <span data-ttu-id="27858-115">以下示例对 `Price` 列执行数学运算。</span><span class="sxs-lookup"><span data-stu-id="27858-115">The following example performs a mathematical operation on the `Price` column.</span></span> <span data-ttu-id="27858-116">除非通过使用 `AS` 关键字提供一个名称，否则以此方式更改的列将没有名称。</span><span class="sxs-lookup"><span data-stu-id="27858-116">Columns that have been changed in this way will not have a name unless you provide one by using the `AS` keyword.</span></span>  
  
    ```  
    -- Returns ProductName and the Price including a 7% tax  
    -- Provides the name CustomerPays for the calculated column  
    SELECT ProductName, Price * 1.07 AS CustomerPays  
        FROM dbo.Products  
    GO  
    ```  
  
## <a name="functions-that-are-useful-in-a-select-statement"></a><span data-ttu-id="27858-117">SELECT 语句中的有用函数</span><span class="sxs-lookup"><span data-stu-id="27858-117">Functions That Are Useful in a SELECT Statement</span></span>  
 <span data-ttu-id="27858-118">有关可以在 SELECT 语句中用来处理数据的一些函数的信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="27858-118">For information about some functions that you can use to work with data in SELECT statements, see the following topics:</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="27858-119">字符串函数 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="27858-119">String Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/string-functions-transact-sql)|[<span data-ttu-id="27858-120">日期和时间数据类型及函数 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="27858-120">Date and Time Data Types and Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|  
|[<span data-ttu-id="27858-121">数学函数 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="27858-121">Mathematical Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/mathematical-functions-transact-sql)|[<span data-ttu-id="27858-122">文本与图像函数 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="27858-122">Text and Image Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/text-and-image-functions-textptr-transact-sql)|  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="27858-123">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="27858-123">Next Task in Lesson</span></span>  
 [<span data-ttu-id="27858-124">摘要：创建数据库对象</span><span class="sxs-lookup"><span data-stu-id="27858-124">Summary: Creating Database Objects</span></span>](lesson-1-5-summary-creating-database-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="27858-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27858-125">See Also</span></span>  
 [<span data-ttu-id="27858-126">SELECT (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="27858-126">SELECT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/select-transact-sql)  
  
  
