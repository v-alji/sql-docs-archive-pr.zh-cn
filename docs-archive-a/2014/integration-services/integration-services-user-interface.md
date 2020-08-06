---
title: Integration Services 用户界面 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services, SSIS Designer
- tools [Integration Services], SSIS Designer
- SSIS Designer
- SSIS, SSIS Designer
- Integration Services, SSIS Designer
ms.assetid: d2c48cff-46f4-4c70-b1f3-c88f9b8757f3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 60951be420397354976b8a0b6a411f18746bc735
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586847"
---
# <a name="integration-services-user-interface"></a><span data-ttu-id="57bad-102">Integration Services 用户界面</span><span class="sxs-lookup"><span data-stu-id="57bad-102">Integration Services User Interface</span></span>
  <span data-ttu-id="57bad-103">除了 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器选项卡上的设计图面外，还可通过用户界面访问下面的窗口和对话框，以便向包添加功能以及配置包对象的属性。</span><span class="sxs-lookup"><span data-stu-id="57bad-103">In addition to the design surfaces on the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer tabs, the user interface provides access to the following windows and dialog boxes for adding features to packages and configuring the properties of package objects:</span></span>  
  
-   <span data-ttu-id="57bad-104">用于向包添加功能（如记录日志和配置）的对话框和窗口。</span><span class="sxs-lookup"><span data-stu-id="57bad-104">The dialog boxes and windows that you use to add functionality such as logging and configurations to packages.</span></span>  
  
-   <span data-ttu-id="57bad-105">配置包对象属性的自定义编辑器。</span><span class="sxs-lookup"><span data-stu-id="57bad-105">The custom editors for configuring the properties of package objects.</span></span> <span data-ttu-id="57bad-106">几乎每种类型的容器、任务和数据流组件都有其自己的自定义编辑器。</span><span class="sxs-lookup"><span data-stu-id="57bad-106">Almost every type of container, task, and data flow component has its own custom editor.</span></span>  
  
-   <span data-ttu-id="57bad-107">**“高级编辑器”** 对话框，这是为许多数据流组件提供更详细的配置选项的通用编辑器。</span><span class="sxs-lookup"><span data-stu-id="57bad-107">The **Advanced Editor** dialog box, a generic editor that provides more detailed configuration options for many data flow components.</span></span>  
  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="57bad-108">还提供了用于配置环境和对包进行操作的窗口和对话框。</span><span class="sxs-lookup"><span data-stu-id="57bad-108">also provides windows and dialog boxes for configuring the environment and working with packages.</span></span>  
  
## <a name="dialog-boxes-and-windows"></a><span data-ttu-id="57bad-109">对话框和窗口</span><span class="sxs-lookup"><span data-stu-id="57bad-109">Dialog Boxes and Windows</span></span>  
 <span data-ttu-id="57bad-110">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中打开包或创建新包后，便可使用下列对话框和窗口。</span><span class="sxs-lookup"><span data-stu-id="57bad-110">After you open a package or create a new package in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, the following dialog boxes and windows are available.</span></span>  
  
 <span data-ttu-id="57bad-111">此表列出可从 **SSIS** 菜单和 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器的设计图面访问的对话框。</span><span class="sxs-lookup"><span data-stu-id="57bad-111">This table lists the dialog boxes that are available from the **SSIS** menu and the design surfaces of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
