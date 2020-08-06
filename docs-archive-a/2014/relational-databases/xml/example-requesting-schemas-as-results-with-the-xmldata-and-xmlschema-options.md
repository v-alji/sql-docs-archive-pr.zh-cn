---
title: 示例：使用 XMLDATA 和 XMLSCHEMA 选项请求架构作为结果 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, requesting schema example
- RAW mode, with XMLDATA and XMLSCHEMA
ms.assetid: 3504ca38-be66-42b2-8dab-f499c9584840
author: rothja
ms.author: jroth
ms.openlocfilehash: af244e3436df4d8665079ce20fb749a44021fe04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692821"
---
# <a name="example-requesting-schemas-as-results-with-the-xmldata-and-xmlschema-options"></a><span data-ttu-id="0a86c-102">示例：使用 XMLDATA 和 XMLSCHEMA 选项请求架构作为结果</span><span class="sxs-lookup"><span data-stu-id="0a86c-102">Example: Requesting Schemas as Results with the XMLDATA and XMLSCHEMA Options</span></span>
  <span data-ttu-id="0a86c-103">下面的查询返回描述文档结构的 XML-DATA 架构。</span><span class="sxs-lookup"><span data-stu-id="0a86c-103">The following query returns the XML-DATA schema that describes the document structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a86c-104">示例</span><span class="sxs-lookup"><span data-stu-id="0a86c-104">Example</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, XMLDATA  
GO  
```  
  
 <span data-ttu-id="0a86c-105">结果如下：</span><span class="sxs-lookup"><span data-stu-id="0a86c-105">This is the result:</span></span>  
  
```  
<Schema name="Schema1" xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:datatypes">  
  <ElementType name="row" content="empty" model="closed">  
    <AttributeType name="ProductModelID" dt:type="i4" />  
    <AttributeType name="Name" dt:type="string" />  
    <attribute type="ProductModelID" />  
    <attribute type="Name" />  
  </ElementType>  
</Schema>  
<row xmlns="x-schema:#Schema1" ProductModelID="122" Name="All-Purpose Bike Stand" />  
<row xmlns="x-schema:#Schema1" ProductModelID="119" Name="Bike Wash" />  
```  
  
> [!NOTE]
>  <span data-ttu-id="0a86c-106"><`Schema`> 被声明为命名空间。</span><span class="sxs-lookup"><span data-stu-id="0a86c-106">The <`Schema`> is declared as a namespace.</span></span> <span data-ttu-id="0a86c-107">在不同的 FOR XML 查询中请求多个 XML-Data 架构时，为了避免命名空间冲突，该示例中的命名空间标识符 `Schema1` 将在每次执行查询时进行更改。</span><span class="sxs-lookup"><span data-stu-id="0a86c-107">To avoid namespace collisions when multiple XML-Data schemas are requested in different FOR XML queries, the namespace identifier, `Schema1` in this example, changes with every query execution.</span></span> <span data-ttu-id="0a86c-108">命名空间标识符由**Schema_n_** 组成，其中**_n_** 为整数。</span><span class="sxs-lookup"><span data-stu-id="0a86c-108">The namespace identifier is made up of **Schema_n_** where **_n_** is an integer.</span></span>  
  
 <span data-ttu-id="0a86c-109">通过指定 `XMLSCHEMA` 选项，您可以针对结果请求 XSD 架构。</span><span class="sxs-lookup"><span data-stu-id="0a86c-109">By specifying the `XMLSCHEMA` option, you can request the XSD schema for the result.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, XMLSCHEMA  
GO  
```  
  
 <span data-ttu-id="0a86c-110">结果如下：</span><span class="sxs-lookup"><span data-stu-id="0a86c-110">This is the result:</span></span>  
  
```  
<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">  
  <xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />  
  <xsd:element name="row">  
    <xsd:complexType>  
      <xsd:attribute name="ProductModelID" type="sqltypes:int" use="required" />  
      <xsd:attribute name="Name" use="required">  
        <xsd:simpleType sqltypes:sqlTypeAlias="[AdventureWorks].[dbo].[Name]">  
          <xsd:restriction base="sqltypes:nvarchar" sqltypes:localeId="1033" sqltypes:sqlCompareOptions="IgnoreCase IgnoreKanaType IgnoreWidth" sqltypes:sqlSortId="52">  
            <xsd:maxLength value="50" />  
          </xsd:restriction>  
        </xsd:simpleType>  
      </xsd:attribute>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
<row xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1" ProductModelID="122" Name="All-Purpose Bike Stand" />  
<row xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1" ProductModelID="119" Name="Bike Wash" />  
  
```  
  
 <span data-ttu-id="0a86c-111">您可以将目标命名空间 URI 指定为 FOR XML 中 XMLSCHEMA 的可选参数。</span><span class="sxs-lookup"><span data-stu-id="0a86c-111">You can specify the target namespace URI as an optional argument to XMLSCHEMA in FOR XML.</span></span> <span data-ttu-id="0a86c-112">这将返回架构中的指定目标命名空间。</span><span class="sxs-lookup"><span data-stu-id="0a86c-112">This returns the specified target namespace in the schema.</span></span> <span data-ttu-id="0a86c-113">每次执行查询时，此目标命名空间都保持不变。</span><span class="sxs-lookup"><span data-stu-id="0a86c-113">This target namespace remains the same every time you execute the query.</span></span> <span data-ttu-id="0a86c-114">例如，下面的查询是通过对上面的查询进行修改得到的，它包含了作为参数的命名空间 URI `'urn:example.com'`。</span><span class="sxs-lookup"><span data-stu-id="0a86c-114">For example, the following modified version of the previous query includes the namespace URI, `'urn:example.com'`, as an argument.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, XMLSCHEMA ('urn:example.com')  
GO  
```  
  
 <span data-ttu-id="0a86c-115">结果如下：</span><span class="sxs-lookup"><span data-stu-id="0a86c-115">This is the result:</span></span>  
  
```  
<xsd:schema targetNamespace="urn:example.com" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">  
  <xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />  
  <xsd:element name="row">  
    <xsd:complexType>  
      <xsd:attribute name="ProductModelID" type="sqltypes:int" use="required" />  
      <xsd:attribute name="Name" use="required">  
        <xsd:simpleType sqltypes:sqlTypeAlias="[AdventureWorks].[dbo].[Name]">  
          <xsd:restriction base="sqltypes:nvarchar" sqltypes:localeId="1033" sqltypes:sqlCompareOptions="IgnoreCase IgnoreKanaType IgnoreWidth" sqltypes:sqlSortId="52">  
            <xsd:maxLength value="50" />  
          </xsd:restriction>  
        </xsd:simpleType>  
      </xsd:attribute>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
<row xmlns="urn:example.com" ProductModelID="122" Name="All-Purpose Bike Stand" />  
<row xmlns="urn:example.com" ProductModelID="119" Name="Bike Wash" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a86c-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0a86c-116">See Also</span></span>  
 [<span data-ttu-id="0a86c-117">将 RAW 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="0a86c-117">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
