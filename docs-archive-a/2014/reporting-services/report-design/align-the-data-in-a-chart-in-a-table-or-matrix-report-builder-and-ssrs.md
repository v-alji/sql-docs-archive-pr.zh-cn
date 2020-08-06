---
title: 在表或矩阵中的图表中对齐数据（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 75137575-d1bf-46d6-8527-5afc85eea5e1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3e4278cd9f0dd5526770b43d2c6d94a8b87158cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590080"
---
# <a name="align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs"></a><span data-ttu-id="56357-102">在表或矩阵中的图表中对齐数据（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="56357-102">Align the Data in a Chart in a Table or Matrix (Report Builder and SSRS)</span></span>
  <span data-ttu-id="56357-103">迷你图和数据条是小的简单图表，它们包含一些额外细节，可以传递很多信息。</span><span class="sxs-lookup"><span data-stu-id="56357-103">Sparklines and data bars are small, simple charts that convey a lot of information with little extraneous detail.</span></span> <span data-ttu-id="56357-104">选中此选项时，迷你图和数据条中的值将在表或矩阵的不同单元中对齐，即使缺少它们所基于的数据的值。</span><span class="sxs-lookup"><span data-stu-id="56357-104">When you check this option, the values in your sparklines and data bars will align across the different cells in the table or matrix, even if there are missing values in the data they are based on.</span></span>  
  
 <span data-ttu-id="56357-105">![rs_SparklineAlignData](../media/rs-sparklinealigndata.gif "rs_SparklineAlignData")</span><span class="sxs-lookup"><span data-stu-id="56357-105">![rs_SparklineAlignData](../media/rs-sparklinealigndata.gif "rs_SparklineAlignData")</span></span>  
  
 <span data-ttu-id="56357-106">在此图像中，柱形图显示每个雇员每天的销售额。</span><span class="sxs-lookup"><span data-stu-id="56357-106">In this image, the column chart shows daily sales for each employee.</span></span> <span data-ttu-id="56357-107">请注意，对于雇员没有销售额数据的那些天，该图留空并水平对齐后面的天。</span><span class="sxs-lookup"><span data-stu-id="56357-107">Note that for days that an employee has no sales, the chart leaves a blank and aligns subsequent days horizontally.</span></span> <span data-ttu-id="56357-108">它还通过使不同大小的图表彼此相对，垂直对齐图表。</span><span class="sxs-lookup"><span data-stu-id="56357-108">It also aligns the charts vertically by making the sizes of the different charts relative to each other.</span></span> <span data-ttu-id="56357-109">有关详细信息，请参阅 [迷你图和数据条（报表生成器和 SSRS）](sparklines-and-data-bars-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="56357-109">For more information, see [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="align-the-data-in-a-sparkline-or-data-bar"></a><span data-ttu-id="56357-110">对齐迷你图或数据条中的数据</span><span class="sxs-lookup"><span data-stu-id="56357-110">Align the data in a sparkline or data bar</span></span>  
  
1.  <span data-ttu-id="56357-111">单击迷你图或数据条，然后单击 **“水平轴属性”** 或 **“垂直轴属性”**。</span><span class="sxs-lookup"><span data-stu-id="56357-111">Click in the sparkline or data bar, and then click **Horizontal Axis Properties** or **Vertical Axis Properties**.</span></span>  
  
2.  <span data-ttu-id="56357-112">在 **“轴选项”** 选项卡上，选中 **“对齐轴”** 框，然后在下拉框中选择要对齐轴的组。</span><span class="sxs-lookup"><span data-stu-id="56357-112">On the **Axis Options** tab, check the **Align axes in** box, and then in the dropdown box, select the group on which to align the axis.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="56357-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="56357-113">See Also</span></span>  
 <span data-ttu-id="56357-114">[图表 &#40;报表生成器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="56357-114">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="56357-115">添加迷你图和数据条（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="56357-115">Add Sparklines and Data Bars &#40;Report Builder and SSRS&#41;</span></span>](add-sparklines-and-data-bars-report-builder-and-ssrs.md)  
  
  
