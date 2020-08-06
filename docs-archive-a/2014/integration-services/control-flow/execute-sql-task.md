---
title: 执行 SQL 任务 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.f1
helpviewer_keywords:
- Transact-SQL statements, SSIS
- statements [Integration Services]
- batches [Integration Services]
- Execute SQL task [Integration Services]
ms.assetid: bebb2e8c-0410-43b2-ac2f-6fc80c8f2e9e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e77b9f442ae8478c57d5b0e68955b541eda38aff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688111"
---
# <a name="execute-sql-task"></a><span data-ttu-id="170da-102">执行 SQL 任务</span><span class="sxs-lookup"><span data-stu-id="170da-102">Execute SQL Task</span></span>
  <span data-ttu-id="170da-103">执行 SQL 任务从包中运行 SQL 语句或存储过程。</span><span class="sxs-lookup"><span data-stu-id="170da-103">The Execute SQL task runs SQL statements or stored procedures from a package.</span></span> <span data-ttu-id="170da-104">此任务可以包含单个 SQL 语句，也可以包含按顺序运行的多个 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="170da-104">The task can contain either a single SQL statement or multiple SQL statements that run sequentially.</span></span> <span data-ttu-id="170da-105">可以将执行 SQL 任务用于下列用途：</span><span class="sxs-lookup"><span data-stu-id="170da-105">You can use the Execute SQL task for the following purposes:</span></span>  
  
-   <span data-ttu-id="170da-106">截断表或视图，以便为插入数据作准备。</span><span class="sxs-lookup"><span data-stu-id="170da-106">Truncate a table or view in preparation for inserting data.</span></span>  
  
-   <span data-ttu-id="170da-107">创建、更改和删除数据库对象（如表和视图）。</span><span class="sxs-lookup"><span data-stu-id="170da-107">Create, alter, and drop database objects such as tables and views.</span></span>  
  
-   <span data-ttu-id="170da-108">在向事实数据表和维度表加载数据之前，重新创建这些表。</span><span class="sxs-lookup"><span data-stu-id="170da-108">Re-create fact and dimension tables before loading data into them.</span></span>  
  
-   <span data-ttu-id="170da-109">运行存储过程。</span><span class="sxs-lookup"><span data-stu-id="170da-109">Run stored procedures.</span></span> <span data-ttu-id="170da-110">如果 SQL 语句调用从临时表返回结果的某一存储过程，则使用 WITH RESULT SETS 选项可为结果集定义元数据。</span><span class="sxs-lookup"><span data-stu-id="170da-110">If the SQL statement invokes a stored procedure that returns results from a temporary table, use the WITH RESULT SETS option to define metadata for the result set.</span></span>  
  
-   <span data-ttu-id="170da-111">将查询返回的行集保存到变量中。</span><span class="sxs-lookup"><span data-stu-id="170da-111">Save the rowset returned from a query into a variable.</span></span>  
  
 <span data-ttu-id="170da-112">执行 SQL 任务可以与 Foreach 循环和 For 循环容器一起组合使用，以运行多个 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="170da-112">The Execute SQL task can be used in combination with the Foreach Loop and For Loop containers to run multiple SQL statements.</span></span> <span data-ttu-id="170da-113">这些容器在包中实现重复运行控制流，并可重复运行执行 SQL 任务。</span><span class="sxs-lookup"><span data-stu-id="170da-113">These containers implement repeating control flows in a package and they can run the Execute SQL task repeatedly.</span></span> <span data-ttu-id="170da-114">例如，包可以使用 Foreach 循环容器来枚举文件夹中的文件，并重复运行执行 SQL 任务来执行存储在各个文件中的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="170da-114">For example, using the Foreach Loop container, a package can enumerate files in a folder and run an Execute SQL task repeatedly to execute the SQL statement stored in each file.</span></span>  
  
