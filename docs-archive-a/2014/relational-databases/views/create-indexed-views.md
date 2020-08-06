---
title: 创建索引视图 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexed views [SQL Server], creating
- clustered indexes, views
- CREATE INDEX statement
- large_value_types_out_of_row option
- indexed views [SQL Server]
- views [SQL Server], indexed views
ms.assetid: f86dd29f-52dd-44a9-91ac-1eb305c1ca8d
author: stevestein
ms.author: sstein
ms.openlocfilehash: d33ff37caca04f46edd6ad92d0686713829bb270
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577462"
---
# <a name="create-indexed-views"></a><span data-ttu-id="ca1e1-102">创建索引视图</span><span class="sxs-lookup"><span data-stu-id="ca1e1-102">Create Indexed Views</span></span>
  <span data-ttu-id="ca1e1-103">本主题将说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中创建索引视图。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-103">This topic describes how to create an indexed view in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ca1e1-104">对视图创建的第一个索引必须是唯一聚集索引。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-104">The first index created on a view must be a unique clustered index.</span></span> <span data-ttu-id="ca1e1-105">创建唯一聚集索引后，可以创建更多非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-105">After the unique clustered index has been created, you can create more nonclustered indexes.</span></span> <span data-ttu-id="ca1e1-106">为视图创建唯一聚集索引可以提高查询性能，因为视图在数据库中的存储方式与具有聚集索引的表的存储方式相同。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-106">Creating a unique clustered index on a view improves query performance because the view is stored in the database in the same way a table with a clustered index is stored.</span></span> <span data-ttu-id="ca1e1-107">查询优化器可使用索引视图加快执行查询的速度。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-107">The query optimizer may use indexed views to speed up the query execution.</span></span> <span data-ttu-id="ca1e1-108">要使优化器考虑将该视图作为替换，并不需要在查询中引用该视图。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-108">The view does not have to be referenced in the query for the optimizer to consider that view for a substitution.</span></span>  
  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ca1e1-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="ca1e1-109">Before You Begin</span></span>  
 <span data-ttu-id="ca1e1-110">创建索引视图需要执行下列步骤并且这些步骤对于成功实现索引视图而言非常重要：</span><span class="sxs-lookup"><span data-stu-id="ca1e1-110">The following steps are required to create an indexed view and are critical to the successful implementation of the indexed view:</span></span>  
  
1.  <span data-ttu-id="ca1e1-111">验证是否视图中将引用的所有现有表的 SET 选项都正确。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-111">Verify the SET options are correct for all existing tables that will be referenced in the view.</span></span>  
  
2.  <span data-ttu-id="ca1e1-112">在创建任意表和视图之前，验证会话的 SET 选项设置是否正确。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-112">Verify that the SET options for the session are set correctly before you create any tables and the view.</span></span>  
  
3.  <span data-ttu-id="ca1e1-113">验证视图定义是否为确定性的。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-113">Verify that the view definition is deterministic.</span></span>  
  
4.  <span data-ttu-id="ca1e1-114">使用 WITH SCHEMABINDING 选项创建视图。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-114">Create the view by using the WITH SCHEMABINDING option.</span></span>  
  
5.  <span data-ttu-id="ca1e1-115">为视图创建唯一的聚集索引。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-115">Create the unique clustered index on the view.</span></span>  
  
###  <a name="required-set-options-for-indexed-views"></a><a name="Restrictions"></a> <span data-ttu-id="ca1e1-116">索引视图所需的 SET 选项</span><span class="sxs-lookup"><span data-stu-id="ca1e1-116">Required SET Options for Indexed Views</span></span>  
 <span data-ttu-id="ca1e1-117">如果执行查询时启用不同的 SET 选项，则在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中对同一表达式求值会产生不同结果。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-117">Evaluating the same expression can produce different results in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] when different SET options are active when the query is executed.</span></span> <span data-ttu-id="ca1e1-118">例如，将 SET 选项 CONCAT_NULL_YIELDS_NULL 设置为 ON 后，表达式 **'** abc **'** + NULL 会返回值 NULL。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-118">For example, after the SET option CONCAT_NULL_YIELDS_NULL is set to ON, the expression **'** abc **'** + NULL returns the value NULL.</span></span> <span data-ttu-id="ca1e1-119">但将 CONCAT_NULL_YIEDS_NULL 设置为 OFF 后，同一表达式会生成 **'** abc **'**。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-119">However, after CONCAT_NULL_YIEDS_NULL is set to OFF, the same expression produces **'** abc **'**.</span></span>  
  
 <span data-ttu-id="ca1e1-120">为了确保能够正确维护视图并返回一致结果，索引视图需要多个 SET 选项具有固定值。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-120">To make sure that the views can be maintained correctly and return consistent results, indexed views require fixed values for several SET options.</span></span> <span data-ttu-id="ca1e1-121">如果出现下列情况，则必须将下表中的 SET 选项设置为**RequiredValue**列中显示的值：</span><span class="sxs-lookup"><span data-stu-id="ca1e1-121">The SET options in the following table must be set to the values shown in the **RequiredValue** column whenever the following conditions occur:</span></span>  
  
-   <span data-ttu-id="ca1e1-122">创建视图和视图上的后续索引。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-122">The view and subsequent indexes on the view are created.</span></span>  
  
