---
title: 使用列集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- sparse columns, column sets
- column sets
ms.assetid: a4f9de95-dc8f-4ad8-b957-137e32bfa500
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9cb496137c3986b78a55862e434c153d354a42ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591207"
---
# <a name="use-column-sets"></a><span data-ttu-id="4a1d6-102">使用列集</span><span class="sxs-lookup"><span data-stu-id="4a1d6-102">Use Column Sets</span></span>
  <span data-ttu-id="4a1d6-103">使用稀疏列的表可以指定一个列集以返回表中的所有稀疏列。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-103">Tables that use sparse columns can designate a column set to return all sparse columns in the table.</span></span> <span data-ttu-id="4a1d6-104">列集是一种非类型化的 XML 表示形式，它将表的所有稀疏列组合成为一种结构化的输出。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-104">A column set is an untyped XML representation that combines all the sparse columns of a table into a structured output.</span></span> <span data-ttu-id="4a1d6-105">列集与计算列的相似之处在于，列集并不是物理地存储在表中。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-105">A column set is like a calculated column in that the column set is not physically stored in the table.</span></span> <span data-ttu-id="4a1d6-106">列集与计算列的不同之处在于，列集可直接更新。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-106">A column set differs from a calculated column in that the column set is directly updatable.</span></span>  
  
 <span data-ttu-id="4a1d6-107">当表中有很多列，且分别对这些列进行操作很烦琐时，应考虑使用列集。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-107">You should consider using column sets when the number of columns in a table is large, and operating on them individually is cumbersome.</span></span> <span data-ttu-id="4a1d6-108">当应用程序通过对具有很多列的表使用列集来选择和插入数据时，可能会在某种程度上改进性能。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-108">Applications might see some performance improvement when they select and insert data by using column sets on tables that have lots of columns.</span></span> <span data-ttu-id="4a1d6-109">但是，当对表中的列定义很多索引时，列集的性能则会下降。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-109">However, the performance of column sets can be reduced when many indexes are defined on the columns in the table.</span></span> <span data-ttu-id="4a1d6-110">这是因为执行计划所需的内存量增加。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-110">This is because the amount of memory that is required for an execution plan increases.</span></span>  
  
 <span data-ttu-id="4a1d6-111">若要定义列集，请在 [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) 或 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 语句中使用 *<column_set_name>* FOR ALL_SPARSE_COLUMNS 关键字。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-111">To define a column set, use the *<column_set_name>* FOR ALL_SPARSE_COLUMNS keywords in the[CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) or [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) statements.</span></span>  
  
## <a name="guidelines-for-using-column-sets"></a><span data-ttu-id="4a1d6-112">列集的使用准则</span><span class="sxs-lookup"><span data-stu-id="4a1d6-112">Guidelines for Using Column Sets</span></span>  
 <span data-ttu-id="4a1d6-113">使用列集时，请考虑以下准则：</span><span class="sxs-lookup"><span data-stu-id="4a1d6-113">When you use column sets, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="4a1d6-114">稀疏列和列集可以作为同一语句的一部分添加。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-114">Sparse columns and a column set can be added as part of the same statement.</span></span>  
  
-   <span data-ttu-id="4a1d6-115">列集无法更改。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-115">The column set cannot be changed.</span></span> <span data-ttu-id="4a1d6-116">若要更改列集，必须删除列集再重新创建。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-116">To change a column set, you must delete and re-create the column set.</span></span>  
  
-   <span data-ttu-id="4a1d6-117">如果某个表已包含稀疏列，则不能向该表中添加列集。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-117">A column set cannot be added to a table if that table already contains sparse columns.</span></span>  
  
-   <span data-ttu-id="4a1d6-118">可以向不包含任何稀疏列的表中添加列集。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-118">A column set can be added to a table that does not include any sparse columns.</span></span> <span data-ttu-id="4a1d6-119">如果以后向表中添加稀疏列，它们将显示在列集中。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-119">If sparse columns are later added to the table, they will appear in the column set.</span></span>  
  
-   <span data-ttu-id="4a1d6-120">每个表只能有一个列集。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-120">Only one column set is allowed per table.</span></span>  
  
-   <span data-ttu-id="4a1d6-121">列集是可选的，不是必须使用列集才能使用稀疏列。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-121">A column set is optional and is not required to use sparse columns.</span></span>  
  
-   <span data-ttu-id="4a1d6-122">不能对列集定义约束或默认值。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-122">Constraints or default values cannot be defined on a column set.</span></span>  
  
-   <span data-ttu-id="4a1d6-123">计算列不能包含列集列。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-123">Computed columns cannot contain column set columns.</span></span>  
  
-   <span data-ttu-id="4a1d6-124">包含列集的表不支持分布式查询。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-124">Distributed queries are not supported on tables that contain column sets.</span></span>  
  
