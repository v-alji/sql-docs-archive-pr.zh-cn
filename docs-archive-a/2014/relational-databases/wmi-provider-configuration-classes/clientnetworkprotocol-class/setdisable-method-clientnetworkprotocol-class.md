---
title: SetDisable 方法 (ClientNetworkProtocol 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDisable Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDisable method
ms.assetid: bce69ab9-ea5b-43fd-8114-08b1b5890755
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2bad312f1f7c7e9540acdaf3dd46df78b953d4ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591798"
---
# <a name="setdisable-method-clientnetworkprotocol-class"></a><span data-ttu-id="5b31f-102">SetDisable 方法（ClientNetworkProtocol 类）</span><span class="sxs-lookup"><span data-stu-id="5b31f-102">SetDisable Method (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="5b31f-103">禁用[配置客户端协议](https://technet.microsoft.com/library/ms181035.aspx)指定的客户端网络协议。</span><span class="sxs-lookup"><span data-stu-id="5b31f-103">Disables the client network protocol that is specified by the [Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b31f-104">语法</span><span class="sxs-lookup"><span data-stu-id="5b31f-104">Syntax</span></span>  
  
```  
  
object  
.SetDisable()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="5b31f-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="5b31f-105">Parts</span></span>  
 <span data-ttu-id="5b31f-106">对象</span><span class="sxs-lookup"><span data-stu-id="5b31f-106">*object*</span></span>  
 <span data-ttu-id="5b31f-107">一个表示客户端使用的网络协议的[ClientNetworkProtocol 类](clientnetworkprotocol-class.md)对象 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5b31f-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="5b31f-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="5b31f-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="5b31f-109">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="5b31f-109">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b31f-110">备注</span><span class="sxs-lookup"><span data-stu-id="5b31f-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b31f-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b31f-111">See Also</span></span>  
 [<span data-ttu-id="5b31f-112">配置客户端网络协议和网络库</span><span class="sxs-lookup"><span data-stu-id="5b31f-112">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
