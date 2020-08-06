---
title: 添加、更改或删除报表参数（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d44a8e0a-10cf-4502-9391-09743ffc9bad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 231cd51d7ed0a481f004b39a2e8819df3fc33748
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586466"
---
# <a name="add-change-or-delete-a-report-parameter-report-builder-and-ssrs"></a><span data-ttu-id="f6148-102">添加、更改或删除报表参数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f6148-102">Add, Change, or Delete a Report Parameter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f6148-103">报表参数为选择报表数据、连接相关报表以及更改报表显示提供了一种方法。</span><span class="sxs-lookup"><span data-stu-id="f6148-103">A report parameter provides a way to choose report data, connect related reports together, and vary the report presentation.</span></span> <span data-ttu-id="f6148-104">您可以提供一个默认值和一列可用值，用户可以更改所选值。</span><span class="sxs-lookup"><span data-stu-id="f6148-104">You can provide a default value and a list of available values, and the user can change the selection.</span></span>  
  
 <span data-ttu-id="f6148-105">报表发布后，您可以在报表服务器上更改报表参数的默认值、可用值以及其他属性。</span><span class="sxs-lookup"><span data-stu-id="f6148-105">After you publish a report, you can change the default values, the available values, and other properties for a report parameter on the report server.</span></span> <span data-ttu-id="f6148-106">通过创建链接报表，您可以提供多组默认参数值。</span><span class="sxs-lookup"><span data-stu-id="f6148-106">You can provide multiple sets of default parameter values by creating linked reports.</span></span> <span data-ttu-id="f6148-107">有关详细信息，请参阅位于 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SQL Server 联机丛书 [上的](https://go.microsoft.com/fwlink/?linkid=120955)文档中的“设置已发布报表的参数属性”。</span><span class="sxs-lookup"><span data-stu-id="f6148-107">For more information, see "Setting Parameter Properties for a Published Report" in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=120955).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-or-edit-a-report-parameter"></a><span data-ttu-id="f6148-108">添加或编辑报表参数</span><span class="sxs-lookup"><span data-stu-id="f6148-108">To add or edit a report parameter</span></span>  
  
1.  <span data-ttu-id="f6148-109">在 **“报表数据”** 窗格中，右键单击 **“参数”** 节点，然后单击 **“添加参数”**。</span><span class="sxs-lookup"><span data-stu-id="f6148-109">In the **Report Data** pane, right-click the **Parameters** node and click **Add Parameter**.</span></span> <span data-ttu-id="f6148-110">此时将打开 **“报表参数属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="f6148-110">The **Report Parameter Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="f6148-111">在 **“名称”** 中，键入参数的名称，或接受默认名称。</span><span class="sxs-lookup"><span data-stu-id="f6148-111">In **Name**, type the name of the parameter or accept the default name.</span></span>  
  
3.  <span data-ttu-id="f6148-112">在 **“提示”** 中，键入当用户运行报表时，参数文本框旁边将会显示的文本。</span><span class="sxs-lookup"><span data-stu-id="f6148-112">In **Prompt**, type the text that appears next to the parameter text box when the user runs the report.</span></span>  
  
4.  <span data-ttu-id="f6148-113">在 **“数据类型”** 中，选择参数值的数据类型。</span><span class="sxs-lookup"><span data-stu-id="f6148-113">In **Data type**, select the data type for the parameter value.</span></span>  
  
5.  <span data-ttu-id="f6148-114">如果参数可以包含空白值，请选择 **“允许空白值”**。</span><span class="sxs-lookup"><span data-stu-id="f6148-114">If the parameter can contain a blank value, select **Allow blank value**.</span></span>  
  
6.  <span data-ttu-id="f6148-115">如果参数可以包含 Null 值，请选择 **“允许 Null 值”**。</span><span class="sxs-lookup"><span data-stu-id="f6148-115">If the parameter can contain a null value, select **Allow null value**.</span></span>  
  
7.  <span data-ttu-id="f6148-116">若要允许用户为参数选择多个值，请选择 **“允许多个值”**。</span><span class="sxs-lookup"><span data-stu-id="f6148-116">To allow a user to select more than one value for the parameter, select **Allow multiple values**.</span></span>  
  
8.  <span data-ttu-id="f6148-117">设置可见性选项。</span><span class="sxs-lookup"><span data-stu-id="f6148-117">Set the visibility option.</span></span>  
  
    -   <span data-ttu-id="f6148-118">若要在报表顶部的工具栏中显示参数，请选择 **“可见”**。</span><span class="sxs-lookup"><span data-stu-id="f6148-118">To show the parameter on the toolbar at the top of the report, select **Visible**.</span></span>  
  
    -   <span data-ttu-id="f6148-119">若要隐藏参数使其不显示在工具栏中，请选择 **“隐藏”**。</span><span class="sxs-lookup"><span data-stu-id="f6148-119">To hide the parameter so that it does not display on the toolbar, select **Hidden**.</span></span>  
  
    -   <span data-ttu-id="f6148-120">若要隐藏参数，以保护其不会在报表发布后，被从报表服务器上修改，请选择 **“内部”**。</span><span class="sxs-lookup"><span data-stu-id="f6148-120">To hide the parameter and protect it from being modified on the report server after the report is published, select **Internal**.</span></span> <span data-ttu-id="f6148-121">这样将仅可在报表定义中查看该报表参数。</span><span class="sxs-lookup"><span data-stu-id="f6148-121">The report parameter can then only be viewed in the report definition.</span></span> <span data-ttu-id="f6148-122">对于此选项，您必须设置一个默认值，或允许参数接受 Null 值。</span><span class="sxs-lookup"><span data-stu-id="f6148-122">For this option, you must set a default value or allow the parameter to accept a null value.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-report-parameter"></a><span data-ttu-id="f6148-123">删除报表参数</span><span class="sxs-lookup"><span data-stu-id="f6148-123">To delete a report parameter</span></span>  
  
1.  <span data-ttu-id="f6148-124">在 **“报表数据”** 窗格中，展开 **“参数”** 节点。</span><span class="sxs-lookup"><span data-stu-id="f6148-124">In the **Report Data** pane, expand the **Parameters** node.</span></span>  
  
2.  <span data-ttu-id="f6148-125">右键单击报表参数，然后单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="f6148-125">Right-click the report parameter and click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6148-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f6148-126">See Also</span></span>  
 <span data-ttu-id="f6148-127">[添加、更改或删除报表参数的可用值 &#40;报表生成器和 SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md) </span><span class="sxs-lookup"><span data-stu-id="f6148-127">[Add, Change, or Delete Available Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md) </span></span>  
 <span data-ttu-id="f6148-128">[添加、更改或删除报表参数 &#40;报表生成器和 SSRS 的默认值&#41;](add-change-or-delete-default-values-for-a-report-parameter.md) </span><span class="sxs-lookup"><span data-stu-id="f6148-128">[Add, Change, or Delete Default Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-default-values-for-a-report-parameter.md) </span></span>  
 <span data-ttu-id="f6148-129">[更改报表参数 &#40;报表生成器和 SSRS 的顺序&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f6148-129">[Change the Order of a Report Parameter &#40;Report Builder and SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f6148-130">[报表参数 &#40;报表生成器和报表设计器&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="f6148-130">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="f6148-131">[报表生成器对话框、窗格和向导的帮助](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="f6148-131">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="f6148-132">[向报表添加级联参数 &#40;报表生成器和 SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f6148-132">[Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f6148-133">[教程：向报表添加参数 &#40;报表生成器&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="f6148-133">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 <span data-ttu-id="f6148-134">[教程 &#40;报表生成器&#41;](../report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="f6148-134">[Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md) </span></span>  
 <span data-ttu-id="f6148-135">[添加数据集筛选器、数据区域筛选器和组筛选器 &#40;报表生成器和 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="f6148-135">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="f6148-136">[参数集合引用 &#40;报表生成器和 SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="f6148-136">[Parameters Collection References &#40;Report Builder and SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span></span>  
 [<span data-ttu-id="f6148-137">将多值参数添加到报表</span><span class="sxs-lookup"><span data-stu-id="f6148-137">Add a multi-value parameter to a Report</span></span>](add-a-multi-value-parameter-to-a-report.md)  
  
  
