---
title: 字词查找转换 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termlookuptrans.f1
helpviewer_keywords:
- extracting data [Integration Services]
- match extracted terms [Integration Services]
- text extraction [Integration Services]
- term extractions [Integration Services]
- lookups [Integration Services]
- counting extracted items
- Term Lookup transformation
ms.assetid: 3c0fa2f8-cb6a-4371-b184-7447be001de1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a679f9e191b2b1ec54d982a715085fe5b6bddfc5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692457"
---
# <a name="term-lookup-transformation"></a><span data-ttu-id="d3f00-102">字词查找转换</span><span class="sxs-lookup"><span data-stu-id="d3f00-102">Term Lookup Transformation</span></span>
  <span data-ttu-id="d3f00-103">字词查找转换将从转换输入列的文本中提取的字词与引用表中的字词进行匹配，</span><span class="sxs-lookup"><span data-stu-id="d3f00-103">The Term Lookup transformation matches terms extracted from text in a transformation input column with terms in a reference table.</span></span> <span data-ttu-id="d3f00-104">然后计算出查找表中的字词在输入数据集中出现的次数，并将计数与引用表中的此字词一并写入转换输出的列中。</span><span class="sxs-lookup"><span data-stu-id="d3f00-104">It then counts the number of times a term in the lookup table occurs in the input data set, and writes the count together with the term from the reference table to columns in the transformation output.</span></span> <span data-ttu-id="d3f00-105">此转换对于创建基于输入文本并带有词频统计信息的自定义词列表很有用。</span><span class="sxs-lookup"><span data-stu-id="d3f00-105">This transformation is useful for creating a custom word list based on the input text, complete with word frequency statistics.</span></span>  
  
 <span data-ttu-id="d3f00-106">字词查找转换在执行查找之前，先使用与字词提取转换相同的方法从输入列的文本中提取词：</span><span class="sxs-lookup"><span data-stu-id="d3f00-106">Before the Term Lookup transformation performs a lookup, it extracts words from the text in an input column using the same method as the Term Extraction transformation:</span></span>  
  
-   <span data-ttu-id="d3f00-107">将文本分割为句子。</span><span class="sxs-lookup"><span data-stu-id="d3f00-107">Text is broken into sentences.</span></span>  
  
-   <span data-ttu-id="d3f00-108">将句子分割为词。</span><span class="sxs-lookup"><span data-stu-id="d3f00-108">Sentences are broken into words.</span></span>  
  
-   <span data-ttu-id="d3f00-109">对词进行规范。</span><span class="sxs-lookup"><span data-stu-id="d3f00-109">Words are normalized.</span></span>  
  
 <span data-ttu-id="d3f00-110">若要进一步自定义要匹配的字词，可以对字词查找转换进行配置，使其在查找匹配时区分大小写。</span><span class="sxs-lookup"><span data-stu-id="d3f00-110">To further customize which terms to match, the Term Lookup transformation can be configured to perform a case-sensitive match.</span></span>  
  
## <a name="matches"></a><span data-ttu-id="d3f00-111">匹配</span><span class="sxs-lookup"><span data-stu-id="d3f00-111">Matches</span></span>  
 <span data-ttu-id="d3f00-112">字词查找使用下列规则执行查找并返回值：</span><span class="sxs-lookup"><span data-stu-id="d3f00-112">The Term Lookup performs a lookup and returns a value using the following rules:</span></span>  
  
-   <span data-ttu-id="d3f00-113">如果转换被配置为在查找匹配项时区分大小写，那么它会放弃大小写不相符的匹配项。</span><span class="sxs-lookup"><span data-stu-id="d3f00-113">If the transformation is configured to perform case-sensitive matches, matches that fail a case-sensitive comparison are discarded.</span></span> <span data-ttu-id="d3f00-114">例如， *student* 和 *STUDENT* 将视为不同的词。</span><span class="sxs-lookup"><span data-stu-id="d3f00-114">For example, *student* and *STUDENT* are treated as separate words.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d3f00-115">非大写字与位于句首的大写字可为匹配项。</span><span class="sxs-lookup"><span data-stu-id="d3f00-115">A non-capitalized word can be matched with a word that is capitalized at the beginning of a sentence.</span></span> <span data-ttu-id="d3f00-116">例如，如果 *Student* 是句首词，则 *student* 和 *Student* 之间匹配成功。</span><span class="sxs-lookup"><span data-stu-id="d3f00-116">For example, the match between *student* and *Student* succeeds when *Student* is the first word in a sentence.</span></span>  
  
