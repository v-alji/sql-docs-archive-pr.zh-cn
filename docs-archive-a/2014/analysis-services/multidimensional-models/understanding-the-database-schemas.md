---
title: 了解数据库架构 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Schema Generation Wizard, database schema
- database schema [Analysis Services]
- relational schema [Analysis Services], database schema
- subject area schema options [Analysis Services]
- staging area schema options [Analysis Services]
- denormalized schemas
ms.assetid: 51e411f9-ee3f-4b92-9833-c2bce8c6b752
author: minewiskan
ms.author: owend
ms.openlocfilehash: 84f44db1b7abca1b8cad45cf5f46fcc0006bd92a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689620"
---
# <a name="understanding-the-database-schemas"></a><span data-ttu-id="d27db-102">了解数据库架构</span><span class="sxs-lookup"><span data-stu-id="d27db-102">Understanding the Database Schemas</span></span>
  <span data-ttu-id="d27db-103">架构生成向导为基于 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中的维度和度量值组的主题区域数据库生成一个非规范化的关系架构。</span><span class="sxs-lookup"><span data-stu-id="d27db-103">The Schema Generation Wizard generates a denormalized relational schema for the subject area database based on the dimensions and measure groups in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="d27db-104">该向导为每个维度生成一个用于存储维度数据的关系表（该表称为维度表）；为每个度量值组生成一个用于存储事实数据的关系表（该表称为事实数据表）。</span><span class="sxs-lookup"><span data-stu-id="d27db-104">The wizard generates a relational table for each dimension to store dimension data, which is called a dimension table, and a relational table for each measure group to store fact data, which is called a fact table.</span></span> <span data-ttu-id="d27db-105">该向导在生成这些关系表时，会忽略链接维度、链接度量值组以及服务器时间维度。</span><span class="sxs-lookup"><span data-stu-id="d27db-105">The wizard ignores linked dimensions, linked measure groups, and server time dimensions when it generates these relational tables.</span></span>  
  
## <a name="validation"></a><span data-ttu-id="d27db-106">验证</span><span class="sxs-lookup"><span data-stu-id="d27db-106">Validation</span></span>  
 <span data-ttu-id="d27db-107">在架构生成向导开始生成基础关系架构之前，它会验证 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 多维数据集和维度。</span><span class="sxs-lookup"><span data-stu-id="d27db-107">Before it begins to generate the underlying relational schema, the Schema Generation Wizard validates the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cubes and dimensions.</span></span> <span data-ttu-id="d27db-108">如果该向导检测到错误，它便会停止并将错误报告到 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的“任务列表”窗口。</span><span class="sxs-lookup"><span data-stu-id="d27db-108">If the wizard detects errors, it stops and reports the errors to the Task List window in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="d27db-109">阻止生成的错误示例包括：</span><span class="sxs-lookup"><span data-stu-id="d27db-109">Examples of errors that prevent generation include the following:</span></span>  
  
-   <span data-ttu-id="d27db-110">具有多个键属性的维度。</span><span class="sxs-lookup"><span data-stu-id="d27db-110">Dimensions that have more than one key attribute.</span></span>  
  
-   <span data-ttu-id="d27db-111">具有键属性以外其他数据类型的父属性。</span><span class="sxs-lookup"><span data-stu-id="d27db-111">Parent attributes that have different data types than the key attributes.</span></span>  
  
-   <span data-ttu-id="d27db-112">没有度量值的度量值组。</span><span class="sxs-lookup"><span data-stu-id="d27db-112">Measure groups that do not have measures.</span></span>  
  
-   <span data-ttu-id="d27db-113">未正确配置的退化维度或度量值。</span><span class="sxs-lookup"><span data-stu-id="d27db-113">Degenerate dimensions or measures that are improperly configured.</span></span>  
  
-   <span data-ttu-id="d27db-114">未正确配置的代理键，如使用 `ScdOriginalID` 属性类型的多个属性，或使用未用整数数据类型绑定到列的 `ScdOriginalID` 的属性。</span><span class="sxs-lookup"><span data-stu-id="d27db-114">Surrogate keys that are improperly configured, such as multiple attributes using the `ScdOriginalID` attribute type or an attribute using the `ScdOriginalID` that is not bound to a column using the integer data type.</span></span>  
  