## <a name="connecting-to-a-data-source"></a><span data-ttu-id="170da-115">连接到数据源</span><span class="sxs-lookup"><span data-stu-id="170da-115">Connecting to a Data Source</span></span>  
 <span data-ttu-id="170da-116">执行 SQL 任务可使用不同类型的连接管理器来连接到在其中运行 SQL 语句或存储过程的数据源。</span><span class="sxs-lookup"><span data-stu-id="170da-116">The Execute SQL task can use different types of connection managers to connect to the data source where it runs the SQL statement or stored procedure.</span></span> <span data-ttu-id="170da-117">此任务可使用下表中列出的连接类型。</span><span class="sxs-lookup"><span data-stu-id="170da-117">The task can use the connection types listed in the following table.</span></span>  
  
|<span data-ttu-id="170da-118">连接类型</span><span class="sxs-lookup"><span data-stu-id="170da-118">Connection type</span></span>|<span data-ttu-id="170da-119">“ODBC 源编辑器”</span><span class="sxs-lookup"><span data-stu-id="170da-119">Connection manager</span></span>|  
|---------------------|------------------------|  
|<span data-ttu-id="170da-120">EXCEL</span><span class="sxs-lookup"><span data-stu-id="170da-120">EXCEL</span></span>|[<span data-ttu-id="170da-121">Excel 连接管理器</span><span class="sxs-lookup"><span data-stu-id="170da-121">Excel Connection Manager</span></span>](../connection-manager/excel-connection-manager.md)|  
|<span data-ttu-id="170da-122">OLE DB</span><span class="sxs-lookup"><span data-stu-id="170da-122">OLE DB</span></span>|[<span data-ttu-id="170da-123">OLE DB 连接管理器</span><span class="sxs-lookup"><span data-stu-id="170da-123">OLE DB Connection Manager</span></span>](../connection-manager/ole-db-connection-manager.md)|  
|<span data-ttu-id="170da-124">ODBC</span><span class="sxs-lookup"><span data-stu-id="170da-124">ODBC</span></span>|[<span data-ttu-id="170da-125">ODBC 连接管理器</span><span class="sxs-lookup"><span data-stu-id="170da-125">ODBC Connection Manager</span></span>](../connection-manager/odbc-connection-manager.md)|  
|<span data-ttu-id="170da-126">ADO</span><span class="sxs-lookup"><span data-stu-id="170da-126">ADO</span></span>|[<span data-ttu-id="170da-127">ADO 连接管理器</span><span class="sxs-lookup"><span data-stu-id="170da-127">ADO Connection Manager</span></span>](../connection-manager/ado-connection-manager.md)|  
|<span data-ttu-id="170da-128">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="170da-128">ADO.NET</span></span>|[<span data-ttu-id="170da-129">ADO.NET 连接管理器</span><span class="sxs-lookup"><span data-stu-id="170da-129">ADO.NET Connection Manager</span></span>](../connection-manager/ado-net-connection-manager.md)|  
|<span data-ttu-id="170da-130">SQLMOBILE</span><span class="sxs-lookup"><span data-stu-id="170da-130">SQLMOBILE</span></span>|[<span data-ttu-id="170da-131">SQL Server Compact Edition 连接管理器</span><span class="sxs-lookup"><span data-stu-id="170da-131">SQL Server Compact Edition Connection Manager</span></span>](../connection-manager/sql-server-compact-edition-connection-manager.md)|  
  
