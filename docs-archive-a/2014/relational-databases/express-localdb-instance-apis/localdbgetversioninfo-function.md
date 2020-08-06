---
title: LocalDBGetVersionInfo 函数 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetVersionInfo
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: d4aaea30-1d0d-4436-bcdc-5c101d27b1c1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e30bb4dcd4c258db899883f650dbfe7100171ef8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693912"
---
# <a name="localdbgetversioninfo-function"></a><span data-ttu-id="5651d-102">LocalDBGetVersionInfo 函数</span><span class="sxs-lookup"><span data-stu-id="5651d-102">LocalDBGetVersionInfo Function</span></span>
  <span data-ttu-id="5651d-103">返回有关指定的 SQL Server Express LocalDB 版本的信息，如该版本是否存在以及完整的 LocalDB 版本号（包括内部版本号和发行版本号）。</span><span class="sxs-lookup"><span data-stu-id="5651d-103">Returns information for the specified SQL Server Express LocalDB version, such as whether it exists and the full LocalDB version number (including build and release numbers).</span></span>  
  
 <span data-ttu-id="5651d-104">此信息以名为 LocalDBVersionInfo 的形式返回 `struct` ， **LocalDBVersionInfo**该格式具有以下定义。</span><span class="sxs-lookup"><span data-stu-id="5651d-104">The information is returned in the form of a `struct` named **LocalDBVersionInfo**, which has the following definition.</span></span>  
  
```  
typedef struct _LocalDBVersionInfo  
{  
      // Contains the size of the LocalDBVersionInfo struct  
      DWORD  cbLocalDBVersionInfoSize;  
  
      // Holds the version name  
      TLocalDBVersionwszVersion;  
  
      // TRUE if the instance files exist on disk, FALSE otherwise  
      BOOL   bExists;  
  
      // Holds the LocalDB version for the instance in the format: major.minor.build.revision  
      DWORD  dwMajor;  
      DWORD  dwMinor;  
      DWORD  dwBuild;  
      DWORD  dwRevision;  
} LocalDBVersionInfo;  
  
```  
  
 <span data-ttu-id="5651d-105">**头文件：** sqlncli.msi</span><span class="sxs-lookup"><span data-stu-id="5651d-105">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5651d-106">语法</span><span class="sxs-lookup"><span data-stu-id="5651d-106">Syntax</span></span>  
  
