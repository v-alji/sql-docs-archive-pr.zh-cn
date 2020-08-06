---
title: FOR XML 查询中的 TYPE 指令 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, TYPE directive
- TYPE directive
ms.assetid: a3df6c30-1f25-45dc-b5a9-bd0e41921293
author: rothja
ms.author: jroth
ms.openlocfilehash: cddce90718ef5edfcf161ddc6cc52b617825a2e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591149"
---
# <a name="type-directive-in-for-xml-queries"></a><span data-ttu-id="bc285-102">FOR XML 查询中的 TYPE 指令</span><span class="sxs-lookup"><span data-stu-id="bc285-102">TYPE Directive in FOR XML Queries</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="bc285-103">支持[xml &#40;transact-sql&#41;](/sql/t-sql/xml/xml-transact-sql)可通过指定 type 指令请求将 for xml 查询的结果作为 `xml` 数据类型返回。</span><span class="sxs-lookup"><span data-stu-id="bc285-103">support for the [xml &#40;Transact-SQL&#41;](/sql/t-sql/xml/xml-transact-sql) enables you to optionally request that the result of a FOR XML query be returned as `xml` data type by specifying the TYPE directive.</span></span> <span data-ttu-id="bc285-104">这样您便可以在服务器上处理 FOR XML 查询的结果。</span><span class="sxs-lookup"><span data-stu-id="bc285-104">This allows you to process the result of a FOR XML query on the server.</span></span> <span data-ttu-id="bc285-105">例如，可以对其指定 XQuery，将结果分配给 `xml` 类型变量，或编写[嵌套的 FOR XML 查询](use-nested-for-xml-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="bc285-105">For example, you can specify an XQuery against it, assign the result to an `xml` type variable, or write [Nested FOR XML queries](use-nested-for-xml-queries.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bc285-106">将 XML 数据类型实例数据作为不同服务器构造（如使用 TYPE 指令的 FOR XML 查询，或在其中使用 `xml` 数据类型返回 SQL 表列和输出参数中的 XML 实例数据值的 FOR XML 查询）的结果返回到客户端。</span><span class="sxs-lookup"><span data-stu-id="bc285-106">returns XML data type instance data to the client as a result of different server-constructs such as FOR XML queries that use the TYPE directive, or where the `xml` data type is used to return XML instance data values from SQL table columns and output parameters.</span></span> <span data-ttu-id="bc285-107">在客户端应用程序代码中，ADO.NET 提供程序请求从服务器以二进制编码发送此 XML 数据类型信息。</span><span class="sxs-lookup"><span data-stu-id="bc285-107">In client application code, the ADO.NET provider requests this XML data type information to be sent in a binary encoding from the server.</span></span> <span data-ttu-id="bc285-108">但是，如果使用的是不带 TYPE 指令的 FOR XML，则 XML 数据将以字符串类型返回。</span><span class="sxs-lookup"><span data-stu-id="bc285-108">However, if you are using FOR XML without the TYPE directive, the XML data comes back as a string type.</span></span> <span data-ttu-id="bc285-109">在任何情况下，客户端访问接口都始终能够处理其中任一种形式的 XML 内容。</span><span class="sxs-lookup"><span data-stu-id="bc285-109">In any case, the client provider will always be able to handle either form of XML.</span></span> <span data-ttu-id="bc285-110">请注意，不带 TYPE 指令的顶级 FOR XML 不能与游标一起使用。</span><span class="sxs-lookup"><span data-stu-id="bc285-110">Note that top-level FOR XML without the TYPE directive cannot be used with cursors.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="bc285-111">示例</span><span class="sxs-lookup"><span data-stu-id="bc285-111">Examples</span></span>  
 <span data-ttu-id="bc285-112">以下示例说明了带 FOR XML 查询的 TYPE 指令的用法。</span><span class="sxs-lookup"><span data-stu-id="bc285-112">The following examples illustrate the use of the TYPE directive with FOR XML queries.</span></span>  
  
### <a name="retrieving-for-xml-query-results-as-xml-type"></a><span data-ttu-id="bc285-113">作为 xml 类型检索 FOR XML 查询结果</span><span class="sxs-lookup"><span data-stu-id="bc285-113">Retrieving FOR XML query results as xml type</span></span>  
 <span data-ttu-id="bc285-114">下面的查询检索 `Contacts` 表中的客户联系信息。</span><span class="sxs-lookup"><span data-stu-id="bc285-114">The following query retrieves customer contact information from the `Contacts` table.</span></span> <span data-ttu-id="bc285-115">由于在 `TYPE` 中指定了 `FOR XML` 指令，因此返回的结果的类型为 `xml`。</span><span class="sxs-lookup"><span data-stu-id="bc285-115">Because the `TYPE` directive is specified in `FOR XML`, the result is returned as `xml` type.</span></span>  
  
