---
title: SetOrderValue 方法 (ClientNetworkProtocol 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetOrderValue Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetOrderValue method
ms.assetid: 15f693fd-37f6-41d9-9dab-d2c93db19895
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6839e85b6131c54e233d980c84a8727eeda2202a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591193"
---
# <a name="setordervalue-method-clientnetworkprotocol-class"></a><span data-ttu-id="2c9c9-102">SetOrderValue 方法（ClientNetworkProtocol 类）</span><span class="sxs-lookup"><span data-stu-id="2c9c9-102">SetOrderValue Method (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="2c9c9-103">从客户端协议列表中选择具有指定顺序值的协议。</span><span class="sxs-lookup"><span data-stu-id="2c9c9-103">Selects the protocol with the specified order value from the client protocol list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c9c9-104">语法</span><span class="sxs-lookup"><span data-stu-id="2c9c9-104">Syntax</span></span>  
  
```  
  
object  
.SetOrderValue(  
OrderValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="2c9c9-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="2c9c9-105">Parts</span></span>  
 <span data-ttu-id="2c9c9-106">对象</span><span class="sxs-lookup"><span data-stu-id="2c9c9-106">*object*</span></span>  
 <span data-ttu-id="2c9c9-107">一个表示 [客户端使用的网络协议的](clientnetworkprotocol-class.md) ClientNetworkProtocol 类 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 对象。</span><span class="sxs-lookup"><span data-stu-id="2c9c9-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="2c9c9-108">参数</span><span class="sxs-lookup"><span data-stu-id="2c9c9-108">Parameters</span></span>  
  
|<span data-ttu-id="2c9c9-109">参数</span><span class="sxs-lookup"><span data-stu-id="2c9c9-109">Parameter</span></span>|<span data-ttu-id="2c9c9-110">说明</span><span class="sxs-lookup"><span data-stu-id="2c9c9-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2c9c9-111">*OrderValue*</span><span class="sxs-lookup"><span data-stu-id="2c9c9-111">*OrderValue*</span></span>|<span data-ttu-id="2c9c9-112">一个设置顺序值的 u`int32` 值。</span><span class="sxs-lookup"><span data-stu-id="2c9c9-112">A u`int32` value that sets the order value.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="2c9c9-113">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="2c9c9-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="2c9c9-114">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="2c9c9-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c9c9-115">备注</span><span class="sxs-lookup"><span data-stu-id="2c9c9-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c9c9-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2c9c9-116">See Also</span></span>  
 [<span data-ttu-id="2c9c9-117">客户端协议属性（“顺序”选项卡）</span><span class="sxs-lookup"><span data-stu-id="2c9c9-117">Client Protocols Properties (Order Tab)</span></span>](https://technet.microsoft.com/library/ms187884.aspx)  
  
  
