---
title: 设置警告阈值 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.setwarningthreshold.f1
ms.assetid: 17f93147-e7d9-4092-b4c2-c11b38051171
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2d5fd9c0213d74f3a6b5d0d4cb2f11d3531d336d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690092"
---
# <a name="set-warning-thresholds"></a><span data-ttu-id="9558b-102">设置警告阈值</span><span class="sxs-lookup"><span data-stu-id="9558b-102">Set Warning Thresholds</span></span>
  <span data-ttu-id="9558b-103">使用该对话框可为在 **“数据库镜像监视器”** 对话框的导航树中选定的数据库启用和配置一个或多个警告阈值。</span><span class="sxs-lookup"><span data-stu-id="9558b-103">Use this dialog box to enable and configure one or more warning thresholds for the database selected in the navigation tree of the **Database Mirroring Monitor** dialog box.</span></span>  
  
 <span data-ttu-id="9558b-104">该对话框尝试连接到两个服务器实例上。</span><span class="sxs-lookup"><span data-stu-id="9558b-104">The dialog box tries to connect to both server instances.</span></span> <span data-ttu-id="9558b-105">将异步建立这两个连接。</span><span class="sxs-lookup"><span data-stu-id="9558b-105">These connections are established asynchronously.</span></span> <span data-ttu-id="9558b-106">对话框显示每个伙伴的连接状态。</span><span class="sxs-lookup"><span data-stu-id="9558b-106">The dialog shows the connection status of each partner.</span></span> <span data-ttu-id="9558b-107">如果伙伴没有连接，则可单击 **“连接”** 。</span><span class="sxs-lookup"><span data-stu-id="9558b-107">If the partner is not connected, you can click **Connect**.</span></span>  
  
 <span data-ttu-id="9558b-108">**使用 SQL Server Management Studio 监视数据库镜像**</span><span class="sxs-lookup"><span data-stu-id="9558b-108">**To use SQL Server Management Studio to monitor database mirroring**</span></span>  
  