```  
USE AdventureWorks2012;  
Go  
SELECT BusinessEntityID, FirstName, LastName  
FROM Person.Person  
ORDER BY BusinessEntityID  
FOR XML AUTO, TYPE;  
```  
  
 <span data-ttu-id="bc285-116">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="bc285-116">This is the partial result:</span></span>  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="S??nchez"/>`  
  
 `<Person.Person BusinessEntityID="2" FirstName="Terri" LastName="Duffy"/>`  
  
 `...`  
  
### <a name="assigning-for-xml-query-results-to-an-xml-type-variable"></a><span data-ttu-id="bc285-117">将 FOR XML 查询结果赋给 xml 类型变量</span><span class="sxs-lookup"><span data-stu-id="bc285-117">Assigning FOR XML query results to an xml type variable</span></span>  
 <span data-ttu-id="bc285-118">在下面的示例中，一个 FOR XML 结果被赋给一个 `xml` 类型变量 `@x`。</span><span class="sxs-lookup"><span data-stu-id="bc285-118">In the following example, a FOR XML result is assigned to an `xml` type variable, `@x`.</span></span> <span data-ttu-id="bc285-119">该查询从的列检索联系信息，例如 `BusinessEntityID` 、、 `FirstName` `LastName` 和其他电话号码 `AdditionalContactInfo` `xml``TYPE` 。</span><span class="sxs-lookup"><span data-stu-id="bc285-119">The query retrieves contact information, such as the `BusinessEntityID`, `FirstName`, `LastName`, and additional telephone numbers, from the `AdditionalContactInfo` column of `xml``TYPE`.</span></span> <span data-ttu-id="bc285-120">由于 `FOR XML` 子句指定了 `TYPE` 指令，因此 XML 返回为 `xml` 类型并赋给某个变量。</span><span class="sxs-lookup"><span data-stu-id="bc285-120">Because the `FOR XML` clause specifies `TYPE` directive, the XML is returned as `xml` type and is assigned to a variable.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @x xml;  
SET @x = (  
   SELECT BusinessEntityID,   
          FirstName,   
          LastName,   
          AdditionalContactInfo.query('  
declare namespace aci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
              //act:telephoneNumber/act:number') as MorePhoneNumbers  
   FROM Person.Person  
   FOR XML AUTO, TYPE);  
SELECT @x;  
GO  
```  
  
