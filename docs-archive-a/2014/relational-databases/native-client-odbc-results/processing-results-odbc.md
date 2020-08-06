---
title: 正在处理 ODBC)  (结果 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], about result sets
- SQLRowCount function
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- COMPUTE clause
- result sets [ODBC]
- COMPUTE BY clause
ms.assetid: 61a8db19-6571-47dd-84e8-fcc97cb60b45
author: rothja
ms.author: jroth
ms.openlocfilehash: 72c0d15231b07a23f10a03b0fca270d1d014891c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693823"
---
# <a name="processing-results-odbc"></a><span data-ttu-id="8d8ad-102">处理结果 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="8d8ad-102">Processing Results (ODBC)</span></span>
  <span data-ttu-id="8d8ad-103">应用程序提交 SQL 语句之后，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会将得到的任何数据作为一个或多个结果集返回。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-103">After an application submits a SQL statement, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] returns any resulting data as one or more result sets.</span></span> <span data-ttu-id="8d8ad-104">结果集是一组与查询条件匹配的行和列。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-104">A result set is a set of rows and columns that match the criteria of the query.</span></span> <span data-ttu-id="8d8ad-105">SELECT 语句、目录函数和某些存储过程可产生以表格格式供应用程序使用的结果集。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-105">SELECT statements, catalog functions, and some stored procedures produce a result set made available to an application in tabular form.</span></span> <span data-ttu-id="8d8ad-106">如果执行的 SQL 语句为存储过程、包含多个命令的批处理或包含关键字的 SELECT 语句，则会有多个要处理的结果集。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-106">If the executed SQL statement is a stored procedure, a batch containing multiple commands, or a SELECT statement containing keywords, there will be multiple result sets to process.</span></span>  
  
 <span data-ttu-id="8d8ad-107">ODBC 目录函数也可以检索数据。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-107">ODBC catalog functions also can retrieve data.</span></span> <span data-ttu-id="8d8ad-108">例如， [SQLColumns](../native-client-odbc-api/sqlcolumns.md)检索有关数据源中的列的数据。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-108">For example, [SQLColumns](../native-client-odbc-api/sqlcolumns.md) retrieves data about columns in the data source.</span></span> <span data-ttu-id="8d8ad-109">这些结果集可以包含零行或更多行。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-109">These result sets can contain zero or more rows.</span></span>  
  
 <span data-ttu-id="8d8ad-110">其他 SQL 语句（如 GRANT 或 REVOKE）不返回结果集。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-110">Other SQL statements, such as GRANT or REVOKE, do not return result sets.</span></span> <span data-ttu-id="8d8ad-111">对于这些语句，从**SQLExecute**或**SQLExecDirect**返回的代码通常是语句成功的唯一指示。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-111">For these statements, the return code from **SQLExecute** or **SQLExecDirect** is usually the only indication the statement was successful.</span></span>  
  
 <span data-ttu-id="8d8ad-112">每个 INSERT、UPDATE 和 DELETE 语句均返回一个仅包含受修改影响的行数的结果集。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-112">Each INSERT, UPDATE, and DELETE statement returns a result set containing only the number of rows affected by the modification.</span></span> <span data-ttu-id="8d8ad-113">当应用程序调用[SQLRowCount](../native-client-odbc-api/sqlrowcount.md)时，此计数可用。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-113">This count is made available when application calls [SQLRowCount](../native-client-odbc-api/sqlrowcount.md).</span></span> <span data-ttu-id="8d8ad-114">ODBC 3。*x*应用程序必须调用**SQLRowCount**来检索结果集，或[SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md)将其取消。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-114">ODBC 3.*x* applications must either call **SQLRowCount** to retrieve the result set or [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) to cancel it.</span></span> <span data-ttu-id="8d8ad-115">当应用程序执行包含多个 INSERT、UPDATE 或 DELETE 语句的批处理或存储过程时，必须使用**SQLRowCount**处理每个修改语句的结果集，或使用**SQLMoreResults**来取消结果集。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-115">When an application executes a batch or stored procedure containing multiple INSERT, UPDATE, or DELETE statements, the result set from each modification statement must be processed using **SQLRowCount** or cancelled using **SQLMoreResults**.</span></span> <span data-ttu-id="8d8ad-116">通过在批处理或存储过程中包含 SET NOCOUNT ON 语句，可以取消这些计数。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-116">These counts can be cancelled by including a SET NOCOUNT ON statement in the batch or stored procedure.</span></span>  
  
 <span data-ttu-id="8d8ad-117">Transact-SQL 包括 SET NOCOUNT 语句。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-117">Transact-SQL includes the SET NOCOUNT statement.</span></span> <span data-ttu-id="8d8ad-118">当 NOCOUNT 选项设置为 on 时，SQL Server 不返回受语句影响的行数， **SQLRowCount**返回0。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-118">When the NOCOUNT option is set on, SQL Server does not return the counts of the rows affected by a statement and **SQLRowCount** returns 0.</span></span> <span data-ttu-id="8d8ad-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序版本引入了特定于驱动程序的[SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md)选项 SQL_SOPT_SS_NOCOUNT_STATUS，以报告 NOCOUNT 选项是打开还是关闭。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-119">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver version introduces a driver-specific [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md) option, SQL_SOPT_SS_NOCOUNT_STATUS, to report on whether the NOCOUNT option is on or off.</span></span> <span data-ttu-id="8d8ad-120">无论何时**SQLRowCount**返回0，应用程序都应测试 SQL_SOPT_SS_NOCOUNT_STATUS。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-120">Anytime **SQLRowCount** returns 0, the application should test SQL_SOPT_SS_NOCOUNT_STATUS.</span></span> <span data-ttu-id="8d8ad-121">如果返回 SQL_NC_ON，则**SQLRowCount**的值将仅指示 SQL Server 未返回行计数。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-121">If SQL_NC_ON is returned, the value of 0 from **SQLRowCount** only indicates that SQL Server has not returned a row count.</span></span> <span data-ttu-id="8d8ad-122">如果返回 SQL_NC_OFF，则表示 NOCOUNT 为 OFF，0与**SQLRowCount**的值指示该语句不会影响任何行。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-122">If SQL_NC_OFF is returned, it means that NOCOUNT is off and the value of 0 from **SQLRowCount** indicates that the statement did not affect any rows.</span></span> <span data-ttu-id="8d8ad-123">SQL_NC_OFF SQL_SOPT_SS_NOCOUNT_STATUS 时，应用程序不应显示**SQLRowCount**的值。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-123">Applications should not display the value of **SQLRowCount** when SQL_SOPT_SS_NOCOUNT_STATUS is SQL_NC_OFF.</span></span> <span data-ttu-id="8d8ad-124">大型批处理或存储过程可能包含多个 SET NOCOUNT 语句，因此程序员不能假定 SQL_SOPT_SS_NOCOUNT_STATUS 保持不变。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-124">Large batches or stored procedures may contain multiple SET NOCOUNT statements so programmers cannot assume SQL_SOPT_SS_NOCOUNT_STATUS remains constant.</span></span> <span data-ttu-id="8d8ad-125">每次**SQLRowCount**返回0时，应测试该选项。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-125">The option should be tested each time **SQLRowCount** returns 0.</span></span>  
  
 <span data-ttu-id="8d8ad-126">有若干其他 Transact-SQL 语句在消息中而不是在结果集中返回它们的值。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-126">Several other Transact-SQL statements return their data in messages rather than result sets.</span></span> <span data-ttu-id="8d8ad-127">当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序收到这些消息时，它将返回 SQL_SUCCESS_WITH_INFO，让应用程序知道提供信息性消息。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-127">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver receives these messages, it returns SQL_SUCCESS_WITH_INFO to let the application know that informational messages are available.</span></span> <span data-ttu-id="8d8ad-128">然后，应用程序可以调用**SQLGetDiagRec**来检索这些消息。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-128">The application can then call **SQLGetDiagRec** to retrieve these messages.</span></span> <span data-ttu-id="8d8ad-129">以这种方式工作的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句如下：</span><span class="sxs-lookup"><span data-stu-id="8d8ad-129">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that work this way are:</span></span>  
  
