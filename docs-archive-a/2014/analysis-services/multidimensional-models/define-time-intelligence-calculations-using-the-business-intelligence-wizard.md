---
title: 使用商业智能向导定义时间智能计算 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- period over period growth [Analysis Services]
- parallel period comparisons [Analysis Services]
- Business Intelligence enhancements [Analysis Services], time intelligence
- time views [Analysis Services]
- hierarchies [Analysis Services], time
- time periods [Analysis Services]
- moving averages
- time [Analysis Services]
- period to date [Analysis Services]
- calculations [Analysis Services], time
- time hierarchies [Analysis Services]
- time intelligence [Analysis Services]
ms.assetid: be36e8fc-f46e-4553-8623-b27d695c330b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 222efb572c227e6a8ca3d1e2295b662cb586184a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578496"
---
# <a name="define-time-intelligence-calculations-using-the-business-intelligence-wizard"></a><span data-ttu-id="35650-102">使用商业智能向导定义时间智能计算</span><span class="sxs-lookup"><span data-stu-id="35650-102">Define Time Intelligence Calculations using the Business Intelligence Wizard</span></span>
  <span data-ttu-id="35650-103">时间智能增强功能是一项多维数据集增强功能，它可以将时间计算（或时间视图）添加到所选层次结构中。</span><span class="sxs-lookup"><span data-stu-id="35650-103">The time intelligence enhancement is a cube enhancement that adds time calculations (or time views) to a selected hierarchy.</span></span> <span data-ttu-id="35650-104">此增强功能支持以下计算类别：</span><span class="sxs-lookup"><span data-stu-id="35650-104">This enhancement supports the following categories of calculations:</span></span>  
  
-   <span data-ttu-id="35650-105">到现在为止时间段。</span><span class="sxs-lookup"><span data-stu-id="35650-105">Period to date.</span></span>  
  
-   <span data-ttu-id="35650-106">逐时间段增长。</span><span class="sxs-lookup"><span data-stu-id="35650-106">Period over period growth.</span></span>  
  
-   <span data-ttu-id="35650-107">移动平均。</span><span class="sxs-lookup"><span data-stu-id="35650-107">Moving averages.</span></span>  
  
-   <span data-ttu-id="35650-108">并行时间段比较。</span><span class="sxs-lookup"><span data-stu-id="35650-108">Parallel period comparisons.</span></span>  
  
 <span data-ttu-id="35650-109">时间智能应用于有时间维度的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="35650-109">You apply time intelligence to cubes that have a time dimension.</span></span> <span data-ttu-id="35650-110">（时间维度是其 `Type` 属性设置为 `Time` 的维度）。</span><span class="sxs-lookup"><span data-stu-id="35650-110">(A time dimension is a dimension whose `Type` property is set to `Time`).</span></span> <span data-ttu-id="35650-111">另外，该维度的时间特性的 `Type` 属性还必须有适当的设置（如年份或月份）。</span><span class="sxs-lookup"><span data-stu-id="35650-111">Additionally, the time attributes of that dimension must also have the appropriate setting (such as, Years or Months) for their `Type` property.</span></span> <span data-ttu-id="35650-112">如果使用维度向导创建时间维度，将会正确设置维度及其特性的 `Type` 属性。</span><span class="sxs-lookup"><span data-stu-id="35650-112">The `Type` property of both the dimension and its attributes will be set correctly if you use the Dimension Wizard to create the time dimension.</span></span>  
  
 <span data-ttu-id="35650-113">若要向多维数据集添加时间智能，请使用商业智能向导，并在 **“选择增强功能”** 页上选择 **“定义时间智能”** 选项。</span><span class="sxs-lookup"><span data-stu-id="35650-113">To add time intelligence to a cube, you use the Business Intelligence Wizard, and select the **Define time intelligence** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="35650-114">然后此向导将指引您完成相应的步骤，以选择将向其添加时间智能的层次结构，并指定将对层次结构中的哪些成员应用时间智能。</span><span class="sxs-lookup"><span data-stu-id="35650-114">This wizard then guides you through the steps of selecting a hierarchy to which you are adding time intelligence and specifying which members in the hierarchy will have time intelligence applied to them.</span></span> <span data-ttu-id="35650-115">在向导的最后一页上，您可以查看将对数据库进行的更改 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 以添加所选的时间智能。</span><span class="sxs-lookup"><span data-stu-id="35650-115">On the last page of the wizard, you can see the changes that will be made to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database to add the selected time intelligence.</span></span>  
  
