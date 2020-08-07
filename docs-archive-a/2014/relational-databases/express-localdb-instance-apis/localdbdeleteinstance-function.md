---
title: LocalDBDeleteInstance 函数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBDeleteInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 37cb2a7e-672a-4223-b6f3-a94d7b8d58cd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8d4c873e045c5effed476ca9d147270d159ec3b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589103"
---
# <a name="localdbdeleteinstance-function"></a><span data-ttu-id="f0899-102">LocalDBDeleteInstance 函数</span><span class="sxs-lookup"><span data-stu-id="f0899-102">LocalDBDeleteInstance Function</span></span>
  <span data-ttu-id="f0899-103">删除指定的 SQL Server Express LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="f0899-103">Removes the specified SQL Server Express LocalDB instance.</span></span>  
  
 <span data-ttu-id="f0899-104">**头文件：** sqlncli.msi</span><span class="sxs-lookup"><span data-stu-id="f0899-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0899-105">语法</span><span class="sxs-lookup"><span data-stu-id="f0899-105">Syntax</span></span>  
  
```  
HRESULT LocalDBDeleteInstance(  
           PCWSTR pInstanceName,  
           DWORD dwFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0899-106">参数</span><span class="sxs-lookup"><span data-stu-id="f0899-106">Parameters</span></span>  
 <span data-ttu-id="f0899-107">*pInstanceName*</span><span class="sxs-lookup"><span data-stu-id="f0899-107">*pInstanceName*</span></span>  
 <span data-ttu-id="f0899-108">[输入] 要删除的 LocalDB 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="f0899-108">[Input] The name of the LocalDB instance to remove.</span></span>  
  
 <span data-ttu-id="f0899-109">dwFlags\*\*</span><span class="sxs-lookup"><span data-stu-id="f0899-109">*dwFlags*</span></span>  
 <span data-ttu-id="f0899-110">[输入] 保留供将来使用。</span><span class="sxs-lookup"><span data-stu-id="f0899-110">[Input] Reserved for future use.</span></span> <span data-ttu-id="f0899-111">当前应设置为 0。</span><span class="sxs-lookup"><span data-stu-id="f0899-111">Currently should be set to 0.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="f0899-112">返回</span><span class="sxs-lookup"><span data-stu-id="f0899-112">Returns</span></span>  
 <span data-ttu-id="f0899-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="f0899-113">S_OK</span></span>  
 <span data-ttu-id="f0899-114">函数成功。</span><span class="sxs-lookup"><span data-stu-id="f0899-114">The function succeeded.</span></span>  
  
 [<span data-ttu-id="f0899-115">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="f0899-115">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="f0899-116">计算机上没有安装 SQL Server Express LocalDB。</span><span class="sxs-lookup"><span data-stu-id="f0899-116">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="f0899-117">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="f0899-117">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="f0899-118">一个或多个指定的输入参数无效。</span><span class="sxs-lookup"><span data-stu-id="f0899-118">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="f0899-119">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="f0899-119">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="f0899-120">指定的实例名称无效。</span><span class="sxs-lookup"><span data-stu-id="f0899-120">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="f0899-121">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="f0899-121">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="f0899-122">指定的实例不存在。</span><span class="sxs-lookup"><span data-stu-id="f0899-122">The specified instance does not exist.</span></span>  
  
 [<span data-ttu-id="f0899-123">LOCALDB_ERROR_INSTANCE_BUSY</span><span class="sxs-lookup"><span data-stu-id="f0899-123">LOCALDB_ERROR_INSTANCE_BUSY</span></span>](../express-localdb-error-messages/localdb-error-instance-busy.md)  
 <span data-ttu-id="f0899-124">指定的实例正在运行。</span><span class="sxs-lookup"><span data-stu-id="f0899-124">The specified instance is running.</span></span>  
  
 [<span data-ttu-id="f0899-125">LOCALDB_ERROR_WAIT_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f0899-125">LOCALDB_ERROR_WAIT_TIMEOUT</span></span>](../express-localdb-error-messages/localdb-error-wait-timeout.md)  
 <span data-ttu-id="f0899-126">试图获取同步锁定时发生超时。</span><span class="sxs-lookup"><span data-stu-id="f0899-126">A time-out occurred while trying to acquire synchronization locks.</span></span>  
  
 [<span data-ttu-id="f0899-127">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="f0899-127">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="f0899-128">应在其中存储该实例的路径的长度超过 MAX_PATH。</span><span class="sxs-lookup"><span data-stu-id="f0899-128">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="f0899-129">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="f0899-129">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 <span data-ttu-id="f0899-130">无法检索用户配置文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="f0899-130">A user profile folder cannot be retrieved.</span></span>  
  
 [<span data-ttu-id="f0899-131">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="f0899-131">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 <span data-ttu-id="f0899-132">无法访问实例文件夹。</span><span class="sxs-lookup"><span data-stu-id="f0899-132">An instance folder cannot be accessed.</span></span>  
  
 [<span data-ttu-id="f0899-133">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="f0899-133">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="f0899-134">无法访问实例注册表。</span><span class="sxs-lookup"><span data-stu-id="f0899-134">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="f0899-135">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="f0899-135">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-modify-instance-registry.md)  
 <span data-ttu-id="f0899-136">无法修改实例注册表。</span><span class="sxs-lookup"><span data-stu-id="f0899-136">An instance registry cannot be modified.</span></span>  
  
 [<span data-ttu-id="f0899-137">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="f0899-137">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="f0899-138">实例配置已损坏。</span><span class="sxs-lookup"><span data-stu-id="f0899-138">An instance configuration is corrupted.</span></span>  
  
 [<span data-ttu-id="f0899-139">LOCALDB_ERROR_CALLER_IS_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f0899-139">LOCALDB_ERROR_CALLER_IS_NOT_OWNER</span></span>](../express-localdb-error-messages/localdb-error-caller-is-not-owner.md)  
 <span data-ttu-id="f0899-140">API 调用方不是本地数据库实例所有者。</span><span class="sxs-lookup"><span data-stu-id="f0899-140">API caller is not Local Database instance owner.</span></span>  
  
 [<span data-ttu-id="f0899-141">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="f0899-141">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="f0899-142">发生了意外错误。</span><span class="sxs-lookup"><span data-stu-id="f0899-142">An unexpected error occurred.</span></span> <span data-ttu-id="f0899-143">有关详细信息，请参阅事件日志。</span><span class="sxs-lookup"><span data-stu-id="f0899-143">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0899-144">备注</span><span class="sxs-lookup"><span data-stu-id="f0899-144">Remarks</span></span>  
 <span data-ttu-id="f0899-145">有关使用 LocalDB API 的代码示例，请参阅[SQL Server Express LocalDB 引用](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="f0899-145">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0899-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0899-146">See Also</span></span>  
 [<span data-ttu-id="f0899-147">SQL Server Express LocalDB 标头信息和版本信息</span><span class="sxs-lookup"><span data-stu-id="f0899-147">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
