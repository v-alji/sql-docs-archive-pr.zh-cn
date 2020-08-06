---
title: 创建 SQL Server Native Client ODBC 驱动程序应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, architecture
- SQL Server Native Client ODBC driver, creating applications
- ODBC function calls
- ODBC, header files
- ODBC applications
- ODBC applications, creating
- SQL Server Native Client ODBC driver, extensions
- applications [SQL Server Native Client]
- SQL Server Native Client ODBC driver, ODBC architecture
- extensions [ODBC]
- ODBC, driver extensions
- function calls [ODBC]
ms.assetid: c83c36e2-734e-4960-bc7e-92235910bc6f
author: rothja
ms.author: jroth
ms.openlocfilehash: c8a1719f8b60885810d9b2f8a1f1023a7ffe6e47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692353"
---
# <a name="creating-a-sql-server-native-client-odbc-driver-application"></a><span data-ttu-id="55e88-102">创建 SQL Server Native Client ODBC 驱动程序应用程序</span><span class="sxs-lookup"><span data-stu-id="55e88-102">Creating a SQL Server Native Client ODBC Driver Application</span></span>
  <span data-ttu-id="55e88-103">ODBC 体系结构具有四个组件，可以执行以下功能：</span><span class="sxs-lookup"><span data-stu-id="55e88-103">ODBC architecture has four components that perform the following functions.</span></span>  
  
|<span data-ttu-id="55e88-104">组件</span><span class="sxs-lookup"><span data-stu-id="55e88-104">Component</span></span>|<span data-ttu-id="55e88-105">函数</span><span class="sxs-lookup"><span data-stu-id="55e88-105">Function</span></span>|  
|---------------|--------------|  
|<span data-ttu-id="55e88-106">应用程序</span><span class="sxs-lookup"><span data-stu-id="55e88-106">Application</span></span>|<span data-ttu-id="55e88-107">调用 ODBC 函数以与 ODBC 数据源通信、提交 SQL 语句以及处理结果集。</span><span class="sxs-lookup"><span data-stu-id="55e88-107">Calls ODBC functions to communicate with an ODBC data source, submits SQL statements, and processes result sets.</span></span>|  
|<span data-ttu-id="55e88-108">驱动程序管理器</span><span class="sxs-lookup"><span data-stu-id="55e88-108">Driver Manager</span></span>|<span data-ttu-id="55e88-109">管理应用程序和该应用程序使用的所有 ODBC 驱动程序之间的通信。</span><span class="sxs-lookup"><span data-stu-id="55e88-109">Manages communication between an application and all ODBC drivers used by the application.</span></span>|  
|<span data-ttu-id="55e88-110">驱动程序</span><span class="sxs-lookup"><span data-stu-id="55e88-110">Driver</span></span>|<span data-ttu-id="55e88-111">处理来自应用程序的所有 ODBC 函数调用、连接到数据源、将 SQL 语句从应用程序传递到数据源以及将结果返回给应用程序。</span><span class="sxs-lookup"><span data-stu-id="55e88-111">Processes all ODBC function calls from the application, connects to a data source, passes SQL statements from the application to the data source, and returns results to the application.</span></span> <span data-ttu-id="55e88-112">必要时，驱动程序将来自应用程序的 ODBC SQL 转换为数据源使用的本机 SQL。</span><span class="sxs-lookup"><span data-stu-id="55e88-112">If necessary, the driver translates ODBC SQL from the application to native SQL used by the data source.</span></span>|  
|<span data-ttu-id="55e88-113">数据源</span><span class="sxs-lookup"><span data-stu-id="55e88-113">Data source</span></span>|<span data-ttu-id="55e88-114">包含驱动程序访问 DBMS 中数据的特定实例所需的所有信息。</span><span class="sxs-lookup"><span data-stu-id="55e88-114">Contains all information a driver needs to access a specific instance of data in a DBMS.</span></span>|  
  
 <span data-ttu-id="55e88-115">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序与实例通信的应用程序 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="55e88-115">An application that uses the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver to communicate with an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] performs the following tasks:</span></span>  
  
