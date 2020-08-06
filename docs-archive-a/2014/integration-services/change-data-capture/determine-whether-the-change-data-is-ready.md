---
title: 确定变更数据是否已准备就绪 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],determining readiness
ms.assetid: 04935f35-96cc-4d70-a250-0fd326f8daff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5e672440938e366e53ba150f65d7bcd6aed8a58c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693017"
---
# <a name="determine-whether-the-change-data-is-ready"></a><span data-ttu-id="3e3e7-102">确定变更数据是否已准备就绪</span><span class="sxs-lookup"><span data-stu-id="3e3e7-102">Determine Whether the Change Data Is Ready</span></span>
  <span data-ttu-id="3e3e7-103">在用于执行变更数据的增量加载的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的控制流中，第二个任务是确保所选间隔的变更数据已准备就绪。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-103">In the control flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the second task is to ensure that the change data for the selected interval is ready.</span></span> <span data-ttu-id="3e3e7-104">此步骤是必需的，因为异步捕获进程可能尚未处理完到达所选端点的所有更改。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-104">This step is necessary because the asynchronous capture process might not yet have processed all the changes up to the selected endpoint.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3e3e7-105">控制流的第一个任务是计算更改间隔的端点。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-105">The first task for the control flow is to calculate the endpoints of the change interval.</span></span> <span data-ttu-id="3e3e7-106">有关此任务的详细信息，请参阅 [指定变更数据的间隔](specify-an-interval-of-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-106">For more information about this task, see [Specify an Interval of Change Data](specify-an-interval-of-change-data.md).</span></span> <span data-ttu-id="3e3e7-107">有关设计控制流的总体过程的说明，请参阅[变更数据捕获 (SSIS)](change-data-capture-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-107">For a description of the overall process of designing the control flow, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="understanding-the-components-of-the-solution"></a><span data-ttu-id="3e3e7-108">了解解决方案的组件</span><span class="sxs-lookup"><span data-stu-id="3e3e7-108">Understanding the Components of the Solution</span></span>  
 <span data-ttu-id="3e3e7-109">本主题中介绍的解决方案使用以下 4 个 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 组件：</span><span class="sxs-lookup"><span data-stu-id="3e3e7-109">The solution described in this topic uses 4 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components:</span></span>  
  
-   <span data-ttu-id="3e3e7-110">一个 For 循环容器，用于重复地计算执行 SQL 任务的输出。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-110">A For Loop container that repeatedly evaluates the output of an Execute SQL Task.</span></span>  
  
-   <span data-ttu-id="3e3e7-111">一个执行 SQL 任务，用于查询变更数据捕获进程维护的特殊表并使用该信息来确定数据是否已准备就绪。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-111">An Execute SQL task that queries special tables that the change data capture process maintains and then uses this information to determine whether data is ready.</span></span>  
  
-   <span data-ttu-id="3e3e7-112">一个用于在数据未准备就绪时实现处理延迟的组件。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-112">A component that implements a delay in processing when the data is not ready.</span></span> <span data-ttu-id="3e3e7-113">这可以是脚本任务，也可以是执行 SQL 任务。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-113">This can be either a Script task or an Execute SQL task.</span></span>  
  
-   <span data-ttu-id="3e3e7-114">一个可选的组件，用于在执行 SQL 任务返回的值指示错误或超时情况时报告错误或超时。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-114">Optionally, a component that reports an error or a timeout when the Execute SQL task returns a value that indicates an error or a timeout condition.</span></span>  
  
 <span data-ttu-id="3e3e7-115">这些组件设置或读取几个包变量的值，以控制循环内以及之后包中的执行流程。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-115">These components set or read the values of several package variables to control the flow of execution inside the loop and later in the package.</span></span>  
  
#### <a name="to-set-up-package-variables"></a><span data-ttu-id="3e3e7-116">设置包变量</span><span class="sxs-lookup"><span data-stu-id="3e3e7-116">To set up package variables</span></span>  
  
1.  <span data-ttu-id="3e3e7-117">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，在 **“变量”** 窗口中创建以下变量：</span><span class="sxs-lookup"><span data-stu-id="3e3e7-117">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in the **Variables** window, create the following variables:</span></span>  
  
    1.  <span data-ttu-id="3e3e7-118">创建一个数据类型为 integer 的变量，以保存执行 SQL 任务返回的状态值。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-118">Create a variable with an integer data type to hold the status value returned by the Execute SQL task.</span></span>  
  
         <span data-ttu-id="3e3e7-119">此示例使用变量名 DataReady，其初始值为 0。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-119">This example uses the variable name, DataReady, with an initial value of 0.</span></span>  
  
    2.  <span data-ttu-id="3e3e7-120">创建一个变量以保存数据未准备就绪时的延迟时间。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-120">Create a variable to hold the period of time to delay when data is not ready.</span></span> <span data-ttu-id="3e3e7-121">如果您计划使用脚本任务来实现延迟，则该变量的数据类型应为 integer。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-121">If you plan to use a Script task to implement the delay, the variable should have an integer data type integer.</span></span> <span data-ttu-id="3e3e7-122">如果您计划使用含有 WAITFOR 语句的执行 SQL 任务，则该变量的数据类型应为 string 以便能够接受诸如 00:00:10 之类的值。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-122">If you plan to use an Execute SQL task with a WAITFOR statement, the variable should have a string data type to accept values such as "00:00:10".</span></span>  
  
         <span data-ttu-id="3e3e7-123">此示例使用变量名 DelaySeconds，其初始值为 10。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-123">This example uses the variable name, DelaySeconds, with an initial value of 10.</span></span>  
  
    3.  <span data-ttu-id="3e3e7-124">创建一个数据类型为 integer 的变量，以保存循环的当前迭代。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-124">Create a variable with an integer data type to hold the current iteration of the loop.</span></span>  
  
         <span data-ttu-id="3e3e7-125">此示例使用变量名 TimeoutCount，其初始值为 0。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-125">This example uses the variable name, TimeoutCount, with an initial value of 0.</span></span>  
  
    4.  <span data-ttu-id="3e3e7-126">创建一个数据类型为 integer 的变量，以指定循环在报告超时情况之前应对数据执行的测试次数。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-126">Create a variable with an integer data type to specify the number of times that the loop should test for data before reporting a timeout condition.</span></span>  
  
         <span data-ttu-id="3e3e7-127">此示例使用变量名 TimeoutCeiling，其初始值为 20。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-127">This example uses the variable name, TimeoutCeiling, with an initial value of 20.</span></span>  
  
    5.  <span data-ttu-id="3e3e7-128">（可选）创建一个数据类型为 integer 的变量以指示变更数据的首次加载。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-128">(Optional) Create a variable with an integer data type that you can use to indicate the first load of change data.</span></span>  
  
         <span data-ttu-id="3e3e7-129">此示例使用变量名 IntervalID，并且仅检查 0 值以指示首次加载。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-129">This example uses the variable name, IntervalID, and checks only for a value of 0 to indicate the initial load.</span></span>  
  
## <a name="configuring-a-for-loop-container"></a><span data-ttu-id="3e3e7-130">配置 For 循环容器</span><span class="sxs-lookup"><span data-stu-id="3e3e7-130">Configuring a For Loop Container</span></span>  
 <span data-ttu-id="3e3e7-131">根据上述变量集，For 循环容器是首先要添加的组件。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-131">With the variables set, the For Loop container is the first component to be added.</span></span>  
  
#### <a name="to-configure-a-for-loop-container-to-wait-until-change-data-is-ready"></a><span data-ttu-id="3e3e7-132">将 For 循环容器配置为等待变更数据准备就绪</span><span class="sxs-lookup"><span data-stu-id="3e3e7-132">To configure a For Loop container to wait until change data is ready</span></span>  
  
1.  <span data-ttu-id="3e3e7-133">在 **设计器的** “控制流” [!INCLUDE[ssIS](../../includes/ssis-md.md)] 选项卡上，向控制流中添加 For 循环容器。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-133">On the **Control Flow** tab of the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add a For Loop container to the control flow.</span></span>  
  
2.  <span data-ttu-id="3e3e7-134">将用于计算间隔端点的执行 SQL 任务连接到 For 循环容器。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-134">Connect the Execute SQL Task that calculates the endpoints of the interval to the For Loop container.</span></span>  
  
3.  <span data-ttu-id="3e3e7-135">在 **“For 循环编辑器”** 中，选择以下选项：</span><span class="sxs-lookup"><span data-stu-id="3e3e7-135">In the **For Loop Editor**, select the following options:</span></span>  
  
    1.  <span data-ttu-id="3e3e7-136">对于 **InitExpression**，输入 `@DataReady = 0`。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-136">For **InitExpression**, enter `@DataReady = 0`.</span></span>  
  
         <span data-ttu-id="3e3e7-137">此表达式设置循环变量的初始值。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-137">This expression sets the initial value of the loop variable.</span></span>  
  
    2.  <span data-ttu-id="3e3e7-138">对于 **EvalExpression**，输入 `@DataReady == 0`。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-138">For **EvalExpression**m, enter `@DataReady == 0`.</span></span>  
  
         <span data-ttu-id="3e3e7-139">如果此表达式的计算结果为 **False**，则执行将跳出循环，开始进行增量加载。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-139">When this expression evaluates to **False**, execution passes out of the loop and the incremental load starts.</span></span>  
  
## <a name="configuring-the-execute-sql-task-that-queries-for-change-data"></a><span data-ttu-id="3e3e7-140">配置用于查询变更数据的执行 SQL 任务</span><span class="sxs-lookup"><span data-stu-id="3e3e7-140">Configuring the Execute SQL Task That Queries for Change Data</span></span>  
 <span data-ttu-id="3e3e7-141">在 For 循环容器内，添加一个执行 SQL 任务。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-141">Inside the For Loop container, you add an Execute SQL task.</span></span> <span data-ttu-id="3e3e7-142">此任务在数据库中查询变更数据捕获进程维护的表。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-142">This task queries the tables that the change data capture process maintains in the database.</span></span> <span data-ttu-id="3e3e7-143">此查询的结果是一个指示变更数据是否已准备就绪的状态值。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-143">The result of this query is a status value that indicates whether the change data is ready.</span></span>  
  
 <span data-ttu-id="3e3e7-144">在下表中，第一列显示 Transact-SQL 示例查询中从执行 SQL 任务返回的值。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-144">In the following table, the first column shows the values returned from the Execute SQL task by the sample Transact-SQL query.</span></span> <span data-ttu-id="3e3e7-145">第二列显示其他组件如何响应这些值。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-145">The second column shows how the other components respond to these values.</span></span>  
  
|<span data-ttu-id="3e3e7-146">返回值</span><span class="sxs-lookup"><span data-stu-id="3e3e7-146">Return Value</span></span>|<span data-ttu-id="3e3e7-147">含义</span><span class="sxs-lookup"><span data-stu-id="3e3e7-147">Meaning</span></span>|<span data-ttu-id="3e3e7-148">响应</span><span class="sxs-lookup"><span data-stu-id="3e3e7-148">Response</span></span>|  
|------------------|-------------|--------------|  
|<span data-ttu-id="3e3e7-149">0</span><span class="sxs-lookup"><span data-stu-id="3e3e7-149">0</span></span>|<span data-ttu-id="3e3e7-150">指示变更数据未准备就绪。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-150">Indicates that the change data is not ready.</span></span><br /><br /> <span data-ttu-id="3e3e7-151">在所选间隔的结束点之后没有变更数据捕获记录。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-151">There are no change data capture records later than the ending point of the selected interval.</span></span>|<span data-ttu-id="3e3e7-152">执行过程通过实现延迟的组件继续执行。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-152">Execution continues with the component that implements a delay.</span></span> <span data-ttu-id="3e3e7-153">然后该控件返回 For 循环容器，只要返回值为 0，就会继续检查执行 SQL 任务。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-153">Then control returns to the For Loop container, which continues to check the Execute SQL task as long as the value returned is 0.</span></span>|  
|<span data-ttu-id="3e3e7-154">1</span><span class="sxs-lookup"><span data-stu-id="3e3e7-154">1</span></span>|<span data-ttu-id="3e3e7-155">可能指示没有捕获到整个间隔的变更数据，或者变更数据已删除。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-155">Might indicate that the change data has not been captured for the complete interval, or that it has been deleted.</span></span> <span data-ttu-id="3e3e7-156">这被视为错误情况。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-156">This is treated as an error condition.</span></span><br /><br /> <span data-ttu-id="3e3e7-157">在所选间隔的起始点之前没有变更数据捕获记录。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-157">There are no change data capture records earlier than the starting point of the selected interval</span></span>|<span data-ttu-id="3e3e7-158">执行过程通过记录错误的可选组件继续执行。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-158">Execution continues with the optional component that logs the error.</span></span>|  
|<span data-ttu-id="3e3e7-159">2</span><span class="sxs-lookup"><span data-stu-id="3e3e7-159">2</span></span>|<span data-ttu-id="3e3e7-160">指示数据已准备就绪。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-160">Indicates that data is ready.</span></span><br /><br /> <span data-ttu-id="3e3e7-161">在所选间隔的起始点之前和结束点之后都存在变更数据捕获记录。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-161">There are change data capture records that are both earlier than the starting point and later than the ending point of the selected interval.</span></span>|<span data-ttu-id="3e3e7-162">执行将跳出 For 循环容器并且增量加载开始进行。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-162">Execution passes out of the For Loop container and the incremental load starts.</span></span>|  
|<span data-ttu-id="3e3e7-163">3</span><span class="sxs-lookup"><span data-stu-id="3e3e7-163">3</span></span>|<span data-ttu-id="3e3e7-164">指示所有可用的变更数据的首次加载。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-164">Indicates the initial load of all available change data.</span></span><br /><br /> <span data-ttu-id="3e3e7-165">条件逻辑从仅用于此目的特殊包变量中获取此值。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-165">The conditional logic obtains this value from a special package variable that is used only for this purpose.</span></span>|<span data-ttu-id="3e3e7-166">执行将跳出 For 循环容器并且增量加载开始进行。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-166">Execution passes out of the For Loop container and the incremental load starts.</span></span>|  
|<span data-ttu-id="3e3e7-167">5</span><span class="sxs-lookup"><span data-stu-id="3e3e7-167">5</span></span>|<span data-ttu-id="3e3e7-168">指示已达到 TimeoutCeiling。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-168">Indicates that the TimeoutCeiling has been reached.</span></span><br /><br /> <span data-ttu-id="3e3e7-169">循环已对数据执行了指定次数的测试，数据仍不可用。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-169">The loop has tested for data the specified number of times, and data is still not available.</span></span> <span data-ttu-id="3e3e7-170">如果没有此测试或类似的测试，该包可能会无限期地运行。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-170">Without this test or a similar test, the package might run indefinitely.</span></span>|<span data-ttu-id="3e3e7-171">执行过程通过记录超时的可选组件继续执行。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-171">Execution continues with the optional component that logs the timeout.</span></span>|  
  
#### <a name="to-configure-an-execute-sql-task-to-query-whether-change-data-is-ready"></a><span data-ttu-id="3e3e7-172">配置执行 SQL 任务，以查询变更数据是否已准备就绪</span><span class="sxs-lookup"><span data-stu-id="3e3e7-172">To configure an Execute SQL task to query whether change data is ready</span></span>  
  
1.  <span data-ttu-id="3e3e7-173">在 For 循环容器内，添加一个执行 SQL 任务。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-173">Inside the For Loop container, add an Execute SQL task.</span></span>  
  
2.  <span data-ttu-id="3e3e7-174">在 **“执行 SQL 任务编辑器”** 中的 **“常规”** 页上，选择以下选项：</span><span class="sxs-lookup"><span data-stu-id="3e3e7-174">In the **Execute SQL Task Editor**, on the **General** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="3e3e7-175">对于 **ResultSet**，选择 **“单行”** 。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-175">For **ResultSet**, select **Single row**.</span></span>  
  
    2.  <span data-ttu-id="3e3e7-176">配置到源数据库的有效连接。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-176">Configure a valid connection to the source database.</span></span>  
  
    3.  <span data-ttu-id="3e3e7-177">对于 **SQLSourceType**，选择 **“直接输入”** 。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-177">For **SQLSourceType**, select **Direct input**.</span></span>  
  
    4.  <span data-ttu-id="3e3e7-178">对于 **SQLStatement**，输入以下 SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="3e3e7-178">For **SQLStatement**, enter the following SQL statement:</span></span>  
  
        ```  
        declare @DataReady int, @TimeoutCount int  
  
        if not exists (select tran_end_time from cdc.lsn_time_mapping  
                where tran_end_time > ?  )  
            select @DataReady = 0  
        else  
            if ? = 0  
                select @DataReady = 3   
        else  
            if not exists (select tran_end_time from cdc.lsn_time_mapping  
                    where tran_end_time <= ? )  
                select @DataReady = 1   
        else  
            select @DataReady = 2  
  
        select @TimeoutCount = ?  
        if (@DataReady = 0)  
            select @TimeoutCount = @TimeoutCount + 1  
        else  
            select @TimeoutCount = 0  
  
        if (@TimeoutCount > ?)  
            select @DataReady = 5  
  
        select @DataReady as DataReady, @TimeoutCount as TimeoutCount  
  
        ```  
  
3.  <span data-ttu-id="3e3e7-179">在 **“执行 SQL 任务编辑器”** 的 **“参数映射”** 页上，进行以下映射：</span><span class="sxs-lookup"><span data-stu-id="3e3e7-179">On the **Parameter Mapping** page of the **Execute SQL Task Editor**, make the following mappings:</span></span>  
  
    1.  <span data-ttu-id="3e3e7-180">将 ExtractEndTime 变量映射到参数 0。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-180">Map the ExtractEndTime variable to parameter 0.</span></span>  
  
    2.  <span data-ttu-id="3e3e7-181">将 IntervalID 变量映射到参数 1。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-181">Map the IntervalID variable to parameter 1.</span></span>  
  
    3.  <span data-ttu-id="3e3e7-182">将 ExtractStartTime 变量映射到参数 2。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-182">Map the ExtractStartTime variable to parameter 2.</span></span>  
  
    4.  <span data-ttu-id="3e3e7-183">将 TimeoutCount 变量映射到参数 3。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-183">Map the TimeoutCount variable to parameter 3.</span></span>  
  
    5.  <span data-ttu-id="3e3e7-184">将 TimeoutCeiling 变量映射到参数 4。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-184">Map the TimeoutCeiling variable to parameter 4.</span></span>  
  
4.  <span data-ttu-id="3e3e7-185">在 **“执行 SQL 任务编辑器”** 的 **“结果集”** 页上，将 DataReady 结果映射到 DataReady 变量，并将 TimeoutCount 结果映射到 TimeoutCount 变量。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-185">On the **Result Set** page of the **Execute SQL Task Editor**, map the DataReady result to the DataReady variable, and the TimeoutCount result to the TimeoutCount variable.</span></span>  
  
## <a name="waiting-until-the-change-data-is-ready"></a><span data-ttu-id="3e3e7-186">等到变更数据准备就绪</span><span class="sxs-lookup"><span data-stu-id="3e3e7-186">Waiting Until the Change Data Is Ready</span></span>  
 <span data-ttu-id="3e3e7-187">当变更数据未准备就绪时，您可以使用多种方法中的一种来实现延迟。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-187">You can use one of several methods to implement a delay when the change data is not ready.</span></span> <span data-ttu-id="3e3e7-188">下面的两个过程演示如何使用脚本任务或执行 SQL 任务来实现延迟。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-188">The following two procedures illustrate how to use a Script task or an Execute SQL task to implement the delay.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3e3e7-189">预编译的脚本产生的开销小于执行 SQL 任务。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-189">A precompiled script incurs less overhead than an Execute SQL task.</span></span>  
  
#### <a name="to-implement-a-delay-by-using-a-script-task"></a><span data-ttu-id="3e3e7-190">使用脚本任务实现延迟</span><span class="sxs-lookup"><span data-stu-id="3e3e7-190">To implement a delay by using a Script task</span></span>  
  
1.  <span data-ttu-id="3e3e7-191">在 For 循环容器内，添加一个脚本任务。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-191">Inside the For Loop container, add a Script task.</span></span>  
  
2.  <span data-ttu-id="3e3e7-192">将进行查询以确定变更数据是否准备就绪的执行 SQL 任务连接到新的脚本任务。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-192">Connect the Execute SQL task that queries to determine whether the change data is ready to the new Script task.</span></span>  
  
3.  <span data-ttu-id="3e3e7-193">对于用于将执行 SQL 任务连接到脚本任务的优先约束，打开 **“优先约束编辑器”** 并选择以下选项：</span><span class="sxs-lookup"><span data-stu-id="3e3e7-193">For the precedence constraint that connects the Execute SQL task to the Script task, open the **Precedence Constraint Editor** and select the following options:</span></span>  
  
    1.  <span data-ttu-id="3e3e7-194">对于 **“求值运算”** ，选择 **“表达式和约束”** 。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-194">For **Evaluation operation**, select **Expression and Constraint**.</span></span>  
  
    2.  <span data-ttu-id="3e3e7-195">对于 **“值”** ，选择 **“成功”** 。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-195">For **Value**, select **Success**.</span></span>  
  
         <span data-ttu-id="3e3e7-196">约束值 **“成功”** 指上一任务成功。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-196">The constraint value of **Success** refers to the success of the previous task.</span></span> <span data-ttu-id="3e3e7-197">在此例中，指执行 SQL 任务成功。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-197">In this case, the success of the Execute SQL task.</span></span>  
  
    3.  <span data-ttu-id="3e3e7-198">对于 **“表达式”** ，输入 `@DataReady == 0 && @TimeoutCount <= @TimeoutCeiling`。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-198">For **Expression**, enter `@DataReady == 0 && @TimeoutCount <= @TimeoutCeiling`.</span></span>  
  
    4.  <span data-ttu-id="3e3e7-199">选择 **“逻辑与。所有约束的计算结果都必须为 True**（如果尚未选择）。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-199">Select **Logical AND. All constraints must evaluate to True**, if not already selected.</span></span>  
  
4.  <span data-ttu-id="3e3e7-200">在 **“脚本任务编辑器”** 的 **“脚本”** 页上，对于 **ReadOnlyVariables**，从列表中选择 **User::DelaySeconds** 整数变量。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-200">In the **Script Task Editor**, on the **Script** page, for **ReadOnlyVariables**, select the **User::DelaySeconds** integer variable from the list.</span></span>  
  
5.  <span data-ttu-id="3e3e7-201">在 **“脚本任务编辑器”** 的 **“脚本”** 页上，单击 **“编辑脚本”** 以打开脚本开发环境。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-201">In the **Script Task Editor**, on the **Script** page, click **Edit Script** to open the script development environment.</span></span>  
  
6.  <span data-ttu-id="3e3e7-202">在 Main 过程中，输入下面的代码行之一：</span><span class="sxs-lookup"><span data-stu-id="3e3e7-202">In the Main procedure, enter one of the following lines of code:</span></span>  
  
    -   <span data-ttu-id="3e3e7-203">如果您是使用 C# 进行编程，请输入下面的代码行：</span><span class="sxs-lookup"><span data-stu-id="3e3e7-203">If you are programming in C#, enter the following line of code:</span></span>  
  
        ```  
        System.Threading.Thread.Sleep((int)Dts.Variables["DelaySeconds"].Value * 1000);  
        ```  
  
         <span data-ttu-id="3e3e7-204">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="3e3e7-204">\- or -</span></span>  
  
    -   <span data-ttu-id="3e3e7-205">如果您是使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]进行编程，请输入下面的代码行：</span><span class="sxs-lookup"><span data-stu-id="3e3e7-205">If you are programming in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], enter the following line of code:</span></span>  
  
        ```  
        System.Threading.Thread.Sleep(Ctype(Dts.Variables("DelaySeconds").Value, Integer) * 1000)  
  
        ```  
  
        > [!NOTE]  
        >  <span data-ttu-id="3e3e7-206">`Thread.Sleep` 方法要求指定参数时以毫秒为单位。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-206">The `Thread.Sleep` method expects an argument that is specified in milliseconds.</span></span>  
  
