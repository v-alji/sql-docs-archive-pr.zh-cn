---
title: SetDefaults 方法 (CInstance 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (CInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: ed9e99c2-3e28-4ee8-bc20-61ca05984973
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5e589796f973592d7f9f549bffbbf8dfbe49cc27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576575"
---
# <a name="setdefaults-method-cinstance-class"></a><span data-ttu-id="42634-102">SetDefaults 方法（CInstance 类）</span><span class="sxs-lookup"><span data-stu-id="42634-102">SetDefaults Method (CInstance Class)</span></span>
  <span data-ttu-id="42634-103">设置客户端实例的所有默认值， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 并提供覆盖现有数据的选项。</span><span class="sxs-lookup"><span data-stu-id="42634-103">Sets all the default values for the instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client with the option to overwrite existing data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42634-104">语法</span><span class="sxs-lookup"><span data-stu-id="42634-104">Syntax</span></span>  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="42634-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="42634-105">Parts</span></span>  
 <span data-ttu-id="42634-106">对象</span><span class="sxs-lookup"><span data-stu-id="42634-106">*object*</span></span>  
 <span data-ttu-id="42634-107">一个表示 [客户端实例的](cinstance-class.md) CInstance 类 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="42634-107">A [CInstance Class](cinstance-class.md) object that represents a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client instance.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="42634-108">参数</span><span class="sxs-lookup"><span data-stu-id="42634-108">Parameters</span></span>  
  
|<span data-ttu-id="42634-109">参数</span><span class="sxs-lookup"><span data-stu-id="42634-109">Parameter</span></span>|<span data-ttu-id="42634-110">说明</span><span class="sxs-lookup"><span data-stu-id="42634-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="42634-111">*OverwriteAll*</span><span class="sxs-lookup"><span data-stu-id="42634-111">*OverwriteAll*</span></span>|<span data-ttu-id="42634-112">一个指定是否覆盖 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端实例的现有值的布尔值：若要覆盖现有数据，则为 `true`；如果不希望覆盖现有数据，则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="42634-112">A Boolean value that specifies whether to overwrite existing values on the instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client: `true` to overwrite existing data, or `false` if existing data is not to be overwritten.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="42634-113">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="42634-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="42634-114">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="42634-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42634-115">备注</span><span class="sxs-lookup"><span data-stu-id="42634-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42634-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="42634-116">See Also</span></span>  
 [<span data-ttu-id="42634-117">配置客户端协议</span><span class="sxs-lookup"><span data-stu-id="42634-117">Configure Client Protocols</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
