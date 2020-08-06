---
title: SetBoolValue 方法 (SqlServiceAdvancedProperty 类) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- SetBoolValue Method (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetBoolValue method
ms.assetid: 5252b439-fce5-446a-8e57-99e3054bee69
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f0c7142d6f192e94e9850b3c1a8a9481dc15a222
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688691"
---
# <a name="setboolvalue-method-sqlserviceadvancedproperty-class"></a><span data-ttu-id="66f36-102">SetBoolValue 方法（SqlServiceAdvancedProperty 类）</span><span class="sxs-lookup"><span data-stu-id="66f36-102">SetBoolValue Method (SqlServiceAdvancedProperty Class)</span></span>
  <span data-ttu-id="66f36-103">设置属性的布尔值。</span><span class="sxs-lookup"><span data-stu-id="66f36-103">Sets the Boolean value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66f36-104">语法</span><span class="sxs-lookup"><span data-stu-id="66f36-104">Syntax</span></span>  
  
```  
  
object  
.SetBoolValue [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="66f36-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="66f36-105">Parts</span></span>  
 <span data-ttu-id="66f36-106">对象</span><span class="sxs-lookup"><span data-stu-id="66f36-106">*object*</span></span>  
 <span data-ttu-id="66f36-107">一个表示高级属性的 [SqlServiceAdvancedProperty 类](../wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="66f36-107">A [SqlServiceAdvancedProperty Class](../wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) object that represents an advanced property.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="66f36-108">参数</span><span class="sxs-lookup"><span data-stu-id="66f36-108">Parameters</span></span>  
  
|<span data-ttu-id="66f36-109">参数</span><span class="sxs-lookup"><span data-stu-id="66f36-109">Parameter</span></span>|<span data-ttu-id="66f36-110">说明</span><span class="sxs-lookup"><span data-stu-id="66f36-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="66f36-111">*BoolValue*</span><span class="sxs-lookup"><span data-stu-id="66f36-111">*BoolValue*</span></span>|<span data-ttu-id="66f36-112">一个指定高级属性的值的布尔值。</span><span class="sxs-lookup"><span data-stu-id="66f36-112">A Boolean value that specifies the value of the advanced property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="66f36-113">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="66f36-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="66f36-114">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="66f36-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66f36-115">备注</span><span class="sxs-lookup"><span data-stu-id="66f36-115">Remarks</span></span>  
 <span data-ttu-id="66f36-116">属性值类型必须为 Boolean，才能将属性设置为布尔值。</span><span class="sxs-lookup"><span data-stu-id="66f36-116">The property value type must be Boolean to set the property to a Boolean value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66f36-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="66f36-117">See Also</span></span>  
 <span data-ttu-id="66f36-118">[启动和停止服务](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="66f36-118">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
