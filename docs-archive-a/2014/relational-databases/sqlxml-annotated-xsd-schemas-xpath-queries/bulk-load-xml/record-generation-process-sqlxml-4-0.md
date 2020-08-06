---
title: " (SQLXML 4.0) 的记录生成过程 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XML Bulk Load [SQLXML], record generation process
- node scopes [SQLXML]
- record subsets [SQLXML]
- scope [SQLXML]
- key ordering rules [SQLXML]
- record generation process for bulk loads [SQLXML]
- entering node scope [SQLXML]
- bulk load [SQLXML], record generation process
- leaving node scope [SQLXML]
- schema mapping [SQLXML]
ms.assetid: d8885bbe-6f15-4fb9-9684-ca7883cfe9ac
author: rothja
ms.author: jroth
ms.openlocfilehash: 5734776864aecbda7adaf0b9b16180b5ebd55ce3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682779"
---
# <a name="record-generation-process-sqlxml-40"></a><span data-ttu-id="d5ee2-102">记录生成过程 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="d5ee2-102">Record Generation Process (SQLXML 4.0)</span></span>
  <span data-ttu-id="d5ee2-103">XML 大容量加载处理 XML 输入数据并为 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的相应表准备记录。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-103">XML Bulk Load processes the XML input data and prepares records for the appropriate tables in Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d5ee2-104">XML 大容量加载中的逻辑确定何时生成新记录、要将哪些子元素或属性值复制到记录的字段以及何时完成记录并可以发送到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以便插入。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-104">The logic in XML Bulk Load determines when to generate a new record, what child element or attribute values to copy into the fields of the record, and when the record is complete and ready to be sent to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for insertion.</span></span>  
  
 <span data-ttu-id="d5ee2-105">XML 大容量加载不将整个 XML 输入数据加载到内存中，在将数据发送到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 之前不生成完整的记录集。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-105">XML Bulk Load does not load the entire XML input data into memory, and does not produce complete record sets before sending data to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d5ee2-106">这是因为 XML 输入数据可能是大文档，将整个文档加载到内存代价过大。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-106">This is because XML input data can be a large document and loading the entire document in memory can be expensive.</span></span> <span data-ttu-id="d5ee2-107">XML 大容量加载改为执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="d5ee2-107">Instead, XML Bulk Load does the following:</span></span>  
  
1.  <span data-ttu-id="d5ee2-108">分析映射架构并准备必要的执行计划。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-108">Analyzes the mapping schema and prepares the necessary execution plan.</span></span>  
  
