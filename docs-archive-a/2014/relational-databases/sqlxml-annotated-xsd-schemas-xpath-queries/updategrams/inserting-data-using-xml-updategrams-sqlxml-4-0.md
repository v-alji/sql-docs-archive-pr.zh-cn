---
title: 使用 XML Updategram 插入数据 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- xsi:nil attribute
- unique values
- <after> block
- id attribute
- data insertions [SQLXML]
- nil attribute
- <before> block
- updg:guid attribute
- multiple record insertions
- returnid attribute
- updategrams [SQLXML], inserting data
- updg:at-identity attribute
- invalid characters [SQLXML]
- updg:returnid attribute
- updg:id attribute
- namespaces [SQLXML], updategrams
- IDENTITY-type column
- guid attribute
- record insertion [SQLXML]
- null values [SQLXML]
- at-identity attribute
- xml data type [SQL Server], SQLXML
ms.assetid: 4dc48762-bc12-43fb-b356-ea1b9c1e287e
author: rothja
ms.author: jroth
ms.openlocfilehash: a80f2cb157e59f30ebcbff5c14abba1003de9e40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689798"
---
# <a name="inserting-data-using-xml-updategrams-sqlxml-40"></a><span data-ttu-id="b2332-102">使用 XML updategram 插入数据 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="b2332-102">Inserting Data Using XML Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="b2332-103">当记录实例出现在 **\<after>** 块中但不在对应的块中时，updategram 指示插入操作 **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="b2332-103">An updategram indicates an insert operation when a record instance appears in the **\<after>** block but not in the corresponding **\<before>** block.</span></span> <span data-ttu-id="b2332-104">在这种情况下，updategram 将块中的记录插入 **\<after>** 到数据库中。</span><span class="sxs-lookup"><span data-stu-id="b2332-104">In this case, the updategram inserts the record in the **\<after>** block into the database.</span></span>  
  
 <span data-ttu-id="b2332-105">以下是 updategram 的插入操作格式：</span><span class="sxs-lookup"><span data-stu-id="b2332-105">This is the updategram format for an insert operation:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema="SampleSchema.xml"]  >  
   [<updg:before>  
   </updg:before>]  
    <updg:after [updg:returnid="x y ...] >  
       <ElementName [updg:id="value"]   
                   [updg:at-identity="x"]   
                   [updg:guid="y"]  
                   attribute="value"   
                   attribute="value"  
                   ...  
       />  
      [<ElementName .../>... ]  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
## <a name="before-block"></a><span data-ttu-id="b2332-106">\<before>模块</span><span class="sxs-lookup"><span data-stu-id="b2332-106">\<before> Block</span></span>  
 <span data-ttu-id="b2332-107">**\<before>** 对于插入操作，可以省略块。</span><span class="sxs-lookup"><span data-stu-id="b2332-107">The **\<before>** block can be omitted for an insert operation.</span></span> <span data-ttu-id="b2332-108">如果 `mapping-schema` 未指定可选属性，则 **\<ElementName>** 在 updategram 中指定的将映射到数据库表，并且子元素或属性将映射到表中的列。</span><span class="sxs-lookup"><span data-stu-id="b2332-108">If the optional `mapping-schema` attribute is not specified, the **\<ElementName>** that is specified in the updategram maps to a database table and the child elements or attributes map to columns in the table.</span></span>  
  
## <a name="after-block"></a><span data-ttu-id="b2332-109">\<after>模块</span><span class="sxs-lookup"><span data-stu-id="b2332-109">\<after> Block</span></span>  
 <span data-ttu-id="b2332-110">可以在块中指定一个或多个记录 **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="b2332-110">You can specify one or more records in the **\<after>** block.</span></span>  
  
 <span data-ttu-id="b2332-111">如果 **\<after>** 块没有为特定列提供值，则 updategram 将使用批注架构 (中指定的默认值（如果) 指定了架构）。</span><span class="sxs-lookup"><span data-stu-id="b2332-111">If the **\<after>** block does not supply a value for a particular column, the updategram uses the default value that is specified in the annotated schema (if a schema has been specified).</span></span> <span data-ttu-id="b2332-112">如果架构未指定列的默认值，则 updategram 不会为此列指定任何显式值，而是会将 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认值指定 (如果) 指定此列。</span><span class="sxs-lookup"><span data-stu-id="b2332-112">If the schema does not specify a default value for the column, the updategram does not specify any explicit value to this column and, instead, assigns the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] default value (if specified) to this column.</span></span> <span data-ttu-id="b2332-113">如果没有 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 默认值并且此列接受 NULL 值，则 updategram 将此列的值设置为 NULL。</span><span class="sxs-lookup"><span data-stu-id="b2332-113">If there is no [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] default value and the column accepts a NULL value, the updategram sets the column value to NULL.</span></span> <span data-ttu-id="b2332-114">如果此列既没有默认值也不接受 NULL 值，则命令将失败并且 updategram 将返回一个错误。</span><span class="sxs-lookup"><span data-stu-id="b2332-114">If the column neither has a default value nor accepts a NULL value, the command fails and the updategram returns an error.</span></span> <span data-ttu-id="b2332-115">如果要添加记录的表包含一个 IDENTITY 类型的列，则使用 `updg:returnid` 属性返回系统生成的标识值。</span><span class="sxs-lookup"><span data-stu-id="b2332-115">The optional `updg:returnid` attribute is used to return the identity value that is generated by the system when a record is added in a table with an IDENTITY-type column.</span></span>  
  
