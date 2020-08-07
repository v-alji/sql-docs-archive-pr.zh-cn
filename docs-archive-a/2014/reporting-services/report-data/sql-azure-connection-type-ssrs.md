---
title: SQL Azure 连接类型 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c84def6c-e8cf-43d9-9912-098171a7ce79
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e2c3d3e75117996f088cff96b2b7a8d4cd504127
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588930"
---
# <a name="sql-azure-connection-type-ssrs"></a><span data-ttu-id="4f023-102">SQL Azure 连接类型 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="4f023-102">SQL Azure Connection Type (SSRS)</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="4f023-103">[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]是基于云的托管关系数据库，是基于技术构建的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4f023-103">[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] is a cloud-based, hosted relational database built on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technologies.</span></span> <span data-ttu-id="4f023-104">若要在报表中包括来自 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 的数据，您必须有一个基于 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]类型的报表数据源的数据集。</span><span class="sxs-lookup"><span data-stu-id="4f023-104">To include data from [!INCLUDE[ssSDS](../../includes/sssds-md.md)] in your report, you must have a dataset that is based on a report data source of type [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span> <span data-ttu-id="4f023-105">此内置数据源类型基于 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 数据扩展插件。</span><span class="sxs-lookup"><span data-stu-id="4f023-105">This built-in data source type is based on the [!INCLUDE[ssSDS](../../includes/sssds-md.md)] data extension.</span></span> <span data-ttu-id="4f023-106">使用此数据源类型可连接到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]并从中检索数据。</span><span class="sxs-lookup"><span data-stu-id="4f023-106">Use this data source type to connect to and retrieve data from [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>

 <span data-ttu-id="4f023-107">此数据扩展插件支持多值参数、服务器聚合以及与连接字符串分开管理的凭据。</span><span class="sxs-lookup"><span data-stu-id="4f023-107">This data extension supports multivalued parameters, server aggregates, and credentials managed separately from the connection string.</span></span>

 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] <span data-ttu-id="4f023-108">类似于内部部署的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，并且从 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 中获取数据与从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中获取数据几乎是相同的（有少数例外）。</span><span class="sxs-lookup"><span data-stu-id="4f023-108">is similar to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on your premises and getting data from [!INCLUDE[ssSDS](../../includes/sssds-md.md)] is, with a few exceptions, identical to getting data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>

