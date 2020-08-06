---
title: 定义数据库维度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], defining
ms.assetid: fe84588b-66a3-4100-a1cf-59b21b7adf01
author: minewiskan
ms.author: owend
ms.openlocfilehash: ad5334e71b0f133f80933a7d1702d8ada7565501
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687288"
---
# <a name="define-database-dimensions"></a><span data-ttu-id="c351f-102">定义数据库维度</span><span class="sxs-lookup"><span data-stu-id="c351f-102">Define Database Dimensions</span></span>
  <span data-ttu-id="c351f-103">使用中的维度设计器 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 可在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目或数据库中配置现有数据库维度。</span><span class="sxs-lookup"><span data-stu-id="c351f-103">Use Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to configure an existing database dimension in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span> <span data-ttu-id="c351f-104">可以使用维度设计器执行下列任务：</span><span class="sxs-lookup"><span data-stu-id="c351f-104">You can use Dimension Designer to do the following:</span></span>  
  
-   <span data-ttu-id="c351f-105">配置维度级别属性。</span><span class="sxs-lookup"><span data-stu-id="c351f-105">Configure the dimension-level properties.</span></span>  
  
-   <span data-ttu-id="c351f-106">添加和配置维度特性。</span><span class="sxs-lookup"><span data-stu-id="c351f-106">Add and configure dimension attributes.</span></span>  
  
-   <span data-ttu-id="c351f-107">定义和配置用户定义层次结构。</span><span class="sxs-lookup"><span data-stu-id="c351f-107">Define and configure user-defined hierarchies.</span></span>  
  
-   <span data-ttu-id="c351f-108">定义和配置特性之间的关系。</span><span class="sxs-lookup"><span data-stu-id="c351f-108">Define and configure relationships between attributes.</span></span>  
  
-   <span data-ttu-id="c351f-109">定义维度翻译。</span><span class="sxs-lookup"><span data-stu-id="c351f-109">Define dimension translations.</span></span>  
  
-   <span data-ttu-id="c351f-110">对于已处理的维度，您可以浏览维度结构并查看数据。</span><span class="sxs-lookup"><span data-stu-id="c351f-110">For processed dimensions, you can browse the dimension structure and view data.</span></span>  
  
 <span data-ttu-id="c351f-111">修改维度、属性或层次结构后，必须处理该维度才能查看更改。</span><span class="sxs-lookup"><span data-stu-id="c351f-111">After you modify a dimension, attribute, or hierarchy, you must process that dimension to view the changes.</span></span> <span data-ttu-id="c351f-112">在项目模式下工作时，应在开始处理前部署对 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例的更改。</span><span class="sxs-lookup"><span data-stu-id="c351f-112">When working in project mode, you deploy the changes to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance before processing.</span></span>  
  
 <span data-ttu-id="c351f-113">有关如何在维度设计器中打开维度的详细信息，请参阅 [在解决方案资源管理器中修改或删除数据库维度](database-dimensions-modify-or-delete-a-database-dimension-in-solution-explorer.md)。</span><span class="sxs-lookup"><span data-stu-id="c351f-113">For more information about how to open a dimension in Dimension Designer, see [Modify or Delete a Database Dimension in Solution Explorer](database-dimensions-modify-or-delete-a-database-dimension-in-solution-explorer.md).</span></span>  
  
 <span data-ttu-id="c351f-114">维度设计器中有三个不同的选项卡，下表对这些选项卡进行了说明。</span><span class="sxs-lookup"><span data-stu-id="c351f-114">Dimension Designer has three different tabs, which are described in the following table.</span></span>  
  
