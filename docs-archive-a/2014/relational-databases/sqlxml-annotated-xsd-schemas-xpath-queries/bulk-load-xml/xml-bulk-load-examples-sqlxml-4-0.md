---
title: XML 大容量加载示例 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- overflow-field annotation
- ConnectionCommand property
- XMLFragment property
- relationship chains [SQLXML]
- multiple table bulk loading
- examples [SQLXML], XML Bulk Load
- overflow data [SQLXML]
- sql:datatype
- transaction mode [SQLXML]
- CheckConstraints property
- sql:overflow-field
- XML Bulk Load [SQLXML], examples
- TempFilePath property
- datatype annotation
- Transaction property
- KeepIdentity property
- Execute method
- streaming XML data
- xml data type [SQL Server], SQLXML
- bulk load [SQLXML], examples
ms.assetid: 970e4553-b41d-4a12-ad50-0ee65d1f305d
author: rothja
ms.author: jroth
ms.openlocfilehash: c7eaec77ef068efd28c4da65833afa5047b222f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682774"
---
# <a name="xml-bulk-load-examples-sqlxml-40"></a><span data-ttu-id="53211-102">XML 大容量加载示例 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="53211-102">XML Bulk Load Examples (SQLXML 4.0)</span></span>
  <span data-ttu-id="53211-103">以下示例说明 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的 XML 大容量加载功能。</span><span class="sxs-lookup"><span data-stu-id="53211-103">The following examples illustrate the XML Bulk Load functionality in Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="53211-104">每个示例都提供了 XSD 架构及其等效的 XDR 架构。</span><span class="sxs-lookup"><span data-stu-id="53211-104">Each example provides an XSD schema and its equivalent XDR schema.</span></span>  
  
## <a name="bulk-loader-script-validateandbulkloadvbs"></a><span data-ttu-id="53211-105">Bulk Loader 脚本 (ValidateAndBulkload.vbs)</span><span class="sxs-lookup"><span data-stu-id="53211-105">Bulk Loader Script (ValidateAndBulkload.vbs)</span></span>  
 <span data-ttu-id="53211-106">下面的脚本编写在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) ，将 xml 文档加载到 XML DOM 中; 根据架构对其进行验证; 如果文档有效，则执行 xml 大容量加载将 xml 加载到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 表中。</span><span class="sxs-lookup"><span data-stu-id="53211-106">The following script, written in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript), loads an XML document into the XML DOM; validates it against a schema; and, if the document is valid, executes an XML bulk load to load the XML into a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="53211-107">此脚本可用于本主题后面提到它的每个单独示例。</span><span class="sxs-lookup"><span data-stu-id="53211-107">This script can be used with each of the individual examples that refer to it later in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="53211-108">如果未从数据文件中上载任何内容，XML 大容量加载将不引发警告或错误。</span><span class="sxs-lookup"><span data-stu-id="53211-108">XML Bulk Load does not throw a warning or an error if no content is uploaded from the data file.</span></span> <span data-ttu-id="53211-109">因此，最好在执行大容量加载操作之前验证您的 XML 数据文件。</span><span class="sxs-lookup"><span data-stu-id="53211-109">Therefore, it is a good practice to validate your XML data file prior to executing a bulk load operation.</span></span>  
  
```  
Dim FileValid  
  
set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
objBL.ConnectionString = "provider=SQLOLEDB;data source=MyServer;database=tempdb;integrated security=SSPI"  
objBL.ErrorLogFile = "c:\error.log"  
  
'Validate the data file prior to bulkload  
Dim sOutput   
sOutput = ValidateFile("SampleXMLData.xml", "", "SampleSchema.xml")  
WScript.Echo sOutput  
  
If FileValid Then  
   ' Check constraints and initiate transaction (if needed)  
   ' objBL.CheckConstraints = True  
   ' objBL.Transaction=True  
  'Execute XML bulkload using file.  
  objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
  set objBL=Nothing  
End If  
  
Function ValidateFile(strXmlFile,strUrn,strXsdFile)  
  
   ' Create a schema cache and add SampleSchema.xml to it.  
   Dim xs, fso, sAppPath  
   Set fso = CreateObject("Scripting.FileSystemObject")   
   Set xs = CreateObject("MSXML2.XMLSchemaCache.6.0")  
   sAppPath = fso.GetFolder(".")   
   xs.Add strUrn, sAppPath & "\" & strXsdFile  
  
   ' Create an XML DOMDocument object.  
   Dim xd   
   Set xd = CreateObject("MSXML2.DOMDocument.6.0")  
  
   ' Assign the schema cache to the DOM document.  
   ' schemas collection.  
   Set xd.schemas = xs  
  
   ' Load XML document as DOM document.  
   xd.async = False  
   xd.Load sAppPath & "\" & strXmlFile  
  
   ' Return validation results in message to the user.  
   If xd.parseError.errorCode <> 0 Then  
        ValidateFile = "Validation failed on " & _  
             strXmlFile & vbCrLf & _  
             "=======" & vbCrLf & _  
             "Reason: " & xd.parseError.reason & _  
             vbCrLf & "Source: " & _  
             xd.parseError.srcText & _  
             vbCrLf & "Line: " & _  
             xd.parseError.Line & vbCrLf  
             FileValid = False  
    Else  
        ValidateFile = "Validation succeeded for " & _  
             strXmlFile & vbCrLf & _  
             "========" & _  
             vbCrLf & "Contents to be bulkloaded" & vbCrLf  
             FileValid = True  
    End If  
End Function  
```  
  
