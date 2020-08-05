---
title: 使用多维数据集写回 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- writeback [Analysis Services], cubes
- cubes [Analysis Services], modifying
- modifying cubes
- UPDATE CUBE statement
- cubes [Analysis Services], writeback
ms.assetid: ae2385fc-7fa0-4f8e-98d7-dcb0a5f0eeea
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3ac43e9206619117c1fc090a594ca32ccbeeeb31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580929"
---
# <a name="using-cube-writebacks-mdx"></a><span data-ttu-id="d704d-102">使用多维数据集写回 (MDX)</span><span class="sxs-lookup"><span data-stu-id="d704d-102">Using Cube Writebacks (MDX)</span></span>
  <span data-ttu-id="d704d-103">可以使用 [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) 语句更新多维数据集。</span><span class="sxs-lookup"><span data-stu-id="d704d-103">You update a cube by using the [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) statement.</span></span> <span data-ttu-id="d704d-104">通过此语句，您可以使用特定值更新元组。</span><span class="sxs-lookup"><span data-stu-id="d704d-104">This statement lets you update a tuple with a specific value.</span></span> <span data-ttu-id="d704d-105">若要有效地使用 UPDATE CUBE 语句更新多维数据集，必须了解该语句的语法、发生错误的条件以及更新可能对多维数据集产生的影响。</span><span class="sxs-lookup"><span data-stu-id="d704d-105">To effectively use the UPDATE CUBE statement to update a cube, you have to understand the syntax for the statement, the error conditions that can occur, and the affect that updates can have on a cube.</span></span>  
  
## <a name="update-cube-statement-syntax"></a><span data-ttu-id="d704d-106">UPDATE CUBE 语句的语法</span><span class="sxs-lookup"><span data-stu-id="d704d-106">UPDATE CUBE Statement Syntax</span></span>  
 <span data-ttu-id="d704d-107">下列语法描述了 UPDATE CUBE 语句：</span><span class="sxs-lookup"><span data-stu-id="d704d-107">The following syntax describes the UPDATE CUBE statement:</span></span>  
  
```  
UPDATE [CUBE] <Cube_Name> SET <tuple>.VALUE = <value> [,<tuple>.VALUE = <value>...]  
 [ USE_EQUAL_ALLOCATION | USE_EQUAL_INCREMENT |  
  USE_WEIGHTED_ALLOCATION [BY <weight value_expression>] |  
  USE_WEIGHTED_INCREMENT [BY <weight value_expression>] ]   
```  
  
 <span data-ttu-id="d704d-108">如果未为元组指定所有坐标，未指定的坐标将使用层次结构的默认成员。</span><span class="sxs-lookup"><span data-stu-id="d704d-108">If a full set of coordinates is not specified for the tuple, the unspecified coordinates will use the default member of the hierarchy.</span></span> <span data-ttu-id="d704d-109">所标识的元组必须引用使用 [Sum](/sql/mdx/sum-mdx) 函数聚合的单元，并且不能将计算成员作为该单元的一个坐标使用。</span><span class="sxs-lookup"><span data-stu-id="d704d-109">The tuple identified must reference a cell that is aggregated with the [Sum](/sql/mdx/sum-mdx) function, and must not use a calculated member as one of the cell's coordinates.</span></span>  
  
 <span data-ttu-id="d704d-110">可以将 UPDATE CUBE 语句视为一个子例程，该子例程生成原子单元的一系列单独的写回操作。</span><span class="sxs-lookup"><span data-stu-id="d704d-110">You can think of the UPDATE CUBE statement as a subroutine that generates a series of individual writeback operations to atomic cells.</span></span> <span data-ttu-id="d704d-111">然后，所有这些单独的写回操作汇总出一个指定的和。</span><span class="sxs-lookup"><span data-stu-id="d704d-111">All these individual writeback operations then roll up into the specified sum.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d704d-112">如果更新的单元不相互重叠，则 `Update Isolation Level` 连接字符串属性可用于提高 UPDATE CUBE 的性能。</span><span class="sxs-lookup"><span data-stu-id="d704d-112">When updated cells do not overlap, the `Update Isolation Level` connection string property can be used to enhance performance for UPDATE CUBE.</span></span> <span data-ttu-id="d704d-113">有关详细信息，请参阅 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="d704d-113">For more information, see <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d704d-114">示例</span><span class="sxs-lookup"><span data-stu-id="d704d-114">Example</span></span>  
 <span data-ttu-id="d704d-115">您可以使用 Adventure Works 多维数据集中的 Sales Targets 度量值组来测试 UPDATE CUBE。</span><span class="sxs-lookup"><span data-stu-id="d704d-115">You can test UPDATE CUBE using the Sales Targets measure group in the Adventure Works cube.</span></span> <span data-ttu-id="d704d-116">此度量值组包含由 SUM 聚合的度量值，这是 UPDATE CUBE 的一个要求。</span><span class="sxs-lookup"><span data-stu-id="d704d-116">This measure group consists of measures aggregated by SUM, which is a requirement for UPDATE CUBE.</span></span>  
  
