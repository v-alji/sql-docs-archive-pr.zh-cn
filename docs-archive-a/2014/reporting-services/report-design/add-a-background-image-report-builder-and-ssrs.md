---
title: 添加背景图像（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c777fefb-8695-44a7-b5cd-a18c587583f2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d7bc15e1b063a73c463cdb1e7e99075af2a3dce9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692742"
---
# <a name="add-a-background-image-report-builder-and-ssrs"></a><span data-ttu-id="3137f-102">添加背景图像（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="3137f-102">Add a Background Image (Report Builder and SSRS)</span></span>
  <span data-ttu-id="3137f-103">您可以向报表项（如矩形、文本框、列表、矩阵、表和某些图表部件）或报表区域（如页眉、页脚或表体）添加背景图像。</span><span class="sxs-lookup"><span data-stu-id="3137f-103">You can add a background image to a report item such as a rectangle, text box, list, matrix, table, and some parts of a chart, or a report section such as the page header, page footer, or report body.</span></span> <span data-ttu-id="3137f-104">在“属性”窗格中，可以为报表设计图面上显示 **BackgroundImage** 的任何所选项定义背景图像。</span><span class="sxs-lookup"><span data-stu-id="3137f-104">You can define a background image for any selected item on the report design surface that displays **BackgroundImage** in the Properties pane.</span></span> <span data-ttu-id="3137f-105">与其他图像相似，背景图像可以是指向报表服务器上的图像的 URL、数据集字段的图像，也可以是报表定义中嵌入的图像。</span><span class="sxs-lookup"><span data-stu-id="3137f-105">Like other images, the background image can be a URL to an image on the report server, an image from a dataset field, or an image embedded in the report definition.</span></span> <span data-ttu-id="3137f-106">若要使用在报表中嵌入的图像，您必须首先向报表定义中添加该嵌入图像，然后才能向设计图面中添加该图像。</span><span class="sxs-lookup"><span data-stu-id="3137f-106">To use an image embedded in the report, you must first add the image to the report definition before you can add the image to the design surface.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-embed-an-image-in-the-report-definition"></a><span data-ttu-id="3137f-107">在报表定义中嵌入图像</span><span class="sxs-lookup"><span data-stu-id="3137f-107">To embed an image in the report definition</span></span>  
  
1.  <span data-ttu-id="3137f-108">在“报表数据”窗格中，右键单击“图像”节点，然后单击“添加图像”   。</span><span class="sxs-lookup"><span data-stu-id="3137f-108">In the Report Data pane, right-click the **Images** node, and then click **Add Image**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3137f-109">如果“报表数据”窗格不可见，请单击“视图”选项卡上的“报表数据”   。</span><span class="sxs-lookup"><span data-stu-id="3137f-109">If the Report Data pane is not visible, on the **View** tab, click **Report Data**.</span></span>  
  
2.  <span data-ttu-id="3137f-110">导航到您要在报表定义中嵌入的图像，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="3137f-110">Navigate to the image you want to embed in your report definition, and then click **OK**.</span></span>  
  
### <a name="to-add-a-background-image"></a><span data-ttu-id="3137f-111">添加背景图像</span><span class="sxs-lookup"><span data-stu-id="3137f-111">To add a background image</span></span>  
  
1.  <span data-ttu-id="3137f-112">在报表设计视图中，选择要向其添加背景图像的报表项。</span><span class="sxs-lookup"><span data-stu-id="3137f-112">In report design view, select the report item to which you want to add a background image.</span></span>  
  
2.  <span data-ttu-id="3137f-113">如果“属性”窗格不可见，请在 **“视图”** 选项卡上选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="3137f-113">If the Properties pane is not visible, on the **View** tab, select **Properties**.</span></span>  
  
