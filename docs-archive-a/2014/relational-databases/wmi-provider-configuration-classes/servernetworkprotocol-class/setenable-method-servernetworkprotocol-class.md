---
title: SetEnable 方法 (ServerNetworkProtocol 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetEnable Method (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetEnable method
ms.assetid: a287950b-086f-4b6d-a2d8-4d3973bd1b21
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8f77b7a92fe226e349a03ffba03cfe8d67c280e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580087"
---
# <a name="setenable-method-servernetworkprotocol-class"></a><span data-ttu-id="13731-102">SetEnable 方法（ServerNetworkProtocol 类）</span><span class="sxs-lookup"><span data-stu-id="13731-102">SetEnable Method (ServerNetworkProtocol Class)</span></span>
  <span data-ttu-id="13731-103">启用服务器网络协议。</span><span class="sxs-lookup"><span data-stu-id="13731-103">Enables the server network protocol.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13731-104">语法</span><span class="sxs-lookup"><span data-stu-id="13731-104">Syntax</span></span>  
  
```  
  
object  
.SetEnable()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="13731-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="13731-105">Parts</span></span>  
 <span data-ttu-id="13731-106">对象</span><span class="sxs-lookup"><span data-stu-id="13731-106">*object*</span></span>  
 <span data-ttu-id="13731-107">一个表示实例使用的网络协议的[ServerNetworkProtocol 类](servernetworkprotocol-class.md)对象 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="13731-107">A [ServerNetworkProtocol Class](servernetworkprotocol-class.md) object that represents the network protocol used by the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="13731-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="13731-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="13731-109">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="13731-109">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13731-110">备注</span><span class="sxs-lookup"><span data-stu-id="13731-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13731-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="13731-111">See Also</span></span>  
 <span data-ttu-id="13731-112">[配置服务器网络协议和网络库](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="13731-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
