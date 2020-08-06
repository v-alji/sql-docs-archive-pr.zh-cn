---
title: "\"填充\" 对话框 (报表生成器和 SSRS) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.reportbody.fill.f1
- "10065"
- "10501"
- sql12.rtp.rptdesigner.shared.filldv.f1
- sql12.rtp.rptdesigner.rectangleproperties.fill.f1
- "10064"
- sql12.rtp.rptdesigner.textboxproperties.fill.f1
- "10124"
ms.assetid: 93a91d02-d558-4a0e-8d17-3fdf21e208d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ae7f2b05d4d108c77f1dcae9ce7fefe5073e2522
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587206"
---
# <a name="fill-dialog-box-report-builder-and-ssrs"></a><span data-ttu-id="dbad8-102">“填充”对话框（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="dbad8-102">Fill Dialog Box (Report Builder and SSRS)</span></span>
  <span data-ttu-id="dbad8-103">在 **“填充”** 选项卡上，您可以为数据区域或文本框中的单个或多个单元的背景指定颜色选项。</span><span class="sxs-lookup"><span data-stu-id="dbad8-103">On the **Fill** tab, you can specify color options for the background of a single cell or multiple cells within a data region or a text box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="dbad8-104">选项</span><span class="sxs-lookup"><span data-stu-id="dbad8-104">Options</span></span>  
 <span data-ttu-id="dbad8-105">**填充颜色**</span><span class="sxs-lookup"><span data-stu-id="dbad8-105">**Fill Color**</span></span>  
 <span data-ttu-id="dbad8-106">单击此颜色按钮可为矩形选择填充颜色。</span><span class="sxs-lookup"><span data-stu-id="dbad8-106">Click the color button to select a fill color for the rectangle.</span></span> <span data-ttu-id="dbad8-107">单击“表达式”_(fx)_ 按钮可编辑表达式，此表达式可以是 RGB 颜色的十六进制值，也可以是“表达式”对话框中提供的预定义的颜色名称之一。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="dbad8-107">Click the **Expression**_(fx)_ button to edit the expression, which can be a hexadecimal value for the RGB color or one of the predefined color names that are provided in the **Expression** dialog box.</span></span> <span data-ttu-id="dbad8-108">若要查看预定义的颜色的列表，请在 **“项”** 窗格中选择 **Web**。</span><span class="sxs-lookup"><span data-stu-id="dbad8-108">To see a list of predefined colors, in the **Item** pane, select **Web**.</span></span> <span data-ttu-id="dbad8-109">可在表达式文本窗格中键入 **“标题”** 窗格中列出的颜色名称。</span><span class="sxs-lookup"><span data-stu-id="dbad8-109">The color names listed in the **Title** pane can be typed into the expression text pane.</span></span> <span data-ttu-id="dbad8-110">键入颜色名称时请勿使用等号 (=) 或引号 ("")。</span><span class="sxs-lookup"><span data-stu-id="dbad8-110">Do not use an equal sign (=) or quotation marks ("") when typing the color name.</span></span>  
  
 <span data-ttu-id="dbad8-111">**选择图像源**</span><span class="sxs-lookup"><span data-stu-id="dbad8-111">**Select the image source**</span></span>  
 <span data-ttu-id="dbad8-112">指示图像的存储位置，以便在呈现报表时报表处理器能够显示它。</span><span class="sxs-lookup"><span data-stu-id="dbad8-112">Indicate where the image is stored so that when the report is rendered, the report processor can display it.</span></span>  
  
-   <span data-ttu-id="dbad8-113">**外部** 如果您希望此图像继续作为文件存在于报表服务器或 Web 服务器上，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="dbad8-113">**External** Choose this option when you want the image to continue to exist as a file on a report server or Web server.</span></span>  
  
-   <span data-ttu-id="dbad8-114">**嵌入** 如果您希望将此图像嵌入到报表中，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="dbad8-114">**Embedded** Choose this option when you want to embed the image into the report.</span></span>  
  
