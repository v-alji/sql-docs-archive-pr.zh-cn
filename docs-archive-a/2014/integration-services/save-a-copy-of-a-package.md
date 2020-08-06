---
title: 保存包的副本 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, saving
- packages [Integration Services], saving
- saving packages
- SSIS packages, saving
- SQL Server Integration Services packages, saving
ms.assetid: 21482a20-e420-4452-b7eb-8f9fa1929f31
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 02ee2374fddb7dbb6b17adc2a4a10707179c882d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688990"
---
# <a name="save-a-copy-of-a-package"></a><span data-ttu-id="7c738-102">保存一个包副本 </span><span class="sxs-lookup"><span data-stu-id="7c738-102">Save a Copy of a Package</span></span>
  <span data-ttu-id="7c738-103">此过程介绍如何将包的副本保存到文件系统、包存储区或 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中的 **msdb** 数据库。</span><span class="sxs-lookup"><span data-stu-id="7c738-103">This procedure describes how to save a copy of a package to the file system, to the package store, or to the **msdb** database in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7c738-104">指定保存包副本的位置时，也能够更新包的名称。</span><span class="sxs-lookup"><span data-stu-id="7c738-104">When you specify a location to save the package copy, you can also update the name of the package.</span></span>  
  
 <span data-ttu-id="7c738-105">包存储区可以同时包括 **msdb** 数据库和文件系统中的文件夹，也可以只包含 **msdb**或文件系统中的文件夹。</span><span class="sxs-lookup"><span data-stu-id="7c738-105">The package store can include both the **msdb** database and the folders in the file system, only **msdb**, or only folders in the file system.</span></span> <span data-ttu-id="7c738-106">在 **msdb**中，包将保存到 **sysssispackages** 表中。</span><span class="sxs-lookup"><span data-stu-id="7c738-106">In **msdb**, packages are saved to the **sysssispackages** table.</span></span> <span data-ttu-id="7c738-107">此表包括一个 **folderid** 列，用于标识包所属的逻辑文件夹。</span><span class="sxs-lookup"><span data-stu-id="7c738-107">This table includes a **folderid** column that identifies the logical folder to which the package belongs.</span></span> <span data-ttu-id="7c738-108">逻辑文件夹提供了对保存到 **msdb** 中的包进行分组的有用方式，文件系统中的文件夹也提供了对保存到文件系统中的包进行分组的方式。</span><span class="sxs-lookup"><span data-stu-id="7c738-108">The logical folders provide a useful way to group packages saved to **msdb** in the same way that folders in the file system provide a way to group packages saved to the file system.</span></span> <span data-ttu-id="7c738-109">**msdb** 中的 **sysssispackagefolders** 表中的行定义这些文件夹。</span><span class="sxs-lookup"><span data-stu-id="7c738-109">Rows in the **sysssispackagefolders** table in **msdb** define the folders.</span></span>  
  
 <span data-ttu-id="7c738-110">在没有将 **msdb** 定义为包存储区的一部分的情况下，如果在 **“包路径”** 选项中选择 SQL Server，则可以继续使包与现有逻辑文件夹关联。</span><span class="sxs-lookup"><span data-stu-id="7c738-110">If **msdb** is not defined as part of the package store, you can continue to associate packages with existing logical folders when you select SQL Server in the **Package Path** option.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7c738-111">在保存包的副本之前，必须在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中打开包。</span><span class="sxs-lookup"><span data-stu-id="7c738-111">The package must be opened in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer before you can save a copy of the package.</span></span>  
  
### <a name="to-save-a-copy-of-a-package"></a><span data-ttu-id="7c738-112">保存包的副本</span><span class="sxs-lookup"><span data-stu-id="7c738-112">To save a copy of a package</span></span>  
  
1.  <span data-ttu-id="7c738-113">在解决方案资源管理器中，双击要保存其副本的包。</span><span class="sxs-lookup"><span data-stu-id="7c738-113">In Solution Explorer, double-click the package of which you want to save a copy.</span></span>  
  
2.  <span data-ttu-id="7c738-114">在“文件”菜单上，单击“将 \<package file> 的副本另存为” 。</span><span class="sxs-lookup"><span data-stu-id="7c738-114">On the **File** menu, click **Save Copy of \<package file> As**.</span></span>  
  
3.  <span data-ttu-id="7c738-115">在 **“保存包的副本”** 对话框，在 **“包位置”** 列表中选择包的位置。</span><span class="sxs-lookup"><span data-stu-id="7c738-115">In the **Save Copy of Package** dialog box, select a package location in the **Package location** list.</span></span>  
  
4.  <span data-ttu-id="7c738-116">如果位置为 **SQL Server** 或 **“SSIS 包存储区”** ，请提供服务器名称。</span><span class="sxs-lookup"><span data-stu-id="7c738-116">If the location is **SQL Server** or **SSIS Package Store**, provide a server name.</span></span>  
  
5.  <span data-ttu-id="7c738-117">如果保存到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，请指定身份验证类型；如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证，还请提供用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="7c738-117">If saving to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], specify the authentication type and, if using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name and password.</span></span>  
  
