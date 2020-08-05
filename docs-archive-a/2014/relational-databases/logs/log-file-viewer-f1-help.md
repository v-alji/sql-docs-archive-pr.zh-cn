---
title: 日志文件查看器 F1 帮助 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configurelogs.errorlog.f1
helpviewer_keywords:
- Log File Viewer
ms.assetid: 2243845c-4880-4aa0-9ee8-0a97a128996b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c6eadb4baa4a47202b40a9cde1eca896022f31d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580734"
---
# <a name="log-file-viewer-f1-help"></a><span data-ttu-id="027a8-102">日志文件查看器 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="027a8-102">Log File Viewer F1 Help</span></span>
  <span data-ttu-id="027a8-103">日志文件查看器显示来自许多不同组件的日志信息。</span><span class="sxs-lookup"><span data-stu-id="027a8-103">Log File Viewer displays log information from many different components.</span></span> <span data-ttu-id="027a8-104">打开日志文件查看器后，请使用 **“选择日志”** 窗格选择要显示的日志。</span><span class="sxs-lookup"><span data-stu-id="027a8-104">When Log File Viewer is open, use the **Select logs** pane to select the logs you want to display.</span></span> <span data-ttu-id="027a8-105">每个日志显示适合于该类别日志的列。</span><span class="sxs-lookup"><span data-stu-id="027a8-105">Each log displays columns appropriate to that kind of log.</span></span>  
  
 <span data-ttu-id="027a8-106">日志是否可用取决于日志文件查看器的打开方式。</span><span class="sxs-lookup"><span data-stu-id="027a8-106">The logs that are available depend on how Log File Viewer is opened.</span></span> <span data-ttu-id="027a8-107">有关详细信息，请参阅 [打开日志文件查看器](open-log-file-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="027a8-107">For more information, see [Open Log File Viewer](open-log-file-viewer.md).</span></span>  
  
 <span data-ttu-id="027a8-108">可以在“工具/选项”  对话框的“SQL Server 对象资源管理器/命令”  页上配置为审核日志显示的行数。</span><span class="sxs-lookup"><span data-stu-id="027a8-108">The number of rows that are displayed for audit logs can be configured on the **SQL Server Object Explorer/Commands** page of the **Tools/Options** dialog box.</span></span> <span data-ttu-id="027a8-109">有关为审核日志显示的列的说明，请参阅 [sys.fn_get_audit_file (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="027a8-109">For descriptions of the columns that are displayed for audit logs, see [sys.fn_get_audit_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql).</span></span>  
  
## <a name="options"></a><span data-ttu-id="027a8-110">选项</span><span class="sxs-lookup"><span data-stu-id="027a8-110">Options</span></span>  
 <span data-ttu-id="027a8-111">**加载日志**</span><span class="sxs-lookup"><span data-stu-id="027a8-111">**Load Log**</span></span>  
 <span data-ttu-id="027a8-112">打开一个对话框，您可以在其中指定要加载的日志文件。</span><span class="sxs-lookup"><span data-stu-id="027a8-112">Open a dialog box where you can specify a log file to load.</span></span>  
  
 <span data-ttu-id="027a8-113">**导出**</span><span class="sxs-lookup"><span data-stu-id="027a8-113">**Export**</span></span>  
 <span data-ttu-id="027a8-114">打开一个对话框，你可以使用该对话框将“日志文件摘要”  网格中显示的信息导入到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="027a8-114">Open a dialog box that lets you export the information that is shown in the **Log file summary** grid to a text file.</span></span>  
  
 <span data-ttu-id="027a8-115">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="027a8-115">**Refresh**</span></span>  
 <span data-ttu-id="027a8-116">刷新选定日志的视图。</span><span class="sxs-lookup"><span data-stu-id="027a8-116">Refresh the view of the selected logs.</span></span> <span data-ttu-id="027a8-117">在应用任何筛选器设置时， **“刷新”** 按钮重新从目标服务器中读取选定的日志。</span><span class="sxs-lookup"><span data-stu-id="027a8-117">The **Refresh** button rereads the selected logs from the target server while applying any filter settings.</span></span>  
  
 <span data-ttu-id="027a8-118">**筛选器**</span><span class="sxs-lookup"><span data-stu-id="027a8-118">**Filter**</span></span>  
 <span data-ttu-id="027a8-119">打开一个对话框，你可以使用该对话框指定用于筛选日志文件的设置，例如“连接” 、“日期” 或其他“常规”  筛选条件。</span><span class="sxs-lookup"><span data-stu-id="027a8-119">Open a dialog box that lets you specify settings that are used to filter the log file, such as **Connection**, **Date**, or other **General** filter criteria.</span></span>  
  
 <span data-ttu-id="027a8-120">**搜索**</span><span class="sxs-lookup"><span data-stu-id="027a8-120">**Search**</span></span>  
 <span data-ttu-id="027a8-121">在日志文件中搜索特定文本。</span><span class="sxs-lookup"><span data-stu-id="027a8-121">Search the log file for specific text.</span></span> <span data-ttu-id="027a8-122">不支持在搜索中使用通配符。</span><span class="sxs-lookup"><span data-stu-id="027a8-122">Searching with wildcard characters is not supported.</span></span>  
  
 <span data-ttu-id="027a8-123">**Stop**</span><span class="sxs-lookup"><span data-stu-id="027a8-123">**Stop**</span></span>  
 <span data-ttu-id="027a8-124">停止加载日志文件条目。</span><span class="sxs-lookup"><span data-stu-id="027a8-124">Stops loading the log file entries.</span></span> <span data-ttu-id="027a8-125">例如，如果远程或脱机日志文件需要较长时间才能加载，并且您只想查看最新的条目，则可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="027a8-125">For example, you can use this option if a remote or offline log file takes a long time to load, and you only want to view the most recent entries.</span></span>  
  
 <span data-ttu-id="027a8-126">**日志文件摘要**</span><span class="sxs-lookup"><span data-stu-id="027a8-126">**Log file summary**</span></span>  
 <span data-ttu-id="027a8-127">此信息窗格显示日志文件筛选摘要。</span><span class="sxs-lookup"><span data-stu-id="027a8-127">This information panel displays a summary of the log file filtering.</span></span> <span data-ttu-id="027a8-128">如果未对文件进行筛选，您将看到以下文本： **“未应用任何筛选器”** 。</span><span class="sxs-lookup"><span data-stu-id="027a8-128">If the file is not filtered, you will see the following text, **No filter applied**.</span></span> <span data-ttu-id="027a8-129">如果对日志应用了筛选器，将看到以下文本：基于以下条件筛选日志项：\<filter criteria>。</span><span class="sxs-lookup"><span data-stu-id="027a8-129">If a filter is applied to the log, you will see the following text, **Filter log entries where:** \<filter criteria>.</span></span>  
  
 <span data-ttu-id="027a8-130">**所选行详细信息**</span><span class="sxs-lookup"><span data-stu-id="027a8-130">**Selected row details**</span></span>  
 <span data-ttu-id="027a8-131">选择一行可以在页面底部显示有关所选事件行的其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="027a8-131">Select a row to display additional details about the selected event row at the bottom of the page.</span></span> <span data-ttu-id="027a8-132">在网格中，通过将列拖动到的新位置可以重新排列各列的顺序。</span><span class="sxs-lookup"><span data-stu-id="027a8-132">The columns can be reordered by dragging them to new locations in the grid.</span></span> <span data-ttu-id="027a8-133">通过将网格标题中的列分隔条向左或向右拖动，可以调列的大小。</span><span class="sxs-lookup"><span data-stu-id="027a8-133">The columns can be resized by dragging the column separator bars in the grid header to the left or right.</span></span> <span data-ttu-id="027a8-134">双击网格标题中的列分隔条，可以按内容宽度自动调整列的大小。</span><span class="sxs-lookup"><span data-stu-id="027a8-134">Double-click the column separator bars in the grid header to automatically size the column to the content width.</span></span>  
  
 <span data-ttu-id="027a8-135">**实例**</span><span class="sxs-lookup"><span data-stu-id="027a8-135">**Instance**</span></span>  
 <span data-ttu-id="027a8-136">发生事件的实例的名称。</span><span class="sxs-lookup"><span data-stu-id="027a8-136">The name of the instance on which the event occurred.</span></span> <span data-ttu-id="027a8-137">这显示为：计算机名称\\实例名称 。</span><span class="sxs-lookup"><span data-stu-id="027a8-137">This is displayed as *computer name*\\*instance name*.</span></span>  
  
## <a name="frequently-displayed-columns"></a><span data-ttu-id="027a8-138">经常显示的列</span><span class="sxs-lookup"><span data-stu-id="027a8-138">Frequently Displayed Columns</span></span>  
 <span data-ttu-id="027a8-139">**Date**</span><span class="sxs-lookup"><span data-stu-id="027a8-139">**Date**</span></span>  
 <span data-ttu-id="027a8-140">显示事件的日期。</span><span class="sxs-lookup"><span data-stu-id="027a8-140">Displays the date of the event.</span></span>  
  
 <span data-ttu-id="027a8-141">**数据源**</span><span class="sxs-lookup"><span data-stu-id="027a8-141">**Source**</span></span>  
 <span data-ttu-id="027a8-142">显示从其创建事件的源功能，例如服务的名称（如 MSSQLSERVER）。</span><span class="sxs-lookup"><span data-stu-id="027a8-142">Displays the source feature from which the event is created, such as the name of the service (MSSQLSERVER, for example).</span></span> <span data-ttu-id="027a8-143">并非对所有日志类型都显示此项。</span><span class="sxs-lookup"><span data-stu-id="027a8-143">This does not appear for all log types.</span></span>  
  
 <span data-ttu-id="027a8-144">**消息**</span><span class="sxs-lookup"><span data-stu-id="027a8-144">**Message**</span></span>  
 <span data-ttu-id="027a8-145">显示与事件相关联的任何消息。</span><span class="sxs-lookup"><span data-stu-id="027a8-145">Displays any messages associated with the event.</span></span>  
  
 <span data-ttu-id="027a8-146">**日志类型**</span><span class="sxs-lookup"><span data-stu-id="027a8-146">**Log Type**</span></span>  
 <span data-ttu-id="027a8-147">显示事件所属的日志类型。</span><span class="sxs-lookup"><span data-stu-id="027a8-147">Displays the type of log to which the event belongs.</span></span> <span data-ttu-id="027a8-148">所有选定的日志都显示在日志文件摘要窗口中。</span><span class="sxs-lookup"><span data-stu-id="027a8-148">All selected logs appear in the log file summary window.</span></span>  
  
 <span data-ttu-id="027a8-149">**日志源**</span><span class="sxs-lookup"><span data-stu-id="027a8-149">**Log Source**</span></span>  
 <span data-ttu-id="027a8-150">显示在其中捕获事件的源日志的说明。</span><span class="sxs-lookup"><span data-stu-id="027a8-150">Displays a description of the source log in which the event is captured.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="027a8-151">权限</span><span class="sxs-lookup"><span data-stu-id="027a8-151">Permissions</span></span>  
 <span data-ttu-id="027a8-152">若要访问 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 联机实例的日志文件，你需要有 securityadmin 固定服务器角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="027a8-152">To access log files for instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that are online, this requires membership in the securityadmin fixed server role.</span></span>  
  
 <span data-ttu-id="027a8-153">若要访问 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 脱机实例的日志文件，不仅必须具有 **Root\Microsoft\SqlServer\ComputerManagement10** WMI 命名空间的读取权限，还必须具有存储日志文件的文件夹的读取权限。</span><span class="sxs-lookup"><span data-stu-id="027a8-153">To access log files for instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that are offline, you must have read access to both the **Root\Microsoft\SqlServer\ComputerManagement10** WMI namespace, and to the folder where the log files are stored.</span></span> <span data-ttu-id="027a8-154">有关详细信息，请参阅 [查看脱机日志文件](view-offline-log-files.md)主题的“安全性”部分。</span><span class="sxs-lookup"><span data-stu-id="027a8-154">For more information, see the Security section of the topic [View Offline Log Files](view-offline-log-files.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="027a8-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="027a8-155">See Also</span></span>  
 <span data-ttu-id="027a8-156">[日志文件查看器](log-file-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="027a8-156">[Log File Viewer](log-file-viewer.md) </span></span>  
 <span data-ttu-id="027a8-157">[打开日志文件查看器](open-log-file-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="027a8-157">[Open Log File Viewer](open-log-file-viewer.md) </span></span>  
 [<span data-ttu-id="027a8-158">查看脱机日志文件</span><span class="sxs-lookup"><span data-stu-id="027a8-158">View Offline Log Files</span></span>](view-offline-log-files.md)  
  
  
