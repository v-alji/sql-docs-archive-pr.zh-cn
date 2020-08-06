---
title: SetStringValue 方法 (ServerNetworkProtocolProperty 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStringValue Method (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStringValue method
ms.assetid: 0911df30-55f7-4fca-a1fb-01d2c91c1467
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8eb4a27d700d801e3ca94362663c6d7feaa7dc86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687664"
---
# <a name="setstringvalue-method-servernetworkprotocolproperty-class"></a><span data-ttu-id="af042-102">SetStringValue 方法（ServerNetworkProtocolProperty 类）</span><span class="sxs-lookup"><span data-stu-id="af042-102">SetStringValue Method (ServerNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="af042-103">设置引用的属性的字符串值。</span><span class="sxs-lookup"><span data-stu-id="af042-103">Sets the string value of the referenced property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af042-104">语法</span><span class="sxs-lookup"><span data-stu-id="af042-104">Syntax</span></span>  
  
```  
  
object  
.SetStringValue(  
StrValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="af042-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="af042-105">Parts</span></span>  
 <span data-ttu-id="af042-106">对象</span><span class="sxs-lookup"><span data-stu-id="af042-106">*object*</span></span>  
 <span data-ttu-id="af042-107">一个表示实例上的网络协议属性的[ServerNetworkProtocolProperty 类](servernetworkprotocolproperty-class.md)对象 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="af042-107">A [ServerNetworkProtocolProperty Class](servernetworkprotocolproperty-class.md) object that represents an attribute of the network protocol on the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="af042-108">参数</span><span class="sxs-lookup"><span data-stu-id="af042-108">Parameters</span></span>  
  
|<span data-ttu-id="af042-109">参数</span><span class="sxs-lookup"><span data-stu-id="af042-109">Parameter</span></span>|<span data-ttu-id="af042-110">说明</span><span class="sxs-lookup"><span data-stu-id="af042-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="af042-111">*StrValue*</span><span class="sxs-lookup"><span data-stu-id="af042-111">*StrValue*</span></span>|<span data-ttu-id="af042-112">一个指定当前属性的新值的字符串值。</span><span class="sxs-lookup"><span data-stu-id="af042-112">A string value that specifies the new value of the current property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="af042-113">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="af042-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="af042-114">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="af042-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af042-115">备注</span><span class="sxs-lookup"><span data-stu-id="af042-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af042-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="af042-116">See Also</span></span>  
 <span data-ttu-id="af042-117">[配置服务器网络协议和网络库](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="af042-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
