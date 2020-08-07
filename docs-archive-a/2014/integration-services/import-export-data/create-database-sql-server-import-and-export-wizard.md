---
title: 创建数据库（SQL Server 导入和导出向导）| Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.createdatabase.f1
ms.assetid: 56a8a79f-086c-4bdc-8888-0045bb4b0cbf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 617b3fe10a17ae2d8659b51e85cdb3fed4470506
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588635"
---
# <a name="create-database-sql-server-import-and-export-wizard"></a><span data-ttu-id="4556b-102">创建数据库（SQL Server 导入和导出向导）</span><span class="sxs-lookup"><span data-stu-id="4556b-102">Create Database (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="4556b-103">使用 "**创建数据库**" 页可以为目标文件定义一个新数据库。</span><span class="sxs-lookup"><span data-stu-id="4556b-103">Use the **Create Database** page to define a new database for a destination file.</span></span>  
  
 <span data-ttu-id="4556b-104">此页提供了一部分可用于创建新数据库的选项。</span><span class="sxs-lookup"><span data-stu-id="4556b-104">This page offers a subset of the available options for creating a new database.</span></span> <span data-ttu-id="4556b-105">若要查看所有选项，请使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4556b-105">To view all the options, use [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="4556b-106">若要了解有关此向导的详细信息，请参阅[SQL Server 导入和导出向导](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="4556b-106">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="4556b-107">若要了解启动向导的选项以及成功运行向导所需的权限，请参阅[运行 SQL Server 导入和导出向导](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="4556b-107">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="4556b-108">SQL Server 导入和导出向导的作用是将数据从源复制到目标。</span><span class="sxs-lookup"><span data-stu-id="4556b-108">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="4556b-109">该向导还可以为您创建目标数据库和目标表。</span><span class="sxs-lookup"><span data-stu-id="4556b-109">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="4556b-110">但是，如果必须复制多个数据库或表，或者必须复制其他类型的数据库对象，则应改用复制数据库向导。</span><span class="sxs-lookup"><span data-stu-id="4556b-110">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="4556b-111">有关详细信息，请参阅 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="4556b-111">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="4556b-112">选项</span><span class="sxs-lookup"><span data-stu-id="4556b-112">Options</span></span>  
 <span data-ttu-id="4556b-113">**名称**</span><span class="sxs-lookup"><span data-stu-id="4556b-113">**Name**</span></span>  
 <span data-ttu-id="4556b-114">为目标 SQL Server 数据库提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="4556b-114">Provide a unique name for the destination SQL Server database.</span></span> <span data-ttu-id="4556b-115">请确保对此数据库命名时遵循 SQL Server 约定。</span><span class="sxs-lookup"><span data-stu-id="4556b-115">Make sure that you follow SQL Server conventions when you name this database.</span></span>  
  
 <span data-ttu-id="4556b-116">**数据文件名**</span><span class="sxs-lookup"><span data-stu-id="4556b-116">**Data file name**</span></span>  
 <span data-ttu-id="4556b-117">查看数据文件的名称。</span><span class="sxs-lookup"><span data-stu-id="4556b-117">View the name of the data file.</span></span> <span data-ttu-id="4556b-118">它是由以前提供的数据库名称派生而来的。</span><span class="sxs-lookup"><span data-stu-id="4556b-118">This is derived from the database name you provided earlier.</span></span>  
  
 <span data-ttu-id="4556b-119">**日志文件名**</span><span class="sxs-lookup"><span data-stu-id="4556b-119">**Log file name**</span></span>  
 <span data-ttu-id="4556b-120">查看日志文件的名称。</span><span class="sxs-lookup"><span data-stu-id="4556b-120">View the name of the log file.</span></span> <span data-ttu-id="4556b-121">它是由以前提供的数据库名称派生而来的。</span><span class="sxs-lookup"><span data-stu-id="4556b-121">This is derived from the database name you provided earlier.</span></span>  
  
 <span data-ttu-id="4556b-122">**初始大小（数据文件）**</span><span class="sxs-lookup"><span data-stu-id="4556b-122">**Initial size (data file)**</span></span>  
 <span data-ttu-id="4556b-123">指定数据文件的初始大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="4556b-123">Specify the number of megabytes for the initial size of the data file.</span></span>  
  
 <span data-ttu-id="4556b-124">**不允许增长（数据文件）**</span><span class="sxs-lookup"><span data-stu-id="4556b-124">**No growth allowed (data file)**</span></span>  
 <span data-ttu-id="4556b-125">指示数据文件是否可以增长以超出指定的初始大小。</span><span class="sxs-lookup"><span data-stu-id="4556b-125">Indicate whether the data file can grow beyond the specified initial size.</span></span>  
  
 <span data-ttu-id="4556b-126">**增长百分比（数据文件）**</span><span class="sxs-lookup"><span data-stu-id="4556b-126">**Grow by percentage (data file)**</span></span>  
 <span data-ttu-id="4556b-127">指定数据文件可以增长的百分比。</span><span class="sxs-lookup"><span data-stu-id="4556b-127">Specify a percentage by which the data file can grow.</span></span>  
  
 <span data-ttu-id="4556b-128">**增长规模（数据文件）**</span><span class="sxs-lookup"><span data-stu-id="4556b-128">**Grow by size (data file)**</span></span>  
 <span data-ttu-id="4556b-129">指定数据文件可以增长的大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="4556b-129">Specify a number of megabytes by which the data file can grow.</span></span>  
  
 <span data-ttu-id="4556b-130">**初始大小（日志文件）**</span><span class="sxs-lookup"><span data-stu-id="4556b-130">**Initial size (log file)**</span></span>  
 <span data-ttu-id="4556b-131">指定日志文件的初始大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="4556b-131">Specify the number of megabytes for the initial size of the log file.</span></span>  
  
 <span data-ttu-id="4556b-132">**不允许增长（日志文件）**</span><span class="sxs-lookup"><span data-stu-id="4556b-132">**No growth allowed (log file)**</span></span>  
 <span data-ttu-id="4556b-133">指示日志文件是否可以增长以超出指定的初始大小。</span><span class="sxs-lookup"><span data-stu-id="4556b-133">Indicate whether the log file can grow beyond the specified initial size.</span></span>  
  
 <span data-ttu-id="4556b-134">**增长百分比（日志文件）**</span><span class="sxs-lookup"><span data-stu-id="4556b-134">**Grow by percentage (log file)**</span></span>  
 <span data-ttu-id="4556b-135">指定日志文件可以增长的百分比。</span><span class="sxs-lookup"><span data-stu-id="4556b-135">Specify a percentage by which the log file can grow.</span></span>  
  
 <span data-ttu-id="4556b-136">**增长规模（日志文件）**</span><span class="sxs-lookup"><span data-stu-id="4556b-136">**Grow by size (log file)**</span></span>  
 <span data-ttu-id="4556b-137">指定日志文件可以增长的大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="4556b-137">Specify a number of megabytes by which the log file can grow.</span></span>  
  
  
