---
title: 处理 SMO 事件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- events [SMO]
- SQL Server Management Objects, events
- SMO [SQL Server], events
- events [SMO], about events
ms.assetid: b4f120dd-ba78-46ff-99c5-e47effac8544
author: stevestein
ms.author: sstein
ms.openlocfilehash: f7ea438142ac283c5ad19670fa827b5e248e80f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590690"
---
# <a name="handling-smo-events"></a><span data-ttu-id="a209c-102">处理 SMO 事件</span><span class="sxs-lookup"><span data-stu-id="a209c-102">Handling SMO Events</span></span>
  <span data-ttu-id="a209c-103">某些服务器事件类型可以通过使用事件处理程序和 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象来进行订阅。</span><span class="sxs-lookup"><span data-stu-id="a209c-103">There are server event types that can be subscribed to by using an event handler and the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
 <span data-ttu-id="a209c-104">当服务器上发生某些操作时，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理对象 (SMO) 中的许多实例类可以触发事件。</span><span class="sxs-lookup"><span data-stu-id="a209c-104">Many of the instance classes in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) can trigger events when certain actions on the server occur.</span></span>  
  
 <span data-ttu-id="a209c-105">通过设置事件处理程序并订阅相关事件，可以以编程方式对这些事件进行处理。</span><span class="sxs-lookup"><span data-stu-id="a209c-105">These events can be handled programmatically by setting up an event handler and subscribing to the associated events.</span></span> <span data-ttu-id="a209c-106">这种事件处理只是暂时性的，因为当 SMO 客户端程序退出时会删除所有的订阅。</span><span class="sxs-lookup"><span data-stu-id="a209c-106">This type of event handling is transient because all the subscriptions are removed when the SMO client program exits.</span></span>  
  
## <a name="connectioncontext-event-handling"></a><span data-ttu-id="a209c-107">ConnectionContext 事件处理</span><span class="sxs-lookup"><span data-stu-id="a209c-107">ConnectionContext Event Handling</span></span>  
 <span data-ttu-id="a209c-108"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 对象支持若干种事件类型。</span><span class="sxs-lookup"><span data-stu-id="a209c-108">The <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object supports several event types.</span></span> <span data-ttu-id="a209c-109">事件属性必须设置为相应事件处理程序的实例，且必须将事件处理程序对象定义为用于处理事件的受保护函数。</span><span class="sxs-lookup"><span data-stu-id="a209c-109">The event property must be set to an instance of an appropriate event handler, and the event handler object must be defined as a protected function that handles the event.</span></span>  
  
