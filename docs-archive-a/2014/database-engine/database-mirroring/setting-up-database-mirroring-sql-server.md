---
title: 设置数据库镜像 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
ms.assetid: da45efed-55eb-4c71-be34-ac2589dfce8d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7e55e973ffbb888394d13578f21e08a08ae9d03c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587581"
---
# <a name="setting-up-database-mirroring-sql-server"></a><span data-ttu-id="18d94-102">设置数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="18d94-102">Setting Up Database Mirroring (SQL Server)</span></span>
  <span data-ttu-id="18d94-103">本节说明了设置数据库镜像的前提条件、建议和步骤。</span><span class="sxs-lookup"><span data-stu-id="18d94-103">This section describes the prerequisites, recommendations, and steps for setting up database mirroring.</span></span> <span data-ttu-id="18d94-104">有关数据库镜像的介绍，请参阅 [数据库镜像 (SQL Server)](database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="18d94-104">For an introduction to database mirroring, see [Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="18d94-105">我们建议您在非高峰时段配置数据库镜像，因为配置会影响性能。</span><span class="sxs-lookup"><span data-stu-id="18d94-105">We recommend that you configure database mirroring during off-peak hours because configuration can impact performance.</span></span>  
  
 
  
##  <a name="preparing-a-server-instance-to-host-a-mirror-server"></a><a name="PrepareInstances"></a> <span data-ttu-id="18d94-106">准备服务器实例以承载镜像服务器</span><span class="sxs-lookup"><span data-stu-id="18d94-106">Preparing a Server Instance to Host a Mirror Server</span></span>  
 <span data-ttu-id="18d94-107">对于每个数据库镜像会话：</span><span class="sxs-lookup"><span data-stu-id="18d94-107">For each database mirroring session:</span></span>  
  
1.  <span data-ttu-id="18d94-108">主体服务器、镜像服务器和见证服务器（如果有）都必须由位于单独的主机系统中的独立服务器实例承载。</span><span class="sxs-lookup"><span data-stu-id="18d94-108">The principal server, mirror server, and witness, if any, must be hosted by separate server instances, which should be on separate host systems.</span></span> <span data-ttu-id="18d94-109">每个服务器实例都需要数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="18d94-109">Each of the server instances requires a database mirroring endpoint.</span></span> <span data-ttu-id="18d94-110">如果您需要创建一个数据库镜像端点，请确保其他服务器实例无法访问该端点。</span><span class="sxs-lookup"><span data-stu-id="18d94-110">If you need to create a database mirroring endpoint, ensure that it is accessible to the other server instances.</span></span>  
  
     <span data-ttu-id="18d94-111">服务器实例对数据库镜像使用的验证形式是其数据库镜像端点的一种属性。</span><span class="sxs-lookup"><span data-stu-id="18d94-111">The form of authentication used for database mirroring by a server instance is a property of its database mirroring endpoint.</span></span> <span data-ttu-id="18d94-112">两种类型的传输安全性可用于数据库镜像：Windows 身份验证或基于证书的身份验证。</span><span class="sxs-lookup"><span data-stu-id="18d94-112">Two types of transport security are available for database mirroring: Windows Authentication or certificate-based authentication.</span></span> <span data-ttu-id="18d94-113">有关详细信息，请参阅[数据库镜像的传输安全性和 AlwaysOn 可用性组 &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="18d94-113">For more information, see [Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md).</span></span>  
  
     <span data-ttu-id="18d94-114">网络访问要求是特定于身份验证形式的，如下所示：</span><span class="sxs-lookup"><span data-stu-id="18d94-114">The requirements for network access are specific to the form of authentication, as follows:</span></span>  
  
    -   <span data-ttu-id="18d94-115">**在使用 Windows 身份验证的情况下**</span><span class="sxs-lookup"><span data-stu-id="18d94-115">**If using Windows Authentication**</span></span>  
  
         <span data-ttu-id="18d94-116">如果服务器实例使用不同的域用户帐户运行，则每个实例还需要在其他实例的 **master** 数据库中具有登录名。</span><span class="sxs-lookup"><span data-stu-id="18d94-116">If server instances are running under different domain user accounts, each requires a login in the **master** database of the others.</span></span> <span data-ttu-id="18d94-117">如果登录名不存在，则必须先创建。</span><span class="sxs-lookup"><span data-stu-id="18d94-117">If the login does not exist, you must create it.</span></span> <span data-ttu-id="18d94-118">有关详细信息，请参阅 [允许使用 Windows 身份验证对数据库镜像终结点进行网络访问 (SQL Server)](../database-mirroring-allow-network-access-windows-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="18d94-118">For more information, see [Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
    -   <span data-ttu-id="18d94-119">**在使用证书的情况下**</span><span class="sxs-lookup"><span data-stu-id="18d94-119">**If using certificates**</span></span>  
  
         <span data-ttu-id="18d94-120">若要在给定的服务器实例上启用数据库镜像的证书验证，系统管理员必须配置每个服务器实例，以在出站连接和进站连接中使用证书。</span><span class="sxs-lookup"><span data-stu-id="18d94-120">To enable certificate authentication for database mirroring on a given server instance, the system administrator must configure each server instance to use certificates on both outbound and inbound connections.</span></span> <span data-ttu-id="18d94-121">必须先配置出站连接。</span><span class="sxs-lookup"><span data-stu-id="18d94-121">Outbound connections must be configured first.</span></span> <span data-ttu-id="18d94-122">有关详细信息，请参阅[使用数据库镜像终结点证书 (Transact-SQL)](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="18d94-122">For more information, see [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).</span></span>  
  
2.  <span data-ttu-id="18d94-123">确保所有数据库用户在镜像服务器上都有登录名。</span><span class="sxs-lookup"><span data-stu-id="18d94-123">Make sure that logins exist on the mirror server for all the database users.</span></span> <span data-ttu-id="18d94-124">有关详细信息，请参阅[设置数据库镜像的登录帐户或 AlwaysOn 可用性组 &#40;SQL Server&#41;](set-up-login-accounts-database-mirroring-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="18d94-124">For more information, see [Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](set-up-login-accounts-database-mirroring-always-on-availability.md).</span></span>  
  
3.  <span data-ttu-id="18d94-125">在将承载镜像数据库的服务器实例上，设置镜像数据库所需的环境的其余部分。</span><span class="sxs-lookup"><span data-stu-id="18d94-125">On the server instance that will host the mirror database, set up the rest of the environment that is required for the mirrored database.</span></span> <span data-ttu-id="18d94-126">有关详细信息，请参阅 [当数据库在其他服务器实例上可用时管理元数据 (SQL Server)](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)。</span><span class="sxs-lookup"><span data-stu-id="18d94-126">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
##  <a name="overview-establishing-a-database-mirroring-session"></a><a name="EstablishUsingWinAuthentication"></a> <span data-ttu-id="18d94-127">概述：建立数据库镜像会话</span><span class="sxs-lookup"><span data-stu-id="18d94-127">Overview: Establishing a Database Mirroring Session</span></span>  
 <span data-ttu-id="18d94-128">以下是建立镜像会话的基本步骤：</span><span class="sxs-lookup"><span data-stu-id="18d94-128">The basic steps for establishing a mirroring session are as follows:</span></span>  
  
1.  <span data-ttu-id="18d94-129">通过对每个还原操作使用 RESTORE WITH NORECOVERY 还原以下备份来创建镜像数据库：</span><span class="sxs-lookup"><span data-stu-id="18d94-129">Create the mirror database by restoring the following backups, using RESTORE WITH NORECOVERY on every restore operation:</span></span>  
  
    1.  <span data-ttu-id="18d94-130">在确保主体数据库在执行备份时使用了完整恢复模式后，还原主体数据库的最新完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="18d94-130">Restore a recent full database backup of the principal database, after making sure that the principal database was already using the full recovery model when the backup was taken.</span></span> <span data-ttu-id="18d94-131">镜像数据库的名称必须与主体数据库的名称相同。</span><span class="sxs-lookup"><span data-stu-id="18d94-131">The mirror database must have the same name as the principal database.</span></span>  
  
    2.  <span data-ttu-id="18d94-132">如果您自还原完整备份以来已对数据库执行任何差异备份，请还原最新的差异备份。</span><span class="sxs-lookup"><span data-stu-id="18d94-132">If you have taken any differential backups of the database since the restored full backup, restore your most recent differential backup.</span></span>  
  
    3.  <span data-ttu-id="18d94-133">还原自完整数据库备份或差异数据库备份以来进行的所有日志备份。</span><span class="sxs-lookup"><span data-stu-id="18d94-133">Restore all the log backups done since the full or differential database backup.</span></span>  
  
     <span data-ttu-id="18d94-134">有关详细信息，请参阅 [为镜像准备镜像数据库 (SQL Server)](prepare-a-mirror-database-for-mirroring-sql-server.md)的各版本中均未提供见证服务器实例。</span><span class="sxs-lookup"><span data-stu-id="18d94-134">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="18d94-135">在进行主体数据库的备份后，尽快完成剩余设置步骤。</span><span class="sxs-lookup"><span data-stu-id="18d94-135">Complete the remaining setup steps as soon as you can after taking the backup of the principal database.</span></span> <span data-ttu-id="18d94-136">对伙伴开始镜像之前，应该创建原始数据库的当前日志备份并将其还原到将来的镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="18d94-136">Before you can start mirroring on the partners, you should create a current log backup on the original database and restore it to the future mirror database.</span></span>  
  
2.  <span data-ttu-id="18d94-137">可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 或数据库镜像向导来设置镜像。</span><span class="sxs-lookup"><span data-stu-id="18d94-137">You can set up mirroring by using either [!INCLUDE[tsql](../../includes/tsql-md.md)] or the Database Mirroring Wizard.</span></span> <span data-ttu-id="18d94-138">有关详细信息，请参阅下列内容之一：</span><span class="sxs-lookup"><span data-stu-id="18d94-138">For more information, see one of the following:</span></span>  
  
    -   [<span data-ttu-id="18d94-139">使用 Windows 身份验证建立数据库镜像会话 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="18d94-139">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
  
    -   [<span data-ttu-id="18d94-140">使用 Windows 身份验证建立数据库镜像会话 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="18d94-140">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
3.  <span data-ttu-id="18d94-141">默认情况下，会话设置为完整事务安全（SAFETY 设置为 FULL），此设置会在同步、不带自动故障转移功能的高安全性模式下启动会话。</span><span class="sxs-lookup"><span data-stu-id="18d94-141">By default a session is set to full transaction safety (SAFETY is set to FULL), which starts the session in synchronous, high-safety mode without automatic failover.</span></span> <span data-ttu-id="18d94-142">您可以将会话重新配置为在具有自动故障转移功能的高安全性模式下运行，或者在异步、高性能模式下运行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="18d94-142">You can reconfigure the session to run in high-safety mode with automatic failover or in asynchronous, high-performance mode, as follows:</span></span>  
  
    -   <span data-ttu-id="18d94-143">**具有自动故障转移的高安全性模式**</span><span class="sxs-lookup"><span data-stu-id="18d94-143">**High-safety mode with automatic failover**</span></span>  
  
         <span data-ttu-id="18d94-144">如果希望高安全性模式会话支持自动故障转移，则请添加见证服务器实例。</span><span class="sxs-lookup"><span data-stu-id="18d94-144">If you want a high-safety mode session to support automatic failover, add a witness server instance.</span></span>  
  
         <span data-ttu-id="18d94-145">**添加见证服务器**</span><span class="sxs-lookup"><span data-stu-id="18d94-145">**To add a witness**</span></span>  
  
        -   [<span data-ttu-id="18d94-146">使用 Windows 身份验证添加数据库镜像见证服务器 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="18d94-146">Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
        -   [<span data-ttu-id="18d94-147">使用 Windows 身份验证建立数据库镜像会话 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="18d94-147">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
        > [!NOTE]  
        >  <span data-ttu-id="18d94-148">数据库所有者可以随时关闭数据库的见证服务器。</span><span class="sxs-lookup"><span data-stu-id="18d94-148">The database owner can turn off the witness for a database at any time.</span></span> <span data-ttu-id="18d94-149">关闭见证服务器就等于没有见证服务器，因此不能进行自动故障转移。</span><span class="sxs-lookup"><span data-stu-id="18d94-149">Turning off the witness is equivalent to having no witness, and automatic failover cannot occur.</span></span>  
  
    -   <span data-ttu-id="18d94-150">**高性能模式**</span><span class="sxs-lookup"><span data-stu-id="18d94-150">**High-performance mode**</span></span>  
  
         <span data-ttu-id="18d94-151">另外，如果您不想进行自动故障转移，并且您对性能的追求超过了可用性，则请关闭事务安全。</span><span class="sxs-lookup"><span data-stu-id="18d94-151">Alternatively, if you do not want automatic failover and you prefer to emphasize performance over availability, turn off transaction safety.</span></span> <span data-ttu-id="18d94-152">有关详细信息，请参阅[更改数据库镜像会话中的事务安全 (Transact-SQL)](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="18d94-152">For more information, see [Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md).</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="18d94-153">在高性能模式下，WITNESS 需设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="18d94-153">In high-performance mode, WITNESS needs to be set to OFF.</span></span> <span data-ttu-id="18d94-154">有关详细信息，请参阅[仲裁：见证服务器如何影响数据库可用性（数据库镜像）](quorum-how-a-witness-affects-database-availability-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="18d94-154">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="18d94-155">有关使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 设置使用 Microsoft Windows 身份验证的数据库镜像的示例，请参阅[示例：使用 Windows 身份验证设置数据库镜像 (Transact-SQL)](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="18d94-155">For an example of using [!INCLUDE[tsql](../../includes/tsql-md.md)] to set up database mirroring using Microsoft Windows Authentication, see [Example: Setting Up Database Mirroring Using Windows Authentication &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md).</span></span>  
>   
>  <span data-ttu-id="18d94-156">有关使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 来设置使用基于证书的安全机制的数据库镜像的示例，请参阅[示例：使用证书设置数据库镜像 (Transact-SQL)](example-setting-up-database-mirroring-using-certificates-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="18d94-156">For an example of using [!INCLUDE[tsql](../../includes/tsql-md.md)] to set up database mirroring using certificate-based security, see [Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md).</span></span>  
  
 
  
##  <a name="in-this-section"></a><a name="InThisSection"></a> <span data-ttu-id="18d94-157">本节内容</span><span class="sxs-lookup"><span data-stu-id="18d94-157">In This Section</span></span>  
 [<span data-ttu-id="18d94-158">为镜像准备镜像数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="18d94-158">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](prepare-a-mirror-database-for-mirroring-sql-server.md)  
 <span data-ttu-id="18d94-159">概述了在恢复挂起的会话之前创建或准备镜像数据库的步骤。</span><span class="sxs-lookup"><span data-stu-id="18d94-159">Summarizes the steps for creating a mirror database or preparing a mirror database before resuming a suspended session.</span></span> <span data-ttu-id="18d94-160">同时还提供了指向操作指南主题的链接。</span><span class="sxs-lookup"><span data-stu-id="18d94-160">Also provides links to how-to topics.</span></span>  
  
 [<span data-ttu-id="18d94-161">指定服务器网络地址（数据库镜像）</span><span class="sxs-lookup"><span data-stu-id="18d94-161">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](specify-a-server-network-address-database-mirroring.md)  
 <span data-ttu-id="18d94-162">说明了服务器网络地址的语法，此地址如何标识服务器实例的数据库镜像端点以及如何查找完全限定的系统域名。</span><span class="sxs-lookup"><span data-stu-id="18d94-162">Describes the syntax of a server network address, how the address identifies the database mirroring endpoint of the server instance, and how to find the fully-qualified domain name of a system.</span></span>  
  
 [<span data-ttu-id="18d94-163">使用 Windows 身份验证建立数据库镜像会话 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="18d94-163">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
 <span data-ttu-id="18d94-164">说明了如何使用配置数据库镜像安全向导在数据库上启动数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="18d94-164">Describes how to use the Configure Database Mirroring Security Wizard to start database mirroring on a database.</span></span>  
  
 [<span data-ttu-id="18d94-165">使用 Windows 身份验证建立数据库镜像会话 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="18d94-165">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
 <span data-ttu-id="18d94-166">说明了设置数据库镜像的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 步骤。</span><span class="sxs-lookup"><span data-stu-id="18d94-166">Describes the [!INCLUDE[tsql](../../includes/tsql-md.md)] steps for setting up database mirroring.</span></span>  
  
 [<span data-ttu-id="18d94-167">示例：使用 Windows 身份验证设置数据库镜像 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="18d94-167">Example: Setting Up Database Mirroring Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md)  
 <span data-ttu-id="18d94-168">包含使用 Windows 身份验证创建带有见证服务器的数据库镜像会话所需的所有阶段的示例。</span><span class="sxs-lookup"><span data-stu-id="18d94-168">Contains an example of all the stages required to create a database mirroring session with a witness, using Windows Authentication.</span></span>  
  
 [<span data-ttu-id="18d94-169">示例：使用证书设置数据库镜像 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="18d94-169">Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;</span></span>](example-setting-up-database-mirroring-using-certificates-transact-sql.md)  
 <span data-ttu-id="18d94-170">包含使用基于证书的身份验证创建带有见证服务器的数据库镜像会话所需的所有阶段的示例。</span><span class="sxs-lookup"><span data-stu-id="18d94-170">Contains an example of all the stages required to create a database mirroring session with a witness, using certificate-based authentication.</span></span>  
  
 [<span data-ttu-id="18d94-171">设置用于数据库镜像或 AlwaysOn 可用性组 &#40;SQL Server 的登录帐户&#41;</span><span class="sxs-lookup"><span data-stu-id="18d94-171">Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](set-up-login-accounts-database-mirroring-always-on-availability.md)  
 <span data-ttu-id="18d94-172">说明了创建使用本地服务器实例以外的帐户的远程服务器实例登录。</span><span class="sxs-lookup"><span data-stu-id="18d94-172">Describes creating a login for a remote server instance that is using a different account than the local server instance.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="18d94-173">相关任务</span><span class="sxs-lookup"><span data-stu-id="18d94-173">Related Tasks</span></span>  
 <span data-ttu-id="18d94-174">**SQL Server Management Studio**</span><span class="sxs-lookup"><span data-stu-id="18d94-174">**SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="18d94-175">启动配置数据库镜像安全向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="18d94-175">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
-   [<span data-ttu-id="18d94-176">使用 Windows 身份验证建立数据库镜像会话 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="18d94-176">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
 <span data-ttu-id="18d94-177">**Transact-SQL**</span><span class="sxs-lookup"><span data-stu-id="18d94-177">**Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="18d94-178">允许使用 Windows 身份验证对数据库镜像终结点进行网络访问 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="18d94-178">Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;</span></span>](../database-mirroring-allow-network-access-windows-authentication.md)  
  
-   [<span data-ttu-id="18d94-179">允许数据库镜像终结点使用证书进行出站连接 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="18d94-179">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-outbound-connections.md)  
  
-   [<span data-ttu-id="18d94-180">允许数据库镜像终结点将证书用于入站连接 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="18d94-180">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="18d94-181">为 Windows 身份验证创建数据库镜像终结点 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="18d94-181">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="18d94-182">使用 Windows 身份验证建立数据库镜像会话 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="18d94-182">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
  
-   [<span data-ttu-id="18d94-183">使用 Windows 身份验证添加数据库镜像见证服务器 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="18d94-183">Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="18d94-184">将镜像数据库设置为使用 Trustworthy 属性 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="18d94-184">Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;</span></span>](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)  
  
 <span data-ttu-id="18d94-185">**Transact-SQL/SQL Server Management Studio**</span><span class="sxs-lookup"><span data-stu-id="18d94-185">**Transact-SQL/SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="18d94-186">在升级服务器实例时最大限度地减少镜像数据库的停机时间</span><span class="sxs-lookup"><span data-stu-id="18d94-186">Minimize Downtime for Mirrored Databases When Upgrading Server Instances</span></span>](upgrading-mirrored-instances.md)  
  
-   [<span data-ttu-id="18d94-187">为镜像准备镜像数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="18d94-187">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
-   [<span data-ttu-id="18d94-188">数据库镜像配置故障排除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="18d94-188">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](troubleshoot-database-mirroring-configuration-sql-server.md)  
  
 
  
## <a name="see-also"></a><span data-ttu-id="18d94-189">另请参阅</span><span class="sxs-lookup"><span data-stu-id="18d94-189">See Also</span></span>  
 <span data-ttu-id="18d94-190">[数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="18d94-190">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="18d94-191">[数据库镜像：互操作性和共存 &#40;SQL Server&#41;](database-mirroring-interoperability-and-coexistence-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="18d94-191">[Database Mirroring: Interoperability and Coexistence &#40;SQL Server&#41;](database-mirroring-interoperability-and-coexistence-sql-server.md) </span></span>  
 <span data-ttu-id="18d94-192">[用于数据库镜像和 AlwaysOn 可用性组 &#40;SQL Server 的传输安全&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="18d94-192">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 [<span data-ttu-id="18d94-193">指定服务器网络地址（数据库镜像）</span><span class="sxs-lookup"><span data-stu-id="18d94-193">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](specify-a-server-network-address-database-mirroring.md)  
  
  