-   <span data-ttu-id="ca1e1-123">在创建表时，在视图中引用的基表。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-123">The base tables referenced in the view at the time the table is created.</span></span>  
  
-   <span data-ttu-id="ca1e1-124">对构成该索引视图的任何表执行了任何插入、更新或删除操作。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-124">There is any insert, update, or delete operation performed on any table that participates in the indexed view.</span></span> <span data-ttu-id="ca1e1-125">此要求包括大容量复制、复制和分布式查询等操作。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-125">This requirement includes operations such as bulk copy, replication, and distributed queries.</span></span>  
  
-   <span data-ttu-id="ca1e1-126">查询优化器使用该索引视图生成查询计划。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-126">The indexed view is used by the query optimizer to produce the query plan.</span></span>  
  
    |<span data-ttu-id="ca1e1-127">SET 选项</span><span class="sxs-lookup"><span data-stu-id="ca1e1-127">SET options</span></span>|<span data-ttu-id="ca1e1-128">所需的值</span><span class="sxs-lookup"><span data-stu-id="ca1e1-128">Required value</span></span>|<span data-ttu-id="ca1e1-129">默认服务器值</span><span class="sxs-lookup"><span data-stu-id="ca1e1-129">Default server value</span></span>|<span data-ttu-id="ca1e1-130">默认</span><span class="sxs-lookup"><span data-stu-id="ca1e1-130">Default</span></span><br /><br /> <span data-ttu-id="ca1e1-131">OLE DB 和 ODBC 值</span><span class="sxs-lookup"><span data-stu-id="ca1e1-131">OLE DB and ODBC value</span></span>|<span data-ttu-id="ca1e1-132">默认</span><span class="sxs-lookup"><span data-stu-id="ca1e1-132">Default</span></span><br /><br /> <span data-ttu-id="ca1e1-133">DB-Library 值</span><span class="sxs-lookup"><span data-stu-id="ca1e1-133">DB-Library value</span></span>|  
    |-----------------|--------------------|--------------------------|---------------------------------------|-----------------------------------|  
    |<span data-ttu-id="ca1e1-134">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="ca1e1-134">ANSI_NULLS</span></span>|<span data-ttu-id="ca1e1-135">ON</span><span class="sxs-lookup"><span data-stu-id="ca1e1-135">ON</span></span>|<span data-ttu-id="ca1e1-136">ON</span><span class="sxs-lookup"><span data-stu-id="ca1e1-136">ON</span></span>|<span data-ttu-id="ca1e1-137">ON</span><span class="sxs-lookup"><span data-stu-id="ca1e1-137">ON</span></span>|<span data-ttu-id="ca1e1-138">OFF</span><span class="sxs-lookup"><span data-stu-id="ca1e1-138">OFF</span></span>|  
    |<span data-ttu-id="ca1e1-139">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="ca1e1-139">ANSI_PADDING</span></span>|<span data-ttu-id="ca1e1-140">ON</span><span class="sxs-lookup"><span data-stu-id="ca1e1-140">ON</span></span>|<span data-ttu-id="ca1e1-141">ON</span><span class="sxs-lookup"><span data-stu-id="ca1e1-141">ON</span></span>|<span data-ttu-id="ca1e1-142">ON</span><span class="sxs-lookup"><span data-stu-id="ca1e1-142">ON</span></span>|<span data-ttu-id="ca1e1-143">OFF</span><span class="sxs-lookup"><span data-stu-id="ca1e1-143">OFF</span></span>|  
    |<span data-ttu-id="ca1e1-144">ANSI_WARNINGS\*</span><span class="sxs-lookup"><span data-stu-id="ca1e1-144">ANSI_WARNINGS\*</span></span>|<span data-ttu-id="ca1e1-145">ON</span><span class="sxs-lookup"><span data-stu-id="ca1e1-145">ON</span></span>|<span data-ttu-id="ca1e1-146">ON</span><span class="sxs-lookup"><span data-stu-id="ca1e1-146">ON</span></span>|<span data-ttu-id="ca1e1-147">ON</span><span class="sxs-lookup"><span data-stu-id="ca1e1-147">ON</span></span>|<span data-ttu-id="ca1e1-148">OFF</span><span class="sxs-lookup"><span data-stu-id="ca1e1-148">OFF</span></span>|  
    |<span data-ttu-id="ca1e1-149">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="ca1e1-149">ARITHABORT</span></span>|<span data-ttu-id="ca1e1-150">ON</span><span class="sxs-lookup"><span data-stu-id="ca1e1-150">ON</span></span>|<span data-ttu-id="ca1e1-151">ON</span><span class="sxs-lookup"><span data-stu-id="ca1e1-151">ON</span></span>|<span data-ttu-id="ca1e1-152">OFF</span><span class="sxs-lookup"><span data-stu-id="ca1e1-152">OFF</span></span>|<span data-ttu-id="ca1e1-153">OFF</span><span class="sxs-lookup"><span data-stu-id="ca1e1-153">OFF</span></span>|  
    |<span data-ttu-id="ca1e1-154">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="ca1e1-154">CONCAT_NULL_YIELDS_NULL</span></span>|<span data-ttu-id="ca1e1-155">ON</span><span class="sxs-lookup"><span data-stu-id="ca1e1-155">ON</span></span>|<span data-ttu-id="ca1e1-156">ON</span><span class="sxs-lookup"><span data-stu-id="ca1e1-156">ON</span></span>|<span data-ttu-id="ca1e1-157">ON</span><span class="sxs-lookup"><span data-stu-id="ca1e1-157">ON</span></span>|<span data-ttu-id="ca1e1-158">OFF</span><span class="sxs-lookup"><span data-stu-id="ca1e1-158">OFF</span></span>|  
    |<span data-ttu-id="ca1e1-159">NUMERIC_ROUNDABORT</span><span class="sxs-lookup"><span data-stu-id="ca1e1-159">NUMERIC_ROUNDABORT</span></span>|<span data-ttu-id="ca1e1-160">OFF</span><span class="sxs-lookup"><span data-stu-id="ca1e1-160">OFF</span></span>|<span data-ttu-id="ca1e1-161">OFF</span><span class="sxs-lookup"><span data-stu-id="ca1e1-161">OFF</span></span>|<span data-ttu-id="ca1e1-162">OFF</span><span class="sxs-lookup"><span data-stu-id="ca1e1-162">OFF</span></span>|<span data-ttu-id="ca1e1-163">OFF</span><span class="sxs-lookup"><span data-stu-id="ca1e1-163">OFF</span></span>|  
    |<span data-ttu-id="ca1e1-164">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="ca1e1-164">QUOTED_IDENTIFIER</span></span>|<span data-ttu-id="ca1e1-165">ON</span><span class="sxs-lookup"><span data-stu-id="ca1e1-165">ON</span></span>|<span data-ttu-id="ca1e1-166">ON</span><span class="sxs-lookup"><span data-stu-id="ca1e1-166">ON</span></span>|<span data-ttu-id="ca1e1-167">ON</span><span class="sxs-lookup"><span data-stu-id="ca1e1-167">ON</span></span>|<span data-ttu-id="ca1e1-168">OFF</span><span class="sxs-lookup"><span data-stu-id="ca1e1-168">OFF</span></span>|  
  
     <span data-ttu-id="ca1e1-169">\*将 ANSI_WARNINGS 设置为 ON 隐式将 ARITHABORT 设置为 ON。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-169">\*Setting ANSI_WARNINGS to ON implicitly sets ARITHABORT to ON.</span></span>  
  
 <span data-ttu-id="ca1e1-170">如果使用的是 OLE DB 或 ODBC 服务器连接，则唯一必须要修改的值是 ARITHABORT 设置。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-170">If you are using an OLE DB or ODBC server connection, the only value that must be modified is the ARITHABORT setting.</span></span> <span data-ttu-id="ca1e1-171">必须使用 **sp_configure** 在服务器级别或使用 SET 命令从应用程序中正确设置所有 DB-Library 值。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-171">All DB-Library values must be set correctly either at the server level by using **sp_configure** or from the application by using the SET command.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ca1e1-172">极力建议在服务器的任一数据库中创建计算列的第一个索引视图或索引后，尽早在服务器范围内将 ARITHABORT 用户选项设置为 ON。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-172">We strongly recommend that you set the ARITHABORT user option to ON server-wide as soon as the first indexed view or index on a computed column is created in any database on the server.</span></span>  
  
