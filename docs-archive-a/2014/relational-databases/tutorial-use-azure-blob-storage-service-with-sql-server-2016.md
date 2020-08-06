---
title: 教程：在 Azure 存储服务中 SQL Server 数据文件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: e69be67d-da1c-41ae-8c9a-6b12c8c2fb61
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 21a0fc11706a0c5ee35cf71e1af69f2927adc9db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591203"
---
# <a name="tutorial-sql-server-data-files-in-azure-storage-service"></a><span data-ttu-id="67dea-102">教程：Azure 存储服务中的 SQL Server 数据文件</span><span class="sxs-lookup"><span data-stu-id="67dea-102">Tutorial: SQL Server Data Files in Azure Storage service</span></span>
  <span data-ttu-id="67dea-103">欢迎使用 Azure 存储服务中的 SQL Server 数据文件教程。</span><span class="sxs-lookup"><span data-stu-id="67dea-103">Welcome to the  SQL Server Data Files in Azure Storage Service tutorial.</span></span> <span data-ttu-id="67dea-104">本教程有助于了解如何将 SQL Server 数据文件直接存储在 Azure Blob 存储服务中。</span><span class="sxs-lookup"><span data-stu-id="67dea-104">This tutorial helps you understand how to store SQL Server data files in the Azure Blob storage service directly.</span></span>  
  
 <span data-ttu-id="67dea-105">Azure Blob 存储服务 SQL Server 集成支持是一种 SQL Server 2014 增强。</span><span class="sxs-lookup"><span data-stu-id="67dea-105">SQL Server integration support for the Azure Blob storage service is a SQL Server 2014 enhancement.</span></span> <span data-ttu-id="67dea-106">有关使用此功能的功能和优势的概述，请参阅[SQL Server Azure 中的数据文件](databases/sql-server-data-files-in-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="67dea-106">For an overview of the functionality and benefits of using this functionality, see [SQL Server Data Files in Azure](databases/sql-server-data-files-in-microsoft-azure.md).</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="67dea-107">学习内容</span><span class="sxs-lookup"><span data-stu-id="67dea-107">What you will learn</span></span>  
 <span data-ttu-id="67dea-108">本教程介绍了如何在 Azure 存储服务中将 SQL Server 的数据文件存储在多个课程中。</span><span class="sxs-lookup"><span data-stu-id="67dea-108">This tutorial shows you how to store SQL Server Data Files in Azure Storage service in multiple lessons.</span></span> <span data-ttu-id="67dea-109">每一课都以一个特定任务为重点。</span><span class="sxs-lookup"><span data-stu-id="67dea-109">Each lesson is focused on a specific task.</span></span> <span data-ttu-id="67dea-110">首先，你将学习如何在 Azure 中创建存储帐户和容器。</span><span class="sxs-lookup"><span data-stu-id="67dea-110">First, you will learn how to create a storage account and a container in Azure.</span></span> <span data-ttu-id="67dea-111">然后，你将了解如何创建 SQL Server 凭据，以便能够将 SQL Server 与 Azure 存储集成。</span><span class="sxs-lookup"><span data-stu-id="67dea-111">Then, you will learn how to create a SQL Server credential to be able to integrate SQL Server with Azure Storage.</span></span> <span data-ttu-id="67dea-112">然后，将直接在 Azure 存储中创建数据库。</span><span class="sxs-lookup"><span data-stu-id="67dea-112">Then, you will create a database in Azure Storage directly.</span></span> <span data-ttu-id="67dea-113">另外，此教程还将演示加密、迁移以及备份和还原方案。</span><span class="sxs-lookup"><span data-stu-id="67dea-113">In addition, the tutorial will demonstrate encryption, migration, and backup and restore scenarios.</span></span>  
  
 <span data-ttu-id="67dea-114">本教程分为 9 课：</span><span class="sxs-lookup"><span data-stu-id="67dea-114">This tutorial is divided into nine lessons:</span></span>  
  
 <span data-ttu-id="67dea-115">**[第 1 课：创建 Azure 存储帐户和容器](../tutorials/lesson-1-create-windows-azure-storage-account-and-container.md)**</span><span class="sxs-lookup"><span data-stu-id="67dea-115">**[Lesson 1: Create Azure Storage Account and Container](../tutorials/lesson-1-create-windows-azure-storage-account-and-container.md)**</span></span>  
 <span data-ttu-id="67dea-116">在本课程中，将创建 Azure 存储帐户和容器。</span><span class="sxs-lookup"><span data-stu-id="67dea-116">In this lesson, you create an Azure Storage account and a container.</span></span>  
  
 <span data-ttu-id="67dea-117">**[第2课。在容器上创建策略并生成共享访问签名 &#40;SAS&#41; 密钥](lesson-1-create-stored-access-policy-and-shared-access-signature.md)**</span><span class="sxs-lookup"><span data-stu-id="67dea-117">**[Lesson 2. Create a policy on container and generate a Shared Access Signature &#40;SAS&#41; key](lesson-1-create-stored-access-policy-and-shared-access-signature.md)**</span></span>  
 <span data-ttu-id="67dea-118">在本课中，您将在 Blob 容器上创建策略并生成共享访问签名。</span><span class="sxs-lookup"><span data-stu-id="67dea-118">In this lesson, you create a policy on the Blob container and also generate a shared access signature.</span></span>  
  
 <span data-ttu-id="67dea-119">**[第 3 课：创建 SQL Server 凭据](lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)**</span><span class="sxs-lookup"><span data-stu-id="67dea-119">**[Lesson 3: Create a SQL Server Credential](lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)**</span></span>  
 <span data-ttu-id="67dea-120">在本课中，你将创建凭据，以存储用于访问 Azure 存储帐户的安全信息。</span><span class="sxs-lookup"><span data-stu-id="67dea-120">In this lesson, you create a Credential to store security information used to access the Azure storage account.</span></span>  
  
 <span data-ttu-id="67dea-121">**[第 4 课：在 Azure 存储中创建数据库](../relational-databases/lesson-3-database-backup-to-url.md)**</span><span class="sxs-lookup"><span data-stu-id="67dea-121">**[Lesson 4: Create a database in Azure Storage](../relational-databases/lesson-3-database-backup-to-url.md)**</span></span>  
 <span data-ttu-id="67dea-122">在本课程中，将使用 "创建数据库文件名" 选项在 Azure 存储中创建数据库。</span><span class="sxs-lookup"><span data-stu-id="67dea-122">In this lesson, you create a database in Azure Storage using CREATE Database FILENAME option.</span></span>  
  
 <span data-ttu-id="67dea-123">**[第5课。&#40;可选&#41; 使用 TDE 加密数据库](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)**</span><span class="sxs-lookup"><span data-stu-id="67dea-123">**[Lesson 5. &#40;Optional&#41; Encrypt your database using TDE](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)**</span></span>  
 <span data-ttu-id="67dea-124">在本课中，您将使用透明数据加密 (TDE) 和服务器证书对数据库进行加密。</span><span class="sxs-lookup"><span data-stu-id="67dea-124">In this lesson, you encrypt your database by using a transparent data encryption (TDE) and a server certificate.</span></span>  
  
 <span data-ttu-id="67dea-125">**[第 6 课：将数据库从本地源计算机迁移至 Azure 中的目标计算机](lesson-5-backup-database-using-file-snapshot-backup.md)**</span><span class="sxs-lookup"><span data-stu-id="67dea-125">**[Lesson 6: Migrate a database from a source machine on-premises to a destination machine in Azure](lesson-5-backup-database-using-file-snapshot-backup.md)**</span></span>  
 <span data-ttu-id="67dea-126">本课程介绍如何使用 CREATE DATABASE FOR ATTACH 将数据库从本地迁移到 Azure 中的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="67dea-126">In this lesson, you migrate a database from on-premises to a virtual machine in Azure using CREATE DATABASE FOR ATTACH option.</span></span>  
  
 <span data-ttu-id="67dea-127">**[第 7 课：将数据文件移动到 Azure 存储](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)**</span><span class="sxs-lookup"><span data-stu-id="67dea-127">**[Lesson 7: Move your data files to Azure Storage](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)**</span></span>  
 <span data-ttu-id="67dea-128">在本课中，将使用 ALTER DATABASE 语句将数据文件移到 Azure 存储。</span><span class="sxs-lookup"><span data-stu-id="67dea-128">In this lesson, you move your data files to Azure Storage using ALTER DATABASE statement.</span></span>  
  
 <span data-ttu-id="67dea-129">**[第8课。将数据库还原到 Azure 存储](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)**</span><span class="sxs-lookup"><span data-stu-id="67dea-129">**[Lesson 8. Restore a database to Azure Storage](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)**</span></span>  
 <span data-ttu-id="67dea-130">在本课中，您将使用 RESTORE Database MOVE 选项将数据库还原到 Azure 存储。</span><span class="sxs-lookup"><span data-stu-id="67dea-130">In this lesson, you restore a database to Azure Storage using RESTORE Database MOVE option.</span></span>  
  
 <span data-ttu-id="67dea-131">**[第9课：从 Azure 存储还原数据库](lesson-8-restore-as-new-database-from-log-backup.md)**</span><span class="sxs-lookup"><span data-stu-id="67dea-131">**[Lesson 9. Restore a database from Azure Storage](lesson-8-restore-as-new-database-from-log-backup.md)**</span></span>  
 <span data-ttu-id="67dea-132">在本课中，您将使用 RESTORE Database MOVE 选项从 Azure 存储还原数据库。</span><span class="sxs-lookup"><span data-stu-id="67dea-132">In this lesson, you restore a database from Azure Storage using RESTORE Database MOVE option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67dea-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67dea-133">See Also</span></span>  
 [<span data-ttu-id="67dea-134">Azure 中的 SQL Server 数据文件</span><span class="sxs-lookup"><span data-stu-id="67dea-134">SQL Server Data Files in Azure</span></span>](databases/sql-server-data-files-in-microsoft-azure.md)  
  
  
