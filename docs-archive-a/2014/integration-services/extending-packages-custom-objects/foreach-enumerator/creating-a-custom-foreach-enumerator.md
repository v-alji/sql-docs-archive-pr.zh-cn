---
title: 创建自定义 Foreach 枚举器 | Microsoft Docs
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
- custom foreach enumerators [Integration Services], creating
ms.assetid: 050e8455-2ed0-4b6d-b3ea-4e80e6c28487
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d99970d466aa53d25a80f0600f1fce7819e94956
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579646"
---
# <a name="creating-a-custom-foreach-enumerator"></a><span data-ttu-id="e4804-102">创建自定义 Foreach 枚举器</span><span class="sxs-lookup"><span data-stu-id="e4804-102">Creating a Custom Foreach Enumerator</span></span>
  <span data-ttu-id="e4804-103">创建自定义 foreach 枚举器的步骤与创建其他任何 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 自定义对象的步骤相似。</span><span class="sxs-lookup"><span data-stu-id="e4804-103">The steps involved in creating a custom foreach enumerator are similar to the steps for creating any other custom object for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="e4804-104">创建一个从基类继承的新类。</span><span class="sxs-lookup"><span data-stu-id="e4804-104">Create a new class that inherits from the base class.</span></span> <span data-ttu-id="e4804-105">对于 foreach 枚举器，基类是 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>。</span><span class="sxs-lookup"><span data-stu-id="e4804-105">For a foreach enumerator, the base class is <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>.</span></span>  
  
-   <span data-ttu-id="e4804-106">将标识对象类型的属性应用于该类。</span><span class="sxs-lookup"><span data-stu-id="e4804-106">Apply the attribute that identifies the type of object to the class.</span></span> <span data-ttu-id="e4804-107">对于 foreach 枚举器，该属性为 <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>。</span><span class="sxs-lookup"><span data-stu-id="e4804-107">For a foreach enumerator, the attribute is <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>.</span></span>  
  
-   <span data-ttu-id="e4804-108">替代基类的方法和属性的实现。</span><span class="sxs-lookup"><span data-stu-id="e4804-108">Override the implementation of the base class's methods and properties.</span></span> <span data-ttu-id="e4804-109">对于 foreach 枚举器，最重要的是 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e4804-109">For a foreach enumerator, the most important is the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> method.</span></span>  
  
-   <span data-ttu-id="e4804-110">可以选择开发自定义用户界面。</span><span class="sxs-lookup"><span data-stu-id="e4804-110">Optionally, develop a custom user interface.</span></span> <span data-ttu-id="e4804-111">对于 foreach 枚举器，这需要实现 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSForEachEnumeratorUI> 接口的类。</span><span class="sxs-lookup"><span data-stu-id="e4804-111">For a foreach enumerator, this requires a class that implements the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSForEachEnumeratorUI> interface.</span></span>  
  
 <span data-ttu-id="e4804-112">自定义枚举器由 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> 容器承载。</span><span class="sxs-lookup"><span data-stu-id="e4804-112">A custom enumerator is hosted by the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> container.</span></span> <span data-ttu-id="e4804-113">在运行时，<xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> 容器会调用自定义枚举器的 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e4804-113">At run time, the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> container calls the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> method of the custom enumerator.</span></span> <span data-ttu-id="e4804-114">自定义枚举器会返回一个实现 `IEnumerable` 接口的对象，如 `ArrayList`。</span><span class="sxs-lookup"><span data-stu-id="e4804-114">The custom enumerator returns an object that implements the `IEnumerable` interface, such as an `ArrayList`.</span></span> <span data-ttu-id="e4804-115"><xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> 随后循环访问该集合中的每个元素，并通过一个用户定义的变量将当前元素的值提供给控制流，然后在容器中执行控制流。</span><span class="sxs-lookup"><span data-stu-id="e4804-115">The <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> then iterates over each element in the collection, provides the value of the current element to the control flow through a user-defined variable, and executes the control flow in the container.</span></span>  
  
## <a name="getting-started-with-a-custom-foreach-enumerator"></a><span data-ttu-id="e4804-116">自定义 ForEach 枚举器入门</span><span class="sxs-lookup"><span data-stu-id="e4804-116">Getting Started with a Custom ForEach Enumerator</span></span>  
  
### <a name="creating-projects-and-classes"></a><span data-ttu-id="e4804-117">创建项目和类</span><span class="sxs-lookup"><span data-stu-id="e4804-117">Creating Projects and Classes</span></span>  
 <span data-ttu-id="e4804-118">由于所有托管 foreach 枚举器都是从基类 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> 派生的，因此创建自定义 foreach 枚举器的第一步是创建一个用您首选的托管编程语言编写的类库项目，然后创建一个从该基类继承的类。</span><span class="sxs-lookup"><span data-stu-id="e4804-118">Because all managed foreach enumerators derive from the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> base class, the first step when you create a custom foreach enumerator is to create a class library project in your preferred managed programming language and create a class that inherits from the base class.</span></span> <span data-ttu-id="e4804-119">在此派生类中重写基类的属性和方法可实现您的自定义功能。</span><span class="sxs-lookup"><span data-stu-id="e4804-119">In this derived class you will override the methods and properties of the base class to implement your custom functionality.</span></span>  
  
 <span data-ttu-id="e4804-120">在同一解决方案中，创建另一个类库项目，用于自定义用户界面。</span><span class="sxs-lookup"><span data-stu-id="e4804-120">In the same solution, create a second class library project for the custom user interface.</span></span> <span data-ttu-id="e4804-121">为便于部署，推荐对用户界面使用单独的程序集，因为这样，您就可以分别更新和重新部署 foreach 枚举器或其用户界面。</span><span class="sxs-lookup"><span data-stu-id="e4804-121">A separate assembly for the user interface is recommended for ease of deployment because it allows you to update and redeploy the foreach enumerator or its user interface independently.</span></span>  
  
 <span data-ttu-id="e4804-122">将这两个项目配置为使用强名称密钥文件对在生成时产生的程序集进行签名。</span><span class="sxs-lookup"><span data-stu-id="e4804-122">Configure both projects to sign the assemblies that will be generated at build time by using a strong name key file.</span></span>  
  
