---
title: 保存 SSIS 包（SQL Server 导入和导出向导）| Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.savedtspackage.f1
ms.assetid: 7bf8ac6a-5599-43ab-bf5c-e072c11b85a0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d4e582558a1f86b18d935fcc6235ba5839faa031
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588618"
---
# <a name="save-ssis-package-sql-server-import-and-export-wizard"></a><span data-ttu-id="86240-102">保存 SSIS 包（SQL Server 导入和导出向导）</span><span class="sxs-lookup"><span data-stu-id="86240-102">Save SSIS Package (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="86240-103">使用 "**保存 SSIS 包**" 页可以将 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Integration Services () 包的名称、说明和保存到数据库中，也可以保存 [!INCLUDE[ssIS](../../includes/ssis-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` 到扩展名为 .dtsx 的文件中。</span><span class="sxs-lookup"><span data-stu-id="86240-103">Use the **Save SSIS Package** page to name, describe, and save a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Integration Services ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) package to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` database or to a file that has the .dtsx extension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="86240-104">在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 中，未提供用来保存该向导所创建的包的选项。</span><span class="sxs-lookup"><span data-stu-id="86240-104">In [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], the option to save the package created by the wizard is not available.</span></span>  
  
 <span data-ttu-id="86240-105">若要了解有关此向导的详细信息，请参阅[SQL Server 导入和导出向导](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="86240-105">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="86240-106">若要了解启动向导的选项以及成功运行向导所需的权限，请参阅[运行 SQL Server 导入和导出向导](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="86240-106">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="86240-107">SQL Server 导入和导出向导的作用是将数据从源复制到目标。</span><span class="sxs-lookup"><span data-stu-id="86240-107">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="86240-108">该向导还可以为您创建目标数据库和目标表。</span><span class="sxs-lookup"><span data-stu-id="86240-108">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="86240-109">但是，如果必须复制多个数据库或表，或者必须复制其他类型的数据库对象，则应改用复制数据库向导。</span><span class="sxs-lookup"><span data-stu-id="86240-109">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="86240-110">有关详细信息，请参阅 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="86240-110">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="86240-111">静态选项</span><span class="sxs-lookup"><span data-stu-id="86240-111">Static Options</span></span>  
 <span data-ttu-id="86240-112">**名称**</span><span class="sxs-lookup"><span data-stu-id="86240-112">**Name**</span></span>  
 <span data-ttu-id="86240-113">为包提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="86240-113">Provide a unique name for the package.</span></span>  
  
 <span data-ttu-id="86240-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="86240-114">**Description**</span></span>  
 <span data-ttu-id="86240-115">为包提供说明。</span><span class="sxs-lookup"><span data-stu-id="86240-115">Provide a description for the package.</span></span> <span data-ttu-id="86240-116">最好按照包的用途对其进行说明，使其一目了然，便于维护。</span><span class="sxs-lookup"><span data-stu-id="86240-116">As a best practice, describe the package in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="86240-117">**Target**</span><span class="sxs-lookup"><span data-stu-id="86240-117">**Target**</span></span>  
 <span data-ttu-id="86240-118">查看以前为目标文件指定的目标对象（[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或文件）</span><span class="sxs-lookup"><span data-stu-id="86240-118">View the target ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or file) that was previously specified for the destination file.</span></span>  
  
## <a name="target-dynamic-options"></a><span data-ttu-id="86240-119">目标动态选项</span><span class="sxs-lookup"><span data-stu-id="86240-119">Target Dynamic Options</span></span>  
  
### <a name="target--sql-server"></a><span data-ttu-id="86240-120">目标 = SQL Server</span><span class="sxs-lookup"><span data-stu-id="86240-120">Target = SQL Server</span></span>  
 <span data-ttu-id="86240-121">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="86240-121">**Server name**</span></span>  
 <span data-ttu-id="86240-122">在选择 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目标后，键入或选择目标服务器名称。</span><span class="sxs-lookup"><span data-stu-id="86240-122">When you have selected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, type or select the destination server name.</span></span>  
  
 <span data-ttu-id="86240-123">**Use Windows Authentication**</span><span class="sxs-lookup"><span data-stu-id="86240-123">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="86240-124">在选择 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目标后，指定是否使用 Windows 集成身份验证连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="86240-124">When you have selected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, specify whether to connect to the server by using Windows Integrated Authentication.</span></span> <span data-ttu-id="86240-125">这是首选的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="86240-125">This is the preferred authentication method.</span></span>  
  
 <span data-ttu-id="86240-126">**Use SQL Server Authentication**</span><span class="sxs-lookup"><span data-stu-id="86240-126">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="86240-127">在选择 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目标后，指定是否使用 SQL Server 身份验证连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="86240-127">When you have selected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, specify whether to connect to the server by using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="86240-128">**用户名**</span><span class="sxs-lookup"><span data-stu-id="86240-128">**User name**</span></span>  
 <span data-ttu-id="86240-129">在选择 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目标，并且指定 SQL Server 身份验证后，键入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户名。</span><span class="sxs-lookup"><span data-stu-id="86240-129">When you have selected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, and have specified SQL Server Authentication, type the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user name.</span></span>  
  
 <span data-ttu-id="86240-130">**密码**</span><span class="sxs-lookup"><span data-stu-id="86240-130">**Password**</span></span>  
 <span data-ttu-id="86240-131">在选择 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目标，并且指定 SQL Server 身份验证后，键入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 密码。</span><span class="sxs-lookup"><span data-stu-id="86240-131">When you have selected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, and have specified SQL Server Authentication, type the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] password.</span></span>  
  
### <a name="target--file-system"></a><span data-ttu-id="86240-132">目标 = 文件系统</span><span class="sxs-lookup"><span data-stu-id="86240-132">Target = File System</span></span>  
 <span data-ttu-id="86240-133">**文件名**</span><span class="sxs-lookup"><span data-stu-id="86240-133">**File name**</span></span>  
 <span data-ttu-id="86240-134">选择了文件目标后，请键入目标文件的路径，或使用 "**浏览**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="86240-134">When you have selected a file destination, type the path for the destination file, or use the **Browse** button.</span></span>  
  
 <span data-ttu-id="86240-135">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="86240-135">**Browse**</span></span>  
 <span data-ttu-id="86240-136">选择文件目标后，使用 "**保存包**" 对话框浏览到目标文件。</span><span class="sxs-lookup"><span data-stu-id="86240-136">When you have selected a file destination, browse to the destination file by using the **Save Package** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86240-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="86240-137">See Also</span></span>  
 [<span data-ttu-id="86240-138">保存包</span><span class="sxs-lookup"><span data-stu-id="86240-138">Save Packages</span></span>](../save-packages.md)  
  
  
