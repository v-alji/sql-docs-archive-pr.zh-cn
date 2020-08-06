---
title: Properties 属性 (ClientNetworkProtocol 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- Properties Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Properties property
ms.assetid: 7e0a4e38-4555-4750-8fd3-4425b29e6aa1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 09836db1f510ac77635924c51e5341686627d54d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591801"
---
# <a name="properties-property-clientnetworkprotocol-class"></a><span data-ttu-id="73832-102">Properties 属性（ClientNetworkProtocol 类）</span><span class="sxs-lookup"><span data-stu-id="73832-102">Properties Property (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="73832-103">获取与[配置客户端协议](https://technet.microsoft.com/library/ms181035.aspx)指定的当前客户端网络协议关联的属性。</span><span class="sxs-lookup"><span data-stu-id="73832-103">Gets the properties associated with the current client network protocol specified by the [Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73832-104">语法</span><span class="sxs-lookup"><span data-stu-id="73832-104">Syntax</span></span>  
  
```  
  
object  
.Properties [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="73832-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="73832-105">Parts</span></span>  
 <span data-ttu-id="73832-106">对象</span><span class="sxs-lookup"><span data-stu-id="73832-106">*object*</span></span>  
 <span data-ttu-id="73832-107">一个表示 [客户端使用的网络协议的](clientnetworkprotocol-class.md) ClientNetworkProtocol 类 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 对象。</span><span class="sxs-lookup"><span data-stu-id="73832-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="73832-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="73832-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="73832-109">一个[ClientNetworkProtocolProperty 类](../clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md)对象的数组，这些对象表示属性引用的当前客户端网络协议支持的属性 `OrderValue` 。</span><span class="sxs-lookup"><span data-stu-id="73832-109">An array of [ClientNetworkProtocolProperty Class](../clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) objects that represent the properties supported by the current client network protocol that is referenced by the `OrderValue` property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73832-110">备注</span><span class="sxs-lookup"><span data-stu-id="73832-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73832-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="73832-111">See Also</span></span>  
 [<span data-ttu-id="73832-112">配置客户端网络协议和网络库</span><span class="sxs-lookup"><span data-stu-id="73832-112">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
