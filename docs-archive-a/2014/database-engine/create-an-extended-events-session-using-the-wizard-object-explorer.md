---
title: 使用向导创建扩展事件会话 (对象资源管理器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- Sql12.ssms.XeWizard.Summary.f1
- Sql12.ssms.XeWizard.SetSessionProperties.f1
- Sql12.ssms.XeWizard.CaptureAddFields.f1
- Sql12.ssms.XeWizard.SelectEvents.f1
- Sql12.ssms.XeWizard.SpecifySessionTargets.f1
- Sql12.ssms.XeWizard.Welcome.f1
- sql12.ssms.XeWizard.Welcome.f1
- Sql12.ssms.XeWizard.ChooseTemplate.f1
- Sql12.ssms.XeWizard.SetSessionEventFilters.f1
- Sql12.ssms.XeWizard.Results.f1
helpviewer_keywords:
- Sql11.ssms.XeWizard.CaptureAddFields.f1
- Sql11.ssms.XeWizard.SetSessionEventFilters.f1
- Sql11.ssms.XeWizard.SpecifySessionTargets.f1
- Sql11.ssms.XeWizard.Results.f1
- Sql11.ssms.XeWizard.ChooseTemplate.f1
- Sql11.ssms.XeWizard.SetSessionProperties.f1
- Sql11.ssms.XeWizard.Welcome.f1
- Sql11.ssms.XeWizard.Summary.f1
- Sql11.ssms.XeWizard.SelectEvents.f1
ms.assetid: 80c0456f-17c0-41d8-b2aa-502a2f3bb6de
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cdfc9141b0b99d5b06fc73044b8f4fae623922b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586953"
---
# <a name="create-an-extended-events-session-using-the-wizard-object-explorer"></a><span data-ttu-id="5c07f-102">使用向导创建扩展事件会话（对象资源管理器）</span><span class="sxs-lookup"><span data-stu-id="5c07f-102">Create an Extended Events Session Using the Wizard (Object Explorer)</span></span>
  <span data-ttu-id="5c07f-103">为了帮助您选择和捕获服务器上的事件，扩展事件包括一个“新建会话”向导，引导您完成创建扩展事件会话所需的步骤。</span><span class="sxs-lookup"><span data-stu-id="5c07f-103">To help you select and capture events on your server, Extended Events includes a New Session Wizard that guides you through the steps to create an Extended Events session.</span></span> <span data-ttu-id="5c07f-104">“新建会话”向导公开大多数扩展事件功能。</span><span class="sxs-lookup"><span data-stu-id="5c07f-104">The New Session Wizard exposes most of the Extended Events functionality.</span></span> <span data-ttu-id="5c07f-105">通过[“新建会话”对话框](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md)，还可以定义捕获、显示和分析数据的扩展事件会话。</span><span class="sxs-lookup"><span data-stu-id="5c07f-105">The [New Session dialog](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md) also lets you define an Extended Events session that captures, displays, and analyzes your data.</span></span> <span data-ttu-id="5c07f-106">“新建会话”对话框公开所有扩展事件功能。</span><span class="sxs-lookup"><span data-stu-id="5c07f-106">The New Session dialog exposes all Extended Events functionality.</span></span>  
  
### <a name="to-open-the-new-session-wizard"></a><span data-ttu-id="5c07f-107">打开“新建会话”向导</span><span class="sxs-lookup"><span data-stu-id="5c07f-107">To open the New Session Wizard</span></span>  
  
1.  <span data-ttu-id="5c07f-108">在对象资源管理器中，依次展开 **“管理”** 节点和 **“扩展事件”**。</span><span class="sxs-lookup"><span data-stu-id="5c07f-108">In Object Explorer, expand the **Management** node, and then expand **Extended Events**.</span></span>  
  
2.  <span data-ttu-id="5c07f-109">右键单击“会话”\*\*\*\*，然后单击“新建会话向导”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5c07f-109">Right-click **Sessions**, and then click **New Session Wizard**.</span></span>  
  
### <a name="use-the-following-new-session-wizard-pages-to-create-an-event-session"></a><span data-ttu-id="5c07f-110">使用以下“新建会话”向导页可以创建事件会话</span><span class="sxs-lookup"><span data-stu-id="5c07f-110">Use the following New Session Wizard pages to create an event session</span></span>  
  
-   [<span data-ttu-id="5c07f-111">简介</span><span class="sxs-lookup"><span data-stu-id="5c07f-111">Introduction</span></span>](#BKMK_Welcome)  
  
-   [<span data-ttu-id="5c07f-112">设置会话属性</span><span class="sxs-lookup"><span data-stu-id="5c07f-112">Set Session Properties</span></span>](#BKMK_SetSessionProperties)  
  
-   [<span data-ttu-id="5c07f-113">选择模板</span><span class="sxs-lookup"><span data-stu-id="5c07f-113">Choose Template</span></span>](#BKMK_ChooseTemplate)  
  
-   [<span data-ttu-id="5c07f-114">选择要捕获的事件</span><span class="sxs-lookup"><span data-stu-id="5c07f-114">Select Events to Capture</span></span>](#BKMK_SelectEventsToCapture)  
  
-   [<span data-ttu-id="5c07f-115">捕获全局字段</span><span class="sxs-lookup"><span data-stu-id="5c07f-115">Capture Global Fields</span></span>](#BKMK_CaptureGlobalFields)  
  
-   [<span data-ttu-id="5c07f-116">设置会话事件筛选器</span><span class="sxs-lookup"><span data-stu-id="5c07f-116">Set Session Event Filters</span></span>](#BKMK_SetSessionEventFilters)  
  
-   [<span data-ttu-id="5c07f-117">指定会话数据存储</span><span class="sxs-lookup"><span data-stu-id="5c07f-117">Specify Session Data Storage</span></span>](#BKMK_SpecifySessionDataOutput)  
  
-   [<span data-ttu-id="5c07f-118">摘要</span><span class="sxs-lookup"><span data-stu-id="5c07f-118">Summary</span></span>](#BKMK_Summary)  
  
-   [<span data-ttu-id="5c07f-119">创建事件会话</span><span class="sxs-lookup"><span data-stu-id="5c07f-119">Create Event Session</span></span>](#BKMK_CreateEventSession)  
  
##  <a name="introduction"></a><a name="BKMK_Welcome"></a><span data-ttu-id="5c07f-120">产品介绍</span><span class="sxs-lookup"><span data-stu-id="5c07f-120">Introduction</span></span>  
 <span data-ttu-id="5c07f-121">在 **“简介”** 页上，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="5c07f-121">On the **Introduction** page, do the following:</span></span>  
  
-   <span data-ttu-id="5c07f-122">在“新建会话”向导的 **“简介”** 页上，单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="5c07f-122">On the **Introduction** page of the New Session Wizard, click **Next**.</span></span>  
  
     <span data-ttu-id="5c07f-123">如果要多次使用该向导并且不想每次启动该向导时都阅读此简介，则选中“不再显示此页”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="5c07f-123">Select the **Do not show this page again** check box if you will be using the wizard more than once and do not want to read the introduction each time the wizard is launched.</span></span>  
  
##  <a name="set-session-properties"></a><a name="BKMK_SetSessionProperties"></a><span data-ttu-id="5c07f-124">设置会话属性</span><span class="sxs-lookup"><span data-stu-id="5c07f-124">Set Session Properties</span></span>  
 <span data-ttu-id="5c07f-125">在 **“设置会话属性”** 页上，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="5c07f-125">On the **Set Session Properties** page, do the following:</span></span>  
  
-   <span data-ttu-id="5c07f-126">在 **“会话名称”** 框中，键入事件会话的有意义的名称。</span><span class="sxs-lookup"><span data-stu-id="5c07f-126">In the **Session name** box, type a meaningful name for the event session.</span></span>  
  
     <span data-ttu-id="5c07f-127">如果您想要在启动服务器时启动会话，则选中 **“在服务器启动时启动事件会话”** 复选框，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="5c07f-127">If you want to start the session when you start the server, select the **Start the event session at server startup** check box, and then click **Next**.</span></span>  
  
##  <a name="choose-template"></a><a name="BKMK_ChooseTemplate"></a><span data-ttu-id="5c07f-128">选择模板</span><span class="sxs-lookup"><span data-stu-id="5c07f-128">Choose Template</span></span>  
 <span data-ttu-id="5c07f-129">在 **“选择模板”** 页上，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="5c07f-129">On the **Choose Template** page, do the following:</span></span>  
  
-   <span data-ttu-id="5c07f-130">选择“使用此事件会话模板”\*\*\*\* 选项可以从为常见问题设计的一组预先配置的模板中进行选择。</span><span class="sxs-lookup"><span data-stu-id="5c07f-130">Select the **Use this event session template** option to select from a set of pre-configured templates designed for common problems.</span></span> <span data-ttu-id="5c07f-131">从下拉列表中选择你要使用的模板，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5c07f-131">Select the template you want to use from the drop-down list, and then click **Next**.</span></span>  
  
     <span data-ttu-id="5c07f-132">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="5c07f-132">-OR-</span></span>  
  
-   <span data-ttu-id="5c07f-133">如果你不想使用任何预先配置的模板，则选择“不使用模板”\*\*\*\* 选项，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5c07f-133">Select the **Do not use a template** option if you do not want to use any pre-configured template, and then click **Next**.</span></span>  
  
##  <a name="select-events-to-capture"></a><a name="BKMK_SelectEventsToCapture"></a><span data-ttu-id="5c07f-134">选择要捕获的事件</span><span class="sxs-lookup"><span data-stu-id="5c07f-134">Select Events to Capture</span></span>  
 <span data-ttu-id="5c07f-135">在 **“选择要捕获的事件“** 页上，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="5c07f-135">On the **Select Events to Capture** page, do the following:</span></span>  
  
1.  <span data-ttu-id="5c07f-136">从 **”事件库“** 中选择要使用的事件，然后单击向右箭头。</span><span class="sxs-lookup"><span data-stu-id="5c07f-136">Select the events you want to capture from the **Event library**, and then click the right arrow.</span></span> <span data-ttu-id="5c07f-137">您可以通过使用 Shift+单击或 Ctrl+单击在事件库中选择多个事件。</span><span class="sxs-lookup"><span data-stu-id="5c07f-137">You can select multiple events in the Event Library by using either Shift+Click or Ctrl+Click.</span></span>  
  
     <span data-ttu-id="5c07f-138">您可以从下拉列表框中选择搜索要捕获的事件的方式。</span><span class="sxs-lookup"><span data-stu-id="5c07f-138">You can select how you want to search for the events you want to capture from the drop-down list box.</span></span> <span data-ttu-id="5c07f-139">例如，您可以搜索事件名称或者事件名称及其说明。</span><span class="sxs-lookup"><span data-stu-id="5c07f-139">For example, you can search for event names or event names and their descriptions.</span></span> <span data-ttu-id="5c07f-140">您可以通过在 **“事件库”** 框中输入要搜索的文本，搜索表中的任何词语。</span><span class="sxs-lookup"><span data-stu-id="5c07f-140">You can search for any word in the table by entering the text you want to search for in the **Event library** box.</span></span> <span data-ttu-id="5c07f-141">例如，如果你想要查找 **lock_acquired** 事件，则可以输入 **lock**或 **lock acquire**。</span><span class="sxs-lookup"><span data-stu-id="5c07f-141">For example, if you want to find the **lock_acquired** event, you can enter **lock**, or **lock acquire**.</span></span>  
  
     <span data-ttu-id="5c07f-142">您选择的事件将出现在 **“所选事件”** 框中。</span><span class="sxs-lookup"><span data-stu-id="5c07f-142">The events you select appear in the **Selected events** box.</span></span> <span data-ttu-id="5c07f-143">若要从 **“所选事件”** 框中删除事件，请单击向左箭头。</span><span class="sxs-lookup"><span data-stu-id="5c07f-143">To remove events from the **Selected events** box, click the left arrow.</span></span>  
  
2.  <span data-ttu-id="5c07f-144">在选择了要捕获的事件后，单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="5c07f-144">After you select the events you want to capture, click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5c07f-145">默认情况下将隐藏来自 **“调试”** 渠道的事件。</span><span class="sxs-lookup"><span data-stu-id="5c07f-145">Events from the **Debug** channel are hidden by default.</span></span> <span data-ttu-id="5c07f-146">若要显示调试事件，请从“渠道”\*\*\*\* 下拉列表中选择“调试”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5c07f-146">To display debug events, select **Debug** from the **Channel** drop-down list.</span></span>  
  
##  <a name="capture-global-fields"></a><a name="BKMK_CaptureGlobalFields"></a><span data-ttu-id="5c07f-147">捕获全局字段</span><span class="sxs-lookup"><span data-stu-id="5c07f-147">Capture Global Fields</span></span>  
 <span data-ttu-id="5c07f-148">使用全局字段（也称作操作）可以关联所选事件的单个或多个操作。</span><span class="sxs-lookup"><span data-stu-id="5c07f-148">You use global fields (also referred to as actions) to associate single or multiple actions for your selected events.</span></span> <span data-ttu-id="5c07f-149">如果您在 **“选择模板”** 页上选择了某个模板，则在该模板中定义的所有全局字段都将显示在此页上。</span><span class="sxs-lookup"><span data-stu-id="5c07f-149">If you selected a template on the **Choose Template** page, all of the global fields that are defined in the template are displayed on this page.</span></span>  
  
 <span data-ttu-id="5c07f-150">在 **“捕获全局字段“** 页上，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="5c07f-150">On the **Capture Global Fields** page, do the following:</span></span>  
  
-   <span data-ttu-id="5c07f-151">选择您要为事件会话捕获的全局字段，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="5c07f-151">Select the global fields that you want to capture for the event session, and then click **Next**.</span></span>  
  
     <span data-ttu-id="5c07f-152">您可以通过选中或取消选中全局字段旁的复选框，删除或添加全局字段。</span><span class="sxs-lookup"><span data-stu-id="5c07f-152">You can remove or add global fields by selecting or clearing the check box next to the global field.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5c07f-153">所选操作将按 **“名称”** 排序，这样，您可以按字母顺序查看关联的操作。</span><span class="sxs-lookup"><span data-stu-id="5c07f-153">The selected actions are sorted by **Name** enabling you to view the associated actions in alphabetical order.</span></span> <span data-ttu-id="5c07f-154">您可以通过单击字段名称旁的列标题，按照说明或者启用/禁用状态进行排序。</span><span class="sxs-lookup"><span data-stu-id="5c07f-154">You can sort by description or by the enable/disable status by clicking the column heading next to the field name.</span></span>  
  
##  <a name="set-session-event-filters"></a><a name="BKMK_SetSessionEventFilters"></a><span data-ttu-id="5c07f-155">设置会话事件筛选器</span><span class="sxs-lookup"><span data-stu-id="5c07f-155">Set Session Event Filters</span></span>  
 <span data-ttu-id="5c07f-156">您可以应用筛选器（也称作谓词）来限制要捕获的事件。</span><span class="sxs-lookup"><span data-stu-id="5c07f-156">You can apply filters (also called predicates) to limit the events that you want to capture.</span></span> <span data-ttu-id="5c07f-157">在 **“设置事件筛选器”** 页上，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="5c07f-157">On the **Set Session Event Filters** page, do the following:</span></span>  
  
1.  <span data-ttu-id="5c07f-158">如果你未在使用预先配置的模板，则创建你的筛选条件，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5c07f-158">If you are not using a pre-configured template, create your filter criteria, and then click **Next**.</span></span>  
  
     <span data-ttu-id="5c07f-159">如果你正在使用某个预先配置的模板，则在\*\*\*\*“来自模板的筛选器(只读)”部分中，“新建会话”向导将列出已根据该模板创建的筛选器。</span><span class="sxs-lookup"><span data-stu-id="5c07f-159">If you are using a pre-configured template, in the **Filters from template (read-only)** section, the New Session Wizard lists filters already created from the template.</span></span>  
  
2.  <span data-ttu-id="5c07f-160">在 **“附加筛选器”** 部分中，您可以配置事件会话的附加筛选器。</span><span class="sxs-lookup"><span data-stu-id="5c07f-160">In the **Additional filters** section, you can configure additional filters for the event session.</span></span>  
  
     <span data-ttu-id="5c07f-161">您配置的筛选器将应用于所有所选事件。</span><span class="sxs-lookup"><span data-stu-id="5c07f-161">The filters you configure apply to all selected events.</span></span> <span data-ttu-id="5c07f-162">“新建会话”向导不支持为每个事件都配置筛选器。</span><span class="sxs-lookup"><span data-stu-id="5c07f-162">The New Session Wizard does not support configuring filters for each event.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5c07f-163">在您为筛选器配置组子句时，在保存结果后多余的括号将从筛选器中删除。</span><span class="sxs-lookup"><span data-stu-id="5c07f-163">When you configure a group clause for your filter, redundant parentheses are removed from the filter after the result is saved.</span></span> <span data-ttu-id="5c07f-164">例如，如果您创建一个筛选器分组 **Clause 1** 和 **Clause 2**，则括号会将这两个子句括起来。</span><span class="sxs-lookup"><span data-stu-id="5c07f-164">For example, if you create a filter grouping **Clause 1** and **Clause 2**, parentheses will appear around the clauses.</span></span> <span data-ttu-id="5c07f-165">在您保存筛选器后，多余的括号将被删除。</span><span class="sxs-lookup"><span data-stu-id="5c07f-165">After you save the filter, the redundant parentheses are removed.</span></span> <span data-ttu-id="5c07f-166">删除这些括号不会影响筛选器逻辑。</span><span class="sxs-lookup"><span data-stu-id="5c07f-166">The removal of the parentheses does not affect the filter logic.</span></span>  
  
##  <a name="specify-session-data-storage"></a><a name="BKMK_SpecifySessionDataOutput"></a><span data-ttu-id="5c07f-167">指定会话数据存储</span><span class="sxs-lookup"><span data-stu-id="5c07f-167">Specify Session Data Storage</span></span>  
 <span data-ttu-id="5c07f-168">使用 **“指定会话数据存储”** 页可以指定您要收集数据以便进行分析的方式。</span><span class="sxs-lookup"><span data-stu-id="5c07f-168">You use the **Specify Session Data Storage** page to specify how you want to collect your data for analysis.</span></span> <span data-ttu-id="5c07f-169">SQL Server 扩展事件使用目标进行数据输出。</span><span class="sxs-lookup"><span data-stu-id="5c07f-169">SQL Server Extended Events uses targets for data output.</span></span> <span data-ttu-id="5c07f-170">目标存储事件数据并且可以执行各种操作，例如写入文件和聚合事件数据。</span><span class="sxs-lookup"><span data-stu-id="5c07f-170">Targets store event data and can perform actions such as writing to a file and aggregating event data.</span></span> <span data-ttu-id="5c07f-171">决定您要收集数据以便进行分析的方式，并且在 **“指定会话数据存储”** 页上，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="5c07f-171">Decide how you want to collect your data for analysis, and on the **Specify Session Data Storage** page, do the following:</span></span>  
  
1.  <span data-ttu-id="5c07f-172">对于大型数据集和创建历史记录，请选中 **“将数据保存到文件以便以后分析”** 复选框，然后执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="5c07f-172">For large data sets and creating historical records, select the **Save data to a file for later analysis** check box, and then do the following:</span></span>  
  
    1.  <span data-ttu-id="5c07f-173">在 **“服务器上的文件名”** 框中，输入路径和文件名，或者单击 **“浏览”** 以便指定服务器上您要用于保存数据的文件目录。</span><span class="sxs-lookup"><span data-stu-id="5c07f-173">In the **File name on server** box, enter the path and file name, or click **Browse** to specify the file directory on the server where you want to save the data.</span></span>  
  
    2.  <span data-ttu-id="5c07f-174">在 **“最大文件大小”** 框中，指定要用于文件目标的最大文件大小。</span><span class="sxs-lookup"><span data-stu-id="5c07f-174">In the **Maximum file size** box, specify the maximum file size to be used for the file target.</span></span> <span data-ttu-id="5c07f-175">如果未指定最大文件大小，则文件将一直增长到磁盘变满为止。</span><span class="sxs-lookup"><span data-stu-id="5c07f-175">If you do not specify the maximum file size, the file will grow until the disk is full.</span></span> <span data-ttu-id="5c07f-176">默认文件大小为 1 GB。</span><span class="sxs-lookup"><span data-stu-id="5c07f-176">The default file size is 1 gigabyte (GB).</span></span>  
  
    3.  <span data-ttu-id="5c07f-177">选中 **“启用文件滚动更新”** 复选框可为文件目标启用文件滚动更新。</span><span class="sxs-lookup"><span data-stu-id="5c07f-177">Select the **Enable file rollover** check box to enable file rollover for the file target.</span></span>  
  
    4.  <span data-ttu-id="5c07f-178">在 **“最大文件数”** 框中，指定您要在文件系统中保留的最大文件数。</span><span class="sxs-lookup"><span data-stu-id="5c07f-178">In the **Maximum number of files** box, specify the maximum number of files you want to retain in the file system.</span></span>  
  
2.  <span data-ttu-id="5c07f-179">若要收集最近的数据，请选中“仅使用最近数据(环形缓冲区目标)”\*\*\*\* 复选框，然后执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="5c07f-179">For collecting recent data, select the **Work with only the most recent data (ring buffer target)** check box, and then do the following:</span></span>  
  
    1.  <span data-ttu-id="5c07f-180">在 **“要保留的事件数目”** 框中，通过使用向上和向下箭头输入或选择您要保留的事件数目。</span><span class="sxs-lookup"><span data-stu-id="5c07f-180">In the **Number of events to keep** box, enter or select the number of events you want to keep by using the up and down arrows.</span></span>  
  
    2.  <span data-ttu-id="5c07f-181">在 **“最大缓冲区内存大小”** 框中，指定要使用的缓冲区内存的最大大小。</span><span class="sxs-lookup"><span data-stu-id="5c07f-181">In the **Maximum buffer memory size** box, specify the maximum amount of buffer memory to use.</span></span> <span data-ttu-id="5c07f-182">达到此值时将删除现有事件。</span><span class="sxs-lookup"><span data-stu-id="5c07f-182">The existing events are dropped when this value is reached.</span></span>  
  
    3.  <span data-ttu-id="5c07f-183">如果你想要在缓冲区中保留每种类型的特定的事件数目，则选中“在缓冲区已满时保留指定数目的事件(按类型)”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="5c07f-183">If you want to keep a specific number of events of each type in the buffer, select the **Keep a specified number of events (per type) when the buffer is full** check box.</span></span>  
  
    4.  <span data-ttu-id="5c07f-184">在“要保留的事件数目(按类型)”\*\*\*\* 框中，通过使用向上和向下箭头输入或选择你要保留的事件数目（按类型）。</span><span class="sxs-lookup"><span data-stu-id="5c07f-184">In the **Number of events to keep (per type)** box, enter or select the number of events (per type) that you want to keep by using the up and down arrows.</span></span>  
  
##  <a name="summary"></a><a name="BKMK_Summary"></a><span data-ttu-id="5c07f-185">总结</span><span class="sxs-lookup"><span data-stu-id="5c07f-185">Summary</span></span>  
 <span data-ttu-id="5c07f-186">在 **“摘要”** 页上，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="5c07f-186">On the **Summary** page, do the following:</span></span>  
  
1.  <span data-ttu-id="5c07f-187">请确保您的选择是正确的。</span><span class="sxs-lookup"><span data-stu-id="5c07f-187">Make sure that your selections are correct.</span></span> <span data-ttu-id="5c07f-188">展开事件会话节点以便确认您的所有选择都包括在事件会话中。</span><span class="sxs-lookup"><span data-stu-id="5c07f-188">Expand the event session nodes to verify that all of your selections will be included in the event session.</span></span>  
  
2.  <span data-ttu-id="5c07f-189">单击 **“脚本”** 以便将会话创建脚本导出到新的查询编辑器窗口中。</span><span class="sxs-lookup"><span data-stu-id="5c07f-189">Click **Script** to export the session creation script to a new Query Editor window.</span></span>  
  
3.  <span data-ttu-id="5c07f-190">单击 **“完成”** 以便创建事件会话。</span><span class="sxs-lookup"><span data-stu-id="5c07f-190">Click **Finish** to create the event session.</span></span>  
  
##  <a name="create-event-session"></a><a name="BKMK_CreateEventSession"></a><span data-ttu-id="5c07f-191">创建事件会话</span><span class="sxs-lookup"><span data-stu-id="5c07f-191">Create Event Session</span></span>  
 <span data-ttu-id="5c07f-192">在 **“创建事件会话”** 页上，在已成功创建您的事件会话后，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="5c07f-192">On the **Create Event Session** page, after your event session has been successfully created, do the following:</span></span>  
  
1.  <span data-ttu-id="5c07f-193">单击 **“在会话创建后立即启动事件会话”** 以便在您关闭向导后启动会话。</span><span class="sxs-lookup"><span data-stu-id="5c07f-193">Click **Start the event session immediately after session creation** to start the session after you close the wizard.</span></span> <span data-ttu-id="5c07f-194">您必须在创建会话后立即启动事件会话，以便能够查看实时数据。</span><span class="sxs-lookup"><span data-stu-id="5c07f-194">You must start the event session immediately after you create the session to be able to watch live data.</span></span>  
  
2.  <span data-ttu-id="5c07f-195">单击 **“在捕获时查看屏幕上的实时数据”** 可以查看您的事件会话的实时数据。</span><span class="sxs-lookup"><span data-stu-id="5c07f-195">Click **Watch live data on screen as it is captured** to view live data for your event session.</span></span> <span data-ttu-id="5c07f-196">实时数据将在创建会话后立即开始显示跟踪。</span><span class="sxs-lookup"><span data-stu-id="5c07f-196">The live data will start displaying tracing immediately after the session is created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c07f-197">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5c07f-197">See Also</span></span>  
 [<span data-ttu-id="5c07f-198">使用“新建会话”对话框创建扩展事件会话</span><span class="sxs-lookup"><span data-stu-id="5c07f-198">Create an Extended Events Session Using the New Session Dialog</span></span>](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md)  
  
  