-   <span data-ttu-id="d3f00-117">如果引用表中存在名词或名词短语的复数形式，则查找仅匹配该名词或名词短语的复数形式。</span><span class="sxs-lookup"><span data-stu-id="d3f00-117">If a plural form of the noun or noun phrase exists in the reference table, the lookup matches only the plural form of the noun or noun phrase.</span></span> <span data-ttu-id="d3f00-118">例如， *students* 的所有实例将与 *student*的实例分别计数。</span><span class="sxs-lookup"><span data-stu-id="d3f00-118">For example, all instances of *students* would be counted separately from the instances of *student*.</span></span>  
  
-   <span data-ttu-id="d3f00-119">如果在引用表中只找到词的单数形式，则该词或短语的单数和复数形式都视为单数形式的匹配项。</span><span class="sxs-lookup"><span data-stu-id="d3f00-119">If only the singular form of the word is found in the reference table, both the singular and the plural forms of the word or phrase are matched to the singular form.</span></span> <span data-ttu-id="d3f00-120">例如，如果查找表包含 *student*，而转换找到两个词 *student* 和 *students*，则两个词都将计为查找字词 *student*的匹配项。</span><span class="sxs-lookup"><span data-stu-id="d3f00-120">For example, if the lookup table contains *student*, and the transformation finds the words *student* and *students*, both words would be counted as a match for the lookup term *student*.</span></span>  
  
-   <span data-ttu-id="d3f00-121">如果输入列中的文本为还原的名词短语，则规范仅影响名词短语中的最后一个词。</span><span class="sxs-lookup"><span data-stu-id="d3f00-121">If the text in the input column is a lemmatized noun phrase, only the last word in the noun phrase is affected by normalization.</span></span> <span data-ttu-id="d3f00-122">例如， *doctors appointments* 的还原形式为 *doctors appointment*。</span><span class="sxs-lookup"><span data-stu-id="d3f00-122">For example, the lemmatized version of *doctors appointments* is *doctors appointment*.</span></span>  
  
 <span data-ttu-id="d3f00-123">如果查找项包含的字词与引用集中的字词重叠，即一个子字词出现在多个引用记录中，则字词查找转换仅返回一个查找结果。</span><span class="sxs-lookup"><span data-stu-id="d3f00-123">When a lookup item contains terms that overlap in the reference set-that is, a sub-term is found in more than one reference record-the Term Lookup transformation returns only one lookup result.</span></span> <span data-ttu-id="d3f00-124">下面的示例显示查找项包含重叠子字词时的结果。</span><span class="sxs-lookup"><span data-stu-id="d3f00-124">The following example shows the result when a lookup item contains an overlapping sub-term.</span></span> <span data-ttu-id="d3f00-125">在本示例中，重叠的子字词为 *Windows*，它出现在两个引用字词中。</span><span class="sxs-lookup"><span data-stu-id="d3f00-125">The overlapping sub-term in this case is *Windows*, which is found within two reference terms.</span></span> <span data-ttu-id="d3f00-126">但是，转换并不返回两个结果，而仅返回一个引用字词 *Windows*。</span><span class="sxs-lookup"><span data-stu-id="d3f00-126">However, the transformation does not return two results, but returns only a single reference term, *Windows*.</span></span> <span data-ttu-id="d3f00-127">第二个引用字词 *Windows 7 Professional*并未返回。</span><span class="sxs-lookup"><span data-stu-id="d3f00-127">The second reference term, *Windows 7 Professional*, is not returned.</span></span>  
  