## <a name="a-bulk-loading-xml-in-a-table"></a><span data-ttu-id="53211-110">A.</span><span class="sxs-lookup"><span data-stu-id="53211-110">A.</span></span> <span data-ttu-id="53211-111">将 XML 大容量加载到表中</span><span class="sxs-lookup"><span data-stu-id="53211-111">Bulk loading XML in a table</span></span>  
 <span data-ttu-id="53211-112">此示例与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (MyServer) 的 ConnectionString 属性中指定的实例建立连接。</span><span class="sxs-lookup"><span data-stu-id="53211-112">This example establishes a connection to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is specified in the ConnectionString property (MyServer).</span></span> <span data-ttu-id="53211-113">该示例还指定 ErrorLogFile 属性。</span><span class="sxs-lookup"><span data-stu-id="53211-113">The example also specifies the ErrorLogFile property.</span></span> <span data-ttu-id="53211-114">因此，错误输出将保存在指定的文件（“C:\error.log”）中，您也可以决定将其更改为其他位置。</span><span class="sxs-lookup"><span data-stu-id="53211-114">Therefore, the error output is saved in the specified file ("C:\error.log"), which you might also decide to change to a different location.</span></span> <span data-ttu-id="53211-115">另请注意，Execute 方法将映射架构文件 ( # A0) 和 XML 数据文件 ( # A1) 。</span><span class="sxs-lookup"><span data-stu-id="53211-115">Notice also that the Execute method has as its parameters both the mapping schema file (SampleSchema.xml) and the XML data file (SampleXMLData.xml).</span></span> <span data-ttu-id="53211-116">当执行大容量加载时，在**tempdb**数据库中创建的 "用户" 表将包含基于 XML 数据文件内容的新记录。</span><span class="sxs-lookup"><span data-stu-id="53211-116">When the bulk load executes, the Cust table you have created in **tempdb** database will contain new records based upon the contents of the XML data file.</span></span>  
  
#### <a name="to-test-a-sample-bulk-load"></a><span data-ttu-id="53211-117">测试示例大容量加载</span><span class="sxs-lookup"><span data-stu-id="53211-117">To test a sample bulk load</span></span>  
  
1.  <span data-ttu-id="53211-118">创建下表：</span><span class="sxs-lookup"><span data-stu-id="53211-118">Create this table:</span></span>  
  
    ```  
    CREATE TABLE Cust(CustomerID  int PRIMARY KEY,  
                      CompanyName varchar(20),  
                      City        varchar(20));  
    GO  
    ```  
  
2.  <span data-ttu-id="53211-119">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="53211-119">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="53211-120">在此文件中，添加以下 XSD 架构：</span><span class="sxs-lookup"><span data-stu-id="53211-120">To this file, add the following XSD schema:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
       <xsd:element name="ROOT" sql:is-constant="1" >  
         <xsd:complexType>  
           <xsd:sequence>  
             <xsd:element name="Customers" sql:relation="Cust" maxOccurs="unbounded">  
               <xsd:complexType>  
                 <xsd:sequence>  
                   <xsd:element name="CustomerID"  type="xsd:integer" />  
                   <xsd:element name="CompanyName" type="xsd:string" />  
                   <xsd:element name="City"        type="xsd:string" />  
                 </xsd:sequence>  
               </xsd:complexType>  
             </xsd:element>  
           </xsd:sequence>  
          </xsd:complexType>  
         </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="53211-121">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 SampleXMLData.xml。</span><span class="sxs-lookup"><span data-stu-id="53211-121">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="53211-122">在此文件中，添加以下 XML 文档：</span><span class="sxs-lookup"><span data-stu-id="53211-122">To this file, add the following XML document:</span></span>  
  
    ```  
    <ROOT>  
      <Customers>  
        <CustomerID>1111</CustomerID>  
        <CompanyName>Sean Chai</CompanyName>  
        <City>New York</City>  
      </Customers>  
      <Customers>  
        <CustomerID>1112</CustomerID>  
        <CompanyName>Tom Johnston</CompanyName>  
         <City>Los Angeles</City>  
      </Customers>  
      <Customers>  
        <CustomerID>1113</CustomerID>  
        <CompanyName>Institute of Art</CompanyName>  
        <City>Chicago</City>  
      </Customers>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="53211-123">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 ValidateAndBulkload.vbs。</span><span class="sxs-lookup"><span data-stu-id="53211-123">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="53211-124">在此文件中，添加本主题前面开头部分提供的 VBScript 代码。</span><span class="sxs-lookup"><span data-stu-id="53211-124">To this file, add the VBScript code that is provided above at the beginning of this topic.</span></span> <span data-ttu-id="53211-125">修改连接字符串以提供适当的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="53211-125">Modify the connection string to provide the appropriate server name.</span></span> <span data-ttu-id="53211-126">为指定为 Execute 方法的参数的文件指定适当的路径。</span><span class="sxs-lookup"><span data-stu-id="53211-126">Specify the appropriate path for the files that are specified as parameters to the Execute method.</span></span>  
  
5.  <span data-ttu-id="53211-127">执行 VBScript 代码。</span><span class="sxs-lookup"><span data-stu-id="53211-127">Execute the VBScript code.</span></span> <span data-ttu-id="53211-128">XML 大容量加载会将 XML 加载到 Cust 表中。</span><span class="sxs-lookup"><span data-stu-id="53211-128">XML Bulk Load loads the XML into the Cust table.</span></span>  
  
 <span data-ttu-id="53211-129">这是等效的 XDR 架构：</span><span class="sxs-lookup"><span data-stu-id="53211-129">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
  
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="ROOT" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers"  sql:relation="Cust" >  
      <element type="CustomerID"  sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City"        sql:field="City" />  
  
   </ElementType>  
</Schema>  
```  
  
## <a name="b-bulk-loading-xml-data-in-multiple-tables"></a><span data-ttu-id="53211-130">B.</span><span class="sxs-lookup"><span data-stu-id="53211-130">B.</span></span> <span data-ttu-id="53211-131">将 XML 数据大容量加载到多个表中</span><span class="sxs-lookup"><span data-stu-id="53211-131">Bulk loading XML data in multiple tables</span></span>  
 <span data-ttu-id="53211-132">在此示例中，XML 文档由 **\<Customer>** 和元素组成 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="53211-132">In this example, the XML document consists of the **\<Customer>** and **\<Order>** elements.</span></span>  
  
```  
<ROOT>  
  <Customers>  
    <CustomerID>1111</CustomerID>  
    <CompanyName>Sean Chai</CompanyName>  
    <City>NY</City>  
    <Order OrderID="1" />  
    <Order OrderID="2" />  
  </Customers>  
  <Customers>  
    <CustomerID>1112</CustomerID>  
    <CompanyName>Tom Johnston</CompanyName>  
     <City>LA</City>    
    <Order OrderID="3" />  
  </Customers>  
  <Customers>  
    <CustomerID>1113</CustomerID>  
    <CompanyName>Institute of Art</CompanyName>  
    <Order OrderID="4" />  
  </Customers>  
</ROOT>  
```  
  
 <span data-ttu-id="53211-133">此示例将 XML 数据大容量加载**到以下两**个**表中：**</span><span class="sxs-lookup"><span data-stu-id="53211-133">This example bulk loads the XML data into two tables, **Cust** and **CustOrder**:</span></span>  
  
```  
Cust(CustomerID, CompanyName, City)  
CustOrder(OrderID, CustomerID)  
```  
  
 <span data-ttu-id="53211-134">以下 XSD 架构定义这些表的 XML 视图。</span><span class="sxs-lookup"><span data-stu-id="53211-134">The following XSD schema defines the XML view of these tables.</span></span> <span data-ttu-id="53211-135">架构指定和元素之间的父子关系 **\<Customer>** **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="53211-135">The schema specifies the parent-child relationship between the **\<Customer>** and **\<Order>** elements.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="CustCustOrder"  
          parent="Cust"  
          parent-key="CustomerID"  
          child="CustOrder"  
          child-key="CustomerID" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="ROOT" sql:is-constant="1" >  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Customers" sql:relation="Cust" >  
          <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="CustomerID"  type="xsd:integer" />  
              <xsd:element name="CompanyName" type="xsd:string" />  
              <xsd:element name="City"        type="xsd:string" />  
              <xsd:element name="Order"   
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder" >  
                <xsd:complexType>  
                  <xsd:attribute name="OrderID" type="xsd:integer" />  
                </xsd:complexType>  
              </xsd:element>  
             </xsd:sequence>  
          </xsd:complexType>  
        </xsd:element>  
      </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="53211-136">XML 大容量加载使用在和元素之间指定的主键/外键 **\<Cust>** 关系 **\<CustOrder>** 将数据大容量加载到这两个表中。</span><span class="sxs-lookup"><span data-stu-id="53211-136">XML Bulk Load uses the primary key/foreign key relationship specified above between the **\<Cust>** and **\<CustOrder>** elements to bulk load the data into both tables.</span></span>  
  
#### <a name="to-test-a-sample-bulk-load"></a><span data-ttu-id="53211-137">测试示例大容量加载</span><span class="sxs-lookup"><span data-stu-id="53211-137">To test a sample bulk load</span></span>  
  
1.  <span data-ttu-id="53211-138">在**tempdb**数据库中创建两个表：</span><span class="sxs-lookup"><span data-stu-id="53211-138">Create two tables in **tempdb** database:</span></span>  
  
    ```  
    USE tempdb;  
    CREATE TABLE Cust(  
           CustomerID  int PRIMARY KEY,  
           CompanyName varchar(20),  
           City        varchar(20));  
    CREATE TABLE CustOrder(        OrderID     int PRIMARY KEY,   
            CustomerID int FOREIGN KEY REFERENCES Cust(CustomerID));  
    ```  
  
2.  <span data-ttu-id="53211-139">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="53211-139">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="53211-140">将在本示例中提供的 XSD 架构添加到此文件中。</span><span class="sxs-lookup"><span data-stu-id="53211-140">Add the XSD schema that is provided in this example to the file.</span></span>  
  
3.  <span data-ttu-id="53211-141">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 SampleData.xml。</span><span class="sxs-lookup"><span data-stu-id="53211-141">Create a file in your preferred text or XML editor, and save it as SampleData.xml.</span></span> <span data-ttu-id="53211-142">将在本示例前面提供的 XML 文档添加到此文件中。</span><span class="sxs-lookup"><span data-stu-id="53211-142">Add the XML document that was provided earlier in this example to the file.</span></span>  
  
4.  <span data-ttu-id="53211-143">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 ValidateAndBulkload.vbs。</span><span class="sxs-lookup"><span data-stu-id="53211-143">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="53211-144">在此文件中，添加本主题前面开头部分提供的 VBScript 代码。</span><span class="sxs-lookup"><span data-stu-id="53211-144">To this file, add the VBScript code that is provided above at the beginning of this topic.</span></span> <span data-ttu-id="53211-145">修改连接字符串以提供适当的服务器和数据库名称。</span><span class="sxs-lookup"><span data-stu-id="53211-145">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="53211-146">为指定为 Execute 方法的参数的文件指定适当的路径。</span><span class="sxs-lookup"><span data-stu-id="53211-146">Specify the appropriate path for the files that are specified as parameters to the Execute method.</span></span>  
  
5.  <span data-ttu-id="53211-147">执行上面的 VBScript 代码。</span><span class="sxs-lookup"><span data-stu-id="53211-147">Execute the VBScript code above.</span></span> <span data-ttu-id="53211-148">XML 大容量加载会将 XML 文档加载到 Cust 表和 CustOrder 表中。</span><span class="sxs-lookup"><span data-stu-id="53211-148">XML Bulk Load loads the XML document into the Cust and CustOrder tables.</span></span>  
  
 <span data-ttu-id="53211-149">这是等效的 XDR 架构：</span><span class="sxs-lookup"><span data-stu-id="53211-149">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="ROOT" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust" >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
<sql:relationship  
                key-relation="Cust"  
                key="CustomerID"  
                foreign-key="CustomerID"  
                foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
</Schema>  
```  
  
## <a name="c-using-chain-relationships-in-the-schema-to-bulk-load-xml"></a><span data-ttu-id="53211-150">C.</span><span class="sxs-lookup"><span data-stu-id="53211-150">C.</span></span> <span data-ttu-id="53211-151">使用架构中的链关系大容量加载 XML</span><span class="sxs-lookup"><span data-stu-id="53211-151">Using chain relationships in the schema to bulk load XML</span></span>  
 <span data-ttu-id="53211-152">本示例说明 XML 大容量加载如何使用在映射架构中指定的 M:N 关系在表中加载表示 M:N 关系的数据。</span><span class="sxs-lookup"><span data-stu-id="53211-152">This example illustrates how the M:N relationship that is specified in the mapping schema is used by XML Bulk Load to load data in a table that represents an M:N relationship.</span></span>  
  
 <span data-ttu-id="53211-153">例如，请看此 XSD 架构：</span><span class="sxs-lookup"><span data-stu-id="53211-153">For example, consider this XSD schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="OrderOD"  
          parent="Ord"  
          parent-key="OrderID"  
          child="OrderDetail"  
          child-key="OrderID" />  
  
    <sql:relationship name="ODProduct"  
          parent="OrderDetail"  
          parent-key="ProductID"  
          child="Product"  
          child-key="ProductID"   
          inverse="true"/>  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="ROOT" sql:is-constant="1" >  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Ord"   
                     sql:key-fields="OrderID" >  
          <xsd:complexType>  
            <xsd:sequence>  
             <xsd:element name="Product"  
                          sql:relation="Product"   
                          sql:key-fields="ProductID"  
                          sql:relationship="OrderOD ODProduct">  
               <xsd:complexType>  
                 <xsd:attribute name="ProductID" type="xsd:int" />  
                 <xsd:attribute name="ProductName" type="xsd:string" />  
               </xsd:complexType>  
             </xsd:element>  
           </xsd:sequence>  
           <xsd:attribute name="OrderID"   type="xsd:integer" />   
           <xsd:attribute name="CustomerID"   type="xsd:string" />  
         </xsd:complexType>  
       </xsd:element>  
      </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="53211-154">架构指定 **\<Order>** 具有子元素的元素 **\<Product>** 。</span><span class="sxs-lookup"><span data-stu-id="53211-154">The schema specifies an **\<Order>** element with a **\<Product>** child element.</span></span> <span data-ttu-id="53211-155">**\<Order>** 元素映射到 Ord 表， **\<Product>** 元素映射到数据库中的 Product 表。</span><span class="sxs-lookup"><span data-stu-id="53211-155">The **\<Order>** element maps to Ord table and the **\<Product>** element maps to the Product table in the database.</span></span> <span data-ttu-id="53211-156">元素上指定的链关系 **\<Product>** 标识由 OrderDetail 表表示的 M:N 关系。</span><span class="sxs-lookup"><span data-stu-id="53211-156">The chain relationship specified on the **\<Product>** element identifies a M:N relationship represented by the OrderDetail table.</span></span> <span data-ttu-id="53211-157">（一个订单可能包含许多产品，而一个产品可能包含在许多订单中。）</span><span class="sxs-lookup"><span data-stu-id="53211-157">(An order can include many products, and a product can be included in many orders.)</span></span>  
  
 <span data-ttu-id="53211-158">当您使用此架构大容量加载 XML 文档时，记录将添加到 Ord、Product 和 OrderDetail 表中。</span><span class="sxs-lookup"><span data-stu-id="53211-158">When you are bulk loading an XML document with this schema, records are added to the Ord, Product, and OrderDetail tables.</span></span>  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="53211-159">测试工作示例</span><span class="sxs-lookup"><span data-stu-id="53211-159">To test a working sample</span></span>  
  
1.  <span data-ttu-id="53211-160">创建三个表：</span><span class="sxs-lookup"><span data-stu-id="53211-160">Create three tables:</span></span>  
  
    ```  
    CREATE TABLE Ord (  
             OrderID     int  PRIMARY KEY,  
             CustomerID  varchar(5));  
    GO  
    CREATE TABLE Product (  
             ProductID   int PRIMARY KEY,  
             ProductName varchar(20));  
    GO  
    CREATE TABLE OrderDetail (  
           OrderID     int FOREIGN KEY REFERENCES Ord(OrderID),  
           ProductID   int FOREIGN KEY REFERENCES Product(ProductID),  
                       CONSTRAINT OD_key PRIMARY KEY (OrderID, ProductID));  
    GO  
    ```  
  
2.  <span data-ttu-id="53211-161">将本示例中上面提供的架构另存为 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="53211-161">Save the schema that is provided above in this example as SampleSchema.xml.</span></span>  
  
3.  <span data-ttu-id="53211-162">将以下示例 XML 数据另存为 SampleXMLData.xml：</span><span class="sxs-lookup"><span data-stu-id="53211-162">Save the following sample XML data as SampleXMLData.xml:</span></span>  
  
    ```  
    <ROOT>    
      <Order OrderID="1" CustomerID="ALFKI">  
        <Product ProductID="1" ProductName="Chai" />  
        <Product ProductID="2" ProductName="Chang" />  
      </Order>  
      <Order OrderID="2" CustomerID="ANATR">  
        <Product ProductID="3" ProductName="Aniseed Syrup" />  
        <Product ProductID="4" ProductName="Gumbo Mix" />  
      </Order>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="53211-163">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 ValidateAndBulkload.vbs。</span><span class="sxs-lookup"><span data-stu-id="53211-163">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="53211-164">在此文件中，添加本主题前面开头部分提供的 VBScript 代码。</span><span class="sxs-lookup"><span data-stu-id="53211-164">To this file, add the VBScript code that is provided above at the beginning of this topic.</span></span> <span data-ttu-id="53211-165">修改连接字符串以提供适当的服务器和数据库名称。</span><span class="sxs-lookup"><span data-stu-id="53211-165">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="53211-166">从该示例的源代码中取消以下各行的注释。</span><span class="sxs-lookup"><span data-stu-id="53211-166">Uncomment the following lines from the source code for this example.</span></span>  
  
    ```  
    objBL.CheckConstraints = True  
    objBL.Transaction=True  
    ```  
  
5.  <span data-ttu-id="53211-167">执行 VBScript 代码。</span><span class="sxs-lookup"><span data-stu-id="53211-167">Execute the VBScript code.</span></span> <span data-ttu-id="53211-168">XML 大容量加载会将 XML 文档加载到 Ord 表和 Product 表中。</span><span class="sxs-lookup"><span data-stu-id="53211-168">XML Bulk Load loads the XML document into the Ord and Product tables.</span></span>  
  
## <a name="d-bulk-loading-in-identity-type-columns"></a><span data-ttu-id="53211-169">D.</span><span class="sxs-lookup"><span data-stu-id="53211-169">D.</span></span> <span data-ttu-id="53211-170">在标识类型列中执行大容量加载</span><span class="sxs-lookup"><span data-stu-id="53211-170">Bulk loading in identity type columns</span></span>  
 <span data-ttu-id="53211-171">本示例说明大容量加载如何处理标识类型列。</span><span class="sxs-lookup"><span data-stu-id="53211-171">This example illustrates how bulk load handles identity type columns.</span></span> <span data-ttu-id="53211-172">在此示例中，数据将被大容量加载到三个表（Ord、Product 和 OrderDetail）中。</span><span class="sxs-lookup"><span data-stu-id="53211-172">In the example, data is bulk loaded into three tables (Ord, Product, and OrderDetail).</span></span>  
  
 <span data-ttu-id="53211-173">在这些表中：</span><span class="sxs-lookup"><span data-stu-id="53211-173">In these tables:</span></span>  
  
-   <span data-ttu-id="53211-174">Ord 表中的 OrderID 是标识类型列。</span><span class="sxs-lookup"><span data-stu-id="53211-174">OrderID in the Ord table is an identity type column</span></span>  
  
-   <span data-ttu-id="53211-175">Product 表中的 ProductID 是标识类型列。</span><span class="sxs-lookup"><span data-stu-id="53211-175">ProductID in the Product table is an identity type column.</span></span>  
  
-   <span data-ttu-id="53211-176">OrderDetail 中的 OrderID 和 ProductID 列是外键列，它们引用 Ord 和 Product 表中的对应主键列。</span><span class="sxs-lookup"><span data-stu-id="53211-176">OrderID and ProductID columns in the OrderDetail are foreign key columns referring to corresponding primary key columns in the Ord and Product tables.</span></span>  
  
 <span data-ttu-id="53211-177">以下是此示例的表架构：</span><span class="sxs-lookup"><span data-stu-id="53211-177">The following are the table schemas for this example:</span></span>  
  
```  
Ord (OrderID, CustomerID)  
Product (ProductID, ProductName)  
OrderDetail (OrderID, ProductID)  
```  
  
 <span data-ttu-id="53211-178">在 XML 大容量加载的这一示例中，BulkLoad 对象模型的 KeepIdentity 属性设置为 false。</span><span class="sxs-lookup"><span data-stu-id="53211-178">In this example of XML Bulk Load, the KeepIdentity property of the BulkLoad object model is set to false.</span></span> <span data-ttu-id="53211-179">因此，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 会分别为 Product 和 Ord 表中的 ProductID 和 OrderID 列生成标识值（忽略在要进行大容量加载的文档中提供的任何值）。</span><span class="sxs-lookup"><span data-stu-id="53211-179">Therefore, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] generates identity values for the ProductID and OrderID columns in the Product and Ord tables, respectively (any values provided in the documents to be bulk loaded are ignored).</span></span>  
  
 <span data-ttu-id="53211-180">在这种情况下，XML 大容量加载将标识各表之间的主键/外键关系。</span><span class="sxs-lookup"><span data-stu-id="53211-180">In this case, XML Bulk Load identifies the primary key/foreign key relationship among tables.</span></span> <span data-ttu-id="53211-181">大容量加载首先在具有主键的表中插入记录，然后将由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 生成的标识值传播到具有外键列的表中。</span><span class="sxs-lookup"><span data-stu-id="53211-181">Bulk Load first inserts records in the tables with the primary key, then propagates the identity value generated by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to the tables with foreign key columns.</span></span> <span data-ttu-id="53211-182">在下面的示例中，XML 大容量加载按以下顺序在表中插入数据：</span><span class="sxs-lookup"><span data-stu-id="53211-182">In the following example, XML Bulk Load inserts data in tables in this order:</span></span>  
  
