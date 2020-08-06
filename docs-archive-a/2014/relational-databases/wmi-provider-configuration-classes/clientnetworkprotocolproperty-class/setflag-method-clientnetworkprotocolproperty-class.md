---
title: SetFlag 方法 (ClientNetworkProtocolProperty 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetFlag Method (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetFlag method
ms.assetid: 0407520f-2f84-4f68-b2b7-429697286c1b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1c83a1d647b62f0e5c5acf0659d54bf787bf0c96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692325"
---
# <a name="setflag-method-clientnetworkprotocolproperty-class"></a><span data-ttu-id="c71b2-102">SetFlag 方法（ClientNetworkProtocolProperty 类）</span><span class="sxs-lookup"><span data-stu-id="c71b2-102">SetFlag Method (ClientNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="c71b2-103">设置 PropertyIdx 属性引用的当前属性的标志[ (ClientNetworkProtocolProperty 类) ](clientnetworkprotocolproperty-class.md)值。</span><span class="sxs-lookup"><span data-stu-id="c71b2-103">Sets the flag of the current property referenced by the [PropertyIdx Property (ClientNetworkProtocolProperty Class)](clientnetworkprotocolproperty-class.md) value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c71b2-104">语法</span><span class="sxs-lookup"><span data-stu-id="c71b2-104">Syntax</span></span>  
  
```  
  
object  
.SetFlag(  
BoolValue  
) [=]  
```  
  
## <a name="parts"></a><span data-ttu-id="c71b2-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="c71b2-105">Parts</span></span>  
 <span data-ttu-id="c71b2-106">对象</span><span class="sxs-lookup"><span data-stu-id="c71b2-106">*object*</span></span>  
 <span data-ttu-id="c71b2-107">表示客户端使用的网络协议属性的[ClientNetworkProtocolProperty 类](clientnetworkprotocolproperty-class.md)对象 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c71b2-107">A [ClientNetworkProtocolProperty Class](clientnetworkprotocolproperty-class.md) object that represents an attribute of the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="c71b2-108">参数</span><span class="sxs-lookup"><span data-stu-id="c71b2-108">Parameters</span></span>  
  
|<span data-ttu-id="c71b2-109">参数</span><span class="sxs-lookup"><span data-stu-id="c71b2-109">Parameter</span></span>|<span data-ttu-id="c71b2-110">说明</span><span class="sxs-lookup"><span data-stu-id="c71b2-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c71b2-111">*BoolValue*</span><span class="sxs-lookup"><span data-stu-id="c71b2-111">*BoolValue*</span></span>|<span data-ttu-id="c71b2-112">一个指定标志的新值的布尔值。</span><span class="sxs-lookup"><span data-stu-id="c71b2-112">A Boolean value that specifies the new value of the flag.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="c71b2-113">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="c71b2-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="c71b2-114">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="c71b2-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c71b2-115">备注</span><span class="sxs-lookup"><span data-stu-id="c71b2-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c71b2-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c71b2-116">See Also</span></span>  
 [<span data-ttu-id="c71b2-117">配置客户端协议</span><span class="sxs-lookup"><span data-stu-id="c71b2-117">Configure Client Protocols</span></span>](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
