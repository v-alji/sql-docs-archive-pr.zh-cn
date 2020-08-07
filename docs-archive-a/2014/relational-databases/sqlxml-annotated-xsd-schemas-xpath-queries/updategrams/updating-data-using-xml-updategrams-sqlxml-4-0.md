---
title: 使用 XML Updategram 更新数据 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- IDREF type attribute [SQLXML]
- before attribute
- <sync> block
- <after> block
- id attribute
- <before> block
- updg:after attribute
- mapping-schema attribute
- IDREFS type attribute [SQLXML]
- updg:id attribute
- multiple record updates
- after attribute
- updategrams [SQLXML], updating data
- updg:before attribute
- record updates [SQLXML]
ms.assetid: 90ef8a33-5ae3-4984-8259-608d2f1d727f
author: rothja
ms.author: jroth
ms.openlocfilehash: 6b019478868b61f293eda824d9b302099728dec4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588436"
---
# <a name="updating-data-using-xml-updategrams-sqlxml-40"></a><span data-ttu-id="75661-102">使用 XML Updategram 更新数据 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="75661-102">Updating Data Using XML Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="75661-103">更新现有数据时，必须同时指定 **\<before>** 和 **\<after>** 块。</span><span class="sxs-lookup"><span data-stu-id="75661-103">When you update existing data, you must specify both the **\<before>** and **\<after>** blocks.</span></span> <span data-ttu-id="75661-104">和块中指定的 **\<before>** 元素 **\<after>** 描述所需的更改。</span><span class="sxs-lookup"><span data-stu-id="75661-104">The elements specified in the **\<before>** and **\<after>** blocks describe the desired change.</span></span> <span data-ttu-id="75661-105">Updategram 使用在块中指定的元素 (s) **\<before>** 来标识数据库中的现有记录 () 。</span><span class="sxs-lookup"><span data-stu-id="75661-105">The updategram uses the element(s) that are specified in the **\<before>** block to identify the existing record(s) in the database.</span></span> <span data-ttu-id="75661-106">块中 (s) 对应的元素 **\<after>** 指示在执行更新操作后记录的外观。</span><span class="sxs-lookup"><span data-stu-id="75661-106">The corresponding element(s) in the **\<after>** block indicate how the records should look after executing the update operation.</span></span> <span data-ttu-id="75661-107">通过此信息，updategram 创建与块匹配的 SQL 语句 **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="75661-107">From this information, the updategram creates an SQL statement that matches the **\<after>** block.</span></span> <span data-ttu-id="75661-108">然后，Updategram 使用该语句更新数据库。</span><span class="sxs-lookup"><span data-stu-id="75661-108">The updategram then uses this statement to update the database.</span></span>  
  
 <span data-ttu-id="75661-109">以下是 Updategram 的更新操作格式：</span><span class="sxs-lookup"><span data-stu-id="75661-109">This is the updategram format for an update operation:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync [mapping-schema="SampleSchema.xml"]  >  
   <updg:before>  
      <ElementName [updg:id="value"] .../>  
      [<ElementName [updg:id="value"] .../> ... ]  
   </updg:before>  
   <updg:after>  
      <ElementName [updg:id="value"] ... />  
      [<ElementName [updg:id="value"] .../> ...]  
   </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
 `<updg:before>`  
 <span data-ttu-id="75661-110">块中的元素用于 **\<before>** 标识数据库表中的现有记录。</span><span class="sxs-lookup"><span data-stu-id="75661-110">The elements in the **\<before>** block identify existing records in the database tables.</span></span>  
  
 `<updg:after>`  
 <span data-ttu-id="75661-111">块中的元素 **\<after>** 说明在应用更新后块中指定的记录的 **\<before>** 外观。</span><span class="sxs-lookup"><span data-stu-id="75661-111">The elements in the **\<after>** block describe how the records specified in the **\<before>** block should look after the updates are applied.</span></span>  
  
 <span data-ttu-id="75661-112">`mapping-schema` 属性用于标识要由 Updategram 使用的映射架构。</span><span class="sxs-lookup"><span data-stu-id="75661-112">The `mapping-schema` attribute identifies the mapping schema to be used by the updategram.</span></span> <span data-ttu-id="75661-113">如果 updategram 指定映射架构，则和块中指定的元素和属性名称 **\<before>** **\<after>** 必须与架构中的名称匹配。</span><span class="sxs-lookup"><span data-stu-id="75661-113">If the updategram specifies a mapping schema, the element and attribute names specified in the **\<before>** and **\<after>** blocks must match the names in the schema.</span></span> <span data-ttu-id="75661-114">该映射架构将这些元素或属性名称映射到数据库表和列名称。</span><span class="sxs-lookup"><span data-stu-id="75661-114">The mapping schema maps these element or attribute names to the database table and column names.</span></span>  
  
 <span data-ttu-id="75661-115">如果 Updategram 不指定架构，则 Updategam 将使用默认映射。</span><span class="sxs-lookup"><span data-stu-id="75661-115">If an updategram does not specify a schema, the updategam uses default mapping.</span></span> <span data-ttu-id="75661-116">在默认映射中， **\<ElementName>** updategram 中指定的将映射到数据库表，并且子元素或属性将映射到数据库列。</span><span class="sxs-lookup"><span data-stu-id="75661-116">In default mapping, the **\<ElementName>** specified in the updategram maps to the database table and the child elements or attributes map to the database columns.</span></span>  
  
 <span data-ttu-id="75661-117">块中的元素 **\<before>** 必须与数据库中的一个表行仅匹配。</span><span class="sxs-lookup"><span data-stu-id="75661-117">An element in the **\<before>** block must match with only one table row in the database.</span></span> <span data-ttu-id="75661-118">如果元素与多个表行匹配或与任何表行都不匹配，则 updategram 将返回一个错误，并取消整个 **\<sync>** 块。</span><span class="sxs-lookup"><span data-stu-id="75661-118">If the element either matches multiple table rows or does not match any table row, the updategram returns an error and cancels the entire **\<sync>** block.</span></span>  
  
 <span data-ttu-id="75661-119">Updategram 可包含多个 **\<sync>** 块。</span><span class="sxs-lookup"><span data-stu-id="75661-119">An updategram can include multiple **\<sync>** blocks.</span></span> <span data-ttu-id="75661-120">每个 **\<sync>** 块都被视为一个事务。</span><span class="sxs-lookup"><span data-stu-id="75661-120">Each **\<sync>** block is treated as a transaction.</span></span> <span data-ttu-id="75661-121">每个 **\<sync>** 块可以有多个 **\<before>** 和 **\<after>** 块。</span><span class="sxs-lookup"><span data-stu-id="75661-121">Each **\<sync>** block can have multiple **\<before>** and **\<after>** blocks.</span></span> <span data-ttu-id="75661-122">例如，如果您要更新两个现有记录，则可以指定两个 **\<before>** 和 **\<after>** 对，每个记录更新一次。</span><span class="sxs-lookup"><span data-stu-id="75661-122">For example, if you are updating two of the existing records, you could specify two **\<before>** and **\<after>** pairs, one for each record being updated.</span></span>  
  
