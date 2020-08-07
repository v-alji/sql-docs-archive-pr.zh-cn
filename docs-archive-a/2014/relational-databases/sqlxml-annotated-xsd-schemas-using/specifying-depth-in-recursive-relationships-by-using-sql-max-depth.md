---
title: 使用 sql：最大深度为递归关系指定深度 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- max-depth annotation
- XPath queries [SQLXML], recursive relationships
- depth in recursive relationships [SQLXML]
- annotated XSD schemas, recursive relationships
- relationships [SQLXML], recursive relationships
- self joins
- recursive relationships [SQLXML]
- recursion [SQLXML]
- sql:max-depth
- recursive joins [SQLXML]
ms.assetid: 0ffdd57d-dc30-44d9-a8a0-f21cadedb327
author: rothja
ms.author: jroth
ms.openlocfilehash: 5e3ccb2de9c7b2ac8f8702b52aa990d755620e46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587743"
---
# <a name="specifying-depth-in-recursive-relationships-by-using-sqlmax-depth"></a><span data-ttu-id="31f1c-102">使用 sql:max-depth 指定递归关系中的深度</span><span class="sxs-lookup"><span data-stu-id="31f1c-102">Specifying Depth in Recursive Relationships by Using sql:max-depth</span></span>
  <span data-ttu-id="31f1c-103">在关系数据库中，当表涉及与其自身的关系时，将它称为递归关系。</span><span class="sxs-lookup"><span data-stu-id="31f1c-103">In relational databases, when a table is involved in a relationship with itself, it is called a recursive relationship.</span></span> <span data-ttu-id="31f1c-104">例如，在监督者和被监督者关系中，存储雇员记录的表涉及与其自身的关系。</span><span class="sxs-lookup"><span data-stu-id="31f1c-104">For example, in a supervisor-supervisee relationship, a table storing employee records is involved in a relationship with itself.</span></span> <span data-ttu-id="31f1c-105">在这种情况下，雇员表在关系的一端扮演监督者的角色，而在另一端则扮演被监督者的角色。</span><span class="sxs-lookup"><span data-stu-id="31f1c-105">In this case, the employees table plays a role of supervisor on one side of the relationship, and the same table plays a role of supervisee on the other side.</span></span>  
  
 <span data-ttu-id="31f1c-106">映射架构可以包含元素及其祖先属于相同类型的递归关系。</span><span class="sxs-lookup"><span data-stu-id="31f1c-106">Mapping schemas can include recursive relationships where an element and its ancestor are of the same type.</span></span>  
  
## <a name="example-a"></a><span data-ttu-id="31f1c-107">示例 A</span><span class="sxs-lookup"><span data-stu-id="31f1c-107">Example A</span></span>  
 <span data-ttu-id="31f1c-108">考虑以下表：</span><span class="sxs-lookup"><span data-stu-id="31f1c-108">Consider the following table:</span></span>  
  
```  
Emp (EmployeeID, FirstName, LastName, ReportsTo)  
```  
  
 <span data-ttu-id="31f1c-109">在该表中，ReportsTo 列存储经理的雇员 ID。</span><span class="sxs-lookup"><span data-stu-id="31f1c-109">In this table, the ReportsTo column stores the employee ID of the manager.</span></span>  
  
 <span data-ttu-id="31f1c-110">假设您想生成一个雇员 XML 层次结构，其中经理雇员位于层次结构的顶部，而向该经理报告的雇员出现在对应的层次结构中，如以下 XML 片段示例所示。</span><span class="sxs-lookup"><span data-stu-id="31f1c-110">Assume that you want to generate an XML hierarchy of employees in which the manager employee is at the top of the hierarchy, and in which the employees that report to that manager appear in the corresponding hierarchy as shown in the following sample XML fragment.</span></span> <span data-ttu-id="31f1c-111">此片段显示的内容是员工1的*递归树*。</span><span class="sxs-lookup"><span data-stu-id="31f1c-111">What this fragment shows is the *recursive tree* for employee 1.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
     <Emp FirstName="Andrew" EmployeeID="2" LastName="Fuller" />   
     <Emp FirstName="Janet" EmployeeID="3" LastName="Leverling">  
        <Emp FirstName="Margaret" EmployeeID="4" LastName="Peacock">  
          <Emp FirstName="Steven" EmployeeID="5" LastName="Devolio">  