## <a name="selecting-a-time-hierarchy"></a><span data-ttu-id="35650-116">选择时间层次结构</span><span class="sxs-lookup"><span data-stu-id="35650-116">Selecting a Time Hierarchy</span></span>  
 <span data-ttu-id="35650-117">在 **“选择目标层次结构和计算”** 页中，选择将应用时间增强功能的时间层次结构。</span><span class="sxs-lookup"><span data-stu-id="35650-117">On the **Choose Target Hierarchy and Calculations** page, you select the time hierarchy to which the time enhancement applies.</span></span> <span data-ttu-id="35650-118">每次运行商业智能向导时，只能向一个时间层次结构应用时间增强功能。</span><span class="sxs-lookup"><span data-stu-id="35650-118">You can apply the time enhancement to only one time hierarchy every time that you run the Business Intelligence Wizard.</span></span> <span data-ttu-id="35650-119">如果希望向多个时间层次结构应用增强功能，请再次运行向导。</span><span class="sxs-lookup"><span data-stu-id="35650-119">If you want to apply the enhancement to more than one time hierarchy, you run the wizard again.</span></span>  
  
 <span data-ttu-id="35650-120">选择时间层次结构后，请在 **“可用时间计算”** 列表中选择将应用于该层次结构的计算。</span><span class="sxs-lookup"><span data-stu-id="35650-120">After you select a time hierarchy, in the **Available time calculations** list, you select the calculations that apply to the hierarchy.</span></span> <span data-ttu-id="35650-121">列出的计算取决于在层次结构中的级别以及每个级别的特性的 `Type` 属性设置。</span><span class="sxs-lookup"><span data-stu-id="35650-121">The calculations that are listed depend on the levels in the hierarchy, and on the `Type` property setting for the attribute for each level.</span></span> <span data-ttu-id="35650-122">例如，“年份”层次结构支持“本年度截止到现在”和“年度同比增长量”，但是“季度”层次结构则不支持。</span><span class="sxs-lookup"><span data-stu-id="35650-122">For example, a Years hierarchy supports Year to Date and Year Over Year Growth, but a Quarters hierarchy does not.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="35650-123">Timeintelligence.xml 模板文件定义了在 **“可用时间计算”** 中列出的时间计算。</span><span class="sxs-lookup"><span data-stu-id="35650-123">The Timeintelligence.xml template file defines the time calculations that are listed in **Available time calculations**.</span></span> <span data-ttu-id="35650-124">如果列出的计算不能满足需要，可以更改现有计算，或在 Timeintelligence.xml 文件中添加新的计算。</span><span class="sxs-lookup"><span data-stu-id="35650-124">If the listed calculations do not meet your needs, you can either change the existing calculations or add new calculations to the Timeintelligence.xml file.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="35650-125">若要查看计算的说明，请使用向上和向下键突出显示该计算。</span><span class="sxs-lookup"><span data-stu-id="35650-125">To view a description for a calculation, use the up and down arrows to highlight that calculation.</span></span>  
  
## <a name="apply-time-views-to-members"></a><span data-ttu-id="35650-126">对成员应用时间视图</span><span class="sxs-lookup"><span data-stu-id="35650-126">Apply Time Views to Members</span></span>  
 <span data-ttu-id="35650-127">在 **“定义计算作用域”** 页中，可以指定要应用新时间视图的成员。</span><span class="sxs-lookup"><span data-stu-id="35650-127">On the **Define Scope of Calculations** page, you specify the members to which the new time views apply.</span></span> <span data-ttu-id="35650-128">可以对下列对象之一应用新的时间视图：</span><span class="sxs-lookup"><span data-stu-id="35650-128">You can apply the new time views to one of the following objects:</span></span>  
  
