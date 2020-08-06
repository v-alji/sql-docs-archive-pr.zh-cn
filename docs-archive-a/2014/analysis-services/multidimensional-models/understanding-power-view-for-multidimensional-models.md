---
title: 了解多维模型的 Power View |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d0558cae-8209-4242-80c5-2c95981b88b9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 778bdb769238618e733e46f903cf70024cd27bff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689635"
---
# <a name="understanding-power-view-for-multidimensional-models"></a><span data-ttu-id="ce3e3-102">了解多维模型的 Power View</span><span class="sxs-lookup"><span data-stu-id="ce3e3-102">Understanding Power View for Multidimensional Models</span></span>
  <span data-ttu-id="ce3e3-103">本文介绍 Microsoft SQL Server 2014 中用于多维模型的 Power View 功能，并为希望在组织中实现多维模型的 Power View 的 BI 专业人员和管理员提供重要信息。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-103">This article describes the Power View for Multidimensional Models feature in Microsoft SQL Server 2014, and provides important information for BI professionals and administrators who intend to implement Power View for Multidimensional Models in their organization.</span></span>  
  
 <span data-ttu-id="ce3e3-104">多维模型提供业界领先的 OLAP 数据建模、存储和分析解决方案。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-104">Multidimensional models provide industry leading OLAP data modeling, storage, and analysis solutions.</span></span> <span data-ttu-id="ce3e3-105">SQL Server 2014 中的多维模型通过使用 Microsoft Power View 支持即席数据分析、探索和可视化。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-105">Multidimensional models in SQL Server 2014 support ad-hoc data analysis, exploration, and visualization by using Microsoft Power View.</span></span>  
  
 <span data-ttu-id="ce3e3-106">Power View 是一种瘦 Web 客户端，可通过 SharePoint 库的共享报表数据源 (.rsds) 文件在浏览器中启动。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-106">Power View is a thin web client that launches in the browser from a shared Report Data Source (.rsds) file in a SharePoint library.</span></span> <span data-ttu-id="ce3e3-107">报表数据源充当该客户端和后端数据源之间的桥梁。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-107">The Report Data Source acts as a bridge between the client and the back-end data source.</span></span> <span data-ttu-id="ce3e3-108">后端数据源可以是 SharePoint 中的 PowerPivot 工作簿、在表格模式下运行的 Analysis Services 服务器上的表格模型或在多维模式下运行的 Analysis Services 服务器上的多维模型。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-108">The back-end data source can be a PowerPivot workbook in SharePoint, a Tabular model on an Analysis Services server running in Tabular mode, or a Multidimensional model on an Analysis Services server running in Multidimensional mode.</span></span> <span data-ttu-id="ce3e3-109">然后，Power View 报表可以保存到 SharePoint 库并与您组织中的其他成员共享。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-109">Power View reports can then be saved to a SharePoint library or gallery and shared with other members in your organization.</span></span>  
  
 <span data-ttu-id="ce3e3-110">**多维模型体系结构的 Power View**</span><span class="sxs-lookup"><span data-stu-id="ce3e3-110">**Power View for Multidimensional Models architecture**</span></span>  
  
 <span data-ttu-id="ce3e3-111">![多维模型体系结构的 Power View](../media/daxmd-architecture.gif "多维模型体系结构的 Power View")</span><span class="sxs-lookup"><span data-stu-id="ce3e3-111">![Power View for Multidimensional Models Architecture](../media/daxmd-architecture.gif "Power View for Multidimensional Models Architecture")</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ce3e3-112">先决条件</span><span class="sxs-lookup"><span data-stu-id="ce3e3-112">Prerequisites</span></span>  
 <span data-ttu-id="ce3e3-113">**服务器要求**</span><span class="sxs-lookup"><span data-stu-id="ce3e3-113">**Server Requirements**</span></span>  
  
-   <span data-ttu-id="ce3e3-114">在多维模式下运行的附带 Analysis Services 的 SQL Server 2014 Enterprise 版本或 Business Intelligence 版本。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-114">SQL Server 2014 Enterprise or Business Intelligence edition with Analysis Services running in Multidimensional mode.</span></span>  
  
-   <span data-ttu-id="ce3e3-115">用于 Microsoft SharePoint Server 2010 或 2013 Enterprise 版本的 SQL Server 2014 Reporting Services 外接程序。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-115">SQL Server 2014 Reporting Services Add-in for Microsoft SharePoint Server 2010 or 2013 Enterprise Edition.</span></span>  
  
 <span data-ttu-id="ce3e3-116">**客户端要求**</span><span class="sxs-lookup"><span data-stu-id="ce3e3-116">**Client Requirements**</span></span>  
  
