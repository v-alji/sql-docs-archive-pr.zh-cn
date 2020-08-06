---
title: 传输主存储过程任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfermasterspstask.f1
helpviewer_keywords:
- Transfer Master Stored Procedures task [Integration Services]
ms.assetid: 81702560-48a3-46d1-a469-e41304c7af8e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1915a3129eeb6e14c4315c37f2c6c2bf5b0d5412
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693418"
---
# <a name="transfer-master-stored-procedures-task"></a><span data-ttu-id="57d89-102">传输主存储过程任务</span><span class="sxs-lookup"><span data-stu-id="57d89-102">Transfer Master Stored Procedures Task</span></span>
  <span data-ttu-id="57d89-103">传输主存储过程任务在 **的实例上的** master [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库之间传输一个或多个用户定义的存储过程。</span><span class="sxs-lookup"><span data-stu-id="57d89-103">The Transfer Master Stored Procedures task transfers one or more user-defined stored procedures between **master** databases on instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="57d89-104">若要从 **master** 数据库传输存储过程，该过程的所有者必须是 dbo。</span><span class="sxs-lookup"><span data-stu-id="57d89-104">To transfer a stored procedure from the **master** database, the owner of the procedure must be dbo.</span></span>  
  
 <span data-ttu-id="57d89-105">传输主存储过程任务可以配置为传输所有存储过程，也可以配置为只传输指定的存储过程。</span><span class="sxs-lookup"><span data-stu-id="57d89-105">The Transfer Master Stored Procedures task can be configured to transfer all stored procedures or only specified stored procedures.</span></span> <span data-ttu-id="57d89-106">此任务并不复制系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="57d89-106">This task does not copy system stored procedures.</span></span>  
  
 <span data-ttu-id="57d89-107">要传输的主存储过程可能已经存在于目标服务器上。</span><span class="sxs-lookup"><span data-stu-id="57d89-107">The master stored procedures to be transferred may already exist on the destination.</span></span> <span data-ttu-id="57d89-108">传输主存储过程可以配置为以下列方式处理现有存储过程：</span><span class="sxs-lookup"><span data-stu-id="57d89-108">The Transfer Master Stored Procedures task can be configured to handle existing stored procedures in the following ways:</span></span>  
  
-   <span data-ttu-id="57d89-109">覆盖现有存储过程。</span><span class="sxs-lookup"><span data-stu-id="57d89-109">Overwrite existing stored procedures.</span></span>  
  
-   <span data-ttu-id="57d89-110">如果存在重复的存储过程，则该任务失败。</span><span class="sxs-lookup"><span data-stu-id="57d89-110">Fail the task when duplicate stored procedures exist.</span></span>  
  
-   <span data-ttu-id="57d89-111">跳过重复的存储过程。</span><span class="sxs-lookup"><span data-stu-id="57d89-111">Skip duplicate stored procedures.</span></span>  
  
 <span data-ttu-id="57d89-112">在运行时，传输主存储过程任务使用两个 SMO 连接管理器连接到源服务器和目标服务器。</span><span class="sxs-lookup"><span data-stu-id="57d89-112">At run time, the Transfer Master Stored Procedures task connects to the source and destination servers by using two SMO connection managers.</span></span> <span data-ttu-id="57d89-113">SMO 连接管理器与传输主存储过程任务分开进行配置，然后在传输主存储过程任务中引用连接管理器。</span><span class="sxs-lookup"><span data-stu-id="57d89-113">The SMO connection managers are configured separately from the Transfer Master Stored Procedures task, and then referenced in the Transfer Master Stored Procedures task.</span></span> <span data-ttu-id="57d89-114">SMO 连接管理器指定服务器以及在访问该服务器时要使用的身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="57d89-114">The SMO connection managers specify the server and the authentication mode to use when accessing the server.</span></span> <span data-ttu-id="57d89-115">有关详细信息，请参阅 [SMO Connection Manager](../connection-manager/smo-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="57d89-115">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
## <a name="transferring-stored-procedures-between-instances-of-sql-server"></a><span data-ttu-id="57d89-116">在 SQL Server 实例之间传输存储过程</span><span class="sxs-lookup"><span data-stu-id="57d89-116">Transferring Stored Procedures Between Instances of SQL Server</span></span>  
 <span data-ttu-id="57d89-117">传输主存储过程任务支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 源和目标。</span><span class="sxs-lookup"><span data-stu-id="57d89-117">The Transfer Master Stored Procedures task supports a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source and destination.</span></span>  
  
## <a name="events"></a><span data-ttu-id="57d89-118">事件</span><span class="sxs-lookup"><span data-stu-id="57d89-118">Events</span></span>  
 <span data-ttu-id="57d89-119">该任务将引发报告已传输的存储过程数的信息事件，而且在覆盖存储过程时还会引发警告事件。</span><span class="sxs-lookup"><span data-stu-id="57d89-119">The task raises an information event that reports the number of stored procedures transferred and a warning event when a stored procedure is overwritten.</span></span>  
  
 <span data-ttu-id="57d89-120">传输主存储过程任务并不报告存储过程传输的进度；它仅报告 0% 和 100 % 完成。</span><span class="sxs-lookup"><span data-stu-id="57d89-120">The Transfer Master Stored Procedures task does not report incremental progress of the login transfer; it reports only 0% and 100 % completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="57d89-121">执行值</span><span class="sxs-lookup"><span data-stu-id="57d89-121">Execution Value</span></span>  
 <span data-ttu-id="57d89-122">在该任务的 `ExecutionValue` 属性中定义的执行值返回已传输的存储过程数。</span><span class="sxs-lookup"><span data-stu-id="57d89-122">The execution value, defined in the `ExecutionValue` property of the task, returns the number of stored procedures transferred.</span></span> <span data-ttu-id="57d89-123">通过将用户定义的变量分配给传输主存储过程任务的 `ExecValueVariable` 属性，包中的其他对象就可以访问有关存储过程传输的信息。</span><span class="sxs-lookup"><span data-stu-id="57d89-123">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer Master Stored Procedures task, information about the stored procedure transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="57d89-124">有关详细信息，请参阅 [Integration Services (SSIS) 变量](../integration-services-ssis-variables.md)和[在包中使用变量](../use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="57d89-124">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="57d89-125">日志项</span><span class="sxs-lookup"><span data-stu-id="57d89-125">Log Entries</span></span>  
 <span data-ttu-id="57d89-126">传输主存储过程任务包括下列自定义日志项：</span><span class="sxs-lookup"><span data-stu-id="57d89-126">The Transfer Master Stored Procedures task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="57d89-127">TransferStoredProceduresTaskStartTransferringObjects   此日志项报告传输已经开始。</span><span class="sxs-lookup"><span data-stu-id="57d89-127">TransferStoredProceduresTaskStartTransferringObjects  This log entry reports that the transfer has started.</span></span> <span data-ttu-id="57d89-128">日志项包括开始时间。</span><span class="sxs-lookup"><span data-stu-id="57d89-128">The log entry includes the start time.</span></span>  
  
-   <span data-ttu-id="57d89-129">TransferSStoredProceduresTaskFinishedTransferringObjects  此日志项报告传输已经完成。</span><span class="sxs-lookup"><span data-stu-id="57d89-129">TransferSStoredProceduresTaskFinishedTransferringObjects  This log entry reports that the transfer has finished.</span></span> <span data-ttu-id="57d89-130">日志项包括结束时间。</span><span class="sxs-lookup"><span data-stu-id="57d89-130">The log entry includes the end time.</span></span>  
  
 <span data-ttu-id="57d89-131">此外，`OnInformation` 事件的日志项报告已传输的存储过程数，`OnWarning` 事件的日志项是为目标服务器上被覆盖的每个存储过程写入的。</span><span class="sxs-lookup"><span data-stu-id="57d89-131">In addition, a log entry for the `OnInformation` event reports the number of stored procedures that were transferred, and a log entry for the `OnWarning` event is written for each stored procedure on the destination that is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="57d89-132">安全和权限</span><span class="sxs-lookup"><span data-stu-id="57d89-132">Security and Permissions</span></span>  
 <span data-ttu-id="57d89-133">用户必须具有查看源服务器上 **master** 数据库中的存储过程列表的权限，而且必须是 sysadmin 服务器角色的成员，或者必须具有对目标服务器上 **master** 数据库中所创建的存储过程的权限。</span><span class="sxs-lookup"><span data-stu-id="57d89-133">The user must have permission to view the list of stored procedure in the **master** database on the source, and must be a member of the sysadmin server role or have permission to created stored procedures in the **master** database on the destination server.</span></span>  
  
## <a name="configuration-of-the-transfer-master-stored-procedures-task"></a><span data-ttu-id="57d89-134">传输主存储过程任务的配置</span><span class="sxs-lookup"><span data-stu-id="57d89-134">Configuration of the Transfer Master Stored Procedures Task</span></span>  
 <span data-ttu-id="57d89-135">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="57d89-135">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="57d89-136">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的信息，请单击以下主题之一：</span><span class="sxs-lookup"><span data-stu-id="57d89-136">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="57d89-137">传输主存储过程任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="57d89-137">Transfer Master Stored Procedures Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="57d89-138">传输主存储过程任务编辑器（“存储过程”页）</span><span class="sxs-lookup"><span data-stu-id="57d89-138">Transfer Master Stored Procedures Task Editor &#40;Stored Procedures Page&#41;</span></span>](../transfer-master-stored-procedures-task-editor-stored-procedures-page.md)  
  
-   [<span data-ttu-id="57d89-139">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="57d89-139">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="57d89-140">有关以编程方式设置这些属性的信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="57d89-140">For information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferStoredProceduresTask.TransferStoredProceduresTask>  
  
### <a name="configuring-the-transfer-master-stored-procedures-task-programmatically"></a><span data-ttu-id="57d89-141">以编程方式配置传输主存储过程任务</span><span class="sxs-lookup"><span data-stu-id="57d89-141">Configuring the Transfer Master Stored Procedures Task Programmatically</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="57d89-142">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="57d89-142">Related Tasks</span></span>  
 <span data-ttu-id="57d89-143">有关如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="57d89-143">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="57d89-144">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="57d89-144">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="57d89-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57d89-145">See Also</span></span>  
 <span data-ttu-id="57d89-146">[传输 SQL Server 对象任务](transfer-sql-server-objects-task.md) </span><span class="sxs-lookup"><span data-stu-id="57d89-146">[Transfer SQL Server Objects Task](transfer-sql-server-objects-task.md) </span></span>  
 <span data-ttu-id="57d89-147">[Integration Services 任务](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="57d89-147">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="57d89-148">控制流</span><span class="sxs-lookup"><span data-stu-id="57d89-148">Control Flow</span></span>](control-flow.md)  
  
  
