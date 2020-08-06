---
title: MSSQLSERVER_8992 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8992 (Database Engine error)
ms.assetid: 68467e6a-09d8-478f-8bd9-3bb09453ada3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: adcf914accab43202cf148fe852b334c9b078287
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591894"
---
# <a name="mssqlserver_8992"></a><span data-ttu-id="40d45-102">MSSQLSERVER_8992</span><span class="sxs-lookup"><span data-stu-id="40d45-102">MSSQLSERVER_8992</span></span>
    
## <a name="details"></a><span data-ttu-id="40d45-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="40d45-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="40d45-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="40d45-104">Product Name</span></span>|<span data-ttu-id="40d45-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="40d45-105">SQL Server</span></span>|  
|<span data-ttu-id="40d45-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="40d45-106">Event ID</span></span>|<span data-ttu-id="40d45-107">8992</span><span class="sxs-lookup"><span data-stu-id="40d45-107">8992</span></span>|  
|<span data-ttu-id="40d45-108">事件源</span><span class="sxs-lookup"><span data-stu-id="40d45-108">Event Source</span></span>|<span data-ttu-id="40d45-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="40d45-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="40d45-110">组件</span><span class="sxs-lookup"><span data-stu-id="40d45-110">Component</span></span>|<span data-ttu-id="40d45-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="40d45-111">SQLEngine</span></span>|  
|<span data-ttu-id="40d45-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="40d45-112">Symbolic Name</span></span>|<span data-ttu-id="40d45-113">DBCC3_CHECK_CATALOG</span><span class="sxs-lookup"><span data-stu-id="40d45-113">DBCC3_CHECK_CATALOG</span></span>|  
|<span data-ttu-id="40d45-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="40d45-114">Message Text</span></span>|<span data-ttu-id="40d45-115">请检查目录消息 ERROR，级别 LEVEL，状态 STATE:MESSAGE。</span><span class="sxs-lookup"><span data-stu-id="40d45-115">Check Catalog Msg ERROR Level LEVEL State STATE: MESSAGE.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="40d45-116">说明</span><span class="sxs-lookup"><span data-stu-id="40d45-116">Explanation</span></span>  
 <span data-ttu-id="40d45-117">DBCC CHECKCATALOG 或 DBCC CHECKDB 在指定对象的系统元数据表中发现了不一致。</span><span class="sxs-lookup"><span data-stu-id="40d45-117">DBCC CHECKCATALOG or DBCC CHECKDB found an inconsistency in the system metadata tables for the specified object.</span></span> <span data-ttu-id="40d45-118">这就是说，已记录的对象 ID 与错误消息中指定的对象之间存在不一致。</span><span class="sxs-lookup"><span data-stu-id="40d45-118">That is, there is an inconsistency between the recorded object ID and the object specified in error message.</span></span>  
  
 <span data-ttu-id="40d45-119">如果通过某种方式手动更新一个或多个系统表，而该方式在系统元数据中造成了不一致，就会发生此错误。</span><span class="sxs-lookup"><span data-stu-id="40d45-119">This error can occur when one or more system tables has been manually updated in a way that creates an inconsistency in the system metadata.</span></span> <span data-ttu-id="40d45-120">例如，用户可能从 **sysobjects** 表中手动删除了某个对象，但未从 **sysindexes** 和 **syscolumns** 等其他表中删除关联的行。</span><span class="sxs-lookup"><span data-stu-id="40d45-120">For example, a user may have manually deleted an object from the **sysobjects** table without removing associated rows in other tables such as **sysindexes** and **syscolumns**.</span></span>  
  
 <span data-ttu-id="40d45-121">在对已从 SQL Server 2000 升级至 SQL Server 2005 或更高版本的数据库运行 DBCC CHECKDB 时，也可能发生此错误。</span><span class="sxs-lookup"><span data-stu-id="40d45-121">This error can occur when running DBCC CHECKDB against a database that has been upgraded from SQL Server 2000 to SQL Server 2005 or later.</span></span> <span data-ttu-id="40d45-122">在 SQL Server 2000 中，DBCC CHECKDB 并不包括 DBCC CHECKCATALOG 功能，因此升级前不会捕捉到此错误，除非专门针对 SQL Server 2000 中的数据库执行 DBCC CHECKCATALOG。</span><span class="sxs-lookup"><span data-stu-id="40d45-122">In SQL Server 2000, DBCC CHECKDB did not include DBCC CHECKCATALOG functionality, so the error would not be caught before upgrade unless DBCC CHECKCATALOG was specifically executed against the database in SQL Server 2000.</span></span>  
  
 <span data-ttu-id="40d45-123">除错误 8992 外，还可能显示以下任一错误：</span><span class="sxs-lookup"><span data-stu-id="40d45-123">You may see any of the following errors in conjunction with error 8992:</span></span>  
  
 <span data-ttu-id="40d45-124">消息 3851 - 在系统表 sys.%ls%ls 中发现无效的行(%ls)。</span><span class="sxs-lookup"><span data-stu-id="40d45-124">Msg 3851 - An invalid row (%ls) was found in the system table sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="40d45-125">消息 3852 - sys.%ls%ls 中的行(%ls)在 sys.%ls%ls 中没有匹配的行(%ls)。</span><span class="sxs-lookup"><span data-stu-id="40d45-125">Msg 3852 - Row (%ls) in sys.%ls%ls does not have a matching row (%ls) in sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="40d45-126">3853 - sys.%ls%ls 中的行(%ls)的属性(%ls)在 sys.%ls%ls 中没有匹配的行(%ls)。</span><span class="sxs-lookup"><span data-stu-id="40d45-126">3853 - Attribute (%ls) of row (%ls) in sys.%ls%ls does not have a matching row (%ls) in sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="40d45-127">3854 - sys.%ls%ls 中的行(%ls)的属性(%ls)与 sys.%ls%ls 中的行(%ls)匹配，但该行无效。</span><span class="sxs-lookup"><span data-stu-id="40d45-127">3854 - Attribute (%ls) of row (%ls) in sys.%ls%ls has a matching row (%ls) in sys.%ls%ls that is invalid.</span></span>  
  
 <span data-ttu-id="40d45-128">3855 - 属性(%ls)存在，但 sys.%ls%ls 中没有行(%ls)。</span><span class="sxs-lookup"><span data-stu-id="40d45-128">3855 - Attribute (%ls) exists without a row (%ls) in sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="40d45-129">3856 - 属性(%ls)存在，但它与 sys.%ls%ls 中的行(%ls)不匹配。</span><span class="sxs-lookup"><span data-stu-id="40d45-129">3856 - Attribute (%ls) exists but should not for row (%ls) in sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="40d45-130">3857 - 缺少 sys.%ls%ls 中的行(%ls)所需的属性(%ls)。</span><span class="sxs-lookup"><span data-stu-id="40d45-130">3857 - The attribute (%ls) is required but is missing for row (%ls) in sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="40d45-131">3858 - sys.%ls%ls 中的行(%ls)的属性(%ls)具有无效的值。</span><span class="sxs-lookup"><span data-stu-id="40d45-131">3858 - The attribute (%ls) of row (%ls) in sys.%ls%ls has an invalid value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="40d45-132">用户操作</span><span class="sxs-lookup"><span data-stu-id="40d45-132">User Action</span></span>  
  
