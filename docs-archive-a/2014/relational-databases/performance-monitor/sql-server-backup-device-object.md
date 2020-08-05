---
title: SQL Server - Backup Device 对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Backup Device
- Backup Device object
ms.assetid: 52e7febf-d5e0-4674-945b-aacc40a9ad6e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e3126310ad31dcc153fc79508dbfaccf86f5da78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580696"
---
# <a name="sql-server-backup-device-object"></a><span data-ttu-id="fda17-102">SQL Server Backup Device 对象</span><span class="sxs-lookup"><span data-stu-id="fda17-102">SQL Server, Backup Device Object</span></span>
  <span data-ttu-id="fda17-103">**Backup Device** 对象提供的计数器可监视用于备份和还原操作的 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份设备。</span><span class="sxs-lookup"><span data-stu-id="fda17-103">The **Backup Device** object provides counters to monitor Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup devices used for backup and restore operations.</span></span> <span data-ttu-id="fda17-104">在希望基于每个设备确定吞吐量或备份和还原操作的进度及性能时，可以监视备份设备。</span><span class="sxs-lookup"><span data-stu-id="fda17-104">Monitor backup devices when you want to determine the throughput or the progress and performance of your backup and restore operations on a per device basis.</span></span> <span data-ttu-id="fda17-105">若要监视整个数据库备份或还原操作的吞吐量，请使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Databases 对象的 Backup/Restore Throughput/sec 计数器 。</span><span class="sxs-lookup"><span data-stu-id="fda17-105">To monitor the throughput of the entire database backup or restore operation, use the **Backup/Restore Throughput/sec** counter of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Databases** object.</span></span> <span data-ttu-id="fda17-106">有关详细信息，请参阅 [SQL Server, Databases Object](sql-server-databases-object.md)。</span><span class="sxs-lookup"><span data-stu-id="fda17-106">For more information, see [SQL Server, Databases Object](sql-server-databases-object.md).</span></span>  
  
 <span data-ttu-id="fda17-107">下表介绍 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份设备计数器。</span><span class="sxs-lookup"><span data-stu-id="fda17-107">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Backup Device** counter.</span></span>  
  
|<span data-ttu-id="fda17-108">SQL Server Backup Device 计数器</span><span class="sxs-lookup"><span data-stu-id="fda17-108">SQL Server Backup Device counters</span></span>|<span data-ttu-id="fda17-109">说明</span><span class="sxs-lookup"><span data-stu-id="fda17-109">Description</span></span>|  
|---------------------------------------|-----------------|  
|<span data-ttu-id="fda17-110">**Device Throughput Bytes/sec**</span><span class="sxs-lookup"><span data-stu-id="fda17-110">**Device Throughput Bytes/sec**</span></span>|<span data-ttu-id="fda17-111">一个备份设备在备份或还原数据库时所用的读写操作的吞吐量（以每秒字节数表示）。</span><span class="sxs-lookup"><span data-stu-id="fda17-111">Throughput of read and write operations (in bytes per second) for a backup device used when backing up or restoring databases.</span></span> <span data-ttu-id="fda17-112">这一计数器只有在备份或还原操作执行时才存在。</span><span class="sxs-lookup"><span data-stu-id="fda17-112">This counter exists only while the backup or restore operation is executing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fda17-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fda17-113">See Also</span></span>  
 <span data-ttu-id="fda17-114">[备份设备 (SQL Server)](../backup-restore/backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fda17-114">[Backup Devices &#40;SQL Server&#41;](../backup-restore/backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="fda17-115">监视资源使用情况（系统监视器）</span><span class="sxs-lookup"><span data-stu-id="fda17-115">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
