---
title: SQLXML 4.0 中的 Diffgram 简介 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotations [SQLXML]
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: 1902d67f-baf3-46e6-a36c-b24b5ba6f8ea
author: rothja
ms.author: jroth
ms.openlocfilehash: e57d87d064ace47247f342ed002b162b920e627f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587289"
---
# <a name="introduction-to-diffgrams-in-sqlxml-40"></a><span data-ttu-id="5a1e3-102">SQLXML 4.0 中的 DiffGrams 简介</span><span class="sxs-lookup"><span data-stu-id="5a1e3-102">Introduction to DiffGrams in SQLXML 4.0</span></span>
  <span data-ttu-id="5a1e3-103">本主题提供对 DiffGrams 的简要介绍。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-103">This topic provides a brief introduction to DiffGrams.</span></span>  
  
## <a name="diffgram-format"></a><span data-ttu-id="5a1e3-104">DiffGram 格式</span><span class="sxs-lookup"><span data-stu-id="5a1e3-104">DiffGram Format</span></span>  
 <span data-ttu-id="5a1e3-105">这是常规 DiffGram 格式：</span><span class="sxs-lookup"><span data-stu-id="5a1e3-105">This is the general DiffGram format:</span></span>  
  
```  
<?xml version="1.0"?>  
<diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
   <DataInstance>  
      ...  
   </DataInstance>  
   [<diffgr:before>  
        ...  
   </diffgr:before>]  
  
   [<diffgr:errors>  
        ...  
   </diffgr:errors>]  
</diffgr:diffgram>  
```  
  
 <span data-ttu-id="5a1e3-106">DiffGram 格式由这些块组成：</span><span class="sxs-lookup"><span data-stu-id="5a1e3-106">The DiffGram format consists of these blocks:</span></span>  
  
 **\<DataInstance>**  
 <span data-ttu-id="5a1e3-107">此元素的名称**DataInstance**用于此文档中的说明。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-107">The name of this element, **DataInstance**, is used for explanation purposes in this documentation.</span></span> <span data-ttu-id="5a1e3-108">例如，如果 DiffGram 是从 .NET Framework 中的数据集生成的，则该数据集的**name**属性的值将用作此元素的名称。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-108">For example, if the DiffGram were generated from a dataset in the .NET Framework, the value of the **Name** property of the dataset would be used as the name of this element.</span></span> <span data-ttu-id="5a1e3-109">此块包含更改后的所有相关数据，可能包括尚未修改的数据。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-109">This block contains all relevant data after the change, possibly including data that has not been modified.</span></span> <span data-ttu-id="5a1e3-110">DiffGram 处理逻辑将忽略未指定**diffgr： hasChanges**特性的块中的元素。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-110">The DiffGram processing logic ignores the elements in this block for which the **diffgr:hasChanges** attribute is not specified.</span></span>  
  
 **\<diffgr:before>**  
 <span data-ttu-id="5a1e3-111">此可选块包含必须更新或删除的原始记录实例（元素）。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-111">This optional block contains the original record instances (elements) that must be updated or deleted.</span></span> <span data-ttu-id="5a1e3-112">要修改的所有数据库表 (DiffGram) 更新或删除这些数据库表都必须显示为块中的顶级元素 **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-112">All the database tables being modified (updated or deleted) by the DiffGram must appear as top-level elements in the **\<before>** block.</span></span>  
  
 **\<diffgr:errors>**  
 <span data-ttu-id="5a1e3-113">DiffGram 处理逻辑将忽略此可选块。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-113">This optional block is ignored by the DiffGram processing logic.</span></span>  
  