7.  <span data-ttu-id="3e3e7-207">保留从脚本执行过程返回 `DtsExecResult.Success` 的默认代码行。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-207">Leave the default line of code which returns `DtsExecResult.Success` from the execution of the script.</span></span>  
  
8.  <span data-ttu-id="3e3e7-208">关闭脚本开发环境和 **“脚本任务编辑器”** 。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-208">Close the script development environment and the **Script Task Editor**.</span></span>  
  
#### <a name="to-implement-a-delay-by-using-an-execute-sql-task"></a><span data-ttu-id="3e3e7-209">使用执行 SQL 任务实现延迟</span><span class="sxs-lookup"><span data-stu-id="3e3e7-209">To implement a delay by using an Execute SQL task</span></span>  
  
1.  <span data-ttu-id="3e3e7-210">在 For 循环容器内，添加一个执行 SQL 任务。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-210">Inside the For Loop container, add an Execute SQL task.</span></span>  
  
2.  <span data-ttu-id="3e3e7-211">将进行查询以确定变更数据是否准备就绪的执行 SQL 任务连接到新的执行 SQL 任务。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-211">Connect the Execute SQL task that queries to determine whether the change data is ready to the new Execute SQL task.</span></span>  
  
3.  <span data-ttu-id="3e3e7-212">对于用于连接两个执行 SQL 任务的优先约束，打开 **“优先约束编辑器”** 并选择以下选项：</span><span class="sxs-lookup"><span data-stu-id="3e3e7-212">For the precedence constraint that connects the two Execute SQL tasks, open the **Precedence Constraint Editor** and select the following options:</span></span>  
  
    1.  <span data-ttu-id="3e3e7-213">对于 **“求值运算”** ，选择 **“表达式和约束”** 。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-213">For **Evaluation operation**, select **Expression and Constraint**.</span></span>  
  
    2.  <span data-ttu-id="3e3e7-214">对于 **“值”** ，选择 **“成功”** 。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-214">For **Value**, select **Success**.</span></span>  
  
         <span data-ttu-id="3e3e7-215">约束值 **“成功”** 指上一执行 SQL 任务成功。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-215">The constraint value of **Success** refers to the success of the previous Execute SQL task.</span></span>  
  
    3.  <span data-ttu-id="3e3e7-216">对于 **“表达式”** ，输入 `@DataReady == 0`。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-216">For **Expression**, enter `@DataReady == 0`.</span></span>  
  
    4.  <span data-ttu-id="3e3e7-217">选择 **“逻辑与。所有约束的计算结果都必须为 True**（如果尚未选择）。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-217">Select **Logical AND. All constraints must evaluate to True**, if not already selected.</span></span>  
  
         <span data-ttu-id="3e3e7-218">此选项要求条件、约束和表达式都必须为 true。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-218">This selection requires that both conditions, the constraint and the expression, must be true.</span></span>  
  
