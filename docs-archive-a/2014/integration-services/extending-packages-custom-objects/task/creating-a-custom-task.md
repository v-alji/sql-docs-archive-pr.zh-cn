---
title: 创建自定义任务 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom tasks [Integration Services], creating
ms.assetid: 42965c09-1782-4cdb-9ce1-216af4c23e0a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f752acad7a442a8e0aad2d24e94938c14195a35d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587919"
---
# <a name="creating-a-custom-task"></a><span data-ttu-id="16a91-102">创建自定义任务</span><span class="sxs-lookup"><span data-stu-id="16a91-102">Creating a Custom Task</span></span>
  <span data-ttu-id="16a91-103">创建自定义任务的步骤与创建其他任何 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 自定义对象的步骤相似：</span><span class="sxs-lookup"><span data-stu-id="16a91-103">The steps involved in creating a custom task are similar to the steps for creating any other custom object for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="16a91-104">创建一个从基类继承的新类。</span><span class="sxs-lookup"><span data-stu-id="16a91-104">Create a new class that inherits from the base class.</span></span> <span data-ttu-id="16a91-105">对于任务，基类是 [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task)。</span><span class="sxs-lookup"><span data-stu-id="16a91-105">For a task, the base class is [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task).</span></span>  
  
-   <span data-ttu-id="16a91-106">将标识对象类型的属性应用于该类。</span><span class="sxs-lookup"><span data-stu-id="16a91-106">Apply the attribute that identifies the type of object to the class.</span></span> <span data-ttu-id="16a91-107">对于任务，该属性是 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>。</span><span class="sxs-lookup"><span data-stu-id="16a91-107">For a task, the attribute is <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>.</span></span>  
  
-   <span data-ttu-id="16a91-108">替代基类的方法和属性的实现。</span><span class="sxs-lookup"><span data-stu-id="16a91-108">Override the implementation of the base class's methods and properties.</span></span> <span data-ttu-id="16a91-109">对于任务，这些方法包括 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A>。</span><span class="sxs-lookup"><span data-stu-id="16a91-109">For a task, these include the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> methods.</span></span>  
  
-   <span data-ttu-id="16a91-110">可以选择开发自定义用户界面。</span><span class="sxs-lookup"><span data-stu-id="16a91-110">Optionally, develop a custom user interface.</span></span> <span data-ttu-id="16a91-111">对于任务，这需要实现 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> 接口的类。</span><span class="sxs-lookup"><span data-stu-id="16a91-111">For a task, this requires a class that implements the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> interface.</span></span>  
  
## <a name="getting-started-with-a-custom-task"></a><span data-ttu-id="16a91-112">自定义任务入门</span><span class="sxs-lookup"><span data-stu-id="16a91-112">Getting Started with a Custom Task</span></span>  
  
### <a name="creating-projects-and-classes"></a><span data-ttu-id="16a91-113">创建项目和类</span><span class="sxs-lookup"><span data-stu-id="16a91-113">Creating Projects and Classes</span></span>  
 <span data-ttu-id="16a91-114">由于所有托管任务都派生自 [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) 基类，所以创建自定义任务的第一步是创建一个用您首选的托管编程语言编写的类库项目，然后创建一个从该基类继承的类。</span><span class="sxs-lookup"><span data-stu-id="16a91-114">Because all managed tasks derive from the [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) base class, the first step when you create a custom task is to create a class library project in your preferred managed programming language and create a class that inherits from the base class.</span></span> <span data-ttu-id="16a91-115">在此派生类中重写基类的属性和方法可实现您的自定义功能。</span><span class="sxs-lookup"><span data-stu-id="16a91-115">In this derived class you will override the methods and properties of the base class to implement your custom functionality.</span></span>  
  
 <span data-ttu-id="16a91-116">在同一解决方案中，创建另一个类库项目，用于自定义用户界面。</span><span class="sxs-lookup"><span data-stu-id="16a91-116">In the same solution, create a second class library project for the custom user interface.</span></span> <span data-ttu-id="16a91-117">为便于部署，推荐对用户界面使用单独的程序集，因为这样，您就可以分别更新和重新部署连接管理器或其用户界面。</span><span class="sxs-lookup"><span data-stu-id="16a91-117">A separate assembly for the user interface is recommended for ease of deployment because it allows you to update and redeploy the connection manager or its user interface independently.</span></span>  
  
 <span data-ttu-id="16a91-118">将这两个项目配置为使用强名称密钥文件对在生成时产生的程序集进行签名。</span><span class="sxs-lookup"><span data-stu-id="16a91-118">Configure both projects to sign the assemblies that will be generated at build time by using a strong name key file.</span></span>  
  
