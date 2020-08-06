---
title: 创建自定义报表项设计时组件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, creating
ms.assetid: 323fd58a-a462-4c48-b188-77ebc0b4212e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b663dc3b0a9c54d1674bf153ee09dd36e0de7a00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577400"
---
# <a name="creating-a-custom-report-item-design-time-component"></a><span data-ttu-id="881dd-102">创建自定义报表项设计时组件</span><span class="sxs-lookup"><span data-stu-id="881dd-102">Creating a Custom Report Item Design-Time Component</span></span>
  <span data-ttu-id="881dd-103">自定义报表项设计时组件是一种可在 Visual Studio 报表设计器环境中使用的控件。</span><span class="sxs-lookup"><span data-stu-id="881dd-103">A custom report item design-time component is a control that can be used in the Visual Studio Report Designer environment.</span></span> <span data-ttu-id="881dd-104">自定义报表项设计时组件可提供能接受拖放操作的激活的设计图面，可与 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 属性浏览器集成，且可提供自定义属性编辑器。</span><span class="sxs-lookup"><span data-stu-id="881dd-104">The custom report item design-time component provides an activated design surface that can accept drag-and-drop operations, integration with the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] property browser, and the ability to provide custom property editors.</span></span>  
  
 <span data-ttu-id="881dd-105">通过自定义报表项设计时组件，用户可以在设计环境下在报表中放置自定义报表项，可以针对自定义报表项设置自定义数据属性，然后可以将自定义报表项另存为报表项目的一部分。</span><span class="sxs-lookup"><span data-stu-id="881dd-105">With a custom report item design-time component, the user can position a custom report item on a report in the design environment, set custom data properties on the custom report item, and then save the custom report item as part of the report project.</span></span>  
  
 <span data-ttu-id="881dd-106">在开发环境中使用设计时组件设置的属性可通过宿主设计环境序列化和反序列化，然后存储为报表定义语言 (RDL) 文件中的元素。</span><span class="sxs-lookup"><span data-stu-id="881dd-106">The properties that are set using the design-time component in the development environment are serialized and deserialized by the host design environment and then stored as elements in the Report Definition Language (RDL) file.</span></span> <span data-ttu-id="881dd-107">报表由报表处理器执行时，使用设计时组件设置的属性将由报表处理器传递给自定义报表项运行时组件，后者将呈现自定义报表项，并将自定义报表项传递回报表处理器。</span><span class="sxs-lookup"><span data-stu-id="881dd-107">When the report is executed by the report processor, the properties that are set using the design-time component are passed by the report processor to a custom report item run-time component, which renders the custom report item and passes it back to the report processor.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="881dd-108">自定义报表项设计时组件以 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 组件的形式实现。</span><span class="sxs-lookup"><span data-stu-id="881dd-108">The custom report item design-time component is implemented as a [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] component.</span></span> <span data-ttu-id="881dd-109">本文档将介绍自定义报表项设计时组件所特有的实现细节。</span><span class="sxs-lookup"><span data-stu-id="881dd-109">This document will describe implementation details specific to the custom report item design-time component.</span></span> <span data-ttu-id="881dd-110">有关使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 开发组件的详细信息，请参阅 MSDN 库中的 [Visual Studio 中的组件](https://go.microsoft.com/fwlink/?LinkId=116576)。</span><span class="sxs-lookup"><span data-stu-id="881dd-110">For more information about developing components using the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], see [Components in Visual Studio](https://go.microsoft.com/fwlink/?LinkId=116576) in the MSDN library.</span></span>  
  
 <span data-ttu-id="881dd-111">有关完全实现的自定义报表项的示例，请参阅 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)（SQL Server Reporting Services 产品示例）。</span><span class="sxs-lookup"><span data-stu-id="881dd-111">For a sample of a fully implemented custom report item, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="implementing-a-design-time-component"></a><span data-ttu-id="881dd-112">实现设计时组件</span><span class="sxs-lookup"><span data-stu-id="881dd-112">Implementing a Design-Time Component</span></span>  
 <span data-ttu-id="881dd-113">自定义报表项设计时组件的主类继承自 `Microsoft.ReportDesigner.CustomReportItemDesigner` 类。</span><span class="sxs-lookup"><span data-stu-id="881dd-113">The main class of a custom report item design-time component is inherited from the `Microsoft.ReportDesigner.CustomReportItemDesigner` class.</span></span> <span data-ttu-id="881dd-114">除了用于 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 控件的标准属性外，该组件类还应定义 `CustomReportItem` 属性。</span><span class="sxs-lookup"><span data-stu-id="881dd-114">In addition to the standard attributes used for a [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] control, your component class should define a `CustomReportItem` attribute.</span></span> <span data-ttu-id="881dd-115">此属性必须与如在 reportserver.config 文件中定义的相应自定义报表项的名称对应。</span><span class="sxs-lookup"><span data-stu-id="881dd-115">This attribute must correspond to the name of the custom report item as it is defined in the reportserver.config file.</span></span> <span data-ttu-id="881dd-116">有关 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 属性的列表，请参阅 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 文档中的“属性”。</span><span class="sxs-lookup"><span data-stu-id="881dd-116">For a list of [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] attributes, see Attributes in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
 <span data-ttu-id="881dd-117">以下代码示例显示的是将应用到自定义报表项设计时控件的属性：</span><span class="sxs-lookup"><span data-stu-id="881dd-117">The following code example shows attributes being applied to a custom report item design-time control:</span></span>  
  
