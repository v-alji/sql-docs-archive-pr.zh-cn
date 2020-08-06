---
title: 表列属性 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65558
- vdtsql.chm:69657
- vdt.ppg.columns
ms.assetid: 09830897-cc10-46b8-95f5-e0e9681b668c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1894b074491af1962d2180337288e188d41b2951
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591825"
---
# <a name="table-column-properties-sql-server-management-studio"></a><span data-ttu-id="19013-102">表列属性 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="19013-102">Table Column Properties (SQL Server Management Studio)</span></span>
  <span data-ttu-id="19013-103">这些属性显示在表设计器的底部窗格中。</span><span class="sxs-lookup"><span data-stu-id="19013-103">These properties appear in the bottom pane of Table Designer.</span></span> <span data-ttu-id="19013-104">除非另行说明，否则在选定列后可以在“属性”窗口中编辑这些属性。</span><span class="sxs-lookup"><span data-stu-id="19013-104">Unless otherwise noted, you can edit these properties in the Properties window when the column is selected.</span></span> <span data-ttu-id="19013-105">**“列属性”** 可以按类别或字母顺序显示。</span><span class="sxs-lookup"><span data-stu-id="19013-105">The **Column Properties** can be displayed in categories or alphabetically.</span></span> <span data-ttu-id="19013-106">许多属性仅针对特定的数据类型显示或有所更改。</span><span class="sxs-lookup"><span data-stu-id="19013-106">Many properties only appear or can only be changed for certain data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19013-107">如果表是为复制发布的，则必须使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理对象 (SMO) 对架构进行更改。</span><span class="sxs-lookup"><span data-stu-id="19013-107">If the table is published for replication, you must make schema changes using the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO).</span></span> <span data-ttu-id="19013-108">使用表设计器或数据库关系图设计器更改架构后，会尝试删除并重新创建表。</span><span class="sxs-lookup"><span data-stu-id="19013-108">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="19013-109">由于您不能删除已发布的对象，因此架构更改将失败。</span><span class="sxs-lookup"><span data-stu-id="19013-109">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
 <span data-ttu-id="19013-110">**常规**</span><span class="sxs-lookup"><span data-stu-id="19013-110">**General**</span></span>  
 <span data-ttu-id="19013-111">展开此项可显示“名称”  、“允许空值”  、“数据类型”  、“默认值或绑定”  、“长度”  、“精度”  和“小数位数”  。</span><span class="sxs-lookup"><span data-stu-id="19013-111">Expands to show **Name**, **Allow Nulls**, **Data Type**, **Default Value or Binding**, **Length**, **Precision**, and **Scale**.</span></span>  
  
 <span data-ttu-id="19013-112">**名称**</span><span class="sxs-lookup"><span data-stu-id="19013-112">**Name**</span></span>  
 <span data-ttu-id="19013-113">显示所选列的名称。</span><span class="sxs-lookup"><span data-stu-id="19013-113">Displays the name of the selected column.</span></span>  
  
 <span data-ttu-id="19013-114">**允许 Null 值**</span><span class="sxs-lookup"><span data-stu-id="19013-114">**Allow Nulls**</span></span>  
 <span data-ttu-id="19013-115">指示此列是否允许空值。</span><span class="sxs-lookup"><span data-stu-id="19013-115">Indicates whether this column allows nulls.</span></span> <span data-ttu-id="19013-116">若要编辑此属性，请在表设计器的顶部窗格中单击与列对应的“允许空值”复选框。</span><span class="sxs-lookup"><span data-stu-id="19013-116">To edit this property, click the Allow Nulls checkbox corresponding to the column in the top pane of Table Designer.</span></span>  
  
 <span data-ttu-id="19013-117">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="19013-117">**Data Type**</span></span>  
 <span data-ttu-id="19013-118">显示所选列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="19013-118">Displays the data type for the selected column.</span></span> <span data-ttu-id="19013-119">若要编辑此属性，请单击该属性的值，展开下拉列表，然后选择其他值。</span><span class="sxs-lookup"><span data-stu-id="19013-119">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
 <span data-ttu-id="19013-120">**默认值或绑定**</span><span class="sxs-lookup"><span data-stu-id="19013-120">**Default Value or Binding**</span></span>  
 <span data-ttu-id="19013-121">当没有为此列指定值时显示此列的默认值。</span><span class="sxs-lookup"><span data-stu-id="19013-121">Displays the default for this column whenever no value is specified for this column.</span></span> <span data-ttu-id="19013-122">此字段的值可以是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 默认约束的值，也可以是此列被绑定到的全局约束的名称。</span><span class="sxs-lookup"><span data-stu-id="19013-122">The value of this field can be either the value of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] default constraint or the name of a global constraint to which the column is bound.</span></span> <span data-ttu-id="19013-123">该下拉列表中包含数据库中定义的所有全局默认值。</span><span class="sxs-lookup"><span data-stu-id="19013-123">The drop-down list contains all global defaults defined in the database.</span></span> <span data-ttu-id="19013-124">若要将该列绑定到某个全局默认值，请从下拉列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="19013-124">To bind the column to a global default, select from the drop-down list.</span></span> <span data-ttu-id="19013-125">另外，若要为该列创建默认约束，请直接以文本格式键入默认值。</span><span class="sxs-lookup"><span data-stu-id="19013-125">Alternatively, to create a default constraint for the column, type the default value directly as text.</span></span>  
  
 <span data-ttu-id="19013-126">**长度**</span><span class="sxs-lookup"><span data-stu-id="19013-126">**Length**</span></span>  
 <span data-ttu-id="19013-127">显示基于字符的数据类型所允许的字符数。</span><span class="sxs-lookup"><span data-stu-id="19013-127">Shows the number of characters allowed for character-based data types.</span></span> <span data-ttu-id="19013-128">此属性仅可用于基于字符的数据类型。</span><span class="sxs-lookup"><span data-stu-id="19013-128">This property is only available for character-based data types</span></span>  
  
 <span data-ttu-id="19013-129">**缩放**</span><span class="sxs-lookup"><span data-stu-id="19013-129">**Scale**</span></span>  
 <span data-ttu-id="19013-130">显示此列中的值小数点右侧可以允许的最大位数。</span><span class="sxs-lookup"><span data-stu-id="19013-130">Displays the maximum number of digits that can appear to the right of the decimal point for values of this column.</span></span> <span data-ttu-id="19013-131">对于非数值数据类型，此属性显示 **0** 。</span><span class="sxs-lookup"><span data-stu-id="19013-131">This property shows **0** for nonnumeric data types.</span></span>  
  
 <span data-ttu-id="19013-132">**精度**</span><span class="sxs-lookup"><span data-stu-id="19013-132">**Precision**</span></span>  
 <span data-ttu-id="19013-133">显示此列中的值的最大位数。</span><span class="sxs-lookup"><span data-stu-id="19013-133">Displays the maximum number of digits for values in this column.</span></span> <span data-ttu-id="19013-134">对于非数值数据类型，此属性显示 **0** 。</span><span class="sxs-lookup"><span data-stu-id="19013-134">This property shows **0** for nonnumeric data types.</span></span>  
  
 <span data-ttu-id="19013-135">**表设计器**</span><span class="sxs-lookup"><span data-stu-id="19013-135">**Table Designer**</span></span>  
 <span data-ttu-id="19013-136">展开“表设计器”  部分。</span><span class="sxs-lookup"><span data-stu-id="19013-136">Expands the **Table Designer** section.</span></span>  
  
 <span data-ttu-id="19013-137">**排序规则**</span><span class="sxs-lookup"><span data-stu-id="19013-137">**Collation**</span></span>  
 <span data-ttu-id="19013-138">显示当使用列值对查询结果的行进行排序时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 默认情况下对列应用的排序规则顺序。</span><span class="sxs-lookup"><span data-stu-id="19013-138">Displays the collating sequence that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applies by default to the column whenever the column values are used to sort rows of a query result.</span></span> <span data-ttu-id="19013-139">若要编辑排序规则，请选择该属性，单击属性值右侧显示的省略号 (   )，以打开“排序规则”  对话框。</span><span class="sxs-lookup"><span data-stu-id="19013-139">To edit the collation, select the property, click the ellipsis (   ) that appears to the right of the property value to bring up the **Collation** dialog box.</span></span>  
  
 <span data-ttu-id="19013-140">**计算所得的列规范**</span><span class="sxs-lookup"><span data-stu-id="19013-140">**Computed Column Specification**</span></span>  
 <span data-ttu-id="19013-141">显示计算所得的列的相关信息。</span><span class="sxs-lookup"><span data-stu-id="19013-141">Displays information about a computed column.</span></span> <span data-ttu-id="19013-142">该属性显示的值与“公式”  子属性的值相同，可显示计算所得的列的公式。</span><span class="sxs-lookup"><span data-stu-id="19013-142">The value shown for property is the same as the value of the **Formula** child property and displays the formula for the computed column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19013-143">若要更改“计算所得的列规范”  属性显示的值，必须展开该属性，再编辑“公式”  子属性。</span><span class="sxs-lookup"><span data-stu-id="19013-143">To change the value shown for the **Computed Column Specification** property, you must expand it and edit the **Formula** child property.</span></span>  
  
