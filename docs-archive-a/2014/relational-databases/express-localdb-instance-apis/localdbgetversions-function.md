---
title: LocalDBGetVersions 函数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetVersions
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 033a9c6b-0d7f-4f8a-ab60-33cd6fee0d33
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 37d2a927346252f1b126f5e3a4ec78ea03cde0a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693366"
---
# <a name="localdbgetversions-function"></a><span data-ttu-id="12f97-102">LocalDBGetVersions 函数</span><span class="sxs-lookup"><span data-stu-id="12f97-102">LocalDBGetVersions Function</span></span>
  <span data-ttu-id="12f97-103">返回计算机上的所有可用 SQL Server Express LocalDB 版本。</span><span class="sxs-lookup"><span data-stu-id="12f97-103">Returns all SQL Server Express LocalDB versions available on the computer.</span></span>  
  
 <span data-ttu-id="12f97-104">**头文件：** sqlncli.msi</span><span class="sxs-lookup"><span data-stu-id="12f97-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12f97-105">语法</span><span class="sxs-lookup"><span data-stu-id="12f97-105">Syntax</span></span>  
  
```  
#define MAX_LOCALDB_VERSION_LENGTH 43typedef WCHAR TLocalDBVersion[MAX_LOCALDB_VERSION_LENGTH + 1];typedef TLocalDBVersion* PTLocalDBVersion;HRESULT LocalDBGetVersions(           PTLocalDBVersion pVersion,           LPDWORD lpdwNumberOfVersions);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12f97-106">参数</span><span class="sxs-lookup"><span data-stu-id="12f97-106">Parameters</span></span>  
 <span data-ttu-id="12f97-107">*pVersionNames*</span><span class="sxs-lookup"><span data-stu-id="12f97-107">*pVersionNames*</span></span>  
 <span data-ttu-id="12f97-108">输出包含用户工作站上可用的 LocalDB 版本的名称。</span><span class="sxs-lookup"><span data-stu-id="12f97-108">[Output] Contains names of the LocalDB versions that are available on the user's workstation.</span></span>  
  
 <span data-ttu-id="12f97-109">*lpdwNumberOfVersions*</span><span class="sxs-lookup"><span data-stu-id="12f97-109">*lpdwNumberOfVersions*</span></span>  
 <span data-ttu-id="12f97-110">[输入/输出]输入时保存*pVersionNames*缓冲区中版本的槽数。</span><span class="sxs-lookup"><span data-stu-id="12f97-110">[Input/Output] On input holds the number of slots for versions in the *pVersionNames* buffer.</span></span>   
<span data-ttu-id="12f97-111">在输出时，将包含现有 LocalDB 版本的数目。</span><span class="sxs-lookup"><span data-stu-id="12f97-111">On output, holds the number of existing LocalDB versions.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="12f97-112">返回</span><span class="sxs-lookup"><span data-stu-id="12f97-112">Returns</span></span>  
 <span data-ttu-id="12f97-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="12f97-113">S_OK</span></span>  
 <span data-ttu-id="12f97-114">函数成功。</span><span class="sxs-lookup"><span data-stu-id="12f97-114">The function succeeded.</span></span>  
  
 [<span data-ttu-id="12f97-115">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="12f97-115">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="12f97-116">计算机上没有安装 SQL Server Express LocalDB。</span><span class="sxs-lookup"><span data-stu-id="12f97-116">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="12f97-117">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="12f97-117">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="12f97-118">一个或多个指定的输入参数无效。</span><span class="sxs-lookup"><span data-stu-id="12f97-118">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="12f97-119">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="12f97-119">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span></span>](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 <span data-ttu-id="12f97-120">输入的缓冲区太小，并且没有要求截断。</span><span class="sxs-lookup"><span data-stu-id="12f97-120">The input buffer is too short, and truncation was not requested.</span></span>  
  
 [<span data-ttu-id="12f97-121">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="12f97-121">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="12f97-122">发生了意外错误。</span><span class="sxs-lookup"><span data-stu-id="12f97-122">An unexpected error occurred.</span></span> <span data-ttu-id="12f97-123">有关详细信息，请参阅事件日志。</span><span class="sxs-lookup"><span data-stu-id="12f97-123">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12f97-124">备注</span><span class="sxs-lookup"><span data-stu-id="12f97-124">Remarks</span></span>  
 <span data-ttu-id="12f97-125">有关使用 LocalDB API 的代码示例，请参阅[SQL Server Express LocalDB 引用](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="12f97-125">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f97-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="12f97-126">See Also</span></span>  
 [<span data-ttu-id="12f97-127">SQL Server Express LocalDB 标头信息和版本信息</span><span class="sxs-lookup"><span data-stu-id="12f97-127">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
