---
title: 架构生成向导 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- relational schema [Analysis Services]
ms.assetid: 68bf7ba3-d0cb-437f-9a3e-9edc0999af19
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2cd58ada8ea4c2dd17ba4427578ac1336a6bd353
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588723"
---
# <a name="schema-generation-wizard-analysis-services"></a><span data-ttu-id="c28af-102">架构生成向导 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="c28af-102">Schema Generation Wizard (Analysis Services)</span></span>
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="c28af-103">项目或数据库中定义 OLAP 对象时， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 支持两种使用关系架构的方法。</span><span class="sxs-lookup"><span data-stu-id="c28af-103">supports two methods of working with relational schemas when defining OLAP objects within an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span> <span data-ttu-id="c28af-104">通常，在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目或数据库中，将基于在数据源视图中构造的逻辑数据模型来定义 OLAP 对象。</span><span class="sxs-lookup"><span data-stu-id="c28af-104">Generally, you will define OLAP objects based on a logical data model constructed in a data source view within an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span> <span data-ttu-id="c28af-105">此数据源视图将基于一个或多个关系数据源中的架构元素定义，如在数据源视图中自定义那样。</span><span class="sxs-lookup"><span data-stu-id="c28af-105">This data source view is defined based on schema elements from one or more relational data sources, as customized in the data source view.</span></span>  
  
 <span data-ttu-id="c28af-106">或者，您可以首先定义 OLAP 对象，然后生成数据源视图、数据源和支持这些 OLAP 对象的基础关系数据库架构。</span><span class="sxs-lookup"><span data-stu-id="c28af-106">Alternatively, you can define OLAP objects first, and then generate a data source view, a data source, and the underlying relational database schema that supports these OLAP objects.</span></span> <span data-ttu-id="c28af-107">该关系数据库称为主题区域数据库。</span><span class="sxs-lookup"><span data-stu-id="c28af-107">This relational database is referred to as the subject area database.</span></span>  
  
 <span data-ttu-id="c28af-108">此方法有时称为由上而下设计，并且通常用于对建模确定原型并进行分析。</span><span class="sxs-lookup"><span data-stu-id="c28af-108">This approach is sometimes called top-down design and is frequently used for prototyping and analysis modeling.</span></span> <span data-ttu-id="c28af-109">使用此方法时，使用架构生成向导基于在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目或数据库中定义的 OLAP 对象创建基础数据源视图和数据源对象。</span><span class="sxs-lookup"><span data-stu-id="c28af-109">When you use this approach, you use the Schema Generation Wizard to create the underlying data source view and data source objects based on the OLAP objects defined in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span>  
  
 <span data-ttu-id="c28af-110">这是一个迭代的方法。</span><span class="sxs-lookup"><span data-stu-id="c28af-110">This is an iterative approach.</span></span> <span data-ttu-id="c28af-111">更改维度和多维数据集的设计时，您很可能多次重新运行该向导。</span><span class="sxs-lookup"><span data-stu-id="c28af-111">You will most likely rerun the wizard multiple times as you change the design of the dimensions and cubes.</span></span> <span data-ttu-id="c28af-112">每次运行该向导时，它会将更改合并到基础对象中，并尽可能保留基础数据库中的数据。</span><span class="sxs-lookup"><span data-stu-id="c28af-112">Each time you run the wizard, it incorporates the changes into the underlying objects and, as much as is possible, preserves the data contained in the underlying databases.</span></span>  
  
 <span data-ttu-id="c28af-113">生成的架构是 SQL Server 关系数据库引擎架构。</span><span class="sxs-lookup"><span data-stu-id="c28af-113">The schema that is generated is a SQL Server relational database engine schema.</span></span> <span data-ttu-id="c28af-114">该向导不生成其他关系数据库产品的架构。</span><span class="sxs-lookup"><span data-stu-id="c28af-114">The wizard does not generate schemas for other relational database products.</span></span>  
  
 <span data-ttu-id="c28af-115">使用您用于填充 SQL Server 关系数据库的任意工具和技术单独添加在主题区域数据库中填充的数据。</span><span class="sxs-lookup"><span data-stu-id="c28af-115">The data that is populated in the subject area database is added separately, using whatever tools and techniques you use to populate a SQL Server relational database.</span></span> <span data-ttu-id="c28af-116">在大多数情况下，重新运行向导时会保留该数据，但是也有例外。</span><span class="sxs-lookup"><span data-stu-id="c28af-116">In most cases, the data is preserved when you rerun the wizard, but there are exceptions.</span></span> <span data-ttu-id="c28af-117">例如，如果您删除包含数据的维度或属性，则必须删除某些数据。</span><span class="sxs-lookup"><span data-stu-id="c28af-117">For example, some data must be dropped if you delete a dimension or an attribute that contains data.</span></span> <span data-ttu-id="c28af-118">如果架构生成向导因架构的更改必须删除某些数据，则您便会在删除数据之前收到一则警告，然后可以取消重新生成。</span><span class="sxs-lookup"><span data-stu-id="c28af-118">If the Schema Generation Wizard must drop some data because of a schema change, you receive a warning before the data is dropped and can then cancel the regeneration.</span></span>  
  
 <span data-ttu-id="c28af-119">作为通用规则，当架构生成向导在以后重新生成对象时，对最初由架构生成向导生成的对象所做的任何更改都要被覆盖。</span><span class="sxs-lookup"><span data-stu-id="c28af-119">As a general rule, any change that you make to an object that was originally generated by the Schema Generation Wizard is overwritten when the Schema Generation Wizard subsequently regenerates that object.</span></span> <span data-ttu-id="c28af-120">但是，当您将列添加到架构生成向导生成的表中时，便属于此规则的主要例外情况。</span><span class="sxs-lookup"><span data-stu-id="c28af-120">The primary exception to this rule is when you add columns to a table that the Schema Generation Wizard generated.</span></span> <span data-ttu-id="c28af-121">在这种情况下，架构生成向导将保留您添加到表中的列以及这些列中的数据。</span><span class="sxs-lookup"><span data-stu-id="c28af-121">In this case, the Schema Generation Wizard preserves the columns that you added to the table, as well as the data in these columns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c28af-122">本节内容</span><span class="sxs-lookup"><span data-stu-id="c28af-122">In this section</span></span>  
 <span data-ttu-id="c28af-123">下表列出了说明如何使用架构生成向导的其他主题。</span><span class="sxs-lookup"><span data-stu-id="c28af-123">The following table lists additional topics that explain how to work with the Schema Generation Wizard.</span></span>  
  