### <a name="deterministic-views"></a><span data-ttu-id="ca1e1-173">确定性视图</span><span class="sxs-lookup"><span data-stu-id="ca1e1-173">Deterministic Views</span></span>  
 <span data-ttu-id="ca1e1-174">索引视图的定义必须是确定性的。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-174">The definition of an indexed view must be deterministic.</span></span> <span data-ttu-id="ca1e1-175">如果选择列表中的所有表达式、WHERE 和 GROUP BY 子句都具有确定性，则视图也具有确定性。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-175">A view is deterministic if all expressions in the select list, as well as the WHERE and GROUP BY clauses, are deterministic.</span></span> <span data-ttu-id="ca1e1-176">在使用特定的输入值集对确定性表达式求值时，它们始终返回相同的结果。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-176">Deterministic expressions always return the same result any time they are evaluated with a specific set of input values.</span></span> <span data-ttu-id="ca1e1-177">只有确定性函数可以加入确定性表达式。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-177">Only deterministic functions can participate in deterministic expressions.</span></span> <span data-ttu-id="ca1e1-178">例如，DATEADD 函数是确定性函数，因为对于其三个参数的任何给定参数值集它总是返回相同的结果。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-178">For example, the DATEADD function is deterministic because it always returns the same result for any given set of argument values for its three parameters.</span></span> <span data-ttu-id="ca1e1-179">GETDATE 不是确定性函数，因为总是使用相同的参数调用它，而它在每次执行时返回结果都不同。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-179">GETDATE is not deterministic because it is always invoked with the same argument, but the value it returns changes each time it is executed.</span></span>  
  
 <span data-ttu-id="ca1e1-180">要确定视图列是否为确定性列，请使用 **COLUMNPROPERTY** 函数的 [IsDeterministic](/sql/t-sql/functions/columnproperty-transact-sql) 属性。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-180">To determine whether a view column is deterministic, use the **IsDeterministic** property of the [COLUMNPROPERTY](/sql/t-sql/functions/columnproperty-transact-sql) function.</span></span> <span data-ttu-id="ca1e1-181">使用 COLUMNPROPERTY 函数的 **IsPrecise** 属性确定具有架构绑定的视图中的确定性列是否为精确列。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-181">To determine if a deterministic column in a view with schema binding is precise, use the **IsPrecise** property of the COLUMNPROPERTY function.</span></span> <span data-ttu-id="ca1e1-182">如果为 TRUE，则 COLUMNPROPERTY 返回 1；如果为 FALSE，则返回 0；如果输入无效，则返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-182">COLUMNPROPERTY returns 1 if TRUE, 0 if FALSE, and NULL for input that is not valid.</span></span> <span data-ttu-id="ca1e1-183">这意味着该列不是确定性列，也不是精确列。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-183">This means the column is not deterministic or not precise.</span></span>  
  
 <span data-ttu-id="ca1e1-184">即使是确定性表达式，如果其中包含浮点表达式，则准确结果也会取决于处理器体系结构或微代码的版本。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-184">Even if an expression is deterministic, if it contains float expressions, the exact result may depend on the processor architecture or version of microcode.</span></span> <span data-ttu-id="ca1e1-185">为了确保数据完整性，此类表达式只能作为索引视图的非键列加入。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-185">To ensure data integrity, such expressions can participate only as non-key columns of indexed views.</span></span> <span data-ttu-id="ca1e1-186">不包含浮点表达式的确定性表达式称为精确表达式。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-186">Deterministic expressions that do not contain float expressions are called precise.</span></span> <span data-ttu-id="ca1e1-187">只有精确的确定性表达式才能加入键列，并包含在索引视图的 WHERE 或 GROUP BY 子句中。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-187">Only precise deterministic expressions can participate in key columns and in WHERE or GROUP BY clauses of indexed views.</span></span>  
  
