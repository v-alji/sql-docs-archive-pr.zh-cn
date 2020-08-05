---
title: 查询和筛选 (浏览器选项卡，多维数据集设计器)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.filterpane.f1
ms.assetid: f5cf0bb1-3afb-4856-a2ef-614deb4e7e49
author: minewiskan
ms.author: owend
ms.openlocfilehash: 66bd299e210b3d00384395177cdd6e89d1c00183
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580441"
---
# <a name="query-and-filter-browser-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="7b02b-102">查询和筛选（“浏览器”选项卡，多维数据集设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="7b02b-102">Query and Filter (Browser Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="7b02b-103">多维数据集设计器中 **“浏览器”** 选项卡的这一区域包含查询和筛选区域，可帮助您从多维数据集中选择用于浏览或查询的数据。</span><span class="sxs-lookup"><span data-stu-id="7b02b-103">This area of the **Browser** tab in Cube Designer contains a query and filter area, to help you choose data from the cube to use in browsing or in queries.</span></span> <span data-ttu-id="7b02b-104">您可以按需添加任意多个多维数据集对象，然后在数据区域中查看结果，或使用“在 Excel 中分析”功能将结果导出到报表，以便演示最终用户将如何查看数据。</span><span class="sxs-lookup"><span data-stu-id="7b02b-104">You can add as many cube objects as you want, and then view the results in the data area, or export the results to a report using Analyze in Excel to visualize how the data would be viewed by end users.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="7b02b-105">当您在此区域中处理数据时，默认情况下 **“浏览器”** 使用图形设计模式。</span><span class="sxs-lookup"><span data-stu-id="7b02b-105">When you are working with data in this area, by default the **Browser** uses the graphical design mode.</span></span> <span data-ttu-id="7b02b-106">但是，您可以通过单击 **“设计模式”** 切换按钮使用 MDX 直接编辑该查询。</span><span class="sxs-lookup"><span data-stu-id="7b02b-106">However, you can edit the query directly using MDX, by clicking the **Design Mode** toggle button.</span></span> <span data-ttu-id="7b02b-107">执行此操作时，用于设计维度筛选器的窗格会消失。</span><span class="sxs-lookup"><span data-stu-id="7b02b-107">When you do so, the pane that lets you design filters on dimensions disappears.</span></span> <span data-ttu-id="7b02b-108">如果您想添加一个筛选器，可以切换回图形设计模式。</span><span class="sxs-lookup"><span data-stu-id="7b02b-108">If you want to add a filter, you can switch back to graphical design mode.</span></span>  
  
 <span data-ttu-id="7b02b-109">默认情况下，在执行查询时，当前用户的凭据（而非在 **“模拟信息”** 页中指定的凭据）用于连接到数据源。</span><span class="sxs-lookup"><span data-stu-id="7b02b-109">By default, the credentials of the current user, not the credentials specified in the **Impersonation Information** page, are used to connect to the data source when a query is executed.</span></span> <span data-ttu-id="7b02b-110">但是，您也可以通过单击 **“工具栏”** 上的 **“更改用户”** 来更改查询或报表的用户上下文。</span><span class="sxs-lookup"><span data-stu-id="7b02b-110">However, you can also change the user context for the query or report by clicking **Change User** on the **Toolbar**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7b02b-111">选项</span><span class="sxs-lookup"><span data-stu-id="7b02b-111">Options</span></span>  
 <span data-ttu-id="7b02b-112">**维度**</span><span class="sxs-lookup"><span data-stu-id="7b02b-112">**Dimension**</span></span>  
 <span data-ttu-id="7b02b-113">选择对子多维数据集进行切片时所在的维度。</span><span class="sxs-lookup"><span data-stu-id="7b02b-113">Select the dimension on which to slice the subcube.</span></span>  
  
 <span data-ttu-id="7b02b-114">**层次结构**</span><span class="sxs-lookup"><span data-stu-id="7b02b-114">**Hierarchy**</span></span>  
 <span data-ttu-id="7b02b-115">选择对子多维数据集进行切片时所在的层次结构。</span><span class="sxs-lookup"><span data-stu-id="7b02b-115">Select the hierarchy on which to slice the subcube.</span></span>  
  
 <span data-ttu-id="7b02b-116">**“运算符”**</span><span class="sxs-lookup"><span data-stu-id="7b02b-116">**Operator**</span></span>  
 <span data-ttu-id="7b02b-117">选择运算符，以定义“筛选表达式”\*\*\*\* 中的表达式如何应用于所选层次结构。</span><span class="sxs-lookup"><span data-stu-id="7b02b-117">Select the operator that defines how the expression in **Filter Expression** is applied to the selected hierarchy.</span></span> <span data-ttu-id="7b02b-118">下表对可用的运算符进行了说明：</span><span class="sxs-lookup"><span data-stu-id="7b02b-118">The following table describes the available operators.</span></span>  
  
