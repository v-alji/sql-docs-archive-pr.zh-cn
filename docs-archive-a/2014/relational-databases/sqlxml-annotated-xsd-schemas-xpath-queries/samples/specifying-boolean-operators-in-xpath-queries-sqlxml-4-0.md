---
title: 在 (SQLXML 4.0) 的 XPath 查询中指定布尔运算符 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath operators [SQLXML]
- OR operator
- Boolean operators
- XPath queries [SQLXML], Boolean operators
- operators [SQLXML]
ms.assetid: 9928cff5-62ac-42aa-96bf-2e09a1df0bc3
author: rothja
ms.author: jroth
ms.openlocfilehash: 02dd6e1f120b53382ce984684ea352b36d34b768
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577480"
---
# <a name="specifying-boolean-operators-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="16c66-102">在 XPath 查询中指定布尔运算符 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="16c66-102">Specifying Boolean Operators in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="16c66-103">以下示例说明如何在 XPath 查询中指定布尔运算符。</span><span class="sxs-lookup"><span data-stu-id="16c66-103">The following example shows how Boolean operators are specified in XPath queries.</span></span> <span data-ttu-id="16c66-104">本示例中的 XPath 查询针对 SampleSchema1.xml 中包含的映射架构指定。</span><span class="sxs-lookup"><span data-stu-id="16c66-104">The XPath query in this example is specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="16c66-105">有关此示例架构的信息，请参阅[&#40;SQLXML 4.0&#41;的 XPath 批注的 XSD 架构示例](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="16c66-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="16c66-106">示例</span><span class="sxs-lookup"><span data-stu-id="16c66-106">Examples</span></span>  
  
### <a name="a-specify-the-or-boolean-operator"></a><span data-ttu-id="16c66-107">A.</span><span class="sxs-lookup"><span data-stu-id="16c66-107">A.</span></span> <span data-ttu-id="16c66-108">指定 OR 布尔运算符</span><span class="sxs-lookup"><span data-stu-id="16c66-108">Specify the OR Boolean operator</span></span>  
 <span data-ttu-id="16c66-109">此 XPath 查询将返回 **\<Customer>** **CustomerID**属性值为13或31的上下文节点的子元素：</span><span class="sxs-lookup"><span data-stu-id="16c66-109">This XPath query returns the **\<Customer>** element children of the context node with the **CustomerID** attribute value of 13 or 31:</span></span>  
  
```  
/child::Customer[attribute::CustomerID="13" or attribute::CustomerID="31"]  
```  
  
 <span data-ttu-id="16c66-110">可以指定指向 `attribute` 轴 (@) 的快捷方式，并且，由于 `child` 轴是默认的，因此可以忽略它：</span><span class="sxs-lookup"><span data-stu-id="16c66-110">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted:</span></span>  
  
```  
/Customer[@CustomerID="13" or @CustomerID="31"]  
```  
  
 <span data-ttu-id="16c66-111">在谓词中， `attribute` 是轴， `CustomerID` 是节点测试 (如果**CustomerID**是节点，则为 TRUE **\<attribute>** ，因为 **\<attribute>** 节点是轴的主节点 `attribute`) 。</span><span class="sxs-lookup"><span data-stu-id="16c66-111">In the predicate, `attribute` is the axis and `CustomerID` is the node test (TRUE if **CustomerID** is an **\<attribute>** node, because the **\<attribute>** node is the primary node for the `attribute` axis).</span></span> <span data-ttu-id="16c66-112">谓词筛选 **\<Customer>** 元素并仅返回满足谓词中指定的条件的元素。</span><span class="sxs-lookup"><span data-stu-id="16c66-112">The predicate filters the **\<Customer>** elements and returns only those that satisfy the condition specified in the predicate.</span></span>  
  
##### <a name="to-test-the-xpath-queries-against-the-mapping-schema"></a><span data-ttu-id="16c66-113">针对映射架构测试 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="16c66-113">To test the XPath queries against the mapping schema</span></span>  
  
1.  <span data-ttu-id="16c66-114">复制[示例架构代码](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="16c66-114">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="16c66-115">将该文件另存为 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="16c66-115">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="16c66-116">创建以下模板 (BooleanOperatorsA.xml) 并将其保存到保存 SampleSchema1.xml 的目录中。</span><span class="sxs-lookup"><span data-stu-id="16c66-116">Create the following template (BooleanOperatorsA.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[@CustomerID="13" or @CustomerID="31"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="16c66-117">为映射架构 (SampleSchema1.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="16c66-117">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="16c66-118">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="16c66-118">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="16c66-119">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="16c66-119">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="16c66-120">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="16c66-120">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="16c66-121">下面是执行该模板的结果集：</span><span class="sxs-lookup"><span data-stu-id="16c66-121">Here is the result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="31" SalesPersonID="286" TerritoryID="7" AccountNumber="31" CustomerType="S" Orders="Ord-51803 Ord-69427">  
    <Order SalesOrderID="Ord-51803" SalesPersonID="286" OrderDate="2003-08-01T00:00:00" DueDate="2003-08-13T00:00:00" ShipDate="2003-08-08T00:00:00">  
      <OrderDetail ProductID="Prod-718" UnitPrice="1059.31" OrderQty="1" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-838" UnitPrice="1059.31" OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
    <Order SalesOrderID="Ord-69427" SalesPersonID="286" OrderDate="2004-05-01T00:00:00" DueDate="2004-05-13T00:00:00" ShipDate="2004-05-08T00:00:00">  
      <OrderDetail ProductID="Prod-835" UnitPrice="440.1742" OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
  </Customer>  
</ROOT>  
```  
  
  
