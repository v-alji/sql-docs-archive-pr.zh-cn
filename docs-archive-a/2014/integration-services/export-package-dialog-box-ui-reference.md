---
title: "\"导出包\" 对话框 UI 参考 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.exportpackage.f1
helpviewer_keywords:
- Export Package dialog box
ms.assetid: 3742fe8a-ef57-444d-b2fb-cb25d16bae97
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8aedb771dc61fca737ba3841e65b8cb8655d173e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694537"
---
# <a name="export-package-dialog-box-ui-reference"></a><span data-ttu-id="35f12-102">“导出包”对话框 UI 参考</span><span class="sxs-lookup"><span data-stu-id="35f12-102">Export Package Dialog Box UI Reference</span></span>
  <span data-ttu-id="35f12-103">可以使用 **中的** “导出包” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]对话框，将 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包导出到其他位置并根据需要修改包的保护级别。</span><span class="sxs-lookup"><span data-stu-id="35f12-103">Use the **Export Package** dialog box, available in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], to export a [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package to a different location and optionally, modify the protection level of the package.</span></span>  
  
## <a name="options"></a><span data-ttu-id="35f12-104">选项</span><span class="sxs-lookup"><span data-stu-id="35f12-104">Options</span></span>  
 <span data-ttu-id="35f12-105">**包位置**</span><span class="sxs-lookup"><span data-stu-id="35f12-105">**Package location**</span></span>  
 <span data-ttu-id="35f12-106">选择要将包导出到的存储区的类型。</span><span class="sxs-lookup"><span data-stu-id="35f12-106">Select the type of storage to export the package to.</span></span> <span data-ttu-id="35f12-107">提供了以下选项：</span><span class="sxs-lookup"><span data-stu-id="35f12-107">The following options are available:</span></span>  
  
 <span data-ttu-id="35f12-108">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="35f12-108">**SQL Server**</span></span>  
  
 <span data-ttu-id="35f12-109">**文件系统**</span><span class="sxs-lookup"><span data-stu-id="35f12-109">**File System**</span></span>  
  
 <span data-ttu-id="35f12-110">**SSIS 包存储**</span><span class="sxs-lookup"><span data-stu-id="35f12-110">**SSIS Package Storage**</span></span>  
  
 <span data-ttu-id="35f12-111">**Server**</span><span class="sxs-lookup"><span data-stu-id="35f12-111">**Server**</span></span>  
 <span data-ttu-id="35f12-112">键入服务器名称或从列表中选择一个服务器。</span><span class="sxs-lookup"><span data-stu-id="35f12-112">Type a server name or select a server from the list.</span></span>  
  
 <span data-ttu-id="35f12-113">**身份验证**</span><span class="sxs-lookup"><span data-stu-id="35f12-113">**Authentication**</span></span>  
 <span data-ttu-id="35f12-114">选择 Windows 身份验证或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证。</span><span class="sxs-lookup"><span data-stu-id="35f12-114">Select Windows Authentication or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="35f12-115">只有在存储位置为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="35f12-115">This option is available only if the storage location is [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="35f12-116">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="35f12-116">Whenever possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="35f12-117">**身份验证类型**</span><span class="sxs-lookup"><span data-stu-id="35f12-117">**Authentication type**</span></span>  
 <span data-ttu-id="35f12-118">选择身份验证类型。</span><span class="sxs-lookup"><span data-stu-id="35f12-118">Select an authentication type.</span></span>  
  
 <span data-ttu-id="35f12-119">**用户名**</span><span class="sxs-lookup"><span data-stu-id="35f12-119">**User name**</span></span>  
 <span data-ttu-id="35f12-120">如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证，请提供用户名。</span><span class="sxs-lookup"><span data-stu-id="35f12-120">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name.</span></span>  
  
 <span data-ttu-id="35f12-121">**密码**</span><span class="sxs-lookup"><span data-stu-id="35f12-121">**Password**</span></span>  
 <span data-ttu-id="35f12-122">如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证，请提供密码。</span><span class="sxs-lookup"><span data-stu-id="35f12-122">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a password.</span></span>  
  
 <span data-ttu-id="35f12-123">**包路径**</span><span class="sxs-lookup"><span data-stu-id="35f12-123">**Package path**</span></span>  
 <span data-ttu-id="35f12-124">键入包路径，或单击浏览按钮 (…)，然后定位存储包的文件夹  。</span><span class="sxs-lookup"><span data-stu-id="35f12-124">Type the package path, or click the browse button **(...)** and locate the folder in which to store the package.</span></span>  
  
 <span data-ttu-id="35f12-125">**保护级别**</span><span class="sxs-lookup"><span data-stu-id="35f12-125">**Protection level**</span></span>  
 <span data-ttu-id="35f12-126">单击浏览按钮 (…)，然后在“包保护级别”对话框中更新保护级别   。</span><span class="sxs-lookup"><span data-stu-id="35f12-126">Click the browse button **(...)** and update the protection level in the **Package Protection Level** dialog box.</span></span> <span data-ttu-id="35f12-127">有关详细信息，请参阅 [“包和项目保护级别”对话框](../../2014/integration-services/package-and-project-protection-level-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="35f12-127">For more information, see [Package and Project Protection Level Dialog Box](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35f12-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="35f12-128">See Also</span></span>  
 <span data-ttu-id="35f12-129">[保存包的副本](../../2014/integration-services/save-copy-of-package.md) </span><span class="sxs-lookup"><span data-stu-id="35f12-129">[Save Copy of Package](../../2014/integration-services/save-copy-of-package.md) </span></span>  
 <span data-ttu-id="35f12-130">["导入包" 对话框 UI 参考](../../2014/integration-services/import-package-dialog-box-ui-reference.md) </span><span class="sxs-lookup"><span data-stu-id="35f12-130">[Import Package Dialog Box UI Reference](../../2014/integration-services/import-package-dialog-box-ui-reference.md) </span></span>  
 <span data-ttu-id="35f12-131">[保存包](save-packages.md) </span><span class="sxs-lookup"><span data-stu-id="35f12-131">[Save Packages](save-packages.md) </span></span>  
 [<span data-ttu-id="35f12-132">导入和导出包（SSIS 服务）</span><span class="sxs-lookup"><span data-stu-id="35f12-132">Import and Export Packages &#40;SSIS Service&#41;</span></span>](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
