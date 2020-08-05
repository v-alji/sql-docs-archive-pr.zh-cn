---
title: MSSQLSERVER_33085 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33085 (Database Engine error)
ms.assetid: c27b8d1d-668a-4ba8-8b61-25a5ebbc5485
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8d774ab115c2d0ddbbd7b35c7e32db17e39fcb2e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581252"
---
# <a name="mssqlserver_33085"></a><span data-ttu-id="fb4e5-102">MSSQLSERVER_33085</span><span class="sxs-lookup"><span data-stu-id="fb4e5-102">MSSQLSERVER_33085</span></span>
    
## <a name="details"></a><span data-ttu-id="fb4e5-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="fb4e5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fb4e5-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="fb4e5-104">Product Name</span></span>|<span data-ttu-id="fb4e5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="fb4e5-105">SQL Server</span></span>|  
|<span data-ttu-id="fb4e5-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="fb4e5-106">Event ID</span></span>|<span data-ttu-id="fb4e5-107">33085</span><span class="sxs-lookup"><span data-stu-id="fb4e5-107">33085</span></span>|  
|<span data-ttu-id="fb4e5-108">事件源</span><span class="sxs-lookup"><span data-stu-id="fb4e5-108">Event Source</span></span>|<span data-ttu-id="fb4e5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="fb4e5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="fb4e5-110">组件</span><span class="sxs-lookup"><span data-stu-id="fb4e5-110">Component</span></span>|<span data-ttu-id="fb4e5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="fb4e5-111">SQLEngine</span></span>|  
|<span data-ttu-id="fb4e5-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="fb4e5-112">Symbolic Name</span></span>|<span data-ttu-id="fb4e5-113">SEC_CRYPTOPROVE_METHOD_CANNOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="fb4e5-113">SEC_CRYPTOPROVE_METHOD_CANNOT_FOUND</span></span>|  
|<span data-ttu-id="fb4e5-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="fb4e5-114">Message Text</span></span>|<span data-ttu-id="fb4e5-115">无法在加密提供程序库“%.\*ls”中找到一个或多个方法。</span><span class="sxs-lookup"><span data-stu-id="fb4e5-115">One or more methods cannot be found in cryptographic provider library '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fb4e5-116">说明</span><span class="sxs-lookup"><span data-stu-id="fb4e5-116">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fb4e5-117">无法使用错误消息中列出的加密提供程序。</span><span class="sxs-lookup"><span data-stu-id="fb4e5-117">was unable to use the cryptographic provider listed in the error message.</span></span> <span data-ttu-id="fb4e5-118">该加密提供程序不支持所需的方法。</span><span class="sxs-lookup"><span data-stu-id="fb4e5-118">The cryptographic provider did not support a required method.</span></span> <span data-ttu-id="fb4e5-119">错误的状态指示未找到哪个方法。</span><span class="sxs-lookup"><span data-stu-id="fb4e5-119">The state of the error indicates which method was not found.</span></span>  
  
