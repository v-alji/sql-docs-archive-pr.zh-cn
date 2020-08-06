---
title: " (ODBC) 连接到数据源 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- checking connection states
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- SQLBrowseConnect function
- ODBC applications, connections
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLConnect function
- SQLDriveConnect function
- verifying connection states
- SQL Server Native Client ODBC driver, data sources
- SQL Server Native Client ODBC driver, connections
ms.assetid: ae30dd1d-06ae-452b-9618-8fd8cd7ba074
author: rothja
ms.author: jroth
ms.openlocfilehash: 25ce5954e45bb8070b5e99d8ebb7bfa9ad149c3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586643"
---
# <a name="connecting-to-a-data-source-odbc"></a><span data-ttu-id="3b40c-102">连接数据源 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="3b40c-102">Connecting to a Data Source (ODBC)</span></span>
  <span data-ttu-id="3b40c-103">在分配环境和连接句柄并设置连接属性后，应用程序将连接到数据源或驱动程序。</span><span class="sxs-lookup"><span data-stu-id="3b40c-103">After allocating environment and connection handles and setting any connection attributes, the application connects to the data source or driver.</span></span> <span data-ttu-id="3b40c-104">有三种可用于连接的函数：</span><span class="sxs-lookup"><span data-stu-id="3b40c-104">There are three functions you can use to connect:</span></span>  
  
-   <span data-ttu-id="3b40c-105">**SQLConnect**</span><span class="sxs-lookup"><span data-stu-id="3b40c-105">**SQLConnect**</span></span>  
  
-   <span data-ttu-id="3b40c-106">**SQLDriverConnect**</span><span class="sxs-lookup"><span data-stu-id="3b40c-106">**SQLDriverConnect**</span></span>  
  