```csharp  
namespace PolygonsCRI  
{  
    [LocalizedName("Polygons")]  
    [Editor(typeof(CustomEditor), typeof(ComponentEditor))]  
        [ToolboxBitmap(typeof(PolygonsDesigner),"Polygons.ico")]  
        [CustomReportItem("Polygons")]  
  
    public class PolygonsDesigner : CustomReportItemDesigner  
    {  
...  
```  
  
### <a name="initializing-the-component"></a><span data-ttu-id="881dd-118">初始化组件</span><span class="sxs-lookup"><span data-stu-id="881dd-118">Initializing the Component</span></span>  
 <span data-ttu-id="881dd-119">可以使用 <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> 类传递自定义报表项的用户指定属性。</span><span class="sxs-lookup"><span data-stu-id="881dd-119">You pass user-specified properties for a custom report item using a <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> class.</span></span> <span data-ttu-id="881dd-120">实现 `CustomReportItemDesigner` 类时应重写 `InitializeNewComponent` 方法以创建相应组件的 <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> 类的新实例，并将其设置为默认值。</span><span class="sxs-lookup"><span data-stu-id="881dd-120">Your implementation of the `CustomReportItemDesigner` class should override the `InitializeNewComponent` method to create a new instance of your component's <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> class and set it to default values.</span></span>  
  
 <span data-ttu-id="881dd-121">下面的代码示例显示的是自定义报表项设计时组件类重写 `CustomReportItemDesigner.InitializeNewComponent` 方法以初始化该组件的 <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> 类的示例：</span><span class="sxs-lookup"><span data-stu-id="881dd-121">The following code example shows an example of a custom report item design-time component class overriding the `CustomReportItemDesigner.InitializeNewComponent` method to initialize the component's <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> class:</span></span>  
  
```csharp  
public override void InitializeNewComponent()  
        {  
            CustomData = new CustomData();  
            CustomData.DataRowHierarchy = new DataHierarchy();  
  
            // Shape grouping  
            CustomData.DataRowHierarchy.DataMembers.Add(new DataMember());  
            CustomData.DataRowHierarchy.DataMembers[0].Group = new Group();  
            CustomData.DataRowHierarchy.DataMembers[0].Group.Name = Name + "_Shape";  
            CustomData.DataRowHierarchy.DataMembers[0].Group.GroupExpressions.Add(new ReportExpression());  
  
            // Point grouping  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers.Add(new DataMember());  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group = new Group();  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group.Name = Name + "_Point";  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group.GroupExpressions.Add(new ReportExpression());  
  
            // Static column  
            CustomData.DataColumnHierarchy = new DataHierarchy();  
            CustomData.DataColumnHierarchy.DataMembers.Add(new DataMember());  
  
            // Points  
            IList<IList<DataValue>> dataValues = new List<IList<DataValue>>();  
            CustomData.DataRows.Add(dataValues);  
            CustomData.DataRows[0].Add(new List<DataValue>());  
            CustomData.DataRows[0][0].Add(NewDataValue("X", ""));  
            CustomData.DataRows[0][0].Add(NewDataValue("Y", ""));  
        }  
```  
  
