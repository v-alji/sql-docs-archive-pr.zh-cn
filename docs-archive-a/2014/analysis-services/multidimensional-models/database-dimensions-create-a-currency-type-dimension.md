---
title: 创建货币类型维度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], currency
- currency [Analysis Services]
- converting currency
- currency dimensions [Analysis Services]
ms.assetid: b1f037d1-ce47-4e47-a1c2-5ec9e781cff6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 91123fb5fda898e90056057114295335fbd1d32c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689072"
---
# <a name="create-a-currency-type-dimension"></a><span data-ttu-id="1bca4-102">创建货币类型维度</span><span class="sxs-lookup"><span data-stu-id="1bca4-102">Create a Currency type Dimension</span></span>
  <span data-ttu-id="1bca4-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，货币类型维度是指其属性表示用于财务报表的货币列表的维度。</span><span class="sxs-lookup"><span data-stu-id="1bca4-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], a currency type dimension is a dimension whose attributes represent a list of currencies for financial reporting purposes.</span></span>  
  
 <span data-ttu-id="1bca4-104">通过货币维度，您可以为 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中的多维数据集添加货币换算功能。</span><span class="sxs-lookup"><span data-stu-id="1bca4-104">A currency dimension lets you add currency conversion capabilities to a cube in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="1bca4-105">若要为多维数据集添加货币换算功能，请使用商业智能向导定义一个多维表达式 (MDX) 脚本命令，该命令可将货币度量值换算为适用于客户端应用程序区域设置的值。</span><span class="sxs-lookup"><span data-stu-id="1bca4-105">To add currency conversion to a cube, you use the Business Intelligence Wizard define a Multidimensional Expressions (MDX) script command that converts currency measures to values that are appropriate for the locale of the client application.</span></span> <span data-ttu-id="1bca4-106">若要创建此 MDX 脚本，商业智能向导需要以下信息：</span><span class="sxs-lookup"><span data-stu-id="1bca4-106">To create this MDX script, the Business Intelligence Wizard needs the following information:</span></span>  
  
-   <span data-ttu-id="1bca4-107">表示源货币的货币维度。</span><span class="sxs-lookup"><span data-stu-id="1bca4-107">A currency dimension that represents source currencies.</span></span> <span data-ttu-id="1bca4-108">（此维度为源货币维度。）</span><span class="sxs-lookup"><span data-stu-id="1bca4-108">(This dimension is the source currency dimension.)</span></span>  
  
