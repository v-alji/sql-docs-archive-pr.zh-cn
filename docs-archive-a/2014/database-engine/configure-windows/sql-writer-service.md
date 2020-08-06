---
title: SQL 编写器服务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- VDI [SQL Server]
- restoring [SQL Server], SQL Writer Service
- backups [SQL Server], while SQL Server running
- Volume Shadow Copy Service
- volume backups while running [SQL Server]
- Virtual Backup Device Interface [SQL Server]
- SQL Writer Service
- services [SQL Server], SQL Writer
- MSDE Writer
- VSS
ms.assetid: 0f299867-f499-4c2a-ad6f-b2ef1869381d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 310722c6617c7a2c9e0f384ec23ae371ab230536
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577828"
---
# <a name="sql-writer-service"></a><span data-ttu-id="6e4d2-102">SQL 编写器服务</span><span class="sxs-lookup"><span data-stu-id="6e4d2-102">SQL Writer Service</span></span>
  <span data-ttu-id="6e4d2-103">SQL 编写器服务通过卷影复制服务框架，提供了用来备份和还原 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的附加功能。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-103">The SQL Writer Service provides added functionality for backup and restore of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] through the Volume Shadow Copy Service framework.</span></span>  
  
 <span data-ttu-id="6e4d2-104">SQL 编写器服务是自动安装的。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-104">The SQL Writer Service is installed automatically.</span></span> <span data-ttu-id="6e4d2-105">在卷影复制服务 (VSS) 应用程序请求备份或还原时，必须运行该服务。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-105">It must be running when the Volume Shadow Copy Service (VSS) application requests a backup or restore.</span></span> <span data-ttu-id="6e4d2-106">若要配置该服务，请使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 服务小程序。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-106">To configure the service, use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Services applet.</span></span> <span data-ttu-id="6e4d2-107">SQL 编写器服务可安装在所有操作系统上。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-107">The SQL Writer Service installs on all operating systems.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="6e4d2-108">目的</span><span class="sxs-lookup"><span data-stu-id="6e4d2-108">Purpose</span></span>  
 <span data-ttu-id="6e4d2-109">在运行时， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 会锁定数据文件并具有独占访问权限。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-109">When running, [!INCLUDE[ssDE](../../includes/ssde-md.md)] locks and has exclusive access to the data files.</span></span> <span data-ttu-id="6e4d2-110">如果 SQL 编写器服务没有运行，Windows 中运行的备份程序将不能访问数据文件，而且必须使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 才能进行备份。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-110">When the SQL Writer Service is not running, backup programs running in Windows do not have access to the data files, and backups must be performed using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup.</span></span>  
  
 <span data-ttu-id="6e4d2-111">使用 SQL 编写器服务，可以使 Windows 备份程序在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 运行时复制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据文件。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-111">Use the SQL Writer Service to permit Windows backup programs to copy [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data files while [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>  
  
## <a name="volume-shadow-copy-service"></a><span data-ttu-id="6e4d2-112">卷影复制服务</span><span class="sxs-lookup"><span data-stu-id="6e4d2-112">Volume Shadow Copy Service</span></span>  
 <span data-ttu-id="6e4d2-113">VSS 是实现某一框架的一组 COM API，使得在系统中的应用程序连续写入卷的同时，能够进行卷备份。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-113">The VSS is a set of COM APIs that implements a framework to allow volume backups to be performed while applications on a system continue to write to the volumes.</span></span> <span data-ttu-id="6e4d2-114">VSS 具有一致的接口，使得更新磁盘数据的用户应用程序（编写器）和备份应用程序的用户应用程序（请求程序）之间能够协同工作。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-114">The VSS provides a consistent interface that allows coordination between user applications that update data on disk (writers) and those that back up applications (requestors).</span></span>  
  
 <span data-ttu-id="6e4d2-115">VSS 可捕获和复制正在运行的系统（尤其是服务器）的稳定映像以进行备份，而且不会过度降低它们所提供服务的性能和稳定性。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-115">The VSS captures and copies stable images for backup on running systems, particularly servers, without unduly degrading the performance and stability of the services they provide.</span></span> <span data-ttu-id="6e4d2-116">有关 VSS 的详细信息，请参阅 Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-116">For more information on the VSS, see your Windows documentation.</span></span>  
  
