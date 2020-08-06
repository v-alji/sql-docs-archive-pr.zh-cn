---
title: 步骤 2：添加并配置日志记录 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 56105f3f-e500-4669-8c8e-acf434527727
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0f2cdce6f34a19e22830d357d20f5d99cff8c14f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689515"
---
# <a name="step-2-adding-and-configuring-logging"></a><span data-ttu-id="6d604-102">步骤 2：添加并配置日志记录</span><span class="sxs-lookup"><span data-stu-id="6d604-102">Step 2: Adding and Configuring Logging</span></span>
  <span data-ttu-id="6d604-103">在本任务中，将为 Lesson 3.dtsx 包中的数据流启用日志记录。</span><span class="sxs-lookup"><span data-stu-id="6d604-103">In this task, you will enable logging for the data flow in the Lesson 3.dtsx package.</span></span> <span data-ttu-id="6d604-104">然后，将配置一个文本文件日志提供程序，以记录 PipelineExecutionPlan 和 PipelineExecuteTrees 事件。</span><span class="sxs-lookup"><span data-stu-id="6d604-104">Then, you will configure a Text File log provider to log the PipelineExecutionPlan and PipelineExecuteTrees events.</span></span> <span data-ttu-id="6d604-105">该文本文件日志提供程序可以创建便于查看并可轻松传输的日志。</span><span class="sxs-lookup"><span data-stu-id="6d604-105">The Text Files log provider creates logs that are easy to view and easily transportable.</span></span> <span data-ttu-id="6d604-106">由于便于使用，因此，这些日志文件在包的基本测试阶段非常有用。</span><span class="sxs-lookup"><span data-stu-id="6d604-106">The simplicity of these log files makes these files especially useful during the basic testing phase of a package.</span></span> <span data-ttu-id="6d604-107">您也可以在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器的“日志事件”窗口中查看日志条目。</span><span class="sxs-lookup"><span data-stu-id="6d604-107">You can also view the log entries in the Log Events window of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
### <a name="to-add-logging-to-the-package"></a><span data-ttu-id="6d604-108">向包中添加日志记录</span><span class="sxs-lookup"><span data-stu-id="6d604-108">To add logging to the package</span></span>  
  
1.  <span data-ttu-id="6d604-109">在 **SSIS** 菜单上，单击 **“日志记录”** 。</span><span class="sxs-lookup"><span data-stu-id="6d604-109">On the **SSIS** menu, click **Logging**.</span></span>  
  
2.  <span data-ttu-id="6d604-110">在“配置 SSIS 日志”\*\*\*\* 对话框的“容器”\*\*\*\* 窗格中，确保选中了最前面的代表第 3 课包的对象。</span><span class="sxs-lookup"><span data-stu-id="6d604-110">In the **Configure SSIS Logs** dialog box, in the **Containers** pane, make sure that the topmost object, which represents the Lesson 3 package, is selected.</span></span>  
  
3.  <span data-ttu-id="6d604-111">在“提供程序和日志”\*\*\*\* 选项卡的“提供程序类型”\*\*\*\* 框中，选择“用于文本文件的 SSIS 日志提供程序”\*\*\*\*，然后单击“添加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6d604-111">On the **Providers and Logs** tab, in the **Provider type** box, select **SSIS log provider for Text files**, and then click **Add**.</span></span>  
  
     <span data-ttu-id="6d604-112">Integration Services 将新的文本文件日志提供程序添加到具有默认名称的**文本文件的 SSIS 日志提供**程序的包中。</span><span class="sxs-lookup"><span data-stu-id="6d604-112">Integration Services adds a new Text File log provider to the package with the default name **SSIS log provider for text files**.</span></span> <span data-ttu-id="6d604-113">现在便可对新的日志提供程序进行配置。</span><span class="sxs-lookup"><span data-stu-id="6d604-113">You can now configure the new log provider.</span></span>  
  
4.  <span data-ttu-id="6d604-114">在 "**名称**" 列中，键入 `Lesson 3 Log File` 。</span><span class="sxs-lookup"><span data-stu-id="6d604-114">In the **Name** column, type `Lesson 3 Log File`.</span></span>  
  
5.  <span data-ttu-id="6d604-115">也可以修改“说明”  。</span><span class="sxs-lookup"><span data-stu-id="6d604-115">Optionally, modify the **Description**.</span></span>  
  
