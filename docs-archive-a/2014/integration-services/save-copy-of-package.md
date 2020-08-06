---
title: 保存包的副本 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.savecopyas.f1
helpviewer_keywords:
- Save Copy of Package dialog box
ms.assetid: 7b44c0d7-d8fa-4491-8836-0899f621d3a8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f0a685d8b38299e1ba1d03c4ec8c1052cc957dbb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692451"
---
# <a name="save-copy-of-package"></a><span data-ttu-id="5d478-102">保存包的副本</span><span class="sxs-lookup"><span data-stu-id="5d478-102">Save Copy of Package</span></span>
  <span data-ttu-id="5d478-103">可以使用 **中的** “保存包的副本” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]对话框，将 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包的副本从 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 保存到其他位置，并根据需要修改包的保护级别。</span><span class="sxs-lookup"><span data-stu-id="5d478-103">Use the **Save Copy of Package** dialog box, available in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], to save a copy of an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package from [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to a different location and, optionally, modify the protection level of the package.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5d478-104">选项</span><span class="sxs-lookup"><span data-stu-id="5d478-104">Options</span></span>  
 <span data-ttu-id="5d478-105">**包位置**</span><span class="sxs-lookup"><span data-stu-id="5d478-105">**Package location**</span></span>  
 <span data-ttu-id="5d478-106">选择要在其中保存包副本的存储位置的类型。</span><span class="sxs-lookup"><span data-stu-id="5d478-106">Select the type of storage location in which to save the package copy.</span></span> <span data-ttu-id="5d478-107">提供了以下选项：</span><span class="sxs-lookup"><span data-stu-id="5d478-107">The following options are available:</span></span>  
  
 <span data-ttu-id="5d478-108">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="5d478-108">**SQL Server**</span></span>  
  
 <span data-ttu-id="5d478-109">**文件系统**</span><span class="sxs-lookup"><span data-stu-id="5d478-109">**File System**</span></span>  
  
 <span data-ttu-id="5d478-110">**SSIS 包存储区**</span><span class="sxs-lookup"><span data-stu-id="5d478-110">**SSIS Package Store**</span></span>  
  
 <span data-ttu-id="5d478-111">**Server**</span><span class="sxs-lookup"><span data-stu-id="5d478-111">**Server**</span></span>  
 <span data-ttu-id="5d478-112">键入服务器名称或从列表中选择一个服务器。</span><span class="sxs-lookup"><span data-stu-id="5d478-112">Type a server name or select a server from the list.</span></span> <span data-ttu-id="5d478-113">只有当存储位置为 **SQL Server** 或 **“SSIS 包存储区”** 时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="5d478-113">This option is available only if the storage location is **SQL Server** or **SSIS Package Store**.</span></span>  
  
 <span data-ttu-id="5d478-114">**身份验证**</span><span class="sxs-lookup"><span data-stu-id="5d478-114">**Authentication**</span></span>  
 <span data-ttu-id="5d478-115">选择 Windows 身份验证或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证。</span><span class="sxs-lookup"><span data-stu-id="5d478-115">Select Windows Authentication or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="5d478-116">只有在存储位置为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="5d478-116">This option is available only if the storage location is [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5d478-117">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="5d478-117">Whenever possible use Windows Authentication.</span></span>  
  
 <span data-ttu-id="5d478-118">**身份验证类型**</span><span class="sxs-lookup"><span data-stu-id="5d478-118">**Authentication type**</span></span>  
 <span data-ttu-id="5d478-119">选择身份验证类型。</span><span class="sxs-lookup"><span data-stu-id="5d478-119">Select an authentication type.</span></span>  
  
 <span data-ttu-id="5d478-120">**用户名**</span><span class="sxs-lookup"><span data-stu-id="5d478-120">**User name**</span></span>  
 <span data-ttu-id="5d478-121">如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证，请提供用户名。</span><span class="sxs-lookup"><span data-stu-id="5d478-121">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name.</span></span>  
  
 <span data-ttu-id="5d478-122">**密码**</span><span class="sxs-lookup"><span data-stu-id="5d478-122">**Password**</span></span>  
 <span data-ttu-id="5d478-123">如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证，请提供密码。</span><span class="sxs-lookup"><span data-stu-id="5d478-123">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a password.</span></span>  
  
 <span data-ttu-id="5d478-124">**包路径**</span><span class="sxs-lookup"><span data-stu-id="5d478-124">**Package path**</span></span>  
 <span data-ttu-id="5d478-125">键入包路径，或单击 "浏览\*\* ( ) ...\*\* " 按钮，然后找到要在其中存储包的文件夹。</span><span class="sxs-lookup"><span data-stu-id="5d478-125">Type the package path, or click the browse **(...)** button and locate the folder in which to store the package.</span></span>  
  
 <span data-ttu-id="5d478-126">**保护级别**</span><span class="sxs-lookup"><span data-stu-id="5d478-126">**Protection level**</span></span>  
 <span data-ttu-id="5d478-127">单击 "浏览\*\* ( ) ...\*\* " 按钮，然后在 "**包保护级别**" 对话框中更新保护级别。</span><span class="sxs-lookup"><span data-stu-id="5d478-127">Click the browse **(...)** button and update the protection level in the **Package Protection Level** dialog box.</span></span> <span data-ttu-id="5d478-128">有关详细信息，请参阅 [“包和项目保护级别”对话框](../../2014/integration-services/package-and-project-protection-level-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="5d478-128">For more information, see [Package and Project Protection Level Dialog Box](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d478-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5d478-129">See Also</span></span>  
 <span data-ttu-id="5d478-130">["导入包" 对话框 UI 参考](../../2014/integration-services/import-package-dialog-box-ui-reference.md) </span><span class="sxs-lookup"><span data-stu-id="5d478-130">[Import Package Dialog Box UI Reference](../../2014/integration-services/import-package-dialog-box-ui-reference.md) </span></span>  
 <span data-ttu-id="5d478-131">["导出包" 对话框 UI 参考](../../2014/integration-services/export-package-dialog-box-ui-reference.md) </span><span class="sxs-lookup"><span data-stu-id="5d478-131">[Export Package Dialog Box UI Reference](../../2014/integration-services/export-package-dialog-box-ui-reference.md) </span></span>  
 <span data-ttu-id="5d478-132">[保存包](save-packages.md) </span><span class="sxs-lookup"><span data-stu-id="5d478-132">[Save Packages](save-packages.md) </span></span>  
 [<span data-ttu-id="5d478-133">导入和导出包（SSIS 服务）</span><span class="sxs-lookup"><span data-stu-id="5d478-133">Import and Export Packages &#40;SSIS Service&#41;</span></span>](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
