---
title: 创建 XML 数据类型的变量和列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xml data type [SQL Server], variables
- xml data type [SQL Server], columns
ms.assetid: 8994ab6e-5519-4ba2-97a1-fac8af6f72db
author: rothja
ms.author: jroth
ms.openlocfilehash: 08b79888eb47634deaccc910b2ea3c93800b7c78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692303"
---
# <a name="create-xml-data-type-variables-and-columns"></a><span data-ttu-id="61802-102">创建 XML 数据类型的变量和列</span><span class="sxs-lookup"><span data-stu-id="61802-102">Create XML Data Type Variables and Columns</span></span>
  <span data-ttu-id="61802-103">`xml` 数据类型是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的内置数据类型，并有些类似于其他内置类型（如 `int` 和 `varchar`）。</span><span class="sxs-lookup"><span data-stu-id="61802-103">The `xml` data type is a built-in data type in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and is somewhat similar to other built-in types such as `int` and `varchar`.</span></span> <span data-ttu-id="61802-104">与其他内置类型一样，在 `xml` 创建表作为变量类型、参数类型、函数返回类型或在[CAST 和 CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql)中时，可以使用数据类型作为列类型。</span><span class="sxs-lookup"><span data-stu-id="61802-104">As with other built-in types, you can use the `xml` data type as a column type when you create a table as a variable type, a parameter type, a function-return type, or in [CAST and CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
## <a name="creating-columns-and-variables"></a><span data-ttu-id="61802-105">创建列和变量</span><span class="sxs-lookup"><span data-stu-id="61802-105">Creating Columns and Variables</span></span>  
 <span data-ttu-id="61802-106">若要创建 `xml` 类型列作为表的一部分，请使用 `CREATE TABLE` 语句，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="61802-106">To create an `xml` type column as part of a table, use a `CREATE TABLE` statement, as shown in the following example:</span></span>  
  
```  
CREATE TABLE T1(Col1 int primary key, Col2 xml)   
```  
  
 <span data-ttu-id="61802-107">可以使用 `DECLARE statement` 创建 `xml` 类型的变量，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="61802-107">You can use a `DECLARE statement` to create a variable of `xml` type, as the following example shows.</span></span>  
  
```  
DECLARE @x xml   
```  
  
 <span data-ttu-id="61802-108">可以通过指定 XML 架构集合创建类型化的 `xml` 变量，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="61802-108">Create a typed `xml` variable by specifying an XML schema collection, as shown in the following example.</span></span>  
  
```  
DECLARE @x xml (Sales.StoreSurveySchemaCollection)  
```  
  
 <span data-ttu-id="61802-109">若要将 `xml` 类型参数传递给存储过程，请使用 `CREATE PROCEDURE` 语句，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="61802-109">To pass an `xml` type parameter to a stored procedure, use a `CREATE PROCEDURE` statement, as shown in the following example.</span></span>  
  
```  
CREATE PROCEDURE SampleProc(@XmlDoc xml) AS ...   
```  
  
 <span data-ttu-id="61802-110">可以使用 XQuery 来查询存储在列、参数或变量中的 XML 实例。</span><span class="sxs-lookup"><span data-stu-id="61802-110">You can use XQuery to query XML instances stored in columns, parameters, or variables.</span></span> <span data-ttu-id="61802-111">还可以使用 XML 数据操作语言 (XML DML) 对 XML 实例进行更新。</span><span class="sxs-lookup"><span data-stu-id="61802-111">You can also use the XML Data Manipulation Language (XML DML) to apply updates to the XML instances.</span></span> <span data-ttu-id="61802-112">由于开发时 XQuery 标准未定义 XQuery DML，因此， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将 [XML 数据修改语言](/sql/t-sql/xml/xml-data-modification-language-xml-dml) 扩展插件引入 XQuery。</span><span class="sxs-lookup"><span data-stu-id="61802-112">Because the XQuery standard did not define XQuery DML at the time of development, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] introduces [XML Data Modification Language](/sql/t-sql/xml/xml-data-modification-language-xml-dml) extensions to XQuery.</span></span> <span data-ttu-id="61802-113">这些扩展插件使您可以执行插入、更新和删除操作。</span><span class="sxs-lookup"><span data-stu-id="61802-113">These extensions allow you to perform insert, update, and delete operations.</span></span>  
  
