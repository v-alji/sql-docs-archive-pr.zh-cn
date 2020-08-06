---
title: 使用 sql：键字段 (SQLXML 4.0) 来标识键列 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- nesting XML results
- proper nesting in results [SQLXML]
- sql:key-fields
- XSD schemas [SQLXML], key columns
- identifying key columns [SQLXML]
- annotated XSD schemas, key columns
- key columns [SQLXML]
- relationships [SQLXML], key columns
- hierarchical relationships [SQLXML]
- key-fields annotation
ms.assetid: 1a5ad868-8602-45c4-913d-6fbb837eebb0
author: rothja
ms.author: jroth
ms.openlocfilehash: 0ab12b34874a54bad2e08a96d08ebd0cc994f946
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693670"
---
# <a name="identifying-key-columns-using-sqlkey-fields-sqlxml-40"></a><span data-ttu-id="0d310-102">使用 sql:key-fields 标识键列 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="0d310-102">Identifying Key Columns Using sql:key-fields (SQLXML 4.0)</span></span>
  <span data-ttu-id="0d310-103">针对 XSD 架构指定 XPath 查询时，大多数情况下必须有键信息才能获得结果中的正确嵌套。</span><span class="sxs-lookup"><span data-stu-id="0d310-103">When an XPath query is specified against an XSD schema, key information is required in most cases to obtain proper nesting in the result.</span></span> <span data-ttu-id="0d310-104">指定 `sql:key-fields` 批注是一种确保生成正确层次结构的方式。</span><span class="sxs-lookup"><span data-stu-id="0d310-104">Specifying the `sql:key-fields` annotation is a way of ensuring that the appropriate hierarchy is generated.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d310-105">若要确保正确的嵌套，建议您为映射到表的元素指定 `sql:key-fields`。</span><span class="sxs-lookup"><span data-stu-id="0d310-105">To ensure proper nesting, it is recommended that you specify `sql:key-fields` for elements that map to tables.</span></span> <span data-ttu-id="0d310-106">所生成的 XML 对于基础结果集的排序敏感。</span><span class="sxs-lookup"><span data-stu-id="0d310-106">The XML produced is sensitive to the ordering of the underlying result set.</span></span> <span data-ttu-id="0d310-107">如果不指定 `sql:key-fields`，则所生成的 XML 的格式可能不正确。</span><span class="sxs-lookup"><span data-stu-id="0d310-107">If `sql:key-fields` is not specified, the XML generated might not be formed properly.</span></span>  
  
 <span data-ttu-id="0d310-108">`sql:key-fields` 的值用于标识唯一标识关系中的行的列。</span><span class="sxs-lookup"><span data-stu-id="0d310-108">The value of `sql:key-fields` identifies the column(s) that uniquely identify the rows in the relation.</span></span> <span data-ttu-id="0d310-109">如果需要多个列才能唯一标识某行，则用空格分隔列值。</span><span class="sxs-lookup"><span data-stu-id="0d310-109">If more than one column is required to uniquely identify a row, the column values are delimited by spaces.</span></span>  
  
 <span data-ttu-id="0d310-110">`sql:key-fields`当元素包含在 **\<sql:relationship>** 元素和子元素之间定义的，但未提供父元素中指定的表的主键时，必须使用批注。</span><span class="sxs-lookup"><span data-stu-id="0d310-110">You must use the `sql:key-fields` annotation when an element contains a **\<sql:relationship>** that is defined between the element and a child element but does not provide the primary key of the table that is specified in the parent element.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0d310-111">示例</span><span class="sxs-lookup"><span data-stu-id="0d310-111">Examples</span></span>  
 <span data-ttu-id="0d310-112">若要创建使用以下示例的工作示例，必须满足某些要求。</span><span class="sxs-lookup"><span data-stu-id="0d310-112">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="0d310-113">有关详细信息，请参阅[运行 SQLXML 示例的要求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="0d310-113">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-producing-the-appropriate-nesting-when-sqlrelationship-does-not-provide-sufficient-information"></a><span data-ttu-id="0d310-114">A.</span><span class="sxs-lookup"><span data-stu-id="0d310-114">A.</span></span> <span data-ttu-id="0d310-115">当 \<sql:relationship> 未提供足够的信息时生成适当的嵌套</span><span class="sxs-lookup"><span data-stu-id="0d310-115">Producing the appropriate nesting when \<sql:relationship> does not provide sufficient information</span></span>  
 <span data-ttu-id="0d310-116">该示例显示必须指定 `sql:key-fields` 的地方。</span><span class="sxs-lookup"><span data-stu-id="0d310-116">This example shows where `sql:key-fields` must be specified.</span></span>  
  
 <span data-ttu-id="0d310-117">请考虑以下架构。</span><span class="sxs-lookup"><span data-stu-id="0d310-117">Consider the following schema.</span></span> <span data-ttu-id="0d310-118">该架构指定了和元素之间的层次结构， **\<Order>** **\<Customer>** 其中 **\<Order>** 元素是父级， **\<Customer>** 元素是子元素。</span><span class="sxs-lookup"><span data-stu-id="0d310-118">The schema specifies a hierarchy between the **\<Order>** and **\<Customer>** elements in which the **\<Order>** element is the parent and the **\<Customer>** element is a child.</span></span>  
  
 <span data-ttu-id="0d310-119">**\<sql:relationship>** 标记用于指定父子关系。</span><span class="sxs-lookup"><span data-stu-id="0d310-119">The **\<sql:relationship>** tag is used to specify the parent-child relationship.</span></span> <span data-ttu-id="0d310-120">它将 Sales.SalesOrderHeader 表中的 CustomerID 标识为父键，该父键引用 Sales.Customer 表中的 CustomerID 子键。</span><span class="sxs-lookup"><span data-stu-id="0d310-120">It identifies CustomerID in the Sales.SalesOrderHeader table as the parent key that refers to the CustomerID child key in the Sales.Customer table.</span></span> <span data-ttu-id="0d310-121">中提供的信息不足 **\<sql:relationship>** 以唯一标识父表中的行， (SalesOrderHeader) 。</span><span class="sxs-lookup"><span data-stu-id="0d310-121">The information provided in **\<sql:relationship>** is not sufficient to uniquely identify rows in the parent table (Sales.SalesOrderHeader).</span></span> <span data-ttu-id="0d310-122">因此，如果没有 `sql:key-fields` 批注，则生成的层次结构不准确。</span><span class="sxs-lookup"><span data-stu-id="0d310-122">Therefore, without the `sql:key-fields` annotation, the hierarchy that is generated is inaccurate.</span></span>  
  
 <span data-ttu-id="0d310-123">对于 `sql:key-fields` 在上指定的 **\<Order>** ，批注唯一标识父 (SalesOrderHeader 表) 中的行，其子元素显示在其父元素之下。</span><span class="sxs-lookup"><span data-stu-id="0d310-123">With `sql:key-fields` specified on **\<Order>**, the annotation uniquely identifies the rows in the parent (Sales.SalesOrderHeader table), and its child elements appear below its parent.</span></span>  
  
 <span data-ttu-id="0d310-124">以下是架构：</span><span class="sxs-lookup"><span data-stu-id="0d310-124">This is the schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="OrdCust"  
        parent="Sales.SalesOrderHeader"  
        parent-key="CustomerID"  
        child="Sales.Customer"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"   
               sql:key-fields="SalesOrderID">  
   <xsd:complexType>  
     <xsd:sequence>  
     <xsd:element name="Customer" sql:relation="Sales.Customer"   
                       sql:relationship="OrdCust"  >  
       <xsd:complexType>  
         <xsd:attribute name="CustID" sql:field="CustomerID" />  
         <xsd:attribute name="SoldBy" sql:field="SalesPersonID" />  
       </xsd:complexType>  
     </xsd:element>  
     </xsd:sequence>  
     <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
     <xsd:attribute name= "CustomerID" type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a><span data-ttu-id="0d310-125">创建此架构的工作示例</span><span class="sxs-lookup"><span data-stu-id="0d310-125">To create a working sample of this schema</span></span>  
  
1.  <span data-ttu-id="0d310-126">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="0d310-126">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="0d310-127">将文件另存为 KeyFields1.xml。</span><span class="sxs-lookup"><span data-stu-id="0d310-127">Save the file as KeyFields1.xml.</span></span>  
  
2.  <span data-ttu-id="0d310-128">复制以下模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="0d310-128">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="0d310-129">在保存 KeyFields1.xml 的相同目录中将该文件另存为 KeyFields1T.xml。</span><span class="sxs-lookup"><span data-stu-id="0d310-129">Save the file as KeyFields1T.xml in the same directory where you saved KeyFields1.xml.</span></span> <span data-ttu-id="0d310-130">模板中的 XPath 查询将返回 **\<Order>** CustomerID 小于3的所有元素。</span><span class="sxs-lookup"><span data-stu-id="0d310-130">The XPath query in the template returns all the **\<Order>** elements with a CustomerID of less than 3.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="KeyFields1.xml">  
            /Order[@CustomerID < 3]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="0d310-131">为映射架构 (KeyFields1.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="0d310-131">The directory path specified for the mapping schema (KeyFields1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="0d310-132">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="0d310-132">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\KeyFields1.xml"  
    ```  
  
3.  <span data-ttu-id="0d310-133">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="0d310-133">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="0d310-134">有关详细信息，请参阅[使用 ADO 执行 SQLXML 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="0d310-134">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="0d310-135">部分结果集如下：</span><span class="sxs-lookup"><span data-stu-id="0d310-135">This is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
    <Order SalesOrderID="43860" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    <Order SalesOrderID="44501" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    <Order SalesOrderID="45283" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    .....  
</ROOT>  
```  
  
### <a name="b-specifying-sqlkey-fields-to-produce-proper-nesting-in-the-result"></a><span data-ttu-id="0d310-136">B.</span><span class="sxs-lookup"><span data-stu-id="0d310-136">B.</span></span> <span data-ttu-id="0d310-137">指定 sql:key-fields 以便在结果中生成正确的嵌套</span><span class="sxs-lookup"><span data-stu-id="0d310-137">Specifying sql:key-fields to produce proper nesting in the result</span></span>  
 <span data-ttu-id="0d310-138">在下面的架构中，没有使用指定的层次结构 **\<sql:relationship>** 。</span><span class="sxs-lookup"><span data-stu-id="0d310-138">In the following schema, there is no hierarchy specified using **\<sql:relationship>**.</span></span> <span data-ttu-id="0d310-139">此架构仍然需要指定 `sql:key-fields` 批注才能唯一标识 HumanResources.Employee 表中的雇员。</span><span class="sxs-lookup"><span data-stu-id="0d310-139">The schema still requires specifying the `sql:key-fields` annotation to uniquely identify employees in the HumanResources.Employee table.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="HumanResources.Employee" sql:key-fields="EmployeeID" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Title">  
          <xsd:complexType>  
            <xsd:simpleContent>  
              <xsd:extension base="xsd:string">  
                 <xsd:attribute name="EmployeeID" type="xsd:integer" />  
              </xsd:extension>  
            </xsd:simpleContent>  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
   </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a><span data-ttu-id="0d310-140">创建此架构的工作示例</span><span class="sxs-lookup"><span data-stu-id="0d310-140">To create a working sample of this schema</span></span>  
  
1.  <span data-ttu-id="0d310-141">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="0d310-141">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="0d310-142">将文件另存为 KeyFields2.xml。</span><span class="sxs-lookup"><span data-stu-id="0d310-142">Save the file as KeyFields2.xml.</span></span>  
  
2.  <span data-ttu-id="0d310-143">复制以下模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="0d310-143">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="0d310-144">在保存 KeyFields2.xml 的相同目录中将该文件另存为 KeyFields2T.xml。</span><span class="sxs-lookup"><span data-stu-id="0d310-144">Save the file as KeyFields2T.xml in the same directory where you saved KeyFields2.xml.</span></span> <span data-ttu-id="0d310-145">模板中的 XPath 查询将返回所有 **\<HumanResources.Employee>** 元素：</span><span class="sxs-lookup"><span data-stu-id="0d310-145">The XPath query in the template returns all the **\<HumanResources.Employee>** elements:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="KeyFields2.xml">  
        /HumanResources.Employee  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="0d310-146">为映射架构 (KeyFields2.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="0d310-146">The directory path specified for the mapping schema (KeyFields2.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="0d310-147">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="0d310-147">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\KeyFields2.xml"  
    ```  
  
3.  <span data-ttu-id="0d310-148">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="0d310-148">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="0d310-149">有关详细信息，请参阅[使用 ADO 执行 SQLXML 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="0d310-149">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="0d310-150">结果如下：</span><span class="sxs-lookup"><span data-stu-id="0d310-150">This is the result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <HumanResources.Employee>  
    <Title EmployeeID="1">Production Technician - WC60</Title>   
  </HumanResources.Employee>  
  <HumanResources.Employee>  
    <Title EmployeeID="2">Marketing Assistant</Title>   
  </HumanResources.Employee>  
  <HumanResources.Employee>  
    <Title EmployeeID="3">Engineering Manager</Title>   
  </HumanResources.Employee>  
  ...  
</ROOT>  
```  
  
  
