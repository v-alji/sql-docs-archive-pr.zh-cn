---
title: 创建视图和存储过程 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- creating views and stored procedures
ms.assetid: 53a0426d-07d8-4b7c-aa21-22632753bad8
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 76f6ecec446536191e8be4b05547ba5fd44c9d8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682575"
---
# <a name="creating-views-and-stored-procedures"></a><span data-ttu-id="51bd9-102">创建视图和存储过程</span><span class="sxs-lookup"><span data-stu-id="51bd9-102">Creating Views and Stored Procedures</span></span>
  <span data-ttu-id="51bd9-103">既然 Mary 可以访问 **TestData** 数据库，你可能希望创建一些数据库对象（如视图和存储过程），再将它们的访问权限授予 Mary。</span><span class="sxs-lookup"><span data-stu-id="51bd9-103">Now that Mary can access the **TestData** database, you may want to create some database objects, such as a view and a stored procedure, and then grant Mary access to them.</span></span> <span data-ttu-id="51bd9-104">视图是存储的 SELECT 语句，而存储过程是以批处理方式执行的一条或多条 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="51bd9-104">A view is a stored SELECT statement, and a stored procedure is one or more [!INCLUDE[tsql](../includes/tsql-md.md)] statements that execute as a batch.</span></span>  
  
 <span data-ttu-id="51bd9-105">视图像表那样进行查询，但不接受参数。</span><span class="sxs-lookup"><span data-stu-id="51bd9-105">Views are queried like tables and do not accept parameters.</span></span> <span data-ttu-id="51bd9-106">存储过程比视图更复杂。</span><span class="sxs-lookup"><span data-stu-id="51bd9-106">Stored procedures are more complex than views.</span></span> <span data-ttu-id="51bd9-107">存储过程可以同时具有输入参数和输出参数，并可以包括控制代码流的语句，如 IF 和 WHILE 语句。</span><span class="sxs-lookup"><span data-stu-id="51bd9-107">Stored procedures can have both input and output parameters and can contain statements to control the flow of the code, such as IF and WHILE statements.</span></span> <span data-ttu-id="51bd9-108">将存储过程用于数据库中的所有重复操作，是一个良好的编程做法。</span><span class="sxs-lookup"><span data-stu-id="51bd9-108">It is good programming practice to use stored procedures for all repetitive actions in the database.</span></span>  
  
 <span data-ttu-id="51bd9-109">在此示例中，你将使用 CREATE VIEW 创建一个视图，该视图仅选择 **Products** 表中的两列。</span><span class="sxs-lookup"><span data-stu-id="51bd9-109">For this example, you will use CREATE VIEW to create a view that selects only two of the columns in the **Products** table.</span></span> <span data-ttu-id="51bd9-110">然后，您将使用 CREATE PROCEDURE 创建一个存储过程，该存储过程接受价格参数，并仅返回价格小于指定参数值的那些产品。</span><span class="sxs-lookup"><span data-stu-id="51bd9-110">Then, you will use CREATE PROCEDURE to create a stored procedure that accepts a price parameter and returns only those products that cost less than the specified parameter value.</span></span>  
  
### <a name="to-create-a-view"></a><span data-ttu-id="51bd9-111">创建视图</span><span class="sxs-lookup"><span data-stu-id="51bd9-111">To create a view</span></span>  
  
1.  <span data-ttu-id="51bd9-112">执行以下语句创建一个非常简单的视图，该视图执行 Select 语句，并将产品的名称和价格返回给用户。</span><span class="sxs-lookup"><span data-stu-id="51bd9-112">Execute the following statement to create a very simple view that executes a select statement, and returns the names and prices of our products to the user.</span></span>  
  
    ```  
    CREATE VIEW vw_Names  
       AS  
       SELECT ProductName, Price FROM Products;  
    GO  
  
    ```  
  
### <a name="test-the-view"></a><span data-ttu-id="51bd9-113">测试视图</span><span class="sxs-lookup"><span data-stu-id="51bd9-113">Test the view</span></span>  
  