6.  <span data-ttu-id="7c738-118">若要指定包路径，请键入路径或单击浏览按钮 (…)，以指定包的位置  。</span><span class="sxs-lookup"><span data-stu-id="7c738-118">To specify the package path, either type the path or click the browse button **(...)** to specify the location of the package.</span></span> <span data-ttu-id="7c738-119">包的默认名称为 Package。</span><span class="sxs-lookup"><span data-stu-id="7c738-119">The default name of the package is Package.</span></span> <span data-ttu-id="7c738-120">也可以将包名称更新为所需的名称。</span><span class="sxs-lookup"><span data-stu-id="7c738-120">Optionally, update the package name to one that suits your needs.</span></span>  
  
     <span data-ttu-id="7c738-121">如果选择 **SQL Server** 作为 **“包路径”** 选项，则包路径由 **msdb** 中的逻辑文件夹和包名称构成。</span><span class="sxs-lookup"><span data-stu-id="7c738-121">If you select **SQL Server** as the **Package Path** option, the package path consists of logical folders in **msdb** and the package name.</span></span> <span data-ttu-id="7c738-122">例如，如果包 DownloadMonthlyData 与 MSDB 文件夹中的 Finance 文件夹（ **msdb**中的根逻辑文件夹的默认名称）相关联，则名为 DownloadMonthlyData 的包的包路径为 MSDB/Finance/DownloadMonthlyData</span><span class="sxs-lookup"><span data-stu-id="7c738-122">For example, if the package DownloadMonthlyData is associated with the Finance folder within the MSDB folder (the default name of the root logical folder in **msdb**), the package path for the package named DownloadMonthlyData is MSDB/Finance/DownloadMonthlyData</span></span>  
  
     <span data-ttu-id="7c738-123">如果选择 **“SSIS 包存储区”** 作为 **“包路径”** 选项，则包路径由 Integration Services 服务管理的文件夹构成。</span><span class="sxs-lookup"><span data-stu-id="7c738-123">If you select **SSIS Package Store** as the **Package Path** option, the package path consists of the folder that the Integration Services service manages.</span></span> <span data-ttu-id="7c738-124">例如，如果包 UpdateDeductions 位于该服务所管理的文件系统文件夹中的 HumanResources 文件夹内，则包路径为 /File System/HumanResources/UpdateDeductions；同样，如果包 PostResumes 与 MSDB 文件夹中的 HumanResources 文件夹关联，则包路径为 MSDB/HumanResources/PostResumes。</span><span class="sxs-lookup"><span data-stu-id="7c738-124">For example, if the package UpdateDeductions is located in the HumanResources folder within the file system folder that the service manages, the package path is /File System/HumanResources/UpdateDeductions; likewise, if the package PostResumes is associated with the HumanResources folder within the MSDB folder, the package path is MSDB/HumanResources/PostResumes.</span></span>  
  
     <span data-ttu-id="7c738-125">如果选择 **“文件系统”** 作为 **“包路径”** 选项，则包路径为文件系统中的位置和文件名。</span><span class="sxs-lookup"><span data-stu-id="7c738-125">If you select **File System** as the **Package Path** option, the package path is the location in the file system and the file name.</span></span> <span data-ttu-id="7c738-126">例如，如果包名称为 UpdateDemographics，则包路径为 C:\HumanResources\Quarterly\UpdateDemographics.dtsx。</span><span class="sxs-lookup"><span data-stu-id="7c738-126">For example, if the package name is UpdateDemographics the package path is C:\HumanResources\Quarterly\UpdateDemographics.dtsx.</span></span>  
  
7.  <span data-ttu-id="7c738-127">查看包保护级别。</span><span class="sxs-lookup"><span data-stu-id="7c738-127">Review the package protection level.</span></span>  
  
8.  <span data-ttu-id="7c738-128">还可以单击“保护级别”旁边的 (…) 浏览按钮，更改保护级别   。</span><span class="sxs-lookup"><span data-stu-id="7c738-128">Optionally, click the browse button **(...)** by the **Protection level** box to change the protection level.</span></span>  
  
    -   <span data-ttu-id="7c738-129">在 **“包保护级别”** 对话框中，选择不同的保护级别。</span><span class="sxs-lookup"><span data-stu-id="7c738-129">In the **Package Protection Level** dialog box, select a different protection level.</span></span>  
  
    -   <span data-ttu-id="7c738-130">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="7c738-130">Click **OK**.</span></span>  
  
9. <span data-ttu-id="7c738-131">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="7c738-131">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c738-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7c738-132">See Also</span></span>  
 <span data-ttu-id="7c738-133">[Integration Services &#40;SSIS&#41; 包](../../2014/integration-services/integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="7c738-133">[Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="7c738-134">配置 Integration Services 服务（SSIS 服务）</span><span class="sxs-lookup"><span data-stu-id="7c738-134">Configuring the Integration Services Service &#40;SSIS Service&#41;</span></span>](service/integration-services-service-ssis-service.md)  
  
  
