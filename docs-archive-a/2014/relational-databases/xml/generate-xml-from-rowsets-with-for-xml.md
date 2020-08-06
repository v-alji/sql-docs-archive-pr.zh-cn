---
title: 使用 FOR XML 从行集生成 XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, generating XML from rowsets
ms.assetid: d061c0f1-3de9-4ad1-bbca-ce45d064b6c8
author: rothja
ms.author: jroth
ms.openlocfilehash: dcf9feb4dab9ad1149ab433c9d9b4999c96c1cdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694367"
---
# <a name="generate-xml-from-rowsets-with-for-xml"></a><span data-ttu-id="182e9-102">使用 FOR XML 从行集生成 XML</span><span class="sxs-lookup"><span data-stu-id="182e9-102">Generate XML from Rowsets with FOR XML</span></span>
  <span data-ttu-id="182e9-103">可以 `xml` 通过将 FOR XML 与新的**type**指令一起使用，从行集生成数据类型实例。</span><span class="sxs-lookup"><span data-stu-id="182e9-103">You can generate an `xml` data type instance from a rowset by using FOR XML with the new **TYPE** directive.</span></span>  
  
 <span data-ttu-id="182e9-104">可以将结果分配给 `xml` 数据类型列、变量或参数。</span><span class="sxs-lookup"><span data-stu-id="182e9-104">The result can be assigned to an `xml` data type column, variable, or parameter.</span></span> <span data-ttu-id="182e9-105">同样，可以嵌套 FOR XML 以生成任意层次结构。</span><span class="sxs-lookup"><span data-stu-id="182e9-105">Also, FOR XML can be nested to generate any hierarchical structure.</span></span> <span data-ttu-id="182e9-106">这使嵌套的 FOR XML 在编写上比 FOR XML EXPLICIT 更为方便，但是对于深层次的结构，它的执行效果不如后者。</span><span class="sxs-lookup"><span data-stu-id="182e9-106">This makes nested FOR XML much more convenient to write than FOR XML EXPLICIT, but it may not perform as well for deep hierarchies.</span></span> <span data-ttu-id="182e9-107">FOR XML 还引入了新的 PATH 模式。</span><span class="sxs-lookup"><span data-stu-id="182e9-107">FOR XML also introduces a new PATH mode.</span></span> <span data-ttu-id="182e9-108">这个新模式指定某个列的值在 XML 树中的路径。</span><span class="sxs-lookup"><span data-stu-id="182e9-108">This new mode specifies the path in the XML tree where a column's value appears.</span></span>  
  
 <span data-ttu-id="182e9-109">可以使用新的 **FOR XML TYPE** 指令，采用 SQL 语法来定义关系数据上的只读 XML 视图。</span><span class="sxs-lookup"><span data-stu-id="182e9-109">The new **FOR XML TYPE** directive can be used to define read-only XML views over relational data with SQL syntax.</span></span> <span data-ttu-id="182e9-110">可以使用 SQL 语句和嵌入式 XQuery 查询该视图，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="182e9-110">The view can be queried with SQL statements and embedded XQuery, as shown in the following example.</span></span> <span data-ttu-id="182e9-111">另外，您还可以在存储过程中引用这些 SQL 视图。</span><span class="sxs-lookup"><span data-stu-id="182e9-111">You can also refer to these SQL views in stored procedures.</span></span>  
  
## <a name="example-sql-view-returning-generated-xml-data-type"></a><span data-ttu-id="182e9-112">示例：返回生成的 xml 数据类型的 SQL 视图</span><span class="sxs-lookup"><span data-stu-id="182e9-112">Example: SQL View Returning Generated xml Data Type</span></span>  
 <span data-ttu-id="182e9-113">以下 SQL 视图定义对关系列 pk 和从 XML 列中检索到的书作者创建 XML 视图：</span><span class="sxs-lookup"><span data-stu-id="182e9-113">The following SQL view definition creates an XML view over a relational column, pk, and book authors retrieved from an XML column:</span></span>  
  
```  
CREATE VIEW V (xmlVal) AS  
SELECT pk, xCol.query('/book/author')  
FROM   T  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="182e9-114">视图中的 Columnxmlvalt 包含单一的 XML 类型的行， `.` 它可以像常规 `xml` 数据类型实例一样进行查询。</span><span class="sxs-lookup"><span data-stu-id="182e9-114">The V view contains a single row with a single columnxmlVal of XML type`.` It can be queried like a regular `xml` data type instance.</span></span> <span data-ttu-id="182e9-115">例如，下面的查询返回名字为“David”的作者：</span><span class="sxs-lookup"><span data-stu-id="182e9-115">For example, the following query returns the author whose first name is "David":</span></span>  
  
```  
SELECT xmlVal.query('//author[first-name = "David"]')  
FROM   V  
```  
  
 <span data-ttu-id="182e9-116">SQL 视图定义与使用带批注的架构创建的 XML 视图有些相似。</span><span class="sxs-lookup"><span data-stu-id="182e9-116">SQL view definitions are somewhat similar to XML views that are created by using annotated schemas.</span></span> <span data-ttu-id="182e9-117">但二者之间存在重要的差异。</span><span class="sxs-lookup"><span data-stu-id="182e9-117">However, there are important differences.</span></span> <span data-ttu-id="182e9-118">SQL 视图定义是只读的，且必须使用嵌入式 XQuery 来操作。</span><span class="sxs-lookup"><span data-stu-id="182e9-118">The SQL view definition is read-only and must be manipulated with embedded XQuery.</span></span> <span data-ttu-id="182e9-119">XML 视图是通过使用带批注的架构创建的。</span><span class="sxs-lookup"><span data-stu-id="182e9-119">The XML views are created by using annotated schema.</span></span> <span data-ttu-id="182e9-120">此外，SQL 视图在应用 XQuery 表达式之前具体化 XML 结果，而对 XML 视图的 XPath 查询是对基础表计算 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="182e9-120">Additionally, the SQL view materializes the XML result before applying the XQuery expression, while the XPath queries on XML views evaluate SQL queries on the underlying tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="182e9-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="182e9-121">See Also</span></span>  
 [<span data-ttu-id="182e9-122">FOR XML (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="182e9-122">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
