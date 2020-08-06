---
title: 在对象资源管理器中管理事件会话 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
ms.assetid: 16849e38-d3fb-414d-8dcb-797b5ffce6ee
author: rothja
ms.author: jroth
ms.openlocfilehash: 1aa33a97137f63348898e6b1fcb7b19b2d218573
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577657"
---
# <a name="manage-event-sessions-in-the-object-explorer"></a><span data-ttu-id="ae00b-102">在对象资源管理器中管理事件会话</span><span class="sxs-lookup"><span data-stu-id="ae00b-102">Manage Event Sessions in the Object Explorer</span></span>
  <span data-ttu-id="ae00b-103">本主题讨论您可以在 **“对象资源管理器”** 中执行的将影响扩展事件的操作：</span><span class="sxs-lookup"><span data-stu-id="ae00b-103">This topic discusses the actions you can take in **Object Explorer** that affect Extended Events:</span></span>  
  
-   <span data-ttu-id="ae00b-104">创建扩展事件会话</span><span class="sxs-lookup"><span data-stu-id="ae00b-104">Create an Extended Events Session</span></span>  
  
-   <span data-ttu-id="ae00b-105">开始或停止扩展事件会话</span><span class="sxs-lookup"><span data-stu-id="ae00b-105">Starting or Stopping an Extended Events Session</span></span>  
  
-   <span data-ttu-id="ae00b-106">导出扩展事件会话</span><span class="sxs-lookup"><span data-stu-id="ae00b-106">Export an Extended Events Session</span></span>  
  
-   <span data-ttu-id="ae00b-107">导入扩展事件会话模板</span><span class="sxs-lookup"><span data-stu-id="ae00b-107">Import an Extended Events Session Template</span></span>  
  
-   <span data-ttu-id="ae00b-108">编辑扩展事件会话</span><span class="sxs-lookup"><span data-stu-id="ae00b-108">Edit an Extended Events Session</span></span>  
  
-   <span data-ttu-id="ae00b-109">删除扩展事件会话</span><span class="sxs-lookup"><span data-stu-id="ae00b-109">Delete an Extended Events Session</span></span>  
  
## <a name="create-an-extended-events-session"></a><span data-ttu-id="ae00b-110">创建扩展事件会话</span><span class="sxs-lookup"><span data-stu-id="ae00b-110">Create an Extended Events Session</span></span>  
 <span data-ttu-id="ae00b-111">有关创建扩展事件会话的详细信息，请参阅 [Create an Extended Events Session](../../database-engine/create-an-extended-events-session.md)。</span><span class="sxs-lookup"><span data-stu-id="ae00b-111">For more information about creating an Extended Events session, see [Create an Extended Events Session](../../database-engine/create-an-extended-events-session.md).</span></span>  
  
## <a name="starting-or-stopping-an-extended-events-session"></a><span data-ttu-id="ae00b-112">开始或停止扩展事件会话</span><span class="sxs-lookup"><span data-stu-id="ae00b-112">Starting or Stopping an Extended Events Session</span></span>  
 <span data-ttu-id="ae00b-113">您可以使用**Query Editor** `ALTER EVENT SESSION` 语句或使用**对象资源管理器**的 "**扩展事件**" 节点，通过查询编辑器启动或停止扩展事件会话。</span><span class="sxs-lookup"><span data-stu-id="ae00b-113">You can start or stop an Extended Events session through the **Query Editor** using the `ALTER EVENT SESSION` statement, or by using the **Extended Events** node of **Object Explorer**.</span></span>  
  
 <span data-ttu-id="ae00b-114">在你停止某一事件会话后，该会话在 sys.dm_xe_sessions 动态管理视图 (DMV) 中不再作为活动会话列出。</span><span class="sxs-lookup"><span data-stu-id="ae00b-114">When you stop an event session, the session is no longer listed as an active session in the sys.dm_xe_sessions dynamic management view (DMV).</span></span> <span data-ttu-id="ae00b-115">但是，会话定义保持不变，并且您可以重新启动该会话。</span><span class="sxs-lookup"><span data-stu-id="ae00b-115">However, the session definition remains intact, and you can restart the session.</span></span> <span data-ttu-id="ae00b-116">若要完全删除某一会话定义，您必须删除该会话。</span><span class="sxs-lookup"><span data-stu-id="ae00b-116">To completely remove a session definition, you must delete the session.</span></span>  
  
 <span data-ttu-id="ae00b-117">若要启动或停止扩展事件会话，您必须拥有 ALTER ANY EVENT SESSION 权限。</span><span class="sxs-lookup"><span data-stu-id="ae00b-117">To start or stop an Extended Events session, you must have the ALTER ANY EVENT SESSION permission.</span></span>  
  
 <span data-ttu-id="ae00b-118">当你停止使用内存中目标（例如环形缓冲区、存储桶、事件配对或同步事件计数器目标）的会话时，在该会话的缓冲区中存储的所有信息（sys.dm_xe_session_targets DMV 的 target_data 列）将会丢失。</span><span class="sxs-lookup"><span data-stu-id="ae00b-118">When you stop a session that uses an in-memory target, such as the ring buffer, bucketing, event pairing, or synchronous event counter targets, all the information stored in the session's buffer (the target_data column of the sys.dm_xe_session_targets DMV) will be lost.</span></span> <span data-ttu-id="ae00b-119">若要在停止该会话后访问事件数据，则应在停止该会话之前保存数据，或者配置该会话以使用文件目标。</span><span class="sxs-lookup"><span data-stu-id="ae00b-119">To access event data after you stop the session, you should either save the data before you stop the session, or configure the session to use the file target.</span></span>  
  
