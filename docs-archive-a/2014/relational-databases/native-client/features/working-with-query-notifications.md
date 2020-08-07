---
title: 使用查询通知 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], query notifications
- rowsets [SQL Server], notifications
- SQL Server Native Client, query notifications
- notifications [SQL Server Native Client]
- query notifications [SQL Server], SQL Server Native Client
- canceling rowset changes
- IRowsetNotify interface
- SQLNCLI, query notifications
- SQL Server Native Client OLE DB provider, query notifications
- consumer notification for rowset changes [SQL Server Native Client]
ms.assetid: 2f906fff-5ed9-4527-9fd3-9c0d27c3dff7
author: rothja
ms.author: jroth
ms.openlocfilehash: ba30bfc8df05a55e297ae8fcb8e2253de57e3ca6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589008"
---
# <a name="working-with-query-notifications"></a><span data-ttu-id="30c1d-102">使用查询通知</span><span class="sxs-lookup"><span data-stu-id="30c1d-102">Working with Query Notifications</span></span>
  <span data-ttu-id="30c1d-103">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 中引入了查询通知。</span><span class="sxs-lookup"><span data-stu-id="30c1d-103">Query notifications were introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="30c1d-104">查询通知建立在 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 中引入的 Service Broker 基础结构之上，并允许在数据发生更改时向应用程序发送通知。</span><span class="sxs-lookup"><span data-stu-id="30c1d-104">Built upon the Service Broker infrastructure introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], query notifications allow applications to be notified when data has changed.</span></span> <span data-ttu-id="30c1d-105">对提供数据库信息的缓存且需要在源数据发生更改时收到通知的应用程序（如 Web 应用程序）而言，以上功能特别有用。</span><span class="sxs-lookup"><span data-stu-id="30c1d-105">This feature is particularly useful for applications that provide a cache of information from a database, such as a Web application, and need to be notified when the source data is changed.</span></span>  
  
 <span data-ttu-id="30c1d-106">查询通知使您可以在查询的基础数据发生更改时请求在指定的超时期限内发送通知。</span><span class="sxs-lookup"><span data-stu-id="30c1d-106">Query notifications allow you to request notification within a specified time-out period when the underlying data of a query changes.</span></span> <span data-ttu-id="30c1d-107">通知请求指定通知选项，其中包括服务名称、消息正文和服务器的超时值。</span><span class="sxs-lookup"><span data-stu-id="30c1d-107">The request for notification specifies the notification options, which include the service name, message text, and time-out value to the server.</span></span> <span data-ttu-id="30c1d-108">通知是通过 Service Broker 队列传递的，应用程序可以轮询该队列以获取可用通知。</span><span class="sxs-lookup"><span data-stu-id="30c1d-108">Notifications are delivered through a Service Broker queue that applications may poll for available notifications.</span></span>  
  
 <span data-ttu-id="30c1d-109">查询通知选项字符串的语法为：</span><span class="sxs-lookup"><span data-stu-id="30c1d-109">The syntax of the query notifications options string is:</span></span>  
  
 `service=<service-name>[;(local database=<database> | broker instance=<broker instance>)]`  
  
 <span data-ttu-id="30c1d-110">例如：</span><span class="sxs-lookup"><span data-stu-id="30c1d-110">For example:</span></span>  
  
 `service=mySSBService;local database=mydb`  
  
 <span data-ttu-id="30c1d-111">由于应用程序可能在创建通知订阅后终止，因此，通知订阅的生存期比启动它们的进程的生存期长。</span><span class="sxs-lookup"><span data-stu-id="30c1d-111">Notification subscriptions outlive the process that initiates them, as an application may create a notification subscription and then terminate.</span></span> <span data-ttu-id="30c1d-112">订阅将保持有效，如果数据发生更改，则将在创建该订阅时指定的超时期限内发送通知。</span><span class="sxs-lookup"><span data-stu-id="30c1d-112">The subscription remains valid, and the notification will occur if the data changes within the time-out period specified when the subscription was created.</span></span> <span data-ttu-id="30c1d-113">通知是通过执行的查询、通知选项和消息正文标识的，将通知的超时值设置为零可以取消该通知。</span><span class="sxs-lookup"><span data-stu-id="30c1d-113">A notification is identified by the query executed, the notification options, and the message text, and may be cancelled by setting its time-out value to zero.</span></span>  
  
 <span data-ttu-id="30c1d-114">只发送一次通知。</span><span class="sxs-lookup"><span data-stu-id="30c1d-114">Notifications are sent only once.</span></span> <span data-ttu-id="30c1d-115">对于数据更改的持续通知，必须在处理每个通知之后重新执行查询来创建新的订阅。</span><span class="sxs-lookup"><span data-stu-id="30c1d-115">For continuous notification of data change, a new subscription must be created by re-executing the query after each notification is processed.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="30c1d-116">本机客户端应用程序通常使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] [receive](/sql/t-sql/statements/receive-transact-sql)命令接收通知，以从与通知选项中指定的服务关联的队列中读取通知。</span><span class="sxs-lookup"><span data-stu-id="30c1d-116">Native Client applications typically receive notifications by using the [!INCLUDE[tsql](../../../includes/tsql-md.md)] [RECEIVE](/sql/t-sql/statements/receive-transact-sql) command to read notifications from the queue associated with the service specified in the notification options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30c1d-117">对于需要通知的查询，必须限定其中的表名，例如 `dbo.myTable`。</span><span class="sxs-lookup"><span data-stu-id="30c1d-117">Table names must be qualified in queries for which notification is required, for example, `dbo.myTable`.</span></span> <span data-ttu-id="30c1d-118">表名必须用包含两个部分的名称进行限定。</span><span class="sxs-lookup"><span data-stu-id="30c1d-118">Table names must be qualified with two part names.</span></span> <span data-ttu-id="30c1d-119">如果使用的名称由三个或四个部分组成，则订阅无效。</span><span class="sxs-lookup"><span data-stu-id="30c1d-119">Subscription is invalid if three- or four-part names are used.</span></span>  
  
 <span data-ttu-id="30c1d-120">通知基础结构构建在 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 中引入的队列功能之上。</span><span class="sxs-lookup"><span data-stu-id="30c1d-120">The notification infrastructure is built on top of a queuing feature introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="30c1d-121">通常，在服务器上生成的通知是通过这些队列发送的，以便在稍后进行处理。</span><span class="sxs-lookup"><span data-stu-id="30c1d-121">In general, notifications generated at the server are sent through these queues to be processed later.</span></span>  
  
 <span data-ttu-id="30c1d-122">若要使用查询通知，服务器上必须存在队列和服务。</span><span class="sxs-lookup"><span data-stu-id="30c1d-122">To use query notifications a queue and a service must exist on the server.</span></span> <span data-ttu-id="30c1d-123">使用如下 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 可以创建队列和服务：</span><span class="sxs-lookup"><span data-stu-id="30c1d-123">These can be created using [!INCLUDE[tsql](../../../includes/tsql-md.md)] similar to the following:</span></span>  
  