> [!NOTE]
>  <span data-ttu-id="4f023-109">打开到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]的连接时，将连接超时值设置为 30 秒。</span><span class="sxs-lookup"><span data-stu-id="4f023-109">When opening a connection to a [!INCLUDE[ssSDS](../../includes/sssds-md.md)], set the connection timeout to 30 seconds.</span></span>

 <span data-ttu-id="4f023-110">有关详细信息，请参阅[AZURE SQL 数据库文档](https://docs.microsoft.com/azure/sql-database/)。</span><span class="sxs-lookup"><span data-stu-id="4f023-110">For more information, see [Azure SQL Database Documentation](https://docs.microsoft.com/azure/sql-database/).</span></span>

 <span data-ttu-id="4f023-111">使用本主题中的信息来生成一个数据源。</span><span class="sxs-lookup"><span data-stu-id="4f023-111">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="4f023-112">有关分步说明，请参阅[添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4f023-112">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>

##  <a name="connection-string"></a><a name="Connection"></a><span data-ttu-id="4f023-113">连接字符串</span><span class="sxs-lookup"><span data-stu-id="4f023-113">Connection String</span></span>
 <span data-ttu-id="4f023-114">连接到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]时，也会连接到云中的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="4f023-114">When you connect to [!INCLUDE[ssSDS](../../includes/sssds-md.md)], you are connecting to a database object in the cloud.</span></span> <span data-ttu-id="4f023-115">正如现场数据库一样，托管数据库可能具有包含多个表、视图和存储过程的不同架构。</span><span class="sxs-lookup"><span data-stu-id="4f023-115">Just like onsite databases, the hosted database might have multiple schemas that have multiple tables, views, and stored procedures.</span></span> <span data-ttu-id="4f023-116">可在查询设计器中指定要使用的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="4f023-116">You specify the database object to use in the query designer.</span></span> <span data-ttu-id="4f023-117">如果未在连接字符串中指定数据库，则将连接到管理员为您分配的默认数据库。</span><span class="sxs-lookup"><span data-stu-id="4f023-117">If you do not specify a database in the connection string, you connect to the default database that the administrator assigned to you.</span></span>

 <span data-ttu-id="4f023-118">请联系数据库管理员，获取连接信息以及用于连接到数据源的凭据。</span><span class="sxs-lookup"><span data-stu-id="4f023-118">Contact your database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="4f023-119">下面的连接字符串示例指定一个名为 AdventureWorks 的托管示例数据库。</span><span class="sxs-lookup"><span data-stu-id="4f023-119">The following connection string example specifies a hosted sample database named AdventureWorks.</span></span>

```
Data Source=<host>;Initial Catalog=AdventureWorks; Encrypt=True;
```

 <span data-ttu-id="4f023-120">此外，使用 **“数据源属性”** 对话框还可以提供凭据，如用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="4f023-120">In addition, you use the **Data Sources Properties** dialog box to provide credentials such as user name and password.</span></span> <span data-ttu-id="4f023-121">`User Id` 和 `Password` 选项自动追加到连接字符串；您无需将它们作为连接字符串的一部分键入其中。</span><span class="sxs-lookup"><span data-stu-id="4f023-121">The `User Id` and `Password` options are automatically appended to the connection string; you do not need to type them as part of the connection string.</span></span>

 <span data-ttu-id="4f023-122">有关连接字符串示例的详细信息，请参阅 [报表生成器中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="4f023-122">For more information and connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>

##  <a name="credentials"></a><a name="Credentials"></a><span data-ttu-id="4f023-123">凭据</span><span class="sxs-lookup"><span data-stu-id="4f023-123">Credentials</span></span>
 <span data-ttu-id="4f023-124">不支持 Windows 身份验证（集成安全性）。</span><span class="sxs-lookup"><span data-stu-id="4f023-124">Windows Authentication (integrated security) is not supported.</span></span> <span data-ttu-id="4f023-125">如果试图使用 Windows 身份验证连接到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ，则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="4f023-125">If you attempt to connect to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] using Windows Authentication an error occurs.</span></span> [!INCLUDE[ssSDS](../../includes/sssds-md.md)] <span data-ttu-id="4f023-126">仅支持 SQL Server 身份验证（用户名和密码），并且在每次连接到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]时，用户都必须提供凭据（登录名和密码）。</span><span class="sxs-lookup"><span data-stu-id="4f023-126">supports only SQL Server Authentication (user name and password) and users must provide credentials (login and password) every time they connect to [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>

 <span data-ttu-id="4f023-127">凭据必须具有足够的权限访问数据库。</span><span class="sxs-lookup"><span data-stu-id="4f023-127">Credentials must be sufficient to access the database.</span></span> <span data-ttu-id="4f023-128">根据要执行的查询，您可能需要具有其他权限，例如运行存储过程和访问表和视图的足够权限。</span><span class="sxs-lookup"><span data-stu-id="4f023-128">Depending on your query, you might need other permissions, such as sufficient permissions to run stored procedures and access tables and views.</span></span> <span data-ttu-id="4f023-129">外部数据源的所有者必须配置相应的凭据，使这些凭据足以提供对所需数据库对象的只读访问。</span><span class="sxs-lookup"><span data-stu-id="4f023-129">The owner of the external data source must configure credentials that are sufficient to provide read-only access to the database objects that you need.</span></span>

 <span data-ttu-id="4f023-130">在报表创作客户端，可以使用下列选项指定凭据：</span><span class="sxs-lookup"><span data-stu-id="4f023-130">From a report authoring client, the following options are available to specify credentials:</span></span>

-   <span data-ttu-id="4f023-131">使用存储的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="4f023-131">Use a stored user name and password.</span></span> <span data-ttu-id="4f023-132">若要协商当包含报表数据的数据库与报表服务器不同时产生的双跃点，请选择使用凭据作为 Windows 凭据的选项。</span><span class="sxs-lookup"><span data-stu-id="4f023-132">To negotiate the double hop that occurs when the database that contains the report data is different than the report server, select options to use credentials as Windows credentials.</span></span> <span data-ttu-id="4f023-133">也可以选择在连接到数据源后模拟经过身份验证的用户。</span><span class="sxs-lookup"><span data-stu-id="4f023-133">You can also chose to impersonate the authenticated user after connecting to the data source.</span></span>

-   <span data-ttu-id="4f023-134">不需要提供任何凭据。</span><span class="sxs-lookup"><span data-stu-id="4f023-134">No credentials are required.</span></span> <span data-ttu-id="4f023-135">若要使用此选项，您必须具有为报表服务器配置的无人参与的执行帐户。</span><span class="sxs-lookup"><span data-stu-id="4f023-135">To use this option, you must have the unattended execution account configured on the report server.</span></span> <span data-ttu-id="4f023-136">有关详细信息，请参阅 msdn.microsoft.com 上 [Reporting Services 文档](https://go.microsoft.com/fwlink/?linkid=121312)中的[配置无人参与的执行帐户（SSRS 配置管理器）](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="4f023-136">For more information, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in on msdn.microsoft.com.</span></span>

 <span data-ttu-id="4f023-137">有关详细信息，请参阅[Reporting Services 中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)或[在报表生成器中指定凭据](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="4f023-137">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>

 

##  <a name="queries"></a><a name="Query"></a><span data-ttu-id="4f023-138">请求</span><span class="sxs-lookup"><span data-stu-id="4f023-138">Queries</span></span>
 <span data-ttu-id="4f023-139">查询指定了要为报表数据集检索哪些数据。</span><span class="sxs-lookup"><span data-stu-id="4f023-139">A query specifies which data to retrieve for a report dataset.</span></span> <span data-ttu-id="4f023-140">查询的结果集中的列填充数据集的字段集合。</span><span class="sxs-lookup"><span data-stu-id="4f023-140">The columns in the result set for a query populate the field collection for a dataset.</span></span> <span data-ttu-id="4f023-141">如果查询返回多个结果集，则报表仅处理查询所检索的第一个结果集。</span><span class="sxs-lookup"><span data-stu-id="4f023-141">If the query returns multiple result sets, the report processes only the first result set that the query retrieves.</span></span> <span data-ttu-id="4f023-142">尽管 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]之间存在一些差别（如所支持的数据库大小），但根据 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]编写查询类似于根据 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库编写查询。</span><span class="sxs-lookup"><span data-stu-id="4f023-142">Although there are some differences between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssSDS](../../includes/sssds-md.md)]s such as the sizes of databases supported, writing queries against [!INCLUDE[ssSDS](../../includes/sssds-md.md)]s is similar to writing queries against [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span> <span data-ttu-id="4f023-143">有些 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句（如 BACKUP）在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]中不受支持，但在报表查询中是不会使用这些语句的。</span><span class="sxs-lookup"><span data-stu-id="4f023-143">Some [!INCLUDE[tsql](../../includes/tsql-md.md)] statements such as BACKUP are not supported in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], but they are not ones that you use in report queries.</span></span> <span data-ttu-id="4f023-144">有关详细信息，请参阅 [SQL Server 连接类型 (SSRS)](sql-server-connection-type-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4f023-144">For more information, see [SQL Server Connection Type &#40;SSRS&#41;](sql-server-connection-type-ssrs.md).</span></span>

 <span data-ttu-id="4f023-145">默认情况下，如果您创建一个新查询，或者打开一个可在图形查询设计器中显示的现有查询，则可以使用关系查询设计器。</span><span class="sxs-lookup"><span data-stu-id="4f023-145">By default, if you create a new query or open an existing query that can be represented in the graphical query designer, the relational query designer is available.</span></span> <span data-ttu-id="4f023-146">可以通过下列方式指定查询：</span><span class="sxs-lookup"><span data-stu-id="4f023-146">You can specify a query in the following ways:</span></span>

-   <span data-ttu-id="4f023-147">以交互方式生成查询。</span><span class="sxs-lookup"><span data-stu-id="4f023-147">Build a query interactively.</span></span> <span data-ttu-id="4f023-148">使用关系查询设计器，此设计器显示表、视图、存储过程及其他数据库项按数据库架构组织的层次结构视图。</span><span class="sxs-lookup"><span data-stu-id="4f023-148">Use the relational query designer that displays a hierarchical view of tables, views, stored procedures, and other database items, organized by database schema.</span></span> <span data-ttu-id="4f023-149">选择表或视图中的列，或者指定存储过程或表值函数。</span><span class="sxs-lookup"><span data-stu-id="4f023-149">Select columns from tables or views, or specify stored procedures or table-valued functions.</span></span> <span data-ttu-id="4f023-150">通过指定筛选条件限制要检索的数据行数。</span><span class="sxs-lookup"><span data-stu-id="4f023-150">Limit the number of rows of data to retrieve by specifying filter criteria.</span></span> <span data-ttu-id="4f023-151">通过设置参数选项自定义报表运行时的筛选器。</span><span class="sxs-lookup"><span data-stu-id="4f023-151">Customize the filter when the report runs by setting the parameter option.</span></span>

-   <span data-ttu-id="4f023-152">键入或粘贴查询。</span><span class="sxs-lookup"><span data-stu-id="4f023-152">Type or paste a query.</span></span> <span data-ttu-id="4f023-153">使用基于文本的查询设计器直接输入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 文本、粘贴来自其他来源的查询文本、输入使用关系查询设计器无法生成的复杂查询，或输入基于查询的表达式。</span><span class="sxs-lookup"><span data-stu-id="4f023-153">Use the text-based query designer to enter [!INCLUDE[tsql](../../includes/tsql-md.md)] text directly, to paste query text from another source, to enter complex queries that cannot be built by using the relational query designer, or to enter query-based expressions.</span></span>

-   <span data-ttu-id="4f023-154">从文件或报表中导入现有的查询。</span><span class="sxs-lookup"><span data-stu-id="4f023-154">Import an existing query from a file or report.</span></span> <span data-ttu-id="4f023-155">使用任一查询设计器中的 **“导入查询”** 按钮浏览到 .sql 文件或 .rdl 文件，然后导入查询。</span><span class="sxs-lookup"><span data-stu-id="4f023-155">Use the **Import** query button from either query designer to browse to a .sql file or .rdl file and import a query.</span></span>

 <span data-ttu-id="4f023-156">基于文本的查询设计器支持以下两种模式：</span><span class="sxs-lookup"><span data-stu-id="4f023-156">The text-based query designer supports the following two modes:</span></span>

-   <span data-ttu-id="4f023-157">[文本](#QueryText) 键入用于从数据源选择数据的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令。</span><span class="sxs-lookup"><span data-stu-id="4f023-157">[Text](#QueryText) Type [!INCLUDE[tsql](../../includes/tsql-md.md)] commands that select data from the data source.</span></span>

-   <span data-ttu-id="4f023-158">[存储过程](#QueryStoredProcedure) 从存储过程的列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="4f023-158">[Stored Procedure](#QueryStoredProcedure) Choose from a list of stored procedures.</span></span>

 <span data-ttu-id="4f023-159">有关详细信息，请参阅[关系查询设计器用户界面（报表生成器）](relational-query-designer-user-interface-report-builder.md)和[基于文本的查询设计器用户界面（报表生成器）](text-based-query-designer-user-interface-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="4f023-159">For more information, see [Relational Query Designer User Interface &#40;Report Builder&#41;](relational-query-designer-user-interface-report-builder.md) and [Text-based Query Designer User Interface &#40;Report Builder&#41;](text-based-query-designer-user-interface-report-builder.md).</span></span>

 <span data-ttu-id="4f023-160">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 使用的图形查询设计器提供对分组和聚合的内置支持，可帮助你编写仅检索摘要数据的查询。</span><span class="sxs-lookup"><span data-stu-id="4f023-160">The graphical query designer that [!INCLUDE[ssSDS](../../includes/sssds-md.md)] uses provides built-in support for grouping and aggregates to help you write queries that retrieve only summary data.</span></span> <span data-ttu-id="4f023-161">[!INCLUDE[tsql](../../includes/tsql-md.md)] 语言功能包括：GROUP BY 子句、DISTINCT 关键字以及 SUM 和 COUNT 等聚合。</span><span class="sxs-lookup"><span data-stu-id="4f023-161">The [!INCLUDE[tsql](../../includes/tsql-md.md)] language features are: the GROUP BY clause, DISTINCT keyword, and aggregates such as SUM and COUNT.</span></span> <span data-ttu-id="4f023-162">基于文本的查询设计器提供对 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语言的完全支持，包括分组和聚合。</span><span class="sxs-lookup"><span data-stu-id="4f023-162">The text-based query designer provides full support for the [!INCLUDE[tsql](../../includes/tsql-md.md)] language, including grouping and aggregates.</span></span> <span data-ttu-id="4f023-163">有关 [!INCLUDE[tsql](../../includes/tsql-md.md)] 的详细信息，请参阅 msdn.microsoft.com 上 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [联机丛书](https://go.microsoft.com/fwlink/?LinkId=141687)中的 [Transact-SQL 引用（数据库引擎）](/sql/t-sql/language-reference)。</span><span class="sxs-lookup"><span data-stu-id="4f023-163">For more information about [!INCLUDE[tsql](../../includes/tsql-md.md)], see [Transact-SQL Reference &#40;Database Engine&#41;](/sql/t-sql/language-reference)in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=141687) on msdn.microsoft.com.</span></span>

###  <a name="using-query-type-text"></a><a name="QueryText"></a><span data-ttu-id="4f023-164">使用查询类型文本</span><span class="sxs-lookup"><span data-stu-id="4f023-164">Using Query Type Text</span></span>
 <span data-ttu-id="4f023-165">在基于文本的查询设计器中，可以键入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令来定义数据集中的数据。</span><span class="sxs-lookup"><span data-stu-id="4f023-165">In the text-based query designer, you type [!INCLUDE[tsql](../../includes/tsql-md.md)] commands to define the data in a dataset.</span></span> <span data-ttu-id="4f023-166">例如，下面的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询选择职位为销售助理的所有雇员的姓名：</span><span class="sxs-lookup"><span data-stu-id="4f023-166">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] query selects the names of all employees who are marketing assistants:</span></span>

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

 <span data-ttu-id="4f023-167">单击工具栏上的 **“运行”** 按钮 (**!**) 可以运行查询并显示结果集。</span><span class="sxs-lookup"><span data-stu-id="4f023-167">Click the **Run** button (**!**) on the toolbar to run the query and display a result set.</span></span>

 <span data-ttu-id="4f023-168">若要参数化此查询，请添加一个查询参数。</span><span class="sxs-lookup"><span data-stu-id="4f023-168">To parameterize this query, add a query parameter.</span></span> <span data-ttu-id="4f023-169">例如，将 WHERE 子句更改为下面的内容：</span><span class="sxs-lookup"><span data-stu-id="4f023-169">For example, change the WHERE clause to the following:</span></span>

```
WHERE HumanResources.Employee.JobTitle = (@JobTitle)
```

 <span data-ttu-id="4f023-170">运行查询时，会自动创建与查询参数对应的报表参数。</span><span class="sxs-lookup"><span data-stu-id="4f023-170">When you run the query, report parameters that correspond to query parameters are automatically created.</span></span> <span data-ttu-id="4f023-171">有关详细信息，请参阅本主题后面的 [查询参数](#Parameters) 。</span><span class="sxs-lookup"><span data-stu-id="4f023-171">For more information, see [Query Parameters](#Parameters) later in this topic.</span></span>



###  <a name="using-query-type-storedprocedure"></a><a name="QueryStoredProcedure"></a><span data-ttu-id="4f023-172">使用查询类型 StoredProcedure</span><span class="sxs-lookup"><span data-stu-id="4f023-172">Using Query Type StoredProcedure</span></span>
 <span data-ttu-id="4f023-173">您可以采用以下方式之一为数据集查询指定存储过程：</span><span class="sxs-lookup"><span data-stu-id="4f023-173">You can specify a stored procedure for a dataset query in one of the following ways:</span></span>

-   <span data-ttu-id="4f023-174">在 **“数据集属性”** 对话框中，设置 **“存储过程”** 选项。</span><span class="sxs-lookup"><span data-stu-id="4f023-174">In the **Dataset Properties** dialog box, set the **Stored Procedure** option.</span></span> <span data-ttu-id="4f023-175">从存储过程和表值函数的下拉列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="4f023-175">Choose from the drop-down list of stored procedures and table-valued functions.</span></span>

-   <span data-ttu-id="4f023-176">在关系查询设计器中的“数据库视图”窗格中，选择存储过程或表值函数。</span><span class="sxs-lookup"><span data-stu-id="4f023-176">In the relational query designer, in the Database view pane, select a stored procedure or table-valued function.</span></span>

-   <span data-ttu-id="4f023-177">在基于文本的查询设计器中，从工具栏中选择 **StoredProcedure** 。</span><span class="sxs-lookup"><span data-stu-id="4f023-177">In the text-based query designer, select **StoredProcedure** from the toolbar.</span></span>

 <span data-ttu-id="4f023-178">选择存储过程或表值函数之后，就可以运行查询。</span><span class="sxs-lookup"><span data-stu-id="4f023-178">After you select a stored procedure or table-valued function, you can run the query.</span></span> <span data-ttu-id="4f023-179">系统将提示您提供输入参数的值。</span><span class="sxs-lookup"><span data-stu-id="4f023-179">You will be prompted for input parameter values.</span></span> <span data-ttu-id="4f023-180">运行查询时，会自动创建与输入参数对应的报表参数。</span><span class="sxs-lookup"><span data-stu-id="4f023-180">When you run the query, report parameters that correspond to input parameters are automatically created.</span></span> <span data-ttu-id="4f023-181">有关详细信息，请参阅本主题后面的 [查询参数](#Parameters) 。</span><span class="sxs-lookup"><span data-stu-id="4f023-181">For more information, see [Query Parameters](#Parameters) later in this topic.</span></span>

 <span data-ttu-id="4f023-182">仅支持为存储过程检索到的第一个结果集。</span><span class="sxs-lookup"><span data-stu-id="4f023-182">Only the first result set that is retrieved for a stored procedure is supported.</span></span> <span data-ttu-id="4f023-183">如果存储过程返回多个结果集，则仅使用第一个结果集。</span><span class="sxs-lookup"><span data-stu-id="4f023-183">If a stored procedure returns multiple result sets, only the first one is used.</span></span>

 <span data-ttu-id="4f023-184">如果某个存储过程带有具有默认值的参数，则您可以访问该值，方法是使用 DEFAULT 关键字作为该参数的值。</span><span class="sxs-lookup"><span data-stu-id="4f023-184">If a stored procedure has a parameter that has a default value, you can access that value by using the DEFAULT keyword as a value for the parameter.</span></span> <span data-ttu-id="4f023-185">如果该查询参数链接到某个报表参数，用户可以在报表参数的输入框中键入或选择单词 DEFAULT。</span><span class="sxs-lookup"><span data-stu-id="4f023-185">If the query parameter is linked to a report parameter, the user can type or select the word DEFAULT in the input box for the report parameter.</span></span>

 <span data-ttu-id="4f023-186">有关存储过程的详细信息，请参阅 msdn.microsoft.com 上 [SQL Server 联机丛书](https://go.microsoft.com/fwlink/?linkid=98335) 中的“存储过程（数据库引擎）”。</span><span class="sxs-lookup"><span data-stu-id="4f023-186">For more information about stored procedures, see "Stored Procedures (Database Engine)" in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=98335) on msdn.microsoft.com.</span></span>



##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="4f023-187">Parameters</span><span class="sxs-lookup"><span data-stu-id="4f023-187">Parameters</span></span>
 <span data-ttu-id="4f023-188">如果查询文本包含查询变量或具有输入参数的存储过程，则将自动生成数据集的对应查询参数和报表的报表参数。</span><span class="sxs-lookup"><span data-stu-id="4f023-188">When query text contains query variables or stored procedures that have input parameters, the corresponding query parameters for the dataset and report parameters for the report are automatically generated.</span></span> <span data-ttu-id="4f023-189">查询文本不得包含针对每个查询变量的 DECLARE 语句。</span><span class="sxs-lookup"><span data-stu-id="4f023-189">The query text must not include the DECLARE statement for each query variable.</span></span>

 <span data-ttu-id="4f023-190">例如，下面的 SQL 查询将创建一个名为 `EmpID` 的报表参数：</span><span class="sxs-lookup"><span data-stu-id="4f023-190">For example, the following SQL query creates a report parameter named `EmpID`:</span></span>

```
SELECT FirstName, LastName FROM HumanResources.Employee E INNER JOIN
       Person.Contact C ON  E.ContactID=C.ContactID 
WHERE EmployeeID = (@EmpID)
```

 <span data-ttu-id="4f023-191">默认情况下，各个报表参数的数据类型均为“Text”，并具有自动创建的数据集，以提供可用值的下拉列表。</span><span class="sxs-lookup"><span data-stu-id="4f023-191">By default, each report parameter has data type Text and an automatically created dataset to provide a drop-down list of available values.</span></span> <span data-ttu-id="4f023-192">创建报表参数后，您可能需要更改默认值。</span><span class="sxs-lookup"><span data-stu-id="4f023-192">After the report parameters are created, you might have to change default values.</span></span> <span data-ttu-id="4f023-193">有关详细信息，请参阅 [报表参数（报表生成器和报表设计器）](../report-design/report-parameters-report-builder-and-report-designer.md)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="4f023-193">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>



##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="4f023-194">注释</span><span class="sxs-lookup"><span data-stu-id="4f023-194">Remarks</span></span>

###### <a name="alternate-data-extensions"></a><span data-ttu-id="4f023-195">备用数据扩展插件</span><span class="sxs-lookup"><span data-stu-id="4f023-195">Alternate Data Extensions</span></span>
 <span data-ttu-id="4f023-196">您还可以通过使用 ODBC 数据源类型从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中检索数据。</span><span class="sxs-lookup"><span data-stu-id="4f023-196">You can also retrieve data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database by using an ODBC data source type.</span></span> <span data-ttu-id="4f023-197">不支持使用 OLE DB 连接到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4f023-197">Connecting to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] by using OLE DB is not supported.</span></span>

 <span data-ttu-id="4f023-198">有关详细信息，请参阅 [ODBC 连接类型 (SSRS)](odbc-connection-type-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4f023-198">For more information, see [ODBC Connection Type &#40;SSRS&#41;](odbc-connection-type-ssrs.md).</span></span>

###### <a name="platform-and-version-information"></a><span data-ttu-id="4f023-199">平台和版本信息</span><span class="sxs-lookup"><span data-stu-id="4f023-199">Platform and Version Information</span></span>
 <span data-ttu-id="4f023-200">有关平台和版本支持的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [联机丛书](https://go.microsoft.com/fwlink/?linkid=121312)的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 文档中的 [Reporting Services 支持的数据源 (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="4f023-200">For more information about platform and version support, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>



##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="4f023-201">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="4f023-201">How-To Topics</span></span>
 <span data-ttu-id="4f023-202">本节包含使用数据连接、数据源和数据集的分步说明。</span><span class="sxs-lookup"><span data-stu-id="4f023-202">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>

 [<span data-ttu-id="4f023-203">添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4f023-203">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)

 [<span data-ttu-id="4f023-204">创建共享数据集或嵌入数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4f023-204">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)

 [<span data-ttu-id="4f023-205">向数据集添加筛选器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4f023-205">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)



##  <a name="related-sections"></a><a name="Related"></a><span data-ttu-id="4f023-206">相关部分</span><span class="sxs-lookup"><span data-stu-id="4f023-206">Related Sections</span></span>
 <span data-ttu-id="4f023-207">文档中的这些章节提供有关报表数据的深入概念性信息，以及有关如何定义、自定义和使用与数据相关的报表部件的步骤信息。</span><span class="sxs-lookup"><span data-stu-id="4f023-207">These sections of the documentation provide in-depth conceptual information about report data, and procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>

 <span data-ttu-id="4f023-208">[将数据添加到报表 &#40;报表生成器和 SSRS&#41;](report-datasets-ssrs.md)提供访问报表数据的概述。</span><span class="sxs-lookup"><span data-stu-id="4f023-208">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) Provides an overview of accessing data for your report.</span></span>

 <span data-ttu-id="4f023-209">[报表生成器中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)提供有关数据连接和数据源的信息。</span><span class="sxs-lookup"><span data-stu-id="4f023-209">[Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md) Provides information about data connections and data sources.</span></span>

 <span data-ttu-id="4f023-210">[报表嵌入数据集和共享数据集 &#40;报表生成器和 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)提供有关嵌入数据集和共享数据集的信息。</span><span class="sxs-lookup"><span data-stu-id="4f023-210">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) Provides information about embedded and shared datasets.</span></span>

 <span data-ttu-id="4f023-211">[数据集字段集合 &#40;报表生成器和 SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)提供有关查询生成的数据集字段集合的信息。</span><span class="sxs-lookup"><span data-stu-id="4f023-211">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) Provides information about the dataset field collection generated by the query.</span></span>

 <span data-ttu-id="4f023-212">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [联机丛书](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 文档中的 [Reporting Services 支持的数据源 (SSRS) ](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="4f023-212">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>
<span data-ttu-id="4f023-213">提供有关每个数据扩展插件的平台和版本支持的详细信息。</span><span class="sxs-lookup"><span data-stu-id="4f023-213">Provides in-depth information about platform and version support for each data extension.</span></span>



## <a name="see-also"></a><span data-ttu-id="4f023-214">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4f023-214">See Also</span></span>
 <span data-ttu-id="4f023-215">[报表参数 &#40;报表生成器和报表设计器&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) [对数据进行筛选、分组和排序 &#40;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)报表生成器和 ssrs&#41;&#40;报表生成器[和 ssrs](../report-design/expressions-report-builder-and-ssrs.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="4f023-215">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) [Expressions &#40;Report Builder and SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)</span></span>


