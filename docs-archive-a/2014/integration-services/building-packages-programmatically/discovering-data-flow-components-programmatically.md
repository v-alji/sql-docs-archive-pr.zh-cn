---
title: 以编程方式发现数据流组件 | Microsoft Docs
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
- PipelineComponentInfos collection
- data flow task [Integration Services], components
- discovering data flow components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: ff92a96a-8af6-4532-82cc-c0bbff92401b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a18102f38f1ad06e918efe2ca529185d40deef9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689560"
---
# <a name="discovering-data-flow-components-programmatically"></a><span data-ttu-id="e0ae1-102">以编程方式查找数据流组件</span><span class="sxs-lookup"><span data-stu-id="e0ae1-102">Discovering Data Flow Components Programmatically</span></span>
  <span data-ttu-id="e0ae1-103">向包中添加数据流任务后，下一步是确定可用的数据流组件。</span><span class="sxs-lookup"><span data-stu-id="e0ae1-103">After you have added a data flow task to a package, your next step may be to determine what data flow components are available for your use.</span></span> <span data-ttu-id="e0ae1-104">可以用编程方式查找本地计算机上安装并且可用的数据流源、转换和目标。</span><span class="sxs-lookup"><span data-stu-id="e0ae1-104">You can programmatically discover the data flow sources, transformations, and destinations that are installed and available on the local computer.</span></span> <span data-ttu-id="e0ae1-105">有关向包添加数据流任务的信息，请参阅[以编程方式添加数据流任务](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="e0ae1-105">For information about adding a data flow task to the package, see [Adding the Data Flow Task Programmatically](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md).</span></span>  
  
## <a name="discovering-components"></a><span data-ttu-id="e0ae1-106">查找组件</span><span class="sxs-lookup"><span data-stu-id="e0ae1-106">Discovering Components</span></span>  
 <span data-ttu-id="e0ae1-107"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 类提供 <xref:Microsoft.SqlServer.Dts.Runtime.Application.PipelineComponentInfos%2A> 集合，该集合包含在本地计算机上正确安装的每个组件的 <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> 对象。</span><span class="sxs-lookup"><span data-stu-id="e0ae1-107">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class provides the <xref:Microsoft.SqlServer.Dts.Runtime.Application.PipelineComponentInfos%2A> collection, which contains a <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> object for each component correctly installed on the local computer.</span></span> <span data-ttu-id="e0ae1-108">每个 <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> 都包含有关组件的信息，如组件的名称、说明和创建名称。</span><span class="sxs-lookup"><span data-stu-id="e0ae1-108">Each <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> contains information about a component such as its name, description, and creation name.</span></span> <span data-ttu-id="e0ae1-109">可在向包中添加组件时使用 <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> 属性中返回的值来设置 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> 的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 属性。</span><span class="sxs-lookup"><span data-stu-id="e0ae1-109">You can use the value returned in the <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> property to set the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> when you add a component to a package.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="e0ae1-110">下一步</span><span class="sxs-lookup"><span data-stu-id="e0ae1-110">Next Step</span></span>  
 <span data-ttu-id="e0ae1-111">发现可用组件后，下一步是添加和配置这些组件，这将在下一主题[以编程方式添加数据流任务](../building-packages-programmatically/adding-data-flow-components-programmatically.md)中讨论。</span><span class="sxs-lookup"><span data-stu-id="e0ae1-111">After discovering available components, the next step is to add and configure the components, which is discussed in the next topic, [Adding Data Flow Components Programmatically](../building-packages-programmatically/adding-data-flow-components-programmatically.md).</span></span>  
  
## <a name="sample"></a><span data-ttu-id="e0ae1-112">示例</span><span class="sxs-lookup"><span data-stu-id="e0ae1-112">Sample</span></span>  
 <span data-ttu-id="e0ae1-113">下面的代码示例演示如何枚举 <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfos> 对象的 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 集合，从而以编程方式查找本地计算机上的可用数据流组件。</span><span class="sxs-lookup"><span data-stu-id="e0ae1-113">The following code sample shows how to enumerate the <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfos> collection of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> object to programmatically discover the data flow components available on the local computer.</span></span> <span data-ttu-id="e0ae1-114">此示例需要引用 Microsoft.SqlServer.ManagedDTS 程序集。</span><span class="sxs-lookup"><span data-stu-id="e0ae1-114">This sample requires a reference to the Microsoft.SqlServer.ManagedDTS assembly.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Application application = new Application();  
      PipelineComponentInfos componentInfos = application.PipelineComponentInfos;  
  
      foreach (PipelineComponentInfo componentInfo in componentInfos)  
      {  
        Console.WriteLine("Name: " + componentInfo.Name + "\n" +  
          " CreationName: " + componentInfo.CreationName + "\n");  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim application As Application = New Application()  
  
    Dim componentInfos As PipelineComponentInfos = application.PipelineComponentInfos  
  
    For Each componentInfo As PipelineComponentInfo In componentInfos  
      Console.WriteLine("Name: " & componentInfo.Name & vbCrLf & _  
        " CreationName: " & componentInfo.CreationName & vbCrLf)  
    Next  
  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
<span data-ttu-id="e0ae1-115">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="e0ae1-115">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="e0ae1-116">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="e0ae1-116">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="e0ae1-117">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="e0ae1-117">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="e0ae1-118">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="e0ae1-118">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0ae1-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e0ae1-119">See Also</span></span>  
 [<span data-ttu-id="e0ae1-120">以编程方式添加数据流组件</span><span class="sxs-lookup"><span data-stu-id="e0ae1-120">Adding Data Flow Components Programmatically</span></span>](../building-packages-programmatically/adding-data-flow-components-programmatically.md)  
  
  