|<span data-ttu-id="c351f-115">选项卡</span><span class="sxs-lookup"><span data-stu-id="c351f-115">Tab</span></span>|<span data-ttu-id="c351f-116">说明</span><span class="sxs-lookup"><span data-stu-id="c351f-116">Description</span></span>|  
|---------|-----------------|  
|<span data-ttu-id="c351f-117">**维度结构**</span><span class="sxs-lookup"><span data-stu-id="c351f-117">**Dimension Structure**</span></span>|<span data-ttu-id="c351f-118">使用此选项卡可以处理维度的结构，以检查或创建维度的数据源视图架构，使用属性以及组织用户定义层次结构中的属性。</span><span class="sxs-lookup"><span data-stu-id="c351f-118">Use this tab to work with the structure of a dimension-to examine or create the data source view schema for a dimension, to work with attributes, and to organize attributes in user-defined hierarchies.</span></span>|  
|<span data-ttu-id="c351f-119">**的维度设计器中，可以在“维度结构”视图的**</span><span class="sxs-lookup"><span data-stu-id="c351f-119">**Attribute Relationships**</span></span>|<span data-ttu-id="c351f-120">使用此选项卡可以创建、修改或删除维度的属性关系。</span><span class="sxs-lookup"><span data-stu-id="c351f-120">Use this tab to create, modify, or delete the attribute relationships of a dimension.</span></span>|  
|<span data-ttu-id="c351f-121">**翻译**</span><span class="sxs-lookup"><span data-stu-id="c351f-121">**Translations**</span></span>|<span data-ttu-id="c351f-122">使用此选项卡可以不同的语言添加和编辑维度元数据的翻译。</span><span class="sxs-lookup"><span data-stu-id="c351f-122">Use this tab to add and edit translations of dimension metadata in different languages.</span></span>|  
|<span data-ttu-id="c351f-123">**浏览器**</span><span class="sxs-lookup"><span data-stu-id="c351f-123">**Browser**</span></span>|<span data-ttu-id="c351f-124">使用此选项卡可检查已处理维度的成员和审查维度元数据的翻译。</span><span class="sxs-lookup"><span data-stu-id="c351f-124">Use this tab to examine the members of a processed dimension and to review translations of dimension metadata.</span></span>|  
  
 <span data-ttu-id="c351f-125">以下主题介绍了您可以在维度设计器中执行的任务。</span><span class="sxs-lookup"><span data-stu-id="c351f-125">The following topics describe the tasks that you can perform in Dimension Designer.</span></span>  
  
 [<span data-ttu-id="c351f-126">维度特性属性参考</span><span class="sxs-lookup"><span data-stu-id="c351f-126">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
 <span data-ttu-id="c351f-127">说明如何定义和配置维度属性。</span><span class="sxs-lookup"><span data-stu-id="c351f-127">Describes how to define and configure a dimension attribute.</span></span>  
  
 [<span data-ttu-id="c351f-128">创建用户定义层次结构</span><span class="sxs-lookup"><span data-stu-id="c351f-128">Create User-Defined Hierarchies</span></span>](user-defined-hierarchies-create.md)  
 <span data-ttu-id="c351f-129">说明如何定义和配置用户定义层次结构。</span><span class="sxs-lookup"><span data-stu-id="c351f-129">Describes how to define and configure a user-defined hierarchy.</span></span>  
  
 [<span data-ttu-id="c351f-130">定义属性关系</span><span class="sxs-lookup"><span data-stu-id="c351f-130">Define Attribute Relationships</span></span>](attribute-relationships-define.md)  
 <span data-ttu-id="c351f-131">说明如何定义和配置属性关系。</span><span class="sxs-lookup"><span data-stu-id="c351f-131">Describes how to define and configure an attribute relationship.</span></span>  
  
 [<span data-ttu-id="c351f-132">使用商业智能向导增强维度</span><span class="sxs-lookup"><span data-stu-id="c351f-132">Use the Business Intelligence Wizard to Enhance Dimensions</span></span>](../use-the-business-intelligence-wizard-to-enhance-dimensions.md)  
 <span data-ttu-id="c351f-133">说明如何使用商业智能向导增强维度。</span><span class="sxs-lookup"><span data-stu-id="c351f-133">Describes how to use the Business Intelligence Wizard to enhance a dimension.</span></span>  
  
  
