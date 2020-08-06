---
title: 保存包 | Microsoft Docs
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
ms.assetid: 17c1de2c-637f-45c2-a148-79294bae0af4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 102e2c3eab001c230722bf3485d6ea9731aa99a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692450"
---
# <a name="save-packages"></a><span data-ttu-id="9bce0-102">保存包</span><span class="sxs-lookup"><span data-stu-id="9bce0-102">Save Packages</span></span>
  <span data-ttu-id="9bce0-103">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，通过使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器可以生成包，并将包作为 XML 文件（.dtsx 文件）保存到文件系统中。</span><span class="sxs-lookup"><span data-stu-id="9bce0-103">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] you build packages by using [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer and save the packages to the file system as XML files (.dtsx files).</span></span> <span data-ttu-id="9bce0-104">还可以将包 XML 文件的副本保存到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中的 msdb 数据库，或保存到包存储区。</span><span class="sxs-lookup"><span data-stu-id="9bce0-104">You can also save copies of the package XML file to the msdb database in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or to the package store.</span></span> <span data-ttu-id="9bce0-105">包存储区表示 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务管理的文件系统位置中的文件夹。</span><span class="sxs-lookup"><span data-stu-id="9bce0-105">The package store represents the folders in the file system location that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service manages.</span></span>  
  
 <span data-ttu-id="9bce0-106">如果将包保存到文件系统，则稍后可以使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务将包导入到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 或包存储区。</span><span class="sxs-lookup"><span data-stu-id="9bce0-106">If you save a package to the file system, you can later use the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service to import the package to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or to the package store.</span></span> <span data-ttu-id="9bce0-107">有关详细信息，请参阅[导入和导出包（SSIS 服务）](../../2014/integration-services/import-and-export-packages-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="9bce0-107">For more information, see [Import and Export Packages &#40;SSIS Service&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md).</span></span>  
  
 <span data-ttu-id="9bce0-108">还可以使用命令提示实用工具 **dtutil**在文件系统和 msdb 之间复制包。</span><span class="sxs-lookup"><span data-stu-id="9bce0-108">You can also use a command prompt utility, **dtutil**, to copy a package between the file system and msdb.</span></span> <span data-ttu-id="9bce0-109">有关详细信息，请参阅 [dtutil Utility](dtutil-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="9bce0-109">For more information, see [dtutil Utility](dtutil-utility.md).</span></span>  
  
### <a name="to-save-a-package"></a><span data-ttu-id="9bce0-110">保存包</span><span class="sxs-lookup"><span data-stu-id="9bce0-110">To save a package</span></span>  
  
-   [<span data-ttu-id="9bce0-111">将包保存到文件系统</span><span class="sxs-lookup"><span data-stu-id="9bce0-111">Save a Package to the File System</span></span>](../../2014/integration-services/save-a-package-to-the-file-system.md)  
  
-   [<span data-ttu-id="9bce0-112">保存包的副本</span><span class="sxs-lookup"><span data-stu-id="9bce0-112">Save a Copy of a Package</span></span>](../../2014/integration-services/save-a-copy-of-a-package.md)  
  
  
