---
title: 了解服务器事件的 WMI 提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- architecture [WMI]
- SQL Server Agent [WMI]
- WMI Provider for Server Events, about WMI Provider for Server Events
ms.assetid: 8fd7bd18-76d0-4b28-8fee-8ad861441ab2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ef583d479e473b6f5e71fef59f2221697248b45f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692824"
---
# <a name="understanding-the-wmi-provider-for-server-events"></a><span data-ttu-id="de0ce-102">了解 WMI Provider for Server Events</span><span class="sxs-lookup"><span data-stu-id="de0ce-102">Understanding the WMI Provider for Server Events</span></span>
  <span data-ttu-id="de0ce-103">使用服务器事件的 WMI 提供程序，可以使用 Windows Management Instrumentation (WMI) 监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中的事件。</span><span class="sxs-lookup"><span data-stu-id="de0ce-103">The WMI Provider for Server Events lets you use the Windows Management Instrumentation (WMI) to monitor events in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="de0ce-104">该提供程序的运行方式是将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 转换为托管的 WMI 对象。</span><span class="sxs-lookup"><span data-stu-id="de0ce-104">The provider works by turning [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] into a managed WMI object.</span></span> <span data-ttu-id="de0ce-105">通过使用该提供程序，WMI 可以利用在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中生成事件通知的任何事件。</span><span class="sxs-lookup"><span data-stu-id="de0ce-105">Any event that can generate an event notification in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be leveraged by the WMI by using this provider.</span></span> <span data-ttu-id="de0ce-106">另外，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作为与 WMI 交互的管理应用程序，可以对这些事件做出响应，从而使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理所覆盖的事件范围超过了以前的版本。</span><span class="sxs-lookup"><span data-stu-id="de0ce-106">Additionally, as a management application that interacts with the WMI, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can respond to these events, increasing the scope of events covered by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent over earlier releases.</span></span>

 <span data-ttu-id="de0ce-107">通过发出 WMI 查询语言 (WQL) 语句，诸如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理这样的管理应用程序可以使用 WMI Provider for Server Events 来访问 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 事件。</span><span class="sxs-lookup"><span data-stu-id="de0ce-107">Management applications such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events using the WMI Provider for Server Events by issuing WMI Query Language (WQL) statements.</span></span> <span data-ttu-id="de0ce-108">WQL 是结构化查询语言 (SQL) 的简化子集，它还包含一些特定于 WMI 的扩展。</span><span class="sxs-lookup"><span data-stu-id="de0ce-108">WQL is a simplified subset of structured query language (SQL), with some WMI-specific extensions.</span></span> <span data-ttu-id="de0ce-109">在使用 WQL 时，应用程序将针对特定数据库或数据库对象来检索事件类型。</span><span class="sxs-lookup"><span data-stu-id="de0ce-109">In using WQL, an application retrieves an event type against a specific database or database object.</span></span> <span data-ttu-id="de0ce-110">WMI Provider for Server Events 会将查询转换成事件通知，实际上就是在目标数据库中创建事件通知。</span><span class="sxs-lookup"><span data-stu-id="de0ce-110">The WMI Provider for Server Events translates the query into an event notification, effectively creating an event notification in the target database.</span></span> <span data-ttu-id="de0ce-111">有关事件通知在中的工作方式的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅[WMI Provider For Server Events 的概念](https://technet.microsoft.com/library/ms180560.aspx)。</span><span class="sxs-lookup"><span data-stu-id="de0ce-111">For more information about how event notifications work in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [WMI Provider for Server Events Concepts](https://technet.microsoft.com/library/ms180560.aspx).</span></span> <span data-ttu-id="de0ce-112">[WMI Provider For Server Events 类和属性](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-classes-and-properties.md)中列出了可以查询的事件。</span><span class="sxs-lookup"><span data-stu-id="de0ce-112">The events that can be queried are listed in [WMI Provider for Server Events Classes and Properties](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-classes-and-properties.md).</span></span>

 <span data-ttu-id="de0ce-113">当发生触发事件通知的事件以发送消息时，该消息将发送到**msdb**中名为**SQL/notification/ProcessWMIEventProviderNotification/** v1.0 的预定义目标服务。</span><span class="sxs-lookup"><span data-stu-id="de0ce-113">When an event occurs that triggers the event notification to send a message, the message goes to a predefined target service in **msdb** that is named **SQL/Notifications/ProcessWMIEventProviderNotification/v1.0**.</span></span> <span data-ttu-id="de0ce-114">服务将事件放入**msdb**中名为**WMIEventProviderNotificationQueue**的预定义队列。</span><span class="sxs-lookup"><span data-stu-id="de0ce-114">The service puts the event into a predefined queue in **msdb** that is named **WMIEventProviderNotificationQueue**.</span></span> <span data-ttu-id="de0ce-115"> (在第一次连接到时，提供程序会动态创建服务和队列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 ) 提供程序将从该队列中读取事件数据，并在将其返回到应用程序之前将其转换为托管对象格式 (MOF) 。</span><span class="sxs-lookup"><span data-stu-id="de0ce-115">(Both the service and the queue are created dynamically by the provider when it first connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].) The provider then reads the event data from this queue and transforms it into managed object format (MOF) before returning it to the application.</span></span> <span data-ttu-id="de0ce-116">下图显示了此过程。</span><span class="sxs-lookup"><span data-stu-id="de0ce-116">The following illustration shows this process.</span></span>

 <span data-ttu-id="de0ce-117">![WMI Provider for Server Events 的流程图](../../../2014/database-engine/dev-guide/media/wmi-provider-functional-spec.gif "WMI Provider for Server Events 的流程图")</span><span class="sxs-lookup"><span data-stu-id="de0ce-117">![Flow diagram of the WMI Provider for Server Events](../../../2014/database-engine/dev-guide/media/wmi-provider-functional-spec.gif "Flow diagram of the WMI Provider for Server Events")</span></span>

 <span data-ttu-id="de0ce-118">例如，请考虑下列 WQL 查询：</span><span class="sxs-lookup"><span data-stu-id="de0ce-118">For example, consider the following WQL Query:</span></span>

```
SELECT * FROM DDL_DATABASE_LEVEL_EVENTS
WHERE DatabaseName = 'AdventureWorks'
```

 <span data-ttu-id="de0ce-119">在响应该查询时，WMI Provider for Server Events 将在目标数据库中创建等效的事件通知：</span><span class="sxs-lookup"><span data-stu-id="de0ce-119">In response to this query, the WMI Provider for Server Events creates the equivalent event notification in the target database:</span></span>

```
USE AdventureWorks ;
GO
CREATE EVENT NOTIFICATION SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9
    ON DATABASE
    WITH FAN_IN
    FOR DDL_DATABASE_LEVEL_EVENTS
    TO SERVICE
        'SQL/Notifications/ProcessWMIEventProviderNotification/v1.0', 
        'A7E5521A-1CA6-4741-865D-826F804E5135';
GO
```

 <span data-ttu-id="de0ce-120">在该示例中，`SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9` 是由前缀 `SQLWEP_` 和 GUID 组成的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 标识符。</span><span class="sxs-lookup"><span data-stu-id="de0ce-120">In this example, `SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9` is a [!INCLUDE[tsql](../../includes/tsql-md.md)] identifier that is made up of the prefix `SQLWEP_` and a GUID.</span></span> <span data-ttu-id="de0ce-121">`SQLWEP` 为每个标识符创建一个新的 GUID。</span><span class="sxs-lookup"><span data-stu-id="de0ce-121">`SQLWEP` creates a new GUID for each identifier.</span></span> <span data-ttu-id="de0ce-122">`A7E5521A-1CA6-4741-865D-826F804E5135`子句中的值 `TO SERVICE` 是用于标识**msdb**数据库中 broker 实例的 GUID。</span><span class="sxs-lookup"><span data-stu-id="de0ce-122">The value `A7E5521A-1CA6-4741-865D-826F804E5135` in the `TO SERVICE` clause is the GUID that identifies the broker instance in the **msdb** database.</span></span>

 <span data-ttu-id="de0ce-123">有关如何使用 WQL 的详细信息，请参阅[将 WQL 与 WMI Provider For Server Events 结合使用](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="de0ce-123">For more information about how to work with WQL, see [Using WQL with the WMI Provider for Server Events](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx).</span></span>

 <span data-ttu-id="de0ce-124">通过连接到由 WMI Provider for Server Events 定义的 WMI 命名空间，管理应用程序将该提供程序定向到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="de0ce-124">Management applications direct the WMI Provider for Server Events to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by connecting to a WMI namespace that is defined by the provider.</span></span> <span data-ttu-id="de0ce-125">Windows WMI 服务将此命名空间映射到提供程序 DLL Sqlwep.dll 并将其加载到内存。</span><span class="sxs-lookup"><span data-stu-id="de0ce-125">The Windows WMI service maps this namespace to the provider DLL, Sqlwep.dll, and loads it into memory.</span></span> <span data-ttu-id="de0ce-126">提供程序为每个实例管理服务器事件的 WMI 命名空间 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，格式为： \\ \\ 。 \\*root*\Microsoft\SqlServer\ServerEvents \\ *instance_name*，其中*instance_name*默认为 MSSQLSERVER。</span><span class="sxs-lookup"><span data-stu-id="de0ce-126">The provider manages a WMI namespace for Server Events for each instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and the format is: \\\\.\\*root*\Microsoft\SqlServer\ServerEvents\\*instance_name*, where *instance_name* defaults to MSSQLSERVER.</span></span> <span data-ttu-id="de0ce-127">有关如何连接到实例的 WMI 命名空间的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅将[WQL 与 wmi Provider For Server Events 结合使用](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="de0ce-127">For more information about how to connect to a WMI namespace for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Using WQL with the WMI Provider for Server Events](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx).</span></span>

 <span data-ttu-id="de0ce-128">提供程序 DLL Sqlwep.dll 仅会加载一次以载入到服务器操作系统的 WMI 主机服务中，而不管服务器上有多少个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="de0ce-128">The provider DLL, Sqlwep.dll, is loaded only one time into the WMI host service of the operating system of the server, regardless of how many instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are on the server.</span></span>

 <span data-ttu-id="de0ce-129">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用 Wmi provider For Server events 的代理管理应用程序的示例，请参阅[示例：使用 wmi Provider For Server events 创建 SQL Server 代理警报](https://technet.microsoft.com/library/ms186385.aspx)。</span><span class="sxs-lookup"><span data-stu-id="de0ce-129">For an example of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent management application that uses the WMI Provider for Server Events, see [Sample: Creating a SQL Server Agent Alert Using the WMI Provider for Server Events](https://technet.microsoft.com/library/ms186385.aspx).</span></span> <span data-ttu-id="de0ce-130">有关在托管代码中使用 WMI Provider for Server Events 的管理应用程序的示例，请参阅[示例：在托管代码中使用 Wmi 事件提供程序](https://technet.microsoft.com/library/ms179315.aspx)。</span><span class="sxs-lookup"><span data-stu-id="de0ce-130">For an example of a management application that uses the WMI Provider for Server Events in managed code, see [Sample: Using the WMI Event Provider in Managed Code](https://technet.microsoft.com/library/ms179315.aspx).</span></span> <span data-ttu-id="de0ce-131">有关 SDK 中的 WMI 的详细信息，请参阅 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="de0ce-131">More information is also available about WMI in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.</span></span>

## <a name="see-also"></a><span data-ttu-id="de0ce-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="de0ce-132">See Also</span></span>
 [<span data-ttu-id="de0ce-133">WMI Provider for Server Events 的概念</span><span class="sxs-lookup"><span data-stu-id="de0ce-133">WMI Provider for Server Events Concepts</span></span>](https://technet.microsoft.com/library/ms180560.aspx)


