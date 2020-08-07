---
title: 物理体系结构 (Analysis Services 数据挖掘) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- server architecture [Analysis Services]
- architecture [Analysis Services]
ms.assetid: 25eeecf0-6e85-4527-b94d-5503d27edaed
author: minewiskan
ms.author: owend
ms.openlocfilehash: 787ca28c08dc41a6b9561251077716a406358c6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690890"
---
# <a name="physical-architecture-analysis-services---data-mining"></a><span data-ttu-id="3c046-102">物理体系结构（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="3c046-102">Physical Architecture (Analysis Services - Data Mining)</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="3c046-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]同时使用服务器组件和客户端组件为商业智能应用程序提供数据挖掘功能：</span><span class="sxs-lookup"><span data-stu-id="3c046-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses both server and client components to supply data mining functionality for business intelligence applications:</span></span>

-   <span data-ttu-id="3c046-104">服务器组件作为 Microsoft Windows 服务来实现。</span><span class="sxs-lookup"><span data-stu-id="3c046-104">The server component is implemented as a Microsoft Windows service.</span></span> <span data-ttu-id="3c046-105">可以在同一台计算机上具有多个实例，每个 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例均作为单独的 Windows 服务实例实现。</span><span class="sxs-lookup"><span data-stu-id="3c046-105">You can have multiple instances on the same computer, with each instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] implemented as a separate instance of the Windows service.</span></span>

-   <span data-ttu-id="3c046-106">客户端使用公用标准 XML for Analysis (XMLA) 与 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 进行通信，作为一项 Web 服务，XMLA 是基于 SOAP 的协议，用于发出命令和接收响应。</span><span class="sxs-lookup"><span data-stu-id="3c046-106">Clients communicate with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] using the public standard XML for Analysis (XMLA), a SOAP-based protocol for issuing commands and receiving responses, exposed as a Web service.</span></span> <span data-ttu-id="3c046-107">还可以通过 XMLA 提供客户端对象模型，可以使用托管提供程序（例如，ADOMD.NET）或本机 OLE DB 访问接口来访问该模型。</span><span class="sxs-lookup"><span data-stu-id="3c046-107">Client object models are also provided over XMLA, and can be accessed either by using a managed provider, such as ADOMD.NET, or a native OLE DB provider.</span></span>