-   <span data-ttu-id="3b40c-107">**SQLBrowseConnect**</span><span class="sxs-lookup"><span data-stu-id="3b40c-107">**SQLBrowseConnect**</span></span>  
  
 <span data-ttu-id="3b40c-108">有关建立与数据源的连接的详细信息，包括可用的各种连接字符串选项，请参阅将[连接字符串关键字用于 SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="3b40c-108">For more information about making connections to a data source, including the various connection string options available, see [Using Connection String Keywords with SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
## <a name="sqlconnect"></a><span data-ttu-id="3b40c-109">SQLConnect</span><span class="sxs-lookup"><span data-stu-id="3b40c-109">SQLConnect</span></span>  
 <span data-ttu-id="3b40c-110">**SQLConnect**是最简单的连接函数。</span><span class="sxs-lookup"><span data-stu-id="3b40c-110">**SQLConnect** is the simplest connection function.</span></span> <span data-ttu-id="3b40c-111">它接受三个参数：数据源名称、用户 ID 和密码。</span><span class="sxs-lookup"><span data-stu-id="3b40c-111">It accepts three parameters: a data source name, a user ID, and a password.</span></span> <span data-ttu-id="3b40c-112">当这三个参数包含连接到数据库所需的所有信息时，请使用**SQLConnect** 。</span><span class="sxs-lookup"><span data-stu-id="3b40c-112">Use **SQLConnect** when these three parameters contain all the information needed to connect to the database.</span></span> <span data-ttu-id="3b40c-113">为此，请使用**SQLDataSources**生成数据源列表;提示用户输入数据源、用户 ID 和密码;然后调用**SQLConnect**。</span><span class="sxs-lookup"><span data-stu-id="3b40c-113">To do this, build a list of data sources using **SQLDataSources**; prompt the user for a data source, user ID, and password; and then call **SQLConnect**.</span></span>  
  
 <span data-ttu-id="3b40c-114">**SQLConnect**假定数据源名称、用户 ID 和密码足以连接到数据源，并且 odbc 数据源包含 odbc 驱动程序建立连接所需的所有其他信息。</span><span class="sxs-lookup"><span data-stu-id="3b40c-114">**SQLConnect** assumes that a data source name, user ID, and password are sufficient to connect to a data source and that the ODBC data source contains all other information the ODBC driver needs to make the connection.</span></span> <span data-ttu-id="3b40c-115">与[SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md)和[SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md)不同， **SQLConnect**不使用连接字符串。</span><span class="sxs-lookup"><span data-stu-id="3b40c-115">Unlike [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) and [SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md), **SQLConnect** does not use a connection string.</span></span>  
  
## <a name="sqldriverconnect"></a><span data-ttu-id="3b40c-116">SQLDriverConnect</span><span class="sxs-lookup"><span data-stu-id="3b40c-116">SQLDriverConnect</span></span>  
 <span data-ttu-id="3b40c-117">当需要超过数据源名称、用户 ID 和密码的信息时，将使用**SQLDriverConnect** 。</span><span class="sxs-lookup"><span data-stu-id="3b40c-117">**SQLDriverConnect** is used when more information than the data source name, user ID, and password is required.</span></span> <span data-ttu-id="3b40c-118">**SQLDriverConnect**的参数之一是包含驱动程序特定信息的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="3b40c-118">One of the parameters to **SQLDriverConnect** is a connection string containing driver-specific information.</span></span> <span data-ttu-id="3b40c-119">由于以下原因，你可以使用**SQLDriverConnect**而不是**SQLConnect** ：</span><span class="sxs-lookup"><span data-stu-id="3b40c-119">You might use **SQLDriverConnect** instead of **SQLConnect** for the following reasons:</span></span>  
  
-   <span data-ttu-id="3b40c-120">在连接时指定特定于驱动程序的信息。</span><span class="sxs-lookup"><span data-stu-id="3b40c-120">To specify driver-specific information at connect time.</span></span>  
  
-   <span data-ttu-id="3b40c-121">请求驱动程序提示用户输入连接信息。</span><span class="sxs-lookup"><span data-stu-id="3b40c-121">To request that the driver prompt the user for connection information.</span></span>  
  
-   <span data-ttu-id="3b40c-122">不使用 ODBC 数据源进行连接。</span><span class="sxs-lookup"><span data-stu-id="3b40c-122">To connect without using an ODBC data source.</span></span>  
  
 <span data-ttu-id="3b40c-123">**SQLDriverConnect**连接字符串包含一系列关键字/值对，这些关键字值对指定 ODBC 驱动程序支持的所有连接信息。</span><span class="sxs-lookup"><span data-stu-id="3b40c-123">The **SQLDriverConnect** connection string contains a series of keyword-value pairs that specify all connection information supported by an ODBC driver.</span></span> <span data-ttu-id="3b40c-124">每个驱动程序都支持标准 ODBC 关键字（DSN、FILEDSN、DRIVER、UID、PWD 和 SAVEFILE），以及用于驱动程序支持的所有连接信息的特定于驱动程序的关键字。</span><span class="sxs-lookup"><span data-stu-id="3b40c-124">Each driver supports the standard ODBC keywords (DSN, FILEDSN, DRIVER, UID, PWD, and SAVEFILE) in addition to driver-specific keywords for all connection information supported by the driver.</span></span> <span data-ttu-id="3b40c-125">**SQLDriverConnect**可用于在不使用数据源的情况下进行连接。</span><span class="sxs-lookup"><span data-stu-id="3b40c-125">**SQLDriverConnect** can be used to connect without a data source.</span></span> <span data-ttu-id="3b40c-126">例如，设计为与实例建立 "无 DSN" 连接的应用程序 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可以使用连接字符串调用**SQLDriverConnect** ，该连接字符串定义登录 ID、密码、网络库、要连接到的服务器名称以及要使用的默认数据库。</span><span class="sxs-lookup"><span data-stu-id="3b40c-126">For example, an application that is designed to make a "DSN-less" connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can call **SQLDriverConnect** with a connection string that defines the login ID, password, network library, server name to connect to, and default database to use.</span></span>  
  
 <span data-ttu-id="3b40c-127">当使用**SQLDriverConnect**时，有两个选项可提示用户输入所需的任何连接信息：</span><span class="sxs-lookup"><span data-stu-id="3b40c-127">When using **SQLDriverConnect**, there are two options for prompting the user for any needed connection information:</span></span>  
  
-   <span data-ttu-id="3b40c-128">应用程序对话框</span><span class="sxs-lookup"><span data-stu-id="3b40c-128">Application dialog box</span></span>  
  
     <span data-ttu-id="3b40c-129">你可以创建一个应用程序对话框，以提示输入连接信息，然后使用空窗口句柄和*DriverCompletion*设置为 SQL_DRIVER_NOPROMPT 来调用**SQLDriverConnect** 。</span><span class="sxs-lookup"><span data-stu-id="3b40c-129">You can create an application dialog box that prompts for connection information, and then calls **SQLDriverConnect** with a NULL window handle and *DriverCompletion* set to SQL_DRIVER_NOPROMPT.</span></span> <span data-ttu-id="3b40c-130">这些参数设置将禁止 ODBC 驱动程序打开自己的对话框。</span><span class="sxs-lookup"><span data-stu-id="3b40c-130">These parameter settings prevent the ODBC driver from opening its own dialog box.</span></span> <span data-ttu-id="3b40c-131">在对应用程序的用户界面进行控制非常重要时，使用此方法。</span><span class="sxs-lookup"><span data-stu-id="3b40c-131">This method is used when it is important to control the user interface of the application.</span></span>  
  
-   <span data-ttu-id="3b40c-132">驱动程序对话框</span><span class="sxs-lookup"><span data-stu-id="3b40c-132">Driver dialog box</span></span>  
  
     <span data-ttu-id="3b40c-133">可以编写应用程序代码，将有效的窗口句柄传递到**SQLDriverConnect** ，并将*DriverCompletion*参数设置为 SQL_DRIVER_COMPLETE、SQL_DRIVER_PROMPT 或 SQL_DRIVER_COMPLETE_REQUIRED。</span><span class="sxs-lookup"><span data-stu-id="3b40c-133">You can code the application to pass a valid window handle to **SQLDriverConnect** and set the *DriverCompletion* parameter to SQL_DRIVER_COMPLETE, SQL_DRIVER_PROMPT, or SQL_DRIVER_COMPLETE_REQUIRED.</span></span> <span data-ttu-id="3b40c-134">驱动程序然后生成一个对话框，以便提示用户输入连接信息。</span><span class="sxs-lookup"><span data-stu-id="3b40c-134">The driver then generates a dialog box to prompt the user for connection information.</span></span> <span data-ttu-id="3b40c-135">此方法可以简化应用程序代码。</span><span class="sxs-lookup"><span data-stu-id="3b40c-135">This method simplifies the application code.</span></span>  
  
## <a name="sqlbrowseconnect"></a><span data-ttu-id="3b40c-136">SQLBrowseConnect</span><span class="sxs-lookup"><span data-stu-id="3b40c-136">SQLBrowseConnect</span></span>  
 <span data-ttu-id="3b40c-137">**SQLBrowseConnect**（如**SQLDriverConnect**）使用连接字符串。</span><span class="sxs-lookup"><span data-stu-id="3b40c-137">**SQLBrowseConnect**, like **SQLDriverConnect**, uses a connection string.</span></span> <span data-ttu-id="3b40c-138">但是，通过使用**SQLBrowseConnect**，应用程序可以在运行时以迭代方式构造完整的连接字符串与数据源。</span><span class="sxs-lookup"><span data-stu-id="3b40c-138">However, by using **SQLBrowseConnect**, an application can construct a complete connection string iteratively with the data source at run time.</span></span> <span data-ttu-id="3b40c-139">这允许应用程序执行以下两种操作：</span><span class="sxs-lookup"><span data-stu-id="3b40c-139">This allows the application to do two things:</span></span>  
  
-   <span data-ttu-id="3b40c-140">生成自己的对话框以提示输入此信息，因此保留对其用户界面的控制。</span><span class="sxs-lookup"><span data-stu-id="3b40c-140">Build its own dialog boxes to prompt for this information, thereby retaining control over its user interface.</span></span>  
  
-   <span data-ttu-id="3b40c-141">浏览系统以找到可由特定的驱动程序使用的数据源，这可能要执行若干步骤。</span><span class="sxs-lookup"><span data-stu-id="3b40c-141">Browse the system for data sources that can be used by a particular driver, possibly in several steps.</span></span>  
  
     <span data-ttu-id="3b40c-142">例如，用户可能要首先浏览网络以找到服务器，然后在选择某一服务器后，浏览该服务器以找到驱动程序可访问的数据库。</span><span class="sxs-lookup"><span data-stu-id="3b40c-142">For example, the user might first browse the network for servers and, after choosing a server, browse the server for databases accessible by the driver.</span></span>  
  
 <span data-ttu-id="3b40c-143">当**SQLBrowseConnect**完成成功连接时，它将返回一个连接字符串，该字符串可用于对**SQLDriverConnect**的后续调用。</span><span class="sxs-lookup"><span data-stu-id="3b40c-143">When **SQLBrowseConnect** completes a successful connection, it returns a connection string that can be used on subsequent calls to **SQLDriverConnect**.</span></span>  
  
 <span data-ttu-id="3b40c-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序始终在成功的**SQLConnect**、 **SQLDriverConnect**或**SQLBrowseConnect**上返回 SQL_SUCCESS_WITH_INFO。</span><span class="sxs-lookup"><span data-stu-id="3b40c-144">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver always returns SQL_SUCCESS_WITH_INFO on a successful **SQLConnect**, **SQLDriverConnect**, or **SQLBrowseConnect**.</span></span> <span data-ttu-id="3b40c-145">如果 ODBC 应用程序在获取 SQL_SUCCESS_WITH_INFO 后调用**SQLGetDiagRec** ，则它可能会收到以下消息：</span><span class="sxs-lookup"><span data-stu-id="3b40c-145">When an ODBC application calls **SQLGetDiagRec** after getting SQL_SUCCESS_WITH_INFO, it can receive the following messages:</span></span>  
  
 <span data-ttu-id="3b40c-146">5701</span><span class="sxs-lookup"><span data-stu-id="3b40c-146">5701</span></span>  
 <span data-ttu-id="3b40c-147">指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将用户的上下文置于在数据源中定义的默认数据库中，或者置于为在连接中使用的登录 ID 定义的默认数据库中（如果数据源没有默认数据库）。</span><span class="sxs-lookup"><span data-stu-id="3b40c-147">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] put the user's context into the default database defined in the data source, or into the default database defined for the login ID used in the connection if the data source did not have a default database.</span></span>  
  
 <span data-ttu-id="3b40c-148">5703</span><span class="sxs-lookup"><span data-stu-id="3b40c-148">5703</span></span>  
 <span data-ttu-id="3b40c-149">指示要在服务器上使用的语言。</span><span class="sxs-lookup"><span data-stu-id="3b40c-149">Indicates the language being used on the server.</span></span>  
  
 <span data-ttu-id="3b40c-150">以下示例显示系统管理员对成功的连接返回的消息：</span><span class="sxs-lookup"><span data-stu-id="3b40c-150">The following example shows the message returned on a successful connection by the system administrator:</span></span>  
  
```  
szSqlState = "01000", *pfNativeError = 5701,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
       Changed database context to 'pubs'."  
szSqlState = "01000", *pfNativeError = 5703,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
       Changed language setting to 'us_english'."  
```  
  
 <span data-ttu-id="3b40c-151">您可以忽略消息 5701 和 5703；它们仅供参考。</span><span class="sxs-lookup"><span data-stu-id="3b40c-151">You can ignore messages 5701 and 5703; they are only informational.</span></span> <span data-ttu-id="3b40c-152">但是，不应忽视 SQL_SUCCESS_WITH_INFO 返回代码，因为可能返回并非 5701 或 5703 的其他消息。</span><span class="sxs-lookup"><span data-stu-id="3b40c-152">You should not, however, ignore a SQL_SUCCESS_WITH_INFO return code because messages other than 5701 or 5703 may be returned.</span></span> <span data-ttu-id="3b40c-153">例如，如果驱动程序连接到运行实例的服务器 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，并且该服务器具有过时的目录存储过程，则 SQL_SUCCESS_WITH_INFO 之后通过**SQLGetDiagRec**返回的错误之一如下：</span><span class="sxs-lookup"><span data-stu-id="3b40c-153">For example, if a driver connects to a server running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with outdated catalog stored procedures, one of the errors returned through **SQLGetDiagRec** after a SQL_SUCCESS_WITH_INFO is:</span></span>  
  
```  
SqlState:   01000  
pfNative:   0  
szErrorMsg: "[Microsoft][SQL Server Native Client]The ODBC  
            catalog stored procedures installed on server  
            my65server are version 06.50.0193; version 07.00.0205  
            or later is required to ensure proper operation.  
            Please contact your system administrator."  
```  
  
 <span data-ttu-id="3b40c-154">连接应用程序的错误处理函数 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 应调用**SQLGetDiagRec** ，直到它返回 SQL_NO_DATA。</span><span class="sxs-lookup"><span data-stu-id="3b40c-154">The error handling function of an application for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connections should call **SQLGetDiagRec** until it returns SQL_NO_DATA.</span></span> <span data-ttu-id="3b40c-155">然后，它应作用于*pfNative*代码不是5701或5703的任何消息。</span><span class="sxs-lookup"><span data-stu-id="3b40c-155">It should then act on any messages other than the ones with a *pfNative* code of 5701 or 5703.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b40c-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3b40c-156">See Also</span></span>  
 [<span data-ttu-id="3b40c-157">与 SQL Server &#40;ODBC&#41;通信</span><span class="sxs-lookup"><span data-stu-id="3b40c-157">Communicating with SQL Server &#40;ODBC&#41;</span></span>](communicating-with-sql-server-odbc.md)  
  
  
