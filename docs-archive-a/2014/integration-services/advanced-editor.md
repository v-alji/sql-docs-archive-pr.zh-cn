---
title: “高级编辑器” | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.advancededitor.columnmappings.f1
- sql12.dts.designer.advancededitor.inputcolumns.f1
- sql12.dts.designer.advancededitor.columnproperties.f1
- sql12.dts.designer.advancededitor.componentproperties.f1
- sql12.dts.designer.advancededitor.connections.f1
ms.assetid: 5ad0ac71-fa8b-4c26-bd42-e6ef00c87571
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7f4897f2589acdeb93efecbdf9aacde07d21ca42
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579727"
---
# <a name="advanced-editor"></a><span data-ttu-id="c069d-102">“高级编辑器”</span><span class="sxs-lookup"><span data-stu-id="c069d-102">Advanced Editor</span></span>
  <span data-ttu-id="c069d-103">使用 **“高级编辑器”** 对话框可为所选 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 对象配置属性。</span><span class="sxs-lookup"><span data-stu-id="c069d-103">Use the **Advanced Editor** dialog box to configure to configure properties for the selected [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="c069d-104">对于具有可配置属性的大多数 **对象，** “高级编辑器” [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 都是可用的。</span><span class="sxs-lookup"><span data-stu-id="c069d-104">The **Advanced Editor** is available for most [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] objects that have configurable properties.</span></span> <span data-ttu-id="c069d-105">对于未公开自定义用户界面的对象，它是唯一可用的编辑器。</span><span class="sxs-lookup"><span data-stu-id="c069d-105">It is the only editor available for those objects that do not expose a custom user interface.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="c069d-106">数据流对象具有可以在组件级、输入和输出级以及输入和输出列级设置的属性。</span><span class="sxs-lookup"><span data-stu-id="c069d-106">data flow objects have properties that can be set at the component level, the input and output level, and the input and output column level.</span></span> <span data-ttu-id="c069d-107">**“高级编辑器”** 可以枚举所选对象的全部通用和自定义属性，并最多可在下列五个选项卡中的四个选项卡上显示相应的属性：</span><span class="sxs-lookup"><span data-stu-id="c069d-107">The **Advanced Editor** enumerates all the common and custom properties of the selected object and displays them on up to four of the following five tabs as applicable:</span></span>  
  
-   <span data-ttu-id="c069d-108"> “连接管理器”-- 使用此选项卡可以设置连接属性</span><span class="sxs-lookup"><span data-stu-id="c069d-108">**Connection Managers** -- use this tab to set connection properties</span></span>  
  
-   <span data-ttu-id="c069d-109"> “组件属性”-- 使用此选项卡可以设置组件级别属性</span><span class="sxs-lookup"><span data-stu-id="c069d-109">**Component Properties** -- use this tab to set component-level properties</span></span>  
  
-   <span data-ttu-id="c069d-110"> “列映射”-- 使用此选项卡可将可用列映射为输出列</span><span class="sxs-lookup"><span data-stu-id="c069d-110">**Column Mappings** -- use this tab to map available columns as output columns</span></span>  
  
-   <span data-ttu-id="c069d-111"> “输入列”-- 使用此选项卡可选择输入列</span><span class="sxs-lookup"><span data-stu-id="c069d-111">**Input Columns** -- use this tab to select input columns</span></span>  
  
-   <span data-ttu-id="c069d-112"> “输入和输出属性”-- 使用此选项卡可设置输入和输出属性；并且可以添加和删除输出、为输入和输出选择或删除列以及为输入和输出设置属性</span><span class="sxs-lookup"><span data-stu-id="c069d-112">**Input and Output Properties** -- use this tab to set input and output properties; and to add and remove outputs, select or remove columns for inputs and outputs, and set properties for inputs and outputs</span></span>  
  
 <span data-ttu-id="c069d-113">所显示的属性因组件而异。</span><span class="sxs-lookup"><span data-stu-id="c069d-113">The properties displayed vary by component.</span></span> <span data-ttu-id="c069d-114">有关可能在 **“高级编辑器”** 中显示的属性的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="c069d-114">For more information on the properties that may be displayed in the **Advanced Editor**, see the following topics:</span></span>  
  
-   [<span data-ttu-id="c069d-115">Common Properties</span><span class="sxs-lookup"><span data-stu-id="c069d-115">Common Properties</span></span>](../../2014/integration-services/common-properties.md)  
  
-   [<span data-ttu-id="c069d-116">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="c069d-116">Transformation Custom Properties</span></span>](data-flow/transformations/transformation-custom-properties.md)  
  
-   [<span data-ttu-id="c069d-117">路径属性</span><span class="sxs-lookup"><span data-stu-id="c069d-117">Path Properties</span></span>](../../2014/integration-services/path-properties.md)  
  
 <span data-ttu-id="c069d-118">有关您所编辑的特定组件的详细信息，请参阅 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 对象和概念文档的“数据流元素”部分中的组件说明。</span><span class="sxs-lookup"><span data-stu-id="c069d-118">For more information about the specific component that you are editing, see the description of the component in the Data Flow Elements section of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Objects and Concepts documentation:</span></span>  
  
-   [<span data-ttu-id="c069d-119">Integration Services 转换</span><span class="sxs-lookup"><span data-stu-id="c069d-119">Integration Services Transformations</span></span>](data-flow/transformations/integration-services-transformations.md)  
  
## <a name="see-also"></a><span data-ttu-id="c069d-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c069d-120">See Also</span></span>  
 [<span data-ttu-id="c069d-121">Integration Services 错误和消息引用</span><span class="sxs-lookup"><span data-stu-id="c069d-121">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
