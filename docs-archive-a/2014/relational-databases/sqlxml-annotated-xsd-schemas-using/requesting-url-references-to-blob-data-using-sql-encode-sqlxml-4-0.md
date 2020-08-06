---
title: 使用 sql：加码 (SQLXML 4.0) 时，请求对 BLOB 数据的 URL 引用 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:encode
- encode annotation
- URL references to BLOB data [SQLXML]
- references to BLOB data [SQLXML]
- annotated XSD schemas, URL references to BLOB data
- requesting URL references to BLOB data
- BLOBs, URL references
- Base 64-encoded format
ms.assetid: 2f8cd93b-c636-462b-8291-167197233ee0
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a9f5edcfab4a9d7307327d97bc2099c78c666c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590125"
---
# <a name="requesting-url-references-to-blob-data-using-sqlencode-sqlxml-40"></a><span data-ttu-id="5b0aa-102">使用 sql:encode 请求 BLOB 数据的 URL 引用 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="5b0aa-102">Requesting URL References to BLOB Data Using sql:encode (SQLXML 4.0)</span></span>
  <span data-ttu-id="5b0aa-103">在带批注的 XSD 架构中，将属性（或元素）映射为 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 BLOB 列时，将在 XML 中以 Base 64 编码格式返回数据。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-103">In an annotated XSD schema, when an attribute (or element) is mapped to a BLOB column in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the data is returned in Base 64-encoded format within XML.</span></span>  
  
 <span data-ttu-id="5b0aa-104">如果希望在稍后使用返回的数据引用 (URI) 来检索二进制格式的 BLOB 数据，请指定 `sql:encode` 批注。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-104">If you want a reference to the data (a URI) to be returned that can be used later to retrieve the BLOB data in a binary format, specify the `sql:encode` annotation.</span></span> <span data-ttu-id="5b0aa-105">您可以针对简单类型的属性或元素指定 `sql:encode`。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-105">You can specify `sql:encode` on an attribute or element of simple type.</span></span>  
  
 <span data-ttu-id="5b0aa-106">指定 `sql:encode` 批注以指示应返回字段的 URL，而非字段的值。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-106">Specify the `sql:encode` annotation to indicate that a URL to the field should be returned instead of the value of the field.</span></span> <span data-ttu-id="5b0aa-107">`sql:encode` 根据主键来在 URL 中生成单一选择。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-107">`sql:encode` depends on the primary key to generate a singleton select in the URL.</span></span> <span data-ttu-id="5b0aa-108">可以使用批注指定主键 `sql:key-fields` 。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-108">The primary key can be specified using the `sql:key-fields` annotation.</span></span>  
  
 <span data-ttu-id="5b0aa-109">可以为 `sql:encode` 批注分配“url”或“default”值。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-109">The `sql:encode` annotation can be assigned the "url" or the "default" value.</span></span> <span data-ttu-id="5b0aa-110">值为“default”将返回 Base 64 编码格式的数据。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-110">A value of "default" returns data in Base 64-encoded format.</span></span>  
  
 <span data-ttu-id="5b0aa-111">`sql:encode` 批注不能与 `sql:use-cdata` 一起使用，也不能用于 ID、IDREF、IDREFS、NMTOKEN 或 NMTOKENS 属性类型。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-111">The `sql:encode` annotation cannot be used with `sql:use-cdata` or on the ID, IDREF, IDREFS, NMTOKEN, or NMTOKENS attribute types.</span></span> <span data-ttu-id="5b0aa-112">它也不能用于 XSD**固定**属性。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-112">It can also not be used with XSD **fixed** attribute.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5b0aa-113">BLOB 类型的列不能用作键或外键的一部分。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-113">BLOB-type columns cannot be used as a part of a key or foreign key.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5b0aa-114">示例</span><span class="sxs-lookup"><span data-stu-id="5b0aa-114">Examples</span></span>  
 <span data-ttu-id="5b0aa-115">若要创建使用以下示例的工作示例，必须满足某些要求。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-115">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="5b0aa-116">有关详细信息，请参阅[运行 SQLXML 示例的要求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-116">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-sqlencode-to-obtain-a-url-reference-to-blob-data"></a><span data-ttu-id="5b0aa-117">A.</span><span class="sxs-lookup"><span data-stu-id="5b0aa-117">A.</span></span> <span data-ttu-id="5b0aa-118">指定 sql:encode 以获取对 BLOB 数据的 URL 引用</span><span class="sxs-lookup"><span data-stu-id="5b0aa-118">Specifying sql:encode to obtain a URL reference to BLOB data</span></span>  
 <span data-ttu-id="5b0aa-119">在此示例中，映射架构指定 `sql:encode` **LargePhoto**属性以检索对特定产品 (照片的 URI 引用，而不是检索以64编码格式) 的二进制数据。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-119">In this example, the mapping schema specifies `sql:encode` on the **LargePhoto** attribute to retrieve the URI reference to a specific product photo (instead of retrieving the binary data in Base 64-encoded format).</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="ProductPhoto" sql:relation="Production.ProductPhoto"   
               sql:key-fields="ProductPhotoID" >  
   <xsd:complexType>  
      <xsd:attribute name="ProductPhotoID"  type="xsd:int"  />  
     <xsd:attribute name="LargePhoto" type="xsd:string" sql:encode="url" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="5b0aa-120">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="5b0aa-120">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="5b0aa-121">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-121">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="5b0aa-122">将文件另存为 sqlEncode.xml。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-122">Save the file as sqlEncode.xml.</span></span>  
  
2.  <span data-ttu-id="5b0aa-123">复制以下模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-123">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="5b0aa-124">在保存 sqlEncode.xml 的相同目录中将该文件另存为 sqlEncodeT.xml。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-124">Save the file as sqlEncodeT.xml in the same directory where you saved sqlEncode.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sqlEncode.xml">  
            /ProductPhoto[@ProductPhotoID=100]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="5b0aa-125">为映射架构 (sqlEncode.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-125">The directory path specified for the mapping schema (sqlEncode.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="5b0aa-126">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="5b0aa-126">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\sqlEncode.xml"  
    ```  
  
3.  <span data-ttu-id="5b0aa-127">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-127">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="5b0aa-128">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="5b0aa-128">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="5b0aa-129">结果如下：</span><span class="sxs-lookup"><span data-stu-id="5b0aa-129">This is the result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <ProductPhoto ProductPhotoID="100"  
                 LargePhoto="dbobject/Production.ProductPhoto[@ProductPhotoID="100"]/@LargePhoto" />   
</ROOT>  
```  
  
  
