---
title: OLAP 引擎服务器组件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- ports [Analysis Services]
- XML/A listener
- server architecture [Analysis Services]
ms.assetid: 5193c976-9dcd-459c-abba-8c3c44e7a7f2
author: minewiskan
ms.author: owend
ms.openlocfilehash: b60d721a69213ad52536830b49b40d6bb82a3811
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693127"
---
# <a name="olap-engine-server-components"></a><span data-ttu-id="9eee8-102">OLAP 引擎服务器组件</span><span class="sxs-lookup"><span data-stu-id="9eee8-102">OLAP Engine Server Components</span></span>
  <span data-ttu-id="9eee8-103">的服务器组件 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 是作为 Windows 服务运行的**msmdsrv.exe**应用程序。</span><span class="sxs-lookup"><span data-stu-id="9eee8-103">The server component of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] is the **msmdsrv.exe** application, which runs as a Windows service.</span></span> <span data-ttu-id="9eee8-104">该应用程序包含安全组件、一个 XML for Analysis (XMLA) 侦听器组件、一个查询处理器组件以及执行下列功能的多个其他内部组件：</span><span class="sxs-lookup"><span data-stu-id="9eee8-104">This application consists of security components, an XML for Analysis (XMLA) listener component, a query processor component and numerous other internal components that perform the following functions:</span></span>

-   <span data-ttu-id="9eee8-105">分析从客户端接收的语句</span><span class="sxs-lookup"><span data-stu-id="9eee8-105">Parsing statements received from clients</span></span>

-   <span data-ttu-id="9eee8-106">管理元数据</span><span class="sxs-lookup"><span data-stu-id="9eee8-106">Managing metadata</span></span>

-   <span data-ttu-id="9eee8-107">处理翻译</span><span class="sxs-lookup"><span data-stu-id="9eee8-107">Handling transactions</span></span>

-   <span data-ttu-id="9eee8-108">处理计算</span><span class="sxs-lookup"><span data-stu-id="9eee8-108">Processing calculations</span></span>

-   <span data-ttu-id="9eee8-109">存储维度和单元数据</span><span class="sxs-lookup"><span data-stu-id="9eee8-109">Storing dimension and cell data</span></span>

-   <span data-ttu-id="9eee8-110">创建聚合</span><span class="sxs-lookup"><span data-stu-id="9eee8-110">Creating aggregations</span></span>

-   <span data-ttu-id="9eee8-111">计划查询</span><span class="sxs-lookup"><span data-stu-id="9eee8-111">Scheduling queries</span></span>

-   <span data-ttu-id="9eee8-112">缓存对象</span><span class="sxs-lookup"><span data-stu-id="9eee8-112">Caching objects</span></span>

-   <span data-ttu-id="9eee8-113">管理服务器资源</span><span class="sxs-lookup"><span data-stu-id="9eee8-113">Managing server resources</span></span>

## <a name="architectural-diagram"></a><span data-ttu-id="9eee8-114">体系结构关系图</span><span class="sxs-lookup"><span data-stu-id="9eee8-114">Architectural Diagram</span></span>
 <span data-ttu-id="9eee8-115">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实例作为独立的服务来运行，与该服务的通信使用 HTTP 或 TCP 通过 XML for Analysis (XMLA) 进行。</span><span class="sxs-lookup"><span data-stu-id="9eee8-115">An [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance runs as a stand-alone service and communication with the service occurs through XML for Analysis (XMLA), by using either HTTP or TCP.</span></span> <span data-ttu-id="9eee8-116">AMO 是用户应用程序和 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实例之间的一层。</span><span class="sxs-lookup"><span data-stu-id="9eee8-116">AMO is a layer between the user application and the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="9eee8-117">这一层提供对 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 管理对象的访问。</span><span class="sxs-lookup"><span data-stu-id="9eee8-117">This layer provides access to [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] administrative objects.</span></span> <span data-ttu-id="9eee8-118">AMO 是一个类库，它从客户端应用程序获取命令，并将这些命令转换为 XMLA 消息，以用于 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="9eee8-118">AMO is a class library that takes commands from a client application and converts those commands into XMLA messages for the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="9eee8-119">AMO 将 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实例对象作为类提供给最终用户应用程序，具有运行命令的方法成员和保持 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 对象的数据的属性成员。</span><span class="sxs-lookup"><span data-stu-id="9eee8-119">AMO presents [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance objects as classes to the end user application, with method members that run commands and property members that hold the data for the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] objects.</span></span>

 <span data-ttu-id="9eee8-120">下图显示了 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 组件体系结构，包括了在 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实例中运行的所有主要元素和与该示例进行交互的所有用户组件。</span><span class="sxs-lookup"><span data-stu-id="9eee8-120">The following illustration shows the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] components architecture, including all major elements running within the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance and all user components that interact with the instance.</span></span> <span data-ttu-id="9eee8-121">该图还表明了访问该实例的唯一方法是通过 HTTP 或 TCP 使用 XML for Analysis (XMLA) 侦听器。</span><span class="sxs-lookup"><span data-stu-id="9eee8-121">The illustration also shows that the only way to access the instance is by using the XML for Analysis (XMLA) Listener, either by using HTTP or TCP.</span></span>

 <span data-ttu-id="9eee8-122">![Analysis Services 系统体系结构关系图](../../../analysis-services/dev-guide/media/analysisservicessystemarchitecture.gif "Analysis Services 系统体系结构关系图")</span><span class="sxs-lookup"><span data-stu-id="9eee8-122">![Analysis Services System Architecture Diagram](../../../analysis-services/dev-guide/media/analysisservicessystemarchitecture.gif "Analysis Services System Architecture Diagram")</span></span>