### <a name="modifying-component-properties"></a><span data-ttu-id="881dd-122">修改组件属性</span><span class="sxs-lookup"><span data-stu-id="881dd-122">Modifying Component Properties</span></span>  
 <span data-ttu-id="881dd-123">可以通过多种方式在设计环境下修改 `CustomData` 属性。</span><span class="sxs-lookup"><span data-stu-id="881dd-123">You can modify `CustomData` properties in the design environment in several ways.</span></span> <span data-ttu-id="881dd-124">可以使用 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 属性浏览器修改任何由设计时组件公开且以 <xref:System.ComponentModel.BrowsableAttribute> 属性标记的特性。</span><span class="sxs-lookup"><span data-stu-id="881dd-124">You can modify any properties that are exposed by the design-time component that are marked with the <xref:System.ComponentModel.BrowsableAttribute> attribute by using the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] property browser.</span></span> <span data-ttu-id="881dd-125">另外，还可通过以下方式修改属性：将相应项拖动到自定义报表项的设计图面，或者在设计环境下右键单击该控件，然后在快捷菜单上选择“属性”以显示自定义属性窗口\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="881dd-125">In addition, you can modify properties by dragging items onto the custom report item's design surface, or by right-clicking the control in the design environment and selecting **Properties** on the shortcut menu to display a custom properties window.</span></span>  
  
 <span data-ttu-id="881dd-126">以下代码示例显示的是已应用 <xref:System.ComponentModel.BrowsableAttribute> 属性的 `Microsoft.ReportDesigner.CustomReportItemDesigner.CustomData` 特性：</span><span class="sxs-lookup"><span data-stu-id="881dd-126">The following code example shows a `Microsoft.ReportDesigner.CustomReportItemDesigner.CustomData` property that has the <xref:System.ComponentModel.BrowsableAttribute> attribute applied:</span></span>  
  
```csharp  
[Browsable(true), Category("Data")]  
public string DataSetName  
{  
      get  
      {  
         return CustomData.DataSetName;  
      }  
      set  
      {  
         CustomData.DataSetName = value;  
      }  
   }  
  
```  
  
 <span data-ttu-id="881dd-127">可以为您的设计时组件提供自定义属性编辑器对话框。</span><span class="sxs-lookup"><span data-stu-id="881dd-127">You can provide your design-time component with a custom properties editor dialog box.</span></span> <span data-ttu-id="881dd-128">自定义属性编辑器实现应继承自 <xref:System.ComponentModel.ComponentEditor> 类，并应创建可用于属性编辑的对话框实例。</span><span class="sxs-lookup"><span data-stu-id="881dd-128">The custom property editor implementation should inherit from the <xref:System.ComponentModel.ComponentEditor> class, and it should create an instance of a dialog box that can be used for property editing.</span></span>  
  
 <span data-ttu-id="881dd-129">下面的示例显示了继承自 <xref:System.ComponentModel.ComponentEditor> 的类的实现，并显示了自定义属性编辑对话框：</span><span class="sxs-lookup"><span data-stu-id="881dd-129">The following example shows an implementation of a class that inherits from <xref:System.ComponentModel.ComponentEditor> and displays a custom property editor dialog box:</span></span>  
  
