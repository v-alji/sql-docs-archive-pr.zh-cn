---
title: LocalDBStopInstance 函数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBStopInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 4bd73187-0aac-4f03-ac54-2b78e41917e5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 48b014e65e0a02a5f866e5301b12dae3cd255b95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682837"
---
# <a name="localdbstopinstance-function"></a><span data-ttu-id="8d791-102">LocalDBStopInstance 函数</span><span class="sxs-lookup"><span data-stu-id="8d791-102">LocalDBStopInstance Function</span></span>
  <span data-ttu-id="8d791-103">停止运行指定的 SQL Server Express LocalD 实例。</span><span class="sxs-lookup"><span data-stu-id="8d791-103">Stops the specified SQL Server Express LocalDB instance from running.</span></span>  
  
 <span data-ttu-id="8d791-104">**头文件：** sqlncli.msi</span><span class="sxs-lookup"><span data-stu-id="8d791-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d791-105">语法</span><span class="sxs-lookup"><span data-stu-id="8d791-105">Syntax</span></span>  
  
```  
HRESULT LocalDBStopInstance(  
           PCWSTR pInstanceName,  
           DWORD dwFlags,   
           ULONG ulTimeout   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d791-106">参数</span><span class="sxs-lookup"><span data-stu-id="8d791-106">Parameters</span></span>  
 <span data-ttu-id="8d791-107">*pInstanceName*</span><span class="sxs-lookup"><span data-stu-id="8d791-107">*pInstanceName*</span></span>  
 <span data-ttu-id="8d791-108">[输入] 要停止的 LocalDB 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="8d791-108">[Input] The name of the LocalDB instance to stop.</span></span>  
  
 <span data-ttu-id="8d791-109">dwFlags\*\*</span><span class="sxs-lookup"><span data-stu-id="8d791-109">*dwFlags*</span></span>  
 <span data-ttu-id="8d791-110">[输入] 指定要停止该实例的方法的一个标志或标志组合。</span><span class="sxs-lookup"><span data-stu-id="8d791-110">[Input] One or a combination of the flag values specifying the way to stop the instance.</span></span>  
  
 <span data-ttu-id="8d791-111">可用标志：</span><span class="sxs-lookup"><span data-stu-id="8d791-111">Available flags:</span></span>  
  
 <span data-ttu-id="8d791-112">LOCALDB_SHUTDOWN_KILL_PROCESS</span><span class="sxs-lookup"><span data-stu-id="8d791-112">LOCALDB_SHUTDOWN_KILL_PROCESS</span></span>  
 <span data-ttu-id="8d791-113">使用终止进程操作系统命令立即关闭。</span><span class="sxs-lookup"><span data-stu-id="8d791-113">Shut down immediately using the kill process operating system command.</span></span>  
  
 <span data-ttu-id="8d791-114">LOCALDB_SHUTDOWN_WITH_NOWAIT</span><span class="sxs-lookup"><span data-stu-id="8d791-114">LOCALDB_SHUTDOWN_WITH_NOWAIT</span></span>  
 <span data-ttu-id="8d791-115">使用 Transact-SQL 命令 WITH NOWAIT 选项关闭。</span><span class="sxs-lookup"><span data-stu-id="8d791-115">Shut down using the WITH NOWAIT option Transact-SQL command.</span></span>  
  
 <span data-ttu-id="8d791-116">如果没有设置标志，则使用 Transact-SQL 命令 SHUTDOWN 关闭 LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="8d791-116">If none of the flags is set, the LocalDB instance will be shut down using the SHUTDOWN Transact-SQL command.</span></span> <span data-ttu-id="8d791-117">如果同时设置了这两个标志，则优先使用 LOCALDB_SHUTDOWN_KILL_PROCESS 标志。</span><span class="sxs-lookup"><span data-stu-id="8d791-117">If both flags are set, the LOCALDB_SHUTDOWN_KILL_PROCESS flag takes precedence.</span></span>  
  
 <span data-ttu-id="8d791-118">*ulTimeout*</span><span class="sxs-lookup"><span data-stu-id="8d791-118">*ulTimeout*</span></span>  
 <span data-ttu-id="8d791-119">[输入] 等待此操作完成的时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="8d791-119">[Input] The time in seconds to wait for this operation to complete.</span></span> <span data-ttu-id="8d791-120">如果该值为 0，此函数将立即返回，而不等待 LocalDB 实例停止。</span><span class="sxs-lookup"><span data-stu-id="8d791-120">If this value is 0, this function will return immediately without waiting for the LocalDB instance to stop.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="8d791-121">返回</span><span class="sxs-lookup"><span data-stu-id="8d791-121">Returns</span></span>  
 <span data-ttu-id="8d791-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="8d791-122">S_OK</span></span>  
 <span data-ttu-id="8d791-123">函数成功。</span><span class="sxs-lookup"><span data-stu-id="8d791-123">The function succeeded.</span></span>  
  
 [<span data-ttu-id="8d791-124">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="8d791-124">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="8d791-125">计算机上没有安装 SQL Server Express LocalDB。</span><span class="sxs-lookup"><span data-stu-id="8d791-125">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="8d791-126">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="8d791-126">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="8d791-127">一个或多个指定的输入参数无效。</span><span class="sxs-lookup"><span data-stu-id="8d791-127">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="8d791-128">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="8d791-128">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="8d791-129">指定的实例名称无效。</span><span class="sxs-lookup"><span data-stu-id="8d791-129">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="8d791-130">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="8d791-130">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="8d791-131">该实例不存在。</span><span class="sxs-lookup"><span data-stu-id="8d791-131">The instance does not exist.</span></span>  
  
 [<span data-ttu-id="8d791-132">LOCALDB_ERROR_WAIT_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8d791-132">LOCALDB_ERROR_WAIT_TIMEOUT</span></span>](../express-localdb-error-messages/localdb-error-wait-timeout.md)  
 <span data-ttu-id="8d791-133">尝试获取同步锁定时超时。</span><span class="sxs-lookup"><span data-stu-id="8d791-133">A time-out occurred while trying to acquire the synchronization locks.</span></span>  
  
 [<span data-ttu-id="8d791-134">LOCALDB_ERROR_INSTANCE_STOP_FAILED</span><span class="sxs-lookup"><span data-stu-id="8d791-134">LOCALDB_ERROR_INSTANCE_STOP_FAILED</span></span>](../express-localdb-error-messages/localdb-error-instance-stop-failed.md)  
 <span data-ttu-id="8d791-135">停止操作在给定的时间内未能完成。</span><span class="sxs-lookup"><span data-stu-id="8d791-135">The stop operation failed to complete within the given time.</span></span>  
  
 [<span data-ttu-id="8d791-136">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="8d791-136">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="8d791-137">应在其中存储该实例的路径的长度超过 MAX_PATH。</span><span class="sxs-lookup"><span data-stu-id="8d791-137">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="8d791-138">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="8d791-138">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 <span data-ttu-id="8d791-139">无法检索用户配置文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="8d791-139">A user profile folder cannot be retrieved.</span></span>  
  
 [<span data-ttu-id="8d791-140">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="8d791-140">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 <span data-ttu-id="8d791-141">无法访问实例文件夹。</span><span class="sxs-lookup"><span data-stu-id="8d791-141">An instance folder cannot be accessed.</span></span>  
  
 [<span data-ttu-id="8d791-142">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="8d791-142">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="8d791-143">无法访问实例注册表。</span><span class="sxs-lookup"><span data-stu-id="8d791-143">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="8d791-144">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="8d791-144">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="8d791-145">实例配置已损坏。</span><span class="sxs-lookup"><span data-stu-id="8d791-145">An instance configuration is corrupted.</span></span>  
  
 [<span data-ttu-id="8d791-146">LOCALDB_ERROR_CALLER_IS_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8d791-146">LOCALDB_ERROR_CALLER_IS_NOT_OWNER</span></span>](../express-localdb-error-messages/localdb-error-caller-is-not-owner.md)  
 <span data-ttu-id="8d791-147">API 调用方不是 LocalDB 实例所有者。</span><span class="sxs-lookup"><span data-stu-id="8d791-147">API caller is not LocalDB instance owner.</span></span>  
  
 [<span data-ttu-id="8d791-148">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="8d791-148">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="8d791-149">发生了意外错误。</span><span class="sxs-lookup"><span data-stu-id="8d791-149">An unexpected error occurred.</span></span> <span data-ttu-id="8d791-150">有关详细信息，请参阅事件日志。</span><span class="sxs-lookup"><span data-stu-id="8d791-150">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d791-151">备注</span><span class="sxs-lookup"><span data-stu-id="8d791-151">Remarks</span></span>  
 <span data-ttu-id="8d791-152">有关使用 LocalDB API 的代码示例，请参阅[SQL Server Express LocalDB 引用](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="8d791-152">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d791-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d791-153">See Also</span></span>  
 [<span data-ttu-id="8d791-154">SQL Server Express LocalDB 标头信息和版本信息</span><span class="sxs-lookup"><span data-stu-id="8d791-154">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
