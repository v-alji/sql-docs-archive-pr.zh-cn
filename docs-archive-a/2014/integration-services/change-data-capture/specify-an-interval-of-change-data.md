---
title: 指定变更数据的间隔 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],specifying interval
ms.assetid: 17899078-8ba3-4f40-8769-e9837dc3ec60
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 70b9c14d609f2db69ee5751eca18acb5262a07a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580320"
---
# <a name="specify-an-interval-of-change-data"></a><span data-ttu-id="0c451-102">指定变更数据的间隔</span><span class="sxs-lookup"><span data-stu-id="0c451-102">Specify an Interval of Change Data</span></span>
  <span data-ttu-id="0c451-103">在用于执行变更数据增量加载的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的控制流中，第一个任务是计算变更数据的端点。</span><span class="sxs-lookup"><span data-stu-id="0c451-103">In the control flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the first task is to calculate the endpoints of the change interval.</span></span> <span data-ttu-id="0c451-104">这些端点是 `datetime` 值，将存储在包变量中以供以后在包中使用。</span><span class="sxs-lookup"><span data-stu-id="0c451-104">These endpoints are `datetime` values and will be stored in package variables for use later in the package.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0c451-105">有关设计控制流的总体过程的说明，请参阅[变更数据捕获 (SSIS)](change-data-capture-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="0c451-105">For a description of the overall process of designing the control flow, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="set-up-package-variables-for-the-endpoints"></a><span data-ttu-id="0c451-106">为端点设置包变量</span><span class="sxs-lookup"><span data-stu-id="0c451-106">Set Up Package Variables for the Endpoints</span></span>  
 <span data-ttu-id="0c451-107">在配置执行 SQL 任务以计算端点之前，必须先定义用于存储端点的包变量。</span><span class="sxs-lookup"><span data-stu-id="0c451-107">Before configuring the Execute SQL task to calculate the endpoints, the package variables that will store the endpoints have to be defined.</span></span>  
  
#### <a name="to-set-up-package-variables"></a><span data-ttu-id="0c451-108">设置包变量</span><span class="sxs-lookup"><span data-stu-id="0c451-108">To set up package variables</span></span>  
  
1.  <span data-ttu-id="0c451-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开新的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="0c451-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="0c451-110">在 **“变量”** 窗口中创建以下变量：</span><span class="sxs-lookup"><span data-stu-id="0c451-110">In the **Variables** window, create the following variables:</span></span>  
  
    1.  <span data-ttu-id="0c451-111">创建一个数据类型为 `datetime` 的变量以保存间隔的起始点。</span><span class="sxs-lookup"><span data-stu-id="0c451-111">Create a variable with the `datetime` data type to hold the starting point for the interval.</span></span>  
  
         <span data-ttu-id="0c451-112">以下示例使用变量名 ExtractStartTime。</span><span class="sxs-lookup"><span data-stu-id="0c451-112">This example uses the variable name, ExtractStartTime.</span></span>  
  
    2.  <span data-ttu-id="0c451-113">再创建一个数据类型为 `datetime` 的变量以保存间隔的结束点。</span><span class="sxs-lookup"><span data-stu-id="0c451-113">Create another variable with the `datetime` data type to hold the ending point for the interval.</span></span>  
  
         <span data-ttu-id="0c451-114">以下示例使用变量名 ExtractEndTime。</span><span class="sxs-lookup"><span data-stu-id="0c451-114">This example uses the variable name, ExtractEndTime.</span></span>  
  
 <span data-ttu-id="0c451-115">如果在执行多个子包的主包中计算端点，则可使用父包变量配置将这些变量的值传递给各个子包。</span><span class="sxs-lookup"><span data-stu-id="0c451-115">If you calculate the endpoints in a master package that executes multiple child packages, you can use Parent Package Variable configurations to pass the values of these variables to each child package.</span></span> <span data-ttu-id="0c451-116">有关详细信息，请参阅 [执行包任务](../control-flow/execute-package-task.md) 和 [在子包中使用变量和参数的值](../use-the-values-of-variables-and-parameters-in-a-child-package.md)。</span><span class="sxs-lookup"><span data-stu-id="0c451-116">For more information, see [Execute Package Task](../control-flow/execute-package-task.md) and [Use the Values of Variables and Parameters in a Child Package](../use-the-values-of-variables-and-parameters-in-a-child-package.md).</span></span>  
  
