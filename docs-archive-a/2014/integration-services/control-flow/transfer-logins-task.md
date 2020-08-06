---
title: 传输登录名任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferloginstask.f1
helpviewer_keywords:
- Transfer Logins task [Integration Services]
ms.assetid: 1df60fd6-c019-405d-8155-c330dbac2cc1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d42d39b6cc7c2f350e3e3adc774be23934981369
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576910"
---
# <a name="transfer-logins-task"></a><span data-ttu-id="9935e-102">传输登录名任务</span><span class="sxs-lookup"><span data-stu-id="9935e-102">Transfer Logins Task</span></span>
  <span data-ttu-id="9935e-103">传输登录名任务在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例之间传输一个或多个登录名。</span><span class="sxs-lookup"><span data-stu-id="9935e-103">The Transfer Logins task transfers one or more logins between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="transfer-logins-between-instances-of-sql-server"></a><span data-ttu-id="9935e-104">在 SQL Server 实例之间传输登录名</span><span class="sxs-lookup"><span data-stu-id="9935e-104">Transfer Logins Between Instances of SQL Server</span></span>  
 <span data-ttu-id="9935e-105">传输登录名任务支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 源和目标。</span><span class="sxs-lookup"><span data-stu-id="9935e-105">The Transfer Logins task supports a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source and destination.</span></span>  
  
