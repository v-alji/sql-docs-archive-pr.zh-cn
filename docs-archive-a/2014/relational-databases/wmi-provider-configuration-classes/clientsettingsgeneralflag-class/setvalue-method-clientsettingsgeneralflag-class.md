---
title: SetValue 方法 (ClientSettingsGeneralFlag 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetValue Method (ClientSettingsGeneralFlag Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetValue method
ms.assetid: 34443689-a0e0-4668-a811-17532c6fd271
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fffa44bd8743f96a43ca4d1787d8d2afaad5e6cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687703"
---
# <a name="setvalue-method-clientsettingsgeneralflag-class"></a><span data-ttu-id="93cd5-102">SetValue 方法（ClientSettingsGeneralFlag 类）</span><span class="sxs-lookup"><span data-stu-id="93cd5-102">SetValue Method (ClientSettingsGeneralFlag Class)</span></span>
  <span data-ttu-id="93cd5-103">设置引用的标志的所有值。</span><span class="sxs-lookup"><span data-stu-id="93cd5-103">Sets all the values of the referenced flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93cd5-104">语法</span><span class="sxs-lookup"><span data-stu-id="93cd5-104">Syntax</span></span>  
  
```  
  
object  
.SetValue(  
Value  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="93cd5-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="93cd5-105">Parts</span></span>  
 <span data-ttu-id="93cd5-106">对象</span><span class="sxs-lookup"><span data-stu-id="93cd5-106">*object*</span></span>  
 <span data-ttu-id="93cd5-107">一个表示服务器设置的常规标志的 [ClientSettingsGeneralFlag 类](clientsettingsgeneralflag-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="93cd5-107">A [ClientSettingsGeneralFlag Class](clientsettingsgeneralflag-class.md) object that represents a general flag for the server settings.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="93cd5-108">参数</span><span class="sxs-lookup"><span data-stu-id="93cd5-108">Parameters</span></span>  
  
|<span data-ttu-id="93cd5-109">参数</span><span class="sxs-lookup"><span data-stu-id="93cd5-109">Parameter</span></span>|<span data-ttu-id="93cd5-110">说明</span><span class="sxs-lookup"><span data-stu-id="93cd5-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93cd5-111">*值*</span><span class="sxs-lookup"><span data-stu-id="93cd5-111">*Value*</span></span>|<span data-ttu-id="93cd5-112">一个指定标志的值的布尔值。</span><span class="sxs-lookup"><span data-stu-id="93cd5-112">A Boolean value that specifies the value of the flag.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="93cd5-113">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="93cd5-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="93cd5-114">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="93cd5-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93cd5-115">备注</span><span class="sxs-lookup"><span data-stu-id="93cd5-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93cd5-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="93cd5-116">See Also</span></span>  
 [<span data-ttu-id="93cd5-117">配置客户端协议</span><span class="sxs-lookup"><span data-stu-id="93cd5-117">Configure Client Protocols</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
