---
title: State 属性 (SqlService 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- State Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- State property
ms.assetid: 9e09f419-947c-4d4b-9a49-2d3396c847cd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a7456113d9ec4444507d1057892a65adf241992f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690429"
---
# <a name="state-property-sqlservice-class"></a><span data-ttu-id="0d5ef-102">State 属性（SqlService 类）</span><span class="sxs-lookup"><span data-stu-id="0d5ef-102">State Property (SqlService Class)</span></span>
  <span data-ttu-id="0d5ef-103">获取或设置服务的当前状态。</span><span class="sxs-lookup"><span data-stu-id="0d5ef-103">Gets or sets the current state of the service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d5ef-104">语法</span><span class="sxs-lookup"><span data-stu-id="0d5ef-104">Syntax</span></span>  
  
```  
  
object  
.State [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="0d5ef-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="0d5ef-105">Parts</span></span>  
 <span data-ttu-id="0d5ef-106">对象</span><span class="sxs-lookup"><span data-stu-id="0d5ef-106">*object*</span></span>  
 <span data-ttu-id="0d5ef-107">一个表示服务的 [SqlService 类](sqlservice-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="0d5ef-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="0d5ef-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="0d5ef-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="0d5ef-109">一个指定服务状态的 uint32 值。</span><span class="sxs-lookup"><span data-stu-id="0d5ef-109">A uint32 value that specifies the state of the service.</span></span>  
  
 <span data-ttu-id="0d5ef-110">可以是下列值之一。</span><span class="sxs-lookup"><span data-stu-id="0d5ef-110">Values can be one of the following.</span></span>  
  
 <span data-ttu-id="0d5ef-111">1</span><span class="sxs-lookup"><span data-stu-id="0d5ef-111">1</span></span>  
 <span data-ttu-id="0d5ef-112">已停止。</span><span class="sxs-lookup"><span data-stu-id="0d5ef-112">Stopped.</span></span> <span data-ttu-id="0d5ef-113">服务已停止。</span><span class="sxs-lookup"><span data-stu-id="0d5ef-113">The service is stopped.</span></span>  
  
 <span data-ttu-id="0d5ef-114">2</span><span class="sxs-lookup"><span data-stu-id="0d5ef-114">2</span></span>  
 <span data-ttu-id="0d5ef-115">启动挂起。</span><span class="sxs-lookup"><span data-stu-id="0d5ef-115">Start Pending.</span></span> <span data-ttu-id="0d5ef-116">服务正在等待启动。</span><span class="sxs-lookup"><span data-stu-id="0d5ef-116">The service is waiting to start.</span></span>  
  
 <span data-ttu-id="0d5ef-117">3</span><span class="sxs-lookup"><span data-stu-id="0d5ef-117">3</span></span>  
 <span data-ttu-id="0d5ef-118">停止挂起。</span><span class="sxs-lookup"><span data-stu-id="0d5ef-118">Stop Pending.</span></span> <span data-ttu-id="0d5ef-119">服务正在等待停止。</span><span class="sxs-lookup"><span data-stu-id="0d5ef-119">The service is waiting to stop.</span></span>  
  
 <span data-ttu-id="0d5ef-120">4</span><span class="sxs-lookup"><span data-stu-id="0d5ef-120">4</span></span>  
 <span data-ttu-id="0d5ef-121">正在运行。</span><span class="sxs-lookup"><span data-stu-id="0d5ef-121">Running.</span></span> <span data-ttu-id="0d5ef-122">服务正在运行。</span><span class="sxs-lookup"><span data-stu-id="0d5ef-122">The service is running.</span></span>  
  
 <span data-ttu-id="0d5ef-123">5</span><span class="sxs-lookup"><span data-stu-id="0d5ef-123">5</span></span>  
 <span data-ttu-id="0d5ef-124">继续挂起。</span><span class="sxs-lookup"><span data-stu-id="0d5ef-124">Continue Pending.</span></span> <span data-ttu-id="0d5ef-125">服务正在等待继续。</span><span class="sxs-lookup"><span data-stu-id="0d5ef-125">The service is waiting to continue.</span></span>  
  
 <span data-ttu-id="0d5ef-126">6</span><span class="sxs-lookup"><span data-stu-id="0d5ef-126">6</span></span>  
 <span data-ttu-id="0d5ef-127">暂停挂起。</span><span class="sxs-lookup"><span data-stu-id="0d5ef-127">Pause Pending.</span></span> <span data-ttu-id="0d5ef-128">服务正在等待暂停。</span><span class="sxs-lookup"><span data-stu-id="0d5ef-128">The service is waiting to pause.</span></span>  
  
 <span data-ttu-id="0d5ef-129">7</span><span class="sxs-lookup"><span data-stu-id="0d5ef-129">7</span></span>  
 <span data-ttu-id="0d5ef-130">已暂停。</span><span class="sxs-lookup"><span data-stu-id="0d5ef-130">Paused.</span></span> <span data-ttu-id="0d5ef-131">服务已暂停。</span><span class="sxs-lookup"><span data-stu-id="0d5ef-131">The service is paused.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d5ef-132">备注</span><span class="sxs-lookup"><span data-stu-id="0d5ef-132">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d5ef-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0d5ef-133">See Also</span></span>  
 <span data-ttu-id="0d5ef-134">[启动和停止服务](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0d5ef-134">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
