---
title: 通过在数据源中生成非时间表来创建维度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data sources [Analysis Services], dimensions without data source
- dimensions [Analysis Services], standard
- dimensions [Analysis Services], creating without data source
- standard dimensions [Analysis Services]
ms.assetid: a37f7a46-7451-4582-ba19-2595196d97bc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 49dbfb0c1fc15c1cbf703514e0fc693dfabf1e9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691966"
---
# <a name="create-a-dimension-by-generating-a-non-time-table-in-the-data-source"></a><span data-ttu-id="825be-102">通过在数据源中生成非时间表来创建维度</span><span class="sxs-lookup"><span data-stu-id="825be-102">Create a Dimension by Generating a Non-Time Table in the Data Source</span></span>
  <span data-ttu-id="825be-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，您可以使用中的维度向导在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 不使用现有数据源的情况下创建维度。</span><span class="sxs-lookup"><span data-stu-id="825be-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use the Dimension Wizard in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to create a dimension without using an existing data source.</span></span> <span data-ttu-id="825be-104">在维度向导的“选择创建方法”页上选择“在数据源中生成非时间表”选项可执行此操作\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="825be-104">You do this by selecting the **Generate a non-time table in the data source** option of the **Select Creation Method** page of the wizard.</span></span> <span data-ttu-id="825be-105">若要在基础数据源中创建新维度，必须具有在基础数据源中创建对象的权限。</span><span class="sxs-lookup"><span data-stu-id="825be-105">To create a new dimension table in the underlying data source, you must have permission to create objects in the underlying data source.</span></span> <span data-ttu-id="825be-106">在不使用预定义数据源视图的情况下定义维度时，可以从头开始定义维度，也可以使用维度模板来定义维度。</span><span class="sxs-lookup"><span data-stu-id="825be-106">When defining a dimension without a predefined data source view, you can either define the dimension from scratch or use a dimension template.</span></span>  
  
 <span data-ttu-id="825be-107">维度向导提供了示例维度模板，您可以使用这些模板生成常用的维度类型。</span><span class="sxs-lookup"><span data-stu-id="825be-107">The Dimension Wizard provides sample dimension templates from which you can build a common dimension type.</span></span> <span data-ttu-id="825be-108">可以从下列维度类型中选择：</span><span class="sxs-lookup"><span data-stu-id="825be-108">You can select from the following types of dimensions:</span></span>  
  
-   <span data-ttu-id="825be-109">帐户</span><span class="sxs-lookup"><span data-stu-id="825be-109">Account</span></span>  
  
-   <span data-ttu-id="825be-110">客户</span><span class="sxs-lookup"><span data-stu-id="825be-110">Customer</span></span>  
  
-   <span data-ttu-id="825be-111">Date</span><span class="sxs-lookup"><span data-stu-id="825be-111">Date</span></span>  
  
-   <span data-ttu-id="825be-112">部门</span><span class="sxs-lookup"><span data-stu-id="825be-112">Department</span></span>  
  
-   <span data-ttu-id="825be-113">目标货币</span><span class="sxs-lookup"><span data-stu-id="825be-113">Destination Currency</span></span>  
  
-   <span data-ttu-id="825be-114">员工</span><span class="sxs-lookup"><span data-stu-id="825be-114">Employee</span></span>  
  
-   <span data-ttu-id="825be-115">地理位置</span><span class="sxs-lookup"><span data-stu-id="825be-115">Geography</span></span>  
  
-   <span data-ttu-id="825be-116">Internet 销售订单详细信息</span><span class="sxs-lookup"><span data-stu-id="825be-116">Internet Sales Order Details</span></span>  
  
-   <span data-ttu-id="825be-117">组织</span><span class="sxs-lookup"><span data-stu-id="825be-117">Organization</span></span>  
  
-   <span data-ttu-id="825be-118">产品</span><span class="sxs-lookup"><span data-stu-id="825be-118">Product</span></span>  
  
-   <span data-ttu-id="825be-119">Promotion</span><span class="sxs-lookup"><span data-stu-id="825be-119">Promotion</span></span>  
  
-   <span data-ttu-id="825be-120">分销商销售订单详细信息</span><span class="sxs-lookup"><span data-stu-id="825be-120">Reseller Sales Order Details</span></span>  
  
-   <span data-ttu-id="825be-121">Reseller</span><span class="sxs-lookup"><span data-stu-id="825be-121">Reseller</span></span>  
  
-   <span data-ttu-id="825be-122">销售渠道</span><span class="sxs-lookup"><span data-stu-id="825be-122">Sales Channel</span></span>  
  
