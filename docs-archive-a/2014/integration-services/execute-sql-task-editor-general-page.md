---
title: " (\"常规\" 页上执行 SQL 任务编辑器) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.general.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: beb39086-28ce-46af-b6d8-f7b4fb8d9069
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 32bec035646c976442eb66ff1270b961835b243b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578957"
---
# <a name="execute-sql-task-editor-general-page"></a><span data-ttu-id="3bfb8-102">执行 SQL 任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="3bfb8-102">Execute SQL Task Editor (General Page)</span></span>
  <span data-ttu-id="3bfb8-103">可以使用 **“执行 SQL 任务编辑器”** 对话框的 **“常规”** 页，配置执行 SQL 任务以及提供任务运行的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-103">Use the **General** page of the **Execute SQL Task Editor** dialog box to configure the Execute SQL task and provide the SQL statement that the task runs.</span></span>  
  
 <span data-ttu-id="3bfb8-104">若要了解有关此任务的信息，请参阅[执行 SQL 任务](control-flow/execute-sql-task.md)、[执行 SQL 任务中的参数和返回代码](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)和[执行 SQL 任务中的结果集](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-104">To learn about this task, see [Execute SQL Task](control-flow/execute-sql-task.md), [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md), and [Result Sets in the Execute SQL Task](../../2014/integration-services/result-sets-in-the-execute-sql-task.md).</span></span> <span data-ttu-id="3bfb8-105">若要了解关于 Transact-SQL 查询语言的详细信息，请参阅 [Transact-SQL 引用（数据库引擎）](/sql/t-sql/language-reference)。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-105">To learn more about the Transact-SQL query language, see [Transact-SQL Reference &#40;Database Engine&#41;](/sql/t-sql/language-reference).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="3bfb8-106">静态选项</span><span class="sxs-lookup"><span data-stu-id="3bfb8-106">Static Options</span></span>  
 <span data-ttu-id="3bfb8-107">**名称**</span><span class="sxs-lookup"><span data-stu-id="3bfb8-107">**Name**</span></span>  
 <span data-ttu-id="3bfb8-108">为工作流中的执行 SQL 任务提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-108">Provide a unique name for the Execute SQL task in the workflow.</span></span> <span data-ttu-id="3bfb8-109">所提供的名称将在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中显示。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-109">The name that is provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="3bfb8-110">**说明**</span><span class="sxs-lookup"><span data-stu-id="3bfb8-110">**Description**</span></span>  
 <span data-ttu-id="3bfb8-111">描述执行 SQL 任务。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-111">Describe the Execute SQL task.</span></span> <span data-ttu-id="3bfb8-112">最好按照任务的用途对其进行说明，使其一目了然，便于维护。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-112">As a best practice, to make packages self-documenting and easier to maintain, describe the task in terms of its purpose.</span></span>  
  
 <span data-ttu-id="3bfb8-113">**TimeOut**</span><span class="sxs-lookup"><span data-stu-id="3bfb8-113">**TimeOut**</span></span>  
 <span data-ttu-id="3bfb8-114">指定任务超时之前运行的最大秒数。如果值为 0，则表示不限制时间。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-114">Specify the maximum number of seconds the task will run before timing out. A value of 0 indicates an infinite time.</span></span> <span data-ttu-id="3bfb8-115">默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-115">The default is 0.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3bfb8-116">如果存储过程通过为要建立的连接和要完成的事务提供比 **TimeOut**指定秒数更长的时间来模拟睡眠功能，则将不会超时。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-116">Stored procedures do not time out if they emulate sleep functionality by providing time for connections to be made and transactions to complete that is greater than the number of seconds specified by **TimeOut**.</span></span> <span data-ttu-id="3bfb8-117">但是，执行查询的存储过程始终受 **TimeOut**指定时间的限制。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-117">However, stored procedures that execute queries are always subject to the time restriction specified by **TimeOut**.</span></span>  
  
 <span data-ttu-id="3bfb8-118">**CodePage**</span><span class="sxs-lookup"><span data-stu-id="3bfb8-118">**CodePage**</span></span>  
 <span data-ttu-id="3bfb8-119">指定在转换变量中的 Unicode 值时要使用的代码页。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-119">Specify the code page to use when translating Unicode values in variables.</span></span> <span data-ttu-id="3bfb8-120">默认值为本地计算机的代码页。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-120">The default value is the code page of the local computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3bfb8-121">当执行 SQL 任务使用 ADO 或 ODBC 连接管理器时， **CodePage** 属性不可用。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-121">When the Execute SQL task uses an ADO or ODBC connection manager, the **CodePage** property is not available.</span></span> <span data-ttu-id="3bfb8-122">如果解决方案需要使用代码页，请将 OLE DB 或 ADO.NET 连接管理器与执行 SQL 任务一起使用。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-122">If your solution requires the use of a code page, use an OLE DB or an ADO.NET connection manager with the Execute SQL task.</span></span>  
  
 <span data-ttu-id="3bfb8-123">**TypeConversionMode**</span><span class="sxs-lookup"><span data-stu-id="3bfb8-123">**TypeConversionMode**</span></span>  
 <span data-ttu-id="3bfb8-124">在您将此属性设置为 `Allowed` 时，“执行 SQL 任务”将尝试将输出参数和查询结果转换为结果赋值给的变量的数据类型。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-124">When you set this property to `Allowed`, the Execute SQL Task will attempt to convert output parameter and query results to the data type of the variable the results are assigned to.</span></span> <span data-ttu-id="3bfb8-125">这适用于 **单行** 结果集类型。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-125">This applies to the **Single row** result set type.</span></span>  
  
 <span data-ttu-id="3bfb8-126">**ResultSet**</span><span class="sxs-lookup"><span data-stu-id="3bfb8-126">**ResultSet**</span></span>  
 <span data-ttu-id="3bfb8-127">指定运行 SQL 语句预期的结果类型。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-127">Specify the result type expected by the SQL statement being run.</span></span> <span data-ttu-id="3bfb8-128">从 **“单行”** 、 **“完整结果集”** 、 **XML**或 **“无”** 中选择。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-128">Choose among **Single row**, **Full result set**, **XML**, or **None**.</span></span>  
  
 <span data-ttu-id="3bfb8-129">**ConnectionType**</span><span class="sxs-lookup"><span data-stu-id="3bfb8-129">**ConnectionType**</span></span>  
 <span data-ttu-id="3bfb8-130">选择连接数据源要使用的连接管理器的类型。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-130">Choose the type of connection manager to use to connect to the data source.</span></span> <span data-ttu-id="3bfb8-131">可用的连接类型包括 **OLE DB**、 **ODBC**、 **ADO**、 **ADO.NET** 和 **SQLMOBILE**。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-131">Available connection types include **OLE DB**, **ODBC**, **ADO**, **ADO.NET** and **SQLMOBILE**.</span></span>  
  
 <span data-ttu-id="3bfb8-132">**相关主题：** [OLE DB 连接管理器](connection-manager/ole-db-connection-manager.md)、[ODBC 连接管理器](connection-manager/odbc-connection-manager.md)、[ADO 连接管理器](connection-manager/ado-connection-manager.md)、[ADO.NET 连接管理器](connection-manager/ado-net-connection-manager.md)、[SQL Server Compact Edition 连接管理器](connection-manager/sql-server-compact-edition-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="3bfb8-132">**Related Topics:** [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md), [ODBC Connection Manager](connection-manager/odbc-connection-manager.md), [ADO Connection Manager](connection-manager/ado-connection-manager.md), [ADO.NET Connection Manager](connection-manager/ado-net-connection-manager.md), [SQL Server Compact Edition Connection Manager](connection-manager/sql-server-compact-edition-connection-manager.md)</span></span>  
  
 <span data-ttu-id="3bfb8-133">**Connection**</span><span class="sxs-lookup"><span data-stu-id="3bfb8-133">**Connection**</span></span>  
 <span data-ttu-id="3bfb8-134">从已定义的连接管理器的列表中选择连接。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-134">Choose the connection from a list of defined connection managers.</span></span> <span data-ttu-id="3bfb8-135">若要创建新的连接，请选择“\<**New connection...**>”。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-135">To create a new connection, select \<**New connection...**>.</span></span>  
  
 <span data-ttu-id="3bfb8-136">**SQLSourceType**</span><span class="sxs-lookup"><span data-stu-id="3bfb8-136">**SQLSourceType**</span></span>  
 <span data-ttu-id="3bfb8-137">选择任务运行的 SQL 语句的源类型。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-137">Select the source type of the SQL statement that the task runs.</span></span>  
  
 <span data-ttu-id="3bfb8-138">根据执行 SQL 任务所用的连接管理器类型，必须在参数化 SQL 语句中使用特定的参数标记。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-138">Depending on the connection manager type that Execute SQL task uses, you must use specific parameter markers in parameterized SQL statements.</span></span>  
  
 <span data-ttu-id="3bfb8-139">**相关主题：**[执行 SQL 任务](control-flow/execute-sql-task.md)中的“运行参数化 SQL 命令”部分</span><span class="sxs-lookup"><span data-stu-id="3bfb8-139">**Related Topics:** Running Parameterized SQL Commands section in [Execute SQL Task](control-flow/execute-sql-task.md)</span></span>  
  
 <span data-ttu-id="3bfb8-140">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-140">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="3bfb8-141">值</span><span class="sxs-lookup"><span data-stu-id="3bfb8-141">Value</span></span>|<span data-ttu-id="3bfb8-142">说明</span><span class="sxs-lookup"><span data-stu-id="3bfb8-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3bfb8-143">**直接输入**</span><span class="sxs-lookup"><span data-stu-id="3bfb8-143">**Direct input**</span></span>|<span data-ttu-id="3bfb8-144">将源设置为某个 Transact-SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-144">Set the source to a Transact-SQL statement.</span></span> <span data-ttu-id="3bfb8-145">选择此值将显示动态选项 **SQLStatement**。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-145">Selecting this value displays the dynamic option, **SQLStatement**.</span></span>|  
|<span data-ttu-id="3bfb8-146">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="3bfb8-146">**File connection**</span></span>|<span data-ttu-id="3bfb8-147">选择包含 Transact-SQL 语句的文件。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-147">Select a file that contains a Transact-SQL statement.</span></span> <span data-ttu-id="3bfb8-148">设置此选项将显示动态选项 **FileConnection**。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-148">Setting this option displays the dynamic option, **FileConnection**.</span></span>|  
|<span data-ttu-id="3bfb8-149">**变量**</span><span class="sxs-lookup"><span data-stu-id="3bfb8-149">**Variable**</span></span>|<span data-ttu-id="3bfb8-150">将源设置为定义 Transact-SQL 语句的变量。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-150">Set the source to a variable that defines the Transact-SQL statement.</span></span> <span data-ttu-id="3bfb8-151">选择此值将显示动态选项 **SourceVariable**。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-151">Selecting this value displays the dynamic option, **SourceVariable**.</span></span>|  
  
 <span data-ttu-id="3bfb8-152">**QueryIsStoredProcedure**</span><span class="sxs-lookup"><span data-stu-id="3bfb8-152">**QueryIsStoredProcedure**</span></span>  
 <span data-ttu-id="3bfb8-153">指示要运行的指定 SQL 语句是否为存储过程。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-153">Indicates whether the specified SQL statement to be run is a stored procedure.</span></span> <span data-ttu-id="3bfb8-154">只有当任务使用 ADO 连接管理器时，此属性才是可读/写的。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-154">This property is read/write only if the task uses the ADO connection manager.</span></span> <span data-ttu-id="3bfb8-155">否则该属性为只读，其值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-155">Otherwise the property is read-only and its value is `false`.</span></span>  
  
 <span data-ttu-id="3bfb8-156">**BypassPrepare**</span><span class="sxs-lookup"><span data-stu-id="3bfb8-156">**BypassPrepare**</span></span>  
 <span data-ttu-id="3bfb8-157">指示 SQL 语句是否已准备就绪。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-157">Indicate whether the SQL statement is prepared.</span></span>  <span data-ttu-id="3bfb8-158">如果为 `true`，则跳过准备过程；如果为 `false`，则在运行 SQL 语句前准备 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-158">`true` skips preparation; `false` prepares the SQL statement before running it.</span></span> <span data-ttu-id="3bfb8-159">此选项仅可用于支持准备的 OLE DB 连接。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-159">This option is available only with OLE DB connections that support preparation.</span></span>  
  
 <span data-ttu-id="3bfb8-160">**相关主题：** [准备好的执行](../relational-databases/native-client-odbc-queries/executing-statements/prepared-execution.md)</span><span class="sxs-lookup"><span data-stu-id="3bfb8-160">**Related Topics:**  [Prepared Execution](../relational-databases/native-client-odbc-queries/executing-statements/prepared-execution.md)</span></span>  
  
 <span data-ttu-id="3bfb8-161">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="3bfb8-161">**Browse**</span></span>  
 <span data-ttu-id="3bfb8-162">使用“打开”  对话框定位包含 SQL 语句的文件。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-162">Locate a file that contains a SQL statement by using the **Open** dialog box.</span></span> <span data-ttu-id="3bfb8-163">选择一个文件，将文件内容作为 SQL 语句复制到 **SQLStatement** 属性中。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-163">Select a file to copy the contents of the file as a SQL statement into the **SQLStatement** property.</span></span>  
  
 <span data-ttu-id="3bfb8-164">**生成查询**</span><span class="sxs-lookup"><span data-stu-id="3bfb8-164">**Build Query**</span></span>  
 <span data-ttu-id="3bfb8-165">使用“查询生成器”  对话框创建 SQL 语句，查询生成器是一种用于创建查询的图形工具。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-165">Create an SQL statement using the **Query Builder** dialog box, a graphical tool used to create queries.</span></span> <span data-ttu-id="3bfb8-166">此选项在 **SQLSourceType** 选项设置为 **“直接输入”** 时可用。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-166">This option is available when the **SQLSourceType** option is set to **Direct input**.</span></span>  
  
 <span data-ttu-id="3bfb8-167">**分析查询**</span><span class="sxs-lookup"><span data-stu-id="3bfb8-167">**Parse Query**</span></span>  
 <span data-ttu-id="3bfb8-168">验证 SQL 语句的语法。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-168">Validate the syntax of the SQL statement.</span></span>  
  
## <a name="sqlsourcetype-dynamic-options"></a><span data-ttu-id="3bfb8-169">SQLSourceType 动态选项</span><span class="sxs-lookup"><span data-stu-id="3bfb8-169">SQLSourceType Dynamic Options</span></span>  
  
### <a name="sqlsourcetype--direct-input"></a><span data-ttu-id="3bfb8-170">SQLSourceType = 直接输入</span><span class="sxs-lookup"><span data-stu-id="3bfb8-170">SQLSourceType = Direct input</span></span>  
 <span data-ttu-id="3bfb8-171">**SQLStatement**</span><span class="sxs-lookup"><span data-stu-id="3bfb8-171">**SQLStatement**</span></span>  
 <span data-ttu-id="3bfb8-172">在选项框中键入要执行的 SQL 语句，或者单击浏览按钮 (…)，在“输入 SQL 查询”对话框中键入 SQL 语句，还可以单击“生成查询”，使用“查询生成器”对话框编写 SQL 语句    。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-172">Type the SQL statement to execute in the option box, or click the browse button (...) to type the SQL statement in the **Enter SQL Query** dialog box, or click **Build Query** to compose the statement using the **Query Builder** dialog box.</span></span>  
  
 <span data-ttu-id="3bfb8-173">**相关主题：** [查询生成器](../../2014/integration-services/query-builder.md)</span><span class="sxs-lookup"><span data-stu-id="3bfb8-173">**Related Topics:** [Query Builder](../../2014/integration-services/query-builder.md)</span></span>  
  
### <a name="sqlsourcetype--file-connection"></a><span data-ttu-id="3bfb8-174">SQLSourceType = 文件连接</span><span class="sxs-lookup"><span data-stu-id="3bfb8-174">SQLSourceType = File connection</span></span>  
 <span data-ttu-id="3bfb8-175">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="3bfb8-175">**FileConnection**</span></span>  
 <span data-ttu-id="3bfb8-176">选择现有“文件连接管理器”，或单击 \<**New connection...**> 以创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-176">Select an existing File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="3bfb8-177">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="3bfb8-177">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="sqlsourcetype--variable"></a><span data-ttu-id="3bfb8-178">SQLSourceType = 变量</span><span class="sxs-lookup"><span data-stu-id="3bfb8-178">SQLSourceType = Variable</span></span>  
 <span data-ttu-id="3bfb8-179">**SourceVariable**</span><span class="sxs-lookup"><span data-stu-id="3bfb8-179">**SourceVariable**</span></span>  
 <span data-ttu-id="3bfb8-180">选择现有变量或单击 \<**New variable...**> 以创建新变量。</span><span class="sxs-lookup"><span data-stu-id="3bfb8-180">Select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="3bfb8-181">**相关主题：** [Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="3bfb8-181">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bfb8-182">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3bfb8-182">See Also</span></span>  
 <span data-ttu-id="3bfb8-183">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3bfb8-183">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="3bfb8-184">[执行 SQL 任务编辑器 &#40;参数映射页&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md) </span><span class="sxs-lookup"><span data-stu-id="3bfb8-184">[Execute SQL Task Editor &#40;Parameter Mapping Page&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md) </span></span>  
 [<span data-ttu-id="3bfb8-185">&#40;"结果集" 页上执行 SQL 任务编辑器&#41;</span><span class="sxs-lookup"><span data-stu-id="3bfb8-185">Execute SQL Task Editor &#40;Result Set Page&#41;</span></span>](../../2014/integration-services/execute-sql-task-editor-result-set-page.md)  
  
  
