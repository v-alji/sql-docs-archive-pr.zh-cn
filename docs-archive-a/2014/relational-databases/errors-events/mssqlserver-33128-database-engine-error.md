---
title: MSSQLSERVER_33128 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33128 (Database Engine error)
ms.assetid: 12c1096f-d120-439b-85f3-f794859503c9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 158cc609a18cf3fe7b76708e351b78263cd80a9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581251"
---
# <a name="mssqlserver_33128"></a><span data-ttu-id="cc19a-102">MSSQLSERVER_33128</span><span class="sxs-lookup"><span data-stu-id="cc19a-102">MSSQLSERVER_33128</span></span>
    
## <a name="details"></a><span data-ttu-id="cc19a-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="cc19a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cc19a-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="cc19a-104">Product Name</span></span>|<span data-ttu-id="cc19a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cc19a-105">SQL Server</span></span>|  
|<span data-ttu-id="cc19a-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="cc19a-106">Event ID</span></span>|<span data-ttu-id="cc19a-107">33128</span><span class="sxs-lookup"><span data-stu-id="cc19a-107">33128</span></span>|  
|<span data-ttu-id="cc19a-108">事件源</span><span class="sxs-lookup"><span data-stu-id="cc19a-108">Event Source</span></span>|<span data-ttu-id="cc19a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cc19a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cc19a-110">组件</span><span class="sxs-lookup"><span data-stu-id="cc19a-110">Component</span></span>|<span data-ttu-id="cc19a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="cc19a-111">SQLEngine</span></span>|  
|<span data-ttu-id="cc19a-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="cc19a-112">Symbolic Name</span></span>|<span data-ttu-id="cc19a-113">SEC_DEPRECATED_ALGO</span><span class="sxs-lookup"><span data-stu-id="cc19a-113">SEC_DEPRECATED_ALGO</span></span>|  
|<span data-ttu-id="cc19a-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="cc19a-114">Message Text</span></span>|<span data-ttu-id="cc19a-115">加密失败。</span><span class="sxs-lookup"><span data-stu-id="cc19a-115">Encryption failed.</span></span> <span data-ttu-id="cc19a-116">密钥使用了不推荐使用的算法“%.\*ls”，这不再受支持。</span><span class="sxs-lookup"><span data-stu-id="cc19a-116">Key uses deprecated algorithm '%.\*ls' which is no longer supported.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cc19a-117">说明</span><span class="sxs-lookup"><span data-stu-id="cc19a-117">Explanation</span></span>  
 <span data-ttu-id="cc19a-118">引用 RC4（或 RC4_128）加密算法时，就会出现此消息。</span><span class="sxs-lookup"><span data-stu-id="cc19a-118">This message occurs when referencing the RC4 (or RC4_128) encryption algorithm.</span></span> <span data-ttu-id="cc19a-119">RC4 和 RC4_128 是弱算法，不推荐使用它们。</span><span class="sxs-lookup"><span data-stu-id="cc19a-119">RC4 and RC4_128 are weak algorithms and are deprecated.</span></span> <span data-ttu-id="cc19a-120">请改用一种较强的算法，如某个 AES 算法。</span><span class="sxs-lookup"><span data-stu-id="cc19a-120">Use a stronger algorithm such as one of the AES algorithms instead.</span></span>  
  
 <span data-ttu-id="cc19a-121">数据库兼容级别为 90 或 100 时，该操作成功，引发不推荐使用事件，该消息仅在环形缓冲区中显示。</span><span class="sxs-lookup"><span data-stu-id="cc19a-121">When the database compatibility level is 90 or 100, the operation succeeds, the deprecation event is raised, and the message appears only in the ring buffer.</span></span>  
  
 <span data-ttu-id="cc19a-122">数据库兼容级别为 110 或更高时，解密操作成功，引发不推荐使用事件，该消息仅在环形缓冲区中显示。</span><span class="sxs-lookup"><span data-stu-id="cc19a-122">When the database compatibility level is 110 or higher, decryption operations succeed, the deprecation event is raised, and the message appears only in the ring buffer.</span></span> <span data-ttu-id="cc19a-123">加密操作将失败，引发不推荐使用事件，对用户显示该消息并在环形缓冲区中显示它。</span><span class="sxs-lookup"><span data-stu-id="cc19a-123">Encryption operations will fail, the deprecation event is raised, and the message is displayed for the user, and the message appears in the ring buffer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cc19a-124">环形缓冲区是未完全介绍的内部组件，不计划提供给客户使用。</span><span class="sxs-lookup"><span data-stu-id="cc19a-124">The ring buffer is an internal component which is not fully documented and is not intended to be used by customers.</span></span> <span data-ttu-id="cc19a-125">与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客户支持联系时，来自环形缓冲区的消息很有用。</span><span class="sxs-lookup"><span data-stu-id="cc19a-125">Messages from the ring buffer are useful when contacting [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Support.</span></span> <span data-ttu-id="cc19a-126">若要查看环形缓冲区，请查询 sys.dm_os_ring_buffers 动态管理视图。</span><span class="sxs-lookup"><span data-stu-id="cc19a-126">To view the ring buffer, query the sys.dm_os_ring_buffers dynamic management view.</span></span>  
  
