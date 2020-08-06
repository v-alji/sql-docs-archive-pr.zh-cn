---
title: " (SSAS 表格) 的 Kpi |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a0524602-5239-45a7-8c44-2477302a3637
author: minewiskan
ms.author: owend
ms.openlocfilehash: 54cc7341f2d0f002496c1936f2c4f0808cd5e243
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687215"
---
# <a name="kpis-ssas-tabular"></a><span data-ttu-id="64aa6-102">KPI（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="64aa6-102">KPIs (SSAS Tabular)</span></span>
  <span data-ttu-id="64aa6-103">在表格模型中，KPI（关键绩效指标）用于根据目标值（由度量值或绝对值定义）度量某一值（由基础度量值定义）的性能\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="64aa6-103">A *KPI* (Key Performance Indicator), in a tabular model, is used to gauge performance of a value, defined by a *Base* measure, against a *Target* value, also defined by a measure or by an absolute value.</span></span> <span data-ttu-id="64aa6-104">本主题帮助表格模型作者对表格模型中的 KPI 有一个基本的了解。</span><span class="sxs-lookup"><span data-stu-id="64aa6-104">This topic provides tabular model authors a basic understanding of KPIs in a tabular model.</span></span>  
  
 <span data-ttu-id="64aa6-105">本主题的内容：</span><span class="sxs-lookup"><span data-stu-id="64aa6-105">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="64aa6-106">优点</span><span class="sxs-lookup"><span data-stu-id="64aa6-106">Benefits</span></span>](#bkmk_benefits)  
  
-   [<span data-ttu-id="64aa6-107">示例</span><span class="sxs-lookup"><span data-stu-id="64aa6-107">Example</span></span>](#bkmk_example)  
  
-   [<span data-ttu-id="64aa6-108">创建和编辑 Kpi</span><span class="sxs-lookup"><span data-stu-id="64aa6-108">Create and Edit KPIs</span></span>](#bkmk_create)  
  
-   [<span data-ttu-id="64aa6-109">相关任务</span><span class="sxs-lookup"><span data-stu-id="64aa6-109">Related Tasks</span></span>](#bkmk_related_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_benefits"></a> <span data-ttu-id="64aa6-110">优势</span><span class="sxs-lookup"><span data-stu-id="64aa6-110">Benefits</span></span>  
 <span data-ttu-id="64aa6-111">在业务术语中，关键绩效指标 (KPI) 是一个用于度量业务目标的可计量度量值。</span><span class="sxs-lookup"><span data-stu-id="64aa6-111">In business terminology, a Key Performance Indicator (KPI) is a quantifiable measurement for gauging business objectives.</span></span> <span data-ttu-id="64aa6-112">经常会在一段时间内评估 KPI。</span><span class="sxs-lookup"><span data-stu-id="64aa6-112">A KPI is frequently evaluated over time.</span></span> <span data-ttu-id="64aa6-113">例如，组织的销售部门可以使用 KPI 来根据预计的毛利润来度量每月毛利润。</span><span class="sxs-lookup"><span data-stu-id="64aa6-113">For example, the sales department of an organization may use a KPI to measure monthly gross profit against projected gross profit.</span></span> <span data-ttu-id="64aa6-114">会计部门可以度量每月的支出与收入之比以便评估成本，而人力资源部门可以度量每季度员工流失情况。</span><span class="sxs-lookup"><span data-stu-id="64aa6-114">The accounting department may measure monthly expenditures against revenue to evaluate costs, and a human resources department may measure quarterly employee turnover.</span></span> <span data-ttu-id="64aa6-115">这两个都是 KPI 的示例。</span><span class="sxs-lookup"><span data-stu-id="64aa6-115">Each is an example of a KPI.</span></span> <span data-ttu-id="64aa6-116">业务专业人员经常使用以业务计分卡形式分组在一起的 KPI 获取迅速且精确的业务绩效历史摘要或标识趋势。</span><span class="sxs-lookup"><span data-stu-id="64aa6-116">Business professionals frequently consume KPIs that are grouped together in a business scorecard to obtain a quick and accurate historical summary of business success or to identify trends.</span></span>  
  
 <span data-ttu-id="64aa6-117">表格模型中的 KPI 包括：</span><span class="sxs-lookup"><span data-stu-id="64aa6-117">A KPI in a tabular model includes:</span></span>  
  
 <span data-ttu-id="64aa6-118">**基础值**</span><span class="sxs-lookup"><span data-stu-id="64aa6-118">**Base Value**</span></span>  
 <span data-ttu-id="64aa6-119">基础值由解析为值的度量值定义。</span><span class="sxs-lookup"><span data-stu-id="64aa6-119">A Base value is defined by a measure that resolves to a value.</span></span> <span data-ttu-id="64aa6-120">例如，该值可以是实际销售额或计算出的度量值（例如给定期间的利润）的聚合。</span><span class="sxs-lookup"><span data-stu-id="64aa6-120">This value, for example, can be an aggregate of actual Sales or a calculated measure such as Profit for a given period.</span></span>  
  
 <span data-ttu-id="64aa6-121">**目标值**</span><span class="sxs-lookup"><span data-stu-id="64aa6-121">**Target value**</span></span>  
 <span data-ttu-id="64aa6-122">目标值由解析为值的度量值定义，也可由绝对值定义。</span><span class="sxs-lookup"><span data-stu-id="64aa6-122">A Target value is defined by a measure that resolves to a value, or by an absolute value.</span></span> <span data-ttu-id="64aa6-123">例如，目标值可以是组织的业务经理希望增加的销售额或利润的数量。</span><span class="sxs-lookup"><span data-stu-id="64aa6-123">For example, a target value could be the amount by which the business managers of an organization want to increase sales or profit.</span></span>  
  
 <span data-ttu-id="64aa6-124">**状态阈值**</span><span class="sxs-lookup"><span data-stu-id="64aa6-124">**Status thresholds**</span></span>  
 <span data-ttu-id="64aa6-125">状态阈值按下限和上限之间的范围或按固定值定义。</span><span class="sxs-lookup"><span data-stu-id="64aa6-125">A Status threshold is defined by the range between a low and high threshold or by a fixed value.</span></span> <span data-ttu-id="64aa6-126">状态阈值在显示时含一个图形，可帮助用户轻松地确定与目标值相比基础值的状态。</span><span class="sxs-lookup"><span data-stu-id="64aa6-126">The Status threshold displays with a graphic to help users easily determine the status of the Base value compared to the Target value.</span></span>  
  
##  <a name="example"></a><a name="bkmk_example"></a> <span data-ttu-id="64aa6-127">示例</span><span class="sxs-lookup"><span data-stu-id="64aa6-127">Example</span></span>  
 <span data-ttu-id="64aa6-128">Adventure Works 的销售经理想要创建一个数据透视表，她可以使用该数据透视表快速显示销售人员是否满足针对给定期间（年）的销售定额。</span><span class="sxs-lookup"><span data-stu-id="64aa6-128">The sales manager at Adventure Works wants to create a PivotTable that she can use to quickly display whether or not sales employees are meeting their sales quota for a given period (year).</span></span> <span data-ttu-id="64aa6-129">对于每个销售雇员，她希望该数据透视表显示以美元表示的实际销售额、以美元表示的销售配额量，以及显示每个销售员工是低于、等于还是高于其销售定额的状态的简单图形显示。</span><span class="sxs-lookup"><span data-stu-id="64aa6-129">For each sales employee, she wants the PivotTable to display the actual sales amount in dollars, the sales quota amount in dollars, and a simple graphic display showing the status of whether or not each sales employee is below, at, or above their sales quota.</span></span> <span data-ttu-id="64aa6-130">她希望能够按年对数据进行切片。</span><span class="sxs-lookup"><span data-stu-id="64aa6-130">She wants to be able to slice the data by year.</span></span>  
  
 <span data-ttu-id="64aa6-131">为实现此目的，销售经理会登记其组织的 BI 解决方案开发人员的帮助，以便将销售 KPI 添加到 AdventureWorks 表格模型中。</span><span class="sxs-lookup"><span data-stu-id="64aa6-131">To do this, the sales manager enlists the help of her organization's BI solution developer to add a Sales KPI to the AdventureWorks Tabular Model.</span></span> <span data-ttu-id="64aa6-132">该销售经理然后使用 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 连接到作为数据源的 Adventure Works 表格模型，并且创建了一个数据透视表，其中包含字段（度量值和 KPI）和切片器以便分析销售人员是否满足其定额。</span><span class="sxs-lookup"><span data-stu-id="64aa6-132">The sales manager will then use [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] to connect to the Adventure Works Tabular Model as a data source and create a PivotTable with the fields (measures and KPI) and slicers to analyze whether or not the sales force is meeting their quotas.</span></span>  
  
 <span data-ttu-id="64aa6-133">在模型中，将在 FactResellerSales 表中的 SalesAmount 列上创建一个度量值，该度量值提供以美元为单位的实际销售额。</span><span class="sxs-lookup"><span data-stu-id="64aa6-133">In the model, a measure on the SalesAmount column in the FactResellerSales table, which gives the actual sales amount in dollars for each sales employee is created.</span></span> <span data-ttu-id="64aa6-134">该度量值定义该 KPI 的基础值。</span><span class="sxs-lookup"><span data-stu-id="64aa6-134">This measure will define the Base value of the KPI.</span></span>  
  
 <span data-ttu-id="64aa6-135">将使用以下公式创建该 Sales 度量值：</span><span class="sxs-lookup"><span data-stu-id="64aa6-135">The Sales measure is created with the following formula:</span></span>  
  
```  
Sales:=Sum(FactResellerSales[SalesAmount])  
```  
  
 <span data-ttu-id="64aa6-136">FactSalesQuota 表中的 SalesAmountQuota 列具有为每位员工定义的销售定额。</span><span class="sxs-lookup"><span data-stu-id="64aa6-136">The SalesAmountQuota column in the FactSalesQuota table has a sales amount quota defined for each employee.</span></span> <span data-ttu-id="64aa6-137">该列中的值将充当 KPI 中的目标度量值（值）。</span><span class="sxs-lookup"><span data-stu-id="64aa6-137">The values in this column will serve as the Target measure (value) in the KPI.</span></span>  
  
 <span data-ttu-id="64aa6-138">将使用以下公式创建该 SalesAmountQuota 度量值：</span><span class="sxs-lookup"><span data-stu-id="64aa6-138">The SalesAmountQuota measure is created with the following formula:</span></span>  
  
```  
Target SalesAmountQuota:=Sum(FactSalesQuota[SalesAmountQuota])  
```  
  
> [!NOTE]  
>  <span data-ttu-id="64aa6-139">在 FactSalesQuota 表的 EmployeeKey 列和 DimEmployees 表的 EmployeeKey 列之间存在一个关系。</span><span class="sxs-lookup"><span data-stu-id="64aa6-139">There is a relationship between the EmployeeKey column in the FactSalesQuota table and the EmployeeKey in the DimEmployees table.</span></span> <span data-ttu-id="64aa6-140">该关系是必需的，以便 DimEmployee 表中的每位销售人员在 FactSalesQuota 表中体现出来。</span><span class="sxs-lookup"><span data-stu-id="64aa6-140">This relationship is necessary so that each sales employee in the DimEmployee table is represented in the FactSalesQuota table.</span></span>  
  
 <span data-ttu-id="64aa6-141">在创建了度量值以便充当 KPI 的基础值和目标值后，对该 Sales 度量值进行扩展以便成为新的 Sales KPI。</span><span class="sxs-lookup"><span data-stu-id="64aa6-141">Now that measures have been created to serve as the Base value and Target value of the KPI, the Sales measure is extended to a new Sales KPI.</span></span> <span data-ttu-id="64aa6-142">在 Sales KPI 中，Target SalesAmountQuota 度量值定义为目标值。</span><span class="sxs-lookup"><span data-stu-id="64aa6-142">In the Sales KPI, the Target SalesAmountQuota measure is defined as the Target value.</span></span> <span data-ttu-id="64aa6-143">“状态”阈值定义为某一百分比的范围，100% 的目标意味着 Sales 度量值定义的实际销售额满足在 Target SalesAmoutnQuota 度量值中定义的定额。</span><span class="sxs-lookup"><span data-stu-id="64aa6-143">The Status threshold is defined as a range by percentage, the target of which is 100% meaning actual sales defined by the Sales measure met the quota amount defined in the Target SalesAmoutnQuota measure.</span></span> <span data-ttu-id="64aa6-144">在状态栏上定义下限和上限百分比，并且选择图形类型。</span><span class="sxs-lookup"><span data-stu-id="64aa6-144">Low and High percentages are defined on the status bar, and a graphic type is selected.</span></span>  
  
 <span data-ttu-id="64aa6-145">销售经理现在可以创建一个数据透视表，将该 KPI 的基础值、目标值和状态添加到 "值" 字段。</span><span class="sxs-lookup"><span data-stu-id="64aa6-145">The sales manager can now create a PivotTable adding the KPI's Base value, Target value, and Status to the Values field.</span></span> <span data-ttu-id="64aa6-146">Employees 列将添加到 RowLabel 字段，而 CalendarYear 列作为切片器添加。</span><span class="sxs-lookup"><span data-stu-id="64aa6-146">The Employees column is added to the RowLabel field, and the CalendarYear column is added as a Slicer.</span></span>  
  
 <span data-ttu-id="64aa6-147">该销售经理可以按年对实际销售额、销售定额和每位销售员工的状态执行切片操作。</span><span class="sxs-lookup"><span data-stu-id="64aa6-147">The sales manager can now slice by year the actual sales amount, sales quota amount, and status for each sales employee.</span></span> <span data-ttu-id="64aa6-148">她可以分析多年中的销售趋势，以便确定是否需要调整某位销售人员的销售定额。</span><span class="sxs-lookup"><span data-stu-id="64aa6-148">She can analyze sales trends over years to determine whether or not she needs to adjust the sales quota for a sales employee.</span></span>  
  
##  <a name="create-and-edit-kpis"></a><a name="bkmk_create"></a><span data-ttu-id="64aa6-149">创建和编辑 Kpi</span><span class="sxs-lookup"><span data-stu-id="64aa6-149">Create and Edit KPIs</span></span>  
 <span data-ttu-id="64aa6-150">为了在模型设计器中创建 KPI，您将使用“关键绩效指标”对话框。</span><span class="sxs-lookup"><span data-stu-id="64aa6-150">To create KPIs, in the model designer, you will use the Key Performance Indicator dialog box.</span></span> <span data-ttu-id="64aa6-151">因为 KPI 必须与某一度量值相关联，所以，您将通过以下方式创建 KPI：扩展求值结果为某一基础值的度量值，然后或者创建求值结果为目标值的度量值，或者输入绝对值。</span><span class="sxs-lookup"><span data-stu-id="64aa6-151">Since KPIs must be associated with a measure, you create a KPI by extending a measure that evaluates to a Base value, and then either creating a measure that evaluates to a Target value or by entering an absolute value.</span></span> <span data-ttu-id="64aa6-152">在定义了基础度量值（值）和目标值之后，您可以定义基础值和目标值之间的状态阈值参数。</span><span class="sxs-lookup"><span data-stu-id="64aa6-152">After the Base measure (value) and Target value is defined, you can then define the status threshold parameters between the Base and Target values.</span></span> <span data-ttu-id="64aa6-153">使用可选的图标、条、图形或颜色以图形格式显示该状态。</span><span class="sxs-lookup"><span data-stu-id="64aa6-153">The status is displayed in a graphical format using selectable icons, bars, graphs, or colors.</span></span> <span data-ttu-id="64aa6-154">然后，可以将基础值和目标值以及状态以可以对其他数据字段执行切片操作的值的形式添加到报表或数据透视表中。</span><span class="sxs-lookup"><span data-stu-id="64aa6-154">The Base and Target values, as well as the Status can then be added to a report or PivotTable as values that can be sliced against other data fields.</span></span>  
  
 <span data-ttu-id="64aa6-155">若要查看“关键绩效指标”对话框，请在表的度量值网格中，右键单击将充当基础值的度量值，然后单击 **“创建 KPI”**。</span><span class="sxs-lookup"><span data-stu-id="64aa6-155">To view the Key Performance Indicator dialog box, in the measure grid for a table, right click a measure that will serve as the Base value, and then click **Create KPI**.</span></span> <span data-ttu-id="64aa6-156">在某一度量值已作为基础值扩展到 KPI 后，一个图标将出现在度量值网格中的该度量值名称旁，以便将该度量值标识为与某一 KPI 相关联。</span><span class="sxs-lookup"><span data-stu-id="64aa6-156">After a measure has been extended to a KPI as a Base value, an icon will appear alongside the measure name in the measure grid identifying the measure as associated with a KPI.</span></span>  
  
##  <a name="related-tasks"></a><a name="bkmk_related_tasks"></a> <span data-ttu-id="64aa6-157">相关任务</span><span class="sxs-lookup"><span data-stu-id="64aa6-157">Related Tasks</span></span>  
  
|<span data-ttu-id="64aa6-158">主题</span><span class="sxs-lookup"><span data-stu-id="64aa6-158">Topic</span></span>|<span data-ttu-id="64aa6-159">说明</span><span class="sxs-lookup"><span data-stu-id="64aa6-159">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="64aa6-160">创建和管理 KPI（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="64aa6-160">Create and Manage KPIs &#40;SSAS Tabular&#41;</span></span>](kpis-ssas-tabular.md)|<span data-ttu-id="64aa6-161">说明如何使用基础度量值、目标度量值和状态阈值创建 KPI。</span><span class="sxs-lookup"><span data-stu-id="64aa6-161">Describes how to create a KPI with a Base measure, a Target measure, and status thresholds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="64aa6-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="64aa6-162">See Also</span></span>  
 <span data-ttu-id="64aa6-163">[&#40;SSAS 表格&#41;度量值](measures-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="64aa6-163">[Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="64aa6-164">透视表（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="64aa6-164">Perspectives &#40;SSAS Tabular&#41;</span></span>](perspectives-ssas-tabular.md)  
  
  
