---
title: 维度类型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- time dimensions [Analysis Services]
- quantitative dimensions [Analysis Services]
- BillOfMaterials dimension [Analysis Services]
- geography dimensions
- utility dimensions [Analysis Services]
- channel dimensions
- dimensions [Analysis Services], types
- products dimensions [Analysis Services]
- account dimensions [Analysis Services]
- organization dimensions
- currency dimensions [Analysis Services]
- rates dimensions
- promotion dimensions
- scenario dimensions [Analysis Services]
- customers dimensions [Analysis Services]
- Type property
ms.assetid: bd3195da-e762-4c98-b643-34c76e842343
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5e0c16a57081aa1d9ed3cc6964d1f17fa7135986
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591614"
---
# <a name="dimension-types"></a><span data-ttu-id="b637e-102">维度类型</span><span class="sxs-lookup"><span data-stu-id="b637e-102">Dimension Types</span></span>
  <span data-ttu-id="b637e-103">`Type` 属性设置为服务器和客户端应用程序提供有关维度内容的信息。</span><span class="sxs-lookup"><span data-stu-id="b637e-103">The `Type` property setting provides information about the contents of a dimension to server and client applications.</span></span> <span data-ttu-id="b637e-104">在某些情况下，`Type` 设置只为客户端应用程序提供指导信息，并且为可选项。</span><span class="sxs-lookup"><span data-stu-id="b637e-104">In some cases, the `Type` setting only provides guidance for client applications and is optional.</span></span> <span data-ttu-id="b637e-105">在其他情况下，例如 `Accounts` 维度或 `Time` 维度，维度及其特性的 `Type` 属性设置可以确定基于服务器的特定行为，并且实现多维数据集中的某些行为也可能需要该属性设置。</span><span class="sxs-lookup"><span data-stu-id="b637e-105">In other cases, such as `Accounts` or `Time` dimensions, the `Type` property settings for the dimension and its attributes determine specific server-based behaviors and may be required to implement certain behaviors in the cube.</span></span> <span data-ttu-id="b637e-106">例如，维度的 `Type` 属性可以设置为 `Accounts`，从而向客户端应用程序指示标准维度包含帐户特性。</span><span class="sxs-lookup"><span data-stu-id="b637e-106">For example, the `Type` property of a dimension can be set to `Accounts` to indicate to client applications that the standard dimension contains account attributes.</span></span> <span data-ttu-id="b637e-107">有关时间、帐户和货币维度的详细信息，请参阅[创建日期类型维度](../multidimensional-models/database-dimensions-create-a-date-type-dimension.md)、[创建父子类型维度的财务帐户](../multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md)和[创建货币类型维度](../multidimensional-models/database-dimensions-create-a-currency-type-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="b637e-107">For more information about time, account, and currency dimensions, see [Create a Date type Dimension](../multidimensional-models/database-dimensions-create-a-date-type-dimension.md), [Create a Finance Account of parent-child type Dimension](../multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md), and [Create a Currency type Dimension](../multidimensional-models/database-dimensions-create-a-currency-type-dimension.md).</span></span>  
  
 <span data-ttu-id="b637e-108">维度类型的默认设置为 `Regular`，该设置不对维度内容进行任何假设。</span><span class="sxs-lookup"><span data-stu-id="b637e-108">The default setting for the dimension type is `Regular`, which makes no assumptions about the contents of the dimension.</span></span> <span data-ttu-id="b637e-109">当您初始定义维度时，该设置为所有维度的默认设置，除非您在使用维度向导定义维度时指定了 `Time`。</span><span class="sxs-lookup"><span data-stu-id="b637e-109">This is the default setting for all dimensions when you initially define a dimension unless you specify `Time` when defining the dimension using the Dimension Wizard.</span></span> <span data-ttu-id="b637e-110">如果维度向导没有为维度类型列出合适的类型，则还应当将 `Regular` 继续用做维度类型。</span><span class="sxs-lookup"><span data-stu-id="b637e-110">You should also leave `Regular` as the dimension type if the Dimension Wizard does not list an appropriate type for Dimension type.</span></span>  
  
## <a name="available-dimension-types"></a><span data-ttu-id="b637e-111">可用维度类型</span><span class="sxs-lookup"><span data-stu-id="b637e-111">Available Dimension Types</span></span>  
 <span data-ttu-id="b637e-112">下表描述了中可用的维度类型 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b637e-112">The following table describes the dimension types available in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="b637e-113">维度类型</span><span class="sxs-lookup"><span data-stu-id="b637e-113">Dimension type</span></span>|<span data-ttu-id="b637e-114">说明</span><span class="sxs-lookup"><span data-stu-id="b637e-114">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="b637e-115">定期</span><span class="sxs-lookup"><span data-stu-id="b637e-115">Regular</span></span>|<span data-ttu-id="b637e-116">一种其类型尚未被设置为特殊维度类型的维度。</span><span class="sxs-lookup"><span data-stu-id="b637e-116">A dimension whose type has not been set to a special dimension type.</span></span>|  
|<span data-ttu-id="b637e-117">时间</span><span class="sxs-lookup"><span data-stu-id="b637e-117">Time</span></span>|<span data-ttu-id="b637e-118">一种其属性表示时间段（如年、半期、季度、月和天）的维度。</span><span class="sxs-lookup"><span data-stu-id="b637e-118">A dimension whose attributes represent time periods, such as years, semesters, quarters, months, and days.</span></span>|  
|<span data-ttu-id="b637e-119">组织</span><span class="sxs-lookup"><span data-stu-id="b637e-119">Organization</span></span>|<span data-ttu-id="b637e-120">一种其属性表示单位信息（如雇员或分公司）的维度。</span><span class="sxs-lookup"><span data-stu-id="b637e-120">A dimension whose attributes represent organizational information, such as employees or subsidiaries.</span></span>|  
|<span data-ttu-id="b637e-121">地理位置</span><span class="sxs-lookup"><span data-stu-id="b637e-121">Geography</span></span>|<span data-ttu-id="b637e-122">一种其属性表示地域信息（如市县或邮政编码）的维度。</span><span class="sxs-lookup"><span data-stu-id="b637e-122">A dimension whose attributes represent geographic information, such as cities or postal codes.</span></span>|  
|<span data-ttu-id="b637e-123">BillOfMaterials</span><span class="sxs-lookup"><span data-stu-id="b637e-123">BillOfMaterials</span></span>|<span data-ttu-id="b637e-124">一种其属性表示库存或制造信息（如产品的部件列表）的维度。</span><span class="sxs-lookup"><span data-stu-id="b637e-124">A dimension whose attributes represent inventory or manufacturing information, such as parts lists for products.</span></span>|  
|<span data-ttu-id="b637e-125">帐户</span><span class="sxs-lookup"><span data-stu-id="b637e-125">Accounts</span></span>|<span data-ttu-id="b637e-126">一种其属性表示用于财务报表用途的科目表的维度。</span><span class="sxs-lookup"><span data-stu-id="b637e-126">A dimension whose attributes represent a chart of accounts for financial reporting purposes.</span></span>|  
|<span data-ttu-id="b637e-127">客户</span><span class="sxs-lookup"><span data-stu-id="b637e-127">Customers</span></span>|<span data-ttu-id="b637e-128">一种其属性表示客户信息或联系信息的维度。</span><span class="sxs-lookup"><span data-stu-id="b637e-128">A dimension whose attributes represent customer or contact information.</span></span>|  
|<span data-ttu-id="b637e-129">产品</span><span class="sxs-lookup"><span data-stu-id="b637e-129">Products</span></span>|<span data-ttu-id="b637e-130">一种其属性表示产品信息的维度。</span><span class="sxs-lookup"><span data-stu-id="b637e-130">A dimension whose attributes represent product information.</span></span>|  
|<span data-ttu-id="b637e-131">方案</span><span class="sxs-lookup"><span data-stu-id="b637e-131">Scenario</span></span>|<span data-ttu-id="b637e-132">一种其属性表示计划或策略分析信息的维度。</span><span class="sxs-lookup"><span data-stu-id="b637e-132">A dimension whose attributes represent planning or strategic analysis information.</span></span>|  
|<span data-ttu-id="b637e-133">Quantitative</span><span class="sxs-lookup"><span data-stu-id="b637e-133">Quantitative</span></span>|<span data-ttu-id="b637e-134">一种其属性表示定量信息的维度。</span><span class="sxs-lookup"><span data-stu-id="b637e-134">A dimension whose attributes represent quantitative information.</span></span>|  
|<span data-ttu-id="b637e-135">实用工具</span><span class="sxs-lookup"><span data-stu-id="b637e-135">Utility</span></span>|<span data-ttu-id="b637e-136">一种其属性表示杂项信息的维度。</span><span class="sxs-lookup"><span data-stu-id="b637e-136">A dimension whose attributes represent miscellaneous information.</span></span>|  
|<span data-ttu-id="b637e-137">货币</span><span class="sxs-lookup"><span data-stu-id="b637e-137">Currency</span></span>|<span data-ttu-id="b637e-138">该类型的维度包含货币数据和元数据。</span><span class="sxs-lookup"><span data-stu-id="b637e-138">This type of dimension contains currency data and metadata.</span></span>|  
|<span data-ttu-id="b637e-139">Rates</span><span class="sxs-lookup"><span data-stu-id="b637e-139">Rates</span></span>|<span data-ttu-id="b637e-140">一种其属性表示货币汇率信息的维度。</span><span class="sxs-lookup"><span data-stu-id="b637e-140">A dimension whose attributes represent currency rate information.</span></span>|  
|<span data-ttu-id="b637e-141">Channel</span><span class="sxs-lookup"><span data-stu-id="b637e-141">Channel</span></span>|<span data-ttu-id="b637e-142">一种其属性表示渠道信息的维度。</span><span class="sxs-lookup"><span data-stu-id="b637e-142">A dimension whose attributes represent channel information.</span></span>|  
|<span data-ttu-id="b637e-143">Promotion</span><span class="sxs-lookup"><span data-stu-id="b637e-143">Promotion</span></span>|<span data-ttu-id="b637e-144">一种其属性表示营销促销信息的维度。</span><span class="sxs-lookup"><span data-stu-id="b637e-144">A dimension whose attributes represent marketing promotion information.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b637e-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b637e-145">See Also</span></span>  
 <span data-ttu-id="b637e-146">[使用现有表创建维度](../multidimensional-models/create-a-dimension-by-using-an-existing-table.md) </span><span class="sxs-lookup"><span data-stu-id="b637e-146">[Create a Dimension by Using an Existing Table](../multidimensional-models/create-a-dimension-by-using-an-existing-table.md) </span></span>  
 [<span data-ttu-id="b637e-147">维度（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="b637e-147">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimensions-analysis-services-multidimensional-data.md)  
  
  
