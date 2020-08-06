---
title: OLE DB 源 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbsource.f1
helpviewer_keywords:
- sources [Integration Services], OLE DB
- OLE DB source [Integration Services]
ms.assetid: f87cc5f6-b078-40f3-9d87-7a65e13e4c86
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ce0d2a95639dc31ee8cf4dd9cdaca6844ad4a1d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579672"
---
# <a name="ole-db-source"></a><span data-ttu-id="befa9-102">OLE DB 源</span><span class="sxs-lookup"><span data-stu-id="befa9-102">OLE DB Source</span></span>
  <span data-ttu-id="befa9-103">OLE DB 源通过使用数据库表、视图或 SQL 命令，从各种兼容 OLE DB 的关系数据库中提取数据。</span><span class="sxs-lookup"><span data-stu-id="befa9-103">The OLE DB source extracts data from a variety of OLE DB-compliant relational databases by using a database table, a view, or an SQL command.</span></span> <span data-ttu-id="befa9-104">例如，OLE DB 源可以从 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的表中提取数据。</span><span class="sxs-lookup"><span data-stu-id="befa9-104">For example, the OLE DB source can extract data from tables in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="befa9-105">OLE DB 源提供四种不同数据访问模式用于提取数据：</span><span class="sxs-lookup"><span data-stu-id="befa9-105">The OLE DB source provides four different data access modes for extracting data:</span></span>  
  
-   <span data-ttu-id="befa9-106">表或视图。</span><span class="sxs-lookup"><span data-stu-id="befa9-106">A table or view.</span></span>  
  
-   <span data-ttu-id="befa9-107">变量中指定的表或视图。</span><span class="sxs-lookup"><span data-stu-id="befa9-107">A table or view specified in a variable.</span></span>  
  
-   <span data-ttu-id="befa9-108">SQL 语句的运行结果。</span><span class="sxs-lookup"><span data-stu-id="befa9-108">The results of an SQL statement.</span></span> <span data-ttu-id="befa9-109">查询可以是参数化查询。</span><span class="sxs-lookup"><span data-stu-id="befa9-109">The query can be a parameterized query.</span></span>  
  
