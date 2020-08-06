---
title: SQLDriverConnect |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLDriverConnect function
ms.assetid: a1e38e2c-3a97-42d1-9c45-a0ca3282ffd1
author: rothja
ms.author: jroth
ms.openlocfilehash: 40691dfb381883b59155607fb56f4933820e3e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691716"
---
# <a name="sqldriverconnect"></a><span data-ttu-id="ff439-102">SQLDriverConnect</span><span class="sxs-lookup"><span data-stu-id="ff439-102">SQLDriverConnect</span></span>
  <span data-ttu-id="ff439-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序定义可替换或增强连接字符串关键字的连接属性。</span><span class="sxs-lookup"><span data-stu-id="ff439-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver defines connection attributes that either replace or enhance connection-string keywords.</span></span> <span data-ttu-id="ff439-104">一些连接字符串关键字已由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序指定了默认值。</span><span class="sxs-lookup"><span data-stu-id="ff439-104">Several connection-string keywords have default values specified by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
 <span data-ttu-id="ff439-105">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序中可用的关键字列表，请参阅将[连接字符串关键字用于 SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="ff439-105">For a list of the keywords available in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, see [Using Connection String Keywords with SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
 <span data-ttu-id="ff439-106">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接属性和驱动程序默认行为的详细信息，请参阅[SQLSetConnectAttr](sqlsetconnectattr.md)。</span><span class="sxs-lookup"><span data-stu-id="ff439-106">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection attributes and driver default behaviors, see [SQLSetConnectAttr](sqlsetconnectattr.md).</span></span>  
  
 <span data-ttu-id="ff439-107">有关对 Native Client 有效的连接字符串关键字的讨论 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅将[连接字符串关键字用于 SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="ff439-107">For a discussion of connection string keywords that are valid for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, see [Using Connection String Keywords with SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
 <span data-ttu-id="ff439-108">当 `SQLDriverConnect` *DriverCompletion*参数值 SQL_DRIVER_PROMPT、SQL_DRIVER_COMPLETE 或 SQL_DRIVER_COMPLETE_REQUIRED 时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序将从显示的对话框中检索关键字值。</span><span class="sxs-lookup"><span data-stu-id="ff439-108">When the `SQLDriverConnect`*DriverCompletion* parameter value is SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE, or SQL_DRIVER_COMPLETE_REQUIRED, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver retrieves keyword values from the displayed dialog box.</span></span> <span data-ttu-id="ff439-109">如果关键字值传递到连接字符串中，并且用户未在对话框中更改关键字的值，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序将使用连接字符串中的值。</span><span class="sxs-lookup"><span data-stu-id="ff439-109">If the keyword value is passed in the connection string and the user does not alter the value for the keyword in the dialog box, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver uses the value from the connection string.</span></span> <span data-ttu-id="ff439-110">如果在连接字符串中未设置值，并且用户在对话框中未指定任何值，则驱动程序将使用默认值。</span><span class="sxs-lookup"><span data-stu-id="ff439-110">If the value is not set in the connection string and the user makes no assignment in the dialog box, the driver uses the default.</span></span>  
  
 <span data-ttu-id="ff439-111">`SQLDriverConnect`如果任何*DriverCompletion*值需要 (或可能需要) 驱动程序的 "连接" 对话框的显示，则必须指定有效的*WindowHandle* 。</span><span class="sxs-lookup"><span data-stu-id="ff439-111">`SQLDriverConnect` must be given a valid *WindowHandle* when any *DriverCompletion* value requires (or could require) the display of the driver's connection dialog box.</span></span> <span data-ttu-id="ff439-112">无效句柄将返回 SQL_ERROR。</span><span class="sxs-lookup"><span data-stu-id="ff439-112">An invalid handle returns SQL_ERROR.</span></span>  
  
 <span data-ttu-id="ff439-113">指定 DRIVER 或 DSN 关键字。</span><span class="sxs-lookup"><span data-stu-id="ff439-113">Specify either the DRIVER or DSN keywords.</span></span> <span data-ttu-id="ff439-114">ODBC 规定，如果同时指定了这两个关键字，驱动程序将使用左边的关键字，而忽略另一个关键字。</span><span class="sxs-lookup"><span data-stu-id="ff439-114">ODBC states that a driver uses the leftmost of these two keywords and ignores the other if both are specified.</span></span> <span data-ttu-id="ff439-115">如果指定了驱动程序，或者指定了驱动程序的最左侧，并且 `SQLDriverConnect` *DriverCompletion*参数值 SQL_DRIVER_NOPROMPT，则需要 SERVER 关键字和适当的值。</span><span class="sxs-lookup"><span data-stu-id="ff439-115">If DRIVER is specified, or is the leftmost of the two, and the `SQLDriverConnect`*DriverCompletion* parameter value is SQL_DRIVER_NOPROMPT, the SERVER keyword and an appropriate value are required.</span></span>  
  
 <span data-ttu-id="ff439-116">当指定 SQL_DRIVER_NOPROMPT 时，用户身份验证关键字必须具有值。</span><span class="sxs-lookup"><span data-stu-id="ff439-116">When SQL_DRIVER_NOPROMPT is specified, user authentication keywords must be present with values.</span></span> <span data-ttu-id="ff439-117">驱动程序确保字符串“Trusted_Connection=yes”或 UID 和 PWD 关键字存在。</span><span class="sxs-lookup"><span data-stu-id="ff439-117">The driver ensures that either the string "Trusted_Connection=yes" or both the UID and PWD keywords are present.</span></span>  
  
 <span data-ttu-id="ff439-118">如果*DriverCompletion*参数值为 SQL_DRIVER_NOPROMPT 或 SQL_DRIVER_COMPLETE_REQUIRED 并且语言或数据库来自连接字符串，并且两者都无效，则 `SQLDriverConnect` 返回 SQL_ERROR。</span><span class="sxs-lookup"><span data-stu-id="ff439-118">If the *DriverCompletion* parameter value is SQL_DRIVER_NOPROMPT or SQL_DRIVER_COMPLETE_REQUIRED and the language or database comes from the connection string and either is invalid, `SQLDriverConnect` returns SQL_ERROR.</span></span>  
  
 <span data-ttu-id="ff439-119">如果*DriverCompletion*参数值为 SQL_DRIVER_NOPROMPT 或 SQL_DRIVER_COMPLETE_REQUIRED 并且语言或数据库来自 ODBC 数据源定义并且无效，则 `SQLDriverConnect` 使用默认语言或数据库作为指定用户 ID 并返回 SQL_SUCCESS_WITH_INFO。</span><span class="sxs-lookup"><span data-stu-id="ff439-119">If the *DriverCompletion* parameter value is SQL_DRIVER_NOPROMPT or SQL_DRIVER_COMPLETE_REQUIRED and the language or database comes from the ODBC data source definitions and either is invalid, `SQLDriverConnect` uses the default language or database for the specified user ID and returns SQL_SUCCESS_WITH_INFO.</span></span>  
  
 <span data-ttu-id="ff439-120">如果*DriverCompletion*参数值为 SQL_DRIVER_COMPLETE 或 SQL_DRIVER_PROMPT 并且如果语言或数据库无效，则将重新 `SQLDriverConnect` 将其</span><span class="sxs-lookup"><span data-stu-id="ff439-120">If the *DriverCompletion* parameter value is SQL_DRIVER_COMPLETE or SQL_DRIVER_PROMPT and if the language or database is invalid, `SQLDriverConnect` redisplays the dialog box.</span></span>  
  
## <a name="sqldriverconnect-support-for-high-availability-disaster-recovery"></a><span data-ttu-id="ff439-121">对高可用性、灾难恢复的 SQLDriverConnect 支持</span><span class="sxs-lookup"><span data-stu-id="ff439-121">SQLDriverConnect Support for High Availability, Disaster Recovery</span></span>  
 <span data-ttu-id="ff439-122">有关使用 `SQLDriverConnect` 连接到群集的详细信息 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] ，请参阅对[高可用性和灾难恢复的 SQL Server Native Client 支持](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)。</span><span class="sxs-lookup"><span data-stu-id="ff439-122">For more information about using `SQLDriverConnect` to connect to a [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] cluster, see [SQL Server Native Client Support for High Availability, Disaster Recovery](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).</span></span>  
  
## <a name="sqldriverconnect-support-for-service-principal-names-spns"></a><span data-ttu-id="ff439-123">对服务主体名称 (SPN) 的 SQLDriverConnect 支持</span><span class="sxs-lookup"><span data-stu-id="ff439-123">SQLDriverConnect Support for Service Principal Names (SPNs)</span></span>  
 <span data-ttu-id="ff439-124">SQLDDriverConnect 将使用 ODBC Login 对话框 boxwhen 提示已启用。</span><span class="sxs-lookup"><span data-stu-id="ff439-124">SQLDDriverConnect will use the ODBC Login dialog boxwhen prompting is enabled.</span></span> <span data-ttu-id="ff439-125">这允许为主体服务器及其故障转移伙伴输入 SPN。</span><span class="sxs-lookup"><span data-stu-id="ff439-125">This allows SPNs to be entered for both the principal server and its failover partner.</span></span>  
  
 <span data-ttu-id="ff439-126">SQLDriverConnect 将接受新的连接字符串关键字 `ServerSPN` 和 `FailoverPartnerSPN` ，并识别 SQL_COPT_SS_SERVER_SPN 和 SQL_COPT_SS_FAILOVER_PARTNER_SPN 的新连接属性。</span><span class="sxs-lookup"><span data-stu-id="ff439-126">SQLDriverConnect will accept the new connection string keywords `ServerSPN` and `FailoverPartnerSPN`, and will recognize the new connection attributes SQL_COPT_SS_SERVER_SPN and SQL_COPT_SS_FAILOVER_PARTNER_SPN.</span></span>  
  
 <span data-ttu-id="ff439-127">当多次指定某个连接属性值时，以编程方式设置的值优先于 DSN 中的值和连接字符串中的值。</span><span class="sxs-lookup"><span data-stu-id="ff439-127">When a connection attribute value is specified more than once, a value that is set programmatically takes precedence over the value in a DSN and a value in a connection string.</span></span> <span data-ttu-id="ff439-128">DSN 中的值优先于连接字符串中的值。</span><span class="sxs-lookup"><span data-stu-id="ff439-128">A value in a DSN takes precedence over a value in a connection string.</span></span>  
  
 <span data-ttu-id="ff439-129">当打开连接时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 将 SQL_COPT_SS_MUTUALLY_AUTHENTICATED 和 SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD 设置为用于打开此连接的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="ff439-129">When a connection is opened, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sets SQL_COPT_SS_MUTUALLY_AUTHENTICATED and SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD to the authentication method used to open the connection.</span></span>  
  
 <span data-ttu-id="ff439-130">有关 Spn 的详细信息，请参阅[&#40;ODBC&#41;的客户端连接中的服务主体名称 &#40;spn&#41; ](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="ff439-130">For more information about SPNs, see [Service Principal Names &#40;SPNs&#41; in Client Connections &#40;ODBC&#41;](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ff439-131">示例</span><span class="sxs-lookup"><span data-stu-id="ff439-131">Examples</span></span>  
 <span data-ttu-id="ff439-132">以下调用说明了所需的最少数据量 `SQLDriverConnect` ：</span><span class="sxs-lookup"><span data-stu-id="ff439-132">The following call illustrates the least amount of data required for `SQLDriverConnect`:</span></span>  
  
```  
SQLDriverConnect(hdbc, hwnd,  
    (SQLTCHAR*) TEXT("DRIVER={SQL Server Native Client 10};"), SQL_NTS, szOutConn,  
    MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
```  
  
 <span data-ttu-id="ff439-133">以下连接字符串演示了在 SQL_DRIVER_NOPROMPT *DriverCompletion*参数值时所需的最小数据量：</span><span class="sxs-lookup"><span data-stu-id="ff439-133">The following connection strings illustrate minimum required data when the *DriverCompletion* parameter value is SQL_DRIVER_NOPROMPT:</span></span>  
  
```  
"DSN=Human Resources;Trusted_Connection=yes"  
  
"FILEDSN=HR_FDSN;Trusted_Connection=yes"  
  
"DRIVER={SQL Server Native Client 10};SERVER=(local);Trusted_Connection=yes"  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff439-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ff439-134">See Also</span></span>  
 <span data-ttu-id="ff439-135">[SQLDriverConnect 函数](https://go.microsoft.com/fwlink/?LinkId=59340) </span><span class="sxs-lookup"><span data-stu-id="ff439-135">[SQLDriverConnect Function](https://go.microsoft.com/fwlink/?LinkId=59340) </span></span>  
 <span data-ttu-id="ff439-136">[ODBC API 实现细节](odbc-api-implementation-details.md) </span><span class="sxs-lookup"><span data-stu-id="ff439-136">[ODBC API Implementation Details](odbc-api-implementation-details.md) </span></span>  
 <span data-ttu-id="ff439-137">[SET ANSI_NULLS (Transact-SQL)](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ff439-137">[SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span></span>  
 <span data-ttu-id="ff439-138">[SET ANSI_PADDING (Transact-SQL)](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ff439-138">[SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span></span>  
 [<span data-ttu-id="ff439-139">SET ANSI_WARNINGS (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ff439-139">SET ANSI_WARNINGS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-ansi-warnings-transact-sql)  
  
  
