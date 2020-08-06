---
title: "\"选择颜色\" 对话框 (报表生成器和 SSRS) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.selectcolor.f1
- "10090"
helpviewer_keywords:
- Select Color dialog box
ms.assetid: ac7089a3-5c7b-4f53-8348-180610e86da2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a2526b755fd4e08faf79998d351e824371fac2f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692660"
---
# <a name="select-color-dialog-box-report-builder-and-ssrs"></a><span data-ttu-id="1a3e5-102">“选择颜色”对话框（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="1a3e5-102">Select Color Dialog Box (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1a3e5-103">使用 **“选择颜色”** 对话框可以为数据区域或文本框中单个或多个单元的背景指定颜色选项，或为图表指定颜色选项。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-103">Use the **Select Color** dialog box to specify color options for the background of a single cell or multiple cells within a data region or a text box, or for a chart.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1a3e5-104">选项</span><span class="sxs-lookup"><span data-stu-id="1a3e5-104">Options</span></span>  
 <span data-ttu-id="1a3e5-105">**颜色选择器**</span><span class="sxs-lookup"><span data-stu-id="1a3e5-105">**Color selector**</span></span>  
 <span data-ttu-id="1a3e5-106">从三个用于指定颜色选择方式的选项中进行选择：</span><span class="sxs-lookup"><span data-stu-id="1a3e5-106">Choose from three options that specify how you want to select colors:</span></span>  
  
-   <span data-ttu-id="1a3e5-107">**选取器 - 色环** 使用“色调/饱和度/亮度”(HSB) 颜色值选择颜色。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-107">**Picker - Color circle** Choose a color using Hue/Saturation/Brightness (HSB) color values.</span></span>  
  
-   <span data-ttu-id="1a3e5-108">**选取器 - 色块** 使用“红/绿/蓝”(RGB) 颜色值选择颜色。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-108">**Picker - Color square** Choose a color using Red/Green/Blue (RGB) color values.</span></span>  
  
