---
title: "\"配置 SSIS 日志\" 对话框 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.configuredtslogs.loggingdetails.f1
- sql12.dts.designer.configuredtslogs.providersandlogs.f1
- sql12.dts.designer.configuredtslogs.containers.f1
helpviewer_keywords:
- Configure SSIS Logs dialog box
ms.assetid: 4b980275-cd9a-4943-8c36-727d51f9a484
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 252b45765fb784790bcca0fb86e2e56e7e7baddc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580826"
---
# <a name="configure-ssis-logs-dialog-box"></a><span data-ttu-id="f4fcc-102">“配置 SSIS 日志”对话框</span><span class="sxs-lookup"><span data-stu-id="f4fcc-102">Configure SSIS Logs Dialog Box</span></span>
  <span data-ttu-id="f4fcc-103">使用 **“配置 SSIS 日志”** 对话框可以定义包的日志记录选项。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-103">Use the **Configure SSIS Logs** dialog box to define logging options for a package.</span></span>  
  
 <span data-ttu-id="f4fcc-104">**您希望做什么？**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-104">**What do you want to do?**</span></span>  
  
1.  [<span data-ttu-id="f4fcc-105">打开“配置 SSIS 日志”对话框</span><span class="sxs-lookup"><span data-stu-id="f4fcc-105">Open the Configure SSIS Logs Dialog Box</span></span>](#open_dialog)  
  
2.  [<span data-ttu-id="f4fcc-106">配置“容器”窗格中的选项</span><span class="sxs-lookup"><span data-stu-id="f4fcc-106">Configure the Options in the Containers Pane</span></span>](#container)  
  
3.  [<span data-ttu-id="f4fcc-107">配置“提供程序和日志”选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="f4fcc-107">Configure the Options on the Providers and Logs Tab</span></span>](#provider)  
  
4.  [<span data-ttu-id="f4fcc-108">配置“详细信息”选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="f4fcc-108">Configure the Options on the Details Tab</span></span>](#detail)  
  
##  <a name="open-the-configure-ssis-logs-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="f4fcc-109">打开“配置 SSIS 日志”对话框</span><span class="sxs-lookup"><span data-stu-id="f4fcc-109">Open the Configure SSIS Logs Dialog Box</span></span>  
 <span data-ttu-id="f4fcc-110">**打开“配置 SSIS 日志”对话框**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-110">**To open the Configure SSIS Logs dialog box**</span></span>  
  
-   <span data-ttu-id="f4fcc-111">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器的 **SSIS** 菜单上，单击 **“日志记录”** 。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-111">In the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click **Logging** on the **SSIS** menu.</span></span>  
  
##  <a name="configure-the-options-in-the-containers-pane"></a><a name="container"></a> <span data-ttu-id="f4fcc-112">配置“容器”窗格中的选项</span><span class="sxs-lookup"><span data-stu-id="f4fcc-112">Configure the Options in the Containers Pane</span></span>  
 <span data-ttu-id="f4fcc-113">可以使用 **“配置 SSIS 日志”** 对话框的 **“容器”** 窗格，为包及其容器启用日志记录。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-113">Use the **Containers** pane of the **Configure SSIS Logs** dialog box to enable the package and its containers for logging.</span></span>  
  
### <a name="options"></a><span data-ttu-id="f4fcc-114">选项</span><span class="sxs-lookup"><span data-stu-id="f4fcc-114">Options</span></span>  
 <span data-ttu-id="f4fcc-115">**容器**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-115">**Containers**</span></span>  
 <span data-ttu-id="f4fcc-116">选中层次结构视图中的该复选框可以为日志记录启用包和包容器：</span><span class="sxs-lookup"><span data-stu-id="f4fcc-116">Select the check boxes in the hierarchical view to enable the package and its containers for logging:</span></span>  
  
-   <span data-ttu-id="f4fcc-117">如果清除此复选框，则不会为日志记录启用容器。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-117">If cleared, the container is not enabled for logging.</span></span> <span data-ttu-id="f4fcc-118">选中此复选框将启用日志记录。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-118">Select to enable logging.</span></span>  
  
-   <span data-ttu-id="f4fcc-119">如果此复选框为灰色，则容器将使用其父容器的日志记录选项。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-119">If dimmed, the container uses the logging options of its parent.</span></span> <span data-ttu-id="f4fcc-120">此选项对包不可用。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-120">This option is not available for the package.</span></span>  
  
-   <span data-ttu-id="f4fcc-121">如果选中此复选框，那么容器将定义自己的日志记录选项。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-121">If checked, the container defines its own logging options.</span></span>  
  
 <span data-ttu-id="f4fcc-122">如果容器为灰色，而您想要设置该容器的日志记录选项，请单击对应复选框两次。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-122">If a container is dimmed and you want to set logging options on the container, click its check box twice.</span></span> <span data-ttu-id="f4fcc-123">第一次单击将清除该复选框，第二次单击将选中该复选框，这样您就可以选择要使用的日志提供程序以及要记录的信息。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-123">The first click clears the check box, and the second click selects it, enabling you to choose the log providers to use and select the information to log.</span></span>  
  
##  <a name="configure-the-options-on-the-providers-and-logs-tab"></a><a name="provider"></a> <span data-ttu-id="f4fcc-124">配置“提供程序和日志”选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="f4fcc-124">Configure the Options on the Providers and Logs Tab</span></span>  
 <span data-ttu-id="f4fcc-125">可以使用“配置 SSIS 日志”对话框的“提供程序和日志”选项卡，创建和配置用于捕获运行时事件的日志。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-125">Use the **Providers and Logs** tab of the **Configure SSIS Logs** dialog box to create and configure logs for capturing run-time events.</span></span>  
  
### <a name="options"></a><span data-ttu-id="f4fcc-126">选项</span><span class="sxs-lookup"><span data-stu-id="f4fcc-126">Options</span></span>  
 <span data-ttu-id="f4fcc-127">**提供程序类型**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-127">**Provider type**</span></span>  
 <span data-ttu-id="f4fcc-128">从列表中选择日志提供程序的类型。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-128">Select a type of log provider from the list.</span></span>  
  
 <span data-ttu-id="f4fcc-129">**添加**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-129">**Add**</span></span>  
 <span data-ttu-id="f4fcc-130">将指定类型的日志添加到包的日志提供程序集合中。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-130">Add a log of the specified type to the collection of log providers of the package.</span></span>  
  
 <span data-ttu-id="f4fcc-131">**名称**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-131">**Name**</span></span>  
 <span data-ttu-id="f4fcc-132">通过使用复选框，可以为在“配置 SSIS 日志”对话框的“容器”窗格中选择的容器或任务启用或禁用日志。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-132">Enable or disable logs for containers or tasks selected in the **Containers** pane of the **Configure SSIS Logs** dialog box, by using the check boxes.</span></span> <span data-ttu-id="f4fcc-133">名称字段是可编辑的。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-133">The name field is editable.</span></span> <span data-ttu-id="f4fcc-134">可以使用提供程序的默认名称，也可以键入唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-134">Use the default name for the provider, or type a unique descriptive name.</span></span>  
  
 <span data-ttu-id="f4fcc-135">**说明**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-135">**Description**</span></span>  
 <span data-ttu-id="f4fcc-136">说明字段是可编辑的。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-136">The description field is editable.</span></span> <span data-ttu-id="f4fcc-137">可以单击该字段，然后修改日志的默认说明。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-137">Click and then modify the default description of the log.</span></span>  
  
 <span data-ttu-id="f4fcc-138">**配置**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-138">**Configuration**</span></span>  
 <span data-ttu-id="f4fcc-139">从列表中选择现有的连接管理器，或单击“\<**New connection...**>”创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-139">Select an existing connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span> <span data-ttu-id="f4fcc-140">根据日志提供程序的类型，您可以配置 OLE DB 连接管理器或文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-140">Depending on the type of log provider, you can configure an OLE DB connection manager or a File connection manager.</span></span> <span data-ttu-id="f4fcc-141">[!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 事件日志的日志提供程序不需要任何连接。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-141">The log provider for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Event Log requires no connection.</span></span>  
  
 <span data-ttu-id="f4fcc-142">相关主题： [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md) 、 [File Connection Manager](connection-manager/file-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="f4fcc-142">Related Topics: [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md) manager, [File Connection Manager](connection-manager/file-connection-manager.md)</span></span>  
  
 <span data-ttu-id="f4fcc-143">**删除**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-143">**Delete**</span></span>  
 <span data-ttu-id="f4fcc-144">选择一个日志提供程序，然后单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-144">Select a log provider and then click **Delete**.</span></span>  
  
##  <a name="configure-the-options-on-the-details-tab"></a><a name="detail"></a> <span data-ttu-id="f4fcc-145">配置“详细信息”选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="f4fcc-145">Configure the Options on the Details Tab</span></span>  
 <span data-ttu-id="f4fcc-146">可以使用 **“配置 SSIS 日志”** 对话框的 **“详细信息”** 选项卡，指定要启用日志记录的事件以及要记录的详细信息。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-146">Use the **Details** tab of the **Configure SSIS Logs** dialog box to specify the events to enable for logging and the information details to log.</span></span> <span data-ttu-id="f4fcc-147">所选的信息适用于包中的所有日志提供程序。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-147">The information that you select applies to all the log providers in the package.</span></span> <span data-ttu-id="f4fcc-148">例如，无法将一些信息写入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例，而在文本文件中写入另外一些信息。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-148">For example, you cannot write some information to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance and different information to a text file.</span></span>  
  
### <a name="options"></a><span data-ttu-id="f4fcc-149">选项</span><span class="sxs-lookup"><span data-stu-id="f4fcc-149">Options</span></span>  
 <span data-ttu-id="f4fcc-150">**事件**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-150">**Events**</span></span>  
 <span data-ttu-id="f4fcc-151">为事件启用或禁用日志记录功能。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-151">Enable or disable events for logging.</span></span>  
  
 <span data-ttu-id="f4fcc-152">**说明**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-152">**Description**</span></span>  
 <span data-ttu-id="f4fcc-153">查看事件的说明。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-153">View a description of the event.</span></span>  
  
 <span data-ttu-id="f4fcc-154">**高级**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-154">**Advanced**</span></span>  
 <span data-ttu-id="f4fcc-155">选中或清除要记录的事件，以及选中或清除要为每个事件记录的信息。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-155">Select or clear events to log, and select or clear information to log for each event.</span></span> <span data-ttu-id="f4fcc-156">单击 **“基本”** 可以隐藏除事件列表之外的所有日志记录详细信息。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-156">Click **Basic** to hide all logging details, except the list of events.</span></span> <span data-ttu-id="f4fcc-157">日志记录可以包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="f4fcc-157">The following information is available for logging:</span></span>  
  
|<span data-ttu-id="f4fcc-158">值</span><span class="sxs-lookup"><span data-stu-id="f4fcc-158">Value</span></span>|<span data-ttu-id="f4fcc-159">说明</span><span class="sxs-lookup"><span data-stu-id="f4fcc-159">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f4fcc-160">**计算机**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-160">**Computer**</span></span>|<span data-ttu-id="f4fcc-161">发生所记录事件的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-161">The name of the computer on which the logged event occurred.</span></span>|  
|<span data-ttu-id="f4fcc-162">**“运算符”**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-162">**Operator**</span></span>|<span data-ttu-id="f4fcc-163">启动包的人员的用户名。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-163">The user name of the person who started the package.</span></span>|  
|<span data-ttu-id="f4fcc-164">**SourceName**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-164">**SourceName**</span></span>|<span data-ttu-id="f4fcc-165">发生所记录事件的包、容器或任务的名称。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-165">The name of the package, container, or task in which the logged event occurred.</span></span>|  
|<span data-ttu-id="f4fcc-166">**SourceID**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-166">**SourceID**</span></span>|<span data-ttu-id="f4fcc-167">发生所记录事件的包、容器或任务的全局唯一标识符 (GUID)。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-167">The global unique identifier (GUID) of the package, container, or task in which the logged event occurred.</span></span>|  
|<span data-ttu-id="f4fcc-168">**ExecutionID**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-168">**ExecutionID**</span></span>|<span data-ttu-id="f4fcc-169">包执行实例的全局唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-169">The global unique identifier of the package execution instance.</span></span>|  
|<span data-ttu-id="f4fcc-170">**MessageText**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-170">**MessageText**</span></span>|<span data-ttu-id="f4fcc-171">与日志项关联的消息。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-171">A message associated with the log entry.</span></span>|  
|<span data-ttu-id="f4fcc-172">**DataBytes**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-172">**DataBytes**</span></span>|<span data-ttu-id="f4fcc-173">保留供将来使用。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-173">Reserved for future use.</span></span>|  
  
 <span data-ttu-id="f4fcc-174">**基本**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-174">**Basic**</span></span>  
 <span data-ttu-id="f4fcc-175">选中或清除要记录的事件。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-175">Select or clear events to log.</span></span> <span data-ttu-id="f4fcc-176">选择此选项将隐藏除事件列表之外的日志记录详细信息。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-176">This option hides logging details except the list of events.</span></span> <span data-ttu-id="f4fcc-177">默认情况下，如果选择某事件，则会为该事件选择所有日志记录详细信息。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-177">If you select an event, all logging details are selected for the event by default.</span></span> <span data-ttu-id="f4fcc-178">单击 **“高级”** 将显示所有日志记录详细信息。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-178">Click **Advanced** to show all logging details.</span></span>  
  
 <span data-ttu-id="f4fcc-179">**加载**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-179">**Load**</span></span>  
 <span data-ttu-id="f4fcc-180">指定要用作设置日志记录选项的模板的现有 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-180">Specify an existing XML file to use as a template for setting logging options.</span></span>  
  
 <span data-ttu-id="f4fcc-181">**保存**</span><span class="sxs-lookup"><span data-stu-id="f4fcc-181">**Save**</span></span>  
 <span data-ttu-id="f4fcc-182">将配置详细信息以模板形式保存到 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="f4fcc-182">Save configuration details as a template to an XML file.</span></span>  
  
  
