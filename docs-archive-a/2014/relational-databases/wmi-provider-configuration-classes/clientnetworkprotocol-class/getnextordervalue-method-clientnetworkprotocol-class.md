---
title: GetNextOrderValue 方法 (ClientNetworkProtocol 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- GetNextOrderValue Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- GetNextOrderValue method
ms.assetid: d741dc5c-c225-43d9-a730-7ad664ac525f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bdc3eecd9e151d7da32a5fd65a90552c0743b3d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591803"
---
# <a name="getnextordervalue-method-clientnetworkprotocol-class"></a><span data-ttu-id="fac46-102">GetNextOrderValue 方法（ClientNetworkProtocol 类）</span><span class="sxs-lookup"><span data-stu-id="fac46-102">GetNextOrderValue Method (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="fac46-103">选择位于协议列表中的下一个位置的协议。</span><span class="sxs-lookup"><span data-stu-id="fac46-103">Selects the protocol that is in the next position in the list of protocols.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fac46-104">语法</span><span class="sxs-lookup"><span data-stu-id="fac46-104">Syntax</span></span>  
  
```  
  
object  
.GetNextOrderValue()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="fac46-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="fac46-105">Parts</span></span>  
 <span data-ttu-id="fac46-106">对象</span><span class="sxs-lookup"><span data-stu-id="fac46-106">*object*</span></span>  
 <span data-ttu-id="fac46-107">一个表示客户端使用的网络协议的[ClientNetworkProtocol 类](clientnetworkprotocol-class.md)对象 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fac46-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="fac46-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="fac46-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="fac46-109">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="fac46-109">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fac46-110">备注</span><span class="sxs-lookup"><span data-stu-id="fac46-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fac46-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fac46-111">See Also</span></span>  
 <span data-ttu-id="fac46-112">[配置客户端协议](https://technet.microsoft.com/library/ms181035.aspx) </span><span class="sxs-lookup"><span data-stu-id="fac46-112">[Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx) </span></span>  
 [<span data-ttu-id="fac46-113">配置客户端网络协议和网络库</span><span class="sxs-lookup"><span data-stu-id="fac46-113">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