```  
CREATE QUEUE myQueue  
CREATE SERVICE myService ON QUEUE myQueue   
  
([https://schemas.microsoft.com/SQL/Notifications/PostQueryNotification])  
```  
  
> [!NOTE]  
>  <span data-ttu-id="30c1d-124">服务必须使用预定义约定 `https://schemas.microsoft.com/SQL/Notifications/PostQueryNotification`，如上所示。</span><span class="sxs-lookup"><span data-stu-id="30c1d-124">The service must use the predefined contract `https://schemas.microsoft.com/SQL/Notifications/PostQueryNotification` as shown above.</span></span>  
  
## <a name="sql-server-native-client-ole-db-provider"></a><span data-ttu-id="30c1d-125">SQL Server Native Client OLE DB 访问接口</span><span class="sxs-lookup"><span data-stu-id="30c1d-125">SQL Server Native Client OLE DB Provider</span></span>  
 <span data-ttu-id="30c1d-126">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序支持按行集修改的使用者通知。</span><span class="sxs-lookup"><span data-stu-id="30c1d-126">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports consumer notification on rowset modification.</span></span> <span data-ttu-id="30c1d-127">使用者在行集修改的每个阶段以及在尝试执行任何更改时接收通知。</span><span class="sxs-lookup"><span data-stu-id="30c1d-127">The consumer receives notification at every phase of rowset modification and on any attempted change.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30c1d-128">使用**ICommand：： Execute**将通知查询传递给服务器，这是使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序订阅查询通知的唯一有效方式。</span><span class="sxs-lookup"><span data-stu-id="30c1d-128">Passing a notifications query to the server with **ICommand::Execute** is the only valid way to subscribe to query notifications with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span>  
  
