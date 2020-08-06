---
title: SetDefaults 方法 (ClientSettings 类) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (ClientSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: 056508f3-a5c8-467c-a196-dc1ef1f5178f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b6985ebfa4a9145dd3474cec31f32cdab9c11cdc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590594"
---
# <a name="setdefaults-method-clientsettings-class"></a><span data-ttu-id="81437-102">SetDefaults 方法（ClientSettings 类）</span><span class="sxs-lookup"><span data-stu-id="81437-102">SetDefaults Method (ClientSettings Class)</span></span>
  <span data-ttu-id="81437-103">设置客户端实例的所有默认值， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 并提供覆盖现有数据的选项。</span><span class="sxs-lookup"><span data-stu-id="81437-103">Sets all the default values for the instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client with the option to overwrite existing data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81437-104">语法</span><span class="sxs-lookup"><span data-stu-id="81437-104">Syntax</span></span>  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="81437-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="81437-105">Parts</span></span>  
 <span data-ttu-id="81437-106">对象</span><span class="sxs-lookup"><span data-stu-id="81437-106">*object*</span></span>  
 <span data-ttu-id="81437-107">一个表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端实例的 `ClientSettings` 对象。</span><span class="sxs-lookup"><span data-stu-id="81437-107">A `ClientSettings` object that represents a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client instance.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="81437-108">参数</span><span class="sxs-lookup"><span data-stu-id="81437-108">Parameters</span></span>  
  
|<span data-ttu-id="81437-109">参数</span><span class="sxs-lookup"><span data-stu-id="81437-109">Parameter</span></span>|<span data-ttu-id="81437-110">说明</span><span class="sxs-lookup"><span data-stu-id="81437-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81437-111">*OverwriteAll*</span><span class="sxs-lookup"><span data-stu-id="81437-111">*OverwriteAll*</span></span>|<span data-ttu-id="81437-112">一个指定是否覆盖 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端实例的现有值的布尔值。</span><span class="sxs-lookup"><span data-stu-id="81437-112">A Boolean value that specifies whether to overwrite existing values on the instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client.</span></span> <span data-ttu-id="81437-113">若要覆盖现有数据，则为 `true`；如果不希望覆盖现有数据，则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="81437-113">`true` to overwrite existing data; `false` if existing data is not to be overwritten.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="81437-114">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="81437-114">Property Value/Return Value</span></span>  
 <span data-ttu-id="81437-115">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="81437-115">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81437-116">备注</span><span class="sxs-lookup"><span data-stu-id="81437-116">Remarks</span></span>  
  
