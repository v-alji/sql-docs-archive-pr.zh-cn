---
title: 指定表中的计算列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- computed columns, define
ms.assetid: 731a4576-09c1-47f0-a8f6-edd0b55679f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 22e4df8d67b61e50383ffd8e33f982990ff3f2ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589454"
---
# <a name="specify-computed-columns-in-a-table"></a><span data-ttu-id="4ca10-102">指定表中的计算列</span><span class="sxs-lookup"><span data-stu-id="4ca10-102">Specify Computed Columns in a Table</span></span>
  <span data-ttu-id="4ca10-103">计算列是虚拟列，并非实际存储在表中，除非此列标记为 PERSISTED。</span><span class="sxs-lookup"><span data-stu-id="4ca10-103">A computed column is a virtual column that is not physically stored in the table, unless the column is marked PERSISTED.</span></span> <span data-ttu-id="4ca10-104">计算列的表达式可以使用其他列中的数据来计算其所属列的值。</span><span class="sxs-lookup"><span data-stu-id="4ca10-104">A computed column expression can use data from other columns to calculate a value for the column to which it belongs.</span></span> <span data-ttu-id="4ca10-105">可以通过使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中为计算列指定一个表达式。</span><span class="sxs-lookup"><span data-stu-id="4ca10-105">You can specify an expression for a computed column in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="4ca10-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="4ca10-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4ca10-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="4ca10-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4ca10-108">限制和局限</span><span class="sxs-lookup"><span data-stu-id="4ca10-108">Limitations and Restrictions</span></span>](#Limitations)  
  
     [<span data-ttu-id="4ca10-109">安全性</span><span class="sxs-lookup"><span data-stu-id="4ca10-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4ca10-110">**使用以下工具指定计算列：**</span><span class="sxs-lookup"><span data-stu-id="4ca10-110">**To specify a computed column, using:**</span></span>  
  
     [<span data-ttu-id="4ca10-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4ca10-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4ca10-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4ca10-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4ca10-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="4ca10-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Limitations"></a> <span data-ttu-id="4ca10-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="4ca10-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="4ca10-115">计算列不能用作 DEFAULT 或 FOREIGN KEY 约束定义，也不能与 NOT NULL 约束定义一起使用。</span><span class="sxs-lookup"><span data-stu-id="4ca10-115">A computed column cannot be used as a DEFAULT or FOREIGN KEY constraint definition or with a NOT NULL constraint definition.</span></span> <span data-ttu-id="4ca10-116">但是，如果计算列值由具有确定性的表达式定义，并且索引列中允许使用计算结果的数据类型，则可将该列用作索引中的键列，或用作 PRIMARY KEY 或 UNIQUE 约束的一部分。</span><span class="sxs-lookup"><span data-stu-id="4ca10-116">However, if the computed column value is defined by a deterministic expression and the data type of the result is allowed in index columns, a computed column can be used as a key column in an index or as part of any PRIMARY KEY or UNIQUE constraint.</span></span> <span data-ttu-id="4ca10-117">例如，如果表中包含整数列 a 和 b，则可以对计算列 a + b 创建索引。但不能对计算列 a+DATEPART(dd, GETDATE()) 创建索引，因为在以后的调用中，其值可能发生更改。</span><span class="sxs-lookup"><span data-stu-id="4ca10-117">For example, if the table has integer columns a and b, the computed column a + b may be indexed, but computed column a + DATEPART(dd, GETDATE()) cannot be indexed, because the value might change in subsequent invocations.</span></span>  
  
-   <span data-ttu-id="4ca10-118">计算列不能作为 INSERT 或 UPDATE 语句的目标。</span><span class="sxs-lookup"><span data-stu-id="4ca10-118">A computed column cannot be the target of an INSERT or UPDATE statement.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4ca10-119">Security</span><span class="sxs-lookup"><span data-stu-id="4ca10-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4ca10-120">权限</span><span class="sxs-lookup"><span data-stu-id="4ca10-120">Permissions</span></span>  
 <span data-ttu-id="4ca10-121">需要对表的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="4ca10-121">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4ca10-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4ca10-122">Using SQL Server Management Studio</span></span>  
  
###  <a name="to-add-a-new-computed-column"></a><a name="NewColumn"></a> <span data-ttu-id="4ca10-123">添加新的计算列</span><span class="sxs-lookup"><span data-stu-id="4ca10-123">To add a new computed column</span></span>  
  
1.  <span data-ttu-id="4ca10-124">在 **“对象资源管理器”** 中，展开要添加新计算列的表。</span><span class="sxs-lookup"><span data-stu-id="4ca10-124">In **Object Explorer**, expand the table for which you want to add the new computed column.</span></span> <span data-ttu-id="4ca10-125">右键单击“列”  ，再选择“新建列”  。</span><span class="sxs-lookup"><span data-stu-id="4ca10-125">Right-click **Columns** and select **New Column**.</span></span>  
  
2.  <span data-ttu-id="4ca10-126">输入列名并接受默认数据类型 (`nchar`(10))。</span><span class="sxs-lookup"><span data-stu-id="4ca10-126">Enter the column name and accept the default data type (`nchar`(10)).</span></span> <span data-ttu-id="4ca10-127">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 通过将数据类型的优先顺序规则应用到在公式中指定的表达式，来确定计算列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="4ca10-127">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] determines the data type of the computed column by applying the rules of data type precedence to the expressions specified in the formula.</span></span> <span data-ttu-id="4ca10-128">例如，如果公式引用一个类型为 `money` 的列和一个类型为 `int` 的列，则计算列的类型将为 `money`，因为该数据类型具有较高优先顺序。</span><span class="sxs-lookup"><span data-stu-id="4ca10-128">For example, if the formula references a column of type `money` and a column of type `int`, the computed column will be of type `money` because that data type has the higher precedence.</span></span> <span data-ttu-id="4ca10-129">有关详细信息，请参阅[数据类型优先级 (Transact-SQL)](/sql/t-sql/data-types/data-type-precedence-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4ca10-129">For more information, see [Data Type Precedence &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-type-precedence-transact-sql).</span></span>  
  
3.  <span data-ttu-id="4ca10-130">在 **“列属性”** 选项卡中，展开 **“计算所得的列规范”** 属性。</span><span class="sxs-lookup"><span data-stu-id="4ca10-130">In the **Column Properties** tab, expand the **Computed Column Specification** property.</span></span>  
  
4.  <span data-ttu-id="4ca10-131">在“(公式)”  子属性中，在右侧的网格单元格中输入此列的表达式。</span><span class="sxs-lookup"><span data-stu-id="4ca10-131">In the **(Formula)** child property, enter the expression for this column in the grid cell to the right.</span></span> <span data-ttu-id="4ca10-132">例如，在 `SalesTotal` 列中，您输入的公式可能是 `SubTotal+TaxAmt+Freight`，它将该值加入到表中每行的这些列中。</span><span class="sxs-lookup"><span data-stu-id="4ca10-132">For example, in a `SalesTotal` column, the formula you enter might be `SubTotal+TaxAmt+Freight`, which adds the value in these columns for each row in the table.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="4ca10-133">当两个不同数据类型的表达式用公式组合后，数据类型优先级规则指定将优先级较低的数据类型转换为优先级较高的数据类型。</span><span class="sxs-lookup"><span data-stu-id="4ca10-133">When a formula combines two expressions of different data types, the rules for data type precedence specify that the data type with the lower precedence is converted to the data type with the higher precedence.</span></span> <span data-ttu-id="4ca10-134">如果此转换不是所支持的隐式转换，则返回错误“`Error validating the formula for column column_name.`”。</span><span class="sxs-lookup"><span data-stu-id="4ca10-134">If the conversion is not a supported implicit conversion, the error "`Error validating the formula for column column_name.`" is returned.</span></span> <span data-ttu-id="4ca10-135">使用 CAST 或 CONVERT 函数解决数据类型冲突。</span><span class="sxs-lookup"><span data-stu-id="4ca10-135">Use the CAST or CONVERT function to resolve the data type conflict.</span></span> <span data-ttu-id="4ca10-136">例如，如果类型为 `nvarchar` 的列与类型为 `int` 的列相结合，则整数类型必须转换为 `nvarchar`，如公式 `('Prod'+CONVERT(nvarchar(23),ProductID))` 中所示。</span><span class="sxs-lookup"><span data-stu-id="4ca10-136">For example, if a column of type `nvarchar` is combined with a column of type `int`, the integer type must be converted to `nvarchar` as shown in this formula `('Prod'+CONVERT(nvarchar(23),ProductID))`.</span></span> <span data-ttu-id="4ca10-137">有关详细信息，请参阅 [CAST 和 CONVERT (Transact-SQL)](/sql/t-sql/functions/cast-and-convert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4ca10-137">For more information, see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
5.  <span data-ttu-id="4ca10-138">从“持久化”子属性的下拉菜单上选择“是”或“否”，以指示该数据是否持久。</span><span class="sxs-lookup"><span data-stu-id="4ca10-138">Indicate whether the data is persisted by choosing **Yes** or **No** from the drop-down for the **Is Persisted** child property.</span></span>  
  
6.  <span data-ttu-id="4ca10-139">在“文件”菜单上，单击“保存表名称”\*\*\*\*\*\*\*\*__。</span><span class="sxs-lookup"><span data-stu-id="4ca10-139">On the **File** menu, click **Save**_table name_.</span></span>  
  
#### <a name="to-add-a-computed-column-definition-to-an-existing-column"></a><span data-ttu-id="4ca10-140">将计算列定义添加到现有列中</span><span class="sxs-lookup"><span data-stu-id="4ca10-140">To add a computed column definition to an existing column</span></span>  
  
1.  <span data-ttu-id="4ca10-141">在“对象资源管理器”  中，右键单击该表以及你要对其更改和展开“列”  文件夹的列。</span><span class="sxs-lookup"><span data-stu-id="4ca10-141">In **Object Explorer**, right-click the table with the column for which you want to change and expand the **Columns** folder.</span></span>  
  
2.  <span data-ttu-id="4ca10-142">右键单击你要为其指定计算列公式的列，然后单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="4ca10-142">Right-click the column for which you want to specify a computed column formula and click **Delete**.</span></span> <span data-ttu-id="4ca10-143">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="4ca10-143">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="4ca10-144">添加一个新列，然后按照前面的步骤添加新计算列以指定新计算列公式。</span><span class="sxs-lookup"><span data-stu-id="4ca10-144">Add a new column and specify the computed column formula by following the previous procedure to add a new computed column.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4ca10-145">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4ca10-145">Using Transact-SQL</span></span>  
  
#### <a name="to-add-a-computed-column-when-creating-a-table"></a><span data-ttu-id="4ca10-146">创建表时添加计算列</span><span class="sxs-lookup"><span data-stu-id="4ca10-146">To add a computed column when creating a table</span></span>  
  
1.  <span data-ttu-id="4ca10-147">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4ca10-147">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4ca10-148">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="4ca10-148">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4ca10-149">将以下示例复制并粘贴到查询窗口中，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="4ca10-149">Copy and paste the following example into the query window and then click **Execute**.</span></span> <span data-ttu-id="4ca10-150">此示例创建了一个表，其中具有一个计算列，该列将 `QtyAvailable` 列的值乘以 `UnitPrice` 列的值。</span><span class="sxs-lookup"><span data-stu-id="4ca10-150">The example creates a table with a computed column that multiplies the value in the `QtyAvailable` column times the value in the `UnitPrice` column.</span></span>  
  
    ```  
    CREATE TABLE dbo.Products   
    (  
        ProductID int IDENTITY (1,1) NOT NULL  
      , QtyAvailable smallint  
      , UnitPrice money  
      , InventoryValue AS QtyAvailable * UnitPrice  
    );  
  
    -- Insert values into the table.  
    INSERT INTO dbo.Products (QtyAvailable, UnitPrice)  
    VALUES (25, 2.00), (10, 1.5);  
  
    -- Display the rows in the table.  
    SELECT ProductID, QtyAvailable, UnitPrice, InventoryValue  
    FROM dbo.Products;  
  
    ```  
  
#### <a name="to-add-a-new-computed-column-to-an-existing-table"></a><span data-ttu-id="4ca10-151">将新计算列定义添加到现有表中</span><span class="sxs-lookup"><span data-stu-id="4ca10-151">To add a new computed column to an existing table</span></span>  
  
1.  <span data-ttu-id="4ca10-152">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4ca10-152">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4ca10-153">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="4ca10-153">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4ca10-154">将以下示例复制并粘贴到查询窗口中，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="4ca10-154">Copy and paste the following example into the query window and then click **Execute**.</span></span> <span data-ttu-id="4ca10-155">以下示例向在前一个示例中创建的表添加一个新列。</span><span class="sxs-lookup"><span data-stu-id="4ca10-155">The following example adds a new column to the table created in the previous example.</span></span>  
  
    ```  
    ALTER TABLE dbo.Products ADD RetailValue AS (QtyAvailable * UnitPrice * 1.35);  
  
    ```  
  
#### <a name="to-change-an-existing-column-to-a-computed-column"></a><span data-ttu-id="4ca10-156">将现有列更改为计算列</span><span class="sxs-lookup"><span data-stu-id="4ca10-156">To change an existing column to a computed column</span></span>  
  
1.  <span data-ttu-id="4ca10-157">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4ca10-157">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4ca10-158">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="4ca10-158">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4ca10-159">若要将现有列更改为计算列，您必须删除后重新创建该计算列。</span><span class="sxs-lookup"><span data-stu-id="4ca10-159">To change an existing column to a computed column you must drop and re-create the computed column.</span></span> <span data-ttu-id="4ca10-160">将以下示例复制并粘贴到查询窗口中，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="4ca10-160">Copy and paste the following example into the query window and then click **Execute**.</span></span> <span data-ttu-id="4ca10-161">以下示例修改在前一个示例中添加的列。</span><span class="sxs-lookup"><span data-stu-id="4ca10-161">The following example modifies the column added in the previous example.</span></span>  
  
    ```  
    ALTER TABLE dbo.Products DROP COLUMN RetailValue;  
    GO  
    ALTER TABLE dbo.Products ADD RetailValue AS (QtyAvailable * UnitPrice * 1.5);  
  
    ```  
  
     <span data-ttu-id="4ca10-162">有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4ca10-162">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
