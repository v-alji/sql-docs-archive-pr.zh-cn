---
title: 批量插入任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.bulkinserttask.f1
helpviewer_keywords:
- Bulk Insert task
- copying data [Integration Services]
ms.assetid: c5166156-6b4c-4369-81ed-27c4ce7040ae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8f0b306af7a067e4dbd46bc8df7ca689770a3ce2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578995"
---
# <a name="bulk-insert-task"></a><span data-ttu-id="e6afa-102">大容量插入任务</span><span class="sxs-lookup"><span data-stu-id="e6afa-102">Bulk Insert Task</span></span>
  <span data-ttu-id="e6afa-103">大容量插入任务为将大量的数据复制到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表或视图提供了有效的方法。</span><span class="sxs-lookup"><span data-stu-id="e6afa-103">The Bulk Insert task provides an efficient way to copy large amounts of data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or view.</span></span> <span data-ttu-id="e6afa-104">例如，假定贵公司在大型主机系统上存储了数百万行的产品列表，但公司的电子商务系统却使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 来填充网页。</span><span class="sxs-lookup"><span data-stu-id="e6afa-104">For example, suppose your company stores its million-row product list on a mainframe system, but the company's e-commerce system uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to populate Web pages.</span></span> <span data-ttu-id="e6afa-105">您必须每晚都用大型机的主产品列表更新 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 产品表。</span><span class="sxs-lookup"><span data-stu-id="e6afa-105">You must update the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] product table nightly with the master product list from the mainframe.</span></span> <span data-ttu-id="e6afa-106">若要更新表，请以制表符分隔格式保存产品列表，并使用大容量插入任务将数据直接复制到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中。</span><span class="sxs-lookup"><span data-stu-id="e6afa-106">To update the table, you save the product list in a tab-delimited format and use the Bulk Insert task to copy the data directly into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="e6afa-107">为确保高速数据复制，在从源文件向表或视图移动数据时，请不要对数据执行转换。</span><span class="sxs-lookup"><span data-stu-id="e6afa-107">To ensure high-speed data copying, transformations cannot be performed on the data while it is moving from the source file to the table or view.</span></span>  
  
## <a name="usage-considerations"></a><span data-ttu-id="e6afa-108">使用注意事项</span><span class="sxs-lookup"><span data-stu-id="e6afa-108">Usage Considerations</span></span>  
 <span data-ttu-id="e6afa-109">在使用大容量插入任务之前，请注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="e6afa-109">Before you use the Bulk Insert task, consider the following:</span></span>  
  
-   <span data-ttu-id="e6afa-110">大容量插入任务只能从文本文件将数据传输到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表或视图中。</span><span class="sxs-lookup"><span data-stu-id="e6afa-110">The Bulk Insert task can transfer data only from a text file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or view.</span></span> <span data-ttu-id="e6afa-111">若要使用大容量插入任务从其他数据库管理系统 (DBMS) 传输数据，必须先将数据从源导出到文本文件，然后再将数据从文本文件导入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表或视图中。</span><span class="sxs-lookup"><span data-stu-id="e6afa-111">To use the Bulk Insert task to transfer data from other database management systems (DBMSs), you must export the data from the source to a text file and then import the data from the text file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or view.</span></span>  
  
