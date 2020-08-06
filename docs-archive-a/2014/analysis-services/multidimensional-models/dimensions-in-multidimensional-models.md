---
title: 多维模型中的维度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OLAP [Analysis Services], dimensions
- dimensions [Analysis Services], about dimensions
- OLAP objects [Analysis Services], dimensions
ms.assetid: 2b62b05c-00fd-4e60-b77f-f707ba83a19b
author: minewiskan
ms.author: owend
ms.openlocfilehash: b9e452453b80de3656abf62cdcd90519cf4a6c99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693536"
---
# <a name="dimensions-in-multidimensional-models"></a><span data-ttu-id="aae2f-102">多维模型中的维度</span><span class="sxs-lookup"><span data-stu-id="aae2f-102">Dimensions in Multidimensional Models</span></span>
  <span data-ttu-id="aae2f-103">数据库维度是相关对象（称为属性）的集合，用于提供有关一个或多个多维数据集中的事实数据的信息。</span><span class="sxs-lookup"><span data-stu-id="aae2f-103">A database dimension is a collection of related objects, called attributes, which can be used to provide information about fact data in one or more cubes.</span></span> <span data-ttu-id="aae2f-104">例如，产品维度中的典型属性可能是产品名称、产品类别、产品系列、产品规格和产品价格。</span><span class="sxs-lookup"><span data-stu-id="aae2f-104">For example, typical attributes in a product dimension might be product name, product category, product line, product size, and product price.</span></span> <span data-ttu-id="aae2f-105">这些对象绑定到数据源视图的一个或多个表中的一个或多个列。</span><span class="sxs-lookup"><span data-stu-id="aae2f-105">These objects are bound to one or more columns in one or more tables in a data source view.</span></span> <span data-ttu-id="aae2f-106">默认情况下，这些属性和属性层次结构一样是可见的，可用于了解多维数据集中的事实数据。</span><span class="sxs-lookup"><span data-stu-id="aae2f-106">By default, these attributes are visible as attribute hierarchies and can be used to understand the fact data in a cube.</span></span> <span data-ttu-id="aae2f-107">可以将属性组织为用户定义层次结构，从而提供导航路径以帮助用户浏览多维数据集中的数据。</span><span class="sxs-lookup"><span data-stu-id="aae2f-107">Attributes can be organized into user-defined hierarchies that provide navigational paths to assist users when browsing the data in a cube.</span></span>  
  
 <span data-ttu-id="aae2f-108">多维数据集包含用户分析事实数据所基于的所有维度。</span><span class="sxs-lookup"><span data-stu-id="aae2f-108">Cubes contain all the dimensions on which users base their analyses of fact data.</span></span> <span data-ttu-id="aae2f-109">多维数据集中的数据库维度实例称为多维数据集维度，它与多维数据集中的一个或多个度量值组有关。</span><span class="sxs-lookup"><span data-stu-id="aae2f-109">An instance of a database dimension in a cube is called a cube dimension and relates to one or more measure groups in the cube.</span></span> <span data-ttu-id="aae2f-110">数据库维度可以在多维数据集中多次使用。</span><span class="sxs-lookup"><span data-stu-id="aae2f-110">A database dimension can be used multiple times in a cube.</span></span> <span data-ttu-id="aae2f-111">例如，事实数据表可以具有多个与时间相关的事实数据，并且可以定义单独的多维数据集维度以帮助分析每个与时间相关的事实数据。</span><span class="sxs-lookup"><span data-stu-id="aae2f-111">For example, a fact table can have multiple time-related facts, and a separate cube dimension can be defined to assist in analyzing each time-related fact.</span></span> <span data-ttu-id="aae2f-112">但是，只需存在一个与时间相关的数据库维度，这也意味着只需存在一个与时间相关的关系数据库表便可支持多个基于时间的多维数据集维度。</span><span class="sxs-lookup"><span data-stu-id="aae2f-112">However, only one time-related database dimension needs to exist, which also means that only one time-related relational database table needs to exist to support multiple cube dimensions based on time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aae2f-113"> 有关与维度设计相关的性能问题，请参阅 [SQL Server 2008 R2 Analysis Services 性能指南](https://go.microsoft.com/fwlink/?LinkId=306717)。</span><span class="sxs-lookup"><span data-stu-id="aae2f-113">For performance issues related to dimension design, see the [SQL Server 2008 R2 Analysis Services Performance Guide](https://go.microsoft.com/fwlink/?LinkId=306717).</span></span>  
  
