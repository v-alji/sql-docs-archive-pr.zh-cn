---
title: SetFlag 方法 (ServerNetworkProtocolProperty 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetFlag Method (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetFlag method
ms.assetid: 95288931-8eb1-4477-ad80-619cf7073e61
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1a90b4fca194f20cc0a2d70c947577594155f051
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688675"
---
# <a name="setflag-method-servernetworkprotocolproperty-class"></a><span data-ttu-id="5d511-102">SetFlag 方法（ServerNetworkProtocolProperty 类）</span><span class="sxs-lookup"><span data-stu-id="5d511-102">SetFlag Method (ServerNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="5d511-103">设置引用的属性的标志。</span><span class="sxs-lookup"><span data-stu-id="5d511-103">Sets the flag of the referenced property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d511-104">语法</span><span class="sxs-lookup"><span data-stu-id="5d511-104">Syntax</span></span>  
  
```  
  
object  
.SetFlag(  
BoolValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="5d511-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="5d511-105">Parts</span></span>  
 <span data-ttu-id="5d511-106">对象</span><span class="sxs-lookup"><span data-stu-id="5d511-106">*object*</span></span>  
 <span data-ttu-id="5d511-107">[ServerNetworkProtocolProperty Class] ServerNetworkProtocolProperty-class.md) 对象，该对象表示实例上的网络协议的属性 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5d511-107">A [ServerNetworkProtocolProperty Class]servernetworkprotocolproperty-class.md) object that represents an attribute of the network protocol on the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="5d511-108">参数</span><span class="sxs-lookup"><span data-stu-id="5d511-108">Parameters</span></span>  
  
|<span data-ttu-id="5d511-109">参数</span><span class="sxs-lookup"><span data-stu-id="5d511-109">Parameter</span></span>|<span data-ttu-id="5d511-110">说明</span><span class="sxs-lookup"><span data-stu-id="5d511-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5d511-111">*BoolValue*</span><span class="sxs-lookup"><span data-stu-id="5d511-111">*BoolValue*</span></span>|<span data-ttu-id="5d511-112">一个指定标志的新值的布尔值。</span><span class="sxs-lookup"><span data-stu-id="5d511-112">A Boolean value that specifies the new value of the flag.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="5d511-113">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="5d511-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="5d511-114">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="5d511-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d511-115">备注</span><span class="sxs-lookup"><span data-stu-id="5d511-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d511-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5d511-116">See Also</span></span>  
 <span data-ttu-id="5d511-117">[配置服务器网络协议和网络库](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="5d511-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
