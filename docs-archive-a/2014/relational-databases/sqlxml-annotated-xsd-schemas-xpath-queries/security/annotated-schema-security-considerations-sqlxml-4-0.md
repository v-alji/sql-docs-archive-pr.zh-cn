---
title: " (SQLXML 4.0) 的批注的架构安全注意事项 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping schema [SQLXML], security
- annotated XDR schemas, security
- XDR schemas [SQLXML], security
- annotations [SQLXML]
- annotated XSD schemas, security
- SQLXML, annotated XSD schemas
- SQLXML, annotated XDR schemas
- security [SQLXML], annotated schemas
- XSD schemas [SQLXML], security
ms.assetid: 7d7e44dc-b6d3-4e0f-95c7-8f99930c94f2
author: rothja
ms.author: jroth
ms.openlocfilehash: 098f554410a846ed0223d17117b51025dfcf7897
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577466"
---
# <a name="annotated-schema-security-considerations-sqlxml-40"></a><span data-ttu-id="2d108-102">带批注的架构的安全注意事项 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="2d108-102">Annotated Schema Security Considerations (SQLXML 4.0)</span></span>
  <span data-ttu-id="2d108-103">以下是在使用带批注的架构时应遵循的安全准则：</span><span class="sxs-lookup"><span data-stu-id="2d108-103">The following are security guidelines for using annotated schemas:</span></span>  
  
-   <span data-ttu-id="2d108-104">避免在映射架构中使用默认映射。</span><span class="sxs-lookup"><span data-stu-id="2d108-104">Avoid using default mapping in the mapping schemas.</span></span> <span data-ttu-id="2d108-105">默认映射会在生成的 XML 文档中公开数据库信息（表和列名），因为在默认情况下元素名映射为表名而属性名则映射为列名。</span><span class="sxs-lookup"><span data-stu-id="2d108-105">The default mapping exposes the database information (table and column names) in the resulting XML document because, by default, the element names map to table names and attribute names map to column names.</span></span> <span data-ttu-id="2d108-106">因此，能够查看该 XML 文档的任何用户都可以获得数据库中表和列的相关信息，从而带来潜在的安全风险。</span><span class="sxs-lookup"><span data-stu-id="2d108-106">Therefore, any user who sees the XML document has access to the table and column information in the database, presenting a potential security risk.</span></span> <span data-ttu-id="2d108-107">若要避免此风险，请在架构中指定随意的元素名和属性名并使用批注将它们显式映射到表和列。</span><span class="sxs-lookup"><span data-stu-id="2d108-107">To avoid this risk, specify arbitrary element and attribute names in the schema and use annotations to explicitly map them to the tables and columns.</span></span> <span data-ttu-id="2d108-108">若要详细了解如何在创建 XSD 架构时使用默认映射，请参阅[&#40;SQLXML 4.0&#41;的 Xsd 元素和属性到表和列的默认映射](../../sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="2d108-108">For more information about using default mapping when you create XSD schemas, see [Default Mapping of XSD Elements and Attributes to Tables and Columns &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="2d108-109">使用批注指定的显式映射公开数据库信息（如表名和列名）。</span><span class="sxs-lookup"><span data-stu-id="2d108-109">The explicit mapping specified using the annotations exposes the database information (such as table names and column names).</span></span> <span data-ttu-id="2d108-110">因此，最好不要让这些架构能够公开使用。</span><span class="sxs-lookup"><span data-stu-id="2d108-110">Therefore, you may not want to make these schemas available publicly.</span></span>  
  
-   <span data-ttu-id="2d108-111">某些查询的执行时间可能较长，例如针对具有递归的映射架构指定的查询（使用设置为较高值的 `max-depth` 批注进行指定）。</span><span class="sxs-lookup"><span data-stu-id="2d108-111">Certain queries such as those specified against mapping schema with recursion (specified using `max-depth` annotation set to a higher value) may take longer to execute.</span></span> <span data-ttu-id="2d108-112">您可以选择指定超时限制，方法是将命令超时属性设置 (以秒为单位) 。</span><span class="sxs-lookup"><span data-stu-id="2d108-112">You can optionally specify a time-out limit by setting the Command Time Out property (in seconds).</span></span> <span data-ttu-id="2d108-113">例如：</span><span class="sxs-lookup"><span data-stu-id="2d108-113">For example:</span></span>  
  
    ```  
    cn.Open "Provider=SQLOLEDB;Server=localhost;Database=tempdb;Integrated Security=SSPI;Command Properties='Command Time Out=50';"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2d108-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2d108-114">See Also</span></span>  
 [<span data-ttu-id="2d108-115">SQLXML 4.0 中的带批注的 XSD 架构</span><span class="sxs-lookup"><span data-stu-id="2d108-115">Annotated XSD Schemas in SQLXML 4.0</span></span>](../../sqlxml/annotated-xsd-schemas/annotated-xsd-schemas-in-sqlxml-4-0.md)  
  
  
