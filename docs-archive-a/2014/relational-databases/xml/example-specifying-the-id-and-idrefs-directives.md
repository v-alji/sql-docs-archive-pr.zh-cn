---
title: 示例：指定 ID 和 IDREFS 指令 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- IDREFS directive
- ID directive
ms.assetid: 99b9f0d8-ecbb-4225-859f-881066c09785
author: rothja
ms.author: jroth
ms.openlocfilehash: c21ba1bd19691014f179801421322970a3dd6dd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590090"
---
# <a name="example-specifying-the-id-and-idrefs-directives"></a><span data-ttu-id="b0b70-102">示例：指定 ID 和 IDREFS 指令</span><span class="sxs-lookup"><span data-stu-id="b0b70-102">Example: Specifying the ID and IDREFS Directives</span></span>
  <span data-ttu-id="b0b70-103">可以将元素属性指定为 `ID` 类型属性，然后就可以使用 `IDREFS` 属性来引用它。</span><span class="sxs-lookup"><span data-stu-id="b0b70-103">An element attribute can be specified as an `ID` type attribute, and the `IDREFS` attribute can then be used to refer to it.</span></span> <span data-ttu-id="b0b70-104">这将启用文档内链接，与关系数据库中主键和外键关系类似。</span><span class="sxs-lookup"><span data-stu-id="b0b70-104">This enables intra-document links and is similar to the primary key and foreign key relationships in relational databases.</span></span>  
  
 <span data-ttu-id="b0b70-105">此示例说明如何使用 `ID` 和 `IDREFS` 指令来创建 `ID` 和 `IDREFS` 类型的属性。</span><span class="sxs-lookup"><span data-stu-id="b0b70-105">This example illustrates how the `ID` and `IDREFS` directives can be used to create attributes of `ID` and `IDREFS` types.</span></span> <span data-ttu-id="b0b70-106">因为 ID 不能是整数值，所以对此示例中的 ID 值进行了转换。</span><span class="sxs-lookup"><span data-stu-id="b0b70-106">Because IDs cannot be integer values, the ID values in this example are converted.</span></span> <span data-ttu-id="b0b70-107">也就是说，它们进行了类型转换。</span><span class="sxs-lookup"><span data-stu-id="b0b70-107">In other words, they are type casted.</span></span> <span data-ttu-id="b0b70-108">ID 值中使用了前缀。</span><span class="sxs-lookup"><span data-stu-id="b0b70-108">Prefixes are used for the ID values.</span></span>  
  
 <span data-ttu-id="b0b70-109">假定要如下所示构造 XML：</span><span class="sxs-lookup"><span data-stu-id="b0b70-109">Assume that you want to construct XML as shown in the following:</span></span>  
  
```  
<Customer CustomerID="C1" SalesOrderIDList=" O11 O22 O33..." >  
    <SalesOrder SalesOrderID="O11" OrderDate="..." />  
    <SalesOrder SalesOrderID="O22" OrderDate="..." />  
    <SalesOrder SalesOrderID="O33" OrderDate="..." />  
    ...  
</Customer>  
```  
  
 <span data-ttu-id="b0b70-110">< `SalesOrderIDList` > 元素的 `Customer` 属性是一个多值属性，它引用 < `SalesOrderID` > 元素的 `SalesOrder` 属性。</span><span class="sxs-lookup"><span data-stu-id="b0b70-110">The `SalesOrderIDList` attribute of the < `Customer` > element is a multivalued attribute that refers to the `SalesOrderID` attribute of the < `SalesOrder` > element.</span></span> <span data-ttu-id="b0b70-111">若要建立此链接，必须将 `SalesOrderID` 属性声明为 `ID` 类型，并且必须将 < `Customer`> 元素的 `SalesOrderIDList` 属性声明为 `IDREFS` 类型。</span><span class="sxs-lookup"><span data-stu-id="b0b70-111">To establish this link, the `SalesOrderID` attribute must be declared of `ID` type, and the `SalesOrderIDList` attribute of the < `Customer`> element must be declared of `IDREFS` type.</span></span> <span data-ttu-id="b0b70-112">因为一个客户可请求多个订单，所以使用 `IDREFS` 类型。</span><span class="sxs-lookup"><span data-stu-id="b0b70-112">Because a customer can request several orders, the `IDREFS` type is used.</span></span>  
  
 <span data-ttu-id="b0b70-113">`IDREFS` 类型的元素也有多个值。</span><span class="sxs-lookup"><span data-stu-id="b0b70-113">Elements of `IDREFS` type also have more than one value.</span></span> <span data-ttu-id="b0b70-114">因此，必须使用单独的 SELECT 子句来重复使用相同的标记、父级和键列信息。</span><span class="sxs-lookup"><span data-stu-id="b0b70-114">Therefore, you have to use a separate select clause that will reuse the same tag, parent, and key column information.</span></span> <span data-ttu-id="b0b70-115">然后，`ORDER BY` 必须确保组成 `IDREFS` 值的行的序列成组显示在它们的父元素下。</span><span class="sxs-lookup"><span data-stu-id="b0b70-115">The `ORDER BY` then has to ensure that the sequence of rows that make up the `IDREFS` values appears grouped together under their parent element.</span></span>  
  
 <span data-ttu-id="b0b70-116">下面是生成所需的 XML 的查询。</span><span class="sxs-lookup"><span data-stu-id="b0b70-116">This is the query that produces the XML you want.</span></span> <span data-ttu-id="b0b70-117">该查询使用 `ID` 和 `IDREFS` 指令来覆盖列名称（`SalesOrder!2!SalesOrderID!ID`、 `Customer!1!SalesOrderIDList!IDREFS`）中的类型。</span><span class="sxs-lookup"><span data-stu-id="b0b70-117">The query uses the `ID` and `IDREFS` directives to overwrite the types in the column names (`SalesOrder!2!SalesOrderID!ID`, `Customer!1!SalesOrderIDList!IDREFS`).</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        C.CustomerID       [Customer!1!CustomerID],  
        NULL               [Customer!1!SalesOrderIDList!IDREFS],  
        NULL               [SalesOrder!2!SalesOrderID!ID],  
        NULL               [SalesOrder!2!OrderDate]  
FROM   Sales.Customer C   
UNION ALL   
SELECT  1 as Tag,  
        0 as Parent,  
        C.CustomerID,  
        'O-'+CAST(SalesOrderID as varchar(10)),   
        NULL,  
        NULL  
FROM   Sales.Customer AS C  
INNER JOIN Sales.SalesOrderHeader AS SOH  
    ON  C.CustomerID = SOH.CustomerID  
UNION ALL  
SELECT 2 as Tag,  
       1 as Parent,  
        C.CustomerID,  
        NULL,  
        'O-'+CAST(SalesOrderID as varchar(10)),  
        OrderDate  
FROM   Sales.Customer AS C  
INNER JOIN Sales.SalesOrderHeader AS SOH  
    ON  C.CustomerID = SOH.CustomerIDORDER BY [Customer!1!CustomerID] ,  
         [SalesOrder!2!SalesOrderID!ID],  
         [Customer!1!SalesOrderIDList!IDREFS]  
FOR XML EXPLICIT;  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0b70-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b0b70-118">See Also</span></span>  
 [<span data-ttu-id="b0b70-119">将 EXPLICIT 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="b0b70-119">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