-   <span data-ttu-id="35650-129">**帐户维度的成员** 在 **“定义计算作用域”** 页中， **“可用度量值”** 列表已包括帐户维度。</span><span class="sxs-lookup"><span data-stu-id="35650-129">**Members of an account dimension** On the **Define Scope of Calculations** page, the **Available measures** list includes account dimensions.</span></span> <span data-ttu-id="35650-130">帐户维度的 `Type` 属性已设置为 `Accounts`。</span><span class="sxs-lookup"><span data-stu-id="35650-130">Account dimensions have their `Type` properties set to `Accounts`.</span></span> <span data-ttu-id="35650-131">如果有帐户维度但该维度没有出现在 **“可用度量值”** 列表中，则可以使用商业智能向导对该维度应用帐户智能。</span><span class="sxs-lookup"><span data-stu-id="35650-131">If you have an accounts dimension but that dimension does not appear in the **Available measures** list, you can use the Business Intelligence Wizard to apply the account intelligence to that dimension.</span></span> <span data-ttu-id="35650-132">有关详细信息，请参阅 [向维度中添加帐户智能](bi-wizard-add-account-intelligence-to-a-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="35650-132">For more information, see [Add Account Intelligence to a Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).</span></span>  
  
-   <span data-ttu-id="35650-133">**度量值** 可以不指定帐户维度，而指定应用时间视图的度量值。</span><span class="sxs-lookup"><span data-stu-id="35650-133">**Measures** Instead of specifying an account dimension, you can specify the measures to which the time views apply.</span></span> <span data-ttu-id="35650-134">在这种情况下，请选择要应用所选时间计算的视图。</span><span class="sxs-lookup"><span data-stu-id="35650-134">In this case, select the views to which selected time calculations apply.</span></span> <span data-ttu-id="35650-135">例如，资产和负债是本年度截止到现在的数据；因此，不对资产或负债度量值应用“本年度截止到现在”的计算。</span><span class="sxs-lookup"><span data-stu-id="35650-135">For example, assets and liabilities are year-to-date data; therefore, you do not apply a Year-to-Date calculation to assets or liabilities measures.</span></span>  
  
## <a name="viewing-the-time-intelligence-enhancement"></a><span data-ttu-id="35650-136">查看时间智能增强功能</span><span class="sxs-lookup"><span data-stu-id="35650-136">Viewing the Time Intelligence Enhancement</span></span>  
 <span data-ttu-id="35650-137">在商业智能向导的最后一页中，可以查看将对 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库进行的更改。</span><span class="sxs-lookup"><span data-stu-id="35650-137">On the final page of the Business Intelligence Wizard, you can view the changes that will be made to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="35650-138">对于时间智能增强功能，向导将按下表所述更改所选时间维度、关联的数据源视图以及关联的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="35650-138">For a time intelligence enhancement, the wizard will change the selected time dimension, associated data source view, and associated cube as described in the following table.</span></span>  
  
|<span data-ttu-id="35650-139">对象</span><span class="sxs-lookup"><span data-stu-id="35650-139">Object</span></span>|<span data-ttu-id="35650-140">更改</span><span class="sxs-lookup"><span data-stu-id="35650-140">Change</span></span>|  
|------------|------------|  
|<span data-ttu-id="35650-141">时间维度</span><span class="sxs-lookup"><span data-stu-id="35650-141">Time dimension</span></span>|<span data-ttu-id="35650-142">为每个计算（或视图）添加属性。</span><span class="sxs-lookup"><span data-stu-id="35650-142">Adds an attribute for each calculation (or view).</span></span>|  
|<span data-ttu-id="35650-143">数据源视图</span><span class="sxs-lookup"><span data-stu-id="35650-143">Data source view</span></span>|<span data-ttu-id="35650-144">在时间表中为时间维度中每个新属性添加计算列。</span><span class="sxs-lookup"><span data-stu-id="35650-144">Adds a calculated column in the time table for each new attribute in the time dimension.</span></span>|  
|<span data-ttu-id="35650-145">多维数据集</span><span class="sxs-lookup"><span data-stu-id="35650-145">Cube</span></span>|<span data-ttu-id="35650-146">添加计算成员，该成员定义了执行此计算的多维表达式 (MDX) 代码。</span><span class="sxs-lookup"><span data-stu-id="35650-146">Adds a calculated member that defines the Multidimensional Expressions (MDX) code to perform the calculation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35650-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="35650-147">See Also</span></span>  
 [<span data-ttu-id="35650-148">创建计算成员</span><span class="sxs-lookup"><span data-stu-id="35650-148">Create Calculated Members</span></span>](create-calculated-members.md)  
  
  
