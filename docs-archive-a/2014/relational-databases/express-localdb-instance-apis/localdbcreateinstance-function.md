---
title: LocalDBCreateInstance 函数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBCreateInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 3eebb485-8a53-4a79-82a9-57b8de9f8e84
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ff822c552176ad8c083a1c8ea6c0f2430f72972f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589108"
---
# <a name="localdbcreateinstance-function"></a><span data-ttu-id="5f3db-102">LocalDBCreateInstance 函数</span><span class="sxs-lookup"><span data-stu-id="5f3db-102">LocalDBCreateInstance Function</span></span>
  <span data-ttu-id="5f3db-103">创建新的 SQL Server Express LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="5f3db-103">Creates a new SQL Server Express LocalDB instance.</span></span>  
  
 <span data-ttu-id="5f3db-104">**头文件：** sqlncli.msi</span><span class="sxs-lookup"><span data-stu-id="5f3db-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f3db-105">语法</span><span class="sxs-lookup"><span data-stu-id="5f3db-105">Syntax</span></span>  
  
```  
HRESULT LocalDBCreateInstance(  
           PCWSTR wszVersion,  
           PCWSTR pInstanceName,   
           DWORD dwFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f3db-106">参数</span><span class="sxs-lookup"><span data-stu-id="5f3db-106">Parameters</span></span>  
 <span data-ttu-id="5f3db-107">*wszVersion*</span><span class="sxs-lookup"><span data-stu-id="5f3db-107">*wszVersion*</span></span>  
 <span data-ttu-id="5f3db-108">[输入] LocalDB 版本，例如 11.0 或 11.0.1094.2。</span><span class="sxs-lookup"><span data-stu-id="5f3db-108">[Input] The LocalDB version, for example 11.0 or 11.0.1094.2.</span></span>  
  
 <span data-ttu-id="5f3db-109">*pInstanceName*</span><span class="sxs-lookup"><span data-stu-id="5f3db-109">*pInstanceName*</span></span>  
 <span data-ttu-id="5f3db-110">[输入] 要创建的 LocalDB 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="5f3db-110">[Input] The name for the LocalDB instance to create.</span></span>  
  
 <span data-ttu-id="5f3db-111">dwFlags\*\*</span><span class="sxs-lookup"><span data-stu-id="5f3db-111">*dwFlags*</span></span>  
 <span data-ttu-id="5f3db-112">[输入] 保留供将来使用。</span><span class="sxs-lookup"><span data-stu-id="5f3db-112">[Input] Reserved for future use.</span></span> <span data-ttu-id="5f3db-113">当前应设置为 0。</span><span class="sxs-lookup"><span data-stu-id="5f3db-113">Currently should be set to 0.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="5f3db-114">返回</span><span class="sxs-lookup"><span data-stu-id="5f3db-114">Returns</span></span>  
 <span data-ttu-id="5f3db-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="5f3db-115">S_OK</span></span>  
 <span data-ttu-id="5f3db-116">函数成功。</span><span class="sxs-lookup"><span data-stu-id="5f3db-116">The function succeeded.</span></span>  
  
 [<span data-ttu-id="5f3db-117">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="5f3db-117">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="5f3db-118">计算机上没有安装 SQL Server Express LocalDB。</span><span class="sxs-lookup"><span data-stu-id="5f3db-118">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="5f3db-119">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="5f3db-119">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="5f3db-120">一个或多个指定的输入参数无效。</span><span class="sxs-lookup"><span data-stu-id="5f3db-120">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="5f3db-121">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="5f3db-121">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="5f3db-122">指定的实例名称无效。</span><span class="sxs-lookup"><span data-stu-id="5f3db-122">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="5f3db-123">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="5f3db-123">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="5f3db-124">应在其中存储该实例的路径的长度超过 MAX_PATH。</span><span class="sxs-lookup"><span data-stu-id="5f3db-124">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="5f3db-125">LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION</span><span class="sxs-lookup"><span data-stu-id="5f3db-125">LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION</span></span>](../express-localdb-error-messages/localdb-error-instance-exists-with-lower-version.md)  
 <span data-ttu-id="5f3db-126">指定的实例已存在，但其版本低于请求的版本。</span><span class="sxs-lookup"><span data-stu-id="5f3db-126">The specified instance already exists but its version is lower than requested.</span></span>  
  
 [<span data-ttu-id="5f3db-127">LOCALDB_ERROR_UNKNOWN_VERSION</span><span class="sxs-lookup"><span data-stu-id="5f3db-127">LOCALDB_ERROR_UNKNOWN_VERSION</span></span>](../express-localdb-error-messages/localdb-error-unknown-version.md)  
 <span data-ttu-id="5f3db-128">指定的版本不可用。</span><span class="sxs-lookup"><span data-stu-id="5f3db-128">The specified version is not available.</span></span>  
  
 [<span data-ttu-id="5f3db-129">LOCALDB_ERROR_VERSION_REQUESTED_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="5f3db-129">LOCALDB_ERROR_VERSION_REQUESTED_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-version-requested-not-installed.md)  
 <span data-ttu-id="5f3db-130">没有安装指定的修补程序级别。</span><span class="sxs-lookup"><span data-stu-id="5f3db-130">The specified patch level is not installed.</span></span>  
  
 [<span data-ttu-id="5f3db-131">LOCALDB_ERROR_CANNOT_CREATE_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="5f3db-131">LOCALDB_ERROR_CANNOT_CREATE_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-create-instance-folder.md)  
 <span data-ttu-id="5f3db-132">不能在 %userprofile% 下创建文件夹。</span><span class="sxs-lookup"><span data-stu-id="5f3db-132">A folder cannot be created under %userprofile%.</span></span>  
  
 [<span data-ttu-id="5f3db-133">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="5f3db-133">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 <span data-ttu-id="5f3db-134">无法检索用户配置文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="5f3db-134">A user profile folder cannot be retrieved.</span></span>  
  
 [<span data-ttu-id="5f3db-135">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="5f3db-135">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 <span data-ttu-id="5f3db-136">无法访问实例文件夹。</span><span class="sxs-lookup"><span data-stu-id="5f3db-136">An instance folder cannot be accessed.</span></span>  
  
 [<span data-ttu-id="5f3db-137">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="5f3db-137">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="5f3db-138">无法访问实例注册表。</span><span class="sxs-lookup"><span data-stu-id="5f3db-138">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="5f3db-139">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="5f3db-139">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-modify-instance-registry.md)  
 <span data-ttu-id="5f3db-140">无法修改实例注册表。</span><span class="sxs-lookup"><span data-stu-id="5f3db-140">An instance registry cannot be modified.</span></span>  
  
 [<span data-ttu-id="5f3db-141">LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED</span><span class="sxs-lookup"><span data-stu-id="5f3db-141">LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED</span></span>](../express-localdb-error-messages/localdb-error-sql-server-startup-failed.md)  
 <span data-ttu-id="5f3db-142">SQL Server 进程已启动，但 SQL Server 启动失败。</span><span class="sxs-lookup"><span data-stu-id="5f3db-142">A SQL Server process is started but SQL Server startup failed.</span></span>  
  
 [<span data-ttu-id="5f3db-143">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="5f3db-143">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="5f3db-144">实例配置已损坏。</span><span class="sxs-lookup"><span data-stu-id="5f3db-144">An instance configuration is corrupted.</span></span>  
  
 [<span data-ttu-id="5f3db-145">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="5f3db-145">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="5f3db-146">发生了意外错误。</span><span class="sxs-lookup"><span data-stu-id="5f3db-146">An unexpected error occurred.</span></span> <span data-ttu-id="5f3db-147">有关详细信息，请参阅事件日志。</span><span class="sxs-lookup"><span data-stu-id="5f3db-147">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f3db-148">备注</span><span class="sxs-lookup"><span data-stu-id="5f3db-148">Remarks</span></span>  
 <span data-ttu-id="5f3db-149">如果 LocalDB 实例完全正常运行，指定的名称已存在并且其版本等于或高于所请求的版本，则结果为 S_OK。</span><span class="sxs-lookup"><span data-stu-id="5f3db-149">If a fully functional LocalDB instance with the specified name already exists and its version is equal to or higher than requested, the result is S_OK.</span></span>  
  
 <span data-ttu-id="5f3db-150">在现有实例损坏的情况下，对 `LocalDBCreateInstance` API 方法的后续调用将失败。</span><span class="sxs-lookup"><span data-stu-id="5f3db-150">In cases when an existing instance becomes corrupted, subsequent calls to the `LocalDBCreateInstance` API method will fail.</span></span> <span data-ttu-id="5f3db-151">必须手动修复损坏的实例或显式删除它们，然后才能再次使用。</span><span class="sxs-lookup"><span data-stu-id="5f3db-151">Corrupted instances must be fixed manually or explicitly deleted before they can be used again.</span></span>  
  
 <span data-ttu-id="5f3db-152">有关使用 LocalDB API 的代码示例，请参阅[SQL Server Express LocalDB 引用](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="5f3db-152">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f3db-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5f3db-153">See Also</span></span>  
 [<span data-ttu-id="5f3db-154">SQL Server Express LocalDB 标头信息和版本信息</span><span class="sxs-lookup"><span data-stu-id="5f3db-154">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