|<span data-ttu-id="fb4e5-120">状态</span><span class="sxs-lookup"><span data-stu-id="fb4e5-120">State</span></span>|<span data-ttu-id="fb4e5-121">说明</span><span class="sxs-lookup"><span data-stu-id="fb4e5-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fb4e5-122">1</span><span class="sxs-lookup"><span data-stu-id="fb4e5-122">1</span></span>|<span data-ttu-id="fb4e5-123">SqlCryptInitializeProvider</span><span class="sxs-lookup"><span data-stu-id="fb4e5-123">SqlCryptInitializeProvider</span></span>|  
|<span data-ttu-id="fb4e5-124">2</span><span class="sxs-lookup"><span data-stu-id="fb4e5-124">2</span></span>|<span data-ttu-id="fb4e5-125">SqlCryptFreeProvider</span><span class="sxs-lookup"><span data-stu-id="fb4e5-125">SqlCryptFreeProvider</span></span>|  
|<span data-ttu-id="fb4e5-126">3</span><span class="sxs-lookup"><span data-stu-id="fb4e5-126">3</span></span>|<span data-ttu-id="fb4e5-127">SqlCryptOpenSession</span><span class="sxs-lookup"><span data-stu-id="fb4e5-127">SqlCryptOpenSession</span></span>|  
|<span data-ttu-id="fb4e5-128">4</span><span class="sxs-lookup"><span data-stu-id="fb4e5-128">4</span></span>|<span data-ttu-id="fb4e5-129">SqlCryptCloseSession</span><span class="sxs-lookup"><span data-stu-id="fb4e5-129">SqlCryptCloseSession</span></span>|  
|<span data-ttu-id="fb4e5-130">5</span><span class="sxs-lookup"><span data-stu-id="fb4e5-130">5</span></span>|<span data-ttu-id="fb4e5-131">SqlCryptGetProviderInfo</span><span class="sxs-lookup"><span data-stu-id="fb4e5-131">SqlCryptGetProviderInfo</span></span>|  
|<span data-ttu-id="fb4e5-132">6</span><span class="sxs-lookup"><span data-stu-id="fb4e5-132">6</span></span>|<span data-ttu-id="fb4e5-133">SqlCryptGetNextAlgorithmId</span><span class="sxs-lookup"><span data-stu-id="fb4e5-133">SqlCryptGetNextAlgorithmId</span></span>|  
|<span data-ttu-id="fb4e5-134">7</span><span class="sxs-lookup"><span data-stu-id="fb4e5-134">7</span></span>|<span data-ttu-id="fb4e5-135">SqlCryptGetAlgorithmInfo</span><span class="sxs-lookup"><span data-stu-id="fb4e5-135">SqlCryptGetAlgorithmInfo</span></span>|  
|<span data-ttu-id="fb4e5-136">8</span><span class="sxs-lookup"><span data-stu-id="fb4e5-136">8</span></span>|<span data-ttu-id="fb4e5-137">SqlCryptCreateKey</span><span class="sxs-lookup"><span data-stu-id="fb4e5-137">SqlCryptCreateKey</span></span>|  
|<span data-ttu-id="fb4e5-138">9</span><span class="sxs-lookup"><span data-stu-id="fb4e5-138">9</span></span>|<span data-ttu-id="fb4e5-139">SqlCryptDropKey</span><span class="sxs-lookup"><span data-stu-id="fb4e5-139">SqlCryptDropKey</span></span>|  
|<span data-ttu-id="fb4e5-140">10</span><span class="sxs-lookup"><span data-stu-id="fb4e5-140">10</span></span>|<span data-ttu-id="fb4e5-141">SqlCryptGetNextKeyId</span><span class="sxs-lookup"><span data-stu-id="fb4e5-141">SqlCryptGetNextKeyId</span></span>|  
|<span data-ttu-id="fb4e5-142">11</span><span class="sxs-lookup"><span data-stu-id="fb4e5-142">11</span></span>|<span data-ttu-id="fb4e5-143">SqlCryptGetKeyInfoByKeyId</span><span class="sxs-lookup"><span data-stu-id="fb4e5-143">SqlCryptGetKeyInfoByKeyId</span></span>|  
|<span data-ttu-id="fb4e5-144">12</span><span class="sxs-lookup"><span data-stu-id="fb4e5-144">12</span></span>|<span data-ttu-id="fb4e5-145">SqlCryptGetKeyInfoByThumb</span><span class="sxs-lookup"><span data-stu-id="fb4e5-145">SqlCryptGetKeyInfoByThumb</span></span>|  
|<span data-ttu-id="fb4e5-146">13</span><span class="sxs-lookup"><span data-stu-id="fb4e5-146">13</span></span>|<span data-ttu-id="fb4e5-147">SqlCryptGetKeyInfoByName</span><span class="sxs-lookup"><span data-stu-id="fb4e5-147">SqlCryptGetKeyInfoByName</span></span>|  
|<span data-ttu-id="fb4e5-148">14</span><span class="sxs-lookup"><span data-stu-id="fb4e5-148">14</span></span>|<span data-ttu-id="fb4e5-149">SqlCryptExportKey</span><span class="sxs-lookup"><span data-stu-id="fb4e5-149">SqlCryptExportKey</span></span>|  
|<span data-ttu-id="fb4e5-150">15</span><span class="sxs-lookup"><span data-stu-id="fb4e5-150">15</span></span>|<span data-ttu-id="fb4e5-151">SqlCryptImportKey</span><span class="sxs-lookup"><span data-stu-id="fb4e5-151">SqlCryptImportKey</span></span>|  
|<span data-ttu-id="fb4e5-152">16</span><span class="sxs-lookup"><span data-stu-id="fb4e5-152">16</span></span>|<span data-ttu-id="fb4e5-153">SqlCryptEncrypt</span><span class="sxs-lookup"><span data-stu-id="fb4e5-153">SqlCryptEncrypt</span></span>|  
|<span data-ttu-id="fb4e5-154">17</span><span class="sxs-lookup"><span data-stu-id="fb4e5-154">17</span></span>|<span data-ttu-id="fb4e5-155">SqlCryptDecrypt</span><span class="sxs-lookup"><span data-stu-id="fb4e5-155">SqlCryptDecrypt</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="fb4e5-156">用户操作</span><span class="sxs-lookup"><span data-stu-id="fb4e5-156">User Action</span></span>  
 <span data-ttu-id="fb4e5-157">请与加密服务供应商联系以获得详细信息。</span><span class="sxs-lookup"><span data-stu-id="fb4e5-157">Contact the cryptographic provider for more information.</span></span>  
  
  