## <a name="using-the-updgid-attribute"></a><span data-ttu-id="75661-123">使用 updg:id 属性</span><span class="sxs-lookup"><span data-stu-id="75661-123">Using the updg:id Attribute</span></span>  
 <span data-ttu-id="75661-124">在和块中指定多个元素时 **\<before>** **\<after>** ，请使用 `updg:id` 特性标记和块中的 **\<before>** 行 **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="75661-124">When multiple elements are specified in the **\<before>** and **\<after>** blocks, use the `updg:id` attribute to mark rows in the **\<before>** and **\<after>** blocks.</span></span> <span data-ttu-id="75661-125">处理逻辑使用此信息来确定块中的哪条记录 **\<before>** 与块中的记录 **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="75661-125">The processing logic uses this information to determine what record in the **\<before>** block pairs with what record in the **\<after>** block.</span></span>  
  
 <span data-ttu-id="75661-126">如果存在以下任一情况，则 `updg:id` 属性不是必需属性（尽管推荐使用该属性）：</span><span class="sxs-lookup"><span data-stu-id="75661-126">The `updg:id` attribute is not necessary (although recommended) if either of the following exists:</span></span>  
  
-   <span data-ttu-id="75661-127">指定的映射架构中的元素定义了 `sql:key-fields` 属性。</span><span class="sxs-lookup"><span data-stu-id="75661-127">The elements in the specified mapping schema have the `sql:key-fields` attribute defined on them.</span></span>  
  
-   <span data-ttu-id="75661-128">为 Updategram 中的键字段提供了一个或多个特定值。</span><span class="sxs-lookup"><span data-stu-id="75661-128">There is one or more specific value supplied for the key field(s) in the updategram.</span></span>  
  
 <span data-ttu-id="75661-129">如果这两种情况，updategram 将使用在中指定的键列 `sql:key-fields` 来配对和块中的元素 **\<before>** **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="75661-129">If either is the case, the updategram uses the key columns that are specified in the `sql:key-fields` to pair the elements in the **\<before>** and **\<after>** blocks.</span></span>  
  
 <span data-ttu-id="75661-130">如果映射架构未标识键列（通过使用 `sql:key-fields`）或者 Updategram 要更新键列值，则必须指定 `updg:id`。</span><span class="sxs-lookup"><span data-stu-id="75661-130">If the mapping schema does not identify key columns (by using `sql:key-fields`) or if the updategram is updating a key column value, you must specify `updg:id`.</span></span>  
  
 <span data-ttu-id="75661-131">和块中标识的记录不必 **\<before>** **\<after>** 按相同顺序排列。</span><span class="sxs-lookup"><span data-stu-id="75661-131">The records that are identified in the **\<before>** and **\<after>** blocks do not have to be in the same order.</span></span> <span data-ttu-id="75661-132">`updg:id`特性强制在和块中指定的元素之间进行关联 **\<before>** **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="75661-132">The `updg:id` attribute forces the association between the elements that are specified in the **\<before>** and **\<after>** blocks.</span></span>  
  
 <span data-ttu-id="75661-133">如果在块中指定一个元素， **\<before>** 并且只在块中指定一个相应的元素 **\<after>** ， `updg:id` 则不需要使用。</span><span class="sxs-lookup"><span data-stu-id="75661-133">If you specify one element in the **\<before>** block and only one corresponding element in the **\<after>** block, using `updg:id` is not necessary.</span></span> <span data-ttu-id="75661-134">但是，建议指定 `updg:id` 以避免多义性。</span><span class="sxs-lookup"><span data-stu-id="75661-134">However, it is recommended that you specify `updg:id` anyway to avoid ambiguity.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="75661-135">示例</span><span class="sxs-lookup"><span data-stu-id="75661-135">Examples</span></span>  
 <span data-ttu-id="75661-136">在使用 Updategram 示例之前，请注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="75661-136">Before you use the updategram examples, note the following:</span></span>  
  
