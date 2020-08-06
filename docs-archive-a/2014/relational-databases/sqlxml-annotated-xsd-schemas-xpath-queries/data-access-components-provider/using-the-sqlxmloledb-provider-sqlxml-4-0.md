---
title: 使用 SQLXMLOLEDB 提供程序 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sample applications [SQLXML]
- SQLXMLOLEDB Provider, samples
- ClientSideXML property
ms.assetid: fbcefac5-29c9-478b-b0e0-d510b593f446
author: rothja
ms.author: jroth
ms.openlocfilehash: 74e3c53eecd657d610c2fe90e108e0290e9b05b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587302"
---
# <a name="using-the-sqlxmloledb-provider-sqlxml-40"></a><span data-ttu-id="23d11-102">使用 SQLXMLOLEDB 访问接口 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="23d11-102">Using the SQLXMLOLEDB Provider (SQLXML 4.0)</span></span>
  <span data-ttu-id="23d11-103">本节中的主题提供 ADO 示例应用程序，这些应用程序说明 SQLXMLOLEDB 访问接口特有的属性的用法。</span><span class="sxs-lookup"><span data-stu-id="23d11-103">The topics in this section provide ADO sample applications that illustrate the use of SQLXMLOLEDB Provider-specific properties.</span></span>  
  
## <a name="application-requirements-for-sqlxmloledb-40-provider"></a><span data-ttu-id="23d11-104">SQLXMLOLEDB 4.0 访问接口的应用程序要求</span><span class="sxs-lookup"><span data-stu-id="23d11-104">Application Requirements for SQLXMLOLEDB 4.0 Provider</span></span>  
 <span data-ttu-id="23d11-105">若要创建使用 SQLXMLOLEDB 4.0 的工作示例，必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="23d11-105">To create working samples that use SQLXMLOLEDB 4.0, you must do the following:</span></span>  
  
1.  <span data-ttu-id="23d11-106">创建 Microsoft Visual Basic .exe 应用程序，并添加以下引用之一：</span><span class="sxs-lookup"><span data-stu-id="23d11-106">Create a Microsoft Visual Basic .exe application and add one of the following references:</span></span>  
  
    -   <span data-ttu-id="23d11-107">Microsoft ActiveX 数据对象2.6 库</span><span class="sxs-lookup"><span data-stu-id="23d11-107">Microsoft ActiveX Data Objects 2.6 Library</span></span>  
  
    -   <span data-ttu-id="23d11-108">Microsoft ActiveX 数据对象2.7 库</span><span class="sxs-lookup"><span data-stu-id="23d11-108">Microsoft ActiveX Data Objects 2.7 Library</span></span>  
  
    -   <span data-ttu-id="23d11-109">Microsoft ActiveX Data Objects 2.8 Library</span><span class="sxs-lookup"><span data-stu-id="23d11-109">Microsoft ActiveX Data Objects 2.8 Library</span></span>  
  