...  
...  
</root>  
```  
  
 <span data-ttu-id="31f1c-112">在该片段中，雇员 5 向雇员 4 报告，雇员 4 向雇员 3 报告，雇员 3 和 2 向雇员 1 报告。</span><span class="sxs-lookup"><span data-stu-id="31f1c-112">In this fragment, employee 5 reports to employee 4, employee 4 reports to employee 3, and employees 3 and 2 reports to employee 1.</span></span>  
  
 <span data-ttu-id="31f1c-113">若要产生该结果，可以使用以下 XSD 架构，并指定针对它的 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="31f1c-113">To produce this result, you can use the following XSD schema and specify an XPath query against it.</span></span> <span data-ttu-id="31f1c-114">此架构描述 **\<Emp>** 类型为 EmployeeType 的元素，该元素包含 **\<Emp>** 一个相同类型的子元素 EmployeeType。</span><span class="sxs-lookup"><span data-stu-id="31f1c-114">The schema describes an **\<Emp>** element of type EmployeeType, consisting of an **\<Emp>** child element of the same type, EmployeeType.</span></span> <span data-ttu-id="31f1c-115">此即属于递归关系（元素和其祖先属于相同类型）。</span><span class="sxs-lookup"><span data-stu-id="31f1c-115">This is a recursive relationship (the element and its ancestor are of the same type).</span></span> <span data-ttu-id="31f1c-116">此外，架构使用 **\<sql:relationship>** 来描述监控器和被监督者之间的父子关系。</span><span class="sxs-lookup"><span data-stu-id="31f1c-116">In addition, the schema uses a **\<sql:relationship>** to describe the parent-child relationship between the supervisor and supervisee.</span></span> <span data-ttu-id="31f1c-117">请注意，在这 **\<sql:relationship>** 种情况下，Emp 既是父级又是子表。</span><span class="sxs-lookup"><span data-stu-id="31f1c-117">Note that in this **\<sql:relationship>**, Emp is both the parent and the child table.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"  
                                  parent="Emp"  
                                  parent-key="EmployeeID"  
                                  child="Emp"  
                                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp" type="EmployeeType"   
                          sql:relation="Emp"   
                          sql:key-fields="EmployeeID"   
                          sql:limit-field="ReportsTo" />  
  <xsd:complexType name="EmployeeType">  
    <xsd:sequence>  
      <xsd:element name="Emp" type="EmployeeType"   
                              sql:relation="Emp"   
                              sql:key-fields="EmployeeID"  
                              sql:relationship="SupervisorSupervisee"  
                              sql:max-depth="6" />  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:ID" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 <span data-ttu-id="31f1c-118">因为该关系是递归关系，所以需要以某种方式指定在架构中的递归深度。</span><span class="sxs-lookup"><span data-stu-id="31f1c-118">Because the relationship is recursive, you need some way to specify the depth of recursion in the schema.</span></span> <span data-ttu-id="31f1c-119">否则，结果将是无穷递归的（雇员向雇员报告而该雇员又向雇员报告，以此类推）。</span><span class="sxs-lookup"><span data-stu-id="31f1c-119">Otherwise, the result will be an endless recursion (employee reporting to employee reporting to employee, and so on).</span></span> <span data-ttu-id="31f1c-120">可以使用 `sql:max-depth` 批注指定递归的深度。</span><span class="sxs-lookup"><span data-stu-id="31f1c-120">The `sql:max-depth` annotation allows you to specify how deep in the recursion to go.</span></span> <span data-ttu-id="31f1c-121">在该特定示例中，若要指定 `sql:max-depth` 的值，必须知道在该公司中其管理层次结构的深度。</span><span class="sxs-lookup"><span data-stu-id="31f1c-121">In this particular example, to specify a value for `sql:max-depth`, you must know how deep the management hierarchy goes in the company.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31f1c-122">该架构指定 `sql:limit-field` 批注，但不指定 `sql:limit-value` 批注。</span><span class="sxs-lookup"><span data-stu-id="31f1c-122">The schema specifies the `sql:limit-field` annotation, but does not specify the `sql:limit-value` annotation.</span></span> <span data-ttu-id="31f1c-123">这会使得所生成的层次结构的顶级节点仅为那些不向任何人报告的雇员。</span><span class="sxs-lookup"><span data-stu-id="31f1c-123">This limits the top node in the resulting hierarchy to only those employees who do not report to anyone.</span></span> <span data-ttu-id="31f1c-124"> (的上级是 NULL。 ) 指定 `sql:limit-field` 和不指定 `sql:limit-value` (默认为 null) 注释即可实现此目标。</span><span class="sxs-lookup"><span data-stu-id="31f1c-124">(ReportsTo is NULL.) Specifying `sql:limit-field` and not specifying `sql:limit-value` (which defaults to NULL) annotation accomplishes this.</span></span> <span data-ttu-id="31f1c-125">如果要让所生成的 XML 包含每个可能的报告树（表中每个雇员的报告树），请从架构中删除 `sql:limit-field` 批注。</span><span class="sxs-lookup"><span data-stu-id="31f1c-125">If you want the resulting XML to include every possible reporting tree (the reporting tree for every employee in the table), remove the `sql:limit-field` annotation from the schema.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31f1c-126">以下过程使用 tempdb 数据库。</span><span class="sxs-lookup"><span data-stu-id="31f1c-126">The following procedure uses the tempdb database.</span></span>  
  
#### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="31f1c-127">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="31f1c-127">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="31f1c-128">在虚拟根目录所指向的 tempdb 数据库中创建称为 Emp 的示例表。</span><span class="sxs-lookup"><span data-stu-id="31f1c-128">Create a sample table called Emp in the tempdb database to which the virtual root points.</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Emp (  
           EmployeeID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    ```  
  