-   <span data-ttu-id="19013-144">**公式** 显示计算所得的列的公式。</span><span class="sxs-lookup"><span data-stu-id="19013-144">**Formula** Displays the formula for the computed column.</span></span> <span data-ttu-id="19013-145">若要编辑此属性，请直接键入新公式。</span><span class="sxs-lookup"><span data-stu-id="19013-145">To edit this property, type a new formula directly.</span></span>  
  
-   <span data-ttu-id="19013-146">**是持久的** 指示是否存储公式的计算结果。</span><span class="sxs-lookup"><span data-stu-id="19013-146">**Is Persisted** Indicates whether the results of the formula are stored.</span></span> <span data-ttu-id="19013-147">如果此属性设置为“否”  ，则只存储公式，每次引用此列时都会计算公式的值。</span><span class="sxs-lookup"><span data-stu-id="19013-147">If this property is set to **No** then only the formula is stored and the values are calculated every time this column is referenced.</span></span> <span data-ttu-id="19013-148">若要编辑此属性，请单击该属性的值，展开下拉列表，然后选择其他值。</span><span class="sxs-lookup"><span data-stu-id="19013-148">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
 <span data-ttu-id="19013-149">有关详细信息，请参阅 [Specify Computed Columns in a Table](../tables/specify-computed-columns-in-a-table.md)。</span><span class="sxs-lookup"><span data-stu-id="19013-149">For more information, see [Specify Computed Columns in a Table](../tables/specify-computed-columns-in-a-table.md).</span></span>  
  
 <span data-ttu-id="19013-150">**简洁数据类型**</span><span class="sxs-lookup"><span data-stu-id="19013-150">**Condensed Data Type**</span></span>  
 <span data-ttu-id="19013-151">按与 SQL CREATE TABLE 语句同样的格式显示有关字段的数据类型的信息。</span><span class="sxs-lookup"><span data-stu-id="19013-151">Displays information about the field's data type, in the same format as the SQL CREATE TABLE statement.</span></span> <span data-ttu-id="19013-152">例如，一个包含可变长度字符串（最大长度为 20 个字符）的字段将表示为“varchar(20)”。</span><span class="sxs-lookup"><span data-stu-id="19013-152">For example, a field containing a variable-length string with a maximum length of 20 characters would be represented as "varchar(20)".</span></span> <span data-ttu-id="19013-153">若要更改此属性，请直接键入值。</span><span class="sxs-lookup"><span data-stu-id="19013-153">To change this property, type the value directly.</span></span>  
  
 <span data-ttu-id="19013-154">**说明**</span><span class="sxs-lookup"><span data-stu-id="19013-154">**Description**</span></span>  
 <span data-ttu-id="19013-155">显示描述此列的文本。</span><span class="sxs-lookup"><span data-stu-id="19013-155">Displays text describing this column.</span></span> <span data-ttu-id="19013-156">若要编辑该说明，请选择属性，单击属性值右侧显示的省略号 (   )，然后在“说明属性”  对话框中编辑说明。</span><span class="sxs-lookup"><span data-stu-id="19013-156">To edit the description, select the property, click the ellipsis (   ) that appears to the right of the property value and edit the description in the **Description Property** dialog box.</span></span>  
  
 <span data-ttu-id="19013-157">**具有确定性**</span><span class="sxs-lookup"><span data-stu-id="19013-157">**Deterministic**</span></span>  
 <span data-ttu-id="19013-158">显示是否可以明确地确定所选列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="19013-158">Shows whether the data type of the selected column can be determined with certainty.</span></span>  
  
 <span data-ttu-id="19013-159">**是 DTS 发布的**</span><span class="sxs-lookup"><span data-stu-id="19013-159">**DTS-published**</span></span>  
 <span data-ttu-id="19013-160">显示该列是否是 DTS 发布的。</span><span class="sxs-lookup"><span data-stu-id="19013-160">Shows whether the column is DTS-published.</span></span>  
  
 <span data-ttu-id="19013-161">**全文本规范**</span><span class="sxs-lookup"><span data-stu-id="19013-161">**Full-text Specification**</span></span>  
 <span data-ttu-id="19013-162">显示全文检索的相关信息。</span><span class="sxs-lookup"><span data-stu-id="19013-162">Displays information about a full-text index.</span></span> <span data-ttu-id="19013-163">此属性的值是“是全文索引的”\*\*\*\* 子属性的值，指示此列是否为全文索引列。</span><span class="sxs-lookup"><span data-stu-id="19013-163">The value of this property is the value of the **Is Full-text Indexed** child property and indicates whether this column is full-text indexed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19013-164">若要更改“全文本规范”\*\*\*\* 属性显示的值，必须展开该属性，再编辑“是全文索引的”\*\*\*\* 子属性。</span><span class="sxs-lookup"><span data-stu-id="19013-164">To change the value shown for the **Full-text Specification** property, you must expand it and edit the **Is Full-text Indexed** child property.</span></span>  
  
