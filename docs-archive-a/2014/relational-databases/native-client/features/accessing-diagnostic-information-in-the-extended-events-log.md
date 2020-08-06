---
title: 访问扩展事件日志中的诊断信息 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: aaa180c2-5e1a-4534-a125-507c647186ab
author: rothja
ms.author: jroth
ms.openlocfilehash: 5148683d464f06e8a4f52cc924baaacac9102b12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688880"
---
# <a name="accessing-diagnostic-information-in-the-extended-events-log"></a><span data-ttu-id="7a62b-102">访问扩展事件日志中的诊断信息</span><span class="sxs-lookup"><span data-stu-id="7a62b-102">Accessing Diagnostic Information in the Extended Events Log</span></span>
  <span data-ttu-id="7a62b-103">从开始 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 和 data access 跟踪 ([数据访问跟踪](https://go.microsoft.com/fwlink/?LinkId=125805)) 已更新，以便更轻松地从连接环形缓冲区和扩展事件日志中的应用程序性能信息获取有关连接失败的诊断信息。</span><span class="sxs-lookup"><span data-stu-id="7a62b-103">Beginning in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client and data access tracing ([Data Access Tracing](https://go.microsoft.com/fwlink/?LinkId=125805)) have been updated to make it easier to get diagnostic information about connection failures from the connectivity ring buffer and application performance information from the extended events log.</span></span>  
  
 <span data-ttu-id="7a62b-104">有关读取扩展事件日志的信息，请参阅[查看事件会话数据](../../../database-engine/view-event-session-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7a62b-104">For information about reading the extended events log, see [View Event Session Data](../../../database-engine/view-event-session-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a62b-105">该功能只用于故障排除和诊断目的，可能不适合审核或安全目的。</span><span class="sxs-lookup"><span data-stu-id="7a62b-105">This feature is intended only for troubleshooting and diagnostic purposes and may not be suitable for auditing or security purposes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a62b-106">备注</span><span class="sxs-lookup"><span data-stu-id="7a62b-106">Remarks</span></span>  
 <span data-ttu-id="7a62b-107">对于连接操作，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 将发送客户端连接 ID。</span><span class="sxs-lookup"><span data-stu-id="7a62b-107">For connection operations, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client will send a client connection ID.</span></span> <span data-ttu-id="7a62b-108">如果连接失败，您可以[使用连接环形) 缓冲区访问 SQL Server 2008 中](https://go.microsoft.com/fwlink/?LinkId=207752)的连接环形缓冲区 (连接性故障排除，并查找 `ClientConnectionID` 字段并获取有关连接失败的诊断信息。</span><span class="sxs-lookup"><span data-stu-id="7a62b-108">If the connection fails, you can access the connectivity ring buffer ([Connectivity troubleshooting in SQL Server 2008 with the Connectivity Ring Buffer](https://go.microsoft.com/fwlink/?LinkId=207752)) and find the `ClientConnectionID` field and get diagnostic information about the connection failure.</span></span> <span data-ttu-id="7a62b-109">仅当发生错误时，才在环形缓冲区中记录客户端连接 ID。</span><span class="sxs-lookup"><span data-stu-id="7a62b-109">Client connection IDs are logged in the ring buffer only if an error occurs.</span></span> <span data-ttu-id="7a62b-110">（如果在发送预登录数据包前连接失败，将不会生成客户端连接 ID。）客户端连接 ID 是 16 字节的 GUID。</span><span class="sxs-lookup"><span data-stu-id="7a62b-110">(If a connection fails before sending the prelogin packet, a client connection ID will not be generated.) The client connection ID is a 16-byte GUID.</span></span> <span data-ttu-id="7a62b-111">如果将 `client_connection_id` 操作添加到扩展事件会话中的事件，则还可以在扩展事件输出目标中找到客户端连接 ID。</span><span class="sxs-lookup"><span data-stu-id="7a62b-111">You can also find the client connection ID in the extended events output target, if the `client_connection_id` action is added to events in an extended events session.</span></span> <span data-ttu-id="7a62b-112">如果您需要进一步的诊断帮助，则可以启用数据访问跟踪并再次运行连接命令，然后观察数据访问跟踪中的 `ClientConnectionID` 字段以查看是否有失败的操作。</span><span class="sxs-lookup"><span data-stu-id="7a62b-112">You can enable data access tracing and rerun the connection command and observe the `ClientConnectionID` field in the data access trace for a failed operation, if you need further diagnostic assistance.</span></span>  
  
 <span data-ttu-id="7a62b-113">如果在 Native Client 中使用 ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 并且连接成功，则可以通过将 `SQL_COPT_SS_CLIENT_CONNECTION_ID` 属性与[SQLGetConnectAttr](../../native-client-odbc-api/sqlgetconnectattr.md)结合使用来获取客户端连接 ID。</span><span class="sxs-lookup"><span data-stu-id="7a62b-113">If you are using ODBC in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client and a connection succeeds, you can get the client connection ID by using the `SQL_COPT_SS_CLIENT_CONNECTION_ID` attribute with [SQLGetConnectAttr](../../native-client-odbc-api/sqlgetconnectattr.md).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="7a62b-114">Native Client 还发送特定于线程的活动 ID。</span><span class="sxs-lookup"><span data-stu-id="7a62b-114">Native Client also sends a thread-specific activity ID.</span></span> <span data-ttu-id="7a62b-115">如果开始会话时启用了 TRACK_CAUSAILITY 选项，则会在扩展的事件会话中捕获活动 ID。</span><span class="sxs-lookup"><span data-stu-id="7a62b-115">The activity ID is captured in the extended events sessions if the sessions are started with the TRACK_CAUSAILITY option enabled.</span></span> <span data-ttu-id="7a62b-116">对于活动连接的性能问题，您可以从客户端的数据访问跟踪（`ActivityID` 字段）中获取活动 ID，然后在扩展事件输出中找到活动 ID。</span><span class="sxs-lookup"><span data-stu-id="7a62b-116">For performance issues with an active connection, you can get the activity ID from the client's data access trace (`ActivityID` field) and then locate the activity ID in the extended events output.</span></span> <span data-ttu-id="7a62b-117">扩展事件中的活动 ID 是 16 字节 GUID（与客户端连接 ID 的 GUID 不同），且后面追加四个字节的序列号。</span><span class="sxs-lookup"><span data-stu-id="7a62b-117">The activity ID in the extended events is a 16-byte GUID (not the same as the GUID for the client connection ID) appended with a four-byte sequence number.</span></span> <span data-ttu-id="7a62b-118">该序列号表示某个请求在线程内的顺序，并指示线程的批处理和 RPC 语句的相对顺序。</span><span class="sxs-lookup"><span data-stu-id="7a62b-118">The sequence number represents the order of a request within a thread and indicates the relative ordering of batch and RPC statements for the thread.</span></span> <span data-ttu-id="7a62b-119">当启用数据访问跟踪且数据访问跟踪配置字词中的第 18 位设置为“打开”时，可以针对 SQL 批处理语句和 RPC 请求发送 `ActivityID`（可选）。</span><span class="sxs-lookup"><span data-stu-id="7a62b-119">The `ActivityID` is optionally sent for SQL batch statements and RPC requests when data access tracing is enabled on and the 18th bit in the data access tracing configuration word is turned ON.</span></span>  
  
 <span data-ttu-id="7a62b-120">以下是一个使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 启动扩展事件会话的示例，该会话将存储在环形缓冲区中，并将记录从客户端针对 RPC 和批处理操作发送的活动 ID。</span><span class="sxs-lookup"><span data-stu-id="7a62b-120">The following is a sample that uses [!INCLUDE[tsql](../../../includes/tsql-md.md)] to start an extended events session that will be stored in a ring buffer and will record the activity ID sent from a client on RPC and batch operations.</span></span>  
  
```  
create event session MySession on server   
add event connectivity_ring_buffer_recorded,   
add event sql_statement_starting (action (client_connection_id)),   
add event sql_statement_completed (action (client_connection_id)),   
add event rpc_starting (action (client_connection_id)),   
add event rpc_completed (action (client_connection_id))  
add target ring_buffer with (track_causality=on)  
  
```  
  
## <a name="control-file"></a><span data-ttu-id="7a62b-121">控制文件</span><span class="sxs-lookup"><span data-stu-id="7a62b-121">Control File</span></span>  
 <span data-ttu-id="7a62b-122">在 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中，SQL Server Native Client 控制文件 (ctrl.guid.snac11) 的内容为：</span><span class="sxs-lookup"><span data-stu-id="7a62b-122">In [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], the contents of the SQL Server Native  Client control file (ctrl.guid.snac11) is:</span></span>  
  
```  
{8B98D3F2-3CC6-0B9C-6651-9649CCE5C752}  0x00000000  0   MSDADIAG.ETW  
{2DA81B52-908E-7DB6-EF81-76856BB47C4F}  0xFFFFFFFF  0   SQLNCLI11.1  
```  
  
## <a name="mof-file"></a><span data-ttu-id="7a62b-123">MOF 文件</span><span class="sxs-lookup"><span data-stu-id="7a62b-123">MOF File</span></span>  
 <span data-ttu-id="7a62b-124">在 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中，SQL Server Native Client mof 文件的内容为：</span><span class="sxs-lookup"><span data-stu-id="7a62b-124">In [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], the contents of the SQL Server Native  Client mof file is:</span></span>  
  
```  
#pragma classflags("forceupdate")  
#pragma namespace ("\\\\.\\Root\\WMI")  
  
/////////////////////////////////////////////////////////////////////////////  
//  
//  MSDADIAG.ETW  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW"),  
 Guid("{8B98D3F2-3CC6-0B9C-6651-9649CCE5C752}"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW : EventTrace  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW"),  
 Guid("{8B98D3F3-3CC6-0B9C-6651-9649CCE5C752}"),  
 DisplayName("msdadiag"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace : Bid2Etw_MSDADIAG_ETW  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW formatted output (A)"),  
 EventType(17),  
 EventTypeName("TextA"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace_TextA : Bid2Etw_MSDADIAG_ETW_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringA"),  
     extension("RString"),  
     read  
    ]  
    object msgStr;  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW formatted output (W)"),  
 EventType(18),  
 EventTypeName("TextW"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace_TextW : Bid2Etw_MSDADIAG_ETW_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringW"),  
     extension("RWString"),  
     read  
    ]  
    object msgStr;  
};  
  
/////////////////////////////////////////////////////////////////////////////  
//  
//  SQLNCLI11.1  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1"),  
 Guid("{2DA81B52-908E-7DB6-EF81-76856BB47C4F}"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1 : EventTrace  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1"),  
 Guid("{2DA81B53-908E-7DB6-EF81-76856BB47C4F}"),  
 DisplayName("SQLNCLI11.1"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1_Trace : Bid2Etw_SQLNCLI11_1  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1 formatted output (A)"),  
 EventType(17),  
 EventTypeName("TextA"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1_Trace_TextA : Bid2Etw_SQLNCLI11_1_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringA"),  
     extension("RString"),  
     read  
    ]  
    object msgStr;  
};  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1 formatted output (W)"),  
 EventType(18),  
 EventTypeName("TextW"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1_Trace_TextW : Bid2Etw_SQLNCLI11_1_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringW"),  
     extension("RWString"),  
     read  
    ]  
    object msgStr;  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a62b-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7a62b-125">See Also</span></span>  
 [<span data-ttu-id="7a62b-126">处理错误和消息</span><span class="sxs-lookup"><span data-stu-id="7a62b-126">Handling Errors and Messages</span></span>](../../native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
