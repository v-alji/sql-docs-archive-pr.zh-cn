---
title: 传输 SQL Server 对象任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfersqlserverobjectstask.f1
helpviewer_keywords:
- Transfer SQL Server Objects task [Integration Services]
ms.assetid: fe86d6e5-e415-406c-88f3-dc3ef71bd5f0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 281acb189e8f4dcfde9dc7ad1d2a74525236d28d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576903"
---
# <a name="transfer-sql-server-objects-task"></a><span data-ttu-id="f01b0-102">传输 SQL Server 对象任务</span><span class="sxs-lookup"><span data-stu-id="f01b0-102">Transfer SQL Server Objects Task</span></span>
  <span data-ttu-id="f01b0-103">传输 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象任务在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例之间传输 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库中一种或多种类型的对象。</span><span class="sxs-lookup"><span data-stu-id="f01b0-103">The Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task transfers one or more types of objects in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f01b0-104">例如，该任务可以复制表和存储过程。</span><span class="sxs-lookup"><span data-stu-id="f01b0-104">For example, the task can copy tables and stored procedures.</span></span> <span data-ttu-id="f01b0-105">可以复制的对象的类型会因用作源的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本而异。</span><span class="sxs-lookup"><span data-stu-id="f01b0-105">Depending on the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is used as a source, different types of objects are available to copy.</span></span> <span data-ttu-id="f01b0-106">例如，只有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库包括架构和用户定义聚合。</span><span class="sxs-lookup"><span data-stu-id="f01b0-106">For example, only a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database includes schemas and user-defined aggregates.</span></span>  
  
## <a name="objects-to-transfer"></a><span data-ttu-id="f01b0-107">要传输的对象</span><span class="sxs-lookup"><span data-stu-id="f01b0-107">Objects to Transfer</span></span>  
 <span data-ttu-id="f01b0-108">可以复制指定数据库中的服务器角色、角色和用户以及这些传输的对象的权限。</span><span class="sxs-lookup"><span data-stu-id="f01b0-108">Server roles, roles, and users from the specified database can be copied, as well as the permissions for the transferred objects.</span></span> <span data-ttu-id="f01b0-109">通过随对象一起复制关联的用户、角色以及权限，您可以立即在目标服务器上对这些传输的对象进行操作。</span><span class="sxs-lookup"><span data-stu-id="f01b0-109">By copying the associated users, roles, and permissions together with the objects, you can make the transferred objects immediately operable on the destination server.</span></span>  
  
 <span data-ttu-id="f01b0-110">下表列出了可以复制的对象的类型。</span><span class="sxs-lookup"><span data-stu-id="f01b0-110">The following table lists the type of objects that can be copied.</span></span>  
  
|<span data-ttu-id="f01b0-111">Object</span><span class="sxs-lookup"><span data-stu-id="f01b0-111">Object</span></span>|  
|------------|  
|<span data-ttu-id="f01b0-112">表</span><span class="sxs-lookup"><span data-stu-id="f01b0-112">Tables</span></span>|  
|<span data-ttu-id="f01b0-113">视图</span><span class="sxs-lookup"><span data-stu-id="f01b0-113">Views</span></span>|  
|<span data-ttu-id="f01b0-114">存储过程</span><span class="sxs-lookup"><span data-stu-id="f01b0-114">Stored Procedures</span></span>|  
|<span data-ttu-id="f01b0-115">用户定义函数</span><span class="sxs-lookup"><span data-stu-id="f01b0-115">User-Defined Functions</span></span>|  
|<span data-ttu-id="f01b0-116">默认值</span><span class="sxs-lookup"><span data-stu-id="f01b0-116">Defaults</span></span>|  
|<span data-ttu-id="f01b0-117">用户定义数据类型</span><span class="sxs-lookup"><span data-stu-id="f01b0-117">User-Defined Data Types</span></span>|  
|<span data-ttu-id="f01b0-118">分区函数</span><span class="sxs-lookup"><span data-stu-id="f01b0-118">Partition Functions</span></span>|  
|<span data-ttu-id="f01b0-119">分区方案</span><span class="sxs-lookup"><span data-stu-id="f01b0-119">Partition Schemes</span></span>|  
|<span data-ttu-id="f01b0-120">架构</span><span class="sxs-lookup"><span data-stu-id="f01b0-120">Schemas</span></span>|  
|<span data-ttu-id="f01b0-121">程序集</span><span class="sxs-lookup"><span data-stu-id="f01b0-121">Assemblies</span></span>|  
|<span data-ttu-id="f01b0-122">用户定义聚合</span><span class="sxs-lookup"><span data-stu-id="f01b0-122">User-Defined Aggregates</span></span>|  
|<span data-ttu-id="f01b0-123">用户定义类型</span><span class="sxs-lookup"><span data-stu-id="f01b0-123">User-Defined Types</span></span>|  
|<span data-ttu-id="f01b0-124">XML 架构集合</span><span class="sxs-lookup"><span data-stu-id="f01b0-124">XML Schema Collection</span></span>|  
  
 <span data-ttu-id="f01b0-125">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例中创建的用户定义类型 (UDT) 对公共语言运行时 (CLR) 程序集具有依赖关系。</span><span class="sxs-lookup"><span data-stu-id="f01b0-125">User-defined types (UDTs) that were created in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] have dependencies on common language runtime (CLR) assemblies.</span></span> <span data-ttu-id="f01b0-126">如果使用传输 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象任务来传输 UDT，则还必须配置用于传输依赖对象的任务。</span><span class="sxs-lookup"><span data-stu-id="f01b0-126">If you use the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task to transfer UDTs, you must also configure the task to transfer dependent objects.</span></span> <span data-ttu-id="f01b0-127">若要传输依赖对象，请将 `IncludeDependentObjects` 属性设为 `True`。</span><span class="sxs-lookup"><span data-stu-id="f01b0-127">To transfer dependent objects, set the `IncludeDependentObjects` property to `True`.</span></span>  
  
