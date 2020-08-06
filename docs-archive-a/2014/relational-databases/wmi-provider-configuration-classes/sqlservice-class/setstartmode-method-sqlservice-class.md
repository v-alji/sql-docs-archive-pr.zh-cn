---
title: SetStartMode 方法 (SqlService 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStartMode Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStartMode method
ms.assetid: f6f198b4-f9a4-468c-8977-76462ef06e61
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a9b7310623f526d7b106485ed9681df3aa100129
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577445"
---
# <a name="setstartmode-method-sqlservice-class"></a><span data-ttu-id="f787a-102">SetStartMode 方法（SqlService 类）</span><span class="sxs-lookup"><span data-stu-id="f787a-102">SetStartMode Method (SqlService Class)</span></span>
  <span data-ttu-id="f787a-103">修改服务实例的启动模式。</span><span class="sxs-lookup"><span data-stu-id="f787a-103">Modifies the start mode of the service instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f787a-104">语法</span><span class="sxs-lookup"><span data-stu-id="f787a-104">Syntax</span></span>  
  
```  
  
object  
.SetStartMode(  
StartMode  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="f787a-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="f787a-105">Parts</span></span>  
 <span data-ttu-id="f787a-106">对象</span><span class="sxs-lookup"><span data-stu-id="f787a-106">*object*</span></span>  
 <span data-ttu-id="f787a-107">一个表示服务的 [SqlService 类](sqlservice-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="f787a-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="f787a-108">参数</span><span class="sxs-lookup"><span data-stu-id="f787a-108">Parameters</span></span>  
 <span data-ttu-id="f787a-109">*StartMode*</span><span class="sxs-lookup"><span data-stu-id="f787a-109">*StartMode*</span></span>  
 <span data-ttu-id="f787a-110">一个指定服务实例的启动模式的 `uint32` 值。</span><span class="sxs-lookup"><span data-stu-id="f787a-110">A `uint32` value that specifies the start mode of the service instance.</span></span>  
  
 <span data-ttu-id="f787a-111">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="f787a-111">The valid values are as follows:</span></span>  
  
 <span data-ttu-id="f787a-112">值 = 0。</span><span class="sxs-lookup"><span data-stu-id="f787a-112">Value = 0.</span></span> <span data-ttu-id="f787a-113">启动 - 设备驱动程序由操作系统加载程序启动。</span><span class="sxs-lookup"><span data-stu-id="f787a-113">Boot - Device driver started by the operating system loader.</span></span> <span data-ttu-id="f787a-114">此值只对驱动程序服务有效。</span><span class="sxs-lookup"><span data-stu-id="f787a-114">This value is valid only for driver services.</span></span>  
  
 <span data-ttu-id="f787a-115">值 = 1。</span><span class="sxs-lookup"><span data-stu-id="f787a-115">Value = 1.</span></span> <span data-ttu-id="f787a-116">系统 - 设备驱动程序由 `IoInitSystem` 方法启动。</span><span class="sxs-lookup"><span data-stu-id="f787a-116">System - Device driver started by the `IoInitSystem` method.</span></span> <span data-ttu-id="f787a-117">此值只对驱动程序服务有效。</span><span class="sxs-lookup"><span data-stu-id="f787a-117">This value is valid only for driver services.</span></span>  
  
 <span data-ttu-id="f787a-118">值 = 2。</span><span class="sxs-lookup"><span data-stu-id="f787a-118">Value = 2.</span></span> <span data-ttu-id="f787a-119">自动 - 服务将在系统启动期间由服务控制管理器自动启动。</span><span class="sxs-lookup"><span data-stu-id="f787a-119">Automatic - Service to be started automatically by the service control manager during system startup.</span></span>  
  
 <span data-ttu-id="f787a-120">值 = 3。</span><span class="sxs-lookup"><span data-stu-id="f787a-120">Value = 3.</span></span> <span data-ttu-id="f787a-121">手动 - 服务将在进程调用 `StartService` 方法时由计算机管理器启动。</span><span class="sxs-lookup"><span data-stu-id="f787a-121">Manual - Service to be started by the Computer Manager when a process calls the `StartService` method.</span></span>  
  
 <span data-ttu-id="f787a-122">值 = 4。</span><span class="sxs-lookup"><span data-stu-id="f787a-122">Value = 4.</span></span> <span data-ttu-id="f787a-123">已禁用 - 无法再启动服务。</span><span class="sxs-lookup"><span data-stu-id="f787a-123">Disabled - Service can no longer be started.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="f787a-124">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="f787a-124">Property Value/Return Value</span></span>  
 <span data-ttu-id="f787a-125">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1。</span><span class="sxs-lookup"><span data-stu-id="f787a-125">A `uint32` value, which is 0 if the service was successfully modified or 1 if the request is not supported.</span></span> <span data-ttu-id="f787a-126">其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="f787a-126">Any other number indicates an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f787a-127">备注</span><span class="sxs-lookup"><span data-stu-id="f787a-127">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f787a-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f787a-128">See Also</span></span>  
 <span data-ttu-id="f787a-129">[启动和停止服务](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="f787a-129">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
