---
title: LocalDBStartTracing 函数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBStartTracing
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: c7b83833-6d2a-4a06-9cb7-42767bed52c6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1b10482e9839d43e29da72dbe2c194a01d8248eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694471"
---
# <a name="localdbstarttracing-function"></a><span data-ttu-id="a96db-102">LocalDBStartTracing 函数</span><span class="sxs-lookup"><span data-stu-id="a96db-102">LocalDBStartTracing Function</span></span>
  <span data-ttu-id="a96db-103">对当前 Windows 用户拥有的所有 SQL Server Express LocalDB 实例启用 API 调用跟踪。</span><span class="sxs-lookup"><span data-stu-id="a96db-103">Enables tracing of API calls for all the SQL Server Express LocalDB instances owned by the current Windows user.</span></span>  
  
 <span data-ttu-id="a96db-104">**头文件：** sqlncli.msi</span><span class="sxs-lookup"><span data-stu-id="a96db-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a96db-105">语法</span><span class="sxs-lookup"><span data-stu-id="a96db-105">Syntax</span></span>  
  
```  
HRESULT LocalDBStartTracing();  
```  
  
## <a name="returns"></a><span data-ttu-id="a96db-106">返回</span><span class="sxs-lookup"><span data-stu-id="a96db-106">Returns</span></span>  
 <span data-ttu-id="a96db-107">S_OK</span><span class="sxs-lookup"><span data-stu-id="a96db-107">S_OK</span></span>  
 <span data-ttu-id="a96db-108">函数成功。</span><span class="sxs-lookup"><span data-stu-id="a96db-108">The function succeeded.</span></span>  
  
 [<span data-ttu-id="a96db-109">LOCALDB_ERROR_XEVENT_FAILED</span><span class="sxs-lookup"><span data-stu-id="a96db-109">LOCALDB_ERROR_XEVENT_FAILED</span></span>](../express-localdb-error-messages/localdb-error-xevent-failed.md)  
 <span data-ttu-id="a96db-110">无法启动 LocalDB 实例 API 内的 XEvent 引擎。</span><span class="sxs-lookup"><span data-stu-id="a96db-110">Failed to start XEvent engine within the LocalDB Instance API.</span></span>  
  
 [<span data-ttu-id="a96db-111">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="a96db-111">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="a96db-112">发生了意外错误。</span><span class="sxs-lookup"><span data-stu-id="a96db-112">An unexpected error occurred.</span></span> <span data-ttu-id="a96db-113">有关详细信息，请参阅事件日志。</span><span class="sxs-lookup"><span data-stu-id="a96db-113">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a96db-114">备注</span><span class="sxs-lookup"><span data-stu-id="a96db-114">Remarks</span></span>  
 <span data-ttu-id="a96db-115">有关使用 LocalDB API 的代码示例，请参阅[SQL Server Express LocalDB 引用](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="a96db-115">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a96db-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a96db-116">See Also</span></span>  
 [<span data-ttu-id="a96db-117">SQL Server Express LocalDB 标头信息和版本信息</span><span class="sxs-lookup"><span data-stu-id="a96db-117">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
