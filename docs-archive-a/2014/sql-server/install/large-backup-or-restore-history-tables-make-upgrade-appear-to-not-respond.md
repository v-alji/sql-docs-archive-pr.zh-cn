---
title: 较大的备份或还原历史记录表会使升级显示为 "未响应" |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- backup history tables
- history tables
ms.assetid: f88d86ec-324b-4518-b6d7-1af7e7265812
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 918c20f58c00c535d8ed41d887e9671f5e821a17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578016"
---
# <a name="large-backup-or-restore-history-tables-make-upgrade-appear-to-not-respond"></a><span data-ttu-id="b63a7-102">很大的备份或还原历史记录表会使升级显得不响应</span><span class="sxs-lookup"><span data-stu-id="b63a7-102">Large backup or restore history tables make upgrade appear to not respond</span></span>
  <span data-ttu-id="b63a7-103">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中，一些备份和还原历史记录表中添加了若干新列。</span><span class="sxs-lookup"><span data-stu-id="b63a7-103">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], new columns were added to some of the backup and restore history tables.</span></span> <span data-ttu-id="b63a7-104">若要升级这些表，则需要对它们进行更改以便添加新列。</span><span class="sxs-lookup"><span data-stu-id="b63a7-104">Upgrading these tables requires altering them to add the new columns.</span></span> <span data-ttu-id="b63a7-105">如果一个或多个这样的表包含很多行，则执行向表添加列的 ALTER TABLE 语句时，升级过程将停顿很长时间。</span><span class="sxs-lookup"><span data-stu-id="b63a7-105">If one or more of these tables contains a large number of rows, the upgrade will stall for a substantial amount of time on the ALTER TABLE statement that adds columns to that table.</span></span>  
  
## <a name="component"></a><span data-ttu-id="b63a7-106">组件</span><span class="sxs-lookup"><span data-stu-id="b63a7-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="b63a7-107">说明</span><span class="sxs-lookup"><span data-stu-id="b63a7-107">Description</span></span>  
 <span data-ttu-id="b63a7-108">如果以下任何备份或还原历史记录表中包含大量行，则升级可能会停止响应：</span><span class="sxs-lookup"><span data-stu-id="b63a7-108">Upgrade can appear to stop responding if any of the following backup or restore history tables contains a large number of rows:</span></span>  
  
-   <span data-ttu-id="b63a7-109">**backupfile**</span><span class="sxs-lookup"><span data-stu-id="b63a7-109">**backupfile**</span></span>  
  
-   <span data-ttu-id="b63a7-110">**backupmediafamily**</span><span class="sxs-lookup"><span data-stu-id="b63a7-110">**backupmediafamily**</span></span>  
  
-   <span data-ttu-id="b63a7-111">**backupmediaset**</span><span class="sxs-lookup"><span data-stu-id="b63a7-111">**backupmediaset**</span></span>  
  
-   <span data-ttu-id="b63a7-112">**backupset**</span><span class="sxs-lookup"><span data-stu-id="b63a7-112">**backupset**</span></span>  
  
-   <span data-ttu-id="b63a7-113">**restorefile**</span><span class="sxs-lookup"><span data-stu-id="b63a7-113">**restorefile**</span></span>  
  
-   <span data-ttu-id="b63a7-114">**restorefilegroup**</span><span class="sxs-lookup"><span data-stu-id="b63a7-114">**restorefilegroup**</span></span>  
  
-   <span data-ttu-id="b63a7-115">**restorehistory**</span><span class="sxs-lookup"><span data-stu-id="b63a7-115">**restorehistory**</span></span>  
  
 <span data-ttu-id="b63a7-116">如果任何这样的表包含 10,000 行或更多的行，则升级顾问将报告不符合条件故障。</span><span class="sxs-lookup"><span data-stu-id="b63a7-116">If any of these tables has 10,000 or more rows, Upgrade Advisor reports a noncompliance failure.</span></span> <span data-ttu-id="b63a7-117">但是不会报告哪个表超过了允许的行数。</span><span class="sxs-lookup"><span data-stu-id="b63a7-117">It does not report which table exceeds the allowed number of rows.</span></span> <span data-ttu-id="b63a7-118">第一个超过 10,000 行的表是导致该故障的原因。</span><span class="sxs-lookup"><span data-stu-id="b63a7-118">The first table that exceeds 10,000 rows causes the failure.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="b63a7-119">纠正措施</span><span class="sxs-lookup"><span data-stu-id="b63a7-119">Corrective Action</span></span>  
 <span data-ttu-id="b63a7-120">升级数据库之前，如果任何这样的表超过了 10,000 行，我们建议将行数减少至 10,000 行以下。</span><span class="sxs-lookup"><span data-stu-id="b63a7-120">Before you upgrade a database, if any of these tables exceeds 10,000 rows, we recommend that you reduce the number to less than 10,000.</span></span> <span data-ttu-id="b63a7-121">若要减少所有这些表中的行，可以运行**sp_delete_backuphistory**存储过程。</span><span class="sxs-lookup"><span data-stu-id="b63a7-121">To reduce rows in all of these tables, you can run the **sp_delete_backuphistory** stored procedure.</span></span> <span data-ttu-id="b63a7-122">此过程会删除所有备份和还原历史记录表中早于指定日期的备份集的条目。</span><span class="sxs-lookup"><span data-stu-id="b63a7-122">This procedure deletes the entries in all of the backup and restore history tables for backup sets older than a specified date.</span></span> <span data-ttu-id="b63a7-123">有关详细信息，请参阅 [sp_delete_backuphistory (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b63a7-123">For more information, see [sp_delete_backuphistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b63a7-124">可以升级其备份和还原历史记录表大于 10,000 行的数据库。</span><span class="sxs-lookup"><span data-stu-id="b63a7-124">You can upgrade a database whose backup and restore history tables are larger than 10,000 rows.</span></span> <span data-ttu-id="b63a7-125">但在更改很大的表时，升级可能会出现停顿。</span><span class="sxs-lookup"><span data-stu-id="b63a7-125">But the upgrade may appear to stall while large tables are being altered.</span></span> <span data-ttu-id="b63a7-126">表越大，完成安装程序所需的时间就越长。</span><span class="sxs-lookup"><span data-stu-id="b63a7-126">The larger the tables, the longer that Setup takes to complete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b63a7-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b63a7-127">See Also</span></span>  
 <span data-ttu-id="b63a7-128">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="b63a7-128">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="b63a7-129">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="b63a7-129">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