### <a name="additional-requirements"></a><span data-ttu-id="ca1e1-188">其他要求</span><span class="sxs-lookup"><span data-stu-id="ca1e1-188">Additional Requirements</span></span>  
 <span data-ttu-id="ca1e1-189">除对 SET 选项和确定性函数的要求外，还必须满足下列要求：</span><span class="sxs-lookup"><span data-stu-id="ca1e1-189">In addition to the SET options and deterministic function requirements, the following requirements must be met:</span></span>  
  
-   <span data-ttu-id="ca1e1-190">执行 CREATE INDEX 的用户必须是视图所有者。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-190">The user that executes CREATE INDEX must be the owner of the view.</span></span>  
  
-   <span data-ttu-id="ca1e1-191">创建索引时，IGNORE_DUP_KEY 选项必须设置为 OFF（默认设置）。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-191">When you create the index, the IGNORE_DUP_KEY option must be set to OFF (the default setting).</span></span>  
  
-   <span data-ttu-id="ca1e1-192">在视图定义中，必须使用两部分名称（即 _schema_ **.** _tablename_ ）来引用表。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-192">Tables must be referenced by two-part names, _schema_**.**_tablename_ in the view definition.</span></span>  
  
-   <span data-ttu-id="ca1e1-193">必须已使用 WITH SCHEMABINDING 选项创建了在视图中引用的用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-193">User-defined functions referenced in the view must be created by using the WITH SCHEMABINDING option.</span></span>  
  
-   <span data-ttu-id="ca1e1-194">视图中引用的任何用户定义函数都必须由两部分组成的名称（_架构_）引用 **。**_函数_。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-194">Any user-defined functions referenced in the view must be referenced by two-part names, _schema_**.**_function_.</span></span>  
  
-   <span data-ttu-id="ca1e1-195">用户定义函数的数据访问属性必须为 NO SQL，外部访问属性必须是 NO。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-195">The data access property of a user-defined function must be NO SQL, and external access property must be NO.</span></span>  
  
-   <span data-ttu-id="ca1e1-196">公共语言运行时 (CLR) 功能可以出现在视图的选择列表中，但不能作为聚集索引键定义的一部分。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-196">Common language runtime (CLR) functions can appear in the select list of the view, but cannot be part of the definition of the clustered index key.</span></span> <span data-ttu-id="ca1e1-197">CLR 函数不能出现在视图的 WHERE 子句中或视图中的 JOIN 运算的 ON 子句中。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-197">CLR functions cannot appear in the WHERE clause of the view or the ON clause of a JOIN operation in the view.</span></span>  
  
