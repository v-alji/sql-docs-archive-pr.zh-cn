---
title: 在 (SQLXML 4.0) 的 XPath 查询中指定布尔函数 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], Boolean functions
- false function
- not function [SQLXML]
- true function
- Boolean functions
ms.assetid: c72cd333-9294-4d41-84f2-1748bf20e3eb
author: rothja
ms.author: jroth
ms.openlocfilehash: d230c7cd8792066732085b9ce501c0794687d17d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577481"
---
# <a name="specifying-boolean-functions-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="6194c-102">在 XPath 查询中指定布尔函数 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="6194c-102">Specifying Boolean Functions in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="6194c-103">以下示例说明如何在 XPath 查询中指定布尔函数。</span><span class="sxs-lookup"><span data-stu-id="6194c-103">The following examples show how Boolean functions are specified in XPath queries.</span></span> <span data-ttu-id="6194c-104">这些示例中的 XPath 查询是针对 SampleSchema1.xml 中包含的映射架构指定的。</span><span class="sxs-lookup"><span data-stu-id="6194c-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="6194c-105">有关此示例架构的信息，请参阅[&#40;SQLXML 4.0&#41;的 XPath 批注的 XSD 架构示例](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="6194c-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6194c-106">示例</span><span class="sxs-lookup"><span data-stu-id="6194c-106">Examples</span></span>  
  
## <a name="a-specify-the-not-boolean-function"></a><span data-ttu-id="6194c-107">A.</span><span class="sxs-lookup"><span data-stu-id="6194c-107">A.</span></span> <span data-ttu-id="6194c-108">指定 not() 布尔函数</span><span class="sxs-lookup"><span data-stu-id="6194c-108">Specify the not() Boolean function</span></span>  
 <span data-ttu-id="6194c-109">此查询返回 **\<Customer>** 不具有子元素的上下文节点的所有子元素 **\<Order>** ：</span><span class="sxs-lookup"><span data-stu-id="6194c-109">This query returns all the **\<Customer>** child elements of the context node that do not have **\<Order>** child elements:</span></span>  
  
```  
/child::Customer[not(child::Order)]  
```  
  
 <span data-ttu-id="6194c-110">`child` 轴为默认轴。</span><span class="sxs-lookup"><span data-stu-id="6194c-110">The `child` axis is the default.</span></span> <span data-ttu-id="6194c-111">因此，可以将该查询指定为：</span><span class="sxs-lookup"><span data-stu-id="6194c-111">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer[not(Order)]  
```  
  
#### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="6194c-112">针对映射架构测试 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="6194c-112">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="6194c-113">复制[示例架构代码](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="6194c-113">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="6194c-114">将该文件另存为 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="6194c-114">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="6194c-115">创建以下模板 (BooleanFunctionsA.xml) 并将其保存到保存 SampleSchema1.xml 的目录中。</span><span class="sxs-lookup"><span data-stu-id="6194c-115">Create the following template (BooleanFunctionsA.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Customer[not(Order)]  
    </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="6194c-116">为映射架构 (SampleSchema1.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="6194c-116">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="6194c-117">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="6194c-117">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="6194c-118">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="6194c-118">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="6194c-119">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="6194c-119">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="6194c-120">下面是执行该模板的部分结果集：</span><span class="sxs-lookup"><span data-stu-id="6194c-120">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="32" SalesPersonID="289" TerritoryID="8" AccountNumber="32" CustomerType="S" />   
  <Customer CustomerID="35" SalesPersonID="275" TerritoryID="2" AccountNumber="35" CustomerType="S" />   
  ...  
</ROOT>  
```  
  
## <a name="b-specify-the-true-and-false-boolean-functions"></a><span data-ttu-id="6194c-121">B.</span><span class="sxs-lookup"><span data-stu-id="6194c-121">B.</span></span> <span data-ttu-id="6194c-122">指定 true() 和 false() 布尔函数</span><span class="sxs-lookup"><span data-stu-id="6194c-122">Specify the true() and false() Boolean functions</span></span>  
 <span data-ttu-id="6194c-123">此查询返回 **\<Customer>** 不具有子元素的上下文节点的所有子元素 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="6194c-123">This query returns all **\<Customer>** element children of the context node that do not have **\<Order>** child elements.</span></span> <span data-ttu-id="6194c-124">就关系而言，此查询返回未下订单的所有客户。</span><span class="sxs-lookup"><span data-stu-id="6194c-124">In relational terms, this query returns all customers who have not placed any orders.</span></span>  
  
```  
/child::Customer[child::Order=false()]  
```  
  
 <span data-ttu-id="6194c-125">`child` 轴为默认轴。</span><span class="sxs-lookup"><span data-stu-id="6194c-125">The `child` axis is the default.</span></span> <span data-ttu-id="6194c-126">因此，可以将该查询指定为：</span><span class="sxs-lookup"><span data-stu-id="6194c-126">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer[Order=false()]  
```  
  
 <span data-ttu-id="6194c-127">此查询等效于以下内容：</span><span class="sxs-lookup"><span data-stu-id="6194c-127">This query is equivalent to the following:</span></span>  
  
```  
/Customer[not(Order)]  
```  
  
 <span data-ttu-id="6194c-128">以下查询返回至少已下了一个订单的客户：</span><span class="sxs-lookup"><span data-stu-id="6194c-128">The following query returns all the customers who have placed at least one order:</span></span>  
  
```  
/Customer[Order=true()]  
```  
  
 <span data-ttu-id="6194c-129">此查询与下列代码功能等效：</span><span class="sxs-lookup"><span data-stu-id="6194c-129">This query is equivalent to this one:</span></span>  
  
```  
/Customer[Order]  
```  
  
#### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="6194c-130">针对映射架构测试 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="6194c-130">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="6194c-131">复制[示例架构代码](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="6194c-131">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="6194c-132">将该文件另存为 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="6194c-132">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="6194c-133">创建以下模板 (BooleanFunctionsB.xml) 并将其保存到保存 SampleSchema1.xml 的目录中。</span><span class="sxs-lookup"><span data-stu-id="6194c-133">Create the following template (BooleanFunctionsB.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[Order=false()]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="6194c-134">为映射架构 (SampleSchema1.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="6194c-134">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="6194c-135">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="6194c-135">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="6194c-136">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="6194c-136">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="6194c-137">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="6194c-137">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="6194c-138">下面是执行该模板的部分结果集：</span><span class="sxs-lookup"><span data-stu-id="6194c-138">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="32" SalesPersonID="289" TerritoryID="8" AccountNumber="32" CustomerType="S" />   
  <Customer CustomerID="35" SalesPersonID="275" TerritoryID="2" AccountNumber="35" CustomerType="S" />   
  ...  
</ROOT>  
```  
  
  
