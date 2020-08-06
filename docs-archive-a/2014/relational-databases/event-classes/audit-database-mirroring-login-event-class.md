---
title: Audit Database Mirroring Login 事件类 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event notifications [SQL Server], database mirroring
- Audit Database Mirroring Login event class
- database mirroring [SQL Server], event notifications
ms.assetid: d0bd436d-aade-4208-a7e5-75cf3b5d0ce9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7c7f36929d8e4d5d16b5cb8467d2f8e950a0c396
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689901"
---
# <a name="audit-database-mirroring-login-event-class"></a><span data-ttu-id="572f2-102">Audit Database Mirroring Login 事件类</span><span class="sxs-lookup"><span data-stu-id="572f2-102">Audit Database Mirroring Login Event Class</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="572f2-103">将创建一个 **Audit Database Mirroring Login** 事件来报告与数据库镜像传输安全性相关的审核消息。</span><span class="sxs-lookup"><span data-stu-id="572f2-103">creates an **Audit Database Mirroring Login** event to report audit messages related to database mirroring transport security.</span></span>  
  
## <a name="audit-database-mirroring-login-event-class-data-columns"></a><span data-ttu-id="572f2-104">Audit Database Mirroring Login 事件类的数据列</span><span class="sxs-lookup"><span data-stu-id="572f2-104">Audit Database Mirroring Login Event Class Data Columns</span></span>  
  
