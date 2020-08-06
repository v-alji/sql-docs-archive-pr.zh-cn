---
title: 数据类型和 XML 大容量加载行为 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 34b03423f3bb88166d0d9ce5b0df450d4455e7ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588449"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a><span data-ttu-id="8814b-102">数据类型和 XML 大容量加载行为 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="8814b-102">Data Types and XML Bulk Load Behavior (SQLXML 4.0)</span></span>
  <span data-ttu-id="8814b-103">一般忽略在映射架构中指定的数据类型（XSD 或 XDR 类型以及 `sql:datatype`），但是以下情况除外：</span><span class="sxs-lookup"><span data-stu-id="8814b-103">The data types that are specified in the mapping schema (XSD or XDR type and `sql:datatype`) are generally ignored, except in the following cases:</span></span>  
  
 <span data-ttu-id="8814b-104">在 XSD 中：</span><span class="sxs-lookup"><span data-stu-id="8814b-104">In XSD:</span></span>  
  
-   <span data-ttu-id="8814b-105">如果类型为 `dateTime` 或 `time`，必须指定 `sql:datatype`，因为 XML 大容量加载在将数据发送到 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 前会执行数据转换。</span><span class="sxs-lookup"><span data-stu-id="8814b-105">If the type is `dateTime` or `time`, you must specify the `sql:datatype` because XML Bulk Load performs data conversion before sending the data to Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="8814b-106">如果要大容量加载到类型的列 `uniqueidentifier` 中 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，并且 XSD 值是包含大括号 ( {and} ) 的 GUID，则必须指定**sql： datatype = "uniqueidentifier"** 才能在将值插入列之前删除大括号。</span><span class="sxs-lookup"><span data-stu-id="8814b-106">When you are bulk loading into a column of `uniqueidentifier` type in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and the XSD value is a GUID that includes braces ({ and }), you must specify **sql:datatype="uniqueidentifier"** to remove the braces before the value is inserted into the column.</span></span> <span data-ttu-id="8814b-107">如果未指定 `sql:datatype`，将发送包含大括号的值并且插入失败。</span><span class="sxs-lookup"><span data-stu-id="8814b-107">If `sql:datatype` is not specified, the value is sent with the braces and the insert fails.</span></span>  
  
 <span data-ttu-id="8814b-108">有关的详细信息 `sql:datatype` ，请参阅[数据类型强制转换和 sql： datatype 批注 &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="8814b-108">For more information about `sql:datatype`, see [Data Type Coercions and the sql:datatype Annotation &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="8814b-109">在 XDR 中：</span><span class="sxs-lookup"><span data-stu-id="8814b-109">In XDR:</span></span>  
  
-   <span data-ttu-id="8814b-110">如果 `dt:type` 为 `datetime`、`time`、`dateTime.tz` 或 `time.tz`，必须同时指定 `dt:type` 和 `sql:datatype` 数据类型，因为 XML 大容量加载在将数据发送到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 前会执行数据转换。</span><span class="sxs-lookup"><span data-stu-id="8814b-110">If the `dt:type` is `datetime`, `time`, `dateTime.tz`, or `time.tz`, you must specify both the `dt:type` and `sql:datatype` data types because XML Bulk Load performs data conversion before it sends the data to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="8814b-111">如果 XML 数据的类型为 `uuid` ， `sql:datatype` 则必须指定;**dt： type = "uuid"** 也是必需的，除非数据是字符串数据。</span><span class="sxs-lookup"><span data-stu-id="8814b-111">If your XML data is of type `uuid`, `sql:datatype` must be specified; **dt:type="uuid"** is also required, unless the data is string data.</span></span> <span data-ttu-id="8814b-112">如果未指定 `dt:uuid`，XML 大容量加载将接受包含大括号的字符串（并根据需要删除大括号）。</span><span class="sxs-lookup"><span data-stu-id="8814b-112">If you do not specify `dt:uuid`, XML Bulk Load accepts strings with braces (and removes them if needed).</span></span>  
  
-   <span data-ttu-id="8814b-113">如果 XML 数据为 `bin.base64` 或 `bin.hex`，必须使用 `dt:type` 指定 XML 数据类型。</span><span class="sxs-lookup"><span data-stu-id="8814b-113">If the XML data is `bin.base64` or `bin.hex`, you must specify the XML data type with `dt:type`.</span></span> <span data-ttu-id="8814b-114">XML 大容量加载然后将数据以十六进制形式加载到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8814b-114">XML Bulk Load then loads the data into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as a hexadecimal representation of the data.</span></span>  
  
  
