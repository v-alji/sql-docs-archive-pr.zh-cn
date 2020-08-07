---
title: SetDisable 方法 (ServerNetworkProtocol 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDisable Method (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDisable method
ms.assetid: 0ebbe0c5-07ad-4a76-a918-e379930adf71
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3176227aba4de1e5aca1be35ec1f071a15caa49e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580089"
---
# <a name="setdisable-method-servernetworkprotocol-class"></a><span data-ttu-id="8182f-102">SetDisable 方法（ServerNetworkProtocol 类）</span><span class="sxs-lookup"><span data-stu-id="8182f-102">SetDisable Method (ServerNetworkProtocol Class)</span></span>
  <span data-ttu-id="8182f-103">禁用服务器网络协议。</span><span class="sxs-lookup"><span data-stu-id="8182f-103">Disables the server network protocol.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8182f-104">语法</span><span class="sxs-lookup"><span data-stu-id="8182f-104">Syntax</span></span>  
  
```  
  
object  
.SetDisable()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="8182f-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="8182f-105">Parts</span></span>  
 <span data-ttu-id="8182f-106">对象</span><span class="sxs-lookup"><span data-stu-id="8182f-106">*object*</span></span>  
 <span data-ttu-id="8182f-107">[ServerNetworkProtocol Class] ServerNetworkProtocol-class.md) 对象，该对象表示实例使用的网络协议 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8182f-107">A [ServerNetworkProtocol Class]servernetworkprotocol-class.md) object that represents the network protocol used by the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="8182f-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="8182f-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="8182f-109">一个 uint32 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="8182f-109">A uint32 value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8182f-110">备注</span><span class="sxs-lookup"><span data-stu-id="8182f-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8182f-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8182f-111">See Also</span></span>  
 <span data-ttu-id="8182f-112">[配置服务器网络协议和网络库](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="8182f-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
