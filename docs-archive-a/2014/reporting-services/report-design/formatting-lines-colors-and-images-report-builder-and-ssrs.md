---
title: 设置线条、颜色和图像的格式（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.textboxproperties.border.f1
- "10502"
- "10094"
- sql12.rtp.rptdesigner.pictureproperties.border.f1
- "10063"
- sql12.rtp.rptdesigner.rectangleproperties.border.f1
- "10055"
- sql12.rtp.rptdesigner.subreportproperties.border.f1
- "10126"
- sql12.rtp.rptdesigner.shared.borderdv.f1
- "10066"
- sql12.rtp.rptdesigner.reportbody.border.f1
ms.assetid: 0f5f0d2a-9537-4152-b441-b40d7f04cf4c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 681ff6b46f692804aef5c7cbbc16e5abe99dbb2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682719"
---
# <a name="formatting-lines-colors-and-images-report-builder-and-ssrs"></a><span data-ttu-id="7e55b-102">设置线条、颜色和图像的格式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="7e55b-102">Formatting Lines, Colors, and Images (Report Builder and SSRS)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="7e55b-103">可以设置线条、颜色、数据区域、图像和其他报表项的格式。</span><span class="sxs-lookup"><span data-stu-id="7e55b-103">gives you the ability to format lines, colors, data regions, images, and other report items.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="borders-lines-and-gridlines"></a><span data-ttu-id="7e55b-104">边框、线条和网格线</span><span class="sxs-lookup"><span data-stu-id="7e55b-104">Borders, Lines and Gridlines</span></span>  
 <span data-ttu-id="7e55b-105">使用边框、线条和网格线可以直观地将页中的项关联在一起，并有助于报表读者轻松读取报表的内容。</span><span class="sxs-lookup"><span data-stu-id="7e55b-105">Borders, lines, and gridlines can visually tie items together on the page and help your report readers easily read the contents of the report.</span></span> <span data-ttu-id="7e55b-106">通过使用预定义的边框样式，您可以快速地在文本框、文本框组或图像周围添加边框。</span><span class="sxs-lookup"><span data-stu-id="7e55b-106">Using the predefined border styles, you can quickly add a border around a text box, a group of text boxes, or an image.</span></span> <span data-ttu-id="7e55b-107">此外，还可以更改边框、线条和网格线的样式、宽度和颜色。</span><span class="sxs-lookup"><span data-stu-id="7e55b-107">In addition, you can change the style, width, and color for the borders, lines, and gridlines.</span></span> <span data-ttu-id="7e55b-108">边框通常添加在整个选定项的周围，或沿着项边缘的边框添加，例如，沿着文本框底部的边框。</span><span class="sxs-lookup"><span data-stu-id="7e55b-108">Borders are added around the entire item selected or around a border along an edge of the item, for example, a border along the bottom of a text box.</span></span>  
  
 <span data-ttu-id="7e55b-109">若要设置文本框、报表布局或图像周围的边框和网格线的格式，请使用报表项的 **“属性”** 对话框中的 **“边框”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="7e55b-109">To format borders and gridlines in a text box, report layout, or around an image, use the **Border** tab of the report item's **Properties** dialog box.</span></span> <span data-ttu-id="7e55b-110">例如，如果要在图像周围添加边框，请右键单击该图像然后在 **“图像属性”** 对话框中，单击 **“边框”** 。</span><span class="sxs-lookup"><span data-stu-id="7e55b-110">For example, if you want to add a border around an image, right-click the image and then in the **Image Properties** dialog box, click **Border**.</span></span>  
  
 <span data-ttu-id="7e55b-111">除了标准边框外，还可以对图表应用其他边框。</span><span class="sxs-lookup"><span data-stu-id="7e55b-111">In addition to the standard border frames, additional border frames can be applied to charts.</span></span> <span data-ttu-id="7e55b-112">有关详细信息，请参阅[向图表添加边框（报表生成器和 SSRS）](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7e55b-112">For more information, see [Add a Border Frame to a Chart &#40;Report Builder and SSRS&#41;](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="7e55b-113">也可将边框添加到报表自身中。</span><span class="sxs-lookup"><span data-stu-id="7e55b-113">You can also add a border to the report itself.</span></span> <span data-ttu-id="7e55b-114">有关详细信息，请参阅 [向报表添加边框（报表生成器和 SSRS）](add-a-border-to-a-report-report-builder-and-ssrs.md)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="7e55b-114">For more information, see [Add a Border to a Report &#40;Report Builder and SSRS&#41;](add-a-border-to-a-report-report-builder-and-ssrs.md).</span></span>  
  
## <a name="applying-background-colors"></a><span data-ttu-id="7e55b-115">应用背景色</span><span class="sxs-lookup"><span data-stu-id="7e55b-115">Applying Background Colors</span></span>  
 <span data-ttu-id="7e55b-116">可以将纯色添加到整个报表或报表内文本框的背景中，也可以添加到数据区域内的单元或单元组。</span><span class="sxs-lookup"><span data-stu-id="7e55b-116">A solid color can be added to the background of the entire report, a text box within the report, or to a cell or group of cells within a data region.</span></span> <span data-ttu-id="7e55b-117">默认情况下，背景色为白色；不过，您可以从报表项中 **“属性”** 对话框的 **“填充”** 选项卡中选择颜色。</span><span class="sxs-lookup"><span data-stu-id="7e55b-117">By default, the background color is white; however, you can select a color from the **Fill** tab of the report item's **Properties** dialog box.</span></span> <span data-ttu-id="7e55b-118">例如，如果要更改文本框的背景色，请右键单击该文本框，然后选择 **“文本框属性”** 。</span><span class="sxs-lookup"><span data-stu-id="7e55b-118">For example, if you want to change the background color of a text box, right-click the text box and select **Text Box Properties**.</span></span> <span data-ttu-id="7e55b-119">单击 **“填充”** ，然后选择需要的颜色。</span><span class="sxs-lookup"><span data-stu-id="7e55b-119">Click **Fill** and then select the color you want.</span></span> <span data-ttu-id="7e55b-120">在此对话框中，可以为所选项选择背景色，也可以添加背景中显示的图像。</span><span class="sxs-lookup"><span data-stu-id="7e55b-120">In this dialog box, you can select a background color for the selected item or you can add an image that appears in the background.</span></span>  
  
 <span data-ttu-id="7e55b-121">使用图表时，还可以指定背景色的渐变样式和图案样式。</span><span class="sxs-lookup"><span data-stu-id="7e55b-121">When you use the chart, you can also specify gradients and pattern styles for background colors.</span></span> <span data-ttu-id="7e55b-122">有关详细信息，请参阅[设置图表格式（报表生成器和 SSRS）](formatting-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7e55b-122">For more information, see [Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md).</span></span>  
  
## <a name="using-images-as-formatting"></a><span data-ttu-id="7e55b-123">使用图像作为格式</span><span class="sxs-lookup"><span data-stu-id="7e55b-123">Using Images as Formatting</span></span>  
 <span data-ttu-id="7e55b-124">可以向数据区域添加包含图像的字段。</span><span class="sxs-lookup"><span data-stu-id="7e55b-124">Fields that contain images can be added to a data region.</span></span> <span data-ttu-id="7e55b-125">如果使用图像字段，则运行报表时将在报表中显示图像。</span><span class="sxs-lookup"><span data-stu-id="7e55b-125">If you use an image field, the images appear in the report with the report is run.</span></span>  
  
 <span data-ttu-id="7e55b-126">还可以将图像（如徽标）添加到报表的背景中，或添加到矩形、文本框、表、矩阵或某些图表部件中，或添加到表体和页部分。</span><span class="sxs-lookup"><span data-stu-id="7e55b-126">You can also add images such as logos to the background of your report or to a rectangle, text box, table, matrix, or some parts of a chart, or to the body and page sections of a report.</span></span> <span data-ttu-id="7e55b-127">有关详细信息，请参阅[图像（报表生成器和 SSRS）](images-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7e55b-127">For more information, see [Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e55b-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7e55b-128">See Also</span></span>  
 <span data-ttu-id="7e55b-129">[设置文本和占位符的格式（报表生成器和 SSRS）](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7e55b-129">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7e55b-130">[设置数字和日期格式（报表生成器和 SSRS）](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7e55b-130">[Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7e55b-131">[设置文本框中文本的格式（报表生成器和 SSRS）](format-text-in-a-text-box-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7e55b-131">[Format Text in a Text Box &#40;Report Builder and SSRS&#41;](format-text-in-a-text-box-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7e55b-132">“填充”对话框（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="7e55b-132">Fill Dialog Box &#40;Report Builder and SSRS&#41;</span></span>](../fill-dialog-box-report-builder-and-ssrs.md)  
  
  