## <a name="creating-sql-statements"></a><span data-ttu-id="170da-132">创建 SQL 语句</span><span class="sxs-lookup"><span data-stu-id="170da-132">Creating SQL Statements</span></span>  
 <span data-ttu-id="170da-133">此任务使用的 SQL 语句的源可以是包含语句的任务属性、到包含一个或多个语句的文件的连接，或者是包含语句的变量的名称。</span><span class="sxs-lookup"><span data-stu-id="170da-133">The source of the SQL statements used by this task can be a task property that contains a statement, a connection to a file that contains one or multiple statements, or the name of a variable that contains a statement.</span></span> <span data-ttu-id="170da-134">必须用源数据库管理系统 (DBMS) 的方言编写 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="170da-134">The SQL statements must be written in the dialect of the source database management system (DBMS).</span></span> <span data-ttu-id="170da-135">有关详细信息，请参阅 [Integration Services (SSIS) 查询](../integration-services-ssis-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="170da-135">For more information, see [Integration Services &#40;SSIS&#41; Queries](../integration-services-ssis-queries.md).</span></span>  
  
 <span data-ttu-id="170da-136">如果 SQL 语句存储在某个文件中，则该任务使用文件连接管理器来连接到该文件。</span><span class="sxs-lookup"><span data-stu-id="170da-136">If the SQL statements are stored in a file, the task uses a File connection manager to connect to the file.</span></span> <span data-ttu-id="170da-137">有关详细信息，请参阅 [File Connection Manager](../connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="170da-137">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="170da-138">在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中，可以使用 **“执行 SQL 任务编辑器”** 对话框来键入 SQL 语句，也可使用 **“查询生成器”** （用于创建 SQL 查询的图形用户界面）键入。</span><span class="sxs-lookup"><span data-stu-id="170da-138">In [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, you can use the **Execute SQL Task Editor** dialog box to type SQL statements, or use **Query Builder**, a graphical user interface for creating SQL queries.</span></span> <span data-ttu-id="170da-139">有关详细信息，请参阅[执行 SQL 任务编辑器（常规页）](../execute-sql-task-editor-general-page.md)和[查询生成器](../query-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="170da-139">For more information, see [Execute SQL Task Editor &#40;General Page&#41;](../execute-sql-task-editor-general-page.md) and [Query Builder](../query-builder.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="170da-140">执行 SQL 任务可能无法成功分析在执行 SQL 任务外编写的有效 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="170da-140">Valid SQL statements written outside the Execute SQL task may not be parsed successfully by the Execute SQL task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="170da-141">执行 SQL 任务将使用 `RecognizeAll` ParseMode 枚举值。</span><span class="sxs-lookup"><span data-stu-id="170da-141">The Execute SQL Task uses the `RecognizeAll` ParseMode enumeration value.</span></span> <span data-ttu-id="170da-142">有关详细信息，请参阅 [ManagedBatchParser 命名空间](https://go.microsoft.com/fwlink/?LinkId=223617)。</span><span class="sxs-lookup"><span data-stu-id="170da-142">For more information, see [ManagedBatchParser Namespace](https://go.microsoft.com/fwlink/?LinkId=223617).</span></span>  
  
## <a name="sending-multiple-statements-in-a-batch"></a><span data-ttu-id="170da-143">按批发送多个语句</span><span class="sxs-lookup"><span data-stu-id="170da-143">Sending Multiple Statements in a Batch</span></span>  
 <span data-ttu-id="170da-144">如果在执行 SQL 任务中包含了多个语句，则可以将这些语句进行分组，并将它们作为一批来运行。</span><span class="sxs-lookup"><span data-stu-id="170da-144">If you include multiple statements in an Execute SQL task, you can group them and run them as a batch.</span></span> <span data-ttu-id="170da-145">若要标明批的结束，请使用 GO 命令。</span><span class="sxs-lookup"><span data-stu-id="170da-145">To signal the end of a batch, use the GO command.</span></span> <span data-ttu-id="170da-146">在两个 GO 命令间的所有 SQL 语句都作为一批发送到 OLE DB 访问接口来运行。</span><span class="sxs-lookup"><span data-stu-id="170da-146">All the SQL statements between two GO commands are sent in a batch to the OLE DB provider to be run.</span></span> <span data-ttu-id="170da-147">SQL 命令可以包含多个由 GO 命令分隔的批。</span><span class="sxs-lookup"><span data-stu-id="170da-147">The SQL command can include multiple batches separated by GO commands.</span></span>  
  
 <span data-ttu-id="170da-148">对可以分组到批的 SQL 语句类型有一些限制。</span><span class="sxs-lookup"><span data-stu-id="170da-148">There are restrictions on the kinds of SQL statements that you can group in a batch.</span></span> <span data-ttu-id="170da-149">有关详细信息，请参阅 [Batches of Statements](../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md)。</span><span class="sxs-lookup"><span data-stu-id="170da-149">For more information, see [Batches of Statements](../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md).</span></span>  
  
 <span data-ttu-id="170da-150">如果执行 SQL 任务运行一个 SQL 语句批，则下列规则适用于批：</span><span class="sxs-lookup"><span data-stu-id="170da-150">If the Execute SQL task runs a batch of SQL statements, the following rules apply to the batch:</span></span>  
  
-   <span data-ttu-id="170da-151">只有一个语句可以返回结果集，且该语句必须是批中的第一个语句。</span><span class="sxs-lookup"><span data-stu-id="170da-151">Only one statement can return a result set and it must be the first statement in the batch.</span></span>  
  
-   <span data-ttu-id="170da-152">如果结果集使用结果绑定，则查询必须返回相同数量的列。</span><span class="sxs-lookup"><span data-stu-id="170da-152">If the result set uses result bindings, the queries must return the same number of columns.</span></span> <span data-ttu-id="170da-153">如果查询返回不同数量的列，则任务失败。</span><span class="sxs-lookup"><span data-stu-id="170da-153">If the queries return a different number of columns, the task fails.</span></span> <span data-ttu-id="170da-154">但是，即使任务失败，其运行的查询（如 DELETE 或 INSERT 查询）也可能成功。</span><span class="sxs-lookup"><span data-stu-id="170da-154">However, even if the task fails, the queries that it runs, such as DELETE or INSERT queries, may succeed.</span></span>  
  
-   <span data-ttu-id="170da-155">如果结果绑定使用列名，则查询必须返回与任务中使用的结果集具有相同名称的列。</span><span class="sxs-lookup"><span data-stu-id="170da-155">If the result bindings use column names, the query must return columns that have the same names as the result set names that are used in the task.</span></span> <span data-ttu-id="170da-156">如果缺少列，则任务失败。</span><span class="sxs-lookup"><span data-stu-id="170da-156">If the columns are missing, the task fails.</span></span>  
  
-   <span data-ttu-id="170da-157">如果任务使用参数绑定，则批中的所有查询都必须具有相同数量和类型的参数。</span><span class="sxs-lookup"><span data-stu-id="170da-157">If the task uses parameter binding, all the queries in the batch must have the same number and types of parameters.</span></span>  
  
## <a name="running-parameterized-sql-commands"></a><span data-ttu-id="170da-158">运行参数化 SQL 命令</span><span class="sxs-lookup"><span data-stu-id="170da-158">Running Parameterized SQL Commands</span></span>  
 <span data-ttu-id="170da-159">SQL 语句和存储过程常常使用输入参数、输出参数和返回代码。</span><span class="sxs-lookup"><span data-stu-id="170da-159">SQL statements and stored procedures frequently use input parameters, output parameters, and return codes.</span></span> <span data-ttu-id="170da-160">执行 SQL 任务支持 `Input`、`Output` 和 `ReturnValue` 参数类型。</span><span class="sxs-lookup"><span data-stu-id="170da-160">The Execute SQL task supports the `Input`, `Output`, and `ReturnValue` parameter types.</span></span> <span data-ttu-id="170da-161">应当将 `Input` 类型用于输入参数，将 `Output` 用于输出参数并将 `ReturnValue` 用于返回代码。</span><span class="sxs-lookup"><span data-stu-id="170da-161">You use the `Input` type for input parameters, `Output` for output parameters, and `ReturnValue` for return codes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="170da-162">只有数据访问接口支持这些参数时，才可在执行 SQL 任务中使用它们。</span><span class="sxs-lookup"><span data-stu-id="170da-162">You can use parameters in an Execute SQL task only if the data provider supports them.</span></span>  
  
 <span data-ttu-id="170da-163">有关在执行 SQL 任务中使用参数和返回代码的信息，请参阅 [执行 SQL 任务中的参数和返回代码](execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="170da-163">For information on using parameters and return codes in the Execute SQL task, see [Parameters and Return Codes in the Execute SQL Task](execute-sql-task.md).</span></span>  
  
## <a name="specifying-a-result-set-type"></a><span data-ttu-id="170da-164">指定结果集类型</span><span class="sxs-lookup"><span data-stu-id="170da-164">Specifying a Result Set Type</span></span>  
 <span data-ttu-id="170da-165">执行 SQL 任务可能有结果集返回也可能没有结果集返回，这取决于 SQL 命令的类型。</span><span class="sxs-lookup"><span data-stu-id="170da-165">Depending on the type of SQL command, a result set may or may not be returned to the Execute SQL task.</span></span> <span data-ttu-id="170da-166">例如，SELECT 语句通常返回结果集，而 INSERT 语句通常不返回结果集。</span><span class="sxs-lookup"><span data-stu-id="170da-166">For example, a SELECT statement typically returns a result set, but an INSERT statement does not.</span></span> <span data-ttu-id="170da-167">SELECT 语句所返回的结果集可包含零行、单行或多行。</span><span class="sxs-lookup"><span data-stu-id="170da-167">The result set from a SELECT statement can contain zero rows, one row, or many rows.</span></span> <span data-ttu-id="170da-168">存储过程还可返回指示过程的执行状态的整数值（称为返回代码）。</span><span class="sxs-lookup"><span data-stu-id="170da-168">Stored procedures can also return an integer value, called a return code, that indicates the execution status of the procedure.</span></span> <span data-ttu-id="170da-169">这种情况下，结果集由单行组成。</span><span class="sxs-lookup"><span data-stu-id="170da-169">In that case, the result set consists of a single row.</span></span>  
  
 <span data-ttu-id="170da-170">有关从执行 SQL 任务的 SQL 命令中检索结果集的信息，请参阅 [执行 SQL 任务中的结果集](../result-sets-in-the-execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="170da-170">For information on retrieving result sets from SQL commands in the Execute SQL task, see [Result Sets in the Execute SQL Task](../result-sets-in-the-execute-sql-task.md).</span></span>  
  
## <a name="troubleshooting-the-execute-sql-task"></a><span data-ttu-id="170da-171">执行 SQL 任务故障排除</span><span class="sxs-lookup"><span data-stu-id="170da-171">Troubleshooting the Execute SQL Task</span></span>  
 <span data-ttu-id="170da-172">可以记录执行 SQL 任务对外部数据访问接口的调用。</span><span class="sxs-lookup"><span data-stu-id="170da-172">You can log the calls that the Execute SQL task makes to external data providers.</span></span> <span data-ttu-id="170da-173">您可以使用这项日志记录功能对执行 SQL 任务运行的 SQL 命令进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="170da-173">You can use this logging capability to troubleshoot the SQL commands that the Execute SQL task runs.</span></span> <span data-ttu-id="170da-174">若要记录执行 SQL 任务对外部数据访问接口的调用，请在包级别启用包日志记录并选择 **“诊断”** 事件。</span><span class="sxs-lookup"><span data-stu-id="170da-174">To log the calls that the Execute SQL task makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="170da-175">有关详细信息，请参阅 [包执行的疑难解答工具](../troubleshooting/troubleshooting-tools-for-package-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="170da-175">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
 <span data-ttu-id="170da-176">有时，SQL 命令或存储过程会返回多个结果集。</span><span class="sxs-lookup"><span data-stu-id="170da-176">Sometimes a SQL command or stored procedure returns multiple result sets.</span></span> <span data-ttu-id="170da-177">这些结果集不仅包含 `SELECT` 查询结果的行集，还包含 `RAISERROR` 或 `PRINT` 语句的错误结果的单个值。</span><span class="sxs-lookup"><span data-stu-id="170da-177">These result sets include not only rowsets that are the result of `SELECT` queries, but single values that are the result of errors of `RAISERROR` or `PRINT` statements.</span></span> <span data-ttu-id="170da-178">该任务是否忽略第一个结果集之后出现的结果集中的错误，取决于所用的连接管理器类型：</span><span class="sxs-lookup"><span data-stu-id="170da-178">Whether the task ignores errors in result sets that occur after the first result set depends on the type of connection manager that is used:</span></span>  
  
-   <span data-ttu-id="170da-179">在您使用 OLE DB 和 ADO 连接管理器时，该任务会忽略在第一个结果集之后出现的结果集。</span><span class="sxs-lookup"><span data-stu-id="170da-179">When you use OLE DB and ADO connection managers, the task ignores the result sets that occur after the first result set.</span></span> <span data-ttu-id="170da-180">因此，使用这些连接管理器，当错误不属于第一个结果集时，该任务会忽略 SQL 命令或存储过程返回的错误。</span><span class="sxs-lookup"><span data-stu-id="170da-180">Therefore, with these connection managers, the task ignores an error returned by an SQL command or a stored procedure when the error is not part of the first result set.</span></span>  
  
-   <span data-ttu-id="170da-181">在您使用 ODBC 和 ADO.NET 连接管理器时，该任务不会忽略在第一个结果集之后出现的结果集。</span><span class="sxs-lookup"><span data-stu-id="170da-181">When you use ODBC and ADO.NET connection managers, the task does not ignore result sets that occur after the first result set.</span></span> <span data-ttu-id="170da-182">使用这些连接管理器，当第一个结果集以外的结果集中包含错误时，该任务将失败并出现错误。</span><span class="sxs-lookup"><span data-stu-id="170da-182">With these connection managers, the task will fail with an error when a result set other than the first result set contains an error.</span></span>  
  
### <a name="custom-log-entries"></a><span data-ttu-id="170da-183">自定义日志项</span><span class="sxs-lookup"><span data-stu-id="170da-183">Custom Log Entries</span></span>  
 <span data-ttu-id="170da-184">下表介绍了执行 SQL 任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="170da-184">The following table describes the custom log entry for the Execute SQL task.</span></span> <span data-ttu-id="170da-185">有关详细信息，请参阅 [Integration Services (SSIS) 日志记录](../performance/integration-services-ssis-logging.md)和[日志记录的自定义消息](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="170da-185">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="170da-186">日志项</span><span class="sxs-lookup"><span data-stu-id="170da-186">Log entry</span></span>|<span data-ttu-id="170da-187">说明</span><span class="sxs-lookup"><span data-stu-id="170da-187">Description</span></span>|  
|---------------|-----------------|  
|`ExecuteSQLExecutingQuery`|<span data-ttu-id="170da-188">提供有关 SQL 语句的执行阶段的信息。</span><span class="sxs-lookup"><span data-stu-id="170da-188">Provides information about the execution phases of the SQL statement.</span></span> <span data-ttu-id="170da-189">在任务获得与数据库的连接时、任务开始准备 SQL 语句时以及执行完 SQL 语句之后写入日志项。</span><span class="sxs-lookup"><span data-stu-id="170da-189">Log entries are written when the task acquires connection to the database, when the task starts to prepare the SQL statement, and after the execution of the SQL statement is completed.</span></span> <span data-ttu-id="170da-190">准备阶段的日志条目包括任务所使用的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="170da-190">The log entry for the prepare phase includes the SQL statement that the task uses.</span></span>|  
  
## <a name="configuring-the-execute-sql-task"></a><span data-ttu-id="170da-191">配置执行 SQL 任务</span><span class="sxs-lookup"><span data-stu-id="170da-191">Configuring the Execute SQL Task</span></span>  
 <span data-ttu-id="170da-192">可以按照下列方式配置执行 SQL 任务：</span><span class="sxs-lookup"><span data-stu-id="170da-192">You can configure the Execute SQL task in the following ways:</span></span>  
  
-   <span data-ttu-id="170da-193">指定用于连接到数据库的连接管理器的类型。</span><span class="sxs-lookup"><span data-stu-id="170da-193">Specify the type of connection manager to use to connect to a database.</span></span>  
  
-   <span data-ttu-id="170da-194">指定 SQL 语句返回的结果集的类型。</span><span class="sxs-lookup"><span data-stu-id="170da-194">Specify the type of result set that the SQL statement returns.</span></span>  
  
-   <span data-ttu-id="170da-195">指定 SQL 语句的超时值。</span><span class="sxs-lookup"><span data-stu-id="170da-195">Specify a time-out for the SQL statements.</span></span>  
  
-   <span data-ttu-id="170da-196">指定 SQL 语句的源。</span><span class="sxs-lookup"><span data-stu-id="170da-196">Specify the source of the SQL statement.</span></span>  
  
-   <span data-ttu-id="170da-197">指明任务是否跳过 SQL 语句的准备阶段。</span><span class="sxs-lookup"><span data-stu-id="170da-197">Indicate whether the task skips the prepare phase for the SQL statement.</span></span>  
  
-   <span data-ttu-id="170da-198">如果使用 ADO 连接类型，则必须指明 SQL 语句是否为存储过程。</span><span class="sxs-lookup"><span data-stu-id="170da-198">If you use the ADO connection type, you must indicate whether the SQL statement is a stored procedure.</span></span> <span data-ttu-id="170da-199">对于其他的连接类型，该属性为只读且其值始终为 `false`。</span><span class="sxs-lookup"><span data-stu-id="170da-199">For other connection types, this property is read-only and its value is always `false`.</span></span>  
  
 <span data-ttu-id="170da-200">可以采用编程方式或通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器来设置属性。</span><span class="sxs-lookup"><span data-stu-id="170da-200">You can set properties programmatically or through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="170da-201">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="170da-201">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="170da-202">&#40;"常规" 页上执行 SQL 任务编辑器&#41;</span><span class="sxs-lookup"><span data-stu-id="170da-202">Execute SQL Task Editor &#40;General Page&#41;</span></span>](../execute-sql-task-editor-general-page.md)  
  
-   [<span data-ttu-id="170da-203">执行 SQL 任务编辑器 &#40;参数映射页&#41;</span><span class="sxs-lookup"><span data-stu-id="170da-203">Execute SQL Task Editor &#40;Parameter Mapping Page&#41;</span></span>](../execute-sql-task-editor-parameter-mapping-page.md)  
  
-   [<span data-ttu-id="170da-204">&#40;"结果集" 页上执行 SQL 任务编辑器&#41;</span><span class="sxs-lookup"><span data-stu-id="170da-204">Execute SQL Task Editor &#40;Result Set Page&#41;</span></span>](../execute-sql-task-editor-result-set-page.md)  
  
-   [<span data-ttu-id="170da-205">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="170da-205">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="170da-206">有关如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="170da-206">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="170da-207">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="170da-207">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="configuring-the-execute-sql-task-programmatically"></a><span data-ttu-id="170da-208">以编程方式配置执行 SQL 任务</span><span class="sxs-lookup"><span data-stu-id="170da-208">Configuring the Execute SQL Task Programmatically</span></span>  
 <span data-ttu-id="170da-209">有关以编程方式设置这些属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="170da-209">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask.ExecuteSQLTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="170da-210">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="170da-210">Related Tasks</span></span>  
  
-   [<span data-ttu-id="170da-211">在执行 SQL 任务中将查询参数映射到变量</span><span class="sxs-lookup"><span data-stu-id="170da-211">Map Query Parameters to Variables in an Execute SQL Task</span></span>](../map-query-parameters-to-variables-in-an-execute-sql-task.md)  
  
-   [<span data-ttu-id="170da-212">将结果集映射到执行 SQL 任务中的变量</span><span class="sxs-lookup"><span data-stu-id="170da-212">Map Result Sets to Variables in an Execute SQL Task</span></span>](../map-result-sets-to-variables-in-an-execute-sql-task.md)  
  
## <a name="related-content"></a><span data-ttu-id="170da-213">相关内容</span><span class="sxs-lookup"><span data-stu-id="170da-213">Related Content</span></span>  
  
-   [<span data-ttu-id="170da-214">执行 SQL 任务中的参数和返回代码</span><span class="sxs-lookup"><span data-stu-id="170da-214">Parameters and Return Codes in the Execute SQL Task</span></span>](execute-sql-task.md)  
  
-   [<span data-ttu-id="170da-215">执行 SQL 任务中的结果集</span><span class="sxs-lookup"><span data-stu-id="170da-215">Result Sets in the Execute SQL Task</span></span>](../result-sets-in-the-execute-sql-task.md)  
  
-   [<span data-ttu-id="170da-216">Transact-SQL 参考（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="170da-216">Transact-SQL Reference &#40;Database Engine&#41;</span></span>](/sql/t-sql/language-reference)  
  
-   <span data-ttu-id="170da-217">mssqltips.com 上的博客文章： [SQL Server 2012 中新的日期和时间函数](https://go.microsoft.com/fwlink/?LinkId=239783)</span><span class="sxs-lookup"><span data-stu-id="170da-217">Blog entry, [New Date and Time Functions in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=239783), on mssqltips.com</span></span>  
  
  