```csharp  
internal sealed class CustomEditor : ComponentEditor  
{  
   public override bool EditComponent(  
      ITypeDescriptorContext context, object component)  
    {  
     PolygonsDesigner designer = (PolygonsDesigner)component;  
     PolygonProperties dialog = new PolygonProperties();  
     dialog.m_designerComponent = designer;  
     DialogResult result = dialog.ShowDialog();  
     if (result == DialogResult.OK)  
     {  
        designer.Invalidate();  
        designer.ChangeService().OnComponentChanged(designer, null, null, null);  
        return true;  
     }  
     else  
        return false;  
    }  
}  
```  
  
 <span data-ttu-id="881dd-130">自定义属性编辑器对话框可以调用报表设计器表达式编辑器。</span><span class="sxs-lookup"><span data-stu-id="881dd-130">Your custom property editor dialog box can invoke the Report Designer Expression Editor.</span></span> <span data-ttu-id="881dd-131">在下面的示例中，在用户选择相应组合框中的第一个元素时，会调用表达式编辑器：</span><span class="sxs-lookup"><span data-stu-id="881dd-131">In the following example, the Expression Editor is invoked when the user selects the first element in the combo box:</span></span>  
  
```csharp  
private void EditableCombo_SelectedIndexChanged(object sender,   
    EventArgs e)  
{  
   ComboBox combo = (ComboBox)sender;  
   if (combo.SelectedIndex == 0 && m_launchEditor)  
   {  
      m_launchEditor = false;  
      ExpressionEditor editor = new ExpressionEditor();  
      string newValue;  
      newValue = (string)editor.EditValue(null, m_designerComponent.Site, m_oldComboValue);  
      combo.Items[0] = newValue;  
   }  
}  
  
```  
  
### <a name="using-designer-verbs"></a><span data-ttu-id="881dd-132">使用设计器谓词</span><span class="sxs-lookup"><span data-stu-id="881dd-132">Using Designer Verbs</span></span>  
 <span data-ttu-id="881dd-133">设计器谓词是与事件处理程序链接的菜单命令。</span><span class="sxs-lookup"><span data-stu-id="881dd-133">A designer verb is a menu command linked to an event handler.</span></span> <span data-ttu-id="881dd-134">在设计环境下使用自定义报表项运行时控件时，可以添加将显示在相应组件的快捷菜单中的设计器谓词。</span><span class="sxs-lookup"><span data-stu-id="881dd-134">You can add designer verbs that will appear in a component's shortcut menu when your custom report item run-time control is being used in the design environment.</span></span> <span data-ttu-id="881dd-135">可以使用 `Verbs` 属性从运行时组件返回可用设计器谓词的列表。</span><span class="sxs-lookup"><span data-stu-id="881dd-135">You can return the list of available designer verbs from your run-time component by using the `Verbs` property.</span></span>  
  
 <span data-ttu-id="881dd-136">下面的代码示例显示的是将添加到 <xref:System.ComponentModel.Design.DesignerVerbCollection> 的设计器谓词和事件处理程序，以及事件处理程序代码：</span><span class="sxs-lookup"><span data-stu-id="881dd-136">The following code example shows a designer verb and an event handler being added to the <xref:System.ComponentModel.Design.DesignerVerbCollection>, as well as the event handler code:</span></span>  
  
```csharp  
public override DesignerVerbCollection Verbs  
{  
    get  
    {  
        if (m_verbs == null)  
        {  
            m_verbs = new DesignerVerbCollection();  
            m_verbs.Add(new DesignerVerb("Proportional Scaling", new EventHandler(OnProportionalScaling)));  
         m_verbs[0].Checked = (GetCustomProperty("poly:Proportional") == bool.TrueString);  
        }  
  
        return m_verbs;  
    }  
}  
  
private void OnProportionalScaling(object sender, EventArgs e)  
{  
   bool proportional = !  
        (GetCustomProperty("poly:Proportional") == bool.TrueString);  
   m_verbs[0].Checked = proportional;  
   SetCustomProperty("poly:Proportional", proportional.ToString());  
   ChangeService().OnComponentChanged(this, null, null, null);  
   Invalidate();  
}  
```  
  
