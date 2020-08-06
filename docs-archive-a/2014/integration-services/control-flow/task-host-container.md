---
title: 任务宿主容器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.taskhostcontainer.f1
helpviewer_keywords:
- containers [Integration Services], Task Host
- Task Host container
ms.assetid: 7394a2c2-1b07-427d-b94a-9792e7783d35
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4429d564cea0f08d5c2408199a8f1837b38389b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589821"
---
# <a name="task-host-container"></a><span data-ttu-id="99fef-102">任务宿主容器</span><span class="sxs-lookup"><span data-stu-id="99fef-102">Task Host Container</span></span>
  <span data-ttu-id="99fef-103">任务宿主容器封装单个任务。</span><span class="sxs-lookup"><span data-stu-id="99fef-103">The task host container encapsulates a single task.</span></span> <span data-ttu-id="99fef-104">在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中，无需对任务宿主进行单独配置；设置其要封装任务的属性时即可对其进行配置。</span><span class="sxs-lookup"><span data-stu-id="99fef-104">In [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the task host is not configured separately; instead, it is configured when you set the properties of the task it encapsulates.</span></span> <span data-ttu-id="99fef-105">有关任务宿主容器所封装任务的详细信息，请参阅 [Integration Services Tasks](integration-services-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="99fef-105">For more information about the tasks that the task host containers encapsulate, see [Integration Services Tasks](integration-services-tasks.md).</span></span>  
  
 <span data-ttu-id="99fef-106">此容器将变量和事件处理程序的使用扩展到任务级。</span><span class="sxs-lookup"><span data-stu-id="99fef-106">This container extends the use of variables and event handlers to the task level.</span></span> <span data-ttu-id="99fef-107">有关详细信息，请参阅 [Integration Services (SSIS) 事件处理程序](../integration-services-ssis-event-handlers.md)和 [Integration Services (SSIS) 变量](../integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="99fef-107">For more information, see [Integration Services &#40;SSIS&#41; Event Handlers](../integration-services-ssis-event-handlers.md) and [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
## <a name="configuration-of-the-task-host"></a><span data-ttu-id="99fef-108">任务宿主的配置</span><span class="sxs-lookup"><span data-stu-id="99fef-108">Configuration of the Task Host</span></span>  
 <span data-ttu-id="99fef-109">可以在 **的** “属性” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 窗口中设置属性，或以编程方式设置属性。</span><span class="sxs-lookup"><span data-stu-id="99fef-109">You can set properties in the **Properties** window of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or programmatically.</span></span>  
  
 <span data-ttu-id="99fef-110">有关在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中设置这些属性的信息，请参阅 [设置任务或容器的属性](../set-the-properties-of-a-task-or-container.md)。</span><span class="sxs-lookup"><span data-stu-id="99fef-110">For information about setting these properties in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
 <span data-ttu-id="99fef-111">有关如何以编程方式设置这些属性的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>。</span><span class="sxs-lookup"><span data-stu-id="99fef-111">For information about programmatically setting these properties, see <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="99fef-112">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="99fef-112">Related Tasks</span></span>  
  
-   [<span data-ttu-id="99fef-113">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="99fef-113">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="99fef-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="99fef-114">See Also</span></span>  
 [<span data-ttu-id="99fef-115">Integration Services 容器</span><span class="sxs-lookup"><span data-stu-id="99fef-115">Integration Services Containers</span></span>](integration-services-containers.md)  
  
  
