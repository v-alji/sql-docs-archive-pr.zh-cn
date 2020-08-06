---
title: 脚本任务编辑器 (脚本页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scripttask.script.f1
helpviewer_keywords:
- Script Task Editor
ms.assetid: 93da0e0d-83f5-406d-b144-4cce216571cb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4eec491cc689d7d5c616e0819075e1ee5159d4e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682947"
---
# <a name="script-task-editor-script-page"></a><span data-ttu-id="75275-102">脚本任务编辑器（“脚本”页）</span><span class="sxs-lookup"><span data-stu-id="75275-102">Script Task Editor (Script Page)</span></span>
  <span data-ttu-id="75275-103">使用 **“脚本任务编辑器”** 对话框的 **“脚本”** 页，可以设置脚本属性并指定脚本可以访问的变量。</span><span class="sxs-lookup"><span data-stu-id="75275-103">Use the **Script** page of the **Script Task Editor** dialog box to set script properties and specify variables that can be accessed by the script.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75275-104">在 [!INCLUDE[ssISversion10](../includes/ssisversion10-md.md)] 和更高版本中，所有脚本都将预编译。</span><span class="sxs-lookup"><span data-stu-id="75275-104">In [!INCLUDE[ssISversion10](../includes/ssisversion10-md.md)] and later versions, all scripts are precompiled.</span></span> <span data-ttu-id="75275-105">而在早期版本中，要设置 **PrecompileScriptIntoBinaryCode** 属性来指定是否对脚本进行预编译。</span><span class="sxs-lookup"><span data-stu-id="75275-105">In earlier versions, you set a **PrecompileScriptIntoBinaryCode** property to specify that the script was precompiled.</span></span>  
  
 <span data-ttu-id="75275-106">若要了解有关脚本任务的详细信息，请参阅 [Script Task](control-flow/script-task.md) 和 [在脚本任务编辑器中配置脚本任务](extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="75275-106">To learn more about the Script task, see [Script Task](control-flow/script-task.md) and [Configuring the Script Task in the Script Task Editor](extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md).</span></span> <span data-ttu-id="75275-107">若要了解如何对脚本任务进行编程，请参阅 [Extending the Package with the Script Task](extending-packages-scripting/task/extending-the-package-with-the-script-task.md)。</span><span class="sxs-lookup"><span data-stu-id="75275-107">To learn about programming the Script task, see [Extending the Package with the Script Task](extending-packages-scripting/task/extending-the-package-with-the-script-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="75275-108">选项</span><span class="sxs-lookup"><span data-stu-id="75275-108">Options</span></span>  
 <span data-ttu-id="75275-109">**ScriptLanguage**</span><span class="sxs-lookup"><span data-stu-id="75275-109">**ScriptLanguage**</span></span>  
 <span data-ttu-id="75275-110">选择任务的脚本语言， [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic 或 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#。</span><span class="sxs-lookup"><span data-stu-id="75275-110">Select the scripting language for the task, either [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#.</span></span>  
  
 <span data-ttu-id="75275-111">创建任务的脚本后，将无法更改 **ScriptLanguage** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="75275-111">After you have created a script for the task, you cannot change the value of the **ScriptLanguage** property.</span></span>  
  
 <span data-ttu-id="75275-112">若要设置脚本任务的默认脚本语言，请使用 **“选项”** 对话框的 **“常规”** 页上的 **“脚本语言”** 选项。</span><span class="sxs-lookup"><span data-stu-id="75275-112">To set the default scripting language for the Script task, use the **Scripting language** option on **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="75275-113">有关详细信息，请参阅 [General Page](general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="75275-113">For more information, see [General Page](general-page-of-integration-services-designers-options.md).</span></span>  
  
 <span data-ttu-id="75275-114">**EntryPoint**</span><span class="sxs-lookup"><span data-stu-id="75275-114">**EntryPoint**</span></span>  
 <span data-ttu-id="75275-115">指定 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 运行时作为脚本任务代码入口点调用的方法。</span><span class="sxs-lookup"><span data-stu-id="75275-115">Specify the method that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] runtime calls as the entry point into the code of the Script task.</span></span> <span data-ttu-id="75275-116">指定的方法必须位于 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (VSTA 的 Tools for Applications) 项目中的 ScriptMain 类。 ScriptMain 类是脚本模板生成的默认类。</span><span class="sxs-lookup"><span data-stu-id="75275-116">The specified method must be in the ScriptMain class of the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA) project The ScriptMain class is the default class generated by the script templates.</span></span>  
  
 <span data-ttu-id="75275-117">若要更改 VSTA 项目中方法的名称，则必须更改 **EntryPoint** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="75275-117">If you change the name of the method in the VSTA project, you must change the value of the **EntryPoint** property.</span></span>  
  
 <span data-ttu-id="75275-118">**ReadOnlyVariables**</span><span class="sxs-lookup"><span data-stu-id="75275-118">**ReadOnlyVariables**</span></span>  
 <span data-ttu-id="75275-119">以逗号分隔的形式键入一列可供脚本使用的只读变量，或单击省略号 (…) 按钮，然后在“选择变量”对话框中选择变量\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="75275-119">Type a comma-separated list of read-only variables that are available to the script, or click the ellipsis (**...**) button and select the variables in the **Select variables** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75275-120">变量名称区分大小写。</span><span class="sxs-lookup"><span data-stu-id="75275-120">Variable names are case sensitive.</span></span>  
  
 <span data-ttu-id="75275-121">**ReadWriteVariables**</span><span class="sxs-lookup"><span data-stu-id="75275-121">**ReadWriteVariables**</span></span>  
 <span data-ttu-id="75275-122">以逗号分隔的形式键入一列可供脚本使用的读/写变量，或单击省略号 (…) 按钮，然后在“选择变量”对话框中选择变量\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="75275-122">Type a comma-separated list of read/write variables that are available to the script, or click the ellipsis (**...**) button and select the variables in the **Select variables** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75275-123">变量名称区分大小写。</span><span class="sxs-lookup"><span data-stu-id="75275-123">Variable names are case sensitive.</span></span>  
  
 <span data-ttu-id="75275-124">**编辑脚本**</span><span class="sxs-lookup"><span data-stu-id="75275-124">**Edit Script**</span></span>  
 <span data-ttu-id="75275-125">打开 VSTA IDE，您可以在其中创建或修改脚本。</span><span class="sxs-lookup"><span data-stu-id="75275-125">Opens the VSTA IDE where you can create or modify the script.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75275-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="75275-126">See Also</span></span>  
 <span data-ttu-id="75275-127">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="75275-127">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="75275-128">[常规页](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="75275-128">[General Page](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="75275-129">[脚本任务编辑器 &#40;常规 "页面&#41;](../../2014/integration-services/script-task-editor-general-page.md) </span><span class="sxs-lookup"><span data-stu-id="75275-129">[Script Task Editor &#40;General Page&#41;](../../2014/integration-services/script-task-editor-general-page.md) </span></span>  
 <span data-ttu-id="75275-130">[“表达式”页](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="75275-130">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="75275-131">[脚本任务示例](extending-packages-scripting-task-examples/script-task-examples.md) </span><span class="sxs-lookup"><span data-stu-id="75275-131">[Script Task Examples](extending-packages-scripting-task-examples/script-task-examples.md) </span></span>  
 <span data-ttu-id="75275-132">[Integration Services (SSIS) 变量](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="75275-132">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 [<span data-ttu-id="75275-133">添加、删除、更改包中用户定义变量的作用域</span><span class="sxs-lookup"><span data-stu-id="75275-133">Add, Delete, Change Scope of User-Defined Variable in a Package</span></span>](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  
