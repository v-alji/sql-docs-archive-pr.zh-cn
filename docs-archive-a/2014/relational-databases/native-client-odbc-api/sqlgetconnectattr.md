---
title: SQLGetConnectAttr |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetConnectAttr function
ms.assetid: 26e4e69a-44fd-45e3-b47a-ae39184f041b
author: rothja
ms.author: jroth
ms.openlocfilehash: f82a0fb71103e811b36280f9722c160791023e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576743"
---
# <a name="sqlgetconnectattr"></a><span data-ttu-id="1dab4-102">SQLGetConnectAttr</span><span class="sxs-lookup"><span data-stu-id="1dab4-102">SQLGetConnectAttr</span></span>
  <span data-ttu-id="1dab4-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序定义了特定于驱动程序的连接属性。</span><span class="sxs-lookup"><span data-stu-id="1dab4-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver defines driver-specific connection attributes.</span></span> <span data-ttu-id="1dab4-104">某些属性可用于 `SQLGetConnectAttr` ，而函数用于报告其当前设置。</span><span class="sxs-lookup"><span data-stu-id="1dab4-104">Some of the attributes are available to `SQLGetConnectAttr`, and the function is used to report their current settings.</span></span> <span data-ttu-id="1dab4-105">在建立连接或使用[SQLSetConnectAttr](sqlsetconnectattr.md)设置特性之前，不保证为这些特性报告的值。</span><span class="sxs-lookup"><span data-stu-id="1dab4-105">The values reported for these attributes are not guaranteed until after a connection has been made or the attribute has been set using [SQLSetConnectAttr](sqlsetconnectattr.md).</span></span>  
  
 <span data-ttu-id="1dab4-106">本主题列出只读属性。</span><span class="sxs-lookup"><span data-stu-id="1dab4-106">This topic lists the read only attributes.</span></span> <span data-ttu-id="1dab4-107">有关其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 特定于 Native CLIENT ODBC 驱动程序特定的连接属性的信息，请参阅[SQLSetConnectAttr](sqlsetconnectattr.md)。</span><span class="sxs-lookup"><span data-stu-id="1dab4-107">For information about the other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver-specific connection attributes, see [SQLSetConnectAttr](sqlsetconnectattr.md).</span></span>  
  
## <a name="sql_copt_ss_connection_dead"></a><span data-ttu-id="1dab4-108">SQL_COPT_SS_CONNECTION_DEAD</span><span class="sxs-lookup"><span data-stu-id="1dab4-108">SQL_COPT_SS_CONNECTION_DEAD</span></span>  
 <span data-ttu-id="1dab4-109">SQL_COPT_SS_CONNECTION_DEAD 属性报告与服务器的连接的状态。</span><span class="sxs-lookup"><span data-stu-id="1dab4-109">The SQL_COPT_SS_CONNECTION_DEAD attribute reports the state of a connection to a server.</span></span> <span data-ttu-id="1dab4-110">驱动程序将查询网络，以获得连接的当前状态。</span><span class="sxs-lookup"><span data-stu-id="1dab4-110">The driver queries the network for the current state of the connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1dab4-111">标准 ODBC 连接属性 SQL_ATTR_CONNECTION_DEAD 返回连接的最近状态。</span><span class="sxs-lookup"><span data-stu-id="1dab4-111">The standard ODBC connection attribute SQL_ATTR_CONNECTION_DEAD returns the most recent state of the connection.</span></span> <span data-ttu-id="1dab4-112">这可能不是当前连接状态。</span><span class="sxs-lookup"><span data-stu-id="1dab4-112">This might not be the current connection state.</span></span>  
  
