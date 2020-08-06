---
title: SQL Server 2014 中数据库引擎功能的行为更改 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- behavior changes [SQL Server]
- Database Engine [SQL Server], what's new
- Transact-SQL behavior changes
ms.assetid: 65eaafa1-9e06-4264-b547-cbee8013c995
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9072b851f3512113b23dedc91f8c9b7151136a57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689591"
---
# <a name="behavior-changes-to-database-engine-features-in-sql-server-2014"></a><span data-ttu-id="f1e50-102">SQL Server 2014 中数据库引擎功能的行为更改</span><span class="sxs-lookup"><span data-stu-id="f1e50-102">Behavior Changes to Database Engine Features in SQL Server 2014</span></span>
  <span data-ttu-id="f1e50-103">本主题介绍[!INCLUDE[ssDE](../includes/ssde-md.md)]中的行为更改。</span><span class="sxs-lookup"><span data-stu-id="f1e50-103">This topic describes behavior changes in the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="f1e50-104">与早期版本的 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 相比， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中的功能的工作或交互方式会受到行为更改的影响。</span><span class="sxs-lookup"><span data-stu-id="f1e50-104">Behavior changes affect how features work or interact in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] as compared to earlier versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="behavior-changes-in-sssql14"></a><a name="SQL14"></a><span data-ttu-id="f1e50-105">中的行为更改[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1e50-105">Behavior Changes in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span></span>  
 <span data-ttu-id="f1e50-106">在早期版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中，如果对其运行查询的 XML 文档包含超过某一特定长度（超过 4020 个字符）的字符串，则查询可能会返回不正确的结果。</span><span class="sxs-lookup"><span data-stu-id="f1e50-106">In earlier versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], queries against an XML document that contains strings over a certain length (more than 4020 characters) can return incorrect results.</span></span> <span data-ttu-id="f1e50-107">在 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 中，此类查询将返回正确的结果。</span><span class="sxs-lookup"><span data-stu-id="f1e50-107">In [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], such queries return the correct results.</span></span>  
  
## <a name="behavior-changes-in-sssql11"></a><a name="Denali"></a><span data-ttu-id="f1e50-108">中的行为更改[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1e50-108">Behavior Changes in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]</span></span>  
  
### <a name="metadata-discovery"></a><span data-ttu-id="f1e50-109">元数据发现</span><span class="sxs-lookup"><span data-stu-id="f1e50-109">Metadata Discovery</span></span>  
 <span data-ttu-id="f1e50-110">[!INCLUDE[ssDE](../includes/ssde-md.md)]从 "允许 SQLDescribeCol" 开始获得的改进， [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 可获得比早期版本的 SQLDescribeCol 返回的预期结果更准确的说明 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f1e50-110">Improvements in the [!INCLUDE[ssDE](../includes/ssde-md.md)] starting with [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] allow SQLDescribeCol to obtain more accurate descriptions of the expected results than those returned by SQLDescribeCol in previous versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f1e50-111">有关详细信息，请参阅[元数据发现](../relational-databases/native-client/features/metadata-discovery.md)。</span><span class="sxs-lookup"><span data-stu-id="f1e50-111">For more information, see [Metadata Discovery](../relational-databases/native-client/features/metadata-discovery.md).</span></span>  
  
 <span data-ttu-id="f1e50-112">用于确定响应格式的[SET FMTONLY](/sql/t-sql/statements/set-fmtonly-transact-sql)选项（未实际运行查询）将替换为[sp_describe_first_result_set &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql)， [sp_describe_undeclared_parameters &#40;](/sql/relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql)transact-sql&#41;， [sys.databases ](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql)dm_exec_describe_first_result_set &#40;transact-sql&#41;，dm_exec_describe_first_result_set_for_object [&#40;transact-sql&#41;。 ](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="f1e50-112">The [SET FMTONLY](/sql/t-sql/statements/set-fmtonly-transact-sql) option for determining the format of a response without actually running the query is replaced with [sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql), [sp_describe_undeclared_parameters &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql), [sys.dm_exec_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql), and [sys.dm_exec_describe_first_result_set_for_object &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql).</span></span>  
  
### <a name="changes-to-behavior-in-scripting-a-sql-server-agent-task"></a><span data-ttu-id="f1e50-113">有关为 SQL Server 代理任务编写脚本的行为的更改</span><span class="sxs-lookup"><span data-stu-id="f1e50-113">Changes to Behavior in Scripting a SQL Server Agent Task</span></span>  
<span data-ttu-id="f1e50-114">从开始 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] ，如果通过复制现有作业中的脚本来创建新作业，则新作业可能会意外影响现有作业。</span><span class="sxs-lookup"><span data-stu-id="f1e50-114">Starting with [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], if you create a new job by copying the script from an existing job, the new job might inadvertently affect the existing job.</span></span> <span data-ttu-id="f1e50-115">若要使用现有作业中的脚本来创建新作业，请手动删除参数\* \@ schedule_uid\*该参数通常是在现有作业中创建作业计划的部分的最后一个参数。</span><span class="sxs-lookup"><span data-stu-id="f1e50-115">To create a new job using the script from an existing job, manually delete the parameter *\@schedule_uid* which is usually the last parameter of the section which creates the job schedule in the existing job.</span></span> <span data-ttu-id="f1e50-116">这将为新作业创建新的独立计划而不影响现有作业。</span><span class="sxs-lookup"><span data-stu-id="f1e50-116">This will create a new independent schedule for the new job without affecting existing jobs.</span></span>  
  
### <a name="constant-folding-for-clr-user-defined-functions-and-methods"></a><span data-ttu-id="f1e50-117">CLR 用户定义函数和方法的常量折叠</span><span class="sxs-lookup"><span data-stu-id="f1e50-117">Constant Folding for CLR User-Defined Functions and Methods</span></span>  
<span data-ttu-id="f1e50-118">从开始 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] ，现在可折叠以下用户定义的 CLR 对象：</span><span class="sxs-lookup"><span data-stu-id="f1e50-118">Starting with [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], the following user-defined CLR objects are now foldable:</span></span>  

