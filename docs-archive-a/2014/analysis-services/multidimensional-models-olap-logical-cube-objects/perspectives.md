---
title: 透视 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- ready-only cube view
- OLAP objects [Analysis Services], perspectives
- storing data [Analysis Services], perspectives
- perspectives [Analysis Services]
- cubes [Analysis Services], perspectives
- visibility [Analysis Services]
- storage [Analysis Services], perspectives
ms.assetid: b064171e-b1b4-4f32-95e5-59e1b831c4c9
author: minewiskan
ms.author: owend
ms.openlocfilehash: f385fd078500739d97394cd8856fc8bd6a3b87e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690189"
---
# <a name="perspectives"></a><span data-ttu-id="d00a5-102">透视</span><span class="sxs-lookup"><span data-stu-id="d00a5-102">Perspectives</span></span>
  <span data-ttu-id="d00a5-103">透视是一种定义，允许用户以一种更简单的方式查看多维数据集。</span><span class="sxs-lookup"><span data-stu-id="d00a5-103">A perspective is a definition that allows users to see a cube in a simpler way.</span></span> <span data-ttu-id="d00a5-104">透视是多维数据集功能的子集。</span><span class="sxs-lookup"><span data-stu-id="d00a5-104">A perspective is a subset of the features of a cube.</span></span> <span data-ttu-id="d00a5-105">管理员使用透视可以创建多维数据集的视图，从而帮助用户将注意力集中在与他们关系最为密切的数据上。</span><span class="sxs-lookup"><span data-stu-id="d00a5-105">A perspective enables administrators to create views of a cube, helping users to focus on the most relevant data for them.</span></span> <span data-ttu-id="d00a5-106">透视包含多维数据集所有对象的子集。</span><span class="sxs-lookup"><span data-stu-id="d00a5-106">A perspective contains subsets of all objects from a cube.</span></span> <span data-ttu-id="d00a5-107">但它不能包含父多维数据集中未定义的元素。</span><span class="sxs-lookup"><span data-stu-id="d00a5-107">A perspective cannot include elements that are not defined in the parent cube.</span></span>  
  
 <span data-ttu-id="d00a5-108">简单 <xref:Microsoft.AnalysisServices.Perspective> 对象由基本信息、维度、度量值组、计算、KPI 和操作组成。</span><span class="sxs-lookup"><span data-stu-id="d00a5-108">A simple <xref:Microsoft.AnalysisServices.Perspective> object is composed of: basic information, dimensions, measure groups, calculations, KPIs, and actions.</span></span> <span data-ttu-id="d00a5-109">基本信息包括透视的名称和默认度量值。</span><span class="sxs-lookup"><span data-stu-id="d00a5-109">Basic information includes the name and the default measure of the perspective.</span></span> <span data-ttu-id="d00a5-110">维度是多维数据集维度的子集。</span><span class="sxs-lookup"><span data-stu-id="d00a5-110">The dimensions are a subset of the cube dimensions.</span></span> <span data-ttu-id="d00a5-111">度量值组是多维数据集度量值组的子集。</span><span class="sxs-lookup"><span data-stu-id="d00a5-111">The measure groups are a subset of the cube measure groups.</span></span> <span data-ttu-id="d00a5-112">计算是多维数据集计算的子集。</span><span class="sxs-lookup"><span data-stu-id="d00a5-112">The calculations are a subset of the cube calculations.</span></span> <span data-ttu-id="d00a5-113">KPI 是多维数据集 KPI 的子集。</span><span class="sxs-lookup"><span data-stu-id="d00a5-113">The KPIs are a subset of the cube KPIs.</span></span> <span data-ttu-id="d00a5-114">操作是多维数据集操作的子集。</span><span class="sxs-lookup"><span data-stu-id="d00a5-114">The actions are a subset of the cube actions.</span></span>  
  
 <span data-ttu-id="d00a5-115">使用透视之前，必须先更新和处理多维数据集。</span><span class="sxs-lookup"><span data-stu-id="d00a5-115">A cube has to be updated and processed before the perspective can be used.</span></span>  
  
 <span data-ttu-id="d00a5-116">多维数据集可能是非常复杂的对象，供用户浏览 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d00a5-116">Cubes can be very complex objects for users to explore in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="d00a5-117">单个多维数据集可以表示完整的数据仓库内容，一个多维数据集中可以有多个度量值组，以表示基于多个维度表的多个事实数据表和多个维度。</span><span class="sxs-lookup"><span data-stu-id="d00a5-117">A single cube can represent the contents of a complete data warehouse, with multiple measure groups in a cube representing multiple fact tables, and multiple dimensions based on multiple dimension tables.</span></span> <span data-ttu-id="d00a5-118">此类多维数据集可能非常复杂并且功能强大，但用户可能只需要与多维数据集的一小部分进行交互即可满足其商业智能和报表要求，因此这样的多维数据集会令用户感到过于复杂。</span><span class="sxs-lookup"><span data-stu-id="d00a5-118">Such a cube can be very complex and powerful, but daunting to users who may only need to interact with a small part of the cube in order to satisfy their business intelligence and reporting requirements.</span></span>  
  
 <span data-ttu-id="d00a5-119">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，您可以使用透视来减小中多维数据集的感知复杂性 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d00a5-119">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use a perspective to reduce the perceived complexity of a cube in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="d00a5-120">透视可定义多维数据集的可查看子集，借此您可以将注意力集中在多维数据集中的特定业务或特定应用程序上。</span><span class="sxs-lookup"><span data-stu-id="d00a5-120">A perspective defines a viewable subset of a cube that provides focused, business-specific or application-specific viewpoints on the cube.</span></span> <span data-ttu-id="d00a5-121">透视可控制多维数据集所包含对象的可见性。</span><span class="sxs-lookup"><span data-stu-id="d00a5-121">The perspective controls the visibility of objects that are contained by a cube.</span></span> <span data-ttu-id="d00a5-122">可在透视中显示或隐藏以下对象：</span><span class="sxs-lookup"><span data-stu-id="d00a5-122">The following objects can be displayed or hidden in a perspective:</span></span>  
  