-   <span data-ttu-id="ca1e1-198">在视图定义中使用的 CLR 函数和 CLR 用户定义类型方法必须具有下表所示的属性设置。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-198">CLR functions and methods of CLR user-defined types used in the view definition must have the properties set as shown in the following table.</span></span>  
  
    |<span data-ttu-id="ca1e1-199">properties</span><span class="sxs-lookup"><span data-stu-id="ca1e1-199">Property</span></span>|<span data-ttu-id="ca1e1-200">注意</span><span class="sxs-lookup"><span data-stu-id="ca1e1-200">Note</span></span>|  
    |--------------|----------|  
    |<span data-ttu-id="ca1e1-201">DETERMINISTIC = TRUE</span><span class="sxs-lookup"><span data-stu-id="ca1e1-201">DETERMINISTIC = TRUE</span></span>|<span data-ttu-id="ca1e1-202">必须显式声明为 Microsoft .NET Framework 方法的属性。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-202">Must be declared explicitly as an attribute of the Microsoft .NET Framework method.</span></span>|  
    |<span data-ttu-id="ca1e1-203">PRECISE = TRUE</span><span class="sxs-lookup"><span data-stu-id="ca1e1-203">PRECISE = TRUE</span></span>|<span data-ttu-id="ca1e1-204">必须显式声明为 .NET Framework 方法的属性。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-204">Must be declared explicitly as an attribute of the .NET Framework method.</span></span>|  
    |<span data-ttu-id="ca1e1-205">DATA ACCESS = NO SQL</span><span class="sxs-lookup"><span data-stu-id="ca1e1-205">DATA ACCESS = NO SQL</span></span>|<span data-ttu-id="ca1e1-206">通过将 DataAccess 属性设置为 DataAccessKind.None 并将 SystemDataAccess 属性设置为 SystemDataAccessKind.None 来确定。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-206">Determined by setting DataAccess attribute to DataAccessKind.None and SystemDataAccess attribute to SystemDataAccessKind.None.</span></span>|  
    |<span data-ttu-id="ca1e1-207">EXTERNAL ACCESS = NO</span><span class="sxs-lookup"><span data-stu-id="ca1e1-207">EXTERNAL ACCESS = NO</span></span>|<span data-ttu-id="ca1e1-208">对于 CLR 例程，该属性的默认设置为 NO。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-208">This property defaults to NO for CLR routines.</span></span>|  
  
-   <span data-ttu-id="ca1e1-209">必须使用 WITH SCHEMABINDING 选项创建视图。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-209">The view must be created by using the WITH SCHEMABINDING option.</span></span>  
  
-   <span data-ttu-id="ca1e1-210">视图必须仅引用与视图位于同一数据库中的基表。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-210">The view must reference only base tables that are in the same database as the view.</span></span> <span data-ttu-id="ca1e1-211">视图无法引用其他视图。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-211">The view cannot reference other views.</span></span>  
  
