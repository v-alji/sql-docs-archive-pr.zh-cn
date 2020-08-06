---
title: 在图表中添加或删除组（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0445b0ac-acae-4462-80fb-fe9735ac66db
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2ac558ccbd8855018877228b2b38debf769f1573
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692727"
---
# <a name="add-or-delete-a-group-in-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="5f29c-102">在图表中添加或删除组（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="5f29c-102">Add or Delete a Group in a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="5f29c-103">单击图表数据区域以显示 **“图表数据”** 窗格。</span><span class="sxs-lookup"><span data-stu-id="5f29c-103">Click in the chart data region to display the **Chart Data** pane.</span></span> <span data-ttu-id="5f29c-104">通过将数据集字段拖到 **“类别组”** 和 **“序列组”** 区域来创建组。</span><span class="sxs-lookup"><span data-stu-id="5f29c-104">Create groups by dragging dataset fields to the **Category Groups** and **Series Groups** areas.</span></span> <span data-ttu-id="5f29c-105">若要添加嵌套组，请向该区域添加多个字段。</span><span class="sxs-lookup"><span data-stu-id="5f29c-105">To add nested groups, add multiple fields to the area.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-parent-or-child-group-to-a-chart"></a><span data-ttu-id="5f29c-106">向图表添加父组或子组</span><span class="sxs-lookup"><span data-stu-id="5f29c-106">To add a parent or child group to a chart</span></span>  
  
1.  <span data-ttu-id="5f29c-107">在报表设计图面上，单击图表中的任意位置以将其选中。</span><span class="sxs-lookup"><span data-stu-id="5f29c-107">On the report design surface, click anywhere in the chart to select it.</span></span> <span data-ttu-id="5f29c-108">此时将显示“图表数据”窗格  。</span><span class="sxs-lookup"><span data-stu-id="5f29c-108">The **Chart Data** pane appears.</span></span>  
  
2.  <span data-ttu-id="5f29c-109">将字段从 **“报表数据”** 窗口拖到 **“类别组”** 或 **“序列组”** 区域。</span><span class="sxs-lookup"><span data-stu-id="5f29c-109">Drag a field from the **Report Data** window to the **Category Groups** or **Series Groups** area.</span></span> <span data-ttu-id="5f29c-110">若要添加父组，请将光标置于现有组之前。</span><span class="sxs-lookup"><span data-stu-id="5f29c-110">To add a parent group, position the cursor in front of an existing group.</span></span> <span data-ttu-id="5f29c-111">若要添加子组，请将光标置于现有组之后。</span><span class="sxs-lookup"><span data-stu-id="5f29c-111">To add a child group, position the cursor after an existing group.</span></span>  
  
### <a name="to-edit-a-category-group-on-a-chart"></a><span data-ttu-id="5f29c-112">在图表中编辑类别组</span><span class="sxs-lookup"><span data-stu-id="5f29c-112">To edit a category group on a chart</span></span>  
  
1.  <span data-ttu-id="5f29c-113">在报表设计图面上，单击图表中的任意位置以将其选中。</span><span class="sxs-lookup"><span data-stu-id="5f29c-113">On the report design surface, click anywhere in the chart to select it.</span></span> <span data-ttu-id="5f29c-114">此时将显示“图表数据”窗格  。</span><span class="sxs-lookup"><span data-stu-id="5f29c-114">The **Chart Data** pane appears.</span></span>  
  
2.  <span data-ttu-id="5f29c-115">在“类别组”  区域中右键单击该组，然后单击“类别组属性”  。</span><span class="sxs-lookup"><span data-stu-id="5f29c-115">Right-click the group in the **Category Groups** area, and then click **Category Group Properties**.</span></span>  
  
3.  <span data-ttu-id="5f29c-116">添加或删除组表达式、筛选器、排序表达式和组变量。</span><span class="sxs-lookup"><span data-stu-id="5f29c-116">Add or remove group expressions, filters, sort expressions, and group variables.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-a-series-group-on-a-chart"></a><span data-ttu-id="5f29c-117">在图表中编辑序列组</span><span class="sxs-lookup"><span data-stu-id="5f29c-117">To edit a series group on a chart</span></span>  
  
1.  <span data-ttu-id="5f29c-118">在报表设计图面上，单击图表中的任意位置以将其选中。</span><span class="sxs-lookup"><span data-stu-id="5f29c-118">On the report design surface, click anywhere in the chart to select it.</span></span> <span data-ttu-id="5f29c-119">此时将显示“图表数据”窗格  。</span><span class="sxs-lookup"><span data-stu-id="5f29c-119">The **Chart Data** pane appears.</span></span>  
  
2.  <span data-ttu-id="5f29c-120">在“序列组”  区域中右键单击该组，然后单击“序列组属性”  。</span><span class="sxs-lookup"><span data-stu-id="5f29c-120">Right-click the group in the **Series Groups** area, and then click **Series Group Properties**.</span></span>  
  
3.  <span data-ttu-id="5f29c-121">添加或删除组表达式、筛选器、排序表达式和组变量。</span><span class="sxs-lookup"><span data-stu-id="5f29c-121">Add or remove group expressions, filters, sort expressions, and group variables.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-group-from-a-chart"></a><span data-ttu-id="5f29c-122">从图表中删除组</span><span class="sxs-lookup"><span data-stu-id="5f29c-122">To delete a group from a chart</span></span>  
  
1.  <span data-ttu-id="5f29c-123">在报表设计图面上，单击图表中的任意位置以将其选中。</span><span class="sxs-lookup"><span data-stu-id="5f29c-123">On the report design surface, click anywhere in the chart to select it.</span></span> <span data-ttu-id="5f29c-124">此时将显示“图表数据”窗格  。</span><span class="sxs-lookup"><span data-stu-id="5f29c-124">The **Chart Data** pane appears.</span></span>  
  
2.  <span data-ttu-id="5f29c-125">在“类别组”  或“序列组”  区域中右键单击该组，然后单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="5f29c-125">Right-click the group in the **Category Groups** or **Series Groups** area, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f29c-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5f29c-126">See Also</span></span>  
 [<span data-ttu-id="5f29c-127">图表&#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5f29c-127">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
