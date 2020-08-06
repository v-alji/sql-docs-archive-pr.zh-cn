---
title: SetStrValue 方法 (ClientNetworkProtocolProperty 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStrValue Method (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStrValue method
ms.assetid: 4ff80124-6e2e-4d96-a692-57c17b53c55e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f3c23eebdbe948e1b77c47ef56a04691fa391938
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693219"
---
# <a name="setstrvalue-method-clientnetworkprotocolproperty-class"></a><span data-ttu-id="95a49-102">SetStrValue 方法（ClientNetworkProtocolProperty 类）</span><span class="sxs-lookup"><span data-stu-id="95a49-102">SetStrValue Method (ClientNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="95a49-103">设置 PropertyIdx 属性引用的当前属性的字符串值[ (ClientNetworkProtocolProperty 类) ](clientnetworkprotocolproperty-class.md)值。</span><span class="sxs-lookup"><span data-stu-id="95a49-103">Sets the string value of the current property referenced by the [PropertyIdx Property (ClientNetworkProtocolProperty Class)](clientnetworkprotocolproperty-class.md) value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95a49-104">语法</span><span class="sxs-lookup"><span data-stu-id="95a49-104">Syntax</span></span>  
  
```  
  
object  
.SetStrValue(  
StrValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="95a49-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="95a49-105">Parts</span></span>  
 <span data-ttu-id="95a49-106">对象</span><span class="sxs-lookup"><span data-stu-id="95a49-106">*object*</span></span>  
 <span data-ttu-id="95a49-107">表示客户端使用的网络协议属性的[ClientNetworkProtocolProperty 类](clientnetworkprotocolproperty-class.md)对象 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="95a49-107">A [ClientNetworkProtocolProperty Class](clientnetworkprotocolproperty-class.md) object that represents an attribute of the network protocol used by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="95a49-108">参数</span><span class="sxs-lookup"><span data-stu-id="95a49-108">Parameters</span></span>  
  
|<span data-ttu-id="95a49-109">参数</span><span class="sxs-lookup"><span data-stu-id="95a49-109">Parameter</span></span>|<span data-ttu-id="95a49-110">说明</span><span class="sxs-lookup"><span data-stu-id="95a49-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="95a49-111">*StrValue*</span><span class="sxs-lookup"><span data-stu-id="95a49-111">*StrValue*</span></span>|<span data-ttu-id="95a49-112">一个指定当前属性的新值的字符串值。</span><span class="sxs-lookup"><span data-stu-id="95a49-112">A string value that specifies the new value of the current property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="95a49-113">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="95a49-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="95a49-114">一个 uint32 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="95a49-114">A uint32 value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95a49-115">备注</span><span class="sxs-lookup"><span data-stu-id="95a49-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a49-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="95a49-116">See Also</span></span>  
 [<span data-ttu-id="95a49-117">配置客户端协议</span><span class="sxs-lookup"><span data-stu-id="95a49-117">Configure Client Protocols</span></span>](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