1.  <span data-ttu-id="53211-183">产品</span><span class="sxs-lookup"><span data-stu-id="53211-183">Product</span></span>  
  
2.  <span data-ttu-id="53211-184">Ord</span><span class="sxs-lookup"><span data-stu-id="53211-184">Ord</span></span>  
  
3.  <span data-ttu-id="53211-185">OrderDetail</span><span class="sxs-lookup"><span data-stu-id="53211-185">OrderDetail</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="53211-186">为了传播在 Products 和 Orders 表中生成的标识值，处理逻辑要求 XML 大容量加载对这些值保持跟踪，以便以后插入到 OrderDetails 表中。</span><span class="sxs-lookup"><span data-stu-id="53211-186">In order to propagate identity values generated in the Products and Orders tables, the processing logic requires XML Bulk Load to keep track of these values for later insertion into the OrderDetails table.</span></span> <span data-ttu-id="53211-187">为此，XML 大容量加载创建中间表，在这些表中填充数据，之后删除这些表。</span><span class="sxs-lookup"><span data-stu-id="53211-187">To do that, XML Bulk Load creates intermediate tables, populates the data in these tables, and later removes them.</span></span>  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="53211-188">测试工作示例</span><span class="sxs-lookup"><span data-stu-id="53211-188">To test a working sample</span></span>  
  
