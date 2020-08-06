---
title: GetCurrentCertificate 方法 (ServerSettings 类) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- GetCurrentCertificate Method (ServerSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- GetCurrentCertificate method
ms.assetid: 450e33c6-91d4-420f-ab7c-1905111f5658
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b36a5fe7cd39da0f336d05fc4c450170fa21199d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687660"
---
# <a name="getcurrentcertificate-method-serversettings-class"></a><span data-ttu-id="a0700-102">GetCurrentCertificate 方法（ServerSettings 类）</span><span class="sxs-lookup"><span data-stu-id="a0700-102">GetCurrentCertificate Method (ServerSettings Class)</span></span>
  <span data-ttu-id="a0700-103">获取当前安全证书。</span><span class="sxs-lookup"><span data-stu-id="a0700-103">Gets the current security certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0700-104">语法</span><span class="sxs-lookup"><span data-stu-id="a0700-104">Syntax</span></span>  
  
```  
  
object  
.GetCurrentCertificate(  
SHA  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="a0700-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="a0700-105">Parts</span></span>  
 <span data-ttu-id="a0700-106">对象</span><span class="sxs-lookup"><span data-stu-id="a0700-106">*object*</span></span>  
 <span data-ttu-id="a0700-107">一个表示 `ServerSettings` 实例上的服务器设置的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 对象。</span><span class="sxs-lookup"><span data-stu-id="a0700-107">A `ServerSettings` object that represents the server settings on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="a0700-108">参数</span><span class="sxs-lookup"><span data-stu-id="a0700-108">Parameters</span></span>  
  
|<span data-ttu-id="a0700-109">参数</span><span class="sxs-lookup"><span data-stu-id="a0700-109">Parameter</span></span>|<span data-ttu-id="a0700-110">说明</span><span class="sxs-lookup"><span data-stu-id="a0700-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a0700-111">*SHA*</span><span class="sxs-lookup"><span data-stu-id="a0700-111">*SHA*</span></span>|<span data-ttu-id="a0700-112">一个在方法完成后指定当前安全证书的字符串对象值（输出参数）。</span><span class="sxs-lookup"><span data-stu-id="a0700-112">A string object value (output parameter) that specifies the current security certificate after the method completes.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="a0700-113">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="a0700-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="a0700-114">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="a0700-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0700-115">备注</span><span class="sxs-lookup"><span data-stu-id="a0700-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0700-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a0700-116">See Also</span></span>  
 <span data-ttu-id="a0700-117">[配置服务器网络协议和网络库](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a0700-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
