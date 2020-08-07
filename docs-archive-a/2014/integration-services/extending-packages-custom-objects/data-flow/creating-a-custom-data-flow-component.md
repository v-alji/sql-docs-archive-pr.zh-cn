---
title: 创建自定义数据流组件 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- design-time component interface [Integration Services]
- custom data flow components [Integration Services], about data flow components
- custom data flow components [Integration Services]
- data flow components [Integration Services]
- data flow components [Integration Services], developing
ms.assetid: 9d96bcf5-eba8-44bd-b113-ed51ad0d0521
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 110d07ff88707ad1a01f299b6f532df99ce58404
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587928"
---
# <a name="creating-a-custom-data-flow-component"></a><span data-ttu-id="8cbc3-102">创建自定义数据流组件</span><span class="sxs-lookup"><span data-stu-id="8cbc3-102">Creating a Custom Data Flow Component</span></span>
  <span data-ttu-id="8cbc3-103">在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中，数据流任务会公开一个对象模型，该对象模型允许开发人员使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 和托管代码创建自定义数据流组件：源、转换和目标。</span><span class="sxs-lookup"><span data-stu-id="8cbc3-103">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], the data flow task exposes an object model that lets developers create custom data flow components-sources, transformations, and destinations-by using the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] and managed code.</span></span>  
  
 <span data-ttu-id="8cbc3-104">数据流任务由包含 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 接口和 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> 对象集合的组件组成，这些对象定义组件之间的数据移动。</span><span class="sxs-lookup"><span data-stu-id="8cbc3-104">A data flow task consists of components that contain an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface and a collection of <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> objects that define the movement of data between components.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8cbc3-105">在您创建自定义提供程序时，需要使用元数据列值更新 ProviderDescriptors.xml 文件。</span><span class="sxs-lookup"><span data-stu-id="8cbc3-105">When you create a custom provider, you need to update the ProviderDescriptors.xml file with the metadata column values.</span></span>  
  
## <a name="design-time-and-run-time"></a><span data-ttu-id="8cbc3-106">设计时和运行时</span><span class="sxs-lookup"><span data-stu-id="8cbc3-106">Design Time and Run Time</span></span>  
 <span data-ttu-id="8cbc3-107">在执行前，称数据流任务处于设计时状态，因为它将接受增量更改。</span><span class="sxs-lookup"><span data-stu-id="8cbc3-107">Before execution, the data flow task is said to be in a design-time state, as it undergoes incremental changes.</span></span> <span data-ttu-id="8cbc3-108">这些更改可以包括添加或删除组件、添加或删除连接组件的路径对象以及更改组件的元数据。</span><span class="sxs-lookup"><span data-stu-id="8cbc3-108">Changes may include the addition or removal of components, the addition or removal of the path objects that connect components, and changes to the metadata of the components.</span></span> <span data-ttu-id="8cbc3-109">出现元数据更改时，组件可监视这些更改并对这些更改作出响应。</span><span class="sxs-lookup"><span data-stu-id="8cbc3-109">When metadata changes occur, the component can monitor and react to the changes.</span></span> <span data-ttu-id="8cbc3-110">例如，组件可以禁止某些更改或为响应某一更改而进行其他更改。</span><span class="sxs-lookup"><span data-stu-id="8cbc3-110">For example, a component can disallow certain changes or to make additional changes in response to a change.</span></span> <span data-ttu-id="8cbc3-111">在设计时，设计器通过设计时 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> 接口与组件进行交互。</span><span class="sxs-lookup"><span data-stu-id="8cbc3-111">At design time, the designer interacts with a component through the design-time <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> interface.</span></span>  
  
 <span data-ttu-id="8cbc3-112">在执行时，数据流任务将检查一系列组件、准备执行计划以及管理执行工作计划的工作线程池。</span><span class="sxs-lookup"><span data-stu-id="8cbc3-112">At execution time, the data flow task examines the sequence of components, prepares an execution plan, and manages a pool of worker threads that execute the work plan.</span></span> <span data-ttu-id="8cbc3-113">虽然每个工作线程都执行数据流任务的一些内部工作，但工作线程的主要任务是通过运行时 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> 接口调用组件的方法。</span><span class="sxs-lookup"><span data-stu-id="8cbc3-113">Although each worker thread performs some work that is internal to the data flow task, the principal task of the worker thread is to call the methods of the component through the run-time <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> interface.</span></span>  
  