## <a name="assigning-defaults"></a><span data-ttu-id="61802-114">分配默认的 XML 实例</span><span class="sxs-lookup"><span data-stu-id="61802-114">Assigning Defaults</span></span>  
 <span data-ttu-id="61802-115">在表中，可以为 `xml` 类型的列分配默认 XML 实例。</span><span class="sxs-lookup"><span data-stu-id="61802-115">In a table, you can assign a default XML instance to a column of `xml` type.</span></span> <span data-ttu-id="61802-116">可以通过两种方式提供默认的 XML：通过使用 XML 常量，或通过使用到 `xml` 类型的显式转换。</span><span class="sxs-lookup"><span data-stu-id="61802-116">You can provide the default XML in one of two ways: by using an XML constant, or by using an explicit cast to the `xml` type.</span></span>  
  
 <span data-ttu-id="61802-117">若要提供默认的 XML 作为 XML 常量，请使用下例所示的语法。</span><span class="sxs-lookup"><span data-stu-id="61802-117">To provide the default XML as an XML constant, use syntax as shown in the following example.</span></span> <span data-ttu-id="61802-118">请注意，此字符串将显式转换为 `xml` 类型。</span><span class="sxs-lookup"><span data-stu-id="61802-118">Note that the string is implicitly CAST to `xml` type.</span></span>  
  
```  
CREATE TABLE T (XmlColumn xml default N'<element1/><element2/>')  
```  
  
 <span data-ttu-id="61802-119">若要提供默认的 XML 作为到 `CAST` 的显式 `xml`，请使用下例所示的语法。</span><span class="sxs-lookup"><span data-stu-id="61802-119">To provide the default XML as an explicit `CAST` to `xml`, use syntax as shown in the following example.</span></span>  
  