6.  <span data-ttu-id="6d604-116">在“配置”\*\*\*\* 列中，单击 **\<New Connection>**，以指定用于写入日志信息的目标位置。</span><span class="sxs-lookup"><span data-stu-id="6d604-116">In the **Configuration** column, click **\<New Connection>** to specify the destination to which the log information is written.</span></span>  
  
     <span data-ttu-id="6d604-117">在“文件连接管理器编辑器”\*\*\*\* 对话框中，对“使用类型”\*\*\*\* 选择“创建文件”\*\*\*\*，然后单击“浏览”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6d604-117">In the **File Connection Manager Editor** dialog box, for **Usage type**, select **Create file**, and then click **Browse**.</span></span> <span data-ttu-id="6d604-118">默认情况下，“选择文件”\*\*\*\* 对话框将打开项目文件夹，但你可以将日志信息保存到任何位置。</span><span class="sxs-lookup"><span data-stu-id="6d604-118">By default, the **Select File** dialog box opens the project folder, but you can save log information to any location.</span></span>  
  
7.  <span data-ttu-id="6d604-119">在 "**选择文件**" 对话框的 "文件名 **" 框中**，键入 `TutorialLog.log` ，并单击 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="6d604-119">In the **Select File** dialog box, in the **File name** box type `TutorialLog.log`, and click **Open**.</span></span>  
  
8.  <span data-ttu-id="6d604-120">单击“确定”\*\*\*\* 关闭“文件连接管理器编辑器”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="6d604-120">Click **OK** to close the **File Connection Manager Editor** dialog box.</span></span>  
  
9. <span data-ttu-id="6d604-121">在“容器”  窗格中，展开包容器层次结构中的所有节点，然后清除包括 **Extract Sample Currency Data** 复选框在内的所有复选框。</span><span class="sxs-lookup"><span data-stu-id="6d604-121">In the **Containers** pane, expand all nodes of the package container hierarchy, and then clear all check boxes, including the **Extract Sample Currency Data** check box.</span></span> <span data-ttu-id="6d604-122">现在选中“Extract Sample Currency Data”  复选框以仅获取有关此节点的事件。</span><span class="sxs-lookup"><span data-stu-id="6d604-122">Now select the check box for **Extract Sample Currency Data** to get only the events for this node.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="6d604-123">如果“Extract Sample Currency Data”\*\*\*\* 复选框显示为灰色而并非选中状态，则该任务将使用父容器的日志设置，无法启用任务特定的日志事件。</span><span class="sxs-lookup"><span data-stu-id="6d604-123">If the state of the **Extract Sample Currency Data** check box is dimmed instead of selected, the task uses the log settings of the parent container and you cannot enable the log events that are specific to the task.</span></span>  
  
10. <span data-ttu-id="6d604-124">在“详细信息”  选项卡的“事件”  列中，选择“PipelineExecutionPlan”  和“PipelineExecutionTrees”  事件。</span><span class="sxs-lookup"><span data-stu-id="6d604-124">On the **Details** tab, in the **Events** column, select the **PipelineExecutionPlan** and **PipelineExecutionTrees** events.</span></span>  
  
11. <span data-ttu-id="6d604-125">单击“高级”\*\*\*\* 可查看日志提供程序将为每个事件写入日志的详细信息。</span><span class="sxs-lookup"><span data-stu-id="6d604-125">Click **Advanced** to review the details that the log provider will write to the log for each event.</span></span> <span data-ttu-id="6d604-126">默认情况下，将为您指定的事件自动选择所有信息类别。</span><span class="sxs-lookup"><span data-stu-id="6d604-126">By default, all information categories are automatically selected for the events you specify.</span></span>  
  
12. <span data-ttu-id="6d604-127">单击“基本”\*\*\*\* 隐藏信息类别。</span><span class="sxs-lookup"><span data-stu-id="6d604-127">Click **Basic** to hide the information categories.</span></span>  
  
13. <span data-ttu-id="6d604-128">在 "**提供程序和日志**" 选项卡上的 "**名称**" 列中，选择 `Lesson 3 Log File` 。</span><span class="sxs-lookup"><span data-stu-id="6d604-128">On the **Provider and Logs** tab, in the **Name** column, select `Lesson 3 Log File`.</span></span> <span data-ttu-id="6d604-129">为包创建日志提供程序后，可以选择取消选择它以临时关闭日志记录，而不必删除后再重新创建日志提供程序。</span><span class="sxs-lookup"><span data-stu-id="6d604-129">Once you have created a log provider for your package, you can optionally deselect it to temporarily turn off logging, without having to delete and re-create a log provider.</span></span>  
  
14. <span data-ttu-id="6d604-130">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="6d604-130">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6d604-131">后续步骤</span><span class="sxs-lookup"><span data-stu-id="6d604-131">Next Steps</span></span>  
 [<span data-ttu-id="6d604-132">步骤 3：测试第 3 课教程包</span><span class="sxs-lookup"><span data-stu-id="6d604-132">Step 3: Testing the Lesson 3 Tutorial Package</span></span>](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
  
