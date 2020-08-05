---
title: CSDLBI 概念 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 2fbdf621-a94d-4a55-a088-3d56d65016ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: 16c6597171eef10da67ad497e4303b3716298e6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580429"
---
# <a name="csdlbi-concepts"></a><span data-ttu-id="25999-102">CSDLBI 概念</span><span class="sxs-lookup"><span data-stu-id="25999-102">CSDLBI Concepts</span></span>
  <span data-ttu-id="25999-103">带 BI 注释的概念性架构定义语言 (CSDLBI) 基于实体数据框架。实体数据框架是一个抽象概念，用于以某种方式表示不同类型的数据，以便能够以编程方式访问、查询或导出不同的数据集。</span><span class="sxs-lookup"><span data-stu-id="25999-103">Conceptual Schema Definition Language with BI annotations (CSDLBI) is based on the Entity Data Framework, which is an abstraction for representing data in a way that enables disparate data sets to be programmatically accessed, queried, or exported.</span></span> <span data-ttu-id="25999-104">CSDLBI 用于表示使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 创建的数据模型，因为它支持丰富的数据驱动的报告和应用程序。</span><span class="sxs-lookup"><span data-stu-id="25999-104">CSDLBI is used to represent data models created using [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] because it supports rich, data-driven reporting and applications.</span></span>  
  
 <span data-ttu-id="25999-105">这部分说明 CSDLBI 表示形式如何映射到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据模型（表格和多维）以及每种模型类型的示例。</span><span class="sxs-lookup"><span data-stu-id="25999-105">This section explains how the CSDLBI representation maps to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data models (both tabular and multidimensional), along with examples of each model type.</span></span>  
  
 <span data-ttu-id="25999-106">用于说明这些概念的示例取自 Codeplex 上提供的 AdventureWorks 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="25999-106">Examples used to illustrate these concepts are taken from the AdventureWorks sample database, available on Codeplex.</span></span> <span data-ttu-id="25999-107">有关示例的详细信息，请参阅[SQL Server 的艾德作品示例](https://go.microsoft.com/fwlink/?linkID=220093)。</span><span class="sxs-lookup"><span data-stu-id="25999-107">For more information about the samples, see [Adventure Works Samples for SQL Server](https://go.microsoft.com/fwlink/?linkID=220093).</span></span>  
  
## <a name="structure-of-a-tabular-model-in-csdlbi"></a><span data-ttu-id="25999-108">CSDLBI 中表格模型的结构</span><span class="sxs-lookup"><span data-stu-id="25999-108">Structure of a Tabular Model in CSDLBI</span></span>  
 <span data-ttu-id="25999-109">描述报表模型及其数据的 CSDLBI 文档以 xsd 语句开头，后跟模型的定义。</span><span class="sxs-lookup"><span data-stu-id="25999-109">A CSDLBI document that describes a report model and its data begins with the xsd statement, followed by the definition of a model.</span></span>  
  
 <span data-ttu-id="25999-110">模型是一个命名空间，其中包含以下主要实体、关联和属性：</span><span class="sxs-lookup"><span data-stu-id="25999-110">The model is a namespace, which contains the following major entities, associations, and properties:</span></span>  
  
-   <span data-ttu-id="25999-111">`EntityContainer` 列出了模型中的表。</span><span class="sxs-lookup"><span data-stu-id="25999-111">The `EntityContainer` lists the tables in the model.</span></span>  
  
-   <span data-ttu-id="25999-112">每个表将与 `EntityContainer` 一起作为 `EntitySet` 列出。</span><span class="sxs-lookup"><span data-stu-id="25999-112">Each table is listed with the `EntityContainer` as an `EntitySet`.</span></span>  
  
-   <span data-ttu-id="25999-113">两个表之间的每个关系均被描述为一个 `AssociationSet`，用于定义关系端点和关系角色。</span><span class="sxs-lookup"><span data-stu-id="25999-113">Each relationship between two tables is described as an `AssociationSet` that defines the relationship end points and the relationship roles.</span></span>  
  
-   <span data-ttu-id="25999-114">`EntityType` 元素针对 BISM 进行了扩展，以提供有关 BISM 中的表和列的其他详细信息，包括用于排序和显示的属性。</span><span class="sxs-lookup"><span data-stu-id="25999-114">The `EntityType` element is extended for BISM to provide additional detail about the tables and the columns in them, including properties for sorting and display purposes.</span></span>  
  
-   <span data-ttu-id="25999-115">`Measure` 元素定义了可在模型中使用的计算。</span><span class="sxs-lookup"><span data-stu-id="25999-115">The `Measure` element defines calculations that can be used in the model.</span></span> <span data-ttu-id="25999-116">可通过使用新的 `KPI` 元素添加一组特殊显示属性来将度量值转换为 KPI。</span><span class="sxs-lookup"><span data-stu-id="25999-116">A measure can be turned into a KPI by adding a set of special display attributes, using the new `KPI` Element.</span></span>  
  
-   <span data-ttu-id="25999-117">没有针对透视的单独表示形式。</span><span class="sxs-lookup"><span data-stu-id="25999-117">There is no separate representation of perspectives.</span></span> <span data-ttu-id="25999-118">虽然透视中未包含的列和表将用 CSDL 表示，但会由 `Hidden` 属性进行标记。</span><span class="sxs-lookup"><span data-stu-id="25999-118">Columns and tables that are not included in a perspective are present in the CSDL but flagged with the `Hidden` attribute.</span></span>  
  
### <a name="entities-entitysets-and-entitytypes"></a><span data-ttu-id="25999-119">实体、EntitySet 和 EntityType</span><span class="sxs-lookup"><span data-stu-id="25999-119">Entities, EntitySets, and EntityTypes</span></span>  
 <span data-ttu-id="25999-120">已对实体数据框架中的实体概念进行扩展，以便表示数据模型中的列和表。</span><span class="sxs-lookup"><span data-stu-id="25999-120">The notion of an entity in the Entity Data Framework is extended to represent columns and tables from the data model.</span></span> <span data-ttu-id="25999-121">以下摘录显示了仅包含三个表的简单模型中的 `EntitySet` 元素的列表。</span><span class="sxs-lookup"><span data-stu-id="25999-121">The following excerpt shows the list of `EntitySet` elements in a simple model containing only three tables.</span></span>  
  
```  
<EntityContainer Name="SimpleModel">  
<EntitySet Name="DimCustomer"EntityType="SimpleModel.DimCustomer">  
     <bi:EntitySet />  
   </EntitySet>  
<EntitySet Name="DimDate" EntityType="SimpleModel.DimDate">  
     <bi:EntitySet />  
   </EntitySet>  
<EntitySet Name="DimGeography" EntityType="SimpleModel.DimGeography">  
     <bi:EntitySet />  
   </EntitySet> />  
  
```  
  
 <span data-ttu-id="25999-122">`EntitySet` 不包含表中的列或数据的相关信息。</span><span class="sxs-lookup"><span data-stu-id="25999-122">The `EntitySet` does not contain information about columns or data in the table.</span></span> <span data-ttu-id="25999-123">EntityType 元素中提供了列及其属性的详细说明。</span><span class="sxs-lookup"><span data-stu-id="25999-123">The detailed description of the columns and their properties is provided in the EntityType element.</span></span>  
  
 <span data-ttu-id="25999-124">每个实体（表）的 `EntitySet` 元素包括一个属性集合，这些属性定义键列、列的数据类型和长度、为 null 性、排序行为等。</span><span class="sxs-lookup"><span data-stu-id="25999-124">The `EntitySet` element for each entity (table) includes a collection of properties that define the key column, the data type and length of the column, nullability, sorting behavior, and so forth.</span></span> <span data-ttu-id="25999-125">例如，以下 CSDL 摘录描述了 Customer 表中的三列。</span><span class="sxs-lookup"><span data-stu-id="25999-125">For example, the following CSDL excerpt describes three columns in the Customer table.</span></span> <span data-ttu-id="25999-126">第一列是模型在内部使用的特殊隐藏列。</span><span class="sxs-lookup"><span data-stu-id="25999-126">The first column is a special hidden column used internally by the model.</span></span>  
  
```  
<EntityType Name="Customer">  
  <Key>  
     <PropertyRef Name="RowNumber" />  
  </Key>  
    <Property Name="RowNumber" Type="Int64" Nullable="false">  
     <bi:Property Hidden="true" Contents="RowNumber"  
       Stability="RowNumber" />  
    </Property>  
    <Property Name="CustomerKey" Type="Int64" Nullable="false">  
      <bi:Property />  
    </Property>  
     <Property Name="FirstName" Type="String" MaxLength="Max" FixedLength="false">  
       <bi:Property />  
      </Property>  
  
```  
  
 <span data-ttu-id="25999-127">为了限制生成的 CSDLBI 文档的大小，在实体中出现多次的属性将由对某个现有属性的引用指定，这样，只需为 `EntityType` 列出该属性一次。</span><span class="sxs-lookup"><span data-stu-id="25999-127">To limit the size of the CSDLBI document that is generated, properties that appear more than once in an entity are specified by a reference to an existing property, so that the property need be listed only once for the `EntityType`.</span></span> <span data-ttu-id="25999-128">客户端应用程序可通过查找与 `EntityType` 匹配的 `OriginEntityType` 来获取属性的值。</span><span class="sxs-lookup"><span data-stu-id="25999-128">The client application can get the value of the property by finding the `EntityType` that matches the `OriginEntityType`.</span></span>  
  
### <a name="relationships"></a><span data-ttu-id="25999-129">关系</span><span class="sxs-lookup"><span data-stu-id="25999-129">Relationships</span></span>  
 <span data-ttu-id="25999-130">在 Entity Data Framework 中，关系定义为实体之间的*关联*。</span><span class="sxs-lookup"><span data-stu-id="25999-130">In the Entity Data Framework, relationships are defined as *associations* between entities.</span></span>  
  
 <span data-ttu-id="25999-131">关联始终有两个端点，每个端点指向表中的一个字段或一个列。</span><span class="sxs-lookup"><span data-stu-id="25999-131">Associations always have exactly two ends, each pointing to a field or column in a table.</span></span> <span data-ttu-id="25999-132">因此，两个表之间可以存在多个关系，前提是这些关系具有不同的端点。</span><span class="sxs-lookup"><span data-stu-id="25999-132">Therefore, multiple relationships are possible between two tables, if the relationships have different end points.</span></span> <span data-ttu-id="25999-133">将为关联的端点分配角色名称，并指示如何在数据模型的上下文中使用关联。</span><span class="sxs-lookup"><span data-stu-id="25999-133">A role name is assigned to the end points of the association, and indicates how the association is used in the context of the data model.</span></span> <span data-ttu-id="25999-134">当应用于与 Orders 表中的客户 ID 相关的客户 ID 时，角色名称的一个示例可能是**ShipTo**的。</span><span class="sxs-lookup"><span data-stu-id="25999-134">An example of a role name might be **ShipTo**, when applied to a customer ID that is related to the customer ID in an Orders table.</span></span>  
  
 <span data-ttu-id="25999-135">模型的 CSDLBI 表示形式还包含关联上的属性，这些属性确定实体如何根据关联的*重数相互*映射。</span><span class="sxs-lookup"><span data-stu-id="25999-135">The CSDLBI representation of the model also contains attributes on the association that determine how the entities are mapped to each other in terms of the *multiplicity* of the association.</span></span> <span data-ttu-id="25999-136">多重性指示位于表之间的关系的端点上的属性或列是位于关系的一方还是多方。</span><span class="sxs-lookup"><span data-stu-id="25999-136">Multiplicity indicates whether the attribute or column at the end point of a relationship between tables is on the one side of a relationship, or on the many side.</span></span> <span data-ttu-id="25999-137">没有针对一对一关系的单独的值。</span><span class="sxs-lookup"><span data-stu-id="25999-137">There is no separate value for one-to-one relationships.</span></span> <span data-ttu-id="25999-138">CSDLBI 注释支持多重性为 0（表示实体未与任何对象关联）或为 0..1（表示一对一关系或一对多关系）。</span><span class="sxs-lookup"><span data-stu-id="25999-138">CSDLBI annotations support multiplicity of 0 (meaning the entity is not associated with anything) or 0..1, which means either a one-one relationship or a one-to-many relationship.</span></span>  
  
 <span data-ttu-id="25999-139">以下示例表示 Date 表和 ProductInventory 表之间的关系的 CSDLBI 输出，其中这两个表通过 DateAlternateKey 列联接。</span><span class="sxs-lookup"><span data-stu-id="25999-139">The following sample represents the CSDLBI output for a relationship between the tables, Date and ProductInventory, where the two tables are joined on the column DateAlternateKey.</span></span> <span data-ttu-id="25999-140">请注意，默认情况下，`AssociationSet` 的名称是关系中涉及的列的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="25999-140">Notice that, by default, the name of the `AssociationSet` is the fully qualified name of the columns that are involved in the relationship.</span></span> <span data-ttu-id="25999-141">但是，可以在设计模型时将此行为更改为使用其他命名格式。</span><span class="sxs-lookup"><span data-stu-id="25999-141">However, you can change this behavior when you design the model, to use a different naming format.</span></span>  
  
```  
<AssociationSet Name="ProductInventory_Date_DateKey" Association="Model.ProductInventory_Date_DateKey">  
              <End EntitySet="ProductInventory" />  
              <End EntitySet="Date" />  
              <bi:AssociationSet />  
            </AssociationSet>  
  
```  
  
### <a name="visualization-and-navigation-properties"></a><span data-ttu-id="25999-142">可视化和导航属性</span><span class="sxs-lookup"><span data-stu-id="25999-142">Visualization and Navigation Properties</span></span>  
 <span data-ttu-id="25999-143">用于定义报告层中的表示形式和导航实体之间的关系的属性是 CSDLBI 注释的一个重要部分。</span><span class="sxs-lookup"><span data-stu-id="25999-143">An important part of the CSDLBI annotations are the properties for defining presentation in the reporting layer, and for navigating the relationships among entities.</span></span> <span data-ttu-id="25999-144">通常，基于客户端应用程序将指定排序和表示形式的其他详细信息这种假设，在创建数据模型时，您会认为控制数据的排序和分组方式或可能的默认值并不重要。</span><span class="sxs-lookup"><span data-stu-id="25999-144">Typically, when you are creating a data model, you do not consider it important to control how the data is ordered or grouped, or what the default value might be, on the assumption that the client application will specify ordering and other details of presentation.</span></span> <span data-ttu-id="25999-145">但是，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 表格模型设计为可以与 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 报表客户端集成，并在报表设计图面中包含支持数据模型中的实体的表示形式的属性和特性。</span><span class="sxs-lookup"><span data-stu-id="25999-145">However, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tabular models are designed for integration with the [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reporting client, and includes properties and attributes that support presentation of entities from the data model in the report design surface.</span></span>  
  
 <span data-ttu-id="25999-146">针对可视化的扩展包括用于以下用途的属性：指定要用于数值数据的默认聚合、指示指向图像的 URL 的文本字段或指定用于为当前字段进行排序的字段。</span><span class="sxs-lookup"><span data-stu-id="25999-146">Extensions for visualization include attributes for specifying the default aggregation to use with numerical data, for indicating that a text field points to a URL of an image, or specifying the field used to sort the current field.</span></span>  
  
### <a name="name-properties-and-naming-conventions"></a><span data-ttu-id="25999-147">名称属性和命名约定</span><span class="sxs-lookup"><span data-stu-id="25999-147">Name Properties and Naming Conventions</span></span>  
 <span data-ttu-id="25999-148">CSDLBI 架构规定每个实体具有一个唯一名称和一个可用作密钥的标识符。</span><span class="sxs-lookup"><span data-stu-id="25999-148">The CSDLBI schema provides that each entity has a unique name and an identifier that can be used as a key.</span></span> <span data-ttu-id="25999-149">此外，某些实体可具有用于显示的标题和随实体的使用位置的不同而不同的上下文名称。</span><span class="sxs-lookup"><span data-stu-id="25999-149">In addition, some entities can have captions used for display purposes, and contextual names that change depending on where the entity is used.</span></span>  
  
 <span data-ttu-id="25999-150">`Documentation` 元素使报表设计人员能够提供实体的说明并帮助业务用户了解数据的含义。</span><span class="sxs-lookup"><span data-stu-id="25999-150">The `Documentation` element provides the opportunity for report designers to furnish a description of the entity, to help business users understand the meaning of the data.</span></span> <span data-ttu-id="25999-151">某些实体还允许一个或多个 `Annotation` 属性，这些属性提供可由应用程序或客户端使用的额外元数据。</span><span class="sxs-lookup"><span data-stu-id="25999-151">Some entities also allow one or more `Annotation` attributes, which provide extra metadata for consumption by the application or by clients.</span></span>  
  
 <span data-ttu-id="25999-152">使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 工具生成模型时，为对象创建的名称应遵循对象命名的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 约定和名称唯一性。</span><span class="sxs-lookup"><span data-stu-id="25999-152">When you generate a model the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tools, the names that are created for objects follow the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] conventions for object naming and name uniqueness.</span></span> <span data-ttu-id="25999-153">但是，由于 CSDLBI 基于实体数据框架 (EDF)，而实体数据框架要求名称遵循 C# 标识符的约定，因此，服务器在为模型创建 CSDLBI 输出时将采用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 架构中使用的名称，并将自动创建符合 EDF 要求的新对象名称。</span><span class="sxs-lookup"><span data-stu-id="25999-153">However, because CSDLBI is based on the Entity Data Framework (EDF), which requires that names adhere to conventions for C# identifiers, when the server creates the CSDLBI output for a model, the server takes the names used within the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] schema and automatically creates new object names that comply with EDF requirements.</span></span> <span data-ttu-id="25999-154">下表描述了用于生成新名称的操作。</span><span class="sxs-lookup"><span data-stu-id="25999-154">The following table describes the operations by which the new names are generated.</span></span>  
  
|<span data-ttu-id="25999-155">规则</span><span class="sxs-lookup"><span data-stu-id="25999-155">Rule</span></span>|<span data-ttu-id="25999-156">操作</span><span class="sxs-lookup"><span data-stu-id="25999-156">Action</span></span>|  
|----------|------------|  
|<span data-ttu-id="25999-157">无禁止字符</span><span class="sxs-lookup"><span data-stu-id="25999-157">No forbidden characters</span></span>|<span data-ttu-id="25999-158">禁止字符将由下划线替换。</span><span class="sxs-lookup"><span data-stu-id="25999-158">Forbidden characters are replaced by underscore.</span></span>|  
|<span data-ttu-id="25999-159">名称必须是唯一的</span><span class="sxs-lookup"><span data-stu-id="25999-159">Names must be unique</span></span>|<span data-ttu-id="25999-160">如果两个字符串相同，则通过为一个字符串追加下划线和数字使其具有唯一性</span><span class="sxs-lookup"><span data-stu-id="25999-160">If two strings are the same, one is made unique by appending underscore plus a number</span></span>|  
  
> [!WARNING]  
>  <span data-ttu-id="25999-161">标题和限定符都有对应的译文，而对于某种给定语言，可能只存在二者之一。</span><span class="sxs-lookup"><span data-stu-id="25999-161">Captions and qualifiers both have translations, and for a given language, one or the other might be present.</span></span> <span data-ttu-id="25999-162">这意味着，当限定符与名称或限定符与标题串联时，字符串可用两种不同的语言表示。</span><span class="sxs-lookup"><span data-stu-id="25999-162">This means that in cases where a qualifier and name or qualifier and caption are concatenated, the strings could be in two different languages.</span></span>  
  
## <a name="additions-to-support-multidimensional-models"></a><span data-ttu-id="25999-163">所增加的用于支持多维模型的内容</span><span class="sxs-lookup"><span data-stu-id="25999-163">Additions to Support Multidimensional Models</span></span>  
 <span data-ttu-id="25999-164">CSDLBI 注释 1.0 版仅支持表格模型。</span><span class="sxs-lookup"><span data-stu-id="25999-164">Version 1.0 of the CSDLBI annotations supported only tabular models.</span></span> <span data-ttu-id="25999-165">在版本 1.1 中，添加了对使用传统 BI 开发工具创建的多维模型（OLAP 多维数据集）的支持。</span><span class="sxs-lookup"><span data-stu-id="25999-165">In version 1.1, support was added for multidimensional models (OLAP cubes) created using traditional BI development tools.</span></span> <span data-ttu-id="25999-166">因此，您现在可以向多维模型发出 XML 请求并接收模型的 CSDLBI 定义，以用于报告。</span><span class="sxs-lookup"><span data-stu-id="25999-166">Therefore, you can now issue an XML request to a multidimensional model and receive a CSDLBI definition of the model, for use in reporting.</span></span>  
  
 <span data-ttu-id="25999-167">**多维数据集：** SQL Server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 表格数据库只能包含一种模式。</span><span class="sxs-lookup"><span data-stu-id="25999-167">**Cubes:** A SQL Server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tabular database can contain only one mode.</span></span> <span data-ttu-id="25999-168">相比较而言，每个多维数据库可以包含多个多维数据集，每个数据库与一个默认的多维数据集关联。</span><span class="sxs-lookup"><span data-stu-id="25999-168">In contrast, each multidimensional database can contain multiple cubes, each database being associated with a default cube.</span></span> <span data-ttu-id="25999-169">因此，当针对多维服务器发出 XML 请求时，需要指定多维数据集；否则，将返回默认多维数据集的 XML。</span><span class="sxs-lookup"><span data-stu-id="25999-169">Therefore, when issuing an XML request against a multidimensional server, it is necessary to specify the cube; otherwise, the XML for the default cube will be returned.</span></span>  
  
 <span data-ttu-id="25999-170">多维数据集的表示形式与表格模型数据库的表示形式非常相似。</span><span class="sxs-lookup"><span data-stu-id="25999-170">The representation of a cube is otherwise very much like that of a tabular model database.</span></span> <span data-ttu-id="25999-171">多维数据集名称和多维数据集分别对应于表格数据库名称和数据库标识符。</span><span class="sxs-lookup"><span data-stu-id="25999-171">The cube name and cube correspond to the tabular database name and database identifier.</span></span>  
  
 <span data-ttu-id="25999-172">**维度：** 维度在 CSDLBI 中表示为具有列和属性的实体 (表) 。</span><span class="sxs-lookup"><span data-stu-id="25999-172">**Dimensions:** A dimension is represented in CSDLBI as an entity (table) with columns and properties.</span></span> <span data-ttu-id="25999-173">请注意，即使未包括在透视中，模型中包括的维度也将表示为 CSDL 输出（标记为 `Hidden`）。</span><span class="sxs-lookup"><span data-stu-id="25999-173">Note that even if not included in a perspective, a dimension that is included in the model will be represented in the CSDL output, marked as `Hidden`.</span></span>  
  
 <span data-ttu-id="25999-174">**透视：** 客户端可以请求单个透视图的 CSDL。</span><span class="sxs-lookup"><span data-stu-id="25999-174">**Perspectives:** A client can request CSDL for individual perspectives.</span></span> <span data-ttu-id="25999-175">有关详细信息，请参阅[DISCOVER_CSDL_METADATA 行集](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-csdl-metadata-rowset)。</span><span class="sxs-lookup"><span data-stu-id="25999-175">For more information, see [DISCOVER_CSDL_METADATA Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-csdl-metadata-rowset).</span></span>  
  
 <span data-ttu-id="25999-176">**层次结构：** 层次结构支持并在 CSDLBI 中表示为一组级别。</span><span class="sxs-lookup"><span data-stu-id="25999-176">**Hierarchies:** Hierarchies are supported and represented in CSDLBI as a set of levels.</span></span>  
  
 <span data-ttu-id="25999-177">**成员：** 已添加对默认成员的支持，并且默认值自动添加到 CSDLBI 输出。</span><span class="sxs-lookup"><span data-stu-id="25999-177">**Members:** Support for the default member has been added and default values are automatically added to the CSDLBI output.</span></span>  
  
 <span data-ttu-id="25999-178">**计算成员：** 多维模型支持具有单个真实成员的**所有**子级的计算成员。</span><span class="sxs-lookup"><span data-stu-id="25999-178">**Calculated Members:** Multidimensional models support calculated members for child of **All** with a single real member.</span></span>  
  
 <span data-ttu-id="25999-179">**维度属性：** 在 CSDLBI 输出中，支持维度属性，并自动将其标记为不可聚合。</span><span class="sxs-lookup"><span data-stu-id="25999-179">**Dimension attributes:** In CSDLBI output, dimension attributes are supported and automatically marked as non-aggregatable.</span></span>  
  
 <span data-ttu-id="25999-180">**Kpi：** CSDLBI 版本1.1 中支持 Kpi，但表示形式已更改。</span><span class="sxs-lookup"><span data-stu-id="25999-180">**KPIs:** KPIs were supported in CSDLBI version 1.1, but the representation has changed.</span></span> <span data-ttu-id="25999-181">以前，KPI 是度量值的属性。</span><span class="sxs-lookup"><span data-stu-id="25999-181">Before, a KPI was a property of a measure.</span></span> <span data-ttu-id="25999-182">在版本1.1 中，可以将 KPI 元素添加到度量值</span><span class="sxs-lookup"><span data-stu-id="25999-182">In version 1.1, the KPI element can be added to a measure</span></span>  
  
 <span data-ttu-id="25999-183">**新属性：** 添加了其他属性以支持 DirectQuery 模型。</span><span class="sxs-lookup"><span data-stu-id="25999-183">**New properties:** Additional attributes were added to support DirectQuery models.</span></span>  
  
 <span data-ttu-id="25999-184">**限制：** 不支持单元安全性。</span><span class="sxs-lookup"><span data-stu-id="25999-184">**Limitations:** Cell security is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25999-185">另请参阅</span><span class="sxs-lookup"><span data-stu-id="25999-185">See Also</span></span>  
 [<span data-ttu-id="25999-186">用于商业智能的 CSDL 批注 (CSDLBI)</span><span class="sxs-lookup"><span data-stu-id="25999-186">CSDL Annotations for Business Intelligence &#40;CSDLBI&#41;</span></span>](/analysis-services/csdlbi/csdl-annotations-for-business-intelligence-csdlbi)  
  
  