-   <span data-ttu-id="4a1d6-125">复制功能不支持列集。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-125">Replication does not support column sets.</span></span>  
  
-   <span data-ttu-id="4a1d6-126">变更数据捕获不支持列集。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-126">Change data capture does not support column sets.</span></span>  
  
-   <span data-ttu-id="4a1d6-127">列集不能是任何类型的索引的一部分。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-127">A column set cannot be part of any kind of index.</span></span> <span data-ttu-id="4a1d6-128">这包括 XML 索引、全文索引和索引视图。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-128">This includes XML indexes, full-text indexes, and indexed views.</span></span> <span data-ttu-id="4a1d6-129">列集不能作为任何索引中的包含列添加。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-129">A column set cannot be added as an included column in any index.</span></span>  
  
-   <span data-ttu-id="4a1d6-130">列集不能用在筛选索引或筛选统计信息的筛选表达式中。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-130">A column set cannot be used in the filter expression of a filtered index or filtered statistics.</span></span>  
  
-   <span data-ttu-id="4a1d6-131">当视图包括列集时，该列集会在视图中显示为一个 XML 列。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-131">When a view includes a column set, the column set appears in the view as an XML column.</span></span>  
  
-   <span data-ttu-id="4a1d6-132">索引视图定义中不能包含列集。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-132">A column set cannot be included in an indexed view definition.</span></span>  
  
-   <span data-ttu-id="4a1d6-133">如果包括含列集的表的已分区视图按名称指定稀疏列，则该已分区视图是可更新的。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-133">Partitioned views that include tables that contain column sets are updatable when the partitioned view specifies the sparse columns by name.</span></span> <span data-ttu-id="4a1d6-134">如果已分区视图引用列集，则是不可更新的。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-134">A partitioned view is not updatable when it references the column set.</span></span>  
  
-   <span data-ttu-id="4a1d6-135">查询通知不能引用列集。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-135">Query notifications that refer to column sets are not permitted.</span></span>  
  
-   <span data-ttu-id="4a1d6-136">XML 数据的大小限制为 2 GB。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-136">XML data has a size limit of 2 GB.</span></span> <span data-ttu-id="4a1d6-137">如果一行中的所有非 null 稀疏列的数据加起来超过此限额，则查询或 DML 操作将产生错误。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-137">If the combined data of all the nonnull sparse columns in a row exceeds this limit, the query or DML operation will produce an error.</span></span>  
  