### <a name="using-adornments"></a><span data-ttu-id="881dd-137">使用修饰</span><span class="sxs-lookup"><span data-stu-id="881dd-137">Using Adornments</span></span>  
 <span data-ttu-id="881dd-138">自定义报表项类还可实现 `Microsoft.ReportDesigner.Design.Adornment` 类。</span><span class="sxs-lookup"><span data-stu-id="881dd-138">Custom report item classes can also implement a `Microsoft.ReportDesigner.Design.Adornment` class.</span></span> <span data-ttu-id="881dd-139">使用修饰后，自定义报表项控件可提供设计图面主矩形之外的区域。</span><span class="sxs-lookup"><span data-stu-id="881dd-139">An adornment allows the custom report item control to provide areas outside the main rectangle of the design surface.</span></span> <span data-ttu-id="881dd-140">这些区域可用来处理用户界面事件，如鼠标单击和拖放操作。</span><span class="sxs-lookup"><span data-stu-id="881dd-140">These areas can handle user interface events, such as mouse clicks and drag-and-drop operations.</span></span> <span data-ttu-id="881dd-141">`Adornment`命名空间中定义的类 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] `Microsoft.ReportDesigner` 是 <xref:System.Windows.Forms.Design.Behavior.Adorner> 在 Windows 窗体中找到的类的传递实现。</span><span class="sxs-lookup"><span data-stu-id="881dd-141">The `Adornment` class that is defined in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] `Microsoft.ReportDesigner` namespace is a pass-through implementation of the <xref:System.Windows.Forms.Design.Behavior.Adorner> class found in Windows Forms.</span></span> <span data-ttu-id="881dd-142">有关类的完整文档 `Adorner` ，请参阅 MSDN library 中的[行为服务概述](https://go.microsoft.com/fwlink/?LinkId=116673)。</span><span class="sxs-lookup"><span data-stu-id="881dd-142">For complete documentation on the `Adorner` class, see [Behavior Service Overview](https://go.microsoft.com/fwlink/?LinkId=116673) in the MSDN library.</span></span> <span data-ttu-id="881dd-143">有关实现类的示例代码 `Microsoft.ReportDesigner.Design.Adornment` ，请参阅[SQL Server Reporting Services 产品示例](https://go.microsoft.com/fwlink/?LinkId=177889)。</span><span class="sxs-lookup"><span data-stu-id="881dd-143">For sample code that implements a `Microsoft.ReportDesigner.Design.Adornment` class, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
 <span data-ttu-id="881dd-144">有关在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 中如何对 Windows 窗体进行编程和使用 Windows 窗体的详细信息，请参见 MSDN Library 中的以下主题：</span><span class="sxs-lookup"><span data-stu-id="881dd-144">For more information about programming and using Windows Forms in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], see these topics in the MSDN Library:</span></span>  
  
-   <span data-ttu-id="881dd-145">Design-Time Attributes for Components（组件的设计时属性）</span><span class="sxs-lookup"><span data-stu-id="881dd-145">Design-Time Attributes for Components</span></span>  
  
-   <span data-ttu-id="881dd-146">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 中的组件</span><span class="sxs-lookup"><span data-stu-id="881dd-146">Components in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]</span></span>  
  
-   <span data-ttu-id="881dd-147">Walkthrough: Creating a Windows Forms Control that Takes Advantage of Visual Studio Design-Time Features（演练：创建一个利用 Visual Studio 设计时功能的 Windows 窗体控件）</span><span class="sxs-lookup"><span data-stu-id="881dd-147">Walkthrough: Creating a Windows Forms Control that Takes Advantage of Visual Studio Design-Time Features</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="881dd-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="881dd-148">See Also</span></span>  
 <span data-ttu-id="881dd-149">[自定义报表项体系结构](custom-report-item-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="881dd-149">[Custom Report Item Architecture](custom-report-item-architecture.md) </span></span>  
 <span data-ttu-id="881dd-150">[创建自定义报表项运行时组件](creating-a-custom-report-item-run-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="881dd-150">[Creating a Custom Report Item Run-Time Component](creating-a-custom-report-item-run-time-component.md) </span></span>  
 <span data-ttu-id="881dd-151">[自定义报表项类库](custom-report-item-class-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="881dd-151">[Custom Report Item Class Libraries](custom-report-item-class-libraries.md) </span></span>  
 [<span data-ttu-id="881dd-152">如何：部署自定义报表项</span><span class="sxs-lookup"><span data-stu-id="881dd-152">How to: Deploy a Custom Report Item</span></span>](how-to-deploy-a-custom-report-item.md)  
  
  
