---
title: 定义半累加性行为 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- semiadditive
- Business Intelligence enhancements [Analysis Services], semiadditive behavior
- measures [Analysis Services], semiadditive
ms.assetid: b25726bc-728b-4601-ad87-9015c39dc615
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9c2028c350046fdcc9f98bcd0f0612d6a91ccabb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587081"
---
# <a name="define-semiadditive-behavior"></a><span data-ttu-id="ebacc-102">定义半累加性行为</span><span class="sxs-lookup"><span data-stu-id="ebacc-102">Define Semiadditive Behavior</span></span>
  <span data-ttu-id="ebacc-103">在很多业务方案中，半累加性度量值是非常常见的，它不在所有维度中统一进行聚合。</span><span class="sxs-lookup"><span data-stu-id="ebacc-103">Semiadditive measures, which do not uniformly aggregate across all dimensions, are very common in many business scenarios.</span></span> <span data-ttu-id="ebacc-104">每个基于余额快照的多维数据集都会随着时间的推移而出现此问题。</span><span class="sxs-lookup"><span data-stu-id="ebacc-104">Every cube that is based on snapshots of balances over time exhibits this problem.</span></span> <span data-ttu-id="ebacc-105">您可以在用于处理证券、帐户余额、预算、人力资源、保险策略和法律事务以及很多其他业务领域的应用程序中找到这些快照。</span><span class="sxs-lookup"><span data-stu-id="ebacc-105">You can find these snapshots in applications dealing with securities, account balances, budgeting, human resources, insurance policies and claims, and many other business domains.</span></span>  
  
 <span data-ttu-id="ebacc-106">通过在多维数据集中添加半累加性行为，可以为帐户类型属性的单个度量值或成员定义聚合方法。</span><span class="sxs-lookup"><span data-stu-id="ebacc-106">Add semiadditive behavior to a cube to define an aggregation method for individual measures or members of the account type attribute.</span></span> <span data-ttu-id="ebacc-107">如果多维数据集包含帐户维度，那么您可以基于该帐户类型来自动设置半累加性行为。</span><span class="sxs-lookup"><span data-stu-id="ebacc-107">If the cube contains an account dimension, you can automatically set semiadditive behavior based on the account type.</span></span>  
  
 <span data-ttu-id="ebacc-108">若要添加半累加性行为，请在多维数据集设计器中打开一个多维数据集，并从“多维数据集”菜单中选择 **“添加商业智能”** 。</span><span class="sxs-lookup"><span data-stu-id="ebacc-108">To add semiadditive behavior, open a cube in Cube Designer and choose **Add Business Intelligence** from the Cube menu.</span></span> <span data-ttu-id="ebacc-109">在商业智能向导中，选择 **“选择增强功能”** 页上的 **“定义半累加性行为”** 选项。</span><span class="sxs-lookup"><span data-stu-id="ebacc-109">In the Business Intelligence Wizard, select the **Define semiadditive behavior** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="ebacc-110">然后，此向导将引导您完成相应的步骤，以标识哪些度量值有半累加性行为。</span><span class="sxs-lookup"><span data-stu-id="ebacc-110">This wizard then guides you through the steps of identifying which measures have semiadditive behavior.</span></span>  
  
 <span data-ttu-id="ebacc-111">除了可用于标准版本的 LastChild 之外，其他的半累加行为仅可用于商业智能或企业版本。</span><span class="sxs-lookup"><span data-stu-id="ebacc-111">With the exception of LastChild which is available in the standard edition, semi-additive behaviors are only available in the business intelligence or enterprise editions.</span></span>  
  
## <a name="define-semiadditive-behavior"></a><span data-ttu-id="ebacc-112">定义半累加性行为</span><span class="sxs-lookup"><span data-stu-id="ebacc-112">Define Semiadditive Behavior</span></span>  
 <span data-ttu-id="ebacc-113">在向导的 **“定义半累加性行为”** 页上，通过选择下列选项之一来选择如何定义半累加性：</span><span class="sxs-lookup"><span data-stu-id="ebacc-113">On the **Define Semiadditive Behavior** page of the wizard, you select how to define semiadditivity by selecting one of the following options:</span></span>  
  
 <span data-ttu-id="ebacc-114">**关闭半累加性行为**</span><span class="sxs-lookup"><span data-stu-id="ebacc-114">**Turn off semiadditive behavior**</span></span>  
 <span data-ttu-id="ebacc-115">从先前定义了半累加性行为的多维数据集中删除半累加性行为。</span><span class="sxs-lookup"><span data-stu-id="ebacc-115">Removes semiadditive behavior from a cube in which semiadditive behavior was previously defined.</span></span> <span data-ttu-id="ebacc-116">如果将它设置为以下聚合函数类型中的任何一个，则该选择将使度量值重置为 `SUM`：</span><span class="sxs-lookup"><span data-stu-id="ebacc-116">This selection resets a measure to `SUM` if it is set to any of the following aggregation function types:</span></span>  
  
