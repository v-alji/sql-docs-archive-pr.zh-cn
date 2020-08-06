---
title: 参数属性页 (报表管理器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ebb53598-2378-46ae-8935-d5192f8ea49a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ddaf6598225c36bd6490797e52aeb1a5fed1b60a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580047"
---
# <a name="parameters-properties-page-report-manager"></a><span data-ttu-id="46986-102">“参数”属性页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="46986-102">Parameters Properties Page (Report Manager)</span></span>
  <span data-ttu-id="46986-103">使用“参数”属性页可以查看或修改参数化报表的参数设置。</span><span class="sxs-lookup"><span data-stu-id="46986-103">Use the Parameters properties page to view or modify parameter settings for a parameterized report.</span></span>  
  
 <span data-ttu-id="46986-104">参数在发布报表之前在报表定义中进行指定。</span><span class="sxs-lookup"><span data-stu-id="46986-104">Parameters are specified in the report definition before the report is published.</span></span> <span data-ttu-id="46986-105">在发布报表后，可以修改某些参数属性值。</span><span class="sxs-lookup"><span data-stu-id="46986-105">After the report is published, you can modify some parameter property values.</span></span> <span data-ttu-id="46986-106">可以修改的值将取决于在报表中定义参数的情况。</span><span class="sxs-lookup"><span data-stu-id="46986-106">The values that you can modify will vary based on how the parameters are defined in the report.</span></span> <span data-ttu-id="46986-107">例如，如果定义了一个参数的静态值列表，就可以选择另一个静态值作为默认值，但是不能在该列表中添加值或删除该列表中的值。</span><span class="sxs-lookup"><span data-stu-id="46986-107">For example, if a list of static values is defined for a parameter, you can choose a different static value to use as a default, but you cannot add or remove values from the list.</span></span> <span data-ttu-id="46986-108">同样，如果参数基于某个查询，则该查询的所有方面（包括所使用的数据集、是否允许 Null 值或空白值以及是否提供默认值）都在发布之前在报表中进行定义。</span><span class="sxs-lookup"><span data-stu-id="46986-108">Similarly, if the parameter is based on a query, all aspects of that query (including the dataset that is used, whether null or blank values are allowed, and whether a default value is provided) are defined in the report before publication.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="46986-109">导航</span><span class="sxs-lookup"><span data-stu-id="46986-109">Navigation</span></span>  
 <span data-ttu-id="46986-110">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="46986-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-parameters-properties-page"></a><span data-ttu-id="46986-111">打开“参数”属性页</span><span class="sxs-lookup"><span data-stu-id="46986-111">To open the Parameters properties page</span></span>  
  
1.  <span data-ttu-id="46986-112">打开报表管理器，找到要修改参数设置的报表。</span><span class="sxs-lookup"><span data-stu-id="46986-112">Open Report Manager, and locate the report for which you want to modify parameter settings.</span></span>  
  
2.  <span data-ttu-id="46986-113">悬停在该报表之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="46986-113">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="46986-114">在下拉菜单中，单击 **“管理”**。</span><span class="sxs-lookup"><span data-stu-id="46986-114">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="46986-115">这会打开该报表的“常规”属性页。</span><span class="sxs-lookup"><span data-stu-id="46986-115">This opens the General properties page for the report.</span></span>  
  
4.  <span data-ttu-id="46986-116">选择 "**参数**" 选项卡。如果 "**参数**" 选项卡不可见，则该报表不包含参数。</span><span class="sxs-lookup"><span data-stu-id="46986-116">Select the **Parameters** tab. If the **Parameters** tab is not visible, the report does not contain parameters.</span></span>  
  
## <a name="options"></a><span data-ttu-id="46986-117">选项</span><span class="sxs-lookup"><span data-stu-id="46986-117">Options</span></span>  
 <span data-ttu-id="46986-118">**参数名称**</span><span class="sxs-lookup"><span data-stu-id="46986-118">**Parameter Name**</span></span>  
 <span data-ttu-id="46986-119">指定参数的名称。</span><span class="sxs-lookup"><span data-stu-id="46986-119">Specifies the name of the parameter.</span></span>  
  
 <span data-ttu-id="46986-120">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="46986-120">**Data Type**</span></span>  
 <span data-ttu-id="46986-121">指定参数的数据类型。</span><span class="sxs-lookup"><span data-stu-id="46986-121">Specifies the data type of the parameter.</span></span>  
  
 <span data-ttu-id="46986-122">**具有默认值**</span><span class="sxs-lookup"><span data-stu-id="46986-122">**Has Default**</span></span>  
 <span data-ttu-id="46986-123">选中此复选框可以指定参数是否具有默认值。</span><span class="sxs-lookup"><span data-stu-id="46986-123">Select this check box to specify whether the parameter has a default value.</span></span> <span data-ttu-id="46986-124">选中此复选框会启用 **“默认值”**。</span><span class="sxs-lookup"><span data-stu-id="46986-124">Selecting this check box enables **Default Value**.</span></span> <span data-ttu-id="46986-125">如果报表参数接受 Null 值，则还会启用 **Null** 。</span><span class="sxs-lookup"><span data-stu-id="46986-125">It also enables **Null** if the report parameter accepts null values.</span></span> <span data-ttu-id="46986-126">如果 **“具有默认值”** 处于未选中状态，则运行报表时必须隐藏默认值或者提示用户提供一个值。</span><span class="sxs-lookup"><span data-stu-id="46986-126">If **Has Default** is not selected, you must either hide the value or prompt the user to provide a value when the report runs.</span></span>  
  
 <span data-ttu-id="46986-127">**默认值**</span><span class="sxs-lookup"><span data-stu-id="46986-127">**Default Value**</span></span>  
 <span data-ttu-id="46986-128">指定参数的值。</span><span class="sxs-lookup"><span data-stu-id="46986-128">Specify a value for the parameter.</span></span> <span data-ttu-id="46986-129">若要指定默认值，则必须选中 **“具有默认值”** ，而不能选中 **Null** 。</span><span class="sxs-lookup"><span data-stu-id="46986-129">To specify a default value, **Has Default** must be selected, and **Null** must not be selected.</span></span> <span data-ttu-id="46986-130">可以通过报表定义提供默认值。</span><span class="sxs-lookup"><span data-stu-id="46986-130">A default value may be provided through the report definition.</span></span> <span data-ttu-id="46986-131">如果 **“默认值”** 由一个或多个静态值填充，则这些值都源自报表。</span><span class="sxs-lookup"><span data-stu-id="46986-131">If **Default Value** is populated with one or more static values, those values originate with the report.</span></span> <span data-ttu-id="46986-132">如果 **“默认值”** 为 **“基于查询”**，则参数值由报表中定义的查询决定。</span><span class="sxs-lookup"><span data-stu-id="46986-132">If **Default value** is **Query Based**, the parameter value is determined by a query that is defined in the report.</span></span>  
  
 <span data-ttu-id="46986-133">如果 **“默认值”** 接受值，则可以键入对于报表使用的数据处理扩展插件有效的常量或语法。</span><span class="sxs-lookup"><span data-stu-id="46986-133">If **Default Value** accepts a value, you can type a constant or syntax that is valid for the data processing extension used with the report.</span></span> <span data-ttu-id="46986-134">例如，如果数据处理扩展插件的查询语言支持通配符，就可以指定通配符作为默认值。</span><span class="sxs-lookup"><span data-stu-id="46986-134">For example, if the query language of the data processing extension supports wildcards, you can specify a wildcard character as a default value.</span></span>  
  
 <span data-ttu-id="46986-135">如果随后指定向用户显示提示符，则默认值就成为用户可以使用或修改的初始值。</span><span class="sxs-lookup"><span data-stu-id="46986-135">If you subsequently specify that a prompt be displayed to the user, the default value becomes an initial value that users can either use or modify.</span></span> <span data-ttu-id="46986-136">如果您不提示输入参数值，则该值将由运行报表的所有用户使用。</span><span class="sxs-lookup"><span data-stu-id="46986-136">If you do not prompt for a parameter value, this value is used for all users who run the report.</span></span>  
  
 <span data-ttu-id="46986-137">**Null**</span><span class="sxs-lookup"><span data-stu-id="46986-137">**Null**</span></span>  
 <span data-ttu-id="46986-138">选中此复选框可以指定 Null 作为默认值。</span><span class="sxs-lookup"><span data-stu-id="46986-138">Select this check box to specify null as the default value.</span></span> <span data-ttu-id="46986-139">Null 值表示即使用户不提供参数值，报表也会运行。</span><span class="sxs-lookup"><span data-stu-id="46986-139">A null value means that the report runs even if the user does not provide a parameter value.</span></span> <span data-ttu-id="46986-140">如果此栏中没有复选框，则参数不接受 Null 值。</span><span class="sxs-lookup"><span data-stu-id="46986-140">If there is no check box in this column, the parameter does not accept null values.</span></span>  
  
 <span data-ttu-id="46986-141">**Hide**</span><span class="sxs-lookup"><span data-stu-id="46986-141">**Hide**</span></span>  
 <span data-ttu-id="46986-142">选中此复选框可以隐藏显示在报表顶部的参数区域中的参数。</span><span class="sxs-lookup"><span data-stu-id="46986-142">Select this check box to hide the parameter in the parameter area that appears at the top of the report.</span></span> <span data-ttu-id="46986-143">此参数仍将出现在订阅定义页中并且仍在报表 URL 上指定。</span><span class="sxs-lookup"><span data-stu-id="46986-143">The parameter will still appear in subscription definition pages and it can still be specified on a report URL.</span></span> <span data-ttu-id="46986-144">如果希望始终用指定的默认值运行报表，隐藏参数会很有用。</span><span class="sxs-lookup"><span data-stu-id="46986-144">Hiding the parameter is useful when you want to always run the report with a default value that you specify.</span></span>  
  
 <span data-ttu-id="46986-145">如果希望参数显示在报表中，请清除此复选框。</span><span class="sxs-lookup"><span data-stu-id="46986-145">Clear this check box if you want the parameter to be visible in the report.</span></span>  
  
 <span data-ttu-id="46986-146">**提示用户**</span><span class="sxs-lookup"><span data-stu-id="46986-146">**Prompt User**</span></span>  
 <span data-ttu-id="46986-147">选中此复选框可以显示提示用户输入参数值的文本框。</span><span class="sxs-lookup"><span data-stu-id="46986-147">Select this check box to display a text box that prompts users for a parameter value.</span></span>  
  
 <span data-ttu-id="46986-148">在下列情况下，请清除此复选框：希望在无人参与模式下运行报表（例如，生成报表历史或报表执行快照）、希望所有用户都使用同一参数值，或者不要求用户输入该值。</span><span class="sxs-lookup"><span data-stu-id="46986-148">Clear this check box if you want to run the report in unattended mode (for example, to generate report history or report execution snapshots), if you want to use the same parameter value for all users, or if you do not require user input for the value.</span></span>  
  
 <span data-ttu-id="46986-149">**显示文本**</span><span class="sxs-lookup"><span data-stu-id="46986-149">**Display Text**</span></span>  
 <span data-ttu-id="46986-150">提供显示在参数文本框旁边的文本字符串。</span><span class="sxs-lookup"><span data-stu-id="46986-150">Provide a text string that appears next to the parameter text box.</span></span> <span data-ttu-id="46986-151">此字符串提供标签或说明性文字。</span><span class="sxs-lookup"><span data-stu-id="46986-151">This string provides a label or descriptive text.</span></span> <span data-ttu-id="46986-152">字符串长度没有限制。</span><span class="sxs-lookup"><span data-stu-id="46986-152">There is no limit on string length.</span></span> <span data-ttu-id="46986-153">较长的文本字符串在所提供的空间中会换行显示。</span><span class="sxs-lookup"><span data-stu-id="46986-153">Longer text strings wrap within the space provided.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46986-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="46986-154">See Also</span></span>  
 <span data-ttu-id="46986-155">[报表 &#40;报表管理器的 "常规属性" 页&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="46986-155">[General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span></span>  
 [<span data-ttu-id="46986-156">报表管理器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="46986-156">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
