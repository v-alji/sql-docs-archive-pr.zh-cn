---
title: 列名为 XPath 节点测试的列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
- XPath node test
ms.assetid: b48adccd-3b6b-486a-b326-20f57170186f
author: rothja
ms.author: jroth
ms.openlocfilehash: 6555815d97308bed6e70d9fedb9858fc3abe7685
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688663"
---
# <a name="columns-with-the-name-of-an-xpath-node-test"></a><span data-ttu-id="1bfa7-102">列名为 XPath 节点测试的列</span><span class="sxs-lookup"><span data-stu-id="1bfa7-102">Columns with the Name of an XPath Node Test</span></span>
  <span data-ttu-id="1bfa7-103">如果列名是某个 XPath 节点测试，将如下表所示映射该列的内容。</span><span class="sxs-lookup"><span data-stu-id="1bfa7-103">If the column name is one of the XPath node tests, the content is mapped as shown in the following table.</span></span> <span data-ttu-id="1bfa7-104">如果列名是某个 XPath 节点测试，则该列的内容将映射到相应的节点。</span><span class="sxs-lookup"><span data-stu-id="1bfa7-104">When the column name is an XPath node test, the content is mapped to the corresponding node.</span></span> <span data-ttu-id="1bfa7-105">如果该列的 SQL 类型是 `xml`，将返回一个错误。</span><span class="sxs-lookup"><span data-stu-id="1bfa7-105">If the SQL type of the column is `xml`, an error is returned.</span></span>  
  
|<span data-ttu-id="1bfa7-106">列名</span><span class="sxs-lookup"><span data-stu-id="1bfa7-106">Column Name</span></span>|<span data-ttu-id="1bfa7-107">行为</span><span class="sxs-lookup"><span data-stu-id="1bfa7-107">Behavior</span></span>|  
|-----------------|--------------|  
|<span data-ttu-id="1bfa7-108">text()</span><span class="sxs-lookup"><span data-stu-id="1bfa7-108">text()</span></span>|<span data-ttu-id="1bfa7-109">对于名为 text() 的列，该列中的字符串值将被添加为文本节点。</span><span class="sxs-lookup"><span data-stu-id="1bfa7-109">For a column with the name of text(), the string value in that column is added as a text node.</span></span>|  
|<span data-ttu-id="1bfa7-110">comment()</span><span class="sxs-lookup"><span data-stu-id="1bfa7-110">comment()</span></span>|<span data-ttu-id="1bfa7-111">对于名为 comment() 的列，该列中的字符串值将被添加为 XML 注释。</span><span class="sxs-lookup"><span data-stu-id="1bfa7-111">For a column with the name of comment(), the string value in that column is added as an XML comment.</span></span>|  
|<span data-ttu-id="1bfa7-112">node()</span><span class="sxs-lookup"><span data-stu-id="1bfa7-112">node()</span></span>|<span data-ttu-id="1bfa7-113">对于名为 node() 的列，结果与列名为通配符 (\*) 时相同。</span><span class="sxs-lookup"><span data-stu-id="1bfa7-113">For a column with the name of node(), the result is the same as it is when the column name is a wildcard character (\*).</span></span>|  
|<span data-ttu-id="1bfa7-114">处理指令（名称）</span><span class="sxs-lookup"><span data-stu-id="1bfa7-114">processing-instruction(name)</span></span>|<span data-ttu-id="1bfa7-115">如果列名为处理指令，该列中的字符串值将被添加为此处理指令目标名称的 PI 值。</span><span class="sxs-lookup"><span data-stu-id="1bfa7-115">For a column with the name of a processing instruction, the string value in that column is added as the PI value for the processing instruction target name.</span></span>|  
  
 <span data-ttu-id="1bfa7-116">以下查询显示用作列名的节点测试。</span><span class="sxs-lookup"><span data-stu-id="1bfa7-116">The following query shows the use of the node tests as column names.</span></span> <span data-ttu-id="1bfa7-117">它在得到的 XML 中添加文本节点和注释。</span><span class="sxs-lookup"><span data-stu-id="1bfa7-117">It adds text nodes and comments in the resulting XML.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
        'Example of using node tests such as text(), comment(), processing-instruction()'                as "comment()",  
        'Some PI'                   as "processing-instruction(PI)",  
        'Employee name and address data' as "text()",  
        'middle name is optional'        as "EmpName/text()",  
        FirstName                        as "EmpName/First",   
        MiddleName                       as "EmpName/Middle",   
        LastName                         as "EmpName/Last",  
        AddressLine1                     as "Address/AddrLine1",  
        AddressLine2                     as "Address/AddrLIne2",  
        City                             as "Address/City"  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P   
    ON P.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.BusinessEntityAddress AS BAE  
    ON BAE.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.Address AS A  
    ON BAE.AddressID = A.AddressID  
WHERE  E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 <span data-ttu-id="1bfa7-118">结果如下：</span><span class="sxs-lookup"><span data-stu-id="1bfa7-118">This is the result:</span></span>  
  
 `<row EmpID="1">`  
  
 `<!--Example of using node tests such as text(), comment(), processing-instruction() -->`  
  
 `<?PI Some PI?>`  
  
 `Employee name and address data`  
  
 `<EmpName>middle name is optional`  
  
 `<First>Ken</First>`  
  
 `<Last>S??nchez</Last>`  
  
 `</EmpName>`  
  
 `<Address>`  
  
 `<AddrLine1>4350 Minute Dr.</AddrLine1>`  
  
 `<City>Minneapolis</City>`  
  
 `</Address>`  
  
 `</row>`  
  
## <a name="see-also"></a><span data-ttu-id="1bfa7-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1bfa7-119">See Also</span></span>  
 [<span data-ttu-id="1bfa7-120">将 PATH 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="1bfa7-120">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