-   <span data-ttu-id="ca1e1-212">视图定义中的 SELECT 语句不能包含下列 Transact-SQL 元素：</span><span class="sxs-lookup"><span data-stu-id="ca1e1-212">The SELECT statement in the view definition must not contain the following Transact-SQL elements:</span></span>  
  
    ||||  
    |-|-|-|  
    |<span data-ttu-id="ca1e1-213">COUNT</span><span class="sxs-lookup"><span data-stu-id="ca1e1-213">COUNT</span></span>|<span data-ttu-id="ca1e1-214">ROWSET 函数（OPENDATASOURCE、OPENQUERY、OPENROWSET 和 OPENXML）</span><span class="sxs-lookup"><span data-stu-id="ca1e1-214">ROWSET functions (OPENDATASOURCE, OPENQUERY, OPENROWSET, AND OPENXML)</span></span>|<span data-ttu-id="ca1e1-215">OUTER 联接（LEFT、RIGHT 或 FULL）</span><span class="sxs-lookup"><span data-stu-id="ca1e1-215">OUTER joins (LEFT, RIGHT, or FULL)</span></span>|  
    |<span data-ttu-id="ca1e1-216">派生表（通过在 FROM 子句中指定 SELECT 语句来定义）</span><span class="sxs-lookup"><span data-stu-id="ca1e1-216">Derived table (defined by specifying a SELECT statement in the FROM clause)</span></span>|<span data-ttu-id="ca1e1-217">自联接</span><span class="sxs-lookup"><span data-stu-id="ca1e1-217">Self-joins</span></span>|<span data-ttu-id="ca1e1-218">通过使用 SELECT \* 或 SELECT *table_name*来指定列。\*</span><span class="sxs-lookup"><span data-stu-id="ca1e1-218">Specifying columns by using SELECT \* or SELECT *table_name*.\*</span></span>|  
    |<span data-ttu-id="ca1e1-219">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="ca1e1-219">DISTINCT</span></span>|<span data-ttu-id="ca1e1-220">STDEV、STDEVP、VAR、VARP 或 AVG</span><span class="sxs-lookup"><span data-stu-id="ca1e1-220">STDEV, STDEVP, VAR, VARP, or AVG</span></span>|<span data-ttu-id="ca1e1-221">公用表表达式 (CTE)</span><span class="sxs-lookup"><span data-stu-id="ca1e1-221">Common table expression (CTE)</span></span>|  
    |<span data-ttu-id="ca1e1-222">`float`\*、 `text` 、 `ntext` 、 `image` 、 `XML` 或 `filestream` 列</span><span class="sxs-lookup"><span data-stu-id="ca1e1-222">`float`\*, `text`, `ntext`, `image`, `XML`, or `filestream` columns</span></span>|<span data-ttu-id="ca1e1-223">子查询</span><span class="sxs-lookup"><span data-stu-id="ca1e1-223">Subquery</span></span>|<span data-ttu-id="ca1e1-224">包括排名或聚合开窗函数的 OVER 子句</span><span class="sxs-lookup"><span data-stu-id="ca1e1-224">OVER clause, which includes ranking or aggregate window functions</span></span>|  
    |<span data-ttu-id="ca1e1-225">全文谓词（CONTAIN、FREETEXT）</span><span class="sxs-lookup"><span data-stu-id="ca1e1-225">Full-text predicates (CONTAIN, FREETEXT)</span></span>|<span data-ttu-id="ca1e1-226">引用可为 Null 的表达式的 SUM 函数</span><span class="sxs-lookup"><span data-stu-id="ca1e1-226">SUM function that references a nullable expression</span></span>|<span data-ttu-id="ca1e1-227">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="ca1e1-227">ORDER BY</span></span>|  
    |<span data-ttu-id="ca1e1-228">CLR 用户定义聚合函数</span><span class="sxs-lookup"><span data-stu-id="ca1e1-228">CLR user-defined aggregate function</span></span>|<span data-ttu-id="ca1e1-229">TOP</span><span class="sxs-lookup"><span data-stu-id="ca1e1-229">TOP</span></span>|<span data-ttu-id="ca1e1-230">CUBE、ROLLUP 或 GROUPING SETS 运算符</span><span class="sxs-lookup"><span data-stu-id="ca1e1-230">CUBE, ROLLUP, or GROUPING SETS operators</span></span>|  
    |<span data-ttu-id="ca1e1-231">MIN、MAX</span><span class="sxs-lookup"><span data-stu-id="ca1e1-231">MIN, MAX</span></span>|<span data-ttu-id="ca1e1-232">UNION、EXCEPT 或 INTERSECT 运算符</span><span class="sxs-lookup"><span data-stu-id="ca1e1-232">UNION, EXCEPT, or INTERSECT operators</span></span>|<span data-ttu-id="ca1e1-233">TABLESAMPLE</span><span class="sxs-lookup"><span data-stu-id="ca1e1-233">TABLESAMPLE</span></span>|  
    |<span data-ttu-id="ca1e1-234">表变量</span><span class="sxs-lookup"><span data-stu-id="ca1e1-234">Table variables</span></span>|<span data-ttu-id="ca1e1-235">OUTER APPLY 或 CROSS APPLY</span><span class="sxs-lookup"><span data-stu-id="ca1e1-235">OUTER APPLY or CROSS APPLY</span></span>|<span data-ttu-id="ca1e1-236">PIVOT、UNPIVOT</span><span class="sxs-lookup"><span data-stu-id="ca1e1-236">PIVOT, UNPIVOT</span></span>|  
    |<span data-ttu-id="ca1e1-237">稀疏列集</span><span class="sxs-lookup"><span data-stu-id="ca1e1-237">Sparse column sets</span></span>|<span data-ttu-id="ca1e1-238">内联或多语句表值函数</span><span class="sxs-lookup"><span data-stu-id="ca1e1-238">Inline or multi-statement table-valued functions</span></span>|<span data-ttu-id="ca1e1-239">OFFSET</span><span class="sxs-lookup"><span data-stu-id="ca1e1-239">OFFSET</span></span>|  
    |<span data-ttu-id="ca1e1-240">CHECKSUM_AGG</span><span class="sxs-lookup"><span data-stu-id="ca1e1-240">CHECKSUM_AGG</span></span>|||  
  
     <span data-ttu-id="ca1e1-241">\*索引视图可以包含 `float` 列，但聚集索引键中不能包含此类列。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-241">\*The indexed view can contain `float` columns; however, such columns cannot be included in the clustered index key.</span></span>  
  
-   <span data-ttu-id="ca1e1-242">如果存在 GROUP BY，则 VIEW 定义必须包含 COUNT_BIG(\*)，并且不得包含 HAVING。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-242">If GROUP BY is present, the VIEW definition must contain COUNT_BIG(\*) and must not contain HAVING.</span></span> <span data-ttu-id="ca1e1-243">这些 GROUP BY 限制仅适用于索引视图定义。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-243">These GROUP BY restrictions are applicable only to the indexed view definition.</span></span> <span data-ttu-id="ca1e1-244">即使一个索引视图不满足这些 GROUP BY 限制，查询也可以在其执行计划中使用该视图。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-244">A query can use an indexed view in its execution plan even if it does not satisfy these GROUP BY restrictions.</span></span>  
  