1.  <span data-ttu-id="d704d-117">为 Adventure Works 数据库的 Sales Targets 度量值组启用写回。</span><span class="sxs-lookup"><span data-stu-id="d704d-117">Enable writeback for the Sales Targets measure group in the Adventure Works database.</span></span> <span data-ttu-id="d704d-118">在 Management Studio 中，右键单击度量值组，指向“写回选项”，然后选择“启用写回”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d704d-118">In Management Studio, right-click a measure group, point to **Write Back Options**, choose **Enable Writeback**.</span></span>  
  
     <span data-ttu-id="d704d-119">您应在 Writeback 文件夹中看到一个新的写回表。</span><span class="sxs-lookup"><span data-stu-id="d704d-119">You should see a new writeback table in the Writeback folder.</span></span> <span data-ttu-id="d704d-120">该表的名称为 WriteTable_Fact Sales Quota。</span><span class="sxs-lookup"><span data-stu-id="d704d-120">The table name is WriteTable_Fact Sales Quota.</span></span>  
  
2.  <span data-ttu-id="d704d-121">打开 MDX 查询窗口。</span><span class="sxs-lookup"><span data-stu-id="d704d-121">Open an MDX query window.</span></span> <span data-ttu-id="d704d-122">运行以下 select 语句以查看原始值：</span><span class="sxs-lookup"><span data-stu-id="d704d-122">Run the following select statement to view the original value:</span></span>  
  
    ```  
    SELECT [Measures].[Sales Amount Quota] on 0 ,  
    [Employee].[Employee Department].[Title].&[Sales Representative].children on 1  
    FROM [Adventure Works]  
  
    ```  
  
     <span data-ttu-id="d704d-123">您应看到每个代表的销售配额。</span><span class="sxs-lookup"><span data-stu-id="d704d-123">You should see sales amount quotas for each representative.</span></span>  
  
3.  <span data-ttu-id="d704d-124">运行 update cube 语句以写回新值。</span><span class="sxs-lookup"><span data-stu-id="d704d-124">Run the update cube statement to write back a new value.</span></span> <span data-ttu-id="d704d-125">在此示例中，我们将销售配额设置为 0。</span><span class="sxs-lookup"><span data-stu-id="d704d-125">In this example, we are setting the sales amount quota to 0.</span></span> <span data-ttu-id="d704d-126">由于新值为 0，请不要指定分配方法。</span><span class="sxs-lookup"><span data-stu-id="d704d-126">Because the new value is 0, do not specify an allocation method.</span></span>  
  
    ```  
    UPDATE CUBE [Adventure Works]   
    SET ([Measures].[Sales Amount Quota], [Employee].[Employee Department].[Department].&[Sales]) = 0  
  
    ```  
  
