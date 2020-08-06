---
title: SupportAlias 属性 (ClientNetworkProtocol 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SupportAlias Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SupportAlias property
ms.assetid: 1e7a2e87-c356-40a6-a6d9-e492467629f9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6fd06ad0921dbb113a89af77e46733a28c2226c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591187"
---
# <a name="supportalias-property-clientnetworkprotocol-class"></a><span data-ttu-id="cebf1-102">SupportAlias 属性（ClientNetworkProtocol Class）</span><span class="sxs-lookup"><span data-stu-id="cebf1-102">SupportAlias Property (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="cebf1-103">获取一个布尔属性，该属性指定由 SetOrderValue 方法指定的当前网络协议是否[ (ClientNetworkProtocol 类) ](clientnetworkprotocol-class.md)支持别名。</span><span class="sxs-lookup"><span data-stu-id="cebf1-103">Gets the Boolean property that specifies whether the current network protocol specified by the [SetOrderValue Method (ClientNetworkProtocol Class)](clientnetworkprotocol-class.md) support aliases.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cebf1-104">语法</span><span class="sxs-lookup"><span data-stu-id="cebf1-104">Syntax</span></span>  
  
```  
  
object  
.SupportAlias [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="cebf1-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="cebf1-105">Parts</span></span>  
 <span data-ttu-id="cebf1-106">对象</span><span class="sxs-lookup"><span data-stu-id="cebf1-106">*object*</span></span>  
 <span data-ttu-id="cebf1-107">一个表示 [客户端使用的网络协议的](clientnetworkprotocol-class.md) ClientNetworkProtocol 类 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 对象。</span><span class="sxs-lookup"><span data-stu-id="cebf1-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="cebf1-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="cebf1-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="cebf1-109">一个指定客户端网络协议是否支持别名的布尔值。</span><span class="sxs-lookup"><span data-stu-id="cebf1-109">A Boolean value that specifies whether the client network protocol supports aliases.</span></span>  
  
 <span data-ttu-id="cebf1-110">如果为 True，则客户端网络协议支持别名。</span><span class="sxs-lookup"><span data-stu-id="cebf1-110">If True, the client network protocol supports aliases.</span></span>  
  
 <span data-ttu-id="cebf1-111">如果为 False，则客户端网络协议不支持别名。</span><span class="sxs-lookup"><span data-stu-id="cebf1-111">If False, the client network protocol does not support aliases.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cebf1-112">备注</span><span class="sxs-lookup"><span data-stu-id="cebf1-112">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cebf1-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cebf1-113">See Also</span></span>  
 [<span data-ttu-id="cebf1-114">配置客户端协议</span><span class="sxs-lookup"><span data-stu-id="cebf1-114">Configure Client Protocols</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