## <a name="calculate-a-starting-point-and-an-ending-point-for-change-data"></a><span data-ttu-id="0c451-117">计算变更数据的起始点和结束点</span><span class="sxs-lookup"><span data-stu-id="0c451-117">Calculate a Starting Point and an Ending Point for Change Data</span></span>  
 <span data-ttu-id="0c451-118">为间隔端点设置包变量之后，即可计算这些端点的实际值并将这些值映射到相应的包变量中。</span><span class="sxs-lookup"><span data-stu-id="0c451-118">After you set up the package variables for the interval endpoints, you can calculate the actual values for those endpoints and map those values to the corresponding package variables.</span></span> <span data-ttu-id="0c451-119">因为这些端点为 `datetime` 值，所以您必须使用可以计算或处理 `datetime` 值的函数。</span><span class="sxs-lookup"><span data-stu-id="0c451-119">Because those endpoints are `datetime` values, you will have to use functions that can calculate or work with `datetime` values.</span></span> <span data-ttu-id="0c451-120">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 表达式语言和 Transact-SQL 都具有可处理 `datetime` 值的函数：</span><span class="sxs-lookup"><span data-stu-id="0c451-120">Both the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language and Transact-SQL have functions that work with `datetime` values:</span></span>  
  
 <span data-ttu-id="0c451-121">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 表达式语言中可处理 `datetime` 值的函数</span><span class="sxs-lookup"><span data-stu-id="0c451-121">Functions in the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language that work with `datetime` values</span></span>  
 -   [<span data-ttu-id="0c451-122">DATEADD（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="0c451-122">DATEADD &#40;SSIS Expression&#41;</span></span>](../expressions/dateadd-ssis-expression.md)  
  
-   [<span data-ttu-id="0c451-123">DATEDIFF（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="0c451-123">DATEDIFF &#40;SSIS Expression&#41;</span></span>](../expressions/datediff-ssis-expression.md)  
  
-   [<span data-ttu-id="0c451-124">DATEPART（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="0c451-124">DATEPART &#40;SSIS Expression&#41;</span></span>](../expressions/datepart-ssis-expression.md)  
  
-   [<span data-ttu-id="0c451-125">DAY（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="0c451-125">DAY &#40;SSIS Expression&#41;</span></span>](../expressions/day-ssis-expression.md)  
  
-   [<span data-ttu-id="0c451-126">GETDATE（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="0c451-126">GETDATE &#40;SSIS Expression&#41;</span></span>](../expressions/getdate-ssis-expression.md)  
  
-   [<span data-ttu-id="0c451-127">GETUTCDATE（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="0c451-127">GETUTCDATE &#40;SSIS Expression&#41;</span></span>](../expressions/getutcdate-ssis-expression.md)  
  
-   [<span data-ttu-id="0c451-128">MONTH（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="0c451-128">MONTH &#40;SSIS Expression&#41;</span></span>](../expressions/month-ssis-expression.md)  
  
-   [<span data-ttu-id="0c451-129">YEAR（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="0c451-129">YEAR &#40;SSIS Expression&#41;</span></span>](../expressions/year-ssis-expression.md)  
  
 <span data-ttu-id="0c451-130">Transact-SQL 中可处理 `datetime` 值的函数</span><span class="sxs-lookup"><span data-stu-id="0c451-130">Functions in Transact-SQL that work with `datetime` values</span></span>  
 <span data-ttu-id="0c451-131">[日期和时间的数据类型及函数 (Transact-SQL)](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0c451-131">[Date and Time Data Types and Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql).</span></span>  
  
 <span data-ttu-id="0c451-132">在使用上述任一 `datetime` 函数来计算端点之前，必须先确定间隔是否固定并且定期发生。</span><span class="sxs-lookup"><span data-stu-id="0c451-132">Before you use any one of these `datetime` functions to calculate the endpoints, you have to determine whether the interval is fixed and occurs on a regular schedule.</span></span> <span data-ttu-id="0c451-133">通常，您会希望定期将在源表中发生的变更应用到目标表中。</span><span class="sxs-lookup"><span data-stu-id="0c451-133">Typically, you want to apply changes that have occurred in source tables to destination tables on a regular schedule.</span></span> <span data-ttu-id="0c451-134">例如，您可能希望每小时、每天或每周应用这些变更。</span><span class="sxs-lookup"><span data-stu-id="0c451-134">For example, you might want to apply those changes on an hourly, daily, or weekly basis.</span></span>  
  
 <span data-ttu-id="0c451-135">在了解变更间隔是固定的还是随机的之后，即可计算端点：</span><span class="sxs-lookup"><span data-stu-id="0c451-135">After you understand whether your change interval is fixed or is more random, you can calculate the endpoints:</span></span>  
  
-   <span data-ttu-id="0c451-136">**计算起始日期和时间**。</span><span class="sxs-lookup"><span data-stu-id="0c451-136">**Calculating the starting date and time**.</span></span> <span data-ttu-id="0c451-137">将上一次加载的结束日期和时间作为当前的起始日期和时间。</span><span class="sxs-lookup"><span data-stu-id="0c451-137">You use the ending date and time from the previous load as the current starting date and time.</span></span> <span data-ttu-id="0c451-138">如果对增量加载使用固定间隔，则可使用 Transact-SQL 或 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 表达式语言的 `datetime` 函数来计算此值。</span><span class="sxs-lookup"><span data-stu-id="0c451-138">If you use a fixed interval for incremental loads, you can calculate this value by using the `datetime` functions of Transact-SQL or of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language.</span></span> <span data-ttu-id="0c451-139">否则，您可能需要保持两个执行之间的端点，并使用执行 SQL 任务或脚本任务来加载上一个端点。</span><span class="sxs-lookup"><span data-stu-id="0c451-139">Otherwise, you might have to persist the endpoints between executions, and use an Execute SQL task or a Script task to load the previous endpoint.</span></span>  
  
-   <span data-ttu-id="0c451-140">**计算结束日期和时间**。</span><span class="sxs-lookup"><span data-stu-id="0c451-140">**Calculating the ending date and time**.</span></span> <span data-ttu-id="0c451-141">如果对增量加载使用固定间隔，则可将当前的结束日期和时间作为起始日期和时间的偏移量来计算。</span><span class="sxs-lookup"><span data-stu-id="0c451-141">If you use a fixed interval for incremental loads, calculate the current ending date and time as an offset from the starting date and time.</span></span> <span data-ttu-id="0c451-142">同样，可以使用 `datetime` transact-sql 或表达式语言的函数来计算此值 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0c451-142">Again, you can calculate this value by using the `datetime` functions of Transact-SQL or of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language.</span></span>  
  
 <span data-ttu-id="0c451-143">在下面的过程中，变更间隔使用固定间隔，并假定无例外的情况下增量加载包每天运行。</span><span class="sxs-lookup"><span data-stu-id="0c451-143">In the following procedure, the change interval uses a fixed interval and assumes that the incremental load package is run daily without exception.</span></span> <span data-ttu-id="0c451-144">否则，缺失间隔的变更数据会丢失。</span><span class="sxs-lookup"><span data-stu-id="0c451-144">Otherwise, change data for missed intervals would be lost.</span></span> <span data-ttu-id="0c451-145">此间隔的起始点是前天午夜，即 24 小时和 48 小时之前。</span><span class="sxs-lookup"><span data-stu-id="0c451-145">The starting point for the interval is midnight the day before yesterday, that is, between 24 and 48 hours ago.</span></span> <span data-ttu-id="0c451-146">此间隔的结束点是昨天午夜，即，昨天晚上，0 和 24 小时之前。</span><span class="sxs-lookup"><span data-stu-id="0c451-146">The ending point for the interval is midnight yesterday, that is, the previous night, between 0 and 24 hours ago.</span></span>  
  
#### <a name="to-calculate-the-starting-point-and-ending-point-for-the-capture-interval"></a><span data-ttu-id="0c451-147">计算捕获间隔的起始点和结束点</span><span class="sxs-lookup"><span data-stu-id="0c451-147">To calculate the starting point and ending point for the capture interval</span></span>  
  
1.  <span data-ttu-id="0c451-148">在 **设计器的** “控制流” [!INCLUDE[ssIS](../../includes/ssis-md.md)] 选项卡上，向包中添加一个执行 SQL 任务。</span><span class="sxs-lookup"><span data-stu-id="0c451-148">On the **Control Flow** tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add an Execute SQL Task to the package.</span></span>  
  
2.  <span data-ttu-id="0c451-149">打开 **“执行 SQL 任务编辑器”** ，在编辑器的 **“常规”** 页上，选择以下选项：</span><span class="sxs-lookup"><span data-stu-id="0c451-149">Open the **Execute SQL Task Editor**, and on the **General** page of the editor, select the following options:</span></span>  
  
    1.  <span data-ttu-id="0c451-150">对于 **ResultSet**，选择 **“单行”** 。</span><span class="sxs-lookup"><span data-stu-id="0c451-150">For **ResultSet**, select **Single row**.</span></span>  
  
    2.  <span data-ttu-id="0c451-151">配置到源数据库的有效连接。</span><span class="sxs-lookup"><span data-stu-id="0c451-151">Configure a valid connection to the source database.</span></span>  
  
    3.  <span data-ttu-id="0c451-152">对于 **SQLSourceType**，选择 **“直接输入”** 。</span><span class="sxs-lookup"><span data-stu-id="0c451-152">For **SQLSourceType**, select **Direct input**.</span></span>  
  
    4.  <span data-ttu-id="0c451-153">对于 **SQLStatement**，输入以下 SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="0c451-153">For **SQLStatement**, enter the following SQL statement:</span></span>  
  
        ```  
        SELECT DATEADD(dd,0, DATEDIFF(dd,0,GETDATE()-1)) AS ExtractStartTime,  
          DATEADD(dd,0, DATEDIFF(dd,0,GETDATE())) AS ExtractEndTime  
  
        ```  
  
3.  <span data-ttu-id="0c451-154">在 **“执行 SQL 任务编辑器”** 的 **“结果集”** 页上，将 ExtractStartTime 结果映射到 ExtractStartTime 包变量，并将 ExtractEndTime 结果映射到 ExtractEndTime 包变量。</span><span class="sxs-lookup"><span data-stu-id="0c451-154">On the **Result Set** page of the **Execute SQL Task Editor**, map the ExtractStartTime result to the ExtractStartTime package variable, and map the ExtractEndTime result to the ExtractEndTime package variable.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0c451-155">如果使用表达式设置 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 变量的值，则每次访问该变量的值时都会计算表达式。</span><span class="sxs-lookup"><span data-stu-id="0c451-155">When you use an expression to set the value of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] variable, the expression is evaluated every time that the value of the variable is accessed.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="0c451-156">下一步</span><span class="sxs-lookup"><span data-stu-id="0c451-156">Next Step</span></span>  
 <span data-ttu-id="0c451-157">计算变更范围的起始点和结束点之后，下一步就是确定变更数据是否已准备就绪。</span><span class="sxs-lookup"><span data-stu-id="0c451-157">After you calculate the starting point and ending point for a range of changes, the next step is to determine whether the change data is ready.</span></span>  
  
 <span data-ttu-id="0c451-158">**下一个主题：** [确定变更数据是否已准备就绪](determine-whether-the-change-data-is-ready.md)</span><span class="sxs-lookup"><span data-stu-id="0c451-158">**Next topic:** [Determine Whether the Change Data Is Ready](determine-whether-the-change-data-is-ready.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c451-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0c451-159">See Also</span></span>  
 <span data-ttu-id="0c451-160">[在包中使用变量](../use-variables-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="0c451-160">[Use Variables in Packages](../use-variables-in-packages.md) </span></span>  
 <span data-ttu-id="0c451-161">[Integration Services (SSIS) 表达式](../expressions/integration-services-ssis-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="0c451-161">[Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md) </span></span>  
 <span data-ttu-id="0c451-162">[执行 SQL 任务](../control-flow/execute-sql-task.md) </span><span class="sxs-lookup"><span data-stu-id="0c451-162">[Execute SQL Task](../control-flow/execute-sql-task.md) </span></span>  
 [<span data-ttu-id="0c451-163">脚本任务</span><span class="sxs-lookup"><span data-stu-id="0c451-163">Script Task</span></span>](../control-flow/script-task.md)  
  
  