-   <span data-ttu-id="3c046-108">可以使用数据挖掘扩展插件 (DMX)（一种面向数据挖掘的行业标准查询语言）发出查询命令。</span><span class="sxs-lookup"><span data-stu-id="3c046-108">Query commands can be issued using Data Mining Extensions (DMX), an industry standard query language oriented toward data mining.</span></span> <span data-ttu-id="3c046-109">Analysis Services 脚本语言 (ASSL) 还可以用来管理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库对象。</span><span class="sxs-lookup"><span data-stu-id="3c046-109">Analysis Services Scripting Language (ASSL) can also be used to manage [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database objects.</span></span>

## <a name="architectural-diagram"></a><span data-ttu-id="3c046-110">体系结构关系图</span><span class="sxs-lookup"><span data-stu-id="3c046-110">Architectural Diagram</span></span>
 <span data-ttu-id="3c046-111">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例作为独立的服务来运行，与该服务的通信使用 HTTP 或 TCP 通过 XML for Analysis (XMLA) 进行。</span><span class="sxs-lookup"><span data-stu-id="3c046-111">An [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance runs as a stand-alone service and communication with the service occurs through XML for Analysis (XMLA), by using either HTTP or TCP.</span></span>

 <span data-ttu-id="3c046-112">AMO 是用户应用程序和 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例之间的一层，它提供对 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理对象的访问。</span><span class="sxs-lookup"><span data-stu-id="3c046-112">AMO is a layer between the user application and the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance that provides access to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrative objects.</span></span> <span data-ttu-id="3c046-113">AMO 是一个类库，它从客户端应用程序获取命令，并将这些命令转换为 XMLA 消息，以用于 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="3c046-113">AMO is a class library that takes commands from a client application and converts those commands into XMLA messages for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="3c046-114">AMO 将 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例对象作为类提供给最终用户应用程序，具有运行命令的方法成员和保持 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象的数据的属性成员。</span><span class="sxs-lookup"><span data-stu-id="3c046-114">AMO presents [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance objects as classes to the end user application, with method members that run commands and property members that hold the data for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects.</span></span>

 <span data-ttu-id="3c046-115">下图显示了 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 组件体系结构，包括了 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例中的服务和与该实例进行交互的用户组件。</span><span class="sxs-lookup"><span data-stu-id="3c046-115">The following illustration shows the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] components architecture, including services within the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and user components that interact with the instance.</span></span>

 <span data-ttu-id="3c046-116">该图表明了访问该实例的唯一方法是通过 HTTP 或 TCP 使用 XML for Analysis (XMLA) 侦听器。</span><span class="sxs-lookup"><span data-stu-id="3c046-116">The illustration shows that the only way to access the instance is by using the XML for Analysis (XMLA) Listener, either by using HTTP or TCP.</span></span>

> [!WARNING]
>  <span data-ttu-id="3c046-117">不推荐使用 DSO。</span><span class="sxs-lookup"><span data-stu-id="3c046-117">DSO has been deprecated.</span></span> <span data-ttu-id="3c046-118">不要使用 DSO 开发解决方案。</span><span class="sxs-lookup"><span data-stu-id="3c046-118">You should not use DSO to develop solutions.</span></span>

 <span data-ttu-id="3c046-119">![Analysis Services 系统体系结构关系图](../dev-guide/media/analysisservicessystemarchitecture.gif "Analysis Services 系统体系结构关系图")</span><span class="sxs-lookup"><span data-stu-id="3c046-119">![Analysis Services System Architecture Diagram](../dev-guide/media/analysisservicessystemarchitecture.gif "Analysis Services System Architecture Diagram")</span></span>

## <a name="server-configuration"></a><span data-ttu-id="3c046-120">服务器配置</span><span class="sxs-lookup"><span data-stu-id="3c046-120">Server Configuration</span></span>
 <span data-ttu-id="3c046-121">一个服务器实例可支持多个 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库，每个数据库都具有其自己的用来响应客户端请求和处理对象的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务实例。</span><span class="sxs-lookup"><span data-stu-id="3c046-121">One server instance can support multiple [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases, each with its own instance of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] service that responds to client requests and processes objects.</span></span>

 <span data-ttu-id="3c046-122">如果要使用表格模型、数据挖掘和/或多维模型，必须安装单独的实例。</span><span class="sxs-lookup"><span data-stu-id="3c046-122">Separate instances must be installed if you want to work with both tabular models and data mining and/or multidimensional models.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="3c046-123">支持并行安装在表格模式（使用 xVelocity 内存中分析引擎 (VertiPaq) 存储引擎）下运行的实例和在常规 OLAP、MOLAP 或 ROLAP 配置中的一种配置中运行的实例。</span><span class="sxs-lookup"><span data-stu-id="3c046-123">supports side-by-side installation of instances running in tabular mode (which uses the xVelocity in-memory analytics engine (VertiPaq) storage engine) and instances running in one of the conventional OLAP, MOLAP, or ROLAP configurations.</span></span> <span data-ttu-id="3c046-124">有关详细信息，请参阅 [确定 Analysis Services 实例的服务器模式](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="3c046-124">For more information, see [Determine the Server Mode of an Analysis Services Instance](../instances/determine-the-server-mode-of-an-analysis-services-instance.md).</span></span>

 <span data-ttu-id="3c046-125">客户端与 Analysis Services 服务器之间的所有通信都使用与平台和语言无关的 XMLA 协议。</span><span class="sxs-lookup"><span data-stu-id="3c046-125">All communications between a client and the Analysis Services server use XMLA, which is a platform-independent and language-independent protocol.</span></span> <span data-ttu-id="3c046-126">从客户端那里收到请求后，Analysis Services 确定该请求是与 OLAP 相关还是与数据挖掘相关，并相应地路由请求。</span><span class="sxs-lookup"><span data-stu-id="3c046-126">When a request is received from a client, Analysis Services determines whether the request relates to OLAP or data mining, and routes the request appropriately.</span></span> <span data-ttu-id="3c046-127">有关详细信息，请参阅 [OLAP 引擎服务器组件](../multidimensional-models/olap-physical/olap-engine-server-components.md)。</span><span class="sxs-lookup"><span data-stu-id="3c046-127">For more information, see [OLAP Engine Server Components](../multidimensional-models/olap-physical/olap-engine-server-components.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3c046-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3c046-128">See Also</span></span>
 [<span data-ttu-id="3c046-129">逻辑体系结构（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="3c046-129">Logical Architecture &#40;Analysis Services - Data Mining&#41;</span></span>](logical-architecture-analysis-services-data-mining.md)


