---
title: 准备查询变更数据 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],preparing query
ms.assetid: 9ea2db7a-3dca-4bbf-9903-cccd2d494b5f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5ab732389d5a747c596472f14f5229361dd46275
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577779"
---
# <a name="prepare-to-query-for-the-change-data"></a><span data-ttu-id="62bec-102">准备查询变更数据</span><span class="sxs-lookup"><span data-stu-id="62bec-102">Prepare to Query for the Change Data</span></span>
  <span data-ttu-id="62bec-103">在用于执行变更数据增量加载的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的控制流中，第三个任务（即最后一个任务）是准备查询变更数据和添加数据流任务。</span><span class="sxs-lookup"><span data-stu-id="62bec-103">In the control flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the third and final task is to prepare to query for the change data and add a Data Flow task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="62bec-104">控制流的第二个任务是确保所选间隔的变更数据已准备就绪。</span><span class="sxs-lookup"><span data-stu-id="62bec-104">The second task for the control flow is to ensure that the change data for the selected interval is ready.</span></span> <span data-ttu-id="62bec-105">有关此任务的详细信息，请参阅 [确定变更数据是否已准备就绪](determine-whether-the-change-data-is-ready.md)。</span><span class="sxs-lookup"><span data-stu-id="62bec-105">For more information about this task, see [Determine Whether the Change Data Is Ready](determine-whether-the-change-data-is-ready.md).</span></span> <span data-ttu-id="62bec-106">有关设计控制流的总体过程的说明，请参阅[变更数据捕获 (SSIS)](change-data-capture-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="62bec-106">For a description of the overall process of designing the control flow, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="design-considerations"></a><span data-ttu-id="62bec-107">设计注意事项</span><span class="sxs-lookup"><span data-stu-id="62bec-107">Design Considerations</span></span>  
 <span data-ttu-id="62bec-108">为了检索变更数据，您将调用 Transact-SQL 表值函数，该函数将间隔的端点接受为输入参数并返回指定间隔的变更数据。</span><span class="sxs-lookup"><span data-stu-id="62bec-108">To retrieve the change data, you will call a Transact-SQL table-valued function that accepts the endpoints of the interval as input parameters and returns change data for the specified interval.</span></span> <span data-ttu-id="62bec-109">数据流中的源组件调用此函数。</span><span class="sxs-lookup"><span data-stu-id="62bec-109">A source component in the data flow calls this function.</span></span> <span data-ttu-id="62bec-110">有关此源组件的信息，请参阅 [检索和了解变更数据](retrieve-and-understand-the-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="62bec-110">For information about this source component, see [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md).</span></span>  
  
 <span data-ttu-id="62bec-111">最常用的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 源组件（包括 OLE DB 源、ADO 源和 ADO NET 源）无法为表值函数派生参数信息。</span><span class="sxs-lookup"><span data-stu-id="62bec-111">The most frequently used [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source components, including the OLE DB source, the ADO source, and the ADO NET source, cannot derive parameter information for a table-valued function.</span></span> <span data-ttu-id="62bec-112">因此，大多数源不能直接调用参数化的函数。</span><span class="sxs-lookup"><span data-stu-id="62bec-112">Therefore, most sources cannot call a parameterized function directly.</span></span>  
  
 <span data-ttu-id="62bec-113">您可以使用以下两个设计选项将输入参数传递到函数：</span><span class="sxs-lookup"><span data-stu-id="62bec-113">You have two design options for passing the input parameters to the function:</span></span>  
  
-   <span data-ttu-id="62bec-114">**将参数化查询组合为字符串**。</span><span class="sxs-lookup"><span data-stu-id="62bec-114">**Assemble the parameterized query as a string**.</span></span> <span data-ttu-id="62bec-115">可以使用脚本任务或执行 SQL 任务将动态的 SQL 字符串与硬编码的参数值组合为字符串。</span><span class="sxs-lookup"><span data-stu-id="62bec-115">You can use a Script task or an Execute SQL task to assemble a dynamic SQL string with parameter values hard-coded into the string.</span></span> <span data-ttu-id="62bec-116">然后，将该字符串存储在包变量中，并用它来设置源组件的 SqlCommand 属性。</span><span class="sxs-lookup"><span data-stu-id="62bec-116">Then, you can store this string in a package variable and use it to set the SqlCommand property of a source component.</span></span> <span data-ttu-id="62bec-117">此方法之所以成功，是因为源组件不再需要参数信息。</span><span class="sxs-lookup"><span data-stu-id="62bec-117">This approach succeeds because the source component no longer requires parameter information.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="62bec-118">预编译的脚本产生的开销小于执行 SQL 任务。</span><span class="sxs-lookup"><span data-stu-id="62bec-118">A precompiled script incurs less overhead than an Execute SQL task.</span></span>  
  
-   <span data-ttu-id="62bec-119">**使用参数化的包装**。</span><span class="sxs-lookup"><span data-stu-id="62bec-119">**Use a parameterized wrapper**.</span></span> <span data-ttu-id="62bec-120">此外，还可以以包装的形式创建一个参数化的存储过程，以调用参数化的表值函数。</span><span class="sxs-lookup"><span data-stu-id="62bec-120">Alternatively, you can create a parameterized stored procedure as a wrapper that calls the parameterized table-valued function.</span></span> <span data-ttu-id="62bec-121">此方法之所以成功，是因为源组件可以成功地为存储过程派生参数信息。</span><span class="sxs-lookup"><span data-stu-id="62bec-121">This approach succeeds because a source component can successfully derive parameter information for a stored procedure.</span></span>  
  
 <span data-ttu-id="62bec-122">本主题使用第一个设计选项，即将参数化查询组合为字符串。</span><span class="sxs-lookup"><span data-stu-id="62bec-122">This topic uses the first design option and assembles a parameterized query as a string.</span></span>  
  
## <a name="preparing-the-query"></a><span data-ttu-id="62bec-123">准备查询</span><span class="sxs-lookup"><span data-stu-id="62bec-123">Preparing the Query</span></span>  
 <span data-ttu-id="62bec-124">将输入参数的值连接到单个查询字符串中之前，必须设置查询所需的包变量。</span><span class="sxs-lookup"><span data-stu-id="62bec-124">Before you can concatenate the values of the input parameters into a single query string, you have to set up the package variables that the query needs.</span></span>  
  
#### <a name="to-set-up-package-variables"></a><span data-ttu-id="62bec-125">设置包变量</span><span class="sxs-lookup"><span data-stu-id="62bec-125">To set up package variables</span></span>  
  
-   <span data-ttu-id="62bec-126">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的 **“变量”** 窗口中，创建一个数据类型为 string 的变量以保存执行 SQL 任务返回的查询字符串。</span><span class="sxs-lookup"><span data-stu-id="62bec-126">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in the **Variables** window, create a variable with a string data type to hold the query string returned by the Execute SQL Task.</span></span>  
  
     <span data-ttu-id="62bec-127">以下示例使用变量名 SqlDataQuery。</span><span class="sxs-lookup"><span data-stu-id="62bec-127">This example uses the variable name, SqlDataQuery.</span></span>  
  
 <span data-ttu-id="62bec-128">创建包变量后，可以使用脚本任务或执行 SQL 任务连接输入参数的值。</span><span class="sxs-lookup"><span data-stu-id="62bec-128">With the package variable created, you can use either a Script task or Execute SQL task to concatenate the values of the input parameters.</span></span> <span data-ttu-id="62bec-129">下面的两个过程介绍如何配置这些组件。</span><span class="sxs-lookup"><span data-stu-id="62bec-129">The following two procedures describe how to configure these components.</span></span>  
  
#### <a name="to-use-a-script-task-to-concatenate-the-query-string"></a><span data-ttu-id="62bec-130">使用脚本任务连接查询字符串</span><span class="sxs-lookup"><span data-stu-id="62bec-130">To use a Script task to concatenate the query string</span></span>  
  
1.  <span data-ttu-id="62bec-131">在 **“控制流”** 选项卡上，在包中的 For 循环容器后添加一个脚本任务，然后将 For 循环容器连接到该任务。</span><span class="sxs-lookup"><span data-stu-id="62bec-131">On the **Control Flow** tab, add a Script task to the package after the For Loop container and connect the For Loop container to the task.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="62bec-132">此过程假定包从一个表中执行增量加载。</span><span class="sxs-lookup"><span data-stu-id="62bec-132">This procedure assumes that the package performs an incremental load from a single table.</span></span> <span data-ttu-id="62bec-133">如果包从多个表加载并且具有包含多个子包的父包，则将该任务作为第一个组件添加到各子包中。</span><span class="sxs-lookup"><span data-stu-id="62bec-133">If the package loads from multiple tables and has a parent package with multiple child packages, this task would be added as the first component to each child package.</span></span> <span data-ttu-id="62bec-134">有关详细信息，请参阅 [执行多个表的增量加载](perform-an-incremental-load-of-multiple-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="62bec-134">For more information, see [Perform an Incremental Load of Multiple Tables](perform-an-incremental-load-of-multiple-tables.md).</span></span>  
  
2.  <span data-ttu-id="62bec-135">在 **“脚本任务编辑器”** 中的 **“脚本”** 页上，选择以下选项：</span><span class="sxs-lookup"><span data-stu-id="62bec-135">In the **Script Task Editor**, on the **Script** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="62bec-136">对于 **ReadOnlyVariables**，从列表中选择 **User::DataReady**、 **User::ExtractStartTime**和 **User::ExtractEndTime** 。</span><span class="sxs-lookup"><span data-stu-id="62bec-136">For **ReadOnlyVariables**, select **User::DataReady**, **User::ExtractStartTime**, and **User::ExtractEndTime** from the.</span></span>  
  
    2.  <span data-ttu-id="62bec-137">对于 **ReadWriteVariables**，从列表中选择 User::SqlDataQuery。</span><span class="sxs-lookup"><span data-stu-id="62bec-137">For **ReadWriteVariables**, select User::SqlDataQuery from the list.</span></span>  
  
3.  <span data-ttu-id="62bec-138">在 **“脚本任务编辑器”** 的 **“脚本”** 页上，单击 **“编辑脚本”** 以打开脚本开发环境。</span><span class="sxs-lookup"><span data-stu-id="62bec-138">In the **Script Task Editor**, on the **Script** page, click **Edit Script** to open the script development environment.</span></span>  
  
4.  <span data-ttu-id="62bec-139">在 Main 过程中，输入下面的代码段之一：</span><span class="sxs-lookup"><span data-stu-id="62bec-139">In the Main procedure, enter one of the following code segments:</span></span>  
  
    -   <span data-ttu-id="62bec-140">如果使用 C# 进行编程，请输入下面的代码行：</span><span class="sxs-lookup"><span data-stu-id="62bec-140">If you are programming in C#, enter the following lines of code:</span></span>  
  
        ```  
        int dataReady;  
        System.DateTime extractStartTime;  
        System.DateTime extractEndTime;  
        string sqlDataQuery;  
  
        dataReady = (int)Dts.Variables["DataReady"].Value;  
        extractStartTime = (System.DateTime)Dts.Variables["ExtractStartTime"].Value;  
        extractEndTime = (System.DateTime)Dts.Variables["ExtractEndTime"].Value;  
  
        if (dataReady == 2)  
          {  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer('" + string.Format("{0:yyyy-MM-dd hh:mm:ss}", extractStartTime) + "', '" + string.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) + "')";  
          }  
        else  
          {  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer(null" + ", '" + string.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) + "')";  
          }  
  
        Dts.Variables["SqlDataQuery"].Value = sqlDataQuery;  
        ```  
  
         <span data-ttu-id="62bec-141">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="62bec-141">\- or -</span></span>  
  
    -   <span data-ttu-id="62bec-142">如果您是使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]进行编程，请输入下面的代码行：</span><span class="sxs-lookup"><span data-stu-id="62bec-142">If you are programming in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], enter the following lines of code:</span></span>  
  
        ```  
        Dim dataReady As Integer  
        Dim extractStartTime As Date  
        Dim extractEndTime As Date  
        Dim sqlDataQuery As String  
  
        dataReady = CType(Dts.Variables("DataReady").Value, Integer)  
        extractStartTime = CType(Dts.Variables("ExtractStartTime").Value, Date)  
        extractEndTime = CType(Dts.Variables("ExtractEndTime").Value, Date)  
  
        If dataReady = 2 Then  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer('" & _  
              String.Format("{0:yyyy-MM-dd hh:mm:ss}", extractStartTime) & _  
              "', '" & _  
              String.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) & _  
              "')"  
        Else  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer(null" & _  
              ", '" & _  
              String.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) & _  
              "')"  
        End If  
  
        Dts.Variables("SqlDataQuery").Value = sqlDataQuery  
  
        ```  
  
5.  <span data-ttu-id="62bec-143">保留从脚本执行过程返回 `DtsExecResult.Success` 的默认代码行。</span><span class="sxs-lookup"><span data-stu-id="62bec-143">Leave the default line of code which returns `DtsExecResult.Success` from the execution of the script.</span></span>  
  
6.  <span data-ttu-id="62bec-144">关闭脚本开发环境和 **“脚本任务编辑器”** 。</span><span class="sxs-lookup"><span data-stu-id="62bec-144">Close the script development environment and the **Script Task Editor**.</span></span>  
  
#### <a name="to-use-an-execute-sql-task-to-concatenate-the-query-string"></a><span data-ttu-id="62bec-145">使用执行 SQL 任务连接查询字符串</span><span class="sxs-lookup"><span data-stu-id="62bec-145">To use an Execute SQL task to concatenate the query string</span></span>  
  
1.  <span data-ttu-id="62bec-146">在 **“控制流”** 选项卡上，在 For 循环容器之后向包添加一个执行 SQL 任务，然后将 For 循环容器连接到该任务。</span><span class="sxs-lookup"><span data-stu-id="62bec-146">On the **Control Flow** tab, add an Execute SQL task to the package after the For Loop container and connect the For Loop container to this task.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="62bec-147">此过程假定包从一个表中执行增量加载。</span><span class="sxs-lookup"><span data-stu-id="62bec-147">This procedure assumes that the package performs an incremental load from a single table.</span></span> <span data-ttu-id="62bec-148">如果包从多个表加载并且具有包含多个子包的父包，则将该任务作为第一个组件添加到各子包中。</span><span class="sxs-lookup"><span data-stu-id="62bec-148">If the package loads from multiple tables and has a parent package with multiple child packages, this task would be added as the first component to each child package.</span></span> <span data-ttu-id="62bec-149">有关详细信息，请参阅 [执行多个表的增量加载](perform-an-incremental-load-of-multiple-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="62bec-149">For more information, see [Perform an Incremental Load of Multiple Tables](perform-an-incremental-load-of-multiple-tables.md).</span></span>  
  
2.  <span data-ttu-id="62bec-150">在 **“执行 SQL 任务编辑器”** 中的 **“常规”** 页上，选择以下选项：</span><span class="sxs-lookup"><span data-stu-id="62bec-150">In the **Execute SQL Task Editor**, on the **General** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="62bec-151">对于 **ResultSet**，选择 **“单行”** 。</span><span class="sxs-lookup"><span data-stu-id="62bec-151">For **ResultSet**, select **Single row**.</span></span>  
  
    2.  <span data-ttu-id="62bec-152">配置到源数据库的有效连接。</span><span class="sxs-lookup"><span data-stu-id="62bec-152">Configure a valid connection to the source database.</span></span>  
  
    3.  <span data-ttu-id="62bec-153">对于 **SQLSourceType**，选择 **“直接输入”** 。</span><span class="sxs-lookup"><span data-stu-id="62bec-153">For **SQLSourceType**, select **Direct input**.</span></span>  
  
    4.  <span data-ttu-id="62bec-154">对于 **SQLStatement**，输入以下 SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="62bec-154">For **SQLStatement**, enter the following SQL statement:</span></span>  
  
        ```  
        declare @ExtractStartTime datetime,  
        @ExtractEndTime datetime,   
        @DataReady int  
  
        select @DataReady = ?,   
        @ExtractStartTime = ?,   
        @ExtractEndTime = ?  
  
        if @DataReady = 2  
        select N'select * from CDCSample.uf_Customer'  
        + N'('''+ convert(nvarchar(30),@ExtractStartTime,120)  
        + ''', '''  
        + convert(nvarchar(30),@ExtractEndTime,120) + ''') '   
        as SqlDataQuery  
        else  
        select N'select * from CDCSample.uf_Customer'  
        + N'(null, '''  
        + convert(nvarchar(30),@ExtractEndTime,120)  
        + ''') '  
        as SqlDataQuery  
  
        ```  
  
        > [!NOTE]  
        >  <span data-ttu-id="62bec-155">上述示例中的 `else` 子句通过为开始日期和时间传递 null 值来生成查询，用于变更数据的首次加载。</span><span class="sxs-lookup"><span data-stu-id="62bec-155">The `else` clause in this sample generates a query for the initial load of change data by passing a null value for the starting date and time.</span></span> <span data-ttu-id="62bec-156">此示例没有涉及到一种情况：必须将启用变更数据捕获功能之前所做的变更上传到数据仓库。</span><span class="sxs-lookup"><span data-stu-id="62bec-156">This sample does not address the scenario in which changes that were made before change data capture was enabled also have to be uploaded to the data warehouse.</span></span>  
  
3.  <span data-ttu-id="62bec-157">在 **“执行 SQL 任务编辑器”** 的 **“参数映射”** 页上，进行以下映射：</span><span class="sxs-lookup"><span data-stu-id="62bec-157">On the **Parameter Mapping** page of the **Execute SQL Task Editor**, do the following mapping:</span></span>  
  
    1.  <span data-ttu-id="62bec-158">将 DataReady 变量映射到参数 0。</span><span class="sxs-lookup"><span data-stu-id="62bec-158">Map the DataReady variable to parameter 0.</span></span>  
  
    2.  <span data-ttu-id="62bec-159">将 ExtractStartTime 变量映射到参数 1。</span><span class="sxs-lookup"><span data-stu-id="62bec-159">Map the ExtractStartTime variable to parameter 1.</span></span>  
  
    3.  <span data-ttu-id="62bec-160">将 ExtractEndTime 变量映射到参数 2。</span><span class="sxs-lookup"><span data-stu-id="62bec-160">Map the ExtractEndTime variable to parameter 2.</span></span>  
  
4.  <span data-ttu-id="62bec-161">在 **“执行 SQL 任务编辑器”** 的 **“结果集”** 页上，将结果名称映射到 SqlDataQuery 变量。</span><span class="sxs-lookup"><span data-stu-id="62bec-161">On the **Result Set** page of the **Execute SQL Task Editor**, map the Result Name to the SqlDataQuery variable.</span></span>  
  
     <span data-ttu-id="62bec-162">该结果名称是返回的单列的名称 SqlDataQuery。</span><span class="sxs-lookup"><span data-stu-id="62bec-162">The Result Name is the name of the single column that is returned, SqlDataQuery.</span></span>  
  
 <span data-ttu-id="62bec-163">上述过程配置的任务使用输入参数的硬编码字符串值准备查询字符串。</span><span class="sxs-lookup"><span data-stu-id="62bec-163">The previous procedures configure a task that prepares a query string with hard-coded string values for the input parameters.</span></span> <span data-ttu-id="62bec-164">下面的代码是此查询字符串的示例：</span><span class="sxs-lookup"><span data-stu-id="62bec-164">The following code is an example of such a query string:</span></span>  
  
 `select * from CDCSample. uf_Customer('2007-06-11 14:21:58', '2007-06-12 14:21:58')`  
  
## <a name="adding-a-data-flow-task"></a><span data-ttu-id="62bec-165">添加数据流任务</span><span class="sxs-lookup"><span data-stu-id="62bec-165">Adding a Data Flow Task</span></span>  
 <span data-ttu-id="62bec-166">设计包的控制流的最后一步是添加数据流任务。</span><span class="sxs-lookup"><span data-stu-id="62bec-166">The last step in designing the control flow for the package is to add a Data Flow task.</span></span>  
  
#### <a name="to-add-a-data-flow-task-and-complete-the-control-flow"></a><span data-ttu-id="62bec-167">添加数据流任务和完成控制流</span><span class="sxs-lookup"><span data-stu-id="62bec-167">To add a Data Flow task and complete the control flow</span></span>  
  
-   <span data-ttu-id="62bec-168">在 **“控制流”** 选项卡上，添加一个数据流任务，并连接用于连接查询字符串的任务。</span><span class="sxs-lookup"><span data-stu-id="62bec-168">On the **Control Flow** tab, add a Data Flow task and connect the task that concatenated the query string.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="62bec-169">下一步</span><span class="sxs-lookup"><span data-stu-id="62bec-169">Next Step</span></span>  
 <span data-ttu-id="62bec-170">在准备查询字符串和配置数据流任务之后，下一步就是创建用于从数据库检索变更数据的表值函数。</span><span class="sxs-lookup"><span data-stu-id="62bec-170">After you prepare the query string and configure the Data Flow task, the next step is create the table-valued function that will retrieve the change data from the database.</span></span>  
  
 <span data-ttu-id="62bec-171">**下一个主题：** [创建函数以检索变更数据](create-the-function-to-retrieve-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="62bec-171">**Next topic:** [Create the Function to Retrieve the Change Data](create-the-function-to-retrieve-the-change-data.md)</span></span>  
  
  
