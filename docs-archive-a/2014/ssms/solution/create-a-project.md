---
title: 创建项目 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], creating
ms.assetid: 7897be19-365b-4b06-bcf0-8a669f67a673
author: stevestein
ms.author: sstein
ms.openlocfilehash: 269feee7225ceb09b1c2ed86419b19ec4001c1f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588220"
---
# <a name="create-a-project"></a><span data-ttu-id="61eb7-102">创建项目</span><span class="sxs-lookup"><span data-stu-id="61eb7-102">Create a Project</span></span>
  <span data-ttu-id="61eb7-103">可以在现有解决方案中创建一个或多个项目。</span><span class="sxs-lookup"><span data-stu-id="61eb7-103">You can create one or more projects within an existing solution.</span></span>  
  
### <a name="to-create-a-new-project-and-add-it-to-a-solution"></a><span data-ttu-id="61eb7-104">创建一个新项目并将其添加到解决方案中</span><span class="sxs-lookup"><span data-stu-id="61eb7-104">To create a new project and add it to a solution</span></span>  
  
1.  <span data-ttu-id="61eb7-105">在解决方案资源管理器中，选择解决方案。</span><span class="sxs-lookup"><span data-stu-id="61eb7-105">In Solution Explorer, select the solution.</span></span>  
  
2.  <span data-ttu-id="61eb7-106">在“文件”  菜单中，指向“添加”  ，再单击“新建项目”  。</span><span class="sxs-lookup"><span data-stu-id="61eb7-106">On the **File** menu, point to **Add**, and click **New Project**.</span></span>  
  