-   <span data-ttu-id="55e88-116">与数据源连接</span><span class="sxs-lookup"><span data-stu-id="55e88-116">Connects with a data source</span></span>  
  
-   <span data-ttu-id="55e88-117">将 SQL 语句发送给数据源</span><span class="sxs-lookup"><span data-stu-id="55e88-117">Sends SQL statements to the data source</span></span>  
  
-   <span data-ttu-id="55e88-118">处理来自数据源的语句结果</span><span class="sxs-lookup"><span data-stu-id="55e88-118">Processes the results of statements from the data source</span></span>  
  
-   <span data-ttu-id="55e88-119">处理错误和消息</span><span class="sxs-lookup"><span data-stu-id="55e88-119">Processes errors and messages</span></span>  
  
-   <span data-ttu-id="55e88-120">终止与数据源的连接</span><span class="sxs-lookup"><span data-stu-id="55e88-120">Terminates the connection to the data source</span></span>  
  
 <span data-ttu-id="55e88-121">为 Native Client ODBC 驱动程序编写的更复杂的应用程序 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 也可能执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="55e88-121">A more complex application written for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver might also perform the following tasks:</span></span>  
  
-   <span data-ttu-id="55e88-122">使用游标控制在结果集中的位置</span><span class="sxs-lookup"><span data-stu-id="55e88-122">Use cursors to control location in a result set</span></span>  
  
-   <span data-ttu-id="55e88-123">请求进行事务控制的提交或回滚操作</span><span class="sxs-lookup"><span data-stu-id="55e88-123">Request commit or rollback operations for transaction control</span></span>  
  
-   <span data-ttu-id="55e88-124">执行涉及两个或多个服务器的分布式事务</span><span class="sxs-lookup"><span data-stu-id="55e88-124">Perform distributed transactions involving two or more servers</span></span>  
  
-   <span data-ttu-id="55e88-125">在远程服务器上运行存储过程</span><span class="sxs-lookup"><span data-stu-id="55e88-125">Run stored procedures on the remote server</span></span>  
  
-   <span data-ttu-id="55e88-126">调用目录函数来查询有关结果集的属性</span><span class="sxs-lookup"><span data-stu-id="55e88-126">Call catalog functions to inquire about the attributes of a result set</span></span>  
  
-   <span data-ttu-id="55e88-127">执行大容量复制操作</span><span class="sxs-lookup"><span data-stu-id="55e88-127">Perform bulk copy operations</span></span>  
  
-   <span data-ttu-id="55e88-128">管理大型数据 (\*\*varchar (max) \*\*、 **nvarchar (max) **和**varbinary (最大**) 列) 操作</span><span class="sxs-lookup"><span data-stu-id="55e88-128">Manage large data (**varchar(max)**, **nvarchar(max)**, and **varbinary(max)** columns) operations</span></span>  
  
-   <span data-ttu-id="55e88-129">在配置数据库镜像时使用重新连接逻辑以便于故障转移</span><span class="sxs-lookup"><span data-stu-id="55e88-129">Use reconnection logic to facilitate failover when database mirroring is configured</span></span>  
  