-   <span data-ttu-id="ebacc-117">By Account</span><span class="sxs-lookup"><span data-stu-id="ebacc-117">By Account</span></span>  
  
-   <span data-ttu-id="ebacc-118">Average of Children</span><span class="sxs-lookup"><span data-stu-id="ebacc-118">Average of Children</span></span>  
  
-   <span data-ttu-id="ebacc-119">First Child</span><span class="sxs-lookup"><span data-stu-id="ebacc-119">First Child</span></span>  
  
-   <span data-ttu-id="ebacc-120">Last Child</span><span class="sxs-lookup"><span data-stu-id="ebacc-120">Last Child</span></span>  
  
-   <span data-ttu-id="ebacc-121">Last Nonempty Child</span><span class="sxs-lookup"><span data-stu-id="ebacc-121">Last Nonempty Child</span></span>  
  
-   <span data-ttu-id="ebacc-122">First Nonempty Child</span><span class="sxs-lookup"><span data-stu-id="ebacc-122">First Nonempty Child</span></span>  
  
-   <span data-ttu-id="ebacc-123">无</span><span class="sxs-lookup"><span data-stu-id="ebacc-123">None</span></span>  
  
 <span data-ttu-id="ebacc-124">此选项不会更改使用常规聚合函数的度量值： `Sum` 、 `Min` 、 `Max` 、 `Count` 或 `Distinct``Count` 。</span><span class="sxs-lookup"><span data-stu-id="ebacc-124">This option does not change measures with a regular aggregation function: `Sum`, `Min`, `Max`, `Count`, or `Distinct``Count`.</span></span>  
  
 <span data-ttu-id="ebacc-125">**向导检测到包含半累加性成员的 "账户" 帐户维度。服务器将根据为每种帐户类型指定的半累加性行为聚合此维度的成员。**</span><span class="sxs-lookup"><span data-stu-id="ebacc-125">**The wizard has detected the 'Account" account dimension, which contains semiadditive members. The server will aggregate members of this dimension according to the semiadditive behavior specified for each account type.**</span></span>  
 <span data-ttu-id="ebacc-126">导致系统将按“帐户”类型维度进行维度化的度量值组中的所有度量值设置为“按帐户”聚合函数，并且服务器将根据为每个帐户类型指定的半累加性行为聚合此维度的成员。</span><span class="sxs-lookup"><span data-stu-id="ebacc-126">Causes the system to set all measures from a measure group dimensioned by an Account type dimension to the By Account aggregation function and the server will aggregate members of the dimension according to the semiadditive behavior specified for each account type.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebacc-127">如果向导检测到“帐户”类型维度，则默认情况下选择此选项。</span><span class="sxs-lookup"><span data-stu-id="ebacc-127">This option is selected by default if the wizard detects an Account type dimension.</span></span>  
  
 <span data-ttu-id="ebacc-128">**定义各个度量值的半累加性行为**</span><span class="sxs-lookup"><span data-stu-id="ebacc-128">**Define semiadditive behavior for individual measures**</span></span>  
 <span data-ttu-id="ebacc-129">逐个选择每个度量值的半累加性行为。</span><span class="sxs-lookup"><span data-stu-id="ebacc-129">Selects the semiadditive behavior of each measure individually.</span></span> <span data-ttu-id="ebacc-130">默认设置是 `SUM` （完全累加）。</span><span class="sxs-lookup"><span data-stu-id="ebacc-130">The default setting is `SUM` (fully additive).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebacc-131">如果向导没有检测到“帐户”类型维度，则默认情况下选择此选项。</span><span class="sxs-lookup"><span data-stu-id="ebacc-131">This option is selected by default if the wizard does not detect an Account type dimension.</span></span>  
  
 <span data-ttu-id="ebacc-132">对于每个度量值，可以从下表所描述的半累加性功能类型中进行选择。</span><span class="sxs-lookup"><span data-stu-id="ebacc-132">For each measure, you can select from the types of semiadditive functionality described in the following table.</span></span>  
  
