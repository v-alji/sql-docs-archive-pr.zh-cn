---
title: SQL Server 导入和导出向导) 保存并执行包 (|Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.saveschedule.f1
ms.assetid: b582c462-3d7a-4a4c-a2a2-2c79fedab75a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a23f69bf66ca3355f1e1c62cc42d51e4aea3da5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588622"
---
# <a name="save-and-execute-package-sql-server-import-and-export-wizard"></a><span data-ttu-id="a1e1c-102">保存并执行包（SQL Server 导入和导出向导）</span><span class="sxs-lookup"><span data-stu-id="a1e1c-102">Save and Execute Package (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="a1e1c-103">使用 "**保存并执行包**" 对话框可以立即运行包，将其保存到稍后运行。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-103">Use the **Save and Execute Package** dialog box to run the package immediately, save it to run later, or both.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1e1c-104"> 如果在包完成运行前停止包，即使选中了 **“保存”** 复选框，也不会保存该包。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-104">If you stop a package before it finishes running, the package is not saved, even if you selected the **Save** check box.</span></span>  
  
 <span data-ttu-id="a1e1c-105">若要了解有关此向导的详细信息，请参阅[SQL Server 导入和导出向导](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-105">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="a1e1c-106">若要了解用于启动向导的选项以及成功运行向导所需的权限，请参阅[运行 SQL Server 导入和导出向导](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-106">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="a1e1c-107">SQL Server 导入和导出向导的作用是将数据从源复制到目标。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-107">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="a1e1c-108">该向导还可以为您创建目标数据库和目标表。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-108">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="a1e1c-109">但是，如果必须复制多个数据库或表，或者必须复制其他类型的数据库对象，则应改用复制数据库向导。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-109">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="a1e1c-110">有关详细信息，请参阅 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-110">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a1e1c-111">选项</span><span class="sxs-lookup"><span data-stu-id="a1e1c-111">Options</span></span>  
 <span data-ttu-id="a1e1c-112">**立即执行**</span><span class="sxs-lookup"><span data-stu-id="a1e1c-112">**Execute immediately**</span></span>  
 <span data-ttu-id="a1e1c-113">选择此选项将立即运行包。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-113">Select this option to run the package immediately.</span></span>  
  
 <span data-ttu-id="a1e1c-114">**保存 SSIS 包**</span><span class="sxs-lookup"><span data-stu-id="a1e1c-114">**Save SSIS Package**</span></span>  
 <span data-ttu-id="a1e1c-115">保存包以便日后运行，也可以根据需要立即运行包。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-115">Save the package to run later, with the option to run it immediately.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1e1c-116">在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 中，未提供用来保存该向导所创建的包的选项。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-116">In [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], the option to save the package created by the wizard is not available.</span></span>  
  
 <span data-ttu-id="a1e1c-117">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="a1e1c-117">**SQL Server**</span></span>  
 <span data-ttu-id="a1e1c-118">选择此选项可将包保存到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` 数据库。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-118">Select this option to save the package to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1e1c-119">仅当选择了 "**保存 SSIS 包**" 选项时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-119">This option is available only if you have selected the **Save SSIS Package** option.</span></span>  
  
 <span data-ttu-id="a1e1c-120">**文件系统**</span><span class="sxs-lookup"><span data-stu-id="a1e1c-120">**File system**</span></span>  
 <span data-ttu-id="a1e1c-121">选择此选项可以将包保存为扩展名为 .dtsx 的文件。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-121">Select this option to save the package as a file that has the .dtsx extension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1e1c-122">仅当选择了 "**保存 SSIS 包**" 选项时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-122">This option is available only if you have selected the **Save SSIS Package** option.</span></span>  
  
 <span data-ttu-id="a1e1c-123">**“包保护级别”**</span><span class="sxs-lookup"><span data-stu-id="a1e1c-123">**Package protection level**</span></span>  
 <span data-ttu-id="a1e1c-124">从列表中选择保护级别。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-124">Select a protection level from the list.</span></span>  
  
 <span data-ttu-id="a1e1c-125">保护级别决定保护包时所使用的方法、密码或用户密钥以及作用域。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-125">The protection level determines the protection method, the password or user key, and the scope of package protection.</span></span> <span data-ttu-id="a1e1c-126">可以保护所有数据，也可以只保护敏感数据。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-126">Protection can include all data or sensitive data only.</span></span> <span data-ttu-id="a1e1c-127">若要了解包安全性的要求和选项，请参阅[对包中敏感数据的访问控制](../security/access-control-for-sensitive-data-in-packages.md)和[安全概述 &#40;Integration Services&#41;](../security/security-overview-integration-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-127">To understand the requirements and options for package security, see [Access Control for Sensitive Data in Packages](../security/access-control-for-sensitive-data-in-packages.md) and [Security Overview &#40;Integration Services&#41;](../security/security-overview-integration-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1e1c-128">仅当选择了 "**保存 SSIS 包**" 选项时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-128">This option is available only if you have selected the **Save SSIS Package** option.</span></span>  
  
 <span data-ttu-id="a1e1c-129">**密码**</span><span class="sxs-lookup"><span data-stu-id="a1e1c-129">**Password**</span></span>  
 <span data-ttu-id="a1e1c-130">键入密码。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-130">Type a password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1e1c-131">仅当已将 "**包保护级别**" 选项设置为 "**使用密码加密敏感数据**" 或 "**使用密码加密所有数据**" 时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-131">This option is available only if you have set the **Package protection level** option to either **Encrypt sensitive data with password** or **Encrypt all data with password**.</span></span>  
  
 <span data-ttu-id="a1e1c-132">**重新键入密码**</span><span class="sxs-lookup"><span data-stu-id="a1e1c-132">**Retype password**</span></span>  
 <span data-ttu-id="a1e1c-133">再次键入该密码。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-133">Type the password again.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1e1c-134">仅当已将 "**包保护级别**" 选项设置为 "**使用密码加密敏感数据**" 或 "**使用密码加密所有数据**" 时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="a1e1c-134">This option is available only if you have set the **Package protection level** option to either **Encrypt sensitive data with password** or **Encrypt all data with password**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e1c-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a1e1c-135">See Also</span></span>  
 <span data-ttu-id="a1e1c-136">[项目和包的执行](../packages/run-integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="a1e1c-136">[Execution of Projects and Packages](../packages/run-integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="a1e1c-137">保存包</span><span class="sxs-lookup"><span data-stu-id="a1e1c-137">Save Packages</span></span>](../save-packages.md)  
  
  