4.  <span data-ttu-id="3e3e7-219">在 **“执行 SQL 任务编辑器”** 中的 **“常规”** 页上，选择以下选项：</span><span class="sxs-lookup"><span data-stu-id="3e3e7-219">In the **Execute SQL Task Editor**, on the **General** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="3e3e7-220">对于 **ResultSet**，选择 **“单行”** 。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-220">For **ResultSet**, select **Single row**.</span></span>  
  
    2.  <span data-ttu-id="3e3e7-221">配置到源数据库的有效连接。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-221">Configure a valid connection to the source database.</span></span>  
  
    3.  <span data-ttu-id="3e3e7-222">对于 **SQLSourceType**，选择 **“直接输入”** 。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-222">For **SQLSourceType**, select **Direct input**.</span></span>  
  
    4.  <span data-ttu-id="3e3e7-223">对于 **SQLStatement**，输入以下 SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="3e3e7-223">For **SQLStatement**, enter the following SQL statement:</span></span>  
  
        ```  
        WAITFOR DELAY ?  
  
        ```  
  
5.  <span data-ttu-id="3e3e7-224">在编辑器的 **“参数映射”** 页上，将 DelaySeconds 字符串变量映射到参数 0。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-224">On the **Parameter Mapping** page of the editor, map the DelaySeconds string variable to parameter 0.</span></span>  
  