-   <span data-ttu-id="825be-123">销售原因</span><span class="sxs-lookup"><span data-stu-id="825be-123">Sales Reason</span></span>  
  
-   <span data-ttu-id="825be-124">销售汇总订单详细信息</span><span class="sxs-lookup"><span data-stu-id="825be-124">Sales Summary Order Details</span></span>  
  
-   <span data-ttu-id="825be-125">销售区域</span><span class="sxs-lookup"><span data-stu-id="825be-125">Sales Territory</span></span>  
  
-   <span data-ttu-id="825be-126">方案</span><span class="sxs-lookup"><span data-stu-id="825be-126">Scenario</span></span>  
  
-   <span data-ttu-id="825be-127">源货币</span><span class="sxs-lookup"><span data-stu-id="825be-127">Source Currency</span></span>  
  
 <span data-ttu-id="825be-128">每个标准模板都支持可选择包括在维度中的属性。</span><span class="sxs-lookup"><span data-stu-id="825be-128">Each of the standard templates supports attributes that you can choose to include in the dimension.</span></span> <span data-ttu-id="825be-129">还可以为经常与数据一起使用的维度添加自己的模板文件。</span><span class="sxs-lookup"><span data-stu-id="825be-129">You can also add your own template files for dimensions that are commonly used with your data.</span></span> <span data-ttu-id="825be-130">维度模板位于以下文件夹中：</span><span class="sxs-lookup"><span data-stu-id="825be-130">The dimension templates are located in the following folder:</span></span>  
  
 `C:\Program Files\Microsoft SQL Server\100\Tools\Templates\olap\1033\Dimension Templates`  
  
 <span data-ttu-id="825be-131">完成维度向导后，可以使用维度设计器来添加、删除和配置维度中的属性和层次结构。</span><span class="sxs-lookup"><span data-stu-id="825be-131">You can use Dimension Designer after you complete the Dimension Wizard to add, remove, and configure attributes and hierarchies in the dimension.</span></span>  
  
 <span data-ttu-id="825be-132">不使用数据源创建非时间维度时，维度向导将引导您完成指定维度类型、标识键属性和渐变维度的步骤。</span><span class="sxs-lookup"><span data-stu-id="825be-132">When you are creating a non-time dimension without using a data source, the Dimension Wizard guides you through the steps of specifying the dimension type, and identifying the key attribute and slowly changing dimensions.</span></span>  
  
## <a name="specify-dimension-type"></a><span data-ttu-id="825be-133">指定维度类型</span><span class="sxs-lookup"><span data-stu-id="825be-133">Specify Dimension Type</span></span>  
 <span data-ttu-id="825be-134">在维度向导的 **“指定维度类型”** 页上，可以指定维度类型。</span><span class="sxs-lookup"><span data-stu-id="825be-134">On the **Specify Dimension Type** page of the Dimension Wizard, you can specify the dimension type.</span></span> <span data-ttu-id="825be-135">如果基于模板生成维度，则维度类型已定义。</span><span class="sxs-lookup"><span data-stu-id="825be-135">If you are building the dimension based on a template, the dimension type is defined for you.</span></span> <span data-ttu-id="825be-136">在此页上，还可以为指定的维度类型选择标准属性（如果有的话）。</span><span class="sxs-lookup"><span data-stu-id="825be-136">On this page, you can also select standard attributes for the specified dimension type if any are available.</span></span>  
  
 <span data-ttu-id="825be-137">如果选择对应于维度类型的模板，则以该维度类型的选项填充此页。</span><span class="sxs-lookup"><span data-stu-id="825be-137">If you selected a template that corresponds to a dimension type, this page is populated with the options for that dimension type.</span></span> <span data-ttu-id="825be-138">如果不选择模板，或没有相应的维度类型，则默认维度类型是 **“常规”**。</span><span class="sxs-lookup"><span data-stu-id="825be-138">If you did not select a template, or if there is no corresponding dimension type, the default dimension type is **Regular**.</span></span> <span data-ttu-id="825be-139">如果尚未选择维度类型，请为要创建的维度选择最合适的类型。</span><span class="sxs-lookup"><span data-stu-id="825be-139">If a dimension type is not already selected, select the most appropriate type for the dimension that you are creating.</span></span> <span data-ttu-id="825be-140">如果没有为 **“维度类型”** 列出合适的类型，请使用 **“常规”**。</span><span class="sxs-lookup"><span data-stu-id="825be-140">If no appropriate type is listed for **Dimension type**, use **Regular**.</span></span>  
  
 <span data-ttu-id="825be-141">选择维度类型时，向导将在 **“维度属性”** 下列出适用于此维度的属性类型。</span><span class="sxs-lookup"><span data-stu-id="825be-141">When you select a dimension type, the wizard lists the attribute types that apply to this dimension under **Dimension attributes**.</span></span> <span data-ttu-id="825be-142">若要选择属性类型，请选中属性类型旁边的 **“包含”** 复选框，并在 **“维度属性”** 下面键入属性的名称。</span><span class="sxs-lookup"><span data-stu-id="825be-142">To select an attribute type, select the **Include** check box next to the attribute type, and type the name for the attribute under **Dimension Attribute**.</span></span> <span data-ttu-id="825be-143">默认名称与 **“属性类型”** 相同。</span><span class="sxs-lookup"><span data-stu-id="825be-143">The default name is the same as **Attribute Type**.</span></span>  
  