### <a name="table-options"></a><span data-ttu-id="f01b0-128">表选项</span><span class="sxs-lookup"><span data-stu-id="f01b0-128">Table Options</span></span>  
 <span data-ttu-id="f01b0-129">在复制表时，可以指示在复制过程中要包含的与表相关的项的类型。</span><span class="sxs-lookup"><span data-stu-id="f01b0-129">When copying tables, you can indicate the types of table-related items to include in the copy process.</span></span> <span data-ttu-id="f01b0-130">以下类型的项可以与相关表一起复制：</span><span class="sxs-lookup"><span data-stu-id="f01b0-130">The following types of items can be copied together with the related table:</span></span>  
  
-   <span data-ttu-id="f01b0-131">索引</span><span class="sxs-lookup"><span data-stu-id="f01b0-131">Indexes</span></span>  
  
-   <span data-ttu-id="f01b0-132">触发器</span><span class="sxs-lookup"><span data-stu-id="f01b0-132">Triggers</span></span>  
  
-   <span data-ttu-id="f01b0-133">全文索引</span><span class="sxs-lookup"><span data-stu-id="f01b0-133">Full-text indexes</span></span>  
  
-   <span data-ttu-id="f01b0-134">主键</span><span class="sxs-lookup"><span data-stu-id="f01b0-134">Primary keys</span></span>  
  
-   <span data-ttu-id="f01b0-135">外键</span><span class="sxs-lookup"><span data-stu-id="f01b0-135">Foreign keys</span></span>  
  
 <span data-ttu-id="f01b0-136">您还可以指示该任务所生成的脚本是否为 Unicode 格式。</span><span class="sxs-lookup"><span data-stu-id="f01b0-136">You can also indicate whether the script that the task generates is in Unicode format.</span></span>  
  