## <a name="defining-dimensions-attributes-and-hierarchies"></a><span data-ttu-id="aae2f-114">定义维度、属性和层次结构</span><span class="sxs-lookup"><span data-stu-id="aae2f-114">Defining Dimensions, Attributes, and Hierarchies</span></span>  
 <span data-ttu-id="aae2f-115">定义数据库和多维数据集的维度、属性和层次结构的最简单方法是使用多维数据集向导在定义多维数据集的同时创建维度。</span><span class="sxs-lookup"><span data-stu-id="aae2f-115">The simplest method for defining database and cube dimensions, attributes, and hierarchies is to use the Cube Wizard to create dimensions at the same time that you define the cube.</span></span> <span data-ttu-id="aae2f-116">多维数据集向导将根据向导在数据源视图中找到的维度表，或您在数据源视图中指定用于多维数据集的维度表来创建维度。</span><span class="sxs-lookup"><span data-stu-id="aae2f-116">The Cube Wizard will create dimensions based on the dimension tables in the data source view that the wizard identifies or that you specify for use in the cube.</span></span> <span data-ttu-id="aae2f-117">这样，该向导创建数据库维度并将其添加到新的多维数据集中，从而创建多维数据集维度。</span><span class="sxs-lookup"><span data-stu-id="aae2f-117">The wizard then creates the database dimensions and adds them to the new cube, creating cube dimensions.</span></span>  
  
 <span data-ttu-id="aae2f-118">创建多维数据集时，还可以将数据库中已存在的任何维度添加到新的多维数据集中。</span><span class="sxs-lookup"><span data-stu-id="aae2f-118">When you create a cube, you can also add to the new cube any dimensions that already exist in the database.</span></span> <span data-ttu-id="aae2f-119">这些维度可能在先前已针对其他多维数据集定义，或者已由维度向导定义。</span><span class="sxs-lookup"><span data-stu-id="aae2f-119">These dimensions may have been previously defined for another cube or by the Dimension Wizard.</span></span> <span data-ttu-id="aae2f-120">定义数据库维度后，您可以在“维度设计器”中修改并配置数据库维度。</span><span class="sxs-lookup"><span data-stu-id="aae2f-120">After a database dimension has been defined, you can modify and configure the database dimension in Dimension Designer.</span></span> <span data-ttu-id="aae2f-121">您还可以在“多维数据集设计器”中对多维数据集维度进行有限程度的自定义。</span><span class="sxs-lookup"><span data-stu-id="aae2f-121">You can also customize the cube dimension, to a limited extent, in Cube Designer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aae2f-122">您还可以使用 XMLA 或“分析管理对象”(AMO)，以编程方式来设计并配置维度、属性和层次结构。</span><span class="sxs-lookup"><span data-stu-id="aae2f-122">You can also design and configure dimensions, attributes, and hierarchies programmatically by using either XMLA or Analysis Management Objects (AMO).</span></span> <span data-ttu-id="aae2f-123">有关详细信息，请参阅[Analysis Services 脚本语言 &#40;ASSL&#41; 引用](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)并[通过分析管理对象 &#40;AMO&#41;进行开发](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)。</span><span class="sxs-lookup"><span data-stu-id="aae2f-123">For more information, see [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) and [Developing with Analysis Management Objects &#40;AMO&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aae2f-124">本节内容</span><span class="sxs-lookup"><span data-stu-id="aae2f-124">In This Section</span></span>  
 <span data-ttu-id="aae2f-125">下表对本部分的主题进行了说明：</span><span class="sxs-lookup"><span data-stu-id="aae2f-125">The following table describes the topics in this section.</span></span>  
  
 [<span data-ttu-id="aae2f-126">定义数据库维度</span><span class="sxs-lookup"><span data-stu-id="aae2f-126">Define Database Dimensions</span></span>](define-database-dimensions.md)  
 <span data-ttu-id="aae2f-127">说明如何使用维度设计器修改和配置数据库维度。</span><span class="sxs-lookup"><span data-stu-id="aae2f-127">Describes how to modify and configure a database dimension by using Dimension Designer.</span></span>  
  
 [<span data-ttu-id="aae2f-128">维度特性属性参考</span><span class="sxs-lookup"><span data-stu-id="aae2f-128">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
 <span data-ttu-id="aae2f-129">说明如何使用维度设计器定义、修改和配置数据库维度属性。</span><span class="sxs-lookup"><span data-stu-id="aae2f-129">Describes how to define, modify, and configure a database dimension attribute by using Dimension Designer.</span></span>  
  
 [<span data-ttu-id="aae2f-130">定义属性关系</span><span class="sxs-lookup"><span data-stu-id="aae2f-130">Define Attribute Relationships</span></span>](attribute-relationships-define.md)  
 <span data-ttu-id="aae2f-131">说明如何使用维度设计器定义、修改和配置属性关系。</span><span class="sxs-lookup"><span data-stu-id="aae2f-131">Describes how to define, modify, and configure an attribute relationship by using Dimension Designer.</span></span>  
  
 [<span data-ttu-id="aae2f-132">创建用户定义层次结构</span><span class="sxs-lookup"><span data-stu-id="aae2f-132">Create User-Defined Hierarchies</span></span>](user-defined-hierarchies-create.md)  
 <span data-ttu-id="aae2f-133">说明如何使用“维度设计器”定义、修改和配置维度属性的用户定义层次结构。</span><span class="sxs-lookup"><span data-stu-id="aae2f-133">Describes how to define, modify, and configure a user-defined hierarchy of dimension attributes by using Dimension Designer.</span></span>  
  
 [<span data-ttu-id="aae2f-134">使用商业智能向导增强维度</span><span class="sxs-lookup"><span data-stu-id="aae2f-134">Use the Business Intelligence Wizard to Enhance Dimensions</span></span>](../use-the-business-intelligence-wizard-to-enhance-dimensions.md)  
 <span data-ttu-id="aae2f-135">说明如何使用商业智能向导增强数据库维度。</span><span class="sxs-lookup"><span data-stu-id="aae2f-135">Describes how to enhance a database dimension by using the Business Intelligence Wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aae2f-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aae2f-136">See Also</span></span>  
 [<span data-ttu-id="aae2f-137">多维模型中的多维数据集</span><span class="sxs-lookup"><span data-stu-id="aae2f-137">Cubes in Multidimensional Models</span></span>](cubes-in-multidimensional-models.md)  
  
  