```  
CREATE TABLE T (XmlColumn xml   
                  default CAST(N'<element1/><element2/>' AS xml))  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="61802-120">还支持对 `xml` 类型列的 NULL 和 NOT NULL 约束。</span><span class="sxs-lookup"><span data-stu-id="61802-120">also supports NULL and NOT NULL constraints on columns of `xml` type.</span></span> <span data-ttu-id="61802-121">例如：</span><span class="sxs-lookup"><span data-stu-id="61802-121">For example:</span></span>  
  
```  
CREATE TABLE T (XmlColumn xml NOT NULL)  
```  
  
## <a name="specifying-constraints"></a><span data-ttu-id="61802-122">指定约束</span><span class="sxs-lookup"><span data-stu-id="61802-122">Specifying Constraints</span></span>  
 <span data-ttu-id="61802-123">创建 `xml` 类型的列时，可以定义列级或表级的约束。</span><span class="sxs-lookup"><span data-stu-id="61802-123">When you create columns of `xml` type, you can define column-level or table-level constraints.</span></span> <span data-ttu-id="61802-124">在下列情况下，请使用约束：</span><span class="sxs-lookup"><span data-stu-id="61802-124">Use constraints in the following situations:</span></span>  
  
-   <span data-ttu-id="61802-125">无法在 XML 架构中表达业务规则。</span><span class="sxs-lookup"><span data-stu-id="61802-125">Your business rules cannot be expressed in XML schemas.</span></span> <span data-ttu-id="61802-126">例如，花店的交货地址必须在其营业地点周围 50 英里之内。</span><span class="sxs-lookup"><span data-stu-id="61802-126">For example, the delivery address of a flower shop must be within 50 miles of its business location.</span></span> <span data-ttu-id="61802-127">这可以编写为 XML 列的约束。</span><span class="sxs-lookup"><span data-stu-id="61802-127">This can be written as a constraint on the XML column.</span></span> <span data-ttu-id="61802-128">此约束可能涉及 `xml` 数据类型方法。</span><span class="sxs-lookup"><span data-stu-id="61802-128">The constraint may involve `xml` data type methods.</span></span>  
  
-   <span data-ttu-id="61802-129">您的约束涉及表中的其他 XML 列或非 XML 列。</span><span class="sxs-lookup"><span data-stu-id="61802-129">Your constraint involves other XML or non-XML columns in the table.</span></span> <span data-ttu-id="61802-130">例如，强制在 XML 实例中找到的客户 ID (`/Customer/@CustId`) 与 CustomerID 关系列中的值匹配。</span><span class="sxs-lookup"><span data-stu-id="61802-130">An example is the enforcement of the ID of a Customer (`/Customer/@CustId`) found in an XML instance to match the value in a relational CustomerID column.</span></span>  
  
 <span data-ttu-id="61802-131">可以为类型化或非类型化的 `xml` 数据类型列指定约束。</span><span class="sxs-lookup"><span data-stu-id="61802-131">You can specify constraints for typed or untyped `xml` data type columns.</span></span> <span data-ttu-id="61802-132">但在指定约束时，不能使用 [XML 数据类型方法](/sql/t-sql/xml/xml-data-type-methods) 。</span><span class="sxs-lookup"><span data-stu-id="61802-132">However, you cannot use the [XML data type methods](/sql/t-sql/xml/xml-data-type-methods) when you specify constraints.</span></span> <span data-ttu-id="61802-133">同时，请注意 `xml` 数据类型不支持以下列和表约束：</span><span class="sxs-lookup"><span data-stu-id="61802-133">Also, note that the `xml` data type does not support the following column and table constraints:</span></span>  
  
-   <span data-ttu-id="61802-134">PRIMARY KEY/ FOREIGN KEY</span><span class="sxs-lookup"><span data-stu-id="61802-134">PRIMARY KEY/ FOREIGN KEY</span></span>  
  
-   <span data-ttu-id="61802-135">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="61802-135">UNIQUE</span></span>  
  
-   <span data-ttu-id="61802-136">COLLATE</span><span class="sxs-lookup"><span data-stu-id="61802-136">COLLATE</span></span>  
  
     <span data-ttu-id="61802-137">XML 提供了它自己的编码。</span><span class="sxs-lookup"><span data-stu-id="61802-137">XML provides its own encoding.</span></span> <span data-ttu-id="61802-138">排序规则只适用于字符串类型。</span><span class="sxs-lookup"><span data-stu-id="61802-138">Collations apply to string types only.</span></span> <span data-ttu-id="61802-139">`xml` 数据类型不是字符串类型。</span><span class="sxs-lookup"><span data-stu-id="61802-139">The `xml` data type is not a string type.</span></span> <span data-ttu-id="61802-140">但是，它有字符串表示形式并允许与字符串数据类型之间的相互转换。</span><span class="sxs-lookup"><span data-stu-id="61802-140">However, it does have string representation and allows casting to and from string data types.</span></span>  
  
-   <span data-ttu-id="61802-141">RULE</span><span class="sxs-lookup"><span data-stu-id="61802-141">RULE</span></span>  
  
 <span data-ttu-id="61802-142">除了使用约束外，还可以创建用户定义函数作为包装来包装 `xml` 数据类型方法，并在检查约束中指定用户定义函数，如下例中所示。</span><span class="sxs-lookup"><span data-stu-id="61802-142">An alternative to using constraints is to create a wrapper, user-defined function to wrap the `xml` data type method and specify user-defined function in the check constraint as shown in the following example.</span></span>  
  
 <span data-ttu-id="61802-143">在以下示例中， `Col2` 的约束指定此列中存储的每个 XML 实例都必须具有包含 `<ProductDescription>` 属性的 `ProductID` 元素。</span><span class="sxs-lookup"><span data-stu-id="61802-143">In the following example, the constraint on `Col2` specifies that each XML instance stored in this column must have a `<ProductDescription>` element that contains a `ProductID` attribute.</span></span> <span data-ttu-id="61802-144">此约束由如下用户定义函数强制执行：</span><span class="sxs-lookup"><span data-stu-id="61802-144">This constraint is enforced by this user-defined function:</span></span>  
  
```  
CREATE FUNCTION my_udf(@var xml) returns bit  
AS BEGIN   
RETURN @var.exist('/ProductDescription/@ProductID')  
END  
GO  
```  
  
 <span data-ttu-id="61802-145">注意，如果实例中的 `exist()` 元素包含 `xml` 属性，则 `1` 数据类型的 `<ProductDescription>` 方法返回 `ProductID` 。</span><span class="sxs-lookup"><span data-stu-id="61802-145">Note that the `exist()` method of the `xml` data type returns `1` if the `<ProductDescription>` element in the instance contains the `ProductID` attribute.</span></span> <span data-ttu-id="61802-146">否则，将返回 `0`。</span><span class="sxs-lookup"><span data-stu-id="61802-146">Otherwise, it returns `0`.</span></span>  
  
 <span data-ttu-id="61802-147">现在，您就可以创建带有列级约束的表，如下所示：</span><span class="sxs-lookup"><span data-stu-id="61802-147">Now, you can create a table with a column-level constraint as follows:</span></span>  
  
```  
CREATE TABLE T (  
    Col1 int primary key,   
    Col2 xml check(dbo.my_udf(Col2)=1))  