## <a name="dimension-tables"></a><span data-ttu-id="d27db-115">维度表</span><span class="sxs-lookup"><span data-stu-id="d27db-115">Dimension Tables</span></span>  
 <span data-ttu-id="d27db-116">对于每个维度，架构生成向导都会生成一个要包含在主题区域数据库中的维度表。</span><span class="sxs-lookup"><span data-stu-id="d27db-116">For each dimension, the Schema Generation Wizard generates a dimension table to be included in the subject area database.</span></span> <span data-ttu-id="d27db-117">维度表的结构取决于在设计它所基于的维度时所做的选择。</span><span class="sxs-lookup"><span data-stu-id="d27db-117">The structure of the dimension table depends on the choices made while designing the dimension on which it is based.</span></span>  
  
 <span data-ttu-id="d27db-118">列</span><span class="sxs-lookup"><span data-stu-id="d27db-118">Columns</span></span>  
 <span data-ttu-id="d27db-119">向导将为与维度表所基于的维度中的每个特性关联的绑定（例如，每个特性的 `KeyColumns`、`NameColumn`、`ValueColumn`、`CustomRollupColumn`、`CustomRollupPropertiesColumn` 和 `UnaryOperatorColumn` 等属性的绑定）生成一列。</span><span class="sxs-lookup"><span data-stu-id="d27db-119">The wizard generates one column for the bindings associated to each attribute in the dimension on which the dimension table is based, such as the bindings for the `KeyColumns`, `NameColumn`, `ValueColumn`, `CustomRollupColumn`, `CustomRollupPropertiesColumn`, and `UnaryOperatorColumn` properties of each attribute.</span></span>  
  
 <span data-ttu-id="d27db-120">关系</span><span class="sxs-lookup"><span data-stu-id="d27db-120">Relationships</span></span>  
 <span data-ttu-id="d27db-121">向导将生成每个父属性的列与维度表的主键之间的关系。</span><span class="sxs-lookup"><span data-stu-id="d27db-121">The wizard generates a relationship between the column for each parent attribute and the primary key of the dimension table.</span></span>  
  
 <span data-ttu-id="d27db-122">如果适用，向导还会生成在多维数据集中被定义为被引用维度的每个附加维度表中主键的关系。</span><span class="sxs-lookup"><span data-stu-id="d27db-122">The wizard also generates a relationship to the primary key in each additional dimension table defined as a referenced dimension in the cube, if applicable.</span></span>  
  
 <span data-ttu-id="d27db-123">约束</span><span class="sxs-lookup"><span data-stu-id="d27db-123">Constraints</span></span>  
 <span data-ttu-id="d27db-124">默认情况下，向导会为基于维度键属性的每个维度表生成一个主键约束。</span><span class="sxs-lookup"><span data-stu-id="d27db-124">The wizard generates a primary key constraint, by default, for each dimension table based on the key attribute of the dimension.</span></span> <span data-ttu-id="d27db-125">如果生成了主键约束，则会在默认情况下生成一个单独的名称列。</span><span class="sxs-lookup"><span data-stu-id="d27db-125">If the primary key constraint is generated, a separate name column is generated by default.</span></span> <span data-ttu-id="d27db-126">逻辑主键在数据源视图中创建，即使您决定不在数据库中创建主键也是如此。</span><span class="sxs-lookup"><span data-stu-id="d27db-126">A logical primary key is created in the data source view even if you decide not to create the primary key in the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d27db-127">如果在维度表所基于的维度中指定了多个键属性，则会出现错误。</span><span class="sxs-lookup"><span data-stu-id="d27db-127">An error occurs if more than one key attribute is specified in the dimension on which the dimension table is based.</span></span>  
  
 <span data-ttu-id="d27db-128">翻译</span><span class="sxs-lookup"><span data-stu-id="d27db-128">Translations</span></span>  
 <span data-ttu-id="d27db-129">向导会生成一个单独的表以保存需要翻译列的任意属性的翻译值。</span><span class="sxs-lookup"><span data-stu-id="d27db-129">The wizard generates a separate table to hold the translated values for any attribute that requires a translation column.</span></span> <span data-ttu-id="d27db-130">向导还会为每种所需的语言创建一个单独的列。</span><span class="sxs-lookup"><span data-stu-id="d27db-130">The wizard also creates a separate column for each of the required languages.</span></span>  
  