-   <span data-ttu-id="f1e50-119">确定性的标量值 CLR 用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="f1e50-119">Deterministic scalar-valued CLR user-defined functions.</span></span>  
-   <span data-ttu-id="f1e50-120">确定性的 CLR 用户定义类型的方法。</span><span class="sxs-lookup"><span data-stu-id="f1e50-120">Deterministic methods of CLR user-defined types.</span></span>  
  
 <span data-ttu-id="f1e50-121">此改进旨在增强当使用相同的参数多次调用这些函数或方法时的性能。</span><span class="sxs-lookup"><span data-stu-id="f1e50-121">This improvement seeks to enhance performance when these functions or methods are called more than once with the same arguments.</span></span> <span data-ttu-id="f1e50-122">但是，此更改可能会在非确定性函数或方法被错误标记为确定性函数或方法时导致意外结果。</span><span class="sxs-lookup"><span data-stu-id="f1e50-122">However, this change may cause unexpected results when non-deterministic functions or methods have been marked as deterministic in error.</span></span> <span data-ttu-id="f1e50-123">CLR 函数或方法的确定性由 `IsDeterministic` 或 `SqlFunctionAttribute` 的 `SqlMethodAttribute` 属性的值指示。</span><span class="sxs-lookup"><span data-stu-id="f1e50-123">The determinism of a CLR function or method is indicated by the value of the `IsDeterministic` property of the `SqlFunctionAttribute` or `SqlMethodAttribute`.</span></span>  
  
### <a name="behavior-of-stenvelope-method-has-changed-with-empty-spatial-types"></a><span data-ttu-id="f1e50-124">具有空的空间类型的 STEnvelope() 方法的行为已更改</span><span class="sxs-lookup"><span data-stu-id="f1e50-124">Behavior of STEnvelope() Method Has Changed with Empty Spatial Types</span></span>  
 <span data-ttu-id="f1e50-125">具有空对象的 `STEnvelope` 方法的行为现在与其他 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 空间方法的行为保持一致。</span><span class="sxs-lookup"><span data-stu-id="f1e50-125">The behavior of the `STEnvelope` method with empty objects is now consistent with the behavior of other [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] spatial methods.</span></span>  
  
 <span data-ttu-id="f1e50-126">在 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 中，在使用空对象调用 `STEnvelope` 方法时，该方法返回以下结果：</span><span class="sxs-lookup"><span data-stu-id="f1e50-126">In [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], the `STEnvelope` method returned the following results when called with empty objects:</span></span>  
  