## <a name="identify-key-attribute-and-changing-dimensions"></a><span data-ttu-id="825be-144">标识键属性和变化的维度</span><span class="sxs-lookup"><span data-stu-id="825be-144">Identify Key Attribute and Changing Dimensions</span></span>  
 <span data-ttu-id="825be-145">在 **“指定维度键和类型”** 页上，选择要作为维度键属性的属性。</span><span class="sxs-lookup"><span data-stu-id="825be-145">On the **Specify Dimension Key and Type** page, select the attribute that you want to be the key attribute for the dimension.</span></span> <span data-ttu-id="825be-146">键属性通常对应于主维度表中的主键列，它通常要为维度的叶成员建立索引。</span><span class="sxs-lookup"><span data-stu-id="825be-146">The key attribute typically corresponds to the primary key column in the main dimension table, and it typically indexes the leaf members of the dimension.</span></span>  
  
 <span data-ttu-id="825be-147">如果选择了模板，并且在模板中定义了键属性，则该属性将成为默认键属性。</span><span class="sxs-lookup"><span data-stu-id="825be-147">If you selected a template, and a key attribute is defined in the template, that attribute is the default key attribute.</span></span> <span data-ttu-id="825be-148">如果选择了模板，但没有在该模板中定义键属性，则默认属性是列表中的第一个属性。</span><span class="sxs-lookup"><span data-stu-id="825be-148">If you selected a template but no key attribute is defined in the template, the default is the first attribute in the list.</span></span> <span data-ttu-id="825be-149">该列表包含在 **“指定维度类型”** 页中选择的所有属性。</span><span class="sxs-lookup"><span data-stu-id="825be-149">The list contains all the attributes that you selected on the **Specify Dimension Type** page.</span></span> <span data-ttu-id="825be-150">可以选择在 **“指定维度类型”** 页中选择的任何一个属性作为键属性。</span><span class="sxs-lookup"><span data-stu-id="825be-150">You can select any one of the attributes that you selected on the **Specify Dimension Type** page to be the key attribute.</span></span> <span data-ttu-id="825be-151">如果不选择任何属性，向导将自动创建键属性，并以串联的维度名称和“ID”进行命名。</span><span class="sxs-lookup"><span data-stu-id="825be-151">If you did not select any attributes, the wizard automatically creates a key attribute and names it by concatenating the dimension name and "ID".</span></span>  
  
 <span data-ttu-id="825be-152">最后，请指定此维度是否是变化的维度。</span><span class="sxs-lookup"><span data-stu-id="825be-152">Finally, specify whether this dimension is a changing dimension.</span></span> <span data-ttu-id="825be-153">在变化的维度中，成员将会随时间的变化移至层次结构中的不同位置。</span><span class="sxs-lookup"><span data-stu-id="825be-153">Members in a changing dimension move over time to different locations in the hierarchy.</span></span> <span data-ttu-id="825be-154">向导将生成其他列，并创建与这些列相对应的属性。</span><span class="sxs-lookup"><span data-stu-id="825be-154">The wizard generates additional columns and creates attributes that correspond to those columns.</span></span> <span data-ttu-id="825be-155">这些列将允许用户以变化中的因素的方式查询维度。</span><span class="sxs-lookup"><span data-stu-id="825be-155">These columns will let users query the dimension in such a way as to factor in the change.</span></span> <span data-ttu-id="825be-156">随后用架构生成向导所创建的任何包将基于维度的渐变维度特征来管理代理键。</span><span class="sxs-lookup"><span data-stu-id="825be-156">Any packages that you subsequently create with the Schema Generation Wizard manage surrogate keys based on slowly changing dimension characteristics of the dimension.</span></span>  
  
 <span data-ttu-id="825be-157">选中 **“这是变化的维度”** 复选框时，维度向导将定义下表中列出的属性：</span><span class="sxs-lookup"><span data-stu-id="825be-157">When you select the **This is a changing dimension** check box, the Dimension Wizard defines the attributes indicated in the following table:</span></span>  
  
