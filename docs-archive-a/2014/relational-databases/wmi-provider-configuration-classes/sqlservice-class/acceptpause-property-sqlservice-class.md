---
title: AcceptPause 属性 (SqlService 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- AcceptPause Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- AcceptPause property
ms.assetid: 4339e903-35ee-4395-b005-ca58b3a24a84
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 930c82f6e4538f7f2e916deaa374e928b756909b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591167"
---
# <a name="acceptpause-property-sqlservice-class"></a><span data-ttu-id="019b6-102">AcceptPause 属性（SqlService 类）</span><span class="sxs-lookup"><span data-stu-id="019b6-102">AcceptPause Property (SqlService Class)</span></span>
  <span data-ttu-id="019b6-103">获取用于指定是否可以暂停服务的布尔值属性。</span><span class="sxs-lookup"><span data-stu-id="019b6-103">Gets the Boolean property value that specifies whether the service can be paused.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="019b6-104">语法</span><span class="sxs-lookup"><span data-stu-id="019b6-104">Syntax</span></span>  
  
```  
  
object  
.AcceptPause [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="019b6-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="019b6-105">Parts</span></span>  
 <span data-ttu-id="019b6-106">对象</span><span class="sxs-lookup"><span data-stu-id="019b6-106">*object*</span></span>  
 <span data-ttu-id="019b6-107">一个表示服务的 [SqlService 类](sqlservice-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="019b6-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="019b6-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="019b6-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="019b6-109">一个指定是否可以暂停服务的布尔值属性。</span><span class="sxs-lookup"><span data-stu-id="019b6-109">A Boolean value that specifies whether the service can be paused.</span></span> <span data-ttu-id="019b6-110">如果可以暂停服务，则为 `true`；如果不能暂停服务，则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="019b6-110">`true` if the service can be paused; `false` if the service cannot be paused.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="019b6-111">备注</span><span class="sxs-lookup"><span data-stu-id="019b6-111">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="019b6-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="019b6-112">See Also</span></span>  
 <span data-ttu-id="019b6-113">[启动和停止服务](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="019b6-113">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
