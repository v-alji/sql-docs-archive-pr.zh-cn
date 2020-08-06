---
title: 使用 sql：溢出字段 (SQLXML 4.0) 检索未使用的数据 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- unconsumed data
- storing unconsumed data
- retrieving unconsumed data
- annotated XSD schemas, unconsumed data
- overflow data [SQLXML]
- sql:overflow-field
ms.assetid: 8526998d-b47d-4a32-8dc2-7f50a8d11097
author: rothja
ms.author: jroth
ms.openlocfilehash: 796fda9428954c5f18c5d37b353de9fd4122551e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590124"
---
# <a name="retrieving-unconsumed-data-using-the-sqloverflow-field-sqlxml-40"></a><span data-ttu-id="ce8d1-102">使用 sql:overflow-field 检索未用完的数据 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="ce8d1-102">Retrieving Unconsumed Data Using the sql:overflow-field (SQLXML 4.0)</span></span>
  <span data-ttu-id="ce8d1-103">使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] OPENXML 函数将 XML 文档中的记录插入数据库时，源 XML 文档中所有未用完的数据可以存储在列中。</span><span class="sxs-lookup"><span data-stu-id="ce8d1-103">When records are inserted in a database from an XML document by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] OPENXML function, all the unconsumed data from the source XML document can be stored in a column.</span></span> <span data-ttu-id="ce8d1-104">使用带批注的架构从数据库检索数据时，可指定 `sql:overflow-field` 属性以标识表中存储溢出数据的列。</span><span class="sxs-lookup"><span data-stu-id="ce8d1-104">When you retrieve data from a database by using annotated schemas, you can specify the `sql:overflow-field` attribute to identify the column in the table in which the overflow data is stored.</span></span> <span data-ttu-id="ce8d1-105">`sql:overflow-field`可以在上指定属性 **\<element>** 。</span><span class="sxs-lookup"><span data-stu-id="ce8d1-105">The `sql:overflow-field` attribute can be specified on **\<element>**.</span></span>  
  
 <span data-ttu-id="ce8d1-106">然后，可以通过以下方式检索此数据：</span><span class="sxs-lookup"><span data-stu-id="ce8d1-106">This data is then retrieved in these ways:</span></span>  
  
-   <span data-ttu-id="ce8d1-107">将在溢出列中存储的属性添加到包含 `sql:overflow-field` 批注的元素。</span><span class="sxs-lookup"><span data-stu-id="ce8d1-107">Attributes stored in the overflow column are added to the element that contains the `sql:overflow-field` annotation.</span></span>  
  
-   <span data-ttu-id="ce8d1-108">存储在数据库的溢出列中的子元素及其后代作为子元素添加在架构中显式指定的内容之后。</span><span class="sxs-lookup"><span data-stu-id="ce8d1-108">The child elements and their descendents, stored in the overflow column in the database, are added as child elements following the content that is explicitly specified in the schema.</span></span> <span data-ttu-id="ce8d1-109">（顺序被打乱。）</span><span class="sxs-lookup"><span data-stu-id="ce8d1-109">(No order is preserved.)</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ce8d1-110">示例</span><span class="sxs-lookup"><span data-stu-id="ce8d1-110">Examples</span></span>  
 <span data-ttu-id="ce8d1-111">若要创建使用以下示例的工作示例，必须满足某些要求。</span><span class="sxs-lookup"><span data-stu-id="ce8d1-111">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="ce8d1-112">有关详细信息，请参阅[运行 SQLXML 示例的要求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="ce8d1-112">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-sqloverflow-field-for-an-element"></a><span data-ttu-id="ce8d1-113">A.</span><span class="sxs-lookup"><span data-stu-id="ce8d1-113">A.</span></span> <span data-ttu-id="ce8d1-114">为元素指定 sql:overflow-field</span><span class="sxs-lookup"><span data-stu-id="ce8d1-114">Specifying sql:overflow-field for an element</span></span>  
 <span data-ttu-id="ce8d1-115">本示例假定已运行了以下脚本，以便 tempdb 数据库中存在名为 Customers2 的表：</span><span class="sxs-lookup"><span data-stu-id="ce8d1-115">This example assumes that the following script has been run so that a table named Customers2 exists in the tempdb database:</span></span>  
  
```  
USE tempdb  
CREATE TABLE Customers2 (  
CustomerID       VARCHAR(10),   
ContactName    VARCHAR(30),   
AddressOverflow    NVARCHAR(500))  
  
GO  
INSERT INTO Customers2 VALUES (  
'ALFKI',   
'Joe',  
'<Address>  
  <Address1>Maple St.</Address1>  
  <Address2>Apt. E105</Address2>  
  <City>Seattle</City>  
  <State>WA</State>  
  <Zip>98147</Zip>  
 </Address>')  
GO  
```  
  
 <span data-ttu-id="ce8d1-116">此外，必须为 tempdb 数据库创建虚拟目录，并创建 `template` 名为 "template" 的模板虚拟名称。</span><span class="sxs-lookup"><span data-stu-id="ce8d1-116">In addition, you must create a virtual directory for the tempdb database-and a template virtual name of `template` type named "template".</span></span>  
  
 <span data-ttu-id="ce8d1-117">在以下示例中，映射架构检索 Customers2 表的 AddressOverflow 列中存储的未用完数据：</span><span class="sxs-lookup"><span data-stu-id="ce8d1-117">In the following example, the mapping schema retrieves the unconsumed data that is stored in the AddressOverflow column of the Customers2 table:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Customers2" sql:overflow-field="AddressOverflow" >  
    <xsd:complexType>  
      <xsd:attribute name="CustomerID"  type="xsd:integer"/>  
      <xsd:attribute name="ContactName"  type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="ce8d1-118">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="ce8d1-118">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="ce8d1-119">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="ce8d1-119">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="ce8d1-120">将文件另存为 Overflow.xml。</span><span class="sxs-lookup"><span data-stu-id="ce8d1-120">Save the file as Overflow.xml.</span></span>  
  
2.  <span data-ttu-id="ce8d1-121">复制以下模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="ce8d1-121">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="ce8d1-122">在保存 Overflow.xml 的相同目录中将该文件另存为 OverflowT.xml。</span><span class="sxs-lookup"><span data-stu-id="ce8d1-122">Save the file as OverflowT.xml in the same directory where you saved Overflow.xml.</span></span> <span data-ttu-id="ce8d1-123">模板中的查询选择 Customers2 表中的记录。</span><span class="sxs-lookup"><span data-stu-id="ce8d1-123">The query in the template selects the records in the Customers2 table.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="Overflow.xml">  
            /Customers2  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="ce8d1-124">为映射架构 (Overflow.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="ce8d1-124">The directory path specified for the mapping schema (Overflow.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="ce8d1-125">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="ce8d1-125">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\Overflow.xml"  
    ```  
  
3.  <span data-ttu-id="ce8d1-126">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="ce8d1-126">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="ce8d1-127">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="ce8d1-127">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="ce8d1-128">下面是结果集：</span><span class="sxs-lookup"><span data-stu-id="ce8d1-128">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customers2 CustomerID="ALFKI" ContactName="Joe">  
    <Address1>Maple St.</Address1>   
    <Address2>Apt. E105</Address2>   
    <City>Seattle</City>   
    <State>WA</State>   
    <Zip>98147</Zip>   
  </Customers2>  
</ROOT>  
```  
  
  
