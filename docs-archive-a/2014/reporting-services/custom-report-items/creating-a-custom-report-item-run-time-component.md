---
title: 创建自定义报表项运行时组件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, creating
ms.assetid: b3e15a4a-98f8-4dbb-b847-bbcb20327051
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 50c5c0211bc5cd1359af9d1493782bd9d96c2b3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577405"
---
# <a name="creating-a-custom-report-item-run-time-component"></a><span data-ttu-id="9b0b5-102">创建自定义报表项运行时组件</span><span class="sxs-lookup"><span data-stu-id="9b0b5-102">Creating a Custom Report Item Run-Time Component</span></span>
  <span data-ttu-id="9b0b5-103">自定义报表项运行时组件作为 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 使用任何符合 CLS 的语言的组件实现，由报表处理器在运行时调用。</span><span class="sxs-lookup"><span data-stu-id="9b0b5-103">The custom report item run-time component is implemented as a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] component using any CLS-compliant language, and is called by the report processor at run time.</span></span> <span data-ttu-id="9b0b5-104">可在设计环境下定义此类运行时组件的属性，方法为修改相应自定义报表项的对应设计时组件。</span><span class="sxs-lookup"><span data-stu-id="9b0b5-104">You define the properties for the run-time component in the design environment by modifying the custom report item's corresponding design-time component.</span></span>  

<!--
Replacing the following multiValue.....

ms.technology: 
  - "docset-sql-devref"
  - "reporting-services-native"

.....with the following single value.....

ms.technology: reporting-services
.

(GeneMi = MightyPen  ,  2019-04-20  ,  DevO= 1515083)
-->

 <span data-ttu-id="9b0b5-105">有关完全实现的自定义报表项的示例，请参阅 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)（SQL Server Reporting Services 产品示例）。</span><span class="sxs-lookup"><span data-stu-id="9b0b5-105">For a sample of a fully implemented custom report item, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="definition-and-instance-objects"></a><span data-ttu-id="9b0b5-106">定义和实例对象</span><span class="sxs-lookup"><span data-stu-id="9b0b5-106">Definition and Instance Objects</span></span>  
 <span data-ttu-id="9b0b5-107">实现自定义报表项之前，必须了解“定义对象”和“实例对象”之间的差别\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9b0b5-107">Before implementing a custom report item it is important to understand the difference between *definition objects* and *instance objects*.</span></span> <span data-ttu-id="9b0b5-108">定义对象用于提供自定义报表项的 RDL 表示形式，而实例对象是定义对象的已计算版本。</span><span class="sxs-lookup"><span data-stu-id="9b0b5-108">Definition objects provide the RDL representation of the custom report item whereas instance objects are the evaluated versions of the definition objects.</span></span> <span data-ttu-id="9b0b5-109">对于报表上的每一项，都只有一个定义对象。</span><span class="sxs-lookup"><span data-stu-id="9b0b5-109">There is only one definition object for each item on the report.</span></span> <span data-ttu-id="9b0b5-110">访问包含表达式的定义对象上的属性时，将获取未经计算的表达式字符串。</span><span class="sxs-lookup"><span data-stu-id="9b0b5-110">When accessing properties on a definition object that contain expressions, you will get the unevaluated expression string.</span></span> <span data-ttu-id="9b0b5-111">实例对象包含定义对象的已计算版本，与项的定义对象可以是一对多的关系。</span><span class="sxs-lookup"><span data-stu-id="9b0b5-111">Instance objects contain the evaluated versions of the definition objects and can have a one-to-many relationship with an item's definition object.</span></span> <span data-ttu-id="9b0b5-112">例如，如果报表有一个 <xref:Microsoft.ReportingServices.OnDemandReportRendering.Tablix> 数据区域，其详细信息行包含 <xref:Microsoft.ReportingServices.OnDemandReportRendering.CustomReportItem>，则在此数据区域中，将只有一个定义对象，但是每一行中都有一个实例对象。</span><span class="sxs-lookup"><span data-stu-id="9b0b5-112">For example, if a report has a <xref:Microsoft.ReportingServices.OnDemandReportRendering.Tablix> data region that contains a <xref:Microsoft.ReportingServices.OnDemandReportRendering.CustomReportItem> in a detail row, there will be only one definition object but there will be an instance object for each row in the data region.</span></span>  
  
## <a name="implementing-the-icustomreportitem-interface"></a><span data-ttu-id="9b0b5-113">实现 ICustomReportItem 接口</span><span class="sxs-lookup"><span data-stu-id="9b0b5-113">Implementing the ICustomReportItem Interface</span></span>  
 <span data-ttu-id="9b0b5-114">若要创建 `CustomReportItem` 运行时组件，则需要实现 Microsoft.ReportingServices.ProcessingCore.dll 中定义的 <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem> 接口：</span><span class="sxs-lookup"><span data-stu-id="9b0b5-114">To create a `CustomReportItem` run-time component you will need to implement the <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem> interface that is defined in the Microsoft.ReportingServices.ProcessingCore.dll:</span></span>  
  
