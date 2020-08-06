---
title: 定义多对多关系和多对多关系属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- many-to-many relationships [Analysis Services]
ms.assetid: edb5f61a-a581-467a-a367-134b7f9b849f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1cd5d46ce07ff8eb6a3893c0dac261797c6ef19e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590399"
---
# <a name="define-a-many-to-many-relationship-and-many-to-many-relationship-properties"></a><span data-ttu-id="36968-102">定义多对多关系和多对多关系属性</span><span class="sxs-lookup"><span data-stu-id="36968-102">Define a Many-to-Many Relationship and Many-to-Many Relationship Properties</span></span>
  <span data-ttu-id="36968-103">本主题介绍 Analysis Services 中的多对多维度，包括何时使用它们以及如何创建它们。</span><span class="sxs-lookup"><span data-stu-id="36968-103">This topic explains many-to-many dimensions in Analysis Services, including when to use them and how to create them.</span></span>  
  
## <a name="introduction"></a><span data-ttu-id="36968-104">介绍</span><span class="sxs-lookup"><span data-stu-id="36968-104">Introduction</span></span>  
 <span data-ttu-id="36968-105">Analysis Services 支持多对多维度，并且允许更复杂的分析，从而超越了传统的星型架构所能提供的功能。</span><span class="sxs-lookup"><span data-stu-id="36968-105">Analysis Services supports many-to-many dimensions, allowing for more complex analytics than what can be described in a classic star schema.</span></span> <span data-ttu-id="36968-106">在传统的星型架构中，所有维度都具有针对事实表的一对多关系。</span><span class="sxs-lookup"><span data-stu-id="36968-106">In a classic star schema, all dimensions have a one-to-many relationship with a fact table.</span></span> <span data-ttu-id="36968-107">每个事实都联接到一个维度成员；单个维度成员与多个事实相关联。</span><span class="sxs-lookup"><span data-stu-id="36968-107">Each fact joins to one dimension member; a single dimension member is associated with many facts.</span></span>  
  
 <span data-ttu-id="36968-108">多对多通过实现了将事实（例如帐户余额）与相同维度的多个成员相关联（联接帐户的余额可能会影响联接帐户的两个或多个所有者），消除了这一模型限制。</span><span class="sxs-lookup"><span data-stu-id="36968-108">Many-to-many removes this modeling restriction by enabling a fact (such as an account balance) to be associated with multiple members of the same dimension (the balance of a joint account can be attributed to two or more owners of a joint account).</span></span>  
  
 <span data-ttu-id="36968-109">从概念上讲，Analysis Services 中的多对多维度关系等效于关系模型中的多对多关系，并且支持相同类型的情形。</span><span class="sxs-lookup"><span data-stu-id="36968-109">Conceptually, a many-to-many dimensional relationship in Analysis Services is equivalent to many-to-many relationships in a relational model, supporting the same kinds of scenarios.</span></span> <span data-ttu-id="36968-110">多对多关系的常见示例包括：</span><span class="sxs-lookup"><span data-stu-id="36968-110">Common examples of many-to-many include:</span></span>  
  
-   <span data-ttu-id="36968-111">学生登记了许多课程；每个课程有许多学生。</span><span class="sxs-lookup"><span data-stu-id="36968-111">Students are enrolled in many courses; each course has many students.</span></span>  
  
-   <span data-ttu-id="36968-112">医生有许多患者；患者有许多医生。</span><span class="sxs-lookup"><span data-stu-id="36968-112">Doctors have many patients; patients have many doctors.</span></span>  
  
-   <span data-ttu-id="36968-113">客户有许多银行帐户；银行帐户可能属于多个客户。</span><span class="sxs-lookup"><span data-stu-id="36968-113">Customers have many bank accounts; bank accounts might belong to more than one customer.</span></span>  
  
