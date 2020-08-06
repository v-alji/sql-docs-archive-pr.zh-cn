---
title: 在计算列中使用 XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- computed columns, XML
- XML [SQL Server], computed columns
ms.assetid: 1313b889-69b4-4018-9868-0496dd83bf44
author: rothja
ms.author: jroth
ms.openlocfilehash: 33a7549823dc3e4a23cecfa97d7345a6421cb1b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682753"
---
# <a name="use-xml-in-computed-columns"></a><span data-ttu-id="338c6-102">在计算列中使用 XML</span><span class="sxs-lookup"><span data-stu-id="338c6-102">Use XML in Computed Columns</span></span>
  <span data-ttu-id="338c6-103">XML 实例可作为计算列的源或计算列的类型出现。</span><span class="sxs-lookup"><span data-stu-id="338c6-103">XML instances can appear as a source for a computed column, or as a type of computed column.</span></span> <span data-ttu-id="338c6-104">本主题中的示例演示如何将 XML 用于计算列。</span><span class="sxs-lookup"><span data-stu-id="338c6-104">The examples in this topic show how to use XML with computed columns.</span></span>  
  
## <a name="creating-computed-columns-from-xml-columns"></a><span data-ttu-id="338c6-105">从 XML 列创建计算列</span><span class="sxs-lookup"><span data-stu-id="338c6-105">Creating Computed Columns from XML Columns</span></span>  
 <span data-ttu-id="338c6-106">在以下 `CREATE TABLE` 语句中，通过 `xml` 计算`col2`类型列 ( `col1`)：</span><span class="sxs-lookup"><span data-stu-id="338c6-106">In the following `CREATE TABLE` statement, an `xml` type column (`col2`) is computed from `col1`:</span></span>  
  
```  
CREATE TABLE T(col1 varchar(max), col2 AS CAST(col1 AS xml) )    
```  
  
 <span data-ttu-id="338c6-107">`xml` 数据类型还可以作为创建计算列的源出现，如以下 `CREATE TABLE` 语句中所示：</span><span class="sxs-lookup"><span data-stu-id="338c6-107">The `xml` data type can also appear as a source in creating a computed column, as shown in the following `CREATE TABLE` statement:</span></span>  
  
```  
CREATE TABLE T (col1 xml, col2 as cast(col1 as varchar(1000) ))   
```  
  
 <span data-ttu-id="338c6-108">可以通过从 `xml` 类型列中提取值来创建计算列，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="338c6-108">You can create a computed column by extracting a value from an `xml` type column as shown in the following example.</span></span> <span data-ttu-id="338c6-109">由于不能将 `xml` 数据类型方法直接用于创建计算列，因此，此示例首先定义可从 XML 实例返回值的函数 (`my_udf`)。</span><span class="sxs-lookup"><span data-stu-id="338c6-109">Because the `xml` data type methods cannot be used directly in creating computed columns, the example first defines a function (`my_udf`) that returns a value from an XML instance.</span></span> <span data-ttu-id="338c6-110">此函数包装 `value()` 类型的 `xml` 方法。</span><span class="sxs-lookup"><span data-stu-id="338c6-110">The function wraps the `value()` method of the `xml` type.</span></span> <span data-ttu-id="338c6-111">然后在 `CREATE TABLE` 语句中为计算列指定函数名称。</span><span class="sxs-lookup"><span data-stu-id="338c6-111">The function name is then specified in the `CREATE TABLE` statement for the computed column.</span></span>  
  
```  
CREATE FUNCTION my_udf(@var xml) returns int  
AS BEGIN   
RETURN @var.value('(/ProductDescription/@ProductModelID)[1]' , 'int')  
END  
GO  
-- Use the function in CREATE TABLE.  
CREATE TABLE T (col1 xml, col2 as dbo.my_udf(col1) )  
GO  
-- Try adding a row.   
INSERT INTO T values('<ProductDescription ProductModelID="1" />')  
GO  
-- Verify results.  
SELECT col2, col1  
FROM T  
  
```  
  
 <span data-ttu-id="338c6-112">与上一个示例相同，以下示例定义函数以便针对计算列返回 `xml` 类型实例。</span><span class="sxs-lookup"><span data-stu-id="338c6-112">As in the previous example, the following example defines a function to return an `xml` type instance for a computed column.</span></span> <span data-ttu-id="338c6-113">在函数内部， `query()` 数据类型的 `xml` 方法从 `xml` 类型参数检索值。</span><span class="sxs-lookup"><span data-stu-id="338c6-113">Inside the function, the `query()` method of the `xml` data type retrieves a value from an `xml` type parameter.</span></span>  
  
```  
CREATE FUNCTION my_udf(@var xml)   
  RETURNS xml AS   
BEGIN   
   RETURN @var.query('ProductDescription/Features')  
END  
```  
  
 <span data-ttu-id="338c6-114">在以下 `CREATE TABLE` 语句中， `Col2` 是使用由以下函数返回的 XML 数据（`<Features>` 元素）的计算列：</span><span class="sxs-lookup"><span data-stu-id="338c6-114">In the following `CREATE TABLE` statement, `Col2` is a computed column that uses the XML data (`<Features>` element) that is returned by the function:</span></span>  
  
```  
CREATE TABLE T (Col1 xml, Col2 as dbo.my_udf(Col1) )  
-- Insert a row in table T.  
INSERT INTO T VALUES('  
<ProductDescription ProductModelID="1" >  
  <Features>  
    <Feature1>description</Feature1>  
    <Feature2>description</Feature2>  
  </Features>  
</ProductDescription>')  
-- Verify the results.  
SELECT *  
FROM T  
```  
  
### <a name="in-this-section"></a><span data-ttu-id="338c6-115">本节内容</span><span class="sxs-lookup"><span data-stu-id="338c6-115">In This Section</span></span>  
  
|<span data-ttu-id="338c6-116">主题</span><span class="sxs-lookup"><span data-stu-id="338c6-116">Topic</span></span>|<span data-ttu-id="338c6-117">说明</span><span class="sxs-lookup"><span data-stu-id="338c6-117">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="338c6-118">使用计算列提升常用的 XML 值</span><span class="sxs-lookup"><span data-stu-id="338c6-118">Promote Frequently Used XML Values with Computed Columns</span></span>](promote-frequently-used-xml-values-with-computed-columns.md)|<span data-ttu-id="338c6-119">介绍如何将属性提升用于计算列和属性表。</span><span class="sxs-lookup"><span data-stu-id="338c6-119">Describes how to use property promotion with computed columns and property tables.</span></span>|  
  
  