|<span data-ttu-id="1dab4-113">值</span><span class="sxs-lookup"><span data-stu-id="1dab4-113">Value</span></span>|<span data-ttu-id="1dab4-114">说明</span><span class="sxs-lookup"><span data-stu-id="1dab4-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1dab4-115">SQL_CD_TRUE</span><span class="sxs-lookup"><span data-stu-id="1dab4-115">SQL_CD_TRUE</span></span>|<span data-ttu-id="1dab4-116">与服务器的连接已丢失。</span><span class="sxs-lookup"><span data-stu-id="1dab4-116">The connection to the server has been lost.</span></span>|  
|<span data-ttu-id="1dab4-117">SQL_CD_FALSE</span><span class="sxs-lookup"><span data-stu-id="1dab4-117">SQL_CD_FALSE</span></span>|<span data-ttu-id="1dab4-118">连接已打开，可以用于执行语句处理。</span><span class="sxs-lookup"><span data-stu-id="1dab4-118">The connection is open and available for statement processing.</span></span>|  
  
## <a name="sql_copt_ss_client_connection_id"></a><span data-ttu-id="1dab4-119">SQL_COPT_SS_CLIENT_CONNECTION_ID</span><span class="sxs-lookup"><span data-stu-id="1dab4-119">SQL_COPT_SS_CLIENT_CONNECTION_ID</span></span>  
 <span data-ttu-id="1dab4-120">SQL_COPT_SS_CLIENT_CONNECTION_ID 属性检索客户端连接 ID，该属性可用于查找：</span><span class="sxs-lookup"><span data-stu-id="1dab4-120">The SQL_COPT_SS_CLIENT_CONNECTION_ID attribute retrieves the client connection ID, which can then be used to locate:</span></span>  
  
-   <span data-ttu-id="1dab4-121">XEvents 日志中的诊断信息（如果启用）。</span><span class="sxs-lookup"><span data-stu-id="1dab4-121">Diagnostic information in the XEvents log, when enabled.</span></span>  
  
-   <span data-ttu-id="1dab4-122">连接环形缓冲区中的连接错误信息。</span><span class="sxs-lookup"><span data-stu-id="1dab4-122">Connection error information in the connection ring buffer.</span></span>  
  
-   <span data-ttu-id="1dab4-123">数据访问跟踪日志中的诊断信息（如果启用）。</span><span class="sxs-lookup"><span data-stu-id="1dab4-123">Diagnostic information in the data access tracing logs, when enabled.</span></span>  
  
 <span data-ttu-id="1dab4-124">有关详细信息，请参阅[访问扩展事件日志中的诊断信息](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)。</span><span class="sxs-lookup"><span data-stu-id="1dab4-124">For more information, see [Accessing Diagnostic Information in the Extended Events Log](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).</span></span>  
  
|<span data-ttu-id="1dab4-125">值</span><span class="sxs-lookup"><span data-stu-id="1dab4-125">Value</span></span>|<span data-ttu-id="1dab4-126">说明</span><span class="sxs-lookup"><span data-stu-id="1dab4-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1dab4-127">SQL_ERROR</span><span class="sxs-lookup"><span data-stu-id="1dab4-127">SQL_ERROR</span></span>|<span data-ttu-id="1dab4-128">连接失败。</span><span class="sxs-lookup"><span data-stu-id="1dab4-128">The connection failed.</span></span>|  
|<span data-ttu-id="1dab4-129">SQL_SUCCESS</span><span class="sxs-lookup"><span data-stu-id="1dab4-129">SQL_SUCCESS</span></span>|<span data-ttu-id="1dab4-130">连接成功。</span><span class="sxs-lookup"><span data-stu-id="1dab4-130">The connection succeeded.</span></span> <span data-ttu-id="1dab4-131">将在输出缓冲区中找到客户端连接 ID。</span><span class="sxs-lookup"><span data-stu-id="1dab4-131">The client connection ID will be found in the output buffer.</span></span>|  
  