|<span data-ttu-id="572f2-105">数据列</span><span class="sxs-lookup"><span data-stu-id="572f2-105">Data column</span></span>|<span data-ttu-id="572f2-106">类型</span><span class="sxs-lookup"><span data-stu-id="572f2-106">Type</span></span>|<span data-ttu-id="572f2-107">说明</span><span class="sxs-lookup"><span data-stu-id="572f2-107">Description</span></span>|<span data-ttu-id="572f2-108">列号</span><span class="sxs-lookup"><span data-stu-id="572f2-108">Column number</span></span>|<span data-ttu-id="572f2-109">可筛选</span><span class="sxs-lookup"><span data-stu-id="572f2-109">Filterable</span></span>|  
|-----------------|----------|-----------------|-------------------|----------------|  
|<span data-ttu-id="572f2-110">ApplicationName </span><span class="sxs-lookup"><span data-stu-id="572f2-110">**ApplicationName**</span></span>|<span data-ttu-id="572f2-111">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="572f2-111">**nvarchar**</span></span>|<span data-ttu-id="572f2-112">在此事件类中未使用。</span><span class="sxs-lookup"><span data-stu-id="572f2-112">Unused in this event class.</span></span>|<span data-ttu-id="572f2-113">10</span><span class="sxs-lookup"><span data-stu-id="572f2-113">10</span></span>|<span data-ttu-id="572f2-114">是</span><span class="sxs-lookup"><span data-stu-id="572f2-114">Yes</span></span>|  
|<span data-ttu-id="572f2-115">**ClientProcessID**</span><span class="sxs-lookup"><span data-stu-id="572f2-115">**ClientProcessID**</span></span>|<span data-ttu-id="572f2-116">**int**</span><span class="sxs-lookup"><span data-stu-id="572f2-116">**int**</span></span>|<span data-ttu-id="572f2-117">在此事件类中未使用。</span><span class="sxs-lookup"><span data-stu-id="572f2-117">Unused in this event class.</span></span>|<span data-ttu-id="572f2-118">9</span><span class="sxs-lookup"><span data-stu-id="572f2-118">9</span></span>|<span data-ttu-id="572f2-119">是</span><span class="sxs-lookup"><span data-stu-id="572f2-119">Yes</span></span>|  
|<span data-ttu-id="572f2-120">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="572f2-120">**DatabaseID**</span></span>|<span data-ttu-id="572f2-121">**int**</span><span class="sxs-lookup"><span data-stu-id="572f2-121">**int**</span></span>|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="572f2-122">数据列而且服务器可用，则 **ServerName** 将显示数据库名。</span><span class="sxs-lookup"><span data-stu-id="572f2-122">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="572f2-123">可使用 DB_ID 函数来确定数据库的值。</span><span class="sxs-lookup"><span data-stu-id="572f2-123">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="572f2-124">3</span><span class="sxs-lookup"><span data-stu-id="572f2-124">3</span></span>|<span data-ttu-id="572f2-125">是</span><span class="sxs-lookup"><span data-stu-id="572f2-125">Yes</span></span>|  
|<span data-ttu-id="572f2-126">**EventClass**</span><span class="sxs-lookup"><span data-stu-id="572f2-126">**EventClass**</span></span>|<span data-ttu-id="572f2-127">**int**</span><span class="sxs-lookup"><span data-stu-id="572f2-127">**int**</span></span>|<span data-ttu-id="572f2-128">捕获的事件类的类型。</span><span class="sxs-lookup"><span data-stu-id="572f2-128">The type of event class captured.</span></span> <span data-ttu-id="572f2-129">对 **Audit Database Mirroring Login** 来说始终是 **154**。</span><span class="sxs-lookup"><span data-stu-id="572f2-129">Always **154** for **Audit Database Mirroring Login**.</span></span>|<span data-ttu-id="572f2-130">27</span><span class="sxs-lookup"><span data-stu-id="572f2-130">27</span></span>|<span data-ttu-id="572f2-131">否</span><span class="sxs-lookup"><span data-stu-id="572f2-131">No</span></span>|  
|<span data-ttu-id="572f2-132">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="572f2-132">**EventSequence**</span></span>|<span data-ttu-id="572f2-133">**int**</span><span class="sxs-lookup"><span data-stu-id="572f2-133">**int**</span></span>|<span data-ttu-id="572f2-134">此事件的序列号。</span><span class="sxs-lookup"><span data-stu-id="572f2-134">Sequence number for this event.</span></span>|<span data-ttu-id="572f2-135">51</span><span class="sxs-lookup"><span data-stu-id="572f2-135">51</span></span>|<span data-ttu-id="572f2-136">否</span><span class="sxs-lookup"><span data-stu-id="572f2-136">No</span></span>|  
|<span data-ttu-id="572f2-137">**EventSubClass**</span><span class="sxs-lookup"><span data-stu-id="572f2-137">**EventSubClass**</span></span>|<span data-ttu-id="572f2-138">**int**</span><span class="sxs-lookup"><span data-stu-id="572f2-138">**int**</span></span>|<span data-ttu-id="572f2-139">事件子类的类型，提供有关每个事件类的进一步信息。</span><span class="sxs-lookup"><span data-stu-id="572f2-139">The type of event subclass, providing further information about each event class.</span></span> <span data-ttu-id="572f2-140">下表列出了此事件的事件子类值。</span><span class="sxs-lookup"><span data-stu-id="572f2-140">The table below lists the event subclass values for this event.</span></span>|<span data-ttu-id="572f2-141">21</span><span class="sxs-lookup"><span data-stu-id="572f2-141">21</span></span>|<span data-ttu-id="572f2-142">是</span><span class="sxs-lookup"><span data-stu-id="572f2-142">Yes</span></span>|  
|<span data-ttu-id="572f2-143">**FileName**</span><span class="sxs-lookup"><span data-stu-id="572f2-143">**FileName**</span></span>|<span data-ttu-id="572f2-144">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="572f2-144">**nvarchar**</span></span>|<span data-ttu-id="572f2-145">在远程数据库镜像端点上配置支持的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="572f2-145">Supported authentication method configured on the remote database mirroring endpoint.</span></span> <span data-ttu-id="572f2-146">如果有多种可用方法，则接受（目标）端点将确定先试用哪种方法。</span><span class="sxs-lookup"><span data-stu-id="572f2-146">When more than one method is available, the accepting (target) endpoint determines which method is tried first.</span></span> <span data-ttu-id="572f2-147">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="572f2-147">Possible values are:</span></span><br /><br /> <span data-ttu-id="572f2-148">**无**。</span><span class="sxs-lookup"><span data-stu-id="572f2-148">**None**.</span></span> <span data-ttu-id="572f2-149">未配置任何身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="572f2-149">No authentication method is configured.</span></span><br /><br /> <span data-ttu-id="572f2-150">**NTLM**。</span><span class="sxs-lookup"><span data-stu-id="572f2-150">**NTLM**.</span></span> <span data-ttu-id="572f2-151">要求使用 NTLM 身份验证。</span><span class="sxs-lookup"><span data-stu-id="572f2-151">Requires NTLM authentication.</span></span><br /><br /> <span data-ttu-id="572f2-152">**KERBEROS**。</span><span class="sxs-lookup"><span data-stu-id="572f2-152">**KERBEROS**.</span></span> <span data-ttu-id="572f2-153">要求使用 Kerberos 身份验证。</span><span class="sxs-lookup"><span data-stu-id="572f2-153">Requires Kerberos authentication.</span></span><br /><br /> <span data-ttu-id="572f2-154">**NEGOTIATE**。</span><span class="sxs-lookup"><span data-stu-id="572f2-154">**NEGOTIATE**.</span></span> <span data-ttu-id="572f2-155">由 Windows 协商身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="572f2-155">Windows negotiates the authentication method.</span></span><br /><br /> <span data-ttu-id="572f2-156">**CERTIFICATE**。</span><span class="sxs-lookup"><span data-stu-id="572f2-156">**CERTIFICATE**.</span></span> <span data-ttu-id="572f2-157">要求使用为端点配置的证书，该证书存储在 **master** 数据库中。</span><span class="sxs-lookup"><span data-stu-id="572f2-157">Requires the certificate configured for the endpoint, which is stored in the **master** database.</span></span><br /><br /> <span data-ttu-id="572f2-158">**NTLM、CERTIFICATE**。</span><span class="sxs-lookup"><span data-stu-id="572f2-158">**NTLM, CERTIFICATE**.</span></span> <span data-ttu-id="572f2-159">使用 NTLM 或端点证书进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="572f2-159">Accepts NTLM or the endpoint certificate for authentication.</span></span><br /><br /> <span data-ttu-id="572f2-160">**KERBEROS、CERTIFICATE**。</span><span class="sxs-lookup"><span data-stu-id="572f2-160">**KERBEROS, CERTIFICATE**.</span></span> <span data-ttu-id="572f2-161">使用 Kerberos 或端点证书进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="572f2-161">Accepts Kerberos or the endpoint certificate for authentication.</span></span><br /><br /> <span data-ttu-id="572f2-162">**NEGOTIATE、CERTIFICATE**。</span><span class="sxs-lookup"><span data-stu-id="572f2-162">**NEGOTIATE, CERTIFICATE**.</span></span> <span data-ttu-id="572f2-163">由 Windows 协商身份验证方法，或者使用端点证书进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="572f2-163">Windows negotiates the authentication method, or an endpoint certificate can be used for authentication.</span></span><br /><br /> <span data-ttu-id="572f2-164">**CERTIFICATE、NTLM**。</span><span class="sxs-lookup"><span data-stu-id="572f2-164">**CERTIFICATE, NTLM**.</span></span> <span data-ttu-id="572f2-165">使用端点证书或 NTLM 进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="572f2-165">Accepts an endpoint certificate or NTLM for authentication.</span></span><br /><br /> <span data-ttu-id="572f2-166">**CERTIFICATE、KERBEROS**。</span><span class="sxs-lookup"><span data-stu-id="572f2-166">**CERTIFICATE, KERBEROS**.</span></span> <span data-ttu-id="572f2-167">使用端点证书或 Kerberos 进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="572f2-167">Accepts an endpoint certificate or Kerberos for authentication.</span></span><br /><br /> <span data-ttu-id="572f2-168">**CERTIFICATE、NEGOTIATE**。</span><span class="sxs-lookup"><span data-stu-id="572f2-168">**CERTIFICATE, NEGOTIATE**.</span></span> <span data-ttu-id="572f2-169">使用端点证书进行身份验证，或由 Windows 协商身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="572f2-169">Accepts an endpoint certificate for authentication or Windows negotiates the authentication method.</span></span>|<span data-ttu-id="572f2-170">36</span><span class="sxs-lookup"><span data-stu-id="572f2-170">36</span></span>|<span data-ttu-id="572f2-171">否</span><span class="sxs-lookup"><span data-stu-id="572f2-171">No</span></span>|  
|<span data-ttu-id="572f2-172">**HostName**</span><span class="sxs-lookup"><span data-stu-id="572f2-172">**HostName**</span></span>|<span data-ttu-id="572f2-173">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="572f2-173">**nvarchar**</span></span>|<span data-ttu-id="572f2-174">在此事件类中未使用。</span><span class="sxs-lookup"><span data-stu-id="572f2-174">Unused in this event class.</span></span>|<span data-ttu-id="572f2-175">8</span><span class="sxs-lookup"><span data-stu-id="572f2-175">8</span></span>|<span data-ttu-id="572f2-176">是</span><span class="sxs-lookup"><span data-stu-id="572f2-176">Yes</span></span>|  
|<span data-ttu-id="572f2-177">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="572f2-177">**IsSystem**</span></span>|<span data-ttu-id="572f2-178">**int**</span><span class="sxs-lookup"><span data-stu-id="572f2-178">**int**</span></span>|<span data-ttu-id="572f2-179">指示事件是发生在系统进程中还是发生在用户进程中。</span><span class="sxs-lookup"><span data-stu-id="572f2-179">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="572f2-180">1 = 系统，0 = 用户。</span><span class="sxs-lookup"><span data-stu-id="572f2-180">1 = system, 0 = user.</span></span>|<span data-ttu-id="572f2-181">60</span><span class="sxs-lookup"><span data-stu-id="572f2-181">60</span></span>|<span data-ttu-id="572f2-182">否</span><span class="sxs-lookup"><span data-stu-id="572f2-182">No</span></span>|  
|<span data-ttu-id="572f2-183">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="572f2-183">**LoginSid**</span></span>|<span data-ttu-id="572f2-184">**图像**</span><span class="sxs-lookup"><span data-stu-id="572f2-184">**image**</span></span>|<span data-ttu-id="572f2-185">已登录用户的安全标识号 (SID)。</span><span class="sxs-lookup"><span data-stu-id="572f2-185">The security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="572f2-186">服务器中的每个登录名都具有唯一的 SID。</span><span class="sxs-lookup"><span data-stu-id="572f2-186">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="572f2-187">41</span><span class="sxs-lookup"><span data-stu-id="572f2-187">41</span></span>|<span data-ttu-id="572f2-188">是</span><span class="sxs-lookup"><span data-stu-id="572f2-188">Yes</span></span>|  
|<span data-ttu-id="572f2-189">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="572f2-189">**NTDomainName**</span></span>|<span data-ttu-id="572f2-190">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="572f2-190">**nvarchar**</span></span>|<span data-ttu-id="572f2-191">用户所属的 Windows 域。</span><span class="sxs-lookup"><span data-stu-id="572f2-191">The Windows domain to which the user belongs.</span></span>|<span data-ttu-id="572f2-192">7</span><span class="sxs-lookup"><span data-stu-id="572f2-192">7</span></span>|<span data-ttu-id="572f2-193">是</span><span class="sxs-lookup"><span data-stu-id="572f2-193">Yes</span></span>|  
|<span data-ttu-id="572f2-194">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="572f2-194">**NTUserName**</span></span>|<span data-ttu-id="572f2-195">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="572f2-195">**nvarchar**</span></span>|<span data-ttu-id="572f2-196">拥有生成此事件的连接的用户的名称。</span><span class="sxs-lookup"><span data-stu-id="572f2-196">The name of the user that owns the connection that generated this event.</span></span>|<span data-ttu-id="572f2-197">6</span><span class="sxs-lookup"><span data-stu-id="572f2-197">6</span></span>|<span data-ttu-id="572f2-198">是</span><span class="sxs-lookup"><span data-stu-id="572f2-198">Yes</span></span>|  
|<span data-ttu-id="572f2-199">**ObjectName**</span><span class="sxs-lookup"><span data-stu-id="572f2-199">**ObjectName**</span></span>|<span data-ttu-id="572f2-200">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="572f2-200">**nvarchar**</span></span>|<span data-ttu-id="572f2-201">用于此连接的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="572f2-201">The connect string used for this connection.</span></span>|<span data-ttu-id="572f2-202">34</span><span class="sxs-lookup"><span data-stu-id="572f2-202">34</span></span>|<span data-ttu-id="572f2-203">否</span><span class="sxs-lookup"><span data-stu-id="572f2-203">No</span></span>|  
|<span data-ttu-id="572f2-204">**OwnerName**</span><span class="sxs-lookup"><span data-stu-id="572f2-204">**OwnerName**</span></span>|<span data-ttu-id="572f2-205">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="572f2-205">**nvarchar**</span></span>|<span data-ttu-id="572f2-206">在本地数据库镜像端点上配置支持的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="572f2-206">Supported authentication method configured on the local database mirroring endpoint.</span></span> <span data-ttu-id="572f2-207">如果有多种可用方法，则接受（目标）端点将确定先试用哪种方法。</span><span class="sxs-lookup"><span data-stu-id="572f2-207">When more than one method is available, the accepting (target) endpoint determines which method is tried first.</span></span> <span data-ttu-id="572f2-208">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="572f2-208">Possible values are:</span></span><br /><br /> <span data-ttu-id="572f2-209">**无**。</span><span class="sxs-lookup"><span data-stu-id="572f2-209">**None**.</span></span> <span data-ttu-id="572f2-210">未配置任何身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="572f2-210">No authentication method is configured.</span></span><br /><br /> <span data-ttu-id="572f2-211">**NTLM**。</span><span class="sxs-lookup"><span data-stu-id="572f2-211">**NTLM**.</span></span> <span data-ttu-id="572f2-212">要求使用 NTLM 身份验证。</span><span class="sxs-lookup"><span data-stu-id="572f2-212">Requires NTLM authentication.</span></span><br /><br /> <span data-ttu-id="572f2-213">**KERBEROS**。</span><span class="sxs-lookup"><span data-stu-id="572f2-213">**KERBEROS**.</span></span> <span data-ttu-id="572f2-214">要求使用 Kerberos 身份验证。</span><span class="sxs-lookup"><span data-stu-id="572f2-214">Requires Kerberos authentication.</span></span><br /><br /> <span data-ttu-id="572f2-215">**NEGOTIATE**。</span><span class="sxs-lookup"><span data-stu-id="572f2-215">**NEGOTIATE**.</span></span> <span data-ttu-id="572f2-216">由 Windows 协商身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="572f2-216">Windows negotiates the authentication method.</span></span><br /><br /> <span data-ttu-id="572f2-217">**CERTIFICATE**。</span><span class="sxs-lookup"><span data-stu-id="572f2-217">**CERTIFICATE**.</span></span> <span data-ttu-id="572f2-218">要求使用为端点配置的证书，该证书存储在 **master** 数据库中。</span><span class="sxs-lookup"><span data-stu-id="572f2-218">Requires the certificate configured for the endpoint, which is stored in the **master** database.</span></span><br /><br /> <span data-ttu-id="572f2-219">**NTLM、CERTIFICATE**。</span><span class="sxs-lookup"><span data-stu-id="572f2-219">**NTLM, CERTIFICATE**.</span></span> <span data-ttu-id="572f2-220">使用 NTLM 或端点证书进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="572f2-220">Accepts NTLM or the endpoint certificate for authentication.</span></span><br /><br /> <span data-ttu-id="572f2-221">**KERBEROS、CERTIFICATE**。</span><span class="sxs-lookup"><span data-stu-id="572f2-221">**KERBEROS, CERTIFICATE**.</span></span> <span data-ttu-id="572f2-222">使用 Kerberos 或端点证书进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="572f2-222">Accepts Kerberos or the endpoint certificate for authentication.</span></span><br /><br /> <span data-ttu-id="572f2-223">**NEGOTIATE、CERTIFICATE**。</span><span class="sxs-lookup"><span data-stu-id="572f2-223">**NEGOTIATE, CERTIFICATE**.</span></span> <span data-ttu-id="572f2-224">由 Windows 协商身份验证方法，或者使用端点证书进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="572f2-224">Windows negotiates the authentication method or an endpoint certificate can be used for authentication.</span></span><br /><br /> <span data-ttu-id="572f2-225">**CERTIFICATE、NTLM**。</span><span class="sxs-lookup"><span data-stu-id="572f2-225">**CERTIFICATE, NTLM**.</span></span> <span data-ttu-id="572f2-226">使用端点证书或 NTLM 进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="572f2-226">Accepts an endpoint certificate or NTLM for authentication.</span></span><br /><br /> <span data-ttu-id="572f2-227">**CERTIFICATE、KERBEROS**。</span><span class="sxs-lookup"><span data-stu-id="572f2-227">**CERTIFICATE, KERBEROS**.</span></span> <span data-ttu-id="572f2-228">使用端点证书或 Kerberos 进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="572f2-228">Accepts an endpoint certificate or Kerberos for authentication.</span></span><br /><br /> <span data-ttu-id="572f2-229">**CERTIFICATE、NEGOTIATE**。</span><span class="sxs-lookup"><span data-stu-id="572f2-229">**CERTIFICATE, NEGOTIATE**.</span></span> <span data-ttu-id="572f2-230">使用端点证书进行身份验证，或由 Windows 协商身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="572f2-230">Accepts an endpoint certificate for authentication or Windows negotiates the authentication method.</span></span>|<span data-ttu-id="572f2-231">37</span><span class="sxs-lookup"><span data-stu-id="572f2-231">37</span></span>|<span data-ttu-id="572f2-232">否</span><span class="sxs-lookup"><span data-stu-id="572f2-232">No</span></span>|  
|<span data-ttu-id="572f2-233">**ProviderName**</span><span class="sxs-lookup"><span data-stu-id="572f2-233">**ProviderName**</span></span>|<span data-ttu-id="572f2-234">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="572f2-234">**nvarchar**</span></span>|<span data-ttu-id="572f2-235">用于此连接的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="572f2-235">The authentication method used for this connection.</span></span>|<span data-ttu-id="572f2-236">46</span><span class="sxs-lookup"><span data-stu-id="572f2-236">46</span></span>|<span data-ttu-id="572f2-237">否</span><span class="sxs-lookup"><span data-stu-id="572f2-237">No</span></span>|  
|<span data-ttu-id="572f2-238">**RoleName**</span><span class="sxs-lookup"><span data-stu-id="572f2-238">**RoleName**</span></span>|<span data-ttu-id="572f2-239">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="572f2-239">**nvarchar**</span></span>|<span data-ttu-id="572f2-240">连接的角色。</span><span class="sxs-lookup"><span data-stu-id="572f2-240">The role of the connection.</span></span> <span data-ttu-id="572f2-241">这可以是 **initiator** 或 **target**。</span><span class="sxs-lookup"><span data-stu-id="572f2-241">This is either **initiator** or **target**.</span></span>|<span data-ttu-id="572f2-242">38</span><span class="sxs-lookup"><span data-stu-id="572f2-242">38</span></span>|<span data-ttu-id="572f2-243">否</span><span class="sxs-lookup"><span data-stu-id="572f2-243">No</span></span>|  
|<span data-ttu-id="572f2-244">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="572f2-244">**ServerName**</span></span>|<span data-ttu-id="572f2-245">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="572f2-245">**nvarchar**</span></span>|<span data-ttu-id="572f2-246">所跟踪的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="572f2-246">The name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="572f2-247">26</span><span class="sxs-lookup"><span data-stu-id="572f2-247">26</span></span>|<span data-ttu-id="572f2-248">否</span><span class="sxs-lookup"><span data-stu-id="572f2-248">No</span></span>|  
|<span data-ttu-id="572f2-249">**SPID**</span><span class="sxs-lookup"><span data-stu-id="572f2-249">**SPID**</span></span>|<span data-ttu-id="572f2-250">**int**</span><span class="sxs-lookup"><span data-stu-id="572f2-250">**int**</span></span>|<span data-ttu-id="572f2-251">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 为客户端所关联的进程分配的服务器进程 ID。</span><span class="sxs-lookup"><span data-stu-id="572f2-251">The server process ID assigned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to the process associated with the client.</span></span>|<span data-ttu-id="572f2-252">12</span><span class="sxs-lookup"><span data-stu-id="572f2-252">12</span></span>|<span data-ttu-id="572f2-253">是</span><span class="sxs-lookup"><span data-stu-id="572f2-253">Yes</span></span>|  
|<span data-ttu-id="572f2-254">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="572f2-254">**StartTime**</span></span>|<span data-ttu-id="572f2-255">**datetime**</span><span class="sxs-lookup"><span data-stu-id="572f2-255">**datetime**</span></span>|<span data-ttu-id="572f2-256">事件（如果有）的开始时间。</span><span class="sxs-lookup"><span data-stu-id="572f2-256">The time at which the event started, when available.</span></span>|<span data-ttu-id="572f2-257">14</span><span class="sxs-lookup"><span data-stu-id="572f2-257">14</span></span>|<span data-ttu-id="572f2-258">是</span><span class="sxs-lookup"><span data-stu-id="572f2-258">Yes</span></span>|  
|<span data-ttu-id="572f2-259">**State**</span><span class="sxs-lookup"><span data-stu-id="572f2-259">**State**</span></span>|<span data-ttu-id="572f2-260">**int**</span><span class="sxs-lookup"><span data-stu-id="572f2-260">**int**</span></span>|<span data-ttu-id="572f2-261">指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 源代码中生成该事件的位置。</span><span class="sxs-lookup"><span data-stu-id="572f2-261">Indicates the location within the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source code that produced the event.</span></span> <span data-ttu-id="572f2-262">可能生成此事件的每个位置都有不同的状态代码。</span><span class="sxs-lookup"><span data-stu-id="572f2-262">Each location that may produce this event has a different state code.</span></span> <span data-ttu-id="572f2-263">Microsoft 支持工程师可使用此状态代码查找生成该事件的位置。</span><span class="sxs-lookup"><span data-stu-id="572f2-263">A Microsoft support engineer can use this state code to find where the event was produced.</span></span>|<span data-ttu-id="572f2-264">30</span><span class="sxs-lookup"><span data-stu-id="572f2-264">30</span></span>|<span data-ttu-id="572f2-265">否</span><span class="sxs-lookup"><span data-stu-id="572f2-265">No</span></span>|  
|<span data-ttu-id="572f2-266">**TargetUserName**</span><span class="sxs-lookup"><span data-stu-id="572f2-266">**TargetUserName**</span></span>|<span data-ttu-id="572f2-267">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="572f2-267">**nvarchar**</span></span>|<span data-ttu-id="572f2-268">登录状态。</span><span class="sxs-lookup"><span data-stu-id="572f2-268">Login state.</span></span> <span data-ttu-id="572f2-269">可取值为：</span><span class="sxs-lookup"><span data-stu-id="572f2-269">One of:</span></span><br /><br /> <span data-ttu-id="572f2-270">INITIAL</span><span class="sxs-lookup"><span data-stu-id="572f2-270">INITIAL</span></span><br /><br /> <span data-ttu-id="572f2-271">WAIT LOGIN NEGOTIATE</span><span class="sxs-lookup"><span data-stu-id="572f2-271">WAIT LOGIN NEGOTIATE</span></span><br /><br /> <span data-ttu-id="572f2-272">ONE ISC</span><span class="sxs-lookup"><span data-stu-id="572f2-272">ONE ISC</span></span><br /><br /> <span data-ttu-id="572f2-273">ONE ASC</span><span class="sxs-lookup"><span data-stu-id="572f2-273">ONE ASC</span></span><br /><br /> <span data-ttu-id="572f2-274">TWO ISC</span><span class="sxs-lookup"><span data-stu-id="572f2-274">TWO ISC</span></span><br /><br /> <span data-ttu-id="572f2-275">TWO ASC</span><span class="sxs-lookup"><span data-stu-id="572f2-275">TWO ASC</span></span><br /><br /> <span data-ttu-id="572f2-276">WAIT ISC Confirm</span><span class="sxs-lookup"><span data-stu-id="572f2-276">WAIT ISC Confirm</span></span><br /><br /> <span data-ttu-id="572f2-277">WAIT ASC Confirm</span><span class="sxs-lookup"><span data-stu-id="572f2-277">WAIT ASC Confirm</span></span><br /><br /> <span data-ttu-id="572f2-278">WAIT REJECT</span><span class="sxs-lookup"><span data-stu-id="572f2-278">WAIT REJECT</span></span><br /><br /> <span data-ttu-id="572f2-279">WAIT PRE-MASTER SECRET</span><span class="sxs-lookup"><span data-stu-id="572f2-279">WAIT PRE-MASTER SECRET</span></span><br /><br /> <span data-ttu-id="572f2-280">WAIT VALIDATION</span><span class="sxs-lookup"><span data-stu-id="572f2-280">WAIT VALIDATION</span></span><br /><br /> <span data-ttu-id="572f2-281">WAIT ARBITRATION</span><span class="sxs-lookup"><span data-stu-id="572f2-281">WAIT ARBITRATION</span></span><br /><br /> <span data-ttu-id="572f2-282">ONLINE</span><span class="sxs-lookup"><span data-stu-id="572f2-282">ONLINE</span></span><br /><br /> <span data-ttu-id="572f2-283">ERROR</span><span class="sxs-lookup"><span data-stu-id="572f2-283">ERROR</span></span><br /><br /> <br /><br /> <span data-ttu-id="572f2-284">注意：ISC = 启动安全上下文。</span><span class="sxs-lookup"><span data-stu-id="572f2-284">Note: ISC = Initiate Security Context.</span></span> <span data-ttu-id="572f2-285">ASC = 接受安全上下文。</span><span class="sxs-lookup"><span data-stu-id="572f2-285">ASC = Accept Security Context.</span></span>|<span data-ttu-id="572f2-286">39</span><span class="sxs-lookup"><span data-stu-id="572f2-286">39</span></span>|<span data-ttu-id="572f2-287">否</span><span class="sxs-lookup"><span data-stu-id="572f2-287">No</span></span>|  
|<span data-ttu-id="572f2-288">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="572f2-288">**TransactionID**</span></span>|<span data-ttu-id="572f2-289">**bigint**</span><span class="sxs-lookup"><span data-stu-id="572f2-289">**bigint**</span></span>|<span data-ttu-id="572f2-290">系统为事务分配的 ID。</span><span class="sxs-lookup"><span data-stu-id="572f2-290">The system-assigned ID of the transaction.</span></span>|<span data-ttu-id="572f2-291">4</span><span class="sxs-lookup"><span data-stu-id="572f2-291">4</span></span>|<span data-ttu-id="572f2-292">否</span><span class="sxs-lookup"><span data-stu-id="572f2-292">No</span></span>|  
  
 <span data-ttu-id="572f2-293">下表列出了此事件类的子类值。</span><span class="sxs-lookup"><span data-stu-id="572f2-293">The table below lists the subclass values for this event class.</span></span>  
  