## <a name="event-subscription"></a><span data-ttu-id="a209c-110">事件订阅</span><span class="sxs-lookup"><span data-stu-id="a209c-110">Event Subscription</span></span>  
 <span data-ttu-id="a209c-111">您可以通过以下方法处理事件：编写事件处理程序类，创建该类的实例，将事件处理程序分配给父对象，然后订阅事件。</span><span class="sxs-lookup"><span data-stu-id="a209c-111">You handle events by writing an event handler class, creating an instance of it, assigning the event handler to the parent object, and then subscribing to the event.</span></span>  
  
 <span data-ttu-id="a209c-112">必须编写事件处理程序类才能处理事件。</span><span class="sxs-lookup"><span data-stu-id="a209c-112">An event handler class must be written to handle events.</span></span> <span data-ttu-id="a209c-113">事件处理程序类可以包含多个事件处理程序函数，且只有在安装事件处理程序类后才能处理事件。</span><span class="sxs-lookup"><span data-stu-id="a209c-113">The event handler class can contain more than one event handler function, and must be installed for the events to be handled.</span></span> <span data-ttu-id="a209c-114">事件处理程序函数从*ServerEventNotificatificationArgs*参数接收有关事件的信息，该事件可用于报告有关事件的信息。</span><span class="sxs-lookup"><span data-stu-id="a209c-114">The event handler functions receive information about the event from the *ServerEventNotificatificationArgs* parameter that can be used to report information about the event.</span></span>  
  
 <span data-ttu-id="a209c-115">类和类中列出了可以处理的数据库和服务器事件的类型 <xref:Microsoft.SqlServer.Management.Smo.DatabaseEventSet> <xref:Microsoft.SqlServer.Management.Smo.ServerEventSet> 。</span><span class="sxs-lookup"><span data-stu-id="a209c-115">The types of database and server events that can be handled are listed in the <xref:Microsoft.SqlServer.Management.Smo.DatabaseEventSet> class and the <xref:Microsoft.SqlServer.Management.Smo.ServerEventSet>class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a209c-116">示例</span><span class="sxs-lookup"><span data-stu-id="a209c-116">Example</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="registering-event-handlers-and-subscribing-to-event-handling-in-visual-basic"></a><span data-ttu-id="a209c-117">在 Visual Basic 中注册事件处理程序并订阅事件处理</span><span class="sxs-lookup"><span data-stu-id="a209c-117">Registering Event Handlers and Subscribing to Event Handling in Visual Basic</span></span>  
 <span data-ttu-id="a209c-118">此代码示例演示如何设置事件处理程序以及如何订阅数据库事件。</span><span class="sxs-lookup"><span data-stu-id="a209c-118">This code example shows how to set up the event handler, and how to subscribe to the database events.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBEvents1](SMO How to#SMO_VBEvents1)]  -->  
  
## <a name="registering-event-handlers-and-subscribing-to-event-handling-in-visual-c"></a><span data-ttu-id="a209c-119">在 Visual C# 中注册事件处理程序并订阅事件处理</span><span class="sxs-lookup"><span data-stu-id="a209c-119">Registering Event Handlers and Subscribing to Event Handling in Visual C#</span></span>  
 <span data-ttu-id="a209c-120">此代码示例演示如何设置事件处理程序以及如何订阅数据库事件。</span><span class="sxs-lookup"><span data-stu-id="a209c-120">This code example shows how to set up the event handler, and how to subscribe to the database events.</span></span>  
  
```  
//Create an event handler subroutine that runs when a table is created.   
private void MyCreateEventHandler(object sender, ServerEventArgs e)   
{   
Console.WriteLine("A table has just been added to the AdventureWorks2012 database.");   
}   
//Create an event handler subroutine that runs when a table is deleted.   
private void MyDropEventHandler(object sender, ServerEventArgs e)   
{   
Console.WriteLine("A table has just been dropped from the AdventureWorks2012 database.");   
}   
public void Main()   
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Create a database event set that contains the CreateTable event only.   
DatabaseEventSet databaseCreateEventSet = new DatabaseEventSet();   
databaseCreateEventSet.CreateTable = true;   
//Create a server event handler and set it to the first event handler subroutine.   
ServerEventHandler serverCreateEventHandler;   
serverCreateEventHandler = new ServerEventHandler(MyCreateEventHandler);   
//Subscribe to the first server event handler when a CreateTable event occurs.   
db.Events.SubscribeToEvents(databaseCreateEventSet, serverCreateEventHandler);   
    //Create a database event set that contains the DropTable event only.   
DatabaseEventSet databaseDropEventSet = new DatabaseEventSet();   
databaseDropEventSet.DropTable = true;   
//Create a server event handler and set it to the second event handler subroutine.   
ServerEventHandler serverDropEventHandler;   
serverDropEventHandler = new ServerEventHandler(MyDropEventHandler);   
//Subscribe to the second server event handler when a DropTable event occurs.   
db.Events.SubscribeToEvents(databaseDropEventSet, serverDropEventHandler);   
//Start event handling.   
db.Events.StartEvents();   
//Create a table on the database.   
Table tb;   
tb = new Table(db, "Test_Table");   
Column mycol1;   
mycol1 = new Column(tb, "Name", DataType.NChar(50));   
mycol1.Collation = "Latin1_General_CI_AS";   
mycol1.Nullable = true;   
tb.Columns.Add(mycol1);   
tb.Create();   
//Remove the table.   
tb.Drop();   
//Wait until the events have occured.   
int x;   
int y;   
for (x = 1; x <= 1000000000; x++) {   
    y = x * 2;   
}   
//Stop event handling.   
db.Events.StopEvents();   
}  
```  
  
  