## <a name="events"></a><span data-ttu-id="9935e-106">事件</span><span class="sxs-lookup"><span data-stu-id="9935e-106">Events</span></span>  
 <span data-ttu-id="9935e-107">该任务将引发报告已传输的登录名数的信息事件，而且在覆盖登录名时还会引发警告事件。</span><span class="sxs-lookup"><span data-stu-id="9935e-107">The task raises an information event that reports the number of logins transferred and a warning event when a login is overwritten.</span></span>  
  
 <span data-ttu-id="9935e-108">传输登录名任务并不报告登录名传输的进度，它仅报告 0% 和 100 % 完成。</span><span class="sxs-lookup"><span data-stu-id="9935e-108">The Transfer Logins task does not report incremental progress of the login transfer; it reports only 0% and 100 % completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="9935e-109">执行值</span><span class="sxs-lookup"><span data-stu-id="9935e-109">Execution Value</span></span>  
 <span data-ttu-id="9935e-110">在该任务的 `ExecutionValue` 属性中定义的执行值返回已传输的登录名数。</span><span class="sxs-lookup"><span data-stu-id="9935e-110">The execution value, defined in the `ExecutionValue` property of the task, returns the number of logins transferred.</span></span> <span data-ttu-id="9935e-111">通过将用户定义的变量分配给传输登录名任务的 `ExecValueVariable` 属性，包中的其他对象就可以访问有关登录名传输的信息。</span><span class="sxs-lookup"><span data-stu-id="9935e-111">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer Logins task, information about the login transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="9935e-112">有关详细信息，请参阅 [Integration Services (SSIS) 变量](../integration-services-ssis-variables.md)和[在包中使用变量](../use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="9935e-112">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="9935e-113">日志项</span><span class="sxs-lookup"><span data-stu-id="9935e-113">Log Entries</span></span>  
 <span data-ttu-id="9935e-114">传输登录名任务包括下列自定义日志项：</span><span class="sxs-lookup"><span data-stu-id="9935e-114">The Transfer Logins task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="9935e-115">TransferLoginsTaskStarTransferringObjects   此日志项报告传输已经开始。</span><span class="sxs-lookup"><span data-stu-id="9935e-115">TransferLoginsTaskStarTransferringObjects    This log entry reports the transfer has started.</span></span> <span data-ttu-id="9935e-116">日志项包括开始时间。</span><span class="sxs-lookup"><span data-stu-id="9935e-116">The log entry includes the start time.</span></span>  
  
-   <span data-ttu-id="9935e-117">TransferLoginsTaskFinishedTransferringObjects   此日志项报告传输已经完成。</span><span class="sxs-lookup"><span data-stu-id="9935e-117">TransferLoginsTaskFinishedTransferringObjects   This log entry reports the transfer has completed.</span></span> <span data-ttu-id="9935e-118">日志项包括结束时间。</span><span class="sxs-lookup"><span data-stu-id="9935e-118">The log entry includes the end time.</span></span>  
  
 <span data-ttu-id="9935e-119">此外，还有 `OnInformation` 事件的日志项（报告已传输的登录名数），以及 `OnWarning` 事件的日志项（是为目标服务器上每个被覆盖的登录名写入的）。</span><span class="sxs-lookup"><span data-stu-id="9935e-119">In addition, a log entry for the `OnInformation` event reports the number of logins that were transferred, and a log entry for the `OnWarning` event is written for each login on the destination that is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="9935e-120">安全和权限</span><span class="sxs-lookup"><span data-stu-id="9935e-120">Security and Permissions</span></span>  
 <span data-ttu-id="9935e-121">若要浏览源服务器上的登录名并在目标服务器上创建登录名，用户必须同时是这两台服务器上 sysadmin 服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="9935e-121">To browse logins on the source server and to create logins on the destination server, the user must be a member of the sysadmin server role on both servers.</span></span>  
  
## <a name="configuration-of-the-transfer-logins-task"></a><span data-ttu-id="9935e-122">传输登录名任务的配置</span><span class="sxs-lookup"><span data-stu-id="9935e-122">Configuration of the Transfer Logins Task</span></span>  
 <span data-ttu-id="9935e-123">传输登录名任务可以配置为传输所有登录名，只传输指定登录名，或者只传输对指定的数据库具有访问权限的所有登录名。</span><span class="sxs-lookup"><span data-stu-id="9935e-123">The Transfer Logins task can be configured to transfer all logins, only specified logins, or all logins that have access to specified databases only.</span></span> <span data-ttu-id="9935e-124">无法传输 sa 登录名。</span><span class="sxs-lookup"><span data-stu-id="9935e-124">The sa login cannot be transferred.</span></span> <span data-ttu-id="9935e-125">可以重命名 sa 登录名；但是，无法传输重命名的 sa 登录名。</span><span class="sxs-lookup"><span data-stu-id="9935e-125">The sa login may be renamed; however, the renamed sa login cannot be transferred either.</span></span>  
  
 <span data-ttu-id="9935e-126">您还可以指示该任务是否复制与登录名关联的安全标识符 (SID)。</span><span class="sxs-lookup"><span data-stu-id="9935e-126">You can also indicate whether the task copies the security identifiers (SIDs) associated with the logins.</span></span> <span data-ttu-id="9935e-127">如果传输登录名任务与传输数据库任务结合使用，则必须将 SID 复制到目标数据库，否则目标数据库将无法识别所传输的登录名。</span><span class="sxs-lookup"><span data-stu-id="9935e-127">If the Transfer Logins task is used in conjunction with the Transfer Database task the SIDs must be copied to the destination; otherwise, the transferred logins are not recognized by the destination database.</span></span>  
  
 <span data-ttu-id="9935e-128">在目标服务器上，所传输的登录名将被禁用，而且将分配给它们随机的密码。</span><span class="sxs-lookup"><span data-stu-id="9935e-128">At the destination, the transferred logins are disabled and assigned random passwords.</span></span> <span data-ttu-id="9935e-129">目标服务器上 sysadmin 角色的成员必须更改这些密码并启用这些登录名，才能使用这些登录名。</span><span class="sxs-lookup"><span data-stu-id="9935e-129">A member of the sysadmin role on the destination server must change the passwords and enable the logins before the logins can be used.</span></span>  
  
 <span data-ttu-id="9935e-130">要传输的登录名可能已经存在于目标服务器上。</span><span class="sxs-lookup"><span data-stu-id="9935e-130">The logins to be transferred may already exist on the destination.</span></span> <span data-ttu-id="9935e-131">传输登录名任务可以配置为以下列方式处理现有登录名：</span><span class="sxs-lookup"><span data-stu-id="9935e-131">The Transfer Logins task can be configured to handle existing logins in the following ways:</span></span>  
  
-   <span data-ttu-id="9935e-132">覆盖现有登录名。</span><span class="sxs-lookup"><span data-stu-id="9935e-132">Overwrite existing logins.</span></span>  
  
-   <span data-ttu-id="9935e-133">如果存在重复登录名，则该任务失败。</span><span class="sxs-lookup"><span data-stu-id="9935e-133">Fail the task when duplicate logins exist.</span></span>  
  
-   <span data-ttu-id="9935e-134">跳过重复登录名。</span><span class="sxs-lookup"><span data-stu-id="9935e-134">Skip duplicate logins.</span></span>  
  
 <span data-ttu-id="9935e-135">在运行时，传输登录名任务使用两个 SMO 连接管理器连接到源服务器和目标服务器。</span><span class="sxs-lookup"><span data-stu-id="9935e-135">At run time, the Transfer Logins task connects to the source and destination servers by using two SMO connection managers.</span></span> <span data-ttu-id="9935e-136">SMO 连接管理器与传输登录名任务分开进行配置，然后在传输登录名任务中引用连接管理器。</span><span class="sxs-lookup"><span data-stu-id="9935e-136">The SMO connection managers are configured separately from the Transfer Logins task, and then referenced in the Transfer Logins task.</span></span> <span data-ttu-id="9935e-137">SMO 连接管理器指定服务器以及在访问该服务器时要使用的身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="9935e-137">The SMO connection managers specify the server and the authentication mode to use when accessing the server.</span></span> <span data-ttu-id="9935e-138">有关详细信息，请参阅 [SMO Connection Manager](../connection-manager/smo-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="9935e-138">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
 <span data-ttu-id="9935e-139">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="9935e-139">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="9935e-140">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="9935e-140">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="9935e-141">传输登录名任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="9935e-141">Transfer Logins Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="9935e-142">传输登录名任务编辑器（“登录名”页）</span><span class="sxs-lookup"><span data-stu-id="9935e-142">Transfer Logins Task Editor &#40;Logins Page&#41;</span></span>](../transfer-logins-task-editor-logins-page.md)  
  
-   [<span data-ttu-id="9935e-143">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="9935e-143">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="9935e-144">有关如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="9935e-144">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="9935e-145">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="9935e-145">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-transfer-logins-task"></a><span data-ttu-id="9935e-146">传输登录名任务的编程配置</span><span class="sxs-lookup"><span data-stu-id="9935e-146">Programmatic Configuration of the Transfer Logins Task</span></span>  
 <span data-ttu-id="9935e-147">有关以编程方式设置这些属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="9935e-147">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferLoginsTask.TransferLoginsTask>  
  
  