2.  <span data-ttu-id="31f1c-129">添加以下示例数据：</span><span class="sxs-lookup"><span data-stu-id="31f1c-129">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Emp values (1, 'Nancy', 'Devolio',NULL)  
    INSERT INTO Emp values (2, 'Andrew', 'Fuller',1)  
    INSERT INTO Emp values (3, 'Janet', 'Leverling',1)  
    INSERT INTO Emp values (4, 'Margaret', 'Peacock',3)  
    INSERT INTO Emp values (5, 'Steven', 'Devolio',4)  
    INSERT INTO Emp values (6, 'Nancy', 'Buchanan',5)  
    INSERT INTO Emp values (7, 'Michael', 'Suyama',6)  
    ```  
  
3.  <span data-ttu-id="31f1c-130">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="31f1c-130">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="31f1c-131">将该文件另存为 maxDepth.xml。</span><span class="sxs-lookup"><span data-stu-id="31f1c-131">Save the file as maxDepth.xml.</span></span>  
  
4.  <span data-ttu-id="31f1c-132">复制以下模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="31f1c-132">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="31f1c-133">该文件另存为 maxDepthT.xml，保存在与 maxDepth.xml 相同的目录中。</span><span class="sxs-lookup"><span data-stu-id="31f1c-133">Save the file as maxDepthT.xml in the same directory where you saved maxDepth.xml.</span></span> <span data-ttu-id="31f1c-134">模板中的查询将返回 Emp 表中的所有雇员。</span><span class="sxs-lookup"><span data-stu-id="31f1c-134">The query in the template returns all the employees in the Emp table.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="maxDepth.xml">  
        /Emp  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="31f1c-135">为映射架构 (maxDepth.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="31f1c-135">The directory path specified for the mapping schema (maxDepth.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="31f1c-136">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="31f1c-136">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\maxDepth.xml"  
    ```  
  