-   <span data-ttu-id="36968-114">在 Adventure Works 中，许多客户会具有许多原因来订购某一产品，并且某一销售原因可与许多订单相关联。</span><span class="sxs-lookup"><span data-stu-id="36968-114">In Adventure Works, many customers have many reasons for ordering a product, and a sales reason can be associated with many orders.</span></span>  
  
 <span data-ttu-id="36968-115">从分析上，多对多关系解决了这样一个问题，即如何精确地表示相对于维度关系的计数或求和（通常通过在为特定维度成员执行计算时消除重复计数）。</span><span class="sxs-lookup"><span data-stu-id="36968-115">Analytically, the problem that a many-to-many relationship solves is accurate representation of a count or sum relative to the dimensional relationship (usually by eliminating double-counts when performing calculations for a specific dimension member).</span></span> <span data-ttu-id="36968-116">我们必须通过一个例子来澄清这一点。</span><span class="sxs-lookup"><span data-stu-id="36968-116">An example is necessary to clarify this point.</span></span> <span data-ttu-id="36968-117">假定某个产品或服务属于多个类别。</span><span class="sxs-lookup"><span data-stu-id="36968-117">Consider a product or service that belongs to more than one category.</span></span> <span data-ttu-id="36968-118">如果您在按类别对服务数目进行计数，您可能希望属于两个类别的某一服务分别包括在各类别中。</span><span class="sxs-lookup"><span data-stu-id="36968-118">If you were counting the number of services by category, you would want a service belonging to both categories to be included in each one.</span></span> <span data-ttu-id="36968-119">同时，您不想重复计算您提供的服务数目。</span><span class="sxs-lookup"><span data-stu-id="36968-119">At the same time, you would not want to overstate the number of services that you provide.</span></span> <span data-ttu-id="36968-120">通过指定多对多维度关系，在按类别或按服务进行查询时，您获得正确结果的可能性更大了。</span><span class="sxs-lookup"><span data-stu-id="36968-120">By specifying the many-to-many dimensional relationship, you are more likely to get the correct results back when querying by category or by service.</span></span> <span data-ttu-id="36968-121">但是，始终需要进行详尽的测试以便确保多对多维度关系适合于这个情形。</span><span class="sxs-lookup"><span data-stu-id="36968-121">However, thorough testing is always necessary to ensure that this is the case.</span></span>  
  
 <span data-ttu-id="36968-122">从结构上来说，创建多对多维度关系的方式类似于在关系数据模型中创建多对多关系。</span><span class="sxs-lookup"><span data-stu-id="36968-122">Structurally, creating a many-to-many dimensional relationship is similar to how you might create many-to-many in a relational data model.</span></span> <span data-ttu-id="36968-123">但关系模型使用“联接表” \*\* 存储行关联，而多维模型使用“中间度量值组” \*\*。</span><span class="sxs-lookup"><span data-stu-id="36968-123">Whereas a relational model uses a *junction table* to store row associations, a multidimensional model uses an *intermediate measure group*.</span></span> <span data-ttu-id="36968-124">中间度量值组是一个术语，用来表示从不同维度映射成员的一种表。</span><span class="sxs-lookup"><span data-stu-id="36968-124">Intermediate measure group is the term we use to refer to a table that maps members from different dimensions.</span></span>  
  
 <span data-ttu-id="36968-125">多对多维度关系没有在多维数据集关系图中直观地指示。</span><span class="sxs-lookup"><span data-stu-id="36968-125">Visually, a many-to-many dimensional relationship is not indicated in a cube diagram.</span></span> <span data-ttu-id="36968-126">而是使用“维度用法”选项卡快速标识某个模型中的任何多对多关系。</span><span class="sxs-lookup"><span data-stu-id="36968-126">Instead, use the Dimension Usage tab to quickly identify any many-to-many relationships in a model.</span></span> <span data-ttu-id="36968-127">多对多关系用以下图标指示。</span><span class="sxs-lookup"><span data-stu-id="36968-127">A many-to-many relationship is indicated by the following icon.</span></span>  
  
 <span data-ttu-id="36968-128">![维度用法中的多对多图标](../media/ssas-m2m-icondimusage.png "维度用法中的多对多图标")</span><span class="sxs-lookup"><span data-stu-id="36968-128">![Many-to-many icon in dimension usage](../media/ssas-m2m-icondimusage.png "Many-to-many icon in dimension usage")</span></span>  
  
 <span data-ttu-id="36968-129">单击该按钮可打开“定义关系”对话框，以便验证关系类型是多对多，并且可以查看在关系中使用了哪一中间度量值组。</span><span class="sxs-lookup"><span data-stu-id="36968-129">Click the button to open the Define Relationship dialog box to verify the relationship type is many-to-many, and to view which intermediate measure group is used in the relationship.</span></span>  
  
 <span data-ttu-id="36968-130">![维度用法中的 "定义关系" 按钮](../media/ssas-m2m-btndimusage.png "维度用法中的 "定义关系" 按钮")</span><span class="sxs-lookup"><span data-stu-id="36968-130">![Define Relationship button  in dimension usage](../media/ssas-m2m-btndimusage.png "Define Relationship button  in dimension usage")</span></span>  
  
 <span data-ttu-id="36968-131">在后面的部分中，您将学习如何设置多对多维度和测试模型行为。</span><span class="sxs-lookup"><span data-stu-id="36968-131">In subsequent sections, you will learn how to set up a many-to-many dimension and test model behaviors.</span></span> <span data-ttu-id="36968-132">如果要先查看其他信息或试学一下教程，请参阅本文结尾的 **了解详细信息** 。</span><span class="sxs-lookup"><span data-stu-id="36968-132">If you would rather review additional information or try tutorials first, see **Learn More** at the end of this article.</span></span>  
  