## <a name="handling-an-error-condition"></a><span data-ttu-id="3e3e7-225">处理错误情况</span><span class="sxs-lookup"><span data-stu-id="3e3e7-225">Handling an Error Condition</span></span>  
 <span data-ttu-id="3e3e7-226">您可以选择在循环内配置额外的组件以记录错误或超时情况：</span><span class="sxs-lookup"><span data-stu-id="3e3e7-226">You can optionally configure an additional component inside the loop to log an error or a timeout condition:</span></span>  
  
-   <span data-ttu-id="3e3e7-227">当 DataReady 变量的值 = 1 时，此组件可以记录错误情况。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-227">This component can log an error condition when the value of the DataReady variable = 1.</span></span> <span data-ttu-id="3e3e7-228">此值指示在所选间隔开始前没有可用的变更数据。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-228">This value indicates that there is no available change data before the start of the selected interval.</span></span>  
  
-   <span data-ttu-id="3e3e7-229">达到 TimeoutCeiling 变量的值时，此组件还可以记录超时情况。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-229">This component can also log a timeout condition when the value of the TimeoutCeiling variable is reached.</span></span> <span data-ttu-id="3e3e7-230">此值指示循环已对数据执行了指定次数的测试，但数据仍不可用。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-230">This value indicates the loop has tested for data the specified number of times, and data is still not available.</span></span> <span data-ttu-id="3e3e7-231">如果没有此测试或类似的测试，该包可能会无限期地运行。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-231">Without this test or a similar test, the package might run indefinitely.</span></span>  
  
