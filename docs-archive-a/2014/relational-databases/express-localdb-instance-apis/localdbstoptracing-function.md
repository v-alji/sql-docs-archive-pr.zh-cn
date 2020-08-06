---
title: LocalDBStopTracing 函数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBStopTracing
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 1d50e040-8602-4ffa-be8f-b8633fdfa7ff
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2bf6051fe8c86728c2ebf0a0b2bc34fabb98edb9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578219"
---
# <a name="localdbstoptracing-function"></a><span data-ttu-id="ef3bc-102">LocalDBStopTracing 函数</span><span class="sxs-lookup"><span data-stu-id="ef3bc-102">LocalDBStopTracing Function</span></span>
  <span data-ttu-id="ef3bc-103">对当前 Windows 用户拥有的所有 SQL Server Express LocalDB 实例禁用 API 调用跟踪。</span><span class="sxs-lookup"><span data-stu-id="ef3bc-103">Disables tracing of API calls for all the SQL Server Express LocalDB instances owned by the current Windows user.</span></span>  
  
 <span data-ttu-id="ef3bc-104">**头文件：** sqlncli.msi</span><span class="sxs-lookup"><span data-stu-id="ef3bc-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef3bc-105">语法</span><span class="sxs-lookup"><span data-stu-id="ef3bc-105">Syntax</span></span>  
  
```  
HRESULT LocalDBStopTracing();  
```  
  
## <a name="returns"></a><span data-ttu-id="ef3bc-106">返回</span><span class="sxs-lookup"><span data-stu-id="ef3bc-106">Returns</span></span>  
 <span data-ttu-id="ef3bc-107">S_OK</span><span class="sxs-lookup"><span data-stu-id="ef3bc-107">S_OK</span></span>  
 <span data-ttu-id="ef3bc-108">函数成功。</span><span class="sxs-lookup"><span data-stu-id="ef3bc-108">The function succeeded.</span></span>  
  
 [<span data-ttu-id="ef3bc-109">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="ef3bc-109">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="ef3bc-110">发生了意外错误。</span><span class="sxs-lookup"><span data-stu-id="ef3bc-110">An unexpected error occurred.</span></span> <span data-ttu-id="ef3bc-111">有关详细信息，请参阅事件日志。</span><span class="sxs-lookup"><span data-stu-id="ef3bc-111">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef3bc-112">备注</span><span class="sxs-lookup"><span data-stu-id="ef3bc-112">Remarks</span></span>  
 <span data-ttu-id="ef3bc-113">有关使用 LocalDB API 的代码示例，请参阅[SQL Server Express LocalDB 引用](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="ef3bc-113">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef3bc-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef3bc-114">See Also</span></span>  
 [<span data-ttu-id="ef3bc-115">SQL Server Express LocalDB 标头信息和版本信息</span><span class="sxs-lookup"><span data-stu-id="ef3bc-115">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
