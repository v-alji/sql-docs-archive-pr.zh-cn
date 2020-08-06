---
title: " (SQLXML 4.0) 执行 XML 数据的大容量加载 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XML Bulk Load [SQLXML]
- bulk load [SQLXML]
- data insertions [SQLXML]
- SQLXML, bulk loading
- XSD schemas [SQLXML], XML Bulk Load
- XDR schemas [SQLXML], XML Bulk Load
- inserting data
ms.assetid: 3708b493-322e-4f3c-9b27-441d0c0ee346
author: rothja
ms.author: jroth
ms.openlocfilehash: ec540ff082b02fa43b9abd9f294752073eb68d5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682781"
---
# <a name="performing-bulk-load-of-xml-data-sqlxml-40"></a><span data-ttu-id="34b5a-102">对 XML 数据执行大容量加载 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="34b5a-102">Performing Bulk Load of XML Data (SQLXML 4.0)</span></span>
  <span data-ttu-id="34b5a-103">XML 大容量加载是使您可以将半结构化 XML 数据加载到 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 表的独立 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="34b5a-103">XML Bulk Load is a standalone COM object that allows you to load semistructured XML data into Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="34b5a-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="34b5a-104">In This Section</span></span>  
 [<span data-ttu-id="34b5a-105">&#40;SQLXML 4.0&#41;的 XML 大容量加载简介</span><span class="sxs-lookup"><span data-stu-id="34b5a-105">Introduction to XML Bulk Load &#40;SQLXML 4.0&#41;</span></span>](introduction-to-xml-bulk-load-sqlxml-4-0.md)  
 <span data-ttu-id="34b5a-106">提供有关使用 XML 大容量加载实用工具对 XML 数据进行大容量加载的常规信息。</span><span class="sxs-lookup"><span data-stu-id="34b5a-106">Provides general information about bulk loading XML data with the XML Bulk Load utility.</span></span> <span data-ttu-id="34b5a-107">主题包括 XML 数据流以及事务和非事务大容量加载操作。</span><span class="sxs-lookup"><span data-stu-id="34b5a-107">Topics include XML data streaming and transacted vs. nontransacted bulk load operations.</span></span>  
  
 [<span data-ttu-id="34b5a-108">&#40;SQLXML 4.0&#41;的记录生成过程</span><span class="sxs-lookup"><span data-stu-id="34b5a-108">Record Generation Process &#40;SQLXML 4.0&#41;</span></span>](record-generation-process-sqlxml-4-0.md)  
 <span data-ttu-id="34b5a-109">介绍为 XML 大容量加载生成记录的过程和规则。</span><span class="sxs-lookup"><span data-stu-id="34b5a-109">Describes the process and rules by which records are generated for XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="34b5a-110">SQLXML 4.0 &#40;的批注解释&#41;</span><span class="sxs-lookup"><span data-stu-id="34b5a-110">Annotation Interpretation &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sqlxml-4-0.md)  
 <span data-ttu-id="34b5a-111">介绍 XML 大容量加载如何解释 XSD 和 XDR 架构中的批注。</span><span class="sxs-lookup"><span data-stu-id="34b5a-111">Describes how XML Bulk Load interprets annotations in XSD and XDR schemas.</span></span>  
  
 [<span data-ttu-id="34b5a-112">SQL Server XML 大容量加载对象模型 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="34b5a-112">SQL Server XML Bulk Load Object Model &#40;SQLXML 4.0&#41;</span></span>](sql-server-xml-bulk-load-object-model-sqlxml-4-0.md)  
 <span data-ttu-id="34b5a-113">描述 SQLXMLBulkLoad 对象及其方法和属性。</span><span class="sxs-lookup"><span data-stu-id="34b5a-113">Describes the SQLXMLBulkLoad object and its methods and properties.</span></span>  
  
 [<span data-ttu-id="34b5a-114">XML 大容量加载示例 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="34b5a-114">XML Bulk Load Examples &#40;SQLXML 4.0&#41;</span></span>](xml-bulk-load-examples-sqlxml-4-0.md)  
 <span data-ttu-id="34b5a-115">提供使用 XML 大容量加载的示例代码。</span><span class="sxs-lookup"><span data-stu-id="34b5a-115">Provides example code that uses XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="34b5a-116">数据类型和 XML 大容量加载行为 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="34b5a-116">Data Types and XML Bulk Load Behavior &#40;SQLXML 4.0&#41;</span></span>](data-types-and-xml-bulk-load-behavior-sqlxml-4-0.md)  
 <span data-ttu-id="34b5a-117">介绍 XML 大容量加载在 XSD 和 XDR 中的不同行为类型。</span><span class="sxs-lookup"><span data-stu-id="34b5a-117">Describes XML Bulk Load Behavior with different types in XSD and XDR.</span></span>  
  
 [<span data-ttu-id="34b5a-118">XML 大容量加载 &#40;SQLXML 4.0&#41;的准则和限制</span><span class="sxs-lookup"><span data-stu-id="34b5a-118">Guidelines and Limitations of XML Bulk Load &#40;SQLXML 4.0&#41;</span></span>](guidelines-and-limitations-of-xml-bulk-load-sqlxml-4-0.md)  
 <span data-ttu-id="34b5a-119">列出了使用 XML 大容量加载时应注意的一些问题。</span><span class="sxs-lookup"><span data-stu-id="34b5a-119">Lists some issues to be aware of when working with XML Bulk Load.</span></span>  
  
  
