---
title: "\"导入包\" 对话框 UI 参考 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.importpackage.f1
helpviewer_keywords:
- Import Package dialog box
ms.assetid: 0e5fb127-c7ff-4dfa-b90e-d9bcf0ce763b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ff20bf8eb221778465a26944280d53b6aab07601
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586893"
---
# <a name="import-package-dialog-box-ui-reference"></a><span data-ttu-id="7f5ca-102">“导入包”对话框 UI 参考</span><span class="sxs-lookup"><span data-stu-id="7f5ca-102">Import Package Dialog Box UI Reference</span></span>
  <span data-ttu-id="7f5ca-103">可以使用 **中的** “导入包” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]对话框，导入 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包以及设置或修改包的保护级别。</span><span class="sxs-lookup"><span data-stu-id="7f5ca-103">Use the **Import Package** dialog box, available in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], to import a [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package and to set or modify the protection level of the package.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7f5ca-104">选项</span><span class="sxs-lookup"><span data-stu-id="7f5ca-104">Options</span></span>  
 <span data-ttu-id="7f5ca-105">**包位置**</span><span class="sxs-lookup"><span data-stu-id="7f5ca-105">**Package location**</span></span>  
 <span data-ttu-id="7f5ca-106">选择要向其中导入包的存储位置的类型。</span><span class="sxs-lookup"><span data-stu-id="7f5ca-106">Select the type of storage location to import the package to.</span></span> <span data-ttu-id="7f5ca-107">提供了以下选项：</span><span class="sxs-lookup"><span data-stu-id="7f5ca-107">The following options are available:</span></span>  
  
 <span data-ttu-id="7f5ca-108">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="7f5ca-108">**SQL Server**</span></span>  
  
 <span data-ttu-id="7f5ca-109">**文件系统**</span><span class="sxs-lookup"><span data-stu-id="7f5ca-109">**File System**</span></span>  
  
 <span data-ttu-id="7f5ca-110">**SSIS 包存储区**</span><span class="sxs-lookup"><span data-stu-id="7f5ca-110">**SSIS Package Store**</span></span>  
  
 <span data-ttu-id="7f5ca-111">**Server**</span><span class="sxs-lookup"><span data-stu-id="7f5ca-111">**Server**</span></span>  
 <span data-ttu-id="7f5ca-112">键入服务器名称或从列表中选择一个服务器。</span><span class="sxs-lookup"><span data-stu-id="7f5ca-112">Type a server name or select a server from the list.</span></span>  
  
 <span data-ttu-id="7f5ca-113">**身份验证**</span><span class="sxs-lookup"><span data-stu-id="7f5ca-113">**Authentication**</span></span>  
 <span data-ttu-id="7f5ca-114">选择 Windows 身份验证或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证。</span><span class="sxs-lookup"><span data-stu-id="7f5ca-114">Select Windows Authentication or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="7f5ca-115">只有在存储位置为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="7f5ca-115">This option is available only if the storage location is [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7f5ca-116">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="7f5ca-116">Whenever possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="7f5ca-117">**身份验证类型**</span><span class="sxs-lookup"><span data-stu-id="7f5ca-117">**Authentication type**</span></span>  
 <span data-ttu-id="7f5ca-118">选择身份验证类型。</span><span class="sxs-lookup"><span data-stu-id="7f5ca-118">Select an authentication type.</span></span>  
  
 <span data-ttu-id="7f5ca-119">**用户名**</span><span class="sxs-lookup"><span data-stu-id="7f5ca-119">**User name**</span></span>  
 <span data-ttu-id="7f5ca-120">如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证，请提供用户名。</span><span class="sxs-lookup"><span data-stu-id="7f5ca-120">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name.</span></span>  
  
 <span data-ttu-id="7f5ca-121">**密码**</span><span class="sxs-lookup"><span data-stu-id="7f5ca-121">**Password**</span></span>  
 <span data-ttu-id="7f5ca-122">如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证，请提供密码。</span><span class="sxs-lookup"><span data-stu-id="7f5ca-122">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a password.</span></span>  
  
 <span data-ttu-id="7f5ca-123">**包路径**</span><span class="sxs-lookup"><span data-stu-id="7f5ca-123">**Package path**</span></span>  
 <span data-ttu-id="7f5ca-124">键入包的路径，或单击浏览按钮 (…) 并查找包  。</span><span class="sxs-lookup"><span data-stu-id="7f5ca-124">Type the package path, or click the browse button **(...)** and locate the package.</span></span>  
  
 <span data-ttu-id="7f5ca-125">**包名称**</span><span class="sxs-lookup"><span data-stu-id="7f5ca-125">**Package name**</span></span>  
 <span data-ttu-id="7f5ca-126">可以根据需要对包进行重命名。</span><span class="sxs-lookup"><span data-stu-id="7f5ca-126">Optionally, rename the package.</span></span> <span data-ttu-id="7f5ca-127">默认名称是要导入的包的名称。</span><span class="sxs-lookup"><span data-stu-id="7f5ca-127">The default name is the name of the package to import.</span></span>  
  
 <span data-ttu-id="7f5ca-128">**保护级别**</span><span class="sxs-lookup"><span data-stu-id="7f5ca-128">**Protection level**</span></span>  
 <span data-ttu-id="7f5ca-129">单击浏览按钮 (…)，然后在“包保护级别”对话框中更新保护级别   。</span><span class="sxs-lookup"><span data-stu-id="7f5ca-129">Click the browse button **(...)** and, in the **Package Protection Level** dialog box, update the protection level.</span></span> <span data-ttu-id="7f5ca-130">有关详细信息，请参阅 [“包和项目保护级别”对话框](../../2014/integration-services/package-and-project-protection-level-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="7f5ca-130">For more information, see [Package and Project Protection Level Dialog Box](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f5ca-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7f5ca-131">See Also</span></span>  
 <span data-ttu-id="7f5ca-132">[保存包的副本](../../2014/integration-services/save-copy-of-package.md) </span><span class="sxs-lookup"><span data-stu-id="7f5ca-132">[Save Copy of Package](../../2014/integration-services/save-copy-of-package.md) </span></span>  
 <span data-ttu-id="7f5ca-133">["导出包" 对话框 UI 参考](../../2014/integration-services/export-package-dialog-box-ui-reference.md) </span><span class="sxs-lookup"><span data-stu-id="7f5ca-133">[Export Package Dialog Box UI Reference](../../2014/integration-services/export-package-dialog-box-ui-reference.md) </span></span>  
 <span data-ttu-id="7f5ca-134">[保存包](save-packages.md) </span><span class="sxs-lookup"><span data-stu-id="7f5ca-134">[Save Packages](save-packages.md) </span></span>  
 [<span data-ttu-id="7f5ca-135">导入和导出包（SSIS 服务）</span><span class="sxs-lookup"><span data-stu-id="7f5ca-135">Import and Export Packages &#40;SSIS Service&#41;</span></span>](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