2.  <span data-ttu-id="23d11-110">部署和安装 SQLXML 4.0 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="23d11-110">Deploy and install SQLXML 4.0 and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
     <span data-ttu-id="23d11-111">有关详细信息，请参阅[SQLXML 4.0 编程概念](../../sqlxml/sqlxml-4-0-programming-concepts.md)和[安装 SQL Server Native Client](../../native-client/applications/installing-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="23d11-111">For more information, see on [SQLXML 4.0 Programming Concepts](../../sqlxml/sqlxml-4-0-programming-concepts.md) and [Installing SQL Server Native Client](../../native-client/applications/installing-sql-server-native-client.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="23d11-112">本节内容</span><span class="sxs-lookup"><span data-stu-id="23d11-112">In This Section</span></span>  
 [<span data-ttu-id="23d11-113">&#40;SQLXMLOLEDB 提供程序执行 SQL 查询&#41;</span><span class="sxs-lookup"><span data-stu-id="23d11-113">Executing SQL Queries &#40;SQLXMLOLEDB Provider&#41;</span></span>](executing-sql-queries-sqlxmloledb-provider.md)  
 <span data-ttu-id="23d11-114">说明如何使用 ClientSideXML 和 xml 根属性来执行 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="23d11-114">Illustrates the use of the ClientSideXML and xml root properties to execute SQL queries.</span></span>  
  
 [<span data-ttu-id="23d11-115">&#40;SQLXMLOLEDB 提供程序执行包含 SQL 查询的模板&#41;</span><span class="sxs-lookup"><span data-stu-id="23d11-115">Executing Templates That Contain SQL Queries &#40;SQLXMLOLEDB Provider&#41;</span></span>](executing-templates-that-contain-sql-queries-sqlxmloledb-provider.md)  
 <span data-ttu-id="23d11-116">说明如何使用 ClientSideXML 属性。</span><span class="sxs-lookup"><span data-stu-id="23d11-116">Illustrates the use of the ClientSideXML property.</span></span>  
  
 [<span data-ttu-id="23d11-117">&#40;SQLXMLOLEDB 提供程序执行 XPath 查询&#41;</span><span class="sxs-lookup"><span data-stu-id="23d11-117">Executing XPath Queries &#40;SQLXMLOLEDB Provider&#41;</span></span>](executing-xpath-queries-sqlxmloledb-provider.md)  
 <span data-ttu-id="23d11-118">阐释 ClientSideXML、基路径和映射架构属性的用法。</span><span class="sxs-lookup"><span data-stu-id="23d11-118">Illustrates the use of the ClientSideXML, Base Path, and Mapping Schema properties.</span></span>  
  
 [<span data-ttu-id="23d11-119">通过命名空间 &#40;SQLXMLOLEDB 提供程序执行 XPath 查询&#41;</span><span class="sxs-lookup"><span data-stu-id="23d11-119">Executing XPath Queries with Namespaces &#40;SQLXMLOLEDB Provider&#41;</span></span>](executing-xpath-queries-with-namespaces-sqlxmloledb-provider.md)  
 <span data-ttu-id="23d11-120">说明如何针对已限定命名空间的架构进行查询。</span><span class="sxs-lookup"><span data-stu-id="23d11-120">Illustrates how to query against namespace-qualified schemas.</span></span>  
  
 [<span data-ttu-id="23d11-121">&#40;SQLXMLOLEDB 提供程序执行包含 XPath 查询的模板&#41;</span><span class="sxs-lookup"><span data-stu-id="23d11-121">Executing Templates That Contain XPath Queries &#40;SQLXMLOLEDB Provider&#41;</span></span>](executing-templates-that-contain-xpath-queries-sqlxmloledb-provider.md)  
 <span data-ttu-id="23d11-122">说明如何使用 ClientSideXML、基路径和映射架构属性执行包含 SQL 查询的模板。</span><span class="sxs-lookup"><span data-stu-id="23d11-122">Illustrates how to execute templates with SQL queries using the ClientSideXML, Base Path, and Mapping Schema properties.</span></span>  
  
 [<span data-ttu-id="23d11-123">&#40;SQLXMLOLEDB 提供程序应用 XSL 转换&#41;</span><span class="sxs-lookup"><span data-stu-id="23d11-123">Applying an XSL Transformation &#40;SQLXMLOLEDB Provider&#41;</span></span>](applying-an-xsl-transformation-sqlxmloledb-provider.md)  
 <span data-ttu-id="23d11-124">说明如何使用 ClientSideXML 和 xsl 属性来应用 XSL 转换。</span><span class="sxs-lookup"><span data-stu-id="23d11-124">Illustrates the use of the ClientSideXML and xsl properties in applying an XSL transformation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23d11-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="23d11-125">See Also</span></span>  
 [<span data-ttu-id="23d11-126">SQL Server Native Client 的系统要求</span><span class="sxs-lookup"><span data-stu-id="23d11-126">System Requirements for SQL Server Native Client</span></span>](../../native-client/system-requirements-for-sql-server-native-client.md)  
  
  
