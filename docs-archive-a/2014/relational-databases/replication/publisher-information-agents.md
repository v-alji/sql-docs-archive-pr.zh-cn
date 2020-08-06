---
title: 发布服务器信息，代理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.commonjobs.f1
ms.assetid: 2346c00d-c269-45a1-af14-68e7fd7ebd7e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bdd2055ed022257524bc4d2784bdc333537be855
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577526"
---
# <a name="publisher-information-agents"></a><span data-ttu-id="7907a-102">发布服务器信息，代理</span><span class="sxs-lookup"><span data-stu-id="7907a-102">Publisher Information, Agents</span></span>
  <span data-ttu-id="7907a-103">**“代理”** 选项卡显示与发布服务器关联的代理和维护作业的相关信息：</span><span class="sxs-lookup"><span data-stu-id="7907a-103">The **Agents** tab displays information about the agents and maintenance jobs that are associated with the Publisher:</span></span>  
  
-   <span data-ttu-id="7907a-104">快照代理，为所有发布显示。</span><span class="sxs-lookup"><span data-stu-id="7907a-104">Snapshot Agent, which is displayed for all publications.</span></span>  
  
-   <span data-ttu-id="7907a-105">日志读取器代理，为所有事务发布显示。</span><span class="sxs-lookup"><span data-stu-id="7907a-105">Log Reader Agent, which is displayed for all transactional publications.</span></span>  
  