-   <span data-ttu-id="d00a5-123">维度</span><span class="sxs-lookup"><span data-stu-id="d00a5-123">Dimensions</span></span>  
  
-   <span data-ttu-id="d00a5-124">属性</span><span class="sxs-lookup"><span data-stu-id="d00a5-124">Attributes</span></span>  
  
-   <span data-ttu-id="d00a5-125">层次结构</span><span class="sxs-lookup"><span data-stu-id="d00a5-125">Hierarchies</span></span>  
  
-   <span data-ttu-id="d00a5-126">度量值组</span><span class="sxs-lookup"><span data-stu-id="d00a5-126">Measure groups</span></span>  
  
-   <span data-ttu-id="d00a5-127">度量值</span><span class="sxs-lookup"><span data-stu-id="d00a5-127">Measures</span></span>  
  
-   <span data-ttu-id="d00a5-128">关键绩效指标 (KPI)</span><span class="sxs-lookup"><span data-stu-id="d00a5-128">Key Performance Indicators (KPIs)</span></span>  
  
-   <span data-ttu-id="d00a5-129">计算（计算成员、命名集和脚本命令）</span><span class="sxs-lookup"><span data-stu-id="d00a5-129">Calculations (calculated members, named sets, and script commands)</span></span>  
  
-   <span data-ttu-id="d00a5-130">操作</span><span class="sxs-lookup"><span data-stu-id="d00a5-130">Actions</span></span>  
  
 <span data-ttu-id="d00a5-131">例如，示例数据库中的**艾德工作**多维数据集 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 包含十一个度量值组和二十个不同的多维数据集维度，表示销售、销售预测和财务数据。</span><span class="sxs-lookup"><span data-stu-id="d00a5-131">For example, the **Adventure Works** cube in the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database contains eleven measure groups and twenty-one different cube dimensions, representing sales, sales forecasting, and financial data.</span></span> <span data-ttu-id="d00a5-132">客户端应用程序可以直接引用完整的多维数据集，但如果用户试图提取基本销售预期信息，则这一点可能颇具吸引力。</span><span class="sxs-lookup"><span data-stu-id="d00a5-132">A client application can directly reference the complete cube, but this viewpoint may be overwhelming to a user trying to extract basic sales forecasting information.</span></span> <span data-ttu-id="d00a5-133">相反，同一用户可以使用 "**销售目标**" 透视将 "**艾德公司**" 多维数据集的视图仅限制为与销售预测相关的对象。</span><span class="sxs-lookup"><span data-stu-id="d00a5-133">Instead, the same user can use the **Sales Targets** perspective to limit the view of the **Adventure Works** cube to only those objects relevant to sales forecasting.</span></span>  
  
 <span data-ttu-id="d00a5-134">多维数据集中通过透视对用户隐藏的对象仍可以使用 XML for Analysis (XMLA)、多维表达式 (MDX) 或数据挖掘扩展插件 (DMX) 语句直接进行引用和检索。</span><span class="sxs-lookup"><span data-stu-id="d00a5-134">Objects in a cube that are not visible to the user through a perspective can still be directly referenced and retrieved using XML for Analysis (XMLA), Multidimensional Expressions (MDX), or Data Mining Extensions (DMX) statements.</span></span> <span data-ttu-id="d00a5-135">透视不会限制对多维数据集中对象的访问，而且也不应以此方式进行使用，相反，应使用透视来为访问多维数据集的用户提供更好的体验。</span><span class="sxs-lookup"><span data-stu-id="d00a5-135">Perspectives do not restrict access to objects in a cube and should not be used as such; instead, perspectives are used to provide a better user experience while accessing a cube.</span></span>  
  
 <span data-ttu-id="d00a5-136">透视是多维数据集的只读视图；无法使用透视来重命名或更改多维数据集中的对象。</span><span class="sxs-lookup"><span data-stu-id="d00a5-136">A perspective is a read-only view of the cube; objects in the cube cannot be renamed or changed by using a perspective.</span></span> <span data-ttu-id="d00a5-137">同样，也无法使用透视更改多维数据集的行为或功能（如可见总计的用法）。</span><span class="sxs-lookup"><span data-stu-id="d00a5-137">Similarly, the behavior or features of a cube, such as the use of visual totals, cannot be changed by using a perspective.</span></span>  
  