-   <span data-ttu-id="ce3e3-117">Power View 客户端功能需要 Microsoft Silverlight 5。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-117">Power View client functionality requires Microsoft Silverlight 5.</span></span> <span data-ttu-id="ce3e3-118">有关详细信息，请参阅[规划 Reporting Services 和 Power View 浏览器支持 &#40;Reporting Services 2014&#41;](../../reporting-services/browser-support-for-reporting-services-and-power-view.md)。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-118">For more information, see [Planning for Reporting Services and Power View Browser Support &#40;Reporting Services 2014&#41;](../../reporting-services/browser-support-for-reporting-services-and-power-view.md).</span></span>  
  
## <a name="features"></a><span data-ttu-id="ce3e3-119">功能</span><span class="sxs-lookup"><span data-stu-id="ce3e3-119">Features</span></span>  
 <span data-ttu-id="ce3e3-120">**对 Power View 的本机支持**</span><span class="sxs-lookup"><span data-stu-id="ce3e3-120">**Native support for Power View**</span></span>  
  
 <span data-ttu-id="ce3e3-121">在此版本中，多维模型通过使用 SharePoint 模式下的 Power View 支持分析和可视化。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-121">With this release, multidimensional models support analysis and visualization by using Power View in SharePoint mode.</span></span> <span data-ttu-id="ce3e3-122">无需对多维模型进行特殊配置。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-122">No special configuration of your multidimensional models is necessary.</span></span> <span data-ttu-id="ce3e3-123">但是，多维模型对象在 Power View 中的显示方式与在其他客户端工具（如 Microsoft Excel 和 Microsoft Performance Point）中的显示方式有一些区别。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-123">There are however some differences in how multidimensional model objects are displayed in Power View compared to other client tools such as Microsoft Excel and Microsoft Performance Point.</span></span> <span data-ttu-id="ce3e3-124">此版本不支持在 Excel 2013 中使用 Power View 来执行多维模型的分析和可视化。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-124">This release does not support analysis and visualization of multidimensional models by using Power View in Excel 2013.</span></span>  
  
 <span data-ttu-id="ce3e3-125">**对 DAX 查询的本机支持**</span><span class="sxs-lookup"><span data-stu-id="ce3e3-125">**Native support for DAX queries**</span></span>  
  
 <span data-ttu-id="ce3e3-126">在此版本中，多维模型除了支持更传统的 MDX 查询外，还支持 DAX 查询和函数。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-126">With this release, multidimensional models support DAX queries and functions in addition to more traditional MDX queries.</span></span> <span data-ttu-id="ce3e3-127">一些 DAX 函数（如 PATH）在多维建模中不适用。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-127">Some DAX functions, such as PATH, are not applicable in multidimensional modeling.</span></span> <span data-ttu-id="ce3e3-128">要更好了解 DAX 以及它与 MDX 的区别，请参阅 [数据分析表达式和 MDX](https://msdn.microsoft.com/library/ff487170\(SQL.105\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-128">For a better understanding of DAX and how it compares to MDX, see [Data Analysis Expressions and MDX](https://msdn.microsoft.com/library/ff487170\(SQL.105\).aspx).</span></span>  
  
## <a name="multidimensional-to-tabular-object-mapping"></a><span data-ttu-id="ce3e3-129">多维到表格对象映射</span><span class="sxs-lookup"><span data-stu-id="ce3e3-129">Multidimensional to tabular object mapping</span></span>  
 <span data-ttu-id="ce3e3-130">Analysis Services 提供多维模型的表格模型元数据表示形式。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-130">Analysis Services provides a tabular model metadata representation of a multidimensional model.</span></span> <span data-ttu-id="ce3e3-131">多维模型中的对象表示为 Power View 和 CSDL out（带 BI 注释）中的表格对象。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-131">Objects in a multidimensional model are represented as tabular objects in Power View and in CSDL out with BI annotations.</span></span>  
  
 <span data-ttu-id="ce3e3-132">**对象映射汇总**</span><span class="sxs-lookup"><span data-stu-id="ce3e3-132">**Object mapping summary**</span></span>  
  
|<span data-ttu-id="ce3e3-133">多维对象</span><span class="sxs-lookup"><span data-stu-id="ce3e3-133">Multidimensional Object</span></span>|<span data-ttu-id="ce3e3-134">表格对象</span><span class="sxs-lookup"><span data-stu-id="ce3e3-134">Tabular Object</span></span>|  
|-----------------------------|--------------------|  
|<span data-ttu-id="ce3e3-135">多维数据集</span><span class="sxs-lookup"><span data-stu-id="ce3e3-135">Cube</span></span>|<span data-ttu-id="ce3e3-136">模型</span><span class="sxs-lookup"><span data-stu-id="ce3e3-136">Model</span></span>|  
|<span data-ttu-id="ce3e3-137">多维数据集维度</span><span class="sxs-lookup"><span data-stu-id="ce3e3-137">Cube Dimension</span></span>|<span data-ttu-id="ce3e3-138">表</span><span class="sxs-lookup"><span data-stu-id="ce3e3-138">Table</span></span>|  
|<span data-ttu-id="ce3e3-139">维度属性（键、名称）</span><span class="sxs-lookup"><span data-stu-id="ce3e3-139">Dimension Attributes (Key(s), Name)</span></span>|<span data-ttu-id="ce3e3-140">列</span><span class="sxs-lookup"><span data-stu-id="ce3e3-140">Column</span></span>|  
|<span data-ttu-id="ce3e3-141">度量值组</span><span class="sxs-lookup"><span data-stu-id="ce3e3-141">Measure Group</span></span>|<span data-ttu-id="ce3e3-142">表</span><span class="sxs-lookup"><span data-stu-id="ce3e3-142">Table</span></span>|  
|<span data-ttu-id="ce3e3-143">度量</span><span class="sxs-lookup"><span data-stu-id="ce3e3-143">Measure</span></span>|<span data-ttu-id="ce3e3-144">度量</span><span class="sxs-lookup"><span data-stu-id="ce3e3-144">Measure</span></span>|  
|<span data-ttu-id="ce3e3-145">不具有度量值组的度量值</span><span class="sxs-lookup"><span data-stu-id="ce3e3-145">Measure without Measure Group</span></span>|<span data-ttu-id="ce3e3-146">在名为 Measures 的表中</span><span class="sxs-lookup"><span data-stu-id="ce3e3-146">In a table named Measures</span></span>|  
|<span data-ttu-id="ce3e3-147">度量值组多维数据集维度关系</span><span class="sxs-lookup"><span data-stu-id="ce3e3-147">Measure Group Cube Dimension Relationship</span></span>|<span data-ttu-id="ce3e3-148">关系</span><span class="sxs-lookup"><span data-stu-id="ce3e3-148">Relationship</span></span>|  
|<span data-ttu-id="ce3e3-149">透视</span><span class="sxs-lookup"><span data-stu-id="ce3e3-149">Perspective</span></span>|<span data-ttu-id="ce3e3-150">透视</span><span class="sxs-lookup"><span data-stu-id="ce3e3-150">Perspective</span></span>|  
|<span data-ttu-id="ce3e3-151">KPI</span><span class="sxs-lookup"><span data-stu-id="ce3e3-151">KPI</span></span>|<span data-ttu-id="ce3e3-152">KPI</span><span class="sxs-lookup"><span data-stu-id="ce3e3-152">KPI</span></span>|  
|<span data-ttu-id="ce3e3-153">用户/父子层次结构</span><span class="sxs-lookup"><span data-stu-id="ce3e3-153">User/Parent-Child Hierarchies</span></span>|<span data-ttu-id="ce3e3-154">层次结构</span><span class="sxs-lookup"><span data-stu-id="ce3e3-154">Hierarchy</span></span>|  
|<span data-ttu-id="ce3e3-155">显示文件夹</span><span class="sxs-lookup"><span data-stu-id="ce3e3-155">Display Folder</span></span>|<span data-ttu-id="ce3e3-156">显示文件夹</span><span class="sxs-lookup"><span data-stu-id="ce3e3-156">Display Folder</span></span>|  
  
## <a name="measures-measure-groups-and-kpis"></a><span data-ttu-id="ce3e3-157">度量值、度量值组和 KPI</span><span class="sxs-lookup"><span data-stu-id="ce3e3-157">Measures, measure groups, and KPIs</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce3e3-158">本文中的一些图像和文本源自 SQL Server 2012 示例数据库的 Adventure Works 多维模型。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-158">Some images and text in this article refer to the Adventure Works Multidimensional Model for SQL Server 2012 sample database.</span></span>  
  
 <span data-ttu-id="ce3e3-159">多维数据集中的度量值组在 Power View 字段列表中显示为带 sigma (∑) 符号的表。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-159">Measure groups in a multidimensional cube are seen in the Power View Field List as tables with the sigma (∑) sign.</span></span>  
  
 <span data-ttu-id="ce3e3-160">**Power View 字段列表中的度量值组**</span><span class="sxs-lookup"><span data-stu-id="ce3e3-160">**Measure groups in the Power View Field List**</span></span>  
  
 <span data-ttu-id="ce3e3-161">![Power View 中的字段列表](../media/daxmd-powerviewfieldlist.gif "Power View 中的字段列表")</span><span class="sxs-lookup"><span data-stu-id="ce3e3-161">![Field List in Power View](../media/daxmd-powerviewfieldlist.gif "Field List in Power View")</span></span>  
  
 <span data-ttu-id="ce3e3-162">度量值组内的度量值显示为度量值。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-162">Measures within a measure group appear as measures.</span></span> <span data-ttu-id="ce3e3-163">如果存在不具有相关度量值组的计算度量值，则会将它们分组在名为 Measures 的特定表下。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-163">If there are calculated measures that do not have an associated measure group, they will be grouped under a special table called Measures.</span></span>  
  
 <span data-ttu-id="ce3e3-164">为了帮助简化更复杂的多维模型，模型作者可以在多维数据集中定义要位于某个显示文件夹内的一组度量值或 KPI。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-164">To help simplify more complex multidimensional models, model authors can define a set of measures or KPIs in a cube to be located within a display folder.</span></span> <span data-ttu-id="ce3e3-165">Power View 可以显示显示文件夹和其中的度量值以及 KPI。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-165">Power View can show display folders and the measures and KPIs in them.</span></span>  
  
 <span data-ttu-id="ce3e3-166">**度量值组中的度量值和 KPI**</span><span class="sxs-lookup"><span data-stu-id="ce3e3-166">**Measures and KPIs in a measure group**</span></span>  
  
 <span data-ttu-id="ce3e3-167">![Power View 字段列表中的度量组](../media/daxmd-fieldlist-group.gif "Power View 字段列表中的度量组")</span><span class="sxs-lookup"><span data-stu-id="ce3e3-167">![Measure group in Power View Field List](../media/daxmd-fieldlist-group.gif "Measure group in Power View Field List")</span></span>  
  
### <a name="measures-as-variants"></a><span data-ttu-id="ce3e3-168">作为变体的度量值</span><span class="sxs-lookup"><span data-stu-id="ce3e3-168">Measures as variants</span></span>  
 <span data-ttu-id="ce3e3-169">多维模型中的度量值是变体。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-169">Measures in multidimensional models are variants.</span></span> <span data-ttu-id="ce3e3-170">这意味着度量值不强类型化，可以具有不同的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-170">This means the measures are not strongly typed and can have different data types.</span></span> <span data-ttu-id="ce3e3-171">例如，在下图中，默认情况下，财务报告表中的金额度量值为 Currency 数据类型，但对于 "统计帐户" （字符串数据类型），还具有字符串值 "NA"。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-171">For example, in the image below, the Amount measure in the Financial Reporting table by default is Currency data type, but also has a string value "NA" for the sub-total of "Statistical Accounts", which is String data type.</span></span> <span data-ttu-id="ce3e3-172">Power View 识别某些作为变体的度量值并在不同可视化对象中显示正确的值和格式。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-172">Power View recognizes certain measures as variants and shows the correct values and formatting in the different visualizations.</span></span>  
  
 <span data-ttu-id="ce3e3-173">**作为变体的度量值**</span><span class="sxs-lookup"><span data-stu-id="ce3e3-173">**Measure as variant**</span></span>  
  
 <span data-ttu-id="ce3e3-174">![Power View 中不可聚合的层次结构](../media/daxmd-nonaggrattrib.gif "Power View 中不可聚合的层次结构")</span><span class="sxs-lookup"><span data-stu-id="ce3e3-174">![Non-aggregatable hierarchy in Power View](../media/daxmd-nonaggrattrib.gif "Non-aggregatable hierarchy in Power View")</span></span>  
  
### <a name="implicit-measures"></a><span data-ttu-id="ce3e3-175">隐式度量值</span><span class="sxs-lookup"><span data-stu-id="ce3e3-175">Implicit measures</span></span>  
 <span data-ttu-id="ce3e3-176">\*\* 表格模型允许用户创建“隐式”度量值，如对字段的计数、求和或计算平均值。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-176">Tabular models provide users the ability to create *implicit* measures such as count, sum, or average on fields.</span></span> <span data-ttu-id="ce3e3-177">对于多维模型，因为维度属性数据以不同方式存储，查询隐式度量值可能需要很长时间。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-177">For multidimensional models, because dimension attribute data is stored is stored differently, querying implicit measures can take a long time.</span></span> <span data-ttu-id="ce3e3-178">因此，在 Power View 中不提供隐式度量值。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-178">Because of this, implicit measures are not available in Power View.</span></span>  
  
## <a name="dimensions-attributes-and-hierarchies"></a><span data-ttu-id="ce3e3-179">维度、属性和层次结构</span><span class="sxs-lookup"><span data-stu-id="ce3e3-179">Dimensions, attributes, and hierarchies</span></span>  
 <span data-ttu-id="ce3e3-180">多维数据集维度显示为表格元数据中的表。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-180">Cube dimensions are exposed as tables in tabular metadata.</span></span> <span data-ttu-id="ce3e3-181">在 Power View 字段列表中，维度属性在显示文件夹中显示为列。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-181">In the Power View Field List, dimension attributes are shown as columns within display folders.</span></span>  <span data-ttu-id="ce3e3-182">其 AttributeHierarchyEnabled 属性设置为 false（例如 Customer 维度中的 Birth Date 属性）或 AttributeHierarchyVisible 属性设置为 false 的维度属性将不显示在 Power View 字段列表中。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-182">The dimension attributes that have the AttributeHierarchyEnabled property set to false; for example: Birth Date attribute in Customer dimension, or AttributeHierarchyVisible property set to false will not appear in the Power View Field List.</span></span> <span data-ttu-id="ce3e3-183">多级层次结构或用户层次结构（例如 Customer 维度中的 Customer Geography）显示为 Power View 字段列表中的层次结构。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-183">Multi-level hierarchies or user hierarchies; for example Customer Geography in the Customer dimension, are exposed as hierarchies in the Power View Field List.</span></span> <span data-ttu-id="ce3e3-184">维度属性的隐藏 UnknownMember 在 DAX 查询和 Power View 中显示。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-184">Hidden UnknownMembers of a dimension attribute are exposed in DAX Queries and in Power View.</span></span>  
  
 <span data-ttu-id="ce3e3-185">**SQL Server Data Tools (SSDT) 和 Power View 字段列表中的维度、属性和层次结构**</span><span class="sxs-lookup"><span data-stu-id="ce3e3-185">**Dimension, attributes and hierarchies in SQL Server Data Tools (SSDT) and Power View Field List**</span></span>  
  
 <span data-ttu-id="ce3e3-186">![SSDT 以及 Power View 字段列表中的维度](../media/daxmd-ssdt-dimensions.gif "SSDT 以及 Power View 字段列表中的维度")</span><span class="sxs-lookup"><span data-stu-id="ce3e3-186">![Dimensions in SSDT and in Power View Field List](../media/daxmd-ssdt-dimensions.gif "Dimensions in SSDT and in Power View Field List")</span></span>  
  
### <a name="dimension-attribute-type"></a><span data-ttu-id="ce3e3-187">维度属性类型</span><span class="sxs-lookup"><span data-stu-id="ce3e3-187">Dimension attribute type</span></span>  
 <span data-ttu-id="ce3e3-188">多维模型支持将维度属性与特定维度属性类型关联。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-188">Multidimensional models support associating dimension attributes with specific dimension attribute types.</span></span> <span data-ttu-id="ce3e3-189">下图显示 Geography 维度，其中 City、State-Province、Country 和 Postal Code 维度属性具有与其相关的地理类型。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-189">The image below shows the Geography dimension where the City, State-Province, Country and Postal Code dimension attributes have geography types associated with them.</span></span> <span data-ttu-id="ce3e3-190">它们在表格元数据中显示。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-190">These are exposed in the tabular metadata.</span></span> <span data-ttu-id="ce3e3-191">Power View 识别元数据，这允许用户创建地图可视化对象。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-191">Power View recognizes the metadata enabling users to create map visualizations.</span></span> <span data-ttu-id="ce3e3-192">它由 Power View 字段列表中 Geography 表的 City、Country、Postal Code 和 State-Province 列旁边的地图图标指示。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-192">This is indicated by the map icon next to the City, Country, Postal Code and State-Province columns in the Geography table in the Power View Field List.</span></span>  
  
 <span data-ttu-id="ce3e3-193">**SSDT 和 Power View 字段列表中的维度属性地理类型**</span><span class="sxs-lookup"><span data-stu-id="ce3e3-193">**Dimension attribute geography types in SSDT and Power View Field List**</span></span>  
  
 <span data-ttu-id="ce3e3-194">![维度特性地理类型](../media/daxmd-ssdt-attribute-geog-types.gif "维度特性地理类型")</span><span class="sxs-lookup"><span data-stu-id="ce3e3-194">![Dimension attribute geography types](../media/daxmd-ssdt-attribute-geog-types.gif "Dimension attribute geography types")</span></span>  
  
### <a name="dimension-calculated-members"></a><span data-ttu-id="ce3e3-195">维度的计算成员</span><span class="sxs-lookup"><span data-stu-id="ce3e3-195">Dimension calculated members</span></span>  
 <span data-ttu-id="ce3e3-196">多维模型支持具有单个真实成员的所有子级的计算成员。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-196">Multidimensional models support calculated members for child of All with a single real member.</span></span> <span data-ttu-id="ce3e3-197">显示此类型的计算成员时应用的额外约束如下：</span><span class="sxs-lookup"><span data-stu-id="ce3e3-197">Additional constraints while exposing this type of calculated member are:</span></span>  
  
-   <span data-ttu-id="ce3e3-198">必须是单个真实成员（维度具有多个属性时）。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-198">Must be a single real member when the dimension has more than one attribute.</span></span>  
  
-   <span data-ttu-id="ce3e3-199">包含计算成员的属性不能是维度的键属性，除非它是仅有的一个属性。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-199">An attribute containing calculated members cannot be the key attribute of the dimension unless it is the only attribute.</span></span>  
  
-   <span data-ttu-id="ce3e3-200">包含计算成员的属性不能是父子属性。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-200">An attribute containing calculated members cannot be a parent-child attribute.</span></span>  
  
 <span data-ttu-id="ce3e3-201">用户层次结构的计算成员不在 Power View 中显示，但是，最终用户仍可以连接到用户层次结构上包含计算成员的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-201">Calculated members of user hierarchies are not exposed in Power View; however, end-users will still be able to connect to a cube containing calculated members on user hierarchies.</span></span>  
  
 <span data-ttu-id="ce3e3-202">下图显示的是一个多维数据集的 Power View 报表，其中包含 Date 维度中维度属性 "会计日期计算" 上的时间智能计算成员。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-202">The image below shows a Power View report for a cube that contains time-intelligence calculated members on dimension attribute "Fiscal Date Calculations" in the Date dimension.</span></span>  
  
 <span data-ttu-id="ce3e3-203">**具有计算成员的 Power View 报表**</span><span class="sxs-lookup"><span data-stu-id="ce3e3-203">**Power View report with calculated members**</span></span>  
  
 <span data-ttu-id="ce3e3-204">![Power View 中的计算成员](../media/daxmd-calcmembersinpowerview.gif "Power View 中的计算成员")</span><span class="sxs-lookup"><span data-stu-id="ce3e3-204">![Calculated members in Power View](../media/daxmd-calcmembersinpowerview.gif "Calculated members in Power View")</span></span>  
  
### <a name="default-members"></a><span data-ttu-id="ce3e3-205">默认成员</span><span class="sxs-lookup"><span data-stu-id="ce3e3-205">Default members</span></span>  
 <span data-ttu-id="ce3e3-206">多维模型支持维度属性的默认成员。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-206">Multidimensional models support default members for dimension attributes.</span></span> <span data-ttu-id="ce3e3-207">当为查询聚合数据时，Analysis Services 使用默认成员。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-207">The default member is used by Analysis Services when aggregating data for a query.</span></span> <span data-ttu-id="ce3e3-208">维度属性的默认成员显示为表格元数据中相应列的默认值或筛选器。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-208">The default member of a dimension attribute is exposed as default value or filter for the corresponding column in the tabular metadata.</span></span>  
  
 <span data-ttu-id="ce3e3-209">应用属性时，Power View 的行为与 Excel 数据透视表基本相同。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-209">Power View behaves much the same as Excel PivotTables when attributes are applied.</span></span> <span data-ttu-id="ce3e3-210">用户将列添加到包含默认值的 Power View 可视化对象（表、矩阵或图表）时，将不应用默认值而是显示所有可用值。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-210">When a user adds a column to a Power View visualization (table, matrix, or chart) that contains a default value, the default value will not be applied and all available values are shown.</span></span> <span data-ttu-id="ce3e3-211">如果用户将列添加到筛选器，将应用默认值。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-211">If the user adds the column to Filters, the default value will be applied.</span></span>  
  
### <a name="dimension-security"></a><span data-ttu-id="ce3e3-212">维度安全性</span><span class="sxs-lookup"><span data-stu-id="ce3e3-212">Dimension security</span></span>  
 <span data-ttu-id="ce3e3-213">多维模型通过角色支持维度和单元级安全性。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-213">Multidimensional models support dimension and cell level security through roles.</span></span> <span data-ttu-id="ce3e3-214">使用 Power View 连接到多维数据集的用户需要经过身份验证并判断他是否具有合适的权限。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-214">A user connecting to a cube by using Power View is authenticated and evaluated for appropriate permissions.</span></span> <span data-ttu-id="ce3e3-215">应用维度安全性时，Power View 中的用户将看不到相应的维度成员；但是如果用户定义了限制某些单元的单元安全性权限，则该用户无法使用 Power View 连接到多维数据集。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-215">When dimension security is applied, the respective dimension members will not be seen by the user in Power View; however if a user has a cell security permission defined where certain cells are restricted, then that user cannot connect to the cube with Power View.</span></span> <span data-ttu-id="ce3e3-216">在某些情况下，在从受保护的数据计算一部分数据时用户可以看到聚合的数据。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-216">In some cases, users can see aggregate data when portions of that data are calculated from secured data.</span></span>  
  
### <a name="non-aggregatable-attributeshierarchies"></a><span data-ttu-id="ce3e3-217">不可聚合的属性/层次结构</span><span class="sxs-lookup"><span data-stu-id="ce3e3-217">Non-aggregatable attributes/hierarchies</span></span>  
 <span data-ttu-id="ce3e3-218">在多维模型中，维度的属性可能将 IsAggregatable 属性设置为 false。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-218">In a multidimensional model, attributes of a dimension can have the IsAggregatable property set to false.</span></span> <span data-ttu-id="ce3e3-219">这意味着模型作者已指定当客户端应用程序查询数据时，不应聚合层次结构（属性或多个级别）上的数据。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-219">This means the model author has specified client applications should not aggregate the data across hierarchies (attribute or multi-level) when they query the data.</span></span> <span data-ttu-id="ce3e3-220">在 Power View 中，此维度属性显示为无法计算小计的列。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-220">In Power View, this dimension attribute is exposed as a column for which sub-totals are not available.</span></span> <span data-ttu-id="ce3e3-221">在下图中，您可以看到一个不可聚合的层次结构的示例：Accounts。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-221">In the image below, you can see an example of a non-aggregatable hierarchy: Accounts.</span></span> <span data-ttu-id="ce3e3-222">Accounts 父子层次结构的最高级别是不可聚合的，而其他级别则可以聚合。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-222">The top-most level of the Accounts parent-child hierarchy is non-aggregatable while other levels are aggregatable.</span></span> <span data-ttu-id="ce3e3-223">在 Accounts 层次结构的矩阵可视化对象（前两个级别）中，您看到 Account Level 02 的小计但是看不到最高级别 (Account Level 01) 的小计。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-223">In a matrix visualization of the Accounts hierarchy (first two levels), you see sub-totals for Account Level 02 but not for the top-most level, Account Level 01.</span></span>  
  
 <span data-ttu-id="ce3e3-224">**Power View 中不可聚合的层次结构**</span><span class="sxs-lookup"><span data-stu-id="ce3e3-224">**Non-aggregatable hierarchy in Power View**</span></span>  
  
 <span data-ttu-id="ce3e3-225">![Power View 中不可聚合的层次结构](../media/daxmd-nonaggrattrib.gif "Power View 中不可聚合的层次结构")</span><span class="sxs-lookup"><span data-stu-id="ce3e3-225">![Non-aggregatable hierarchy in Power View](../media/daxmd-nonaggrattrib.gif "Non-aggregatable hierarchy in Power View")</span></span>  
  
## <a name="images"></a><span data-ttu-id="ce3e3-226">映像</span><span class="sxs-lookup"><span data-stu-id="ce3e3-226">Images</span></span>  
 <span data-ttu-id="ce3e3-227">Power View 可呈现图像。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-227">Power View provides the ability to render images.</span></span> <span data-ttu-id="ce3e3-228">在多维模型中，您向 Power View 提供图像的方式之一是公开图像的包含 URL（统一资源定位符）的列。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-228">In multidimensional models, one of the ways you can provide images to Power View is to expose columns containing URLs (Uniform Resource Locator) of the images.</span></span> <span data-ttu-id="ce3e3-229">在此版本中，Analysis Services 支持将维度属性标记为类型 ImageURL。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-229">With this release, Analysis Services supports tagging dimension attributes as type ImageURL.</span></span> <span data-ttu-id="ce3e3-230">然后通过表格元数据将此数据类型提供给 Power View。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-230">This data type is then provided to Power View in the tabular metadata.</span></span> <span data-ttu-id="ce3e3-231">Power View 然后可以下载并在可视化对象内显示 URL 中指定的图像。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-231">Power View can then download and display the images specified in the URLs within visualizations.</span></span>  
  
 <span data-ttu-id="ce3e3-232">**SSDT 中的 ImageURL 维度属性类型**</span><span class="sxs-lookup"><span data-stu-id="ce3e3-232">**ImageURL dimension attribute type in SSDT**</span></span>  
  
 <span data-ttu-id="ce3e3-233">![维度特性属性](../media/daxmd-dimattribute-properties.gif "维度特性属性")</span><span class="sxs-lookup"><span data-stu-id="ce3e3-233">![Dimension attribute properties](../media/daxmd-dimattribute-properties.gif "Dimension attribute properties")</span></span>  
  
## <a name="parent-child-hierarchies"></a><span data-ttu-id="ce3e3-234">父子层次结构</span><span class="sxs-lookup"><span data-stu-id="ce3e3-234">Parent-child hierarchies</span></span>  
 <span data-ttu-id="ce3e3-235">多维模型支持父子层次结构，这些结构显示为表格元数据中的层次结构。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-235">Multidimensional models support parent-child hierarchies, which are exposed as a hierarchy in the tabular metadata.</span></span> <span data-ttu-id="ce3e3-236">父子层次结构的每个级别显示为隐藏的列。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-236">Each level of the parent-child hierarchy is exposed as a hidden column.</span></span> <span data-ttu-id="ce3e3-237">父子维度的键属性不在表格元数据内显示。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-237">The key attribute of the parent-child dimension is not exposed in the tabular metadata.</span></span>  
  
 <span data-ttu-id="ce3e3-238">**Power View 中的父子层次结构**</span><span class="sxs-lookup"><span data-stu-id="ce3e3-238">**Parent-child hierarchies in Power View**</span></span>  
  
 <span data-ttu-id="ce3e3-239">![父子层次结构](../media/daxmd-ssdt-hierarchies.gif "父子层次结构")</span><span class="sxs-lookup"><span data-stu-id="ce3e3-239">![Parent-child hierarchies](../media/daxmd-ssdt-hierarchies.gif "Parent-child hierarchies")</span></span>  
  
## <a name="perspectives-and-translations"></a><span data-ttu-id="ce3e3-240">透视和翻译</span><span class="sxs-lookup"><span data-stu-id="ce3e3-240">Perspectives and translations</span></span>  
 <span data-ttu-id="ce3e3-241">透视是多维数据集的视图，其中仅在客户端工具中显示某些维度或度量值组。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-241">Perspectives are views of cubes where only certain dimensions or measure groups are visible in client tools.</span></span> <span data-ttu-id="ce3e3-242">您可以指定透视名称作为 Cube 连接字符串属性的值。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-242">You can specify a perspective name as a value to the Cube connection string property.</span></span> <span data-ttu-id="ce3e3-243">例如，在以下连接字符串中，"Direct Sales" 是多维模型中的一个透视：</span><span class="sxs-lookup"><span data-stu-id="ce3e3-243">For example, in the following connection string, 'Direct Sales' is a perspective in the multidimensional model:</span></span>  
  
 `Data Source=localost;Initial Catalog=AdventureWorksDW-MD;Cube='Direct Sales'`  
  
 <span data-ttu-id="ce3e3-244">多维数据集可以具有元数据和为模型内各种语言指定的数据翻译。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-244">Cubes can have metadata and data translations specified for various Languages within the model.</span></span> <span data-ttu-id="ce3e3-245">若要查看 (数据和元数据的翻译) 需要向 .RSDS 文件中的连接字符串添加可选的 "区域设置标识符" 属性，如下所示。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-245">In order to see the translations (data and metadata) you need to add the optional "Locale Identifier" property to the connection string in the RSDS file as shown below.</span></span>  
  
 `Data Source=localost;Initial Catalog=AdventureWorksDW-MD;Cube='Adventure Works'; Locale Identifier=3084`  
  
 <span data-ttu-id="ce3e3-246">Power View 连接到具有“Locale Identifier”的 .rsds 文件内的多维模型时，如果多维数据集中包含相应的翻译，用户将在 Power View 中看到翻译。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-246">When Power View connects to a multidimensional model with an .rsds file that has a Locale Identifier, and if a corresponding translation is contained in the cube, users will see the translations in Power View.</span></span>  
  
 <span data-ttu-id="ce3e3-247">有关详细信息，请参阅 [Create a Report Data Source](create-a-report-data-source.md)。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-247">For more information, see [Create a Report Data Source](create-a-report-data-source.md).</span></span>  
  
## <a name="power-view-pinned-filters"></a><span data-ttu-id="ce3e3-248">Power View 固定的筛选器</span><span class="sxs-lookup"><span data-stu-id="ce3e3-248">Power View pinned filters</span></span>  
 <span data-ttu-id="ce3e3-249">Power View 报表可以包含多个视图。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-249">Power View reports can contain multiple views.</span></span> <span data-ttu-id="ce3e3-250">\*\* 在此版本中，用于表格模型和多维模型的“固定筛选器”功能可创建适用于报表中所有视图的筛选器。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-250">With this release, the *Pin Filter* feature for both tabular and multidimensional models provides the ability to create filters that apply across all views in a report.</span></span> <span data-ttu-id="ce3e3-251">下图显示视图筛选器的“固定筛选器”切换按钮。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-251">The image below shows the Pin filter toggle button for a view filter.</span></span> <span data-ttu-id="ce3e3-252">默认情况下，取消固定视图筛选器，使之仅适用于该视图。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-252">By default, a view filter is unpinned and applies only to that view.</span></span> <span data-ttu-id="ce3e3-253">固定视图筛选器会使筛选器适用于所有视图，取消固定它则将该筛选器从其他视图中删除。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-253">Pinning a view filter applies it to all views; unpinning it removes it from other views.</span></span>  
  
 <span data-ttu-id="ce3e3-254">**固定的筛选器**</span><span class="sxs-lookup"><span data-stu-id="ce3e3-254">**Pinned Filters**</span></span>  
  
 <span data-ttu-id="ce3e3-255">![固定筛选器](../media/daxmd-pinnedfilterinpowerview.gif "固定筛选器")</span><span class="sxs-lookup"><span data-stu-id="ce3e3-255">![Pinned Filter](../media/daxmd-pinnedfilterinpowerview.gif "Pinned Filter")</span></span>  
  
## <a name="unsupported-features"></a><span data-ttu-id="ce3e3-256">不支持的功能</span><span class="sxs-lookup"><span data-stu-id="ce3e3-256">Unsupported features</span></span>  
 <span data-ttu-id="ce3e3-257">**Excel 2013 中的 Power View** -不支持连接到多维模型的报表和创建报表。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-257">**Power View in Excel 2013** - does not support connecting to and creating reports for multidimensional models.</span></span> <span data-ttu-id="ce3e3-258">Power View for Multidimensional Models 仅支持基于浏览器的 Power View 客户端。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-258">Power View for multidimensional models supports browser based Power View clients only.</span></span>  
  
 <span data-ttu-id="ce3e3-259">**操作** - 在 Power View 报表或针对多维模型的 DAX 查询中不受支持。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-259">**Actions** - are not supported in Power View reports or in DAX queries against a multidimensional model.</span></span>  
  
 <span data-ttu-id="ce3e3-260">**已命名的集** - 在多维模型中，在 Power View 或针对多维模型的 DAX 查询中不支持已命名的集。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-260">**Named sets** - in multidimensional models, are not supported in Power View or in DAX queries against a multidimensional model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce3e3-261">不支持的操作和已命名的集不阻止用户使用 Power View 连接到多维模型并利用它。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-261">Unsupported Actions and Named sets do not prevent users from connecting to and exploring multidimensional models using Power View.</span></span>  
  
 <span data-ttu-id="ce3e3-262">**单元级别安全性**-在 Power View 报表中不受支持。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-262">**Cell level security** - is not supported in Power View reports.</span></span>  
  
## <a name="csdlbi-annotations"></a><span data-ttu-id="ce3e3-263">CSDLBI 注释</span><span class="sxs-lookup"><span data-stu-id="ce3e3-263">CSDLBI Annotations</span></span>  
 <span data-ttu-id="ce3e3-264">多维数据集元数据被带商业智能注释的概念架构定义语言 (CSDLBI) 作为基于实体数据模型 (EDM) 的概念模型显示。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-264">Multidimensional cube metadata is exposed as an Entity Data Model (EDM) based conceptual model by Conceptual Schema Definition Language with Business Intelligence annotations (CSDLBI).</span></span>  
  
 <span data-ttu-id="ce3e3-265">将 DISCOVER_CSDL_METADATA 请求发送到 Analysis Services 实例时，将多维元数据表示为 CSDLBI 文档或 CSDL out 中的表格模型命名空间。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-265">Multidimensional metadata is represented as a tabular model namespace in a CSDLBI document, or CSDL out, when a DISCOVER_CSDL_METADATA request is sent to the Analysis Services instance.</span></span>  
  
 <span data-ttu-id="ce3e3-266">**示例 DISCOVER_CSDL_METADATA 请求**</span><span class="sxs-lookup"><span data-stu-id="ce3e3-266">**Sample DISCOVER_CSDL_METADATA request**</span></span>  
  
```  
<Envelopexmlns="http://schemas.xmlsoap.org/soap/envelope/">  
   <Body>  
      <Discoverxmlns="urn:schemas-microsoft-com:xml-analysis">  
         <RequestType>DISCOVER_CSDL_METADATA</RequestType>  
         <Restrictions>  
            <RestrictionList>  
              <CATALOG_NAME>"catalogname"<CATALOG_NAME>  
            </RestrictionList>  
         </Restrictions>  
         <Properties>  
            <PropertyList>  
            </PropertyList>  
         </Properties>  
      </Discover>  
   </Body>  
</Envelope>  
  
```  
  
 <span data-ttu-id="ce3e3-267">DISCOVER_CSDL_METADATA 请求具有以下限制：</span><span class="sxs-lookup"><span data-stu-id="ce3e3-267">DISCOVER_CSDL_METADATA request has the following restrictions:</span></span>  
  
|<span data-ttu-id="ce3e3-268">名称</span><span class="sxs-lookup"><span data-stu-id="ce3e3-268">Name</span></span>|<span data-ttu-id="ce3e3-269">必须</span><span class="sxs-lookup"><span data-stu-id="ce3e3-269">Required</span></span>|<span data-ttu-id="ce3e3-270">说明</span><span class="sxs-lookup"><span data-stu-id="ce3e3-270">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="ce3e3-271">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="ce3e3-271">CATALOG_NAME</span></span>|<span data-ttu-id="ce3e3-272">是</span><span class="sxs-lookup"><span data-stu-id="ce3e3-272">Yes</span></span>|<span data-ttu-id="ce3e3-273">目录\数据库名称。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-273">The catalog\database name.</span></span>|  
|<span data-ttu-id="ce3e3-274">PERSPECTIVE_NAME</span><span class="sxs-lookup"><span data-stu-id="ce3e3-274">PERSPECTIVE_NAME</span></span>|<span data-ttu-id="ce3e3-275">是（如果多维数据集包含多个透视）。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-275">Yes, if the cube contains more than one perspective.</span></span> <span data-ttu-id="ce3e3-276">如果只有一个多维数据集或有一个默认透视，则为可选的。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-276">Optional if there is only one cube or there is a default perspective.</span></span>|<span data-ttu-id="ce3e3-277">多维数据库中的多维数据集名称或透视名称。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-277">The cube name or perspective name in the multidimensional database.</span></span>|  
|<span data-ttu-id="ce3e3-278">VERSION</span><span class="sxs-lookup"><span data-stu-id="ce3e3-278">VERSION</span></span>|<span data-ttu-id="ce3e3-279">是</span><span class="sxs-lookup"><span data-stu-id="ce3e3-279">Yes</span></span>|<span data-ttu-id="ce3e3-280">客户端请求的 CSDL 版本。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-280">CSDL version requested by client.</span></span> <span data-ttu-id="ce3e3-281">在版本 2.0 中支持多维功能和构造。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-281">Multidimensional features and constructs are supported in version 2.0.</span></span>|  
  
 <span data-ttu-id="ce3e3-282">返回的 CSDL out 文档将模型表示为命名空间，其中包含实体、关联和属性。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-282">The return CSDL out document represents the model as a namespace, containing entities, associations, and properties.</span></span>  
  
 <span data-ttu-id="ce3e3-283">有关表格模型的 CSDLBI 注释的详细信息，请参阅 MSDN 上的 [用于商业智能的 CSDL 注释技术参考](/analysis-services/csdlbi/technical-reference-for-bi-annotations-to-csdl) 和 [\[MS-CSDLBI\]：带商业智能注释的概念架构定义文件格式](https://msdn.microsoft.com/library/jj161299\(SQL.105\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="ce3e3-283">For more detailed information about CSDLBI annotations for tabular models, see [Technical Reference for BI Annotations to CSDL](/analysis-services/csdlbi/technical-reference-for-bi-annotations-to-csdl) on MSDN, and [\[MS-CSDLBI\]: Conceptual Schema Definitions File Format with Business Intelligence Annotations](https://msdn.microsoft.com/library/jj161299\(SQL.105\).aspx).</span></span>  
  
## <a name="client-help-on-officecom"></a><span data-ttu-id="ce3e3-284">Office.com 上的客户端帮助</span><span class="sxs-lookup"><span data-stu-id="ce3e3-284">Client Help on Office.com</span></span>  
 <span data-ttu-id="ce3e3-285">Office.com 上提供以下文章来帮助用户了解多维模型对象在 Power View 中的显示方式以及如何创建示例报表：</span><span class="sxs-lookup"><span data-stu-id="ce3e3-285">The following articles are provided on Office.com to help users learn about how Multidimensional Model objects appear in Power View and how to create a sample report:</span></span>  
  
 [<span data-ttu-id="ce3e3-286">了解 Power View 中的多维模型对象</span><span class="sxs-lookup"><span data-stu-id="ce3e3-286">Understanding Multidimensional Model Objects in Power View</span></span>](https://office.microsoft.com/excel-help/understanding-multidimensional-model-objects-in-power-view-HA104018589.aspx)  
  
 [<span data-ttu-id="ce3e3-287">通过使用 Power View 了解 Adventure Works 多维模型</span><span class="sxs-lookup"><span data-stu-id="ce3e3-287">Explore the Adventure Works Multidimensional Model by using Power View</span></span>](https://office.microsoft.com/excel-help/explore-the-adventure-works-multidimensional-model-by-using-power-view-HA104046830.aspx)  
  
