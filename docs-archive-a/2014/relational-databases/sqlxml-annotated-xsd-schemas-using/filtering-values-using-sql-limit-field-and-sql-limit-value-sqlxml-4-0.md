---
title: 使用 sql： limit-字段和 sql： limit-value (SQLXML 4.0) 来筛选值 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, filtering values
- limiting values [SQLXML]
- limit-value annotation
- limit-field annotation
- sql:limit-field
- sql:limit-value
- filtering [SQLXML]
ms.assetid: c0f7ae92-eeec-430e-a66a-f22c3ae64a5e
author: rothja
ms.author: jroth
ms.openlocfilehash: 7886a9a6f51c76ed693576ca6f4659f4051d1f20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693675"
---
# <a name="filtering-values-using-sqllimit-field-and-sqllimit-value-sqlxml-40"></a><span data-ttu-id="67f09-102">使用 sql:limit-field 和 sql:limit-value 筛选值 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="67f09-102">Filtering Values Using sql:limit-field and sql:limit-value (SQLXML 4.0)</span></span>
  <span data-ttu-id="67f09-103">可以基于某些限制值来限制从数据库查询返回的行。</span><span class="sxs-lookup"><span data-stu-id="67f09-103">You can limit rows that are returned from a database query on the basis of some limiting value.</span></span> <span data-ttu-id="67f09-104">`sql:limit-field` 和 `sql:limit-value` 批注用于标识包含限制值的数据库列和指定用于筛选返回的数据的特定限制值。</span><span class="sxs-lookup"><span data-stu-id="67f09-104">The `sql:limit-field` and `sql:limit-value` annotations are used to identify the database column that contains limiting values and to specify a specific limiting value to be used to filter the data returned.</span></span>  
  
 <span data-ttu-id="67f09-105">`sql:limit-field` 批注用于标识包含限制值的列；对于每个映射的元素或属性允许该批注。</span><span class="sxs-lookup"><span data-stu-id="67f09-105">The `sql:limit-field` annotation is used to identify a column that contains a limiting value; it is allowed on each mapped element or attribute.</span></span>  
  
 <span data-ttu-id="67f09-106">`sql:limit-value` 批注用于指定在 `sql:limit-field` 批注所指定的列中的受限制值。</span><span class="sxs-lookup"><span data-stu-id="67f09-106">The `sql:limit-value` annotation is used to specify the limited value in the column that is specified in the `sql:limit-field` annotation.</span></span> <span data-ttu-id="67f09-107">`sql:limit-value` 批注是可选的。</span><span class="sxs-lookup"><span data-stu-id="67f09-107">The `sql:limit-value` annotation is optional.</span></span> <span data-ttu-id="67f09-108">如果未指定 `sql:limit-value`，将采用 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="67f09-108">If `sql:limit-value` is not specified, a NULL value is assumed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67f09-109">使用 `sql:limit-field`（其中映射的 SQL 列为 `real` 类型）时，SQLXML 4.0 对 `sql:limit-value` 执行转换（如作为 `nvarchar` 指定值在 XML 架构中指定）。</span><span class="sxs-lookup"><span data-stu-id="67f09-109">When working with a `sql:limit-field` where the mapped SQL column is of type `real`, SQLXML 4.0 performs conversion on the `sql:limit-value` as specified in XML schemas as an `nvarchar` specified value.</span></span> <span data-ttu-id="67f09-110">这要求使用纯科学记数法指定小数限制值。</span><span class="sxs-lookup"><span data-stu-id="67f09-110">This requires that decimal limit values be specified using full scientific notation.</span></span> <span data-ttu-id="67f09-111">有关详细信息，请参阅下面的示例 B。</span><span class="sxs-lookup"><span data-stu-id="67f09-111">For more information, see Example B below.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="67f09-112">示例</span><span class="sxs-lookup"><span data-stu-id="67f09-112">Examples</span></span>  
 <span data-ttu-id="67f09-113">若要创建使用这些示例的工作示例，需要安装以下产品：</span><span class="sxs-lookup"><span data-stu-id="67f09-113">To create working samples using these examples, you need to have the following installed:</span></span>  
  
