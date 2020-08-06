---
title: 添加现有包的副本 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.addcopyexistingpackage.f1
helpviewer_keywords:
- Add Copy of Existing Package dialog box
ms.assetid: ed530b0d-438d-4c93-8e91-13f2b2b6a8b2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d535e24fbd13e62cecdb9970a8b9b576b00ddb03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585953"
---
# <a name="add-copy-of-existing-package"></a><span data-ttu-id="86d3b-102">添加现有包的副本</span><span class="sxs-lookup"><span data-stu-id="86d3b-102">Add Copy of Existing Package</span></span>
  <span data-ttu-id="86d3b-103">可以使用 **“添加现有包的副本”** 对话框，将 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、文件系统或 SSIS 包存储区中存储的包副本添加到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目中。</span><span class="sxs-lookup"><span data-stu-id="86d3b-103">Use the **Add Copy of Existing Package** dialog box to add a copy of a package stored in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the file system, or the SSIS Package Store to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
## <a name="options"></a><span data-ttu-id="86d3b-104">选项</span><span class="sxs-lookup"><span data-stu-id="86d3b-104">Options</span></span>  
 <span data-ttu-id="86d3b-105">**包位置**</span><span class="sxs-lookup"><span data-stu-id="86d3b-105">**Package location**</span></span>  
 <span data-ttu-id="86d3b-106">选择要从中复制包的存储位置的类型。</span><span class="sxs-lookup"><span data-stu-id="86d3b-106">Select the type of storage location from which to copy the package.</span></span>  
  
 <span data-ttu-id="86d3b-107">**Server**</span><span class="sxs-lookup"><span data-stu-id="86d3b-107">**Server**</span></span>  
 <span data-ttu-id="86d3b-108">如果从 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 或 SSIS 包存储区中复制，请键入服务器名称或从列表中选择服务器。</span><span class="sxs-lookup"><span data-stu-id="86d3b-108">If copying from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or the SSIS Package Store, type a server name or select a server from the list.</span></span>  
  
 <span data-ttu-id="86d3b-109">**身份验证类型**</span><span class="sxs-lookup"><span data-stu-id="86d3b-109">**Authentication type**</span></span>  
 <span data-ttu-id="86d3b-110">如果从 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中复制，请选择一种身份验证类型。</span><span class="sxs-lookup"><span data-stu-id="86d3b-110">If copying from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], select an authentication type.</span></span>  
  
 <span data-ttu-id="86d3b-111">**用户名**</span><span class="sxs-lookup"><span data-stu-id="86d3b-111">**User name**</span></span>  
 <span data-ttu-id="86d3b-112">如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证，请提供用户名。</span><span class="sxs-lookup"><span data-stu-id="86d3b-112">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name.</span></span>  
  
 <span data-ttu-id="86d3b-113">**密码**</span><span class="sxs-lookup"><span data-stu-id="86d3b-113">**Password**</span></span>  
 <span data-ttu-id="86d3b-114">如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证，请提供密码。</span><span class="sxs-lookup"><span data-stu-id="86d3b-114">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a password.</span></span>  
  
 <span data-ttu-id="86d3b-115">**包路径**</span><span class="sxs-lookup"><span data-stu-id="86d3b-115">**Package path**</span></span>  
 <span data-ttu-id="86d3b-116">键入包的路径，或单击浏览按钮 (…) 并查找要复制的包  。</span><span class="sxs-lookup"><span data-stu-id="86d3b-116">Type the package path, or click the browse button **(...)** and locate the package to copy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d3b-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="86d3b-117">See Also</span></span>  
 <span data-ttu-id="86d3b-118">[保存包的副本](../../2014/integration-services/save-copy-of-package.md) </span><span class="sxs-lookup"><span data-stu-id="86d3b-118">[Save Copy of Package](../../2014/integration-services/save-copy-of-package.md) </span></span>  
 <span data-ttu-id="86d3b-119">["导入包" 对话框 UI 参考](../../2014/integration-services/import-package-dialog-box-ui-reference.md) </span><span class="sxs-lookup"><span data-stu-id="86d3b-119">[Import Package Dialog Box UI Reference](../../2014/integration-services/import-package-dialog-box-ui-reference.md) </span></span>  
 <span data-ttu-id="86d3b-120">["导出包" 对话框 UI 参考](../../2014/integration-services/export-package-dialog-box-ui-reference.md) </span><span class="sxs-lookup"><span data-stu-id="86d3b-120">[Export Package Dialog Box UI Reference](../../2014/integration-services/export-package-dialog-box-ui-reference.md) </span></span>  
 <span data-ttu-id="86d3b-121">[保存包](save-packages.md) </span><span class="sxs-lookup"><span data-stu-id="86d3b-121">[Save Packages](save-packages.md) </span></span>  
 [<span data-ttu-id="86d3b-122">导入和导出包（SSIS 服务）</span><span class="sxs-lookup"><span data-stu-id="86d3b-122">Import and Export Packages &#40;SSIS Service&#41;</span></span>](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
