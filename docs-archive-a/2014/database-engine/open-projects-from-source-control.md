---
title: 从源代码管理打开项目 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], opening
- opening projects
ms.assetid: 942f93a3-e264-4ec4-ba72-a28e0509a527
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 944b121516e3782e35e213e165405b0ecceb7456
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590350"
---
# <a name="open-projects-from-source-control"></a><span data-ttu-id="f09fd-102">从源代码管理打开项目</span><span class="sxs-lookup"><span data-stu-id="f09fd-102">Open Projects from Source Control</span></span>
  <span data-ttu-id="f09fd-103">可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 直接从源代码管理打开项目。</span><span class="sxs-lookup"><span data-stu-id="f09fd-103">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to open projects directly from source control.</span></span> <span data-ttu-id="f09fd-104">执行此操作时，[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 将检索项目的最新版本，并将其复制到本地磁盘中。</span><span class="sxs-lookup"><span data-stu-id="f09fd-104">When you do this, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] retrieves the latest version of the project and copies it to your local disk.</span></span> <span data-ttu-id="f09fd-105">此外，[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 环境还可以为项目自动创建一个解决方案。</span><span class="sxs-lookup"><span data-stu-id="f09fd-105">The [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment also creates a solution for the project automatically.</span></span>  
  
 <span data-ttu-id="f09fd-106">从源代码管理打开一个项目后，可以签出和修改项目文件。</span><span class="sxs-lookup"><span data-stu-id="f09fd-106">After you have opened a project from source control, you can check out and modify the project files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f09fd-107">下列过程只能使用一次。</span><span class="sxs-lookup"><span data-stu-id="f09fd-107">The following procedure should only be used once.</span></span> <span data-ttu-id="f09fd-108">此后，你应该通过依次单击 "**文件**"、"**打开**"，然后单击 "**项目**") ，与任何其他项目 (打开项目。</span><span class="sxs-lookup"><span data-stu-id="f09fd-108">Thereafter, you should open the project like any other project (by clicking **File**, **Open**, and then **Project**).</span></span>  
  
### <a name="to-open-a-project-from-source-control"></a><span data-ttu-id="f09fd-109">从源代码管理打开项目</span><span class="sxs-lookup"><span data-stu-id="f09fd-109">To open a project from source control</span></span>  
  
1.  <span data-ttu-id="f09fd-110">在 "**文件**" 菜单上，指向 "**源代码管理**"，然后单击 "**从源代码管理打开**"。</span><span class="sxs-lookup"><span data-stu-id="f09fd-110">On the **File** menu, point to **Source Control**, and click **Open From Source Control**.</span></span>  
  
2.  <span data-ttu-id="f09fd-111">如果出现提示，请登录到 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe。</span><span class="sxs-lookup"><span data-stu-id="f09fd-111">If prompted, log on to [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe.</span></span>  
  
3.  <span data-ttu-id="f09fd-112">在 "**从 SourceSafe 创建本地项目**" 对话框中，打开包含要打开的项目的文件夹。</span><span class="sxs-lookup"><span data-stu-id="f09fd-112">In the **Create local project from SourceSafe** dialog box, open the folder that contains the project to open.</span></span>  
  
4.  <span data-ttu-id="f09fd-113">"**在文件夹中创建一个新项目"** 框将发生更改，以标识在其中创建项目的本地目录。</span><span class="sxs-lookup"><span data-stu-id="f09fd-113">The **Create a new project in the folder** box changes to identify the local directory in which the project will be created.</span></span> <span data-ttu-id="f09fd-114">如果要将项目放在其他目录中，请键入该目录的路径，或使用**浏览**按钮在本地磁盘上查找该目录。</span><span class="sxs-lookup"><span data-stu-id="f09fd-114">If you want to place the project in a different directory, type the path to the directory or use the **Browse** button to locate the directory on your local disk.</span></span>  
  
5.  <span data-ttu-id="f09fd-115">在 "在**文件夹中创建一个新项目" 框**中，验证是否显示了正确的文件夹，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="f09fd-115">In the **Create a new project in the folder box**, verify that the correct folder is displayed, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="f09fd-116">在 "**打开解决方案**" 对话框中，选择要打开的项目，然后单击 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="f09fd-116">In the **Open Solution** dialog box, select the project you want to open, and click **Open**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f09fd-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f09fd-117">See Also</span></span>  
 <span data-ttu-id="f09fd-118">[从源代码管理打开解决方案和项目](../../2014/database-engine/open-solutions-and-projects-from-source-control.md) </span><span class="sxs-lookup"><span data-stu-id="f09fd-118">[Open Solutions and Projects from Source Control](../../2014/database-engine/open-solutions-and-projects-from-source-control.md) </span></span>  
 [<span data-ttu-id="f09fd-119">从源代码管理打开解决方案</span><span class="sxs-lookup"><span data-stu-id="f09fd-119">Open Solutions from Source Control</span></span>](../../2014/database-engine/open-solutions-from-source-control.md)  
  
  
