---
title: 设置断点 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.setbreakpoints.f1
helpviewer_keywords:
- Set Breakpoints dialog box
ms.assetid: 876e61b7-875c-43f4-bbce-d7eeb90f6730
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8115fcd845ee5ff415d13aa4fe36230234e33ca0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692317"
---
# <a name="set-breakpoints"></a><span data-ttu-id="577a9-102">“设置断点”</span><span class="sxs-lookup"><span data-stu-id="577a9-102">Set Breakpoints</span></span>
  <span data-ttu-id="577a9-103">可以使用 **“设置断点”** 对话框，指定要启用断点和控制断点行为的事件。</span><span class="sxs-lookup"><span data-stu-id="577a9-103">Use the **Set Breakpoints** dialog box to specify the events on which to enable breakpoints and to control the behavior of the breakpoint.</span></span>  
  
## <a name="options"></a><span data-ttu-id="577a9-104">选项</span><span class="sxs-lookup"><span data-stu-id="577a9-104">Options</span></span>  
 <span data-ttu-id="577a9-105">**已启用**</span><span class="sxs-lookup"><span data-stu-id="577a9-105">**Enabled**</span></span>  
 <span data-ttu-id="577a9-106">选择此选项可以对事件启用断点。</span><span class="sxs-lookup"><span data-stu-id="577a9-106">Select to enable a breakpoint on an event.</span></span>  
  
 <span data-ttu-id="577a9-107">**Break Condition**</span><span class="sxs-lookup"><span data-stu-id="577a9-107">**Break Condition**</span></span>  
 <span data-ttu-id="577a9-108">查看可设置断点的事件列表。</span><span class="sxs-lookup"><span data-stu-id="577a9-108">View a list of available events on which to set breakpoints.</span></span>  
  
 <span data-ttu-id="577a9-109">**Hit Count Type**</span><span class="sxs-lookup"><span data-stu-id="577a9-109">**Hit Count Type**</span></span>  
 <span data-ttu-id="577a9-110">指定断点生效的时间。</span><span class="sxs-lookup"><span data-stu-id="577a9-110">Specify when the breakpoint takes effect.</span></span>  
  
|<span data-ttu-id="577a9-111">值</span><span class="sxs-lookup"><span data-stu-id="577a9-111">Value</span></span>|<span data-ttu-id="577a9-112">说明</span><span class="sxs-lookup"><span data-stu-id="577a9-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="577a9-113">**始终**</span><span class="sxs-lookup"><span data-stu-id="577a9-113">**Always**</span></span>|<span data-ttu-id="577a9-114">断点命中时始终挂起执行。</span><span class="sxs-lookup"><span data-stu-id="577a9-114">Execution is always suspended when the breakpoint is hit.</span></span>|  
|<span data-ttu-id="577a9-115">**命中计数等于**</span><span class="sxs-lookup"><span data-stu-id="577a9-115">**Hit count equals**</span></span>|<span data-ttu-id="577a9-116">断点发生的次数等于命中计数时挂起执行。</span><span class="sxs-lookup"><span data-stu-id="577a9-116">Execution is suspended when the number of times the breakpoint has occurred is equal to the hit count.</span></span>|  
|<span data-ttu-id="577a9-117">**命中计数大于或等于**</span><span class="sxs-lookup"><span data-stu-id="577a9-117">**Hit greater or equal**</span></span>|<span data-ttu-id="577a9-118">断点发生的次数等于或大于命中计数时挂起执行。</span><span class="sxs-lookup"><span data-stu-id="577a9-118">Execution is suspended when the number of times the breakpoint has occurred is equal to or greater than the hit count.</span></span>|  
|<span data-ttu-id="577a9-119">**命中计数倍增基数**</span><span class="sxs-lookup"><span data-stu-id="577a9-119">**Hit count multiple**</span></span>|<span data-ttu-id="577a9-120">断点发生的次数为命中计数的倍数时挂起执行。</span><span class="sxs-lookup"><span data-stu-id="577a9-120">Execution is suspended when a multiple of the hit count occurs.</span></span> <span data-ttu-id="577a9-121">例如，如果将此选项设置为 5，则每命中五次就挂起执行。</span><span class="sxs-lookup"><span data-stu-id="577a9-121">For example, if you set this option to 5, execution is suspended every fifth time.</span></span>|  
  
 <span data-ttu-id="577a9-122">**命中计数**</span><span class="sxs-lookup"><span data-stu-id="577a9-122">**Hit Count**</span></span>  
 <span data-ttu-id="577a9-123">指定触发中断的命中次数。</span><span class="sxs-lookup"><span data-stu-id="577a9-123">Specify the number of hits at which to trigger a break.</span></span> <span data-ttu-id="577a9-124">如果断点始终有效，则此选项将不可用。</span><span class="sxs-lookup"><span data-stu-id="577a9-124">This option is not available if the breakpoint is always in effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="577a9-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="577a9-125">See Also</span></span>  
 [<span data-ttu-id="577a9-126">调试控制流</span><span class="sxs-lookup"><span data-stu-id="577a9-126">Debugging Control Flow</span></span>](../../../integration-services/troubleshooting/debugging-control-flow.md)  
  
  
