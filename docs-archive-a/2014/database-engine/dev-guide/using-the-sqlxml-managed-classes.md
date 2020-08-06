---
title: 使用 SQLXML 托管类 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- sample applications [SQLXML]
- SQLXML Managed Classes, sample applications
- examples [SQLXML], managed classes
- Managed Classes [SQLXML], samples
ms.assetid: 3f021290-00ee-44e1-af4b-33d3ba8c6302
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 634a0e4110b13931201edd026ee95028cb94e859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690070"
---
# <a name="using-the-sqlxml-managed-classes"></a><span data-ttu-id="0c2f9-102">使用 SQLXML 托管类</span><span class="sxs-lookup"><span data-stu-id="0c2f9-102">Using the SQLXML Managed Classes</span></span>
  <span data-ttu-id="0c2f9-103">本部分提供了演示如何使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 托管类的示例应用程序。</span><span class="sxs-lookup"><span data-stu-id="0c2f9-103">This section provides sample applications that demonstrate how to use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML Managed Classes.</span></span>  
  
 <span data-ttu-id="0c2f9-104">有关访问和修改 .NET Framework 中的数据以及如何使用 Diffgram 更新表中的数据的信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅[在 .NET 环境中访问 SQLXML 功能](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="0c2f9-104">For information about accessing and modifying data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] within the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework, and about using DiffGrams to update data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables, see [Accessing SQLXML Functionality in the .NET Environment](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0c2f9-105">您还可以编写 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 应用程序，以便使用 XML 大容量加载对 XML 文档执行大容量加载。</span><span class="sxs-lookup"><span data-stu-id="0c2f9-105">You can also write [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio applications to bulk load XML documents by using XML Bulk Load.</span></span> <span data-ttu-id="0c2f9-106">有关详细信息，请参阅[&#40;SQLXML 4.0&#41;执行 XML 数据的大容量加载](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="0c2f9-106">For more information, see [Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md).</span></span> <span data-ttu-id="0c2f9-107">必须在应用程序中添加指向 XML 大容量加载 DLL (Xblkld4.dll) 的引用。</span><span class="sxs-lookup"><span data-stu-id="0c2f9-107">You must add a reference to the XML Bulk Load DLL (Xblkld4.dll) in your application.</span></span> <span data-ttu-id="0c2f9-108">Visual Studio .NET 将为此 COM DLL 自动创建包装库。</span><span class="sxs-lookup"><span data-stu-id="0c2f9-108">This is a COM DLL for which Visual Studio .NET automatically creates the wrapper library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0c2f9-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="0c2f9-109">In This Section</span></span>  
 [<span data-ttu-id="0c2f9-110">&#40;SQLXML 托管类执行 SQL 查询&#41;</span><span class="sxs-lookup"><span data-stu-id="0c2f9-110">Executing SQL Queries &#40;SQLXML Managed Classes&#41;</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md)  
  [<span data-ttu-id="0c2f9-111">使用 ExecuteXMLReader 方法执行 SQL 查询</span><span class="sxs-lookup"><span data-stu-id="0c2f9-111">Executing SQL Queries by Using the ExecuteXMLReader Method</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-by-using-the-executexmlreader-method.md)  
  [<span data-ttu-id="0c2f9-112">&#40;SQLXML 托管类在客户端处理 XML&#41;</span><span class="sxs-lookup"><span data-stu-id="0c2f9-112">Processing XML on the Client Side &#40;SQLXML Managed Classes&#41;</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/processing-xml-on-the-client-side-sqlxml-managed-classes.md)  
  [<span data-ttu-id="0c2f9-113">&#40;SQLXML 托管类执行 XPath 查询&#41;</span><span class="sxs-lookup"><span data-stu-id="0c2f9-113">Executing XPath Queries &#40;SQLXML Managed Classes&#41;</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-sqlxml-managed-classes.md)  
  [<span data-ttu-id="0c2f9-114">通过命名空间执行 XPath 查询 &#40;SQLXML 托管类&#41;</span><span class="sxs-lookup"><span data-stu-id="0c2f9-114">Executing XPath Queries with Namespaces &#40;SQLXML Managed Classes&#41;</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md)  
  [<span data-ttu-id="0c2f9-115">使用 CommandText 属性执行模板文件</span><span class="sxs-lookup"><span data-stu-id="0c2f9-115">Executing Template Files by Using the CommandText Property</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandtext-property.md)  
  [<span data-ttu-id="0c2f9-116">使用 CommandStream 属性执行模板文件</span><span class="sxs-lookup"><span data-stu-id="0c2f9-116">Executing Template Files by Using the CommandStream Property</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandstream-property.md)  
  [<span data-ttu-id="0c2f9-117">将 XSL 转换 &#40;SQLXML 托管类&#41;</span><span class="sxs-lookup"><span data-stu-id="0c2f9-117">Applying an XSL Transformation &#40;SQLXML Managed Classes&#41;</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/applying-an-xsl-transformation-sqlxml-managed-classes.md)  
  