1.  <span data-ttu-id="51bd9-114">视图的处理方式与表类似。</span><span class="sxs-lookup"><span data-stu-id="51bd9-114">Views are treated just like tables.</span></span> <span data-ttu-id="51bd9-115">使用 `SELECT` 语句访问视图。</span><span class="sxs-lookup"><span data-stu-id="51bd9-115">Use a `SELECT` statement to access a view.</span></span>  
  
    ```  
    SELECT * FROM vw_Names;  
    GO  
  
    ```  
  
### <a name="to-create-a-stored-procedure"></a><span data-ttu-id="51bd9-116">创建存储过程</span><span class="sxs-lookup"><span data-stu-id="51bd9-116">To create a stored procedure</span></span>  
  
1.  <span data-ttu-id="51bd9-117">以下语句创建一个名为 `pr_Names`的存储过程，接受名为 `@VarPrice` 、数据类型为 `money`的输入参数。</span><span class="sxs-lookup"><span data-stu-id="51bd9-117">The following statement creates a stored procedure name `pr_Names`, accepts an input parameter named `@VarPrice` of data type `money`.</span></span> <span data-ttu-id="51bd9-118">该存储过程打印与输入参数（已从 `Products less than` 数据类型更改为 `money` 字符数据类型）串联的语句 `varchar(10)` 。</span><span class="sxs-lookup"><span data-stu-id="51bd9-118">The stored procedure prints the statement `Products less than` concatenated with the input parameter that is changed from the `money` data type into a `varchar(10)` character data type.</span></span> <span data-ttu-id="51bd9-119">然后，该存储过程对视图执行 `SELECT` 语句，将输入参数作为 `WHERE` 子句的一部分进行传递。</span><span class="sxs-lookup"><span data-stu-id="51bd9-119">Then, the procedure executes a `SELECT` statement on the view, passing the input parameter as part of the `WHERE` clause.</span></span> <span data-ttu-id="51bd9-120">这将返回价格小于输入参数值的所有产品。</span><span class="sxs-lookup"><span data-stu-id="51bd9-120">This returns all products that cost less than the input parameter value.</span></span>  
  
    ```  
    CREATE PROCEDURE pr_Names @VarPrice money  
       AS  
       BEGIN  
          -- The print statement returns text to the user  
          PRINT 'Products less than ' + CAST(@VarPrice AS varchar(10));  
          -- A second statement starts here  
          SELECT ProductName, Price FROM vw_Names  
                WHERE Price < @varPrice;  
       END  
    GO  
  
    ```  
  
### <a name="test-the-stored-procedure"></a><span data-ttu-id="51bd9-121">测试存储过程</span><span class="sxs-lookup"><span data-stu-id="51bd9-121">Test the stored procedure</span></span>  
  
1.  <span data-ttu-id="51bd9-122">若要测试存储过程，请键入并执行以下语句。</span><span class="sxs-lookup"><span data-stu-id="51bd9-122">To test the stored procedure, type and execute the following statement.</span></span> <span data-ttu-id="51bd9-123">存储过程应该返回在第 1 课中向 `Products` 表中输入的、其价格小于 `10.00`的两个产品的名称。</span><span class="sxs-lookup"><span data-stu-id="51bd9-123">The procedure should return the names of the two products entered into the `Products` table in Lesson 1 with a price that is less than `10.00`.</span></span>  
  
    ```  
    EXECUTE pr_Names 10.00;  
    GO  
  
    ```  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="51bd9-124">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="51bd9-124">Next Task in Lesson</span></span>  
 [<span data-ttu-id="51bd9-125">授予访问数据库对象的权限</span><span class="sxs-lookup"><span data-stu-id="51bd9-125">Granting Access to a Database Object</span></span>](lesson-2-4-granting-access-to-a-database-object.md)  
  
## <a name="see-also"></a><span data-ttu-id="51bd9-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="51bd9-126">See Also</span></span>  
 <span data-ttu-id="51bd9-127">[CREATE VIEW (Transact-SQL)](/sql/t-sql/statements/create-view-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="51bd9-127">[CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) </span></span>  
 [<span data-ttu-id="51bd9-128">CREATE PROCEDURE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="51bd9-128">CREATE PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-procedure-transact-sql)  
  
  
