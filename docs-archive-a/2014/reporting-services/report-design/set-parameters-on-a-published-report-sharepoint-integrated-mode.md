---
title: 在 SharePoint 集成模式下 (Reporting Services 上设置已发布报表的参数) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], content management
- report parameters [Reporting Services]
ms.assetid: dec5d985-a6c1-4dd8-8a66-a848e89a2e18
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4d0a2b1a23f382adb9e0cdddbebcded0050d34bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577277"
---
# <a name="set-parameters-on-a-published-report-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="dcab5-102">设置已发布报表的参数（SharePoint 集成模式下的 Reporting Services）</span><span class="sxs-lookup"><span data-stu-id="dcab5-102">Set Parameters on a Published Report (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="dcab5-103">参数化报表可以在运行报表时接受用于筛选数据的输入值。</span><span class="sxs-lookup"><span data-stu-id="dcab5-103">A parameterized report is a report that accepts input values that are used to filter data when you run the report.</span></span> <span data-ttu-id="dcab5-104">参数是在创建报表时定义的。</span><span class="sxs-lookup"><span data-stu-id="dcab5-104">Parameters are defined when the report is created.</span></span> <span data-ttu-id="dcab5-105">根据报表定义中报表参数的定义方式，参数可以接受单值、多值或者根据上一选择而变化的动态值（例如，选择产品类别后，下一选择可能是该类别中的特定产品）。</span><span class="sxs-lookup"><span data-stu-id="dcab5-105">Depending on how a report parameter is defined in the report definition, it can accept a single value, multiple values, or dynamic values, which change in response to a previous selection (for example, when you select product category, your next selection might be a specific product from that category).</span></span> <span data-ttu-id="dcab5-106">参数可以具有默认值，该值可用于自动运行经过筛选的报表，也可以由不同的值来代替。</span><span class="sxs-lookup"><span data-stu-id="dcab5-106">A parameter can have a default value, which can be used to run a filtered version of the report automatically or possibly be replaced with a different value.</span></span>  
  
 <span data-ttu-id="dcab5-107">这些属性可在报表定义中设置，也可以在报表发布后设置。</span><span class="sxs-lookup"><span data-stu-id="dcab5-107">These properties can be set in the report definition, or after the report is published.</span></span> <span data-ttu-id="dcab5-108">虽然可以在已发布报表中修改某些参数属性以更改值和显示属性，但是不能更改参数名或数据类型。</span><span class="sxs-lookup"><span data-stu-id="dcab5-108">Although you can modify some parameter properties in a published to change the value and display properties, you cannot change a parameter name or the data type.</span></span> <span data-ttu-id="dcab5-109">参数名称和数据类型只能由报表作者在报表定义中更改。</span><span class="sxs-lookup"><span data-stu-id="dcab5-109">The parameter name and data type can only be changed by the report author in the report definition.</span></span>  
  
 <span data-ttu-id="dcab5-110">若要运行参数化报表，通常必须知道要键入哪些值（尽管报表可能包含用于从中选择有效值的下拉列表）。</span><span class="sxs-lookup"><span data-stu-id="dcab5-110">To run a parameterized report, you typically must know which values to type, although a report might include drop-down lists of valid values from which to choose.</span></span>  
  
 <span data-ttu-id="dcab5-111">若要设置已发布报表的参数属性，必须拥有报表的“编辑项”权限。</span><span class="sxs-lookup"><span data-stu-id="dcab5-111">To set parameter properties on a published report, you must have Edit Items permission for the report.</span></span> <span data-ttu-id="dcab5-112">对于通过 SharePoint 站点运行的报表，您可以设置其部分或全部参数属性。</span><span class="sxs-lookup"><span data-stu-id="dcab5-112">You can modify some or all of the parameter properties on a report that you run from a SharePoint site.</span></span> <span data-ttu-id="dcab5-113">不可以通过保存希望重复使用的参数值组合来对报表进行个性化设置。</span><span class="sxs-lookup"><span data-stu-id="dcab5-113">You cannot personalize a report by saving a combination of parameter values that you want to use repeatedly.</span></span> <span data-ttu-id="dcab5-114">您指定的任何默认值都将由打开报表的所有用户使用。</span><span class="sxs-lookup"><span data-stu-id="dcab5-114">Any default values that you specify are used by all users who open the report.</span></span>  
  
 <span data-ttu-id="dcab5-115">如果报表嵌入报表查看器 Web 部件中，并且此部件已配置为始终显示该报表，则可以设置报表查看器 Web 部件的属性。</span><span class="sxs-lookup"><span data-stu-id="dcab5-115">If the report is embedded in a Report Viewer Web part that is configured to always show that report, set the properties on the Report Viewer Web Part.</span></span> <span data-ttu-id="dcab5-116">有关详细信息，请参阅[将报表查看器 Web 部件添加到网页（SharePoint 集成模式下的 Reporting Services）](../report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)。</span><span class="sxs-lookup"><span data-stu-id="dcab5-116">For more information, see [Add the Report Viewer Web Part to a Web Page &#40;Reporting Services in SharePoint Integrated Mode&#41;](../report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md).</span></span>  
  
### <a name="to-run-a-parameterized-report"></a><span data-ttu-id="dcab5-117">运行参数化报表</span><span class="sxs-lookup"><span data-stu-id="dcab5-117">To run a parameterized report</span></span>  
  
1.  <span data-ttu-id="dcab5-118">打开包含该报表的库。</span><span class="sxs-lookup"><span data-stu-id="dcab5-118">Open the library that contains the report.</span></span>  
  
2.  <span data-ttu-id="dcab5-119">单击报表名称。</span><span class="sxs-lookup"><span data-stu-id="dcab5-119">Click the report name.</span></span> <span data-ttu-id="dcab5-120">您必须事先知道哪些报表具有参数。</span><span class="sxs-lookup"><span data-stu-id="dcab5-120">You must know in advance which reports have parameters.</span></span> <span data-ttu-id="dcab5-121">报表没有表明它是参数化报表的可视标识符。</span><span class="sxs-lookup"><span data-stu-id="dcab5-121">There is no visual identifier on the report to indicate that it is parameterized.</span></span>  
  
3.  <span data-ttu-id="dcab5-122">打开报表时，指定要使用的参数。</span><span class="sxs-lookup"><span data-stu-id="dcab5-122">When the report opens, specify the parameters you want to use.</span></span> <span data-ttu-id="dcab5-123">参数区域可能处于可见、折叠或隐藏状态，具体取决于对报表查看器 Web 部件的属性设置。</span><span class="sxs-lookup"><span data-stu-id="dcab5-123">The Parameters area might be visible, collapsed, or hidden depending on how properties are set on the Report Viewer Web Part.</span></span>  
  
    1.  <span data-ttu-id="dcab5-124">如果参数区域可见，则为每个参数选择一个值。</span><span class="sxs-lookup"><span data-stu-id="dcab5-124">If the Parameters area is visible, choose a value for each parameter.</span></span>  
  
    2.  <span data-ttu-id="dcab5-125">如果沿报表长度有一条细的彩条且中间带有箭头，则表明参数区域处于折叠状态。</span><span class="sxs-lookup"><span data-stu-id="dcab5-125">If there is a thin strip of color that runs down the length of the report that has an arrow in the middle of it, the Parameters area is collapsed.</span></span> <span data-ttu-id="dcab5-126">可以单击箭头将其展开。</span><span class="sxs-lookup"><span data-stu-id="dcab5-126">You can click the arrow to expand it.</span></span>  
  
    3.  <span data-ttu-id="dcab5-127">如果参数区域是隐藏的，则不能指定值。</span><span class="sxs-lookup"><span data-stu-id="dcab5-127">If the Parameters area is hidden, you cannot specify a value.</span></span>  
  
4.  <span data-ttu-id="dcab5-128">单击参数区域底部的 **“应用”** 以运行报表。</span><span class="sxs-lookup"><span data-stu-id="dcab5-128">Click **Apply** at the bottom of the Parameters area to run the report.</span></span>  
  
     <span data-ttu-id="dcab5-129">指定的值组合可能无法让您获得所需的结果。</span><span class="sxs-lookup"><span data-stu-id="dcab5-129">It is possible to specify a combination of values that do not give you the results you expect.</span></span> <span data-ttu-id="dcab5-130">如果您无法获得所需信息，则报表作者可能需要修改报表。</span><span class="sxs-lookup"><span data-stu-id="dcab5-130">The report might need to be modified by the report author if you are not getting the information you require.</span></span>  
  
5.  <span data-ttu-id="dcab5-131">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="dcab5-131">Click **OK**.</span></span>  
  
### <a name="to-set-parameter-properties"></a><span data-ttu-id="dcab5-132">设置参数属性</span><span class="sxs-lookup"><span data-stu-id="dcab5-132">To set parameter properties</span></span>  
  
1.  <span data-ttu-id="dcab5-133">打开包含报表的库或文件夹。</span><span class="sxs-lookup"><span data-stu-id="dcab5-133">Open the library or folder that contains the report.</span></span>  
  
2.  <span data-ttu-id="dcab5-134">指向报表，然后单击向下箭头。</span><span class="sxs-lookup"><span data-stu-id="dcab5-134">Point to the report and click the down arrow.</span></span>  
  
3.  <span data-ttu-id="dcab5-135">单击 **“管理参数”** 。</span><span class="sxs-lookup"><span data-stu-id="dcab5-135">Click **Manage Parameters**.</span></span> <span data-ttu-id="dcab5-136">如果报表包含参数，页面上将列出每个参数。</span><span class="sxs-lookup"><span data-stu-id="dcab5-136">If the report contains parameters, each parameter will be listed on the page.</span></span> <span data-ttu-id="dcab5-137">此列表显示参数名称、数据类型、默认情况下使用的数据值以及打开报表时参数在参数区域中是否可见。</span><span class="sxs-lookup"><span data-stu-id="dcab5-137">The list shows the parameter name, data type, data value that is used by default, and whether it is visible in the parameter area when you open the report.</span></span>  
  
4.  <span data-ttu-id="dcab5-138">单击列表中的参数可修改其设置。</span><span class="sxs-lookup"><span data-stu-id="dcab5-138">Click a parameter in the list to modify its settings.</span></span>  
  
5.  <span data-ttu-id="dcab5-139">在“默认值”中，为参数输入值。</span><span class="sxs-lookup"><span data-stu-id="dcab5-139">In Default Value, enter a value for the parameter.</span></span> <span data-ttu-id="dcab5-140">系统不会验证该值，因此请确保提供的值对于报表是有效的。</span><span class="sxs-lookup"><span data-stu-id="dcab5-140">The value will not be validated, so be sure that you are providing a value that works for the report.</span></span>  
  
    1.  <span data-ttu-id="dcab5-141">如果希望使用创建报表时定义的默认值，请选择 **“使用报表定义中指定的值表达式”** 。</span><span class="sxs-lookup"><span data-stu-id="dcab5-141">Choose **Use value expression specified in report definition** if you want to use the default value that was defined when the report was created.</span></span> <span data-ttu-id="dcab5-142">如果报表定义没有提供默认值，此选项将不可用。</span><span class="sxs-lookup"><span data-stu-id="dcab5-142">If the report definition does not provide a default value, this option will be unavailable.</span></span>  
  
    2.  <span data-ttu-id="dcab5-143">如果希望指定一个报表定义默认值的替换值，请选择 **“覆盖报表默认值”** 。</span><span class="sxs-lookup"><span data-stu-id="dcab5-143">Choose **Override the report default value** if you want to specify a replacement for the report definition default value.</span></span> <span data-ttu-id="dcab5-144">（可选）对于接受 Null 值的报表参数，可以选中 **Null** 复选框以防止基于该参数进行筛选。</span><span class="sxs-lookup"><span data-stu-id="dcab5-144">Optionally, for report parameters that accept null values, you can select the **Null** check box to prevent filtering based on that parameter.</span></span>  
  
    3.  <span data-ttu-id="dcab5-145">如果希望在处理报表前由每个用户来指定值，请选择 **“参数没有默认值”** 。</span><span class="sxs-lookup"><span data-stu-id="dcab5-145">Choose **Parameter does not have a default value** if you want each user to specify a value before the report is processed.</span></span> <span data-ttu-id="dcab5-146">如果选择此选项，则应设定提示用户指定值的显示设置。</span><span class="sxs-lookup"><span data-stu-id="dcab5-146">If you select this option, you should set display settings that prompt the user to specify a value.</span></span>  
  
     <span data-ttu-id="dcab5-147">请注意，如果所有参数值都具有默认值，当用户打开报表时，报表将使用这些值自动运行。</span><span class="sxs-lookup"><span data-stu-id="dcab5-147">Note that if all parameter values have a default value, the report will automatically run with those values when the user opens the report.</span></span> <span data-ttu-id="dcab5-148">但是，如果显示了参数区域，用户可以覆盖默认值并重新运行报表。</span><span class="sxs-lookup"><span data-stu-id="dcab5-148">However, if the parameter area is displayed, users can override the default value and re-run the report.</span></span>  
  
6.  <span data-ttu-id="dcab5-149">设置显示选项以确定参数是否可见。</span><span class="sxs-lookup"><span data-stu-id="dcab5-149">Set display options to determine whether the parameter is visible.</span></span>  
  
    1.  <span data-ttu-id="dcab5-150">选择 **“提示用户”** 以在页面上显示参数。</span><span class="sxs-lookup"><span data-stu-id="dcab5-150">Choose **Prompt User** to show the parameter on the page.</span></span> <span data-ttu-id="dcab5-151">您可以指定出现在字段中的提示文本，以提供有关用户必须提供的数据格式或类型的简短说明。</span><span class="sxs-lookup"><span data-stu-id="dcab5-151">You can specify prompt text that appears within a field to provide a brief statement about the format or type of data that the user must provide.</span></span>  
  
    2.  <span data-ttu-id="dcab5-152">如果使用默认值且不希望在参数区域中显示参数，请选择 **“隐藏”** 。</span><span class="sxs-lookup"><span data-stu-id="dcab5-152">Choose **Hidden** if you are using a default value and you do not want the parameter to be visible in the Parameters area.</span></span>  
  
    3.  <span data-ttu-id="dcab5-153">如果使用默认值且不希望在参数区域中或订阅页上显示参数，请选择 **“内部”** 。</span><span class="sxs-lookup"><span data-stu-id="dcab5-153">Choose **Internal** if you are using a default value and you do not want the parameter to be visible in the Parameters area or on subscription pages.</span></span>  
  
7.  <span data-ttu-id="dcab5-154">单击“应用”  。</span><span class="sxs-lookup"><span data-stu-id="dcab5-154">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcab5-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dcab5-155">See Also</span></span>  
 [<span data-ttu-id="dcab5-156">报表服务器项的 SharePoint 站点和列表权限参考</span><span class="sxs-lookup"><span data-stu-id="dcab5-156">SharePoint Site and List Permission Reference for Report Server Items</span></span>](../security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)  
  
  
