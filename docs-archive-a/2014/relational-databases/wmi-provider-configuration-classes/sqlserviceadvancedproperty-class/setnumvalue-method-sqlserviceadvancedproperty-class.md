---
title: SetNumValue 方法 (SqlServiceAdvancedProperty 类) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetNumValue Method (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetNumValue method
ms.assetid: a5e1056b-0b75-4ad6-99c1-89246010d815
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 01388855a27dcf14754f677a42c13f8d29cbaacc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690421"
---
# <a name="setnumvalue-method-sqlserviceadvancedproperty-class"></a><span data-ttu-id="a5367-102">SetNumValue 方法（SqlServiceAdvancedProperty 类）</span><span class="sxs-lookup"><span data-stu-id="a5367-102">SetNumValue Method (SqlServiceAdvancedProperty Class)</span></span>
  <span data-ttu-id="a5367-103">设置属性的数值。</span><span class="sxs-lookup"><span data-stu-id="a5367-103">Sets the numeric value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5367-104">语法</span><span class="sxs-lookup"><span data-stu-id="a5367-104">Syntax</span></span>  
  
```  
  
object  
.SetNumValue(  
NumValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="a5367-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="a5367-105">Parts</span></span>  
 <span data-ttu-id="a5367-106">对象</span><span class="sxs-lookup"><span data-stu-id="a5367-106">*object*</span></span>  
 <span data-ttu-id="a5367-107">一个表示高级属性的 [SqlServiceAdvancedProperty 类](sqlserviceadvancedproperty-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="a5367-107">A [SqlServiceAdvancedProperty Class](sqlserviceadvancedproperty-class.md) object that represents an advanced property.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="a5367-108">参数</span><span class="sxs-lookup"><span data-stu-id="a5367-108">Parameters</span></span>  
  
|<span data-ttu-id="a5367-109">参数</span><span class="sxs-lookup"><span data-stu-id="a5367-109">Parameter</span></span>|<span data-ttu-id="a5367-110">说明</span><span class="sxs-lookup"><span data-stu-id="a5367-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a5367-111">*NumValue*</span><span class="sxs-lookup"><span data-stu-id="a5367-111">*NumValue*</span></span>|<span data-ttu-id="a5367-112">一个指定高级属性的值的 `uint32` 值。</span><span class="sxs-lookup"><span data-stu-id="a5367-112">A `uint32` value that specifies the value of the advanced property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="a5367-113">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="a5367-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="a5367-114">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="a5367-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5367-115">备注</span><span class="sxs-lookup"><span data-stu-id="a5367-115">Remarks</span></span>  
 <span data-ttu-id="a5367-116">属性值类型必须为 Numeric，才能将属性设置为数值。</span><span class="sxs-lookup"><span data-stu-id="a5367-116">The property value type must be numeric to be able to set the property to a numeric value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5367-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a5367-117">See Also</span></span>  
 <span data-ttu-id="a5367-118">[启动和停止服务](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a5367-118">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
