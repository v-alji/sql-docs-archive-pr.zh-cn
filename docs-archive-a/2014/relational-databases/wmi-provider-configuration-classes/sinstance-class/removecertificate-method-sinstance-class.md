---
title: RemoveCertificate 方法 (SInstance 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- RemoveCertificate Method (SInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- RemoveCertificate method
ms.assetid: 7e5dbafa-a634-4617-9622-510514fce0ce
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4b876cd75778d1da9c9a46f65f39b915ebee0552
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687635"
---
# <a name="removecertificate-method-sinstance-class"></a><span data-ttu-id="67697-102">RemoveCertificate 方法（SInstance 类）</span><span class="sxs-lookup"><span data-stu-id="67697-102">RemoveCertificate Method (SInstance Class)</span></span>
  <span data-ttu-id="67697-103">从 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]实例中删除当前安全证书。</span><span class="sxs-lookup"><span data-stu-id="67697-103">Removes the current security certificate from the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67697-104">语法</span><span class="sxs-lookup"><span data-stu-id="67697-104">Syntax</span></span>  
  
```  
  
object  
.RemoveCertificate()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="67697-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="67697-105">Parts</span></span>  
 <span data-ttu-id="67697-106">对象</span><span class="sxs-lookup"><span data-stu-id="67697-106">*object*</span></span>  
 <span data-ttu-id="67697-107">一个表示 [实例上的服务器设置的](sinstance-class.md) SInstance 类 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]对象。</span><span class="sxs-lookup"><span data-stu-id="67697-107">An [SInstance Class](sinstance-class.md) object that represents the server settings on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="67697-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="67697-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="67697-109">一个 uint32 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="67697-109">A uint32 value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67697-110">备注</span><span class="sxs-lookup"><span data-stu-id="67697-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67697-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67697-111">See Also</span></span>  
 <span data-ttu-id="67697-112">[配置服务器网络协议和网络库](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="67697-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