## <a name="xmla-listener"></a><span data-ttu-id="9eee8-123">XMLA 侦听器</span><span class="sxs-lookup"><span data-stu-id="9eee8-123">XMLA Listener</span></span>
 <span data-ttu-id="9eee8-124">XMLA 侦听器组件处理 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 与其客户端之间的所有 XMLA 通信。</span><span class="sxs-lookup"><span data-stu-id="9eee8-124">The XMLA listener component handles all XMLA communications between [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] and its clients.</span></span> <span data-ttu-id="9eee8-125">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] `Port` msmdsrv.ini 文件中的配置设置可用于指定 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实例侦听的端口。</span><span class="sxs-lookup"><span data-stu-id="9eee8-125">The [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] `Port` configuration setting in the msmdsrv.ini file can be used to specify a port on which an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance listens.</span></span> <span data-ttu-id="9eee8-126">此文件中的值 0 指示 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 侦听默认端口。</span><span class="sxs-lookup"><span data-stu-id="9eee8-126">A value of 0 in this file indicates that [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] listen on the default port.</span></span> <span data-ttu-id="9eee8-127">除非另有指定，否则 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 使用下列默认的 TCP 端口：</span><span class="sxs-lookup"><span data-stu-id="9eee8-127">Unless otherwise specified, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] uses the following default TCP ports:</span></span>

|<span data-ttu-id="9eee8-128">端口</span><span class="sxs-lookup"><span data-stu-id="9eee8-128">Port</span></span>|<span data-ttu-id="9eee8-129">说明</span><span class="sxs-lookup"><span data-stu-id="9eee8-129">Description</span></span>|
|----------|-----------------|
|<span data-ttu-id="9eee8-130">2383</span><span class="sxs-lookup"><span data-stu-id="9eee8-130">2383</span></span>|<span data-ttu-id="9eee8-131">的默认实例 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9eee8-131">Default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|
|<span data-ttu-id="9eee8-132">2382</span><span class="sxs-lookup"><span data-stu-id="9eee8-132">2382</span></span>|<span data-ttu-id="9eee8-133">其他实例的重定向程序 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9eee8-133">Redirector for other instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|
|<span data-ttu-id="9eee8-134">在服务器启动时动态分配</span><span class="sxs-lookup"><span data-stu-id="9eee8-134">Dynamically assigned at server startup</span></span>|<span data-ttu-id="9eee8-135">的命名实例 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9eee8-135">Named instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|

 <span data-ttu-id="9eee8-136">有关更多详细信息，请参阅[配置 Windows 防火墙以允许 Analysis Services 访问](../../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)。</span><span class="sxs-lookup"><span data-stu-id="9eee8-136">See [Configure the Windows Firewall to Allow Analysis Services Access](../../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) for more details.</span></span>

## <a name="see-also"></a><span data-ttu-id="9eee8-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9eee8-137">See Also</span></span>
 <span data-ttu-id="9eee8-138">[对象命名规则 &#40;Analysis Services&#41;](object-naming-rules-analysis-services.md) [物理体系结构 &#40;Analysis Services 多维数据](understanding-microsoft-olap-physical-architecture.md)&#41;[逻辑体系结构 &#40;Analysis Services 多维数据&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)</span><span class="sxs-lookup"><span data-stu-id="9eee8-138">[Object Naming Rules &#40;Analysis Services&#41;](object-naming-rules-analysis-services.md) [Physical Architecture &#40;Analysis Services - Multidimensional Data&#41;](understanding-microsoft-olap-physical-architecture.md) [Logical Architecture &#40;Analysis Services - Multidimensional Data&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)</span></span>


