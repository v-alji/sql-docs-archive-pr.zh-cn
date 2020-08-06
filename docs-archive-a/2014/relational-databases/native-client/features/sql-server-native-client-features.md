---
title: SQL Server Native Client 功能 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- SQLNCLI, about SQL Server Native Client
- data access [SQL Server Native Client], features
ms.assetid: 7bb32865-5afb-41ab-98b4-3fa545ee8953
author: rothja
ms.author: jroth
ms.openlocfilehash: bb4ba07f84848f754519f8f4fa1c3e56485e85a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579558"
---
# <a name="sql-server-native-client-features"></a><span data-ttu-id="c1622-102">SQL Server Native Client 功能</span><span class="sxs-lookup"><span data-stu-id="c1622-102">SQL Server Native Client Features</span></span>
  <span data-ttu-id="c1622-103">除公开 Windows（以前为 Microsoft）数据访问组件 (WDAC) 的功能以外，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 还实现诸多其他功能以公开 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="c1622-103">In addition to exposing features of the Windows (formerly Microsoft) Data Access Components (WDAC), [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client also implements many other features to expose [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1622-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="c1622-104">In This Section</span></span>  
 [<span data-ttu-id="c1622-105">处理字符转换时 ODBC 驱动程序行为的变化</span><span class="sxs-lookup"><span data-stu-id="c1622-105">ODBC Driver Behavior Change When Handling Character Conversions</span></span>](odbc-driver-behavior-change-when-handling-character-conversions.md)  
 <span data-ttu-id="c1622-106">介绍从 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client 开始的行为变化。</span><span class="sxs-lookup"><span data-stu-id="c1622-106">Discusses a change of behavior beginning in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client.</span></span>  
  
 [<span data-ttu-id="c1622-107">使用数据库镜像</span><span class="sxs-lookup"><span data-stu-id="c1622-107">Using Database Mirroring</span></span>](using-database-mirroring.md)  
 <span data-ttu-id="c1622-108">讨论 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 如何支持使用镜像数据库，这是在备用服务器上保留数据库的副本或镜像功能 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c1622-108">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports the use of mirrored databases, which is the ability to keep a copy, or mirror, of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database on a standby server.</span></span>  
  
 [<span data-ttu-id="c1622-109">执行异步操作</span><span class="sxs-lookup"><span data-stu-id="c1622-109">Performing Asynchronous Operations</span></span>](performing-asynchronous-operations.md)  
 <span data-ttu-id="c1622-110">讨论 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 如何支持异步操作，即在不阻塞调用线程的情况下立即返回的功能。</span><span class="sxs-lookup"><span data-stu-id="c1622-110">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports asynchronous operations, which is the ability to return immediately without blocking on the calling thread.</span></span>  
  
 [<span data-ttu-id="c1622-111">使用多个活动的结果集 (MARS)</span><span class="sxs-lookup"><span data-stu-id="c1622-111">Using Multiple Active Result Sets &#40;MARS&#41;</span></span>](using-multiple-active-result-sets-mars.md)  
 <span data-ttu-id="c1622-112">讨论 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 如何支持多个活动结果集 (MARS)。</span><span class="sxs-lookup"><span data-stu-id="c1622-112">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports multiple active result sets (MARS).</span></span> <span data-ttu-id="c1622-113">MARS 支持使用单一数据库连接执行和接收多个结果集。</span><span class="sxs-lookup"><span data-stu-id="c1622-113">MARS enables you to execute and receive multiple result sets using a single database connection</span></span>  
  
 [<span data-ttu-id="c1622-114">使用 XML 数据类型</span><span class="sxs-lookup"><span data-stu-id="c1622-114">Using XML Data Types</span></span>](using-xml-data-types.md)  
 <span data-ttu-id="c1622-115">讨论 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 如何支持 XML 数据类型，此基于 XML 的数据类型可用作列类型、变量类型、参数类型或函数返回类型。</span><span class="sxs-lookup"><span data-stu-id="c1622-115">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports the XML data type, which is a XML-based data type that can be used as a column type, variable type, parameter type, or function return type.</span></span>  
  
 [<span data-ttu-id="c1622-116">使用用户定义类型</span><span class="sxs-lookup"><span data-stu-id="c1622-116">Using User-Defined Types</span></span>](using-user-defined-types.md)  
 <span data-ttu-id="c1622-117">讨论 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 如何支持 (UDT) 的用户定义类型，它通过允许您在数据库中存储对象和自定义数据结构，从而扩展了 SQL 类型系统 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c1622-117">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports User-Defined Types (UDT), which extends the SQL type system by allowing you to store objects and custom data structures in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>  
  
 [<span data-ttu-id="c1622-118">使用大值类型</span><span class="sxs-lookup"><span data-stu-id="c1622-118">Using Large Value Types</span></span>](using-large-value-types.md)  
 <span data-ttu-id="c1622-119">讨论 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 如何支持大值数据类型，该类型是大型对象数据类型 (LOB)。</span><span class="sxs-lookup"><span data-stu-id="c1622-119">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports large value data types, which are large object data types (LOB).</span></span>  
  
 [<span data-ttu-id="c1622-120">以编程方式更改密码</span><span class="sxs-lookup"><span data-stu-id="c1622-120">Changing Passwords Programmatically</span></span>](changing-passwords-programmatically.md)  
 <span data-ttu-id="c1622-121">讨论 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 如何支持处理过期密码，现在可以在不需要管理员介入的情况下在客户端更改密码。</span><span class="sxs-lookup"><span data-stu-id="c1622-121">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports the handling of expired passwords so that passwords can now be changed on the client without administrator involvement.</span></span>  
  
 [<span data-ttu-id="c1622-122">使用快照隔离</span><span class="sxs-lookup"><span data-stu-id="c1622-122">Working with Snapshot Isolation</span></span>](working-with-snapshot-isolation.md)  
 <span data-ttu-id="c1622-123">讨论 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 如何支持对行版本控制的增强功能，该功能通过避免读取器-编写器阻塞情况来提高数据库性能。</span><span class="sxs-lookup"><span data-stu-id="c1622-123">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports the enhancement to row versioning that improves database performance by avoiding reader-writer blocking scenarios.</span></span>  
  
 [<span data-ttu-id="c1622-124">使用查询通知</span><span class="sxs-lookup"><span data-stu-id="c1622-124">Working with Query Notifications</span></span>](working-with-query-notifications.md)  
 <span data-ttu-id="c1622-125">讨论 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 如何支持基于行集修改的使用者通知。</span><span class="sxs-lookup"><span data-stu-id="c1622-125">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports consumer notification on rowset modification.</span></span>  
  
 [<span data-ttu-id="c1622-126">执行大容量复制操作</span><span class="sxs-lookup"><span data-stu-id="c1622-126">Performing Bulk Copy Operations</span></span>](performing-bulk-copy-operations.md)  
 <span data-ttu-id="c1622-127">讨论 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 如何支持大容量复制操作，这些操作允许将大量数据传入或传出 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 表或视图。</span><span class="sxs-lookup"><span data-stu-id="c1622-127">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports bulk copy operations that allow the transfer of large amounts of data into or out of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table or view.</span></span>  
  
 [<span data-ttu-id="c1622-128">使用不带验证的加密</span><span class="sxs-lookup"><span data-stu-id="c1622-128">Using Encryption Without Validation</span></span>](using-encryption-without-validation.md)  
 <span data-ttu-id="c1622-129">讨论如何使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 对发送到服务器的数据加密，而无需验证证书。</span><span class="sxs-lookup"><span data-stu-id="c1622-129">Discusses how to use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client to encrypt data sent to the server without validating the certificate.</span></span>  
  
 [<span data-ttu-id="c1622-130">表值参数 &#40;SQL Server Native Client&#41;</span><span class="sxs-lookup"><span data-stu-id="c1622-130">Table-Valued Parameters &#40;SQL Server Native Client&#41;</span></span>](table-valued-parameters-sql-server-native-client.md)  
 <span data-ttu-id="c1622-131">讨论 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 对表值参数的支持。</span><span class="sxs-lookup"><span data-stu-id="c1622-131">Discusses [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client support for the table-valued parameters.</span></span>  
  
 [<span data-ttu-id="c1622-132">大型 CLR 用户定义类型</span><span class="sxs-lookup"><span data-stu-id="c1622-132">Large CLR User-Defined Types</span></span>](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
 <span data-ttu-id="c1622-133">讨论对大型公共语言运行时 (CLR) 用户定义类型 (UDT) 的支持。</span><span class="sxs-lookup"><span data-stu-id="c1622-133">Discusses support for large common language runtime (CLR) user-defined types (UDTs).</span></span>  
  
 [<span data-ttu-id="c1622-134">FILESTREAM 支持</span><span class="sxs-lookup"><span data-stu-id="c1622-134">FILESTREAM Support</span></span>](filestream-support.md)  
 <span data-ttu-id="c1622-135">讨论 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 对增强型 FILESTREAM 功能的支持。</span><span class="sxs-lookup"><span data-stu-id="c1622-135">Discusses [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client support for the enhanced FILESTREAM feature.</span></span>  
  
 [<span data-ttu-id="c1622-136">客户端连接中的服务主体名称 (SPN) 支持</span><span class="sxs-lookup"><span data-stu-id="c1622-136">Service Principal Name &#40;SPN&#41; Support in Client Connections</span></span>](service-principal-name-spn-support-in-client-connections.md)  
 <span data-ttu-id="c1622-137">讨论如何扩展对服务主体名称 (SPN) 的支持，以便能够跨所有协议进行相互身份验证。</span><span class="sxs-lookup"><span data-stu-id="c1622-137">Discusses how support for service principal names (SPNs) has been extended to enable mutual authentication across all protocols.</span></span>  
  
 [<span data-ttu-id="c1622-138">SQL Server Native Client 中的稀疏列支持</span><span class="sxs-lookup"><span data-stu-id="c1622-138">Sparse Columns Support in SQL Server Native Client</span></span>](sparse-columns-support-in-sql-server-native-client.md)  
 <span data-ttu-id="c1622-139">讨论 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 对稀疏列的支持。</span><span class="sxs-lookup"><span data-stu-id="c1622-139">Discusses [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client support for sparse columns.</span></span>  
  
 [<span data-ttu-id="c1622-140">日期和时间改进</span><span class="sxs-lookup"><span data-stu-id="c1622-140">Date and Time Improvements</span></span>](date-and-time-improvements.md)  
 <span data-ttu-id="c1622-141">讨论 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 中添加的对日期和时间数据类型的支持。</span><span class="sxs-lookup"><span data-stu-id="c1622-141">Discusses support added to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client for the date and time data types.</span></span>  
  
 [<span data-ttu-id="c1622-142">元数据发现</span><span class="sxs-lookup"><span data-stu-id="c1622-142">Metadata Discovery</span></span>](metadata-discovery.md)  
 <span data-ttu-id="c1622-143">讨论对 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中的元数据发现功能进行的改进。</span><span class="sxs-lookup"><span data-stu-id="c1622-143">Discusses metadata discovery improvements that were made in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span>  
  
 [<span data-ttu-id="c1622-144">SQL Server Native Client 11.0 中的 UTF-16 支持</span><span class="sxs-lookup"><span data-stu-id="c1622-144">UTF-16 Support in SQL Server Native Client 11.0</span></span>](utf-16-support-in-sql-server-native-client-11-0.md)  
 <span data-ttu-id="c1622-145">讨论 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中引入的行为更改。</span><span class="sxs-lookup"><span data-stu-id="c1622-145">Discusses a behavior change introduced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span> <span data-ttu-id="c1622-146">如果出现以下情况，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 将不会向缓冲区添加高代理项码位：在绑定列结果或输出参数时提供了一个固定长度缓冲区；写入到缓冲区中终止符之前的 `wchar` 字符是代理项对的高代理项码位；并且下一个 `wchar` 字符是一个低代理项码位。</span><span class="sxs-lookup"><span data-stu-id="c1622-146">If you supply a fixed-length buffer when binding a column result or output parameter and if the `wchar` character written into the buffer before the terminating character is a high surrogate code point of a surrogate pair, and if the next `wchar` character is a low surrogate code point, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client will not add the high surrogate code point to the buffer.</span></span>  
  
 [<span data-ttu-id="c1622-147">对高可用性、灾难恢复的 SQL Server Native Client 支持</span><span class="sxs-lookup"><span data-stu-id="c1622-147">SQL Server Native Client Support for High Availability, Disaster Recovery</span></span>](sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
 <span data-ttu-id="c1622-148">讨论如何配置应用程序以利用 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中添加的高可用性和灾难恢复功能。</span><span class="sxs-lookup"><span data-stu-id="c1622-148">Discusses how your application can be configured to take advantage of the high-availability, disaster recovery features added in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span>  
  
 [<span data-ttu-id="c1622-149">访问扩展事件日志中的诊断信息</span><span class="sxs-lookup"><span data-stu-id="c1622-149">Accessing Diagnostic Information in the Extended Events Log</span></span>](accessing-diagnostic-information-in-the-extended-events-log.md)  
 <span data-ttu-id="c1622-150">讨论对于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 和跟踪数据的增强功能，它们使您可以访问环形缓冲区和 XEvents 日志中的诊断信息。</span><span class="sxs-lookup"><span data-stu-id="c1622-150">Discusses enhancements to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client and data tracing that gives you access to diagnostic information in the ring buffer and XEvents log.</span></span>  
  
 [<span data-ttu-id="c1622-151">SQL Server Native Client 对 LocalDB 的支持</span><span class="sxs-lookup"><span data-stu-id="c1622-151">SQL Server Native Client Support for LocalDB</span></span>](sql-server-native-client-support-for-localdb.md)  
 <span data-ttu-id="c1622-152">讨论 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 对 LocalDB 功能的支持。</span><span class="sxs-lookup"><span data-stu-id="c1622-152">Discusses [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client support for the LocalDB feature.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1622-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c1622-153">See Also</span></span>  
 <span data-ttu-id="c1622-154">[SQL Server Native Client 编程](../sql-server-native-client-programming.md) </span><span class="sxs-lookup"><span data-stu-id="c1622-154">[SQL Server Native Client Programming](../sql-server-native-client-programming.md) </span></span>  
 <span data-ttu-id="c1622-155">[ODBC 操作指南主题](../../native-client-odbc-how-to/odbc-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="c1622-155">[ODBC How-to Topics](../../native-client-odbc-how-to/odbc-how-to-topics.md) </span></span>  
 <span data-ttu-id="c1622-156">[OLE DB 操作指南主题](../../native-client-ole-db-how-to/ole-db-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="c1622-156">[OLE DB How-to Topics](../../native-client-ole-db-how-to/ole-db-how-to-topics.md) </span></span>  
 [<span data-ttu-id="c1622-157">安装 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="c1622-157">Installing SQL Server Native Client</span></span>](../applications/installing-sql-server-native-client.md)  
  
  