-   <span data-ttu-id="befa9-110">存储在变量中的 SQL 语句的运行结果。</span><span class="sxs-lookup"><span data-stu-id="befa9-110">The results of an SQL statement stored in a variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="befa9-111">在您使用 SQL 语句调用从临时表返回结果的某一存储过程时，使用 WITH RESULT SETS 选项可为结果集定义元数据。</span><span class="sxs-lookup"><span data-stu-id="befa9-111">When you use an SQL statement to invoke a stored procedure that returns results from a temporary table, use the WITH RESULT SETS option to define metadata for the result set.</span></span>  
  
 <span data-ttu-id="befa9-112">如果使用参数化查询，则可以将变量映射到参数，以便在 SQL 语句中指定单个参数的值。</span><span class="sxs-lookup"><span data-stu-id="befa9-112">If you use a parameterized query, you can map variables to parameters to specify the values for individual parameters in the SQL statements.</span></span>  
  
 <span data-ttu-id="befa9-113">这个源使用 OLE DB 连接管理器连接到数据源，而该连接管理器则指定要使用的 OLE DB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="befa9-113">This source uses an OLE DB connection manager to connect to a data source, and the connection manager specifies the OLE DB provider to use.</span></span> <span data-ttu-id="befa9-114">有关详细信息，请参阅 [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="befa9-114">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="befa9-115">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目也提供可据以创建 OLE DB 连接管理器的数据源对象，从而使 OLE DB 源可以使用数据源和数据源视图。</span><span class="sxs-lookup"><span data-stu-id="befa9-115">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project also provides the data source object from which you can create an OLE DB connection manager, making data sources and data source views available to the OLE DB source.</span></span>  
  
 <span data-ttu-id="befa9-116">根据不同的 OLE DB 访问接口，对 OLE DB 源存在一些限制：</span><span class="sxs-lookup"><span data-stu-id="befa9-116">Depending on the OLE DB provider, some limitations apply to the OLE DB source:</span></span>  
  
-   <span data-ttu-id="befa9-117">[!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Oracle 不支持 Oracle 数据类型 BLOB、CLOB、NCLOB、BFILE 或 UROWID，因此，OLE DB 源不能从包含这些数据类型列的表中提取数据。</span><span class="sxs-lookup"><span data-stu-id="befa9-117">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB provider for Oracle does not support the Oracle data types BLOB, CLOB, NCLOB, BFILE, OR UROWID, and the OLE DB source cannot extract data from tables that contain columns with these data types.</span></span>  
  
-   <span data-ttu-id="befa9-118">IBM OLE DB DB2 访问接口和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB DB2 访问接口不支持使用调用存储过程的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="befa9-118">The IBM OLE DB DB2 provider and [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB DB2 provider do not support using an SQL command that calls a stored procedure.</span></span> <span data-ttu-id="befa9-119">如果使用这种命令，OLE DB 源将无法创建列元数据，这样一来，数据流中 OLE DB 源之后的数据流组件将没有可用的列数据，从而导致数据流执行失败。</span><span class="sxs-lookup"><span data-stu-id="befa9-119">When this kind of command is used, the OLE DB source cannot create the column metadata and, as a result, the data flow components that follow the OLE DB source in the data flow have no column data available and the execution of the data flow fails.</span></span>  
  
 <span data-ttu-id="befa9-120">OLE DB 源有一个常规输出和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="befa9-120">The OLE DB source has one regular output and one error output.</span></span>  
  
## <a name="using-parameterized-sql-statements"></a><span data-ttu-id="befa9-121">使用参数化 SQL 语句</span><span class="sxs-lookup"><span data-stu-id="befa9-121">Using Parameterized SQL Statements</span></span>  
 <span data-ttu-id="befa9-122">OLE DB 源可以使用 SQL 语句来提取数据。</span><span class="sxs-lookup"><span data-stu-id="befa9-122">The OLE DB source can use an SQL statement to extract data.</span></span> <span data-ttu-id="befa9-123">此语句可以是 SELECT 或 EXEC 语句。</span><span class="sxs-lookup"><span data-stu-id="befa9-123">The statement can be a SELECT or an EXEC statement.</span></span>  
  
 <span data-ttu-id="befa9-124">OLE DB 源使用 OLE DB 连接管理器来连接到它从中提取数据的数据源。</span><span class="sxs-lookup"><span data-stu-id="befa9-124">The OLE DB source uses an OLE DB connection manager to connect to the data source from which it extracts data.</span></span> <span data-ttu-id="befa9-125">取决于 OLE DB 连接管理器所使用的访问接口和连接管理器所连接的关系数据库管理系统 (RDBMS)，参数的命名和列出将应用不同的规则。</span><span class="sxs-lookup"><span data-stu-id="befa9-125">Depending on the provider that the OLE DB connection manager uses and the Relational Database Management System (RDBMS) that the connection manager connects to, different rules apply to the naming and listing of parameters.</span></span> <span data-ttu-id="befa9-126">如果参数名是从 RDBMS 返回的，则可以使用参数名来将参数列表中的参数映射到 SQL 语句中的参数；否则，参数将按它们在参数列表中的序数位置映射到 SQL 语句中的参数。</span><span class="sxs-lookup"><span data-stu-id="befa9-126">If the parameter names are returned from the RDBMS, you can use parameter names to map parameters in a parameter list to parameters in an SQL statement; otherwise, the parameters are mapped to the parameter in the SQL statement by their ordinal position in the parameter list.</span></span> <span data-ttu-id="befa9-127">支持的参数名类型按访问接口而各不相同。</span><span class="sxs-lookup"><span data-stu-id="befa9-127">The types of parameter names that are supported vary by provider.</span></span> <span data-ttu-id="befa9-128">例如，某些访问接口要求使用变量或列名称，而某些访问接口则要求使用诸如 0 或 Param0 这样的符号名称。</span><span class="sxs-lookup"><span data-stu-id="befa9-128">For example, some providers require that you use the variable or column names, whereas some providers require that you use symbolic names such as 0 or Param0.</span></span> <span data-ttu-id="befa9-129">应当参阅访问接口对应的文档，了解有关在 SQL 语句中使用的参数名称的信息。</span><span class="sxs-lookup"><span data-stu-id="befa9-129">You should see the provider-specific documentation for information about the parameter names to use in SQL statements.</span></span>  
  
 <span data-ttu-id="befa9-130">使用 OLE DB 连接管理器时，不能使用参数化子查询，这是因为 OLE DB 源不能通过 OLE DB 访问接口派生参数信息。</span><span class="sxs-lookup"><span data-stu-id="befa9-130">When you are use an OLE DB connection manager, you cannot use parameterized subqueries, because the OLE DB source cannot derive parameter information through the OLE DB provider.</span></span> <span data-ttu-id="befa9-131">但是，可以使用表达式将参数值连接到查询字符串并设置该源的 SqlCommand 属性。在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中，可以使用“OLE DB 源编辑器”对话框配置 OLE DB 源，并在“设置查询参数”对话框中将参数映射到变量。</span><span class="sxs-lookup"><span data-stu-id="befa9-131">However, you can use an expression to concatenate the parameter values into the query string and to set the SqlCommand property of the source.In [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, you configure an OLE DB source by using the **OLE DB Source Editor** dialog box and map the parameters to variables in the **Set Query Parameter** dialog box.</span></span>  
  
### <a name="specifying-parameters-by-using-ordinal-positions"></a><span data-ttu-id="befa9-132">使用序号位置指定参数</span><span class="sxs-lookup"><span data-stu-id="befa9-132">Specifying Parameters by Using Ordinal Positions</span></span>  
 <span data-ttu-id="befa9-133">如果没有返回参数名，则 **“设置查询参数”** 对话框中的 **“参数”** 列表中的参数列出顺序将控制运行时参数将映射哪个参数标记。</span><span class="sxs-lookup"><span data-stu-id="befa9-133">If no parameter names are returned, the order in which the parameters are listed in the **Parameters** list in the **Set Query Parameter** dialog box governs which parameter marker they are mapped to at run time.</span></span> <span data-ttu-id="befa9-134">列表中的第一个参数将映射到 SQL 语句中的第一个 ?，</span><span class="sxs-lookup"><span data-stu-id="befa9-134">The first parameter in the list maps to the first ?</span></span> <span data-ttu-id="befa9-135">第二个参数映射到第二个 ?，以此类推。</span><span class="sxs-lookup"><span data-stu-id="befa9-135">in the SQL statement, the second to the second ?, and so on.</span></span>  
  
 <span data-ttu-id="befa9-136">以下 SQL 语句选择 **数据库的** Product [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] 表中的行。</span><span class="sxs-lookup"><span data-stu-id="befa9-136">The following SQL statement selects rows from the **Product** table in the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] database.</span></span> <span data-ttu-id="befa9-137">**Mappings** 列表中的第一个参数映射到 **Color** 列的第一个参数，第二个参数映射到 **Size** 列。</span><span class="sxs-lookup"><span data-stu-id="befa9-137">The first parameter in the **Mappings** list maps to the first parameter to the **Color** column, the second parameter to the **Size** column.</span></span>  
  
 `SELECT * FROM Production.Product WHERE Color = ? AND Size = ?`  
  
 <span data-ttu-id="befa9-138">参数名不受影响。</span><span class="sxs-lookup"><span data-stu-id="befa9-138">The parameter names have no effect.</span></span> <span data-ttu-id="befa9-139">例如，如果参数与它所应用的列同名，但在 **“参数”** 列表中没有放在正确的序号位置，则在运行时发生的参数映射将使用参数的序号位置，而不是参数名称。</span><span class="sxs-lookup"><span data-stu-id="befa9-139">For example, if a parameter is named the same as the column to which it applies, but not put in the correct ordinal position in the **Parameters** list, the parameter mapping that occurs at run time will use the ordinal position of the parameter, not the parameter name.</span></span>  
  
 <span data-ttu-id="befa9-140">EXEC 命令通常要求在过程中使用提供参数值的变量的名称作为参数名称。</span><span class="sxs-lookup"><span data-stu-id="befa9-140">The EXEC command typically requires that you use the names of the variables that provide parameter values in the procedure as parameter names.</span></span>  
  
### <a name="specifying-parameters-by-using-names"></a><span data-ttu-id="befa9-141">使用名称来指定参数</span><span class="sxs-lookup"><span data-stu-id="befa9-141">Specifying Parameters by Using Names</span></span>  
 <span data-ttu-id="befa9-142">如果实际参数名称是从 RDBMS 返回的，则 SELECT 和 EXEC 语句所使用的参数将按名称进行映射。</span><span class="sxs-lookup"><span data-stu-id="befa9-142">If the actual parameter names are returned from the RDBMS, the parameters used by a SELECT and EXEC statement are mapped by name.</span></span> <span data-ttu-id="befa9-143">参数名称必须与存储过程（由 SELECT 语句或 EXEC 语句运行）所期望的名称匹配。</span><span class="sxs-lookup"><span data-stu-id="befa9-143">The parameter names must match the names that the stored procedure, run by the SELECT statement or the EXEC statement, expects.</span></span>  
  
 <span data-ttu-id="befa9-144">以下 SQL 语句运行 **uspGetWhereUsedProductID** 存储过程（在 [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] 数据库中可用）。</span><span class="sxs-lookup"><span data-stu-id="befa9-144">The following SQL statement runs the **uspGetWhereUsedProductID** stored procedure, available in the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] database.</span></span>  
  
 `EXEC uspGetWhereUsedProductID ?, ?`  
  
 <span data-ttu-id="befa9-145">存储过程希望变量 `@StartProductID` 和 `@CheckDate`提供参数值。</span><span class="sxs-lookup"><span data-stu-id="befa9-145">The stored procedure expects the variables, `@StartProductID` and `@CheckDate`, to provide parameter values.</span></span> <span data-ttu-id="befa9-146">参数出现在 **“映射”** 列表中的顺序是不相关的。</span><span class="sxs-lookup"><span data-stu-id="befa9-146">The order in which the parameters appear in the **Mappings** list is irrelevant.</span></span> <span data-ttu-id="befa9-147">唯一要求是，参数名必须与存储过程中的变量名一致，包括 \@ 符号在内。</span><span class="sxs-lookup"><span data-stu-id="befa9-147">The only requirement is that the parameter names match the variable names in the stored procedure, including the \@ sign.</span></span>  
  
### <a name="mapping-parameters-to-variables"></a><span data-ttu-id="befa9-148">将参数映射到变量</span><span class="sxs-lookup"><span data-stu-id="befa9-148">Mapping Parameters to Variables</span></span>  
 <span data-ttu-id="befa9-149">在运行时参数将映射到提供参数值的变量。</span><span class="sxs-lookup"><span data-stu-id="befa9-149">The parameters are mapped to variables that provide the parameter values at run time.</span></span> <span data-ttu-id="befa9-150">尽管也可以使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 提供的系统变量，但变量通常是用户定义变量。</span><span class="sxs-lookup"><span data-stu-id="befa9-150">The variables are typically user-defined variables, although you can also use the system variables that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides.</span></span> <span data-ttu-id="befa9-151">如果使用用户定义变量，请确保将数据类型设置为与映射参数所引用的列的数据类型相兼容的类型。</span><span class="sxs-lookup"><span data-stu-id="befa9-151">If you use user-defined variables, make sure that you set the data type to a type that is compatible with the data type of the column that the mapped parameter references.</span></span> <span data-ttu-id="befa9-152">有关详细信息，请参阅 [Integration Services (SSIS) 变量](../integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="befa9-152">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
## <a name="troubleshooting-the-ole-db-source"></a><span data-ttu-id="befa9-153">OLE DB 源故障排除</span><span class="sxs-lookup"><span data-stu-id="befa9-153">Troubleshooting the OLE DB Source</span></span>  
 <span data-ttu-id="befa9-154">可以记录 OLE DB 源对外部数据访问接口所做的调用。</span><span class="sxs-lookup"><span data-stu-id="befa9-154">You can log the calls that the OLE DB source makes to external data providers.</span></span> <span data-ttu-id="befa9-155">利用此日志记录功能，可以对 OLE DB 源执行的从外部数据源加载数据的操作进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="befa9-155">You can use this logging capability to troubleshoot the loading of data from external data sources that the OLE DB source performs.</span></span> <span data-ttu-id="befa9-156">若要记录 OLE DB 源对外部数据访问接口所做的调用，请在包级别启用包日志记录并选择 **“诊断”** 事件。</span><span class="sxs-lookup"><span data-stu-id="befa9-156">To log the calls that the OLE DB source makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="befa9-157">有关详细信息，请参阅 [包执行的疑难解答工具](../troubleshooting/troubleshooting-tools-for-package-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="befa9-157">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="configuring-the-ole-db-source"></a><span data-ttu-id="befa9-158">配置 OLE DB 源</span><span class="sxs-lookup"><span data-stu-id="befa9-158">Configuring the OLE DB Source</span></span>  
 <span data-ttu-id="befa9-159">可以采用编程方式或通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器来设置属性。</span><span class="sxs-lookup"><span data-stu-id="befa9-159">You can set properties programmatically or through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="befa9-160">有关可以在 **“OLE DB 源编辑器”** 对话框中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="befa9-160">For more information about the properties that you can set in the **OLE DB Source Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="befa9-161">OLE DB 源编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="befa9-161">OLE DB Source Editor &#40;Connection Manager Page&#41;</span></span>](../ole-db-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="befa9-162">OLE DB 源编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="befa9-162">OLE DB Source Editor &#40;Columns Page&#41;</span></span>](../ole-db-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="befa9-163">OLE DB 源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="befa9-163">OLE DB Source Editor &#40;Error Output Page&#41;</span></span>](../ole-db-source-editor-error-output-page.md)  
  
 <span data-ttu-id="befa9-164">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="befa9-164">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="befa9-165">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="befa9-165">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="befa9-166">Common Properties</span><span class="sxs-lookup"><span data-stu-id="befa9-166">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="befa9-167">OLE DB 自定义属性</span><span class="sxs-lookup"><span data-stu-id="befa9-167">OLE DB Custom Properties</span></span>](ole-db-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="befa9-168">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="befa9-168">Related Tasks</span></span>  
  
-   [<span data-ttu-id="befa9-169">使用 OLE DB 源提取数据</span><span class="sxs-lookup"><span data-stu-id="befa9-169">Extract Data by Using the OLE DB Source</span></span>](ole-db-source.md)  
  
-   [<span data-ttu-id="befa9-170">将查询参数映射到数据流组件中的变量</span><span class="sxs-lookup"><span data-stu-id="befa9-170">Map Query Parameters to Variables in a Data Flow Component</span></span>](map-query-parameters-to-variables-in-a-data-flow-component.md)  
  
-   [<span data-ttu-id="befa9-171">设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="befa9-171">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
-   [<span data-ttu-id="befa9-172">为合并转换和合并联接转换排序数据</span><span class="sxs-lookup"><span data-stu-id="befa9-172">Sort Data for the Merge and Merge Join Transformations</span></span>](transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="related-content"></a><span data-ttu-id="befa9-173">相关内容</span><span class="sxs-lookup"><span data-stu-id="befa9-173">Related Content</span></span>  
 <span data-ttu-id="befa9-174">social.technet.microsoft.com 上的 Wiki 文章 [SSIS 与 Oracle 连接器](https://go.microsoft.com/fwlink/?LinkId=220670)。</span><span class="sxs-lookup"><span data-stu-id="befa9-174">Wiki article, [SSIS with Oracle Connectors](https://go.microsoft.com/fwlink/?LinkId=220670), on social.technet.microsoft.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="befa9-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="befa9-175">See Also</span></span>  
 <span data-ttu-id="befa9-176">[OLE DB 目标](ole-db-destination.md) </span><span class="sxs-lookup"><span data-stu-id="befa9-176">[OLE DB Destination](ole-db-destination.md) </span></span>  
 <span data-ttu-id="befa9-177">[Integration Services (SSIS) 变量](../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="befa9-177">[Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) </span></span>  
 [<span data-ttu-id="befa9-178">数据流</span><span class="sxs-lookup"><span data-stu-id="befa9-178">Data Flow</span></span>](data-flow.md)  
  
  