-   <span data-ttu-id="7907a-106">队列读取器代理，为那些针对排队更新订阅启用的事务发布显示。</span><span class="sxs-lookup"><span data-stu-id="7907a-106">Queue Reader Agent, which is displayed for those transactional publications that are enabled for queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="7907a-107">维护作业，为所有发布显示：</span><span class="sxs-lookup"><span data-stu-id="7907a-107">Maintenance jobs, displayed for all publications:</span></span>  
  
    -   <span data-ttu-id="7907a-108">重新初始化出现数据验证失败的订阅</span><span class="sxs-lookup"><span data-stu-id="7907a-108">Reinitialize subscriptions that have data validation failures</span></span>  
  
    -   <span data-ttu-id="7907a-109">代理历史记录清除：分发</span><span class="sxs-lookup"><span data-stu-id="7907a-109">Agent history cleanup: distribution</span></span>  
  
    -   <span data-ttu-id="7907a-110">分发的复制监视刷新器</span><span class="sxs-lookup"><span data-stu-id="7907a-110">Replication monitoring refresher for distribution</span></span>  
  
    -   <span data-ttu-id="7907a-111">复制代理检查</span><span class="sxs-lookup"><span data-stu-id="7907a-111">Replication agents checkup</span></span>  
  
    -   <span data-ttu-id="7907a-112">分发清除：分发</span><span class="sxs-lookup"><span data-stu-id="7907a-112">Distribution cleanup: distribution</span></span>  
  
    -   <span data-ttu-id="7907a-113">过期的订阅清除</span><span class="sxs-lookup"><span data-stu-id="7907a-113">Expired subscription cleanup</span></span>  
  
 <span data-ttu-id="7907a-114">有关这些作业的详细信息，请参阅[复制代理管理](agents/replication-agent-administration.md)。</span><span class="sxs-lookup"><span data-stu-id="7907a-114">For more information about these jobs, see [Replication Agent Administration](agents/replication-agent-administration.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="7907a-115">选项</span><span class="sxs-lookup"><span data-stu-id="7907a-115">Options</span></span>  
 <span data-ttu-id="7907a-116">若要显示有关代理或作业的信息，请从 **“代理和作业类型”** 下拉菜单中选择。</span><span class="sxs-lookup"><span data-stu-id="7907a-116">To display information about an agent or job, select from the **Agent and Job Types** drop-down menu.</span></span> <span data-ttu-id="7907a-117">若要查看与代理或作业相关的详细信息和任务，请右键单击该代理或作业所在的行，然后单击快捷菜单上的选项。</span><span class="sxs-lookup"><span data-stu-id="7907a-117">For more detailed information and tasks that are related to an agent or job, right-click the row for that agent or job, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="7907a-118">若要更改网格显示数据的方式，请右键单击网格，然后单击以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="7907a-118">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="7907a-119">**排序**：按 **“列排序”** 对话框中的一列或多列排序。</span><span class="sxs-lookup"><span data-stu-id="7907a-119">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="7907a-120">**选择要显示的列**：选择要显示哪些列以及要在 **“选择列”** 对话框中以何种顺序显示它们。</span><span class="sxs-lookup"><span data-stu-id="7907a-120">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="7907a-121">**筛选器**：根据 **“筛选设置”** 对话框中的列值筛选网格中的行。</span><span class="sxs-lookup"><span data-stu-id="7907a-121">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="7907a-122">**清除筛选器**：清除网格的任何筛选设置。</span><span class="sxs-lookup"><span data-stu-id="7907a-122">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="7907a-123">筛选设置是特定于每个网格的。</span><span class="sxs-lookup"><span data-stu-id="7907a-123">Filter settings are specific to each grid.</span></span> <span data-ttu-id="7907a-124">列的选择和排序应用于同一类型的所有网格，如每个发布服务器的发布网格。</span><span class="sxs-lookup"><span data-stu-id="7907a-124">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="7907a-125">以下各节说明了此选项卡上为每个代理或作业显示的数据。</span><span class="sxs-lookup"><span data-stu-id="7907a-125">The following sections describe the data that is displayed on this tab for each agent or job.</span></span>  
  
### <a name="snapshot-agent"></a><span data-ttu-id="7907a-126">快照代理</span><span class="sxs-lookup"><span data-stu-id="7907a-126">Snapshot Agent</span></span>  
 <span data-ttu-id="7907a-127">**Status**</span><span class="sxs-lookup"><span data-stu-id="7907a-127">**Status**</span></span>  
 <span data-ttu-id="7907a-128">此代理的状态。</span><span class="sxs-lookup"><span data-stu-id="7907a-128">The status of the agent.</span></span> <span data-ttu-id="7907a-129">下面列出了可能的状态值：</span><span class="sxs-lookup"><span data-stu-id="7907a-129">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="7907a-130">错误</span><span class="sxs-lookup"><span data-stu-id="7907a-130">Error</span></span>  
  
-   <span data-ttu-id="7907a-131">重试</span><span class="sxs-lookup"><span data-stu-id="7907a-131">Retry</span></span>  
  
-   <span data-ttu-id="7907a-132">正在运行</span><span class="sxs-lookup"><span data-stu-id="7907a-132">Running</span></span>  
  
-   <span data-ttu-id="7907a-133">已完成</span><span class="sxs-lookup"><span data-stu-id="7907a-133">Completed</span></span>  
  
 <span data-ttu-id="7907a-134">**发布**</span><span class="sxs-lookup"><span data-stu-id="7907a-134">**Publication**</span></span>  
 <span data-ttu-id="7907a-135">与此代理关联的发布的名称。</span><span class="sxs-lookup"><span data-stu-id="7907a-135">The name of the publication with which the agent is associated.</span></span>  
  
 <span data-ttu-id="7907a-136">**上次启动时间**</span><span class="sxs-lookup"><span data-stu-id="7907a-136">**Last Start Time**</span></span>  
 <span data-ttu-id="7907a-137">上次启动此代理的时间。</span><span class="sxs-lookup"><span data-stu-id="7907a-137">The last time at which the agent started.</span></span>  
  
 <span data-ttu-id="7907a-138">**Duration**</span><span class="sxs-lookup"><span data-stu-id="7907a-138">**Duration**</span></span>  
 <span data-ttu-id="7907a-139">此代理已经运行的时间长度。</span><span class="sxs-lookup"><span data-stu-id="7907a-139">The length of time the agent has run.</span></span> <span data-ttu-id="7907a-140">如果此代理当前正在运行，该时间表示已运行的时间；如果此代理之前已运行完毕，则该时间表示总时间。</span><span class="sxs-lookup"><span data-stu-id="7907a-140">The time represents elapsed time if the agent is currently running, and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="7907a-141">**上一操作**</span><span class="sxs-lookup"><span data-stu-id="7907a-141">**Last Action**</span></span>  
 <span data-ttu-id="7907a-142">在此代理最近一次运行的过程中最后执行的操作。</span><span class="sxs-lookup"><span data-stu-id="7907a-142">The last action performed during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="7907a-143">**传送速率**</span><span class="sxs-lookup"><span data-stu-id="7907a-143">**Delivery Rate**</span></span>  
 <span data-ttu-id="7907a-144">在此代理最近一次运行期间分发数据库中提交初始化命令的速率，以每秒的命令数表示。</span><span class="sxs-lookup"><span data-stu-id="7907a-144">The rate, in commands per second, at which initialization commands are committed in the distribution database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="7907a-145">**事务数**</span><span class="sxs-lookup"><span data-stu-id="7907a-145">**#Trans**</span></span>  
 <span data-ttu-id="7907a-146">在此代理最近一次运行期间分发数据库中提交的事务数。</span><span class="sxs-lookup"><span data-stu-id="7907a-146">The number of transactions committed in the distribution database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="7907a-147">**命令数**</span><span class="sxs-lookup"><span data-stu-id="7907a-147">**#Cmds**</span></span>  
 <span data-ttu-id="7907a-148">在此代理最近一次运行期间分发数据库中提交的命令数。</span><span class="sxs-lookup"><span data-stu-id="7907a-148">The number of commands committed in the distribution database during the most recent run of the agent.</span></span> <span data-ttu-id="7907a-149">一个命令相当于一次数据更改，如一次更新。</span><span class="sxs-lookup"><span data-stu-id="7907a-149">A command is equivalent to a data change, such as an update.</span></span>  
  
### <a name="log-reader-agent"></a><span data-ttu-id="7907a-150">日志读取器代理</span><span class="sxs-lookup"><span data-stu-id="7907a-150">Log Reader Agent</span></span>  
 <span data-ttu-id="7907a-151">**Status**</span><span class="sxs-lookup"><span data-stu-id="7907a-151">**Status**</span></span>  
 <span data-ttu-id="7907a-152">此代理的状态。</span><span class="sxs-lookup"><span data-stu-id="7907a-152">The status of the agent.</span></span> <span data-ttu-id="7907a-153">下面列出了可能的状态值：</span><span class="sxs-lookup"><span data-stu-id="7907a-153">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="7907a-154">错误</span><span class="sxs-lookup"><span data-stu-id="7907a-154">Error</span></span>  
  
-   <span data-ttu-id="7907a-155">重试</span><span class="sxs-lookup"><span data-stu-id="7907a-155">Retry</span></span>  
  
-   <span data-ttu-id="7907a-156">正在运行</span><span class="sxs-lookup"><span data-stu-id="7907a-156">Running</span></span>  
  
-   <span data-ttu-id="7907a-157">未运行</span><span class="sxs-lookup"><span data-stu-id="7907a-157">Not running</span></span>  
  
 <span data-ttu-id="7907a-158">**发布数据库**</span><span class="sxs-lookup"><span data-stu-id="7907a-158">**Publication Database**</span></span>  
 <span data-ttu-id="7907a-159">与此代理关联的发布的名称。</span><span class="sxs-lookup"><span data-stu-id="7907a-159">The name of the publication with which the agent is associated.</span></span>  
  
 <span data-ttu-id="7907a-160">**上次启动时间**</span><span class="sxs-lookup"><span data-stu-id="7907a-160">**Last Start Time**</span></span>  
 <span data-ttu-id="7907a-161">上次启动此代理的时间。</span><span class="sxs-lookup"><span data-stu-id="7907a-161">The last time at which the agent started.</span></span>  
  
 <span data-ttu-id="7907a-162">**Duration**</span><span class="sxs-lookup"><span data-stu-id="7907a-162">**Duration**</span></span>  
 <span data-ttu-id="7907a-163">此代理已经运行的时间长度。</span><span class="sxs-lookup"><span data-stu-id="7907a-163">The length of time the agent has run.</span></span> <span data-ttu-id="7907a-164">如果此代理当前正在运行，该时间表示已运行的时间；如果此代理之前已运行完毕，则该时间表示总时间。</span><span class="sxs-lookup"><span data-stu-id="7907a-164">The time represents elapsed time if the agent is currently running, and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="7907a-165">**上一操作**</span><span class="sxs-lookup"><span data-stu-id="7907a-165">**Last Action**</span></span>  
 <span data-ttu-id="7907a-166">在此代理最近一次运行的过程中最后执行的操作。</span><span class="sxs-lookup"><span data-stu-id="7907a-166">The last action performed during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="7907a-167">**传送速率**</span><span class="sxs-lookup"><span data-stu-id="7907a-167">**Delivery Rate**</span></span>  
 <span data-ttu-id="7907a-168">在分发数据库中提交更改的速率，以每秒的命令数为单位。</span><span class="sxs-lookup"><span data-stu-id="7907a-168">The rate, in commands per second, at which changes are committed in the distribution database.</span></span>  
  
 <span data-ttu-id="7907a-169">**滞后时间**</span><span class="sxs-lookup"><span data-stu-id="7907a-169">**Latency**</span></span>  
 <span data-ttu-id="7907a-170">从在发布数据库中提交最近的更改到在分发数据库中提交对应的命令经过的时间，以秒为单位。</span><span class="sxs-lookup"><span data-stu-id="7907a-170">The amount of time, in seconds, that has elapsed between the most recent change being committed in the publication database, and the corresponding command being committed in the distribution database.</span></span>  
  
 <span data-ttu-id="7907a-171">**事务数**</span><span class="sxs-lookup"><span data-stu-id="7907a-171">**#Trans**</span></span>  
 <span data-ttu-id="7907a-172">在此代理最近一次运行期间分发数据库中提交的事务数。</span><span class="sxs-lookup"><span data-stu-id="7907a-172">The number of transactions committed in the distribution database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="7907a-173">**命令数**</span><span class="sxs-lookup"><span data-stu-id="7907a-173">**#Cmds**</span></span>  
 <span data-ttu-id="7907a-174">在此代理最近一次运行期间分发数据库中提交的命令数。</span><span class="sxs-lookup"><span data-stu-id="7907a-174">The number of commands committed in the distribution database during the most recent run of the agent.</span></span> <span data-ttu-id="7907a-175">一个命令相当于一次数据更改，如一次更新。</span><span class="sxs-lookup"><span data-stu-id="7907a-175">A command is equivalent to a data change, such as an update.</span></span>  
  
 <span data-ttu-id="7907a-176">**平均命令数**</span><span class="sxs-lookup"><span data-stu-id="7907a-176">**Avg. #Cmds**</span></span>  
 <span data-ttu-id="7907a-177">在此代理最近一次运行期间平均每个事务的命令数。</span><span class="sxs-lookup"><span data-stu-id="7907a-177">The average number of commands per transaction during the most recent run of the agent.</span></span>  
  
### <a name="queue-reader-agent"></a><span data-ttu-id="7907a-178">队列读取器代理</span><span class="sxs-lookup"><span data-stu-id="7907a-178">Queue Reader Agent</span></span>  
 <span data-ttu-id="7907a-179">**Status**</span><span class="sxs-lookup"><span data-stu-id="7907a-179">**Status**</span></span>  
 <span data-ttu-id="7907a-180">此代理的状态。</span><span class="sxs-lookup"><span data-stu-id="7907a-180">The status of the agent.</span></span> <span data-ttu-id="7907a-181">下面列出了可能的状态值：</span><span class="sxs-lookup"><span data-stu-id="7907a-181">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="7907a-182">错误</span><span class="sxs-lookup"><span data-stu-id="7907a-182">Error</span></span>  
  
-   <span data-ttu-id="7907a-183">重试</span><span class="sxs-lookup"><span data-stu-id="7907a-183">Retry</span></span>  
  
-   <span data-ttu-id="7907a-184">正在运行</span><span class="sxs-lookup"><span data-stu-id="7907a-184">Running</span></span>  
  
-   <span data-ttu-id="7907a-185">未运行</span><span class="sxs-lookup"><span data-stu-id="7907a-185">Not running</span></span>  
  
 <span data-ttu-id="7907a-186">**分发数据库**</span><span class="sxs-lookup"><span data-stu-id="7907a-186">**Distribution Database**</span></span>  
 <span data-ttu-id="7907a-187">与此代理关联的分发数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="7907a-187">The name of the distribution database with which the agent is associated.</span></span>  
  
 <span data-ttu-id="7907a-188">**上次启动时间**</span><span class="sxs-lookup"><span data-stu-id="7907a-188">**Last Start Time**</span></span>  
 <span data-ttu-id="7907a-189">上次启动此代理的时间。</span><span class="sxs-lookup"><span data-stu-id="7907a-189">The last time at which the agent started.</span></span>  
  
 <span data-ttu-id="7907a-190">**Duration**</span><span class="sxs-lookup"><span data-stu-id="7907a-190">**Duration**</span></span>  
 <span data-ttu-id="7907a-191">此代理已经运行的时间长度。</span><span class="sxs-lookup"><span data-stu-id="7907a-191">The length of time the agent has run.</span></span> <span data-ttu-id="7907a-192">如果代理当前正在运行，该时间表示已用时间；如果代理已在之前运行完毕，则该时间表示总时间。</span><span class="sxs-lookup"><span data-stu-id="7907a-192">The time represents elapsed time if the agent is currently running and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="7907a-193">**上一操作**</span><span class="sxs-lookup"><span data-stu-id="7907a-193">**Last Action**</span></span>  
 <span data-ttu-id="7907a-194">在此代理最近一次运行的过程中最后执行的操作。</span><span class="sxs-lookup"><span data-stu-id="7907a-194">The last action performed during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="7907a-195">**传送速率**</span><span class="sxs-lookup"><span data-stu-id="7907a-195">**Delivery Rate**</span></span>  
 <span data-ttu-id="7907a-196">在分发数据库中提交更改的速率，以每秒的命令数为单位。</span><span class="sxs-lookup"><span data-stu-id="7907a-196">The rate, in commands per second, at which changes are committed in the distribution database.</span></span>  
  
 <span data-ttu-id="7907a-197">**滞后时间**</span><span class="sxs-lookup"><span data-stu-id="7907a-197">**Latency**</span></span>  
 <span data-ttu-id="7907a-198">从在订阅数据库中提交最近的更改到在发布数据库中提交对应的命令经过的时间，以秒为单位。</span><span class="sxs-lookup"><span data-stu-id="7907a-198">The amount of time, in seconds, that has elapsed between the most recent change being committed in a subscription database, and the corresponding command being committed in the publication database.</span></span>  
  
 <span data-ttu-id="7907a-199">**事务数**</span><span class="sxs-lookup"><span data-stu-id="7907a-199">**#Trans**</span></span>  
 <span data-ttu-id="7907a-200">在此代理最近一次运行期间发布数据库中提交的事务数。</span><span class="sxs-lookup"><span data-stu-id="7907a-200">The number of transactions committed in the publication database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="7907a-201">**命令数**</span><span class="sxs-lookup"><span data-stu-id="7907a-201">**#Cmds**</span></span>  
 <span data-ttu-id="7907a-202">在此代理最近一次运行期间发布数据库中提交的命令数。</span><span class="sxs-lookup"><span data-stu-id="7907a-202">The number of commands committed in the publication database during the most recent run of the agent.</span></span> <span data-ttu-id="7907a-203">一个命令相当于一次数据更改，如一次更新。</span><span class="sxs-lookup"><span data-stu-id="7907a-203">A command is equivalent to a data change, such as an update.</span></span>  
  
 <span data-ttu-id="7907a-204">**平均命令数**</span><span class="sxs-lookup"><span data-stu-id="7907a-204">**Avg. #Cmds**</span></span>  
 <span data-ttu-id="7907a-205">在此代理最近一次运行期间平均每个事务的命令数。</span><span class="sxs-lookup"><span data-stu-id="7907a-205">The average number of commands per transaction during the most recent run of the agent.</span></span>  
  
### <a name="maintenance-jobs"></a><span data-ttu-id="7907a-206">维护作业</span><span class="sxs-lookup"><span data-stu-id="7907a-206">Maintenance Jobs</span></span>  
 <span data-ttu-id="7907a-207">**Status**</span><span class="sxs-lookup"><span data-stu-id="7907a-207">**Status**</span></span>  
 <span data-ttu-id="7907a-208">每个作业的状态。</span><span class="sxs-lookup"><span data-stu-id="7907a-208">The status of each job.</span></span> <span data-ttu-id="7907a-209">下面列出了可能的状态值：</span><span class="sxs-lookup"><span data-stu-id="7907a-209">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="7907a-210">错误</span><span class="sxs-lookup"><span data-stu-id="7907a-210">Error</span></span>  
  
-   <span data-ttu-id="7907a-211">重试</span><span class="sxs-lookup"><span data-stu-id="7907a-211">Retry</span></span>  
  
-   <span data-ttu-id="7907a-212">正在运行</span><span class="sxs-lookup"><span data-stu-id="7907a-212">Running</span></span>  
  
-   <span data-ttu-id="7907a-213">未运行</span><span class="sxs-lookup"><span data-stu-id="7907a-213">Not running</span></span>  
  
 <span data-ttu-id="7907a-214">**作业**</span><span class="sxs-lookup"><span data-stu-id="7907a-214">**Job**</span></span>  
 <span data-ttu-id="7907a-215">作业的名称。</span><span class="sxs-lookup"><span data-stu-id="7907a-215">The name of the job.</span></span>  
  
 <span data-ttu-id="7907a-216">**上次启动时间**</span><span class="sxs-lookup"><span data-stu-id="7907a-216">**Last Start Time**</span></span>  
 <span data-ttu-id="7907a-217">上次启动作业的时间。</span><span class="sxs-lookup"><span data-stu-id="7907a-217">The last time at which the job started.</span></span>  
  
 <span data-ttu-id="7907a-218">**Duration**</span><span class="sxs-lookup"><span data-stu-id="7907a-218">**Duration**</span></span>  
 <span data-ttu-id="7907a-219">作业已运行的时间。</span><span class="sxs-lookup"><span data-stu-id="7907a-219">The length of time the job has run.</span></span> <span data-ttu-id="7907a-220">如果此作业当前正在运行，该时间表示已运行的时间；如果此作业之前已运行完毕，该时间表示总时间。</span><span class="sxs-lookup"><span data-stu-id="7907a-220">The time represents elapsed time if the job is currently running, and total time if the job has run previously.</span></span>  
  
 <span data-ttu-id="7907a-221">**上一操作**</span><span class="sxs-lookup"><span data-stu-id="7907a-221">**Last Action**</span></span>  
 <span data-ttu-id="7907a-222">在此作业最近一次运行的过程中最后执行的操作。</span><span class="sxs-lookup"><span data-stu-id="7907a-222">The last action performed during the most recent run of the job.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7907a-223">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7907a-223">See Also</span></span>  
 <span data-ttu-id="7907a-224">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="7907a-224">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="7907a-225">[使用复制监视器查看信息和执行任务](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="7907a-225">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="7907a-226">监视复制</span><span class="sxs-lookup"><span data-stu-id="7907a-226">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