```sql  
SELECT geometry::Parse('POINT EMPTY').STEnvelope().ToString()  
-- returns POINT EMPTY  
SELECT geometry::Parse('LINESTRING EMPTY').STEnvelope().ToString()  
-- returns LINESTRING EMPTY  
SELECT geometry::Parse('POLYGON EMPTY').STEnvelope().ToString()  
-- returns POLYGON EMPTY  
```  
  
 <span data-ttu-id="f1e50-127">在 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 中，现在使用空对象调用 `STEnvelope` 方法时，该方法返回以下结果：</span><span class="sxs-lookup"><span data-stu-id="f1e50-127">In [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], the `STEnvelope` method now returns the following results when called with empty objects:</span></span>  
  
```sql  
SELECT geometry::Parse('POINT EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
SELECT geometry::Parse('LINESTRING EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
SELECT geometry::Parse('POLYGON EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
```  
  
 <span data-ttu-id="f1e50-128">若要确定空间对象是否为空，请&#41;方法中调用[STIsEmpty &#40;Geometry 数据类型](/sql/t-sql/spatial-geometry/stisempty-geometry-data-type)。</span><span class="sxs-lookup"><span data-stu-id="f1e50-128">To determine whether a spatial object is empty, call the [STIsEmpty &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisempty-geometry-data-type) method.</span></span>  
  
### <a name="log-function-has-new-optional-parameter"></a><span data-ttu-id="f1e50-129">LOG 函数具有新的可选参数</span><span class="sxs-lookup"><span data-stu-id="f1e50-129">LOG Function Has New Optional Parameter</span></span>  
 <span data-ttu-id="f1e50-130">`LOG`函数现在具有可选的*基*参数。</span><span class="sxs-lookup"><span data-stu-id="f1e50-130">The `LOG` function now has an optional *base* parameter.</span></span> <span data-ttu-id="f1e50-131">有关详细信息，请参阅[LOG &#40;transact-sql&#41;](/sql/t-sql/functions/log-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f1e50-131">For more information, see [LOG &#40;Transact-SQL&#41;](/sql/t-sql/functions/log-transact-sql).</span></span>  
  
### <a name="statistics-computation-during-partitioned-index-operations-has-changed"></a><span data-ttu-id="f1e50-132">已分区索引操作期间的统计信息计算已更改</span><span class="sxs-lookup"><span data-stu-id="f1e50-132">Statistics Computation during Partitioned Index Operations Has Changed</span></span>  
<span data-ttu-id="f1e50-133">在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 中，当创建或重新生成已分区索引时，并非通过扫描表中的所有行来创建统计信息。</span><span class="sxs-lookup"><span data-stu-id="f1e50-133">In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], statistics are not created by scanning all rows in the table when a partitioned index is created or rebuilt.</span></span> <span data-ttu-id="f1e50-134">相反，查询优化器使用默认采样算法来生成统计信息。</span><span class="sxs-lookup"><span data-stu-id="f1e50-134">Instead, the Query Optimizer uses the default sampling algorithm to generate statistics.</span></span> <span data-ttu-id="f1e50-135">在升级具有已分区索引的数据库后，您可以在直方图数据中注意到针对这些索引的差异。</span><span class="sxs-lookup"><span data-stu-id="f1e50-135">After upgrading a database with partitioned indexes, you may notice a difference in the histogram data for these indexes.</span></span> <span data-ttu-id="f1e50-136">此行为更改可能不会影响查询性能。</span><span class="sxs-lookup"><span data-stu-id="f1e50-136">This change in behavior may not affect query performance.</span></span> <span data-ttu-id="f1e50-137">若要通过扫描表中所有行的方法获得有关已分区索引的统计信息，请使用 `CREATE STATISTICS` 或 `UPDATE STATISTICS` 以及 `FULLSCAN` 子句。</span><span class="sxs-lookup"><span data-stu-id="f1e50-137">To obtain statistics on partitioned indexes by scanning all the rows in the table, use `CREATE STATISTICS` or `UPDATE STATISTICS` with the `FULLSCAN` clause.</span></span>  
  