#### <a name="to-configure-an-optional-script-task-to-log-an-error-condition"></a><span data-ttu-id="3e3e7-232">配置可选的脚本任务以记录错误情况</span><span class="sxs-lookup"><span data-stu-id="3e3e7-232">To configure an optional Script task to log an error condition</span></span>  
  
1.  <span data-ttu-id="3e3e7-233">如果想要通过将消息写入日志记录来报告错误或超时，请配置包的日志记录功能。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-233">If you want to report the error or timeout by writing a message to the log, configure logging for the package.</span></span> <span data-ttu-id="3e3e7-234">有关详细信息，请参阅 [在 SQL Server Data Tools 中启用包日志记录](../enable-package-logging-in-sql-server-data-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-234">For more information, see [Enable Package Logging in SQL Server Data Tools](../enable-package-logging-in-sql-server-data-tools.md).</span></span>  
  
2.  <span data-ttu-id="3e3e7-235">在 For 循环容器内，添加一个脚本任务。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-235">Inside the For Loop container, add a Script task.</span></span>  
  
3.  <span data-ttu-id="3e3e7-236">将进行查询以确定变更数据是否准备就绪的执行 SQL 任务连接到新的脚本任务。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-236">Connect the Execute SQL task that queries to determine whether the change data is ready to the new Script task.</span></span>  
  