|<span data-ttu-id="57bad-112">对话框</span><span class="sxs-lookup"><span data-stu-id="57bad-112">Dialog box</span></span>|<span data-ttu-id="57bad-113">目的</span><span class="sxs-lookup"><span data-stu-id="57bad-113">Purpose</span></span>|<span data-ttu-id="57bad-114">访问</span><span class="sxs-lookup"><span data-stu-id="57bad-114">Access</span></span>|  
|----------------|-------------|------------|  
|<span data-ttu-id="57bad-115">**入门**</span><span class="sxs-lookup"><span data-stu-id="57bad-115">**Getting Started**</span></span>|<span data-ttu-id="57bad-116">访问示例、教程和视频内容。</span><span class="sxs-lookup"><span data-stu-id="57bad-116">Access samples, tutorials, and videos.</span></span>|<span data-ttu-id="57bad-117">右键单击“控制流”  选项卡或“数据流”  选项卡的设计图面，然后单击“入门”  。</span><span class="sxs-lookup"><span data-stu-id="57bad-117">On the design surface of the **Control Flow** tab or the **Data Flow** tab, right-click and then click **Getting Started**.</span></span><br /><br /> <span data-ttu-id="57bad-118">要在创建新的 **项目时自动显示** “入门” [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 窗口，请选择该窗口底部的 **“始终在新项目中显示”** 。</span><span class="sxs-lookup"><span data-stu-id="57bad-118">To automatically display the **Getting Started** window when you create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, select **Always show in new project** at the bottom of the window.</span></span>|  
|<span data-ttu-id="57bad-119">**配置 SSIS 日志**</span><span class="sxs-lookup"><span data-stu-id="57bad-119">**Configure SSIS Logs**</span></span>|<span data-ttu-id="57bad-120">添加日志和设置日志记录详细信息，从而配置包及其任务的日志记录。</span><span class="sxs-lookup"><span data-stu-id="57bad-120">Configure logging for a package and its tasks by adding logs and setting logging details.</span></span>|<span data-ttu-id="57bad-121">在 **SSIS** 菜单上，单击 **“日志记录”** 。</span><span class="sxs-lookup"><span data-stu-id="57bad-121">On the **SSIS** menu, click **Logging**.</span></span><br /><br /> <span data-ttu-id="57bad-122">-或-</span><span class="sxs-lookup"><span data-stu-id="57bad-122">-or-</span></span><br /><br /> <span data-ttu-id="57bad-123">右键单击“控制流”  选项卡的设计图面上任意位置，再单击“日志记录”  。</span><span class="sxs-lookup"><span data-stu-id="57bad-123">Right-click anywhere on the design surface of the **Control Flow** tab, and then click **Logging**.</span></span>|  
|<span data-ttu-id="57bad-124">**包配置组织程序**</span><span class="sxs-lookup"><span data-stu-id="57bad-124">**Package Configuration Organizer**</span></span>|<span data-ttu-id="57bad-125">添加和编辑包配置。</span><span class="sxs-lookup"><span data-stu-id="57bad-125">Add and edit package configurations.</span></span> <span data-ttu-id="57bad-126">请从此对话框运行包配置向导。</span><span class="sxs-lookup"><span data-stu-id="57bad-126">You run the Package Configuration Wizard from this dialog box.</span></span>|<span data-ttu-id="57bad-127">在 **SSIS** 菜单上，单击 **“包配置”** 。</span><span class="sxs-lookup"><span data-stu-id="57bad-127">On the **SSIS** menu, click **Package Configurations**.</span></span><br /><br /> <span data-ttu-id="57bad-128">-或-</span><span class="sxs-lookup"><span data-stu-id="57bad-128">-or-</span></span><br /><br /> <span data-ttu-id="57bad-129">右键单击“控制流”  选项卡的设计图面上任意位置，再单击“包配置”  。</span><span class="sxs-lookup"><span data-stu-id="57bad-129">Right-click anywhere on the design surface of the **Control Flow** tab, and then click **Package Configurations**.</span></span>|  
|<span data-ttu-id="57bad-130">**数字签名**</span><span class="sxs-lookup"><span data-stu-id="57bad-130">**Digital Signing**</span></span>|<span data-ttu-id="57bad-131">为包签名或从包中删除签名。</span><span class="sxs-lookup"><span data-stu-id="57bad-131">Sign a package or remove the signature from the package.</span></span>|<span data-ttu-id="57bad-132">在 **SSIS** 菜单上，单击 **“数字签名”** 。</span><span class="sxs-lookup"><span data-stu-id="57bad-132">On the **SSIS** menu, click **Digital Signing**.</span></span><br /><br /> <span data-ttu-id="57bad-133">-或-</span><span class="sxs-lookup"><span data-stu-id="57bad-133">-or-</span></span><br /><br /> <span data-ttu-id="57bad-134">右键单击“控制流”  选项卡的设计图面上任意位置，再单击“数字签名”  。</span><span class="sxs-lookup"><span data-stu-id="57bad-134">Right-click anywhere on the design surface of the **Control Flow** tab, and then click **Digital Signing**.</span></span>|  
|<span data-ttu-id="57bad-135">**设置断点**</span><span class="sxs-lookup"><span data-stu-id="57bad-135">**Set Breakpoints**</span></span>|<span data-ttu-id="57bad-136">对任务启用断点，并设置断点属性。</span><span class="sxs-lookup"><span data-stu-id="57bad-136">Enable breakpoints on tasks and set breakpoint properties.</span></span>|<span data-ttu-id="57bad-137">在“控制流”  选项卡的设计图面上，右键单击任务或容器，再单击“编辑断点”  。</span><span class="sxs-lookup"><span data-stu-id="57bad-137">On the design surface of the **Control Flow** tab, right-click a task or container, and then click **Edit Breakpoints**.</span></span> <span data-ttu-id="57bad-138">若要对包设置断点，请右键单击“控制流”  选项卡的设计图面上的任意位置，再单击“编辑断点”  。</span><span class="sxs-lookup"><span data-stu-id="57bad-138">To set a breakpoint on the package, right-click anywhere on the design surface of the **Control Flow** tab, and then click **Edit Breakpoints**.</span></span>|  
  
 <span data-ttu-id="57bad-139">**“入门”** 窗口提供指向示例、教程和视频内容的链接。</span><span class="sxs-lookup"><span data-stu-id="57bad-139">The **Getting Started** window provides links to samples, tutorials, and videos.</span></span> <span data-ttu-id="57bad-140">若要添加指向更多内容的链接，请修改 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]当前版本附带的 SamplesSites.xml 文件。</span><span class="sxs-lookup"><span data-stu-id="57bad-140">To add links to additional content, modify the SamplesSites.xml file that is included with the current release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="57bad-141">建议不要修改指定 RSS 源 URL 的 \<GettingStartedSamples> 元素值。</span><span class="sxs-lookup"><span data-stu-id="57bad-141">It is recommended that you not modify the \<GettingStartedSamples> element value that specifies the RSS feed URL.</span></span> <span data-ttu-id="57bad-142">该文件位于 \<drive>:\Program Files\Microsoft SQL Server\110\DTS\Binn 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="57bad-142">The file is located in the *\<drive>*:\Program Files\Microsoft SQL Server\110\DTS\Binn folder.</span></span> <span data-ttu-id="57bad-143">在 64 位计算机上，该文件位于 \<drive>:\Program Files(x86)\Microsoft SQL Server\110\DTS\Binn 文件夹中</span><span class="sxs-lookup"><span data-stu-id="57bad-143">On a 64-bit computer, the file is located in the *\<drive>*:\Program Files(x86)\Microsoft SQL Server\110\DTS\Binn folder</span></span>  
  
 <span data-ttu-id="57bad-144">如果 SamplesSites.xml 文件确已损坏，请用下面的默认 xml 替换该文件中的 xml。</span><span class="sxs-lookup"><span data-stu-id="57bad-144">If the SamplesSites.xml file does become corrupted, replace the xml in the file with the following default xml.</span></span>  
  
 `<?xml version="1.0" ?>`  
  
 `- <SamplesSites>`  
  
 `<GettingStartedSamples>https://go.microsoft.com/fwlink/?LinkID=203147</GettingStartedSamples>`  
  
 `- <ToolboxSamples>`  
  
 `<Site>https://go.microsoft.com/fwlink/?LinkID=203286&query=SSIS%20{0}</Site>`  
  
 `</ToolboxSamples>`  
  
 `</SamplesSites>`  
  
 <span data-ttu-id="57bad-145">此表列出可从 **SSIS** 和 **“视图”** 菜单以及 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器的设计图面访问的窗口。</span><span class="sxs-lookup"><span data-stu-id="57bad-145">This table lists the windows that are available from the **SSIS** and **View** menus and the design surfaces of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
