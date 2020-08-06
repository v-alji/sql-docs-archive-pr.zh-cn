---
title: SetDefaults 方法 (SInstance 类) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (SInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: dc3c6a85-0711-4688-bf4f-91168c57af28
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c581834d3c97bed622d16fbb35e48704f8679531
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687632"
---
# <a name="setdefaults-method-sinstance-class"></a><span data-ttu-id="b1945-102">SetDefaults 方法（SInstance 类）</span><span class="sxs-lookup"><span data-stu-id="b1945-102">SetDefaults Method (SInstance Class)</span></span>
  <span data-ttu-id="b1945-103">设置实例的所有默认值， [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 并提供覆盖现有数据的选项。</span><span class="sxs-lookup"><span data-stu-id="b1945-103">Sets all the default values for the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with the option to overwrite existing data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1945-104">语法</span><span class="sxs-lookup"><span data-stu-id="b1945-104">Syntax</span></span>  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="b1945-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="b1945-105">Parts</span></span>  
 <span data-ttu-id="b1945-106">对象</span><span class="sxs-lookup"><span data-stu-id="b1945-106">*object*</span></span>  
 <span data-ttu-id="b1945-107">一个表示服务器实例的[SInstance 类](sinstance-class.md)对象。</span><span class="sxs-lookup"><span data-stu-id="b1945-107">An [SInstance Class](sinstance-class.md) object that represents a server instance.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="b1945-108">参数</span><span class="sxs-lookup"><span data-stu-id="b1945-108">Parameters</span></span>  
  
|<span data-ttu-id="b1945-109">参数</span><span class="sxs-lookup"><span data-stu-id="b1945-109">Parameter</span></span>|<span data-ttu-id="b1945-110">说明</span><span class="sxs-lookup"><span data-stu-id="b1945-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1945-111">*OverwriteAll*</span><span class="sxs-lookup"><span data-stu-id="b1945-111">*OverwriteAll*</span></span>|<span data-ttu-id="b1945-112">一个指定是否覆盖 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 客户端实例的现有值的布尔值：若要覆盖现有值，则为 `true`；如果不希望覆盖现有值，则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="b1945-112">A Boolean value that specifies whether to overwrite existing value on the instance of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client: `true` if existing data is overwritten, or `false` if existing data is not overwritten.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b1945-113">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="b1945-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="b1945-114">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="b1945-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1945-115">备注</span><span class="sxs-lookup"><span data-stu-id="b1945-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1945-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b1945-116">See Also</span></span>  
 <span data-ttu-id="b1945-117">[配置服务器网络协议和网络库](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="b1945-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