|<span data-ttu-id="825be-158">Attribute</span><span class="sxs-lookup"><span data-stu-id="825be-158">Attribute</span></span>|<span data-ttu-id="825be-159">类型</span><span class="sxs-lookup"><span data-stu-id="825be-159">Type</span></span>|  
|---------------|----------|  
|<span data-ttu-id="825be-160">SCD OriginalID</span><span class="sxs-lookup"><span data-stu-id="825be-160">SCD OriginalID</span></span>|<span data-ttu-id="825be-161">SCDOriginalID</span><span class="sxs-lookup"><span data-stu-id="825be-161">SCDOriginalID</span></span>|  
|<span data-ttu-id="825be-162">SCD End Date</span><span class="sxs-lookup"><span data-stu-id="825be-162">SCD End Date</span></span>|<span data-ttu-id="825be-163">SCDEndDate</span><span class="sxs-lookup"><span data-stu-id="825be-163">SCDEndDate</span></span>|  
|<span data-ttu-id="825be-164">SCD Start Date</span><span class="sxs-lookup"><span data-stu-id="825be-164">SCD Start Date</span></span>|<span data-ttu-id="825be-165">SCDStartDate</span><span class="sxs-lookup"><span data-stu-id="825be-165">SCDStartDate</span></span>|  
|<span data-ttu-id="825be-166">SCD 状态</span><span class="sxs-lookup"><span data-stu-id="825be-166">SCD Status</span></span>|<span data-ttu-id="825be-167">SCDStatus</span><span class="sxs-lookup"><span data-stu-id="825be-167">SCDStatus</span></span>|  
  
 <span data-ttu-id="825be-168">如果使用已定义这些渐变维度属性的模板，则默认情况下已选中 **“这是变化的维度”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="825be-168">By default, the **This is a changing dimension** check box is selected if you use a template that has these slowly changing dimension attributes defined.</span></span> <span data-ttu-id="825be-169">如果清除了该复选框，将从维度中删除渐变维度属性。</span><span class="sxs-lookup"><span data-stu-id="825be-169">If you clear the check box, the slowly changing dimension attributes are removed from the dimension.</span></span>  
  
 <span data-ttu-id="825be-170">可以使用维度设计器配置渐变维度的属性。</span><span class="sxs-lookup"><span data-stu-id="825be-170">You can use Dimension Designer to configure properties for a slowly changing dimension.</span></span>  
  
## <a name="completing-the-dimension-wizard"></a><span data-ttu-id="825be-171">完成维度向导</span><span class="sxs-lookup"><span data-stu-id="825be-171">Completing the Dimension Wizard</span></span>  
 <span data-ttu-id="825be-172">在 **“完成向导”** 页中，键入新维度的名称并查看维度结构。</span><span class="sxs-lookup"><span data-stu-id="825be-172">On the **Completing the Wizard** page, type a name for the new dimension and view the dimension structure.</span></span> <span data-ttu-id="825be-173">选中 **“立即生成架构”** 复选框，以在单击 **“完成”** 之后启动架构生成向导。</span><span class="sxs-lookup"><span data-stu-id="825be-173">Select the **Generate schema now** check box to start the Schema Generation Wizard after you click **Finish**.</span></span> <span data-ttu-id="825be-174">在大多数情况下，如果计划创建其他对象，则不应选中该复选框。</span><span class="sxs-lookup"><span data-stu-id="825be-174">In most cases, you should not select this check box if you plan to create additional objects.</span></span> <span data-ttu-id="825be-175">如果不选中此复选框，则可以随后使用维度设计器生成架构。</span><span class="sxs-lookup"><span data-stu-id="825be-175">If you do not select this check box, you can use Dimension Designer to generate the schema later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="825be-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="825be-176">See Also</span></span>  
 <span data-ttu-id="825be-177">[通过生成时间表来创建时间维度](create-a-time-dimension-by-generating-a-time-table.md) </span><span class="sxs-lookup"><span data-stu-id="825be-177">[Create a Time Dimension by Generating a Time Table](create-a-time-dimension-by-generating-a-time-table.md) </span></span>  
 [<span data-ttu-id="825be-178">通过生成时间表来创建时间维度</span><span class="sxs-lookup"><span data-stu-id="825be-178">Create a Time Dimension by Generating a Time Table</span></span>](create-a-time-dimension-by-generating-a-time-table.md)  
  
  