-   <span data-ttu-id="55e88-130">记录性能数据和长时间运行的查询</span><span class="sxs-lookup"><span data-stu-id="55e88-130">Log performance data and long-running queries</span></span>  
  
 <span data-ttu-id="55e88-131">若要进行 ODBC 函数调用，C 或 C++ 应用程序必须包括 sql.h、sqlext.h 和 sqltypes.h 头文件。</span><span class="sxs-lookup"><span data-stu-id="55e88-131">To make ODBC function calls, a C or C++ application must include the sql.h, sqlext.h, and sqltypes.h header files.</span></span> <span data-ttu-id="55e88-132">若要进行 ODBC 安装程序 API 函数调用，应用程序必须包括 odbcinst.h 头文件。</span><span class="sxs-lookup"><span data-stu-id="55e88-132">To make calls to the ODBC installer API functions, an application must include the odbcinst.h header file.</span></span> <span data-ttu-id="55e88-133">Unicode ODBC 应用程序必须包括 sqlucode.h 头文件。</span><span class="sxs-lookup"><span data-stu-id="55e88-133">A Unicode ODBC application must include the sqlucode.h header file.</span></span> <span data-ttu-id="55e88-134">ODBC 应用程序必须与 odbc32.lib 文件链接。</span><span class="sxs-lookup"><span data-stu-id="55e88-134">ODBC applications must be linked with the odbc32.lib file.</span></span> <span data-ttu-id="55e88-135">调用 ODBC 安装程序 API 函数的 ODBC 应用程序必须与 odbccp32.lib 文件链接。</span><span class="sxs-lookup"><span data-stu-id="55e88-135">ODBC applications that call the ODBC installer API functions must be linked with the odbccp32.lib file.</span></span> <span data-ttu-id="55e88-136">这些文件包括在 Windows 平台 SDK 中。</span><span class="sxs-lookup"><span data-stu-id="55e88-136">These files are included in the Windows Platform SDK.</span></span>  
  
 <span data-ttu-id="55e88-137">许多 ODBC 驱动程序（包括 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT odbc 驱动程序）提供特定于驱动程序的 odbc 扩展。</span><span class="sxs-lookup"><span data-stu-id="55e88-137">Many ODBC drivers, including the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver, offer driver-specific ODBC extensions.</span></span> <span data-ttu-id="55e88-138">若要利用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 特定于 Native CLIENT ODBC 驱动程序的扩展插件，应用程序应包含 sqlncli.msi 头文件。</span><span class="sxs-lookup"><span data-stu-id="55e88-138">To take advantage of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver-specific extensions, an application should include the sqlncli.h header file.</span></span> <span data-ttu-id="55e88-139">此头文件包含：</span><span class="sxs-lookup"><span data-stu-id="55e88-139">This header file contains:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="55e88-140">Native Client ODBC 驱动程序特定的连接属性。</span><span class="sxs-lookup"><span data-stu-id="55e88-140">Native Client ODBC driver-specific connection attributes.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="55e88-141">Native Client ODBC 驱动程序特定的语句属性。</span><span class="sxs-lookup"><span data-stu-id="55e88-141">Native Client ODBC driver-specific statement attributes.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="55e88-142">Native Client ODBC 驱动程序特定的列属性。</span><span class="sxs-lookup"><span data-stu-id="55e88-142">Native Client ODBC driver-specific column attributes.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="55e88-143">特定的数据类型。</span><span class="sxs-lookup"><span data-stu-id="55e88-143">-specific data types.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="55e88-144">特定的用户定义数据类型。</span><span class="sxs-lookup"><span data-stu-id="55e88-144">-specific user-defined data types.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="55e88-145">Native Client ODBC 驱动程序特定的[SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md)类型。</span><span class="sxs-lookup"><span data-stu-id="55e88-145">Native Client ODBC driver-specific [SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md) types.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="55e88-146">Native Client ODBC 驱动程序诊断字段。</span><span class="sxs-lookup"><span data-stu-id="55e88-146">Native Client ODBC driver diagnostics fields.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="55e88-147">特定的诊断动态函数代码。</span><span class="sxs-lookup"><span data-stu-id="55e88-147">-specific diagnostic dynamic function codes.</span></span>  
  
-   <span data-ttu-id="55e88-148">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 特定的本机 C 数据类型的 C/C++ 类型定义（当列绑定到 C 数据类型 SQL_C_BINARY 时返回）。</span><span class="sxs-lookup"><span data-stu-id="55e88-148">C/C++ type definitions for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-specific native C data types (returned when columns bound to C data type SQL_C_BINARY).</span></span>  
  
-   <span data-ttu-id="55e88-149">SQLPERF 数据结构的类型定义。</span><span class="sxs-lookup"><span data-stu-id="55e88-149">Type definition for the SQLPERF data structure.</span></span>  
  