|<span data-ttu-id="ebacc-133">半累加性函数</span><span class="sxs-lookup"><span data-stu-id="ebacc-133">Semiadditive function</span></span>|<span data-ttu-id="ebacc-134">说明</span><span class="sxs-lookup"><span data-stu-id="ebacc-134">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="ebacc-135">Average of Children</span><span class="sxs-lookup"><span data-stu-id="ebacc-135">Average of Children</span></span>|<span data-ttu-id="ebacc-136">成员的聚合是其子级的平均。</span><span class="sxs-lookup"><span data-stu-id="ebacc-136">The aggregation of a member is the average of its children.</span></span>|  
|<span data-ttu-id="ebacc-137">ByAccount</span><span class="sxs-lookup"><span data-stu-id="ebacc-137">ByAccount</span></span>|<span data-ttu-id="ebacc-138">系统读取为帐户类型指定的半累加性行为。</span><span class="sxs-lookup"><span data-stu-id="ebacc-138">The system reads the semiadditive behavior specified for the account type.</span></span>|  
|<span data-ttu-id="ebacc-139">计数</span><span class="sxs-lookup"><span data-stu-id="ebacc-139">Count</span></span>|<span data-ttu-id="ebacc-140">聚合是成员的计数。</span><span class="sxs-lookup"><span data-stu-id="ebacc-140">The aggregation is a count of members.</span></span>|  
|<span data-ttu-id="ebacc-141">Distinct Count</span><span class="sxs-lookup"><span data-stu-id="ebacc-141">Distinct Count</span></span>|<span data-ttu-id="ebacc-142">聚合是唯一成员的计数。</span><span class="sxs-lookup"><span data-stu-id="ebacc-142">The aggregation is a count of unique members.</span></span>|  
|<span data-ttu-id="ebacc-143">First Child</span><span class="sxs-lookup"><span data-stu-id="ebacc-143">First Child</span></span>|<span data-ttu-id="ebacc-144">将成员值认定为其沿时间维度的第一个子级的值。</span><span class="sxs-lookup"><span data-stu-id="ebacc-144">The member value is evaluated as the value of its first child along the time dimension.</span></span>|  
|<span data-ttu-id="ebacc-145">FirstNonEmpty</span><span class="sxs-lookup"><span data-stu-id="ebacc-145">FirstNonEmpty</span></span>|<span data-ttu-id="ebacc-146">将成员值认定为其包含数据的沿时间维度的第一个子级的值。</span><span class="sxs-lookup"><span data-stu-id="ebacc-146">The member value is evaluated as the value of its first child along the time dimension that contains data.</span></span>|  
|<span data-ttu-id="ebacc-147">LastChild</span><span class="sxs-lookup"><span data-stu-id="ebacc-147">LastChild</span></span>|<span data-ttu-id="ebacc-148">将成员值认定为其沿时间维度的最后一个子级的值。</span><span class="sxs-lookup"><span data-stu-id="ebacc-148">The member value is evaluated as the value of its last child along the time dimension.</span></span>|  
|<span data-ttu-id="ebacc-149">LastNonEmpty</span><span class="sxs-lookup"><span data-stu-id="ebacc-149">LastNonEmpty</span></span>|<span data-ttu-id="ebacc-150">将成员值认定为其包含数据的沿时间维度的最后一个子级的值。</span><span class="sxs-lookup"><span data-stu-id="ebacc-150">The member value is evaluated as the value of its last child along the time dimension that contains data.</span></span>|  
|<span data-ttu-id="ebacc-151">最大值</span><span class="sxs-lookup"><span data-stu-id="ebacc-151">Max</span></span>|<span data-ttu-id="ebacc-152">应用标准的最大值聚合函数。</span><span class="sxs-lookup"><span data-stu-id="ebacc-152">The standard maximum aggregation function is applied.</span></span>|  
|<span data-ttu-id="ebacc-153">最小值</span><span class="sxs-lookup"><span data-stu-id="ebacc-153">Min</span></span>|<span data-ttu-id="ebacc-154">应用标准的最小值聚合函数。</span><span class="sxs-lookup"><span data-stu-id="ebacc-154">The standard minimum aggregation function is applied.</span></span>|  
|<span data-ttu-id="ebacc-155">无</span><span class="sxs-lookup"><span data-stu-id="ebacc-155">None</span></span>|<span data-ttu-id="ebacc-156">不应用聚合。</span><span class="sxs-lookup"><span data-stu-id="ebacc-156">No aggregation is applied.</span></span>|  
|<span data-ttu-id="ebacc-157">Sum</span><span class="sxs-lookup"><span data-stu-id="ebacc-157">Sum</span></span>|<span data-ttu-id="ebacc-158">应用标准的求和函数。</span><span class="sxs-lookup"><span data-stu-id="ebacc-158">The standard summation function is applied.</span></span>|  
  
 <span data-ttu-id="ebacc-159">完成向导时，将覆盖任何现有的半累加性行为。</span><span class="sxs-lookup"><span data-stu-id="ebacc-159">Any existing semiadditive behavior is overwritten when you complete the wizard.</span></span>  
  
  
