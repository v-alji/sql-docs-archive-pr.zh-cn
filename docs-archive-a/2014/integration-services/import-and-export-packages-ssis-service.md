---
title: 在 SSIS 服务)  (导入和导出包 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], importing
- packages [Integration Services], exporting
- importing packages
- exporting packages
ms.assetid: ef18ec11-b536-47d9-abd1-794099f43486
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b69f9d23431ed86f6b84be6857b7104cd8ba3dcc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588652"
---
# <a name="import-and-export-packages-ssis-service"></a><span data-ttu-id="bd7d2-102">导入和导出包（SSIS 服务）</span><span class="sxs-lookup"><span data-stu-id="bd7d2-102">Import and Export Packages (SSIS Service)</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="bd7d2-103">本主题论述 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务，该服务是用于管理 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包的一种 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="bd7d2-104">支持该服务以便与 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]的早期版本向后兼容。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="bd7d2-105">从 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]开始，您可以在 Integration Services 服务器上管理诸如包之类的对象。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="bd7d2-106">包既可以保存在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb 数据库的 sysssispackages 表中，也可以保存在文件系统中。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-106">Packages can be saved either in the sysssispackages table in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb database or in the file system.</span></span>  
  
 <span data-ttu-id="bd7d2-107">包存储区是 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务监视和管理的逻辑存储区，它包括在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务的配置文件中指定的 msdb 数据库和文件系统。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-107">The package store, which is the logical storage that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service monitors and manages, can include both the msdb database and the file system folders specified in the configuration file for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="bd7d2-108">您可以在下列存储类型之间导入和导出包：</span><span class="sxs-lookup"><span data-stu-id="bd7d2-108">You can import and export packages between the following storage types:</span></span>  
  
-   <span data-ttu-id="bd7d2-109">文件系统中任意位置的文件系统文件夹。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-109">File system folders anywhere in the file system.</span></span>  
  
-   <span data-ttu-id="bd7d2-110">SSIS 包存储区中的文件夹。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-110">Folders in the SSIS Package Store.</span></span> <span data-ttu-id="bd7d2-111">这两个默认文件夹分别称为“文件系统”和“MSDB”。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-111">The two default folders are named File System and MSDB.</span></span>  
  
-   <span data-ttu-id="bd7d2-112">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb 数据库。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-112">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb database.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="bd7d2-113">提供了导入和导出包的功能，通过此功能可以更改包的存储格式和位置。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-113">gives you the ability to import and export packages, and by doing this change the storage format and location of packages.</span></span> <span data-ttu-id="bd7d2-114">使用导入和导出功能，您可以将包添加到文件系统、包存储区或 msdb 数据库，然后将包从一种存储格式复制为另一种存储格式。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-114">Using the import and export features, you can add packages to the file system, package store, or msdb database, and copy packages from one storage format to another.</span></span> <span data-ttu-id="bd7d2-115">例如，保存在 msdb 中的包可以复制到文件系统中，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-115">For example, packages saved in msdb can be copied to the file system and vice versa.</span></span>  
  
 <span data-ttu-id="bd7d2-116">还可以使用 **dtutil** 命令提示实用工具 (dtutil.exe) 将包复制为其他格式。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-116">You can also copy a package to a different format using the **dtutil** command prompt utility (dtutil.exe).</span></span> <span data-ttu-id="bd7d2-117">有关详细信息，请参阅 [dtutil Utility](dtutil-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-117">For more information, see [dtutil Utility](dtutil-utility.md).</span></span>  
  
## <a name="to-import-or-export-a-package"></a><span data-ttu-id="bd7d2-118">导入或导出包</span><span class="sxs-lookup"><span data-stu-id="bd7d2-118">To import or export a package</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bd7d2-119">本主题讨论作为 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 的一部分的 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]服务。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-119">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service that is part of [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="bd7d2-120">支持 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务以便与 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]向后兼容。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-120">supports the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service for backward compatibility with [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span> <span data-ttu-id="bd7d2-121">有关在 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 中管理包的信息，请参阅 [Integration Services (SSIS) 服务器](catalog/integration-services-ssis-server-and-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-121">For information about managing packages in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], see [Integration Services &#40;SSIS&#41; Server](catalog/integration-services-ssis-server-and-catalog.md).</span></span>  
  
 <span data-ttu-id="bd7d2-122">您可以从以下位置导出 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包，或将包导入以下位置：</span><span class="sxs-lookup"><span data-stu-id="bd7d2-122">You can import or export an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package from or to the following locations:</span></span>  
  
