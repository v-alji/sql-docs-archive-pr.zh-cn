---
title: 创建自定义连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom connection managers [Integration Services], creating
ms.assetid: e83f8e02-ace4-42e0-b979-2f6be1460985
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 857efebbe311e5510e15cae9e78a2b424559ded7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694045"
---
# <a name="creating-a-custom-connection-manager"></a><span data-ttu-id="62b20-102">创建自定义连接管理器</span><span class="sxs-lookup"><span data-stu-id="62b20-102">Creating a Custom Connection Manager</span></span>
  <span data-ttu-id="62b20-103">创建自定义连接管理器时必须遵循的步骤与创建任何其他 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 自定义对象的步骤相似。</span><span class="sxs-lookup"><span data-stu-id="62b20-103">The steps that you must follow to create a custom connection manager are similar to the steps for creating any other custom object for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="62b20-104">创建一个从基类继承的新类。</span><span class="sxs-lookup"><span data-stu-id="62b20-104">Create a new class that inherits from the base class.</span></span> <span data-ttu-id="62b20-105">对于连接管理器，该基类为 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase>。</span><span class="sxs-lookup"><span data-stu-id="62b20-105">For a connection manager, the base class is <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase>.</span></span>  
  
-   <span data-ttu-id="62b20-106">将标识对象类型的属性应用于该类。</span><span class="sxs-lookup"><span data-stu-id="62b20-106">Apply the attribute that identifies the type of object to the class.</span></span> <span data-ttu-id="62b20-107">对于连接管理器，该属性为 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>。</span><span class="sxs-lookup"><span data-stu-id="62b20-107">For a connection manager, the attribute is <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>.</span></span>  
  
-   <span data-ttu-id="62b20-108">重写基类的方法和属性的实现。</span><span class="sxs-lookup"><span data-stu-id="62b20-108">Override the implementation of the methods and properties of the base class.</span></span> <span data-ttu-id="62b20-109">对于连接管理器，所涉及的属性和方法包括 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> 属性以及 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="62b20-109">For a connection manager, these include the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> property and the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> methods.</span></span>  
  
-   <span data-ttu-id="62b20-110">可以选择开发自定义用户界面。</span><span class="sxs-lookup"><span data-stu-id="62b20-110">Optionally, develop a custom user interface.</span></span> <span data-ttu-id="62b20-111">对于连接管理器，这需要一个实现 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> 接口的类。</span><span class="sxs-lookup"><span data-stu-id="62b20-111">For a connection manager, this requires a class that implements the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> interface.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="62b20-112">内置于 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 的大多数任务、源和目标都只能与特定类型的内置连接管理器一起工作。</span><span class="sxs-lookup"><span data-stu-id="62b20-112">Most of the tasks, sources, and destinations that have been built into [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] work only with specific types of built-in connection managers.</span></span> <span data-ttu-id="62b20-113">因此，不能使用内置任务和组件测试这些示例。</span><span class="sxs-lookup"><span data-stu-id="62b20-113">Therefore, these samples cannot be tested with the built-in tasks and components.</span></span>  
  
## <a name="getting-started-with-a-custom-connection-manager"></a><span data-ttu-id="62b20-114">自定义连接管理器入门</span><span class="sxs-lookup"><span data-stu-id="62b20-114">Getting Started with a Custom Connection Manager</span></span>  
  
### <a name="creating-projects-and-classes"></a><span data-ttu-id="62b20-115">创建项目和类</span><span class="sxs-lookup"><span data-stu-id="62b20-115">Creating Projects and Classes</span></span>  
 <span data-ttu-id="62b20-116">由于所有托管连接管理器都派生自 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> 基类，因此创建自定义连接管理器的第一步是以您首选的托管编程语言创建一个类库项目，然后创建一个从该基类继承的类。</span><span class="sxs-lookup"><span data-stu-id="62b20-116">Because all managed connection managers derive from the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> base class, the first step when you create a custom connection manager is to create a class library project in your preferred managed programming language and create a class that inherits from the base class.</span></span> <span data-ttu-id="62b20-117">在此派生类中重写基类的属性和方法可实现自定义功能。</span><span class="sxs-lookup"><span data-stu-id="62b20-117">In this derived class, you will override the methods and properties of the base class to implement your custom functionality.</span></span>  
  
 <span data-ttu-id="62b20-118">在同一解决方案中，创建另一个类库项目，用于自定义用户界面。</span><span class="sxs-lookup"><span data-stu-id="62b20-118">In the same solution, create a second class library project for the custom user interface.</span></span> <span data-ttu-id="62b20-119">为便于部署，建议对用户界面使用单独的程序集，因为这可使您分别更新和重新部署连接管理器或其用户界面。</span><span class="sxs-lookup"><span data-stu-id="62b20-119">A separate assembly for the user interface is recommended for ease of deployment because it lets you update and redeploy the connection manager or its user interface independently.</span></span>  
  
 <span data-ttu-id="62b20-120">将这两个项目配置为使用强名称密钥文件对在生成时产生的程序集进行签名。</span><span class="sxs-lookup"><span data-stu-id="62b20-120">Configure both projects to sign the assemblies that will be generated at build time by using a strong name key file.</span></span>  
  
