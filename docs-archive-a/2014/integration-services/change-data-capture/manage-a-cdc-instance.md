---
title: 管理 CDC 实例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- manIns
ms.assetid: cfed22c8-c666-40ca-9e73-24d93e85ba92
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9b8d750c417cf5efda3f0d376151c30b6da1eb3b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579704"
---
# <a name="manage-a-cdc-instance"></a><span data-ttu-id="e3ca5-102">管理 CDC 实例</span><span class="sxs-lookup"><span data-stu-id="e3ca5-102">Manage a CDC Instance</span></span>
  <span data-ttu-id="e3ca5-103">您可以使用 CDC 设计器控制台查看与您创建的实例有关的信息，以及管理实例操作。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-103">You can use the CDC Designer Console to view information about the instances that you create and to manage the operation of the instances.</span></span>  
  
 <span data-ttu-id="e3ca5-104">在左侧窗格中单击某一实例的名称可查看与该实例有关的信息。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-104">Click on the name of an instance in the left pane to view the information about the instance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e3ca5-105">如果您在左侧窗格中选择某一服务，则可用实例的列表也会显示在 CDC 设计器控制台的中央。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-105">If you select a service in the left pane, the list of available instances is also displayed in the center of the CDC Designer Console.</span></span> <span data-ttu-id="e3ca5-106">如果您在该部分中选择某一实例，则可以在右侧窗格中执行任务；但是，您将不能在属性选项卡中查看信息。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-106">If you select one of the instances in this section, you can carry out the tasks in the right pane; however, you will not be able to view the information in the property tabs.</span></span>  
  
