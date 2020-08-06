---
title: LocalDBGetInstanceInfo 函数 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetInstanceInfo
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 231706f5-26c6-42eb-ab47-315df6b8f824
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dc7cbe2c59a7502a1fd0c8b4f92fb14e5defd50b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579592"
---
# <a name="localdbgetinstanceinfo-function"></a><span data-ttu-id="477b8-102">LocalDBGetInstanceInfo 函数</span><span class="sxs-lookup"><span data-stu-id="477b8-102">LocalDBGetInstanceInfo Function</span></span>
  <span data-ttu-id="477b8-103">返回有关指定的 SQL Server Express LocalDB 实例的信息，如该实例是否存在、实例使用的 LocalDB 版本以及实例是否正在运行等。</span><span class="sxs-lookup"><span data-stu-id="477b8-103">Returns information for the specified SQL Server Express LocalDB instance, such as whether it exists, the LocalDB version it uses, whether it is running, and so on.</span></span>  
  
 <span data-ttu-id="477b8-104">此信息将在 `struct` 名为**LocalDBInstanceInfo**的中返回，该名称具有以下定义。</span><span class="sxs-lookup"><span data-stu-id="477b8-104">The information is returned in a `struct` named **LocalDBInstanceInfo**, which has the following definition.</span></span>  
  
```  
typedef struct _LocalDBInstanceInfo  
{  
      // Contains the size of the LocalDBInstanceInfo struct  
      DWORD  cbLocalDBInstanceInfoSize;  
  
      // Holds the instance name  
      TLocalDBInstanceNamewszInstanceName;  
  
      // TRUE if the instance files exist on disk, FALSE otherwise  
      BOOL   bExists;  
  
      // TRUE if the instance configuration registry is corrupted, FALSE otherwise  
      BOOLbConfigurationCorrupted;  
  
      // TRUE if the instance is running at the moment, FALSE otherwise  
      BOOL   bIsRunning;  
  
      // Holds the LocalDB version for the instance in the format: major.minor.build.revision  
      DWORD  dwMajor;  
      DWORD  dwMinor;  
      DWORD  dwBuild;  
      DWORD  dwRevision;  
  
      // Holds the date and time when the instance was started for the last time  
      FILETIME ftLastStartUTC;  
  
      // Holds the name of the TDS named pipe to connect to the instance  
      WCHARwszConnection;  
  
      // TRUE if the instance is shared, FALSE otherwise  
      BOOLbIsShared;  
  
      // Holds the shared name for the instance (if the instance is shared)  
      TLocalDBInstanceNamewszSharedInstanceName;  
  
      // Holds the SID of the instance owner (if the instance is shared)  
      WCHARwszOwnerSID;   
  
      // TRUE if the instance is Automatic, FALSE otherwise  
      BOOLbIsAutomatic;  
} LocalDBInstanceInfo;  
  
```  
  
 <span data-ttu-id="477b8-105">**头文件：** sqlncli.msi</span><span class="sxs-lookup"><span data-stu-id="477b8-105">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="477b8-106">语法</span><span class="sxs-lookup"><span data-stu-id="477b8-106">Syntax</span></span>  
  
