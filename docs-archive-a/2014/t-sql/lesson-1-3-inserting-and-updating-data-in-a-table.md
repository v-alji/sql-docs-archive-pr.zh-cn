---
title: 插入和更新表中的数据（教程）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- inserting and updating data
ms.assetid: 514dc87a-b829-43b5-8fc8-1a400a260284
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0646019f166e1c2cc126a4cc7d2ed8f27a7bd2f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588176"
---
# <a name="inserting-and-updating-data-in-a-table-tutorial"></a><span data-ttu-id="11373-102">插入和更新表中的数据（教程）</span><span class="sxs-lookup"><span data-stu-id="11373-102">Inserting and Updating Data in a Table (Tutorial)</span></span>
  <span data-ttu-id="11373-103">现在已经创建了 **Products** 表，可以通过使用 INSERT 语句将数据插入到表中。</span><span class="sxs-lookup"><span data-stu-id="11373-103">Now that you have created the **Products** table, you are ready to insert data into the table by using the INSERT statement.</span></span> <span data-ttu-id="11373-104">插入数据后，将通过使用 UPDATE 语句更改行的内容。</span><span class="sxs-lookup"><span data-stu-id="11373-104">After the data is inserted, you will change the content of a row by using an UPDATE statement.</span></span> <span data-ttu-id="11373-105">您将使用 UPDATE 语句的 WHERE 子句，以限制对单个行的更新。</span><span class="sxs-lookup"><span data-stu-id="11373-105">You will use the WHERE clause of the UPDATE statement to restrict the update to a single row.</span></span> <span data-ttu-id="11373-106">这四条语句将输入以下数据。</span><span class="sxs-lookup"><span data-stu-id="11373-106">The four statements will enter the following data.</span></span>  
  
|<span data-ttu-id="11373-107">ProductID</span><span class="sxs-lookup"><span data-stu-id="11373-107">ProductID</span></span>|<span data-ttu-id="11373-108">ProductName</span><span class="sxs-lookup"><span data-stu-id="11373-108">ProductName</span></span>|<span data-ttu-id="11373-109">价格</span><span class="sxs-lookup"><span data-stu-id="11373-109">Price</span></span>|<span data-ttu-id="11373-110">ProductDescription</span><span class="sxs-lookup"><span data-stu-id="11373-110">ProductDescription</span></span>|  
|---------------|-----------------|-----------|------------------------|  
|<span data-ttu-id="11373-111">1</span><span class="sxs-lookup"><span data-stu-id="11373-111">1</span></span>|<span data-ttu-id="11373-112">Clamp</span><span class="sxs-lookup"><span data-stu-id="11373-112">Clamp</span></span>|<span data-ttu-id="11373-113">12.48</span><span class="sxs-lookup"><span data-stu-id="11373-113">12.48</span></span>|<span data-ttu-id="11373-114">Workbench clamp</span><span class="sxs-lookup"><span data-stu-id="11373-114">Workbench clamp</span></span>|  
|<span data-ttu-id="11373-115">50</span><span class="sxs-lookup"><span data-stu-id="11373-115">50</span></span>|<span data-ttu-id="11373-116">Screwdriver</span><span class="sxs-lookup"><span data-stu-id="11373-116">Screwdriver</span></span>|<span data-ttu-id="11373-117">3.17</span><span class="sxs-lookup"><span data-stu-id="11373-117">3.17</span></span>|<span data-ttu-id="11373-118">Flat head</span><span class="sxs-lookup"><span data-stu-id="11373-118">Flat head</span></span>|  
|<span data-ttu-id="11373-119">75</span><span class="sxs-lookup"><span data-stu-id="11373-119">75</span></span>|<span data-ttu-id="11373-120">Tire Bar</span><span class="sxs-lookup"><span data-stu-id="11373-120">Tire Bar</span></span>||<span data-ttu-id="11373-121">Tool for changing tires.</span><span class="sxs-lookup"><span data-stu-id="11373-121">Tool for changing tires.</span></span>|  
|<span data-ttu-id="11373-122">3000</span><span class="sxs-lookup"><span data-stu-id="11373-122">3000</span></span>|<span data-ttu-id="11373-123">3mm Bracket</span><span class="sxs-lookup"><span data-stu-id="11373-123">3mm Bracket</span></span>|<span data-ttu-id="11373-124">.52</span><span class="sxs-lookup"><span data-stu-id="11373-124">.52</span></span>||  
  
 <span data-ttu-id="11373-125">基本语法如下：INSERT、表名、列的列表、VALUES，然后是要插入的值的列表。</span><span class="sxs-lookup"><span data-stu-id="11373-125">The basic syntax is: INSERT, table name, column list, VALUES, and then a list of the values to be inserted.</span></span> <span data-ttu-id="11373-126">如果某行的前面有两个连字符，则指示该行为注释，编译器将忽略其文本。</span><span class="sxs-lookup"><span data-stu-id="11373-126">The two hyphens in front of a line indicate that the line is a comment and the text will be ignored by the compiler.</span></span> <span data-ttu-id="11373-127">在这种情况下，注释说明允许的语法变体。</span><span class="sxs-lookup"><span data-stu-id="11373-127">In this case, the comment describes a permissible variation of the syntax.</span></span>  
  
