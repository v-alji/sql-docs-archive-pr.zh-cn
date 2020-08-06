---
title: 指定一个图像作为仪表上的指针 (报表生成器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9d73b3c3-a068-4868-a2be-0cd261b6e92b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c694cdb90fb668c43eb7e9971bba967bad8dd9cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691047"
---
# <a name="specify-an-image-as-a-pointer-on-a-gauge-report-builder-and-ssrs"></a><span data-ttu-id="c810f-102">指定图像作为仪表的指针（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="c810f-102">Specify an Image as a Pointer on a Gauge (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c810f-103">仪表包含三个可用于自定义指针外观的内置样式。</span><span class="sxs-lookup"><span data-stu-id="c810f-103">The gauge contains three built-in styles that can be used to customize the appearance of the pointer.</span></span> <span data-ttu-id="c810f-104">对于径向仪表，内置样式为：针、标记和图条。</span><span class="sxs-lookup"><span data-stu-id="c810f-104">For a radial gauge, the built in styles are: Needle, Marker and Bar.</span></span> <span data-ttu-id="c810f-105">对于线性仪表，内置样式为：标记、图条和温度计。</span><span class="sxs-lookup"><span data-stu-id="c810f-105">For a linear gauge, the built-in styles are Marker, Bar, and Thermometer.</span></span> <span data-ttu-id="c810f-106">如果需要一个唯一指针，则用户可以创建一个图像并指定其作为全功能指针。</span><span class="sxs-lookup"><span data-stu-id="c810f-106">If a unique pointer is required, the user can create and specify an image which can be used as a fully functional pointer.</span></span>  
  
 <span data-ttu-id="c810f-107">为指针指定图像时，图像必须满足以下规范：</span><span class="sxs-lookup"><span data-stu-id="c810f-107">When you are specifying an image for the pointer, your image must have the following specifications:</span></span>  
  
-   <span data-ttu-id="c810f-108">指针的原点或旋转中心必须位于图像的顶部。</span><span class="sxs-lookup"><span data-stu-id="c810f-108">The origin of the pointer, or center of rotation, must be at the top of the image.</span></span>  
  
-   <span data-ttu-id="c810f-109">指针的末端必须指向下方。</span><span class="sxs-lookup"><span data-stu-id="c810f-109">The end of the pointer must be pointing down.</span></span>  
  
 <span data-ttu-id="c810f-110">由于指针形状不规则，所以您需要指定透明色，以隐藏不必要的图像部分。</span><span class="sxs-lookup"><span data-stu-id="c810f-110">Since the pointer is an irregular shape, you will need to specify a transparency color to hide the unnecessary portions of the image.</span></span> <span data-ttu-id="c810f-111">请考虑使用通常仪表中不显示的颜色作为透明色，因为所指定的颜色不显示在仪表中。</span><span class="sxs-lookup"><span data-stu-id="c810f-111">Consider using a color that would not normally be shown on the gauge as the transparency color, since the colors specified will not appear on the gauge.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-an-image-as-a-pointer-on-the-gauge"></a><span data-ttu-id="c810f-112">指定一个图像作为仪表上的指针</span><span class="sxs-lookup"><span data-stu-id="c810f-112">To specify an image as a pointer on the gauge</span></span>  
  
1.  <span data-ttu-id="c810f-113">在“设计”视图中，单击仪表指针。</span><span class="sxs-lookup"><span data-stu-id="c810f-113">In Design view, click the pointer of the gauge.</span></span>  
  
2.  <span data-ttu-id="c810f-114"> (可选) 如果仪表上没有指针，请右键单击仪表，然后选择 "**添加指针**"。</span><span class="sxs-lookup"><span data-stu-id="c810f-114">(Optional) If no pointer exists on the gauge, right-click on the gauge and select **Add Pointer**.</span></span> <span data-ttu-id="c810f-115">此时将会有一个指针添加到仪表上。</span><span class="sxs-lookup"><span data-stu-id="c810f-115">A pointer is added to the gauge.</span></span>  
  
3.  <span data-ttu-id="c810f-116">单击功能区上的 "**插入**" 选项卡，然后双击图像图标。</span><span class="sxs-lookup"><span data-stu-id="c810f-116">Click the **Insert** tab on the ribbon and double-click the image icon.</span></span> <span data-ttu-id="c810f-117">将打开“图像属性”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="c810f-117">The **Image Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="c810f-118">向报表添加图像。</span><span class="sxs-lookup"><span data-stu-id="c810f-118">Add an image to your report.</span></span> <span data-ttu-id="c810f-119">有关详细信息，请参阅[在报表中嵌入图像 &#40;报表生成器和 SSRS&#41;](report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c810f-119">For more information, see [Embed an Image in a Report &#40;Report Builder and SSRS&#41;](report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md).</span></span>  
  
5.  <span data-ttu-id="c810f-120">打开“属性”窗格。</span><span class="sxs-lookup"><span data-stu-id="c810f-120">Open the Properties pane.</span></span>  
  
6.  <span data-ttu-id="c810f-121">在设计图面上，单击该指针。</span><span class="sxs-lookup"><span data-stu-id="c810f-121">On the design surface, click on the pointer.</span></span> <span data-ttu-id="c810f-122">指针的属性将显示在“属性”窗格中。</span><span class="sxs-lookup"><span data-stu-id="c810f-122">The properties for the pointer are displayed in the Properties pane.</span></span>  
  
7.  <span data-ttu-id="c810f-123">展开 "PointerImage" 节点。</span><span class="sxs-lookup"><span data-stu-id="c810f-123">Expand the PointerImage node.</span></span>  
  
8.  <span data-ttu-id="c810f-124">在 "**源**" 中，从下拉列表中选择 "**嵌入**"。</span><span class="sxs-lookup"><span data-stu-id="c810f-124">In **Source**, select **Embedded** from the drop-down list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c810f-125">如果图像存储在数据库中或 Web 上，则可以为此属性指定适当的选项。</span><span class="sxs-lookup"><span data-stu-id="c810f-125">If your image is stored in the database or on the web, you can specify the appropriate option for this property.</span></span> <span data-ttu-id="c810f-126">有关详细信息，请参阅["图像属性" 对话框-"常规" &#40;报表生成器和 SSRS&#41;](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c810f-126">For more information, see [Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md).</span></span>  
  
9. <span data-ttu-id="c810f-127">在 "**值**" 中，从下拉列表中选择映像的名称。</span><span class="sxs-lookup"><span data-stu-id="c810f-127">In **Value**, select the name of your image from the drop-down list.</span></span>  
  
10. <span data-ttu-id="c810f-128">在**TransparentColor**中，选择要从图像中删除的颜色值。</span><span class="sxs-lookup"><span data-stu-id="c810f-128">In **TransparentColor**, pick a color value that you want to remove from the image.</span></span> <span data-ttu-id="c810f-129">这将使指针的外观无缝地融入仪表。</span><span class="sxs-lookup"><span data-stu-id="c810f-129">This will create a seamless appearance for the pointer in the gauge.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c810f-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c810f-130">See Also</span></span>  
 <span data-ttu-id="c810f-131">[设置仪表上的指针格式 &#40;报表生成器和 SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c810f-131">[Formatting Pointers on a Gauge &#40;Report Builder and SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c810f-132">[向报表添加仪表 &#40;报表生成器和 SSRS&#41;](report-design/add-a-gauge-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c810f-132">[Add a Gauge to a Report &#40;Report Builder and SSRS&#41;](report-design/add-a-gauge-to-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c810f-133">[设置线条、颜色和图像的格式 &#40;报表生成器和 SSRS&#41;](report-design/images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c810f-133">[Formatting Lines, Colors, and Images &#40;Report Builder and SSRS&#41;](report-design/images-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c810f-134">仪表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="c810f-134">Gauges &#40;Report Builder and SSRS&#41;</span></span>](report-design/gauges-report-builder-and-ssrs.md)  
  
  
