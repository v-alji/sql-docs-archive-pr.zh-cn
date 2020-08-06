---
title: SetProtocolsOrder 方法 (ClientNetworkProtocol 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetProtocolsOrder Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetProtocolsOrder method
ms.assetid: b86d98b9-aae4-4e74-b4da-1ec984d5c8b4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: aaa1d43c8a2f7f210f61761b28313a93ac6c7a90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591189"
---
# <a name="setprotocolsorder-method-clientnetworkprotocol-class"></a><span data-ttu-id="caacf-102">SetProtocolsOrder 方法（ClientNetworkProtocol 类）</span><span class="sxs-lookup"><span data-stu-id="caacf-102">SetProtocolsOrder Method (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="caacf-103">更改协议列表的顺序。</span><span class="sxs-lookup"><span data-stu-id="caacf-103">Changes the order of the protocol list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caacf-104">语法</span><span class="sxs-lookup"><span data-stu-id="caacf-104">Syntax</span></span>  
  
```  
  
object  
.SetProtocolsOrder(  
ProtocolOrderList  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="caacf-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="caacf-105">Parts</span></span>  
 <span data-ttu-id="caacf-106">对象</span><span class="sxs-lookup"><span data-stu-id="caacf-106">*object*</span></span>  
 <span data-ttu-id="caacf-107">一个表示客户端使用的网络协议的[ClientNetworkProtocol 类](clientnetworkprotocol-class.md)对象 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="caacf-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="caacf-108">参数</span><span class="sxs-lookup"><span data-stu-id="caacf-108">Parameters</span></span>  
  
|<span data-ttu-id="caacf-109">参数</span><span class="sxs-lookup"><span data-stu-id="caacf-109">Parameter</span></span>|<span data-ttu-id="caacf-110">说明</span><span class="sxs-lookup"><span data-stu-id="caacf-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="caacf-111">*ProtocolOrderList*</span><span class="sxs-lookup"><span data-stu-id="caacf-111">*ProtocolOrderList*</span></span>|<span data-ttu-id="caacf-112">一个以新的顺序列出客户端网络协议的字符串数组。</span><span class="sxs-lookup"><span data-stu-id="caacf-112">A string[] array that lists the client network protocols in the new order.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="caacf-113">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="caacf-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="caacf-114">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="caacf-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="caacf-115">备注</span><span class="sxs-lookup"><span data-stu-id="caacf-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caacf-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="caacf-116">See Also</span></span>  
 <span data-ttu-id="caacf-117">[配置客户端协议](https://technet.microsoft.com/library/ms181035.aspx) </span><span class="sxs-lookup"><span data-stu-id="caacf-117">[Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx) </span></span>  
 [<span data-ttu-id="caacf-118">配置客户端网络协议和网络库</span><span class="sxs-lookup"><span data-stu-id="caacf-118">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
