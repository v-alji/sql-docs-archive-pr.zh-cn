---
title: 自定义报表项类库 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, RDL
- RDL [Reporting Services], custom report items
ms.assetid: f18c5d8f-1d6b-4f0b-8657-c14896c2ce0d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 60f8cf912eb6ff3f5080e9cf757df40f37e65079
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577398"
---
# <a name="custom-report-item-class-libraries"></a><span data-ttu-id="9f996-102">自定义报表项类库</span><span class="sxs-lookup"><span data-stu-id="9f996-102">Custom Report Item Class Libraries</span></span>
  <span data-ttu-id="9f996-103">自定义报表项使用 `Microsoft.ReportDesigner` 命名空间中的类。</span><span class="sxs-lookup"><span data-stu-id="9f996-103">Custom report items use classes from the `Microsoft.ReportDesigner` namespace.</span></span> <span data-ttu-id="9f996-104">用于实现自定义报表项的类可分为两个主要类别：旨在支持自定义报表项基础结构的唯一类和用于封装相关报表定义语言 (RDL) 元素功能的托管包装类。</span><span class="sxs-lookup"><span data-stu-id="9f996-104">The classes used to implement a custom report item can be grouped into two main categories: unique classes designed to support custom report item infrastructure, and managed wrapper classes that encapsulate the functionality of relevant Report Definition Language (RDL) elements.</span></span> <span data-ttu-id="9f996-105">有关如何使用这些类的代码示例，请参阅 [SQL Server Reporting Services Product Samples（SQL Server Reporting Services 产品示例）](https://go.microsoft.com/fwlink/?LinkId=177889)。</span><span class="sxs-lookup"><span data-stu-id="9f996-105">For a code sample on how to use these classes, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="custom-report-item-infrastructure-classes"></a><span data-ttu-id="9f996-106">自定义报表项基础结构类</span><span class="sxs-lookup"><span data-stu-id="9f996-106">Custom Report Item Infrastructure Classes</span></span>  
 <span data-ttu-id="9f996-107">以下类用于实现自定义报表项。</span><span class="sxs-lookup"><span data-stu-id="9f996-107">The following classes are used to implement a custom report item.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f996-108">以下表并非完整列表；这些表仅包括每个类最常用的属性和方法。</span><span class="sxs-lookup"><span data-stu-id="9f996-108">The following tables are not complete listings; they include only the most commonly used properties and methods for each class.</span></span>  
  
### <a name="microsoftreportdesignercustomreportitemdesigner"></a><span data-ttu-id="9f996-109">Microsoft.ReportDesigner.CustomReportItemDesigner</span><span class="sxs-lookup"><span data-stu-id="9f996-109">Microsoft.ReportDesigner.CustomReportItemDesigner</span></span>  
 <span data-ttu-id="9f996-110">这是自定义报表项主类。</span><span class="sxs-lookup"><span data-stu-id="9f996-110">This is the main custom report item class.</span></span> <span data-ttu-id="9f996-111">自定义报表项实现的主类必须继承自此类。</span><span class="sxs-lookup"><span data-stu-id="9f996-111">The main class of your custom report item implementation must inherit from this class.</span></span>  
  
#### <a name="public-properties"></a><span data-ttu-id="9f996-112">公共属性</span><span class="sxs-lookup"><span data-stu-id="9f996-112">Public Properties</span></span>  
  
|||  
|-|-|  
|`Name`|<span data-ttu-id="9f996-113">自定义报表项的名称。</span><span class="sxs-lookup"><span data-stu-id="9f996-113">The name of the custom report item.</span></span>|  
|`Type`|<span data-ttu-id="9f996-114">自定义报表项的类型。</span><span class="sxs-lookup"><span data-stu-id="9f996-114">The type of the custom report item.</span></span>|  
|`CustomData`|<span data-ttu-id="9f996-115">用于封装在设计时指定的自定义报表项数据属性的 <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> 对象。</span><span class="sxs-lookup"><span data-stu-id="9f996-115">A <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> object that encapsulates the custom report item data properties specified at design time.</span></span>|  
|`CustomProperties`|<span data-ttu-id="9f996-116">自定义报表项的自定义属性的集合。</span><span class="sxs-lookup"><span data-stu-id="9f996-116">A collection of custom properties for the custom report item.</span></span>|  
|`Height`|<span data-ttu-id="9f996-117">自定义报表项控件的高度。</span><span class="sxs-lookup"><span data-stu-id="9f996-117">The height of the custom report item control.</span></span>|  
|`Width`|<span data-ttu-id="9f996-118">自定义报表项控件的宽度。</span><span class="sxs-lookup"><span data-stu-id="9f996-118">The width of the custom report item control.</span></span>|  
|`Report`|<span data-ttu-id="9f996-119">报表级别属性（如报表中数据集的列表）的容器。</span><span class="sxs-lookup"><span data-stu-id="9f996-119">A container for the report-level properties, such as the list of datasets in the report.</span></span>|  
|`AltReportItem`|<span data-ttu-id="9f996-120">备用报表项对象，可在不支持自定义报表项运行时控件时使用。</span><span class="sxs-lookup"><span data-stu-id="9f996-120">The alternate report item object, to be used where the custom report item run-time control is not supported.</span></span>|  
|`Style`|<span data-ttu-id="9f996-121">自定义报表项的样式属性。</span><span class="sxs-lookup"><span data-stu-id="9f996-121">The style properties for the custom report item.</span></span>|  
|`Adornment`|<span data-ttu-id="9f996-122">用于对控件进行交互式编辑的修饰窗口。</span><span class="sxs-lookup"><span data-stu-id="9f996-122">An adornment window used for interactive editing of the control.</span></span>|  
|`Site`|<span data-ttu-id="9f996-123">组件的 `ISite`。</span><span class="sxs-lookup"><span data-stu-id="9f996-123">The `ISite` of the component.</span></span>|  
|`DesignerVerbCollection`|<span data-ttu-id="9f996-124">控件快捷菜单的自定义谓词的数组。</span><span class="sxs-lookup"><span data-stu-id="9f996-124">An array of custom verbs for the control's shortcut menu.</span></span>|  
  
#### <a name="public-methods"></a><span data-ttu-id="9f996-125">公共方法</span><span class="sxs-lookup"><span data-stu-id="9f996-125">Public Methods</span></span>  
  
|||  
|-|-|  
|`BeginEdit`|<span data-ttu-id="9f996-126">激活控件的交互式编辑。</span><span class="sxs-lookup"><span data-stu-id="9f996-126">Activates interactive editing for the control.</span></span>|  
|`DoDefaultAction`|<span data-ttu-id="9f996-127">在响应对控件的双击或在控件上按 Return 键时调用。</span><span class="sxs-lookup"><span data-stu-id="9f996-127">Called in response to double-clicking or pressing Return on the control.</span></span>|  
|`EndEdit`|<span data-ttu-id="9f996-128">停用控件的交互式编辑。</span><span class="sxs-lookup"><span data-stu-id="9f996-128">Deactivates interactive editing for the control.</span></span>|  
|`GetService`|<span data-ttu-id="9f996-129">返回一个表示服务的对象。</span><span class="sxs-lookup"><span data-stu-id="9f996-129">Returns an object which represents a service.</span></span>|  
|`InitializeNewComponent`|<span data-ttu-id="9f996-130">当创建新的自定义报表项时调用。</span><span class="sxs-lookup"><span data-stu-id="9f996-130">Called when a new custom report item is created.</span></span>|  
|`Invalidate`|<span data-ttu-id="9f996-131">重新绘制控件的整个图面。</span><span class="sxs-lookup"><span data-stu-id="9f996-131">Repaints the entire surface of the control.</span></span>|  
|`OnDragEnter`<br /><br /> `OnDragDrop`|<span data-ttu-id="9f996-132">当将对象拖到控件上时调用。</span><span class="sxs-lookup"><span data-stu-id="9f996-132">Called when an object is dragged onto the control.</span></span>|  
|`OnPaint`|<span data-ttu-id="9f996-133">当响应 `Paint` 事件时调用。</span><span class="sxs-lookup"><span data-stu-id="9f996-133">Called in response to the `Paint` event.</span></span>|  
  
### <a name="microsoftreportdesignercustomreportitemattribute"></a><span data-ttu-id="9f996-134">Microsoft.ReportDesigner.CustomReportItemAttribute</span><span class="sxs-lookup"><span data-stu-id="9f996-134">Microsoft.ReportDesigner.CustomReportItemAttribute</span></span>  
 <span data-ttu-id="9f996-135">这是用于标识自定义报表项的类型的属性。</span><span class="sxs-lookup"><span data-stu-id="9f996-135">This is the attribute used to identify the type of the custom report item.</span></span> <span data-ttu-id="9f996-136">该名称必须与 `Name` `ReportItem` 报表设计器配置文件中元素的 <> 属性的值相匹配。</span><span class="sxs-lookup"><span data-stu-id="9f996-136">The name must match the value of the <`Name`> attribute of the `ReportItem` element in the Report Designer configuration file.</span></span>  
  
#### <a name="public-methods"></a><span data-ttu-id="9f996-137">公共方法</span><span class="sxs-lookup"><span data-stu-id="9f996-137">Public Methods</span></span>  
  
|||  
|-|-|  
|`CustomReportItemAttribute`|<span data-ttu-id="9f996-138">构造 CustomReportItemAttribute 对象。</span><span class="sxs-lookup"><span data-stu-id="9f996-138">Constructs the CustomReportItemAttribute object.</span></span>|  
  
### <a name="microsoftreportdesignerlocalizednameattribute"></a><span data-ttu-id="9f996-139">Microsoft.ReportDesigner.LocalizedNameAttribute</span><span class="sxs-lookup"><span data-stu-id="9f996-139">Microsoft.ReportDesigner.LocalizedNameAttribute</span></span>  
 <span data-ttu-id="9f996-140">这是用于指定自定义报表项设计器所使用的显示名称的属性。</span><span class="sxs-lookup"><span data-stu-id="9f996-140">This is the attribute used to specify display name to use for the custom report item designer.</span></span>  
  
#### <a name="public-methods"></a><span data-ttu-id="9f996-141">公共方法</span><span class="sxs-lookup"><span data-stu-id="9f996-141">Public Methods</span></span>  
  
|||  
|-|-|  
|`LocalizedNameAttribute`|<span data-ttu-id="9f996-142">构造 LocalizedNameAttribute 对象。</span><span class="sxs-lookup"><span data-stu-id="9f996-142">Constructs the LocalizedNameAttribute object.</span></span>|  
  
### <a name="microsoftreportdesigneradornment"></a><span data-ttu-id="9f996-143">Microsoft.ReportDesigner.Adornment</span><span class="sxs-lookup"><span data-stu-id="9f996-143">Microsoft.ReportDesigner.Adornment</span></span>  
 <span data-ttu-id="9f996-144">自定义报表项设计时组件使用 `Adornment` 类来提供设计图面主矩形之外的区域。</span><span class="sxs-lookup"><span data-stu-id="9f996-144">The `Adornment` class is used by the custom report item design-time component to provide areas outside of the main rectangle of the design surface.</span></span> <span data-ttu-id="9f996-145">这些区域可用来处理用户界面事件，如鼠标单击和拖放操作。</span><span class="sxs-lookup"><span data-stu-id="9f996-145">These areas can handle user interface events, such as mouse clicks and drag-and-drop operations.</span></span>  
  
#### <a name="public-methods"></a><span data-ttu-id="9f996-146">公共方法</span><span class="sxs-lookup"><span data-stu-id="9f996-146">Public Methods</span></span>  
  
|||  
|-|-|  
|`OnShow`|<span data-ttu-id="9f996-147">当激活 `Adornment` 时调用。</span><span class="sxs-lookup"><span data-stu-id="9f996-147">Called when the `Adornment` is activated.</span></span>|  
|`OnHide`|<span data-ttu-id="9f996-148">当停用 `Adornment` 时调用。</span><span class="sxs-lookup"><span data-stu-id="9f996-148">Called when the `Adornment` is deactivated.</span></span>|  
|`Paint`|<span data-ttu-id="9f996-149">当响应 `Paint` 事件时调用。</span><span class="sxs-lookup"><span data-stu-id="9f996-149">Called in response to the `Paint` event.</span></span>|  
|`OnDragEnter`<br /><br /> `OnDragOver`<br /><br /> `OnDragLeave`<br /><br /> `OnDragDrop`|<span data-ttu-id="9f996-150">当将对象拖入 `Adornment` 时调用。</span><span class="sxs-lookup"><span data-stu-id="9f996-150">Called when an object is dragged into the `Adornment`.</span></span>|  
  
### <a name="microsoftreportdesigneradornerservice"></a><span data-ttu-id="9f996-151">Microsoft.ReportDesigner.AdornerService</span><span class="sxs-lookup"><span data-stu-id="9f996-151">Microsoft.ReportDesigner.AdornerService</span></span>  
 <span data-ttu-id="9f996-152">此类用于提供自定义报表项所使用的一组显示服务，以支持自定义报表项设计时组件中的 `Adornment` 对象。</span><span class="sxs-lookup"><span data-stu-id="9f996-152">This class is used to provide a collection of display services used by the custom report item to support `Adornment` objects for the custom report item design-time component.</span></span>  
  
#### <a name="public-properties"></a><span data-ttu-id="9f996-153">公共属性</span><span class="sxs-lookup"><span data-stu-id="9f996-153">Public Properties</span></span>  
  
|||  
|-|-|  
|`AdornerWindowBounds`|<span data-ttu-id="9f996-154">装饰器窗口的界限。</span><span class="sxs-lookup"><span data-stu-id="9f996-154">The bounds of the Adorner window.</span></span>|  
|`AdornerWindowRegion`|<span data-ttu-id="9f996-155">装饰器窗口的区域。</span><span class="sxs-lookup"><span data-stu-id="9f996-155">The region of the Adorner window.</span></span>|  
|`AdornerWindowGraphics`|<span data-ttu-id="9f996-156">装饰器窗口的图形上下文。</span><span class="sxs-lookup"><span data-stu-id="9f996-156">A graphics context for the Adorner window.</span></span>|  
  
#### <a name="public-methods"></a><span data-ttu-id="9f996-157">公共方法</span><span class="sxs-lookup"><span data-stu-id="9f996-157">Public Methods</span></span>  
  
|||  
|-|-|  
|`ComponentRectInDesignerFrame`|<span data-ttu-id="9f996-158">返回转换为设计器框架坐标的组件的边界。</span><span class="sxs-lookup"><span data-stu-id="9f996-158">Returns the bounds of the component translated into designer frame coordinates.</span></span>|  
|`InvalidateAdorner`|<span data-ttu-id="9f996-159">使装饰器窗口失效。</span><span class="sxs-lookup"><span data-stu-id="9f996-159">Invalidates the Adorner window.</span></span>|  
|`PointToAdorner`|<span data-ttu-id="9f996-160">返回转换为装饰器窗口坐标的屏幕坐标中的点。</span><span class="sxs-lookup"><span data-stu-id="9f996-160">Returns a point in screen coordinates translated to Adorner window coordinates.</span></span>|  
  
### <a name="microsoftreportdesignerexpressioneditor"></a><span data-ttu-id="9f996-161">Microsoft.ReportDesigner.ExpressionEditor</span><span class="sxs-lookup"><span data-stu-id="9f996-161">Microsoft.ReportDesigner.ExpressionEditor</span></span>  
 <span data-ttu-id="9f996-162">可以从自定义报表项设计时控件使用此类调用表达式编辑器。</span><span class="sxs-lookup"><span data-stu-id="9f996-162">This class can be used from your custom report item design-time control to invoke the Expression Editor.</span></span>  
  
#### <a name="public-methods"></a><span data-ttu-id="9f996-163">公共方法</span><span class="sxs-lookup"><span data-stu-id="9f996-163">Public Methods</span></span>  
  
|||  
|-|-|  
|`EditValue`|<span data-ttu-id="9f996-164">调用以给定的对象值初始化的表达式编辑器。</span><span class="sxs-lookup"><span data-stu-id="9f996-164">Invokes the Expression Editor, initialized with the given object value.</span></span>|  
  
### <a name="microsoftreportdesignerifieldsdataobject"></a><span data-ttu-id="9f996-165">Microsoft.ReportDesigner.IFieldsDataObject</span><span class="sxs-lookup"><span data-stu-id="9f996-165">Microsoft.ReportDesigner.IFieldsDataObject</span></span>  
 <span data-ttu-id="9f996-166">此类是 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 字段的集合，用于支持设计环境中的拖放事件。</span><span class="sxs-lookup"><span data-stu-id="9f996-166">This class is a collection of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fields, and is used to support drag-and-drop events in the design environment.</span></span> <span data-ttu-id="9f996-167">继承自 `IReportItemDataObject`。</span><span class="sxs-lookup"><span data-stu-id="9f996-167">Inherits from `IReportItemDataObject`.</span></span>  
  
#### <a name="public-properties"></a><span data-ttu-id="9f996-168">公共属性</span><span class="sxs-lookup"><span data-stu-id="9f996-168">Public Properties</span></span>  
  
|||  
|-|-|  
|`DataSetName`|<span data-ttu-id="9f996-169">包含要拖放的字段的数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="9f996-169">The name of the dataset containing the fields to be dropped.</span></span>|  
|`Fields`|<span data-ttu-id="9f996-170">要拖放的字段 (`Microsoft.ReportDesigner.Field`) 的集合。</span><span class="sxs-lookup"><span data-stu-id="9f996-170">The collection of fields (`Microsoft.ReportDesigner.Field`) to be dropped.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f996-171">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9f996-171">See Also</span></span>  
 <span data-ttu-id="9f996-172">[&#40;SSRS&#41;的报表定义语言](../reports/report-definition-language-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9f996-172">[Report Definition Language &#40;SSRS&#41;](../reports/report-definition-language-ssrs.md) </span></span>  
 <span data-ttu-id="9f996-173">[创建自定义报表项运行时组件](creating-a-custom-report-item-run-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="9f996-173">[Creating a Custom Report Item Run-Time Component](creating-a-custom-report-item-run-time-component.md) </span></span>  
 [<span data-ttu-id="9f996-174">创建自定义报表项设计时组件</span><span class="sxs-lookup"><span data-stu-id="9f996-174">Creating a Custom Report Item Design-Time Component</span></span>](creating-a-custom-report-item-design-time-component.md)  
  
  