|<span data-ttu-id="7b02b-119">值</span><span class="sxs-lookup"><span data-stu-id="7b02b-119">Value</span></span>|<span data-ttu-id="7b02b-120">说明</span><span class="sxs-lookup"><span data-stu-id="7b02b-120">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7b02b-121">**等于**</span><span class="sxs-lookup"><span data-stu-id="7b02b-121">**Equal**</span></span>|<span data-ttu-id="7b02b-122">结果限制为在 **“筛选表达式”** 中定义的集合。</span><span class="sxs-lookup"><span data-stu-id="7b02b-122">The results are restricted to the set defined in **Filter Expression**.</span></span>|  
|<span data-ttu-id="7b02b-123">**不等于**</span><span class="sxs-lookup"><span data-stu-id="7b02b-123">**Not Equal**</span></span>|<span data-ttu-id="7b02b-124">结果限制为排除在 **“筛选表达式”** 中所定义集合之外的成员。</span><span class="sxs-lookup"><span data-stu-id="7b02b-124">The results are restricted to the members excluded by the set defined in **Filter Expression**.</span></span>|  
|<span data-ttu-id="7b02b-125">**在**</span><span class="sxs-lookup"><span data-stu-id="7b02b-125">**In**</span></span>|<span data-ttu-id="7b02b-126">结果限制为在 **“筛选表达式”** 中选择的命名集。</span><span class="sxs-lookup"><span data-stu-id="7b02b-126">The results are restricted to the named set chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="7b02b-127">**不位于**</span><span class="sxs-lookup"><span data-stu-id="7b02b-127">**Not In**</span></span>|<span data-ttu-id="7b02b-128">结果限制为排除在 **“筛选表达式”** 中所选命名集之外的成员。</span><span class="sxs-lookup"><span data-stu-id="7b02b-128">The results are restricted to the members excluded by the named set chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="7b02b-129">**包含**</span><span class="sxs-lookup"><span data-stu-id="7b02b-129">**Contains**</span></span>|<span data-ttu-id="7b02b-130">结果限制为成员名称包含 **“筛选表达式”** 中的字符串的成员。</span><span class="sxs-lookup"><span data-stu-id="7b02b-130">The results are restricted to members whose member names contain the string in **Filter Expression**.</span></span>|  
|<span data-ttu-id="7b02b-131">**开头为**</span><span class="sxs-lookup"><span data-stu-id="7b02b-131">**Begins With**</span></span>|<span data-ttu-id="7b02b-132">结果限制为成员名称以 **“筛选表达式”** 中的字符串开头的成员。</span><span class="sxs-lookup"><span data-stu-id="7b02b-132">The results are restricted to members whose member names begin with the string in **Filter Expression**.</span></span>|  
|<span data-ttu-id="7b02b-133">**范围(包括)**</span><span class="sxs-lookup"><span data-stu-id="7b02b-133">**Range (Inclusive)**</span></span>|<span data-ttu-id="7b02b-134">结果限制为在 **“筛选表达式”** 中选择的范围。</span><span class="sxs-lookup"><span data-stu-id="7b02b-134">The results are restricted to the range chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="7b02b-135">**范围(不包括)**</span><span class="sxs-lookup"><span data-stu-id="7b02b-135">**Range (Exclusive)**</span></span>|<span data-ttu-id="7b02b-136">结果限制为排除在 **“筛选表达式”** 中所选范围之外的成员。</span><span class="sxs-lookup"><span data-stu-id="7b02b-136">The results are restricted to the members excluded by the range chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="7b02b-137">**MDX**</span><span class="sxs-lookup"><span data-stu-id="7b02b-137">**MDX**</span></span>|<span data-ttu-id="7b02b-138">结果限制为在“筛选表达式”\*\*\*\* 中设置的多维表达式 (MDX) 表达式。</span><span class="sxs-lookup"><span data-stu-id="7b02b-138">The results are restricted to the Multidimensional Expressions (MDX) expression set in **Filter Expression**.</span></span>|  
  
 <span data-ttu-id="7b02b-139">**筛选表达式**</span><span class="sxs-lookup"><span data-stu-id="7b02b-139">**Filter Expression**</span></span>  
 <span data-ttu-id="7b02b-140">键入通过“运算符”\*\*\*\* 计算的表达式，该表达式可限制要浏览的结果。</span><span class="sxs-lookup"><span data-stu-id="7b02b-140">Type the expression that is to be evaluated by **Operator**, which restricts the results to be browsed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b02b-141">此字段是动态数据输入元素，其外观将根据所选运算符的不同而相应改变，以反映该运算符所需的数据类型。</span><span class="sxs-lookup"><span data-stu-id="7b02b-141">This field is a dynamic data entry element, changing appearance to reflect the types of data necessary for the selected operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b02b-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7b02b-142">See Also</span></span>  
 <span data-ttu-id="7b02b-143">[多维数据集设计器 &#40;Analysis Services 多维数据&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7b02b-143">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="7b02b-144">[浏览器 &#40;多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7b02b-144">[Browser &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="7b02b-145">[工具栏 &#40;浏览器选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7b02b-145">[Toolbar &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="7b02b-146">[在 Excel &#40;浏览器选项卡、多维数据集设计器&#41; &#40;Analysis Services 多维数据中分析&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7b02b-146">[Analyze in Excel &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="7b02b-147">元数据 &#40;浏览器选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="7b02b-147">Metadata &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md)  
  
  