|<span data-ttu-id="57bad-146">窗口</span><span class="sxs-lookup"><span data-stu-id="57bad-146">Window</span></span>|<span data-ttu-id="57bad-147">目的</span><span class="sxs-lookup"><span data-stu-id="57bad-147">Purpose</span></span>|<span data-ttu-id="57bad-148">访问</span><span class="sxs-lookup"><span data-stu-id="57bad-148">Access</span></span>|  
|------------|-------------|------------|  
|<span data-ttu-id="57bad-149">**变量**</span><span class="sxs-lookup"><span data-stu-id="57bad-149">**Variables**</span></span>|<span data-ttu-id="57bad-150">添加和管理自定义变量。</span><span class="sxs-lookup"><span data-stu-id="57bad-150">Add and manage custom variables.</span></span>|<span data-ttu-id="57bad-151">在 **SSIS** 菜单上单击 **“变量”** 。</span><span class="sxs-lookup"><span data-stu-id="57bad-151">On the **SSIS** menu, click **Variables**.</span></span><br /><br /> <span data-ttu-id="57bad-152">-或-</span><span class="sxs-lookup"><span data-stu-id="57bad-152">-or-</span></span><br /><br /> <span data-ttu-id="57bad-153">右键单击“控制流”  和“数据流”  选项卡的设计图面上任意位置，再单击“变量”  。</span><span class="sxs-lookup"><span data-stu-id="57bad-153">Right-click anywhere in the design surface of the **Control Flow** and **Data Flow** tabs, and then click **Variables**.</span></span><br /><br /> <span data-ttu-id="57bad-154">-或-</span><span class="sxs-lookup"><span data-stu-id="57bad-154">-or-</span></span><br /><br /> <span data-ttu-id="57bad-155">在 **“视图”** 菜单上，指向 **“其他窗口”** ，再单击 **“变量”** 。</span><span class="sxs-lookup"><span data-stu-id="57bad-155">On the **View** menu, point to **Other Windows**, and then click **Variables**.</span></span>|  
|<span data-ttu-id="57bad-156">**日志事件**</span><span class="sxs-lookup"><span data-stu-id="57bad-156">**Log Events**</span></span>|<span data-ttu-id="57bad-157">在运行时查看日志项。</span><span class="sxs-lookup"><span data-stu-id="57bad-157">View log entries at run time.</span></span>|<span data-ttu-id="57bad-158">在 **SSIS** 菜单上单击 **“日志事件”** 。</span><span class="sxs-lookup"><span data-stu-id="57bad-158">On the **SSIS** menu, click **Log Events**.</span></span><br /><br /> <span data-ttu-id="57bad-159">-或-</span><span class="sxs-lookup"><span data-stu-id="57bad-159">-or-</span></span><br /><br /> <span data-ttu-id="57bad-160">右键单击“控制流”  和“数据流”  选项卡的设计图面上的任意位置，再单击“日志事件”  。</span><span class="sxs-lookup"><span data-stu-id="57bad-160">Right-click anywhere in the design surface of the **Control Flow** and **Data Flow** tabs, and then click **Log Events**.</span></span><br /><br /> <span data-ttu-id="57bad-161">-或-</span><span class="sxs-lookup"><span data-stu-id="57bad-161">-or-</span></span><br /><br /> <span data-ttu-id="57bad-162">在 **“视图”** 菜单上指向 **“其他窗口”** ，再单击 **“日志事件”** 。</span><span class="sxs-lookup"><span data-stu-id="57bad-162">On the **View** menu, point to **Other Windows**, and then click **Log Events**.</span></span>|  
  
