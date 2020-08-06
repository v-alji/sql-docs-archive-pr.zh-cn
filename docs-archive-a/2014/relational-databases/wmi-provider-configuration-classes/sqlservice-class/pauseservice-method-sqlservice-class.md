---
title: PauseService 方法 (SqlService 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- PauseService Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- PauseService method
ms.assetid: 5c3a8feb-58b8-4385-b4c8-bf33cf4d276d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8286e123bbbc279ba461336c5716eeb208c5b238
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586541"
---
# <a name="pauseservice-method-sqlservice-class"></a><span data-ttu-id="eb16e-102">PauseService 方法（SqlService 类）</span><span class="sxs-lookup"><span data-stu-id="eb16e-102">PauseService Method (SqlService Class)</span></span>
  <span data-ttu-id="eb16e-103">尝试将服务置于暂停状态。</span><span class="sxs-lookup"><span data-stu-id="eb16e-103">Attempts to place the service in the paused state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb16e-104">语法</span><span class="sxs-lookup"><span data-stu-id="eb16e-104">Syntax</span></span>  
  
```  
  
object  
.PauseService()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="eb16e-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="eb16e-105">Parts</span></span>  
 <span data-ttu-id="eb16e-106">对象</span><span class="sxs-lookup"><span data-stu-id="eb16e-106">*object*</span></span>  
 <span data-ttu-id="eb16e-107">一个表示服务的 [SqlService 类](sqlservice-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="eb16e-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="eb16e-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="eb16e-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="eb16e-109">一个 uint32 值，如果服务已成功停止，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="eb16e-109">A uint32 value, which is 0 if the service was successfully stopped, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb16e-110">备注</span><span class="sxs-lookup"><span data-stu-id="eb16e-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb16e-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eb16e-111">See Also</span></span>  
 <span data-ttu-id="eb16e-112">[启动和停止服务](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="eb16e-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
