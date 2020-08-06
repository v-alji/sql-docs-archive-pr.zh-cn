---
title: 变量网格选项 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.variableoptionswindow.f1
helpviewer_keywords:
- Choose Variable Columns dialog box
ms.assetid: 7cccc230-3b20-4074-804f-3448d9616a83
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b90e1a3c69e4eaf1f123603e0082ecb1eda4e893
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578931"
---
# <a name="variable-grid-options"></a><span data-ttu-id="ac3b2-102">变量网格选项</span><span class="sxs-lookup"><span data-stu-id="ac3b2-102">Variable Grid Options</span></span>
  <span data-ttu-id="ac3b2-103">使用 **“变量网格选项”** 对话框，可以选择将在 **“变量”** 窗口中显示的列并选择要应用于变量列表的筛选器。</span><span class="sxs-lookup"><span data-stu-id="ac3b2-103">Use the **Variable Grid Options** dialog box to select the columns that will display in the **Variables** window and to select the filters to apply to the list of variables.</span></span> <span data-ttu-id="ac3b2-104">有关相应变量属性的详细信息，请参阅 [Integration Services (SSIS) 变量](integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="ac3b2-104">For more information about the corresponding variable properties, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>  
  
## <a name="options-for-filter"></a><span data-ttu-id="ac3b2-105">筛选器选项</span><span class="sxs-lookup"><span data-stu-id="ac3b2-105">Options for Filter</span></span>  
 <span data-ttu-id="ac3b2-106">**显示系统变量**</span><span class="sxs-lookup"><span data-stu-id="ac3b2-106">**Show system variables**</span></span>  
 <span data-ttu-id="ac3b2-107">选择此项可在“变量”\*\*\*\* 窗口中列出系统变量。</span><span class="sxs-lookup"><span data-stu-id="ac3b2-107">Select to list system variables in the **Variables** window.</span></span> <span data-ttu-id="ac3b2-108">系统变量是预定义的。</span><span class="sxs-lookup"><span data-stu-id="ac3b2-108">System variables are predefined.</span></span> <span data-ttu-id="ac3b2-109">您无法添加或删除系统变量。</span><span class="sxs-lookup"><span data-stu-id="ac3b2-109">You cannot add or delete system variables.</span></span> <span data-ttu-id="ac3b2-110">可以修改 **“RaiseChangedEvent”** 属性设置。</span><span class="sxs-lookup"><span data-stu-id="ac3b2-110">You can modify the **RaiseChangedEvent** property setting.</span></span>  
  
 <span data-ttu-id="ac3b2-111">此列表使用颜色进行标记。</span><span class="sxs-lookup"><span data-stu-id="ac3b2-111">This list is color coded.</span></span> <span data-ttu-id="ac3b2-112">系统变量呈灰色，而用户定义变量则呈黑色。</span><span class="sxs-lookup"><span data-stu-id="ac3b2-112">System variables are gray, and user-defined variables are black.</span></span>  
  
 <span data-ttu-id="ac3b2-113">**显示所有作用域的变量**</span><span class="sxs-lookup"><span data-stu-id="ac3b2-113">**Show variables of all scopes**</span></span>  
 <span data-ttu-id="ac3b2-114">选择以显示包范围内的变量以及包中的容器、任务和事件处理程序范围内的变量。</span><span class="sxs-lookup"><span data-stu-id="ac3b2-114">Select to show variables within the scope the package, and within the scope of containers, tasks, and event handlers in the package.</span></span> <span data-ttu-id="ac3b2-115">清除此选项以仅显示包范围内的变量以及所选容器、任务或事件处理程序范围内的变量。</span><span class="sxs-lookup"><span data-stu-id="ac3b2-115">Clear this option to show only variables within the scope of the package and within the scope of a selected container, task, or event handler.</span></span>  
  
 <span data-ttu-id="ac3b2-116">有关变量作用域的详细信息，请参阅 [Integration Services (SSIS) 变量](integration-services-ssis-variables.md)区域之下。</span><span class="sxs-lookup"><span data-stu-id="ac3b2-116">For more information about variable scope, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>  
  
## <a name="options-for-columns"></a><span data-ttu-id="ac3b2-117">列选项</span><span class="sxs-lookup"><span data-stu-id="ac3b2-117">Options for Columns</span></span>  
 <span data-ttu-id="ac3b2-118">选择希望在 **“变量”** 窗口中显示的列。</span><span class="sxs-lookup"><span data-stu-id="ac3b2-118">Select the columns that you want to appear in the **Variables** window.</span></span>  
  
-   <span data-ttu-id="ac3b2-119">**范围**</span><span class="sxs-lookup"><span data-stu-id="ac3b2-119">**Scope**</span></span>  
  
-   <span data-ttu-id="ac3b2-120">**Data type**</span><span class="sxs-lookup"><span data-stu-id="ac3b2-120">**Data type**</span></span>  
  
-   <span data-ttu-id="ac3b2-121">**值**</span><span class="sxs-lookup"><span data-stu-id="ac3b2-121">**Value**</span></span>  
  
-   <span data-ttu-id="ac3b2-122">**命名空间**</span><span class="sxs-lookup"><span data-stu-id="ac3b2-122">**Namespace**</span></span>  
  
-   <span data-ttu-id="ac3b2-123">**变量值更改时引发事件**</span><span class="sxs-lookup"><span data-stu-id="ac3b2-123">**Raise event when variable value changes**</span></span>  
  
-   <span data-ttu-id="ac3b2-124">**说明**</span><span class="sxs-lookup"><span data-stu-id="ac3b2-124">**Description**</span></span>  
  
-   <span data-ttu-id="ac3b2-125">**表达式**</span><span class="sxs-lookup"><span data-stu-id="ac3b2-125">**Expression**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac3b2-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ac3b2-126">See Also</span></span>  
 <span data-ttu-id="ac3b2-127">[变量窗口](../../2014/integration-services/variables-window.md) </span><span class="sxs-lookup"><span data-stu-id="ac3b2-127">[Variables Window](../../2014/integration-services/variables-window.md) </span></span>  
 <span data-ttu-id="ac3b2-128">[Integration Services (SSIS) 变量](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="ac3b2-128">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="ac3b2-129">[使用包中的变量](../../2014/integration-services/use-variables-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="ac3b2-129">[Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md) </span></span>  
 [<span data-ttu-id="ac3b2-130">Integration Services (SSIS) 事件处理程序</span><span class="sxs-lookup"><span data-stu-id="ac3b2-130">Integration Services &#40;SSIS&#41; Event Handlers</span></span>](integration-services-ssis-event-handlers.md)  
  
  
