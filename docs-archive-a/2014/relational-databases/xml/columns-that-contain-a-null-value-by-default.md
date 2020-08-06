---
title: 默认情况下包含 Null 值的列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- columns [XML in SQL Server], null default value
ms.assetid: 9381c07f-6887-4a62-9730-32661f9aa87c
author: rothja
ms.author: jroth
ms.openlocfilehash: 92ea51101f73695be2075a1b41deb62ca021f496
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577428"
---
# <a name="columns-that-contain-a-null-value-by-default"></a><span data-ttu-id="01ef2-102">默认情况下包含 Null 值的列</span><span class="sxs-lookup"><span data-stu-id="01ef2-102">Columns that Contain a Null Value By Default</span></span>
  <span data-ttu-id="01ef2-103">默认情况下，列中的 Null 值映射为“缺少相应的属性、节点或元素”。</span><span class="sxs-lookup"><span data-stu-id="01ef2-103">By default, a null value in a column maps to the absence of the attribute, node, or element.</span></span> <span data-ttu-id="01ef2-104">通过使用 ELEMENTS 指令请求以元素为中心的 XML 并指定 XSINIL 来请求为 NULL 值添加元素，可以覆盖此默认行为，如以下查询所示：</span><span class="sxs-lookup"><span data-stu-id="01ef2-104">This default behavior can be overwritten by requesting element-centric XML using the ELEMENTS directive and specifying XSINIL to request adding elements for NULL values, as shown in the following query:</span></span>  
  
```  
SELECT EmployeeID as "@EmpID",   
       FirstName  as "EmpName/First",   
       MiddleName as "EmpName/Middle",   
       LastName   as "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH, ELEMENTS XSINIL  
```  
  
 <span data-ttu-id="01ef2-105">下面显示了结果。</span><span class="sxs-lookup"><span data-stu-id="01ef2-105">The following shows the result.</span></span> <span data-ttu-id="01ef2-106">请注意，如果未指定 XSINIL，将缺少 <`Middle`> 元素。</span><span class="sxs-lookup"><span data-stu-id="01ef2-106">Note that if XSINIL is not specified, the <`Middle`> element will be absent.</span></span>  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## <a name="see-also"></a><span data-ttu-id="01ef2-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="01ef2-107">See Also</span></span>  
 [<span data-ttu-id="01ef2-108">将 PATH 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="01ef2-108">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
