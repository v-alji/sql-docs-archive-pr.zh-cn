---
title: 操作 UDT 数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- CAST function
- data deletions [CLR integration]
- data insertions [CLR integration]
- CONVERT function
- data updates [CLR integration]
- comparing data
- updating data [CLR integration]
- removing data
- IsByteOrdered property
- variables [CLR integration]
- data manipulation [CLR integration]
- user-defined types [CLR integration], data manipulation
- deleting data
- UDTs [CLR integration], data manipulation
- invoking UDT methods
- inserting data
ms.assetid: 51b1a5f2-7591-4e11-bfe2-d88e0836403f
author: rothja
ms.author: jroth
ms.openlocfilehash: 75810a2ffd92130e45025f742d43ba7917d73992
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688947"
---
# <a name="manipulating-udt-data"></a><span data-ttu-id="582a8-102">操作 UDT 数据</span><span class="sxs-lookup"><span data-stu-id="582a8-102">Manipulating UDT Data</span></span>
  [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="582a8-103">没有为在对用户定义类型 (UDT) 列中的数据进行修改时所使用的 INSERT、UPDATE 或 DELETE 语句提供专用语法。</span><span class="sxs-lookup"><span data-stu-id="582a8-103">provides no specialized syntax for INSERT, UPDATE, or DELETE statements when modifying data in user-defined type (UDT) columns.</span></span> <span data-ttu-id="582a8-104">[!INCLUDE[tsql](../../includes/tsql-md.md)] CAST 或 CONVERT 函数用于将本机数据类型转换为 UDT 类型。</span><span class="sxs-lookup"><span data-stu-id="582a8-104">The [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST or CONVERT functions are used to cast native data types to the UDT type.</span></span>  
  
## <a name="inserting-data-in-a-udt-column"></a><span data-ttu-id="582a8-105">在 UDT 列中插入数据</span><span class="sxs-lookup"><span data-stu-id="582a8-105">Inserting Data in a UDT Column</span></span>  
 <span data-ttu-id="582a8-106">以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句将三行示例数据插入到**Points**表中。</span><span class="sxs-lookup"><span data-stu-id="582a8-106">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements insert three rows of sample data into the **Points** table.</span></span> <span data-ttu-id="582a8-107">**Point**数据类型由作为 UDT 属性公开的 X 和 Y 整数值组成。</span><span class="sxs-lookup"><span data-stu-id="582a8-107">The **Point** data type consists of X and Y integer values that are exposed as properties of the UDT.</span></span> <span data-ttu-id="582a8-108">必须使用 CAST 或 CONVERT 函数将以逗号分隔的 X 和 Y 值转换为**点**类型。</span><span class="sxs-lookup"><span data-stu-id="582a8-108">You must use either the CAST or CONVERT function to cast the comma-delimited X and Y values to the **Point** type.</span></span> <span data-ttu-id="582a8-109">前两个语句使用 CONVERT 函数将字符串值转换为**点**类型，第三个语句使用 CAST 函数：</span><span class="sxs-lookup"><span data-stu-id="582a8-109">The first two statements use the CONVERT function to convert a string value to the **Point** type, and the third statement uses the CAST function:</span></span>  
  
```  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '3,4'));  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '1,5'));  
INSERT INTO dbo.Points (PointValue) VALUES (CAST ('1,99' AS Point));  
```  
  
## <a name="selecting-data"></a><span data-ttu-id="582a8-110">选择数据</span><span class="sxs-lookup"><span data-stu-id="582a8-110">Selecting Data</span></span>  
 <span data-ttu-id="582a8-111">下面的 SELECT 语句选择 UDT 的二进制值。</span><span class="sxs-lookup"><span data-stu-id="582a8-111">The following SELECT statement selects the binary value of the UDT.</span></span>  
  
```  
SELECT ID, PointValue FROM dbo.Points  
```  
  
 <span data-ttu-id="582a8-112">若要查看以可读格式显示的输出，请调用 `ToString` **Point** UDT 的方法，该方法将值转换为其字符串表示形式。</span><span class="sxs-lookup"><span data-stu-id="582a8-112">To see the output displayed in a readable format, call the `ToString` method of the **Point** UDT, which converts the value to its string representation.</span></span>  
  
```  
SELECT ID, PointValue.ToString() AS PointValue   
FROM dbo.Points;  
```  
  
 <span data-ttu-id="582a8-113">这将产生以下结果：</span><span class="sxs-lookup"><span data-stu-id="582a8-113">This produces the following results.</span></span>  
  
```  
IDPointValue  
----------  
13,4  
21,5  
31,99  
```  
  
 <span data-ttu-id="582a8-114">还可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST 和 CONVERT 函数以取得相同结果。</span><span class="sxs-lookup"><span data-stu-id="582a8-114">You can also use the [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST and CONVERT functions to achieve the same results.</span></span>  
  
```  
SELECT ID, CAST(PointValue AS varchar)   
FROM dbo.Points;  
  
SELECT ID, CONVERT(varchar, PointValue)   
FROM dbo.Points;  
```  
  
 <span data-ttu-id="582a8-115">**Point** UDT 将其 X 和 Y 坐标公开为属性，然后您可以单独选择这些属性。</span><span class="sxs-lookup"><span data-stu-id="582a8-115">The **Point** UDT exposes its X and Y coordinates as properties, which you can then select individually.</span></span> <span data-ttu-id="582a8-116">以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句将分别选择 X 和 Y 坐标：</span><span class="sxs-lookup"><span data-stu-id="582a8-116">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement selects the X and Y coordinates separately:</span></span>  
  
```  
SELECT ID, PointValue.X AS xVal, PointValue.Y AS yVal   
FROM dbo.Points;  
```  
  
 <span data-ttu-id="582a8-117">X 和 Y 属性将返回整数值，该值在结果集中显示。</span><span class="sxs-lookup"><span data-stu-id="582a8-117">The X and Y properties return an integer value, which is displayed in the result set.</span></span>  
  
```  
IDxValyVal  
----------  
134  
215  
3199  
```  
  
## <a name="working-with-variables"></a><span data-ttu-id="582a8-118">使用变量</span><span class="sxs-lookup"><span data-stu-id="582a8-118">Working with Variables</span></span>  
 <span data-ttu-id="582a8-119">可以通过使用 DECLARE 语句将变量分配给 UDT 类型来使用变量。</span><span class="sxs-lookup"><span data-stu-id="582a8-119">You can work with variables using the DECLARE statement to assign a variable to a UDT type.</span></span> <span data-ttu-id="582a8-120">以下语句使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] SET 语句执行赋值，并通过对变量调用 UDT 的 `ToString` 方法来显示结果：</span><span class="sxs-lookup"><span data-stu-id="582a8-120">The following statements assign a value using the [!INCLUDE[tsql](../../includes/tsql-md.md)] SET statement and display the results by calling the UDT's `ToString` method on the variable:</span></span>  
  
```  
DECLARE @PointValue Point;  
SET @PointValue = (SELECT PointValue FROM dbo.Points  
    WHERE ID = 2);  
SELECT @PointValue.ToString() AS PointValue;  
```  
  
 <span data-ttu-id="582a8-121">结果集显示变量值：</span><span class="sxs-lookup"><span data-stu-id="582a8-121">The result set displays the variable value:</span></span>  
  
```  
PointValue  
----------  
-1,5  
```  
  
 <span data-ttu-id="582a8-122">以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句使用 SELECT 而不是 SET 进行变量赋值，可取得相同结果：</span><span class="sxs-lookup"><span data-stu-id="582a8-122">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements achieve the same result using SELECT rather than SET for the variable assignment:</span></span>  
  
```  
DECLARE @PointValue Point;  
SELECT @PointValue = PointValue FROM dbo.Points  
    WHERE ID = 2;  
SELECT @PointValue.ToString() AS PointValue;  
```  
  
 <span data-ttu-id="582a8-123">使用 SELECT 和使用 SET 进行变量赋值的差异是 SELECT 允许在一个 SELECT 语句中为多个变量赋值，而 SET 语法则要求每次变量赋值都要有自己的 SET 语句。</span><span class="sxs-lookup"><span data-stu-id="582a8-123">The difference between using SELECT and SET for variable assignment is that SELECT allows you to assign multiple variables in one SELECT statement, whereas the SET syntax requires each variable assignment to have its own SET statement.</span></span>  
  
## <a name="comparing-data"></a><span data-ttu-id="582a8-124">比较数据</span><span class="sxs-lookup"><span data-stu-id="582a8-124">Comparing Data</span></span>  
 <span data-ttu-id="582a8-125">如果已在定义类时将 `IsByteOrdered` 属性设置为 `true`，则可以在 UDT 中使用比较运算符进行值的比较。</span><span class="sxs-lookup"><span data-stu-id="582a8-125">You can use comparison operators to compare values in your UDT if you have set the `IsByteOrdered` property to `true` when defining the class.</span></span> <span data-ttu-id="582a8-126">有关详细信息，请参阅[创建用户定义类型](creating-user-defined-types.md)。</span><span class="sxs-lookup"><span data-stu-id="582a8-126">For more information, see [Creating a User-Defined Type](creating-user-defined-types.md).</span></span>  
  
```  
SELECT ID, PointValue.ToString() AS Points   
FROM dbo.Points  
WHERE PointValue > CONVERT(Point, '2,2');  
```  
  
 <span data-ttu-id="582a8-127">如果值本身是可比较的，则可以比较 UDT 的内部值，而无需考虑 `IsByteOrdered` 设置。</span><span class="sxs-lookup"><span data-stu-id="582a8-127">You can compare internal values of the UDT regardless of the `IsByteOrdered` setting if the values themselves are comparable.</span></span> <span data-ttu-id="582a8-128">以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句选择 X 大于 Y 的行：</span><span class="sxs-lookup"><span data-stu-id="582a8-128">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement selects rows where X is greater than Y:</span></span>  
  
```  
SELECT ID, PointValue.ToString() AS PointValue   
FROM dbo.Points  
WHERE PointValue.X < PointValue.Y;  
```  
  
 <span data-ttu-id="582a8-129">还可以对变量使用比较运算符，如搜索匹配的 PointValue 的查询所示。</span><span class="sxs-lookup"><span data-stu-id="582a8-129">You can also use comparison operators with variables, as shown in this query that searches for a matching PointValue.</span></span>  
  
```  
DECLARE @ComparePoint Point;  
SET @ComparePoint = CONVERT(Point, '3,4');  
SELECT ID, PointValue.ToString() AS MatchingPoint   
FROM dbo.Points  
WHERE PointValue = @ComparePoint;  
```  
  
## <a name="invoking-udt-methods"></a><span data-ttu-id="582a8-130">调用 UDT 方法</span><span class="sxs-lookup"><span data-stu-id="582a8-130">Invoking UDT Methods</span></span>  
 <span data-ttu-id="582a8-131">还可以在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中调用在 UDT 中定义的方法。</span><span class="sxs-lookup"><span data-stu-id="582a8-131">You can also invoke methods that are defined in your UDT in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="582a8-132">**Point**类包含三个方法： `Distance` 、 `DistanceFrom` 和 `DistanceFromXY` 。</span><span class="sxs-lookup"><span data-stu-id="582a8-132">The **Point** class contains three methods, `Distance`, `DistanceFrom`, and `DistanceFromXY`.</span></span> <span data-ttu-id="582a8-133">有关定义这三个方法的代码清单，请参阅[编写用户定义类型](creating-user-defined-types-coding.md)的代码。</span><span class="sxs-lookup"><span data-stu-id="582a8-133">For the code listings defining these three methods, see [Coding User-Defined Types](creating-user-defined-types-coding.md).</span></span>  
  
 <span data-ttu-id="582a8-134">以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句调用 `PointValue.Distance` 方法：</span><span class="sxs-lookup"><span data-stu-id="582a8-134">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement calls the `PointValue.Distance` method:</span></span>  
  
```  
SELECT ID, PointValue.X AS [Point.X],   
    PointValue.Y AS [Point.Y],  
    PointValue.Distance() AS DistanceFromZero   
FROM dbo.Points;  
```  
  
 <span data-ttu-id="582a8-135">结果显示在 `Distance` 列中：</span><span class="sxs-lookup"><span data-stu-id="582a8-135">The results are displayed in the `Distance` column:</span></span>  
  
```  
IDXYDistance  
------------------------  
1345  
2155.09901951359278  
319999.0050503762308  
```  
  
 <span data-ttu-id="582a8-136">`DistanceFrom`方法采用**点**数据类型的自变量，并显示从指定点到 PointValue 的距离：</span><span class="sxs-lookup"><span data-stu-id="582a8-136">The `DistanceFrom` method takes an argument of **Point** data type, and displays the distance from the specified point to the PointValue:</span></span>  
  
```  
SELECT ID, PointValue.ToString() AS Pnt,  
   PointValue.DistanceFrom(CONVERT(Point, '1,99')) AS DistanceFromPoint  
FROM dbo.Points;  
```  
  
 <span data-ttu-id="582a8-137">结果将针对表中的每一行显示 `DistanceFrom` 方法的结果：</span><span class="sxs-lookup"><span data-stu-id="582a8-137">The results display the results of the `DistanceFrom` method for each row in the table:</span></span>  
  
```  
ID PntDistanceFromPoint  
---------------------  
13,495.0210502993942  
21,594  
31,990  
```  
  
 <span data-ttu-id="582a8-138">`DistanceFromXY` 方法逐个接受各点作为参数：</span><span class="sxs-lookup"><span data-stu-id="582a8-138">The `DistanceFromXY` method takes the points individually as arguments:</span></span>  
  
```  
SELECT ID, PointValue.X as X, PointValue.Y as Y,   
PointValue.DistanceFromXY(1, 99) AS DistanceFromXY   
FROM dbo.Points  
```  
  
 <span data-ttu-id="582a8-139">结果集与 `DistanceFrom` 方法相同。</span><span class="sxs-lookup"><span data-stu-id="582a8-139">The result set is the same as the `DistanceFrom` method.</span></span>  
  
## <a name="updating-data-in-a-udt-column"></a><span data-ttu-id="582a8-140">更新 UDT 列中的数据</span><span class="sxs-lookup"><span data-stu-id="582a8-140">Updating Data in a UDT Column</span></span>  
 <span data-ttu-id="582a8-141">若要更新 UDT 列中的数据，请使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE 语句。</span><span class="sxs-lookup"><span data-stu-id="582a8-141">To update data in a UDT column, use the [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE statement.</span></span> <span data-ttu-id="582a8-142">还可以使用 UDT 的方法以更新对象的状态。</span><span class="sxs-lookup"><span data-stu-id="582a8-142">You can also use a method of the UDT to update the state of the object.</span></span> <span data-ttu-id="582a8-143">以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句更新表中的单个行：</span><span class="sxs-lookup"><span data-stu-id="582a8-143">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement updates a single row in the table:</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue = CAST('1,88' AS Point)  
WHERE ID = 3  
```  
  
 <span data-ttu-id="582a8-144">还可以单独更新 UDT 元素。</span><span class="sxs-lookup"><span data-stu-id="582a8-144">You can also update UDT elements separately.</span></span> <span data-ttu-id="582a8-145">以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句仅更新 Y 坐标：</span><span class="sxs-lookup"><span data-stu-id="582a8-145">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement updates only the Y coordinate:</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue.Y = 99  
WHERE ID = 3  
```  
  
 <span data-ttu-id="582a8-146">如果已在将字节顺序设置为 `true` 的情况下定义 UDT，则 [!INCLUDE[tsql](../../includes/tsql-md.md)] 可以通过 WHERE 子句计算 UDT 列。</span><span class="sxs-lookup"><span data-stu-id="582a8-146">If the UDT has been defined with byte ordering set to `true`, [!INCLUDE[tsql](../../includes/tsql-md.md)] can evaluate the UDT column in a WHERE clause.</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue = '4,5'  
WHERE PointValue = '3,4';  
```  
  
### <a name="updating-limitations"></a><span data-ttu-id="582a8-147">更新限制</span><span class="sxs-lookup"><span data-stu-id="582a8-147">Updating Limitations</span></span>  
 <span data-ttu-id="582a8-148">无法使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 一次更新多个属性。</span><span class="sxs-lookup"><span data-stu-id="582a8-148">You cannot update multiple properties at once using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="582a8-149">例如，以下 UPDATE 语句将失败并返回错误，因为无法在一个 UDATE 语句中两次使用相同的列名称。</span><span class="sxs-lookup"><span data-stu-id="582a8-149">For example, the following UPDATE statement fails with an error because you cannot use the same column name twice in one UDATE statement.</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue.X = 5, PointValue.Y = 99  
WHERE ID = 3  
```  
  
 <span data-ttu-id="582a8-150">若要分别更新每个点，需要在 Point UDT 程序集中创建赋值函数方法。</span><span class="sxs-lookup"><span data-stu-id="582a8-150">To update each point individually, you would need to create a mutator method in the Point UDT assembly.</span></span> <span data-ttu-id="582a8-151">然后，可以在 [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE 语句中调用赋值函数方法以更新对象，如下所示：</span><span class="sxs-lookup"><span data-stu-id="582a8-151">You can then invoke the mutator method to update the object in a [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE statement, as in the following:</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue.SetXY(5, 99)  
WHERE ID = 3  
```  
  
## <a name="deleting-data-in-a-udt-column"></a><span data-ttu-id="582a8-152">删除 UDT 列中的数据</span><span class="sxs-lookup"><span data-stu-id="582a8-152">Deleting Data in a UDT Column</span></span>  
 <span data-ttu-id="582a8-153">若要删除 UDT 中的数据，请使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] DELETE 语句。</span><span class="sxs-lookup"><span data-stu-id="582a8-153">To delete data in a UDT, use the [!INCLUDE[tsql](../../includes/tsql-md.md)] DELETE statement.</span></span> <span data-ttu-id="582a8-154">以下语句删除该表中与 WHERE 子句中指定的条件匹配的所有行。</span><span class="sxs-lookup"><span data-stu-id="582a8-154">The following statement deletes all rows in the table that match the criteria specified in the WHERE clause.</span></span> <span data-ttu-id="582a8-155">如果在 DELETE 语句中省略 WHERE 子句，将删除表中所有行。</span><span class="sxs-lookup"><span data-stu-id="582a8-155">If you omit the WHERE clause in a DELETE statement, all rows in the table will be deleted.</span></span>  
  
```  
DELETE FROM dbo.Points  
WHERE PointValue = CAST('1,99' AS Point)  
```  
  
 <span data-ttu-id="582a8-156">如果要删除 UDT 列中的值而不改变其他行值，请使用 UPDATE 语句。</span><span class="sxs-lookup"><span data-stu-id="582a8-156">Use the UPDATE statement if you want to remove the values in a UDT column while leaving other row values intact.</span></span> <span data-ttu-id="582a8-157">下面的示例将 PointValue 设置为 Null：</span><span class="sxs-lookup"><span data-stu-id="582a8-157">This example sets the PointValue to null.</span></span>  
  
```  
UPDATE dbo.Points  
SET PointValue = null  
WHERE ID = 2  
```  
  
## <a name="see-also"></a><span data-ttu-id="582a8-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="582a8-158">See Also</span></span>  
 [<span data-ttu-id="582a8-159">使用 SQL Server 中的用户定义类型</span><span class="sxs-lookup"><span data-stu-id="582a8-159">Working with User-Defined Types in SQL Server</span></span>](working-with-user-defined-types-in-sql-server.md)  
  
  
