---
title: 在脚本任务编辑器中配置脚本任务 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], configuring
- Script Task Editor
- SSIS Script task, configuring
ms.assetid: 232de0c9-b24d-4c38-861d-6c1f4a75bdf3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b75b4a030e6c5baa2e26c610b0e8216843c8cca7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579642"
---
# <a name="configuring-the-script-task-in-the-script-task-editor"></a><span data-ttu-id="9d842-102">在脚本任务编辑器中配置脚本任务</span><span class="sxs-lookup"><span data-stu-id="9d842-102">Configuring the Script Task in the Script Task Editor</span></span>
  <span data-ttu-id="9d842-103">在脚本任务中编写自定义代码之前，请在“脚本任务编辑器”  的三个页面中配置它的主要属性。</span><span class="sxs-lookup"><span data-stu-id="9d842-103">Before you write custom code in the Script task, you configure its principal properties in the three pages of the **Script Task Editor**.</span></span> <span data-ttu-id="9d842-104">使用“属性”窗口可以配置非脚本任务特有的其他任务属性。</span><span class="sxs-lookup"><span data-stu-id="9d842-104">You can configure additional task properties that are not unique to the Script task by using the Properties window.</span></span>

> [!NOTE]
>  <span data-ttu-id="9d842-105">在早期版本中，您可以指示是否对脚本进行预编译，而从 [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] 开始，不同的是，所有脚本都要预编译。</span><span class="sxs-lookup"><span data-stu-id="9d842-105">Unlike earlier versions where you could indicate whether scripts were precompiled, all scripts are precompiled beginning in [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)].</span></span>

## <a name="general-page-of-the-script-task-editor"></a><span data-ttu-id="9d842-106">脚本任务编辑器的“常规”页</span><span class="sxs-lookup"><span data-stu-id="9d842-106">General Page of the Script Task Editor</span></span>
 <span data-ttu-id="9d842-107">在“脚本任务编辑器”的“常规”页中，可以为脚本任务分配唯一的名称和说明   。</span><span class="sxs-lookup"><span data-stu-id="9d842-107">On the **General** page of the **Script Task Editor**, you assign a unique name and a description for the Script task.</span></span>

## <a name="script-page-of-the-script-task-editor"></a><span data-ttu-id="9d842-108">脚本任务编辑器的“脚本”页</span><span class="sxs-lookup"><span data-stu-id="9d842-108">Script Page of the Script Task Editor</span></span>
 <span data-ttu-id="9d842-109">“脚本任务编辑器”的“脚本”页显示脚本任务的自定义属性   。</span><span class="sxs-lookup"><span data-stu-id="9d842-109">The **Script** page of the **Script Task Editor** displays the custom properties of the Script task.</span></span>

