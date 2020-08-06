---
title: 复制包对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- control flow [Integration Services], copying objects
- copying package objects [Integration Services]
- data flow [Integration Services], copying objects
- connection managers [Integration Services], copying
ms.assetid: 99b85e5c-d6bd-4e7c-afe4-51f6ce151c2f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3219f0023c9a28ed270adeb6fd2b795e3459c3e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579693"
---
# <a name="copy-package-objects"></a><span data-ttu-id="095ab-102">复制包对象</span><span class="sxs-lookup"><span data-stu-id="095ab-102">Copy Package Objects</span></span>
  <span data-ttu-id="095ab-103">此主题介绍如何在包内或包之间复制控制流项、数据流项和连接管理器。</span><span class="sxs-lookup"><span data-stu-id="095ab-103">This topic describes how to copy control flow items, data flow items, and connection managers within a package or between packages.</span></span>  
  
### <a name="to-copy-control-and-data-flow-items"></a><span data-ttu-id="095ab-104">复制控制和数据流项</span><span class="sxs-lookup"><span data-stu-id="095ab-104">To copy control and data flow items</span></span>  
  
1.  <span data-ttu-id="095ab-105">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含要处理的包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="095ab-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the packages that you want work with.</span></span>  
  
2.  <span data-ttu-id="095ab-106">在解决方案资源管理器中，双击希望在其间复制的包。</span><span class="sxs-lookup"><span data-stu-id="095ab-106">In Solution Explorer, double-click the packages that you want to copy between.</span></span>  
  
3.  <span data-ttu-id="095ab-107">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中，单击包含要复制的项的包对应的选项卡，并单击 **“控制流”** 、 **“数据流”** 或 **“事件处理程序”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="095ab-107">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the tab for the package that contains the items to copy and click the **Control Flow**, **Data Flow**, or **Event Handlers** tab.</span></span>  
  
4.  <span data-ttu-id="095ab-108">选择要复制的控制流或数据流项。</span><span class="sxs-lookup"><span data-stu-id="095ab-108">Select the control flow or data flow items to copy.</span></span> <span data-ttu-id="095ab-109">可以通过按 Shift 键并单击项以一次一个的方式来选择多项，也可以通过拖动指针扫过希望选择的项来按组选择多项。</span><span class="sxs-lookup"><span data-stu-id="095ab-109">You can either select items one at a time by pressing the Shift key and clicking the item or select items as a group by dragging the pointer across the items you want to select.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="095ab-110">如果选择的两个项相互连接，则不会自动选择连接这些项的优先级约束和路径。</span><span class="sxs-lookup"><span data-stu-id="095ab-110">The precedence constraints and paths that connect items are not selected automatically when you select the two items that they connect.</span></span> <span data-ttu-id="095ab-111">若要复制经过排序的工作流（一段控制流或数据流），请确保同时复制优先级约束和路径。</span><span class="sxs-lookup"><span data-stu-id="095ab-111">To copy an ordered workflow-a segment of control flow or data flow-make sure to also copy the precedence constrains and the paths.</span></span>  
  
5.  <span data-ttu-id="095ab-112">右键单击所选项并单击“复制”  。</span><span class="sxs-lookup"><span data-stu-id="095ab-112">Right-click a selected item and click **Copy**.</span></span>  
  
6.  <span data-ttu-id="095ab-113">如果将项复制到其他包，请单击要复制到其中的包，然后单击适合该项类型的合适的选项卡。</span><span class="sxs-lookup"><span data-stu-id="095ab-113">If copying items to a different package, click the package that you want to copy to, and then click the appropriate tab for the item type.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="095ab-114">无法将数据流复制到包中，除非包至少包含一个“数据流”任务。</span><span class="sxs-lookup"><span data-stu-id="095ab-114">You cannot copy a data flow to a package unless the package contains at least one Data Flow task.</span></span>  
  
7.  <span data-ttu-id="095ab-115">右键单击并单击“粘贴”  。</span><span class="sxs-lookup"><span data-stu-id="095ab-115">Right-click and click **Paste**.</span></span>  
  
### <a name="to-copy-connection-managers"></a><span data-ttu-id="095ab-116">复制连接管理器</span><span class="sxs-lookup"><span data-stu-id="095ab-116">To copy connection managers</span></span>  
  
1.  <span data-ttu-id="095ab-117">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含要处理的包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="095ab-117">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package that you want to work with.</span></span>  
  
2.  <span data-ttu-id="095ab-118">在解决方案资源管理器中，双击包。</span><span class="sxs-lookup"><span data-stu-id="095ab-118">In Solution Explorer, double-click the package.</span></span>  
  
3.  <span data-ttu-id="095ab-119">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中，单击 **“控制流”** 、 **“数据流”** 或 **“事件处理程序”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="095ab-119">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Control Flow**, **Data Flow**, or **Event Handler** tab.</span></span>  
  
4.  <span data-ttu-id="095ab-120">在“连接管理器”  区域中，右键单击连接管理器，然后单击“复制”  。</span><span class="sxs-lookup"><span data-stu-id="095ab-120">In the **Connection Managers** area, right-click the connection manager, and then click **Copy**.</span></span> <span data-ttu-id="095ab-121">每次只能复制一个连接管理器。</span><span class="sxs-lookup"><span data-stu-id="095ab-121">You can copy only one connection manager at a time.</span></span>  
  
5.  <span data-ttu-id="095ab-122">如果要将项复制到其他包，请单击希望复制到其中的包，然后单击 **“控制流”** 、 **“数据流”** 或 **“事件处理程序”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="095ab-122">If you are copying items to a different package, click the package that you want to copy to and then click the **Control Flow**, **Data Flow**, or **Event Handler** tab.</span></span>  
  
6.  <span data-ttu-id="095ab-123">右键单击“连接管理器”  区域，并单击“粘贴”  。</span><span class="sxs-lookup"><span data-stu-id="095ab-123">Right-click in the **Connection Managers** area and click **Paste**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="095ab-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="095ab-124">See Also</span></span>  
 <span data-ttu-id="095ab-125">[控制流](control-flow/control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="095ab-125">[Control Flow](control-flow/control-flow.md) </span></span>  
 <span data-ttu-id="095ab-126">[数据流](data-flow/data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="095ab-126">[Data Flow](data-flow/data-flow.md) </span></span>  
 <span data-ttu-id="095ab-127">[Integration Services (SSIS) 连接](connection-manager/integration-services-ssis-connections.md) </span><span class="sxs-lookup"><span data-stu-id="095ab-127">[Integration Services &#40;SSIS&#41; Connections](connection-manager/integration-services-ssis-connections.md) </span></span>  
 [<span data-ttu-id="095ab-128">复制项目项</span><span class="sxs-lookup"><span data-stu-id="095ab-128">Copy Project Items</span></span>](../../2014/integration-services/copy-project-items.md)  
  
  