## <a name="diffgram-annotations"></a><span data-ttu-id="5a1e3-114">DiffGram 批注</span><span class="sxs-lookup"><span data-stu-id="5a1e3-114">DiffGram Annotations</span></span>  
 <span data-ttu-id="5a1e3-115">这些批注在 DiffGram 命名空间 **"urn：架构-microsoft-com： xml-DiffGram-01"** 中定义：</span><span class="sxs-lookup"><span data-stu-id="5a1e3-115">These annotations are defined in the DiffGram namespace **"urn:schemas-microsoft-com:xml-diffgram-01"**:</span></span>  
  
 <span data-ttu-id="5a1e3-116">**id**</span><span class="sxs-lookup"><span data-stu-id="5a1e3-116">**id**</span></span>  
 <span data-ttu-id="5a1e3-117">此特性用于将和块中的元素配对 **\<before>** **\<DataInstance>** 。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-117">This attribute is used to pair the elements in the **\<before>** and the **\<DataInstance>** blocks.</span></span>  
  
 <span data-ttu-id="5a1e3-118">**hasChanges**</span><span class="sxs-lookup"><span data-stu-id="5a1e3-118">**hasChanges**</span></span>  
 <span data-ttu-id="5a1e3-119">对于插入操作或更新操作，DiffGram 必须使用**插入**或**修改**的值来指定此属性。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-119">For an insert or an update operation, the DiffGram must specify this attribute with the value **inserted** or **modified**.</span></span> <span data-ttu-id="5a1e3-120">如果此属性不存在，则处理逻辑将忽略中的相应元素， **\<DataInstance>** 并且不执行任何更新。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-120">If this attribute is not present, the corresponding element in the **\<DataInstance>** is ignored by the processing logic and no updates are performed.</span></span> <span data-ttu-id="5a1e3-121">有关工作示例，请参阅[SQLXML 4.0&#41;的 DiffGram 示例 &#40;](diffgram-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-121">For working samples, see [DiffGram Examples &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="5a1e3-122">**parentID**</span><span class="sxs-lookup"><span data-stu-id="5a1e3-122">**parentID**</span></span>  
 <span data-ttu-id="5a1e3-123">该属性在 DiffGram 中用于指定元素之间的父子关系。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-123">This attribute is used to specify parent-child relationships among the elements in the DiffGram.</span></span> <span data-ttu-id="5a1e3-124">此属性仅出现在 \<before> 块中。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-124">This attribute appears only in the \<before> block.</span></span> <span data-ttu-id="5a1e3-125">应用更新时，SQLXML 将使用它。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-125">It is used by SQLXML when applying updates.</span></span> <span data-ttu-id="5a1e3-126">在确定 DiffGram 中元素的处理顺序时，将使用该父子关系。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-126">The parent-child relationship is used in determining the order in which the elements in the DiffGram are processed.</span></span>  
  
## <a name="understanding-the-diffgram-processing-logic"></a><span data-ttu-id="5a1e3-127">了解 DiffGram 处理逻辑</span><span class="sxs-lookup"><span data-stu-id="5a1e3-127">Understanding the DiffGram Processing Logic</span></span>  
 <span data-ttu-id="5a1e3-128">DiffGram 处理逻辑使用某些规则来确定操作是否是插入、更新或删除操作。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-128">The DiffGram processing logic uses certain rules to determine whether an operation is an insert, update, or delete operation.</span></span> <span data-ttu-id="5a1e3-129">下表描述了这些规则。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-129">These rules are described in the following table.</span></span>  
  
|<span data-ttu-id="5a1e3-130">Operation</span><span class="sxs-lookup"><span data-stu-id="5a1e3-130">Operation</span></span>|<span data-ttu-id="5a1e3-131">说明</span><span class="sxs-lookup"><span data-stu-id="5a1e3-131">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a1e3-132">Insert</span><span class="sxs-lookup"><span data-stu-id="5a1e3-132">Insert</span></span>|<span data-ttu-id="5a1e3-133">当元素出现在 **\<DataInstance>** 块中但不在相应的块中时，DiffGram 指示插入操作 **\<before>** ，并且**diffgr： hasChanges**特性是 (**diffgr： hasChanges =** 指定元素上插入) 。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-133">A DiffGram indicates an insert operation when an element appears in the **\<DataInstance>** block but not in the corresponding **\<before>** block, and the **diffgr:hasChanges** attribute is specified (**diffgr:hasChanges=inserted**) on the element.</span></span> <span data-ttu-id="5a1e3-134">在这种情况下，DiffGram 将在块中指定的记录实例插入 **\<DataInstance>** 到数据库中。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-134">In this case, the DiffGram inserts the record instance that is specified in the **\<DataInstance>** block into the database.</span></span><br /><br /> <span data-ttu-id="5a1e3-135">如果未指定**diffgr： hasChanges**属性，处理逻辑将忽略元素，并且不执行任何插入操作。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-135">If the **diffgr:hasChanges** attribute is not specified, the element is ignored by the processing logic and no insert is performed.</span></span> <span data-ttu-id="5a1e3-136">有关工作示例，请参阅[SQLXML 4.0&#41;的 DiffGram 示例 &#40;](diffgram-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-136">For working samples, see [DiffGram Examples &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md).</span></span>|  
|<span data-ttu-id="5a1e3-137">更新</span><span class="sxs-lookup"><span data-stu-id="5a1e3-137">Update</span></span>|<span data-ttu-id="5a1e3-138">如果在块中有一个对应的 (元素，而该元素在块中有一个对应的元素，则 DiffGram 指示一个更新操作 \<before> **\<DataInstance>** ，这两个元素的**diffgr： id**属性具有相同的值) 并且使用在块中的元素上**修改**的值指定**diffgr： hasChanges**特性 **\<DataInstance>** 。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-138">The DiffGram indicates an update operation when there is an element in the \<before> block for which there is a corresponding element in the **\<DataInstance>** block (that is, both elements have a **diffgr:id** attribute with same value) and the **diffgr:hasChanges** attribute is specified with the value **modified** on the element in the **\<DataInstance>** block.</span></span><br /><br /> <span data-ttu-id="5a1e3-139">如果未在块中的元素上指定**diffgr： hasChanges**属性 **\<DataInstance>** ，处理逻辑将返回错误。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-139">If the **diffgr:hasChanges** attribute is not specified on the element in the **\<DataInstance>** block, an error is returned by the processing logic.</span></span> <span data-ttu-id="5a1e3-140">有关工作示例，请参阅[SQLXML 4.0&#41;的 DiffGram 示例 &#40;](diffgram-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-140">For working samples, see [DiffGram Examples &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md).</span></span><br /><br /> <span data-ttu-id="5a1e3-141">如果在块中指定了**diffgr： parentid** **\<before>** ，则由**parentID**指定的元素的父子关系用于确定更新记录的顺序。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-141">If **diffgr:parentID** is specified in the **\<before>** block, the parent-child relationship of elements that are specified by **parentID** are used in determining the order in which records are updated.</span></span>|  
|<span data-ttu-id="5a1e3-142">删除</span><span class="sxs-lookup"><span data-stu-id="5a1e3-142">Delete</span></span>|<span data-ttu-id="5a1e3-143">DiffGram 指示当元素出现在块中但不出现在 **\<before>** 相应的块中时的删除操作 **\<DataInstance>** 。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-143">A DiffGram indicates a delete operation when an element appears in the **\<before>** block but not in the corresponding **\<DataInstance>** block.</span></span> <span data-ttu-id="5a1e3-144">在这种情况下，DiffGram 将从数据库中删除在块中指定的记录实例 **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-144">In this case, the DiffGram deletes the record instance that is specified in the **\<before>** block from the database.</span></span> <span data-ttu-id="5a1e3-145">有关工作示例，请参阅[SQLXML 4.0&#41;的 DiffGram 示例 &#40;](diffgram-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-145">For working samples, see [DiffGram Examples &#40;SQLXML 4.0&#41;](diffgram-examples-sqlxml-4-0.md).</span></span><br /><br /> <span data-ttu-id="5a1e3-146">如果在块中指定了**diffgr： parentid** **\<before>** ，则由**parentID**指定的元素的父子关系用于确定删除记录的顺序。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-146">If **diffgr:parentID** is specified in the **\<before>** block, the parent-child relationship of elements that are specified by **parentID** are used in determining the order in which records are deleted.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="5a1e3-147">参数无法传递到 DiffGrams。</span><span class="sxs-lookup"><span data-stu-id="5a1e3-147">Parameters cannot be passed to DiffGrams.</span></span>  
  
  