### <a name="scriptlanguage-property"></a><span data-ttu-id="9d842-110">ScriptLanguage 属性</span><span class="sxs-lookup"><span data-stu-id="9d842-110">ScriptLanguage Property</span></span>
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="9d842-111">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 支持 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# 编程语言。</span><span class="sxs-lookup"><span data-stu-id="9d842-111">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) supports the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# programming languages.</span></span> <span data-ttu-id="9d842-112">在脚本任务中创建脚本后，不能更改“ScriptLanguage”  属性的值。</span><span class="sxs-lookup"><span data-stu-id="9d842-112">After you create a script in the Script task, you cannot change value of the **ScriptLanguage** property.</span></span>

 <span data-ttu-id="9d842-113">若要设置脚本任务和脚本组件的默认脚本语言，请使用“选项”对话框的“常规”页上的“ScriptLanguage”属性    。</span><span class="sxs-lookup"><span data-stu-id="9d842-113">To set the default script language for Script tasks and Script components, use the **ScriptLanguage** property on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="9d842-114">有关详细信息，请参阅 [General Page](../../general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="9d842-114">For more information, see [General Page](../../general-page-of-integration-services-designers-options.md).</span></span>

### <a name="entrypoint-property"></a><span data-ttu-id="9d842-115">EntryPoint 属性</span><span class="sxs-lookup"><span data-stu-id="9d842-115">EntryPoint Property</span></span>
 <span data-ttu-id="9d842-116">`EntryPoint` 属性对 VSTA 项目中的 `ScriptMain` 类指定一种方法，[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 运行时会将该方法作为脚本任务代码的入口点来调用。</span><span class="sxs-lookup"><span data-stu-id="9d842-116">The `EntryPoint` property specifies the method on the `ScriptMain` class in the VSTA project that the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime calls as the entry point into the Script task code.</span></span> <span data-ttu-id="9d842-117">`ScriptMain`类是脚本模板生成的默认类。</span><span class="sxs-lookup"><span data-stu-id="9d842-117">The `ScriptMain` class is the default class generated by the script templates.</span></span>

 <span data-ttu-id="9d842-118">若要更改 VSTA 项目中该方法的名称，必须更改 `EntryPoint` 属性的值。</span><span class="sxs-lookup"><span data-stu-id="9d842-118">If you change the name of the method in the VSTA project, you must change the value of the `EntryPoint` property.</span></span>

### <a name="readonlyvariables-and-readwritevariables-properties"></a><span data-ttu-id="9d842-119">ReadOnlyVariables 和 ReadWriteVariables 属性</span><span class="sxs-lookup"><span data-stu-id="9d842-119">ReadOnlyVariables and ReadWriteVariables Properties</span></span>
 <span data-ttu-id="9d842-120">可以输入以逗号分隔的现有变量列表作为这些属性的值，使这些变量在脚本任务代码中可用于只读或读/写访问。</span><span class="sxs-lookup"><span data-stu-id="9d842-120">You can enter comma-delimited lists of existing variables as the values of these properties to make the variables available for read-only or read/write access within the Script task code.</span></span> <span data-ttu-id="9d842-121">这两种类型的变量都可以在代码中通过 `Dts` 对象的 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 属性来访问。</span><span class="sxs-lookup"><span data-stu-id="9d842-121">Variables of both types are accessed in code through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property of the `Dts` object.</span></span> <span data-ttu-id="9d842-122">有关详细信息，请参阅 [Using Variables in the Script Task](../../extending-packages-scripting/task/using-variables-in-the-script-task.md)。</span><span class="sxs-lookup"><span data-stu-id="9d842-122">For more information, see [Using Variables in the Script Task](../../extending-packages-scripting/task/using-variables-in-the-script-task.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="9d842-123">变量名称区分大小写。</span><span class="sxs-lookup"><span data-stu-id="9d842-123">Variable names are case-sensitive.</span></span>

 <span data-ttu-id="9d842-124">若要选择变量，请单击属性字段旁边的省略号 (…) 按钮  。</span><span class="sxs-lookup"><span data-stu-id="9d842-124">To select the variables, click the ellipsis (**...**) button next to the property field.</span></span> <span data-ttu-id="9d842-125">有关详细信息，请参阅[“选择变量”页](../../control-flow/select-variables-page.md)。</span><span class="sxs-lookup"><span data-stu-id="9d842-125">For more information, see [Select Variables Page](../../control-flow/select-variables-page.md).</span></span>

### <a name="edit-script-button"></a><span data-ttu-id="9d842-126">“编辑脚本”按钮</span><span class="sxs-lookup"><span data-stu-id="9d842-126">Edit Script Button</span></span>
 <span data-ttu-id="9d842-127">“编辑脚本”  按钮用于启动 VSTA 开发环境，可以在其中编写自定义脚本。</span><span class="sxs-lookup"><span data-stu-id="9d842-127">The **Edit Script** button launches the VSTA development environment in which you write your custom script.</span></span> <span data-ttu-id="9d842-128">有关详细信息，请参阅[脚本任务的编码和调试](coding-and-debugging-the-script-task.md)。</span><span class="sxs-lookup"><span data-stu-id="9d842-128">For more information, see [Coding and Debugging the Script Task](coding-and-debugging-the-script-task.md).</span></span>

## <a name="expressions-page-of-the-script-task-editor"></a><span data-ttu-id="9d842-129">脚本任务编辑器的“表达式”页</span><span class="sxs-lookup"><span data-stu-id="9d842-129">Expressions Page of the Script Task Editor</span></span>
 <span data-ttu-id="9d842-130">在“脚本任务编辑器”的“表达式”页中，可以使用表达式为上面列出的脚本任务属性和其他许多任务属性提供值   。</span><span class="sxs-lookup"><span data-stu-id="9d842-130">On the **Expressions** page of the **Script Task Editor**, you can use expressions to provide values for the properties of the Script task listed above and for many other task properties.</span></span> <span data-ttu-id="9d842-131">有关详细信息，请参阅 [Integration Services (SSIS) 表达式](../../expressions/integration-services-ssis-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="9d842-131">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md).</span></span>

<span data-ttu-id="9d842-132">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="9d842-132">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="9d842-133">若要从 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="9d842-133">For the latest downloads, articles, samples, and videos from [!INCLUDE[msCoName](../../../includes/msconame-md.md)], as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="9d842-134">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="9d842-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="9d842-135">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="9d842-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d842-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9d842-136">See Also</span></span>
 [<span data-ttu-id="9d842-137">脚本任务的编码和调试</span><span class="sxs-lookup"><span data-stu-id="9d842-137">Coding and Debugging the Script Task</span></span>](coding-and-debugging-the-script-task.md)