```csharp  
namespace Microsoft.ReportingServices.OnDemandReportRendering  
{  
    public interface ICustomReportItem  
    {  
        void GenerateReportItemDefinition(CustomReportItem customReportItem);  
void EvaluateReportItemInstance(CustomReportItem customReportItem);  
    }  
}  
```  
  
 <span data-ttu-id="9b0b5-115">实现 <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem> 接口后，将为您生成两个方法存根：<xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.GenerateReportItemDefinition%2A> 和 <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.EvaluateReportItemInstance%2A>。</span><span class="sxs-lookup"><span data-stu-id="9b0b5-115">After you have implemented the <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem> interface, two method stubs will be generated for you: <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.GenerateReportItemDefinition%2A> and <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.EvaluateReportItemInstance%2A>.</span></span> <span data-ttu-id="9b0b5-116">先调用的是 <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.GenerateReportItemDefinition%2A> 方法，该方法用于设置定义属性和创建 <xref:Microsoft.ReportingServices.OnDemandReportRendering.Image> 对象，后者将包含用于呈现相应项的定义属性和实例属性。</span><span class="sxs-lookup"><span data-stu-id="9b0b5-116">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.GenerateReportItemDefinition%2A> method is called first and is used for setting definition properties and creating the <xref:Microsoft.ReportingServices.OnDemandReportRendering.Image> object that will contain both the definition and instance properties that are used for rendering the item.</span></span> <span data-ttu-id="9b0b5-117"><xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.EvaluateReportItemInstance%2A> 方法在定义对象被计算后调用，该方法可提供将用于呈现相应项的实例对象。</span><span class="sxs-lookup"><span data-stu-id="9b0b5-117">The <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.EvaluateReportItemInstance%2A> method is called after the definition objects have been evaluated, and it provides the instance objects that will be used for rendering the item.</span></span>  
  
 <span data-ttu-id="9b0b5-118">以下示例是用于将相应控件名称呈现为图像的自定义报表项的实现示例。</span><span class="sxs-lookup"><span data-stu-id="9b0b5-118">The following is an example implementation of a custom report item that renders the name of the control as an image.</span></span>  
  
```csharp  
namespace Microsoft.Samples.ReportingServices  
{  
    using System;  
    using System.Collections.Generic;  
    using System.Collections.Specialized;  
    using System.Drawing.Imaging;  
    using System.IO;  
    using System.Text;  
    using Microsoft.ReportingServices.OnDemandReportRendering;  
  
    public class PolygonsCustomReportItem : ICustomReportItem  
    {  
        #region ICustomReportItem Members  
  
        public void GenerateReportItemDefinition(CustomReportItem cri)  
        {  
            // Create the Image object that will be   
            // used to render the custom report item  
            cri.CreateCriImageDefinition();  
            Image polygonImage = (Image)cri.GeneratedReportItem;  
        }  
  
        public void EvaluateReportItemInstance(CustomReportItem cri)  
        {  
            // Get the Image definition  
            Image polygonImage = (Image)cri.GeneratedReportItem;  
  
            // Create the image for the custom report item  
            polygonImage.ImageInstance.ImageData = DrawImage(cri);  
        }  
  
        #endregion  
  
        /// <summary>  
        /// Creates an image of the CustomReportItem's name  
        /// </summary>  
        private byte[] DrawImage(CustomReportItem customReportItem)  
        {  
            int width = 1;          // pixels  
            int height = 1;         // pixels  
            int resolution = 75;    // dpi  
  
            System.Drawing.Bitmap bitmap = new System.Drawing.Bitmap(width, height);  
            bitmap.SetResolution(resolution, resolution);  
  
            System.Drawing.Graphics graphics = System.Drawing.Graphics.FromImage(bitmap);  
            graphics.PageUnit = System.Drawing.GraphicsUnit.Pixel;  
  
            // Get the Font for the Text  
            System.Drawing.Font font = new System.Drawing.Font(System.Drawing.FontFamily.GenericMonospace,  
                12, System.Drawing.FontStyle.Regular);  
  
            // Get the Brush for drawing the Text  
            System.Drawing.Brush brush = new System.Drawing.SolidBrush(System.Drawing.Color.LightGreen);  
  
            // Get the measurements for the image  
            System.Drawing.SizeF maxStringSize = graphics.MeasureString(customReportItem.Name, font);  
            width = (int)(maxStringSize.Width + 2 * font.GetHeight(resolution));  
            height = (int)(maxStringSize.Height + 2 * font.GetHeight(resolution));  
  
            bitmap.Dispose();  
            bitmap = new System.Drawing.Bitmap(width, height);  
            bitmap.SetResolution(resolution, resolution);  
  
            graphics.Dispose();  
            graphics = System.Drawing.Graphics.FromImage(bitmap);  
            graphics.PageUnit = System.Drawing.GraphicsUnit.Pixel;  
  
            // Draw the text  
            graphics.DrawString(customReportItem.Name, font, brush, font.GetHeight(resolution),   
                font.GetHeight(resolution));  
  
            // Create the byte array of the image data  
            MemoryStream memoryStream = new MemoryStream();  
            bitmap.Save(memoryStream, ImageFormat.Bmp);  
            memoryStream.Position = 0;  
            byte[] imageData = new byte[memoryStream.Length];  
            memoryStream.Read(imageData, 0, imageData.Length);  
  
            return imageData;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b0b5-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9b0b5-119">See Also</span></span>  
 <span data-ttu-id="9b0b5-120">[自定义报表项体系结构](custom-report-item-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="9b0b5-120">[Custom Report Item Architecture](custom-report-item-architecture.md) </span></span>  
 <span data-ttu-id="9b0b5-121">[创建自定义报表项设计时组件](creating-a-custom-report-item-design-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="9b0b5-121">[Creating a Custom Report Item Design-Time Component](creating-a-custom-report-item-design-time-component.md) </span></span>  
 <span data-ttu-id="9b0b5-122">[自定义报表项类库](custom-report-item-class-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="9b0b5-122">[Custom Report Item Class Libraries](custom-report-item-class-libraries.md) </span></span>  
 [<span data-ttu-id="9b0b5-123">如何：部署自定义报表项</span><span class="sxs-lookup"><span data-stu-id="9b0b5-123">How to: Deploy a Custom Report Item</span></span>](how-to-deploy-a-custom-report-item.md)  
  
  
