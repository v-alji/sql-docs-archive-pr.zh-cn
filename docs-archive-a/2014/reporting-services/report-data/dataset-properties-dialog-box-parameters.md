---
title: “数据集属性”对话框 ->“参数”| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10150"
- sql12.rtp.rptdesigner.datasetproperties.parameters.f1
ms.assetid: 43b00aab-e2c3-4e85-abe1-a2b5a21efeed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0073971de373321ce347f416657671e1f497dd1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694283"
---
# <a name="dataset-properties-dialog-box-parameters"></a><span data-ttu-id="59bb9-102">“数据集属性”对话框 ->“参数”</span><span class="sxs-lookup"><span data-stu-id="59bb9-102">Dataset Properties Dialog Box, Parameters</span></span>
  <span data-ttu-id="59bb9-103">选择 **“数据集属性”** 对话框中的 **“参数”** 可以添加、更改和删除查询参数，包括链接到报表参数的查询参数。</span><span class="sxs-lookup"><span data-stu-id="59bb9-103">Select **Parameters** on the **Dataset Properties** dialog box to add, change, and delete query parameters, including query parameters that link to report parameters.</span></span>  
  
 <span data-ttu-id="59bb9-104">无论何时在查询选项卡上更改查询，都会对查询命令进行分析。</span><span class="sxs-lookup"><span data-stu-id="59bb9-104">Whenever the query is changed on the query tab, the query command is parsed.</span></span> <span data-ttu-id="59bb9-105">对标识的每个查询参数，将创建其名称完全相同且区分大小写的报表参数。</span><span class="sxs-lookup"><span data-stu-id="59bb9-105">For each query parameter that is identified, a report parameter with an identical case-sensitive name is created.</span></span> <span data-ttu-id="59bb9-106">默认情况下，查询参数将自动添加到查询参数列表中并链接到相应的报表参数。</span><span class="sxs-lookup"><span data-stu-id="59bb9-106">By default, the query parameter is automatically added to the query parameter list and linked to the corresponding report parameter.</span></span>  
  
 <span data-ttu-id="59bb9-107">如果某个报表参数的默认值与另一个链接到查询参数的报表参数存在依赖关系，则报表参数的顺序（即其在“报表参数属性”对话框中显示的顺序）十分重要  。</span><span class="sxs-lookup"><span data-stu-id="59bb9-107">If there are dependencies for the default values of one report parameter on another report parameter that is linked to a query parameter, the order of report parameters (as they appear in the **Report Parameters Properties** dialog box) is important.</span></span> <span data-ttu-id="59bb9-108">列表中后面的报表参数可以引用列表中前面的参数。</span><span class="sxs-lookup"><span data-stu-id="59bb9-108">Report parameters later in the list can refer to report parameters earlier in the list.</span></span> <span data-ttu-id="59bb9-109">有关报表参数的详细信息，请参阅 [报表参数（报表生成器和报表设计器）](../report-design/report-parameters-report-builder-and-report-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="59bb9-109">For more information about report parameters, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="59bb9-110">选项</span><span class="sxs-lookup"><span data-stu-id="59bb9-110">Options</span></span>  
 <span data-ttu-id="59bb9-111">**添加**</span><span class="sxs-lookup"><span data-stu-id="59bb9-111">**Add**</span></span>  
 <span data-ttu-id="59bb9-112">将新的参数添加到列表。</span><span class="sxs-lookup"><span data-stu-id="59bb9-112">Add a new parameter to the list.</span></span>  
  
 <span data-ttu-id="59bb9-113">**删除**</span><span class="sxs-lookup"><span data-stu-id="59bb9-113">**Delete**</span></span>  
 <span data-ttu-id="59bb9-114">从列表中删除所选参数。</span><span class="sxs-lookup"><span data-stu-id="59bb9-114">Remove the selected parameter from the list.</span></span>  
  
 <span data-ttu-id="59bb9-115">**参数名称**</span><span class="sxs-lookup"><span data-stu-id="59bb9-115">**Parameter name**</span></span>  
 <span data-ttu-id="59bb9-116">键入添加到“数据集属性”  对话框“查询”  选项卡上数据集中的查询参数的名称。</span><span class="sxs-lookup"><span data-stu-id="59bb9-116">Type the name of a query parameter that you added to the dataset on the **Query** tab of the **Dataset Properties** dialog box.</span></span>  
  
 <span data-ttu-id="59bb9-117">**参数值**</span><span class="sxs-lookup"><span data-stu-id="59bb9-117">**Parameter value**</span></span>  
 <span data-ttu-id="59bb9-118">输入查询参数的值。</span><span class="sxs-lookup"><span data-stu-id="59bb9-118">Enter a value for the query parameter.</span></span> <span data-ttu-id="59bb9-119">此值既可以是静态值，也可以是引用报表内对象的表达式（但不能引用任何报表项或字段）。</span><span class="sxs-lookup"><span data-stu-id="59bb9-119">This can be a static value or an expression that refers to an object within the report, but it cannot refer to any report items or fields.</span></span> <span data-ttu-id="59bb9-120">默认情况下， **“值”** 中包含指向报表参数的表达式。</span><span class="sxs-lookup"><span data-stu-id="59bb9-120">By default, **Value** contains an expression that points to a report parameter.</span></span>  
  
 <span data-ttu-id="59bb9-121">**向上键**</span><span class="sxs-lookup"><span data-stu-id="59bb9-121">**Up arrow**</span></span>  
 <span data-ttu-id="59bb9-122">在列表中向上移动所选的参数。</span><span class="sxs-lookup"><span data-stu-id="59bb9-122">Move the selected parameter up in the list.</span></span>  
  
 <span data-ttu-id="59bb9-123">**向下键**</span><span class="sxs-lookup"><span data-stu-id="59bb9-123">**Down arrow**</span></span>  
 <span data-ttu-id="59bb9-124">在列表中向下移动所选的参数。</span><span class="sxs-lookup"><span data-stu-id="59bb9-124">Move the selected parameter down in the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59bb9-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="59bb9-125">See Also</span></span>  
 <span data-ttu-id="59bb9-126">[报表参数（报表生成器和报表设计器）](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="59bb9-126">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="59bb9-127">[将数据添加到报表 &#40;报表生成器和 SSRS&#41;](report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="59bb9-127">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) </span></span>  
 [<span data-ttu-id="59bb9-128">更改报表参数的顺序（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="59bb9-128">Change the Order of a Report Parameter &#40;Report Builder and SSRS&#41;</span></span>](../report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)  
  
  
