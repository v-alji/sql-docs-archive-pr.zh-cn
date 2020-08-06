---
title: 添加迷你图和数据条（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0b297c2e-d48b-41b0-aabd-29680cdcdb05
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 55ec15354cdc78dd9678b9466f30d2fca0a73adc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578647"
---
# <a name="add-sparklines-and-data-bars-report-builder-and-ssrs"></a><span data-ttu-id="234e0-102">添加迷你图和数据条（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="234e0-102">Add Sparklines and Data Bars (Report Builder and SSRS)</span></span>
  <span data-ttu-id="234e0-103">迷你图和数据条是小的备用图，它包含一些额外细节，可以传递很多信息。</span><span class="sxs-lookup"><span data-stu-id="234e0-103">Sparklines and data bars are small, spare charts that convey a lot of information with little extraneous detail.</span></span> <span data-ttu-id="234e0-104">有关它们的详细信息，请参阅[迷你图和数据条（报表生成器和 SSRS）](sparklines-and-data-bars-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="234e0-104">For more information about them, see [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="234e0-105">迷你图和数据条在表或矩阵的单元中最常见。</span><span class="sxs-lookup"><span data-stu-id="234e0-105">Sparklines and data bars are most commonly placed in cells in a table or matrix.</span></span> <span data-ttu-id="234e0-106">迷你图通常每个只显示一个系列。</span><span class="sxs-lookup"><span data-stu-id="234e0-106">Sparklines usually display only one series each.</span></span> <span data-ttu-id="234e0-107">数据条可以包含一个或多个数据点。</span><span class="sxs-lookup"><span data-stu-id="234e0-107">Data bars can contain one or more data points.</span></span> <span data-ttu-id="234e0-108">迷你图和数据条都是通过重复表或矩阵中每行的序列信息来得出它们的影响。</span><span class="sxs-lookup"><span data-stu-id="234e0-108">Both sparklines and data bars derive their impact from repeating the series information for each row in the table or matrix.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-sparkline-or-data-bar-to-a-table-or-matrix"></a><span data-ttu-id="234e0-109">向表或矩阵添加迷你图或数据条</span><span class="sxs-lookup"><span data-stu-id="234e0-109">To add a sparkline or data bar to a table or matrix</span></span>  
  
1.  <span data-ttu-id="234e0-110">如果还没有这样做，请使用要显示的数据创建一个表或矩阵。</span><span class="sxs-lookup"><span data-stu-id="234e0-110">If you have not done so already, create a table or matrix with the data you want to display.</span></span> <span data-ttu-id="234e0-111">有关详细信息，请参阅[表（报表生成器和 SSRS）](tables-report-builder-and-ssrs.md)或[矩阵（报表生成器和 SSRS）](create-a-matrix-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="234e0-111">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) or [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="234e0-112">在您的表或矩阵中插入列。</span><span class="sxs-lookup"><span data-stu-id="234e0-112">Insert a column in your table or matrix.</span></span> <span data-ttu-id="234e0-113">有关详细信息，请参阅[插入或删除列（报表生成器和 SSRS）](insert-or-delete-a-column-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="234e0-113">For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
3.  <span data-ttu-id="234e0-114">在 **“插入”** 选项卡上，单击 **“迷你图”** 或 **“数据条”**，然后单击新列中的单元。</span><span class="sxs-lookup"><span data-stu-id="234e0-114">On the **Insert** tab, click **Sparkline** or **Data Bar**, and then click in a cell in the new column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="234e0-115">不能将迷你图放置于表的详细信息组中。</span><span class="sxs-lookup"><span data-stu-id="234e0-115">You cannot place sparklines in a detail group in a table.</span></span> <span data-ttu-id="234e0-116">它们必须处于与组相关联的单元中。</span><span class="sxs-lookup"><span data-stu-id="234e0-116">They must go in a cell associated with a group.</span></span>  
  
4.  <span data-ttu-id="234e0-117">在“更改迷你图/数据条类型”\*\*\*\* 对话框中，单击所需的迷你图或数据条类型，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="234e0-117">In the **Change Sparkline/Data Bar Type** dialog box, click the kind of sparkline or data bar you want, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="234e0-118">单击该迷你图或数据条。</span><span class="sxs-lookup"><span data-stu-id="234e0-118">Click the sparkline or data bar.</span></span>  
  
     <span data-ttu-id="234e0-119">将打开 **“图表数据”** 窗格。</span><span class="sxs-lookup"><span data-stu-id="234e0-119">The **Chart Data** pane opens.</span></span>  
  
6.  <span data-ttu-id="234e0-120">在“值”\*\*\*\* 区域中，单击“添加字段”\*\*\*\* 加号 (**+**)，然后单击要将其值制成图表的字段。</span><span class="sxs-lookup"><span data-stu-id="234e0-120">In the **Values** area, click the **Add Fields** plus sign (**+**), and then click the field whose values you want charted.</span></span>  
  
7.  <span data-ttu-id="234e0-121">在“类别组”\*\*\*\* 区域中，单击“添加字段”\*\*\*\* 加号 (**+**)，然后单击要依据其值分组的字段。</span><span class="sxs-lookup"><span data-stu-id="234e0-121">In the **Category Groups** area, click the **Add Fields** plus sign (**+**), and then click the field whose values you want to group by.</span></span>  
  
     <span data-ttu-id="234e0-122">对于迷你图和数据条，通常不向 **“序列组”** 区域添加字段，因为每行只需要一个序列。</span><span class="sxs-lookup"><span data-stu-id="234e0-122">Typically for sparklines and data bars, you will not add a field to the **Series Group** area because you only want one series for each row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="234e0-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="234e0-123">See Also</span></span>  
 <span data-ttu-id="234e0-124">[图表 &#40;报表生成器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="234e0-124">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="234e0-125">在表或矩阵中的图表中对齐数据（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="234e0-125">Align the Data in a Chart in a Table or Matrix &#40;Report Builder and SSRS&#41;</span></span>](align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs.md)  
  
  
