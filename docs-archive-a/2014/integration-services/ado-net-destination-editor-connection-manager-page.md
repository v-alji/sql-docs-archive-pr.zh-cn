---
title: ADO NET 目标编辑器 (连接管理器页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.connection.f1
ms.assetid: a3b11286-32c8-40e1-8ae7-090e2590345a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 78851d5bbad18d2d1076eaa87200dd73e6962a90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576945"
---
# <a name="ado-net-destination-editor-connection-manager-page"></a><span data-ttu-id="f9a8b-102">ADO NET 目标编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="f9a8b-102">ADO NET Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="f9a8b-103">可以使用 **“ADO NET 目标编辑器”** 对话框的 **“连接管理器”** 页，为目标选择 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 连接。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-103">Use the **Connection Manager** page of the **ADO NET Destination Editor** dialog box to select the [!INCLUDE[vstecado](../includes/vstecado-md.md)] connection for the destination.</span></span> <span data-ttu-id="f9a8b-104">使用此页还可以选择数据库中的表或视图。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-104">This page also lets you select a table or view from the database.</span></span>  
  
 <span data-ttu-id="f9a8b-105">若要了解有关 ADO NET 目标的详细信息，请参阅 [ADO NET Destination](data-flow/ado-net-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-105">To learn more about the ADO NET destination, see [ADO NET Destination](data-flow/ado-net-destination.md).</span></span>  
  
 <span data-ttu-id="f9a8b-106">**打开“连接管理器”页**</span><span class="sxs-lookup"><span data-stu-id="f9a8b-106">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="f9a8b-107">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开具有 ADO NET 目标的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-107">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET destination.</span></span>  
  
2.  <span data-ttu-id="f9a8b-108">在“数据流”  选项卡上，双击 ADO NET 目标。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-108">On the **Data Flow** tab, double-click the ADO NET destination.</span></span>  
  
3.  <span data-ttu-id="f9a8b-109">在 **“ADO NET 目标编辑器”** 中，单击 **“连接管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-109">In the **ADO NET Destination Editor**, click **Connection Manager**.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="f9a8b-110">静态选项</span><span class="sxs-lookup"><span data-stu-id="f9a8b-110">Static Options</span></span>  
 <span data-ttu-id="f9a8b-111">**“ODBC 目标编辑器”**</span><span class="sxs-lookup"><span data-stu-id="f9a8b-111">**Connection manager**</span></span>  
 <span data-ttu-id="f9a8b-112">从列表中选择一个现有连接管理器，或通过单击“新建”  创建一个新连接。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-112">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="f9a8b-113">**新建**</span><span class="sxs-lookup"><span data-stu-id="f9a8b-113">**New**</span></span>  
 <span data-ttu-id="f9a8b-114">使用“配置 ADO.NET 连接管理器”  对话框创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-114">Create a new connection manager by using the **Configure ADO.NET Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="f9a8b-115">**使用表或视图**</span><span class="sxs-lookup"><span data-stu-id="f9a8b-115">**Use a table or view**</span></span>  
 <span data-ttu-id="f9a8b-116">从列表中选择现有表或视图，或单击  “新建”创建新表。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-116">Select an existing table or view from the list, or create a new table by clicking **New**..</span></span>  
  
 <span data-ttu-id="f9a8b-117">**新建**</span><span class="sxs-lookup"><span data-stu-id="f9a8b-117">**New**</span></span>  
 <span data-ttu-id="f9a8b-118">使用  “创建表”对话框创建新表或视图。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-118">Create a new table or view by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9a8b-119">单击 **“新建”** 时， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 将基于所连接的数据源生成一条默认的 CREATE TABLE 语句。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-119">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="f9a8b-120">即使源表包含一个已声明了 FILESTREAM 属性的列，此默认 CREATE TABLE 语句也不会包含 FILESTREAM 属性。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-120">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="f9a8b-121">若要运行具有 FILESTREAM 属性的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 组件，首先要在目标数据库上实现 FILESTREAM 存储。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-121">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="f9a8b-122">然后在 **“创建表”** 对话框中将 FILESTREAM 属性添加到 CREATE TABLE 语句中。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-122">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="f9a8b-123">有关详细信息，请参阅[二进制大型对象 (Blob) 数据 (SQL Server)](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-123">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="f9a8b-124">**预览**</span><span class="sxs-lookup"><span data-stu-id="f9a8b-124">**Preview**</span></span>  
 <span data-ttu-id="f9a8b-125">使用“预览查询结果”  对话框预览结果。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-125">Preview results by using the **Preview Query Results** dialog box.</span></span> <span data-ttu-id="f9a8b-126">预览最多可以显示 200 行。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-126">Preview can display up to 200 rows.</span></span>  
  
 <span data-ttu-id="f9a8b-127">**可用时使用大容量插入**</span><span class="sxs-lookup"><span data-stu-id="f9a8b-127">**Use bulk insert when available**</span></span>  
 <span data-ttu-id="f9a8b-128">指定是否使用 <xref:System.Data.SqlClient.SqlBulkCopy> 接口来提高大容量插入操作的性能。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-128">Specify whether to use the <xref:System.Data.SqlClient.SqlBulkCopy> interface to improve the performance of bulk insert operations.</span></span>  
  
 <span data-ttu-id="f9a8b-129">只有可返回 <xref:System.Data.SqlClient.SqlConnection> 对象的 ADO.NET 提供程序才支持使用 <xref:System.Data.SqlClient.SqlBulkCopy> 接口。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-129">Only ADO.NET providers that return a <xref:System.Data.SqlClient.SqlConnection> object support the use of the <xref:System.Data.SqlClient.SqlBulkCopy> interface.</span></span> <span data-ttu-id="f9a8b-130">SQL Server 的 .NET 数据提供程序 (SqlClient) 可以返回 <xref:System.Data.SqlClient.SqlConnection> 对象，而自定义提供程序可以返回 <xref:System.Data.SqlClient.SqlConnection> 对象。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-130">The .NET Data Provider for SQL Server (SqlClient) returns a <xref:System.Data.SqlClient.SqlConnection> object, and a custom provider may return a <xref:System.Data.SqlClient.SqlConnection> object.</span></span>  
  
 <span data-ttu-id="f9a8b-131">可使用 SQL Server 的 .NET 数据提供程序 (SqlClient) 连接到 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-131">You can use the .NET Data Provider for SQL Server (SqlClient) to connect to [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)].</span></span>  
  
 <span data-ttu-id="f9a8b-132">如果选择“可用时使用大容量插入”并将“错误”选项设置为“重定向该行”，则目标重定向到错误输出的数据批次可能包含正确的行。    有关以大容量操作方式处理错误的详细信息，请参阅[数据中的错误处理](data-flow/error-handling-in-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-132">If you select **Use bulk insert when available**, and set the **Error** option to **Redirect the row**, the batch of data that the destination redirects to the error output may include good rows.For more information about handling errors in bulk operations, see [Error Handling in Data](data-flow/error-handling-in-data.md).</span></span> <span data-ttu-id="f9a8b-133">有关  “错误”选项的详细信息，请参阅 [ADO NET 目标编辑器（“错误输出”页）](../../2014/integration-services/ado-net-destination-editor-error-output-page.md)。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-133">For more information about the **Error** option, see [ADO NET Destination Editor &#40;Error Output Page&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9a8b-134">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 或 Sybase 源表包含一个标识列，则必须在 ADO NET 目标前后使用执行 SQL 任务来运行 SET IDENTITY_INSERT 语句。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-134">If a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or Sybase source table includes an identity column, you must use Execute SQL tasks to run a SET IDENTITY_INSERT statement before and after the ADO NET destination.</span></span> <span data-ttu-id="f9a8b-135">标识列属性为列指定一个增量值。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-135">The identity column property specifies an incremental value for the column.</span></span> <span data-ttu-id="f9a8b-136">SET IDENTITY_INSERT 语句启用要插入到标识列的显式值。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-136">The SET IDENTITY_INSERT statement enables explicit values to be inserted into the identity column.</span></span> <span data-ttu-id="f9a8b-137">若要基于同一个数据库连接运行 CREATE TABLE 和 SET IDENTITY 语句，请将 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 连接管理器的 `RetainSameConnection` 属性设置为 `True`。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-137">To run the CREATE TABLE and SET IDENTITY statements on the same database connection, set the `RetainSameConnection` property of the [!INCLUDE[vstecado](../includes/vstecado-md.md)] connection manager to `True`.</span></span> <span data-ttu-id="f9a8b-138">此外，还要对执行 SQL 任务和 ADO NET 目标使用相同的 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-138">Also, use the same [!INCLUDE[vstecado](../includes/vstecado-md.md)] connection manager for the Execute SQL tasks and the ADO NET destination.</span></span>  
>   
>  <span data-ttu-id="f9a8b-139">有关详细信息，请参阅 [SET IDENTITY_INSERT (Transact SQL)](/sql/t-sql/statements/set-identity-insert-transact-sql) 和 [IDENTITY（属性）(Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql-identity-property)。</span><span class="sxs-lookup"><span data-stu-id="f9a8b-139">For more information, see [SET IDENTITY_INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-identity-insert-transact-sql) and [IDENTITY &#40;Property&#41; &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql-identity-property).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="f9a8b-140">外部资源</span><span class="sxs-lookup"><span data-stu-id="f9a8b-140">External Resources</span></span>  
 <span data-ttu-id="f9a8b-141">sqlcat.com 上的技术文章 [快速将数据加载到 Azure SQL 数据库中](https://go.microsoft.com/fwlink/?LinkId=244333)</span><span class="sxs-lookup"><span data-stu-id="f9a8b-141">Technical article, [Loading data to Azure SQL Database the fast way](https://go.microsoft.com/fwlink/?LinkId=244333), on sqlcat.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9a8b-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f9a8b-142">See Also</span></span>  
 <span data-ttu-id="f9a8b-143">[ADO NET 目标编辑器 &#40;映射 "页面&#41;](../../2014/integration-services/ado-net-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="f9a8b-143">[ADO NET Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/ado-net-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="f9a8b-144">[ADO NET 目标编辑器 &#40;错误输出页&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="f9a8b-144">[ADO NET Destination Editor &#40;Error Output Page&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="f9a8b-145">[ADO.NET 连接管理器](connection-manager/ado-net-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="f9a8b-145">[ADO.NET Connection Manager](connection-manager/ado-net-connection-manager.md) </span></span>  
 [<span data-ttu-id="f9a8b-146">执行 SQL 任务</span><span class="sxs-lookup"><span data-stu-id="f9a8b-146">Execute SQL Task</span></span>](control-flow/execute-sql-task.md)  
  
  