-   <span data-ttu-id="67f09-114">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span><span class="sxs-lookup"><span data-stu-id="67f09-114">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span></span>  
  
-   <span data-ttu-id="67f09-115">MDAC 2.6 或更高版本</span><span class="sxs-lookup"><span data-stu-id="67f09-115">MDAC 2.6 or later</span></span>  
  
 <span data-ttu-id="67f09-116">在这些示例中，使用模板来指定针对映射 XSD 架构的 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="67f09-116">In these examples, templates are used to specify XPath queries against the mapping XSD schema.</span></span>  
  
### <a name="a-limiting-the-customer-addresses-returned-to-a-specific-address-type"></a><span data-ttu-id="67f09-117">A.</span><span class="sxs-lookup"><span data-stu-id="67f09-117">A.</span></span> <span data-ttu-id="67f09-118">将返回的客户地址限制为特定地址类型</span><span class="sxs-lookup"><span data-stu-id="67f09-118">Limiting the customer addresses returned to a specific address type</span></span>  
 <span data-ttu-id="67f09-119">在此示例中，数据库包含两个表：</span><span class="sxs-lookup"><span data-stu-id="67f09-119">In this example, a database contains two tables:</span></span>  
  
-   <span data-ttu-id="67f09-120">Customer (CustomerID, CompanyName)</span><span class="sxs-lookup"><span data-stu-id="67f09-120">Customer (CustomerID, CompanyName)</span></span>  
  
-   <span data-ttu-id="67f09-121">Addresses (CustomerID, AddressType, StreetAddress)</span><span class="sxs-lookup"><span data-stu-id="67f09-121">Addresses (CustomerID, AddressType, StreetAddress)</span></span>  
  
 <span data-ttu-id="67f09-122">一个客户可以具有发货地址和/或开票地址。</span><span class="sxs-lookup"><span data-stu-id="67f09-122">A customer can have a shipping address and/or a billing address.</span></span> <span data-ttu-id="67f09-123">AddressType 列值是 Shipping 和 Billing。</span><span class="sxs-lookup"><span data-stu-id="67f09-123">The AddressType column values are Shipping and Billing.</span></span>  
  
 <span data-ttu-id="67f09-124">这是映射架构，其中**ShipTo**架构属性映射到地址关系中的 StreetAddress 列。</span><span class="sxs-lookup"><span data-stu-id="67f09-124">This is the mapping schema in which the **ShipTo** schema attribute maps to the StreetAddress column in the Addresses relation.</span></span> <span data-ttu-id="67f09-125">此属性返回的值仅限于通过指定和批注来发送地址 `sql:limit-field` `sql:limit-value` 。</span><span class="sxs-lookup"><span data-stu-id="67f09-125">The values that are returned for this attribute are limited to only shipping addresses by specifying the `sql:limit-field` and `sql:limit-value` annotations.</span></span> <span data-ttu-id="67f09-126">同样， **BillTo**架构特性仅返回客户的帐单地址。</span><span class="sxs-lookup"><span data-stu-id="67f09-126">Similarly, the **BillTo** schema attribute returns only the billing address of a customer.</span></span>  
  
 <span data-ttu-id="67f09-127">以下是架构：</span><span class="sxs-lookup"><span data-stu-id="67f09-127">This is the schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustAddr"  
        parent="Customer"  
        parent-key="CustomerID"  
        child="Addresses"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Customer" >  
   <xsd:complexType>  
        <xsd:sequence>  
        <xsd:element name="BillTo"   
                       type="xsd:string"   
                       sql:relation="Addresses"   
                       sql:field="StreetAddress"  
                       sql:limit-field="AddressType"  
                       sql:limit-value="billing"  
                       sql:relationship="CustAddr" >  
        </xsd:element>  
        <xsd:element name="ShipTo"   
                       type="xsd:string"   
                       sql:relation="Addresses"   
                       sql:field="StreetAddress"  
                       sql:limit-field="AddressType"  
                       sql:limit-value="shipping"  
                       sql:relationship="CustAddr" >  
        </xsd:element>  
        </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:int" />   
        <xsd:attribute name="CompanyName"  type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="67f09-128">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="67f09-128">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="67f09-129">在**tempdb**数据库中创建两个表：</span><span class="sxs-lookup"><span data-stu-id="67f09-129">Create two tables in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Customer (CustomerID int primary key,   
                           CompanyName varchar(30))  
    CREATE TABLE Addresses(CustomerID int,   
                           StreetAddress varchar(50),  
                           AddressType varchar(10))  
    ```  
  
2.  <span data-ttu-id="67f09-130">添加示例数据：</span><span class="sxs-lookup"><span data-stu-id="67f09-130">Add the sample data:</span></span>  
  
    ```  
    INSERT INTO Customer values (1, 'Company A')  
    INSERT INTO Customer values (2, 'Company B')  
  
    INSERT INTO Addresses values  
               (1, 'Obere Str. 57 Berlin', 'billing')  
    INSERT INTO Addresses values  
               (1, 'Avda. de la Constituci??n 2222 M??xico D.F.', 'shipping')  
    INSERT INTO Addresses values  
               (2, '120 Hanover Sq., London', 'billing')  
    INSERT INTO Addresses values  
               (2, 'Forsterstr. 57, Mannheim', 'shipping')  
    ```  
  
3.  <span data-ttu-id="67f09-131">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="67f09-131">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="67f09-132">将文件另存为 LimitFieldValue.xml。</span><span class="sxs-lookup"><span data-stu-id="67f09-132">Save the file as LimitFieldValue.xml.</span></span>  
  
4.  <span data-ttu-id="67f09-133">创建以下模板 (LimitFieldValueT.xml)，然后将其保存到上一步中用于保存该架构 (LimitFieldValue.xml) 的相同目录中：</span><span class="sxs-lookup"><span data-stu-id="67f09-133">Create the following template (LimitFieldValueT.xml), and save it in the same where you saved the schema (LimitFieldValue.xml) in the previous step:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="LimitFieldValue.xml">  
            /Customer  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="67f09-134">为映射架构 (LimitFieldValue.xml) 指定的目录路径是相对于保存模板的目录而言的。</span><span class="sxs-lookup"><span data-stu-id="67f09-134">The directory path specified for the mapping schema (LimitFieldValue.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="67f09-135">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="67f09-135">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\LimitFieldValue.xml"  
    ```  
  
