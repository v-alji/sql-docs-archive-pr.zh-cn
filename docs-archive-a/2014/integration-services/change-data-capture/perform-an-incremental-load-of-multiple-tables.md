---
title: 执行多个表的增量加载 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],multiple tables
ms.assetid: 39252dd5-09c3-46f9-a17b-15208cfd336d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e4bf81d1d529e8102271c66839440ef712219600
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579009"
---
# <a name="perform-an-incremental-load-of-multiple-tables"></a><span data-ttu-id="b1013-102">执行多个表的增量加载</span><span class="sxs-lookup"><span data-stu-id="b1013-102">Perform an Incremental Load of Multiple Tables</span></span>
  <span data-ttu-id="b1013-103">在主题 [通过变更数据捕获改善增量加载](change-data-capture-ssis.md)中，关系图演示的是仅对一个表执行增量加载的基本包。</span><span class="sxs-lookup"><span data-stu-id="b1013-103">In the topic, [Improving Incremental Loads with Change Data Capture](change-data-capture-ssis.md), the diagram illustrates a basic package that performs an incremental load on just one table.</span></span> <span data-ttu-id="b1013-104">但是，加载一个表并不像执行多个表的增量加载那样常见。</span><span class="sxs-lookup"><span data-stu-id="b1013-104">However, loading one table is not as common as having to perform an incremental load of multiple tables.</span></span>  
  
 <span data-ttu-id="b1013-105">在执行多个表的增量加载时，有些步骤必须对所有表执行一次，而有些步骤则必须针对每个源表重复执行。</span><span class="sxs-lookup"><span data-stu-id="b1013-105">When you perform an incremental load of multiple tables, some steps have to be performed once for all the tables, and other steps have to be repeated for each source table.</span></span> <span data-ttu-id="b1013-106">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]中提供了多个用于实现这些步骤的选项：</span><span class="sxs-lookup"><span data-stu-id="b1013-106">You have more than one option for implementing these steps in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="b1013-107">使用父包和子包。</span><span class="sxs-lookup"><span data-stu-id="b1013-107">Use a parent package and child packages.</span></span>  
  
-   <span data-ttu-id="b1013-108">在一个包中使用多个数据流任务。</span><span class="sxs-lookup"><span data-stu-id="b1013-108">Use multiple Data Flow tasks in a single package.</span></span>  
  
## <a name="loading-multiple-tables-by-using-a-parent-package-and-multiple-child-packages"></a><span data-ttu-id="b1013-109">使用一个父包和多个子包来加载多个表</span><span class="sxs-lookup"><span data-stu-id="b1013-109">Loading Multiple Tables by Using a Parent Package and Multiple Child Packages</span></span>  
 <span data-ttu-id="b1013-110">可以使用父包来执行只需执行一次的步骤。</span><span class="sxs-lookup"><span data-stu-id="b1013-110">You can use a parent package to perform those steps that only have to be done once.</span></span> <span data-ttu-id="b1013-111">子包将执行针对各源表的步骤。</span><span class="sxs-lookup"><span data-stu-id="b1013-111">The child packages will perform those steps that have to be done for each source table.</span></span>  
  
#### <a name="to-create-a-parent-package-that-performs-those-steps-that-only-have-to-be-done-once"></a><span data-ttu-id="b1013-112">创建父包以执行只需执行一次的步骤</span><span class="sxs-lookup"><span data-stu-id="b1013-112">To create a parent package that performs those steps that only have to be done once</span></span>  
  
1.  <span data-ttu-id="b1013-113">创建父包。</span><span class="sxs-lookup"><span data-stu-id="b1013-113">Create a parent package.</span></span>  
  