### <a name="applying-the-dtsconnection-attribute"></a><span data-ttu-id="62b20-121">应用 DtsConnection 属性</span><span class="sxs-lookup"><span data-stu-id="62b20-121">Applying the DtsConnection Attribute</span></span>  
 <span data-ttu-id="62b20-122">对已创建的类应用 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> 属性，以将其标识为连接管理器。</span><span class="sxs-lookup"><span data-stu-id="62b20-122">Apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> attribute to the class that you have created to identify it as a connection manager.</span></span> <span data-ttu-id="62b20-123">此属性提供设计时信息，例如连接管理器的名称、说明和连接类型。</span><span class="sxs-lookup"><span data-stu-id="62b20-123">This attribute provides design-time information such as the name, description, and connection type of the connection manager.</span></span> <span data-ttu-id="62b20-124"><xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.ConnectionType%2A>和 `Description` 属性与**Type** `Description` "**添加 SSIS 连接管理器**" 对话框中显示的类型和列相对应，该对话框在中为包配置连接时显示 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="62b20-124">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.ConnectionType%2A> and `Description` properties correspond to the **Type** and `Description` columns displayed in the **Add SSIS Connection Manager** dialog box, which is displayed when configuring connections for a package in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="62b20-125">使用 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.UITypeName%2A> 属性将连接管理器链接到其自定义用户界面。</span><span class="sxs-lookup"><span data-stu-id="62b20-125">Use the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.UITypeName%2A> property to link the connection manager to its custom user interface.</span></span> <span data-ttu-id="62b20-126">要获取此属性所需的公钥令牌，可使用 sn.exe -t 来显示要用于对用户界面程序集签名的密钥对 (.snk) 文件中的公钥令牌  。</span><span class="sxs-lookup"><span data-stu-id="62b20-126">To obtain the public key token that is required for this property, you an use **sn.exe -t** to display the public key token from the key pair (.snk) file that you intend to use to sign the user interface assembly.</span></span>  
  
```vb  
<DtsConnection(ConnectionType:="SQLVB", _  
  DisplayName:="SqlConnectionManager (VB)", _  
  Description:="Connection manager for Sql Server", _  
  UITypeName:="SqlConnMgrUIVB.SqlConnMgrUIVB,SqlConnMgrUIVB,Version=1.0.0.0,Culture=neutral,PublicKeyToken=<insert public key token here>")> _  
Public Class SqlConnMgrVB  
  Inherits ConnectionManagerBase  
  . . .  
End Class  
```  
  
```csharp  
[DtsConnection(ConnectionType = "SQLCS",  
  DisplayName = "SqlConnectionManager (CS)",  
  Description = "Connection manager for Sql Server",  
  UITypeName = "SqlConnMgrUICS.SqlConnMgrUICS,SqlConnMgrUICS,Version=1.0.0.0,Culture=neutral,PublicKeyToken=<insert public key token here>")]  
public class SqlConnMgrCS :  
ConnectionManagerBase  
{  
  . . .  
}  
```  
  
## <a name="building-deploying-and-debugging-a-custom-connection-manager"></a><span data-ttu-id="62b20-127">生成、部署和调试自定义连接管理器</span><span class="sxs-lookup"><span data-stu-id="62b20-127">Building, Deploying, and Debugging a Custom Connection Manager</span></span>  
 <span data-ttu-id="62b20-128">在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中生成、部署和调试自定义连接管理器的步骤与其他自定义对象类型所需的步骤相似。</span><span class="sxs-lookup"><span data-stu-id="62b20-128">The steps for building, deploying, and debugging a custom connection manager in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] are similar to the steps for other types of custom objects.</span></span> <span data-ttu-id="62b20-129">有关详细信息，请参阅[生成、部署和调试自定义对象](../building-deploying-and-debugging-custom-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="62b20-129">For more information, see [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md).</span></span>  
  
<span data-ttu-id="62b20-130">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="62b20-130">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="62b20-131">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="62b20-131">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="62b20-132">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="62b20-132">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="62b20-133">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="62b20-133">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62b20-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62b20-134">See Also</span></span>  
 <span data-ttu-id="62b20-135">[编写自定义连接管理器代码](coding-a-custom-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="62b20-135">[Coding a Custom Connection Manager](coding-a-custom-connection-manager.md) </span></span>  
 [<span data-ttu-id="62b20-136">为自定义连接管理器开发用户界面</span><span class="sxs-lookup"><span data-stu-id="62b20-136">Developing a User Interface for a Custom Connection Manager</span></span>](developing-a-user-interface-for-a-custom-connection-manager.md)  
  
  