### <a name="applying-the-dtstask-attribute"></a><span data-ttu-id="16a91-119">应用 DtsTask 属性</span><span class="sxs-lookup"><span data-stu-id="16a91-119">Applying the DtsTask Attribute</span></span>  
 <span data-ttu-id="16a91-120">将 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 属性应用于您创建的类以将其标识为任务。</span><span class="sxs-lookup"><span data-stu-id="16a91-120">Apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute to the class that you have created to identify it as a task.</span></span> <span data-ttu-id="16a91-121">此属性提供设计时信息，例如任务的名称、说明和任务类型。</span><span class="sxs-lookup"><span data-stu-id="16a91-121">This attribute provides design-time information such as the name, description, and task type of the task.</span></span>  
  
 <span data-ttu-id="16a91-122">使用 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> 属性链接任务与其自定义用户界面。</span><span class="sxs-lookup"><span data-stu-id="16a91-122">Use the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> property to link the task to its custom user interface.</span></span> <span data-ttu-id="16a91-123">要获取此属性所需的公钥令牌，可使用 sn.exe -t 来显示要用于对用户界面程序集签名的密钥对 (.snk) 文件中的公钥令牌。</span><span class="sxs-lookup"><span data-stu-id="16a91-123">To obtain the public key token that is required for this property, you an use **sn.exe -t** to display the public key token from the key pair (.snk) file that you intend to use to sign the user interface assembly.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
namespace Microsoft.SSIS.Samples  
{  
  [DtsTask  
  (  
   DisplayName = "MyTask",  
   IconResource = "MyTask.MyTaskIcon.ico",  
   UITypeName = "My Custom Task," +  
   "Version=1.0.0.0," +  
   "Culture = Neutral," +  
   "PublicKeyToken = 12345abc6789de01",  
   TaskType = "PackageMaintenance",  
   TaskContact = "MyTask; company name; any other information",  
   RequiredProductLevel = DTSProductLevel.None  
   )]  
  public class MyTask : Task  
  {  
    // Your code here.  
  }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
  
<DtsTask(DisplayName:="MyTask", _  
 IconResource:="MyTask.MyTaskIcon.ico", _  
 UITypeName:="My Custom Task," & _  
 "Version=1.0.0.0,Culture=Neutral," & _  
 "PublicKeyToken=12345abc6789de01", _  
 TaskType:="PackageMaintenance", _  
 TaskContact:="MyTask; company name; any other information", _  
 RequiredProductLevel:=DTSProductLevel.None)> _  
Public Class MyTask  
  Inherits Task  
  
  ' Your code here.  
  
End Class 'MyTask  
```  
  
## <a name="building-deploying-and-debugging-a-custom-task"></a><span data-ttu-id="16a91-124">生成、部署和调试自定义任务</span><span class="sxs-lookup"><span data-stu-id="16a91-124">Building, Deploying, and Debugging a Custom Task</span></span>  
 <span data-ttu-id="16a91-125">在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中生成、部署和调试自定义任务的步骤与其他自定义对象类型所需的步骤相似。</span><span class="sxs-lookup"><span data-stu-id="16a91-125">The steps for building, deploying, and debugging a custom task in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] are similar to the steps required for other types of custom objects.</span></span> <span data-ttu-id="16a91-126">有关详细信息，请参阅[生成、部署和调试自定义对象](../building-deploying-and-debugging-custom-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="16a91-126">For more information, see [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md).</span></span>  
  
<span data-ttu-id="16a91-127">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="16a91-127">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="16a91-128">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="16a91-128">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="16a91-129">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="16a91-129">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="16a91-130">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="16a91-130">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16a91-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="16a91-131">See Also</span></span>  
 <span data-ttu-id="16a91-132">[创建自定义任务](creating-a-custom-task.md) </span><span class="sxs-lookup"><span data-stu-id="16a91-132">[Creating a Custom Task](creating-a-custom-task.md) </span></span>  
 <span data-ttu-id="16a91-133">[编写自定义任务代码](coding-a-custom-task.md) </span><span class="sxs-lookup"><span data-stu-id="16a91-133">[Coding a Custom Task](coding-a-custom-task.md) </span></span>  
 [<span data-ttu-id="16a91-134">为自定义任务开发用户界面</span><span class="sxs-lookup"><span data-stu-id="16a91-134">Developing a User Interface for a Custom Task</span></span>](developing-a-user-interface-for-a-custom-task.md)  
  
  
