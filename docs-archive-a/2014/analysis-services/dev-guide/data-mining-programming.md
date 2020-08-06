---
title: 数据挖掘编程 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- data mining [Analysis Services], developer's guide
ms.assetid: 9fd77b16-0b89-44ce-bcf1-7c04b62499da
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd4bd48b5914d5fda89f94c0a959e670ffec3321
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687332"
---
# <a name="data-mining-programming"></a><span data-ttu-id="33842-102">数据挖掘编程</span><span class="sxs-lookup"><span data-stu-id="33842-102">Data Mining Programming</span></span>
  <span data-ttu-id="33842-103">如果您觉得 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的内置工具和查看器不符合您的要求，您可以编写自己的扩展插件代码来扩展 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的功能。</span><span class="sxs-lookup"><span data-stu-id="33842-103">If you find that the built-in tools and viewers in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] do not meet your requirements, you can extend the power of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] by coding your own extensions.</span></span> <span data-ttu-id="33842-104">如果采用这种方法，您有两种选择：</span><span class="sxs-lookup"><span data-stu-id="33842-104">In this approach, you have two options:</span></span>  
  
-   <span data-ttu-id="33842-105">**XMLA**</span><span class="sxs-lookup"><span data-stu-id="33842-105">**XMLA**</span></span>  
  
     [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="33842-106">[!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]支持 XML for Analysis (XMLA) 作为协议以便与客户端应用程序进行通信。</span><span class="sxs-lookup"><span data-stu-id="33842-106">[!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] supports XML for Analysis (XMLA) as a protocol for communication with client applications.</span></span> <span data-ttu-id="33842-107">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 还支持其他扩展了 XML for Analysis 规范的命令。</span><span class="sxs-lookup"><span data-stu-id="33842-107">Additional commands are supported by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that extend the XML for Analysis specification.</span></span>  
  
     <span data-ttu-id="33842-108">由于 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将 XMLA 用于数据定义、数据操作和数据控制支持，因此您可以使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 提供的可视化工具创建挖掘结构和挖掘模型，然后扩展已使用数据挖掘扩展插件 (DMX) 和 Analysis Services 脚本语言 (ASSL) 脚本创建的数据挖掘对象。</span><span class="sxs-lookup"><span data-stu-id="33842-108">Because [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses XMLA for data definition, data manipulation, and data control support, you can create mining structures and mining models by using the visual tools provided by [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], and then extend the data mining objects that you have created by using Data Mining Extensions (DMX) and Analysis Services Scripting Language (ASSL) scripts.</span></span>  
  
     <span data-ttu-id="33842-109">您可以创建和修改 XMLA 脚本中的全部数据挖掘对象，并以编程方式从您自己的应用程序对模型运行预测查询。</span><span class="sxs-lookup"><span data-stu-id="33842-109">You can create and modify data mining objects entirely in XMLA scripts, and run prediction queries against the models programmatically from your own applications.</span></span>  
  
-   <span data-ttu-id="33842-110">**分析管理对象 (AMO)**</span><span class="sxs-lookup"><span data-stu-id="33842-110">**Analysis Management Objects (AMO)**</span></span>  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="33842-111">还提供了一个完整的框架，该框架使第三方数据挖掘访问接口能够将数据挖掘对象集成到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="33842-111">also provides a complete framework that enables third-party data mining providers to integrate the data mining objects into [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="33842-112">可以使用 AMO 创建挖掘结构和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="33842-112">You can create mining structures and mining models by using AMO.</span></span> <span data-ttu-id="33842-113">在 CodePlex 中查看以下示例：</span><span class="sxs-lookup"><span data-stu-id="33842-113">See the following samples in CodePlex:</span></span>  
  
    -   <span data-ttu-id="33842-114">AMO 浏览器</span><span class="sxs-lookup"><span data-stu-id="33842-114">AMO Browser</span></span>  
  
         <span data-ttu-id="33842-115">连接到您指定的 SSAS 实例，并列出所有服务器对象及其属性（包括挖掘结构和挖掘模型）。</span><span class="sxs-lookup"><span data-stu-id="33842-115">Connects to the SSAS instance you specify and lists all server objects and their properties, including mining structure and mining models.</span></span>  
  
    -   <span data-ttu-id="33842-116">AMO 简单示例</span><span class="sxs-lookup"><span data-stu-id="33842-116">AMO Simple Sample</span></span>  
  
         <span data-ttu-id="33842-117">AS 简单示例涉及对大多数主要对象的编程访问，并演示元数据浏览以及对象中的值的访问。</span><span class="sxs-lookup"><span data-stu-id="33842-117">The AS Simple Sample covers programmatic access to most major objects, and demonstrates metadata browsing, and access to the values in objects.</span></span>  
  
         <span data-ttu-id="33842-118">该示例还演示如何创建和处理数据挖掘结构和模型，以及浏览现有数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="33842-118">The sample also demonstrates how to create and process a data mining structure and model, as well as browse an existing data mining model.</span></span>  
  
-   <span data-ttu-id="33842-119">**DMX**</span><span class="sxs-lookup"><span data-stu-id="33842-119">**DMX**</span></span>  
  
     <span data-ttu-id="33842-120">您可以使用 DMX 封装命令语句、预测查询和元数据查询并以表格格式返回结果（假定您创建了与 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务器的连接）。</span><span class="sxs-lookup"><span data-stu-id="33842-120">You can use DMX to encapsulate command statements, prediction queries, and metadata queries and return results in a tabular format, assuming you have created a connection to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="33842-121">本节内容</span><span class="sxs-lookup"><span data-stu-id="33842-121">In This Section</span></span>  
 [<span data-ttu-id="33842-122">OLE DB for Data Mining</span><span class="sxs-lookup"><span data-stu-id="33842-122">OLE DB for Data Mining</span></span>](../../../2014/analysis-services/dev-guide/ole-db-for-data-mining.md)  
 <span data-ttu-id="33842-123">介绍在支持数据挖掘和多维数据方面对规范的扩展：新的架构行集和列，以及用于创建和管理挖掘结构的数据挖掘扩展插件 (DMX) 语言。</span><span class="sxs-lookup"><span data-stu-id="33842-123">Describes additions to the specification to support data mining and multidimensional data: new schema rowsets and columns, Data Mining Extensions (DMX) language for creating and managing mining structures.</span></span>  
  
## <a name="related-reference"></a><span data-ttu-id="33842-124">相关参考</span><span class="sxs-lookup"><span data-stu-id="33842-124">Related Reference</span></span>  
 [<span data-ttu-id="33842-125">使用 ADOMD.NET 进行开发</span><span class="sxs-lookup"><span data-stu-id="33842-125">Developing with ADOMD.NET</span></span>](https://docs.microsoft.com/bi-reference/adomd/developing-with-adomd-net)  
 <span data-ttu-id="33842-126">介绍 ADOMD.NET 客户端和服务器编程对象。</span><span class="sxs-lookup"><span data-stu-id="33842-126">Introduces ADOMD.NET client and server programming objects.</span></span>  
  
 [<span data-ttu-id="33842-127">使用分析管理对象 (AMO) 进行开发</span><span class="sxs-lookup"><span data-stu-id="33842-127">Developing with Analysis Management Objects &#40;AMO&#41;</span></span>](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)  
 <span data-ttu-id="33842-128">介绍 AMO 编程库。</span><span class="sxs-lookup"><span data-stu-id="33842-128">Introduces the AMO programming library.</span></span>  
  
 [<span data-ttu-id="33842-129">使用 Analysis Services 脚本语言 (ASSL) 开发</span><span class="sxs-lookup"><span data-stu-id="33842-129">Developing with Analysis Services Scripting Language &#40;ASSL&#41;</span></span>](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
 <span data-ttu-id="33842-130">介绍 XML for Analysis (XMLA) 及其扩展插件。</span><span class="sxs-lookup"><span data-stu-id="33842-130">Introduces XML for Analysis (XMLA) and its extensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33842-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="33842-131">See Also</span></span>  
 <span data-ttu-id="33842-132">[开发人员指南 &#40;Analysis Services&#41;](../analysis-services-developer-documentation.md) </span><span class="sxs-lookup"><span data-stu-id="33842-132">[Developer's Guide &#40;Analysis Services&#41;](../analysis-services-developer-documentation.md) </span></span>  
 [<span data-ttu-id="33842-133">数据挖掘扩展插件 (DMX) 参考</span><span class="sxs-lookup"><span data-stu-id="33842-133">Data Mining Extensions &#40;DMX&#41; Reference</span></span>](/sql/dmx/data-mining-extensions-dmx-reference)  
  
  
