---
title: 模糊分组转换 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtrans.f1
helpviewer_keywords:
- cleaning data
- comparing data
- token delimiters [Integration Services]
- temporary indexes [Integration Services]
- Fuzzy Grouping transformation
- temporary tables [Integration Services]
- grouping data
- standardizing data [Integration Services]
- columns [Integration Services], standardizing
- similarity thresholds [Integration Services]
- data cleaning [Integration Services]
- duplicate data [Integration Services]
ms.assetid: e43f17bd-9d13-4a8f-9f29-cce44cac1025
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f26948b4046d31aff934db539a3878cad99ac1ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578971"
---
# <a name="fuzzy-grouping-transformation"></a><span data-ttu-id="ed619-102">模糊分组转换</span><span class="sxs-lookup"><span data-stu-id="ed619-102">Fuzzy Grouping Transformation</span></span>
  <span data-ttu-id="ed619-103">模糊分组转换执行数据清理任务，它首先查找可能重复的数据行，然后选择要在对数据进行标准化的过程中使用的规范数据行。</span><span class="sxs-lookup"><span data-stu-id="ed619-103">The Fuzzy Grouping transformation performs data cleaning tasks by identifying rows of data that are likely to be duplicates and selecting a canonical row of data to use in standardizing the data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ed619-104">有关模糊分组转换（包括性能和内存限制）的详细信息，请参阅白皮书 [SQL Server Integration Services 2005 中的模糊查找和模糊分组](https://go.microsoft.com/fwlink/?LinkId=96604)。</span><span class="sxs-lookup"><span data-stu-id="ed619-104">For more detailed information about the Fuzzy Grouping transformation, including performance and memory limitations, see the white paper, [Fuzzy Lookup and Fuzzy Grouping in SQL Server Integration Services 2005](https://go.microsoft.com/fwlink/?LinkId=96604).</span></span>  
  
 <span data-ttu-id="ed619-105">模糊分组转换要求与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的实例建立连接，以创建该转换算法完成工作所需的临时 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 表。</span><span class="sxs-lookup"><span data-stu-id="ed619-105">The Fuzzy Grouping transformation requires a connection to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to create the temporary [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables that the transformation algorithm requires to do its work.</span></span> <span data-ttu-id="ed619-106">该连接必须解析为有权在数据库中创建表的用户。</span><span class="sxs-lookup"><span data-stu-id="ed619-106">The connection must resolve to a user who has permission to create tables in the database.</span></span>  
  
 <span data-ttu-id="ed619-107">若要配置该转换，必须选择要在确定重复项时使用的输入列，而且必须为每列选择匹配类型（模糊匹配或完全匹配）。</span><span class="sxs-lookup"><span data-stu-id="ed619-107">To configure the transformation, you must select the input columns to use when identifying duplicates, and you must select the type of match-fuzzy or exact-for each column.</span></span> <span data-ttu-id="ed619-108">完全匹配保证只对该列中具有相同值的行进行分组。</span><span class="sxs-lookup"><span data-stu-id="ed619-108">An exact match guarantees that only rows that have identical values in that column will be grouped.</span></span> <span data-ttu-id="ed619-109">完全匹配可以应用到除 DT_TEXT、DT_NTEXT 和 DT_IMAGE 之外的任何 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 数据类型的列。</span><span class="sxs-lookup"><span data-stu-id="ed619-109">Exact matching can be applied to columns of any [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] data type except DT_TEXT, DT_NTEXT, and DT_IMAGE.</span></span> <span data-ttu-id="ed619-110">模糊匹配对具有相似值的行进行分组。</span><span class="sxs-lookup"><span data-stu-id="ed619-110">A fuzzy match groups rows that have approximately the same values.</span></span> <span data-ttu-id="ed619-111">近似匹配数据的方法基于用户指定的相似性得分。</span><span class="sxs-lookup"><span data-stu-id="ed619-111">The method for approximate matching of data is based on a user-specified similarity score.</span></span> <span data-ttu-id="ed619-112">在模糊匹配中，只能使用具有 DT_WSTR 和 DT_STR 数据类型的列。</span><span class="sxs-lookup"><span data-stu-id="ed619-112">Only columns with the DT_WSTR and DT_STR data types can be used in fuzzy matching.</span></span> <span data-ttu-id="ed619-113">有关详细信息，请参阅 [Integration Services 数据类型](../integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="ed619-113">For more information, see [Integration Services Data Types](../integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="ed619-114">该转换输出包括所有输入列、一个或多个具有标准化数据的列以及一个包含相似性得分的列。</span><span class="sxs-lookup"><span data-stu-id="ed619-114">The transformation output includes all input columns, one or more columns with standardized data, and a column that contains the similarity score.</span></span> <span data-ttu-id="ed619-115">该得分是一个介于 0 和 1 之间的小数值。</span><span class="sxs-lookup"><span data-stu-id="ed619-115">The score is a decimal value between 0 and 1.</span></span> <span data-ttu-id="ed619-116">规范行的得分为 1。</span><span class="sxs-lookup"><span data-stu-id="ed619-116">The canonical row has a score of 1.</span></span> <span data-ttu-id="ed619-117">模糊组中其他行具有的得分指明该行与规范行的匹配程度。</span><span class="sxs-lookup"><span data-stu-id="ed619-117">Other rows in the fuzzy group have scores that indicate how well the row matches the canonical row.</span></span> <span data-ttu-id="ed619-118">得分越接近 1，行与规范行的匹配程度越高。</span><span class="sxs-lookup"><span data-stu-id="ed619-118">The closer the score is to 1, the more closely the row matches the canonical row.</span></span> <span data-ttu-id="ed619-119">如果模糊组包括与规范行完全匹配的行，则这些行的得分也为 1。</span><span class="sxs-lookup"><span data-stu-id="ed619-119">If the fuzzy group includes rows that are exact duplicates of the canonical row, these rows also have a score of 1.</span></span> <span data-ttu-id="ed619-120">该转换不删除这些重复的行；它通过创建一个将规范行与相似行关联的键对重复行进行分组。</span><span class="sxs-lookup"><span data-stu-id="ed619-120">The transformation does not remove duplicate rows; it groups them by creating a key that relates the canonical row to similar rows.</span></span>  
  
 <span data-ttu-id="ed619-121">该转换为每个输入行产生一个输出行，同时还包括下面的附加列：</span><span class="sxs-lookup"><span data-stu-id="ed619-121">The transformation produces one output row for each input row, with the following additional columns:</span></span>  
  
-   <span data-ttu-id="ed619-122">**_key_in**，唯一标识每行的列。</span><span class="sxs-lookup"><span data-stu-id="ed619-122">**_key_in**, a column that uniquely identifies each row.</span></span>  
  
-   <span data-ttu-id="ed619-123">**_key_out**，标识一组重复行的列。</span><span class="sxs-lookup"><span data-stu-id="ed619-123">**_key_out**, a column that identifies a group of duplicate rows.</span></span> <span data-ttu-id="ed619-124">在规范数据行中， **_key_out** 列的值就是 **_key_in** 列。</span><span class="sxs-lookup"><span data-stu-id="ed619-124">The **_key_out** column has the value of the **_key_in** column in the canonical data row.</span></span> <span data-ttu-id="ed619-125">**_key_out** 中的值相同的行属于同一个组。</span><span class="sxs-lookup"><span data-stu-id="ed619-125">Rows with the same value in **_key_out** are part of the same group.</span></span> <span data-ttu-id="ed619-126">组的 **_key_out**值对应于规范数据行中 **_key_in** 值。</span><span class="sxs-lookup"><span data-stu-id="ed619-126">The **_key_out**value for a group corresponds to the value of **_key_in** in the canonical data row.</span></span>  
  
-   <span data-ttu-id="ed619-127">**_score**，一个介于 0 和 1 之间的值，指示输入行与规范行之间的相似性。</span><span class="sxs-lookup"><span data-stu-id="ed619-127">**_score**, a value between 0 and 1 that indicates the similarity of the input row to the canonical row.</span></span>  
  
 <span data-ttu-id="ed619-128">这些都是默认列名，您可以将模糊分组转换配置为使用其他名称。</span><span class="sxs-lookup"><span data-stu-id="ed619-128">These are the default column names and you can configure the Fuzzy Grouping transformation to use other names.</span></span> <span data-ttu-id="ed619-129">输出还提供了参与模糊分组的每列的相似性得分。</span><span class="sxs-lookup"><span data-stu-id="ed619-129">The output also provides a similarity score for each column that participates in a fuzzy grouping.</span></span>  
  
 <span data-ttu-id="ed619-130">模糊分组转换包括两个用于自定义所执行的分组的功能：标记分隔符和相似性阈值。</span><span class="sxs-lookup"><span data-stu-id="ed619-130">The Fuzzy Grouping transformation includes two features for customizing the grouping it performs: token delimiters and similarity threshold.</span></span> <span data-ttu-id="ed619-131">该转换提供了一组用于对数据进行词汇切分的默认分隔符，但您可以添加新的分隔符以改善您数据的词汇切分。</span><span class="sxs-lookup"><span data-stu-id="ed619-131">The transformation provides a default set of delimiters used to tokenize the data, but you can add new delimiters that improve the tokenization of your data.</span></span>  
  
 <span data-ttu-id="ed619-132">相似性阈值指示该转换标识重复项的严格程度。</span><span class="sxs-lookup"><span data-stu-id="ed619-132">The similarity threshold indicates how strictly the transformation identifies duplicates.</span></span> <span data-ttu-id="ed619-133">相似性阈值可以在组件级和列级设置。</span><span class="sxs-lookup"><span data-stu-id="ed619-133">The similarity thresholds can be set at the component and the column levels.</span></span> <span data-ttu-id="ed619-134">列级相似性阈值只适用于执行模糊匹配的列。</span><span class="sxs-lookup"><span data-stu-id="ed619-134">The column-level similarity threshold is only available to columns that perform a fuzzy match.</span></span> <span data-ttu-id="ed619-135">相似性范围是 0 到 1。</span><span class="sxs-lookup"><span data-stu-id="ed619-135">The similarity range is 0 to 1.</span></span> <span data-ttu-id="ed619-136">阈值越接近 1，则行和列必须越相似，才能被认定为重复。</span><span class="sxs-lookup"><span data-stu-id="ed619-136">The closer to 1 the threshold is, the more similar the rows and columns must be to qualify as duplicates.</span></span> <span data-ttu-id="ed619-137">通过在组件级和列级别设置 MinSimilarity 属性，可以指定行和列之间的相似性阈值。</span><span class="sxs-lookup"><span data-stu-id="ed619-137">You specify the similarity threshold among rows and columns by setting the MinSimilarity property at the component and column levels.</span></span> <span data-ttu-id="ed619-138">为了满足在组件级指定的相似性，所有列的所有行都必须具有大于或等于在组件级所指定的相似性阈值的相似性。</span><span class="sxs-lookup"><span data-stu-id="ed619-138">To satisfy the similarity that is specified at the component level, all rows must have a similarity across all columns that is greater than or equal to the similarity threshold that is specified at the component level.</span></span>  
  
 <span data-ttu-id="ed619-139">模糊分组转换计算相似性的内部度量值，如果行的相似性低于 MinSimilarity 中指定的值，则不对这些行进行分组。</span><span class="sxs-lookup"><span data-stu-id="ed619-139">The Fuzzy Grouping transformation calculates internal measures of similarity, and rows that are less similar than the value specified in MinSimilarity are not grouped.</span></span>  
  
 <span data-ttu-id="ed619-140">若要确定适合您数据的相似性阈值，您可能需要使用不同的最低相似性阈值多次应用模糊分组转换。</span><span class="sxs-lookup"><span data-stu-id="ed619-140">To identify a similarity threshold that works for your data, you may have to apply the Fuzzy Grouping transformation several times using different minimum similarity thresholds.</span></span> <span data-ttu-id="ed619-141">在运行时，转换输出中的得分列包含组中每行的相似性得分。</span><span class="sxs-lookup"><span data-stu-id="ed619-141">At run time, the score columns in transformation output contain the similarity scores for each row in a group.</span></span> <span data-ttu-id="ed619-142">您可以使用这些值来确定适合您数据的相似性阈值。</span><span class="sxs-lookup"><span data-stu-id="ed619-142">You can use these values to identify the similarity threshold that is appropriate for your data.</span></span> <span data-ttu-id="ed619-143">如果要增加相似性，应该将 MinSimilarity 设置为一个大于得分列中所示值的值。</span><span class="sxs-lookup"><span data-stu-id="ed619-143">If you want to increase similarity, you should set MinSimilarity to a value larger than the value in the score columns.</span></span>  
  
 <span data-ttu-id="ed619-144">您可以通过设置模糊分组转换输入中的列属性来自定义该转换所执行的分组。</span><span class="sxs-lookup"><span data-stu-id="ed619-144">You can customize the grouping that the transformation performs by setting the properties of the columns in the Fuzzy Grouping transformation input.</span></span> <span data-ttu-id="ed619-145">例如，FuzzyComparisonFlags 属性指定该转换如何比较列中的字符串数据，ExactFuzzy 属性指定该转换是执行模糊匹配还是执行完全匹配。</span><span class="sxs-lookup"><span data-stu-id="ed619-145">For example, the FuzzyComparisonFlags property specifies how the transformation compares the string data in a column, and the ExactFuzzy property specifies whether the transformation performs a fuzzy match or an exact match.</span></span>  
  
 <span data-ttu-id="ed619-146">可以通过设置 MaxMemoryUsage 自定义属性来配置模糊分组转换所使用的内存数量。</span><span class="sxs-lookup"><span data-stu-id="ed619-146">The amount of memory that the Fuzzy Grouping transformation uses can be configured by setting the MaxMemoryUsage custom property.</span></span> <span data-ttu-id="ed619-147">可以指定 MB 数，或使用值 0 以允许转换基于其需要和可用物理内存而使用动态内存数量。</span><span class="sxs-lookup"><span data-stu-id="ed619-147">You can specify the number of megabytes (MB) or use the value 0 to allow the transformation to use a dynamic amount of memory based on its needs and the physical memory available.</span></span> <span data-ttu-id="ed619-148">加载包时，可以通过属性表达式来更新 MaxMemoryUsage 自定义属性。</span><span class="sxs-lookup"><span data-stu-id="ed619-148">The MaxMemoryUsage custom property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="ed619-149">有关详细信息，请参阅 [Integration Services (SSIS) 表达式](../../expressions/integration-services-ssis-expressions.md)、[在包中使用属性表达式](../../expressions/use-property-expressions-in-packages.md)和[转换自定义属性](transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="ed619-149">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="ed619-150">此转换有一个输入和一个输出。</span><span class="sxs-lookup"><span data-stu-id="ed619-150">This transformation has one input and one output.</span></span> <span data-ttu-id="ed619-151">它不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="ed619-151">It does not support an error output.</span></span>  
  
## <a name="row-comparison"></a><span data-ttu-id="ed619-152">行比较</span><span class="sxs-lookup"><span data-stu-id="ed619-152">Row Comparison</span></span>  
 <span data-ttu-id="ed619-153">在配置模糊分组转换时，可以指定该转换比较转换输入中的行所用的算法。</span><span class="sxs-lookup"><span data-stu-id="ed619-153">When you configure the Fuzzy Grouping transformation, you can specify the comparison algorithm that the transformation uses to compare rows in the transformation input.</span></span> <span data-ttu-id="ed619-154">如果将 "穷举" 属性设置为 `true` ，则转换会将输入中的每一行与输入中的每个其他行进行比较。</span><span class="sxs-lookup"><span data-stu-id="ed619-154">If you set the Exhaustive property to `true`, the transformation compares every row in the input to every other row in the input.</span></span> <span data-ttu-id="ed619-155">这种比较算法可以生成更准确的结果，但是除非输入中的行数很少，否则很有可能使转换的执行速度变得很慢。</span><span class="sxs-lookup"><span data-stu-id="ed619-155">This comparison algorithm may produce more accurate results, but it is likely to make the transformation perform more slowly unless the number of rows in the input is small.</span></span> <span data-ttu-id="ed619-156">若要避免性能问题，最好将详尽的属性设置为 `true` 仅在包开发期间进行设置。</span><span class="sxs-lookup"><span data-stu-id="ed619-156">To avoid performance issues, it is advisable to set the Exhaustive property to `true` only during package development.</span></span>  
  
## <a name="temporary-tables-and-indexes"></a><span data-ttu-id="ed619-157">临时表和索引</span><span class="sxs-lookup"><span data-stu-id="ed619-157">Temporary Tables and Indexes</span></span>  
 <span data-ttu-id="ed619-158">在运行时，模糊分组转换会在该转换所连接到的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库中创建临时对象，例如表和索引，这些表和索引可能会非常大。</span><span class="sxs-lookup"><span data-stu-id="ed619-158">At run time, the Fuzzy Grouping transformation creates temporary objects such as tables and indexes, potentially of significant size, in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database that the transformation connects to.</span></span> <span data-ttu-id="ed619-159">表和索引的大小与转换输入中的行数和模糊分组转换所创建的标记数成比例。</span><span class="sxs-lookup"><span data-stu-id="ed619-159">The size of the tables and indexes are proportional to the number of rows in the transformation input and the number of tokens created by the Fuzzy Grouping transformation.</span></span>  
  
 <span data-ttu-id="ed619-160">该转换也会查询这些临时表。</span><span class="sxs-lookup"><span data-stu-id="ed619-160">The transformation also queries the temporary tables.</span></span> <span data-ttu-id="ed619-161">因此，应该考虑将模糊分组转换连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的非生产实例中，在生产服务器只有有限的可用磁盘空间时，尤其应该如此。</span><span class="sxs-lookup"><span data-stu-id="ed619-161">You should therefore consider connecting the Fuzzy Grouping transformation to a non-production instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], especially if the production server has limited disk space available.</span></span>  
  
 <span data-ttu-id="ed619-162">如果此转换所使用的表和索引位于本地计算机，则此转换的性能可能会提高。</span><span class="sxs-lookup"><span data-stu-id="ed619-162">The performance of this transformation may improve if the tables and indexes it uses are located on the local computer.</span></span>  
  
## <a name="configuration-of-the-fuzzy-grouping-transformation"></a><span data-ttu-id="ed619-163">配置模糊分组转换</span><span class="sxs-lookup"><span data-stu-id="ed619-163">Configuration of the Fuzzy Grouping Transformation</span></span>  
 <span data-ttu-id="ed619-164">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="ed619-164">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="ed619-165">有关可以在 **“模糊分组转换编辑器”** 对话框中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="ed619-165">For more information about the properties that you can set in the **Fuzzy Grouping Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="ed619-166">模糊分组转换编辑器（“连接管理器”选项卡）</span><span class="sxs-lookup"><span data-stu-id="ed619-166">Fuzzy Grouping Transformation Editor &#40;Connection Manager Tab&#41;</span></span>](../../fuzzy-grouping-transformation-editor-connection-manager-tab.md)  
  
-   [<span data-ttu-id="ed619-167">模糊分组转换编辑器（“列”选项卡）</span><span class="sxs-lookup"><span data-stu-id="ed619-167">Fuzzy Grouping Transformation Editor &#40;Columns Tab&#41;</span></span>](../../fuzzy-grouping-transformation-editor-columns-tab.md)  
  
-   [<span data-ttu-id="ed619-168">模糊分组转换编辑器（“高级”选项卡）</span><span class="sxs-lookup"><span data-stu-id="ed619-168">Fuzzy Grouping Transformation Editor &#40;Advanced Tab&#41;</span></span>](../../fuzzy-grouping-transformation-editor-advanced-tab.md)  
  
 <span data-ttu-id="ed619-169">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="ed619-169">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="ed619-170">Common Properties</span><span class="sxs-lookup"><span data-stu-id="ed619-170">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="ed619-171">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="ed619-171">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="ed619-172">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="ed619-172">Related Tasks</span></span>  
 <span data-ttu-id="ed619-173">有关如何设置此任务的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="ed619-173">For details about how to set properties of this task, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="ed619-174">使用模糊分组转换标识相似数据行</span><span class="sxs-lookup"><span data-stu-id="ed619-174">Identify Similar Data Rows by Using the Fuzzy Grouping Transformation</span></span>](fuzzy-grouping-transformation.md)  
  
-   [<span data-ttu-id="ed619-175">设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="ed619-175">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="see-also"></a><span data-ttu-id="ed619-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ed619-176">See Also</span></span>  
 <span data-ttu-id="ed619-177">[模糊查找转换](lookup-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="ed619-177">[Fuzzy Lookup Transformation](lookup-transformation.md) </span></span>  
 [<span data-ttu-id="ed619-178">Integration Services 转换</span><span class="sxs-lookup"><span data-stu-id="ed619-178">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
