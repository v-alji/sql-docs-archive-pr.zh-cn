---
title: LocalDBStartInstance 函数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBStartInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: cb325f5d-10ee-4a56-ba28-db0074ab3926
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 748bc373e8b0dbad0a91247e068d21b67f2dbc1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590823"
---
# <a name="localdbstartinstance-function"></a><span data-ttu-id="3b7b6-102">LocalDBStartInstance 函数</span><span class="sxs-lookup"><span data-stu-id="3b7b6-102">LocalDBStartInstance Function</span></span>
  <span data-ttu-id="3b7b6-103">启动指定的 SQL Server Express LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-103">Starts the specified SQL Server Express LocalDB instance.</span></span>  
  
 <span data-ttu-id="3b7b6-104">**头文件：** sqlncli.msi</span><span class="sxs-lookup"><span data-stu-id="3b7b6-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b7b6-105">语法</span><span class="sxs-lookup"><span data-stu-id="3b7b6-105">Syntax</span></span>  
  
```  
HRESULT LocalDBStartInstance(  
           PCWSTR pInstanceName,  
           DWORD dwFlags,   
           LPWSTR wszSqlConnection,   
           LPDWORD lpcchSqlConnection   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b7b6-106">参数</span><span class="sxs-lookup"><span data-stu-id="3b7b6-106">Parameters</span></span>  
 <span data-ttu-id="3b7b6-107">*pInstanceName*</span><span class="sxs-lookup"><span data-stu-id="3b7b6-107">*pInstanceName*</span></span>  
 <span data-ttu-id="3b7b6-108">[输入] 要启动的 LocalDB 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-108">[Input] The name of the LocalDB instance to start.</span></span>  
  
 <span data-ttu-id="3b7b6-109">dwFlags\*\*</span><span class="sxs-lookup"><span data-stu-id="3b7b6-109">*dwFlags*</span></span>  
 <span data-ttu-id="3b7b6-110">[输入] 保留供将来使用。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-110">[Input] Reserved for future use.</span></span> <span data-ttu-id="3b7b6-111">当前应设置为 0。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-111">Currently should be set to 0.</span></span>  
  
 <span data-ttu-id="3b7b6-112">*wszSqlConnection*</span><span class="sxs-lookup"><span data-stu-id="3b7b6-112">*wszSqlConnection*</span></span>  
 <span data-ttu-id="3b7b6-113">[输出] 要存储 LocalDB 实例的连接字符串的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-113">[Output] The buffer to store the connection string to the LocalDB instance.</span></span>  
  
 <span data-ttu-id="3b7b6-114">*lpcchSqlConnection*</span><span class="sxs-lookup"><span data-stu-id="3b7b6-114">*lpcchSqlConnection*</span></span>  
 <span data-ttu-id="3b7b6-115">[输入/输出]输入时包含*wszSqlConnection*缓冲区的大小（包括任何尾随 null）。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-115">[Input/Output] On input contains the size of the *wszSqlConnection* buffer in characters, including any trailing nulls.</span></span> <span data-ttu-id="3b7b6-116">输出时，如果给定的缓冲区太小，则包含所需的缓冲区大小（以字符为单位），包括任何尾随空格。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-116">On output, if the given buffer size is too small, contains the required buffer size in characters, including any trailing nulls.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="3b7b6-117">返回</span><span class="sxs-lookup"><span data-stu-id="3b7b6-117">Returns</span></span>  
 <span data-ttu-id="3b7b6-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="3b7b6-118">S_OK</span></span>  
 <span data-ttu-id="3b7b6-119">函数成功。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-119">The function succeeded.</span></span>  
  
 [<span data-ttu-id="3b7b6-120">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="3b7b6-120">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="3b7b6-121">计算机上没有安装 SQL Server Express LocalDB。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-121">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="3b7b6-122">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="3b7b6-122">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="3b7b6-123">一个或多个指定的输入参数无效。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-123">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="3b7b6-124">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="3b7b6-124">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="3b7b6-125">指定的实例名称无效。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-125">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="3b7b6-126">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="3b7b6-126">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="3b7b6-127">该实例不存在。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-127">The instance does not exist.</span></span>  
  
 [<span data-ttu-id="3b7b6-128">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="3b7b6-128">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span></span>](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 <span data-ttu-id="3b7b6-129">指定的缓冲区*wszSqlConnection*太小。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-129">The specified buffer *wszSqlConnection* is too small.</span></span>  
  
 [<span data-ttu-id="3b7b6-130">LOCALDB_ERROR_WAIT_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3b7b6-130">LOCALDB_ERROR_WAIT_TIMEOUT</span></span>](../express-localdb-error-messages/localdb-error-wait-timeout.md)  
 <span data-ttu-id="3b7b6-131">尝试获取同步锁定时超时。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-131">A time-out occurred while trying to acquire the synchronization locks.</span></span>  
  
 [<span data-ttu-id="3b7b6-132">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="3b7b6-132">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="3b7b6-133">应在其中存储该实例的路径的长度超过 MAX_PATH。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-133">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="3b7b6-134">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="3b7b6-134">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 <span data-ttu-id="3b7b6-135">无法检索用户配置文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-135">A user profile folder cannot be retrieved.</span></span>  
  
 [<span data-ttu-id="3b7b6-136">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="3b7b6-136">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 <span data-ttu-id="3b7b6-137">无法访问实例文件夹。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-137">An instance folder cannot be accessed.</span></span>  
  
 [<span data-ttu-id="3b7b6-138">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="3b7b6-138">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="3b7b6-139">无法访问实例注册表。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-139">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="3b7b6-140">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="3b7b6-140">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-modify-instance-registry.md)  
 <span data-ttu-id="3b7b6-141">无法修改实例注册表。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-141">An instance registry cannot be modified.</span></span>  
  
 [<span data-ttu-id="3b7b6-142">LOCALDB_ERROR_CANNOT_CREATE_SQL_PROCESS</span><span class="sxs-lookup"><span data-stu-id="3b7b6-142">LOCALDB_ERROR_CANNOT_CREATE_SQL_PROCESS</span></span>](../express-localdb-error-messages/localdb-error-cannot-create-sql-process.md)  
 <span data-ttu-id="3b7b6-143">无法创建 SQL Server 进程。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-143">A process for SQL Server cannot be created.</span></span>  
  
 [<span data-ttu-id="3b7b6-144">LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED</span><span class="sxs-lookup"><span data-stu-id="3b7b6-144">LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED</span></span>](../express-localdb-error-messages/localdb-error-sql-server-startup-failed.md)  
 <span data-ttu-id="3b7b6-145">SQL Server 进程已启动，但 SQL Server 启动失败。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-145">A SQL Server process was started, but SQL Server startup failed.</span></span>  
  
 [<span data-ttu-id="3b7b6-146">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="3b7b6-146">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="3b7b6-147">实例配置已损坏。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-147">An instance configuration was corrupted.</span></span>  
  
 [<span data-ttu-id="3b7b6-148">LOCALDB_ERROR_AUTO_INSTANCE_CREATE_FAILED</span><span class="sxs-lookup"><span data-stu-id="3b7b6-148">LOCALDB_ERROR_AUTO_INSTANCE_CREATE_FAILED</span></span>](../express-localdb-error-messages/localdb-error-auto-instance-create-failed.md)  
 <span data-ttu-id="3b7b6-149">不能创建自动实例。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-149">Cannot create an automatic instance.</span></span> <span data-ttu-id="3b7b6-150">有关错误详细信息，请参阅 Windows 应用程序事件日志。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-150">See the Windows Application event log for error details.</span></span>  
  
 [<span data-ttu-id="3b7b6-151">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="3b7b6-151">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="3b7b6-152">发生了意外错误。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-152">An unexpected error occurred.</span></span> <span data-ttu-id="3b7b6-153">有关详细信息，请参阅事件日志。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-153">See the event log for details.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3b7b6-154">详细信息</span><span class="sxs-lookup"><span data-stu-id="3b7b6-154">Details</span></span>  
 <span data-ttu-id="3b7b6-155">连接缓冲区参数 (*wszSqlConnection*) ，并且连接缓冲区大小参数 (*lpcchSqlConnection*) 是可选的。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-155">Both the connection buffer argument (*wszSqlConnection*) and the connection buffer size argument (*lpcchSqlConnection*) are optional.</span></span> <span data-ttu-id="3b7b6-156">下表显示了为使用这些参数提供的选项及其结果。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-156">The following table shows options for using these arguments and their results.</span></span>  
  
|<span data-ttu-id="3b7b6-157">Buffer</span><span class="sxs-lookup"><span data-stu-id="3b7b6-157">Buffer</span></span>|<span data-ttu-id="3b7b6-158">缓冲区大小</span><span class="sxs-lookup"><span data-stu-id="3b7b6-158">Buffer size</span></span>|<span data-ttu-id="3b7b6-159">理由</span><span class="sxs-lookup"><span data-stu-id="3b7b6-159">Rationale</span></span>|<span data-ttu-id="3b7b6-160">操作</span><span class="sxs-lookup"><span data-stu-id="3b7b6-160">Action</span></span>|  
|------------|-----------------|---------------|------------|  
|<span data-ttu-id="3b7b6-161">Null</span><span class="sxs-lookup"><span data-stu-id="3b7b6-161">NULL</span></span>|<span data-ttu-id="3b7b6-162">Null</span><span class="sxs-lookup"><span data-stu-id="3b7b6-162">NULL</span></span>|<span data-ttu-id="3b7b6-163">用户想要启动实例，而不需要管道名称。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-163">User wants to start the instance and doesn't need a pipe name.</span></span>|<span data-ttu-id="3b7b6-164">启动实例（不返回管道且不要求返回缓冲区大小）。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-164">Starts an instance (no pipe return and no required buffer size return).</span></span>|  
|<span data-ttu-id="3b7b6-165">Null</span><span class="sxs-lookup"><span data-stu-id="3b7b6-165">NULL</span></span>|<span data-ttu-id="3b7b6-166">现值</span><span class="sxs-lookup"><span data-stu-id="3b7b6-166">Present</span></span>|<span data-ttu-id="3b7b6-167">用户要求提供输出缓冲区大小。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-167">User asks for the output buffer size.</span></span> <span data-ttu-id="3b7b6-168">（在下一次调用中，用户将可能要求实际启动。)</span><span class="sxs-lookup"><span data-stu-id="3b7b6-168">(In the next call the user will probably ask for an actual start.)</span></span>|<span data-ttu-id="3b7b6-169">返回所需的缓冲区大小（不启动且不返回管道）。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-169">Returns a required buffer size (no start and no pipe return).</span></span> <span data-ttu-id="3b7b6-170">结果为 S_OK。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-170">Result is S_OK.</span></span>|  
|<span data-ttu-id="3b7b6-171">现值</span><span class="sxs-lookup"><span data-stu-id="3b7b6-171">Present</span></span>|<span data-ttu-id="3b7b6-172">Null</span><span class="sxs-lookup"><span data-stu-id="3b7b6-172">NULL</span></span>|<span data-ttu-id="3b7b6-173">不允许；输入不正确。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-173">Not allowed; incorrect input.</span></span>|<span data-ttu-id="3b7b6-174">返回结果为 LOCALDB_ERROR_INVALID_PARAMETER。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-174">Returned result is LOCALDB_ERROR_INVALID_PARAMETER.</span></span>|  
|<span data-ttu-id="3b7b6-175">现值</span><span class="sxs-lookup"><span data-stu-id="3b7b6-175">Present</span></span>|<span data-ttu-id="3b7b6-176">现值</span><span class="sxs-lookup"><span data-stu-id="3b7b6-176">Present</span></span>|<span data-ttu-id="3b7b6-177">用户想要启动实例，并且在启动后需要管道名称以便连接到此实例。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-177">User wants to start the instance and needs the pipe name to connect to it after it is started.</span></span>|<span data-ttu-id="3b7b6-178">检查缓冲区大小，启动实例，并在缓冲区中返回管道名称。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-178">Checks the buffer size, starts the instance, and returns the pipe name in the buffer.</span></span> <br /><span data-ttu-id="3b7b6-179">Buffer size 参数返回 "server =" 字符串的长度，不包括终止 null。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-179">The buffer size argument returns the length of the "server=" string, not including terminating nulls.</span></span>|  
  
 <span data-ttu-id="3b7b6-180">有关使用 LocalDB API 的代码示例，请参阅[SQL Server Express LocalDB 引用](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="3b7b6-180">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b7b6-181">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3b7b6-181">See Also</span></span>  
 [<span data-ttu-id="3b7b6-182">SQL Server Express LocalDB 标头信息和版本信息</span><span class="sxs-lookup"><span data-stu-id="3b7b6-182">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