## <a name="what-you-can-do-when-you-display-the-cdc-instance-information"></a><span data-ttu-id="e3ca5-107">在显示 CDC 实例信息时您可以执行的操作</span><span class="sxs-lookup"><span data-stu-id="e3ca5-107">What you can do when you display the CDC Instance information</span></span>  
 <span data-ttu-id="e3ca5-108">从右窗格中执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="e3ca5-108">The following actions are carried out from the right pane:</span></span>  
  
 <span data-ttu-id="e3ca5-109">**启动**</span><span class="sxs-lookup"><span data-stu-id="e3ca5-109">**Start**</span></span>  
 <span data-ttu-id="e3ca5-110">单击“开始”  可为所选的 CDC 实例开始捕获更改。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-110">Click **Start** to start the capturing changes for the selected CDC instance.</span></span>  
  
 <span data-ttu-id="e3ca5-111">**Stop**</span><span class="sxs-lookup"><span data-stu-id="e3ca5-111">**Stop**</span></span>  
 <span data-ttu-id="e3ca5-112">单击“停止”  可为所选的 CDC 实例停止捕获更改。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-112">Click **Stop** to stop capturing changes for the selected CDC instance.</span></span> <span data-ttu-id="e3ca5-113">在您停止该 CDC 实例时，在该时间点前已捕获的更改将不会丢失，并且这些更改将在恢复该 CDC 实例时提供。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-113">When you stop the CDC instance, the changes that were captured to that point are not lost and are delivered when the CDC instance is resumed.</span></span>  
  
 <span data-ttu-id="e3ca5-114">**重置**</span><span class="sxs-lookup"><span data-stu-id="e3ca5-114">**Reset**</span></span>  
 <span data-ttu-id="e3ca5-115">单击“重置”  可将 CDC 实例重置为其初始（空）状态。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-115">Click **Reset** to reset the CDC instance to its initial (empty) state.</span></span> <span data-ttu-id="e3ca5-116">此选项在 CDC 实例停止后可用。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-116">This option is available when the CDC instance is stopped.</span></span> <span data-ttu-id="e3ca5-117">更改表中的所有更改以及 CDC 实例内部状态将被删除。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-117">All changes in the change tables and the CDC instance internal state are deleted.</span></span> <span data-ttu-id="e3ca5-118">当 CDC 实例在以后启动时，变更捕获将从该时间点开始，并且仅包含在 CDC 实例启动后开始的事务。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-118">When the CDC instance is started later, the change capture starts from that point in time and only includes transactions that started after the CDC instance started.</span></span>  
  
 <span data-ttu-id="e3ca5-119">在确认对话框中单击 **“确定”** ，以便确认您要重置 CDC 实例并且删除写入更改表的更改。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-119">Click **OK** in the confirmation dialog box to confirm that you want to reset the CDC instance and delete the changes written to the change tables.</span></span>  
  
 <span data-ttu-id="e3ca5-120">**删除**</span><span class="sxs-lookup"><span data-stu-id="e3ca5-120">**Delete**</span></span>  
 <span data-ttu-id="e3ca5-121">单击“删除”  可永久删除 CDC 实例。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-121">Click **Delete** to delete the CDC instance permanently.</span></span> <span data-ttu-id="e3ca5-122">此选项仅在 CDC 实例停止后可用。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-122">This option is available only when the CDC instance is stopped.</span></span>  
  
 <span data-ttu-id="e3ca5-123">在确认对话框中单击 **“确定”** ，以便确认您要删除 CDC 实例。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-123">Click **OK** in the confirmation dialog box to confirm that you want to delete the CDC instance.</span></span>  
  
 <span data-ttu-id="e3ca5-124">**Oracle 日志记录脚本**</span><span class="sxs-lookup"><span data-stu-id="e3ca5-124">**Oracle Logging Script**</span></span>  
 <span data-ttu-id="e3ca5-125">单击此链接将显示具有 Oracle 补充日志记录脚本的“Oracle 日志记录脚本”对话框。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-125">Click this link to display the Oracle Logging script dialog box with the Oracle supplemental-logging script.</span></span> <span data-ttu-id="e3ca5-126">有关可以在此对话框中执行的操作的信息，请参阅 [Oracle Supplemental Logging Script](oracle-supplemental-logging-script.md)。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-126">For information on what you can do in this dialog box, see [Oracle Supplemental Logging Script](oracle-supplemental-logging-script.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e3ca5-127">在您运行补充日志记录脚本时，“用于运行脚本的 Oracle 凭据”对话框将打开，您可以在其中提供有效的 Oracle 用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-127">When you run the supplemental logging scripts, the Oracle Credentials for Running Script dialog box opens where you provide a valid Oracle user name and password.</span></span> <span data-ttu-id="e3ca5-128">有关如何提供适当的 Oracle 凭据的信息，请参阅 [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md)。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-128">For information on how to provide the proper Oracle credentials, see [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md).</span></span>  
  
 <span data-ttu-id="e3ca5-129">**CDC 实例部署脚本**</span><span class="sxs-lookup"><span data-stu-id="e3ca5-129">**CDC Instance Deployment Script**</span></span>  
 <span data-ttu-id="e3ca5-130">单击此链接可显示 CDC 实例部署脚本的“CDC 实例部署脚本”对话框。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-130">Click this link to display the CDC Instance Deployment Script dialog box that displays the CDC instance deployment script.</span></span> <span data-ttu-id="e3ca5-131">有关此对话框的信息，请参阅 [CDC Instance Deployment Script](cdc-instance-deployment-script.md)。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-131">For information about this dialog box, see [CDC Instance Deployment Script](cdc-instance-deployment-script.md).</span></span>  
  
 <span data-ttu-id="e3ca5-132">**属性**</span><span class="sxs-lookup"><span data-stu-id="e3ca5-132">**Properties**</span></span>  
 <span data-ttu-id="e3ca5-133">单击此链接可打开属性编辑器。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-133">Click this link to open the property editor.</span></span> <span data-ttu-id="e3ca5-134">您使用属性编辑器编辑 CDC 实例配置。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-134">You edit the CDC instance configuration using the property editor.</span></span> <span data-ttu-id="e3ca5-135">有关编辑 CDC 实例属性的详细信息，请参阅 [Edit Instance Properties](edit-instance-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-135">For more information about editing the properties for a CDC instance, see [Edit Instance Properties](edit-instance-properties.md).</span></span>  
  
 <span data-ttu-id="e3ca5-136">**查看器的选项卡**</span><span class="sxs-lookup"><span data-stu-id="e3ca5-136">**Viewer Tabs**</span></span>  
  
 <span data-ttu-id="e3ca5-137">在您查看 CDC 实例的信息时，以下查看器选项卡可用。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-137">The following Viewer tabs are available when you view information for the CDC instance.</span></span> <span data-ttu-id="e3ca5-138">这些选项卡中的信息是只读的。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-138">The information in these tabs is read only.</span></span>  
  
 <span data-ttu-id="e3ca5-139">**Status**</span><span class="sxs-lookup"><span data-stu-id="e3ca5-139">**Status**</span></span>  
 <span data-ttu-id="e3ca5-140">此选项卡提供有关 CDC 实例的当前状态的信息和统计信息。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-140">This tab provides information and statistics about the CDC instance current status.</span></span> <span data-ttu-id="e3ca5-141">其中包含以下信息。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-141">It contains the following information.</span></span>  
  
-   <span data-ttu-id="e3ca5-142">**状态**：一个指示 CDC 实例的当前状态的图标。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-142">**Status**: An icon that indicates the current status for the CDC instance.</span></span> <span data-ttu-id="e3ca5-143">下面将介绍这些状态。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-143">The following describes the statuses.</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="e3ca5-144">![错误](../media/error.gif "错误")</span><span class="sxs-lookup"><span data-stu-id="e3ca5-144">![Error](../media/error.gif "Error")</span></span>|<span data-ttu-id="e3ca5-145">**错误**。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-145">**Error**.</span></span> <span data-ttu-id="e3ca5-146">Oracle CDC 实例因为发生了不可重试的错误而未运行。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-146">The Oracle CDC Instance is not running because a non-retryable error occurred.</span></span> <span data-ttu-id="e3ca5-147">以下子状态可用：</span><span class="sxs-lookup"><span data-stu-id="e3ca5-147">The following sub-statuses are available:</span></span><br /><br /> <span data-ttu-id="e3ca5-148">**配置不当**：发生了需要手动干预的配置错误。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-148">**Misconfigured**: A configuration error occurred that requires manual intervention.</span></span><br /><br /> <span data-ttu-id="e3ca5-149">**要求提供密码**：没有为 Oracle CDC 实例设置密码或密码无效。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-149">**Password Required**: No password was set for the Oracle CDC Instance or the password is not valid.</span></span><br /><br /> <span data-ttu-id="e3ca5-150">**意外**。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-150">**Unexpected**.</span></span> <span data-ttu-id="e3ca5-151">所有其他不可恢复错误。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-151">All other non-recoverable errors.</span></span>|  
    |<span data-ttu-id="e3ca5-152">![确定](../media/okay.gif "确定")</span><span class="sxs-lookup"><span data-stu-id="e3ca5-152">![Okay](../media/okay.gif "Okay")</span></span>|<span data-ttu-id="e3ca5-153">**正在运行**：CDC 实例正在运行并且正在处理更改记录。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-153">**Running**: The CDC Instance is running and is processing change records.</span></span> <span data-ttu-id="e3ca5-154">以下子状态可用。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-154">The following sub-statuses are available.</span></span><br /><br /> <span data-ttu-id="e3ca5-155">**空闲**：所有更改记录都已处理并且存储在目标更改表中。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-155">**Idle**: All change records have been processed and stored in the target change tables.</span></span> <span data-ttu-id="e3ca5-156">没有活动事务。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-156">There are no more active transactions.</span></span><br /><br /> <span data-ttu-id="e3ca5-157">**正在处理**：存在正处理、但尚未写入更改表的更改记录。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-157">**Processing**: There are change records being process that are not yet written to the change tables.</span></span>|  
    |<span data-ttu-id="e3ca5-158">![Stop](../media/stop.gif "停止")</span><span class="sxs-lookup"><span data-stu-id="e3ca5-158">![Stop](../media/stop.gif "Stop")</span></span>|<span data-ttu-id="e3ca5-159">**已停止**：CDC 实例未在运行。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-159">**Stopped**: The CDC instance is not running.</span></span> <span data-ttu-id="e3ca5-160">该已停止状态指示 CDC 实例已正常停止。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-160">The stopped status indicates that the CDC instance was stopped in a normal manner.</span></span>|  
    |<span data-ttu-id="e3ca5-161">![已暂停](../media/paused.gif "已暂停")</span><span class="sxs-lookup"><span data-stu-id="e3ca5-161">![Paused](../media/paused.gif "Paused")</span></span>|<span data-ttu-id="e3ca5-162">**已暂停**：CDC 实例正在运行，但由于可重试错误处理已挂起。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-162">**Paused**: The CDC instance is running but processing is suspended because of a retryable error.</span></span> <span data-ttu-id="e3ca5-163">以下子状态可用：</span><span class="sxs-lookup"><span data-stu-id="e3ca5-163">The following sub-statuses are available:</span></span><br /><br /> <span data-ttu-id="e3ca5-164">**断开连接**：无法建立到源 Oracle 数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-164">**Disconnected**: The connection to the source Oracle database cannot be established.</span></span> <span data-ttu-id="e3ca5-165">在连接恢复时会继续处理。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-165">Processing resumes when the connection is restored.</span></span><br /><br /> <span data-ttu-id="e3ca5-166">**存储**：存储已满。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-166">**Storage**: The storage is full.</span></span> <span data-ttu-id="e3ca5-167">在其他存储变为可用时将继续处理。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-167">Processing resumes when additional storage becomes available.</span></span><br /><br /> <span data-ttu-id="e3ca5-168">**记录器**：记录器连接到 Oracle，但由于临时问题（例如，所需的事务日志不可用）无法读取 Oracle 事务日志。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-168">**Logger**: The logger is connected to Oracle but cannot read the Oracle transaction logs due to a temporary problem, for example, a required transaction log is not available.</span></span>|  
  
-   <span data-ttu-id="e3ca5-169">**详细状态**：当前子状态。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-169">**Detailed Status**: The current substatus.</span></span>  
  
-   <span data-ttu-id="e3ca5-170">**状态消息**：有关当前状态的详细信息。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-170">**Status Message**: More information about the current status.</span></span>  
  
-   <span data-ttu-id="e3ca5-171">**时间戳**：上次从状态表中读取 CDC 状态时的 UTC 时间。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-171">**Timestamp**: The UTC time for when the CDC state was last read from the state table.</span></span>  
  
-   <span data-ttu-id="e3ca5-172">**当前正处理**：您在此部分中监视下列信息。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-172">**Currently Processing**: You monitor the following information in this section.</span></span>  
  
    -   <span data-ttu-id="e3ca5-173">**上一个事务时间戳**：写入更改表的上一个事务的本地时间。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-173">**Last transaction timestamp**: The local time of the last transaction written to the change tables.</span></span>  
  
    -   <span data-ttu-id="e3ca5-174">**上一个更改时间戳**：Oracle CDC 实例在源 Oracle 数据库事务日志中看到的最近更改的本地时间。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-174">**Last change timestamp**: The local time of the most recent change seen by the Oracle CDC Instance in the source Oracle database transaction logs.</span></span> <span data-ttu-id="e3ca5-175">它提供了读取 Oracle 事务日志时与 CDC 实例的当前延迟有关的信息。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-175">This provides information about the current latency of the CDC instance in reading the Oracle transaction log.</span></span>  
  
    -   <span data-ttu-id="e3ca5-176">**事务日志头 CN**：从 Oracle 事务日志读取的最近更改号 (CN)。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-176">**Transaction log head CN**: The most recent change number (CN) that was read from the Oracle transaction log.</span></span>  
  
    -   <span data-ttu-id="e3ca5-177">**事务日志尾 CN**：用于恢复或重新启动 CDC 实例的更改号。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-177">**Transaction log tail CN**: The change number for recovery or restarting the CDC instance.</span></span> <span data-ttu-id="e3ca5-178">在发生重新启动或任何其他类型的失败（包括群集故障转移）时 Oracle CDC 实例将重新定位到此位置。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-178">The Oracle CDC instance will reposition to this location in the event of a re-start or any other type of failure (including cluster failover).</span></span>  
  
    -   <span data-ttu-id="e3ca5-179">**当前 CN**：在源 Oracle 数据库（而非事务日志）中看到的最后的更改号 (SCN)。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-179">**Current CN**: The last change number (SCN) seen in the source Oracle database (not the transaction log).</span></span>  
  
    -   <span data-ttu-id="e3ca5-180">**活动事务**：Oracle CDC 实例正在处理但尚未决定（提交/回退）的源 Oracle 事务的当前数目。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-180">**Active transactions**: The current number of source Oracle transactions that are being processed by the Oracle CDC Instance and are not yet decided (commit/rollback).</span></span>  
  
    -   <span data-ttu-id="e3ca5-181">**暂存事务**：暂存到 [cdc.xdbcdc_staged_transactions](the-oracle-cdc-databases.md#bkmk_cdcxdbcdc_staged_transactions) 表的当前源 Oracle 事务的数目。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-181">**Staged transactions**: The current number source Oracle transactions that are staged to the [cdc.xdbcdc_staged_transactions](the-oracle-cdc-databases.md#bkmk_cdcxdbcdc_staged_transactions) table.</span></span>  
  
-   <span data-ttu-id="e3ca5-182">**计数器**：您在此部分中监视下列信息。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-182">**Counters**: You monitor the following information in this section.</span></span>  
  
    -   <span data-ttu-id="e3ca5-183">**完成的事务数**：自上次重置 CDC 实例后完成的事务数。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-183">**Completed transactions**: The number of transactions completed since the CDC instance was last reset.</span></span> <span data-ttu-id="e3ca5-184">此计数中不包括那些不包含有关表的事务。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-184">This does not include transactions that do not contain tables of interest.</span></span>  
  
    -   <span data-ttu-id="e3ca5-185">**写入的更改数**：已写入 SQL Server 更改表的更改的数目。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-185">**Written changes**: The number of changes written to the SQL Server change tables.</span></span>  
  
 <span data-ttu-id="e3ca5-186">**Oracle**</span><span class="sxs-lookup"><span data-stu-id="e3ca5-186">**Oracle**</span></span>  
 <span data-ttu-id="e3ca5-187">显示与 CDC 实例及其与 Oracle 数据库的连接有关的信息。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-187">Displays information about the CDC instance and its connection to the Oracle database.</span></span> <span data-ttu-id="e3ca5-188">此选项卡为只读。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-188">This tab is read only.</span></span> <span data-ttu-id="e3ca5-189">若要编辑这些属性，请在左侧窗格中右键单击实例，然后选择“属性”；或者在右侧窗格中单击“属性”以打开“\<instance> 属性”对话框 。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-189">To edit these properties, right-click the instance in the left pane and select **Properties** or click **Properties** in the right pane to open the \<instance> Properties dialog box.</span></span>  
  
 <span data-ttu-id="e3ca5-190">有关这些属性以及如何编辑它们的信息，请参阅 [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-190">For information about these properties and how to edit them, see [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md).</span></span>  
  
 <span data-ttu-id="e3ca5-191">**表**</span><span class="sxs-lookup"><span data-stu-id="e3ca5-191">**Tables**</span></span>  
 <span data-ttu-id="e3ca5-192">显示有关 CDC 实例中包含的表的信息。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-192">Displays information about the tables included in the CDC instance.</span></span> <span data-ttu-id="e3ca5-193">在此处也提供列信息。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-193">Column information is also available here.</span></span> <span data-ttu-id="e3ca5-194">此选项卡为只读。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-194">This tab is read only.</span></span> <span data-ttu-id="e3ca5-195">若要编辑这些属性，请在左侧窗格中右键单击实例，然后选择“属性”；或者在右侧窗格中单击“属性”以打开“\<instance> 属性”对话框 。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-195">To edit these properties, right-click the instance in the left pane and select **Properties** or click **Properties** in the right pane to open the \<instance> Properties dialog box.</span></span>  
  
 <span data-ttu-id="e3ca5-196">有关这些属性以及如何编辑它们的信息，请参阅 [Edit Tables](edit-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-196">For information about these properties and how to edit them, see [Edit Tables](edit-tables.md).</span></span>  
  
 <span data-ttu-id="e3ca5-197">**高级**</span><span class="sxs-lookup"><span data-stu-id="e3ca5-197">**Advanced**</span></span>  
 <span data-ttu-id="e3ca5-198">显示 CDC 实例的高级属性和属性值。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-198">Displays the advanced properties for the CDC instance and the property values.</span></span> <span data-ttu-id="e3ca5-199">此选项卡为只读。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-199">This tab is read only.</span></span> <span data-ttu-id="e3ca5-200">若要编辑这些属性，请在左侧窗格中右键单击实例，然后选择“属性”；或者在右侧窗格中单击“属性”以打开“\<instance> 属性”对话框 。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-200">To edit these properties, right-click the instance in the left pane and select **Properties** or click **Properties** in the right pane to open the \<instance> Properties dialog box.</span></span>  
  
 <span data-ttu-id="e3ca5-201">有关这些属性以及如何编辑它们的信息，请参阅 [Edit the Advanced Properties](edit-the-advanced-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e3ca5-201">For information about these properties and how to edit them, see [Edit the Advanced Properties](edit-the-advanced-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3ca5-202">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3ca5-202">See Also</span></span>  
 <span data-ttu-id="e3ca5-203">[如何创建 SQL Server 更改数据库实例](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="e3ca5-203">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 <span data-ttu-id="e3ca5-204">[如何查看 CDC 实例属性](how-to-view-the-cdc-instance-properties.md) </span><span class="sxs-lookup"><span data-stu-id="e3ca5-204">[How to View the CDC Instance Properties](how-to-view-the-cdc-instance-properties.md) </span></span>  
 <span data-ttu-id="e3ca5-205">[如何编辑 CDC 实例属性](how-to-edit-the-cdc-instance-properties.md) </span><span class="sxs-lookup"><span data-stu-id="e3ca5-205">[How to Edit the CDC Instance Properties](how-to-edit-the-cdc-instance-properties.md) </span></span>  
 [<span data-ttu-id="e3ca5-206">使用新建实例向导</span><span class="sxs-lookup"><span data-stu-id="e3ca5-206">Use the New Instance Wizard</span></span>](use-the-new-instance-wizard.md)  
