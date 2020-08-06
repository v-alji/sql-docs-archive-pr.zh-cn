---
title: 脚本转换编辑器 (脚本页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.script.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: 4c6d1901-ef21-4aa7-9d0a-6bbeb7fadf1c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: df89bddd0a2f12e1d0efe0db74f4e10aadd772eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586780"
---
# <a name="script-transformation-editor-script-page"></a><span data-ttu-id="b00b2-102">脚本转换编辑器（“脚本”页）</span><span class="sxs-lookup"><span data-stu-id="b00b2-102">Script Transformation Editor (Script Page)</span></span>
  <span data-ttu-id="b00b2-103">可以使用 **“脚本转换编辑器”** 对话框的 **“脚本”** 选项卡指定脚本及相关属性。</span><span class="sxs-lookup"><span data-stu-id="b00b2-103">Use the **Script** tab of the **Script Transformation Editor** dialog box to specify a script and related properties.</span></span>  
  
 <span data-ttu-id="b00b2-104">若要了解有关脚本组件的详细信息，请参阅 [Script Component](data-flow/transformations/script-component.md) 和 [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="b00b2-104">To learn more about the Script component, see [Script Component](data-flow/transformations/script-component.md) and [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span> <span data-ttu-id="b00b2-105">若要了解如何对脚本组件进行编程，请参阅 [使用脚本组件扩展数据流](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="b00b2-105">To learn about programming the Script component, see [Extending the Data Flow with the Script Component](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b00b2-106">选项</span><span class="sxs-lookup"><span data-stu-id="b00b2-106">Options</span></span>  
 <span data-ttu-id="b00b2-107">**属性**</span><span class="sxs-lookup"><span data-stu-id="b00b2-107">**Properties**</span></span>  
 <span data-ttu-id="b00b2-108">查看和修改脚本转换的属性。</span><span class="sxs-lookup"><span data-stu-id="b00b2-108">View and modify the properties of the Script transformation.</span></span> <span data-ttu-id="b00b2-109">显示的许多属性是只读的。</span><span class="sxs-lookup"><span data-stu-id="b00b2-109">Many of the properties displayed are read-only.</span></span> <span data-ttu-id="b00b2-110">您可以修改以下属性：</span><span class="sxs-lookup"><span data-stu-id="b00b2-110">You can modify the following properties:</span></span>  
  
|<span data-ttu-id="b00b2-111">值</span><span class="sxs-lookup"><span data-stu-id="b00b2-111">Value</span></span>|<span data-ttu-id="b00b2-112">说明</span><span class="sxs-lookup"><span data-stu-id="b00b2-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b00b2-113">**说明**</span><span class="sxs-lookup"><span data-stu-id="b00b2-113">**Description**</span></span>|<span data-ttu-id="b00b2-114">说明脚本转换的用途。</span><span class="sxs-lookup"><span data-stu-id="b00b2-114">Describe the script transformation in terms of its purpose.</span></span>|  
|<span data-ttu-id="b00b2-115">**LocaleID**</span><span class="sxs-lookup"><span data-stu-id="b00b2-115">**LocaleID**</span></span>|<span data-ttu-id="b00b2-116">指定区域设置，以便为排序以及日期和时间转换提供区域特定的信息。</span><span class="sxs-lookup"><span data-stu-id="b00b2-116">Specify the locale to provide region-specific information for ordering, and for date and time conversion.</span></span>|  
|<span data-ttu-id="b00b2-117">**名称**</span><span class="sxs-lookup"><span data-stu-id="b00b2-117">**Name**</span></span>|<span data-ttu-id="b00b2-118">为组件键入说明性名称。</span><span class="sxs-lookup"><span data-stu-id="b00b2-118">Type a descriptive name for the component.</span></span>|  
|<span data-ttu-id="b00b2-119">**ValidateExternalMetadata**</span><span class="sxs-lookup"><span data-stu-id="b00b2-119">**ValidateExternalMetadata**</span></span>|<span data-ttu-id="b00b2-120">指示在设计时脚本转换是否要根据外部数据源对列的元数据进行验证。</span><span class="sxs-lookup"><span data-stu-id="b00b2-120">Indicate whether the Script transformation validates column metadata against external data sources at design time.</span></span> <span data-ttu-id="b00b2-121">如果值为 `false`，则会将验证延迟到执行时。</span><span class="sxs-lookup"><span data-stu-id="b00b2-121">A value of `false` delays validation until the time of execution.</span></span>|  
|<span data-ttu-id="b00b2-122">**ReadOnlyVariables**</span><span class="sxs-lookup"><span data-stu-id="b00b2-122">**ReadOnlyVariables**</span></span>|<span data-ttu-id="b00b2-123">以逗号分隔的形式键入一列可供脚本转换只读访问的变量。</span><span class="sxs-lookup"><span data-stu-id="b00b2-123">Type a comma-separated list of variables for read-only access by the Script transformation.</span></span><br /><br /> <span data-ttu-id="b00b2-124">注意：变量名称区分大小写。</span><span class="sxs-lookup"><span data-stu-id="b00b2-124">Note: Variable names are case-sensitive.</span></span>|  
|<span data-ttu-id="b00b2-125">**ReadWriteVariables**</span><span class="sxs-lookup"><span data-stu-id="b00b2-125">**ReadWriteVariables**</span></span>|<span data-ttu-id="b00b2-126">以逗号分隔的形式键入一列可供脚本转换读/写访问的变量。</span><span class="sxs-lookup"><span data-stu-id="b00b2-126">Type a comma-separated list of variables for read/write access by the Script transformation.</span></span><br /><br /> <span data-ttu-id="b00b2-127">注意：变量名称区分大小写。</span><span class="sxs-lookup"><span data-stu-id="b00b2-127">Note: Variable names are case-sensitive.</span></span>|  
|<span data-ttu-id="b00b2-128">**ScriptLanguage**</span><span class="sxs-lookup"><span data-stu-id="b00b2-128">**ScriptLanguage**</span></span>|<span data-ttu-id="b00b2-129">选择脚本组件要使用的脚本语言。</span><span class="sxs-lookup"><span data-stu-id="b00b2-129">Select the script language to be used by the Script component.</span></span><br /><br /> <span data-ttu-id="b00b2-130">若要设置脚本组件和脚本任务的默认脚本语言，请使用 **“选项”** 对话框的 **“常规”** 页上的 **“脚本语言”** 选项。</span><span class="sxs-lookup"><span data-stu-id="b00b2-130">To set the default script language for Script components and Script tasks, use the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="b00b2-131">有关详细信息，请参阅 [General Page](general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="b00b2-131">For more information, see [General Page](general-page-of-integration-services-designers-options.md).</span></span>|  
|<span data-ttu-id="b00b2-132">**UserComponentTypeName**</span><span class="sxs-lookup"><span data-stu-id="b00b2-132">**UserComponentTypeName**</span></span>|<span data-ttu-id="b00b2-133">指定 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost> 类和支持 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 基础结构的 `Microsoft.SqlServer.TxScript` 程序集。</span><span class="sxs-lookup"><span data-stu-id="b00b2-133">Specifies the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost> class and the `Microsoft.SqlServer.TxScript` assembly that support the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] infrastructure.</span></span>|  
  
 <span data-ttu-id="b00b2-134">**编辑脚本**</span><span class="sxs-lookup"><span data-stu-id="b00b2-134">**Edit Script**</span></span>  
 <span data-ttu-id="b00b2-135">使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA) 创建或修改脚本。</span><span class="sxs-lookup"><span data-stu-id="b00b2-135">Use [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA) to create or modify a script.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b00b2-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b00b2-136">See Also</span></span>  
 <span data-ttu-id="b00b2-137">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b00b2-137">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="b00b2-138">[选择脚本组件类型](../../2014/integration-services/select-script-component-type.md) </span><span class="sxs-lookup"><span data-stu-id="b00b2-138">[Select Script Component Type](../../2014/integration-services/select-script-component-type.md) </span></span>  
 <span data-ttu-id="b00b2-139">[脚本转换编辑器 &#40;输入列 "页&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="b00b2-139">[Script Transformation Editor &#40;Input Columns Page&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md) </span></span>  
 <span data-ttu-id="b00b2-140">[脚本转换编辑器 &#40;"输入和输出" 页&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md) </span><span class="sxs-lookup"><span data-stu-id="b00b2-140">[Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md) </span></span>  
 <span data-ttu-id="b00b2-141">[脚本转换编辑器 &#40;连接管理器页&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span><span class="sxs-lookup"><span data-stu-id="b00b2-141">[Script Transformation Editor &#40;Connection Managers Page&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span></span>  
 [<span data-ttu-id="b00b2-142">其他脚本组件示例</span><span class="sxs-lookup"><span data-stu-id="b00b2-142">Additional Script Component Examples</span></span>](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