5.  <span data-ttu-id="31f1c-137">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="31f1c-137">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span> <span data-ttu-id="31f1c-138">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="31f1c-138">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="31f1c-139">结果如下：</span><span class="sxs-lookup"><span data-stu-id="31f1c-139">This is the result:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
  <Emp FirstName="Andrew" EmployeeID="2" LastName="Fuller" />   
    <Emp FirstName="Janet" EmployeeID="3" LastName="Leverling">  
      <Emp FirstName="Margaret" EmployeeID="4" LastName="Peacock">  
        <Emp FirstName="Steven" EmployeeID="5" LastName="Devolio">  
          <Emp FirstName="Nancy" EmployeeID="6" LastName="Buchanan">  
            <Emp FirstName="Michael" EmployeeID="7" LastName="Suyama" />   
          </Emp>  
        </Emp>  
      </Emp>  
    </Emp>  
  </Emp>  
</root>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="31f1c-140">若要在结果中产生不同深度的层次结构，请更改架构中 `sql:max-depth` 批注的值，并在每次更改之后再次执行该模板。</span><span class="sxs-lookup"><span data-stu-id="31f1c-140">To produce different depths of hierarchies in the result, change the value of the `sql:max-depth` annotation in the schema and execute the template again after each change.</span></span>  
  
 <span data-ttu-id="31f1c-141">在前面的架构中，所有 **\<Emp>** 元素都具有完全相同的属性集 (**雇员 id**、 **FirstName**和**LastName**) 。</span><span class="sxs-lookup"><span data-stu-id="31f1c-141">In the previous schema, all the **\<Emp>** elements had exactly the same set of attributes (**EmployeeID**, **FirstName**, and **LastName**).</span></span> <span data-ttu-id="31f1c-142">已对以下架构进行了略微修改，为向经理报告的所有元素返回其他**上级**属性 **\<Emp>** 。</span><span class="sxs-lookup"><span data-stu-id="31f1c-142">The following schema has been slightly modified to return an additional **ReportsTo** attribute for all the **\<Emp>** elements that report to a manager.</span></span>  
  
 <span data-ttu-id="31f1c-143">例如，该 XML 片段显示雇员 1 的下级：</span><span class="sxs-lookup"><span data-stu-id="31f1c-143">For example, this XML fragment shows the subordinates of employee 1:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
<Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
  <Emp FirstName="Andrew" EmployeeID="2"   
       ReportsTo="1" LastName="Fuller" />   
  <Emp FirstName="Janet" EmployeeID="3"   
       ReportsTo="1" LastName="Leverling">  
...  
...  
```  
  
 <span data-ttu-id="31f1c-144">这是修改后的架构：</span><span class="sxs-lookup"><span data-stu-id="31f1c-144">This is the revised schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:documentation>  
      Customer-Order-Order Details Schema  
      Copyright 2000 Microsoft. All rights reserved.  
    </xsd:documentation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"   
                  parent="Emp"  
                  parent-key="EmployeeID"  
                  child="Emp"  
                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp"   
                   type="EmpType"   
                   sql:relation="Emp"   
                   sql:key-fields="EmployeeID"   
                   sql:limit-field="ReportsTo" />  
  <xsd:complexType name="EmpType">  
    <xsd:sequence>  
       <xsd:element name="Emp"   
                    type="EmpType"   
                    sql:relation="Emp"   
                    sql:key-fields="EmployeeID"  
                    sql:relationship="SupervisorSupervisee"  
                    sql:max-depth="6"/>  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:int" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
    <xsd:attribute name="ReportsTo" type="xsd:int" />  
  </xsd:complexType>  
</xsd:schema>  
```  
  