## <a name="creating-a-component"></a><span data-ttu-id="8cbc3-114">创建组件</span><span class="sxs-lookup"><span data-stu-id="8cbc3-114">Creating a Component</span></span>  
 <span data-ttu-id="8cbc3-115">若要创建数据流组件，可从 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 基类派生类，再应用 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> 类，然后重写适当的基类方法。</span><span class="sxs-lookup"><span data-stu-id="8cbc3-115">To create a data flow component, you derive a class from the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class, apply the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> class, and then override the appropriate methods of the base class.</span></span> <span data-ttu-id="8cbc3-116"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 实现 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> 接口，并公开这些接口的方法，供您在组件中重写。</span><span class="sxs-lookup"><span data-stu-id="8cbc3-116">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> interfaces, and exposes their methods for you to override in your component.</span></span>  
  
 <span data-ttu-id="8cbc3-117">根据您的组件所使用的对象，您的项目将需要引用以下部分或全部程序集：</span><span class="sxs-lookup"><span data-stu-id="8cbc3-117">Depending on the objects used by your component, your project will require references to some or all of the following assemblies:</span></span>  
  
|<span data-ttu-id="8cbc3-118">Feature</span><span class="sxs-lookup"><span data-stu-id="8cbc3-118">Feature</span></span>|<span data-ttu-id="8cbc3-119">要引用的程序集</span><span class="sxs-lookup"><span data-stu-id="8cbc3-119">Assembly to reference</span></span>|<span data-ttu-id="8cbc3-120">要导入的命名空间</span><span class="sxs-lookup"><span data-stu-id="8cbc3-120">Namespace to import</span></span>|  
|-------------|---------------------------|-------------------------|  
|<span data-ttu-id="8cbc3-121">数据流</span><span class="sxs-lookup"><span data-stu-id="8cbc3-121">Data flow</span></span>|<span data-ttu-id="8cbc3-122">Microsoft.SqlServer.PipelineHost</span><span class="sxs-lookup"><span data-stu-id="8cbc3-122">Microsoft.SqlServer.PipelineHost</span></span>|<xref:Microsoft.SqlServer.Dts.Pipeline>|  
|<span data-ttu-id="8cbc3-123">数据流包装</span><span class="sxs-lookup"><span data-stu-id="8cbc3-123">Data flow wrapper</span></span>|<span data-ttu-id="8cbc3-124">Microsoft.SqlServer.DTSPipelineWrap</span><span class="sxs-lookup"><span data-stu-id="8cbc3-124">Microsoft.SqlServer.DTSPipelineWrap</span></span>|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>|  
|<span data-ttu-id="8cbc3-125">运行时</span><span class="sxs-lookup"><span data-stu-id="8cbc3-125">Runtime</span></span>|<span data-ttu-id="8cbc3-126">Microsoft.SQLServer.ManagedDTS</span><span class="sxs-lookup"><span data-stu-id="8cbc3-126">Microsoft.SQLServer.ManagedDTS</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime>|  
|<span data-ttu-id="8cbc3-127">运行时包装</span><span class="sxs-lookup"><span data-stu-id="8cbc3-127">Runtime wrapper</span></span>|<span data-ttu-id="8cbc3-128">Microsoft.SqlServer.DTSRuntimeWrap</span><span class="sxs-lookup"><span data-stu-id="8cbc3-128">Microsoft.SqlServer.DTSRuntimeWrap</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper>|  
  
 <span data-ttu-id="8cbc3-129">下面的代码示例演示了一个简单的组件，该组件从基类派生，并应用 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>。</span><span class="sxs-lookup"><span data-stu-id="8cbc3-129">The following code example shows a simple component that derives from the base class, and applies the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>.</span></span> <span data-ttu-id="8cbc3-130">你需要添加对 DTSPipelineWrap 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="8cbc3-130">You need to add a reference to the DTSPipelineWrap assembly.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsPipelineComponent(DisplayName = "SampleComponent", ComponentType = ComponentType.Transform )]  
    public class BasicComponent: PipelineComponent  
    {  
        // TODO: Override the base class methods.  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
<DtsPipelineComponent(DisplayName:="SampleComponent", ComponentType:=ComponentType.Transform)> _  
Public Class BasicComponent  
  
    Inherits PipelineComponent  
  
    ' TODO: Override the base class methods.  
  
End Class  
```  
  
<span data-ttu-id="8cbc3-131">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="8cbc3-131">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="8cbc3-132">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="8cbc3-132">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="8cbc3-133">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="8cbc3-133">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="8cbc3-134">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="8cbc3-134">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cbc3-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8cbc3-135">See Also</span></span>  
 [<span data-ttu-id="8cbc3-136">为数据流组件开发用户界面</span><span class="sxs-lookup"><span data-stu-id="8cbc3-136">Developing a User Interface for a Data Flow Component</span></span>](developing-a-user-interface-for-a-data-flow-component.md)  
  
  