-   <span data-ttu-id="e6afa-112">目标必须是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中的表或视图。</span><span class="sxs-lookup"><span data-stu-id="e6afa-112">The destination must be a table or view in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="e6afa-113">如果目标表或视图已经包含数据，则在大容量插入任务运行时，新数据会追加到现有数据中。</span><span class="sxs-lookup"><span data-stu-id="e6afa-113">If the destination table or view already contains data, the new data is appended to the existing data when the Bulk Insert task runs.</span></span> <span data-ttu-id="e6afa-114">如果希望替换数据，请在运行大容量插入任务前运行可执行 DELETE 或 TRUNCATE 语句的“执行 SQL”任务。</span><span class="sxs-lookup"><span data-stu-id="e6afa-114">If you want to replace the data, run an Execute SQL task that runs a DELETE or TRUNCATE statement before you run the Bulk Insert task.</span></span> <span data-ttu-id="e6afa-115">有关详细信息，请参阅 [Execute SQL Task](execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="e6afa-115">For more information, see [Execute SQL Task](execute-sql-task.md).</span></span>  
  
-   <span data-ttu-id="e6afa-116">可以在大容量插入任务对象中使用格式化文件。</span><span class="sxs-lookup"><span data-stu-id="e6afa-116">You can use a format file in the Bulk Insert task object.</span></span> <span data-ttu-id="e6afa-117">如果已通过 **bcp** 实用工具创建了格式化文件，则可以在大容量插入任务中指定其路径。</span><span class="sxs-lookup"><span data-stu-id="e6afa-117">If you have a format file that was created by the **bcp** utility, you can specify its path in the Bulk Insert task.</span></span> <span data-ttu-id="e6afa-118">大容量插入任务支持 XML 和非 XML 格式化文件。</span><span class="sxs-lookup"><span data-stu-id="e6afa-118">The Bulk Insert task supports both XML and nonXML format files.</span></span> <span data-ttu-id="e6afa-119">有关格式化文件的详细信息，请参阅[导入或导出数据的格式化文件 (SQL Server)](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e6afa-119">For more information about format files, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
-   <span data-ttu-id="e6afa-120">只有 sysadmin 固定服务器角色的成员才能够运行包含大容量插入任务的包。</span><span class="sxs-lookup"><span data-stu-id="e6afa-120">Only members of the sysadmin fixed server role can run a package that contains a Bulk Insert task.</span></span>  
  
## <a name="bulk-insert-task-with-transactions"></a><span data-ttu-id="e6afa-121">使用事务的大容量插入任务</span><span class="sxs-lookup"><span data-stu-id="e6afa-121">Bulk Insert Task with Transactions</span></span>  
 <span data-ttu-id="e6afa-122">如果没有设置批大小，则整个大容量复制操作将被视为一个事务。</span><span class="sxs-lookup"><span data-stu-id="e6afa-122">If a batch size is not set, the complete bulk copy operation is treated as one transaction.</span></span> <span data-ttu-id="e6afa-123">批大小为 **0** 表示在一个批中将数据插入。</span><span class="sxs-lookup"><span data-stu-id="e6afa-123">A batch size of **0** indicates that the data is inserted in one batch.</span></span> <span data-ttu-id="e6afa-124">如果设置了批大小，则每个批代表一个事务，当批运行完成时，该事务也就被提交。</span><span class="sxs-lookup"><span data-stu-id="e6afa-124">If a batch size is set, each batch represents a transaction that is committed when the batch finishes running.</span></span>  
  
 <span data-ttu-id="e6afa-125">由于大容量插入任务与事务相关，所以其行为取决于任务是否加入了包事务。</span><span class="sxs-lookup"><span data-stu-id="e6afa-125">The behavior of the Bulk Insert task, as it relates to transactions, depends on whether the task joins the package transaction.</span></span> <span data-ttu-id="e6afa-126">如果大容量插入任务未加入包事务，则在尝试处理下一个批之前，将每个未出错的批作为一个单元提交。</span><span class="sxs-lookup"><span data-stu-id="e6afa-126">If the Bulk Insert task does not join the package transaction, each error-free batch is committed as a unit before the next batch is tried.</span></span> <span data-ttu-id="e6afa-127">如果大容量插入任务加入了包事务，则在任务结束时，未出错的批会保留在事务中。</span><span class="sxs-lookup"><span data-stu-id="e6afa-127">If the Bulk Insert task joins the package transaction, error-free batches remain in the transaction at the conclusion of the task.</span></span> <span data-ttu-id="e6afa-128">这些批要受到包的提交或回滚操作的影响。</span><span class="sxs-lookup"><span data-stu-id="e6afa-128">These batches are subject to the commit or rollback operation of the package.</span></span>  
  
 <span data-ttu-id="e6afa-129">大容量插入任务中的失败不自动回滚已成功加载的批；同样，若任务成功，批也不会自动提交。</span><span class="sxs-lookup"><span data-stu-id="e6afa-129">A failure in the Bulk Insert task does not automatically roll back successfully loaded batches; similarly, if the task succeeds, batches are not automatically committed.</span></span> <span data-ttu-id="e6afa-130">只有在响应包和工作流属性设置时，才会发生提交和回滚操作。</span><span class="sxs-lookup"><span data-stu-id="e6afa-130">Commit and rollback operations occur only in response to package and workflow property settings.</span></span>  
  
## <a name="source-and-destination"></a><span data-ttu-id="e6afa-131">源和目标</span><span class="sxs-lookup"><span data-stu-id="e6afa-131">Source and Destination</span></span>  
 <span data-ttu-id="e6afa-132">指定文本源文件的位置时，请注意下列事项：</span><span class="sxs-lookup"><span data-stu-id="e6afa-132">When you specify the location of the text source file, consider the following:</span></span>  
  
-   <span data-ttu-id="e6afa-133">服务器必须具有访问文件和目标数据库的权限。</span><span class="sxs-lookup"><span data-stu-id="e6afa-133">The server must have permission to access both the file and the destination database.</span></span>  
  
-   <span data-ttu-id="e6afa-134">服务器运行大容量插入任务。</span><span class="sxs-lookup"><span data-stu-id="e6afa-134">The server runs the Bulk Insert task.</span></span> <span data-ttu-id="e6afa-135">因此，任务使用的所有格式化文件都必须位于服务器上。</span><span class="sxs-lookup"><span data-stu-id="e6afa-135">Therefore, any format file that the task uses must be located on the server.</span></span>  
  
-   <span data-ttu-id="e6afa-136">大容量插入任务加载的源文件可以和要向其插入数据的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库位于同一服务器上，也可以位于远程服务器上。</span><span class="sxs-lookup"><span data-stu-id="e6afa-136">The source file that the Bulk Insert task loads can be on the same server as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database into which data is inserted, or on a remote server.</span></span> <span data-ttu-id="e6afa-137">如果文件在远程服务器上，则必须在路径中使用通用命名约定 (UNC) 名称来指定该文件名。</span><span class="sxs-lookup"><span data-stu-id="e6afa-137">If the file is on a remote server, you must specify the file name using the Universal Naming Convention (UNC) name in the path.</span></span>  
  
## <a name="performance-optimization"></a><span data-ttu-id="e6afa-138">性能优化</span><span class="sxs-lookup"><span data-stu-id="e6afa-138">Performance Optimization</span></span>  
 <span data-ttu-id="e6afa-139">若要优化性能，请注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="e6afa-139">To optimize performance, consider the following:</span></span>  
  
-   <span data-ttu-id="e6afa-140">如果文本文件与要向其插入数据的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库位于同一计算机上，则复制操作可以更快的速度进行，因为数据不是在网络上移动的。</span><span class="sxs-lookup"><span data-stu-id="e6afa-140">If the text file is located on the same computer as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database into which data is inserted, the copy operation occurs at an even faster rate because the data is not moved over the network.</span></span>  
  
-   <span data-ttu-id="e6afa-141">大容量插入任务不记录引发错误的行。</span><span class="sxs-lookup"><span data-stu-id="e6afa-141">The Bulk Insert task does not log error-causing rows.</span></span> <span data-ttu-id="e6afa-142">如果必须捕获此信息，请使用数据流组件的错误输出来将引发错误的行捕获到一个异常错误文件中。</span><span class="sxs-lookup"><span data-stu-id="e6afa-142">If you must capture this information, use the error outputs of data flow components to capture error-causing rows in an exception file.</span></span>  
  
## <a name="custom-log-entries-available-on-the-bulk-insert-task"></a><span data-ttu-id="e6afa-143">大容量插入任务可用的自定义日志项</span><span class="sxs-lookup"><span data-stu-id="e6afa-143">Custom Log Entries Available on the Bulk Insert Task</span></span>  
 <span data-ttu-id="e6afa-144">下表列出了大容量插入任务的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="e6afa-144">The following table lists the custom log entries for the Bulk Insert task.</span></span> <span data-ttu-id="e6afa-145">有关详细信息，请参阅 [Integration Services (SSIS) 日志记录](../performance/integration-services-ssis-logging.md)和[日志记录的自定义消息](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="e6afa-145">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="e6afa-146">日志项</span><span class="sxs-lookup"><span data-stu-id="e6afa-146">Log entry</span></span>|<span data-ttu-id="e6afa-147">说明</span><span class="sxs-lookup"><span data-stu-id="e6afa-147">Description</span></span>|  
|---------------|-----------------|  
|`BulkInsertTaskBegin`|<span data-ttu-id="e6afa-148">指示大容量插入开始。</span><span class="sxs-lookup"><span data-stu-id="e6afa-148">Indicates that the bulk insert began.</span></span>|  
|`BulkInsertTaskEnd`|<span data-ttu-id="e6afa-149">指示大容量插入完成。</span><span class="sxs-lookup"><span data-stu-id="e6afa-149">Indicates that the bulk insert finished.</span></span>|  
|`BulkInsertTaskInfos`|<span data-ttu-id="e6afa-150">提供有关任务的说明性信息。</span><span class="sxs-lookup"><span data-stu-id="e6afa-150">Provides descriptive information about the task.</span></span>|  
  
## <a name="bulk-insert-task-configuration"></a><span data-ttu-id="e6afa-151">大容量插入任务配置</span><span class="sxs-lookup"><span data-stu-id="e6afa-151">Bulk Insert Task Configuration</span></span>  
 <span data-ttu-id="e6afa-152">可以按照下列方法来配置大容量插入任务：</span><span class="sxs-lookup"><span data-stu-id="e6afa-152">You can configure the Bulk Insert task in the following ways:</span></span>  
  
-   <span data-ttu-id="e6afa-153">指定 OLE DB 连接管理器，以便连接到目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库以及要向其插入数据的表或视图。</span><span class="sxs-lookup"><span data-stu-id="e6afa-153">Specify the OLE DB connection manager to connect to the destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database and the table or view into which data is inserted.</span></span> <span data-ttu-id="e6afa-154">大容量插入任务仅支持目标数据库的 OLE DB 连接。</span><span class="sxs-lookup"><span data-stu-id="e6afa-154">The Bulk Insert task supports only OLE DB connections for the destination database.</span></span>  
  
-   <span data-ttu-id="e6afa-155">指定文件或平面文件连接管理器来访问该源文件。</span><span class="sxs-lookup"><span data-stu-id="e6afa-155">Specify the File or Flat File connection manager to access the source file.</span></span> <span data-ttu-id="e6afa-156">大容量插入任务仅将连接管理器用于源文件位置。</span><span class="sxs-lookup"><span data-stu-id="e6afa-156">The Bulk Insert task uses the connection manager only for the location of the source file.</span></span> <span data-ttu-id="e6afa-157">该任务将忽略在连接管理器编辑器中所选择的其他选项。</span><span class="sxs-lookup"><span data-stu-id="e6afa-157">The task ignores other options that you select in the connection manager editor.</span></span>  
  
-   <span data-ttu-id="e6afa-158">通过使用格式化文件或通过定义源数据的列和行分隔符来定义大容量插入任务使用的格式。</span><span class="sxs-lookup"><span data-stu-id="e6afa-158">Define the format that is used by the Bulk Insert task, either by using a format file or by defining the column and row delimiters of the source data.</span></span> <span data-ttu-id="e6afa-159">如果使用格式化文件，请指定文件连接管理器来访问该格式化文件。</span><span class="sxs-lookup"><span data-stu-id="e6afa-159">If using a format file, specify the File connection manager to access the format file.</span></span>  
  
-   <span data-ttu-id="e6afa-160">指定在任务插入数据时要对目标表或视图执行的操作。</span><span class="sxs-lookup"><span data-stu-id="e6afa-160">Specify actions to perform on the destination table or view when the task inserts the data.</span></span> <span data-ttu-id="e6afa-161">选项包括是否检查约束、启用标识插入、保留空值、激发触发器或锁定表。</span><span class="sxs-lookup"><span data-stu-id="e6afa-161">The options include whether to check constraints, enable identity inserts, keep nulls, fire triggers, or lock the table.</span></span>  
  
-   <span data-ttu-id="e6afa-162">提供要插入的数据批的信息，如批大小、文件中要插入的第一行和最后一行、发生多少次插入错误后任务停止插入行以及要排序的列的名称。</span><span class="sxs-lookup"><span data-stu-id="e6afa-162">Provide information about the batch of data to insert, such as the batch size, the first and last row from the file to insert, the number of insert errors that can occur before the task stops inserting rows, and the names of the columns that will be sorted.</span></span>  
  
 <span data-ttu-id="e6afa-163">如果大容量插入任务使用平面文件连接管理器访问源文件，则该任务不使用在平面文件连接管理器中指定的格式。</span><span class="sxs-lookup"><span data-stu-id="e6afa-163">If the Bulk Insert task uses a Flat File connection manager to access the source file, the task does not use the format specified in the Flat File connection manager.</span></span> <span data-ttu-id="e6afa-164">相反，大容量插入任务将使用在格式化文件中指定的格式，或者使用该任务的 RowDelimite 和 ColumnDelimiter 属性的值。</span><span class="sxs-lookup"><span data-stu-id="e6afa-164">Instead, the Bulk Insert task uses either the format specified in a format file, or the values of the RowDelimiter and ColumnDelimiter properties of the task.</span></span>  
  
 <span data-ttu-id="e6afa-165">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="e6afa-165">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="e6afa-166">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="e6afa-166">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="e6afa-167">大容量插入任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="e6afa-167">Bulk Insert Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="e6afa-168">大容量插入任务编辑器（“连接”页）</span><span class="sxs-lookup"><span data-stu-id="e6afa-168">Bulk Insert Task Editor &#40;Connection Page&#41;</span></span>](../bulk-insert-task-editor-connection-page.md)  
  
-   [<span data-ttu-id="e6afa-169">大容量插入任务编辑器（“选项”页）</span><span class="sxs-lookup"><span data-stu-id="e6afa-169">Bulk Insert Task Editor &#40;Options Page&#41;</span></span>](../bulk-insert-task-editor-options-page.md)  
  
-   [<span data-ttu-id="e6afa-170">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="e6afa-170">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="e6afa-171">有关如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="e6afa-171">For more information about how to setthese properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="e6afa-172">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="e6afa-172">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
### <a name="programmatic-configuration-of-the-bulk-insert-task"></a><span data-ttu-id="e6afa-173">大容量插入任务的编程配置</span><span class="sxs-lookup"><span data-stu-id="e6afa-173">Programmatic Configuration of the Bulk Insert Task</span></span>  
 <span data-ttu-id="e6afa-174">有关以编程方式设置这些属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="e6afa-174">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="e6afa-175">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="e6afa-175">Related Tasks</span></span>  
 [<span data-ttu-id="e6afa-176">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="e6afa-176">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-content"></a><span data-ttu-id="e6afa-177">相关内容</span><span class="sxs-lookup"><span data-stu-id="e6afa-177">Related Content</span></span>  
  
-   <span data-ttu-id="e6afa-178">support.microsoft.com 上的技术文章 [您可能会在支持 UAC 的系统上看到“无法准备 SSIS 大容量插入以插入数据”错误](https://go.microsoft.com/fwlink/?LinkId=233693)。</span><span class="sxs-lookup"><span data-stu-id="e6afa-178">Technical article, [You may get "Unable to prepare the SSIS bulk insert for data insertion" error on UAC enabled systems](https://go.microsoft.com/fwlink/?LinkId=233693), on support.microsoft.com.</span></span>  
  
-   <span data-ttu-id="e6afa-179">msdn.microsoft.com 上的技术文章 [数据加载性能指南](https://go.microsoft.com/fwlink/?LinkId=233700)。</span><span class="sxs-lookup"><span data-stu-id="e6afa-179">Technical article, [The Data Loading Performance Guide](https://go.microsoft.com/fwlink/?LinkId=233700), on msdn.microsoft.com.</span></span>  
  
-   <span data-ttu-id="e6afa-180">simple-talk.com 上的技术文章 [使用 SQL Server Integration Services 大容量加载数据](https://go.microsoft.com/fwlink/?LinkId=233701)。</span><span class="sxs-lookup"><span data-stu-id="e6afa-180">Technical article, [Using SQL Server Integration Services to Bulk Load Data](https://go.microsoft.com/fwlink/?LinkId=233701), on simple-talk.com.</span></span>  
  
  
