---
title: 以编程方式添加数据流任务 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- adding Data Flow task
- SSIS data flow
- data flow task [Integration Services], adding
- MainPipe object
ms.assetid: 0ca03712-a82e-4aa7-949b-f869a8936ddf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4f7e699cc8e88bafb2a4508fdac8560fa73befe1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580842"
---
# <a name="adding-the-data-flow-task-programmatically"></a><span data-ttu-id="9d99b-102">以编程方式添加数据流任务</span><span class="sxs-lookup"><span data-stu-id="9d99b-102">Adding the Data Flow Task Programmatically</span></span>
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="9d99b-103">包含了一个称为数据流任务的任务，由对象模型中的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper> 命名空间表示。</span><span class="sxs-lookup"><span data-stu-id="9d99b-103">includes a task called the Data Flow task, which is represented by the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper> namespace in the object model.</span></span> <span data-ttu-id="9d99b-104">数据流任务是一个专门用于在包执行期间转换和移动数据的专用高性能任务。</span><span class="sxs-lookup"><span data-stu-id="9d99b-104">The Data Flow task is a specialized, high-performance task, dedicated to transforming and moving data during package execution.</span></span> <span data-ttu-id="9d99b-105">与其他任务相似，数据流任务由 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 对象包装，从运行时引擎的角度出发，此任务只是该包中的另一个任务。</span><span class="sxs-lookup"><span data-stu-id="9d99b-105">Like other tasks, the Data Flow task is wrapped by the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> object, and from the perspective of the run-time engine, this task is just another task in the package.</span></span> <span data-ttu-id="9d99b-106">但是，数据流包含称为数据流组件的其他对象。</span><span class="sxs-lookup"><span data-stu-id="9d99b-106">However, the data flow contains additional objects called data flow components.</span></span> <span data-ttu-id="9d99b-107">这些组件将数据从源移到目标，有时候还会经过转换。</span><span class="sxs-lookup"><span data-stu-id="9d99b-107">These components are the components that make data move from a source to a destination, sometimes through a transformation.</span></span> <span data-ttu-id="9d99b-108">这些组件定义数据的移动方向和转换数据的方式。</span><span class="sxs-lookup"><span data-stu-id="9d99b-108">The components define both the direction of movement and how data is transformed.</span></span> <span data-ttu-id="9d99b-109">配置数据流任务涉及向任务添加组件，然后连接这些组件以便建立数据流并完成所需的转换。</span><span class="sxs-lookup"><span data-stu-id="9d99b-109">Configuring the Data Flow task involves adding components to the task, and then connecting them to establish the flow of data and achieve the intended transformation.</span></span>  
  
 <span data-ttu-id="9d99b-110">数据流中有三种类型的组件：“数据流源”、“数据流转换”和“数据流目标”，它们以该顺序显示在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器的工具箱中。</span><span class="sxs-lookup"><span data-stu-id="9d99b-110">There are three types of components within a Data Flow task: **Data Flow Sources**, **Data Flow Transformations**, and **Data Flow Destinations**, shown in that order within the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer toolbox.</span></span> <span data-ttu-id="9d99b-111">这些类型又简称为源、转换和目标。</span><span class="sxs-lookup"><span data-stu-id="9d99b-111">These types are also referred to more simply as sources, transformations, or destinations.</span></span> <span data-ttu-id="9d99b-112">顾名思义，数据流从源到转换，然后到达目标。</span><span class="sxs-lookup"><span data-stu-id="9d99b-112">As implied by the names, data flows from a source to a transformation, and then to a destination.</span></span> <span data-ttu-id="9d99b-113">这是简化的数据流说明，只为说明概念，但是数据流任务却很灵活很强大，足以处理多个源以及将许多向多个目标发送输出的转换连接在一起。</span><span class="sxs-lookup"><span data-stu-id="9d99b-113">This is a simplistic description of the data flow to illustrate the concept, but the Data Flow task is flexible and powerful enough to handle multiple sources, and to connect together many transformations that send output to multiple destinations.</span></span>  
  
 <span data-ttu-id="9d99b-114">将数据流任务添加到包的方法与添加其他任务相同。</span><span class="sxs-lookup"><span data-stu-id="9d99b-114">The Data Flow task is added to a package the same way other tasks are added.</span></span> <span data-ttu-id="9d99b-115">添加该任务后，可配置该任务，方法是向数据流任务添加组件，然后配置并连接任务中的组件。</span><span class="sxs-lookup"><span data-stu-id="9d99b-115">After the task has been added, it is configured by adding components to the data flow task, and configuring and connecting components in the task.</span></span>  
  
## <a name="sample"></a><span data-ttu-id="9d99b-116">示例</span><span class="sxs-lookup"><span data-stu-id="9d99b-116">Sample</span></span>  
 <span data-ttu-id="9d99b-117">下面的代码示例演示如何向包添加数据流任务。</span><span class="sxs-lookup"><span data-stu-id="9d99b-117">The following code sample shows how to add a Data Flow task to a package.</span></span> <span data-ttu-id="9d99b-118">此示例需要引用程序集 Microsoft.SqlServer.PipelineHost、Microsoft.SqlServer.DTSPipelineWrap 和 Microsoft.SqlServer.ManagedDTS。</span><span class="sxs-lookup"><span data-stu-id="9d99b-118">This example requires a reference to the assemblies Microsoft.SqlServer.PipelineHost, Microsoft.SqlServer.DTSPipelineWrap, and Microsoft.SqlServer.ManagedDTS.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
      Executable e = p.Executables.Add("STOCK:PipelineTask");  
      TaskHost thMainPipe = e as TaskHost;  
      MainPipe dataFlowTask = thMainPipe.InnerObject as MainPipe;   
    }  
  }  
}  
```  
  
```vb  
Imports System.IO  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    Dim e As Executable = p.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As TaskHost = CType(e, TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
  End Sub  
  
End Module  
```  
  
## <a name="external-resources"></a><span data-ttu-id="9d99b-119">外部资源</span><span class="sxs-lookup"><span data-stu-id="9d99b-119">External Resources</span></span>  
 <span data-ttu-id="9d99b-120">blogs.msdn.com 上的博客文章 [EzAPI - 为 SQL Server 2012 更新](https://go.microsoft.com/fwlink/?LinkId=243223)。</span><span class="sxs-lookup"><span data-stu-id="9d99b-120">Blog entry, [EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223), on blogs.msdn.com.</span></span>  
  
<span data-ttu-id="9d99b-121">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="9d99b-121">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="9d99b-122">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="9d99b-122">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="9d99b-123">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="9d99b-123">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="9d99b-124">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="9d99b-124">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d99b-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9d99b-125">See Also</span></span>  
 [<span data-ttu-id="9d99b-126">以编程方式查找数据流组件</span><span class="sxs-lookup"><span data-stu-id="9d99b-126">Discovering Data Flow Components Programmatically</span></span>](../building-packages-programmatically/discovering-data-flow-components-programmatically.md)  
  
  
