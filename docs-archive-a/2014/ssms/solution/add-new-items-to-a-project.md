---
title: 向项目添加新项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 76af8692-324f-4f5e-b1a0-d72ca8a107e3
author: stevestein
ms.author: sstein
ms.openlocfilehash: c73c58952c7801b3a0e2c86652feb461292cf37c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591027"
---
# <a name="add-new-items-to-a-project"></a><span data-ttu-id="8248f-102">向项目添加新项</span><span class="sxs-lookup"><span data-stu-id="8248f-102">Add New Items to a Project</span></span>
  <span data-ttu-id="8248f-103">向项目中添加新项，以扩展应用程序功能。</span><span class="sxs-lookup"><span data-stu-id="8248f-103">Add new items to a project to extend application functionality.</span></span> <span data-ttu-id="8248f-104">新项可以是查询或连接。</span><span class="sxs-lookup"><span data-stu-id="8248f-104">A new item can be a query or a connection.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="8248f-105">有两个项目类型： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 脚本项目和 Analysis Services 脚本项目。</span><span class="sxs-lookup"><span data-stu-id="8248f-105">has two project types: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Script Project, and Analysis Services Script Project.</span></span> <span data-ttu-id="8248f-106">至于哪些项可以添加到项目中，这取决于项目类型。</span><span class="sxs-lookup"><span data-stu-id="8248f-106">The project type determines the items that you can add to the project.</span></span> <span data-ttu-id="8248f-107">例如，可以将 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询（扩展名为 .sql 的文件）添加到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 脚本项目，但是不能将其添加到 Analysis Services 脚本项目。</span><span class="sxs-lookup"><span data-stu-id="8248f-107">For example, you can add a [!INCLUDE[tsql](../../includes/tsql-md.md)] query (a file with a .sql extension) to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Script project, but you cannot add it to an Analysis Services Script Project.</span></span>  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="8248f-108">不允许在项目中创建文件夹。</span><span class="sxs-lookup"><span data-stu-id="8248f-108">does not allow you to create folders within projects.</span></span> <span data-ttu-id="8248f-109">若要组织您的工作，请在解决方案中创建多个项目。</span><span class="sxs-lookup"><span data-stu-id="8248f-109">To organize your work, create multiple projects within the solution.</span></span>  
  
### <a name="to-add-a-new-query-to-an-existing-project"></a><span data-ttu-id="8248f-110">在现有项目中添加新查询</span><span class="sxs-lookup"><span data-stu-id="8248f-110">To add a new query to an existing project</span></span>  
  
1.  <span data-ttu-id="8248f-111">在解决方案资源管理器中，选择目标项目。</span><span class="sxs-lookup"><span data-stu-id="8248f-111">In Solution Explorer, select a target project.</span></span>  
  
2.  <span data-ttu-id="8248f-112">在 **“项目”** 菜单上，单击 **“添加新项”** 。</span><span class="sxs-lookup"><span data-stu-id="8248f-112">On the **Project** menu, click **Add New Item**.</span></span>  
  
3.  <span data-ttu-id="8248f-113">在“添加新项”  对话框的左窗格中，选择一个类别。</span><span class="sxs-lookup"><span data-stu-id="8248f-113">In the **Add New Item** dialog box, select a category in the left pane.</span></span>  
  
4.  <span data-ttu-id="8248f-114">在右窗格中选择一个查询模板，再单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="8248f-114">Select a query template in the right pane, and then click **Add**.</span></span> <span data-ttu-id="8248f-115">新查询随即被添加到项目的“查询”  文件夹中。</span><span class="sxs-lookup"><span data-stu-id="8248f-115">The new query is added in the **Queries** folder of the project.</span></span>  
  
5.  <span data-ttu-id="8248f-116">在“连接到数据库引擎”  对话框中，为新查询指定一个连接，再单击“连接”  。</span><span class="sxs-lookup"><span data-stu-id="8248f-116">In the **Connect to Database Engine** dialog box, specify a connection for the new query, and then click **Connect**.</span></span> <span data-ttu-id="8248f-117">如果不希望将连接与新查询关联，可以在连接对话框中单击“取消”  。</span><span class="sxs-lookup"><span data-stu-id="8248f-117">You can click **Cancel** on the connection dialog if you do not want to associate a connection to the new query.</span></span>  
  
6.  <span data-ttu-id="8248f-118">如果需要，可在解决方案资源管理器中重命名查询。</span><span class="sxs-lookup"><span data-stu-id="8248f-118">Rename the query in Solution Explorer if you wish.</span></span>  
  
### <a name="to-add-a-new-connection-to-an-existing-project"></a><span data-ttu-id="8248f-119">在现有项目中添加新连接</span><span class="sxs-lookup"><span data-stu-id="8248f-119">To add a new connection to an existing project</span></span>  
  
1.  <span data-ttu-id="8248f-120">在解决方案资源管理器中，选择目标项目。</span><span class="sxs-lookup"><span data-stu-id="8248f-120">In Solution Explorer, select a target project.</span></span>  
  
2.  <span data-ttu-id="8248f-121">在 **“项目”** 菜单上，单击 **“添加新项”** 。</span><span class="sxs-lookup"><span data-stu-id="8248f-121">On the **Project** menu, click **Add New Item**.</span></span>  
  
3.  <span data-ttu-id="8248f-122">在左窗格中选择“连接”  。</span><span class="sxs-lookup"><span data-stu-id="8248f-122">Select **Connection** in the left pane.</span></span>  
  
4.  <span data-ttu-id="8248f-123">在右窗格中选择“新建连接”  ，再单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="8248f-123">Select **New Connection** in the right pane, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="8248f-124">在“连接到数据库引擎”  对话框中，为新查询指定一个连接，再单击“连接”  。</span><span class="sxs-lookup"><span data-stu-id="8248f-124">In the **Connect to Database Engine** dialog box, specify a connection for the new query, and then click **Connect**.</span></span> <span data-ttu-id="8248f-125">新连接随即被添加到项目的“连接”  文件夹中。</span><span class="sxs-lookup"><span data-stu-id="8248f-125">The new connection gets added in the **Connections** folder of the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8248f-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8248f-126">See Also</span></span>  
 <span data-ttu-id="8248f-127">[解决方案资源管理器](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="8248f-127">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="8248f-128">[将文件扩展名与代码编辑器关联](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md) </span><span class="sxs-lookup"><span data-stu-id="8248f-128">[Associate File Extensions to a Code Editor](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md) </span></span>  
 <span data-ttu-id="8248f-129">[向项目中添加现有项](add-existing-items-to-a-project.md) </span><span class="sxs-lookup"><span data-stu-id="8248f-129">[Add Existing Items to a Project](add-existing-items-to-a-project.md) </span></span>  
 [<span data-ttu-id="8248f-130">移除或删除项或项目</span><span class="sxs-lookup"><span data-stu-id="8248f-130">Remove or Delete an Item or Project</span></span>](remove-or-delete-an-item-or-project.md)  
  
  
