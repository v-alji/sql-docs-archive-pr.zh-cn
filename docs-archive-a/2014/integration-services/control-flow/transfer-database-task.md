---
title: 传输数据库任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.f1
helpviewer_keywords:
- Transfer Database task [Integration Services]
ms.assetid: b9a2e460-cdbc-458f-8df8-06b8b2de3d67
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 85123eaff3e274bb4a96908ea99aef02c328ba23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576914"
---
# <a name="transfer-database-task"></a><span data-ttu-id="e90d1-102">传输数据库任务</span><span class="sxs-lookup"><span data-stu-id="e90d1-102">Transfer Database Task</span></span>
  <span data-ttu-id="e90d1-103">传输数据库任务在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的两个实例之间传输 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库。</span><span class="sxs-lookup"><span data-stu-id="e90d1-103">The Transfer Database task transfers a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database between two instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e90d1-104">与只通过复制方式传输 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象的其他任务相比，传输数据库任务既可以复制也可以移动数据库。</span><span class="sxs-lookup"><span data-stu-id="e90d1-104">In contrast to the other tasks that only transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects by copying them, the Transfer Database task can either copy or move a database.</span></span> <span data-ttu-id="e90d1-105">此任务还可以用来复制同一个服务器上的数据库。</span><span class="sxs-lookup"><span data-stu-id="e90d1-105">This task can also be used to copy a database within the same server.</span></span>  
  
## <a name="offline-and-online-modes"></a><span data-ttu-id="e90d1-106">脱机和联机模式</span><span class="sxs-lookup"><span data-stu-id="e90d1-106">Offline and Online Modes</span></span>  
 <span data-ttu-id="e90d1-107">可以使用联机模式或脱机模式传输数据库。</span><span class="sxs-lookup"><span data-stu-id="e90d1-107">The database can be transferred by using online or offline mode.</span></span> <span data-ttu-id="e90d1-108">在使用联机模式时，数据库保持连接的情况下，通过使用 SQL 管理对象 (SMO) 复制数据库对象来传输数据库。</span><span class="sxs-lookup"><span data-stu-id="e90d1-108">When you use online mode, the database remains attached and it is transferred by using SQL Management Object (SMO) to copy the database objects.</span></span> <span data-ttu-id="e90d1-109">在使用脱机模式时，数据库断开连接，然后复制或移动数据库文件，在传输成功完成后，数据库连接到目标服务器。</span><span class="sxs-lookup"><span data-stu-id="e90d1-109">When you use offline mode, the database is detached, the database files are copied or moved, and the database is attached at the destination after the transfer finishes successfully.</span></span> <span data-ttu-id="e90d1-110">如果是复制数据库，则在复制成功后，数据库自动与源服务器重新连接。</span><span class="sxs-lookup"><span data-stu-id="e90d1-110">If the database is copied, it is automatically reattached at the source if the copy is successful.</span></span> <span data-ttu-id="e90d1-111">在脱机模式中，复制数据库的速度会快一些，但在传输过程中用户无法使用该数据库。</span><span class="sxs-lookup"><span data-stu-id="e90d1-111">In offline mode, the database is copied more quickly, but the database is unavailable to users during the transfer.</span></span>  
  
 <span data-ttu-id="e90d1-112">脱机模式要求您在源服务器和目标服务器上指定包含数据库文件的网络文件共享。</span><span class="sxs-lookup"><span data-stu-id="e90d1-112">Offline mode requires that you specify the network file shares on the source and destination servers that contain the database files.</span></span> <span data-ttu-id="e90d1-113">如果共享了该文件夹且用户可以访问它，则可以使用语法 \\\computername\Program Files\myfolder\\来引用该网络共享。</span><span class="sxs-lookup"><span data-stu-id="e90d1-113">If the folder is shared and can be accessed by the user, you can reference the network share using the syntax \\\computername\Program Files\myfolder\\.</span></span> <span data-ttu-id="e90d1-114">否则，必须使用语法 \\\computername\c$\Program Files\myfolder\\。</span><span class="sxs-lookup"><span data-stu-id="e90d1-114">Otherwise, you must use the syntax \\\computername\c$\Program Files\myfolder\\.</span></span> <span data-ttu-id="e90d1-115">若要使用后一种语法，用户必须对源和目标网络共享具有写权限。</span><span class="sxs-lookup"><span data-stu-id="e90d1-115">To use the latter syntax, the user must have write access to the source and destination network shares.</span></span>  
  
