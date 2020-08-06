---
title: 依赖项属性 (SqlService 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- Dependencies Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Dependencies property
ms.assetid: 92d54b7e-de2f-4978-b601-0196e37cbb41
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b5b64aee371a41bc0d58ec4a52a1a1526bc13388
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692320"
---
# <a name="dependencies-property-sqlservice-class"></a><span data-ttu-id="52815-102">Dependencies 属性（SqlService 类）</span><span class="sxs-lookup"><span data-stu-id="52815-102">Dependencies Property (SqlService Class)</span></span>
  <span data-ttu-id="52815-103">获取依赖于所引用服务的服务列表。</span><span class="sxs-lookup"><span data-stu-id="52815-103">Gets a list of services that are dependent on the referenced service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52815-104">语法</span><span class="sxs-lookup"><span data-stu-id="52815-104">Syntax</span></span>  
  
```  
  
object  
.Dependencies [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="52815-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="52815-105">Parts</span></span>  
 <span data-ttu-id="52815-106">对象</span><span class="sxs-lookup"><span data-stu-id="52815-106">*object*</span></span>  
 <span data-ttu-id="52815-107">一个表示服务的 [SqlService 类](sqlservice-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="52815-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="52815-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="52815-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="52815-109">一个包含依赖于所引用服务的服务列表的字符串数组。</span><span class="sxs-lookup"><span data-stu-id="52815-109">A string[] array that contains a list of services dependent on the referenced service.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52815-110">备注</span><span class="sxs-lookup"><span data-stu-id="52815-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52815-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="52815-111">See Also</span></span>  
 <span data-ttu-id="52815-112">[启动和停止服务](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="52815-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