### <a name="drop-and-re-create-the-specified-object"></a><span data-ttu-id="40d45-133">删除并重新创建指定的对象</span><span class="sxs-lookup"><span data-stu-id="40d45-133">Drop and Re-create the Specified Object</span></span>  
 <span data-ttu-id="40d45-134">如果可能，请删除并重新创建指定的对象。</span><span class="sxs-lookup"><span data-stu-id="40d45-134">If possible, drop and recreate the specified object.</span></span> <span data-ttu-id="40d45-135">例如，如果该对象是一个存储过程或用户定义类型，则重新创建该对象将可能解决该问题。</span><span class="sxs-lookup"><span data-stu-id="40d45-135">For example, if the object is a stored procedure or user-defined type, recreating the object may resolve the problem.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="40d45-136">从备份还原</span><span class="sxs-lookup"><span data-stu-id="40d45-136">Restore from Backup</span></span>  
 <span data-ttu-id="40d45-137">如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="40d45-137">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span> <span data-ttu-id="40d45-138">只有备份中没有元数据错误时，此操作才适用。</span><span class="sxs-lookup"><span data-stu-id="40d45-138">This action is only applicable if the backup does not contain the metadata error.</span></span>  
  
### <a name="export-the-data-to-a-new-database"></a><span data-ttu-id="40d45-139">将数据导出到新数据库</span><span class="sxs-lookup"><span data-stu-id="40d45-139">Export the Data to a New Database</span></span>  
 <span data-ttu-id="40d45-140">如果备份还包含元数据不一致性，则您需要创建一个新的数据库，并将现有数据库的内容导出到这个新的数据库。</span><span class="sxs-lookup"><span data-stu-id="40d45-140">If the backup also contains the metadata inconsistency, you need to create a new database and export the contents of the existing database to the new database.</span></span>  
  
