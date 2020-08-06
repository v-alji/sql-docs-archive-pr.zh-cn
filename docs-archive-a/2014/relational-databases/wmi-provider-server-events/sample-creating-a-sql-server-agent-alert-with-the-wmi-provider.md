---
title: 示例：使用 WMI Provider for Server Events 创建 SQL Server 代理警报 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- SQL Server Agent [WMI]
- WMI Provider for Server Events, samples
- sample applications [WMI]
ms.assetid: d44811c7-cd46-4017-b284-c863ca088e8f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f23a3a8738435dc6a27a230f4521300a3ee2470f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690415"
---
# <a name="sample-creating-a-sql-server-agent-alert-by-using-the-wmi-provider-for-server-events"></a><span data-ttu-id="4b07d-102">示例：使用 WMI Provider for Server Events 创建 SQL Server 代理警报</span><span class="sxs-lookup"><span data-stu-id="4b07d-102">Sample: Creating a SQL Server Agent Alert by Using the WMI Provider for Server Events</span></span>
  <span data-ttu-id="4b07d-103">WMI 事件提供程序的一个常见用法是创建响应特定事件的 SQL Server 代理警报。</span><span class="sxs-lookup"><span data-stu-id="4b07d-103">One common way to use the WMI Event Provider is to create SQL Server Agent alerts that respond to specific events.</span></span> <span data-ttu-id="4b07d-104">以下示例提供一个在表中保存 XML 死锁图形事件以供以后分析的简单警报。</span><span class="sxs-lookup"><span data-stu-id="4b07d-104">The following sample presents a simple alert that saves XML deadlock graph events in a table for later analysis.</span></span> <span data-ttu-id="4b07d-105">SQL Server 代理提交 WQL 请求、接收 WMI 事件并运行作业以响应该事件。</span><span class="sxs-lookup"><span data-stu-id="4b07d-105">SQL Server Agent submits a WQL request, receives WMI events, and runs a job in response to the event.</span></span> <span data-ttu-id="4b07d-106">请注意，尽管在处理通知消息中涉及几个 Service Broker 对象，WMI 事件提供程序将处理创建和管理这些对象的详细信息。</span><span class="sxs-lookup"><span data-stu-id="4b07d-106">Notice that, although several Service Broker objects are involved in processing the notification message, the WMI Event Provider handles the details of creating and managing these objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b07d-107">示例</span><span class="sxs-lookup"><span data-stu-id="4b07d-107">Example</span></span>  
 <span data-ttu-id="4b07d-108">首先，在 `AdventureWorks` 数据库中创建一个表来存放死锁图形事件。</span><span class="sxs-lookup"><span data-stu-id="4b07d-108">First, a table is created in the `AdventureWorks` database to hold the deadlock graph event.</span></span> <span data-ttu-id="4b07d-109">该表包含两列：`AlertTime` 列存放警报运行的时间，`DeadlockGraph` 列则存放包含死锁图形的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="4b07d-109">The table contains two columns: The `AlertTime` column holds the time that the alert runs, and the `DeadlockGraph` column holds the XML document that contains the deadlock graph.</span></span>  
  
 <span data-ttu-id="4b07d-110">然后，创建警报。</span><span class="sxs-lookup"><span data-stu-id="4b07d-110">Then, the alert is created.</span></span> <span data-ttu-id="4b07d-111">脚本首先创建将运行警报的作业，将作业步骤添加到作业，然后指定作业目标为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的当前实例。</span><span class="sxs-lookup"><span data-stu-id="4b07d-111">The script first creates the job that the alert will run, adds a job step to the job, and targets the job to the current instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4b07d-112">然后，脚本创建警报。</span><span class="sxs-lookup"><span data-stu-id="4b07d-112">The script then creates the alert.</span></span>  
  
 <span data-ttu-id="4b07d-113">作业步骤检索 WMI 事件实例的**TextData**属性，并将该值插入到**DeadlockEvents**表的**DeadlockGraph**列中。</span><span class="sxs-lookup"><span data-stu-id="4b07d-113">The job step retrieves the **TextData** property of the WMI event instance and inserts that value into the **DeadlockGraph** column of the **DeadlockEvents** table.</span></span> <span data-ttu-id="4b07d-114">请注意，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将该字符串隐式转换为 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="4b07d-114">Notice that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implicitly converts the string into XML format.</span></span> <span data-ttu-id="4b07d-115">因为作业步骤使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 子系统，因此它不指定代理。</span><span class="sxs-lookup"><span data-stu-id="4b07d-115">Because the job step uses the [!INCLUDE[tsql](../../includes/tsql-md.md)] subsystem, the job step does not specify a proxy.</span></span>  
  
 <span data-ttu-id="4b07d-116">每当记录死锁图形跟踪事件时，警报都将运行该作业。</span><span class="sxs-lookup"><span data-stu-id="4b07d-116">The alert runs the job whenever a deadlock graph trace event would be logged.</span></span> <span data-ttu-id="4b07d-117">对于 WMI 警报，SQL Server 代理使用指定的命名空间和 WQL 语句创建一个通知查询。</span><span class="sxs-lookup"><span data-stu-id="4b07d-117">For a WMI alert, SQL Server Agent creates a notification query using the namespace and WQL statement specified.</span></span> <span data-ttu-id="4b07d-118">对于此警报，SQL Server 代理监视本地计算机上的默认实例。</span><span class="sxs-lookup"><span data-stu-id="4b07d-118">For this alert, SQL Server Agent monitors the default instance on the local computer.</span></span> <span data-ttu-id="4b07d-119">WQL 语句请求默认实例中的任何 `DEADLOCK_GRAPH` 事件。</span><span class="sxs-lookup"><span data-stu-id="4b07d-119">The WQL statement requests any `DEADLOCK_GRAPH` event in the default instance.</span></span> <span data-ttu-id="4b07d-120">若要更改警报监视的实例，请替换该警报的 `MSSQLSERVER` 中 `@wmi_namespace` 的实例名称。</span><span class="sxs-lookup"><span data-stu-id="4b07d-120">To change the instance that the alert monitors, substitute the instance name for `MSSQLSERVER` in the `@wmi_namespace` for the alert.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b07d-121">对于接收 WMI 事件的 SQL Server 代理， [!INCLUDE[ssSB](../../includes/sssb-md.md)] 必须在**msdb**和中启用 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4b07d-121">For SQL Server Agent to receive WMI events, [!INCLUDE[ssSB](../../includes/sssb-md.md)] must be enabled in **msdb** and [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
```  
USE AdventureWorks ;  
GO  
  
IF OBJECT_ID('DeadlockEvents', 'U') IS NOT NULL  
BEGIN  
    DROP TABLE DeadlockEvents ;  
END ;  
GO  
  
CREATE TABLE DeadlockEvents  
    (AlertTime DATETIME, DeadlockGraph XML) ;  
GO  
-- Add a job for the alert to run.  
  
EXEC  msdb.dbo.sp_add_job @job_name=N'Capture Deadlock Graph',   
    @enabled=1,   
    @description=N'Job for responding to DEADLOCK_GRAPH events' ;  
GO  
  
-- Add a jobstep that inserts the current time and the deadlock graph into  
-- the DeadlockEvents table.  
  
EXEC msdb.dbo.sp_add_jobstep  
    @job_name = N'Capture Deadlock Graph',  
    @step_name=N'Insert graph into LogEvents',  
    @step_id=1,   
    @on_success_action=1,   
    @on_fail_action=2,   
    @subsystem=N'TSQL',   
    @command= N'INSERT INTO DeadlockEvents  
                (AlertTime, DeadlockGraph)  
                VALUES (getdate(), N''$(ESCAPE_SQUOTE(WMI(TextData)))'')',  
    @database_name=N'AdventureWorks' ;  
GO  
  
-- Set the job server for the job to the current instance of SQL Server.  
  
EXEC msdb.dbo.sp_add_jobserver @job_name = N'Capture Deadlock Graph' ;  
GO  
  
-- Add an alert that responds to all DEADLOCK_GRAPH events for  
-- the default instance. To monitor deadlocks for a different instance,  
-- change MSSQLSERVER to the name of the instance.  
  
EXEC msdb.dbo.sp_add_alert @name=N'Respond to DEADLOCK_GRAPH',   
@wmi_namespace=N'\\.\root\Microsoft\SqlServer\ServerEvents\MSSQLSERVER',   
    @wmi_query=N'SELECT * FROM DEADLOCK_GRAPH',   
    @job_name='Capture Deadlock Graph' ;  
GO  
```  
  
## <a name="testing-the-sample"></a><span data-ttu-id="4b07d-122">测试示例</span><span class="sxs-lookup"><span data-stu-id="4b07d-122">Testing the Sample</span></span>  
 <span data-ttu-id="4b07d-123">若要查看作业运行情况，请造成死锁。</span><span class="sxs-lookup"><span data-stu-id="4b07d-123">To see the job run, provoke a deadlock.</span></span> <span data-ttu-id="4b07d-124">在中 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，打开两个**SQL 查询**选项卡，并将两个查询连接到同一个实例。</span><span class="sxs-lookup"><span data-stu-id="4b07d-124">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open two **SQL Query** tabs and connect both queries to the same instance.</span></span> <span data-ttu-id="4b07d-125">在其中一个查询选项卡中运行以下脚本。</span><span class="sxs-lookup"><span data-stu-id="4b07d-125">Run the following script in one of the query tabs.</span></span> <span data-ttu-id="4b07d-126">此脚本生成一个结果集，然后结束。</span><span class="sxs-lookup"><span data-stu-id="4b07d-126">This script produces one result set and finishes.</span></span>  
  
```  
USE AdventureWorks ;  
GO  
  
BEGIN TRANSACTION ;  
GO  
  
SELECT TOP(1) Name FROM Production.Product WITH (XLOCK) ;  
GO  
```  
  
 <span data-ttu-id="4b07d-127">在第二个 "查询" 选项卡中运行以下脚本。此脚本生成一个结果集，然后阻止等待获取锁定 `Production.Product` 。</span><span class="sxs-lookup"><span data-stu-id="4b07d-127">Run the following script in the second query tab. This script produces one result set and then blocks, waiting to acquire a lock on `Production.Product`.</span></span>  
  
```  
USE AdventureWorks ;  
GO  
  
BEGIN TRANSACTION ;  
GO  
  
SELECT TOP(1) Name FROM Production.Location WITH (XLOCK) ;  
GO  
  
SELECT TOP(1) Name FROM Production.Product WITH (XLOCK) ;  
GO  
```  
  
 <span data-ttu-id="4b07d-128">在第一个 "查询" 选项卡中运行以下脚本。此脚本会阻止等待获取锁定 `Production.Location` 。</span><span class="sxs-lookup"><span data-stu-id="4b07d-128">Run the following script in the first query tab. This script blocks, waiting to acquire a lock on `Production.Location`.</span></span> <span data-ttu-id="4b07d-129">在很短的超时值过后，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将选择此脚本或示例中的脚本作为死锁牺牲品，然后结束事务。</span><span class="sxs-lookup"><span data-stu-id="4b07d-129">After a short time-out, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will choose either this script or the script in the sample as the deadlock victim and end the transaction.</span></span>  
  
```  
SELECT TOP(1) Name FROM Production.Location WITH (XLOCK) ;  
GO  
```  
  
 <span data-ttu-id="4b07d-130">造成死锁后，等待一段时间，以便 SQL Server 代理激活警报并运行作业。</span><span class="sxs-lookup"><span data-stu-id="4b07d-130">After provoking the deadlock, wait several moments for SQL Server Agent to activate the alert and run the job.</span></span> <span data-ttu-id="4b07d-131">通过运行以下脚本查看 `DeadlockEvents` 表的内容：</span><span class="sxs-lookup"><span data-stu-id="4b07d-131">Examine the contents of the `DeadlockEvents` table by running the following script:</span></span>  
  
```  
SELECT * FROM DeadlockEvents ;  
GO  
```  
  
 <span data-ttu-id="4b07d-132">`DeadlockGraph` 列应包含显示死锁图形事件的所有属性的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="4b07d-132">The `DeadlockGraph` column should contain an XML document that shows all the properties of the deadlock graph event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b07d-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b07d-133">See Also</span></span>  
 [<span data-ttu-id="4b07d-134">WMI Provider for Server Events 的概念</span><span class="sxs-lookup"><span data-stu-id="4b07d-134">WMI Provider for Server Events Concepts</span></span>](wmi-provider-for-server-events-concepts.md)  
  
  
