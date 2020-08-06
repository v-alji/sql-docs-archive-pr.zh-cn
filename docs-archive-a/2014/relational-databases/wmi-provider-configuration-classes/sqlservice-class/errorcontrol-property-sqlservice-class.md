---
title: ErrorControl 属性 (SqlService 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ErrorControl Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ErrorControl property
ms.assetid: cbb1e0fa-5bfc-4b1b-a6ed-f7d5cfad4d73
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 73c726af514f2880484cf927282fc0e007f07e2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692314"
---
# <a name="errorcontrol-property-sqlservice-class"></a><span data-ttu-id="215f2-102">ErrorControl 属性（SqlService 类）</span><span class="sxs-lookup"><span data-stu-id="215f2-102">ErrorControl Property (SqlService Class)</span></span>
  <span data-ttu-id="215f2-103">获取或设置启动期间服务无法启动时的错误严重性。</span><span class="sxs-lookup"><span data-stu-id="215f2-103">Gets or sets the severity of the error if the service fails to start during startup.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="215f2-104">语法</span><span class="sxs-lookup"><span data-stu-id="215f2-104">Syntax</span></span>  
  
```  
  
object  
.ErrorControl [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="215f2-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="215f2-105">Parts</span></span>  
 <span data-ttu-id="215f2-106">对象</span><span class="sxs-lookup"><span data-stu-id="215f2-106">*object*</span></span>  
 <span data-ttu-id="215f2-107">一个表示服务的 [SqlService 类](sqlservice-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="215f2-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="215f2-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="215f2-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="215f2-109">一个字符串值，用于指定启动期间服务无法启动时所报告的错误的严重性。</span><span class="sxs-lookup"><span data-stu-id="215f2-109">A string value that specifies the error severity reported if the service fails during startup.</span></span> <span data-ttu-id="215f2-110">下表列出了可能的值。</span><span class="sxs-lookup"><span data-stu-id="215f2-110">The following table shows the possible values.</span></span>  
  
 <span data-ttu-id="215f2-111">忽略</span><span class="sxs-lookup"><span data-stu-id="215f2-111">Ignore</span></span>  
 <span data-ttu-id="215f2-112">不通知用户。</span><span class="sxs-lookup"><span data-stu-id="215f2-112">User is not notified.</span></span>  
  
 <span data-ttu-id="215f2-113">普通</span><span class="sxs-lookup"><span data-stu-id="215f2-113">Normal</span></span>  
 <span data-ttu-id="215f2-114">通知用户。</span><span class="sxs-lookup"><span data-stu-id="215f2-114">User is notified.</span></span>  
  
 <span data-ttu-id="215f2-115">Severe</span><span class="sxs-lookup"><span data-stu-id="215f2-115">Severe</span></span>  
 <span data-ttu-id="215f2-116">使用上一次已知正确的配置重新启动系统。</span><span class="sxs-lookup"><span data-stu-id="215f2-116">System is restarted with the last-known-good configuration.</span></span>  
  
 <span data-ttu-id="215f2-117">严重</span><span class="sxs-lookup"><span data-stu-id="215f2-117">Critical</span></span>  
 <span data-ttu-id="215f2-118">系统将尝试使用正确的配置重新启动。</span><span class="sxs-lookup"><span data-stu-id="215f2-118">System attempts to restart with a good configuration.</span></span>  
  
 <span data-ttu-id="215f2-119">未知</span><span class="sxs-lookup"><span data-stu-id="215f2-119">Unknown</span></span>  
 <span data-ttu-id="215f2-120">严重性未知。</span><span class="sxs-lookup"><span data-stu-id="215f2-120">The severity is unknown.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="215f2-121">备注</span><span class="sxs-lookup"><span data-stu-id="215f2-121">Remarks</span></span>  
 <span data-ttu-id="215f2-122">此值指示出现故障时启动程序采取的操作。</span><span class="sxs-lookup"><span data-stu-id="215f2-122">The value indicates the action taken by the startup program if a failure occurs.</span></span> <span data-ttu-id="215f2-123">所有的错误都由计算机系统记录。</span><span class="sxs-lookup"><span data-stu-id="215f2-123">All errors are logged by the computer system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="215f2-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="215f2-124">See Also</span></span>  
 <span data-ttu-id="215f2-125">[启动和停止服务](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="215f2-125">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
