---
title: 开发特定类型的脚本组件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: dfbbe959-6b4e-4b47-b9dd-bcc31929482d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 114c9ddca90ea02a8e1847444b28b9d5876650a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587474"
---
# <a name="developing-specific-types-of-script-components"></a><span data-ttu-id="9a151-102">开发特定类型的脚本组件</span><span class="sxs-lookup"><span data-stu-id="9a151-102">Developing Specific Types of Script Components</span></span>
  <span data-ttu-id="9a151-103">脚本组件是一个可配置的工具，您可以在包的数据流中使用，它可以满足几乎所有 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 附带的源、转换和目标所无法满足的要求。</span><span class="sxs-lookup"><span data-stu-id="9a151-103">The Script component is a configurable tool that you can use in the data flow of a package to fill almost any requirement that is not met by the sources, transformations, and destinations that are included with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="9a151-104">本节包含一些脚本组件代码示例，这些示例演示了用于配置脚本组件的四个选项：</span><span class="sxs-lookup"><span data-stu-id="9a151-104">This section contains Script component code samples that demonstrate the four options for configuring the Script component:</span></span>  
  
-   <span data-ttu-id="9a151-105">作为源。</span><span class="sxs-lookup"><span data-stu-id="9a151-105">As a source.</span></span>  
  
-   <span data-ttu-id="9a151-106">作为具有同步输出的转换。</span><span class="sxs-lookup"><span data-stu-id="9a151-106">As a transformation with synchronous outputs.</span></span>  
  
-   <span data-ttu-id="9a151-107">作为具有异步输出的转换。</span><span class="sxs-lookup"><span data-stu-id="9a151-107">As a transformation with asynchronous outputs.</span></span>  
  
-   <span data-ttu-id="9a151-108">作为目标。</span><span class="sxs-lookup"><span data-stu-id="9a151-108">As a destination.</span></span>  
  
 <span data-ttu-id="9a151-109">有关脚本组件的其他示例，请参阅[其他脚本组件示例](../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="9a151-109">For additional examples of the Script component, see [Additional Script Component Examples](../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9a151-110">本节内容</span><span class="sxs-lookup"><span data-stu-id="9a151-110">In This Section</span></span>  
 [<span data-ttu-id="9a151-111">使用脚本组件创建源</span><span class="sxs-lookup"><span data-stu-id="9a151-111">Creating a Source with the Script Component</span></span>](creating-a-source-with-the-script-component.md)  
 <span data-ttu-id="9a151-112">说明并演示如何使用脚本组件创建数据流源。</span><span class="sxs-lookup"><span data-stu-id="9a151-112">Explains and demonstrates how to create a data flow source by using the Script component.</span></span>  
  
 [<span data-ttu-id="9a151-113">使用脚本组件创建同步转换</span><span class="sxs-lookup"><span data-stu-id="9a151-113">Creating a Synchronous Transformation with the Script Component</span></span>](creating-a-synchronous-transformation-with-the-script-component.md)  
 <span data-ttu-id="9a151-114">说明并演示如何使用脚本组件创建具有同步输出的数据流转换。</span><span class="sxs-lookup"><span data-stu-id="9a151-114">Explains and demonstrates how to create a data flow transformation with synchronous outputs by using the Script component.</span></span> <span data-ttu-id="9a151-115">这种类型的转换可在数据通过组件时原地修改数据行。</span><span class="sxs-lookup"><span data-stu-id="9a151-115">This kind of transformation modifies rows of data in place as they pass through the component.</span></span>  
  
 [<span data-ttu-id="9a151-116">使用脚本组件创建异步转换</span><span class="sxs-lookup"><span data-stu-id="9a151-116">Creating an Asynchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
 <span data-ttu-id="9a151-117">说明并演示如何使用脚本组件创建具有异步输出的数据流转换。</span><span class="sxs-lookup"><span data-stu-id="9a151-117">Explains and demonstrates how to create a data flow transformation with asynchronous outputs by using the Script component.</span></span> <span data-ttu-id="9a151-118">这种类型的转换必须先读取所有数据行，然后才能向通过组件的数据添加更多信息，如计算聚合。</span><span class="sxs-lookup"><span data-stu-id="9a151-118">This kind of transformation has to read all rows of data before it can add more information, such as calculated aggregates, to the data that passes through the component.</span></span>  
  
 [<span data-ttu-id="9a151-119">使用脚本组件创建目标</span><span class="sxs-lookup"><span data-stu-id="9a151-119">Creating a Destination with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
 <span data-ttu-id="9a151-120">说明并演示如何使用脚本组件创建数据流目标。</span><span class="sxs-lookup"><span data-stu-id="9a151-120">Explains and demonstrates how to create a data flow destination by using the Script component.</span></span>  
  
<span data-ttu-id="9a151-121">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="9a151-121">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="9a151-122">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="9a151-122">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="9a151-123">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="9a151-123">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="9a151-124">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="9a151-124">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a151-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9a151-125">See Also</span></span>  
 <span data-ttu-id="9a151-126">[比较脚本解决方案和自定义对象](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span><span class="sxs-lookup"><span data-stu-id="9a151-126">[Comparing Scripting Solutions and Custom Objects](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md) </span></span>  
 [<span data-ttu-id="9a151-127">开发特定类型的数据流组件</span><span class="sxs-lookup"><span data-stu-id="9a151-127">Developing Specific Types of Data Flow Components</span></span>](../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)  
  
  
