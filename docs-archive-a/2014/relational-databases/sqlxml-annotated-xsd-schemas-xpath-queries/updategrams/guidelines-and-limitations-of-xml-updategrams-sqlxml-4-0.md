---
title: XML Updategram (SQLXML 4.0) 的准则和限制 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updategrams [SQLXML], about updategrams
ms.assetid: b5231859-14e2-4276-bc17-db2817b6f235
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e01e366edc2889691862de639f69220ac4bb439
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689802"
---
# <a name="guidelines-and-limitations-of-xml-updategrams-sqlxml-40"></a><span data-ttu-id="cdfbc-102">XML Updategram 的指导原则和限制 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="cdfbc-102">Guidelines and Limitations of XML Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="cdfbc-103">在使用 XML updategram 时，请记住以下事项：</span><span class="sxs-lookup"><span data-stu-id="cdfbc-103">Remember the following when using XML updategrams:</span></span>  
  
-   <span data-ttu-id="cdfbc-104">如果将 updategram 用于只包含一对和块的插入操作 **\<before>** **\<after>** ，则 **\<before>** 可以省略块。</span><span class="sxs-lookup"><span data-stu-id="cdfbc-104">If you are using an updategram for an insert operation with only a single pair of **\<before>** and **\<after>** blocks, the **\<before>** block can be omitted.</span></span> <span data-ttu-id="cdfbc-105">相反，如果是删除操作，则 **\<after>** 可以省略块。</span><span class="sxs-lookup"><span data-stu-id="cdfbc-105">Conversely, in case of a delete operation, the **\<after>** block can be omitted.</span></span>  
  
-   <span data-ttu-id="cdfbc-106">如果在标记中使用具有多个 **\<before>** 和 **\<after>** 块的 updategram **\<sync>** ，则 **\<before>** **\<after>** 必须指定块和块以形成 **\<before>** 和 **\<after>** 配对。</span><span class="sxs-lookup"><span data-stu-id="cdfbc-106">If you are using an updategram with multiple **\<before>** and **\<after>** blocks in the **\<sync>** tag, both **\<before>** blocks and **\<after>** blocks must be specified to form **\<before>** and **\<after>** pairs.</span></span>  
  
-   <span data-ttu-id="cdfbc-107">updategram 中的更新适用于 XML 架构提供的 XML 视图。</span><span class="sxs-lookup"><span data-stu-id="cdfbc-107">The updates in an updategram are applied to the XML view that is provided by the XML schema.</span></span> <span data-ttu-id="cdfbc-108">因此，为使默认映射成功，必须在 updategram 中指定架构文件名；或者，如果未提供文件名，则元素名称和属性名称必须匹配数据库中的表名和列名。</span><span class="sxs-lookup"><span data-stu-id="cdfbc-108">Therefore, for the default mapping to succeed either you must specify the schema file name in the updategram or, if the file name is not provided, the element and attribute names must match the table and column names in the database.</span></span>  
  
