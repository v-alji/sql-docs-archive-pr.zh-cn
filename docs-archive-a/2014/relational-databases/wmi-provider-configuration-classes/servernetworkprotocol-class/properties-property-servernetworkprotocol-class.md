---
title: Properties 属性 (ServerNetworkProtocol 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- Properties Property (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Properties property
ms.assetid: 6c971bfc-c277-4c1e-a06e-146dcc34e759
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 32d6ebf59d48639e3b65c60a726f6bd1bf4291f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576560"
---
# <a name="properties-property-servernetworkprotocol-class"></a><span data-ttu-id="c158d-102">Properties 属性（ServerNetworkProtocol 类）</span><span class="sxs-lookup"><span data-stu-id="c158d-102">Properties Property (ServerNetworkProtocol Class)</span></span>
  <span data-ttu-id="c158d-103">获取与服务器网络协议关联的属性。</span><span class="sxs-lookup"><span data-stu-id="c158d-103">Gets the properties associated with the server network protocol.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c158d-104">语法</span><span class="sxs-lookup"><span data-stu-id="c158d-104">Syntax</span></span>  
  
```  
  
object  
.Properties [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="c158d-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="c158d-105">Parts</span></span>  
 <span data-ttu-id="c158d-106">对象</span><span class="sxs-lookup"><span data-stu-id="c158d-106">*object*</span></span>  
 <span data-ttu-id="c158d-107">一个表示实例使用的网络协议的[ServerNetworkProtocol 类](servernetworkprotocol-class.md)对象 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c158d-107">A [ServerNetworkProtocol Class](servernetworkprotocol-class.md) object that represents the network protocol used by the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="c158d-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="c158d-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="c158d-109">一个[ServerNetworkProtocolProperty 类](../servernetworkprotocolproperty-class/servernetworkprotocolproperty-class.md)对象的数组，这些对象表示服务器网络协议支持的属性。</span><span class="sxs-lookup"><span data-stu-id="c158d-109">An array of [ServerNetworkProtocolProperty Class](../servernetworkprotocolproperty-class/servernetworkprotocolproperty-class.md) objects that represent the properties supported by the server network protocol.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c158d-110">备注</span><span class="sxs-lookup"><span data-stu-id="c158d-110">Remarks</span></span>  
  