```  
HRESULT LocalDBGetInstanceInfo(  
           PCWSTR wszInstanceName,  
           PLocalDBInstanceInfo pInstanceInfo,  
           DWORD dwInstanceInfoSize   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="477b8-107">参数</span><span class="sxs-lookup"><span data-stu-id="477b8-107">Parameters</span></span>  
 <span data-ttu-id="477b8-108">*wszInstanceName*</span><span class="sxs-lookup"><span data-stu-id="477b8-108">*wszInstanceName*</span></span>  
 <span data-ttu-id="477b8-109">[输入] 实例名称。</span><span class="sxs-lookup"><span data-stu-id="477b8-109">[Input] The instance name.</span></span>  
  
 <span data-ttu-id="477b8-110">*pInstanceInfo*</span><span class="sxs-lookup"><span data-stu-id="477b8-110">*pInstanceInfo*</span></span>  
 <span data-ttu-id="477b8-111">[输出] 要存储有关 LocalDB 实例信息的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="477b8-111">[Output] The buffer to store the information about the LocalDB instance.</span></span>  
  
 <span data-ttu-id="477b8-112">*dwInstanceInfoSize*</span><span class="sxs-lookup"><span data-stu-id="477b8-112">*dwInstanceInfoSize*</span></span>  
 <span data-ttu-id="477b8-113">送保存*InstanceInfo*缓冲区的大小。</span><span class="sxs-lookup"><span data-stu-id="477b8-113">[Input] Holds the size of the *InstanceInfo* buffer.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="477b8-114">返回</span><span class="sxs-lookup"><span data-stu-id="477b8-114">Returns</span></span>  
 <span data-ttu-id="477b8-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="477b8-115">S_OK</span></span>  
 <span data-ttu-id="477b8-116">函数成功。</span><span class="sxs-lookup"><span data-stu-id="477b8-116">The function succeeded.</span></span>  
  
 [<span data-ttu-id="477b8-117">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="477b8-117">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="477b8-118">计算机上没有安装 SQL Server Express LocalDB。</span><span class="sxs-lookup"><span data-stu-id="477b8-118">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="477b8-119">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="477b8-119">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="477b8-120">一个或多个指定的输入参数无效。</span><span class="sxs-lookup"><span data-stu-id="477b8-120">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="477b8-121">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="477b8-121">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="477b8-122">指定的实例名称无效。</span><span class="sxs-lookup"><span data-stu-id="477b8-122">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="477b8-123">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="477b8-123">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="477b8-124">该实例不存在。</span><span class="sxs-lookup"><span data-stu-id="477b8-124">The instance does not exist.</span></span>  
  
 [<span data-ttu-id="477b8-125">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="477b8-125">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="477b8-126">应在其中存储该实例的路径的长度超过 MAX_PATH。</span><span class="sxs-lookup"><span data-stu-id="477b8-126">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="477b8-127">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="477b8-127">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 <span data-ttu-id="477b8-128">无法访问实例文件夹。</span><span class="sxs-lookup"><span data-stu-id="477b8-128">An instance folder cannot be accessed.</span></span>  
  
 [<span data-ttu-id="477b8-129">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="477b8-129">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="477b8-130">无法访问实例注册表。</span><span class="sxs-lookup"><span data-stu-id="477b8-130">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="477b8-131">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="477b8-131">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="477b8-132">实例配置已损坏。</span><span class="sxs-lookup"><span data-stu-id="477b8-132">An instance configuration is corrupted.</span></span>  
  
 [<span data-ttu-id="477b8-133">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="477b8-133">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="477b8-134">发生了意外错误。</span><span class="sxs-lookup"><span data-stu-id="477b8-134">An unexpected error occurred.</span></span> <span data-ttu-id="477b8-135">有关详细信息，请参阅事件日志。</span><span class="sxs-lookup"><span data-stu-id="477b8-135">See the event log for details.</span></span>  
  
## <a name="details"></a><span data-ttu-id="477b8-136">详细信息</span><span class="sxs-lookup"><span data-stu-id="477b8-136">Details</span></span>  
 <span data-ttu-id="477b8-137">引入 `struct` 大小参数 (*lpInstanceInfoSize*) 的基本原理是使 API 能够返回不同版本的**LocalDBInstanceInfostruct**，从而有效地实现向前和向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="477b8-137">The rationale behind the introduction of the `struct` size argument (*lpInstanceInfoSize*) is to enable the API to return different versions of the **LocalDBInstanceInfostruct**, effectively enabling forward and backward compatibility.</span></span>  
  
 <span data-ttu-id="477b8-138">如果 `struct` size 参数 (*LpInstanceInfoSize*) 与**LocalDBInstanceInfostruct**的已知版本大小匹配，则返回该版本的 `struct` 。</span><span class="sxs-lookup"><span data-stu-id="477b8-138">If the `struct` size argument (*lpInstanceInfoSize*) matches the size of a known version of the **LocalDBInstanceInfostruct**, that version of the `struct` is returned.</span></span> <span data-ttu-id="477b8-139">否则，返回 LOCALDB_ERROR_INVALID_PARAMETER。</span><span class="sxs-lookup"><span data-stu-id="477b8-139">Otherwise, LOCALDB_ERROR_INVALID_PARAMETER is returned.</span></span>  
  
 <span data-ttu-id="477b8-140">**LocalDBGetInstanceInfo** API 用法的典型示例如下所示：</span><span class="sxs-lookup"><span data-stu-id="477b8-140">A typical example of **LocalDBGetInstanceInfo** API usage looks like this:</span></span>  
  
```  
LocalDBInstanceInfo ii;  
LocalDBInstanceInfo(L"Test", &ii, sizeof(LocalDBInstanceInfo));  
  
```  
  
 <span data-ttu-id="477b8-141">有关使用 LocalDB API 的代码示例，请参阅[SQL Server Express LocalDB 引用](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="477b8-141">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="477b8-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="477b8-142">See Also</span></span>  
 [<span data-ttu-id="477b8-143">SQL Server Express LocalDB 标头信息和版本信息</span><span class="sxs-lookup"><span data-stu-id="477b8-143">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
