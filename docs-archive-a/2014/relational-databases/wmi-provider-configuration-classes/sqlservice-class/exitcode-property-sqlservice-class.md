---
title: ExitCode 属性 (SqlService 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ExitCode Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ExitCode property
ms.assetid: e6b8bff2-946f-4abe-bd50-1f7bb11fdddf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f7f5414afd8507a1fc9c592d6b8226692e9683a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580073"
---
# <a name="exitcode-property-sqlservice-class"></a><span data-ttu-id="7edac-102">ExitCode 属性（SqlService 类）</span><span class="sxs-lookup"><span data-stu-id="7edac-102">ExitCode Property (SqlService Class)</span></span>
  <span data-ttu-id="7edac-103">获取或设置 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 错误代码，它用于定义在启动或停止服务时遇到的问题。</span><span class="sxs-lookup"><span data-stu-id="7edac-103">Gets or sets the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 error code that defines problems encountered when starting and stopping the service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7edac-104">语法</span><span class="sxs-lookup"><span data-stu-id="7edac-104">Syntax</span></span>  
  
```  
  
object  
.ExitCode [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="7edac-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="7edac-105">Parts</span></span>  
 <span data-ttu-id="7edac-106">对象</span><span class="sxs-lookup"><span data-stu-id="7edac-106">*object*</span></span>  
 <span data-ttu-id="7edac-107">一个表示服务的 [SqlService 类](sqlservice-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="7edac-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="7edac-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="7edac-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="7edac-109">一个指定退出代码的 `uint32` 值。</span><span class="sxs-lookup"><span data-stu-id="7edac-109">A `uint32` value that specifies the exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7edac-110">备注</span><span class="sxs-lookup"><span data-stu-id="7edac-110">Remarks</span></span>  
 <span data-ttu-id="7edac-111">如果错误是此类表示的服务所特有的，则此属性将设置为 ERROR_SERVICE_SPECIFIC_ERROR (1066)。</span><span class="sxs-lookup"><span data-stu-id="7edac-111">This property is set to ERROR_SERVICE_SPECIFIC_ERROR (1066) when the error is unique to the service represented by this class.</span></span> <span data-ttu-id="7edac-112">当服务运行时，将此值设置为 NO_ERROR；而当服务正常终止时，再次将它设置为此值。</span><span class="sxs-lookup"><span data-stu-id="7edac-112">The service sets this value to NO_ERROR when running, and again upon normal termination.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7edac-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7edac-113">See Also</span></span>  
 <span data-ttu-id="7edac-114">[启动和停止服务](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="7edac-114">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