1.  <span data-ttu-id="53211-189">创建以下表：</span><span class="sxs-lookup"><span data-stu-id="53211-189">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Ord (  
             OrderID     int identity(1,1)  PRIMARY KEY,  
             CustomerID  varchar(5));  
    GO  
    CREATE TABLE Product (  
             ProductID   int identity(1,1) PRIMARY KEY,  
             ProductName varchar(20));  
    GO  
    CREATE TABLE OrderDetail (  
           OrderID     int FOREIGN KEY REFERENCES Ord(OrderID),  
           ProductID   int FOREIGN KEY REFERENCES Product(ProductID),  
                       CONSTRAINT OD_key PRIMARY KEY (OrderID, ProductID));  
    GO  
    ```  
  
2.  <span data-ttu-id="53211-190">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="53211-190">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="53211-191">将此 XSD 架构添加到此文件中。</span><span class="sxs-lookup"><span data-stu-id="53211-191">Add this XSD schema to this file.</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
     <xsd:annotation>  
       <xsd:appinfo>  
        <sql:relationship name="OrderOD"  
              parent="Ord"  
              parent-key="OrderID"  
              child="OrderDetail"  
              child-key="OrderID" />  
        <sql:relationship name="ODProduct"  
              parent="OrderDetail"  
              parent-key="ProductID"  
              child="Product"  
              child-key="ProductID"   
              inverse="true"/>  
       </xsd:appinfo>  
     </xsd:annotation>  
  
      <xsd:element name="Order" sql:relation="Ord"   
                                sql:key-fields="OrderID" >  
       <xsd:complexType>  
         <xsd:sequence>  
            <xsd:element name="Product" sql:relation="Product"   
                         sql:key-fields="ProductID"  
                         sql:relationship="OrderOD ODProduct">  
              <xsd:complexType>  
                 <xsd:attribute name="ProductID" type="xsd:int" />  
                 <xsd:attribute name="ProductName" type="xsd:string" />  
              </xsd:complexType>  
            </xsd:element>  
         </xsd:sequence>  
            <xsd:attribute name="OrderID"   type="xsd:integer" />   
            <xsd:attribute name="CustomerID"   type="xsd:string" />  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="53211-192">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 SampleXMLData.xml。</span><span class="sxs-lookup"><span data-stu-id="53211-192">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="53211-193">添加下列 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="53211-193">Add the following XML document.</span></span>  
  
    ```  
    <ROOT>    
      <Order OrderID="11" CustomerID="ALFKI">  
        <Product ProductID="11" ProductName="Chai" />  
        <Product ProductID="22" ProductName="Chang" />  
      </Order>  
      <Order OrderID="22" CustomerID="ANATR">  
         <Product ProductID="33" ProductName="Aniseed Syrup" />  
        <Product ProductID="44" ProductName="Gumbo Mix" />  
      </Order>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="53211-194">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 ValidateAndBulkload.vbs。</span><span class="sxs-lookup"><span data-stu-id="53211-194">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="53211-195">在此文件中，添加以下 VBScript 代码。</span><span class="sxs-lookup"><span data-stu-id="53211-195">To this file, add the following VBScript code.</span></span> <span data-ttu-id="53211-196">修改连接字符串以提供适当的服务器和数据库名称。</span><span class="sxs-lookup"><span data-stu-id="53211-196">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="53211-197">为用作方法的参数的文件指定适当的路径 `Execute` 。</span><span class="sxs-lookup"><span data-stu-id="53211-197">Specify the appropriate path for the files that serve as parameters to the `Execute` method.</span></span>  
  
    ```  
    Set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "C:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Transaction = False  
    objBL.KeepIdentity = False  
    objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
    Set objBL = Nothing  
    MsgBox "Done."  
    ```  
  
5.  <span data-ttu-id="53211-198">执行 VBScript 代码。</span><span class="sxs-lookup"><span data-stu-id="53211-198">Execute the VBScript code.</span></span> <span data-ttu-id="53211-199">XML 大容量加载会将数据加载到适当的表中。</span><span class="sxs-lookup"><span data-stu-id="53211-199">The XML Bulk Load will load the data into the appropriate tables.</span></span>  
  
## <a name="e-generating-table-schemas-before-bulk-loading"></a><span data-ttu-id="53211-200">E.</span><span class="sxs-lookup"><span data-stu-id="53211-200">E.</span></span> <span data-ttu-id="53211-201">在大容量加载之前生成表架构</span><span class="sxs-lookup"><span data-stu-id="53211-201">Generating table schemas before bulk loading</span></span>  
 <span data-ttu-id="53211-202">如果在大容量加载之前表不存在，则 XML 大容量加载可以选择生成这些表。</span><span class="sxs-lookup"><span data-stu-id="53211-202">XML Bulk Load can optionally generate the tables if they do not exist before bulk loading.</span></span> <span data-ttu-id="53211-203">将 SQLXMLBulkLoad 对象的 SchemaGen 属性设置为 TRUE 可实现此功能。</span><span class="sxs-lookup"><span data-stu-id="53211-203">Setting the SchemaGen property of the SQLXMLBulkLoad object to TRUE does this.</span></span> <span data-ttu-id="53211-204">你还可以选择请求 XML 大容量加载来删除任何现有表，并通过将 SGDropTables 属性设置为 TRUE 来重新创建它们。</span><span class="sxs-lookup"><span data-stu-id="53211-204">You can also optionally request XML Bulk Load to drop any existing tables and re-create them by setting the SGDropTables property to TRUE.</span></span> <span data-ttu-id="53211-205">下面的 VBScript 示例阐释了这些属性的用法。</span><span class="sxs-lookup"><span data-stu-id="53211-205">The following VBScript example illustrates the use of these properties.</span></span>  
  
 <span data-ttu-id="53211-206">此外，此示例将另外两个属性设置为 TRUE：</span><span class="sxs-lookup"><span data-stu-id="53211-206">Also, this example sets two additional properties to TRUE:</span></span>  
  
-   <span data-ttu-id="53211-207">CheckConstraints.</span><span class="sxs-lookup"><span data-stu-id="53211-207">CheckConstraints.</span></span> <span data-ttu-id="53211-208">通过将此属性设置为 TRUE，可确保要插入表中的数据不违反已在表上指定的任何约束（在此情况下，在 Cust 表与 CustOrder 表之间指定了 PRIMARY KEY/FOREIGN KEY 约束）。</span><span class="sxs-lookup"><span data-stu-id="53211-208">Setting this property to TRUE ensures that the data being inserted into the tables does not violate any constraints that have been specified on the tables (in this case the PRIMARY KEY/FOREIGN KEY constraints specified between the Cust and CustOrder tables).</span></span> <span data-ttu-id="53211-209">如果存在约束冲突，则大容量加载失败。</span><span class="sxs-lookup"><span data-stu-id="53211-209">If there is a constraint violation, the bulk load fails.</span></span>  
  
-   <span data-ttu-id="53211-210">XMLFragment.</span><span class="sxs-lookup"><span data-stu-id="53211-210">XMLFragment.</span></span> <span data-ttu-id="53211-211">因为示例 XML 文档（数据源）不包含单一顶级元素（因此它是片段），所以此属性必须设置为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="53211-211">This property must be set to TRUE because the sample XML document (data source) contains no single, top-level element (and is thus a fragment).</span></span>  
  
 <span data-ttu-id="53211-212">以下是 VBScript 代码：</span><span class="sxs-lookup"><span data-stu-id="53211-212">This is the VBScript code:</span></span>  
  
```  
Dim objBL   
Set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
objBL.ErrorLogFile = "c:\error.log"  
  
objBL.CheckConstraints=true  
objBL.XMLFragment = True  
objBL.SchemaGen = True  
objBL.SGDropTables = True  
  
objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
Set objBL = Nothing  
```  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="53211-213">测试工作示例</span><span class="sxs-lookup"><span data-stu-id="53211-213">To test a working sample</span></span>  
  
1.  <span data-ttu-id="53211-214">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="53211-214">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="53211-215">将在前面的示例“使用架构中的链关系大容量加载 XML”中提供的 XSD 架构添加到此文件中。</span><span class="sxs-lookup"><span data-stu-id="53211-215">Add the XSD schema that is provided in the earlier example, "Using chain relationships in the schema to bulk load XML", to the file.</span></span>  
  
2.  <span data-ttu-id="53211-216">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 SampleXMLData.xml。</span><span class="sxs-lookup"><span data-stu-id="53211-216">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="53211-217">将在前面的示例“使用架构中的链关系大容量加载 XML”中提供的 XML 文档添加到此文件中。</span><span class="sxs-lookup"><span data-stu-id="53211-217">Add the XML document that is provided in the earlier example, "Using chain relationships in the schema to bulk load XML", to the file.</span></span> <span data-ttu-id="53211-218">删除 \<ROOT> 文档 (中的元素，使其成为) 片段。</span><span class="sxs-lookup"><span data-stu-id="53211-218">Remove the \<ROOT> element from the document (to make it a fragment).</span></span>  
  
3.  <span data-ttu-id="53211-219">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 ValidateAndBulkload.vbs。</span><span class="sxs-lookup"><span data-stu-id="53211-219">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="53211-220">在此文件中，添加本示例中的 VBScript 代码。</span><span class="sxs-lookup"><span data-stu-id="53211-220">To this file, add the VBScript code in this example.</span></span> <span data-ttu-id="53211-221">修改连接字符串以提供适当的服务器和数据库名称。</span><span class="sxs-lookup"><span data-stu-id="53211-221">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="53211-222">为指定为 Execute 方法的参数的文件指定适当的路径。</span><span class="sxs-lookup"><span data-stu-id="53211-222">Specify the appropriate path for the files that are specified as parameters to the Execute method.</span></span>  
  
4.  <span data-ttu-id="53211-223">执行 VBScript 代码。</span><span class="sxs-lookup"><span data-stu-id="53211-223">Execute the VBScript code.</span></span> <span data-ttu-id="53211-224">XML 大容量加载将根据所提供的映射架构创建必需的表，然后将数据大容量加载到其中。</span><span class="sxs-lookup"><span data-stu-id="53211-224">The XML Bulk Load creates the necessary tables on the basis of the mapping schema that is provided and bulk loads the data in it.</span></span>  
  
