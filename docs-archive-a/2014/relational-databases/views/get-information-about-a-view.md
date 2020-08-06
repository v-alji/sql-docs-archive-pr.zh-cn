---
title: 获取有关视图的信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.viewproperties.general.f1
helpviewer_keywords:
- views [SQL Server], status information
- metadata [SQL Server], views
- dependencies [SQL Server], views
- displaying view information
- views [SQL Server], metadata
- viewing view information
- status information [SQL Server], views
- view dependencies
ms.assetid: 05a73e33-8f85-4fb6-80c1-1b659e753403
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4277aad4c1de0140606575c7ba437408518b3c8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577457"
---
# <a name="get-information-about-a-view"></a><span data-ttu-id="31543-102">获取有关视图的信息</span><span class="sxs-lookup"><span data-stu-id="31543-102">Get Information About a View</span></span>
  <span data-ttu-id="31543-103">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中，通过使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 可以获取有关视图的定义或属性的信息。</span><span class="sxs-lookup"><span data-stu-id="31543-103">You can gain information about a view's definition or properties in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="31543-104">您可能需要查看视图定义以了解数据从源表中的提取方式，或查看视图所定义的数据。</span><span class="sxs-lookup"><span data-stu-id="31543-104">You may need to see the definition of the view to understand how its data is derived from the source tables or to see the data defined by the view.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="31543-105">如果更改视图所引用对象的名称，则必须更改视图，使其文本反映新的名称。</span><span class="sxs-lookup"><span data-stu-id="31543-105">If you change the name of an object referenced by a view, you must modify the view so that its text reflects the new name.</span></span> <span data-ttu-id="31543-106">因此，在重命名对象之前，首先显示该对象的依赖关系，以确定即将发生的更改是否会影响任何视图。</span><span class="sxs-lookup"><span data-stu-id="31543-106">Therefore, before renaming an object, display the dependencies of the object first to determine if any views are affected by the proposed change.</span></span>  
  
 <span data-ttu-id="31543-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="31543-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="31543-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="31543-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="31543-109">安全性</span><span class="sxs-lookup"><span data-stu-id="31543-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="31543-110">**获取有关视图的信息，使用：**</span><span class="sxs-lookup"><span data-stu-id="31543-110">**To get information about a view, using:**</span></span>  
  
     [<span data-ttu-id="31543-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="31543-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="31543-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="31543-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="31543-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="31543-113">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="31543-114">Security</span><span class="sxs-lookup"><span data-stu-id="31543-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="31543-115">权限</span><span class="sxs-lookup"><span data-stu-id="31543-115">Permissions</span></span>  
 <span data-ttu-id="31543-116">使用 `sp_helptext` 返回视图的定义需要 **public** 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="31543-116">Using `sp_helptext` to return the definition of a view requires membership in the **public** role.</span></span> <span data-ttu-id="31543-117">使用 `sys.sql_expression_dependencies` 查找视图的所有依赖关系需要对该数据库的 VIEW DEFINITION 权限以及对数据库的 `sys.sql_expression_dependencies` 的 SELECT 权限。</span><span class="sxs-lookup"><span data-stu-id="31543-117">Using `sys.sql_expression_dependencies` to find all the dependencies on a view requires VIEW DEFINITION permission on the database and SELECT permission on `sys.sql_expression_dependencies` for the database.</span></span> <span data-ttu-id="31543-118">系统对象定义（如 SELECT OBJECT_DEFINITION 中返回的对象定义）是公开可见的。</span><span class="sxs-lookup"><span data-stu-id="31543-118">System object definitions, like the ones returned in SELECT OBJECT_DEFINITION, are publicly visible.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="31543-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="31543-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="get-view-properties-by-using-object-explorer"></a><span data-ttu-id="31543-120">使用对象资源管理器获取视图属性</span><span class="sxs-lookup"><span data-stu-id="31543-120">Get view properties by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="31543-121">在 **“对象资源管理器”** 中，单击包含要查看属性的视图的数据库旁边的加号，然后单击加号以展开 **“视图”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="31543-121">In **Object Explorer**, click the plus sign next to the database that contains the view to which you want to view the properties, and then click the plus sign to expand the **Views** folder.</span></span>  
  
2.  <span data-ttu-id="31543-122">右键单击要查看其属性的视图，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="31543-122">Right-click the view of which you want to view the properties and select **Properties**.</span></span>  
  
     <span data-ttu-id="31543-123">**“视图属性”** 对话框中显示以下属性：</span><span class="sxs-lookup"><span data-stu-id="31543-123">The following properties show in the **View Properties** dialog box.</span></span>  
  
     <span data-ttu-id="31543-124">**Database**</span><span class="sxs-lookup"><span data-stu-id="31543-124">**Database**</span></span>  
     <span data-ttu-id="31543-125">包含此视图的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="31543-125">The name of the database containing this view.</span></span>  
  
     <span data-ttu-id="31543-126">**Server**</span><span class="sxs-lookup"><span data-stu-id="31543-126">**Server**</span></span>  
     <span data-ttu-id="31543-127">当前服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="31543-127">The name of the current server instance.</span></span>  
  
     <span data-ttu-id="31543-128">**用户**</span><span class="sxs-lookup"><span data-stu-id="31543-128">**User**</span></span>  
     <span data-ttu-id="31543-129">此连接的用户名。</span><span class="sxs-lookup"><span data-stu-id="31543-129">The name of the user of this connection.</span></span>  
  
     <span data-ttu-id="31543-130">**创建日期**</span><span class="sxs-lookup"><span data-stu-id="31543-130">**Created date**</span></span>  
     <span data-ttu-id="31543-131">显示视图的创建日期。</span><span class="sxs-lookup"><span data-stu-id="31543-131">Displays the date the view was created.</span></span>  
  
     <span data-ttu-id="31543-132">**名称**</span><span class="sxs-lookup"><span data-stu-id="31543-132">**Name**</span></span>  
     <span data-ttu-id="31543-133">当前视图的名称。</span><span class="sxs-lookup"><span data-stu-id="31543-133">The name of the current view.</span></span>  
  
     <span data-ttu-id="31543-134">**架构**</span><span class="sxs-lookup"><span data-stu-id="31543-134">**Schema**</span></span>  
     <span data-ttu-id="31543-135">显示视图所属的架构。</span><span class="sxs-lookup"><span data-stu-id="31543-135">Displays the schema that owns the view.</span></span>  
  
     <span data-ttu-id="31543-136">**系统对象**</span><span class="sxs-lookup"><span data-stu-id="31543-136">**System object**</span></span>  
     <span data-ttu-id="31543-137">指示视图是否为系统对象。</span><span class="sxs-lookup"><span data-stu-id="31543-137">Indicates whether the view is a system object.</span></span> <span data-ttu-id="31543-138">值为 True 和 False。</span><span class="sxs-lookup"><span data-stu-id="31543-138">Values are True and False.</span></span>  
  
     <span data-ttu-id="31543-139">**ANSI NULLs**</span><span class="sxs-lookup"><span data-stu-id="31543-139">**ANSI NULLs**</span></span>  
     <span data-ttu-id="31543-140">指示创建对象时是否选择了 ANSI NULLs 选项。</span><span class="sxs-lookup"><span data-stu-id="31543-140">Indicates if the object was created with the ANSI NULLs option.</span></span>  
  
     <span data-ttu-id="31543-141">**已加密**</span><span class="sxs-lookup"><span data-stu-id="31543-141">**Encrypted**</span></span>  
     <span data-ttu-id="31543-142">指示视图是否已加密。</span><span class="sxs-lookup"><span data-stu-id="31543-142">Indicates whether the view is encrypted.</span></span> <span data-ttu-id="31543-143">值为 True 和 False。</span><span class="sxs-lookup"><span data-stu-id="31543-143">Values are True and False.</span></span>  
  
     <span data-ttu-id="31543-144">**带引号的标识符**</span><span class="sxs-lookup"><span data-stu-id="31543-144">**Quoted identifier**</span></span>  
     <span data-ttu-id="31543-145">指示创建对象时是否选择了“带引号的标识符”选项。</span><span class="sxs-lookup"><span data-stu-id="31543-145">Indicates if the object was created with the quoted identifier option.</span></span>  
  
     <span data-ttu-id="31543-146">**架构已绑定**</span><span class="sxs-lookup"><span data-stu-id="31543-146">**Schema bound**</span></span>  
     <span data-ttu-id="31543-147">指示视图是否绑定到架构。</span><span class="sxs-lookup"><span data-stu-id="31543-147">Indicates whether the view is schema-bound.</span></span> <span data-ttu-id="31543-148">值为 True 和 False。</span><span class="sxs-lookup"><span data-stu-id="31543-148">Values are True and False.</span></span> <span data-ttu-id="31543-149">有关绑定到架构的视图的信息，请参阅 [CREATE VIEW (Transact-SQL)](/sql/t-sql/statements/create-view-transact-sql) 的 SCHEMABINDING 部分。</span><span class="sxs-lookup"><span data-stu-id="31543-149">For information about schema-bound views, see the SCHEMABINDING portion of [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).</span></span>  
  
#### <a name="getting-view-properties-by-using-the-view-designer-tool"></a><span data-ttu-id="31543-150">使用视图设计器工具获取视图属性</span><span class="sxs-lookup"><span data-stu-id="31543-150">Getting view properties by using the View Designer tool</span></span>  
  
1.  <span data-ttu-id="31543-151">在 **“对象资源管理器”** 中，展开包含要查看属性的视图的数据库，然后展开 **“视图”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="31543-151">In **Object Explorer**, expand the database that contains the view to which you want to view the properties, and then expand the **Views** folder.</span></span>  
  
2.  <span data-ttu-id="31543-152">右键单击要查看其属性的视图，然后选择“设计”  。</span><span class="sxs-lookup"><span data-stu-id="31543-152">Right-click the view of which you want to view the properties and select **Design**.</span></span>  
  
3.  <span data-ttu-id="31543-153">右键单击“关系图”窗格中的空白区域，再单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="31543-153">Right-click in the blank space of the Diagram pane and click **Properties**.</span></span>  
  
     <span data-ttu-id="31543-154">**“属性”** 窗格中显示以下属性：</span><span class="sxs-lookup"><span data-stu-id="31543-154">The following properties show in the **Properties** pane.</span></span>  
  
     <span data-ttu-id="31543-155">**(名称)**</span><span class="sxs-lookup"><span data-stu-id="31543-155">**(Name)**</span></span>  
     <span data-ttu-id="31543-156">当前视图的名称。</span><span class="sxs-lookup"><span data-stu-id="31543-156">The name of the current view.</span></span>  
  
     <span data-ttu-id="31543-157">**Database Name**</span><span class="sxs-lookup"><span data-stu-id="31543-157">**Database Name**</span></span>  
     <span data-ttu-id="31543-158">包含此视图的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="31543-158">The name of the database containing this view.</span></span>  
  
     <span data-ttu-id="31543-159">**说明**</span><span class="sxs-lookup"><span data-stu-id="31543-159">**Description**</span></span>  
     <span data-ttu-id="31543-160">对当前视图的简短说明。</span><span class="sxs-lookup"><span data-stu-id="31543-160">A brief description of the current view.</span></span>  
  
     <span data-ttu-id="31543-161">**架构**</span><span class="sxs-lookup"><span data-stu-id="31543-161">**Schema**</span></span>  
     <span data-ttu-id="31543-162">显示视图所属的架构。</span><span class="sxs-lookup"><span data-stu-id="31543-162">Displays the schema that owns the view.</span></span>  
  
     <span data-ttu-id="31543-163">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="31543-163">**Server Name**</span></span>  
     <span data-ttu-id="31543-164">当前服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="31543-164">The name of the current server instance.</span></span>  
  
     <span data-ttu-id="31543-165">**绑定到架构**</span><span class="sxs-lookup"><span data-stu-id="31543-165">**Bind to Schema**</span></span>  
     <span data-ttu-id="31543-166">防止用户以会使视图定义失效的任何方式修改影响此视图的基础对象。</span><span class="sxs-lookup"><span data-stu-id="31543-166">Prevents users from modifying the underlying objects that contribute to this view in any way that would invalidate the view definition.</span></span>  
  
     <span data-ttu-id="31543-167">**具有确定性**</span><span class="sxs-lookup"><span data-stu-id="31543-167">**Deterministic**</span></span>  
     <span data-ttu-id="31543-168">显示是否可以明确地确定所选列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="31543-168">Shows whether the data type of the selected column can be determined with certainty</span></span>  
  
     <span data-ttu-id="31543-169">**非重复值**</span><span class="sxs-lookup"><span data-stu-id="31543-169">**Distinct Values**</span></span>  
     <span data-ttu-id="31543-170">指定查询将在视图中筛选出重复值。</span><span class="sxs-lookup"><span data-stu-id="31543-170">Specifies that the query will filter out duplicates in the view.</span></span> <span data-ttu-id="31543-171">当只使用表中的部分列并且这些列可能包含重复值时，或者当联接两个或更多表的过程会在结果集中产生重复行时，此选项非常有用。</span><span class="sxs-lookup"><span data-stu-id="31543-171">This option is useful when you are using only some of the columns from a table and those columns might contain duplicate values, or when the process of joining two or more tables produces duplicate rows in the result set.</span></span> <span data-ttu-id="31543-172">选择该选项等效于向 SQL 窗格内的语句中插入关键字 DISTINCT。</span><span class="sxs-lookup"><span data-stu-id="31543-172">Choosing this option is equivalent to inserting the keyword DISTINCT into the statement in the SQL pane.</span></span>  
  
     <span data-ttu-id="31543-173">**GROUP BY 扩展**</span><span class="sxs-lookup"><span data-stu-id="31543-173">**GROUP BY Extension**</span></span>  
     <span data-ttu-id="31543-174">指定对于基于聚合查询的视图，附加选项可用。</span><span class="sxs-lookup"><span data-stu-id="31543-174">Specifies that additional options for views based on aggregate queries are available.</span></span>  
  
     <span data-ttu-id="31543-175">**输出所有列**</span><span class="sxs-lookup"><span data-stu-id="31543-175">**Output All Columns**</span></span>  
     <span data-ttu-id="31543-176">显示所有列是否都由所选视图返回。</span><span class="sxs-lookup"><span data-stu-id="31543-176">Shows whether all columns are returned by the selected view.</span></span> <span data-ttu-id="31543-177">这是在创建视图时设置的。</span><span class="sxs-lookup"><span data-stu-id="31543-177">This is set at the time the view is created.</span></span>  
  
     <span data-ttu-id="31543-178">**SQL 注释**</span><span class="sxs-lookup"><span data-stu-id="31543-178">**SQL Comment**</span></span>  
     <span data-ttu-id="31543-179">显示 SQL 语句的说明。</span><span class="sxs-lookup"><span data-stu-id="31543-179">Shows a description of the SQL statements.</span></span> <span data-ttu-id="31543-180">若要查看或编辑完整的说明，请单击相应的说明，再单击属性右侧的省略号 (…)  。</span><span class="sxs-lookup"><span data-stu-id="31543-180">To see the entire description, or to edit it, click the description and then click the ellipses **(...)** to the right of the property.</span></span> <span data-ttu-id="31543-181">您的注释可以包含视图使用者和使用时间等信息。</span><span class="sxs-lookup"><span data-stu-id="31543-181">Your comments might include information such as who uses the view and when they use it.</span></span>  
  
     <span data-ttu-id="31543-182">**Top 规范**</span><span class="sxs-lookup"><span data-stu-id="31543-182">**Top Specification**</span></span>  
     <span data-ttu-id="31543-183">展开此项可显示“Top”  、“表达式”  、“百分比”  和“等同值”  属性的属性。</span><span class="sxs-lookup"><span data-stu-id="31543-183">Expands to show properties for the **Top**, **Expression**, **Percent**, and **With Ties** properties.</span></span>  
  
     <span data-ttu-id="31543-184">**(最前面)**</span><span class="sxs-lookup"><span data-stu-id="31543-184">**(Top)**</span></span>  
     <span data-ttu-id="31543-185">指定视图将包括 TOP 子句，该子句只返回结果集中的前 n 行或前百分之 n 行。</span><span class="sxs-lookup"><span data-stu-id="31543-185">Specifies that the view will include a TOP clause, which returns only the first n rows or first n percentage of rows in the result set.</span></span> <span data-ttu-id="31543-186">默认情况下，视图将在结果集中返回前 10 行。</span><span class="sxs-lookup"><span data-stu-id="31543-186">The default is that the view returns the first 10 rows in the result set.</span></span> <span data-ttu-id="31543-187">使用此项可更改返回的行数或指定不同的百分比</span><span class="sxs-lookup"><span data-stu-id="31543-187">Use this to change the number of rows to return or to specify a different percentage</span></span>  
  
     <span data-ttu-id="31543-188">**表达式**</span><span class="sxs-lookup"><span data-stu-id="31543-188">**Expression**</span></span>  
     <span data-ttu-id="31543-189">显示视图将返回的百分比（如果“百分比”  设置为“是”  ）或记录（如果“百分比”  设置为“否”  ）。</span><span class="sxs-lookup"><span data-stu-id="31543-189">Shows what percent (if **Percent** is set to **Yes**) or records (if **Percent** is set to **No**) that the view will return.</span></span>  
  
     <span data-ttu-id="31543-190">**百分比**</span><span class="sxs-lookup"><span data-stu-id="31543-190">**Percent**</span></span>  
     <span data-ttu-id="31543-191">指定查询将包含一个 **TOP** 子句，仅返回结果集中前百分之 n 行</span><span class="sxs-lookup"><span data-stu-id="31543-191">Specifies that the query will include a **TOP** clause, returning only the first n percentage of rows in the result set</span></span>  
  
     <span data-ttu-id="31543-192">**With Ties**</span><span class="sxs-lookup"><span data-stu-id="31543-192">**With Ties**</span></span>  
     <span data-ttu-id="31543-193">指定视图将包括 **WITH TIES** 子句。</span><span class="sxs-lookup"><span data-stu-id="31543-193">Specifies that the view will include a **WITH TIES** clause.</span></span> <span data-ttu-id="31543-194">如果视图包含**WITH TIES** 子句和基于百分比的 **WITH TIES** 子句， **WITH TIES** 将非常有用。</span><span class="sxs-lookup"><span data-stu-id="31543-194">**WITH TIES** is useful if a view includes an **ORDER BY** clause and a **TOP** clause based on percentage.</span></span> <span data-ttu-id="31543-195">如果设置了该选项，并且百分比截止位置在一组行的中间，且这些行在 **ORDER BY** 子句中具有相同的值，则视图将会扩展，以包含所有这样的行。</span><span class="sxs-lookup"><span data-stu-id="31543-195">If this option is set, and if the percentage cutoff falls in the middle of a set of rows with identical values in the **ORDER BY** clause, the view is extended to include all such rows.</span></span>  
  
     <span data-ttu-id="31543-196">**更新规范**</span><span class="sxs-lookup"><span data-stu-id="31543-196">**Update Specification**</span></span>  
     <span data-ttu-id="31543-197">展开此项可显示“使用视图规则更新”  和“Check 选项”  属性。</span><span class="sxs-lookup"><span data-stu-id="31543-197">Expands to show properties for the **Update Using View Rules** and **Check Option** properties.</span></span>  
  
     <span data-ttu-id="31543-198">**(使用视图规则更新)**</span><span class="sxs-lookup"><span data-stu-id="31543-198">**(Update Using View Rules)**</span></span>  
     <span data-ttu-id="31543-199">指示对视图的所有更新和插入将由 Microsoft 数据访问组件 (MDAC) 转换为引用视图的 SQL 语句，而非转换为直接引用视图的基表的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="31543-199">Indicates that all updates and insertions to the view will be translated by Microsoft Data Access Components (MDAC) into SQL statements that refer to the view, rather than into SQL statements that refer directly to the view's base tables.</span></span>  
  
     <span data-ttu-id="31543-200">在某些情况下，MDAC 将视图更新和视图插入操作表示为针对视图的基本基表的更新和插入。</span><span class="sxs-lookup"><span data-stu-id="31543-200">In some cases, MDAC manifests view update and view insert operations as updates and inserts against the view's underlying base tables.</span></span> <span data-ttu-id="31543-201">通过选择 **“使用视图规则更新”** ，您可以确保 MDAC 针对视图本身生成更新和插入操作。</span><span class="sxs-lookup"><span data-stu-id="31543-201">By selecting **Update Using View Rules**, you can ensure that MDAC generates update and insert operations against the view itself.</span></span>  
  
     <span data-ttu-id="31543-202">**Check 选项**</span><span class="sxs-lookup"><span data-stu-id="31543-202">**Check Option**</span></span>  
     <span data-ttu-id="31543-203">指示当打开此视图并修改“结果”  窗格时，数据源检查添加或修改的数据是否满足视图定义的 **WHERE** 子句的要求。</span><span class="sxs-lookup"><span data-stu-id="31543-203">Indicates that when you open this view and modify the **Results** pane, the data source checks whether the added or modified data satisfies the **WHERE** clause of the view definition.</span></span> <span data-ttu-id="31543-204">如果您的修改不满足 **WHERE** 子句的要求，将看到一个包含详细信息的错误。</span><span class="sxs-lookup"><span data-stu-id="31543-204">If your modification do not satisfy the **WHERE** clause, you will see an error with more information.</span></span>  
  
#### <a name="to-get-dependencies-on-the-view"></a><span data-ttu-id="31543-205">获取视图的依赖关系</span><span class="sxs-lookup"><span data-stu-id="31543-205">To get dependencies on the view</span></span>  
  
1.  <span data-ttu-id="31543-206">在 **“对象资源管理器”** 中，展开包含要查看属性的视图的数据库，然后展开 **“视图”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="31543-206">In **Object Explorer**, expand the database that contains the view to which you want to view the properties, and then expand the **Views** folder.</span></span>  
  
2.  <span data-ttu-id="31543-207">右键单击要查看其属性的视图，然后选择“查看依赖关系”  。</span><span class="sxs-lookup"><span data-stu-id="31543-207">Right-click the view of which you want to view the properties and select **View Dependencies**.</span></span>  
  
3.  <span data-ttu-id="31543-208">选择“依赖于 [视图名称] 的对象”  可以显示引用该视图的对象。</span><span class="sxs-lookup"><span data-stu-id="31543-208">Select **Objects that depend on [view name]** to display the objects that refer to the view.</span></span>  
  
4.  <span data-ttu-id="31543-209">选择“[视图名称] 依赖的对象”  可以显示由该视图引用的对象。</span><span class="sxs-lookup"><span data-stu-id="31543-209">Select **Objects on which [view name] depends** to display the objects that are referenced by the view.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="31543-210">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="31543-210">Using Transact-SQL</span></span>  
  
#### <a name="to-get-the-definition-and-properties-of-a-view"></a><span data-ttu-id="31543-211">获取视图的定义和属性</span><span class="sxs-lookup"><span data-stu-id="31543-211">To get the definition and properties of a view</span></span>  
  
1.  <span data-ttu-id="31543-212">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="31543-212">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="31543-213">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="31543-213">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="31543-214">将以下示例之一复制并粘贴到查询窗口中，然后单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="31543-214">Copy and paste one of the following examples into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT definition, uses_ansi_nulls, uses_quoted_identifier, is_schema_bound  
    FROM sys.sql_modules  
    WHERE object_id = OBJECT_ID('HumanResources.vEmployee');   
    GO  
    ```  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    SELECT OBJECT_DEFINITION (OBJECT_ID('HumanResources.vEmployee')) AS ObjectDefinition;   
    GO  
    ```  
  
    ```  
    EXEC sp_helptext 'HumanResources.vEmployee';  
    ```  
  
 <span data-ttu-id="31543-215">有关详细信息，请参阅 [sys.sql_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)、[OBJECT_DEFINITION (Transact-SQL)](/sql/t-sql/functions/object-definition-transact-sql) 和 [sp_helptext (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="31543-215">For more information, see [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql), [OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql) and [sp_helptext &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql).</span></span>  
  
#### <a name="to-get-the-dependencies-of-a-view"></a><span data-ttu-id="31543-216">获取视图的依赖关系</span><span class="sxs-lookup"><span data-stu-id="31543-216">To get the dependencies of a view</span></span>  
  
1.  <span data-ttu-id="31543-217">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="31543-217">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="31543-218">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="31543-218">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="31543-219">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="31543-219">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referencing_id = OBJECT_ID(N'Production.vProductAndDescription');  
    GO  
    ```  
  
 <span data-ttu-id="31543-220">有关详细信息，请参阅 [sys.sql_expression_dependencies (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) 和 [sys.objects (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="31543-220">For more information, see [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) and [sys.objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql).</span></span>  
  
  