## <a name="virtual-backup-device-interface-vdi"></a><span data-ttu-id="6e4d2-117">虚拟备份设备接口 (VDI)</span><span class="sxs-lookup"><span data-stu-id="6e4d2-117">Virtual Backup Device Interface (VDI)</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6e4d2-118">提供称为虚拟备份设备接口 (VDI) 的 API，使独立软件供应商能够将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 集成到他们的产品中来支持备份和还原操作。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-118">provides an API called Virtual Backup Device Interface (VDI) that enables independent software vendors to integrate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] into their products for providing support for backup and restore operations.</span></span> <span data-ttu-id="6e4d2-119">这些 API 能够提供非常高的可靠性和极佳的性能，并支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的所有备份与还原功能，包括所有的热备份和快照备份功能。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-119">These APIs are engineered to provide maximum reliability and performance, and support the full range of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore functionality, including the full range of hot and snapshot backup capabilities.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="6e4d2-120">权限</span><span class="sxs-lookup"><span data-stu-id="6e4d2-120">Permissions</span></span>  
 <span data-ttu-id="6e4d2-121">SQL 编写器服务必须以 **Local System** 帐户运行。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-121">The SQL Writer service must run under the **Local System** account.</span></span> <span data-ttu-id="6e4d2-122">SQL 编写器服务使用 **NT Service\SQLWriter** 登录以连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-122">The SQL Writer service uses the **NT Service\SQLWriter** login to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6e4d2-123">使用 **NT Service\SQLWriter** 登录可使 SQL 编写器进程以较低的特权等级（指定为 **no login**的帐户）运行，以提高安全性。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-123">Using the **NT Service\SQLWriter** login allows the SQL Writer process to run at a lower privilege level in an account designated as **no login**, which limits vulnerability.</span></span> <span data-ttu-id="6e4d2-124">如果禁用 SQL 编写器服务，则依赖 VSS 快照的所有实用程序（如系统中心数据保护管理器，及某些其他的第三方产品）可能会出错，甚至更糟 — 获得的可能是不一致的数据库备份。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-124">If the SQL Writer service is disabled, then any utility which in relies on VSS snapshots, such as System Center Data Protection Manager, as well as some other 3rd-party products, would be broken, or worse, at risk of taking backups of databases which were not consistent.</span></span> <span data-ttu-id="6e4d2-125">如果运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的系统及主机系统（在运行虚拟机的情况下）均无需使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 以外的任何备份，则可安全地禁用 SQL 编写器服务并移除其登录项。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-125">If neither [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the system it runs on, nor the host system (in the event of a virtual machine), need to use anything besides [!INCLUDE[tsql](../../includes/tsql-md.md)] backup, then the SQL Writer service can be safely disabled and the login removed.</span></span>  <span data-ttu-id="6e4d2-126">注意：SQL 编写器服务可能会被系统或卷级备份（无论该备份是否直接基于快照）调用。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-126">Note that the SQL Writer service may be invoked by a system or volume level backup, whether the backup is directly snapshot-based or not.</span></span> <span data-ttu-id="6e4d2-127">某些系统备份产品使用 VSS 来避免被已打开或已锁定的文件阻止访问。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-127">Some system backup products use VSS to avoid being blocked by open or locked files.</span></span> <span data-ttu-id="6e4d2-128">需要在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中提升 SQL 编写器服务的权限，这是因为，在活动期间，它会简单地冻结 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的所有 I/O。</span><span class="sxs-lookup"><span data-stu-id="6e4d2-128">The SQL Writer service needs elevated permissions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] because in the course of its activities it briefly freezes all I/O for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="features"></a><span data-ttu-id="6e4d2-129">功能</span><span class="sxs-lookup"><span data-stu-id="6e4d2-129">Features</span></span>  
 <span data-ttu-id="6e4d2-130">SQL 编写器支持：</span><span class="sxs-lookup"><span data-stu-id="6e4d2-130">SQL Writer supports:</span></span>  
  
-   <span data-ttu-id="6e4d2-131">完整数据库备份和还原，包括全文目录</span><span class="sxs-lookup"><span data-stu-id="6e4d2-131">Full database backup and restore including full-text catalogs</span></span>  
  
-   <span data-ttu-id="6e4d2-132">差异备份和还原</span><span class="sxs-lookup"><span data-stu-id="6e4d2-132">Differential backup and restore</span></span>  
  
-   <span data-ttu-id="6e4d2-133">移动式还原</span><span class="sxs-lookup"><span data-stu-id="6e4d2-133">Restore with move</span></span>  
  
-   <span data-ttu-id="6e4d2-134">数据库重命名</span><span class="sxs-lookup"><span data-stu-id="6e4d2-134">Database rename</span></span>  
  
-   <span data-ttu-id="6e4d2-135">仅复制备份</span><span class="sxs-lookup"><span data-stu-id="6e4d2-135">Copy-only backup</span></span>  
  
-   <span data-ttu-id="6e4d2-136">自动恢复数据库快照</span><span class="sxs-lookup"><span data-stu-id="6e4d2-136">Auto-recovery of database snapshot</span></span>  
  
 <span data-ttu-id="6e4d2-137">SQL 编写器不支持：</span><span class="sxs-lookup"><span data-stu-id="6e4d2-137">SQL Writer does not support:</span></span>  
  
-   <span data-ttu-id="6e4d2-138">日志备份</span><span class="sxs-lookup"><span data-stu-id="6e4d2-138">Log backups</span></span>  
  
-   <span data-ttu-id="6e4d2-139">文件和文件组备份</span><span class="sxs-lookup"><span data-stu-id="6e4d2-139">File and filegroup backup</span></span>  
  
-   <span data-ttu-id="6e4d2-140">页面还原</span><span class="sxs-lookup"><span data-stu-id="6e4d2-140">Page restore</span></span>  
  
  
