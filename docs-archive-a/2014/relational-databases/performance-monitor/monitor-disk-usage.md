---
title: 监视磁盘使用情况 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- database monitoring [SQL Server], disk usage
- disks [SQL Server]
- monitoring performance [SQL Server], disk usage
- server performance [SQL Server], disk usage
- monitoring [SQL Server], disk activity
- excess paging [SQL Server]
- tuning databases [SQL Server], disk usage
- I/O [SQL Server], monitoring
- disks [SQL Server], monitoring activity
- isolating disk activity [SQL Server]
- database performance [SQL Server], disk usage
- monitoring server performance [SQL Server], disk usage
ms.assetid: 1525449c-ea7d-4222-b294-1ba1fe99c9ac
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 51479b024864322d34dc3b0208e29e93d7454184
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692860"
---
# <a name="monitor-disk-usage"></a><span data-ttu-id="c3801-102">监视磁盘使用情况</span><span class="sxs-lookup"><span data-stu-id="c3801-102">Monitor Disk Usage</span></span>
  <span data-ttu-id="c3801-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用 Microsoft Windows 操作系统输入/输出 (I/O) 调用来对您的磁盘执行读和写操作。</span><span class="sxs-lookup"><span data-stu-id="c3801-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses Microsoft Windows operating system input/output (I/O) calls to perform read and write operations on your disk.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c3801-104">管理何时以及如何执行磁盘 I/O，但是 Windows 操作系统执行基础 I/O 操作。</span><span class="sxs-lookup"><span data-stu-id="c3801-104">manages when and how disk I/O is performed, but the Windows operating system performs the underlying I/O operations.</span></span> <span data-ttu-id="c3801-105">I/O 子系统包括系统总线、磁盘控制卡、磁盘、磁带驱动器、CD-ROM 驱动器以及许多其他 I/O 设备。</span><span class="sxs-lookup"><span data-stu-id="c3801-105">The I/O subsystem includes the system bus, disk controller cards, disks, tape drives, CD-ROM drive, and many other I/O devices.</span></span> <span data-ttu-id="c3801-106">磁盘 I/O 是导致系统瓶颈的最常见原因。</span><span class="sxs-lookup"><span data-stu-id="c3801-106">Disk I/O is frequently the cause of bottlenecks in a system.</span></span>  
  
 <span data-ttu-id="c3801-107">监视磁盘活动涉及两个主要方面：</span><span class="sxs-lookup"><span data-stu-id="c3801-107">Monitoring disk activity involves two areas of focus:</span></span>  
  
-   <span data-ttu-id="c3801-108">监视磁盘 I/O 及检测过度换页</span><span class="sxs-lookup"><span data-stu-id="c3801-108">Monitoring Disk I/O and Detecting Excess Paging</span></span>  
  
-   <span data-ttu-id="c3801-109">隔离 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 产生的磁盘活动</span><span class="sxs-lookup"><span data-stu-id="c3801-109">Isolating Disk Activity That [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Creates</span></span>  
  
 <span data-ttu-id="c3801-110">有关详细信息，请参阅[监视磁盘使用情况](https://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx)</span><span class="sxs-lookup"><span data-stu-id="c3801-110">For more information see, [Monitoring Disk Usage](https://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx)</span></span>  
  
  
