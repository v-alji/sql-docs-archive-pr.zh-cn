---
title: 数据挖掘体系结构 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 105f52e1-ad3b-4cd0-b67b-06dbb451c304
author: minewiskan
ms.author: owend
ms.openlocfilehash: a372972fd7fa39f7bcfd2e10abbc4fbf8f8c10aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589969"
---
# <a name="data-mining-architecture"></a><span data-ttu-id="bdeb2-102">数据挖掘体系结构</span><span class="sxs-lookup"><span data-stu-id="bdeb2-102">Data Mining Architecture</span></span>
  <span data-ttu-id="bdeb2-103">本节介绍在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]实例中托管的数据挖掘解决方案的体系结构。</span><span class="sxs-lookup"><span data-stu-id="bdeb2-103">This section describes the architecture of data mining solutions that are hosted in an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="bdeb2-104">本节中的主题介绍支持数据挖掘的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例的逻辑和物理体系结构，并提供可用于与数据挖掘服务器通信以及通过本地或远程方式处理数据挖掘对象的客户端、访问接口和协议的相关信息。</span><span class="sxs-lookup"><span data-stu-id="bdeb2-104">The topics in this section describe the logical and physical architecture of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance that supports data mining, and also provide information about the clients, providers, and protocols that can be used to communicate with data mining servers, and to work with data mining objects either locally or remotely.</span></span>  
  
 <span data-ttu-id="bdeb2-105">通常，SQL Server 数据挖掘作为一个服务来操作，该服务作为以多维模式运行的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例的一部分来提供；因此，我们建议您还要查看“联机丛书”中介绍 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 多维解决方案的操作、维护和配置的以下各节。</span><span class="sxs-lookup"><span data-stu-id="bdeb2-105">In general, SQL Server Data Mining operates as a service that is provided as part of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance running in multidimensional mode; therefore, we recommend that you also review the following sections of Books Online that describe the operation, maintenance, and configuration of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] multidimensional solutions.</span></span>  
  
 [<span data-ttu-id="bdeb2-106">多维模型对象处理</span><span class="sxs-lookup"><span data-stu-id="bdeb2-106">Multidimensional Model Object Processing</span></span>](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)  
  
 [<span data-ttu-id="bdeb2-107">连接到 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="bdeb2-107">Connect to Analysis Services</span></span>](../instances/connect-to-analysis-services.md)  
  
 [<span data-ttu-id="bdeb2-108">数据库存储位置</span><span class="sxs-lookup"><span data-stu-id="bdeb2-108">Database Storage Location</span></span>](../multidimensional-models/database-storage-location.md)  
  
 [<span data-ttu-id="bdeb2-109">在 ReadOnly 和 ReadWrite 模式之间切换 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="bdeb2-109">Switch an Analysis Services database between ReadOnly and ReadWrite modes</span></span>](../multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
 <span data-ttu-id="bdeb2-110">有关如何在您的商业智能解决方案中实施数据挖掘的详细信息，请参阅 MSDN Library 中的“解决方案指南”一节。</span><span class="sxs-lookup"><span data-stu-id="bdeb2-110">For more information about how you can implement data mining in your business intelligence solution, see the Solution Guides section of the MSDN Library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bdeb2-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="bdeb2-111">In This Section</span></span>  
 [<span data-ttu-id="bdeb2-112">逻辑体系结构（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="bdeb2-112">Logical Architecture &#40;Analysis Services - Data Mining&#41;</span></span>](logical-architecture-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="bdeb2-113">物理体系结构（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="bdeb2-113">Physical Architecture &#40;Analysis Services - Data Mining&#41;</span></span>](physical-architecture-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="bdeb2-114">数据挖掘服务和数据源</span><span class="sxs-lookup"><span data-stu-id="bdeb2-114">Data Mining Services and Data Sources</span></span>](data-mining-services-and-data-sources.md)  
  
 [<span data-ttu-id="bdeb2-115">管理数据挖掘解决方案和对象</span><span class="sxs-lookup"><span data-stu-id="bdeb2-115">Management of Data Mining Solutions and Objects</span></span>](management-of-data-mining-solutions-and-objects.md)  
  
 [<span data-ttu-id="bdeb2-116">安全性概述（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="bdeb2-116">Security Overview &#40;Data Mining&#41;</span></span>](security-overview-data-mining.md)  
  
## <a name="see-also"></a><span data-ttu-id="bdeb2-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bdeb2-117">See Also</span></span>  
 <span data-ttu-id="bdeb2-118">[多维模型编程](../multidimensional-models/multidimensional-model-programming.md) </span><span class="sxs-lookup"><span data-stu-id="bdeb2-118">[Multidimensional Model Programming](../multidimensional-models/multidimensional-model-programming.md) </span></span>  
 [<span data-ttu-id="bdeb2-119">数据挖掘编程</span><span class="sxs-lookup"><span data-stu-id="bdeb2-119">Data Mining Programming</span></span>](../dev-guide/data-mining-programming.md)  
  
  