## <a name="fact-tables"></a><span data-ttu-id="d27db-131">事实数据表</span><span class="sxs-lookup"><span data-stu-id="d27db-131">Fact Tables</span></span>  
 <span data-ttu-id="d27db-132">对于多维数据集中的每个度量值组，架构生成向导都会生成一个要包含在主题区域数据库中的事实数据表。</span><span class="sxs-lookup"><span data-stu-id="d27db-132">For each measure group in a cube, the Schema Generation Wizard generates a fact table to be included in the subject area database.</span></span> <span data-ttu-id="d27db-133">事实数据表的结构取决于在设计它所基于的度量值组时所做的选择，以及在度量值组和任何包含的维度之间建立的关系。</span><span class="sxs-lookup"><span data-stu-id="d27db-133">The structure of the fact table depends on the choices made while designing the measure group on which it is based, and the relationships established between the measure group and any included dimensions.</span></span>  
  
 <span data-ttu-id="d27db-134">列</span><span class="sxs-lookup"><span data-stu-id="d27db-134">Columns</span></span>  
 <span data-ttu-id="d27db-135">除了使用 `Count` 聚合函数的度量值以外，向导为每个度量值生成一列。</span><span class="sxs-lookup"><span data-stu-id="d27db-135">The wizard generates one column for each measure, except for measures that use the `Count` aggregation function.</span></span> <span data-ttu-id="d27db-136">此类度量值在事实数据表中不需要对应的列。</span><span class="sxs-lookup"><span data-stu-id="d27db-136">Such measures do not require a corresponding column in the fact table.</span></span>  
  
 <span data-ttu-id="d27db-137">如果适用，向导还会为度量值组中每个常规维度关系的每个粒度属性列生成一列；为与维度（与该表基于的度量值组具有事实维度关系）的每个属性关联的绑定生成一列或多列。</span><span class="sxs-lookup"><span data-stu-id="d27db-137">The wizard also generates one column for each granularity attribute column of each regular dimension relationship on the measure group, and one or more columns for the bindings associated to each attribute of a dimension that has a fact dimension relationship to the measure group on which this table is based, if applicable.</span></span>  
  
 <span data-ttu-id="d27db-138">关系</span><span class="sxs-lookup"><span data-stu-id="d27db-138">Relationships</span></span>  
 <span data-ttu-id="d27db-139">向导会为每个从事实数据表到维度表的粒度属性的常规维度关系生成一种关系。</span><span class="sxs-lookup"><span data-stu-id="d27db-139">The wizard generates one relationship for each regular dimension relationship from the fact table to the dimension table's granularity attribute.</span></span> <span data-ttu-id="d27db-140">如果粒度基于维度表的键属性，则在数据库和数据源视图中创建关系。</span><span class="sxs-lookup"><span data-stu-id="d27db-140">If the granularity is based on the key attribute of the dimension table, the relationship is created in the database and in the data source view.</span></span> <span data-ttu-id="d27db-141">如果粒度基于其他属性，则仅在数据源视图中创建关系。</span><span class="sxs-lookup"><span data-stu-id="d27db-141">If the granularity is based on another attribute, the relationship is created only in the data source view.</span></span>  
  
 <span data-ttu-id="d27db-142">如果选择在向导中生成索引，则会为这些关系列中的每个关系列生成非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="d27db-142">If you chose to generate indexes in the wizard, a nonclustered index is generated for each of these relationship columns.</span></span>  
  
 <span data-ttu-id="d27db-143">约束</span><span class="sxs-lookup"><span data-stu-id="d27db-143">Constraints</span></span>  
 <span data-ttu-id="d27db-144">主键不会在事实数据表中生成。</span><span class="sxs-lookup"><span data-stu-id="d27db-144">Primary keys are not generated on fact tables.</span></span>  
  
 <span data-ttu-id="d27db-145">如果您选择强制实施引用完整性，则会在适当的时候，在维度表和事实数据表之间生成引用完整性约束。</span><span class="sxs-lookup"><span data-stu-id="d27db-145">If you chose to enforce referential integrity, referential integrity constraints are generated between dimension tables and fact tables where applicable.</span></span>  
  
 <span data-ttu-id="d27db-146">翻译</span><span class="sxs-lookup"><span data-stu-id="d27db-146">Translations</span></span>  
 <span data-ttu-id="d27db-147">向导会生成一个单独的表以保存度量值组中需要翻译列的任意属性的翻译值。</span><span class="sxs-lookup"><span data-stu-id="d27db-147">The wizard generates a separate table to hold the translated values for any property in the measure group that requires a translation column.</span></span> <span data-ttu-id="d27db-148">向导还会为每种所需的语言创建一个单独的列。</span><span class="sxs-lookup"><span data-stu-id="d27db-148">The wizard also creates a separate column for each of the required languages.</span></span>  
  
