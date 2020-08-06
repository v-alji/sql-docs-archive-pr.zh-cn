---
title: 在报表中添加钻取操作（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 153729c4-d01e-4629-b78f-0cfd5a7f83da
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a429380f677a309e4e1437a2e3c5036bb4e8a455
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579999"
---
# <a name="add-a-drillthrough-action-on-a-report-report-builder-and-ssrs"></a><span data-ttu-id="f2da3-102">在报表中添加钻取操作（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f2da3-102">Add a Drillthrough Action on a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f2da3-103">单击主报表中的链接时打开的报表称为“钻取报表”  。</span><span class="sxs-lookup"><span data-stu-id="f2da3-103">The report that opens when you click the link in the main report is known as a *drillthrough report*.</span></span> <span data-ttu-id="f2da3-104">此钻取链接启用了一个钻取操作。</span><span class="sxs-lookup"><span data-stu-id="f2da3-104">This drillthrough link enables a drillthrough action.</span></span>  
  
 <span data-ttu-id="f2da3-105">钻取报表必须发布到与主报表相同的报表服务器上，但可位于不同的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f2da3-105">Drillthrough reports must be published to the same report server as the main report, but they can be in different folders.</span></span> <span data-ttu-id="f2da3-106">可以向具有 **“操作”** 属性的任何项添加钻取链接，例如文本框、图像或图表中的数据点。</span><span class="sxs-lookup"><span data-stu-id="f2da3-106">You can add a drillthrough link to any item that has an **Action** property, such as a text box, an image, or data points on a chart.</span></span>  
  
 <span data-ttu-id="f2da3-107">若要为某个报表添加钻取链接，必须首先创建主报表将链接到的钻取报表。</span><span class="sxs-lookup"><span data-stu-id="f2da3-107">To add a drillthrough link to a report, you must first create the drillthrough report that the main report will link to.</span></span> <span data-ttu-id="f2da3-108">钻取报表通常包含原始摘要报表中包含的某项的详细信息，并且经常包含一些参数，将基于从主报表传递给钻取报表的这些参数来筛选钻取报表。</span><span class="sxs-lookup"><span data-stu-id="f2da3-108">A drillthrough report commonly contains details about an item that is contained in the original summary report, and often contains parameters that filter the drillthrough report based on parameters passed to it from the main report.</span></span> <span data-ttu-id="f2da3-109">有关创建钻取报表的详细信息，请参阅[钻取报表（报表生成器和 SSRS）](drillthrough-reports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f2da3-109">For more information on creating the drillthrough report, see [Drillthrough Reports &#40;Report Builder and SSRS&#41;](drillthrough-reports-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-drillthrough-action"></a><span data-ttu-id="f2da3-110">添加钻取操作</span><span class="sxs-lookup"><span data-stu-id="f2da3-110">To add a drillthrough action</span></span>  
  
1.  <span data-ttu-id="f2da3-111">在“设计”视图中，右键单击要添加链接的文本框、图像或图表，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="f2da3-111">In Design view, right-click the text box, image, or chart to which you want to add a link and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="f2da3-112">在项的 **“属性”** 对话框中，单击 **“操作”** 。</span><span class="sxs-lookup"><span data-stu-id="f2da3-112">In the item's **Properties** dialog box, click **Action**.</span></span>  
  
3.  <span data-ttu-id="f2da3-113">选择 **“转到报表”** 。</span><span class="sxs-lookup"><span data-stu-id="f2da3-113">Select **Go to report**.</span></span> <span data-ttu-id="f2da3-114">其他部分将显示在此选项的对话框中。</span><span class="sxs-lookup"><span data-stu-id="f2da3-114">Additional sections appear in the dialog box for this option.</span></span>  
  
4.  <span data-ttu-id="f2da3-115">在 **“指定报表”** 中，单击 **“浏览”** 以查找要跳转到的报表，或键入报表的名称。</span><span class="sxs-lookup"><span data-stu-id="f2da3-115">In **Specify a report**, click **Browse** to locate the report that you want to jump to, or type the name of the report.</span></span> <span data-ttu-id="f2da3-116">也可以单击表达式 (**fx**) 按钮为该报表名创建表达式。</span><span class="sxs-lookup"><span data-stu-id="f2da3-116">Alternatively, click the expression (**fx**) button to create an expression for the report name.</span></span>  
  
     <span data-ttu-id="f2da3-117">对于本机模式和 SharePoint 集成模式，钻取报表的路径格式有所不同。</span><span class="sxs-lookup"><span data-stu-id="f2da3-117">The format of the path to the drillthrough report differs for native and SharePoint integrated mode.</span></span> <span data-ttu-id="f2da3-118">如果浏览到报表，则将提供正确格式的路径。</span><span class="sxs-lookup"><span data-stu-id="f2da3-118">If you browse to the report, a path of the correct format is provided.</span></span> <span data-ttu-id="f2da3-119">有关详细信息，请参阅[指定外部项的路径（报表生成器和 SSRS）](specifying-paths-to-external-items-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f2da3-119">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
     <span data-ttu-id="f2da3-120">如果必须为钻取报表指定参数，请执行下一个步骤。</span><span class="sxs-lookup"><span data-stu-id="f2da3-120">If you have to specify parameters for the drillthrough report, follow the next step.</span></span>  
  
5.  <span data-ttu-id="f2da3-121">在 **“使用这些参数运行报表”** 中，单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="f2da3-121">In **Use these parameters to run the report**, click **Add**.</span></span> <span data-ttu-id="f2da3-122">将向参数网格添加一个新行。</span><span class="sxs-lookup"><span data-stu-id="f2da3-122">A new row is added to the parameter grid.</span></span>  
  
    -   <span data-ttu-id="f2da3-123">在“名称”文本框中，单击下拉列表或键入钻取报表中的报表参数名称  。</span><span class="sxs-lookup"><span data-stu-id="f2da3-123">In the **Name** text box, click the drop-down list or type the name of the report parameter in the drillthrough report.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="f2da3-124">参数列表中的名称必须与目标报表中的期望参数完全匹配。</span><span class="sxs-lookup"><span data-stu-id="f2da3-124">The names in the parameter list must match the expected parameters in the target report exactly.</span></span> <span data-ttu-id="f2da3-125">例如，参数名称必须大小写格式匹配。</span><span class="sxs-lookup"><span data-stu-id="f2da3-125">For example, parameter names must match by case.</span></span> <span data-ttu-id="f2da3-126">如果名称不匹配，或者并未列出某个预期的参数，则钻取报表将出错。</span><span class="sxs-lookup"><span data-stu-id="f2da3-126">If the names do not match, or if an expected parameter is not listed, the drillthrough report fails.</span></span>  
  
    -   <span data-ttu-id="f2da3-127">在 **“值”** 中，键入或选择要传递给钻取报表中的参数的值。</span><span class="sxs-lookup"><span data-stu-id="f2da3-127">In **Value**, type or select the value to pass to the parameter in the drillthrough report.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="f2da3-128">值可以包含其计算结果将传递到报表参数的表达式。</span><span class="sxs-lookup"><span data-stu-id="f2da3-128">Values can contain an expression that evaluates to a value to pass to the report parameter.</span></span> <span data-ttu-id="f2da3-129">值列表中的表达式包括当前报表的字段列表。</span><span class="sxs-lookup"><span data-stu-id="f2da3-129">The expressions in the value list include the field list for the current report.</span></span>  
  
     <span data-ttu-id="f2da3-130">有关如何在报表中隐藏参数的信息，请参阅[添加、更改或删除报表参数（报表生成器和 SSRS）](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f2da3-130">For information on how to hide parameters in reports, see [Add, Change, or Delete a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md).</span></span>  
  
6.  <span data-ttu-id="f2da3-131">（可选）对于文本框，通过更改功能区的“主文件夹”选项卡上的文本颜色和效果有助于向用户指示该文本是一个链接  。</span><span class="sxs-lookup"><span data-stu-id="f2da3-131">(Optional) For text boxes, it is helpful to indicate to the user that the text is a link by changing the color and effect of the text on the **Home** tab of the Ribbon.</span></span>  
  
7.  <span data-ttu-id="f2da3-132">若要测试该链接，请运行报表，然后单击对其设置此链接的报表项。</span><span class="sxs-lookup"><span data-stu-id="f2da3-132">To test the link, run the report and click the report item that you set this link on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2da3-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f2da3-133">See Also</span></span>  
 <span data-ttu-id="f2da3-134">[“操作属性”对话框（报表生成器和 SSRS）](../action-properties-dialog-box-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f2da3-134">[Action Properties Dialog Box &#40;Report Builder and SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f2da3-135">[设置图表上数据点的格式（报表生成器和 SSRS）](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f2da3-135">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f2da3-136">在序列上显示工具提示（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f2da3-136">Show ToolTips on a Series &#40;Report Builder and SSRS&#41;</span></span>](show-tooltips-on-a-series-report-builder-and-ssrs.md)  
  
  
