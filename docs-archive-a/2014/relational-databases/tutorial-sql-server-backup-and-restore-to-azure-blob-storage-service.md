---
title: 教程：将 SQL Server 备份和还原到 Azure Blob 存储服务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
author: rothja
ms.author: jroth
ms.openlocfilehash: d15200968011cdb314829736512f39730782dc0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687743"
---
# <a name="tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service"></a><span data-ttu-id="b7aca-102">教程：将 SQL Server 备份和还原到 Azure Blob 存储服务</span><span class="sxs-lookup"><span data-stu-id="b7aca-102">Tutorial: SQL Server Backup and Restore to Azure Blob Storage Service</span></span>
  <span data-ttu-id="b7aca-103">欢迎使用使用 Azure Blob 存储服务进行备份和还原 SQL Server 教程的入门。</span><span class="sxs-lookup"><span data-stu-id="b7aca-103">Welcome to the Getting Started with SQL Server Backup and Restore with Azure Blob Storage Service tutorial.</span></span> <span data-ttu-id="b7aca-104">本教程将帮助您了解如何将备份写入 Azure Blob 存储服务以及如何从中还原。</span><span class="sxs-lookup"><span data-stu-id="b7aca-104">This tutorial helps you understand how to write backups to and restore from the Azure Blob storage service.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="b7aca-105">学习内容</span><span class="sxs-lookup"><span data-stu-id="b7aca-105">What You Will Learn</span></span>  
 <span data-ttu-id="b7aca-106">本教程演示如何创建 Windows 存储帐户和 Blob 容器、创建用于访问存储帐户的凭据、将备份写入 Blob 服务和执行简单还原。</span><span class="sxs-lookup"><span data-stu-id="b7aca-106">This tutorial shows you how to create a Windows Storage account, a blob container, creating credentials to access the storage account, writing a backup to the blob service, and performing a simple restore.</span></span> <span data-ttu-id="b7aca-107">本教程分为四课：</span><span class="sxs-lookup"><span data-stu-id="b7aca-107">This tutorial is divided into four lessons:</span></span>  
  
 [<span data-ttu-id="b7aca-108">第1课：创建 Azure 存储对象</span><span class="sxs-lookup"><span data-stu-id="b7aca-108">Lesson 1: Create Azure Storage Objects</span></span>](../tutorials/lesson-1-create-windows-azure-storage-objects.md)  
 <span data-ttu-id="b7aca-109">在本课中，你将创建 Azure 存储帐户和 Blob 容器。</span><span class="sxs-lookup"><span data-stu-id="b7aca-109">In this lesson, you create an Azure storage account and a blob container.</span></span>  
  
 [<span data-ttu-id="b7aca-110">第 2 课：创建 SQL Server 凭据</span><span class="sxs-lookup"><span data-stu-id="b7aca-110">Lesson 2: Create a SQL Server Credential</span></span>](../tutorials/lesson-2-create-a-sql-server-credential.md)  
 <span data-ttu-id="b7aca-111">在本课中，你将创建凭据，以存储用于访问 Azure 存储帐户的安全信息。</span><span class="sxs-lookup"><span data-stu-id="b7aca-111">In this lesson, you create a Credential to store security information used to access the Azure storage account.</span></span>  
  
 [<span data-ttu-id="b7aca-112">第 3 课：将完整数据库备份写入到 Azure Blob 存储服务</span><span class="sxs-lookup"><span data-stu-id="b7aca-112">Lesson 3: Write a Full Database Backup to the Azure Blob Storage Service</span></span>](../tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md)  
 <span data-ttu-id="b7aca-113">在本课中，你将发出一条 T-SQL 语句，用于将 AdventureWorks2012 数据库的备份写入到 Azure Blob 存储服务。</span><span class="sxs-lookup"><span data-stu-id="b7aca-113">In this lesson, you issue a T-SQL statement to write a backup of the AdventureWorks2012 database to the Azure Blob storage service.</span></span>  
  
 [<span data-ttu-id="b7aca-114">第 4 课：从完整数据库备份执行还原</span><span class="sxs-lookup"><span data-stu-id="b7aca-114">Lesson 4: Perform a Restore From a Full Database Backup</span></span>](../tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md)  
 <span data-ttu-id="b7aca-115">在本课中，您将发出一条 T-SQL 语句，用于从您在上一课中创建的数据库备份中进行还原。</span><span class="sxs-lookup"><span data-stu-id="b7aca-115">In this lesson, you issue a T-SQL statement to restore from the database backup you created in the previous lesson.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="b7aca-116">要求</span><span class="sxs-lookup"><span data-stu-id="b7aca-116">Requirements</span></span>  
 <span data-ttu-id="b7aca-117">若要完成本教程，你必须熟悉 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 备份和还原概念以及 T-SQL 语法。</span><span class="sxs-lookup"><span data-stu-id="b7aca-117">To complete this tutorial, you must be familiar with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backup and restore concepts and T-SQL syntax.</span></span> <span data-ttu-id="b7aca-118">若要使用本教程，您的系统必须满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="b7aca-118">To use this tutorial, your system must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="b7aca-119">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 的实例，以及安装了 AdventureWorks2012 数据库。</span><span class="sxs-lookup"><span data-stu-id="b7aca-119">An instance of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], and AdventureWorks2012 database installed.</span></span>  
  
     <span data-ttu-id="b7aca-120">SQL Server 实例可以在本地，也可以在 Azure 虚拟机中。</span><span class="sxs-lookup"><span data-stu-id="b7aca-120">The SQL Server instance can be on-premises or in an Azure Virtual Machine.</span></span>  
  
     <span data-ttu-id="b7aca-121">可以使用用户数据库代替 AdventureWorks2012，并相应地修改 tsql 语法。</span><span class="sxs-lookup"><span data-stu-id="b7aca-121">You can use a user database in place of AdventureWorks2012, and modify the tsql syntax accordingly.</span></span>  
  
-   <span data-ttu-id="b7aca-122">用于发出 BACKUP 或 RESTORE 命令的用户帐户应属于具有“更改任意凭据”权限的 **db_backup 操作员**数据库角色。</span><span class="sxs-lookup"><span data-stu-id="b7aca-122">The user account that is used to issue BACKUP or RESTORE commands should be in the **db_backup operator** database role with **Alter any credential** permissions.</span></span>  
  
### <a name="additional-reading"></a><span data-ttu-id="b7aca-123">附加阅读材料</span><span class="sxs-lookup"><span data-stu-id="b7aca-123">Additional Reading</span></span>  
 <span data-ttu-id="b7aca-124">以下是一些建议阅读的主题，便于了解概念以及在将 Azure Blob 存储服务用于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 备份时的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="b7aca-124">Following are some recommended reading to understand the concepts, best practices when using Azure Blob storage service for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backups.</span></span>  
  
1.  [<span data-ttu-id="b7aca-125">使用 Azure Blob 存储服务进行 SQL Server 备份和还原</span><span class="sxs-lookup"><span data-stu-id="b7aca-125">SQL Server Backup and Restore with Azure Blob Storage Service</span></span>](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
2.  [<span data-ttu-id="b7aca-126">从 SQL Server 备份到 URL 的最佳做法和故障排除</span><span class="sxs-lookup"><span data-stu-id="b7aca-126">SQL Server Backup to URL Best Practices and Troubleshooting</span></span>](backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
  