GO  
```  
  
 <span data-ttu-id="61802-148">如下插入操作将成功：</span><span class="sxs-lookup"><span data-stu-id="61802-148">The following insert succeeds:</span></span>  
  
```  
INSERT INTO T values(1,'<ProductDescription ProductID="1" />')  
```  
  
 <span data-ttu-id="61802-149">由于存在约束，因此如下插入操作失败：</span><span class="sxs-lookup"><span data-stu-id="61802-149">Because of the constraint, the following insert fails:</span></span>  
  
```  
INSERT INTO T values(1,'<Product />')  
```  
  
## <a name="same-or-different-table"></a><span data-ttu-id="61802-150">相同或不同的表</span><span class="sxs-lookup"><span data-stu-id="61802-150">Same or Different Table</span></span>  
 <span data-ttu-id="61802-151">`xml`可以在包含其他关系列的表中创建数据类型列，也可以在具有与主表的外键关系的单独表中创建数据类型列。</span><span class="sxs-lookup"><span data-stu-id="61802-151">An `xml` data type column can be created in a table that contains other relational columns, or in a separate table with a foreign key relationship to a main table.</span></span>  
  
 <span data-ttu-id="61802-152">`xml`如果满足以下条件之一，则在同一个表中创建数据类型列：</span><span class="sxs-lookup"><span data-stu-id="61802-152">Create an `xml` data type column in the same table when one of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="61802-153">您的应用程序对 XML 列执行数据检索，并且不需要 XML 列的 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="61802-153">Your application performs data retrieval on the XML column and does not require an XML index on the XML column.</span></span>  
  
-   <span data-ttu-id="61802-154">您想要对 `xml` 数据类型列生成 XML 索引，并且主表的主键与它的聚集键相同。</span><span class="sxs-lookup"><span data-stu-id="61802-154">You want to build an XML index on the `xml` data type column and the primary key of the main table is the same as its clustering key.</span></span> <span data-ttu-id="61802-155">有关详细信息，请参阅 [XML 索引 (SQL Server)](xml-indexes-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="61802-155">For more information, see [XML Indexes &#40;SQL Server&#41;](xml-indexes-sql-server.md).</span></span>  
  
 <span data-ttu-id="61802-156">如果符合下列条件，则在单独的表中创建 `xml` 数据类型列：</span><span class="sxs-lookup"><span data-stu-id="61802-156">Create the `xml` data type column in a separate table if the following conditions are true:</span></span>  
  
-   <span data-ttu-id="61802-157">您想要对 `xml` 数据类型列生成 XML 索引，但是主表的主键与它的聚集键不同，或者主表没有主键，或者主表为一个堆（没有聚集键）。</span><span class="sxs-lookup"><span data-stu-id="61802-157">You want to build an XML index on the `xml` data type column, but the primary key of the main table is different from its clustering key, or the main table does not have a primary key, or the main table is a heap (no clustering key).</span></span> <span data-ttu-id="61802-158">如果主表已存在，可能会这样。</span><span class="sxs-lookup"><span data-stu-id="61802-158">This may be true if the main table already exists.</span></span>  
  
-   <span data-ttu-id="61802-159">您不希望因为表中存在 XML 列而降低表扫描的速度。</span><span class="sxs-lookup"><span data-stu-id="61802-159">You do not want table scans to slow down because of the presence of the XML column in the table.</span></span> <span data-ttu-id="61802-160">无论该列是存储在行内还是行外，都会占用空间。</span><span class="sxs-lookup"><span data-stu-id="61802-160">This uses space whether it is stored in-row or out-of-row.</span></span>  
  
  
