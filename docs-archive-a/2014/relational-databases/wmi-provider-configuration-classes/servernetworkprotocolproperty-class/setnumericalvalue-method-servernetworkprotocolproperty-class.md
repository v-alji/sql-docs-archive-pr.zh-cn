---
title: SetNumericalValue 方法 (ServerNetworkProtocolProperty 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetNumericalValue Method (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetNumericalValue method
ms.assetid: b3b4bce8-9d9e-4ccb-a223-0454281353b0
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f5a4b8d6819dae11abe4cc097f0e423c23d909e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586553"
---
# <a name="setnumericalvalue-method-servernetworkprotocolproperty-class"></a><span data-ttu-id="6279e-102">SetNumericalValue 方法（ServerNetworkProtocolProperty 类）</span><span class="sxs-lookup"><span data-stu-id="6279e-102">SetNumericalValue Method (ServerNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="6279e-103">设置引用的属性的数值。</span><span class="sxs-lookup"><span data-stu-id="6279e-103">Sets the numeric value of the referenced property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6279e-104">语法</span><span class="sxs-lookup"><span data-stu-id="6279e-104">Syntax</span></span>  
  
```  
  
object  
.SetNumericalValue(  
NumValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="6279e-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="6279e-105">Parts</span></span>  
 <span data-ttu-id="6279e-106">对象</span><span class="sxs-lookup"><span data-stu-id="6279e-106">*object*</span></span>  
 <span data-ttu-id="6279e-107">[ServerNetworkProtocolProperty Class] ServerNetworkProtocolProperty-class.md) 对象，该对象表示实例上的网络协议的属性 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6279e-107">A [ServerNetworkProtocolProperty Class]servernetworkprotocolproperty-class.md) object that represents an attribute of the network protocol on the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="6279e-108">参数</span><span class="sxs-lookup"><span data-stu-id="6279e-108">Parameters</span></span>  
  
|<span data-ttu-id="6279e-109">参数</span><span class="sxs-lookup"><span data-stu-id="6279e-109">Parameter</span></span>|<span data-ttu-id="6279e-110">说明</span><span class="sxs-lookup"><span data-stu-id="6279e-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6279e-111">*NumValue*</span><span class="sxs-lookup"><span data-stu-id="6279e-111">*NumValue*</span></span>|<span data-ttu-id="6279e-112">一个指定当前属性的新值的 `uint32` 值。</span><span class="sxs-lookup"><span data-stu-id="6279e-112">A `uint32` value that specifies the new value of the current property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="6279e-113">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="6279e-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="6279e-114">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="6279e-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6279e-115">备注</span><span class="sxs-lookup"><span data-stu-id="6279e-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6279e-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6279e-116">See Also</span></span>  
 <span data-ttu-id="6279e-117">[配置服务器网络协议和网络库](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="6279e-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