2.  <span data-ttu-id="d5ee2-109">将执行计划应用到输入流中的数据。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-109">Applies the execution plan to the data in the input stream.</span></span>  
  
 <span data-ttu-id="d5ee2-110">这种顺序处理使得按特定方式提供 XML 输入数据很重要。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-110">This sequential processing makes it important to provide the XML input data in a specific way.</span></span> <span data-ttu-id="d5ee2-111">您必须了解 XML 大容量加载是如何分析映射架构以及是如何生成记录的，</span><span class="sxs-lookup"><span data-stu-id="d5ee2-111">You must understand how XML Bulk Load analyzes the mapping schema and how the record generation process occurs.</span></span> <span data-ttu-id="d5ee2-112">这样才能为 XML 大容量加载提供映射架构以生成您所要的结果。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-112">With this understanding, you can provide a mapping schema to XML Bulk Load that produces the results you want.</span></span>  
  
 <span data-ttu-id="d5ee2-113">XML 大容量加载处理常见映射架构批注，包括列和表映射（通过使用批注显式指定或通过默认映射隐式指定）以及联接关系。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-113">XML Bulk Load handles common mapping schema annotations, including column and table mappings (specified explicitly by using annotations or implicitly through the default mapping), and join relationships.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d5ee2-114">此处假定您熟悉带批注的 XSD 或 XDR 映射架构。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-114">It is assumed that you are familiar with annotated XSD or XDR mapping schemas.</span></span> <span data-ttu-id="d5ee2-115">有关架构的详细信息，请参阅 &#40;SQLXML 4.0&#41;或带批注的 XDR 架构的[批注的 XSD 架构简介](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md) [&#40;sqlxml 4.0&#41;中弃用](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-115">For more information about schemas, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md) or [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="d5ee2-116">了解记录生成需要了解以下概念：</span><span class="sxs-lookup"><span data-stu-id="d5ee2-116">Understanding record generation requires understanding the following concepts:</span></span>  
  
-   <span data-ttu-id="d5ee2-117">节点作用域</span><span class="sxs-lookup"><span data-stu-id="d5ee2-117">Scope of a node</span></span>  
  
-   <span data-ttu-id="d5ee2-118">记录生成规则</span><span class="sxs-lookup"><span data-stu-id="d5ee2-118">Record Generation Rule</span></span>  
  
-   <span data-ttu-id="d5ee2-119">记录子集和键排序规则</span><span class="sxs-lookup"><span data-stu-id="d5ee2-119">Record subset and the Key Ordering Rule</span></span>  
  
-   <span data-ttu-id="d5ee2-120">记录生成规则的例外情况</span><span class="sxs-lookup"><span data-stu-id="d5ee2-120">Exceptions to the Record Generation Rule</span></span>  
  
## <a name="scope-of-a-node"></a><span data-ttu-id="d5ee2-121">节点的作用域</span><span class="sxs-lookup"><span data-stu-id="d5ee2-121">Scope of a Node</span></span>  
 <span data-ttu-id="d5ee2-122">当 xml 大容量加载在 XML 输入数据流中遇到时，XML 文档中的元素或属性)  (的节点将进入*范围*。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-122">A node (an element or an attribute) in an XML document enters *into scope* when XML Bulk Load encounters it in the XML input data stream.</span></span> <span data-ttu-id="d5ee2-123">对于元素节点，元素的开始标记使该元素进入作用域。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-123">For an element node, the start tag of the element brings the element in scope.</span></span> <span data-ttu-id="d5ee2-124">对于属性节点，属性名称使该属性进入作用域。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-124">For an attribute node, the attribute name brings the attribute in scope.</span></span>  
  
 <span data-ttu-id="d5ee2-125">当在结束标记（对于元素节点）或属性值结尾（对于属性节点）没有更多数据用于节点时，则表示节点离开作用域。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-125">A node leaves scope when there is no more data for it: either at the end tag (in the case of an element node) or at the end of an attribute value (in the case of an attribute node).</span></span>  
  
## <a name="record-generation-rule"></a><span data-ttu-id="d5ee2-126">记录生成规则</span><span class="sxs-lookup"><span data-stu-id="d5ee2-126">Record Generation Rule</span></span>  
 <span data-ttu-id="d5ee2-127">节点（元素或属性）进入作用域时，可能从该节点生成记录。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-127">When a node (element or attribute) enters into scope, there is a potential for generating a record from that node.</span></span> <span data-ttu-id="d5ee2-128">只要相关的节点在作用域中，该记录就存在。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-128">The record lives as long as the associated node is in scope.</span></span> <span data-ttu-id="d5ee2-129">当节点离开作用域时，XML 大容量加载认为生成的记录已完成（带数据）并将它发送到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以便进行插入。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-129">When the node goes out of scope, XML Bulk Load considers the generated record complete (with data) and sends it to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for insertion.</span></span>  
  
 <span data-ttu-id="d5ee2-130">例如，考虑下面的 XSD 架构片段：</span><span class="sxs-lookup"><span data-stu-id="d5ee2-130">For example, consider the following XSD schema fragment:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Customer" sql:relation="Customers" >  
   <xsd:complexType>  
     <xsd:attribute name="CustomerID" type="xsd:string" />  
     <xsd:attribute name="CompanyName" type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="d5ee2-131">架构指定 **\<Customer>** 具有**CustomerID**和**名称**属性的元素。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-131">The schema specifies a **\<Customer>** element with **CustomerID** and **CompanyName** attributes.</span></span> <span data-ttu-id="d5ee2-132">`sql:relation`批注将元素映射 **\<Customer>** 到 Customers 表。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-132">The `sql:relation` annotation maps the **\<Customer>** element to the Customers table.</span></span>  
  
 <span data-ttu-id="d5ee2-133">考虑 XML 文档的以下片段：</span><span class="sxs-lookup"><span data-stu-id="d5ee2-133">Consider this fragment of an XML document:</span></span>  
  
```  
<Customer CustomerID="1" CompanyName="xyz" />  
<Customer CustomerID="2" CompanyName="abc" />  
...  
```  
  
 <span data-ttu-id="d5ee2-134">将前文中所述的架构提供给 XML 大容量加载并使用 XML 数据作为输入，XML 大容量加载按以下方式处理源数据中的节点（元素和属性）：</span><span class="sxs-lookup"><span data-stu-id="d5ee2-134">When XML Bulk Load is provided with the schema described in the preceding paragraphs and XML data as input, it processes the nodes (elements and attributes) in the source data as follows:</span></span>  
  
-   <span data-ttu-id="d5ee2-135">第一个元素的开始标记使 **\<Customer>** 该元素在范围内。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-135">The start tag of the first **\<Customer>** element brings that element in scope.</span></span> <span data-ttu-id="d5ee2-136">将此节点映射到 Customers 表。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-136">This node maps to the Customers table.</span></span> <span data-ttu-id="d5ee2-137">因此，XML 大容量加载为 Customers 表生成一个记录。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-137">Therefore, XML Bulk Load generates a record for the Customers table.</span></span>  
  
-   <span data-ttu-id="d5ee2-138">在架构中，元素的所有属性都 **\<Customer>** 映射到 Customers 表的列。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-138">In the schema, all attributes of the **\<Customer>** element map to columns of the Customers table.</span></span> <span data-ttu-id="d5ee2-139">这些属性进入作用域时，XML 大容量加载将它们的值复制到父作用域已生成的客户记录。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-139">As these attributes enter into scope, XML Bulk Load copies their values to the customer record that is already generated by the parent scope.</span></span>  
  
-   <span data-ttu-id="d5ee2-140">当 XML 大容量加载到达元素的结束标记时 **\<Customer>** ，元素会超出范围。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-140">When XML Bulk Load reaches the end tag for the **\<Customer>** element, the element goes out of scope.</span></span> <span data-ttu-id="d5ee2-141">这将导致 XML 大容量加载认为该记录已完成并将其发送到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-141">This causes XML Bulk Load to consider the record complete and send it to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d5ee2-142">对于每个后续元素，XML 大容量加载遵循此过程 **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-142">XML Bulk Load follows this process for each subsequent **\<Customer>** element.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d5ee2-143">在此模型中，由于是在到达结束标记（或节点离开作用域）时插入记录，因此必须定义节点作用域内与该记录相关的所有数据。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-143">In this model, because a record is inserted when the end tag is reached (or the node is out of scope), you must define all of the data that is associated with the record within the scope of the node.</span></span>  
  
## <a name="record-subset-and-the-key-ordering-rule"></a><span data-ttu-id="d5ee2-144">记录子集和键排序规则</span><span class="sxs-lookup"><span data-stu-id="d5ee2-144">Record Subset and the Key Ordering Rule</span></span>  
 <span data-ttu-id="d5ee2-145">指定使用 `<sql:relationship>` 的映射架构时，“子集”一词指针对关系的外键关系生成的记录集。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-145">When you specify a mapping schema that uses `<sql:relationship>`, the subset term refers to the set of records that is generated on the foreign side of the relationship.</span></span> <span data-ttu-id="d5ee2-146">在下面的示例中，CustOrder 记录是针对外键关系 `<sql:relationship>` 生成的。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-146">In the following example, the CustOrder records are on the foreign side, `<sql:relationship>`.</span></span>  
  
 <span data-ttu-id="d5ee2-147">例如，假定一个数据库包含以下各表：</span><span class="sxs-lookup"><span data-stu-id="d5ee2-147">For example, suppose a database contains the following tables:</span></span>  
  
-   <span data-ttu-id="d5ee2-148">Cust (CustomerID, CompanyName, City)</span><span class="sxs-lookup"><span data-stu-id="d5ee2-148">Cust (CustomerID, CompanyName, City)</span></span>  
  
-   <span data-ttu-id="d5ee2-149">CustOrder (CustomerID, OrderID)</span><span class="sxs-lookup"><span data-stu-id="d5ee2-149">CustOrder (CustomerID, OrderID)</span></span>  
  
 <span data-ttu-id="d5ee2-150">CustOrder 表中的 CustomerID 是外键，它引用 Cust 表中的 CustomerID 主键。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-150">The CustomerID in the CustOrder table is a foreign key that refers to the CustomerID primary key in the Cust table.</span></span>  
  
 <span data-ttu-id="d5ee2-151">现在，请考虑在以下带批注的 XSD 架构中指定的 XML 视图。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-151">Now, consider the XML view as specified in the following annotated XSD schema.</span></span> <span data-ttu-id="d5ee2-152">此架构使用 `<sql:relationship>` 指定 Cust 表和 CustOrder 表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-152">This schema uses `<sql:relationship>` to specify the relationship between the Cust and CustOrder tables.</span></span>  
  
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
</xsd:schema>  
```  
  
 <span data-ttu-id="d5ee2-153">下面给出了示例 XML 数据和创建工作示例的步骤。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-153">The sample XML data and the steps to create a working sample are given below.</span></span>  
  
-   <span data-ttu-id="d5ee2-154">当 **\<Customer>** xml 数据文件中的元素节点进入作用域时，Xml 大容量加载将为 "已加入" 表生成一条记录。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-154">When a **\<Customer>** element node in the XML data file enters into scope, XML Bulk Load generates a record for the Cust table.</span></span> <span data-ttu-id="d5ee2-155">然后，XML 大容量加载从、和子元素中复制所需的列值 (CustomerID、公司名称和 City) **\<CustomerID>** ， **\<CompanyName>** **\<City>** 因为这些元素进入范围。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-155">XML Bulk Load then copies the necessary column values (CustomerID, CompanyName, and City) from the **\<CustomerID>**, **\<CompanyName>**, and the **\<City>** child elements as these elements enter into scope.</span></span>  
  
-   <span data-ttu-id="d5ee2-156">当 **\<Order>** 元素节点进入作用域时，XML 大容量加载为 CustOrder 表生成一条记录。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-156">When an **\<Order>** element node enters into scope, XML Bulk Load generates a record for the CustOrder table.</span></span> <span data-ttu-id="d5ee2-157">XML 大容量加载会将 "**订单 id** " 属性的值复制到此记录。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-157">XML Bulk Load copies the value of the **OrderID** attribute to this record.</span></span> <span data-ttu-id="d5ee2-158">将从元素的子元素中获取 CustomerID 列所需的值 **\<CustomerID>** **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-158">The value required for the CustomerID column is obtained from the **\<CustomerID>** child element of the **\<Customer>** element.</span></span> <span data-ttu-id="d5ee2-159">XML 大容量加载使用在中指定的信息 `<sql:relationship>` 获取此记录的 customerid 外键值，除非在元素中指定了**customerid**属性 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-159">XML Bulk Load uses the information that is specified in `<sql:relationship>` to obtain the CustomerID foreign key value for this record, unless the **CustomerID** attribute was specified in the **\<Order>** element.</span></span> <span data-ttu-id="d5ee2-160">一般规则是：如果子元素显式指定外键属性的值，则 XML 大容量加载使用该值，而不通过使用指定的 `<sql:relationship>` 来获取父元素的值。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-160">The general rule is that if the child element explicitly specifies a value for the foreign key attribute, XML Bulk Load uses that value and does not obtain the value from the parent element by using the specified `<sql:relationship>`.</span></span> <span data-ttu-id="d5ee2-161">由于此 **\<Order>** 元素节点超出范围，XML 大容量加载会将记录发送到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，然后 **\<Order>** 以相同的方式处理所有后续的元素节点。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-161">As this **\<Order>** element node goes out of scope, XML Bulk Load sends the record to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and then processes all the subsequent **\<Order>** element nodes in the same manner.</span></span>  
  
-   <span data-ttu-id="d5ee2-162">最后， **\<Customer>** 元素节点超出范围。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-162">Finally, the **\<Customer>** element node goes out of scope.</span></span> <span data-ttu-id="d5ee2-163">此时，XML 大容量加载将客户记录发送到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-163">At that time, XML Bulk Load sends the customer record to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d5ee2-164">XML 大容量加载为 XML 数据流中的所有后续客户执行此过程。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-164">XML Bulk Load follows this process for all the subsequent customers in the XML data stream.</span></span>  
  
 <span data-ttu-id="d5ee2-165">以下是有关映射架构的两点结论：</span><span class="sxs-lookup"><span data-stu-id="d5ee2-165">Here are two observations about the mapping schema:</span></span>  
  
-   <span data-ttu-id="d5ee2-166">如果架构满足 "包含" 规则 (例如，与客户关联的所有数据和订单在) 的关联 **\<Customer>** 节点和元素节点的范围内定义 **\<Order>** ，则大容量加载将成功。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-166">When the schema satisfies the "containment" rule (for example, all data that is associated with the customer and the order is defined within the scope of the associated **\<Customer>** and **\<Order>** element nodes), the bulk load succeeds.</span></span>  
  
-   <span data-ttu-id="d5ee2-167">在描述 **\<Customer>** 元素的情况下，其子元素按适当的顺序指定。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-167">In describing the **\<Customer>** element, its child elements are specified in the appropriate order.</span></span> <span data-ttu-id="d5ee2-168">在这种情况下， **\<CustomerID>** 子元素将在 **\<Order>** 子元素之前指定。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-168">In this case, the **\<CustomerID>** child element is specified before the **\<Order>** child element.</span></span> <span data-ttu-id="d5ee2-169">这意味着在输入 XML 数据文件中， **\<CustomerID>** 当 **\<Order>** 元素进入作用域时，元素值可用作外键值。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-169">This means that in the input XML data file, the **\<CustomerID>** element value is available as the foreign key value when the **\<Order>** element enters into scope.</span></span> <span data-ttu-id="d5ee2-170">首先指定键属性，此即“键排序规则”。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-170">The key attributes are specified first; this is the "Key Ordering Rule."</span></span>  
  
     <span data-ttu-id="d5ee2-171">如果在 **\<CustomerID>** 子元素之后指定子元素 **\<Order>** ，则当元素进入范围时，值将不可用 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-171">If you specify the **\<CustomerID>** child element after the **\<Order>** child element, the value is not available when the **\<Order>** element enters into scope.</span></span> <span data-ttu-id="d5ee2-172">**\</Order>** 然后读取结束标记后，CustOrder 表的记录将被视为已完成，并且会在 CustOrder 表中插入值为 CustomerID 列的 NULL 值，这不是所需的结果。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-172">When the **\</Order>** end tag is then read, the record for CustOrder table is considered complete and is inserted in the CustOrder table with a NULL value for the CustomerID column, which is not the desired result.</span></span>  
  
#### <a name="to-create-a-working-sample"></a><span data-ttu-id="d5ee2-173">创建工作示例</span><span class="sxs-lookup"><span data-stu-id="d5ee2-173">To create a working sample</span></span>  
  
1.  <span data-ttu-id="d5ee2-174">将在该示例中提供的架构另存为 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-174">Save the schema that is provided in this example as SampleSchema.xml.</span></span>  
  
2.  <span data-ttu-id="d5ee2-175">创建以下表：</span><span class="sxs-lookup"><span data-stu-id="d5ee2-175">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Cust (  
                  CustomerID     int         PRIMARY KEY,  
                  CompanyName    varchar(20) NOT NULL,  
                  City           varchar(20) DEFAULT 'Seattle')  
    GO  
    CREATE TABLE CustOrder (  
                 OrderID        int         PRIMARY KEY,  
                 CustomerID     int         FOREIGN KEY REFERENCES                                          Cust(CustomerID))  
    GO  
    ```  
  
3.  <span data-ttu-id="d5ee2-176">将以下示例 XML 输入数据另存为 SampleXMLData.xml：</span><span class="sxs-lookup"><span data-stu-id="d5ee2-176">Save the following sample XML input data as SampleXMLData.xml:</span></span>  
  
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
  
4.  <span data-ttu-id="d5ee2-177">若要执行 XML 大容量加载，请保存并执行以下 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) 示例 (BulkLoad.vbs)：</span><span class="sxs-lookup"><span data-stu-id="d5ee2-177">To execute XML Bulk Load, save and execute the following [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) example (BulkLoad.vbs):</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
## <a name="exceptions-to-the-record-generation-rule"></a><span data-ttu-id="d5ee2-178">记录生成规则的例外情况</span><span class="sxs-lookup"><span data-stu-id="d5ee2-178">Exceptions to the Record Generation Rule</span></span>  
 <span data-ttu-id="d5ee2-179">如果节点属于 IDREF 或 IDREFS 类型，则在它进入作用域时，XML 大容量加载不为该节点生成记录。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-179">XML Bulk Load does not generate a record for a node when it enters into scope if that node is either an IDREF or IDREFS type.</span></span> <span data-ttu-id="d5ee2-180">您必须确保在架构的同一位置存在记录的完整描述。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-180">You must make sure that a complete description of the record occurs at some place in the schema.</span></span> <span data-ttu-id="d5ee2-181">忽略 `dt:type="nmtokens"` 批注，就像忽略 IDREFS 类型一样。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-181">The `dt:type="nmtokens"` annotations are ignored just as the IDREFS type is ignored.</span></span>  
  
 <span data-ttu-id="d5ee2-182">例如，请考虑以下用于描述和元素的 XSD 架构 **\<Customer>** **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-182">For example, consider the following XSD schema that describes **\<Customer>** and **\<Order>** elements.</span></span> <span data-ttu-id="d5ee2-183">**\<Customer>** 元素包含 IDREFS 类型的**OrderList**属性。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-183">The **\<Customer>** element includes an **OrderList** attribute of the IDREFS type.</span></span> <span data-ttu-id="d5ee2-184">`<sql:relationship>` 标记指定客户和订单列表之间的一对多关系。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-184">The `<sql:relationship>` tag specifies the one-to-many relationship between the customer and list of orders.</span></span>  
  
 <span data-ttu-id="d5ee2-185">以下是架构：</span><span class="sxs-lookup"><span data-stu-id="d5ee2-185">This is the schema:</span></span>  
  
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
  
  <xsd:element name="Customers" sql:relation="Cust" >  
   <xsd:complexType>  
    <xsd:attribute name="CustomerID" type="xsd:integer" />  
    <xsd:attribute name="CompanyName" type="xsd:string" />  
    <xsd:attribute name="City" type="xsd:string" />  
    <xsd:attribute name="OrderList"   
                       type="xsd:IDREFS"   
                       sql:relation="CustOrder"   
                       sql:field="OrderID"  
                       sql:relationship="CustCustOrder" >  
    </xsd:attribute>  
  </xsd:complexType>  
 </xsd:element>  
  
  <xsd:element name="Order" sql:relation="CustOrder" >  
   <xsd:complexType>  
    <xsd:attribute name="OrderID" type="xsd:string" />  
    <xsd:attribute name="CustomerID" type="xsd:integer" />  
    <xsd:attribute name="OrderDate" type="xsd:date" />  
  </xsd:complexType>  
 </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="d5ee2-186">由于大容量加载将忽略 IDREFS 类型的节点，因此当**OrderList**属性节点进入作用域时，不会生成任何记录。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-186">Because Bulk Load ignores the nodes of IDREFS type, there is no record generation when the **OrderList** attribute node enters into scope.</span></span> <span data-ttu-id="d5ee2-187">如果要将订单记录添加到 Orders 表，必须在架构中的某个地方描述这些订单。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-187">Therefore, if you want the order records added to the Orders table, you must describe those orders somewhere in the schema.</span></span> <span data-ttu-id="d5ee2-188">在此架构中，指定 **\<Order>** 元素可确保 XML 大容量加载将订单记录添加到 Orders 表中。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-188">In this schema, specifying the **\<Order>** element ensures that XML Bulk Load adds the order records to the Orders table.</span></span> <span data-ttu-id="d5ee2-189">**\<Order>** 元素描述填充 CustOrder 表的记录所需的所有属性。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-189">The **\<Order>** element describes all the attributes that are required to fill the record for the CustOrder table.</span></span>  
  
 <span data-ttu-id="d5ee2-190">必须确保元素中的**CustomerID**和**订单 id**值 **\<Customer>** 与元素中的值匹配 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-190">You must ensure that the **CustomerID** and **OrderID** values in the **\<Customer>** element match the values in the **\<Order>** element.</span></span> <span data-ttu-id="d5ee2-191">由您负责维护引用完整性。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-191">You are responsible for maintaining referential integrity.</span></span>  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="d5ee2-192">测试工作示例</span><span class="sxs-lookup"><span data-stu-id="d5ee2-192">To test a working sample</span></span>  
  