## <a name="sqlmax-depth-annotation"></a><span data-ttu-id="31f1c-145">sql:max-depth 批注</span><span class="sxs-lookup"><span data-stu-id="31f1c-145">sql:max-depth Annotation</span></span>  
 <span data-ttu-id="31f1c-146">在由递归关系组成的架构中，必须在架构中显式指定递归的深度。</span><span class="sxs-lookup"><span data-stu-id="31f1c-146">In a schema consisting of recursive relationships, the depth of recursion must be explicitly specified in the schema.</span></span> <span data-ttu-id="31f1c-147">若要成功生成可返回所请求的结果的相应 FOR XML EXPLICIT 查询，则必须这样做。</span><span class="sxs-lookup"><span data-stu-id="31f1c-147">This is required to successfully produce the corresponding FOR XML EXPLICIT query that returns the requested results.</span></span>  
  
 <span data-ttu-id="31f1c-148">使用该架构中的 `sql:max-depth` 批注可以指定此架构中所描述的递归关系中的递归深度。</span><span class="sxs-lookup"><span data-stu-id="31f1c-148">Use the `sql:max-depth` annotation in the schema to specify the depth of recursion in a recursive relationship that is described in the schema.</span></span> <span data-ttu-id="31f1c-149">`sql:max-depth` 批注的值是指示递归数的正整数（1 到 50）：值为 1 将使递归停止于指定了 `sql:max-depth` 批注的元素；值为 2 则使递归停止于指定了 `sql:max-depth` 的元素的下一级；以此类推。</span><span class="sxs-lookup"><span data-stu-id="31f1c-149">The value of the `sql:max-depth` annotation is a positive integer (1 to 50) that indicates the number of recursions:  A value of 1 stops the recursion at the element for which the `sql:max-depth` annotation is specified; a value of 2 stops the recursion at the next level from the element at which `sql:max-depth` is specified; and so on.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31f1c-150">在基础实现中，针对映射架构指定的 XPath 查询将转换为 SELECT .。。FOR XML EXPLICIT 查询。</span><span class="sxs-lookup"><span data-stu-id="31f1c-150">In the underlying implementation, an XPath query that is specified against a mapping schema is converted to a SELECT ... FOR XML EXPLICIT query.</span></span> <span data-ttu-id="31f1c-151">该查询需要您指定一个有限的递归深度。</span><span class="sxs-lookup"><span data-stu-id="31f1c-151">This query requires you to specify a finite depth of recursion.</span></span> <span data-ttu-id="31f1c-152">为 `sql:max-depth` 指定的值越高，所生成的 FOR XML EXPLICIT 查询越大。</span><span class="sxs-lookup"><span data-stu-id="31f1c-152">The higher the value that you specify for `sql:max-depth`, the larger the FOR XML EXPLICIT query that is generated.</span></span> <span data-ttu-id="31f1c-153">这可能会使检索时间变长。</span><span class="sxs-lookup"><span data-stu-id="31f1c-153">This might slow the retrieval time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31f1c-154">Updategram 和 XML 大容量加载将忽略最大深度批注。</span><span class="sxs-lookup"><span data-stu-id="31f1c-154">Updategrams and XML Bulk Load ignore the max-depth annotation.</span></span> <span data-ttu-id="31f1c-155">这意味着，不管为最大深度指定了什么值，都将发生递归更新或插入。</span><span class="sxs-lookup"><span data-stu-id="31f1c-155">This means, recursive updates or insertions will happen regardless of what value you specify for max-depth.</span></span>  
  
## <a name="specifying-sqlmax-depth-on-complex-elements"></a><span data-ttu-id="31f1c-156">在复杂元素上指定 sql:max-depth</span><span class="sxs-lookup"><span data-stu-id="31f1c-156">Specifying sql:max-depth on Complex Elements</span></span>  
 <span data-ttu-id="31f1c-157">可以在任何复杂内容元素上指定 `sql:max-depth` 批注。</span><span class="sxs-lookup"><span data-stu-id="31f1c-157">The `sql:max-depth` annotation can be specified on any complex content element.</span></span>  
  
