---
title: 网络属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- LingerTimeout property
- EnableNagleAlgorithm property
- MinPendingAcceptExCount property
- MaxPendingSendCount property
- EnableBinaryXML property
- MinPendingReceiveCount property
- MaxCompletedReceiveCount property
- DisableNonblockingMode property
- RequestSizeThreshold property
- CompressionLevel property
- ReceiveBufferSize property
- EnableCompression property
- ServerSendTimeout property
- IPV4Support property
- MaxPendingReceiveCount property
- MaxPendingAcceptExCount property
- IPV6Support property
- MaxAllowedRequestSize property
- ServerReceiveTimeout property
- EnableLingerOnClose property
- InitialConnectTimeout property
- SendBufferSize property
- ScatterReceiveMultiplier property
- network properties [Analysis Services]
ms.assetid: ef4251e2-abe5-4c5b-9868-7549782d0244
author: minewiskan
ms.author: owend
ms.openlocfilehash: 10ad5bbbcffdfc3d3c4fefe3111e4c4425919915
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586007"
---
# <a name="network-properties"></a><span data-ttu-id="07924-102">网络属性</span><span class="sxs-lookup"><span data-stu-id="07924-102">Network Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="07924-103">支持下表中列出的服务器属性。</span><span class="sxs-lookup"><span data-stu-id="07924-103">supports the server properties listed in the following tables.</span></span> <span data-ttu-id="07924-104">有关更多服务器属性以及如何设置这些属性的详细信息，请参阅 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="07924-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="07924-105">**适用于：** 多维和表格服务器模式</span><span class="sxs-lookup"><span data-stu-id="07924-105">**Applies to:** Multidimensional and Tabular server mode</span></span>  
  
## <a name="general"></a><span data-ttu-id="07924-106">常规</span><span class="sxs-lookup"><span data-stu-id="07924-106">General</span></span>  
 `ListenOnlyOnLocalConnections`  
 <span data-ttu-id="07924-107">一个布尔值属性，指定是否仅侦听本地连接（例如 localhost）。</span><span class="sxs-lookup"><span data-stu-id="07924-107">A Boolean property that identifies whether to listen only on local connections, for example localhost.</span></span>  
  
## <a name="listener"></a><span data-ttu-id="07924-108">侦听器</span><span class="sxs-lookup"><span data-stu-id="07924-108">Listener</span></span>  
 `IPV4Support`  
 <span data-ttu-id="07924-109">有符号 32 位整数属性，用于定义 IPv4 协议支持。</span><span class="sxs-lookup"><span data-stu-id="07924-109">A signed 32-bit integer property that defines support for IPv4 protocol.</span></span> <span data-ttu-id="07924-110">此属性具有下表所列的值之一：</span><span class="sxs-lookup"><span data-stu-id="07924-110">This property has one of the values listed in the following table:</span></span>  
  
|<span data-ttu-id="07924-111">值</span><span class="sxs-lookup"><span data-stu-id="07924-111">Value</span></span>|<span data-ttu-id="07924-112">说明</span><span class="sxs-lookup"><span data-stu-id="07924-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="07924-113">*0*</span><span class="sxs-lookup"><span data-stu-id="07924-113">*0*</span></span>|<span data-ttu-id="07924-114">禁用 IPv4；客户端无法连接。</span><span class="sxs-lookup"><span data-stu-id="07924-114">IPv4 disabled; clients can't connect.</span></span>|  
|<span data-ttu-id="07924-115">*1*</span><span class="sxs-lookup"><span data-stu-id="07924-115">*1*</span></span>|<span data-ttu-id="07924-116">（默认值）要求使用 IPv4；如果服务器无法侦听 IPv4，则不启动服务器。</span><span class="sxs-lookup"><span data-stu-id="07924-116">(Default) IPv4 is required; server won't start if it cannot listen to IPv4.</span></span>|  
|<span data-ttu-id="07924-117">*2*</span><span class="sxs-lookup"><span data-stu-id="07924-117">*2*</span></span>|<span data-ttu-id="07924-118">IPv4 为可选项；服务器将尝试侦听 IPv4，但即使无法侦听，也会启动服务器。</span><span class="sxs-lookup"><span data-stu-id="07924-118">IPv4 is optional; server tries to listen to IPv4 but starts even if unable to.</span></span>|  
  
 `IPV6Support`  
 <span data-ttu-id="07924-119">有符号 32 位整数属性，用于定义 IPv6 协议支持。</span><span class="sxs-lookup"><span data-stu-id="07924-119">A signed 32-bit integer property that defines support for IPv6 protocol.</span></span> <span data-ttu-id="07924-120">此属性具有下表所列的值之一：</span><span class="sxs-lookup"><span data-stu-id="07924-120">This property has one of the values listed in the following table:</span></span>  
  
