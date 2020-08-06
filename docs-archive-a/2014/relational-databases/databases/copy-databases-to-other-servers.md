---
title: 将数据库复制到其他服务器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- servers [SQL Server], copying databases between
- bulk exporting [SQL Server], between servers
- database copying [SQL Server]
- migrating databases [SQL Server]
- moving databases
- copying databases
- bulk importing [SQL Server], between servers
ms.assetid: 978406d6-a3c8-4902-b1f4-4ced75234be5
author: stevestein
ms.author: sstein
ms.openlocfilehash: bcde6185f25129596b4be7a150d4ee230c54c1a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689434"
---
# <a name="copy-databases-to-other-servers"></a><span data-ttu-id="4394c-102">将数据库复制到其他服务器</span><span class="sxs-lookup"><span data-stu-id="4394c-102">Copy Databases to Other Servers</span></span>
  <span data-ttu-id="4394c-103">有时候将数据库从一台计算机复制到另一台计算机会很有用，无论是用于测试、检查一致性、开发软件、运行报表、创建镜像数据库还是将数据库用于远程分支操作。</span><span class="sxs-lookup"><span data-stu-id="4394c-103">It is sometimes useful to copy a database from one computer to another, whether for testing, checking consistency, developing software, running reports, creating a mirror database, or, possibly, to make the database available to remote-branch operations.</span></span>  
  
 <span data-ttu-id="4394c-104">有几种复制数据库的方法：</span><span class="sxs-lookup"><span data-stu-id="4394c-104">There are several ways to copy a database:</span></span>  
  
-   <span data-ttu-id="4394c-105">使用复制数据库向导</span><span class="sxs-lookup"><span data-stu-id="4394c-105">Using the Copy Database Wizard</span></span>  
  
     <span data-ttu-id="4394c-106">可以使用复制数据库向导在服务器之间复制或移动数据库，或者将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库升级到更高版本。</span><span class="sxs-lookup"><span data-stu-id="4394c-106">You can use the Copy Database Wizard to copy or move databases between servers or to upgrade a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database to a later version.</span></span> <span data-ttu-id="4394c-107">有关详细信息，请参阅 [Use the Copy Database Wizard](use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="4394c-107">For more information, see [Use the Copy Database Wizard](use-the-copy-database-wizard.md).</span></span>  
  
-   <span data-ttu-id="4394c-108">还原数据库备份</span><span class="sxs-lookup"><span data-stu-id="4394c-108">Restoring a database backup</span></span>  
  
     <span data-ttu-id="4394c-109">若要复制整个数据库，可以使用 BACKUP 和 RESTORE [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="4394c-109">To copy an entire database, you can use the BACKUP and RESTORE [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="4394c-110">通常，还原数据库的完整备份用于因各种原因将数据库从一台计算机复制到其他计算机。</span><span class="sxs-lookup"><span data-stu-id="4394c-110">Typically, restoring a full backup of a database is used to copy the database from one computer to another for a variety of reasons.</span></span> <span data-ttu-id="4394c-111">有关使用备份和还原复制数据库的信息，请参阅 [通过备份和还原复制数据库](copy-databases-with-backup-and-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="4394c-111">For information on using backup and restore to copy a database, see [Copy Databases with Backup and Restore](copy-databases-with-backup-and-restore.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4394c-112">若要为进行数据库镜像设置镜像数据库，则必须使用 RESTORE DATABASE *<database_name>* WITH NORECOVERY 将数据库还原到镜像服务器。</span><span class="sxs-lookup"><span data-stu-id="4394c-112">To set up a mirror database for database mirroring, you must restore the database onto the mirror server by using RESTORE DATABASE *<database_name>* WITH NORECOVERY.</span></span> <span data-ttu-id="4394c-113">有关详细信息，请参阅 [为镜像准备镜像数据库 (SQL Server)](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)的各版本中均未提供见证服务器实例。</span><span class="sxs-lookup"><span data-stu-id="4394c-113">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
-   <span data-ttu-id="4394c-114">使用生成脚本向导发布数据库</span><span class="sxs-lookup"><span data-stu-id="4394c-114">Using the Generate Scripts Wizard to publish databases</span></span>  
  
     <span data-ttu-id="4394c-115">可以使用生成脚本向导将数据库从本地计算机传输到 Web 宿主提供程序。</span><span class="sxs-lookup"><span data-stu-id="4394c-115">You can use the Generate Scripts Wizard to transfer a database from a local computer to a Web hosting provider.</span></span> <span data-ttu-id="4394c-116">有关详细信息，请参阅 [生成和发布脚本向导](../scripting/generate-and-publish-scripts-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="4394c-116">For more information, see [Generate and Publish Scripts Wizard](../scripting/generate-and-publish-scripts-wizard.md).</span></span>  
  
  
