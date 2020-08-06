---
title: ODBC API 实现详细信息 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, functions
- SQL Server Native Client ODBC driver, SQL Server-specific behaviors
- ODBC, SQL Server-specific behaviors
- functions [ODBC]
ms.assetid: dca92489-f179-4b1f-997c-adcc46aa17a3
author: rothja
ms.author: jroth
ms.openlocfilehash: 1af47924090e7cb1df8ed7907ba0f793b9df2420
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693302"
---
# <a name="odbc-api-implementation-details"></a><span data-ttu-id="633a2-102">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="633a2-102">ODBC API Implementation Details</span></span>
  <span data-ttu-id="633a2-103">本节介绍了与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序一起使用时呈现 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 特定行为的 ODBC 函数。</span><span class="sxs-lookup"><span data-stu-id="633a2-103">This section documents the ODBC functions that exhibit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific behaviors when used with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="633a2-104">此处只介绍部分 ODBC 函数。</span><span class="sxs-lookup"><span data-stu-id="633a2-104">Not all ODBC functions are documented here.</span></span> <span data-ttu-id="633a2-105">各个单独的主题只讨论 ODBC 函数的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 特定问题，</span><span class="sxs-lookup"><span data-stu-id="633a2-105">The individual topics only discuss the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific issues for an ODBC function.</span></span> <span data-ttu-id="633a2-106">它们不提供 ODBC 函数的完整参考资料。</span><span class="sxs-lookup"><span data-stu-id="633a2-106">They are not a complete reference for the ODBC functions.</span></span>  
  
 <span data-ttu-id="633a2-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序符合 ODBC 3.51 规范，如果您使用 Windows 7 SDK，则符合 ODBC 3.8 规范。</span><span class="sxs-lookup"><span data-stu-id="633a2-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver complies with the ODBC 3.51 specification and, if you are using the Windows 7 SDK, with the ODBC 3.8 specification.</span></span> <span data-ttu-id="633a2-108">有关综合性 ODBC 引用，请联机查看[Odbc 程序员参考](https://go.microsoft.com/fwlink/?LinkId=45250)。</span><span class="sxs-lookup"><span data-stu-id="633a2-108">For a comprehensive ODBC reference, view the [ODBC Programmer's Reference](https://go.microsoft.com/fwlink/?LinkId=45250) online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="633a2-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="633a2-109">In This Section</span></span>  
  
-   [<span data-ttu-id="633a2-110">SQLBindCol</span><span class="sxs-lookup"><span data-stu-id="633a2-110">SQLBindCol</span></span>](sqlbindcol.md)  
  
-   [<span data-ttu-id="633a2-111">SQLBindParameter</span><span class="sxs-lookup"><span data-stu-id="633a2-111">SQLBindParameter</span></span>](sqlbindparameter.md)  
  
-   [<span data-ttu-id="633a2-112">SQLBrowseConnect</span><span class="sxs-lookup"><span data-stu-id="633a2-112">SQLBrowseConnect</span></span>](sqlbrowseconnect.md)  
  
-   [<span data-ttu-id="633a2-113">SQLCancel</span><span class="sxs-lookup"><span data-stu-id="633a2-113">SQLCancel</span></span>](sqlcancel.md)  
  
-   [<span data-ttu-id="633a2-114">SQLCloseCursor</span><span class="sxs-lookup"><span data-stu-id="633a2-114">SQLCloseCursor</span></span>](sqlclosecursor.md)  
  
-   [<span data-ttu-id="633a2-115">SQLColAttribute</span><span class="sxs-lookup"><span data-stu-id="633a2-115">SQLColAttribute</span></span>](sqlcolattribute.md)  
  
-   [<span data-ttu-id="633a2-116">SQLColumnPrivileges</span><span class="sxs-lookup"><span data-stu-id="633a2-116">SQLColumnPrivileges</span></span>](sqlcolumnprivileges.md)  
  
-   [<span data-ttu-id="633a2-117">SQLColumns</span><span class="sxs-lookup"><span data-stu-id="633a2-117">SQLColumns</span></span>](sqlcolumns.md)  
  
-   [<span data-ttu-id="633a2-118">SQLConfigDataSource</span><span class="sxs-lookup"><span data-stu-id="633a2-118">SQLConfigDataSource</span></span>](sqlconfigdatasource.md)  
  
-   [<span data-ttu-id="633a2-119">SQLConnect</span><span class="sxs-lookup"><span data-stu-id="633a2-119">SQLConnect</span></span>](sqlconnect.md)  
  
-   [<span data-ttu-id="633a2-120">SQLDescribeCol</span><span class="sxs-lookup"><span data-stu-id="633a2-120">SQLDescribeCol</span></span>](sqldescribecol.md)  
  
-   [<span data-ttu-id="633a2-121">SQLDescribeParam</span><span class="sxs-lookup"><span data-stu-id="633a2-121">SQLDescribeParam</span></span>](sqldescribeparam.md)  
  
-   [<span data-ttu-id="633a2-122">SQLDriverConnect</span><span class="sxs-lookup"><span data-stu-id="633a2-122">SQLDriverConnect</span></span>](sqldriverconnect.md)  
  
-   [<span data-ttu-id="633a2-123">SQLDrivers</span><span class="sxs-lookup"><span data-stu-id="633a2-123">SQLDrivers</span></span>](sqldrivers.md)  
  
-   [<span data-ttu-id="633a2-124">SQLEndTran</span><span class="sxs-lookup"><span data-stu-id="633a2-124">SQLEndTran</span></span>](sqlendtran.md)  
  
-   [<span data-ttu-id="633a2-125">SQLExecDirect</span><span class="sxs-lookup"><span data-stu-id="633a2-125">SQLExecDirect</span></span>](sqlexecdirect.md)  
  
-   [<span data-ttu-id="633a2-126">SQLExecute</span><span class="sxs-lookup"><span data-stu-id="633a2-126">SQLExecute</span></span>](sqlexecute.md)  
  
-   [<span data-ttu-id="633a2-127">SQLFetch</span><span class="sxs-lookup"><span data-stu-id="633a2-127">SQLFetch</span></span>](sqlfetch.md)  
  
-   [<span data-ttu-id="633a2-128">SQLFetchScroll</span><span class="sxs-lookup"><span data-stu-id="633a2-128">SQLFetchScroll</span></span>](sqlfetchscroll.md)  
  
-   [<span data-ttu-id="633a2-129">SQLForeignKeys</span><span class="sxs-lookup"><span data-stu-id="633a2-129">SQLForeignKeys</span></span>](sqlforeignkeys.md)  
  
-   [<span data-ttu-id="633a2-130">SQLFreeHandle</span><span class="sxs-lookup"><span data-stu-id="633a2-130">SQLFreeHandle</span></span>](sqlfreehandle.md)  
  
-   [<span data-ttu-id="633a2-131">SQLFreeStmt</span><span class="sxs-lookup"><span data-stu-id="633a2-131">SQLFreeStmt</span></span>](sqlfreestmt.md)  
  
-   [<span data-ttu-id="633a2-132">SQLGetConnectAttr</span><span class="sxs-lookup"><span data-stu-id="633a2-132">SQLGetConnectAttr</span></span>](sqlgetconnectattr.md)  
  
-   [<span data-ttu-id="633a2-133">SQLGetCursorName</span><span class="sxs-lookup"><span data-stu-id="633a2-133">SQLGetCursorName</span></span>](sqlgetcursorname.md)  
  
-   [<span data-ttu-id="633a2-134">SQLGetData</span><span class="sxs-lookup"><span data-stu-id="633a2-134">SQLGetData</span></span>](sqlgetdata.md)  
  
-   [<span data-ttu-id="633a2-135">SQLGetDescField</span><span class="sxs-lookup"><span data-stu-id="633a2-135">SQLGetDescField</span></span>](sqlgetdescfield.md)  
  
-   [<span data-ttu-id="633a2-136">SQLGetDescRec</span><span class="sxs-lookup"><span data-stu-id="633a2-136">SQLGetDescRec</span></span>](sqlgetdescrec.md)  
  
-   [<span data-ttu-id="633a2-137">SQLGetDiagField</span><span class="sxs-lookup"><span data-stu-id="633a2-137">SQLGetDiagField</span></span>](sqlgetdiagfield.md)  
  
-   [<span data-ttu-id="633a2-138">SQLGetFunctions</span><span class="sxs-lookup"><span data-stu-id="633a2-138">SQLGetFunctions</span></span>](sqlgetfunctions.md)  
  
-   [<span data-ttu-id="633a2-139">SQLGetInfo</span><span class="sxs-lookup"><span data-stu-id="633a2-139">SQLGetInfo</span></span>](sqlgetinfo.md)  
  
-   [<span data-ttu-id="633a2-140">SQLGetStmtAttr</span><span class="sxs-lookup"><span data-stu-id="633a2-140">SQLGetStmtAttr</span></span>](sqlgetstmtattr.md)  
  
-   [<span data-ttu-id="633a2-141">SQLGetTypeInfo</span><span class="sxs-lookup"><span data-stu-id="633a2-141">SQLGetTypeInfo</span></span>](sqlgettypeinfo.md)  
  
-   [<span data-ttu-id="633a2-142">SQLMoreResults</span><span class="sxs-lookup"><span data-stu-id="633a2-142">SQLMoreResults</span></span>](sqlmoreresults.md)  
  
-   [<span data-ttu-id="633a2-143">SQLNativeSql</span><span class="sxs-lookup"><span data-stu-id="633a2-143">SQLNativeSql</span></span>](sqlnativesql.md)  
  
-   [<span data-ttu-id="633a2-144">SQLNumParams</span><span class="sxs-lookup"><span data-stu-id="633a2-144">SQLNumParams</span></span>](sqlnumparams.md)  
  
-   [<span data-ttu-id="633a2-145">SQLNumResultCols</span><span class="sxs-lookup"><span data-stu-id="633a2-145">SQLNumResultCols</span></span>](sqlnumresultcols.md)  
  
-   [<span data-ttu-id="633a2-146">SQLParamData</span><span class="sxs-lookup"><span data-stu-id="633a2-146">SQLParamData</span></span>](sqlparamdata.md)  
  
-   [<span data-ttu-id="633a2-147">SQLPrimaryKeys</span><span class="sxs-lookup"><span data-stu-id="633a2-147">SQLPrimaryKeys</span></span>](sqlprimarykeys.md)  
  
-   [<span data-ttu-id="633a2-148">SQLProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="633a2-148">SQLProcedureColumns</span></span>](sqlprocedurecolumns.md)  
  
-   [<span data-ttu-id="633a2-149">SQLProcedures</span><span class="sxs-lookup"><span data-stu-id="633a2-149">SQLProcedures</span></span>](sqlprocedures.md)  
  
-   [<span data-ttu-id="633a2-150">SQLPutData</span><span class="sxs-lookup"><span data-stu-id="633a2-150">SQLPutData</span></span>](sqlputdata.md)  
  
-   [<span data-ttu-id="633a2-151">SQLRowCount</span><span class="sxs-lookup"><span data-stu-id="633a2-151">SQLRowCount</span></span>](sqlrowcount.md)  
  
-   [<span data-ttu-id="633a2-152">SQLSetConnectAttr</span><span class="sxs-lookup"><span data-stu-id="633a2-152">SQLSetConnectAttr</span></span>](sqlsetconnectattr.md)  
  
-   [<span data-ttu-id="633a2-153">SQLSetDescField</span><span class="sxs-lookup"><span data-stu-id="633a2-153">SQLSetDescField</span></span>](sqlsetdescfield.md)  
  
-   [<span data-ttu-id="633a2-154">SQLSetDescRec</span><span class="sxs-lookup"><span data-stu-id="633a2-154">SQLSetDescRec</span></span>](sqlsetdescrec.md)  
  
-   [<span data-ttu-id="633a2-155">SQLSetEnvAttr</span><span class="sxs-lookup"><span data-stu-id="633a2-155">SQLSetEnvAttr</span></span>](sqlsetenvattr.md)  
  
-   [<span data-ttu-id="633a2-156">SQLSetStmtAttr</span><span class="sxs-lookup"><span data-stu-id="633a2-156">SQLSetStmtAttr</span></span>](sqlsetstmtattr.md)  
  
-   [<span data-ttu-id="633a2-157">SQLSpecialColumns</span><span class="sxs-lookup"><span data-stu-id="633a2-157">SQLSpecialColumns</span></span>](sqlspecialcolumns.md)  
  
-   [<span data-ttu-id="633a2-158">SQLStatistics</span><span class="sxs-lookup"><span data-stu-id="633a2-158">SQLStatistics</span></span>](../statistics/statistics.md)  
  
-   [<span data-ttu-id="633a2-159">SQLTablePrivileges</span><span class="sxs-lookup"><span data-stu-id="633a2-159">SQLTablePrivileges</span></span>](sqltableprivileges.md)  
  
-   [<span data-ttu-id="633a2-160">SQLTables</span><span class="sxs-lookup"><span data-stu-id="633a2-160">SQLTables</span></span>](sqltables.md)  
  
## <a name="see-also"></a><span data-ttu-id="633a2-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="633a2-161">See Also</span></span>  
 <span data-ttu-id="633a2-162">[SQL Server Native Client &#40;ODBC&#41; 引用](../../database-engine/dev-guide/sql-server-native-client-odbc-reference.md) </span><span class="sxs-lookup"><span data-stu-id="633a2-162">[SQL Server Native Client &#40;ODBC&#41; Reference](../../database-engine/dev-guide/sql-server-native-client-odbc-reference.md) </span></span>  
 [<span data-ttu-id="633a2-163">使用 SQL Server Native Client 生成应用程序</span><span class="sxs-lookup"><span data-stu-id="633a2-163">Building Applications with SQL Server Native Client</span></span>](../native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