-   <span data-ttu-id="1bca4-109">表示要使用的汇率的度量值组。</span><span class="sxs-lookup"><span data-stu-id="1bca4-109">A measure group that represents the exchange rates that will be used.</span></span>  
  
 <span data-ttu-id="1bca4-110">商业智能向导将根据此信息设计货币换算进程，该进程可以标识相应的目标货币维度（表示目标货币的货币维度）。</span><span class="sxs-lookup"><span data-stu-id="1bca4-110">From this information, the Business Intelligence Wizard will design a currency conversion process that identifies the appropriate destination currency dimension (the currency dimension that represents destination currencies).</span></span> <span data-ttu-id="1bca4-111">根据商业智能解决方案需要的货币换算的数量，商业智能向导可以定义多个目标货币维度。</span><span class="sxs-lookup"><span data-stu-id="1bca4-111">Depending on the number of currency conversions that your business intelligence solution requires, the Business Intelligence Wizard can define multiple destination currency dimensions.</span></span> <span data-ttu-id="1bca4-112">有关定义货币换算的详细信息，请参阅[货币换算 (Analysis Services)](../currency-conversions-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1bca4-112">For more information about defining currency conversions, see [Currency Conversions &#40;Analysis Services&#41;](../currency-conversions-analysis-services.md).</span></span>  
  
 <span data-ttu-id="1bca4-113">若要将某个维度标识为货币维度，请将该维度的 `Type` 属性设置为 `Currency`。</span><span class="sxs-lookup"><span data-stu-id="1bca4-113">To identify a dimension as a currency dimension, set the `Type` property of the dimension to `Currency`.</span></span>  
  
## <a name="dimension-structure"></a><span data-ttu-id="1bca4-114">维度结构</span><span class="sxs-lookup"><span data-stu-id="1bca4-114">Dimension Structure</span></span>  
 <span data-ttu-id="1bca4-115">一个货币维度必须在货币维度的维度表中至少包含一个用于标识单个货币的键特性。</span><span class="sxs-lookup"><span data-stu-id="1bca4-115">A currency dimension contains, at least, a key attribute identifying individual currencies in the dimension table for the currency dimension.</span></span> <span data-ttu-id="1bca4-116">源货币维度和目标货币维度中的键特性的值不相同：</span><span class="sxs-lookup"><span data-stu-id="1bca4-116">The value of the key attribute is different in both source and destination currency dimensions:</span></span>  
  
-   <span data-ttu-id="1bca4-117">若要将某个特性标识为源货币维度的键特性，请将该特性的 `Type` 属性设置为 `CurrencySource`。</span><span class="sxs-lookup"><span data-stu-id="1bca4-117">To identify an attribute as the key attribute of a source currency dimension, set the `Type` property of the attribute to `CurrencySource`.</span></span>  
  
-   <span data-ttu-id="1bca4-118">若要将某个特性标识为目标货币维度，请将该特性的 `Type` 属性设置为 `CurrencyDestination`。</span><span class="sxs-lookup"><span data-stu-id="1bca4-118">To identify an attribute as the destination currency dimension, set the `Type` property of the attribute to `CurrencyDestination`.</span></span>  
  
 <span data-ttu-id="1bca4-119">用于报表时，源货币维度和目标货币维度都可以包含以下特性（可选）：</span><span class="sxs-lookup"><span data-stu-id="1bca4-119">For reporting purposes, both source and destination currency dimensions can optionally contain the following attributes:</span></span>  
  
-   <span data-ttu-id="1bca4-120">货币名称特性。</span><span class="sxs-lookup"><span data-stu-id="1bca4-120">A currency name attribute.</span></span>  
  
     <span data-ttu-id="1bca4-121">若要将某个特性标识为货币名称特性，请将该特性的 `Type` 属性设置为 `CurrencyName`。</span><span class="sxs-lookup"><span data-stu-id="1bca4-121">To identify an attribute as a currency name attribute, set the `Type` property of the attribute to `CurrencyName`.</span></span>  
  
-   <span data-ttu-id="1bca4-122">货币源特性。</span><span class="sxs-lookup"><span data-stu-id="1bca4-122">A currency source attribute.</span></span>  
  
     <span data-ttu-id="1bca4-123">若要将某个特性标识为货币源特性，请将该特性的 `Type` 属性设置为 `CurrencySource`。</span><span class="sxs-lookup"><span data-stu-id="1bca4-123">To identify an attribute as a currency source attribute, set the `Type` property of the attribute to `CurrencySource`.</span></span>  
  
-   <span data-ttu-id="1bca4-124">货币的国际标准组织 (ISO) 代码。</span><span class="sxs-lookup"><span data-stu-id="1bca4-124">A currency International Standards Organization (ISO) code.</span></span>  
  
     <span data-ttu-id="1bca4-125">若要将某个特性标识为货币的 ISO 代码特性，请将该特性的 `Type` 属性设置为 `CurrencyIsoCode`。</span><span class="sxs-lookup"><span data-stu-id="1bca4-125">To identify an attribute as a currency ISO code attribute, set the `Type` property of the attribute to `CurrencyIsoCode`.</span></span>  
  
 <span data-ttu-id="1bca4-126">有关属性类型的详细信息，请参阅 [配置属性类型](attribute-properties-configure-attribute-types.md)。</span><span class="sxs-lookup"><span data-stu-id="1bca4-126">For more information about attribute types, see [Configure Attribute Types](attribute-properties-configure-attribute-types.md).</span></span>  
  
## <a name="defining-account-intelligence-with-the-business-intelligence-wizard"></a><span data-ttu-id="1bca4-127">通过商业智能向导定义帐户智能</span><span class="sxs-lookup"><span data-stu-id="1bca4-127">Defining Account Intelligence with the Business Intelligence Wizard</span></span>  
 <span data-ttu-id="1bca4-128">如果定义了帐户维度并将该维度添加到了多维数据集中，则可以使用商业智能向导来为维度添加帐户智能功能（如标识和映射帐户类型）。</span><span class="sxs-lookup"><span data-stu-id="1bca4-128">After you have defined an account dimension and added that dimension to a cube, you can use the Business Intelligence Wizard to add account intelligence functionality, such as identifying and mapping account types, to the dimension.</span></span> <span data-ttu-id="1bca4-129">有关详细信息，请参阅 [向维度中添加帐户智能](bi-wizard-add-account-intelligence-to-a-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="1bca4-129">For more information, see [Add Account Intelligence to a Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bca4-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1bca4-130">See Also</span></span>  
 <span data-ttu-id="1bca4-131">[属性和属性层次结构](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="1bca4-131">[Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span></span>  
 <span data-ttu-id="1bca4-132">[商业智能向导的 F1 帮助](../business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="1bca4-132">[Business Intelligence Wizard F1 Help](../business-intelligence-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="1bca4-133">维度类型</span><span class="sxs-lookup"><span data-stu-id="1bca4-133">Dimension Types</span></span>](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  
