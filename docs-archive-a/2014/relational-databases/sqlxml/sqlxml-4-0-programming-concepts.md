---
title: SQLXML 4.0 编程概念 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, about SQLXML
- SQLXML
ms.assetid: 5a11cda2-b8a3-4453-848f-641afdaa7024
author: rothja
ms.author: jroth
ms.openlocfilehash: 90a383d2a12e073f262d24a94abe1b094509713c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588404"
---
# <a name="sqlxml-40-programming-concepts"></a><span data-ttu-id="e5670-102">SQLXML 4.0 编程概念</span><span class="sxs-lookup"><span data-stu-id="e5670-102">SQLXML 4.0 Programming Concepts</span></span>
  <span data-ttu-id="e5670-103">SQLXML 3.0 作为 Web 版本提供，以提供附加客户端 XML 功能和现有功能的增强功能，例如带批注的 XSD 架构、XML 大容量加载、Web 服务 (SOAP) 支持和 updategram。</span><span class="sxs-lookup"><span data-stu-id="e5670-103">SQLXML 3.0 was offered as a Web release to provide additional client-side XML functionality and enhancements to existing features, such as annotated XSD schemas, XML bulk load, Web services (SOAP) support, and updategrams.</span></span>  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="e5670-104">引入了 SQLXML 4.0，它继续提供与 SQLXML 3.0 相同的功能，另外还提供附加的更新以接纳随 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 引入的新功能。</span><span class="sxs-lookup"><span data-stu-id="e5670-104">introduced SQLXML 4.0, which continues to deliver the same functionality as SQLXML 3.0 plus additional updates provided to accommodate new features introduced with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="e5670-105">本部分提供有关 SQLXML 4.0 的信息。</span><span class="sxs-lookup"><span data-stu-id="e5670-105">This section provides information about SQLXML 4.0.</span></span>  
  
 [<span data-ttu-id="e5670-106">SQL Server 中未安装 SQLXML</span><span class="sxs-lookup"><span data-stu-id="e5670-106">SQLXML Is Not Installed in SQL Server</span></span>](sqlxml-is-not-installed-in-sql-server.md)  
 <span data-ttu-id="e5670-107">说明如何安装 SQLXML 4.0。</span><span class="sxs-lookup"><span data-stu-id="e5670-107">Describes how to install SQLXML 4.0.</span></span>  
  
 [<span data-ttu-id="e5670-108">SQLXML 4.0 SP1 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="e5670-108">What's New in SQLXML 4.0 SP1</span></span>](what-s-new-in-sqlxml-4-0-sp1.md)  
 <span data-ttu-id="e5670-109">介绍 SQLXML 4.0 中的更新和增强功能，并提供指向本文档中相关主题的链接。</span><span class="sxs-lookup"><span data-stu-id="e5670-109">Describes the updates and enhancements in SQLXML 4.0, and provides links to relevant topics in this documentation.</span></span>  
  
 [<span data-ttu-id="e5670-110">使用 ADO 执行 SQLXML 4.0 查询</span><span class="sxs-lookup"><span data-stu-id="e5670-110">Using ADO to Execute SQLXML 4.0 Queries</span></span>](using-ado-to-execute-sqlxml-4-0-queries.md)  
 <span data-ttu-id="e5670-111">介绍如何将 ADO 用于 SQLXML 查询。</span><span class="sxs-lookup"><span data-stu-id="e5670-111">Describes how to use ADO for SQLXML queries.</span></span> <span data-ttu-id="e5670-112">相对以前版本而言，ADO 在 SQLXML 4.0 中更为重要。</span><span class="sxs-lookup"><span data-stu-id="e5670-112">ADO is more prominent in SQLXML 4.0 than in previous versions.</span></span>  
  
 [<span data-ttu-id="e5670-113">SQLXML 4.0 中的 xml 数据类型支持</span><span class="sxs-lookup"><span data-stu-id="e5670-113">xml Data Type Support in SQLXML 4.0</span></span>](xml-data-type-support-in-sqlxml-4-0.md)  
 <span data-ttu-id="e5670-114">介绍对 SQLXML 4.0 中新增的 xml 数据类型的支持。</span><span class="sxs-lookup"><span data-stu-id="e5670-114">Describes the support for the xml data type that has been added for SQLXML 4.0.</span></span>  
  
 [<span data-ttu-id="e5670-115">运行 SQLXML 示例的要求</span><span class="sxs-lookup"><span data-stu-id="e5670-115">Requirements for Running SQLXML Examples</span></span>](requirements-for-running-sqlxml-examples.md)  
 <span data-ttu-id="e5670-116">介绍从所提供的 SQLXML 示例创建工作示例的要求。</span><span class="sxs-lookup"><span data-stu-id="e5670-116">Describe the requirements for creating working samples from the SQLXML examples provided.</span></span>  
  
 [<span data-ttu-id="e5670-117">&#40;SQLXML 4.0&#41;的客户端和服务器端格式设置</span><span class="sxs-lookup"><span data-stu-id="e5670-117">Client-side and Server-side Formatting &#40;SQLXML 4.0&#41;</span></span>](formatting/client-side-and-server-side-formatting-sqlxml-4-0.md)  
 <span data-ttu-id="e5670-118">提供有关客户端和服务器端格式设置的信息以及二者的比较，包括用于构造 XML 文档的 FOR XML 命令。</span><span class="sxs-lookup"><span data-stu-id="e5670-118">Provides information about and comparisons of client-side and server-side formatting, including the FOR XML command for constructing XML documents.</span></span>  
  
 [<span data-ttu-id="e5670-119">SQLXML 4.0 中的带批注的 XSD 架构</span><span class="sxs-lookup"><span data-stu-id="e5670-119">Annotated XSD Schemas in SQLXML 4.0</span></span>](annotated-xsd-schemas/annotated-xsd-schemas-in-sqlxml-4-0.md)  
 <span data-ttu-id="e5670-120">提供有关使用 SQLXML 4.0 中带批注的 XSD 架构的信息。</span><span class="sxs-lookup"><span data-stu-id="e5670-120">Provides information about using annotated XSD schemas in SQLXML 4.0.</span></span> <span data-ttu-id="e5670-121">同时提供有关用于早期应用程序的带批注 XDR 架构的信息。</span><span class="sxs-lookup"><span data-stu-id="e5670-121">Also provides information about annotated XDR schemas for use in legacy applications.</span></span>  
  
 [<span data-ttu-id="e5670-122">在 SQLXML 4.0 中使用 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="e5670-122">Using XPath Queries in SQLXML 4.0</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/using-xpath-queries-in-sqlxml-4-0.md)  
 <span data-ttu-id="e5670-123">介绍如何使用 XPath 语言的子集查询由带批注的 XSD 架构创建的 XML 视图，并提供了示例。</span><span class="sxs-lookup"><span data-stu-id="e5670-123">Describes how to use a subset of the XPath language to query the XML views created by an annotated XSD schema, and provides examples.</span></span>  
  
 [<span data-ttu-id="e5670-124">使用 Updategram 修改 SQLXML 4.0 中的数据</span><span class="sxs-lookup"><span data-stu-id="e5670-124">Using Updategrams to Modify Data in SQLXML 4.0</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/using-updategrams-to-modify-data-in-sqlxml-4-0.md)  
 <span data-ttu-id="e5670-125">提供有关 updategram 的信息，它通过处理由带批注的 XSD（或 XDR）架构提供的 XML 视图来修改数据库中的数据。</span><span class="sxs-lookup"><span data-stu-id="e5670-125">Provides information about updategrams, which modify data in a database by working against the XML views provided by XSD (or XDR) annotated schemas.</span></span>  
  
 [<span data-ttu-id="e5670-126">对 XML 数据执行大容量加载 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e5670-126">Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)  
 <span data-ttu-id="e5670-127">介绍如何在 SQLXML 4.0 中大容量加载 XML。</span><span class="sxs-lookup"><span data-stu-id="e5670-127">Describes how to bulk load XML in SQLXML 4.0.</span></span>  
  
 [<span data-ttu-id="e5670-128">SQLXML 4.0 数据访问组件</span><span class="sxs-lookup"><span data-stu-id="e5670-128">SQLXML 4.0 Data Access Components</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/sqlxml-4-0-data-access-components-sqlxmloledb-provider.md)  
 <span data-ttu-id="e5670-129">提供 SQLXMLOLEDB 访问接口的说明，并提供指向其他 SQLXML 4.0 数据访问组件的链接。</span><span class="sxs-lookup"><span data-stu-id="e5670-129">Documents the SQLXMLOLEDB Provider and provides links to other SQLXML 4.0 data access components.</span></span>  
  
 [<span data-ttu-id="e5670-130">SQLXML 4.0 .NET Framework 支持</span><span class="sxs-lookup"><span data-stu-id="e5670-130">SQLXML 4.0 .NET Framework Support</span></span>](../../database-engine/dev-guide/sqlxml-4-0-net-framework-support.md)  
 <span data-ttu-id="e5670-131">介绍 SQLXML 4.0 对 .NET Framework 的支持。</span><span class="sxs-lookup"><span data-stu-id="e5670-131">Describes the SQLXML 4.0 support for the .NET Framework.</span></span>  
  
 [<span data-ttu-id="e5670-132">&#40;SQLXML 4.0&#41;缓存模板、XSL 和架构</span><span class="sxs-lookup"><span data-stu-id="e5670-132">Caching Templates, XSL, and Schemas &#40;SQLXML 4.0&#41;</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/caching-templates-xsl-and-schemas-sqlxml-4-0.md)  
 <span data-ttu-id="e5670-133">介绍在 SQLXML 中提供的用于提高性能的缓存功能。</span><span class="sxs-lookup"><span data-stu-id="e5670-133">Describes the caching functionality provided in SQLXML to improve performance.</span></span>  
  
 [<span data-ttu-id="e5670-134">SQLXML 4.0 安全注意事项</span><span class="sxs-lookup"><span data-stu-id="e5670-134">SQLXML 4.0 Security Considerations</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/security/sqlxml-4-0-security-considerations.md)  
 <span data-ttu-id="e5670-135">讨论与 SQLXML 4.0 相关的安全问题。</span><span class="sxs-lookup"><span data-stu-id="e5670-135">Discusses security issues relevant to SQLXML 4.0.</span></span>  
  
 [<span data-ttu-id="e5670-136">SQLXML 4.0 的准则和限制</span><span class="sxs-lookup"><span data-stu-id="e5670-136">Guidelines and Limitations of SQLXML 4.0</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/guidelines-and-limitations-of-sqlxml-4-0.md)  
 <span data-ttu-id="e5670-137">列出使用 SQLXML 4.0 时要记住的问题。</span><span class="sxs-lookup"><span data-stu-id="e5670-137">Lists issues to remember when working with SQLXML 4.0.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5670-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e5670-138">See Also</span></span>  
 [<span data-ttu-id="e5670-139">XML 数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e5670-139">XML Data &#40;SQL Server&#41;</span></span>](../xml/xml-data-sql-server.md)  
  
  
