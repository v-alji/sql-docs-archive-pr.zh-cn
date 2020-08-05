---
title: 添加子报表和参数（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10093"
- sql12.rtp.rptdesigner.subreportproperties.general.f1
ms.assetid: 94f960f8-a629-4f1e-8277-c3b8f0680d98
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3aeede343763ea5fc8fbdfde179208f98fa1a2ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577284"
---
# <a name="add-a-subreport-and-parameters-report-builder-and-ssrs"></a><span data-ttu-id="f9eef-102">添加子报表和参数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f9eef-102">Add a Subreport and Parameters (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f9eef-103">当您希望创建作为多个相关报表的容器的主报表时，可以向报表添加子报表。</span><span class="sxs-lookup"><span data-stu-id="f9eef-103">Add subreports to a report when you want to create a main report that is a container for multiple related reports.</span></span> <span data-ttu-id="f9eef-104">子报表是对另一个报表的引用。</span><span class="sxs-lookup"><span data-stu-id="f9eef-104">A subreport is a reference to another report.</span></span> <span data-ttu-id="f9eef-105">若要通过数据值使报表相关联（例如，使多个报表显示同一客户的数据），必须设计参数化报表（例如，显示特定客户详细信息的报表）作为子报表。</span><span class="sxs-lookup"><span data-stu-id="f9eef-105">To relate the reports through data values (for example, to have multiple reports show data for the same customer), you must design a parameterized report (for example, a report that shows the details for a specific customer) as the subreport.</span></span> <span data-ttu-id="f9eef-106">向主报表添加子报表时，可以指定传递给子报表的参数。</span><span class="sxs-lookup"><span data-stu-id="f9eef-106">When you add a subreport to the main report, you can specify parameters to pass to the subreport.</span></span>  
  
 <span data-ttu-id="f9eef-107">还可以向表或矩阵中的动态行或动态列添加子报表。</span><span class="sxs-lookup"><span data-stu-id="f9eef-107">You can also add subreports to dynamic rows or columns in a table or matrix.</span></span> <span data-ttu-id="f9eef-108">处理主报表时，会处理每行的子报表。</span><span class="sxs-lookup"><span data-stu-id="f9eef-108">When the main report is processed, the subreport is processed for each row.</span></span> <span data-ttu-id="f9eef-109">在这种情况下，请考虑您是否能通过使用数据区域或嵌套数据区域实现所需的效果。</span><span class="sxs-lookup"><span data-stu-id="f9eef-109">In this case, consider whether you can achieve the desired effect by using data regions or nested data regions.</span></span>  
  
 <span data-ttu-id="f9eef-110">若要向报表中添加子报表，您必须首先创建将作为子报表的报表。</span><span class="sxs-lookup"><span data-stu-id="f9eef-110">To add a subreport to a report, you must first create the report that will act as the subreport.</span></span> <span data-ttu-id="f9eef-111">有关创建子报表详细信息，请参阅 [子报表（报表生成器和 SSRS）](subreports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f9eef-111">For more information on creating the subreport, see [Subreports &#40;Report Builder and SSRS&#41;](subreports-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-subreport"></a><span data-ttu-id="f9eef-112">添加子报表</span><span class="sxs-lookup"><span data-stu-id="f9eef-112">To add a subreport</span></span>  
  
1.  <span data-ttu-id="f9eef-113">在 **“插入”** 选项卡上，单击 **“子报表”** 。</span><span class="sxs-lookup"><span data-stu-id="f9eef-113">On the **Insert** tab, click **Subreport**.</span></span>  
  
2.  <span data-ttu-id="f9eef-114">在设计图面上，单击报表上的某个位置，然后拖动一个框调整到所需子报表大小。</span><span class="sxs-lookup"><span data-stu-id="f9eef-114">On the design surface, click a location on the report and then drag a box to the desired size of the subreport.</span></span> <span data-ttu-id="f9eef-115">也可以单击设计图面来创建默认大小的子报表。</span><span class="sxs-lookup"><span data-stu-id="f9eef-115">Alternatively, click the design surface to create a subreport of default size.</span></span>  
  
3.  <span data-ttu-id="f9eef-116">右键单击子报表，然后单击“子报表属性”  。</span><span class="sxs-lookup"><span data-stu-id="f9eef-116">Right-click the subreport, and then click **Subreport Properties**.</span></span>  
  
4.  <span data-ttu-id="f9eef-117">在 **“子报表属性”** 对话框的 **“名称”** 文本框中键入名称，或接受默认值。</span><span class="sxs-lookup"><span data-stu-id="f9eef-117">In the **Subreport Properties** dialog box, type a name in the **Name** text box or accept the default.</span></span> <span data-ttu-id="f9eef-118">该名称在报表中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="f9eef-118">The name must be unique within the report.</span></span> <span data-ttu-id="f9eef-119">默认情况下，会分配一个常规名称，例如 Subreport1 或 Subreport2。</span><span class="sxs-lookup"><span data-stu-id="f9eef-119">By default, a general name such as Subreport1 or Subreport2 is assigned.</span></span>  
  
5.  <span data-ttu-id="f9eef-120">在 **“将此报表用作子报表”** 框中，单击 **“浏览”** ，或者键入报表的名称。</span><span class="sxs-lookup"><span data-stu-id="f9eef-120">In the **Use this report as a subreport** box, click **Browse**, or type the name of the report.</span></span> <span data-ttu-id="f9eef-121">应当优先单击 **“浏览”** ，因为将自动指定子报表的路径。</span><span class="sxs-lookup"><span data-stu-id="f9eef-121">Clicking **Browse** is preferred because the path to the subreport will be specified automatically.</span></span> <span data-ttu-id="f9eef-122">可以通过多种方式指定报表。</span><span class="sxs-lookup"><span data-stu-id="f9eef-122">You can specify the report in the several ways.</span></span> <span data-ttu-id="f9eef-123">有关详细信息，请参阅[指定外部项的路径（报表生成器和 SSRS）](specifying-paths-to-external-items-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f9eef-123">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
6.  <span data-ttu-id="f9eef-124">（可选）如果子报表横跨多页，针对“去掉分页符上的边框”单击“是”，就可以避免在子报表中间呈现边框   。</span><span class="sxs-lookup"><span data-stu-id="f9eef-124">(Optional) Click **Yes** for **Omit border on page break** to prevent a border from being rendered in the middle of the subreport if the subreport spans more than one page.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-specify-parameters-to-pass-to-a-subreport"></a><span data-ttu-id="f9eef-125">指定传递给子报表的参数</span><span class="sxs-lookup"><span data-stu-id="f9eef-125">To specify parameters to pass to a subreport</span></span>  
  
1.  <span data-ttu-id="f9eef-126">在“设计”视图中，右键单击子报表，然后单击“子报表属性”  。</span><span class="sxs-lookup"><span data-stu-id="f9eef-126">In Design view, right-click the subreport and then click **Subreport Properties**.</span></span>  
  
2.  <span data-ttu-id="f9eef-127">在 **“子报表属性”** 对话框中，单击 **“参数”** 。</span><span class="sxs-lookup"><span data-stu-id="f9eef-127">In the **Subreport Properties** dialog box, click **Parameters**.</span></span>  
  
3.  <span data-ttu-id="f9eef-128">单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="f9eef-128">Click **Add**.</span></span> <span data-ttu-id="f9eef-129">将向参数网格添加一个新行。</span><span class="sxs-lookup"><span data-stu-id="f9eef-129">A new row is added to the parameter grid.</span></span>  
  
4.  <span data-ttu-id="f9eef-130">在 **“名称”** 文本框中，键入子报表中参数的名称或者从列表框中选择该名称。</span><span class="sxs-lookup"><span data-stu-id="f9eef-130">In the **Name** text box, type the name of a parameter in the subreport or choose it from the list box.</span></span> <span data-ttu-id="f9eef-131">该名称必须与子报表中的报表参数的名称（而不是查询参数的名称）相匹配。</span><span class="sxs-lookup"><span data-stu-id="f9eef-131">This name must match a report parameter, not a query parameter, in the subreport.</span></span>  
  
5.  <span data-ttu-id="f9eef-132">在 **“值”** 列表框中，键入或选择要传递给子报表的值。</span><span class="sxs-lookup"><span data-stu-id="f9eef-132">In the **Value** list box, type or select a value to pass to the subreport.</span></span> <span data-ttu-id="f9eef-133">此值可以是静态文本、引用字段的表达式或主报表中的其他对象。</span><span class="sxs-lookup"><span data-stu-id="f9eef-133">This value can be static text or an expression that references a field or other object in the main report.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f9eef-134">在报表生成器中，如果“参数”列表中缺少某参数并且子报表定义了默认值，则会正确处理子报表  。</span><span class="sxs-lookup"><span data-stu-id="f9eef-134">In Report Builder, if a parameter is missing from the **Parameters** list and the subreport has a default value defined, the subreport will be processed correctly.</span></span>  
    >   
    >  <span data-ttu-id="f9eef-135">在报表设计器中，子报表所需的所有参数都必须包括在 **“参数”** 列表中。</span><span class="sxs-lookup"><span data-stu-id="f9eef-135">In Report Designer, all parameters that are required by the subreport must be included in the **Parameters** list.</span></span> <span data-ttu-id="f9eef-136">如果缺少必需的参数，子报表将不会在主报表中正确显示。</span><span class="sxs-lookup"><span data-stu-id="f9eef-136">If a required parameter is missing, the subreport is not displayed correctly in the main report.</span></span>  
  
6.  <span data-ttu-id="f9eef-137">重复步骤 3-5，以便指定每个子报表参数的名称和值。</span><span class="sxs-lookup"><span data-stu-id="f9eef-137">Repeat steps 3-5 to specify a name and value for each subreport parameter.</span></span>  
  
7.  <span data-ttu-id="f9eef-138">若要删除子报表参数，请单击参数网格中的相应参数，然后单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="f9eef-138">To delete a subreport parameter, click the parameter in the parameter grid, and then click **Delete**.</span></span>  
  
8.  <span data-ttu-id="f9eef-139">若要更改子报表参数的顺序，请单击相应参数，再单击上移按钮或下移按钮。</span><span class="sxs-lookup"><span data-stu-id="f9eef-139">To change the order of a subreport parameter, click the parameter, and then click the up button or the down button.</span></span>  
  
     <span data-ttu-id="f9eef-140">更改子报表参数的顺序不会影响子报表的处理。</span><span class="sxs-lookup"><span data-stu-id="f9eef-140">Changing the order of a subreport parameter does not affect the processing of the subreport.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9eef-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f9eef-141">See Also</span></span>  
 <span data-ttu-id="f9eef-142">[子报表（报表生成器和 SSRS）](subreports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f9eef-142">[Subreports &#40;Report Builder and SSRS&#41;](subreports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f9eef-143">呈现行为（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f9eef-143">Rendering Behaviors &#40;Report Builder  and SSRS&#41;</span></span>](rendering-behaviors-report-builder-and-ssrs.md)  
  
  