### <a name="start-or-stop-an-extended-events-session-using-query-editor"></a><span data-ttu-id="ae00b-120">使用查询编辑器启动或停止扩展事件会话</span><span class="sxs-lookup"><span data-stu-id="ae00b-120">Start or Stop an Extended Events Session Using Query Editor</span></span>  
 <span data-ttu-id="ae00b-121">若要启用某一会话，请发出以下语句，使用扩展事件会话的名称替换 *session_name* ：</span><span class="sxs-lookup"><span data-stu-id="ae00b-121">To start a session, issue the following statements, replacing *session_name* with the name of the Extended Events session:</span></span>  
  
```  
ALTER EVENT SESSION [session_name]  
ON SERVER  
STATE = START  
```  
  
 <span data-ttu-id="ae00b-122">若要停止某一会话，请发出以下语句，使用扩展事件会话的名称替换 *session_name* ：</span><span class="sxs-lookup"><span data-stu-id="ae00b-122">To stop a session, issue the following statements, replacing *session_name* with the name of the Extended Events session:</span></span>  
  
```  
ALTER EVENT SESSION [session_name]  
ON SERVER  
STATE = STOP  
```  
  
### <a name="start-or-stop-an-extended-events-session-in-object-explorer"></a><span data-ttu-id="ae00b-123">在对象资源管理器中启动或停止扩展事件会话</span><span class="sxs-lookup"><span data-stu-id="ae00b-123">Start or Stop an Extended Events Session in Object Explorer</span></span>  
 <span data-ttu-id="ae00b-124">若要在 **“对象资源管理器”** 中启动或停止扩展事件会话，则依次展开 **“管理”** 、 **“扩展事件”** 和“会话”  节点，右键单击所需的会话，然后单击 **“启动会话”** 或 **“停止会话”** 。</span><span class="sxs-lookup"><span data-stu-id="ae00b-124">To start or stop an Extended Events session in **Object Explorer**, expand the **Management**, **Extended Events**, and then **Sessions** nodes and right click on a session and then click **Start Session** or **Stop Session**.</span></span>  
  
## <a name="export-an-extended-events-session-template"></a><span data-ttu-id="ae00b-125">导出扩展事件会话模板</span><span class="sxs-lookup"><span data-stu-id="ae00b-125">Export an Extended Events Session Template</span></span>  
 <span data-ttu-id="ae00b-126">可以使用 **“对象资源管理器”** 导出扩展事件会话，并将它保存为 .xml 模板文件。</span><span class="sxs-lookup"><span data-stu-id="ae00b-126">You can export an Extended Events session using **Object Explorer**, and save it as an .xml template file.</span></span> <span data-ttu-id="ae00b-127">例如，您可能要导出会话，然后使用 **“新建会话向导”** 或 **“新建会话”** 对话框将模板应用到新的事件会话。</span><span class="sxs-lookup"><span data-stu-id="ae00b-127">For example, you may want to export a session and then apply the template to a new event session using the **New Session Wizard** or the **New Session** wizard.</span></span>  
  
 <span data-ttu-id="ae00b-128">导出会话时，确保将模板文件保存到使用 NTFS 文件系统的某个位置，并且只允许有权查看该信息的用户对其进行访问。</span><span class="sxs-lookup"><span data-stu-id="ae00b-128">When you export a session, make sure that you save the template file to a location that uses the NTFS file system, and that you restrict access to users who are authorized to view the information.</span></span>  
  
 <span data-ttu-id="ae00b-129">在 **“对象资源管理器”** 中导出扩展事件会话：</span><span class="sxs-lookup"><span data-stu-id="ae00b-129">To export an Extended Events session in **Object Explorer**:</span></span>  
  
