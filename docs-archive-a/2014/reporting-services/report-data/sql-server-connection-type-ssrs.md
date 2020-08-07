---
title: SQL Server 连接类型 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 957e7091-e08f-48d2-9506-872227ae8b20
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 34a519c8a291dc351be98316b18a45ade4918579
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588928"
---
# <a name="sql-server-connection-type-ssrs"></a><span data-ttu-id="15901-102">SQL Server 连接类型 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="15901-102">SQL Server Connection Type (SSRS)</span></span>
  <span data-ttu-id="15901-103">若要在报表中包括来自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的数据，你必须具有一个基于 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]类型的报表数据源的数据集。</span><span class="sxs-lookup"><span data-stu-id="15901-103">To include data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database in your report, you must have a dataset that is based on a report data source of type [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="15901-104">此内置数据源类型基于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据扩展插件。</span><span class="sxs-lookup"><span data-stu-id="15901-104">This built-in data source type is based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data extension.</span></span> <span data-ttu-id="15901-105">使用此数据源类型可连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的当前版本和早期版本并从中检索数据。</span><span class="sxs-lookup"><span data-stu-id="15901-105">Use this data source type to connect to and retrieve data from the current version and earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="15901-106">此数据扩展插件支持多值参数、服务器聚合以及与连接字符串分开管理的凭据。</span><span class="sxs-lookup"><span data-stu-id="15901-106">This data extension supports multivalue parameters, server aggregates, and credentials managed separately from the connection string.</span></span>  
  
 <span data-ttu-id="15901-107">使用本主题中的信息来生成一个数据源。</span><span class="sxs-lookup"><span data-stu-id="15901-107">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="15901-108">有关分步说明，请参阅[添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="15901-108">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="15901-109">连接字符串</span><span class="sxs-lookup"><span data-stu-id="15901-109">Connection String</span></span>  
 <span data-ttu-id="15901-110">当连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库时，您将会连接到服务器上一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="15901-110">When you connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, you are connecting to the database object in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a server.</span></span> <span data-ttu-id="15901-111">该数据库可能具有包含多个表、视图和存储过程的不同架构。</span><span class="sxs-lookup"><span data-stu-id="15901-111">The database might have multiple schemas that have multiple tables, views, and stored procedures.</span></span> <span data-ttu-id="15901-112">可在查询设计器中指定要使用的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="15901-112">You specify the database object to use in the query designer.</span></span> <span data-ttu-id="15901-113">如果未在连接字符串中指定数据库，则将连接到数据库管理员为您分配的默认数据库。</span><span class="sxs-lookup"><span data-stu-id="15901-113">If you do not specify a database in the connection string, you connect to the default database that the database administrator assigned to you.</span></span>  
  
 <span data-ttu-id="15901-114">请联系数据库管理员，获取连接信息以及用于连接到数据源的凭据。</span><span class="sxs-lookup"><span data-stu-id="15901-114">Contact your database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="15901-115">下面的连接字符串示例指定本地客户端上的示例数据库：</span><span class="sxs-lookup"><span data-stu-id="15901-115">The following connection string example specifies a sample database on the local client:</span></span>  
  
```  
Data Source=<server>;Initial Catalog=AdventureWorks  
```  
  
 <span data-ttu-id="15901-116">有关连接字符串示例的详细信息，请参阅 [报表生成器中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="15901-116">For more information about connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="15901-117">凭据</span><span class="sxs-lookup"><span data-stu-id="15901-117">Credentials</span></span>  
 <span data-ttu-id="15901-118">执行以下操作时需要提供凭据：运行查询、本地预览报表以及从报表服务器预览报表。</span><span class="sxs-lookup"><span data-stu-id="15901-118">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="15901-119">报表发布后，您可能需要更改数据源的凭据，以使报表在报表服务器上运行时，用于检索数据的权限有效。</span><span class="sxs-lookup"><span data-stu-id="15901-119">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="15901-120">在报表创作客户端，可以使用下列选项指定凭据：</span><span class="sxs-lookup"><span data-stu-id="15901-120">From a report authoring client, the following options are available to specify credentials:</span></span>  
  
-   <span data-ttu-id="15901-121">当前 Windows 用户（也称为集成安全性）。</span><span class="sxs-lookup"><span data-stu-id="15901-121">Current Windows user (also known as integrated security).</span></span>  
  
-   <span data-ttu-id="15901-122">使用存储的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="15901-122">Use a stored user name and password.</span></span>  
  
-   <span data-ttu-id="15901-123">提示用户输入凭据。</span><span class="sxs-lookup"><span data-stu-id="15901-123">Prompt the user for credentials.</span></span> <span data-ttu-id="15901-124">此选项仅支持 Windows 集成安全性。</span><span class="sxs-lookup"><span data-stu-id="15901-124">This option supports Windows integrated security only.</span></span>  
  
-   <span data-ttu-id="15901-125">不需要提供任何凭据。</span><span class="sxs-lookup"><span data-stu-id="15901-125">No credentials are required.</span></span> <span data-ttu-id="15901-126">若要使用此选项，您必须具有为报表服务器配置的无人参与的执行帐户。</span><span class="sxs-lookup"><span data-stu-id="15901-126">To use this option, you must have the unattended execution account configured on the report server.</span></span> <span data-ttu-id="15901-127">有关详细信息，请参阅 msdn.microsoft.com 上 [Reporting Services 文档](https://go.microsoft.com/fwlink/?linkid=121312)中的[配置无人参与的执行帐户（SSRS 配置管理器）](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="15901-127">For more information, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="15901-128">有关详细信息，请参阅[Reporting Services 中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)或[在报表生成器中指定凭据](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="15901-128">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
  
##  <a name="queries"></a><a name="Query"></a> <span data-ttu-id="15901-129">查询</span><span class="sxs-lookup"><span data-stu-id="15901-129">Queries</span></span>  
 <span data-ttu-id="15901-130">查询指定了要为报表数据集检索哪些数据。</span><span class="sxs-lookup"><span data-stu-id="15901-130">A query specifies which data to retrieve for a report dataset.</span></span> <span data-ttu-id="15901-131">查询的结果集中的列填充数据集的字段集合。</span><span class="sxs-lookup"><span data-stu-id="15901-131">The columns in the result set for a query populate the field collection for a dataset.</span></span> <span data-ttu-id="15901-132">报表仅处理查询检索的第一个结果集。</span><span class="sxs-lookup"><span data-stu-id="15901-132">A report processes only the first result set that a query retrieves.</span></span>  
  
 <span data-ttu-id="15901-133">默认情况下，如果您创建一个新查询，或者打开一个可在图形查询设计器中显示的现有查询，则可以使用关系查询设计器。</span><span class="sxs-lookup"><span data-stu-id="15901-133">By default, if you create a new query or open an existing query that can be represented in the graphical query designer, the relational query designer is available.</span></span> <span data-ttu-id="15901-134">可以通过下列方式指定查询：</span><span class="sxs-lookup"><span data-stu-id="15901-134">You can specify a query in the following ways:</span></span>  
  
-   <span data-ttu-id="15901-135">以交互方式生成查询。</span><span class="sxs-lookup"><span data-stu-id="15901-135">Build a query interactively.</span></span> <span data-ttu-id="15901-136">使用关系查询设计器，此设计器显示表、视图、存储过程及其他数据库项按数据库架构组织的层次结构视图。</span><span class="sxs-lookup"><span data-stu-id="15901-136">Use the relational query designer that displays a hierarchical view of tables, views, stored procedures, and other database items, organized by database schema.</span></span> <span data-ttu-id="15901-137">选择表或视图中的列，或者指定存储过程或表值函数。</span><span class="sxs-lookup"><span data-stu-id="15901-137">Select columns from tables or views, or specify stored procedures or table-valued functions.</span></span> <span data-ttu-id="15901-138">通过指定筛选条件限制要检索的数据行数。</span><span class="sxs-lookup"><span data-stu-id="15901-138">Limit the number of rows of data to retrieve by specifying filter criteria.</span></span> <span data-ttu-id="15901-139">通过设置参数选项自定义报表运行时的筛选器。</span><span class="sxs-lookup"><span data-stu-id="15901-139">Customize the filter when the report runs by setting the parameter option.</span></span>  
  
-   <span data-ttu-id="15901-140">键入或粘贴查询。</span><span class="sxs-lookup"><span data-stu-id="15901-140">Type or paste a query.</span></span> <span data-ttu-id="15901-141">使用基于文本的查询设计器直接输入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 文本、粘贴来自其他来源的查询文本、输入使用关系查询设计器无法生成的复杂查询，或输入基于查询的表达式。</span><span class="sxs-lookup"><span data-stu-id="15901-141">Use the text-based query designer to enter [!INCLUDE[tsql](../../includes/tsql-md.md)] text directly, to paste query text from another source, to enter complex queries that cannot be built by using the relational query designer, or to enter query-based expressions.</span></span>  
  
-   <span data-ttu-id="15901-142">从文件或报表中导入现有的查询。</span><span class="sxs-lookup"><span data-stu-id="15901-142">Import an existing query from a file or report.</span></span> <span data-ttu-id="15901-143">使用任一查询设计器中的 **“导入查询”** 按钮浏览到 .sql 文件或 .rdl 文件，然后导入查询。</span><span class="sxs-lookup"><span data-stu-id="15901-143">Use the **Import** query button from either query designer to browse to a .sql file or .rdl file and import a query.</span></span>  
  
 <span data-ttu-id="15901-144">有关详细信息，请参阅[关系查询设计器用户界面（报表生成器）](relational-query-designer-user-interface-report-builder.md)和[基于文本的查询设计器用户界面（报表生成器）](text-based-query-designer-user-interface-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="15901-144">For more information, see [Relational Query Designer User Interface &#40;Report Builder&#41;](relational-query-designer-user-interface-report-builder.md) and [Text-based Query Designer User Interface &#40;Report Builder&#41;](text-based-query-designer-user-interface-report-builder.md).</span></span>  
  
 <span data-ttu-id="15901-145">支持以下查询模式：</span><span class="sxs-lookup"><span data-stu-id="15901-145">The following query modes are supported:</span></span>  
  
-   <span data-ttu-id="15901-146">[文本](#QueryText) 键入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令。</span><span class="sxs-lookup"><span data-stu-id="15901-146">[Text](#QueryText) Type in [!INCLUDE[tsql](../../includes/tsql-md.md)] commands.</span></span>  
  
-   <span data-ttu-id="15901-147">[存储过程](#QueryStoredProcedure) 从存储过程的列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="15901-147">[Stored Procedure](#QueryStoredProcedure) Choose from a list of stored procedures.</span></span>  
  
###  <a name="using-query-type-text"></a><a name="QueryText"></a> <span data-ttu-id="15901-148">使用 Text 查询类型</span><span class="sxs-lookup"><span data-stu-id="15901-148">Using Query Type Text</span></span>  
 <span data-ttu-id="15901-149">在基于文本的查询设计器中，可以键入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令来定义数据集中的数据。</span><span class="sxs-lookup"><span data-stu-id="15901-149">In the text-based query designer, you can type [!INCLUDE[tsql](../../includes/tsql-md.md)] commands to define the data in a dataset.</span></span> <span data-ttu-id="15901-150">例如，下面的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询选择职位为销售助理的所有雇员的姓名：</span><span class="sxs-lookup"><span data-stu-id="15901-150">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] query selects the names of all employees who are marketing assistants:</span></span>  
  
```  
SELECT  
  HumanResources.Employee.BusinessEntityID  
  ,HumanResources.Employee.JobTitle  
  ,Person.Person.FirstName  
  ,Person.Person.LastName  
FROM  
  Person.Person  
  INNER JOIN HumanResources.Employee  
    ON Person.Person.BusinessEntityID = HumanResources.Employee.BusinessEntityID  
WHERE HumanResources.Employee.JobTitle = 'Marketing Assistant'   
```  
  
 <span data-ttu-id="15901-151">单击工具栏上的 **“运行”** 按钮 ( **!** ) 可以运行查询并显示结果集。</span><span class="sxs-lookup"><span data-stu-id="15901-151">Click the **Run** button (**!**) on the toolbar to run the query and display a result set.</span></span>  
  
 <span data-ttu-id="15901-152">若要参数化此查询，请添加一个查询参数。</span><span class="sxs-lookup"><span data-stu-id="15901-152">To parameterize this query, add a query parameter.</span></span> <span data-ttu-id="15901-153">例如，将 WHERE 子句更改为下面的内容：</span><span class="sxs-lookup"><span data-stu-id="15901-153">For example, change the WHERE clause to the following:</span></span>  
  
 `WHERE HumanResources.Employee.JobTitle = (@JobTitle)`  
  
 <span data-ttu-id="15901-154">运行查询时，会自动创建与查询参数对应的报表参数。</span><span class="sxs-lookup"><span data-stu-id="15901-154">When you run the query, report parameters that correspond to query parameters are automatically created.</span></span> <span data-ttu-id="15901-155">有关详细信息，请参阅本主题后面的 [查询参数](#Parameters) 。</span><span class="sxs-lookup"><span data-stu-id="15901-155">For more information, see [Query Parameters](#Parameters) later in this topic.</span></span>  
  
  
###  <a name="using-query-type-storedprocedure"></a><a name="QueryStoredProcedure"></a> <span data-ttu-id="15901-156">使用 StoredProcedure 查询类型</span><span class="sxs-lookup"><span data-stu-id="15901-156">Using Query Type StoredProcedure</span></span>  
 <span data-ttu-id="15901-157">您可以采用以下方式之一为数据集查询指定存储过程：</span><span class="sxs-lookup"><span data-stu-id="15901-157">You can specify a stored procedure for a dataset query in one of the following ways:</span></span>  
  
-   <span data-ttu-id="15901-158">在 **“数据集属性”** 对话框中，设置 **“存储过程”** 选项。</span><span class="sxs-lookup"><span data-stu-id="15901-158">In the **Dataset Properties** dialog box, set the **Stored Procedure** option.</span></span> <span data-ttu-id="15901-159">从存储过程和表值函数的下拉列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="15901-159">Choose from the drop-down list of stored procedures and table-valued functions.</span></span>  
  
-   <span data-ttu-id="15901-160">在关系查询设计器中的“数据库视图”窗格中，选择存储过程或表值函数。</span><span class="sxs-lookup"><span data-stu-id="15901-160">In the relational query designer, in the Database view pane, select a stored procedure or table-valued function.</span></span>  
  
-   <span data-ttu-id="15901-161">在基于文本的查询设计器中，从工具栏中选择 **StoredProcedure** 。</span><span class="sxs-lookup"><span data-stu-id="15901-161">In the text-based query designer, select **StoredProcedure** from the toolbar.</span></span>  
  
 <span data-ttu-id="15901-162">选择存储过程或表值函数之后，就可以运行查询。</span><span class="sxs-lookup"><span data-stu-id="15901-162">After you select a stored procedure or table-valued function, you can run the query.</span></span> <span data-ttu-id="15901-163">系统将提示您提供输入参数的值。</span><span class="sxs-lookup"><span data-stu-id="15901-163">You will be prompted for input parameter values.</span></span> <span data-ttu-id="15901-164">运行查询时，会自动创建与输入参数对应的报表参数。</span><span class="sxs-lookup"><span data-stu-id="15901-164">When you run the query, report parameters that correspond to input parameters are automatically created.</span></span> <span data-ttu-id="15901-165">有关详细信息，请参阅本主题后面的 [查询参数](#Parameters) 。</span><span class="sxs-lookup"><span data-stu-id="15901-165">For more information, see [Query Parameters](#Parameters) later in this topic.</span></span>  
  
 <span data-ttu-id="15901-166">仅支持为存储过程检索到的第一个结果集。</span><span class="sxs-lookup"><span data-stu-id="15901-166">Only the first result set that is retrieved for a stored procedure is supported.</span></span> <span data-ttu-id="15901-167">如果存储过程返回多个结果集，则仅使用第一个结果集。</span><span class="sxs-lookup"><span data-stu-id="15901-167">If a stored procedure returns multiple result sets, only the first one is used.</span></span>  
  
 <span data-ttu-id="15901-168">如果某个存储过程带有具有默认值的参数，则您可以访问该值，方法是使用 DEFAULT 关键字作为该参数的值。</span><span class="sxs-lookup"><span data-stu-id="15901-168">If a stored procedure has a parameter that has a default value, you can access that value by using the DEFAULT keyword as a value for the parameter.</span></span> <span data-ttu-id="15901-169">如果该查询参数链接到某个报表参数，用户可以在报表参数的输入框中键入或选择单词 DEFAULT。</span><span class="sxs-lookup"><span data-stu-id="15901-169">If the query parameter is linked to a report parameter, the user can type or select the word DEFAULT in the input box for the report parameter.</span></span>  
  
 <span data-ttu-id="15901-170">有关详细信息，请参阅 msdn.microsoft.com 上 [SQL Server 联机丛书](https://go.microsoft.com/fwlink/?linkid=98335) 中的“存储过程（数据库引擎）”。</span><span class="sxs-lookup"><span data-stu-id="15901-170">For more information, see "Stored Procedures (Database Engine)" in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=98335) on msdn.microsoft.com.</span></span>  
  
  
##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="15901-171">Parameters</span><span class="sxs-lookup"><span data-stu-id="15901-171">Parameters</span></span>  
 <span data-ttu-id="15901-172">如果查询文本包含查询变量或具有输入参数的存储过程，则将自动生成数据集的对应查询参数和报表的报表参数。</span><span class="sxs-lookup"><span data-stu-id="15901-172">When query text contains query variables or stored procedures that have input parameters, the corresponding query parameters for the dataset and report parameters for the report are automatically generated.</span></span> <span data-ttu-id="15901-173">查询文本不得包含针对每个查询变量的 DECLARE 语句。</span><span class="sxs-lookup"><span data-stu-id="15901-173">The query text must not include the DECLARE statement for each query variable.</span></span>  
  
 <span data-ttu-id="15901-174">例如，下面的 SQL 查询将创建一个名为 `EmpID` 的报表参数：</span><span class="sxs-lookup"><span data-stu-id="15901-174">For example, the following SQL query creates a report parameter named `EmpID`:</span></span>  
  
```  
SELECT FirstName, LastName FROM HumanResources.Employee E INNER JOIN  
       Person.Contact C ON  E.ContactID=C.ContactID   
WHERE EmployeeID = (@EmpID)  
```  
  
 <span data-ttu-id="15901-175">报表参数是用可能需要修改的默认属性值创建的。</span><span class="sxs-lookup"><span data-stu-id="15901-175">Report parameters are created with default property values that you might need to modify.</span></span> <span data-ttu-id="15901-176">例如：</span><span class="sxs-lookup"><span data-stu-id="15901-176">For example:</span></span>  
  
-   <span data-ttu-id="15901-177">默认情况下，每个报表参数的数据类型均为 **Text**。</span><span class="sxs-lookup"><span data-stu-id="15901-177">By default, each report parameter is data type **Text**.</span></span> <span data-ttu-id="15901-178">如果基础数据属于其他数据类型，则必须更改参数的数据类型。</span><span class="sxs-lookup"><span data-stu-id="15901-178">If the underlying data is a different data type, you must change the parameter data type.</span></span>  
  
-   <span data-ttu-id="15901-179">如果选择多值参数选项，您必须手动更改查询，使用 `IN` 运算符（如 `WHERE EmployeeID IN (@EmpID)`）测试这些值是否属于集的一部分。</span><span class="sxs-lookup"><span data-stu-id="15901-179">If you select the option for multivalued parameters, you must manually change the query to test whether values are part of a set by using the `IN` operator, for example, `WHERE EmployeeID IN (@EmpID)`.</span></span>  
  
 <span data-ttu-id="15901-180">有关详细信息，请参阅 [报表参数（报表生成器和报表设计器）](../report-design/report-parameters-report-builder-and-report-designer.md)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="15901-180">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="15901-181">注释</span><span class="sxs-lookup"><span data-stu-id="15901-181">Remarks</span></span>  
 <span data-ttu-id="15901-182">您还可以通过使用 OLE DB 或 ODBC 数据源类型从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中检索数据。</span><span class="sxs-lookup"><span data-stu-id="15901-182">You can also retrieve data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database by using an OLE DB or ODBC data source type.</span></span> <span data-ttu-id="15901-183">有关详细信息，请参阅 [OLE DB 连接类型 (SSRS)](ole-db-connection-type-ssrs.md) 或 [ODBC 连接类型 (SSRS)](odbc-connection-type-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="15901-183">For more information, see [OLE DB Connection Type &#40;SSRS&#41;](ole-db-connection-type-ssrs.md) or [ODBC Connection Type &#40;SSRS&#41;](odbc-connection-type-ssrs.md).</span></span>  
  
###### <a name="platform-and-version-information"></a><span data-ttu-id="15901-184">平台和版本信息</span><span class="sxs-lookup"><span data-stu-id="15901-184">Platform and Version Information</span></span>  
 <span data-ttu-id="15901-185">有关平台和版本支持的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [联机丛书](https://go.microsoft.com/fwlink/?linkid=121312)的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 文档中的 [Reporting Services 支持的数据源 (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="15901-185">For more information about platform and version support, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a> <span data-ttu-id="15901-186">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="15901-186">How-To Topics</span></span>  
 <span data-ttu-id="15901-187">本节包含使用数据连接、数据源和数据集的分步说明。</span><span class="sxs-lookup"><span data-stu-id="15901-187">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="15901-188">添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="15901-188">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="15901-189">创建共享数据集或嵌入数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="15901-189">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="15901-190">向数据集添加筛选器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="15901-190">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="15901-191">相关章节</span><span class="sxs-lookup"><span data-stu-id="15901-191">Related Sections</span></span>  
 <span data-ttu-id="15901-192">文档中的这些章节提供有关报表数据的深入概念性信息，以及有关如何定义、自定义和使用与数据相关的报表部件的步骤信息。</span><span class="sxs-lookup"><span data-stu-id="15901-192">These sections of the documentation provide in-depth conceptual information about report data, and procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="15901-193">将数据添加到报表 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="15901-193">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="15901-194">提供访问报表数据的概述。</span><span class="sxs-lookup"><span data-stu-id="15901-194">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="15901-195">报表生成器中的数据连接、数据源和连接字符串</span><span class="sxs-lookup"><span data-stu-id="15901-195">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="15901-196">提供有关数据连接和数据源的信息。</span><span class="sxs-lookup"><span data-stu-id="15901-196">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="15901-197">报表的嵌入数据集和共享数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="15901-197">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="15901-198">提供有关嵌入数据集和共享数据集的信息。</span><span class="sxs-lookup"><span data-stu-id="15901-198">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="15901-199">数据集字段集合（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="15901-199">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="15901-200">提供有关查询生成的数据集字段集合的信息。</span><span class="sxs-lookup"><span data-stu-id="15901-200">Provides information about the dataset field collection generated by the query.</span></span>  
  
 <span data-ttu-id="15901-201">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [联机丛书](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 文档中的 [Reporting Services 支持的数据源 (SSRS) ](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="15901-201">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="15901-202">提供有关每个数据扩展插件的平台和版本支持的详细信息。</span><span class="sxs-lookup"><span data-stu-id="15901-202">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="15901-203">另请参阅</span><span class="sxs-lookup"><span data-stu-id="15901-203">See Also</span></span>  
 <span data-ttu-id="15901-204">[报表参数（报表生成器和报表设计器）](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="15901-204">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="15901-205">[对数据进行筛选、分组和排序（报表生成器和 SSRS）](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="15901-205">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="15901-206">表达式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="15901-206">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