## <a name="f-bulk-loading-from-a-stream"></a><span data-ttu-id="53211-225">F.</span><span class="sxs-lookup"><span data-stu-id="53211-225">F.</span></span> <span data-ttu-id="53211-226">从流中执行大容量加载</span><span class="sxs-lookup"><span data-stu-id="53211-226">Bulk loading from a stream</span></span>  
 <span data-ttu-id="53211-227">XML 大容量加载对象模型的 Execute 方法采用两个参数。</span><span class="sxs-lookup"><span data-stu-id="53211-227">The Execute method of the XML Bulk Load object model takes two parameters.</span></span> <span data-ttu-id="53211-228">第一个参数是映射架构文件。</span><span class="sxs-lookup"><span data-stu-id="53211-228">The first parameter is the mapping schema file.</span></span> <span data-ttu-id="53211-229">第二个参数提供要加载到数据库中的 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="53211-229">The second parameter provides the XML data that is to be loaded in the database.</span></span> <span data-ttu-id="53211-230">可以通过两种方法将 XML 数据传递到 XML 大容量加载的 Execute 方法：</span><span class="sxs-lookup"><span data-stu-id="53211-230">There are two ways to pass the XML data to the Execute method of XML Bulk Load:</span></span>  
  
-   <span data-ttu-id="53211-231">指定文件名作为参数。</span><span class="sxs-lookup"><span data-stu-id="53211-231">Specify the file name as the parameter.</span></span>  
  
-   <span data-ttu-id="53211-232">传递包含 XML 数据的流。</span><span class="sxs-lookup"><span data-stu-id="53211-232">Pass a stream that contains the XML data.</span></span>  
  
 <span data-ttu-id="53211-233">本示例说明如何从流中执行大容量加载。</span><span class="sxs-lookup"><span data-stu-id="53211-233">This example illustrates how to bulk load from a stream.</span></span>  
  
 <span data-ttu-id="53211-234">VBScript 首先执行 SELECT 语句从 Northwind 数据库的 Customers 表中检索客户信息。</span><span class="sxs-lookup"><span data-stu-id="53211-234">VBScript first executes a SELECT statement to retrieve customer information from the Customers table in the Northwind database.</span></span> <span data-ttu-id="53211-235">因为在 SELECT 语句中指定了 FOR XML 子句（具有 ELEMENTS 选项），所以，查询将以如下格式返回以元素为中心的 XML 文档：</span><span class="sxs-lookup"><span data-stu-id="53211-235">Because the FOR XML clause is specified (with the ELEMENTS option) in the SELECT statement, the query returns an element-centric XML document of this form:</span></span>  
  
```  
<Customer>  
  <CustomerID>..</CustomerID>  
  <CompanyName>..</CompanyName>  
  <City>..</City>  
</Customer>  
...  
```  
  
 <span data-ttu-id="53211-236">然后，该脚本将 XML 作为流传递到 Execute 方法，作为其第二个参数。</span><span class="sxs-lookup"><span data-stu-id="53211-236">The script then passes the XML as a stream to the Execute method as its second parameter.</span></span> <span data-ttu-id="53211-237">Execute 方法将数据大容量加载到已加入的表中。</span><span class="sxs-lookup"><span data-stu-id="53211-237">The Execute method bulk loads the data into the Cust table.</span></span>  
  
 <span data-ttu-id="53211-238">由于此脚本将 SchemaGen 属性设置为 TRUE，将 SGDropTables 属性设置为 TRUE，因此 XML 大容量加载会在指定数据库中创建 "已创建" 表。</span><span class="sxs-lookup"><span data-stu-id="53211-238">Because this script sets the SchemaGen property to TRUE and SGDropTables property to TRUE, XML Bulk Load creates the Cust table in the specified database.</span></span> <span data-ttu-id="53211-239">（如果该表已经存在，它首先删除此表，然后重新创建该表。）</span><span class="sxs-lookup"><span data-stu-id="53211-239">(If the table already exists, it first drops the table and then re-creates it.)</span></span>  
  
 <span data-ttu-id="53211-240">以下是 VBScript 示例：</span><span class="sxs-lookup"><span data-stu-id="53211-240">This is the VBScript example:</span></span>  
  
```  
Set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
Set objCmd = CreateObject("ADODB.Command")  
Set objConn = CreateObject("ADODB.Connection")  
Set objStrmOut = CreateObject ("ADODB.Stream")  
  
objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
objBL.ErrorLogFile     = "c:\error.log"  
objBL.CheckConstraints = True  
objBL.SchemaGen        = True  
objBL.SGDropTables     = True  
objBL.XMLFragment      = True  
' Open a connection to the instance of SQL Server to get the source data.  
  
objConn.Open "provider=SQLOLEDB;server=(local);database=tempdb;integrated security=SSPI"  
Set objCmd.ActiveConnection = objConn  
objCmd.CommandText = "SELECT CustomerID, CompanyName, City FROM Customers FOR XML AUTO, ELEMENTS"  
  
' Open the return stream and execute the command.  
Const adCRLF = -1  
Const adExecuteStream = 1024  
objStrmOut.Open  
objStrmOut.LineSeparator = adCRLF  
objCmd.Properties("Output Stream").Value = objStrmOut  
objCmd.Execute , , adExecuteStream  
objStrmOut.Position = 0  
  
' Execute bulk load. Read source XML data from the stream.  
objBL.Execute "SampleSchema.xml", objStrmOut  
  
Set objBL = Nothing  
```  
  
 <span data-ttu-id="53211-241">以下 XSD 映射架构提供了创建此表所需的信息：</span><span class="sxs-lookup"><span data-stu-id="53211-241">The following XSD mapping schema provides the necessary information to create the table:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:element name="ROOT" sql:is-constant="true" >  
  <xsd:complexType>  
    <xsd:sequence>  
      <xsd:element ref="Customers"/>  
    </xsd:sequence>  
  </xsd:complexType>  
</xsd:element>  
<xsd:element name="Customers" sql:relation="Cust" >  
  <xsd:complexType>  
    <xsd:sequence>  
      <xsd:element name="CustomerID"  
                   type="xsd:string"  
                   sql:datatype="nvarchar(5)"/>  
      <xsd:element name="CompanyName"  
                   type="xsd:string"  
                   sql:datatype="nvarchar(40)"/>  
      <xsd:element name="City"  
                   type="xsd:string"  
                   sql:datatype="nvarchar(40)"/>  
    </xsd:sequence>  
  </xsd:complexType>  
</xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="53211-242">以下是等效的 XDR 架构：</span><span class="sxs-lookup"><span data-stu-id="53211-242">This is equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust"  >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
    </ElementType>  
</Schema>  
```  
  
### <a name="opening-a-stream-on-an-existing-file"></a><span data-ttu-id="53211-243">在现有文件中打开流</span><span class="sxs-lookup"><span data-stu-id="53211-243">Opening a Stream on an Existing File</span></span>  
 <span data-ttu-id="53211-244">您还可以在现有的 XML 数据文件上打开流，并将该流作为参数传递给 Execute 方法 (而不是将文件名作为参数传递) 。</span><span class="sxs-lookup"><span data-stu-id="53211-244">You can also open a stream on an existing XML data file and pass the stream as a parameter to the Execute method (instead of passing the file name as the parameter).</span></span>  
  
 <span data-ttu-id="53211-245">以下是将流作为参数传递的 Visual Basic 示例：</span><span class="sxs-lookup"><span data-stu-id="53211-245">This is a Visual Basic example of passing a stream as the parameter:</span></span>  
  
```  
Private Sub Form_Load()  
Dim objBL As New SQLXMLBulkLoad  
Dim objStrm As New ADODB.Stream  
Dim objFileSystem As New Scripting.FileSystemObject  
Dim objFile As Scripting.TextStream  
  
MsgBox "Begin BulkLoad..."  
objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
objBL.ErrorLogFile = "c:\error.log"  
objBL.CheckConstraints = True  
objBL.SchemaGen = True  
objBL.SGDropTables = True  
' Here again a stream is specified that contains the source data   
' (instead of the file name). But this is just an illustration.  
' Usually this is useful if you have an XML data   
' stream that is created by some other means that you want to bulk   
' load. This example starts with an XML text file, so it may not be the   
' best to use a stream (you can specify the file name directly).  
' Here you could have specified the file name itself.   
Set objFile = objFileSystem.OpenTextFile("c:\SampleData.xml")  
objStrm.Open  
objStrm.WriteText objFile.ReadAll  
objStrm.Position = 0  
objBL.Execute "c:\SampleSchema.xml", objStrm  
  
Set objBL = Nothing  
MsgBox "Done."  
End Sub  
```  
  
 <span data-ttu-id="53211-246">为了测试应用程序，请使用文件 (SampleData.xml) 中的以下 XML 文档和本示例中提供的 XSD 架构：</span><span class="sxs-lookup"><span data-stu-id="53211-246">To test the application, use the following XML document in a file (SampleData.xml) and the XSD schema that is provided in this example:</span></span>  
  
 <span data-ttu-id="53211-247">以下是 XML 元数据 (SampleData.xml)：</span><span class="sxs-lookup"><span data-stu-id="53211-247">This is the XML source data (SampleData.xml):</span></span>  
  
```  
<ROOT>  
  <Customers>  
    <CustomerID>1111</CustomerID>  
    <CompanyName>Hanari Carnes</CompanyName>  
    <City>NY</City>  
    <Order OrderID="1" />  
    <Order OrderID="2" />  
  </Customers>  
  
  <Customers>  
    <CustomerID>1112</CustomerID>  
    <CompanyName>Toms Spezialitten</CompanyName>  
     <City>LA</City>  
    <Order OrderID="3" />  
  </Customers>  
  <Customers>  
    <CustomerID>1113</CustomerID>  
    <CompanyName>Victuailles en stock</CompanyName>  
    <Order CustomerID= "4444" OrderID="4" />  
