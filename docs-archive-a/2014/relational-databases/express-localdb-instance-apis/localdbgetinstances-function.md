---
title: LocalDBGetInstances 函数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetInstances
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: f95a9980-8bc0-426c-8aa1-e2660b6784cf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4a6f758bd647fd69a14f72a0651bb3e2e33a7c79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682838"
---
# <a name="localdbgetinstances-function"></a><span data-ttu-id="b38f4-102">LocalDBGetInstances 函数</span><span class="sxs-lookup"><span data-stu-id="b38f4-102">LocalDBGetInstances Function</span></span>
  <span data-ttu-id="b38f4-103">返回具有给定版本的所有 SQL Server Express LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="b38f4-103">Returns all SQL Server Express LocalDB instances with the given version.</span></span>  
  
 <span data-ttu-id="b38f4-104">**头文件：** sqlncli.msi</span><span class="sxs-lookup"><span data-stu-id="b38f4-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b38f4-105">语法</span><span class="sxs-lookup"><span data-stu-id="b38f4-105">Syntax</span></span>  
  
```  
#define MAX_LOCALDB_INSTANCE_NAME_LENGTH 128typedef WCHAR TLocalDBInstanceName[MAX_LOCALDB_INSTANCE_NAME_LENGTH + 1];typedef TLocalDBInstanceName* PTLocalDBInstanceName;  
HRESULT LocalDBGetInstances(  
           PTLocalDBInstanceName pInstanceNames,  
           LPDWORD lpdwNumberOfInstances  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b38f4-106">参数</span><span class="sxs-lookup"><span data-stu-id="b38f4-106">Parameters</span></span>  
 <span data-ttu-id="b38f4-107">*pInstanceNames*</span><span class="sxs-lookup"><span data-stu-id="b38f4-107">*pInstanceNames*</span></span>  
 <span data-ttu-id="b38f4-108">输出此函数返回时，将包含用户工作站上命名的和默认的 LocalDB 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="b38f4-108">[Output] When this function returns, contains the names of both named and default LocalDB instances on the user's workstation.</span></span>  
  
 <span data-ttu-id="b38f4-109">*lpdwNumberOfInstances*</span><span class="sxs-lookup"><span data-stu-id="b38f4-109">*lpdwNumberOfInstances*</span></span>  
 <span data-ttu-id="b38f4-110">[输入/输出]输入时包含*pInstanceNames*缓冲区中实例名称的槽数。</span><span class="sxs-lookup"><span data-stu-id="b38f4-110">[Input/Output] On input, contains the number of slots for instance names in the *pInstanceNames* buffer.</span></span> <span data-ttu-id="b38f4-111">输出时包含在用户工作站上找到的 LocalDB 实例的数目。</span><span class="sxs-lookup"><span data-stu-id="b38f4-111">On output, contains the number of LocalDB instances found on the user's workstation.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="b38f4-112">返回</span><span class="sxs-lookup"><span data-stu-id="b38f4-112">Returns</span></span>  
 <span data-ttu-id="b38f4-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b38f4-113">S_OK</span></span>  
 <span data-ttu-id="b38f4-114">函数成功。</span><span class="sxs-lookup"><span data-stu-id="b38f4-114">The function succeeded.</span></span>  
  
 [<span data-ttu-id="b38f4-115">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="b38f4-115">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="b38f4-116">计算机上没有安装 SQL Server Express LocalDB。</span><span class="sxs-lookup"><span data-stu-id="b38f4-116">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="b38f4-117">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="b38f4-117">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="b38f4-118">一个或多个指定的输入参数无效。</span><span class="sxs-lookup"><span data-stu-id="b38f4-118">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="b38f4-119">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="b38f4-119">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span></span>](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 <span data-ttu-id="b38f4-120">输入的缓冲区太小，并且没有要求截断。</span><span class="sxs-lookup"><span data-stu-id="b38f4-120">The input buffer is too short, and truncation was not requested.</span></span>  
  
 [<span data-ttu-id="b38f4-121">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="b38f4-121">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="b38f4-122">应在其中存储该实例的路径的长度超过 MAX_PATH。</span><span class="sxs-lookup"><span data-stu-id="b38f4-122">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="b38f4-123">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="b38f4-123">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="b38f4-124">无法访问实例注册表。</span><span class="sxs-lookup"><span data-stu-id="b38f4-124">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="b38f4-125">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="b38f4-125">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="b38f4-126">实例配置已损坏。</span><span class="sxs-lookup"><span data-stu-id="b38f4-126">An instance configuration is corrupted.</span></span>  
  
 [<span data-ttu-id="b38f4-127">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="b38f4-127">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="b38f4-128">发生了意外错误。</span><span class="sxs-lookup"><span data-stu-id="b38f4-128">An unexpected error occurred.</span></span> <span data-ttu-id="b38f4-129">有关详细信息，请参阅事件日志。</span><span class="sxs-lookup"><span data-stu-id="b38f4-129">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b38f4-130">备注</span><span class="sxs-lookup"><span data-stu-id="b38f4-130">Remarks</span></span>  
 <span data-ttu-id="b38f4-131">有关使用 LocalDB API 的代码示例，请参阅[SQL Server Express LocalDB 引用](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="b38f4-131">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b38f4-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b38f4-132">See Also</span></span>  
 [<span data-ttu-id="b38f4-133">SQL Server Express LocalDB 标头信息和版本信息</span><span class="sxs-lookup"><span data-stu-id="b38f4-133">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