```  
HRESULT LocalDBGetVersionInfo(  
           PCWSTR wszVersionName,           PLocalDBVersionInfo pVersionInfo,           DWORD dwVersionInfoSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5651d-107">参数</span><span class="sxs-lookup"><span data-stu-id="5651d-107">Parameters</span></span>  
 <span data-ttu-id="5651d-108">*wszVersionName*</span><span class="sxs-lookup"><span data-stu-id="5651d-108">*wszVersionName*</span></span>  
 <span data-ttu-id="5651d-109">[输入] LocalDB 版本名称。</span><span class="sxs-lookup"><span data-stu-id="5651d-109">[Input] The LocalDB version name.</span></span>  
  
 <span data-ttu-id="5651d-110">*pVersionInfo*</span><span class="sxs-lookup"><span data-stu-id="5651d-110">*pVersionInfo*</span></span>  
 <span data-ttu-id="5651d-111">[输出] 要存储有关 LocalDB 版本信息的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="5651d-111">[Output] The buffer to store the information about the LocalDB version.</span></span>  
  
 <span data-ttu-id="5651d-112">*dwVersionInfoSize*</span><span class="sxs-lookup"><span data-stu-id="5651d-112">*dwVersionInfoSize*</span></span>  
 <span data-ttu-id="5651d-113">送保存*VersionInfo*缓冲区的大小。</span><span class="sxs-lookup"><span data-stu-id="5651d-113">[Input] Holds the size of the *VersionInfo* buffer.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="5651d-114">返回</span><span class="sxs-lookup"><span data-stu-id="5651d-114">Returns</span></span>  
 <span data-ttu-id="5651d-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="5651d-115">S_OK</span></span>  
 <span data-ttu-id="5651d-116">函数成功。</span><span class="sxs-lookup"><span data-stu-id="5651d-116">The function succeeded.</span></span>  
  
 [<span data-ttu-id="5651d-117">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="5651d-117">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="5651d-118">计算机上没有安装 SQL Server Express LocalDB。</span><span class="sxs-lookup"><span data-stu-id="5651d-118">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="5651d-119">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="5651d-119">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="5651d-120">一个或多个指定的输入参数无效。</span><span class="sxs-lookup"><span data-stu-id="5651d-120">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="5651d-121">LOCALDB_ERROR_UNKNOWN_VERSION</span><span class="sxs-lookup"><span data-stu-id="5651d-121">LOCALDB_ERROR_UNKNOWN_VERSION</span></span>](../express-localdb-error-messages/localdb-error-unknown-version.md)  
 <span data-ttu-id="5651d-122">指定的 LocalDB 版本不存在。</span><span class="sxs-lookup"><span data-stu-id="5651d-122">The specified LocalDB version does not exist.</span></span>  
  
 [<span data-ttu-id="5651d-123">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="5651d-123">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="5651d-124">发生了意外错误。</span><span class="sxs-lookup"><span data-stu-id="5651d-124">An unexpected error occurred.</span></span> <span data-ttu-id="5651d-125">有关详细信息，请参阅事件日志。</span><span class="sxs-lookup"><span data-stu-id="5651d-125">See the event log for details.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5651d-126">详细信息</span><span class="sxs-lookup"><span data-stu-id="5651d-126">Details</span></span>  
 <span data-ttu-id="5651d-127">引入 `struct` 大小参数 (*lpVersionInfoSize*) 的基本原理是使 API 能够返回不同版本的**LocalDBVersionInfostruct**，从而有效地实现向前和向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="5651d-127">The rationale behind the introduction of the `struct` size argument (*lpVersionInfoSize*) is to enable the API to return different versions of the **LocalDBVersionInfostruct**, effectively enabling forward and backward compatibility.</span></span>  
  
 <span data-ttu-id="5651d-128">如果 `struct` size 参数 (*LpVersionInfoSize*) 与**LocalDBVersionInfostruct**的已知版本大小匹配，则返回该版本的 `struct` 。</span><span class="sxs-lookup"><span data-stu-id="5651d-128">If the `struct` size argument (*lpVersionInfoSize*) matches the size of a known version of the **LocalDBVersionInfostruct**, that version of the `struct` is returned.</span></span> <span data-ttu-id="5651d-129">否则，返回 LOCALDB_ERROR_INVALID_PARAMETER。</span><span class="sxs-lookup"><span data-stu-id="5651d-129">Otherwise, LOCALDB_ERROR_INVALID_PARAMETER is returned.</span></span>  
  
 <span data-ttu-id="5651d-130">**LocalDBGetVersionInfo** API 用法的典型示例如下所示：</span><span class="sxs-lookup"><span data-stu-id="5651d-130">A typical example of **LocalDBGetVersionInfo** API usage looks like this:</span></span>  
  
```  
LocalDBVersionInfo vi;  
LocalDBVersionInfo(L"11.0", &vi, sizeof(LocalDBVersionInfo));  
  
```  
  
## <a name="remarks"></a><span data-ttu-id="5651d-131">备注</span><span class="sxs-lookup"><span data-stu-id="5651d-131">Remarks</span></span>  
 <span data-ttu-id="5651d-132">有关使用 LocalDB API 的代码示例，请参阅[SQL Server Express LocalDB 引用](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="5651d-132">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5651d-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5651d-133">See Also</span></span>  
 [<span data-ttu-id="5651d-134">SQL Server Express LocalDB 标头信息和版本信息</span><span class="sxs-lookup"><span data-stu-id="5651d-134">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