-   <span data-ttu-id="19013-165">“是全文索引的”\*\*\*\* 指示此列是否为全文索引列。</span><span class="sxs-lookup"><span data-stu-id="19013-165">**Is Full-text Indexed** Indicates whether this column is full-text indexed.</span></span> <span data-ttu-id="19013-166">只有在可对此列的数据类型进行全文搜索并且为此列所属的表指定了全文索引时，此属性才可设置为“是”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="19013-166">This property can be set to **Yes** only if the data type for this column is full-text searchable and if the table to which this column belongs has a full-text index specified for it.</span></span> <span data-ttu-id="19013-167">若要编辑此属性，请单击该属性的值，展开下拉列表，然后选择其他值。</span><span class="sxs-lookup"><span data-stu-id="19013-167">To edit this property, click its value, expand the drop-down list, and choose a value.</span></span>  
  
-   <span data-ttu-id="19013-168">“全文类型列”\*\*\*\* 显示对此列进行全文索引所基于的列的名称。</span><span class="sxs-lookup"><span data-stu-id="19013-168">**Full-text Type Column** Displays the name of the column on which this column is full-text indexed.</span></span> <span data-ttu-id="19013-169">如果此列的“数据类型” \*\*\*\* 属性为 **image** 或 **varbinary**，则必须设置此属性。</span><span class="sxs-lookup"><span data-stu-id="19013-169">This property must be set if the **Datatype** property for this column is either **image** or **varbinary**.</span></span> <span data-ttu-id="19013-170">此属性中指定的列必须是 **[n]char、[n]varchar** 或 **xml**类型，并且此属性的下拉列表中只包含这三种数据类型的列。</span><span class="sxs-lookup"><span data-stu-id="19013-170">The column named in this property must be of type **[n]char, [n]varchar,** or **xml**, and the drop-down list for this property contains only columns that have one of these three data types.</span></span> <span data-ttu-id="19013-171">此属性指定的列中的行指示可全文搜索列中相应行的文档类型。</span><span class="sxs-lookup"><span data-stu-id="19013-171">Rows in the column named by this property indicate the document type of the corresponding rows in the full-text-searchable column.</span></span> <span data-ttu-id="19013-172">若要编辑此属性，请单击该属性的值，展开下拉列表，然后选择其他值。</span><span class="sxs-lookup"><span data-stu-id="19013-172">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
-   <span data-ttu-id="19013-173">**语言** 指示用于对该列进行索引的断字符的语言。</span><span class="sxs-lookup"><span data-stu-id="19013-173">**Language** Indicates the language of the word breaker used to index the column.</span></span> <span data-ttu-id="19013-174">该属性中存储的值实际上是断字符的区域设置标识符。</span><span class="sxs-lookup"><span data-stu-id="19013-174">The value stored in the property is actually the locale identifier for the word breaker.</span></span> <span data-ttu-id="19013-175">有关断字符和 LCID 的详细信息，请参阅“断字符和词干分析器”。</span><span class="sxs-lookup"><span data-stu-id="19013-175">For more information about word breakers and LCIDs, see Word Breakers and Stemmers.</span></span> <span data-ttu-id="19013-176">若要编辑此属性，请单击该属性的值，展开下拉列表，然后选择其他值。</span><span class="sxs-lookup"><span data-stu-id="19013-176">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
 <span data-ttu-id="19013-177">**统计语义**</span><span class="sxs-lookup"><span data-stu-id="19013-177">**Statistical Semantics**</span></span>  
 <span data-ttu-id="19013-178">选择是否为所选列启用统计语义索引。</span><span class="sxs-lookup"><span data-stu-id="19013-178">Select whether to enable statistical semantic indexing for the selected column.</span></span> <span data-ttu-id="19013-179">有关详细信息，请参阅[语义搜索 (SQL Server)](../search/semantic-search-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="19013-179">For more information, see [Semantic Search &#40;SQL Server&#41;](../search/semantic-search-sql-server.md).</span></span>  
  
 <span data-ttu-id="19013-180">如果您在选择 **“统计语义”** 前选择某一 **“语言”**，并且所选语言没有关联的语义语言模型，则 **“统计语义”** 复选框将设置为 **“否”** 并且无法修改。</span><span class="sxs-lookup"><span data-stu-id="19013-180">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** option is set to **No** and cannot be modified.</span></span> <span data-ttu-id="19013-181">如果您在选择 **“语言”** 前为 **“统计语义”** 选项选择 **“是”**，则 **“语言”** 列中提供的语言将限制为存在语义语言模型支持的那些语言。</span><span class="sxs-lookup"><span data-stu-id="19013-181">If you select **Yes** for the **Statistical Semantics** option prior to selecting a **Language**, then the languages available in the **Language** column will be restricted to those for which there is Semantic Language Model support.</span></span>  
  
 <span data-ttu-id="19013-182">**具有非 SQL Server 订户**</span><span class="sxs-lookup"><span data-stu-id="19013-182">**Has Non-SQL Server Subscriber**</span></span>  
 <span data-ttu-id="19013-183">指示是否要将列复制到非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="19013-183">Indicates if the column is being replicated to a subscriber that is not a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="19013-184">**标识规范**</span><span class="sxs-lookup"><span data-stu-id="19013-184">**Identity Specification**</span></span>  
 <span data-ttu-id="19013-185">显示此列是否以及如何对其值强制唯一性的相关信息。</span><span class="sxs-lookup"><span data-stu-id="19013-185">Displays information about whether and how this column enforces uniqueness on its values.</span></span> <span data-ttu-id="19013-186">此属性的值指示此列是否为标识列以及是否与子属性“是标识” \*\*\*\* 的值相同。</span><span class="sxs-lookup"><span data-stu-id="19013-186">The value of this property indicates whether or not this column is an identity column and is the same as the value of the child property **Is Identity**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19013-187"> 若要更改“标识规范”\ \*\*\** 属性显示的值，必须展开该属性，再编辑“是标识”\ \*\*\** 子属性。</span><span class="sxs-lookup"><span data-stu-id="19013-187">To change the value shown for the **Identity Specification** property, you must expand it and edit the **Is Identity** child property.</span></span>  
  
-   <span data-ttu-id="19013-188">**是标识** 指示此列是否为标识列。</span><span class="sxs-lookup"><span data-stu-id="19013-188">**Is Identity** Indicates whether or not this column is an identity column.</span></span> <span data-ttu-id="19013-189">若要编辑此属性，请单击该属性的值，展开下拉列表，然后选择其他值。</span><span class="sxs-lookup"><span data-stu-id="19013-189">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
-   <span data-ttu-id="19013-190">**标识种子** 显示在此标识列的创建过程中指定的种子值。</span><span class="sxs-lookup"><span data-stu-id="19013-190">**Identity Seed** Displays the seed value specified during the creation of this identity column.</span></span> <span data-ttu-id="19013-191">此值将赋给表中的第一行。</span><span class="sxs-lookup"><span data-stu-id="19013-191">This value is assigned to the first row in the table.</span></span> <span data-ttu-id="19013-192">如果将此单元格保留为空白，则默认情况下，会将值 1 赋给该单元格。</span><span class="sxs-lookup"><span data-stu-id="19013-192">If you leave this cell blank, the value 1 will be assigned by default.</span></span> <span data-ttu-id="19013-193">若要编辑此属性，请直接键入新值。</span><span class="sxs-lookup"><span data-stu-id="19013-193">To edit this property, type the new value directly.</span></span>  
  
-   <span data-ttu-id="19013-194">**标识增量** 显示在此标识列的创建过程中指定的增量值。</span><span class="sxs-lookup"><span data-stu-id="19013-194">**Identity Increment** Displays the increment value specified during the creation of this identity column.</span></span> <span data-ttu-id="19013-195">此值是基于 **“标识种子”** 依次为每个后续行增加的增量。</span><span class="sxs-lookup"><span data-stu-id="19013-195">This value is the increment that will be added to the **Identity Seed** for each subsequent row.</span></span> <span data-ttu-id="19013-196">如果将此单元格保留为空白，则默认情况下，会将值 1 赋给该单元格。</span><span class="sxs-lookup"><span data-stu-id="19013-196">If you leave this cell blank, the value 1 will be assigned by default.</span></span> <span data-ttu-id="19013-197">若要编辑此属性，请直接键入新值。</span><span class="sxs-lookup"><span data-stu-id="19013-197">To edit this property, type the new value directly.</span></span>  
  
 <span data-ttu-id="19013-198">**是可索引的**</span><span class="sxs-lookup"><span data-stu-id="19013-198">**Indexable**</span></span>  
 <span data-ttu-id="19013-199">显示是否可以对所选列进行索引。</span><span class="sxs-lookup"><span data-stu-id="19013-199">Shows whether the selected column can be indexed.</span></span> <span data-ttu-id="19013-200">例如，不能对不确定的计算列进行索引。</span><span class="sxs-lookup"><span data-stu-id="19013-200">For example, non-deterministic computed columns cannot be indexed.</span></span>  
  
 <span data-ttu-id="19013-201">**是合并发布的**</span><span class="sxs-lookup"><span data-stu-id="19013-201">**Merge-published**</span></span>  
 <span data-ttu-id="19013-202">显示该列是否是合并发布的。</span><span class="sxs-lookup"><span data-stu-id="19013-202">Shows whether the column is merge-published.</span></span>  
  
 <span data-ttu-id="19013-203">**不用于复制**</span><span class="sxs-lookup"><span data-stu-id="19013-203">**Not For Replication**</span></span>  
 <span data-ttu-id="19013-204">指示在复制期间是否保留原始标识值。</span><span class="sxs-lookup"><span data-stu-id="19013-204">Indicates whether original identity values are preserved during replication.</span></span> <span data-ttu-id="19013-205">有关复制的详细信息，请参阅 CREATE TABLE。</span><span class="sxs-lookup"><span data-stu-id="19013-205">For more information on replication see CREATE TABLE.</span></span> <span data-ttu-id="19013-206">若要编辑此属性，请单击该属性的值，展开下拉列表，然后选择其他值。</span><span class="sxs-lookup"><span data-stu-id="19013-206">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
 <span data-ttu-id="19013-207">**复制**</span><span class="sxs-lookup"><span data-stu-id="19013-207">**Replicated**</span></span>  
 <span data-ttu-id="19013-208">显示是否在其他位置复制此列。</span><span class="sxs-lookup"><span data-stu-id="19013-208">Shows whether this column is replicated in another location.</span></span>  
  
 <span data-ttu-id="19013-209">**RowGuid**</span><span class="sxs-lookup"><span data-stu-id="19013-209">**RowGuid**</span></span>  
 <span data-ttu-id="19013-210">指示 SQL Server 是否将该列用作 ROWGUID。</span><span class="sxs-lookup"><span data-stu-id="19013-210">Indicates whether SQL Server uses the column as a ROWGUID.</span></span> <span data-ttu-id="19013-211">只有对唯一标识列才可将此值设置为 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="19013-211">You can set this value to **Yes** only for a unique identity column.</span></span> <span data-ttu-id="19013-212">若要编辑此属性，请单击该属性的值，展开下拉列表，然后选择其他值。</span><span class="sxs-lookup"><span data-stu-id="19013-212">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
 <span data-ttu-id="19013-213">**大小**</span><span class="sxs-lookup"><span data-stu-id="19013-213">**Size**</span></span>  
 <span data-ttu-id="19013-214">显示该列的数据类型所允许的大小（字节）。</span><span class="sxs-lookup"><span data-stu-id="19013-214">Shows the size in bytes allowed by column's data type.</span></span> <span data-ttu-id="19013-215">例如，某个 nchar 数据类型的长度为 10（字符数），但在 Unicode 字符集中，该数据类型的大小为 20。</span><span class="sxs-lookup"><span data-stu-id="19013-215">For example, a nchar data type may have a length of 10 (the number of characters) but it would have a size of 20 to account for Unicode character sets.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19013-216">**(max)** 数据类型的长度对于每一行都会有所不同。</span><span class="sxs-lookup"><span data-stu-id="19013-216">The length of a **(max)** data types vary for each row.</span></span> <span data-ttu-id="19013-217">**sp_help** 返回 (-1) 作为 **(max)** 列的长度。</span><span class="sxs-lookup"><span data-stu-id="19013-217">**sp_help** returns (-1) as the length of **(max)** columns.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="19013-218">显示 -1 作为列大小。</span><span class="sxs-lookup"><span data-stu-id="19013-218">displays -1 as the column size.</span></span>  
  
  
