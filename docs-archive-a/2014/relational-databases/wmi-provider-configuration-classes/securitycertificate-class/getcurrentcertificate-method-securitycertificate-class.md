---
title: GetCurrentCertificate 方法 (SecurityCertificate 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- GetCurrentCertificate Method (SecurityCertificate Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- GetCurrentCertificate method
ms.assetid: 987a2671-1801-45c4-93e6-29f883c58720
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ab96b2e2a8fabf9e9ccce647e54be1983fe40ca0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687679"
---
# <a name="getcurrentcertificate-method-securitycertificate-class"></a><span data-ttu-id="677ee-102">GetCurrentCertificate 方法（SecurityCertificate 类）</span><span class="sxs-lookup"><span data-stu-id="677ee-102">GetCurrentCertificate Method (SecurityCertificate Class)</span></span>
  <span data-ttu-id="677ee-103">获取当前安全证书。</span><span class="sxs-lookup"><span data-stu-id="677ee-103">Gets the current security certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="677ee-104">语法</span><span class="sxs-lookup"><span data-stu-id="677ee-104">Syntax</span></span>  
  
```  
  
object  
.GetCurrentCertificate(  
SHA , SQLInstance  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="677ee-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="677ee-105">Parts</span></span>  
 <span data-ttu-id="677ee-106">对象</span><span class="sxs-lookup"><span data-stu-id="677ee-106">*object*</span></span>  
 <span data-ttu-id="677ee-107">一个表示安全证书的 [SecurityCertificate 类](securitycertificate-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="677ee-107">A [SecurityCertificate Class](securitycertificate-class.md) object that represents a security certificate.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="677ee-108">参数</span><span class="sxs-lookup"><span data-stu-id="677ee-108">Parameters</span></span>  
  
|<span data-ttu-id="677ee-109">参数</span><span class="sxs-lookup"><span data-stu-id="677ee-109">Parameter</span></span>|<span data-ttu-id="677ee-110">说明</span><span class="sxs-lookup"><span data-stu-id="677ee-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="677ee-111">*SHA*</span><span class="sxs-lookup"><span data-stu-id="677ee-111">*SHA*</span></span>|<span data-ttu-id="677ee-112">一个在方法完成后指定当前安全证书 SHA 指纹的字符串值（输出参数）。</span><span class="sxs-lookup"><span data-stu-id="677ee-112">A string value (output parameter) that specifies the current security certificate SHA thumbprint after the method completes.</span></span>|  
|<span data-ttu-id="677ee-113">*SQLInstance*</span><span class="sxs-lookup"><span data-stu-id="677ee-113">*SQLInstance*</span></span>|<span data-ttu-id="677ee-114">一个为所需证书指定实例的字符串值。</span><span class="sxs-lookup"><span data-stu-id="677ee-114">A string value that specifies the instance for which the certificate is required.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="677ee-115">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="677ee-115">Property Value/Return Value</span></span>  
 <span data-ttu-id="677ee-116">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="677ee-116">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="677ee-117">备注</span><span class="sxs-lookup"><span data-stu-id="677ee-117">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="677ee-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="677ee-118">See Also</span></span>  
 <span data-ttu-id="677ee-119">[配置服务器网络协议和网络库](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="677ee-119">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