-   [<span data-ttu-id="9558b-109">启动数据库镜像监视器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9558b-109">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="options"></a><span data-ttu-id="9558b-110">选项</span><span class="sxs-lookup"><span data-stu-id="9558b-110">Options</span></span>  
 <span data-ttu-id="9558b-111">*服务器实例及其连接状态*</span><span class="sxs-lookup"><span data-stu-id="9558b-111">*Server instance and its connection status*</span></span>  
 <span data-ttu-id="9558b-112">伙伴服务器实例的名称，格式为_SYSTEM_ **\\** _INSTANCE_NAME_。</span><span class="sxs-lookup"><span data-stu-id="9558b-112">Name of a partner server instance in the form _SYSTEM_**\\**_INSTANCE_NAME_.</span></span> <span data-ttu-id="9558b-113">对于默认服务器实例，只显示系统名。</span><span class="sxs-lookup"><span data-stu-id="9558b-113">For a default server instance, only the system name is displayed.</span></span>  
  
 <span data-ttu-id="9558b-114">该字段还指示当前监视器是否连接至该服务器实例。</span><span class="sxs-lookup"><span data-stu-id="9558b-114">This field also indicates whether the monitor is currently connected to this server instance.</span></span> <span data-ttu-id="9558b-115">可能的连接状态为：</span><span class="sxs-lookup"><span data-stu-id="9558b-115">The possible connection statuses are:</span></span>  
  
-   <span data-ttu-id="9558b-116">未连接到 server_instance_name</span><span class="sxs-lookup"><span data-stu-id="9558b-116">**Not connected to**  *server_instance_name*</span></span>  
  
-   <span data-ttu-id="9558b-117">正尝试连接到 server_instance_name</span><span class="sxs-lookup"><span data-stu-id="9558b-117">**Trying to connect to**  *server_instance_name*</span></span>  
  
-   <span data-ttu-id="9558b-118">已连接到 server_instance_name</span><span class="sxs-lookup"><span data-stu-id="9558b-118">**Connected to**  *server_instance_name*</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9558b-119">如果你不是 sysadmin 固定服务器角色的成员，状态将为“已连接到 server_instance_name (受限权限)” 。</span><span class="sxs-lookup"><span data-stu-id="9558b-119">If you do are not a member of the **sysadmin** fixed server role, this status is **Connected to** *server_instance_name* **(Limited permissions)**.</span></span>  
  
 <span data-ttu-id="9558b-120">每个伙伴服务器实例的名称将在单独的 *“服务器实例及其连接状态”* 字段中显示。</span><span class="sxs-lookup"><span data-stu-id="9558b-120">The name of each of the partner server instances is displayed in a separate *Server instance and its connection status* field.</span></span> <span data-ttu-id="9558b-121">当监视器开始运行时，顶部字段会列出主体服务器。</span><span class="sxs-lookup"><span data-stu-id="9558b-121">The top field lists the principal server when the monitor started running.</span></span>  
  
 <span data-ttu-id="9558b-122">**连接**/**取消**</span><span class="sxs-lookup"><span data-stu-id="9558b-122">**Connect**/**Cancel**</span></span>  
 <span data-ttu-id="9558b-123">“连接/取消” 按钮和每个*服务器实例及其连接状态*字段相关联。</span><span class="sxs-lookup"><span data-stu-id="9558b-123">A **Connect**/**Cancel** button is associated with each *Server instance and its connection status* fields.</span></span> <span data-ttu-id="9558b-124">按钮状态取决于连接状态：</span><span class="sxs-lookup"><span data-stu-id="9558b-124">The state of the button depends on the connection status:</span></span>  
  
-   <span data-ttu-id="9558b-125">如果未与服务器实例建立连接，则按钮文本为 **“连接”** 。</span><span class="sxs-lookup"><span data-stu-id="9558b-125">If there is no connection to the server instance, the button text is **Connect**.</span></span> <span data-ttu-id="9558b-126">单击可连接到服务器实例。</span><span class="sxs-lookup"><span data-stu-id="9558b-126">Click to connect to the server instance.</span></span>  
  
-   <span data-ttu-id="9558b-127">当正在进行连接尝试时，按钮文本为 **“取消”** 。</span><span class="sxs-lookup"><span data-stu-id="9558b-127">When a connection attempt is in progress, the button text is **Cancel**.</span></span> <span data-ttu-id="9558b-128">单击可取消连接尝试。</span><span class="sxs-lookup"><span data-stu-id="9558b-128">Click to cancel the connection attempt.</span></span>  
  
-   <span data-ttu-id="9558b-129">如果服务器已连接，按钮文本为 **“已连接”** ，并且该按钮呈灰色。</span><span class="sxs-lookup"><span data-stu-id="9558b-129">If the server is connected, the button text is **Connected**, and the button is dimmed.</span></span>  
  
 <span data-ttu-id="9558b-130">**Thresholds**</span><span class="sxs-lookup"><span data-stu-id="9558b-130">**Thresholds**</span></span>  
 <span data-ttu-id="9558b-131">**阈值** 网格显示两个服务器实例的警告设置。</span><span class="sxs-lookup"><span data-stu-id="9558b-131">The **Thresholds** grid displays the warnings settings for the two server instances.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9558b-132">如果服务器实例未连接，它的列将显示为空单元格和灰色背景。</span><span class="sxs-lookup"><span data-stu-id="9558b-132">If a server instance is not connected, its columns are displayed with empty cells and a gray background.</span></span> <span data-ttu-id="9558b-133">当连接打开时，网格将自动显示来自实例的内容。</span><span class="sxs-lookup"><span data-stu-id="9558b-133">When the connection opens, the grid automatically displays the content from the instance.</span></span>  
  
 <span data-ttu-id="9558b-134">该网格包含以下列：</span><span class="sxs-lookup"><span data-stu-id="9558b-134">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="9558b-135">**警告**</span><span class="sxs-lookup"><span data-stu-id="9558b-135">**Warnings**</span></span>  
 <span data-ttu-id="9558b-136">列出所支持的警告：</span><span class="sxs-lookup"><span data-stu-id="9558b-136">Lists the supported warnings:</span></span>  
  
|<span data-ttu-id="9558b-137">警告</span><span class="sxs-lookup"><span data-stu-id="9558b-137">Warning</span></span>|<span data-ttu-id="9558b-138">说明</span><span class="sxs-lookup"><span data-stu-id="9558b-138">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9558b-139">**如果未发送日志超出了阈值，则发出警告**</span><span class="sxs-lookup"><span data-stu-id="9558b-139">**Warn if the unsent log exceeds the threshold**</span></span>|<span data-ttu-id="9558b-140">该阈值指示在主体服务器的发送队列中未发送日志的 KB 值。</span><span class="sxs-lookup"><span data-stu-id="9558b-140">The threshold indicates the number of kilobytes (KB) of the unsent log in the send queue on the principal.</span></span>|  
|<span data-ttu-id="9558b-141">**如果未还原日志超出了阈值，则发出警告**</span><span class="sxs-lookup"><span data-stu-id="9558b-141">**Warn if the unrestored log exceeds the threshold**</span></span>|<span data-ttu-id="9558b-142">该阈值指示在镜像服务器实例中重做队列的 KB 值。</span><span class="sxs-lookup"><span data-stu-id="9558b-142">The threshold indicates the number of KB of the redo queue on the mirror server instance.</span></span>|  
|<span data-ttu-id="9558b-143">**如果最早的未发送事务的保留时间超出了阈值，则发出警告**</span><span class="sxs-lookup"><span data-stu-id="9558b-143">**Warn if the age of the oldest unsent transaction exceeds the threshold**</span></span>|<span data-ttu-id="9558b-144">该阈值指示事务没有从发送队列发送到镜像服务器实例中的分钟数。</span><span class="sxs-lookup"><span data-stu-id="9558b-144">The threshold indicates the number of minutes of transactions that have not yet been sent from the send queue to the mirror server instance.</span></span> <span data-ttu-id="9558b-145">该值有助于测量数据丢失的可能性（以时间计）。</span><span class="sxs-lookup"><span data-stu-id="9558b-145">This value helps measure the potential for data loss in terms of time.</span></span>|  
|<span data-ttu-id="9558b-146">**如果镜像提交开销超过了阈值则发出警告**</span><span class="sxs-lookup"><span data-stu-id="9558b-146">**Warn if the mirror commit overhead exceeds the threshold**</span></span>|<span data-ttu-id="9558b-147">该阈值指示每个事务的延迟的毫秒数（只适用于高安全模式）。</span><span class="sxs-lookup"><span data-stu-id="9558b-147">The threshold indicates the number of milliseconds of delay per transaction (relevant only in high-safety mode).</span></span> <span data-ttu-id="9558b-148">此延迟是主体服务器实例等待镜像服务器实例将事务日志记录写入重做队列时，所发生的开销量。</span><span class="sxs-lookup"><span data-stu-id="9558b-148">This delay is the amount of overhead incurred while the principal server instance waits for the mirror server instance to write the transaction's log record into the redo queue.</span></span>|  
  
 <span data-ttu-id="9558b-149">已在“\<server instance>”中启用</span><span class="sxs-lookup"><span data-stu-id="9558b-149">**Enabled at '** *\<server instance>* **'**</span></span>  
 <span data-ttu-id="9558b-150">空白复选框指示当前在服务器实例中禁用该警告。</span><span class="sxs-lookup"><span data-stu-id="9558b-150">A blank check box indicates that the warning is currently disabled on the server instance.</span></span> <span data-ttu-id="9558b-151">若要启用警告，请单击其复选框。</span><span class="sxs-lookup"><span data-stu-id="9558b-151">To enable a warning, click its check box.</span></span>  
  
 <span data-ttu-id="9558b-152">“\<server instance>”的阈值</span><span class="sxs-lookup"><span data-stu-id="9558b-152">**Threshold at '** *\<server instance>* **'**</span></span>  
 <span data-ttu-id="9558b-153">启用警告时，可在该列的左边设置阈值。</span><span class="sxs-lookup"><span data-stu-id="9558b-153">When a warning is enabled, set the threshold on the left side of this column.</span></span> <span data-ttu-id="9558b-154">更新状态表时，如果达到指定阈值，则会触发事件。</span><span class="sxs-lookup"><span data-stu-id="9558b-154">An event occurs if the specified threshold has been reached when the status table is updated.</span></span> <span data-ttu-id="9558b-155">如果在配置一个值后禁用阈值，该值将保留在字段中。如果重新启用警告，将继续使用该值。</span><span class="sxs-lookup"><span data-stu-id="9558b-155">If you disable a threshold after configuring a value, your value remains in this field and will be used if you re-enable the warning.</span></span>  
  
 <span data-ttu-id="9558b-156">未启用警告时，该字段将处于不活动状态。</span><span class="sxs-lookup"><span data-stu-id="9558b-156">When a warning is not enabled, this field is inactive.</span></span>  
  
 <span data-ttu-id="9558b-157">**确定**</span><span class="sxs-lookup"><span data-stu-id="9558b-157">**OK**</span></span>  
 <span data-ttu-id="9558b-158">单击“确定”可关闭此对话框，并显示当前在“警告”选项卡式页的“阈值”网格中指定的警告阈值。</span><span class="sxs-lookup"><span data-stu-id="9558b-158">Clicking **OK** closes this dialog box and displays the currently specified values of warning thresholds in the **Thresholds** grid on the **Warnings**tabbed page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9558b-159">备注</span><span class="sxs-lookup"><span data-stu-id="9558b-159">Remarks</span></span>  
 <span data-ttu-id="9558b-160">在同一时间阈值只适用于一个伙伴，但我们建议您在两个伙伴上都为给定事件设置阈值，以确保数据库进行故障转移时，警告仍然存在。</span><span class="sxs-lookup"><span data-stu-id="9558b-160">A threshold is only applicable at one partner at a time, but we recommend that you set a threshold for a given event on both partners to ensure that the warning persists if the database fails over.</span></span> <span data-ttu-id="9558b-161">每个伙伴的相应阈值取决于伙伴系统的性能。</span><span class="sxs-lookup"><span data-stu-id="9558b-161">The appropriate threshold for each partner depends on the performance capabilities of that partner's system.</span></span>  
  
 <span data-ttu-id="9558b-162">更新状态表时，只有在性能值处于或高于阈值的情况下，才会将事件写入性能的事件日志。</span><span class="sxs-lookup"><span data-stu-id="9558b-162">An event is written to the event log for a performance only if its value is at or above its threshold when the status table is being updated.</span></span> <span data-ttu-id="9558b-163">如果峰值在两次状态更新之间瞬间达到阈值，峰值将丢失。</span><span class="sxs-lookup"><span data-stu-id="9558b-163">If a peak value reaches the threshold momentarily between status updates that peak is missed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9558b-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9558b-164">See Also</span></span>  
 <span data-ttu-id="9558b-165">[启动数据库镜像监视器 (SQL Server Management Studio)](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="9558b-165">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="9558b-166">[监视数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9558b-166">[Monitoring Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="9558b-167">启动配置数据库镜像安全向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9558b-167">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
  
