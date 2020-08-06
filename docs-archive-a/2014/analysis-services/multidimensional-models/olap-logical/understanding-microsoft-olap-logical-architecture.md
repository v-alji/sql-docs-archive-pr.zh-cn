---
title: 逻辑体系结构 (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- logical architecture [Analysis Services Multidimensional Data]
ms.assetid: 1b9cae0a-8990-4194-af5f-a1ea5f2aff06
author: minewiskan
ms.author: owend
ms.openlocfilehash: d93361fb14bc6544ffa7376439c2da0c8e06c3fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589298"
---
# <a name="logical-architecture-analysis-services---multidimensional-data"></a><span data-ttu-id="fe621-102">逻辑体系结构（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="fe621-102">Logical Architecture (Analysis Services - Multidimensional Data)</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="fe621-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 同时使用服务器组件和客户端组件为商业智能应用程序提供联机分析处理 (OLAP) 和数据挖掘功能：</span><span class="sxs-lookup"><span data-stu-id="fe621-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] uses both server and client components to supply online analytical processing (OLAP) and data mining functionality for business intelligence applications:</span></span>  
  
-   <span data-ttu-id="fe621-104">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 的服务器组件是作为 Microsoft Windows 服务来实现。</span><span class="sxs-lookup"><span data-stu-id="fe621-104">The server component of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] is implemented as a Microsoft Windows service.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="fe621-105">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]支持同一台计算机上的多个实例，每个实例都 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实现为 Windows 服务的单独实例。</span><span class="sxs-lookup"><span data-stu-id="fe621-105">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supports multiple instances on the same computer, with each instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] implemented as a separate instance of the Windows service.</span></span>  
  
-   <span data-ttu-id="fe621-106">客户端使用公用标准 XML for Analysis (XMLA) 与 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 进行通信，作为一项 Web 服务，XMLA 是基于 SOAP 的协议，用于发出命令和接收响应。</span><span class="sxs-lookup"><span data-stu-id="fe621-106">Clients communicate with [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] using the public standard XML for Analysis (XMLA), a SOAP-based protocol for issuing commands and receiving responses, exposed as a Web service.</span></span> <span data-ttu-id="fe621-107">还可以通过 XMLA 提供客户端对象模型，可以使用托管提供程序（例如，ADOMD.NET）或本机 OLE DB 访问接口来访问该模型。</span><span class="sxs-lookup"><span data-stu-id="fe621-107">Client object models are also provided over XMLA, and can be accessed either by using a managed provider, such as ADOMD.NET, or a native OLE DB provider.</span></span>  
  
-   <span data-ttu-id="fe621-108">可以使用以下语言发出查询命令：SQL、多维表达式 (MDX)（一种用于分析的行业标准查询语言）或数据挖掘扩展插件 (DMX)（一种面向数据挖掘的行业标准查询语言）。</span><span class="sxs-lookup"><span data-stu-id="fe621-108">Query commands can be issued using the following languages: SQL; Multidimensional Expressions (MDX), an industry standard query language for analysis; or Data Mining Extensions (DMX), an industry standard query language oriented toward data mining.</span></span> <span data-ttu-id="fe621-109">Analysis Services 脚本语言 (ASSL) 还可以用来管理 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 数据库对象。</span><span class="sxs-lookup"><span data-stu-id="fe621-109">Analysis Services Scripting Language (ASSL) can also be used to manage [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database objects.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="fe621-110">还支持本地多维数据集引擎，已断开连接的客户端上的应用程序可在该引擎的帮助下，在本地浏览已存储的多维数据。</span><span class="sxs-lookup"><span data-stu-id="fe621-110">also supports a local cube engine that enables applications on disconnected clients to browse locally stored multidimensional data.</span></span> <span data-ttu-id="fe621-111">有关详细信息，请参阅[Analysis Services 开发的客户端体系结构要求](../olap-physical/client-architecture-requirements-for-analysis-services-development.md)</span><span class="sxs-lookup"><span data-stu-id="fe621-111">For more information, see [Client Architecture Requirements for Analysis Services Development](../olap-physical/client-architecture-requirements-for-analysis-services-development.md)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fe621-112">本节内容</span><span class="sxs-lookup"><span data-stu-id="fe621-112">In This Section</span></span>  
 <span data-ttu-id="fe621-113">**逻辑体系结构概述**</span><span class="sxs-lookup"><span data-stu-id="fe621-113">**Logical Architecture Overview**</span></span>  
 [<span data-ttu-id="fe621-114">逻辑体系结构概述 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="fe621-114">Logical Architecture Overview &#40;Analysis Services - Multidimensional Data&#41;</span></span>](logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 <span data-ttu-id="fe621-115">**服务器对象**</span><span class="sxs-lookup"><span data-stu-id="fe621-115">**Server Objects**</span></span>  
 [<span data-ttu-id="fe621-116">Analysis Services 多维数据 &#40;服务器对象&#41;</span><span class="sxs-lookup"><span data-stu-id="fe621-116">Server Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](server-objects-analysis-services-multidimensional-data.md)  
  
 <span data-ttu-id="fe621-117">**数据库对象**</span><span class="sxs-lookup"><span data-stu-id="fe621-117">**Database Objects**</span></span>  
 [<span data-ttu-id="fe621-118">数据库对象（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="fe621-118">Database Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](database-objects-analysis-services-multidimensional-data.md)  
  
 <span data-ttu-id="fe621-119">**Dimension 对象**</span><span class="sxs-lookup"><span data-stu-id="fe621-119">**Dimension Objects**</span></span>  
 [<span data-ttu-id="fe621-120">维度对象 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="fe621-120">Dimension Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../../multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 <span data-ttu-id="fe621-121">**多维数据集对象**</span><span class="sxs-lookup"><span data-stu-id="fe621-121">**Cube Objects**</span></span>  
 [<span data-ttu-id="fe621-122">多维数据集对象 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="fe621-122">Cube Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../../multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 <span data-ttu-id="fe621-123">**代码访问安全性**</span><span class="sxs-lookup"><span data-stu-id="fe621-123">**User Access Security**</span></span>  
 [<span data-ttu-id="fe621-124">用户访问安全性体系结构</span><span class="sxs-lookup"><span data-stu-id="fe621-124">User Access Security Architecture</span></span>](understanding-microsoft-olap-logical-architecture.md)  
  
## <a name="see-also"></a><span data-ttu-id="fe621-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fe621-125">See Also</span></span>  
 <span data-ttu-id="fe621-126">[了解 Microsoft OLAP 体系结构](../olap-physical/understanding-microsoft-olap-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="fe621-126">[Understanding Microsoft OLAP Architecture](../olap-physical/understanding-microsoft-olap-architecture.md) </span></span>  
 [<span data-ttu-id="fe621-127">物理体系结构（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="fe621-127">Physical Architecture &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  
