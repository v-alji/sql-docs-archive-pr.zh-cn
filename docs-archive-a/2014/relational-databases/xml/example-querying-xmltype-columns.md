---
title: 示例：查询 XMLType 列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, querying XML example
ms.assetid: d9f3710d-7a2e-4abe-9c02-3e3c0df4d620
author: rothja
ms.author: jroth
ms.openlocfilehash: 0eedfa5a5a265f3715a76a6ca80d489bbec199bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577422"
---
# <a name="example-querying-xmltype-columns"></a><span data-ttu-id="c3b01-102">示例：查询 XMLType 列</span><span class="sxs-lookup"><span data-stu-id="c3b01-102">Example: Querying XMLType Columns</span></span>
  <span data-ttu-id="c3b01-103">下面的查询包括 `xml` 类型的列。</span><span class="sxs-lookup"><span data-stu-id="c3b01-103">The following query includes columns of `xml` type.</span></span> <span data-ttu-id="c3b01-104">该查询从 `xml` 类型的 `Instructions` 列的第一个位置检索产品型号 ID、名称和生产步骤。</span><span class="sxs-lookup"><span data-stu-id="c3b01-104">The query retrieves product model ID, name, and manufacturing steps at the first location from the `Instructions` column of the `xml` type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3b01-105">示例</span><span class="sxs-lookup"><span data-stu-id="c3b01-105">Example</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
')   
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData')  
GO  
```  
  
 <span data-ttu-id="c3b01-106">结果如下：</span><span class="sxs-lookup"><span data-stu-id="c3b01-106">The following is the result.</span></span> <span data-ttu-id="c3b01-107">注意，该表仅存储某些产品型号的生产说明。</span><span class="sxs-lookup"><span data-stu-id="c3b01-107">Note that the table stores manufacturing instructions for only some product models.</span></span> <span data-ttu-id="c3b01-108">在结果中，生产步骤作为 <`ProductModelData`> 元素的子元素返回。</span><span class="sxs-lookup"><span data-stu-id="c3b01-108">The manufacturing steps are returned as subelements of the <`ProductModelData`> element in the result.</span></span>  
  
```  
<ProductModelData ProductModelID="5" Name="HL Mountain Frame" />  
<ProductModelData ProductModelID="6" Name="HL Road Frame" />  
<ProductModelData ProductModelID="7" Name="HL Touring Frame">  
    <MI:step> ... </MI:step>  
    <MI:step> ... </MI:step>  
 </ProductModelData>  
```  
  
 <span data-ttu-id="c3b01-109">如果查询为 XQuery 返回的 XML 指定列名（如以下 `SELECT` 语句中所指定），则生产步骤将包含在具有指定名称的元素中。</span><span class="sxs-lookup"><span data-stu-id="c3b01-109">If the query specifies a column name for the XML returned by the XQuery, as specified in the following `SELECT` statement, the manufacturing steps are wrapped in the element that has the specified name.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
') as ManuSteps  
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData')  
go  
```  
  
 <span data-ttu-id="c3b01-110">结果如下：</span><span class="sxs-lookup"><span data-stu-id="c3b01-110">This is the result:</span></span>  
  
```  
<ProductModelData ProductModelID="5" Name="HL Mountain Frame" />  
<ProductModelData ProductModelID="6" Name="HL Road Frame" />  
<ProductModelData ProductModelID="7" Name="HL Touring Frame">  
  <ManuSteps>  
    <MI:step ... </MI:step>  
    <MI:step ... </MI:step>  
  </ManuSteps>  
</ProductModelData>  
```  
  
 <span data-ttu-id="c3b01-111">以下查询将指定 `ELEMENTS` 指令。</span><span class="sxs-lookup"><span data-stu-id="c3b01-111">The following query specifies the `ELEMENTS` directive.</span></span> <span data-ttu-id="c3b01-112">因此，返回的结果以元素为中心。</span><span class="sxs-lookup"><span data-stu-id="c3b01-112">Therefore, the result returned is element-centric.</span></span> <span data-ttu-id="c3b01-113">即使行集中的对应列为 NULL，与 `XSINIL` 指令一起指定的 `ELEMENTS` 选项仍可以返回 <`ManuSteps`> 元素。</span><span class="sxs-lookup"><span data-stu-id="c3b01-113">The `XSINIL` option specified with the `ELEMENTS` directive returns the <`ManuSteps`> elements, even if the corresponding column in the rowset is NULL.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
') as ManuSteps  
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData'), root('MyRoot'), ELEMENTS XSINIL  
go  
```  
  
 <span data-ttu-id="c3b01-114">结果如下：</span><span class="sxs-lookup"><span data-stu-id="c3b01-114">This is the result:</span></span>  
  
```  
<MyRoot xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
   ...  
  <ProductModelData>  
    <ProductModelID>6</ProductModelID>  
    <Name>HL Road Frame</Name>  
    <ManuSteps xsi:nil="true" />  
  </ProductModelData>  
  <ProductModelData>  
    <ProductModelID>7</ProductModelID>  
    <Name>HL Touring Frame</Name>  
    <ManuSteps>  
      <MI:step ... </MI:step>  
      <MI:step ...</MI:step>  
       ...  
    </ManuSteps>  
  </ProductModelData>  
</MyRoot>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3b01-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3b01-115">See Also</span></span>  
 [<span data-ttu-id="c3b01-116">将 RAW 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="c3b01-116">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