4.  <span data-ttu-id="3e3e7-237">对于用于将执行 SQL 任务连接到脚本任务的优先约束，打开 **“优先约束编辑器”** 并选择以下选项：</span><span class="sxs-lookup"><span data-stu-id="3e3e7-237">For the precedence constraint that connects the Execute SQL task to the Script task, open the **Precedence Constraint Editor** and select the following options:</span></span>  
  
    1.  <span data-ttu-id="3e3e7-238">对于 **“求值运算”** ，选择 **“表达式和约束”** 。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-238">For **Evaluation operation**, select **Expression and Constraint**.</span></span>  
  
    2.  <span data-ttu-id="3e3e7-239">对于 **“值”** ，选择 **“成功”** 。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-239">For **Value**, select **Success**.</span></span>  
  
         <span data-ttu-id="3e3e7-240">约束值 **“成功”** 指上一任务成功。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-240">The constraint value of **Success** refers to the success of the previous task.</span></span> <span data-ttu-id="3e3e7-241">在此例中，指执行 SQL 任务成功。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-241">In this case, the success of the Execute SQL task.</span></span>  
  
    3.  <span data-ttu-id="3e3e7-242">对于 **“表达式”** ，输入 `@DataReady == 1 || @DataReady == 5`。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-242">For **Expression**, enter `@DataReady == 1 || @DataReady == 5`.</span></span>  
  
    4.  <span data-ttu-id="3e3e7-243">选择 **“逻辑与。所有约束的计算结果都必须为 True**（如果尚未选择）。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-243">Select **Logical AND. All constraints must evaluate to True**, if not already selected.</span></span>  
  
         <span data-ttu-id="3e3e7-244">此选项要求条件、约束和表达式都必须为 true。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-244">This selection requires that both conditions, the constraint and the expression, must be true.</span></span>  
  