### <a name="the-dbpropset_sqlserverrowset-property-set"></a><span data-ttu-id="30c1d-129">DBPROPSET_SQLSERVERROWSET 属性集</span><span class="sxs-lookup"><span data-stu-id="30c1d-129">The DBPROPSET_SQLSERVERROWSET Property Set</span></span>  
 <span data-ttu-id="30c1d-130">为了通过 OLE DB 支持查询通知， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 将以下新属性添加到 DBPROPSET_SQLSERVERROWSET 属性集。</span><span class="sxs-lookup"><span data-stu-id="30c1d-130">In order to support query notifications through OLE DB, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client adds the following new properties to the DBPROPSET_SQLSERVERROWSET property set.</span></span>  
  
|<span data-ttu-id="30c1d-131">名称</span><span class="sxs-lookup"><span data-stu-id="30c1d-131">Name</span></span>|<span data-ttu-id="30c1d-132">类型</span><span class="sxs-lookup"><span data-stu-id="30c1d-132">Type</span></span>|<span data-ttu-id="30c1d-133">说明</span><span class="sxs-lookup"><span data-stu-id="30c1d-133">Description</span></span>|  
|----------|----------|-----------------|  
|<span data-ttu-id="30c1d-134">SSPROP_QP_NOTIFICATION_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="30c1d-134">SSPROP_QP_NOTIFICATION_TIMEOUT</span></span>|<span data-ttu-id="30c1d-135">VT_UI4</span><span class="sxs-lookup"><span data-stu-id="30c1d-135">VT_UI4</span></span>|<span data-ttu-id="30c1d-136">查询通知保持为活动状态的秒数。</span><span class="sxs-lookup"><span data-stu-id="30c1d-136">The number of seconds that the query notification is to remain active.</span></span><br /><br /> <span data-ttu-id="30c1d-137">默认为 432000 秒（5 天）。</span><span class="sxs-lookup"><span data-stu-id="30c1d-137">The default is 432000 seconds (5 days).</span></span> <span data-ttu-id="30c1d-138">最小值为 1 秒，最大值为 2^31-1 秒。</span><span class="sxs-lookup"><span data-stu-id="30c1d-138">The minimum value is 1 second, and the maximum value is 2^31-1 seconds.</span></span>|  
|<span data-ttu-id="30c1d-139">SSPROP_QP_NOTIFICATION_MSGTEXT</span><span class="sxs-lookup"><span data-stu-id="30c1d-139">SSPROP_QP_NOTIFICATION_MSGTEXT</span></span>|<span data-ttu-id="30c1d-140">VT_BSTR</span><span class="sxs-lookup"><span data-stu-id="30c1d-140">VT_BSTR</span></span>|<span data-ttu-id="30c1d-141">通知的消息正文。</span><span class="sxs-lookup"><span data-stu-id="30c1d-141">The message text of the notification.</span></span> <span data-ttu-id="30c1d-142">消息正文是用户定义的，没有预定义格式。</span><span class="sxs-lookup"><span data-stu-id="30c1d-142">This is user defined, and has no predefined format.</span></span><br /><br /> <span data-ttu-id="30c1d-143">默认情况下，该字符串为空。</span><span class="sxs-lookup"><span data-stu-id="30c1d-143">By default, the string is empty.</span></span> <span data-ttu-id="30c1d-144">您可以使用 1 至 2000 个字符指定消息。</span><span class="sxs-lookup"><span data-stu-id="30c1d-144">You can specify a message using 1-2000 characters.</span></span>|  
|<span data-ttu-id="30c1d-145">SSPROP_QP_NOTIFICATION_OPTIONS</span><span class="sxs-lookup"><span data-stu-id="30c1d-145">SSPROP_QP_NOTIFICATION_OPTIONS</span></span>|<span data-ttu-id="30c1d-146">VT_BSTR</span><span class="sxs-lookup"><span data-stu-id="30c1d-146">VT_BSTR</span></span>|<span data-ttu-id="30c1d-147">查询通知选项。</span><span class="sxs-lookup"><span data-stu-id="30c1d-147">The query notification options.</span></span> <span data-ttu-id="30c1d-148">这些值是在*名称* = *值*为语法的字符串中指定的。</span><span class="sxs-lookup"><span data-stu-id="30c1d-148">These are specified in a string with *name*=*value* syntax.</span></span> <span data-ttu-id="30c1d-149">用户负责创建服务并从队列中读取通知。</span><span class="sxs-lookup"><span data-stu-id="30c1d-149">The user is responsible for creating the service and reading notifications off of the queue.</span></span><br /><br /> <span data-ttu-id="30c1d-150">默认值为空字符串。</span><span class="sxs-lookup"><span data-stu-id="30c1d-150">The default is an empty string.</span></span>|  
  
 <span data-ttu-id="30c1d-151">无论语句是在用户事务中运行还是以自动提交模式运行，或者无论是提交还是回滚运行语句的事务，将始终提交通知订阅。</span><span class="sxs-lookup"><span data-stu-id="30c1d-151">The notification subscription is always committed, regardless of whether the statement ran in a user transaction or in auto commit or whether the transaction in which the statement ran committed or rolled back.</span></span> <span data-ttu-id="30c1d-152">根据以下任一无效通知条件激发服务器通知：更改基础数据或架构，或者当达到超时期限时（以先发生者为准）。</span><span class="sxs-lookup"><span data-stu-id="30c1d-152">The server notification fires upon any of the following invalid notification conditions: change of underlying data or schema, or when the timeout period is reached; whichever is first.</span></span> <span data-ttu-id="30c1d-153">激发通知后将立即删除通知注册。</span><span class="sxs-lookup"><span data-stu-id="30c1d-153">Notification registrations are deleted as soon as they are fired.</span></span> <span data-ttu-id="30c1d-154">因此，在接收通知时，应用程序必须再次订阅通知，以备进一步更新之用。</span><span class="sxs-lookup"><span data-stu-id="30c1d-154">Hence upon receiving notifications, the application must subscribe again in case they want to get further updates.</span></span>  
  
 <span data-ttu-id="30c1d-155">其他连接或线程可以检查通知的目标队列。</span><span class="sxs-lookup"><span data-stu-id="30c1d-155">Another connection or thread can check the destination queue for notifications.</span></span> <span data-ttu-id="30c1d-156">例如：</span><span class="sxs-lookup"><span data-stu-id="30c1d-156">For example:</span></span>  
  