### <a name="recursive-elements"></a><span data-ttu-id="31f1c-158">递归元素</span><span class="sxs-lookup"><span data-stu-id="31f1c-158">Recursive Elements</span></span>  
 <span data-ttu-id="31f1c-159">如果在递归关系中的父元素和子元素上都指定了 `sql:max-depth`，则在父元素上指定的 `sql:max-depth` 批注优先。</span><span class="sxs-lookup"><span data-stu-id="31f1c-159">If `sql:max-depth` is specified on both the parent element and the child element in a recursive relationship, the `sql:max-depth` annotation specified on the parent takes precedence.</span></span> <span data-ttu-id="31f1c-160">例如，在以下架构中，在父、子雇员元素上都指定了 `sql:max-depth` 批注。</span><span class="sxs-lookup"><span data-stu-id="31f1c-160">For example, in the following schema, the `sql:max-depth` annotation is specified on both the parent and the child employee elements.</span></span> <span data-ttu-id="31f1c-161">在这种情况下，在 `sql:max-depth=4` **\<Emp>** 父元素上指定 (扮演监察员) 的角色，优先。</span><span class="sxs-lookup"><span data-stu-id="31f1c-161">In this case, `sql:max-depth=4`, specified on the **\<Emp>** parent element (playing a role of supervisor), takes precedence.</span></span> <span data-ttu-id="31f1c-162">在 `sql:max-depth` (扮演被监督者) 角色的子元素上指定的将被 **\<Emp>** 忽略。</span><span class="sxs-lookup"><span data-stu-id="31f1c-162">The `sql:max-depth` specified on the child **\<Emp>** element (playing a role of supervisee) is ignored.</span></span>  
  
#### <a name="example-b"></a><span data-ttu-id="31f1c-163">示例 B</span><span class="sxs-lookup"><span data-stu-id="31f1c-163">Example B</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"  
                                  parent="Emp"  
                                  parent-key="EmployeeID"  
                                  child="Emp"  
                                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp" type="EmployeeType"   
                          sql:relation="Emp"   
                          sql:key-fields="EmployeeID"   
                          sql:limit-field="ReportsTo"   
                          sql:max-depth="3" />  
  <xsd:complexType name="EmployeeType">  
    <xsd:sequence>  
      <xsd:element name="Emp" type="EmployeeType"   
                              sql:relation="Emp"   
                              sql:key-fields="EmployeeID"  
                              sql:relationship="SupervisorSupervisee"  
                              sql:max-depth="2" />  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:ID" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 <span data-ttu-id="31f1c-164">若要测试此架构，请按照本主题前面的示例 A 中提供的步骤进行操作。</span><span class="sxs-lookup"><span data-stu-id="31f1c-164">To test this schema, follow the steps provided for Sample A, earlier in this topic.</span></span>  
  