|<span data-ttu-id="572f2-294">ID</span><span class="sxs-lookup"><span data-stu-id="572f2-294">ID</span></span>|<span data-ttu-id="572f2-295">子类</span><span class="sxs-lookup"><span data-stu-id="572f2-295">Subclass</span></span>|<span data-ttu-id="572f2-296">说明</span><span class="sxs-lookup"><span data-stu-id="572f2-296">Description</span></span>|  
|--------|--------------|-----------------|  
|<span data-ttu-id="572f2-297">1</span><span class="sxs-lookup"><span data-stu-id="572f2-297">1</span></span>|<span data-ttu-id="572f2-298">Login Success</span><span class="sxs-lookup"><span data-stu-id="572f2-298">Login Success</span></span>|<span data-ttu-id="572f2-299">Login Success 事件报告相邻的数据库镜像登录进程已成功完成。</span><span class="sxs-lookup"><span data-stu-id="572f2-299">A Login Success event reports that the adjacent database mirroring login process has finished successfully.</span></span>|  
|<span data-ttu-id="572f2-300">2</span><span class="sxs-lookup"><span data-stu-id="572f2-300">2</span></span>|<span data-ttu-id="572f2-301">Login Protocol Error</span><span class="sxs-lookup"><span data-stu-id="572f2-301">Login Protocol Error</span></span>|<span data-ttu-id="572f2-302">Login Protocol Error 事件报告数据库镜像登录收到一条格式正确但对登录进程的当前状态无效的消息。</span><span class="sxs-lookup"><span data-stu-id="572f2-302">A Login Protocol Error event reports that the database mirroring login receives a message that is well-formed but not valid for the current state of the login process.</span></span> <span data-ttu-id="572f2-303">消息可能已丢失，或未按顺序发送。</span><span class="sxs-lookup"><span data-stu-id="572f2-303">The message may have been lost or sent out-of-sequence.</span></span>|  
|<span data-ttu-id="572f2-304">3</span><span class="sxs-lookup"><span data-stu-id="572f2-304">3</span></span>|<span data-ttu-id="572f2-305">Message Format Error</span><span class="sxs-lookup"><span data-stu-id="572f2-305">Message Format Error</span></span>|<span data-ttu-id="572f2-306">Message Format Error 事件报告数据库镜像登录收到一条与所需格式不匹配的消息。</span><span class="sxs-lookup"><span data-stu-id="572f2-306">A Message Format Error event reports that the database mirroring login received a message that does not match the expected format.</span></span> <span data-ttu-id="572f2-307">消息可能已损坏，或者其他程序（而非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ）正在向数据库镜像使用的端口发送消息。</span><span class="sxs-lookup"><span data-stu-id="572f2-307">The message may have been corrupted, or a program other than [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] may be sending messages to the port that database mirroring uses.</span></span>|  
|<span data-ttu-id="572f2-308">4</span><span class="sxs-lookup"><span data-stu-id="572f2-308">4</span></span>|<span data-ttu-id="572f2-309">Negotiate Failure</span><span class="sxs-lookup"><span data-stu-id="572f2-309">Negotiate Failure</span></span>|<span data-ttu-id="572f2-310">Negotiate Failure 事件报告本地数据库镜像端点和远程数据库镜像端点互相支持身份验证的排他级别。</span><span class="sxs-lookup"><span data-stu-id="572f2-310">A Negotiate Failure event reports that the local database mirroring endpoint and the remote database mirroring endpoint support mutually exclusive levels of authentication.</span></span>|  
|<span data-ttu-id="572f2-311">5</span><span class="sxs-lookup"><span data-stu-id="572f2-311">5</span></span>|<span data-ttu-id="572f2-312">Authentication Failure</span><span class="sxs-lookup"><span data-stu-id="572f2-312">Authentication Failure</span></span>|<span data-ttu-id="572f2-313">Authentication Failure 事件报告数据库镜像端点由于错误而无法对连接执行身份验证。</span><span class="sxs-lookup"><span data-stu-id="572f2-313">An Authentication Failure event reports that a database mirroring endpoint cannot perform authentication for the connection due to an error.</span></span> <span data-ttu-id="572f2-314">对于 Windows 身份验证，此事件报告数据库镜像端点无法使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="572f2-314">For Windows Authentication, this event reports that the database mirroring endpoint is unable to use Windows Authentication.</span></span> <span data-ttu-id="572f2-315">对于基于证书的身份验证，此事件报告数据库镜像端点无法访问证书。</span><span class="sxs-lookup"><span data-stu-id="572f2-315">For certificate-based authentication, this event reports that the database mirroring endpoint is unable to access the certificate.</span></span>|  
|<span data-ttu-id="572f2-316">6</span><span class="sxs-lookup"><span data-stu-id="572f2-316">6</span></span>|<span data-ttu-id="572f2-317">授权失败</span><span class="sxs-lookup"><span data-stu-id="572f2-317">Authorization Failure</span></span>|<span data-ttu-id="572f2-318">Authorization Failure 事件报告数据库镜像端点拒绝为连接授权。</span><span class="sxs-lookup"><span data-stu-id="572f2-318">An Authorization Failure event reports that a database mirroring endpoint denied authorization for the connection.</span></span> <span data-ttu-id="572f2-319">对于 Windows 身份验证，此事件报告连接的安全标识符与数据库用户不匹配。</span><span class="sxs-lookup"><span data-stu-id="572f2-319">For Windows Authentication, this event reports that the security identifier for the connection does not match a database user.</span></span> <span data-ttu-id="572f2-320">对于基于证书的身份验证，此事件报告消息中传递的公钥与 **master** 数据库中的证书不对应。</span><span class="sxs-lookup"><span data-stu-id="572f2-320">For certificate-based authentication, this event reports that the public key delivered in the message does not correspond to a certificate in the **master** database.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="572f2-321">另请参阅</span><span class="sxs-lookup"><span data-stu-id="572f2-321">See Also</span></span>  
 <span data-ttu-id="572f2-322">[CREATE ENDPOINT (Transact-SQL)](/sql/t-sql/statements/create-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="572f2-322">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="572f2-323">[ALTER ENDPOINT (Transact-SQL)](/sql/t-sql/statements/alter-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="572f2-323">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span></span>  
 [<span data-ttu-id="572f2-324">数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="572f2-324">Database Mirroring &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  