|<span data-ttu-id="cc19a-127">状态</span><span class="sxs-lookup"><span data-stu-id="cc19a-127">State</span></span>|<span data-ttu-id="cc19a-128">说明</span><span class="sxs-lookup"><span data-stu-id="cc19a-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cc19a-129">1</span><span class="sxs-lookup"><span data-stu-id="cc19a-129">1</span></span>|<span data-ttu-id="cc19a-130">RC4 密钥在内置的 encryptbykey() 函数使用。</span><span class="sxs-lookup"><span data-stu-id="cc19a-130">A RC4 key is used in the built-in encryptbykey() function.</span></span> <span data-ttu-id="cc19a-131">内置函数返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="cc19a-131">Built-in function returns NULL.</span></span> <span data-ttu-id="cc19a-132">此消息仅显示在环形缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="cc19a-132">This message only appears in the ring buffer.</span></span>|  
|<span data-ttu-id="cc19a-133">2</span><span class="sxs-lookup"><span data-stu-id="cc19a-133">2</span></span>|<span data-ttu-id="cc19a-134">RC4 密钥在内置的 decryptbykey() 函数中使用。</span><span class="sxs-lookup"><span data-stu-id="cc19a-134">A RC4 key is used in by the built-in decryptbykey() function.</span></span> <span data-ttu-id="cc19a-135">此消息仅显示在环形缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="cc19a-135">This message only appears in the ring buffer.</span></span>|  
|<span data-ttu-id="cc19a-136">3</span><span class="sxs-lookup"><span data-stu-id="cc19a-136">3</span></span>|<span data-ttu-id="cc19a-137">对称密钥正在对不推荐使用的 RC4 密钥加密。</span><span class="sxs-lookup"><span data-stu-id="cc19a-137">A deprecated RC4 key is being encrypted by a symmetric key.</span></span> <span data-ttu-id="cc19a-138">显示给用户和在环形缓冲区中显示。</span><span class="sxs-lookup"><span data-stu-id="cc19a-138">Seen by users and in the ring buffer.</span></span> <span data-ttu-id="cc19a-139">不能在兼容级别 110 中更改不推荐使用的 RC4 对称密钥。</span><span class="sxs-lookup"><span data-stu-id="cc19a-139">Deprecated RC4 symmetric keys cannot be altered in compatibility level 110.</span></span> <span data-ttu-id="cc19a-140">尝试使用非 RC4 密钥进行加密操作。</span><span class="sxs-lookup"><span data-stu-id="cc19a-140">Try to use non-RC4 keys for crypto operations.</span></span> <span data-ttu-id="cc19a-141">如果需要，将向后兼容级别设置为 90 或 100。</span><span class="sxs-lookup"><span data-stu-id="cc19a-141">If necessary, set backward compatibility level to a 90 or 100.</span></span>|  
|<span data-ttu-id="cc19a-142">4</span><span class="sxs-lookup"><span data-stu-id="cc19a-142">4</span></span>|<span data-ttu-id="cc19a-143">不推荐使用的 RC4 对称密钥正在对非 RC4 密钥加密。</span><span class="sxs-lookup"><span data-stu-id="cc19a-143">A non-RC4 key is being encrypted by a deprecated RC4 symmetric key.</span></span> <span data-ttu-id="cc19a-144">显示给用户和在环形缓冲区中显示。</span><span class="sxs-lookup"><span data-stu-id="cc19a-144">Seen by users and in the ring buffer.</span></span> <span data-ttu-id="cc19a-145">修改应用程序以使用非 RC4 对称密钥或将向后兼容级别设置为 90 或 100。</span><span class="sxs-lookup"><span data-stu-id="cc19a-145">Modify the application to use non-RC4 symmetric keys or set backward compatibility level to 90 or 100.</span></span>|  
|<span data-ttu-id="cc19a-146">5</span><span class="sxs-lookup"><span data-stu-id="cc19a-146">5</span></span>|<span data-ttu-id="cc19a-147">对称密钥正在对不推荐使用的 RC4 密钥解密。</span><span class="sxs-lookup"><span data-stu-id="cc19a-147">A deprecated RC4 key is being decrypted by a symmetric key.</span></span> <span data-ttu-id="cc19a-148">此消息仅显示在环形缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="cc19a-148">This message only appears in the ring buffer.</span></span>|  
|<span data-ttu-id="cc19a-149">6</span><span class="sxs-lookup"><span data-stu-id="cc19a-149">6</span></span>|<span data-ttu-id="cc19a-150">RC4 对称密钥正在对非 RC4 密钥解密。</span><span class="sxs-lookup"><span data-stu-id="cc19a-150">A non-RC4 key is being decrypted by an RC4 symmetric key.</span></span> <span data-ttu-id="cc19a-151">此消息仅显示在环形缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="cc19a-151">This message only appears in the ring buffer.</span></span>|  
|<span data-ttu-id="cc19a-152">7</span><span class="sxs-lookup"><span data-stu-id="cc19a-152">7</span></span>|<span data-ttu-id="cc19a-153">证书正在对 RC4 对称密钥加密。</span><span class="sxs-lookup"><span data-stu-id="cc19a-153">A RC4 symmetric key is being encrypted by the certificate.</span></span> <span data-ttu-id="cc19a-154">显示给用户和在环形缓冲区中显示。</span><span class="sxs-lookup"><span data-stu-id="cc19a-154">Seen by users and in the ring buffer.</span></span>|  
|<span data-ttu-id="cc19a-155">8</span><span class="sxs-lookup"><span data-stu-id="cc19a-155">8</span></span>|<span data-ttu-id="cc19a-156">证书正在对 RC4 对称密钥解密。</span><span class="sxs-lookup"><span data-stu-id="cc19a-156">A RC4 symmetric key is being decrypted by the certificate.</span></span> <span data-ttu-id="cc19a-157">此消息仅显示在环形缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="cc19a-157">This message only appears in the ring buffer.</span></span>|  
|<span data-ttu-id="cc19a-158">9</span><span class="sxs-lookup"><span data-stu-id="cc19a-158">9</span></span>|<span data-ttu-id="cc19a-159">EKM 密钥正在对 RC4 对称密钥加密。</span><span class="sxs-lookup"><span data-stu-id="cc19a-159">A RC4 symmetric key is being encrypted by the EKM key.</span></span>|  
|<span data-ttu-id="cc19a-160">10</span><span class="sxs-lookup"><span data-stu-id="cc19a-160">10</span></span>|<span data-ttu-id="cc19a-161">EKM 密钥正在对 RC4 对称密钥解密。</span><span class="sxs-lookup"><span data-stu-id="cc19a-161">A RC4 symmetric key is being decrypted by the EKM key.</span></span> <span data-ttu-id="cc19a-162">此消息仅显示在环形缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="cc19a-162">This message only appears in the ring buffer.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="cc19a-163">用户操作</span><span class="sxs-lookup"><span data-stu-id="cc19a-163">User Action</span></span>  
 <span data-ttu-id="cc19a-164">请改用一种较强的算法，如某个 AES 算法。</span><span class="sxs-lookup"><span data-stu-id="cc19a-164">Use a stronger algorithm such as one of the AES algorithms instead.</span></span> <span data-ttu-id="cc19a-165">（建议）</span><span class="sxs-lookup"><span data-stu-id="cc19a-165">(Recommended)</span></span>  
  
 <span data-ttu-id="cc19a-166">使用 ALTER DATABASE SET COMPATIBILITY_LEVEL 将数据库兼容级别设置为 100。</span><span class="sxs-lookup"><span data-stu-id="cc19a-166">Use ALTER DATABASE SET COMPATIBILITY_LEVEL to set the database to compatibility level 100.</span></span> <span data-ttu-id="cc19a-167">（建议不要使用。）</span><span class="sxs-lookup"><span data-stu-id="cc19a-167">(Not recommended.)</span></span>  
  
  
