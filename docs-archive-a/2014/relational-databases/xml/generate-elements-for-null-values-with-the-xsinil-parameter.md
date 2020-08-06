---
title: 使用 XSINIL 参数生成 NULL 值对应的元素 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, null values
- null values [SQL Server], XML
- ELEMENTS directive
- XSINIL parameter
ms.assetid: 2dbc4e48-1cae-4d83-b371-3265da9687cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 602de12b5aa9be8997fbd49a2f23e0b73444aac0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694369"
---
# <a name="generate-elements-for-null-values-with-the-xsinil-parameter"></a><span data-ttu-id="5208b-102">使用 XSINIL 参数生成 NULL 值对应的元素</span><span class="sxs-lookup"><span data-stu-id="5208b-102">Generate Elements for NULL Values with the XSINIL Parameter</span></span>
  <span data-ttu-id="5208b-103">**ELEMENTS** 指令将构造 XML，其中每个列值映射到 XML 中的一个元素。</span><span class="sxs-lookup"><span data-stu-id="5208b-103">The **ELEMENTS** directive constructs XML in which each column value maps to an element in the XML.</span></span> <span data-ttu-id="5208b-104">如果列值为 NULL，则不添加元素。</span><span class="sxs-lookup"><span data-stu-id="5208b-104">If the column value is NULL, no element is added.</span></span> <span data-ttu-id="5208b-105">通过对 ELEMENTS 指令指定可选的 **XSINIL** 参数，可以请求创建 NULL 值对应的元素。</span><span class="sxs-lookup"><span data-stu-id="5208b-105">By specifying the optional **XSINIL** parameter on the ELEMENTS directive, you can request that an element also be created for the NULL value.</span></span> <span data-ttu-id="5208b-106">在这种情况下，将为每个 NULL 列值返回一个元素，其 **xsi:nil** 属性被设置为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="5208b-106">In this case, an element that has the **xsi:nil** attribute set to TRUE is returned for each NULL column value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5208b-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5208b-107">See Also</span></span>  
 [<span data-ttu-id="5208b-108">将 RAW 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="5208b-108">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