## <a name="security"></a><span data-ttu-id="d00a5-138">安全性</span><span class="sxs-lookup"><span data-stu-id="d00a5-138">Security</span></span>  
 <span data-ttu-id="d00a5-139">透视的用途不是为了作为一种安全机制，而是作为一个可在商业智能应用程序中为用户提供更好体验的工具。</span><span class="sxs-lookup"><span data-stu-id="d00a5-139">Perspectives are not meant to be used as a security mechanism, but as a tool for providing a better user experience in business intelligence applications.</span></span> <span data-ttu-id="d00a5-140">特定透视的所有安全性都从基础多维数据集继承。</span><span class="sxs-lookup"><span data-stu-id="d00a5-140">All security for a particular perspective is inherited from the underlying cube.</span></span> <span data-ttu-id="d00a5-141">例如，透视无法让用户访问该用户尚未拥有访问权的多维数据集中的对象。</span><span class="sxs-lookup"><span data-stu-id="d00a5-141">For example, perspectives cannot provide access to objects in a cube to which a user does not already have access.</span></span> <span data-ttu-id="d00a5-142">必须先解决多维数据集的安全性，然后才能通过透视访问多维数据集中的对象。</span><span class="sxs-lookup"><span data-stu-id="d00a5-142">- Security for the cube must be resolved before access to objects in the cube can be provided through a perspective.</span></span>  
  
  