-   <span data-ttu-id="dbad8-115">**数据库** 如果您希望包括表示您要包含在报表中的图像的数据库字段名称，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="dbad8-115">**Database** Choose this option when you want to include a database field name that represents the images that you want to include in your report.</span></span>  
  
 <span data-ttu-id="dbad8-116">**使用此图像**</span><span class="sxs-lookup"><span data-stu-id="dbad8-116">**Use this image**</span></span>  
 <span data-ttu-id="dbad8-117">选择“嵌入”\*\*\*\* 或“外部”\*\*\*\* 选项时，便会出现此选项。</span><span class="sxs-lookup"><span data-stu-id="dbad8-117">This option appears when you select the **Embedded** or **External** option.</span></span>  
  
 <span data-ttu-id="dbad8-118">如果您要嵌入相应图像，请从下拉列表中选择您要添加到报表中的图片。</span><span class="sxs-lookup"><span data-stu-id="dbad8-118">If you are embedding the image, choose the picture that you want to add to the report from the drop-down list.</span></span> <span data-ttu-id="dbad8-119">单击“导入”可将图像添加到下拉列表中。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="dbad8-119">Click **Import** to add the image to the drop-down list.</span></span> <span data-ttu-id="dbad8-120">如果向“数据”窗格添加了一张图像，则可以通过如下方法选择此图像：选择“嵌入”，然后从下拉列表中选择此图像。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="dbad8-120">If you added an image to the **Data** pane, you can select that image by choosing **Embedded** and then selecting the image from the drop-down list.</span></span>  
  
 <span data-ttu-id="dbad8-121">如果您选择 **“外部”** 选项，请键入相应图像的 URL。</span><span class="sxs-lookup"><span data-stu-id="dbad8-121">If you select the **External** option, type the URL of the image.</span></span> <span data-ttu-id="dbad8-122">对于发布到配置为纯模式的 Report Server 的报表，请使用完整路径或相对路径 (例如，http:// *\<servername>* /images/image1.jpg) 。</span><span class="sxs-lookup"><span data-stu-id="dbad8-122">For a report published to a report server configured for native mode, use a full or relative path (for example, http://*\<servername>*/images/image1.jpg).</span></span> <span data-ttu-id="dbad8-123">对于发布到在 SharePoint 集成模式下配置的 Report Server 的报表，请使用完全限定的 URL (例如 http:// *\<SharePointservername>/\<site>* /Documents/images/image1.jpg) 。</span><span class="sxs-lookup"><span data-stu-id="dbad8-123">For a report published to a report server configured in SharePoint integrated mode, use a fully qualified URL (for example, http://*\<SharePointservername>/\<site>*/Documents/images/image1.jpg).</span></span>  
  
 <span data-ttu-id="dbad8-124">**导入**</span><span class="sxs-lookup"><span data-stu-id="dbad8-124">**Import**</span></span>  
 <span data-ttu-id="dbad8-125">此选项在选择“嵌入”后可用。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="dbad8-125">Available when you select **Embedded**.</span></span> <span data-ttu-id="dbad8-126">单击此选项可以向“使用此图像”\*\*\*\* 下拉列表中添加图像。</span><span class="sxs-lookup"><span data-stu-id="dbad8-126">Click to add an image to the **Use this image** drop-down list.</span></span>  
  
 <span data-ttu-id="dbad8-127">**使用此字段**</span><span class="sxs-lookup"><span data-stu-id="dbad8-127">**Use this field**</span></span>  
 <span data-ttu-id="dbad8-128">此选项在选择“数据库”后可用。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="dbad8-128">Available when you select **Database**.</span></span> <span data-ttu-id="dbad8-129">请选择字段名称。</span><span class="sxs-lookup"><span data-stu-id="dbad8-129">Select the field name.</span></span>  
  
 <span data-ttu-id="dbad8-130">**使用此 MIME 类型**</span><span class="sxs-lookup"><span data-stu-id="dbad8-130">**Use this MIME type**</span></span>  
 <span data-ttu-id="dbad8-131">选择数据库中包含的图片的适当格式（例如，.bmp、.jpeg、.gif、.png 或 .x-png）。</span><span class="sxs-lookup"><span data-stu-id="dbad8-131">Choose the appropriate format of the pictures contained in the database (for example, .bmp, .jpeg, .gif, .png, or .x-png).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbad8-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dbad8-132">See Also</span></span>  
 <span data-ttu-id="dbad8-133">[&#40;报表生成器和 SSRS 的格式设置报表项&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dbad8-133">[Formatting Report Items &#40;Report Builder and SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="dbad8-134">[设置文本和占位符的格式 &#40;报表生成器和 SSRS&#41;](report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dbad8-134">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="dbad8-135">图像（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="dbad8-135">Images &#40;Report Builder and SSRS&#41;</span></span>](report-design/images-report-builder-and-ssrs.md)  
  
  