5.  <span data-ttu-id="67f09-136">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="67f09-136">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="67f09-137">有关详细信息，请参阅[使用 ADO 执行 SQLXML 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="67f09-137">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="67f09-138">结果如下：</span><span class="sxs-lookup"><span data-stu-id="67f09-138">This is the result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Customer CustomerID="1" CompanyName="Company A">   
     <BillTo>Obere Str. 57 Berlin</BillTo>   
     <ShipTo>Avda. de la Constituci??n 2222 M??xico D.F.</ShipTo>   
  </Customer>   
  <Customer CustomerID="2" CompanyName="Company B">   
     <BillTo>120 Hanover Sq., London</BillTo>   
     <ShipTo>Forsterstr. 57, Mannheim</ShipTo>   
   </Customer>   
</ROOT>  
```  
  
### <a name="b-limiting-results-based-on-a-discount-value-of-type-real-data"></a><span data-ttu-id="67f09-139">B.</span><span class="sxs-lookup"><span data-stu-id="67f09-139">B.</span></span> <span data-ttu-id="67f09-140">基于 real 数据类型的折扣值限制结果</span><span class="sxs-lookup"><span data-stu-id="67f09-140">Limiting results based on a discount value of type real data</span></span>  
 <span data-ttu-id="67f09-141">在此示例中，数据库包含两个表：</span><span class="sxs-lookup"><span data-stu-id="67f09-141">In this example, a database contains two tables:</span></span>  
  
-   <span data-ttu-id="67f09-142">Orders (OrderID)</span><span class="sxs-lookup"><span data-stu-id="67f09-142">Orders (OrderID)</span></span>  
  
-   <span data-ttu-id="67f09-143">OrderDetails (OrderID, ProductID, UnitPrice, Quantity, Price, Discount)</span><span class="sxs-lookup"><span data-stu-id="67f09-143">OrderDetails (OrderID, ProductID, UnitPrice, Quantity, Price, Discount)</span></span>  
  
 <span data-ttu-id="67f09-144">这是订单详细信息中的 "订单**id** " 属性映射到订单关系中的 "订单 id" 列的映射架构。</span><span class="sxs-lookup"><span data-stu-id="67f09-144">This is the mapping schema in which the **OrderID** attribute on the order details maps to the OrderID column in the orders relation.</span></span> <span data-ttu-id="67f09-145">此属性返回的值仅限于具有 2.0000000 e-001 (0.2) 的值的值，这些值是使用和批注为**折扣**属性指定的 `sql:limit-field` `sql:limit-value` 。</span><span class="sxs-lookup"><span data-stu-id="67f09-145">The values that are returned for this attribute are limited to only those that have a value of 2.0000000e-001 (0.2) as specified for the **Discount** attribute using the `sql:limit-field` and `sql:limit-value` annotations.</span></span>  
  
 <span data-ttu-id="67f09-146">以下是架构：</span><span class="sxs-lookup"><span data-stu-id="67f09-146">This is the schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
   <xsd:appinfo>  
    <sql:relationship name="OrderOrderDetails"  
        parent="Orders"  
        parent-key="OrderID"  
        child="OrderDetails"  
        child-key="OrderID" />  
   </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="root" sql:is-constant="1">  
   <xsd:complexType>  
     <xsd:sequence>  
       <xsd:element name="Order" sql:relation="Orders" >  
          <xsd:complexType>  
             <xsd:sequence>  
                <xsd:element name="orderDetail"   
                       sql:relation="OrderDetails"   
                       sql:limit-field="Discount"                       sql:limit-value="2.0000000e-001"  
                       sql:relationship="OrderOrderDetails">  
                   <xsd:complexType>  
                     <xsd:attribute name="OrderID"   />   
                     <xsd:attribute name="ProductID" />   
                     <xsd:attribute name="Discount"  />   
                     <xsd:attribute name="Quantity"  />   
                     <xsd:attribute name="UnitPrice" />   
                   </xsd:complexType>  
                </xsd:element>  
            </xsd:sequence>  
           <xsd:attribute name="OrderID"/>   
          </xsd:complexType>  
       </xsd:element>  
     </xsd:sequence>  
   </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="67f09-147">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="67f09-147">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="67f09-148">在**tempdb**数据库中创建两个表：</span><span class="sxs-lookup"><span data-stu-id="67f09-148">Create two tables in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Orders ([OrderID] int NOT NULL ) ON [PRIMARY]  
    ALTER TABLE Orders WITH NOCHECK ADD   
    CONSTRAINT [PK_Orders] PRIMARY KEY  CLUSTERED (  
       [OrderID]  
     )  ON [PRIMARY]   
    CREATE TABLE [OrderDetails] (  
       [OrderID] int NOT NULL ,  
       [ProductID] int NOT NULL ,  
       [UnitPrice] money NULL ,  
       [Quantity] smallint NOT NULL ,  
       [Discount] real NOT NULL   
    ) ON [PRIMARY]  
    ```  
  
2.  <span data-ttu-id="67f09-149">添加示例数据：</span><span class="sxs-lookup"><span data-stu-id="67f09-149">Add the sample data:</span></span>  
  
    ```  
    INSERT INTO Orders ([OrderID]) values (10248)  
    INSERT INTO Orders ([OrderID]) values (10250)  
    INSERT INTO Orders ([OrderID]) values (10251)  
    INSERT INTO Orders ([OrderID]) values (10257)  
    INSERT INTO Orders ([OrderID]) values (10258)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10248,11,14,12,0)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10250,51,42.4,35,0.15)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10251,22,16.8,6,0.05)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10257,77,10.4,15,0)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10258,2,15.2,50,0.2)  
    ```  
  
3.  <span data-ttu-id="67f09-150">在目录中保存架构 (LimitFieldValue.xml)。</span><span class="sxs-lookup"><span data-stu-id="67f09-150">Save the schema (LimitFieldValue.xml) in a directory.</span></span>  
  
4.  <span data-ttu-id="67f09-151">创建以下测试脚本 (TestQuery.vbs)，将 MyServer 修改为您的 SQL Server 计算机的名称并将其保存在上一步中用于保存架构的同一目录中：</span><span class="sxs-lookup"><span data-stu-id="67f09-151">Create the following test script (TestQuery.vbs), modify MyServer to the name of your SQL Server computer and save it in the same directory as you used in the previous step to save the schema:</span></span>  
  
    ```  
    Set conn = CreateObject("ADODB.Connection")  
    conn.Open "Provider=SQLOLEDB;Data Source=MyServer;Database=tempdb;Integrated Security=SSPI"  
    conn.Properties("SQLXML Version") = "sqlxml.4.0"   
    Set cmd = CreateObject("ADODB.Command")  
    Set stm = CreateObject("ADODB.Stream")  
    Set cmd.ActiveConnection = conn  
    stm.open  
    result ="none"  
    strXPathQuery="/root"  
    DBGUID_XPATH = "{EC2A4293-E898-11D2-B1B7-00C04F680C56}"  
    cmd.Dialect = DBGUID_XPATH  
    cmd.CommandText = strXPathQuery  
    cmd.Properties("Mapping schema") = "LimitFieldReal.xml"  
    cmd.Properties("Output Stream").Value = stm  
    cmd.Properties("Output Encoding") = "utf-8"  
    WScript.Echo "executing for xml query"  
    On Error Resume Next  
    cmd.Execute , ,1024  
    if err then  
    Wscript.Echo err.description  
    Wscript.Echo err.Number  
    Wscript.Echo err.source  
    On Error GoTo 0  
    else  
    stm.Position = 0  
    result  = stm.ReadText  
    end if  
    WScript.Echo result  
    Wscript.Echo "done"  
    ```  
  
5.  <span data-ttu-id="67f09-152">通过在 Windows 资源管理器中单击 TestQuery.vbs 文件来执行它。</span><span class="sxs-lookup"><span data-stu-id="67f09-152">Execute the TestQuery.vbs file by clicking on it in Windows Explorer.</span></span>  
  
     <span data-ttu-id="67f09-153">结果如下：</span><span class="sxs-lookup"><span data-stu-id="67f09-153">This is the result:</span></span>  
  
    ```  
    <root>  
      <Order OrderID="10248"/>  
      <Order OrderID="10250"/>  
      <Order OrderID="10251"/>  
      <Order OrderID="10257"/>  
      <Order OrderID="10258">  
        <orderDetail OrderID="10258"   
                     ProductID="2"   
                     Discount="0.2"   
                     Quantity="50"/>  
      </Order>  
    </root>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="67f09-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67f09-154">See Also</span></span>  
 <span data-ttu-id="67f09-155">[float 和 real &#40;Transact-sql&#41;](/sql/t-sql/data-types/float-and-real-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="67f09-155">[float and real &#40;Transact-SQL&#41;](/sql/t-sql/data-types/float-and-real-transact-sql) </span></span>  
 <span data-ttu-id="67f09-156">[nchar 和 nvarchar &#40;Transact-sql&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="67f09-156">[nchar and nvarchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql) </span></span>  
 <span data-ttu-id="67f09-157">[安装 SQL Server Native Client](../../relational-databases/native-client/applications/installing-sql-server-native-client.md) </span><span class="sxs-lookup"><span data-stu-id="67f09-157">[Installing SQL Server Native Client](../../relational-databases/native-client/applications/installing-sql-server-native-client.md) </span></span>  
 [<span data-ttu-id="67f09-158">在查询中使用带批注的 XSD 架构 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="67f09-158">Using Annotated XSD Schemas in Queries &#40;SQLXML 4.0&#41;</span></span>](../../relational-databases/sqlxml/annotated-xsd-schemas/using-annotated-xsd-schemas-in-queries-sqlxml-4-0.md)  
  
  