3.  <span data-ttu-id="61eb7-107">在“新建项目”  对话框中，单击一个项目类型。</span><span class="sxs-lookup"><span data-stu-id="61eb7-107">In the  **New Project** dialog box, click a type of project.</span></span>  
  
     <span data-ttu-id="61eb7-108">**模板**</span><span class="sxs-lookup"><span data-stu-id="61eb7-108">**Templates**</span></span>  
     <span data-ttu-id="61eb7-109">在“模板”  框中，选择一个模板。</span><span class="sxs-lookup"><span data-stu-id="61eb7-109">In the **Templates** box, select a template.</span></span> <span data-ttu-id="61eb7-110">在“模板”  框下会显示所选项目模板的简短说明。</span><span class="sxs-lookup"><span data-stu-id="61eb7-110">A brief description of the selected project template appears beneath the **Templates** box.</span></span>  
  
     <span data-ttu-id="61eb7-111">**名称**</span><span class="sxs-lookup"><span data-stu-id="61eb7-111">**Name**</span></span>  
     <span data-ttu-id="61eb7-112">输入要创建的脚本项目的名称。</span><span class="sxs-lookup"><span data-stu-id="61eb7-112">Enter the name of the script project you want to create.</span></span> <span data-ttu-id="61eb7-113">同时将会在“位置”  字段中显示的位置创建一个与项目同名的文件夹。</span><span class="sxs-lookup"><span data-stu-id="61eb7-113">A folder with the same name as the project is also created in the location displayed in the **Location** field.</span></span> <span data-ttu-id="61eb7-114">对于某些项目， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 将创建源文件和其他支持文件，并将其添加到新项目文件夹中。</span><span class="sxs-lookup"><span data-stu-id="61eb7-114">For some projects, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] creates source and other supporting files and adds them to the new project folder.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="61eb7-115">对于某些项目类型，由于指定位置即设置了名称，所以“名称”  文本框不可用。</span><span class="sxs-lookup"><span data-stu-id="61eb7-115">For some project types, the **Name** text box is unavailable because specifying the location sets the name.</span></span> <span data-ttu-id="61eb7-116">例如，Web 应用程序和 Web 服务位于 Web 服务器上，因此它们的名称都取自其所在服务器上指定的虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="61eb7-116">For example, Web applications and Web services are located on a Web server and derive their name from the virtual directory specified on that server.</span></span>  
  
     <span data-ttu-id="61eb7-117">名称不能包含下列字符：</span><span class="sxs-lookup"><span data-stu-id="61eb7-117">Names cannot contain the following characters:</span></span>  
  
    -   <span data-ttu-id="61eb7-118">井号 (#)</span><span class="sxs-lookup"><span data-stu-id="61eb7-118">Pound (#)</span></span>  
  
    -   <span data-ttu-id="61eb7-119">百分号 (%)</span><span class="sxs-lookup"><span data-stu-id="61eb7-119">Percent (%)</span></span>  
  
    -   <span data-ttu-id="61eb7-120">与符号 (&)</span><span class="sxs-lookup"><span data-stu-id="61eb7-120">Ampersand (&)</span></span>  
  
    -   <span data-ttu-id="61eb7-121">星号 (\*)</span><span class="sxs-lookup"><span data-stu-id="61eb7-121">Asterisk (\*)</span></span>  
  
    -   <span data-ttu-id="61eb7-122">竖线 (|)</span><span class="sxs-lookup"><span data-stu-id="61eb7-122">Vertical bar (|)</span></span>  
  
    -   <span data-ttu-id="61eb7-123">反斜杠 (\\)</span><span class="sxs-lookup"><span data-stu-id="61eb7-123">Backslash (\\)</span></span>  
  
    -   <span data-ttu-id="61eb7-124">冒号 (:)</span><span class="sxs-lookup"><span data-stu-id="61eb7-124">Colon (:)</span></span>  
  
    -   <span data-ttu-id="61eb7-125">引号 (")</span><span class="sxs-lookup"><span data-stu-id="61eb7-125">Quotation mark (")</span></span>  
  
    -   <span data-ttu-id="61eb7-126">小于号 (\<)</span><span class="sxs-lookup"><span data-stu-id="61eb7-126">Less than (\<)</span></span>  
  
    -   <span data-ttu-id="61eb7-127">大于号 (>)</span><span class="sxs-lookup"><span data-stu-id="61eb7-127">Greater than (>)</span></span>  
  
    -   <span data-ttu-id="61eb7-128">问号 (?)</span><span class="sxs-lookup"><span data-stu-id="61eb7-128">Question mark (?)</span></span>  
  
    -   <span data-ttu-id="61eb7-129">正斜杠 (/)</span><span class="sxs-lookup"><span data-stu-id="61eb7-129">Forward slash (/)</span></span>  
  
    -   <span data-ttu-id="61eb7-130">前导空格或尾随空格 (' ')</span><span class="sxs-lookup"><span data-stu-id="61eb7-130">Leading or trailing spaces (' ')</span></span>  
  
    -   <span data-ttu-id="61eb7-131">为 Microsoft Windows 或 MS-DOS 保留的名称，如（“nul”、“aux”、“con”、“com1”、“lpt1”等）</span><span class="sxs-lookup"><span data-stu-id="61eb7-131">Names reserved for Microsoft Windows or MS-DOS, such as ("nul", "aux", "con", "com1", "lpt1", and so on)</span></span>  
  
     <span data-ttu-id="61eb7-132">**位置**</span><span class="sxs-lookup"><span data-stu-id="61eb7-132">**Location**</span></span>  
     <span data-ttu-id="61eb7-133">输入要创建项目的位置，或者从列表中选择位置。</span><span class="sxs-lookup"><span data-stu-id="61eb7-133">Enter the location where you want to create your project, or choose one from the list.</span></span>  
  
     <span data-ttu-id="61eb7-134">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="61eb7-134">**Browse**</span></span>  
     <span data-ttu-id="61eb7-135">显示“项目位置”  对话框，使用该对话框，可以导航到一个保存项目的新目录。</span><span class="sxs-lookup"><span data-stu-id="61eb7-135">Displays the **Project Location** dialog box, allowing you to navigate to a new directory in which to save the project.</span></span>  
  
     <span data-ttu-id="61eb7-136">**解决方案**</span><span class="sxs-lookup"><span data-stu-id="61eb7-136">**Solution**</span></span>  
     <span data-ttu-id="61eb7-137">选择“创建新的解决方案”  在“解决方案资源管理器”中创建一个解决方案。</span><span class="sxs-lookup"><span data-stu-id="61eb7-137">Select **Create new Solution** to create a solution in Solution Explorer.</span></span> <span data-ttu-id="61eb7-138">选择“添加到解决方案”  将新项目添加到“解决方案资源管理器”当前打开的解决方案。</span><span class="sxs-lookup"><span data-stu-id="61eb7-138">Select **Add to Solution** to add the new project to the solution currently open in Solution Explorer.</span></span>  
  
     <span data-ttu-id="61eb7-139">**创建解决方案的目录**</span><span class="sxs-lookup"><span data-stu-id="61eb7-139">**Create directory for Solution**</span></span>  
     <span data-ttu-id="61eb7-140">选择启用“(解决方案)名称”  文本框。</span><span class="sxs-lookup"><span data-stu-id="61eb7-140">Select to enable the **(Solution) Name** text box.</span></span> <span data-ttu-id="61eb7-141">此选项会创建一个新的目录，其名称是您为项目和解决方案选择的名称。</span><span class="sxs-lookup"><span data-stu-id="61eb7-141">This option creates a new directory of the name you choose for your project and solution.</span></span>  
  
     <span data-ttu-id="61eb7-142">**解决方案名称**</span><span class="sxs-lookup"><span data-stu-id="61eb7-142">**Solution Name**</span></span>  
     <span data-ttu-id="61eb7-143">输入要在其中创建项目的新解决方案的名称。</span><span class="sxs-lookup"><span data-stu-id="61eb7-143">Enter the name of the new solution in which you want your project to be created.</span></span> <span data-ttu-id="61eb7-144">默认情况下，此字段使用的名称与在“名称”  字段中输入的名称相同。</span><span class="sxs-lookup"><span data-stu-id="61eb7-144">By default, this field uses the same name as entered in the **Name** field.</span></span>  
  
     <span data-ttu-id="61eb7-145">**注意**若要访问此选项，必须同时选中“解决方案”中的“创建新的解决方案”复选框和“创建解决方案的目录”复选框。</span><span class="sxs-lookup"><span data-stu-id="61eb7-145">**Note** To access this option, you must select both the **Create New Solution** in the **Solution** and the **Create directory for Solution** check boxes.</span></span> <span data-ttu-id="61eb7-146">某些项目模板不支持此选项，例如 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="61eb7-146">Some project templates do not support this option, such as Web applications.</span></span>  
  
     <span data-ttu-id="61eb7-147">**添加到源代码管理**</span><span class="sxs-lookup"><span data-stu-id="61eb7-147">**Add to Source Control**</span></span>  
     <span data-ttu-id="61eb7-148">选中此复选框后，在单击“确定”  时即会打开源代码管理应用程序。</span><span class="sxs-lookup"><span data-stu-id="61eb7-148">When this check box is selected, your source control application opens when you click **OK**.</span></span> <span data-ttu-id="61eb7-149">填写源代码管理应用程序所要求的所有信息以继续进行操作。</span><span class="sxs-lookup"><span data-stu-id="61eb7-149">Complete any information required by your source control application to continue.</span></span> <span data-ttu-id="61eb7-150">必须安装源代码管理客户端应用程序才能使用此选项。</span><span class="sxs-lookup"><span data-stu-id="61eb7-150">You must have a source control client application installed to use this option.</span></span>  
  
4.  <span data-ttu-id="61eb7-151">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="61eb7-151">Click **OK**.</span></span>  
  
 <span data-ttu-id="61eb7-152">您可以设置脚本项目的名称，但文件夹名称则由 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 确定，并且不能更改。</span><span class="sxs-lookup"><span data-stu-id="61eb7-152">You can set a name for the script project, but the folder names are established by [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and cannot be changed.</span></span> <span data-ttu-id="61eb7-153">可以使用“添加新项目”  对话框，为一组公共文件夹配置驱动器和路径说明。</span><span class="sxs-lookup"><span data-stu-id="61eb7-153">You can configure the drive and path specification for the common set of folders by using the **Add New Project** dialog box.</span></span> <span data-ttu-id="61eb7-154">右键单击“解决方案资源管理器”  中的解决方案图标，再单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="61eb7-154">Right-click the solution icon in **Solution Explorer**, and then click **Add**.</span></span> <span data-ttu-id="61eb7-155">脚本项目文件夹的默认位置是 C:\Documents and Settings\\*username*\My Documents\SQL Server Management Studio\Projects\\。</span><span class="sxs-lookup"><span data-stu-id="61eb7-155">The default location for script project folders is: C:\Documents and Settings\\*username*\My Documents\SQL Server Management Studio\Projects\\.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61eb7-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="61eb7-156">See Also</span></span>  
 <span data-ttu-id="61eb7-157">[解决方案资源管理器](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="61eb7-157">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="61eb7-158">[向解决方案添加现有项目](add-an-existing-project-to-a-solution.md) </span><span class="sxs-lookup"><span data-stu-id="61eb7-158">[Add an Existing Project to a Solution](add-an-existing-project-to-a-solution.md) </span></span>  
 <span data-ttu-id="61eb7-159">[向项目添加新项](add-new-items-to-a-project.md) </span><span class="sxs-lookup"><span data-stu-id="61eb7-159">[Add New Items to a Project](add-new-items-to-a-project.md) </span></span>  
 <span data-ttu-id="61eb7-160">[向项目中添加现有项](add-existing-items-to-a-project.md) </span><span class="sxs-lookup"><span data-stu-id="61eb7-160">[Add Existing Items to a Project](add-existing-items-to-a-project.md) </span></span>  
 <span data-ttu-id="61eb7-161">[更改项目的默认位置](change-the-default-location-for-projects.md) </span><span class="sxs-lookup"><span data-stu-id="61eb7-161">[Change the Default Location for Projects](change-the-default-location-for-projects.md) </span></span>  
 <span data-ttu-id="61eb7-162">[删除或删除项或项目](remove-or-delete-an-item-or-project.md) </span><span class="sxs-lookup"><span data-stu-id="61eb7-162">[Remove or Delete an Item or Project](remove-or-delete-an-item-or-project.md) </span></span>  
 [<span data-ttu-id="61eb7-163">删除解决方案</span><span class="sxs-lookup"><span data-stu-id="61eb7-163">Delete a Solution</span></span>](delete-a-solution.md)  
  
  
