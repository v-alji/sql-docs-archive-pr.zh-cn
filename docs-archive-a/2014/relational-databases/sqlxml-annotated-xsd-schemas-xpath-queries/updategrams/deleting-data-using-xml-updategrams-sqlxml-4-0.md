---
title: 使用 XML Updategram 删除数据 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- <after> block
- updategrams [SQLXML], deleting data
- <before> block
- mapping-schema attribute
- record deletions [SQLXML]
ms.assetid: 4fb116d7-7652-474a-a567-cb475a20765c
author: rothja
ms.author: jroth
ms.openlocfilehash: d941005c71dc33dd8c4f5c5cc15f645cd0e68177
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589469"
---
# <a name="deleting-data-using-xml-updategrams-sqlxml-40"></a><span data-ttu-id="75705-102">使用 XML updategram 删除数据 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="75705-102">Deleting Data Using XML Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="75705-103">当记录实例出现在块中，而在块中没有相应记录时，updategram 指示删除操作 **\<before>** **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="75705-103">An updategram indicates a delete operation when a record instance appears in the **\<before>** block with no corresponding records in the **\<after>** block.</span></span> <span data-ttu-id="75705-104">在这种情况下，updategram 将从数据库中删除该记录 **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="75705-104">In this case, the updategram deletes the record in the **\<before>** block from the database.</span></span>  
  
 <span data-ttu-id="75705-105">下面是 updategram 的删除操作格式：</span><span class="sxs-lookup"><span data-stu-id="75705-105">This is the updategram format for a delete operation:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema="SampleSchema.xml"]  >  
   <updg:before>  
       <ElementName />  
      [<ElementName .../>... ]  
   </updg:before>  
    [<updg:after>  
    </updg:after>]  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="75705-106">**\<after>** 如果 updategram 仅执行删除操作，则可以省略标记。</span><span class="sxs-lookup"><span data-stu-id="75705-106">You can omit the **\<after>** tag if the updategram is performing only a delete operation.</span></span> <span data-ttu-id="75705-107">如果未指定可选 `mapping-schema` 属性，则在 **\<ElementName>** updategram 中指定的将映射到数据库表，并且子元素或属性将映射到表中的列。</span><span class="sxs-lookup"><span data-stu-id="75705-107">If you do not specify the optional `mapping-schema` attribute, the **\<ElementName>** specified in the updategram maps to a database table and the child elements or attributes map to columns in the table.</span></span>  
  
 <span data-ttu-id="75705-108">如果 updategram 中指定的元素与表中的多行匹配或与任何行都不匹配，则 updategram 将返回一个错误，并取消整个 **\<sync>** 块。</span><span class="sxs-lookup"><span data-stu-id="75705-108">If an element specified in the updategram either matches more than one row in the table or does not match any row, the updategram returns an error and cancels the entire **\<sync>** block.</span></span> <span data-ttu-id="75705-109">updategram 中的元素每次只能删除一个记录。</span><span class="sxs-lookup"><span data-stu-id="75705-109">Only one record at a time can be deleted by an element in the updategram.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="75705-110">示例</span><span class="sxs-lookup"><span data-stu-id="75705-110">Examples</span></span>  
 <span data-ttu-id="75705-111">本节中的示例使用默认映射（即未在 updategram 中指定映射架构）。</span><span class="sxs-lookup"><span data-stu-id="75705-111">Examples in this section use default mapping (that is, no mapping schema is specified in the updategram).</span></span> <span data-ttu-id="75705-112">有关使用映射架构的 updategram 的更多示例，请参阅[在 Updategram &#40;SQLXML 4.0&#41;中指定带批注的映射架构](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="75705-112">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="75705-113">若要创建使用以下示例的工作示例，必须满足[运行 SQLXML 示例的要求](../../sqlxml/requirements-for-running-sqlxml-examples.md)中指定的要求。</span><span class="sxs-lookup"><span data-stu-id="75705-113">To create working samples using the following examples, you must meet the requirements specified in [Requirements for Running SQLXML Examples](../../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-deleting-a-record-by-using-an-updategram"></a><span data-ttu-id="75705-114">A.</span><span class="sxs-lookup"><span data-stu-id="75705-114">A.</span></span> <span data-ttu-id="75705-115">使用 updategram 删除记录</span><span class="sxs-lookup"><span data-stu-id="75705-115">Deleting a record by using an updategram</span></span>  
 <span data-ttu-id="75705-116">以下 updategram 将从 HumanResources.Shift 表中删除两个记录。</span><span class="sxs-lookup"><span data-stu-id="75705-116">The following updategrams deletes two records from the HumanResources.Shift table.</span></span>  
  
 <span data-ttu-id="75705-117">在这些示例中，updategram 不指定映射架构。</span><span class="sxs-lookup"><span data-stu-id="75705-117">In these examples, the updategram does not specify a mapping schema.</span></span> <span data-ttu-id="75705-118">因此，updategram 使用默认映射，其中元素名称映射到表名称，而属性或子元素映射到列。</span><span class="sxs-lookup"><span data-stu-id="75705-118">Therefore, the updategram uses default mapping, in which the element name maps to table name and the attributes or subelements map to columns.</span></span>  
  
 <span data-ttu-id="75705-119">此第一个 updategram 是以属性为中心的，它标识在块中 (白天和晚上夜) 的两个班次 **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="75705-119">This first updategram is attribute-centric and identifies two shifts (Day-Evening and Evening-Night) in the **\<before>** block.</span></span> <span data-ttu-id="75705-120">因为块中没有相应 **\<after>** 的记录，所以这是一个删除操作。</span><span class="sxs-lookup"><span data-stu-id="75705-120">Because there is no corresponding record in the **\<after>** block, this is a delete operation.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
       <HumanResources.Shift ShiftID="4"  
                        Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift ShiftID="5"  
                        Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
  </updg:before>  
  <updg:after>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="75705-121">测试 updategram</span><span class="sxs-lookup"><span data-stu-id="75705-121">To test the updategram</span></span>  
  
1.  <span data-ttu-id="75705-122">完成示例 B ( "使用 updategram 插入多个记录" ) [使用 XML updategram &#40;SQLXML 4.0&#41;插入数据](inserting-data-using-xml-updategrams-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="75705-122">Complete example B ("Inserting multiple records by using an updategram") in [Inserting Data Using XML Updategrams &#40;SQLXML 4.0&#41;](inserting-data-using-xml-updategrams-sqlxml-4-0.md).</span></span>  
  
2.  <span data-ttu-id="75705-123">将上面的 updategram 复制到记事本，并将其保存为与用来完成 ( "使用 updategram 插入多个记录" ) 使用 "使用 XML Updategram 插入多个记录" [&#40;SQLXML 4.0&#41;](inserting-data-using-xml-updategrams-sqlxml-4-0.md)的相同文件夹中的 Updategram-RemoveShifts.xml。</span><span class="sxs-lookup"><span data-stu-id="75705-123">Copy the updategram above to Notepad and save it as Updategram-RemoveShifts.xml in the same folder as was used to complete ("Inserting multiple records by using an updategram") in [Inserting Data Using XML Updategrams &#40;SQLXML 4.0&#41;](inserting-data-using-xml-updategrams-sqlxml-4-0.md).</span></span>  
  
3.  <span data-ttu-id="75705-124">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 以执行 updategram。</span><span class="sxs-lookup"><span data-stu-id="75705-124">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="75705-125">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="75705-125">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75705-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="75705-126">See Also</span></span>  
 [<span data-ttu-id="75705-127">&#40;SQLXML 4.0&#41;的 Updategram 安全注意事项</span><span class="sxs-lookup"><span data-stu-id="75705-127">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
