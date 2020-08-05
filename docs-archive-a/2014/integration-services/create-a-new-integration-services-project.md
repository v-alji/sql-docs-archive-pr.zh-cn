---
title: 创建新 Integration Services 项目 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Integration Services], creating
- Integration Services projects, creating
- SQL Server Integration Services projects, creating
- SSIS projects, creating
ms.assetid: 1e23f259-0401-4333-ab4f-89809aae63b1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f62d3ac2d33bb51a0ccc3b77d9f8b5ec0f52b345
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580814"
---
# <a name="create-a-new-integration-services-project"></a><span data-ttu-id="6d2d3-102">创建新的 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="6d2d3-102">Create a New Integration Services Project</span></span>
  <span data-ttu-id="6d2d3-103">此过程创建新项目和新的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 解决方案。</span><span class="sxs-lookup"><span data-stu-id="6d2d3-103">This procedure creates a new project and a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] solution.</span></span>  
  
### <a name="to-create-a-new-integration-services-project"></a><span data-ttu-id="6d2d3-104">创建新的 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="6d2d3-104">To create a new Integration Services project</span></span>  
  
1.  <span data-ttu-id="6d2d3-105">打开 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6d2d3-105">Open [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="6d2d3-106">在 **“文件”** 菜单上，指向 **“新建”** ，然后单击 **“项目”** 。</span><span class="sxs-lookup"><span data-stu-id="6d2d3-106">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="6d2d3-107">在 **“新建项目”** 对话框中，从 **“模板”** 窗格选择 **“Integration Services 项目”** 模板。</span><span class="sxs-lookup"><span data-stu-id="6d2d3-107">In the **New Project** dialog box, in the **Templates** pane, select the **Integration Services Project** template.</span></span>  
  
     <span data-ttu-id="6d2d3-108">**“Integration Services 项目”** 模板创建包含单个空包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="6d2d3-108">The **Integration Services Project** template creates an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains a single, empty package.</span></span>  
  
4.  <span data-ttu-id="6d2d3-109">（可选）编辑项目名称和位置。</span><span class="sxs-lookup"><span data-stu-id="6d2d3-109">(Optional) Edit the project name and the location.</span></span>  
  
     <span data-ttu-id="6d2d3-110">解决方案名称被自动更新，以匹配项目名称。</span><span class="sxs-lookup"><span data-stu-id="6d2d3-110">The solution name is automatically updated to match the project name.</span></span>  
  
5.  <span data-ttu-id="6d2d3-111">若要为解决方案文件创建单独的文件夹，请选择 **“创建解决方案的目录”**。</span><span class="sxs-lookup"><span data-stu-id="6d2d3-111">To create a separate folder for the solution file, select **Create directory for solution**.</span></span> <span data-ttu-id="6d2d3-112">这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="6d2d3-112">This is the default option.</span></span>  
  
6.  <span data-ttu-id="6d2d3-113">如果计算机上安装了源代码管理软件，请选择 **“添加到源代码管理”**  ，以将项目与源代码管理关联起来。</span><span class="sxs-lookup"><span data-stu-id="6d2d3-113">If source control software is installed on the computer, select **Add to source control**  to associate the project with source control.</span></span>  
  
7.  <span data-ttu-id="6d2d3-114">如果源代码管理软件是 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe， **“Visual SourceSafe 登录”** 对话框就会打开。</span><span class="sxs-lookup"><span data-stu-id="6d2d3-114">If the source control software is [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, the **Visual SourceSafe Login** dialog box opens.</span></span> <span data-ttu-id="6d2d3-115">在 **“Visual SourceSafe 登录”** 对话框中，提供用户名、密码和 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe 数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="6d2d3-115">In **Visual SourceSafe Login**, provide a user name, a password, and the name of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe database.</span></span> <span data-ttu-id="6d2d3-116">单击 **“浏览”** 查找数据库。</span><span class="sxs-lookup"><span data-stu-id="6d2d3-116">Click **Browse** to locate the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6d2d3-117">若要查看和更改选定的源代码管理插件以及配置源代码管理环境，请单击“工具”\*\*\*\* 菜单上的“选项”\*\*\*\*，然后展开“源代码管理”\*\*\*\* 节点。</span><span class="sxs-lookup"><span data-stu-id="6d2d3-117">To view and change the selected source control plug-in and to configure the source control environment, click **Options** on the **Tools** menu, and then expand the **Source Control** node.</span></span>  
  
8.  <span data-ttu-id="6d2d3-118">单击 **"确定"** ，将解决方案添加到**解决方案探索**r，并将项目添加到解决方案中。</span><span class="sxs-lookup"><span data-stu-id="6d2d3-118">Click **OK** to add the solution to **Solution Explore**r and add the project to the solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d2d3-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6d2d3-119">See Also</span></span>  
 <span data-ttu-id="6d2d3-120">[Integration Services &#40;SSIS&#41; 项目](integration-services-ssis-projects-and-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="6d2d3-120">[Integration Services &#40;SSIS&#41; Projects](integration-services-ssis-projects-and-solutions.md) </span></span>  
 [<span data-ttu-id="6d2d3-121">在解决方案中添加或删除 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="6d2d3-121">Add or Remove an Integration Services Project in a Solution</span></span>](../../2014/integration-services/add-or-remove-an-integration-services-project-in-a-solution.md)  
  
  