```  
WAITFOR (RECEIVE * FROM MyQueue);   // Where MyQueue is the queue name.   
```  
  
 <span data-ttu-id="30c1d-157">请注意，SELECT \* 不会删除 Queue 中的项，但 RECEIVE \* FROM 将删除相应项。</span><span class="sxs-lookup"><span data-stu-id="30c1d-157">Note that SELECT \* does not delete the entry from the Queue, however RECEIVE \* FROM does.</span></span> <span data-ttu-id="30c1d-158">如果队列为空，该语句将停止服务器线程。</span><span class="sxs-lookup"><span data-stu-id="30c1d-158">This stalls a server thread if the queue is empty.</span></span> <span data-ttu-id="30c1d-159">如果调用时存在队列项，则会立即返回这些队列项；否则调用将一直等待，直到生成队列项为止。</span><span class="sxs-lookup"><span data-stu-id="30c1d-159">If there are queue entries at the time of the call, they are returned immediately; otherwise the call waits until a queue entry is made.</span></span>  
  
```  
RECEIVE * FROM MyQueue  
```  
  
 <span data-ttu-id="30c1d-160">如果队列为空，该语句将立即返回空的结果集；否则会返回所有队列通知。</span><span class="sxs-lookup"><span data-stu-id="30c1d-160">This statement immediately returns an empty result set if the queue is empty; otherwise it returns all queue notifications.</span></span>  
  
 <span data-ttu-id="30c1d-161">如果 SSPROP_QP_NOTIFICATION_MSGTEXT 和 SSPROP_QP_NOTIFICATION_OPTIONS 为非 NULL 和非空，当执行其中的每个命令时，将向服务器发送包含上面定义的三个属性的查询通知 TDS 头。</span><span class="sxs-lookup"><span data-stu-id="30c1d-161">If SSPROP_QP_NOTIFICATION_MSGTEXT and SSPROP_QP_NOTIFICATION_OPTIONS are non-NULL and non-empty, the query notifications TDS header containing the three properties defined above are sent to the server with each execution of the command.</span></span> <span data-ttu-id="30c1d-162">如果其中任一属性为 Null（或空），则不会发送头，并引发 DB_E_ERRORSOCCURRED（或者如果两个属性均标记为可选，则引发 DB_S_ERRORSOCCURRED），同时将状态值设置为 DBPROPSTATUS_BADVALUE。</span><span class="sxs-lookup"><span data-stu-id="30c1d-162">If either of them is null (or empty), the header is not sent and DB_E_ERRORSOCCURRED is raised, (or DB_S_ERRORSOCCURRED if the properties are both marked as optional), and the status value is set to DBPROPSTATUS_BADVALUE.</span></span> <span data-ttu-id="30c1d-163">在执行/准备期间进行验证。</span><span class="sxs-lookup"><span data-stu-id="30c1d-163">The validation occurs on Execute/Prepare.</span></span> <span data-ttu-id="30c1d-164">类似地，当设置查询通知属性以便连接到 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 之前的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本时，将引发 DB_S_ERRORSOCCURED。</span><span class="sxs-lookup"><span data-stu-id="30c1d-164">Similarly, DB_S_ERRORSOCCURED is raised when the query notification properties are set for connections to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] versions before [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="30c1d-165">在这种情况下，状态值为 DBPROPSTATUS_NOTSUPPORTED。</span><span class="sxs-lookup"><span data-stu-id="30c1d-165">The status value in this case is DBPROPSTATUS_NOTSUPPORTED.</span></span>  
  
 <span data-ttu-id="30c1d-166">启动订阅不能保证将成功传递后续消息。</span><span class="sxs-lookup"><span data-stu-id="30c1d-166">Initiating a subscription does not guarantee that subsequent messages will be successfully delivered.</span></span> <span data-ttu-id="30c1d-167">此外，不会检查指定服务名称的有效性。</span><span class="sxs-lookup"><span data-stu-id="30c1d-167">In addition, no check is made as to the validity of the service name specified.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30c1d-168">准备语句永远不会启动订阅；只有执行语句才能实现此目的，并且 OLE DB 核心服务的使用不会影响查询通知。</span><span class="sxs-lookup"><span data-stu-id="30c1d-168">Preparing statements will never cause the subscription to be initiated; only statement execution will achieve this and query notifications are not impacted by the use of OLE DB core services.</span></span>  
  
 <span data-ttu-id="30c1d-169">有关 DBPROPSET_SQLSERVERROWSET 属性集的详细信息，请参阅[行集属性和行为](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)。</span><span class="sxs-lookup"><span data-stu-id="30c1d-169">For more information about the DBPROPSET_SQLSERVERROWSET property set, see [Rowset Properties and Behaviors](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md).</span></span>  
  
## <a name="sql-server-native-client-odbc-driver"></a><span data-ttu-id="30c1d-170">SQL Server Native Client ODBC 驱动程序</span><span class="sxs-lookup"><span data-stu-id="30c1d-170">SQL Server Native Client ODBC Driver</span></span>  
 <span data-ttu-id="30c1d-171">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序通过向[SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md)和[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)函数添加三个新属性，支持查询通知：</span><span class="sxs-lookup"><span data-stu-id="30c1d-171">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports query notifications through the addition of three new attributes to the [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) and [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) functions:</span></span>  
  
-   <span data-ttu-id="30c1d-172">SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT</span><span class="sxs-lookup"><span data-stu-id="30c1d-172">SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT</span></span>  
  
-   <span data-ttu-id="30c1d-173">SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS</span><span class="sxs-lookup"><span data-stu-id="30c1d-173">SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS</span></span>  
  
-   <span data-ttu-id="30c1d-174">SQL_SOPT_SS_QUERYNOTIFICATION_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="30c1d-174">SQL_SOPT_SS_QUERYNOTIFICATION_TIMEOUT</span></span>  
  
 <span data-ttu-id="30c1d-175">如果 SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT 和 SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS 不为 NULL，每次执行命令时，则不会向服务器发送包含上面定义的三个属性的查询通知 TDS 头。</span><span class="sxs-lookup"><span data-stu-id="30c1d-175">If SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT and SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS are not NULL, the query notifications TDS header containing the three attributes defined above will be sent to the server each time the command is executed.</span></span> <span data-ttu-id="30c1d-176">如果上述两个属性中的任一属性为 Null，则不会发送标头，并返回 SQL_SUCCESS_WITH_INFO。</span><span class="sxs-lookup"><span data-stu-id="30c1d-176">If either of them is null, the header is not sent, and SQL_SUCCESS_WITH_INFO is returned.</span></span> <span data-ttu-id="30c1d-177">验证在[SQLPrepare 函数](https://go.microsoft.com/fwlink/?LinkId=59360)、 **SqlExecDirect**和**SqlExecute**上进行，如果特性无效，则所有这些操作都将失败。</span><span class="sxs-lookup"><span data-stu-id="30c1d-177">The validation occurs on [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360), **SqlExecDirect**, and **SqlExecute**, all of which fail if the attributes are not valid.</span></span> <span data-ttu-id="30c1d-178">类似地，当针对 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 之前的 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 版本设置这些查询通知属性时，执行将失败，并返回 SQL_SUCCESS_WITH_INFO。</span><span class="sxs-lookup"><span data-stu-id="30c1d-178">Similarly, when these query notification attributes are set for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] versions before [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], the execution fails with SQL_SUCCESS_WITH_INFO.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30c1d-179">准备语句永远不会启动订阅；可以通过执行语句启动订阅。</span><span class="sxs-lookup"><span data-stu-id="30c1d-179">Prepare statements will never cause the subscription to be initiated; subscription can be initiated by statement execution.</span></span>  
  
## <a name="special-cases-and-restrictions"></a><span data-ttu-id="30c1d-180">特殊事例和限制</span><span class="sxs-lookup"><span data-stu-id="30c1d-180">Special Cases and Restrictions</span></span>  
 <span data-ttu-id="30c1d-181">通知不支持以下数据类型：</span><span class="sxs-lookup"><span data-stu-id="30c1d-181">The following data types are not supported for notifications:</span></span>  
  
-   `text`  
  
-   `ntext`  
  
-   `image`  
  
 <span data-ttu-id="30c1d-182">如果针对返回以上任一类型的查询执行通知请求，则立即激发通知，并指明不可能实现通知订阅。</span><span class="sxs-lookup"><span data-stu-id="30c1d-182">If a notification request is made for a query which returns any of these types, the notification fires immediately, specifying that notification subscription was not possible.</span></span>  
  
 <span data-ttu-id="30c1d-183">如果发出批处理或存储过程订阅请求，则会针对批处理或存储过程内执行的每个语句发出单独的订阅请求。</span><span class="sxs-lookup"><span data-stu-id="30c1d-183">If a subscription request is made for a batch or stored procedure, a separate subscription request is made for each statement executed within the batch or stored procedure.</span></span> <span data-ttu-id="30c1d-184">EXECUTE 语句不会注册通知，但是会将通知请求发送到已执行的命令。</span><span class="sxs-lookup"><span data-stu-id="30c1d-184">EXECUTE statements will not register a notification, but will send the notification request to the executed command.</span></span> <span data-ttu-id="30c1d-185">如果为批处理，则上下文将适用于已执行的语句，并且应用上述相同规则。</span><span class="sxs-lookup"><span data-stu-id="30c1d-185">If it is a batch, the context will be applied to the executed statements and the same rules described above apply.</span></span>  
  
 <span data-ttu-id="30c1d-186">提交通知的查询，该查询由同一用户在同一数据库上下文中提交，并且具有相同的模板、相同的参数值、相同的通知 ID 以及与现有活动订阅相同的送达位置，将续订现有订阅，并重置新指定的超时值。这意味着，如果针对相同的查询请求通知，则仅发送一条通知。</span><span class="sxs-lookup"><span data-stu-id="30c1d-186">Submission of a query for notification that was submitted by the same user under the same database context and has the same template, same parameter values, same notification ID, and same delivery location of an existing active subscription, will renew the existing subscription, resetting the new specified time-out. This means that if notification is requested for identical queries, only one notification will be sent.</span></span> <span data-ttu-id="30c1d-187">这将适用于批处理中的重复查询，也适用于存储过程中调用多次的查询。</span><span class="sxs-lookup"><span data-stu-id="30c1d-187">This would apply to a query duplicated in a batch, or a query in a stored procedure that was called multiple times.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30c1d-188">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30c1d-188">See Also</span></span>  
 [<span data-ttu-id="30c1d-189">SQL Server Native Client 功能</span><span class="sxs-lookup"><span data-stu-id="30c1d-189">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
