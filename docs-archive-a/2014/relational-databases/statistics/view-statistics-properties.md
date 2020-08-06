---
title: 查看统计信息属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.statistics.details.f1
helpviewer_keywords:
- viewing statistics properties
- statistics [SQL Server], viewing properties
ms.assetid: 0eaa2101-006e-4015-9979-3468b50e0aaa
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 63cabc5d8844982604993acac6a791317ee36925
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590103"
---
# <a name="view-statistics-properties"></a><span data-ttu-id="86236-102">查看统计信息属性</span><span class="sxs-lookup"><span data-stu-id="86236-102">View Statistics Properties</span></span>
  <span data-ttu-id="86236-103">您可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 显示 [!INCLUDE[tsql](../../includes/tsql-md.md)]中表或索引视图的当前查询优化统计信息。</span><span class="sxs-lookup"><span data-stu-id="86236-103">You can display current query optimization statistics for a table or indexed view in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="86236-104">统计信息对象包含一个带有统计信息的相关元数据的标题、一个带有统计信息对象第一个键列中的值的分布的直方图，以及一个用于度量各列之间的相关性的密度向量。</span><span class="sxs-lookup"><span data-stu-id="86236-104">Statistics objects include a header with metadata about the statistics, a histogram with the distribution of values in the first key column of the statistics object, and a density vector to measure cross-column correlation.</span></span> <span data-ttu-id="86236-105">有关直方图和密度向量的详细信息，请参阅 [DBCC SHOW_STATISTICS (Transact-SQL) ](/sql/t-sql/database-console-commands/dbcc-show-statistics-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="86236-105">For more information about histograms and density vectors, see [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-show-statistics-transact-sql)</span></span>  
  
 <span data-ttu-id="86236-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="86236-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="86236-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="86236-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="86236-108">安全性</span><span class="sxs-lookup"><span data-stu-id="86236-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="86236-109">**若要查看统计信息属性，请使用：**</span><span class="sxs-lookup"><span data-stu-id="86236-109">**To view statistics properties, using:**</span></span>  
  
     [<span data-ttu-id="86236-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="86236-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="86236-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="86236-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="86236-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="86236-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="86236-113">Security</span><span class="sxs-lookup"><span data-stu-id="86236-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="86236-114">权限</span><span class="sxs-lookup"><span data-stu-id="86236-114">Permissions</span></span>  
 <span data-ttu-id="86236-115">为了查看统计信息对象，用户必须是表所有者，或者是 `sysadmin` 固定服务器角色、`db_owner` 固定数据库角色或 `db_ddladmin` 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="86236-115">In order to view the statistics object, the user must own the table or the user must be a member of the `sysadmin` fixed server role, the `db_owner` fixed database role, or the `db_ddladmin` fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="86236-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="86236-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-statistics-properties"></a><span data-ttu-id="86236-117">查看统计信息属性</span><span class="sxs-lookup"><span data-stu-id="86236-117">To view statistics properties</span></span>  
  
1.  <span data-ttu-id="86236-118">在 **“对象资源管理器”** 中，单击加号以便展开要创建新的统计信息的数据库。</span><span class="sxs-lookup"><span data-stu-id="86236-118">In **Object Explorer**, click the plus sign to expand the database in which you want to create a new statistic.</span></span>  
  
2.  <span data-ttu-id="86236-119">单击加号以便展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="86236-119">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="86236-120">单击加号以展开要查看统计信息的属性的表。</span><span class="sxs-lookup"><span data-stu-id="86236-120">Click the plus sign to expand the table in which you want to view the statistic's properties.</span></span>  
  
4.  <span data-ttu-id="86236-121">单击加号以便展开 **“统计信息”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="86236-121">Click the plus sign to expand the **Statistics** folder.</span></span>  
  
5.  <span data-ttu-id="86236-122">双击要查看其属性的统计信息对象，然后选择“属性”。</span><span class="sxs-lookup"><span data-stu-id="86236-122">Right-click the Statistics object of which you want to view the properties and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="86236-123">在“统计信息属性 - statistics_name”对话框的“选择页”窗格中，选择“详细信息” 。</span><span class="sxs-lookup"><span data-stu-id="86236-123">In the **Statistics Properties -** _statistics_name_ dialog box, in the **Select a page** pane, select **Details**.</span></span>  
  
     <span data-ttu-id="86236-124">以下属性将显示在“统计信息属性 - statistics_name”对话框的“详细信息”页上 。</span><span class="sxs-lookup"><span data-stu-id="86236-124">The following properties show on the **Details** page in the **Statistics Properties -** _statistics_name_ dialog box.</span></span>  
  
     <span data-ttu-id="86236-125">**表名**</span><span class="sxs-lookup"><span data-stu-id="86236-125">**Table Name**</span></span>  
     <span data-ttu-id="86236-126">显示统计信息中所涉及表的名称。</span><span class="sxs-lookup"><span data-stu-id="86236-126">Displays the name of the table described by the statistics.</span></span>  
  
     <span data-ttu-id="86236-127">**统计信息名称**</span><span class="sxs-lookup"><span data-stu-id="86236-127">**Statistics Name**</span></span>  
     <span data-ttu-id="86236-128">显示存储统计信息的数据库对象的名称。</span><span class="sxs-lookup"><span data-stu-id="86236-128">Displays the name of the database object where the statistics are stored.</span></span>  
  
     <span data-ttu-id="86236-129">**INDEX 统计信息 statistics_name**</span><span class="sxs-lookup"><span data-stu-id="86236-129">**Statistics for INDEXstatistics_name**</span></span>  
     <span data-ttu-id="86236-130">此文本框显示从统计信息对象返回的属性。</span><span class="sxs-lookup"><span data-stu-id="86236-130">This text box shows the properties returned from the statistics object.</span></span> <span data-ttu-id="86236-131">此属性可分为三个部分：统计信息头、密度向量和直方图。</span><span class="sxs-lookup"><span data-stu-id="86236-131">This properties are divided into three sections: Stats Header, Density Vector, and Histogram.</span></span>  
  
     <span data-ttu-id="86236-132">下面的信息介绍结果集中为统计信息头返回的列。</span><span class="sxs-lookup"><span data-stu-id="86236-132">The following information describes the columns returned in the result set for the Stats Header.</span></span>  
  
     <span data-ttu-id="86236-133">**名称**</span><span class="sxs-lookup"><span data-stu-id="86236-133">**Name**</span></span>  
     <span data-ttu-id="86236-134">统计信息对象的名称。</span><span class="sxs-lookup"><span data-stu-id="86236-134">Name of the statistics object.</span></span>  
  
     <span data-ttu-id="86236-135">**已更新**</span><span class="sxs-lookup"><span data-stu-id="86236-135">**Updated**</span></span>  
     <span data-ttu-id="86236-136">上一次更新统计信息的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="86236-136">Date and time the statistics were last updated.</span></span>  
  
     <span data-ttu-id="86236-137">**行**</span><span class="sxs-lookup"><span data-stu-id="86236-137">**Rows**</span></span>  
     <span data-ttu-id="86236-138">上次更新统计信息时表或索引视图中的总行数。</span><span class="sxs-lookup"><span data-stu-id="86236-138">Total number of rows in the table or indexed view when the statistics were last updated.</span></span> <span data-ttu-id="86236-139">如果筛选统计信息或者统计信息与筛选索引对应，该行数可能小于表中的行数。</span><span class="sxs-lookup"><span data-stu-id="86236-139">If the statistics are filtered or correspond to a filtered index, the number of rows might be less than the number of rows in the table.</span></span>  
  
     <span data-ttu-id="86236-140">**Rows Sampled**</span><span class="sxs-lookup"><span data-stu-id="86236-140">**Rows Sampled**</span></span>  
     <span data-ttu-id="86236-141">用于统计信息计算的抽样总行数。</span><span class="sxs-lookup"><span data-stu-id="86236-141">Total number of rows sampled for statistics calculations.</span></span> <span data-ttu-id="86236-142">如果 Rows Sampled < Rows，显示的直方图和密度结果则是根据抽样行估计的。</span><span class="sxs-lookup"><span data-stu-id="86236-142">If Rows Sampled < Rows, the displayed histogram and density results are estimates based on the sampled rows.</span></span>  
  
     <span data-ttu-id="86236-143">**步骤**</span><span class="sxs-lookup"><span data-stu-id="86236-143">**Steps**</span></span>  
     <span data-ttu-id="86236-144">直方图中的梯级数。</span><span class="sxs-lookup"><span data-stu-id="86236-144">Number of steps in the histogram.</span></span> <span data-ttu-id="86236-145">每个梯级都跨越一个列值范围，后跟上限列值。</span><span class="sxs-lookup"><span data-stu-id="86236-145">Each step spans a range of column values followed by an upper bound column value.</span></span> <span data-ttu-id="86236-146">直方图梯级是根据统计信息中的第一个键列定义的。</span><span class="sxs-lookup"><span data-stu-id="86236-146">The histogram steps are defined on the first key column in the statistics.</span></span> <span data-ttu-id="86236-147">最大梯级数为 200。</span><span class="sxs-lookup"><span data-stu-id="86236-147">The maximum number of steps is 200.</span></span>  
  
     <span data-ttu-id="86236-148">**Density**</span><span class="sxs-lookup"><span data-stu-id="86236-148">**Density**</span></span>  
     <span data-ttu-id="86236-149">计算公式为 1/统计信息对象第一个键列中的所有值（不包括直方图边界值）的非重复值。</span><span class="sxs-lookup"><span data-stu-id="86236-149">Calculated as 1 / *distinct values* for all values in the first key column of the statistics object, excluding the histogram boundary values.</span></span> <span data-ttu-id="86236-150">查询优化器不使用此 Density 值，显示此值的目的是为了与 SQL Server 2008 之前的版本实现向后兼容。</span><span class="sxs-lookup"><span data-stu-id="86236-150">This Density value is not used by the query optimizer and is displayed for backward compatibility with versions before SQL Server 2008.</span></span>  
  
     <span data-ttu-id="86236-151">**Average Key Length**</span><span class="sxs-lookup"><span data-stu-id="86236-151">**Average Key Length**</span></span>  
     <span data-ttu-id="86236-152">统计信息对象中所有键列的每个值的平均字节数。</span><span class="sxs-lookup"><span data-stu-id="86236-152">Average number of bytes per value for all of the key columns in the statistics object.</span></span>  
  
     <span data-ttu-id="86236-153">**String Index**</span><span class="sxs-lookup"><span data-stu-id="86236-153">**String Index**</span></span>  
     <span data-ttu-id="86236-154">Yes 指示统计信息对象包含字符串摘要统计信息，以改进对使用 LIKE 运算符的查询谓词的基数估计；例如 `WHERE ProductName LIKE '%Bike'`。</span><span class="sxs-lookup"><span data-stu-id="86236-154">Yes indicates the statistics object contains string summary statistics to improve the cardinality estimates for query predicates that use the LIKE operator; for example, `WHERE ProductName LIKE '%Bike'`.</span></span> <span data-ttu-id="86236-155">字符串摘要统计信息与直方图分开存储，如果统计信息对象为 **char**、 **varchar**、 **nchar**、 **nvarchar**、 **varchar(max)** 、 **nvarchar(max)** 、 **text**或 **ntext**类型，则基于其第一个键列创建字符串摘要统计信息。</span><span class="sxs-lookup"><span data-stu-id="86236-155">String summary statistics are stored separately from the histogram and are created on the first key column of the statistics object when it is of type **char**, **varchar**, **nchar**, **nvarchar**, **varchar(max)**, **nvarchar(max)**, **text**, or **ntext**.</span></span>  
  
     <span data-ttu-id="86236-156">**筛选表达式**</span><span class="sxs-lookup"><span data-stu-id="86236-156">**Filter Expression**</span></span>  
     <span data-ttu-id="86236-157">包含在统计信息对象中的表行子集的谓词。</span><span class="sxs-lookup"><span data-stu-id="86236-157">Predicate for the subset of table rows included in the statistics object.</span></span> <span data-ttu-id="86236-158">NULL = 未筛选的统计信息。</span><span class="sxs-lookup"><span data-stu-id="86236-158">NULL = non-filtered statistics.</span></span>  
  
     <span data-ttu-id="86236-159">**Unfiltered Rows**</span><span class="sxs-lookup"><span data-stu-id="86236-159">**Unfiltered Rows**</span></span>  
     <span data-ttu-id="86236-160">应用筛选表达式前表中的总行数。</span><span class="sxs-lookup"><span data-stu-id="86236-160">Total number of rows in the table before applying the filter expression.</span></span> <span data-ttu-id="86236-161">如果筛选表达式为 NULL，则 Unfiltered Rows 等于 Rows。</span><span class="sxs-lookup"><span data-stu-id="86236-161">If Filter Expression is NULL, Unfiltered Rows is equal to Rows.</span></span>  
  
     <span data-ttu-id="86236-162">下面的信息介绍结果集中为密度向量返回的列。</span><span class="sxs-lookup"><span data-stu-id="86236-162">The following information describes the columns returned in the result set for the Density Vector.</span></span>  
  
     <span data-ttu-id="86236-163">**All Density**</span><span class="sxs-lookup"><span data-stu-id="86236-163">**All Density**</span></span>  
     <span data-ttu-id="86236-164">密度为 1/非重复值。</span><span class="sxs-lookup"><span data-stu-id="86236-164">Density is 1 / *distinct values*.</span></span> <span data-ttu-id="86236-165">结果显示统计信息对象中各列的每个前缀的密度，每个密度显示一行。</span><span class="sxs-lookup"><span data-stu-id="86236-165">Results display density for each prefix of columns in the statistics object, one row per density.</span></span> <span data-ttu-id="86236-166">非重复值是每个行前缀和列前缀的列值的非重复列表。</span><span class="sxs-lookup"><span data-stu-id="86236-166">A distinct value is a distinct list of the column values per row and per columns prefix.</span></span> <span data-ttu-id="86236-167">例如，如果统计信息对象包含键列 (A, B, C)，结果将报告以下每个列前缀中非重复值列表的密度：(A)、(A,B) 和 (A, B, C)。</span><span class="sxs-lookup"><span data-stu-id="86236-167">For example, if the statistics object contains key columns (A, B, C), the results report the density of the distinct lists of values in each of these column prefixes: (A), (A,B), and (A, B, C).</span></span> <span data-ttu-id="86236-168">使用前缀 (A, B, C)，以下每个列表都是一个非重复值列表：(3, 5, 6)、(4, 4, 6)、(4, 5, 6) 和 (4, 5, 7)。</span><span class="sxs-lookup"><span data-stu-id="86236-168">Using the prefix (A, B, C), each of these lists is a distinct value list: (3, 5, 6), (4, 4, 6), (4, 5, 6), (4, 5, 7).</span></span> <span data-ttu-id="86236-169">使用前缀 (A, B)，相同列值具有以下非重复值列表：(3, 5)、(4, 4) 和 (4, 5)。</span><span class="sxs-lookup"><span data-stu-id="86236-169">Using the prefix (A, B) the same column values have these distinct value lists: (3, 5), (4, 4), and (4, 5).</span></span>  
  
     <span data-ttu-id="86236-170">**Average Length**</span><span class="sxs-lookup"><span data-stu-id="86236-170">**Average Length**</span></span>  
     <span data-ttu-id="86236-171">存储列前缀的列值列表的平均长度（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="86236-171">Average length, in bytes, to store a list of the column values for the column prefix.</span></span> <span data-ttu-id="86236-172">例如，如果列表 (3, 5, 6) 中的每个值都需要 4 个字节，则长度为 12 个字节。</span><span class="sxs-lookup"><span data-stu-id="86236-172">For example, if the values in the list (3, 5, 6) each require 4 bytes the length is 12 bytes.</span></span>  
  
     <span data-ttu-id="86236-173">**“列”**</span><span class="sxs-lookup"><span data-stu-id="86236-173">**Columns**</span></span>  
     <span data-ttu-id="86236-174">为其显示 All density 和 Average length 的前缀中的列的名称。</span><span class="sxs-lookup"><span data-stu-id="86236-174">Names of columns in the prefix for which All density and Average length are displayed.</span></span>  
  
     <span data-ttu-id="86236-175">下面的信息介绍结果集中为直方图返回的列。</span><span class="sxs-lookup"><span data-stu-id="86236-175">The following information describes the columns returned in the result set for the Histogram.</span></span>  
  
     <span data-ttu-id="86236-176">**RANGE_HI_KEY**</span><span class="sxs-lookup"><span data-stu-id="86236-176">**RANGE_HI_KEY**</span></span>  
     <span data-ttu-id="86236-177">直方图梯级的上限列值。</span><span class="sxs-lookup"><span data-stu-id="86236-177">Upper bound column value for a histogram step.</span></span> <span data-ttu-id="86236-178">列值也称为键值。</span><span class="sxs-lookup"><span data-stu-id="86236-178">The column value is also called a key value.</span></span>  
  
     <span data-ttu-id="86236-179">**RANGE_ROWS**</span><span class="sxs-lookup"><span data-stu-id="86236-179">**RANGE_ROWS**</span></span>  
     <span data-ttu-id="86236-180">其列值位于直方图梯级内（不包括上限）的行的估算数目。</span><span class="sxs-lookup"><span data-stu-id="86236-180">Estimated number of rows whose column value falls within a histogram step, excluding the upper bound.</span></span>  
  
     <span data-ttu-id="86236-181">**EQ_ROWS**</span><span class="sxs-lookup"><span data-stu-id="86236-181">**EQ_ROWS**</span></span>  
     <span data-ttu-id="86236-182">其列值等于直方图梯级的上限的行的估算数目。</span><span class="sxs-lookup"><span data-stu-id="86236-182">Estimated number of rows whose column value equals the upper bound of the histogram step.</span></span>  
  
     <span data-ttu-id="86236-183">**DISTINCT_RANGE_ROWS**</span><span class="sxs-lookup"><span data-stu-id="86236-183">**DISTINCT_RANGE_ROWS**</span></span>  
     <span data-ttu-id="86236-184">非重复列值位于直方图梯级内（不包括上限）的行的估算数目。</span><span class="sxs-lookup"><span data-stu-id="86236-184">Estimated number of rows with a distinct column value within a histogram step, excluding the upper bound.</span></span>  
  
     <span data-ttu-id="86236-185">**AVG_RANGE_ROWS**</span><span class="sxs-lookup"><span data-stu-id="86236-185">**AVG_RANGE_ROWS**</span></span>  
     <span data-ttu-id="86236-186">重复列值位于直方图梯级内（不包括上限）的平均行数（如果 DISTINCT_RANGE_ROWS > 0，则为 RANGE_ROWS / DISTINCT_RANGE_ROWS）。</span><span class="sxs-lookup"><span data-stu-id="86236-186">Average number of rows with duplicate column values within a histogram step, excluding the upper bound (RANGE_ROWS / DISTINCT_RANGE_ROWS for DISTINCT_RANGE_ROWS > 0).</span></span>  
  
7.  <span data-ttu-id="86236-187">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="86236-187">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="86236-188">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="86236-188">Using Transact-SQL</span></span>  
  
#### <a name="to-view-statistics-properties"></a><span data-ttu-id="86236-189">查看统计信息属性</span><span class="sxs-lookup"><span data-stu-id="86236-189">To view statistics properties</span></span>  
  
1.  <span data-ttu-id="86236-190">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="86236-190">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="86236-191">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="86236-191">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="86236-192">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="86236-192">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- The following example displays all statistics information for the AK_Address_rowguid index of the Person.Address table.   
    DBCC SHOW_STATISTICS ("Person.Address", AK_Address_rowguid);   
    GO  
    ```  
  
 <span data-ttu-id="86236-193">有关详细信息，请参阅 [DBCC SHOW_STATISTICS (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-show-statistics-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="86236-193">For more information, see [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-show-statistics-transact-sql).</span></span>  
  
#### <a name="to-find-all-of-the-statistics-on-a-table-or-view"></a><span data-ttu-id="86236-194">查找表或视图上的所有统计信息</span><span class="sxs-lookup"><span data-stu-id="86236-194">To find all of the statistics on a table or view</span></span>  
  
1.  <span data-ttu-id="86236-195">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="86236-195">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="86236-196">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="86236-196">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="86236-197">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="86236-197">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    /*Gets the following information: name and ID of the statistics, whether the statistics were created automatically or by the user, whether the statistics were created with the NORECOMPUTE option, and whether the statistics have a filter and, if so, what that filter is.  
    */  
    SELECT name AS statistics_name  
        ,stats_id  
        ,auto_created  
        ,user_created  
        ,no_recompute  
        ,has_filter  
        ,filter_definition  
    -- using the sys.stats catalog view  
    FROM sys.stats  
    -- for the Sales.SpecialOffer table  
    WHERE object_id = OBJECT_ID('Sales.SpecialOffer');  
    GO  
    ```  
  
 <span data-ttu-id="86236-198">有关详细信息，请参阅 [sys.stats (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-stats-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="86236-198">For more information, see [sys.stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-stats-transact-sql).</span></span>  
  
  