## <a name="updgid-attribute"></a><span data-ttu-id="b2332-116">updg:id 属性</span><span class="sxs-lookup"><span data-stu-id="b2332-116">updg:id Attribute</span></span>  
 <span data-ttu-id="b2332-117">如果 updategram 只是要插入记录，则 updategram 不需要 `updg:id` 属性。</span><span class="sxs-lookup"><span data-stu-id="b2332-117">If the updategram is inserting only records, the updategram does not require the `updg:id` attribute.</span></span> <span data-ttu-id="b2332-118">有关的详细信息 `updg:id` ，请参阅[使用 XML Updategram 更新数据 &#40;SQLXML 4.0&#41;](updating-data-using-xml-updategrams-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="b2332-118">For more information about `updg:id`, see [Updating Data Using XML Updategrams &#40;SQLXML 4.0&#41;](updating-data-using-xml-updategrams-sqlxml-4-0.md).</span></span>  
  
## <a name="updgat-identity-attribute"></a><span data-ttu-id="b2332-119">updg:at-identity 属性</span><span class="sxs-lookup"><span data-stu-id="b2332-119">updg:at-identity Attribute</span></span>  
 <span data-ttu-id="b2332-120">如果 updategram 要在其中插入记录的表包含一个 IDENTITY 类型的列，则 updategram 可通过使用可选的 `updg:at-identity` 属性捕获系统分配的值。</span><span class="sxs-lookup"><span data-stu-id="b2332-120">When an updategram inserts a record in a table that has an IDENTITY-type column, the updategram can capture the system assigned value by using the optional `updg:at-identity` attribute.</span></span> <span data-ttu-id="b2332-121">然后，updategram 可以在后续操作中使用此值。</span><span class="sxs-lookup"><span data-stu-id="b2332-121">The updategram can then use this value in subsequent operations.</span></span> <span data-ttu-id="b2332-122">一旦执行 updategram，即可通过指定 `updg:returnid` 属性返回生成的标识值。</span><span class="sxs-lookup"><span data-stu-id="b2332-122">Upon execution of the updategram, you can return the identity value that is generated by specifying the `updg:returnid` attribute.</span></span>  
  
## <a name="updgguid-attribute"></a><span data-ttu-id="b2332-123">updg:guid 属性</span><span class="sxs-lookup"><span data-stu-id="b2332-123">updg:guid Attribute</span></span>  
 <span data-ttu-id="b2332-124">`updg:guid` 属性是一个生成全局唯一标识符的可选属性。</span><span class="sxs-lookup"><span data-stu-id="b2332-124">The `updg:guid` attribute is an optional attribute that generates a globally unique identifier.</span></span> <span data-ttu-id="b2332-125">此值保留在指定它的整个块的作用域中 **\<sync>** 。</span><span class="sxs-lookup"><span data-stu-id="b2332-125">This value remains in scope for the entire **\<sync>** block in which it is specified.</span></span> <span data-ttu-id="b2332-126">可以在块中的任何位置使用此值 **\<sync>** 。</span><span class="sxs-lookup"><span data-stu-id="b2332-126">You can use this value anywhere in the **\<sync>** block.</span></span> <span data-ttu-id="b2332-127">特性调用 `NEWGUID()` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 函数以生成唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="b2332-127">The attribute calls the `NEWGUID()`[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] function to generate the unique identifier.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b2332-128">示例</span><span class="sxs-lookup"><span data-stu-id="b2332-128">Examples</span></span>  
 <span data-ttu-id="b2332-129">若要创建使用以下示例的工作示例，必须满足[运行 SQLXML 示例的要求](../../sqlxml/requirements-for-running-sqlxml-examples.md)中指定的要求。</span><span class="sxs-lookup"><span data-stu-id="b2332-129">To create working samples using the following examples, you must meet the requirements specified in [Requirements for Running SQLXML Examples](../../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
 <span data-ttu-id="b2332-130">在使用 updategram 示例前，请注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="b2332-130">Before using the updategram examples, note the following:</span></span>  
  
-   <span data-ttu-id="b2332-131">大多数示例使用默认映射（即，未在 updategram 中指定任何映射架构）。</span><span class="sxs-lookup"><span data-stu-id="b2332-131">Most of the examples use default mapping (that is, no mapping schema is specified in the updategram).</span></span> <span data-ttu-id="b2332-132">有关使用映射架构的 updategram 的更多示例，请参阅[在 Updategram &#40;SQLXML 4.0&#41;中指定带批注的映射架构](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="b2332-132">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="b2332-133">大多数示例使用 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="b2332-133">Most of the examples use the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="b2332-134">已对该数据库中的表应用所有更新。</span><span class="sxs-lookup"><span data-stu-id="b2332-134">All the updates are applied to the tables in this database.</span></span>  
  
### <a name="a-inserting-a-record-by-using-an-updategram"></a><span data-ttu-id="b2332-135">A.</span><span class="sxs-lookup"><span data-stu-id="b2332-135">A.</span></span> <span data-ttu-id="b2332-136">使用 updategram 插入记录</span><span class="sxs-lookup"><span data-stu-id="b2332-136">Inserting a record by using an updategram</span></span>  
 <span data-ttu-id="b2332-137">这个以属性为中心的 updategram 在 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 数据库的 HumanResources.Employee 表中插入一条记录。</span><span class="sxs-lookup"><span data-stu-id="b2332-137">This attribute-centric updategram inserts a record in the HumanResources.Employee table in the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database.</span></span>  
  
 <span data-ttu-id="b2332-138">在此示例中，updategram 没有指定映射架构。</span><span class="sxs-lookup"><span data-stu-id="b2332-138">In this example, the updategram does not specify a mapping schema.</span></span> <span data-ttu-id="b2332-139">因此，updategram 使用默认映射，在默认映射中，元素名称映射到表名，而属性或子元素则映射到该表中的列。</span><span class="sxs-lookup"><span data-stu-id="b2332-139">Therefore, the updategram uses default mapping, in which the element name maps to a table name and the attributes or child elements map to columns in that table.</span></span>  
  
 <span data-ttu-id="b2332-140">HumanResources.Department 表的 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 架构对所有列施加了“not null”限制。</span><span class="sxs-lookup"><span data-stu-id="b2332-140">The [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] schema for the HumanResources.Department table imposes a 'not null' restriction on all columns.</span></span> <span data-ttu-id="b2332-141">所以，updategram 必须包括为所有列指定的值。</span><span class="sxs-lookup"><span data-stu-id="b2332-141">Therefore, the updategram must include values specified for all columns.</span></span> <span data-ttu-id="b2332-142">DepartmentID 是一个 IDENTITY 类型的列。</span><span class="sxs-lookup"><span data-stu-id="b2332-142">The DepartmentID is an IDENTITY-type column.</span></span> <span data-ttu-id="b2332-143">因此，没有为其指定任何值。</span><span class="sxs-lookup"><span data-stu-id="b2332-143">Therefore, no values are specified for it.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department   
            Name="New Product Research"   
            GroupName="Research and Development"   
            ModifiedDate="2010-08-31"/>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="b2332-144">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="b2332-144">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="b2332-145">复制上面的 updategram，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="b2332-145">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="b2332-146">将文件另存为 MyUpdategram.xml。</span><span class="sxs-lookup"><span data-stu-id="b2332-146">Save the file as MyUpdategram.xml.</span></span>  
  
2.  <span data-ttu-id="b2332-147">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="b2332-147">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="b2332-148">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="b2332-148">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="b2332-149">在以元素为中心的映射中，updategram 如下所示：</span><span class="sxs-lookup"><span data-stu-id="b2332-149">In an element-centric mapping, the updategram looks like this:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department>  
            <Name> New Product Research </Name>  
            <GroupName> Research and Development </GroupName>  
            <ModifiedDate>2010-08-31</ModifiedDate>  
       </HumanResources.Department>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="b2332-150">在混合模式（以元素为中心和以属性为中心）的 updategram 中，元素可以同时具有属性和子元素，如以下 updategram 所示：</span><span class="sxs-lookup"><span data-stu-id="b2332-150">In a mixed-mode (element-centric and attribute-centric) updategram, an element can have both attributes and subelements, as shown in this updategram:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department   
            Name=" New Product Research "   
            <GroupName>Research and Development</GroupName>  
            <ModifiedDate>2010-08-31</ModifiedDate>  
       </HumanResources.Department>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
### <a name="b-inserting-multiple-records-by-using-an-updategram"></a><span data-ttu-id="b2332-151">B.</span><span class="sxs-lookup"><span data-stu-id="b2332-151">B.</span></span> <span data-ttu-id="b2332-152">使用 updategram 插入多个记录</span><span class="sxs-lookup"><span data-stu-id="b2332-152">Inserting multiple records by using an updategram</span></span>  
 <span data-ttu-id="b2332-153">此 updategram 向 HumanResources.Shift 表添加两个新的轮班记录。</span><span class="sxs-lookup"><span data-stu-id="b2332-153">This updategram adds two new shift records to the HumanResources.Shift table.</span></span> <span data-ttu-id="b2332-154">Updategram 不指定可选的 **\<before>** 块。</span><span class="sxs-lookup"><span data-stu-id="b2332-154">The updategram does not specify the optional **\<before>** block.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync>  
    <updg:after >  
       <HumanResources.Shift Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="b2332-155">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="b2332-155">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="b2332-156">复制上面的 updategram，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="b2332-156">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="b2332-157">将文件另存为 Updategram-AddShifts.xml。</span><span class="sxs-lookup"><span data-stu-id="b2332-157">Save the file as Updategram-AddShifts.xml.</span></span>  
  
2.  <span data-ttu-id="b2332-158">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="b2332-158">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="b2332-159">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="b2332-159">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="b2332-160">此示例的另一个版本是 updategram，它使用两个单独的 **\<after>** 块而不是一个块来插入两个雇员。</span><span class="sxs-lookup"><span data-stu-id="b2332-160">Another version of this example is an updategram that uses two separate **\<after>** blocks instead of one block to insert the two employees.</span></span> <span data-ttu-id="b2332-161">这种做法是有效的，并且可以按照如下形式进行编码：</span><span class="sxs-lookup"><span data-stu-id="b2332-161">This is valid and can be encoded as follows:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync>  
    <updg:after >  
       <HumanResources.Shift Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
    <updg:before>  
    </updg:before>  
    <updg:after >  
       <HumanResources.Shift Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
### <a name="c-working-with-valid-sql-server-characters-that-are-not-valid-in-xml"></a><span data-ttu-id="b2332-162">C.</span><span class="sxs-lookup"><span data-stu-id="b2332-162">C.</span></span> <span data-ttu-id="b2332-163">使用在 XML 中无效的有效 SQL Server 字符</span><span class="sxs-lookup"><span data-stu-id="b2332-163">Working with valid SQL Server characters that are not valid in XML</span></span>  
 <span data-ttu-id="b2332-164">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，表名可以包括空格，例如 Northwind 数据库中的 Order Details 表。</span><span class="sxs-lookup"><span data-stu-id="b2332-164">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], table names can include a space, such as the Order Details table in the Northwind database.</span></span> <span data-ttu-id="b2332-165">但是，这在作为有效标识符的 XML 字符中无效， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 但不能使用 "__xHHHH" 作为编码值对有效的 xml 标识符进行编码 \_ \_ ，其中 HHHH 代表最高有效位第一次的字符的四位十六进制 UCS-2 代码。</span><span class="sxs-lookup"><span data-stu-id="b2332-165">However, this is not valid in XML characters that are valid [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identifiers but not valid XML identifiers can be encoded using '__xHHHH\_\_' as the encoding value, where HHHH stands for the four-digit hexadecimal UCS-2 code for the character in the most significant bit-first order.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b2332-166">此示例使用 Northwind 数据库。</span><span class="sxs-lookup"><span data-stu-id="b2332-166">This example uses the Northwind database.</span></span> <span data-ttu-id="b2332-167">可以通过使用可从[Microsoft 网站](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)下载的 SQL 脚本来安装 Northwind 数据库。</span><span class="sxs-lookup"><span data-stu-id="b2332-167">You can install the Northwind database by using an SQL script available for download from this [Microsoft Web site](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>  
  
 <span data-ttu-id="b2332-168">此外，元素名必须括在方括号 ([ ]) 内。</span><span class="sxs-lookup"><span data-stu-id="b2332-168">Also, the element name must be enclosed within brackets ([ ]).</span></span> <span data-ttu-id="b2332-169">因为字符 [and] 在 XML 中无效，所以必须分别将它们编码为 _x005B \_ 和 _x005D \_ 。</span><span class="sxs-lookup"><span data-stu-id="b2332-169">Because the characters [and] are not valid in XML, you must encode them as _x005B\_ and _x005D\_, respectively.</span></span> <span data-ttu-id="b2332-170">（如果使用映射架构，可以提供不包含无效字符（如空格）的元素名。</span><span class="sxs-lookup"><span data-stu-id="b2332-170">(If you use a mapping schema, you can provide element names that do not contain characters that are not valid, such as white spaces.</span></span> <span data-ttu-id="b2332-171">映射架构会执行必要的映射；因此，无需对这些字符进行编码。）</span><span class="sxs-lookup"><span data-stu-id="b2332-171">The mapping schema does the necessary mapping; therefore, you do not need to encode for these characters).</span></span>  
  
 <span data-ttu-id="b2332-172">此 updategram 向 Northwind 数据库中的 Order Details 表添加一条记录：</span><span class="sxs-lookup"><span data-stu-id="b2332-172">This updategram adds a record to the Order Details table in the Northwind database:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
      <_x005B_Order_x0020_Details_x005D_ OrderID="1"  
            ProductID="11"  
            UnitPrice="$1.0"  
            Quantity="1"  
            Discount="0.0" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="b2332-173">Order Details 表中的 UnitPrice 列的类型为 `money`。</span><span class="sxs-lookup"><span data-stu-id="b2332-173">The UnitPrice column in the Order Details table is of the `money` type.</span></span> <span data-ttu-id="b2332-174">若要应用适当的类型转换（从 `string` 类型到 `money` 类型），必须将美元符号 ($) 添加为该值的一部分。</span><span class="sxs-lookup"><span data-stu-id="b2332-174">To apply the appropriate type conversion (from a `string` type to a `money` type), the dollar sign character ($) must be added as part of the value.</span></span> <span data-ttu-id="b2332-175">如果 updategram 未指定映射架构，将对 `string` 值的第一个字符进行计算。</span><span class="sxs-lookup"><span data-stu-id="b2332-175">If the updategram does not specify a mapping schema, the first character of the `string` value is evaluated.</span></span> <span data-ttu-id="b2332-176">如果第一个字符为美元符号 ($)，则会应用适当的转换。</span><span class="sxs-lookup"><span data-stu-id="b2332-176">If the first character is a dollar sign ($), the appropriate conversion is applied.</span></span>  
  
 <span data-ttu-id="b2332-177">如果是针对某个映射架构指定 updategram，并且在架构中该列相应地标记为 `dt:type="fixed.14.4"` 或 `sql:datatype="money"`，则不需要美元符号 ($) 映射就会处理转换。</span><span class="sxs-lookup"><span data-stu-id="b2332-177">If the updategram is specified against a mapping schema where the column is appropriately marked as either `dt:type="fixed.14.4"` or `sql:datatype="money"`, the dollar sign ($) is not required and the conversion is handled by the mapping.</span></span> <span data-ttu-id="b2332-178">建议采用这种方式以确保能够进行适当的类型转换。</span><span class="sxs-lookup"><span data-stu-id="b2332-178">This is the recommended way to ensure that the appropriate type conversion occurs.</span></span>  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="b2332-179">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="b2332-179">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="b2332-180">复制上面的 updategram，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="b2332-180">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="b2332-181">将文件另存为 UpdategramSpacesInTableName.xml。</span><span class="sxs-lookup"><span data-stu-id="b2332-181">Save the file as UpdategramSpacesInTableName.xml.</span></span>  
  
2.  <span data-ttu-id="b2332-182">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="b2332-182">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="b2332-183">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="b2332-183">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="d-using-the-at-identity-attribute-to-retrieve-the-value-that-has-been-inserted-in-the-identity-type-column"></a><span data-ttu-id="b2332-184">D.</span><span class="sxs-lookup"><span data-stu-id="b2332-184">D.</span></span> <span data-ttu-id="b2332-185">使用 at-identity 属性检索已在 IDENTITY 类型的列中插入的值</span><span class="sxs-lookup"><span data-stu-id="b2332-185">Using the at-identity attribute to retrieve the value that has been inserted in the IDENTITY-type column</span></span>  
 <span data-ttu-id="b2332-186">以下 updategram 插入两条记录：在 Sales.SalesOrderHeader 表中插入一条记录而在 Sales.SalesOrderDetail 表中插入另一条记录。</span><span class="sxs-lookup"><span data-stu-id="b2332-186">The following updategram inserts two records: one in the Sales.SalesOrderHeader table and another in the Sales.SalesOrderDetail table.</span></span>  
  
 <span data-ttu-id="b2332-187">首先，updategram 向 Sales.SalesOrderHeader 表中添加一条记录。</span><span class="sxs-lookup"><span data-stu-id="b2332-187">First, the updategram adds a record to the Sales.SalesOrderHeader table.</span></span> <span data-ttu-id="b2332-188">在该表中，SalesOrderID 列为 IDENTITY 类型的列。</span><span class="sxs-lookup"><span data-stu-id="b2332-188">In this table, the SalesOrderID column is an IDENTITY-type column.</span></span> <span data-ttu-id="b2332-189">因此，在向该表添加此记录时，updategram 使用 `at-identity` 属性将已赋值的 SalesOrderID 值捕获为“x”（占位符值）。</span><span class="sxs-lookup"><span data-stu-id="b2332-189">Therefore, when you add this record to the table, the updategram uses the `at-identity` attribute to capture the assigned SalesOrderID value as "x" (a placeholder value).</span></span> <span data-ttu-id="b2332-190">然后，updategam 将此 `at-identity` 变量指定为元素中 SalesOrderID 属性的值 \<Sales.SalesOrderDetail> 。</span><span class="sxs-lookup"><span data-stu-id="b2332-190">The updategam then specifies this `at-identity` variable as the value of SalesOrderID attribute in the \<Sales.SalesOrderDetail> element.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
 <updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
   <Sales.SalesOrderHeader updg:at-identity="x"   
             RevisionNumber="1"  
             OrderDate="2001-07-01 00:00:00.000"  
             DueDate="2001-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             CustomerID="676"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="00001111-2222-3333-4444-556677889900"  
             ModifiedDate="2001-07-08 00:00:00.000" />  
      <Sales.SalesOrderDetail SalesOrderID="x"  
                LineNumber="1"  
                OrderQty="1"  
                ProductID="776"  
                SpecialOfferID="1"  
                UnitPrice="2429.9928"  
                UnitPriceDiscount="0.00"  
                rowguid="aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee"  
                ModifiedDate="2001-07-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="b2332-191">如果要返回 `updg:at-identity` 属性生成的标识值，可以使用 `updg:returnid` 属性。</span><span class="sxs-lookup"><span data-stu-id="b2332-191">If you want to return the identity value that is generated by the `updg:at-identity` attribute, you can use the `updg:returnid` attribute.</span></span> <span data-ttu-id="b2332-192">以下是经过修改的返回此标识值的 updategram。</span><span class="sxs-lookup"><span data-stu-id="b2332-192">The following is a revised updategram that returns this identity value.</span></span> <span data-ttu-id="b2332-193">（此 updategram 添加两条订单记录和两条订单详细信息记录，目的在于让示例变得稍微复杂一点。）</span><span class="sxs-lookup"><span data-stu-id="b2332-193">(This updategram adds two order records and two order detail records, just to make the example a little more complex.)</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
 <updg:sync>  
  <updg:before>  
  </updg:before>  
  <updg:after updg:returnid="x y" >  
       <HumanResources.Shift updg:at-identity="x" Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift updg:at-identity="y" Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
  </updg:after>  
 </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="b2332-194">在执行 updategram 时，它会返回类似于如下的结果，包括生成的标识值（用于表标识的 ShiftID 列的生成值）：</span><span class="sxs-lookup"><span data-stu-id="b2332-194">When the updategram is executed, it returns results similar to the following, which includes the identity value (the generated value of the ShiftID column used for table identity) that was generated:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">   
  <returnid>   
    <x>4</x>   
    <y>5</y>   
  </returnid>   
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="b2332-195">针对架构测试示例 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="b2332-195">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="b2332-196">复制上面的 updategram，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="b2332-196">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="b2332-197">将文件另存为 Updategram-returnId.xml。</span><span class="sxs-lookup"><span data-stu-id="b2332-197">Save the file as Updategram-returnId.xml.</span></span>  
  
2.  <span data-ttu-id="b2332-198">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="b2332-198">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="b2332-199">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="b2332-199">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="e-using-the-updgguid-attribute-to-generate-a-unique-value"></a><span data-ttu-id="b2332-200">E.</span><span class="sxs-lookup"><span data-stu-id="b2332-200">E.</span></span> <span data-ttu-id="b2332-201">使用 updg:guid 属性生成唯一值</span><span class="sxs-lookup"><span data-stu-id="b2332-201">Using the updg:guid attribute to generate a unique value</span></span>  
 <span data-ttu-id="b2332-202">在本示例中，updategram 在 Cust 和 CustOrder 表中插入一条新记录。</span><span class="sxs-lookup"><span data-stu-id="b2332-202">In this example, the updategram inserts a record in the Cust and CustOrder tables.</span></span> <span data-ttu-id="b2332-203">此外，updategram 还使用 `updg:guid` 属性，为 CustomerID 属性生成唯一的值。</span><span class="sxs-lookup"><span data-stu-id="b2332-203">Also, the updategram generates a unique value for the CustomerID attribute by using the `updg:guid` attribute.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after updg:returnid="x" >  
      <Cust updg:guid="x" >  
         <CustID>x</CustID>  
         <LastName>Fuller</LastName>  
      </Cust>  
      <CustOrder>  
         <CustID>x</CustID>  
         <OrderID>1</OrderID>  
      </CustOrder>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="b2332-204">updategram 指定 `returnid` 属性。</span><span class="sxs-lookup"><span data-stu-id="b2332-204">The updategram specifies the `returnid` attribute.</span></span> <span data-ttu-id="b2332-205">生成的 GUID 作为结果返回：</span><span class="sxs-lookup"><span data-stu-id="b2332-205">As a result, the GUID that is generated is returned:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <returnid>  
    <x>7111BD1A-7F0B-4CEE-B411-260DADFEFA2A</x>   
  </returnid>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="b2332-206">测试 updategram</span><span class="sxs-lookup"><span data-stu-id="b2332-206">To test the updategram</span></span>  
  
1.  <span data-ttu-id="b2332-207">复制上面的 updategram，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="b2332-207">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="b2332-208">将文件另存为 Updategram-GenerateGuid.xml。</span><span class="sxs-lookup"><span data-stu-id="b2332-208">Save the file as Updategram-GenerateGuid.xml.</span></span>  
  
2.  <span data-ttu-id="b2332-209">创建以下表：</span><span class="sxs-lookup"><span data-stu-id="b2332-209">Create these tables:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust (CustID uniqueidentifier, LastName varchar(20))  
    CREATE TABLE CustOrder (CustID uniqueidentifier, OrderID int)  
    ```  
  
3.  <span data-ttu-id="b2332-210">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="b2332-210">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="b2332-211">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="b2332-211">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="f-specifying-a-schema-in-an-updategram"></a><span data-ttu-id="b2332-212">F.</span><span class="sxs-lookup"><span data-stu-id="b2332-212">F.</span></span> <span data-ttu-id="b2332-213">在 updategram 中指定架构</span><span class="sxs-lookup"><span data-stu-id="b2332-213">Specifying a schema in an updategram</span></span>  
 <span data-ttu-id="b2332-214">在此示例中，updategram 在以下表中插入一条记录：</span><span class="sxs-lookup"><span data-stu-id="b2332-214">The updategram in this example inserts a record into the following table:</span></span>  
  
```  
CustOrder(OrderID, EmployeeID, OrderType)  
```  
  
 <span data-ttu-id="b2332-215">在此 updategram 中指定了一个 XSD 架构（即，updategram 元素和属性不存在任何默认映射）。</span><span class="sxs-lookup"><span data-stu-id="b2332-215">An XSD schema is specified in this updategram (that is, there is no default mapping of updategram elements and attributes).</span></span> <span data-ttu-id="b2332-216">架构提供了元素和属性与数据库表和列之间的必要映射。</span><span class="sxs-lookup"><span data-stu-id="b2332-216">The schema provides the necessary mapping of the elements and attributes to the database tables and columns.</span></span>  
  
 <span data-ttu-id="b2332-217">以下架构 ( # A0) 描述 **\<CustOrder>** 包含**订单 Id**和**雇员 id**属性的元素。</span><span class="sxs-lookup"><span data-stu-id="b2332-217">The following schema (CustOrderSchema.xml) describes a **\<CustOrder>** element that consists of the **OrderID** and **EmployeeID** attributes.</span></span> <span data-ttu-id="b2332-218">为了使该架构更有趣，将为 "**雇员 id** " 属性分配一个默认值。</span><span class="sxs-lookup"><span data-stu-id="b2332-218">To make the schema more interesting, a default value is assigned to the **EmployeeID** attribute.</span></span> <span data-ttu-id="b2332-219">updategram 仅在执行插入操作以及仅在没有指定该属性时才使用属性的默认值。</span><span class="sxs-lookup"><span data-stu-id="b2332-219">An updategram uses an attribute's default value only for insert operations, and then only if the updategram does not specify that attribute.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="CustOrder" >  
   <xsd:complexType>  
        <xsd:attribute name="OrderID"     type="xsd:integer" />   
        <xsd:attribute name="EmployeeID"  type="xsd:integer" />  
        <xsd:attribute name="OrderType  " type="xsd:integer" default="1"/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="b2332-220">此 updategram 在 CustOrder 表中插入一条记录。</span><span class="sxs-lookup"><span data-stu-id="b2332-220">This updategram inserts a record into the CustOrder table.</span></span> <span data-ttu-id="b2332-221">updategram 仅指定了 OrderID 和 EmployeeID 属性值。</span><span class="sxs-lookup"><span data-stu-id="b2332-221">The updategram specifies only the OrderID and EmployeeID attribute values.</span></span> <span data-ttu-id="b2332-222">它未指定 OrderType 属性值。</span><span class="sxs-lookup"><span data-stu-id="b2332-222">It does not specify the OrderType attribute value.</span></span> <span data-ttu-id="b2332-223">因此，updategram 使用在前面的架构中指定的 EmployeeID 属性的默认值。</span><span class="sxs-lookup"><span data-stu-id="b2332-223">Therefore, the updategram uses the default value of the EmployeeID attribute that is specified in the preceding schema.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"  
             xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync mapping-schema='CustOrderSchema.xml'>  
<updg:after>  
       <CustOrder OrderID="98000" EmployeeID="1" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="b2332-224">有关指定映射架构的 updategram 的更多示例，请参阅[在 Updategram &#40;SQLXML 4.0&#41;中指定带批注的映射架构](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="b2332-224">For more examples of updategrams that specify a mapping schema, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="b2332-225">测试 updategram</span><span class="sxs-lookup"><span data-stu-id="b2332-225">To test the updategram</span></span>  
  
1.  <span data-ttu-id="b2332-226">在**tempdb**数据库中创建此表：</span><span class="sxs-lookup"><span data-stu-id="b2332-226">Create this table in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE CustOrder(  
                     OrderID int,   
                     EmployeeID int,   
                     OrderType int)  
    ```  
  
2.  <span data-ttu-id="b2332-227">复制上面的架构，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="b2332-227">Copy the schema above and paste it into a text file.</span></span> <span data-ttu-id="b2332-228">将文件另存为 CustOrderSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="b2332-228">Save the file as CustOrderSchema.xml.</span></span>  
  
3.  <span data-ttu-id="b2332-229">复制上面的 updategram，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="b2332-229">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="b2332-230">在与上一步骤中所使用文件夹相同的文件夹中将文件另存为 CustOrderUpdategram.xml。</span><span class="sxs-lookup"><span data-stu-id="b2332-230">Save the file as CustOrderUpdategram.xml in the same folder used in the previous step.</span></span>  
  
4.  <span data-ttu-id="b2332-231">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 以执行 updategram。</span><span class="sxs-lookup"><span data-stu-id="b2332-231">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="b2332-232">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="b2332-232">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="b2332-233">这是等效的 XDR 架构：</span><span class="sxs-lookup"><span data-stu-id="b2332-233">This is the equivalent XDR schema:</span></span>  
  
```  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
 <ElementType name="CustOrder" >  
    <AttributeType name="OrderID" />  
    <AttributeType name="EmployeeID" />  
    <AttributeType name="OrderType" default="1" />  
    <attribute type="OrderID"  />  
    <attribute type="EmployeeID" />  
    <attribute type="OrderType" />  
  </ElementType>  
</Schema>  
```  
  
### <a name="g-using-the-xsinil-attribute-to-insert-null-values-in-a-column"></a><span data-ttu-id="b2332-234">G.</span><span class="sxs-lookup"><span data-stu-id="b2332-234">G.</span></span> <span data-ttu-id="b2332-235">使用 xsi:nil 属性在列中插入 null 值</span><span class="sxs-lookup"><span data-stu-id="b2332-235">Using the xsi:nil attribute to insert null values in a column</span></span>  
 <span data-ttu-id="b2332-236">如果要在表的对应列中插入 null 值，可以在 updategram 中指定元素的 `xsi:nil` 属性。</span><span class="sxs-lookup"><span data-stu-id="b2332-236">If you want to insert a null value in the corresponding column in the table, you can specify the `xsi:nil` attribute on an element in an updategram.</span></span> <span data-ttu-id="b2332-237">在对应的 XSD 架构中，还必须指定 XSD `nillable` 属性。</span><span class="sxs-lookup"><span data-stu-id="b2332-237">In the corresponding XSD schema, the XSD `nillable` attribute also must be specified.</span></span>  
  
 <span data-ttu-id="b2332-238">例如，请看此 XSD 架构：</span><span class="sxs-lookup"><span data-stu-id="b2332-238">For example, consider this XSD schema:</span></span>  
  
```  
<?xml version="1.0"?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:element name="Student" sql:relation="Students">  
  <xsd:complexType>  
    <xsd:all>  
      <xsd:element name="fname" sql:field="first_name"   
                                type="xsd:string"   
                                 nillable="true"/>  
    </xsd:all>  
    <xsd:attribute name="SID"   
                        sql:field="StudentID"  
                        type="xsd:ID"/>      
    <xsd:attribute name="lname"       
                        sql:field="last_name"  
                        type="xsd:string"/>  
    <xsd:attribute name="minitial"    
                        sql:field="middle_initial"   
                        type="xsd:string"/>  
    <xsd:attribute name="years"       
                         sql:field="no_of_years"  
                         type="xsd:integer"/>  
  </xsd:complexType>  
 </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="b2332-239">XSD 架构为元素指定**nillable = "true"** **\<fname>** 。</span><span class="sxs-lookup"><span data-stu-id="b2332-239">The XSD schema specifies **nillable="true"** for the **\<fname>** element.</span></span> <span data-ttu-id="b2332-240">以下 updategram 使用此架构：</span><span class="sxs-lookup"><span data-stu-id="b2332-240">The following updategram uses this schema:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"  
      xmlns:updg="urn:schemas-microsoft-com:xml-updategram"  
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  
<updg:sync mapping-schema='StudentSchema.xml'>  
  <updg:before/>  
  <updg:after>  
    <Student SID="S00004" lname="Elmaci" minitial="" years="2">  
      <fname xsi:nil="true">  
    </fname>  
    </Student>  
  </updg:after>  
</updg:sync>  
  
</ROOT>  
```  
  
 <span data-ttu-id="b2332-241">Updategram `xsi:nil` 为 **\<fname>** 块中的元素指定 **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="b2332-241">The updategram specifies `xsi:nil` for the **\<fname>** element in the **\<after>** block.</span></span> <span data-ttu-id="b2332-242">因此，在执行此 updategram 时，会为表中的 first_name 列插入 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="b2332-242">Therefore, when this updategram is executed, a value of NULL is inserted for the first_name column in the table.</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="b2332-243">测试 updategram</span><span class="sxs-lookup"><span data-stu-id="b2332-243">To test the updategram</span></span>  
  
1.  <span data-ttu-id="b2332-244">在**tempdb**数据库中创建以下表：</span><span class="sxs-lookup"><span data-stu-id="b2332-244">Create the following table in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Students (  
       StudentID char(6)NOT NULL ,  
       first_name varchar(50),  
       last_name varchar(50),  
       middle_initial char(1),  
       no_of_years int NULL)  
    GO  
    ```  
  
2.  <span data-ttu-id="b2332-245">复制上面的架构，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="b2332-245">Copy the schema above and paste it into a text file.</span></span> <span data-ttu-id="b2332-246">将文件另存为 StudentSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="b2332-246">Save the file as StudentSchema.xml.</span></span>  
  
3.  <span data-ttu-id="b2332-247">复制上面的 updategram，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="b2332-247">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="b2332-248">在与上一步骤中保存 StudentSchema.xml 所使用文件夹相同的文件夹中将文件另存为 StudentUpdategram.xml。</span><span class="sxs-lookup"><span data-stu-id="b2332-248">Save the file as StudentUpdategram.xml in the same folder used in previous step to save StudentSchema.xml.</span></span>  
  
4.  <span data-ttu-id="b2332-249">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 以执行 updategram。</span><span class="sxs-lookup"><span data-stu-id="b2332-249">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="b2332-250">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="b2332-250">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="h-specifying-namespaces-in-an-updategram"></a><span data-ttu-id="b2332-251">H.</span><span class="sxs-lookup"><span data-stu-id="b2332-251">H.</span></span> <span data-ttu-id="b2332-252">在 updategram 中指定命名空间</span><span class="sxs-lookup"><span data-stu-id="b2332-252">Specifying namespaces in an updategram</span></span>  
 <span data-ttu-id="b2332-253">在 updategram 中，元素所属的命名空间可以在 updategram 中的同一元素中进行声明。</span><span class="sxs-lookup"><span data-stu-id="b2332-253">In an updategram you can have elements that belong to a namespace declared in the same element in the updategram.</span></span> <span data-ttu-id="b2332-254">在这种情况下，对应的架构也必须声明相同的命名空间，并且元素必须属于该目标命名空间。</span><span class="sxs-lookup"><span data-stu-id="b2332-254">In this case, the corresponding schema must also declare the same namespace and the element must belong to that target namespace.</span></span>  
  
 <span data-ttu-id="b2332-255">例如，在以下 updategram ( # A0) 中， **\<Order>** 元素属于元素中声明的命名空间。</span><span class="sxs-lookup"><span data-stu-id="b2332-255">For example, in the following updategram (UpdateGram-ElementHavingNamespace.xml), the **\<Order>** element belongs to a namespace declared in the element.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema='XSD-ElementHavingNameSpace.xml'>  
    <updg:after>  
       <x:Order  xmlns:x="http://server/xyz/schemas/"  
             updg:at-identity="SalesOrderID"   
             RevisionNumber="1"  
             OrderDate="2001-07-01 00:00:00.000"  
             DueDate="2001-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             CustomerID="676"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="00009999-8888-7777-6666-554433221100"  
             ModifiedDate="2001-07-08 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="b2332-256">在这种情况下，架构也必须声明该命名空间，如此架构中所示：</span><span class="sxs-lookup"><span data-stu-id="b2332-256">In this case, the schema must also declare the namespace as shown in this schema:</span></span>  
  
 <span data-ttu-id="b2332-257">以下架构 (XSD-ElementHavingNamespace.xml) 演示如何必须声明对应的元素和属性。</span><span class="sxs-lookup"><span data-stu-id="b2332-257">The following schema (XSD-ElementHavingNamespace.xml) shows how the corresponding element and attributes must be declared.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
     xmlns:dt="urn:schemas-microsoft-com:datatypes"   
     xmlns:sql="urn:schemas-microsoft-com:mapping-schema"    
     xmlns:x="http://server/xyz/schemas/"   
     targetNamespace="http://server/xyz/schemas/" >  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" type="x:Order_type"/>  
  <xsd:complexType name="Order_type">  
    <xsd:attribute name="SalesOrderID"  type="xsd:ID"/>  
    <xsd:attribute name="RevisionNumber" type="xsd:unsignedByte"/>  
    <xsd:attribute name="OrderDate" type="xsd:dateTime"/>  
    <xsd:attribute name="DueDate" type="xsd:dateTime"/>  
    <xsd:attribute name="ShipDate" type="xsd:dateTime"/>  
    <xsd:attribute name="Status" type="xsd:unsignedByte"/>  
    <xsd:attribute name="OnlineOrderFlag" type="xsd:boolean"/>  
    <xsd:attribute name="SalesOrderNumber" type="xsd:string"/>  
    <xsd:attribute name="PurchaseOrderNumber" type="xsd:string"/>  
    <xsd:attribute name="AccountNumber" type="xsd:string"/>  
    <xsd:attribute name="CustomerID" type="xsd:int"/>  
    <xsd:attribute name="ContactID" type="xsd:int"/>  
    <xsd:attribute name="SalesPersonID" type="xsd:int"/>  
    <xsd:attribute name="TerritoryID" type="xsd:int"/>  
    <xsd:attribute name="BillToAddressID" type="xsd:int"/>  
    <xsd:attribute name="ShipToAddressID" type="xsd:int"/>  
    <xsd:attribute name="ShipMethodID" type="xsd:int"/>  
    <xsd:attribute name="CreditCardID" type="xsd:int"/>  
    <xsd:attribute name="CreditCardApprovalCode" type="xsd:string"/>  
    <xsd:attribute name="CurrencyRateID" type="xsd:int"/>  
    <xsd:attribute name="SubTotal" type="xsd:decimal"/>  
    <xsd:attribute name="TaxAmt" type="xsd:decimal"/>  
    <xsd:attribute name="Freight" type="xsd:decimal"/>  
    <xsd:attribute name="TotalDue" type="xsd:decimal"/>  
    <xsd:attribute name="Comment" type="xsd:string"/>  
    <xsd:attribute name="rowguid" type="xsd:string"/>  
    <xsd:attribute name="ModifiedDate" type="xsd:dateTime"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="b2332-258">测试 updategram</span><span class="sxs-lookup"><span data-stu-id="b2332-258">To test the updategram</span></span>  
  
1.  <span data-ttu-id="b2332-259">复制上面的架构，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="b2332-259">Copy the schema above and paste it into a text file.</span></span> <span data-ttu-id="b2332-260">将文件另存为 XSD-ElementHavingNamespace.xml。</span><span class="sxs-lookup"><span data-stu-id="b2332-260">Save the file as XSD-ElementHavingNamespace.xml.</span></span>  
  
2.  <span data-ttu-id="b2332-261">复制上面的 updategram，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="b2332-261">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="b2332-262">在用于保存 XSD-ElementHavingnamespace.xml 的同一文件夹中将文件另存为 Updategram-ElementHavingNamespace.xml。</span><span class="sxs-lookup"><span data-stu-id="b2332-262">Save the file as Updategram-ElementHavingNamespace.xml in the same folder used to save XSD-ElementHavingnamespace.xml.</span></span>  
  
3.  <span data-ttu-id="b2332-263">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 以执行 updategram。</span><span class="sxs-lookup"><span data-stu-id="b2332-263">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="b2332-264">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="b2332-264">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="i-inserting-data-into-an-xml-data-type-column"></a><span data-ttu-id="b2332-265">I.</span><span class="sxs-lookup"><span data-stu-id="b2332-265">I.</span></span> <span data-ttu-id="b2332-266">将数据插入到 XML 数据类型列</span><span class="sxs-lookup"><span data-stu-id="b2332-266">Inserting data into an XML data type column</span></span>  
 <span data-ttu-id="b2332-267">在 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 中已引入了 `xml` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="b2332-267">The `xml` data type was introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="b2332-268">可以使用 updategram 插入和更新存储在 `xml` 数据类型列中的数据，但必须遵守以下规定：</span><span class="sxs-lookup"><span data-stu-id="b2332-268">You can use updategrams to insert and update data stored in `xml` data type columns with the following provisions:</span></span>  
  
-   <span data-ttu-id="b2332-269">`xml` 列不能用于标识现有行。</span><span class="sxs-lookup"><span data-stu-id="b2332-269">The `xml` column cannot be used for identifying an existing row.</span></span> <span data-ttu-id="b2332-270">因此，它不能包括在 updategram 的 `updg:before` 部分中。</span><span class="sxs-lookup"><span data-stu-id="b2332-270">Therefore, it cannot be included in the `updg:before` section of an updategram.</span></span>  
  
-   <span data-ttu-id="b2332-271">将保留插入到 `xml` 列的 XML 片段的作用域中的命名空间，并且会将其命名空间声明添加到所插入片段的顶级元素中。</span><span class="sxs-lookup"><span data-stu-id="b2332-271">Namespaces that are in scope of the XML fragment inserted into the `xml` column will be preserved and their namespace declarations are added to the top element of the inserted fragment.</span></span>  
  
 <span data-ttu-id="b2332-272">例如，在下面的 updategram 中 ( # A0) ，该 **\<Desc>** 元素将更新示例数据库中生产>productModel 表中的 ProductDescription 列 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b2332-272">For example, in the following updategram (SampleUpdateGram.xml), the **\<Desc>** element updates the ProductDescription column in the Production>productModel table in the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="b2332-273">此 updategram 的结果是，ProductDescription 列的 XML 内容是更新元素的 XML 内容 **\<Desc>** 。</span><span class="sxs-lookup"><span data-stu-id="b2332-273">The result of this updategram is that the XML contents of the ProductDescription column are update with the XML contents of the **\<Desc>** element.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
    <updg:sync mapping-schema="SampleSchema.xml" >  
       <updg:before>  
<ProductModel ProductModelID="19">  
   <Name>Mountain-100</Name>  
</ProductModel>  
    </updg:before>  
    <updg:after>  
 <ProductModel>  
    <Name>Mountain-100</Name>  
    <Desc><?xml-stylesheet href="ProductDescription.xsl" type="text/xsl"?>  
        <p1:ProductDescription xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription"   
              xmlns:wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"   
              xmlns:wf="http://www.adventure-works.com/schemas/OtherFeatures"   
              xmlns:html="http://www.w3.org/1999/xhtml"   
              xmlns="">  
  <p1:Summary>  
     <html:p>Insert Example</html:p>  
  </p1:Summary>  
  <p1:Manufacturer>  
    <p1:Name>AdventureWorks</p1:Name>  
    <p1:Copyright>2002</p1:Copyright>  
    <p1:ProductURL>HTTP://www.Adventure-works.com</p1:ProductURL>  
  </p1:Manufacturer>  
  <p1:Features>These are the product highlights.   
    <wm:Warranty>  
       <wm:WarrantyPeriod>3 years</wm:WarrantyPeriod>  
       <wm:Description>parts and labor</wm:Description>  
    </wm:Warranty>  
    <wm:Maintenance>  
       <wm:NoOfYears>10 years</wm:NoOfYears>  
       <wm:Description>maintenance contract available through your dealer or any AdventureWorks retail store.</wm:Description>  
    </wm:Maintenance>  
    <wf:wheel>High performance wheels.</wf:wheel>  
    <wf:saddle>  
      <html:i>Anatomic design</html:i> and made from durable leather for a full-day of riding in comfort.</wf:saddle>  
    <wf:pedal>  
       <html:b>Top-of-the-line</html:b> clipless pedals with adjustable tension.</wf:pedal>  
    <wf:BikeFrame>Each frame is hand-crafted in our Bothell facility to the optimum diameter and wall-thickness required of a premium mountain frame. The heat-treated welded aluminum frame has a larger diameter tube that absorbs the bumps.</wf:BikeFrame>  
    <wf:crankset> Triple crankset; alumunim crank arm; flawless shifting. </wf:crankset>  
   </p1:Features>  
   <p1:Picture>  
      <p1:Angle>front</p1:Angle>  
      <p1:Size>small</p1:Size>  
      <p1:ProductPhotoID>118</p1:ProductPhotoID>  
   </p1:Picture>  
   <p1:Specifications> These are the product specifications.  
     <Material>Almuminum Alloy</Material>  
     <Color>Available in most colors</Color>  
     <ProductLine>Mountain bike</ProductLine>  
     <Style>Unisex</Style>  
     <RiderExperience>Advanced to Professional riders</RiderExperience>  
   </p1:Specifications>  
  </p1:ProductDescription>  
 </Desc>  
      </ProductModel>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="b2332-274">updategram 引用以下带批注的 XSD 架构 (SampleSchema.xml)。</span><span class="sxs-lookup"><span data-stu-id="b2332-274">The updategram refers to the following annotated XSD schema (SampleSchema.xml).</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
           xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
           xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">   
  <xsd:element name="ProductModel"  sql:relation="Production.ProductModel" >  
     <xsd:complexType>  
       <xsd:sequence>  
          <xsd:element name="Name" type="xsd:string"></xsd:element>  
          <xsd:element name="Desc" sql:field="CatalogDescription" sql:datatype="xml">  
           <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="ProductDescription">  
                 <xsd:complexType>  
                   <xsd:sequence>  
                     <xsd:element name="Summary" type="xsd:anyType">  
                     </xsd:element>  
                   </xsd:sequence>  
                 </xsd:complexType>  
              </xsd:element>  
            </xsd:sequence>  
           </xsd:complexType>  
          </xsd:element>   
       </xsd:sequence>  
       <xsd:attribute name="ProductModelID" sql:field="ProductModelID"/>  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="b2332-275">测试 updategram</span><span class="sxs-lookup"><span data-stu-id="b2332-275">To test the updategram</span></span>  
  
1.  <span data-ttu-id="b2332-276">复制上面的架构，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="b2332-276">Copy the schema above and paste it into a text file.</span></span> <span data-ttu-id="b2332-277">将文件另存为 XSD-SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="b2332-277">Save the file as XSD-SampleSchema.xml.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b2332-278">由于 updategram 支持默认映射，所以没有办法识别 `xml` 数据类型的开始和结束。</span><span class="sxs-lookup"><span data-stu-id="b2332-278">Because updategrams support default mapping, there is no way to identify the beginning and ending of the `xml` data type.</span></span> <span data-ttu-id="b2332-279">也就是说，在使用 `xml` 数据类型列插入或更新表时，需要一个映射架构。</span><span class="sxs-lookup"><span data-stu-id="b2332-279">This effectively means that a mapping schema is required when inserting or updating tables with `xml` data type columns.</span></span> <span data-ttu-id="b2332-280">如果没有提供架构，SQLXML 将返回错误，指出表中缺少某一列。</span><span class="sxs-lookup"><span data-stu-id="b2332-280">When a schema is not provided, SQLXML returns an error indicating that one of the columns is missing from the table.</span></span>  
  
2.  <span data-ttu-id="b2332-281">复制上面的 updategram，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="b2332-281">Copy the updategram above and paste it into a text file.</span></span> <span data-ttu-id="b2332-282">在用于保存 SampleSchema.xml 的同一文件夹中将文件另存为 SampleUpdategram.xml。</span><span class="sxs-lookup"><span data-stu-id="b2332-282">Save the file as SampleUpdategram.xml in the same folder used to save SampleSchema.xml.</span></span>  
  
3.  <span data-ttu-id="b2332-283">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 以执行 updategram。</span><span class="sxs-lookup"><span data-stu-id="b2332-283">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="b2332-284">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="b2332-284">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2332-285">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2332-285">See Also</span></span>  
 [<span data-ttu-id="b2332-286">&#40;SQLXML 4.0&#41;的 Updategram 安全注意事项</span><span class="sxs-lookup"><span data-stu-id="b2332-286">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