4.  <span data-ttu-id="d704d-127">重新运行 SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="d704d-127">Re-run the SELECT statement.</span></span> <span data-ttu-id="d704d-128">您现在应看到配额为零。</span><span class="sxs-lookup"><span data-stu-id="d704d-128">You should now see zero for the quotas.</span></span>  
  
 <span data-ttu-id="d704d-129">写回值约束为仅用于当前会话。</span><span class="sxs-lookup"><span data-stu-id="d704d-129">The writeback value is constrained to the current session.</span></span> <span data-ttu-id="d704d-130">若要在各用户和会话之间保留该值，请处理写回表。</span><span class="sxs-lookup"><span data-stu-id="d704d-130">To persist the value across users and sessions, process the writeback table.</span></span> <span data-ttu-id="d704d-131">在 Management Studio 中，右键单击“WriteTable_Fact Sales Quota”，然后选择“处理”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d704d-131">In Management Studio, right-click WriteTable_Fact Sales Quota and choose **Process**.</span></span>  
  
 <span data-ttu-id="d704d-132">若要指定分配方法，新值必须大于零。</span><span class="sxs-lookup"><span data-stu-id="d704d-132">To specify an allocation method, the new value must be greater than zero.</span></span> <span data-ttu-id="d704d-133">在此示例中，“Sales Amount Quota”的新值为两百万，该分配方法将该金额在所有销售代表之间进行分配。</span><span class="sxs-lookup"><span data-stu-id="d704d-133">In this example, the new value for Sales Amount Quota is two million and the allocation method distributes the amount across all sales representatives.</span></span>  
  
```  
UPDATE CUBE [Adventure Works]   
SET ([Measures].[Sales Amount Quota], [Employee].[Employee Department].[Department].&[Sales]) = 2000000   
USE_EQUAL_ALLOCATION  
```  
  
## <a name="error-conditions"></a><span data-ttu-id="d704d-134">错误条件</span><span class="sxs-lookup"><span data-stu-id="d704d-134">Error Conditions</span></span>  
 <span data-ttu-id="d704d-135">下表介绍了可能导致写回失败的原因以及这些错误的结果。</span><span class="sxs-lookup"><span data-stu-id="d704d-135">The following table describes both what can cause writebacks to fail and the result of those errors.</span></span>  
  
|<span data-ttu-id="d704d-136">错误条件</span><span class="sxs-lookup"><span data-stu-id="d704d-136">Error Condition</span></span>|<span data-ttu-id="d704d-137">结果</span><span class="sxs-lookup"><span data-stu-id="d704d-137">Result</span></span>|  
|---------------------|------------|  
|<span data-ttu-id="d704d-138">更新包括同一维度中不能共存的成员。</span><span class="sxs-lookup"><span data-stu-id="d704d-138">Update includes members from the same dimension that do not exist with one another.</span></span>|<span data-ttu-id="d704d-139">更新将失败。</span><span class="sxs-lookup"><span data-stu-id="d704d-139">Update will fail.</span></span> <span data-ttu-id="d704d-140">多维数据集空间将不包含被引用单元。</span><span class="sxs-lookup"><span data-stu-id="d704d-140">The cube space will not contain the referenced cell.</span></span>|  
|<span data-ttu-id="d704d-141">更新包括作为无符号类型的度量值的来源的度量值。</span><span class="sxs-lookup"><span data-stu-id="d704d-141">Update includes a measure sourced to a measure of an unsigned type.</span></span>|<span data-ttu-id="d704d-142">更新将失败。</span><span class="sxs-lookup"><span data-stu-id="d704d-142">Update will fail.</span></span> <span data-ttu-id="d704d-143">增量需要度量值能够取负值。</span><span class="sxs-lookup"><span data-stu-id="d704d-143">Increments require that the measure be able to take a negative value.</span></span>|  
|<span data-ttu-id="d704d-144">更新包括执行非求和聚合的度量值。</span><span class="sxs-lookup"><span data-stu-id="d704d-144">Update includes a measure that aggregates other than sum.</span></span>|<span data-ttu-id="d704d-145">已引发错误。</span><span class="sxs-lookup"><span data-stu-id="d704d-145">An error is raised.</span></span>|  
|<span data-ttu-id="d704d-146">尝试更新子多维数据集。</span><span class="sxs-lookup"><span data-stu-id="d704d-146">Update was tried on a subcube.</span></span>|<span data-ttu-id="d704d-147">已引发错误。</span><span class="sxs-lookup"><span data-stu-id="d704d-147">An error is raised.</span></span>|  
  
