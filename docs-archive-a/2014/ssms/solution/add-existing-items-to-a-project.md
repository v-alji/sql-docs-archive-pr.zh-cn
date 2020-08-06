---
title: 向项目中添加现有项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 084b3879-e96b-45a7-b421-6a4b0db2b92b
author: stevestein
ms.author: sstein
ms.openlocfilehash: cffa683bfa2a2c81c059d887231531f03d5c892b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591028"
---
# <a name="add-existing-items-to-a-project"></a><span data-ttu-id="264a9-102">向项目中添加现有项</span><span class="sxs-lookup"><span data-stu-id="264a9-102">Add Existing Items to a Project</span></span>
  <span data-ttu-id="264a9-103">向项目中添加新项，以扩展应用程序功能。</span><span class="sxs-lookup"><span data-stu-id="264a9-103">Add new items to a project to extend application functionality.</span></span> <span data-ttu-id="264a9-104">现有项可以是查询，也可以是杂项文件。</span><span class="sxs-lookup"><span data-stu-id="264a9-104">An existing item can be a query or a miscellaneous file.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="264a9-105">有两个项目类型： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 脚本项目和 Analysis Services 脚本项目。</span><span class="sxs-lookup"><span data-stu-id="264a9-105">has two project types: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Script Project, and Analysis Services Script Project.</span></span> <span data-ttu-id="264a9-106">至于哪些查询文件可以添加到项目中，则取决于项目类型。</span><span class="sxs-lookup"><span data-stu-id="264a9-106">The project type determines the query files that you can add to the project.</span></span> <span data-ttu-id="264a9-107">例如，可以将 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询（扩展名为 .sql 的文件）添加到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 脚本项目，但是不能将其添加到 Analysis Services 脚本项目。</span><span class="sxs-lookup"><span data-stu-id="264a9-107">For example, you can add a [!INCLUDE[tsql](../../includes/tsql-md.md)] query (a file with a .sql extension) to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Script project, but you cannot add it to an Analysis Services Script Project.</span></span> <span data-ttu-id="264a9-108">若要将其他文件扩展名关联到项目类型，请参阅[将文件扩展名与代码编辑器关联](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="264a9-108">To associate additional file extensions to a project type, see [Associate File Extensions to a Code Editor](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md).</span></span>  
  
### <a name="to-add-an-existing-query-or-a-miscellaneous-file-to-a-project"></a><span data-ttu-id="264a9-109">向项目中添加现有查询或杂项文件</span><span class="sxs-lookup"><span data-stu-id="264a9-109">To add an existing query or a miscellaneous file to a project</span></span>  
  
1.  <span data-ttu-id="264a9-110">在解决方案资源管理器中，选择目标项目。</span><span class="sxs-lookup"><span data-stu-id="264a9-110">In Solution Explorer, select a target project.</span></span>  
  
2.  <span data-ttu-id="264a9-111">在“项目”  菜单上，单击“添加现有项”  。</span><span class="sxs-lookup"><span data-stu-id="264a9-111">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
     <span data-ttu-id="264a9-112">**Look in**</span><span class="sxs-lookup"><span data-stu-id="264a9-112">**Look in**</span></span>  
     <span data-ttu-id="264a9-113">找到要从此列表添加到项目中的文件或文件夹。</span><span class="sxs-lookup"><span data-stu-id="264a9-113">Locate the files or folders to add to your project from this list.</span></span> <span data-ttu-id="264a9-114">对于 XML Web services 和 ASP.NET Web 应用程序，文件位于 Web 服务器上。</span><span class="sxs-lookup"><span data-stu-id="264a9-114">For XML Web services and ASP.NET Web applications, the files are located on the Web server.</span></span>  
  
     <span data-ttu-id="264a9-115">**桌面**</span><span class="sxs-lookup"><span data-stu-id="264a9-115">**Desktop**</span></span>  
     <span data-ttu-id="264a9-116">显示桌面上的文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="264a9-116">Displays the files and folders located on the desktop.</span></span>  
  
     <span data-ttu-id="264a9-117">**我的项目**</span><span class="sxs-lookup"><span data-stu-id="264a9-117">**My Projects**</span></span>  
     <span data-ttu-id="264a9-118">显示默认“我的项目”  位置中的文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="264a9-118">Displays the files and folders at the default **My Projects** location.</span></span>  
  
     <span data-ttu-id="264a9-119">**我的电脑**</span><span class="sxs-lookup"><span data-stu-id="264a9-119">**My Computer**</span></span>  
     <span data-ttu-id="264a9-120">显示“我的电脑”  文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="264a9-120">Displays the contents of your **My Computer** folder.</span></span>  
  
     <span data-ttu-id="264a9-121">**文件名**</span><span class="sxs-lookup"><span data-stu-id="264a9-121">**File name**</span></span>  
     <span data-ttu-id="264a9-122">使用此选项可以筛选所显示的文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="264a9-122">Use this option to filter the files and folders that are displayed.</span></span> <span data-ttu-id="264a9-123">输入要用来筛选的完整或部分文件名，使用星号 (`*`) 作为通配符。</span><span class="sxs-lookup"><span data-stu-id="264a9-123">Enter the full or partial file name on which to filter; use an asterisk (`*`) as a wildcard.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="264a9-124">通过在“文件名”  框中输入 URL 或网络路径，导航到 Web 和网络位置。</span><span class="sxs-lookup"><span data-stu-id="264a9-124">Navigate to Web and network locations by entering the URL or network path in the **File name** box.</span></span> <span data-ttu-id="264a9-125">例如，输入 http://mywebsite 可显示 mywebsite Web 位置中可用的文件，输入 \\\myserver\myshare 可显示 myserver 上的 myshare 位置中可用的文件。</span><span class="sxs-lookup"><span data-stu-id="264a9-125">For example, **http://mywebsite** displays the files available at the mywebsite Web location, and **\\\myserver\myshare** displays the files available at the myshare location on myserver.</span></span>  
  
     <span data-ttu-id="264a9-126">**文件类型**</span><span class="sxs-lookup"><span data-stu-id="264a9-126">**Files of type**</span></span>  
     <span data-ttu-id="264a9-127">使用此选项基于文件扩展名筛选文件。</span><span class="sxs-lookup"><span data-stu-id="264a9-127">Use this option to filter files based on file extension.</span></span> <span data-ttu-id="264a9-128">每个产品列出最常用文件类型的默认筛选器。</span><span class="sxs-lookup"><span data-stu-id="264a9-128">Each product lists default filters of the most common file types.</span></span>  
  
     <span data-ttu-id="264a9-129">**添加**</span><span class="sxs-lookup"><span data-stu-id="264a9-129">**Add**</span></span>  
     <span data-ttu-id="264a9-130">使用此下拉按钮可以向项目中添加项以及在默认编辑器中打开该项。</span><span class="sxs-lookup"><span data-stu-id="264a9-130">Use this drop-down button to add the item to the project and open the item in its default editor.</span></span>  
  
    -   <span data-ttu-id="264a9-131">**添加**</span><span class="sxs-lookup"><span data-stu-id="264a9-131">**Add**</span></span>  
  
         <span data-ttu-id="264a9-132">将现有项复制到磁盘上的项目文件夹，并添加解决方案资源管理器中选定项目下的项。</span><span class="sxs-lookup"><span data-stu-id="264a9-132">Copies the existing item to your project folder on disk and adds the item under the selected project in Solution Explorer.</span></span> <span data-ttu-id="264a9-133">对该项所做的任何更改没有反映原始位置中的项。</span><span class="sxs-lookup"><span data-stu-id="264a9-133">Any changes made to the item are not reflected in the item at the original location.</span></span> <span data-ttu-id="264a9-134">这是该文件类型的默认编辑器。</span><span class="sxs-lookup"><span data-stu-id="264a9-134">This is the default editor for the file type.</span></span>  
  
    -   <span data-ttu-id="264a9-135">**添加为链接**</span><span class="sxs-lookup"><span data-stu-id="264a9-135">**Add As Link**</span></span>  
  
         <span data-ttu-id="264a9-136">向项目中添加所选文件，并以该文件类型的默认编辑器打开文件。</span><span class="sxs-lookup"><span data-stu-id="264a9-136">Adds the selected file to the project and opens it with the default editor for the file type.</span></span> <span data-ttu-id="264a9-137">该选项将打开最初选定的文件，而不将文件复制到项目文件夹中。</span><span class="sxs-lookup"><span data-stu-id="264a9-137">This option opens the originally selected file and does not copy the file to the project folder.</span></span>  
  
3.  <span data-ttu-id="264a9-138">如果添加查询文件，则“连接”对话框将提示您为查询指定连接。</span><span class="sxs-lookup"><span data-stu-id="264a9-138">If you are adding query files, the connection dialog will prompt you to specify a connection for the query.</span></span> <span data-ttu-id="264a9-139">如果不希望将连接关联到查询，则可以单击“连接”对话框中的“取消”  。</span><span class="sxs-lookup"><span data-stu-id="264a9-139">You can click **Cancel** on the connection dialog if you do not want to associate a connection to the query.</span></span>  
  
4.  <span data-ttu-id="264a9-140">该文件将添加到项目的“查询”  或“杂项文件”  文件夹中。</span><span class="sxs-lookup"><span data-stu-id="264a9-140">The file will be added to the **Queries** or **Miscellaneous Files** folder of the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="264a9-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="264a9-141">See Also</span></span>  
 <span data-ttu-id="264a9-142">[解决方案资源管理器](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="264a9-142">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="264a9-143">[向项目添加新项](add-new-items-to-a-project.md) </span><span class="sxs-lookup"><span data-stu-id="264a9-143">[Add New Items to a Project](add-new-items-to-a-project.md) </span></span>  
 [<span data-ttu-id="264a9-144">移除或删除项或项目</span><span class="sxs-lookup"><span data-stu-id="264a9-144">Remove or Delete an Item or Project</span></span>](remove-or-delete-an-item-or-project.md)  
  
  
