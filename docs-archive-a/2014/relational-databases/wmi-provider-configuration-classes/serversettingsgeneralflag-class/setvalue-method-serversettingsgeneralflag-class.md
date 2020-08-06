---
title: SetValue 方法 (ServerSettingsGeneralFlag 类) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetValue Method (ServerSettingsGeneralFlag Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetValue method
ms.assetid: a889feac-c0e0-4635-b506-843863d86967
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 74c4c189b72b7a469794e0828faf062a88cdf46f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694402"
---
# <a name="setvalue-method-serversettingsgeneralflag-class"></a><span data-ttu-id="b3ee0-102">SetValue 方法（ServerSettingsGeneralFlag 类）</span><span class="sxs-lookup"><span data-stu-id="b3ee0-102">SetValue Method (ServerSettingsGeneralFlag Class)</span></span>
  <span data-ttu-id="b3ee0-103">设置引用的标志的所有值。</span><span class="sxs-lookup"><span data-stu-id="b3ee0-103">Sets all the values of the referenced flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3ee0-104">语法</span><span class="sxs-lookup"><span data-stu-id="b3ee0-104">Syntax</span></span>  
  
```  
  
object  
.SetValue(  
Value  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="b3ee0-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="b3ee0-105">Parts</span></span>  
 <span data-ttu-id="b3ee0-106">对象</span><span class="sxs-lookup"><span data-stu-id="b3ee0-106">*object*</span></span>  
 <span data-ttu-id="b3ee0-107">一个表示服务器设置的常规标志的 [ServerSettingsGeneralFlag 类](serversettingsgeneralflag-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="b3ee0-107">A [ServerSettingsGeneralFlag Class](serversettingsgeneralflag-class.md) object that represents a general flag for the server settings.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="b3ee0-108">参数</span><span class="sxs-lookup"><span data-stu-id="b3ee0-108">Parameters</span></span>  
  
|<span data-ttu-id="b3ee0-109">参数</span><span class="sxs-lookup"><span data-stu-id="b3ee0-109">Parameter</span></span>|<span data-ttu-id="b3ee0-110">说明</span><span class="sxs-lookup"><span data-stu-id="b3ee0-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b3ee0-111">*值*</span><span class="sxs-lookup"><span data-stu-id="b3ee0-111">*Value*</span></span>|<span data-ttu-id="b3ee0-112">一个指定标志的值的布尔值。</span><span class="sxs-lookup"><span data-stu-id="b3ee0-112">A Boolean value that specifies the value of the flag.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b3ee0-113">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="b3ee0-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="b3ee0-114">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="b3ee0-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3ee0-115">备注</span><span class="sxs-lookup"><span data-stu-id="b3ee0-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3ee0-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3ee0-116">See Also</span></span>  
 <span data-ttu-id="b3ee0-117">[配置服务器网络协议和网络库](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="b3ee0-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