-   <span data-ttu-id="ca1e1-245">如果视图定义包含 GROUP BY 子句，则唯一聚集索引的键只能引用 GROUP BY 子句中指定的列。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-245">If the view definition contains a GROUP BY clause, the key of the unique clustered index can reference only the columns specified in the GROUP BY clause.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="ca1e1-246">建议</span><span class="sxs-lookup"><span data-stu-id="ca1e1-246">Recommendations</span></span>  
 <span data-ttu-id="ca1e1-247">引用索引视图中的 `datetime` 和 `smalldatetime` 字符串文字时，建议使用确定性日期格式样式将文字显式转换为所需日期类型。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-247">When you refer to `datetime` and `smalldatetime` string literals in indexed views, we recommend that you explicitly convert the literal to the date type you want by using a deterministic date format style.</span></span> <span data-ttu-id="ca1e1-248">有关确定性日期格式样式的列表，请参阅 [CAST 与 CONVERT (Transact-SQL)](/sql/t-sql/functions/cast-and-convert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-248">For a list of the date format styles that are deterministic, see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span> <span data-ttu-id="ca1e1-249">将字符串隐式转换为 `datetime` 或 `smalldatetime` 所涉及的表达式被视为具有不确定性。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-249">Expressions that involve implicit conversion of character strings to `datetime` or `smalldatetime` are considered nondeterministic.</span></span> <span data-ttu-id="ca1e1-250">这是因为结果取决于服务器会话的 LANGUAGE 和 DATEFORMAT 设置。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-250">This is because the results depend on the LANGUAGE and DATEFORMAT settings of the server session.</span></span> <span data-ttu-id="ca1e1-251">例如，表达式 `CONVERT (datetime, '30 listopad 1996', 113)` 的结果取决于 LANGUAGE 设置，因为字符串`listopad`在不同语言中表示不同的月份。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-251">For example, the results of the expression `CONVERT (datetime, '30 listopad 1996', 113)` depend on the LANGUAGE setting because the string '`listopad`' means different months in different languages.</span></span> <span data-ttu-id="ca1e1-252">同样，在 `DATEADD(mm,3,'2000-12-01')`表达式中， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 基于 DATEFORMAT 设置解释 `'2000-12-01'` 字符串。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-252">Similarly, in the expression `DATEADD(mm,3,'2000-12-01')`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interprets the string `'2000-12-01'` based on the DATEFORMAT setting.</span></span>  
  
 <span data-ttu-id="ca1e1-253">非 Unicode 字符数据在排序规则间的隐式转换也被视为具有不确定性。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-253">Implicit conversion of non-Unicode character data between collations is also considered nondeterministic.</span></span>  
  
