---
title: MSSQLSERVER_33028 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33028 (Database Engine error)
ms.assetid: c5cec0e4-0bcd-4907-826f-e7d835cfcb37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 555dcf0220793abc0e8af81b3f56867f9960c5f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581254"
---
# <a name="mssqlserver_33028"></a><span data-ttu-id="19add-102">MSSQLSERVER_33028</span><span class="sxs-lookup"><span data-stu-id="19add-102">MSSQLSERVER_33028</span></span>
    
## <a name="details"></a><span data-ttu-id="19add-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="19add-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="19add-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="19add-104">Product Name</span></span>|<span data-ttu-id="19add-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="19add-105">SQL Server</span></span>|  
|<span data-ttu-id="19add-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="19add-106">Event ID</span></span>|<span data-ttu-id="19add-107">33028</span><span class="sxs-lookup"><span data-stu-id="19add-107">33028</span></span>|  
|<span data-ttu-id="19add-108">事件源</span><span class="sxs-lookup"><span data-stu-id="19add-108">Event Source</span></span>|<span data-ttu-id="19add-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="19add-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="19add-110">组件</span><span class="sxs-lookup"><span data-stu-id="19add-110">Component</span></span>|<span data-ttu-id="19add-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="19add-111">SQLEngine</span></span>|  
|<span data-ttu-id="19add-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="19add-112">Symbolic Name</span></span>|<span data-ttu-id="19add-113">SEC_CRYPTOPROV_CANTOPENSESSION</span><span class="sxs-lookup"><span data-stu-id="19add-113">SEC_CRYPTOPROV_CANTOPENSESSION</span></span>|  
|<span data-ttu-id="19add-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="19add-114">Message Text</span></span>|<span data-ttu-id="19add-115">无法为 %S_MSG '%.\*ls' 打开会话。</span><span class="sxs-lookup"><span data-stu-id="19add-115">Cannot open session for %S_MSG '%.\*ls'.</span></span> <span data-ttu-id="19add-116">提供程序错误代码: %d。</span><span class="sxs-lookup"><span data-stu-id="19add-116">Provider error code: %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="19add-117">说明</span><span class="sxs-lookup"><span data-stu-id="19add-117">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="19add-118">无法打开错误消息中列出的加密提供程序。</span><span class="sxs-lookup"><span data-stu-id="19add-118">was unable to open the cryptographic provider listed in the error message.</span></span> <span data-ttu-id="19add-119">加密提供程序提供的错误代码如下所示。</span><span class="sxs-lookup"><span data-stu-id="19add-119">The cryptographic provider supplied the error code listed.</span></span> <span data-ttu-id="19add-120">您可能需要联系您的加密服务供应商以获得有关错误的详细信息。</span><span class="sxs-lookup"><span data-stu-id="19add-120">You may need to contact your cryptographic provider for more information about the error.</span></span>  
  
|<span data-ttu-id="19add-121">错误代码</span><span class="sxs-lookup"><span data-stu-id="19add-121">Error code</span></span>|<span data-ttu-id="19add-122">说明</span><span class="sxs-lookup"><span data-stu-id="19add-122">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="19add-123">0</span><span class="sxs-lookup"><span data-stu-id="19add-123">0</span></span>|<span data-ttu-id="19add-124">成功。</span><span class="sxs-lookup"><span data-stu-id="19add-124">Success.</span></span> <span data-ttu-id="19add-125">没有错误。</span><span class="sxs-lookup"><span data-stu-id="19add-125">No error.</span></span>|  
|<span data-ttu-id="19add-126">1</span><span class="sxs-lookup"><span data-stu-id="19add-126">1</span></span>|<span data-ttu-id="19add-127">失败。</span><span class="sxs-lookup"><span data-stu-id="19add-127">Failure.</span></span> <span data-ttu-id="19add-128">出现了未指定的错误或意外错误。</span><span class="sxs-lookup"><span data-stu-id="19add-128">An unspecified or unexpected error occurred.</span></span> <span data-ttu-id="19add-129">无法获得其他信息。</span><span class="sxs-lookup"><span data-stu-id="19add-129">Additional information is not available.</span></span>|  
|<span data-ttu-id="19add-130">2</span><span class="sxs-lookup"><span data-stu-id="19add-130">2</span></span>|<span data-ttu-id="19add-131">缓冲区不足。</span><span class="sxs-lookup"><span data-stu-id="19add-131">Insufficient Buffer.</span></span> <span data-ttu-id="19add-132">无法为加密提供程序分配空间。</span><span class="sxs-lookup"><span data-stu-id="19add-132">Space could not be allocated for the cryptographic provider.</span></span>|  
|<span data-ttu-id="19add-133">3</span><span class="sxs-lookup"><span data-stu-id="19add-133">3</span></span>|<span data-ttu-id="19add-134">不提供支持。</span><span class="sxs-lookup"><span data-stu-id="19add-134">Not Supported.</span></span> <span data-ttu-id="19add-135">此版本不支持该加密提供程序。</span><span class="sxs-lookup"><span data-stu-id="19add-135">The cryptographic provider is not supported by this release.</span></span> <span data-ttu-id="19add-136">请选择其他加密提供程序。</span><span class="sxs-lookup"><span data-stu-id="19add-136">Select another cryptographic provider.</span></span>|  
|<span data-ttu-id="19add-137">4</span><span class="sxs-lookup"><span data-stu-id="19add-137">4</span></span>|<span data-ttu-id="19add-138">找不到该加密提供程序。</span><span class="sxs-lookup"><span data-stu-id="19add-138">Not Found.</span></span> <span data-ttu-id="19add-139">指定的加密提供程序不存在或您无权访问这些文件。</span><span class="sxs-lookup"><span data-stu-id="19add-139">The specified cryptographic provider is not present or you do not have authorization to access the files.</span></span>|  
|<span data-ttu-id="19add-140">5</span><span class="sxs-lookup"><span data-stu-id="19add-140">5</span></span>|<span data-ttu-id="19add-141">授权失败。</span><span class="sxs-lookup"><span data-stu-id="19add-141">Authorization Failure.</span></span> <span data-ttu-id="19add-142">可能是创建凭据时提供了不正确的密码或用户名所致。</span><span class="sxs-lookup"><span data-stu-id="19add-142">Can result from providing an incorrect password or username when creating the credential.</span></span> <span data-ttu-id="19add-143">也可能是凭据不存在所致。</span><span class="sxs-lookup"><span data-stu-id="19add-143">Can result if the credential does not exist.</span></span>|  
|<span data-ttu-id="19add-144">6</span><span class="sxs-lookup"><span data-stu-id="19add-144">6</span></span>|<span data-ttu-id="19add-145">参数无效。</span><span class="sxs-lookup"><span data-stu-id="19add-145">Invalid Argument.</span></span> <span data-ttu-id="19add-146">传递到加密提供程序的参数无效。</span><span class="sxs-lookup"><span data-stu-id="19add-146">An invalid argument was passed to the cryptographic provider.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="19add-147">用户操作</span><span class="sxs-lookup"><span data-stu-id="19add-147">User Action</span></span>  
 <span data-ttu-id="19add-148">解决该错误，或联系加密服务提供商以获得详细信息。</span><span class="sxs-lookup"><span data-stu-id="19add-148">Resolve the error, or contact the cryptographic provider for more information.</span></span>  
  
  
