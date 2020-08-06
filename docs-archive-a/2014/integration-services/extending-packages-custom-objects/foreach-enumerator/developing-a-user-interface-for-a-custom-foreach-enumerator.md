---
title: 为自定义 ForEach 枚举器开发用户界面 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom user interface [Integration Services], custom foreach enumerators
- custom foreach enumerators [Integration Services], developing custom user interface
ms.assetid: 8aa4aa80-c9ba-42b3-ba87-ae5ea5d3cac3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 500c67f1ee4577190d7a24286bbfeed0347e92fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586903"
---
# <a name="developing-a-user-interface-for-a-custom-foreach-enumerator"></a><span data-ttu-id="dea45-102">为自定义 ForEach 枚举器开发用户界面</span><span class="sxs-lookup"><span data-stu-id="dea45-102">Developing a User Interface for a Custom ForEach Enumerator</span></span>
  <span data-ttu-id="dea45-103">重写基类的属性和方法的实现以提供自定义功能后，您可能需要为 Foreach 枚举器创建自定义用户界面。</span><span class="sxs-lookup"><span data-stu-id="dea45-103">After you have overridden the implementation of the properties and methods of the base class to provide your custom functionality, you may want to create a custom user interface for your Foreach enumerator.</span></span> <span data-ttu-id="dea45-104">如果未创建自定义用户界面，用户只能使用“属性”窗口来配置新的自定义 Foreach 枚举器。</span><span class="sxs-lookup"><span data-stu-id="dea45-104">If you do not create a custom user interface, users can only configure the new custom Foreach enumerator by using the Properties window.</span></span>  
  
 <span data-ttu-id="dea45-105">在自定义用户界面项目或程序集中，可以创建一个实现 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI> 的类。</span><span class="sxs-lookup"><span data-stu-id="dea45-105">In a custom user interface project or assembly, you create a class that implements <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI>.</span></span> <span data-ttu-id="dea45-106">此类派生自通常用于创建复合控件以承载其他 Windows 窗体控件的 System.Windows.Forms.UserControl。</span><span class="sxs-lookup"><span data-stu-id="dea45-106">This class derives from System.Windows.Forms.UserControl, which is typically used to create a composite control to host other Windows Forms controls.</span></span> <span data-ttu-id="dea45-107">你创建的控件显示在“Foreach 循环编辑器”的“集合”选项卡的“枚举器配置”区域中    。</span><span class="sxs-lookup"><span data-stu-id="dea45-107">The control that you create is displayed in the **Enumerator configuration** area of the **Collection** tab of the **Foreach Loop Editor**.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dea45-108">在按照[生成、部署并调试自定义对象](../building-deploying-and-debugging-custom-objects.md)中的说明生成自定义用户界面并签名而且在全局程序集缓存中安装后，还要在<xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> 的 <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> 属性中提供此类的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="dea45-108">After signing and building your custom user interface and installing it in the global assembly cache as described in [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md), remember to provide the fully qualified name of this class in the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>.</span></span>  
  
## <a name="coding-the-user-interface-control-class"></a><span data-ttu-id="dea45-109">编写用户界面控件类代码</span><span class="sxs-lookup"><span data-stu-id="dea45-109">Coding the User Interface Control Class</span></span>  
  
### <a name="initializing-the-user-interface"></a><span data-ttu-id="dea45-110">初始化用户界面</span><span class="sxs-lookup"><span data-stu-id="dea45-110">Initializing the User Interface</span></span>  
 <span data-ttu-id="dea45-111">可以重写 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.Initialize%2A> 方法以缓存对主机对象以及包中定义的连接管理器集合和变量集合的引用。</span><span class="sxs-lookup"><span data-stu-id="dea45-111">You override the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.Initialize%2A> method to cache references to the host object, and to the collections of connection managers and variables defined in the package.</span></span>  
  
### <a name="setting-properties-on-the-user-interface-control"></a><span data-ttu-id="dea45-112">设置用户界面控件的属性</span><span class="sxs-lookup"><span data-stu-id="dea45-112">Setting Properties on the User Interface Control</span></span>  
 <span data-ttu-id="dea45-113">从中派生用户界面类的 UserControl 类用作承载其他 Windows 窗体控件的复合控件。</span><span class="sxs-lookup"><span data-stu-id="dea45-113">The UserControl class, from which the user interface class is derived, is intended for use as a composite control to host other Windows Forms controls.</span></span> <span data-ttu-id="dea45-114">由于此类承载其他控件，因此您可以像在任何 Windows 窗体应用程序中一样，通过拖放控件、排列控件、设置控件属性以及在运行时响应控件的事件来设计您自己的自定义用户界面。</span><span class="sxs-lookup"><span data-stu-id="dea45-114">Because this class hosts other controls, you can design your custom user interface by dragging and dropping controls, arranging them, setting their properties, and responding at run time to their events as in any Windows Forms application.</span></span>  
  
### <a name="saving-settings"></a><span data-ttu-id="dea45-115">保存设置</span><span class="sxs-lookup"><span data-stu-id="dea45-115">Saving Settings</span></span>  
 <span data-ttu-id="dea45-116">可以重写 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.SaveSettings%2A> 方法，以在用户关闭编辑器时，将用户选择的值从控件复制到枚举器的属性。</span><span class="sxs-lookup"><span data-stu-id="dea45-116">You override the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.SaveSettings%2A> method to copy the values selected by the user from the controls to the properties of the enumerator when the user closes the editor.</span></span>  
  
<span data-ttu-id="dea45-117">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="dea45-117">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="dea45-118">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="dea45-118">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="dea45-119">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="dea45-119">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="dea45-120">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="dea45-120">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dea45-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dea45-121">See Also</span></span>  
 <span data-ttu-id="dea45-122">[创建自定义 Foreach 枚举器](creating-a-custom-foreach-enumerator.md) </span><span class="sxs-lookup"><span data-stu-id="dea45-122">[Creating a Custom Foreach Enumerator](creating-a-custom-foreach-enumerator.md) </span></span>  
 [<span data-ttu-id="dea45-123">编写自定义 Foreach 枚举器代码</span><span class="sxs-lookup"><span data-stu-id="dea45-123">Coding a Custom Foreach Enumerator</span></span>](coding-a-custom-foreach-enumerator.md)  
  
  
