---
title: 将 value() 和 nodes() 方法用于 OPENXML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- OpenXML method [XML in SQL Server]
- value method [XML in SQL Server]
- nodes method [XML in SQL Server]
ms.assetid: c73dbe55-d685-42eb-b0ee-9f3c5b9d97f3
author: rothja
ms.author: jroth
ms.openlocfilehash: 5dccf5a7ef626d1f1a42d011d22ba77807b34eba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692289"
---
# <a name="use-the-value-and-nodes-methods-with-openxml"></a><span data-ttu-id="094f8-102">将 value() 和 nodes() 方法用于 OPENXML</span><span class="sxs-lookup"><span data-stu-id="094f8-102">Use the value() and nodes() Methods with OPENXML</span></span>
  <span data-ttu-id="094f8-103">您可以对 SELECT 子句中的数据类型使用多个**值 ( # B1**方法 `xml` ，以生成提取值的行集。 **SELECT**</span><span class="sxs-lookup"><span data-stu-id="094f8-103">You can use multiple **value()** methods on `xml` data type in a **SELECT** clause to generate a rowset of extracted values.</span></span> <span data-ttu-id="094f8-104">**nodes()** 方法为可用于其他查询的每个所选节点生成一个内部引用。</span><span class="sxs-lookup"><span data-stu-id="094f8-104">The **nodes()** method yields an internal reference for each selected node that can be used for additional query.</span></span> <span data-ttu-id="094f8-105">生成行集时，如果行集有多个列且用于生成行集的路径表达式比较复杂，结合使用 **nodes()** 和 **value()** 方法可能会更有效。</span><span class="sxs-lookup"><span data-stu-id="094f8-105">The combination of the **nodes()** and **value()** methods can be more efficient in generating the rowset when it has several columns and, perhaps, when the path expressions used in its generation are complex.</span></span>  
  
 <span data-ttu-id="094f8-106">**节点 ( # B1**方法生成特殊数据类型的实例 `xml` ，每个实例都将其上下文设置为不同的选定节点。</span><span class="sxs-lookup"><span data-stu-id="094f8-106">The **nodes()** method yields instances of a special `xml` data type, each of which has its context set to a different selected node.</span></span> <span data-ttu-id="094f8-107">这种 XML 实例支持 **query()** 、**value()** 、**nodes()** 和 **exist()** 方法，并可在 **count(\*)** 聚合中使用。</span><span class="sxs-lookup"><span data-stu-id="094f8-107">This kind of XML instance supports **query()**, **value()**, **nodes()**, and **exist()** methods and can be used in **count(\*)** aggregations.</span></span> <span data-ttu-id="094f8-108">所有其他用法都会导致错误。</span><span class="sxs-lookup"><span data-stu-id="094f8-108">All other uses cause an error.</span></span>  
  
## <a name="example-using-nodes"></a><span data-ttu-id="094f8-109">示例：使用 nodes()</span><span class="sxs-lookup"><span data-stu-id="094f8-109">Example: Using nodes()</span></span>  
 <span data-ttu-id="094f8-110">假定您希望提取作者的名字和姓氏，而名字不是“David”。</span><span class="sxs-lookup"><span data-stu-id="094f8-110">Assume that you want to extract the first and last names of authors, and the first name is not "David".</span></span> <span data-ttu-id="094f8-111">此外，您希望提取该信息作为一个包含两列 FirstName 和 LastName 的行集。</span><span class="sxs-lookup"><span data-stu-id="094f8-111">Additionally, you want to extract this information as a rowset that contains two columns, FirstName and LastName.</span></span> <span data-ttu-id="094f8-112">通过使用 **nodes()** 方法和 **value()** 方法便可以完成该操作，如下所示：</span><span class="sxs-lookup"><span data-stu-id="094f8-112">By using **nodes()** and **value()** methods, you can accomplish this as shown in the following:</span></span>  
  
```  
SELECT nref.value('(first-name/text())[1]', 'nvarchar(50)') FirstName,  
       nref.value('(last-name/text())[1]', 'nvarchar(50)') LastName  
FROM   T CROSS APPLY xCol.nodes('//author') AS R(nref)  
WHERE  nref.exist('first-name[. != "David"]') = 1  
```  
  
 <span data-ttu-id="094f8-113">在此示例中， `nodes('//author')` 生成一个由对每个 XML 实例的 `<author>` 元素引用组成的行集。</span><span class="sxs-lookup"><span data-stu-id="094f8-113">In this example, `nodes('//author')` yields a rowset of references to `<author>` elements for each XML instance.</span></span> <span data-ttu-id="094f8-114">通过计算与那些引用相关的 **value()** 方法，即可获得作者的名字和姓氏。</span><span class="sxs-lookup"><span data-stu-id="094f8-114">The first and last names of authors are obtained by evaluating **value()** methods relative to those references.</span></span>  
  
 <span data-ttu-id="094f8-115">SQL Server 2000 提供了通过使用 **OpenXml()** 从 XML 实例生成行集的功能。</span><span class="sxs-lookup"><span data-stu-id="094f8-115">SQL Server 2000 provides the capability for generating a rowset from an XML instance by using **OpenXml()**.</span></span> <span data-ttu-id="094f8-116">您可以指定行集的关系架构，以及如何将 XML 实例中的值映射到行集中的列。</span><span class="sxs-lookup"><span data-stu-id="094f8-116">You can specify the relational schema for the rowset and how values inside the XML instance map to columns in the rowset.</span></span>  
  
## <a name="example-using-openxml-on-the-xml-data-type"></a><span data-ttu-id="094f8-117">示例：对 xml 数据类型使用 OpenXml()</span><span class="sxs-lookup"><span data-stu-id="094f8-117">Example: Using OpenXml() on the xml Data Type</span></span>  
 <span data-ttu-id="094f8-118">可以通过使用 **OpenXml()** 重写上一个示例中的查询，如下所示。</span><span class="sxs-lookup"><span data-stu-id="094f8-118">The query can be rewritten from the previous example by using **OpenXml()** as shown in the following.</span></span> <span data-ttu-id="094f8-119">方法是创建一个游标，该游标将每个 XML 实例读取到 XML 变量，然后向其应用 OpenXML：</span><span class="sxs-lookup"><span data-stu-id="094f8-119">This is done by creating a cursor that reads each XML instance into an XML variable and then applies OpenXML to it:</span></span>  
  
```  
DECLARE name_cursor CURSOR  
FOR  
   SELECT xCol   
   FROM   T  
OPEN name_cursor  
DECLARE @xmlVal XML  
DECLARE @idoc int  
FETCH NEXT FROM name_cursor INTO @xmlVal  
  
WHILE (@@FETCH_STATUS = 0)  
BEGIN  
   EXEC sp_xml_preparedocument @idoc OUTPUT, @xmlVal  
   SELECT   *  
   FROM   OPENXML (@idoc, '//author')  
          WITH (FirstName  varchar(50) 'first-name',  
                LastName   varchar(50) 'last-name') R  
   WHERE  R.FirstName != 'David'  
  
   EXEC sp_xml_removedocument @idoc  
   FETCH NEXT FROM name_cursor INTO @xmlVal  
END  
CLOSE name_cursor  
DEALLOCATE name_cursor   
```  
  
 <span data-ttu-id="094f8-120">**OpenXml()** 创建一个内存中的表示形式，并且使用工作表而不是查询处理器。</span><span class="sxs-lookup"><span data-stu-id="094f8-120">**OpenXml()** creates an in-memory representation and uses work tables instead of the query processor.</span></span> <span data-ttu-id="094f8-121">它依赖于 MSXML 3.0 版的 XPath 1.0 版处理器，而不是 XQuery 引擎。</span><span class="sxs-lookup"><span data-stu-id="094f8-121">It relies on the XPath version 1.0 processor of MSXML version 3.0 instead of the XQuery engine.</span></span> <span data-ttu-id="094f8-122">工作表在对 **OpenXml()** 的多个调用间不共享（即使是在同一个 XML 实例上）。</span><span class="sxs-lookup"><span data-stu-id="094f8-122">The work tables are not shared among multiple calls to **OpenXml()**, even on the same XML instance.</span></span> <span data-ttu-id="094f8-123">这就限制了它的可伸缩性。</span><span class="sxs-lookup"><span data-stu-id="094f8-123">This limits its scalability.</span></span> <span data-ttu-id="094f8-124">在未指定 WITH 子句时，可以通过**OpenXml()** 访问 XML 数据的边缘表格式。</span><span class="sxs-lookup"><span data-stu-id="094f8-124">**OpenXml()** allows you to access an edge table format for the XML data when the WITH clause is not specified.</span></span> <span data-ttu-id="094f8-125">另外，也可以通过它在单独的“overflow”列中使用其余的 XML 值。</span><span class="sxs-lookup"><span data-stu-id="094f8-125">Also, it allows you to use the remaining XML value in a separate, "overflow" column.</span></span>  
  
 <span data-ttu-id="094f8-126">将 **nodes()** 和 **value()** 函数结合起来可有效地使用 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="094f8-126">The combination of **nodes()** and **value()** functions uses XML indexes effectively.</span></span> <span data-ttu-id="094f8-127">因此，与 **OpenXml**相比，这种结合有更高的可伸缩性。</span><span class="sxs-lookup"><span data-stu-id="094f8-127">As a result, this combination can exhibit more scalability than **OpenXml**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="094f8-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="094f8-128">See Also</span></span>  
 [<span data-ttu-id="094f8-129">OPENXML (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="094f8-129">OPENXML &#40;SQL Server&#41;</span></span>](openxml-sql-server.md)  
  
  
