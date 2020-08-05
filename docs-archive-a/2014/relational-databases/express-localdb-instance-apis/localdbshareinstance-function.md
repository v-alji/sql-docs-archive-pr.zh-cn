---
title: LocalDBShareInstance 函数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBShareInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 21eb3b9a-7d32-455b-89bb-f624198cd202
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 238bff0b3512ceb03ead186dc001165274bd4e30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581194"
---
# <a name="localdbshareinstance-function"></a><span data-ttu-id="c20fd-102">LocalDBShareInstance 函数</span><span class="sxs-lookup"><span data-stu-id="c20fd-102">LocalDBShareInstance Function</span></span>
  <span data-ttu-id="c20fd-103">使用指定的共享名称与其他计算机用户共享指定的 SQL Server Express LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="c20fd-103">Shares the specified SQL Server Express LocalDB instance with other users of the computer, using the specified shared name.</span></span>  
  
 <span data-ttu-id="c20fd-104">**头文件：** sqlncli.msi</span><span class="sxs-lookup"><span data-stu-id="c20fd-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c20fd-105">语法</span><span class="sxs-lookup"><span data-stu-id="c20fd-105">Syntax</span></span>  
  
```  
HRESULT LocalDBShareInstance(  
           PSID pOwnerSID,  
           PCWSTR pInstancePrivateName,  
           PCWSTR pInstanceSharedName,   
           DWORD dwFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c20fd-106">参数</span><span class="sxs-lookup"><span data-stu-id="c20fd-106">Parameters</span></span>  
 <span data-ttu-id="c20fd-107">*pOwnerSID*</span><span class="sxs-lookup"><span data-stu-id="c20fd-107">*pOwnerSID*</span></span>  
 <span data-ttu-id="c20fd-108">[输入] 实例所有者的 SID。</span><span class="sxs-lookup"><span data-stu-id="c20fd-108">[Input] The SID of the instance owner.</span></span>  
  
 <span data-ttu-id="c20fd-109">*pInstancePrivateName*</span><span class="sxs-lookup"><span data-stu-id="c20fd-109">*pInstancePrivateName*</span></span>  
 <span data-ttu-id="c20fd-110">[输入] 要共享的 LocalDB 实例的专用名称。</span><span class="sxs-lookup"><span data-stu-id="c20fd-110">[Input] The private name for the LocalDB instance to share.</span></span>  
  
 <span data-ttu-id="c20fd-111">*pInstanceSharedName*</span><span class="sxs-lookup"><span data-stu-id="c20fd-111">*pInstanceSharedName*</span></span>  
 <span data-ttu-id="c20fd-112">[输入] 要共享的 LocalDB 实例的共享名称。</span><span class="sxs-lookup"><span data-stu-id="c20fd-112">[Input] The shared name for the LocalDB instance to share.</span></span>  
  
 <span data-ttu-id="c20fd-113">dwFlags\*\*</span><span class="sxs-lookup"><span data-stu-id="c20fd-113">*dwFlags*</span></span>  
 <span data-ttu-id="c20fd-114">[输入] 保留供将来使用。</span><span class="sxs-lookup"><span data-stu-id="c20fd-114">[Input] Reserved for future use.</span></span> <span data-ttu-id="c20fd-115">当前应设置为 0。</span><span class="sxs-lookup"><span data-stu-id="c20fd-115">Currently should be set to 0.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="c20fd-116">返回</span><span class="sxs-lookup"><span data-stu-id="c20fd-116">Returns</span></span>  
 <span data-ttu-id="c20fd-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="c20fd-117">S_OK</span></span>  
 <span data-ttu-id="c20fd-118">函数成功。</span><span class="sxs-lookup"><span data-stu-id="c20fd-118">The function succeeded.</span></span>  
  
 [<span data-ttu-id="c20fd-119">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="c20fd-119">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="c20fd-120">计算机上没有安装 SQL Server Express LocalDB。</span><span class="sxs-lookup"><span data-stu-id="c20fd-120">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="c20fd-121">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="c20fd-121">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="c20fd-122">一个或多个指定的输入参数无效。</span><span class="sxs-lookup"><span data-stu-id="c20fd-122">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="c20fd-123">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="c20fd-123">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="c20fd-124">指定的实例名称无效。</span><span class="sxs-lookup"><span data-stu-id="c20fd-124">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="c20fd-125">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="c20fd-125">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="c20fd-126">指定的实例不存在。</span><span class="sxs-lookup"><span data-stu-id="c20fd-126">The specified instance does not exist.</span></span>  
  
 [<span data-ttu-id="c20fd-127">LOCALDB_ERROR_ADMIN_RIGHTS_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="c20fd-127">LOCALDB_ERROR_ADMIN_RIGHTS_REQUIRED</span></span>](../express-localdb-error-messages/localdb-error-admin-rights-required.md)  
 <span data-ttu-id="c20fd-128">执行此操作需要管理员权限。</span><span class="sxs-lookup"><span data-stu-id="c20fd-128">Administrator privileges are required in order to execute this operation.</span></span>  
  
 [<span data-ttu-id="c20fd-129">LOCALDB_ERROR_SHARED_NAME_TAKEN</span><span class="sxs-lookup"><span data-stu-id="c20fd-129">LOCALDB_ERROR_SHARED_NAME_TAKEN</span></span>](../express-localdb-error-messages/localdb-error-shared-name-taken.md)  
 <span data-ttu-id="c20fd-130">指定的共享名称名已存在。</span><span class="sxs-lookup"><span data-stu-id="c20fd-130">The specified shared name is already taken.</span></span>  
  
 [<span data-ttu-id="c20fd-131">LOCALDB_ERROR_INSTANCE_ALREADY_SHARED</span><span class="sxs-lookup"><span data-stu-id="c20fd-131">LOCALDB_ERROR_INSTANCE_ALREADY_SHARED</span></span>](../express-localdb-error-messages/localdb-error-instance-already-shared.md)  
 <span data-ttu-id="c20fd-132">指定的实例已经共享。</span><span class="sxs-lookup"><span data-stu-id="c20fd-132">The specified instance is already shared.</span></span>  
  
 [<span data-ttu-id="c20fd-133">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="c20fd-133">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="c20fd-134">发生了意外错误。</span><span class="sxs-lookup"><span data-stu-id="c20fd-134">An unexpected error occurred.</span></span> <span data-ttu-id="c20fd-135">有关详细信息，请参阅事件日志。</span><span class="sxs-lookup"><span data-stu-id="c20fd-135">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c20fd-136">备注</span><span class="sxs-lookup"><span data-stu-id="c20fd-136">Remarks</span></span>  
 <span data-ttu-id="c20fd-137">有关使用 LocalDB API 的代码示例，请参阅[SQL Server Express LocalDB 引用](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="c20fd-137">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c20fd-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c20fd-138">See Also</span></span>  
 [<span data-ttu-id="c20fd-139">SQL Server Express LocalDB 标头信息和版本信息</span><span class="sxs-lookup"><span data-stu-id="c20fd-139">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
