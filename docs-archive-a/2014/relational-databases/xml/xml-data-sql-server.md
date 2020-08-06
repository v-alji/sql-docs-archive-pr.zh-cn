---
title: XML 数据 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XML [SQL Server]
- XML [SQL Server], about XML
ms.assetid: 6a1793c9-9856-485c-aac5-88fda62f61a8
author: rothja
ms.author: jroth
ms.openlocfilehash: 48ddec1de8492c86aecfd80ea960c4a01673c24f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578743"
---
# <a name="xml-data-sql-server"></a><span data-ttu-id="1bc80-102">XML 数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1bc80-102">XML Data (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1bc80-103">提供了一个强大的平台，以针对半结构化数据管理开发功能丰富的应用程序。</span><span class="sxs-lookup"><span data-stu-id="1bc80-103">provides a powerful platform for developing rich applications for semi-structured data management.</span></span> <span data-ttu-id="1bc80-104">对 XML 的支持已集成到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的所有组件中，包括下面几项：</span><span class="sxs-lookup"><span data-stu-id="1bc80-104">Support for XML is integrated into all the components in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and includes the following:</span></span>  
  
-   <span data-ttu-id="1bc80-105">`xml` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="1bc80-105">The `xml` data type.</span></span> <span data-ttu-id="1bc80-106">可将 XML 值本机存储在根据 XML 架构集合类型化或保持非类型化的 `xml` 数据类型列中。</span><span class="sxs-lookup"><span data-stu-id="1bc80-106">XML values can be stored natively in an `xml` data type column that can be typed according to a collection of XML schemas, or left untyped.</span></span> <span data-ttu-id="1bc80-107">可为 XML 列编制索引。</span><span class="sxs-lookup"><span data-stu-id="1bc80-107">You can index the XML column.</span></span>  
  
-   <span data-ttu-id="1bc80-108">可以指定针对 `xml` 类型的列和变量中存储的 XML 数据的 XQuery 查询。</span><span class="sxs-lookup"><span data-stu-id="1bc80-108">The ability to specify an XQuery query against XML data stored in columns and variables of the `xml` type.</span></span>  
  
-   <span data-ttu-id="1bc80-109">增强了 OPENROWSET 以允许大容量加载 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="1bc80-109">Enhancements to OPENROWSET to allow bulk loading of XML data.</span></span>  
  
-   <span data-ttu-id="1bc80-110">FOR XML 子句，用于检索 XML 格式的关系数据。</span><span class="sxs-lookup"><span data-stu-id="1bc80-110">The FOR XML clause, to retrieve relational data in XML format.</span></span>  
  
-   <span data-ttu-id="1bc80-111">OPENXML 函数，用于检索关系格式的 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="1bc80-111">The OPENXML function, to retrieve XML data in relational format.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1bc80-112">本节内容</span><span class="sxs-lookup"><span data-stu-id="1bc80-112">In This Section</span></span>  
 [<span data-ttu-id="1bc80-113">XML 数据类型和列 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1bc80-113">XML Data Type and Columns &#40;SQL Server&#41;</span></span>](xml-data-type-and-columns-sql-server.md)  
 [<span data-ttu-id="1bc80-114">XML 索引 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1bc80-114">XML Indexes &#40;SQL Server&#41;</span></span>](xml-indexes-sql-server.md)  
 [<span data-ttu-id="1bc80-115">XML 架构集合 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1bc80-115">XML Schema Collections &#40;SQL Server&#41;</span></span>](xml-schema-collections-sql-server.md)  
 [<span data-ttu-id="1bc80-116">FOR XML (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1bc80-116">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
 [<span data-ttu-id="1bc80-117">OPENXML (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1bc80-117">OPENXML &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/openxml-transact-sql)  
  
## <a name="related-content"></a><span data-ttu-id="1bc80-118">相关内容</span><span class="sxs-lookup"><span data-stu-id="1bc80-118">Related Content</span></span>  
 [<span data-ttu-id="1bc80-119">批量导入和导出 XML 文档的示例 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1bc80-119">Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;</span></span>](../import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
 [<span data-ttu-id="1bc80-120">XQuery 语言参考 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1bc80-120">XQuery Language Reference &#40;SQL Server&#41;</span></span>](/sql/xquery/xquery-language-reference-sql-server)  
  