## <a name="sql_copt_ss_perf_data"></a><span data-ttu-id="1dab4-132">SQL_COPT_SS_PERF_DATA</span><span class="sxs-lookup"><span data-stu-id="1dab4-132">SQL_COPT_SS_PERF_DATA</span></span>  
 <span data-ttu-id="1dab4-133">SQL_COPT_SS_PERF_DATA 属性返回包含当前驱动程序性能统计信息的 SQLPERF 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="1dab4-133">The SQL_COPT_SS_PERF_DATA attribute returns a pointer to a SQLPERF structure containing the current driver performance statistics.</span></span> <span data-ttu-id="1dab4-134">`SQLGetConnectAttr`如果未启用性能日志记录，将返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="1dab4-134">`SQLGetConnectAttr` will return NULL if performance logging is not enabled.</span></span> <span data-ttu-id="1dab4-135">驱动程序不会动态更新 SQLPERF 结构中的统计信息。</span><span class="sxs-lookup"><span data-stu-id="1dab4-135">The statistics in the SQLPERF structure are not dynamically updated by the driver.</span></span> <span data-ttu-id="1dab4-136">`SQLGetConnectAttr`每次需要刷新性能统计信息时调用。</span><span class="sxs-lookup"><span data-stu-id="1dab4-136">Call `SQLGetConnectAttr` each time the performance statistics need to be refreshed.</span></span>  
  
|<span data-ttu-id="1dab4-137">值</span><span class="sxs-lookup"><span data-stu-id="1dab4-137">Value</span></span>|<span data-ttu-id="1dab4-138">说明</span><span class="sxs-lookup"><span data-stu-id="1dab4-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1dab4-139">Null</span><span class="sxs-lookup"><span data-stu-id="1dab4-139">NULL</span></span>|<span data-ttu-id="1dab4-140">未启用性能记录。</span><span class="sxs-lookup"><span data-stu-id="1dab4-140">Performance logging is not enabled.</span></span>|  
|<span data-ttu-id="1dab4-141">任何其他值</span><span class="sxs-lookup"><span data-stu-id="1dab4-141">Any other value</span></span>|<span data-ttu-id="1dab4-142">SQLPERF 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="1dab4-142">A pointer to a SQLPERF structure.</span></span>|  
  
## <a name="sql_copt_ss_perf_query"></a><span data-ttu-id="1dab4-143">SQL_COPT_SS_PERF_QUERY</span><span class="sxs-lookup"><span data-stu-id="1dab4-143">SQL_COPT_SS_PERF_QUERY</span></span>  
 <span data-ttu-id="1dab4-144">如果启用对长时间运行查询的记录，则 SQL_COPT_SS_PERF_QUERY 属性返回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="1dab4-144">The SQL_COPT_SS_PERF_QUERY attribute returns TRUE if logging of long running queries is enabled.</span></span> <span data-ttu-id="1dab4-145">如果查询记录不处于活动状态，则请求返回 FALSE。</span><span class="sxs-lookup"><span data-stu-id="1dab4-145">The request returns FALSE if query logging is not active.</span></span>  
  
## <a name="sql_copt_ss_user_data"></a><span data-ttu-id="1dab4-146">SQL_COPT_SS_USER_DATA</span><span class="sxs-lookup"><span data-stu-id="1dab4-146">SQL_COPT_SS_USER_DATA</span></span>  
 <span data-ttu-id="1dab4-147">SQL_COPT_SS_USER_DATA 属性检索用户数据指针。</span><span class="sxs-lookup"><span data-stu-id="1dab4-147">The SQL_COPT_SS_USER_DATA attribute retrieves the user-data pointer.</span></span> <span data-ttu-id="1dab4-148">用户数据存储在客户端拥有的内存中，并在每次连接时进行记录。</span><span class="sxs-lookup"><span data-stu-id="1dab4-148">User data is stored in client-owned memory and recorded per connection.</span></span> <span data-ttu-id="1dab4-149">如果尚未设置用户数据指针，则返回 SQL_UD_NOTSET（NULL 指针）。</span><span class="sxs-lookup"><span data-stu-id="1dab4-149">If the user-data pointer has not been set, SQL_UD_NOTSET, a NULL pointer, is returned.</span></span>  
  
|<span data-ttu-id="1dab4-150">值</span><span class="sxs-lookup"><span data-stu-id="1dab4-150">Value</span></span>|<span data-ttu-id="1dab4-151">说明</span><span class="sxs-lookup"><span data-stu-id="1dab4-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1dab4-152">SQL_UD_NOTSET</span><span class="sxs-lookup"><span data-stu-id="1dab4-152">SQL_UD_NOTSET</span></span>|<span data-ttu-id="1dab4-153">未设置用户数据指针。</span><span class="sxs-lookup"><span data-stu-id="1dab4-153">No user-data pointer is set.</span></span>|  
|<span data-ttu-id="1dab4-154">任何其他值</span><span class="sxs-lookup"><span data-stu-id="1dab4-154">Any other value</span></span>|<span data-ttu-id="1dab4-155">用户数据的指针。</span><span class="sxs-lookup"><span data-stu-id="1dab4-155">A pointer to the user data.</span></span>|  
  
