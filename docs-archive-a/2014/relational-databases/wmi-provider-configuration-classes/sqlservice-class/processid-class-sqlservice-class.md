---
title: ProcessId 类 (SqlService 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ProcessId Class (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ProcessId property
ms.assetid: 99b5a2e9-b44a-48a0-993e-04bd15c7fef4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7c4c40eea826b5009e52d26b1d930eaf5febbcdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586540"
---
# <a name="processid-class-sqlservice-class"></a><span data-ttu-id="7bba7-102">ProcessId 类（SqlService 类）</span><span class="sxs-lookup"><span data-stu-id="7bba7-102">ProcessId Class (SqlService Class)</span></span>
  <span data-ttu-id="7bba7-103">获取唯一标识服务的系统进程 ID。</span><span class="sxs-lookup"><span data-stu-id="7bba7-103">Gets the system process ID that uniquely identifies a service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bba7-104">语法</span><span class="sxs-lookup"><span data-stu-id="7bba7-104">Syntax</span></span>  
  
```  
  
object  
.ProcessId [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="7bba7-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="7bba7-105">Parts</span></span>  
 <span data-ttu-id="7bba7-106">对象</span><span class="sxs-lookup"><span data-stu-id="7bba7-106">*object*</span></span>  
 <span data-ttu-id="7bba7-107">一个表示服务的 [SqlService 类](sqlservice-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="7bba7-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="7bba7-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="7bba7-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="7bba7-109">一个指定唯一标识进程的 `uint32` 值。</span><span class="sxs-lookup"><span data-stu-id="7bba7-109">A `uint32` value that specifies the ID that uniquely identifies the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bba7-110">备注</span><span class="sxs-lookup"><span data-stu-id="7bba7-110">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bba7-111">示例</span><span class="sxs-lookup"><span data-stu-id="7bba7-111">Example</span></span>  
  
```  
mysqlservice.ProcessId = 324  
```  
  
## <a name="see-also"></a><span data-ttu-id="7bba7-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7bba7-112">See Also</span></span>  
 <span data-ttu-id="7bba7-113">[启动和停止服务](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="7bba7-113">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