## <a name="create-a-many-to-many-dimension"></a><span data-ttu-id="36968-133">创建多对多维度</span><span class="sxs-lookup"><span data-stu-id="36968-133">Create a many-to-many dimension</span></span>  
 <span data-ttu-id="36968-134">一个简单的多对多关系包括具有多对多基数的两个维度、用于存储成员关联的一个中间度量值组以及包含可度量数据（例如总销售额的求和或银行帐户的余额）的事实度量值组。</span><span class="sxs-lookup"><span data-stu-id="36968-134">A simple many-to-many relationship includes two dimensions having a many-to-many cardinality, an intermediate measure group for storing member associations, and a fact measure group containing measurable data, such as sum of total sales or the balance of a bank account.</span></span>  
  
 <span data-ttu-id="36968-135">多对多关系中的维度可能在 DSV 中具有对应表，其中，模型中的每个维度都基于数据源中的现有表。</span><span class="sxs-lookup"><span data-stu-id="36968-135">Dimensions in a many-to-many relationship might have correspondent tables in the DSV, where each dimension in the model is based on an existing table in a data source.</span></span> <span data-ttu-id="36968-136">相反，您的模型中的维度可能派生自 DSV 中更少或不同的物理表。</span><span class="sxs-lookup"><span data-stu-id="36968-136">Conversely, the dimensions in your model might derive from fewer or different physical tables in the DSV.</span></span> <span data-ttu-id="36968-137">现在以销售原因和销售订单为例，Adventure Works 示例多维数据集使用作为仅限模型的数据结构（在 DSV 中没有物理对等项）存在的维度演示一个多对多关系。</span><span class="sxs-lookup"><span data-stu-id="36968-137">Using Sales Reasons and Sales Orders as a case in point, the Adventure Works sample cube demonstrates a many-to-many relationship using dimensions that exist as model-only data structures, without physical counterparts in the DSV.</span></span> <span data-ttu-id="36968-138">在基础数据源中，该销售订单维度基于事实表，而不是基于维度表。</span><span class="sxs-lookup"><span data-stu-id="36968-138">The Sales Order dimension is based on a fact table, rather than a dimension table, in the underlying data source.</span></span>  
  
 <span data-ttu-id="36968-139">下一个过程假定您已经知道哪些实体参与多对多关系。</span><span class="sxs-lookup"><span data-stu-id="36968-139">The next procedure assumes that you already know which entities participate in the many-to-many relationship.</span></span> <span data-ttu-id="36968-140">若要进一步学习，请参阅 **了解详细信息** 。</span><span class="sxs-lookup"><span data-stu-id="36968-140">See **Learn More** for further study.</span></span>  
  
 <span data-ttu-id="36968-141">为了阐明在创建多对多关系中使用的步骤，此过程在 Adventure Works 示例多维数据集中重新创建了其中一个多对多关系。</span><span class="sxs-lookup"><span data-stu-id="36968-141">To illustrate the steps used to create a many-to-many relationship, this procedure re-creates one of the many-to-many relationships in the Adventure Works sample cube.</span></span> <span data-ttu-id="36968-142">如果您具有在某一关系数据库引擎实例上安装的源数据（即，Adventure Works 示例数据仓库），则可以按照以下步骤执行。</span><span class="sxs-lookup"><span data-stu-id="36968-142">If you have the source data (that is, the Adventure Works sample data warehouse) installed on a relational database engine instance, you can follow these steps.</span></span>  
  
#### <a name="step-1-verify-dsv-relationships"></a><span data-ttu-id="36968-143">步骤 1：验证 DSV 关系</span><span class="sxs-lookup"><span data-stu-id="36968-143">Step 1: Verify DSV relationships</span></span>  
  
1.  <span data-ttu-id="36968-144">在 SQL Server Data Tools 中，在一个多维项目中创建指向 Adventure Works DW 2012 关系数据仓库的数据源，该数据源在 SQL Server 数据库引擎实例上承载。</span><span class="sxs-lookup"><span data-stu-id="36968-144">In SQL Server Data Tools, in a multidimensional project, create a data source to the Adventure Works DW 2012 relational data warehouse, hosted on a SQL Server Database Engine instance.</span></span>  
  
2.  <span data-ttu-id="36968-145">使用以下现有表创建数据源视图：</span><span class="sxs-lookup"><span data-stu-id="36968-145">Create a Data Source View using the following existing tables:</span></span>  
  
    -   <span data-ttu-id="36968-146">FactInternetSales</span><span class="sxs-lookup"><span data-stu-id="36968-146">FactInternetSales</span></span>  
  
    -   <span data-ttu-id="36968-147">FactInternetSalesReason</span><span class="sxs-lookup"><span data-stu-id="36968-147">FactInternetSalesReason</span></span>  
  
    -   <span data-ttu-id="36968-148">DimSalesReason</span><span class="sxs-lookup"><span data-stu-id="36968-148">DimSalesReason</span></span>  
  