## <a name="custom-editors"></a><span data-ttu-id="57bad-163">自定义编辑器</span><span class="sxs-lookup"><span data-stu-id="57bad-163">Custom Editors</span></span>  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="57bad-164">为大多数容器、任务、源、转换和目标提供了自定义对话框。</span><span class="sxs-lookup"><span data-stu-id="57bad-164">provides a custom dialog box for most containers, tasks, sources, transformations, and destinations.</span></span>  
  
 <span data-ttu-id="57bad-165">下表介绍如何访问自定义对话框。</span><span class="sxs-lookup"><span data-stu-id="57bad-165">The following table describes how to access custom dialog boxes.</span></span>  
  
|<span data-ttu-id="57bad-166">编辑器类型</span><span class="sxs-lookup"><span data-stu-id="57bad-166">Editor type</span></span>|<span data-ttu-id="57bad-167">访问</span><span class="sxs-lookup"><span data-stu-id="57bad-167">Access</span></span>|  
|-----------------|------------|  
|<span data-ttu-id="57bad-168">容器。</span><span class="sxs-lookup"><span data-stu-id="57bad-168">Container.</span></span> <span data-ttu-id="57bad-169">有关详细信息，请参阅 [Integration Services 容器](control-flow/integration-services-containers.md)。</span><span class="sxs-lookup"><span data-stu-id="57bad-169">For more information, see [Integration Services Containers](control-flow/integration-services-containers.md).</span></span>|<span data-ttu-id="57bad-170">在“控制流”  选项卡的设计图面上，双击容器。</span><span class="sxs-lookup"><span data-stu-id="57bad-170">On the design surface of the **Control Flow** tab, double-click the container.</span></span>|  
|<span data-ttu-id="57bad-171">任务。</span><span class="sxs-lookup"><span data-stu-id="57bad-171">Task.</span></span> <span data-ttu-id="57bad-172">有关详细信息，请参阅 [Integration Services Tasks](control-flow/integration-services-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="57bad-172">For more information, see [Integration Services Tasks](control-flow/integration-services-tasks.md).</span></span>|<span data-ttu-id="57bad-173">在“控制流”  选项卡的设计图面上，双击任务。</span><span class="sxs-lookup"><span data-stu-id="57bad-173">On the design surface of the **Control Flow** tab, double-click the task.</span></span>|  
|<span data-ttu-id="57bad-174">源。</span><span class="sxs-lookup"><span data-stu-id="57bad-174">Source.</span></span>|<span data-ttu-id="57bad-175">在“数据流”  选项卡的设计图面上，双击源。</span><span class="sxs-lookup"><span data-stu-id="57bad-175">On the design surface of the **Data Flow** tab, double-click the source.</span></span>|  
|<span data-ttu-id="57bad-176">转换。</span><span class="sxs-lookup"><span data-stu-id="57bad-176">Transformation.</span></span> <span data-ttu-id="57bad-177">有关详细信息，请参阅 [Integration Services Transformations](data-flow/transformations/integration-services-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="57bad-177">For more information, see [Integration Services Transformations](data-flow/transformations/integration-services-transformations.md).</span></span>|<span data-ttu-id="57bad-178">在“数据流”  选项卡的设计图面上，双击转换。</span><span class="sxs-lookup"><span data-stu-id="57bad-178">On the design surface of the **Data Flow** tab, double-click the transformation.</span></span>|  
|<span data-ttu-id="57bad-179">目标。</span><span class="sxs-lookup"><span data-stu-id="57bad-179">Destination.</span></span>|<span data-ttu-id="57bad-180">在“数据流”  选项卡的设计图面上，双击目标。</span><span class="sxs-lookup"><span data-stu-id="57bad-180">On the design surface of the **Data Flow** tab, double-click the destination.</span></span>|  
  
## <a name="advanced-editor"></a><span data-ttu-id="57bad-181">“高级编辑器”</span><span class="sxs-lookup"><span data-stu-id="57bad-181">Advanced Editor</span></span>  
 <span data-ttu-id="57bad-182">**“高级编辑器”** 对话框是用于配置数据流组件的用户界面。</span><span class="sxs-lookup"><span data-stu-id="57bad-182">The **Advanced Editor** dialog box is a user interface for configuring data flow components.</span></span> <span data-ttu-id="57bad-183">它使用通用的布局反映组件的属性。</span><span class="sxs-lookup"><span data-stu-id="57bad-183">It reflects the properties of the component using a generic layout.</span></span> <span data-ttu-id="57bad-184">**“高级编辑器”** 对话框对具有多个输入的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 转换不可用。</span><span class="sxs-lookup"><span data-stu-id="57bad-184">The **Advanced Editor** dialog box is not available to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] transformations that have multiple inputs.</span></span>  
  
 <span data-ttu-id="57bad-185">若要打开此编辑器，请单击“属性”窗口中的“显示高级编辑器”，或右键单击数据流组件，再单击“显示高级编辑器”。</span><span class="sxs-lookup"><span data-stu-id="57bad-185">To open this editor, click **ShowAdvanced Editor** in the **Properties** window or right-click a data flow component, and then click **ShowAdvanced Editor**.</span></span>  
  
 <span data-ttu-id="57bad-186">如果创建自定义源、转换或目标，但不想编写自定义用户界面，则可以使用 **“高级编辑器”** 。</span><span class="sxs-lookup"><span data-stu-id="57bad-186">If you create a custom source, transformation, or destination but do not want to write a custom user interface, you can use the **Advanced Editor** instead.</span></span>  
  
## <a name="sql-server-data-tools-features"></a><span data-ttu-id="57bad-187">SQL Server Data Tools 功能</span><span class="sxs-lookup"><span data-stu-id="57bad-187">SQL Server Data Tools Features</span></span>  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="57bad-188">提供用于对 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包进行操作的窗口、对话框和菜单选项。</span><span class="sxs-lookup"><span data-stu-id="57bad-188">provides windows, dialog boxes, and menu options for working with [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span>  
  
 <span data-ttu-id="57bad-189">以下是可用窗口和菜单的摘要：</span><span class="sxs-lookup"><span data-stu-id="57bad-189">The following is a summary of the available windows and menus:</span></span>  
  
-   <span data-ttu-id="57bad-190">**“解决方案资源管理器”** 窗口列出项目（包括用于开发 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目）和项目文件。</span><span class="sxs-lookup"><span data-stu-id="57bad-190">The **Solution Explorer** window lists projects, including the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in which you develop [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages, and project files.</span></span>  
  
     <span data-ttu-id="57bad-191">若要按项目中包含的包的名称排序，请右键单击“SSIS 包”  节点，然后单击“按名称排序”  。</span><span class="sxs-lookup"><span data-stu-id="57bad-191">To sort by name the packages contained in a project, right-click the **SSIS Packages** node and then click **Sort by name**.</span></span>  
  
-   <span data-ttu-id="57bad-192">**“工具箱”** 窗口列出用于生成控制流和数据流的控制流项和数据流项。</span><span class="sxs-lookup"><span data-stu-id="57bad-192">The **Toolbox** window lists the control flow and data flow items for building control flows and data flows.</span></span>  
  
-   <span data-ttu-id="57bad-193">**“属性”** 窗口列出对象属性。</span><span class="sxs-lookup"><span data-stu-id="57bad-193">The **Properties** window lists object properties.</span></span>  
  
-   <span data-ttu-id="57bad-194">**“格式”** 菜单提供用于在包中调整控件大小和对齐控件的选项。</span><span class="sxs-lookup"><span data-stu-id="57bad-194">The **Format** menu provides options for sizing and aligning controls in a package.</span></span>  
  
-   <span data-ttu-id="57bad-195">**“编辑”** 菜单提供在设计图面上复制对象的复制和粘贴功能。</span><span class="sxs-lookup"><span data-stu-id="57bad-195">The **Edit** menu provides copy and paste functionality for copying objects on the design surfaces.</span></span>  
  
-   <span data-ttu-id="57bad-196">**“视图”** 菜单提供用于在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中修改对象图形表现形式的选项。</span><span class="sxs-lookup"><span data-stu-id="57bad-196">The **View** menu provides options for modifying the graphical representation of objects in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer</span></span>  
  
 <span data-ttu-id="57bad-197">有关其他窗口和菜单的详细信息，请参阅 Visual Studio 文档。</span><span class="sxs-lookup"><span data-stu-id="57bad-197">For more information about additional windows and menus, see the Visual Studio documentation.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="57bad-198">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="57bad-198">Related Tasks</span></span>  
 <span data-ttu-id="57bad-199">有关如何在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中创建包的信息，请参阅 [在 SQL Server Data Tools 中创建包](create-packages-in-sql-server-data-tools.md)</span><span class="sxs-lookup"><span data-stu-id="57bad-199">For information about how to create packages in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], see [Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57bad-200">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57bad-200">See Also</span></span>  
 [<span data-ttu-id="57bad-201">SSIS 设计器</span><span class="sxs-lookup"><span data-stu-id="57bad-201">SSIS Designer</span></span>](ssis-designer.md)  
  
  
