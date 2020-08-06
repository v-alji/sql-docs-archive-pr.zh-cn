---
title: RemoveCertificate 方法 (ServerSettings 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- RemoveCertificate Method (ServerSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- RemoveCertificate method
ms.assetid: 9ffdbc39-93f5-48fb-859a-86a3ad545827
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 00731fab5c4bdec61848df93829dd5013a7454f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687639"
---
# <a name="removecertificate-method-serversettings-class"></a><span data-ttu-id="ed14f-102">RemoveCertificate 方法（ServerSettings 类）</span><span class="sxs-lookup"><span data-stu-id="ed14f-102">RemoveCertificate Method (ServerSettings Class)</span></span>
  <span data-ttu-id="ed14f-103">从 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]实例中删除当前安全证书。</span><span class="sxs-lookup"><span data-stu-id="ed14f-103">Removes the current security certificate from the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed14f-104">语法</span><span class="sxs-lookup"><span data-stu-id="ed14f-104">Syntax</span></span>  
  
```  
  
object  
.RemoveCertificate()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="ed14f-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="ed14f-105">Parts</span></span>  
 <span data-ttu-id="ed14f-106">对象</span><span class="sxs-lookup"><span data-stu-id="ed14f-106">*object*</span></span>  
 <span data-ttu-id="ed14f-107">一个表示 [实例上的服务器设置的](serversettings-class.md) ServerSettings 类 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]对象。</span><span class="sxs-lookup"><span data-stu-id="ed14f-107">A [ServerSettings Class](serversettings-class.md) object that represents the server settings on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="ed14f-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="ed14f-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="ed14f-109">一个 u`int32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="ed14f-109">A u`int32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed14f-110">备注</span><span class="sxs-lookup"><span data-stu-id="ed14f-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed14f-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ed14f-111">See Also</span></span>  
 <span data-ttu-id="ed14f-112">[配置服务器网络协议和网络库](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="ed14f-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
