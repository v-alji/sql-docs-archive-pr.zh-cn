---
title: 从饼图顶部开始绘制饼图值（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d0e6fb59-ca4e-4d70-97cb-0ad183da21d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ed010eeaf3e4d581cce2f7242144c4f73ec2895b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577255"
---
# <a name="start-pie-chart-values-at-the-top-of-the-pie-report-builder-and-ssrs"></a><span data-ttu-id="a5bc5-102">从饼图顶部开始绘制饼图值（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="a5bc5-102">Start Pie Chart Values at the Top of the Pie (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a5bc5-103">默认情况下，在饼图中，数据集中的第一个值从与饼顶部成 90 度的位置开始绘制。</span><span class="sxs-lookup"><span data-stu-id="a5bc5-103">By default in pie charts, the first value in the dataset starts at 90 degrees from the top of the pie.</span></span> <span data-ttu-id="a5bc5-104">您可能希望从顶部开始绘制第一个值。</span><span class="sxs-lookup"><span data-stu-id="a5bc5-104">You may prefer that the first value start from the top.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-start-the-pie-chart-at-the-top-of-the-pie"></a><span data-ttu-id="a5bc5-105">从饼顶部开始绘制饼图</span><span class="sxs-lookup"><span data-stu-id="a5bc5-105">To Start the Pie Chart at the Top of the Pie</span></span>  
  
1.  <span data-ttu-id="a5bc5-106">单击饼图本身。</span><span class="sxs-lookup"><span data-stu-id="a5bc5-106">Click the pie itself.</span></span>  
  
2.  <span data-ttu-id="a5bc5-107">如果 **“属性”** 窗格未打开，请单击 **“视图”** 选项卡上的 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="a5bc5-107">If the **Properties** pane is not open, on the **View** tab, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="a5bc5-108">在 "**属性**" 窗格中的 "**自定义属性**" 下，将**PieStartAngle**从**0**更改为**270**。</span><span class="sxs-lookup"><span data-stu-id="a5bc5-108">In the **Properties** pane, under **Custom Attributes**, change **PieStartAngle** from **0** to **270**.</span></span>  
  
4.  <span data-ttu-id="a5bc5-109">单击 **“运行”** 以预览报表。</span><span class="sxs-lookup"><span data-stu-id="a5bc5-109">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="a5bc5-110">第一个值现在将从饼图顶部开始绘制。</span><span class="sxs-lookup"><span data-stu-id="a5bc5-110">The first value now starts at the top of the pie chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5bc5-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a5bc5-111">See Also</span></span>  
 <span data-ttu-id="a5bc5-112">[设置图表格式 &#40;报表生成器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a5bc5-112">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a5bc5-113">饼图&#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a5bc5-113">Pie Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
