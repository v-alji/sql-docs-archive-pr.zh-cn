---
title: 升级数据流组件的版本 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- PerformUpgrade method
- custom data flow components [Integration Services], upgrading version
- data flow components [Integration Services], upgrading version
- upgrading data flow components [Integration Services]
ms.assetid: c2a298c6-01b3-4ad1-884d-6108165eb56e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f494793a20f1cdcd108553278b82a44daeea75ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591482"
---
# <a name="upgrading-the-version-of-a-data-flow-component"></a><span data-ttu-id="b1fae-102">升级数据流组件的版本</span><span class="sxs-lookup"><span data-stu-id="b1fae-102">Upgrading the Version of a Data Flow Component</span></span>
  <span data-ttu-id="b1fae-103">通过较早版本的组件创建的包可能包含不再有效的元数据，例如已在更新版本的组件中修改其用法的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="b1fae-103">Packages that were created with an older version of your component may contain metadata that is no longer valid, such as custom properties whose usage has been modified in newer versions of the component.</span></span> <span data-ttu-id="b1fae-104">可以重写 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> 基类的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 方法来更新之前保存在较早的包中的元数据，从而反映组件的当前属性。</span><span class="sxs-lookup"><span data-stu-id="b1fae-104">You can override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class to update the metadata previously saved in older packages to reflect the current properties of your component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b1fae-105">为新版本的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 重新编译自定义组件时，如果组件的属性尚未更改，则不必更改 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="b1fae-105">When you recompile a custom component for a new version of [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], you do not have to change the value of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A> property if the component's properties have not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1fae-106">示例</span><span class="sxs-lookup"><span data-stu-id="b1fae-106">Example</span></span>  
 <span data-ttu-id="b1fae-107">下面的示例包含 2.0 版本的虚拟数据流组件的代码。</span><span class="sxs-lookup"><span data-stu-id="b1fae-107">The following sample contains code from version 2.0 of a fictitious data flow component.</span></span> <span data-ttu-id="b1fae-108">新的版本号在 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A> 的 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> 属性中定义。</span><span class="sxs-lookup"><span data-stu-id="b1fae-108">The new version number is defined in the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>.</span></span> <span data-ttu-id="b1fae-109">该组件具有一个用于定义如何处理超出阈值的数值的属性。</span><span class="sxs-lookup"><span data-stu-id="b1fae-109">The component has a property that defines how numeric values that exceed a threshold are to be handled.</span></span> <span data-ttu-id="b1fae-110">在 1.0 版本的虚拟组件中，此属性名为 `RaiseErrorOnInvalidValue` 并接受布尔值 True 或 False。</span><span class="sxs-lookup"><span data-stu-id="b1fae-110">In version 1.0 of the fictitious component, this property was named `RaiseErrorOnInvalidValue` and accepted a Boolean value of true or false.</span></span> <span data-ttu-id="b1fae-111">在 2.0 版本的虚拟组件中，已将属性重命名为 `InvalidValueHandling` 并接受来自自定义枚举的四个可能值中的一个。</span><span class="sxs-lookup"><span data-stu-id="b1fae-111">In version 2.0 of the fictitious component, the property has been renamed to `InvalidValueHandling` and accepts one of four possible values from a custom enumeration.</span></span>  
  
 <span data-ttu-id="b1fae-112">下列示例中的已重写的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> 方法将执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b1fae-112">The overridden <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> method in the following sample performs the following actions:</span></span>  
  
-   <span data-ttu-id="b1fae-113">获取当前版本的组件。</span><span class="sxs-lookup"><span data-stu-id="b1fae-113">Gets the current version of the component.</span></span>  
  
-   <span data-ttu-id="b1fae-114">获取原有自定义属性的值。</span><span class="sxs-lookup"><span data-stu-id="b1fae-114">Gets the value of the old custom property.</span></span>  
  
-   <span data-ttu-id="b1fae-115">删除自定义属性集合中的原有属性。</span><span class="sxs-lookup"><span data-stu-id="b1fae-115">Removes the old property from the custom property collection.</span></span>  
  
-   <span data-ttu-id="b1fae-116">基于原有属性的值设置新自定义属性的值（如果可能）。</span><span class="sxs-lookup"><span data-stu-id="b1fae-116">Sets the value of the new custom property based on the value of the old property, if possible.</span></span>  
  
-   <span data-ttu-id="b1fae-117">将版本元数据设置为当前的组件版本。</span><span class="sxs-lookup"><span data-stu-id="b1fae-117">Sets the version metadata to the current version of the component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b1fae-118">数据流引擎会将自己的版本号传递到 pipelineVersion 参数的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> 方法中  。</span><span class="sxs-lookup"><span data-stu-id="b1fae-118">The data flow engine passes its own version number into the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> method in the *pipelineVersion* parameter.</span></span> <span data-ttu-id="b1fae-119">此参数在 1.0 版本的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中没有任何用处，但是在后续版本中可能有用。</span><span class="sxs-lookup"><span data-stu-id="b1fae-119">This parameter is not useful in version 1.0 of [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], but may become useful in subsequent versions.</span></span>  
  
 <span data-ttu-id="b1fae-120">示例代码只使用直接映射到自定义属性的先前布尔值的两个枚举值。</span><span class="sxs-lookup"><span data-stu-id="b1fae-120">The sample code uses only the two enumeration values that map directly to the prior Boolean values for the custom property.</span></span> <span data-ttu-id="b1fae-121">用户可以在高级编辑器中通过组件的自定义用户界面或以编程方式选择其他可用枚举值。</span><span class="sxs-lookup"><span data-stu-id="b1fae-121">Users can select the other available enumeration values through the component's custom user interface, in the Advanced Editor, or programmatically.</span></span> <span data-ttu-id="b1fae-122">有关在高级编辑器中显示自定义属性的枚举值的信息，请参阅[数据流组件的设计时方法](design-time-methods-of-a-data-flow-component.md)中的“创建自定义属性”。</span><span class="sxs-lookup"><span data-stu-id="b1fae-122">For information on displaying enumeration values for a custom property in the Advanced Editor, see "Creating Custom Properties" in [Design-time Methods of a Data Flow Component](design-time-methods-of-a-data-flow-component.md).</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