### <a name="data-type-conversion-by-the-xml-value-method-has-changed"></a><span data-ttu-id="f1e50-138">通过 XML value 方法进行的数据类型转换已更改</span><span class="sxs-lookup"><span data-stu-id="f1e50-138">Data Type Conversion by the XML value Method Has Changed</span></span>  
<span data-ttu-id="f1e50-139"> 数据类型的  方法的内部行为已更改。</span><span class="sxs-lookup"><span data-stu-id="f1e50-139">The internal behavior of the `value` method of the `xml` data type has changed.</span></span> <span data-ttu-id="f1e50-140">此方法对 XML 执行 XQuery，并返回指定的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据类型的标量值。</span><span class="sxs-lookup"><span data-stu-id="f1e50-140">This method performs an XQuery against the XML and returns a scalar value of the specified [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data type.</span></span> <span data-ttu-id="f1e50-141">xs 类型必须转换为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="f1e50-141">The xs type has to be converted to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data type.</span></span> <span data-ttu-id="f1e50-142">以前，`value` 方法在内部将源值转换为 xs:string，然后将 xs:string 转换为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="f1e50-142">Previously, the `value` method internally converted the source value to an xs:string, then converted the xs:string to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data type.</span></span> <span data-ttu-id="f1e50-143">在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 中，以下情况下将跳过到 xs:string 的转换：</span><span class="sxs-lookup"><span data-stu-id="f1e50-143">In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], the conversion to xs:string is skipped in the following cases:</span></span>  
  
|<span data-ttu-id="f1e50-144">源 XS 数据类型</span><span class="sxs-lookup"><span data-stu-id="f1e50-144">Source XS data type</span></span>|<span data-ttu-id="f1e50-145">目标 SQL Server 数据类型</span><span class="sxs-lookup"><span data-stu-id="f1e50-145">Destination SQL Server data type</span></span>|  
|-------------------------|--------------------------------------|  
|<span data-ttu-id="f1e50-146">字节</span><span class="sxs-lookup"><span data-stu-id="f1e50-146">byte</span></span><br /><br /> <span data-ttu-id="f1e50-147">short</span><span class="sxs-lookup"><span data-stu-id="f1e50-147">short</span></span><br /><br /> <span data-ttu-id="f1e50-148">int</span><span class="sxs-lookup"><span data-stu-id="f1e50-148">int</span></span><br /><br /> <span data-ttu-id="f1e50-149">integer</span><span class="sxs-lookup"><span data-stu-id="f1e50-149">integer</span></span><br /><br /> <span data-ttu-id="f1e50-150">long</span><span class="sxs-lookup"><span data-stu-id="f1e50-150">long</span></span><br /><br /> <span data-ttu-id="f1e50-151">unsignedByte</span><span class="sxs-lookup"><span data-stu-id="f1e50-151">unsignedByte</span></span><br /><br /> <span data-ttu-id="f1e50-152">unsignedShort</span><span class="sxs-lookup"><span data-stu-id="f1e50-152">unsignedShort</span></span><br /><br /> <span data-ttu-id="f1e50-153">unsignedInt</span><span class="sxs-lookup"><span data-stu-id="f1e50-153">unsignedInt</span></span><br /><br /> <span data-ttu-id="f1e50-154">unsignedLong</span><span class="sxs-lookup"><span data-stu-id="f1e50-154">unsignedLong</span></span><br /><br /> <span data-ttu-id="f1e50-155">positiveInteger</span><span class="sxs-lookup"><span data-stu-id="f1e50-155">positiveInteger</span></span><br /><br /> <span data-ttu-id="f1e50-156">nonPositiveInteger</span><span class="sxs-lookup"><span data-stu-id="f1e50-156">nonPositiveInteger</span></span><br /><br /> <span data-ttu-id="f1e50-157">negativeInteger</span><span class="sxs-lookup"><span data-stu-id="f1e50-157">negativeInteger</span></span><br /><br /> <span data-ttu-id="f1e50-158">nonNegativeInteger</span><span class="sxs-lookup"><span data-stu-id="f1e50-158">nonNegativeInteger</span></span>|<span data-ttu-id="f1e50-159">tinyint</span><span class="sxs-lookup"><span data-stu-id="f1e50-159">tinyint</span></span><br /><br /> <span data-ttu-id="f1e50-160">smallint</span><span class="sxs-lookup"><span data-stu-id="f1e50-160">smallint</span></span><br /><br /> <span data-ttu-id="f1e50-161">int</span><span class="sxs-lookup"><span data-stu-id="f1e50-161">int</span></span><br /><br /> <span data-ttu-id="f1e50-162">bigint</span><span class="sxs-lookup"><span data-stu-id="f1e50-162">bigint</span></span><br /><br /> <span data-ttu-id="f1e50-163">Decimal</span><span class="sxs-lookup"><span data-stu-id="f1e50-163">decimal</span></span><br /><br /> <span data-ttu-id="f1e50-164">numeric</span><span class="sxs-lookup"><span data-stu-id="f1e50-164">numeric</span></span>|  
|<span data-ttu-id="f1e50-165">decimal</span><span class="sxs-lookup"><span data-stu-id="f1e50-165">decimal</span></span>|<span data-ttu-id="f1e50-166">Decimal</span><span class="sxs-lookup"><span data-stu-id="f1e50-166">decimal</span></span><br /><br /> <span data-ttu-id="f1e50-167">numeric</span><span class="sxs-lookup"><span data-stu-id="f1e50-167">numeric</span></span>|  
|<span data-ttu-id="f1e50-168">FLOAT</span><span class="sxs-lookup"><span data-stu-id="f1e50-168">float</span></span>|<span data-ttu-id="f1e50-169">real</span><span class="sxs-lookup"><span data-stu-id="f1e50-169">real</span></span>|  
|<span data-ttu-id="f1e50-170">Double</span><span class="sxs-lookup"><span data-stu-id="f1e50-170">double</span></span>|<span data-ttu-id="f1e50-171">FLOAT</span><span class="sxs-lookup"><span data-stu-id="f1e50-171">float</span></span>|  
  
 <span data-ttu-id="f1e50-172">新行为改进了可跳过中间转换时的性能。</span><span class="sxs-lookup"><span data-stu-id="f1e50-172">The new behavior improves performance when the intermediate conversion can be skipped.</span></span> <span data-ttu-id="f1e50-173">但是，当数据类型转换失败时，您看到的错误消息将有别于从中间 xs:string 值进行转换时引发的错误消息。</span><span class="sxs-lookup"><span data-stu-id="f1e50-173">However, when data type conversions fail, you see different error messages than those that were raised when converting from the intermediate xs:string value.</span></span> <span data-ttu-id="f1e50-174">例如，如果 value 方法未能将 `int` 值 100000 转换为 `smallint`，则之前的错误消息为：</span><span class="sxs-lookup"><span data-stu-id="f1e50-174">For example, if the value method failed to convert the `int` value 100000 to a `smallint`, the previous error message was:</span></span>  
  
 `The conversion of the nvarchar value '100000' overflowed an INT2 column. Use a larger integer column.`  
  
 <span data-ttu-id="f1e50-175">在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 中，如果没有到 xs:string 的中间转换，则错误消息为：</span><span class="sxs-lookup"><span data-stu-id="f1e50-175">In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], without the intermediate conversion to xs:string, the error message is:</span></span>  
  
 `Arithmetic overflow error converting expression to data type smallint.`  
  
