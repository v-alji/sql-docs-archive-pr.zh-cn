---
title: AcceptStop 属性 (SqlService 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- AcceptStop Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- AcceptStop property
ms.assetid: bf8ffe79-4f4c-4a2d-82e5-2ae8f5d466c5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d555a3763b4e8c769cd52ce72019b66bddd594fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586542"
---
# <a name="acceptstop-property-sqlservice-class"></a><span data-ttu-id="4d48b-102">AcceptStop 属性（SqlService 类）</span><span class="sxs-lookup"><span data-stu-id="4d48b-102">AcceptStop Property (SqlService Class)</span></span>
  <span data-ttu-id="4d48b-103">获取用于指定是否可以停止服务的布尔值属性。</span><span class="sxs-lookup"><span data-stu-id="4d48b-103">Gets the Boolean property value that specifies whether the service can be stopped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d48b-104">语法</span><span class="sxs-lookup"><span data-stu-id="4d48b-104">Syntax</span></span>  
  
```  
  
object  
.AcceptStop [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="4d48b-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="4d48b-105">Parts</span></span>  
 <span data-ttu-id="4d48b-106">对象</span><span class="sxs-lookup"><span data-stu-id="4d48b-106">*object*</span></span>  
 <span data-ttu-id="4d48b-107">一个表示服务的[SqlService 类](sqlservice-class.md)对象</span><span class="sxs-lookup"><span data-stu-id="4d48b-107">A [SqlService Class](sqlservice-class.md) object that represents the service</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="4d48b-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="4d48b-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="4d48b-109">一个指定是否可以停止服务的布尔值属性。如果可以停止服务，则为 `true`；如果不能停止服务，则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="4d48b-109">A Boolean value that specifies whether the service can be stopped: `true` if the service can be stopped, or `false` if the service cannot be stopped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d48b-110">备注</span><span class="sxs-lookup"><span data-stu-id="4d48b-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d48b-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4d48b-111">See Also</span></span>  
 <span data-ttu-id="4d48b-112">[启动和停止服务](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="4d48b-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