### <a name="querying-results-of-a-for-xml-query"></a><span data-ttu-id="bc285-121">查询 FOR XML 查询的结果</span><span class="sxs-lookup"><span data-stu-id="bc285-121">Querying results of a FOR XML query</span></span>  
 <span data-ttu-id="bc285-122">FOR XML 查询返回 XML。</span><span class="sxs-lookup"><span data-stu-id="bc285-122">The FOR XML queries return XML.</span></span> <span data-ttu-id="bc285-123">因此，可以将 `xml` 类型方法（如 `query()` 和 `value()`）应用于 FOR XML 查询返回的 XML 结果。</span><span class="sxs-lookup"><span data-stu-id="bc285-123">Therefore, you can apply `xml` type methods, such as `query()` and `value()`, to the XML result returned by FOR XML queries.</span></span>  
  
 <span data-ttu-id="bc285-124">在下面的查询中，`xml` 数据类型的 `query()` 方法用于查询 `FOR XML` 查询的结果。</span><span class="sxs-lookup"><span data-stu-id="bc285-124">In the following query, the `query()` method of the `xml` data type is used to query the result of the `FOR XML` query.</span></span> <span data-ttu-id="bc285-125">有关详细信息，请参阅 [query() 方法（xml 数据类型）](/sql/t-sql/xml/query-method-xml-data-type)。</span><span class="sxs-lookup"><span data-stu-id="bc285-125">For more information, see [query&#40;&#41; Method &#40;xml Data Type&#41;](/sql/t-sql/xml/query-method-xml-data-type).</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT (SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
DECLARE namespace aci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
DECLARE namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumbers  
FROM Person.Person  
FOR XML AUTO, TYPE).query('/Person.Person[1]');  
```  
  
 <span data-ttu-id="bc285-126">内部 `SELECT ... FOR XML` 查询返回 `xml` 类型结果，外部 `SELECT` 将 `query()` 方法应用于该 `xml` 类型。</span><span class="sxs-lookup"><span data-stu-id="bc285-126">The inner `SELECT ... FOR XML` query returns an `xml` type result to which the outer `SELECT` applies the `query()` method to the `xml` type.</span></span> <span data-ttu-id="bc285-127">请注意指定的 `TYPE` 指令。</span><span class="sxs-lookup"><span data-stu-id="bc285-127">Note the `TYPE` directive specified.</span></span>  
  
 <span data-ttu-id="bc285-128">结果如下：</span><span class="sxs-lookup"><span data-stu-id="bc285-128">This is the result:</span></span>  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="S??nchez">`  
  
 `<PhoneNumbers>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">111-111-1111</act:number>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">112-111-1111</act:number>`  
  
 `</PhoneNumbers>`  
  
 `</Person.Person>`  
  
 <span data-ttu-id="bc285-129">在下面的查询中，`xml` 数据类型的 `value()` 方法用于检索 `SELECT...FOR XML` 查询返回的 XML 结果中的值。</span><span class="sxs-lookup"><span data-stu-id="bc285-129">In the following query, the `value()` method of the `xml` data type is used to retrieve a value from the XML result returned by the `SELECT...FOR XML` query.</span></span> <span data-ttu-id="bc285-130">有关详细信息，请参阅 [value() 方法（xml 数据类型）](/sql/t-sql/xml/value-method-xml-data-type)。</span><span class="sxs-lookup"><span data-stu-id="bc285-130">For more information, see [value&#40;&#41; Method &#40;xml Data Type&#41;](/sql/t-sql/xml/value-method-xml-data-type).</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @FirstPhoneFromAdditionalContactInfo varchar(40);  
SELECT @FirstPhoneFromAdditionalContactInfo =   
 ( SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace aci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
   //act:telephoneNumber/act:number  
   ') AS PhoneNumbers  
   FROM Person.Person Contact  
   FOR XML AUTO, TYPE).value('  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
  /Contact[@BusinessEntityID="1"][1]/PhoneNumbers[1]/act:number[1]', 'varchar(40)'  
 )  
SELECT @FirstPhoneFromAdditionalContactInfo;  
```  
  
 <span data-ttu-id="bc285-131">`value()` 方法中的 XQuery 路径表达式检索 `BusinessEntityID` 为 `1`的客户联系人的第一个电话号码。</span><span class="sxs-lookup"><span data-stu-id="bc285-131">The XQuery path expression in the `value()` method retrieves the first telephone number of a customer contact whose `BusinessEntityID` is `1`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bc285-132">如果未指定 TYPE 指令，则返回的 FOR XML 查询结果的类型为 `nvarchar(max)`。</span><span class="sxs-lookup"><span data-stu-id="bc285-132">If the TYPE directive is not specified, the FOR XML query result is returned as type `nvarchar(max)`.</span></span>  
  
### <a name="using-for-xml-query-results-in-insert-update-and-delete-transact-sql-dml"></a><span data-ttu-id="bc285-133">在 INSERT、UPDATE 和 DELETE 中使用 FOR XML 查询结果 (Transact-SQL DML)</span><span class="sxs-lookup"><span data-stu-id="bc285-133">Using FOR XML query results in INSERT, UPDATE, and DELETE (Transact-SQL DML)</span></span>  
 <span data-ttu-id="bc285-134">下面的示例说明了如何在数据操作语言 (DML) 语句中使用 FOR XML 查询。</span><span class="sxs-lookup"><span data-stu-id="bc285-134">The following example demonstrates how FOR XML queries can be used in Data Manipulation Language (DML) statements.</span></span> <span data-ttu-id="bc285-135">在此示例中，`FOR XML` 返回 `xml` 类型的实例。</span><span class="sxs-lookup"><span data-stu-id="bc285-135">In the example, the `FOR XML` returns an instance of `xml` type.</span></span> <span data-ttu-id="bc285-136">`INSERT` 语句将此 XML 插入表中。</span><span class="sxs-lookup"><span data-stu-id="bc285-136">The `INSERT` statement inserts this XML into a table.</span></span>  
  
```  
CREATE TABLE T1(intCol int, XmlCol xml);  
GO  
INSERT INTO T1   
VALUES(1, '<Root><ProductDescription ProductModelID="1" /></Root>');  
GO  
  
CREATE TABLE T2(XmlCol xml)  
GO  
INSERT INTO T2(XmlCol)   
SELECT (SELECT XmlCol.query('/Root')   
        FROM T1   
        FOR XML AUTO,TYPE);   
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc285-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bc285-137">See Also</span></span>  
 [<span data-ttu-id="bc285-138">FOR XML (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bc285-138">FOR XML &#40;SQL Server&#41;</span></span>](../xml/for-xml-sql-server.md)  
  
  
