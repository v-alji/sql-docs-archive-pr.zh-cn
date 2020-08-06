---
title: StartMode 属性 (SqlService 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- StartMode Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- StartMode property
ms.assetid: c0c2c7f8-d4ae-44f2-ad8e-aecfcb7c2878
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bafffcc3c8f82f69896d0a22e9b0a9060e04cd10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690435"
---
# <a name="startmode-property-sqlservice-class"></a><span data-ttu-id="7541f-102">StartMode 属性（SqlService 类）</span><span class="sxs-lookup"><span data-stu-id="7541f-102">StartMode Property (SqlService Class)</span></span>
  <span data-ttu-id="7541f-103">获取服务的启动模式。</span><span class="sxs-lookup"><span data-stu-id="7541f-103">Gets the start mode of the service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7541f-104">语法</span><span class="sxs-lookup"><span data-stu-id="7541f-104">Syntax</span></span>  
  
```  
  
object  
.StartMode [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="7541f-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="7541f-105">Parts</span></span>  
 <span data-ttu-id="7541f-106">对象</span><span class="sxs-lookup"><span data-stu-id="7541f-106">*object*</span></span>  
 <span data-ttu-id="7541f-107">一个表示服务的 [SqlService 类](sqlservice-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="7541f-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="7541f-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="7541f-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="7541f-109">一个指定服务模式的 uint32 值。</span><span class="sxs-lookup"><span data-stu-id="7541f-109">A uint32 value that specifies the mode of the service.</span></span>  
  
 <span data-ttu-id="7541f-110">可以是下列值之一。</span><span class="sxs-lookup"><span data-stu-id="7541f-110">Values can be one of the following.</span></span>  
  
 <span data-ttu-id="7541f-111">启动</span><span class="sxs-lookup"><span data-stu-id="7541f-111">Boot</span></span>  
 <span data-ttu-id="7541f-112">值 = 0。</span><span class="sxs-lookup"><span data-stu-id="7541f-112">Value = 0.</span></span> <span data-ttu-id="7541f-113">服务由操作系统加载程序启动。</span><span class="sxs-lookup"><span data-stu-id="7541f-113">Service started by the operating system loader.</span></span> <span data-ttu-id="7541f-114">此选项只对驱动程序服务有效。</span><span class="sxs-lookup"><span data-stu-id="7541f-114">This option is valid only for driver services.</span></span>  
  
 <span data-ttu-id="7541f-115">System</span><span class="sxs-lookup"><span data-stu-id="7541f-115">System</span></span>  
 <span data-ttu-id="7541f-116">值 = 1。</span><span class="sxs-lookup"><span data-stu-id="7541f-116">Value = 1.</span></span> <span data-ttu-id="7541f-117">服务由 `IoInitSystem` 方法启动。</span><span class="sxs-lookup"><span data-stu-id="7541f-117">Service started by the `IoInitSystem` method.</span></span> <span data-ttu-id="7541f-118">此选项只对驱动程序服务有效。</span><span class="sxs-lookup"><span data-stu-id="7541f-118">This option is valid only for driver services.</span></span>  
  
 <span data-ttu-id="7541f-119">自动</span><span class="sxs-lookup"><span data-stu-id="7541f-119">Automatic</span></span>  
 <span data-ttu-id="7541f-120">值 = 2。</span><span class="sxs-lookup"><span data-stu-id="7541f-120">Value = 2.</span></span> <span data-ttu-id="7541f-121">服务将在系统启动期间由服务控制管理器自动启动。</span><span class="sxs-lookup"><span data-stu-id="7541f-121">Service to be started automatically by the service control manager during system startup.</span></span>  
  
 <span data-ttu-id="7541f-122">手动</span><span class="sxs-lookup"><span data-stu-id="7541f-122">Manual</span></span>  
 <span data-ttu-id="7541f-123">值 = 3。</span><span class="sxs-lookup"><span data-stu-id="7541f-123">Value = 3.</span></span> <span data-ttu-id="7541f-124">服务将在进程调用 `StartService` 方法时由计算机管理器启动。</span><span class="sxs-lookup"><span data-stu-id="7541f-124">Service to be started by the Computer Manager when a process calls the `StartService` method.</span></span>  
  
 <span data-ttu-id="7541f-125">已禁用</span><span class="sxs-lookup"><span data-stu-id="7541f-125">Disabled</span></span>  
 <span data-ttu-id="7541f-126">值 = 4。</span><span class="sxs-lookup"><span data-stu-id="7541f-126">Value = 4.</span></span> <span data-ttu-id="7541f-127">无法启动服务。</span><span class="sxs-lookup"><span data-stu-id="7541f-127">Service cannot be started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7541f-128">备注</span><span class="sxs-lookup"><span data-stu-id="7541f-128">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7541f-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7541f-129">See Also</span></span>  
 <span data-ttu-id="7541f-130">[启动和停止服务](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="7541f-130">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