3.  <span data-ttu-id="3137f-114">在“属性”窗口中，展开 **BackgroundImage**，然后执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="3137f-114">In the Properties pane, expand **BackgroundImage**, and then do the following:</span></span>  
  
    -   <span data-ttu-id="3137f-115">对于嵌入的图像：</span><span class="sxs-lookup"><span data-stu-id="3137f-115">For an embedded image:</span></span>  
  
         <span data-ttu-id="3137f-116">将 **“源”** 设置为 **“嵌入”** 。</span><span class="sxs-lookup"><span data-stu-id="3137f-116">Set **Source** to **Embedded**.</span></span>  
  
         <span data-ttu-id="3137f-117">将 **“值”** 设置为在报表中嵌入的图像的名称。</span><span class="sxs-lookup"><span data-stu-id="3137f-117">Set **Value** to the name of an image that is embedded in the report.</span></span>  
  
    -   <span data-ttu-id="3137f-118">对于外部图像：</span><span class="sxs-lookup"><span data-stu-id="3137f-118">For an external image:</span></span>  
  
         <span data-ttu-id="3137f-119">将 **“源”** 设置为 **“外部”** 。</span><span class="sxs-lookup"><span data-stu-id="3137f-119">Set **Source** to **External**.</span></span>  
  
         <span data-ttu-id="3137f-120">将 **“值”** 设置为指向图像的有效路径。</span><span class="sxs-lookup"><span data-stu-id="3137f-120">Set **Value** to a valid path to an image.</span></span> <span data-ttu-id="3137f-121">此图像可在本机模式或 SharePoint 集成模式下处于报表服务器上，或者可处于任何其他网站上。</span><span class="sxs-lookup"><span data-stu-id="3137f-121">This can be on a report server in native mode or SharePoint integrated mode, or it can be on any other Web site.</span></span> <span data-ttu-id="3137f-122">有关详细信息，请参阅[添加外部图像（报表生成器和 SSRS）](add-an-external-image-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="3137f-122">For more information, see [Add an External Image &#40;Report Builder and SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md).</span></span>  
  
    -   <span data-ttu-id="3137f-123">对于包含在报表项所连接的数据库的某个字段中的图像：</span><span class="sxs-lookup"><span data-stu-id="3137f-123">For an image is that is contained in a field in the database to which the report item is connected:</span></span>  
  
         <span data-ttu-id="3137f-124">将 **“源”** 设置为 **“数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="3137f-124">Set **Source** to **Database**.</span></span>  
  
         <span data-ttu-id="3137f-125">将 **“值”** 设置为报表数据集中某个字段的名称。</span><span class="sxs-lookup"><span data-stu-id="3137f-125">Set **Value** to the name of a field in the report dataset.</span></span> <span data-ttu-id="3137f-126">有关详细信息，请参阅[添加数据绑定图像（报表生成器和 SSRS）](add-a-data-bound-image-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="3137f-126">For more information, see [Add a Data-Bound Image &#40;Report Builder and SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md).</span></span>  
  
         <span data-ttu-id="3137f-127">对于 MIMEType 或文件格式，为图像选择适当的 MIME 类型，如 .bmp  。</span><span class="sxs-lookup"><span data-stu-id="3137f-127">For **MIMEType**, or file format, select the appropriate MIME type for the image-for example, .bmp.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="3137f-128">仅当 **Source** 属性设置为 **Database**时，MIMEType 才适用。</span><span class="sxs-lookup"><span data-stu-id="3137f-128">MIMEType applies only if the **Source** property is set to **Database**.</span></span> <span data-ttu-id="3137f-129">如果将 **Source** 属性设置为 **External** 或 **Embedded**，则忽略 **MIMEType** 的值。</span><span class="sxs-lookup"><span data-stu-id="3137f-129">If the **Source** property is set to **External** or **Embedded**, the value of **MIMEType** is ignored.</span></span>  
  
    -   <span data-ttu-id="3137f-130">对于 **BackgroundRepeat**，选择一个表达式，再选择 **Default**、 **Repeat**、 **RepeatX**、 **RepeatY**或 **Clip**。</span><span class="sxs-lookup"><span data-stu-id="3137f-130">For **BackgroundRepeat**, select an expression, **Default**, **Repeat**, **RepeatX**, or **RepeatY**, or **Clip**.</span></span>  
  
         <span data-ttu-id="3137f-131">对于图表中的背景图像， **BackgroundRepeat** 可设置为 **Default**、 **Repeat**、 **Fit**和 **Clip**，但不可设置为 **RepeatX** 或 **RepeatY**。</span><span class="sxs-lookup"><span data-stu-id="3137f-131">For background images in a chart, **BackgroundRepeat** can be set to **Default**, **Repeat**, **Fit**, and **Clip**, but not **RepeatX** or **RepeatY**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3137f-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3137f-132">See Also</span></span>  
 <span data-ttu-id="3137f-133">[图像（报表生成器和 SSRS）](images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3137f-133">[Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="3137f-134">“图像属性”对话框 ->“常规”（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="3137f-134">Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
