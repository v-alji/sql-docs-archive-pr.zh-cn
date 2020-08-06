---
title: LocalDBUnshareInstance 函数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBUnshareInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 54012ccb-eded-43f7-8ea5-da5ce79224c6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 77ebf8cad9d410b047fccede4360ca0041637986
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578220"
---
# <a name="localdbunshareinstance-function"></a><span data-ttu-id="acd20-102">LocalDBUnshareInstance 函数</span><span class="sxs-lookup"><span data-stu-id="acd20-102">LocalDBUnshareInstance Function</span></span>
  <span data-ttu-id="acd20-103">停止共享指定的 SQL Server Express LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="acd20-103">Stops the sharing of the specified SQL Server Express LocalDB instance.</span></span>  
  
 <span data-ttu-id="acd20-104">**头文件：** sqlncli.msi</span><span class="sxs-lookup"><span data-stu-id="acd20-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acd20-105">语法</span><span class="sxs-lookup"><span data-stu-id="acd20-105">Syntax</span></span>  
  
```  
HRESULT LocalDBUnShareInstance(  
           PCWSTR pInstanceSharedName,   
           DWORD dwFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acd20-106">参数</span><span class="sxs-lookup"><span data-stu-id="acd20-106">Parameters</span></span>  
 <span data-ttu-id="acd20-107">*pInstanceSharedName*</span><span class="sxs-lookup"><span data-stu-id="acd20-107">*pInstanceSharedName*</span></span>  
 <span data-ttu-id="acd20-108">[输入] 要取消共享的 LocalDB 实例的共享名称。</span><span class="sxs-lookup"><span data-stu-id="acd20-108">[Input] The shared name for the LocalDB instance to unshare.</span></span>  
  
 <span data-ttu-id="acd20-109">dwFlags\*\*</span><span class="sxs-lookup"><span data-stu-id="acd20-109">*dwFlags*</span></span>  
 <span data-ttu-id="acd20-110">[输入] 保留供将来使用。</span><span class="sxs-lookup"><span data-stu-id="acd20-110">[Input] Reserved for future use.</span></span> <span data-ttu-id="acd20-111">当前应设置为 0。</span><span class="sxs-lookup"><span data-stu-id="acd20-111">Currently should be set to 0.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="acd20-112">返回</span><span class="sxs-lookup"><span data-stu-id="acd20-112">Returns</span></span>  
 <span data-ttu-id="acd20-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="acd20-113">S_OK</span></span>  
 <span data-ttu-id="acd20-114">函数成功。</span><span class="sxs-lookup"><span data-stu-id="acd20-114">The function succeeded.</span></span>  
  
 [<span data-ttu-id="acd20-115">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="acd20-115">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="acd20-116">计算机上没有安装 SQL Server Express LocalDB。</span><span class="sxs-lookup"><span data-stu-id="acd20-116">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="acd20-117">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="acd20-117">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="acd20-118">一个或多个指定的输入参数无效。</span><span class="sxs-lookup"><span data-stu-id="acd20-118">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="acd20-119">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="acd20-119">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="acd20-120">指定的实例名称无效。</span><span class="sxs-lookup"><span data-stu-id="acd20-120">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="acd20-121">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="acd20-121">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="acd20-122">指定的实例不存在。</span><span class="sxs-lookup"><span data-stu-id="acd20-122">The specified instance does not exist.</span></span>  
  
 [<span data-ttu-id="acd20-123">LOCALDB_ERROR_ADMIN_RIGHTS_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="acd20-123">LOCALDB_ERROR_ADMIN_RIGHTS_REQUIRED</span></span>](../express-localdb-error-messages/localdb-error-admin-rights-required.md)  
 <span data-ttu-id="acd20-124">执行此操作需要管理员权限。</span><span class="sxs-lookup"><span data-stu-id="acd20-124">Administrator privileges are required in order to execute this operation.</span></span>  
  
 [<span data-ttu-id="acd20-125">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="acd20-125">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="acd20-126">发生了意外错误。</span><span class="sxs-lookup"><span data-stu-id="acd20-126">An unexpected error occurred.</span></span> <span data-ttu-id="acd20-127">有关详细信息，请参阅事件日志。</span><span class="sxs-lookup"><span data-stu-id="acd20-127">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acd20-128">备注</span><span class="sxs-lookup"><span data-stu-id="acd20-128">Remarks</span></span>  
 <span data-ttu-id="acd20-129">有关使用 LocalDB API 的代码示例，请参阅[SQL Server Express LocalDB 引用](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="acd20-129">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acd20-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="acd20-130">See Also</span></span>  
 [<span data-ttu-id="acd20-131">SQL Server Express LocalDB 标头信息和版本信息</span><span class="sxs-lookup"><span data-stu-id="acd20-131">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
