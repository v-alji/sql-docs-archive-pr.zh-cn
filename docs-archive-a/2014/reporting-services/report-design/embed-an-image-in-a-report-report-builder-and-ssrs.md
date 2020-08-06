---
title: 在报表中嵌入图像（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.embeddedimages.f1
- "10060"
ms.assetid: aed77345-5eeb-41f0-96c9-db6b4a11ec6f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6599092e0ef37dd9bbc15f4815c0315c77e7943b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682732"
---
# <a name="embed-an-image-in-a-report-report-builder-and-ssrs"></a><span data-ttu-id="c3ca0-102">在报表中嵌入图像（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="c3ca0-102">Embed an Image in a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c3ca0-103">报表中可以包含嵌入图像。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-103">A report can include an embedded image.</span></span> <span data-ttu-id="c3ca0-104">嵌入图像可确保图像对报表始终可用，但会影响报表定义（即定义报表的文件）的大小。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-104">Embedding an image ensures that the image is always available to a report, but can affect the size of the report definition, the file that defines the report.</span></span> <span data-ttu-id="c3ca0-105">报表中嵌入的图像在“报表数据”窗格中列出。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-105">The images embedded in a report are listed in the Report Data pane.</span></span>  
  
 <span data-ttu-id="c3ca0-106">您最好将某一图像嵌入到报表定义中，然后将该图像添加到设计图面。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-106">You might want to embed an image in the report definition before adding the image to the design surface.</span></span> <span data-ttu-id="c3ca0-107">有关详细信息，请参阅[添加背景图像（报表生成器和 SSRS）](add-a-background-image-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-107">For more information, see [Add a Background Image &#40;Report Builder and SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-embed-an-image-in-a-report"></a><span data-ttu-id="c3ca0-108">在报表中嵌入图像</span><span class="sxs-lookup"><span data-stu-id="c3ca0-108">To embed an image in a report</span></span>  
  
1.  <span data-ttu-id="c3ca0-109">在报表设计视图的 **“插入”** 选项卡上，单击 **“图像”** 。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-109">In report design view, on the **Insert** tab, click **Image**.</span></span>  
  
2.  <span data-ttu-id="c3ca0-110">在设计图面上，单击某个位置，然后拖动一个框调整到所需图像大小。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-110">On the design surface, click and then drag a box to the desired size of the image.</span></span>  
  
3.  <span data-ttu-id="c3ca0-111">在 **“图像属性”** 对话框的 **“常规”** 页中，在 **“名称”** 文本框中键入名称，或接受默认名称。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-111">In the **General** page of the **Image Properties** dialog box, type a name in the **Name** text box or accept the default.</span></span>  
  
4.  <span data-ttu-id="c3ca0-112">（可选）在“工具提示”文本框中，键入当用户将鼠标指针悬停在呈现报表中的图像上时所要显示的文本  。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-112">(Optional) In the **ToolTip** text box, type the text that you want to appear when the user hovers over the image in the rendered report.</span></span>  
  
5.  <span data-ttu-id="c3ca0-113">在 **“选择图像源”** 中，选择 **“嵌入”** 。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-113">In **Select the image source**, select **Embedded**.</span></span>  
  
6.  <span data-ttu-id="c3ca0-114">单击 **“使用此图像”** 文本框旁的 **“导入”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-114">Click the **Import** button next to the **Use this image** text box</span></span>  
  
7.  <span data-ttu-id="c3ca0-115">在 **“文件类型”** 中，选择图像文件类型，导航到该文件，然后单击 **“打开”** 。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-115">In **Files of type**, select the image file type, navigate to the file, and then click **Open**.</span></span>  
  
8.  <span data-ttu-id="c3ca0-116">在 **“图像属性”** 对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-116">In the **Image Properties** dialog box, click **OK**.</span></span>  
  
     <span data-ttu-id="c3ca0-117">图像将显示在您在设计图面上绘制的框中，并且文件显示在“报表数据”窗格中“图像”文件夹的下方。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-117">The image is displayed in the box you drew on the design surface, and the file is displayed under the Images folder in the Report Data pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c3ca0-118">MIME 类型（如 bmp）是导入图像时自动派生得来的。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-118">The MIME type (for example, bmp) is derived automatically when the image is imported.</span></span> <span data-ttu-id="c3ca0-119">若要更改 MIME 类型，请参见下一个过程。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-119">To change the MIME type, see the next procedure.</span></span>  
  
### <a name="optional-to-change-the-mime-type-of-an-imported-image"></a><span data-ttu-id="c3ca0-120">（可选）更改导入图像的 MIME 类型</span><span class="sxs-lookup"><span data-stu-id="c3ca0-120">(optional) To change the MIME type of an imported image</span></span>  
  
1.  <span data-ttu-id="c3ca0-121">在“设计”视图中打开报表。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-121">Open the report in Design view.</span></span>  
  
2.  <span data-ttu-id="c3ca0-122">在设计图面上选择图像。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-122">Select the image on the design surface.</span></span> <span data-ttu-id="c3ca0-123">**“属性”** 窗格将显示图像属性。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-123">The **Properties** pane displays the image properties.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c3ca0-124">如果“属性”窗格不可见，请单击“视图”选项卡上的“属性”   。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-124">If the Properties pane is not visible, on the **View** tab, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="c3ca0-125">在 **MIMEType** 属性旁边的文本框内单击，并从下拉列表中选择一个新 MIME 类型。</span><span class="sxs-lookup"><span data-stu-id="c3ca0-125">Click in the text box next to the **MIMEType** property and select a new MIME type from the drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ca0-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3ca0-126">See Also</span></span>  
 <span data-ttu-id="c3ca0-127">[图像（报表生成器和 SSRS）](images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c3ca0-127">[Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c3ca0-128">[添加数据绑定图像（报表生成器和 SSRS）](add-a-data-bound-image-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c3ca0-128">[Add a Data-Bound Image &#40;Report Builder and SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c3ca0-129">“图像属性”对话框 ->“常规”（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="c3ca0-129">Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