### <a name="sqlcmdexe-behavior-change-in-xml-mode"></a><span data-ttu-id="f1e50-176">XML 模式中的 sqlcmd.exe 行为更改</span><span class="sxs-lookup"><span data-stu-id="f1e50-176">sqlcmd.exe Behavior Change in XML Mode</span></span>  
 <span data-ttu-id="f1e50-177">如果将 sqlcmd.exe 与 XML 模式一起使用 (：在命令) 上执行 SELECT \* from T FOR XML ... 时，会发生行为更改。</span><span class="sxs-lookup"><span data-stu-id="f1e50-177">There are behavior changes if you use sqlcmd.exe with XML mode (:XML ON command) when executing a SELECT \* from T FOR XML ....</span></span>  
  
### <a name="dbcc-checkident-revised-message"></a><span data-ttu-id="f1e50-178">DBCC CHECKIDENT 修改了消息</span><span class="sxs-lookup"><span data-stu-id="f1e50-178">DBCC CHECKIDENT Revised Message</span></span>  
 <span data-ttu-id="f1e50-179">在中 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] ，DBCC CHECKIDENT 命令返回的消息仅当与种子设定项一起使用*new_reseed_value*更改当前标识值时才发生更改。</span><span class="sxs-lookup"><span data-stu-id="f1e50-179">In [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], the message returned by the DBCC CHECKIDENT command has changed only when it is used with RESEED *new_reseed_value*  to change current identity value.</span></span> <span data-ttu-id="f1e50-180">新消息为 *"正在检查标识信息：当前标识值 ' \<current identity value> '"*。</span><span class="sxs-lookup"><span data-stu-id="f1e50-180">The new message is *"Checking identity information: current identity value '\<current identity value>'"*.</span></span> <span data-ttu-id="f1e50-181">DBCC 执行完毕。</span><span class="sxs-lookup"><span data-stu-id="f1e50-181">DBCC execution completed.</span></span> <span data-ttu-id="f1e50-182">如果 DBCC 输出了错误消息，请与系统管理员联系。”</span><span class="sxs-lookup"><span data-stu-id="f1e50-182">If DBCC printed error messages, contact your system administrator."</span></span>  
  
 <span data-ttu-id="f1e50-183">在早期版本中，消息为 *"正在检查标识信息：当前标识值 ' \<current identity value> '，当前列值 ' \<current column value> '。DBCC 执行完毕。如果 DBCC 打印了错误消息，请与系统管理员联系。 "*</span><span class="sxs-lookup"><span data-stu-id="f1e50-183">In earlier versions, the message is *"Checking identity information: current identity value '\<current identity value>', current column value '\<current column value>'. DBCC execution completed. If DBCC printed error messages, contact your system administrator."*</span></span> <span data-ttu-id="f1e50-184">当 `DBCC CHECKIDENT` 使用 `NORESEED` 、而不是第二个参数，或者没有种子设定值时，消息将保持不变。</span><span class="sxs-lookup"><span data-stu-id="f1e50-184">The message is unchanged when `DBCC CHECKIDENT` is specified with `NORESEED`, without a second parameter, or without a reseed value.</span></span> <span data-ttu-id="f1e50-185">有关详细信息，请参阅 [DBCC CHECKIDENT &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkident-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f1e50-185">For more information, see [DBCC CHECKIDENT &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkident-transact-sql).</span></span>  
  
### <a name="behavior-of-exist-function-on-xml-datatype-has-changed"></a><span data-ttu-id="f1e50-186">XML 数据类型的 exist() 函数的行为已更改</span><span class="sxs-lookup"><span data-stu-id="f1e50-186">Behavior of exist() function on XML datatype has changed</span></span>  
 <span data-ttu-id="f1e50-187">将 `exist()` XML 数据类型与 null 值进行比较时，函数的行为已更改， (零) 。</span><span class="sxs-lookup"><span data-stu-id="f1e50-187">The behavior of the `exist()` function has changed when comparing an XML data type with a null value to 0 (zero).</span></span> <span data-ttu-id="f1e50-188">请考虑以下示例：</span><span class="sxs-lookup"><span data-stu-id="f1e50-188">Consider the following example:</span></span>  
  
```sql  
DECLARE @test XML;  
SET @test = null;  
SELECT COUNT(1) WHERE @test.exist('/dogs') = 0;  
```  
  
 <span data-ttu-id="f1e50-189">在早期版本中，此比较将返回 1 (true)；现在，此比较将返回 0（零，false）。</span><span class="sxs-lookup"><span data-stu-id="f1e50-189">In earlier versions, this comparison return 1 (true); now, this comparison returns 0 (zero, false).</span></span>  
  
 <span data-ttu-id="f1e50-190">以下比较未发生更改：</span><span class="sxs-lookup"><span data-stu-id="f1e50-190">The following comparisons have not changed:</span></span>  
  
```sql  
DECLARE @test XML;  
SET @test = null;  
SELECT COUNT(1) WHERE @test.exist('/dogs') = 1; -- 0 expected, 0 returned  
SELECT COUNT(1) WHERE @test.exist('/dogs') IS NULL; -- 1 expected, 1 returned  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1e50-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1e50-191">See Also</span></span>  
 <span data-ttu-id="f1e50-192">[SQL Server 2014 中数据库引擎功能的重大更改](breaking-changes-to-database-engine-features-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="f1e50-192">[Breaking Changes to Database Engine Features in SQL Server 2014](breaking-changes-to-database-engine-features-in-sql-server-2016.md) </span></span>  
 <span data-ttu-id="f1e50-193">[SQL Server 2014 中不推荐使用的数据库引擎功能](deprecated-database-engine-features-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="f1e50-193">[Deprecated Database Engine Features in SQL Server 2014](deprecated-database-engine-features-in-sql-server-2016.md) </span></span>  
 <span data-ttu-id="f1e50-194">[SQL Server 2014 中废止数据库引擎功能](discontinued-database-engine-functionality-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="f1e50-194">[Discontinued Database Engine Functionality in SQL Server 2014](discontinued-database-engine-functionality-in-sql-server-2016.md) </span></span>  
 [<span data-ttu-id="f1e50-195">ALTER DATABASE 兼容级别 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f1e50-195">ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
  
