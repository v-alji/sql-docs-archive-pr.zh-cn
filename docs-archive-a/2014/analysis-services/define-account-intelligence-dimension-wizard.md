---
title: 定义帐户智能 (维度向导) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.accountintelligencetypemapping.f1
ms.assetid: cbcff072-3a7e-4e98-858f-1b4265461561
author: minewiskan
ms.author: owend
ms.openlocfilehash: 90871e2299d1531db1b678b1f4b16ddd7f1db767
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588751"
---
# <a name="define-account-intelligence-dimension-wizard"></a><span data-ttu-id="450b6-102">定义帐户智能（维度向导）</span><span class="sxs-lookup"><span data-stu-id="450b6-102">Define Account Intelligence (Dimension Wizard)</span></span>
  <span data-ttu-id="450b6-103">可以使用 **“定义帐户智能”** 页，将 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例中定义的帐户类型映射到与维度中的 **“帐户类型”** 属性类型关联的维度属性中定义的帐户类型。</span><span class="sxs-lookup"><span data-stu-id="450b6-103">Use the **Define Account Intelligence** page to map account types defined on the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance to account types defined in the dimension attribute associated with the **Account Type** attribute type in the dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="450b6-104"> 仅当您在 **“选择维度类型”** 页中选择 **“标准维度”** 以及在 **“指定维度类型”** 页上将维度属性映射到 **“帐户类型”** 属性类型时，才会显示此页。</span><span class="sxs-lookup"><span data-stu-id="450b6-104">This page is displayed only if you selected **Standard dimension** on the **Select the Dimension Type** page and if you mapped a dimension attribute to the **Account Type** attribute type on the **Specify Dimension Type** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="450b6-105">选项</span><span class="sxs-lookup"><span data-stu-id="450b6-105">Options</span></span>  
 <span data-ttu-id="450b6-106">**源表帐户类型**</span><span class="sxs-lookup"><span data-stu-id="450b6-106">**Source Table Account Types**</span></span>  
 <span data-ttu-id="450b6-107">显示分配给“指定维度键和类型”\*\*\*\* 页中“帐户类型”\*\*\*\* 属性类型的维度属性中包含的值。</span><span class="sxs-lookup"><span data-stu-id="450b6-107">Displays the values contained in the dimension attribute assigned to the **Account Type** attribute type in the **Specify Dimension Key and Type** page.</span></span>  
  
 <span data-ttu-id="450b6-108">**内置帐户类型**</span><span class="sxs-lookup"><span data-stu-id="450b6-108">**Built-In Account Types**</span></span>  
 <span data-ttu-id="450b6-109">选择在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例中定义的帐户类型，该帐户类型将映射到源表中的帐户类型。</span><span class="sxs-lookup"><span data-stu-id="450b6-109">Select the account type defined on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that maps to the account types in the source table.</span></span>  
  
 <span data-ttu-id="450b6-110">下表列出了在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例中定义的帐户类型：</span><span class="sxs-lookup"><span data-stu-id="450b6-110">The following table lists the account types that are defined on an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span>  
  
|<span data-ttu-id="450b6-111">值</span><span class="sxs-lookup"><span data-stu-id="450b6-111">Value</span></span>|<span data-ttu-id="450b6-112">说明</span><span class="sxs-lookup"><span data-stu-id="450b6-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="450b6-113">**资产**</span><span class="sxs-lookup"><span data-stu-id="450b6-113">**Asset**</span></span>|<span data-ttu-id="450b6-114">在特定时间拥有的物品的价值。</span><span class="sxs-lookup"><span data-stu-id="450b6-114">Value of things owned at a specific time.</span></span>|  
|<span data-ttu-id="450b6-115">**Balance**</span><span class="sxs-lookup"><span data-stu-id="450b6-115">**Balance**</span></span>|<span data-ttu-id="450b6-116">在特定时间某物的计数。</span><span class="sxs-lookup"><span data-stu-id="450b6-116">Count of something at a specific time.</span></span>|  
|<span data-ttu-id="450b6-117">**费用**</span><span class="sxs-lookup"><span data-stu-id="450b6-117">**Expense**</span></span>|<span data-ttu-id="450b6-118">所花费的价值。</span><span class="sxs-lookup"><span data-stu-id="450b6-118">Value of things spent.</span></span>|  
|<span data-ttu-id="450b6-119">**流向**</span><span class="sxs-lookup"><span data-stu-id="450b6-119">**Flow**</span></span>|<span data-ttu-id="450b6-120">事物的增量计数。</span><span class="sxs-lookup"><span data-stu-id="450b6-120">Incremental count of things.</span></span>|  
|<span data-ttu-id="450b6-121">**收入**</span><span class="sxs-lookup"><span data-stu-id="450b6-121">**Income**</span></span>|<span data-ttu-id="450b6-122">收到的价值。</span><span class="sxs-lookup"><span data-stu-id="450b6-122">Value of things received.</span></span>|  
|<span data-ttu-id="450b6-123">**负债**</span><span class="sxs-lookup"><span data-stu-id="450b6-123">**Liability**</span></span>|<span data-ttu-id="450b6-124">在特定时间所拖欠的价值。</span><span class="sxs-lookup"><span data-stu-id="450b6-124">Value of things owed at a specific time.</span></span>|  
|<span data-ttu-id="450b6-125">**统计**</span><span class="sxs-lookup"><span data-stu-id="450b6-125">**Statistical**</span></span>|<span data-ttu-id="450b6-126">某事物的计算比率，或者未聚合的某事物的计数。</span><span class="sxs-lookup"><span data-stu-id="450b6-126">Calculated ratio of something, or count of something that does not aggregate.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="450b6-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="450b6-127">See Also</span></span>  
 <span data-ttu-id="450b6-128">[维度向导的 F1 帮助](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="450b6-128">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="450b6-129">[Analysis Services 多维数据 &#40;维度&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="450b6-129">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="450b6-130">多维模型中的维度</span><span class="sxs-lookup"><span data-stu-id="450b6-130">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