-   <span data-ttu-id="4a1d6-138">有关 COLUMNS_UPDATED 函数返回的数据的信息，请参阅 [使用稀疏列](use-sparse-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-138">For information about the data that is returned by the COLUMNS_UPDATED function, see [Use Sparse Columns](use-sparse-columns.md).</span></span>  
  
## <a name="guidelines-for-selecting-data-from-a-column-set"></a><span data-ttu-id="4a1d6-139">从列集中选择数据的准则</span><span class="sxs-lookup"><span data-stu-id="4a1d6-139">Guidelines for Selecting Data from a Column Set</span></span>  
 <span data-ttu-id="4a1d6-140">从列集中选择数据时，请考虑下面的准则：</span><span class="sxs-lookup"><span data-stu-id="4a1d6-140">Consider the following guidelines for selecting data from a column set:</span></span>  
  
-   <span data-ttu-id="4a1d6-141">从概念上讲，列集是一种可更新的 XML 计算列，它将一组基础关系列聚合为一种 XML 表示形式。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-141">Conceptually, a column set is a type of updatable, computed XML column that aggregates a set of underlying relational columns into a single XML representation.</span></span> <span data-ttu-id="4a1d6-142">列集仅仅支持 ALL_SPARSE_COLUMNS 属性。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-142">The column set only supports the ALL_SPARSE_COLUMNS property.</span></span> <span data-ttu-id="4a1d6-143">此属性用于聚合特定行的所有稀疏列中的所有非 null 值。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-143">This property is used to aggregate all nonnull values from all sparse columns for a particular row.</span></span>  
  
-   <span data-ttu-id="4a1d6-144">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 表编辑器中，列集显示为一个可编辑的 XML 字段。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-144">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] table editor, column sets are displayed as an editable XML field.</span></span> <span data-ttu-id="4a1d6-145">按如下格式定义列集：</span><span class="sxs-lookup"><span data-stu-id="4a1d6-145">Define column sets in the format:</span></span>  
  
    ```  
    <column_name_1>value1</column_name_1><column_name_2>value2</column_name_2>...  
    ```  
  
     <span data-ttu-id="4a1d6-146">下面给出了一些列集值的示例：</span><span class="sxs-lookup"><span data-stu-id="4a1d6-146">Examples of column set values are as follows:</span></span>  
  
    -   `<sparseProp1>10</sparseProp1><sparseProp3>20</sparseProp3>`  
  
    -   `<DocTitle>Bicycle Parts List</DocTitle><Region>West</Region>`  
  
-   <span data-ttu-id="4a1d6-147">在列集的 XML 表示中将忽略包含 null 值的稀疏列。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-147">Sparse columns that contain null values are omitted from the XML representation for the column set.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="4a1d6-148">添加列集会更改 SELECT \* 查询的行为。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-148">Adding a column set changes the behavior of SELECT \* queries.</span></span> <span data-ttu-id="4a1d6-149">此查询会将列集作为 XML 列返回，而不返回单个稀疏列。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-149">The query will return the column set as an XML column and not return the individual sparse columns.</span></span> <span data-ttu-id="4a1d6-150">架构设计人员和软件开发人员必须小心，不要破坏现有应用程序。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-150">Schema designers and software developers must be careful not to break existing applications.</span></span>  
  
## <a name="inserting-or-modifying-data-in-a-column-set"></a><span data-ttu-id="4a1d6-151">在列集中插入或修改数据</span><span class="sxs-lookup"><span data-stu-id="4a1d6-151">Inserting or Modifying Data in a Column Set</span></span>  
 <span data-ttu-id="4a1d6-152">可以通过以下方法来执行稀疏列的数据操作：使用单个列的名称，或者引用列集的名称并使用列集的 XML 格式来指定列集的值。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-152">Data manipulation of a sparse column can be performed by using the name of the individual columns, or by referencing the name of the column set and specifying the values of the column set by using the XML format of the column set.</span></span> <span data-ttu-id="4a1d6-153">稀疏列可以按任何顺序出现在 XML 列中。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-153">Sparse columns can appear in any order in the XML column.</span></span>  
  
 <span data-ttu-id="4a1d6-154">当使用 XML 列集插入或更新稀疏列值时，插入基础稀疏列的值将从 `xml` 数据类型隐式转换为另一种类型。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-154">When sparse column values are inserted or updated by using the XML column set, the values that are inserted into the underlying sparse columns are implicitly converted from the `xml` data type.</span></span> <span data-ttu-id="4a1d6-155">对于数值列，数值列的 XML 中的空白值将转换为空字符串。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-155">In the case of numeric columns, a blank value in the XML for the numeric column converts to an empty string.</span></span> <span data-ttu-id="4a1d6-156">这会导致在数值列中插入零，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-156">This causes a zero to be inserted into the numeric column as shown in the following example.</span></span>  
  
```  
CREATE TABLE t (i int SPARSE, cs xml column_set FOR ALL_SPARSE_COLUMNS);  
GO  
INSERT t(cs) VALUES ('<i/>');  
GO  
SELECT i FROM t;  
GO  
```  
  
 <span data-ttu-id="4a1d6-157">在本示例中，没有为 `i`列指定值，但插入了 `0` 值。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-157">In this example, no value was specified for the column `i`, but the value `0` was inserted.</span></span>  
  
## <a name="using-the-sql_variant-data-type"></a><span data-ttu-id="4a1d6-158">使用 sql_variant 数据类型</span><span class="sxs-lookup"><span data-stu-id="4a1d6-158">Using the sql_variant Data Type</span></span>  
 <span data-ttu-id="4a1d6-159">`sql_variant` 日期类型可以存储多种不同的数据类型，如 `int`、`char` 和 `date`。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-159">The `sql_variant` date type can store multiple different data types, such as `int`, `char`, and `date`.</span></span> <span data-ttu-id="4a1d6-160">列集会输出数据类型信息（例如与 `sql_variant` 值关联的小数位数、精度以及区域设置信息）作为生成的 XML 列中的属性。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-160">Column sets output the data type information such as scale, precision, and locale information that is associated with a `sql_variant` value as attributes in the generated XML column.</span></span> <span data-ttu-id="4a1d6-161">如果尝试在自定义生成的 XML 语句中将这些属性作为对列集的插入或更新操作的输入提供，则其中一些属性是必需的，并会为一些属性分配默认值。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-161">If you try to provide these attributes in a custom-generated XML statement as an input for an insert or update operation on a column set, some of these attributes are required and some of them are assigned a default value.</span></span> <span data-ttu-id="4a1d6-162">下表列出数据类型以及在未提供值时服务器所生成的默认值。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-162">The following table lists the data types and the default values that the server generates when the value is not provided.</span></span>  
  
|<span data-ttu-id="4a1d6-163">数据类型</span><span class="sxs-lookup"><span data-stu-id="4a1d6-163">Data type</span></span>|<span data-ttu-id="4a1d6-164">localeID\*</span><span class="sxs-lookup"><span data-stu-id="4a1d6-164">localeID\*</span></span>|<span data-ttu-id="4a1d6-165">sqlCompareOptions</span><span class="sxs-lookup"><span data-stu-id="4a1d6-165">sqlCompareOptions</span></span>|<span data-ttu-id="4a1d6-166">sqlCollationVersion</span><span class="sxs-lookup"><span data-stu-id="4a1d6-166">sqlCollationVersion</span></span>|<span data-ttu-id="4a1d6-167">SqlSortId</span><span class="sxs-lookup"><span data-stu-id="4a1d6-167">SqlSortId</span></span>|<span data-ttu-id="4a1d6-168">最大长度</span><span class="sxs-lookup"><span data-stu-id="4a1d6-168">Maximum length</span></span>|<span data-ttu-id="4a1d6-169">Precision</span><span class="sxs-lookup"><span data-stu-id="4a1d6-169">Precision</span></span>|<span data-ttu-id="4a1d6-170">缩放</span><span class="sxs-lookup"><span data-stu-id="4a1d6-170">Scale</span></span>|  
|---------------|----------------|-----------------------|-------------------------|---------------|--------------------|---------------|-----------|  
|<span data-ttu-id="4a1d6-171">`char`, `varchar`, `binary`</span><span class="sxs-lookup"><span data-stu-id="4a1d6-171">`char`, `varchar`, `binary`</span></span>|<span data-ttu-id="4a1d6-172">-1</span><span class="sxs-lookup"><span data-stu-id="4a1d6-172">-1</span></span>|<span data-ttu-id="4a1d6-173">'Default'</span><span class="sxs-lookup"><span data-stu-id="4a1d6-173">'Default'</span></span>|<span data-ttu-id="4a1d6-174">0</span><span class="sxs-lookup"><span data-stu-id="4a1d6-174">0</span></span>|<span data-ttu-id="4a1d6-175">0</span><span class="sxs-lookup"><span data-stu-id="4a1d6-175">0</span></span>|<span data-ttu-id="4a1d6-176">8000</span><span class="sxs-lookup"><span data-stu-id="4a1d6-176">8000</span></span>|<span data-ttu-id="4a1d6-177">不适用\*\*</span><span class="sxs-lookup"><span data-stu-id="4a1d6-177">Not applicable\*\*</span></span>|<span data-ttu-id="4a1d6-178">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-178">Not applicable</span></span>|  
|`nvarchar`|<span data-ttu-id="4a1d6-179">-1</span><span class="sxs-lookup"><span data-stu-id="4a1d6-179">-1</span></span>|<span data-ttu-id="4a1d6-180">'Default'</span><span class="sxs-lookup"><span data-stu-id="4a1d6-180">'Default'</span></span>|<span data-ttu-id="4a1d6-181">0</span><span class="sxs-lookup"><span data-stu-id="4a1d6-181">0</span></span>|<span data-ttu-id="4a1d6-182">0</span><span class="sxs-lookup"><span data-stu-id="4a1d6-182">0</span></span>|<span data-ttu-id="4a1d6-183">4000</span><span class="sxs-lookup"><span data-stu-id="4a1d6-183">4000</span></span>|<span data-ttu-id="4a1d6-184">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-184">Not applicable</span></span>|<span data-ttu-id="4a1d6-185">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-185">Not applicable</span></span>|  
|<span data-ttu-id="4a1d6-186">`decimal`, `float`, `real`</span><span class="sxs-lookup"><span data-stu-id="4a1d6-186">`decimal`, `float`, `real`</span></span>|<span data-ttu-id="4a1d6-187">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-187">Not applicable</span></span>|<span data-ttu-id="4a1d6-188">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-188">Not applicable</span></span>|<span data-ttu-id="4a1d6-189">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-189">Not applicable</span></span>|<span data-ttu-id="4a1d6-190">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-190">Not applicable</span></span>|<span data-ttu-id="4a1d6-191">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-191">Not applicable</span></span>|<span data-ttu-id="4a1d6-192">18</span><span class="sxs-lookup"><span data-stu-id="4a1d6-192">18</span></span>|<span data-ttu-id="4a1d6-193">0</span><span class="sxs-lookup"><span data-stu-id="4a1d6-193">0</span></span>|  
|<span data-ttu-id="4a1d6-194">`integer`, `bigint`, `tinyint`, `smallint`</span><span class="sxs-lookup"><span data-stu-id="4a1d6-194">`integer`, `bigint`, `tinyint`, `smallint`</span></span>|<span data-ttu-id="4a1d6-195">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-195">Not applicable</span></span>|<span data-ttu-id="4a1d6-196">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-196">Not applicable</span></span>|<span data-ttu-id="4a1d6-197">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-197">Not applicable</span></span>|<span data-ttu-id="4a1d6-198">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-198">Not applicable</span></span>|<span data-ttu-id="4a1d6-199">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-199">Not applicable</span></span>|<span data-ttu-id="4a1d6-200">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-200">Not applicable</span></span>|<span data-ttu-id="4a1d6-201">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-201">Not applicable</span></span>|  
|`datetime2`|<span data-ttu-id="4a1d6-202">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-202">Not applicable</span></span>|<span data-ttu-id="4a1d6-203">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-203">Not applicable</span></span>|<span data-ttu-id="4a1d6-204">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-204">Not applicable</span></span>|<span data-ttu-id="4a1d6-205">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-205">Not applicable</span></span>|<span data-ttu-id="4a1d6-206">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-206">Not applicable</span></span>|<span data-ttu-id="4a1d6-207">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-207">Not applicable</span></span>|<span data-ttu-id="4a1d6-208">7</span><span class="sxs-lookup"><span data-stu-id="4a1d6-208">7</span></span>|  
|`datetime offset`|<span data-ttu-id="4a1d6-209">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-209">Not applicable</span></span>|<span data-ttu-id="4a1d6-210">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-210">Not applicable</span></span>|<span data-ttu-id="4a1d6-211">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-211">Not applicable</span></span>|<span data-ttu-id="4a1d6-212">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-212">Not applicable</span></span>|<span data-ttu-id="4a1d6-213">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-213">Not applicable</span></span>|<span data-ttu-id="4a1d6-214">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-214">Not applicable</span></span>|<span data-ttu-id="4a1d6-215">7</span><span class="sxs-lookup"><span data-stu-id="4a1d6-215">7</span></span>|  
|<span data-ttu-id="4a1d6-216">`datetime`, `date`, `smalldatetime`</span><span class="sxs-lookup"><span data-stu-id="4a1d6-216">`datetime`, `date`, `smalldatetime`</span></span>|<span data-ttu-id="4a1d6-217">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-217">Not applicable</span></span>|<span data-ttu-id="4a1d6-218">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-218">Not applicable</span></span>|<span data-ttu-id="4a1d6-219">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-219">Not applicable</span></span>|<span data-ttu-id="4a1d6-220">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-220">Not applicable</span></span>|<span data-ttu-id="4a1d6-221">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-221">Not applicable</span></span>|<span data-ttu-id="4a1d6-222">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-222">Not applicable</span></span>|<span data-ttu-id="4a1d6-223">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-223">Not applicable</span></span>|  
|<span data-ttu-id="4a1d6-224">`money`, `smallmoney`</span><span class="sxs-lookup"><span data-stu-id="4a1d6-224">`money`, `smallmoney`</span></span>|<span data-ttu-id="4a1d6-225">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-225">Not applicable</span></span>|<span data-ttu-id="4a1d6-226">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-226">Not applicable</span></span>|<span data-ttu-id="4a1d6-227">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-227">Not applicable</span></span>|<span data-ttu-id="4a1d6-228">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-228">Not applicable</span></span>|<span data-ttu-id="4a1d6-229">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-229">Not applicable</span></span>|<span data-ttu-id="4a1d6-230">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-230">Not applicable</span></span>|<span data-ttu-id="4a1d6-231">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-231">Not applicable</span></span>|  
|`time`|<span data-ttu-id="4a1d6-232">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-232">Not applicable</span></span>|<span data-ttu-id="4a1d6-233">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-233">Not applicable</span></span>|<span data-ttu-id="4a1d6-234">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-234">Not applicable</span></span>|<span data-ttu-id="4a1d6-235">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-235">Not applicable</span></span>|<span data-ttu-id="4a1d6-236">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-236">Not applicable</span></span>|<span data-ttu-id="4a1d6-237">不适用</span><span class="sxs-lookup"><span data-stu-id="4a1d6-237">Not applicable</span></span>|<span data-ttu-id="4a1d6-238">7</span><span class="sxs-lookup"><span data-stu-id="4a1d6-238">7</span></span>|  
  
 <span data-ttu-id="4a1d6-239">\*  localeID -1 表示默认区域设置。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-239">\*  localeID -1 means the default locale.</span></span> <span data-ttu-id="4a1d6-240">英语的区域设置为 1033。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-240">The English locale is 1033.</span></span>  
  
 <span data-ttu-id="4a1d6-241">\*\* 不适用 = 在针对列集的选择操作期间不会为这些属性输出值。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-241">\*\*  Not applicable = No values are output for these attributes during a select operation on the column set.</span></span> <span data-ttu-id="4a1d6-242">当调用方在插入或更新操作期间使用为列集提供的 XML 表达形式为该属性指定值时，会生成错误。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-242">Generates an error when a value is specified for this attribute by the caller in the XML representation provided for a column set in an insert or update operation.</span></span>  
  
## <a name="security"></a><span data-ttu-id="4a1d6-243">安全性</span><span class="sxs-lookup"><span data-stu-id="4a1d6-243">Security</span></span>  
 <span data-ttu-id="4a1d6-244">列集的安全模式的工作原理类似于表与列之间存在的安全模式。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-244">The security model for a column set works similar to the security model that exists between table and columns.</span></span> <span data-ttu-id="4a1d6-245">可以将列集视为一个小型表，选择操作类似于针对该微型表的 SELECT \* 操作。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-245">Column sets can be visualized as a minitable and a select operation is like a SELECT \* operation on this minitable.</span></span> <span data-ttu-id="4a1d6-246">但是，列集与稀疏列之间的关系是分组关系，而不是严格意义上的容器关系。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-246">But, the relationship between column set to sparse columns is a grouping relationship instead of strictly a container.</span></span> <span data-ttu-id="4a1d6-247">安全模式检查列集列的安全性，并允许对基础稀疏列执行 DENY 操作。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-247">The security model checks the security on the column set column, and honors the DENY operations on the underlying sparse columns.</span></span> <span data-ttu-id="4a1d6-248">安全模式的其他特征有：</span><span class="sxs-lookup"><span data-stu-id="4a1d6-248">Additional characteristics of the security model are as follows:</span></span>  
  
-   <span data-ttu-id="4a1d6-249">可以为列集列授予安全权限，也可以撤消这一权限，这与表中的其他任何列类似。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-249">Security permissions can be granted and revoked from the column set column, similar to any other column in the table.</span></span>  
  
-   <span data-ttu-id="4a1d6-250">列集列的 SELECT、INSERT、UPDATE、DELETE 和 REFERENCES 权限的 GRANT 或 REVOKE 不会传播到该列集的基础成员列。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-250">A GRANT or REVOKE of SELECT, INSERT, UPDATE, DELETE, and REFERENCES permission on a column set column does not propagate to the underlying member columns of that set.</span></span> <span data-ttu-id="4a1d6-251">它仅仅适用于列集列的使用。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-251">It applies only to the usage of the column set column.</span></span> <span data-ttu-id="4a1d6-252">列集的 DENY 权限则会传播到表的基础稀疏列。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-252">DENY permission on a column set does propagate to the underlying sparse columns of the table.</span></span>  
  
-   <span data-ttu-id="4a1d6-253">对列集列执行 SELECT、INSERT、UPDATE 和 DELETE 语句要求用户对该列集列拥有对应的权限，此外还必须对表中的所有稀疏列都拥有对应的权限。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-253">Executing SELECT, INSERT, UPDATE, and DELETE statements on the column set column require that the user has corresponding permissions on the column set column, and also the corresponding permission on all the sparse columns in the table.</span></span> <span data-ttu-id="4a1d6-254">因为列集表示表中的所有稀疏列，所以您必须对所有稀疏列（包括您可能不会更改的稀疏列）都拥有权限。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-254">Because the column set represents all the sparse columns in the table, you must have permission on all the sparse columns, and this includes sparse columns that you might not be changing.</span></span>  
  
-   <span data-ttu-id="4a1d6-255">对稀疏列或列集执行 REVOKE 语句会默认将安全性设置为其父对象的安全性。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-255">Executing a REVOKE statement on a sparse column or column set defaults the security to their parent object.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4a1d6-256">示例</span><span class="sxs-lookup"><span data-stu-id="4a1d6-256">Examples</span></span>  
 <span data-ttu-id="4a1d6-257">在下面的示例中，文档表包含列 `DocID` 和 `Title`的通用集。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-257">In the following examples, a document table contains the common set of columns `DocID` and `Title`.</span></span> <span data-ttu-id="4a1d6-258">生产组希望所有生产文档都有一个 `ProductionSpecification` 列和一个 `ProductionLocation` 列。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-258">The Production group wants a `ProductionSpecification` and `ProductionLocation` column for all production documents.</span></span> <span data-ttu-id="4a1d6-259">市场组希望所有市场文档都有一个 `MarketingSurveyGroup` 列。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-259">The Marketing group wants a `MarketingSurveyGroup` column for marketing documents.</span></span>  
  
### <a name="a-creating-a-table-that-has-a-column-set"></a><span data-ttu-id="4a1d6-260">A.</span><span class="sxs-lookup"><span data-stu-id="4a1d6-260">A.</span></span> <span data-ttu-id="4a1d6-261">A. 创建具有列集的表</span><span class="sxs-lookup"><span data-stu-id="4a1d6-261">Creating a table that has a column set</span></span>  
 <span data-ttu-id="4a1d6-262">下面的示例创建使用稀疏列并包括列集 `SpecialPurposeColumns`的表。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-262">The following example creates the table that uses sparse columns and includes the column set `SpecialPurposeColumns`.</span></span> <span data-ttu-id="4a1d6-263">该示例在表中插入两行，然后从表中选择数据。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-263">The example inserts two rows into the table, and then selects data from the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4a1d6-264">该表只有五列，以便易于显示和读取。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-264">This table has only five columns to make it easier to display and read.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
  
CREATE TABLE DocumentStoreWithColumnSet  
    (DocID int PRIMARY KEY,  
     Title varchar(200) NOT NULL,  
     ProductionSpecification varchar(20) SPARSE NULL,  
     ProductionLocation smallint SPARSE NULL,  
     MarketingSurveyGroup varchar(20) SPARSE NULL,  
     MarketingProgramID int SPARSE NULL,  
     SpecialPurposeColumns XML COLUMN_SET FOR ALL_SPARSE_COLUMNS);  
GO  
```  
  
### <a name="b-inserting-data-to-a-table-by-using-the-names-of-the-sparse-columns"></a><span data-ttu-id="4a1d6-265">B.</span><span class="sxs-lookup"><span data-stu-id="4a1d6-265">B.</span></span> <span data-ttu-id="4a1d6-266">使用稀疏列的名称向表中插入数据</span><span class="sxs-lookup"><span data-stu-id="4a1d6-266">Inserting data to a table by using the names of the sparse columns</span></span>  
 <span data-ttu-id="4a1d6-267">下面的示例向示例 A 中创建的表插入两行。这些示例使用稀疏列的名称，而不引用列集。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-267">The following examples insert two rows into the table that is created in example A. The examples use the names of the sparse columns and do not reference the column set.</span></span>  
  
```  
INSERT DocumentStoreWithColumnSet (DocID, Title, ProductionSpecification, ProductionLocation)  
VALUES (1, 'Tire Spec 1', 'AXZZ217', 27);  
GO  
  
INSERT DocumentStoreWithColumnSet (DocID, Title, MarketingSurveyGroup)  
VALUES (2, 'Survey 2142', 'Men 25 - 35');  
GO  
```  
  
### <a name="c-inserting-data-to-a-table-by-using-the-name-of-the-column-set"></a><span data-ttu-id="4a1d6-268">C.</span><span class="sxs-lookup"><span data-stu-id="4a1d6-268">C.</span></span> <span data-ttu-id="4a1d6-269">使用列集的名称向表中插入数据</span><span class="sxs-lookup"><span data-stu-id="4a1d6-269">Inserting data to a table by using the name of the column set</span></span>  
 <span data-ttu-id="4a1d6-270">下面的示例向示例 A 中创建的表插入第三行。这一次不使用稀疏列的名称，</span><span class="sxs-lookup"><span data-stu-id="4a1d6-270">The following example inserts a third row into the table that is created in example A. This time the names of the sparse columns are not used.</span></span> <span data-ttu-id="4a1d6-271">而是使用列集的名称，插入操作以 XML 格式为四个稀疏列中的两列提供值。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-271">Instead, the name of the column set is used, and the insert provides the values for two of the four sparse columns in XML format.</span></span>  
  
```  
INSERT DocumentStoreWithColumnSet (DocID, Title, SpecialPurposeColumns)  
VALUES (3, 'Tire Spec 2', '<ProductionSpecification>AXW9R411</ProductionSpecification><ProductionLocation>38</ProductionLocation>');  
GO  
```  
  
### <a name="d-observing-the-results-of-a-column-set-when-select--is-used"></a><span data-ttu-id="4a1d6-272">D.</span><span class="sxs-lookup"><span data-stu-id="4a1d6-272">D.</span></span> <span data-ttu-id="4a1d6-273">观察使用 SELECT \* 时的列集结果</span><span class="sxs-lookup"><span data-stu-id="4a1d6-273">Observing the results of a column set when SELECT \* is used</span></span>  
 <span data-ttu-id="4a1d6-274">下面的示例从包含列集的表中选择所有列。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-274">The following example selects all the columns from the table that contains a column set.</span></span> <span data-ttu-id="4a1d6-275">它返回具有稀疏列的组合值的 XML 列，</span><span class="sxs-lookup"><span data-stu-id="4a1d6-275">It returns an XML column with the combined values of the sparse columns.</span></span> <span data-ttu-id="4a1d6-276">而不是单独返回每个稀疏列。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-276">It does not return the sparse columns individually.</span></span>  
  
```  
SELECT DocID, Title, SpecialPurposeColumns FROM DocumentStoreWithColumnSet ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DocID Title        SpecialPurposeColumns`  
  
 `1      Tire Spec 1  <ProductionSpecification>AXZZ217</ProductionSpecification><ProductionLocation>27</ProductionLocation>`  
  
 `2      Survey 2142  <MarketingSurveyGroup>Men 25 - 35</MarketingSurveyGroup>`  
  
 `3      Tire Spec 2  <ProductionSpecification>AXW9R411</ProductionSpecification><ProductionLocation>38</ProductionLocation>`  
  
### <a name="e-observing-the-results-of-selecting-the-column-set-by-name"></a><span data-ttu-id="4a1d6-277">E.</span><span class="sxs-lookup"><span data-stu-id="4a1d6-277">E.</span></span> <span data-ttu-id="4a1d6-278">观察按名称选择列集的结果</span><span class="sxs-lookup"><span data-stu-id="4a1d6-278">Observing the results of selecting the column set by name</span></span>  
 <span data-ttu-id="4a1d6-279">因为生产部门对市场数据不感兴趣，所以本示例添加 `WHERE` 子句以限制输出。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-279">Because the Production department is not interested in the marketing data, this example adds a `WHERE` clause to restrict the output.</span></span> <span data-ttu-id="4a1d6-280">本示例使用列集的名称。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-280">The example uses the name of the column set.</span></span>  
  
```  
SELECT DocID, Title, SpecialPurposeColumns  
FROM DocumentStoreWithColumnSet  
WHERE ProductionSpecification IS NOT NULL ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DocID Title        SpecialPurposeColumns`  
  
 `1     Tire Spec 1  <ProductionSpecification>AXZZ217</ProductionSpecification><ProductionLocation>27</ProductionLocation>`  
  
 `3     Tire Spec 2  <ProductionSpecification>AXW9R411</ProductionSpecification><ProductionLocation>38</ProductionLocation>`  
  
### <a name="f-observing-the-results-of-selecting-sparse-columns-by-name"></a><span data-ttu-id="4a1d6-281">F.</span><span class="sxs-lookup"><span data-stu-id="4a1d6-281">F.</span></span> <span data-ttu-id="4a1d6-282">观察按名称选择稀疏列的结果</span><span class="sxs-lookup"><span data-stu-id="4a1d6-282">Observing the results of selecting sparse columns by name</span></span>  
 <span data-ttu-id="4a1d6-283">当表包含列集时，您仍然可以使用各列名称来查询表，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-283">When a table contains a column set, you can still query the table by using the individual column names as shown in the following example.</span></span>  
  
```  
SELECT DocID, Title, ProductionSpecification, ProductionLocation   
FROM DocumentStoreWithColumnSet  
WHERE ProductionSpecification IS NOT NULL ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DocID Title        ProductionSpecification ProductionLocation`  
  
 `1     Tire Spec 1  AXZZ217                 27`  
  
 `3     Tire Spec 2  AXW9R411                38`  
  
### <a name="g-updating-a-table-by-using-a-column-set"></a><span data-ttu-id="4a1d6-284">G.</span><span class="sxs-lookup"><span data-stu-id="4a1d6-284">G.</span></span> <span data-ttu-id="4a1d6-285">使用列集来更新表</span><span class="sxs-lookup"><span data-stu-id="4a1d6-285">Updating a table by using a column set</span></span>  
 <span data-ttu-id="4a1d6-286">下面的示例用第三个记录所在行使用的两个稀疏列的新值来更新该记录。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-286">The following example updates the third record with new values for both sparse columns that are used by that row.</span></span>  
  
```  
UPDATE DocumentStoreWithColumnSet  
SET SpecialPurposeColumns = '<ProductionSpecification>ZZ285W</ProductionSpecification><ProductionLocation>38</ProductionLocation>'  
WHERE DocID = 3 ;  
GO  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4a1d6-287">使用列集的 UPDATE 语句更新表中的所有稀疏列。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-287">An UPDATE statement that uses a column set updates all the sparse columns in the table.</span></span> <span data-ttu-id="4a1d6-288">未引用的稀疏列将更新为 NULL。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-288">Sparse columns that are not referenced are updated to NULL.</span></span>  
  
 <span data-ttu-id="4a1d6-289">下面的示例更新第三个记录，但仅仅指定两个已填充列的其中一列的值。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-289">The following example updates the third record, but only specifies the value of one of the two populated columns.</span></span> <span data-ttu-id="4a1d6-290">在 `ProductionLocation` 语句中未包括第二列 `UPDATE` ，所以该列更新为 NULL。</span><span class="sxs-lookup"><span data-stu-id="4a1d6-290">The second column `ProductionLocation` is not included in the `UPDATE` statement and is updated to NULL.</span></span>  
  
```  
UPDATE DocumentStoreWithColumnSet  
SET SpecialPurposeColumns = '<ProductionSpecification>ZZ285W</ProductionSpecification>'  
WHERE DocID = 3 ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a1d6-291">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4a1d6-291">See Also</span></span>  
 [<span data-ttu-id="4a1d6-292">使用稀疏列</span><span class="sxs-lookup"><span data-stu-id="4a1d6-292">Use Sparse Columns</span></span>](use-sparse-columns.md)  
  
  
