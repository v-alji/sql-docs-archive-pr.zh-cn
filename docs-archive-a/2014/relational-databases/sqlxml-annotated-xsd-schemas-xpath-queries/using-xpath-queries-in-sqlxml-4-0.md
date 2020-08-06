---
title: 在 SQLXML 4.0 中使用 XPath 查询 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML]
- annotated XSD schemas, XPath queries
- queries [SQLXML], XPath
- XML views [SQLXML]
ms.assetid: 7814d099-81ec-4fb8-894a-729cdbb5015a
author: rothja
ms.author: jroth
ms.openlocfilehash: 80d82513b22d2a50aedb37955a210dd33746db86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588433"
---
# <a name="using-xpath-queries-in-sqlxml-40"></a><span data-ttu-id="9a413-102">在 SQLXML 4.0 中使用 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="9a413-102">Using XPath Queries in SQLXML 4.0</span></span>
  <span data-ttu-id="9a413-103">通过 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对带批注的 XSD 架构的支持，您可以对数据库中存储的关系数据创建 XML 视图。</span><span class="sxs-lookup"><span data-stu-id="9a413-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support for annotated XSD schemas allows you to create XML views of the relational data stored in the database.</span></span> <span data-ttu-id="9a413-104">您可以使用 XPath 语言的子集查询由带批注的 XSD 架构创建的 XML 视图。</span><span class="sxs-lookup"><span data-stu-id="9a413-104">You can use a subset of the XPath language to query the XML views created by an annotated XSD schema.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9a413-105">若要了解 SQLXML 4.0 中的 XPath 查询，必须熟悉 XML 视图和相关的概念，如模板和映射架构。</span><span class="sxs-lookup"><span data-stu-id="9a413-105">To understand XPath queries in SQLXML 4.0, you must be familiar with XML views and related concepts such as templates and mapping schema.</span></span> <span data-ttu-id="9a413-106">有关详细信息，请参阅[&#40;SQLXML 4.0&#41;中带批注的 XSD 架构简介](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="9a413-106">For more information, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md).</span></span> <span data-ttu-id="9a413-107">有关 XPath 的详细信息，请参阅万维网联合会 (W3C) 中定义的 XPath 标准 http://www.w3.org/TR/xpath 。</span><span class="sxs-lookup"><span data-stu-id="9a413-107">For more information about XPath, see the XPath standard defined by the World Wide Web Consortium (W3C) at http://www.w3.org/TR/xpath.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9a413-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="9a413-108">In This Section</span></span>  
 [<span data-ttu-id="9a413-109">&#40;SQLXML 4.0&#41;使用 XPath 查询简介</span><span class="sxs-lookup"><span data-stu-id="9a413-109">Introduction to Using XPath Queries &#40;SQLXML 4.0&#41;</span></span>](introduction-to-using-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="9a413-110">提供有关 SQLXML 4.0 中的 XPath 查询的介绍性信息，其中包括 W3C XPath 规范中支持和不支持的功能。</span><span class="sxs-lookup"><span data-stu-id="9a413-110">Provides introductory information about XPath queries in SQLXML 4.0, including supported and unsupported functionality from the W3C XPath specification.</span></span>  
  
 [<span data-ttu-id="9a413-111">&#40;SQLXML 4.0 指定位置路径&#41;</span><span class="sxs-lookup"><span data-stu-id="9a413-111">Specifying a Location Path &#40;SQLXML 4.0&#41;</span></span>](location-path/specifying-a-location-path-sqlxml-4-0.md)  
 <span data-ttu-id="9a413-112">介绍如何在 XPath 查询中指定位置路径。</span><span class="sxs-lookup"><span data-stu-id="9a413-112">Describes how to specify location paths in XPath queries.</span></span>  
  
 [<span data-ttu-id="9a413-113">&#40;SQLXML 4.0&#41;的示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="9a413-113">Sample XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/sample-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="9a413-114">提供 SQLXML 4.0 的示例 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="9a413-114">Provides sample XPath queries for SQLXML 4.0.</span></span>  
  
 [<span data-ttu-id="9a413-115">SQLXML 4.0 &#40;的 XPath 数据类型&#41;</span><span class="sxs-lookup"><span data-stu-id="9a413-115">XPath Data Types &#40;SQLXML 4.0&#41;</span></span>](xpath-data-types-sqlxml-4-0.md)  
 <span data-ttu-id="9a413-116">介绍与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 XSD 的数据类型有很大区别的 XPath 数据类型。</span><span class="sxs-lookup"><span data-stu-id="9a413-116">Describes XPath data types, which are significantly different from those of both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and XSD.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a413-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9a413-117">See Also</span></span>  
 [<span data-ttu-id="9a413-118">&#40;SQLXML 4.0&#41;的客户端 XML 格式</span><span class="sxs-lookup"><span data-stu-id="9a413-118">Client-side XML Formatting &#40;SQLXML 4.0&#41;</span></span>](../sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)  
  
  