-   <span data-ttu-id="8d8ad-130">DBCC</span><span class="sxs-lookup"><span data-stu-id="8d8ad-130">DBCC</span></span>  
  
-   <span data-ttu-id="8d8ad-131">SET SHOWPLAN（在早期版本的 SQL Server 中提供）</span><span class="sxs-lookup"><span data-stu-id="8d8ad-131">SET SHOWPLAN (available with earlier versions of SQL Server)</span></span>  
  
-   <span data-ttu-id="8d8ad-132">SET STATISTICS</span><span class="sxs-lookup"><span data-stu-id="8d8ad-132">SET STATISTICS</span></span>  
  
-   <span data-ttu-id="8d8ad-133">PRINT</span><span class="sxs-lookup"><span data-stu-id="8d8ad-133">PRINT</span></span>  
  
-   <span data-ttu-id="8d8ad-134">RAISERROR</span><span class="sxs-lookup"><span data-stu-id="8d8ad-134">RAISERROR</span></span>  
  
 <span data-ttu-id="8d8ad-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序在严重性为11或更高的 RAISERROR 上返回 SQL_ERROR。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-135">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver returns SQL_ERROR on a RAISERROR with a severity of 11 or higher.</span></span> <span data-ttu-id="8d8ad-136">如果 RAISERROR 的严重性级别为 19 或更高，则连接也会断开。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-136">If the severity of the RAISERROR is 19 or higher, the connection is also dropped.</span></span>  
  
 <span data-ttu-id="8d8ad-137">为了处理 SQL 语句产生的结果集，应用程序会执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="8d8ad-137">To process the result sets from an SQL statement, the application:</span></span>  
  