</Customers>  
</ROOT>  
```  
  
 <span data-ttu-id="53211-248">这是等效的 XDR 架构：</span><span class="sxs-lookup"><span data-stu-id="53211-248">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
  
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust"  >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
             <sql:relationship  
                key-relation="Cust"  
                key="CustomerID"  
                foreign-key="CustomerID"  
                foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
</Schema>  
```  
  
## <a name="g-bulk-loading-in-overflow-columns"></a><span data-ttu-id="53211-249">G.</span><span class="sxs-lookup"><span data-stu-id="53211-249">G.</span></span> <span data-ttu-id="53211-250">在溢出列中执行大容量加载</span><span class="sxs-lookup"><span data-stu-id="53211-250">Bulk loading in overflow columns</span></span>  
 <span data-ttu-id="53211-251">如果映射架构通过使用 `sql:overflow-field` 批注指定一个溢出列，则 XML 大容量加载会将源文档中的所有未用完的数据复制到此列中。</span><span class="sxs-lookup"><span data-stu-id="53211-251">If the mapping schema specifies an overflow column by using the `sql:overflow-field` annotation, XML Bulk Load copies all unconsumed data from the source document into this column.</span></span>  
  
 <span data-ttu-id="53211-252">请看下面的 XSD 架构：</span><span class="sxs-lookup"><span data-stu-id="53211-252">Consider this XSD schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustCustOrder"  
          parent="Cust"  
          parent-key="CustomerID"  
          child="CustOrder"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  <xsd:element name="Customers" sql:relation="Cust"  
                                sql:overflow-field="OverflowColumn" >  
   <xsd:complexType>  
     <xsd:sequence>  
       <xsd:element name="CustomerID"  type="xsd:integer" />  
       <xsd:element name="CompanyName" type="xsd:string" />  
       <xsd:element name="City"        type="xsd:string" />  
       <xsd:element name="Order"   
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder" >  
         <xsd:complexType>  
          <xsd:attribute name="OrderID" type="xsd:integer" />  
          <xsd:attribute name="CustomerID" type="xsd:integer" />  
         </xsd:complexType>  
       </xsd:element>  
     </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="53211-253">此架构标识 Cust 表的溢出列 (OverflowColumn)。</span><span class="sxs-lookup"><span data-stu-id="53211-253">The schema identifies an overflow column (OverflowColumn) for the Cust table.</span></span> <span data-ttu-id="53211-254">因此，每个元素的所有未用完的 XML 数据 **\<Customer>** 都将添加到此列中。</span><span class="sxs-lookup"><span data-stu-id="53211-254">As a result, all unconsumed XML data for each **\<Customer>** element is added to this column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="53211-255">) 为其指定了**abstract = "true"** (元素的所有抽象元素，并且指定了**禁止 = "true"** (属性) 被 XML 大容量加载时被视为溢出，并将其添加到了溢出列（如果已指定）。</span><span class="sxs-lookup"><span data-stu-id="53211-255">All abstract elements (elements for which **abstract="true"** is specified) and all prohibited attributes (attributes for which **prohibited="true"** is specified) are considered overflow by XML Bulk Load and are added to the overflow column, if specified.</span></span> <span data-ttu-id="53211-256">（否则，将忽略它们。）</span><span class="sxs-lookup"><span data-stu-id="53211-256">(Otherwise, they are ignored.)</span></span>  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="53211-257">测试工作示例</span><span class="sxs-lookup"><span data-stu-id="53211-257">To test a working sample</span></span>  
  
1.  <span data-ttu-id="53211-258">在**tempdb**数据库中创建两个表：</span><span class="sxs-lookup"><span data-stu-id="53211-258">Create two tables in **tempdb** database:</span></span>  
  
    ```  
    USE tempdb;  
    CREATE TABLE Cust (  
                  CustomerID     int         PRIMARY KEY,  
                  CompanyName    varchar(20) NOT NULL,  
                  City           varchar(20) DEFAULT 'Seattle',  
                  OverflowColumn nvarchar(200));  
    GO  
    CREATE TABLE CustOrder (  
                  OrderID    int PRIMARY KEY,  
                  CustomerID int FOREIGN KEY   
                                 REFERENCES Cust(CustomerID));  
    GO  
    ```  
  
2.  <span data-ttu-id="53211-259">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="53211-259">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="53211-260">将在本示例中提供的 XSD 架构添加到此文件中。</span><span class="sxs-lookup"><span data-stu-id="53211-260">Add the XSD schema that is provided in this example to the file.</span></span>  
  
3.  <span data-ttu-id="53211-261">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 SampleXMLData.xml。</span><span class="sxs-lookup"><span data-stu-id="53211-261">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="53211-262">将以下 XML 文档添加到此文件中：</span><span class="sxs-lookup"><span data-stu-id="53211-262">Add the following XML document to the file:</span></span>  
  
    ```  
    <ROOT>  
      <Customers>  
        <CustomerID>1111</CustomerID>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City><![CDATA[NY]]> </City>  
        <Junk>garbage in overflow</Junk>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
      </Customers>  
  
      <Customers>  
        <CustomerID>1112</CustomerID>  
        <CompanyName>Toms Spezialitten</CompanyName>  
         <![CDATA[LA]]>   
        <!-- <xyz><address>111 Maple, Seattle</address></xyz>   -->  
        <Order OrderID="3" />  
      </Customers>  
      <Customers>  
        <CustomerID>1113</CustomerID>  
        <CompanyName>Victuailles en stock</CompanyName>  
        <Order OrderID="4" />  
    </Customers>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="53211-263">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 ValidateAndBulkload.vbs。</span><span class="sxs-lookup"><span data-stu-id="53211-263">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="53211-264">在此文件中，添加以下 Microsoft Visual Basic Scripting Edition (VBScript) 代码。</span><span class="sxs-lookup"><span data-stu-id="53211-264">To this file, add the following Microsoft Visual Basic Scripting Edition (VBScript) code.</span></span> <span data-ttu-id="53211-265">修改连接字符串以提供适当的服务器和数据库名称。</span><span class="sxs-lookup"><span data-stu-id="53211-265">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="53211-266">为指定为 Execute 方法的参数的文件指定适当的路径。</span><span class="sxs-lookup"><span data-stu-id="53211-266">Specify the appropriate path for the files that are specified as parameters to the Execute method.</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
5.  <span data-ttu-id="53211-267">执行 VBScript 代码。</span><span class="sxs-lookup"><span data-stu-id="53211-267">Execute the VBScript code.</span></span>  
  
 <span data-ttu-id="53211-268">这是等效的 XDR 架构：</span><span class="sxs-lookup"><span data-stu-id="53211-268">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
  
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust"   
                       sql:overflow-field="OverflowColumn"  >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
             <sql:relationship  
                key-relation="Cust"  
                key="CustomerID"  
                foreign-key="CustomerID"  
                foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
</Schema>  
```  
  
## <a name="h-specifying-the-file-path-for-temp-files-in-transaction-mode"></a><span data-ttu-id="53211-269">H.</span><span class="sxs-lookup"><span data-stu-id="53211-269">H.</span></span> <span data-ttu-id="53211-270">在事务模式下为 temp 文件指定文件路径</span><span class="sxs-lookup"><span data-stu-id="53211-270">Specifying the file path for temp files in transaction mode</span></span>  
 <span data-ttu-id="53211-271">在事务模式下进行大容量加载时 (也就是说，当 Transaction 属性设置为 TRUE) 时，如果满足以下条件之一，则还必须设置 TempFilePath 属性：</span><span class="sxs-lookup"><span data-stu-id="53211-271">When you are bulk loading in transaction mode (that is, when the Transaction property is set to TRUE), you also must set the TempFilePath property when either of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="53211-272">您要大容量加载到远程服务器。</span><span class="sxs-lookup"><span data-stu-id="53211-272">You are bulk loading to a remote server.</span></span>  
  
-   <span data-ttu-id="53211-273">您要使用备用本地驱动器或文件夹（不同于由 TEMP 环境变量指定的路径）存储在事务模式下创建的临时文件。</span><span class="sxs-lookup"><span data-stu-id="53211-273">You want to use an alternate local drive or folder (one other than the path that is specified by the TEMP environment variable) to store the temporary files that are created in the transaction mode.</span></span>  
  
 <span data-ttu-id="53211-274">例如，以下 VBScript 代码在事务模式下将 SampleXMLData.xml 文件中的数据大容量加载到数据库表中。</span><span class="sxs-lookup"><span data-stu-id="53211-274">For example, the following VBScript code bulk loads data from the SampleXMLData.xml file into the database tables in transaction mode.</span></span> <span data-ttu-id="53211-275">指定 TempFilePath 属性以设置在事务模式下生成的临时文件的路径。</span><span class="sxs-lookup"><span data-stu-id="53211-275">The TempFilePath property is specified to set the path for the temporary files that are generated in transaction mode.</span></span>  
  
```  
set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
objBL.ErrorLogFile = "c:\error.log"  
objBL.CheckConstraints = True  
objBL.Transaction=True  
objBL.TempFilePath="\\Server\MyDir"  
objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
set objBL=Nothing  
```  
  
> [!NOTE]  
>  <span data-ttu-id="53211-276">此临时文件路径必须是一个共享位置，该共享位置可供 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的目标实例的服务帐户和运行大容量加载应用程序的帐户访问。</span><span class="sxs-lookup"><span data-stu-id="53211-276">The temporary file path must be a shared location that is accessible to the service account of the target instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and to the account that is running the bulk load application.</span></span> <span data-ttu-id="53211-277">除非在本地服务器上进行大容量加载，否则临时文件路径必须是 UNC 路径 (例如 \\ \servername\sharename ....) 。</span><span class="sxs-lookup"><span data-stu-id="53211-277">Unless you are bulk loading on a local server, the temporary file path must be a UNC path (such as \\\servername\sharename).</span></span>  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="53211-278">测试工作示例</span><span class="sxs-lookup"><span data-stu-id="53211-278">To test a working sample</span></span>  
  
1.  <span data-ttu-id="53211-279">在**tempdb**数据库中创建此表：</span><span class="sxs-lookup"><span data-stu-id="53211-279">Create this table in **tempdb** database:</span></span>  
  
    ```  
    USE tempdb;  
    CREATE TABLE Cust (     CustomerID uniqueidentifier,   
          LastName  varchar(20));  
    GO  
    ```  
  
2.  <span data-ttu-id="53211-280">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="53211-280">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="53211-281">将以下 XSD 架构添加到此文件中：</span><span class="sxs-lookup"><span data-stu-id="53211-281">Add the following XSD schema to the file:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
      <xsd:element name="ROOT" sql:is-constant="true" >  
        <xsd:complexType>  
          <xsd:sequence>  
            <xsd:element ref="Customers" />  
          </xsd:sequence>  
        </xsd:complexType>  
      </xsd:element>  
  
      <xsd:element name="Customers" sql:relation="Cust" >  
       <xsd:complexType>  
         <xsd:attribute name="CustomerID"  type="xsd:string" />  
         <xsd:attribute name="LastName" type="xsd:string" />  
       </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="53211-282">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 SampleXMLData.xml。</span><span class="sxs-lookup"><span data-stu-id="53211-282">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="53211-283">将以下 XML 文档添加到此文件中：</span><span class="sxs-lookup"><span data-stu-id="53211-283">Add the following XML document to the file:</span></span>  
  
    ```  
    <ROOT>  
    <Customers CustomerID="6F9619FF-8B86-D011-B42D-00C04FC964FF"   
               LastName="Smith" />  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="53211-284">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 ValidateAndBulkload.vbs。</span><span class="sxs-lookup"><span data-stu-id="53211-284">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="53211-285">在此文件中，添加以下 VBScript 代码。</span><span class="sxs-lookup"><span data-stu-id="53211-285">To this file, add the following VBScript code.</span></span> <span data-ttu-id="53211-286">修改连接字符串以提供适当的服务器和数据库名称。</span><span class="sxs-lookup"><span data-stu-id="53211-286">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="53211-287">为指定为 Execute 方法的参数的文件指定适当的路径。</span><span class="sxs-lookup"><span data-stu-id="53211-287">Specify the appropriate path for the files that are specified as parameters to the Execute method.</span></span> <span data-ttu-id="53211-288">同时为 TempFilePath 属性指定适当的路径。</span><span class="sxs-lookup"><span data-stu-id="53211-288">Also specify the appropriate path for the TempFilePath property.</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Transaction=True  
    objBL.TempFilePath="\\server\folder"  
    objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
5.  <span data-ttu-id="53211-289">执行 VBScript 代码。</span><span class="sxs-lookup"><span data-stu-id="53211-289">Execute the VBScript code.</span></span>  
  
     <span data-ttu-id="53211-290">`sql:datatype`当**customerid**的值指定为包含大括号 ( {and} ) 的 GUID 时，架构必须为**customerid**属性指定对应的，例如：</span><span class="sxs-lookup"><span data-stu-id="53211-290">The schema must specify the corresponding `sql:datatype` for the **CustomerID** attribute when the value for **CustomerID** is specified as a GUID that includes braces ({ and }), such as:</span></span>  
  
    ```  
    <ROOT>  
    <Customers CustomerID="{6F9619FF-8B86-D011-B42D-00C04FC964FF}"   
               LastName="Smith" />  
    </ROOT>  
    ```  
  
     <span data-ttu-id="53211-291">以下是更新后的架构：</span><span class="sxs-lookup"><span data-stu-id="53211-291">This is the updated schema:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
      <xsd:element name="ROOT" sql:is-constant="true" >  
        <xsd:complexType>  
          <xsd:sequence>  
            <xsd:element ref="Customers" />  
          </xsd:sequence>  
        </xsd:complexType>  
      </xsd:element>  
  
      <xsd:element name="Customers" sql:relation="Cust" >  
       <xsd:complexType>  
         <xsd:attribute name="CustomerID"  type="xsd:string"   
                        sql:datatype="uniqueidentifier" />  
         <xsd:attribute name="LastName" type="xsd:string" />  
       </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
     <span data-ttu-id="53211-292">如果 `sql:datatype` 指定将列类型标识为 `uniqueidentifier` ，则大容量加载操作将从**CustomerID**值中删除大括号 ( {and} ) ，然后将其插入列中。</span><span class="sxs-lookup"><span data-stu-id="53211-292">When `sql:datatype` is specified identifying the column type as `uniqueidentifier`, the bulk load operation removes the braces ({ and }) from the **CustomerID** value before inserting it in the column.</span></span>  
  
 <span data-ttu-id="53211-293">这是等效的 XDR 架构：</span><span class="sxs-lookup"><span data-stu-id="53211-293">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
<ElementType name="ROOT" sql:is-constant="1">  
      <element type="Customers" />  
</ElementType>  
<ElementType name="Customers" sql:relation="Cust" >  
  <AttributeType name="CustomerID"  sql:datatype="uniqueidentifier" />  
  <AttributeType name="LastName"   />  
  
  <attribute type="CustomerID" />  
  <attribute type="LastName"   />  
</ElementType>  
</Schema>  
```  
  
## <a name="i-using-an-existing-database-connection-with-the-connectioncommand-property"></a><span data-ttu-id="53211-294">I.</span><span class="sxs-lookup"><span data-stu-id="53211-294">I.</span></span> <span data-ttu-id="53211-295">将现有数据库连接用于 ConnectionCommand 属性</span><span class="sxs-lookup"><span data-stu-id="53211-295">Using an existing database connection with the ConnectionCommand property</span></span>  
 <span data-ttu-id="53211-296">可以使用现有 ADO 连接以大容量加载 XML。</span><span class="sxs-lookup"><span data-stu-id="53211-296">You can use an existing ADO connection to bulk load XML.</span></span> <span data-ttu-id="53211-297">如果 XML 大容量加载只是将对数据源执行的许多操作之一，则这一点很有用。</span><span class="sxs-lookup"><span data-stu-id="53211-297">This is useful if XML Bulk Load is just one of many operations that will be performed on a data source.</span></span>  
  
 <span data-ttu-id="53211-298">ConnectionCommand 属性使你能够通过使用 ADO 命令对象来使用现有 ADO 连接。</span><span class="sxs-lookup"><span data-stu-id="53211-298">The ConnectionCommand property enables you to use an existing ADO connection by using an ADO command object.</span></span> <span data-ttu-id="53211-299">下面的 Visual Basic 示例说明了这一点：</span><span class="sxs-lookup"><span data-stu-id="53211-299">This is illustrated in the following Visual Basic example:</span></span>  
  
```  
Private Sub Form_Load()  
Dim objBL As New SQLXMLBulkLoad4  
Dim objCmd As New ADODB.Command  
Dim objConn As New ADODB.Connection  
  
'Open a connection to an instance of SQL Server.  
objConn.Open "provider=SQLOLEDB;data source=(local);database=tempdb;integrated security=SSPI"  
'Ask the Command object to use the connection just established.  
Set objCmd.ActiveConnection = objConn  
  
'Tell Bulk Load to use the active command object that is using the Connection obj.  
objBL.ConnectionCommand = objCmd  
objBL.ErrorLogFile = "c:\error.log"  
objBL.CheckConstraints = True  
'The Transaction property must be set to True if you use ConnectionCommand.  
objBL.Transaction = True  
objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
Set objBL = Nothing  
End Sub  
```  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="53211-300">测试工作示例</span><span class="sxs-lookup"><span data-stu-id="53211-300">To test a working sample</span></span>  
  
1.  <span data-ttu-id="53211-301">在**tempdb**数据库中创建两个表：</span><span class="sxs-lookup"><span data-stu-id="53211-301">Create two tables in **tempdb** database:</span></span>  
  
    ```  
    USE tempdb;  
    CREATE TABLE Cust(  
                   CustomerID   varchar(5) PRIMARY KEY,  
                   CompanyName  varchar(30),  
                   City         varchar(20));  
    GO  
    CREATE TABLE CustOrder(  
                   CustomerID  varchar(5) references Cust (CustomerID),  
                   OrderID     varchar(5) PRIMARY KEY);  
    GO  
    ```  
  
2.  <span data-ttu-id="53211-302">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="53211-302">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="53211-303">将以下 XSD 架构添加到此文件中：</span><span class="sxs-lookup"><span data-stu-id="53211-303">Add the following XSD schema to the file:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
    <xsd:annotation>  
      <xsd:appinfo>  
        <sql:relationship name="CustCustOrder"  
              parent="Cust"  
              parent-key="CustomerID"  
              child="CustOrder"  
              child-key="CustomerID" />  
      </xsd:appinfo>  
    </xsd:annotation>  
      <xsd:element name="ROOT" sql:is-constant="true" >  
        <xsd:complexType>  
          <xsd:sequence>  
            <xsd:element ref="Customers" />  
          </xsd:sequence>  
        </xsd:complexType>  
      </xsd:element>  
      <xsd:element name="Customers" sql:relation="Cust" >  
       <xsd:complexType>  
         <xsd:sequence>  
           <xsd:element name="CustomerID"  type="xsd:integer" />  
           <xsd:element name="CompanyName" type="xsd:string" />  
           <xsd:element name="City"        type="xsd:string" />  
           <xsd:element name="Order"   
                              sql:relation="CustOrder"  
                              sql:relationship="CustCustOrder" >  
             <xsd:complexType>  
              <xsd:attribute name="OrderID" type="xsd:integer" />  
              <xsd:attribute name="CustomerID" type="xsd:integer" />  
             </xsd:complexType>  
           </xsd:element>  
         </xsd:sequence>  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="53211-304">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 SampleXMLData.xml。</span><span class="sxs-lookup"><span data-stu-id="53211-304">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="53211-305">将以下 XML 文档添加到此文件中：</span><span class="sxs-lookup"><span data-stu-id="53211-305">Add the following XML document to the file:</span></span>  
  
    ```  
    <ROOT>  
      <Customers>  
        <CustomerID>1111</CustomerID>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City>NY</City>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
      </Customers>  
  
      <Customers>  
        <CustomerID>1112</CustomerID>  
        <CompanyName>Toms Spezialitten</CompanyName>  
         <City>LA</City>  
        <Order OrderID="3" />  
      </Customers>  
      <Customers>  
        <CustomerID>1113</CustomerID>  
        <CompanyName>Victuailles en stock</CompanyName>  
        <Order OrderID="4" />  
    </Customers>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="53211-306">创建 Visual Basic（标准 EXE）应用程序以及以上代码。</span><span class="sxs-lookup"><span data-stu-id="53211-306">Create a Visual Basic (Standard EXE) application and the preceding code.</span></span> <span data-ttu-id="53211-307">将这些引用添加到项目中：</span><span class="sxs-lookup"><span data-stu-id="53211-307">Add these references to the project:</span></span>  
  
    ```  
    Microsoft XML BulkLoad for SQL Server 4.0 Type Library  
    Microsoft ActiveX Data objects 2.6 Library  
    ```  
  
5.  <span data-ttu-id="53211-308">执行应用程序。</span><span class="sxs-lookup"><span data-stu-id="53211-308">Execute the application.</span></span>  
  
 <span data-ttu-id="53211-309">这是等效的 XDR 架构：</span><span class="sxs-lookup"><span data-stu-id="53211-309">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust"  >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
         <sql:relationship  
                key-relation="Cust"  
                key="CustomerID"  
                foreign-key="CustomerID"  
                foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
</Schema>  
```  
  
## <a name="j-bulk-loading-in-xml-data-type-columns"></a><span data-ttu-id="53211-310">J.</span><span class="sxs-lookup"><span data-stu-id="53211-310">J.</span></span> <span data-ttu-id="53211-311">在 xml 数据类型列中执行大容量加载</span><span class="sxs-lookup"><span data-stu-id="53211-311">Bulk loading in xml Data Type columns</span></span>  
 <span data-ttu-id="53211-312">如果映射架构通过使用批注指定了[xml 数据类型](/sql/t-sql/xml/xml-transact-sql)列 `sql:datatype="xml"` ，Xml 大容量加载可以将源文档中映射字段的 xml 子元素复制到此列中。</span><span class="sxs-lookup"><span data-stu-id="53211-312">If the mapping schema specifies a [xml data type](/sql/t-sql/xml/xml-transact-sql) column by using the `sql:datatype="xml"` annotation, XML Bulk Load can copy XML child elements for the mapped field from the source document into this column.</span></span>  
  
 <span data-ttu-id="53211-313">请看以下 XSD 架构，它映射 AdventureWorks 示例数据库中 Production.ProductModel 表的视图。</span><span class="sxs-lookup"><span data-stu-id="53211-313">Consider the following XSD schema, which maps a view of the Production.ProductModel table in the AdventureWorks sample database.</span></span> <span data-ttu-id="53211-314">在此表中， `xml` 使用和批注将数据类型的 CatalogDescription 字段映射到 **\<Desc>** 元素 `sql:field` `sql:datatype="xml"` 。</span><span class="sxs-lookup"><span data-stu-id="53211-314">In this table, the CatalogDescription field of `xml` data type is mapped to a **\<Desc>** element using the `sql:field` and `sql:datatype="xml"` annotations.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
           xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
           xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">   
  <xsd:element name="ProductModel"  sql:relation="Production.ProductModel" >  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Name" type="xs:string"></xsd:element>  
        <xsd:element name="Desc" sql:field="CatalogDescription" sql:datatype="xml">  
        <xsd:complexType>  
          <xsd:sequence>  
            <xsd:element name="ProductDescription">  
              <xsd:complexType>  
                <xsd:sequence>  
                  <xsd:element name="Summary" type="xs:anyType"/>  
                </xsd:sequence>  
              </xsd:complexType>  
            </xsd:element>  
          </xsd:sequence>  
        </xsd:complexType>  
        </xsd:element>   
     </xsd:sequence>  
     <xsd:attribute name="ProductModelID" sql:field="ProductModelID" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="53211-315">测试工作示例</span><span class="sxs-lookup"><span data-stu-id="53211-315">To test a working sample</span></span>  
  
1.  <span data-ttu-id="53211-316">验证已安装了 AdventureWorks 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="53211-316">Verify that the AdventureWorks sample database is installed.</span></span>  
  
2.  <span data-ttu-id="53211-317">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="53211-317">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="53211-318">复制上面的 XSD 架构并将其粘贴到文件中，然后保存该文件。</span><span class="sxs-lookup"><span data-stu-id="53211-318">Copy the XSD schema above and paste it into the file and save it.</span></span>  
  
3.  <span data-ttu-id="53211-319">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 SampleXMLData.xml。</span><span class="sxs-lookup"><span data-stu-id="53211-319">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="53211-320">复制以下 XML 文档并将其粘贴到该文件中，然后将其保存到上一步中所用的同一个文件夹中。</span><span class="sxs-lookup"><span data-stu-id="53211-320">Copy the following XML document below and paste it into the file and save it in the same folder as was used for the previous step.</span></span>  
  
    ```  
    <ProductModel ProductModelID="2005">  
        <Name>Mountain-100 (2005 model)</Name>  
        <Desc><?xml-stylesheet href="ProductDescription.xsl" type="text/xsl"?>  
            <p1:ProductDescription xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription"   
                  xmlns:wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"   
                  xmlns:wf="http://www.adventure-works.com/schemas/OtherFeatures"   
                  xmlns:html="http://www.w3.org/1999/xhtml"   
                  xmlns="">  
                <p1:Summary>  
                    <html:p>Our top-of-the-line competition mountain bike.   
          Performance-enhancing options include the innovative HL Frame,   
          super-smooth front suspension, and traction for all terrain.  
                            </html:p>  
                </p1:Summary>  
                <p1:Manufacturer>  
                    <p1:Name>AdventureWorks</p1:Name>  
                    <p1:Copyright>2002-2005</p1:Copyright>  
                    <p1:ProductURL>HTTP://www.Adventure-works.com</p1:ProductURL>  
                </p1:Manufacturer>  
                <p1:Features>These are the product highlights.   
                     <wm:Warranty>  
                        <wm:WarrantyPeriod>3 years</wm:WarrantyPeriod>  
                        <wm:Description>parts and labor</wm:Description>  
                    </wm:Warranty><wm:Maintenance>  
                        <wm:NoOfYears>10 years</wm:NoOfYears>  
                        <wm:Description>maintenance contract available through your dealer or any AdventureWorks retail store.</wm:Description>  
                    </wm:Maintenance><wf:wheel>High performance wheels.</wf:wheel><wf:saddle>  
                        <html:i>Anatomic design</html:i> and made from durable leather for a full-day of riding in comfort.</wf:saddle><wf:pedal>  
                        <html:b>Top-of-the-line</html:b> clipless pedals with adjustable tension.</wf:pedal><wf:BikeFrame>Each frame is hand-crafted in our Bothell facility to the optimum diameter   
          and wall-thickness required of a premium mountain frame.   
          The heat-treated welded aluminum frame has a larger diameter tube that absorbs the bumps.</wf:BikeFrame><wf:crankset> Triple crankset; alumunim crank arm; flawless shifting. </wf:crankset></p1:Features>  
                <!-- add one or more of these elements... one for each specific product in this product model -->  
                <p1:Picture>  
                    <p1:Angle>front</p1:Angle>  
                    <p1:Size>small</p1:Size>  
                    <p1:ProductPhotoID>118</p1:ProductPhotoID>  
                </p1:Picture>  
                <!-- add any tags in <specifications> -->  
                <p1:Specifications> These are the product specifications.  
                       <Material>Almuminum Alloy</Material><Color>Available in most colors</Color><ProductLine>Mountain bike</ProductLine><Style>Unisex</Style><RiderExperience>Advanced to Professional riders</RiderExperience></p1:Specifications>  
            </p1:ProductDescription>  
        </Desc>  
    </ProductModel>  
    ```  
  
4.  <span data-ttu-id="53211-321">在您首选的文本编辑器或 XML 编辑器中创建文件，然后将其另存为 BulkloadXml.vbs。</span><span class="sxs-lookup"><span data-stu-id="53211-321">Create a file in your preferred text or XML editor, and save it as BulkloadXml.vbs.</span></span> <span data-ttu-id="53211-322">复制下面的 VBScript 代码并将其粘贴到该文件中。</span><span class="sxs-lookup"><span data-stu-id="53211-322">Copy the following VBScript code and paste it into the file.</span></span> <span data-ttu-id="53211-323">将其保存到用于先前的 XML 数据和架构文件的相同文件夹中。</span><span class="sxs-lookup"><span data-stu-id="53211-323">Save it in the same folder as was used for the previous XML data and schema files.</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=MyServer;database=AdventureWorks;integrated security=SSPI"  
  
    Dim fso, sAppPath  
    Set fso = CreateObject("Scripting.FileSystemObject")   
    sAppPath = fso.GetFolder(".")   
  
    objBL.ErrorLogFile = sAppPath & "\error.log"  
  
    'Execute XML bulkload using file.  
    objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
5.  <span data-ttu-id="53211-324">执行 BulkloadXml.vbs 脚本。</span><span class="sxs-lookup"><span data-stu-id="53211-324">Execute the BulkloadXml.vbs script.</span></span>  
  
  
