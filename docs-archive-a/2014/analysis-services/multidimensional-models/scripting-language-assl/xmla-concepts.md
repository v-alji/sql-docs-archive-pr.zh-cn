---
title: XMLA 概念 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XMLA, concepts
ms.assetid: 816183a7-d2f7-4e14-8e5b-2a4c1798fbc1
author: minewiskan
ms.author: owend
ms.openlocfilehash: b2e18917b56d40f8b813ba10083cc1b408e51a98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588720"
---
# <a name="xmla-concepts"></a><span data-ttu-id="5559c-102">XMLA 概念</span><span class="sxs-lookup"><span data-stu-id="5559c-102">XMLA Concepts</span></span>
  <span data-ttu-id="5559c-103">XML for Analysis (XMLA) 开放标准支持对位于万维网上的数据源的数据访问。</span><span class="sxs-lookup"><span data-stu-id="5559c-103">The XML for Analysis (XMLA) open standard supports data access to data sources that reside on the World Wide Web.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="5559c-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 按 xmla 1.1 规范实现 xmla。</span><span class="sxs-lookup"><span data-stu-id="5559c-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] implements XMLA per the XMLA 1.1 specification.</span></span>  
  
 <span data-ttu-id="5559c-105">XML for Analysis (XMLA) 是一种基于简单对象访问协议 (SOAP) 的 XML 协议，它是专为对驻留在 Web 上的任何标准多维数据源的通用数据访问而设计的。</span><span class="sxs-lookup"><span data-stu-id="5559c-105">XML for Analysis (XMLA) is a Simple Object Access Protocol (SOAP)-based XML protocol, designed specifically for universal data access to any standard multidimensional data source residing on the Web.</span></span> <span data-ttu-id="5559c-106">XMLA 还无需部署 (COM) 或 .NET Framework 接口公开组件对象模型的客户端组件 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5559c-106">XMLA also eliminates the need to deploy a client component that exposes Component Object Model (COM) or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework interfaces.</span></span> <span data-ttu-id="5559c-107">如果与服务器之间的往返通信要占用大量时间和资源，并且对数据源的有状态连接会限制服务器上的用户连接数，则 XMLA 会针对 Internet 进行优化。</span><span class="sxs-lookup"><span data-stu-id="5559c-107">XMLA is optimized for the Internet, when round trips to the server are expensive in terms of time and resources, and when stateful connections to a data source can limit user connections on the server.</span></span>  
  
 <span data-ttu-id="5559c-108">XMLA 是的本机协议 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ，用于客户端应用程序和实例之间的所有交互 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5559c-108">XMLA is the native protocol for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], used for all interaction between a client application and an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="5559c-109">完全支持 XML for Analysis 1.1，并且还提供了支持元数据管理、会话管理和锁定功能的扩展。</span><span class="sxs-lookup"><span data-stu-id="5559c-109">fully supports XML for Analysis 1.1, and also provides extensions to support metadata management, session management, and locking capabilities.</span></span> <span data-ttu-id="5559c-110">与 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实例进行通信时，分析管理对象 (AMO) 和 ADOMD.NET 都使用 XMLA 协议。</span><span class="sxs-lookup"><span data-stu-id="5559c-110">Both Analysis Management Objects (AMO) and ADOMD.NET use the XMLA protocol when communicating with an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="handling-xmla-communications"></a><span data-ttu-id="5559c-111">处理 XMLA 通信</span><span class="sxs-lookup"><span data-stu-id="5559c-111">Handling XMLA Communications</span></span>  
 <span data-ttu-id="5559c-112">XMLA 开放标准介绍了以下两种常规访问方法：`Discover` 和 `Execute`。</span><span class="sxs-lookup"><span data-stu-id="5559c-112">The XMLA open standard describes two generally accessible methods: `Discover` and `Execute`.</span></span> <span data-ttu-id="5559c-113">这些方法使用 XML 支持的松散耦合客户端和服务器体系结构处理有关 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实例的传入和传出信息。</span><span class="sxs-lookup"><span data-stu-id="5559c-113">These methods use the loosely-coupled client and server architecture supported by XML to handle incoming and outgoing information on an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="5559c-114">`Discover` 方法可从 Web 服务获取信息和元数据。</span><span class="sxs-lookup"><span data-stu-id="5559c-114">The `Discover` method obtains information and metadata from a Web service.</span></span> <span data-ttu-id="5559c-115">此信息可包含可用数据源的列表以及任何数据源访问接口的相关信息。</span><span class="sxs-lookup"><span data-stu-id="5559c-115">This information can include a list of available data sources, as well as information about any of the data source providers.</span></span> <span data-ttu-id="5559c-116">属性可定义并定形从数据源中获取的数据。</span><span class="sxs-lookup"><span data-stu-id="5559c-116">Properties define and shape the data that is obtained from a data source.</span></span> <span data-ttu-id="5559c-117">`Discover` 方法是定义多种类型的信息的常用方法，客户端应用程序可能需要从 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实例的数据源中获取这些信息。</span><span class="sxs-lookup"><span data-stu-id="5559c-117">The `Discover` method is a common method for defining the many types of information a client application may require from data sources on [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instances.</span></span> <span data-ttu-id="5559c-118">属性和泛型接口可提供可扩展性，而无需重写客户端应用程序中的现有函数。</span><span class="sxs-lookup"><span data-stu-id="5559c-118">The properties and the generic interface provide extensibility without requiring you to rewrite existing functions in a client application.</span></span>  
  
 <span data-ttu-id="5559c-119">`Execute` 方法使应用程序能够对 XMLA 数据源运行特定于访问接口的命令。</span><span class="sxs-lookup"><span data-stu-id="5559c-119">The `Execute` method allows applications to run provider-specific commands against XMLA data sources.</span></span>  
  
 <span data-ttu-id="5559c-120">尽管 XMLA 协议是针对 Web 应用程序进行优化的，但它还可用于面向 LAN 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="5559c-120">Although the XMLA protocol is optimized for Web applications, it can also be leveraged for LAN-oriented applications.</span></span> <span data-ttu-id="5559c-121">下列应用程序可从基于此 XML 的 API 中获益：</span><span class="sxs-lookup"><span data-stu-id="5559c-121">The following applications can benefit from this XML-based API:</span></span>  
  
-   <span data-ttu-id="5559c-122">需要在客户端与服务器之间使用灵活技术的客户端/服务器应用程序</span><span class="sxs-lookup"><span data-stu-id="5559c-122">Client/server applications that require flexible technology between clients and the server</span></span>  
  
-   <span data-ttu-id="5559c-123">针对多个操作系统的客户端/服务器应用程序</span><span class="sxs-lookup"><span data-stu-id="5559c-123">Client/server applications that target multiple operating systems</span></span>  
  
-   <span data-ttu-id="5559c-124">不需要明显状态以便增加服务器容量的客户端</span><span class="sxs-lookup"><span data-stu-id="5559c-124">Clients that do not require significant state in order to increase server capacity</span></span>  
  
## <a name="xmla-and-the-unified-dimensional-model"></a><span data-ttu-id="5559c-125">XMLA 和统一维度模型</span><span class="sxs-lookup"><span data-stu-id="5559c-125">XMLA and the Unified Dimensional Model</span></span>  
 <span data-ttu-id="5559c-126">XMLA 是采用统一维度模型 (UDM) 方法的商业智能应用程序所使用的协议</span><span class="sxs-lookup"><span data-stu-id="5559c-126">XMLA is the protocol used by business intelligence applications that employ the Unified Dimensional Model (UDM) methodology</span></span>  
  
  