### <a name="dbcc-checkdb-cannot-repair-this-error"></a><span data-ttu-id="40d45-141">DBCC CHECKDB 无法修复此错误</span><span class="sxs-lookup"><span data-stu-id="40d45-141">DBCC CHECKDB Cannot Repair This Error</span></span>  
 <span data-ttu-id="40d45-142">无法修复此错误。</span><span class="sxs-lookup"><span data-stu-id="40d45-142">This error cannot be repaired.</span></span>  <span data-ttu-id="40d45-143">如果无法从备份还原数据库，请与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客户服务与支持部门 (CSS) 联系。</span><span class="sxs-lookup"><span data-stu-id="40d45-143">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
### <a name="do-not-manually-update-system-tables"></a><span data-ttu-id="40d45-144">不手动更新系统表</span><span class="sxs-lookup"><span data-stu-id="40d45-144">Do Not Manually Update System Tables</span></span>  
 <span data-ttu-id="40d45-145">不对系统表进行手动更新。</span><span class="sxs-lookup"><span data-stu-id="40d45-145">Do not make manual updates to system tables.</span></span> <span data-ttu-id="40d45-146">SQL Server 不支持对系统数据库进行任何手动更改。</span><span class="sxs-lookup"><span data-stu-id="40d45-146">SQL Server does not support any manual changes to system databases.</span></span> <span data-ttu-id="40d45-147">如果您更新 SQL Server 数据库中的系统表，则会记录两个事件（事件 ID 17659 和事件 ID 3859）。</span><span class="sxs-lookup"><span data-stu-id="40d45-147">If you update a system table in a SQL Server database, two events (event ID 17659 and event ID 3859) are logged.</span></span> <span data-ttu-id="40d45-148">有关详细信息，请参阅知识库文章 2688307：“当更新 SQL Server 数据库中的系统表时，将记录事件 ID 17659 和事件 ID 3859”。</span><span class="sxs-lookup"><span data-stu-id="40d45-148">For more information, see KB article 2688307, "Event ID 17659 and event ID 3859 are logged when you update system tables in a SQL Server database".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40d45-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="40d45-149">See Also</span></span>  
 [<span data-ttu-id="40d45-150">当更新 SQL Server 数据库中的系统表时，将记录事件 ID 17659 和事件 ID 3859</span><span class="sxs-lookup"><span data-stu-id="40d45-150">Event ID 17659 and event ID 3859 are logged when you update system tables in a SQL Server database</span></span>](https://support.microsoft.com/kb/2688307/EN-US)  
  
  
