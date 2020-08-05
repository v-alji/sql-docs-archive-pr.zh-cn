---
title: 在执行 SQL 任务中将查询参数映射到变量 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- queries [Integration Services], parameter mapping
- parameterized SQL commands [Integration Services]
- parameters [Integration Services]
- mapping query parameters to variables [Integration Services]
- Execute SQL task [Integration Services]
- variables [Integration Services], mapping parameters to
ms.assetid: 6a164349-dfcf-4995-80bc-d4e7aee52a83
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8511d70b40f2934680e1cb790763045c04e8204a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581358"
---
# <a name="map-query-parameters-to-variables-in-an-execute-sql-task"></a><span data-ttu-id="be178-102">在执行 SQL 任务中将查询参数映射到变量</span><span class="sxs-lookup"><span data-stu-id="be178-102">Map Query Parameters to Variables in an Execute SQL Task</span></span>

  <span data-ttu-id="be178-103">本主题介绍如何在执行 SQL 任务中使用参数化 SQL 语句以及在 SQL 语句的变量和参数之间创建映射。</span><span class="sxs-lookup"><span data-stu-id="be178-103">This topic describes how to use a parameterized SQL statement in the Execute SQL task and create mappings between variables and the parameters in the SQL statement.</span></span>  
  
 <span data-ttu-id="be178-104">若要了解用于不同连接类型的执行 SQL 任务、参数标记和参数名称的详细信息，请参阅 [执行 SQL 任务](control-flow/execute-sql-task.md) 和 [执行 SQL 任务中的参数和返回代码](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="be178-104">To learn more about the Execute SQL task, the parameter markers, and parameter names you use with different connection types, see [Execute SQL Task](control-flow/execute-sql-task.md) and [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>  
  
### <a name="to-map-a-query-parameter-to-a-variable"></a><span data-ttu-id="be178-105">将查询参数映射到变量</span><span class="sxs-lookup"><span data-stu-id="be178-105">To map a query parameter to a variable</span></span>  
  
1.  <span data-ttu-id="be178-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开要使用的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="be178-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package you want to work with.</span></span>  
  
2.  <span data-ttu-id="be178-107">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="be178-107">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="be178-108">单击 **“控制流”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="be178-108">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="be178-109">如果该包尚未包括执行 SQL 任务，则向该包的控制流中添加一个此类任务。</span><span class="sxs-lookup"><span data-stu-id="be178-109">If the package does not already include an Execute SQL task, add one to the control flow of the package.</span></span> <span data-ttu-id="be178-110">有关详细信息，请参阅[在控制流中添加或删除任务或容器](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span><span class="sxs-lookup"><span data-stu-id="be178-110">For more information, see [Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span></span>  
  <span data-ttu-id="be178-111">.</span><span class="sxs-lookup"><span data-stu-id="be178-111">.</span></span>  
  
5.  <span data-ttu-id="be178-112">双击执行 SQL 任务。</span><span class="sxs-lookup"><span data-stu-id="be178-112">Double-click the Execute SQL task.</span></span>  
  
6.  <span data-ttu-id="be178-113">以下列方式之一提供参数化 SQL 命令：</span><span class="sxs-lookup"><span data-stu-id="be178-113">Provide a parameterized SQL command in one of the following ways:</span></span>  
  
    -   <span data-ttu-id="be178-114">在 SQLStatement 属性中使用直接输入并键入 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="be178-114">Use direct input and type the SQL command in the SQLStatement property.</span></span>  
  
    -   <span data-ttu-id="be178-115">使用直接输入，单击 **“生成查询”** ，然后使用查询生成器提供的图形工具创建 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="be178-115">Use direct input, click **Build Query**, and then create an SQL command using the graphical tools that the Query Builder provides.</span></span>  
  
    -   <span data-ttu-id="be178-116">使用文件连接，然后引用包含该 SQL 命令的文件。</span><span class="sxs-lookup"><span data-stu-id="be178-116">Use a file connection and then reference the file that contains the SQL command.</span></span>  
  
    -   <span data-ttu-id="be178-117">使用变量，然后引用包含该 SQL 命令的变量。</span><span class="sxs-lookup"><span data-stu-id="be178-117">Use a variable and then reference the variable that contains the SQL command.</span></span>  
  
     <span data-ttu-id="be178-118">参数化 SQL 语句中使用的参数标记取决于执行 SQL 任务所使用的连接类型。</span><span class="sxs-lookup"><span data-stu-id="be178-118">The parameter markers that you use in parameterized SQL statements depend on the connection type that the Execute SQL task uses.</span></span>  
  
    |<span data-ttu-id="be178-119">连接类型</span><span class="sxs-lookup"><span data-stu-id="be178-119">Connection type</span></span>|<span data-ttu-id="be178-120">参数标记</span><span class="sxs-lookup"><span data-stu-id="be178-120">Parameter marker</span></span>|  
    |---------------------|----------------------|  
    |<span data-ttu-id="be178-121">ADO</span><span class="sxs-lookup"><span data-stu-id="be178-121">ADO</span></span>|<span data-ttu-id="be178-122">?</span><span class="sxs-lookup"><span data-stu-id="be178-122">?</span></span>|  
    |<span data-ttu-id="be178-123">ADO.NET 和 SQLMOBILE</span><span class="sxs-lookup"><span data-stu-id="be178-123">ADO.NET and SQLMOBILE</span></span>|@\<parameter name>|  
    |<span data-ttu-id="be178-124">ODBC</span><span class="sxs-lookup"><span data-stu-id="be178-124">ODBC</span></span>|<span data-ttu-id="be178-125">?</span><span class="sxs-lookup"><span data-stu-id="be178-125">?</span></span>|  
    |<span data-ttu-id="be178-126">EXCEL 和 OLE DB</span><span class="sxs-lookup"><span data-stu-id="be178-126">EXCEL and OLE DB</span></span>|<span data-ttu-id="be178-127">?</span><span class="sxs-lookup"><span data-stu-id="be178-127">?</span></span>|  
  
     <span data-ttu-id="be178-128">下表按连接管理器类型列出了 SELECT 命令的示例。</span><span class="sxs-lookup"><span data-stu-id="be178-128">The following table lists examples of the SELECT command by connection manager type.</span></span> <span data-ttu-id="be178-129">参数在 WHERE 子句中提供筛选值。</span><span class="sxs-lookup"><span data-stu-id="be178-129">Parameters provide the filter values in the WHERE clauses.</span></span> <span data-ttu-id="be178-130">示例使用 SELECT 返回 **的** Product [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)] 表中 **ProductID** 大于且小于由两个参数指定的值的产品。</span><span class="sxs-lookup"><span data-stu-id="be178-130">The examples use SELECT to return products from the **Product** table in [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)] that have a **ProductID** greater than and less than the values specified by two parameters.</span></span>  
  
    |<span data-ttu-id="be178-131">连接类型</span><span class="sxs-lookup"><span data-stu-id="be178-131">Connection type</span></span>|<span data-ttu-id="be178-132">SELECT 语法</span><span class="sxs-lookup"><span data-stu-id="be178-132">SELECT syntax</span></span>|  
    |---------------------|-------------------|  
    |<span data-ttu-id="be178-133">EXCEL、ODBC 和 OLEDB</span><span class="sxs-lookup"><span data-stu-id="be178-133">EXCEL, ODBC, and OLEDB</span></span>|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
    |<span data-ttu-id="be178-134">ADO</span><span class="sxs-lookup"><span data-stu-id="be178-134">ADO</span></span>|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
    |[!INCLUDE[vstecado](../includes/vstecado-md.md)]|`SELECT* FROM Production.Product WHERE ProductId > @parmMinProductID AND ProductID < @parmMaxProductID`|  
  
     <span data-ttu-id="be178-135">有关在存储过程中使用参数的示例，请参阅 [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="be178-135">For examples of using parameters with stored procedures, see [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>  
  
7.  <span data-ttu-id="be178-136">单击 **“参数映射”** 。</span><span class="sxs-lookup"><span data-stu-id="be178-136">Click **Parameter Mapping**.</span></span>  
  
8.  <span data-ttu-id="be178-137">若要添加参数映射，请单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="be178-137">To add a parameter mapping, click **Add**.</span></span>  
  
9. <span data-ttu-id="be178-138">在 **“参数名称”** 框中提供名称。</span><span class="sxs-lookup"><span data-stu-id="be178-138">Provide a name in the **Parameter Name** box.</span></span>  
  
     <span data-ttu-id="be178-139">所使用的参数名称取决于执行 SQL 任务所使用的连接类型。</span><span class="sxs-lookup"><span data-stu-id="be178-139">The parameter names that you use depend on the connection type that the Execute SQL task uses.</span></span>  
  
    |<span data-ttu-id="be178-140">连接类型</span><span class="sxs-lookup"><span data-stu-id="be178-140">Connection type</span></span>|<span data-ttu-id="be178-141">参数名称</span><span class="sxs-lookup"><span data-stu-id="be178-141">Parameter name</span></span>|  
    |---------------------|--------------------|  
    |<span data-ttu-id="be178-142">ADO</span><span class="sxs-lookup"><span data-stu-id="be178-142">ADO</span></span>|<span data-ttu-id="be178-143">Param1, Param2, …</span><span class="sxs-lookup"><span data-stu-id="be178-143">Param1, Param2, ...</span></span>|  
    |<span data-ttu-id="be178-144">ADO.NET 和 SQLMOBILE</span><span class="sxs-lookup"><span data-stu-id="be178-144">ADO.NET and SQLMOBILE</span></span>|@\<parameter name>|  
    |<span data-ttu-id="be178-145">ODBC</span><span class="sxs-lookup"><span data-stu-id="be178-145">ODBC</span></span>|<span data-ttu-id="be178-146">1, 2, 3, …</span><span class="sxs-lookup"><span data-stu-id="be178-146">1, 2, 3, ...</span></span>|  
    |<span data-ttu-id="be178-147">EXCEL 和 OLE DB</span><span class="sxs-lookup"><span data-stu-id="be178-147">EXCEL and OLE DB</span></span>|<span data-ttu-id="be178-148">0, 1, 2, 3, …</span><span class="sxs-lookup"><span data-stu-id="be178-148">0, 1, 2, 3, ...</span></span>|  
  
10. <span data-ttu-id="be178-149">从 **“变量名称”** 列表中选择变量。</span><span class="sxs-lookup"><span data-stu-id="be178-149">From the **Variable Name** list, select a variable.</span></span> <span data-ttu-id="be178-150">有关详细信息，请参阅 [添加、删除、更改包中用户定义变量的作用域](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)。</span><span class="sxs-lookup"><span data-stu-id="be178-150">For more information, see [Add, Delete, Change Scope of User-Defined Variable in a Package](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md).</span></span>  
  
11. <span data-ttu-id="be178-151">在 **“方向”** 列表中指定该参数是输入、输出还是返回值。</span><span class="sxs-lookup"><span data-stu-id="be178-151">In the **Direction** list, specify if the parameter is an input, an output, or a return value.</span></span>  
  
12. <span data-ttu-id="be178-152">在 **“数据类型”** 列表中，设置该参数的数据类型。</span><span class="sxs-lookup"><span data-stu-id="be178-152">In the **Data Type** list, set the data type of the parameter.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="be178-153">参数的数据类型必须与变量的数据类型兼容。</span><span class="sxs-lookup"><span data-stu-id="be178-153">The data type of the parameter must be compatible with the data type of the variable.</span></span>  
  
13. <span data-ttu-id="be178-154">对 SQL 语句中的每个参数重复步骤 8 到 11。</span><span class="sxs-lookup"><span data-stu-id="be178-154">Repeat steps 8 through 11 for each parameter in the SQL statement.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="be178-155">参数映射的顺序必须与参数在 SQL 语句中出现的顺序相同。</span><span class="sxs-lookup"><span data-stu-id="be178-155">The order of parameter mappings must be the same as the order in which the parameters appear in the SQL statement.</span></span>  
  
14. <span data-ttu-id="be178-156">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="be178-156">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be178-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="be178-157">See Also</span></span>  
 <span data-ttu-id="be178-158">[执行 SQL 任务](control-flow/execute-sql-task.md) </span><span class="sxs-lookup"><span data-stu-id="be178-158">[Execute SQL Task](control-flow/execute-sql-task.md) </span></span>  
 <span data-ttu-id="be178-159">[执行 SQL 任务中的参数和返回代码](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md) </span><span class="sxs-lookup"><span data-stu-id="be178-159">[Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md) </span></span>  
 [<span data-ttu-id="be178-160">Integration Services (SSIS) 变量</span><span class="sxs-lookup"><span data-stu-id="be178-160">Integration Services &#40;SSIS&#41; Variables</span></span>](integration-services-ssis-variables.md)  
  
  
