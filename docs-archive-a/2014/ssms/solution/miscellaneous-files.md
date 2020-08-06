---
title: 杂项文件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- files [SQL Server Management Studio], miscellaneous
- projects [SQL Server Management Studio], files
- solutions [SQL Server Management Studio], files
- miscellaneous files folder [SQL Server]
ms.assetid: 3c952b0b-8f5f-4d86-9e5d-616c10b9df0d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f65c04326e791fa3684a06213c3042a42f2f2ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690281"
---
# <a name="miscellaneous-files"></a><span data-ttu-id="c5ecc-102">杂项文件</span><span class="sxs-lookup"><span data-stu-id="c5ecc-102">Miscellaneous Files</span></span>
  <span data-ttu-id="c5ecc-103">不属于任何项目的文件称为杂项文件  。</span><span class="sxs-lookup"><span data-stu-id="c5ecc-103">Files that are external to any project are called *miscellaneous files*.</span></span> <span data-ttu-id="c5ecc-104">当您打开解决方案时，可以打开并修改与该项目相关的杂项文件。</span><span class="sxs-lookup"><span data-stu-id="c5ecc-104">When you have a solution open, you can open and modify miscellaneous files related to the project.</span></span> <span data-ttu-id="c5ecc-105">如果文件扩展名与项目代码编辑器不关联，则将此文件归类为杂项文件。</span><span class="sxs-lookup"><span data-stu-id="c5ecc-105">A file is classified as a miscellaneous file if the file extension is not associated with the project code editor.</span></span> <span data-ttu-id="c5ecc-106">例如，在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 脚本项目中，扩展名为 .txt 或 .mdx 的文件被视为杂项文件。</span><span class="sxs-lookup"><span data-stu-id="c5ecc-106">For example, in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Scripts Project, files with the extension .txt or .mdx will be treated as miscellaneous files.</span></span> <span data-ttu-id="c5ecc-107">在 MDX 项目中，扩展名为 .txt 或 .sql 的文件被视为杂项文件。</span><span class="sxs-lookup"><span data-stu-id="c5ecc-107">In an MDX project, files with the extension of .txt or .sql will be treated as miscellaneous files.</span></span> <span data-ttu-id="c5ecc-108">若要将文件扩展名与代码编辑器相关联，请参阅[将文件扩展名与代码编辑器关联](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="c5ecc-108">To associate a file extension with a code editor, see [Associate File Extensions to a Code Editor](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md).</span></span>  
  
 <span data-ttu-id="c5ecc-109">为项目添加杂项文件的功能非常有用，许多理由都可以说明这一点。</span><span class="sxs-lookup"><span data-stu-id="c5ecc-109">There are a number of reasons why it is useful to be able to add miscellaneous files to your project.</span></span> <span data-ttu-id="c5ecc-110">您的某个文件可能是无需识别的脚本，但却是解决方案开发中不可缺少的一部分。</span><span class="sxs-lookup"><span data-stu-id="c5ecc-110">You might have a file that is not necessarily a recognized script but integral to the solution's development.</span></span> <span data-ttu-id="c5ecc-111">常见示例包括开发注释或说明、数据文件和代码片段。</span><span class="sxs-lookup"><span data-stu-id="c5ecc-111">Common examples include development notes or instructions, data files, and code clips.</span></span>  
  
 <span data-ttu-id="c5ecc-112">杂项文件可提供灵活性。</span><span class="sxs-lookup"><span data-stu-id="c5ecc-112">Miscellaneous files provide flexibility.</span></span> <span data-ttu-id="c5ecc-113">例如，假定有一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 脚本项目，该项目具有多个用于在数据库中创建表和存储过程的脚本。</span><span class="sxs-lookup"><span data-stu-id="c5ecc-113">For example, suppose you have a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Scripts Project that has several scripts for creation of tables and stored procedures in your database.</span></span> <span data-ttu-id="c5ecc-114">还有几个文件扩展名为 .BCP 的用于表的数据文件，以及一个包括执行说明的 README.TXT 文件。</span><span class="sxs-lookup"><span data-stu-id="c5ecc-114">You also have several data files for the tables with file extensions .BCP and execution instructions in a README.TXT file.</span></span> <span data-ttu-id="c5ecc-115">您可以将数据文件和 README 文件作为杂项文件附加到项目中，以利用项目系统的源代码管理和其他功能。</span><span class="sxs-lookup"><span data-stu-id="c5ecc-115">You can attach the data and the README files as miscellaneous files to the project to take advantage of source control and other features of the project system.</span></span>  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="c5ecc-116">菜单和工具栏会随打开的文件的格式而改变。</span><span class="sxs-lookup"><span data-stu-id="c5ecc-116">menus and toolbars change according to the format of the file you open.</span></span> <span data-ttu-id="c5ecc-117">例如，打开文本文件时，会显示文本编辑器工具栏。</span><span class="sxs-lookup"><span data-stu-id="c5ecc-117">When you open a text file, for example, the Text Editor toolbar appears.</span></span> <span data-ttu-id="c5ecc-118">如果打开 XML 架构文件，则显示 XML 架构工具栏。</span><span class="sxs-lookup"><span data-stu-id="c5ecc-118">If you open an XML Schema file, the XML Schema toolbar appears.</span></span> <span data-ttu-id="c5ecc-119">编辑 XML 架构时，文本编辑器工具栏将不可用。</span><span class="sxs-lookup"><span data-stu-id="c5ecc-119">While editing your XML Schema, the Text Editor toolbar is unavailable.</span></span> <span data-ttu-id="c5ecc-120">在项目文件和杂项文件之间切换时，与项目相关的所有命令和工具栏均被与杂项文件相关的命令和工具栏取代。</span><span class="sxs-lookup"><span data-stu-id="c5ecc-120">When you switch between a project file and a miscellaneous file, all project-related commands and toolbars are replaced by those relevant to the miscellaneous file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5ecc-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5ecc-121">See Also</span></span>  
 <span data-ttu-id="c5ecc-122">[用于管理解决方案和项目的文件](files-that-manage-solutions-and-projects.md) </span><span class="sxs-lookup"><span data-stu-id="c5ecc-122">[Files That Manage Solutions and Projects](files-that-manage-solutions-and-projects.md) </span></span>  
 <span data-ttu-id="c5ecc-123">[SQL Server Management Studio 的解决方案 &#40;&#41;](solutions-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="c5ecc-123">[Solutions &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="c5ecc-124">项目 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="c5ecc-124">Projects &#40;SQL Server Management Studio&#41;</span></span>](projects-sql-server-management-studio.md)  
  
  
