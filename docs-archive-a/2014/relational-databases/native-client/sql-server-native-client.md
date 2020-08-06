---
title: SQL Server Native Client&#39;的新增功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: e4d4fe39-0090-42a7-8405-6378370d11cb
author: rothja
ms.author: jroth
ms.openlocfilehash: f7a8fdd6716f7ba571ed8d1d8b5f959666961aa8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591318"
---
# <a name="what39s-new-in-sql-server-native-client"></a><span data-ttu-id="7d208-102">&#39;中的新增功能 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="7d208-102">What&#39;s New in SQL Server Native Client</span></span>
  [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="7d208-103">会安装 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="7d208-103">installs [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client.</span></span> <span data-ttu-id="7d208-104">没有 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="7d208-104">There is no [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="7d208-105">未来 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 中的 ODBC 驱动程序将不会再更新。</span><span class="sxs-lookup"><span data-stu-id="7d208-105">There will be no more updates to the ODBC driver in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="7d208-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 中 ODBC 驱动程序的后继版本（在 Windows 上称为 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]）将随 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 一同安装。</span><span class="sxs-lookup"><span data-stu-id="7d208-106">The successor to the ODBC driver in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, which is called the [!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on Windows, is installed with [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].</span></span> <span data-ttu-id="7d208-107">有关 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 上的 ODBC driver 11 for 的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅[Microsoft odbc driver 11 for SQL Server](https://www.microsoft.com/download/details.aspx?id=36434)。</span><span class="sxs-lookup"><span data-stu-id="7d208-107">For more information about the [!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on Windows, see [Microsoft ODBC Driver 11 for SQL Server - Windows](https://www.microsoft.com/download/details.aspx?id=36434).</span></span>  
  
 <span data-ttu-id="7d208-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 最近更新了 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client 中的 OLE DB Provider。</span><span class="sxs-lookup"><span data-stu-id="7d208-108">The OLE DB Provider in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client was last updated in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client.</span></span> <span data-ttu-id="7d208-109">想要使用 OLE DB 访问接口连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的最新版本的开发人员必须使用在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client 中随附的 OLE DB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="7d208-109">Developers who wish to use an OLE DB provider to connect to the latest version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must use the OLE DB provider that shipped in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="7d208-110">下列主题说明 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中新增的 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client 重要功能。</span><span class="sxs-lookup"><span data-stu-id="7d208-110">The following topics describe significant new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client features in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
-   [<span data-ttu-id="7d208-111">SQL Server Native Client 对 LocalDB 的支持</span><span class="sxs-lookup"><span data-stu-id="7d208-111">SQL Server Native Client Support for LocalDB</span></span>](features/sql-server-native-client-support-for-localdb.md)  
  
-   [<span data-ttu-id="7d208-112">元数据发现</span><span class="sxs-lookup"><span data-stu-id="7d208-112">Metadata Discovery</span></span>](features/metadata-discovery.md)  
  
-   [<span data-ttu-id="7d208-113">SQL Server Native Client 11.0 中的 UTF-16 支持</span><span class="sxs-lookup"><span data-stu-id="7d208-113">UTF-16 Support in SQL Server Native Client 11.0</span></span>](features/utf-16-support-in-sql-server-native-client-11-0.md)  
  
-   [<span data-ttu-id="7d208-114">对高可用性、灾难恢复的 SQL Server Native Client 支持</span><span class="sxs-lookup"><span data-stu-id="7d208-114">SQL Server Native Client Support for High Availability, Disaster Recovery</span></span>](features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
  
-   [<span data-ttu-id="7d208-115">访问扩展事件日志中的诊断信息</span><span class="sxs-lookup"><span data-stu-id="7d208-115">Accessing Diagnostic Information in the Extended Events Log</span></span>](features/accessing-diagnostic-information-in-the-extended-events-log.md)  
  
 <span data-ttu-id="7d208-116">此外，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 中的 ODBC 现在支持添加到 Windows 7 SDK 中的标准 ODBC 的三项功能：</span><span class="sxs-lookup"><span data-stu-id="7d208-116">In addition, ODBC in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client now supports three features that were added to standard ODBC in the Windows 7 SDK:</span></span>  
  
-   <span data-ttu-id="7d208-117">异步执行与连接相关的操作。</span><span class="sxs-lookup"><span data-stu-id="7d208-117">Asynchronous execution on connection-related operations.</span></span> <span data-ttu-id="7d208-118">有关详细信息，请参阅[异步执行](https://go.microsoft.com/fwlink/?LinkID=191493)。</span><span class="sxs-lookup"><span data-stu-id="7d208-118">For more information, see [Asynchronous Execution](https://go.microsoft.com/fwlink/?LinkID=191493).</span></span>  
  
-   <span data-ttu-id="7d208-119">C 数据类型扩展能力。</span><span class="sxs-lookup"><span data-stu-id="7d208-119">C Data Type Extensibility.</span></span> <span data-ttu-id="7d208-120">有关详细信息，请参阅[ODBC 中的 C 数据类型](https://go.microsoft.com/fwlink/?LinkID=191495)。</span><span class="sxs-lookup"><span data-stu-id="7d208-120">For more information, see [C Data Types in ODBC](https://go.microsoft.com/fwlink/?LinkID=191495).</span></span>  
  
     <span data-ttu-id="7d208-121">若要在 Native Client 中支持此功能 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ， `SQL_C_SS_TIME2` `time` `SQL_C_SS_TIMESTAMPOFFSET` `datetimeoffset` `SQL_C_BINARY` 如果应用程序使用 ODBC 3.8，则 SQLGetDescField 可以返回类型) 为) 或 (的 (，而不是。</span><span class="sxs-lookup"><span data-stu-id="7d208-121">To support this feature in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, SQLGetDescField can return `SQL_C_SS_TIME2` (for `time` types) or `SQL_C_SS_TIMESTAMPOFFSET` (for `datetimeoffset`) instead of `SQL_C_BINARY`, if your application uses ODBC 3.8.</span></span> <span data-ttu-id="7d208-122">有关详细信息，请参阅[对 ODBC 日期和时间改进的数据类型支持](features/date-and-time-improvements.md)。</span><span class="sxs-lookup"><span data-stu-id="7d208-122">For more information, see [Data Type Support for ODBC Date and Time Improvements](features/date-and-time-improvements.md).</span></span>  
  
-   <span data-ttu-id="7d208-123">用小缓冲区多次调用 `SQLGetData` 来检索一个大型参数值。</span><span class="sxs-lookup"><span data-stu-id="7d208-123">Calling `SQLGetData` with a small buffer multiple times to retrieve a large parameter value.</span></span> <span data-ttu-id="7d208-124">有关详细信息，请参阅[使用 SQLGetData 检索输出参数](https://go.microsoft.com/fwlink/?LinkID=191494)。</span><span class="sxs-lookup"><span data-stu-id="7d208-124">For more information, see [Retrieving Output Parameters Using SQLGetData](https://go.microsoft.com/fwlink/?LinkID=191494).</span></span>  
  
 <span data-ttu-id="7d208-125">下列主题描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client 行为更改。</span><span class="sxs-lookup"><span data-stu-id="7d208-125">The following topics describe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client behavior changes in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
-   <span data-ttu-id="7d208-126">调用时 `ICommandWithParameters::SetParameterInfo` ，传递给*pwszName*参数的值必须是有效的标识符。</span><span class="sxs-lookup"><span data-stu-id="7d208-126">When calling `ICommandWithParameters::SetParameterInfo`, the value passed to the *pwszName* parameter must be a valid identifier.</span></span> <span data-ttu-id="7d208-127">有关详细信息，请参阅[ICommandWithParameters](../native-client-ole-db-interfaces/icommandwithparameters.md)。</span><span class="sxs-lookup"><span data-stu-id="7d208-127">For more information, see [ICommandWithParameters](../native-client-ole-db-interfaces/icommandwithparameters.md).</span></span>  
  
-   <span data-ttu-id="7d208-128">`SQLDescribeParam` 现在将一致地返回符合 ODBC 规范的值。</span><span class="sxs-lookup"><span data-stu-id="7d208-128">`SQLDescribeParam` will now consistently return a value that conforms to the ODBC specification.</span></span> <span data-ttu-id="7d208-129">有关详细信息，请参阅[SQLDescribeParam](../native-client-odbc-api/sqldescribeparam.md)。</span><span class="sxs-lookup"><span data-stu-id="7d208-129">For more information, see [SQLDescribeParam](../native-client-odbc-api/sqldescribeparam.md).</span></span>  
  
-   [<span data-ttu-id="7d208-130">处理字符转换时 ODBC 驱动程序行为的变化</span><span class="sxs-lookup"><span data-stu-id="7d208-130">ODBC Driver Behavior Change When Handling Character Conversions</span></span>](features/odbc-driver-behavior-change-when-handling-character-conversions.md)  
  
## <a name="see-also"></a><span data-ttu-id="7d208-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7d208-131">See Also</span></span>  
 [<span data-ttu-id="7d208-132">SQL Server Native Client 功能</span><span class="sxs-lookup"><span data-stu-id="7d208-132">SQL Server Native Client Features</span></span>](features/sql-server-native-client-features.md)  
  
  