|<span data-ttu-id="c28af-124">主题</span><span class="sxs-lookup"><span data-stu-id="c28af-124">Topic</span></span>|<span data-ttu-id="c28af-125">说明</span><span class="sxs-lookup"><span data-stu-id="c28af-125">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c28af-126">使用架构生成向导 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="c28af-126">Use the Schema Generation Wizard &#40;Analysis Services&#41;</span></span>](schema-generation-wizard-analysis-services.md)|<span data-ttu-id="c28af-127">介绍如何为主题区域数据库和临时区域数据库生成架构。</span><span class="sxs-lookup"><span data-stu-id="c28af-127">Describes how to generate the schema for the subject area and staging area databases.</span></span>|  
|[<span data-ttu-id="c28af-128">了解数据库架构</span><span class="sxs-lookup"><span data-stu-id="c28af-128">Understanding the Database Schemas</span></span>](understanding-the-database-schemas.md)|<span data-ttu-id="c28af-129">介绍为主题区域数据库和临时区域数据库生成的架构。</span><span class="sxs-lookup"><span data-stu-id="c28af-129">Describes the schema that is generated for the subject area and staging area databases.</span></span>|  
|[<span data-ttu-id="c28af-130">了解增量生成</span><span class="sxs-lookup"><span data-stu-id="c28af-130">Understanding Incremental Generation</span></span>](understanding-incremental-generation.md)|<span data-ttu-id="c28af-131">介绍架构生成向导的增量式生成功能。</span><span class="sxs-lookup"><span data-stu-id="c28af-131">Describes the incremental generation capabilities of the Schema Generation Wizard.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c28af-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c28af-132">See Also</span></span>  
 <span data-ttu-id="c28af-133">[多维模型中的数据源视图](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="c28af-133">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="c28af-134">[多维模型中的数据源](data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="c28af-134">[Data Sources in Multidimensional Models](data-sources-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="c28af-135">支持 &#40;SSAS 多维&#41;的数据源</span><span class="sxs-lookup"><span data-stu-id="c28af-135">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](supported-data-sources-ssas-multidimensional.md)  
  
  
