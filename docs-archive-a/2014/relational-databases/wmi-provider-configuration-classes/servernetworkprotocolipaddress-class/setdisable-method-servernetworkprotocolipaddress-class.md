---
title: SetDisable 方法 (ServerNetworkProtocolIPAddress 类) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDisable Method (ServerNetworkProtocolIPAddress Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDisable method
ms.assetid: 7a7cc8cc-9fb8-4bf5-b483-2150d633ee10
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9fbe928de1144c3065ddabb07bfd48606fdcea51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687672"
---
# <a name="setdisable-method-servernetworkprotocolipaddress-class"></a><span data-ttu-id="bf162-102">SetDisable 方法（ServerNetworkProtocolIPAddress 类）</span><span class="sxs-lookup"><span data-stu-id="bf162-102">SetDisable Method (ServerNetworkProtocolIPAddress Class)</span></span>
  <span data-ttu-id="bf162-103">禁用 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="bf162-103">Disables the IP address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf162-104">语法</span><span class="sxs-lookup"><span data-stu-id="bf162-104">Syntax</span></span>  
  
```  
  
object  
.SetDisable()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="bf162-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="bf162-105">Parts</span></span>  
 <span data-ttu-id="bf162-106">对象</span><span class="sxs-lookup"><span data-stu-id="bf162-106">*object*</span></span>  
 <span data-ttu-id="bf162-107">[ServerNetworkProtocolIPAdress Class] servernetworkprotocolipaddress-class.md) 对象，该对象表示实例上的网络协议的 IP 地址 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="bf162-107">A [ServerNetworkProtocolIPAdress Class]servernetworkprotocolipaddress-class.md) object that represents an IP address for the network protocol on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="bf162-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="bf162-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="bf162-109">一个 uint32 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="bf162-109">A uint32 value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf162-110">备注</span><span class="sxs-lookup"><span data-stu-id="bf162-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf162-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bf162-111">See Also</span></span>  
 <span data-ttu-id="bf162-112">[配置服务器网络协议和网络库](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="bf162-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