<DtsPipelineComponent(ComponentType:=ComponentType.Transform, CurrentVersion:=2)> _  
Public Class PerformUpgrade  
  Inherits PipelineComponent  
  
  ' Define the set of possible values for the new custom property.  
  Private Enum InvalidValueHandling  
    Ignore  
    FireInformation  
    FireWarning  
    FireError  
  End Enum  
  
  Public Overloads Overrides Sub PerformUpgrade(ByVal pipelineVersion As Integer)  
  
    ' Obtain the current component version from the attribute.  
    Dim componentAttribute As DtsPipelineComponentAttribute = _  
      CType(Attribute.GetCustomAttribute(Me.GetType, _  
      GetType(DtsPipelineComponentAttribute), False), _  
      DtsPipelineComponentAttribute)  
    Dim currentVersion As Integer = componentAttribute.CurrentVersion  
  
    ' If the component version saved in the package is less than  
    '  the current version, Version 2, perform the upgrade.  
    If ComponentMetaData.Version < currentVersion Then  
  
      ' Get the current value of the old custom property, RaiseErrorOnInvalidValue,   
      ' and then remove the property from the custom property collection.  
      Dim oldValue As Boolean = False  
      Try  
        Dim oldProperty As IDTSCustomProperty100 = _  
          ComponentMetaData.CustomPropertyCollection("RaiseErrorOnInvalidValue")  
        oldValue = CType(oldProperty.Value, Boolean)  
        ComponentMetaData.CustomPropertyCollection.RemoveObjectByIndex("RaiseErrorOnInvalidValue")  
      Catch ex As Exception  
        ' If the old custom property is not available, ignore the error.  
      End Try  
  
      ' Set the value of the new custom property, InvalidValueHandling,  
      '  by using the appropriate enumeration value.  
      Dim newProperty As IDTSCustomProperty100 = _  
        ComponentMetaData.CustomPropertyCollection("InvalidValueHandling")  
      If oldValue = True Then  
        newProperty.Value = InvalidValueHandling.FireError  
      Else  
        newProperty.Value = InvalidValueHandling.Ignore  
      End If  
  
    End If  
  
    ' Update the saved component version metadata to the current version.  
    ComponentMetaData.Version = currentVersion  
  
  End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
[DtsPipelineComponent(ComponentType = ComponentType.Transform, CurrentVersion = 2)]  
public class PerformUpgradeCS :  
  PipelineComponent  
  
  // Define the set of possible values for the new custom property.  
{  
  private enum InvalidValueHandling  
  {  
    Ignore,  
    FireInformation,  
    FireWarning,  
    FireError  
  };  
  
  public override void PerformUpgrade(int pipelineVersion)  
  {  
  
    // Obtain the current component version from the attribute.  
    DtsPipelineComponentAttribute componentAttribute =   
      (DtsPipelineComponentAttribute)Attribute.GetCustomAttribute(this.GetType(), typeof(DtsPipelineComponentAttribute), false);  
    int currentVersion = componentAttribute.CurrentVersion;  
  
    // If the component version saved in the package is less than  
    //  the current version, Version 2, perform the upgrade.  
    if (ComponentMetaData.Version < currentVersion)  
  
    // Get the current value of the old custom property, RaiseErrorOnInvalidValue,   
    // and then remove the property from the custom property collection.  
    {  
      bool oldValue = false;  
      try  
      {  
        IDTSCustomProperty100 oldProperty =   
          ComponentMetaData.CustomPropertyCollection["RaiseErrorOnInvalidValue"];  
        oldValue = (bool)oldProperty.Value;  
        ComponentMetaData.CustomPropertyCollection.RemoveObjectByIndex("RaiseErrorOnInvalidValue");  
      }  
      catch (Exception ex)  
      {  
        // If the old custom property is not available, ignore the error.  
      }  
  
      // Set the value of the new custom property, InvalidValueHandling,  
      //  by using the appropriate enumeration value.  
      IDTSCustomProperty100 newProperty =   
         ComponentMetaData.CustomPropertyCollection["InvalidValueHandling"];  
      if (oldValue == true)  
      {  
        newProperty.Value = InvalidValueHandling.FireError;  
      }  
      else  
      {  
        newProperty.Value = InvalidValueHandling.Ignore;  
      }  
  
    }  
  
    // Update the saved component version metadata to the current version.  
    ComponentMetaData.Version = currentVersion;  
  
  }  
  
}  
```  
  
<span data-ttu-id="b1fae-123">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="b1fae-123">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="b1fae-124">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="b1fae-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="b1fae-125">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="b1fae-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="b1fae-126">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="b1fae-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