## <a name="transfer-of-databases-between-versions-of-sql-server"></a><span data-ttu-id="e90d1-116">在不同版本的 SQL Server 之间传输数据库</span><span class="sxs-lookup"><span data-stu-id="e90d1-116">Transfer of Databases Between Versions of SQL Server</span></span>  
 <span data-ttu-id="e90d1-117">传输数据库任务可在不同 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本的实例之间传输数据库。</span><span class="sxs-lookup"><span data-stu-id="e90d1-117">The Transfer Database task can transfer a database between instances of different [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions.</span></span>  
  
## <a name="events"></a><span data-ttu-id="e90d1-118">事件</span><span class="sxs-lookup"><span data-stu-id="e90d1-118">Events</span></span>  
 <span data-ttu-id="e90d1-119">传输数据库任务并不报告错误消息传输的进度，它仅报告 0% 和 100 % 完成。</span><span class="sxs-lookup"><span data-stu-id="e90d1-119">The Transfer Database task does not report incremental progress of the error message transfer; it reports only 0% and 100 % completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="e90d1-120">执行值</span><span class="sxs-lookup"><span data-stu-id="e90d1-120">Execution Value</span></span>  
 <span data-ttu-id="e90d1-121">在该任务的 `ExecutionValue` 属性中定义的执行值返回值 1，因为与其他传输任务相比，传输数据库任务只能传输一个数据库。</span><span class="sxs-lookup"><span data-stu-id="e90d1-121">The execution value, defined in the `ExecutionValue` property of the task, returns the value 1, because in contrast to other transfer tasks, the Transfer Database task can transfer only one database.</span></span>  
  
 <span data-ttu-id="e90d1-122">通过将用户定义变量分配给传输数据库任务的 `ExecValueVariable` 属性，包中的其他对象就可以访问有关错误消息传输的信息。</span><span class="sxs-lookup"><span data-stu-id="e90d1-122">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer Database task, information about the error message transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="e90d1-123">有关详细信息，请参阅 [Integration Services (SSIS) 变量](../integration-services-ssis-variables.md)和[在包中使用变量](../use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="e90d1-123">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="e90d1-124">日志项</span><span class="sxs-lookup"><span data-stu-id="e90d1-124">Log Entries</span></span>  
 <span data-ttu-id="e90d1-125">传输数据库任务包括下列自定义日志项：</span><span class="sxs-lookup"><span data-stu-id="e90d1-125">The Transfer Database task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="e90d1-126">SourceSQLServer   此日志项列出源服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="e90d1-126">SourceSQLServer    This log entry lists the name of the source server.</span></span>  
  
-   <span data-ttu-id="e90d1-127">DestSQLServer   此日志项列出目标服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="e90d1-127">DestSQLServer    This log entry lists the name of the destination server.</span></span>  
  
-   <span data-ttu-id="e90d1-128">SourceDB   此日志项列出已传输的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="e90d1-128">SourceDB    This log entry lists the name of the database that is transferred.</span></span>  
  
 <span data-ttu-id="e90d1-129">此外，在覆盖目标数据库时会写入 `OnInformation` 事件的日志项。</span><span class="sxs-lookup"><span data-stu-id="e90d1-129">In addition, a log entry for the `OnInformation` event is written when the destination database is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="e90d1-130">安全和权限</span><span class="sxs-lookup"><span data-stu-id="e90d1-130">Security and Permissions</span></span>  
 <span data-ttu-id="e90d1-131">若要使用脱机模式传输数据库，运行包的用户必须是 sysadmin 服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="e90d1-131">To transfer a database using offline mode, the user who runs the package must be a member of the sysadmin server role.</span></span>  
  
 <span data-ttu-id="e90d1-132">若要使用联机模式传输数据库，运行包的用户必须是 sysadmin 服务器角色的成员或所选数据库的数据库所有者 (dbo)。</span><span class="sxs-lookup"><span data-stu-id="e90d1-132">To transfer a database using online mode, the user who runs the package must be a member of the sysadmin server role or the database owner (dbo) of the selected database.</span></span>  
  
## <a name="configuration-of-the-transfer-database-task"></a><span data-ttu-id="e90d1-133">传输数据库任务的配置</span><span class="sxs-lookup"><span data-stu-id="e90d1-133">Configuration of the Transfer Database Task</span></span>  
 <span data-ttu-id="e90d1-134">您可以指定该任务是否在源数据库传输失败后尝试重新连接该数据库。</span><span class="sxs-lookup"><span data-stu-id="e90d1-134">You can specify whether the task tries to reattach the source database if the database transfer fails.</span></span>  
  
 <span data-ttu-id="e90d1-135">传输数据库任务还可以配置为允许覆盖同名的目标数据库，也就是替换目标数据库。</span><span class="sxs-lookup"><span data-stu-id="e90d1-135">The Transfer Database task can also be configured to permit overwriting a destination database that has the same name, replacing the destination database.</span></span>  
  
 <span data-ttu-id="e90d1-136">源数据库也可以在传输过程中重命名。</span><span class="sxs-lookup"><span data-stu-id="e90d1-136">The source database can also be renamed as part of the transfer process.</span></span> <span data-ttu-id="e90d1-137">如果要将数据库传输到已经包含同名数据库的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的目标实例，则可以重命名源数据库，以允许传输该数据库。</span><span class="sxs-lookup"><span data-stu-id="e90d1-137">If you want to transfer a database to a destination instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that already contains a database that has the same name, renaming the source database allows the database to be transferred.</span></span> <span data-ttu-id="e90d1-138">但是，数据库文件名也必须不同；如果同名数据库文件已经存在于目标实例上，则该任务将失败。</span><span class="sxs-lookup"><span data-stu-id="e90d1-138">However, the database file names must also be different; if database files that have the same names already exist at the destination, the task fails.</span></span>  
  
 <span data-ttu-id="e90d1-139">复制数据库时，数据库不能比目标服务器上的 **模型** 数据库小。</span><span class="sxs-lookup"><span data-stu-id="e90d1-139">When you copy a database, the database cannot be smaller than the size of the **model** database on the destination server.</span></span> <span data-ttu-id="e90d1-140">可以增加要复制的数据库的大小，也可以减小 **模型**数据库的大小。</span><span class="sxs-lookup"><span data-stu-id="e90d1-140">You can either increase the size of the database to copy, or reduce the size of **model**.</span></span>  
  
 <span data-ttu-id="e90d1-141">在运行时，传输数据库任务使用一个或多个 SMO 连接管理器连接到源服务器和目标服务器。</span><span class="sxs-lookup"><span data-stu-id="e90d1-141">At run time, the Transfer Database task connects to the source and destination servers by using one or two SMO connection managers.</span></span> <span data-ttu-id="e90d1-142">在同一服务器上创建数据库的副本时，只需要一个 SMO 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e90d1-142">When you create a copy of a database on the same server, only one SMO connection manager is required.</span></span> <span data-ttu-id="e90d1-143">SMO 连接管理器与传输数据库任务分开进行配置，然后在传输数据库任务中引用连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e90d1-143">The SMO connection managers are configured separately from the Transfer Database task, and then are referenced in the Transfer Database task.</span></span> <span data-ttu-id="e90d1-144">SMO 连接管理器指定在该任务访问服务器时使用的服务器和身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="e90d1-144">The SMO connection managers specify the server and the authentication mode to use when the task accesses the server.</span></span> <span data-ttu-id="e90d1-145">有关详细信息，请参阅 [SMO Connection Manager](../connection-manager/smo-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="e90d1-145">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
 <span data-ttu-id="e90d1-146">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="e90d1-146">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="e90d1-147">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="e90d1-147">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="e90d1-148">传输数据库任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="e90d1-148">Transfer Database Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="e90d1-149">传输数据库任务编辑器（“数据库”页）</span><span class="sxs-lookup"><span data-stu-id="e90d1-149">Transfer Database Task Editor &#40;Databases Page&#41;</span></span>](../transfer-database-task-editor-databases-page.md)  
  
-   [<span data-ttu-id="e90d1-150">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="e90d1-150">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="e90d1-151">有关如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="e90d1-151">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="e90d1-152">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="e90d1-152">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-transfer-database-task"></a><span data-ttu-id="e90d1-153">传输数据库任务的编程配置</span><span class="sxs-lookup"><span data-stu-id="e90d1-153">Programmatic Configuration of the Transfer Database Task</span></span>  
 <span data-ttu-id="e90d1-154">有关以编程方式设置这些属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="e90d1-154">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferDatabaseTask.TransferDatabaseTask>  
  
  