-   <span data-ttu-id="75661-137">大多数示例使用默认映射（即，未在 updategram 中指定任何映射架构）。</span><span class="sxs-lookup"><span data-stu-id="75661-137">Most of the examples use default mapping (that is, no mapping schema is specified in the updategram).</span></span> <span data-ttu-id="75661-138">有关使用映射架构的 updategram 的更多示例，请参阅[在 Updategram &#40;SQLXML 4.0&#41;中指定带批注的映射架构](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="75661-138">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="75661-139">大多数示例使用 AdventureWorks 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="75661-139">Most of the examples use the AdventureWorks sample database.</span></span> <span data-ttu-id="75661-140">已对该数据库中的表应用所有更新。</span><span class="sxs-lookup"><span data-stu-id="75661-140">All the updates are applied to the tables in this database.</span></span> <span data-ttu-id="75661-141">您可以还原 AdventureWorks 数据库。</span><span class="sxs-lookup"><span data-stu-id="75661-141">You can restore the AdventureWorks database.</span></span>  
  
### <a name="a-updating-a-record"></a><span data-ttu-id="75661-142">A.</span><span class="sxs-lookup"><span data-stu-id="75661-142">A.</span></span> <span data-ttu-id="75661-143">更新记录</span><span class="sxs-lookup"><span data-stu-id="75661-143">Updating a record</span></span>  
 <span data-ttu-id="75661-144">以下 Updategram 将 AdventureWorks 数据库的 Person.Contact 表中的雇员姓氏更新为 Fuller。</span><span class="sxs-lookup"><span data-stu-id="75661-144">The following updategram updates the employee last name to Fuller in the Person.Contact table in the AdventureWorks database.</span></span> <span data-ttu-id="75661-145">Updategram 不指定任何映射架构，因此，Updategram 使用默认映射。</span><span class="sxs-lookup"><span data-stu-id="75661-145">The updategram does not specify any mapping schema; therefore, the updategram uses default mapping.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
   <Person.Contact ContactID="1" />  
</updg:before>  
<updg:after>  
   <Person.Contact LastName="Abel-Achong" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="75661-146">块中所述的记录 **\<before>** 表示数据库中的当前记录。</span><span class="sxs-lookup"><span data-stu-id="75661-146">The record described in the **\<before>** block represents the current record in the database.</span></span> <span data-ttu-id="75661-147">Updategram 使用在块中指定的所有列值 **\<before>** 来搜索记录。</span><span class="sxs-lookup"><span data-stu-id="75661-147">The updategram uses all of the column values specified in the **\<before>** block to search for the record.</span></span> <span data-ttu-id="75661-148">在此 updategram 中， **\<before>** 块仅提供 ContactID 列; 因此，updategram 只使用值来搜索记录。</span><span class="sxs-lookup"><span data-stu-id="75661-148">In this updategram, the **\<before>** block provides only the ContactID column; therefore, the updategram uses only the value to search for the record.</span></span> <span data-ttu-id="75661-149">如果要将 LastName 值添加到该块，则 Updategram 会同时使用 ContactID 和 LastName 值执行搜索。</span><span class="sxs-lookup"><span data-stu-id="75661-149">If you were to add the LastName value to this block, the updategram would use both the ContactID and LastName values to search.</span></span>  
  
 <span data-ttu-id="75661-150">在此 updategram 中， **\<after>** 块仅提供 LastName 列值，因为这是唯一要更改的值。</span><span class="sxs-lookup"><span data-stu-id="75661-150">In this updategram, the **\<after>** block provides only the LastName column value because this is the only value that is being changed.</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="75661-151">测试 updategram</span><span class="sxs-lookup"><span data-stu-id="75661-151">To test the updategram</span></span>  
  
1.  <span data-ttu-id="75661-152">复制上面的 Updategram 模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="75661-152">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="75661-153">将该文件另存为 UpdateLastName.xml。</span><span class="sxs-lookup"><span data-stu-id="75661-153">Save the file as UpdateLastName.xml.</span></span>  
  
2.  <span data-ttu-id="75661-154">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 以执行 updategram。</span><span class="sxs-lookup"><span data-stu-id="75661-154">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="75661-155">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="75661-155">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="b-updating-multiple-records-by-using-the-updgid-attribute"></a><span data-ttu-id="75661-156">B.</span><span class="sxs-lookup"><span data-stu-id="75661-156">B.</span></span> <span data-ttu-id="75661-157">使用 updg:id 属性更新多个记录</span><span class="sxs-lookup"><span data-stu-id="75661-157">Updating multiple records by using the updg:id attribute</span></span>  
 <span data-ttu-id="75661-158">在该示例中，Updategram 对 AdventureWorks 数据库中的 HumanResources.Shift 表执行两次更新：</span><span class="sxs-lookup"><span data-stu-id="75661-158">In this example, the updategram performs two updates on the HumanResources.Shift table in the AdventureWorks database:</span></span>  
  
-   <span data-ttu-id="75661-159">它将 7:00AM 开始的原始白班的名称从“Day”更改为“Early Morning”。</span><span class="sxs-lookup"><span data-stu-id="75661-159">It changes the name of the original day shift that starts at 7:00AM from "Day" to "Early Morning".</span></span>  
  
-   <span data-ttu-id="75661-160">它插入名为“Late Morning”的从 10:00AM 开始的新班。</span><span class="sxs-lookup"><span data-stu-id="75661-160">It inserts a new shift named "Late Morning" that starts at 10:00AM.</span></span>  
  
 <span data-ttu-id="75661-161">在 updategram 中， `updg:id` 属性在和块中的元素之间创建关联 **\<before>** **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="75661-161">In the updategram, the `updg:id` attribute creates associations between elements in the **\<before>** and **\<after>** blocks.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Shift updg:id="x" Name="Day" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift updg:id="y" Name="Late Morning"   
                            StartTime="1900-01-01 10:00:00.000"  
                            EndTime="1900-01-01 18:00:00.000"  
                            ModifiedDate="2004-06-01 00:00:00.000"/>  
      <HumanResources.Shift updg:id="x" Name="Early Morning" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="75661-162">请注意属性如何将 `updg:id` 块中的元素的第一个实例 \<HumanResources.Shift> **\<before>** 与 \<HumanResources.Shift> 块中元素的第二个实例配对 **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="75661-162">Notice how the `updg:id` attribute pairs the first instance of the \<HumanResources.Shift> element in the **\<before>** block with the second instance of the \<HumanResources.Shift> element in the **\<after>** block.</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="75661-163">测试 updategram</span><span class="sxs-lookup"><span data-stu-id="75661-163">To test the updategram</span></span>  
  
1.  <span data-ttu-id="75661-164">复制上面的 Updategram 模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="75661-164">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="75661-165">将该文件另存为 UpdateMultipleRecords.xml。</span><span class="sxs-lookup"><span data-stu-id="75661-165">Save the file as UpdateMultipleRecords.xml.</span></span>  
  
2.  <span data-ttu-id="75661-166">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 以执行 updategram。</span><span class="sxs-lookup"><span data-stu-id="75661-166">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="75661-167">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="75661-167">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="c-specifying-multiple-before-and-after-blocks"></a><span data-ttu-id="75661-168">C.</span><span class="sxs-lookup"><span data-stu-id="75661-168">C.</span></span> <span data-ttu-id="75661-169">指定多个 \<before> 和 \<after> 块</span><span class="sxs-lookup"><span data-stu-id="75661-169">Specifying multiple \<before> and \<after> blocks</span></span>  
 <span data-ttu-id="75661-170">若要避免多义性，可以通过使用多个 **\<before>** 和块对来编写示例 B 中的 updategram **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="75661-170">To avoid ambiguity, you can write the updategram in Example B by using multiple **\<before>** and **\<after>** block pairs.</span></span> <span data-ttu-id="75661-171">指定 **\<before>** 和 **\<after>** 对是指定多个更新的一种方法，其中至少有混淆。</span><span class="sxs-lookup"><span data-stu-id="75661-171">Specifying **\<before>** and **\<after>** pairs is one way of specifying multiple updates with a minimum of confusion.</span></span> <span data-ttu-id="75661-172">此外，如果每个 **\<before>** 和 **\<after>** 块最多指定一个元素，则无需使用 `updg:id` 特性。</span><span class="sxs-lookup"><span data-stu-id="75661-172">Also, if each of the **\<before>** and **\<after>** blocks specify at most one element, you do not have to use the `updg:id` attribute.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75661-173">若要形成一对， **\<after>** 标记必须紧跟在其对应的 **\<before>** 标记之后。</span><span class="sxs-lookup"><span data-stu-id="75661-173">To form a pair, the **\<after>** tag must immediately follow its corresponding **\<before>** tag.</span></span>  
  
 <span data-ttu-id="75661-174">在以下 updategram 中，第一个 **\<before>** 和 **\<after>** 对将更新当天的 shift 名称。</span><span class="sxs-lookup"><span data-stu-id="75661-174">In the following updategram, the first **\<before>** and **\<after>** pair updates the shift name for the day shift.</span></span> <span data-ttu-id="75661-175">第二对将插入新的轮班记录。</span><span class="sxs-lookup"><span data-stu-id="75661-175">The second pair inserts a new shift record.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Shift ShiftID="1" Name="Day" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift Name="Early Morning" />  
    </updg:after>  
    <updg:before>  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift Name="Late Morning"   
                            StartTime="1900-01-01 10:00:00.000"  
                            EndTime="1900-01-01 18:00:00.000"  
                            ModifiedDate="2004-06-01 00:00:00.000"/>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="75661-176">测试 updategram</span><span class="sxs-lookup"><span data-stu-id="75661-176">To test the updategram</span></span>  
  
1.  <span data-ttu-id="75661-177">复制上面的 Updategram 模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="75661-177">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="75661-178">将该文件另存为 UpdateMultipleBeforeAfter.xml。</span><span class="sxs-lookup"><span data-stu-id="75661-178">Save the file as UpdateMultipleBeforeAfter.xml.</span></span>  
  
2.  <span data-ttu-id="75661-179">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 以执行 updategram。</span><span class="sxs-lookup"><span data-stu-id="75661-179">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="75661-180">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="75661-180">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="d-specifying-multiple-sync-blocks"></a><span data-ttu-id="75661-181">D.</span><span class="sxs-lookup"><span data-stu-id="75661-181">D.</span></span> <span data-ttu-id="75661-182">指定多个 \<sync> 块</span><span class="sxs-lookup"><span data-stu-id="75661-182">Specifying multiple \<sync> blocks</span></span>  
 <span data-ttu-id="75661-183">可以 **\<sync>** 在 updategram 中指定多个块。</span><span class="sxs-lookup"><span data-stu-id="75661-183">You can specify multiple **\<sync>** blocks in an updategram.</span></span> <span data-ttu-id="75661-184">指定的每个 **\<sync>** 块都是独立的事务。</span><span class="sxs-lookup"><span data-stu-id="75661-184">Each **\<sync>** block that is specified is an independent transaction.</span></span>  
  
 <span data-ttu-id="75661-185">在下面的 updategram 中，第一个 **\<sync>** 块更新 Customer 表中的一条记录。</span><span class="sxs-lookup"><span data-stu-id="75661-185">In the following updategram, the first **\<sync>** block updates a record in the Sales.Customer table.</span></span> <span data-ttu-id="75661-186">出于简化原因，Updategram 仅指定必需的列值：标识值 (CustomerID) 和要更新的值 (SalesPersonID)。</span><span class="sxs-lookup"><span data-stu-id="75661-186">For the sake of simplicity, the updategram specifies only the required column values; the identity value (CustomerID) and the value being updated (SalesPersonID).</span></span>  
  
 <span data-ttu-id="75661-187">第二个 **\<sync>** 块将两个记录添加到 SalesOrderHeader 表中。</span><span class="sxs-lookup"><span data-stu-id="75661-187">The second **\<sync>** block adds two records to the Sales.SalesOrderHeader table.</span></span> <span data-ttu-id="75661-188">对于该表，SalesOrderID 是 IDENTITY 类型的列。</span><span class="sxs-lookup"><span data-stu-id="75661-188">For this table, SalesOrderID is an IDENTITY-type column.</span></span> <span data-ttu-id="75661-189">因此，updategram 不会在每个元素中指定 SalesOrderID 的值 \<Sales.SalesOrderHeader> 。</span><span class="sxs-lookup"><span data-stu-id="75661-189">Therefore, the updategram does not specify the value of SalesOrderID in each of the \<Sales.SalesOrderHeader> elements.</span></span>  
  
 <span data-ttu-id="75661-190">指定多个 **\<sync>** 块很有用，因为如果第二个 **\<sync>** 块 (事务) 未能将记录添加到 SalesOrderHeader 表中，则第一个 **\<sync>** 块仍可更新 customer 表中的 customer 记录。</span><span class="sxs-lookup"><span data-stu-id="75661-190">Specifying multiple **\<sync>** blocks is useful because if the second **\<sync>** block (a transaction) fails to add records to Sales.SalesOrderHeader table, the first **\<sync>** block can still update the customer record in the Sales.Customer table.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
      <Sales.Customer CustomerID="1" SalesPersonID="280" />  
    </updg:before>  
    <updg:after>  
      <Sales.Customer CustomerID="1" SalesPersonID="283" />  
    </updg:after>  
  </updg:sync>  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
   <Sales.SalesOrderHeader   
             CustomerID="1"  
             RevisionNumber="1"  
             OrderDate="2004-07-01 00:00:00.000"  
             DueDate="2004-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="01010101-2222-3333-4444-556677889900"  
             ModifiedDate="2004-07-08 00:00:00.000" />  
   <Sales.SalesOrderHeader  
             CustomerID="1"  
             RevisionNumber="1"  
             OrderDate="2004-07-01 00:00:00.000"  
             DueDate="2004-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="1000.0000"  
             TaxAmt="0.0000"  
             Freight="0.0000"  
             rowguid="10101010-2222-3333-4444-556677889900"  
             ModifiedDate="2004-07-09 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="75661-191">测试 updategram</span><span class="sxs-lookup"><span data-stu-id="75661-191">To test the updategram</span></span>  
  
1.  <span data-ttu-id="75661-192">复制上面的 Updategram 模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="75661-192">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="75661-193">将文件另存为 UpdateMultipleSyncs.xml。</span><span class="sxs-lookup"><span data-stu-id="75661-193">Save the file as UpdateMultipleSyncs.xml.</span></span>  
  
2.  <span data-ttu-id="75661-194">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 以执行 updategram。</span><span class="sxs-lookup"><span data-stu-id="75661-194">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="75661-195">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="75661-195">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="e-using-a-mapping-schema"></a><span data-ttu-id="75661-196">E.</span><span class="sxs-lookup"><span data-stu-id="75661-196">E.</span></span> <span data-ttu-id="75661-197">使用映射架构</span><span class="sxs-lookup"><span data-stu-id="75661-197">Using a mapping schema</span></span>  
 <span data-ttu-id="75661-198">在该示例中，Updategram 通过使用 `mapping-schema` 属性来指定映射架构。</span><span class="sxs-lookup"><span data-stu-id="75661-198">In this example, the updategram specifies a mapping schema by using the `mapping-schema` attribute.</span></span> <span data-ttu-id="75661-199">（没有默认映射；就是说，由映射架构提供所需的映射，将 Updategram 中的元素和属性映射到数据库表和列。）</span><span class="sxs-lookup"><span data-stu-id="75661-199">(There is no default mapping; that is, the mapping schema provides the necessary mapping of elements and attributes in the updategram to the database tables and columns.)</span></span>  
  
 <span data-ttu-id="75661-200">在 Updategram 中指定的元素和属性将引用映射架构中的元素和属性。</span><span class="sxs-lookup"><span data-stu-id="75661-200">The elements and attributes specified in the updategram refer to the elements and attributes in the mapping schema.</span></span>  
  
 <span data-ttu-id="75661-201">下面的 XSD 映射架构具有 **\<Customer>** 、 **\<Order>** 和 **\<OD>** 元素，这些元素映射到数据库中的 SalesOrderHeader 表和 SalesOrderDetail 表。</span><span class="sxs-lookup"><span data-stu-id="75661-201">The following XSD mapping schema has **\<Customer>**, **\<Order>**, and **\<OD>** elements that map to the Sales.Customer, Sales.SalesOrderHeader, and Sales.SalesOrderDetail tables in the database.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustomerOrder"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
  
    <sql:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                     sql:relationship="CustomerOrder" >  
           <xsd:complexType>  
              <xsd:sequence>  
                <xsd:element name="OD"   
                             sql:relation="Sales.SalesOrderDetail"  
                             sql:relationship="OrderOD" >  
                 <xsd:complexType>  
                  <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                  <xsd:attribute name="ProductID" type="xsd:integer" />  
                  <xsd:attribute name="UnitPrice" type="xsd:decimal" />  
                  <xsd:attribute name="OrderQty" type="xsd:integer" />  
                  <xsd:attribute name="UnitPriceDiscount" type="xsd:decimal" />   
                 </xsd:complexType>  
                </xsd:element>  
              </xsd:sequence>  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="OrderDate" type="xsd:date" />  
           </xsd:complexType>  
        </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="CustomerID"   type="xsd:string" />   
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="75661-202">以下 Updategram 指定该映射架构 (UpdategramMappingSchema.xml)。</span><span class="sxs-lookup"><span data-stu-id="75661-202">This mapping schema (UpdategramMappingSchema.xml) is specified in the following updategram.</span></span> <span data-ttu-id="75661-203">该 Updategram 在 Sales.SalesOrderDetail 表中为特定顺序添加顺序细节项。</span><span class="sxs-lookup"><span data-stu-id="75661-203">The updategram adds an order detail item in the Sales.SalesOrderDetail table for a specific order.</span></span> <span data-ttu-id="75661-204">Updategram 包括嵌套元素： **\<OD>** 嵌套在元素内的元素 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="75661-204">The updategram includes nested elements: an **\<OD>** element nested inside an **\<Order>** element.</span></span> <span data-ttu-id="75661-205">在映射架构中指定了这两个元素之间的主键/外键关系。</span><span class="sxs-lookup"><span data-stu-id="75661-205">The primary key/foreign key relationship between these two elements is specified in the mapping schema.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="UpdategramMappingSchema.xml" >  
    <updg:before>  
       <Order SalesOrderID="43659" />  
    </updg:before>  
    <updg:after>  
      <Order SalesOrderID="43659" >  
          <OD ProductID="776" UnitPrice="2329.0000"  
              OrderQty="2" UnitPriceDiscount="0.0" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="75661-206">测试 updategram</span><span class="sxs-lookup"><span data-stu-id="75661-206">To test the updategram</span></span>  
  
1.  <span data-ttu-id="75661-207">复制上面的映射架构，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="75661-207">Copy the mapping schema above and paste it into a text file.</span></span> <span data-ttu-id="75661-208">将该文件另存为 UpdategramMappingSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="75661-208">Save the file as UpdategramMappingSchema.xml.</span></span>  
  
2.  <span data-ttu-id="75661-209">复制上面的 Updategram 模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="75661-209">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="75661-210">在用于保存映射架构 (UpdategramMappingSchema.xml) 的相同文件夹中将该文件另存为 UpdateWithMappingSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="75661-210">Save the file as UpdateWithMappingSchema.xml in the same folder as was used to save the mapping schema (UpdategramMappingSchema.xml).</span></span>  
  
3.  <span data-ttu-id="75661-211">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 以执行 updategram。</span><span class="sxs-lookup"><span data-stu-id="75661-211">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="75661-212">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="75661-212">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="75661-213">有关使用映射架构的 updategram 的更多示例，请参阅[在 Updategram &#40;SQLXML 4.0&#41;中指定带批注的映射架构](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="75661-213">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
### <a name="f-using-a-mapping-schema-with-idrefs-attributes"></a><span data-ttu-id="75661-214">F.</span><span class="sxs-lookup"><span data-stu-id="75661-214">F.</span></span> <span data-ttu-id="75661-215">将 IDREFS 属性与映射架构一起使用</span><span class="sxs-lookup"><span data-stu-id="75661-215">Using a mapping schema with IDREFS attributes</span></span>  
 <span data-ttu-id="75661-216">该示例说明 Updategram 如何在映射架构中使用 IDREFS 属性以更新多个表中的记录。</span><span class="sxs-lookup"><span data-stu-id="75661-216">This example illustrates how updategrams use the IDREFS attributes in the mapping schema to update records in multiple tables.</span></span> <span data-ttu-id="75661-217">对于该示例，假定数据库由以下表组成：</span><span class="sxs-lookup"><span data-stu-id="75661-217">For this example, assume that the database consists of the following tables:</span></span>  
  
-   <span data-ttu-id="75661-218">Student(StudentID, LastName)</span><span class="sxs-lookup"><span data-stu-id="75661-218">Student(StudentID, LastName)</span></span>  
  
-   <span data-ttu-id="75661-219">Course(CourseID, CourseName)</span><span class="sxs-lookup"><span data-stu-id="75661-219">Course(CourseID, CourseName)</span></span>  
  
-   <span data-ttu-id="75661-220">Enrollment(StudentID, CourseID)</span><span class="sxs-lookup"><span data-stu-id="75661-220">Enrollment(StudentID, CourseID)</span></span>  
  
 <span data-ttu-id="75661-221">由于学生可以注册参加很多课程，而且一种课程可以有很多学生，因此需要用第三个表 Enrollment 表以表示该 M:N 关系。</span><span class="sxs-lookup"><span data-stu-id="75661-221">Because a student can enroll in many courses and a course can have many students, the third table, the Enrollment table, is required to represent this M:N relationship.</span></span>  
  
 <span data-ttu-id="75661-222">下面的 XSD 映射架构通过使用 **\<Student>** 、和元素提供表的 XML 视图 **\<Course>** **\<Enrollment>** 。</span><span class="sxs-lookup"><span data-stu-id="75661-222">The following XSD mapping schema provides an XML view of the tables by using the **\<Student>**, **\<Course>**, and **\<Enrollment>** elements.</span></span> <span data-ttu-id="75661-223">映射架构中的**IDREFS**特性指定这些元素之间的关系。</span><span class="sxs-lookup"><span data-stu-id="75661-223">The **IDREFS** attributes in the mapping schema specify the relationship between these elements.</span></span> <span data-ttu-id="75661-224">元素上的**StudentIDList**属性 **\<Course>** 是一个**IDREFS**类型属性，该属性引用注册表中的 StudentID 列。</span><span class="sxs-lookup"><span data-stu-id="75661-224">The **StudentIDList** attribute on the **\<Course>** element is an **IDREFS** type attribute that refers to the StudentID column in the Enrollment table.</span></span> <span data-ttu-id="75661-225">同样，元素上的**EnrolledIn**属性 **\<Student>** 是一个**IDREFS**类型属性，该属性引用注册表中的 CourseID 列。</span><span class="sxs-lookup"><span data-stu-id="75661-225">Likewise, the **EnrolledIn** attribute on the **\<Student>** element is an **IDREFS** type attribute that refers to the CourseID column in the Enrollment table.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="StudentEnrollment"  
          parent="Student"  
          parent-key="StudentID"  
          child="Enrollment"  
          child-key="StudentID" />  
  
    <sql:relationship name="CourseEnrollment"  
          parent="Course"  
          parent-key="CourseID"  
          child="Enrollment"  
          child-key="CourseID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Course" sql:relation="Course"   
                             sql:key-fields="CourseID" >  
    <xsd:complexType>  
    <xsd:attribute name="CourseID"  type="xsd:string" />   
    <xsd:attribute name="CourseName"   type="xsd:string" />   
    <xsd:attribute name="StudentIDList" sql:relation="Enrollment"  
                 sql:field="StudentID"  
                 sql:relationship="CourseEnrollment"   
                                     type="xsd:IDREFS" />  
  
    </xsd:complexType>  
  </xsd:element>  
  <xsd:element name="Student" sql:relation="Student" >  
    <xsd:complexType>  
    <xsd:attribute name="StudentID"  type="xsd:string" />   
    <xsd:attribute name="LastName"   type="xsd:string" />   
    <xsd:attribute name="EnrolledIn" sql:relation="Enrollment"  
                 sql:field="CourseID"  
                 sql:relationship="StudentEnrollment"   
                                     type="xsd:IDREFS" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="75661-226">一旦在 Updategram 中指定该架构，并在 Course 表中插入记录，则 Updategram 将在 Course 表中插入新的课程记录。</span><span class="sxs-lookup"><span data-stu-id="75661-226">Whenever you specify this schema in an updategram and insert a record in the Course table, the updategram inserts a new course record in the Course table.</span></span> <span data-ttu-id="75661-227">如果为 StudentIDList 属性指定一个或多个新学生 ID，则 Updategram 还将在 Enrollment 表中为每个新学生插入记录。</span><span class="sxs-lookup"><span data-stu-id="75661-227">If you specify one or more new student IDs for the StudentIDList attribute, the updategram also inserts a record in the Enrollment table for the each new student.</span></span> <span data-ttu-id="75661-228">该 Updategram 将确保不向 Enrollment 表添加重复项。</span><span class="sxs-lookup"><span data-stu-id="75661-228">The updategram ensures that no duplicates are added to the Enrollment table.</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="75661-229">测试 updategram</span><span class="sxs-lookup"><span data-stu-id="75661-229">To test the updategram</span></span>  
  
1.  <span data-ttu-id="75661-230">在虚拟根目录中所指定的数据库内创建这些表：</span><span class="sxs-lookup"><span data-stu-id="75661-230">Create these tables in the database that is specified in the virtual root:</span></span>  
  
    ```  
    CREATE TABLE Student(StudentID varchar(10) primary key,   
                         LastName varchar(25))  
    CREATE TABLE Course(CourseID varchar(10) primary key,   
                        CourseName varchar(25))  
    CREATE TABLE Enrollment(StudentID varchar(10)   
                                      references Student(StudentID),  
                           CourseID varchar(10)   
                                      references Course(CourseID))  
    ```  
  
2.  <span data-ttu-id="75661-231">添加以下示例数据：</span><span class="sxs-lookup"><span data-stu-id="75661-231">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Student VALUES ('S1','Davoli')  
    INSERT INTO Student VALUES ('S2','Fuller')  
  
    INSERT INTO Course VALUES  ('CS101', 'C Programming')  
    INSERT INTO Course VALUES  ('CS102', 'Understanding XML')  
  
    INSERT INTO Enrollment VALUES ('S1', 'CS101')  
    INSERT INTO Enrollment VALUES ('S1', 'CS102')  
    ```  
  
3.  <span data-ttu-id="75661-232">复制上面的映射架构，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="75661-232">Copy the mapping schema above and paste it into a text file.</span></span> <span data-ttu-id="75661-233">将该文件另存为 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="75661-233">Save the file as SampleSchema.xml.</span></span>  
  
4.  <span data-ttu-id="75661-234">将 Updategram (SampleUpdategram) 保存到上一步中用于保存映射架构的相同文件夹中。</span><span class="sxs-lookup"><span data-stu-id="75661-234">Save the updategram (SampleUpdategram) in the same folder used to save the mapping schema in the previous step.</span></span> <span data-ttu-id="75661-235">（该 Updategram 从 CS102 课程中删除 StudentID="1" 的学生。）</span><span class="sxs-lookup"><span data-stu-id="75661-235">(This updategram drops a student with StudentID="1" from the CS102 course.)</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleSchema.xml" >  
        <updg:before>  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101 CS102" />  
        </updg:before>  
        <updg:after >  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
5.  <span data-ttu-id="75661-236">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 以执行 updategram。</span><span class="sxs-lookup"><span data-stu-id="75661-236">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="75661-237">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="75661-237">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
6.  <span data-ttu-id="75661-238">按照前面描述的步骤，保存并执行以下 Updategram。</span><span class="sxs-lookup"><span data-stu-id="75661-238">Save and execute the following updategram as described in the previous steps.</span></span> <span data-ttu-id="75661-239">该 Updategram 在 Enrollment 表中添加记录，从而将 StudentID="1" 的学生重新添加到 CS102 课程中。</span><span class="sxs-lookup"><span data-stu-id="75661-239">The updategram adds the student with StudentID="1" back into the CS102 course by adding a record in the Enrollment table.</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleSchema.xml" >  
        <updg:before>  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101" />  
        </updg:before>  
        <updg:after >  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101 CS102" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
7.  <span data-ttu-id="75661-240">按照前面描述的步骤，保存并执行下一个 Updategram。</span><span class="sxs-lookup"><span data-stu-id="75661-240">Save and execute this next updategram as described in the previous steps.</span></span> <span data-ttu-id="75661-241">该 Updategram 插入三个新学生，并将他们注册到 CS101 课程。</span><span class="sxs-lookup"><span data-stu-id="75661-241">This updategram inserts three new students and enrolls them in the CS101 course.</span></span> <span data-ttu-id="75661-242">同样，IDREFS 关系将在 Enrollment 表中插入记录。</span><span class="sxs-lookup"><span data-stu-id="75661-242">Again, the IDREFS relationship inserts records in the Enrollment table.</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleSchema.xml" >  
        <updg:before>  
           <Course updg:id="y" CourseID="CS101"   
                               CourseName="C Programming" />  
        </updg:before>  
        <updg:after >  
           <Student updg:id="x1" StudentID="S3" LastName="Leverling" />  
           <Student updg:id="x2" StudentID="S4" LastName="Pecock" />  
           <Student updg:id="x3" StudentID="S5" LastName="Buchanan" />  
           <Course updg:id="y" CourseID="CS101"  
                               CourseName="C Programming"  
                               StudentIDList="S3 S4 S5" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
 <span data-ttu-id="75661-243">这是等效的 XDR 架构：</span><span class="sxs-lookup"><span data-stu-id="75661-243">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <ElementType name="Enrollment" sql:relation="Enrollment" sql:key-fields="StudentID CourseID">  
    <AttributeType name="StudentID" dt:type="id" />  
    <AttributeType name="CourseID" dt:type="id" />  
  
    <attribute type="StudentID" />  
    <attribute type="CourseID" />  
  </ElementType>  
  <ElementType name="Course" sql:relation="Course" sql:key-fields="CourseID">  
    <AttributeType name="CourseID" dt:type="id" />  
    <AttributeType name="CourseName" />  
  
    <attribute type="CourseID" />  
    <attribute type="CourseName" />  
  
    <AttributeType name="StudentIDList" dt:type="idrefs" />  
    <attribute type="StudentIDList" sql:relation="Enrollment" sql:field="StudentID" >  
        <sql:relationship  
                key-relation="Course"  
                key="CourseID"  
                foreign-relation="Enrollment"  
                foreign-key="CourseID" />  
    </attribute>  
  
  </ElementType>  
  <ElementType name="Student" sql:relation="Student">  
    <AttributeType name="StudentID" dt:type="id" />  
     <AttributeType name="LastName" />  
  
    <attribute type="StudentID" />  
    <attribute type="LastName" />  
  
    <AttributeType name="EnrolledIn" dt:type="idrefs" />  
    <attribute type="EnrolledIn" sql:relation="Enrollment" sql:field="CourseID" >  
        <sql:relationship  
                key-relation="Student"  
                key="StudentID"  
                foreign-relation="Enrollment"  
                foreign-key="StudentID" />  
    </attribute>  
  
    <element type="Enrollment" sql:relation="Enrollment" >  
        <sql:relationship key-relation="Student"  
                          key="StudentID"  
                          foreign-relation="Enrollment"  
                          foreign-key="StudentID" />  
    </element>  
  </ElementType>  
  
</Schema>  
```  
  
 <span data-ttu-id="75661-244">有关使用映射架构的 updategram 的更多示例，请参阅[在 Updategram &#40;SQLXML 4.0&#41;中指定带批注的映射架构](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="75661-244">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75661-245">另请参阅</span><span class="sxs-lookup"><span data-stu-id="75661-245">See Also</span></span>  
 [<span data-ttu-id="75661-246">&#40;SQLXML 4.0&#41;的 Updategram 安全注意事项</span><span class="sxs-lookup"><span data-stu-id="75661-246">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