-   <span data-ttu-id="bd7d2-123">可以导入存储在 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例、文件系统或 [!INCLUDE[ssIS](../includes/ssis-md.md)] 包存储区中的包。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-123">You can import a package that is stored in an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], in the file system, or in the [!INCLUDE[ssIS](../includes/ssis-md.md)] package store.</span></span> <span data-ttu-id="bd7d2-124">导入的包将保存至 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssIS](../includes/ssis-md.md)] 包存储区中的文件夹。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-124">The imported package is saved to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or to a folder in the [!INCLUDE[ssIS](../includes/ssis-md.md)] package store.</span></span>  
  
-   <span data-ttu-id="bd7d2-125">可以将存储在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例、文件系统或 [!INCLUDE[ssIS](../includes/ssis-md.md)] 包存储区中的包导出至不同的存储格式和位置。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-125">You can export a package that is stored in an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the file system, or the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Store to a different storage format and location.</span></span>  
  
 <span data-ttu-id="bd7d2-126">但对于在不同版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]之间导入和导出包，存在一些限制：</span><span class="sxs-lookup"><span data-stu-id="bd7d2-126">However, there are some restrictions on importing and exporting a package between different versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="bd7d2-127">对于 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]实例，可以从 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]实例导入包，但不能将包导出到 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-127">On an instance of [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], you can import packages from an instance of [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], but you cannot export packages to an instance of [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)].</span></span>  
  
-   <span data-ttu-id="bd7d2-128">对于 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]实例，不能从 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]实例导入包，也不能将包导出到该实例。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-128">On an instance of [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], you cannot import packages from, or export packages to, an instance of [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="bd7d2-129">下列过程说明如何使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 导入或导出包。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-129">The following procedures describe how to use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to import or export a package.</span></span>  
  
#### <a name="to-import-a-package-by-using-sql-server-management-studio"></a><span data-ttu-id="bd7d2-130">使用 SQL Server Management Studio 导入包</span><span class="sxs-lookup"><span data-stu-id="bd7d2-130">To import a package by Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="bd7d2-131">单击“开始”  ，指向 Microsoft  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，然后单击“SQL Server Management Studio”  。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-131">Click **Start**, point to **Microsoft** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="bd7d2-132">在 **“连接到服务器”** 对话框中，设置以下选项：</span><span class="sxs-lookup"><span data-stu-id="bd7d2-132">In the **Connect to Server** dialog box set the following options:</span></span>  
  
    -   <span data-ttu-id="bd7d2-133">在 **“服务器类型”** 框中，选择 **“Integration Services”** 。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-133">In the **Server type** box, select **Integration Services**.</span></span>  
  
    -   <span data-ttu-id="bd7d2-134">在“服务器名称”框中，提供服务器名称或单击 \<Browse for more...>，并找到要使用的服务器 。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-134">In the **Server name** box, provide a server name or click **\<Browse for more...>** and locate the server to use.</span></span>  
  
3.  <span data-ttu-id="bd7d2-135">如果对象资源管理器未打开，请在 **“视图”** 菜单上，单击 **“对象资源管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-135">If Object Explorer is not open, on the **View** menu, click **Object Explorer**.</span></span>  
  
4.  <span data-ttu-id="bd7d2-136">在对象资源管理器中，展开 **“已存储的包”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-136">In Object Explorer, expand the **Stored Packages** folder.</span></span>  
  
5.  <span data-ttu-id="bd7d2-137">展开子文件夹，找到要向其中导入包的文件夹。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-137">Expand the subfolders to locate the folder into which you want to import a package.</span></span>  
  