## <a name="data-type-conversion-and-default-lengths"></a><span data-ttu-id="d27db-149">数据类型转换和默认长度</span><span class="sxs-lookup"><span data-stu-id="d27db-149">Data Type Conversion and Default Lengths</span></span>  
 <span data-ttu-id="d27db-150">架构生成向导会在所有情况下忽略数据类型，但使用数据类型的列除外 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `wchar` 。</span><span class="sxs-lookup"><span data-stu-id="d27db-150">Schema Generation Wizard ignores data types in all cases except for columns that use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `wchar` data type.</span></span> <span data-ttu-id="d27db-151">`wchar` 数据大小直接翻译为 `nvarchar` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="d27db-151">The `wchar` data size translates directly to the `nvarchar` data type.</span></span> <span data-ttu-id="d27db-152">但是，如果使用 `wchar` 大小的列的指定长度大于 4000 字节，则架构生成向导会生成一个错误。</span><span class="sxs-lookup"><span data-stu-id="d27db-152">However, if the specified length of a column using the `wchar` size is larger than 4000 bytes, the Schema Generation Wizard generates an error.</span></span>  
  
 <span data-ttu-id="d27db-153">如果数据项（如属性的绑定）没有指定的长度，则针对该列使用下表中列出的默认长度。</span><span class="sxs-lookup"><span data-stu-id="d27db-153">If a data item, such as the binding for an attribute, has no specified length, the default length listed in the following table is used for the column.</span></span>  
  
|<span data-ttu-id="d27db-154">数据项</span><span class="sxs-lookup"><span data-stu-id="d27db-154">Data item</span></span>|<span data-ttu-id="d27db-155">默认长度（字节）</span><span class="sxs-lookup"><span data-stu-id="d27db-155">Default length (bytes)</span></span>|  
|---------------|------------------------------|  
|<span data-ttu-id="d27db-156">KeyColumn</span><span class="sxs-lookup"><span data-stu-id="d27db-156">KeyColumn</span></span>|<span data-ttu-id="d27db-157">50</span><span class="sxs-lookup"><span data-stu-id="d27db-157">50</span></span>|  
|<span data-ttu-id="d27db-158">NameColumn</span><span class="sxs-lookup"><span data-stu-id="d27db-158">NameColumn</span></span>|<span data-ttu-id="d27db-159">50</span><span class="sxs-lookup"><span data-stu-id="d27db-159">50</span></span>|  
|<span data-ttu-id="d27db-160">CustomRollupColumn</span><span class="sxs-lookup"><span data-stu-id="d27db-160">CustomRollupColumn</span></span>|<span data-ttu-id="d27db-161">3000</span><span class="sxs-lookup"><span data-stu-id="d27db-161">3000</span></span>|  
|<span data-ttu-id="d27db-162">CustomRollupPropertiesColumn</span><span class="sxs-lookup"><span data-stu-id="d27db-162">CustomRollupPropertiesColumn</span></span>|<span data-ttu-id="d27db-163">500</span><span class="sxs-lookup"><span data-stu-id="d27db-163">500</span></span>|  
|<span data-ttu-id="d27db-164">UnaryOperatorColumn</span><span class="sxs-lookup"><span data-stu-id="d27db-164">UnaryOperatorColumn</span></span>|<span data-ttu-id="d27db-165">1</span><span class="sxs-lookup"><span data-stu-id="d27db-165">1</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d27db-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d27db-166">See Also</span></span>  
 <span data-ttu-id="d27db-167">[了解增量生成](understanding-incremental-generation.md) </span><span class="sxs-lookup"><span data-stu-id="d27db-167">[Understanding Incremental Generation](understanding-incremental-generation.md) </span></span>  
 [<span data-ttu-id="d27db-168">管理对数据源视图和数据源所做的更改</span><span class="sxs-lookup"><span data-stu-id="d27db-168">Manage Changes to Data Source Views and Data Sources</span></span>](manage-changes-to-data-source-views-and-data-sources.md)  
  
  
