---
title: 脚本转换编辑器 (输入列) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.inputcolumn.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: d6e4ce84-3335-48e6-82d3-1c359ed87f63
author: chugugrace
ms.author: chugu
ms.openlocfilehash: daffb52b62ad59ae4fe574d7fa27d4820b9cb5a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682942"
---
# <a name="script-transformation-editor-input-columns-page"></a><span data-ttu-id="9750a-102">脚本转换编辑器（“输入列”页）</span><span class="sxs-lookup"><span data-stu-id="9750a-102">Script Transformation Editor (Input Columns Page)</span></span>
  <span data-ttu-id="9750a-103">可以使用 **“脚本转换编辑器”** 对话框的 **“输入列”** 页设置输入列的属性。</span><span class="sxs-lookup"><span data-stu-id="9750a-103">Use the **Input Columns** page of the **Script Transformation Editor** dialog box to set properties on input columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9750a-104">由于源组件只有输出而没有输入，因此对于源组件不能显示“输入列”页  。</span><span class="sxs-lookup"><span data-stu-id="9750a-104">The **Input Columns** page is not displayed for Source components, which have outputs but no inputs.</span></span>  
  
 <span data-ttu-id="9750a-105">若要了解有关脚本组件的详细信息，请参阅 [Script Component](data-flow/transformations/script-component.md) 和 [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="9750a-105">To learn more about the Script component, see [Script Component](data-flow/transformations/script-component.md) and [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span> <span data-ttu-id="9750a-106">若要了解如何对脚本组件进行编程，请参阅 [使用脚本组件扩展数据流](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="9750a-106">To learn about programming the Script component, see [Extending the Data Flow with the Script Component](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="9750a-107">选项</span><span class="sxs-lookup"><span data-stu-id="9750a-107">Options</span></span>  
 <span data-ttu-id="9750a-108">**输入名称**</span><span class="sxs-lookup"><span data-stu-id="9750a-108">**Input name**</span></span>  
 <span data-ttu-id="9750a-109">从可用输入的列表中选择。</span><span class="sxs-lookup"><span data-stu-id="9750a-109">Select from the list of available inputs.</span></span>  
  
 <span data-ttu-id="9750a-110">**可用输入列**</span><span class="sxs-lookup"><span data-stu-id="9750a-110">**Available Input Columns**</span></span>  
 <span data-ttu-id="9750a-111">使用复选框指定脚本转换要使用的列。</span><span class="sxs-lookup"><span data-stu-id="9750a-111">Using the check boxes, specify the columns that the script transformation will use.</span></span>  
  
 <span data-ttu-id="9750a-112">**输入列**</span><span class="sxs-lookup"><span data-stu-id="9750a-112">**Input Column**</span></span>  
 <span data-ttu-id="9750a-113">从每行的可用输入列的列表中选择。</span><span class="sxs-lookup"><span data-stu-id="9750a-113">Select from the list of available input columns for each row.</span></span> <span data-ttu-id="9750a-114">通过选中“可用输入列”  表中的复选框来选择列。</span><span class="sxs-lookup"><span data-stu-id="9750a-114">Your selections are reflected in the check box selections in the **Available Input Columns**table.</span></span>  
  
 <span data-ttu-id="9750a-115">**输出别名**</span><span class="sxs-lookup"><span data-stu-id="9750a-115">**Output Alias**</span></span>  
 <span data-ttu-id="9750a-116">为每个输出列键入一个别名。</span><span class="sxs-lookup"><span data-stu-id="9750a-116">Type an alias for each output column.</span></span> <span data-ttu-id="9750a-117">默认值为输入列的名称；不过，您也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="9750a-117">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="9750a-118">**使用类型**</span><span class="sxs-lookup"><span data-stu-id="9750a-118">**Usage Type**</span></span>  
 <span data-ttu-id="9750a-119">指定脚本转换是将每个列视为 `ReadOnly` 还是 `ReadWrite`。</span><span class="sxs-lookup"><span data-stu-id="9750a-119">Specify whether the Script Transformation will treat each column as `ReadOnly` or `ReadWrite`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9750a-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9750a-120">See Also</span></span>  
 <span data-ttu-id="9750a-121">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9750a-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="9750a-122">[选择脚本组件类型](../../2014/integration-services/select-script-component-type.md) </span><span class="sxs-lookup"><span data-stu-id="9750a-122">[Select Script Component Type](../../2014/integration-services/select-script-component-type.md) </span></span>  
 <span data-ttu-id="9750a-123">[脚本转换编辑器 &#40;"输入和输出" 页&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md) </span><span class="sxs-lookup"><span data-stu-id="9750a-123">[Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md) </span></span>  
 <span data-ttu-id="9750a-124">[脚本转换编辑器 &#40;脚本页&#41;](../../2014/integration-services/script-transformation-editor-script-page.md) </span><span class="sxs-lookup"><span data-stu-id="9750a-124">[Script Transformation Editor &#40;Script Page&#41;](../../2014/integration-services/script-transformation-editor-script-page.md) </span></span>  
 <span data-ttu-id="9750a-125">[脚本转换编辑器 &#40;连接管理器页&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span><span class="sxs-lookup"><span data-stu-id="9750a-125">[Script Transformation Editor &#40;Connection Managers Page&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span></span>  
 [<span data-ttu-id="9750a-126">其他脚本组件示例</span><span class="sxs-lookup"><span data-stu-id="9750a-126">Additional Script Component Examples</span></span>](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