3.  <span data-ttu-id="36968-149">确认您计划在多对多关系中使用的所有表都在 DSV 中通过主键关系相关。</span><span class="sxs-lookup"><span data-stu-id="36968-149">Verify that all of the tables you plan to use in the many-to-many relationships are related in the DSV through primary key relationships.</span></span> <span data-ttu-id="36968-150">这是针对在后续步骤中创建指向中间度量值组的链接的要求。</span><span class="sxs-lookup"><span data-stu-id="36968-150">This is a requirement for establishing a link to the intermediate measure group in a subsequent step.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="36968-151">如果基础数据源未提供主键和外键关系，您可以在 DSV 中手动创建这些关系。</span><span class="sxs-lookup"><span data-stu-id="36968-151">If the underlying data source does not provide primary and foreign key relationships, you can create the relationships manually in the DSV.</span></span> <span data-ttu-id="36968-152">有关详细信息，请参阅[在数据源视图中定义逻辑关系 (Analysis Services)](define-logical-relationships-in-a-data-source-view-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="36968-152">For more information, see [Define Logical Relationships in a Data Source View &#40;Analysis Services&#41;](define-logical-relationships-in-a-data-source-view-analysis-services.md).</span></span>  
  
     <span data-ttu-id="36968-153">下面的示例确认使用主键链接在该过程中使用的表。</span><span class="sxs-lookup"><span data-stu-id="36968-153">The following example confirms that the tables used in this procedure are linked using primary keys.</span></span>  
  
     <span data-ttu-id="36968-154">![显示相关表的 DSV](../media/ssas-m2m-dsvpkeys.PNG "显示相关表的 DSV")</span><span class="sxs-lookup"><span data-stu-id="36968-154">![DSV showing related tables](../media/ssas-m2m-dsvpkeys.PNG "DSV showing related tables")</span></span>  
  
#### <a name="step-2-create-dimensions-and-measure-groups"></a><span data-ttu-id="36968-155">步骤 2：创建维度和度量值组</span><span class="sxs-lookup"><span data-stu-id="36968-155">Step 2: Create dimensions and measure groups</span></span>  
  
1.  <span data-ttu-id="36968-156">在 SQL Server Data Tools 中，在一个多维项目中右键单击“维度”\*\*\*\* 并选择“新建维度”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="36968-156">In SQL Server Data Tools, in a multidimensional project, right-click **Dimensions** and select **New Dimension**.</span></span>  
  
2.  <span data-ttu-id="36968-157">在现有表 **DimSalesReason**的基础上新建一个维度。</span><span class="sxs-lookup"><span data-stu-id="36968-157">Create a new dimension based on existing table, **DimSalesReason**.</span></span> <span data-ttu-id="36968-158">在指定源时接受所有默认值。</span><span class="sxs-lookup"><span data-stu-id="36968-158">Accept all of the default values when specifying the source.</span></span>  
  
     <span data-ttu-id="36968-159">对于属性，选择“全部”。</span><span class="sxs-lookup"><span data-stu-id="36968-159">For attributes, select all.</span></span>  
  
     <span data-ttu-id="36968-160">![新维度中的属性列表](../media/ssas-m2m-dimsalesreason.PNG "新维度中的属性列表")</span><span class="sxs-lookup"><span data-stu-id="36968-160">![Attributes list in new dimension](../media/ssas-m2m-dimsalesreason.PNG "Attributes list in new dimension")</span></span>  
  
3.  <span data-ttu-id="36968-161">基于现有表 Fact Internet Sales 创建第二个维度。</span><span class="sxs-lookup"><span data-stu-id="36968-161">Create a second dimension based on existing table, Fact Internet Sales.</span></span> <span data-ttu-id="36968-162">尽管这是一个事实表，但它包含销售订单信息。</span><span class="sxs-lookup"><span data-stu-id="36968-162">Although this is a fact table, it contains Sales Order information.</span></span> <span data-ttu-id="36968-163">我们将使用它来生成一个销售订单维度。</span><span class="sxs-lookup"><span data-stu-id="36968-163">We'll use it to build a Sales Order dimension.</span></span>  
  
4.  <span data-ttu-id="36968-164">在“指定源信息”中，您将看到一个警告，指示必须指定“名称”列。</span><span class="sxs-lookup"><span data-stu-id="36968-164">In Specify Source Information, you will see a warning that indicates a Name column must be specified.</span></span> <span data-ttu-id="36968-165">选择 **SalesOrderNumber** 作为名称。</span><span class="sxs-lookup"><span data-stu-id="36968-165">Choose **SalesOrderNumber** as the Name.</span></span>  
  
     <span data-ttu-id="36968-166">![显示名称列的销售订单维度](../media/ssas-m2m-dimsalesordersource.PNG "显示名称列的销售订单维度")</span><span class="sxs-lookup"><span data-stu-id="36968-166">![Sales Order dimension showing the name column](../media/ssas-m2m-dimsalesordersource.PNG "Sales Order dimension showing the name column")</span></span>  
  
5.  <span data-ttu-id="36968-167">在该向导的下一页上，选择属性。</span><span class="sxs-lookup"><span data-stu-id="36968-167">On the next page of the wizard, choose the attributes.</span></span> <span data-ttu-id="36968-168">在此示例中，你可以只选择 **SalesOrderNumber**。</span><span class="sxs-lookup"><span data-stu-id="36968-168">In this example, you can select just **SalesOrderNumber**.</span></span>  
  
     <span data-ttu-id="36968-169">![显示属性列表的销售订单维度](../media/ssas-m2m-dimsalesorderattrib.PNG "显示属性列表的销售订单维度")</span><span class="sxs-lookup"><span data-stu-id="36968-169">![Sales order dimension showing attribute list](../media/ssas-m2m-dimsalesorderattrib.PNG "Sales order dimension showing attribute list")</span></span>  
  
6.  <span data-ttu-id="36968-170">将该维度重命名为 **Dim Sales Orders**，以便保持一致的维度命名约定。</span><span class="sxs-lookup"><span data-stu-id="36968-170">Rename the dimension to **Dim Sales Orders**, so that you have a consistent naming convention for the dimensions.</span></span>  
  
     <span data-ttu-id="36968-171">![显示维度重命名的向导页](../media/ssas-m2m-dimsalesorders.PNG "显示维度重命名的向导页")</span><span class="sxs-lookup"><span data-stu-id="36968-171">![Wizard page showing dimension rename](../media/ssas-m2m-dimsalesorders.PNG "Wizard page showing dimension rename")</span></span>  
  
7.  <span data-ttu-id="36968-172">右键单击“多维数据集”\*\*\*\*，然后选择“新建多维数据集”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="36968-172">Right-click **Cubes** and select **New Cube**.</span></span>  
  
8.  <span data-ttu-id="36968-173">在度量值组表中，选择 **FactInternetSales** 和 **FactInternetSalesReason**。</span><span class="sxs-lookup"><span data-stu-id="36968-173">In measure group tables, choose **FactInternetSales** and **FactInternetSalesReason**.</span></span>  
  
     <span data-ttu-id="36968-174">选择 **FactInternetSales** 是因为它包含要在多维数据集中使用的度量值。</span><span class="sxs-lookup"><span data-stu-id="36968-174">You are choosing **FactInternetSales** because it contains the measures you want to use in the cube.</span></span> <span data-ttu-id="36968-175">选择 **FactInternetSalesReason** 是因为它是中间度量值组，并且提供将销售订单与销售原因相关联的成员关联数据。</span><span class="sxs-lookup"><span data-stu-id="36968-175">You are choosing **FactInternetSalesReason** because it is the intermediate measure group, providing member association data that relates sales orders to sales reasons.</span></span>  
  
9. <span data-ttu-id="36968-176">为每个事实表选择度量值。</span><span class="sxs-lookup"><span data-stu-id="36968-176">Choose measures for each fact table.</span></span>  
  
     <span data-ttu-id="36968-177">若要简化模型，请清除所有度量值，然后只选择列表底部的 **Sales Amount** 和 **Fact Internet Sales Count** 。</span><span class="sxs-lookup"><span data-stu-id="36968-177">To simplify your model, clear all the measures, and then select just **Sales Amount** and **Fact Internet Sales Count** at the bottom of the list.</span></span> <span data-ttu-id="36968-178">由于 **FactInternetSalesReason** 只有一个度量值，因此系统会自动为你选择该度量值。</span><span class="sxs-lookup"><span data-stu-id="36968-178">The **FactInternetSalesReason** only has one measure, so it is selected for you automatically.</span></span>  
  
10. <span data-ttu-id="36968-179">在维度列表中，你应该会看到 **Dim Sales Reason** 和 **Dim Sales Orders**。</span><span class="sxs-lookup"><span data-stu-id="36968-179">In the dimension list, you should see **Dim Sales Reason** and **Dim Sales Orders**.</span></span>  
  
     <span data-ttu-id="36968-180">在“选择新维度”页中，向导会提示你为 **Fact Internet Sales Dimension**新建一个维度。</span><span class="sxs-lookup"><span data-stu-id="36968-180">In the Select New Dimensions page, the wizard prompts you to create a new dimension for **Fact Internet Sales Dimension**.</span></span> <span data-ttu-id="36968-181">您不需要此维度，因此可以从列表中清除它。</span><span class="sxs-lookup"><span data-stu-id="36968-181">You do not need this dimension, so you can clear it from the list.</span></span>  
  
11. <span data-ttu-id="36968-182">命名该多维数据集并且单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="36968-182">Name the cube and click **Finish**.</span></span>  
  
#### <a name="step-3-define-many-to-many-relationship"></a><span data-ttu-id="36968-183">步骤 3：定义多对多关系</span><span class="sxs-lookup"><span data-stu-id="36968-183">Step 3: Define Many-to-Many relationship</span></span>  
  
1.  <span data-ttu-id="36968-184">在多维数据集设计器中，单击 "维度用法" 选项卡。请注意，维度**销售原因**与**事实 Internet 销售**之间已存在多对多的关系。</span><span class="sxs-lookup"><span data-stu-id="36968-184">In cube designer, click Dimension Usage tab. Notice that there is already a many-to-many relationship between **Dim Sales Reason** and **Fact Internet Sales**.</span></span> <span data-ttu-id="36968-185">请记住，以下图标指示多对多关系。</span><span class="sxs-lookup"><span data-stu-id="36968-185">Recall that the following icon indicates a many-to-many relationship.</span></span>  
  
     <span data-ttu-id="36968-186">![维度用法中的多对多图标](../media/ssas-m2m-icondimusage.png "维度用法中的多对多图标")</span><span class="sxs-lookup"><span data-stu-id="36968-186">![Many-to-many icon in dimension usage](../media/ssas-m2m-icondimusage.png "Many-to-many icon in dimension usage")</span></span>  
  
2.  <span data-ttu-id="36968-187">单击 **Dim Sales Reason** 和 **Fact Internet Sales**的交集单元格，然后单击按钮打开“定义关系”对话框。</span><span class="sxs-lookup"><span data-stu-id="36968-187">Click on the intersection cell between **Dim Sales Reason** and **Fact Internet Sales**, and then click the button to open the Define Relationship dialog box.</span></span>  
  
     <span data-ttu-id="36968-188">您可以看到，将使用此对话框指定多对多关系。</span><span class="sxs-lookup"><span data-stu-id="36968-188">You can see that this dialog box is used to specify a many-to-many relationship.</span></span> <span data-ttu-id="36968-189">如果您过去添加了具有常规关系的维度，则应使用该对话框将其更改为多对多关系。</span><span class="sxs-lookup"><span data-stu-id="36968-189">If you were adding dimensions that had a regular relationship instead, you would use this dialog box to change it to many-to-many.</span></span>  
  
     <span data-ttu-id="36968-190">![维度用法中的 "定义关系" 按钮](../media/ssas-m2m-btndimusage.png "维度用法中的 "定义关系" 按钮")</span><span class="sxs-lookup"><span data-stu-id="36968-190">![Define Relationship button  in dimension usage](../media/ssas-m2m-btndimusage.png "Define Relationship button  in dimension usage")</span></span>  
  
3.  <span data-ttu-id="36968-191">将该项目部署到 Analysis Services 多维实例。</span><span class="sxs-lookup"><span data-stu-id="36968-191">Deploy the project to an Analysis Services multidimensional instance.</span></span> <span data-ttu-id="36968-192">在下一步中，您将在 Excel 中浏览该多维数据集以便验证其行为。</span><span class="sxs-lookup"><span data-stu-id="36968-192">In the next step, you will browse the cube in Excel to verify its behaviors.</span></span>  
  
## <a name="testing-many-to-many"></a><span data-ttu-id="36968-193">测试多对多关系</span><span class="sxs-lookup"><span data-stu-id="36968-193">Testing Many-to-Many</span></span>  
 <span data-ttu-id="36968-194">当您在某一多维数据集中定义多对多关系时，必须进行测试以便确保查询返回预期结果。</span><span class="sxs-lookup"><span data-stu-id="36968-194">When you define a many-to-many relationship in a cube, testing is imperative to ensure queries return expected results.</span></span> <span data-ttu-id="36968-195">您应该使用最终用户将使用的客户端应用程序工具对该多维数据集进行测试。</span><span class="sxs-lookup"><span data-stu-id="36968-195">You should test the cube using the client application tool that will be used by end-users.</span></span> <span data-ttu-id="36968-196">在下一过程中，您将使用 Excel 连接到该多维数据集并且验证查询结果。</span><span class="sxs-lookup"><span data-stu-id="36968-196">In this next procedure, you will use Excel to connect to the cube and verify query results.</span></span>  
  
#### <a name="browse-the-cube-in-excel"></a><span data-ttu-id="36968-197">在 Excel 中浏览多维数据集</span><span class="sxs-lookup"><span data-stu-id="36968-197">Browse the cube in Excel</span></span>  
  
1.  <span data-ttu-id="36968-198">部署该项目，然后浏览多维数据集以便确认聚合有效。</span><span class="sxs-lookup"><span data-stu-id="36968-198">Deploy the project and then browse the cube to confirm the aggregations are valid.</span></span>  
  
2.  <span data-ttu-id="36968-199">在 Excel 中， **Data**单击 "  |  **来自 Analysis Services 的其他源**中的数据"  |  **From Analysis Services**。</span><span class="sxs-lookup"><span data-stu-id="36968-199">In Excel, click **Data** | **From Other Sources** | **From Analysis Services**.</span></span> <span data-ttu-id="36968-200">输入服务器的名称，选择数据库和多维数据集。</span><span class="sxs-lookup"><span data-stu-id="36968-200">Enter the name of the server, choose the database and cube.</span></span>  
  
3.  <span data-ttu-id="36968-201">创建一个数据透视表，它使用以下内容：</span><span class="sxs-lookup"><span data-stu-id="36968-201">Create a PivotTable that uses the following:</span></span>  
  
    -   <span data-ttu-id="36968-202">作为值的**Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="36968-202">**Sales Amount** as the Value</span></span>  
  
    -   <span data-ttu-id="36968-203">列上的**Sales Reason Name**</span><span class="sxs-lookup"><span data-stu-id="36968-203">**Sales Reason Name** on Columns</span></span>  
  
    -   <span data-ttu-id="36968-204">行上的 **“销售订单号”**</span><span class="sxs-lookup"><span data-stu-id="36968-204">**Sales Order Number** on Rows</span></span>  
  
4.  <span data-ttu-id="36968-205">分析结果。</span><span class="sxs-lookup"><span data-stu-id="36968-205">Analyze the results.</span></span> <span data-ttu-id="36968-206">因为我们在使用示例数据，所以，最初的印象是所有销售订单都具有完全相同的值。</span><span class="sxs-lookup"><span data-stu-id="36968-206">Because we are using sample data, the initial impression is that all sales orders have identical values.</span></span> <span data-ttu-id="36968-207">但是，如果您向下滚动，则会开始看到数据变化。</span><span class="sxs-lookup"><span data-stu-id="36968-207">However, if you scroll down, you begin to see data variation.</span></span>  
  
     <span data-ttu-id="36968-208">继续向下，你可以找到订单号 **SO5382**的销售额和销售原因。</span><span class="sxs-lookup"><span data-stu-id="36968-208">Part way down, you can find the sales amount and sales reasons for order number **SO5382**.</span></span> <span data-ttu-id="36968-209">此特定订单的销售额总计是 **539.99**，销售原因包括“促销”、“其他”和“价格”。</span><span class="sxs-lookup"><span data-stu-id="36968-209">Grand total of this particular order is **539.99**, and the purchase reasons attributed to this order include Promotion, Other and Price.</span></span>  
  
     <span data-ttu-id="36968-210">![显示多对多聚合的 Excel 工作表](../media/ssas-m2m-excel.png "显示多对多聚合的 Excel 工作表")</span><span class="sxs-lookup"><span data-stu-id="36968-210">![Excel worksheet showing many-to-many aggregations](../media/ssas-m2m-excel.png "Excel worksheet showing many-to-many aggregations")</span></span>  
  
     <span data-ttu-id="36968-211">请注意，系统对此订单的销售额的计算是正确的；整个订单的销售额是 **539.99** 。</span><span class="sxs-lookup"><span data-stu-id="36968-211">Notice that the Sales Amount is correctly calculated for the order; it is **539.99** for the entire order.</span></span> <span data-ttu-id="36968-212">尽管系统会对每个原因都显示 **539.99** ，但不会对这三个原因所显示的值进行求和，因为这样做会导致销售额总计虚高。</span><span class="sxs-lookup"><span data-stu-id="36968-212">Although **539.99** is indicated for each reason, that value is not summed for all three reasons, erroneously inflating our grand total.</span></span>  
  
     <span data-ttu-id="36968-213">为什么将销售额放到第一个位置中的每个销售原因之下呢？</span><span class="sxs-lookup"><span data-stu-id="36968-213">Why put a sales amount under each sales reason in the first place?</span></span> <span data-ttu-id="36968-214">其原因就是，这样做将使得我们能够标识我们可归于每个原因的销售额。</span><span class="sxs-lookup"><span data-stu-id="36968-214">The answer is that it allows us to identify the amount of sales we can attribute to each reason.</span></span>  
  
5.  <span data-ttu-id="36968-215">滚动到工作表的底部。</span><span class="sxs-lookup"><span data-stu-id="36968-215">Scroll to the bottom of the worksheet.</span></span> <span data-ttu-id="36968-216">现在，很容易就可以看出，相对于其他原因以及总计而言，价格是影响客户购买的最重要原因。</span><span class="sxs-lookup"><span data-stu-id="36968-216">It is now easy to see that Price is the most important reason for customer purchases, relative to other reasons as well as the grand total.</span></span>  
  
     <span data-ttu-id="36968-217">![在多对多中显示总计的 Excel 工作簿](../media/ssas-m2m-excelgrandtotal.png "在多对多中显示总计的 Excel 工作簿")</span><span class="sxs-lookup"><span data-stu-id="36968-217">![Excel workbook showing totals in many-to-many](../media/ssas-m2m-excelgrandtotal.png "Excel workbook showing totals in many-to-many")</span></span>  
  
#### <a name="tips-for-handling-unexpected-query-results"></a><span data-ttu-id="36968-218">用于处理意外查询结果的技巧</span><span class="sxs-lookup"><span data-stu-id="36968-218">Tips for handling unexpected query results</span></span>  
  
1.  <span data-ttu-id="36968-219">隐藏在查询中未返回有意义结果的中间度量值组的度量值，例如计数。</span><span class="sxs-lookup"><span data-stu-id="36968-219">Hide measures in the intermediate measure group, such as the count, that do not return meaningful results in a query.</span></span> <span data-ttu-id="36968-220">这样做可防止一些人尝试使用聚合生成无意义的数据。</span><span class="sxs-lookup"><span data-stu-id="36968-220">This prevents people from trying to use aggregations producing meaningless data.</span></span> <span data-ttu-id="36968-221">若要隐藏某一度量值，请在维度设计器中将属性的 **“可见性”** 设置为 **False** 。</span><span class="sxs-lookup"><span data-stu-id="36968-221">To hide a measure, set **Visibility** to **False** on the attribute in dimension designer.</span></span>  
  
2.  <span data-ttu-id="36968-222">创建视角以便使用支持您要提供的分析体验的度量值和维度的子集。</span><span class="sxs-lookup"><span data-stu-id="36968-222">Create perspectives to use a subset of measures and dimensions that support the analytical experience you want to provide.</span></span> <span data-ttu-id="36968-223">包含许多度量值组和维度的多维数据集可能不是在所有情况下都可以很好地一起工作。</span><span class="sxs-lookup"><span data-stu-id="36968-223">Possibly, a cube that contains many measure groups and dimensions do not work well together in all cases.</span></span> <span data-ttu-id="36968-224">通过隔离您要一起使用的维度和度量值组，可确保您获得更具可预测性的结果。</span><span class="sxs-lookup"><span data-stu-id="36968-224">By isolating the dimensions and measure groups that you intend to be used together, you ensure a more predictable outcome.</span></span>  
  
3.  <span data-ttu-id="36968-225">务必要在更改模型后进行部署和重新连接。</span><span class="sxs-lookup"><span data-stu-id="36968-225">Always remember to deploy and reconnect after changing a model.</span></span> <span data-ttu-id="36968-226">在 Excel 中，使用“数据透视表分析”功能区上的“刷新”按钮。</span><span class="sxs-lookup"><span data-stu-id="36968-226">In Excel, use the Refresh button on the PivotTable Analyze ribbon.</span></span>  
  
4.  <span data-ttu-id="36968-227">避免在多个多对多关系中使用链接度量值组（尤其是在这些关系处于不同多维数据集中时）。</span><span class="sxs-lookup"><span data-stu-id="36968-227">Avoid using linked measure groups in multiple many-to-many relationships, especially when those relationships are in different cubes.</span></span> <span data-ttu-id="36968-228">这样做可能导致不明确的聚合。</span><span class="sxs-lookup"><span data-stu-id="36968-228">Doing so can result in ambiguous aggregations.</span></span> <span data-ttu-id="36968-229">有关详细信息，请参阅 [Incorrect Amounts for Linked Measures in Cubes containing Many-to-Many Relationships](https://social.technet.microsoft.com/wiki/contents/articles/22911.incorrect-amounts-for-linked-measures-in-cubes-containing-many-to-many-relationships-ssas-troubleshooting.aspx)（包含多对多关系的多维数据集中链接度量值的不正确数量）。</span><span class="sxs-lookup"><span data-stu-id="36968-229">For more information, see [Incorrect Amounts for Linked Measures in Cubes containing Many-to-Many Relationships](https://social.technet.microsoft.com/wiki/contents/articles/22911.incorrect-amounts-for-linked-measures-in-cubes-containing-many-to-many-relationships-ssas-troubleshooting.aspx).</span></span>  
  
##  <a name="learn-more"></a><a name="bkmk_Learn"></a><span data-ttu-id="36968-230">了解更多信息</span><span class="sxs-lookup"><span data-stu-id="36968-230">Learn more</span></span>  
 <span data-ttu-id="36968-231">使用以下链接可获取帮助您掌握这些概念的其他信息。</span><span class="sxs-lookup"><span data-stu-id="36968-231">Use the following links to get additional information that helps you master the concepts.</span></span>  
  
 [<span data-ttu-id="36968-232">如何在 Analysis Services 中定义多对多维度</span><span class="sxs-lookup"><span data-stu-id="36968-232">How do I define a many-to-many dimension in Analysis Services</span></span>](../lesson-5-3-defining-a-many-to-many-relationship.md)  
  
 [<span data-ttu-id="36968-233">多对多变革 2.0</span><span class="sxs-lookup"><span data-stu-id="36968-233">The many-to-many Revolution 2.0</span></span>](https://go.microsoft.com/fwlink/?LinkId=324760)  
  
 [<span data-ttu-id="36968-234">教程：针对 SQL Server Analysis Services 的多对多维度示例</span><span class="sxs-lookup"><span data-stu-id="36968-234">Tutorial: Many-to-many dimension example for SQL Server Analysis Services</span></span>](https://go.microsoft.com/fwlink/?LinkId=324761)  
  
## <a name="see-also"></a><span data-ttu-id="36968-235">另请参阅</span><span class="sxs-lookup"><span data-stu-id="36968-235">See Also</span></span>  
 <span data-ttu-id="36968-236">[维度关系](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span><span class="sxs-lookup"><span data-stu-id="36968-236">[Dimension Relationships](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span></span>  
 <span data-ttu-id="36968-237">[安装 Analysis Services 多维建模教程的示例数据和项目](../install-sample-data-and-projects.md) </span><span class="sxs-lookup"><span data-stu-id="36968-237">[Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](../install-sample-data-and-projects.md) </span></span>  
 <span data-ttu-id="36968-238">[&#40;SSDT 部署 Analysis Services 项目&#41;](deploy-analysis-services-projects-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="36968-238">[Deploy Analysis Services Projects &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md) </span></span>  
 [<span data-ttu-id="36968-239">多维模型中的透视</span><span class="sxs-lookup"><span data-stu-id="36968-239">Perspectives in Multidimensional Models</span></span>](perspectives-in-multidimensional-models.md)  
  
  
