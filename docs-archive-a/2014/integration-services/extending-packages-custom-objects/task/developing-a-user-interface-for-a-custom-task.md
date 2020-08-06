---
title: 为自定义任务开发用户界面 | Microsoft Docs
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
- custom user interfaces [Integration Services]
- IDtsTaskUI interface
- DtsTaskAttribute attribute
- custom tasks [Integration Services], user interface
- custom user interface [Integration Services], custom tasks
- user interface [Integration Services]
- SSIS custom tasks, user interface
ms.assetid: 1e940cd1-c5f8-4527-b678-e89ba5dc398a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ed96bbc302cba4c207e5ce7b2e4fb4b74fed4ee2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590290"
---
# <a name="developing-a-user-interface-for-a-custom-task"></a><span data-ttu-id="4c393-102">为自定义任务开发用户界面</span><span class="sxs-lookup"><span data-stu-id="4c393-102">Developing a User Interface for a Custom Task</span></span>
  <span data-ttu-id="4c393-103">自定义任务开发人员使用 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 对象模型可以轻松地为任务创建自定义用户界面，该任务随后可以集成并显示在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="4c393-103">The [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] object model provides custom task developers the ability to easily create a custom user interface for a task that can then be integrated and displayed in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="4c393-104">用户界面可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中向用户提供有用的信息，并指导用户正确配置自定义任务的属性和设置。</span><span class="sxs-lookup"><span data-stu-id="4c393-104">The user interface can provide helpful information to the user in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, and guide users to correctly configure the properties and settings of the custom task.</span></span>  
  
 <span data-ttu-id="4c393-105">为任务开发自定义用户界面包括使用两个重要的类。</span><span class="sxs-lookup"><span data-stu-id="4c393-105">Developing a custom user interface for a task involves using two important classes.</span></span> <span data-ttu-id="4c393-106">下表介绍了这两个类。</span><span class="sxs-lookup"><span data-stu-id="4c393-106">The following table describes those classes.</span></span>  
  