1.  <span data-ttu-id="ae00b-130">依次展开 **“管理”** 、 **“扩展事件”** 和 **“会话”** 节点。</span><span class="sxs-lookup"><span data-stu-id="ae00b-130">Expand the **Management**, **Extended Events**, and then **Sessions** nodes</span></span>  
  
2.  <span data-ttu-id="ae00b-131">右键单击要导出的会话，然后选择“导出会话”。</span><span class="sxs-lookup"><span data-stu-id="ae00b-131">Right-click the session that you want to export, and select **Export Session**.</span></span>  
  
3.  <span data-ttu-id="ae00b-132">在 **“另存为”** 对话框中选择保存文件的位置，在 **“文件名”** 框中键入文件名，然后单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="ae00b-132">In the **Save As** dialog box, select a location to save the file, type the file name in the **File name** box, and then click **Save**.</span></span>  
  
     <span data-ttu-id="ae00b-133">如果您将文件保存到默认的 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 模板位置，则当您使用 **“新建会话向导”** 和 **“新建会话”** 对话框时，该模板将出现在预定义模板的下拉列表中。</span><span class="sxs-lookup"><span data-stu-id="ae00b-133">If you save the file to the default [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] template location, the template will appear in the dropdown list of predefined templates when you use the **New Session Wizard** and **New Session** dialog.</span></span>  
  
## <a name="import-an-extended-events-session-template"></a><span data-ttu-id="ae00b-134">导入扩展事件会话模板</span><span class="sxs-lookup"><span data-stu-id="ae00b-134">Import an Extended Events Session Template</span></span>  
 <span data-ttu-id="ae00b-135">通过使用 **“对象资源管理器”** ，您可导入扩展事件会话的模板。</span><span class="sxs-lookup"><span data-stu-id="ae00b-135">Using **Object Explorer**, you can import a template for an Extended Events session.</span></span> <span data-ttu-id="ae00b-136">例如，您可能希望执行此操作以利用从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的其他实例导出的模板创建会话。</span><span class="sxs-lookup"><span data-stu-id="ae00b-136">For example, you may want to do this to create a session from a template that was exported from another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="ae00b-137">若要导入扩展事件会话，则您必须具有必要的 `ALTER ANY EVENT SESSION` 权限。</span><span class="sxs-lookup"><span data-stu-id="ae00b-137">To import an Extended Events session, you must have the necessary `ALTER ANY EVENT SESSION` permissions.</span></span>  
  
 <span data-ttu-id="ae00b-138">在您导入模板文件之前，确保该文件来自受信任的源。</span><span class="sxs-lookup"><span data-stu-id="ae00b-138">Before you import a template file, make sure that the file is from a trusted source.</span></span> <span data-ttu-id="ae00b-139">应将模板文件保存到一个使用 NTFS 文件系统的位置，并限制只有获得授权查看信息的用户才可以访问该位置。</span><span class="sxs-lookup"><span data-stu-id="ae00b-139">Template files should be saved to a location that uses the NTFS file system and where access is restricted to users who are authorized to view the information.</span></span>  
  
 <span data-ttu-id="ae00b-140">若要导入扩展事件会话：</span><span class="sxs-lookup"><span data-stu-id="ae00b-140">To import an Extended Events session:</span></span>  
  
1.  <span data-ttu-id="ae00b-141">在 **“对象资源管理器”** 中，依次展开 **“管理”** 和 **“扩展事件”** 节点。</span><span class="sxs-lookup"><span data-stu-id="ae00b-141">In **Object Explorer**, expand the **Management**, and then **Extended Events** nodes.</span></span>  
  
