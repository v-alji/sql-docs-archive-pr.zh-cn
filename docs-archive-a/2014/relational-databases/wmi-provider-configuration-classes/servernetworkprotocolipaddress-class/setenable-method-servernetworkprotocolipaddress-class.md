---
title: SetEnable 方法 (ServerNetworkProtocolIPAddress 类) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetEnable Method (ServerNetworkProtocolIPAddress Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetEnable method
ms.assetid: baa86deb-95dd-416f-b2c7-cec1dfb91ab4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5be9c30acacaedba320fd68363e531b178918271
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587728"
---
# <a name="setenable-method-servernetworkprotocolipaddress-class"></a><span data-ttu-id="f5017-102">SetEnable 方法（ServerNetworkProtocolIPAddress 类）</span><span class="sxs-lookup"><span data-stu-id="f5017-102">SetEnable Method (ServerNetworkProtocolIPAddress Class)</span></span>
  <span data-ttu-id="f5017-103">启用 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f5017-103">Enables the IP address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5017-104">语法</span><span class="sxs-lookup"><span data-stu-id="f5017-104">Syntax</span></span>  
  
```  
  
object  
.SetEnable()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="f5017-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="f5017-105">Parts</span></span>  
 <span data-ttu-id="f5017-106">对象</span><span class="sxs-lookup"><span data-stu-id="f5017-106">*object*</span></span>  
 <span data-ttu-id="f5017-107">一个表示实例上的网络协议 IP 地址的[ServerNetworkProtocolIPAdress 类](servernetworkprotocolipaddress-class.md)对象 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f5017-107">A [ServerNetworkProtocolIPAdress Class](servernetworkprotocolipaddress-class.md) object that represents an IP address for the network protocol on the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="f5017-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="f5017-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="f5017-109">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="f5017-109">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5017-110">备注</span><span class="sxs-lookup"><span data-stu-id="f5017-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5017-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f5017-111">See Also</span></span>  
 <span data-ttu-id="f5017-112">[配置服务器网络协议和网络库](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="f5017-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
