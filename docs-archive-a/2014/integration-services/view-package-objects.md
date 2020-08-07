---
title: 查看包对象 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, properties
- properties [Integration Services]
- Package Explorer window [Integration Services]
- packages [Integration Services], properties
- explorer view [Integration Services]
- SSIS packages, properties
- viewing package objects
- SQL Server Integration Services packages, properties
ms.assetid: a85c0245-0a68-4eb0-83b1-9b11df80bd10
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ffe46be35db26186f715b18ba6114732d130e02e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588597"
---
# <a name="view-package-objects"></a><span data-ttu-id="4b582-102">查看包对象</span><span class="sxs-lookup"><span data-stu-id="4b582-102">View Package Objects</span></span>
  <span data-ttu-id="4b582-103">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中， **“包资源管理器”** 选项卡提供包的资源管理器视图。</span><span class="sxs-lookup"><span data-stu-id="4b582-103">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, the **Package Explorer** tab provides an explorer view of the package.</span></span> <span data-ttu-id="4b582-104">该视图反映了 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 体系结构的容器层次结构。</span><span class="sxs-lookup"><span data-stu-id="4b582-104">The view reflects the container hierarchy of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] architecture.</span></span> <span data-ttu-id="4b582-105">包容器位于层次结构的顶层，您可以展开包来查看连接、可执行文件、事件处理程序、日志提供程序、优先约束和包中的变量。</span><span class="sxs-lookup"><span data-stu-id="4b582-105">The package container is at the top of the hierarchy, and you expand the package to view the connections, executables, event handlers, log providers, precedence constraints, and variables in the package.</span></span>

 <span data-ttu-id="4b582-106">可执行文件（包中的容器和任务）可以包含事件处理程序、优先约束和变量。</span><span class="sxs-lookup"><span data-stu-id="4b582-106">The executables, which are the containers and tasks in the package, can include event handlers, precedence constraints, and variables.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="4b582-107">支持嵌套的容器层次结构，而 For 循环容器、Foreach 循环容器以及序列容器可包含其他可执行文件。</span><span class="sxs-lookup"><span data-stu-id="4b582-107">supports a nested hierarchy of containers, and the For Loop, Foreach Loop, and Sequence containers can include other executables.</span></span>

 <span data-ttu-id="4b582-108">如果包包含数据流， **包资源管理器** 将列出数据流任务，并包含列有数据流组件的 **“组件”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="4b582-108">If a package includes a data flow, the **Package Explorer** lists the Data Flow task and includes a **Components** folder that lists the data flow components.</span></span>

 <span data-ttu-id="4b582-109">可以从 **“包资源管理器”** 选项卡中删除包中的对象，并访问 **“属性”** 窗口来查看对象属性。</span><span class="sxs-lookup"><span data-stu-id="4b582-109">From the **Package Explorer** tab, you can delete objects in a package and access the **Properties** window to view object properties.</span></span>

 <span data-ttu-id="4b582-110">下面的关系图显示一个简单包的树视图。</span><span class="sxs-lookup"><span data-stu-id="4b582-110">The following diagram shows a tree view of a simple package.</span></span>

 <span data-ttu-id="4b582-111">![“包资源管理器”选项卡的屏幕快照](media/packageexplorer.gif "“包资源管理器”选项卡的屏幕快照")</span><span class="sxs-lookup"><span data-stu-id="4b582-111">![Screenshot of the Package Explorer tab](media/packageexplorer.gif "Screenshot of the Package Explorer tab")</span></span>

### <a name="to-view-package-content"></a><span data-ttu-id="4b582-112">查看包内容</span><span class="sxs-lookup"><span data-stu-id="4b582-112">To view package content</span></span>

-   [<span data-ttu-id="4b582-113">在包资源管理器中查看包对象</span><span class="sxs-lookup"><span data-stu-id="4b582-113">View Package Objects in Package Explorer</span></span>](../../2014/integration-services/view-package-objects-in-package-explorer.md)

## <a name="see-also"></a><span data-ttu-id="4b582-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b582-114">See Also</span></span>
 <span data-ttu-id="4b582-115">[Integration Services 任务](control-flow/integration-services-tasks.md) [Integration Services 容器](control-flow/integration-services-containers.md)[优先约束](control-flow/precedence-constraints.md) [INTEGRATION SERVICES &#40;Ssis&#41; 变量](integration-services-ssis-variables.md)Integration Services &#40;[Ssis&#41; 事件处理程序](integration-services-ssis-event-handlers.md)Integration Services [&#40;ssis&#41; 日志记录](performance/integration-services-ssis-logging.md)</span><span class="sxs-lookup"><span data-stu-id="4b582-115">[Integration Services Tasks](control-flow/integration-services-tasks.md) [Integration Services Containers](control-flow/integration-services-containers.md) [Precedence Constraints](control-flow/precedence-constraints.md) [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) [Integration Services &#40;SSIS&#41; Event Handlers](integration-services-ssis-event-handlers.md) [Integration Services &#40;SSIS&#41; Logging](performance/integration-services-ssis-logging.md)</span></span>