2.  <span data-ttu-id="ae00b-142">右键单击“会话”，然后选择“新建会话”。</span><span class="sxs-lookup"><span data-stu-id="ae00b-142">Right-click **Sessions** and select **New Session**.</span></span>  
  
3.  <span data-ttu-id="ae00b-143">指定会话的名称。</span><span class="sxs-lookup"><span data-stu-id="ae00b-143">Specify a name for the session.</span></span>  
  
4.  <span data-ttu-id="ae00b-144">展开 **“模板”** 下拉框。</span><span class="sxs-lookup"><span data-stu-id="ae00b-144">Expand the **Template** drop down box.</span></span>  
  
5.  <span data-ttu-id="ae00b-145">单击“\<File From ...>打开”并通过浏览找到要导入的会话（XML 文件）。</span><span class="sxs-lookup"><span data-stu-id="ae00b-145">Click **\<File From ...>Open** and browse for the session (XML file) you want to import.</span></span>  
  
 <span data-ttu-id="ae00b-146">会话将出现在 **“会话”** 节点下。</span><span class="sxs-lookup"><span data-stu-id="ae00b-146">The session appears under the **Sessions** node.</span></span> <span data-ttu-id="ae00b-147">默认情况下，不会启动会话。</span><span class="sxs-lookup"><span data-stu-id="ae00b-147">By default, the session is not started.</span></span>  
  
## <a name="edit-an-extended-events-session"></a><span data-ttu-id="ae00b-148">编辑扩展事件会话</span><span class="sxs-lookup"><span data-stu-id="ae00b-148">Edit an Extended Events Session</span></span>  
 <span data-ttu-id="ae00b-149">您可在“对象资源管理器”中编辑扩展事件会话。</span><span class="sxs-lookup"><span data-stu-id="ae00b-149">You can edit an Extended Events session in Object Explorer.</span></span>  
  
 <span data-ttu-id="ae00b-150">编辑扩展事件会话：</span><span class="sxs-lookup"><span data-stu-id="ae00b-150">To edit an Extended Events session:</span></span>  
  
1.  <span data-ttu-id="ae00b-151">在 **“对象资源管理器”** 中，依次展开 **“管理”** 、 **“扩展事件”** 和 **“会话”** 节点。</span><span class="sxs-lookup"><span data-stu-id="ae00b-151">In **Object Explorer**, expand the **Management**, **Extended Events**, and then **Sessions** nodes.</span></span>  
  
2.  <span data-ttu-id="ae00b-152">右键单击一个会话，然后选择“属性”。</span><span class="sxs-lookup"><span data-stu-id="ae00b-152">Right-click a session and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="ae00b-153">在 **“选择页”** 部分，选择您要编辑的页。</span><span class="sxs-lookup"><span data-stu-id="ae00b-153">In the **Select a page** section, select the page or pages you want to edit.</span></span>  
  
4.  <span data-ttu-id="ae00b-154">在完成对事件会话的修改后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="ae00b-154">After you finish revising the event session, click **OK**.</span></span>  
  
## <a name="script-an-event-session-definition-using-tsql"></a><span data-ttu-id="ae00b-155">使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae00b-155">Script an Event Session Definition Using [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
 <span data-ttu-id="ae00b-156">“新建会话向导”和“新建会话”对话框都包含一个可用于生成定义扩展事件会话的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 的“脚本”选项。</span><span class="sxs-lookup"><span data-stu-id="ae00b-156">Both the New Session Wizard and the New Session dialog have a Script option that generates the [!INCLUDE[tsql](../../includes/tsql-md.md)] that defines the Extended Events session.</span></span>  
  
 <span data-ttu-id="ae00b-157">可以通过以下方法访问现有扩展事件会话的 [!INCLUDE[tsql](../../includes/tsql-md.md)] ：右键单击该会话名称，选择 **“编写会话脚本为”** ，然后再选择 **“CREATE 到”** 。</span><span class="sxs-lookup"><span data-stu-id="ae00b-157">You can access the [!INCLUDE[tsql](../../includes/tsql-md.md)] for an existing Extended Events session by right clicking the session name, selecting **Script Session as**, and then selecting **Create to**.</span></span>  
  
