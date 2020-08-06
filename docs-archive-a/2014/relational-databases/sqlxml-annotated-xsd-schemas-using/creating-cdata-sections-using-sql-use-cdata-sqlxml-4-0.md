---
title: 使用 sql： use-CDATA (SQLXML 4.0) 创建 CDATA 节 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- markup characters [SQLXML]
- special characters [SQLXML]
- use-cdata annotation
- plain text [SQLXML]
- CDATA sections
- escaping blocks of text [SQLXML]
- annotated XSD schemas, CDATA sections
- sql:use-cdata
ms.assetid: 26d2b9dc-f857-44ff-bcd4-aaf64ff809d0
author: rothja
ms.author: jroth
ms.openlocfilehash: c0ba0787efbda400590a75f0f3529e3df8819e41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590133"
---
# <a name="creating-cdata-sections-using-sqluse-cdata-sqlxml-40"></a><span data-ttu-id="43dd8-102">使用 sql:use-cdata 创建 CDATA 节 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="43dd8-102">Creating CDATA Sections Using sql:use-cdata (SQLXML 4.0)</span></span>
  <span data-ttu-id="43dd8-103">在 XML 中，CDATA 节用于对那些所含字符不转义则会识别为标记字符的特定文本块进行转义。</span><span class="sxs-lookup"><span data-stu-id="43dd8-103">In XML, CDATA sections are used to escape blocks of text that contain characters that would otherwise be recognized as markup characters.</span></span>  
  
 <span data-ttu-id="43dd8-104">Microsoft 中的数据库 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 有时可以包含由 XML 分析器视为标记字符的字符; 例如，尖括号 (\< and >) ，小于或等于符号 ( # B0 =) ，and 号 ( # A1) 被视为标记字符。</span><span class="sxs-lookup"><span data-stu-id="43dd8-104">A database in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can sometimes contain characters that are treated as markup characters by the XML parser; for example, angle brackets (\< and >), the less-than-or-equal-to symbol (<=), and the ampersand (&) are treated as markup characters.</span></span> <span data-ttu-id="43dd8-105">但是，可以在 CDATA 节中对这类特殊字符进行包装，使它们不被视为标记字符。</span><span class="sxs-lookup"><span data-stu-id="43dd8-105">However, you can wrap this type of special characters in a CDATA section to prevent them from being treated as markup characters.</span></span> <span data-ttu-id="43dd8-106">XML 语法分析程序将 CDATA 节中的文本视为纯文本。</span><span class="sxs-lookup"><span data-stu-id="43dd8-106">The text within the CDATA section is treated by the XML parser as plain text.</span></span>  
  
 <span data-ttu-id="43dd8-107">`sql:use-cdata` 批注用于指定应当将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回的数据包含在 CDATA 节中，就是说，它指示是否应当将由 `sql:field` 指定的列中的值包含在 CDATA 节中。</span><span class="sxs-lookup"><span data-stu-id="43dd8-107">The `sql:use-cdata` annotation is used to specify that the data returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should be wrapped in a CDATA section (that is, it indicates whether the value from a column that is specified by `sql:field` should be enclosed in a CDATA section).</span></span> <span data-ttu-id="43dd8-108">可以仅对映射到数据库列的元素指定 `sql:use-cdata` 批注。</span><span class="sxs-lookup"><span data-stu-id="43dd8-108">The `sql:use-cdata` annotation can be specified only on elements that map to a database column.</span></span>  
  
 <span data-ttu-id="43dd8-109">`sql:use-cdata` 批注接受布尔值（0 = false，1 = true）。</span><span class="sxs-lookup"><span data-stu-id="43dd8-109">The `sql:use-cdata` annotation takes a Boolean value (0 = false, 1 = true).</span></span> <span data-ttu-id="43dd8-110">可接受的值为 0、1、true 和 false。</span><span class="sxs-lookup"><span data-stu-id="43dd8-110">The acceptable values are 0, 1, true, and false.</span></span>  
  
 <span data-ttu-id="43dd8-111">该批注不能与 `sql:url-encode` 一起使用，也不能对 ID、IDREF、IDREFS、NMTOKEN 和 NMTOKENS 属性类型使用。</span><span class="sxs-lookup"><span data-stu-id="43dd8-111">This annotation cannot be used with `sql:url-encode` or on the ID, IDREF, IDREFS, NMTOKEN, and NMTOKENS attribute types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="43dd8-112">示例</span><span class="sxs-lookup"><span data-stu-id="43dd8-112">Examples</span></span>  
 <span data-ttu-id="43dd8-113">若要创建使用以下示例的工作示例，必须满足某些要求。</span><span class="sxs-lookup"><span data-stu-id="43dd8-113">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="43dd8-114">有关详细信息，请参阅[运行 SQLXML 示例的要求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="43dd8-114">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-sqluse-cdata-on-an-element"></a><span data-ttu-id="43dd8-115">A.</span><span class="sxs-lookup"><span data-stu-id="43dd8-115">A.</span></span> <span data-ttu-id="43dd8-116">在元素上指定 sql:use-cdata</span><span class="sxs-lookup"><span data-stu-id="43dd8-116">Specifying sql:use-cdata on an element</span></span>  
 <span data-ttu-id="43dd8-117">在下面的架构中，在 `sql:use-cdata` 元素内的中，将设置为 1 (True) **\<AddressLine1>** **\<Address>** 。</span><span class="sxs-lookup"><span data-stu-id="43dd8-117">In the following schema, `sql:use-cdata` is set to 1 (True) for the **\<AddressLine1>** within the **\<Address>** element.</span></span> <span data-ttu-id="43dd8-118">结果，将在 CDATA 节中返回数据。</span><span class="sxs-lookup"><span data-stu-id="43dd8-118">As a result, the data is returned in a CDATA section.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Address"   
               sql:relation="Person.Address"   
               sql:key-fields="AddressID" >  
   <xsd:complexType>  
        <xsd:sequence>  
          <xsd:element name="AddressID"  type="xsd:string" />  
          <xsd:element name="AddressLine1" type="xsd:string"   
                       sql:use-cdata="1" />  
        </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="43dd8-119">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="43dd8-119">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="43dd8-120">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="43dd8-120">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="43dd8-121">将文件另存为 UseCData.xml。</span><span class="sxs-lookup"><span data-stu-id="43dd8-121">Save the file as UseCData.xml.</span></span>  
  
2.  <span data-ttu-id="43dd8-122">复制以下模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="43dd8-122">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="43dd8-123">在保存 UseCData.xml 的相同目录中将文件另存为 UseCDataT.xml。</span><span class="sxs-lookup"><span data-stu-id="43dd8-123">Save the file as UseCDataT.xml in the same directory where you saved UseCData.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="UseCData.xml">  
            /Address[AddressID < 11]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="43dd8-124">为映射架构 (UseCData.xml) 指定的目录路径相对于保存模板的目录。</span><span class="sxs-lookup"><span data-stu-id="43dd8-124">The directory path specified for the mapping schema (UseCData.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="43dd8-125">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="43dd8-125">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\UseCData.xml"  
    ```  
  
3.  <span data-ttu-id="43dd8-126">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="43dd8-126">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="43dd8-127">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="43dd8-127">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="43dd8-128">部分结果集如下：</span><span class="sxs-lookup"><span data-stu-id="43dd8-128">This is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Address>   
    <AddressID>1</CustomerID>   
    <AddressLine1>   
      <![CDATA[ 1970 Napa Ct.  ]]>   
    </AddressLine1>   
  </Address>  
  <Address>  
    <AddressLine1>   
      <![CDATA[ 9833 Mt. Dias Blv. ]]>   
    </AddressLine1>   
  </Address>  
  ...  
</ROOT>  
```  
  
  
