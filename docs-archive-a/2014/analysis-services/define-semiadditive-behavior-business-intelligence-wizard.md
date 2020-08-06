---
title: )  (商业智能向导定义半累加性行为 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.semiadditivememberdetection.f1
ms.assetid: e57080ba-ce96-40f8-bca7-6701d1725b3c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5a3c46de038a7e45dcb39805e324260676a03228
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687355"
---
# <a name="define-semiadditive-behavior-business-intelligence-wizard"></a><span data-ttu-id="ae759-102">定义半累加行为（商业智能向导）</span><span class="sxs-lookup"><span data-stu-id="ae759-102">Define Semiadditive Behavior (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="ae759-103">可以使用“定义半累加性行为”\*\*\*\* 页启用或禁用针对度量值的半累加行为。</span><span class="sxs-lookup"><span data-stu-id="ae759-103">Use the **Define Semiadditive Behavior** page to enable or disable semi-additive behavior on measures.</span></span> <span data-ttu-id="ae759-104">半累加行为确定多维数据集所包含的度量值在一定时间维度内如何聚合。</span><span class="sxs-lookup"><span data-stu-id="ae759-104">Semi-additive behavior determines how measures that are contained by a cube are aggregated over a time dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ae759-105">除了可用于标准版本的 LastChild 之外，其他的半累加行为仅可用于商业智能或企业版本。</span><span class="sxs-lookup"><span data-stu-id="ae759-105">With the exception of LastChild which is available in the standard edition, semi-additive behaviors are only available in the business intelligence or enterprise editions.</span></span> <span data-ttu-id="ae759-106">此外，由于半累加性行为是只针对度量值而不针对维度定义的，如果从维度设计器或者通过在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]的解决方案资源管理器中右键单击维度启动了商业智能向导，将不会看到此页。</span><span class="sxs-lookup"><span data-stu-id="ae759-106">Furthermore, because semiadditive behavior is defined only on measures and not dimensions, you will not find this page in the Business Intelligence Wizard if it was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="ae759-107">选项</span><span class="sxs-lookup"><span data-stu-id="ae759-107">Options</span></span>  
 <span data-ttu-id="ae759-108">**关闭半累加性行为**</span><span class="sxs-lookup"><span data-stu-id="ae759-108">**Turn off semiadditive behavior**</span></span>  
 <span data-ttu-id="ae759-109">在多维数据集所包含的所有度量值中禁用半累加性行为。</span><span class="sxs-lookup"><span data-stu-id="ae759-109">Disables semi-additive behavior in all measures contained by the cube.</span></span>  
  
 <span data-ttu-id="ae759-110">**向导检测到 \<dimension name> 包含半累加性成员的帐户维度。服务器将根据为每种帐户类型指定的半累加性行为聚合此维度的成员。**</span><span class="sxs-lookup"><span data-stu-id="ae759-110">**The wizard has detected the \<dimension name> account dimension, which contains semiadditive members. The server will aggregate members of this dimension according to the semiadditive behavior specified for each account type.**</span></span>  
 <span data-ttu-id="ae759-111">对包含半累加性成员的帐户维度启用半累加性行为。</span><span class="sxs-lookup"><span data-stu-id="ae759-111">Enables semi-additive behavior for account dimensions that contain semi-additive members.</span></span> <span data-ttu-id="ae759-112">选择此选项将把引用该帐户维度的度量值组中所有度量值的聚合函数设置为 `ByAccount`。</span><span class="sxs-lookup"><span data-stu-id="ae759-112">Selecting this option sets the aggregation function of all measures in measure groups that reference the account dimension to `ByAccount`.</span></span>  
  
 <span data-ttu-id="ae759-113">有关帐户维度的详细信息，请参阅 [创建父子类型维度的财务帐户](multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md)。</span><span class="sxs-lookup"><span data-stu-id="ae759-113">For more information about account dimensions, see [Create a Finance Account of parent-child type Dimension](multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md).</span></span>  
  
 <span data-ttu-id="ae759-114">**为各个成员定义半累加性行为**</span><span class="sxs-lookup"><span data-stu-id="ae759-114">**Define semiadditive behavior for individual members**</span></span>  
 <span data-ttu-id="ae759-115">为特定度量值启用半累加性行为，并指定半累加性聚合函数。</span><span class="sxs-lookup"><span data-stu-id="ae759-115">Enables semi-additive behavior and specifies the semi-additive aggregation function for specific measures.</span></span> <span data-ttu-id="ae759-116">该聚合函数将应用于包含该度量值的度量值组所引用的所有维度。</span><span class="sxs-lookup"><span data-stu-id="ae759-116">The aggregation function applies to all dimensions that are referenced by the measure group that contains the measure.</span></span>  
  
 <span data-ttu-id="ae759-117">**措施**</span><span class="sxs-lookup"><span data-stu-id="ae759-117">**Measures**</span></span>  
 <span data-ttu-id="ae759-118">显示多维数据集所包含的度量值的名称。</span><span class="sxs-lookup"><span data-stu-id="ae759-118">Displays the name of a measure contained by the cube.</span></span>  
  
 <span data-ttu-id="ae759-119">**半累加性函数**</span><span class="sxs-lookup"><span data-stu-id="ae759-119">**Semiadditive Function**</span></span>  
 <span data-ttu-id="ae759-120">为所选度量值选择聚合函数。</span><span class="sxs-lookup"><span data-stu-id="ae759-120">Select the aggregation function for the selected measure.</span></span> <span data-ttu-id="ae759-121">下表列出了可用的聚合函数：</span><span class="sxs-lookup"><span data-stu-id="ae759-121">The following table lists the aggregation functions that are available.</span></span>  
  
|<span data-ttu-id="ae759-122">值</span><span class="sxs-lookup"><span data-stu-id="ae759-122">Value</span></span>|<span data-ttu-id="ae759-123">说明</span><span class="sxs-lookup"><span data-stu-id="ae759-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ae759-124">**AverageOfChildren**</span><span class="sxs-lookup"><span data-stu-id="ae759-124">**AverageOfChildren**</span></span>|<span data-ttu-id="ae759-125">通过返回度量值子成员的平均值进行聚合。</span><span class="sxs-lookup"><span data-stu-id="ae759-125">Aggregated by returning the average of the measure's children.</span></span>|  
|`ByAccount`|<span data-ttu-id="ae759-126">通过与帐户维度中属性的指定帐户类型关联的聚合函数进行聚合。</span><span class="sxs-lookup"><span data-stu-id="ae759-126">Aggregated by the aggregation function associated with the specified account type of an attribute in an account dimension.</span></span>|  
|`Count`|<span data-ttu-id="ae759-127">使用 `Count` 函数聚合。</span><span class="sxs-lookup"><span data-stu-id="ae759-127">Aggregated using the `Count` function.</span></span>|  
|`DistinctCount`|<span data-ttu-id="ae759-128">使用 `DistinctCount` 函数聚合。</span><span class="sxs-lookup"><span data-stu-id="ae759-128">Aggregated using the `DistinctCount` function.</span></span>|  
|<span data-ttu-id="ae759-129">**FirstChild**</span><span class="sxs-lookup"><span data-stu-id="ae759-129">**FirstChild**</span></span>|<span data-ttu-id="ae759-130">通过返回度量值在一定时间维度内的第一个子成员聚合。</span><span class="sxs-lookup"><span data-stu-id="ae759-130">Aggregated by returning the measure's first child member over a time dimension.</span></span>|  
|<span data-ttu-id="ae759-131">**FirstNonEmpty**</span><span class="sxs-lookup"><span data-stu-id="ae759-131">**FirstNonEmpty**</span></span>|<span data-ttu-id="ae759-132">通过返回度量值在一定时间维度内的第一个非空成员聚合。</span><span class="sxs-lookup"><span data-stu-id="ae759-132">Aggregated by returning the measure's first nonempty member over a time dimension.</span></span>|  
|<span data-ttu-id="ae759-133">**LastChild**</span><span class="sxs-lookup"><span data-stu-id="ae759-133">**LastChild**</span></span>|<span data-ttu-id="ae759-134">通过返回度量值在一定时间维度内的最后一个子成员聚合。</span><span class="sxs-lookup"><span data-stu-id="ae759-134">Aggregated by returning the measure's last child member over a time dimension.</span></span>|  
|<span data-ttu-id="ae759-135">**LastNonEmpty**</span><span class="sxs-lookup"><span data-stu-id="ae759-135">**LastNonEmpty**</span></span>|<span data-ttu-id="ae759-136">通过返回度量值在一定时间维度内的最后一个非空成员聚合。</span><span class="sxs-lookup"><span data-stu-id="ae759-136">Aggregated by returning the measure's last nonempty member over a time dimension.</span></span>|  
|`Max`|<span data-ttu-id="ae759-137">使用 `Max` 函数聚合。</span><span class="sxs-lookup"><span data-stu-id="ae759-137">Aggregated using the `Max` function.</span></span>|  
|`Min`|<span data-ttu-id="ae759-138">使用 `Min` 函数聚合。</span><span class="sxs-lookup"><span data-stu-id="ae759-138">Aggregated using the `Min` function.</span></span>|  
|<span data-ttu-id="ae759-139">**无**</span><span class="sxs-lookup"><span data-stu-id="ae759-139">**None**</span></span>|<span data-ttu-id="ae759-140">不执行聚合。</span><span class="sxs-lookup"><span data-stu-id="ae759-140">No aggregation performed.</span></span>|  
|`Sum`|<span data-ttu-id="ae759-141">使用 `Sum` 函数聚合。</span><span class="sxs-lookup"><span data-stu-id="ae759-141">Aggregated using the `Sum` function.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="ae759-142">只有在选择了“为各个成员定义半累加性行为”\*\*\*\* 之后，才会应用对此选项所做的选择。</span><span class="sxs-lookup"><span data-stu-id="ae759-142">Selections made for this option apply only if **Define semiadditive behavior for individual members** is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae759-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ae759-143">See Also</span></span>  
 <span data-ttu-id="ae759-144">[商业智能向导的 F1 帮助](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="ae759-144">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="ae759-145">[多维数据集设计器 &#40;Analysis Services 多维数据&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="ae759-145">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="ae759-146">维度设计器 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="ae759-146">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
