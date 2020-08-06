---
title: 表格模型编程 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 0ceb461e-12c1-44ea-97ac-b99bf308676b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2565ed28a882750ab9b37beadbce698d3a0abb19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694577"
---
# <a name="tabular-model-programming"></a><span data-ttu-id="05ce0-102">表格模型编程</span><span class="sxs-lookup"><span data-stu-id="05ce0-102">Tabular Model Programming</span></span>
  <span data-ttu-id="05ce0-103">表格模型使用关系构造对分析和报表应用程序使用的 Analysis Services 数据建模。</span><span class="sxs-lookup"><span data-stu-id="05ce0-103">Tabular models use relational constructs to model the Analysis Services data used by analytical and reporting applications.</span></span> <span data-ttu-id="05ce0-104">这些模型运行在配置用于表格模式的 Analysis Service 实例上，使用内存中分析引擎执行存储和快速表扫描（支持在请求数据时对其进行聚合和计算）。</span><span class="sxs-lookup"><span data-stu-id="05ce0-104">These models run on an Analysis Service instance that is configured for tabular mode, using an in-memory analytics engine for storage and fast table scans that aggregate and calculate data as it is requested.</span></span>  
  
 <span data-ttu-id="05ce0-105">从编程角度来看，您在 AMO、ADOMD.NET、XMLA 或 OLE DB 中处理的对象对于表格解决方案和多维解决方案而言都是基本相同的。</span><span class="sxs-lookup"><span data-stu-id="05ce0-105">Programmatically, the objects you work with in AMO, ADOMD.NET, XMLA, or OLE DB are fundamentally the same for both tabular and multidimensional solutions.</span></span> <span data-ttu-id="05ce0-106">如果表格模型数据库最能满足您的自定义 BI 解决方案的要求，则可以使用任意 Analysis Services 客户端库和编程接口将您的应用程序集成到 Analysis Services 实例上的表格模型。</span><span class="sxs-lookup"><span data-stu-id="05ce0-106">If the requirements of your custom BI solution are best met by a tabular model database, you can use any of the Analysis Services client libraries and programming interfaces to integrate your application with tabular models on an Analysis Services instance.</span></span> <span data-ttu-id="05ce0-107">若要查询和计算表格模型数据，可以在代码中使用嵌入的 MDX 或 DAX。</span><span class="sxs-lookup"><span data-stu-id="05ce0-107">To query and calculate tabular model data, you can use either embedded MDX or DAX in your code.</span></span>  
  
 <span data-ttu-id="05ce0-108">本节提供有关如何以编程方式使用表格模型实体及其属性的详细信息。</span><span class="sxs-lookup"><span data-stu-id="05ce0-108">This section provides more information about how you can programmatically work with tabular model entities and their properties.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="05ce0-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="05ce0-109">In This Section</span></span>  
 [<span data-ttu-id="05ce0-110">用于商业智能的 CSDL 批注 (CSDLBI)</span><span class="sxs-lookup"><span data-stu-id="05ce0-110">CSDL Annotations for Business Intelligence &#40;CSDLBI&#41;</span></span>](/analysis-services/csdlbi/csdl-annotations-for-business-intelligence-csdlbi)  
  
 [<span data-ttu-id="05ce0-111">了解表格对象模型</span><span class="sxs-lookup"><span data-stu-id="05ce0-111">Understanding the Tabular Object Model</span></span>](representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
 [<span data-ttu-id="05ce0-112">用于商业智能的 CSDL 注释技术参考</span><span class="sxs-lookup"><span data-stu-id="05ce0-112">Technical Reference for BI Annotations to CSDL</span></span>](/analysis-services/csdlbi/technical-reference-for-bi-annotations-to-csdl)  
  
 [<span data-ttu-id="05ce0-113">IMDEmbedded 接口</span><span class="sxs-lookup"><span data-stu-id="05ce0-113">IMDEmbedded Interface</span></span>](imdembeddeddata-interface.md)  
  
## <a name="see-also"></a><span data-ttu-id="05ce0-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="05ce0-114">See Also</span></span>  
 <span data-ttu-id="05ce0-115">[&#40;SSAS 表格&#41;的表格建模](../tabular-models/tabular-models-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="05ce0-115">[Tabular Modeling &#40;SSAS Tabular&#41;](../tabular-models/tabular-models-ssas.md) </span></span>  
 [<span data-ttu-id="05ce0-116">&#40;SSAS 表格&#41;的表格模型设计器</span><span class="sxs-lookup"><span data-stu-id="05ce0-116">Tabular Model Designer &#40;SSAS Tabular&#41;</span></span>](../tabular-model-designer-ssas-tabular.md)  
  
  
