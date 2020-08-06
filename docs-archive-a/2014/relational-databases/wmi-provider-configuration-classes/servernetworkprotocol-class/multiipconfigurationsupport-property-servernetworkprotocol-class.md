---
title: MultiIpConfigurationSupport 属性 (ServerNetworkProtocol 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- MultiIpConfigurationSupport Property (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- MultiIpConfigurationSupport property
ms.assetid: 442c6133-4038-42db-a67d-2631285ac76b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 80401a607c9155451a869082162affcca401ebca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576563"
---
# <a name="multiipconfigurationsupport-property-servernetworkprotocol-class"></a><span data-ttu-id="57fc4-102">MultiIpConfigurationSupport 属性（ServerNetworkProtocol 类）</span><span class="sxs-lookup"><span data-stu-id="57fc4-102">MultiIpConfigurationSupport Property (ServerNetworkProtocol Class)</span></span>
  <span data-ttu-id="57fc4-103">获取用于指定服务器网络协议是否支持多个 IP 地址的布尔值属性。</span><span class="sxs-lookup"><span data-stu-id="57fc4-103">Gets the Boolean property that specifies whether multiple IP addresses are supported by a server network protocol.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57fc4-104">语法</span><span class="sxs-lookup"><span data-stu-id="57fc4-104">Syntax</span></span>  
  
```  
  
object  
.MultiIpConfigurationSupport [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="57fc4-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="57fc4-105">Parts</span></span>  
 <span data-ttu-id="57fc4-106">对象</span><span class="sxs-lookup"><span data-stu-id="57fc4-106">*object*</span></span>  
 <span data-ttu-id="57fc4-107">[ProtocolName 属性 (ServerNetworkProtocol 类) ](servernetworkprotocol-class.md)对象，该对象表示实例使用的网络协议 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="57fc4-107">A [ProtocolName Property (ServerNetworkProtocol Class)](servernetworkprotocol-class.md) object that represents the network protocol used by the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="57fc4-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="57fc4-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="57fc4-109">一个指定服务器网络协议是否支持多个 IP 地址的布尔值：如果服务器网络协议支持多个 IP 地址，则为 `true`；如果服务器网络协议不支持多个 IP 地址，则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="57fc4-109">A Boolean value that specifies whether multiple IP addresses are supported by the server network protocol: `true` if multiple IP addresses are supported by the server network protocol, or `false` if multiple IP addresses are not supported by the server network protocol.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57fc4-110">备注</span><span class="sxs-lookup"><span data-stu-id="57fc4-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57fc4-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57fc4-111">See Also</span></span>  
 <span data-ttu-id="57fc4-112">[配置服务器网络协议和网络库](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="57fc4-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
