---
title: 创建自定义日志提供程序 | Microsoft Docs
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
- custom log providers [Integration Services], creating
ms.assetid: fc20af96-9eb8-4195-8d3f-8a4d7c753f24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c1efb736aece2cc8d118c81326989559f0d17a60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689944"
---
# <a name="creating-a-custom-log-provider"></a><span data-ttu-id="fa443-102">创建自定义日志提供程序</span><span class="sxs-lookup"><span data-stu-id="fa443-102">Creating a Custom Log Provider</span></span>
  <span data-ttu-id="fa443-103">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 运行时环境具有广泛的日志记录功能。</span><span class="sxs-lookup"><span data-stu-id="fa443-103">The [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] run-time environment has extensive logging capabilities.</span></span> <span data-ttu-id="fa443-104">日志可使您捕获在包执行期间发生的事件。</span><span class="sxs-lookup"><span data-stu-id="fa443-104">A log lets you capture events that occur during package execution.</span></span> [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="fa443-105">包含各种日志提供程序，可用于创建日志并以诸如 XML、文本、数据库或 Windows 事件日志的格式存储这些日志。</span><span class="sxs-lookup"><span data-stu-id="fa443-105">includes a variety of log providers that enable logs to be created and stored in multiple formats, such as XML, text, database, or in the Windows event log.</span></span> <span data-ttu-id="fa443-106">如果这些提供程序或输出格式不能满足您的需要，您可以创建自定义日志提供程序。</span><span class="sxs-lookup"><span data-stu-id="fa443-106">If one of these providers or output formats does not fit your needs, you can create a custom log provider.</span></span>

 <span data-ttu-id="fa443-107">创建自定义日志提供程序的步骤与创建其他任何 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 自定义对象的步骤相似：</span><span class="sxs-lookup"><span data-stu-id="fa443-107">The steps involved in creating a custom log provider are similar to the steps for creating any other custom object for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:</span></span>

-   <span data-ttu-id="fa443-108">创建一个从基类继承的新类。</span><span class="sxs-lookup"><span data-stu-id="fa443-108">Create a new class that inherits from the base class.</span></span> <span data-ttu-id="fa443-109">对于日志提供程序，该基类为 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>。</span><span class="sxs-lookup"><span data-stu-id="fa443-109">For a log provider, the base class is <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>.</span></span>

-   <span data-ttu-id="fa443-110">将标识对象类型的属性应用于该类。</span><span class="sxs-lookup"><span data-stu-id="fa443-110">Apply the attribute that identifies the type of object to the class.</span></span> <span data-ttu-id="fa443-111">对于日志提供程序，该属性为 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute>。</span><span class="sxs-lookup"><span data-stu-id="fa443-111">For a log provider, the attribute is <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute>.</span></span>

-   <span data-ttu-id="fa443-112">替代基类的方法和属性的实现。</span><span class="sxs-lookup"><span data-stu-id="fa443-112">Override the implementation of the base class's methods and properties.</span></span> <span data-ttu-id="fa443-113">对于日志提供程序，所涉及的属性和方法包括 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> 属性以及 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="fa443-113">For a log provider, these include the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> property and the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> methods.</span></span>

-   <span data-ttu-id="fa443-114">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中不实现自定义日志提供程序的自定义用户界面。</span><span class="sxs-lookup"><span data-stu-id="fa443-114">Custom user interfaces for custom log providers are not implemented in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>

## <a name="getting-started-with-a-custom-log-provider"></a><span data-ttu-id="fa443-115">自定义日志提供程序入门</span><span class="sxs-lookup"><span data-stu-id="fa443-115">Getting Started with a Custom Log Provider</span></span>

### <a name="creating-projects-and-classes"></a><span data-ttu-id="fa443-116">创建项目和类</span><span class="sxs-lookup"><span data-stu-id="fa443-116">Creating Projects and Classes</span></span>
 <span data-ttu-id="fa443-117">由于所有托管日志提供程序都派生自 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> 基类，所以创建自定义日志提供程序的第一步是以您的首选托管编程语言创建一个类库项目，然后创建一个从该基类继承的类。</span><span class="sxs-lookup"><span data-stu-id="fa443-117">Because all managed log providers derive from the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> base class, the first step when you create a custom log provider is to create a class library project in your preferred managed programming language, and then create a class that inherits from the base class.</span></span> <span data-ttu-id="fa443-118">在此派生类中重写基类的属性和方法可实现您的自定义功能。</span><span class="sxs-lookup"><span data-stu-id="fa443-118">In this derived class you will override the methods and properties of the base class to implement your custom functionality.</span></span>

 <span data-ttu-id="fa443-119">将此项目配置为使用强名称密钥文件对将要生成的程序集进行签名。</span><span class="sxs-lookup"><span data-stu-id="fa443-119">Configure the project to sign the assembly that will be generated with a strong name key file.</span></span>

> [!NOTE]
>  <span data-ttu-id="fa443-120">许多 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 日志提供程序都有一个自定义用户界面，该界面实现 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI>，并用已筛选的可用连接管理器下拉列表替换“配置 SSIS 日志”对话框中的“配置”文本框   。</span><span class="sxs-lookup"><span data-stu-id="fa443-120">Many [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] log providers have a custom user interface that implements <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> and replaces the **Configuration** text box in the **Configure SSIS Logs** dialog box with a filtered dropdown list of available connection managers.</span></span> <span data-ttu-id="fa443-121">但是，[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中不实现自定义日志提供程序的自定义用户界面。</span><span class="sxs-lookup"><span data-stu-id="fa443-121">However custom user interfaces for custom log providers are not implemented in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>

### <a name="applying-the-dtslogprovider-attribute"></a><span data-ttu-id="fa443-122">应用 DtsLogProvider 属性</span><span class="sxs-lookup"><span data-stu-id="fa443-122">Applying the DtsLogProvider Attribute</span></span>
 <span data-ttu-id="fa443-123">将 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> 属性应用于您创建的类以将其标识为日志提供程序。</span><span class="sxs-lookup"><span data-stu-id="fa443-123">Apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> attribute to the class that you have created to identify it as a log provider.</span></span> <span data-ttu-id="fa443-124">此属性提供设计时信息，如日志提供程序的名称和说明。</span><span class="sxs-lookup"><span data-stu-id="fa443-124">This attribute provides design-time information such as the name and description of the log provider.</span></span> <span data-ttu-id="fa443-125">`DisplayName`属性的和 `Description` 属性对应于 " **Name** `Description` **配置 SSIS 日志**编辑器" 中显示的名称和列，在中为包配置日志记录时，将显示该编辑器 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fa443-125">The `DisplayName` and `Description` properties of the attribute correspond to the **Name** and `Description` columns displayed in the **Configure SSIS Logs** editor, which is displayed when configuring logging for a package in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="fa443-126">不使用此特性的 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.LogProviderType%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="fa443-126">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.LogProviderType%2A> property of the attribute is not used.</span></span> <span data-ttu-id="fa443-127">但是，必须为该属性输入一个值，否则自定义日志提供程序将不会显示在可用日志提供程序列表中。</span><span class="sxs-lookup"><span data-stu-id="fa443-127">However, you must enter a value for it, or the custom log provider will not appear in the list of available log providers.</span></span>

> [!NOTE]
>  <span data-ttu-id="fa443-128">由于自定义日志提供程序的自定义用户界面不在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中实现，因此，为 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.UITypeName%2A> 的 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> 属性指定值将不起作用。</span><span class="sxs-lookup"><span data-stu-id="fa443-128">Since custom user interfaces for custom log providers are not implemented in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], specifying a value for the <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.UITypeName%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> has no effect.</span></span>

```vb
<DtsLogProvider(DisplayName:="MyLogProvider", Description:="A simple log provider.", LogProviderType:="Custom")> _
Public Class MyLogProvider
     Inherits LogProviderBase
    ' TODO: Override the base class methods.
End Class
```

```csharp
[DtsLogProvider(DisplayName="MyLogProvider", Description="A simple log provider.", LogProviderType="Custom")]
public class MyLogProvider : LogProviderBase
{
    // TODO: Override the base class methods.
}
```

## <a name="building-deploying-and-debugging-a-custom-log-provider"></a><span data-ttu-id="fa443-129">生成、部署和调试自定义日志提供程序</span><span class="sxs-lookup"><span data-stu-id="fa443-129">Building, Deploying, and Debugging a Custom Log Provider</span></span>
 <span data-ttu-id="fa443-130">在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中生成、部署和调试自定义日志提供程序的步骤与其他自定义对象类型所需的步骤非常相似。</span><span class="sxs-lookup"><span data-stu-id="fa443-130">The steps for building, deploying, and debugging a custom log provider in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] are very similar to the steps required for other types of custom objects.</span></span> <span data-ttu-id="fa443-131">有关详细信息，请参阅[生成、部署和调试自定义对象](../building-deploying-and-debugging-custom-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="fa443-131">For more information, see [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md).</span></span>

<span data-ttu-id="fa443-132">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="fa443-132">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="fa443-133">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="fa443-133">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="fa443-134">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="fa443-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="fa443-135">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="fa443-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa443-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa443-136">See Also</span></span>
 <span data-ttu-id="fa443-137">[编写自定义日志提供程序的代码](coding-a-custom-log-provider.md)[为自定义日志提供程序开发用户界面](developing-a-user-interface-for-a-custom-log-provider.md)</span><span class="sxs-lookup"><span data-stu-id="fa443-137">[Coding a Custom Log Provider](coding-a-custom-log-provider.md) [Developing a User Interface for a Custom Log Provider](developing-a-user-interface-for-a-custom-log-provider.md)</span></span>