## <a name="affect-of-cube-changes"></a><span data-ttu-id="d704d-148">多维数据集更改的影响</span><span class="sxs-lookup"><span data-stu-id="d704d-148">Affect of Cube Changes</span></span>  
 <span data-ttu-id="d704d-149">下列更改将不会对写回产生影响：</span><span class="sxs-lookup"><span data-stu-id="d704d-149">The following changes will not have an effect on a writeback:</span></span>  
  
-   <span data-ttu-id="d704d-150">处理多维数据集、多维数据集的度量值组或多维数据集的维度。</span><span class="sxs-lookup"><span data-stu-id="d704d-150">Processing of a cube, the cube's measure groups, or the cube's dimensions.</span></span>  
  
-   <span data-ttu-id="d704d-151">向任何维度中添加属性。</span><span class="sxs-lookup"><span data-stu-id="d704d-151">Adding attributes to any dimension.</span></span>  
  
-   <span data-ttu-id="d704d-152">添加新维度。</span><span class="sxs-lookup"><span data-stu-id="d704d-152">Adding a new dimension.</span></span>  
  
-   <span data-ttu-id="d704d-153">删除不包含写回的维度。</span><span class="sxs-lookup"><span data-stu-id="d704d-153">Deleting a dimension that does not include the writeback.</span></span>  
  
-   <span data-ttu-id="d704d-154">添加、修改或删除层次结构。</span><span class="sxs-lookup"><span data-stu-id="d704d-154">Adding, modifying, or removing a hierarchy.</span></span>  
  
-   <span data-ttu-id="d704d-155">添加新度量值。</span><span class="sxs-lookup"><span data-stu-id="d704d-155">Adding a new measure.</span></span>  
  
 <span data-ttu-id="d704d-156">只有删除写回数据才能进行下列更改：</span><span class="sxs-lookup"><span data-stu-id="d704d-156">The following changes cannot be made without removing the writeback data:</span></span>  
  
-   <span data-ttu-id="d704d-157">删除属性或其属性层次结构（如果该属性包含在写回中）。</span><span class="sxs-lookup"><span data-stu-id="d704d-157">Deleting an attribute, or its attribute hierarchy, if the attribute is included in the writeback.</span></span> <span data-ttu-id="d704d-158">这包括显式删除属性或其属性层次结构，或者删除属性的父维度。</span><span class="sxs-lookup"><span data-stu-id="d704d-158">This includes explicitly removing the attribute, or its attribute hierarchy, or removing the attribute's parent dimension.</span></span>  
  
-   <span data-ttu-id="d704d-159">删除写回中包含的度量值。</span><span class="sxs-lookup"><span data-stu-id="d704d-159">Deleting a measure included in the writeback.</span></span>  
  
-   <span data-ttu-id="d704d-160">向写回中包含的维度添加不带 `(All)` 级别的属性。</span><span class="sxs-lookup"><span data-stu-id="d704d-160">Adding an attribute without an `(All)` level to a dimension included in the writeback.</span></span>  
  
-   <span data-ttu-id="d704d-161">更改写回中包含的维度的维度粒度。</span><span class="sxs-lookup"><span data-stu-id="d704d-161">Changing the dimension granularity for a dimension included in the writeback.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d704d-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d704d-162">See Also</span></span>  
 [<span data-ttu-id="d704d-163">修改数据 (MDX)</span><span class="sxs-lookup"><span data-stu-id="d704d-163">Modifying Data &#40;MDX&#41;</span></span>](mdx-data-modification-modifying-data.md)  
  
  
