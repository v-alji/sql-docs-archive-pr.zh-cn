---
title: 在 SQL Server Data Tools 中复制包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], copying
- copying packages
- regenerating package GUID
- updating package properties
ms.assetid: 03edc659-e76d-48c0-a749-5f1899b6b507
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bd6ed4dd66ee4755181f5df6f3c1b5466b3f26b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587536"
---
# <a name="copy-a-package-in-sql-server-data-tools"></a><span data-ttu-id="534f5-102">在 SQL Server Data Tools 中复制包</span><span class="sxs-lookup"><span data-stu-id="534f5-102">Copy a Package in SQL Server Data Tools</span></span>
  <span data-ttu-id="534f5-103">此主题介绍如何通过复制现有包来创建新的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包，以及如何更新新包的 `Name` 和 `GUID` 属性。</span><span class="sxs-lookup"><span data-stu-id="534f5-103">This topic describes how to create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package by copying an existing package, and how to update the `Name` and `GUID` properties of the new package.</span></span>  
  
### <a name="to-copy-a-package"></a><span data-ttu-id="534f5-104">复制包</span><span class="sxs-lookup"><span data-stu-id="534f5-104">To copy a package</span></span>  
  
1.  <span data-ttu-id="534f5-105">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开含有要复制的包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="534f5-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package that you want to copy.</span></span>  
  
2.  <span data-ttu-id="534f5-106">在解决方案资源管理器中，双击包。</span><span class="sxs-lookup"><span data-stu-id="534f5-106">In Solution Explorer, double-click the package.</span></span>  
  
3.  <span data-ttu-id="534f5-107">验证已在解决方案资源管理器中选择要复制的包，或者包含该包的 SSIS 设计器的选项卡是活动的选项卡。</span><span class="sxs-lookup"><span data-stu-id="534f5-107">Verify either the package to copy is selected in Solution Explorer or the tab in SSIS Designer that contains the package is the active tab</span></span>  
  
4.  <span data-ttu-id="534f5-108">在“文件”菜单上，单击“将 \<package name> 另存为”。</span><span class="sxs-lookup"><span data-stu-id="534f5-108">On the **File** menu, click **Save \<package name> As**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="534f5-109">必须在 SSIS 设计器中打开包，然后“另存为”  选项才会出现在“文件”  菜单中。</span><span class="sxs-lookup"><span data-stu-id="534f5-109">The package must be opened in SSIS Designer before the **Save As** option appears on the **File** menu.</span></span>  
  
5.  <span data-ttu-id="534f5-110">（可选）浏览到其他文件夹。</span><span class="sxs-lookup"><span data-stu-id="534f5-110">Optionally, browse to a different folder.</span></span>  
  
6.  <span data-ttu-id="534f5-111">更新包文件的名称。</span><span class="sxs-lookup"><span data-stu-id="534f5-111">Update the name of the package file.</span></span> <span data-ttu-id="534f5-112">确保保留 .dtsx 文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="534f5-112">Make sure that you retain the .dtsx file extension.</span></span>  
  
7.  <span data-ttu-id="534f5-113">单击“保存”  。</span><span class="sxs-lookup"><span data-stu-id="534f5-113">Click **Save**.</span></span>  
  
8.  <span data-ttu-id="534f5-114">在出现提示时，选择是否更新包对象的名称，使其与文件名匹配。</span><span class="sxs-lookup"><span data-stu-id="534f5-114">At the prompt, choose whether to update the name of the package object to match the file name.</span></span> <span data-ttu-id="534f5-115">如果单击 **"是**"，将 `Name` 更新包的属性。</span><span class="sxs-lookup"><span data-stu-id="534f5-115">If you click **Yes**, the `Name` property of the package is updated.</span></span> <span data-ttu-id="534f5-116">新的包将添加到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目，并在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中打开。</span><span class="sxs-lookup"><span data-stu-id="534f5-116">The new package is added to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project and opened in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
9. <span data-ttu-id="534f5-117">（可选）单击 **“控制流”** 选项卡的背景，并单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="534f5-117">Optionally, click in the background of the **Control Flow** tab, and the click **Properties**.</span></span>  
  
10. <span data-ttu-id="534f5-118">在“属性”窗口中，单击 ID 属性的值，然后在下拉列表中单击 \<Generate New ID>。</span><span class="sxs-lookup"><span data-stu-id="534f5-118">In the Properties window, click the value of the ID property, and then in the drop-down list click **\<Generate New ID>**.</span></span>  
  
11. <span data-ttu-id="534f5-119">在 **“文件”** 菜单上，单击 **“保存选定项”** ，以保存新建的包。</span><span class="sxs-lookup"><span data-stu-id="534f5-119">On the **File** menu, click **Save Selected Items** to save the new package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="534f5-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="534f5-120">See Also</span></span>  
 <span data-ttu-id="534f5-121">[保存一个包副本](../../2014/integration-services/save-a-copy-of-a-package.md) </span><span class="sxs-lookup"><span data-stu-id="534f5-121">[Save a Copy of a Package](../../2014/integration-services/save-a-copy-of-a-package.md) </span></span>  
 <span data-ttu-id="534f5-122">[在 SQL Server Data Tools 中创建包](create-packages-in-sql-server-data-tools.md) </span><span class="sxs-lookup"><span data-stu-id="534f5-122">[Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) </span></span>  
 [<span data-ttu-id="534f5-123">Integration Services (SSIS) 包</span><span class="sxs-lookup"><span data-stu-id="534f5-123">Integration Services &#40;SSIS&#41; Packages</span></span>](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  
