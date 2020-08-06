---
title: 移动数据库文件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- disaster recovery [SQL Server], moving database files
- files [SQL Server], moving
- data files [SQL Server], moving
- file moving [SQL Server]
- moving full-text catalogs
- moving databases
- full-text catalogs [SQL Server], moving
- moving database files
- scheduled disk maintenance [SQL Server]
- moving files
- relocating database files
- planned database relocations [SQL Server]
- databases [SQL Server], moving
ms.assetid: 89f01b10-5fae-4ed8-b0fb-a4b9f540fd28
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5491f3c4dfd47cac4047d0409c78001be80d6f13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691735"
---
# <a name="move-database-files"></a><span data-ttu-id="968b7-102">移动数据库文件</span><span class="sxs-lookup"><span data-stu-id="968b7-102">Move Database Files</span></span>
  <span data-ttu-id="968b7-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，可以通过在 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) 语句的 FILENAME 子句中指定新的文件位置来移动系统数据库和用户数据库。</span><span class="sxs-lookup"><span data-stu-id="968b7-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can move system and user databases by specifying the new file location in the FILENAME clause of the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement.</span></span> <span data-ttu-id="968b7-104">数据、日志和全文目录文件也可以通过此方法进行移动。</span><span class="sxs-lookup"><span data-stu-id="968b7-104">Data, log, and full-text catalog files can be moved in this way.</span></span> <span data-ttu-id="968b7-105">这在下列情况下可能很有用：</span><span class="sxs-lookup"><span data-stu-id="968b7-105">This may be useful in the following situations:</span></span>  
  
-   <span data-ttu-id="968b7-106">故障恢复。</span><span class="sxs-lookup"><span data-stu-id="968b7-106">Failure recovery.</span></span> <span data-ttu-id="968b7-107">例如，由于硬件故障，数据库处于可疑模式或被关闭。</span><span class="sxs-lookup"><span data-stu-id="968b7-107">For example, the database is in suspect mode or has shut down, because of a hardware failure.</span></span>  
  
-   <span data-ttu-id="968b7-108">预先安排的重定位。</span><span class="sxs-lookup"><span data-stu-id="968b7-108">Planned relocation.</span></span>  
  
-   <span data-ttu-id="968b7-109">为预定的磁盘维护操作而进行的重定位。</span><span class="sxs-lookup"><span data-stu-id="968b7-109">Relocation for scheduled disk maintenance.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="968b7-110">本节内容</span><span class="sxs-lookup"><span data-stu-id="968b7-110">In This Section</span></span>  
  
|<span data-ttu-id="968b7-111">主题</span><span class="sxs-lookup"><span data-stu-id="968b7-111">Topic</span></span>|<span data-ttu-id="968b7-112">说明</span><span class="sxs-lookup"><span data-stu-id="968b7-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="968b7-113">移动用户数据库</span><span class="sxs-lookup"><span data-stu-id="968b7-113">Move User Databases</span></span>](move-user-databases.md)|<span data-ttu-id="968b7-114">说明将用户数据库文件和全文目录文件移动到新位置的过程。</span><span class="sxs-lookup"><span data-stu-id="968b7-114">Describes the procedures for moving user database files and full-text catalog files to a new location.</span></span>|  
|[<span data-ttu-id="968b7-115">移动系统数据库</span><span class="sxs-lookup"><span data-stu-id="968b7-115">Move System Databases</span></span>](system-databases.md)|<span data-ttu-id="968b7-116">说明将系统数据库文件移动到新位置的过程。</span><span class="sxs-lookup"><span data-stu-id="968b7-116">Describes the procedures for moving system database files to a new location.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="968b7-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="968b7-117">See Also</span></span>  
 <span data-ttu-id="968b7-118">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="968b7-118">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="968b7-119">[CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="968b7-119">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="968b7-120">数据库分离和附加 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="968b7-120">Database Detach and Attach &#40;SQL Server&#41;</span></span>](database-detach-and-attach-sql-server.md)  
  
  