2.  <span data-ttu-id="b1013-114">在控制流中，使用执行 SQL 任务或 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 表达式来计算端点。</span><span class="sxs-lookup"><span data-stu-id="b1013-114">In the control flow, use an Execute SQL task or [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expressions to calculate the endpoints.</span></span>  
  
     <span data-ttu-id="b1013-115">有关如何计算端点的示例，请参阅 [指定变更数据的间隔](specify-an-interval-of-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b1013-115">For an example of how to calculate endpoints, see [Specify an Interval of Change Data](specify-an-interval-of-change-data.md).</span></span>  
  
3.  <span data-ttu-id="b1013-116">如果需要，可使用 For 循环容器来延迟执行，直到所选周期的变更数据准备就绪。</span><span class="sxs-lookup"><span data-stu-id="b1013-116">If needed, use a For Loop container to delay execution until change data for the selected period is ready.</span></span>  
  
     <span data-ttu-id="b1013-117">有关 For 循环容器的示例，请参阅 [确定变更数据是否已准备就绪](determine-whether-the-change-data-is-ready.md)。</span><span class="sxs-lookup"><span data-stu-id="b1013-117">For an example of such a For Loop container, see [Determine Whether the Change Data Is Ready](determine-whether-the-change-data-is-ready.md).</span></span>  
  
4.  <span data-ttu-id="b1013-118">使用多个执行包任务针对每个要加载的表执行子包。</span><span class="sxs-lookup"><span data-stu-id="b1013-118">Use multiple Execute Package tasks to execute child packages for each table to be loaded.</span></span> <span data-ttu-id="b1013-119">使用父包变量配置将父包中计算的端点传递到各个子包。</span><span class="sxs-lookup"><span data-stu-id="b1013-119">Pass the endpoints calculated in the parent package to each child package by using Parent Package Variable configurations.</span></span>  
  
     <span data-ttu-id="b1013-120">有关详细信息，请参阅 [执行包任务](../control-flow/execute-package-task.md) 和 [在子包中使用变量和参数的值](../use-the-values-of-variables-and-parameters-in-a-child-package.md)。</span><span class="sxs-lookup"><span data-stu-id="b1013-120">For more information, see [Execute Package Task](../control-flow/execute-package-task.md) and [Use the Values of Variables and Parameters in a Child Package](../use-the-values-of-variables-and-parameters-in-a-child-package.md).</span></span>  
  
#### <a name="to-create-child-packages-to-perform-those-steps-that-have-to-be-done-for-each-source-table"></a><span data-ttu-id="b1013-121">创建子包以执行针对各源表的步骤</span><span class="sxs-lookup"><span data-stu-id="b1013-121">To create child packages to perform those steps that have to be done for each source table</span></span>  
  
1.  <span data-ttu-id="b1013-122">应为每个源表各创建一个子包。</span><span class="sxs-lookup"><span data-stu-id="b1013-122">For each source table, create a child package.</span></span>  
  
2.  <span data-ttu-id="b1013-123">在控制流中，使用脚本任务或执行 SQL 任务汇集将用于查询变更的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="b1013-123">In the control flow, use a Script task or an Execute SQL task to assemble the SQL statement that will be used to query for changes.</span></span>  
  
     <span data-ttu-id="b1013-124">有关如何汇集查询的示例，请参阅 [准备查询变更数据](prepare-to-query-for-the-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b1013-124">For an example of how to assemble the query, see [Prepare to Query for the Change Data](prepare-to-query-for-the-change-data.md).</span></span>  
  
3.  <span data-ttu-id="b1013-125">在每个子包中使用一个的数据流任务加载变更数据，并将变更数据应用到目标。</span><span class="sxs-lookup"><span data-stu-id="b1013-125">Use a single Data Flow task in each child package to load the change data and apply it to the destination.</span></span> <span data-ttu-id="b1013-126">按照下面的步骤说明配置数据流：</span><span class="sxs-lookup"><span data-stu-id="b1013-126">Configure the Data Flow as described in the following steps:</span></span>  
  
    1.  <span data-ttu-id="b1013-127">在数据流中，使用源组件来查询变更表中在所选端点内发生的变更。</span><span class="sxs-lookup"><span data-stu-id="b1013-127">In the data flow, use a source component to query the change tables for the changes that fall within the selected endpoints.</span></span>  
  
         <span data-ttu-id="b1013-128">有关如何查询变更表的示例，请参阅 [检索和了解变更数据](retrieve-and-understand-the-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b1013-128">For an example of how to query the change tables, see [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md).</span></span>  
  
    2.  <span data-ttu-id="b1013-129">使用有条件拆分转换将插入、更新和删除操作定向到不同的输出，以便于进行适当的处理。</span><span class="sxs-lookup"><span data-stu-id="b1013-129">Use a Conditional Split transformation to direct inserts, updates, and deletes to different outputs for appropriate processing.</span></span>  
  
         <span data-ttu-id="b1013-130">有关如何配置此转换以定向输出的示例，请参阅 [处理插入、更新和删除](process-inserts-updates-and-deletes.md)。</span><span class="sxs-lookup"><span data-stu-id="b1013-130">For an example of how to configure this transformation to direct output, see [Process Inserts, Updates, and Deletes](process-inserts-updates-and-deletes.md).</span></span>  
  
    3.  <span data-ttu-id="b1013-131">使用目标组件将插入操作应用到目标。</span><span class="sxs-lookup"><span data-stu-id="b1013-131">Use a destination component to apply the inserts to the destination.</span></span> <span data-ttu-id="b1013-132">使用具有参数化的 UPDATE 和 DELETE 语句的 OLE DB 命令转换，将更新和删除操作应用到目标。</span><span class="sxs-lookup"><span data-stu-id="b1013-132">Use OLE DB Command transformations with parameterized UPDATE and DELETE statements to apply updates and deletes to the destination.</span></span>  
  
         <span data-ttu-id="b1013-133">有关如何使用此转换来应用更新和删除操作的示例，请参阅 [将变更应用到目标](apply-the-changes-to-the-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="b1013-133">For an example of how to use this transformation to apply updates and deletes, see [Apply the Changes to the Destination](apply-the-changes-to-the-destination.md).</span></span>  
  
## <a name="loading-multiple-tables-by-using-multiple-data-flow-tasks-in-a-single-package"></a><span data-ttu-id="b1013-134">在单个包中使用多个数据流任务加载多个表</span><span class="sxs-lookup"><span data-stu-id="b1013-134">Loading Multiple Tables by Using Multiple Data Flow Tasks in a Single Package</span></span>  
 <span data-ttu-id="b1013-135">或者，您也可以使用针对每个要加载的源表都包含一个独立数据流任务的单个包。</span><span class="sxs-lookup"><span data-stu-id="b1013-135">Alternatively, you can use a single package that contains a separate Data Flow task for each source table to be loaded.</span></span>  
  
#### <a name="to-load-multiple-tables-by-using-multiple-data-flow-tasks-in-a-single-package"></a><span data-ttu-id="b1013-136">在单个包中使用多个数据流任务加载多个表</span><span class="sxs-lookup"><span data-stu-id="b1013-136">To load multiple tables by using multiple Data Flow tasks in a single package</span></span>  
  
1.  <span data-ttu-id="b1013-137">创建一个包。</span><span class="sxs-lookup"><span data-stu-id="b1013-137">Create a single package.</span></span>  
  
2.  <span data-ttu-id="b1013-138">在控制流中，使用执行 SQL 任务或 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 表达式来计算端点。</span><span class="sxs-lookup"><span data-stu-id="b1013-138">In the control flow, use an Execute SQL Task or [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expressions to calculate the endpoints.</span></span>  
  
     <span data-ttu-id="b1013-139">有关如何计算端点的示例，请参阅 [指定变更数据的间隔](specify-an-interval-of-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b1013-139">For an example of how to calculate endpoints, see [Specify an Interval of Change Data](specify-an-interval-of-change-data.md).</span></span>  
  
3.  <span data-ttu-id="b1013-140">如果需要，可使用 For 循环容器延迟执行过程，直到所选间隔的变更数据准备就绪。</span><span class="sxs-lookup"><span data-stu-id="b1013-140">If needed, use a For Loop container to delay execution until the change data for the selected interval is ready.</span></span>  
  
     <span data-ttu-id="b1013-141">有关 For 循环容器的示例，请参阅 [确定变更数据是否已准备就绪](determine-whether-the-change-data-is-ready.md)。</span><span class="sxs-lookup"><span data-stu-id="b1013-141">For an example of such a For Loop container, see [Determine Whether the Change Data Is Ready](determine-whether-the-change-data-is-ready.md).</span></span>  
  
4.  <span data-ttu-id="b1013-142">使用脚本任务或执行 SQL 任务汇集将用于查询变更的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="b1013-142">Use a Script task or an Execute SQL task to assemble the SQL statement that will be used to query for changes.</span></span>  
  
     <span data-ttu-id="b1013-143">有关如何汇集查询的示例，请参阅 [准备查询变更数据](prepare-to-query-for-the-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b1013-143">For an example of how to assemble the query, see [Prepare to Query for the Change Data](prepare-to-query-for-the-change-data.md).</span></span>  
  
5.  <span data-ttu-id="b1013-144">使用多个数据流任务加载各源表中的变更数据，并将变更数据应用到目标。</span><span class="sxs-lookup"><span data-stu-id="b1013-144">Use multiple Data Flow tasks to load the change data from each source table and apply it to the destination.</span></span> <span data-ttu-id="b1013-145">按照下面的步骤说明配置各个数据流。</span><span class="sxs-lookup"><span data-stu-id="b1013-145">Configure each Data Flow task as described in the following steps.</span></span>  
  
    1.  <span data-ttu-id="b1013-146">在各个数据流中，使用源组件来查询变更表中在所选端点内发生的变更。</span><span class="sxs-lookup"><span data-stu-id="b1013-146">In each data flow, use a source component to query the change tables for the changes that fall within the selected endpoints.</span></span>  
  
         <span data-ttu-id="b1013-147">有关如何查询变更表的示例，请参阅 [检索和了解变更数据](retrieve-and-understand-the-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b1013-147">For an example of how to query the change tables, see [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md).</span></span>  
  
    2.  <span data-ttu-id="b1013-148">使用有条件拆分转换将插入、更新和删除操作定向到不同的输出，以便于进行适当的处理。</span><span class="sxs-lookup"><span data-stu-id="b1013-148">Use a Conditional Split transformation to direct inserts, updates, and deletes to different outputs for appropriate processing.</span></span>  
  
         <span data-ttu-id="b1013-149">有关如何配置此转换以定向输出的示例，请参阅 [处理插入、更新和删除](process-inserts-updates-and-deletes.md)。</span><span class="sxs-lookup"><span data-stu-id="b1013-149">For an example of how to configure this transformation to direct output, see [Process Inserts, Updates, and Deletes](process-inserts-updates-and-deletes.md).</span></span>  
  
    3.  <span data-ttu-id="b1013-150">使用目标组件将插入操作应用到目标。</span><span class="sxs-lookup"><span data-stu-id="b1013-150">Use a destination component to apply the inserts to the destination.</span></span> <span data-ttu-id="b1013-151">使用具有参数化的 UPDATE 和 DELETE 语句的 OLE DB 命令转换，将更新和删除操作应用到目标。</span><span class="sxs-lookup"><span data-stu-id="b1013-151">Use OLE DB Command transformations with parameterized UPDATE and DELETE statements to apply updates and deletes to the destination.</span></span>  
  
         <span data-ttu-id="b1013-152">有关如何使用此转换来应用更新和删除操作的示例，请参阅 [将变更应用到目标](apply-the-changes-to-the-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="b1013-152">For an example of how to use this transformation to apply updates and deletes, see [Apply the Changes to the Destination](apply-the-changes-to-the-destination.md).</span></span>  
  
  