### <a name="applying-the-dtsforeachenumerator-attribute"></a><span data-ttu-id="e4804-123">应用 DtsForEachEnumerator 属性</span><span class="sxs-lookup"><span data-stu-id="e4804-123">Applying the DtsForEachEnumerator Attribute</span></span>  
 <span data-ttu-id="e4804-124">将 <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> 属性应用于您创建的类以将其标识为 foreach 枚举器。</span><span class="sxs-lookup"><span data-stu-id="e4804-124">Apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> attribute to the class that you have created to identify it as a foreach enumerator.</span></span> <span data-ttu-id="e4804-125">此属性提供设计时信息，如 foreach 枚举器的名称和说明。</span><span class="sxs-lookup"><span data-stu-id="e4804-125">This attribute provides design-time information such as the name and description of the foreach enumerator.</span></span> <span data-ttu-id="e4804-126">该 `Name` 属性将显示在 " **Foreach 循环编辑器**" 对话框的 "**集合**" 选项卡上的可用枚举器下拉列表中。</span><span class="sxs-lookup"><span data-stu-id="e4804-126">The `Name` property appears in the dropdown list of available enumerators on the **Collection** tab of the **Foreach Loop Editor** dialog box.</span></span>  
  
 <span data-ttu-id="e4804-127">使用 <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> 属性链接 foreach 枚举器与其自定义用户界面。</span><span class="sxs-lookup"><span data-stu-id="e4804-127">Use the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> property to link the foreach enumerator to its custom user interface.</span></span> <span data-ttu-id="e4804-128">要获取此属性所需的公钥令牌，可使用 sn.exe -t 来显示要用于对用户界面程序集签名的密钥对 (.snk) 文件中的公钥令牌  。</span><span class="sxs-lookup"><span data-stu-id="e4804-128">To obtain the public key token that is required for this property, you an use **sn.exe -t** to display the public key token from the key pair (.snk) file that you intend to use to sign the user interface assembly.</span></span>  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
Namespace Microsoft.Samples.SqlServer.Dts  
    <DtsForEachEnumerator(DisplayName = "MyEnumerator", Description="A sample custom enumerator", UITypeName="FullyQualifiedTypeName,AssemblyName,Version=1.00.000.00,Culture=Neutral,PublicKeyToken=<publickeytoken>")> _   
    Public Class MyEnumerator  
     Inherits ForEachEnumerator  
        'Insert code here.  
    End Class  
End Namespace  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsForEachEnumerator( DisplayName = "MyEnumerator", Description="A sample custom enumerator", UITypeName="FullyQualifiedTypeName,AssemblyName,Version=1.00.000.00,Culture=Neutral,PublicKeyToken=<publickeytoken>")]  
    public class MyEnumerator : ForEachEnumerator  
    {  
        //Insert code here.  
    }  
}  
```  
  
## <a name="building-deploying-and-debugging-a-custom-enumerator"></a><span data-ttu-id="e4804-129">生成、部署和调试自定义枚举器</span><span class="sxs-lookup"><span data-stu-id="e4804-129">Building, Deploying, and Debugging a Custom Enumerator</span></span>  
 <span data-ttu-id="e4804-130">在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中生成、部署和调试自定义 foreach 枚举器的步骤与其他自定义对象类型所需的步骤非常相似。</span><span class="sxs-lookup"><span data-stu-id="e4804-130">The steps for building, deploying, and debugging a custom foreach enumerator in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] are very similar to the steps required for other types of custom objects.</span></span> <span data-ttu-id="e4804-131">有关详细信息，请参阅[生成、部署和调试自定义对象](../building-deploying-and-debugging-custom-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="e4804-131">For more information, see [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md).</span></span>  
  
<span data-ttu-id="e4804-132">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="e4804-132">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="e4804-133">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="e4804-133">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="e4804-134">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="e4804-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="e4804-135">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="e4804-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4804-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4804-136">See Also</span></span>  
 <span data-ttu-id="e4804-137">[编写自定义 Foreach 枚举器代码](coding-a-custom-foreach-enumerator.md) </span><span class="sxs-lookup"><span data-stu-id="e4804-137">[Coding a Custom Foreach Enumerator](coding-a-custom-foreach-enumerator.md) </span></span>  
 [<span data-ttu-id="e4804-138">为自定义 ForEach 枚举器开发用户界面</span><span class="sxs-lookup"><span data-stu-id="e4804-138">Developing a User Interface for a Custom ForEach Enumerator</span></span>](developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
  
  
