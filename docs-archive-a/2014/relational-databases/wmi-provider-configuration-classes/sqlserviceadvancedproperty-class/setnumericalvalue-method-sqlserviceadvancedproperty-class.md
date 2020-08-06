---
title: SetNumericalValue 方法 (SqlServiceAdvancedProperty 类) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetNumericalValue Method (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetNumericalValue method
ms.assetid: 950ed1e8-0538-4db4-807c-a2c36f43cf6b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: db823938d77f4e2c67284cae0f11faca12aba6d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692307"
---
# <a name="setnumericalvalue-method-sqlserviceadvancedproperty-class"></a><span data-ttu-id="66c90-102">SetNumericalValue 方法（SqlServiceAdvancedProperty 类）</span><span class="sxs-lookup"><span data-stu-id="66c90-102">SetNumericalValue Method (SqlServiceAdvancedProperty Class)</span></span>
  <span data-ttu-id="66c90-103">设置属性的数值。</span><span class="sxs-lookup"><span data-stu-id="66c90-103">Sets the numeric value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66c90-104">语法</span><span class="sxs-lookup"><span data-stu-id="66c90-104">Syntax</span></span>  
  
```  
  
object  
.SetNumericalValue(  
NumValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="66c90-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="66c90-105">Parts</span></span>  
 <span data-ttu-id="66c90-106">对象</span><span class="sxs-lookup"><span data-stu-id="66c90-106">*object*</span></span>  
 <span data-ttu-id="66c90-107">一个表示高级属性的 [SqlServiceAdvancedProperty 类](sqlserviceadvancedproperty-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="66c90-107">A [SqlServiceAdvancedProperty Class](sqlserviceadvancedproperty-class.md) object that represents an advanced property.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="66c90-108">参数</span><span class="sxs-lookup"><span data-stu-id="66c90-108">Parameters</span></span>  
  
|<span data-ttu-id="66c90-109">参数</span><span class="sxs-lookup"><span data-stu-id="66c90-109">Parameter</span></span>|<span data-ttu-id="66c90-110">说明</span><span class="sxs-lookup"><span data-stu-id="66c90-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="66c90-111">*NumValue*</span><span class="sxs-lookup"><span data-stu-id="66c90-111">*NumValue*</span></span>|<span data-ttu-id="66c90-112">一个指定高级属性的值的 `uint32` 值。</span><span class="sxs-lookup"><span data-stu-id="66c90-112">A `uint32` value that specifies the value of the advanced property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="66c90-113">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="66c90-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="66c90-114">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="66c90-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66c90-115">备注</span><span class="sxs-lookup"><span data-stu-id="66c90-115">Remarks</span></span>  
 <span data-ttu-id="66c90-116">属性值类型必须为 Numeric，才能将属性设置为数值。</span><span class="sxs-lookup"><span data-stu-id="66c90-116">The property value type must be numeric to be able to set the property to a numeric value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66c90-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="66c90-117">See Also</span></span>  
 <span data-ttu-id="66c90-118">[启动和停止服务](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="66c90-118">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