|<span data-ttu-id="d3f00-128">Item</span><span class="sxs-lookup"><span data-stu-id="d3f00-128">Item</span></span>|<span data-ttu-id="d3f00-129">值</span><span class="sxs-lookup"><span data-stu-id="d3f00-129">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="d3f00-130">输入字词</span><span class="sxs-lookup"><span data-stu-id="d3f00-130">Input term</span></span>|<span data-ttu-id="d3f00-131">Windows 7 Professional</span><span class="sxs-lookup"><span data-stu-id="d3f00-131">Windows 7 Professional</span></span>|  
|<span data-ttu-id="d3f00-132">引用字词</span><span class="sxs-lookup"><span data-stu-id="d3f00-132">Reference terms</span></span>|<span data-ttu-id="d3f00-133">Windows、Windows 7 Professional</span><span class="sxs-lookup"><span data-stu-id="d3f00-133">Windows, Windows 7 Professional</span></span>|  
|<span data-ttu-id="d3f00-134">输出</span><span class="sxs-lookup"><span data-stu-id="d3f00-134">Output</span></span>|<span data-ttu-id="d3f00-135">Windows</span><span class="sxs-lookup"><span data-stu-id="d3f00-135">Windows</span></span>|  
  
 <span data-ttu-id="d3f00-136">字词查找转换可以匹配包含特殊字符的名词和名词短语，而引用表中的数据可能包含这些字符。</span><span class="sxs-lookup"><span data-stu-id="d3f00-136">The Term Lookup transformation can match nouns and noun phrases that contain special characters, and the data in the reference table may include these characters.</span></span> <span data-ttu-id="d3f00-137">特殊字符如下所示：%、@，&、$、#、\*、:、;、.、,、!、?、\<, >、+、=、^、~、|、\\、/、(、)、[、]、{、}、" 和 '。</span><span class="sxs-lookup"><span data-stu-id="d3f00-137">The special characters are as follows: %, @, &, $, #, \*, :, ;, ., **,** , !, ?, \<, >, +, =, ^, ~, |, \\, /, (, ), [, ], {, }, ", and '.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="d3f00-138">数据类型</span><span class="sxs-lookup"><span data-stu-id="d3f00-138">Data Types</span></span>  
 <span data-ttu-id="d3f00-139">字词查找转换只能使用数据类型为 DT_WSTR 或 DT_NTEXT 的列。</span><span class="sxs-lookup"><span data-stu-id="d3f00-139">The Term Lookup transformation can only use a column that has either the DT_WSTR or the DT_NTEXT data type.</span></span> <span data-ttu-id="d3f00-140">如果列包含文本，但不具有这两种数据类型之一，则数据转换可以将数据类型为 DT_WSTR 或 DT_NTEXT 的列添加到数据流，并将列值复制到新列。</span><span class="sxs-lookup"><span data-stu-id="d3f00-140">If a column contains text, but does not have one of these data types, the Data Conversion transformation can add a column with the DT_WSTR or DT_NTEXT data type to the data flow and copy the column values to the new column.</span></span> <span data-ttu-id="d3f00-141">然后，数据转换的输出就可以用作字词查找转换的输入。</span><span class="sxs-lookup"><span data-stu-id="d3f00-141">The output from the Data Conversion transformation can then be used as the input to the Term Lookup transformation.</span></span> <span data-ttu-id="d3f00-142">有关详细信息，请参阅 [Data Conversion Transformation](data-conversion-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="d3f00-142">For more information, see [Data Conversion Transformation](data-conversion-transformation.md).</span></span>  
  
## <a name="configuration-the-term-lookup-transformation"></a><span data-ttu-id="d3f00-143">字词查找转换的配置</span><span class="sxs-lookup"><span data-stu-id="d3f00-143">Configuration the Term Lookup Transformation</span></span>  
 <span data-ttu-id="d3f00-144">字词查找转换输入列包含 InputColumnType 属性，用于指示该列的用途。</span><span class="sxs-lookup"><span data-stu-id="d3f00-144">The Term Lookup transformation input columns includes the InputColumnType property, which indicates the use of the column.</span></span> <span data-ttu-id="d3f00-145">InputColumnType 可能包含以下值：</span><span class="sxs-lookup"><span data-stu-id="d3f00-145">InputColumnType can contain the following values:</span></span>  
  
-   <span data-ttu-id="d3f00-146">值 0 指示将列仅传递到输出，而不在查找中使用。</span><span class="sxs-lookup"><span data-stu-id="d3f00-146">The value 0 indicates the column is passed through to the output only and is not used in the lookup.</span></span>  
  
-   <span data-ttu-id="d3f00-147">值 1 指示仅在查找中使用列。</span><span class="sxs-lookup"><span data-stu-id="d3f00-147">The value 1 indicates the column is used in the lookup only.</span></span>  
  
-   <span data-ttu-id="d3f00-148">值 2 指示将列传递到输出，并在查找中使用列。</span><span class="sxs-lookup"><span data-stu-id="d3f00-148">The value 2 indicates the column is passed through to the output, and is also used in the lookup.</span></span>  
  
 <span data-ttu-id="d3f00-149">InputColumnType 属性设置为 0 或 2 的转换输出列包含列的 CustomLineageID 属性，该属性包含由上游数据流组件分配给列的沿袭标识符。</span><span class="sxs-lookup"><span data-stu-id="d3f00-149">Transformation output columns whose InputColumnType property is set to 0 or 2 include the CustomLineageID property for a column, which contains the lineage identifier assigned to the column by an upstream data flow component.</span></span>  
  
 <span data-ttu-id="d3f00-150">字词查找转换还将两列添加到转换输出，默认名称分别为 `Term` 和 `Frequency`。</span><span class="sxs-lookup"><span data-stu-id="d3f00-150">The Term Lookup transformation adds two columns to the transformation output, named by default `Term` and `Frequency`.</span></span> <span data-ttu-id="d3f00-151">`Term` 包含查找表中的字词，而 `Frequency` 包含引用表中的字词在输入数据集中出现的次数。</span><span class="sxs-lookup"><span data-stu-id="d3f00-151">`Term` contains a term from the lookup table and `Frequency` contains the number of times the term in the reference table occurs in the input data set.</span></span> <span data-ttu-id="d3f00-152">这些列不包含 CustomLineageID 属性。</span><span class="sxs-lookup"><span data-stu-id="d3f00-152">These columns do not include the CustomLineageID property.</span></span>  
  
 <span data-ttu-id="d3f00-153">查找表必须是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 或 Access 数据库中的表。</span><span class="sxs-lookup"><span data-stu-id="d3f00-153">The lookup table must be a table in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or an Access database.</span></span> <span data-ttu-id="d3f00-154">如果将字词提取转换的输出保存到表，则可以使用此表作为引用表，但也可以使用其他表。</span><span class="sxs-lookup"><span data-stu-id="d3f00-154">If the output of the Term Extraction transformation is saved to a table, this table can be used as the reference table, but other tables can also be used.</span></span> <span data-ttu-id="d3f00-155">必须先将平面文件中、Excel 工作簿或其他源的文本导入到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库或 Access 数据库，然后才能使用字词查找转换。</span><span class="sxs-lookup"><span data-stu-id="d3f00-155">Text in flat files, Excel workbooks or other sources must be imported to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database or an Access database before you can use the Term Lookup transformation.</span></span>  
  
 <span data-ttu-id="d3f00-156">字词查找转换使用单独的 OLE DB 连接来连接到引用表。</span><span class="sxs-lookup"><span data-stu-id="d3f00-156">The Term Lookup transformation uses a separate OLE DB connection to connect to the reference table.</span></span> <span data-ttu-id="d3f00-157">有关详细信息，请参阅 [OLE DB Connection Manager](../../connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="d3f00-157">For more information, see [OLE DB Connection Manager](../../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="d3f00-158">字词查找转换以完全预缓存模式工作。</span><span class="sxs-lookup"><span data-stu-id="d3f00-158">The Term Lookup transformation works in a fully precached mode.</span></span> <span data-ttu-id="d3f00-159">运行时，字词查找转换先从引用表中读取字词并将其存储到自己的专用内存，然后再处理转换输入行。</span><span class="sxs-lookup"><span data-stu-id="d3f00-159">At run time, the Term Lookup transformation reads the terms from the reference table and stores them in its private memory before it processes any transformation input rows.</span></span>  
  
 <span data-ttu-id="d3f00-160">因为输入列行中的字词可能重复，所以字词查找转换的输出通常具有比转换输入更多的行。</span><span class="sxs-lookup"><span data-stu-id="d3f00-160">Because the terms in an input column row may repeat, the output of the Term Lookup transformation typically has more rows than the transformation input.</span></span>  
  
 <span data-ttu-id="d3f00-161">此转换具有一个输入和一个输出。</span><span class="sxs-lookup"><span data-stu-id="d3f00-161">The transformation has one input and one output.</span></span> <span data-ttu-id="d3f00-162">它不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="d3f00-162">It does not support error outputs.</span></span>  
  
 <span data-ttu-id="d3f00-163">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="d3f00-163">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="d3f00-164">有关可在 **“字词查找转换编辑器”** 对话框中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="d3f00-164">For more information about the properties that you can set in the **Term Lookup Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d3f00-165">字词查找转换编辑器（“引用表”选项卡）</span><span class="sxs-lookup"><span data-stu-id="d3f00-165">Term Lookup Transformation Editor &#40;Reference Table Tab&#41;</span></span>](../../term-lookup-transformation-editor-reference-table-tab.md)  
  
-   [<span data-ttu-id="d3f00-166">字词查找转换编辑器（“字词查找”选项卡）</span><span class="sxs-lookup"><span data-stu-id="d3f00-166">Term Lookup Transformation Editor &#40;Term Lookup Tab&#41;</span></span>](../../term-lookup-transformation-editor-term-lookup-tab.md)  
  
-   [<span data-ttu-id="d3f00-167">字词查找转换编辑器（“高级”选项卡）</span><span class="sxs-lookup"><span data-stu-id="d3f00-167">Term Lookup Transformation Editor &#40;Advanced Tab&#41;</span></span>](../../term-lookup-transformation-editor-advanced-tab.md)  
  
 <span data-ttu-id="d3f00-168">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="d3f00-168">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d3f00-169">Common Properties</span><span class="sxs-lookup"><span data-stu-id="d3f00-169">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="d3f00-170">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="d3f00-170">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="d3f00-171">有关如何设置属性的详细信息，请参阅 [设置数据流组件的属性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="d3f00-171">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