-   <span data-ttu-id="1a3e5-109">**调色板 - 标准颜色** 从预定义的颜色值列表中选择颜色。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-109">**Palette - Standard colors** Choose a color from a predefined list of color values.</span></span>  
  
 <span data-ttu-id="1a3e5-110">**色环**</span><span class="sxs-lookup"><span data-stu-id="1a3e5-110">**Color circle**</span></span>  
 <span data-ttu-id="1a3e5-111">用于 HSB 颜色，因为 HSB 值映射到柱面坐标系。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-111">Use for HSB colors because HSB values are mapped onto a cylindrical coordinate system.</span></span> <span data-ttu-id="1a3e5-112">色调是实际的颜色，饱和度是颜色纯度，亮度是相对的明暗。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-112">Hue is the actual color, saturation is purity of color, brightness is relative brightness or darkness.</span></span>  
  
 <span data-ttu-id="1a3e5-113">当您选取一个颜色时，圆的中心决定了颜色。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-113">When you pick a color, the center of the circle determines the color.</span></span> <span data-ttu-id="1a3e5-114">使用颜色滑块可更改色调。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-114">Use the color slider to change the hue.</span></span> <span data-ttu-id="1a3e5-115">x 坐标和 y 坐标分别表示饱和度和亮度值。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-115">The x and y coordinates represent saturation and brightness values respectively.</span></span>  
  
 <span data-ttu-id="1a3e5-116">**色块**</span><span class="sxs-lookup"><span data-stu-id="1a3e5-116">**Color square**</span></span>  
 <span data-ttu-id="1a3e5-117">用于 RGB 颜色，因为 RGB 值映射到笛卡尔坐标系。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-117">Use for RGB colors because RGB values are mapped to a Cartesian coordinate system.</span></span> <span data-ttu-id="1a3e5-118">R 代表红色值，G 代表绿色值，B 代表蓝色值。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-118">R is the value for Red, G is the value for Green, B is the value for Blue.</span></span>  
  
 <span data-ttu-id="1a3e5-119">当您选取一个颜色时，方块的中心决定了颜色。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-119">When you pick a color, the center of the square determines the color.</span></span> <span data-ttu-id="1a3e5-120">使用颜色滑块可更改所选颜色的范围。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-120">Use the color slider to change the range of the chosen color.</span></span> <span data-ttu-id="1a3e5-121">x 和 y 坐标代表其他两种颜色。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-121">The x and y coordinates represent the other two colors.</span></span> <span data-ttu-id="1a3e5-122">例如，如果您选择绿色，滑块将显示绿色值的范围，x 和 y 坐标则分别代表红色和蓝色值。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-122">For example, if you pick green, the slider shows the range of green values, the x and y coordinates represent red and blue values respectively.</span></span>  
  
 <span data-ttu-id="1a3e5-123">**标准调色板颜色**</span><span class="sxs-lookup"><span data-stu-id="1a3e5-123">**Standard palette color**</span></span>  
 <span data-ttu-id="1a3e5-124">用于枚举中的命名颜色 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] `KnownColor` 。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-124">Use for named colors from the [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] `KnownColor` enumeration.</span></span>  
  
 <span data-ttu-id="1a3e5-125">**颜色系统**</span><span class="sxs-lookup"><span data-stu-id="1a3e5-125">**Color system**</span></span>  
 <span data-ttu-id="1a3e5-126">指定 RGB 或 HSB 颜色。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-126">Specify RGB or HSB colors.</span></span> <span data-ttu-id="1a3e5-127">该选项用于更改显示器以显示 RGB 或 HSB 值，当您使用 **“颜色选择器”** 的色环或色块时，这些值将以交互方式更新。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-127">This choice changes the display to show RGB or HSB values, which are updated interactively when you use a color circle or color square for the **Color selector**.</span></span>  
  
 <span data-ttu-id="1a3e5-128">对于某些属性，如果颜色可包含透明度值，则会显示 **Alpha** 值。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-128">The **Alpha** value displays for some properties when a color can include a transparency value.</span></span> <span data-ttu-id="1a3e5-129">例如，图表序列填充。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-129">For example, Chart series fill.</span></span> <span data-ttu-id="1a3e5-130">对于不支持透明度的属性，该值将被禁用。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-130">For properties that do not support transparency, this value is disabled.</span></span>  
  
 <span data-ttu-id="1a3e5-131">**红色**</span><span class="sxs-lookup"><span data-stu-id="1a3e5-131">**Red**</span></span>  
 <span data-ttu-id="1a3e5-132">代表 RGB 颜色中红色部分的十进制值。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-132">The decimal value for the red part of the RGB color.</span></span> <span data-ttu-id="1a3e5-133">使用数字调整框可更改值或键入一个介于 0 到 255 之间的值。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-133">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="1a3e5-134">**绿色**</span><span class="sxs-lookup"><span data-stu-id="1a3e5-134">**Green**</span></span>  
 <span data-ttu-id="1a3e5-135">代表 RGB 颜色中绿色部分的十进制值。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-135">The decimal value for the green part of the RGB color.</span></span> <span data-ttu-id="1a3e5-136">使用数字调整框可更改值或键入一个介于 0 到 255 之间的值。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-136">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="1a3e5-137">**蓝色**</span><span class="sxs-lookup"><span data-stu-id="1a3e5-137">**Blue**</span></span>  
 <span data-ttu-id="1a3e5-138">代表 RGB 颜色中蓝色部分的十进制值。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-138">The decimal value for the blue part of the RGB color.</span></span> <span data-ttu-id="1a3e5-139">使用数字调整框可更改值或键入一个介于 0 到 255 之间的值。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-139">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="1a3e5-140">**Alpha**</span><span class="sxs-lookup"><span data-stu-id="1a3e5-140">**Alpha**</span></span>  
 <span data-ttu-id="1a3e5-141">代表颜色中 Alpha 或透明度部分的十进制值。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-141">The decimal value for the alpha or transparency part of the color.</span></span> <span data-ttu-id="1a3e5-142">启用该值后，您可使用滑块开关调整至所需的透明度。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-142">When this value is enabled, you can use the slider switch to adjust the degree of transparency you want.</span></span>  
  
 <span data-ttu-id="1a3e5-143">**Hue**</span><span class="sxs-lookup"><span data-stu-id="1a3e5-143">**Hue**</span></span>  
 <span data-ttu-id="1a3e5-144">代表 HSB 颜色色调的十进制值。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-144">The decimal value for the hue of the HSB color.</span></span> <span data-ttu-id="1a3e5-145">使用数字调整框可更改值或键入一个介于 0 到 255 之间的值。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-145">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="1a3e5-146">**饱和度**</span><span class="sxs-lookup"><span data-stu-id="1a3e5-146">**Saturation**</span></span>  
 <span data-ttu-id="1a3e5-147">代表 HSB 颜色饱和度的十进制值。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-147">The decimal value for the saturation of the HSB color.</span></span> <span data-ttu-id="1a3e5-148">使用数字调整框可更改值或键入一个介于 0 到 255 之间的值。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-148">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="1a3e5-149">**亮度**</span><span class="sxs-lookup"><span data-stu-id="1a3e5-149">**Brightness**</span></span>  
 <span data-ttu-id="1a3e5-150">代表 HSB 颜色亮度的十进制值。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-150">The decimal value for the brightness of the HSB color.</span></span> <span data-ttu-id="1a3e5-151">使用数字调整框可更改值或键入一个介于 0 到 255 之间的值。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-151">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="1a3e5-152">**颜色示例**</span><span class="sxs-lookup"><span data-stu-id="1a3e5-152">**Color sample**</span></span>  
 <span data-ttu-id="1a3e5-153">在窗格的左半部分显示当前颜色，并在窗格的右半部分以交互方式显示您所选择的新颜色。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-153">Shows the current color on the left half of the pane and interactively shows the new color you are choosing on the right half of the pane.</span></span> <span data-ttu-id="1a3e5-154">如果没有默认颜色，窗格的左半部分为白色。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-154">If there is no default color, the left half of the pane is white.</span></span> <span data-ttu-id="1a3e5-155">绝大多数 RDL 属性没有默认颜色。</span><span class="sxs-lookup"><span data-stu-id="1a3e5-155">Most RDL properties have no default color.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a3e5-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1a3e5-156">See Also</span></span>  
 <span data-ttu-id="1a3e5-157">[&#40;报表生成器和 SSRS 的格式设置报表项&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1a3e5-157">[Formatting Report Items &#40;Report Builder and SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1a3e5-158">设置文本和占位符的格式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="1a3e5-158">Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;</span></span>](report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md)  
  
  