###  <a name="considerations"></a><a name="Considerations"></a> <span data-ttu-id="ca1e1-254">注意事项</span><span class="sxs-lookup"><span data-stu-id="ca1e1-254">Considerations</span></span>  
 <span data-ttu-id="ca1e1-255">索引视图中列的 **large_value_types_out_of_row** 选项的设置继承的是基表中相应列的设置。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-255">The setting of the **large_value_types_out_of_row** option of columns in an indexed view is inherited from the setting of the corresponding column in the base table.</span></span> <span data-ttu-id="ca1e1-256">此值是使用 [sp_tableoption](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql)设置的。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-256">This value is set by using [sp_tableoption](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql).</span></span> <span data-ttu-id="ca1e1-257">从表达式组成的列的默认设置为 0。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-257">The default setting for columns formed from expressions is 0.</span></span> <span data-ttu-id="ca1e1-258">这意味着大值类型存储在行内。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-258">This means that large value types are stored in-row.</span></span>  
  
 <span data-ttu-id="ca1e1-259">可以对已分区表创建索引视图，并可以由其自行分区。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-259">Indexed views can be created on a partitioned table, and can themselves be partitioned.</span></span>  
  
 <span data-ttu-id="ca1e1-260">若要防止 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 使用索引视图，请在查询中包含 OPTION (EXPAND VIEWS) 提示。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-260">To prevent the [!INCLUDE[ssDE](../../includes/ssde-md.md)] from using indexed views, include the OPTION (EXPAND VIEWS) hint on the query.</span></span> <span data-ttu-id="ca1e1-261">此外，任何所列选项设置不正确均会阻止优化器使用视图上的索引。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-261">Also, if any of the listed options are incorrectly set, this will prevent the optimizer from using the indexes on the views.</span></span> <span data-ttu-id="ca1e1-262">有关 OPTION (EXPAND VIEWS) 提示的详细信息，请参阅 [SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-262">For more information about the OPTION (EXPAND VIEWS) hint, see [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql).</span></span>  
  
 <span data-ttu-id="ca1e1-263">若删除视图，该视图的所有索引也将被删除。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-263">All indexes on a view are dropped when the view is dropped.</span></span> <span data-ttu-id="ca1e1-264">若删除聚集索引，视图的所有非聚集索引和自动创建的统计信息也将被删除。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-264">All nonclustered indexes and auto-created statistics on the view are dropped when the clustered index is dropped.</span></span> <span data-ttu-id="ca1e1-265">视图中用户创建的统计信息受到维护。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-265">User-created statistics on the view are maintained.</span></span> <span data-ttu-id="ca1e1-266">非聚集索引可以分别删除。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-266">Nonclustered indexes can be individually dropped.</span></span> <span data-ttu-id="ca1e1-267">删除视图的聚集索引将删除存储的结果集，并且优化器将重新像处理标准视图那样处理视图。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-267">Dropping the clustered index on the view removes the stored result set, and the optimizer returns to processing the view like a standard view.</span></span>  
  
 <span data-ttu-id="ca1e1-268">可以禁用表和视图的索引。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-268">Indexes on tables and views can be disabled.</span></span> <span data-ttu-id="ca1e1-269">禁用表的聚集索引时，与该表关联的视图的索引也将被禁用。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-269">When a clustered index on a table is disabled, indexes on views associated with the table are also disabled.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ca1e1-270">Security</span><span class="sxs-lookup"><span data-stu-id="ca1e1-270">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ca1e1-271">权限</span><span class="sxs-lookup"><span data-stu-id="ca1e1-271">Permissions</span></span>  
 <span data-ttu-id="ca1e1-272">要求在数据库中具有 CREATE VIEW 权限，并具有在其中创建视图的架构的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-272">Requires CREATE VIEW permission in the database and ALTER permission on the schema in which the view is being created.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ca1e1-273">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ca1e1-273">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-indexed-view"></a><span data-ttu-id="ca1e1-274">创建索引视图</span><span class="sxs-lookup"><span data-stu-id="ca1e1-274">To create an indexed view</span></span>  
  
1.  <span data-ttu-id="ca1e1-275">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-275">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ca1e1-276">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-276">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ca1e1-277">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-277">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ca1e1-278">该示例将创建一个视图并为该视图创建索引。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-278">The example creates a view and an index on that view.</span></span> <span data-ttu-id="ca1e1-279">包含两个使用该索引视图的查询。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-279">Two queries are included that use the indexed view.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    --Set the options to support indexed views.  
    SET NUMERIC_ROUNDABORT OFF;  
    SET ANSI_PADDING, ANSI_WARNINGS, CONCAT_NULL_YIELDS_NULL, ARITHABORT,  
        QUOTED_IDENTIFIER, ANSI_NULLS ON;  
    GO  
    --Create view with schemabinding.  
    IF OBJECT_ID ('Sales.vOrders', 'view') IS NOT NULL  
    DROP VIEW Sales.vOrders ;  
    GO  
    CREATE VIEW Sales.vOrders  
    WITH SCHEMABINDING  
    AS  
        SELECT SUM(UnitPrice*OrderQty*(1.00-UnitPriceDiscount)) AS Revenue,  
            OrderDate, ProductID, COUNT_BIG(*) AS COUNT  
        FROM Sales.SalesOrderDetail AS od, Sales.SalesOrderHeader AS o  
        WHERE od.SalesOrderID = o.SalesOrderID  
        GROUP BY OrderDate, ProductID;  
    GO  
    --Create an index on the view.  
    CREATE UNIQUE CLUSTERED INDEX IDX_V1   
        ON Sales.vOrders (OrderDate, ProductID);  
    GO  
    --This query can use the indexed view even though the view is   
    --not specified in the FROM clause.  
    SELECT SUM(UnitPrice*OrderQty*(1.00-UnitPriceDiscount)) AS Rev,   
        OrderDate, ProductID  
    FROM Sales.SalesOrderDetail AS od  
        JOIN Sales.SalesOrderHeader AS o ON od.SalesOrderID=o.SalesOrderID  
            AND ProductID BETWEEN 700 and 800  
            AND OrderDate >= CONVERT(datetime,'05/01/2002',101)  
    GROUP BY OrderDate, ProductID  
    ORDER BY Rev DESC;  
    GO  
    --This query can use the above indexed view.  
    SELECT  OrderDate, SUM(UnitPrice*OrderQty*(1.00-UnitPriceDiscount)) AS Rev  
    FROM Sales.SalesOrderDetail AS od  
        JOIN Sales.SalesOrderHeader AS o ON od.SalesOrderID=o.SalesOrderID  
            AND DATEPART(mm,OrderDate)= 3  
            AND DATEPART(yy,OrderDate) = 2002  
    GROUP BY OrderDate  
    ORDER BY OrderDate ASC;  
    GO  
    ```  
  
 <span data-ttu-id="ca1e1-280">有关详细信息，请参阅 [CREATE VIEW (Transact-SQL)](/sql/t-sql/statements/create-view-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ca1e1-280">For more information, see [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca1e1-281">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ca1e1-281">See Also</span></span>  
 <span data-ttu-id="ca1e1-282">[CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ca1e1-282">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="ca1e1-283">[SET ANSI_NULLS (Transact-SQL)](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ca1e1-283">[SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span></span>  
 <span data-ttu-id="ca1e1-284">[SET ANSI_PADDING (Transact-SQL)](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ca1e1-284">[SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span></span>  
 <span data-ttu-id="ca1e1-285">[SET ANSI_WARNINGS (Transact-SQL)](/sql/t-sql/statements/set-ansi-warnings-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ca1e1-285">[SET ANSI_WARNINGS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql) </span></span>  
 <span data-ttu-id="ca1e1-286">[SET ARITHABORT (Transact-SQL)](/sql/t-sql/statements/set-arithabort-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ca1e1-286">[SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql) </span></span>  
 <span data-ttu-id="ca1e1-287">[SET CONCAT_NULL_YIELDS_NULL (Transact-SQL)](/sql/t-sql/statements/set-concat-null-yields-null-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ca1e1-287">[SET CONCAT_NULL_YIELDS_NULL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-concat-null-yields-null-transact-sql) </span></span>  
 <span data-ttu-id="ca1e1-288">[SET NUMERIC_ROUNDABORT (Transact-SQL)](/sql/t-sql/statements/set-numeric-roundabort-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ca1e1-288">[SET NUMERIC_ROUNDABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-numeric-roundabort-transact-sql) </span></span>  
 [<span data-ttu-id="ca1e1-289">SET QUOTED_IDENTIFIER (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ca1e1-289">SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-quoted-identifier-transact-sql)  
  
  