### <a name="to-insert-data-into-a-table"></a><span data-ttu-id="11373-128">将数据插入到表</span><span class="sxs-lookup"><span data-stu-id="11373-128">To insert data into a table</span></span>  
  
1.  <span data-ttu-id="11373-129">执行以下语句，将一行插入到在上一个任务中创建的 `Products` 表中。</span><span class="sxs-lookup"><span data-stu-id="11373-129">Execute the following statement to insert a row into the `Products` table that was created in the previous task.</span></span> <span data-ttu-id="11373-130">基本语法如下：</span><span class="sxs-lookup"><span data-stu-id="11373-130">This is the basic syntax.</span></span>  
  
    ```  
    -- Standard syntax  
    INSERT dbo.Products (ProductID, ProductName, Price, ProductDescription)  
        VALUES (1, 'Clamp', 12.48, 'Workbench clamp')  
    GO  
  
    ```  
  
2.  <span data-ttu-id="11373-131">以下语句显示如何通过在字段列表（在圆括号中）中和值列表中均切换 `ProductID` 和 `ProductName` 的位置，更改提供参数的顺序。</span><span class="sxs-lookup"><span data-stu-id="11373-131">The following statement shows how you can change the order in which the parameters are provided by switching the placement of the `ProductID` and `ProductName` in both the field list (in parentheses) and in the values list.</span></span>  
  
    ```  
    -- Changing the order of the columns  
    INSERT dbo.Products (ProductName, ProductID, Price, ProductDescription)  
        VALUES ('Screwdriver', 50, 3.17, 'Flat head')  
    GO  
  
    ```  
  
3.  <span data-ttu-id="11373-132">以下语句演示，只要值是按正确顺序列出的，列的名称就是可选的。</span><span class="sxs-lookup"><span data-stu-id="11373-132">The following statement demonstrates that the names of the columns are optional, as long as the values are listed in the correct order.</span></span> <span data-ttu-id="11373-133">此语法很常见，但是建议不要使用它，因为其他人了解您的代码可能会更困难。</span><span class="sxs-lookup"><span data-stu-id="11373-133">This syntax is common but is not recommended because it might be harder for others to understand your code.</span></span> <span data-ttu-id="11373-134">`NULL` 为 `Price` 列指定，因为还不知道此产品的价格。</span><span class="sxs-lookup"><span data-stu-id="11373-134">`NULL` is specified for the `Price` column because the price for this product is not yet known.</span></span>  
  
    ```  
    -- Skipping the column list, but keeping the values in order  
    INSERT dbo.Products  
        VALUES (75, 'Tire Bar', NULL, 'Tool for changing tires.')  
    GO  
  
    ```  
  
4.  <span data-ttu-id="11373-135">只要在默认架构中访问和更改表，架构名称就是可选的。</span><span class="sxs-lookup"><span data-stu-id="11373-135">The schema name is optional as long as you are accessing and changing a table in your default schema.</span></span> <span data-ttu-id="11373-136">由于 `ProductDescription` 列允许 Null 值，而且没有提供值，因此可以从语句中完全删除 `ProductDescription` 列的名称和值。</span><span class="sxs-lookup"><span data-stu-id="11373-136">Because the `ProductDescription` column allows null values and no value is being provided, the `ProductDescription` column name and value can be dropped from the statement completely.</span></span>  
  
    ```  
    -- Dropping the optional dbo and dropping the ProductDescription column  
    INSERT Products (ProductID, ProductName, Price)  
        VALUES (3000, '3mm Bracket', .52)  
    GO  
    ```  
  
### <a name="to-update-the-products-table"></a><span data-ttu-id="11373-137">更新 products 表</span><span class="sxs-lookup"><span data-stu-id="11373-137">To update the products table</span></span>  
  
1.  <span data-ttu-id="11373-138">键入并执行以下 `UPDATE` 语句，将第二种产品的 `ProductName` 从 `Screwdriver`更改为 `Flat Head Screwdriver`。</span><span class="sxs-lookup"><span data-stu-id="11373-138">Type and execute the following `UPDATE` statement to change the `ProductName` of the second product from `Screwdriver`, to `Flat Head Screwdriver`.</span></span>  
  
    ```  
    UPDATE dbo.Products  
        SET ProductName = 'Flat Head Screwdriver'  
        WHERE ProductID = 50  
    GO  
    ```  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="11373-139">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="11373-139">Next Task in Lesson</span></span>  
 [<span data-ttu-id="11373-140">读取表中的数据（教程）</span><span class="sxs-lookup"><span data-stu-id="11373-140">Reading the Data in a Table &#40;Tutorial&#41;</span></span>](lesson-1-4-reading-the-data-in-a-table.md)  
  
## <a name="see-also"></a><span data-ttu-id="11373-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="11373-141">See Also</span></span>  
 <span data-ttu-id="11373-142">[INSERT (Transact-SQL)](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="11373-142">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 [<span data-ttu-id="11373-143">UPDATE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="11373-143">UPDATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/update-transact-sql)  
  
  