6.  <span data-ttu-id="bd7d2-138">右键单击该文件夹，单击“导入包”。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-138">Right-click the folder, click **Import Package**.</span></span> <span data-ttu-id="bd7d2-139">然后请执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="bd7d2-139">and then do one of the following:</span></span>  
  
    -   <span data-ttu-id="bd7d2-140">若要从 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的实例导入，请选择 **“SQL Server”** 选项，然后指定服务器并选择身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-140">To import from an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], select the **SQL Server** option, and then specify the server and select the authentication mode.</span></span> <span data-ttu-id="bd7d2-141">如果选择 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证，请提供用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-141">If you select [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name and a password.</span></span>  
  
         <span data-ttu-id="bd7d2-142">单击浏览按钮 (…)，选择要导入的包，再单击“确定”   。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-142">Click the browse button **(...)**, select the package to import, and then click **OK.**</span></span>  
  
    -   <span data-ttu-id="bd7d2-143">若要从文件系统导入，请选择 **“文件系统”** 选项。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-143">To import from the file system, select the **File system** option.</span></span>  
  
         <span data-ttu-id="bd7d2-144">单击浏览按钮 (…)，选择要导入的包，然后单击“打开”   。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-144">Click the browse button **(...)**, select the package to import, and then click **Open.**</span></span>  
  
    -   <span data-ttu-id="bd7d2-145">若要从 [!INCLUDE[ssIS](../includes/ssis-md.md)] 包存储区中导入，请选择 **“SSIS 包存储区”** 选项，并指定服务器。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-145">To import from the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Store, select the **SSIS Package Store** option and specify the server.</span></span>  
  
         <span data-ttu-id="bd7d2-146">单击浏览按钮 (…)，选择要导入的包，再单击“确定”   。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-146">Click the browse button **(...)**, select the package to import, and then click **OK.**</span></span>  
  
7.  <span data-ttu-id="bd7d2-147">根据需要，也可以更新包名称。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-147">Optionally, update the package name.</span></span>  
  
8.  <span data-ttu-id="bd7d2-148">若要更新包的保护级别，请单击浏览按钮 (…)，然后使用“包保护级别”对话框选择其他保护级别   。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-148">To update the protection level of the package, click the browse button **(...)** and choose a different protection level by using the **Package Protection Level** dialog box.</span></span> <span data-ttu-id="bd7d2-149">如果选定了 **“使用密码加密敏感数据”** 或 **“使用密码加密所有数据”** 选项，请键入并确认密码。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-149">If the **Encrypt sensitive data with password** or the **Encrypt all data with password** option is selected, type and confirm a password.</span></span>  
  
9. <span data-ttu-id="bd7d2-150">单击 **“确定”** ，完成导入操作。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-150">Click **OK** to complete the import.</span></span>  
  
#### <a name="to-export-a-package-by-using-sql-server-management-studio"></a><span data-ttu-id="bd7d2-151">使用 SQL Server Management Studio 导出包</span><span class="sxs-lookup"><span data-stu-id="bd7d2-151">To export a package by Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="bd7d2-152">单击“开始”  ，指向 Microsoft  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，然后单击“SQL Server Management Studio”  。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-152">Click **Start**, point to **Microsoft** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="bd7d2-153">在 **“连接到服务器”** 对话框中，设置下列选项：</span><span class="sxs-lookup"><span data-stu-id="bd7d2-153">In the **Connect to Server** dialog box, set the following options:</span></span>  
  
    -   <span data-ttu-id="bd7d2-154">在 **“服务器类型”** 框中，选择 **“Integration Services”** 。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-154">In the **Server type** box, select **Integration Services**.</span></span>  
  
    -   <span data-ttu-id="bd7d2-155">在“服务器名称”框中，提供服务器名称或单击 \<Browse for more...>，并找到要使用的服务器 。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-155">In the **Server name** box, provide a server name or click **\<Browse for more...>** and locate the server to use.</span></span>  
  
3.  <span data-ttu-id="bd7d2-156">如果对象资源管理器未打开，请在 **“视图”** 菜单上，单击 **“对象资源管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-156">If Object Explorer is not open, on the **View** menu, click **Object Explorer**.</span></span>  
  
4.  <span data-ttu-id="bd7d2-157">在对象资源管理器中，展开 **“已存储的包”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-157">In Object Explorer, expand the **Stored Packages** folder.</span></span>  
  
5.  <span data-ttu-id="bd7d2-158">展开子文件夹以找到要导出的包。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-158">Expand the subfolders to locate the package you want to export.</span></span>  
  
6.  <span data-ttu-id="bd7d2-159">右键单击该包，单击“导出”  ，然后执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="bd7d2-159">Right-click the package, click **Export**, and then do one of the following:</span></span>  
  
    -   <span data-ttu-id="bd7d2-160">若要导出到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的实例，请选择 **SQL Server** 选项，然后指定服务器并选择身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-160">To export to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], select the **SQL Server** option, and then specify the server and select the authentication mode.</span></span> <span data-ttu-id="bd7d2-161">如果选择 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证，请提供用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-161">If you select [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name and a password.</span></span>  
  
         <span data-ttu-id="bd7d2-162">单击浏览按钮 (…)，展开“SSIS 包”文件夹以找到要存储此包的文件夹   。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-162">Click the browse button **(...)**, and expand the **SSIS Packages** folder to locate the folder to which you want to save the package.</span></span> <span data-ttu-id="bd7d2-163">也可以更新此包的默认名称，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-163">Optionally, update the default name of the package, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="bd7d2-164">要导出到文件系统，请选择 **“文件系统”** 选项。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-164">To export to the file system, select the **File System** option.</span></span>  
  
         <span data-ttu-id="bd7d2-165">单击浏览按钮 (…) 以查找要向其中导出包的文件夹，键入包文件的名称，然后单击“保存”   。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-165">Click the browse button **(...)** to locate the folder to which you want to export the package, type the name of the package file, and then click **Save.**</span></span>  
  
    -   <span data-ttu-id="bd7d2-166">若要导出到 [!INCLUDE[ssIS](../includes/ssis-md.md)] 包存储区，请选择 **“SSIS 包存储区”** 选项并指定服务器。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-166">To export to the [!INCLUDE[ssIS](../includes/ssis-md.md)] package store, select the **SSIS Package Store** option, and specify the server.</span></span>  
  
         <span data-ttu-id="bd7d2-167">单击浏览按钮 (…)，展开“SSIS 包”文件夹，然后选择要存储此包的文件夹   。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-167">Click the browse button **(...)**, expand the **SSIS Packages** folder, and select the folder to which you want to save the package.</span></span> <span data-ttu-id="bd7d2-168">也可以在 **“包名称”** 文本框中为包键入新名称。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-168">Optionally, enter a new name for the package in the **Package Name** text box.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="bd7d2-169">若要更新包的保护级别，请单击浏览按钮 (…)，然后使用“包保护级别”对话框选择其他保护级别   。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-169">To update the protection level of the package, click the browse button **(...)** and choose a different protection level by using the **Package Protection Level** dialog box.</span></span> <span data-ttu-id="bd7d2-170">如果选定了 **“使用密码加密敏感数据”** 或 **“使用密码加密所有数据”** 选项，请键入并确认密码。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-170">If the **Encrypt sensitive data with password** or the **Encrypt all data with password** option is selected, type and confirm a password.</span></span>  
  
8.  <span data-ttu-id="bd7d2-171">单击 **“确定”** ，完成导出操作。</span><span class="sxs-lookup"><span data-stu-id="bd7d2-171">Click **OK** to complete the export.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd7d2-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bd7d2-172">See Also</span></span>  
 [<span data-ttu-id="bd7d2-173">包管理（SSIS 服务）</span><span class="sxs-lookup"><span data-stu-id="bd7d2-173">Package Management &#40;SSIS Service&#41;</span></span>](service/package-management-ssis-service.md)  
  
  