## <a name="destination-options"></a><span data-ttu-id="f01b0-137">目标选项</span><span class="sxs-lookup"><span data-stu-id="f01b0-137">Destination Options</span></span>  
 <span data-ttu-id="f01b0-138">您可以将传输 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象任务配置为在传输时包括架构名称、数据、所传输的对象的扩展属性以及依赖对象。</span><span class="sxs-lookup"><span data-stu-id="f01b0-138">You can configure the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task to include schema names, data, extended properties of transferred objects, and dependent objects in the transfer.</span></span> <span data-ttu-id="f01b0-139">如果复制数据，则它可以替换或追加到现有数据。</span><span class="sxs-lookup"><span data-stu-id="f01b0-139">If data is copied, it can replace or append existing data.</span></span>  
  
 <span data-ttu-id="f01b0-140">某些选项只适用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f01b0-140">Some options apply only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f01b0-141">例如，只有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持架构。</span><span class="sxs-lookup"><span data-stu-id="f01b0-141">For example, only [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supports schemas.</span></span>  
  
## <a name="security-options"></a><span data-ttu-id="f01b0-142">安全选项</span><span class="sxs-lookup"><span data-stu-id="f01b0-142">Security Options</span></span>  
 <span data-ttu-id="f01b0-143">传输 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象任务可以包括通过所传输的对象的源、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名和权限所产生的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库级用户和角色。</span><span class="sxs-lookup"><span data-stu-id="f01b0-143">The Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task can include [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database-level users and roles from the source, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins, and the permissions for transferred objects.</span></span> <span data-ttu-id="f01b0-144">例如，传输可以包括所传输的表的权限。</span><span class="sxs-lookup"><span data-stu-id="f01b0-144">For example, the transfer can include the permissions on the transferred tables.</span></span>  
  
## <a name="transfer-objects-between-instances-of-sql-server"></a><span data-ttu-id="f01b0-145">在 SQL Server 实例之间传输对象</span><span class="sxs-lookup"><span data-stu-id="f01b0-145">Transfer Objects Between Instances of SQL Server</span></span>  
 <span data-ttu-id="f01b0-146">传输 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象任务支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 源和目标。</span><span class="sxs-lookup"><span data-stu-id="f01b0-146">The Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task supports a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source and destination.</span></span>  
  
## <a name="events"></a><span data-ttu-id="f01b0-147">事件</span><span class="sxs-lookup"><span data-stu-id="f01b0-147">Events</span></span>  
 <span data-ttu-id="f01b0-148">该任务将引发报告已传输的对象的信息事件，而且在覆盖对象时还会引发警告事件。</span><span class="sxs-lookup"><span data-stu-id="f01b0-148">The task raises an information event that reports the object transferred and a warning event when an object is overwritten.</span></span> <span data-ttu-id="f01b0-149">信息事件还可以由截断数据库表这样的操作引发。</span><span class="sxs-lookup"><span data-stu-id="f01b0-149">An information event is also raised for actions such as the truncation of database tables.</span></span>  
  
 <span data-ttu-id="f01b0-150">传输 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象任务并不报告对象传输的进度；它仅报告 0% 和 100 % 完成。</span><span class="sxs-lookup"><span data-stu-id="f01b0-150">The Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task does not report incremental progress of the object transfer; it reports only 0% and 100 % completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="f01b0-151">执行值</span><span class="sxs-lookup"><span data-stu-id="f01b0-151">Execution Value</span></span>  
 <span data-ttu-id="f01b0-152">在任务的 `ExecutionValue` 属性中存储的执行值返回已传输的对象数。</span><span class="sxs-lookup"><span data-stu-id="f01b0-152">The execution value, stored in the `ExecutionValue` property of the task, returns the number of objects transferred.</span></span> <span data-ttu-id="f01b0-153">通过将用户定义的变量分配给传输 SQL Server 对象任务的 `ExecValueVariable` 属性，包中的其他对象就可以访问有关对象传输的信息。</span><span class="sxs-lookup"><span data-stu-id="f01b0-153">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer SQL Server Objects task, information about the object transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="f01b0-154">有关详细信息，请参阅 [Integration Services (SSIS) 变量](../integration-services-ssis-variables.md)和[在包中使用变量](../use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="f01b0-154">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="f01b0-155">日志项</span><span class="sxs-lookup"><span data-stu-id="f01b0-155">Log Entries</span></span>  
 <span data-ttu-id="f01b0-156">传输 SQL Server 对象任务包括下列自定义日志项：</span><span class="sxs-lookup"><span data-stu-id="f01b0-156">The Transfer SQL Server Objects task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="f01b0-157">TransferSqlServerObjectsTaskStartTransferringObjects   此日志项报告传输已经开始。</span><span class="sxs-lookup"><span data-stu-id="f01b0-157">TransferSqlServerObjectsTaskStartTransferringObjects   This log entry reports that the transfer has started.</span></span> <span data-ttu-id="f01b0-158">日志项包括开始时间。</span><span class="sxs-lookup"><span data-stu-id="f01b0-158">The log entry includes the start time.</span></span>  
  
-   <span data-ttu-id="f01b0-159">TransferSqlServerObjectsTaskFinishedTransferringObjects    此日志项报告传输已经完成。</span><span class="sxs-lookup"><span data-stu-id="f01b0-159">TransferSqlServerObjectsTaskFinishedTransferringObjects    This log entry reports that the transfer has completed.</span></span> <span data-ttu-id="f01b0-160">日志项包括结束时间。</span><span class="sxs-lookup"><span data-stu-id="f01b0-160">The log entry includes the end time.</span></span>  
  
 <span data-ttu-id="f01b0-161">此外，`OnInformation` 事件的日志项报告属于为传输所选的对象类型的对象数、已经传输的对象数以及随表传输数据时截断表这样的操作。</span><span class="sxs-lookup"><span data-stu-id="f01b0-161">In addition, a log entry for an `OnInformation` event reports the number of objects of the object types that have been selected for transfer, the number of objects that were transferred, and actions such as the truncation of tables when data is transferred with tables.</span></span> <span data-ttu-id="f01b0-162">当覆盖目标上的每个对象时，都会写入 `OnWarning` 事件的日志项。</span><span class="sxs-lookup"><span data-stu-id="f01b0-162">A log entry for the `OnWarning` event is written for each object on the destination that is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="f01b0-163">安全和权限</span><span class="sxs-lookup"><span data-stu-id="f01b0-163">Security and Permissions</span></span>  
 <span data-ttu-id="f01b0-164">用户必须具有浏览源服务器上的对象的权限，同时必须具有在目标服务器上删除和创建对象的权限，此外用户还必须具有访问指定数据库和数据库对象的权限。</span><span class="sxs-lookup"><span data-stu-id="f01b0-164">The user must have permission to browse objects on the source server, and must have permission to drop and create objects on the destination server; moreover, the user must have access to the specified database and database objects.</span></span>  
  
## <a name="configuration-of-the-transfer-sql-server-objects-task"></a><span data-ttu-id="f01b0-165">配置传输 SQL Server 对象任务</span><span class="sxs-lookup"><span data-stu-id="f01b0-165">Configuration of the Transfer SQL Server Objects Task</span></span>  
 <span data-ttu-id="f01b0-166">传输 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象任务可以配置为传输所有对象，传输某种类型的所有对象，或者只传输某种类型的指定对象。</span><span class="sxs-lookup"><span data-stu-id="f01b0-166">The Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task can be configured to transfer all objects, all objects of a type, or only specified objects of a type.</span></span> <span data-ttu-id="f01b0-167">例如，可以选择只复制 AdventureWorks 数据库中的选定表。</span><span class="sxs-lookup"><span data-stu-id="f01b0-167">For example, you can choose to copy only selected tables in the AdventureWorks database.</span></span>  
  
 <span data-ttu-id="f01b0-168">如果传输 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象任务传输表，可指定随表一起复制、与表相关的对象的类型。</span><span class="sxs-lookup"><span data-stu-id="f01b0-168">If the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task transfers tables, you can specify the types of table-related objects to copy with the tables.</span></span> <span data-ttu-id="f01b0-169">例如，您可以指定随表一起复制主键。</span><span class="sxs-lookup"><span data-stu-id="f01b0-169">For example, you can specify that primary keys are copied with tables.</span></span>  
  
 <span data-ttu-id="f01b0-170">若要进一步增强所传输的对象的功能，您可以将传输 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象任务配置为在传输时包括架构名称、数据、所传输的对象的扩展属性以及依赖对象。</span><span class="sxs-lookup"><span data-stu-id="f01b0-170">To further enhance functionality of transferred objects, you can configure the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task to include schema names, data, extended properties of transferred objects, and dependent objects in the transfer.</span></span> <span data-ttu-id="f01b0-171">在复制数据时，您可以指定是替换现有数据还是追加到现有数据。</span><span class="sxs-lookup"><span data-stu-id="f01b0-171">When copying data, you can specify whether to replace or append existing data.</span></span>  
  
 <span data-ttu-id="f01b0-172">运行时，传输 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象任务使用两个 SMO 连接管理器连接到源服务器和目标服务器。</span><span class="sxs-lookup"><span data-stu-id="f01b0-172">At run time, the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task connects to the source and destination servers by using two SMO connection managers.</span></span> <span data-ttu-id="f01b0-173">这两个 SMO 连接管理器与传输 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象任务分开配置，然后由传输 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象任务引用。</span><span class="sxs-lookup"><span data-stu-id="f01b0-173">The SMO connection managers are configured separately from the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task, and then referenced in the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task.</span></span> <span data-ttu-id="f01b0-174">SMO 连接管理器指定服务器以及在访问该服务器时要使用的身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="f01b0-174">The SMO connection managers specify the server and the authentication mode to use when accessing the server.</span></span> <span data-ttu-id="f01b0-175">有关详细信息，请参阅 [SMO Connection Manager](../connection-manager/smo-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="f01b0-175">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
 <span data-ttu-id="f01b0-176">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="f01b0-176">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="f01b0-177">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="f01b0-177">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="f01b0-178">传输 SQL Server 对象任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="f01b0-178">Transfer SQL Server Objects Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="f01b0-179">传输 SQL Server 对象任务编辑器（“对象”页）</span><span class="sxs-lookup"><span data-stu-id="f01b0-179">Transfer SQL Server Objects Task Editor &#40;Objects Page&#41;</span></span>](../transfer-sql-server-objects-task-editor-objects-page.md)  
  
-   [<span data-ttu-id="f01b0-180">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="f01b0-180">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="f01b0-181">有关如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="f01b0-181">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="f01b0-182">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="f01b0-182">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-transfer-sql-server-objects-task"></a><span data-ttu-id="f01b0-183">以编程方式配置传输 SQL Server 对象任务</span><span class="sxs-lookup"><span data-stu-id="f01b0-183">Programmatic Configuration of the Transfer SQL Server Objects Task</span></span>  
 <span data-ttu-id="f01b0-184">有关以编程方式设置这些属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="f01b0-184">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferSqlServerObjectsTask.TransferSqlServerObjectsTask>  
  
  