## <a name="sqlgetconnectattr-support-for-service-principal-names-spns"></a><span data-ttu-id="1dab4-156">对服务主体名称 (SPN) 的 SQLGetConnectAttr 支持</span><span class="sxs-lookup"><span data-stu-id="1dab4-156">SQLGetConnectAttr Support for Service Principal Names (SPNs)</span></span>  
 <span data-ttu-id="1dab4-157">SQLGetConnectAttr 可用于查询新连接属性的值，SQL_COPT_SS_SERVER_SPN、SQL_COPT_SS_FAILOVER_PARTNER_SPN、SQL_COPT_SS_MUTUALLY_AUTHENTICATED 和 SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD。</span><span class="sxs-lookup"><span data-stu-id="1dab4-157">SQLGetConnectAttr can be used to query the value of the new connection attributes SQL_COPT_SS_SERVER_SPN, SQL_COPT_SS_FAILOVER_PARTNER_SPN, SQL_COPT_SS_MUTUALLY_AUTHENTICATED, and SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD.</span></span> <span data-ttu-id="1dab4-158"> (SQLGetConnectOption 还可用于查询这些值。 ) </span><span class="sxs-lookup"><span data-stu-id="1dab4-158">(SQLGetConnectOption can also be used to query these values.)</span></span>  
  
 <span data-ttu-id="1dab4-159">SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD 仅对使用 Windows 身份验证的打开的连接可用。</span><span class="sxs-lookup"><span data-stu-id="1dab4-159">SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD is only available for open connections that use Windows Authentication.</span></span>  
  
 <span data-ttu-id="1dab4-160">如果尚未设置 SQL_COPT_SS_SERVER_SPN 或 SQL_COPT_SS_FAILOVER_PARTNER，则返回默认值（空字符串）。</span><span class="sxs-lookup"><span data-stu-id="1dab4-160">If SQL_COPT_SS_SERVER_SPN or SQL_COPT_SS_FAILOVER_PARTNER has not been set, the default value (an empty string) is returned.</span></span>  
  
 <span data-ttu-id="1dab4-161">有关 Spn 的详细信息，请参阅[&#40;ODBC&#41;的客户端连接中的服务主体名称 &#40;spn&#41; ](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="1dab4-161">For more information about SPNs, see [Service Principal Names &#40;SPNs&#41; in Client Connections &#40;ODBC&#41;](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dab4-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1dab4-162">See Also</span></span>  
 <span data-ttu-id="1dab4-163">[SQLGetConnectAttr 函数](https://go.microsoft.com/fwlink/?LinkId=59347) </span><span class="sxs-lookup"><span data-stu-id="1dab4-163">[SQLGetConnectAttr Function](https://go.microsoft.com/fwlink/?LinkId=59347) </span></span>  
 <span data-ttu-id="1dab4-164">[ODBC API 实现细节](odbc-api-implementation-details.md) </span><span class="sxs-lookup"><span data-stu-id="1dab4-164">[ODBC API Implementation Details](odbc-api-implementation-details.md) </span></span>  
 <span data-ttu-id="1dab4-165">[将 QUOTED_IDENTIFIER 设置 &#40;Transact-sql&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1dab4-165">[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql) </span></span>  
 <span data-ttu-id="1dab4-166">[SET ANSI_NULLS (Transact-SQL)](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1dab4-166">[SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span></span>  
 <span data-ttu-id="1dab4-167">[SET ANSI_PADDING (Transact-SQL)](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1dab4-167">[SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span></span>  
 [<span data-ttu-id="1dab4-168">SET ANSI_WARNINGS (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1dab4-168">SET ANSI_WARNINGS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-ansi-warnings-transact-sql)  
  
  
