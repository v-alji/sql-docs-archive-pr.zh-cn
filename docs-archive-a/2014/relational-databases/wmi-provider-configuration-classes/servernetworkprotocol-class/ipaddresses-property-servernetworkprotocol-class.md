---
title: IpAddresses 属性 (ServerNetworkProtocol 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- IpAddresses Property (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- IpAddresses property
ms.assetid: e5d66f7e-9719-436e-b723-12d56f914a05
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b94c4c11327abc1f02bd1e99c414f806f75bc145
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576564"
---
# <a name="ipaddresses-property-servernetworkprotocol-class"></a><span data-ttu-id="ef329-102">IpAddresses 属性（ServerNetworkProtocol 类）</span><span class="sxs-lookup"><span data-stu-id="ef329-102">IpAddresses Property (ServerNetworkProtocol Class)</span></span>
  <span data-ttu-id="ef329-103">获取与服务器网络协议关联的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="ef329-103">Gets the IP addresses associated with the server network protocol.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef329-104">语法</span><span class="sxs-lookup"><span data-stu-id="ef329-104">Syntax</span></span>  
  
```  
  
object  
.IpAddresses [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="ef329-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="ef329-105">Parts</span></span>  
 <span data-ttu-id="ef329-106">对象</span><span class="sxs-lookup"><span data-stu-id="ef329-106">*object*</span></span>  
 <span data-ttu-id="ef329-107">一个 `ServerNetworkProtocol` 对象，该对象表示实例使用的网络协议 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ef329-107">A `ServerNetworkProtocol` object that represents the network protocol used by the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="ef329-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="ef329-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="ef329-109">一个[ServerNetworkProtocolIPAdress 类](../servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md)对象的数组，这些对象表示服务器网络协议支持的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="ef329-109">An array of [ServerNetworkProtocolIPAdress Class](../servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md) objects that represent the IP addresses supported by the server network protocol.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef329-110">备注</span><span class="sxs-lookup"><span data-stu-id="ef329-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef329-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef329-111">See Also</span></span>  
 <span data-ttu-id="ef329-112">[配置服务器网络协议和网络库](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="ef329-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