|<span data-ttu-id="4c393-107">类</span><span class="sxs-lookup"><span data-stu-id="4c393-107">Class</span></span>|<span data-ttu-id="4c393-108">说明</span><span class="sxs-lookup"><span data-stu-id="4c393-108">Description</span></span>|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>|<span data-ttu-id="4c393-109">标识托管任务的特性，该特性通过其属性提供设计时信息以控制 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器显示对象和与对象交互的方式。</span><span class="sxs-lookup"><span data-stu-id="4c393-109">An attribute that identifies a managed task, and supplies design-time information through its properties to control how [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer displays and interacts with the object.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI>|<span data-ttu-id="4c393-110">任务所用的接口，用来将任务与其自定义用户界面相关联。</span><span class="sxs-lookup"><span data-stu-id="4c393-110">An interface used by the task to associate the task with its custom user interface.</span></span>|  
  
 <span data-ttu-id="4c393-111">本节介绍为自定义任务开发用户界面时，<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 特性和 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> 接口的角色，并提供有关如何在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中创建、集成、部署和调试任务的详细信息。</span><span class="sxs-lookup"><span data-stu-id="4c393-111">This section describes the role of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute and the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> interface when you are developing a user interface for a custom task, and provides details about how to create, integrate, deploy, and debug the task within [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="4c393-112">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器为任务提供用户界面的多个入口点：用户可以从快捷菜单中选择“编辑”  ，双击任务，或者单击属性表底部的“显示编辑器”  链接。</span><span class="sxs-lookup"><span data-stu-id="4c393-112">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer provides multiple entry points to the user interface for the task: the user can select **Edit** on the shortcut menu, double-click the task, or click the **Show Editor** link at the bottom of the property sheet.</span></span> <span data-ttu-id="4c393-113">当用户访问其中一个入口点时，[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 编辑器会定位并加载包含该任务的用户界面的程序集。</span><span class="sxs-lookup"><span data-stu-id="4c393-113">When the user accesses one of these entry points, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer locates and loads the assembly that contains the user interface for the task.</span></span> <span data-ttu-id="4c393-114">任务的用户界面负责创建在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中向用户显示的属性对话框。</span><span class="sxs-lookup"><span data-stu-id="4c393-114">The user interface for the task is responsible for creating the properties dialog box that is displayed to the user in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="4c393-115">任务及其用户界面是不同的实体。</span><span class="sxs-lookup"><span data-stu-id="4c393-115">A task and its user interface are separate entities.</span></span> <span data-ttu-id="4c393-116">应该在不同的程序集中实现它们，以减少本地化、部署和维护的工作。</span><span class="sxs-lookup"><span data-stu-id="4c393-116">They should be implemented in separate assemblies to reduce localization, deployment, and maintenance work.</span></span> <span data-ttu-id="4c393-117">除了在任务中编码的 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 特性值中包含的信息外，任务 DLL 不会加载、调用或通常的包含其用户界面的任何知识。</span><span class="sxs-lookup"><span data-stu-id="4c393-117">The task DLL does not load, call, or generally contain any knowledge of its user interface, except for the information that is contained in the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute values coded in the task.</span></span> <span data-ttu-id="4c393-118">此信息是任务与其用户界面相关联的唯一方式。</span><span class="sxs-lookup"><span data-stu-id="4c393-118">This is the only way that a task and its user interface are associated.</span></span>  
  
## <a name="the-dtstask-attribute"></a><span data-ttu-id="4c393-119">DtsTask 特性</span><span class="sxs-lookup"><span data-stu-id="4c393-119">The DtsTask Attribute</span></span>  
 <span data-ttu-id="4c393-120"><xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 特性包含在任务类代码中，用于关联任务与其用户界面。</span><span class="sxs-lookup"><span data-stu-id="4c393-120">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute is included in the task class code to associate a task with its user interface.</span></span> <span data-ttu-id="4c393-121">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器使用该特性的属性来确定任务在设计器中的显示方式。</span><span class="sxs-lookup"><span data-stu-id="4c393-121">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer uses the properties of the attribute to determine how to display the task in the designer.</span></span> <span data-ttu-id="4c393-122">这些属性包含要显示的名称和图标（如果有）。</span><span class="sxs-lookup"><span data-stu-id="4c393-122">These properties include the name to display and the icon, if any.</span></span>  
  
 <span data-ttu-id="4c393-123">下表介绍了 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 特性的各属性。</span><span class="sxs-lookup"><span data-stu-id="4c393-123">The following table describes the properties of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute.</span></span>  
  
|<span data-ttu-id="4c393-124">properties</span><span class="sxs-lookup"><span data-stu-id="4c393-124">Property</span></span>|<span data-ttu-id="4c393-125">说明</span><span class="sxs-lookup"><span data-stu-id="4c393-125">Description</span></span>|  
|--------------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.DisplayName%2A>|<span data-ttu-id="4c393-126">在“控制流”工具箱中显示任务名称。</span><span class="sxs-lookup"><span data-stu-id="4c393-126">Displays the task name in the Control Flow toolbox.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.Description%2A>|<span data-ttu-id="4c393-127">任务说明（继承自 <xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute>）。</span><span class="sxs-lookup"><span data-stu-id="4c393-127">The task description (inherited from <xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute>).</span></span> <span data-ttu-id="4c393-128">此属性显示在工具提示中。</span><span class="sxs-lookup"><span data-stu-id="4c393-128">This property is shown in ToolTips.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A>|<span data-ttu-id="4c393-129">显示在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中的图标。</span><span class="sxs-lookup"><span data-stu-id="4c393-129">The icon displayed in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.RequiredProductLevel%2A>|<span data-ttu-id="4c393-130">如果使用，请将其设置为 <xref:Microsoft.SqlServer.Dts.Runtime.DTSProductLevel> 枚举中的一个值。</span><span class="sxs-lookup"><span data-stu-id="4c393-130">If used, set it to one of the values in the <xref:Microsoft.SqlServer.Dts.Runtime.DTSProductLevel> enumeration.</span></span> <span data-ttu-id="4c393-131">例如，`RequiredProductLevel = DTSProductLevel.None` 。</span><span class="sxs-lookup"><span data-stu-id="4c393-131">For example, `RequiredProductLevel = DTSProductLevel.None`.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.TaskContact%2A>|<span data-ttu-id="4c393-132">保存联系信息，以备任务需要技术支持。</span><span class="sxs-lookup"><span data-stu-id="4c393-132">Holds contact information for occasions when the task requires technical support.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.TaskType%2A>|<span data-ttu-id="4c393-133">为任务分配类型。</span><span class="sxs-lookup"><span data-stu-id="4c393-133">Assigns a type to the task.</span></span>|  
|<span data-ttu-id="4c393-134">Attribute.TypeId</span><span class="sxs-lookup"><span data-stu-id="4c393-134">Attribute.TypeId</span></span>|<span data-ttu-id="4c393-135">在派生类中实现时，获取此特性的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="4c393-135">When implemented in a derived class, gets a unique identifier for this Attribute.</span></span> <span data-ttu-id="4c393-136">有关详细信息，请参阅 .NET Framework 类库中的 `Attribute.TypeID` 属性。</span><span class="sxs-lookup"><span data-stu-id="4c393-136">For more information, see `Attribute.TypeID` property in the .NET Framework Class Library.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A>|<span data-ttu-id="4c393-137">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器用于加载程序集的程序集类型名。</span><span class="sxs-lookup"><span data-stu-id="4c393-137">The type name of the assembly that is used by [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer to load the assembly.</span></span> <span data-ttu-id="4c393-138">此属性用于查找任务的用户界面程序集。</span><span class="sxs-lookup"><span data-stu-id="4c393-138">This property is used to find the user interface assembly for the task.</span></span>|  
  
 <span data-ttu-id="4c393-139">下面的代码示例演示按照上面的类定义进行编码以得到所需显示效果的 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>。</span><span class="sxs-lookup"><span data-stu-id="4c393-139">The following code example shows the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> as it would look, coded above the class definition.</span></span>  
  
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
  
 <span data-ttu-id="4c393-140">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器使用包含程序集名称、类型名称、版本、区域性和公钥标记的特性的 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> 属性在全局程序集缓存 (GAC) 中查找程序集并加载该程序集，以供设计器使用。</span><span class="sxs-lookup"><span data-stu-id="4c393-140">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer uses the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> property of the attribute that includes the assembly name, type name, version, culture, and public key token, to locate the assembly in the Global Assembly Cache (GAC) and load it for use by the designer.</span></span>  
  
 <span data-ttu-id="4c393-141">找到程序集后，[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器使用该特性中的其他属性在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中显示任务的其他信息，例如任务的名称、图标和说明。</span><span class="sxs-lookup"><span data-stu-id="4c393-141">After the assembly has been located, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer uses the other properties in the attribute to display additional information about the task in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, such as the name, icon, and description of the task.</span></span>  
  
 <span data-ttu-id="4c393-142"><xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.DisplayName%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.Description%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A> 属性指定将任务呈现给用户的方式。</span><span class="sxs-lookup"><span data-stu-id="4c393-142">The <xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.DisplayName%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.Description%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A> properties specify how the task is presented to the user.</span></span> <span data-ttu-id="4c393-143"><xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A> 属性包含嵌入在用户界面程序集中的图标的资源 ID。</span><span class="sxs-lookup"><span data-stu-id="4c393-143">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A> property contains the resource ID of the icon embedded in the user interface assembly.</span></span> <span data-ttu-id="4c393-144">设计器根据 ID 从程序集中加载图标资源，并且在任务添加到包后，将其显示在工具箱中和设计器图面上任务名称的旁边。</span><span class="sxs-lookup"><span data-stu-id="4c393-144">The designer loads the icon resource by ID from the assembly, and displays it next to the task name in the toolbox and on the designer surface when the task is added to a package.</span></span> <span data-ttu-id="4c393-145">如果任务未提供图标资源，设计器将对该任务使用默认图标。</span><span class="sxs-lookup"><span data-stu-id="4c393-145">If a task does not provide an icon resource, the designer uses a default icon for the task.</span></span>  
  
## <a name="the-idtstaskui-interface"></a><span data-ttu-id="4c393-146">IDTSTaskUI 接口</span><span class="sxs-lookup"><span data-stu-id="4c393-146">The IDTSTaskUI Interface</span></span>  
 <span data-ttu-id="4c393-147"><xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> 接口定义 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器为初始化和显示与任务关联的用户界面而调用的方法和属性的集合。</span><span class="sxs-lookup"><span data-stu-id="4c393-147">The <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> interface defines the collection of methods and properties called by [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer to initialize and display the user interface associated with the task.</span></span> <span data-ttu-id="4c393-148">调用任务的用户界面时，设计器调用 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.Initialize%2A> 方法（该方法在您写入时由任务用户界面实现），然后分别提供任务和包的 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 集合和 <xref:Microsoft.SqlServer.Dts.Runtime.Connections> 集合作为参数。</span><span class="sxs-lookup"><span data-stu-id="4c393-148">When the user interface for a task is invoked, the designer calls the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.Initialize%2A> method, implemented by the task user interface when you wrote it, and then provides the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> and <xref:Microsoft.SqlServer.Dts.Runtime.Connections> collections of the task and package, respectively, as parameters.</span></span> <span data-ttu-id="4c393-149">这些集合存储在本地，随后用在 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> 方法中。</span><span class="sxs-lookup"><span data-stu-id="4c393-149">These collections are stored locally, and used subsequently in the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> method.</span></span>  
  
 <span data-ttu-id="4c393-150">设计器调用 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> 方法以请求显示在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中的窗口。</span><span class="sxs-lookup"><span data-stu-id="4c393-150">The designer calls the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> method to request the window that is displayed in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="4c393-151">任务会创建一个包含任务的用户界面的窗口实例，并将用户界面返回设计器以供显示。</span><span class="sxs-lookup"><span data-stu-id="4c393-151">The task creates an instance of the window that contains the user interface for the task, and returns the user interface to the designer for display.</span></span> <span data-ttu-id="4c393-152">通常，<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 和 <xref:Microsoft.SqlServer.Dts.Runtime.Connections> 对象通过重载构造函数提供给窗口，以便可以用于配置任务。</span><span class="sxs-lookup"><span data-stu-id="4c393-152">Typically, the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> and <xref:Microsoft.SqlServer.Dts.Runtime.Connections> objects are provided to the window through an overloaded constructor so they can be used to configure the task.</span></span>  
  
 <span data-ttu-id="4c393-153">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器调用任务 UI 的 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> 方法来显示任务的用户界面。</span><span class="sxs-lookup"><span data-stu-id="4c393-153">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer calls the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> method of the task UI to display the user interface for the task.</span></span> <span data-ttu-id="4c393-154">任务用户界面从此方法返回 Windows 窗体，[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器将此窗体显示为模式对话框。</span><span class="sxs-lookup"><span data-stu-id="4c393-154">The task user interface returns the Windows form from this method, and [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer shows this form as a modal dialog box.</span></span> <span data-ttu-id="4c393-155">关闭窗体时，[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器将检查该窗体的 `DialogResult` 属性的值，以确定任务是否已修改以及是否应保存这些修改。</span><span class="sxs-lookup"><span data-stu-id="4c393-155">When the form is closed, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer examines the value of the `DialogResult` property of the form to determine whether the task has been modified and if these modifications should be saved.</span></span> <span data-ttu-id="4c393-156">如果 `DialogResult` 属性的值是 `OK`，则 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器将调用任务的持久性方法以保存更改；否则，将放弃更改。</span><span class="sxs-lookup"><span data-stu-id="4c393-156">If the value of the `DialogResult` property is `OK`, the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer calls the persistence methods of the task to save the changes; otherwise, the changes are discarded.</span></span>  
  
 <span data-ttu-id="4c393-157">下面的代码实例实现 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> 接口，并假定存在名为 SampleTaskForm 的 Windows 窗体类。</span><span class="sxs-lookup"><span data-stu-id="4c393-157">The following code sample implements the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> interface, and assumes the existence of a Windows form class named SampleTaskForm.</span></span>  
  
```csharp  
using System;  
using System.Windows.Forms;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Runtime.Design;  
  
namespace Sample  
{  
   public class HelloWorldTaskUI : IDtsTaskUI  
   {  
      TaskHost   taskHost;  
      Connections connections;  
      public void Initialize(TaskHost taskHost, IServiceProvider serviceProvider)  
      {  
         this.taskHost = taskHost;  
         IDtsConnectionService cs = serviceProvider.GetService  
         ( typeof( IDtsConnectionService ) ) as   IDtsConnectionService;   
         this.connections = cs.GetConnections();  
      }  
      public ContainerControl GetView()  
      {  
        return new HelloWorldTaskForm(this.taskHost, this.connections);  
      }  
     public void Delete(IWin32Window parentWindow)  
     {  
     }  
     public void New(IWin32Window parentWindow)  
     {  
     }  
   }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Runtime.Design  
Imports System.Windows.Forms  
  
Public Class HelloWorldTaskUI  
  Implements IDtsTaskUI  
  
  Dim taskHost As TaskHost  
  Dim connections As Connections  
  
  Public Sub Initialize(ByVal taskHost As TaskHost, ByVal serviceProvider As IServiceProvider) _  
    Implements IDtsTaskUI.Initialize  
  
    Dim cs As IDtsConnectionService  
  
    Me.taskHost = taskHost  
    cs = DirectCast(serviceProvider.GetService(GetType(IDtsConnectionService)), IDtsConnectionService)  
    Me.connections = cs.GetConnections()  
  
  End Sub  
  
  Public Function GetView() As ContainerControl _  
    Implements IDtsTaskUI.GetView  
  
    Return New HelloWorldTaskForm(Me.taskHost, Me.connections)  
  
  End Function  
  
  Public Sub Delete(ByVal parentWindow As IWin32Window) _  
    Implements IDtsTaskUI.Delete  
  
  End Sub  
  
  Public Sub [New](ByVal parentWindow As IWin32Window) _  
    Implements IDtsTaskUI.[New]  
  
  End Sub  
  
End Class  
```  
  
<span data-ttu-id="4c393-158">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="4c393-158">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="4c393-159">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="4c393-159">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="4c393-160">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="4c393-160">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="4c393-161">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="4c393-161">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c393-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4c393-162">See Also</span></span>  
 <span data-ttu-id="4c393-163">[创建自定义任务](creating-a-custom-task.md) </span><span class="sxs-lookup"><span data-stu-id="4c393-163">[Creating a Custom Task](creating-a-custom-task.md) </span></span>  
 <span data-ttu-id="4c393-164">[编写自定义任务代码](coding-a-custom-task.md) </span><span class="sxs-lookup"><span data-stu-id="4c393-164">[Coding a Custom Task](coding-a-custom-task.md) </span></span>  
 [<span data-ttu-id="4c393-165">为自定义任务开发用户界面</span><span class="sxs-lookup"><span data-stu-id="4c393-165">Developing a User Interface for a Custom Task</span></span>](developing-a-user-interface-for-a-custom-task.md)  
  
  