-   <span data-ttu-id="55e88-150">大容量复制宏和原型，用于支持通过 ODBC 连接使用大容量复制 API。</span><span class="sxs-lookup"><span data-stu-id="55e88-150">Bulk copy macros and prototypes to support bulk copy API usage through an ODBC connection.</span></span>  
  
-   <span data-ttu-id="55e88-151">调用分布式查询元数据 API 函数，以获取链接服务器及其目录的列表。</span><span class="sxs-lookup"><span data-stu-id="55e88-151">Call the distributed query metadata API functions for lists of linked servers and their catalogs.</span></span>  
  
 <span data-ttu-id="55e88-152">使用 Native Client ODBC 驱动程序的大容量复制功能的任何 C 或 c + + ODBC 应用程序 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 必须与 sqlncli11 文件链接。</span><span class="sxs-lookup"><span data-stu-id="55e88-152">Any C or C++ ODBC application that uses the bulk copy feature of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver must be linked with the sqlncli11.lib file.</span></span> <span data-ttu-id="55e88-153">调用分布式查询元数据 API 函数的应用程序也必须与 sqlncli11.lib 文件链接。</span><span class="sxs-lookup"><span data-stu-id="55e88-153">Applications calling the distributed query metadata API functions must also be linked with sqlncli11.lib.</span></span> <span data-ttu-id="55e88-154">Sqlncli.msi 和 sqlncli11 文件作为开发人员工具的一部分进行分发 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="55e88-154">The sqlncli.h and sqlncli11.lib files are distributed as part of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] developer's tools.</span></span> <span data-ttu-id="55e88-155">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Include 和 Lib 目录应在编译器的 INCLUDE 和 LIB 路径中，具体如下所示：</span><span class="sxs-lookup"><span data-stu-id="55e88-155">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Include and Lib directories should be in the compiler's INCLUDE and LIB paths as in the following:</span></span>  
  
```  
LIB=c:\Program Files\Microsoft Data Access SDK 2.8\Libs\x86\lib;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Lib;  
INCLUDE=c:\Program Files\Microsoft Data Access SDK 2.8\inc;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Include;  
```  
  
 <span data-ttu-id="55e88-156">在生成应用程序过程的早期所做的一个设计决策是应用程序是否需要同时进行多个 ODBC 调用。</span><span class="sxs-lookup"><span data-stu-id="55e88-156">One design decision made early in the process of building an application is whether the application needs to have multiple ODBC calls outstanding at the same time.</span></span> <span data-ttu-id="55e88-157">有两种方法可支持多个并发 ODBC 调用，将在本节的其余主题中介绍。</span><span class="sxs-lookup"><span data-stu-id="55e88-157">There are two methods for supporting multiple concurrent ODBC calls, which are described in the remaining topics in this section.</span></span> <span data-ttu-id="55e88-158">有关详细信息，请参阅[ODBC 程序员参考](https://go.microsoft.com/fwlink/?LinkId=45250)。</span><span class="sxs-lookup"><span data-stu-id="55e88-158">For more information, see the [ODBC Programmer's Reference](https://go.microsoft.com/fwlink/?LinkId=45250).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="55e88-159">本节内容</span><span class="sxs-lookup"><span data-stu-id="55e88-159">In This Section</span></span>  
  
-   [<span data-ttu-id="55e88-160">异步模式和 SQLCancel</span><span class="sxs-lookup"><span data-stu-id="55e88-160">Asynchronous Mode and SQLCancel</span></span>](../../native-client-odbc-api/sqlcancel.md)  
  
-   [<span data-ttu-id="55e88-161">多线程应用程序</span><span class="sxs-lookup"><span data-stu-id="55e88-161">Multithreaded Applications</span></span>](creating-a-driver-application-multithreaded-applications.md)  
  
## <a name="see-also"></a><span data-ttu-id="55e88-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="55e88-162">See Also</span></span>  
 [<span data-ttu-id="55e88-163">SQL Server Native Client (ODBC)</span><span class="sxs-lookup"><span data-stu-id="55e88-163">SQL Server Native Client &#40;ODBC&#41;</span></span>](sql-server-native-client-odbc.md)  
  
  
