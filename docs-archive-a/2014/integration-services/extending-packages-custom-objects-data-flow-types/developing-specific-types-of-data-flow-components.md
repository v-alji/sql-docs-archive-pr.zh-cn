---
title: 开发特定类型的数据流组件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow task [Integration Services], components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: 348e219a-b8ff-425e-b9c6-811880101c54
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3e168c866e03bfa5fd1f32127e4bfd6e58a2e8d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691813"
---
# <a name="developing-specific-types-of-data-flow-components"></a><span data-ttu-id="b6694-102">开发特定类型的数据流组件</span><span class="sxs-lookup"><span data-stu-id="b6694-102">Developing Specific Types of Data Flow Components</span></span>
  <span data-ttu-id="b6694-103">本节包括开发源组件、具有同步输出的转换组件、具有异步输出的转换组件以及目标组件的具体内容。</span><span class="sxs-lookup"><span data-stu-id="b6694-103">This section covers the specifics of developing source components, transformation components with synchronous outputs, transformation components with asynchronous outputs, and destination components.</span></span>  
  
 <span data-ttu-id="b6694-104">有关组件开发的常规信息，请参阅[开发自定义数据流组件](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="b6694-104">For information about component development in general, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b6694-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="b6694-105">In This Section</span></span>  
 [<span data-ttu-id="b6694-106">开发自定义源组件</span><span class="sxs-lookup"><span data-stu-id="b6694-106">Developing a Custom Source Component</span></span>](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)  
 <span data-ttu-id="b6694-107">包含有关开发组件的信息，该组件访问外部数据源中的数据，并向该数据提供数据流中的下游组件。</span><span class="sxs-lookup"><span data-stu-id="b6694-107">Contains information on developing a component that accesses data from an external data source and supplies it to downstream components in the data flow.</span></span>  
  
 [<span data-ttu-id="b6694-108">开发具有同步输出的自定义转换组件</span><span class="sxs-lookup"><span data-stu-id="b6694-108">Developing a Custom Transformation Component with Synchronous Outputs</span></span>](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)  
 <span data-ttu-id="b6694-109">包含有关开发其输出与输入同步的转换组件的信息。</span><span class="sxs-lookup"><span data-stu-id="b6694-109">Contains information on developing a transformation component whose outputs are synchronous to its inputs.</span></span> <span data-ttu-id="b6694-110">这些组件不向数据流中添加数据，但处理通过该数据流的数据。</span><span class="sxs-lookup"><span data-stu-id="b6694-110">These components do not add data to the data flow, but process data as it passes through.</span></span>  
  
 [<span data-ttu-id="b6694-111">开发具有异步输出的自定义转换组件</span><span class="sxs-lookup"><span data-stu-id="b6694-111">Developing a Custom Transformation Component with Asynchronous Outputs</span></span>](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)  
 <span data-ttu-id="b6694-112">包含有关开发其输出与输入不同步的转换组件的信息。</span><span class="sxs-lookup"><span data-stu-id="b6694-112">Contains information on developing a transformation component whose outputs are not synchronous to its inputs.</span></span> <span data-ttu-id="b6694-113">这些组件接收来自上游组件的数据，但是也向数据流中添加数据。</span><span class="sxs-lookup"><span data-stu-id="b6694-113">These components receive data from upstream components, but also add data to the dataflow.</span></span>  
  
 [<span data-ttu-id="b6694-114">开发自定义目标组件</span><span class="sxs-lookup"><span data-stu-id="b6694-114">Developing a Custom Destination Component</span></span>](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)  
 <span data-ttu-id="b6694-115">包含有关开发组件的信息，该组件接收来自数据流上游组件的行，并将这些行写入外部数据源。</span><span class="sxs-lookup"><span data-stu-id="b6694-115">Contains information on developing a component that receives rows from upstream components in the data flow and writes them to an external data source.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b6694-116">参考</span><span class="sxs-lookup"><span data-stu-id="b6694-116">Reference</span></span>  
 <xref:Microsoft.SqlServer.Dts.Pipeline>  
 <span data-ttu-id="b6694-117">包含用于创建自定义数据流组件的类和接口。</span><span class="sxs-lookup"><span data-stu-id="b6694-117">Contains the classes and interfaces used to create custom data flow components.</span></span>  
  
 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>  
 <span data-ttu-id="b6694-118">包含数据流任务的非托管类和接口。</span><span class="sxs-lookup"><span data-stu-id="b6694-118">Contains the unmanaged classes and interfaces of the data flow task.</span></span> <span data-ttu-id="b6694-119">开发人员在以编程方式生成数据流或创建自定义数据流组件时，使用这些类和接口，以及托管 <xref:Microsoft.SqlServer.Dts.Pipeline> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="b6694-119">The developer uses these, and the managed <xref:Microsoft.SqlServer.Dts.Pipeline> namespace, when building a data flow programmatically or creating custom data flow components.</span></span>  
  
<span data-ttu-id="b6694-120">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="b6694-120">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="b6694-121">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="b6694-121">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="b6694-122">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="b6694-122">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="b6694-123">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="b6694-123">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6694-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6694-124">See Also</span></span>  
 <span data-ttu-id="b6694-125">[比较脚本解决方案和自定义对象](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span><span class="sxs-lookup"><span data-stu-id="b6694-125">[Comparing Scripting Solutions and Custom Objects](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span></span>  
 [<span data-ttu-id="b6694-126">开发特定类型的脚本组件</span><span class="sxs-lookup"><span data-stu-id="b6694-126">Developing Specific Types of Script Components</span></span>](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)  
  
  
