---
title: SetDefaults 方法 (ServerSettings 类) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (ServerSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: 76e4cfab-4b15-4da4-bb2f-8aac6f927f79
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 93dd2eee5a395d4d7463ebf9b85530fcf82d1888
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689290"
---
# <a name="setdefaults-method-serversettings-class"></a><span data-ttu-id="c2c82-102">SetDefaults 方法（ServerSettings 类）</span><span class="sxs-lookup"><span data-stu-id="c2c82-102">SetDefaults Method (ServerSettings Class)</span></span>
  <span data-ttu-id="c2c82-103">设置实例的所有默认值， [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 并提供覆盖现有数据的选项。</span><span class="sxs-lookup"><span data-stu-id="c2c82-103">Sets all the default values for the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with the option to overwrite existing data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2c82-104">语法</span><span class="sxs-lookup"><span data-stu-id="c2c82-104">Syntax</span></span>  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="c2c82-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="c2c82-105">Parts</span></span>  
 <span data-ttu-id="c2c82-106">对象</span><span class="sxs-lookup"><span data-stu-id="c2c82-106">*object*</span></span>  
 <span data-ttu-id="c2c82-107">一个表示客户端实例的[ServerSettings 类](serversettings-class.md)对象 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c2c82-107">A [ServerSettings Class](serversettings-class.md) object that represents a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client instance.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="c2c82-108">参数</span><span class="sxs-lookup"><span data-stu-id="c2c82-108">Parameters</span></span>  
  
|<span data-ttu-id="c2c82-109">参数</span><span class="sxs-lookup"><span data-stu-id="c2c82-109">Parameter</span></span>|<span data-ttu-id="c2c82-110">说明</span><span class="sxs-lookup"><span data-stu-id="c2c82-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c2c82-111">*OverwriteAll*</span><span class="sxs-lookup"><span data-stu-id="c2c82-111">*OverwriteAll*</span></span>|<span data-ttu-id="c2c82-112">一个指定是否覆盖 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例上的现有值的布尔值。若要覆盖现有数据，则为 `true`；如果不希望覆盖现有数据，则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="c2c82-112">A Boolean value that specifies whether to overwrite existing values on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: `true` to overwrite existing data, or `false` if existing data is not to be overwritten.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="c2c82-113">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="c2c82-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="c2c82-114">一个 u`int32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="c2c82-114">A u`int32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2c82-115">备注</span><span class="sxs-lookup"><span data-stu-id="c2c82-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2c82-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c2c82-116">See Also</span></span>  
 <span data-ttu-id="c2c82-117">[配置服务器网络协议和网络库](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="c2c82-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
