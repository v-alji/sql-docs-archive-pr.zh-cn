---
title: WMI Provider for Server Events 类和属性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- event classes [WMI]
- WMI Provider for Server Events, events listed
- classes [WMI]
ms.assetid: e2916cd7-a3ed-41e6-97b4-2ee060754cbe
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 471e77cb7afa4e6aed441dcbbc8b3b70064f6737
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692817"
---
# <a name="wmi-provider-for-server-events-classes-and-properties"></a><span data-ttu-id="36a96-102">WMI Provider for Server Events 类和属性</span><span class="sxs-lookup"><span data-stu-id="36a96-102">WMI Provider for Server Events Classes and Properties</span></span>
  <span data-ttu-id="36a96-103">以下服务器事件构成了 WMI Provider for Server Events 的编程模型。</span><span class="sxs-lookup"><span data-stu-id="36a96-103">The following server events make up the programming model for the WMI Provider for Server Events.</span></span> <span data-ttu-id="36a96-104">通过针对提供程序发出 WQL 查询，可以对两种主要的事件类别进行查询。</span><span class="sxs-lookup"><span data-stu-id="36a96-104">There are two main categories of events that can be queried by issuing WQL queries against the provider.</span></span> <span data-ttu-id="36a96-105">它们分别是数据定义语言 (DDL) 事件和跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="36a96-105">These are data definition language (DDL) events and trace events.</span></span> <span data-ttu-id="36a96-106">还可以查询 QUEUE_ACTIVATION 和 BROKER_QUEUE_DISABLED Service Broker 事件。</span><span class="sxs-lookup"><span data-stu-id="36a96-106">The QUEUE_ACTIVATION and BROKER_QUEUE_DISABLED service broker events can also be queried.</span></span> <span data-ttu-id="36a96-107">请注意以下树形关系图中的内在关系。</span><span class="sxs-lookup"><span data-stu-id="36a96-107">Note the inclusive nature of the following tree diagrams.</span></span> <span data-ttu-id="36a96-108">例如，DDL_ASSEMBLY_EVENTS 事件包括任意 ALTER_ASSEMBLY、CREATE_ASSEMBLY 和 DROP_ASSEMBLY 事件。</span><span class="sxs-lookup"><span data-stu-id="36a96-108">The DDL_ASSEMBLY_EVENTS event, for example, includes any ALTER_ASSEMBLY, CREATE_ASSEMBLY, and DROP_ASSEMBLY event.</span></span> <span data-ttu-id="36a96-109">同样，TRC_FULL_TEXT 事件包括任意 FT_CRAWL_ABORTED、FT_CRAWL_STARTED 和 FT_CRAWL_STOPPED 事件。</span><span class="sxs-lookup"><span data-stu-id="36a96-109">Similarly, the TRC_FULL_TEXT event includes any FT_CRAWL_ABORTED, FT_CRAWL_STARTED, and FT_CRAWL_STOPPED event.</span></span> <span data-ttu-id="36a96-110">ALL_EVENTS 包括所有 DDL 事件、跟踪事件、QUEUE_ACTIVATION 和 BROKER_QUEUE_DISABLED。</span><span class="sxs-lookup"><span data-stu-id="36a96-110">ALL_EVENTS covers all DDL events, trace events, QUEUE_ACTIVATION, and BROKER_QUEUE_DISABLED.</span></span>  
  
 <span data-ttu-id="36a96-111">若要了解可以通过事件或事件组查询的属性，请参考事件架构。</span><span class="sxs-lookup"><span data-stu-id="36a96-111">To learn which properties can be queried from an event or event group, refer to the event schema.</span></span> <span data-ttu-id="36a96-112">默认情况下，事件架构安装在以下目录中：[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools\Binn\schemas\sqlserver\2006\11\events\events.xsd。</span><span class="sxs-lookup"><span data-stu-id="36a96-112">By default, the event schema is installed in the following directory: [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools\Binn\schemas\sqlserver\2006\11\events\events.xsd.</span></span>  
  
 <span data-ttu-id="36a96-113">或者，您可以引用在处发布的事件架构 [https://schemas.microsoft.com/sqlserver](https://go.microsoft.com/fwlink/?linkid=43100) 。</span><span class="sxs-lookup"><span data-stu-id="36a96-113">Alternatively, you can refer to the event schema published at [https://schemas.microsoft.com/sqlserver](https://go.microsoft.com/fwlink/?linkid=43100).</span></span>  
  
 <span data-ttu-id="36a96-114">例如，通过参考 ALTER_DATABASE 事件，您将了解到该事件的父事件为 DDL_SERVER_LEVEL_EVENTS，该事件的属性为 `TSQLCommand` 和 `DatabaseName`。</span><span class="sxs-lookup"><span data-stu-id="36a96-114">For example, by referring to the ALTER_DATABASE event, you will learn that its parent event is DDL_SERVER_LEVEL_EVENTS and its properties are `TSQLCommand` and `DatabaseName`.</span></span> <span data-ttu-id="36a96-115">该事件还继承属性 `SQLInstance`、`PostTime`、`ComputerName`、`SPID` 和 `LoginName`。</span><span class="sxs-lookup"><span data-stu-id="36a96-115">The event also inherits the properties `SQLInstance`, `PostTime`, `ComputerName`, `SPID`, and `LoginName`.</span></span> <span data-ttu-id="36a96-116">该事件没有子事件。</span><span class="sxs-lookup"><span data-stu-id="36a96-116">The event has no children events.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="36a96-117">执行 DDL 式操作的系统存储过程还可以激发事件通知。</span><span class="sxs-lookup"><span data-stu-id="36a96-117">System stored procedures that perform DDL-like operations can also fire event notifications.</span></span> <span data-ttu-id="36a96-118">测试您的事件通知以确定它们是否响应运行的系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="36a96-118">Test your event notifications to determine their responses to system stored procedures that are run.</span></span> <span data-ttu-id="36a96-119">例如，CREATE TYPE 语句和**sp_addtype**存储过程都将激发在 CREATE_TYPE 事件上创建的事件通知。</span><span class="sxs-lookup"><span data-stu-id="36a96-119">For example, the CREATE TYPE statement and **sp_addtype** stored procedure will both fire an event notification that is created on a CREATE_TYPE event.</span></span> <span data-ttu-id="36a96-120">有关详细信息，请参阅[DDL 事件](../../relational-databases/triggers/ddl-events.md)。</span><span class="sxs-lookup"><span data-stu-id="36a96-120">For more information, see[DDL Events](../../relational-databases/triggers/ddl-events.md).</span></span>  
  
 <span data-ttu-id="36a96-121">**数据定义语言事件和事件组**</span><span class="sxs-lookup"><span data-stu-id="36a96-121">**Data Definition Language Events and Event Groups**</span></span>  
  
 <span data-ttu-id="36a96-122">![WMI Provider for Server Events 事件树](../../../2014/database-engine/dev-guide/media/sql-wmi-ddl-events-ktm.gif "WMI Provider for Server Events 事件树")</span><span class="sxs-lookup"><span data-stu-id="36a96-122">![WMI Provider for Server Events Event Tree](../../../2014/database-engine/dev-guide/media/sql-wmi-ddl-events-ktm.gif "WMI Provider for Server Events Event Tree")</span></span>  
  
 <span data-ttu-id="36a96-123">**跟踪事件和事件组**</span><span class="sxs-lookup"><span data-stu-id="36a96-123">**Trace Events and Event Groups**</span></span>  
  
 <span data-ttu-id="36a96-124">![跟踪事件和事件组](../../../2014/database-engine/dev-guide/media/sql-wmi-trc-all-events.gif "跟踪事件和事件组")</span><span class="sxs-lookup"><span data-stu-id="36a96-124">![Trace events and event groups](../../../2014/database-engine/dev-guide/media/sql-wmi-trc-all-events.gif "Trace events and event groups")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36a96-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="36a96-125">See Also</span></span>  
 <span data-ttu-id="36a96-126">[WMI Provider for Server Events 的概念](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="36a96-126">[WMI Provider for Server Events Concepts](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md) </span></span>  
 [<span data-ttu-id="36a96-127">将 WQL 与 WMI Provider for Server Events 结合使用</span><span class="sxs-lookup"><span data-stu-id="36a96-127">Using WQL with the WMI Provider for Server Events</span></span>](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)  
  
  