-   <span data-ttu-id="cdfbc-109">SQLXML 4.0 要求 updategram 中的所有列值都必须显式映射在提供的架构（XDR 或 XSD）中，以便为其子元素编写 XML 视图。</span><span class="sxs-lookup"><span data-stu-id="cdfbc-109">SQLXML 4.0 requires that all column values in an updategram must be explicitly mapped in the schema (either XDR or XSD) provided to compose the XML view for its child elements.</span></span> <span data-ttu-id="cdfbc-110">此行为不同于 SQLXML 的早期版本，这些版本允许架构中未映射的列值（如果它表示为 `sql:relationship` 批注中外键的一部分）。</span><span class="sxs-lookup"><span data-stu-id="cdfbc-110">This behavior differs from earlier versions of SQLXML, which allowed a value for a column not mapped in the schema if it was implied as part of the foreign Key in a `sql:relationship` annotation.</span></span> <span data-ttu-id="cdfbc-111">请注意，这一变化并不影响主键值传播到子元素，如果没有为子元素显式指定值，则对于 SQLXML 4.0，主键值仍会传播到子元素。</span><span class="sxs-lookup"><span data-stu-id="cdfbc-111">(Note that this change does not affect propagation of primary key values to child elements, which still occurs for SQLXML 4.0 if no value is explicitly specified for the child element.</span></span>  
  
-   <span data-ttu-id="cdfbc-112">如果使用 updategram 来修改二进制列中的数据 (如 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `image` 数据类型) ，则必须提供一个映射架构 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，其中数据类型 (，例如 `sql:datatype="image"`) 和 XML 数据类型 (， `dt:type="binhex"` 或者 `dt:type="binbase64` 必须指定) 。</span><span class="sxs-lookup"><span data-stu-id="cdfbc-112">If you are using an updategram to modify data in a binary column (such as the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `image` data type), you must provide a mapping schema in which the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type (for example, `sql:datatype="image"`) and the XML data type (for example, `dt:type="binhex"` or `dt:type="binbase64`) must be specified.</span></span> <span data-ttu-id="cdfbc-113">必须在 updategram 中指定二进制列的数据；updategram 将忽略在映射架构中指定的 `sql:url-encode` 批注。</span><span class="sxs-lookup"><span data-stu-id="cdfbc-113">The data for the binary column must be specified in the updategram; the `sql:url-encode` annotation that is specified in the mapping schema is ignored by the updategram.</span></span>  
  
-   <span data-ttu-id="cdfbc-114">在您撰写某一 XSD 架构时，如果为 `sql:relation` 或 `sql:field` 批注指定的值包括特殊字符，例如空格字符（如“Order Details”表名称中的空格），则该值必须用括号括起来（例如“[Order Details]”）。</span><span class="sxs-lookup"><span data-stu-id="cdfbc-114">When you are writing an XSD schema, if the value you specify for the `sql:relation` or `sql:field` annotation includes a special character, such as a space character (for example, in the "Order Details" table name), this value must be enclosed in brackets (for example, "[Order Details]").</span></span>  
  
-   <span data-ttu-id="cdfbc-115">在使用 updategram 时，不支持链关系。</span><span class="sxs-lookup"><span data-stu-id="cdfbc-115">When using updategrams, chain relationships are not supported.</span></span> <span data-ttu-id="cdfbc-116">例如，如果表 A 和 C 通过使用表 B 的链关系相关，则在尝试运行和执行 updategram 时将发生以下错误：</span><span class="sxs-lookup"><span data-stu-id="cdfbc-116">For example, if tables A and C are related through a chain relationship that uses table B, the following error will occur when attempting to run and execute the updategram:</span></span>  
  
    ```  
    There is an inconsistency in the schema provided.  
    ```  
  
     <span data-ttu-id="cdfbc-117">即使架构和 updategram 均正确并且有效建立，但如果存在某一链关系，此错误仍将发生。</span><span class="sxs-lookup"><span data-stu-id="cdfbc-117">Even if both schema and updategram are otherwise correct and validly formed, this error will occur if a chain relationship is present.</span></span>  
  
-   <span data-ttu-id="cdfbc-118">Updategram 不允许在更新期间将 `image` 类型数据作为参数传递。</span><span class="sxs-lookup"><span data-stu-id="cdfbc-118">Updategrams do not permit the passing of `image` type data as parameters during updates.</span></span>  
  
-   <span data-ttu-id="cdfbc-119">当使用 updategram 时，不应在块中将二进制大型对象 (BLOB) 类型（如 `text/ntext` 和 **\<before>** ），因为这将包含它们以用于并发控制。</span><span class="sxs-lookup"><span data-stu-id="cdfbc-119">Binary large object (BLOB) types like `text/ntext` and images should not be used in the **\<before>** block in when working with updategrams, because this will include them for use in concurrency control.</span></span> <span data-ttu-id="cdfbc-120">由于 BLOB 类型的比较限制，这可能导致 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 出现问题。</span><span class="sxs-lookup"><span data-stu-id="cdfbc-120">This can cause problems with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] because of the limitations on comparison for BLOB types.</span></span> <span data-ttu-id="cdfbc-121">例如，在 WHERE 子句中使用 LIKE 关键字比较 `text` 数据类型的列；不过，对于数据大小大于 8K 的 BLOB 类型，比较将失败。</span><span class="sxs-lookup"><span data-stu-id="cdfbc-121">For example, the LIKE keyword is used in the WHERE clause for comparing between columns of the `text` data type; however, comparisons will fail in the case of BLOB types where the size of the data is greater than 8K.</span></span>  
  
-   <span data-ttu-id="cdfbc-122">由于 BLOB 类型的比较限制，`ntext` 数据中的特殊字符可能导致 SQLXML 4.0 出现问题。</span><span class="sxs-lookup"><span data-stu-id="cdfbc-122">Special characters in `ntext` data can cause problems with SQLXML 4.0 because of the limitations on comparison for BLOB types.</span></span> <span data-ttu-id="cdfbc-123">例如，在对类型的列进行并发检查时，在 updategram 块中使用 "[Serializable]" **\<before>** `ntext` 会失败，并出现以下 SQLOLEDB 错误说明：</span><span class="sxs-lookup"><span data-stu-id="cdfbc-123">For example, the use of "[Serializable]" in the **\<before>** block of an updategrams when used in concurrency checking of a column of `ntext` type will fail with the following SQLOLEDB error description:</span></span>  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cdfbc-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cdfbc-124">See Also</span></span>  
 [<span data-ttu-id="cdfbc-125">&#40;SQLXML 4.0&#41;的 Updategram 安全注意事项</span><span class="sxs-lookup"><span data-stu-id="cdfbc-125">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
