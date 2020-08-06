---
title: 更改指示器图标和指示器集（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8a056adf-4473-473d-9b0c-314675af7bfd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 398d21319ab6da22f2b10c3607baf8f110d6e65b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692261"
---
# <a name="change-indicator-icons-and-indicator-sets-report-builder-and-ssrs"></a><span data-ttu-id="bad4b-102">更改指示器图标和指示器集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="bad4b-102">Change Indicator Icons and Indicator Sets (Report Builder and SSRS)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="bad4b-103">提供预先配置的指示器集，这可能不会始终有效地描述您的数据，并且在传递的报表中可以正常工作。</span><span class="sxs-lookup"><span data-stu-id="bad4b-103">provides preconfigured indicators sets, which might not always depict your data effectively and work well in the delivered report.</span></span> <span data-ttu-id="bad4b-104">本主题提供的过程介绍如何更改指示器图标的外观，以及如何更改指示器集以便包括不同的指示器图标或者更多或更少的指示器图标。</span><span class="sxs-lookup"><span data-stu-id="bad4b-104">This topic provides procedures to change the appearance of indicator icons and change the indicator sets to include different, more, or fewer indicator icons.</span></span>  
  
 <span data-ttu-id="bad4b-105">可以通过使用表达式设置颜色之类的选项。</span><span class="sxs-lookup"><span data-stu-id="bad4b-105">Options such as colors can be set by using expressions.</span></span> <span data-ttu-id="bad4b-106">有关详细信息，请参阅[表达式（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="bad4b-106">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-color-of-an-indicator-icon"></a><span data-ttu-id="bad4b-107">更改指示器图标的颜色</span><span class="sxs-lookup"><span data-stu-id="bad4b-107">To change the color of an indicator icon</span></span>  
  
1.  <span data-ttu-id="bad4b-108">右键单击要更改的指示器，然后单击“指示器属性”  。</span><span class="sxs-lookup"><span data-stu-id="bad4b-108">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="bad4b-109">在左窗格中单击 **“值和状态”** 。</span><span class="sxs-lookup"><span data-stu-id="bad4b-109">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="bad4b-110">单击您要更改的图标旁的 **“颜色”** 列中的向下箭头，单击要使用的颜色、 **“无颜色”** 或 **“其他颜色”** 。</span><span class="sxs-lookup"><span data-stu-id="bad4b-110">Click the down arrow in the **Color** column next to the icon that you want to change and click the color to use, **No Color**, or **More colors**.</span></span>  
  
     <span data-ttu-id="bad4b-111">根据需要，可以单击“表达式”(fx) 按钮以编辑设置该“颜色”选项的值的表达式    。</span><span class="sxs-lookup"><span data-stu-id="bad4b-111">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the value of the **Color** option.</span></span>  
  
     <span data-ttu-id="bad4b-112">如果您单击了 **“其他颜色”** ，则 **“选择颜色”** 对话框将打开，从中可以选择多种不同的颜色。</span><span class="sxs-lookup"><span data-stu-id="bad4b-112">If you clicked **More Colors**, the **Select Color** dialog box opens, where you can choose from a wide array of colors.</span></span> <span data-ttu-id="bad4b-113">有关其选项的详细信息，请参阅[选择颜色对话框（报表生成器和 SSRS）](../select-color-dialog-box-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="bad4b-113">For more information about its options, see [Select Color Dialog Box &#40;Report Builder and SSRS&#41;](../select-color-dialog-box-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="bad4b-114">单击 **“确定”** 关闭 **“选择颜色”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="bad4b-114">Click **OK** to close the **Select Color** dialog box.</span></span>  
  
4.  <span data-ttu-id="bad4b-115">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="bad4b-115">Click **OK**.</span></span>  
  
### <a name="to-change-the-icon"></a><span data-ttu-id="bad4b-116">更改图标</span><span class="sxs-lookup"><span data-stu-id="bad4b-116">To change the icon</span></span>  
  
1.  <span data-ttu-id="bad4b-117">右键单击要更改的指示器，然后单击“指示器属性”  。</span><span class="sxs-lookup"><span data-stu-id="bad4b-117">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="bad4b-118">在左窗格中单击 **“值和状态”** 。</span><span class="sxs-lookup"><span data-stu-id="bad4b-118">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="bad4b-119">单击您要更改的图标旁的向下箭头，然后选择其他图标。</span><span class="sxs-lookup"><span data-stu-id="bad4b-119">Click the down arrow next to the icon that you want to change and select a different icon.</span></span>  
  
     <span data-ttu-id="bad4b-120">根据需要，可以单击“表达式”(fx) 按钮以编辑设置该“图标”选项的值的表达式    。</span><span class="sxs-lookup"><span data-stu-id="bad4b-120">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the value of the **Icon** option.</span></span>  
  
4.  <span data-ttu-id="bad4b-121">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="bad4b-121">Click **OK**.</span></span>  
  
### <a name="to-use-a-custom-image-as-an-indicator-icon"></a><span data-ttu-id="bad4b-122">使用自定义图像作为指示器图标</span><span class="sxs-lookup"><span data-stu-id="bad4b-122">To use a custom image as an indicator icon</span></span>  
  
1.  <span data-ttu-id="bad4b-123">右键单击要更改的指示器，然后单击“指示器属性”  。</span><span class="sxs-lookup"><span data-stu-id="bad4b-123">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="bad4b-124">在左窗格中单击 **“值和状态”** 。</span><span class="sxs-lookup"><span data-stu-id="bad4b-124">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="bad4b-125">单击您要更改的图标旁的向下箭头，然后选择 **“图像”** 。</span><span class="sxs-lookup"><span data-stu-id="bad4b-125">Click the down arrow next to the icon that you wan to change and select **Image**.</span></span>  
  
4.  <span data-ttu-id="bad4b-126">在 **“选择图像源”** 列表中，单击 **“外部”** 、 **“嵌入”** 或 **“数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="bad4b-126">In the **Select the image source** list, click **External**, **Embedded**, or **Database**.</span></span>  
  
5.  <span data-ttu-id="bad4b-127">根据图像的源，执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="bad4b-127">Depending on the source of the image, do the one of the following:</span></span>  
  
    -   <span data-ttu-id="bad4b-128">若要使用在报表外部存储的图像，请单击 **“浏览”** 并且找到该图像。</span><span class="sxs-lookup"><span data-stu-id="bad4b-128">To use an image that is stored externally to the report, click **Browse** and locate the image.</span></span> <span data-ttu-id="bad4b-129">该报表将包含对图像的引用。</span><span class="sxs-lookup"><span data-stu-id="bad4b-129">The report will include a reference to the image.</span></span>  
  
    -   <span data-ttu-id="bad4b-130">若要使用在报表中嵌入的图像，请单击 **“导入”** 并且找到该图像。</span><span class="sxs-lookup"><span data-stu-id="bad4b-130">To use an image that is embedded in the report, click **Import** and locate the image.</span></span> <span data-ttu-id="bad4b-131">图像将被添加到报表定义中并一起保存。</span><span class="sxs-lookup"><span data-stu-id="bad4b-131">The image will be added to the report definition and saved with it.</span></span>  
  
    -   <span data-ttu-id="bad4b-132">若要使用位于数据库中的图像，请在 **“使用此字段”** 列表中选择相应字段，</span><span class="sxs-lookup"><span data-stu-id="bad4b-132">To use an image that is in a database, in the **Use this field** list.</span></span> <span data-ttu-id="bad4b-133">然后在 **“使用此 MIME 类型”** 列表中选择图像的 MIME 类型。</span><span class="sxs-lookup"><span data-stu-id="bad4b-133">select the field from the list and then in the **Use this MIME type** list, select the MIME type of the image.</span></span>  
  
6.  <span data-ttu-id="bad4b-134">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="bad4b-134">Click **OK**.</span></span>  
  
### <a name="to-add-an-icon-to-the-indicator-set"></a><span data-ttu-id="bad4b-135">将图标添加到指示器集</span><span class="sxs-lookup"><span data-stu-id="bad4b-135">To add an icon to the indicator set</span></span>  
  
1.  <span data-ttu-id="bad4b-136">右键单击要更改的指示器，然后单击“指示器属性”  。</span><span class="sxs-lookup"><span data-stu-id="bad4b-136">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="bad4b-137">在左窗格中单击 **“值和状态”** 。</span><span class="sxs-lookup"><span data-stu-id="bad4b-137">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="bad4b-138">单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="bad4b-138">Click **Add**.</span></span> <span data-ttu-id="bad4b-139">将添加一个指示器，并且使用默认图标和 **“无颜色”** 选项。</span><span class="sxs-lookup"><span data-stu-id="bad4b-139">An indicator is added, using the default icon and the **No Color** option.</span></span>  
  
     <span data-ttu-id="bad4b-140">配置该指示器以便使用您所需的图标和颜色。</span><span class="sxs-lookup"><span data-stu-id="bad4b-140">Configure the indictor to use the icon and color you want.</span></span> <span data-ttu-id="bad4b-141">本主题中前面的过程描述用于执行此操作的步骤。</span><span class="sxs-lookup"><span data-stu-id="bad4b-141">Procedures earlier in this topic describe the steps to do this.</span></span>  
  
4.  <span data-ttu-id="bad4b-142">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="bad4b-142">Click **OK**.</span></span>  
  
### <a name="to-delete-an-icon-to-the-indicator-set"></a><span data-ttu-id="bad4b-143">从指示器集中删除图标</span><span class="sxs-lookup"><span data-stu-id="bad4b-143">To delete an icon to the indicator set</span></span>  
  
1.  <span data-ttu-id="bad4b-144">右键单击要更改的指示器，然后单击“指示器属性”  。</span><span class="sxs-lookup"><span data-stu-id="bad4b-144">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="bad4b-145">在左窗格中单击 **“值和状态”** 。</span><span class="sxs-lookup"><span data-stu-id="bad4b-145">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="bad4b-146">选择要删除的图标，然后单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="bad4b-146">Select the icon to delete, and click **Delete**.</span></span>  
  
4.  <span data-ttu-id="bad4b-147">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="bad4b-147">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bad4b-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bad4b-148">See Also</span></span>  
 [<span data-ttu-id="bad4b-149">指示器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="bad4b-149">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
