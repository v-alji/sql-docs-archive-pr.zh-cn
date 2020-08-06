---
title: 默认情况下，功能 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a9529edf-337e-4fdd-9a13-99cfe96b4fa1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 87752b8760ffc80e80c87ac1132cae36f2f151b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689106"
---
# <a name="features-off-by-default-analysis-services"></a><span data-ttu-id="6e048-102">默认情况下功能关闭 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="6e048-102">Features off by default (Analysis Services)</span></span>
  <span data-ttu-id="6e048-103">默认情况下， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例在设计上是安全的。</span><span class="sxs-lookup"><span data-stu-id="6e048-103">An instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is designed to be secure by default.</span></span> <span data-ttu-id="6e048-104">因此，可能危及安全的功能默认处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="6e048-104">Therefore, features that might compromise security are disabled by default.</span></span> <span data-ttu-id="6e048-105">下列功能在安装后处于禁用状态，如果要使用它们，则必须专门进行启用。</span><span class="sxs-lookup"><span data-stu-id="6e048-105">The following features are installed in a disabled state and must specifically be enabled if you want to use them.</span></span>  
  
## <a name="feature-list"></a><span data-ttu-id="6e048-106">功能列表</span><span class="sxs-lookup"><span data-stu-id="6e048-106">Feature List</span></span>  
 <span data-ttu-id="6e048-107">若要启用以下功能，请使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 连接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6e048-107">To enable the following features, connect to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="6e048-108">右键单击实例名称，选择“方面”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6e048-108">Right-click the instance name and choose **Facets**.</span></span> <span data-ttu-id="6e048-109">或者，可通过服务器属性来启用这些功能，如下一节所述。</span><span class="sxs-lookup"><span data-stu-id="6e048-109">Alternatively, you can enable these features through server properties, as described in the next section.</span></span>  
  
-   <span data-ttu-id="6e048-110">即席数据挖掘 (OpenRowset) 查询</span><span class="sxs-lookup"><span data-stu-id="6e048-110">Ad Hoc Data Mining (OpenRowset) Queries</span></span>  
  
-   <span data-ttu-id="6e048-111">链接对象（目标）</span><span class="sxs-lookup"><span data-stu-id="6e048-111">Linked Objects (To)</span></span>  
  
-   <span data-ttu-id="6e048-112">链接对象（来源）</span><span class="sxs-lookup"><span data-stu-id="6e048-112">Linked Objects (From)</span></span>  
  
-   <span data-ttu-id="6e048-113">仅侦听本地连接</span><span class="sxs-lookup"><span data-stu-id="6e048-113">Listen Only On Local Connections</span></span>  
  
-   <span data-ttu-id="6e048-114">用户定义的函数</span><span class="sxs-lookup"><span data-stu-id="6e048-114">User Defined Functions</span></span>  
  
## <a name="server-properties"></a><span data-ttu-id="6e048-115">服务器属性</span><span class="sxs-lookup"><span data-stu-id="6e048-115">Server properties</span></span>  
 <span data-ttu-id="6e048-116">可通过服务器属性启用默认情况下处于关闭状态的其他功能。</span><span class="sxs-lookup"><span data-stu-id="6e048-116">Additional features that are off by default can be enabled through server properties.</span></span> <span data-ttu-id="6e048-117">使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 连接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6e048-117">Connect to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="6e048-118">右键单击实例名称，选择“属性”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6e048-118">Right-click the instance name and choose **Properties**.</span></span> <span data-ttu-id="6e048-119">单击 **“常规”**，然后单击 **“显示高级”** ，以显示较大的属性列表。</span><span class="sxs-lookup"><span data-stu-id="6e048-119">Click **General**, and then click **Show Advanced** to display a larger property list.</span></span>  
  
-   <span data-ttu-id="6e048-120">即席数据挖掘 (OpenRowset) 查询</span><span class="sxs-lookup"><span data-stu-id="6e048-120">Ad Hoc Data Mining (OpenRowset) Queries</span></span>  
  
-   <span data-ttu-id="6e048-121">允许会话挖掘模型（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="6e048-121">Allow Session Mining Models (Data Mining)</span></span>  
  
-   <span data-ttu-id="6e048-122">链接对象（目标）</span><span class="sxs-lookup"><span data-stu-id="6e048-122">Linked Objects (To)</span></span>  
  
-   <span data-ttu-id="6e048-123">链接对象（来源）</span><span class="sxs-lookup"><span data-stu-id="6e048-123">Linked Objects (From)</span></span>  
  
-   <span data-ttu-id="6e048-124">基于 COM 的用户定义函数</span><span class="sxs-lookup"><span data-stu-id="6e048-124">COM based user-defined functions</span></span>  
  
-   <span data-ttu-id="6e048-125">网络流量记录器跟踪定义（模板）。</span><span class="sxs-lookup"><span data-stu-id="6e048-125">Flight Recorder Trace Definitions (templates).</span></span>  
  
-   <span data-ttu-id="6e048-126">查询日志记录</span><span class="sxs-lookup"><span data-stu-id="6e048-126">Query logging</span></span>  
  
-   <span data-ttu-id="6e048-127">仅侦听本地连接</span><span class="sxs-lookup"><span data-stu-id="6e048-127">Listen Only On Local Connections</span></span>  
  
-   <span data-ttu-id="6e048-128">二进制 XML</span><span class="sxs-lookup"><span data-stu-id="6e048-128">Binary XML</span></span>  
  
-   <span data-ttu-id="6e048-129">压缩</span><span class="sxs-lookup"><span data-stu-id="6e048-129">Compression</span></span>  
  
-   <span data-ttu-id="6e048-130">组关联。</span><span class="sxs-lookup"><span data-stu-id="6e048-130">Group affinity.</span></span> <span data-ttu-id="6e048-131">有关详细信息，请参阅 [Thread Pool Properties](../server-properties/thread-pool-properties.md) 。</span><span class="sxs-lookup"><span data-stu-id="6e048-131">See [Thread Pool Properties](../server-properties/thread-pool-properties.md) for details.</span></span>  
  
  
