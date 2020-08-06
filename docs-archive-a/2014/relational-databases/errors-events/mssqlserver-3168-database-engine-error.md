---
title: MSSQLSERVER_3168 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3168 (Database Engine error)
ms.assetid: 991111d9-1eb3-43e9-9333-a75a775c3200
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 764f456653365c085e9f756a749910bbd03b4259
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586722"
---
# <a name="mssqlserver_3168"></a><span data-ttu-id="30664-102">MSSQLSERVER_3168</span><span class="sxs-lookup"><span data-stu-id="30664-102">MSSQLSERVER_3168</span></span>
    
## <a name="details"></a><span data-ttu-id="30664-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="30664-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="30664-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="30664-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="30664-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="30664-105">Event ID</span></span>|<span data-ttu-id="30664-106">3168</span><span class="sxs-lookup"><span data-stu-id="30664-106">3168</span></span>|  
|<span data-ttu-id="30664-107">事件源</span><span class="sxs-lookup"><span data-stu-id="30664-107">Event Source</span></span>|<span data-ttu-id="30664-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="30664-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="30664-109">组件</span><span class="sxs-lookup"><span data-stu-id="30664-109">Component</span></span>|<span data-ttu-id="30664-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="30664-110">SQLEngine</span></span>|  
|<span data-ttu-id="30664-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="30664-111">Symbolic Name</span></span>|<span data-ttu-id="30664-112">LDDB_SYSTEMWRONGVER</span><span class="sxs-lookup"><span data-stu-id="30664-112">LDDB_SYSTEMWRONGVER</span></span>|  
|<span data-ttu-id="30664-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="30664-113">Message Text</span></span>|<span data-ttu-id="30664-114">无法还原设备 %ls 上的系统数据库备份，因为创建该数据库的服务器版本 (%ls) 与此服务器 (%ls) 的版本不同。</span><span class="sxs-lookup"><span data-stu-id="30664-114">The backup of the system database on the device %ls cannot be restored because it was created by a different version of the server (%ls) than this server (%ls).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="30664-115">说明</span><span class="sxs-lookup"><span data-stu-id="30664-115">Explanation</span></span>  
 <span data-ttu-id="30664-116">不能在与原来执行备份的服务器内部版本不同的内部版本上还原系统数据库（**master**、**model** 或 **msdb**）的备份。</span><span class="sxs-lookup"><span data-stu-id="30664-116">You cannot restore a backup of a system database (**master**, **model**, or **msdb**) on a server build that differs from the build on which the backup was originally performed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30664-117">安装 Service Pack 或修补程序会更改服务器内部版本号，并且服务器内部版本始终是递增的。</span><span class="sxs-lookup"><span data-stu-id="30664-117">Installing a service pack or a hotfix build changes the server build number, and server builds are always incremental.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="30664-118">可能的原因</span><span class="sxs-lookup"><span data-stu-id="30664-118">Possible Causes</span></span>  
 <span data-ttu-id="30664-119">系统数据库的数据库架构在各服务器内部版本之间可能会发生更改。</span><span class="sxs-lookup"><span data-stu-id="30664-119">The database schema for system databases may be changed across server builds.</span></span> <span data-ttu-id="30664-120">为确保架构更改不会产生不一致，RESTORE 语句会将备份文件的服务器内部版本号与尝试在其上还原备份的服务器内部版本号进行比较。</span><span class="sxs-lookup"><span data-stu-id="30664-120">To make sure that a schema change does not cause inconsistencies, the RESTORE statement compares the server build number on the backup file to the build number of the server on which you are trying to restore the backup.</span></span> <span data-ttu-id="30664-121">如果内部版本不相同，则该语句会发出 3168 错误消息，从而导致还原操作异常终止。</span><span class="sxs-lookup"><span data-stu-id="30664-121">If the builds are different, the statement issues the 3168 error message, and the restore operation terminates abnormally.</span></span>  
  
 <span data-ttu-id="30664-122">可能发生此错误的情况包括：</span><span class="sxs-lookup"><span data-stu-id="30664-122">Some scenarios in which this problem may occur include the following:</span></span>  
  
-   <span data-ttu-id="30664-123">用户试图在服务器 A 上使用在服务器 B 上执行的备份来还原系统数据库。服务器 A 和 B 的服务器内部版本不同。</span><span class="sxs-lookup"><span data-stu-id="30664-123">A user tries to restore a system database on Server A from a backup taken on Server B. Servers A and B are on different server builds.</span></span> <span data-ttu-id="30664-124">例如，服务器 A 可能是原始发布版本的内部版本，而服务器 B 可能是 Service Pack 1 (SP1) 内部版本。</span><span class="sxs-lookup"><span data-stu-id="30664-124">For example, Server A might be on the original release version build and Server B might be on a service pack 1 (SP1) build.</span></span>  
  
-   <span data-ttu-id="30664-125">用户试图从在同一服务器上执行的备份还原系统数据库。</span><span class="sxs-lookup"><span data-stu-id="30664-125">A user tries to restore a system database from a backup taken on the same server.</span></span> <span data-ttu-id="30664-126">但是，执行备份时服务器运行的是不同的内部版本。</span><span class="sxs-lookup"><span data-stu-id="30664-126">However, the server was running a different build when the backup occurred.</span></span> <span data-ttu-id="30664-127">即执行备份后对服务器进行了升级。</span><span class="sxs-lookup"><span data-stu-id="30664-127">That is, the server was upgraded since the backup was performed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="30664-128">用户操作</span><span class="sxs-lookup"><span data-stu-id="30664-128">User Action</span></span>  
 <span data-ttu-id="30664-129">在此情况下的还原过程相当复杂，应在不得已的情况下才使用。</span><span class="sxs-lookup"><span data-stu-id="30664-129">The restore process in this situation is fairly involved, and used only as a last resort.</span></span> <span data-ttu-id="30664-130">有关详细信息，请参阅“[无法将系统数据库备份还原到不同内部版本的 SQL Server](https://support.microsoft.com/kb/264474)”。</span><span class="sxs-lookup"><span data-stu-id="30664-130">For more information, see"[You cannot restore system database backups to a different build of SQL Server](https://support.microsoft.com/kb/264474)".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30664-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30664-131">See Also</span></span>  
 [<span data-ttu-id="30664-132">备份和还原系统数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="30664-132">Back Up and Restore of System Databases &#40;SQL Server&#41;</span></span>](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
  
