---
title: 在 (SQLXML 4.0) 的 XPath 查询中指定算术运算符 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- arithmetic operators
- XPath operators [SQLXML]
- XPath queries [SQLXML], arithmetic operators
- operators [SQLXML]
ms.assetid: fdfbc87d-759f-4abc-acf5-a21de01f78d3
author: rothja
ms.author: jroth
ms.openlocfilehash: 904f3b920029d45d1b72641a19e2ac07befd4def
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577484"
---
# <a name="specifying-arithmetic-operators-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="44737-102">在 XPath 查询中指定算数运算符 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="44737-102">Specifying Arithmetic Operators in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="44737-103">以下示例说明如何在 XPath 查询中指定算数运算符。</span><span class="sxs-lookup"><span data-stu-id="44737-103">The following example shows how arithmetic operators are specified in XPath queries.</span></span> <span data-ttu-id="44737-104">本示例中的 XPath 查询针对 SampleSchema1.xml 中包含的映射架构指定。</span><span class="sxs-lookup"><span data-stu-id="44737-104">The XPath query in this example is specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="44737-105">有关此示例架构的信息，请参阅[&#40;SQLXML 4.0&#41;的 XPath 批注的 XSD 架构示例](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="44737-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="44737-106">示例</span><span class="sxs-lookup"><span data-stu-id="44737-106">Examples</span></span>  
  
### <a name="a-specify-the--arithmetic-operator"></a><span data-ttu-id="44737-107">A.</span><span class="sxs-lookup"><span data-stu-id="44737-107">A.</span></span> <span data-ttu-id="44737-108">指定 \* 算数运算符</span><span class="sxs-lookup"><span data-stu-id="44737-108">Specify the \* arithmetic operator</span></span>  
 <span data-ttu-id="44737-109">此 XPath 查询返回 **\<OrderDetail>** 满足指定谓词的元素：</span><span class="sxs-lookup"><span data-stu-id="44737-109">This XPath query returns **\<OrderDetail>** elements that satisfy the predicate specified:</span></span>  
  
```  
/child::OrderDetail[@UnitPrice * @Quantity = 12.350]  
```  
  
 <span data-ttu-id="44737-110">在查询中， `child` 是轴， `OrderDetail` 是节点测试 (如果**OrderDetail**为，则为 TRUE **\<element node>** ，因为 **\<element>** 节点是轴) 的主节点 `child` 。</span><span class="sxs-lookup"><span data-stu-id="44737-110">In the query, `child` is the axis and `OrderDetail` is the node test (TRUE if **OrderDetail** is an **\<element node>**, because the **\<element>** node is the primary node for the `child` axis).</span></span> <span data-ttu-id="44737-111">对于所有 **\<OrderDetail>** 元素节点，将应用谓词中的测试，并只返回满足条件的那些节点。</span><span class="sxs-lookup"><span data-stu-id="44737-111">For all the **\<OrderDetail>** element nodes, the test in the predicate is applied, and only those nodes that satisfy the condition are returned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="44737-112">XPath 中的数字是双精度浮点数，对本示例中的浮点数进行比较将导致舍入。</span><span class="sxs-lookup"><span data-stu-id="44737-112">The numbers in XPath are double-precision floating-point numbers, and comparing floating-point numbers as in the example causes rounding.</span></span>  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="44737-113">针对映射架构测试 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="44737-113">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="44737-114">复制[示例架构代码](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="44737-114">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="44737-115">将该文件另存为 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="44737-115">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="44737-116">创建以下模板 (ArithmeticOperatorA.xml)，并将它保存在保存 SampleSchema1.xml 的目录中。</span><span class="sxs-lookup"><span data-stu-id="44737-116">Create the following template (ArithmeticOperatorA.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /OrderDetail[@UnitPrice * @OrderQty = 12.350]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="44737-117">为映射架构 (SampleSchema1.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="44737-117">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="44737-118">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="44737-118">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="44737-119">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="44737-119">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="44737-120">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="44737-120">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
```  
Here is the partial result set of the template execution:    
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-710" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
   ...  
</ROOT>  
```  
  
  
