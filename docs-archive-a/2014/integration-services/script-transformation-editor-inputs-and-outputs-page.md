---
title: ) 的 "输入和输出" 页的脚本转换编辑器 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.columnproperties.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: 9659d2d2-5d73-4470-9768-e07b77142fc9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 16adf74a1cd8f0c778bc18eaff84437b8fc13603
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682940"
---
# <a name="script-transformation-editor-inputs-and-outputs-page"></a><span data-ttu-id="b8f62-102">脚本转换编辑器（“输入和输出”页）</span><span class="sxs-lookup"><span data-stu-id="b8f62-102">Script Transformation Editor (Inputs and Outputs Page)</span></span>
  <span data-ttu-id="b8f62-103">可以使用 **“脚本转换编辑器”** 对话框的 **“输入和输出”** 页，添加、删除和配置脚本转换的输入和输出。</span><span class="sxs-lookup"><span data-stu-id="b8f62-103">Use the **Inputs and Outputs** page of the **Script Transformation Editor** dialog box to add, remove, and configure inputs and outputs for the Script Transformation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b8f62-104">源组件有输出但没有输入，而目标组件有输入但没有输出。</span><span class="sxs-lookup"><span data-stu-id="b8f62-104">Source components have outputs and no inputs, while destination components have inputs but no outputs.</span></span> <span data-ttu-id="b8f62-105">转换既有输入，也有输出。</span><span class="sxs-lookup"><span data-stu-id="b8f62-105">Transformations have both inputs and outputs.</span></span>  
  
 <span data-ttu-id="b8f62-106">若要了解有关脚本组件的详细信息，请参阅 [Script Component](data-flow/transformations/script-component.md) 和 [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="b8f62-106">To learn more about the Script component, see [Script Component](data-flow/transformations/script-component.md) and [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span> <span data-ttu-id="b8f62-107">若要了解如何对脚本组件进行编程，请参阅 [使用脚本组件扩展数据流](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="b8f62-107">To learn about programming the Script component, see [Extending the Data Flow with the Script Component](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b8f62-108">选项</span><span class="sxs-lookup"><span data-stu-id="b8f62-108">Options</span></span>  
 <span data-ttu-id="b8f62-109">**Inputs and outputs**</span><span class="sxs-lookup"><span data-stu-id="b8f62-109">**Inputs and outputs**</span></span>  
 <span data-ttu-id="b8f62-110">在左侧选择输入或输出即可在右侧的表中查看其属性。</span><span class="sxs-lookup"><span data-stu-id="b8f62-110">Select an input or output on the left to view its properties in the table on the right.</span></span> <span data-ttu-id="b8f62-111">选择不同的输入或输出，可编辑的属性也有所不同。</span><span class="sxs-lookup"><span data-stu-id="b8f62-111">Properties available for editing vary according to the selection.</span></span> <span data-ttu-id="b8f62-112">显示的许多属性是只读的。</span><span class="sxs-lookup"><span data-stu-id="b8f62-112">Many of the properties displayed are read-only.</span></span> <span data-ttu-id="b8f62-113">有关各个属性的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="b8f62-113">For more information on the individual properties, see the following topics.</span></span>  
  
 [<span data-ttu-id="b8f62-114">Common Properties</span><span class="sxs-lookup"><span data-stu-id="b8f62-114">Common Properties</span></span>](../../2014/integration-services/common-properties.md)  
  
 [<span data-ttu-id="b8f62-115">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="b8f62-115">Transformation Custom Properties</span></span>](data-flow/transformations/transformation-custom-properties.md)  
  
 <span data-ttu-id="b8f62-116">**添加输出**</span><span class="sxs-lookup"><span data-stu-id="b8f62-116">**Add Output**</span></span>  
 <span data-ttu-id="b8f62-117">将其他输出添加到列表中。</span><span class="sxs-lookup"><span data-stu-id="b8f62-117">Add an additional output to the list.</span></span>  
  
 <span data-ttu-id="b8f62-118">**添加列**</span><span class="sxs-lookup"><span data-stu-id="b8f62-118">**Add Column**</span></span>  
 <span data-ttu-id="b8f62-119">选择用于放置新输出列的文件夹，再单击“添加列”  来添加该列。</span><span class="sxs-lookup"><span data-stu-id="b8f62-119">Select a folder in which to place the new output column, and then add the column by clicking **Add Column**.</span></span>  
  
 <span data-ttu-id="b8f62-120">**删除输出**</span><span class="sxs-lookup"><span data-stu-id="b8f62-120">**Remove Output**</span></span>  
 <span data-ttu-id="b8f62-121">选择某个输出，再单击“删除输出”  即可将其删除。</span><span class="sxs-lookup"><span data-stu-id="b8f62-121">Select an output, and then remove it by clicking **Remove Output**.</span></span>  
  
 <span data-ttu-id="b8f62-122">**删除列**</span><span class="sxs-lookup"><span data-stu-id="b8f62-122">**Remove Column**</span></span>  
 <span data-ttu-id="b8f62-123">选择某个列，然后单击“删除列”  来删除该列。</span><span class="sxs-lookup"><span data-stu-id="b8f62-123">Select a column, and then remove it by clicking **Remove Column**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8f62-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b8f62-124">See Also</span></span>  
 <span data-ttu-id="b8f62-125">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b8f62-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="b8f62-126">[选择脚本组件类型](../../2014/integration-services/select-script-component-type.md) </span><span class="sxs-lookup"><span data-stu-id="b8f62-126">[Select Script Component Type](../../2014/integration-services/select-script-component-type.md) </span></span>  
 <span data-ttu-id="b8f62-127">[脚本转换编辑器 &#40;输入列 "页&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="b8f62-127">[Script Transformation Editor &#40;Input Columns Page&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md) </span></span>  
 <span data-ttu-id="b8f62-128">[脚本转换编辑器 &#40;脚本页&#41;](../../2014/integration-services/script-transformation-editor-script-page.md) </span><span class="sxs-lookup"><span data-stu-id="b8f62-128">[Script Transformation Editor &#40;Script Page&#41;](../../2014/integration-services/script-transformation-editor-script-page.md) </span></span>  
 <span data-ttu-id="b8f62-129">[脚本转换编辑器 &#40;连接管理器页&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span><span class="sxs-lookup"><span data-stu-id="b8f62-129">[Script Transformation Editor &#40;Connection Managers Page&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span></span>  
 [<span data-ttu-id="b8f62-130">其他脚本组件示例</span><span class="sxs-lookup"><span data-stu-id="b8f62-130">Additional Script Component Examples</span></span>](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