5.  <span data-ttu-id="3e3e7-245">在 **“脚本任务编辑器”** 的 **“脚本”** 页上，对于 **ReadOnlyVariables**，从列表中选择 **User::DataReady** 和 **User::ExtractStartTime** 以便脚本可以使用它们的值。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-245">In the **Script Task Editor**, on the **Script** page of the editor, for **ReadOnlyVariables**, select **User::DataReady** and **User::ExtractStartTime** from the list to make their values available to the script.</span></span>  
  
     <span data-ttu-id="3e3e7-246">如果要在写入日志记录的信息中包含特定的系统变量信息（例如 System::PackageName），还可选择这些变量。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-246">If you want to include information from certain system variables (for example, System::PackageName) in the information that you write to the log, select those variables also.</span></span>  
  
6.  <span data-ttu-id="3e3e7-247">在 **“脚本任务编辑器”** 的 **“脚本”** 页上，单击 **“编辑脚本”** 以打开脚本开发环境。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-247">In the **Script Task Editor**, on the **Script** page, click **Edit Script** to open the script development environment.</span></span>  
  
7.  <span data-ttu-id="3e3e7-248">在 Main 过程中，输入代码以通过调用 `Dts.Log` 方法来记录错误，或者通过调用 `Dts.Events` 接口的方法之一来引发事件。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-248">In the Main procedure, enter code to log an error by calling the `Dts.Log` method, or to raise an event by calling one of the methods of the `Dts.Events` interface.</span></span> <span data-ttu-id="3e3e7-249">通过返回 `Dts.TaskResult = Dts.Results.Failure`向包发出错误通知。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-249">Inform the package of the error by returning `Dts.TaskResult = Dts.Results.Failure`.</span></span>  
  
     <span data-ttu-id="3e3e7-250">下面的示例显示如何将消息写入日志。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-250">The following sample shows how to write a message to the log.</span></span> <span data-ttu-id="3e3e7-251">有关详细信息，请参阅 [Logging in the Script Task](../extending-packages-scripting/task/logging-in-the-script-task.md)、 [Raising Events in the Script Task](../extending-packages-scripting/task/raising-events-in-the-script-task.md)和 [Returning Results from the Script Task](../extending-packages-scripting/task/returning-results-from-the-script-task.md)。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-251">For more information, see [Logging in the Script Task](../extending-packages-scripting/task/logging-in-the-script-task.md), [Raising Events in the Script Task](../extending-packages-scripting/task/raising-events-in-the-script-task.md), and [Returning Results from the Script Task](../extending-packages-scripting/task/returning-results-from-the-script-task.md).</span></span>  
  
    ```  
    ' User variables.  
    Dim dataReady As Integer = _  
      CType(Dts.Variables("DataReady").Value, Integer)  
    Dim extractStartTime As Date = _  
      CType(Dts.Variables("ExtractStartTime").Value, DateTime)  
  
    ' System variables.  
    Dim packageName As String = _  
      Dts.Variables("PackageName").Value.ToString()  
    Dim executionStartTime As Date = _  
      CType(Dts.Variables("StartTime").Value, DateTime)  
  
    Dim eventMessage As New System.Text.StringBuilder()  
  
    If dataReady = 1 OrElse dataReady = 5 Then  
  
      If dataReady = 1 Then  
        eventMessage.AppendLine("Start Time Error")  
      Else  
        eventMessage.AppendLine("Timeout Error")  
      End If  
  
      With eventMessage  
        .Append("The package ")  
        .Append(packageName)  
        .Append(" started at ")  
        .Append(executionStartTime.ToString())  
        .Append(" and ended at ")  
        .AppendLine(DateTime.Now().ToString())  
        If dataReady = 1 Then  
          .Append("The specified ExtractStartTime was ")  
          .AppendLine(extractStartTime.ToString())  
        End If  
      End With  
  
      System.Windows.Forms.MessageBox.Show(eventMessage.ToString())  
  
      Dts.Log(eventMessage.ToString(), 0, Nothing)  
  
      Dts.TaskResult = Dts.Results.Failure  
  
    Else  
  
      Dts.TaskResult = Dts.Results.Success  
  
    End If  
  
    ```  
  
8.  <span data-ttu-id="3e3e7-252">关闭脚本开发环境和 **“脚本任务编辑器”** 。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-252">Close the script development environment and the **Script Task Editor**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="3e3e7-253">下一步</span><span class="sxs-lookup"><span data-stu-id="3e3e7-253">Next Step</span></span>  
 <span data-ttu-id="3e3e7-254">在确定变更数据已准备就绪之后，下一步就是准备查询变更数据。</span><span class="sxs-lookup"><span data-stu-id="3e3e7-254">After you determine that change data is ready, the next step is to prepare to query for the change data.</span></span>  
  
 <span data-ttu-id="3e3e7-255">**下一个主题：** [准备查询变更数据](prepare-to-query-for-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="3e3e7-255">**Next topic:** [Prepare to Query for the Change Data](prepare-to-query-for-the-change-data.md)</span></span>  
  
  
