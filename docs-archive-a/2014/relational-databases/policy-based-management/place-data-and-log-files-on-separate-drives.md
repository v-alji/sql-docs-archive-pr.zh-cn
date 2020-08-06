---
title: 将数据和日志文件放到不同的驱动器上 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 6cbedc27-4d77-44ad-bed2-c23b628475a7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d3f972ea29322a046c09657e2ed2499655c82aed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588467"
---
# <a name="place-data-and-log-files-on-separate-drives"></a><span data-ttu-id="d7b67-102">将数据和日志文件放到不同的驱动器上</span><span class="sxs-lookup"><span data-stu-id="d7b67-102">Place Data and Log Files on Separate Drives</span></span>
  <span data-ttu-id="d7b67-103">此规则检查是否将数据和日志文件放到了不同的逻辑驱动器上。</span><span class="sxs-lookup"><span data-stu-id="d7b67-103">This rule checks whether data and log files are placed on separate logical drives.</span></span> <span data-ttu-id="d7b67-104">将数据和日志文件放到同一个设备上会导致该设备的争用，并且会导致性能降低。</span><span class="sxs-lookup"><span data-stu-id="d7b67-104">Placing both data and log files on the same device can cause contention for that device and result in poor performance.</span></span> <span data-ttu-id="d7b67-105">将文件放到不同的驱动器上允许数据和日志文件的 I/O 活动同时发生。</span><span class="sxs-lookup"><span data-stu-id="d7b67-105">Placing the files on separate drives allows the I/O activity to occur at the same time for both the data and log files.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="d7b67-106">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="d7b67-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="d7b67-107">创建新的数据库时，为数据和日志指定不同的驱动器。</span><span class="sxs-lookup"><span data-stu-id="d7b67-107">When you create a new database, specify separate drives for the data and log.</span></span> <span data-ttu-id="d7b67-108">若要在创建数据库后移动文件，则必须使数据库脱机。</span><span class="sxs-lookup"><span data-stu-id="d7b67-108">To move files after the database is created, the database must be taken offline.</span></span> <span data-ttu-id="d7b67-109">使用下列方法之一移动文件：</span><span class="sxs-lookup"><span data-stu-id="d7b67-109">Move the files by using one of the following methods:</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d7b67-110">此策略无法通过装入点检测分开的物理设备。</span><span class="sxs-lookup"><span data-stu-id="d7b67-110">This policy cannot detect separate physical devices through mount points</span></span>  
  
-   <span data-ttu-id="d7b67-111">使用具有 WITH MOVE 选项的 RESTORE DATABASE 语句从备份还原数据库。</span><span class="sxs-lookup"><span data-stu-id="d7b67-111">Restore the database from backup by using the RESTORE DATABASE statement with the WITH MOVE option.</span></span>  
  
-   <span data-ttu-id="d7b67-112">通过为数据和日志设备指定不同的位置来分离然后附加数据库。</span><span class="sxs-lookup"><span data-stu-id="d7b67-112">Detach and then attach the database specifying separate locations for the data and log devices.</span></span>  
  
-   <span data-ttu-id="d7b67-113">指定新位置，方法是运行具有 MODIFY FILE 选项的 ALTER DATABASE 语句，然后重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="d7b67-113">Specify a new location by running the ALTER DATABASE statement with the MODIFY FILE option, and then restarting the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="d7b67-114">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="d7b67-114">For More Information</span></span>  
 [<span data-ttu-id="d7b67-115">移动数据库文件</span><span class="sxs-lookup"><span data-stu-id="d7b67-115">Move Database Files</span></span>](../databases/move-database-files.md)  
  
 [<span data-ttu-id="d7b67-116">移动用户数据库</span><span class="sxs-lookup"><span data-stu-id="d7b67-116">Move User Databases</span></span>](../databases/move-user-databases.md)  
  
 [<span data-ttu-id="d7b67-117">数据库分离和附加 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d7b67-117">Database Detach and Attach &#40;SQL Server&#41;</span></span>](../databases/database-detach-and-attach-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="d7b67-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d7b67-118">See Also</span></span>  
 [<span data-ttu-id="d7b67-119">使用基于策略的管理来监视和强制执行最佳做法</span><span class="sxs-lookup"><span data-stu-id="d7b67-119">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
