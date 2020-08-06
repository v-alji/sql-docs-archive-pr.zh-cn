---
title: 分配连接句柄 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, passwords
- ODBC applications, connections
- handles [SQL Server Native Client]
- expiration [SQL Server Native Client]
- passwords [SQL Server], modifying
- SQL Server Native Client ODBC driver, connection handles
- connection handles [SQL Server Native Client]
- modifying passwords
- SQLAllocHandle function
ms.assetid: 471d8a31-199c-4f92-bb10-004fc7733b35
author: rothja
ms.author: jroth
ms.openlocfilehash: d3cf84e541f114d527d9a00cd19bce705a09af30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693855"
---
# <a name="allocating-a-connection-handle"></a><span data-ttu-id="4be44-102">分配连接句柄</span><span class="sxs-lookup"><span data-stu-id="4be44-102">Allocating a Connection Handle</span></span>
  <span data-ttu-id="4be44-103">应用程序可以连接到数据源或驱动程序之前，必须分配连接句柄。</span><span class="sxs-lookup"><span data-stu-id="4be44-103">Before the application can connect to a data source or driver, it must allocate a connection handle.</span></span> <span data-ttu-id="4be44-104">这是通过调用**SQLAllocHandle**并将*HandleType*参数设置为 SQL_HANDLE_DBC，并将*将 inputhandle*指向已初始化的环境句柄来完成的。</span><span class="sxs-lookup"><span data-stu-id="4be44-104">This is done by calling **SQLAllocHandle** with the *HandleType* parameter set to SQL_HANDLE_DBC and *InputHandle* pointing to an initialized environment handle.</span></span>  
  
 <span data-ttu-id="4be44-105">连接的特征通过设置连接属性控制。</span><span class="sxs-lookup"><span data-stu-id="4be44-105">The characteristics of the connection are controlled by setting connection attributes.</span></span> <span data-ttu-id="4be44-106">例如，因为事务发生在连接级别，所以事务隔离级别就是一个连接属性。</span><span class="sxs-lookup"><span data-stu-id="4be44-106">For example, because transactions occur at the connection level, the transaction isolation level is a connection attribute.</span></span> <span data-ttu-id="4be44-107">与此类似，登录超时或超时前尝试连接的等待秒数，也是连接属性。</span><span class="sxs-lookup"><span data-stu-id="4be44-107">Similarly, the login time-out, or number of seconds to wait while trying to connect before timing out, is a connection attribute.</span></span>  
  
 <span data-ttu-id="4be44-108">连接属性是通过[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)设置的，其当前设置是通过[SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md)检索的。</span><span class="sxs-lookup"><span data-stu-id="4be44-108">Connection attributes are set with [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md), and their current settings are retrieved with [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md).</span></span> <span data-ttu-id="4be44-109">如果在尝试连接之前调用**SQLSetConnectAttr** ，ODBC 驱动程序管理器会将属性存储在其连接结构中，并在该驱动程序中将它们设置为连接过程的一部分。</span><span class="sxs-lookup"><span data-stu-id="4be44-109">If **SQLSetConnectAttr** is called before a connection is attempted, the ODBC Driver Manager stores the attributes in its connection structure and sets them in the driver as part of the connection process.</span></span> <span data-ttu-id="4be44-110">有些连接属性必须在应用程序尝试连接前设置，另一些则可以在连接完成之后设置。</span><span class="sxs-lookup"><span data-stu-id="4be44-110">Some connection attributes must be set before the application attempts to connect; others can be set after the connection has completed.</span></span> <span data-ttu-id="4be44-111">例如，SQL_ATTR_ODBC_CURSORS 必须在连接前设置，但 SQL_ATTR_AUTOCOMMIT 可以在连接后设置。</span><span class="sxs-lookup"><span data-stu-id="4be44-111">For example, SQL_ATTR_ODBC_CURSORS must be set before a connection is made, but SQL_ATTR_AUTOCOMMIT can be set after connecting.</span></span>  
  
 <span data-ttu-id="4be44-112">针对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 或更高版本运行的应用程序，可以通过重置表格格式数据流 (TDS) 网络数据包大小，改善它们的性能。</span><span class="sxs-lookup"><span data-stu-id="4be44-112">Applications running against [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 or later can sometimes improve their performance by resetting the tabular data stream (TDS) network packet size.</span></span> <span data-ttu-id="4be44-113">服务器上设置的默认数据包大小为 4 KB。</span><span class="sxs-lookup"><span data-stu-id="4be44-113">The default packet size is set at the server, at 4 KB.</span></span> <span data-ttu-id="4be44-114">一般来说，数据包大小介于 4 KB 到 8 KB 之间时表现出的性能最佳。</span><span class="sxs-lookup"><span data-stu-id="4be44-114">A packet size of 4 KB to 8 KB generally gives the best performance.</span></span> <span data-ttu-id="4be44-115">如果测试表明采用另一数据包大小时，应用程序的性能表现更佳，则可以重置数据包大小。</span><span class="sxs-lookup"><span data-stu-id="4be44-115">If testing shows that it performs better with a different packet size, the application can reset the packet size.</span></span> <span data-ttu-id="4be44-116">ODBC 应用程序可以通过使用 SQL_ATTR_PACKET_SIZE 选项调用**SQLSetConnectAttr**来进行连接。</span><span class="sxs-lookup"><span data-stu-id="4be44-116">ODBC applications can do this before connecting by calling **SQLSetConnectAttr** with the SQL_ATTR_PACKET_SIZE option.</span></span> <span data-ttu-id="4be44-117">有些应用程序在使用较大的数据包时表现更佳，但数据包大小大于 8 KB 时，性能鲜有提高。</span><span class="sxs-lookup"><span data-stu-id="4be44-117">Some applications perform better with a larger packet size, but performance improvements are generally minimal for packet sizes larger than 8 KB.</span></span>  
  
 <span data-ttu-id="4be44-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序具有许多扩展连接属性，应用程序可以使用这些属性来增加其功能。</span><span class="sxs-lookup"><span data-stu-id="4be44-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver has a number of extended connection attributes that an application can use to increase its functionality.</span></span> <span data-ttu-id="4be44-119">在这些属性当中，有些控制可以在数据源中指定的相同选项，并覆盖数据源中设置的任何选项。</span><span class="sxs-lookup"><span data-stu-id="4be44-119">Some of these attributes control the same options that can be specified in data sources and used to override whatever option is set in a data source.</span></span> <span data-ttu-id="4be44-120">例如，如果应用程序使用带引号的标识符，它可以将特定于驱动程序的属性 SQL_COPT_SS_QUOTED_IDENT 设置为 SQL_QI_ON，确保无论数据源中如何设置，该选项始终这样设置。</span><span class="sxs-lookup"><span data-stu-id="4be44-120">For example, if an application uses quoted identifiers, it can set the driver-specific attribute SQL_COPT_SS_QUOTED_IDENT to SQL_QI_ON to ensure this option is always set regardless of the setting in any data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4be44-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4be44-121">See Also</span></span>  
 [<span data-ttu-id="4be44-122">与 SQL Server &#40;ODBC&#41;通信</span><span class="sxs-lookup"><span data-stu-id="4be44-122">Communicating with SQL Server &#40;ODBC&#41;</span></span>](communicating-with-sql-server-odbc.md)  
  
  