-   <span data-ttu-id="8d8ad-138">确定结果集的特征。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-138">Determines the characteristics of the result set.</span></span>  
  
-   <span data-ttu-id="8d8ad-139">将列绑定到程序变量。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-139">Binds the columns to program variables.</span></span>  
  
-   <span data-ttu-id="8d8ad-140">检索单个值、整行值或多行值。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-140">Retrieves a single value, an entire row of values, or multiple rows of values.</span></span>  
  
-   <span data-ttu-id="8d8ad-141">进行测试以查看是否存在多个结果集，如果存在，则进行环回以确定新结果集的特征。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-141">Tests to see if there are more result sets, and if so, loops back to determining the characteristics of the new result set.</span></span>  
  
 <span data-ttu-id="8d8ad-142">从数据源中检索行并将其返回给应用程序的过程称为提取。</span><span class="sxs-lookup"><span data-stu-id="8d8ad-142">The process of retrieving rows from the data source and returning them to the application is called fetching.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8d8ad-143">本节内容</span><span class="sxs-lookup"><span data-stu-id="8d8ad-143">In This Section</span></span>  
  
-   [<span data-ttu-id="8d8ad-144">确定结果集的特征 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="8d8ad-144">Determining the Characteristics of a Result Set &#40;ODBC&#41;</span></span>](determining-the-characteristics-of-a-result-set-odbc.md)  
  
-   [<span data-ttu-id="8d8ad-145">分配存储区</span><span class="sxs-lookup"><span data-stu-id="8d8ad-145">Assigning Storage</span></span>](assigning-storage.md)  
  
-   [<span data-ttu-id="8d8ad-146">提取结果数据</span><span class="sxs-lookup"><span data-stu-id="8d8ad-146">Fetching Result Data</span></span>](fetching-result-data.md)  
  
-   [<span data-ttu-id="8d8ad-147">将数据类型映射 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="8d8ad-147">Mapping Data Types &#40;ODBC&#41;</span></span>](mapping-data-types-odbc.md)  
  
-   [<span data-ttu-id="8d8ad-148">数据类型用法</span><span class="sxs-lookup"><span data-stu-id="8d8ad-148">Data Type Usage</span></span>](data-type-usage.md)  
  
-   [<span data-ttu-id="8d8ad-149">字符数据的自动转换</span><span class="sxs-lookup"><span data-stu-id="8d8ad-149">Autotranslation of Character Data</span></span>](autotranslation-of-character-data.md)  
  
## <a name="see-also"></a><span data-ttu-id="8d8ad-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d8ad-150">See Also</span></span>  
 <span data-ttu-id="8d8ad-151">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="8d8ad-151">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 [<span data-ttu-id="8d8ad-152">处理结果操作指南主题 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="8d8ad-152">Processing Results How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)  
  
  
