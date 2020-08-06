---
title: 查看 SQL Server 代理错误日志 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- viewing SQL Server Agent error logs
- displaying SQL Server Agent error logs
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: de920425-fa44-469f-b83d-49e3f97e97f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: b88214a158a970a754c5f313bde3d53f2652ae73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691024"
---
# <a name="view-sql-server-agent-error-log-sql-server-management-studio"></a><span data-ttu-id="649ba-102">View SQL Server Agent Error Log (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="649ba-102">View SQL Server Agent Error Log (SQL Server Management Studio)</span></span>
  <span data-ttu-id="649ba-103">本主题介绍如何使用  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中查看 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]代理错误日志。</span><span class="sxs-lookup"><span data-stu-id="649ba-103">This topic describes how to view the  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="649ba-104">日志文件查看器显示来自许多不同组件的日志信息。</span><span class="sxs-lookup"><span data-stu-id="649ba-104">Log File Viewer displays log information from many different components.</span></span> <span data-ttu-id="649ba-105">打开日志文件查看器后，请使用 **“选择日志”** 窗格选择要显示的日志。</span><span class="sxs-lookup"><span data-stu-id="649ba-105">When Log File Viewer is open, use the **Select logs** pane to select the logs you want to display.</span></span> <span data-ttu-id="649ba-106">每个日志显示适合于该类别日志的列。</span><span class="sxs-lookup"><span data-stu-id="649ba-106">Each log displays columns appropriate to that kind of log.</span></span> <span data-ttu-id="649ba-107">日志是否可用取决于日志文件查看器的打开方式。</span><span class="sxs-lookup"><span data-stu-id="649ba-107">The logs that are available depend on how Log File Viewer is opened.</span></span>  
  
 <span data-ttu-id="649ba-108">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="649ba-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="649ba-109">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="649ba-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="649ba-110">限制和局限</span><span class="sxs-lookup"><span data-stu-id="649ba-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="649ba-111">安全性</span><span class="sxs-lookup"><span data-stu-id="649ba-111">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="649ba-112">使用 SQL Server Management Studio 查看 SQL Server 代理错误日志</span><span class="sxs-lookup"><span data-stu-id="649ba-112">To view the SQL Server Agent error log, using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="649ba-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="649ba-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="649ba-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="649ba-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="649ba-115">“对象资源管理器”仅在您拥有使用权限时才显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理节点。</span><span class="sxs-lookup"><span data-stu-id="649ba-115">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="649ba-116">Security</span><span class="sxs-lookup"><span data-stu-id="649ba-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="649ba-117">权限</span><span class="sxs-lookup"><span data-stu-id="649ba-117">Permissions</span></span>  
 <span data-ttu-id="649ba-118">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，必须将 **代理配置为使用** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定服务器角色的成员帐户的凭据，才能执行其功能。</span><span class="sxs-lookup"><span data-stu-id="649ba-118">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="649ba-119">该帐户必须拥有以下 Windows 权限：</span><span class="sxs-lookup"><span data-stu-id="649ba-119">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="649ba-120">以服务身份登录 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="649ba-120">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="649ba-121">替换进程级别标记 (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="649ba-121">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="649ba-122">跳过遍历检查 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="649ba-122">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="649ba-123">调整进程的内存配额 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="649ba-123">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="649ba-124">有关代理服务帐户所需的 Windows 权限的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅为[SQL Server 代理服务选择帐户](select-an-account-for-the-sql-server-agent-service.md)和[配置 Windows 服务帐户和权限](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="649ba-124">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="649ba-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="649ba-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-ssnoversion-agent-error-log"></a><span data-ttu-id="649ba-126">查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理错误日志</span><span class="sxs-lookup"><span data-stu-id="649ba-126">To view the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log</span></span>  
  
1.  <span data-ttu-id="649ba-127">在 **“对象资源管理器”** 中，单击加号以展开包含要查看的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理错误日志的服务器。</span><span class="sxs-lookup"><span data-stu-id="649ba-127">In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log that you want to view.</span></span>  
  
2.  <span data-ttu-id="649ba-128">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="649ba-128">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="649ba-129">单击加号以展开 **“错误日志”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="649ba-129">Click the plus sign to expand the **Error Logs** folder.</span></span>  
  
4.  <span data-ttu-id="649ba-130">右键单击要查看的错误日志，并选择“查看代理日志”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="649ba-130">Right-click the error log you want to view and select **View Agent Log**.</span></span>  
  
     <span data-ttu-id="649ba-131">“日志文件查看器 - server_name”对话框中提供以下选项\*\*\*\*__：</span><span class="sxs-lookup"><span data-stu-id="649ba-131">The following options are available in the **Log File Viewer -**_server_name_ dialog box:</span></span>  
  
     <span data-ttu-id="649ba-132">**加载日志**</span><span class="sxs-lookup"><span data-stu-id="649ba-132">**Load Log**</span></span>  
     <span data-ttu-id="649ba-133">打开一个对话框，您可以在其中指定要加载的日志文件。</span><span class="sxs-lookup"><span data-stu-id="649ba-133">Open a dialog box where you can specify a log file to load.</span></span>  
  
     <span data-ttu-id="649ba-134">**导出**</span><span class="sxs-lookup"><span data-stu-id="649ba-134">**Export**</span></span>  
     <span data-ttu-id="649ba-135">打开一个对话框，你可以使用该对话框将“日志文件摘要”  网格中显示的信息导入到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="649ba-135">Open a dialog box that lets you export the information that is shown in the **Log file summary** grid to a text file.</span></span>  
  
     <span data-ttu-id="649ba-136">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="649ba-136">**Refresh**</span></span>  
     <span data-ttu-id="649ba-137">刷新选定日志的视图。</span><span class="sxs-lookup"><span data-stu-id="649ba-137">Refresh the view of the selected logs.</span></span> <span data-ttu-id="649ba-138">在应用任何筛选器设置时， **“刷新”** 按钮重新从目标服务器中读取选定的日志。</span><span class="sxs-lookup"><span data-stu-id="649ba-138">The **Refresh** button rereads the selected logs from the target server while applying any filter settings.</span></span>  
  
     <span data-ttu-id="649ba-139">**筛选器**</span><span class="sxs-lookup"><span data-stu-id="649ba-139">**Filter**</span></span>  
     <span data-ttu-id="649ba-140">打开一个对话框，你可以使用该对话框指定用于筛选日志文件的设置，例如“连接” 、“日期” 或其他“常规”  筛选条件。</span><span class="sxs-lookup"><span data-stu-id="649ba-140">Open a dialog box that lets you specify settings that are used to filter the log file, such as **Connection**, **Date**, or other **General** filter criteria.</span></span>  
  
     <span data-ttu-id="649ba-141">**搜索**</span><span class="sxs-lookup"><span data-stu-id="649ba-141">**Search**</span></span>  
     <span data-ttu-id="649ba-142">在日志文件中搜索特定文本。</span><span class="sxs-lookup"><span data-stu-id="649ba-142">Search the log file for specific text.</span></span> <span data-ttu-id="649ba-143">不支持在搜索中使用通配符。</span><span class="sxs-lookup"><span data-stu-id="649ba-143">Searching with wildcard characters is not supported.</span></span>  
  
     <span data-ttu-id="649ba-144">**Stop**</span><span class="sxs-lookup"><span data-stu-id="649ba-144">**Stop**</span></span>  
     <span data-ttu-id="649ba-145">停止加载日志文件条目。</span><span class="sxs-lookup"><span data-stu-id="649ba-145">Stops loading the log file entries.</span></span> <span data-ttu-id="649ba-146">例如，如果远程或脱机日志文件需要较长时间才能加载，并且您只想查看最新的条目，则可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="649ba-146">For example, you can use this option if a remote or offline log file takes a long time to load, and you only want to view the most recent entries.</span></span>  
  
     <span data-ttu-id="649ba-147">**日志文件摘要**</span><span class="sxs-lookup"><span data-stu-id="649ba-147">**Log file summary**</span></span>  
     <span data-ttu-id="649ba-148">此信息窗格显示日志文件筛选摘要。</span><span class="sxs-lookup"><span data-stu-id="649ba-148">This information panel displays a summary of the log file filtering.</span></span> <span data-ttu-id="649ba-149">如果未对文件进行筛选，您将看到以下文本： **“未应用任何筛选器”** 。</span><span class="sxs-lookup"><span data-stu-id="649ba-149">If the file is not filtered, you will see the following text, **No filter applied**.</span></span> <span data-ttu-id="649ba-150">如果对日志应用了筛选器，将看到以下文本：基于以下条件筛选日志项：\<filter criteria>。</span><span class="sxs-lookup"><span data-stu-id="649ba-150">If a filter is applied to the log, you will see the following text, **Filter log entries where:** \<filter criteria>.</span></span>  
  
     <span data-ttu-id="649ba-151">**所选行详细信息**</span><span class="sxs-lookup"><span data-stu-id="649ba-151">**Selected row details**</span></span>  
     <span data-ttu-id="649ba-152">选择一行可以在页面底部显示有关所选事件行的其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="649ba-152">Select a row to display additional details about the selected event row at the bottom of the page.</span></span> <span data-ttu-id="649ba-153">在网格中，通过将列拖动到的新位置可以重新排列各列的顺序。</span><span class="sxs-lookup"><span data-stu-id="649ba-153">The columns can be reordered by dragging them to new locations in the grid.</span></span> <span data-ttu-id="649ba-154">通过将网格标题中的列分隔条向左或向右拖动，可以调列的大小。</span><span class="sxs-lookup"><span data-stu-id="649ba-154">The columns can be resized by dragging the column separator bars in the grid header to the left or right.</span></span> <span data-ttu-id="649ba-155">双击网格标题中的列分隔条，可以按内容宽度自动调整列的大小。</span><span class="sxs-lookup"><span data-stu-id="649ba-155">Double-click the column separator bars in the grid header to automatically size the column to the content width.</span></span>  
  
     <span data-ttu-id="649ba-156">**实例**</span><span class="sxs-lookup"><span data-stu-id="649ba-156">**Instance**</span></span>  
     <span data-ttu-id="649ba-157">发生事件的实例的名称。</span><span class="sxs-lookup"><span data-stu-id="649ba-157">The name of the instance on which the event occurred.</span></span> <span data-ttu-id="649ba-158">这显示为：计算机名称\\实例名称 。</span><span class="sxs-lookup"><span data-stu-id="649ba-158">This is displayed as *computer name*\\*instance name*.</span></span>  
  
     <span data-ttu-id="649ba-159">**Date**</span><span class="sxs-lookup"><span data-stu-id="649ba-159">**Date**</span></span>  
     <span data-ttu-id="649ba-160">显示事件的日期。</span><span class="sxs-lookup"><span data-stu-id="649ba-160">Displays the date of the event.</span></span>  
  
     <span data-ttu-id="649ba-161">**数据源**</span><span class="sxs-lookup"><span data-stu-id="649ba-161">**Source**</span></span>  
     <span data-ttu-id="649ba-162">显示从其创建事件的源功能，例如服务的名称（如 MSSQLSERVER）。</span><span class="sxs-lookup"><span data-stu-id="649ba-162">Displays the source feature from which the event is created, such as the name of the service (MSSQLSERVER, for example).</span></span> <span data-ttu-id="649ba-163">并非对所有日志类型都显示此项。</span><span class="sxs-lookup"><span data-stu-id="649ba-163">This does not appear for all log types.</span></span>  
  
     <span data-ttu-id="649ba-164">**消息**</span><span class="sxs-lookup"><span data-stu-id="649ba-164">**Message**</span></span>  
     <span data-ttu-id="649ba-165">显示与事件相关联的任何消息。</span><span class="sxs-lookup"><span data-stu-id="649ba-165">Displays any messages associated with the event.</span></span>  
  
     <span data-ttu-id="649ba-166">**日志类型**</span><span class="sxs-lookup"><span data-stu-id="649ba-166">**Log Type**</span></span>  
     <span data-ttu-id="649ba-167">显示事件所属的日志类型。</span><span class="sxs-lookup"><span data-stu-id="649ba-167">Displays the type of log to which the event belongs.</span></span> <span data-ttu-id="649ba-168">所有选定的日志都显示在日志文件摘要窗口中。</span><span class="sxs-lookup"><span data-stu-id="649ba-168">All selected logs appear in the log file summary window.</span></span>  
  
     <span data-ttu-id="649ba-169">**日志源**</span><span class="sxs-lookup"><span data-stu-id="649ba-169">**Log Source**</span></span>  
     <span data-ttu-id="649ba-170">显示在其中捕获事件的源日志的说明。</span><span class="sxs-lookup"><span data-stu-id="649ba-170">Displays a description of the source log in which the event is captured.</span></span>  
  
5.  <span data-ttu-id="649ba-171">完成后，单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="649ba-171">When finished, click **Close**.</span></span>  
  
  
