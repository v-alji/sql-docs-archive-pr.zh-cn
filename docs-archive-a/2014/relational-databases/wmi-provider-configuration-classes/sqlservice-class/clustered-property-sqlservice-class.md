---
title: 聚集属性 (SqlService 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- Clustered Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Clustered property
ms.assetid: f714e7f5-c2db-45c6-9536-6ca2cb5b42aa
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 86fdc87bb7b691580f7efd5ccd7b333d88a3aa78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687599"
---
# <a name="clustered-property-sqlservice-class"></a><span data-ttu-id="d6e7e-102">Clustered 属性（SqlService 类）</span><span class="sxs-lookup"><span data-stu-id="d6e7e-102">Clustered Property (SqlService Class)</span></span>
  <span data-ttu-id="d6e7e-103">获取用于指定服务是否是群集实例的一部分的布尔值属性。</span><span class="sxs-lookup"><span data-stu-id="d6e7e-103">Gets the Boolean property value that specifies whether the service is part of a clustered instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6e7e-104">语法</span><span class="sxs-lookup"><span data-stu-id="d6e7e-104">Syntax</span></span>  
  
```  
  
object  
.Clustered [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="d6e7e-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="d6e7e-105">Parts</span></span>  
 <span data-ttu-id="d6e7e-106">对象</span><span class="sxs-lookup"><span data-stu-id="d6e7e-106">*object*</span></span>  
 <span data-ttu-id="d6e7e-107">一个表示服务的 [SqlService 类](sqlservice-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="d6e7e-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="d6e7e-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="d6e7e-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="d6e7e-109">一个指定服务是否参与群集实例的布尔值：如果服务参与群集实例，则为 `true`；如果服务不参与群集实例，则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="d6e7e-109">A Boolean value that specifies whether the service is participating in a clustered instance: `true` if the service is participating in a clustered instance, or `false` if the service is not participating in a clustered instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6e7e-110">备注</span><span class="sxs-lookup"><span data-stu-id="d6e7e-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6e7e-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d6e7e-111">See Also</span></span>  
 <span data-ttu-id="d6e7e-112">[启动和停止服务](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="d6e7e-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
