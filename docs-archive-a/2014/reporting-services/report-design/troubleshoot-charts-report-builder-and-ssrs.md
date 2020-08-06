---
title: 图表故障排除（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b931b50545ba2b8d7c4c06cc5c48d6415a05470a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690377"
---
# <a name="troubleshoot-charts-report-builder-and-ssrs"></a><span data-ttu-id="a807f-102">图表故障排除（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="a807f-102">Troubleshoot Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a807f-103">对以下问题的解答可能在您使用图表时对您有所帮助。</span><span class="sxs-lookup"><span data-stu-id="a807f-103">These issues can be helpful when working with charts.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="why-does-my-chart-count-not-sum-the-values-on-the-value-axis"></a><span data-ttu-id="a807f-104">为什么我的图表对值轴上的值进行计数，而不是求和？</span><span class="sxs-lookup"><span data-stu-id="a807f-104">Why does my chart count, not sum, the values on the value axis?</span></span>  
 <span data-ttu-id="a807f-105">大多数图表类型都要求数值放置在通常作为 y 轴的值轴上，以便能够正确地绘制图表。</span><span class="sxs-lookup"><span data-stu-id="a807f-105">Most chart types require numeric values along the value axis, which is typically the y-axis, in order to draw correctly.</span></span> <span data-ttu-id="a807f-106">如果值字段的数据类型是 `String`，则图表将无法显示数值，即使这些字段中包含数字也是如此。</span><span class="sxs-lookup"><span data-stu-id="a807f-106">If the data type of your value field is `String`, the chart cannot display a numeric value, even if there are numerals in the fields.</span></span> <span data-ttu-id="a807f-107">相反，该图表将显示包含该字段中值的行的总行数。</span><span class="sxs-lookup"><span data-stu-id="a807f-107">Instead, the chart displays a count of the total number of rows that contain a value in that field.</span></span> <span data-ttu-id="a807f-108">若要避免出现此情况，请确保用于值序列的字段是数字数据类型的，而不是包含格式化数字的字符串。</span><span class="sxs-lookup"><span data-stu-id="a807f-108">To avoid this behavior, make sure that the fields that you use for value series have numeric data types, as opposed to strings that contain formatted numbers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a807f-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a807f-109">See Also</span></span>  
 [<span data-ttu-id="a807f-110">图表&#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a807f-110">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