### <a name="nonrecursive-elements"></a><span data-ttu-id="31f1c-165">非递归元素</span><span class="sxs-lookup"><span data-stu-id="31f1c-165">Nonrecursive Elements</span></span>  
 <span data-ttu-id="31f1c-166">如果在架构中不导致任何递归的元素上指定 `sql:max-depth` 批注，将忽略该批注。</span><span class="sxs-lookup"><span data-stu-id="31f1c-166">If the `sql:max-depth` annotation is specified on an element in the schema that does not cause any recursion, it is ignored.</span></span> <span data-ttu-id="31f1c-167">在下面的架构中， **\<Emp>** 元素由 **\<Constant>** 子元素组成，后者又具有 **\<Emp>** 子元素。</span><span class="sxs-lookup"><span data-stu-id="31f1c-167">In the following schema, an **\<Emp>** element consists of a **\<Constant>** child element, which, in turn, has an **\<Emp>** child element.</span></span>  
  
 <span data-ttu-id="31f1c-168">在此架构中，将 `sql:max-depth` 忽略在元素上指定的批注， **\<Constant>** 因为 **\<Emp>** 父元素和子元素之间不存在递归 **\<Constant>** 。</span><span class="sxs-lookup"><span data-stu-id="31f1c-168">In this schema, the `sql:max-depth` annotation specified on the **\<Constant>** element is ignored because there is no recursion between the **\<Emp>** parent and the **\<Constant>** child element.</span></span> <span data-ttu-id="31f1c-169">但在 **\<Emp>** 祖先和子级之间存在递归 **\<Emp>** 。</span><span class="sxs-lookup"><span data-stu-id="31f1c-169">But there is recursion between the **\<Emp>** ancestor and the **\<Emp>** child.</span></span> <span data-ttu-id="31f1c-170">该架构在二者上都指定了 `sql:max-depth` 批注。</span><span class="sxs-lookup"><span data-stu-id="31f1c-170">The schema specifies the `sql:max-depth` annotation on both.</span></span> <span data-ttu-id="31f1c-171">因此，在 `sql:max-depth` 主管角色) 中指定的 (的批注 **\<Emp>** 优先。</span><span class="sxs-lookup"><span data-stu-id="31f1c-171">Therefore, the `sql:max-depth` annotation that is specified on the ancestor (**\<Emp>** in the supervisor role) takes precedence.</span></span>  
  
#### <a name="example-c"></a><span data-ttu-id="31f1c-172">示例 C</span><span class="sxs-lookup"><span data-stu-id="31f1c-172">Example C</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"   
                  parent="Emp"   
                  child="Emp"   
                  parent-key="EmployeeID"   
                  child-key="ReportsTo"/>  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp"   
               sql:relation="Emp"   
               type="EmpType"  
               sql:limit-field="ReportsTo"  
               sql:max-depth="1" />  
    <xsd:complexType name="EmpType" >  
      <xsd:sequence>  
       <xsd:element name="Constant"   
                    sql:is-constant="1"   
                    sql:max-depth="20" >  
         <xsd:complexType >  
           <xsd:sequence>  
            <xsd:element name="Emp"   
                         sql:relation="Emp" type="EmpType"  
                         sql:relationship="SupervisorSupervisee"   
                         sql:max-depth="3" />  
         </xsd:sequence>  
         </xsd:complexType>  
         </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="EmployeeID" type="xsd:int" />  
    </xsd:complexType>  
</xsd:schema>  
```  
  
 <span data-ttu-id="31f1c-173">若要测试该架构，请执行为本主题前面的示例 A 提供的步骤。</span><span class="sxs-lookup"><span data-stu-id="31f1c-173">To test this schema, follow the steps provided for Example A, earlier in this topic.</span></span>  
  
## <a name="complex-types-derived-by-restriction"></a><span data-ttu-id="31f1c-174">由限制派生的复杂类型</span><span class="sxs-lookup"><span data-stu-id="31f1c-174">Complex Types Derived by Restriction</span></span>  
 <span data-ttu-id="31f1c-175">如果你使用派生复杂类型 **\<restriction>** ，则对应的基本复杂类型的元素将无法指定该 `sql:max-depth` 批注。</span><span class="sxs-lookup"><span data-stu-id="31f1c-175">If you have a complex type derivation by **\<restriction>**, elements of the corresponding base complex type cannot specify the `sql:max-depth` annotation.</span></span> <span data-ttu-id="31f1c-176">在这些情况下，可以向派生类型的元素添加 `sql:max-depth` 批注。</span><span class="sxs-lookup"><span data-stu-id="31f1c-176">In these cases, the `sql:max-depth` annotation can be added to the element of the derived type.</span></span>  
  
 <span data-ttu-id="31f1c-177">另一方面，如果您使用派生复杂类型 **\<extension>** ，则对应的基本复杂类型的元素可以指定 `sql:max-depth` 批注。</span><span class="sxs-lookup"><span data-stu-id="31f1c-177">On the other hand, if you have a complex type derivation by **\<extension>**, the elements of the corresponding base complex type can specify the `sql:max-depth` annotation.</span></span>  
  
 <span data-ttu-id="31f1c-178">例如，以下 XSD 架构将产生错误，因为在基类型上指定了 `sql:max-depth` 批注。</span><span class="sxs-lookup"><span data-stu-id="31f1c-178">For example, the following XSD schema generates an error because the `sql:max-depth` annotation is specified on the base type.</span></span> <span data-ttu-id="31f1c-179">在 **\<restriction>** 从另一种类型派生的类型上不支持此注释。</span><span class="sxs-lookup"><span data-stu-id="31f1c-179">This annotation is not supported on a type that is derived by **\<restriction>** from another type.</span></span> <span data-ttu-id="31f1c-180">若要解决该问题，必须更改架构，并在派生类型的元素上指定 `sql:max-depth` 批注。</span><span class="sxs-lookup"><span data-stu-id="31f1c-180">To fix this problem, you must change the schema and specify the `sql:max-depth` annotation on element in the derived type.</span></span>  
  
#### <a name="example-d"></a><span data-ttu-id="31f1c-181">示例 D</span><span class="sxs-lookup"><span data-stu-id="31f1c-181">Example D</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:complexType name="CustomerBaseType">   
    <xsd:sequence>  
       <xsd:element name="CID" msdata:field="CustomerID" />  
       <xsd:element name="CompanyName"/>  
       <xsd:element name="Customers" msdata:max-depth="3">  
         <xsd:annotation>  
           <xsd:appinfo>  
             <msdata:relationship  
                     parent="Customers"  
                     parent-key="CustomerID"  
                     child-key="CustomerID"  
                     child="Customers" />  
           </xsd:appinfo>  
         </xsd:annotation>  
       </xsd:element>  
    </xsd:sequence>  
  </xsd:complexType>  
  <xsd:element name="Customers" type="CustomerType"/>  
  <xsd:complexType name="CustomerType">  
    <xsd:complexContent>  
       <xsd:restriction base="CustomerBaseType">  
          <xsd:sequence>  
            <xsd:element name="CID"   
                         type="xsd:string"/>  
            <xsd:element name="CompanyName"   
                         type="xsd:string"  
                         msdata:field="CName" />  
            <xsd:element name="Customers"   
                         type="CustomerType" />  
          </xsd:sequence>  
       </xsd:restriction>  
    </xsd:complexContent>  
  </xsd:complexType>  
</xsd:schema>   
```  
  
 <span data-ttu-id="31f1c-182">在此架构中，在 `sql:max-depth` 复杂类型上指定了 `CustomerBaseType`。</span><span class="sxs-lookup"><span data-stu-id="31f1c-182">In the schema, `sql:max-depth` is specified on a `CustomerBaseType` complex type.</span></span> <span data-ttu-id="31f1c-183">该架构还指定 **\<Customer>** 派生自的类型为的元素 `CustomerType` `CustomerBaseType` 。</span><span class="sxs-lookup"><span data-stu-id="31f1c-183">The schema also specifies a **\<Customer>** element of type `CustomerType`, which is derived from `CustomerBaseType`.</span></span> <span data-ttu-id="31f1c-184">在这样的架构上指定的 XPath 查询将生成错误，因为在 restriction 基类型中定义的元素不支持 `sql:max-depth`。</span><span class="sxs-lookup"><span data-stu-id="31f1c-184">An XPath query specified on such a schema will generate an error, because `sql:max-depth` is not supported on an element that is defined in a restriction base type.</span></span>  
  
## <a name="schemas-with-a-deep-hierarchy"></a><span data-ttu-id="31f1c-185">具有深层次结构的架构</span><span class="sxs-lookup"><span data-stu-id="31f1c-185">Schemas with a Deep Hierarchy</span></span>  
 <span data-ttu-id="31f1c-186">您可能有一个包含深层次结构的架构，在该层次结构中，元素包含子元素，而该子元素又包含另一个子元素，以此类推。</span><span class="sxs-lookup"><span data-stu-id="31f1c-186">You might have a schema that includes a deep hierarchy in which an element contains a child element, which in turn contains another child element, and so on.</span></span> <span data-ttu-id="31f1c-187">如果在这样的架构中指定的 `sql:max-depth` 批注生成了一个 XML 文档，并且该文档中包括一个超过 500 级（顶级元素在第 1 级，其子元素在第 2 级，以此类推）的层次结构，则会返回错误。</span><span class="sxs-lookup"><span data-stu-id="31f1c-187">If the `sql:max-depth` annotation specified in such a schema generates an XML document that includes a hierarchy of more than 500 levels (with top-level element at level 1, its child at level 2, and so on), an error is returned.</span></span>  
  
  