|<span data-ttu-id="07924-121">值</span><span class="sxs-lookup"><span data-stu-id="07924-121">Value</span></span>|<span data-ttu-id="07924-122">说明</span><span class="sxs-lookup"><span data-stu-id="07924-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="07924-123">*0*</span><span class="sxs-lookup"><span data-stu-id="07924-123">*0*</span></span>|<span data-ttu-id="07924-124">禁用 IPv6；客户端无法连接。</span><span class="sxs-lookup"><span data-stu-id="07924-124">IPv6 disabled; clients can't connect.</span></span>|  
|<span data-ttu-id="07924-125">*1*</span><span class="sxs-lookup"><span data-stu-id="07924-125">*1*</span></span>|<span data-ttu-id="07924-126">（默认值）要求使用 IPv6；如果服务器无法侦听 IPv6，则不启动服务器。</span><span class="sxs-lookup"><span data-stu-id="07924-126">(Default) IPv6 is required; server won't start if it cannot listen to IPv6.</span></span>|  
|<span data-ttu-id="07924-127">*2*</span><span class="sxs-lookup"><span data-stu-id="07924-127">*2*</span></span>|<span data-ttu-id="07924-128">IPv6 为可选项；服务器将尝试侦听 IPv6，但即使无法侦听，也会启动服务器。</span><span class="sxs-lookup"><span data-stu-id="07924-128">IPv6 is optional; server tries to listen to IPv6 but starts even if unable to.</span></span>|  
  
 `MaxAllowedRequestSize`  
 <span data-ttu-id="07924-129">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="07924-129">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `RequestSizeThreshold`  
 <span data-ttu-id="07924-130">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="07924-130">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ServerReceiveTimeout`  
 <span data-ttu-id="07924-131">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="07924-131">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ServerSendTimeout`  
 <span data-ttu-id="07924-132">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="07924-132">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="requests"></a><span data-ttu-id="07924-133">请求</span><span class="sxs-lookup"><span data-stu-id="07924-133">Requests</span></span>  
 `EnableBinaryXML`  
 <span data-ttu-id="07924-134">布尔值属性，指定服务器是否识别二进制 xml 格式请求。</span><span class="sxs-lookup"><span data-stu-id="07924-134">A Boolean property that specifies whether the server will recognize requests binary xml format.</span></span>  
  
 `EnableCompression`  
 <span data-ttu-id="07924-135">布尔值属性，指定是否对请求启用压缩。</span><span class="sxs-lookup"><span data-stu-id="07924-135">A Boolean property that specifies whether compression is enabled for requests.</span></span>  
  
## <a name="responses"></a><span data-ttu-id="07924-136">响应</span><span class="sxs-lookup"><span data-stu-id="07924-136">Responses</span></span>  
 `CompressionLevel`  
 <span data-ttu-id="07924-137">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="07924-137">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `EnableBinaryXML`  
 <span data-ttu-id="07924-138">布尔值属性，指定是否启用服务器的二进制 xml 响应。</span><span class="sxs-lookup"><span data-stu-id="07924-138">A Boolean property that specifies whether the server is enabled for binary xml responses.</span></span>  
  
 `EnableCompression`  
 <span data-ttu-id="07924-139">布尔值属性，指定是否对客户端请求的响应启用压缩。</span><span class="sxs-lookup"><span data-stu-id="07924-139">A Boolean property that specifies whether compression is enabled for responses to client requests.</span></span>  
  
## <a name="tcp"></a><span data-ttu-id="07924-140">TCP</span><span class="sxs-lookup"><span data-stu-id="07924-140">TCP</span></span>  
 `InitialConnectTimeout`  
 <span data-ttu-id="07924-141">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="07924-141">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MaxCompletedReceiveCount`  
 <span data-ttu-id="07924-142">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="07924-142">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MaxPendingAcceptExCount`  
 <span data-ttu-id="07924-143">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="07924-143">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MaxPendingReceiveCount`  
 <span data-ttu-id="07924-144">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="07924-144">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MaxPendingSendCount`  
 <span data-ttu-id="07924-145">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="07924-145">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MinPendingAcceptExCount`  
 <span data-ttu-id="07924-146">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="07924-146">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MinPendingReceiveCount`  
 <span data-ttu-id="07924-147">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="07924-147">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ScatterReceiveMultiplier`  
 <span data-ttu-id="07924-148">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="07924-148">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\ DisableNonblockingMode`  
 <span data-ttu-id="07924-149">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="07924-149">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\ EnableLingerOnClose`  
 <span data-ttu-id="07924-150">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="07924-150">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\EnableNagleAlgorithm`  
 <span data-ttu-id="07924-151">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="07924-151">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\ LingerTimeout`  
 <span data-ttu-id="07924-152">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="07924-152">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\ ReceiveBufferSize`  
 <span data-ttu-id="07924-153">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="07924-153">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\ SendBufferSize`  
 <span data-ttu-id="07924-154">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="07924-154">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07924-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07924-155">See Also</span></span>  
 <span data-ttu-id="07924-156">[在 Analysis Services 中配置服务器属性](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="07924-156">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="07924-157">确定 Analysis Services 实例的服务器模式</span><span class="sxs-lookup"><span data-stu-id="07924-157">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
