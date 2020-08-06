---
title: "\"算法参数\" 对话框 (挖掘模型 \"视图) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.models.algorithmparameters.f1
helpviewer_keywords:
- Algorithm Parameters dialog box
ms.assetid: 57f9f6f8-8ca4-4a6e-8f18-85f0571b7060
author: minewiskan
ms.author: owend
ms.openlocfilehash: 303d8b5bd3437690c65873e106a94cf2ce8eb9f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579415"
---
# <a name="algorithm-parameters-dialog-box-mining-models-view"></a><span data-ttu-id="94e5b-102">“算法参数”对话框（“挖掘模型”视图）</span><span class="sxs-lookup"><span data-stu-id="94e5b-102">Algorithm Parameters Dialog Box (Mining Models View)</span></span>
  <span data-ttu-id="94e5b-103">可以使用 **“算法参数”** 对话框调整专用于选定模型的算法参数。</span><span class="sxs-lookup"><span data-stu-id="94e5b-103">Use the **Algorithm Parameters** dialog box to adjust algorithm parameters that are specific to the selected model.</span></span> <span data-ttu-id="94e5b-104">当更改算法参数时，将通常更改挖掘模型的结果。</span><span class="sxs-lookup"><span data-stu-id="94e5b-104">When you change an algorithm parameter, you will usually change the results of the mining model.</span></span> <span data-ttu-id="94e5b-105">每个参数对结果的影响方式取决于您使用的算法和数据。</span><span class="sxs-lookup"><span data-stu-id="94e5b-105">The way that each parameter affects the results depends on the algorithm you are using, and on your data.</span></span> <span data-ttu-id="94e5b-106">有关详细信息，请参阅 [自定义挖掘模型和结构](data-mining/customize-mining-models-and-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="94e5b-106">For more information, see [Customize Mining Models and Structure](data-mining/customize-mining-models-and-structure.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="94e5b-107">选项</span><span class="sxs-lookup"><span data-stu-id="94e5b-107">Options</span></span>  
 <span data-ttu-id="94e5b-108">**参数**</span><span class="sxs-lookup"><span data-stu-id="94e5b-108">**Parameters**</span></span>  
 <span data-ttu-id="94e5b-109">列出选定挖掘模型可用的参数。</span><span class="sxs-lookup"><span data-stu-id="94e5b-109">Lists the parameters that are available for the selected mining model.</span></span>  
  
 <span data-ttu-id="94e5b-110">下表对可用列进行了说明：</span><span class="sxs-lookup"><span data-stu-id="94e5b-110">The following list describes the available columns.</span></span>  
  
|<span data-ttu-id="94e5b-111">列</span><span class="sxs-lookup"><span data-stu-id="94e5b-111">Column</span></span>|<span data-ttu-id="94e5b-112">说明</span><span class="sxs-lookup"><span data-stu-id="94e5b-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="94e5b-113">**Parameter**</span><span class="sxs-lookup"><span data-stu-id="94e5b-113">**Parameter**</span></span>|<span data-ttu-id="94e5b-114">列出参数的名称。</span><span class="sxs-lookup"><span data-stu-id="94e5b-114">List the name of the parameter.</span></span>|  
|<span data-ttu-id="94e5b-115">**值**</span><span class="sxs-lookup"><span data-stu-id="94e5b-115">**Value**</span></span>|<span data-ttu-id="94e5b-116">仅当要更改参数的默认值时才能输入新值。</span><span class="sxs-lookup"><span data-stu-id="94e5b-116">Enter a value only if you want to change the default value of the parameter.</span></span>|  
|<span data-ttu-id="94e5b-117">**Default**</span><span class="sxs-lookup"><span data-stu-id="94e5b-117">**Default**</span></span>|<span data-ttu-id="94e5b-118">如果没有在 **“值”** 列提供值，将列出算法使用的参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="94e5b-118">List the default value of the parameter that the algorithm will use if you do not supply a value in the **Value** column.</span></span>|  
|<span data-ttu-id="94e5b-119">**范围**</span><span class="sxs-lookup"><span data-stu-id="94e5b-119">**Range**</span></span>|<span data-ttu-id="94e5b-120">列出可以在 **“值”** 列中输入的可能值的范围。</span><span class="sxs-lookup"><span data-stu-id="94e5b-120">List the range of possible values that you can enter into the **Value** column.</span></span> <span data-ttu-id="94e5b-121">范围可以是以下各项之一：</span><span class="sxs-lookup"><span data-stu-id="94e5b-121">The ranges can be one of the following:</span></span><br /><br /> <span data-ttu-id="94e5b-122">离散列表，例如1、2、3</span><span class="sxs-lookup"><span data-stu-id="94e5b-122">A discrete list, such as 1, 2, 3</span></span><br /><br /> <span data-ttu-id="94e5b-123">包含范围，例如 [0，100]</span><span class="sxs-lookup"><span data-stu-id="94e5b-123">An inclusive range, such as [0, 100]</span></span><br /><br /> <span data-ttu-id="94e5b-124">排他范围，如 (0,... ) </span><span class="sxs-lookup"><span data-stu-id="94e5b-124">An exclusive range, such as (0,...)</span></span><br /><br /> <span data-ttu-id="94e5b-125">组合，例如 [0,... ) </span><span class="sxs-lookup"><span data-stu-id="94e5b-125">A combination, such as [0,...)</span></span>|  
  
 <span data-ttu-id="94e5b-126">**说明**</span><span class="sxs-lookup"><span data-stu-id="94e5b-126">**Description**</span></span>  
 <span data-ttu-id="94e5b-127">说明在“参数”\*\*\*\* 列表中选定的参数。</span><span class="sxs-lookup"><span data-stu-id="94e5b-127">Describes the selected parameter in the **Parameters** list.</span></span>  
  
 <span data-ttu-id="94e5b-128">**添加**</span><span class="sxs-lookup"><span data-stu-id="94e5b-128">**Add**</span></span>  
 <span data-ttu-id="94e5b-129">单击此选项可以向列表中添加其他算法的特定参数。</span><span class="sxs-lookup"><span data-stu-id="94e5b-129">Click to add additional, algorithm specific-parameters to the list.</span></span> <span data-ttu-id="94e5b-130">添加参数以后，可以在 **“参数”** 列中输入正确的名称，在 **“值”** 列中提供值。</span><span class="sxs-lookup"><span data-stu-id="94e5b-130">After adding the parameter, you can enter the correct name in the **Parameter** column and provide a value in the **Value** column.</span></span>  
  
 <span data-ttu-id="94e5b-131">**移除**</span><span class="sxs-lookup"><span data-stu-id="94e5b-131">**Remove**</span></span>  
 <span data-ttu-id="94e5b-132">单击此选项可以从列表中删除自定义参数。</span><span class="sxs-lookup"><span data-stu-id="94e5b-132">Click to delete a custom parameter from the list.</span></span>  
  
 <span data-ttu-id="94e5b-133">如果从列表删除标准 Analysis Services 算法参数之一，模型仍会使用此参数，但将使用此参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="94e5b-133">If you delete one of the standard Analysis Services algorithm parameters from the list, the parameter will still be used in the model, but with the default values for that parameter.</span></span> <span data-ttu-id="94e5b-134">此参数并不会永久删除，并将在下一次打开对话框时显示。</span><span class="sxs-lookup"><span data-stu-id="94e5b-134">The parameter is not permanently deleted and will appear the next time that you open the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94e5b-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94e5b-135">See Also</span></span>  
 <span data-ttu-id="94e5b-136">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="94e5b-136">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="94e5b-137">[挖掘模型视图 &#40;数据挖掘模型设计器&#41;](mining-models-view-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="94e5b-137">[Mining Models View &#40;Data Mining Model Designer&#41;](mining-models-view-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="94e5b-138">移动数据挖掘对象</span><span class="sxs-lookup"><span data-stu-id="94e5b-138">Moving Data Mining Objects</span></span>](data-mining/moving-data-mining-objects.md)  
  
  
