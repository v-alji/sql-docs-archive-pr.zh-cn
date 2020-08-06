---
title: 示例：指定 ID 和 IDREF 指令 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- IDREF directive
- ID directive
ms.assetid: 7ff1ea73-71ca-4786-bd42-564f1b5de2d9
author: rothja
ms.author: jroth
ms.openlocfilehash: 864acbbe55037f1760bbb0e62557e3e80d3628c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590091"
---
# <a name="example-specifying-the-id-and-idref-directives"></a><span data-ttu-id="751c2-102">示例：指定 ID 和 IDREF 指令</span><span class="sxs-lookup"><span data-stu-id="751c2-102">Example: Specifying the ID and IDREF Directives</span></span>
  <span data-ttu-id="751c2-103">此示例与 [指定 ELEMENTXSINIL 指令](example-specifying-the-elementxsinil-directive.md) 示例几乎相同。</span><span class="sxs-lookup"><span data-stu-id="751c2-103">This example is almost the same the [Specifying the ELEMENTXSINIL Directive](example-specifying-the-elementxsinil-directive.md) example.</span></span> <span data-ttu-id="751c2-104">唯一的差别在于查询指定的是 **ID** 和 **IDREF** 指令。</span><span class="sxs-lookup"><span data-stu-id="751c2-104">The only difference is that the query specifies the **ID** and **IDREF** directives.</span></span> <span data-ttu-id="751c2-105">这些指令覆盖 <`OrderHeader`> 和 <`OrderDetail`> 元素中 **SalesPersonID** 属性的类型。</span><span class="sxs-lookup"><span data-stu-id="751c2-105">These directives overwrite the types of the **SalesPersonID** attribute in the <`OrderHeader`> and <`OrderDetail`> elements.</span></span> <span data-ttu-id="751c2-106">这会形成文档内链接。</span><span class="sxs-lookup"><span data-stu-id="751c2-106">This forms intra-document links.</span></span> <span data-ttu-id="751c2-107">您需要使用架构才能查看被覆盖的类型。</span><span class="sxs-lookup"><span data-stu-id="751c2-107">You need the schema to see the overwritten types.</span></span> <span data-ttu-id="751c2-108">因此，该查询在 FOR XML 子句中指定 **XMLDATA** 选项来检索架构。</span><span class="sxs-lookup"><span data-stu-id="751c2-108">Therefore, the query specifies the **XMLDATA** option in the FOR XML clause to retrieve the schema.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        SalesOrderID  as [OrderHeader!1!SalesOrderID!id],  
        OrderDate     as [OrderHeader!1!OrderDate],  
        CustomerID    as [OrderHeader!1!CustomerID],  
        NULL          as [SalesPerson!2!SalesPersonID],  
        NULL          as [OrderDetail!3!SalesOrderID!idref],  
        NULL          as [OrderDetail!3!LineTotal],  
        NULL          as [OrderDetail!3!ProductID],  
        NULL          as [OrderDetail!3!OrderQty]  
FROM   Sales.SalesOrderHeader  
WHERE  SalesOrderID=43659 or SalesOrderID=43661  
UNION ALL   
SELECT 2 as Tag,  
       1 as Parent,  
        SalesOrderID,   
        NULL,  
        NULL,  
        SalesPersonID,    
        NULL,           
        NULL,           
        NULL,  
        NULL           
FROM   Sales.SalesOrderHeader  
WHERE  SalesOrderID=43659 or SalesOrderID=43661  
UNION ALL  
SELECT 3 as Tag,  
       1 as Parent,  
        SOD.SalesOrderID,  
        NULL,  
        NULL,  
        SalesPersonID,  
        SOH.SalesOrderID,  
        LineTotal,  
        ProductID,  
        OrderQty     
FROM    Sales.SalesOrderHeader SOH,Sales.SalesOrderDetail SOD  
WHERE   SOH.SalesOrderID = SOD.SalesOrderID  
AND     (SOH.SalesOrderID=43659 or SOH.SalesOrderID=43661)  
ORDER BY [OrderHeader!1!SalesOrderID!id], [SalesPerson!2!SalesPersonID],  
         [OrderDetail!3!SalesOrderID!idref],[OrderDetail!3!LineTotal]  
FOR XML EXPLICIT, XMLDATA  
```  
  
 <span data-ttu-id="751c2-109">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="751c2-109">This is the partial result.</span></span> <span data-ttu-id="751c2-110">请注意，在架构中，**ID** 和 **IDREF** 指令已经覆盖了 <`OrderHeader`> 和 <`OrderDetail`> 元素中 **SalesOrderID** 属性的数据类型。</span><span class="sxs-lookup"><span data-stu-id="751c2-110">In the schema, note that the **ID** and **IDREF** directives have overwritten the data types of the **SalesOrderID** attribute in the <`OrderHeader`> and <`OrderDetail`> elements.</span></span> <span data-ttu-id="751c2-111">如果删除这些指令，架构将返回这些属性的原始类型。</span><span class="sxs-lookup"><span data-stu-id="751c2-111">If you remove these directives, the schema returns original types of these attributes.</span></span>  
  
```  
<Schema name="Schema1" xmlns="urn:schemas-microsoft-com:xml-data" xmlns:dt="urn:schemas-microsoft-com:datatypes">  
  <ElementType name="OrderHeader" content="mixed" model="open">  
    <AttributeType name="SalesOrderID" dt:type="id" />  
    <AttributeType name="OrderDate" dt:type="dateTime" />  
    <AttributeType name="CustomerID" dt:type="i4" />  
    <attribute type="SalesOrderID" />  
    <attribute type="OrderDate" />  
    <attribute type="CustomerID" />  
  </ElementType>  
  <ElementType name="SalesPerson" content="mixed" model="open">  
    <AttributeType name="SalesPersonID" dt:type="i4" />  
    <attribute type="SalesPersonID" />  
  </ElementType>  
  <ElementType name="OrderDetail" content="mixed" model="open">  
    <AttributeType name="SalesOrderID" dt:type="idref" />  
    <AttributeType name="LineTotal" dt:type="number" />  
    <AttributeType name="ProductID" dt:type="i4" />  
    <AttributeType name="OrderQty" dt:type="i2" />  
    <attribute type="SalesOrderID" />  
    <attribute type="LineTotal" />  
    <attribute type="ProductID" />  
    <attribute type="OrderQty" />  
  </ElementType>  
</Schema>  
<OrderHeader xmlns="x-schema:#Schema1" SalesOrderID="43659" OrderDate="2001-07-01T00:00:00" CustomerID="676">  
  <SalesPerson SalesPersonID="279" />  
  <OrderDetail SalesOrderID="43659" LineTotal="10.373000" ProductID="712" OrderQty="2" />  
  ...  
</OrderHeader>  
...  
```  
  
## <a name="see-also"></a><span data-ttu-id="751c2-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="751c2-112">See Also</span></span>  
 [<span data-ttu-id="751c2-113">将 EXPLICIT 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="751c2-113">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
