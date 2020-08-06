---
title: 将 XSD 数据类型映射到 (SQLXML 4.0) 的 XPath 数据类型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping data types [SQLXML]
- data types [SQLXML], converting
- annotated XSD schemas, mapping data types
- XPath queries [SQLXML], mapping data types
- converting data types [SQLXML]
- data types [SQLXML], mapping data types
- XPath data types [SQLXML]
- XSD schemas [SQLXML], mapping data types
ms.assetid: ced1a95e-18d4-4a5a-8da8-dbb6d58bbd45
author: rothja
ms.author: jroth
ms.openlocfilehash: a4a3bd0b100dd935b5cea0d9ee4565633a9cb80e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590130"
---
# <a name="mapping-xsd-data-types-to-xpath-data-types-sqlxml-40"></a><span data-ttu-id="42c71-102">将 XSD 数据类型映射到 XPath 数据类型 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="42c71-102">Mapping XSD Data Types to XPath Data Types (SQLXML 4.0)</span></span>
  <span data-ttu-id="42c71-103">针对 XSD 架构执行 XPath 查询且在 `xsd:type` 属性中指定 XSD 类型时，XPath 使用它处理查询时指定的数据类型。</span><span class="sxs-lookup"><span data-stu-id="42c71-103">When an XPath query is executed against an XSD schema and the XSD type is specified in the `xsd:type` attribute, XPath uses the data type specified when it processes the query.</span></span>  
  
 <span data-ttu-id="42c71-104">节点的 XPath 数据类型从架构中的 XSD 数据类型派生，如下表中所示。</span><span class="sxs-lookup"><span data-stu-id="42c71-104">The XPath data type of a node is derived from the XSD data type in the schema, as shown in the following table.</span></span> <span data-ttu-id="42c71-105">（EmployeeID 节点用于演示目的。）</span><span class="sxs-lookup"><span data-stu-id="42c71-105">(The EmployeeID node is used for the purpose of illustration.)</span></span>  
  
|<span data-ttu-id="42c71-106">XSD 数据类型</span><span class="sxs-lookup"><span data-stu-id="42c71-106">XSD data type</span></span>|<span data-ttu-id="42c71-107">XDR 数据类型</span><span class="sxs-lookup"><span data-stu-id="42c71-107">XDR data type</span></span>|<span data-ttu-id="42c71-108">等效</span><span class="sxs-lookup"><span data-stu-id="42c71-108">Equivalent</span></span><br /><br /> <span data-ttu-id="42c71-109">XPath 数据类型</span><span class="sxs-lookup"><span data-stu-id="42c71-109">XPath data type</span></span>|<span data-ttu-id="42c71-110">SQL Server</span><span class="sxs-lookup"><span data-stu-id="42c71-110">SQL Server</span></span><br /><br /> <span data-ttu-id="42c71-111">使用的转换</span><span class="sxs-lookup"><span data-stu-id="42c71-111">conversion that is used</span></span>|  
|-------------------|-------------------|------------------------------------|--------------------------------------------|  
|`Base64Binary`<br /><br /> `HexBinary`|`None`<br /><br /> `bin.base64bin.hex`|`Not applicable`|<span data-ttu-id="42c71-112">无</span><span class="sxs-lookup"><span data-stu-id="42c71-112">None</span></span><br /><br /> <span data-ttu-id="42c71-113">EmployeeID</span><span class="sxs-lookup"><span data-stu-id="42c71-113">EmployeeID</span></span>|  
|`Boolean`|`boolean`|`boolean`|<span data-ttu-id="42c71-114">CONVERT(bit, EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="42c71-114">CONVERT(bit, EmployeeID)</span></span>|  
|`Decimal, integer, float, byte, short, int, long, float, double, unsignedByte, unsignedShort, unsignedInt, unsignedLong`|`number, int, float,i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8`|`number`|<span data-ttu-id="42c71-115">CONVERT(float(53), EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="42c71-115">CONVERT(float(53), EmployeeID)</span></span>|  
|`id, idref, idrefsentity, entities, notation, nmtoken, nmtokens, DateTime, string, AnyURI`|`id, idref, idrefsentity, entities, enumeration, notation, nmtoken, nmtokens, char, dateTime, dateTime.tz, string, uri, uuid`|`string`|<span data-ttu-id="42c71-116">CONVERT(nvarchar(4000), EmployeeID, 126)</span><span class="sxs-lookup"><span data-stu-id="42c71-116">CONVERT(nvarchar(4000), EmployeeID, 126)</span></span>|  
|`decimal`|`fixed14.4`|`Not applicable (There is no data type in XPath that is equivalent to the fixed14.4 XDR data type.)`|<span data-ttu-id="42c71-117">CONVERT(money, EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="42c71-117">CONVERT(money, EmployeeID)</span></span>|  
|`date`|`date`|`string`|<span data-ttu-id="42c71-118">LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)</span><span class="sxs-lookup"><span data-stu-id="42c71-118">LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)</span></span>|  
|`time`|`time`<br /><br /> `time.tz`|`string`|<span data-ttu-id="42c71-119">SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)</span><span class="sxs-lookup"><span data-stu-id="42c71-119">SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)</span></span>|  
  
  