1.  <span data-ttu-id="d5ee2-193">创建以下表：</span><span class="sxs-lookup"><span data-stu-id="d5ee2-193">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Cust (  
                  CustomerID     int          PRIMARY KEY,  
                  CompanyName    varchar(20)  NOT NULL,  
                  City           varchar(20)  DEFAULT 'Seattle')  
    GO  
    CREATE TABLE CustOrder (  
                  OrderID        varchar(10) PRIMARY KEY,  
                  CustomerID     int         FOREIGN KEY REFERENCES                                          Cust(CustomerID),  
                  OrderDate      datetime DEFAULT '2000-01-01')  
    GO  
    ```  
  
2.  <span data-ttu-id="d5ee2-194">将在该示例中提供的映射架构另存为 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="d5ee2-194">Save the mapping schema provided in this example as SampleSchema.xml.</span></span>  
  
3.  <span data-ttu-id="d5ee2-195">将以下示例 XML 数据另存为 SampleXMLData.xml：</span><span class="sxs-lookup"><span data-stu-id="d5ee2-195">Save the following sample XML data as SampleXMLData.xml:</span></span>  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1111" CompanyName="Sean Chai" City="NY"  
                 OrderList="Ord1 Ord2" />  
      <Customers CustomerID="1112" CompanyName="Dont Know" City="LA"  
                 OrderList="Ord3 Ord4" />  
      <Order OrderID="Ord1" CustomerID="1111" OrderDate="1999-01-01" />  
      <Order OrderID="Ord2" CustomerID="1111" OrderDate="1999-02-01" />  
      <Order OrderID="Ord3" CustomerID="1112" OrderDate="1999-03-01" />  
      <Order OrderID="Ord4" CustomerID="1112" OrderDate="1999-04-01" />  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="d5ee2-196">若要执行 XML 大容量加载，请保存并执行此 VBScript 示例 (SampleVB.vbs)：</span><span class="sxs-lookup"><span data-stu-id="d5ee2-196">To execute XML Bulk Load, save and execute this VBScript example (SampleVB.vbs):</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
  