## <a name="delete-an-extended-events-session"></a><span data-ttu-id="ae00b-158">删除扩展事件会话</span><span class="sxs-lookup"><span data-stu-id="ae00b-158">Delete an Extended Events Session</span></span>  
 <span data-ttu-id="ae00b-159">您可以删除扩展事件会话：</span><span class="sxs-lookup"><span data-stu-id="ae00b-159">You can delete an Extended Events session:</span></span>  
  
-   <span data-ttu-id="ae00b-160">在“查询编辑器”中使用 `DROP EVENT SESSION`。</span><span class="sxs-lookup"><span data-stu-id="ae00b-160">In Query Editor using `DROP EVENT SESSION`.</span></span>  
  
-   <span data-ttu-id="ae00b-161">在 **“对象资源管理器”** 中。</span><span class="sxs-lookup"><span data-stu-id="ae00b-161">In **Object Explorer**.</span></span>  
  
 <span data-ttu-id="ae00b-162">在你删除某一事件会话时，所有配置信息都将被删除，并且会话定义不再在 sys.server_event_sessions 目录视图中出现。</span><span class="sxs-lookup"><span data-stu-id="ae00b-162">When you delete an event session, all configuration information is removed and the session definition no longer appears in the sys.server_event_sessions catalog view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ae00b-163">system_health 和 AlwaysOn_health 包含在中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; 不要删除它们。</span><span class="sxs-lookup"><span data-stu-id="ae00b-163">system_health and AlwaysOn_health are included with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; do not delete them.</span></span> <span data-ttu-id="ae00b-164">默认情况下，将启用 system_health（有关详细信息，请参阅 [使用 system_health 会话](use-the-ssms-xe-profiler.md)）。</span><span class="sxs-lookup"><span data-stu-id="ae00b-164">system_health is enabled by default (for more information, see [Use the system_health Session](use-the-ssms-xe-profiler.md)).</span></span> <span data-ttu-id="ae00b-165">默认情况下，AlwaysOn_health 处于关闭状态。</span><span class="sxs-lookup"><span data-stu-id="ae00b-165">AlwaysOn_health is off by default.</span></span> <span data-ttu-id="ae00b-166">这些会话将收集可用于诊断性能问题的数据。</span><span class="sxs-lookup"><span data-stu-id="ae00b-166">These sessions collect data that can be useful for diagnosing performance issues.</span></span>  
  
 <span data-ttu-id="ae00b-167">若要删除某一扩展事件会话，您必须具有 ALTER ANY EVENT SESSION 权限。</span><span class="sxs-lookup"><span data-stu-id="ae00b-167">To delete an Extended Events session, you must have the ALTER ANY EVENT SESSION permission.</span></span>  
  
 <span data-ttu-id="ae00b-168">若要在 **“对象资源管理器”** 中删除扩展事件会话：</span><span class="sxs-lookup"><span data-stu-id="ae00b-168">To delete an Extended Events session in **Object Explorer**:</span></span>  
  
1.  <span data-ttu-id="ae00b-169">依次展开 **“管理”** 、 **“扩展事件”** 和 **“会话”** 节点。</span><span class="sxs-lookup"><span data-stu-id="ae00b-169">Expand the **Management**, **Extended Events**, and then **Sessions** nodes.</span></span>  
  
2.  <span data-ttu-id="ae00b-170">右键单击一个会话，然后选择“删除”。</span><span class="sxs-lookup"><span data-stu-id="ae00b-170">Right-click a session and select **Delete**.</span></span>  
  
3.  <span data-ttu-id="ae00b-171">在 **“删除对象”** 对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="ae00b-171">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
4.  <span data-ttu-id="ae00b-172">在完成对事件会话的修改后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="ae00b-172">After you finish revising the event session, click **OK**.</span></span>  
  
 <span data-ttu-id="ae00b-173">若要在“查询编辑器”中删除一个扩展事件会话，请发出以下语句，并将 *session_name* 替换为你要删除的扩展事件会话的名称：</span><span class="sxs-lookup"><span data-stu-id="ae00b-173">To delete an Extended Events session in the **Query Editor**, Issue the following statements, replacing *session_name* with the name of the Extended Events session that you want to delete:</span></span>  
  
```  
DROP EVENT SESSION [session_name]  
ON SERVER  
```  
  
  
